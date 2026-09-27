---
tags:
  - geometria-algebra-lineare
  - matrici
  - esercizi
  - rouche-capelli
  - cramer
  - matrice-inversa
  - gauss-jordan
  - equazioni-matriciali
---
Dieci esercizi, in ordine di difficoltà crescente, pensati per coprire **tutto** il materiale delle note di teoria collegate: operazioni tra matrici, Rouché-Capelli, Cramer, matrice inversa (formula $2\times2$ e Gauss-Jordan), equazioni matriciali. Prova a risolverli da solo/a prima di guardare le soluzioni in fondo.

## Collegamenti alla teoria

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari quadrati e teorema di Cramer.md|Sistemi lineari quadrati e teorema di Cramer]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Eliminazione di Gauss-Jordan e calcolo della matrice inversa.md|Eliminazione di Gauss-Jordan e calcolo della matrice inversa]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Equazioni matriciali.md|Equazioni matriciali]]

---

## Esercizi

**1. Operazioni base.** Date
$$
A=\begin{bmatrix}2&-1&0\\3&1&4\end{bmatrix},\qquad B=\begin{bmatrix}1&2&-1\\0&-2&5\end{bmatrix},
$$
calcolare $A+2B$, $A-B$, $3A$ e la trasposta $A^{\mathsf T}$.

**2. Prodotto tra matrici e non commutatività.** Date
$$
A=\begin{bmatrix}1&2\\0&1\end{bmatrix},\qquad B=\begin{bmatrix}3&0\\1&2\end{bmatrix},
$$
calcolare $AB$ e $BA$ e verificare che sono diverse.

**3. Trasposta di un prodotto.** Usando le stesse $A,B$ dell'esercizio 2, verificare numericamente che $(AB)^{\mathsf T}=B^{\mathsf T}A^{\mathsf T}$.

**4. Prodotto matrice-vettore.** Scrivere in forma matriciale $A\underline x=\underline b$ il sistema
$$
\begin{cases}2x+y=5\\ x-y=1\end{cases}
$$
e risolverlo usando il prodotto matrice-vettore (verifica per sostituzione).

**5. Rouché-Capelli (caso numerico).** Discutere e risolvere il sistema
$$
\begin{cases}x+y+z=6\\ 2x-y+z=3\\ x-2y=-3\end{cases}
$$

**6. Rouché-Capelli (caso parametrico).** Discutere, al variare di $k\in\mathbb R$, il sistema
$$
\begin{cases}x+y+z=3\\ x+2y+kz=4\\ x+y+kz=k\end{cases}
$$
e risolverlo esplicitamente per $k\ne 1$.

