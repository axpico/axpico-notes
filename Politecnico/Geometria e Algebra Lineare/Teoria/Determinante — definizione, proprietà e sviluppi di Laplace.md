---
tags:
  - geometria-algebra-lineare
  - determinante
  - laplace
  - sarrus
---
# Determinante — definizione, proprietà e sviluppi di Laplace

Fonte: Lezione 9, parte 1a (pp. 39–52) e parte 1b (pp. 2–12).
Riepilogo compatto con Cramer e inversa: [[Determinante, sviluppo di Laplace e formula di Cramer]]. Continua in [[Applicazioni dei determinanti — Binet, inversa, Cramer, Kronecker]].

## 1. Definizione (assiomatica)

> [!important] Proposizione
> Per ogni $n\in\mathbb N$ esiste **un'unica** mappa
> $$\det:M_{\mathbb K}(n,n)\to\mathbb K$$
> (il **determinante di ordine $n$**; $M_{\mathbb K}(n,n)$ = matrici $n\times n$ con elementi in $\mathbb K$) con le 4 proprietà:
> 1. **(i) scambio.** Se $A'$ si ottiene da $A$ scambiando due righe: $\det A'=-\det A$.
> 2. **(ii) scalare.** Se $A''$ si ottiene moltiplicando **una** riga di $A$ per $\lambda\in\mathbb K$: $\det A''=\lambda\det A$.
> 3. **(iii) combinazione.** Se $A'''$ si ottiene sommando/sottraendo a una riga un multiplo di un'altra riga: $\det A'''=\det A$.
> 4. **(iv) triangolare.** Se tutti gli elementi **sotto** la diagonale principale sono nulli (**triangolare alta**):
> $$\det A=a_{11}a_{22}\cdots a_{nn}.$$

(i)–(iii) dicono come cambia $\det$ sotto le **mosse di Gauss** (MEG); (iv) dà il valore sulla forma finale.

**Notazione.** $\det A=\begin{vmatrix}a_{11}&\cdots&a_{1n}\\\vdots&&\vdots\\a_{n1}&\cdots&a_{nn}\end{vmatrix}$ (barre al posto delle parentesi quadre).

> [!warning] (ii) agisce su UNA riga
> Moltiplicare tutta la matrice per $\lambda$ moltiplica ogni riga: $\det(\lambda A)=\lambda^n\det A$.

### Formula $2\times2$ (dimostrata dagli assiomi)

$A=\begin{bmatrix}a&b\\c&d\end{bmatrix}$.

- **Caso $a\neq0$.** $R_2\to R_2-\frac caR_1$ dà $A'''=\begin{bmatrix}a&b\\0&d-\frac{bc}a\end{bmatrix}$, triangolare alta. Per (iv) e (iii):
$$\det A=\det A'''=a\Big(d-\frac{bc}a\Big)=ad-bc .$$
- **Caso $a=0$.** $R_1\leftrightarrow R_2$: $A'=\begin{bmatrix}c&d\\0&b\end{bmatrix}$, $\det A'=cb$. Per (i): $\det A=-cb=0\cdot d-bc$.

$$\boxed{\det\begin{bmatrix}a&b\\c&d\end{bmatrix}=ad-bc}$$

## 2. Calcolo con MEG

**Esempio.**
$$\begin{vmatrix}0&1&1\\3&4&6\\3&2&2\end{vmatrix}\overset{R_3\leftrightarrow R_1}{=}-\begin{vmatrix}3&2&2\\3&4&6\\0&1&1\end{vmatrix}\overset{R_2\to R_2-R_1}{=}-\begin{vmatrix}3&2&2\\0&2&4\\0&1&1\end{vmatrix}\overset{R_2\to\frac12R_2}{=}-2\begin{vmatrix}3&2&2\\0&1&2\\0&1&1\end{vmatrix}$$
$$\overset{R_3\to R_3-R_2}{=}-2\begin{vmatrix}3&2&2\\0&1&2\\0&0&-1\end{vmatrix}\overset{\text{(iv)}}{=}-2\cdot\big(3\cdot1\cdot(-1)\big)=6 .$$

