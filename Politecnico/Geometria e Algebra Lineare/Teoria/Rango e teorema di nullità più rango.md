---
tags:
  - geometria-algebra-lineare
  - rango
  - nullità
---
## Rango e teorema di nullità più rango

↑ [[Politecnico/Geometria e Algebra Lineare/Indice|Indice]] · tappa 5 (Applicazioni lineari) · prima: [[Basi di nucleo, immagine e span|Basi di nucleo, immagine e span]]

> Fonte: [[06 Dipendenza lineare. Condizioni di una base. Basi di nucleo e di span. Rango di una matrice ed una mappa lineare. Teorema di nullita piu rango.pdf|Lezione 6 (PDF)]], pp. 63–92.

Nella Lezione 1 il rango di una matrice era definito come il numero di righe non nulle della sua forma ridotta a scala. In realtà il rango è legato direttamente ai concetti di **dimensione** e di **indipendenza lineare**.

### 1. Spazio colonna e spazio riga

**Definizione.** Sia $A\in M_{\mathbb K}(m,n)$.
- Lo **spazio colonna** $\operatorname{Col}(A)\subseteq\mathbb K^m$ è il sottospazio generato dalle colonne di $A$.
- Lo **spazio riga** $\operatorname{Row}(A)\subseteq\mathbb K^n$ è il sottospazio generato dalle righe di $A$.
- Il **rango per colonne** è $\dim\operatorname{Col}(A)$; il **rango per righe** è $\dim\operatorname{Row}(A)$.

**Esempio.** $A=\begin{pmatrix}1&3&5\\2&4&6\end{pmatrix}$.
- $\operatorname{Row}(A)=\operatorname{span}\{(1,3,5),(2,4,6)\}\subset\mathbb R^3$. I due vettori sono indipendenti, quindi il rango per righe è $2$.
- $\operatorname{Col}(A)=\operatorname{span}\{(1,2),(3,4),(5,6)\}\subset\mathbb R^2$. In $\mathbb R^2$ ci sono al massimo 2 vettori indipendenti, e $(1,2),(3,4)$ lo sono, quindi formano una base: il rango per colonne è $2$.
- Riducendo a scala: $A\xrightarrow{R_2\to R_2-2R_1}\begin{pmatrix}\boxed1&3&5\\0&\boxed{-2}&-4\end{pmatrix}$, quindi $r(A)=2$.

I tre numeri coincidono, e non è un caso:

> **Teorema 1 (sul rango).** Per ogni matrice $A$:
> $$r(A)=\dim\operatorname{Col}(A)=\dim\operatorname{Row}(A).$$
> (Senza dimostrazione.)

### 2. Immagine di $L_A$ = spazio colonna

Per $L_A:\mathbb K^n\to\mathbb K^m$, $L_A(\mathbf x)=A\mathbf x$, indicando con $\mathbf v_j$ la $j$-esima colonna di $A$:
$$\operatorname{im}L_A=\{A\mathbf x:\mathbf x\in\mathbb K^n\}=\{x_1\mathbf v_1+\dots+x_n\mathbf v_n\}=\operatorname{span}\{\mathbf v_1,\dots,\mathbf v_n\}=\operatorname{Col}(A).$$

> $$\dim\operatorname{im}L_A=r(A).$$

**Definizione.** Il **rango** di una mappa lineare $L:V\to W$ è $r(L):=\dim\operatorname{im}L$.

**Esempio.** $L:\mathbb R^3\to\mathbb R^3$, $L(x,y,z)=(x+y,\ x+y+z,\ x+y-z)$:
$$A=\begin{pmatrix}1&1&0\\1&1&1\\1&1&-1\end{pmatrix}\xrightarrow[R_3\to R_3-R_1]{R_2\to R_2-R_1}\begin{pmatrix}1&1&0\\0&0&1\\0&0&-1\end{pmatrix}\xrightarrow{R_3\to R_3+R_2}\begin{pmatrix}\boxed1&1&0\\0&0&\boxed1\\0&0&0\end{pmatrix}.$$
Quindi $r(L)=r(A)=2$.

### 3. Teorema di nullità più rango

> **Teorema 2 (nullità più rango).** Sia $L:V\to W$ lineare con $\dim V=n<+\infty$. Allora
> $$\boxed{\ r(L)+\dim\ker L=n=\dim(\text{dominio})\ }$$

- La formula **non** contiene la dimensione del codominio.
- $\dim\ker L$ si chiama **nullità** di $L$.
- In parole: la nullità conta le direzioni "cancellate" da $L$; nell'immagine restano $n-\dim\ker L$ direzioni indipendenti.

