# 🧩 Progettazione Concettuale

---

## 🗺️ Cos'è la progettazione concettuale?

La **progettazione di un database** si articola in tre fasi:

1. **Concettuale** — si definisce *cosa* rappresentare, indipendentemente dalla tecnologia → produce lo **Schema ER**
2. **Logica** — si traduce il modello concettuale in tabelle relazionali → produce lo schema relazionale
3. **Fisica** — si ottimizza la memorizzazione su disco (indici, partizionamento, ecc.)

> La fase concettuale è la più importante: un errore qui si propaga a tutto il sistema.
> 

---

## 🔷 Il Modello ER (Entity-Relationship)

Il modello **ER** (Entity-Relationship), proposto da *Peter Chen nel 1976*, è il linguaggio grafico standard per la progettazione concettuale. Descrive la realtà di interesse attraverso tre concetti fondamentali:

- **Entità** — gli oggetti del mondo reale
- **Attributi** — le proprietà delle entità
- **Associazioni (Relationship)** — i legami tra entità

---

## 🟦 Entità

Un'**entità** rappresenta una classe di oggetti del mondo reale con esistenza autonoma e con proprietà comuni.

> ✅ Esempi: `STUDENTE`, `CORSO`, `PROFESSORE`, `ORDINE`, `PRODOTTO`
> 

**Rappresentazione grafica:** rettangolo con il nome dell'entità al centro (nome sempre in MAIUSCOLO per convenzione).

### Istanza vs. Entità

| Concetto | Significato | Esempio |
| --- | --- | --- |
| Entità (tipo) | La classe / categoria | `STUDENTE` |
| Istanza | Un elemento specifico della classe | Lo studente "Mario Rossi, matr. 12345" |

### Come riconoscere un'entità?

Una buona entità:

- Ha **identità propria** (esiste indipendentemente da altri oggetti)
- Ha **più istanze** nel sistema
- Ha **attributi propri** significativi
- Partecipa a **relazioni** con altre e**Relationship**ntità

> ❌ Non è un'entità: qualcosa che ha solo un valore e nessuna proprietà aggiuntiva (quello è un attributo).
> 

---

## 🟡 Attributi

Gli **attributi** descrivono le proprietà di un'entità. Ogni attributo ha un nome e un **dominio** (insieme dei valori ammessi).

**Rappresentazione grafica:** ellisse collegata all'entità (o rombo per le relazioni).

### Tipi di attributo

- 🔑 Attributo chiave (identificatore)
    
    L'**attributo chiave** (o *identificatore*) identifica univocamente ogni istanza dell'entità.
    
    - Graficamente: il nome è **sottolineato**
    - Deve essere **univoco** e **non nullo** per ogni istanza
    - Esempi: `CodiceStudente`, `CodiceFiscale`, `NumeroOrdine`
    
    > Un'entità può avere più candidati come chiave; si sceglie il più stabile e significativo.
    > 
- 📦 Attributo semplice vs. composto
    
    **Semplice:** non ulteriormente divisibile — `Cognome`, `Prezzo`, `DataNascita`
    
    **Composto:** formato da sotto-attributi — es. `Indirizzo` → (`Via`, `CAP`, `Città`, `Provincia`)
    
    > Conviene usare attributo composto quando i componenti vengono usati separatamente in query.
    > 
- 🔢 Attributo monovalore vs. multivalore
    
    **Monovalore:** ogni istanza ha un solo valore — `CodiceFiscale`, `DataNascita`
    
    **Multivalore:** ogni istanza può avere più valori — `NumeroTelefono` (uno studente può averne più di uno)
    
    **Rappresentazione grafica del multivalore:** doppia ellisse
    
    > I multivalore nella fase logica diventano quasi sempre una tabella separata.
    > 
- 💡 Attributo derivato
    
    **Derivato:** calcolabile da altri attributi — es. `Età` (calcolata da `DataNascita`)
    
    **Rappresentazione grafica:** ellisse tratteggiata
    
    > Non si memorizza: si calcola al momento della query. Salvo eccezioni di performance.
    > 
- ⬜ Attributo opzionale (nullable)
    
    Può assumere valore **NULL** — cioè il dato potrebbe non essere disponibile o non applicabile.
    
    Esempio: `DataLaurea` per uno studente non ancora laureato.
    

---

## 🔗 Associazioni (Relationship)

Un'**associazione** rappresenta un legame logico tra due o più entità.

**Rappresentazione grafica:** rombo collegato alle entità partecipanti.

> ✅ Esempi: `STUDIA` (tra STUDENTE e CORSO), `INSEGNA` (tra PROFESSORE e CORSO), `LAVORA_IN` (tra IMPIEGATO e DIPARTIMENTO)
> 

### Grado di un'associazione

