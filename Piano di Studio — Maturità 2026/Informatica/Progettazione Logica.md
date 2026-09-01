---
subject: informatica
tags:
  - informatica
  - progettazione-database
  - schema-relazionale
  - maturita-2026
---
## Obiettivo della fase logica

Prendere lo **schema ER** prodotto nella fase concettuale e tradurlo in **tabelle relazionali** (schema relazionale), pronto per essere implementato in un DBMS relazionale (es. MySQL, PostgreSQL).

> La fase logica è indipendente dal DBMS specifico — si parla ancora di modello astratto.

---

## Regole di trasformazione ER → Relazionale

### Regola 1 — Entità → Tabella

Ogni **entità** diventa una **tabella**.

- Il nome dell'entità → nome della tabella
- Gli attributi dell'entità → colonne della tabella
- L'attributo chiave → **Primary Key (PK)**

> Esempio: `STUDENTE(CodiceStudente, Nome, Cognome, DataNascita)` dove `CodiceStudente` è PK.

---

### Regola 2 — Associazione 1:1

Due entità A e B in relazione 1:1. Strategia più comune: si aggiunge la **chiave esterna (FK)** nell'entità con partecipazione totale (o in quella con meno istanze).

**Caso partecipazione totale di B:**

```
A(PK_A, ...)
B(PK_B, ..., FK_A)  ← FK_A referenzia A
```

**Caso entrambe parziali:** si può anche creare una tabella separata per la relazione, con le due FK.

> Esempio: PERSONA(CF, Nome) e PASSAPORTO(NumPassaporto, DataScadenza, CF_Persona)

> CF_Persona è FK che referenzia PERSONA, e ha anche vincolo UNIQUE (per mantenere 1:1).

---

### Regola 3 — Associazione 1:N

L'entità sul lato **N** ("molti") acquisisce la **chiave esterna** che referenzia l'entità sul lato 1.

```
DIPARTIMENTO(CodDip, Nome, Budget)
IMPIEGATO(Matricola, Nome, Stipendio, CodDip_FK)  ← CodDip_FK referenzia DIPARTIMENTO
```

- `CodDip_FK` è **NOT NULL** se la partecipazione di IMPIEGATO è totale
- `CodDip_FK` può essere **NULL** se la partecipazione è parziale

> Regola da memorizzare: **la FK va sul lato N**.

---

### Regola 4 — Associazione N:M → Tabella di giunzione

Una relazione **N:M** non si può rappresentare direttamente con FK. Si crea una **tabella di giunzione** (o tabella ponte / tabella associativa).

```
STUDENTE(Matricola, Nome, ...)
CORSO(CodCorso, NomeCorso, ...)
ISCRIZIONE(Matricola_FK, CodCorso_FK, DataIscrizione, Voto)
             ↑              ↑
          FK→STUDENTE    FK→CORSO
```

- La **PK** della tabella di giunzione è composta dalle due FK (PK composita)
- Gli **attributi della relazione ER** (es. `Voto`, `DataIscrizione`) diventano colonne della tabella di giunzione

---

### Regola 5 — Entità debole → Tabella con PK composita

Un'**entità debole** (identificata da un discriminatore + FK verso l'entità forte) diventa una tabella con **chiave primaria composita**.

```sql
ORDINE(NumOrdine PK, DataOrdine, CodCliente_FK)

RIGA_ORDINE(
  NumOrdine_FK     → ORDINE(NumOrdine),
  NumRiga,                    ← discriminatore (chiave parziale)
  CodProdotto_FK,
  Quantità,
  PrezzoUnitario,
  PRIMARY KEY (NumOrdine_FK, NumRiga)
)
```

**Punti chiave:**

- La PK della tabella debole è **sempre composita**: (FK entità forte + discriminatore)
- La FK verso l'entità forte ha **ON DELETE CASCADE** — se l'ordine viene eliminato, le righe vengono eliminate automaticamente
- Non si usa una chiave surrogata artificiale (es. ID auto-increment) se si vuole rispecchiare fedelmente il modello ER

