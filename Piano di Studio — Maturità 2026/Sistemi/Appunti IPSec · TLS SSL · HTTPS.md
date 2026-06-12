# Panoramica

Questa pagina copre i tre protocolli che rendono sicure le comunicazioni su reti non fidate: **IPSec** (sicurezza a livello IP), **TLS/SSL** (sicurezza a livello trasporto) e **HTTPS** (HTTP su TLS). Sono la base tecnica di VPN, navigazione sicura, e-commerce, e-banking.

---

# 1IPSec — Internet Protocol Security

## Cos'è

**IPSec** è una suite di protocolli che aggiunge **autenticazione, integrità e cifratura a livello 3** (Rete). A differenza di TLS che opera a livello 4-7 e protegge una singola applicazione, IPSec protegge **tutto il traffico IP** indipendentemente dall'applicazione che lo genera.

- **Livello OSI**: 3 (Rete) — incapsulato direttamente in IP
- **RFC**: 4301 (architettura), 4302 (AH), 4303 (ESP)
- **Uso principale**: VPN (site-to-site e client-to-site)

## Componenti di IPSec

IPSec non è un singolo protocollo ma una **suite** composta da:

| Componente | Funzione |
| --- | --- |
| **AH** (Authentication Header) | Autenticazione e integrità, **nessuna cifratura** |
| **ESP** (Encapsulating Security Payload) | Autenticazione, integrità **e cifratura** |
| **IKE** (Internet Key Exchange) | Negoziazione e scambio delle chiavi |
| **SA** (Security Association) | Parametri concordati per una connessione IPSec |

In pratica si usa quasi sempre **ESP** (che include tutto) e si depreca AH.

## AH — Authentication Header

AH protegge **l'integrità e l'autenticità** del pacchetto IP (header + payload) usando un HMAC. Non cifra nulla — il payload rimane in chiaro.

```
[IP Header] [AH Header] [Payload in chiaro]
              |
              HMAC su tutto il pacchetto
              (garantisce che non sia stato modificato)
```

**Problema con NAT**: AH autentica anche l'IP header. Il NAT modifica l'IP sorgente → il controllo HMAC fallisce. **AH è incompatibile con NAT.**

## ESP — Encapsulating Security Payload

ESP protegge **integrità, autenticità e riservatezza** del payload. È il componente principale di IPSec.

```
[IP Header] [ESP Header] [Payload CIFRATO] [ESP Trailer] [ESP Auth]
                         |___________________________|       |
                                   cifrato               HMAC su
                                                     ESP header+payload
```

L'IP header esterno non viene cifrato (i router devono poter leggere src/dst per instradare). Il payload è completamente cifrato e autenticato.

**Compatibile con NAT**: solo il payload viene autenticato, non l'IP header esterno.

## IKE — Internet Key Exchange

**IKE** (porta UDP 500, o UDP 4500 con NAT traversal) è il protocollo che stabilisce le **Security Associations** prima di iniziare a trasmettere con IPSec.

Opera in due fasi:

- IKE Phase 1 — Stabilisce il canale di controllo sicuro

    Scopo: creare un canale sicuro e autenticato tra i due peer per poi negoziare i parametri IPSec.

    1. Negoziazione degli algoritmi da usare (cipher suite): algoritmo di cifratura (AES), hash (SHA), gruppo Diffie-Hellman, metodo di autenticazione
    2. Scambio Diffie-Hellman per generare il materiale chiave
    3. Autenticazione reciproca dei peer (con certificati X.509, pre-shared key, o EAP)
    4. Risultato: una **IKE SA** (canale cifrato e autenticato) da usare per la fase 2

    Due modalità: **Main Mode** (6 messaggi, più sicuro) e **Aggressive Mode** (3 messaggi, più veloce ma meno sicuro).

- IKE Phase 2 — Negozia i parametri IPSec

    Scopo: negoziare le **IPSec SA** (una per ogni direzione del traffico) dentro il canale sicuro stabilito in fase 1.

    1. Negoziazione dei parametri: protocollo (ESP o AH), algoritmi di cifratura e hash, durata della SA
    2. Generazione delle chiavi di sessione (derivate dal materiale DH di fase 1 + nonce)
    3. Risultato: due **IPSec SA** (una per ogni direzione), ognuna identificata da un **SPI** (Security Parameter Index)

    Modalità: **Quick Mode** (3 messaggi).


