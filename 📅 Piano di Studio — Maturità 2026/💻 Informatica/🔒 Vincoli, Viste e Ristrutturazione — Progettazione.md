# 🔒 Vincoli, Viste e Ristrutturazione — Progettazione Logica Avanzata

---

## 1️⃣ Regole aziendali e vincoli di integrità

I **vincoli di integrità** sono condizioni che i dati devono rispettare in ogni istante. Si dividono in due categorie:

| Tipo | Descrizione |
| --- | --- |
| **Vincoli statici** | Condizioni sui valori in un dato istante (es. stipendio > 0) |
| **Vincoli dinamici** | Condizioni che coinvolgono la transizione tra stati (es. lo stipendio non può diminuire) |

---

### Vincoli intra-relazionali

Riguardano una singola tabella.

**NOT NULL**

```sql
Nome VARCHAR(50) NOT NULL
```

Impedisce valori nulli su un attributo.

**UNIQUE**

```sql
Email VARCHAR(100) UNIQUE
```

Garantisce che non esistano due righe con lo stesso valore. A differenza della PK, ammette NULL (ma un solo NULL per colonna in molti DBMS).

**PRIMARY KEY**

```sql
PRIMARY KEY (Matricola)
-- oppure PK composita:
PRIMARY KEY (Matricola_FK, CodCorso_FK)
```

Implica automaticamente NOT NULL + UNIQUE.

**CHECK**

```sql
Stipendio DECIMAL(10,2) CHECK (Stipendio > 0)
Voto INTEGER CHECK (Voto BETWEEN 18 AND 30)
Tipo CHAR(1) CHECK (Tipo IN ('A', 'B', 'C'))
```

Permette di esprimere qualsiasi condizione booleana sui valori della riga.

> I vincoli CHECK vengono valutati a ogni INSERT e UPDATE. Se la condizione è FALSE, l'operazione viene rifiutata.
> 

**DEFAULT**

```sql
DataIscrizione DATE DEFAULT CURRENT_DATE
Attivo BOOLEAN DEFAULT TRUE
```

Assegna un valore di default quando l'attributo non viene specificato nell'INSERT.

---

### Vincoli inter-relazionali

Riguardano più tabelle — il principale è il **vincolo di integrità referenziale** (già visto nella pagina precedente).

```sql
CREATE TABLE IMPIEGATO (
  Matricola INT PRIMARY KEY,
  Nome VARCHAR(50) NOT NULL,
  CodDip INT,
  FOREIGN KEY (CodDip) REFERENCES DIPARTIMENTO(CodDip)
    ON DELETE SET NULL
    ON UPDATE CASCADE
);
```

**Politiche disponibili:**

| Politica | ON DELETE | ON UPDATE |
| --- | --- | --- |
| `CASCADE` | Elimina le righe figlie | Propaga il nuovo valore |
| `SET NULL` | Imposta NULL nella FK | Imposta NULL nella FK |
| `RESTRICT` | Blocca se esistono figli | Blocca se esistono figli |
| `NO ACTION` | Come RESTRICT (a fine transazione) | Come RESTRICT |
| `SET DEFAULT` | Imposta il valore di default | Imposta il valore di default |

---

### Asserzioni (ASSERTION)

Le asserzioni sono **vincoli globali** che non appartengono a una singola tabella. Sono definite con `CREATE ASSERTION` e valutate a ogni modifica del DB.

```sql
CREATE ASSERTION max_impiegati_per_dip
  CHECK (
    NOT EXISTS (
      SELECT CodDip
      FROM IMPIEGATO
      GROUP BY CodDip
      HAVING COUNT(*) > 50
    )
  );
```

> Le asserzioni sono previste dallo standard SQL ma supportate da pochissimi DBMS reali. In pratica si usano i **trigger** per lo stesso scopo.
> 

---

### Trigger

Un **trigger** è una procedura che il DBMS esegue automaticamente al verificarsi di un evento (INSERT, UPDATE, DELETE).

Struttura generale:

```sql
CREATE TRIGGER nome_trigger
  {BEFORE | AFTER} {INSERT | UPDATE | DELETE}
  ON nome_tabella
  [FOR EACH ROW]
  BEGIN
    -- istruzioni SQL
  END;
```

**Esempio — vincolo dinamico (stipendio non può diminuire):**

```sql
CREATE TRIGGER check_stipendio
  BEFORE UPDATE ON IMPIEGATO
  FOR EACH ROW
  BEGIN
    IF NEW.Stipendio < OLD.Stipendio THEN
      SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Lo stipendio non può diminuire';
    END IF;
  END;
```

- `OLD` → riga prima della modifica
- `NEW` → riga dopo la modifica
- `SIGNAL` → lancia un errore e annulla l'operazione

> I trigger sono lo strumento principale per vincoli dinamici, derivazioni automatiche e log di audit.
> 

---

## 2️⃣ Dalla progettazione al modello relazionale: relazioni e viste

### Tabella base vs Vista