---

### Regola 6 — Generalizzazione/Specializzazione (IS-A) → 3 strategie

Quando nel modello ER esiste una gerarchia IS-A (entità padre con sottoclassi), ci sono **tre strategie** di traduzione:

- Strategia A — Tabella unica (table per hierarchy)

    Si crea **una sola tabella** con tutti gli attributi del padre e delle sottoclassi. Un attributo discriminatore indica il tipo.

    ```sql
    PERSONA(
      CF PK,
      Nome,
      Cognome,
      Tipo,           ← 'STUDENTE' | 'PROFESSORE'
      Matricola,      ← solo per studenti (NULL per professori)
      Stipendio,      ← solo per professori (NULL per studenti)
      Dipartimento    ← solo per professori (NULL per studenti)
    )
    ```

    **Pro:** query semplici, nessun JOIN

    **Contro:** molti NULL, viola la 3NF se ci sono attributi dipendenti dal tipo

- Strategia B — Tabella per ogni sottoclasse (table per type)

    Si crea una tabella per il padre e **una tabella per ogni sottoclasse**, contenente solo gli attributi specializzati + FK verso il padre.

    ```sql
    PERSONA(CF PK, Nome, Cognome)
    STUDENTE(CF_FK PK → PERSONA, Matricola, AnnoIscrizione)
    PROFESSORE(CF_FK PK → PERSONA, Stipendio, Dipartimento)
    ```

    **Pro:** nessun NULL, rispetta la normalizzazione

    **Contro:** query che coinvolgono attributi di padre e figlio richiedono JOIN

    > Strategia preferibile nella maggior parte dei casi reali.
    >
- Strategia C — Tabella per ogni classe concreta (table per concrete class)

    Si eliminano le tabelle delle superclassi: ogni sottoclasse ha una tabella autonoma con **tutti** gli attributi (ereditati + propri).

    ```sql
    STUDENTE(CF PK, Nome, Cognome, Matricola, AnnoIscrizione)
    PROFESSORE(CF PK, Nome, Cognome, Stipendio, Dipartimento)
    ```

    **Pro:** nessun JOIN, massima autonomia

    **Contro:** attributi del padre duplicati; se la generalizzazione è **parziale** (esistono istanze del solo padre), quelle istanze non hanno tabella

    > Non applicabile se la gerarchia è parziale.
    >

**Riepilogo strategia:**

|  | Tabella unica | Per sottoclasse | Per classe concreta |
| --- | --- | --- | --- |
| JOIN necessari | No | Sì (padre + figlio) | No |
| NULL | Molti | Nessuno | Nessuno |
| Gerarchia parziale | OK | OK | Problemi |
| Normalizzazione | Scarsa | Buona | Buona |

---

### Regola 7 — Attributo multivalore → Tabella separata

Un attributo multivalore (es. `Telefono` di STUDENTE) diventa una tabella separata.

```
STUDENTE(Matricola, Nome, ...)
TELEFONO_STUDENTE(Matricola_FK, Numero)  ← PK = (Matricola_FK, Numero)
```

---

### Regola 8 — Attributo composto → Colonne separate

Un attributo composto (es. `Indirizzo` = Via + CAP + Città) viene "appiattito" in colonne distinte.

```
INDIRIZZO_VIA VARCHAR(100),
INDIRIZZO_CAP CHAR(5),
INDIRIZZO_CITTA VARCHAR(50)
```

> Alternativa: conservarlo come unica stringa se i singoli componenti non servono separatamente.

---

### Regola 9 — Associazione ricorsiva

Una relazione unaria (entità con sé stessa) si gestisce aggiungendo una FK che punta alla stessa tabella.

**Esempio (1:N ricorsiva — gerarchia manageriale):**

