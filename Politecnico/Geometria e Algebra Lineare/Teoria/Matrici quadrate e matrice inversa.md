---
tags:
  - geometria-algebra-lineare
  - matrici
  - matrice-inversa
  - algebra-lineare
---
## Matrici quadrate e matrice inversa

### Definizioni di base

- Una matrice $A$ si dice **quadrata** se $\#\text{righe in } A = \#\text{colonne in } A$.
- Una matrice quadrata $n\times n$ si dice **di ordine $n$**.
- Una matrice **diagonale** è una matrice quadrata i cui elementi fuori dalla diagonale principale sono tutti nulli:

$$
\operatorname{diag}(\lambda_1,\lambda_2,\dots,\lambda_n) := \begin{bmatrix} \lambda_1 & 0 & \cdots & 0\\ 0 & \lambda_2 & \cdots & 0\\ \vdots & & \ddots & \vdots\\ 0 & 0 & \cdots & \lambda_n\end{bmatrix}
$$

- La **matrice identità** di ordine $n$ è la matrice diagonale con tutti $1$ sulla diagonale:

$$
I_n := \operatorname{diag}(\underbrace{1,1,\dots,1}_{n\ \text{volte}}) = \begin{bmatrix} 1 & 0 & \cdots & 0\\ 0 & 1 & \cdots & 0\\ \vdots & & \ddots & \vdots\\ 0 & 0 & \cdots & 1\end{bmatrix}.
$$

### Prodotto per una matrice diagonale

Moltiplicare $A$ **a destra** per una matrice diagonale riscala le **colonne** di $A$: se $A_j$ indica la $j$-esima colonna di $A$,

$$
A\cdot\operatorname{diag}(\lambda_1,\dots,\lambda_n) = \big[\ \lambda_1 A_1 \ \ \lambda_2 A_2\ \ \cdots\ \ \lambda_n A_n\ \big],
$$

perché $A\begin{bmatrix}\lambda_i\\0\\\vdots\\0\end{bmatrix}$ (con $\lambda_i$ nella posizione $i$) seleziona e riscala esattamente la colonna $i$ di $A$.

Moltiplicare a **sinistra** per una diagonale, invece, riscala le **righe**. Lo si dimostra usando la formula per la trasposta di un prodotto, $(CB)^{\mathsf T} = B^{\mathsf T}C^{\mathsf T}$, e il fatto che una matrice diagonale è **simmetrica** ($\operatorname{diag}(\lambda_1,\dots,\lambda_n)^{\mathsf T} = \operatorname{diag}(\lambda_1,\dots,\lambda_n)$):

$$
\big[\operatorname{diag}(\lambda_1,\dots,\lambda_n)\,B\big]^{\mathsf T} = B^{\mathsf T}\operatorname{diag}(\lambda_1,\dots,\lambda_n)^{\mathsf T} = B^{\mathsf T}\operatorname{diag}(\lambda_1,\dots,\lambda_n),
$$

che per il punto precedente riscala le colonne di $B^{\mathsf T}$ (cioè le righe di $B$) di $\lambda_1,\dots,\lambda_n$; trasponendo di nuovo si ottiene $\operatorname{diag}(\lambda_1,\dots,\lambda_n)B$ con la riga $i$ di $B$ moltiplicata per $\lambda_i$.

**Caso particolare** $\lambda_1=\cdots=\lambda_n=1$ (cioè la diagonale è $I_n$): riscalare per $1$ non cambia nulla, quindi

$$
A\,I_n = A, \qquad I_n\,B = B,
$$

in perfetta analogia con $a\cdot 1 = 1\cdot a = a$ per gli scalari. Più in generale, per ogni matrice quadrata $A$ di ordine $n$: $AI_n = I_nA = A$.

### Matrice inversa

**Definizione.** Siano $A$ e $B$ due matrici quadrate di ordine $n$. $B$ si dice **inversa** di $A$ se

$$
AB = BA = I_n.
$$

### Teorema 3 (unicità dell'inversa)

*Ogni matrice quadrata ammette al più un'inversa.*

**Dimostrazione.** Sia $A$ di ordine $n$ e siano $B_1, B_2$ entrambe inverse di $A$, cioè

