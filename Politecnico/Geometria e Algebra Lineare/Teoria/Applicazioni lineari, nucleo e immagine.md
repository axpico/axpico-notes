---
tags:
  - geometria-algebra-lineare
  - applicazioni-lineari
  - nucleo
  - immagine
  - algebra-lineare
---
## Applicazioni lineari, nucleo e immagine

### Definizione

Siano $V,W$ spazi vettoriali sullo stesso campo $\mathbb K$. Una mappa $\ell:V\to W$ si dice **lineare** se soddisfa entrambe:

1. **additività**: $\ell(\mathbf u+\mathbf v)=\ell(\mathbf u)+\ell(\mathbf v)\quad\forall\,\mathbf u,\mathbf v\in V$;
2. **omogeneità**: $\ell(\lambda\mathbf v)=\lambda\,\ell(\mathbf v)\quad\forall\,\lambda\in\mathbb K,\ \mathbf v\in V$.

**Condizione unica equivalente:** $\ell(\lambda\mathbf u+\mu\mathbf v)=\lambda\ell(\mathbf u)+\mu\ell(\mathbf v)$ per ogni $\lambda,\mu\in\mathbb K$, $\mathbf u,\mathbf v\in V$. In altre parole $\ell$ "commuta" con le combinazioni lineari: è un **omomorfismo di spazi vettoriali** (rispetta la struttura algebrica).

**Conseguenze immediate.**
- $\ell(\mathbf 0_V)=\mathbf 0_W$ (da omogeneità con $\lambda=0$, oppure $\ell(\mathbf 0)=\ell(\mathbf 0+\mathbf 0)=2\ell(\mathbf 0)$).
- $\ell(-\mathbf v)=-\ell(\mathbf v)$.
- Quindi una mappa con $\ell(\mathbf 0)\neq\mathbf 0$ **non può** essere lineare (utile per escluderle subito).

### Esempi

**Es. 1 — $f:\mathbb R\to\mathbb R$, $f(x)=ax+b$.** Per l'osservazione sopra, se $f$ è lineare allora $f(0)=b=0$. Verifica diretta:
$f(\lambda x)=a\lambda x+b$ e $\lambda f(x)=\lambda ax+\lambda b$, uguali per ogni $\lambda$ solo se $b=0$. Per $b=0$: $f(x+y)=a(x+y)=ax+ay=f(x)+f(y)$. Dunque **$f$ è lineare $\iff b=0$**. (Geometricamente: le funzioni lineari $\mathbb R\to\mathbb R$ sono le rette per l'origine; una retta che non passa per l'origine è *affine*, non lineare.)

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

*Blu/primo grafico: $y=2x$ passa per l'origine ed è lineare; $y=2x+1$ non passa per l'origine, quindi non è lineare (solo affine).*

**Es. 2 — Derivata.** $V=\mathbb R^{\mathbb R}$ (o $C^1$), $D(f)=f'$. $D(\alpha f+\beta g)=\alpha f'+\beta g'$: lineare, per le regole di derivazione.

**Es. 3 — Integrale.** $V=C([0,1])$, $W=\mathbb R$, $\ell(f)=\int_0^1 f(x)\,dx$. Per linearità dell'integrale:
$$\ell(\alpha f+\beta g)=\int_0^1(\alpha f+\beta g)=\alpha\int_0^1 f+\beta\int_0^1 g=\alpha\ell(f)+\beta\ell(g).$$

**Es. 4 — Mappa associata a una matrice.** Sia $A\in M_{m\times n}(\mathbb K)$. Definiamo
$$\ell_A:\mathbb K^n\to\mathbb K^m,\qquad \ell_A(\mathbf x):=A\mathbf x\quad(\mathbf x\text{ vettore colonna }n\times1).$$
È lineare per le proprietà del prodotto matrice-vettore: $A(\mathbf x+\mathbf y)=A\mathbf x+A\mathbf y$ e $A(\lambda\mathbf x)=\lambda A\mathbf x$. Questo è **l'esempio fondamentale**: il teorema di rappresentazione (prossimo argomento) dirà che *ogni* mappa lineare tra spazi di dimensione finita è, a meno di basi, della forma $\ell_A$.

