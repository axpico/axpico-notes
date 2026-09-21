---
subject: informatica
tags:
  - informatica
  - sql
  - database
  - maturita-2026
---
## Cosa sono le clausole

Le **clausole** sono le istruzioni che compongono una query SQL. Ogni clausola ha un ruolo specifico e insieme definiscono **quali dati recuperare**, **da dove** e **con quali condizioni**.

I comandi SQL si dividono in due categorie principali:

- **DDL** (Data Definition Language) — definisce e modifica la _struttura_ del database: `CREATE TABLE`, `ALTER TABLE`, `DROP TABLE`.
- **DML** (Data Manipulation Language) — legge e modifica i _dati_: `SELECT`, `INSERT`, `UPDATE`, `DELETE`.
- **DCL** (Data Control Language) — gestisce i _permessi_ di accesso: `GRANT`, `REVOKE`.

---

## Creare una tabella: `CREATE TABLE`

Prima di poter interrogare un database, le tabelle devono essere definite. Il comando **`CREATE TABLE`** specifica il nome della tabella, le colonne con i loro tipi di dato, e i vincoli che i dati devono rispettare.

```sql
CREATE TABLE Studenti (
    matricola   INT            NOT NULL,
    cognome     VARCHAR(50)    NOT NULL,
    nome        VARCHAR(50)    NOT NULL,
    classe      VARCHAR(10),
    eta         INT
);
```

I tipi di dato più comuni sono:

|Tipo|Descrizione|Esempio|
|---|---|---|
|`INT`|Numero intero (da -2 miliardi a +2 miliardi)|`42`, `-7`|
|`TINYINT`|Intero piccolo (0–255 senza segno, oppure -128–127)|età, flag|
|`SMALLINT`|Intero medio (-32768 a 32767)|anno scolastico|
|`BIGINT`|Intero molto grande|ID univoci su larga scala|
|`DECIMAL(p, s)`|Numero decimale esatto con `p` cifre totali e `s` decimali|`DECIMAL(5,2)` → `123.45`|
|`FLOAT` / `DOUBLE`|Numero decimale approssimato (virgola mobile)|calcoli scientifici|
|`CHAR(n)`|Testo di lunghezza **fissa** di `n` caratteri (riempie con spazi)|codici, sigla provincia|
|`VARCHAR(n)`|Testo di lunghezza **variabile** fino a `n` caratteri|nomi, descrizioni|
|`TEXT`|Testo lungo senza limite di lunghezza definito|note, contenuti|
|`DATE`|Solo data: `YYYY-MM-DD`|`2024-09-15`|
|`TIME`|Solo ora: `HH:MM:SS`|`08:30:00`|
|`DATETIME`|Data e ora combinate: `YYYY-MM-DD HH:MM:SS`|timestamp di un evento|
|`TIMESTAMP`|Come `DATETIME`, ma si aggiorna automaticamente|ultima modifica|
|`BOOLEAN`|Valore vero/falso (in MySQL: `TINYINT(1)`, 0 = falso, 1 = vero)|`TRUE`, `FALSE`|
|`ENUM('a','b',…)`|Valore scelto da un insieme fisso di opzioni|`ENUM('M','F')`|
|`BLOB`|Dati binari grezzi (immagini, file)|file allegati|

> **`CHAR` vs `VARCHAR`**: `CHAR(10)` occupa sempre 10 byte; `VARCHAR(10)` occupa solo quanto serve. Usa `CHAR` per valori di lunghezza sempre uguale (es. codice fiscale), `VARCHAR` per tutto il resto. `DECIMAL` è preferibile a `FLOAT`/`DOUBLE` per valori monetari, perché non introduce errori di arrotondamento.

---

## Vincoli: `PRIMARY KEY`, `NOT NULL`, `FOREIGN KEY`, `CHECK`, `CONSTRAINT`

I **vincoli** (constraints) sono regole che il database impone automaticamente su ogni operazione di inserimento o modifica. Se un'operazione viola un vincolo, il database la rifiuta con un errore.

### `NOT NULL`

Impedisce che una colonna contenga valori `NULL`. Va usato su ogni colonna che deve avere sempre un valore.

```sql
cognome VARCHAR(50) NOT NULL
```

### `PRIMARY KEY`

Identifica in modo univoco ogni riga della tabella. Implica automaticamente `NOT NULL` e `UNIQUE`: non possono esistere due righe con lo stesso valore nella chiave primaria.

```sql
CREATE TABLE Studenti (
    matricola INT PRIMARY KEY,
    cognome   VARCHAR(50) NOT NULL
);
```

La chiave primaria può essere composta da più colonne (chiave composta), nel qual caso va definita come vincolo di tabella:

```sql
CREATE TABLE Interrogazioni (
    matricola INT,
    data      DATE,
    PRIMARY KEY (matricola, data)
);
```

### `FOREIGN KEY`

Stabilisce una relazione tra due tabelle: una colonna nella tabella corrente deve fare riferimento a valori esistenti nella chiave primaria di un'altra tabella. Garantisce l'**integrità referenziale**: non si può inserire un valore nella chiave esterna se non esiste già nella tabella referenziata.

```sql
CREATE TABLE Interrogazioni (
    matricola   INT,
    data        DATE,
    voto        INT,
    PRIMARY KEY (matricola, data),
    FOREIGN KEY (matricola) REFERENCES Studenti(matricola)
);
```

- La colonna `matricola` in `Interrogazioni` è una chiave esterna (FK) che punta alla chiave primaria `matricola` di `Studenti`.
- Non è possibile inserire un'interrogazione per uno studente che non esiste nella tabella `Studenti`.
- Se si tenta di eliminare uno studente che ha interrogazioni collegate, il database blocca l'operazione (comportamento di default).

È possibile specificare il comportamento da adottare quando il record referenziato viene eliminato o modificato, usando `ON DELETE` e `ON UPDATE`:

|Opzione|Comportamento|
|---|---|
|`RESTRICT` (default)|Blocca l'operazione se esistono righe collegate|
|`CASCADE`|Elimina/aggiorna automaticamente anche le righe collegate|
|`SET NULL`|Imposta la chiave esterna a `NULL` nelle righe collegate|
|`SET DEFAULT`|Imposta la chiave esterna al suo valore di default|

```sql
FOREIGN KEY (matricola) REFERENCES Studenti(matricola)
    ON DELETE CASCADE
    ON UPDATE CASCADE
```

Con `ON DELETE CASCADE`, eliminare uno studente eliminerà automaticamente anche tutte le sue interrogazioni.

### `CHECK`

Impone che i valori di una colonna soddisfino sempre una condizione logica. Accetta qualsiasi espressione valida nel `WHERE`, inclusi `AND`, `OR`, `LIKE` e confronti tra colonne.

```sql
CREATE TABLE Studenti (
    matricola   INT            PRIMARY KEY,
    cognome     VARCHAR(50)    NOT NULL,
    voto        INT            CHECK (voto >= 0 AND voto <= 10),
    eta         INT            CHECK (eta >= 14),
    classe      VARCHAR(10)    CHECK (classe LIKE '_BI' OR classe LIKE '_AI')
);
```

Un `CHECK` su più colonne si scrive come vincolo di tabella, fuori dalla definizione della singola colonna:

```sql
CREATE TABLE Interrogazioni (
    matricola   INT,
    data        DATE,
    voto        INT,
    recupero    BOOLEAN,
    CHECK (recupero = FALSE OR voto >= 6)
);
```

Questo vincolo impone che un'interrogazione segnata come recupero abbia necessariamente voto sufficiente.