**IKEv2**: versione moderna (RFC 7296), più semplice, più veloce (4 messaggi totali invece di 9+), supporta MOBIKE (mobilità — cambia IP senza rinegoziare), standard per VPN moderne.

## Security Association (SA)

Una **SA** è un insieme unidirezionale di parametri che descrive come proteggere il traffico tra due peer:

- Protocollo (AH o ESP)
- Algoritmo di cifratura e chiave
- Algoritmo di autenticazione e chiave
- SPI (Security Parameter Index) — identificatore della SA
- Durata (lifetime in secondi o byte)

Poiché la SA è unidirezionale, per una comunicazione bidirezionale servono **due SA** (una per A→B, una per B→A). Sono memorizzate nel **SAD** (Security Association Database).

## Modalità operative di IPSec

### Transport Mode

```
Original: [IP Header | TCP | Data]
IPSec:    [IP Header | ESP Header | TCP | Data (cifrato) | ESP Trailer | ESP Auth]
```

- L'IP header originale rimane invariato
- Solo il payload (TCP + dati) viene cifrato/autenticato
- Usato per comunicazioni **host-to-host** dirette
- Più leggero (meno overhead)

### Tunnel Mode

```
Original: [IP Header | TCP | Data]
IPSec:    [NEW IP Header | ESP Header | IP Header | TCP | Data (tutto cifrato) | ESP Trailer | ESP Auth]
```

- L'**intero pacchetto originale** viene incapsulato e cifrato
- Viene aggiunto un nuovo IP header esterno con gli indirizzi dei gateway VPN
- Usato per **VPN gateway-to-gateway** (site-to-site) e **client-to-gateway**
- Nasconde completamente la topologia interna (gli indirizzi IP originali sono cifrati)

> **Quando si usa quale**: Transport mode per IPSec tra due host specifici (es. due server che si parlano). Tunnel mode per VPN: i due gateway cifrano tutto il traffico tra le due reti, i dispositivi interni non sanno nulla di IPSec.
>

## IPSec e le VPN

IPSec è la tecnologia più usata per le **VPN site-to-site** aziendali:

```
Sede A                    Internet                  Sede B
[LAN A] ─► [Gateway A] ───[tunnel IPSec cifrato]─── [Gateway B] ─► [LAN B]
```

I gateway (router o firewall) gestiscono tutto IPSec. I PC delle due sedi comunicano normalmente — non sanno che il traffico viene cifrato e tunnelato attraverso Internet.

---

# 2SSL e TLS

## Storia e relazione SSL/TLS

| Versione | Anno | Stato |
| --- | --- | --- |
| SSL 1.0 | Mai rilasciato pubblicamente | Vulnerabilità critiche |
| SSL 2.0 | 1995 (Netscape) | Deprecato (RFC 6176) |
| SSL 3.0 | 1996 (Netscape) | Deprecato — vulnerabile a POODLE |
| TLS 1.0 | 1999 (RFC 2246) | Deprecato nel 2020 |
| TLS 1.1 | 2006 (RFC 4346) | Deprecato nel 2020 |
| TLS 1.2 | 2008 (RFC 5246) | Ancora ampiamente usato, sicuro |
| TLS 1.3 | 2018 (RFC 8446) | **Standard attuale**, più veloce e sicuro |

> **SSL è morto.** Quando si dice "SSL" oggi si intende quasi sempre TLS. I certificati si chiamano ancora "SSL certificate" per abitudine storica, ma usano TLS.
>

## Cosa offre TLS

TLS opera tra il livello trasporto (TCP) e il livello applicazione. Fornisce tre garanzie:

- **Confidentiality**: i dati sono cifrati — solo mittente e destinatario possono leggerli
- **Integrity**: i dati non possono essere modificati senza rilevamento (MAC)
- **Authentication**: almeno il server viene autenticato tramite certificato digitale (e opzionalmente anche il client)

