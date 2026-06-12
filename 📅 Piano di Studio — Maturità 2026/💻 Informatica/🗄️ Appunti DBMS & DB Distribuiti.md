## 🧩 1. Funzionalità del DBMS

Il **DBMS** (Database Management System) è il software che gestisce l'accesso, la memorizzazione e la manipolazione dei dati in modo efficiente, sicuro e coerente.

### 1.1 Gestore dell'interfaccia utente

- Interpreta i comandi SQL inviati dall'utente o dall'applicazione
- Traduce le query in operazioni interne ottimizzate
- Fornisce strumenti di amministrazione (es. MySQL Workbench, phpMyAdmin)

### 1.2 Gestore delle interrogazioni (Query Processor)

- **Parsing**: verifica sintattica e semantica della query
- **Ottimizzazione**: sceglie il piano d'esecuzione più efficiente (query optimizer)
- **Esecuzione**: accede ai dati fisici secondo il piano scelto
- 🔍 Fasi del ciclo di una query
    1. Query SQL → parser
    2. Verifica dei permessi (autorizzazione)
    3. Ottimizzazione logica (riscrittura della query)
    4. Ottimizzazione fisica (scelta degli indici, join order)
    5. Esecuzione e restituzione del risultato

### 1.3 Gestore delle transazioni

Una **transazione** è una sequenza di operazioni che deve essere eseguita come un'unità atomica.

| Proprietà | Descrizione |
| --- | --- |
| **A**tomicità | O tutto o niente: la transazione viene eseguita completamente o non viene eseguita affatto |
| **C**oerenza | Il DB passa da uno stato coerente a un altro stato coerente |
| **I**solamento | Le transazioni concorrenti non si interferiscono tra loro |
| **D**urabilità | Gli effetti di una transazione confermata (COMMIT) sono permanenti |

Le proprietà ACID sono garantite dal DBMS attraverso:

- **Lock** (blocchi) per l'isolamento
- **Log** per atomicità e durabilità
- **Controllo di concorrenza** per la consistenza

### 1.4 Gestore dei guasti (Recovery Manager)

Il DBMS deve garantire la **persistenza** dei dati anche in caso di guasto.

- ⚡ Tipi di guasto
    - **Guasto di transazione**: errore logico o di sistema che interrompe una singola transazione → ROLLBACK
    - **Guasto di sistema** (crash): perdita della memoria volatile (RAM) → ripristino dal log
    - **Guasto di supporto** (disk failure): perdita della memoria permanente → ripristino da backup + log

Tecniche di recovery:

- **Checkpoint**: salvataggio periodico dello stato del DB sul disco
- **Log (journal)**: registro cronologico di tutte le operazioni (`BEGIN`, `WRITE`, `COMMIT`, `ABORT`)
- **UNDO**: annulla le operazioni di transazioni non completate
- **REDO**: riesegue le operazioni di transazioni completate ma non ancora scritte su disco

### 1.5 Gestore della memoria

- Gestisce il **buffer pool**: porzione di RAM usata come cache per i blocchi del disco
- Usa algoritmi di rimpiazzo (LRU, Clock) per decidere quali blocchi tenere in memoria
- Ottimizza le letture/scritture su disco (I/O è il collo di bottiglia principale)

---

## 🌐 2. Database Distribuiti

Un **DB distribuito** è un insieme di basi di dati logicamente correlate, fisicamente distribuite su nodi diversi (server, siti) collegati da una rete.

> 💡 L'utente vede il sistema come se fosse un unico database centralizzato — **trasparenza della distribuzione**.
> 

### 2.1 Vantaggi dei DB distribuiti

- **Affidabilità**: se un nodo cade, gli altri continuano a funzionare
- **Disponibilità**: i dati possono essere replicati su più nodi
- **Prestazioni**: le query possono essere eseguite in parallelo su più nodi
- **Scalabilità**: si aggiungono nodi senza ricostruire tutto il sistema
- **Autonomia locale**: ogni sede gestisce i propri dati

### 2.2 Svantaggi

- **Complessità** progettuale e gestionale
- **Costi di comunicazione** tra i nodi
- **Gestione della coerenza** dei dati replicati
- **Sicurezza** distribuita più difficile da implementare

### 2.3 Tecniche di progettazione

#### Frammentazione

I dati vengono suddivisi tra i nodi. Esistono tre tipi:

- 📦 Frammentazione orizzontale
    
    Divisione per **righe**: ogni nodo contiene un sottoinsieme di tuple.
    
    ```
    Tabella Clienti:
      Nodo Milano → clienti della Lombardia
      Nodo Roma   → clienti del Lazio
    ```
    
    Criterio: una condizione logica (`WHERE regione = 'Lombardia'`)
    
- 📦 Frammentazione verticale
    
    Divisione per **colonne**: ogni nodo contiene un sottoinsieme di attributi (+ la chiave primaria per ricostruire le tuple).
    
    ```jsx
    Tabella Impiegati:
      Nodo A → id, nome, cognome
      Nodo B → id, stipendio, reparto
    ```
    