(Attenzione al passo con (ii): se divido una riga per $2$, il fattore $2$ esce **fuori**.)

## 3. Determinante e rango

**Oss. 1.** Ogni matrice quadrata **a scala** è triangolare alta.

**Oss. 2.** In una matrice quadrata a scala gli elementi sulla diagonale sono **tutti non nulli** $\iff$ non ci sono righe nulle $\iff$ $r(A)=n$.

Esempi: $A=\begin{bmatrix}1&2&3\\0&4&5\\0&0&6\end{bmatrix}$, $r(A)=3$, $\det A=24\neq0$; $\ B=\begin{bmatrix}1&2&3&4\\0&5&6&7\\0&0&0&8\\0&0&0&0\end{bmatrix}$, $r(B)=3<4$, $\det B=1\cdot5\cdot0\cdot0=0$.

Quindi per una matrice a scala $\det A\neq0\iff r(A)=n$. Siccome ogni matrice si riduce a scala con MEG, e MEG non cambia né il rango né l'essere $\det\neq0$ (al più cambia segno o fattore non nullo):

> [!important] Per ogni $A$ di ordine $n$
> $$\det A\neq0\iff r(A)=n .$$

## 4. Regola di Sarrus ($n=3$)

$$\det A=a_{11}a_{22}a_{33}+a_{12}a_{23}a_{31}+a_{13}a_{21}a_{32}-a_{13}a_{22}a_{31}-a_{11}a_{23}a_{32}-a_{12}a_{21}a_{33}$$

Si ricopiano le prime due colonne a destra: tre diagonali "discendenti" col $+$, tre "ascendenti" col $-$. Utile quando $A$ ha molti zeri. **Vale solo per $n=3$.**

## 5. Determinante della trasposta

> [!important] Teorema 1
> Per ogni matrice quadrata $A$: $\det(A^T)=\det A$. (senza dimostrazione)

**Esempio.** $A=\begin{bmatrix}1&2&3\\0&2&0\\3&2&1\end{bmatrix}$:
- con $R_1\to R_1-R_2$, $R_3\to R_3-R_2$ e Sarrus: $\begin{vmatrix}1&0&3\\0&2&0\\3&0&1\end{vmatrix}=2-18=-16$;
- $\det A^T=\begin{vmatrix}1&0&3\\2&2&2\\3&0&1\end{vmatrix}\to\begin{vmatrix}1&0&3\\0&2&-4\\0&0&-8\end{vmatrix}=-16$. ✓

**Conseguenza: tutto ciò che vale per le righe vale per le colonne.**
- scambiare due **colonne** cambia il segno;
- moltiplicare una colonna per $\lambda$ moltiplica $\det$ per $\lambda$;
- sommare a una colonna un multiplo di un'altra non cambia $\det$.

**Def.** $A$ è **triangolare bassa** se tutti gli elementi **sopra** la diagonale sono nulli. Allora $A^T$ è triangolare alta con la stessa diagonale, quindi anche
$$\det A=a_{11}a_{22}\cdots a_{nn}\quad\text{(triangolare bassa)}.$$

**Esempio (colonne).** $\begin{vmatrix}1&0&1\\1&1&1\\1&2&3\end{vmatrix}\overset{C_3\to C_3-C_1}{=}\begin{vmatrix}1&0&0\\1&1&0\\1&2&3\end{vmatrix}=1\cdot1\cdot3=3$.

