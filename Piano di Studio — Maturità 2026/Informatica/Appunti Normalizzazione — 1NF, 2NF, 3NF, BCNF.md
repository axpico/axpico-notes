## Perché normalizzare?

La **normalizzazione** è il processo che porta uno schema relazionale a rispettare progressivamente le **forme normali**, eliminando ridondanze e le **anomalie** che ne derivano. È l'ultimo passo della [[Progettazione Logica]], dopo la traduzione ER → Relazionale.

> Decomposizione **senza perdita di informazione** (lossless join): scomponendo una tabella in due o più tabelle più piccole, deve essere sempre possibile ricostruire (via JOIN) esattamente i dati originali.

### Le tre anomalie

| Anomalia | Descrizione | Esempio |
| --- | --- | --- |
| **Inserimento** | Non posso inserire un'informazione senza inserirne un'altra, magari non ancora disponibile | Non posso registrare un nuovo corso se non ho ancora uno studente iscritto |
| **Cancellazione** | Cancellando una riga perdo anche informazioni "indipendenti" da essa | Se l'unico studente iscritto a un corso si cancella, perdo anche i dati del corso (NomeCorso, CFU, Docente) |
| **Aggiornamento** | Lo stesso dato è ripetuto in più righe → rischio di incoerenza se non aggiornato ovunque | Se cambia il nome di un corso, devo aggiornare tutte le righe di ISCRIZIONE che lo riportano |

> Esempio di tabella **non normalizzata**:

```
ISCRIZIONI(Matricola, NomeStudente, CodCorso, NomeCorso, CFU, Docente, Voto)
```

- `NomeStudente` si ripete per ogni corso a cui lo studente è iscritto
- `NomeCorso`, `CFU`, `Docente` si ripetono per ogni studente iscritto allo stesso corso

---

## Dipendenze funzionali — richiami veloci

Una **dipendenza funzionale (FD)** `X → Y` significa: *per ogni coppia di righe con lo stesso valore di X, il valore di Y deve essere lo stesso*.

- **X** = determinante
- **Y** = dipendente

| Tipo di FD | Definizione | Rilevante per |
| --- | --- | --- |
| **Completa (full FD)** | `X → Y` e nessun sottoinsieme proprio di X determina Y | 2NF |
| **Parziale** | Y dipende solo da *una parte* di una chiave composita X | violazione 2NF |
| **Transitiva** | `X → Y` e `Y → Z` (con Y non chiave) ⇒ `X → Z` | violazione 3NF |
| **Banale** | `X → Y` con Y ⊆ X (sempre vera, non interessante) | — |

> **Attributo primo (prime)**: fa parte di almeno una chiave candidata.
> **Attributo non primo**: non fa parte di nessuna chiave candidata.

---

## Prima Forma Normale (1NF)

Una relazione è in **1NF** se:

- ogni cella contiene un valore **atomico** (non scomponibile, non una lista)
- non esistono **gruppi ripetuti** (attributi multivalore)
- ogni riga è distinguibile (esiste una chiave)

> Violazione:

```
STUDENTE(Matricola, Nome, Telefoni)
123, "Mario Rossi", "333-1111111, 333-2222222"
```

`Telefoni` contiene più valori nella stessa cella → non atomico.

> Correzione — Regola 7 (attributo multivalore → tabella separata):

```sql
STUDENTE(Matricola PK, Nome)
TELEFONO(Matricola_FK, Numero, PRIMARY KEY (Matricola_FK, Numero))
```

---

## Seconda Forma Normale (2NF)

Una relazione è in **2NF** se:

- è in **1NF**, **e**
- ogni attributo non-chiave dipende dalla **chiave primaria nella sua interezza** (nessuna dipendenza parziale)

> La 2NF è rilevante **solo se la PK è composita**. Se la PK è formata da un solo attributo, la relazione è automaticamente in 2NF (non possono esistere dipendenze "parziali" da una chiave singola).

> Violazione:

```
ISCRIZIONE(Matricola_FK, CodCorso_FK, NomeCorso, CFU, Voto)
PK = (Matricola_FK, CodCorso_FK)
```

