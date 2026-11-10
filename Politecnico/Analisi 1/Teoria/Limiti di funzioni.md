---
tags:
  - analisi1
  - limiti-funzioni
  - asintoti
  - politecnico
---
# Limiti di funzioni

Fonte: Lezione 12 (26 ottobre) e Lezione 13 (4 novembre), AM1 2026-27 — **seconda parte** del corso.
Prosegue da [[Funzioni]] e [[Politecnico/Analisi 1/Teoria/Limiti di successioni|Limiti di successioni]]; continua in [[Funzioni continue e punti di discontinuità]].

In tutta la nota $f:A\subseteq\mathbb R\to\mathbb R$.

## 1. Limiti all'infinito

### $x\to+\infty$ (serve $A\supseteq(a,+\infty)$)

| | Limite | Definizione |
|---|---|---|
| (1) | $\displaystyle\lim_{x\to+\infty}f(x)=\ell\in\mathbb R$ | $\forall\varepsilon>0\ \exists\nu_\varepsilon>0$ t.c. $\lvert f(x)-\ell\rvert<\varepsilon\quad\forall x>\nu_\varepsilon,\ x\in A$ |
| (2) | $\displaystyle\lim_{x\to+\infty}f(x)=+\infty$ | $\forall M>0\ \exists\nu_M>0$ t.c. $f(x)>M\quad\forall x>\nu_M,\ x\in A$ |
| (3) | $\displaystyle\lim_{x\to+\infty}f(x)=-\infty$ | $\forall M>0\ \exists\nu_M>0$ t.c. $f(x)<-M\quad\forall x>\nu_M,\ x\in A$ |

### $x\to-\infty$ (serve $A\supseteq(-\infty,a)$)

| | Limite | Definizione |
|---|---|---|
| (4) | $\displaystyle\lim_{x\to-\infty}f(x)=\ell\in\mathbb R$ | $\forall\varepsilon>0\ \exists\nu_\varepsilon<0$ t.c. $\lvert f(x)-\ell\rvert<\varepsilon\quad\forall x<\nu_\varepsilon,\ x\in A$ |
| (5) | $\displaystyle\lim_{x\to-\infty}f(x)=+\infty$ | $\forall M>0\ \exists\nu_M<0$ t.c. $f(x)>M\quad\forall x<\nu_M,\ x\in A$ |
| (6) | $\displaystyle\lim_{x\to-\infty}f(x)=-\infty$ | $\forall M>0\ \exists\nu_M<0$ t.c. $f(x)<-M\quad\forall x<\nu_M,\ x\in A$ |

## 2. Intorni e punti di accumulazione

Per $r>0$, $x_0\in\mathbb R$: $\ \lvert x-x_0\rvert<r\iff x_0-r<x<x_0+r$.

- **Intorno** di centro $x_0$ e raggio $r$: $I_r(x_0):=\{x\in\mathbb R:\lvert x-x_0\rvert<r\}$
- **Intorno destro**: $I_r^+(x_0):=\{x\in\mathbb R:x_0<x<x_0+r\}$
- **Intorno sinistro**: $I_r^-(x_0):=\{x\in\mathbb R:x_0-r<x<x_0\}$

**Def (punto di accumulazione).** Sia $E\subseteq\mathbb R$. $x_0\in\mathbb R$ è **punto di accumulazione** per $E$ se
$$\forall r>0\qquad\big[I_r(x_0)\cap E\big]\setminus\{x_0\}\neq\varnothing .$$
Cioè: vicino quanto voglio a $x_0$ trovo sempre punti di $E$ **diversi da $x_0$**. Non serve che $x_0\in E$.

**Esempi.**
- $E=(a,b)$, $x_0\in(a,b)$: di accumulazione (anche $a$ e $b$ lo sono).
- $E=(a,x_0)\cup(x_0,b)$: $x_0$ è di accumulazione anche se $x_0\notin E$.
- $E=[x_0,b)$: $x_0$ è di accumulazione.
- $E=[a,b)\cup\{x_0\}$ con $x_0>b$: $x_0$ **non** è di accumulazione → **punto isolato**.

