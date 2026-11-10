---
tags:
  - geometria-algebra-lineare
  - determinante
  - binet
  - cramer
  - kronecker
  - rango
  - matrice-inversa
---
# Applicazioni dei determinanti — Binet, inversa, Cramer, Kronecker

Fonte: Lezione 9, parte 2 (nel PDF intitolata "Lezione 10"), pp. 1–31. Libro: ALG §§5–7, pp. 271–281.
Prerequisito: [[Determinante — definizione, proprietà e sviluppi di Laplace]].

## 1. Determinante, invertibilità, rango, indipendenza

> [!important] Teorema 1 (condizioni equivalenti)
> Sia $A$ quadrata di ordine $n$. Sono equivalenti:
> - (a) $A$ è **invertibile**;
> - (b) $\det A\neq0$;
> - (c) $r(A)=n$ (rango massimo);
> - (d) le **righe** di $A$ sono linearmente indipendenti;
> - (e) le **colonne** di $A$ sono linearmente indipendenti;
> - (f) $A\underline x=\underline0$ ha solo la soluzione banale $\underline x=\underline0\in\mathbb K^n$;
> - (g) $\exists\,\underline b\in\mathbb K^n$ t.c. $A\underline x=\underline b$ ha un'unica soluzione;
> - (h) $\forall\,\underline b\in\mathbb K^n$, $A\underline x=\underline b$ ha un'unica soluzione;
> - (i) la mappa $L_A:\mathbb K^n\to\mathbb K^n$, $L_A(\underline x)=A\underline x$ è **iniettiva**;
> - (j) $L_A$ è **suriettiva**;
> - (k) $L_A$ è **biiettiva**.

Oss.: (f), (g), (h) sono equivalenti **solo per matrici quadrate**; l'unica soluzione in (g), (h) è $\underline x=A^{-1}\underline b$.

**Conseguenza utile.** Se $A$ ha una riga (o colonna) **nulla**, oppure una riga (colonna) **multipla di un'altra**, allora $\det A=0$.

**Esempi.**
- $\begin{bmatrix}1\\2\end{bmatrix}$, $\begin{bmatrix}3\\6\end{bmatrix}=3\begin{bmatrix}1\\2\end{bmatrix}$ dipendenti ⇒ $\begin{vmatrix}1&3\\2&6\end{vmatrix}=6-6=0$, e $r=1<2$.
- $\begin{vmatrix}0&1&0\\1&1&1\\0&1&0\end{vmatrix}=0$ (due righe uguali).
- $\begin{vmatrix}1&2&3&4\\6&7&0&5\\2&4&6&8\\3&7&9&11\end{vmatrix}=0$ (3ª riga $=2\cdot$1ª).
- $\begin{vmatrix}1&2&3\\4&5&6\\7&8&9\end{vmatrix}\overset{\substack{R_2-R_1\\R_3-R_1}}{=}\begin{vmatrix}1&2&3\\3&3&3\\6&6&6\end{vmatrix}=0$ (3ª riga $=2\cdot$2ª).

### Corollario 1 (basi di $\mathbb K^n$)

> [!important] Corollario 1
> $n$ vettori $\underline v_1,\dots,\underline v_n\in\mathbb K^n$ formano una **base** di $\mathbb K^n$ $\iff$ $\det A\neq0$, dove $A=[\underline v_1|\cdots|\underline v_n]$.

Poiché $\det A=\det A^T$, si possono mettere i vettori anche come **righe**.

**Esempio.** Quali sono basi di $\mathbb R^3$?
$\mathcal B_1=\{(1,2,0),(0,2,3),(1,0,3)\}$, $\mathcal B_2=\{(1,2,3),(3,2,1),(1,1,1)\}$, $\mathcal B_3$ con 4 vettori, $\mathcal B_4$ con 2 vettori.

- $\dim\mathbb R^3=3$: $\mathcal B_3$, $\mathcal B_4$ **non** sono basi (numero sbagliato).
- $\mathcal B_1$: $\begin{vmatrix}1&2&0\\0&2&3\\1&0&3\end{vmatrix}=6+6=12\neq0$ ⇒ **base**.
- $\mathcal B_2$: $\begin{vmatrix}1&2&3\\3&2&1\\1&1&1\end{vmatrix}\overset{\substack{R_1-2R_3\\R_2-2R_3}}{=}\begin{vmatrix}-1&0&1\\1&0&-1\\1&1&1\end{vmatrix}\overset{\text{2ª col.}}{=}-1\cdot\begin{vmatrix}-1&1\\1&-1\end{vmatrix}=0$ ⇒ **non** è base.

