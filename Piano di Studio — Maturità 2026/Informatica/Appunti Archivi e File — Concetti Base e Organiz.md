# Panoramica

Un **archivio** è un insieme di informazioni relative a oggetti dello stesso tipo, memorizzato su un supporto di memoria permanente (memoria di massa). Il **file** è la struttura fisica concreta che implementa l'archivio.

---

# Concetti Base

## Record, Campo, Archivio

| Termine | Definizione |
| --- | --- |
| **Campo** (field) | Unità elementare di informazione. Attributo di un record. Può essere **elementare** o **composto** (aggregato di più info semplici). |
| **Record** (logico) | Struttura composta da un insieme finito di campi eterogenei tra loro logicamente connessi. Corrisponde a un'entità del dominio. |
| **Archivio** | Struttura dati astratta composta da un insieme di record omogenei (tutti con gli stessi campi). |
| **File** | Struttura fisica di memoria che implementa l'archivio. Sequenza di byte o di record fisici su disco. |

> **Distinzione fondamentale**: un archivio è sempre implementato da uno o più file, ma un file non è sempre l'implementazione di un archivio (es. un file Word, un'immagine, un audio non sono archivi strutturati).

## Caratteristiche fondamentali di un archivio

- **Permanenza**: le informazioni devono essere conservate inalterate sul supporto per tutto il tempo necessario. Solo l'intervento umano può modificarle o distruggerle.
- **Razionalità**: le informazioni devono essere organizzate in modo da garantire un reperimento rapido e senza errori.
- **Sistematicità**: tutte le informazioni appartenenti allo stesso archivio devono essere strutturalmente uguali tra loro (stessi campi in ogni record).

## Record logico e record fisico

Il disco non legge e scrive un record alla volta: lavora sempre per **blocchi**, cioè porzioni di disco di dimensione fissa (di solito 512, 1024 o 4096 byte — sempre una potenza di 2). Questo crea una distinzione importante tra due "versioni" dello stesso record:

**Record logico** — il record così come lo vede il programmatore: un insieme di campi (es. nome, cognome, data di nascita). La sua dimensione è la somma delle dimensioni dei campi.

**Record fisico (blocco)** — l'unità minima che il disco legge o scrive in una singola operazione. La sua dimensione è fissa e decisa dal sistema operativo, non dal programmatore.

> Esempio concreto: se un record logico pesa 16 byte e il blocco fisico è 512 byte, in un blocco ci stanno 32 record logici. Il disco non può leggere solo 1 di quei 32 record: legge tutto il blocco da 512 byte in una volta sola e lo copia in RAM.

**Buffer**: area della RAM dove il sistema operativo copia il blocco fisico appena letto dal disco. Il programma poi legge i record logici che gli servono direttamente dal buffer, senza tornare ogni volta sul disco — molto più veloce.

**Fattore di bloccaggio**: quanti record logici stanno dentro un singolo blocco fisico.

| Fattore di bloccaggio | Situazione | Nome |
| --- | --- | --- |
| **> 1** (es. 32) | Più record logici stanno dentro un blocco | Record **bloccati** — caso normale, efficiente |
| **= 1** | Un record logico occupa esattamente un blocco | Record **sbloccati** |
| **< 1** (es. 0.5) | Un record logico è così grande che occupa più blocchi | **Multiblocco** — caso raro, poco efficiente |

---

# Chiave Primaria e Chiave Secondaria

## Chiave primaria

Campo o insieme di campi i cui valori **identificano univocamente** un record all'interno dell'archivio.

**Proprietà**:

- **Unicità**: non esistono due record con lo stesso valore di chiave
- **Non ridondanza**: non deve contenere campi superflui rispetto alla funzione identificativa

**Esempi**:

- Numero di matricola studente
- Codice fiscale (chiave "parlante": 16 caratteri che codificano cognome, nome, anno/mese/giorno nascita, comune, codice di controllo)
- Codice IBAN (chiave "parlante": sigla nazione + codice controllo internazionale + codice controllo nazionale + ABI + CAB + numero conto)
- Codice articolo magazzino

## Chiave secondaria

Chiave **non primaria** che identifica in genere **più record** (non uno solo). Si dice **selettiva** se individua un numero non elevato di record.

**Esempi**:

- `DataAperturaConto`: selettiva se applicata a una data specifica (pochi conti aperti quel giorno)
- `IdentifCorrentista`: identifica tutti i conti di una stessa persona

