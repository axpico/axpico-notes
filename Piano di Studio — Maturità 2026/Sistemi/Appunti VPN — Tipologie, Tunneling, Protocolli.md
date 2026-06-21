# Panoramica

Una **VPN** (Virtual Private Network) è una **rete privata virtuale** costruita sopra un'infrastruttura pubblica e non fidata (tipicamente Internet). Permette a host o reti geograficamente distanti di comunicare **come se fossero sulla stessa LAN privata**, garantendo riservatezza, integrità e autenticazione del traffico.

L'idea chiave: invece di affittare costose linee dedicate (es. leased line) per collegare due sedi, si sfrutta Internet — economico ma insicuro — e si crea un **tunnel cifrato** che simula un collegamento privato punto-punto.

- **Virtual**: il collegamento non è fisico ma logico (un tunnel software)
- **Private**: il traffico è cifrato e isolato, invisibile a chi sta in mezzo
- **Network**: collega host/reti come fossero adiacenti

---

# Perché una VPN — Il problema che risolve

```
SENZA VPN — sede A vuole parlare con sede B via Internet
[LAN A] ──► pacchetti in CHIARO su Internet ──► [LAN B]
                     ▲
            chiunque sul percorso (ISP, router,
            attaccante MitM) legge tutto
```

```
CON VPN — tunnel cifrato gateway-to-gateway
[LAN A] ──► [GW A] ══════ tunnel cifrato ══════ [GW B] ──► [LAN B]
                          (payload illeggibile
                           per chi intercetta)
```

![[vpn_tunnel_concept.svg|697]]

Una VPN fornisce le tre garanzie di sicurezza (vedi [[Appunti CIA · Attacchi e Minacce · Malware · Te]]):

- **Confidenzialità**: il traffico è cifrato (es. AES) → chi intercetta vede solo dati casuali
- **Integrità**: ogni pacchetto è autenticato (HMAC) → modifiche rilevate e scartate
- **Autenticazione**: i due estremi si verificano a vicenda (certificati, pre-shared key) → niente impostori

---

# Concetto chiave: il Tunneling

Il **tunneling** è la tecnica alla base di ogni VPN: consiste nell'**incapsulare un pacchetto dentro un altro pacchetto**.

Il pacchetto originale (con gli indirizzi privati della LAN) diventa il *payload* di un nuovo pacchetto esterno, che viaggia su Internet con gli indirizzi pubblici dei gateway VPN.

```
Pacchetto originale (rete privata):
    [IP privato 192.168.1.10 → 10.0.0.5 | TCP | Dati]

Dopo incapsulamento + cifratura nel tunnel:
    [IP pubblico GW_A → GW_B | header VPN | (pacchetto originale CIFRATO)]
     └─────── visibile su Internet ──────┘ └──── illeggibile ────┘
```

![[vpn_tunneling_encapsulation.svg|697]]

- I router di Internet instradano in base al **nuovo header esterno** (IP pubblici dei gateway)
- Il pacchetto interno con gli indirizzi privati è **nascosto e cifrato**
- Arrivato a destinazione, il gateway **decapsula** e **decifra**, ottenendo il pacchetto originale che inoltra nella LAN

> Il tunneling da solo (es. GRE) incapsula ma **non cifra**. Una VPN sicura combina tunneling **+ cifratura + autenticazione**.

---

# Tipologie di VPN (per architettura)

![[vpn_site_to_site_vs_client_v4.svg|697]]

## 1. VPN Site-to-Site (rete-rete)

Collega **due intere reti** attraverso i rispettivi gateway (router/firewall). Tipica delle aziende con più sedi.

```
       Sede Milano                Internet               Sede Roma
[LAN 192.168.1.0/24]                                [LAN 192.168.2.0/24]
   PC ── Server ──[Gateway A]══tunnel IPSec══[Gateway B]── PC ── Server
                       │                          │
              gestisce tutta la VPN      gestisce tutta la VPN
```

- I **PC delle due sedi non sanno nulla** della VPN: inviano traffico normale
- Solo i gateway cifrano/decifrano (la VPN è **trasparente** agli host)
- Tecnologia tipica: **IPSec in tunnel mode** (vedi [[Appunti IPSec · TLS SSL · HTTPS]])
- Sempre attiva (tunnel permanente)

**Sotto-tipi**:
- **Intranet VPN**: collega sedi della stessa azienda
- **Extranet VPN**: collega l'azienda a partner/fornitori esterni (accesso limitato)

## 2. VPN Client-to-Site (Remote Access / host-rete)