**Esempio in $\mathbb C^4$.** $\mathcal B=\{(1,1,i,1),(0,i,0,-i),(i,0,1,0),(0,1,0,1)\}$:
$$\begin{vmatrix}1&0&i&0\\1&i&0&1\\i&0&1&0\\1&-i&0&1\end{vmatrix}\overset{R_3\to R_3-iR_1}{=}\begin{vmatrix}1&0&i&0\\1&i&0&1\\0&0&2&0\\1&-i&0&1\end{vmatrix}\overset{\text{3ª riga}}{=}2\begin{vmatrix}1&0&0\\1&i&1\\1&-i&1\end{vmatrix}=2\begin{vmatrix}i&1\\-i&1\end{vmatrix}=4i\neq0$$
⇒ $\mathcal B$ è base di $\mathbb C^4$.

## 2. Teorema di Binet

> [!important] Teorema 2 (Binet)
> Se $A,B$ sono quadrate dello stesso ordine:
> $$\det(AB)=\det A\cdot\det B=\det(BA).$$
> In particolare, se $A$ è invertibile: $\displaystyle\det(A^{-1})=\frac1{\det A}$ (da $AA^{-1}=I$, $\det I=1$).

> [!warning] Non vale per la somma
> In generale $\det(A+B)\neq\det A+\det B$.

**Esempio.** $A$ invertibile $3\times3$ con $BA^{-1}=C$, $B=\begin{bmatrix}1&2&3\\0&4&5\\0&0&6\end{bmatrix}$, $C=\begin{bmatrix}1&0&0\\1&2&0\\1&2&3\end{bmatrix}$. Trovare $\det A$.

$\det B\cdot\det(A^{-1})=\det C\Rightarrow\frac{\det B}{\det A}=\det C\Rightarrow\det A=\frac{\det B}{\det C}=\frac{1\cdot4\cdot6}{1\cdot2\cdot3}=\frac{24}6=4.$

(Trovato $\det A$ senza trovare $A$.)

## 3. Formula di Laplace per l'inversa

Sia $A$ invertibile (per semplicità $3\times3$; vale per ogni $n$) e $C=[C_{ij}]$ la **matrice dei complementi algebrici**, $C_{ij}=(-1)^{i+j}\det A_{ij}$.

Posto $\lambda_{ik}:=\sum_j a_{ij}C_{kj}$ (riga $i$ di $A$ "per" riga $k$ di $C$):
- $\lambda_{ii}=a_{i1}C_{i1}+a_{i2}C_{i2}+a_{i3}C_{i3}=\det A$ (Laplace lungo la riga $i$);
- $\lambda_{ik}=0$ per $i\neq k$: è lo sviluppo di Laplace di una matrice $A'$ che ha la riga $k$ sostituita con la riga $i$. I cofattori di una riga **non dipendono** dagli elementi di quella riga, quindi coincidono con quelli di $A$; $A'$ ha due righe uguali ⇒ $\det A'=0$.

Esempio: $\lambda_{12}=a_{11}C_{21}+a_{12}C_{22}+a_{13}C_{23}=\begin{vmatrix}a_{11}&a_{12}&a_{13}\\a_{11}&a_{12}&a_{13}\\a_{31}&a_{32}&a_{33}\end{vmatrix}=0$.

Quindi $AC^T=[\lambda_{ik}]=\det A\cdot I$ e:

> [!important] Formula di Laplace per l'inversa
> $$A^{-1}=\frac1{\det A}\,C^T,\qquad\text{cioè}\qquad(A^{-1})_{ji}=\frac{C_{ij}}{\det A}.$$

**Esempio.** Inversa di $A=\begin{bmatrix}1&1&1\\2&3&4\\0&1&0\end{bmatrix}$.

