---
tags:
  - analisi1
  - successioni
  - limiti
  - politecnico
---
Prosegue da [[Successioni]].

## Proprietà "definitivamente"

**Definizione.** Sia $P(n)$ una proprietà che dipende da $n\in\mathbb{N}$. Si dice che **$P(n)$ vale definitivamente** se
$$
\exists\, n_0\in\mathbb{N} \ \text{t.c.}\ P(n)\ \text{è vera}\ \ \forall n\ge n_0 .
$$

Due modi di leggerla:
- vera da un certo indice $n_0$ **in poi, sempre**;
- la negazione: $P(n)$ è falsa per **infiniti** indici (non "falsa solo per un numero finito di indici, da $0$ a $n_0$").

Quindi "definitivamente" ammette al più un numero **finito** di eccezioni iniziali: il comportamento a $+\infty$ è ciò che conta.

## Striscia e definizione di limite

**Striscia** attorno a $a\in\mathbb{R}$ di semiampiezza $r>0$:
$$
S_{a,r} := \{(x,y)\in\mathbb{R}^2 : |y-a|<r\}.
$$
Poiché $|y-a|<r \iff a-r<y<a+r$, è la fascia orizzontale dei punti con $y\in(a-r,a+r)$, per ogni $x\in\mathbb{R}$ ($r$ = distanza massima da $y=a$).

