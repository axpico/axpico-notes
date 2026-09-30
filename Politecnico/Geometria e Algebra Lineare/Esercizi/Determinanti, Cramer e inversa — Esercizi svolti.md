---
tags:
  - geometria-algebra-lineare
  - esercizi
  - determinante
  - laplace
  - cramer
  - matrice-inversa
  - gauss-jordan
  - rouche-capelli
---
Esercizi trascritti dagli appunti a mano (GAL 1), **con gli errori corretti**. Teoria di riferimento: [[Politecnico/Geometria e Algebra Lineare/Teoria/Determinante, sviluppo di Laplace e formula di Cramer.md|Determinante, sviluppo di Laplace e formula di Cramer]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Eliminazione di Gauss-Jordan e calcolo della matrice inversa.md|Gauss-Jordan]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Rouché-Capelli]].

---

## Esercizio 1 — Sistema con Gauss-Jordan e inversa

$$
\begin{cases}x+2y=4\\2x+5y-3z=0\\x+4y-8z=-18\end{cases}
\qquad A=\begin{bmatrix}1&2&0\\2&5&-3\\1&4&-8\end{bmatrix},\ \ \underline b=\begin{bmatrix}4\\0\\-18\end{bmatrix}.
$$

### (a) Soluzione con MEG-J

$R_2\to R_2-2R_1$, $R_3\to R_3-R_1$:

$$
\left(\begin{array}{ccc|c}1&2&0&4\\0&1&-3&-8\\0&2&-8&-22\end{array}\right)
\xrightarrow{R_3\to R_3-2R_2}
\left(\begin{array}{ccc|c}1&2&0&4\\0&1&-3&-8\\0&0&-2&-6\end{array}\right)
\xrightarrow{R_3\to-\frac12R_3}
\left(\begin{array}{ccc|c}1&2&0&4\\0&1&-3&-8\\0&0&1&3\end{array}\right)
$$

Risalita: $R_2\to R_2+3R_3$ e poi $R_1\to R_1-2R_2$:

$$
\left(\begin{array}{ccc|c}1&2&0&4\\0&1&0&1\\0&0&1&3\end{array}\right)\to
\left(\begin{array}{ccc|c}1&0&0&2\\0&1&0&1\\0&0&1&3\end{array}\right)
\quad\Longrightarrow\quad (x,y,z)=(2,\,1,\,3).
$$