- 📦 Frammentazione mista
    
    Combinazione di orizzontale e verticale. Prima si frammenta orizzontalmente, poi verticalmente (o viceversa).
    

#### Replicazione

Le stesse porzioni di dati sono copiate su più nodi.

| Tipo | Descrizione |
| --- | --- |
| **Replicazione completa** | Ogni nodo ha una copia dell'intero DB → massima disponibilità, scritture lente |
| **Replicazione parziale** | Solo alcuni frammenti sono replicati |
| **Nessuna replicazione** | Ogni dato esiste su un solo nodo → più semplice, meno fault-tolerant |

#### Allocazione

Decide **dove** collocare frammenti e repliche:

- **Centralizzata**: tutti i dati su un unico nodo (non distribuita)
- **Partizionata**: ogni frammento su un solo nodo
- **Replicata**: i frammenti esistono su più nodi

### 2.4 Trasparenza

Il DBMS distribuito deve nascondere all'utente la complessità della distribuzione:

| Livello | Cosa nasconde |
| --- | --- |
| **Trasparenza di frammentazione** | L'utente non sa che i dati sono divisi |
| **Trasparenza di replicazione** | L'utente non sa che esistono copie multiple |
| **Trasparenza di locazione** | L'utente non sa su quale nodo si trovano i dati |

### 2.5 Transazioni distribuite

Le transazioni distribuite coinvolgono più nodi → serve il **Two-Phase Commit (2PC)**:

- 🔄 Protocollo Two-Phase Commit
    
    **Fase 1 — Prepare (Voting):**
    
    - Il **coordinatore** invia `PREPARE` a tutti i nodi partecipanti
    - Ogni nodo risponde `YES` (pronto a fare commit) o `NO` (abort)
    
    **Fase 2 — Commit/bv bAbort:**
    
    - Se tutti hanno risposto `YES` → coordinatore invia `COMMIT` a tutti
    - Se almeno uno ha risposto `NO` → coordinatore invia `ABORT` a tutti
    
    ⚠️ Problema: se il coordinatore si blocca dopo la fase 1, i partecipanti rimangono in attesa (blocking problem).
    

### OLTP vs OLAP

I DBMS distribuiti gestiscono due grandi categorie di carichi di lavoro, con obiettivi opposti:

|  | **OLTP** | **OLAP** |
| --- | --- | --- |
| Nome esteso | Online Transaction Processing | Online Analytical Processing |
| Scopo | Gestire operazioni quotidiane (inserimenti, aggiornamenti, letture puntuali) | Analizzare grandi volumi di dati storici per decisioni aziendali |
| Tipo di query | Semplici, brevi, molte in parallelo | Complesse, lunghe, pochi utenti |
| Dati coinvolti | Poche righe per volta | Milioni di righe (aggregazioni, tendenze) |
| Esempi | Prenotazione biglietto, pagamento POS, login utente | Report vendite annuali, analisi trend, Data Mining |
| DB tipico | DB relazionale normalizzato | Data Warehouse, DB denormalizzato |
| Priorità | Velocità, integrità, ACID | Throughput lettura, prestazioni aggregazioni |

> 💡 In un DDBMS: l'**OLTP** è distribuito per garantire disponibilità e velocità locale. L'**OLAP** è tipicamente centralizzato in un Data Warehouse alimentato dai nodi OLTP.
> 

### Elaborazione Online vs Offline

- 🟢 Elaborazione Online
    
    Le operazioni vengono eseguite **in tempo reale**, non appena arrivano:
    
    - L'utente interagisce direttamente col sistema e riceve risposta immediata
    - Il DB è sempre aggiornato e consistente
    - Esempi: prenotazione voli, home banking, e-commerce
    - Richiede alta disponibilità, bassa latenza, transazioni ACID
- 🔴 Elaborazione Offline (Batch)
    
    Le operazioni vengono **accumulate** e processate in blocco in un momento successivo (tipicamente di notte o nei periodi di basso carico):
    
    - Non c'è interazione in tempo reale con l’utente
    - Adatta per operazioni massive e non urgenti
    - Esempi: calcolo stipendi mensili, generazione estratti conto, backup notturno, ETL verso il Data Warehouse
    - Richiede alto throughput, non bassa latenza

|  | **Online** | **Offline (Batch)** |
| --- | --- | --- |
| Tempistica | Immediata, real-time | Differita, pianificata |
| Interazione utente | Diretta | Nessuna durante l’esecuzione |
| Volume per esecuzione | Piccolo (singole transazioni) | Grande (milioni di record) |
| Priorità | Latenza bassa | Throughput alto |
| Tipico uso | OLTP | ETL, report, backup |

---

### 2.6 Come funziona una query in un DDBMS

Quando l'utente esegue una query su un DB distribuito, il DDBMS non la esegue su un singolo nodo — la **decompone e propaga** ai nodi che contengono i dati rilevanti, poi **raccoglie e assembla** i risultati.

#### Fasi della query distribuita

