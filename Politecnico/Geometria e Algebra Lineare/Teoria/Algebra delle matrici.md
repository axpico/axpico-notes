---
tags:
  - geometria-algebra-lineare
  - matrici
  - algebra-lineare
---
## 1. Somma, differenza e prodotto per scalare

Siano $A = [a_{ij}]$ e $B = [b_{ij}]$ due matrici **della stessa dimensione** $m \times n$ (condizione necessaria: senza di essa somma e differenza non sono definite). Si possono sommare e sottrarre elemento per elemento:

$$
C = A \pm B \quad \iff \quad c_{ij} = a_{ij} \pm b_{ij}, \qquad i=1,\dots,m,\ j = 1,\dots,n
$$

Analogamente si definisce il **prodotto per uno scalare** $\lambda \in \mathbb{R}$:

$$
\lambda A := [\lambda\, a_{ij}]
$$

cioè si moltiplica ogni elemento della matrice per $\lambda$.

### Proprietà delle operazioni

Per ogni $A, B, C$ matrici $m\times n$ e $\lambda, \mu \in \mathbb{R}$:

1. **Commutativa**: $A + B = B + A$
2. **Associativa**: $(A+B)+C = A+(B+C)$
3. **Esistenza dell'elemento neutro**: esiste la matrice nulla $0$ (tutti elementi $0$) tale che $A + 0 = A$
4. **Esistenza dell'opposto**: $\forall A\ \exists!\, {-A}$ tale che $A + (-A) = 0$
5. **Distributiva rispetto alla somma di matrici**: $\lambda(A+B) = \lambda A + \lambda B$
6. **Distributiva rispetto alla somma di scalari**: $(\lambda+\mu)A = \lambda A + \mu A$
7. **Associativa mista**: $\lambda(\mu A) = (\lambda \mu) A$

> Le proprietà (v)-(vii) dell'appunto originale erano lasciate in bianco: sono le proprietà standard dello spazio vettoriale delle matrici $m\times n$ rispetto al prodotto per scalare, riportate sopra. Insieme, le proprietà 1-7 dicono che l'insieme delle matrici $m\times n$ con queste due operazioni forma uno **spazio vettoriale**.