**Definizione (limite).** Diciamo che $\ell\in\mathbb{R}$ è il **limite** della successione $\{a_n\}$ (oppure che $a_n$ **converge**/**tende** a $\ell$) e scriviamo
$$
\lim_{n\to\infty} a_n = \ell \qquad (a_n \xrightarrow[n\to\infty]{} \ell)
$$
se
$$
\forall\varepsilon>0\ \ \exists\, \nu_\varepsilon\in\mathbb{N}\ \text{t.c.}\ |a_n-\ell|<\varepsilon \quad \forall n>\nu_\varepsilon .
$$

**Significato geometrico.** $\forall\varepsilon>0$ i punti $P_n=(n,a_n)$ del grafico appartengono **definitivamente** alla striscia $S_{\ell,\varepsilon}$: per quanto la striscia sia sottile, da un certo indice in poi tutti i punti ci cadono dentro (solo un numero finito ne resta fuori). $\nu_\varepsilon$ dipende in generale da $\varepsilon$: più $\varepsilon$ è piccolo, più $\nu_\varepsilon$ è grande.

### Esempio: $b_n=\dfrac1n \to 0$

```desmos-graph
left=-0.5; right=10;
top=1.2; bottom=-0.4;
grid=true
---
(1,1)
(2,0.5)
(3,0.3333)
(4,0.25)
(5,0.2)
(6,0.1667)
(7,0.1429)
(8,0.125)
(9,0.1111)
y=0.3|hidden
y=-0.3|hidden
```

*Graficamente:* i punti si avvicinano all'asse $y=0$ e rientrano in ogni striscia $S_{0,\varepsilon}$.

*Analiticamente:* sia $\varepsilon>0$ arbitrario. Si vuole $|b_n-0|<\varepsilon$:
$$
\left|\frac1n\right|<\varepsilon \iff \frac1n<\varepsilon \iff n>\frac1\varepsilon .
$$
Si prende $\nu_\varepsilon=\left[\tfrac1\varepsilon\right]+1$: allora $|b_n-0|<\varepsilon\ \ \forall n>\nu_\varepsilon$. Questa è esattamente la definizione di limite, quindi $\lim_{n\to\infty}\frac1n=0$. ∎

## Unicità del limite

**Teorema (unicità).** Se una successione $\{a_n\}$ ammette limite, questo è **unico**.

**Dimostrazione (per assurdo).** Sia $\{a_n\}$ convergente e siano $\ell_1\ne\ell_2$ due limiti. Per definizione:
$$
\forall\varepsilon>0\ \exists\,\nu_{\varepsilon,1}:\ |a_n-\ell_1|<\varepsilon\ \ \forall n>\nu_{\varepsilon,1}, \qquad
\forall\varepsilon>0\ \exists\,\nu_{\varepsilon,2}:\ |a_n-\ell_2|<\varepsilon\ \ \forall n>\nu_{\varepsilon,2}.
$$

*Idea geometrica:* $P_n\in S_{\ell_1,\varepsilon}$ definitivamente e $P_n\in S_{\ell_2,\varepsilon}$ definitivamente, quindi $P_n\in S_{\ell_1,\varepsilon}\cap S_{\ell_2,\varepsilon}$ definitivamente; ma per $\varepsilon$ abbastanza piccolo $S_{\ell_1,\varepsilon}\cap S_{\ell_2,\varepsilon}=\varnothing$: **assurdo**.

*Analiticamente:* sia $\nu_\varepsilon=\max\{\nu_{\varepsilon,1},\nu_{\varepsilon,2}\}$, così per $n>\nu_\varepsilon$ valgono **entrambe** le disuguaglianze. Si sceglie
$$
\varepsilon=\frac{|\ell_1-\ell_2|}{2}>0 .
$$
Per la disuguaglianza triangolare:
$$
|\ell_1-\ell_2| = |\ell_1-a_n+a_n-\ell_2| \le |\ell_1-a_n|+|a_n-\ell_2| < 2\varepsilon = |\ell_1-\ell_2|,
$$
cioè $|\ell_1-\ell_2|<|\ell_1-\ell_2|$, **assurdo**. Quindi $\ell_1=\ell_2$. ∎

## Successioni convergenti e limitatezza

**Definizione.** $\{a_n\}$ si dice **convergente** se $a_n\to\ell$ per qualche $\ell\in\mathbb{R}$.

**Osservazione.** $\{a_n\}$ è limitata se $\exists\, m,M$ t.c. $m\le a_n\le M\ \ \forall n$. Equivalentemente (si può scegliere $K$ opportuno) $\exists K\in\mathbb{R}$, $K>0$ t.c. $-K\le a_n\le K$, cioè $|a_n|\le K\ \ \forall n$.

**Teorema.** Sia $\{a_n\}$ convergente. Allora $\{a_n\}$ è **limitata**.

**Dimostrazione.** $a_n\to\ell$, $\ell\in\mathbb{R}$, significa
$$
\forall\varepsilon>0\ \exists\,\nu_\varepsilon:\ |a_n-\ell|<\varepsilon\ \ \forall n>\nu_\varepsilon \iff \ell-\varepsilon<a_n<\ell+\varepsilon\ \ \forall n>\nu_\varepsilon .
$$
Quindi, **definitivamente**, $a_n\in(\ell-\varepsilon,\ell+\varepsilon)$: i termini con $n>\nu_\varepsilon$ sono limitati, e restano solo un **numero finito** di elementi $a_0,a_1,\dots,a_{\nu_\varepsilon}$ fuori dalla striscia. Scelgo $\varepsilon=1$ e pongo
$$
K=\max\{\,1+|\ell|,\ |a_0|,\ |a_1|,\ \dots,\ |a_{\nu_1}|\,\}.
$$
Allora $|a_n|\le K\ \ \forall n\in\mathbb{N}$. ∎

> [!warning] Il viceversa è falso
> Limitata $\not\Rightarrow$ convergente: $(-1)^n$ è limitata ma non converge (vedi sotto).

## Non esistenza del limite

Negando la definizione:
$$
a_n\not\to\ell \iff \exists\,\varepsilon>0\ \text{t.c.}\ P_n=(n,a_n)\notin S_{\ell,\varepsilon}\ \text{per infiniti } n,
$$
cioè **infiniti** punti non appartengono alla striscia. Se ciò accade per **ogni** $\ell\in\mathbb{R}$, allora $\{a_n\}$ **non ammette limite**.

### Esempio: $a_n=(-1)^n$ non ammette limite

```desmos-graph
left=-1; right=8;
top=2; bottom=-2;
grid=true
---
(0,1)
(1,-1)
(2,1)
(3,-1)
(4,1)
(5,-1)
(6,1)
(7,-1)
```

- Scelgo $\ell=1$ come candidato: tutti i punti con $n$ **dispari** ($a_n=-1$) non stanno in $S_{1,\varepsilon}$ (per $\varepsilon<2$), quindi $a_n\not\to1$.
- Stesso discorso con $\ell=-1$: i punti con $n$ pari sono fuori.
- Le due **sottosuccessioni** $a_{2k}=1\to1$ e $a_{2k+1}=-1\to-1$ hanno limiti diversi: **2 candidati limite** ⟹ la successione non ammette limite.

> [!note] Criterio
> Se due sottosuccessioni hanno limiti diversi, $\{a_n\}$ non ammette limite ($\nexists\lim a_n$).

### Esercizio: $a_n=\sin(\pi n)$ e $a_n=\sin\!\left(n\frac\pi2\right)$

- $a_n=\sin(\pi n)$: $a_0=0,\ a_1=0,\ a_2=0,\dots$ è la successione **costante** $0$, quindi ammette limite: $\lim a_n=0$.
- $a_n=\sin\!\left(n\frac\pi2\right)$: $a_0=0,\ a_1=1,\ a_2=0,\ a_3=-1,\ a_4=0,\dots$. Sottosuccessioni:
$$
a_{2k}=0\to0,\qquad a_{4k+1}=1\to1,\qquad a_{4k+3}=-1\to-1\quad(k\to\infty).
$$
Hanno limiti diversi ⟹ $a_n$ **non ammette limite**.

## Limiti infiniti

**Definizione (divergenza a $+\infty$).** $\{a_n\}$ ha limite $+\infty$ (*tende a $+\infty$*, *diverge positivamente*) e si scrive
$$
\lim_{n\to+\infty}a_n=+\infty \quad\text{se}\quad \forall M>0\ \ \exists\,\nu_M\in\mathbb{N}\ \text{t.c.}\ a_n>M\ \ \forall n>\nu_M .
$$
Geometricamente: $\forall M>0$, $P_n=(n,a_n)\in S_M:=\{(x,y)\in\mathbb{R}^2: y>M\}$ **definitivamente** (semipiano sopra la retta $y=M$).

**Definizione (divergenza a $-\infty$).**
$$
\lim_{n\to+\infty}a_n=-\infty \quad\text{se}\quad \forall M>0\ \ \exists\,\nu_M\in\mathbb{N}\ \text{t.c.}\ a_n<-M\ \ \forall n>\nu_M ,
$$
cioè $P_n\in S_M:=\{(x,y): y<-M\}$ definitivamente.

### Esempio: $a_n=n^2\to+\infty$

```desmos-graph
left=-0.5; right=5;
top=26; bottom=-2;
grid=true
---
(0,0)
(1,1)
(2,4)
(3,9)
(4,16)
y=10|hidden
```

Sia $M>0$ arbitrario:
$$
a_n>M \iff n^2>M \iff n>\sqrt M \quad(\text{l'altra soluzione } n<-\sqrt M \text{ si scarta perché } n\ge0).
$$
Basta prendere $\nu_M=\left[\sqrt M\right]+1$: allora $a_n>M\ \ \forall n>\nu_M$. Quindi $\lim_{n\to+\infty}n^2=+\infty$. ∎

## Riepilogo dei comportamenti

| Comportamento | Definizione | Esempio |
|---|---|---|
| Converge a $\ell\in\mathbb{R}$ | $\forall\varepsilon\ \exists\nu_\varepsilon:\ \lvert a_n-\ell\rvert<\varepsilon\ \forall n>\nu_\varepsilon$ | $\frac1n\to0$ |
| Diverge a $+\infty$ | $\forall M\ \exists\nu_M:\ a_n>M\ \forall n>\nu_M$ | $n^2$ |
| Diverge a $-\infty$ | $\forall M\ \exists\nu_M:\ a_n<-M\ \forall n>\nu_M$ | $-n^2$ |
| Non ammette limite | (oscilla, $\ge2$ candidati) | $(-1)^n$, $\sin(n\pi/2)$ |
