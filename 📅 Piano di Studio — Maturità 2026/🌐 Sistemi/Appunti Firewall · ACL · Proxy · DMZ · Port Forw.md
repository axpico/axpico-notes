---

# 🛡️ Panoramica

Questa pagina copre la **sicurezza perimetrale**: i meccanismi che proteggono il confine tra la rete interna (trusted) e il mondo esterno (untrusted). Firewall, ACL, proxy, DMZ e port forwarding sono i mattoni fondamentali di qualsiasi architettura di rete sicura.

---
# 1️⃣ Firewall

## Cos'è

Un **firewall** è un sistema (hardware, software, o entrambi) che **filtra il traffico di rete** in base a regole predefinite. Si posiziona tra due reti con diversi livelli di fiducia e decide quali pacchetti possono passare e quali vengono bloccati.

**Funzione base**: implementare una **policy di sicurezza** — un insieme di regole che specificano cosa è permesso e cosa è vietato.

## Tipologie di firewall

- 1. Packet Filter (Stateless)
    
    Opera al **livello 3–4** (Rete/Trasporto). Analizza ogni pacchetto singolarmente e indipendentemente dagli altri, in base a:
    
    - IP sorgente e destinazione
    - Porta sorgente e destinazione
    - Protocollo (TCP, UDP, ICMP)
    - Interfaccia di ingresso/uscita
    - Flag TCP (SYN, ACK, FIN...)
    
    **Stateless**: non tiene traccia dello stato delle connessioni. Ogni pacchetto viene valutato da zero.
    
    **Problema**: non sa distinguere un pacchetto di risposta legittimo da un pacchetto malevolo in ingresso. Se vuoi bloccare connessioni in ingresso ma permettere il traffico di risposta alle connessioni uscenti, devi aprire esplicitamente porte in ingresso per le risposte — il che crea vulnerabilità.
    
    **Esempio di regola** (iptables):
    
    ```bash
    # Permetti HTTP in uscita
    iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
    # Blocca tutto il resto in ingresso
    iptables -A INPUT -j DROP
    ```
    
    **Vantaggi**: velocissimo, nessun overhead di stato, supportato da tutti i router
    
    **Svantaggi**: non capisce il contesto, vulnerabile a spoofing e frammentazione
    
- 2. Stateful Firewall (Stateful Packet Inspection — SPI)
    
    Opera ai **livelli 3–4**. Mantiene una **tabella delle connessioni attive** (state table) che traccia lo stato di ogni connessione TCP/UDP.
    
    **Come funziona**: quando un host interno avvia una connessione verso l'esterno (es. GET HTTP), il firewall registra la connessione nella state table (IP src, IP dst, porta src, porta dst, stato TCP). Quando arriva la risposta dal server esterno, il firewall la riconosce come parte di una connessione legittima già stabilita e la lascia passare automaticamente — senza dover aprire porte in ingresso nelle regole statiche.
    
    **Stati TCP tracciati**: NEW (primo SYN), ESTABLISHED (connessione attiva), RELATED (connessione correlata, es. FTP data), INVALID
    
    **Esempio** (iptables stateful):
    
    ```bash
    # Permetti connessioni stabilite e correlate in ingresso
    iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
    # Permetti nuove connessioni in uscita
    iptables -A OUTPUT -m state --state NEW,ESTABLISHED -j ACCEPT
    # Blocca tutto il resto
    iptables -A INPUT -j DROP
    ```
    
    **Vantaggi**: molto più sicuro del packet filter, gestisce automaticamente il traffico di ritorno
    
    **Svantaggi**: consumo di memoria per la state table, possibile attacco di esaurimento della tabella (SYN flood)
    
