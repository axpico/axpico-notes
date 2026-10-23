---
tags:
  - geometria-algebra-lineare
  - rette-e-piani
  - posizione-reciproca
---
## Posizione reciproca di rette e piani

↑ [[Politecnico/Geometria e Algebra Lineare/Indice|Indice]] · tappa 6 (Geometria analitica) · prima: [[Rette e piani — equazioni parametriche e cartesiane|Rette e piani — equazioni parametriche e cartesiane]]

> Fonte: [[07 Lezione 7 NUOVA (parte 1).pdf|Lezione 7 (parte 1, PDF)]], pp. 1–40.

**Idea unica.** Per trovare la posizione reciproca si **interseca**: si scrive il sistema lineare che descrive l'intersezione e lo si classifica con [[Sistemi lineari e teorema di Rouché-Capelli|Rouché–Capelli]], confrontando $r(A)$ e $r([A|\mathbf b])$.

### Parte 1 — Due rette nel piano

#### Caso I: equazioni parametriche
$$\ell_1:\ \mathbf r=\mathbf r_1+t\mathbf v_1,\qquad\ell_2:\ \mathbf r=\mathbf r_2+s\mathbf v_2,\qquad\mathbf v_1,\mathbf v_2\neq\mathbf 0.$$
$P\in\ell_1\cap\ell_2\iff\mathbf r_P=\mathbf r_1+t\mathbf v_1=\mathbf r_2+s\mathbf v_2$, cioè
$$t\mathbf v_1+s(-\mathbf v_2)=\mathbf r_2-\mathbf r_1\quad\Longleftrightarrow\quad A\begin{pmatrix}t\\s\end{pmatrix}=\mathbf b,\qquad A:=[\mathbf v_1|-\mathbf v_2],\ \ \mathbf b:=\mathbf r_2-\mathbf r_1.\tag{3}$$

**Esempio.** $\ell_1:\ \mathbf r=\binom76+t\binom12$, $\ \ell_2:\ \mathbf r=\binom0{-6}+s\binom34$.
In coordinate, $\begin{cases}7+t=3s\\6+2t=-6+4s\end{cases}$, cioè
$$\begin{pmatrix}1&-3\\2&-4\end{pmatrix}\begin{pmatrix}t\\s\end{pmatrix}=\begin{pmatrix}-7\\-12\end{pmatrix}.$$
- $\mathbf v_1=\binom12$ e $\mathbf v_2=\binom34$ sono indipendenti, quindi $r(A)=2$ e (Cramer) c'è soluzione unica.
- $$\left(\begin{array}{cc|c}1&-3&-7\\2&-4&-12\end{array}\right)\xrightarrow{R_2\to R_2-2R_1}\left(\begin{array}{cc|c}1&-3&-7\\0&2&2\end{array}\right)\Rightarrow s=1,\ t=-4.$$
- Quindi $\mathbf r_P=\binom76-4\binom12=\binom3{-2}$ e $\ell_1\cap\ell_2=\{P(3,-2)\}$. (Controllo con $s=1$: $\binom0{-6}+\binom34=\binom3{-2}$ ✓)

**I tre casi nel piano.**

| Direzioni | $r(A)$ | $r([A\vert\mathbf b])$ | Soluzioni | Posizione |
|---|---|---|---|---|
| $\mathbf v_1,\mathbf v_2$ indipendenti | 2 | 2 | unica | **incidenti** |
| $\mathbf v_2=\lambda\mathbf v_1$ | 1 | 2 | nessuna | **parallele distinte** |
| $\mathbf v_2=\lambda\mathbf v_1$ | 1 | 1 | infinite | **coincidenti** |

- Direzioni dipendenti significa rette **parallele in senso largo**.
- Distinte $\iff\mathbf r_2-\mathbf r_1$ **non** è multiplo di $\mathbf v_1$.
- Coincidenti $\iff$ sia $\mathbf v_2$ sia $\mathbf r_2-\mathbf r_1$ sono multipli di $\mathbf v_1$.

