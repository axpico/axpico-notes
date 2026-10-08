---
tags:
  - geometria-algebra-lineare
  - matrici
  - determinante
  - laplace
  - cramer
  - matrice-inversa
  - rango
---
## Il determinante

Il **determinante** è una funzione

$$
\det:\ M_n(\mathbb R)\longrightarrow\mathbb R,\qquad A\longmapsto \det A=|A|,
$$

definita solo per matrici **quadrate**. Intuizione: $|\det A|$ è il fattore di scala con cui la trasformazione lineare $x\mapsto Ax$ cambia aree ($n=2$) o volumi ($n=3$); il segno dice se l'orientazione viene mantenuta o ribaltata. Il determinante è zero esattamente quando la trasformazione "schiaccia" lo spazio in uno di dimensione inferiore, cioè quando $A$ non è invertibile.

### Casi $n=1,2$

$$
n=1:\ \det[a]=a,\qquad\qquad n=2:\ \det\begin{bmatrix}a&b\\c&d\end{bmatrix}=ad-bc .
$$

Per $n=2$ è la quantità che compare nella formula dell'inversa (Teorema 5 nella nota [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]).

### Minori e complementi algebrici

Sia $A=(a_{ij})\in M_n(\mathbb R)$.

- Il **minore complementare** $A_{ij}$ è la matrice $(n-1)\times(n-1)$ ottenuta cancellando la riga $i$ e la colonna $j$ di $A$. (Alcuni testi chiamano *minore* il suo determinante: controlla la convenzione del corso.)
- Il **complemento algebrico** (o *cofattore*) di $a_{ij}$ è
$$
C_{ij}:=(-1)^{i+j}\,\det A_{ij}.
$$
Il segno segue la "scacchiera":
$$
\begin{bmatrix}+&-&+&\cdots\\-&+&-&\cdots\\+&-&+&\cdots\\\vdots&&&\ddots\end{bmatrix}
$$

### Sviluppo di Laplace

**Teorema.** Per ogni riga $i$ fissata (sviluppo *lungo la riga* $i$) e per ogni colonna $j$ fissata (sviluppo *lungo la colonna* $j$) vale

$$
\det A=\sum_{j=1}^{n}a_{ij}\,C_{ij}=\sum_{i=1}^{n}a_{ij}\,C_{ij}.
$$

Il risultato **non dipende** dalla riga/colonna scelta: conviene scegliere quella con più zeri.

**Caso $n=3$, sviluppo lungo la prima riga:**

$$
\det A=a_{11}\begin{vmatrix}a_{22}&a_{23}\\a_{32}&a_{33}\end{vmatrix}-a_{12}\begin{vmatrix}a_{21}&a_{23}\\a_{31}&a_{33}\end{vmatrix}+a_{13}\begin{vmatrix}a_{21}&a_{22}\\a_{31}&a_{32}\end{vmatrix}
$$

$$
=a_{11}(a_{22}a_{33}-a_{32}a_{23})-a_{12}(a_{21}a_{33}-a_{23}a_{31})+a_{13}(a_{21}a_{32}-a_{22}a_{31}).
$$

**Esempio.** $A=\begin{bmatrix}1&1&0\\3&-1&1\\2&0&1\end{bmatrix}$. Sviluppo lungo la **terza colonna** (contiene uno zero):

$$
\det A=\underbrace{0\cdot C_{13}}_{0}+1\cdot(-1)^{2+3}\begin{vmatrix}1&1\\2&0\end{vmatrix}+1\cdot(-1)^{3+3}\begin{vmatrix}1&1\\3&-1\end{vmatrix}=-(-2)+(-4)=-2.
$$

### Proprietà utili (senza dimostrazione)

1. $\det I_n=1$; $\det A^{\mathsf T}=\det A$ (quindi ciò che vale per le righe vale per le colonne).
2. **Scambiare due righe** cambia il segno; **moltiplicare una riga per $\lambda$** moltiplica $\det$ per $\lambda$; **sommare a una riga un multiplo di un'altra** *non* cambia $\det$. (È il motivo per cui Gauss permette di calcolare i determinanti.)
3. Due righe (o colonne) uguali o proporzionali, o una riga nulla $\Rightarrow\det A=0$.
4. **Teorema di Binet**: $\det(AB)=\det A\cdot\det B$.
5. Se $A$ è **triangolare** (o diagonale), $\det A$ è il prodotto degli elementi sulla diagonale.
6. $\det(\lambda A)=\lambda^n\det A$ (non $\lambda\det A$!).

