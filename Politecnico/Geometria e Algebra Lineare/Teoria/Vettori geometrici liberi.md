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
3. hanno lo stesso **verso**: $B_1$ e $B_2$ sono contenuti nello **stesso semipiano** rispetto alla retta $A_1A_2$ (nel caso in cui le due rette $A_1B_1$ e $A_2B_2$ siano distinte; se coincidono, il verso è quello della stessa orientazione sulla retta).

Nello **spazio** (3D) la definizione è analoga: le rette $A_1B_1$ e $A_2B_2$ giacciono in uno stesso piano (se sono parallele e distinte) e si applica la stessa condizione sul semipiano di tale piano.

Si tratta di una **relazione di equivalenza** (riflessiva, simmetrica, transitiva): è riflessiva e simmetrica in modo ovvio, e transitiva perché lunghezza, direzione e verso uguali a quelli di un terzo segmento sono uguali tra loro. Equivalentemente, $\overrightarrow{A_1B_1}$ e $\overrightarrow{A_2B_2}$ sono equivalenti se e solo se $A_1B_1B_2A_2$ è un parallelogramma (eventualmente degenere).

> **Vettore libero.** Un **vettore (libero)** $\vec v$ è una **classe di equivalenza** di segmenti orientati. Ogni segmento della classe è un **rappresentante** di $\vec v$, e si scrive $\vec v=\overrightarrow{AB}$. Il punto di applicazione non conta: contano solo lunghezza, direzione e verso.

**Notazione.** In stampa i vettori liberi si indicano con lettere latine minuscole in grassetto ($\mathbf a,\mathbf u,\mathbf v,\dots$); a mano si usa la freccia sopra ($\vec a,\vec u,\vec v$). La scrittura $\vec v=\overrightarrow{AB}$ significa che il vettore $\vec v$ è la classe di equivalenza del segmento orientato $\overrightarrow{AB}$, cioè l'insieme di tutti i segmenti orientati equivalenti ad $\overrightarrow{AB}$; in tal caso si dice che $\vec v$ è **rappresentato** dal segmento orientato $\overrightarrow{AB}$.

Il **vettore nullo** $\vec 0$ è rappresentato da un qualunque segmento orientato con punto iniziale e finale coincidenti ($\overrightarrow{AA}$, per ogni $A$); ha lunghezza $0$ e **non ammette né direzione né verso**.

**Coerenza con la fisica.** Una grandezza vettoriale (forza, spostamento, velocità, accelerazione) è caratterizzata da direzione, verso e intensità (modulo), proprio come i vettori liberi: la definizione è quindi quella richiesta dalle applicazioni fisiche.

### Esistenza e unicità del rappresentante in un punto

> **Proprietà.** Dati un punto $A$ e un vettore $\vec v$, esiste **un unico** punto $B$ tale che $\vec v=\overrightarrow{AB}$.
> (Cioè: esiste un unico segmento orientato applicato in $A$ che rappresenta $\vec v$.)

*Giustificazione.* Basta riportare da $A$, nella direzione e verso di $\vec v$, un segmento di lunghezza $|\vec v|$: il suo estremo è $B$. Altri punti darebbero lunghezza, direzione o verso diversi.

### Traslazioni

Questa proprietà permette di definire la **traslazione** di vettore $\vec v$: la funzione $\tau_{\vec v}$ che a ogni punto $A$ associa l'unico punto $B$ con $\overrightarrow{AB}=\vec v$:

$$
\tau_{\vec v}(A) := B \iff \overrightarrow{AB}=\vec v .
$$

**Corrispondenza biunivoca vettori-traslazioni.** Ogni vettore libero $\vec v$ definisce una traslazione $\tau_{\vec v}$ e, viceversa, per ogni traslazione $\tau$ esiste **un unico** vettore $\vec v$ tale che $\tau=\tau_{\vec v}$ (basta prendere il vettore rappresentato da $\overrightarrow{A\tau(A)}$, che per definizione non dipende da $A$). Perciò un modo alternativo di introdurre i vettori liberi è **identificarli con le traslazioni**. Le traslazioni sono applicazioni biiettive del piano (o spazio) in sé, con $\tau_{\vec v}^{-1}=\tau_{-\vec v}$: si veda [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni (terminologia generale).md|Applicazioni (terminologia generale)]].

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

In termini di traslazioni: $A\mapsto B=\tau_{\vec u}(A)\mapsto C=\tau_{\vec v}(B)$, quindi **la somma di vettori corrisponde alla composizione delle traslazioni**: $\tau_{\vec u+\vec v}=\tau_{\vec v}\circ\tau_{\vec u}$.

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

