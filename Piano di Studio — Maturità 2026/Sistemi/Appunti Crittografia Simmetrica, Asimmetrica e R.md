# Panoramica

La crittografia è la scienza di trasformare informazioni leggibili in forma illeggibile per chi non è autorizzato, e di riportarle alla forma originale per chi lo è. È il fondamento tecnico di quasi ogni meccanismo di sicurezza Informatica: HTTPS, VPN, firma digitale, autenticazione.

Due paradigmi fondamentali: **crittografia simmetrica** (una chiave) e **crittografia asimmetrica** (coppia di chiavi). Capire quando e perché si usa ciascuno è essenziale.

---

# Concetti Base

## Terminologia

| Termine | Definizione |
| --- | --- |
| **Plaintext** | Il messaggio originale in chiaro |
| **Ciphertext** | Il messaggio cifrato |
| **Cifratura (Encryption)** | Trasformazione plaintext → ciphertext tramite algoritmo + chiave |
| **Decifratura (Decryption)** | Trasformazione ciphertext → plaintext tramite algoritmo + chiave |
| **Chiave (Key)** | Parametro segreto che controlla la cifratura/decifratura |
| **Algoritmo (Cipher)** | La funzione matematica che esegue la trasformazione |
| **Keyspace** | L'insieme di tutte le chiavi possibili per un dato algoritmo |

## Principio di Kerckhoffs (1883)

> *"La sicurezza di un sistema crittografico non deve dipendere dalla segretezza dell'algoritmo, ma solo dalla segretezza della chiave."*

In pratica: gli algoritmi sono pubblici e analizzati da tutta la community scientifica. La sicurezza sta interamente nella chiave. Un algoritmo segreto che nessuno ha potuto analizzare è molto meno affidabile di uno pubblico e ampiamente testato.

## Misure di sicurezza

**Lunghezza della chiave (key length)**: misurata in bit. Determina il keyspace: una chiave a 128 bit ha 2^128 combinazioni possibili ≈ 3,4 × 10^38. Un attacco brute-force che prova tutte le chiavi è computazionalmente impossibile.

**Attacco brute-force**: prova ogni possibile chiave finché non trova quella giusta. La complessità è O(2^n) dove n è la lunghezza della chiave in bit. Con hardware moderno:

- 40 bit: pochi secondi
- 56 bit (DES): ore/giorni
- 128 bit (AES): più anni del tempo stimato dell'universo

**Attacco crittoanalitico**: sfrutta debolezze matematiche dell'algoritmo per ridurre il keyspace effettivo. Un buon algoritmo non deve avere queste debolezze.

---

# Crittografia Simmetrica

## Principio

Mittente e destinatario usano la **stessa chiave** sia per cifrare che per decifrare. La chiave è un segreto condiviso.

```
[Plaintext] ──► [Encrypt] ──► [Ciphertext] ──► [Decrypt] ──► [Plaintext]
                 ↑                               ↑
             Chiave K                         Chiave K (stessa)
```

## Vantaggi e svantaggi

|                              | Simmetrica                                                                                           |
| ---------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Velocità**                 | Ordini di grandezza più veloce dell'asimmetrica (operazioni semplici su bit)                         |
| **Efficienza**               | Adatta a cifrare grandi quantità di dati                                                             |
| **Key distribution problem** | Come si scambia la chiave in modo sicuro? Se il canale è insicuro, la chiave può essere intercettata |
| **Scalabilità**              | Con n utenti servono n·(n−1)/2 chiavi (ogni coppia ne ha una diversa)                                |

## Tipi di cifrari simmetrici

**Cifrari a blocchi (Block cipher)**: dividono il plaintext in blocchi di dimensione fissa (es. 128 bit) e cifrano ogni blocco. Se il messaggio non è multiplo della dimensione del blocco si aggiunge **padding**.

**Cifrari a flusso (Stream cipher)**: cifrano il plaintext un bit o un byte alla volta, combinandolo con un flusso pseudocasuale generato dalla chiave. Più veloci dei block cipher, usati in applicazioni real-time (es. RC4 — ora deprecato).

## Modalità operative dei block cipher

Un block cipher da solo cifra ogni blocco indipendentemente — questo è un problema: due blocchi identici di plaintext producono due blocchi identici di ciphertext, rivelando pattern. Le **modalità operative** risolvono questo:

- ECB — Electronic Code Book

    Ogni blocco viene cifrato indipendentemente con la stessa chiave. È la modalità più semplice ma la più insicura: blocchi identici di plaintext producono blocchi identici di ciphertext → i pattern nel messaggio rimangono visibili nel ciphertext.

    **Non usare mai ECB per dati reali.** Il classico esempio è il pinguino Linux cifrato in ECB: il ciphertext rivela ancora la sagoma dell'immagine originale.

- CBC — Cipher Block Chaining

    Prima di cifrare ogni blocco, si fa XOR con il ciphertext del blocco precedente. Il primo blocco usa un **IV** (Initialization Vector) casuale al posto del blocco precedente.

    ```
    C[i] = Encrypt(P[i] XOR C[i-1])
    C[0] = Encrypt(P[0] XOR IV)
    ```

    Blocchi identici di plaintext producono ciphertext diversi. È la modalità più diffusa per i file. Un errore in un blocco si propaga ai blocchi successivi.

- CTR — Counter Mode

    Un contatore viene cifrato con la chiave, producendo un keystream. Il plaintext viene messo in XOR con il keystream. Trasforma un block cipher in stream cipher.

    Permette parallelizzazione (ogni blocco è indipendente), buono per hardware moderno. Usato in AES-GCM (il modo più comune per HTTPS).


## Algoritmi simmetrici principali

### DES — Data Encryption Standard

- **Anno**: 1977 (NIST)
- **Lunghezza chiave**: 56 bit
- **Dimensione blocco**: 64 bit
- **Struttura**: rete di Feistel a 16 round
- **Stato**: **obsoleto e insicuro** — nel 1999 un hardware dedicato ha trovato la chiave in meno di 24 ore con brute-force. 56 bit sono troppo pochi.

**Rete di Feistel**: il blocco di 64 bit viene diviso in metà sinistra (L) e destra (R). Ad ogni round: `L[i+1] = R[i]`, `R[i+1] = L[i] XOR F(R[i], K[i])`. La funzione F usa S-box (Substitution boxes) per introdurre non-linearità.

### 3DES — Triple DES

- **Anno**: 1998
- **Lunghezza chiave effettiva**: 112 bit (con 3 chiavi diverse)
- **Meccanismo**: applica DES tre volte: `Encrypt(K1) → Decrypt(K2) → Encrypt(K3)`
- **Stato**: deprecato dal NIST nel 2023. Più sicuro di DES ma molto lento (3x DES).

### AES — Advanced Encryption Standard

