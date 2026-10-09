---
tags:
  - geometria-algebra-lineare
  - basi
  - dimensione
  - coordinate
  - algebra-lineare
---
## Basi, dimensione e coordinate

### Base di uno spazio vettoriale

Sia $V$ uno spazio vettoriale su $\mathbb K$. Un insieme ordinato $\mathcal B=(\mathbf v_1,\dots,\mathbf v_n)$ di vettori di $V$ è una **base** se:

1. **genera** $V$: $\operatorname{span}(\mathbf v_1,\dots,\mathbf v_n)=V$ (vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Combinazioni lineari e sottospazio generato.md|Combinazioni lineari e sottospazio generato]]);
2. è **linearmente indipendente**: $\lambda_1\mathbf v_1+\dots+\lambda_n\mathbf v_n=\mathbf 0\Rightarrow\lambda_1=\dots=\lambda_n=0$.

**Teorema (coordinate).** $\mathcal B$ è una base $\iff$ ogni $\mathbf v\in V$ si scrive in **un unico modo**
$$\mathbf v=c_1\mathbf v_1+\dots+c_n\mathbf v_n,\qquad c_i\in\mathbb K.$$

*Dimostrazione.* Esistenza = generazione. Unicità: se $\sum c_i\mathbf v_i=\sum c_i'\mathbf v_i$ allora $\sum(c_i-c_i')\mathbf v_i=\mathbf 0$, quindi per indipendenza $c_i=c_i'$. Viceversa, l'unicità della scrittura di $\mathbf 0$ è proprio l'indipendenza. $\square$

I coefficienti $(c_1,\dots,c_n)$ sono le **coordinate** (o componenti) di $\mathbf v$ rispetto a $\mathcal B$:
$$[\mathbf v]_{\mathcal B}:=\begin{pmatrix}c_1\\\vdots\\c_n\end{pmatrix}\in\mathbb K^n.$$
Cambiando la base cambiano le coordinate dello stesso vettore (stesso fenomeno dei sistemi di riferimento, vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi di riferimento nel piano.md|Sistemi di riferimento nel piano]]).

**Base canonica di $\mathbb K^n$:** $\mathbf e_1=(1,0,\dots,0),\ \dots,\ \mathbf e_n=(0,\dots,0,1)$. Rispetto ad essa le coordinate di $\mathbf x\in\mathbb K^n$ coincidono con le sue componenti: $\mathbf x=x_1\mathbf e_1+\dots+x_n\mathbf e_n$.

### Dimensione

**Teorema (Steinitz / invarianza del numero di elementi di una base).** Se $V$ ha una base di $n$ elementi, allora **ogni** base di $V$ ha $n$ elementi. Questo numero si chiama **dimensione** di $V$: $\dim V=n$ ($\dim\{\mathbf 0\}=0$).

*Idea della dimostrazione.* Lemma di scambio: in uno spazio generato da $n$ vettori, ogni insieme con più di $n$ vettori è linearmente dipendente (sistema omogeneo con più incognite che equazioni, che ha soluzioni non banali per Rouché–Capelli). Quindi due basi, essendo ciascuna indipendente e generatrice, hanno cardinalità $\le$ l'una dell'altra. $\square$

**Conseguenze utili** (se $\dim V=n$):
- $n+1$ vettori (o più) sono sempre dipendenti; meno di $n$ vettori non generano $V$;
- $n$ vettori sono una base $\iff$ sono indipendenti $\iff$ generano $V$ (basta verificare **una** delle due);
- se $W\le V$ allora $\dim W\le\dim V$, con uguaglianza $\iff W=V$.

### Esempio fondamentale: $M_{\mathbb K}(m,n)$ ha dimensione $mn$

Lo spazio $M_{\mathbb K}(m,n)$ delle matrici $m\times n$ (somma e prodotto per scalare componente per componente) ha come base le **matrici elementari** $E_{ij}$ ($1\le i\le m,\ 1\le j\le n$): $E_{ij}$ ha $1$ al posto $(i,j)$ e $0$ altrove. Infatti
$$A=(a_{ij})=\sum_{i,j}a_{ij}E_{ij}\quad\text{(unica scrittura)}.$$
Gli $E_{ij}$ sono $mn$, quindi
$$\boxed{\dim M_{\mathbb K}(m,n)=mn.}$$

**Caso $2\times2$.**
$$\begin{pmatrix}a&b\\c&d\end{pmatrix}=a\begin{pmatrix}1&0\\0&0\end{pmatrix}+b\begin{pmatrix}0&1\\0&0\end{pmatrix}+c\begin{pmatrix}0&0\\1&0\end{pmatrix}+d\begin{pmatrix}0&0\\0&1\end{pmatrix},\qquad\dim=4.$$
Le coordinate rispetto a $(E_{11},E_{12},E_{21},E_{22})$ sono $(a,b,c,d)$: $M_{\mathbb K}(2,2)\cong\mathbb K^4$.

### Esempio: matrici simmetriche $2\times2$

