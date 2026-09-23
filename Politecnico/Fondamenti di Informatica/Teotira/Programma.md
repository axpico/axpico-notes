## Definizione
Un **programma** è la codifica di un **algoritmo** — cioè una combinazione di passi elementari eseguibili da un esecutore — in un **linguaggio** che comprende istruzioni (e altri costrutti) comprensibili dall'esecutore stesso.

## Linguaggio macchina
Ogni esecutore ha un proprio **linguaggio macchina**, con cui può:
- caricare l'istruzione da eseguire;
- caricare valori dalla memoria;
- calcolare (addizioni, moltiplicazioni, confronti);
- memorizzare valori in memoria;
- saltare a una data istruzione del programma (salto/jump).

Grazie a queste operazioni, l'esecutore è in grado di eseguire programmi scritti nel proprio linguaggio macchina.

## Linguaggi di programmazione: basso vs alto livello

**Linguaggio macchina (basso livello)**
- insieme ridotto di istruzioni, ognuna corrispondente direttamente a un'operazione del processore;
- difficile codificare algoritmi complessi e interpretare il codice a posteriori;
- vantaggi: linguaggio preciso, controllo completo sulle risorse della macchina.

**Linguaggi ad alto livello**
- più vicini al linguaggio naturale e comprensibili per l'uomo;
- precisi e sintetici, usano riferimenti simbolici (nomi di variabili, funzioni) invece di indirizzi;
- permettono di esprimere istruzioni astraendo dai dettagli dell'hardware sottostante.

La traduzione da un linguaggio ad alto livello al linguaggio macchina è compito di un **compilatore** (o traduttore).

## Linguaggi ad alto livello (es. C)
Il **C** è un linguaggio ad alto livello, indipendente dalla macchina, che permette di:
- calcolare e memorizzare valori in memoria;
- estrarre valori dalla memoria;
- leggere dati in ingresso e stampare risultati in uscita;
- eseguire selezioni (if/else) e cicli (for/while).

Per eseguire un programma scritto in un linguaggio ad alto livello è necessario un **compilatore**, che lo traduce nell'opportuno linguaggio macchina.

### Cenni storici sul C
- Nasce nel **1972** da **Dennis Ritchie** come linguaggio ad alto livello per la scrittura di sistemi operativi (usato per riscrivere UNIX).
- Negli anni '80 si diffondono versioni del C per diverse architetture.
- Nel **1983** l'**ANSI** (American National Standards Institute) definisce uno standard del linguaggio, aggiornato successivamente (es. ANSI99).
- Ancora oggi gran parte dei sistemi operativi è scritta in C (o C++).

## Macchina virtuale C
Esecutore considerato: la **macchina virtuale C**. Un **bus** trasporta le informazioni tra le sue unità.

**RAM**
- in C, per distinguere un contenitore (variabile) si usa un nome;
- è comunque possibile usare direttamente l'indirizzo.

**CPU** (*central processing unit*)
- esegue le istruzioni del programma.

**Standard Input**
- unica unità di ingresso (tipicamente la tastiera).

**Standard Output**
- unica unità di uscita (tipicamente il video).

Standard Input, Standard Output e memoria sono divisi in celle elementari, ciascuna contenente un dato, e sono utilizzati dal programma per interagire con l'utente.

**Differenza tra macchina di Von Neumann e macchina virtuale C**
- nella macchina virtuale si ignora dove risiedono fisicamente i programmi in memoria;
- si considera comunque presente un'area di memoria riservata al programma da eseguire.

## Struttura di un programma C

```c
/* commento */
#include <stdio.h>   // direttiva al preprocessore

int main()           // punto di inizio
{
	printf("Hello world!");
	return 0;
}
```

**Commenti** — `/* ... */` racchiude testo ignorato dal compilatore, utile solo per la leggibilità del codice.

**Direttive al compilatore** — `#include<nomeLibreria.h>` rende disponibili nel codice tutte le funzioni definite nella libreria indicata, come se fossero istruzioni del linguaggio. La libreria `stdio.h` (*standard input/output*) contiene le funzioni per la gestione di I/O, tra cui `printf` e `scanf`.

**`main`** — è il punto da cui inizia l'esecuzione del programma; ogni programma C deve contenerne uno.
- Le parentesi tonde `()` indicano che si tratta di una funzione.
- `int main() {...}` dichiara che la funzione restituisce un valore intero (è possibile anche `void main(){...}`, senza valore di ritorno).
- Il corpo della funzione è racchiuso tra parentesi graffe `{ }` e contiene le istruzioni che ne definiscono il comportamento.