| Grado | Nome | Esempio |
| --- | --- | --- |
| 2 entità | Binaria (la più comune) | STUDENTE — *iscritta* — CORSO |
| 3 entità | Ternaria | MEDICO — *prescrive* — FARMACO — *a* — PAZIENTE |
| 1 entità | Ricorsiva (unaria) | IMPIEGATO — *è supervisore di* — IMPIEGATO |

### Attributi di un'associazione

Anche le associazioni possono avere attributi propri — es. la relazione `ESAME` tra STUDENTE e CORSO ha l'attributo `Voto` e `Data`.

---

## 📊 Cardinalità (molteplicità)

La **cardinalità** specifica quante istanze di un'entità possono essere associate a quante istanze dell'altra.

### Tipi di cardinalità (notazione base)

| Tipo | Notazione | Significato | Esempio |
| --- | --- | --- | --- |
| **1:1** (uno a uno) | 1 — 1 | Un'istanza A è associata a max una istanza B e viceversa | PERSONA — *ha* — PASSAPORTO |
| **1:N** (uno a molti) | 1 — N | Un'istanza A è associata a molte B, ma ogni B a una sola A | DIPARTIMENTO — *contiene* — IMPIEGATO |
| **N:M** (molti a molti) | N — M | Molte A associate a molte B | STUDENTE — *frequenta* — CORSO |

> ⚠️ Le relazioni N:M nella fase logica richiedono sempre una **tabella intermedia** (tabella di giunzione).
> 

### Notazione (min, max) — cardinalità vincolata

La notazione estesa **(min, max)** specifica quante volte **al minimo** e **al massimo** un'istanza di un'entità può partecipare a un'associazione. È più precisa della notazione base 1:N.

**Formato:** si scrive `(min, max)` su ciascun lato del rombo, accanto all'entità opposta a cui si riferisce.

**Valori speciali:**