- 3. Application Layer Firewall / WAF
    
    Opera al **livello 7** (Applicazione). Analizza il payload delle connessioni, non solo gli header IP/TCP.
    
    **WAF** (Web Application Firewall): specializzato nel traffico HTTP/HTTPS. Può rilevare e bloccare:
    
    - SQL injection nei parametri GET/POST
    - Cross-Site Scripting (XSS)
    - Command injection
    - Violazioni del protocollo HTTP
    - Pattern di attacco noti (OWASP Top 10)
    
    Per analizzare HTTPS deve fare **SSL inspection** (SSL termination): decifra il traffico, lo analizza, lo ricifra. Questo richiede che il certificato del firewall sia trusted dai client.
    
    **Vantaggi**: vede gli attacchi applicativi invisibili ai firewall di rete
    
    **Svantaggi**: molto più lento (deve decodificare il payload), costoso, falsi positivi
    
- 4. Next-Generation Firewall (NGFW)
    
    Combina in un unico dispositivo:
    
    - Stateful inspection
    - **Deep Packet Inspection (DPI)**: analisi del payload a livello applicativo
    - **IPS** (Intrusion Prevention System) integrato
    - Controllo delle applicazioni (identifica WhatsApp, Netflix, BitTorrent... indipendentemente dalla porta)
    - Ispezione SSL/TLS
    - Reputazione IP/URL (blocca IP e domini noti come malevoli)
    - Filtraggio URL per categorie
    - Sandbox per analisi malware
    
    Esempi: Palo Alto Networks, Fortinet FortiGate, Cisco Firepower, Check Point.
    

## Politica di default

Ogni firewall ha una **politica di default** che si applica quando nessuna regola esplicita corrisponde al traffico:

- **Default deny (whitelist)**: blocca tutto ciò che non è esplicitamente permesso. Più sicuro, più restrittivo. Raccomandato per reti aziendali.
- **Default allow (blacklist)**: permette tutto ciò che non è esplicitamente bloccato. Più comodo, molto meno sicuro.

> 💡 La regola `DENY ALL` alla fine di ogni ACL implementa il **default deny**. In pratica: si aprono solo le porte strettamente necessarie, tutto il resto è bloccato.
> 

---

# 2️⃣ ACL — Access Control List

## Cos'è

Una **ACL** è una lista ordinata di regole (dette **ACE** — Access Control Entry) che definiscono quale traffico è **permesso (permit)** o **negato (deny)**. Le ACL sono il meccanismo con cui si configurano i firewall e i router per filtrare il traffico.

Le regole vengono valutate **in ordine**: la prima regola che corrisponde al pacchetto viene applicata, le successive vengono ignorate. Se nessuna regola corrisponde si applica il **deny implicito** finale.

## Struttura di una ACE

```
[numero] [permit|deny] [protocollo] [src_ip] [src_mask] [dst_ip] [dst_mask] [porta] [flag]
```

## Tipi di ACL (nomenclatura Cisco)

**Standard ACL** (numeri 1–99 e 1300–1999):

- Filtra solo in base all'**IP sorgente**
- Semplice ma limitata
- Va applicata il più vicino possibile alla destinazione

```
access-list 10 permit 192.168.1.0 0.0.0.255
access-list 10 deny any
```

**Extended ACL** (numeri 100–199 e 2000–2699):

- Filtra in base a IP sorgente, IP destinazione, protocollo, porta sorgente, porta destinazione
- Molto più granulare
- Va applicata il più vicino possibile alla sorgente (per bloccare il traffico il prima possibile)

```
! Permetti HTTP da rete interna verso qualsiasi destinazione
access-list 100 permit tcp 192.168.1.0 0.0.0.255 any eq 80
! Permetti HTTPS
access-list 100 permit tcp 192.168.1.0 0.0.0.255 any eq 443
! Permetti DNS
access-list 100 permit udp 192.168.1.0 0.0.0.255 any eq 53
! Blocca tutto il resto
access-list 100 deny ip any any
```

## Wildcard mask

Nelle ACL Cisco si usa la **wildcard mask** (inverso della subnet mask):

- `0.0.0.0` = controlla tutti i bit (host specifico)
- `0.0.0.255` = ignora gli ultimi 8 bit (intera /24)
- `255.255.255.255` = ignora tutti i bit (any)

Esempio: `192.168.1.0 0.0.0.255` corrisponde a tutti gli IP da 192.168.1.0 a 192.168.1.255.

## Direzione di applicazione