> **Errori corretti negli appunti.**
> 1. Nella prima riduzione il termine noto di $R_2$ è $0-2\cdot4=\mathbf{-8}$, non $-4$ (era l'errore di calcolo cerchiato in rosso). Il $-6$ scritto dopo nella terza riga era invece già coerente con $-8$ ($-22-2\cdot(-8)=-6$), quindi l'errore era solo di trascrizione.
> 2. La soluzione finale $x=14,\ y=-5,\ z=3$ è sbagliata (solo $z=3$ è corretto). Con $z=3$: $y=-8+3z=1$, $x=4-2y=2$.
>
> Verifica nel sistema originale: $2+2\cdot1=4$ ✓; $4+5-9=0$ ✓; $2+4-24=-18$ ✓.

### (b) Inversa con MEG-J

Si imposta $[A\,|\,I_3]$ e si riduce a $[I_3\,|\,A^{-1}]$: risulta

$$
A^{-1}=\begin{bmatrix}14&-8&3\\-\tfrac{13}2&4&-\tfrac32\\-\tfrac32&1&-\tfrac12\end{bmatrix}.
$$

### (c) Controllo con i complementi algebrici

$\det A=1(5\cdot(-8)-(-3)\cdot4)-2(2\cdot(-8)-(-3)\cdot1)+0=-28+26=-2\ne0$, quindi $A$ è invertibile.

Matrice dei cofattori $C_{ij}=(-1)^{i+j}\det A_{ij}$:

$$
C=\begin{bmatrix}-28&13&3\\16&-8&-2\\-6&3&1\end{bmatrix},\qquad
A^{-1}=\frac1{-2}\,C^{\mathsf T}=-\frac12\begin{bmatrix}-28&16&-6\\13&-8&3\\3&-2&1\end{bmatrix}
$$

che coincide con la matrice di (b). (Nota la trasposizione: $C_{12}=13$ va in posizione $(2,1)$.)

### (d) Terza via: $\underline x=A^{-1}\underline b$

$$
\underline x=\begin{bmatrix}14&-8&3\\-\tfrac{13}2&4&-\tfrac32\\-\tfrac32&1&-\tfrac12\end{bmatrix}\begin{bmatrix}4\\0\\-18\end{bmatrix}=\begin{bmatrix}56-54\\-26+27\\-6+9\end{bmatrix}=\begin{bmatrix}2\\1\\3\end{bmatrix}\ \checkmark
$$

Le tre strade concordano: $\underline x=(2,1,3)$.

---

## Esercizio 2 — Determinante con Laplace

Calcolare $|A|$ per $A=\begin{bmatrix}1&1&0\\3&-1&1\\2&0&1\end{bmatrix}$.

Sviluppo lungo la **terza colonna** (ha uno zero):

$$
|A|=0\cdot C_{13}+1\cdot(-1)^{2+3}\begin{vmatrix}1&1\\2&0\end{vmatrix}+1\cdot(-1)^{3+3}\begin{vmatrix}1&1\\3&-1\end{vmatrix}
=-(0-2)+(-1-3)=2-4=-2 .
$$

Controllo con lo sviluppo lungo la prima riga: $1\begin{vmatrix}-1&1\\0&1\end{vmatrix}-1\begin{vmatrix}3&1\\2&1\end{vmatrix}+0=-1-1=-2$ ✓.

Poiché $|A|=-2\ne0$: $A$ è **invertibile** (non singolare), e ogni sistema $A\underline x=\underline b$ ha un'unica soluzione.

---

## Esercizio 3 — Parametro e unicità della soluzione

Sia $A=\begin{bmatrix}1&0&3\\-1&1&0\\2&1&-\alpha\end{bmatrix}$, $\alpha\in\mathbb R$. Per quali $\alpha$ il sistema $A\underline x=\underline b$ ha **una e una sola soluzione** (qualunque sia $\underline b$)?

Sviluppo lungo la terza colonna:

$$
|A|=3\begin{vmatrix}-1&1\\2&1\end{vmatrix}+0-\alpha\begin{vmatrix}1&0\\-1&1\end{vmatrix}=3\cdot(-3)-\alpha\cdot1=-9-\alpha .
$$

Per il teorema di Cramer e la caratterizzazione dell'invertibilità:

$$
|\mathrm{Sol}|=1\iff r(A)=3\iff|A|\neq0\iff\boxed{\alpha\ne-9}.
$$

Per $\alpha=-9$: $|A|=0$, $r(A)\le2$ (in realtà $=2$, il minore $\begin{vmatrix}1&0\\-1&1\end{vmatrix}=1\ne0$); il sistema è impossibile o ha $\infty^1$ soluzioni a seconda di $\underline b$ (si confronta $r(A)$ con $r(A')$ per Rouché–Capelli).

> Nel foglio il termine noto del sistema era illeggibile; il risultato sopra vale per ogni $\underline b$ quando $\alpha\ne-9$.

---

## Esercizio 4 — Regola di Cramer

$$
A=\begin{bmatrix}1&2&1\\1&1&1\\3&-1&1\end{bmatrix},\quad\underline b=\begin{bmatrix}4\\0\\-1\end{bmatrix},\quad A\underline x=\underline b.
$$

**Determinante.**

$$
|A|=1\begin{vmatrix}1&1\\-1&1\end{vmatrix}-2\begin{vmatrix}1&1\\3&1\end{vmatrix}+1\begin{vmatrix}1&1\\3&-1\end{vmatrix}=2+4-4=2\ne0 .
$$

**Matrici $A_i$** (colonna $i$ sostituita da $\underline b$) e relativi determinanti:

$$
|A_1|=\begin{vmatrix}4&2&1\\0&1&1\\-1&-1&1\end{vmatrix}=4(2)-2(1)+1(1)=7,\quad
|A_2|=\begin{vmatrix}1&4&1\\1&0&1\\3&-1&1\end{vmatrix}=1(1)-4(-2)+1(-1)=8,
$$

$$
|A_3|=\begin{vmatrix}1&2&4\\1&1&0\\3&-1&-1\end{vmatrix}=1(-1)-2(-1)+4(-4)=-15 .
$$

$$
x_1=\frac{|A_1|}{|A|}=\frac72,\qquad x_2=\frac{|A_2|}{|A|}=4,\qquad x_3=\frac{|A_3|}{|A|}=-\frac{15}2 .
$$

Verifica: $\tfrac72+8-\tfrac{15}2=4$ ✓; $\tfrac72+4-\tfrac{15}2=0$ ✓; $\tfrac{21}2-4-\tfrac{15}2=-1$ ✓.

---

## Esercizio 5 — Sistema con $|A|=0$: $\infty^1$ soluzioni

$$
\begin{cases}x-2y-3z=1\\x+y=3\\2x+2y=6\end{cases}
\qquad A=\begin{bmatrix}1&-2&-3\\1&1&0\\2&2&0\end{bmatrix}.
$$

**Passo 1: rango.** $|A|=0$ (la terza riga è $2\times$ la seconda), quindi $r(A)\le2$. Il minore $\begin{vmatrix}1&-2\\1&1\end{vmatrix}=3\neq0$ dà $r(A)=2$. Anche $r(A')=2$, perché la terza equazione è $2\times$ la seconda anche nei termini noti ($6=2\cdot3$). Per Rouché–Capelli: compatibile con $\infty^{3-2}=\infty^1$ soluzioni.

**Passo 2: riduzione.** Si elimina l'ultima equazione (dipendente) e si sceglie $z=t$ come parametro, portandolo a destra:

$$
\begin{cases}x-2y=1+3t\\x+y=3\end{cases}\qquad\text{matrice }\begin{bmatrix}1&-2\\1&1\end{bmatrix},\ \det=3\ne0 .
$$

**Passo 3: Cramer sul sistema $2\times2$.**

$$
x=\frac{\begin{vmatrix}1+3t&-2\\3&1\end{vmatrix}}{3}=\frac{(1+3t)+6}{3}=\frac{3t+7}3,\qquad
y=\frac{\begin{vmatrix}1&1+3t\\1&3\end{vmatrix}}{3}=\frac{3-(1+3t)}3=\frac{2-3t}3,\qquad z=t .
$$

$$
\underline x=\begin{bmatrix}\tfrac{3t+7}3\\[2pt]\tfrac{2-3t}3\\[2pt]t\end{bmatrix}=\begin{bmatrix}7/3\\2/3\\0\end{bmatrix}+t\begin{bmatrix}1\\-1\\1\end{bmatrix},\quad t\in\mathbb R .
$$

Verifica: $x+y=\tfrac{9}{3}=3$ ✓; $x-2y-3z=\tfrac{3t+7-4+6t}3-3t=3t+1-3t=1$ ✓.

> **Errore corretto.** Nell'ultimo vettore degli appunti $x$ compare come $\frac{3t+5}3$ (o simile): il numeratore corretto è $3t+\mathbf7$, come mostra la riga precedente ($\tfrac13(1+3t+6)$). Con $+5$ la prima equazione non sarebbe soddisfatta.

---

## Riepilogo dei metodi

| Obiettivo | Metodo | Quando conviene |
|---|---|---|
| Risolvere $A\underline x=\underline b$ numerico | Gauss / Gauss-Jordan | quasi sempre |
| Risolvere con $\det A\ne0$ e ordine piccolo | Cramer $x_i=|A_i|/|A|$ | $n=2,3$, parametri |
| Invertibilità / unicità con parametro | $\det A\ne0$ | sempre il primo controllo |
| Calcolare $A^{-1}$ | MEG-J su $[A\,|\,I]$; o $\frac1{|A|}C^{\mathsf T}$ | MEG-J numerico; cofattori simbolico |
| Caso $\det A=0$ | rango (pivot o minori) + Rouché–Capelli, poi Cramer ridotto | sistemi con $\infty^k$ soluzioni |