Un **singolo dispositivo** (laptop, smartphone di un dipendente in smart working) si collega alla rete aziendale.

```
   Dipendente a casa                Internet            Azienda
[Laptop + client VPN]══════tunnel cifrato══════[VPN Gateway]──[LAN aziendale]
   IP virtuale: 10.8.0.7                            │
                                          assegna IP virtuale al client
```

- Il client installa un **software VPN** (es. OpenVPN, client Cisco AnyConnect, WireGuard)
- Il gateway assegna al client un **IP virtuale** della rete aziendale → il laptop "entra" nella LAN
- Tecnologie tipiche: **IPSec/IKEv2**, **OpenVPN (SSL/TLS)**, **WireGuard**
- Attivo solo quando il dipendente si connette

## 3. VPN Host-to-Host

Collega **due singoli dispositivi** direttamente (es. due server che si scambiano dati sensibili). Raro, usa **IPSec in transport mode**.

---

# Tipologie di VPN (per protocollo / livello OSI)

| Protocollo | Livello OSI | Cifratura | Note |
| --- | --- | --- | --- |
| **PPTP** | 2 (Datalink) | Debole (MPPE) | Obsoleto, **insicuro**, da non usare |
| **L2TP/IPSec** | 2 + 3 | IPSec (AES) | L2TP fa il tunnel, IPSec cifra |
| **IPSec** | 3 (Rete) | AES, 3DES | Standard per site-to-site |
| **OpenVPN** | 4-7 (su SSL/TLS) | AES, ChaCha20 | Open source, flessibile, porta 1194/443 |
| **WireGuard** | 3 (Rete) | ChaCha20 | Moderno, semplice, velocissimo |
| **SSTP** | 4-7 (su TLS) | TLS | Microsoft, passa firewall (porta 443) |

## PPTP — Point-to-Point Tunneling Protocol

Vecchissimo (Microsoft, 1999). Usa **GRE** per il tunnel e **MPPE** per cifrare. **Completamente insicuro** (MS-CHAPv2 craccabile in ore). Citato solo per contesto storico — **mai usare**.

## L2TP/IPSec — Layer 2 Tunneling Protocol

L2TP da solo **non cifra**: crea solo il tunnel di livello 2. Si combina sempre con **IPSec** che fornisce la cifratura. Doppio incapsulamento → più overhead. Usa UDP 500/4500 (IKE) + UDP 1701 (L2TP).

## IPSec

La suite standard per VPN site-to-site. Coperto in dettaglio in [[Appunti IPSec · TLS SSL · HTTPS]]. Riepilogo:
- **ESP** cifra+autentica il payload, **AH** solo autentica (incompatibile NAT)
- **IKE** (UDP 500/4500) negozia chiavi e Security Association
- **Tunnel mode** per VPN (incapsula tutto il pacchetto), **transport mode** host-to-host

## OpenVPN

VPN open source basata su **SSL/TLS** (la stessa di HTTPS). Molto flessibile:
- Gira in **user-space** (più portabile, leggermente più lento del kernel)
- Può usare **UDP** (più veloce) o **TCP** (attraversa firewall restrittivi)
- Può girare sulla **porta 443** → indistinguibile dal traffico HTTPS, supera i firewall
- Autenticazione con certificati X.509, username/password, o chiavi condivise

## WireGuard

VPN moderna (2020, integrata nel kernel Linux). Filosofia: **semplicità estrema**.
- Solo ~4000 righe di codice (IPSec/OpenVPN ne hanno centinaia di migliaia) → meno superficie d'attacco
- Crittografia fissa e moderna: **ChaCha20** (cifratura), **Poly1305** (autenticazione), **Curve25519** (key exchange)
- Usa **UDP**, configurazione minimale basata su coppie di chiavi pubbliche/private (modello tipo SSH)
- Molto più veloce di IPSec e OpenVPN

---

# Esempio pratico — Configurazione WireGuard

WireGuard è l'esempio più semplice da capire. Ogni peer ha una **chiave privata** (segreta) e una **chiave pubblica** (condivisa con l'altro peer).

**Server (sede aziendale)** — `/etc/wireguard/wg0.conf`:

```ini
[Interface]
# Chiave privata del server (segreta)
PrivateKey = aB3...serverPriv...xZ9=
# IP virtuale del server nella rete VPN
Address = 10.8.0.1/24
# Porta UDP su cui ascolta
ListenPort = 51820

[Peer]
# Chiave pubblica del client (laptop dipendente)
PublicKey = cD4...clientPub...yW8=
# Quali IP può usare questo client nel tunnel
AllowedIPs = 10.8.0.7/32
```