|  | Tabella base | Vista |
| --- | --- | --- |
| **Dati** | Fisicamente memorizzati | Non memorizzati (calcolati on-demand) |
| **Definizione** | `CREATE TABLE` | `CREATE VIEW` |
| **Aggiornabilità** | Sempre | Solo in certi casi |
| **Scopo** | Struttura del DB | Astrazione, sicurezza, semplicità |

---

### CREATE VIEW

Una vista è una **query salvata con un nome**. Ogni volta che la si interroga, la query sottostante viene rieseguita.

```sql
CREATE VIEW ImpiegatiRoma AS
  SELECT Matricola, Nome, Cognome, Stipendio
  FROM IMPIEGATO
  WHERE Citta = 'Roma';
```

Utilizzo:

```sql
SELECT * FROM ImpiegatiRoma WHERE Stipendio > 30000;
```

Il DBMS esegue internamente:

```sql
SELECT * FROM (
  SELECT Matricola, Nome, Cognome, Stipendio
  FROM IMPIEGATO
  WHERE Citta = 'Roma'
) WHERE Stipendio > 30000;
```

---

### Viste aggiornabili

Una vista è **aggiornabile** (supporta INSERT/UPDATE/DELETE) solo se:

- Fa riferimento a **una sola tabella base**
- Non contiene `DISTINCT`, `GROUP BY`, `HAVING`, funzioni aggregate
- Non contiene sottoqueries nella clausola SELECT
- Include la PK della tabella base

```sql
-- Vista aggiornabile:
CREATE VIEW ImpiegatiRoma AS
  SELECT Matricola, Nome, Cognome
  FROM IMPIEGATO
  WHERE Citta = 'Roma';

UPDATE ImpiegatiRoma SET Nome = 'Luca' WHERE Matricola = 101;  -- OK
```

```sql
-- Vista NON aggiornabile (contiene aggregazione):
CREATE VIEW StipendioMedioPerDip AS
  SELECT CodDip, AVG(Stipendio) AS StipMedio
  FROM IMPIEGATO
  GROUP BY CodDip;

UPDATE StipendioMedioPerDip SET StipMedio = 3000 ...;  -- ERRORE
```

---

### WITH CHECK OPTION

Se si aggiorna una vista con `WITH CHECK OPTION`, il DBMS verifica che le righe inserite/modificate soddisfino ancora la condizione della vista.

```sql
CREATE VIEW ImpiegatiRoma AS
  SELECT * FROM IMPIEGATO
  WHERE Citta = 'Roma'
  WITH CHECK OPTION;

-- Questo fallisce: la riga non sarebbe più visibile nella vista
UPDATE ImpiegatiRoma SET Citta = 'Milano' WHERE Matricola = 101;  -- ERRORE
```

---

### Usi principali delle viste

**1. Sicurezza e controllo degli accessi**

```sql
-- L'utente vede solo nome e reparto, non lo stipendio
CREATE VIEW ImpiegatiPubblici AS
  SELECT Matricola, Nome, Cognome, Reparto
  FROM IMPIEGATO;

GRANT SELECT ON ImpiegatiPubblici TO utente_generico;
```

**2. Semplificazione di query complesse**

```sql
CREATE VIEW IscrizioniComplete AS
  SELECT s.Nome, s.Cognome, c.NomeCorso, i.Voto
  FROM STUDENTE s
  JOIN ISCRIZIONE i ON s.Matricola = i.Matricola_FK
  JOIN CORSO c ON c.CodCorso = i.CodCorso_FK;
```

**3. Indipendenza logica** — se la struttura delle tabelle cambia, si può adattare la vista senza modificare le applicazioni che la usano.

---

## 3️⃣ Ristrutturazione dello schema concettuale

Prima di tradurre lo schema ER in relazionale, si esegue una fase di **ristrutturazione** per semplificarlo e ottimizzarlo. È un passaggio intermedio tra progettazione concettuale e logica.

---

### Analisi delle ridondanze

Una **ridondanza** nello schema ER è un'informazione derivabile da altre informazioni già presenti.

**Esempio:**

- Entità ORDINE con attributo `TotaleOrdine`
- Entità RIGA_ORDINE con attributi `Quantità` e `PrezzoUnitario`
- `TotaleOrdine = SUM(Quantità × PrezzoUnitario)` → ridondanza

**Valutazione:**

| Aspetto | Mantenere la ridondanza | Eliminare la ridondanza |
| --- | --- | --- |
| Spazio | Occupa più spazio | Spazio minore |
| Lettura | Query più veloci (dato già pronto) | Query più lente (calcolo necessario) |
| Scrittura | Aggiornamento obbligatorio a ogni modifica | Nessun overhead in scrittura |
| Consistenza | Rischio di inconsistenza | Sempre consistente |

> La scelta dipende dal carico di lavoro: se il dato viene letto spesso e aggiornato raramente, conviene mantenerlo.
> 

---

### Eliminazione delle generalizzazioni

Lo schema ER può contenere gerarchie IS-A che vanno **eliminate** prima della traduzione, applicando una delle tre strategie:

- **Strategia A** — accorpamento delle figlie nel padre (tabella unica)
- **Strategia B** — accorpamento del padre nelle figlie (tabella per sottoclasse)
- **Strategia C** — sostituzione con associazioni (tabella per classe concreta)

La scelta si fa in base a:

- Numero di attributi specializzati
- Frequenza di accesso alle sottoclassi
- Se la gerarchia è totale o parziale

---

### Partizionamento / accorpamento di entità

**Partizionamento verticale:** si divide un'entità con molti attributi in due entità separate, legate da una relazione 1:1, per motivi di performance.

```
IMPIEGATO(Matricola, Nome, Cognome, DataNascita, Email, Foto, CV, Note)
↓ partizionamento verticale
IMPIEGATO(Matricola, Nome, Cognome, Email)          ← dati acceduti spesso
IMPIEGATO_DETTAGLIO(Matricola_FK, Foto, CV, Note)   ← dati acceduti raramente
```

**Accorpamento:** si fondono due entità legate da una relazione 1:1 in un'unica entità, se vengono sempre accedute insieme.

---

### Scelta degli identificatori primari

Ogni entità deve avere un identificatore che diventerà la PK nella traduzione relazionale. I criteri di scelta:

| Criterio | Spiegazione |
| --- | --- |
| **Semplicità** | Preferire attributo singolo a chiave composita |
| **Immutabilità** | La PK non dovrebbe cambiare nel tempo |
| **Brevità** | Valori corti = JOIN più veloci |
| **Non significatività** | Meglio una chiave surrogata (ID auto-increment) che un codice con significato che potrebbe cambiare |

> Se un'entità non ha un identificatore naturale adatto, si introduce un **identificatore surrogato** (es. `ID INT AUTO_INCREMENT`).
> 

---

## 4️⃣ Regole di derivazione

Un **attributo derivato** è un valore calcolabile a partire da altri dati già presenti nel DB. Nello schema ER viene marcato con una linea tratteggiata.

**Esempi tipici:**

- `Età` derivata da `DataNascita` e dalla data corrente
- `TotaleOrdine` derivata da righe d'ordine
- `NumeroImpiegati` di un dipartimento derivata dal conteggio degli impiegati

---

### Strategie di gestione

**Strategia 1 — Non memorizzare, calcolare sempre**

```sql
SELECT Nome, TIMESTAMPDIFF(YEAR, DataNascita, CURDATE()) AS Età
FROM PERSONA;
```

- Pro: sempre consistente
- Contro: calcolo a ogni query

**Strategia 2 — Memorizzare e aggiornare con trigger**

```sql
-- Colonna memorizzata
ALTER TABLE DIPARTIMENTO ADD NumImpiegati INT DEFAULT 0;

-- Trigger che mantiene il contatore aggiornato
CREATE TRIGGER aggiorna_num_impiegati_ins
  AFTER INSERT ON IMPIEGATO
  FOR EACH ROW
  BEGIN
    UPDATE DIPARTIMENTO
    SET NumImpiegati = NumImpiegati + 1
    WHERE CodDip = NEW.CodDip;
  END;

CREATE TRIGGER aggiorna_num_impiegati_del
  AFTER DELETE ON IMPIEGATO
  FOR EACH ROW
  BEGIN
    UPDATE DIPARTIMENTO
    SET NumImpiegati = NumImpiegati - 1
    WHERE CodDip = OLD.CodDip;
  END;
```

- Pro: lettura istantanea, utile se il dato viene letto molto
- Contro: overhead in scrittura, rischio inconsistenza se un trigger fallisce

**Strategia 3 — Vista**

```sql
CREATE VIEW DipartimentoConContatore AS
  SELECT d.CodDip, d.Nome, COUNT(i.Matricola) AS NumImpiegati
  FROM DIPARTIMENTO d
  LEFT JOIN IMPIEGATO i ON d.CodDip = i.CodDip
  GROUP BY d.CodDip, d.Nome;
```

- Pro: sempre consistente, nessuna ridondanza fisica
- Contro: query più lenta (JOIN + COUNT a ogni accesso)

---

### Riepilogo — quando usare quale strategia

| Scenario | Strategia consigliata |
| --- | --- |
| Dato letto raramente, calcolo semplice | Calcolo in query (no memorizzazione) |
| Dato letto spesso, aggiornato raramente | Memorizzato + trigger |
| Dato letto spesso, aggiornato spesso | Vista (o cache applicativa) |
| Dato complesso ma accessibile da più query | Vista |

---

## 📎 Collegamento con altri argomenti

- Schema ER — [🧩 Progettazione Concettuale — Schema ER (Parte 1)](🧩%20Progettazione%20Concettuale.md)
- Trasformazione ER → Relazionale — [🔄 Progettazione Logica — Da ER a Relazionale](🔄%20Progettazione%20Logica.md)
- DBMS & DB Distribuiti — [🗄️ Appunti: DBMS & DB Distribuiti](https://app.notion.com/p/36b2b96c97f58138b8d7d77b97823f18?pvs=21)