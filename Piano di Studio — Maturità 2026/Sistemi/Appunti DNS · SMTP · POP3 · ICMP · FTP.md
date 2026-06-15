# Panoramica

Questa pagina copre i principali protocolli applicativi (livello 7 OSI) che rendono funzionante Internet nella pratica quotidiana: risoluzione dei nomi (DNS), posta elettronica (SMTP, POP3), diagnostica di rete (ICMP) e trasferimento file (FTP).

---
# DNS — Domain Name System

## Il problema che risolve

Gli esseri umani ricordano nomi (`www.google.com`), le macchine comunicano con indirizzi IP (`142.250.180.46`). DNS è il sistema che traduce i primi nei secondi — una rubrica telefonica distribuita di Internet.

Senza DNS dovresti memorizzare l'IP di ogni sito che vuoi visitare. Con DNS digiti il nome e il sistema risolve automaticamente l'indirizzo.

## Caratteristiche fondamentali

- **Protocollo**: UDP porta **53** (per query normali), TCP porta 53 (per risposte > 512 byte o trasferimenti di zona)
- **Architettura**: distribuita e gerarchica — nessun server conosce tutti i nomi del mondo
- **Database**: distribuito su milioni di server nel mondo
- **Cache**: ogni risposta ha un TTL (Time To Live) — dopo quel tempo la cache scade e bisogna rifare la query

## Struttura gerarchica dei nomi

```
        . (root)
        |
   _____|_____
  |     |     |
 .com  .it  .org  ...  (TLD — Top Level Domain)
  |         |
google    wikipedia
  |         |
 www       www          (sottodomini / hostname)
```

Un **FQDN** (Fully Qualified Domain Name) è il nome completo con tutti i livelli fino alla root:

```
www.google.com.
              ^ punto finale = root (spesso omesso)
```

## Tipi di TLD

| Tipo | Esempi | Descrizione |
| --- | --- | --- |
| **gTLD** (generico) | `.com`, `.org`, `.net`, `.edu`, `.gov` | Originali, non legati a nazioni |
| **ccTLD** (country code) | `.it`, `.uk`, `.de`, `.fr` | Assegnati a ogni nazione |
| **new gTLD** | `.app`, `.dev`, `.shop`, `.pizza` | Introdotti dal 2012, migliaia disponibili |

## Record DNS

Ogni dominio ha associati diversi **record** nel database DNS:

| Tipo | Nome | Contenuto | Uso |
| --- | --- | --- | --- |
| **A** | Address | IPv4 (es. `93.184.216.34`) | Associa hostname → IPv4 |
| **AAAA** | IPv6 Address | IPv6 (es. `2606:2800::1`) | Associa hostname → IPv6 |
| **CNAME** | Canonical Name | Alias (es. `www` → `example.com`) | Alias di un altro hostname |
| **MX** | Mail Exchanger | Hostname del server email | Posta in arrivo per il dominio |
| **NS** | Name Server | Hostname del DNS autoritativo | Delega la zona a un server |
| **PTR** | Pointer | Hostname | Risoluzione inversa: IP → nome |
| **TXT** | Text | Testo libero | SPF, DKIM, verifica dominio |
| **SOA** | Start of Authority | Info sulla zona (serial, refresh...) | Metadati della zona DNS |

## Funzionamento della risoluzione DNS

Quando il browser richiede `www.example.com`:

- Passo per passo — risoluzione ricorsiva
    1. Il browser controlla la **cache locale** del sistema operativo (e la propria cache interna)
    2. Se non trovato, interroga il **resolver ricorsivo** (di solito fornito dall'ISP o configurato manualmente — es. `8.8.8.8` di Google, `1.1.1.1` di Cloudflare)
    3. Il resolver controlla la propria cache. Se non ha la risposta:
    4. Il resolver interroga un **Root Name Server** (ce ne sono 13 nel mondo, identificati da `a.root-servers.net` a `m.root-servers.net`). Il root server non conosce `www.example.com` ma sa qual è il name server responsabile per `.com`.
    5. Il resolver interroga il **TLD Name Server** per `.com`. Questo sa qual è il name server autoritativo per `example.com`.
    6. Il resolver interroga il **Name Server autoritativo** per `example.com`. Questo conosce il record A per `www.example.com` e risponde con l'IP.
    7. Il resolver restituisce l'IP al client e lo mette in **cache** per il TTL specificato nel record.
    8. Il browser apre la connessione TCP verso quell'IP.

    > Tutta questa catena avviene tipicamente in **millisecondi** grazie all'estesa caching a ogni livello.
    >
- Differenza tra query ricorsiva e iterativa

    ## Query ricorsiva

    Il client chiede al resolver: **"dammi l'IP di [www.example.com](http://www.example.com)"** e si aspetta una risposta definitiva. Il resolver fa tutto il lavoro — interroga root server, TLD server, autoritativo — e alla fine risponde con l'IP finale. Se non riesce a trovarlo, risponde con un errore.

    Il client non sa nulla di come il resolver ha ottenuto la risposta: delega completamente. È il tipo di query usato dai **client (browser, OS) verso il proprio resolver** (es. `8.8.8.8`, `1.1.1.1` o quello dell'ISP).

    ## Query iterativa

    Il client chiede al server: **"dammi l'IP di [www.example.com](http://www.example.com)"** ma il server risponde con il meglio che conosce in quel momento — non l'IP finale, ma un **riferimento** a chi potrebbe saperlo:

    > *"Io non so dove sta `www.example.com`, ma so che il TLD server per `.com` è `a.gtld-servers.net` — chiedi a lui."*
    >

    Il resolver riceve questo riferimento, chiude la conversazione con quel server, e **apre una nuova query** verso il server suggerito. Poi ripete:

    ```
    Resolver  ──►  Root Server
              ◄──  "Non lo so. TLD per .com: a.gtld-servers.net"

    Resolver  ──►  a.gtld-servers.net
              ◄──  "Non lo so. Autoritativo per example.com: ns1.example.com"

    Resolver  ──►  ns1.example.com
              ◄──  "www.example.com = 93.184.216.34"  ← risposta finale
    ```

    In ogni passo il resolver riceve solo **un passo avanti**, non la risposta completa. È il resolver che tiene traccia di dove è arrivato e decide a chi chiedere dopo. È il tipo usato dal **resolver quando interroga root server e TLD server**.

    ## Perché questa distinzione esiste?

    I root server e i TLD server ricevono miliardi di query al giorno da tutto il mondo. Se dovessero fare il lavoro completo per ogni query (ricorsiva), sarebbero sommersi. Con le query iterative fanno il minimo: "non lo so, chiedi là" — e passano il problema al resolver. Il carico rimane distribuito.

    Il resolver dell'ISP o di Google/Cloudflare invece accetta query ricorsive dai client perché è appositamente dimensionato per farlo, e usa la cache per evitare di rifare le stesse query iterative ogni volta.


## DNS e sicurezza

- **DNS spoofing / cache poisoning**: un attaccante inserisce record falsi nella cache del resolver, reindirizzando gli utenti verso siti malevoli
- **DNSSEC**: estensione che aggiunge firme digitali ai record DNS per garantirne l'autenticità
- **DNS over HTTPS (DoH)** e **DNS over TLS (DoT)**: cifrano le query DNS per impedire a terzi di vedere quali siti visita l'utente

---

# SMTP — Simple Mail Transfer Protocol

## Cos'è

**SMTP** è il protocollo usato per **inviare** email. Gestisce il trasferimento di messaggi dal client al server di posta del mittente, e poi da server a server fino al destinatario.

- **Livello OSI**: 7 (Applicazione)
- **Trasporto**: TCP
- **Porte**: 25 (server↔server), **587** (client→server, con autenticazione — SMTP Submission), 465 (SMTPS — SMTP su TLS)
- **RFC**: 5321

## Architettura della posta elettronica

```
[Client mittente]
      |
      | SMTP (porta 587)
      ▼
[MTA mittente]  ────── SMTP (porta 25) ──────►  [MTA destinatario]
(Mail Transfer Agent)                            (Mail Transfer Agent)
                                                         |
                                                         ▼
                                                 [Mailbox destinatario]
                                                         |
                                              POP3/IMAP (porta 110/143)
                                                         ▼
                                                 [Client destinatario]
```

- **MUA** (Mail User Agent): il client email dell'utente (Outlook, Thunderbird, Gmail web)
- **MTA** (Mail Transfer Agent): il server che instrada le email (Postfix, Sendmail, Exchange)
- **MDA** (Mail Delivery Agent): consegna il messaggio nella mailbox del destinatario

## Funzionamento — dialogo SMTP

SMTP è un protocollo **testuale**: client e server si scambiano comandi e risposte in ASCII.

```
S: 220 mail.example.com ESMTP Postfix
C: EHLO client.example.com
S: 250-mail.example.com Hello
S: 250-SIZE 52428800
S: 250 STARTTLS
C: MAIL FROM:<mittente@example.com>
S: 250 Ok
C: RCPT TO:<destinatario@example.com>
S: 250 Ok
C: DATA
S: 354 End data with <CR><LF>.<CR><LF>
C: From: Mittente <mittente@example.com>
C: To: Destinatario <destinatario@example.com>
C: Subject: Test
C:
C: Corpo del messaggio.
C: .
S: 250 Ok: queued as 12345
C: QUIT
S: 221 Bye
```

## Comandi SMTP principali

| Comando | Descrizione |
| --- | --- |
| `EHLO` / `HELO` | Saluto iniziale, il client si presenta al server. EHLO richiede estensioni ESMTP. |
| `MAIL FROM` | Specifica l'indirizzo del mittente (envelope sender) |
| `RCPT TO` | Specifica l'indirizzo del destinatario (ripetibile per più destinatari) |
| `DATA` | Inizia il trasferimento del corpo del messaggio |
| `QUIT` | Chiude la connessione |
| `STARTTLS` | Aggiorna la connessione a TLS cifrato |
| `AUTH` | Autenticazione del client (LOGIN, PLAIN, CRAM-MD5) |
| `RSET` | Resetta la transazione corrente |

## Codici di risposta SMTP

| Codice | Significato |
| --- | --- |
| **220** | Servizio pronto |
| **221** | Chiusura connessione |
| **250** | Azione completata con successo |
| **354** | Inizia input messaggio, termina con `.` su riga sola |
| **421** | Servizio non disponibile (temporaneo) |
| **450** | Mailbox non disponibile (temporaneo) |
| **500** | Errore di sintassi nel comando |
| **550** | Mailbox non trovata / accesso rifiutato (permanente) |

## Struttura di un'email (formato MIME)

Un'email è composta da:

- **Envelope**: informazioni di instradamento (MAIL FROM, RCPT TO) — usate dagli MTA, non visibili all'utente
- **Header**: campi visibili (From, To, Subject, Date, Message-ID, CC, BCC...)
- **Body**: il contenuto del messaggio

**MIME** (Multipurpose Internet Mail Extensions) estende il formato base (solo testo ASCII) per supportare allegati, HTML, caratteri non ASCII:

```
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="----=_Part_123"

------=_Part_123
Content-Type: text/plain; charset=UTF-8

Testo del messaggio.

------=_Part_123
Content-Type: application/pdf
Content-Disposition: attachment; filename="documento.pdf"
Content-Transfer-Encoding: base64

JVBERi0xLjQK...
```

---

# POP3 e IMAP — Protocolli di ricezione email

## Cos'è POP3

**POP3** è il protocollo usato per **scaricare** le email dal server di posta al client. È il contrario di SMTP: mentre SMTP consegna, POP3 recupera.

- **Livello OSI**: 7 (Applicazione)
- **Trasporto**: TCP
- **Porte**: **110** (POP3 non cifrato), **995** (POP3S — POP3 su TLS)
- **RFC**: 1939

## Funzionamento — dialogo POP3

Anche POP3 è un protocollo testuale:

```
S: +OK POP3 server ready
C: USER mario@example.com
S: +OK
C: PASS password123
S: +OK Logged in
C: STAT
S: +OK 3 12345       ← 3 messaggi, 12345 byte totali
C: LIST
S: +OK 3 messages
S: 1 4200
S: 2 3100
S: 3 5045
S: .
C: RETR 1             ← scarica messaggio 1
S: +OK 4200 octets
S: [contenuto del messaggio]
S: .
C: DELE 1             ← marca per eliminazione
S: +OK
C: QUIT
S: +OK Bye
```

## Comandi POP3 principali

| Comando | Descrizione |
| --- | --- |
| `USER` | Specifica il nome utente |
| `PASS` | Specifica la password |
| `STAT` | Numero di messaggi e dimensione totale |
| `LIST` | Elenco messaggi con dimensioni |
| `RETR n` | Scarica il messaggio n |
| `DELE n` | Marca il messaggio n per eliminazione |
| `NOOP` | Nessuna operazione (keep-alive) |
| `RSET` | Annulla le marcature di eliminazione |
| `QUIT` | Applica le eliminazioni e chiude |

## Caratteristica chiave: scarica e cancella

Il comportamento classico di POP3 è **scarica il messaggio sul client e cancellalo dal server**. Questo significa:

- Le email sono archiviate localmente sul dispositivo dell'utente
- Il server non conserva i messaggi dopo il download
- Accedendo da un secondo dispositivo, le email non ci sono più

È possibile configurare POP3 per lasciare i messaggi sul server, ma rimane un'impostazione opzionale e non è il design originale.

## POP3 vs IMAP

|  | POP3 | IMAP |
| --- | --- | --- |
| **Porta** | 110 / 995 | 143 / 993 |
| **Modalità** | Scarica ed elimina dal server | Sincronizza: le email restano sul server |
| **Multi-dispositivo** | Problematico | Nativo |
| **Accesso offline** | (dopo il download) | (con cache locale) |
| **Cartelle sul server** | Solo Inbox | Gestione cartelle sul server |
| **Consumo banda** | Basso (scarica una volta) | Più alto (sincronizzazione continua) |
| **Uso oggi** | In declino | Standard de facto |

> IMAP (Internet Message Access Protocol, RFC 3501) è il successore moderno di POP3. Gmail, Outlook e quasi tutti i client moderni usano IMAP o protocolli proprietari (Exchange ActiveSync).

---

# 3b IMAP — Internet Message Access Protocol

## Cos'è

**IMAP** è il protocollo moderno per **accedere e gestire** le email direttamente sul server, senza necessariamente scaricarle. A differenza di POP3 che è pensato per un singolo dispositivo, IMAP è progettato per la sincronizzazione tra più client.

- **Livello OSI**: 7 (Applicazione)
- **Trasporto**: TCP
- **Porte**: **143** (IMAP non cifrato), **993** (IMAPS — IMAP su TLS)
- **RFC**: 3501

## Differenza concettuale con POP3

Con POP3 il server è solo un deposito temporaneo: scarichi, cancelli, e il client diventa l'unica copia delle email. Con IMAP il server è il **repository permanente**: i client si sincronizzano con il server, non lo svuotano. Leggi una mail da telefono → risulta letta anche da PC e viceversa.

## Funzionamento — dialogo IMAP

Anche IMAP è un protocollo testuale, ma più complesso di POP3. Ogni comando è preceduto da un **tag** (identificatore univoco) che permette di abbinare le risposte ai comandi:

```
S: * OK IMAP4rev1 server ready
C: A1 LOGIN mario@example.com password123
S: A1 OK LOGIN completed
C: A2 LIST "" "*"
S: * LIST (\HasNoChildren) "/" INBOX
S: * LIST (\HasNoChildren) "/" Sent
S: * LIST (\HasNoChildren) "/" Trash
S: A2 OK LIST completed
C: A3 SELECT INBOX
S: * 42 EXISTS            ← 42 messaggi nella cartella
S: * 3 RECENT             ← 3 nuovi dall'ultima connessione
S: * OK [UNSEEN 40]
S: A3 OK [READ-WRITE] SELECT completed
C: A4 FETCH 42 (FLAGS ENVELOPE)
S: * 42 FETCH (FLAGS (\Seen) ENVELOPE ("Mon, 9 Jun 2026" "Oggetto" ...))
S: A4 OK FETCH completed
C: A5 FETCH 42 BODY[]
S: * 42 FETCH (BODY[] {1234}    ← scarica il corpo del messaggio
S: [contenuto del messaggio]
S: A5 OK FETCH completed
C: A6 STORE 42 +FLAGS (\Seen)
S: * 42 FETCH (FLAGS (\Seen \Recent))
S: A6 OK STORE completed
C: A7 LOGOUT
S: * BYE IMAP4rev1 server logging out
S: A7 OK LOGOUT completed
```

## Comandi IMAP principali

| Comando | Descrizione |
| --- | --- |
| `LOGIN` | Autenticazione con username e password |
| `LIST` | Elenca le cartelle disponibili |
| `SELECT` | Apre una cartella (in lettura/scrittura) |
| `EXAMINE` | Apre una cartella in sola lettura |
| `FETCH` | Recupera messaggi o parti di messaggi (header, body, flags) |
| `STORE` | Modifica i flag di un messaggio |
| `SEARCH` | Cerca messaggi in base a criteri (data, mittente, oggetto...) |
| `COPY` | Copia messaggi in un'altra cartella |
| `MOVE` | Sposta messaggi in un'altra cartella |
| `CREATE` | Crea una nuova cartella |
| `DELETE` | Elimina una cartella |
| `EXPUNGE` | Rimuove definitivamente i messaggi marcati con `\Deleted` |
| `IDLE` | Il server notifica il client quando arrivano nuovi messaggi (push) |
| `LOGOUT` | Chiude la sessione |

## Flag IMAP

Ogni messaggio in IMAP ha dei **flag** che ne descrivono lo stato. I flag di sistema sono:

| Flag | Significato |
| --- | --- |
| `\Seen` | Messaggio letto |
| `\Answered` | Messaggio a cui si è risposto |
| `\Flagged` | Messaggio contrassegnato (stella) |
| `\Deleted` | Messaggio marcato per eliminazione (non ancora rimosso) |
| `\Draft` | Bozza |
| `\Recent` | Nuovo dall'ultima connessione |

> In IMAP eliminare un messaggio è un processo in due fasi: prima si imposta il flag `\Deleted`, poi si esegue `EXPUNGE` che rimuove fisicamente tutti i messaggi marcati. Questo permette di "annullare" una cancellazione prima di fare EXPUNGE.

## IMAP e la sincronizzazione multi-dispositivo

Quando accedi alla stessa casella da più dispositivi (telefono, PC, tablet, webmail):

1. Ogni client si connette al server con IMAP
2. Tutte le operazioni (lettura, spostamento, cancellazione, creazione cartelle) avvengono **sul server**
3. Gli altri client vedono le modifiche alla prossima sincronizzazione (o in tempo reale con il comando `IDLE`)
4. Non c'è mai una "copia master" su un singolo dispositivo: il server è sempre la fonte di verità

Questo è il motivo per cui se elimini una mail da Gmail sul telefono, scompare anche da Gmail sul PC — entrambi parlano con lo stesso server IMAP.

## IMAP vs POP3 — quando usare quale

Oggi **IMAP è sempre la scelta giusta** tranne in casi molto specifici:

- **POP3 ha senso se**: hai spazio limitato sul server, vuoi un archivio locale unico, non hai accesso stabile a Internet
- **IMAP ha senso se**: usi più dispositivi, vuoi accedere alle email da qualunque posto, preferisci che il backup sia sul server (spesso più affidabile del disco locale)

---

# ICMP — Internet Control Message Protocol

## Cos'è

**ICMP** è il protocollo di **diagnostica e controllo** di IP. Non trasporta dati applicativi: serve a segnalare errori, verificare la raggiungibilità degli host e misurare i tempi di risposta.

- **Livello OSI**: 3 (Rete) — è incapsulato direttamente in IP, non usa TCP o UDP
- **RFC**: 792 (ICMPv4), 4443 (ICMPv6)
- **Campi chiave**: Type (tipo di messaggio), Code (sotto-tipo), Checksum, e payload variabile

## Struttura del messaggio ICMP

```
 0                   1                   2                   3
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |     Code      |          Checksum             |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    (dipende dal tipo)                         |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

## Messaggi ICMP principali

| Type | Code | Nome | Descrizione |
| --- | --- | --- | --- |
| **0** | 0 | Echo Reply | Risposta a un ping |
| **3** | 0 | Destination Unreachable — Network | La rete di destinazione non è raggiungibile |
| **3** | 1 | Destination Unreachable — Host | L'host di destinazione non risponde |
| **3** | 3 | Destination Unreachable — Port | La porta di destinazione non è in ascolto |
| **5** | — | Redirect | Il router suggerisce un percorso migliore |
| **8** | 0 | Echo Request | Richiesta ping |
| **11** | 0 | Time Exceeded — TTL | Il TTL del pacchetto è scaduto (usato da traceroute) |
| **11** | 1 | Time Exceeded — Fragment | Timeout nel riassemblaggio dei frammenti |

> **Nota sui codici Destination Unreachable**: anche se ICMP opera al livello 3 e non conosce le porte, il Code 3 (Port Unreachable) esiste perché è generato dall’**host di destinazione** — non da un router intermedio. Il pacchetto è già arrivato a destinazione, ma nessun processo UDP è in ascolto su quella porta: l’host usa ICMP come meccanismo di notifica verso il mittente. I codici 0 e 1 invece vengono generati da un **router** che non riesce a instradare il pacchetto verso la rete o l’host.

> Per **TCP** il messaggio Port Unreachable non serve: se la porta è chiusa, il TCP stack risponde direttamente con un segmento **RST** — nessun ICMP coinvolto.

## ping

**ping** è lo strumento di diagnostica più usato. Invia pacchetti ICMP Echo Request (Type 8) all'host target e misura se e in quanto tempo arriva l'Echo Reply (Type 0).

```bash
$ ping www.google.com
PING www.google.com (142.250.180.46)
64 bytes from 142.250.180.46: icmp_seq=1 ttl=116 time=12.3 ms
64 bytes from 142.250.180.46: icmp_seq=2 ttl=116 time=11.8 ms
64 bytes from 142.250.180.46: icmp_seq=3 ttl=116 time=12.1 ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss
rtt min/avg/max = 11.8/12.0/12.3 ms
```

- `ttl=116`: TTL residuo del pacchetto di risposta. Il TTL originale era 128 (Windows) o 64 (Linux/macOS) — la differenza indica il numero approssimativo di hop.
- `time=12.3 ms`: RTT (Round Trip Time) — tempo di andata e ritorno
- `0% packet loss`: nessun pacchetto perso → connettività OK

## traceroute / tracert

**traceroute** (Linux/macOS) o **tracert** (Windows) mappa il percorso che i pacchetti compiono attraverso la rete, hop per hop.

**Come funziona**: invia una serie di pacchetti con TTL crescente (1, 2, 3...). Ogni router che riceve un pacchetto con TTL=0 lo scarta e manda un ICMP Time Exceeded (Type 11) al mittente. Dal messaggio ICMP si ricava l'IP del router.

```bash
$ traceroute www.google.com
 1  192.168.1.1 (router di casa)    1.2 ms
 2  10.0.0.1 (router ISP)           8.4 ms
 3  195.22.x.x (backbone ISP)      10.1 ms
 4  * * *                           (router che non risponde a ICMP)
 5  142.250.180.46                  12.3 ms
```

## Il campo TTL in IP

Il **TTL** (Time To Live) è un campo nell'header IP che vale inizialmente 64 o 128. Ogni router che instrada il pacchetto lo decrementa di 1. Quando arriva a 0, il router scarta il pacchetto e manda un ICMP Time Exceeded al mittente.

Scopo: evitare che i pacchetti girino all'infinito nella rete in caso di loop di routing.

## ICMP e sicurezza

ICMP può essere usato per attacchi:

- **Ping flood**: inviare un numero enorme di Echo Request per saturare la banda della vittima (DDoS)
- **Smurf attack**: inviare Echo Request con IP sorgente falsificato (spoofed) verso indirizzi broadcast — tutti gli host della rete rispondono alla vittima
- **ICMP redirect attack**: inviare falsi messaggi Redirect per alterare le tabelle di routing

Per questo molti firewall bloccano o limitano ICMP, anche se questo rende più difficile la diagnostica.

---

# FTP — File Transfer Protocol

## Cos'è

**FTP** è il protocollo per il **trasferimento di file** tra client e server. È uno dei protocolli applicativi più antichi di Internet (1971, RFC 959 del 1985).

- **Livello OSI**: 7 (Applicazione)
- **Trasporto**: TCP
- **Caratteristica distintiva**: usa **due connessioni TCP separate** — una per i comandi, una per i dati

## Le due connessioni FTP

| Connessione | Porta server | Porta client | Uso |
| --- | --- | --- | --- |
| **Control** | 21 | Casuale (>1023) | Comandi e risposte, sempre aperta |
| **Data** | 20 (modalità attiva) | Casuale (>1023) | Trasferimento effettivo dei file |

Questa separazione è insolita rispetto agli altri protocolli e crea complessità con i firewall e il NAT.

## Modalità attiva vs passiva

- Modalità attiva (Active mode)
    1. Il client apre la connessione di controllo verso la porta 21 del server
    2. Il client sceglie una porta casuale per i dati e la comunica al server con il comando `PORT`
    3. Il **server** apre la connessione dati **dalla sua porta 20** verso la porta indicata dal client

    **Problema**: il server deve aprire una connessione verso il client. Se il client è dietro un firewall o NAT, questa connessione in ingresso viene tipicamente bloccata.

- Modalità passiva (Passive mode — PASV)
    1. Il client apre la connessione di controllo verso la porta 21 del server
    2. Il client manda il comando `PASV`
    3. Il **server** apre una porta casuale e la comunica al client
    4. Il **client** apre la connessione dati verso quella porta del server

    **Vantaggio**: è sempre il client ad aprire le connessioni, quindi funziona attraverso firewall e NAT. È la modalità usata praticamente sempre oggi.


## Funzionamento — dialogo FTP

```
S: 220 FTP server ready
C: USER mario
S: 331 Password required
C: PASS password123
S: 230 Login successful
C: PWD
S: 257 "/home/mario"
C: PASV
S: 227 Entering Passive Mode (192,168,1,100,195,149)
   ← porta dati: 195*256+149 = 50069
C: RETR documento.pdf
S: 150 Opening data connection
   [trasferimento file sulla connessione dati]
S: 226 Transfer complete
C: QUIT
S: 221 Goodbye
```

## Comandi FTP principali

| Comando | Descrizione |
| --- | --- |
| `USER` | Nome utente |
| `PASS` | Password |
| `PWD` | Stampa la directory corrente |
| `CWD` | Cambia directory |
| `LIST` | Elenca i file nella directory corrente |
| `RETR` | Scarica un file dal server |
| `STOR` | Carica un file sul server |
| `DELE` | Elimina un file |
| `MKD` | Crea una directory |
| `RMD` | Rimuove una directory |
| `PASV` | Entra in modalità passiva |
| `PORT` | Specifica porta per modalità attiva |
| `TYPE` | Imposta modalità trasferimento (A=ASCII, I=Binary) |
| `QUIT` | Chiude la sessione |

## Codici di risposta FTP

| Codice | Significato |
| --- | --- |
| **150** | Apertura connessione dati in corso |
| **200** | Comando OK |
| **220** | Servizio pronto |
| **226** | Trasferimento completato |
| **227** | Modalità passiva (con IP e porta) |
| **230** | Login riuscito |
| **331** | Password richiesta |
| **425** | Impossibile aprire la connessione dati |
| **530** | Autenticazione fallita |
| **550** | File non trovato o permesso negato |

## Modalità di trasferimento

- **ASCII (TYPE A)**: per file di testo. Il server converte i fine riga in base al sistema operativo (CRLF su Windows, LF su Unix). Non usare per file binari.
- **Binario (TYPE I — Image)**: trasferimento byte per byte, senza modifiche. Da usare sempre per file non di testo (PDF, immagini, eseguibili, ZIP).

## Limiti di sicurezza e alternative

**FTP non cifra nulla**: credenziali, comandi e dati viaggiano in chiaro. Un attaccante sulla stessa rete può intercettare username e password.

| Protocollo | Descrizione | Porta |
| --- | --- | --- |
| **FTPS** (FTP Secure) | FTP + TLS/SSL. Due varianti: Explicit (STARTTLS su porta 21) e Implicit (porta 990) | 21 / 990 |
| **SFTP** (SSH FTP) | Non è FTP: è un sottosistema di SSH. Usa un unico canale cifrato. | **22** |
| **SCP** | Copia file su SSH, più semplice di SFTP | **22** |

> FTPS e SFTP sono protocolli diversi nonostante i nomi simili. SFTP non ha nulla a che fare con FTP dal punto di vista tecnico — usa SSH, non FTP.

---

# Tabella Riepilogativa — Tutti i Protocolli

| Protocollo | Livello OSI | Trasporto | Porta | Funzione |
| --- | --- | --- | --- | --- |
| **DNS** | 7 | UDP (query) / TCP (zona) | **53** | Risoluzione nomi → IP |
| **SMTP** | 7 | TCP | **25** (server), **587** (client auth) | Invio email |
| **POP3** | 7 | TCP | **110** / 995 (TLS) | Ricezione email (scarica) |
| **IMAP** | 7 | TCP | **143** / 993 (TLS) | Ricezione email (sincronizza) |
| **ICMP** | 3 | — (diretto su IP) | — | Diagnostica e controllo |
| **FTP** | 7 | TCP | **21** (ctrl) / **20** (dati) | Trasferimento file |
| **FTPS** | 7 | TCP | 21 / 990 | FTP cifrato con TLS |
| **SFTP** | 7 | TCP | **22** | Trasferimento file su SSH |

---

# Domande tipiche da orale

- Come funziona la risoluzione DNS? Quanti server coinvolge?

    La risoluzione coinvolge tipicamente 3 tipi di server oltre al resolver dell'ISP: root name server (13 nel mondo, sanno a chi chiedere per ogni TLD), TLD name server (gestiscono .com, .it ecc.), name server autoritativo (conosce i record del dominio specifico). Il processo usa query iterative tra resolver e server, e la risposta viene messa in cache per il TTL specificato.

- Differenza tra SMTP e POP3

    SMTP invia email (client→server mittente, poi server→server destinatario). POP3 riceve email (server→client destinatario). Sono complementari: SMTP è il postino che consegna, POP3 è l'ufficio postale da cui vai a ritirare.

- A cosa serve ICMP? Non è TCP né UDP.

    ICMP è il protocollo di diagnostica di IP: segnala errori (host irraggiungibile, TTL scaduto, porta chiusa) e risponde alle richieste di verifica di raggiungibilità (ping). Non è a livello di trasporto: è incapsulato direttamente in IP (protocol number 1). Strumenti come ping e traceroute si basano interamente su ICMP.

- Perché FTP usa due connessioni TCP?

    Il design originale separa il canale di controllo (comandi) da quello dati per mantenere la sessione aperta durante il trasferimento e per permettere trasferimenti multipli nella stessa sessione senza riautenticarsi. Lo svantaggio è che crea problemi con NAT e firewall, risolti dalla modalità passiva dove è sempre il client ad aprire entrambe le connessioni.

- Differenza tra FTP attivo e FTP passivo

    In modalità attiva è il server che apre la connessione dati verso il client (dalla porta 20): problematico con firewall/NAT lato client. In modalità passiva il server apre una porta random e il client ci si connette: funziona sempre perché è il client (già dietro NAT) ad aprire tutte le connessioni. Oggi si usa quasi esclusivamente la modalità passiva.

- Perché FTP non è sicuro? Cosa si usa invece?

    FTP trasmette tutto in chiaro — credenziali incluse. Chiunque sulla rete può fare sniffing e leggere username e password. Le alternative sicure sono FTPS (FTP con TLS, stessa logica a due canali ma cifrata) e SFTP (sottosistema SSH, protocollo completamente diverso, un solo canale cifrato sulla porta 22). SFTP è oggi lo standard per i trasferimenti sicuri.

- Cos'è il TTL e perché è importante in DNS e in IP?

    In **IP**: il TTL è un campo nell'header che parte da 64 o 128 e viene decrementato di 1 da ogni router. A 0, il pacchetto viene scartato e viene inviato un ICMP Time Exceeded. Scopo: evitare loop infiniti. Traceroute sfrutta questo meccanismo.

    In **DNS**: il TTL è il tempo in secondi per cui una risposta può essere tenuta in cache. TTL alto = meno query DNS, più lentezza nell'aggiornare i record. TTL basso = record più aggiornati, più carico sui server DNS.


---

> **Collegamento con altri argomenti**: HTTP e architettura client-server — 13 giu | Cybersecurity (sniffing, spoofing, firewall) — 15 giu | Socket e programmazione di rete — Informatica