> Le chiavi secondarie si usano per velocizzare la ricerca su campi che non sono la chiave primaria (es. cerca tutti i clienti di Milano).

---

# Organizzazione degli Archivi

## Organizzazione fisica

Riguarda il **supporto fisico** di memoria:

| Tipo di supporto | Caratteristica | Accesso |
| --- | --- | --- |
| **Nastro** | Blocchi sequenziali, lettura testa a testa | Solo sequenziale |
| **Disco** (HDD, SSD) | Blocchi in settori/cilindri/tracce | Sequenziale **e** diretto |
- **Supporti ad accesso sequenziale** (nastri): per accedere al record N bisogna passare per i record 1…N-1. Organizzazione logica e fisica coincidono sempre.
- **Supporti ad accesso diretto** (dischi): si può accedere a qualsiasi blocco direttamente. Organizzazione logica e fisica possono differire.

## Organizzazione logica

Riguarda **come i record sono disposti** nell'archivio e come possono essere reperiti:

- **Sequenziale**: ogni record ha un predecessore e un successore (tranne il primo e l'ultimo). I record sono memorizzati uno dietro l'altro.
- **Non sequenziale**: i record sono memorizzati in modo sparso. L'accesso avviene tramite la chiave.

## Metodi di accesso

| Metodo | Descrizione | Tempo |
| --- | --- | --- |
| **Sequenziale** | Si accede a un record solo dopo tutti quelli precedenti | Proporzionale alla posizione |
| **Diretto** (random) | Ci si posiziona direttamente sul record tramite indirizzo | Indipendente dalla posizione |

> I supporti fisici ad accesso sequenziale possono ospitare **solo** archivi sequenziali. I supporti ad accesso diretto possono ospitare sia archivi sequenziali sia non sequenziali.

---

# Organizzazione Sequenziale

## Caratteristiche

**Archivio logico sequenziale**: i record sono registrati in posizioni contigue a partire dalla prima.

- Se l'ordine logico coincide con quello fisico → **archivio sequenziale ordinato**
- Se non c'è ordinamento → **archivio sequenziale seriale** (o non ordinato)

**Caratteristiche fondamentali**:

- Immissione solo **in coda** (non si perde l'ordine di inserimento)
- Vantaggioso per operazioni **batch (offline)**: si elabora tutto il file in blocco
- Inefficiente per operazioni **interattive (online)**: tempi di risposta elevati
- Unico metodo di accesso possibile: **sequenziale puro**

## Allocazione fisica sequenziale: allocazione contigua

Quando un file viene salvato su disco con allocazione contigua, tutti i suoi blocchi occupano posizioni consecutive: se il file inizia al blocco numero `b` ed è lungo `n` blocchi, occupa esattamente i blocchi `b, b+1, b+2, ..., b+n-1`.

Immagina il disco come una fila di cassetti numerati: il file occupa cassetti adiacenti, uno dopo l'altro senza salti.

**Vantaggio**: la testina del disco non deve saltare da un posto all'altro — legge tutto in un colpo solo, molto veloce.

**Problema — la frammentazione**: col tempo, man mano che i file vengono creati e cancellati, sul disco restano tanti "buchi" liberi sparsi. A un certo punto può succedere che lo spazio libero totale sia sufficiente per un nuovo file, ma non esista un blocco contiguo abbastanza grande da contenerlo tutto. Come se in una fila di cassetti ci fossero 10 cassetti liberi ma mai 5 di fila.

Per cercare dove mettere un file nuovo, il sistema operativo usa diverse strategie:

| Strategia | Come funziona |
| --- | --- |
| **First-fit** | Prende il primo buco libero abbastanza grande che trova, partendo dall'inizio |
| **Next-fit** | Come first-fit, ma riparte dal punto dove si era fermata l'ultima volta |
| **Best-fit** | Cerca il buco più piccolo che possa contenere il file (spreca meno spazio) |
| **Worst-fit** | Prende il buco più grande disponibile (lascia avanzi più grandi e riutilizzabili) |

Nessuna di queste strategie risolve davvero la frammentazione nel lungo periodo — la peggiorano tutte, solo più lentamente.

## Operazioni logiche sugli archivi sequenziali

- Inserimento

    **Archivio non ordinato**: nessun problema. Il record si aggiunge in coda o nella prima posizione libera.

    **Archivio ordinato**: bisogna trovare la posizione esatta e traslare tutti i record successivi per fare spazio. Soluzioni:

    - **Archivio differenziale**: i nuovi record vanno in un archivio temporaneo; periodicamente si fonde con il principale. Svantaggio: la ricerca deve scandire entrambi.
    - **Aree di overflow (trabocchi)**: aree libere predisposte per accogliere i nuovi record.
        - **Distribuite**: sparse lungo l'archivio principale o in un archivio differenziale
        - **Concentrate**: tutte in un unico punto dell'archivio o in un archivio differenziale separato
- Aggiornamento (riscrittura)

    **Accesso sequenziale**: si deve riscrivere l'intero archivio. Le modifiche vengono raccolte in un archivio differenziale, poi si fonde con il principale.

    **Accesso diretto**: molto semplice. 1) Ricerca del record di chiave K. 2) Modifica in memoria. 3) Riscrittura nella stessa posizione.

