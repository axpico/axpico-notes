# Programma (esecuzione di un algoritmo)

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

## Linguaggi ad alto livello (es. C)
Il **C** è un linguaggio ad alto livello, indipendente dalla macchina, che permette di:
- calcolare e memorizzare valori in memoria;
- estrarre valori dalla memoria;
- leggere dati in ingresso e stampare risultati in uscita;
- eseguire selezioni (if/else) e cicli (for/while).

Per eseguire un programma scritto in un linguaggio ad alto livello è necessario un **compilatore**, che lo traduce nell'opportuno linguaggio macchina.

## Macchina virtuale C
Esecutore considerato: la **macchina virtuale C**. Un **bus** trasporta le informazioni tra le sue unità.

**RAM**
- in C, per distinguere un contenitore (variabile) si usa un nome;
- è comunque possibile usare direttamente l'indirizzo.

**CPU** (*central processing unit*)
- esegue le istruzioni del programma.

**Standard Input**
- unità di ingresso.

**Standard Output**
- unità di uscita.

Standard Input e Output sono utilizzati dal programma per interagire con l'utente.

**Differenza tra macchina di Von Neumann e macchina virtuale C**
- nella macchina virtuale si ignora dove risiedono fisicamente i programmi in memoria;
- si considera comunque presente un'area di memoria riservata al programma da eseguire.

## Introduzione al C 