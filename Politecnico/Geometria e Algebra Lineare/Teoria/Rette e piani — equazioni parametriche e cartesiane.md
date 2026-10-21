---
tags:
  - geometria-algebra-lineare
  - geometria-analitica
  - sistemi-lineari
  - nucleo
---
## Rette e piani — equazioni parametriche e cartesiane

> **Idea.** Una retta o un piano si possono descrivere in due modi duali:
> - **parametrico** ("da dove parto e in che direzioni mi muovo"): $\mathbf r=\mathbf r_0+t\mathbf a$ (retta), $\mathbf r=\mathbf r_0+t\mathbf u+s\mathbf v$ (piano);
> - **cartesiano** ("quali condizioni devono soddisfare le coordinate"): un sistema lineare $A\mathbf x=\mathbf b$.
>
> Passare dall'uno all'altro è, algebricamente, passare tra due rappresentazioni di un sottospazio: come **span** (immagine di una parametrizzazione) e come **nucleo** di una matrice.

Prerequisiti: [[Vettori geometrici liberi|Vettori geometrici liberi]], [[Sistemi di riferimento nel piano|Sistemi di riferimento nel piano]], [[Sistemi lineari e teorema di Rouché-Capelli|Sistemi lineari e teorema di Rouché-Capelli]].

Il ragionamento vale sia nel piano ($\mathbb R^2$) sia nello spazio ($\mathbb R^3$). Fissato un sistema di riferimento con origine $O$, ogni punto $P$ si identifica con il suo **vettore posizione** $\mathbf r_P=\overrightarrow{OP}$.

---

### 1. Equazione parametrica di una retta

Sia $\ell$ una retta e siano $A\neq B$ due punti di $\ell$.

**Caso retta per l'origine** (prendiamo $O=A$). Un punto $P$ sta su $\ell$ **se e solo se** $\overrightarrow{AP}$ è un multiplo di $\overrightarrow{AB}$ (definizione di prodotto vettore per scalare: i due vettori sono paralleli). Quindi
$$\mathbf r=t\,\mathbf a,\quad t\in\mathbb R,\qquad\mathbf a:=\overrightarrow{AB}.$$