**Esempio.** Sono date
$$\ell_1:\ \mathbf r=\binom23+t\binom{-1}2,\qquad\ell_2:\ \mathbf r=\binom31+s\binom2{-4},\qquad\ell_3:\ \mathbf r=\binom13+s\binom2{-4}.$$
$\mathbf v_2=\mathbf v_3=-2\mathbf v_1$, quindi le tre rette sono parallele in senso largo.
- $\ell_1$ e $\ell_2$: $[A|\mathbf b]=[\mathbf v_1|-\mathbf v_2|\mathbf r_2-\mathbf r_1]=\begin{pmatrix}-1&-2&1\\2&4&-2\end{pmatrix}$. La seconda riga è $-2$ volte la prima, quindi $r([A|\mathbf b])=r(A)=1$: infinite soluzioni, $\ell_1=\ell_2$.
- $\ell_1$ e $\ell_3$: $\mathbf r_3-\mathbf r_1=\binom{-1}0$, $[A|\mathbf b]=\begin{pmatrix}-1&-2&-1\\2&4&0\end{pmatrix}$. Qui $r([A|\mathbf b])=2>r(A)=1$: nessuna soluzione, quindi **parallele distinte**.

#### Caso II: equazioni cartesiane
$$\ell_1:\ a_1x+b_1y=c_1,\qquad\ell_2:\ a_2x+b_2y=c_2.$$
Si risolve il sistema delle due equazioni:
- soluzione unica: **incidenti**;
- nessuna soluzione: **parallele distinte**;
- infinite soluzioni: **coincidenti**.

**Esempio.** $\ell_1:\ 2x-y=3$, $\ \ell_2:\ x+2y=-1$. La matrice dei coefficienti è invertibile:
$$\begin{pmatrix}2&-1\\1&2\end{pmatrix}^{-1}=\frac15\begin{pmatrix}2&1\\-1&2\end{pmatrix}\ \Rightarrow\ \begin{pmatrix}x\\y\end{pmatrix}=\frac15\begin{pmatrix}2&1\\-1&2\end{pmatrix}\begin{pmatrix}3\\-1\end{pmatrix}=\begin{pmatrix}1\\-1\end{pmatrix}.$$
Le rette sono incidenti in $(1,-1)$.

### Parte 2 — Due rette nello spazio

Qui si usano **solo equazioni parametriche**: se le rette sono date in forma cartesiana, prima si passa alla parametrica. Il sistema è ancora $A\binom ts=\mathbf b$ con $A=[\mathbf v_1|-\mathbf v_2]$, $\mathbf b=\mathbf r_2-\mathbf r_1$, ma ora $A$ è $3\times2$ e i casi sono **4**.

| Direzioni | $r(A)$ | $r([A\vert\mathbf b])$ | Posizione |
|---|---|---|---|
| dipendenti | 1 | 1 | **coincidenti** |
| dipendenti | 1 | 2 | **parallele distinte** |
| indipendenti | 2 | 2 | **incidenti** (un punto) |
| indipendenti | 2 | 3 | **sghembe** |

> **Novità rispetto al piano:** direzioni indipendenti (rette non parallele) **non** garantiscono che le rette si incontrino. Se $\ell_1\cap\ell_2=\emptyset$ senza che siano parallele, le rette sono **sghembe**.

**Esempio 1 (sghembe).** $\ell_1:\ \mathbf r=(1,2,3)+t(1,-1,0)$, $\ \ell_2:\ \mathbf r=(3,2,1)+s(2,1,1)$.
- Le direzioni sono indipendenti, quindi le rette non sono parallele.
- $\mathbf b=(2,0,-2)$:
$$\left(\begin{array}{cc|c}1&-2&2\\-1&-1&0\\0&-1&-2\end{array}\right)\xrightarrow{R_2\to R_2+R_1}\left(\begin{array}{cc|c}1&-2&2\\0&-3&2\\0&-1&-2\end{array}\right)\xrightarrow{R_2\leftrightarrow R_3}\left(\begin{array}{cc|c}1&-2&2\\0&-1&-2\\0&-3&2\end{array}\right)\xrightarrow{R_3\to R_3-3R_2}\left(\begin{array}{cc|c}1&-2&2\\0&-1&-2\\0&0&\boxed8\end{array}\right).$$
- $r([A|\mathbf b])=3$: nessuna soluzione, quindi le rette sono **sghembe**.