**Mappa nulla.** $\forall\mathbf v:\ \ell(\mathbf v)=\mathbf 0\in W$. È lineare (corrisponde alla matrice nulla).

### Composizione di mappe

Date $f:X\to Y$ e $g:Y\to Z$, la **composta** è $g\circ f:X\to Z$, $(g\circ f)(x):=g(f(x))$ (si applica prima $f$, poi $g$).

**Teorema (linearità della composta).** Se $f:U\to V$ e $g:V\to W$ sono lineari, allora $g\circ f$ è lineare.

*Dimostrazione.* Omogeneità: $(g\circ f)(\lambda\mathbf u)=g(f(\lambda\mathbf u))=g(\lambda f(\mathbf u))=\lambda g(f(\mathbf u))$ (prima si usa l'omogeneità di $f$, poi quella di $g$). Additività: $(g\circ f)(\mathbf u+\mathbf v)=g(f(\mathbf u)+f(\mathbf v))=g(f(\mathbf u))+g(f(\mathbf v))$. $\square$

**Osservazione (composizione $\leftrightarrow$ prodotto di matrici).** Se $A\in M_{m\times n}$, $B\in M_{p\times m}$ allora
$$\ell_B\circ\ell_A=\ell_{BA}\qquad(\text{in generale: }\ell_{AB}=\ell_A\circ\ell_B).$$
Infatti $(\ell_B\circ\ell_A)(\mathbf x)=B(A\mathbf x)=(BA)\mathbf x$ per l'associatività del prodotto. È il motivo per cui il prodotto di matrici è definito proprio così, e perché **non è commutativo**: la composizione di funzioni non lo è. Vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]].

### Immagine e nucleo

Sia $\ell:V\to W$ lineare.

- **Immagine:** $\operatorname{im}(\ell)=\{\ell(\mathbf v):\mathbf v\in V\}\subseteq W$ (terminologia in [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni (terminologia generale).md|Applicazioni (terminologia generale)]]).
- **Nucleo (kernel):** $\ker(\ell):=\ell^{-1}(\mathbf 0)=\{\mathbf x\in V:\ \ell(\mathbf x)=\mathbf 0\}\subseteq V$ — la controimmagine del vettore nullo.

**Proposizione 1.** $\operatorname{im}(\ell)$ è un **sottospazio di $W$** e $\ker(\ell)$ è un **sottospazio di $V$**.

*Dimostrazione (nucleo).* $\ell(\mathbf 0)=\mathbf 0$, quindi $\mathbf 0\in\ker\ell\neq\varnothing$. Se $\mathbf u,\mathbf v\in\ker\ell$ e $\alpha,\beta\in\mathbb K$:
$$\ell(\alpha\mathbf u+\beta\mathbf v)=\alpha\ell(\mathbf u)+\beta\ell(\mathbf v)=\alpha\mathbf 0+\beta\mathbf 0=\mathbf 0,$$
quindi $\alpha\mathbf u+\beta\mathbf v\in\ker\ell$: chiuso per combinazioni lineari, dunque sottospazio.

*Dimostrazione (immagine).* $\mathbf 0=\ell(\mathbf 0)\in\operatorname{im}\ell$. Se $\mathbf w_1=\ell(\mathbf v_1)$, $\mathbf w_2=\ell(\mathbf v_2)$ allora $\alpha\mathbf w_1+\beta\mathbf w_2=\ell(\alpha\mathbf v_1+\beta\mathbf v_2)\in\operatorname{im}\ell$. $\square$

**Caso matriciale.** Per $\ell_A:\mathbb K^n\to\mathbb K^m$:
- $\ker(\ell_A)=\{\mathbf x\in\mathbb K^n: A\mathbf x=\mathbf 0\}$ = **insieme delle soluzioni del sistema omogeneo** $A\mathbf x=\mathbf 0$. Ritroviamo così che l'insieme delle soluzioni di un sistema omogeneo è un sottospazio di $\mathbb K^n$.
- $\operatorname{im}(\ell_A)=\{A\mathbf x\}=\operatorname{span}(\text{colonne di }A)$, lo **spazio delle colonne** di $A$ (perché $A\mathbf x=x_1A^1+\dots+x_nA^n$ è una combinazione lineare delle colonne). Per $\mathbf b\in\mathbb K^m$: $A\mathbf x=\mathbf b$ è risolubile $\iff\mathbf b\in\operatorname{im}(A)$ (è il contenuto del teorema di Rouché–Capelli, [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Sistemi lineari e teorema di Rouché-Capelli]]).

