---
tags:
  - geometria-algebra-lineare
  - basi
  - nucleo
  - immagine
---
## Basi di nucleo, immagine e span

↑ [[Politecnico/Geometria e Algebra Lineare/Indice|Indice]] · tappa 5 (Applicazioni lineari) · prima: [[Dipendenza lineare|Dipendenza lineare]] · dopo: [[Rango e teorema di nullità più rango|Rango e teorema di nullità più rango]]

> Fonte: [[06 Dipendenza lineare. Condizioni di una base. Basi di nucleo e di span. Rango di una matrice ed una mappa lineare. Teorema di nullita piu rango.pdf|Lezione 6 (PDF)]], pp. 41–62.

### 1. Il problema

Dato un sottospazio $W=\operatorname{span}\{\mathbf v_1,\dots,\mathbf v_n\}\subseteq V$, trovare **una base di $W$**.

**Definizione.** Se $W=\operatorname{span}\{\mathbf u_1,\dots,\mathbf u_n\}$, si dice che $\{\mathbf u_1,\dots,\mathbf u_n\}$ è un **insieme di generatori** di $W$.

> **Proposizione (sottosistema che è base dello span).** Sia $\mathcal B=\{\mathbf v_1,\dots,\mathbf v_n\}\subset V$ e $\mathcal B'\subseteq\mathcal B$ un sottosistema non vuoto. Allora $\mathcal B'$ è una base di $W:=\operatorname{span}(\mathcal B)$ se e solo se:
> 1. $\mathcal B'$ è linearmente indipendente;
> 2. $\mathcal B\subset\operatorname{span}(\mathcal B')$, cioè ogni vettore di $\mathcal B$ è combinazione lineare dei vettori di $\mathcal B'$.
>
> In particolare, se $\mathcal B$ è indipendente, è una base di $\operatorname{span}(\mathcal B)$.

### 2. Base dello span di vettori di $\mathbb K^m$

**Esempio.** Base e dimensione di $W=\operatorname{span}\{\mathbf v_1,\mathbf v_2,\mathbf v_3\}$, con
$$\mathbf v_1=\begin{pmatrix}1\\2\\1\end{pmatrix},\quad\mathbf v_2=\begin{pmatrix}2\\4\\2\end{pmatrix},\quad\mathbf v_3=\begin{pmatrix}1\\1\\1\end{pmatrix}.$$

**Soluzione 1 (a occhio).** $\mathbf v_2=2\mathbf v_1$, quindi $\{\mathbf v_1,\mathbf v_2,\mathbf v_3\}$ è dipendente e non è una base. Però $\mathcal B'=\{\mathbf v_1,\mathbf v_3\}$ è indipendente (non proporzionali) e $\mathbf v_2=2\mathbf v_1+0\mathbf v_3\in\operatorname{span}(\mathcal B')$. Per la Proposizione, $\mathcal B'$ è una base di $W$.

**Soluzione 2 (metodo generale: colonne pivot).** Si riduce a scala $A=[\mathbf v_1|\mathbf v_2|\mathbf v_3]$:
$$\begin{pmatrix}1&2&1\\2&4&1\\1&2&1\end{pmatrix}\xrightarrow[R_3\to R_3-R_1]{R_2\to R_2-2R_1}\begin{pmatrix}\boxed1&2&1\\0&0&\boxed{-1}\\0&0&0\end{pmatrix}.$$

> **Teorema (colonne pivot).** I vettori **originali** che corrispondono alle colonne con pivot della forma a scala formano una base dello span delle colonne.

Pivot nelle colonne 1 e 3, quindi una base di $W$ è $\{\mathbf v_1,\mathbf v_3\}$ e $\dim W=2$.

> **Attenzione:** si prendono le colonne della matrice **di partenza**, non quelle della forma a scala.

### 3. Base del nucleo di una matrice

**Esempio.** Base di $\ker(A)$, con $A=\begin{pmatrix}1&2&3&4\\2&4&5&9\end{pmatrix}$.