Sia $V=M_{\mathbb K}(2,2)$ e
$$W=\{A\in V:\ A^{\mathsf T}=A\}\quad\text{(matrici simmetriche).}$$

**$W$ è un sottospazio.** Se $A,B\in W$ e $\alpha,\beta\in\mathbb K$:
$$(\alpha A+\beta B)^{\mathsf T}=\alpha A^{\mathsf T}+\beta B^{\mathsf T}=\alpha A+\beta B\ \Rightarrow\ \alpha A+\beta B\in W$$
(e $0\in W$). Sfrutta la linearità della trasposizione.

**Descrizione esplicita.** $A^{\mathsf T}=A\iff b=c$, quindi
$$W=\left\{\begin{pmatrix}a&b\\b&d\end{pmatrix}:\ a,b,d\in\mathbb K\right\}
=\left\{a\begin{pmatrix}1&0\\0&0\end{pmatrix}+d\begin{pmatrix}0&0\\0&1\end{pmatrix}+b\begin{pmatrix}0&1\\1&0\end{pmatrix}\right\}.$$
Le tre matrici generano $W$ e sono indipendenti (la combinazione è la matrice nulla solo con $a=b=d=0$): sono una **base** di $W$, quindi $\dim W=3$.

**Una base diversa.** Anche
$$\mathcal B'=\left(\underbrace{\begin{pmatrix}1&0\\0&-1\end{pmatrix}}_{B_1},\ \underbrace{\begin{pmatrix}1&0\\0&1\end{pmatrix}}_{B_2},\ \underbrace{\begin{pmatrix}0&1\\1&0\end{pmatrix}}_{B_3}\right)$$
è una base di $W$. Per trovare le coordinate di $\begin{pmatrix}a&b\\b&d\end{pmatrix}$ si impone
$$c_1B_1+c_2B_2+c_3B_3=\begin{pmatrix}c_1+c_2&c_3\\c_3&c_2-c_1\end{pmatrix}=\begin{pmatrix}a&b\\b&d\end{pmatrix}
\iff\begin{cases}c_1+c_2=a\\c_3=b\\c_2-c_1=d\end{cases}$$
(la condizione $c_3=b=c$ è la simmetria). Il sistema ha **un'unica** soluzione:
$$c_1=\frac{a-d}{2},\qquad c_2=\frac{a+d}{2},\qquad c_3=b.$$
L'esistenza e unicità per ogni $(a,b,d)$ prova che $\mathcal B'$ è base. In forma matriciale il sistema è $M\mathbf c=(a,b,d)^{\mathsf T}$ con
$$M=\begin{pmatrix}1&1&0\\0&0&1\\-1&1&0\end{pmatrix},$$
e $\mathcal B'$ è base $\iff M$ è invertibile (sviluppando lungo la seconda riga, $\det M=-1\cdot\det\begin{pmatrix}1&1\\-1&1\end{pmatrix}=-2\ne0$). Si risolve con Gauss–Jordan (vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Eliminazione di Gauss-Jordan e calcolo della matrice inversa.md|Gauss-Jordan]]).

> **Metodo generale.** Per trovare le coordinate di $\mathbf v$ rispetto a una base $\mathcal B=(\mathbf v_1,\dots,\mathbf v_n)$ di $V\cong\mathbb K^n$: si risolve $c_1\mathbf v_1+\dots+c_n\mathbf v_n=\mathbf v$, cioè il sistema lineare $[\mathbf v_1|\cdots|\mathbf v_n]\,\mathbf c=\mathbf v$. La base garantisce soluzione esistente e unica.

### Isomorfismi

Una mappa lineare **biiettiva** $\ell:V\to W$ è un **isomorfismo** ($V\cong W$): trasporta basi in basi e conserva tutta la struttura (la sua inversa è lineare, vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni lineari, nucleo e immagine.md|Applicazioni lineari, nucleo e immagine]]).

**Teorema (coordinate come isomorfismo).** Se $\mathcal B$ è una base di $V$ con $\dim V=n$, la mappa
$$\kappa_{\mathcal B}:V\to\mathbb K^n,\qquad\mathbf v\mapsto[\mathbf v]_{\mathcal B}$$
è un isomorfismo. Dunque **ogni spazio di dimensione $n$ su $\mathbb K$ è isomorfo a $\mathbb K^n$**, e
$$V\cong W\iff\dim V=\dim W\quad(\text{dimensione finita}).$$
Per questo il calcolo in qualunque spazio di dimensione finita si riduce a calcoli in $\mathbb K^n$ (es. $M_{\mathbb K}(2,2)\cong\mathbb K^4$, $W\cong\mathbb K^3$ nell'esempio sopra).

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Combinazioni lineari e sottospazio generato.md|Combinazioni lineari e sottospazio generato]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni lineari, nucleo e immagine.md|Applicazioni lineari, nucleo e immagine]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Teorema di rappresentazione e matrice rappresentativa.md|Teorema di rappresentazione e matrice rappresentativa]]
