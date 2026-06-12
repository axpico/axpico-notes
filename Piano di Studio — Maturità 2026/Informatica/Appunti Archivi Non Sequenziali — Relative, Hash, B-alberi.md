# Panoramica

L'**organizzazione non sequenziale** consente di accedere a un record **senza dover attraversare tutti quelli precedenti**, ricavando direttamente l'indirizzo tramite la chiave del record stesso.

Tre implementazioni principali:

- **Organizzazione relative**: la chiave coincide con la posizione fisica
- **Organizzazione hash**: la chiave viene trasformata in un indirizzo tramite una funzione
- **Organizzazione a B-alberi**: struttura ad albero bilanciato in altezza

---

# Organizzazione Logica Non Sequenziale

## Concetti fondamentali

L'organizzazione non sequenziale è possibile su **supporti ad accesso diretto** (dischi). Non richiede che i record siano memorizzati in maniera contigua: ogni record non ha un predecessore o successore definito.

**Requisito**: un campo del record deve fungere da **chiave primaria** che crea una relazione univoca tra il valore della chiave e l'indirizzo del record.

Operazioni consentite: **lettura, scrittura, riscrittura, cancellazione, posizionamento**.

## Organizzazione fisica: allocazione concatenata e indicizzata

Un archivio fisico non sequenziale è composto da blocchi non necessariamente contigui. Il SO usa due tecniche per collegarli:

| Tecnica | Come funziona | Usata in |
| --- | --- | --- |
| **Allocazione concatenata** | Ogni blocco contiene un puntatore al blocco successivo (lista concatenata). Per accedere al blocco N occorre percorrere i blocchi 1…N-1. | FAT (DOS, Windows, macOS) |
| **Allocazione indicizzata** | Tutti i riferimenti ai blocchi del file stanno in un vettore chiamato **blocco indice**. Per il blocco N si legge l'elemento N del blocco indice → accesso diretto. | Unix (i-node) |

**FAT** (File Allocation Table): tabella che rappresenta l'immagine virtuale dei blocchi su disco e contiene i riferimenti tra blocchi. Evita di memorizzarli dentro il file stesso.

**i-node** (Unix): il blocco indice di ogni file. Il suo indirizzo fisico è memorizzato nella directory che contiene il file.

---

# Organizzazione Relative

## Definizione

Nell'organizzazione relative la **chiave primaria identifica univocamente sia il record sia l'indirizzo logico** in cui è registrato. La chiave corrisponde alla posizione del record all'interno dell'archivio.

> Esempio: archivio delle temperature rilevate ogni ora — la temperatura delle ore 12 è nella dodicesima riga. Archivio dei posti di un aereo numerati 1…N — il record del posto k è alla posizione k.

## Come si calcola l'indirizzo fisico

Il SO calcola automaticamente:

```
Indirizzo fisico del record k =
  Indirizzo fisico del 1° record + (k - 1) × dimensione del record
```

## Vantaggi e svantaggi