**Caso generale.** Spostiamo l'origine in $O'=A$. Con $\mathbf r_0:=\overrightarrow{OO'}$ e $\mathbf r'_P:=\overrightarrow{O'P}=t\mathbf a$:
$$\mathbf r_P=\overrightarrow{OO'}+\overrightarrow{O'P}=\mathbf r_0+t\mathbf a .$$

> **Equazione parametrica vettoriale di una retta**
> $$\boxed{\ \mathbf r=\mathbf r_0+t\,\mathbf a,\qquad t\in\mathbb R\ }$$
> - $\mathbf r_0$ = vettore posizione di un **punto qualsiasi** della retta;
> - $\mathbf a\neq\mathbf 0$ = **vettore direzione**, cioè un vettore non nullo parallelo a $\ell$.

Nelle coordinate si ottengono le **equazioni parametriche scalari**, ad esempio in $\mathbb R^3$: $x=x_0+ta_1,\ y=y_0+ta_2,\ z=z_0+ta_3$. La mappa $t\mapsto\mathbf r_0+t\mathbf a$ è una **biiezione** tra $\mathbb R$ e la retta.

**La parametrizzazione non è unica.** Si può cambiare il punto $\mathbf r_0$ (un altro punto della retta) e il vettore direzione $\mathbf a$ (qualsiasi suo multiplo non nullo). Le equazioni ottenute descrivono la stessa retta e si trasformano l'una nell'altra con un **cambio di parametro** (affine, $t\mapsto\alpha t+\beta$ con $\alpha\ne0$).

**Appartenenza di un punto.** $P\in\ell$ $\iff$ il sistema nell'incognita $t$ ottenuto uguagliando le coordinate di $P$ alle equazioni parametriche ha soluzione. (Esempi 5 e 6 negli esercizi.)

---

### 2. Equazione parametrica di un piano

Sia $\Pi$ un piano nello spazio e siano $O_\Pi,A,B\in\Pi$ tre punti **non allineati**. Poniamo
$$\mathbf u:=\overrightarrow{O_\Pi A},\qquad\mathbf v:=\overrightarrow{O_\Pi B}\qquad(\mathbf u,\mathbf v\text{ linearmente indipendenti}).$$
La terna $(O_\Pi,A,B)$ definisce un sistema di riferimento nel piano $\Pi$.

**Affermazione.**
$$P\in\Pi\iff\overrightarrow{O_\Pi P}=t\mathbf u+s\mathbf v\quad\text{per opportuni }t,s\in\mathbb R.\tag{$*$}$$

*Perché.* ($\Rightarrow$) $\mathbf u,\mathbf v$ sono una base dei vettori paralleli a $\Pi$. ($\Leftarrow$) i punti $O_\Pi$, $\tilde A=O_\Pi+t\mathbf u$ (che sta sulla retta $O_\Pi A\subset\Pi$), $\tilde B=O_\Pi+s\mathbf v$ (sulla retta $O_\Pi B\subset\Pi$) e $P$ sono i vertici di un **parallelogramma**; una figura piana, quindi $P$ sta nel piano di $\tilde A,\tilde B,O_\Pi$, cioè in $\Pi$.

Con origine $O$ qualunque e $\mathbf r_0:=\overrightarrow{OO_\Pi}$:
$$\mathbf r=\overrightarrow{OO_\Pi}+\overrightarrow{O_\Pi P}\ \Longrightarrow\ \boxed{\ \mathbf r=\mathbf r_0+t\,\mathbf u+s\,\mathbf v,\qquad t,s\in\mathbb R\ }$$
(se $O=O_\Pi$ si ha $\mathbf r_0=\mathbf 0$ e basta $(*)$). Anche qui la mappa $(t,s)\mapsto\mathbf r_0+t\mathbf u+s\mathbf v$ è una biiezione $\mathbb R^2\to\Pi$, e la parametrizzazione non è unica.

---

### 3. Dal cartesiano al parametrico

Un sistema lineare $A\mathbf x=\mathbf b$ compatibile ha come insieme delle soluzioni
$$\{\text{soluzioni}\}=\mathbf x_p+\ker A$$
([[Sistemi lineari e teorema di Rouché-Capelli|Rouché-Capelli]]): una soluzione particolare più il nucleo. Il nucleo si descrive con $n-\operatorname{rk}A$ **variabili libere** $\Rightarrow$ $n-\operatorname{rk}A$ **parametri**.

**Procedura.**
1. Ridurre il sistema a scala (metodo di eliminazione di Gauss).
2. Individuare le variabili libere (colonne senza pivot) e chiamarle con i nomi dei parametri.
3. Esprimere le variabili dipendenti con la sostituzione all'indietro.
4. Scrivere il risultato nella forma $\mathbf r_0+t_1\mathbf a_1+\dots$ (il termine noto dà $\mathbf r_0$, il coefficiente di ogni parametro dà un vettore direzione).

| Oggetto | Ambiente | # equazioni cartesiane indipendenti | # parametri |
|---|---|---|---|
| retta | $\mathbb R^2$ | 1 | 1 |
| retta | $\mathbb R^3$ | 2 | 1 |
| piano | $\mathbb R^3$ | 1 | 2 |
| sottospazio affine di dim. $k$ | $\mathbb R^n$ | $n-k$ | $k$ |

L'equazione $x+2y-3z=4$ è *un'*equazione cartesiana del piano (ogni multiplo non nullo descrive lo stesso piano); un sistema di due equazioni indipendenti in $\mathbb R^3$ è un sistema di equazioni cartesiane di una retta. (Esempi 5.1 e 5.2.)

---

### 4. Dal parametrico al cartesiano: span come nucleo di una matrice

**Problema.** Dati $\mathbf v_1,\dots,\mathbf v_k\in\mathbb R^n$, trovare una matrice $A$ tale che
$$\ker A=\operatorname{span}\{\mathbf v_1,\dots,\mathbf v_k\}.$$
(Equivale a trovare equazioni cartesiane del sottospazio generato dai $\mathbf v_j$: lo span è passante per l'origine, quindi le equazioni sono omogenee.)

**Metodo.**
1. Cerchiamo i vettori $\mathbf u\in\mathbb R^n$ **ortogonali** a ogni $\mathbf v_j$, cioè $\mathbf v_j^T\mathbf u=0$ per $j=1,\dots,k$. Basta imporlo sui generatori (per linearità sarà vero su tutto lo span).
2. Questo è il sistema omogeneo
 $$\begin{bmatrix}\mathbf v_1^T\\\vdots\\\mathbf v_k^T\end{bmatrix}\mathbf u=\mathbf 0 ,\tag{$*$}$$
 la cui matrice dei coefficienti ha i $\mathbf v_j$ scritti **come righe**.
3. Lo risolviamo con Gauss e scriviamo l'insieme delle soluzioni come $\operatorname{span}\{\mathbf u_1,\dots,\mathbf u_d\}$ (con $d=n-\operatorname{rk}[\mathbf v_1|\cdots|\mathbf v_k]$).
4. La matrice cercata è
 $$A=\begin{bmatrix}\mathbf u_1^T\\\vdots\\\mathbf u_d^T\end{bmatrix}\quad(\text{i }\mathbf u_i\text{ scritti come righe}).$$

**Perché funziona.**
- $\operatorname{span}\{\mathbf v_j\}\subseteq\ker A$: ogni riga $\mathbf u_i^T$ di $A$ annulla ogni $\mathbf v_j$ (per costruzione, $\mathbf u_i\perp\mathbf v_j$), quindi $A\mathbf v_j=\mathbf 0$.
- Uguaglianza per dimensione: le righe $\mathbf u_i^T$ sono linearmente indipendenti (formano una base dello spazio delle soluzioni), quindi $\operatorname{rk}A=d$ e, per il teorema rango–nullità, $\dim\ker A=n-d=\operatorname{rk}[\mathbf v_1|\cdots|\mathbf v_k]=\dim\operatorname{span}\{\mathbf v_j\}$. Un sottospazio contenuto in un altro della stessa dimensione (finita) coincide con esso. $\square$

*(Il ragionamento della lezione dice la stessa cosa in termini di ortogonalità: lo span è l'insieme dei vettori ortogonali a tutti gli $\mathbf u\in\operatorname{span}\{\mathbf u_i\}$, cioè "il complemento ortogonale del complemento ortogonale".)*

**Caso affine (retta/piano che NON passa per l'origine).** Se $\ell=\{\mathbf r_0+t\mathbf a\}$ (analogo per il piano):
1. si trasla l'origine in $\mathbf r_0$: la retta diventa $\operatorname{span}\{\mathbf a\}$;
2. si applica il metodo sopra e si ottiene $A\mathbf x=\mathbf 0$ per la retta traslata;
3. si **ripristina l'origine**: $\mathbf x\mapsto\mathbf x-\mathbf r_0$, cioè le equazioni diventano
$$\boxed{\ A\mathbf x=A\mathbf r_0\ }$$
(il termine noto è $A\mathbf r_0$: si sostituiscono le coordinate di $\mathbf r_0$ nei lati sinistri).

> **Controllo.** Verificare sempre che $\mathbf r_0$ (e $\mathbf r_0+\mathbf a$, ...) soddisfino le equazioni trovate.

---

### Esempi svolti

#### Esempio 5 — retta per due punti del piano

Retta $\ell$ per $A(1,2)$ e $B(2,-1)$.
$$\mathbf a=\overrightarrow{AB}=\begin{bmatrix}2\\-1\end{bmatrix}-\begin{bmatrix}1\\2\end{bmatrix}=\begin{bmatrix}1\\-3\end{bmatrix},\qquad\mathbf r=\begin{bmatrix}1\\2\end{bmatrix}+t\begin{bmatrix}1\\-3\end{bmatrix},\ t\in\mathbb R\tag{1}$$
ovvero $x=1+t,\ y=2-3t$.

**Altra parametrizzazione**: con $\mathbf a=\overrightarrow{BA}=(-1,3)$ e punto $B$:
$$\mathbf r=\begin{bmatrix}2\\-1\end{bmatrix}+s\begin{bmatrix}-1\\3\end{bmatrix}\tag{2}$$
Descrive la stessa retta: ponendo $s=1-t$ in (2),
$\begin{bmatrix}2\\-1\end{bmatrix}+(1-t)\begin{bmatrix}-1\\3\end{bmatrix}=\begin{bmatrix}1\\2\end{bmatrix}+t\begin{bmatrix}1\\-3\end{bmatrix}$ che è (1).

**Equazione cartesiana** (dalla §4 della teoria, vettore ortogonale a $\mathbf a$): $u_1-3u_2=0\Rightarrow\mathbf u=(3,1)$, quindi $3x+y=3\cdot1+2=5$. Controllo con $B$: $3\cdot2-1=5$ ✓.

#### Esempio 6 — appartenenza di un punto a una retta

Dire se $P_1(0,5)$ e $P_2(3,4)$ appartengono alla retta (1): $x=1+t,\ y=2-3t$.

- $P_1$: $0=1+t$ e $5=2-3t$. Dalla prima $t=-1$; la seconda: $2-3(-1)=5$ ✓. Il sistema ha l'unica soluzione $t=-1$, quindi $P_1\in\ell$. (Con la cartesiana: $3\cdot0+5=5$ ✓.)
- $P_2$: $3=1+t$ e $4=2-3t$. Dalla prima $t=2$; la seconda darebbe $2-6=-4\ne4$. Sistema **incompatibile**, quindi $P_2\notin\ell$. (Cartesiana: $3\cdot3+4=13\ne5$.)

**Grafico** (retta $3x+y=5$, punti $A,B$ sulla retta, $P_1$ sulla retta, $P_2$ fuori):

```desmos-graph
left=-2; right=5;
top=8; bottom=-3;
---
y=5-3x
(1,2)|label:A
(2,-1)|label:B
(0,5)|label:P1
(3,4)|label:P2
```

#### Esempio 7 — dal cartesiano al parametrico: un piano

Piano $x+2y-3z=4$. È un sistema di **un'equazione** in 3 incognite: $x$ dipendente, $y,z$ libere. Poniamo $y=t,\ z=s$:
$$x=4-2t+3s .$$
$$\begin{bmatrix}x\\y\\z\end{bmatrix}=\underbrace{\begin{bmatrix}4\\0\\0\end{bmatrix}}_{\mathbf r_0}+t\underbrace{\begin{bmatrix}-2\\1\\0\end{bmatrix}}_{\mathbf u}+s\underbrace{\begin{bmatrix}3\\0\\1\end{bmatrix}}_{\mathbf v},\qquad t,s\in\mathbb R .$$
È il piano per $O_\Pi(4,0,0)$, $A=O_\Pi+\mathbf u=(2,1,0)$, $B=O_\Pi+\mathbf v=(7,0,1)$. Controllo: $2+2\cdot1=4$ ✓, $7-3\cdot1=4$ ✓. La mappa $(t,s)\mapsto$ punto è una biiezione tra $\mathbb R^2$ e il piano.

**Grafico (curve di livello).** Fissando $z=c$ il piano $x+2y-3z=4$ taglia il piano $(x,y)$ nella retta $x+2y=4+3c$: al variare di $c$ si ottiene una famiglia di rette parallele. Qui $z=0$ e $z=1$, con le proiezioni su $(x,y)$ di $O_\Pi$, $A$ (entrambi a $z=0$) e $B$ (a $z=1$):

```desmos-graph
left=-2; right=10;
top=5; bottom=-3;
---
x+2y=4
x+2y=7
(4,0)|label:O_Π (z=0)
(2,1)|label:A (z=0)
(7,0)|label:B (z=1)
```

#### Esempio 8 — dal cartesiano al parametrico: una retta in $\mathbb R^3$

$$\begin{cases}x+y+z=3\\x-y+2z=2\end{cases}\xrightarrow{R_2-R_1}\begin{cases}x+y+z=3\\-2y+z=-1\end{cases}$$
$x,y$ dipendenti, $z$ libera: $z=t$, $y=\frac{1+z}2=\frac12+\frac12t$, $x=3-y-z=\frac52-\frac32t$.
$$\mathbf r=\begin{bmatrix}5/2\\1/2\\0\end{bmatrix}+t\begin{bmatrix}-3/2\\1/2\\1\end{bmatrix},\qquad t\in\mathbb R .$$
Controllo nella seconda equazione: $\frac52-\frac32t-\frac12-\frac12t+2t=2$ ✓ (i termini in $t$ si cancellano). Quindi il sistema descrive una **retta** in $\mathbb R^3$ (due equazioni indipendenti, $3-2=1$ parametro).

> *Nota sull'originale.* Negli appunti scritti a mano la forma in coordinate riporta $x=\frac52-\frac12t$, ma il vettore direzione è correttamente $(-\frac32,\frac12,1)$: il coefficiente giusto è $-\frac32$.

#### Esempio 9 — dal parametrico al cartesiano: una retta in $\mathbb R^3$

Retta $x=-1+t,\ y=2t,\ z=1+3t$. Scrivere le equazioni cartesiane.

1. In forma vettoriale: $\mathbf x=\mathbf r_0+t\mathbf v_1$ con $\mathbf r_0=(-1,0,1)$, $\mathbf v_1=(1,2,3)$.
2. **Traslando l'origine** in $\mathbf r_0$ la retta diventa $\operatorname{span}\{\mathbf v_1\}$.
3. Vettori $\mathbf u\perp\mathbf v_1$: una sola equazione $u_1+2u_2+3u_3=0$, soluzione generale $\mathbf u=\begin{bmatrix}-2t-3s\\t\\s\end{bmatrix}=t\underbrace{\begin{bmatrix}-2\\1\\0\end{bmatrix}}_{\mathbf u_1}+s\underbrace{\begin{bmatrix}-3\\0\\1\end{bmatrix}}_{\mathbf u_2}$.
4. $A=\begin{bmatrix}-2&1&0\\-3&0&1\end{bmatrix}$ e per la retta traslata $-2x+y=0,\ -3x+z=0$.
5. **Ripristiniamo l'origine**: i termini noti sono $A\mathbf r_0$:
 $$-2(-1)+0=2,\qquad-3(-1)+1=4 .$$

$$\boxed{\ \begin{cases}-2x+y=2\\-3x+z=4\end{cases}\ }$$
*Verifica:* sostituendo $x=-1+t,y=2t,z=1+3t$: $2-2t+2t=2$ ✓ e $3-3t+1+3t=4$ ✓.

> *Nota sull'originale.* Negli appunti scritti a mano i termini noti risultano $-2$ e $-2$, ma $-2x_0+y_0=-2(-1)+0=+2$ e $-3x_0+z_0=+3+1=4$: il risultato corretto è quello qui sopra.

#### Esempio 10 (aggiunto) — dal parametrico al cartesiano: un piano

Piano $\mathbf r=(1,0,2)+t(1,1,0)+s(0,1,1)$. Righe: $\mathbf v_1^T=(1,1,0)$, $\mathbf v_2^T=(0,1,1)$. Sistema per $\mathbf u$: $u_1+u_2=0,\ u_2+u_3=0\Rightarrow\mathbf u=\alpha(1,-1,1)$ (una sola variabile libera: $3-2=1$ equazione cartesiana). Allora $x-y+z=1-0+2=3$.

Controllo sui punti $\mathbf r_0=(1,0,2)$, $\mathbf r_0+\mathbf v_1=(2,1,2)$, $\mathbf r_0+\mathbf v_2=(1,1,3)$: $1-0+2=3$ ✓, $2-1+2=3$ ✓, $1-1+3=3$ ✓.

**Grafico (curve di livello).** Per $z=c$ il piano $x-y+z=3$ dà la retta $x-y=3-c$. Proiezioni su $(x,y)$ dei tre punti: $\mathbf r_0$ e $\mathbf r_0+\mathbf v_1$ stanno a $z=2$ (stessa retta $x-y=1$), $\mathbf r_0+\mathbf v_2$ a $z=3$ ($x-y=0$):

```desmos-graph
left=-2; right=5;
top=4; bottom=-2;
---
x-y=1
x-y=0
(1,0)|label:r0 (z=2)
(2,1)|label:r0+v1 (z=2)
(1,1)|label:r0+v2 (z=3)
```

### Schema riassuntivo

$$\underbrace{A\mathbf x=\mathbf b}_{\text{cartesiano}}\ \underset{\ \text{ortogonali ai generatori, righe}\ }{\overset{\ \text{Gauss, variabili libere}\ }{\rightleftarrows}}\ \underbrace{\mathbf r=\mathbf r_0+\textstyle\sum t_i\mathbf a_i}_{\text{parametrico}}$$

### Ripasso intuitivo e controlli

**Varietà affine.** Retta e piano sono $P_0+W$ con $W$ sottospazio vettoriale (la *direzione*): $\dim W=1$ per la retta, $2$ per il piano, in qualunque $\mathbb R^n$.

| | Parametrica | Cartesiana |
|---|---|---|
| Idea | come **genero** i punti | quali condizioni **verificano** i punti |
| Forma | $X=P_0+t\mathbf v$ | $A\mathbf x=\mathbf b$ |
| Pregio | scrivere punti è immediato | verificare l'appartenenza è immediato |

- Il numero di parametri è la **dimensione**; il numero di equazioni indipendenti è la **codimensione** $n-\dim$. Controllo: $\dim W+\#\text{equazioni indipendenti}=n$.
- Retta per due punti $P,Q$: $X=P+t(Q-P)$.
- Cartesiano → parametrico: Gauss; le variabili libere diventano parametri; $\{A\mathbf x=\mathbf b\}=\mathbf x_p+\ker A$ (Rouché-Capelli).
- Parametrico → cartesiano: impongo che $\mathbf x=s\mathbf v+t\mathbf w$ sia compatibile nelle incognite $s,t$ (Gauss su $[\mathbf v|\mathbf w|\mathbf x]$: le condizioni sulle righe nulle sono le equazioni). Scorciatoia in $\mathbb R^3$: piano $\mathbf n\cdot(X-P_0)=0$ con $\mathbf n=\mathbf v\times\mathbf w$.
- Esempio rapido: $(1,2,0)+t(1,1,1)$ ha $x=1+t,\ y=2+t,\ z=t$; eliminando $t=z$ si ottiene $\begin{cases}x-z=1\\y-z=2\end{cases}$.

**Errori tipici**
1. Direzioni $\mathbf v,\mathbf w$ del piano dipendenti: il "piano" collassa in una retta.
2. Direzione della retta per due punti scritta come un vettore che dipende dal punto, invece di $Q-P$.
3. Passare all'omogeneo e dimenticare il termine noto: la soluzione è $\mathbf x_p+\ker A$, non solo $\ker A$.

### Collegamenti

- [[Combinazioni lineari e sottospazio generato|Combinazioni lineari e sottospazio generato]] (span)
- [[Applicazioni lineari, nucleo e immagine|Applicazioni lineari, nucleo e immagine]] (nucleo)
- [[Spazi vettoriali e sottospazi|Spazi vettoriali e sottospazi]]