Le ACL vengono applicate a un'**interfaccia** di un router in una direzione:

- **IN**: filtra il traffico che entra nell'interfaccia (prima che venga instradato)
- **OUT**: filtra il traffico che esce dall'interfaccia (dopo l'instradamento)

```
interface GigabitEthernet0/0
 ip access-group 100 in
```

## Esempio completo — ACL su router perimetrale

```
! Scenario: rete interna 192.168.1.0/24, server web in DMZ 10.0.0.10

! Permetti agli interni di navigare su HTTP/HTTPS
access-list 110 permit tcp 192.168.1.0 0.0.0.255 any eq 80
access-list 110 permit tcp 192.168.1.0 0.0.0.255 any eq 443
! Permetti agli interni di usare DNS
access-list 110 permit udp 192.168.1.0 0.0.0.255 any eq 53
! Permetti traffico verso il server web in DMZ
access-list 110 permit tcp any host 10.0.0.10 eq 80
access-list 110 permit tcp any host 10.0.0.10 eq 443
! Blocca accesso diretto alla rete interna dall'esterno
access-list 110 deny ip any 192.168.1.0 0.0.0.255
! Deny implicito finale
access-list 110 deny ip any any
```

---

# 3️⃣ Proxy Server

## Cos'è

Un **proxy** è un intermediario che si interpone tra i client della rete interna e i server esterni. I client non comunicano direttamente con i server: inviano le richieste al proxy, che le inoltro per loro conto.

```
[Client interno] ──► [Proxy] ──► [Server esterno]
                         ↑
               Il proxy fa la richiesta
               per conto del client.
               Il server vede l'IP del proxy,
               non del client.
```

## Proxy forward (esplicito)

Il client è **configurato esplicitamente** per usare il proxy (impostazione nel browser o nel sistema operativo). Il client sa di star usando un proxy.

**Funzioni**:

- **Anonimizzazione**: il server vede l'IP del proxy, non del client → privacy
- **Filtraggio URL**: il proxy può bloccare categorie di siti (social, streaming, adulti...) — usato in reti aziendali e scolastiche
- **Caching**: salva le risposte delle richieste frequenti. La prossima volta che un client chiede la stessa risorsa, il proxy risponde dalla cache senza contattare il server esterno → riduce traffico e latenza
- **Logging**: registra tutte le richieste HTTP dei client → controllo e auditing
- **Autenticazione**: richiede credenziali prima di dare accesso a Internet
- **Content inspection**: analisi del contenuto per rilevare malware o DLP (Data Loss Prevention)

## Transparent proxy

Il client **non sa** di usare un proxy. Il traffico viene intercettato e reindirizzato al proxy tramite regole di routing o firewall (redirect sulla porta 80/443). Usato spesso dagli ISP per caching o filtraggio.

## Reverse proxy

Funziona in direzione opposta: si mette **davanti ai server** interni per proteggere e ottimizzare l'accesso dall'esterno.

```
[Client esterno] ──► [Reverse Proxy] ──► [Server 1]
                                      └──► [Server 2]
                                      └──► [Server 3]
```

**Funzioni**:

- **Load balancing**: distribuisce le richieste tra più server backend
- **SSL termination**: gestisce TLS centralmente, i server backend comunicano in HTTP non cifrato nella rete interna
- **Caching**: serve contenuti statici dalla cache senza coinvolgere i server
- **Protezione**: nasconde l'IP e la struttura dei server backend
- **WAF**: filtra richieste malevole prima che raggiungano i server

Esempi: Nginx, HAProxy, Apache (mod_proxy), Cloudflare.

## Proxy vs NAT

|  | Proxy | NAT |
| --- | --- | --- |
| **Livello OSI** | 7 (Applicazione) | 3–4 (Rete/Trasporto) |
| **Consapevolezza** | Il client può saperlo (forward) o no (transparent) | Il client non lo sa mai |
| **Contenuto** | Può leggere e modificare il payload | Modifica solo header IP/TCP |
| **Caching** | ✅ Sì | ❌ No |
| **Filtraggio URL** | ✅ Sì | ❌ No |
| **Performance** | Più overhead (deve elaborare il payload) | Minimo overhead |

