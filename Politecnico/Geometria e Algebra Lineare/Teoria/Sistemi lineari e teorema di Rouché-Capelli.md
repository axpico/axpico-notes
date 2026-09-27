---
tags:
  - geometria-algebra-lineare
  - matrici
  - sistemi-lineari
  - rouche-capelli
---
## Teorema di Rouché-Capelli

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

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari quadrati e teorema di Cramer.md|Sistemi lineari quadrati e teorema di Cramer]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Insiemi, vettori e sistemi lineari — nozioni di base.md|Insiemi, vettori e sistemi lineari — nozioni di base]]