### Struttura delle controimmagini

Sia $\ell:V\to W$ lineare e $\mathbf w_0\in W$. Due casi mutuamente esclusivi:

1. $\mathbf w_0\notin\operatorname{im}(\ell)\ \Rightarrow\ \ell^{-1}(\mathbf w_0)=\varnothing$ (l'equazione $\ell(\mathbf x)=\mathbf w_0$ non ha soluzioni);
2. $\mathbf w_0\in\operatorname{im}(\ell)\ \Rightarrow$ esiste almeno una soluzione $\mathbf v_0\in V$ con $\ell(\mathbf v_0)=\mathbf w_0$.

**Teorema (struttura delle soluzioni).** Nel caso 2,
$$\boxed{\ \ell^{-1}(\mathbf w_0)=\{\mathbf v_0+\mathbf u:\ \mathbf u\in\ker(\ell)\}=\mathbf v_0+\ker(\ell)\ }$$
cioè: *soluzione generale = una soluzione particolare + soluzione generale dell'omogenea associata*. È lo stesso schema dei sistemi lineari e delle equazioni differenziali lineari.

*Dimostrazione.* Occorre provare: $\mathbf v\in\ell^{-1}(\mathbf w_0)\iff\exists\,\mathbf u\in\ker\ell$ con $\mathbf v=\mathbf v_0+\mathbf u$.

($\Rightarrow$) Se $\ell(\mathbf v)=\mathbf w_0$, per linearità
$$\ell(\mathbf v-\mathbf v_0)=\ell(\mathbf v)-\ell(\mathbf v_0)=\mathbf w_0-\mathbf w_0=\mathbf 0,$$
quindi $\mathbf u:=\mathbf v-\mathbf v_0\in\ker\ell$ e $\mathbf v=\mathbf v_0+\mathbf u$.

($\Leftarrow$) Se $\mathbf v=\mathbf v_0+\mathbf u$ con $\mathbf u\in\ker\ell$, allora
$$\ell(\mathbf v)=\ell(\mathbf v_0)+\ell(\mathbf u)=\mathbf w_0+\mathbf 0=\mathbf w_0.\ \square$$

**Interpretazione geometrica.** L'insieme delle controimmagini è un **sottospazio traslato** (classe laterale / sottospazio affine) parallelo a $\ker\ell$: stessa "forma" di $\ker\ell$, ma spostato di $\mathbf v_0$; passa per l'origine solo se $\mathbf w_0=\mathbf 0$.

**Esempio grafico.** $\ell:\mathbb R^2\to\mathbb R$, $\ell(x,y)=x-y$. Il nucleo è la retta $y=x$; la controimmagine di $w_0=1$ è la retta parallela $y=x-1=\mathbf v_0+\ker\ell$ con $\mathbf v_0=(1,0)$ (infatti $\ell(1,0)=1$).

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

*$y=x$: $\ker\ell$ ($w_0=0$). $y=x-1$: $\ell^{-1}(1)$. $y=x+2$: $\ell^{-1}(-2)$. Sono tutte rette parallele a $\ker\ell$.*

### Iniettività e nucleo

**Corollario.** $\ell$ è iniettiva $\iff\ker(\ell)=\{\mathbf 0\}$.

*Dimostrazione.*
- ($\Rightarrow$) Se $\ell$ è iniettiva, $\mathbf 0$ ha al più una controimmagine; poiché $\ell(\mathbf 0)=\mathbf 0$, essa è $\mathbf 0$ e quindi $\ker\ell=\{\mathbf 0\}$. Se invece $\ker\ell\neq\{\mathbf 0\}$, contiene un $\mathbf u\neq\mathbf 0$ e $\ell(\mathbf u)=\ell(\mathbf 0)$: non iniettiva.
- ($\Leftarrow$) Siano $\mathbf v_0,\mathbf v_1$ con $\ell(\mathbf v_0)=\ell(\mathbf v_1)=\mathbf w_0$. Per il teorema, $\mathbf v_1=\mathbf v_0+\mathbf u$ con $\mathbf u\in\ker\ell=\{\mathbf 0\}$, quindi $\mathbf v_1=\mathbf v_0$. $\square$

**Perché è un fatto notevole:** per una funzione generica iniettività richiede di confrontare *tutte* le coppie di punti; per una mappa **lineare** basta controllare un solo vettore ($\mathbf 0$).

*Per una matrice:* $\ell_A$ iniettiva $\iff$ il sistema omogeneo $A\mathbf x=\mathbf 0$ ha solo la soluzione banale $\iff\operatorname{rk}(A)=n$ (numero di colonne).

### Mappe biiettive e mappa inversa

Se $f:X\to Y$ è **biiettiva**, $\forall y\in Y\ \exists!\,x\in X$ con $f(x)=y$; la **mappa inversa** $f^{-1}:Y\to X$ associa a $y$ tale unico $x$, ed è caratterizzata da
$$f(x)=y\iff x=f^{-1}(y),\qquad f^{-1}\circ f=\mathrm{id}_X,\quad f\circ f^{-1}=\mathrm{id}_Y.$$

**Esempio.** $f:\mathbb R\to\mathbb R$, $f(x)=x^3$: l'equazione $x^3=y$ ammette un'unica soluzione $x=\sqrt[3]{y}$, perciò $f^{-1}(y)=\sqrt[3]{y}$ e $f(\sqrt[3]{y})=y$.

**Attenzione alla notazione.** $f^{-1}(B)$ (controimmagine di un insieme) è definita per *ogni* $f$; $f^{-1}$ come *funzione* esiste solo se $f$ è biiettiva.

**Teorema (linearità della mappa inversa).** Se $\ell:V\to W$ è lineare e biiettiva, allora anche $\ell^{-1}:W\to V$ è lineare.

*Dimostrazione (traccia).* Siano $\mathbf w_1,\mathbf w_2\in W$, $\mathbf v_i=\ell^{-1}(\mathbf w_i)$. Allora $\ell(\alpha\mathbf v_1+\beta\mathbf v_2)=\alpha\mathbf w_1+\beta\mathbf w_2$, cioè $\ell^{-1}(\alpha\mathbf w_1+\beta\mathbf w_2)=\alpha\mathbf v_1+\beta\mathbf v_2=\alpha\ell^{-1}(\mathbf w_1)+\beta\ell^{-1}(\mathbf w_2)$. $\square$

**Caso matriciale.** Se $A$ è quadrata invertibile ($n\times n$), $\ell_A:\mathbb K^n\to\mathbb K^n$ è biiettiva e
$$(\ell_A)^{-1}=\ell_{A^{-1}}.$$
Infatti $\ell_{A^{-1}}\circ\ell_A=\ell_{A^{-1}A}=\ell_{I}=\mathrm{id}$. In particolare, per $\mathbf b\in\mathbb K^n$ il sistema $A\mathbf x=\mathbf b$ ha l'unica soluzione $\mathbf x=A^{-1}\mathbf b$ (vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]).

### Riassunto: sistemi lineari letti come mappe

| Sistema $A\mathbf x=\mathbf b$ | Significato per $\ell_A$ |
|---|---|
| $\mathbf b\notin\operatorname{im}(A)$ | nessuna soluzione |
| $\mathbf b\in\operatorname{im}(A)$ | soluzioni $=\mathbf x_0+\ker(A)$ |
| $\ker(A)=\{\mathbf 0\}$ | soluzione, se esiste, **unica** ($\ell_A$ iniettiva) |
| $\operatorname{im}(A)=\mathbb K^m$ | soluzione **sempre** esistente ($\ell_A$ suriettiva) |
| $A$ quadrata invertibile | esistenza **e** unicità: $\mathbf x=A^{-1}\mathbf b$ |

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni (terminologia generale).md|Applicazioni (terminologia generale)]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi di riferimento nel piano.md|Sistemi di riferimento nel piano]]