---

# 4️⃣ DMZ — Demilitarized Zone

## Cos'è

La **DMZ** è una sottorete isolata che ospita i server che devono essere raggiungibili da Internet (web server, mail server, DNS pubblico, FTP server) mantenendoli **separati dalla rete interna**.

Il nome viene dalla terminologia militare: la zona demilitarizzata è una fascia di territorio tra due eserciti dove nessuno dei due ha pieno controllo.

## Architettura a tre zone

```
                  INTERNET
                     |
              [Firewall esterno]
              /              \
       DMZ (zona grigia)    BLOCCATO
  [Web server 80/443]      verso rete interna
  [Mail server 25/587]
  [DNS pubblico 53]
       |
[Firewall interno]
       |
RETE INTERNA (trusted)
  [PC utenti]
  [DB server]
  [File server]
  [Stampanti]
```

**Regole tipiche**:

- Internet → DMZ: permesso solo sulle porte dei servizi pubblici (80, 443, 25, 53)
- DMZ → Internet: permesso per aggiornamenti, risposta alle connessioni
- Internet → Rete interna: **bloccato completamente**
- Rete interna → DMZ: permesso (gli admin devono gestire i server)
- DMZ → Rete interna: **bloccato** o molto limitato (es. solo verso il DB server sulla porta specifica)
- Rete interna → Internet: permesso (con controlli)

## Implementazione con un solo firewall (three-legged)

```
     [Firewall]
    /    |     \
WAN   DMZ   LAN
```

Un solo firewall con tre interfacce (WAN, DMZ, LAN). Più economico ma se il firewall è compromesso, sia DMZ che LAN sono esposte.

## Implementazione con due firewall

```
Internet ─► [FW esterno] ─► DMZ ─► [FW interno] ─► LAN
```

Più sicura: anche se l'attaccante compromette il firewall esterno o un server in DMZ, deve ancora superare il firewall interno per raggiungere la LAN. I due firewall possono essere di vendor diversi (riduce il rischio che una vulnerabilità li colpisca entrambi).

## Perché la DMZ aumenta la sicurezza

Senza DMZ, il web server sarebbe direttamente nella LAN. Se un attaccante compromette il web server, ha accesso diretto a tutti i PC, ai file server, ai database interni. Con la DMZ, la compromissione del web server non implica automaticamente l'accesso alla LAN — l'attaccante deve ancora penetrare il firewall interno.

**Principio**: la DMZ implementa la **difesa in profondità** (defense in depth) — più strati di difesa, ciascuno indipendente.

---

# 5️⃣ NAT — Network Address Translation

## Cos'è

**NAT** è il meccanismo con cui un router traduce gli indirizzi IP privati della rete interna in un indirizzo IP pubblico per comunicare con Internet, e viceversa per le risposte.

## Il problema che risolve

Gli indirizzi IPv4 pubblici sono esauriti. Una casa o un'azienda tipicamente ha **un solo IP pubblico** assegnato dall'ISP, ma al suo interno può avere decine o centinaia di dispositivi. NAT permette a tutti di condividere quell'unico IP pubblico.

## Come funziona PAT (Port Address Translation / NAT overload)

La variante più comune di NAT è **PAT** (anche detta NAPT o NAT overload), che usa le **porte** per distinguere i flussi di più client interni.

```
PC1 (192.168.1.10:5000) ┐
                         ├► Router NAT (203.0.113.1) ► Internet
PC2 (192.168.1.20:5001) ┘
```

**Tabella NAT** (mantenuta dal router):

| IP interno | Porta interna | IP pubblico | Porta esterna | IP destinazione | Porta destinazione |
| --- | --- | --- | --- | --- | --- |
| 192.168.1.10 | 5000 | 203.0.113.1 | 10001 | 93.184.216.34 | 80 |
| 192.168.1.20 | 5001 | 203.0.113.1 | 10002 | 93.184.216.34 | 80 |

Quando arriva la risposta sulla porta esterna 10001, il router sa di doverla girare a 192.168.1.10:5000.