> I valori `NULL` superano sempre il `CHECK`: se la colonna è `NULL`, la condizione non viene valutata e l'inserimento viene accettato. Per bloccare anche i `NULL` si aggiunge `NOT NULL` separatamente.

### `CONSTRAINT`

`CONSTRAINT` permette di assegnare un **nome esplicito** a un vincolo. È utile per identificare quale vincolo viene violato quando il database restituisce un errore, e per poterlo modificare o eliminare in seguito.

```sql
CREATE TABLE Studenti (
    matricola   INT,
    cognome     VARCHAR(50)     NOT NULL,
    voto        INT,
    eta         INT,
    CONSTRAINT pk_studenti      PRIMARY KEY (matricola),
    CONSTRAINT ck_voto          CHECK (voto BETWEEN 0 AND 10),
    CONSTRAINT ck_eta           CHECK (eta >= 14)
);
```

Senza `CONSTRAINT`, il database assegna nomi automatici ai vincoli, che sono spesso poco leggibili.

---

## Modificare una tabella: `ALTER TABLE`

Il comando **`ALTER TABLE`** modifica la struttura di una tabella già esistente, senza toccare i dati presenti. Permette di aggiungere o rimuovere colonne, cambiare tipi di dato e aggiungere o eliminare vincoli.

### Aggiungere una colonna

```sql
ALTER TABLE Studenti
ADD COLUMN email VARCHAR(100);
```

La nuova colonna viene aggiunta a tutte le righe esistenti con valore `NULL` (a meno che non si specifichi un `DEFAULT`).

### Rimuovere una colonna

```sql
ALTER TABLE Studenti
DROP COLUMN email;
```

> ⚠️ Eliminare una colonna è un'operazione irreversibile: i dati contenuti in quella colonna vengono persi definitivamente. Inoltre, se altri oggetti (viste, indici, o chiavi esterne di altre tabelle) dipendono da quella colonna, il database potrebbe bloccare l'operazione.

### Modificare il tipo di una colonna

```sql
ALTER TABLE Studenti
MODIFY COLUMN eta SMALLINT;
```

> La sintassi varia tra DBMS: MySQL usa `MODIFY COLUMN`, PostgreSQL e SQL Server usano `ALTER COLUMN`.

### Aggiungere un vincolo

```sql
ALTER TABLE Interrogazioni
ADD CONSTRAINT fk_matricola
    FOREIGN KEY (matricola) REFERENCES Studenti(matricola);
```

```sql
ALTER TABLE Studenti
ADD CONSTRAINT ck_voto CHECK (voto BETWEEN 0 AND 10);
```

### Rimuovere un vincolo

```sql
ALTER TABLE Studenti
DROP CONSTRAINT ck_voto;
```

Per rimuovere un vincolo è necessario conoscerne il nome — motivo per cui è buona pratica assegnare nomi espliciti con `CONSTRAINT` al momento della creazione.

---

## Viste (`VIEW`)

Una **vista** è una query salvata nel database con un nome, che si comporta come una tabella virtuale. Non contiene dati propri: ogni volta che viene interrogata, esegue la query sottostante e restituisce il risultato aggiornato.

```sql
CREATE VIEW nome_vista AS
SELECT ...
FROM ...
WHERE ...;
```

Una volta creata, la vista si usa esattamente come una tabella:

```sql
SELECT * FROM nome_vista;
```

### Esempio

Vista che mostra i concerti con il nome dell'orchestra e della sala:

```sql
CREATE VIEW concerti_dettaglio AS
SELECT c.CodC, c.Data, o.NomeO, s.NomeS, s.Citta, c.PrezzoBiglietto
FROM CONCERTI c
    INNER JOIN ORCHESTRA o ON c.CodO = o.CodO
    INNER JOIN SALE s ON c.CodS = s.CodS;
```

Interrogazione della vista:

```sql
SELECT * FROM concerti_dettaglio WHERE Citta = 'Milano';
```

Il database esegue la join completa ogni volta, restituendo solo i concerti a Milano.

### Vantaggi

- **Semplificazione**: nasconde query complesse dietro un nome semplice.
- **Sicurezza**: si può dare accesso a una vista senza dare accesso alle tabelle sottostanti.
- **Consistenza**: la logica della query è definita in un solo posto.

### Eliminare una vista

```sql
DROP VIEW concerti_dettaglio;
```

> Le viste di solito non sono aggiornabili (non si può fare `INSERT` o `UPDATE` su di esse) se coinvolgono join, aggregazioni o `DISTINCT`. In quei casi sono da considerare in sola lettura.

---

## Permessi: `GRANT`, `REVOKE` e ruoli

I database implementano un sistema di **controllo degli accessi** (DCL — Data Control Language): ogni utente può eseguire solo le operazioni per cui ha ricevuto un permesso esplicito. I permessi si gestiscono con `GRANT` (concedere) e `REVOKE` (revocare).

### `GRANT`

Concede uno o più privilegi a un utente o a un ruolo su un oggetto del database (tabella, vista, procedura…).

```sql
GRANT privilegio [, privilegio ...]
ON oggetto
TO utente [WITH GRANT OPTION];
```

I privilegi più comuni sono:

|Privilegio|Permette di|
|---|---|
|`SELECT`|Leggere i dati|
|`INSERT`|Inserire nuove righe|
|`UPDATE`|Modificare righe esistenti|
|`UPDATE (col)`|Modificare solo una colonna specifica|
|`DELETE`|Eliminare righe|
|`EXECUTE`|Eseguire una procedura o funzione|
|`ALL PRIVILEGES`|Tutti i privilegi sopra elencati|

```sql
-- Permette a mario di leggere la tabella CONCERTI
GRANT SELECT ON CONCERTI TO mario;

-- Permette a laura di inserire e leggere su MUSICISTA
GRANT SELECT, INSERT ON MUSICISTA TO laura;

-- Permette a cassiere di modificare solo il prezzo del biglietto
GRANT UPDATE (PrezzoBiglietto) ON CONCERTI TO cassiere;

-- Permette a admin di fare tutto sulla tabella ORCHESTRA
GRANT ALL PRIVILEGES ON ORCHESTRA TO admin;
```

### `WITH GRANT OPTION`

Aggiungendo `WITH GRANT OPTION`, l'utente che riceve il privilegio può a sua volta concederlo ad altri:

```sql
GRANT SELECT ON CONCERTI TO mario WITH GRANT OPTION;
```

`mario` può ora concedere lo stesso permesso ad altri utenti. Usarla con cautela: la catena di permessi può diventare difficile da tracciare.

### `REVOKE`

Rimuove uno o più privilegi precedentemente concessi.

```sql
REVOKE privilegio [, privilegio ...]
ON oggetto
FROM utente;
```

```sql
-- Revoca il permesso di INSERT a laura su MUSICISTA
REVOKE INSERT ON MUSICISTA FROM laura;

-- Revoca tutti i permessi a admin su ORCHESTRA
REVOKE ALL PRIVILEGES ON ORCHESTRA FROM admin;
```

> ⚠️ Se `mario` aveva ricevuto il permesso `WITH GRANT OPTION` e lo aveva già trasferito ad altri, revocare il permesso a `mario` **non** revoca automaticamente i permessi che lui aveva concesso. Bisogna revocarli separatamente oppure usare `REVOKE ... CASCADE` (dove supportato).

### Permessi sulle viste

È pratica comune usare le viste per limitare l'accesso ai dati: si concede il permesso di `SELECT` solo sulla vista, non sulla tabella sottostante.

