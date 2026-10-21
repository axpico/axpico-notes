---
tags:
  - geometria-algebra-lineare
  - applicazioni-lineari
  - nucleo
  - immagine
---
## Applicazioni lineari, nucleo e immagine

> **Idea in una riga.** Un'applicazione lineare è una funzione tra spazi vettoriali che *rispetta somma e moltiplicazione per scalari*. Il **nucleo** misura "cosa viene schiacciato su zero" (quindi quanta informazione si perde), l'**immagine** misura "cosa si riesce a raggiungere". Tutta la teoria dei sistemi lineari è una riscrittura di queste due idee.

---

### 1. Definizione

Siano $V,W$ spazi vettoriali sullo stesso campo $\mathbb K$ (ad es. $\mathbb R$). Una funzione $\ell:V\to W$ è **lineare** se vale:

1. **additività**: $\ell(\mathbf u+\mathbf v)=\ell(\mathbf u)+\ell(\mathbf v)$ per ogni $\mathbf u,\mathbf v\in V$;
2. **omogeneità**: $\ell(\lambda\mathbf v)=\lambda\,\ell(\mathbf v)$ per ogni $\lambda\in\mathbb K$, $\mathbf v\in V$.

**Come leggerla.** Dire "prima sommo e poi applico $\ell$" è lo stesso che dire "prima applico $\ell$ e poi sommo". Lo stesso vale per gli scalari. Si dice che $\ell$ *commuta con le operazioni*.

**Le due condizioni si fondono in una.**
$$\ell(\lambda\mathbf u+\mu\mathbf v)=\lambda\,\ell(\mathbf u)+\mu\,\ell(\mathbf v)\qquad\forall\,\lambda,\mu\in\mathbb K,\ \forall\,\mathbf u,\mathbf v\in V.$$
Quindi $\ell$ manda combinazioni lineari in combinazioni lineari con gli stessi coefficienti. In linguaggio algebrico è un **omomorfismo di spazi vettoriali**: una funzione che conserva la struttura.

**Due conseguenze utili.**
- $\ell(\mathbf 0_V)=\mathbf 0_W$. Dimostrazione: $\ell(\mathbf 0)=\ell(0\cdot\mathbf 0)=0\cdot\ell(\mathbf 0)=\mathbf 0$.
- $\ell(-\mathbf v)=-\ell(\mathbf v)$ (si prende $\lambda=-1$).

> **Test rapido di non-linearità.** Se $\ell(\mathbf 0)\neq\mathbf 0$, la mappa **non è lineare**. È il primo controllo da fare negli esercizi. Attenzione: il viceversa è falso, perché $\ell(\mathbf 0)=\mathbf 0$ è necessario ma non sufficiente (ad es. $x\mapsto x^2$).

---

### 2. Esempi

**Es. 1 — $f:\mathbb R\to\mathbb R$, $f(x)=ax+b$.**
Se $f$ fosse lineare, avremmo $f(0)=b=0$. Verifichiamo che $b=0$ basta:
- se $b=0$: $f(x+y)=a(x+y)=ax+ay=f(x)+f(y)$ e $f(\lambda x)=a\lambda x=\lambda f(x)$ ✓;
- se $b\neq0$: $f(\lambda x)=a\lambda x+b$, mentre $\lambda f(x)=\lambda ax+\lambda b$. Sono diverse per $\lambda\ne1$ ✗.

Dunque **$f$ è lineare $\iff b=0$**. Geometricamente le mappe lineari $\mathbb R\to\mathbb R$ sono le rette *per l'origine*. Una retta che non passa per l'origine si dice **affine**, non lineare.

```desmos-graph
left=-4; right=4; top=3; bottom=-3; width=600; height=450;
---
y=2x
y=2x+1
(0,0)|label:f(0)=0
(-1,-2)|label:y=2x
(-1,-1)|label:y=2x+1
(0,1)|label:f(0)=1 ≠ 0
```

*$y=2x$ passa per l'origine ed è lineare. $y=2x+1$ non ci passa: è solo affine.*