Somma/sottrazione e prodotto per scalare richiedono che le matrici coinvolte abbiano **le stesse dimensioni** ("simili", nel linguaggio dell'appunto originale): non ha senso sommare una $2\times3$ con una $3\times2$.

## 2. Vettori come matrici riga/colonna

Dato $x := (x_1, x_2, \dots, x_n)$, gli si possono associare due matrici:

$$
\underbrace{[x_1\ x_2\ \cdots\ x_n]}_{\text{matrice riga } (1\times n)}
\qquad\qquad
\underbrace{\begin{bmatrix} x_1\\ x_2\\ \vdots\\ x_n\end{bmatrix}}_{\text{matrice colonna } (n\times 1)}
$$

Per convenzione, in algebra lineare **i vettori si identificano con le matrici colonna**. La matrice riga corrispondente si indica con il simbolo di trasposizione:

$$
x^{\mathsf T} = (x_1, x_2, \dots, x_n)
$$

### Trasposizione

**Definizione.** Data $A = [a_{ij}]$ di dimensione $m \times n$, la sua **trasposta** è la matrice $A^{\mathsf T} = [a'_{ij}]$ di dimensione $n\times m$ definita da

$$
a'_{ij} = a_{ji}
$$

cioè si scambiano righe e colonne (la riga $i$ di $A$ diventa la colonna $i$ di $A^{\mathsf T}$).

## 3. Prodotto riga per colonna

Dato un vettore riga $1\times n$ e un vettore colonna $n\times 1$ (stessa lunghezza $n$), si definisce:

$$
[a_1\ a_2\ \cdots\ a_n]
\begin{bmatrix} b_1\\ b_2\\ \vdots\\ b_n\end{bmatrix}
:= \sum_{i=1}^{n} a_i b_i = a_1 b_1 + a_2 b_2 + \cdots + a_n b_n
$$

Il risultato è uno **scalare** (matrice $1\times 1$): il prodotto riga per colonna altro non è che il **prodotto scalare** $a \cdot b$ tra i due vettori.

## 4. Prodotto matrice per vettore

Sia $A$ una matrice $m\times n$ e $b \in \mathbb{R}^n$ un vettore colonna. Il prodotto $Ab$ è il vettore colonna $c = (c_1,\dots,c_m)$ ottenuto moltiplicando ogni riga di $A$ per $b$:

$$
c_i = \sum_{j=1}^{n} a_{ij}\, b_j, \qquad i = 1,\dots,m
$$

(Condizione: il numero di colonne di $A$ deve coincidere con la lunghezza di $b$.)

## 5. Prodotto tra matrici — caso generale

Siano $A = [a_{ij}]$ di dimensione $m\times n$ e $B=[b_{ij}]$ di dimensione $n\times k$ (**il numero di colonne di $A$ deve essere uguale al numero di righe di $B$**). Il prodotto $AB$ è la matrice $C = [c_{ij}]$ di dimensione $m \times k$ definita da

$$
c_{ij} = \sum_{l=1}^{n} a_{il}\, b_{lj}, \qquad i=1,\dots,m,\ j=1,\dots,k
$$

cioè l'elemento $(i,j)$ di $C$ è il prodotto scalare tra la riga $i$ di $A$ e la colonna $j$ di $B$.

> **Condizione di compatibilità**: $AB$ è definito **solo se** (colonne di $A$) = (righe di $B$).

### Esempio numerico

$$
A = \begin{bmatrix} 1 & 2\\ 0 & -1\end{bmatrix}_{2\times 2}, \qquad
B = \begin{bmatrix} 3 & 1\\ 2 & 0\end{bmatrix}_{2\times 2}
$$

$$
AB = \begin{bmatrix} 1\cdot 3+2\cdot 2 & 1\cdot 1+2\cdot 0\\ 0\cdot 3+(-1)\cdot 2 & 0\cdot 1+(-1)\cdot 0\end{bmatrix}
= \begin{bmatrix} 7 & 1\\ -2 & 0\end{bmatrix}
$$

$$
BA = \begin{bmatrix} 3\cdot 1+1\cdot 0 & 3\cdot 2+1\cdot(-1)\\ 2\cdot 1+0\cdot 0 & 2\cdot 2+0\cdot(-1)\end{bmatrix}
= \begin{bmatrix} 3 & 5\\ 2 & 4\end{bmatrix}
$$

$AB \ne BA$: il prodotto tra matrici **non è commutativo**, nemmeno quando entrambe sono quadrate della stessa dimensione (come mostra l'esempio). Inoltre, in generale, se esiste $AB$ non è detto che esista $BA$ (basta che le dimensioni non siano compatibili nell'altro ordine).

### Proprietà del prodotto

Per $A,B,C$ di dimensioni compatibili e $\lambda \in \mathbb{R}$:

1. **Distributiva**: $(A+B)C = AC + BC$
2. **Associativa mista con lo scalare**: $(\lambda A)B = \lambda(AB) = A(\lambda B)$
3. **Associativa**: $(AB)C = A(BC)$
4. $AB \ne BA$ in generale (non commutativo)

## 6. Teorema di Rouché-Capelli

Un sistema lineare di $m$ equazioni in $n$ incognite

$$
\sum_{j=1}^{n} a_{ij}\, x_j = b_i, \qquad i = 1,\dots,m
$$

si scrive in forma matriciale come $Ax = b$, dove $A$ è la **matrice dei coefficienti** ($m\times n$), $x = (x_1,\dots,x_n)$ è il vettore delle incognite e $b$ il vettore dei termini noti.

### Esempio

$$
\begin{cases} 2x_1 + 3x_2 + x_3 = 5\\ x_1 + 5x_3 = 7 \end{cases}
\quad\Longleftrightarrow\quad
\begin{bmatrix} 2 & 3 & 1\\ 1 & 0 & 5\end{bmatrix}
\begin{bmatrix} x_1\\ x_2\\ x_3\end{bmatrix}
=
\begin{bmatrix} 5\\ 7\end{bmatrix}
$$

### Enunciato

Sia $Ax = b$ con $A$ matrice $m\times n$, $x = (x_1,\dots,x_n)$ le $n$ incognite. Sia $[A\,|\,b]$ la **matrice completa** (o orlata), ottenuta affiancando ad $A$ la colonna $b$.

**(a) Esistenza.** Il sistema ammette soluzione **se e solo se**

$$
r := \operatorname{rk}(A) = \operatorname{rk}([A\,|\,b])
$$

(il rango della matrice dei coefficienti coincide con il rango della matrice completa).

**(b) Struttura delle soluzioni**, supponendo che (a) sia soddisfatta:
- se $n = r$: la soluzione è **unica**;
- se $n > r$: esistono **infinite** soluzioni, dipendenti da $n-r$ parametri liberi; esistono $v_0, v_1,\dots,v_{n-r} \in \mathbb{R}^n$ tali che l'insieme delle soluzioni si scrive come
$$
v_0 + t_1 v_1 + \cdots + t_{n-r} v_{n-r}, \qquad t_1,\dots,t_{n-r}\in\mathbb{R}
$$
($v_0$ è una soluzione particolare, $v_1,\dots,v_{n-r}$ generano lo spazio delle soluzioni del sistema omogeneo associato).

**(c) Sistema omogeneo.** Se $Ax = 0$ (cioè $b = 0$), il sistema ammette **sempre** soluzione, perché $x=0$ la soddisfa banalmente. In particolare:
- se $n = r$: l'**unica** soluzione è $x=0$;
- se $n > r$: esistono **infinite** soluzioni dipendenti da $n-r$ parametri (lo spazio delle soluzioni ha dimensione $n-r$).

### Perché la struttura è $v_0 + t_1v_1 + \cdots + t_{n-r}v_{n-r}$

Questo è il punto lasciato solo accennato nell'appunto a mano: vediamo da dove viene.

Siano $x$ e $x'$ **due soluzioni qualsiasi** di $Ax=b$, cioè $Ax=b$ e $Ax'=b$. Definiamo il vettore differenza

$$
\tilde x := x' - x.
$$

Per la linearità del prodotto matrice-vettore (proprietà distributiva):

$$
A\tilde x = A(x'-x) = Ax' - Ax = b - b = 0.
$$

Quindi **la differenza fra due soluzioni qualsiasi di $Ax=b$ è sempre una soluzione del sistema omogeneo associato** $Ax=0$. In altre parole, l'insieme delle soluzioni di $Ax=b$ (quando non vuoto) è un'unica soluzione particolare **traslata** dell'insieme delle soluzioni di $Ax=0$ (il nucleo/kernel di $A$):

$$
\{x : Ax=b\} = x_{\text{part}} + \{\tilde x : A\tilde x = 0\}.
$$

Questo spiega la formula: $v_0$ è una soluzione particolare qualunque, e $v_1,\dots,v_{n-r}$ sono una base dello spazio delle soluzioni del sistema omogeneo (uno spazio di dimensione $n-r$, tante quante le variabili libere).

**Come si costruiscono in pratica $v_0, v_1,\dots,v_{n-r}$** (metodo usato nell'appunto):
1. Si riduce il sistema a scalini e si individuano le variabili **dipendenti** (quelle con pivot) e le variabili **libere** (le altre, che diventano i parametri $t_1,\dots,t_{n-r}$).
2. Si pone $v_0$ = soluzione ottenuta ponendo **tutte le variabili libere a zero** ($t_1=\cdots=t_{n-r}=0$).
3. Si pone $v_k$ (per $k=1,\dots,n-r$) = soluzione **del sistema omogeneo** ottenuta ponendo la $k$-esima variabile libera $=1$ e tutte le altre variabili libere $=0$.

Con questa costruzione, ogni combinazione $v_0 + t_1v_1+\cdots+t_{n-r}v_{n-r}$ risolve $Ax=b$ (verifica diretta per linearità), e viceversa ogni soluzione si ottiene così, perché i valori delle variabili libere determinano univocamente quelli delle variabili dipendenti.

#### Esempio (ripreso dal caso precedente)

Riprendiamo il sistema dell'esempio del Teorema di Rouché-Capelli:

$$
\begin{cases} 2x_1 + 3x_2 + x_3 = 5\\ x_1 + 5x_3 = 7 \end{cases}
$$

Qui $m=2$, $n=3$. La matrice dei coefficienti $A=\begin{bmatrix}2&3&1\\1&0&5\end{bmatrix}$ ha rango $r=2$ (le due righe non sono proporzionali), quindi $r(A)=r([A|b])=2$: il sistema è compatibile e ammette $n-r = 3-2=1$ parametro libero.

Dalla seconda equazione: $x_1 = 7-5x_3$. Sostituendo nella prima: $2(7-5x_3)+3x_2+x_3=5 \implies 3x_2 = -9+9x_3 \implies x_2 = -3+3x_3$.

Ponendo $x_3 = t$ (variabile libera):

$$
x = \begin{bmatrix}x_1\\x_2\\x_3\end{bmatrix} = \begin{bmatrix}7\\-3\\0\end{bmatrix} + t\begin{bmatrix}-5\\3\\1\end{bmatrix} = v_0 + t\,v_1.
$$

Verifica che $v_1$ risolve il sistema omogeneo $Ax=0$:

$$
Av_1 = \begin{bmatrix}2&3&1\\1&0&5\end{bmatrix}\begin{bmatrix}-5\\3\\1\end{bmatrix} = \begin{bmatrix}2(-5)+3(3)+1(1)\\1(-5)+0(3)+5(1)\end{bmatrix} = \begin{bmatrix}0\\0\end{bmatrix}. \checkmark
$$

## 7. Sistemi lineari quadrati e Teorema di Cramer

Un sistema lineare $Ax=b$ si dice **quadrato** quando il numero di incognite è uguale al numero di equazioni, cioè $A$ è una matrice $n \times n$ (di **ordine** $n$).

Per qualunque matrice $C$ vale sempre

$$
r(C) \le \min\{\#\text{colonne}, \#\text{righe}\};
$$

quando $C$ è quadrata di ordine $n$ e $r(C)=n$, si dice che $C$ ha **rango massimo**.

### Teorema (di Cramer)

Sia $Ax=b$ un sistema lineare quadrato di $n$ equazioni in $n$ incognite ($A$ di ordine $n$). Allora:

- **(i)** se $r(A) \ne n$: per alcuni $b\in\mathbb R^n$ il sistema $Ax=b$ **non ammette soluzione**, mentre per altri $b\in\mathbb R^n$ può ammetterne **infinite**;
- **(ii)** se $r(A) = n$: **per ogni** $b\in\mathbb R^n$ il sistema $Ax=b$ ammette **un'unica soluzione**.

### Dimostrazione: è un corollario di Rouché-Capelli

Per definizione di rango, aggiungere una colonna non può far diminuire il rango né superare il numero di righe:

$$
r(A) \le r([A\,|\,b]) \le \#\text{righe} = n.
$$

Se $r(A)=n$, dalla catena di disuguaglianze segue $n \ge r([A\,|\,b]) \ge r(A) = n$, cioè $r([A\,|\,b])=n$. Dunque $r(A) = r([A\,|\,b]) = n$: per Rouché-Capelli il sistema è compatibile, e poiché $n=r$ (numero di incognite = rango), la soluzione è **unica**. Questo prova (ii) (e, per differenza, (i): se $r(A)\ne n$ allora $r(A)<n$, e a seconda di $b$ si può avere $r([A|b])=r(A)$, infinite soluzioni, oppure $r([A|b])>r(A)$, nessuna soluzione).

Il Teorema di Cramer, quindi, non è un risultato indipendente: è semplicemente Rouché-Capelli **specializzato al caso quadrato**, dove "rango massimo" equivale a "$n=r$" in entrambe le condizioni (a) ed (b) del teorema generale. $\blacksquare$

### Esempio

$$
\begin{cases} x_1 + x_2 = b_1\\ x_1 - x_2 = b_2 \end{cases}
$$

ammette, per **ogni** $b_1,b_2\in\mathbb R$, un'unica soluzione:

$$
x_1 = \frac{b_1+b_2}{2}, \qquad x_2 = \frac{b_1-b_2}{2}.
$$

Infatti la matrice dei coefficienti $A = \begin{bmatrix}1&1\\1&-1\end{bmatrix}$ riduce a scalini a $\begin{bmatrix}1&1\\0&-2\end{bmatrix}$ (con $R_2 \to R_2 - R_1$), quindi $r(A)=2=$ ordine del sistema: per il Teorema di Cramer c'è sempre soluzione unica, qualunque sia il termine noto.

## 8. Matrici quadrate e matrice inversa

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

- **(i) $\Rightarrow$ (ii) e (iii).** Se $A$ è invertibile esiste $A^{-1}$ con $AA^{-1}=A^{-1}A=I_n$: basta prendere $B=C=A^{-1}$.

- **(ii) $\Rightarrow$ (iv).** Se esiste $B$ con $AB=I_n$, dalla teoria del rango del prodotto tra matrici si ha $r(AB) \le r(A)$ (moltiplicare non può far *aumentare* il rango). Ma $r(AB)=r(I_n)=n$, quindi $n \le r(A)$; d'altra parte $r(A)\le n$ sempre (Sezione 7). Dunque $r(A)=n$.

- **(iii) $\Rightarrow$ (iv).** Analogo, usando $CA=I_n$ e $r(CA)\le r(A)$.

- **(iv) $\Rightarrow$ (v).** Se $r(A)=n$, per il Teorema di Cramer (Sezione 7, punto (ii)) ogni sistema $Ax=b$ ammette un'unica soluzione, qualunque sia $b$.

- **(v) $\Leftrightarrow$ (vi).** Il sistema omogeneo $Ax=0$ è il caso particolare $b=0$ di (v): se (v) vale per ogni $b$, vale in particolare per $b=0$, e poiché $x=0$ è sempre soluzione, è **l'unica**, cioè (vi). Viceversa, se vale (vi) allora $r(A)=n$ (l'unicità della soluzione nel Teorema di Rouché-Capelli richiede $n=r$), e quindi per Cramer vale (v).

- **(vi) $\Rightarrow$ (vii).** Basta prendere $b=0$: per (vi) il sistema $Ax=0$ ammette un'unica soluzione, quindi esiste (almeno) un $b$ — cioè $b=0$ — con questa proprietà.

- **(vii) $\Rightarrow$ (v).** Se **un** particolare $b$ dà soluzione unica, allora per Rouché-Capelli $n=r(A)$ (l'unicità richiede sempre $n=r$, indipendentemente da quale $b$ si sia scelto, perché $r(A)$ non dipende da $b$). Ma allora $r(A)=n$, e per Cramer (v) vale per **ogni** $b$.

- **(iv) $\Rightarrow$ (i)** *(chiude il ciclo con (ii)-(iii))*. Se $r(A)=n$, riducendo $A$ a scalini con operazioni elementari (equivalenti a moltiplicare a sinistra per matrici invertibili $E_1,\dots,E_k$) si ottiene $E_k\cdots E_1 A = I_n$: quindi $B:=E_k\cdots E_1$ soddisfa $BA=I_n$. Si dimostra (con un argomento analogo, o applicando quanto già provato a $B$) che questa stessa $B$ soddisfa anche $AB=I_n$: dunque $B=A^{-1}$ e $A$ è invertibile.

Questo chiude la catena di equivalenze: (i) $\Leftrightarrow$ (ii) $\Leftrightarrow$ (iii) $\Leftrightarrow$ (iv) $\Leftrightarrow$ (v) $\Leftrightarrow$ (vi) $\Leftrightarrow$ (vii). $\blacksquare$

**Osservazione.** Il punto più utile in pratica è che per una matrice **quadrata** basta un'inversa **da un solo lato** (destra o sinistra) per concludere che $A$ è invertibile a tutti gli effetti (e che quell'inversa unilaterale coincide con $A^{-1}$). Questo **non** vale per matrici non quadrate.

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Insiemi, vettori e sistemi lineari — nozioni di base.md|Insiemi, vettori e sistemi lineari — nozioni di base]]