$$
AB_1 = B_1A = AB_2 = B_2A = I_n.
$$

Calcoliamo $(B_2A)B_1$ in due modi.

Da un lato, poiché $B_2A = I_n$:

$$
(B_2A)B_1 = I_n B_1 = B_1.
$$

Dall'altro, per la proprietà **associativa** del prodotto tra matrici e poiché $AB_1=I_n$:

$$
(B_2A)B_1 = B_2(AB_1) = B_2 I_n = B_2.
$$

Confrontando le due espressioni: $B_1 = B_2$. $\blacksquare$

Grazie a questo teorema ha senso parlare de **l'**inversa di $A$ (se esiste), indicata con $A^{-1}$.

**Definizione.** Una matrice quadrata $A$ si dice **invertibile** (o **non singolare**) se ammette l'inversa. Altrimenti $A$ si dice **singolare** (o **non invertibile**).

### Teorema 4 (condizioni di invertibilità)

Sia $A$ una matrice quadrata di ordine $n$. Le seguenti condizioni sono equivalenti fra loro:

(i) $A$ è invertibile;
(ii) esiste una matrice $B$ tale che $AB = I_n$ ($B$ è un'**inversa destra**);
(iii) esiste una matrice $C$ tale che $CA = I_n$ ($C$ è un'**inversa sinistra**);
(iv) il rango di $A$ è massimo: $r(A) = n$;
(v) per ogni $b\in\mathbb R^n$ il sistema lineare $Ax=b$ ammette una e una sola soluzione;
(vi) il sistema omogeneo $Ax=0$ ammette **solo** la soluzione banale $x=0$;
(vii) esiste almeno un $b\in\mathbb R^n$ tale che il sistema lineare $Ax=b$ ammette un'unica soluzione.

> Nell'appunto originale la dimostrazione è solo citata per numero di pagina (43-45) e non riportata per esteso; qui viene ricostruita in modo completo, seguendo lo schema logico indicato: $(\mathrm{iv})\Rightarrow(\mathrm v)\Leftrightarrow(\mathrm{vi})\Rightarrow(\mathrm{vii})\Rightarrow(\mathrm v)$, chiuso poi con $(\mathrm i)\Rightarrow(\mathrm{ii}),(\mathrm{iii})\Rightarrow(\mathrm{iv})\Rightarrow(\mathrm i)$.

**Dimostrazione (schema completo).**

- **(i) $\Rightarrow$ (ii) e (iii).** Se $A$ è invertibile esiste $A^{-1}$ con $AA^{-1}=A^{-1}A=I_n$: basta prendere $B=C=A^{-1}$

- **(ii) $\Rightarrow$ (iv).** Se esiste $B$ con $AB=I_n$, dalla teoria del rango del prodotto tra matrici si ha $r(AB) \le r(A)$ (moltiplicare non può far *aumentare* il rango). Ma $r(AB)=r(I_n)=n$, quindi $n \le r(A)$; d'altra parte $r(A)\le n$ sempre. Dunque $r(A)=n$.

- **(iii) $\Rightarrow$ (iv).** Analogo, usando $CA=I_n$ e $r(CA)\le r(A)$.

- **(iv) $\Rightarrow$ (v).** Se $r(A)=n$, per il Teorema di Cramer ogni sistema $Ax=b$ ammette un'unica soluzione, qualunque sia $b$.

- **(v) $\Leftrightarrow$ (vi).** Il sistema omogeneo $Ax=0$ è il caso particolare $b=0$ di (v): se (v) vale per ogni $b$, vale in particolare per $b=0$, e poiché $x=0$ è sempre soluzione, è **l'unica**, cioè (vi). Viceversa, se vale (vi) allora $r(A)=n$ (l'unicità della soluzione nel Teorema di Rouché-Capelli richiede $n=r$), e quindi per Cramer vale (v).

- **(vi) $\Rightarrow$ (vii).** Basta prendere $b=0$: per (vi) il sistema $Ax=0$ ammette un'unica soluzione, quindi esiste (almeno) un $b$ — cioè $b=0$ — con questa proprietà.

- **(vii) $\Rightarrow$ (v).** Se **un** particolare $b$ dà soluzione unica, allora per Rouché-Capelli $n=r(A)$ (l'unicità richiede sempre $n=r$, indipendentemente da quale $b$ si sia scelto, perché $r(A)$ non dipende da $b$). Ma allora $r(A)=n$, e per Cramer (v) vale per **ogni** $b$.

- **(iv) $\Rightarrow$ (i)** *(chiude il ciclo con (ii)-(iii))*. Se $r(A)=n$, riducendo $A$ a scalini con operazioni elementari (equivalenti a moltiplicare a sinistra per matrici invertibili $E_1,\dots,E_k$) si ottiene $E_k\cdots E_1 A = I_n$: quindi $B:=E_k\cdots E_1$ soddisfa $BA=I_n$. Si dimostra (con un argomento analogo, o applicando quanto già provato a $B$) che questa stessa $B$ soddisfa anche $AB=I_n$: dunque $B=A^{-1}$ e $A$ è invertibile.

Questo chiude la catena di equivalenze: (i) $\Leftrightarrow$ (ii) $\Leftrightarrow$ (iii) $\Leftrightarrow$ (iv) $\Leftrightarrow$ (v) $\Leftrightarrow$ (vi) $\Leftrightarrow$ (vii). $\blacksquare$

**Osservazione.** Il punto più utile in pratica è che per una matrice **quadrata** basta un'inversa **da un solo lato** (destra o sinistra) per concludere che $A$ è invertibile a tutti gli effetti (e che quell'inversa unilaterale coincide con $A^{-1}$). Questo **non** vale per matrici non quadrate.

### Dimostrazione diretta ed elementare di (i) $\Rightarrow$ (v) $\Rightarrow$ (ii)

Oltre allo schema "ciclico" sopra (che passa per il rango), esiste una dimostrazione diretta e molto concreta di questi due passaggi, utile perché non richiede il Teorema di Cramer: è quella riportata negli appunti a mano e ricostruita qui per esteso.

**(i) $\Rightarrow$ (v).** Supponiamo $A$ invertibile, con inversa $A^{-1}$. Fissato un qualsiasi $b\in\mathbb R^n$, mostriamo che $Ax=b$ ammette **esattamente una** soluzione.

*Esistenza.* Poniamo $x := A^{-1}b$. Allora, per l'associatività del prodotto tra matrici,

$$
Ax = A(A^{-1}b) = (AA^{-1})b = I_n b = b,
$$

quindi $x=A^{-1}b$ è effettivamente una soluzione.

*Unicità.* Sia $x$ una soluzione qualunque, cioè $Ax=b$. Moltiplicando **a sinistra** entrambi i membri per $A^{-1}$:

$$
A^{-1}(Ax) = A^{-1}b \quad\overset{\text{associativa}}{\Longrightarrow}\quad (A^{-1}A)x = A^{-1}b \quad\Longrightarrow\quad I_n x = A^{-1}b \quad\Longrightarrow\quad x = A^{-1}b.
$$

Ogni soluzione coincide quindi con $A^{-1}b$: la soluzione è unica. $\blacksquare$

**(v) $\Rightarrow$ (ii).** Supponiamo che per ogni $b\in\mathbb R^n$ il sistema $Ax=b$ ammetta un'unica soluzione. Vogliamo costruire esplicitamente una matrice $B$ con $AB=I_n$.

Siano $e_1,\dots,e_n\in\mathbb R^n$ le colonne della matrice identità, cioè

$$
e_1 = \begin{bmatrix}1\\0\\\vdots\\0\end{bmatrix},\quad e_2 = \begin{bmatrix}0\\1\\\vdots\\0\end{bmatrix},\quad \dots,\quad e_n = \begin{bmatrix}0\\0\\\vdots\\1\end{bmatrix}.
$$

Per ipotesi (v), per ogni $j=1,\dots,n$ il sistema $Ax = e_j$ ammette un'(unica) soluzione: chiamiamola $u_j$. Costruiamo la matrice $B$ affiancando queste soluzioni come colonne:

$$
B := \big[\, u_1 \mid u_2 \mid \cdots \mid u_n \,\big].
$$

Allora, usando che moltiplicare $A$ per una matrice equivale a moltiplicare $A$ per ciascuna colonna separatamente,

$$
AB = \big[\, Au_1 \mid Au_2 \mid \cdots \mid Au_n \,\big] = \big[\, e_1 \mid e_2 \mid \cdots \mid e_n \,\big] = I_n.
$$

Dunque $B$ è un'inversa destra di $A$, cioè vale (ii). $\blacksquare$

> Questa costruzione è anche la giustificazione teorica del metodo pratico per calcolare $A^{-1}$: risolvere gli $n$ sistemi $Ax=e_j$ (uno per ogni colonna di $I_n$) equivale esattamente a fare l'eliminazione di Gauss-Jordan sulla matrice orlata $[A\mid I_n]$ — si veda [[Politecnico/Geometria e Algebra Lineare/Teoria/Eliminazione di Gauss-Jordan e calcolo della matrice inversa.md|Eliminazione di Gauss-Jordan e calcolo della matrice inversa]].

### Teorema 5 (formula esplicita dell'inversa $2\times 2$)

Una matrice $2\times 2$

$$
A = \begin{bmatrix} a & b\\ c & d\end{bmatrix}
$$

è **invertibile se e solo se** $ad-bc \ne 0$, e in tal caso

$$
A^{-1} = \frac{1}{ad-bc}\begin{bmatrix} d & -b\\ -c & a\end{bmatrix}.
$$

**Verifica.** Basta controllare che $AA^{-1}=I_2$ (e analogamente $A^{-1}A=I_2$):

$$
A\cdot\frac{1}{ad-bc}\begin{bmatrix} d & -b\\ -c & a\end{bmatrix} = \frac{1}{ad-bc}\begin{bmatrix} ad-bc & -ab+ba\\ cd-dc & -cb+da\end{bmatrix} = \frac{1}{ad-bc}\begin{bmatrix} ad-bc & 0\\ 0 & ad-bc\end{bmatrix} = I_2.
$$

La quantità $ad-bc$ è il **determinante** di $A$ nel caso $2\times2$: la formula generalizza l'idea che una matrice è invertibile esattamente quando il suo "fattore di scala" non è nullo.

#### Esempio

Sia $A = \begin{bmatrix}1&2\\3&4\end{bmatrix}$. Allora $ad-bc = 1\cdot 4 - 2\cdot 3 = 4-6=-2 \ne 0$, quindi $A$ è invertibile e

$$
A^{-1} = \frac{1}{-2}\begin{bmatrix}4&-2\\-3&1\end{bmatrix} = \begin{bmatrix}-2&1\\ \tfrac32 & -\tfrac12\end{bmatrix}.
$$

(Verifica diretta: $AA^{-1}=I_2$, calcolo lasciato al lettore.)

### Esempio (invertibilità di una matrice triangolare)

Sia

$$
A = \begin{bmatrix} 1 & 0 & 1\\ 0 & 4 & 2\\ 0 & 0 & 7\end{bmatrix}.
$$

$A$ è già **a scala** (triangolare superiore) e ha tutti i pivot non nulli ($1,4,7$ sulla diagonale), quindi $r(A)=3=$ ordine di $A$: per il Teorema 4, punto (iv) $\Rightarrow$ (i), $A$ è **invertibile**. (Per il calcolo esplicito di $A^{-1}$ si veda [[Politecnico/Geometria e Algebra Lineare/Teoria/Eliminazione di Gauss-Jordan e calcolo della matrice inversa.md|Eliminazione di Gauss-Jordan e calcolo della matrice inversa]].)

> **Osservazione generale.** Una matrice triangolare (superiore o inferiore) è invertibile se e solo se tutti gli elementi sulla diagonale principale sono non nulli: infatti in tal caso la matrice è già a scala con $n$ pivot, cioè $r(A)=n$.

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari quadrati e teorema di Cramer.md|Sistemi lineari quadrati e teorema di Cramer]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Eliminazione di Gauss-Jordan e calcolo della matrice inversa.md|Eliminazione di Gauss-Jordan e calcolo della matrice inversa]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Equazioni matriciali.md|Equazioni matriciali]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Determinante, sviluppo di Laplace e formula di Cramer.md|Determinante, sviluppo di Laplace e formula di Cramer]]
