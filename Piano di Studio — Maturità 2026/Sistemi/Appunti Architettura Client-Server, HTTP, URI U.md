# Panoramica

Questa pagina copre il livello applicazione del modello OSI: come è strutturata la comunicazione web, come funziona HTTP, cosa sono URI e URL, e come si è evoluto il Web dalla sua nascita.

---
# Architettura Client-Server

## Cos'è

Il modello **client-server** è il paradigma dominante nelle reti. Divide i nodi in due ruoli distinti:

- **Client**: inizia la comunicazione, fa richieste, consuma servizi. Non deve essere sempre attivo.
- **Server**: aspetta le richieste, le elabora e risponde. Deve essere sempre attivo e raggiungibile.

La comunicazione è **asimmetrica**: è sempre il client a iniziare, mai il server (salvo tecniche come WebSocket o long polling).

## Caratteristiche del server

- Ha un **indirizzo IP fisso** (o un hostname DNS stabile)
- Ascolta su una **porta ben nota** (es. 80 per HTTP, 443 per HTTPS)
- Può servire **molti client contemporaneamente** (concorrenza tramite thread, processi o I/O asincrono)
- Spesso replicato su più macchine fisiche per scalabilità e fault tolerance

## Caratteristiche del client

- Ha indirizzo IP **dinamico** (assegnato dal DHCP)
- Apre una connessione verso il server, poi la chiude
- Non è direttamente raggiungibile dall'esterno (spesso dietro NAT)
- Esempi: browser, app mobile, client FTP

## Confronto con altri modelli

| Modello | Descrizione | Esempi |
| --- | --- | --- |
| **Client-Server** | Ruoli fissi, server centralizzato | Web, email, DNS |
| **Peer-to-Peer (P2P)** | Ogni nodo è sia client che server | BitTorrent, blockchain |
| **Ibrido** | P2P con server centrale per il coordinamento | Skype (storico), Spotify |

## Tier architetturali

Nelle applicazioni web moderne l'architettura client-server si articola in livelli (**tier**):

- 2-tier (client ↔ server)

    Il client comunica direttamente con il server che gestisce sia la logica applicativa che i dati. Semplice ma poco scalabile.

    **Esempio**: applicazione desktop che accede direttamente a un database.

- 3-tier (client ↔ application server ↔ database server)

    Si aggiunge un livello intermedio (application server o web server) che separa la logica di business dal database.

    - **Livello 1 — Presentation tier**: il client (browser)
    - **Livello 2 — Logic tier**: web server + applicazione (es. PHP, Node.js)
    - **Livello 3 — Data tier**: database (MySQL, PostgreSQL)

    **Vantaggi**: scalabilità, sicurezza (il DB non è esposto direttamente), manutenibilità.

- N-tier / microservizi

    Ulteriore scomposizione: ogni funzionalità è un servizio indipendente (autenticazione, pagamenti, catalogo...). Usato nelle grandi piattaforme (Amazon, Netflix).


---

# URI e URL

## URI — Uniform Resource Identifier

Un **URI** è una stringa che identifica univocamente una risorsa. È il concetto generale.

Si divide in due sottotipi:

- **URL** (Uniform Resource **Locator**): identifica la risorsa *e* dice come raggiungerla (protocollo + posizione)
- **URN** (Uniform Resource **Name**): identifica la risorsa per nome, indipendentemente dalla posizione (es. `urn:isbn:978-88-386-6525-8`)

> In pratica, nella navigazione web si usano sempre URL. URI è il termine formale che li include entrambi.

## Struttura di un URL

```
schema://userinfo@host:porta/percorso?query#fragment
```