*Dimostrazione (caso $L:\mathbb K^n\to\mathbb K^m$).* Per il [[Teorema di rappresentazione e matrice rappresentativa|teorema di rappresentazione]] $L=L_A$ con $A\in M(m,n)$, quindi $r(L)=r(A)$ e $\ker L=\ker A$. $\ker A$ è l'insieme delle soluzioni di $A\mathbf x=\mathbf 0$. Per Rouché–Capelli e per il metodo della [[Basi di nucleo, immagine e span|base del nucleo]], la sua dimensione è il numero di variabili libere, cioè $n-r(A)$. Dunque $n=\dim\ker A+r(A)=\dim\ker L+r(L)$. $\blacksquare$

**Esempio 1.** $\dim\ker A$ per $A=\begin{pmatrix}1&1&1&1\\1&2&2&2\\1&2&3&3\end{pmatrix}$.
$L_A:\mathbb R^4\to\mathbb R^3$; conta solo il dominio, quindi $n=4$.
$$A\xrightarrow[R_3\to R_3-R_1]{R_2\to R_2-R_1}\begin{pmatrix}1&1&1&1\\0&1&1&1\\0&1&2&2\end{pmatrix}\xrightarrow{R_3\to R_3-R_2}\begin{pmatrix}\boxed1&1&1&1\\0&\boxed1&1&1\\0&0&\boxed1&1\end{pmatrix}.$$
Quindi $r(A)=3$ e $\dim\ker A=4-3=1$.

**Esempio 2.** $L:P_2\to\mathbb R$, $L(p)=\int_0^1p(x)\,dx$.
- $\operatorname{im}L\neq\{0\}$ (ad es. $L(1)=1$), quindi $r(L)>0$.
- $\operatorname{im}L\subseteq\mathbb R$, quindi $r(L)\le1$. Dunque $r(L)=1$.
- Per il teorema: $\dim\ker L=\dim P_2-r(L)=3-1=2$.

*Verifica diretta.* $\int_0^1(a_0+a_1x+a_2x^2)\,dx=a_0+\frac{a_1}2+\frac{a_2}3=0$, quindi
$$\begin{pmatrix}a_0\\a_1\\a_2\end{pmatrix}=s\begin{pmatrix}-\frac12\\1\\0\end{pmatrix}+t\begin{pmatrix}-\frac13\\0\\1\end{pmatrix}\ \Rightarrow\ \ker L=\operatorname{span}\{q_1,q_2\},\quad q_1=x-\tfrac12,\ q_2=x^2-\tfrac13.$$
Le coordinate sono indipendenti, quindi $\{q_1,q_2\}$ è una base e $\dim\ker L=2$. ✓

### 4. Usare lo spazio colonna in geometria