**Esempio 2 (incidenti).** Stessa $\ell_1$, $\ \ell_2:\ \mathbf r=(3,2,1)+s(2,1,-3)$.
$$\left(\begin{array}{cc|c}1&-2&2\\-1&-1&0\\0&3&-2\end{array}\right)\xrightarrow{R_2\to R_2+R_1}\left(\begin{array}{cc|c}1&-2&2\\0&-3&2\\0&3&-2\end{array}\right)\xrightarrow{R_3\to R_3+R_2}\left(\begin{array}{cc|c}1&-2&2\\0&-3&2\\0&0&0\end{array}\right).$$
- $r=r([A|\mathbf b])=2=\#$incognite, quindi c'è soluzione unica: $s=-\frac23$, $t=\frac23$.
- $\mathbf r_P=(3,2,1)-\frac23(2,1,-3)=\left(\frac53,\frac43,3\right)$, quindi le rette sono **incidenti** in $P\left(\frac53,\frac43,3\right)$.
- Controllo con $t=\frac23$ in $\ell_1$: $(1+\frac23,\ 2-\frac23,\ 3)$ ✓.

### Parte 3 — Due piani nello spazio

Si usano le equazioni cartesiane (se un piano è dato in forma parametrica, si converte):
$$\Pi_1:\ a_1x+b_1y+c_1z=d_1,\qquad\Pi_2:\ a_2x+b_2y+c_2z=d_2,\qquad(a_i,b_i,c_i)\neq\mathbf 0.\tag{6}$$
$[A|\mathbf b]$ ha 2 righe non nulle, quindi $1\le r(A)\le r([A|\mathbf b])\le2$. Ci sono tre casi:

| $r(A)$ | $r([A\vert\mathbf b])$ | Significato | Posizione |
|---|---|---|---|
| 1 | 2 | $(a_2,b_2,c_2)\propto(a_1,b_1,c_1)$, ma $(\dots,d_2)\not\propto(\dots,d_1)$ | **paralleli distinti** |
| 1 | 1 | le due equazioni sono proporzionali | **coincidenti** ($3-1=2$ parametri) |
| 2 | 2 | normali non proporzionali | **incidenti** lungo una retta ($3-2=1$ parametro) |

Nel caso incidente, il sistema (6) stesso è un'equazione cartesiana della retta $\ell=\Pi_1\cap\Pi_2$; risolvendolo se ne ottiene la forma parametrica.

**Esempi.**
- **(a)** $x+y-z=1$ e $z-x-y=2$. Le righe di $A$ sono opposte, quindi $r(A)=1$. Le righe di $[A|\mathbf b]$, $(1,1,-1|1)$ e $(-1,-1,1|2)$, sono indipendenti, quindi $r=2$: piani **paralleli distinti**.
- **(b)** $2x-y-3z=1$ e $-4x+2y+6z=-2$. La seconda equazione è $-2$ volte la prima: piani **coincidenti**.
- **(c)** $x+y+z=0$ e $2x+3y+z=1$. $r(A)=2$, quindi i piani sono incidenti:
$$\left(\begin{array}{ccc|c}1&1&1&0\\2&3&1&1\end{array}\right)\xrightarrow{R_2\to R_2-2R_1}\left(\begin{array}{ccc|c}\boxed1&1&1&0\\0&\boxed1&-1&1\end{array}\right).$$
Con $z=t$ si ottiene la retta
$$\ell:\ \mathbf r=\begin{pmatrix}-1\\1\\0\end{pmatrix}+t\begin{pmatrix}-2\\1\\1\end{pmatrix}.$$

