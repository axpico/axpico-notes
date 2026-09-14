---
tags: [fondamenti-informatica, algoritmo, flowchart, ansi-c89, boehm-jacopini]
---
## Algoritmo
Un algoritmo si basa su due nozioni:
- **problema**
- **esecutore**
## Problema
Un problema è composto da una terna **(I, O, R)**:
- **I** — ingresso (input): deve soddisfare alcune condizioni di validità
- **O** — uscita (output): deve soddisfare alcune condizioni di validità
- **R** — relazione: deve essere soddisfatta per qualunque insieme di dati valido, tra dati in ingresso e risultati in uscita

### Esempio: minimo tra due numeri naturali
- **I** — due numeri naturali
- **O** — un numero naturale
- **R** — il risultato è uno dei due dati in ingresso: il risultato non è maggiore dell'altro dato (cioè è il minimo dei due)
#### Implementazione in ANSI C89
```c
#include <stdio.h>

/* R: restituisce il minore tra a e b (uno dei due dati, non maggiore dell'altro) */
unsigned int minimo(unsigned int a, unsigned int b)
{
    if (a < b) {
        return a;
    }
    return b;
}

int main(void)
{
    unsigned int a, b;

    printf("Inserisci due numeri naturali: ");
    if (scanf("%u %u", &a, &b) != 2) {
        return 1;
    }

    printf("Il minimo e' %u\n", minimo(a, b));

    return 0;
}
```
> Note ANSI C89: dichiarazioni delle variabili all'inizio del blocco, commenti solo `/* ... */`, `main` con prototipo esplicito `(void)`.

## Esecutore
Un sistema capace di eseguire in modo deterministico ciascun passo elementare appartenente a un insieme (esiguo) di passi elementari.
### Esempio
Insieme di passi elementari eseguibili:
- acquisizione dei dati ("lettura")
- produzione dei risultati ("scrittura")
- addizione di due numeri
- sottrazione fra due numeri
- confronto fra due numeri (calcolo dell'esito "vero" o "falso" di un confronto)

## Algoritmo (definizione formale)
Dati un problema P e un esecutore E, un algoritmo è una combinazione finita di passi elementari, ciascuno eseguibile dall'esecutore E, in grado di risolvere il problema P (cioè per qualunque insieme valido di dati in ingresso, produce in uscita risultati validi che soddisfano la relazione specificata tra ingresso e uscita).

### Esempio: l'opposto di un intero
1. acquisisci un intero
2. sottrai dal valore 0 il valore del numero acquisito
3. produci in uscita il risultato della sottrazione
4. TERMINA

### Esempio: massimo tra due numeri naturali
I: due numeri interi $d_1$ e $d_2$
O: un numero naturale
R: $r \in \{d_1, d_2\}$
$\quad r = d_1 \text{ se } d_1 > d_2$
$\quad r = d_2 \text{ se } d_1 < d_2$

1. acquisisci 2 numeri naturali
2. confronto i 2 numeri naturali
	1. se il primo è maggiore del secondo restituisco il primo
	2. se il secondo è maggiore del primo restituisco il secondo
3. TERMINA
## Combinazione
I passi elementari possono essere combinati in diversi modi: in **sequenza** (lineare) o tramite **selezione** (if/else) — e, come si vedrà, tramite **iterazione**.

## Diagrammi di flusso
Un diagramma di flusso (*flowchart*) è una rappresentazione grafica di un algoritmo: i passi elementari e i punti di decisione sono raffigurati con simboli standardizzati, collegati da frecce (edge) che ne indicano il flusso di controllo.

### Simboli fondamentali
| Simbolo | Forma | Significato |
| --- | --- | --- |
| **Terminatore** | pillola/ellisse | punto di INIZIO o FINE dell'algoritmo |
| **Elaborazione (processo)** | rettangolo | un'operazione elementare (es. assegnazione, calcolo) |
| **Decisione** | rombo | test logico con due uscite (vero/falso) |
| **Input/Output** | parallelogramma | acquisizione (lettura) o produzione (scrittura) di dati |
| **Freccia (edge)** | linea orientata | indica il flusso di controllo tra un passo e il successivo |

### Regole di costruzione
- Ogni diagramma ha un solo punto di INIZIO e almeno un punto di FINE.
- Ogni cammino che parte dall'INIZIO deve condurre, in un numero finito di passi, a un FINE (l'algoritmo deve terminare).
- Ogni simbolo di decisione ha esattamente due uscite (vero e falso).

### Le tre strutture di controllo fondamentali (teorema di Böhm-Jacopini)
Il teorema di Böhm-Jacopini (1966) dimostra che qualunque algoritmo calcolabile tramite diagramma di flusso può essere riscritto usando solo tre costrutti di controllo, opportunamente annidati e composti in sequenza — è la base teorica della **programmazione strutturata**:

1. **Sequenza** — due o più passi eseguiti uno dopo l'altro, nell'ordine in cui compaiono.
2. **Selezione** (if-then-else) — in base all'esito di una decisione, il flusso prosegue lungo uno tra due cammini alternativi, che poi si ricongiungono.
3. **Iterazione** (while/repeat) — un blocco di passi viene ripetuto finché una condizione resta soddisfatta (o finché non lo è più).