```sql
-- Crea una vista che mostra solo i concerti a Milano
CREATE VIEW concerti_milano AS
SELECT * FROM CONCERTI
WHERE CodS IN (SELECT CodS FROM SALE WHERE Citta = 'Milano');

-- Concede accesso alla vista ma non alla tabella
GRANT SELECT ON concerti_milano TO cassiere;
REVOKE SELECT ON CONCERTI FROM cassiere;
```

`cassiere` può interrogare `concerti_milano` ma non accedere direttamente alla tabella `CONCERTI`.

### Ruoli

Invece di assegnare permessi utente per utente, si possono creare **ruoli** — insiemi di privilegi con un nome — e poi assegnare il ruolo a più utenti.

```sql
-- Crea il ruolo
CREATE ROLE cassiere;

-- Assegna privilegi al ruolo
GRANT SELECT, INSERT ON CONCERTI TO cassiere;
GRANT SELECT ON SALE TO cassiere;

-- Assegna il ruolo a uno o più utenti
GRANT cassiere TO mario;
GRANT cassiere TO laura;
```

Se si vuole aggiungere un privilegio a tutti i cassieri, basta aggiornare il ruolo — tutti gli utenti con quel ruolo lo ricevono automaticamente:

```sql
GRANT UPDATE (PrezzoBiglietto) ON CONCERTI TO cassiere;
```

Per rimuovere un ruolo da un utente:

```sql
REVOKE cassiere FROM mario;
```

> Non esiste un comando `MODIFY` per i permessi in SQL standard. La modifica si fa sempre con `REVOKE` seguito da un nuovo `GRANT` con i permessi aggiornati.

## Inserire dati: `INSERT INTO`

Il comando **`INSERT INTO`** aggiunge una o più righe in una tabella esistente.

```sql
INSERT INTO Studenti (matricola, cognome, nome, classe, eta)
VALUES (1, 'Rossi', 'Mario', '5BI', 17);
```

- Le colonne e i valori devono corrispondere per ordine e tipo.
- Le colonne `NOT NULL` senza valore di default devono essere sempre specificate.
- Le colonne omesse ricevono `NULL` (se consentito) o il loro valore di default.

È possibile inserire più righe in un solo comando:

```sql
INSERT INTO Studenti (matricola, cognome, nome, classe, eta)
VALUES
    (1, 'Rossi',   'Mario',  '5BI', 17),
    (2, 'Bianchi', 'Laura',  '5AI', 18),
    (3, 'Verdi',   'Giulia', '5BI', 17);
```

> Se si omette l'elenco delle colonne, i valori devono essere forniti per **tutte** le colonne nell'ordine in cui sono definite nella tabella — pratica sconsigliata perché fragile a modifiche future dello schema.

---

## SELECT e FROM

`SELECT` e `FROM` sono le due clausole obbligatorie in ogni query.

- **`FROM`** indica la tabella da cui leggere i dati.
- **`SELECT`** indica quali colonne (attributi) restituire nel risultato.

L'ordine di **esecuzione** (come il database elabora la query) è diverso dall'ordine di **scrittura**:

|Ordine di scrittura|Ordine di esecuzione|
|---|---|
|1. SELECT|1. FROM|
|2. FROM|2. SELECT|

Il database prima individua la tabella, poi seleziona le colonne.

### Selezione di tutte le colonne (`*`)

Il simbolo `*` è un carattere jolly che significa "tutte le colonne":

```sql
SELECT *
FROM studenti;
```

Restituisce tutte le colonne di ogni riga della tabella `studenti`.

---

### Proiezione

In algebra relazionale, la **proiezione** è l'operazione che seleziona solo alcune colonne di una tabella, scartando le altre.

```sql
SELECT cognome
FROM studenti;
```

Restituisce solo la colonna `cognome` per ogni riga della tabella `studenti`.

---

---

## Alias (`AS`)

La parola chiave `AS` permette di assegnare un **nome temporaneo** (alias) a una colonna o a una tabella, valido solo per quella query.

```sql
SELECT cognome AS cognome_studente
FROM studenti AS s;
```

- La colonna `cognome` verrà visualizzata nel risultato con il nome `cognome_studente`.
- La tabella `studenti` viene referenziata nella query con l'alias `s` (utile soprattutto quando si lavora con più tabelle).

> L'alias **non modifica** la struttura del database: è solo un'etichetta visiva nel risultato della query.

---

## Filtro con `WHERE`

La clausola **`WHERE`** permette di filtrare le righe restituite, mantenendo solo quelle che soddisfano una condizione.

```sql
SELECT *
FROM studenti
WHERE voto > 3 AND citta LIKE 'castellanza';
```

- **`voto > 3`** → seleziona solo le righe in cui il valore della colonna `voto` è maggiore di 3.
- **`citta LIKE 'castellanza'`** → seleziona solo le righe in cui la colonna `citta` corrisponde al pattern specificato (vedi sotto).
- **`AND`** → entrambe le condizioni devono essere vere contemporaneamente.

### L'operatore `LIKE` e i caratteri jolly

`LIKE` confronta una colonna testuale con un pattern. Supporta due caratteri jolly:

|Jolly|Significato|Esempio|
|---|---|---|
|`%`|Zero o più caratteri qualsiasi|`'Ca%'` trova "Ca", "Cala", "Castellanza"|
|`_`|Esattamente un carattere qualsiasi|`'_oma'` trova "Roma", "Coma" ma non "Paloma"|

Senza jolly, `LIKE` si comporta come '=': `LIKE 'Milano'` trova solo "Milano".

### Valutazione delle righe

La clausola `WHERE` lavora **una tupla (riga) alla volta**:

- per ogni riga della tabella, il database valuta la condizione
- se la condizione è **vera**, la riga viene inserita nella tabella risultato
- se la condizione è **falsa**, la riga viene scartata

---

### WHERE composto (`AND`, `OR`, `NOT`, `XOR`)

È possibile combinare più condizioni usando operatori logici:

- **`AND`** → tutte le condizioni devono essere vere
- **`OR`** → almeno una condizione deve essere vera
- **`NOT`** → nega una condizione
- **`XOR`** → esattamente una condizione deve essere vera (non entrambe)

```sql
SELECT *
FROM studenti
WHERE (voto >= 6 AND citta = 'Milano')
   OR NOT (eta < 18);
```

Esempio con `XOR`:

```sql
SELECT *
FROM studenti
WHERE corso = 'Informatica' XOR corso = 'Matematica';
```

> È possibile usare le parentesi `()` per controllare la precedenza delle condizioni.

---

### Ordine di esecuzione con WHERE

|Passo|Clausola|Operazione|
|---|---|---|
|1|`FROM`|Accede alla tabella|
|2|`WHERE`|Filtra le righe|
|3|`SELECT`|Restituisce le colonne|

`WHERE` viene sempre eseguita **prima** di `SELECT`: il database filtra prima le righe, poi decide quali colonne mostrare.

---

## Eliminazione dei duplicati con `DISTINCT`

La parola chiave **`DISTINCT`**, inserita subito dopo `SELECT`, elimina le righe duplicate dal risultato: vengono restituite solo le combinazioni di valori **uniche**.

```sql
SELECT DISTINCT genere, autore
FROM libri;
```

- **`DISTINCT`** → elimina le righe in cui la combinazione `(genere, autore)` appare più di una volta.
- Se lo stesso autore ha scritto più libri dello stesso genere, quella coppia verrà mostrata **una volta sola**.
- `DISTINCT` agisce sull'intera combinazione delle colonne selezionate, non sulla singola colonna.

### Esempio

Supponiamo che la tabella `libri` contenga:

|titolo|genere|autore|
|---|---|---|
|Il nome della rosa|Thriller|Umberto Eco|
|Il pendolo di Foucault|Thriller|Umberto Eco|
|Baudolino|Storico|Umberto Eco|
|Shining|Horror|Stephen King|

La query `SELECT DISTINCT genere, autore FROM libri` restituisce:

|genere|autore|
|---|---|
|Thriller|Umberto Eco|
|Storico|Umberto Eco|
|Horror|Stephen King|

La coppia `(Thriller, Umberto Eco)` appare una sola volta, anche se nella tabella originale era presente due volte.

> `DISTINCT` è utile quando si vuole ottenere un **elenco di valori unici**, ad esempio tutti i generi presenti in un catalogo o tutti gli autori che hanno pubblicato almeno un libro.

---

## Ordinamento con `ORDER BY`

La clausola **`ORDER BY`** permette di ordinare le righe del risultato in base a una o più colonne.

- **`ASC`** (default) → ordine crescente (A→Z, 0→9)
- **`DESC`** → ordine decrescente (Z→A, 9→0)

Quando si specificano più colonne, l'ordinamento avviene in cascata: prima per la prima colonna, poi — a parità di valore — per la seconda.

### Esempio

> Visualizzare cognome e città di provenienza degli studenti con voto maggiore o uguale a 6, ordinati per città di provenienza (decrescente) e poi per data di nascita (crescente).

```sql
SELECT cognome, citta
FROM studenti
WHERE voto >= 6
ORDER BY citta DESC, data_nascita;
```

- **`WHERE voto >= 6`** → mantiene solo gli studenti con voto maggiore o uguale a 6.
- **`ORDER BY citta DESC`** → ordina i risultati per città in ordine alfabetico inverso (Z→A).
- **`, data_nascita`** → a parità di città, ordina per data di nascita in ordine crescente (dal più vecchio al più giovane).

### Ordine di esecuzione con ORDER BY

|Passo|Clausola|Operazione|
|---|---|---|
|1|`FROM`|Accede alla tabella `studenti`|
|2|`WHERE`|Filtra le righe in base alle condizioni|
|3|`ORDER BY`|Ordina le righe risultanti|
|4|`SELECT`|Restituisce le colonne specificate|

> `ORDER BY` viene eseguita **dopo** il filtraggio ma **prima** della restituzione finale del risultato.

---

## JOIN

La clausola **`JOIN`** permette di combinare i dati provenienti da **due o più tabelle** in base a una relazione tra di esse.

### Come funziona: il Cross Join

Il punto di partenza è il **Cross Join** (prodotto cartesiano): ogni riga della prima tabella viene combinata con ogni riga della seconda, producendo tutte le combinazioni possibili.

Esempio: tabella `auto` (3 righe) e tabella `proprietario` (2 righe):

| id_auto | modello | | id_prop | nome | |---------|---------| |---------|------| | a1 | Golf | | p1 | Mario | | a2 | Panda | | p2 | Laura | | a3 | Punto |

Il prodotto cartesiano genera 3 × 2 = **6 righe** (ogni auto abbinata a ogni proprietario):

|id_auto|modello|id_prop|nome|
|---|---|---|---|
|a1|Golf|p1|Mario|
|a1|Golf|p2|Laura|
|a2|Panda|p1|Mario|
|a2|Panda|p2|Laura|
|a3|Punto|p1|Mario|
|a3|Punto|p2|Laura|

La maggior parte di queste combinazioni non ha senso semantico: la Golf non appartiene necessariamente a Laura, né la Punto a Mario.

### INNER JOIN: filtrare solo le righe significative

Per ottenere solo le combinazioni **significative**, si usa la condizione di join: si mantengono solo le righe in cui la **chiave esterna** (FK) della tabella `auto` corrisponde alla **chiave primaria** (PK) della tabella `proprietario`.

```sql
FROM auto INNER JOIN
    proprietario ON auto.fk = proprietario.pk
```