**Un piano cartesiano e uno parametrico.** Si sostituisce la parametrica nella cartesiana.
- $\Pi_1:\ x+y+z=0$, $\ \Pi_2:\ (x,y,z)=(1,0,-1)+s(1,-1,2)+t(0,1,1)$.
 - Sostituendo: $(1+s)+(-s+t)+(-1+2s+t)=2s+2t=0$, cioè $s=-t$: un parametro libero.
 - Quindi $\Pi_1\cap\Pi_2$ è la retta $\mathbf r=(1,0,-1)+t(-1,2,-1)$.
- $\Pi_1:\ x+y+z=1$, $\ \Pi_2:\ (x,y,z)=(1,1,1)+s(-1,0,1)+t(1,-2,1)$.
 - Sostituendo: $(1-s+t)+(1-2t)+(1+s+t)=3$, cioè $3=1$, impossibile.
 - Quindi $\Pi_1\cap\Pi_2=\emptyset$: piani **paralleli**.

### Parte 4 — Una retta e un piano nello spazio

Si calcola $\ell\cap\Pi$:
- un unico punto: retta e piano **incidenti**;
- $\emptyset$: $\ell$ **parallela** a $\Pi$;
- infiniti punti: $\ell\subset\Pi$ (**contenuta**).

**Esempio (a): retta contenuta.** $\ell:\ \begin{cases}x-y+z=-1\\x+y+z=3\end{cases}$ e $\Pi:\ x+z=1$.
$$\left(\begin{array}{ccc|c}1&-1&1&-1\\1&1&1&3\\1&0&1&1\end{array}\right)\xrightarrow[R_3\to R_3-R_1]{R_2\to R_2-R_1}\left(\begin{array}{ccc|c}1&-1&1&-1\\0&2&0&4\\0&1&0&2\end{array}\right)\xrightarrow{R_3\to R_3-\frac12R_2}\left(\begin{array}{ccc|c}\boxed1&-1&1&-1\\0&\boxed2&0&4\\0&0&0&0\end{array}\right).$$
Ci sono infinite soluzioni $(x,y,z)=(1-t,\ 2,\ t)$, quindi $\ell\subset\Pi$. Si ottiene anche la forma parametrica di $\ell$.

**Esempio (b): retta incidente.** $\ell':\ \mathbf r=(1,3,2)+t(1,1,1)$ e $\Pi:\ x+z=1$.
- Sostituendo: $(1+t)+(2+t)=1$, cioè $t=-1$: soluzione unica.
- $\mathbf r=(1,3,2)-(1,1,1)=(0,2,1)$, quindi $\Pi\cap\ell'=\{P(0,2,1)\}$.

### Riepilogo

| Coppia | Sistema | Casi |
|---|---|---|
| 2 rette nel piano | $[\mathbf v_1\vert-\mathbf v_2]\binom ts=\mathbf r_2-\mathbf r_1$ (o le 2 cartesiane) | incidenti / parallele / coincidenti |
| 2 rette nello spazio | idem, $A$ $3\times2$ | + **sghembe** ($r(A)=2$, $r([A\vert\mathbf b])=3$) |
| 2 piani | 2 cartesiane in 3 incognite | paralleli / coincidenti / retta |
| retta–piano | sostituire la parametrica nella cartesiana | incidenti / parallela / contenuta |

## Collegamenti

- HTML interattivo: [[Lezione 7 — Rette, piani, ortogonalità e fasci.html|Lezione 7 completa]]

- [[Rette e piani — equazioni parametriche e cartesiane|Rette e piani — equazioni parametriche e cartesiane]]
- [[Sistemi lineari e teorema di Rouché-Capelli|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Dipendenza lineare|Dipendenza lineare]]
- [[Rango e teorema di nullità più rango|Rango e teorema di nullità più rango]]
- Prosegue in: [[Ortogonalità e fasci di rette e piani|Ortogonalità e fasci di rette e piani]] (Lezione 7, parti 2–3)