- 1️⃣ Ricezione e parsing
    - L'utente invia la query SQL al **nodo coordinatore** (o nodo locale)
    - Il coordinatore fa il parsing e verifica la correttezza sintattica/semantica
    - Consulta il **catalogo distribuito** (dizionario dei dati) per sapere dove si trovano i frammenti coinvolti
- 2️⃣ Decomposizione e ottimizzazione globale
    - La query viene **decomposta** in sotto-query, una per ogni nodo che possiede dati rilevanti
    - L'ottimizzatore globale sceglie il piano migliore tenendo conto di:
        - Dove sono i frammenti (locazione)
        - Costo di trasmissione dei dati in rete
        - Carico dei nodi
    
    > 💡 Obiettivo: **minimizzare i dati trasferiti in rete**, non solo il tempo di elaborazione locale.
    > 
- 3️⃣ Propagazione ai nodi (esecuzione locale)
    - Il coordinatore **invia le sotto-query** ai nodi coinvolti
    - Ogni nodo esegue la propria sotto-query **localmente** sul proprio frammento
    - I nodi lavorano **in parallelo** → vantaggio principale del modello distribuito
    
    ```
    Query globale: SELECT * FROM Ordini WHERE anno = 2024
    
      Nodo Milano → SELECT * FROM Ordini_MI WHERE anno = 2024
      Nodo Roma   → SELECT * FROM Ordini_RM WHERE anno = 2024
      Nodo Napoli → SELECT * FROM Ordini_NA WHERE anno = 2024
    ```
    
- 4️⃣ Raccolta e assemblaggio dei risultati
    - Ogni nodo **restituisce il proprio risultato parziale** al coordinatore
    - Il coordinatore **assembla** i risultati (es. UNION, JOIN, aggregazione)
    - La tabella finale viene restituita all'utente come se provenisse da un unico DB
    
    ```
    Risultato finale = unione dei risultati di Milano + Roma + Napoli
    ```
    

#### Schema riassuntivo

| Fase | Attore | Operazione |
| --- | --- | --- |
| 1. Ricezione | Coordinatore | Parsing + consultazione catalogo |
| 2. Decomposizione | Coordinatore | Scomposizione in sotto-query + ottimizzazione |
| 3. Propagazione | Coordinatore → Nodi | Invio sotto-query in parallelo |
| 4. Esecuzione | Ogni nodo | Query locale sul proprio frammento |
| 5. Assemblaggio | Coordinatore | Unione risultati → tabella finale |

> ⚠️ Il **costo di rete** (latenza + banda) è il fattore critico nelle query distribuite — l'ottimizzatore cerca sempre di spostare il meno possibile tra i nodi.
> 

## 📊 3. Big Data — Le quattro V

> Il termine **Big Data** indica dataset di dimensioni talmente grandi e complessi che i tradizionali strumenti di gestione dei dati non sono sufficienti per elaborarli.
> 

### Le 4 V fondamentali

| V | Nome | Descrizione |
| --- | --- | --- |
| **V1** | **Volume** | Quantità enorme di dati generati (petabyte, exabyte). Es: social media, sensori IoT, log di sistema |
| **V2** | **Velocità** | I dati arrivano e devono essere elaborati in tempo reale o quasi. Es: transazioni finanziarie, stream Twitter |
| **V3** | **Varietà** | Dati di tipi eterogenei: strutturati (tabelle), semi-strutturati (JSON, XML), non strutturati (video, testo, audio) |
| **V4** | **Veridicità** | Qualità e affidabilità dei dati: i dati possono essere rumorosi, incompleti o incoerenti |
- ➕ V aggiuntive (spesso citate)
    - **Valore**: i dati devono produrre informazioni utili → trasformare dati grezzi in conoscenza
    - **Visualizzazione**: capacità di rappresentare i dati in modo comprensibile

### Tecnologie per il Big Data

- **Hadoop**: framework per l'elaborazione distribuita di grandi dataset (MapReduce)
- **Spark**: elaborazione in-memory, più veloce di Hadoop
- **NoSQL**: database non relazionali adatti a dati non strutturati (MongoDB, Cassandra, Redis)
- **Data Lake**: archivio centralizzato di dati grezzi in qualsiasi formato
- **Data Warehouse**: archivio di dati strutturati per l'analisi (OLAP)

---

## 📝 Riepilogo rapido

| Argomento | Concetti chiave |
| --- | --- |
| **DBMS — componenti** | Interfaccia · Query Processor · Transaction Manager · Recovery Manager · Buffer Manager |
| **Transazioni** | Proprietà ACID: Atomicità, Coerenza, Isolamento, Durabilità |
| **Recovery** | Log · Checkpoint · UNDO · REDO · ROLLBACK |
| **DB Distribuiti** | Frammentazione (orizz./vert./mista) · Replicazione · Allocazione |
| **Trasparenza** | Di frammentazione · Di replicazione · Di locazione |
| **2PC** | Protocollo per transazioni distribuite: fase Prepare + fase Commit |
| **Big Data — 4V** | Volume · Velocità · Varietà · Veridicità |

---