- `Voto` dipende dall'**intera** PK → OK
- `NomeCorso` e `CFU` dipendono **solo da** `CodCorso_FK` → dipendenza **parziale**

> Decomposizione:

```sql
CORSO(CodCorso PK, NomeCorso, CFU)

ISCRIZIONE(
  Matricola_FK → STUDENTE(Matricola),
  CodCorso_FK  → CORSO(CodCorso),
  Voto,
  PRIMARY KEY (Matricola_FK, CodCorso_FK)
)
```

---

## Terza Forma Normale (3NF)

Una relazione è in **3NF** se:

- è in **2NF**, **e**
- non esistono **dipendenze transitive** verso attributi non-chiave → ogni attributo non-chiave dipende **direttamente** dalla chiave, non tramite un altro attributo non-chiave

> Violazione:

```
IMPIEGATO(Matricola PK, Nome, CodDip, NomeDip, Budget)
```

- `Matricola → CodDip` (CodDip dipende dalla chiave)
- `CodDip → NomeDip`, `CodDip → Budget` (NomeDip e Budget dipendono da CodDip, non-chiave)
- quindi `Matricola → CodDip → NomeDip` è una **dipendenza transitiva**

> Decomposizione:

```sql
DIPARTIMENTO(CodDip PK, NomeDip, Budget)

IMPIEGATO(
  Matricola PK,
  Nome,
  CodDip_FK → DIPARTIMENTO(CodDip)
)
```

> **Definizione formale equivalente di 3NF**: per ogni FD non banale `X → A` nella relazione, deve valere almeno una di:
> 1. X è una **superchiave**, oppure
> 2. A è un attributo **primo** (fa parte di una chiave candidata)
> Questa seconda condizione è ciò che **distingue 3NF da BCNF** (vedi sotto).

---

## Forma Normale di Boyce-Codd (BCNF)

Una relazione è in **BCNF** se:

- per **ogni** dipendenza funzionale non banale `X → Y`, **X è una superchiave**

> A differenza della 3NF, la BCNF **non ammette eccezioni** per gli attributi primi: anche se Y è parte di una chiave candidata, se X non è una superchiave la dipendenza viola la BCNF.

### Esempio classico — 3NF ma non BCNF

```
ISCRIZIONE_DOCENTE(Studente, Corso, Docente)
```

Ipotesi del problema:

- uno studente può seguire più corsi
- ogni corso può essere insegnato da più docenti (in sezioni diverse)
- **ogni docente insegna un solo corso** → `Docente → Corso`

**Chiavi candidate:** `(Studente, Corso)` e `(Studente, Docente)` — entrambe identificano univocamente la riga.

Verifica `Docente → Corso`:

- `Corso` è un attributo **primo** (fa parte della chiave `(Studente, Corso)`) → la 3NF è **rispettata** (condizione 2 soddisfatta)
- `Docente` **non è una superchiave** (da solo non determina la riga) → la **BCNF è violata**

> Decomposizione BCNF:

```sql
DOCENTE_CORSO(Docente PK, Corso)

ISCRIZIONE(
  Studente_FK,
  Docente_FK → DOCENTE_CORSO(Docente),
  PRIMARY KEY (Studente_FK, Docente_FK)
)
```

> Nota: questa decomposizione **non preserva** la dipendenza `(Studente, Corso)` come vincolo direttamente verificabile in un'unica tabella — è il classico **trade-off BCNF**: si elimina ogni ridondanza, ma a volte si perde la possibilità di verificare una dipendenza con un semplice vincolo (serve un JOIN).

### Algoritmo di decomposizione BCNF (idea generale)

1. Trova una FD `X → Y` nella relazione R che **viola** la BCNF (X non superchiave)
2. Decomponi R in:
    - `R1 = X ∪ Y`
    - `R2 = R − (Y − X)` (cioè R meno gli attributi "spostati", mantenendo X)
3. Ripeti ricorsivamente su R1 e R2 finché ogni relazione è in BCNF

---

## 3NF vs BCNF — confronto

