---
subject: sistemi
tags:
  - sistemi
  - reti
  - maturita-2026
---
# Panoramica

Classificare una rete significa descriverla secondo **tre assi distinti**:

1. **Criteri strutturali** — com'è fatta fisicamente e logicamente (estensione, topologia)
2. **Servizi offerti** — cosa fa la rete (trasmissione, accesso, sicurezza)
3. **Standard tecnologici** — quali protocolli e tecnologie implementano la comunicazione

Questi tre assi sono **ortogonali**: puoi avere una LAN (strutturale) con topologia a stella (strutturale) che usa Ethernet (standard) e offre accesso a Internet (servizio). Non si escludono a vicenda.

---

# Classificazione Strutturale

La classificazione strutturale risponde alla domanda: **quanto è grande la rete e com'è organizzata nello spazio?**

## 1.1 — Estensione geografica

| Sigla | Nome | Estensione tipica | Esempi concreti |
| --- | --- | --- | --- |
| **PAN** | Personal Area Network | < 10 m | Bluetooth tra telefono e auricolari, USB |
| **LAN** | Local Area Network | 10 m – 1 km | Rete scolastica, ufficio, appartamento |
| **MAN** | Metropolitan Area Network | 1 km – 100 km | Rete di un campus universitario, rete cittadina |
| **WAN** | Wide Area Network | > 100 km (fino a globale) | Internet, reti aziendali intercontinentali |

> **Osservazione critica**: i confini tra LAN, MAN, WAN sono sfumati. Quello che conta davvero è la **tecnologia** e il **gestore**, non i km esatti. Una fibra ottica che collega due edifici a 500 m può essere gestita come WAN se passa da un ISP.

## 1.2 — Topologia

La **topologia** descrive la struttura di una rete: come i nodi sono collegati e come scorrono i dati tra loro.

È fondamentale distinguere due piani:

- **Topologia fisica**: la struttura reale del cablaggio — dove passano i cavi, come sono disposti fisicamente i dispositivi
- **Topologia logica**: il percorso che seguono i dati — che può essere completamente diverso da quello fisico

> **Esempio classico**: una rete con **hub** ha topologia fisica a stella (tutti i cavi convergono sull'hub), ma topologia logica a **bus** (l'hub non smista: riceve il segnale e lo ritrasmette su tutte le porte contemporaneamente, esattamente come farebbe un bus condiviso). Con uno **switch** invece la topologia logica diventa punta-a-punta (punto-punto): il frame viene inoltrato solo sulla porta del destinatario.

### Topologie fisiche principali

- Bus

    **Com'è fatta**: tutti i nodi sono collegati a un unico cavo condiviso (il "bus"). Ai due capi ci sono dei **terminatori** che assorbono il segnale e impediscono riflessioni.

    **Come funziona**: quando un nodo trasmette, il segnale si propaga in entrambe le direzioni lungo il cavo e raggiunge tutti gli altri nodi. Ogni nodo legge il frame, verifica se è destinato a lui, e lo scarta o lo processa.

    **Il problema delle collisioni**: se due nodi trasmettono contemporaneamente, i segnali si sovrappongono e si corrompono (collisione). Per questo si usa **CSMA/CD**: prima di trasmettere si ascolta il canale, e se avviene una collisione si ritrasmette dopo un backoff casuale.

    **Punto di rottura critico**: basta che il cavo si spezzi in qualsiasi punto (anche nel mezzo) e la rete cade tutta, perché il segnale non arriva più ai terminatori e si generano riflessioni che corrompono tutto il traffico.

    **Vantaggi**: economica, semplice da cablare, pochi componenti

    **Svantaggi**: singolo punto di failure sul cavo, collisioni frequenti, difficile troubleshooting, non scalabile

    **Usata in**: Ethernet 10Base2 (coassiale "thin") e 10Base5 (coassiale "thick") — entrambe obsolete