- Cancellazione

    **Accesso sequenziale**: si riscrive l'intero archivio senza il record eliminato su un archivio differenziale.

    **Accesso diretto**:

    - **Cancellazione logica**: si marca il record con un campo speciale (es. flag = 1). Il record rimane fisicamente ma viene ignorato.
    - **Cancellazione fisica**: periodicamente si compatta l'archivio eliminando fisicamente i record marcati.
- Ricerca

    **Su supporto sequenziale (nastro)**:

    - Ricerca completa: (N+1)/2 accessi (successo), N accessi (insuccesso)
    - Se le chiavi più frequenti sono in testa: proporzionale alla probabilità della chiave (successo), N (insuccesso)
    - Archivio ordinato — ricerca sequenziale ottimizzata: (N+1)/2 sia per successo che insuccesso (ci si ferma quando si supera la chiave cercata)

    **Su supporto ad accesso diretto**:

    - Indirizzo noto: 1 accesso
    - Archivio disordinato: come accesso sequenziale
    - Archivio ordinato — **ricerca binaria**: log₂(N) accessi (sia successo che insuccesso, sia caso medio che pessimo)
    - Archivio ordinato — **ricerca interpolata**: log₂(log₂(N)) accessi (solo se le chiavi sono distribuite uniformemente; caso medio)

    **Ricerca binaria** — algoritmo:

    1. Posizionati al record centrale della porzione da esaminare
    2. Se la chiave cercata = chiave del record → trovata
    3. Se ci sono altri record da esaminare:
        - chiave cercata > chiave record → applica la ricerca binaria alla metà destra
        - chiave cercata < chiave record → applica la ricerca binaria alla metà sinistra
    4. Se non ci sono altri record → chiave non trovata

---

# Organizzazione Sequenziale con Indice (Indexed Sequential)

## Struttura

Variante dell'organizzazione sequenziale per supporti ad accesso diretto. Usa uno o più **indici** per velocizzare la ricerca senza scansione completa.

Due elementi fondamentali:

- **Archivio primario**: record consecutivi (possono essere ordinati)
- **Archivio secondario (indice / dizionario)**: ogni record è composto da:
    - **Campo chiave**: la chiave del record nel primario
    - **Campo puntatore**: posizione del record nell'archivio primario

L'indice consente di stabilire una corrispondenza tra ogni chiave e la posizione del relativo record.

## Strutture ordinate con indice a pagine

L'archivio primario viene diviso in gruppi di record chiamati **sottoarchivi** (o pagine), ciascuno con lo stesso numero di record. L'indice tiene traccia di dove inizia ogni gruppo, memorizzando la **chiave più alta** contenuta in quel gruppo e il **numero del sottoarchivio** (puntatore).

Pensa all'indice come all'indice analitico di un libro: non elenca ogni parola, ma dice "le parole dalla A alla C sono a pagina 10, dalla D alla G a pagina 24", ecc.

```
INDICE                        ARCHIVIO PRIMARIO
Chiave più alta | Sottoarch.
      20        |     1    →  sottoarchivio 1: [2, 5, 20]
      85        |     2    →  sottoarchivio 2: [48, 52, 85]
     190        |     3    →  sottoarchivio 3: [125, 154, 190]
     214        |     4    →  sottoarchivio 4: [199, 211, 214]
```

Il puntatore all'indice indica implicitamente anche la chiave più bassa del gruppo: siccome i record sono ordinati, la chiave più bassa del sottoarchivio 2 è quella subito dopo la chiave più alta del sottoarchivio 1.