| Aspetto | 3NF | BCNF |
| --- | --- | --- |
| Condizione su X → A | X superchiave **oppure** A attributo primo | X deve **sempre** essere superchiave |
| Ridondanza residua | Possibile (se A è primo) | Eliminata completamente |
| Preservazione delle dipendenze | Sempre garantita (algoritmo di sintesi) | Non sempre garantita |
| Decomposizione lossless | Sempre garantita | Sempre garantita |
| Uso pratico | Livello standard richiesto in un progetto | Obiettivo ideale, non sempre raggiungibile senza perdere FD |

> **In pratica**: la maggior parte degli schemi ottenuti applicando correttamente le regole ER → Relazionale sono **già in BCNF**. Le violazioni emergono soprattutto quando ci sono **più chiavi candidate che si sovrappongono** (come nell'esempio Studente/Corso/Docente).

---

## Esempio completo — decomposizione passo-passo

Tabella di partenza (non normalizzata):

```
ORDINI(NumOrdine, DataOrdine, CodCliente, NomeCliente, CittaCliente,
       CodProdotto, NomeProdotto, PrezzoUnitario, Quantità)
```

**FD individuate:**

- `NumOrdine → DataOrdine, CodCliente`
- `CodCliente → NomeCliente, CittaCliente`
- `CodProdotto → NomeProdotto, PrezzoUnitario`
- `(NumOrdine, CodProdotto) → Quantità`

### → 1NF

Già rispettata: ogni cella è atomica, nessun gruppo ripetuto.

### → 2NF

PK = `(NumOrdine, CodProdotto)`.

- `DataOrdine, CodCliente, NomeCliente, CittaCliente` dipendono solo da `NumOrdine` → dipendenza parziale
- `NomeProdotto, PrezzoUnitario` dipendono solo da `CodProdotto` → dipendenza parziale

Decomposizione:

```sql
ORDINE(NumOrdine PK, DataOrdine, CodCliente, NomeCliente, CittaCliente)
PRODOTTO(CodProdotto PK, NomeProdotto, PrezzoUnitario)
RIGA_ORDINE(NumOrdine_FK, CodProdotto_FK, Quantità,
            PRIMARY KEY (NumOrdine_FK, CodProdotto_FK))
```

### → 3NF

In `ORDINE`: `NumOrdine → CodCliente → NomeCliente, CittaCliente` → dipendenza transitiva

Decomposizione:

```sql
CLIENTE(CodCliente PK, NomeCliente, CittaCliente)
ORDINE(NumOrdine PK, DataOrdine, CodCliente_FK → CLIENTE(CodCliente))
```

### → BCNF

Tutte le chiavi determinanti rimaste (`NumOrdine`, `CodCliente`, `CodProdotto`, `(NumOrdine, CodProdotto)`) sono superchiavi delle rispettive tabelle → schema finale **già in BCNF**.

**Schema finale:**

```sql
CLIENTE(CodCliente PK, NomeCliente, CittaCliente)
PRODOTTO(CodProdotto PK, NomeProdotto, PrezzoUnitario)
ORDINE(NumOrdine PK, DataOrdine, CodCliente_FK → CLIENTE(CodCliente))
RIGA_ORDINE(NumOrdine_FK, CodProdotto_FK, Quantità,
            PRIMARY KEY (NumOrdine_FK, CodProdotto_FK))
```

---

## Riepilogo — tabella delle forme normali

| Forma | Requisito aggiuntivo | Problema risolto |
| --- | --- | --- |
| **1NF** | Valori atomici, nessun gruppo ripetuto | Attributi multivalore/composti |
| **2NF** | Nessuna dipendenza parziale dalla PK | Ridondanza su parte della chiave |
| **3NF** | Nessuna dipendenza transitiva | Ridondanza tramite attributi non-chiave |
| **BCNF** | Ogni determinante è superchiave | Ridondanza residua tra chiavi candidate sovrapposte |

> Da ricordare per l'esame: **1NF → atomicità**, **2NF → dipendenza parziale (solo con PK composita)**, **3NF → dipendenza transitiva**, **BCNF → ogni X→Y richiede X superchiave, senza eccezioni**.