| Vantaggi | Svantaggi |
| --- | --- |
| Accesso diretto immediato tramite chiave numerica | Difficile stabilire una relazione univoca tra chiave primaria generica e posizione |
| Supporta sia accesso sequenziale che diretto | Obbliga a usare chiavi strettamente legate alla posizione, oppure metodi di randomizzazione |
| Ottimo per operazioni interattive | La cancellazione avviene solo logicamente (tranne l'ultimo record) |
| Con puntatori si può ottenere ordine logico diverso da quello fisico | Solo su supporti ad accesso diretto |

---

# Organizzazione Hash

## Definizione e principio

La **tecnica hash** usa una funzione H (funzione hash) che trasforma la chiave K di ogni record in un numero intero X (**indirizzo hash**), compreso tra 1 e N (dove N è il numero di indirizzi logici disponibili):

```
H(K) = X
```

L'indirizzo X deve essere ricalcolato ogni volta che si accede al record di chiave K per operazioni di I/O.

## Caratteristiche di una funzione hash ottimale

1. **Facilmente calcolabile**: calcoli semplici, per non appesantire il tempo di accesso
2. **Deterministica**: stessa chiave → stesso indirizzo sempre
3. **Distribuzione uniforme**: indirizzi distribuiti uniformemente nell'archivio
4. **Distribuzione casuale su chiavi simili**: chiavi come X1, X2, X3 oppure DARE/MARE/CARE devono produrre indirizzi diversi
5. **Copertura totale**: coprire l'intero intervallo degli indirizzi disponibili
6. **Indirizzi diversi per chiavi diverse**: idealmente una corrispondenza uno-a-uno (**trasformazione perfetta**)
7. **Minimo numero di collisioni**: con procedure per gestire i sinonimi

> La **trasformazione perfetta** (corrispondenza 1-a-1 tra chiave e indirizzo) è quasi impossibile nella pratica: richiederebbe che il numero di record fisici sia uguale al numero di possibili valori della chiave, con enorme spreco di memoria.

## Collisioni e sinonimi

Quando due chiavi diverse producono lo stesso indirizzo si genera una **collisione**. Le chiavi che producono lo stesso indirizzo si chiamano **sinonimi**.

La funzione hash reale produce una corrispondenza **molti-a-uno**: bisogna quindi prevedere procedure di **gestione delle collisioni**.

---

# Metodi di Calcolo degli Indirizzi Hash

- Metodo del troncamento

    Si estrare un sottoinsieme di cifre dalla chiave (es. le ultime 3) che rappresentano direttamente l'indirizzo.

    **Quando si usa**: chiave numerica con molte cifre, numero di record limitato.

    **Esempio** (palestra, 1000 record, chiave = numero tessera a 7 cifre):

    ```
    H(1548968) + 1 = 969
    H(0003254) + 1 = 255
    H(3293001) + 1 = 002  ← sinonimo
    H(6331254) + 1 = 255  ← sinonimo (stesse ultime 3 cifre)
    ```

    **Su chiave alfanumerica**: si estraggono gli ultimi k caratteri, si converte in base 26 (A=0, B=1, … Z=25), poi si applica troncamento. Esempio:

    ```
    H(HELLOCIAO) → CIAO → C×26³ + I×26² + A×26¹ + O×26⁰
                 = 2×17576 + 8×676 + 0 + 14×1 = 40574
    ```

    **Vantaggi**: molto efficiente quando le chiavi sono essenzialmente consecutive.

    **Svantaggi**: genera sinonimi quando le chiavi hanno le stesse ultime cifre; l'archivio deve avere dimensione pari a una potenza di 10.

- Metodo folding ("piegare")

    Si divide la chiave numerica in due o più parti e si sommano tra loro. L'immagine mentale è quella di "piegare" la chiave su se stessa come un foglio.

    **Esempio**:

    ```
    H(563710) = 365 + 710 = 1075
    ```

    Se la somma supera il numero massimo di cifre dell'indirizzo, si tronca.

    **Svantaggi**: genera collisioni (H(563710) = H(349132)); stesso problema del troncamento sull'arrotondamento a potenza di 10.

- Metodo della divisione modulo N

    L'indirizzo si ottiene dal resto della divisione della chiave per il numero massimo di record:

    ```
    H(K) = (K MOD N) + 1
    ```

    Il `+1` sposta l'intervallo da [0, N-1] a [1, N].

    **Esempio** (archivio da 20 record):

    ```
    Chiave  H(K) = (K mod 20) + 1
    92      12 + 1 = 13
    64       4 + 1 = 5
    21       1 + 1 = 2
    80       0 + 1 = 1
    12      12 + 1 = 13  ← collisione con 92
    13      13 + 1 = 14
    9        9 + 1 = 10
    88       8 + 1 = 9
    11      11 + 1 = 12
    58      18 + 1 = 19
    ```

    **Vantaggi rispetto agli altri metodi**:

    - Applicabile anche quando N non è una potenza di 10
    - Gli indirizzi generati non necessitano di troncamento (il modulo garantisce che stiano in [0, N-1])
    - La scelta di N è il fattore fondamentale per minimizzare le collisioni

---

# Gestione delle Collisioni

Le tecniche di gestione delle collisioni servono a individuare un **indirizzo libero** per la chiave K quando H(K) restituisce un indirizzo già occupato.

> In fase di **inserimento**: si calcola H(K), si testa se la posizione è libera; se occupata si cerca la prossima posizione libera.

> In fase di **ricerca**: si calcola H(K), si accede al record; se la chiave non coincide, si scandisce secondo la stessa strategia usata in inserimento.
- Scansione lineare (indirizzamento aperto)

    When a collision occurs, the archive is scanned linearly to find the first free position, moving by a fixed step p.

    Se **p = 1** → **scansione lineare con passo unitario**: si esamina la posizione successiva, poi quella dopo, ecc. Se si raggiunge la fine dell'archivio, si riparte dall'inizio. Il processo si interrompe quando si trova un posto libero, oppure quando è stata esaminata metà dell'archivio (archivio pieno).

    **Esempio** (archivio da 9 record, divisione mod 9):

    ```
    Chiavi da inserire: 9  28  29  35  24  48  71  64

    9  → pos 1   (OK)
    28 → pos 2   (OK)
    29 → pos 3   (OK)
    35 → pos 9   (OK)
    24 → pos 7   (OK)
    48 → pos 4   (OK)
    71 → pos 9   COLLISIONE con 35
       → pos 1   COLLISIONE con 9
       → pos 2   COLLISIONE con 28
       → pos 3   COLLISIONE con 29
       → pos 4   COLLISIONE con 48
       → pos 5   LIBERA → memorizzato in 5
    64 → pos 2   COLLISIONE con 28
       → pos 3   COLLISIONE
       → pos 4   COLLISIONE
       → pos 5   COLLISIONE con 71
       → pos 6   LIBERA → memorizzato in 6
    ```

    **Problema**: **agglomerazione (clustering)** — si formano lunghe catene di record adiacenti occupati (cluster), che rallentano significativamente l'accesso.

- Scansione non lineare (pseudo-random)

    Variante dell'indirizzamento aperto. Invece di spostarsi di un passo fisso, ogni collisione genera un **nuovo indirizzo di rehash** tramite una **funzione di rehash** che produce numeri pseudo-casuali.

    **Perché pseudo-casuale e non casuale?** In fase di ricerca devono essere ricalcolati esattamente gli stessi indirizzi usati in fase di inserimento: la sequenza deve essere riproducibile.

    **Vantaggio rispetto alla scansione lineare**: risolve il problema del clustering perché i record non si addensano in zone contigue.


---

# B-alberi (Balanced Trees)

## Perché i B-alberi?

Gli alberi binari di ricerca bilanciati sono efficienti, ma bastano uno o due inserimenti per squilibrarli e costringere a un ribilanciamento costoso. I **B-alberi** sono nati nei primi anni '70 per offrire un modello più efficiente per la gestione dinamica e ordinata di archivi.

Sono alberi **ordinati secondo la chiave** e **perfettamente bilanciati in altezza** (tutte le foglie allo stesso livello). Non sono alberi binari: ogni nodo può contenere più chiavi e avere più di 2 figli.

**Vantaggi**:

- Ottime prestazioni sia per ricerca che per aggiornamento (entrambe con procedure semplici)
- Permettono elaborazioni di tipo sequenziale sull'archivio primario senza riorganizzazione

## Definizione formale: B-albero di ordine m

Un B-albero di ordine m soddisfa le seguenti proprietà:

1. **Perfettamente bilanciato in altezza**: tutte le foglie sono allo stesso livello
2. Il **nodo radice** ha un numero d di figli tale che: **1 ≤ d ≤ 2m + 1**
3. Ogni **nodo non radice** ha un numero d di figli tale che: **m ≤ d ≤ 2m**
4. Ogni nodo ha le chiavi disposte in **ordine crescente**
5. Ogni nodo, esclusa la radice, contiene **almeno m chiavi** e al massimo **2m chiavi**
6. La radice contiene al massimo **2m chiavi**

> Esempio di B-albero di ordine 3: radice con al massimo 6 chiavi e fino a 7 figli. Ogni nodo non radice ha tra 3 e 6 chiavi.

## Struttura di un nodo

```
| n | P₀ | K₁ | P₁ | K₂ | P₂ | ... | Kᵢ | Pᵢ | Kᵢ₊₁ | ... | Kₘ | Pₘ |
```

- **n**: numero di chiavi presenti nel nodo
- **P₀**: puntatore al sottoalbero con chiavi **< K₁** (tutte minori della più piccola)
- **Pᵢ**: puntatore al sottoalbero con chiavi comprese tra **Kᵢ** e **Kᵢ₊₁**
- **Pₘ**: puntatore al sottoalbero con chiavi **> Kₘ** (tutte maggiori della più grande)

## Ricerca in un B-albero

Analoga alla ricerca in un albero binario di ricerca, ma generalizzata a nodi con più chiavi:

1. Si parte dalla **radice**
2. Nel nodo corrente si cerca K tra le chiavi memorizzate
3. Se trovata → successo
4. Se non trovata → si sceglie il sottoalbero corrispondente all'intervallo in cui cade K (tramite i puntatori Pᵢ)
5. Si ripete finché K è trovata (successo) oppure si raggiunge una foglia senza trovare K (insuccesso)

## Inserimento e splitting

L'inserimento deve mantenere l'albero sempre bilanciato.

**Caso normale**: il nodo foglia ha spazio → si inserisce la chiave rispettando l'ordine crescente.

**Nodo saturo** (già 2m chiavi): si applica lo **splitting** (sdoppiamento):

1. Le chiavi vengono divise in parti uguali
2. La chiave **centrale** sale al nodo di livello superiore
3. Se anche il nodo superiore è saturo, si ripete il procedimento verso l'alto
4. Se la radice è satura, si crea una nuova radice → l'altezza dell'albero aumenta di 1

---

# Altezza di un B-albero (grado minimo t)

Notazione: **grado minimo t** — ogni nodo (tranne la radice) ha tra **t-1** e **2t-1** chiavi, e tra **t** e **2t** figli.

## Numero minimo e massimo di chiavi per altezza h

|  | Formula | Significato |
| --- | --- | --- |
| **N_min(h)** | 2·tʰ − 1 | Caso più vuoto (nodi riempiti al minimo) |
| **N_max(h)** | (2t)^(h+1) − 1 | Caso più pieno (tutti i nodi saturi) |

## Altezza massima (caso pessimo)

```
h_max = ⌊log_t((N+1)/2)⌋
```

## Altezza minima (caso ottimo)

```
h_min = ⌈log_{2t}(N+1)⌉ − 1
```

## Esempio: t = 2, N = 200

```
h_max = ⌊log₂(101)⌋ = 6
h_min = ⌈log₄(201)⌉ − 1 = ⌈3.83⌉ − 1 = 3
```

Un B-albero di grado minimo 2 con 200 chiavi ha altezza compresa tra **3 e 6**.

## Tabella (t = 2: ogni nodo ha tra 1 e 3 chiavi)

| Altezza | N_min | N_max | Intervallo |
| --- | --- | --- | --- |
| 0 | 1 | 3 | da 1 a 3 |
| 1 | 3 | 15 | da 3 a 15 |
| 2 | 7 | 63 | da 7 a 63 |
| 3 | 15 | 255 | da 15 a 255 |
| 4 | 31 | 1023 | da 31 a 1023 |
| 5 | 63 | 4095 | da 63 a 4095 |
| 6 | 127 | 16383 | da 127 a 16383 |
| 7 | 255 | 65535 | da 255 a 65535 |

> **Come leggere la tabella**: se N = 200, l'altezza non può essere < 3 (perché 200 > 63 = N_max a h=2) e non può essere > 6 (perché 200 < 255 = N_min a h=7). Quindi altezza tra 3 e 6.

---

# Confronto tra le Organizzazioni

| Organizzazione | Accesso | Quando usarla | Limite principale |
| --- | --- | --- | --- |
| **Sequenziale** | Sequenziale puro | Elaborazioni batch, archivi statici | Inefficiente per ricerche e aggiornamenti frequenti |
| **Relative** | Diretto (chiave = posizione) | Chiave numerica consecutiva con poche lacune | Chiave deve coincidere con la posizione |
| **Hash** | Diretto tramite funzione | Ricerche per chiave esatta, alta frequenza | Collisioni, nessun ordinamento |
| **B-albero** | Diretto + ordinato | Ricerche per intervallo, archivi dinamici | Struttura più complessa da gestire |

---

# Domande tipiche da orale

- Cos'è l'organizzazione hash e cosa sono le collisioni?

    L'organizzazione hash usa una funzione H(K) per trasformare la chiave K in un indirizzo logico X. Quando due chiavi diverse producono lo stesso indirizzo si ha una **collisione**. Le due chiavi si chiamano **sinonimi**. Poiché è quasi impossibile evitare le collisioni, ogni sistema hash deve prevedere una strategia di gestione. Le più comuni sono la scansione lineare (si cerca il prossimo posto libero in ordine) e la scansione pseudo-random (si usa una funzione di rehash per generare un nuovo indirizzo casuale).

- Cos'è il clustering e perché è un problema?

    Il clustering (agglomerazione o addensamento primario) è un effetto della scansione lineare: le catene di sinonimi tendono a unirsi formando lunghi blocchi di record adiacenti occupati. Quando arriva un nuovo record con collisione in quell'area, deve attraversare tutta la catena esistente prima di trovare uno spazio libero. Questo rallenta significativamente sia l'inserimento che la ricerca. La scansione pseudo-random risolve questo problema perché i salti sono pseudo-casuali e non formano catene contigue.

- Cos'è un B-albero e perché è bilanciato?

    Un B-albero di ordine m è un albero di ricerca in cui ogni nodo può contenere più chiavi (da m a 2m, tranne la radice) e avere più figli. È perfettamente bilanciato in altezza: tutte le foglie si trovano allo stesso livello. Il bilanciamento è garantito dalle operazioni di splitting (sdoppiamento) durante gli inserimenti: quando un nodo è saturo, la chiave centrale sale al nodo padre, mantenendo l'altezza uniforme senza costi di ribilanciamento globale (come invece accade negli alberi AVL).

- Differenza tra scansione lineare e pseudo-random

    Entrambi sono metodi per gestire le collisioni nell'hash. La scansione lineare si sposta di un passo fisso (di solito 1) fino al primo posto libero: semplice ma crea clustering. La scansione pseudo-random usa una funzione di rehash per generare un nuovo indirizzo ad ogni collisione: l'indirizzo è pseudo-casuale (non puramente casuale) perché in fase di ricerca deve essere riprodotta la stessa sequenza di indirizzi usata in inserimento.

- Come si calcola l'altezza di un B-albero?

    Dato il grado minimo t e il numero di chiavi N:

    - **Altezza massima** (caso pessimo, nodi più vuoti possibili): h_max = ⌊log_t((N+1)/2)⌋
    - **Altezza minima** (caso ottimo, tutti i nodi pieni): h_min = ⌈log_{2t}(N+1)⌉ − 1

    Esempio: t=2, N=200 → altezza tra 3 e 6.

- Differenza tra FAT e i-node

    Entrambi sono tecniche di allocazione non contigua su disco. La **FAT** (File Allocation Table) è una tabella centralizzata che contiene i riferimenti tra i blocchi di tutti i file: ogni cella punta al blocco successivo. Usata in DOS, Windows, macOS. Il problema è che su dischi grandi la FAT diventa enorme. L'**i-node** (Unix) è invece un blocco indice per singolo file: contiene l'elenco degli indirizzi fisici di tutti i blocchi del file. Per accedere al blocco N si legge direttamente l'elemento N dell'i-node. Più efficiente su dischi grandi.


---

> **Collegamento con altri argomenti**: Archivi sequenziali → [Appunti: Archivi e File — Concetti Base e Organizzazione Sequenziale](Appunti%20Archivi%20e%20File%20—%20Concetti%20Base%20e%20Organiz.md) | DBMS e SQL → [Appunti: DBMS & DB Distribuiti](Appunti%20DBMS%20&%20DB%20Distribuiti.md)