| Componente | Descrizione | Esempio |
| --- | --- | --- |
| **schema** | Protocollo da usare | `https`, `http`, `ftp`, `mailto` |
| **userinfo** | Credenziali opzionali (raro nel web moderno) | `user:password@` |
| **host** | Nome di dominio o indirizzo IP del server | `www.example.com`, `192.168.1.1` |
| **porta** | Porta TCP (opzionale se è quella di default) | `:80`, `:443`, `:8080` |
| **percorso** | Posizione della risorsa sul server | `/articoli/reti/index.html` |
| **query** | Parametri opzionali (coppie chiave=valore) | `?id=42&lang=it` |
| **fragment** | Ancora nella pagina (processata solo dal browser, non inviata al server) | `#sezione-2` |

**Esempio completo**:

```
https://www.example.com:443/corso/sistemi?capitolo=3&pagina=12#http
```

- Schema: `https`
- Host: `www.example.com`
- Porta: `443` (default per HTTPS, di solito omessa)
- Percorso: `/corso/sistemi`
- Query: `capitolo=3&pagina=12`
- Fragment: `#http`

## Encoding dell'URL

I caratteri speciali non ammessi nell'URL (spazi, accenti, simboli) vengono codificati con **percent-encoding**: ogni carattere diventa `%XX` dove XX è il valore esadecimale del byte.

Esempi: spazio → `%20`, `@` → `%40`, `/` nel path → `%2F`

---

# Protocollo HTTP

## Cos'è

**HTTP** (HyperText Transfer Protocol) è il protocollo applicativo alla base del Web. Definisce come client e server si scambiano messaggi per trasferire risorse (pagine HTML, immagini, JSON, ecc.).

- Livello OSI: **7 (Applicazione)**
- Trasporto sottostante: **TCP** (porta 80 per HTTP, 443 per HTTPS)
- Caratteristica fondamentale: **stateless** — ogni richiesta è indipendente, il server non ricorda le precedenti

## Modello richiesta-risposta

Ogni interazione HTTP è una coppia:

1. Il client invia una **HTTP Request**
2. Il server risponde con una **HTTP Response**

## Struttura di una HTTP Request

```
METODO /percorso HTTP/versione
Header1: valore
Header2: valore
[riga vuota]
[body opzionale]
```

**Esempio reale**:

```
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
Accept: text/html
Connection: keep-alive
```

## Metodi HTTP

| Metodo | Scopo | Body nella richiesta | Idempotente | Safe |
| --- | --- | --- | --- | --- |
| **GET** | Recupera una risorsa | No | Sì | Sì |
| **POST** | Invia dati al server (crea risorsa) | Sì | No | No |
| **PUT** | Sostituisce completamente una risorsa | Sì | Sì | No |
| **PATCH** | Modifica parzialmente una risorsa | Sì | No | No |
| **DELETE** | Elimina una risorsa | No | Sì | No |
| **HEAD** | Come GET ma senza body nella risposta | No | Sì | Sì |
| **OPTIONS** | Chiede quali metodi supporta il server | No | Sì | Sì |

> **Idempotente**: fare la stessa richiesta N volte produce lo stesso risultato di farla una volta sola. **Safe**: non modifica lo stato del server.

## Struttura di una HTTP Response

```
HTTP/versione CODICE messaggio-stato
Header1: valore
Header2: valore
[riga vuota]
[body: HTML, JSON, immagine...]
```

**Esempio reale**:

```
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 1452
Date: Mon, 08 Jun 2026 10:00:00 GMT

<!DOCTYPE html>...
```

## Codici di stato HTTP

| Classe | Range | Significato | Esempi comuni |
| --- | --- | --- | --- |
| **1xx** | 100–199 | Informational — richiesta ricevuta, in elaborazione | 100 Continue |
| **2xx** | 200–299 | Success — richiesta elaborata con successo | 200 OK, 201 Created, 204 No Content |
| **3xx** | 300–399 | Redirection — il client deve fare un'altra richiesta | 301 Moved Permanently, 302 Found, 304 Not Modified |
| **4xx** | 400–499 | Client Error — errore nella richiesta del client | 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found |
| **5xx** | 500–599 | Server Error — errore interno del server | 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable |

## Header HTTP principali

