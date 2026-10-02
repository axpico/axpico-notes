---
tags:
  - geometria-algebra-lineare
  - vettori
  - geometria-euclidea
---
## Vettori geometrici liberi

Nella geometria euclidea (piano o spazio) un vettore si introduce in due passi: prima i **segmenti orientati**, poi una **relazione di equivalenza** che identifica quelli "uguali a meno di spostamento". Il risultato è il concetto di **vettore libero**, che è l'oggetto geometrico di cui $\mathbb R^2,\mathbb R^3$ sono il modello in coordinate (si veda [[Politecnico/Geometria e Algebra Lineare/Teoria/Insiemi, vettori e sistemi lineari — nozioni di base.md|Insiemi, vettori e sistemi lineari — nozioni di base]]).

### Segmenti orientati

Un **segmento orientato** $\overrightarrow{AB}$ (vettore applicato in $A$) è una **coppia ordinata** $(A,B)$ di punti: $A$ è il punto iniziale (di applicazione), $B$ quello finale. Ha:

- una **lunghezza** (modulo) $|\overrightarrow{AB}|$ = distanza tra $A$ e $B$;
- una **direzione**: la retta per $A$ e $B$ (a meno di parallelismo);
- un **verso**: da $A$ verso $B$.

Se $A=B$ i due punti coincidono: il segmento è degenere e si parla di **vettore nullo**.

### Equivalenza tra segmenti orientati

Due segmenti orientati $\overrightarrow{A_1B_1}$ e $\overrightarrow{A_2B_2}$ nel piano (o spazio) euclideo si dicono **equivalenti** se:

1. hanno la stessa **lunghezza**: $|\overrightarrow{A_1B_1}| = |\overrightarrow{A_2B_2}|$;
2. hanno la stessa **direzione**: le rette $A_1B_1$ e $A_2B_2$ sono parallele (o coincidono): $A_1B_1\parallel A_2B_2$;
3. hanno lo stesso **verso**.

Si tratta di una **relazione di equivalenza** (riflessiva, simmetrica, transitiva): è riflessiva e simmetrica in modo ovvio, e transitiva perché lunghezza, direzione e verso uguali a quelli di un terzo segmento sono uguali tra loro. Equivalentemente, $\overrightarrow{A_1B_1}$ e $\overrightarrow{A_2B_2}$ sono equivalenti se e solo se $A_1B_1B_2A_2$ è un parallelogramma (eventualmente degenere).

> **Vettore libero.** Un **vettore (libero)** $\vec v$ è una **classe di equivalenza** di segmenti orientati. Ogni segmento della classe è un **rappresentante** di $\vec v$, e si scrive $\vec v=\overrightarrow{AB}$. Il punto di applicazione non conta: contano solo lunghezza, direzione e verso.

Il **vettore nullo** $\vec 0$ è rappresentato da un qualunque segmento orientato con punto iniziale e finale coincidenti ($\overrightarrow{AA}$, per ogni $A$); ha lunghezza $0$ e direzione/verso non definiti.

### Esistenza e unicità del rappresentante in un punto

> **Proprietà.** Dati un punto $A$ e un vettore $\vec v$, esiste **un unico** punto $B$ tale che $\vec v=\overrightarrow{AB}$.
> (Cioè: esiste un unico segmento orientato applicato in $A$ che rappresenta $\vec v$.)

*Giustificazione.* Basta riportare da $A$, nella direzione e verso di $\vec v$, un segmento di lunghezza $|\vec v|$: il suo estremo è $B$. Altri punti darebbero lunghezza, direzione o verso diversi.

### Traslazioni

Questa proprietà permette di definire la **traslazione** di vettore $\vec v$: la funzione $\tau_{\vec v}$ che a ogni punto $A$ associa l'unico punto $B$ con $\overrightarrow{AB}=\vec v$:

$$
\tau_{\vec v}(A) := B \iff \overrightarrow{AB}=\vec v .
$$

In generale una traslazione (del piano o dello spazio euclideo) è una trasformazione tale che, per ogni coppia di punti $A_1,A_2$, i segmenti orientati $\overrightarrow{A_1\,\tau(A_1)}$ e $\overrightarrow{A_2\,\tau(A_2)}$ sono **equivalenti tra loro**: tutti i punti vengono spostati dello stesso vettore.

### Somma di vettori

Dati due vettori liberi $\vec u,\vec v$, fissiamo un punto $A$ e poniamo

$$
B:=\tau_{\vec u}(A),\qquad C:=\tau_{\vec v}(B).
$$