**`printf("Hello world!");`**
- è un'istruzione (*statement*), termina con `;`;
- costituisce una **chiamata** alla funzione `printf`, definita nella libreria standard (nel programma compare solo la chiamata);
- le parentesi tonde raccolgono i parametri passati alla funzione (qui, una stringa);
- il carattere di escape `\n` indica un "a capo" (*new line*).

**`return 0;`**
- termina la funzione, restituendo il valore indicato;
- compatibile con la dichiarazione `int main()`;
- per convenzione, `0` indica terminazione senza errori; altri valori sono associati a diversi tipi di errore.

**Linker (collegatore)** — quando si chiama una funzione (es. `printf`), il compilatore la cerca nel codice; se non la trova, il collegatore la cerca nelle librerie (quella standard e quelle incluse con `#include`). La funzione viene copiata dalla libreria nel programma oggetto. Un errore nel nome di una funzione viene rilevato dal collegatore, che non riesce a trovarla.

## Le variabili

Le **variabili** sono riferimenti simbolici a porzioni di memoria in cui sono memorizzati dati manipolabili dal programma. Ogni variabile ha:
- un **nome** (identificatore);
- un **tipo** (insieme di valori e operazioni ammissibili);
- una **dimensione**;
- un **indirizzo** (individua la/le celle di memoria corrispondenti);
- un **valore**.

Leggere il valore di una variabile non lo modifica; assegnare un nuovo valore sostituisce (e distrugge) quello precedente.

**Regole sugli identificatori**
- devono iniziare con una lettera (non con una cifra), seguita da lettere, cifre o `_`;
- il C è *case-sensitive*: `Beta`, `beta`, `bEta`, `BetA` sono identificatori diversi.

