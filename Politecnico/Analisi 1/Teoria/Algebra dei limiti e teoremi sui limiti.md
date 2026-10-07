---
tags:
  - analisi1
  - successioni
  - limiti
  - politecnico
---
Prosegue da [[Limiti di successioni]].

## Successioni regolari

**Definizione.** $\{a_n\}$ è **regolare** se ammette limite (converge o diverge); se non ammette limite si dice **irregolare**.

| Successione | Limite | Tipo |
|---|---|---|
| $a_n=n^2$ | $+\infty$ | regolare (limite infinito) |
| $b_n=\frac1n$ | $0$ | regolare (limite finito) |
| $c_n=(-1)^n$ | non esiste | irregolare |

## Algebra dei limiti

Siano $a_n\to a$ e $b_n\to b$ con $a,b\in\overline{\mathbb{R}}=\mathbb{R}\cup\{\pm\infty\}$. Le tabelle dicono quando il limite dell'operazione è determinato dai limiti dei singoli termini.

### Somma $a_n+b_n$

| $\lim a_n$ | $\lim b_n$ | $\lim (a_n+b_n)$ |
|---|---|---|
| $a$ | $b$ | $a+b$ |
| $\pm\infty$ | $b$ | $\pm\infty$ |
| $a$ | $\pm\infty$ | $\pm\infty$ |
| $+\infty$ | $+\infty$ | $+\infty$ |
| $-\infty$ | $-\infty$ | $-\infty$ |

> [!warning] Forma indeterminata
> $+\infty-\infty$ (FI): il limite non è determinato dai soli limiti di $a_n,b_n$.

### Prodotto $a_n\cdot b_n$

| $\lim a_n$ | $\lim b_n$ | $\lim a_nb_n$ |
|---|---|---|
| $a$ | $b$ | $a\cdot b$ |
| $+\infty$ | $b>0$ | $+\infty$ |
| $+\infty$ | $b<0$ | $-\infty$ |
| $a>0$ | $+\infty$ | $+\infty$ |
| $a<0$ | $+\infty$ | $-\infty$ |
| $+\infty$ | $+\infty$ | $+\infty$ |
| $-\infty$ | $-\infty$ | $+\infty$ |
| $-\infty$ | $+\infty$ | $-\infty$ |

(regola dei segni, simmetrica per $-\infty$ e per lo scambio $a_n\leftrightarrow b_n$).

> [!warning] Forma indeterminata
> $0\cdot(\pm\infty)$ (FI), cioè $a=0$ e $b=\pm\infty$.

### Quoziente $a_n/b_n$ (con $b_n\ne0$ definitivamente)

| $\lim a_n$ | $\lim b_n$ | $\lim \frac{a_n}{b_n}$ |
|---|---|---|
| $a$ | $b\ne0$ | $a/b$ |
| $a$ | $\pm\infty$ | $0$ |
| $\pm\infty$ | $b>0$ / $b<0$ | $\pm\infty$ (regola dei segni) |
| $a\ne0$ | $0$ | vedi sotto |

Caso $b_n\to0$, $a\neq0$ (il segno si ottiene dal cambio segni, $a$ per $b_n$):
- $b_n$ definitivamente **positivo** ⟹ $\pm\infty$ col segno di $a$ ($+\infty$ se $a>0$);
- $b_n$ definitivamente **negativo** ⟹ segno opposto a quello di $a$;
- altrimenti ($b_n$ cambia segno infinite volte) ⟹ **irregolare**.

> [!warning] Forme indeterminate
> $\dfrac00$ e $\dfrac{\pm\infty}{\pm\infty}$ (FI).

### Potenza $a_n^{b_n}$ (con $a_n>0$)

| $\lim a_n$ | $\lim b_n$ | $\lim a_n^{b_n}$ |
|---|---|---|
| $a>0$ | $b$ | $a^b$ |
| $0\le a<1$ | $+\infty$ | $0$ |
| $0\le a<1$ | $-\infty$ | $+\infty$ |
| $a>1$ | $+\infty$ | $+\infty$ |
| $a>1$ | $-\infty$ | $0$ |
| $+\infty$ | $b>0$ | $+\infty$ |
| $+\infty$ | $b<0$ | $0$ |
| $+\infty$ | $+\infty$ | $+\infty$ |
| $+\infty$ | $-\infty$ | $0$ |

### Casi esclusi: forme indeterminate

$$
+\infty-\infty;\quad 0\cdot(\pm\infty);\quad \frac00;\quad \frac{\pm\infty}{\pm\infty};\quad 0^0;\quad 1^{\pm\infty};\quad (\pm\infty)^0 .
$$