**7. Teorema di Cramer.** Verificare che il sistema
$$
\begin{cases}2x+y-z=3\\ x-y+2z=-1\\ 3x+2y+z=8\end{cases}
$$
ha matrice dei coefficienti di rango massimo (quindi, per Cramer, un'unica soluzione per ogni termine noto) e trovarla.

**8. Inversa $2\times2$.** Usando la formula del Teorema 5, calcolare l'inversa di
$$
A=\begin{bmatrix}3&1\\5&2\end{bmatrix}
$$
e verificare $AA^{-1}=I_2$.

**9. Inversa con Gauss-Jordan (MEG-J).** Calcolare l'inversa di
$$
A=\begin{bmatrix}2&0&0\\1&2&0\\1&1&1\end{bmatrix}
$$
riducendo la matrice orlata $[A\mid I_3]$ con l'eliminazione di Gauss-Jordan.

**10. Equazioni matriciali.** Sia $A=\begin{bmatrix}3&1\\5&2\end{bmatrix}$ (come nell'esercizio 8).
- (a) Risolvere $AX=B$ con $B=\begin{bmatrix}4&2\\7&3\end{bmatrix}$.
- (b) Risolvere $YA=C$ con $C=\begin{bmatrix}5&3\\7&4\\9&5\end{bmatrix}$.

---

## Soluzioni

### Soluzione 1

$$
A+2B=\begin{bmatrix}2+2&-1+4&0-2\\3+0&1-4&4+10\end{bmatrix}=\begin{bmatrix}4&3&-2\\3&-3&14\end{bmatrix}
$$

$$
A-B=\begin{bmatrix}1&-3&1\\3&3&-1\end{bmatrix},\qquad 3A=\begin{bmatrix}6&-3&0\\9&3&12\end{bmatrix}
$$

$$
A^{\mathsf T}=\begin{bmatrix}2&3\\-1&1\\0&4\end{bmatrix}
$$

> **Errore tipico (svolgimento a mano).** Un errore ricorrente in questo esercizio è scrivere la prima riga di $A^{\mathsf T}$ come $[3\ \ 2]$ invece di $[2\ \ 3]$. Va ricordato: la **colonna $j$ di $A$ diventa la riga $j$ di $A^{\mathsf T}$**, mantenendo l'ordine degli elementi. Qui la colonna 1 di $A$ è $\begin{bmatrix}2\\3\end{bmatrix}$ (nell'ordine: elemento di riga 1, poi elemento di riga 2), quindi la riga 1 di $A^{\mathsf T}$ deve essere $[2\ \ 3]$, non $[3\ \ 2]$: le altre due colonne/righe (di solito) vengono trasposte correttamente perché coincidono per simmetria dei valori, mascherando l'errore.

### Soluzione 2

$$
AB=\begin{bmatrix}1\cdot3+2\cdot1 & 1\cdot0+2\cdot2\\0\cdot3+1\cdot1&0\cdot0+1\cdot2\end{bmatrix}=\begin{bmatrix}5&4\\1&2\end{bmatrix}
$$

$$
BA=\begin{bmatrix}3\cdot1+0\cdot0&3\cdot2+0\cdot1\\1\cdot1+2\cdot0&1\cdot2+2\cdot1\end{bmatrix}=\begin{bmatrix}3&6\\1&4\end{bmatrix}
$$

$AB\ne BA$: il prodotto tra matrici non è commutativo, come atteso.

### Soluzione 3

Dall'esercizio 2, $AB=\begin{bmatrix}5&4\\1&2\end{bmatrix}$, quindi $(AB)^{\mathsf T}=\begin{bmatrix}5&1\\4&2\end{bmatrix}$.

D'altra parte $A^{\mathsf T}=\begin{bmatrix}1&0\\2&1\end{bmatrix}$, $B^{\mathsf T}=\begin{bmatrix}3&1\\0&2\end{bmatrix}$, e

$$
B^{\mathsf T}A^{\mathsf T}=\begin{bmatrix}3\cdot1+1\cdot2&3\cdot0+1\cdot1\\0\cdot1+2\cdot2&0\cdot0+2\cdot1\end{bmatrix}=\begin{bmatrix}5&1\\4&2\end{bmatrix}=(AB)^{\mathsf T}. \ \checkmark
$$

(In generale: l'elemento $(i,j)$ di $(AB)^{\mathsf T}$ è l'elemento $(j,i)$ di $AB$, cioè la riga $j$ di $A$ per la colonna $i$ di $B$; questo coincide esattamente con la riga $i$ di $B^{\mathsf T}$ per la colonna $j$ di $A^{\mathsf T}$, che è l'elemento $(i,j)$ di $B^{\mathsf T}A^{\mathsf T}$.)

### Soluzione 4

$$
A=\begin{bmatrix}2&1\\1&-1\end{bmatrix},\qquad \underline b=\begin{bmatrix}5\\1\end{bmatrix}
$$

Sommando le due equazioni originali, $3x=6\Rightarrow x=2$, e sostituendo $x-y=1\Rightarrow y=1$. Quindi $\underline x=\begin{bmatrix}2\\1\end{bmatrix}$.

Verifica: $2\cdot2+1=5$ ✓, $2-1=1$ ✓.

### Soluzione 5

Matrice completa e riduzione:

$$
\left(\begin{array}{ccc|c}1&1&1&6\\2&-1&1&3\\1&-2&0&-3\end{array}\right)
\xrightarrow[R_3\to R_3-R_1]{R_2\to R_2-2R_1}
\left(\begin{array}{ccc|c}1&1&1&6\\0&-3&-1&-9\\0&-3&-1&-9\end{array}\right)
\xrightarrow{R_3\to R_3-R_2}
\left(\begin{array}{ccc|c}1&1&1&6\\0&-3&-1&-9\\0&0&0&0\end{array}\right)
$$

$\text{rk}(A)=\text{rk}(A')=2 < n=3$: per Rouché-Capelli il sistema è **compatibile** con $\infty^{3-2}=\infty^1$ soluzioni.

Dalla seconda riga: $-3y-z=-9 \Rightarrow z=9-3y$. Dalla prima: $x=6-y-z=6-y-(9-3y)=2y-3$. Ponendo $y=t$:

$$
\underline x=\begin{bmatrix}x\\y\\z\end{bmatrix}=\begin{bmatrix}-3\\0\\9\end{bmatrix}+t\begin{bmatrix}2\\1\\-3\end{bmatrix},\qquad t\in\mathbb R.
$$

*(Verifica con $t=1$: $x=-1,y=1,z=6$: $-1+1+6=6$ ✓; $-2-1+6=3$ ✓; $-1-2=-3$ ✓.)*

### Soluzione 6

$$
\left(\begin{array}{ccc|c}1&1&1&3\\1&2&k&4\\1&1&k&k\end{array}\right)
\xrightarrow[R_3\to R_3-R_1]{R_2\to R_2-R_1}
\left(\begin{array}{ccc|c}1&1&1&3\\0&1&k-1&1\\0&0&k-1&k-3\end{array}\right)
$$

(la terza riga si ottiene già così: $R_3-R_1$ dà $(0,0,k-1\mid k-3)$, e $R_3\to R_3-R_2$ non serve perché la colonna 2 è già $0$).

- **Se $k\ne1$**: il terzo pivot $k-1\ne0$ esiste, quindi $\text{rk}(A)=\text{rk}(A')=3=n$: **soluzione unica**.
- **Se $k=1$**: la terza riga diventa $(0,0,0\mid -2)$, cioè $0=-2$: **sistema impossibile** ($\text{rk}(A)=2\ne\text{rk}(A')=3$).

Non ci sono valori di $k$ con $\infty^1$ soluzioni: o $k\ne1$ (unica) o $k=1$ (impossibile).

**Soluzione esplicita per $k\ne1$** (sostituzione all'indietro):

$$
z=\frac{k-3}{k-1},\qquad y=1-(k-1)z=1-(k-3)=4-k,\qquad x=3-y-z=(k-1)-\frac{k-3}{k-1}=\frac{k^2-3k+4}{k-1}.
$$

*(Verifica per $k=0$: $z=3,\,y=4,\,x=-4$; sostituendo nelle equazioni originali con $k=0$: $-4+4+3=3$ ✓, $-4+8+0=4$ ✓, $-4+4+0=0=k$ ✓.)*

### Soluzione 7

$$
\left(\begin{array}{ccc|c}2&1&-1&3\\1&-1&2&-1\\3&2&1&8\end{array}\right)
\xrightarrow{R_1\leftrightarrow R_2}
\left(\begin{array}{ccc|c}1&-1&2&-1\\2&1&-1&3\\3&2&1&8\end{array}\right)
\xrightarrow[R_3\to R_3-3R_1]{R_2\to R_2-2R_1}
\left(\begin{array}{ccc|c}1&-1&2&-1\\0&3&-5&5\\0&5&-5&11\end{array}\right)
$$

$$
\xrightarrow{R_3\to R_3-\tfrac53 R_2}
\left(\begin{array}{ccc|c}1&-1&2&-1\\0&3&-5&5\\0&0&\tfrac{10}{3}&\tfrac83\end{array}\right)
$$

Tre pivot non nulli $\Rightarrow \text{rk}(A)=3=$ ordine del sistema: per il Teorema di Cramer c'è un'**unica soluzione**, qualunque sia il termine noto (in particolare per questo).

Sostituzione all'indietro: $z=\dfrac{8/3}{10/3}=\dfrac{4}{5}$; da $3y-5z=5$: $y=\dfrac{5+5\cdot\frac45}{3}=\dfrac{5+4}{3}=3$; da $x-y+2z=-1$: $x=-1+y-2z=-1+3-\dfrac85=\dfrac25$.

$$
x=\frac25,\qquad y=3,\qquad z=\frac45.
$$

*(Verifica nella prima equazione originale: $2\cdot\frac25+3-\frac45=\frac45+3-\frac45=3$ ✓.)*

### Soluzione 8

$ad-bc=3\cdot2-1\cdot5=6-5=1\ne0$, quindi $A$ è invertibile e

$$
A^{-1}=\frac11\begin{bmatrix}2&-1\\-5&3\end{bmatrix}=\begin{bmatrix}2&-1\\-5&3\end{bmatrix}.
$$

Verifica: $AA^{-1}=\begin{bmatrix}3\cdot2+1\cdot(-5)&3\cdot(-1)+1\cdot3\\5\cdot2+2\cdot(-5)&5\cdot(-1)+2\cdot3\end{bmatrix}=\begin{bmatrix}1&0\\0&1\end{bmatrix}=I_2$. ✓

### Soluzione 9

$$
\left(\begin{array}{ccc|ccc}2&0&0&1&0&0\\1&2&0&0&1&0\\1&1&1&0&0&1\end{array}\right)
\xrightarrow{R_1\to \tfrac12R_1}
\left(\begin{array}{ccc|ccc}1&0&0&\tfrac12&0&0\\1&2&0&0&1&0\\1&1&1&0&0&1\end{array}\right)
$$

$$
\xrightarrow[R_3\to R_3-R_1]{R_2\to R_2-R_1}
\left(\begin{array}{ccc|ccc}1&0&0&\tfrac12&0&0\\0&2&0&-\tfrac12&1&0\\0&1&1&-\tfrac12&0&1\end{array}\right)
\xrightarrow{R_2\to\tfrac12R_2}
\left(\begin{array}{ccc|ccc}1&0&0&\tfrac12&0&0\\0&1&0&-\tfrac14&\tfrac12&0\\0&1&1&-\tfrac12&0&1\end{array}\right)
$$

$$
\xrightarrow{R_3\to R_3-R_2}
\left(\begin{array}{ccc|ccc}1&0&0&\tfrac12&0&0\\0&1&0&-\tfrac14&\tfrac12&0\\0&0&1&-\tfrac14&-\tfrac12&1\end{array}\right)
$$

La parte sinistra è $I_3$ (nessun'altra eliminazione "sopra" i pivot è necessaria, perché le colonne 2 e 3 di $A$ erano già nulle nelle righe superiori), quindi

$$
A^{-1}=\begin{bmatrix}\tfrac12&0&0\\-\tfrac14&\tfrac12&0\\-\tfrac14&-\tfrac12&1\end{bmatrix}.
$$

Verifica (riga 3 di $A$ per $A^{-1}$, la più delicata): $[1,1,1]\cdot\text{colonne}$: col1: $\tfrac12-\tfrac14-\tfrac14=0$; col2: $0+\tfrac12-\tfrac12=0$; col3: $0+0+1=1$ → riga $(0,0,1)$, corretta.

### Soluzione 10

**(a)** $AX=B \Rightarrow X=A^{-1}B$. Con $A^{-1}=\begin{bmatrix}2&-1\\-5&3\end{bmatrix}$ (esercizio 8):

$$
X=\begin{bmatrix}2&-1\\-5&3\end{bmatrix}\begin{bmatrix}4&2\\7&3\end{bmatrix}=\begin{bmatrix}2\cdot4-1\cdot7 & 2\cdot2-1\cdot3\\-5\cdot4+3\cdot7&-5\cdot2+3\cdot3\end{bmatrix}=\begin{bmatrix}1&1\\1&-1\end{bmatrix}.
$$

Verifica: $AX=\begin{bmatrix}3+1&3-1\\5+2&5-2\end{bmatrix}=\begin{bmatrix}4&2\\7&3\end{bmatrix}=B$. ✓

**(b)** $YA=C \Rightarrow Y=CA^{-1}$:

$$
Y=\begin{bmatrix}5&3\\7&4\\9&5\end{bmatrix}\begin{bmatrix}2&-1\\-5&3\end{bmatrix}=\begin{bmatrix}5\cdot2-3\cdot5 & -5+3\cdot3\\7\cdot2-4\cdot5&-7+4\cdot3\\9\cdot2-5\cdot5&-9+5\cdot3\end{bmatrix}=\begin{bmatrix}-5&4\\-6&5\\-7&6\end{bmatrix}.
$$

Verifica (prima riga): $[-5,4]\cdot A = [-5\cdot3+4\cdot5,\ -5\cdot1+4\cdot2]=[-15+20,\,-5+8]=[5,3]=$ prima riga di $C$. ✓