## NAT come sicurezza

NAT fornisce un **effetto collaterale di sicurezza**: i dispositivi interni non sono direttamente raggiungibili da Internet (non hanno un IP pubblico). Un attaccante esterno non può iniziare una connessione verso un host interno — il router non sa dove instradarla.

> ⚠️ NAT **non è** un meccanismo di sicurezza intenzionale — è una soluzione all'esaurimento degli indirizzi IPv4. Non sostituisce un firewall.
> 

---

# 6️⃣ Port Forwarding

## Cos'è

Il **port forwarding** (o destination NAT / DNAT) è una configurazione del router/firewall che **reindirizza il traffico** in ingresso su una specifica porta pubblica verso un host e una porta specifici nella rete interna.

Risolve il problema inverso di NAT: NAT permette agli interni di uscire, il port forwarding permette agli esterni di entrare — ma solo su porte specifiche verso host specifici.

## Come funziona

```
Client esterno
│
│ Richiesta verso 203.0.113.1:8080
▼
[Router/Firewall NAT]
│ Regola: traffico in ingresso su porta 8080 → reindirizza a 192.168.1.50:80
▼
[Server web interno 192.168.1.50:80]
```

Il client esterno vede solo l'IP pubblico del router. Non sa nulla dell'IP interno del server.

## Configurazione tipica (interfaccia router home)

| Servizio | Porta esterna | IP interno | Porta interna |
| --- | --- | --- | --- |
| Web server | 80 | 192.168.1.50 | 80 |
| Web server HTTPS | 443 | 192.168.1.50 | 443 |
| SSH | 2222 | 192.168.1.100 | 22 |
| Minecraft server | 25565 | 192.168.1.30 | 25565 |
| NAS | 5000 | 192.168.1.20 | 5000 |

> 💡 **Best practice**: non esporre la porta SSH standard (22) su Internet — viene scansionata e attaccata in continuazione. Usare una porta esterna non standard (es. 2222) riduce il rumore degli attacchi automatizzati (security through obscurity, non una difesa reale, ma riduce il log di brute-force).
> 

## Usi tipici del port forwarding

- Ospitare un server web, game server, FTP server, NAS su una connessione domestica
- Accesso remoto SSH a un server interno
- Telecamere IP accessibili da remoto
- Redirect di servizi su porte non standard

## Port forwarding vs DMZ host

I router home hanno spesso un'opzione chiamata **"DMZ host"** (non confondere con la DMZ enterprise): designa un singolo host interno che riceve **tutto il traffico in ingresso** che non corrisponde ad altre regole di port forwarding. Espone completamente quell'host a Internet — utile solo per console di gioco o test, mai per server reali.

---

# 🔗 Architettura Completa — Come si Integrano

```
               INTERNET
                  |
            IP pubblico
         203.0.113.1
                  |
    [FIREWALL ESTERNO / ROUTER]
    - ACL: permetti 80,443 verso DMZ
    - ACL: permetti 25 verso mail server
    - Port forwarding: 80 → 10.0.0.10
    - NAT: rete interna → IP pubblico
    - Stateful: blocca tutto non richiesto
           /            \
  DMZ 10.0.0.0/24     BLOCCATO
[Web server 10.0.0.10]   verso LAN
[Mail server 10.0.0.11]
[DNS 10.0.0.12]
           |
[PROXY / FIREWALL INTERNO]
- Forward proxy per gli utenti LAN
- Filtraggio URL
- ACL: blocca DMZ → LAN (eccetto DB)
           |
    LAN 192.168.1.0/24
  [PC utenti]
  [DB server 192.168.1.100]
  [File server]
```

**Flusso di una richiesta HTTP esterna**:

1. Client chiede `http://203.0.113.1`
2. Firewall esterno: ACL permette TCP/80 in ingresso, port forwarding → 10.0.0.10
3. Il web server in DMZ elabora la richiesta
4. Se il web server ha bisogno di dati: apre una connessione verso il DB nella LAN (il firewall interno ha una regola specifica che permette solo questa connessione)
5. La risposta torna al client attraverso NAT