### Esempio: diagramma di flusso per il minimo tra due numeri naturali
Traduzione in diagramma di flusso dell'algoritmo visto sopra (§ Esempio: minimo tra due numeri naturali): una sequenza (INIZIO → lettura → scrittura → FINE) con una selezione al suo interno per stabilire quale dei due valori sia il minimo.

![[Diagramma di flusso - minimo.canvas]]

## Memorizzazione
Memorizzazione di un valore "in un contenitore": salvataggio e conservazione interna di un valore durante l'esecuzione di altri passi.

Sintatticamente indicati (da noi) con
```txt
A <-- ...
```
Qui A identifica il contenitore in cui verrà memorizzato il valore di ciò che sta dopo il simbolo `<--`.

Poi in ANSI C89:
```c
A = ... ;
```

```txt
A <-- A + B
```
Il contenitore A viene aggiornato con la somma del suo valore corrente e di B (letto prima di essere sovrascritto).

In ANSI C89:
```c
A = A + B;
```

## Scambio tra due contenitori
### Problema
I: due contenitori M e N, ciascuno con un valore memorizzato
O: gli stessi due contenitori M e N, ciascuno con un valore memorizzato
R: i valori dei due dati e dei due risultati sono gli stessi, ma tali valori sono memorizzati ciascuno nel contenitore in cui era inizialmente memorizzato l'altro (scambio)

### Esecutore
Insieme di passi elementari richiesto: lettura/scrittura di un contenitore e operazione **XOR bit a bit** (`^`) tra i valori di due contenitori (oltre alle operazioni elementari già viste).

### Codice
Scambio "classico" con contenitore ausiliario T:
1. T <-- M
2. M <-- N
3. N <-- T
4. TERMINA

Scambio **senza variabile ausiliaria**, sfruttando le proprietà dello XOR ($a \oplus a = 0$, $a \oplus 0 = a$, associativa e commutativa) — usa solo i due contenitori M e N:
1. M <-- M XOR N
2. N <-- M XOR N
3. M <-- M XOR N
4. TERMINA

#### Implementazione in ANSI C89
```c
#include <stdio.h>

/* R: scambia i valori di *m e *n usando solo le due variabili (XOR swap) */
void scambia(unsigned int *m, unsigned int *n)
{
    *m = *m ^ *n;
    *n = *m ^ *n;
    *m = *m ^ *n;
}

int main(void)
{
    unsigned int m, n;

    printf("Inserisci due numeri naturali: ");
    if (scanf("%u %u", &m, &n) != 2) {
        return 1;
    }

    scambia(&m, &n);

    printf("m = %u, n = %u\n", m, n);

    return 0;
}
```
> Attenzione: lo XOR swap fallisce se M e N sono lo **stesso** contenitore (`scambia(&x, &x)` azzera il valore) — in pratica si preferisce comunque la variabile ausiliaria per chiarezza e sicurezza; lo XOR swap è soprattutto un esercizio sulle proprietà dell'operatore.

## Altri modi per combinare passi elementari
Coerentemente col teorema di Böhm-Jacopini (§ sopra), i passi elementari di un algoritmo si combinano solo in tre modi:
- **sequenza**
- **selezione**
- **iterazione** (o ciclo)

### Iterazione (o ciclo)
Un ciclo è caratterizzato da:
- una **condizione** (espressione booleana, esito vero/falso), e
- una **sequenza** (più in generale, una combinazione) di passi elementari, detta **corpo del ciclo**.

Semantica operativa: ad ogni "giro" la condizione viene **valutata prima** di eseguire il corpo (ciclo *pre-condizionale*, tipico del `while`):
- se la condizione risulta **falsa**, il ciclo non viene eseguito (o non viene più eseguito) e il controllo passa al passo successivo al ciclo;
- se la condizione risulta **vera**, si esegue il corpo del ciclo, poi si ritorna a valutare nuovamente la condizione.

In altre parole: il corpo del ciclo viene eseguito ripetutamente, tante volte quante la condizione risulta vera — zero o più volte in totale.

Perché è una forma di combinazione a sé (non riducibile a sequenza+selezione): a differenza della selezione, dopo l'esecuzione del blocco il flusso **torna indietro** (arco all'indietro, *back-edge*) invece di proseguire in avanti; questo è ciò che permette di ripetere un numero di volte non noto a priori (dipendente dai dati in ingresso), condizione necessaria per poter esprimere computazioni come somme, ricerche o elaborazioni su sequenze di lunghezza arbitraria.

#### Diagramma di flusso del ciclo (pre-condizionale, tipo `while`)
```mermaid
flowchart TD
    Start([INIZIO]) --> Cond{condizione?}
    Cond -- vero --> Body[corpo del ciclo]
    Body --> Cond
    Cond -- falso --> End([FINE / passo successivo])
```

#### Corrispondenza in ANSI C89
```c
while (condizione) {
    /* corpo del ciclo */
}
```

> Nota terminologica: questa è la forma **pre-condizionale** (`while`), in cui la condizione è valutata *prima* del corpo, quindi il corpo può essere eseguito **zero** volte. Esiste anche la forma **post-condizionale** (`do ... while` in C), in cui la condizione è valutata *dopo* il corpo: il corpo viene eseguito **almeno una volta**. Il teorema di Böhm-Jacopini richiede solo l'esistenza di una struttura iterativa; entrambe le varianti sono espressioni equivalenti dello stesso concetto di ciclo.