**Def (accumulazione da destra / da sinistra).** $x_0$ è di accumulazione **da destra** per $E$ se $\forall r>0\ [I_r^+(x_0)\cap E]\setminus\{x_0\}\neq\varnothing$; **da sinistra** se lo stesso vale con $I_r^-(x_0)$.

## 3. Limiti per $x\to x_0$

Sia $x_0$ punto di accumulazione di $A$.

**(7)** $\displaystyle\lim_{x\to x_0}f(x)=\ell\in\mathbb R$ se
$$\forall\varepsilon>0\ \exists\delta=\delta_{\varepsilon,x_0}>0\ \text{t.c.}\ \lvert f(x)-\ell\rvert<\varepsilon\quad\forall x\in I_\delta(x_0)\cap A,\ x\neq x_0 .$$
Equivalente: $\forall x\in A$ con $0<\lvert x-x_0\rvert<\delta$.

**(8)** $\displaystyle\lim_{x\to x_0}f(x)=+\infty$ se $\forall M>0\ \exists\delta>0$ t.c. $f(x)>M\ \ \forall x\in I_\delta(x_0)\cap A,\ x\neq x_0$.

**(9)** $\displaystyle\lim_{x\to x_0}f(x)=-\infty$ se $\forall M>0\ \exists\delta>0$ t.c. $f(x)<-M\ \ \forall x\in I_\delta(x_0)\cap A,\ x\neq x_0$.

> [!note] Il valore $f(x_0)$ non conta
> Il limite guarda solo i punti **vicini** a $x_0$, mai $x_0$ stesso ($x\neq x_0$). $f$ può anche non essere definita in $x_0$.

### Limiti destro e sinistro

Se $x_0$ è di accumulazione **da destra** per $A$:

**(10)** $\displaystyle\lim_{x\to x_0^+}f(x)=\ell$ se $\forall\varepsilon>0\ \exists\delta>0$ t.c. $\lvert f(x)-\ell\rvert<\varepsilon\ \ \forall x\in I_\delta^+(x_0)\cap A$.

(11), (12) analoghi con $\pm\infty$. Da **sinistra** (13)–(15): stessa cosa con $I_\delta^-(x_0)$.

**Osservazioni.**
1. $\displaystyle\lim_{x\to x_0^-}f=\ell_1\neq\ell_2=\lim_{x\to x_0^+}f\ \Rightarrow\ \nexists\lim_{x\to x_0}f$.
2. $\displaystyle\lim_{x\to x_0^-}f=\ell=\lim_{x\to x_0^+}f\ \Rightarrow\ \exists\lim_{x\to x_0}f=\ell$.
3. Se $x_0$ è di accumulazione sia da destra sia da sinistra e $\exists\lim_{x\to x_0}f=\ell$, allora esistono anche $\lim_{x\to x_0^\pm}f=\ell$.

**Esempio.** $f(x)=\sqrt x$: $\lim_{x\to0}f=\lim_{x\to0^+}f=0$, ma $\nexists\lim_{x\to0^-}f$, perché $0$ **non** è di accumulazione da sinistra per il dominio $[0,+\infty)$.

**Esempio.** $f(x)=\frac1x$, $A=(-\infty,0)\cup(0,+\infty)$, $x_0=0$:
$\lim_{x\to0^-}\frac1x=-\infty$, $\lim_{x\to0^+}\frac1x=+\infty\ \Rightarrow\ \nexists\lim_{x\to0}\frac1x$.