- Stella (Star)

    **Com'è fatta**: ogni nodo ha un cavo dedicato che lo collega direttamente a un **dispositivo centrale** (switch, hub, o access point). Nessun cavo è condiviso tra più nodi.

    **Come funziona con hub**: l'hub è passivo (livello 1). Riceve un segnale su una porta e lo ritrasmette su tutte le altre porte. Non ha intelligenza: non sa chi sono i destinatari, non ha MAC table. Risultato: traffico broadcast inutile, collisioni possibili, sicurezza zero.

    **Come funziona con switch**: lo switch opera a livello 2. Impara gli indirizzi MAC dei dispositivi collegati costruendo una **MAC address table** (o CAM table). Quando riceve un frame, lo manda solo sulla porta del destinatario. Nessuna collisione (ogni link è full-duplex), nessun traffico inutile.

    **Punto di rottura critico**: se il dispositivo centrale cade, tutta la rete è isolata. Un singolo nodo che si guasta non influenza gli altri.

    **Vantaggi**: guasto di un nodo non abbatte la rete; aggiungere/rimuovere nodi è semplice; troubleshooting facile (isoli il cavo problematico); con switch: no collisioni, performance elevate

    **Svantaggi**: richiede più cablaggio rispetto al bus; se cade il centro, cade tutto

    **Usata in**: **quasi tutte le LAN moderne** (switch Ethernet), Wi-Fi (l'Access Point è il centro della stella wireless)

- Anello (Ring)

    **Com'è fatta**: i nodi sono collegati in sequenza formando un anello chiuso. Ogni nodo ha esattamente due vicini: il precedente e il successivo.

    **Come funziona**: i dati circolano in una sola direzione (anello semplice) o in entrambe (anello doppio / dual ring). Ogni nodo funziona da **ripetitore**: riceve il segnale, lo amplifica e lo ritrasmette al nodo successivo.

    **Accesso al mezzo — Token Passing**: per evitare le collisioni, l'accesso al canale è regolato da un **token** (gettone), un frame speciale che circola nell'anello. Solo il nodo che detiene il token può trasmettere. Finito di trasmettere, il token viene liberato e passa al nodo successivo. Risultato: accesso deterministico, nessuna collisione, latenza prevedibile.

    **Punto di rottura critico**: in un anello semplice, se un singolo nodo o cavo si guasta, l'anello si interrompe e la rete cade. Negli anelli doppi (es. FDDI) il guasto viene bypassato usando il secondo anello.

    **Vantaggi**: prestazioni prevedibili e costanti (utile in ambienti industriali o real-time), nessuna collisione con token passing, uso efficiente della banda sotto carico elevato

    **Svantaggi**: un guasto interrompe l'anello (se non doppio); aggiungere o rimuovere nodi richiede interruzione della rete

    **Usata in**: Token Ring (IBM, 4/16 Mbps — anni '80-'90), FDDI (Fiber Distributed Data Interface, 100 Mbps su fibra, anello doppio), SDH/SONET nelle dorsali WAN

- Maglia (Mesh)

    **Com'è fatta**: ogni nodo ha connessioni dirette verso uno o più altri nodi. Esistono due varianti:

    - **Full mesh (maglia completa)**: ogni nodo è collegato direttamente a tutti gli altri. Per n nodi servono **n·(n−1)/2** collegamenti (es. 5 nodi → 10 link, 10 nodi → 45 link).
    - **Partial mesh (maglia parziale)**: solo alcuni nodi hanno connessioni ridondanti. Il compromesso pratico tra costo e ridondanza.

    **Come funziona**: non esiste un percorso unico tra due nodi. I **protocolli di routing** (es. OSPF, BGP) calcolano il percorso ottimale e possono instradare il traffico su percorsi alternativi in caso di guasto.

    **Tolleranza ai guasti**: è la topologia più robusta. Se un link o un nodo cade, il traffico viene reindirizzato automaticamente su un altro percorso. È per questo che Internet è stata progettata con questa filosofia.

    **Vantaggi**: alta ridondanza, nessun singolo punto di failure, tolleranza ai guasti, alta disponibilità

    **Svantaggi**: costo elevatissimo in full mesh (il numero di link cresce quadraticamente con i nodi); gestione e configurazione complessa

    **Usata in**: Internet (backbone dei provider), reti militari, reti critiche che non possono permettersi downtime, reti Wi-Fi mesh domestiche (es. Google Nest WiFi)

- Albero (Tree) / Gerarchica

    **Com'è fatta**: è una generalizzazione della stella su più livelli. I nodi sono organizzati in una gerarchia ad albero: c'è un nodo radice (root), poi nodi intermedi (switch di distribuzione), poi le foglie (PC, stampanti, ecc.).

    **Come funziona**: ogni nodo comunica con i propri vicini diretti. Il traffico verso nodi in rami diversi dell'albero deve risalire fino al nodo antenato comune.

    **Esempio concreto — rete scolastica**:

    - **Livello 0 (root)**: router/firewall di istituto
    - **Livello 1**: switch di core (uno per edificio)
    - **Livello 2**: switch di distribuzione (uno per piano)
    - **Livello 3 (foglie)**: PC, stampanti, AP Wi-Fi

    **Punto di rottura**: se cade un nodo intermedio, tutto il sottoalbero sotto di lui è isolato. Più è in alto nella gerarchia il guasto, più dispositivi vengono disconnessi.

    **Vantaggi**: scalabile (si aggiungono rami senza toccare il resto), gestione gerarchica e strutturata, facile da documentare

    **Svantaggi**: dipendenza dai nodi intermedi; latenza leggermente maggiore tra foglie di rami diversi

    **Usata in**: quasi tutte le reti aziendali e scolastiche reali


### Tabella comparativa

| Topologia | Ridondanza | Scalabilità | Costo | Fault tolerance | Dove si usa oggi |
| --- | --- | --- | --- | --- | --- |
| Bus | Nulla | Pessima | Bassissimo | Nulla | Obsoleta |
| Stella | Solo se switch ridondanti | Alta | Media | Media (dipende dal centro) | LAN moderne |
| Anello | Solo con dual ring | Media | Media | Media (dual ring: buona) | Dorsali WAN (SDH) |
| Maglia | Massima | Alta | Elevato | Massima | Internet, backbone |
| Albero | Dipende dalla gerarchia | Alta | Media | Media | Reti aziendali/scolastiche |

## 1.3 — Mezzo trasmissivo

| Mezzo | Banda tipica | Distanza massima | Note |
| --- | --- | --- | --- |
| Coppie intrecciate Cat 5e (UTP) | 1 Gbps | 100 m | Standard minimo per Gigabit Ethernet; economico, diffusissimo nelle LAN |
| Coppie intrecciate Cat 6 (UTP/STP) | 1 Gbps (10 Gbps fino a 55 m) | 100 m (10G: 55 m) | Setto interno riduce il crosstalk; comune nelle installazioni recenti |
| Coppie intrecciate Cat 6a (STP) | 10 Gbps | 100 m | Schermatura completa; usato per 10GbE full distance o ambienti con forti interferenze |
| Coppie intrecciate Cat 7 / Cat 8 | 10–40 Gbps | 100 m (Cat 7) / 30 m (Cat 8) | Cat 8 per uplink tra switch in data center; richiede connettori GG45 o TERA |
| Cavo coassiale | fino a 10 Gbps | centinaia di m | Schermato, usato in TV via cavo e Ethernet storica |
| Fibra ottica | fino a Tbps | decine di km (monomodale) | Immune a EMI, alta velocità, alto costo |
| Wi-Fi (IEEE 802.11) | fino a ~9.6 Gbps (Wi-Fi 6) | ~100 m indoor | Interferenze, condivisione del mezzo |
| Bluetooth | fino a 3 Mbps (classic), 2 Mbps (BLE) | ~10 m | PAN, basso consumo |

---

# Classificazione per Servizi

La classificazione per servizi risponde a: **cosa offre la rete agli utenti e alle applicazioni?**

## 2.1 — Tipo di collegamento

**Connection-oriented (con connessione)**

- Prima si stabilisce un circuito virtuale o fisico, poi si trasmette, poi si chiude
- Garantisce ordine, affidabilità, QoS
- Esempio: TCP, reti telefoniche tradizionali (PSTN), ATM

**Connectionless (senza connessione)**

- Ogni pacchetto è instradato indipendentemente, senza setup preventivo
- Nessuna garanzia di ordine o consegna
- Esempio: UDP, IP, Ethernet

> **Attenzione**: TCP è connection-oriented ma gira su IP che è connectionless. I livelli OSI hanno caratteristiche indipendenti!

## 2.2 — Modalità di accesso al canale di comunicazione

| Tipo | Descrizione | Esempio |
| --- | --- | --- |
| **Accesso dedicato** | Il canale è riservato a una coppia mittente/destinatario | Linea affittata (leased line) |
| **Accesso condiviso** | Il canale è diviso tra più utenti | Ethernet con hub, Wi-Fi |
| **Commutazione di circuito** | Risorsa allocata end-to-end per tutta la durata | Telefonia tradizionale |
| **Commutazione di pacchetto** | I dati viaggiano a pacchetti che si contendono le risorse | Internet |
| **Commutazione di cella** | Pacchetti a lunghezza fissa (celle) | ATM (53 byte per cella) |

## 2.3 — Tipo di rete per utenza

**Rete pubblica**: accessibile a chiunque, gestita da operatore (ISP). Esempio: Internet.

**Rete privata**: accesso limitato, gestita internamente. Esempio: intranet aziendale.

**VPN** (Virtual Private Network): rete privata che si sovrappone logicamente su infrastruttura pubblica, usando crittografia e tunneling.

## 2.4 — Qualità del servizio (QoS)

Le reti possono garantire (o meno) parametri come:

- **Banda minima garantita**
- **Latenza massima**
- **Jitter** (variazione della latenza)
- **Tasso di perdita di pacchetti**

Le reti **best-effort** (come Internet pubblica) non garantiscono nulla. Le reti con QoS (es. MPLS, ATM) riservano risorse per certi flussi.

---

# Standard Tecnologici

Gli standard tecnologici definiscono **come si parla** sulla rete: formati dei frame, metodi di accesso al mezzo, velocità, modulazione.

## 3.1 — Il modello OSI come riferimento

Gli standard si collocano ai diversi livelli OSI. Fondamentale tenerlo a mente:

| Livello | Nome | Cosa fa | Standard tipici |
| --- | --- | --- | --- |
| 7 | Applicazione | Interfaccia diretta con le applicazioni dell'utente. Gestisce i protocolli di alto livello: richieste web, trasferimento file, posta elettronica, risoluzione nomi. | HTTP, FTP, SMTP, DNS |
| 6 | Presentazione | Traduce i dati tra formati diversi: codifica (UTF-8, ASCII), compressione, cifratura/decifratura. Garantisce che i dati abbiano lo stesso significato su [[Sistemi indice]] diversi. | TLS/SSL, JPEG, MPEG |
| 5 | Sessione | Apre, gestisce e chiude le sessioni di comunicazione tra applicazioni. Gestisce la sincronizzazione e il ripristino in caso di interruzione. | NetBIOS, RPC |
| 4 | Trasporto | Trasferimento end-to-end tra processi (identificati da porte). TCP offre consegna affidabile, controllo di flusso e controllo di congestione. UDP è veloce ma inaffidabile. Unità dati: **segmento** (TCP) / **datagramma** (UDP). | TCP, UDP |
| 3 | Rete | Instradamento (routing) dei pacchetti tra reti diverse. Usa indirizzi logici (**indirizzi IP**) per identificare sorgente e destinazione. I router operano a questo livello. Unità dati: **pacchetto**. | IP (v4, v6), ICMP, OSPF, BGP |
| 2 | Collegamento dati | Trasferimento affidabile tra due nodi direttamente connessi sullo stesso mezzo fisico. Usa indirizzi fisici (**MAC address**, 48 bit) per identificare i dispositivi sulla rete locale. Gestisce il controllo degli errori (CRC) e l'accesso al mezzo (CSMA/CD, token). Gli switch operano a questo livello. Unità dati: **frame**. | Ethernet (802.3), Wi-Fi (802.11), PPP |
| 1 | Fisico | Trasmissione dei bit grezzi sul mezzo fisico (cavo, fibra, onde radio). Definisce tensioni, frequenze, connettori, modulazione. Non ha concetto di indirizzo o errore: trasmette bit, punto. Unità dati: **bit**. | IEEE 802.3 (specifiche fisiche), 10BASE-T, 100BASE-TX |

## 3.2 — Standard per LAN

### Ethernet (IEEE 802.3)

Lo standard dominante per LAN cablate. Funziona a livello fisico e datalink.

**Evoluzione delle velocità**:

- 10 Mbps → 10BASE-T (doppino, anni '90)
- 100 Mbps → Fast Ethernet (100BASE-TX)
- 1 Gbps → Gigabit Ethernet (1000BASE-T)
- 10 Gbps → 10GBASE-T
- 100 Gbps → nelle dorsali e data center

**Metodo di accesso**: CSMA/CD (Carrier Sense Multiple Access / Collision Detection)

- Prima di trasmettere, il nodo ascolta il canale (Carrier Sense)
- Se il canale è libero, trasmette
- Se c'è collisione, si rileva (Collision Detection) e si ritrasmette dopo backoff casuale
- Con gli switch moderni le collisioni sono quasi eliminate (full-duplex)

**Formato del frame Ethernet**:

| Campo | Dimensione | Descrizione |
| --- | --- | --- |
| Preambolo | 7 byte | Sincronizzazione (10101010 ripetuto) |
| SFD | 1 byte | Start Frame Delimiter (10101011) |
| MAC destinazione | 6 byte | Indirizzo fisico destinatario |
| MAC sorgente | 6 byte | Indirizzo fisico mittente |
| EtherType / Lunghezza | 2 byte | Tipo protocollo superiore (es. 0x0800 = IPv4) |
| Dati (payload) | 46–1500 byte | Dati del livello superiore |
| FCS | 4 byte | Frame Check Sequence (CRC per rilevare errori) |

> Il **MTU** (Maximum Transmission Unit) di Ethernet è **1500 byte**. Se un pacchetto IP è più grande, viene frammentato.

### Metodi di accesso al mezzo: CSMA/CD e CSMA/CA

Quando più nodi condividono lo stesso mezzo trasmissivo, serve un meccanismo per decidere **chi trasmette e quando**. I due principali sono CSMA/CD (Ethernet) e CSMA/CA (Wi-Fi).

Entrambi partono da **CSMA** — Carrier Sense Multiple Access:

- **Carrier Sense**: prima di trasmettere, il nodo *ascolta* il canale per verificare se è libero
- **Multiple Access**: più nodi condividono lo stesso mezzo

La differenza sta in cosa succede quando due nodi trasmettono contemporaneamente.

- CSMA/CD — Collision Detection (Ethernet)

    **CD = Collision Detection**: il nodo *rileva* la collisione mentre sta trasmettendo.

    **Funzionamento passo per passo**:

    1. Il nodo ascolta il canale (Carrier Sense)
    2. Se il canale è libero, inizia a trasmettere
    3. **Mentre trasmette**, continua ad ascoltare il canale
    4. Se rileva una collisione (il segnale che legge è diverso da quello che sta inviando), interrompe subito la trasmissione e invia un **segnale di jamming** (32 bit) per avvisare tutti gli altri nodi
    5. Tutti i nodi coinvolti aspettano un tempo casuale (**backoff esponenziale binario**) e poi riprovano

    **Backoff esponenziale**: al primo tentativo fallito si aspetta un tempo casuale tra 0 e 1 slot; al secondo tra 0 e 3; al terzo tra 0 e 7; e così via fino a 16 tentativi, dopo i quali si dichiara errore.

    **Perché non si usa sul wireless**: sul Wi-Fi il nodo non può ascoltare il canale mentre trasmette — il suo stesso segnale in uscita sovrasta quello in ingresso. Non è fisicamente possibile rilevare la collisione in quel momento.

    **Requisito sulla lunghezza minima del frame**: per garantire che la collisione venga rilevata *prima* che il nodo finisca di trasmettere, il frame deve essere abbastanza lungo da impiegare almeno il tempo di andata e ritorno del segnale (2 × propagation delay). In Ethernet questo corrisponde a una dimensione minima di **64 byte** — se i dati sono meno, si aggiunge **padding**.

- CSMA/CA — Collision Avoidance (Wi-Fi)

    **CA = Collision Avoidance**: il nodo cerca di *evitare* le collisioni prima che accadano, perché sul wireless non può rilevarle.

    **Funzionamento passo per passo**:

    1. Il nodo ascolta il canale (Carrier Sense)
    2. Se il canale è occupato, aspetta finché non si libera
    3. Quando il canale si libera, **non trasmette subito**: aspetta un tempo fisso (**DIFS** — Distributed Interframe Space) più un tempo casuale di **backoff** (slot casuali)
    4. Durante il backoff, continua ad ascoltare: se il canale torna occupato, congela il contatore e riprende solo quando si libera di nuovo
    5. Quando il contatore arriva a zero, trasmette
    6. Il destinatario, se riceve correttamente, invia un **ACK** (acknowledgement) dopo un breve tempo (**SIFS**)
    7. Se il mittente non riceve l'ACK entro un timeout, assume che ci sia stata una collisione e ritrasmette

    **Problema del terminale nascosto**: il nodo A e il nodo C sono entrambi nel range dell'AP ma non si vedono tra loro. A sente il canale libero (non sente C), trasmette, ma C sta già trasmettendo → collisione sull'AP. Soluzione: **RTS/CTS** (Request To Send / Clear To Send). A manda un RTS all'AP; l'AP risponde con un CTS che tutti sentono; solo allora A trasmette. C, sentendo il CTS, sa che il canale è occupato e aspetta.

    **Perché si chiama "Avoidance" e non "Detection"**: non si rileva la collisione durante la trasmissione, ma si usa il backoff casuale *prima* per ridurre la probabilità che due nodi trasmettano nello stesso momento. La conferma di successo è l'ACK.

- Confronto CSMA/CD vs CSMA/CA


    |  | CSMA/CD | CSMA/CA |
    | --- | --- | --- |
    | Usato in | Ethernet (LAN cablata) | Wi-Fi (802.11) |
    | Gestione collisioni | Rileva e ritrasmette | Evita con backoff preventivo |
    | ACK richiesto | No (la collisione si rileva direttamente) | Sì (unico modo per sapere se è andato a buon fine) |
    | Efficienza sotto basso carico | Alta (trasmette subito) | Leggermente inferiore (DIFS + backoff anche senza contesa) |
    | Efficienza sotto alto carico | Cala per le collisioni | Cala per il backoff crescente |
    | Problema principale | Collisioni frequenti con hub / molti nodi | Terminale nascosto, overhead ACK/RTS-CTS |
    | Half/Full duplex | Full duplex con switch (nessuna collisione) | Half duplex (un nodo alla volta sul canale) |

### Wi-Fi (IEEE 802.11)

Standard per LAN wireless. Gestisce il mezzo condiviso tramite **CSMA/CA** (Collision Avoidance, non Detection — sul wireless non si può rilevare la collisione mentre si trasmette).

**Principali versioni**:

| Standard | Nome commerciale | Banda | Velocità max teorica |
| --- | --- | --- | --- |
| 802.11b | Wi-Fi 1 | 2.4 GHz | 11 Mbps |
| 802.11a | Wi-Fi 2 | 5 GHz | 54 Mbps |
| 802.11g | Wi-Fi 3 | 2.4 GHz | 54 Mbps |
| 802.11n | Wi-Fi 4 | 2.4/5 GHz | 600 Mbps |
| 802.11ac | Wi-Fi 5 | 5 GHz | ~3.5 Gbps |
| 802.11ax | Wi-Fi 6/6E | 2.4/5/6 GHz | ~9.6 Gbps |

## 3.3 — Standard per WAN

**ADSL / VDSL** (Asymmetric/Very-high-speed DSL): trasmissione su doppino telefonico. Asimmetrica: download > upload.

**FTTX** (Fiber To The X): fibra ottica fino a un punto, poi doppino o coax:

- **FTTH** (Home): fibra fino in casa — massima prestazione
- **FTTB** (Building): fibra fino al palazzo
- **FTTC** (Cabinet): fibra fino all'armadietto stradale

**MPLS** (Multi-Protocol Label Switching): tecnica WAN che usa etichette numeriche per instradare i pacchetti più velocemente dell'IP tradizionale. Usata dagli ISP.

**SDH/SONET**: standard per trasmissione su fibra nelle dorsali. Bit rate multipli (STM-1 = 155 Mbps, STM-64 = 10 Gbps).

## 3.4 — Standard per reti mobili

| Generazione | Velocità tipica | Tecnologia chiave |
| --- | --- | --- |
| 2G (GSM) | ~9.6–384 kbps | TDMA, voce digitale |
| 3G (UMTS/HSPA) | 384 kbps – 42 Mbps | WCDMA |
| 4G (LTE) | fino a ~150 Mbps | OFDMA, MIMO |
| 5G (NR) | fino a ~20 Gbps (teorico) | mmWave, massive MIMO, network slicing |

## 3.5 — Protocolli di rete (livello 3 in su)

**IP (Internet Protocol)**: protocollo di rete di Internet. Versioni:

- **IPv4**: indirizzi a 32 bit (es. 192.168.1.1) — ~4 miliardi di indirizzi, quasi esauriti
- **IPv6**: indirizzi a 128 bit (es. 2001:0db8::1) — praticamente illimitati

**TCP (Transmission Control Protocol)**: livello trasporto, connection-oriented, affidabile (ritrasmette i pacchetti persi), controllo di flusso e congestione.

**UDP (User Datagram Protocol)**: livello trasporto, connectionless, non affidabile, ma veloce. Usato per streaming, DNS, VoIP.

---

# Mappa Concettuale — Relazioni tra le Tre Classificazioni

- Esempio 1: La rete scolastica di Facchinetti
    - **Strutturale**: LAN, topologia ad albero/stella, mezzo UTP cat. 5e/6
    - **Servizi**: connectionless (IP/UDP/TCP), accesso condiviso tramite switch, rete privata
    - **Standard tecnologici**: Ethernet 802.3 (100BASE-TX o Gigabit), Wi-Fi 802.11ac, IP, TCP/UDP
- Esempio 2: Internet
    - **Strutturale**: WAN (globale), topologia a maglia parziale tra router
    - **Servizi**: best-effort, connectionless (IP), commutazione di pacchetto
    - **Standard tecnologici**: IP, TCP, UDP, BGP (routing inter-AS), MPLS nelle dorsali, fibra ottica come mezzo fisico nelle dorsali
- Esempio 3: Rete 5G
    - **Strutturale**: WAN/MAN wireless, topologia a celle
    - **Servizi**: alta velocità, bassa latenza, supporto IoT massivo
    - **Standard tecnologici**: NR (New Radio), OFDMA, network slicing, IP

---

# Domande tipiche da orale

- Differenza tra LAN e WAN?

    La LAN è una rete locale (edificio, campus) con tecnologie ad alta velocità e bassa latenza, tipicamente di proprietà dell'organizzazione. La WAN copre distanze geografiche ampie, usa infrastrutture degli ISP, e ha latenze e costi maggiori. La discriminante non è solo geografica ma anche tecnologica e gestionale.

- Perché CSMA/CA e non CSMA/CD nel Wi-Fi?

    Sul wireless non è possibile rilevare le collisioni mentre si trasmette (il segnale trasmesso sovrasta quello ricevuto). Quindi si cerca di **evitarle** (CA = Collision Avoidance): si aspetta il canale libero, poi si aggiunge un tempo casuale (backoff) prima di trasmettere. Esiste anche il meccanismo RTS/CTS per gestire il problema del terminale nascosto.

- Cosa sono gli standard IEEE 802?

    Il progetto IEEE 802 è una famiglia di standard per le reti locali e metropolitane. I più importanti: 802.3 (Ethernet), 802.11 (Wi-Fi), 802.15 (Bluetooth/ZigBee), 802.1Q (VLAN tagging).

- Topologia fisica vs logica — fai un esempio concreto

    Una rete con hub ha topologia fisica a stella (tutti i cavi vanno all'hub centrale) ma topologia logica a bus (l'hub diffonde ogni frame a tutti i nodi, come farebbe un bus). Con gli switch invece la topologia logica diventa punta-a-punta.

- IPv4 vs IPv6 — perché migrare?

    IPv4 ha ~4,3 miliardi di indirizzi, esauriti dal 2011 (IANA). IPv6 ha 2^128 ≈ 3,4 × 10^38 indirizzi, eliminando il problema. Inoltre IPv6 semplifica l'header, elimina il NAT (necessario con IPv4 per risparmiare indirizzi), e introduce funzionalità native come autoconfigurazione e IPsec obbligatorio.


---

> **Collegamento con altri argomenti**: questa pagina è propedeutica al livello di trasporto (TCP/UDP — 12 giu), al livello applicazione (HTTP, DNS — 13 giu), e alla cybersecurity (15 giu). Vedi anche le reti private virtuali: [[Appunti VPN — Tipologie, Tunneling, Protocolli]].