```
IMPIEGATO(Matricola, Nome, Matricola_Supervisore_FK)
```

`Matricola_Supervisore_FK` → referenzia `MATRICOLA` nella stessa tabella `IMPIEGATO`. Può essere NULL (il top manager non ha supervisore).

**Esempio (N:M ricorsiva — prerequisiti tra corsi):**

```
CORSO(CodCorso, Nome)
PREREQUISITO(CodCorso_FK, CodPrerequisito_FK)
```

---

### Regola 10 — Associazione ternaria → Tabella di giunzione a 3 FK

Si crea una tabella con tre FK, una per ogni entità partecipante.

```
PRESCRIZIONE(CodMedico_FK, CodFarmaco_FK, CodPaziente_FK, Dosaggio, DataPrescrizione)
```

PK composita = (CodMedico_FK, CodFarmaco_FK, CodPaziente_FK) salvo casi particolari.

---

## Chiavi nel modello relazionale

| Concetto | Definizione |
| --- | --- |
| **Superchiave** | Insieme di attributi che identifica univocamente ogni riga |
| **Chiave candidata** | Superchiave minimale (non ha attributi ridondanti) |
| **Chiave primaria (PK)** | La chiave candidata scelta come identificatore principale |
| **Chiave esterna (FK)** | Attributo che referenzia la PK di un'altra tabella |

### Vincolo di integrità referenziale

Se una tabella ha una FK, il valore di quella FK deve:

- corrispondere a una PK esistente nella tabella referenziata, **oppure**
- essere NULL (se la FK è nullable)

I DBMS garantiscono questo vincolo tramite politiche su UPDATE e DELETE:

| Politica | Comportamento |
| --- | --- |
| `CASCADE` | Propaga la modifica/cancellazione alle righe figlie |
| `SET NULL` | Imposta NULL nella FK figlia |
| `RESTRICT` | Blocca l'operazione se esistono figli |
| `NO ACTION` | Come RESTRICT, verificato a fine transazione |

---

## Dipendenze funzionali (base per la normalizzazione)

Prima di capire le forme normali serve capire cos'è una **dipendenza funzionale**.

Una dipendenza funzionale **X → Y** significa: *dato il valore di X, il valore di Y è univocamente determinato*.

> Esempio: `Matricola → Nome` — conoscendo la matricola si conosce esattamente il nome dello studente.

> Esempio: `(CodCorso, Matricola) → Voto` — il voto dipende dalla coppia corso+studente, non da uno solo dei due.

**Dipendenza parziale:** Y dipende solo da *parte* della chiave composita (problema 2NF).

**Dipendenza transitiva:** X → Z tramite un attributo intermedio non-chiave (X → Y → Z) (problema 3NF).

---

## Normalizzazione (cenni)

Dopo la traduzione ER → Relazionale, si verifica che le tabelle rispettino le **forme normali** per evitare ridondanze e anomalie.

- 1NF — Prima Forma Normale

    Ogni cella contiene un valore **atomico** (non liste, non valori composti).

    Non ci sono gruppi ripetuti.

- 2NF — Seconda Forma Normale

    È in 1NF **e** ogni attributo non-chiave dipende dall'**intera** chiave primaria, non da una sua parte.

    Problema tipico: PK composita dove un attributo dipende solo da una parte della PK.

    > Esempio di violazione:
    >

    > `ISCRIZIONE(Matricola_FK, CodCorso_FK, NomeCorso, Voto)`
    >

    > `NomeCorso` dipende solo da `CodCorso_FK`, non dalla coppia — dipendenza parziale.
    >

    > Soluzione: spostare `NomeCorso` nella tabella `CORSO`.
    >
