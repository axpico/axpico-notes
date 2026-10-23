---
tags:
  - geometria-algebra-lineare
  - spazi-vettoriali
  - sottospazi
  - grassmann
---
## Intersezione, somma e somma diretta di sottospazi — formula di Grassmann

↑ [[Politecnico/Geometria e Algebra Lineare/Indice|Indice]] · tappa 7 (Somma e intersezione di sottospazi) · prima: [[Completamento a base|Completamento a base]]

> Fonte: [[08 completa.pdf|Lezione 8 (PDF)]], pp. 18–77. Testo di riferimento (ALG): p. 197 (Prop. 8.5–8.7), pp. 239–242.

**Idea.** Dati due sottospazi $W_1,W_2\subseteq V$ ci chiediamo quali sottospazi "naturali" se ne ricavano. L'**intersezione** è il più grande sottospazio contenuto in entrambi; l'**unione** in generale non è un sottospazio, e il suo sostituto corretto è la **somma** $W_1+W_2$, il più piccolo sottospazio che li contiene entrambi. La **formula di Grassmann** misura di quanto $\dim(W_1+W_2)$ è inferiore a $\dim W_1+\dim W_2$: esattamente di $\dim(W_1\cap W_2)$, cioè di quanto i due sottospazi "si sovrappongono". La **somma diretta** è il caso senza sovrapposizione.

---

### 1. Intersezione di sottospazi

> [!theorem] Proposizione 1
> Se $W_1,\dots,W_k$ sono sottospazi di $V$ (su $K$), allora $W:=\bigcap_{i=1}^kW_i$ è un sottospazio di $V$.

*Dimostrazione.* Siano $\mathbf u,\mathbf v\in W$, $\alpha,\beta\in K$. Allora $\mathbf u,\mathbf v\in W_i$ per ogni $i$; essendo ogni $W_i$ un sottospazio, $\alpha\mathbf u+\beta\mathbf v\in W_i$ per ogni $i$, quindi $\alpha\mathbf u+\beta\mathbf v\in W$. (Inoltre $\mathbf 0\in W_i\ \forall i$, quindi $W\ne\varnothing$.) $\blacksquare$

**In pratica:** se i $W_i$ sono dati con **equazioni cartesiane**, l'intersezione si ottiene mettendo a sistema *tutte* le equazioni. Se sono dati come **span**, si uguagliano due combinazioni lineari generiche (vedi Esempio 2).

#### Esempi

