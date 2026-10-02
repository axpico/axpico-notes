---
tags:
  - geometria-algebra-lineare
  - matrici
  - equazioni-matriciali
  - matrice-inversa
---
## Impostazione generale

Indichiamo con $M_{m,n}(K)$ l'insieme delle matrici $m\times n$ a elementi in un campo $K$ (tipicamente $K=\mathbb R$ o $K=\mathbb C$). Un'**equazione matriciale** è un'equazione in cui l'incognita non è un vettore $x\in K^n$ come nei sistemi lineari $Ax=b$, ma un'intera **matrice** incognita.

Le due forme più comuni, per $A \in M_{n,n}(K)$ **quadrata e invertibile**, sono:

$$
AX = B \qquad \text{e} \qquad YA = C,
$$

dove $X, B$ e $Y, C$ sono matrici (non necessariamente quadrate). La prima moltiplica l'incognita **a destra** di $A$, la seconda **a sinistra**: i due casi si risolvono in modo simmetrico ma **non identico**, perché il prodotto tra matrici non è commutativo.

### Compatibilità delle dimensioni

Se $A$ è $n\times n$:

- in $AX=B$: $X$ deve avere $n$ righe (tante quante le colonne di $A$); se $X$ è $n\times p$, allora $B$ è $n\times p$;
- in $YA=C$: $Y$ deve avere $n$ colonne (tante quante le righe di $A$); se $Y$ è $q\times n$, allora $C$ è $q \times n$.

In entrambi i casi le dimensioni di $B$ (risp. $C$) **determinano** quelle dell'incognita.

## Soluzione di $AX=B$

Se $A$ è **invertibile**, moltiplichiamo **a sinistra** entrambi i membri per $A^{-1}$:

$$
A^{-1}(AX) = A^{-1}B \ \overset{\text{associativa}}{\Longrightarrow}\ (A^{-1}A)X = A^{-1}B \ \Longrightarrow\ I_n X = A^{-1}B \ \Longrightarrow\ X = A^{-1}B.
$$

(Attenzione: bisogna moltiplicare **a sinistra** su entrambi i lati — moltiplicare a destra darebbe $AXA^{-1}$, che non si semplifica.)

Equivalentemente, se $X = [x_1\mid x_2\mid\cdots\mid x_p]$ e $B=[b_1\mid b_2\mid\cdots\mid b_p]$ sono scritte per colonne, l'equazione $AX=B$ equivale a $p$ sistemi lineari indipendenti $Ax_j = b_j$ (uno per ogni colonna), esattamente come nella costruzione dell'inversa vista in [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]].

## Soluzione di $YA=C$

Se $A$ è invertibile, moltiplichiamo **a destra** entrambi i membri per $A^{-1}$:

$$
(YA)A^{-1} = CA^{-1} \ \overset{\text{associativa}}{\Longrightarrow}\ Y(AA^{-1}) = CA^{-1} \ \Longrightarrow\ Y I_n = CA^{-1} \ \Longrightarrow\ Y = CA^{-1}.
$$

## Esempio completo

Sia $A = \begin{bmatrix}1&2\\3&4\end{bmatrix}$. Per il Teorema 5 (si veda [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]), $A$ è invertibile perché $ad-bc = 1\cdot4-2\cdot3=-2\ne0$, e

$$
A^{-1} = \frac{1}{-2}\begin{bmatrix}4&-2\\-3&1\end{bmatrix} = \begin{bmatrix}-2&1\\ \tfrac32&-\tfrac12\end{bmatrix}.
$$

### Caso $AX=B$

Risolviamo

$$
\begin{bmatrix}1&2\\3&4\end{bmatrix} X = \begin{bmatrix}1&3&5\\2&4&6\end{bmatrix}.
$$

Qui $A$ è $2\times2$ e $B$ è $2\times3$, quindi $X$ deve essere $2\times 3$ (compatibilità: colonne di $A$ = righe di $X$, cioè $2=2$; $B$ eredita le righe di $A$ e le colonne di $X$). Per la formula:

$$
X = A^{-1}B = \begin{bmatrix}-2&1\\ \tfrac32&-\tfrac12\end{bmatrix}\begin{bmatrix}1&3&5\\2&4&6\end{bmatrix} = \begin{bmatrix}-2\cdot1+1\cdot2 & -2\cdot3+1\cdot4 & -2\cdot5+1\cdot6\\ \tfrac32\cdot1-\tfrac12\cdot2 & \tfrac32\cdot3-\tfrac12\cdot4 & \tfrac32\cdot5-\tfrac12\cdot6\end{bmatrix} = \begin{bmatrix}0 & -2 & -4\\ \tfrac12 & \tfrac52 & \tfrac92\end{bmatrix}.
$$

**Verifica** ($AX$ deve ridare $B$):

$$
AX = \begin{bmatrix}1&2\\3&4\end{bmatrix}\begin{bmatrix}0&-2&-4\\ \tfrac12&\tfrac52&\tfrac92\end{bmatrix} = \begin{bmatrix}1\cdot0+2\cdot\tfrac12 & 1\cdot(-2)+2\cdot\tfrac52 & 1\cdot(-4)+2\cdot\tfrac92\\ 3\cdot0+4\cdot\tfrac12 & 3\cdot(-2)+4\cdot\tfrac52 & 3\cdot(-4)+4\cdot\tfrac92\end{bmatrix} = \begin{bmatrix}1&3&5\\2&4&6\end{bmatrix}=B. \ \checkmark
$$

### Caso $YA=C$

Risolviamo

$$
Y\begin{bmatrix}1&2\\3&4\end{bmatrix} = \begin{bmatrix}1&2\\3&4\\5&6\end{bmatrix}.
$$

Qui $C$ è $3\times2$, quindi $Y$ deve essere $3\times2$ (colonne di $Y$ = righe di $A$, cioè $2=2$; $C$ eredita le righe di $Y$ e le colonne di $A$). Per la formula:

$$
Y = CA^{-1} = \begin{bmatrix}1&2\\3&4\\5&6\end{bmatrix}\begin{bmatrix}-2&1\\ \tfrac32&-\tfrac12\end{bmatrix} = \begin{bmatrix}1\cdot(-2)+2\cdot\tfrac32 & 1\cdot1+2\cdot(-\tfrac12)\\ 3\cdot(-2)+4\cdot\tfrac32 & 3\cdot1+4\cdot(-\tfrac12)\\ 5\cdot(-2)+6\cdot\tfrac32 & 5\cdot1+6\cdot(-\tfrac12)\end{bmatrix} = \begin{bmatrix}1&0\\0&1\\-1&2\end{bmatrix}.
$$

**Verifica** ($YA$ deve ridare $C$):

$$
YA = \begin{bmatrix}1&0\\0&1\\-1&2\end{bmatrix}\begin{bmatrix}1&2\\3&4\end{bmatrix} = \begin{bmatrix}1&2\\3&4\\5&6\end{bmatrix}=C. \ \checkmark
$$

> **Nota sugli appunti originali.** Nella versione a mano il calcolo di $X$ era stato impostato correttamente (equazione $AX=B$, verifica di invertibilità di $A$, $A^{-1}$ corretta) ma **interrotto prima del risultato finale**; il caso $YA=C$ era solo abbozzato senza la formula risolutiva "a destra". Qui sopra sono riportati entrambi i calcoli per esteso, con verifica.

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Eliminazione di Gauss-Jordan e calcolo della matrice inversa.md|Eliminazione di Gauss-Jordan e calcolo della matrice inversa]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Teorema 6 — inversa di un prodotto $(AB)^{-1}=B^{-1}A^{-1}$]]
- [[Politecnico/Geometria e Algebra Lineare/Esercizi/Matrici — Esercizi svolti.md|Esercizi — Matrici]]