Cioè $\vec u=\overrightarrow{AB}$ e $\vec v=\overrightarrow{BC}$ (secondo segmento "in coda" al primo). Si definisce $\vec u+\vec v$ come il vettore $\vec w$ rappresentato dal segmento orientato $\overrightarrow{AC}$:

$$
\overrightarrow{AB}+\overrightarrow{BC}=\overrightarrow{AC}\qquad\text{(regola del triangolo)}.
$$

**Buona definizione.** Il risultato **non dipende dalla scelta di $A$**: scegliendo un altro punto $A'$ si ottiene un triangolo $A'B'C'$ ottenuto da $ABC$ per traslazione, quindi $\overrightarrow{A'C'}$ è equivalente a $\overrightarrow{AC}$ e rappresenta lo stesso vettore libero. (È proprio qui che serve passare dai segmenti ai vettori liberi.)

**Regola del parallelogramma.** Applicando $\vec u$ e $\vec v$ nello stesso punto $A$ e completando il parallelogramma, la diagonale uscente da $A$ rappresenta $\vec u+\vec v$. Poiché la stessa diagonale si ottiene scambiando i ruoli di $\vec u$ e $\vec v$,

$$
\vec u+\vec v=\vec v+\vec u\qquad\text{(commutatività)}.
$$

**Elemento neutro.**

$$
\vec u+\vec 0=\vec 0+\vec u=\vec u .
$$

(Segue dalla regola del triangolo con $B=C$ oppure $A=B$.) L'associatività $(\vec u+\vec v)+\vec w=\vec u+(\vec v+\vec w)$ si vede accodando tre segmenti $\overrightarrow{AB},\overrightarrow{BC},\overrightarrow{CD}$: entrambi i membri sono rappresentati da $\overrightarrow{AD}$.

### Vettore opposto

Per ogni $\vec v=\overrightarrow{AB}$ il **vettore opposto** è $-\vec v:=\overrightarrow{BA}$ (stessa lunghezza e direzione, verso contrario), e vale

$$
\vec v+(-\vec v)=\vec 0,\qquad\text{cioè}\qquad \overrightarrow{AB}+\overrightarrow{BA}=\overrightarrow{AA}=\vec 0 .
$$

### Differenza

La **differenza** $\vec w-\vec v$ è il vettore $\vec u$ che sommato a $\vec v$ dà $\vec w$: $\vec v+\vec u=\vec w$. Geometricamente, se $\vec v=\overrightarrow{AB}$ e $\vec w=\overrightarrow{AC}$ (stessa origine), allora $\vec w-\vec v=\overrightarrow{BC}$ (il vettore che va dalla punta di $\vec v$ alla punta di $\vec w$). Valgono

$$
\vec v+(\vec w-\vec v)=\vec w,\qquad -\vec v+\vec w=\vec w-\vec v,
$$

e in generale la differenza è la somma con l'opposto: $\vec w-\vec v=\vec w+(-\vec v)$.

### Moltiplicazione per uno scalare

Sia $\lambda\in\mathbb R$ e $\vec v=\overrightarrow{AB}\ne\vec 0$. Il vettore $\lambda\vec v$ si definisce così:

- se $\lambda>0$: stessa direzione **e stesso verso** di $\vec v$, lunghezza moltiplicata per $\lambda$ (si "allunga" o "accorcia");
- se $\lambda<0$: stessa direzione, **verso opposto**, lunghezza moltiplicata per $|\lambda|$;
- in ogni caso $|\lambda\vec v|=|\lambda|\,|\vec v|$; in particolare, se $\overrightarrow{AC}=\lambda\overrightarrow{AB}$, allora $|\overrightarrow{AC}|=|\lambda|\,|\overrightarrow{AB}|$ e $A,B,C$ sono **allineati**;
- se $\vec v=\vec 0$ **oppure** $\lambda=0$: $\lambda\vec v=\vec 0$.

Notare che $(-1)\vec v=-\vec v$ e $1\cdot\vec v=\vec v$.

### Perché è importante

Somma e prodotto per scalare di vettori liberi soddisfano le stesse proprietà algebriche delle operazioni su $\mathbb R^n$ e delle matrici. Estrarre tali proprietà e prenderle come definizione porta al concetto astratto di **spazio vettoriale**: si veda [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]].

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Insiemi, vettori e sistemi lineari — nozioni di base.md|Insiemi, vettori e sistemi lineari — nozioni di base]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]]