Cofattori:
$$C=\begin{bmatrix}+\begin{vmatrix}3&4\\1&0\end{vmatrix}&-\begin{vmatrix}2&4\\0&0\end{vmatrix}&+\begin{vmatrix}2&3\\0&1\end{vmatrix}\\[1mm]-\begin{vmatrix}1&1\\1&0\end{vmatrix}&+\begin{vmatrix}1&1\\0&0\end{vmatrix}&-\begin{vmatrix}1&1\\0&1\end{vmatrix}\\[1mm]+\begin{vmatrix}1&1\\3&4\end{vmatrix}&-\begin{vmatrix}1&1\\2&4\end{vmatrix}&+\begin{vmatrix}1&1\\2&3\end{vmatrix}\end{bmatrix}=\begin{bmatrix}-4&0&2\\1&0&-1\\1&-2&1\end{bmatrix}.$$
$\det A$ lungo la 1ª riga: $(1,1,1)\cdot(-4,0,2)=-2\neq0$ ⇒ invertibile.
$$A^{-1}=-\frac12\begin{bmatrix}-4&1&1\\0&0&-2\\2&-1&1\end{bmatrix}=\begin{bmatrix}2&-\frac12&-\frac12\\0&0&1\\-1&\frac12&-\frac12\end{bmatrix}.$$

## 4. Regola di Cramer

> [!important] Teorema 3 (regola di Cramer)
> Sia $A$ quadrata $n\times n$ con $\det A\neq0$, $\underline b\in\mathbb K^n$ qualsiasi. L'unica soluzione di $A\underline x=\underline b$ è $\underline x=(x_1,\dots,x_n)$ con
> $$x_j=\frac{\det(A_j)}{\det A},\qquad j=1,\dots,n,$$
> dove $A_j$ = $A$ con la **$j$-esima colonna sostituita dal vettore $\underline b$**.

*Dim.* $\det A\neq0$ ⇒ $A$ invertibile ⇒ unica soluzione $\underline x=A^{-1}\underline b$, cioè $x_j=\sum_i(A^{-1})_{ji}b_i=\frac1{\det A}\sum_i C_{ij}b_i$. La somma $\sum_i C_{ij}b_i$ è lo sviluppo di Laplace di $\det A_j$ lungo la colonna $j$ (in $A_j$ la colonna $j$ è $\underline b$ e i cofattori di quella colonna sono gli stessi di $A$). $\blacksquare$

**Esempio.** $\begin{cases}x+y+z=4\\2x-y-z=-7\\-x+2y+z=8\end{cases}$, $A=\begin{bmatrix}1&1&1\\2&-1&-1\\-1&2&1\end{bmatrix}$, $\underline b=\begin{bmatrix}4\\-7\\8\end{bmatrix}$.

$\Delta=\det A\overset{R_2\to R_2+R_1}{=}\begin{vmatrix}1&1&1\\3&0&0\\-1&2&1\end{vmatrix}\overset{\text{2ª riga}}{=}-3\begin{vmatrix}1&1\\2&1\end{vmatrix}=3\neq0$ ⇒ soluzione unica.

- $\Delta_1=\begin{vmatrix}4&1&1\\-7&-1&-1\\8&2&1\end{vmatrix}\overset{C_2\to C_2-C_3}{=}\begin{vmatrix}4&0&1\\-7&0&-1\\8&1&1\end{vmatrix}=-\begin{vmatrix}4&1\\-7&-1\end{vmatrix}=-3$ ⇒ $x=\frac{-3}3=-1$.
- $\Delta_2=\begin{vmatrix}1&4&1\\2&-7&-1\\-1&8&1\end{vmatrix}\overset{R_2\to R_2+R_3}{=}\begin{vmatrix}1&4&1\\1&1&0\\-1&8&1\end{vmatrix}=-\begin{vmatrix}4&1\\8&1\end{vmatrix}+\begin{vmatrix}1&1\\-1&1\end{vmatrix}=4+2=6$ ⇒ $y=2$.
- $\Delta_3=\begin{vmatrix}1&1&4\\2&-1&-7\\-1&2&8\end{vmatrix}\to\begin{vmatrix}1&1&4\\0&-3&-15\\0&0&-3\end{vmatrix}=9$ ⇒ $z=3$.

Soluzione: $(x,y,z)=(-1,2,3)$.

## 5. Teorema di Kronecker (rango con i minori)