**Client (laptop del dipendente)** — `wg0.conf`:

```ini
[Interface]
# Chiave privata del client
PrivateKey = eF5...clientPriv...vU7=
# IP virtuale assegnato al client
Address = 10.8.0.7/24
# DNS da usare dentro la VPN
DNS = 10.8.0.1

[Peer]
# Chiave pubblica del server
PublicKey = gH6...serverPub...tS6=
# IP pubblico e porta del server
Endpoint = vpn.azienda.it:51820
# Instrada TUTTO il traffico nel tunnel (full tunnel)
AllowedIPs = 0.0.0.0/0
# Mantiene viva la connessione attraverso il NAT
PersistentKeepalive = 25
```

Avvio del tunnel:

```bash
# Attiva l'interfaccia VPN
sudo wg-quick up wg0

# Verifica lo stato (handshake, dati trasferiti)
sudo wg show

# Disattiva
sudo wg-quick down wg0
```

Dopo `wg-quick up`, il laptop ha un IP `10.8.0.7` nella rete aziendale e tutto il traffico (`AllowedIPs = 0.0.0.0/0`) passa cifrato verso `vpn.azienda.it`.

---

# Full Tunnel vs Split Tunnel

Decisione importante: **quale traffico** del client deve passare nella VPN?

![[vpn_full_vs_split_tunnel.svg|697]]

## Full Tunnel — tutto nella VPN

```
Laptop ──► [TUTTO il traffico] ──► VPN Gateway ──► Internet / LAN aziendale
                                        │
                              anche Google, YouTube, ecc.
                              escono dall'IP aziendale
```