**Unicità dell'opposto.** Il vettore libero rappresentato da $\overrightarrow{BA}$ non dipende dal segmento scelto per rappresentare $\vec v$: se $\overrightarrow{A_1B_1}$ è equivalente a $\overrightarrow{AB}$, allora $\overrightarrow{B_1A_1}$ è equivalente a $\overrightarrow{BA}$ (stessa lunghezza, direzione parallela, verso opposto per entrambe). Inoltre $\vec u:=-\vec v$ è l'**unico** vettore tale che $\vec v+\vec u=\vec 0$ (dimostrazione sotto, dopo la differenza).

### Differenza

Dati $\vec u,\vec v$, fissato un punto $A$ si pongono $B:=\tau_{\vec v}(A)$ e $C:=\tau_{\vec u}(A)$ (**stessa origine** $A$). Il vettore $\vec w$ rappresentato da $\overrightarrow{BC}$ **non dipende dalla scelta di $A$** e si chiama la **differenza** $\vec u-\vec v$: è il vettore che va dalla punta di $\vec v$ alla punta di $\vec u$.

Equivalentemente la **differenza** $\vec w-\vec v$ è il vettore $\vec u$ che sommato a $\vec v$ dà $\vec w$: $\vec v+\vec u=\vec w$. Geometricamente, se $\vec v=\overrightarrow{AB}$ e $\vec w=\overrightarrow{AC}$ (stessa origine), allora $\vec w-\vec v=\overrightarrow{BC}$ (il vettore che va dalla punta di $\vec v$ alla punta di $\vec w$). Valgono

$$
\vec v+(\vec w-\vec v)=\vec w,\qquad -\vec v+\vec w=\vec w-\vec v,
$$

e in generale la differenza è la somma con l'opposto: $\vec w-\vec v=\vec w+(-\vec v)$.

Dalle definizioni precedenti segue, per ogni $\vec u,\vec v$:

$$
\vec v+(\vec u-\vec v)=\vec u\quad(1),\qquad -\vec v+\vec u=\vec u-\vec v\quad(2).
$$

**Dimostrazione dell'unicità dell'opposto** (se $\vec v+\vec u=\vec 0$ allora $\vec u=-\vec v$). Poiché $\vec v=-(-\vec v)$, sostituendo $\vec v$ con $-\vec v$ in (2):

$$
\vec 0=\vec v+\vec u=-(-\vec v)+\vec u\overset{(2)}{=}\vec u-(-\vec v).
$$

Sommando $-\vec v$ a entrambi i lati: il lato destro è $-\vec v+\vec 0=-\vec v$; il lato sinistro, sostituendo $\vec v$ con $-\vec v$ in (1), è $-\vec v+(\vec u-(-\vec v))=\vec u$. Dunque $\vec u=-\vec v$. $\blacksquare$

### Moltiplicazione per uno scalare

Sia $\lambda\in\mathbb R$ e $\vec v=\overrightarrow{AB}\ne\vec 0$. Il vettore $\lambda\vec v$ si definisce così:

Formalmente: dati un vettore libero $\vec v$ e $\lambda\in\mathbb R$ (**scalare**), si fissa un punto $A$ e si pone $B:=\tau_{\vec v}(A)$ (cioè $\vec v=\overrightarrow{AB}$). Due casi.

**Caso 1: $\vec v\ne\vec 0$ (quindi $B\ne A$) e $\lambda\ne0$.** Si considera l'unico punto $C$ tale che:

1. $C$ appartiene alla retta $AB$;
2. $|\overrightarrow{AC}|=|\lambda|\,|\overrightarrow{AB}|$;
3. se $\lambda>0$, $C$ appartiene alla **semiretta** $AB$ (uscente da $A$ e passante per $B$);
4. se $\lambda<0$, $C$ appartiene alla semiretta **complementare** a quella $AB$ (opposta rispetto ad $A$).

Il vettore rappresentato da $\overrightarrow{AC}$ **non dipende dalla scelta di $A$** e si chiama il **prodotto di $\vec v$ per lo scalare $\lambda$**, indicato $\lambda\vec v$.

**Caso 2: $\vec v=\vec 0$ oppure $\lambda=0$** (o entrambi): per definizione $\lambda\vec v:=\vec 0$.

In sintesi:

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
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni (terminologia generale).md|Applicazioni (terminologia generale)]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]]
- [[Politecnico/Geometria e Algebra Lineare/Esercizi/Vettori, spazi vettoriali, sottospazi e applicazioni — Esercizi svolti.md|Esercizi — Vettori, spazi vettoriali, sottospazi e applicazioni]]
