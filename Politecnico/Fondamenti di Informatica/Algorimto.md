## Algoritmo
Un algoritmo si basa su due nozioni:
- **problema**
- **esecutore**
## Problema
Un problema è composto da una terna **(I, O, R)**:
- **I** — ingresso (input): deve soddisfare alcune condizioni di validità
- **O** — uscita (output): deve soddisfare alcune condizioni di validità
- **R** — relazione: deve essere soddisfatta per qualunque insieme di dati valido, tra dati in ingresso e risultati in uscita
### Esempio: Massimo tra due numeri naturali 
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
Un sistema capace di eseguire in modo deterministico ciascun passo elementare appartenente a un insieme (esiguo) di passi elementari
### Esempio
insimei di passi elementari eseguibili:
- acquisizione dei dati ("Lettura")
- produzione dei risultati ("scrittura")
- addizione di due numeri 
- sottrazione fra due numeri
- confronto fra due numeri (calcolo dell'esisto "vero" o "falso" di un confronto)
## Algoritmo
dati un problema P e un esecutore E, e una combinazione finita di passi elemntari, ciascuno eseguibile dall'esecutore E, in grado di risolvere il problema P (cioe per qualunque insime valido di dati in ingresso, produce in unscita risultati validi che soddisfano la relazione specifica con dati n ingresso)

### Esempio: l'oppsoto di un intero
1. acuisici un intero
2. sottrai dal valore 0 il valore del numero aquisito
3. produci in unscita il risultato della sottrazione
4. TERMINA

### Esempio: massimo tra due numeri naturali
I: due numeri interi d_1 e d_2
O: un numero naturale
R: $ r \\E  {d_1, d_2}$
	$ $
1. aquisitsci 2 numeri natruali
2. contfronto i valori 
3. confronto i  2 numeri naturali
	1. se il primo e maggiore del secondo torno il primo
	2. se il secondo e maggiore dle primo torno il secodno 
4. TERMINA

## 