## Determinante e invertibilità

**Teorema.** Per $A\in M_n(\mathbb R)$:

$$
A\ \text{invertibile}\iff\det A\ne0 \qquad(\text{cioè }A\text{ non singolare}).
$$

Si aggiunge così una condizione equivalente alle (i)–(vii) del Teorema 4: $\det A\neq0\iff r(A)=n$. Motivo: le operazioni di Gauss trasformano $\det$ al più per un fattore non nullo, e una forma a scala ha $\det=$ prodotto dei pivot, non nullo se e solo se ci sono $n$ pivot.

Conseguenza per il sistema omogeneo: $A\underline x=\underline0$ ha soluzione unica (quella banale) $\iff\det A\ne0$. Per un sistema con parametro, il valore del parametro che annulla $\det A$ è **l'unico candidato** in cui cambia la natura delle soluzioni: va studiato a parte con Rouché–Capelli.

**Esempio (parametro).** $A=\begin{bmatrix}1&0&3\\-1&1&0\\2&1&-\alpha\end{bmatrix}$; sviluppando lungo la terza colonna:

$$
\det A=3\begin{vmatrix}-1&1\\2&1\end{vmatrix}+0-\alpha\begin{vmatrix}1&0\\-1&1\end{vmatrix}=3(-3)-\alpha(1)=-9-\alpha .
$$

$\det A=0\iff\alpha=-9$. Dunque $A\underline x=\underline b$ ha **soluzione unica** ($|\mathrm{Sol}|=1$) $\iff\alpha\ne-9$; per $\alpha=-9$ si ha $r(A)<3$ e servono Rouché–Capelli e il confronto con $r(A')$.

## Inversa con i complementi algebrici

Sia $C=(C_{ij})$ la **matrice dei complementi algebrici** e $\operatorname{adj}(A):=C^{\mathsf T}$ la **(aggiunta classica)**. Allora

$$
A\cdot\operatorname{adj}(A)=\operatorname{adj}(A)\cdot A=(\det A)\,I_n\qquad\Longrightarrow\qquad \boxed{A^{-1}=\frac{1}{\det A}\,C^{\mathsf T}}\quad(\det A\ne0).
$$

*Perché.* L'elemento $(i,i)$ di $A\operatorname{adj}(A)$ è $\sum_j a_{ij}C_{ij}=\det A$ (Laplace lungo la riga $i$). L'elemento $(i,k)$ con $i\ne k$ è $\sum_j a_{ij}C_{kj}$: è lo sviluppo di Laplace della matrice ottenuta da $A$ sostituendo la riga $k$ con la riga $i$; ha due righe uguali, quindi vale $0$. $\blacksquare$

Attenzione alla **trasposizione**: il cofattore $C_{ij}$ va nella posizione $(j,i)$.

Per $n=2$ ritrova la formula nota: $C=\begin{bmatrix}d&-c\\-b&a\end{bmatrix}$, $C^{\mathsf T}=\begin{bmatrix}d&-b\\-c&a\end{bmatrix}$.

Per $n\ge3$ il metodo è più costoso di Gauss–Jordan (vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Eliminazione di Gauss-Jordan e calcolo della matrice inversa.md|Eliminazione di Gauss-Jordan]]): $\sim n^2$ determinanti di ordine $n-1$ contro $O(n^3)$ operazioni. Ha però il vantaggio di dare una formula **simbolica** (utile con parametri).

## Regola di Cramer (formula risolutiva)

Nella nota [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari quadrati e teorema di Cramer.md|Teorema di Cramer]] si è visto *che* esiste un'unica soluzione se $r(A)=n$. Col determinante si ottiene anche **la formula**.

**Teorema (regola di Cramer).** Sia $A\in M_n(\mathbb R)$ con $\det A\ne0$ e $A\underline x=\underline b$. Indicata con $A_i$ la matrice ottenuta da $A$ **sostituendo la $i$-esima colonna con la colonna dei termini noti** $\underline b$, la soluzione è

