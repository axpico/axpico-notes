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

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Insiemi, vettori e sistemi lineari — nozioni di base.md|Insiemi, vettori e sistemi lineari — nozioni di base]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Equazioni matriciali.md|Equazioni matriciali]]
- [[Politecnico/Geometria e Algebra Lineare/Esercizi/Matrici — Esercizi svolti.md|Esercizi — Matrici]]