**Come si cerca la chiave K** (es. K = 60):

1. Si scorre l'indice cercando la prima chiave `≥ 60` → si trova `85` (sottoarchivio 2)
2. Si va nel sottoarchivio 2
3. Si cerca 60 dentro quel gruppo → non c'è (sta tra 52 e 85 ma non è presente)

## Aggiornamento: aree di overflow

Problema: i sottoarchivi hanno dimensione fissa. Se un sottoarchivio è già pieno e bisogna inserire un nuovo record che appartiene a quel gruppo, non c'è spazio.

Soluzione: si predispongono delle **aree di overflow** (aree di trabocco) — spazio libero riservato apposta per i record in eccesso. Quando un sottoarchivio trabocca, il record che non ci sta va nell'area di overflow.

Per tener traccia di tutto, ogni riga dell'indice viene estesa con due campi aggiuntivi:

```
(Kh, P, Kovf, Povf)
  │    │   │     └─ puntatore all'area di overflow di quel sottoarchivio
  │    │   └─────── chiave più alta presente nell'area di overflow
  │    └─────────── numero del sottoarchivio
  └──────────────── chiave più alta nel sottoarchivio principale
```

Se non c'è overflow, Kovf e Povf sono vuoti (NIL). Quando si cerca la chiave K, si controlla prima il sottoarchivio principale e, solo se è pieno e K è nell'intervallo di overflow, si va a cercare anche lì.

## Indici multipli (a più livelli)

Se i sottoarchivi diventano molti, anche l'indice diventa grande e cercarlo diventa lento. La soluzione è costruire un **indice dell'indice**: un secondo indice più piccolo che punta a sezioni del primo indice, che a sua volta punta ai sottoarchivi.

Funziona esattamente come un libro con un indice per capitoli e un indice analitico: per trovare una parola vai prima all'indice dei capitoli, poi all'indice del capitolo giusto, poi alla pagina.

```
Indice livello 1 (piccolo, poche voci)
  └→ Indice livello 2 (medio)
       └→ Indice livello 3 (dettagliato)
            └→ Archivio primario (i dati veri)
```

In fase di ricerca si scende livello per livello: ogni livello restringe la zona da guardare, fino ad arrivare al sottoarchivio esatto.

**Esempio tipico su hard disk**:

- **Indice di unità** → su quale disco fisico cercare (se ce ne sono più)
- **Indice di cilindro** → su quale cilindro di quel disco
- **Indice di traccia** → su quale traccia di quel cilindro

Ogni livello riduce drasticamente il numero di posizioni da esaminare al livello successivo.

## Archivio secondario denso vs sparso

|  | Denso | Sparso |
| --- | --- | --- |
| **Definizione** | Un'entry per ogni record del primario | Un'entry per ogni blocco (o ogni k record) del primario |
| **Quando si usa** | Primario disordinato o per accesso su qualsiasi chiave | Solo se il primario è ordinato per la chiave di ricerca |
| **Vantaggio** | Ricerca rapida su qualsiasi chiave | Occupa meno spazio, meno blocchi da leggere |
| **Svantaggio** | Occupa più spazio | Non funziona se il primario è disordinato |

---

# Formati di File Sequenziali

- File di testo

    Contiene solo caratteri ASCII/Unicode, senza informazioni di formato (colore, dimensione, font). Leggibile con qualsiasi editor di testo.

    **Caratteri di controllo**: `tab` (tabulazione), `CR` (Carriage Return — ritorno a capo), `LF` (Line Feed — avanzamento riga). Su DOS/Windows: `CR+LF`; su Unix/Linux: solo `LF`.

    **Uso**: file di configurazione (`.ini`), log, dati di scambio.

- File CSV (Comma Separated Values)

    File di testo in cui ogni riga è un record e i campi sono separati da virgola (o punto e virgola). Record separati da `CR+LF`.

    Regole:

    - Campi contenenti virgole vanno racchiusi tra doppie virgolette
    - Un carattere `"` dentro un campo va raddoppiato: `""`
    - Nessuno spazio prima/dopo i campi (a meno che non siano tra virgolette)

    Uso: scambio dati tra sistemi diversi (database, fogli di calcolo, piattaforme incompatibili).