In una FI il limite **dipende dalle successioni scelte**: si risolve con manipolazioni algebriche (raccoglimenti, razionalizzazioni, ecc.).

### Esempio: il limite del quoziente può non esistere

Siano $a_n=1$ e $b_n=\dfrac{(-1)^n}{n}$, con $a_n\to1$, $b_n\to0$. Allora
$$
\lim_{n\to\infty}\frac{a_n}{b_n}=\lim_{n\to\infty}\frac{n}{(-1)^n}=\lim_{n\to\infty}(-1)^n n \quad\text{non ammette limite.}
$$
Posto $c_n:=\frac{a_n}{b_n}$: $c_{2n}\to+\infty$, $c_{2n+1}\to-\infty$ ⟹ il limite è **irregolare**. (Qui $b_n$ cambia segno infinite volte, come nel caso "altrimenti" sopra.)

### Esempi di risoluzione di FI

**1)** $\alpha_n=(n+1)^2-(n-1)^2$, $\ \lim\alpha_n=[+\infty-\infty]$ FI. Si sviluppa:
$$
\alpha_n=n^2+1+2n-n^2-1+2n=4n\ \Rightarrow\ \lim\alpha_n=\lim 4n=+\infty .
$$

**2)** $\beta_n=(n+1)^2-(n+3)^2$, $\ \lim\beta_n=[+\infty-\infty]$ FI.
$$
\beta_n=n^2+1+2n-n^2-9-6n=-4n-8\ \Rightarrow\ \lim\beta_n=\lim(-4n-8)=-\infty .
$$

**3)** $\alpha_n=\dfrac{n+1}{n^2}$, $\ \dfrac{+\infty}{+\infty}$ FI. Raccolgo $n$:
$$
\alpha_n=\frac{n\left(1+\frac1n\right)}{n^2}=\frac{1+\frac1n}{n}\ \Rightarrow\ \lim\alpha_n=\frac{1}{+\infty}=0 .
$$

**4)** $\beta_n=\dfrac{n-1}{n}$, $\ \dfrac{+\infty}{+\infty}$ FI.
$$
\beta_n=\frac{n\left(1-\frac1n\right)}{n}=1-\frac1n\ \Rightarrow\ \lim\beta_n=1 .
$$

**5)** $\alpha_n=\dfrac{1/n^2}{1/n}$, $\ \dfrac00$ FI.
$$
\alpha_n=\frac1{n^2}\cdot n=\frac1n\ \Rightarrow\ \lim\alpha_n=0 .
$$

**6)** $\beta_n=\dfrac{1/n^2}{1/n^3}$, $\ \dfrac00$ FI.
$$
\beta_n=\frac1{n^2}\cdot n^3=n\ \Rightarrow\ \lim\beta_n=+\infty .
$$

Stessa forma $\frac00$ (o $\frac\infty\infty$), risultati diversi ($0$, $1$, $+\infty$): per questo sono *indeterminate*.

## Teorema (limite della somma)

**Teorema.** Se $a_n\to a\in\mathbb{R}$ e $b_n\to b\in\mathbb{R}$, allora $a_n+b_n\to a+b$.