**Flusso di un utente interno che naviga**:

1. PC 192.168.1.10 vuole accedere a [google.com](http://google.com)
2. Il proxy intercetta la richiesta (transparent o esplicito)
3. Il proxy controlla la policy URL (non è un sito bloccato)
4. Il proxy apre la connessione verso [google.com](http://google.com) usando l'IP pubblico (NAT)
5. La risposta passa attraverso il proxy (caching, logging)
6. Il proxy risponde al PC interno

---

# ❓ Domande tipiche da orale

- Differenza tra firewall stateless e stateful
    
    Il firewall stateless analizza ogni pacchetto in modo indipendente, senza sapere se fa parte di una connessione esistente. È veloce ma limitato: per permettere il traffico di ritorno bisogna aprire esplicitamente porte in ingresso.
    
    Il firewall stateful mantiene una tabella delle connessioni attive. Riconosce automaticamente i pacchetti di risposta come appartenenti a connessioni legittime e li lascia passare senza regole esplicite. È molto più sicuro e gestisce correttamente il traffico bidirezionale.
    
- Cos'è una ACL e come funziona l'ordine delle regole?
    
    Una ACL è una lista ordinata di regole (permit/deny) applicate a un'interfaccia di rete. Le regole vengono valutate in ordine: la prima che corrisponde al pacchetto viene applicata, le successive ignorate. Se nessuna corrisponde si applica il deny implicito finale. L'ordine è critico: una regola troppo permissiva messa prima di una restrittiva la rende inutile.
    
- Differenza tra proxy forward e reverse proxy
    
    Il proxy forward si mette tra i client interni e Internet: i client lo usano per uscire (navigazione), il server esterno vede l'IP del proxy. Funzioni: caching, filtraggio URL, anonimizzazione, logging.
    
    Il reverse proxy si mette davanti ai server interni: i client esterni lo raggiungono, lui distribuisce le richieste ai server backend. Funzioni: load balancing, SSL termination, caching, protezione.
    
- Perché si usa la DMZ? Non basta un firewall?
    
    Senza DMZ, i server pubblici starebbero direttamente nella LAN. Se un attaccante compromette il web server, ha accesso immediato a tutta la rete interna (PC, database, file server). La DMZ isola i server pubblici: anche se compromessi, l'attaccante deve superare un secondo firewall per raggiungere la LAN interna. Implementa la difesa in profondità.
    
- Cos'è il port forwarding e perché serve?
    
    Il port forwarding è una regola NAT che reindirizza il traffico in ingresso su una porta pubblica verso un host e porta specifici nella rete interna. Serve perché con NAT i dispositivi interni non hanno IP pubblici e non sono raggiungibili dall'esterno. Il port forwarding è l'eccezione controllata: apre un "buco" specifico nel NAT solo per il servizio che deve essere raggiungibile.
    
- NAT è un meccanismo di sicurezza?
    
    NAT non è progettato come meccanismo di sicurezza — è una soluzione all'esaurimento degli indirizzi IPv4. Il fatto che impedisca connessioni in ingresso non richieste è un effetto collaterale, non l'obiettivo. NAT non filtra il traffico, non ispeziona i pacchetti, non blocca malware. Non sostituisce un firewall. Con IPv6 non esiste NAT (ogni dispositivo ha un IP pubblico), ma la sicurezza si ottiene con il firewall.
    
- Differenza tra DMZ enterprise e DMZ host sui router home
    
    La DMZ enterprise è una sottorete separata tra due firewall, con regole precise su cosa può entrare e uscire. Offre isolamento reale.
    
    La DMZ host sui router domestici è una funzione completamente diversa: espone un singolo host a tutto il traffico in ingresso che non ha altre regole. Non è una vera DMZ — è essenzialmente togliere il NAT a quell'host. Utile per console di gioco, pericoloso per qualsiasi cosa con dati sensibili.
    

---

> 📌 **Collegamento con altri argomenti**: CIA e attacchi — 15 giu | Crittografia e TLS — 16 giu | VPN, IPSec, HTTPS — 17 giu (prossimo)
>