- 3NF — Terza Forma Normale

    È in 2NF **e** non esistono **dipendenze transitive** — ogni attributo non-chiave dipende direttamente dalla PK, non tramite un altro attributo non-chiave.

    > Esempio di violazione:
    >

    > `IMPIEGATO(Matricola PK, Nome, CodDip, NomeDip)`
    >

    > `NomeDip` dipende da `CodDip`, che non è la PK — dipendenza transitiva `Matricola → CodDip → NomeDip`.
    >

    > Soluzione: spostare `NomeDip` nella tabella `DIPARTIMENTO`.
    >

    > La 3NF è il livello standard richiesto in un progetto relazionale corretto.
    >
- BCNF — Boyce-Codd Normal Form

    Versione più forte della 3NF. Ogni dipendenza funzionale X → Y deve avere X come superchiave.

    > In pratica la BCNF è raggiunta nella maggior parte dei casi quando si applica correttamente la trasformazione ER.
    >

---

## Esempio completo — Università

### Schema ER (descrizione testuale)

- **STUDENTE** (Matricola⁻¹, Nome, Cognome, DataNascita, Email)
- **CORSO** (CodCorso⁻¹, NomeCorso, CFU, Semestre)
- **PROFESSORE** (CodiceProfessore⁻¹, Nome, Cognome, Dipartimento)
- Associazione **ISCRIZIONE** N:M tra STUDENTE e CORSO → attributi: `DataIscrizione`, `Voto`
- Associazione **INSEGNA** 1:N tra PROFESSORE e CORSO (un professore insegna molti corsi, ogni corso ha un titolare)
- Associazione **PROPEDEUTICO** ricorsiva N:M su CORSO (un corso può avere più prerequisiti)

### Schema relazionale risultante

```sql
STUDENTE(Matricola PK, Nome, Cognome, DataNascita, Email)

PROFESSORE(CodiceProfessore PK, Nome, Cognome, Dipartimento)

CORSO(
  CodCorso PK,
  NomeCorso,
  CFU,
  Semestre,
  CodiceProfessore_FK  → PROFESSORE(CodiceProfessore)  -- lato N di INSEGNA
)

ISCRIZIONE(
  Matricola_FK    → STUDENTE(Matricola),
  CodCorso_FK     → CORSO(CodCorso),
  DataIscrizione,
  Voto,
  PRIMARY KEY (Matricola_FK, CodCorso_FK)
)

PROPEDEUTICO(
  CodCorso_FK         → CORSO(CodCorso),
  CodPrerequisito_FK  → CORSO(CodCorso),
  PRIMARY KEY (CodCorso_FK, CodPrerequisito_FK)
)
```

---

## Riepilogo regole — Schema di memorizzazione rapido

| Caso ER | Risultato nello schema logico |
| --- | --- |
| Entità (forte) | Tabella con PK |
| Entità debole | Tabella con PK composita (discriminatore + FK), ON DELETE CASCADE |
| Attributo semplice | Colonna |
| Attributo composto | Colonne separate (una per componente) |
| Attributo multivalore | Tabella separata con FK |
| Attributo derivato | Non si memorizza (si calcola) |
| Relazione 1:1 | FK nell'entità a partecipazione totale (+ UNIQUE) |
| Relazione 1:N | FK nel lato N |
| Relazione N:M | Tabella di giunzione con PK composita |
| Relazione ricorsiva 1:N | FK che punta alla stessa tabella |
| Relazione ricorsiva N:M | Tabella di giunzione auto-referenziante |
| Relazione ternaria | Tabella con 3 FK |
| Generalizzazione IS-A | 3 strategie: tabella unica / per sottoclasse / per classe concreta |

---

## Collegamento con altri argomenti

- Schema ER ([[Progettazione Concettuale]]) — [Progettazione Concettuale — Schema ER (Parte 1)](Progettazione%20Concettuale.md)
- DBMS & DB Distribuiti — [Appunti: DBMS & DB Distribuiti](Appunti%20DBMS%20&%20DB%20Distribuiti.md)
- SQL DDL (CREATE TABLE, vincoli FK, PK) — [[Appunti SQL]] separati
