---
date: 2026-09-07
subject: matematica
topic: algebra - polinomi
tags:
  - matematica
  - algebra
  - polinomi
  - equazioni
---
# Lezione 3: Algebra — Warm-up

Corso di ripasso Matematica, laboratorio FDS (MOOC MAT101 Polimi).

## A) Polinomi

### Cos'è un polinomio

Un **polinomio** in $x$ è una somma finita di termini del tipo $c \cdot x^n$, dove:
- $c$ è un coefficiente (numero reale),
- $n$ è un esponente **intero non negativo** ($0, 1, 2, 3, \dots$).

Quindi **non sono ammessi**: radici della variabile ($\sqrt{x}$, perché è $x^{1/2}$), la variabile a denominatore ($1/x = x^{-1}$), esponenti negativi o frazionari.

### Esercizio 1 — quali sono polinomi?

| Espressione | È un polinomio? | Perché |
|---|---|---|
| $x^2 - 3x + 5$ | **Sì** | Solo potenze intere non negative di $x$ (2, 1, 0) |
| $\sqrt{x}$ | **No** | Equivale a $x^{1/2}$, esponente non intero |
| $\dfrac{4x^2-2}{x}$ | **No** | Semplificando: $4x - 2x^{-1}$, contiene $x^{-1}$ |
| $4 - \sqrt{x}$ | **No** | Contiene $\sqrt{x} = x^{1/2}$ |

> ponytail: la tabella segue la traccia originale; se l'OCR ha spezzato male le espressioni del testo, il criterio per riconoscerle resta questo: solo esponenti interi ≥ 0.

### Esercizio 2 — costruire polinomi con radici date

Se un polinomio ha radice $r$, allora è divisibile per $(x-r)$: si costruisce come prodotto di fattori $(x-r_i)$.

**(a) Radici 1, 2, 3:**
$$
p(x) = (x-1)(x-2)(x-3)
$$

**(b) Una radice sia 0:**
$$
p(x) = x \quad \text{(qualunque polinomio con termine noto } =0\text{ va bene, es. } x^2+x\text{)}
$$

**(c) Radici 1, 2, 3 e grado 4:**
Serve un quarto fattore qualsiasi (anche ripetendo una radice):
$$
p(x) = (x-1)(x-2)(x-3)(x-4)
$$
oppure, con radice doppia:
$$
p(x) = (x-1)^2(x-2)(x-3)
$$

**(d) Divisibile per $(x^2-25)$:**
Basta moltiplicare per un fattore qualsiasi, es. $(x+1)$:
$$
p(x) = (x^2-25)(x+1) = (x-5)(x+5)(x+1)
$$

## B) Quiz

### 1. Ultima cifra di $7^{2001}$

Le potenze di 7 hanno cifra finale periodica di periodo 4:
$$
7^1=7,\quad 7^2=49,\quad 7^3=343,\quad 7^4=2401,\quad 7^5=16807,\dots
$$
cifre finali: $7, 9, 3, 1, 7, 9, 3, 1, \dots$

$2001 = 4 \cdot 500 + 1$, quindi $7^{2001}$ ha lo stesso ultimo digit di $7^1$.

**Risposta: l'ultima cifra è 7.**

### 2. Quanti dei seguenti numeri sono minori di 1? (per $x>0,\ x\ne 1$)

$$
x, \quad \frac1x, \quad \frac{x}{1+x^2}, \quad \frac{1+x}{2}, \quad \frac{2x}{1+x^2}
$$

Metodo: confrontare ciascuna espressione con 1 algebricamente, non per tentativi.

- **$x/(1+x^2) < 1$**: equivale a $x < 1+x^2 \iff x^2-x+1>0$. Discriminante $=1-4=-3<0$ → **sempre vero**, per ogni $x$.
- **$2x/(1+x^2) < 1$**: equivale a $2x < 1+x^2 \iff (x-1)^2>0$ → **sempre vero** perché $x\ne 1$.
- **$x$ e $1/x$**: il loro prodotto è $1$. Se $x\ne1$, uno dei due è $<1$ e l'altro $>1$ (mai entrambi uguali). Quindi **esattamente uno** dei due è minore di 1.
- **$(1+x)/2 < 1 \iff x<1$**: vero solo se $0<x<1$, falso se $x>1$.

Sommando: il conteggio è **sempre almeno 3** (i due sempre veri + uno tra $x,1/x$), e diventa **4** se $0<x<1$ (si aggiunge anche $(1+x)/2$).

**Risposta: 3 se $x>1$, 4 se $0<x<1$** — dipende da dove sta $x$ rispetto a 1; le prime due frazioni e una tra $x,1/x$ sono garantite sempre.

### 3. Condizione su $c$ (equazione $x^3+ax^2+bx+c=0$)

Siano $p,q,r$ le tre radici. Per le formule di Viète:
$$
p+q+r=-a,\qquad pq+pr+qr=b,\qquad pqr=-c
$$

Vogliamo che **due** radici sommino a zero, es. $p+q=0 \Rightarrow q=-p$. Allora la terza radice è:
$$
r = -a-(p+q) = -a
$$
Poiché $r=-a$ è radice, sostituendo nell'equazione:
$$
(-a)^3+a(-a)^2+b(-a)+c=0 \;\Rightarrow\; -a^3+a^3-ab+c=0 \;\Rightarrow\; c=ab
$$

**Risposta: $c = ab$.**

### 4. $a^3+b^3$ se $a,b$ risolvono $x^2-3x+1=0$

Per Viète: $a+b=3$, $ab=1$. Usando l'identità:
$$
a^3+b^3=(a+b)^3-3ab(a+b)
$$
$$
= 27 - 3\cdot1\cdot3 = 27-9 = 18
$$

**Risposta: 18.**