## TLS 1.2 — Handshake dettagliato

```
Client                                          Server
  |
  |── ClientHello ───────────────────────────────►|
  |  (versione TLS, cipher suites, client_random) |
  |                                                |
  |◄── ServerHello ──────────────────────────────|
  |  (versione scelta, cipher suite scelta,        |
  |   server_random)                               |
  |                                                |
  |◄── Certificate ─────────────────────────────|
  |  (certificato X.509 del server)                |
  |                                                |
  |◄── ServerKeyExchange (se DHE/ECDHE) ─────────|
  |  (parametri DH per il key exchange)            |
  |                                                |
  |◄── ServerHelloDone ────────────────────────|
  |                                                |
  | [Client verifica il certificato del server]    |
  |                                                |
  |── ClientKeyExchange ────────────────────────►|
  |  (pre_master_secret cifrato con PK server,     |
  |   oppure valore DH pubblico del client)        |
  |                                                |
  | [Entrambi derivano il master_secret e          |
  |  le chiavi di sessione da:                     |
  |  pre_master_secret + client_random             |
  |  + server_random]                              |
  |                                                |
  |── ChangeCipherSpec ────────────────────────►|
  |── Finished (HMAC di tutto l'handshake) ────►|
  |                                                |
  |◄── ChangeCipherSpec ────────────────────────|
  |◄── Finished ──────────────────────────────|
  |                                                |
  |====== Dati applicativi cifrati (AES-GCM) ======|
```

**Derivazione delle chiavi**: da `pre_master_secret + client_random + server_random` vengono derivate (con PRF — Pseudo-Random Function) le chiavi simmetriche di sessione:

- `client_write_key`: chiave per cifrare i dati dal client al server
- `server_write_key`: chiave per cifrare i dati dal server al client
- `client_write_MAC_key` e `server_write_MAC_key`: chiavi per l'autenticazione

I due random (`client_random`, `server_random`) garantiscono che anche se `pre_master_secret` fosse compromesso, le chiavi di ogni sessione siano diverse.

## TLS 1.3 — Novità e miglioramenti

TLS 1.3 è una riscrittura sostanziale, non un aggiornamento incrementale.

**Handshake ridotto a 1-RTT** (TLS 1.2 richiedeva 2-RTT):

```
Client                              Server
  |── ClientHello + KeyShare ───►|  (invia anche il valore DH pubblico)
  |◄── ServerHello + KeyShare ───|  (invia il suo valore DH)
  |◄── Certificate + Finished ───|  (già cifrati con la chiave derivata)
  |── Finished ─────────────►|
  |====== Dati cifrati ============|
```

