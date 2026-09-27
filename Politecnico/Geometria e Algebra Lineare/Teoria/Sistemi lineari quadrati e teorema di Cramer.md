---
tags:
  - geometria-algebra-lineare
  - matrici
  - sistemi-lineari
  - cramer
---
## Sistemi lineari quadrati e Teorema di Cramer

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

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]