- File XML (eXtensible Markup Language)

    File di testo strutturato ad albero con tag personalizzabili. A differenza di HTML (che definisce la presentazione), XML definisce la struttura e il significato dei dati.

    Struttura:

    - Un solo elemento radice (root)
    - Elementi annidati gerarchicamente
    - Tag di apertura e chiusura: `<ELEMENTO>...</ELEMENTO>`
    - Attributi nei tag: `<ELEMENTO attr="valore">`

    Uso: scambio dati tra applicazioni, file di configurazione, export da DBMS.

- File binari

    Sequenza di byte senza struttura testuale. Non leggibile direttamente dall'uomo — aperti con editor di testo mostrano caratteri incomprensibili.

    Contenuto: immagini, audio, eseguibili, dati compressi, rappresentazioni binarie di numeri.

    Differenza da file di testo: non è nella macchina (entrambi sono byte) ma in cosa i byte rappresentano e come vengono interpretati.


---

# Operazioni Fisiche e Logiche

## Operazioni fisiche

Coinvolgono il file come struttura fisica: **lettura** e **scrittura** di record sul disco. Comportano accesso sia alla memoria di massa che alla RAM (tramite buffer).

## Operazioni logiche principali

| Operazione | Descrizione |
| --- | --- |
| **Apertura** | Apre un archivio precedentemente creato |
| **Inserimento** | Aggiunge un nuovo record |
| **Cancellazione logica** | Marca il record come cancellato (campo flag) |
| **Cancellazione fisica** | Rimuove effettivamente il record dall'archivio |
| **Aggiornamento** | Modifica i campi di un record (non la chiave) |
| **Ricerca** | Trova record per valore di chiave |
| **Scansione** | Scorre tutti i record per compiere un'operazione |
| **Ordinamento** | Riordina i record per un campo (ottimizza ricerca e scansione) |
| **Chiusura** | Termina le operazioni, completa il trasferimento a disco |

> **Ordine fisico vs logico**: un archivio si dice **ordinato** quando ordine fisico e logico coincidono. È possibile avere un ordine logico diverso da quello fisico usando puntatori.

---

# Domande tipiche da orale

- Differenza tra record logico e record fisico

    Il **record logico** è il record così come lo vede il programmatore: un insieme di campi (nome, cognome, data…). Il **record fisico** (o blocco) è invece l'unità minima che il disco legge o scrive in una sola operazione — ha dimensione fissa decisa dal sistema operativo (es. 512 byte). Quando il programma chiede un record logico, il sistema operativo legge l'intero blocco fisico che lo contiene e lo copia nel buffer in RAM; il programma poi legge il suo record da lì. Il **fattore di bloccaggio** dice quanti record logici stanno in un blocco: se è 32, con una sola lettura disco si caricano 32 record in RAM.

- Cos'è un archivio sequenziale ordinato e perché conviene?

    Un archivio sequenziale ordinato è un archivio in cui l'ordine logico dei record (secondo la chiave) coincide con l'ordine fisico su disco. Conviene perché abilita la ricerca binaria (log₂N accessi invece di N/2), la ricerca sequenziale ottimizzata che si interrompe appena supera la chiave cercata, e algoritmi di fusione efficienti.

- Cosa sono le aree di overflow e perché si usano?

    Sono aree libere predisposte per accogliere i record inseriti in un archivio ordinato senza dover traslare tutti i record successivi. Possono essere distribuite (sparse lungo l'archivio) o concentrate (in un unico punto). Migliorano le prestazioni di inserimento a scapito di quelle di ricerca, che deve controllare anche le aree di overflow.

- Differenza tra archivio secondario denso e sparso

    L'indice denso ha un'entry per ogni record del primario: individua qualsiasi record direttamente, funziona anche se il primario è disordinato, ma occupa più spazio. L'indice sparso ha un'entry per ogni blocco (o pagina) del primario: funziona solo se il primario è ordinato per quella chiave, occupa molto meno spazio e richiede meno accessi all'indice.

- Ricerca binaria: quanti accessi servono?

    log₂(N) accessi sia in caso di successo che di insuccesso, sia nel caso medio che in quello pessimo. Dove N è il numero di record. Esempio: 1000 record → max 10 accessi invece di 500 con ricerca sequenziale. La ricerca interpolata (quando le chiavi sono distribuite uniformemente) scende a log₂(log₂(N)) nel caso medio.


---

> **Collegamento con altri argomenti**: Archivi non sequenziali (hash, b-alberi) — [[Informatica indice]] 3-11 giu | DBMS e SQL — già studiato | PHP e accesso ai dati — 3-5 giu