- `AllowedIPs = 0.0.0.0/0` → **tutto** il traffico, anche la navigazione web, passa per l'azienda
- **Pro**: massima sicurezza e controllo (l'azienda filtra/logga tutto), nasconde il vero IP del client
- **Contro**: più lento (deviazione attraverso l'azienda), carica la banda aziendale

## Split Tunnel — solo il traffico aziendale nella VPN

```
Laptop ──► [traffico 192.168.x.x] ──► VPN Gateway ──► LAN aziendale
       └─► [traffico Internet generico] ──────────► Internet diretto
```

- Solo il traffico verso la rete aziendale entra nel tunnel; il resto (Google, YouTube) va diretto
- **Pro**: più veloce, non spreca banda aziendale
- **Contro**: meno controllo/sicurezza (il traffico generale non è filtrato dall'azienda)

---

# VPN e NAT — il problema del NAT Traversal

Le VPN IPSec hanno problemi con il **NAT** (vedi [[Appunti Firewall · ACL · Proxy · DMZ · Port Forw]]):

- **AH** autentica l'IP header → il NAT modifica l'IP sorgente → autenticazione fallisce → **AH incompatibile con NAT**
- **ESP** non autentica l'IP header esterno, ma il NAT modifica le porte e ESP non ha porte visibili

**Soluzione — NAT-T (NAT Traversal)**: incapsula i pacchetti ESP dentro **UDP porta 4500**. Così il NAT vede una normale connessione UDP e la gestisce correttamente.

```
Senza NAT-T:  [IP] [ESP] [payload cifrato]          ← NAT lo rompe
Con NAT-T:    [IP] [UDP:4500] [ESP] [payload]        ← NAT lo gestisce
```

---

# Confronto tra le principali tecnologie VPN

|  | IPSec | OpenVPN | WireGuard |
| --- | --- | --- | --- |
| **Livello OSI** | 3 (Rete) | 4-7 (SSL/TLS) | 3 (Rete) |
| **Dove gira** | Kernel | User-space | Kernel |
| **Velocità** | Alta | Media | Altissima |
| **Configurazione** | Complessa (IKE, SA) | Media | Semplice |
| **Attraversa firewall** | Difficile (UDP 500) | Sì (può usare TCP 443) | Difficile (UDP) |
| **Crittografia** | Configurabile (AES…) | Configurabile | Fissa e moderna |
| **Codice** | Molto complesso | Complesso | ~4000 righe |
| **Uso tipico** | Site-to-site aziendale | Remote access flessibile | Moderno tutto-fare |

---

# VPN vs Proxy — non confondere

| | Proxy | VPN |
| --- | --- | --- |
| **Livello** | Applicativo (es. solo HTTP) | Rete (tutto il traffico) |
| **Cifratura** | Non necessariamente | Sempre |
| **Cosa copre** | Una singola app/protocollo | Tutto il dispositivo |
| **Autenticazione reciproca** | No | Sì |

Un **proxy** (vedi [[Appunti Firewall · ACL · Proxy · DMZ · Port Forw]]) inoltra solo il traffico di una specifica applicazione e spesso non cifra. Una **VPN** cifra e tunnela **tutto** il traffico IP del dispositivo.

---

# Schema riepilogativo — Dove opera una VPN

```
Livello 7 — Applicazione   [HTTP] [SMTP] [FTP]   ← OpenVPN/SSTP cifrano qui sopra
                               |
Livello 5-6                  [SSL/TLS] ←──────────── OpenVPN, SSTP
                               |
Livello 4 — Trasporto        [TCP] [UDP]
                               |
Livello 3 — Rete             [IP]
                          [IPSec / WireGuard] ←───── cifrano il payload IP
                               |
Livello 2 — Datalink         [Ethernet] [PPTP] [L2TP] ← tunnel di livello 2
                               |
Livello 1 — Fisico           [cavi, onde radio]
```

---

# Domande tipiche da orale

- Cos'è una VPN e a cosa serve?

    Una VPN (Virtual Private Network) è una rete privata virtuale costruita sopra una rete pubblica come Internet. Crea un tunnel cifrato tra due estremi, permettendo a host o reti distanti di comunicare in modo sicuro come se fossero sulla stessa LAN. Serve a collegare sedi aziendali (site-to-site) o a far accedere dipendenti remoti alla rete aziendale (client-to-site), garantendo confidenzialità, integrità e autenticazione senza il costo di linee dedicate.

- Cos'è il tunneling?

    Il tunneling è la tecnica di incapsulare un pacchetto dentro un altro pacchetto. Il pacchetto originale, con gli indirizzi privati, diventa il payload di un nuovo pacchetto esterno con gli IP pubblici dei gateway. I router di Internet instradano in base all'header esterno, mentre il pacchetto interno viaggia cifrato e nascosto. A destinazione il gateway decapsula e decifra.

- Differenza tra VPN site-to-site e client-to-site?

    La site-to-site collega due intere reti tramite i loro gateway: gli host delle due reti non sanno nulla della VPN, è trasparente, e tipicamente usa IPSec in tunnel mode. La client-to-site (remote access) collega un singolo dispositivo alla rete aziendale: il client installa un software VPN e riceve un IP virtuale della LAN aziendale, tipico dello smart working.

- Differenza tra full tunnel e split tunnel?

    Nel full tunnel tutto il traffico del client passa nella VPN, anche la navigazione web generica: massima sicurezza ma più lento. Nello split tunnel solo il traffico verso la rete aziendale entra nel tunnel, il resto va diretto su Internet: più veloce ma meno controllato.

- Perché L2TP si usa sempre con IPSec?

    Perché L2TP da solo crea solo il tunnel di livello 2 ma non cifra nulla. Si combina con IPSec, che fornisce la cifratura e l'autenticazione. La sigla L2TP/IPSec indica appunto questa combinazione.

- Cos'è il NAT Traversal e perché serve?

    IPSec ha problemi con il NAT: AH autentica l'IP header che il NAT modifica, rendendolo incompatibile; ESP non ha porte che il NAT possa tradurre. Il NAT-T risolve incapsulando i pacchetti ESP dentro UDP sulla porta 4500, così il NAT li vede come traffico UDP normale e li gestisce correttamente.

- Differenza tra VPN e proxy?

    Un proxy opera a livello applicativo e inoltra solo il traffico di una specifica applicazione (es. HTTP), spesso senza cifrarlo. Una VPN opera a livello rete, cifra e tunnela tutto il traffico IP del dispositivo, e prevede autenticazione reciproca tra i due estremi.

- Perché WireGuard è considerato più sicuro/semplice di IPSec?

    WireGuard ha solo circa 4000 righe di codice contro le centinaia di migliaia di IPSec/OpenVPN, quindi una superficie d'attacco molto minore e più facile da verificare. Usa una crittografia moderna e fissa (ChaCha20, Poly1305, Curve25519) senza negoziazioni complesse, e un modello di chiavi pubbliche/private simile a SSH. È anche più veloce perché integrato nel kernel.

---

> **Collegamento con altri argomenti**: IPSec, TLS/SSL, HTTPS — [[Appunti IPSec · TLS SSL · HTTPS]] | Crittografia simmetrica/asimmetrica — [[Appunti Crittografia Simmetrica, Asimmetrica e R]] | Firewall, NAT, Proxy, DMZ — [[Appunti Firewall · ACL · Proxy · DMZ · Port Forw]] | CIA e sicurezza — [[Appunti CIA · Attacchi e Minacce · Malware · Te]]