**Esempio (righe e colonne insieme).**
$$\begin{vmatrix}13&14&12\\12&14&11\\17&20&17\end{vmatrix}\overset{\substack{C_1\to C_1-C_3\\C_2\to C_2-C_3}}{=}\begin{vmatrix}1&2&12\\1&3&11\\0&3&17\end{vmatrix}\overset{R_2\to R_2-R_1}{=}\begin{vmatrix}1&2&12\\0&1&-1\\0&3&17\end{vmatrix}\overset{R_3\to R_3-3R_2}{=}\begin{vmatrix}1&2&12\\0&1&-1\\0&0&20\end{vmatrix}=20 .$$

## 6. Sviluppi di Laplace

Idea: ridurre un determinante di ordine $n$ a determinanti di ordine $n-1$.

**Def.** Data $A$ quadrata:
- $A_{ij}$ = matrice ottenuta **cancellando la riga $i$ e la colonna $j$**; il suo determinante (a volte $A_{ij}$ stessa) è il **minore complementare** di $a_{ij}$;
- il **cofattore** (o **complemento algebrico**) di $a_{ij}$ è
$$C_{ij}:=(-1)^{i+j}\det(A_{ij}).$$

**Esempio.** $A=\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}$, elemento $a_{21}=4$: $A_{21}=\begin{bmatrix}2&3\\8&9\end{bmatrix}$,
$C_{21}=(-1)^{2+1}\begin{vmatrix}2&3\\8&9\end{vmatrix}=-(18-24)=6$.

> [!important] Teorema 2 (sviluppi di Laplace)
> Sia $A$ di ordine $n$.
> 1. Fissata una riga $i_0$: $\displaystyle\det A=\sum_{j=1}^n a_{i_0j}C_{i_0j}$ (sviluppo rispetto alla $i_0$-esima riga).
> 2. Fissata una colonna $j_0$: $\displaystyle\det A=\sum_{i=1}^n a_{ij_0}C_{ij_0}$ (sviluppo rispetto alla $j_0$-esima colonna).
>
> (senza dimostrazione)

Segni $(-1)^{i+j}$ a scacchiera: $\begin{bmatrix}+&-&+\\-&+&-\\+&-&+\end{bmatrix}$.

**Esempio (prima riga).**
$$\begin{vmatrix}1&0&2\\2&1&3\\0&3&1\end{vmatrix}=1\cdot C_{11}+0\cdot C_{12}+2\cdot C_{13}=\begin{vmatrix}1&3\\3&1\end{vmatrix}+2\begin{vmatrix}2&1\\0&3\end{vmatrix}=(1-9)+2\cdot6=4 .$$

**Stesso determinante, seconda colonna.**
$$=0\cdot C_{12}+1\cdot C_{22}+3\cdot C_{32}=(-1)^{2+2}\begin{vmatrix}1&2\\0&1\end{vmatrix}+3(-1)^{3+2}\begin{vmatrix}1&2\\2&3\end{vmatrix}=1-3(3-4)=4 .$$

**Strategia:** scegli la riga/colonna con **più zeri** (eventualmente creali prima con MEG).

**Esempio $4\times4$.**
$$\begin{vmatrix}2&1&0&0\\0&1&0&1\\1&0&4&1\\0&2&0&3\end{vmatrix}\overset{\text{3ª col.}}{=}+4\begin{vmatrix}2&1&0\\0&1&1\\0&2&3\end{vmatrix}\overset{\text{1ª col.}}{=}4\cdot2\begin{vmatrix}1&1\\2&3\end{vmatrix}=8(3-2)=8 .$$

## Collegamenti
- Successiva: [[Applicazioni dei determinanti — Binet, inversa, Cramer, Kronecker]]
- Riepilogo/esercizi: [[Determinante, sviluppo di Laplace e formula di Cramer]] · [[Determinanti, Cramer e inversa — Esercizi svolti]]
- Rango: [[Rango e teorema di nullità più rango]] · MEG: [[Eliminazione di Gauss-Jordan e calcolo della matrice inversa]]
- PDF: [[09 parte 1a. Determinanti (definizione).pdf|Parte 1a]] · [[09 parte 1b. Sviluppi di Laplace.pdf|Parte 1b]]