**(1) Due piani in $\mathbb R^3$.** $W_1:\ x+y+z=0$, $W_2:\ x-z=0$ (piani per l'origine, $\dim=2$). $(x,y,z)\in W_1\cap W_2$ sse soddisfa entrambe:
$$\begin{cases}x+y+z=0\\x-z=0\end{cases}\iff x=z,\ y=-2z\quad\Rightarrow\quad W_1\cap W_2=\operatorname{span}\{(1,-2,1)\},$$
una retta per l'origine, $\dim=1$.

**(2) Due piani in $\mathbb R^4$ con intersezione banale.**
$$W_1=\operatorname{span}\left\{\begin{bmatrix}1\\2\\2\\1\end{bmatrix},\begin{bmatrix}1\\1\\1\\1\end{bmatrix}\right\},\qquad W_2=\operatorname{span}\left\{\begin{bmatrix}-1\\0\\0\\1\end{bmatrix},\begin{bmatrix}0\\1\\-1\\0\end{bmatrix}\right\}.$$
Un vettore sta in $W_1\cap W_2$ sse si scrive in entrambi i modi:
$$t_1\begin{bmatrix}1\\2\\2\\1\end{bmatrix}+t_2\begin{bmatrix}1\\1\\1\\1\end{bmatrix}=s_1\begin{bmatrix}-1\\0\\0\\1\end{bmatrix}+s_2\begin{bmatrix}0\\1\\-1\\0\end{bmatrix}\iff A\begin{bmatrix}t_1\\t_2\\s_1\\s_2\end{bmatrix}=\mathbf 0,\quad A=\begin{bmatrix}1&1&1&0\\2&1&0&-1\\2&1&0&1\\1&1&-1&0\end{bmatrix}$$
(le ultime due colonne sono $-\mathbf w_1,-\mathbf w_2$, perché portiamo tutto a sinistra).
$$A\xrightarrow[R_4\to R_4-R_1]{R_2\to R_2-2R_1,\ R_3\to R_3-2R_1}\begin{bmatrix}1&1&1&0\\0&-1&-2&-1\\0&-1&-2&1\\0&0&-2&0\end{bmatrix}\xrightarrow{R_3\to R_3-R_2}\begin{bmatrix}1&1&1&0\\0&-1&-2&-1\\0&0&0&2\\0&0&-2&0\end{bmatrix}\xrightarrow{R_3\leftrightarrow R_4}\begin{bmatrix}\boxed1&1&1&0\\0&\boxed{-1}&-2&-1\\0&0&\boxed{-2}&0\\0&0&0&\boxed2\end{bmatrix}$$
$\rho(A)=4=\#$incognite ⇒ solo la soluzione banale ⇒ $W_1\cap W_2=\{\mathbf 0\}$.

> Fatto notevole: in $\mathbb R^4$ due piani per l'origine possono incontrarsi **solo** nell'origine — cosa impossibile in $\mathbb R^3$ (lo spiega Grassmann: $\dim(W_1+W_2)\le3$ forza $\dim(W_1\cap W_2)\ge1$).

**(3) Matrici.** In $V=M_K(n,n)$:
- $W_1=\{A=A^T\}$ (simmetriche),
- $W_2=\{a_{ij}=0\text{ per }i>j\}$ (triangolari superiori),
- $W_3=\{a_{ij}=0\text{ per }j>i\}$ (triangolari inferiori).

$W_1\cap W_2\cap W_3$ = matrici **diagonali**. Anzi, già $W_1\cap W_2=W_2\cap W_3=W_1\cap W_3=$ diagonali (una simmetrica triangolare superiore ha $a_{ij}=a_{ji}=0$ per $i\neq j$).

#### L'unione non è un sottospazio

> [!warning] Osservazione
> L'analogo della Prop. 1 per l'unione è **falso**.

Controesempio in $\mathbb R^2$: $W_1:\ y=x$, $W_2:\ y=-x$. $W_1\cap W_2=\{(0,0)\}$, ma $W_1\cup W_2=\{|x|=|y|\}$ non è chiuso per somma: $(1,1)\in W_1$, $(-1,1)\in W_2$, ma $(1,1)+(-1,1)=(0,2)\notin W_1\cup W_2$.

(In generale $W_1\cup W_2$ è un sottospazio sse $W_1\subseteq W_2$ o $W_2\subseteq W_1$.)

---

### 2. Somma di sottospazi

> [!definition] Definizione
> La **somma** di due sottospazi $W_1,W_2\subseteq V$ è
> $$W_1+W_2:=\{\mathbf w\in V:\ \exists\,\mathbf w_1\in W_1,\ \mathbf w_2\in W_2\ \text{t.c.}\ \mathbf w=\mathbf w_1+\mathbf w_2\}.$$

> [!theorem] Proposizione 2
> $W_1+W_2$ è un sottospazio di $V$. Inoltre, se $W_1=\operatorname{span}\{\mathbf v_1,\dots,\mathbf v_k\}$ e $W_2=\operatorname{span}\{\mathbf u_1,\dots,\mathbf u_m\}$, allora
> $$W_1+W_2=\operatorname{span}\{\mathbf v_1,\dots,\mathbf v_k,\mathbf u_1,\dots,\mathbf u_m\}.$$

*Dimostrazione.*
- **Sottospazio.** Siano $\mathbf u=\mathbf u_1+\mathbf u_2$, $\mathbf v=\mathbf v_1+\mathbf v_2$ con $\mathbf u_1,\mathbf v_1\in W_1$, $\mathbf u_2,\mathbf v_2\in W_2$. Per $\lambda,\beta\in K$:
$$\lambda\mathbf u+\beta\mathbf v=\underbrace{(\lambda\mathbf u_1+\beta\mathbf v_1)}_{\in W_1}+\underbrace{(\lambda\mathbf u_2+\beta\mathbf v_2)}_{\in W_2}\in W_1+W_2.$$
- **$\supseteq$.** $W_1\subseteq W_1+W_2$ perché $\mathbf w_1=\mathbf w_1+\mathbf 0$ con $\mathbf 0\in W_2$; analogamente $W_2\subseteq W_1+W_2$. Quindi tutti i $\mathbf v_i,\mathbf u_j$ stanno in $W_1+W_2$ e, essendo questo un sottospazio, anche il loro span.
- **$\subseteq$.** Se $\mathbf w=\mathbf w_1+\mathbf w_2$, allora $\mathbf w_1=\sum\lambda_i\mathbf v_i$ e $\mathbf w_2=\sum\beta_j\mathbf u_j$, quindi $\mathbf w=\sum\lambda_i\mathbf v_i+\sum\beta_j\mathbf u_j\in\operatorname{span}\{\dots\}$. $\blacksquare$

> **Osservazione (minimalità).** $W_1+W_2$ è il **più piccolo** sottospazio contenente $W_1\cup W_2$: se $W\supseteq W_1,W_2$ è un sottospazio, ogni $\mathbf w_1+\mathbf w_2$ sta in $W$ (chiusura per somma). È l'analogo, per sottospazi, di $\operatorname{span}(W_1\cup W_2)$ — e infatti coincide con esso.

**Ricetta.** Base di $W_1+W_2$: unisci i generatori di $W_1$ e di $W_2$ ed **estrai** una base con MEG (colonne pivot).

#### Esempi

**(a)** In $\mathbb R^2$, $W_1=\operatorname{span}\{(1,1)\}$, $W_2=\operatorname{span}\{(1,-1)\}$: i due generatori sono indipendenti ⇒ $\dim(W_1+W_2)=2$ ⇒ $W_1+W_2=\mathbb R^2$.

**(b) Esempio 4 — polinomi.** In $P_3$:
$$W_1=\operatorname{span}\{(x+1)^2,(x-1)^2\},\qquad W_2=\operatorname{span}\{x^3+x^2+1,\ x^3-x^2-1\}.$$
Per la Prop. 2, $W_1+W_2=\operatorname{span}$ dei quattro polinomi. Coordinate rispetto a $\{1,x,x^2,x^3\}$:
$$(x+1)^2\mapsto\begin{bmatrix}1\\2\\1\\0\end{bmatrix},\ (x-1)^2\mapsto\begin{bmatrix}1\\-2\\1\\0\end{bmatrix},\ x^3+x^2+1\mapsto\begin{bmatrix}1\\0\\1\\1\end{bmatrix},\ x^3-x^2-1\mapsto\begin{bmatrix}-1\\0\\-1\\1\end{bmatrix}.$$
$$\begin{bmatrix}1&1&1&-1\\2&-2&0&0\\1&1&1&-1\\0&0&1&1\end{bmatrix}\xrightarrow[R_3\to R_3-R_1]{R_2\to R_2-2R_1}\begin{bmatrix}1&1&1&-1\\0&-4&-2&2\\0&0&0&0\\0&0&1&1\end{bmatrix}\xrightarrow{R_3\leftrightarrow R_4}\begin{bmatrix}\boxed1&1&1&-1\\0&\boxed{-4}&-2&2\\0&0&\boxed1&1\\0&0&0&0\end{bmatrix}$$
Pivot nelle prime tre colonne ⇒ base di $W_1+W_2$: $\{(x+1)^2,(x-1)^2,x^3+x^2+1\}$, $\dim(W_1+W_2)=3$.

Nota: $\dim W_1=\dim W_2=2$, quindi qui $\dim(W_1+W_2)=3<4=\dim W_1+\dim W_2$. In generale
$$\dim(W_1+W_2)\le\dim W_1+\dim W_2\tag{7}$$
perché unendo le basi si ottiene un sistema di generatori, non necessariamente indipendente.

---

### 3. Somma diretta (esterna)

La somma diretta è una **costruzione** di un nuovo spazio a partire da due spazi qualsiasi $U,V$ sullo stesso campo $K$ (non serve che siano sottospazi di qualcosa).

> [!definition] Definizione
> $U\oplus V$ è l'insieme delle coppie ordinate $(\mathbf u,\mathbf v)$, $\mathbf u\in U$, $\mathbf v\in V$, con le operazioni componente per componente:
> $$(\mathbf u_1,\mathbf v_1)+(\mathbf u_2,\mathbf v_2):=(\mathbf u_1+\mathbf u_2,\ \mathbf v_1+\mathbf v_2),\qquad \lambda(\mathbf u,\mathbf v):=(\lambda\mathbf u,\lambda\mathbf v).$$
> Lo zero è $(\mathbf 0_U,\mathbf 0_V)$.

(Insiemisticamente è il prodotto cartesiano $U\times V$; il simbolo $\oplus$ ricorda la struttura lineare.)

**Esempi.**
- $K^2\oplus K^2\cong M_K(2,2)$ tramite $L\big(\mathbf u,\mathbf v\big)=[\mathbf u\,|\,\mathbf v]=\begin{bmatrix}x_1&y_1\\x_2&y_2\end{bmatrix}$: biettiva e lineare per come sono definite le operazioni.
- $K^2\oplus K^2\cong K^4$ tramite $L(\mathbf x,\mathbf y)=(x_1,x_2,y_1,y_2)$. Più in generale $K^n\oplus K^m\cong K^{n+m}$.
- $U\oplus V$ e $V\oplus U$ sono formalmente spazi diversi, ma isomorfi tramite lo scambio $\mu(\mathbf u,\mathbf v)=(\mathbf v,\mathbf u)$.

> [!theorem] Proposizione 3
> Se $\mathcal B_U=\{\mathbf u_1,\dots,\mathbf u_n\}$ è base di $U$ e $\mathcal B_V=\{\mathbf v_1,\dots,\mathbf v_m\}$ è base di $V$, allora
> $$\mathcal B=\{(\mathbf u_1,\mathbf 0),\dots,(\mathbf u_n,\mathbf 0),(\mathbf 0,\mathbf v_1),\dots,(\mathbf 0,\mathbf v_m)\}$$
> è base di $U\oplus V$. In particolare
> $$\dim(U\oplus V)=\dim U+\dim V.\tag{6}$$

*Dimostrazione.*
- **(a) Indipendenza.** $\sum\lambda_i(\mathbf u_i,\mathbf 0)+\sum\beta_j(\mathbf 0,\mathbf v_j)=(\mathbf 0,\mathbf 0)$ equivale, per definizione delle operazioni, a $\big(\sum\lambda_i\mathbf u_i,\ \sum\beta_j\mathbf v_j\big)=(\mathbf 0,\mathbf 0)$, cioè al sistema $\sum\lambda_i\mathbf u_i=\mathbf 0_U$, $\sum\beta_j\mathbf v_j=\mathbf 0_V$. Per l'indipendenza di $\mathcal B_U$ e $\mathcal B_V$: tutti i $\lambda_i,\beta_j$ sono nulli.
- **(b) Generazione.** Dato $(\mathbf u,\mathbf v)$, scrivi $\mathbf u=\sum\lambda_i\mathbf u_i$, $\mathbf v=\sum\beta_j\mathbf v_j$. L'inclusione $L_U:U\to U\oplus V$, $L_U(\mathbf u)=(\mathbf u,\mathbf 0)$, è lineare (iniettiva, non suriettiva: è un isomorfismo di $U$ sul sottospazio $\{(\mathbf u,\mathbf 0)\}$); applicandola si ottiene $(\mathbf u,\mathbf 0)=\sum\lambda_i(\mathbf u_i,\mathbf 0)$, e analogamente $(\mathbf 0,\mathbf v)=\sum\beta_j(\mathbf 0,\mathbf v_j)$. Sommando:
$$(\mathbf u,\mathbf v)=(\mathbf u,\mathbf 0)+(\mathbf 0,\mathbf v)=\sum_{i=1}^n\lambda_i(\mathbf u_i,\mathbf 0)+\sum_{j=1}^m\beta_j(\mathbf 0,\mathbf v_j).\qquad\blacksquare$$

> **Tensione tra (6) e (7).** Per la somma diretta la dimensione si somma esattamente, per la somma di sottospazi solo "al più". Grassmann spiega la differenza.

---

### 4. Formula di Grassmann

> [!theorem] Teorema 1 (formula di Grassmann)
> Siano $W_1,W_2$ sottospazi di $V$ con $\dim W_1,\dim W_2<+\infty$. Allora
> $$\boxed{\ \dim(W_1+W_2)=\dim W_1+\dim W_2-\dim(W_1\cap W_2)\ }$$

*Dimostrazione.* Si considera la **mappa somma**
$$L:\ W_1\oplus W_2\to V,\qquad L(\mathbf w_1,\mathbf w_2):=\mathbf w_1+\mathbf w_2.$$
È lineare e, per definizione di $W_1+W_2$, $\operatorname{im}L=W_1+W_2$. Per la Prop. 3, $\dim(W_1\oplus W_2)=\dim W_1+\dim W_2$. Per il [[Rango e teorema di nullità più rango|teorema di nullità più rango]]:
$$\dim(W_1+W_2)=\dim\operatorname{im}L=\dim W_1+\dim W_2-\dim\ker L.$$
Resta da mostrare $\dim\ker L=\dim(W_1\cap W_2)$.

$(\mathbf w_1,\mathbf w_2)\in\ker L\iff\mathbf w_1+\mathbf w_2=\mathbf 0\iff\mathbf w_2=-\mathbf w_1$. Quindi gli elementi del nucleo sono le coppie $(\mathbf v,-\mathbf v)$ con $\mathbf v\in W_1$ e $-\mathbf v\in W_2$; ma $-\mathbf v\in W_2\iff\mathbf v\in W_2$ ($W_2$ è un sottospazio). Dunque
$$\ker L=\{(\mathbf v,-\mathbf v):\ \mathbf v\in W_1\cap W_2\}=\operatorname{im}\mu,\qquad \mu:W_1\cap W_2\to W_1\oplus W_2,\ \mu(\mathbf v)=(\mathbf v,-\mathbf v).$$
$\mu$ è lineare e iniettiva ($\ker\mu=\{\mathbf 0\}$), quindi di nuovo per nullità + rango
$$\dim\ker L=\dim\operatorname{im}\mu=\dim(W_1\cap W_2)-\underbrace{\dim\ker\mu}_{0}=\dim(W_1\cap W_2).\qquad\blacksquare$$

> **Interpretazione.** Ogni vettore di $W_1\cap W_2$ si può "contare due volte": $\mathbf v=\mathbf v+\mathbf 0=\mathbf 0+\mathbf v$. Il nucleo della mappa somma misura esattamente questa ridondanza, ed è una copia di $W_1\cap W_2$. È l'analogo lineare di $|A\cup B|=|A|+|B|-|A\cap B|$.

> **Uso tipico.** Grassmann lega quattro numeri: conoscendone tre si ricava il quarto. Spesso si calcola $\dim(W_1+W_2)$ (facile: rango dei generatori uniti) e si deduce $\dim(W_1\cap W_2)$ senza risolvere sistemi.

---

### 5. Somma diretta interna

> [!theorem] Corollario 1
> Se $W_1\cap W_2=\{\mathbf 0\}$, la mappa somma $L:W_1\oplus W_2\to W_1+W_2$ è un isomorfismo; quindi $W_1+W_2\cong W_1\oplus W_2$.

(Infatti $\ker L\cong W_1\cap W_2=\{\mathbf 0\}$ ⇒ $L$ iniettiva; ed è suriettiva su $W_1+W_2$ per definizione.)

**Vale il viceversa:** se $W_1+W_2\cong W_1\oplus W_2$, le dimensioni coincidono e Grassmann dà $\dim(W_1\cap W_2)=0$, cioè $W_1\cap W_2=\{\mathbf 0\}$.

In questo caso si identifica la somma diretta (che vive in $V\oplus V$) con $W_1+W_2$ (che vive in $V$) e si scrive
$$W=W_1\oplus W_2.$$

> [!note] Due significati del simbolo $\oplus$
> - **Somma diretta esterna**: lo spazio delle coppie $W_1\oplus W_2\subseteq V\oplus V$ — sempre definita.
> - **Somma diretta interna**: il sottospazio $W_1+W_2\subseteq V$, quando è isomorfo alla esterna — **ben definita se e solo se** $W_1\cap W_2=\{\mathbf 0\}$.

**Caratterizzazione equivalente (molto usata):** $V=W_1\oplus W_2$ (interna) $\iff$ ogni $\mathbf v\in V$ si scrive **in uno e un solo modo** come $\mathbf v=\mathbf w_1+\mathbf w_2$, $\mathbf w_i\in W_i$ $\iff$ $W_1+W_2=V$ e $W_1\cap W_2=\{\mathbf 0\}$ $\iff$ (in dim. finita) $W_1\cap W_2=\{\mathbf 0\}$ e $\dim W_1+\dim W_2=\dim V$.

#### Esempi

**(1)** In $\mathbb R^2$, le rette $y=x$ e $y=-x$: $W_1\cap W_2=\{\mathbf 0\}$, quindi
$$\dim(W_1+W_2)=1+1-0=2=\dim\mathbb R^2\ \Rightarrow\ \mathbb R^2=W_1\oplus W_2.$$
Il piano è somma diretta di due rette distinte per l'origine.

**(2)** In $\mathbb R^3$, i piani $x+y+z=0$ e $x-z=0$: l'intersezione è una retta ($\dim1$), quindi
$$\dim(W_1+W_2)=2+2-1=3=\dim\mathbb R^3\ \Rightarrow\ W_1+W_2=\mathbb R^3,$$
ma la somma **non** è diretta, perché $W_1\cap W_2\neq\{\mathbf 0\}$: ogni vettore si scrive come $\mathbf w_1+\mathbf w_2$ in infiniti modi.

**(3)** Riprendendo l'Esempio 4 (polinomi): $\dim(W_1+W_2)=3$, dunque
$$\dim(W_1\cap W_2)=2+2-3=1.$$
Basta trovare **un** polinomio non nullo comune. Osserviamo:
$$\tfrac12(x+1)^2+\tfrac12(x-1)^2=x^2+1\in W_1,\qquad \tfrac12(x^3+x^2+1)-\tfrac12(x^3-x^2-1)=x^2+1\in W_2.$$
Quindi una base di $W_1\cap W_2$ è $\{g_0\}$, $g_0(x)=x^2+1$. (Qui Grassmann ha evitato di risolvere un sistema $4\times4$: sapere che la dimensione è 1 basta a dire che un solo vettore comune non nullo è già una base.)

---

### 6. Complemento di un sottospazio

> [!definition] Definizione
> Dato un sottospazio $W\subseteq V$, un **complemento** di $W$ è un sottospazio $U\subseteq V$ tale che $W\oplus U=V$ (somma diretta interna).

> [!theorem] Fatto
> Se $\dim V<+\infty$, ogni sottospazio ammette almeno un complemento.

**Come trovarlo.** Poiché $V\cong K^n$, basta saperlo fare in $K^n$: prendi una base $\{\mathbf w_1,\dots,\mathbf w_k\}$ di $W$, [[Completamento a base|completala]] a una base $\{\mathbf w_1,\dots,\mathbf w_k,\mathbf u_{k+1},\dots,\mathbf u_n\}$ di $K^n$, e poni $U=\operatorname{span}\{\mathbf u_{k+1},\dots,\mathbf u_n\}$ (lo span dei vettori **aggiunti**).

*Perché:* l'unione delle due basi è una base di $K^n$ ⇒ $W+U=K^n$ e $\dim W+\dim U=n$ ⇒ per Grassmann $\dim(W\cap U)=0$.

**Esempio.** Complemento del piano $W\subset\mathbb R^3$, $W:\ z=3y$.
- Base di $W$: $z$ dipendente, $x,y$ liberi. $(x,y)=(1,0)\Rightarrow\mathbf v_1=(1,0,0)^T$; $(x,y)=(0,1)\Rightarrow\mathbf v_2=(0,1,3)^T$.
- Completamento:
$$\left[\begin{array}{cc|ccc}1&0&1&0&0\\0&1&0&1&0\\0&3&0&0&1\end{array}\right]\xrightarrow{R_3\to R_3-3R_2}\left[\begin{array}{cc|ccc}\boxed1&0&1&0&0\\0&\boxed1&0&1&0\\0&0&0&\boxed{-3}&1\end{array}\right]$$
  Pivot in colonna 4 ⇒ $\mathbf v_3=\mathbf e_2$.
- Complemento: $U=\operatorname{span}\{(0,1,0)^T\}=\{(x,y,z):\ x=z=0\}$ (l'asse $y$).

> **Osservazione (non unicità).** Se $\{\mathbf 0\}\neq W\neq V$, i complementi sono **infiniti**. Per un piano $W\subset\mathbb R^3$ per l'origine, **ogni** retta $U$ per l'origine non contenuta in $W$ è un complemento: $W\cap U=\{\mathbf 0\}$ e Grassmann dà $\dim(W+U)=2+1-0=3$.

#### Complemento ortogonale

In $\mathbb R^n$, col prodotto scalare standard, c'è un complemento **canonico**:

> [!definition] Definizione
> $$W^\perp:=\{\mathbf u\in\mathbb R^n:\ \mathbf u\perp\mathbf w\ \ \forall\,\mathbf w\in W\}.$$

Si vedrà più avanti che $W^\perp$ è un sottospazio, che $W\oplus W^\perp=\mathbb R^n$ (quindi è uno dei complementi di $W$) e che $(W^\perp)^\perp=W$.

**Calcolo.** Se $W=\operatorname{span}\{\mathbf w_1,\dots,\mathbf w_k\}$, basta imporre l'ortogonalità ai generatori (per linearità del prodotto scalare segue quella a tutto $W$):
$$W^\perp=\{\mathbf x:\ \langle\mathbf x,\mathbf w_1\rangle=0,\dots,\langle\mathbf x,\mathbf w_k\rangle=0\}=\ker A,\qquad A=[\mathbf w_1|\cdots|\mathbf w_k]^T$$
(i generatori scritti come **righe**).

**Esempio.** $W=\operatorname{span}\{(1,0,0)^T,(0,1,3)^T\}$ (il piano $z=3y$ di prima):
$$\begin{cases}x=0\\y+3z=0\end{cases}\iff\begin{cases}x=0\\y=-3z\end{cases}\ \Rightarrow\ W^\perp=\operatorname{span}\{(0,-3,1)^T\}.$$

*Metodo alternativo.* $\dim W^\perp=\dim\mathbb R^3-\dim W=3-2=1$, quindi $W^\perp$ è la retta per l'origine ortogonale al piano $W$. Scrivendo $W:\ 0\cdot x-3y+1\cdot z=0$, i coefficienti dell'equazione cartesiana sono le coordinate di un vettore normale al piano (vedi [[Ortogonalità e fasci di rette e piani]]) ⇒ $W^\perp=\operatorname{span}\{(0,-3,1)^T\}$.

> Confronta: il complemento trovato con il completamento ($\operatorname{span}\{\mathbf e_2\}$) **non** è ortogonale a $W$; $W^\perp$ è l'unico complemento ortogonale.

---

### 7. Somma diretta di $m$ spazi

**Esterna.** Per $V_1,\dots,V_m$ su $K$:
$$V_1\oplus\cdots\oplus V_m:=\{(\mathbf v_1,\dots,\mathbf v_m):\ \mathbf v_i\in V_i\},$$
con somma e prodotto per scalare componente per componente. Esempio: $\underbrace{K^n\oplus\cdots\oplus K^n}_{m\text{ volte}}\cong M_K(n,m)$ (ogni addendo è una colonna).

**Interna.** $V=W_1\oplus\cdots\oplus W_m=\bigoplus_{i=1}^mW_i$ se ogni $\mathbf v\in V$ si scrive **in uno e un solo modo** come $\mathbf v=\mathbf w_1+\cdots+\mathbf w_m$, $\mathbf w_i\in W_i$.

Equivalentemente: la mappa $L:\bigoplus_{i=1}^mW_i\to V$, $L(\mathbf w_1,\dots,\mathbf w_m)=\sum_i\mathbf w_i$, è biettiva (quindi un isomorfismo).

> [!warning] Attenzione con $m\ge3$
> Per tre o più sottospazi **non basta** che le intersezioni a coppie siano banali. Es.: in $\mathbb R^2$ le tre rette $\operatorname{span}\{\mathbf e_1\}$, $\operatorname{span}\{\mathbf e_2\}$, $\operatorname{span}\{\mathbf e_1+\mathbf e_2\}$ si intersecano a due a due in $\{\mathbf 0\}$, ma $\mathbf e_1+\mathbf e_2$ ha due scritture diverse. Il criterio corretto è l'unicità della scrittura (o, in dim. finita, $\sum\dim W_i=\dim V$ insieme a $\sum W_i=V$).

**Esempio.** $\mathbb R^m=\operatorname{span}\{\mathbf e_1\}\oplus\operatorname{span}\{\mathbf e_2\}\oplus\cdots\oplus\operatorname{span}\{\mathbf e_m\}$: $\mathbb R^m$ è somma diretta delle $m$ rette generate dai vettori della base canonica (la scrittura unica è proprio $\mathbf x=\sum x_i\mathbf e_i$).

---

### Riassunto

| Oggetto | Definizione | Dimensione |
|---|---|---|
| $W_1\cap W_2$ | vettori in entrambi | da Grassmann o risolvendo il sistema |
| $W_1+W_2$ | $\{\mathbf w_1+\mathbf w_2\}$ = span dei generatori uniti | $\dim W_1+\dim W_2-\dim(W_1\cap W_2)$ |
| $U\oplus V$ (esterna) | coppie $(\mathbf u,\mathbf v)$ | $\dim U+\dim V$ |
| $W_1\oplus W_2$ (interna) | $W_1+W_2$ con $W_1\cap W_2=\{\mathbf 0\}$ | $\dim W_1+\dim W_2$ |
| complemento $U$ di $W$ | $W\oplus U=V$ | $\dim V-\dim W$ |
| $W^\perp$ | $\ker[\mathbf w_1|\cdots|\mathbf w_k]^T$ | $n-\dim W$ |

Collegamenti: [[Spazi vettoriali e sottospazi]] · [[Combinazioni lineari e sottospazio generato]] · [[Rango e teorema di nullità più rango]] · [[Completamento a base]] · esercizi: [[Isomorfismi, basi, dipendenza lineare e somma di sottospazi — Esercizi corretti]]