**Def (minori).** Un **minore di ordine $k$** di una matrice $M$ (non necessariamente quadrata) è il determinante di una sottomatrice $k\times k$ di $M$ (si scelgono $k$ righe e $k$ colonne).

**Def (orlare).** Un minore $\det B$ di ordine $p+1$ **orla** un minore $\det A$ di ordine $p$ se $A$ è sottomatrice di $B$ (si aggiunge una riga e una colonna).

**Esempio 1.** $M=\begin{bmatrix}1&2&3&4\\5&6&7&8\\9&0&-1&3\end{bmatrix}$. $A=\begin{bmatrix}1&3\\5&7\end{bmatrix}$ (righe 1,2; colonne 1,3) dà il minore $\det A=7-15=-8\neq0$. Il minore $\begin{vmatrix}1&3&4\\5&7&8\\9&-1&3\end{vmatrix}$ lo **orla**.

> [!important] Teorema 4 (Kronecker sul rango)
> Sia $M$ una matrice qualsiasi.
> - (a) Se $A$ è sottomatrice quadrata di $M$ con $\det A\neq0$, allora le **righe** di $M$ che contengono le righe di $A$ sono linearmente indipendenti, e così le **colonne** di $M$ che contengono le colonne di $A$.
> - (b) Se $M$ ha un minore non nullo di ordine $p$, allora $r(M)\ge p$.
> - (c) Ogni minore di $M$ di ordine $p>r(M)$ è nullo. ((c) ⇔ (b), entrambe da (a).)
> - (d) Se $M$ ha un minore $\delta$ di ordine $p$ con
>   1. $\delta\neq0$,
>   2. **ogni** minore di ordine $p+1$ che **orla** $\delta$ è nullo,
>
>   allora $r(M)=p$.

Inoltre le colonne di $M$ che contengono le colonne di $\delta$ formano una **base di $\operatorname{Im}(M)$** (perché sono indipendenti e $\dim\operatorname{Im}M=r(M)=p$).

> [!tip] Perché conviene
> Non serve controllare **tutti** i minori di ordine $p+1$, solo quelli che orlano $\delta$.

**Esempio 1 (continua).** $\delta=\begin{vmatrix}1&3&4\\5&7&8\\9&-1&3\end{vmatrix}=-72\neq0$, ordine $3$; minori di ordine $4$ non esistono ($M$ ha 3 righe). Quindi $r(M)=3$; le colonne 1, 3, 4 formano una base di $\operatorname{Im}(M)$.

**Esempio 2.** $M=\begin{bmatrix}1&2&3&4&5\\5&4&3&2&1\\1&1&1&1&1\end{bmatrix}$: trovare $r(M)$ e una base di $\operatorname{Im}(M)$.

$\delta=\begin{vmatrix}1&2\\5&4\end{vmatrix}=-6\neq0$, $p=2$. I minori di ordine $3$ che lo orlano:
$$\begin{vmatrix}1&2&3\\5&4&3\\1&1&1\end{vmatrix},\quad\begin{vmatrix}1&2&4\\5&4&2\\1&1&1\end{vmatrix},\quad\begin{vmatrix}1&2&5\\5&4&1\\1&1&1\end{vmatrix}$$
sono tutti nulli. Quindi $r(M)=2$ e una base di $\operatorname{Im}(M)$ è $\left\{\begin{bmatrix}1\\5\\1\end{bmatrix},\begin{bmatrix}2\\4\\1\end{bmatrix}\right\}$.

## Collegamenti
- Precedente: [[Determinante — definizione, proprietà e sviluppi di Laplace]]
- Successiva: [[Similitudine, potenze e interpretazione geometrica del determinante]]
- Riepilogo ed esercizi: [[Determinante, sviluppo di Laplace e formula di Cramer]] · [[Determinanti, Cramer e inversa — Esercizi svolti]]
- [[Matrici quadrate e matrice inversa]] · [[Sistemi lineari quadrati e teorema di Cramer]] · [[Rango e teorema di nullità più rango]] · [[Basi, dimensione e coordinate]]
- PDF: [[09 parte 2. Applicazioni dei determinanti - Invertibilita e dipendenza lineare. Teorema di Binet. La formula di Laplace e regola di Cramer. Calcolo del rango di una matrice con il Teorema di Kronecker.pdf|Parte 2]]