- `0` → partecipazione **opzionale** (l'istanza può non partecipare)
- `1` → partecipazione **obbligatoria** (l'istanza deve partecipare almeno una volta)
- `N` (o `*`) → **nessun limite superiore**

**Esempi:**

| Scenario | Notazione (min,max) lato A | Notazione (min,max) lato B | Lettura |
| --- | --- | --- | --- |
| Ogni impiegato lavora in esattamente 1 dipartimento; ogni dipartimento ha da 1 a N impiegati | `(1,1)` su IMPIEGATO | `(1,N)` su DIPARTIMENTO | Obbligatorio per entrambi |
| Uno studente può essere iscritto a 0 o più corsi; ogni corso ha almeno 1 studente | `(0,N)` su STUDENTE | `(1,N)` su CORSO | Studente opzionale, corso obbligatorio |
| Ogni persona ha 0 o 1 passaporti; ogni passaporto appartiene a esattamente 1 persona | `(0,1)` su PERSONA | `(1,1)` su PASSAPORTO | 1:1 con partecipazione parziale |

> ⚠️ **Attenzione alla direzione di lettura:** il vincolo `(min, max)` si legge dal lato dell'entità, non dell'associazione. `(1,N)` sul lato DIPARTIMENTO significa: *ogni dipartimento partecipa da 1 a N volte all'associazione*, cioè ha da 1 a N impiegati.
> 

> 💡 La notazione `(0, N)` corrisponde alla partecipazione **parziale** della notazione base; `(1, N)` o `(1, 1)` alla **totale**.
> 

### Partecipazione (vincolo di esistenza)

- **Totale (obbligatoria):** ogni istanza dell'entità partecipa necessariamente — rappresentata con **doppia linea**
- **Parziale (opzionale):** alcune istanze possono non partecipare — rappresentata con **linea singola**

Esempio: ogni IMPIEGATO lavora obbligatoriamente in un DIPARTIMENTO (partecipazione totale di IMPIEGATO), ma un DIPARTIMENTO può esistere anche senza impiegati (partecipazione parziale di DIPARTIMENTO).

---

## 🏚️ Entità debole (Weak Entity)

Un'**entità debole** è un'entità che **non possiede un identificatore proprio**: la sua identità dipende da un'altra entità, chiamata **entità forte** (o owner entity).

**Caratteristiche:**

- Non ha una chiave primaria autonoma
- Dipende esistenzialmente dall'entità forte: se l'entità forte viene eliminata, le istanze dipendenti vengono eliminate di conseguenza
- Si identifica combinando la **chiave parziale** (o discriminatore) con la chiave dell'entità forte

**Rappresentazione grafica:**

- L'entità debole si rappresenta con un **doppio rettangolo**
- L'associazione che la collega all'entità forte si rappresenta con un **doppio rombo**
- La chiave parziale (discriminatore) ha il nome **sottolineato tratteggiato**

> ✅ Esempio classico: `ORDINE` (entità forte) — *contiene* — `RIGA_ORDINE` (entità debole). Una riga d'ordine è identificata dal numero di riga *più* il riferimento all'ordine a cui appartiene. Senza l'ordine, la riga non ha senso.
> 

> ✅ Altro esempio: `EDIFICIO` — *ha* — `APPARTAMENTO`. L'appartamento ha un numero interno (es. "Scala A, Piano 2, Int. 3") ma è univoco solo all'interno dello stesso edificio.
> 

**Distinzione importante:**

| Concetto | Entità forte | Entità debole |
| --- | --- | --- |
| Identificatore | Autonomo (chiave primaria propria) | Parziale (discriminatore + chiave entità forte) |
| Esistenza | Indipendente | Dipende dall'entità forte |
| Grafica | Rettangolo singolo | Doppio rettangolo |
| Relazione con owner | — | Doppio rombo |

> ⚠️ Le entità deboli nella fase logica diventano tabelle con chiave primaria **composta**: (FK verso entità forte) + discriminatore.
> 

---

## 🔄 Associazioni particolari

- ↩️ Associazione ricorsiva (unaria)
    
    Un'entità è in relazione con sé stessa.
    
    Esempio: `IMPIEGATO` — *è_supervisore_di* — `IMPIEGATO`
    
    Si usano **nomi di ruolo** sulle linee per distinguere i due lati (es. *supervisore* e *subordinato*).
    
- 🔺 Associazione ternaria
    
    Coinvolge tre entità contemporaneamente. Il rombo ha tre linee.
    
    Esempio: `MEDICO` — *prescrive* — `FARMACO` — *a* — `PAZIENTE`
    
    > Difficile da gestire nella fase logica. Spesso si scompone in relazioni binarie con un'entità intermediaria.
    > 

---

## 📐 Regole aziendali nel modello ER

Le **regole aziendali** (business rules) sono informazioni che completano lo schema ER e che non sempre trovano posto direttamente nel diagramma. Si classificano in tre tipi:

### Descrizione di un concetto

La definizione precisa di un'entità, un attributo o un'associazione rilevante per l'applicazione. Chiarisce il significato esatto del concetto nel contesto specifi;co, eliminando ambiguità.

> Esempio: `STUDENTE` — persona regolarmente iscritta al corso di laurea, con matricola assegnata dalla segreteria. Non include uditori o iscritti a singoli esami.
> 

> Esempio: `DataIscrizione` in ISCRIZIONE — data in cui lo studente ha effettuato l'iscrizione all'esame, non la data in cui lo ha sostenuto.
> 

### Vincolo di integrità

Un vincolo sui dati dell'applicazione. Può essere:

- **Espresso con i costrutti del modello ER** — ad esempio tramite cardinalità, partecipazione totale, identificatori
- **Non esprimibile direttamente** nel diagramma ER, e quindi documentato testualmente nel dizionario dei dati

> Esempio esprimibile: ogni IMPIEGATO deve appartenere a esattamente un DIPARTIMENTO → cardinalità `(1,1)` su IMPIEGATO.
> 

> Esempio non esprimibile: `DataFine >= DataInizio` per un contratto; lo stipendio non può diminuire nel tempo. Questi vanno documentati a parte e implementati con trigger o CHECK nella fase logica.
> 

### Derivazione

Un concetto che può essere ottenuto per inferenza o per calcolo aritmetico da altri concetti già presenti nello schema. Non viene memorizzato direttamente, ma calcolato al momento del bisogno.

> Esempio: `Età` — derivata da `DataNascita` e dalla data corrente.
> 

> Esempio: `TotaleOrdine` — derivato dalla somma di `Quantità × PrezzoUnitario` delle righe d'ordine associate.
> 

> Esempio: `NumeroImpiegati` di un dipartimento — derivato dal conteggio delle istanze di IMPIEGATO collegate a quel dipartimento.
> 

Nello schema ER gli attributi derivati si rappresentano con **ellisse tratteggiata**. Nella fase logica si gestiscono con una query, una vista, o un trigger che mantiene il valore aggiornato.

---

## 📎 Collegamento con altri argomenti

- Progettazione logica (trasformazione ER → Relazionale) — [🧩 Progettazione Logica — Da ER a Relazionale (Parte 2)](%F0%9F%97%84%EF%B8%8F%20Appunti%20DBMS%20&%20DB%20Distribuiti%2036b2b96c97f58164af85c7400bcc9524.md)
- DBMS & DB Distribuiti — [🗄️ Appunti: DBMS & DB Distribuiti](https://app.notion.com/p/36b2b96c97f58138b8d7d77b97823f18?pvs=21)
- SQL (DDL — creazione tabelle dallo schema logico) — appunti SQL separati