**Esempio.** $f(x)=\operatorname{sgn}(x)=\begin{cases}1&x>0\\0&x=0\\-1&x<0\end{cases}$:
$\lim_{x\to0^-}f=-1\neq1=\lim_{x\to0^+}f\Rightarrow\nexists\lim_{x\to0}f$ (e $f(0)=0$ non c'entra).

```desmos-graph
left=-3; right=3; top=2; bottom=-2;
---
y=\operatorname{sign}(x)
(0,0)
(0,1)|open
(0,-1)|open
```

## 4. Teorema ponte (limiti di funzioni ↔ limiti di successioni)

Se $\{x_n\}\subseteq A$, allora $b_n:=f(x_n)$ è una nuova successione.

> [!important] Teorema (ponte)
> Sia $f:A\to\mathbb R$, $x_0$ punto di accumulazione per $A$. Allora
> $$\lim_{x\to x_0}f(x)=\ell\iff\forall\{x_n\}\subseteq A\setminus\{x_0\}\ \text{con}\ x_n\to x_0:\quad\lim_{n\to\infty}f(x_n)=\ell .$$
> (vale anche con $x_0=\pm\infty$ e $\ell=\pm\infty$)

**Esempio.** $f(x)=x^2$, $x_0=0$. Sia $\{x_n\}\subseteq\mathbb R\setminus\{0\}$ con $x_n\to0$: allora $b_n=(x_n)^2\to0$ (algebra dei limiti di successioni). Vale per **ogni** tale successione, quindi $\lim_{x\to0}x^2=0$.

**Uso principale: dimostrare che un limite NON esiste.**

> [!tip] Criterio di non esistenza
> Se esistono $\{x_n\},\{y_n\}\subseteq A\setminus\{x_0\}$, entrambe $\to x_0$, con
> $$\lim_{n}f(x_n)=\ell_1\neq\ell_2=\lim_n f(y_n),$$
> allora $\nexists\lim_{x\to x_0}f(x)$.

**Esempio.** $f(x)=\cos\frac1x$, $x_0=0$.
- $x_n=\frac1{2n\pi}\to0$: $f(x_n)=\cos(2n\pi)=1\to1$.
- $y_n=\frac1{(2n+1)\pi}\to0$: $f(y_n)=\cos((2n+1)\pi)=-1\to-1$.

Quindi $\nexists\lim_{x\to0}\cos\frac1x$.

## 5. Teoremi sui limiti

L'**algebra dei limiti** resta invariata rispetto alle successioni (vedi [[Algebra dei limiti e teoremi sui limiti]]), con le stesse forme indeterminate.

**Teorema (permanenza del segno).** $x_0$ di accumulazione per $A$. Se $\lim_{x\to x_0}f(x)=M>0$ allora $\exists\delta>0$ t.c.
$$f(x)>\frac M2\ (>0)\qquad\forall x\in I_\delta(x_0)\cap A,\ x\neq x_0 .$$

**Teorema (unicità del limite).** Se esiste $\lim_{x\to x_0}f(x)=\ell$, allora il limite è unico.

**Teorema (dei due carabinieri).** Siano $f,g,h$ con $g(x)\le f(x)\le h(x)$ per ogni $x\in[I_\sigma(x_0)\setminus\{x_0\}]\cap A$ (per qualche $\sigma>0$). Se
$$\lim_{x\to x_0}g(x)=\lim_{x\to x_0}h(x)=\ell\quad\Longrightarrow\quad\exists\lim_{x\to x_0}f(x)=\ell .$$

**Lemma.** $f(x)\xrightarrow{x\to x_0}0\iff\lvert f(x)\rvert\xrightarrow{x\to x_0}0$.

**Corollario.** Se $f(x)\to0$ per $x\to x_0$ e $g$ è **limitata** in un intorno di $x_0$, allora $\lim_{x\to x_0}f(x)g(x)=0$.
(Es.: $x\sin\frac1x\to0$ per $x\to0$.)

## 6. Limiti notevoli

| Limite | | Limite | |
|---|---|---|---|
| $\displaystyle\lim_{x\to0}\sin x$ | $=0$ | $\displaystyle\lim_{x\to+\infty}\Big(1+\frac1x\Big)^x$ | $=e$ |
| $\displaystyle\lim_{x\to0}\cos x$ | $=1$ | $\displaystyle\lim_{x\to0}\frac{e^x-1}{x}$ | $=1$ |
| $\displaystyle\lim_{x\to0}\frac{\sin x}{x}$ | $=1$ | $\displaystyle\lim_{x\to0}\frac{\log(1+x)}{x}$ | $=1$ |
| $\displaystyle\lim_{x\to0}\frac{1-\cos x}{x^2}$ | $=\dfrac12$ | $\displaystyle\lim_{x\to0}\frac{(1+x)^\alpha-1}{x}$ | $=\alpha\quad\forall\alpha\in\mathbb R$ |

**Gerarchia degli infiniti** ($a>1$, $\alpha>0$):
$$\lim_{x\to+\infty}\frac{\log_a x}{x^\alpha}=0,\qquad\lim_{x\to+\infty}\frac{x^\alpha}{a^x}=0 .$$

**Esempio ($0\cdot\infty$).** $\displaystyle\lim_{x\to0^+}x^\alpha\log_a x$ con $\alpha>0$, $a>1$. Sostituisco $y=\frac1x$ ($y\to+\infty$ per $x\to0^+$):
$$\lim_{x\to0^+}x^\alpha\log_a x=\lim_{y\to+\infty}\Big(\frac1y\Big)^\alpha\log_a\Big(\frac1y\Big)=\lim_{y\to+\infty}\frac{-\log_a y}{y^\alpha}=0\quad\text{(gerarchia)}.$$
$$\boxed{\lim_{x\to0^+}x^\alpha\log_a x=0\qquad\forall\alpha>0,\ a>1}$$

**Esempi (forme $\infty^0$, $0^0$)** — si riscrive $f^g=e^{g\log f}$:
$$\lim_{x\to+\infty}x^{1/x}=\lim_{x\to+\infty}e^{\frac{\log x}{x}}=e^0=1,\qquad\lim_{x\to0^+}x^x=\lim_{x\to0^+}e^{x\log x}=e^0=1 .$$

## 7. Infinitesimi e infiniti

**Def.** $f$ è **infinitesima** per $x\to x_0$ (o $x\to\pm\infty$) se $\lim f=0$; è **infinita** se $\lim f=\pm\infty$.

**Confronto tra infinitesimi** ($x_0\in\mathbb R\cup\{\pm\infty\}$). Siano $f,g$ infinitesime per $x\to x_0$:

| $\displaystyle\lim_{x\to x_0}\frac{f(x)}{g(x)}$ | allora |
|---|---|
| $0$ | $f$ infinitesimo di **ordine superiore** a $g$ |
| $\pm\infty$ | $f$ infinitesimo di **ordine inferiore** a $g$ |
| $\ell\neq0$ finito | $f$ e $g$ dello **stesso ordine** |
| $\nexists$ | **non paragonabili** |

Caso speciale $\ell=1$: $f$ e $g$ sono **asintoticamente equivalenti**, $f\sim g$ per $x\to x_0$.

**Confronto tra infiniti.** Siano $f,g$ infinite per $x\to x_0$:

| $\displaystyle\lim_{x\to x_0}\frac{f(x)}{g(x)}$ | allora |
|---|---|
| $0$ | $f$ infinito di **ordine inferiore** a $g$ |
| $\pm\infty$ | $f$ infinito di **ordine superiore** a $g$ |
| $\ell\neq0$ finito | stesso ordine |
| $\nexists$ | non paragonabili |

> [!warning] Attenzione ai versi
> Per gli infinitesimi "rapporto $\to0$" = ordine **superiore** (va a zero più in fretta); per gli infiniti "rapporto $\to0$" = ordine **inferiore**.

**Def ("o piccolo").** Se $\displaystyle\lim_{x\to x_0}\frac{f(x)}{g(x)}=0$ si scrive $f(x)=o(g(x))$ per $x\to x_0$. In particolare $\displaystyle\lim_{x\to x_0}\frac{o(g(x))}{g(x)}=0$.

**Esempi.**
- $x^3=o(x^2)$ per $x\to0$: $\frac{x^3}{x^2}=x\to0$.
- $x^2=o(x^3)$ per $x\to+\infty$: $\frac{x^2}{x^3}=\frac1x\to0$.

Regole pratiche e legame $\sim$/o piccolo: [[Confronti e stime asintotiche]].

## 8. Limiti di funzioni monotone

> [!important] Teorema
> Sia $f:(a,b)\to\mathbb R$ **crescente** e $x_0\in(a,b)$. Allora
> $$\lim_{x\to x_0^-}f(x)=\sup_{a<x<x_0}f(x),\qquad\lim_{x\to x_0^+}f(x)=\inf_{x_0<x<b}f(x).$$
> Se $f$ è **decrescente**:
> $$\lim_{x\to x_0^-}f(x)=\inf_{a<x<x_0}f(x),\qquad\lim_{x\to x_0^+}f(x)=\sup_{x_0<x<b}f(x).$$

Quindi i limiti destro e sinistro di una funzione monotona **esistono sempre** (finiti). Lo stesso agli estremi:
- $f$ crescente in $(a,+\infty)\Rightarrow\lim_{x\to+\infty}f=\sup_{x>a}f$
- $f$ decrescente in $(a,+\infty)\Rightarrow\lim_{x\to+\infty}f=\inf_{x>a}f$
- $f$ crescente in $(-\infty,a)\Rightarrow\lim_{x\to-\infty}f=\inf_{x<a}f$
- $f$ decrescente in $(-\infty,a)\Rightarrow\lim_{x\to-\infty}f=\sup_{x<a}f$

(qui sup/inf possono valere $\pm\infty$). È l'analogo del teorema di regolarità delle successioni monotone, vedi [[Successioni monotone, infinitesimi e limiti notevoli]].

## 9. Asintoti

### Verticale
**Def.** Se $\lim_{x\to x_0}f(x)=\pm\infty$ (oppure $\lim_{x\to x_0^-}f=\pm\infty$ e $\lim_{x\to x_0^+}f=\mp\infty$), la retta $x=x_0$ è **asintoto verticale** per $f$.
- Se solo $\lim_{x\to x_0^-}f=\pm\infty$: **asintoto verticale sinistro**.
- Se solo $\lim_{x\to x_0^+}f=\pm\infty$: **asintoto verticale destro**.

**Esempi.** $f(x)=\frac1x$: $x=0$ asintoto verticale. $f(x)=\frac1{\sqrt x}$ su $(0,+\infty)$: $\lim_{x\to0^+}f=+\infty$, $x=0$ asintoto verticale **destro**.

### Orizzontale
**Def.** Se $\lim_{x\to\pm\infty}f(x)=b\in\mathbb R$, la retta $y=b$ è **asintoto orizzontale** per $x\to\pm\infty$.

**Esempi.**
- $f(x)=\arctan x$: $y=\frac\pi2$ per $x\to+\infty$, $y=-\frac\pi2$ per $x\to-\infty$.
- $f(x)=\frac{\sin x}{x}$ su $\mathbb R\setminus\{0\}$: $y=0$ per $x\to\pm\infty$ (il grafico lo attraversa infinite volte: un asintoto può essere intersecato).

### Obliquo
**Def.** Sia $f:(c,+\infty)\to\mathbb R$. La retta $y=mx+q$ è **asintoto** per $x\to+\infty$ se
$$\lim_{x\to+\infty}\big[f(x)-mx-q\big]=0 .$$
Se $m=0$ è orizzontale, se $m\neq0$ è **obliquo**. (Analogo per $x\to-\infty$.)

> [!important] Teorema (calcolo di $m$ e $q$)
> $f$ ha asintoto $y=mx+q$ per $x\to+\infty$ $\iff$ esistono **finiti** i limiti
> $$m=\lim_{x\to+\infty}\frac{f(x)}{x},\qquad q=\lim_{x\to+\infty}\big[f(x)-mx\big].$$

*Dim.* ($\Rightarrow$) Per definizione $f(x)-mx-q\to0$. Dividendo per $x$: $\frac{f(x)}x-m-\frac qx\to0$ e $\frac qx\to0$, quindi $\frac{f(x)}x\to m$. Poi $f(x)-mx=(f(x)-mx-q)+q\to q$.
($\Leftarrow$) Se $m,q$ esistono finiti, dal secondo limite $f(x)-mx-q\to0$: è la definizione. $\blacksquare$

**Esempio (asintoto che non c'è).** $f(x)=2x+\sin x$:
$\frac{f(x)}x=2+\frac{\sin x}x\to2=m$, ma $f(x)-2x=\sin x$ non ha limite. Nessun asintoto (ci serve **anche** $q$ finito).

Dimostrazione d'esame: [[4.1 Asintoti (★★)]].

## Collegamenti
- Esercizi: [[Limiti di funzioni — Esercizi]]
- Continua: [[Funzioni continue e punti di discontinuità]]
- PDF: [[Lezione 12 (26 ottobre) AM1 2026-27.pdf|Lezione 12]] · [[Lezione 13 (4 novembre) AM1 2026-27.pdf|Lezione 13]]