- **`INNER JOIN`** → restituisce solo le righe in cui esiste una corrispondenza tra le due tabelle.
- **`ON auto.fk = proprietario.pk`** → è la condizione di join: la chiave esterna di `auto` deve essere uguale alla chiave primaria di `proprietario`.
- Le righe di `auto` che non hanno un proprietario associato (come `a3` nell'esempio) vengono **escluse** dal risultato.

> La chiave esterna (FK) è un attributo nella tabella `auto` che fa riferimento alla chiave primaria (PK) della tabella `proprietario`, stabilendo così la relazione tra le due entità.

---

### 1. Cross Join

Il **Cross Join** produce il **prodotto cartesiano** tra due tabelle: ogni riga della prima tabella viene abbinata con ogni riga della seconda, senza alcuna condizione di collegamento.

```sql
SELECT *
FROM auto CROSS JOIN proprietario;
```

Se `auto` ha **3 righe** e `proprietario` ha **2 righe**, il risultato avrà **3 × 2 = 6 righe**.

Non si usa quasi mai da solo in pratica, perché produce molte combinazioni prive di significato. È però il punto di partenza teorico su cui si basano tutti gli altri tipi di join.

---

### 2. Inner Join

L'**Inner Join** è un Cross Join a cui viene applicata una **condizione di filtro** (`ON`): vengono restituite solo le righe in cui la chiave esterna di una tabella corrisponde alla chiave primaria dell'altra.

```sql
SELECT *
FROM auto INNER JOIN proprietario
    ON auto.fk_proprietario = proprietario.pk;
```

Le righe che **non trovano corrispondenza** in nessuna delle due tabelle vengono **escluse** dal risultato.

|auto|proprietario|Inclusa nel risultato?|
|---|---|---|
|a1|p1|sì (fk = pk)|
|a2|p2|sì (fk = pk)|
|a3||no (nessun proprietario associato)|

> `INNER JOIN` è il tipo di join più usato. Restituisce solo i dati che hanno una relazione valida in entrambe le tabelle.

---

### 3. Natural Join

Il **Natural Join** è una variante dell'Inner Join che **non richiede la clausola `ON`**: il database individua automaticamente le colonne con lo **stesso nome** nelle due tabelle e le usa come condizione di join.

```sql
SELECT *
FROM auto NATURAL JOIN proprietario;
```

Se entrambe le tabelle hanno una colonna chiamata `id_proprietario`, il Natural Join la usa automaticamente come condizione di collegamento, equivalendo a:

```sql
FROM auto INNER JOIN proprietario
    ON auto.id_proprietario = proprietario.id_proprietario;
```

Nel risultato, la colonna comune appare **una sola volta** (non duplicata).

> ⚠️ Il Natural Join è comodo ma **rischioso**: se le due tabelle condividono per caso colonne con lo stesso nome ma significati diversi, il join produce risultati errati senza dare errori. Per questo motivo si preferisce sempre usare `INNER JOIN` con la condizione `ON` esplicita.

---

### 4. Left Join

Il **Left Join** restituisce tutte le righe della tabella di **sinistra** (la prima), più le righe corrispondenti della tabella di destra. Se una riga della tabella sinistra non ha corrispondenza nella tabella destra, le colonne della tabella destra vengono riempite con `NULL`.

```sql
SELECT s.cognome, i.voto
FROM Studenti s LEFT JOIN Interrogazioni i
    ON s.matricola = i.matricola;
```

- Gli studenti **senza interrogazioni** appaiono comunque nel risultato, con `voto = NULL`.
- Gli studenti **con interrogazioni** appaiono normalmente con i loro voti.

È utile quando si vuole ottenere **tutti** i record della tabella principale, anche quelli che non hanno dati correlati nell'altra tabella.

---

### 5. Right Join

Il **Right Join** è il simmetrico del Left Join: restituisce tutte le righe della tabella di **destra** (la seconda), più le righe corrispondenti della tabella sinistra. Le colonne della tabella sinistra sono `NULL` dove non c'è corrispondenza.

```sql
SELECT s.cognome, i.voto
FROM Studenti s RIGHT JOIN Interrogazioni i
    ON s.matricola = i.matricola;
```

- Vengono incluse tutte le interrogazioni, anche quelle che non hanno uno studente associato nella tabella `Studenti` (situazione anomala, ma possibile se i vincoli non sono applicati).

> In pratica il `RIGHT JOIN` è raramente necessario: qualsiasi `RIGHT JOIN` può essere riscritto come `LEFT JOIN` invertendo l'ordine delle tabelle. La maggior parte degli sviluppatori usa sempre `LEFT JOIN` per convenzione.

---

### 6. Full Outer Join

Il **Full Outer Join** combina `LEFT JOIN` e `RIGHT JOIN`: restituisce **tutte le righe di entrambe le tabelle**, con `NULL` dove non c'è corrispondenza da nessuna delle due parti.

```sql
SELECT s.cognome, i.voto
FROM Studenti s FULL OUTER JOIN Interrogazioni i
    ON s.matricola = i.matricola;
```

- Studenti senza interrogazioni → `voto = NULL`
- Interrogazioni senza studente associato → `cognome = NULL`
- Tutte le corrispondenze valide → dati completi

> ⚠️ **MySQL non supporta `FULL OUTER JOIN`** nativamente. Si può simulare combinando un `LEFT JOIN` e un `RIGHT JOIN` con `UNION`:
> 
> ```sql
> SELECT s.cognome, i.voto FROM Studenti s LEFT JOIN Interrogazioni i ON s.matricola = i.matricola
> UNION
> SELECT s.cognome, i.voto FROM Studenti s RIGHT JOIN Interrogazioni i ON s.matricola = i.matricola;
> ```

---

### Riepilogo

|Tipo|Righe restituite|
|---|---|
|**Cross Join**|Tutte le combinazioni possibili (prodotto cartesiano)|
|**Inner Join**|Solo le righe con corrispondenza in **entrambe** le tabelle|
|**Left Join**|Tutte le righe della tabella **sinistra** + corrispondenze della destra (`NULL` se assenti)|
|**Right Join**|Tutte le righe della tabella **destra** + corrispondenze della sinistra (`NULL` se assenti)|
|**Full Outer Join**|Tutte le righe di **entrambe** le tabelle (`NULL` dove manca corrispondenza)|
|**Natural Join**|Come Inner Join, ma la condizione è automatica (colonne con stesso nome)|

---

## Funzioni di aggregazione

Le **funzioni di aggregazione** operano su un insieme di righe (un'intera colonna o un gruppo di righe) e restituiscono **un solo valore** come risultato, riassumendo i dati.

### `COUNT`

Conta il numero di righe restituite dalla query. Il simbolo `*` indica che vengono conteggiate tutte le tuple, incluse quelle con valori `NULL`.

```sql
SELECT COUNT(*) AS n_studenti
FROM studenti;
```

- **`COUNT(*)`** → conta tutte le righe della tabella, indipendentemente dai valori presenti.
- **`AS n_studenti`** → assegna un alias al risultato per renderlo più leggibile.

> Se si passa il nome di una colonna invece di `*` (es. `COUNT(voto)`), vengono conteggiate solo le righe in cui quella colonna **non è NULL**.

---

### Altre funzioni di aggregazione

|Funzione|Descrizione|
|---|---|
|`AVG(colonna)`|Calcola la **media** dei valori della colonna|
|`SUM(colonna)`|Calcola la **somma** dei valori della colonna|
|`MIN(colonna)`|Restituisce il **valore minimo** della colonna|
|`MAX(colonna)`|Restituisce il **valore massimo** della colonna|

### Esempio

```sql
SELECT AVG(voto)  AS media_voti,
       SUM(voto)  AS somma_voti,
       MIN(voto)  AS voto_minimo,
       MAX(voto)  AS voto_massimo
FROM studenti;
```

> Le funzioni di aggregazione **ignorano i valori `NULL`** (tranne `COUNT(*)`): ad esempio, `AVG` calcola la media solo sulle righe in cui il valore è presente.

---

### ⚠️ Mescolare aggregazioni e colonne normali

Mettere nella stessa `SELECT` una funzione di aggregazione e una colonna normale è **problematico**:

```sql
SELECT MAX(voto), cognome
FROM studenti;
```

Il comportamento dipende dal DBMS:

- **La maggior parte dei DBMS** (PostgreSQL, Oracle, SQL Server…) → restituisce un **errore**, perché `MAX(voto)` produce un unico valore mentre `cognome` ne avrebbe molti.
- **MySQL** (in modalità permissiva) → non dà errore, ma il risultato è **inaffidabile**: mostra correttamente il voto massimo, ma il `cognome` restituito è semplicemente il **primo valore trovato nella colonna**, non necessariamente il cognome dello studente con quel voto.

---

## Raggruppamento con `GROUP BY`

La clausola **`GROUP BY`** raggruppa le righe che hanno lo stesso valore in una o più colonne, in modo da applicare funzioni di aggregazione su ciascun gruppo separatamente.

```sql
SELECT voto, COUNT(*) AS numero_studenti
FROM studenti
GROUP BY voto;
```

- La tabella **non cambia struttura**, ma viene riorganizzata internamente in gruppi.
- Nel risultato finale viene prodotta **una sola tupla per gruppo**.
- È possibile raggruppare per **più colonne**: si generano tanti gruppi quante sono le combinazioni distinte dei valori di quelle colonne.
- Nel `SELECT` si possono inserire **solo** gli attributi presenti nel `GROUP BY` oppure funzioni di aggregazione.

### Ordine di esecuzione con GROUP BY

|Passo|Clausola|Operazione|
|---|---|---|
|1|`FROM`|Accede alla tabella|
|2|`WHERE`|Filtra le singole righe (prima del raggruppamento)|
|3|`GROUP BY`|Raggruppa le righe per i valori della colonna specificata|
|4|`SELECT`|Restituisce una riga per gruppo, con i valori aggregati|

> `WHERE` filtra le righe **prima** che vengano raggruppate; `GROUP BY` agisce invece sulle righe già filtrate.

---

## Filtrare i gruppi con `HAVING`

La clausola **`HAVING`** filtra i **gruppi** prodotti da `GROUP BY`, mantenendo nel risultato solo quelli che soddisfano una condizione — tipicamente basata su una funzione di aggregazione.

```sql
SELECT voto, COUNT(*) AS numero_studenti
FROM studenti
GROUP BY voto
HAVING COUNT(*) > 5;
```

- **`HAVING COUNT(*) > 5`** → scarta i gruppi che contengono 5 o meno studenti; vengono mantenuti solo i voti ottenuti da più di 5 studenti.

La differenza chiave con `WHERE` è **quando** agisce:

|Clausola|Quando agisce|Filtra|
|---|---|---|
|`WHERE`|Prima del raggruppamento|Le singole **righe**|
|`HAVING`|Dopo il raggruppamento|I **gruppi**|

> `WHERE` non può usare funzioni di aggregazione (`COUNT`, `AVG`, …) perché agisce riga per riga, prima che i gruppi esistano. `HAVING` è nato proprio per questo scopo.

### Ordine di esecuzione con HAVING

|Passo|Clausola|Operazione|
|---|---|---|
|1|`FROM`|Accede alla tabella|
|2|`WHERE`|Filtra le singole righe|
|3|`GROUP BY`|Raggruppa le righe per i valori specificati|
|4|`HAVING`|Filtra i gruppi in base alla condizione|
|5|`SELECT`|Restituisce una riga per ogni gruppo rimasto|

---

## Query annidate e query correlate

Una **query annidata** (o sottoquery) è una query contenuta all'interno di un'altra query. Si distinguono due tipi in base al grado di dipendenza tra le due query.

Una sottoquery **non correlata** può essere eseguita in modo completamente indipendente dalla query esterna: il database la esegue una volta sola, salva il risultato in una tabella temporanea e lo passa alla query esterna.

```sql
SELECT cognome
FROM studenti
WHERE voto = (SELECT MAX(voto) FROM studenti);
```

- La query interna (`SELECT MAX(voto) FROM studenti`) viene eseguita per prima e produce un unico valore.
- Quel valore viene passato alla query esterna, che filtra le righe in base ad esso.
- Non c'è nessun legame tra le due query: la sottoquery non ha bisogno di sapere nulla della query esterna per essere eseguita.

Una **query correlata** è invece una sottoquery che **usa un valore proveniente dalla query esterna**: fa riferimento a una colonna della riga che la query esterna sta elaborando in quel momento, quindi deve essere rieseguita una volta per ogni riga.

```sql
SELECT cognome
FROM studenti s1
WHERE voto > (SELECT AVG(voto) FROM studenti s2 WHERE s2.corso = s1.corso);
```

La query esterna assegna l'alias `s1` alla tabella; la sottoquery usa `s1.corso` — un valore che appartiene alla riga corrente di `s1`. Il database esegue i passi seguenti per ogni riga della query esterna:

1. Prende la riga corrente di `s1` (es. uno studente del corso "Informatica").
2. Passa il valore `s1.corso = 'Informatica'` alla sottoquery.
3. La sottoquery calcola `AVG(voto)` solo per gli studenti di "Informatica".
4. Confronta il voto dello studente corrente con quella media.
5. Passa alla riga successiva di `s1` e ricomincia dal passo 1.

Poiché la sottoquery deve essere rieseguita per ogni riga, le query correlate sono generalmente **più lente** di quelle non correlate.

> **Riconoscere una query correlata**: se rimuovendo la query esterna la sottoquery diventa priva di senso (perché referenzia una colonna come `s1.corso` che non esiste più), allora è correlata. Se la sottoquery è autonoma e produce un risultato da sola, è non correlata.

### Esempi pratici

**Studenti con voto superiore alla media della propria classe:**

```sql
SELECT cognome, classe, voto
FROM Studenti s1
WHERE voto > (SELECT AVG(voto)
              FROM Studenti s2
              WHERE s2.classe = s1.classe);
```

Per ogni studente in `s1`, la sottoquery calcola la media solo degli studenti della sua stessa classe. Uno studente con voto 7 in una classe con media 6 viene incluso; lo stesso voto 7 in una classe con media 8 viene escluso.

---

**Studenti che hanno preso il voto più alto nella propria classe:**

```sql
SELECT cognome, classe, voto
FROM Studenti s1
WHERE voto = (SELECT MAX(voto)
              FROM Studenti s2
              WHERE s2.classe = s1.classe);
```

La sottoquery trova il massimo della classe dello studente corrente. Vengono restituiti tutti gli studenti a pari merito se più studenti condividono il voto massimo.

---

**Studenti che hanno sostenuto almeno un'interrogazione in ogni materia:**

```sql
SELECT cognome
FROM Studenti s
WHERE NOT EXISTS (
    SELECT 1
    FROM Materie m
    WHERE NOT EXISTS (
        SELECT 1
        FROM Interrogazioni i
        WHERE i.matricola = s.matricola
          AND i.materia = m.materia
    )
);
```

Questo è un esempio di query correlata **doppiamente annidata**: per ogni studente `s`, controlla che non esista nessuna materia `m` per cui quello studente non abbia interrogazioni. Se nessuna materia manca → lo studente viene incluso.

---

---

## Sottoquery scalari

Una sottoquery è **scalare** quando restituisce esattamente **un solo valore** (una riga, una colonna). Solo in questo caso può essere usata con gli operatori di confronto semplici ('=', `>`, `<`, `>=`, `<=`, `<>`), perché confrontare una colonna con un insieme di valori produce un errore.

```sql
SELECT cognome
FROM Studenti
WHERE voto > (SELECT AVG(voto) FROM Interrogazioni);
```

Qui la sottoquery restituisce un singolo numero (la media generale), che viene poi usato direttamente nel confronto.

> ⚠️ Se la sottoquery dovesse restituire più di un valore — ad esempio perché la condizione non è sufficientemente restrittiva — il database genera un errore. In quei casi si usano invece `IN`, `ANY` o `ALL`.

---

## Sottoquery che restituiscono un insieme di valori

Quando la sottoquery restituisce **più valori**, non si possono usare gli operatori di confronto semplici. Si usano invece operatori appositi.

### `IN` e `NOT IN`

Verificano se un valore è presente (o assente) nell'insieme restituito dalla sottoquery.

```sql
SELECT cognome
FROM Studenti
WHERE matricola IN (SELECT matricola FROM Interrogazioni WHERE voto >= 8);
```

Restituisce gli studenti che hanno ottenuto almeno un voto maggiore o uguale a 8.

```sql
SELECT cognome
FROM Studenti
WHERE matricola NOT IN (SELECT matricola FROM Interrogazioni WHERE voto < 6);
```

Restituisce gli studenti che non hanno mai preso un voto inferiore a 6.

> ⚠️ **Attenzione con `NOT IN` e i `NULL`**: se la sottoquery restituisce anche un solo valore `NULL` nell'insieme, `NOT IN` non restituisce nessuna riga. Questo perché il confronto con `NULL` è sempre indeterminato. In questi casi è più sicuro usare `NOT EXISTS`.

### `EXISTS` e `NOT EXISTS`

`EXISTS` verifica se la sottoquery restituisce **almeno una riga**. Non importa quali valori contiene — basta che il risultato non sia vuoto. Per questo motivo la sottoquery è quasi sempre scritta come `SELECT 1` o `SELECT *`: il valore restituito non viene usato.

```sql
SELECT cognome
FROM Studenti s
WHERE EXISTS (SELECT 1 FROM Interrogazioni i WHERE i.matricola = s.matricola AND i.voto >= 8);
```

Restituisce gli studenti che hanno **almeno una** interrogazione con voto ≥ 8. La sottoquery usa `s.matricola` dalla query esterna — è quindi una **query correlata**, rieseguita per ogni studente.

`NOT EXISTS` è vero quando la sottoquery **non restituisce nessuna riga**:

```sql
SELECT cognome
FROM Studenti s
WHERE NOT EXISTS (SELECT 1 FROM Interrogazioni i WHERE i.matricola = s.matricola AND i.voto < 6);
```

Restituisce gli studenti che **non hanno mai** preso un voto inferiore a 6.

**Perché preferire `NOT EXISTS` a `NOT IN`:**

||`NOT IN`|`NOT EXISTS`|
|---|---|---|
|Comportamento con `NULL` nella sottoquery|⚠️ Restituisce 0 righe|✅ Funziona correttamente|
|Tipo di query|Non correlata|Correlata|
|Leggibilità|Più semplice|Più esplicita|

> In generale `EXISTS` è più efficiente di `IN` quando la sottoquery restituisce molte righe, perché si ferma appena trova la prima corrispondenza invece di costruire l'intero insieme.

### `ANY`

Abbinato a un operatore di confronto, è vero se la condizione è soddisfatta da **almeno un elemento** dell'insieme. È equivalente a confrontare con il valore più "permissivo" dell'insieme.

```sql
SELECT cognome
FROM Studenti
WHERE voto > ANY (SELECT voto FROM Interrogazioni WHERE classe LIKE '5BI');
```

Restituisce gli studenti il cui voto è maggiore di almeno uno dei voti della classe `5BI`. In pratica equivale a `voto > MIN(...)`: basta superare il voto più basso.

> '= ANY (...)' è equivalente a `IN (...)`.

### `ALL`

Abbinato a un operatore di confronto, è vero solo se la condizione è soddisfatta da **tutti gli elementi** dell'insieme.

```sql
SELECT cognome
FROM Studenti
WHERE voto > ALL (SELECT voto FROM Interrogazioni WHERE classe LIKE '5BI');
```

Restituisce gli studenti il cui voto è maggiore di tutti i voti della classe `5BI`. In pratica equivale a `voto > MAX(...)`: bisogna superare anche il voto più alto.

---

## Dove si può annidare una sottoquery

#### Nella `FROM`

Una sottoquery può comparire nella clausola `FROM` al posto di una tabella. È utile per pre-filtrare i dati prima di eseguire un join, riducendo il numero di righe coinvolte nell'operazione.

Versione senza sottoquery (il join coinvolge tutta la tabella `Studenti`, più dispendioso):

```sql
SELECT AVG(voto)
FROM Interrogazione NATURAL JOIN Studenti
WHERE classe LIKE '5BI';
```

Versione ottimizzata con sottoquery nella `FROM` (prima si filtrano solo gli studenti della classe `5BI`, poi si esegue il join):

```sql
SELECT AVG(voto)
FROM Interrogazione NATURAL JOIN (SELECT * FROM Studenti WHERE classe LIKE '5BI') AS studenti_5BI;
```

> In SQL standard una sottoquery nella `FROM` deve avere sempre un **alias** (qui `AS studenti_5BI`), altrimenti il database non sa come riferirsi a essa.

#### Nella `WHERE`

Una sottoquery può comparire nella clausola `WHERE` per confrontare un valore con il risultato di un'altra query.

```sql
SELECT DISTINCT matricola, cognome
FROM Studenti NATURAL JOIN Interrogazioni
WHERE voto = (SELECT MAX(voto) FROM Interrogazioni WHERE classe LIKE '5BI');
```

- La sottoquery `SELECT MAX(voto) FROM Interrogazioni WHERE classe LIKE '5BI'` calcola il voto massimo tra gli studenti della classe `5BI`.
- La query esterna restituisce i dati degli studenti che hanno ottenuto esattamente quel voto.

#### Nella `HAVING`

Una sottoquery può comparire nella clausola `HAVING` per filtrare i gruppi in base al risultato di un'altra query.

```sql
SELECT DISTINCT matricola, cognome, AVG(voto)
FROM Interrogazioni NATURAL JOIN Studenti
WHERE classe LIKE '5BI'
GROUP BY matricola, cognome
HAVING AVG(voto) > (SELECT AVG(voto) FROM Interrogazioni NATURAL JOIN Studenti WHERE classe LIKE '5BI');
```

- La sottoquery calcola la **media generale** dei voti di tutta la classe `5BI`.
- La query esterna raggruppa gli studenti per matricola e cognome, calcolando la media individuale.
- `HAVING` mantiene solo gli studenti la cui media personale è **superiore** alla media della classe.

---

## Operatori insiemistici

Gli operatori insiemistici combinano i risultati di **due query** trattandoli come insiemi. Per funzionare correttamente, le due query devono avere lo **stesso numero di colonne**, nello **stesso ordine**, con **tipi compatibili**: la prima colonna della prima query viene unita alla prima colonna della seconda, la seconda alla seconda, e così via. I nomi delle colonne nel risultato finale sono quelli della prima query.

|Operatore|Risultato|
|---|---|
|`UNION`|Tutte le righe di entrambe le query, senza duplicati|
|`INTERSECT`|Solo le righe presenti in **entrambe** le query|
|`EXCEPT`|Le righe della prima query che **non compaiono** nella seconda|

```sql
-- Studenti che hanno preso almeno un 8 O che sono in classe 5BI
SELECT matricola FROM Interrogazioni WHERE voto >= 8
UNION
SELECT matricola FROM Studenti WHERE classe LIKE '5BI';
```

```sql
-- Studenti che hanno preso almeno un 8 E sono in classe 5BI
SELECT matricola FROM Interrogazioni WHERE voto >= 8
INTERSECT
SELECT matricola FROM Studenti WHERE classe LIKE '5BI';
```

```sql
-- Studenti che hanno preso almeno un 8 ma NON sono in classe 5BI
SELECT matricola FROM Interrogazioni WHERE voto >= 8
EXCEPT
SELECT matricola FROM Studenti WHERE classe LIKE '5BI';
```

> `UNION ALL` include i duplicati nel risultato, a differenza di `UNION` che li elimina automaticamente.

---

## Funzioni speciali e gestione dei `NULL`

### `IFNULL`

La funzione **`IFNULL`** gestisce i valori `NULL` sostituendoli con un valore di default specificato. Prende due argomenti: se il primo è `NULL`, restituisce il secondo; altrimenti restituisce il primo.

```sql
IFNULL(espressione, valore_default)
```

### Esempio

```sql
SELECT cognome, IFNULL(voto, 0) AS voto
FROM Studenti;
```

- Se la colonna `voto` contiene `NULL` (es. lo studente non ha ancora sostenuto l'interrogazione), viene restituito `0` al suo posto.
- Se `voto` ha un valore, viene restituito normalmente.

> ⚠️ `NULL` non è zero: è l'assenza di un valore. Le funzioni di aggregazione come `AVG` e `SUM` ignorano i `NULL` automaticamente, il che può portare a risultati diversi da quelli attesi. `IFNULL` è utile quando si vuole trattare esplicitamente i valori mancanti come un valore concreto prima di usarli in calcoli o confronti.

---

---

### `COALESCE`

**`COALESCE`** accetta un numero qualsiasi di argomenti e restituisce il **primo valore non `NULL`** che trova, leggendoli da sinistra a destra. Se tutti i valori sono `NULL`, restituisce `NULL`.

```sql
COALESCE(valore1, valore2, valore3, …)
```

```sql
SELECT cognome, COALESCE(cellulare, telefono_fisso, 'N/D') AS contatto
FROM Studenti;
```

- Se `cellulare` non è `NULL` → restituisce `cellulare`.
- Se `cellulare` è `NULL` ma `telefono_fisso` non lo è → restituisce `telefono_fisso`.
- Se entrambi sono `NULL` → restituisce la stringa `'N/D'`.

> `COALESCE` è la versione generalizzata di `IFNULL`: `IFNULL(a, b)` equivale a `COALESCE(a, b)`, ma `COALESCE` accetta più di due argomenti ed è lo standard SQL.

---

---

### `NULLIF`

**`NULLIF`** confronta due valori e restituisce `NULL` se sono uguali, altrimenti restituisce il primo valore. È l'operazione inversa di `IFNULL`.

```sql
NULLIF(valore1, valore2)
```

```sql
SELECT cognome, NULLIF(voto, 0) AS voto
FROM Studenti;
```

- Se `voto = 0` → restituisce `NULL` (tratta lo zero come assenza di valore).
- Se `voto ≠ 0` → restituisce `voto` normalmente.

Un uso comune è evitare divisioni per zero:

```sql
SELECT totale / NULLIF(divisore, 0) AS risultato
FROM tabella;
```

Se `divisore` è `0`, `NULLIF` lo trasforma in `NULL`, e la divisione per `NULL` restituisce `NULL` invece di generare un errore.

---

---

### `CASE`

**`CASE`** è un'espressione condizionale che restituisce valori diversi in base a condizioni, simile a un `if-else`. Può essere usata in `SELECT`, `WHERE`, `ORDER BY` e `HAVING`.

Esistono due forme:

### Forma semplice (confronto con un valore fisso)

```sql
CASE espressione
    WHEN valore1 THEN risultato1
    WHEN valore2 THEN risultato2
    …
    ELSE risultato_default
END
```

```sql
SELECT cognome,
       CASE voto
           WHEN 10 THEN 'Eccellente'
           WHEN 9  THEN 'Ottimo'
           WHEN 8  THEN 'Buono'
           ELSE 'Sufficiente o inferiore'
       END AS giudizio
FROM Studenti;
```

### Forma ricercata (condizioni arbitrarie)

```sql
CASE
    WHEN condizione1 THEN risultato1
    WHEN condizione2 THEN risultato2
    …
    ELSE risultato_default
END
```

```sql
SELECT cognome,
       CASE
           WHEN voto >= 9 THEN 'Ottimo'
           WHEN voto >= 7 THEN 'Buono'
           WHEN voto >= 6 THEN 'Sufficiente'
           ELSE 'Insufficiente'
       END AS giudizio
FROM Studenti;
```

Le condizioni vengono valutate nell'ordine in cui sono scritte: appena una è vera, viene restituito il suo risultato e le successive vengono ignorate.

> La clausola `ELSE` è opzionale: se omessa e nessuna condizione è soddisfatta, `CASE` restituisce `NULL`. È buona pratica includerla sempre per evitare valori inattesi.

---

## Trigger

Un **trigger** è un blocco di codice SQL che viene eseguito automaticamente dal database in risposta a un evento su una tabella (`INSERT`, `UPDATE` o `DELETE`). A differenza delle procedure, non viene chiamato manualmente: si attiva da solo quando si verifica l'evento specificato.

### Struttura

```sql
CREATE TRIGGER nome_trigger
{ BEFORE | AFTER } { INSERT | UPDATE | DELETE }
ON nome_tabella
FOR EACH ROW
BEGIN
    -- istruzioni
END;
```

- **`BEFORE`** → il codice viene eseguito **prima** che l'operazione venga applicata alla tabella. Utile per validare o modificare i dati prima dell'inserimento.
- **`AFTER`** → il codice viene eseguito **dopo** che l'operazione è avvenuta. Utile per aggiornare altre tabelle in conseguenza della modifica.
- **`FOR EACH ROW`** → il trigger viene eseguito una volta per ogni riga coinvolta nell'operazione.

### `NEW` e `OLD`

All'interno del trigger si possono usare due riferimenti speciali per accedere ai valori della riga che ha scatenato l'evento:

|Riferimento|Disponibile in|Contiene|
|---|---|---|
|`NEW`|`INSERT`, `UPDATE`|I valori della riga **dopo** la modifica|
|`OLD`|`DELETE`, `UPDATE`|I valori della riga **prima** della modifica|

### Esempio

Dato il seguente schema:

```
ORCHESTRA(CodO, NomeO, NomeDirettore, numElementi)
CONCERTI(CodC, Data, CodO, CodS, PrezzoBiglietto)
SALE(CodS, NomeS, Citta, Capienza)
MUSICISTA(CodM, nome, cognome, strumento, CodO)
```

Quando viene inserito un nuovo musicista, si vuole incrementare automaticamente il contatore `numElementi` dell'orchestra a cui appartiene:

```sql
CREATE TRIGGER aumento_numero_musicisti
AFTER INSERT ON MUSICISTA
FOR EACH ROW
BEGIN
    UPDATE ORCHESTRA
    SET numElementi = numElementi + 1
    WHERE CodO = NEW.CodO;
END;
```

- Il trigger si attiva **dopo** ogni `INSERT` sulla tabella `MUSICISTA`.
- `NEW.CodO` contiene il valore di `CodO` della riga appena inserita.
- L'`UPDATE` aggiorna solo l'orchestra a cui appartiene il nuovo musicista.

Analogamente, un trigger `AFTER DELETE` può decrementare il contatore:

```sql
CREATE TRIGGER diminuzione_numero_musicisti
AFTER DELETE ON MUSICISTA
FOR EACH ROW
BEGIN
    UPDATE ORCHESTRA
    SET numElementi = numElementi - 1
    WHERE CodO = OLD.CodO;
END;
```

Qui si usa `OLD.CodO` perché la riga è già stata eliminata: `NEW` non esiste in un trigger `DELETE`.

### Gestione degli errori con `SIGNAL`

All'interno di un trigger (o di una procedura) è possibile bloccare l'operazione e restituire un errore personalizzato usando `SIGNAL`:

```sql
CREATE TRIGGER controlla_capienza
BEFORE INSERT ON CONCERTI
FOR EACH ROW
BEGIN
    DECLARE capienza_sala INT;
    SELECT Capienza INTO capienza_sala
    FROM SALE WHERE CodS = NEW.CodS;

    IF capienza_sala < 100 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'La sala non ha capienza sufficiente per un concerto.';
    END IF;
END;
```

- **`SIGNAL SQLSTATE '45000'`** → genera un errore e interrompe l'operazione. `'45000'` è il codice standard per errori personalizzati.
- **`SET MESSAGE_TEXT`** → imposta il messaggio di errore che verrà restituito all'utente o all'applicazione.
- Poiché il trigger è `BEFORE INSERT`, se `SIGNAL` viene eseguito l'inserimento non avviene.

---

## Procedure

Una **procedura** (stored procedure) è un blocco di codice SQL salvato nel database con un nome, che può essere richiamato manualmente tramite `CALL`. A differenza del trigger, non si attiva automaticamente: viene eseguita solo quando viene chiamata esplicitamente.

```sql
CREATE PROCEDURE nome_procedura(parametri)
BEGIN
    -- istruzioni
END;
```

### Parametri

I parametri possono avere tre modalità:

|Modalità|Descrizione|
|---|---|
|`IN`|Valore passato alla procedura (input)|
|`OUT`|Valore restituito dalla procedura (output)|
|`INOUT`|Valore passato e poi restituito modificato|

### Esempio

Procedura che trasferisce un musicista da un'orchestra a un'altra, aggiornando i contatori di entrambe:

```sql
CREATE PROCEDURE trasferisci_musicista(
    IN p_CodM INT,
    IN p_nuovoCodO INT
)
BEGIN
    DECLARE vecchio_CodO INT;

    SELECT CodO INTO vecchio_CodO
    FROM MUSICISTA WHERE CodM = p_CodM;

    UPDATE ORCHESTRA
    SET numElementi = numElementi - 1
    WHERE CodO = vecchio_CodO;

    UPDATE MUSICISTA
    SET CodO = p_nuovoCodO
    WHERE CodM = p_CodM;

    UPDATE ORCHESTRA
    SET numElementi = numElementi + 1
    WHERE CodO = p_nuovoCodO;
END;
```

Per eseguire la procedura:

```sql
CALL trasferisci_musicista(42, 7);
```

Questo sposta il musicista con `CodM = 42` nell'orchestra con `CodO = 7`, aggiornando entrambi i contatori.

> Le procedure possono contenere variabili locali (`DECLARE`), strutture di controllo (`IF`, `WHILE`, `LOOP`) e gestione degli errori (`SIGNAL`). Sono utili per raggruppare operazioni complesse che devono essere eseguite più volte o da più parti dell'applicazione.

---