- Header di richiesta


    | Header | Descrizione | Esempio |
    | --- | --- | --- |
    | `Host` | Nome del server (obbligatorio in HTTP/1.1) | `Host: www.example.com` |
    | `User-Agent` | Identifica il client (browser, bot...) | `User-Agent: Mozilla/5.0` |
    | `Accept` | Formati accettati nella risposta | `Accept: text/html, application/json` |
    | `Accept-Language` | Lingua preferita | `Accept-Language: it-IT, en;q=0.9` |
    | `Authorization` | Credenziali di autenticazione | `Authorization: Bearer <token>` |
    | `Cookie` | Cookie inviati al server | `Cookie: session=abc123` |
    | `Content-Type` | Tipo del body nella richiesta | `Content-Type: application/json` |
    | `Content-Length` | Dimensione del body in byte | `Content-Length: 348` |
- Header di risposta


    | Header | Descrizione | Esempio |
    | --- | --- | --- |
    | `Content-Type` | Tipo del contenuto restituito | `Content-Type: text/html; charset=UTF-8` |
    | `Content-Length` | Dimensione del body | `Content-Length: 1452` |
    | `Set-Cookie` | Imposta un cookie nel browser | `Set-Cookie: session=abc123; HttpOnly` |
    | `Location` | URL di redirect (usato con 3xx) | `Location: https://www.example.com/new` |
    | `Cache-Control` | Istruzioni sulla cache | `Cache-Control: max-age=3600` |
    | `Server` | Software del server | `Server: Apache/2.4` |
    | `Strict-Transport-Security` | Forza HTTPS | `HSTS: max-age=31536000` |

## HTTP stateless e gestione dello stato

HTTP è **stateless**: il server non ricorda nulla tra una richiesta e la successiva. Per mantenere lo stato (es. utente loggato, carrello) si usano:

- **Cookie**: piccoli file di testo salvati nel browser, inviati automaticamente ad ogni richiesta verso quel dominio
- **Session**: il server crea una sessione con un ID univoco, l'ID viene salvato in un cookie, i dati restano sul server
- **Token JWT**: token firmato che contiene le informazioni dell'utente, inviato nell'header `Authorization`

## Evoluzione di HTTP

| Versione | Anno | Novità principali |
| --- | --- | --- |
| **HTTP/0.9** | 1991 | Solo GET, solo HTML, nessun header |
| **HTTP/1.0** | 1996 | Header, metodi POST e HEAD, codici di stato, Content-Type. Una connessione TCP per richiesta. |
| **HTTP/1.1** | 1997 | **Persistent connection** (keep-alive): la connessione TCP rimane aperta per più richieste. Pipelining (limitato). Header `Host` obbligatorio. Chunked transfer. |
| **HTTP/2** | 2015 | Multiplexing: più richieste in parallelo sulla stessa connessione TCP. Compressione degli header (HPACK). Server push. Binario (non più testuale). |
| **HTTP/3** | 2022 | Abbandona TCP: usa **QUIC** (basato su UDP). Elimina il problema del head-of-line blocking. Connessione più rapida (0-RTT). TLS integrato. |

> **Head-of-line blocking in HTTP/1.1**: con il pipelining, se una richiesta si blocca, tutte le successive aspettano. HTTP/2 risolve con il multiplexing a livello applicativo; HTTP/3 risolve anche a livello di trasporto (QUIC su UDP gestisce ogni stream indipendentemente).

## HTTPS

**HTTPS** = HTTP + **TLS** (Transport Layer Security). Il payload HTTP viene cifrato da TLS prima di essere passato a TCP.