$\ker(A)$ è l'insieme delle soluzioni di $A\mathbf x=\mathbf 0$:
$$\begin{pmatrix}1&2&3&4\\2&4&5&9\end{pmatrix}\xrightarrow{R_2\to R_2-2R_1}\begin{pmatrix}\boxed1&2&3&4\\0&0&\boxed{-1}&1\end{pmatrix}\qquad\begin{cases}x_1+2x_2+3x_3+4x_4=0\\-x_3+x_4=0\end{cases}$$
Le variabili dipendenti (pivot) sono $x_1,x_3$, quelle libere $x_2=s$, $x_4=t$:
$$\mathbf x=\begin{pmatrix}-(2s+7t)\\s\\t\\t\end{pmatrix}=s\begin{pmatrix}-2\\1\\0\\0\end{pmatrix}+t\begin{pmatrix}-7\\0\\1\\1\end{pmatrix},\qquad s,t\in\mathbb K.$$

**Perché questi due vettori sono una base.** $\ker(A)$ è l'immagine della mappa
$$L:\mathbb K^2\to\mathbb K^4,\qquad L(s,t)=\bigl(-(2s+7t),\,s,\,t,\,t\bigr).$$
Per linearità $L(s\mathbf e_1+t\mathbf e_2)=sL(\mathbf e_1)+tL(\mathbf e_2)$, quindi $\ker(A)=\operatorname{im}L=\operatorname{span}\{L(\mathbf e_1),L(\mathbf e_2)\}$.
$L$ è **iniettiva**, perché $s$ e $t$ si leggono nella 2ª e 4ª componente. Le immagini di $L(\mathbf e_1),L(\mathbf e_2)$ tramite $L^{-1}:\operatorname{im}L\to\mathbb K^2$ sono $\mathbf e_1,\mathbf e_2$, che sono indipendenti. Per la Prop. 3 di [[Dipendenza lineare|Dipendenza lineare]], anche $L(\mathbf e_1),L(\mathbf e_2)$ sono indipendenti, e quindi sono una base.

> **Metodo pratico.** Una base di $\ker(A)$ si ottiene risolvendo $A\mathbf x=\mathbf 0$ assegnando a turno il valore $1$ a una variabile libera e $0$ alle altre.
> Qui $(x_2,x_4)=(1,0)$ dà $(-2,1,0,0)$, e $(x_2,x_4)=(0,1)$ dà $(-7,0,1,1)$.
> Quindi $\dim\ker(A)=\#$variabili libere $=2$.

*Verifica:* $A(-7,0,1,1)^{\mathsf T}=(-7+3+4,\ -14+5+9)^{\mathsf T}=(0,0)^{\mathsf T}$. ✓

### 4. Esempio completo: immagine e nucleo di $L:P_2\to\mathbb R^3$

