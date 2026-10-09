---
tags:
  - geometria-algebra-lineare
  - applicazioni-lineari
  - matrice-rappresentativa
  - teorema-di-rappresentazione
  - algebra-lineare
---
## Teorema di rappresentazione e matrice rappresentativa

### Enunciato (caso $\mathbb K^n\to\mathbb K^m$)

**Teorema.** Per ogni mappa lineare $\ell:\mathbb K^n\to\mathbb K^m$ esiste una matrice $A\in M_{\mathbb K}(m,n)$ tale che
$$\ell=\ell_A,\qquad\text{cioè}\qquad\ell(\mathbf x)=A\mathbf x\quad\forall\,\mathbf x\in\mathbb K^n.$$
La matrice $A$ è **unica** ed è detta **matrice rappresentativa** di $\ell$ (rispetto alle basi canoniche).

La mappa $\ell_A$ (vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni lineari, nucleo e immagine.md|Applicazioni lineari, nucleo e immagine]]) è quella che associa a $\mathbf x\in\mathbb K^n$ il vettore $A\mathbf x\in\mathbb K^m$. Il teorema dice che questo esempio è **l'unico**: le mappe lineari $\mathbb K^n\to\mathbb K^m$ sono esattamente le $\ell_A$, e
$$M_{\mathbb K}(m,n)\ \longleftrightarrow\ \{\text{mappe lineari }\mathbb K^n\to\mathbb K^m\},\qquad A\mapsto\ell_A$$
è una biiezione (anzi un isomorfismo di spazi vettoriali).

### Dimostrazione e costruzione di $A$

Siano $\mathbf e_1,\dots,\mathbf e_n$ la base canonica di $\mathbb K^n$. Ogni $\mathbf x=\sum_j x_j\mathbf e_j$, quindi per linearità
$$\ell(\mathbf x)=\sum_{j=1}^n x_j\,\ell(\mathbf e_j).$$
Definiamo $A$ mettendo come **$j$-esima colonna** il vettore $\ell(\mathbf e_j)\in\mathbb K^m$:
$$A=\Big[\ \ell(\mathbf e_1)\ \Big|\ \ell(\mathbf e_2)\ \Big|\ \cdots\ \Big|\ \ell(\mathbf e_n)\ \Big]\in M_{\mathbb K}(m,n).$$
Poiché $A\mathbf x=x_1A^1+\dots+x_nA^n$ (combinazione lineare delle colonne), si ha $A\mathbf x=\sum_jx_j\ell(\mathbf e_j)=\ell(\mathbf x)$. Unicità: se $A\mathbf x=B\mathbf x$ per ogni $\mathbf x$, ponendo $\mathbf x=\mathbf e_j$ le colonne coincidono, quindi $A=B$. $\square$

> **Regola pratica.** *Le colonne della matrice rappresentativa sono le immagini dei vettori della base canonica.* Una mappa lineare è determinata dai valori sulla base.

**Esempio.** $\ell:\mathbb R^3\to\mathbb R^2$, $\ell(x,y,z)=(x+2y,\ y-z)$. Allora $\ell(\mathbf e_1)=(1,0)$, $\ell(\mathbf e_2)=(2,1)$, $\ell(\mathbf e_3)=(0,-1)$, quindi
$$A=\begin{pmatrix}1&2&0\\0&1&-1\end{pmatrix}.$$

### Conseguenze: nucleo, immagine, rango

Per $\ell=\ell_A$:
- $\ker\ell=\{\mathbf x:A\mathbf x=\mathbf 0\}$ (sistema omogeneo);
- $\operatorname{im}\ell=\operatorname{span}(\text{colonne di }A)$, quindi $\dim\operatorname{im}\ell=\operatorname{rk}A$;
- $\ell$ iniettiva $\iff\operatorname{rk}A=n$; suriettiva $\iff\operatorname{rk}A=m$.

**Teorema delle dimensioni (rango–nullità).** Per $\ell:V\to W$ lineare con $\dim V$ finita,
$$\dim V=\dim\ker\ell+\dim\operatorname{im}\ell,$$
cioè, per $A\in M(m,n)$: $n=\dim\ker A+\operatorname{rk}A$.

### Caso generale: basi qualsiasi

Sia $\ell:V\to W$ lineare, $\mathcal B=(\mathbf v_1,\dots,\mathbf v_n)$ base di $V$, $\mathcal C$ base di $W$ ($\dim W=m$). La **matrice rappresentativa** $M_{\mathcal C}^{\mathcal B}(\ell)\in M(m,n)$ ha come $j$-esima colonna le **coordinate** di $\ell(\mathbf v_j)$ rispetto a $\mathcal C$:
$$M_{\mathcal C}^{\mathcal B}(\ell)=\Big[\ [\ell(\mathbf v_1)]_{\mathcal C}\ \Big|\ \cdots\ \Big|\ [\ell(\mathbf v_n)]_{\mathcal C}\ \Big].$$
Vale
$$[\ell(\mathbf v)]_{\mathcal C}=M_{\mathcal C}^{\mathcal B}(\ell)\,[\mathbf v]_{\mathcal B}\quad\forall\mathbf v\in V,$$
cioè il diagramma $V\xrightarrow{\ \ell\ }W$, $\ \mathbb K^n\xrightarrow{\ \ell_A\ }\mathbb K^m$ (con le frecce verticali $\kappa_{\mathcal B},\kappa_{\mathcal C}$, isomorfismi di coordinate) **commuta**. Il caso precedente è $V=\mathbb K^n$, $W=\mathbb K^m$ con basi canoniche.

**Procedura per calcolarla:**
1. calcolare $\ell(\mathbf v_j)$ per ogni vettore della base di partenza;
2. esprimere ciascuno in coordinate rispetto a $\mathcal C$ (risolvendo un sistema lineare, vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Basi, dimensione e coordinate.md|Basi, dimensione e coordinate]]);
3. incolonnare i risultati.

**Composizione.** $M^{\mathcal B}_{\mathcal D}(g\circ f)=M^{\mathcal C}_{\mathcal D}(g)\,M^{\mathcal B}_{\mathcal C}(f)$: la composizione corrisponde al prodotto di matrici. Inoltre $\ell$ è un isomorfismo $\iff$ la matrice rappresentativa è quadrata invertibile, e $M(\ell^{-1})=M(\ell)^{-1}$.

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni lineari, nucleo e immagine.md|Applicazioni lineari, nucleo e immagine]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Basi, dimensione e coordinate.md|Basi, dimensione e coordinate]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]