**Dimostrazione.** Per ipotesi:
$$
\forall\varepsilon>0\ \exists\,\nu_{\varepsilon,1}\in\mathbb{N}:\ |a_n-a|<\varepsilon\ \ \forall n>\nu_{\varepsilon,1},
\qquad
\forall\varepsilon>0\ \exists\,\nu_{\varepsilon,2}\in\mathbb{N}:\ |b_n-b|<\varepsilon\ \ \forall n>\nu_{\varepsilon,2}.
$$
Definisco $\nu_\varepsilon:=\max\{\nu_{\varepsilon,1},\nu_{\varepsilon,2}\}$: per $n>\nu_\varepsilon$ valgono **entrambe**. Allora, per la **disuguaglianza triangolare**,
$$
|(a_n+b_n)-(a+b)|=|a_n-a+b_n-b|\le\underbrace{|a_n-a|}_{<\varepsilon}+\underbrace{|b_n-b|}_{<\varepsilon}<2\varepsilon .
$$
Poiché $\varepsilon>0$ è arbitrario, anche $2\varepsilon$ lo è (basta applicare l'ipotesi con $\varepsilon/2$): $\forall\varepsilon>0\ \exists\nu\in\mathbb{N}$ t.c. $|(a_n+b_n)-(a+b)|<\varepsilon\ \forall n>\nu$, cioè $a_n+b_n\to a+b$. ∎

## Teorema di permanenza del segno

**Teorema.** Se $a_n\to a$ e $a>0$, allora $\exists\,\nu\in\mathbb{N}$ t.c. $a_n>0\ \ \forall n>\nu$ (cioè $a_n>0$ **definitivamente**).

**Dimostrazione.** Per definizione, $\forall\varepsilon>0\ \exists\,\nu_\varepsilon$ t.c. $|a_n-a|<\varepsilon\ \forall n>\nu_\varepsilon$, ovvero
$$
-\varepsilon<a_n-a<\varepsilon \iff a-\varepsilon<a_n<a+\varepsilon .
$$
Scelgo $\varepsilon=\dfrac a2>0$ (possibile perché $a>0$):
$$
\underbrace{a-\frac a2}_{=a/2>0}<a_n<a+\frac a2\qquad\forall n>\nu_{a/2}
\ \Rightarrow\ a_n>\frac a2>0\ \ \forall n>\nu_{a/2}. \ ∎
$$

**Corollario.** Se $a_n\to a$ e $a_n\ge0\ \ \forall n\in\mathbb{N}$ (o definitivamente), allora $a\ge0$.

*Dimostrazione (per assurdo).* Suppongo $a<0$. Applicando il teorema di permanenza del segno a $-a_n\to-a>0$ si deduce $a_n<0$ definitivamente, in contraddizione con $a_n\ge0$. Quindi $a\ge0$. ∎

> [!warning] Osservazione: il segno stretto non si conserva al limite
> Se $a_n\to a$ e $a_n>0\ \forall n$, **non** si può concludere $a>0$, solo $a\ge0$. Esempio: $a_n=\frac1n>0\ \forall n$ ma $a_n\to0$.

## Corollario (proprietà di confronto)

**Teorema.** Se $a_n\to a$, $b_n\to b$ e $a_n\ge b_n\ \ \forall n\in\mathbb{N}$, allora $a\ge b$.

**Dimostrazione.** Definisco la successione $c_n:=a_n-b_n$. Per ipotesi $c_n\ge0\ \forall n$. Per il teorema sull'algebra dei limiti (somma, con $-b_n\to-b$):
$$
c_n\xrightarrow[n\to\infty]{}a-b .
$$
Per il corollario della permanenza del segno, $c_n\ge0\Rightarrow a-b\ge0$, cioè $a\ge b$. ∎

## Teorema dei due carabinieri

**Teorema.** Siano $\{a_n\},\{b_n\},\{c_n\}$ tre successioni tali che
$$
a_n\le c_n\le b_n\qquad\text{(definitivamente)}.
$$
Se $\displaystyle\lim_{n\to\infty}a_n=\lim_{n\to\infty}b_n=\ell\in\mathbb{R}$, allora $\displaystyle\lim_{n\to\infty}c_n=\ell$.

**Dimostrazione.** Per ipotesi:
$$
\forall\varepsilon>0\ \exists\,\nu_{\varepsilon,1}:\ |a_n-\ell|<\varepsilon\ \ \forall n>\nu_{\varepsilon,1},
\qquad
\forall\varepsilon>0\ \exists\,\nu_{\varepsilon,2}:\ |b_n-\ell|<\varepsilon\ \ \forall n>\nu_{\varepsilon,2}.
$$
Sia $\nu_\varepsilon:=\max\{\nu_{\varepsilon,1},\nu_{\varepsilon,2}\}$. Allora $\forall n>\nu_\varepsilon$:
$$
|a_n-\ell|<\varepsilon\iff \ell-\varepsilon<a_n<\ell+\varepsilon,\qquad
|b_n-\ell|<\varepsilon\iff \ell-\varepsilon<b_n<\ell+\varepsilon .
$$
Quindi
$$
\ell-\varepsilon<a_n\le c_n\le b_n<\ell+\varepsilon
\iff \ell-\varepsilon<c_n<\ell+\varepsilon
\iff |c_n-\ell|<\varepsilon\quad\forall n>\nu_\varepsilon ,
$$
cioè $\forall\varepsilon>0\ \exists\,\nu_\varepsilon\in\mathbb{N}$ t.c. $|c_n-\ell|<\varepsilon\ \forall n>\nu_\varepsilon$: $c_n\to\ell$. ∎

*Idea:* $c_n$ è "schiacciata" tra due successioni (i carabinieri) che vanno nello stesso punto $\ell$, quindi deve andarci anche lei.

---

## Collegamenti

- Prosegue in [[Successioni monotone, infinitesimi e limiti notevoli]]
- [[Limiti di successioni]]
- [[Successioni]]