(L'interpretazione geometrica dello spazio riga è rimandata alla lezione successiva.)

**Esempio 3: un punto appartiene a un piano?** Dati $P_1(1,2,3)$, $P_2(3,2,1)$ e
$$\Pi:\begin{cases}x=-1+t\\y=2t+s\\z=1-s\end{cases}\quad\text{cioè}\quad\begin{pmatrix}x\\y\\z\end{pmatrix}=\underbrace{\begin{pmatrix}-1\\0\\1\end{pmatrix}}_{\mathbf r_0}+t\underbrace{\begin{pmatrix}1\\2\\0\end{pmatrix}}_{\mathbf u}+s\underbrace{\begin{pmatrix}0\\1\\-1\end{pmatrix}}_{\mathbf v}.$$

*Soluzione 1 (sostituzione).*
- Per $P_1$: $1=-1+t$, $2=2t+s$, $3=1-s$, che ha soluzione $t=2$, $s=-2$. Quindi $P_1\in\Pi$.
- Per $P_2$: $3=-1+t$ dà $t=4$, $1=1-s$ dà $s=0$, ma allora $2t+s=8\neq2$: nessuna soluzione, quindi $P_2\notin\Pi$.

*Oss.:* un sistema così non può avere più di una soluzione. *(Perché? Domanda lasciata aperta a lezione.)* Perché $\mathbf u,\mathbf v$ sono indipendenti, quindi la matrice $[\mathbf u|\mathbf v]$ ha rango $2=\#$incognite.

*Soluzione 2 (spazio colonna).* $P\in\Pi\iff\mathbf b:=\mathbf r_P-\mathbf r_0\in\operatorname{Col}(A)$, con $A=[\mathbf u|\mathbf v]$. Questo equivale a $\operatorname{Col}([A|\mathbf b])=\operatorname{Col}(A)$, cioè a
$$r([A|\mathbf b])=r(A)$$
(la stessa condizione di Rouché–Capelli per $A\binom ts=\mathbf b$). Qui $r(A)=2$.
- $P_1$: $\mathbf b=(2,2,2)$:
$$\begin{pmatrix}1&0&2\\2&1&2\\0&-1&2\end{pmatrix}\to\begin{pmatrix}1&0&2\\0&1&-2\\0&-1&2\end{pmatrix}\to\begin{pmatrix}1&0&2\\0&1&-2\\0&0&0\end{pmatrix}.$$
Rango $2=r(A)$, quindi $P_1\in\Pi$.
- $P_2$: $\mathbf b_2=(4,2,0)$:
$$\begin{pmatrix}1&0&4\\2&1&2\\0&-1&0\end{pmatrix}\to\begin{pmatrix}1&0&4\\0&1&-6\\0&-1&0\end{pmatrix}\to\begin{pmatrix}1&0&4\\0&1&-6\\0&0&-6\end{pmatrix}.$$
Rango $3>2$, quindi $P_2\notin\Pi$.

**Esempio 4: equazione cartesiana dello stesso piano.**

*Metodo 1 (nucleo di $A^{\mathsf T}$, già visto in [[Rette e piani — equazioni parametriche e cartesiane|Rette e piani]]).* Si scrivono $\mathbf u,\mathbf v$ come righe, $A^{\mathsf T}=\begin{pmatrix}1&2&0\\0&1&-1\end{pmatrix}$, già a scala. Con $x_3=1$ (libera) si ottiene $x_2=1$, $x_1=-2$, quindi $\ker A^{\mathsf T}=\operatorname{span}\{(-2,1,1)\}$:
$$-2x+y+z=d,\quad d=-2(-1)+0+1=3\ \Rightarrow\ \boxed{-2x+y+z=3}.$$

*Metodo 2 (rango).* $P(x,y,z)\in\Pi\iff\mathbf b=(x+1,\ y,\ z-1)\in\operatorname{Col}(A)\iff r([A|\mathbf b])=2$:
$$\begin{pmatrix}1&0&x+1\\2&1&y\\0&-1&z-1\end{pmatrix}\xrightarrow{R_2\to R_2-2R_1}\begin{pmatrix}1&0&x+1\\0&1&y-2x-2\\0&-1&z-1\end{pmatrix}\xrightarrow{R_3\to R_3+R_2}\begin{pmatrix}1&0&x+1\\0&1&y-2x-2\\0&0&z+y-2x-3\end{pmatrix}.$$
Quindi $r=2\iff z+y-2x-3=0$, la stessa equazione. ✓

**Esempio 5: equazioni cartesiane di un'immagine.** $L:C^\infty(\mathbb R)\to\mathbb R^3$, $L(f)=\bigl(f(0),f'(0),f''(0)\bigr)$, $V=\operatorname{span}\{\cos x\}$.
- $\cos x\neq0$, quindi $\{\cos x\}$ è base di $V$.
- $L(\cos x)=(1,0,-1)$, quindi la matrice rappresentativa di $L|_V$ è $A=\begin{pmatrix}1\\0\\-1\end{pmatrix}$ e $L(V)=\operatorname{Col}(A)$.
- $(x,y,z)\in L(V)\iff r([A|\mathbf x])=1$:
$$\begin{pmatrix}1&x\\0&y\\-1&z\end{pmatrix}\xrightarrow{R_3\to R_3+R_1}\begin{pmatrix}1&x\\0&y\\0&z+x\end{pmatrix}\ \Rightarrow\ L(V):\begin{cases}y=0\\x+z=0\end{cases}$$
(una retta per l'origine).

> **Metodo generale.** Le equazioni cartesiane di $\operatorname{Col}(A)$ si ottengono imponendo che le righe nulle della forma a scala di $[A|\mathbf x]$ abbiano termine noto nullo.

### Riepilogo

| Concetto | Formula |
|---|---|
| Teorema 1 | $r(A)=\dim\operatorname{Col}A=\dim\operatorname{Row}A$ |
| Immagine | $\operatorname{im}L_A=\operatorname{Col}A$, $\ r(L)=\dim\operatorname{im}L$ |
| Nullità + rango | $\dim\ker L+r(L)=\dim V$ (dominio!) |
| $\mathbf b\in\operatorname{Col}A$ | $\iff r([A\vert\mathbf b])=r(A)$ |

## Collegamenti

- [[Basi di nucleo, immagine e span|Basi di nucleo, immagine e span]]
- [[Teorema di rappresentazione e matrice rappresentativa|Teorema di rappresentazione e matrice rappresentativa]]
- [[Sistemi lineari e teorema di Rouché-Capelli|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Rette e piani — equazioni parametriche e cartesiane|Rette e piani — equazioni parametriche e cartesiane]]
- [[Posizione reciproca di rette e piani|Posizione reciproca di rette e piani]]