Tutte le variabili devono essere **dichiarate** (tipicamente all'inizio del blocco) prima di essere utilizzate, e devono essere inizializzate in modo opportuno per evitare valori indeterminati.

### Tipi semplici predefiniti (built-in)
| Tipo | Contenuto |
|---|---|
| `char` | un carattere della tabella ASCII, corrispondente a un intero in `[0,255]` |
| `int` | numeri interi (anche negativi); range dipendente dall'architettura |
| `float` | numeri decimali a singola precisione |
| `double` | numeri decimali a doppia precisione |

Sono parole chiave (*keyword*) riservate al linguaggio: non possono essere usate come identificatori.

### Dichiarazione di variabili
```c
int a;                 // dichiarazione singola
int a, b;               // più variabili dello stesso tipo
int a = 0, b = 8;       // dichiarazione + inizializzazione
const float Pi = 3.1415; // costante: il contenuto non può essere modificato
```

Il valore di inizializzazione può poi essere modificato con istruzioni di assegnamento o di lettura da Standard Input (per questo si chiamano *variabili*).

## Le istruzioni

Ogni istruzione (*statement*) termina con `;`. Tre categorie principali:
- di **assegnamento**;
- di **ingresso/uscita** (I/O);
- **composte** (selezione, iterazione).

### Istruzione di assegnamento
```
nomeVariabile = espressione;
```
Esecuzione: (1) valuta `espressione`; (2) memorizza il risultato in `nomeVariabile`, sostituendo il valore precedente.

> Il simbolo '=' è l'operatore di **assegnamento**, non di uguaglianza: per confrontare due valori si usa '=='.

`espressione` può essere: una costante (`13`, `'a'`, `2.7182`), una variabile, oppure una combinazione di espressioni tramite operatori e parentesi tonde.

```c
int a, b;
a = 5;      // a = 5
b = a + 2;  // b = 7
a = b;      // a = 7 (copia il valore di b in a)
a = a + 3;  // a = 10
```

I caratteri (`char`) si assegnano tra apici singoli: `a = 'A';`. Attenzione: `a = '1';` assegna il codice ASCII del carattere `'1'` (49), non il numero `1`.

### Operatori aritmetici

**Tra interi (`int`)**

- assegnamento: =
- aritmetici: `+` `-` `*` somma, sottrazione, moltiplicazione
- `/` divisione con troncamento della parte non intera
- `%` resto della divisione intera (modulo)
- relazionali (confronto): uguale = =, diverso !=, minore &lt;, maggiore >;, minore o uguale<=, maggiore o uguale >;= — risultato booleano (`0` per falso, valore diverso da `0` per vero)

- `/` tra interi calcola il quoziente troncato: `int a,b; float c; c = a / b;` esegue comunque una divisione intera prima della conversione. Per ottenere un risultato con parte decimale occorre forzare l'operando a `float`: `c = (1.0 * a) / b;`.
- `%` (modulo): es. `17 % 5` vale `2`; utile per verificare la divisibilità tra numeri. Vale sempre `a` uguale a `(a/b)*b + a%b`.

**Tra reali (`float`, `double`)** — stesse operazioni aritmetiche e relazionali (`+` `-` `*` `/` e confronti), ma **`%` non è definito** tra float.

### Istruzioni di ingresso/uscita (I/O)

**`printf`** — scrittura su Standard Output.
```
printf(stringaControllo, elementiStampa);
```
- `stringaControllo`: stringa tra doppi apici, può contenere caratteri di stampa normali, caratteri speciali (`\n` a capo, `\t` tabulazione) e caratteri di conversione (segnaposto);
- `elementiStampa`: variabili/espressioni/costanti separate da virgola, sostituite nell'ordine ai segnaposto corrispondenti.

Segnaposto principali: `%d` intero, `%f` reale, `%c` carattere, `%s` stringa.

```c
printf("\n %d + %d = %d", a, b, a+b);
```

**`scanf`** — lettura da Standard Input.
```
scanf(stringaControllo, &nomeVariabile);
```
Legge un valore da tastiera, lo converte nel tipo indicato da `stringaControllo` e lo copia nella variabile all'indirizzo `&nomeVariabile`.
- `&variabile` indica l'**indirizzo** in memoria della variabile;
- sono possibili letture multiple: `scanf("%d%d%f", &x, &y, &z);`
- dopo una `scanf("%c", ...)` conviene ripulire il buffer di ingresso (l'invio digitato resta nel buffer) con `fflush(stdin);` oppure `scanf("%*c");`

### Esempio completo
```c
/* somma di due numeri inseriti dall'utente */
#include <stdio.h>
int main()
{
	int a, b;
	int somma;

	printf("Inserire a:");
	scanf("%d", &a);
	printf("Inserire b:");
	scanf("%d", &b);

	somma = a + b;
	printf("\n %d + %d = %d", a, b, somma);
	return 0;
}
```
L'incolonnamento (tab/spazi) non ha effetto sul compilatore: serve solo a migliorare la leggibilità.

## La sequenza di istruzioni

In C le istruzioni sono eseguite **sequenzialmente**, dalla prima all'ultima: terminata la i-esima, si esegue la (i+1)-esima.

```c
int a, z, x;
a = 45;
z = 5;
x = (a - z) / 10;   // x = 4
```

## Il costrutto condizionale `if`

```c
if (condizione)
	statement1;
else
	statement0;
```
- `condizione` è un'espressione booleana valutata a runtime (`0` = falso, valore `!=0` = vero);
- se vera, si esegue `statement1`; altrimenti (se presente) `statement0`;
- `else` è opzionale;
- se il ramo contiene più istruzioni, va racchiuso tra `{ }`;
- l'indentazione è irrilevante per il compilatore, ma va comunque usata per leggibilità.

```c
if (x % 7 == 0)
	printf("%d multiplo di 7", x);
else
	printf("%d non multiplo di 7", x);
```

### `if` annidati
Il corpo di un `if` può contenere a sua volta altri `if`, realizzando condizioni annidate:

```c
if (x % 5 == 0)
	if (x % 7 == 0)
		printf("x multiplo di 5 e anche di 7");
	else
		printf("x multiplo di 5 ma non di 7");
else
	printf("x non multiplo di 5");
```

**Regola di associazione** — in assenza di parentesi, ogni `else` si associa all'`if` più vicino non ancora abbinato. Per associare un `else` a un `if` esterno, o per evitare ambiguità, è necessario usare le parentesi graffe `{ }` attorno al blocco dell'`if` interno.

## Dalla sorgente all'eseguibile

Per un linguaggio compilato come il C, dal codice sorgente si arriva a un programma eseguibile attraverso sei fasi:

1. **Videoscrittura (editing)** — il programmatore scrive il codice sorgente con un editor, ottenendo un file `.c`.
2. **Pre-compilazione (preprocessing)** — il preprocessore elabora le direttive (es. `#include`).
3. **Traduzione (compilazione)** — il **compilatore** traduce il codice sorgente in linguaggio macchina, segnalando eventuali errori lessicali/sintattici; genera un file oggetto (`.obj`).
4. **Collegamento (linking)** — il **collegatore (linker)** unisce il file oggetto ai sottoprogrammi richiesti (dalle librerie o definiti dal programmatore), risolvendo i riferimenti agli indirizzi; genera il **file eseguibile** (`.exe`). Errori tipici: nomi di funzioni non trovate.
5. **Caricamento (loading)** — il **caricatore (loader)**, a cura del Sistema Operativo, copia il contenuto del file eseguibile in un'area libera della memoria centrale.
6. **Esecuzione** — il programma riceve i dati in ingresso e produce i risultati in uscita. Possono verificarsi **errori di run-time** (errori semantici): risultati scorretti (es. overflow), calcoli impossibili (divisione per zero, radice/logaritmo di numero negativo), o errori nella concezione dell'algoritmo.