$$L(p):=\bigl(p(0),\ p'(1),\ p''(0)+2p(1)\bigr).$$
Si chiede di (a) trovare base e dimensione di $\operatorname{im}L$; (b) stabilire se $\mathbf u=(-1,1,0)$ e $\mathbf v=(1,1,1)$ stanno in $\operatorname{im}L$ e, in caso affermativo, trovarne le coordinate; (c) trovare base e dimensione di $\ker L$; (d) dire se $L$ è iniettiva, suriettiva, biiettiva.

**(a) Immagine.** Con la base $p_k(x)=x^k$ ($k=0,1,2$), se $p=a_0p_0+a_1p_1+a_2p_2$ allora $L(p)=a_0L(p_0)+a_1L(p_1)+a_2L(p_2)$. Dunque
$$\operatorname{im}L=\operatorname{span}\{\mathbf v_0,\mathbf v_1,\mathbf v_2\},\qquad\mathbf v_k:=L(p_k).$$

> **Fatto generale.** Le immagini di una base del dominio sono un insieme di generatori di $\operatorname{im}L$. Non sono sempre una base, ma ne **contengono** sempre una.

$$\mathbf v_0=L(1)=\begin{pmatrix}1\\0\\2\end{pmatrix},\quad\mathbf v_1=L(x)=\begin{pmatrix}0\\1\\2\end{pmatrix},\quad\mathbf v_2=L(x^2)=\begin{pmatrix}0\\2\\4\end{pmatrix}.$$
$$A=\begin{pmatrix}1&0&0\\0&1&2\\2&2&4\end{pmatrix}\xrightarrow{R_3\to R_3-2R_1}\begin{pmatrix}1&0&0\\0&1&2\\0&2&4\end{pmatrix}\xrightarrow{R_3\to R_3-2R_2}\begin{pmatrix}\boxed1&0&0\\0&\boxed1&2\\0&0&0\end{pmatrix}.$$
I pivot sono nelle colonne 1 e 2, quindi una base di $\operatorname{im}L$ è $\{\mathbf v_0,\mathbf v_1\}$ e $\dim\operatorname{im}L=2$ (infatti $\mathbf v_2=2\mathbf v_1$).

**(b) Appartenenza all'immagine.** $\mathbf u\in\operatorname{im}L\iff$ il sistema $[\mathbf v_0|\mathbf v_1]\mathbf x=\mathbf u$ è compatibile:
$$\left(\begin{array}{cc|c}1&0&-1\\0&1&1\\2&2&0\end{array}\right)\to\left(\begin{array}{cc|c}1&0&-1\\0&1&1\\0&0&0\end{array}\right)\Rightarrow x_1=-1,\ x_2=1.$$
Quindi $\mathbf u\in\operatorname{im}L$, con coordinate $(-1,1)$ rispetto a $\{\mathbf v_0,\mathbf v_1\}$. Per $\mathbf v$:
$$\left(\begin{array}{cc|c}1&0&1\\0&1&1\\2&2&1\end{array}\right)\to\left(\begin{array}{cc|c}1&0&1\\0&1&1\\0&0&\boxed{-3}\end{array}\right):\quad 0=-3,\ \text{incompatibile}\Rightarrow\mathbf v\notin\operatorname{im}L.$$

**(c) Nucleo.** Si identifica $p=a_0+a_1x+a_2x^2$ con $(a_0,a_1,a_2)\in\mathbb R^3$. Allora $\ker L=\ker A$, con $A=[L(\mathbf e_1)|L(\mathbf e_2)|L(\mathbf e_3)]$, la stessa matrice di prima. Dalla forma a scala si ha $x_1=0$ e $x_2+2x_3=0$, con una variabile libera. Ponendo $x_3=1$:
$$\ker A=\operatorname{span}\left\{\begin{pmatrix}0\\-2\\1\end{pmatrix}\right\}\ \longleftrightarrow\ q(x)=x^2-2x.$$
Quindi una base di $\ker L$ è $\{q\}$ e $\dim\ker L=1$. *(Verifica: $q(0)=0$, $q'(1)=0$, $q''(0)+2q(1)=2-2=0$.)*

**(d)**
- **Non iniettiva**, perché $\ker L\neq\{\mathbf 0\}$ (vedi [[Applicazioni lineari, nucleo e immagine|nucleo e iniettività]]).
- **Non suriettiva**, perché $\dim\operatorname{im}L=2<3=\dim\mathbb R^3$.
- Quindi **non biiettiva**.

*(Nota: $\dim\ker L+\dim\operatorname{im}L=1+2=3=\dim P_2$, come previsto dal [[Rango e teorema di nullità più rango|teorema di nullità più rango]].)*

### 5. Esercizi consigliati (ALG, Mauri–Schlesinger)

- §4.1: 4.2–4.8, 4.20
- §4.3: 4.40, 4.41, 4.43
- §4.4: 4.47, 4.48, 4.51
- §4.5: 4.62, 4.63, 4.70, 4.71
- §4.6: 4.76, 4.78, 4.79, 4.80
- §4.8: 4.107, 4.108, 4.109, 4.117

## Collegamenti

- [[Dipendenza lineare|Dipendenza lineare]]
- [[Basi, dimensione e coordinate|Basi, dimensione e coordinate]]
- [[Applicazioni lineari, nucleo e immagine|Applicazioni lineari, nucleo e immagine]]
- [[Rango e teorema di nullità più rango|Rango e teorema di nullità più rango]]