$$
x_i=\frac{\det A_i}{\det A},\qquad i=1,\dots,n.
$$

*Dimostrazione.* $\underline x=A^{-1}\underline b$, quindi $x_i=\frac1{\det A}\sum_j C_{ji}\,b_j$. La somma $\sum_j b_jC_{ji}$ è lo sviluppo di Laplace lungo la colonna $i$ della matrice $A_i$ (i cofattori della colonna $i$ non dipendono da quella colonna): vale $\det A_i$. $\blacksquare$

**Esempio.** $A=\begin{bmatrix}1&2&1\\1&1&1\\3&-1&1\end{bmatrix}$, $\underline b=\begin{bmatrix}4\\0\\-1\end{bmatrix}$.

$\det A=1\begin{vmatrix}1&1\\-1&1\end{vmatrix}-2\begin{vmatrix}1&1\\3&1\end{vmatrix}+1\begin{vmatrix}1&1\\3&-1\end{vmatrix}=2+4-4=2\ne0$, quindi la soluzione è unica e

$$
x_1=\frac{\begin{vmatrix}4&2&1\\0&1&1\\-1&-1&1\end{vmatrix}}{2}=\frac72,\quad
x_2=\frac{\begin{vmatrix}1&4&1\\1&0&1\\3&-1&1\end{vmatrix}}{2}=\frac82=4,\quad
x_3=\frac{\begin{vmatrix}1&2&4\\1&1&0\\3&-1&-1\end{vmatrix}}{2}=-\frac{15}2 .
$$

Verifica: $\tfrac72+8-\tfrac{15}2=4$ ✓; $\tfrac72+4-\tfrac{15}2=0$ ✓; $\tfrac{21}2-4-\tfrac{15}2=-1$ ✓.

> La regola di Cramer è elegante ma poco efficiente per $n$ grande: per risolvere un sistema numerico Gauss è molto più rapido.

## Rango e minori

Per $A\in M_{m,n}(\mathbb R)$ il rango si può definire in due modi **equivalenti**:

1. $r(A)=$ numero di **pivot** di una forma a scala (metodo di Gauss);
2. $r(A)=$ **massimo ordine di un minore non nullo**, dove qui *minore di ordine $k$* = determinante di una sottomatrice $k\times k$ ottenuta scegliendo $k$ righe e $k$ colonne di $A$ (esistenza di un minore non nullo di ordine $k$, e tutti quelli di ordine $k+1$ nulli).

Uso pratico: se $\det A=0$ ($A$ quadrata $3\times3$) allora $r(A)\le2$; se trovo un minore $2\times2$ non nullo, $r(A)=2$ esattamente.

## Sistemi con $\det A=0$: riduzione a un sistema di Cramer

Se $A$ è quadrata con $\det A=0$ e $r(A)=r<n$ (sistema compatibile):

1. si **eliminano** le $n-r$ equazioni dipendenti dalle altre (combinazioni lineari: non cambiano l'insieme delle soluzioni);
2. si scelgono $n-r$ incognite come **parametri** (con un minore $r\times r$ non nullo sulle restanti colonne);
3. si porta a destra il contributo dei parametri e si applica Cramer al sistema $r\times r$ ottenuto, che ha $\det\ne0$;
4. le soluzioni sono $\infty^{\,n-r}$.

Un esempio completo è nella nota [[Politecnico/Geometria e Algebra Lineare/Esercizi/Determinanti, Cramer e inversa — Esercizi svolti.md|Determinanti, Cramer e inversa — Esercizi svolti]] (Esercizio 5).

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari quadrati e teorema di Cramer.md|Sistemi lineari quadrati e teorema di Cramer]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Eliminazione di Gauss-Jordan e calcolo della matrice inversa.md|Eliminazione di Gauss-Jordan e calcolo della matrice inversa]]
- [[Politecnico/Geometria e Algebra Lineare/Esercizi/Rango, sottospazi, combinazioni lineari e indipendenza — Appunti ed esercizi.md|Esercizi — Rango, sottospazi, combinazioni lineari]]