**0-RTT resumption**: per connessioni riprese con un server già visitato, il client può inviare dati applicativi nel primo messaggio (senza aspettare il completamento dell'handshake). Attenzione: i dati 0-RTT non sono protetti contro i replay attack.

**Rimozione degli algoritmi deboli**: TLS 1.3 rimuove:

- RSA key exchange statico (non ha forward secrecy)
- Tutti i cipher CBC con MAC-then-Encrypt
- RC4, DES, 3DES, MD5, SHA-1
- Compressione TLS (vulnerabile a CRIME)

**Algoritmi supportati in TLS 1.3**:

- Key exchange: solo ECDHE e DHE (garantisce **forward secrecy**)
- Cifratura: solo AEAD (AES-GCM, AES-CCM, ChaCha20-Poly1305)
- Hash: SHA-256, SHA-384

## Forward Secrecy (PFS — Perfect Forward Secrecy)

Con RSA key exchange statico (TLS 1.2 vecchio stile): il client cifra il `pre_master_secret` con la chiave pubblica del server. Se un attaccante registra tutto il traffico cifrato e in futuro riesce a ottenere la chiave privata del server, può decifrare **tutto il traffico passato**.

Con **ECDHE/DHE** (Ephemeral Diffie-Hellman): le chiavi di sessione vengono generate con valori DH temporanei (efimeri), usati una sola volta e poi scartati. Anche conoscendo la chiave privata del server, non si può ricostruire le chiavi di sessione passate. Ogni sessione è indipendente.

## Cipher Suite

Una **cipher suite** è una stringa che descrive la combinazione di algoritmi usati in una sessione TLS:

```perl
TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
    |       |         |       |    |
    |       |         |       |    +-- Hash per il PRF (SHA-256)
    |       |         |       +------- Modalità (GCM)
    |       |         +--------------- Algoritmo simmetrico (AES-128)
    |       +------------------------- Autenticazione (RSA)
    +--------------------------------- Key exchange (ECDHE)
```

In TLS 1.3 la cipher suite è semplificata (key exchange e autenticazione sono separati):

```
TLS_AES_256_GCM_SHA384
    |           |
    |           +-- Hash
    +-------------- Cifratura AEAD
```

## Certificati digitali X.509

Un **certificato digitale** lega una chiave pubblica a un'identità (nome di dominio, organizzazione). È firmato digitalmente da una **CA** (Certificate Authority) fidata.

**Contenuto di un certificato X.509**:

- Subject: a chi appartiene (es. `CN=www.example.com`)
- Issuer: chi lo ha firmato (es. `Let's Encrypt Authority`)
- Validity: date di inizio e scadenza
- Public Key: la chiave pubblica del soggetto
- Subject Alternative Names (SAN): domini alternativi coperti
- Signature: firma digitale della CA sull'hash del certificato
- Serial Number e altri metadati

**Chain of trust (catena di fiducia)**:

```
Root CA (autosfirmato, nel trust store del browser)
    └─► Intermediate CA (firmato da Root CA)
            └─► Certificato del sito (firmato da Intermediate CA)
```

Il browser ha pre-installati i certificati delle Root CA fidate (~150 CA nel mondo). Per verificare un certificato risale la catena fino a una Root CA fidata.

**Tipi di certificati per validazione**:

| Tipo | Validazione | Contenuto | Uso |
| --- | --- | --- | --- |
| **DV** (Domain Validation) | Solo controllo del dominio (email o DNS challenge) | Nome dominio | Siti personali, blog |
| **OV** (Organization Validation) | Verifica identità legale dell'organizzazione | Dominio + organizzazione | Aziende |
| **EV** (Extended Validation) | Verifica approfondita (atti legali, fisica) | Dominio + organizzazione verificata | Banche, e-commerce |

**Certificate Revocation**: un certificato può essere revocato prima della scadenza (chiave compromessa, CA compromessa). Meccanismi:

- **CRL** (Certificate Revocation List): lista di certificati revocati pubblicata dalla CA
- **OCSP** (Online Certificate Status Protocol): verifica in tempo reale lo stato di un certificato
- **OCSP Stapling**: il server include la risposta OCSP nel handshake TLS (più efficiente)

---

# 3HTTPS

## Cos'è

**HTTPS** = HTTP + TLS. Il protocollo HTTP viene eseguito sopra una connessione TLS invece che su TCP diretto.

- **Porta**: 443 (HTTP usa la 80)
- **Indicatore**: lucchetto nel browser, URL con `https://`
- **Standard**: RFC 2818

## Cosa protegge esattamente HTTPS

**Protegge**:

- Il contenuto della richiesta HTTP (URL completo dopo il dominio, headers, body, cookie, credenziali)
- Il contenuto della risposta (HTML, dati, token)
- Gli header HTTP in entrambe le direzioni

**Non protegge**:

- Il nome del dominio (hostname) — visibile in chiaro nel campo **SNI** (Server Name Indication) dell'handshake TLS e nelle query DNS (a meno di DoH/DoT)
- L'indirizzo IP del server
- La dimensione approssimativa del traffico (un attaccante vede quanto dati vengono trasferiti)

> **SNI** (Server Name Indication): estensione TLS che il client invia all'inizio dell'handshake per indicare quale dominio vuole raggiungere. Necessario per i server che ospitano più domini sullo stesso IP (virtual hosting). È in chiaro, quindi l'ISP e chi intercetta il traffico vede quale sito si sta visitando, anche se non il contenuto.
>

## HTTPS e il processo completo di connessione

Quando il browser visita `https://www.example.com`:

```
1. DNS lookup: www.example.com → 93.184.216.34
2. TCP SYN → 93.184.216.34:443
3. TCP SYN-ACK → browser
4. TCP ACK (connessione TCP stabilita)
5. TLS ClientHello (inizio handshake)
6. TLS ServerHello + Certificate
7. Browser verifica il certificato:
   - È firmato da una CA fidata?
   - Il CN/SAN corrisponde al dominio?
   - Non è scaduto?
   - Non è revocato?
8. TLS key exchange (ECDHE)
9. TLS Finished (entrambi i lati)
10. HTTP GET /index.html (cifrato in AES-GCM)
11. HTTP 200 OK + contenuto (cifrato)
```

## HSTS — HTTP Strict Transport Security

**HSTS** è un meccanismo che istruisce il browser a **usare sempre HTTPS** per un dominio, anche se l'utente digita `http://` o clicca un link HTTP.

Il server invia l'header:

```
Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
```

- `max-age`: per quanti secondi il browser ricorda di usare solo HTTPS (31536000 = 1 anno)
- `includeSubDomains`: vale anche per tutti i sottodomini
- `preload`: il dominio può essere incluso nella HSTS preload list — la lista hardcoded nei browser di domini che usano sempre HTTPS (anche al primo accesso, prima di ricevere l'header)

**Protegge da SSL stripping**: senza HSTS, un attaccante MitM può intercettare la prima richiesta HTTP e impedire il redirect a HTTPS. Con HSTS il browser non fa mai la prima richiesta in HTTP.

## Certificate Pinning

Tecnica che fa sì che un'applicazione (browser o app mobile) accetti **solo un certificato specifico** o una specifica CA per un dato dominio — ignorando il normale trust store.

**Vantaggio**: protegge anche contro CA compromesse o rogue che emettono certificati falsi per il dominio.

**Svantaggio**: se il certificato viene rinnovato senza aggiornare il pin, l'app smette di funzionare.

Nei browser: HPKP (HTTP Public Key Pinning) è stato deprecato. Il pinning è ancora usato nelle app mobili.

## Mixed Content

Una pagina HTTPS che carica risorse (immagini, script, CSS) via HTTP è detta **mixed content**:

- **Passive mixed content**: immagini, audio, video HTTP in pagina HTTPS — il browser mostra warning
- **Active mixed content**: script, CSS, iframe HTTP in pagina HTTPS — il browser blocca (un script HTTP può modificare il DOM e rubare dati dalla pagina HTTPS)

---

# 4Confronto IPSec vs TLS

|  | IPSec | TLS |
| --- | --- | --- |
| **Livello OSI** | 3 (Rete) | 4–7 (Trasporto-Applicazione) |
| **Cosa protegge** | Tutto il traffico IP | Singola connessione applicativa |
| **Trasparente alle app** | Sì — le app non sanno nulla | No — l'app deve supportare TLS |
| **Configurazione** | Complessa (IKE, SA, policy) | Semplice (libreria nel linguaggio) |
| **Compatibilità NAT** | Problematica (AH incompatibile, ESP ok con NAT-T) | Nessun problema |
| **Uso tipico** | VPN site-to-site, VPN client aziendale | HTTPS, SMTPS, IMAPS, FTPS |
| **Performance** | Overhead maggiore (doppia incapsulazione in tunnel mode) | Overhead minore |
| **Forward Secrecy** | Sì (con IKEv2 + ECDHE) | Sì (con ECDHE, obbligatorio in TLS 1.3) |

---

# Schema Riepilogativo — Dove Opera Ognuno

```
Livello 7 — Applicazione   [HTTP] [SMTP] [FTP] [DNS]
                               |
Livello 6–5                  [TLS/SSL] ← cifra il traffico applicativo
                               |
Livello 4 — Trasporto        [TCP] [UDP]
                               |
Livello 3 — Rete             [IP]
                          [IPSec AH/ESP] ← cifra il payload IP
                               |
Livello 2 — Datalink         [Ethernet] [Wi-Fi]
                               |
Livello 1 — Fisico           [cavi, onde radio]
```

**Risultato combinato**:

- HTTPS = HTTP (L7) + TLS (L5-6) + TCP (L4) + IP (L3)
- VPN IPSec = qualsiasi app (L7) + TCP/UDP (L4) + IPSec ESP (L3) + IP esterno (L3)

---

# Domande tipiche da orale

- Differenza tra AH e ESP in IPSec

    AH autentica l'integrità di header + payload IP ma non cifra nulla — il contenuto rimane leggibile. È incompatibile con NAT perché autentica anche l'IP header che NAT modifica.

    ESP cifra il payload e lo autentica, non tocca l'IP header esterno. È compatibile con NAT (con NAT traversal su UDP 4500). In pratica si usa sempre ESP.

- Transport mode vs Tunnel mode in IPSec

    In transport mode l'IP header originale rimane invariato e solo il payload viene protetto. Usato per comunicazioni dirette host-to-host.

    In tunnel mode l'intero pacchetto originale viene incapsulato dentro un nuovo pacchetto IP. Gli indirizzi IP originali sono cifrati e invisibili. Usato per VPN: i gateway aggiungono il loro IP come sorgente/destinazione esterna, la rete interna è completamente nascosta.

- Cosa succede durante il TLS handshake?
    1. Client invia ClientHello (versioni supportate, cipher suites, client_random)
    2. Server risponde con ServerHello (versione e cipher suite scelte, server_random) + certificato
    3. Client verifica il certificato (CA fidata, dominio corrispondente, non scaduto)
    4. Key exchange (ECDHE): entrambi generano il pre_master_secret
    5. Entrambi derivano le chiavi di sessione (pre_master_secret + i due random)
    6. Finished cifrato: entrambi confermano che l'handshake non è stato manomesso
    7. Dati applicativi cifrati con AES-GCM
- Cos'è la forward secrecy e perché è importante?

    Senza forward secrecy (RSA key exchange statico): se un attaccante registra tutto il traffico cifrato e un giorno ruba la chiave privata del server, può decifrare retroattivamente tutto il traffico passato.

    Con forward secrecy (ECDHE): le chiavi di sessione vengono generate con valori DH efimeri (usa-e-getta). Anche conoscendo la chiave privata del server, non si può ricostruire le chiavi di sessioni passate. TLS 1.3 rende ECDHE obbligatorio.

- Cosa vede chi intercetta traffico HTTPS?

    Vede: l'indirizzo IP del server, il nome del dominio (dall'SNI in chiaro nel ClientHello e dalla query DNS), la dimensione approssimativa dei dati trasferiti, i timestamp.

    Non vede: l'URL specifico dopo il dominio, gli header HTTP, il body delle richieste/risposte, i cookie, le credenziali di login, il contenuto delle pagine.

- Differenza tra IPSec e TLS: quando si usa quale?

    IPSec opera a livello 3 e protegge tutto il traffico IP indipendentemente dall'applicazione. Le applicazioni non devono essere modificate. È la scelta per VPN aziendali site-to-site dove si vuole connettere due reti intere.

    TLS opera a livello applicativo e protegge una singola connessione. L'applicazione deve supportarlo esplicitamente. È la scelta per proteggere servizi specifici: web (HTTPS), email (SMTPS, IMAPS), trasferimento file (FTPS, SFTP-over-TLS).

- Cos'è HSTS e perché protegge da SSL stripping?

    HSTS è un header che il server invia per dire al browser: "d'ora in poi usa sempre HTTPS per questo dominio, per max-age secondi". Il browser memorizza questa istruzione e non tenterà mai una connessione HTTP.

    Senza HSTS: la prima visita a [http://example.com](http://example.com) può essere intercettata da un attaccante MitM che impedisce il redirect a HTTPS (SSL stripping). Con HSTS: il browser non fa mai la prima richiesta in HTTP — va direttamente in HTTPS. La HSTS preload list estende la protezione anche alla prima visita assoluta.


---

> **Collegamento con altri argomenti**: Crittografia simmetrica/asimmetrica/RSA — 16 giu | Firewall e DMZ — 17 giu | CIA e HTTPS — 15 giu | DNS over HTTPS — 14 giu
>