- **Anno**: 2001 (NIST, vincitore di una competizione pubblica — l'algoritmo si chiama Rijndael)
- **Lunghezza chiave**: 128, 192 o 256 bit
- **Dimensione blocco**: 128 bit (fisso)
- **Struttura**: rete a sostituzione-permutazione, 10/12/14 round (dipende dalla lunghezza della chiave)
- **Stato**: **standard attuale**, sicuro, velocissimo (istruzioni hardware dedicate su CPU moderne: AES-NI)

**Come funziona AES** (struttura interna):

Il blocco di 128 bit è rappresentato come una matrice 4×4 di byte. Ad ogni round vengono applicate 4 trasformazioni:

1. **SubBytes**: ogni byte viene sostituito con un altro tramite una S-box (non-lineare)
2. **ShiftRows**: le righe della matrice vengono ruotate ciclicamente di 0, 1, 2, 3 posizioni
3. **MixColumns**: ogni colonna viene moltiplicata per una matrice fissa in GF(2⁸) (introduce diffusione)
4. **AddRoundKey**: XOR tra la matrice e la sottochiave del round corrente

L'ultimo round omette MixColumns. La sicurezza deriva dalla combinazione di confusione (SubBytes) e diffusione (ShiftRows + MixColumns).

> **Confusione e diffusione** (Shannon, 1949): la confusione rende complessa la relazione tra chiave e ciphertext (S-box), la diffusione distribuisce l'influenza di ogni bit del plaintext su tutto il ciphertext (ShiftRows + MixColumns). Ogni buon cifrario moderno implementa entrambe.

---

# Crittografia Asimmetrica

## Il problema che risolve

La crittografia simmetrica ha il **key distribution problem**: come si scambia la chiave segreta su un canale insicuro? Se due parti non si sono mai incontrate di persona, non possono condividere una chiave senza rischiare che venga intercettata.

La crittografia asimmetrica risolve questo problema eliminando la necessità di scambiare segreti.

## Principio

Ogni partecipante ha una **coppia di chiavi matematicamente correlate**:

- **Chiave pubblica (PK)**: distribuita liberamente a chiunque
- **Chiave privata (SK)**: non lascia mai il proprietario, tenuta segreta

La relazione fondamentale: **ciò che viene cifrato con una chiave può essere decifrato solo con l'altra**.

```
Cifratura per confidenzialità:
[Plaintext] ──► Encrypt(PK_destinatario) ──► [Ciphertext] ──► Decrypt(SK_destinatario) ──► [Plaintext]

Firma digitale:
[Hash] ──► Sign(SK_mittente) ──► [Firma] ──► Verify(PK_mittente) ──► [Hash verificato]
```

## Vantaggi e svantaggi

|  | Asimmetrica |
| --- | --- |
| **Key distribution** | La chiave pubblica si distribuisce liberamente, nessun segreto da scambiare |
| **Scalabilità** | Con n utenti bastano n coppie di chiavi (non n·(n−1)/2) |
| **Firma digitale** | Permette autenticazione e non-repudiation |
| **Velocità** | 100–1000x più lenta della simmetrica (operazioni su grandi numeri) |
| **Non adatta a grandi dati** | Usata solo per scambiare chiavi simmetriche o firmare hash |

## Come si usa in pratica: schema ibrido

In tutti i [[Sistemi indice]] reali (TLS, PGP, SSH) le due crittografie vengono combinate:

1. Si usa l'asimmetrica per scambiare in modo sicuro una **chiave simmetrica di sessione** (key exchange)
2. Si usa la simmetrica con quella chiave per cifrare tutti i dati

Si ottiene la sicurezza dello scambio di chiavi + la velocità della simmetrica.

---

# RSA

## Storia e contesto

**RSA** = Rivest, Shamir, Adleman — i tre matematici del MIT che lo pubblicarono nel **1977**. È il primo e ancora più usato algoritmo di crittografia a chiave pubblica. La sua sicurezza si basa su un problema matematico non ancora risolto efficientemente.

## Fondamento matematico: il problema della fattorizzazione

RSA si basa sul fatto che:

- **Moltiplicare** due numeri primi grandi è computazionalmente **facile**
- **Fattorizzare** il loro prodotto (trovare i fattori originali) è computazionalmente **impossibile** per numeri abbastanza grandi

Esempio semplificato:

```
17 × 19 = 323          ← facile
323 = ? × ?            ← difficile (per numeri di centinaia di cifre)
```

In RSA reale si usano numeri primi di 1024–2048 bit (≈ 300–600 cifre decimali). Non esiste algoritmo efficiente per fattorizzarli con hardware classico.

## Generazione delle chiavi RSA (passo per passo)

**Step 1**: Scegliere due numeri primi grandi `p` e `q` (generati casualmente, tenuti segreti)

**Step 2**: Calcolare `n = p × q` — questo è il **modulo** (parte pubblica)

**Step 3**: Calcolare la funzione di Eulero: `φ(n) = (p-1) × (q-1)`

**Step 4**: Scegliere `e` tale che:

- `1 < e < φ(n)`
- `MCD(e, φ(n)) = 1` (e e φ(n) sono coprimi)
- Valore comune: `e = 65537` (primo, forma 2^16 + 1, buone proprietà computazionali)

**Step 5**: Calcolare `d` tale che `d × e ≡ 1 (mod φ(n))` — `d` è l'inverso moltiplicativo di `e` modulo `φ(n)`. Si calcola con l'**algoritmo esteso di Euclide**.

**Chiave pubblica**: `(n, e)`

**Chiave privata**: `(n, d)` — (p, q, φ(n) vengono distrutti dopo la generazione)

## Cifratura e decifratura RSA

**Cifratura** (con chiave pubblica del destinatario):

```
C = M^e mod n
```

Dove M è il plaintext rappresentato come numero intero, C è il ciphertext.

**Decifratura** (con chiave privata del destinatario):

```
M = C^d mod n
```

**Esempio numerico semplificato**:

```
p = 61,  q = 53
n = 61 × 53 = 3233
φ(n) = 60 × 52 = 3120
e = 17  (coprimo con 3120)
d = 2753  (perché 17 × 2753 = 46801 = 15 × 3120 + 1)

Chiave pubblica: (3233, 17)
Chiave privata: (3233, 2753)

Cifratura di M = 65:
C = 65^17 mod 3233 = 2790

Decifratura:
M = 2790^2753 mod 3233 = 65  ✓
```

## Perché funziona: il teorema di Eulero

Il cuore matematico di RSA è il **teorema di Eulero**:

```
M^(φ(n)) ≡ 1 (mod n)    per ogni M coprimo con n
```

Poiché `d × e ≡ 1 (mod φ(n))`, esiste k tale che `d × e = kφ(n) + 1`. Quindi:

```
C^d = (M^e)^d = M^(e×d) = M^(kφ(n)+1) = (M^(φ(n)))^k × M ≡ 1^k × M = M (mod n)
```

La decifratura restituisce esattamente il messaggio originale.

## RSA per firma digitale

La firma digitale inverte l'uso delle chiavi:

1. Il mittente calcola l'**hash** del messaggio: `H = hash(M)`
2. **Firma** con la propria chiave privata: `S = H^d mod n`
3. Il destinatario riceve M e S
4. **Verifica** con la chiave pubblica del mittente: `H' = S^e mod n`
5. Se `H' == hash(M)` → la firma è valida

**Cosa garantisce**:

- **Autenticità**: solo chi possiede SK può aver generato S
- **Integrità**: se M è stato modificato, hash(M) ≠ H'
- **Non-repudiation**: il mittente non può negare di aver firmato

> Si firma l'**hash**, non il messaggio intero, perché RSA è lento. L'hash ha dimensione fissa e piccola (es. 256 bit per SHA-256), il messaggio potrebbe essere gigabyte.

## Lunghezze di chiave RSA e sicurezza

| Lunghezza chiave RSA | Sicurezza equivalente AES | Stato |
| --- | --- | --- |
| 1024 bit | ~80 bit | Deprecata, non usare |
| 2048 bit | ~112 bit | Minimo raccomandato oggi |
| 3072 bit | ~128 bit | Raccomandato per nuove applicazioni |
| 4096 bit | ~140 bit | Alta sicurezza, più lento |

> Le chiavi RSA devono essere molto più lunghe di quelle AES per lo stesso livello di sicurezza, perché la fattorizzazione è un problema più facile del brute-force su AES.

## RSA e il futuro: minaccia quantistica

I computer quantistici, tramite l'**algoritmo di Shor** (1994), possono fattorizzare n in tempo polinomiale — rompendo RSA completamente. Lo stesso vale per Diffie-Hellman ed ECC.

Per questo il NIST sta standardizzando algoritmi **post-quantum** (PQC): CRYSTALS-Kyber (key exchange), CRYSTALS-Dilithium (firma digitale), basati su problemi matematici resistenti ai computer quantistici (reticoli, codici, hash).

---

# Diffie-Hellman Key Exchange

## Il problema

Come possono Alice e Bob concordare una chiave simmetrica segreta su un canale pubblico, senza che Eve (che intercetta tutto) riesca a ricavarla?

## Il protocollo (1976)

Si basa sulla difficoltà del **problema del logaritmo discreto**: dato `g^x mod p`, trovare `x` è computazionalmente impossibile per p grande.

```
Parametri pubblici: p (numero primo grande), g (generatore)

Alice sceglie segreto a, calcola A = g^a mod p  → invia A a Bob
Bob   sceglie segreto b, calcola B = g^b mod p  → invia B ad Alice

Alice calcola: K = B^a mod p = g^(ab) mod p
Bob   calcola: K = A^b mod p = g^(ab) mod p

K è la chiave condivisa. Eve vede p, g, A, B ma non può ricavare a, b, o K.
```

DH non cifra nulla da solo: serve solo per scambiare una chiave simmetrica. È vulnerabile ad attacchi MitM se non autenticato — per questo in TLS si usa **DHE** (Ephemeral) combinato con certificati RSA/ECDSA per l'autenticazione.

---

# ECC — Elliptic Curve Cryptography

## Cos'è

Alternativa moderna a RSA, basata sulla matematica delle **curve ellittiche** su campi finiti. La sicurezza si basa sul problema del logaritmo discreto su curve ellittiche (ECDLP), ancora più difficile da risolvere della fattorizzazione.

**Vantaggio chiave**: chiavi molto più corte a pari sicurezza.

| Sicurezza | RSA | ECC |
| --- | --- | --- |
| 80 bit | 1024 bit | 160 bit |
| 128 bit | 3072 bit | 256 bit |
| 256 bit | 15360 bit | 512 bit |

**Usi**: TLS (ECDHE per key exchange, ECDSA per firme), Bitcoin (secp256k1), Signal Protocol, carte di pagamento.

---

# Confronto Finale

|  | Simmetrica (AES) | Asimmetrica (RSA) | ECC |
| --- | --- | --- | --- |
| **Chiavi** | 1 condivisa | Coppia pubblica/privata | Coppia pubblica/privata |
| **Velocità** | Molto veloce | Lenta | Media |
| **Key exchange** | Problema | Nativo | Nativo |
| **Firma digitale** | No | Sì | Sì |
| **Lunghezza chiave** | 128–256 bit | 2048–4096 bit | 256–512 bit |
| **Uso tipico** | Cifratura bulk dati | Key exchange, firme | Key exchange, firme (mobile) |
| **Resistenza quantum** | Parziale (AES-256) | No (Shor) | No (Shor) |

---

# Domande tipiche da orale

- Perché si usano simmetrica e asimmetrica insieme?

    L'asimmetrica risolve il key distribution problem ma è troppo lenta per cifrare grandi dati. La simmetrica è velocissima ma richiede uno scambio sicuro della chiave. In TLS: si usa RSA o ECDH per scambiare una chiave simmetrica AES di sessione, poi AES cifra tutto il traffico. Si ottiene entrambi i vantaggi.

- Perché RSA è sicuro? Su cosa si basa?

    RSA si basa sulla difficoltà computazionale della fattorizzazione di interi: dato n = p × q con p e q primi grandi, trovare p e q conoscendo solo n è un problema per cui non esiste algoritmo polinomiale con hardware classico. Conoscere d (chiave privata) richiede conoscere φ(n) = (p-1)(q-1), che richiede conoscere p e q, che richiede fattorizzare n.

- Differenza tra cifratura con chiave pubblica e firma digitale in RSA

    Nella cifratura per riservatezza si cifra con la **chiave pubblica del destinatario**: solo lui, con la sua chiave privata, può decifrare. Nella firma digitale si firma con la **chiave privata del mittente**: chiunque, con la chiave pubblica del mittente, può verificare che sia stato lui a firmare. Stessa matematica, chiavi invertite, obiettivi opposti.

- Cos'è il principio di Kerckhoffs e perché è importante?

    Un sistema crittografico deve essere sicuro anche se tutto è noto tranne la chiave. In pratica: gli algoritmi (AES, RSA...) sono pubblici, analizzati da migliaia di ricercatori nel mondo, e la loro sicurezza è matematicamente provata. Un algoritmo segreto e non analizzato potrebbe avere debolezze nascoste che solo l'attaccante conosce.

- Perché RSA con 2048 bit è equivalente ad AES con 112 bit?

    Perché i problemi matematici sottostanti hanno difficoltà diverse. Il brute-force su AES-112 richiede 2^112 operazioni. La fattorizzazione di un modulo RSA a 2048 bit, con i migliori algoritmi noti (General Number Field Sieve), richiede circa 2^112 operazioni equivalenti. La difficoltà della fattorizzazione cresce molto più lentamente all'aumentare della lunghezza della chiave rispetto al brute-force simmetrico.

- Cosa cambia con i computer quantistici?

    L'algoritmo di Shor (1994) permette a un computer quantistico sufficientemente potente di fattorizzare n in tempo polinomiale, rompendo RSA. Lo stesso vale per il logaritmo discreto (DH, ECC). AES resiste parzialmente: l'algoritmo di Grover riduce la sicurezza effettiva della metà (AES-256 scende a 128 bit di sicurezza quantistica), quindi AES-256 rimane sicuro. Per questo si lavora su crittografia post-quantum basata su problemi diversi (reticoli, codici a correzione d'errore).


---

> **Collegamento con altri argomenti**: VPN (cifratura del tunnel) — [[Appunti VPN — Tipologie, Tunneling, Protocolli]] | TLS/HTTPS — 13 giu | Firma digitale e certificati — 16 giu (prossimo) | CIA e attacchi — 15 giu