- Garantisce **confidenzialità** (nessuno può leggere il traffico), **integrità** (nessuno può modificarlo), **autenticazione** (il certificato digitale del server prova l'identità)
- Porta default: **443**
- Il certificato è emesso da una **CA** (Certificate Authority) fidata
- Oggi è lo standard de facto: i browser marcano HTTP come "non sicuro"

---

# Il Web e la sua storia

## Le origini — ARPANET e Internet

| Anno | Evento |
| --- | --- |
| **1969** | ARPANET: prima rete a commutazione di pacchetto, 4 nodi (UCLA, Stanford, UCSB, Utah). Prima trasmissione: "LO" (tentativo di "LOGIN", il sistema craşşò dopo due lettere). |
| **1971** | Prima email su ARPANET (Ray Tomlinson inventa l'uso della `@` per separare utente e host) |
| **1974** | TCP/IP definito da Cerf e Kahn nel paper "A Protocol for Packet Network Intercommunication" |
| **1983** | ARPANET adotta TCP/IP (**"The Big Switch"**). Nasce formalmente Internet. |
| **1984** | DNS introdotto da Paul Mockapetris — sostituisce il file HOSTS.TXT centralizzato |
| **1991** | Tim Berners-Lee pubblica il primo sito web al mondo su un NeXT computer al CERN |

## La nascita del Web — Tim Berners-Lee al CERN

Nel **1989** Tim Berners-Lee, fisico informatico al CERN di Ginevra, propose un sistema per condividere documenti tra ricercatori. La proposta si chiamava *"Information Management: A Proposal"* e il suo capo la commentò con *"Vague but exciting"*.

Nel **1991** vengono definiti e pubblicati i tre pilastri del Web:

- **HTML** (HyperText Markup Language): linguaggio per strutturare i documenti
- **HTTP** (HyperText Transfer Protocol): protocollo per trasferirli
- **URL** (Uniform Resource Locator): sistema per identificarli e localizzarli

Il primo sito web è ancora online: [http://info.cern.ch](http://info.cern.ch)

## Evoluzione del Web

- Web 1.0 (1991–2004) — Web statico
    - Pagine HTML statiche, solo testo e immagini
    - Comunicazione **unidirezionale**: il server pubblica, l'utente legge
    - Nessuna interazione, nessun database dinamico
    - Browser principali: Mosaic (1993, primo browser grafico), Netscape Navigator (1994)
    - **1994**: nasce il W3C (World Wide Web Consortium) fondato da Berners-Lee per standardizzare il Web
    - **1995**: JavaScript creato da Brendan Eich in 10 giorni per Netscape. CSS 1 pubblicato.
    - **1998**: Google fondato da Page e Brin a Stanford
- Web 2.0 (2004–oggi) — Web dinamico e sociale
    - Il termine è coniato da Tim O'Reilly nel 2004
    - Pagine dinamiche generate lato server (PHP, ASP, JSP)
    - **AJAX** (Asynchronous JavaScript and XML): permette di aggiornare parti della pagina senza ricaricarla tutta. Rivoluziona l'esperienza utente. (Gmail, Google Maps lo usano nel 2005)
    - **User-generated content**: gli utenti non sono più solo lettori ma produttori (blog, Wikipedia, YouTube, Facebook)
    - **2004**: Facebook fondato da Zuckerberg
    - **2005**: YouTube fondato
    - **2006**: Twitter fondato
    - API REST: i servizi espongono interfacce programmatiche che altri possono usare
- Web 3.0 / Web semantico — futuro
    - Concetto proposto da Berners-Lee: dati strutturati e collegati in modo che le macchine li capiscano (RDF, ontologie)
    - In senso popolare il termine è usato per il Web decentralizzato basato su blockchain
    - Non ancora una realtà consolidata

## Browser principali e la guerra dei browser

| Anno | Evento |
| --- | --- |
| **1993** | **Mosaic**: primo browser con supporto grafico (immagini inline). Sviluppato da Marc Andreessen all'NCSA. |
| **1994** | **Netscape Navigator**: domina il mercato con oltre il 90% degli utenti |
| **1995** | **Internet Explorer** di Microsoft: Microsoft lo bundla con Windows 95. Inizia la prima guerra dei browser. |
| **1998** | Netscape rilascia il codice sorgente → nasce il progetto **Mozilla** |
| **2003** | **Safari** di Apple (basato su KHTML, poi WebKit) |
| **2004** | **Firefox** 1.0 (da Mozilla). Ruba quote a IE. |
| **2008** | **Chrome** di Google (motore V8 per JS, molto più veloce). Domina il mercato. |
| **2015** | Microsoft sostituisce IE con **Edge** (poi rifatto su Chromium nel 2020) |

## Tecnologie fondamentali del Web

| Tecnologia | Ruolo | Livello |
| --- | --- | --- |
| **HTML** | Struttura del contenuto | Client (markup) |
| **CSS** | Presentazione visiva | Client (stile) |
| **JavaScript** | Comportamento e interattività | Client (logica) |
| **HTTP/HTTPS** | Trasporto del contenuto | Protocollo applicativo |
| **DNS** | Risoluzione nomi → IP | Infrastruttura |
| **TCP/IP** | Trasporto affidabile | Trasporto/Rete |
| **PHP/Node.js/Python** | Generazione dinamica lato server | Server (logica) |
| **SQL/NoSQL** | Persistenza dei dati | Server (dati) |

---

# Domande tipiche da orale

- Cos'è HTTP e perché è stateless?

    HTTP è il protocollo applicativo del Web, usato per trasferire risorse tra client e server. È stateless perché ogni richiesta è completamente indipendente: il server non conserva memoria delle richieste precedenti. Questo lo rende semplice e scalabile, ma richiede meccanismi aggiuntivi (cookie, sessioni, token) per mantenere lo stato dell'utente.

- Differenza tra HTTP e HTTPS

    HTTP trasmette i dati in chiaro; chiunque intercetti il traffico può leggerlo. HTTPS aggiunge un livello TLS che cifra il payload: garantisce confidenzialità (i dati non sono leggibili), integrità (non modificabili) e autenticazione (il certificato digitale prova l'identità del server). HTTPS usa la porta 443 invece della 80.

- Differenza tra GET e POST

    GET recupera una risorsa: i parametri vanno nella query string dell'URL, non ha body, è idempotente e safe (non modifica lo stato del server). POST invia dati al server: i dati vanno nel body della richiesta, non è idempotente (due POST uguali possono creare due risorse), usato per form, upload, creazione di risorse.

- Cosa succede quando digito un URL nel browser?
    1. Il browser analizza l'URL (schema, host, percorso)
    2. **Risoluzione DNS**: chiede al resolver DNS l'IP corrispondente al hostname
    3. **Connessione TCP**: three-way handshake con il server (SYN, SYN-ACK, ACK)
    4. Se HTTPS: **TLS handshake** (scambio certificati, negoziazione chiave)
    5. Il browser invia la **HTTP Request** (es. `GET /index.html HTTP/1.1`)
    6. Il server elabora e invia la **HTTP Response** (es. `200 OK` + HTML)
    7. Il browser riceve l'HTML, lo parsa, richiede le risorse collegate (CSS, JS, immagini) con ulteriori richieste HTTP
    8. Il browser renderizza la pagina
- Chi ha inventato il Web e quando?

    Tim Berners-Lee, fisico informatico al CERN di Ginevra. Propose il sistema nel 1989, definì HTML, HTTP e URL nel 1991 e pubblì il primo sito web. Il Web non è Internet: Internet è l'infrastruttura di rete (TCP/IP, nata nel 1983 da ARPANET), il Web è un servizio che ci gira sopra.

- Differenza tra Web e Internet

    Internet è la rete fisica e logica globale: cavi, router, protocolli TCP/IP, DNS. Nasce da ARPANET nel 1983. Il Web è uno dei servizi che girano su Internet: usa HTTP per trasferire documenti HTML collegati da hyperlink. Altri servizi su Internet: email (SMTP/POP3/IMAP), FTP, SSH, VoIP. Confondere i due è un errore classico.


---

> **Collegamento con altri argomenti**: DNS, SMTP, POP3, ICMP, FTP — 14 giu | Cybersecurity e HTTPS — 15 giu | Cookie e sessioni → Informatica (già studiato)
