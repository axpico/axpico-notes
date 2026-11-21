---
tags:
  - analisi1
  - derivate
  - calcolo-differenziale
  - politecnico
---
# Punti di non derivabilità, massimi e minimi relativi

Fonte: [[Lezione 17 (16 novembre) AM1 2026-27.pdf|Lezione 17 (16 novembre)]].
Prosegue da [[Derivate]]; continua in [[Teoremi di Rolle e Lagrange, monotonia]].

## 1. Punti di non derivabilità

**Def.** Sia $f:(a,b)\to\mathbb R$, $x_0\in(a,b)$. Se il limite del rapporto incrementale
$$\lim_{h\to0}\frac{f(x_0+h)-f(x_0)}h$$
**non esiste** oppure è **infinito**, allora $x_0$ è un **punto di non derivabilità**.

**Def. (derivate destra e sinistra)**
$$f'_+(x_0)=\lim_{h\to0^+}\frac{f(x_0+h)-f(x_0)}h\qquad f'_-(x_0)=\lim_{h\to0^-}\frac{f(x_0+h)-f(x_0)}h$$

$f$ è derivabile in $x_0$ $\iff$ $f'_+(x_0)$ e $f'_-(x_0)$ esistono, sono finite e uguali.

> [!note] Tutti i punti di discontinuità sono anche punti di non derivabilità
> È la contronominale di [[Derivate#4. Derivabile ⇒ continua|derivabile ⇒ continua]].

### a) Punto angoloso
$f'_+(x_0)=\ell_1$, $f'_-(x_0)=\ell_2$ **finite** ma $\ell_1\ne\ell_2$.

*Esempio:* $f(x)=|x|$, $x_0=0$:
$$\lim_{h\to0^+}\frac{|h|}h=\lim_{h\to0^+}\frac hh=1,\qquad \lim_{h\to0^-}\frac{|h|}h=\lim_{h\to0^-}\frac{-h}h=-1 .$$
$\Rightarrow x_0=0$ è un punto angoloso.

### b) Flesso a tangente verticale
$$\lim_{h\to0}\frac{f(x_0+h)-f(x_0)}h=+\infty\quad(\text{oppure }-\infty)$$
La tangente al grafico $G_f$ in $x_0$ è **parallela all'asse $y$**.

*Esempio:* $f(x)=\sqrt[3]x$, $x_0=0$:
$$\lim_{h\to0}\frac{\sqrt[3]h}h=\lim_{h\to0}\frac1{h^{2/3}}=+\infty .$$

### c) Cuspide
I limiti destro e sinistro sono infiniti **di segno opposto**: $f'_+(x_0)=+\infty$ e $f'_-(x_0)=-\infty$ (o viceversa).

*Esempio:* $f(x)=\sqrt[3]{|x|}$, $x_0=0$:
$$\lim_{h\to0^+}\frac{\sqrt[3]{h}}h=\lim_{h\to0^+}\frac1{h^{2/3}}=+\infty,\qquad \lim_{h\to0^-}\frac{\sqrt[3]{-h}}h=\lim_{h\to0^-}-\frac1{|h|^{2/3}}=-\infty .$$

```desmos-graph
left=-3; right=3;
top=2.5; bottom=-2;
---
y=|x|
y=\sqrt[3]{x}
y=\sqrt[3]{|x|}
```

### d) Altri casi (misti / limite inesistente)
- $f(x)=\begin{cases}\sqrt[3]x & x\ge0\\ -x & x<0\end{cases}$, $x_0=0$. È continua in $0$ ($\lim_{x\to0^\pm}f=0=f(0)$), ma
$$f'_+(0)=\lim_{h\to0^+}\frac{\sqrt[3]h}h=+\infty,\qquad f'_-(0)=\lim_{h\to0^-}\frac{-h}h=-1 ,$$
quindi $0$ è punto di non derivabilità (una derivata infinita, l'altra finita).
- $f(x)=\begin{cases}x\sin\frac1x & x\ne0\\ 0 & x=0\end{cases}$. È continua in $0$ ($|x\sin\frac1x|\le|x|\to0$), ma
$$\lim_{h\to0}\frac{h\sin\frac1h}h=\lim_{h\to0}\sin\frac1h\quad\nexists ,$$
quindi $0$ è punto di non derivabilità (il limite non esiste).

## 2. Funzione derivata

Se $f:(a,b)\to\mathbb R$ è derivabile in $(a,b)$ (cioè derivabile in ogni $x_0\in(a,b)$), la **funzione derivata** è
$$f':(a,b)\to\mathbb R,\qquad x\mapsto f'(x).$$

*Esempio:* $f(x)=\log(3+\sin x)$ è derivabile $\forall x\in\mathbb R$ e $f'(x)=\dfrac{\cos x}{3+\sin x}$.

*Esempio importante:* $f(x)=\begin{cases}x^2\sin\frac1x & x\ne0\\ 0 & x=0\end{cases}$.
- **Continuità in 0:** $\lim_{x\to0}x^2\sin\frac1x=0=f(0)$.
- **Derivabilità in 0:** $\displaystyle\lim_{h\to0}\frac{h^2\sin\frac1h}h=\lim_{h\to0}h\sin\frac1h=0$, quindi $f'(0)=0$.
- **Per $x\ne0$** (composizione di funzioni derivabili):
$$f'(x)=2x\sin\tfrac1x+x^2\cos\tfrac1x\cdot\left(-\tfrac1{x^2}\right)=2x\sin\tfrac1x-\cos\tfrac1x .$$

Quindi $f$ è derivabile su tutto $\mathbb R$ con $f'(x)=\begin{cases}2x\sin\frac1x-\cos\frac1x & x\ne0\\ 0 & x=0\end{cases}$.

> [!warning] Oss.
> $\lim_{x\to0}f'(x)=\lim_{x\to0}\left(2x\sin\frac1x-\cos\frac1x\right)$ **non esiste**, anche se $f'(0)=0$ esiste. Quindi in generale
> $$\lim_{x\to x_0}f'(x)\ne f'(x_0)$$
> ($f'$ può non essere continua). Il viceversa parziale è il [[Teoremi di Rolle e Lagrange, monotonia#6. Limite della derivata|teorema del limite della derivata]].

## 3. Massimi e minimi relativi

**Def.** Sia $f:A\subseteq\mathbb R\to\mathbb R$. $x_0\in A$ è **punto di massimo (minimo) relativo** se esiste un intorno di $x_0$, cioè $\exists\delta>0$, t.c.
$$f(x)\le f(x_0)\quad(\ge)\qquad\forall x\in I_\delta(x_0)\cap A .$$
$x_0$ è un **punto di estremo relativo** se è punto di massimo o di minimo relativo.

Esempio su $f:[a,b]\to\mathbb R$: nel grafico, $x_1,x_2$ sono punti di max relativo, $a,b,x_3$ punti di min relativo (anche gli estremi dell'intervallo possono esserlo).

> [!note] Oss.
> $x_0$ max assoluto $\Rightarrow$ $x_0$ max relativo. Il viceversa è **falso**.

**Def.** Sia $f:(a,b)\to\mathbb R$ e $x_0\in(a,b)$ (punto **interno**). $x_0$ è **punto critico** (o **stazionario**) per $f$ se $\exists f'(x_0)=0$.

*Esempio:* $f(x)=2-x^2$, $f'(x)=-2x=0\iff x=0$. $x=0$ è punto critico (ed è max assoluto); la tangente in $0$ è $y=2$.

**Oss.** La tangente in $x_0$ è $y=f'(x_0)(x-x_0)+f(x_0)$; se $x_0$ è critico diventa $y=f(x_0)$, **parallela all'asse $x$**.

## 4. Teorema di Fermat

> [!important] Teorema (Fermat)
> Sia $f:(a,b)\to\mathbb R$ e $x_0\in(a,b)$ punto di estremo relativo. Se $f$ è **derivabile in $x_0$**, allora
> $$f'(x_0)=0 ,$$
> cioè $x_0$ è punto critico.

*Dim.* (caso max; il min è analogo) Sia $r>0$ t.c. $I_r(x_0)\subset(a,b)$ e $f(x)\le f(x_0)$ $\forall x\in I_r(x_0)$. Per $|h|<r$ è $x_0+h\in I_r(x_0)$, quindi $f(x_0+h)-f(x_0)\le0$ e:
- per $h>0$: $\dfrac{f(x_0+h)-f(x_0)}h\le0\ \Rightarrow\ f'_+(x_0)\le0$;
- per $h<0$: $\dfrac{f(x_0+h)-f(x_0)}h\ge0\ \Rightarrow\ f'_-(x_0)\ge0$

(permanenza del segno). Poiché $f$ è derivabile in $x_0$:
$$0\ge f'_+(x_0)=f'(x_0)=f'_-(x_0)\ge0\ \Rightarrow\ f'(x_0)=0.\qquad\blacksquare$$

Versione d'esame: [[5.5 Teorema di Fermat (★)]].

> [!warning] Oss. — le ipotesi sono essenziali
> 1. **Derivabilità in $x_0$:** $f(x)=|x|$ ha min relativo in $x_0=0$ (interno) ma $f$ non è derivabile lì, e $f'\ne0$ ovunque.
> 2. **$x_0$ interno:** su $[a,b]$, $x_0=a$ può essere min relativo con $f'_+(a)\ne0$.
> 3. **Il viceversa è falso:** $f(x)=x^3$ ha $f'(0)=0$ (punto critico) ma $0$ non è estremo relativo: è un **punto di flesso** (a tangente orizzontale).

## Collegamenti
- Teoria precedente: [[Derivate]]
- Teoria successiva: [[Teoremi di Rolle e Lagrange, monotonia]]
- Continuità e Weierstrass: [[Funzioni continue e punti di discontinuità]]
- Dimostrazioni: [[5.5 Teorema di Fermat (★)|5.5]]
- PDF: [[Lezione 17 (16 novembre) AM1 2026-27.pdf]]