**Es. 2 — Derivata.** Su $V=C^1(\mathbb R)$ poniamo $D(f)=f'$. Per le regole di derivazione $D(\alpha f+\beta g)=\alpha f'+\beta g'$, quindi $D$ è lineare. Qui i "vettori" sono funzioni.

**Es. 3 — Integrale.** Su $V=C([0,1])$ con valori in $W=\mathbb R$, $\ell(f)=\int_0^1 f(x)\,dx$. Per la linearità dell'integrale
$$\ell(\alpha f+\beta g)=\alpha\int_0^1 f+\beta\int_0^1 g=\alpha\,\ell(f)+\beta\,\ell(g).$$

**Es. 4 — La mappa associata a una matrice (l'esempio fondamentale).**
Sia $A\in M_{m\times n}(\mathbb K)$. Definiamo
$$\ell_A:\mathbb K^n\to\mathbb K^m,\qquad \ell_A(\mathbf x):=A\mathbf x\quad(\mathbf x\ \text{vettore colonna}).$$
È lineare perché $A(\mathbf x+\mathbf y)=A\mathbf x+A\mathbf y$ e $A(\lambda\mathbf x)=\lambda A\mathbf x$. Il [[Teorema di rappresentazione e matrice rappresentativa|teorema di rappresentazione]] dirà che *ogni* mappa lineare tra spazi di dimensione finita è, scelte le basi, di questa forma.

**Mappa nulla.** $\ell(\mathbf v)=\mathbf 0$ per ogni $\mathbf v$. È lineare e corrisponde alla matrice nulla.

---

### 3. Composizione di mappe

Date $f:X\to Y$ e $g:Y\to Z$, la **composta** è $g\circ f:X\to Z$ con $(g\circ f)(x)=g(f(x))$. Si legge da destra a sinistra: si applica prima $f$, poi $g$.

**Teorema.** Se $f:U\to V$ e $g:V\to W$ sono lineari, allora $g\circ f$ è lineare.

*Dimostrazione.* Si usa la linearità prima di $f$ e poi di $g$:
- omogeneità: $g(f(\lambda\mathbf u))=g(\lambda f(\mathbf u))=\lambda\,g(f(\mathbf u))$;
- additività: $g(f(\mathbf u+\mathbf v))=g(f(\mathbf u)+f(\mathbf v))=g(f(\mathbf u))+g(f(\mathbf v))$. $\square$

**Composizione $\leftrightarrow$ prodotto di matrici.** Se $A\in M_{m\times n}$ e $B\in M_{p\times m}$,
$$\ell_B\circ\ell_A=\ell_{BA}$$
perché $(\ell_B\circ\ell_A)(\mathbf x)=B(A\mathbf x)=(BA)\mathbf x$ per l'associatività. Questo è il motivo per cui il prodotto di matrici è definito in quel modo, e perché **non è commutativo**: la composizione di funzioni in generale non lo è. Vedi [[Operazioni tra matrici|Operazioni tra matrici]].

---

### 4. Immagine e nucleo

Sia $\ell:V\to W$ lineare.

| Oggetto | Definizione | Vive in | Domanda a cui risponde |
|---|---|---|---|
| **Immagine** | $\operatorname{im}(\ell)=\{\ell(\mathbf v):\mathbf v\in V\}$ | $W$ (arrivo) | *Quali vettori posso ottenere?* |
| **Nucleo** | $\ker(\ell)=\{\mathbf x\in V:\ell(\mathbf x)=\mathbf 0\}$ | $V$ (partenza) | *Quali vettori vengono annullati?* |

Il nucleo è la controimmagine del vettore nullo: $\ker\ell=\ell^{-1}(\mathbf 0)$. Per la terminologia generale vedi [[Applicazioni (terminologia generale)|Applicazioni (terminologia generale)]].

**Proposizione 1.** $\ker(\ell)$ è un sottospazio di $V$ e $\operatorname{im}(\ell)$ è un sottospazio di $W$.

*Dimostrazione per il nucleo.* Un sottospazio deve contenere $\mathbf 0$ ed essere chiuso per combinazioni lineari.
- $\ell(\mathbf 0)=\mathbf 0$, quindi $\mathbf 0\in\ker\ell$.
- Se $\mathbf u,\mathbf v\in\ker\ell$ e $\alpha,\beta\in\mathbb K$:
$$\ell(\alpha\mathbf u+\beta\mathbf v)=\alpha\,\ell(\mathbf u)+\beta\,\ell(\mathbf v)=\alpha\mathbf 0+\beta\mathbf 0=\mathbf 0,$$
quindi $\alpha\mathbf u+\beta\mathbf v\in\ker\ell$.

*Dimostrazione per l'immagine.* $\mathbf 0=\ell(\mathbf 0)\in\operatorname{im}\ell$. Se $\mathbf w_1=\ell(\mathbf v_1)$ e $\mathbf w_2=\ell(\mathbf v_2)$, allora $\alpha\mathbf w_1+\beta\mathbf w_2=\ell(\alpha\mathbf v_1+\beta\mathbf v_2)\in\operatorname{im}\ell$. $\square$

#### Il caso delle matrici

Per $\ell_A:\mathbb K^n\to\mathbb K^m$:

- $\ker(\ell_A)=\{\mathbf x: A\mathbf x=\mathbf 0\}$ è l'**insieme delle soluzioni del sistema omogeneo**. Questo spiega perché tali soluzioni formano un sottospazio.
- $\operatorname{im}(\ell_A)=\operatorname{span}(\text{colonne di }A)$. Infatti, se $A^1,\dots,A^n$ sono le colonne,
$$A\mathbf x=x_1A^1+x_2A^2+\dots+x_nA^n,$$
cioè $A\mathbf x$ è *sempre* una combinazione lineare delle colonne, e ogni combinazione si ottiene scegliendo opportunamente $\mathbf x$.

Di conseguenza $A\mathbf x=\mathbf b$ è risolubile $\iff\mathbf b\in\operatorname{im}(A)$. È il contenuto del teorema di [[Sistemi lineari e teorema di Rouché-Capelli|Rouché–Capelli]].

#### Esempio numerico completo

Sia
$$A=\begin{pmatrix}1&2&1\\0&1&1\end{pmatrix},\qquad \ell_A:\mathbb R^3\to\mathbb R^2.$$

**Nucleo.** Risolviamo $A\mathbf x=\mathbf 0$:
$$\begin{cases}x+2y+z=0\\ y+z=0\end{cases}\ \Rightarrow\ y=-z,\quad x=-2y-z=2z-z=z.$$
Ponendo $z=t$ si ottiene $(x,y,z)=t\,(1,-1,1)$. Quindi $\ker\ell_A=\operatorname{span}\{(1,-1,1)\}$, una **retta** in $\mathbb R^3$.

**Immagine.** Le colonne sono $(1,0)$, $(2,1)$, $(1,1)$. Le prime due sono linearmente indipendenti in $\mathbb R^2$, quindi generano tutto $\mathbb R^2$. Dunque $\operatorname{im}\ell_A=\mathbb R^2$ e $\ell_A$ è suriettiva.

**Controllo di coerenza:** $\dim\ker+\dim\operatorname{im}=1+2=3=\dim\mathbb R^3$. È un'anticipazione del teorema del rango (nullità + rango = dimensione del dominio).

---

### 5. Struttura delle controimmagini

Sia $\ell:V\to W$ lineare e fissiamo $\mathbf w_0\in W$. Vogliamo risolvere $\ell(\mathbf x)=\mathbf w_0$. Ci sono due soli casi:

1. $\mathbf w_0\notin\operatorname{im}\ell$: **nessuna soluzione**, $\ell^{-1}(\mathbf w_0)=\varnothing$.
2. $\mathbf w_0\in\operatorname{im}\ell$: esiste almeno una soluzione $\mathbf v_0$ con $\ell(\mathbf v_0)=\mathbf w_0$.

**Teorema (struttura delle soluzioni).** Nel caso 2,
$$\boxed{\ \ell^{-1}(\mathbf w_0)=\mathbf v_0+\ker(\ell)=\{\mathbf v_0+\mathbf u:\ \mathbf u\in\ker\ell\}\ }$$
In parole: **soluzione generale = una soluzione particolare + soluzione generale dell'omogenea**. È lo stesso schema delle equazioni differenziali lineari.

*Dimostrazione.* Si mostrano due inclusioni.

($\subseteq$) Se $\ell(\mathbf v)=\mathbf w_0$, per linearità
$$\ell(\mathbf v-\mathbf v_0)=\ell(\mathbf v)-\ell(\mathbf v_0)=\mathbf w_0-\mathbf w_0=\mathbf 0.$$
Quindi $\mathbf u:=\mathbf v-\mathbf v_0\in\ker\ell$ e $\mathbf v=\mathbf v_0+\mathbf u$.

($\supseteq$) Se $\mathbf u\in\ker\ell$, allora $\ell(\mathbf v_0+\mathbf u)=\ell(\mathbf v_0)+\ell(\mathbf u)=\mathbf w_0+\mathbf 0=\mathbf w_0$. $\square$

**Interpretazione geometrica.** L'insieme delle soluzioni è il nucleo **traslato** di $\mathbf v_0$: ha la stessa forma di $\ker\ell$ (una retta, un piano, …) ma non passa per l'origine, a meno che $\mathbf w_0=\mathbf 0$. Si chiama *sottospazio affine* (o classe laterale).

**Continuiamo l'esempio numerico.** Con la stessa $A$ risolviamo $A\mathbf x=(3,2)^T$. Una soluzione particolare si trova ponendo $z=0$: da $y=2$ e $x+4=3$ segue $\mathbf v_0=(-1,2,0)$. La soluzione generale è
$$(x,y,z)=(-1,2,0)+t\,(1,-1,1),\qquad t\in\mathbb R,$$
una retta parallela al nucleo, spostata di $\mathbf v_0$.

**Esempio grafico.** $\ell:\mathbb R^2\to\mathbb R$, $\ell(x,y)=x-y$. Il nucleo è la retta $y=x$. La controimmagine di $w_0=1$ è la retta parallela $y=x-1$, cioè $\mathbf v_0+\ker\ell$ con $\mathbf v_0=(1,0)$ (infatti $\ell(1,0)=1$).

```desmos-graph
left=-4; right=4; top=3; bottom=-3; width=600; height=450;
---
y=x
y=x-1
y=x+2
(0,0)|label:0
(1,0)|label:v_0
(-2,-2)|label:ker ℓ: y=x
(2,1)|label:ℓ⁻¹(1)
(-3,-1)|label:ℓ⁻¹(-2)
```

*$y=x$ è $\ker\ell$ (caso $w_0=0$). $y=x-1$ è $\ell^{-1}(1)$. $y=x+2$ è $\ell^{-1}(-2)$. Sono tutte parallele al nucleo.*

---

### 6. Iniettività e nucleo

**Corollario.** $\ell$ è iniettiva $\iff\ker(\ell)=\{\mathbf 0\}$.

*Dimostrazione.*
- ($\Rightarrow$) Se $\ell$ è iniettiva, $\mathbf 0_W$ ha al più una controimmagine. Poiché $\ell(\mathbf 0_V)=\mathbf 0_W$, quella controimmagine è $\mathbf 0_V$, quindi $\ker\ell=\{\mathbf 0\}$.
- ($\Leftarrow$) Siano $\ell(\mathbf v_0)=\ell(\mathbf v_1)=\mathbf w_0$. Per il teorema della sezione 5, $\mathbf v_1=\mathbf v_0+\mathbf u$ con $\mathbf u\in\ker\ell=\{\mathbf 0\}$, quindi $\mathbf v_1=\mathbf v_0$. $\square$

**Perché è notevole.** Per una funzione generica, provare l'iniettività richiede di confrontare *tutte* le coppie di punti. Per una mappa **lineare** basta guardare un solo vettore, lo zero.

**Per le matrici:** $\ell_A$ iniettiva $\iff A\mathbf x=\mathbf 0$ ha solo la soluzione banale $\iff\operatorname{rk}(A)=n$ (numero di colonne).

*Nell'esempio numerico $\ker\ell_A$ è una retta, quindi $\ell_A$ **non** è iniettiva: infatti $\operatorname{rk}A=2<3=n$.*

---

### 7. Mappe biiettive e mappa inversa

Se $f:X\to Y$ è **biiettiva** (iniettiva e suriettiva), per ogni $y\in Y$ esiste **un unico** $x\in X$ con $f(x)=y$. La **mappa inversa** $f^{-1}:Y\to X$ associa a $y$ quell'$x$:
$$f(x)=y\iff x=f^{-1}(y),\qquad f^{-1}\circ f=\mathrm{id}_X,\quad f\circ f^{-1}=\mathrm{id}_Y.$$

**Esempio.** $f(x)=x^3$ su $\mathbb R$: l'equazione $x^3=y$ ha sempre un'unica soluzione, quindi $f^{-1}(y)=\sqrt[3]{y}$.

> **Attenzione alla notazione.** $f^{-1}(B)$ (controimmagine di un *insieme* $B$) esiste per ogni $f$. Invece $f^{-1}$ come *funzione* esiste solo se $f$ è biiettiva.

**Teorema.** Se $\ell:V\to W$ è lineare e biiettiva, anche $\ell^{-1}:W\to V$ è lineare.

*Dimostrazione.* Siano $\mathbf w_1,\mathbf w_2\in W$ e $\mathbf v_i=\ell^{-1}(\mathbf w_i)$. Per linearità di $\ell$, $\ell(\alpha\mathbf v_1+\beta\mathbf v_2)=\alpha\mathbf w_1+\beta\mathbf w_2$. Applicando $\ell^{-1}$ a entrambi i membri:
$$\ell^{-1}(\alpha\mathbf w_1+\beta\mathbf w_2)=\alpha\mathbf v_1+\beta\mathbf v_2=\alpha\,\ell^{-1}(\mathbf w_1)+\beta\,\ell^{-1}(\mathbf w_2).\ \square$$

**Caso matriciale.** Se $A$ è quadrata e invertibile, $\ell_A$ è biiettiva e
$$(\ell_A)^{-1}=\ell_{A^{-1}},$$
perché $\ell_{A^{-1}}\circ\ell_A=\ell_{A^{-1}A}=\ell_I=\mathrm{id}$. Allora $A\mathbf x=\mathbf b$ ha l'unica soluzione $\mathbf x=A^{-1}\mathbf b$. Vedi [[Matrici quadrate e matrice inversa|Matrici quadrate e matrice inversa]].

---

### 8. Riassunto: sistemi lineari letti come mappe

| Proprietà di $A\mathbf x=\mathbf b$ | Significato per $\ell_A$ |
|---|---|
| $\mathbf b\notin\operatorname{im}(A)$ | nessuna soluzione |
| $\mathbf b\in\operatorname{im}(A)$ | soluzioni $=\mathbf x_0+\ker(A)$ |
| $\ker(A)=\{\mathbf 0\}$ | soluzione, se esiste, **unica** ($\ell_A$ iniettiva) |
| $\operatorname{im}(A)=\mathbb K^m$ | soluzione **sempre esistente** ($\ell_A$ suriettiva) |
| $A$ quadrata invertibile | esistenza **e** unicità: $\mathbf x=A^{-1}\mathbf b$ |

**Dizionario mentale:**
- *esistenza* della soluzione $\leftrightarrow$ immagine (suriettività);
- *unicità* della soluzione $\leftrightarrow$ nucleo (iniettività).

---

## Collegamenti

- [[Applicazioni (terminologia generale)|Applicazioni (terminologia generale)]]
- [[Spazi vettoriali e sottospazi|Spazi vettoriali e sottospazi]]
- [[Sistemi lineari e teorema di Rouché-Capelli|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Operazioni tra matrici|Operazioni tra matrici]]
- [[Sistemi di riferimento nel piano|Sistemi di riferimento nel piano]]
- [[Basi, dimensione e coordinate|Basi, dimensione e coordinate]]
- [[Teorema di rappresentazione e matrice rappresentativa|Teorema di rappresentazione e matrice rappresentativa]]
