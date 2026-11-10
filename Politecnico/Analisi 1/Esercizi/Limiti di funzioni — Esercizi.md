---
tags:
  - analisi1
  - limiti-funzioni
  - asintotici
  - continuità
  - esercizi
---
# Limiti di funzioni — Esercizi

Svolti a mano il 6/11 ([[Drawing 2026-11-06 15.02.34.excalidraw|appunti Excalidraw]]), ricopiati e corretti.
Teoria: [[Limiti di funzioni]] · [[Funzioni continue e punti di discontinuità]] · [[Confronti e stime asintotiche]].

## Strumenti

Per $\varepsilon(x)\to0$ (limiti notevoli in forma di equivalenza):

| | |
|---|---|
| $\sin\varepsilon\sim\varepsilon$ | $\tan\varepsilon\sim\varepsilon$ |
| $1-\cos\varepsilon\sim\frac{\varepsilon^2}2$ | $\log(1+\varepsilon)\sim\varepsilon$ |
| $e^\varepsilon-1\sim\varepsilon$ | $(1+\varepsilon)^\alpha-1\sim\alpha\varepsilon$ |

$\sim$ si usa liberamente in **prodotti e quozienti**; nelle **somme** si passa per gli o piccoli ($x+o(x)\sim x$).

---

## Esercizio 1 — $\frac00$

$$\lim_{x\to0}\frac{\log(\cos 3x)}{\sin(x-\pi)\,(e^x-1)}$$

**Numeratore.** $\log(\cos3x)=\log\big(1+(\cos3x-1)\big)$ con $\cos3x-1\to0$:
$$\log(\cos3x)\sim\cos3x-1=-\big[1-\cos3x\big]\sim-\frac12(3x)^2=-\frac92x^2 .$$

**Denominatore.** $\sin(x-\pi)=\sin x\cos\pi-\cos x\sin\pi=-\sin x\sim-x$, e $e^x-1\sim x$:
$$\sin(x-\pi)(e^x-1)\sim-x^2 .$$

$$\lim_{x\to0}\frac{-\frac92x^2}{-x^2}=\boxed{\frac92}$$

## Esercizio 2 — $1^\infty$

$$\lim_{x\to+\infty}\Big(\frac{x^2}{x^2+1}\Big)^{x(x-1)}$$

$$\Big(\frac{x^2+1-1}{x^2+1}\Big)^{x^2-x}=\Big(1+\frac{-1}{x^2+1}\Big)^{x^2-x}=\bigg[\Big(1+\frac{-1}{x^2+1}\Big)^{x^2+1}\bigg]^{\frac{x^2-x}{x^2+1}}$$

La parentesi quadra $\to e^{-1}$ (limite notevole $(1+\frac cy)^y\to e^c$ con $y=x^2+1$), l'esponente $\frac{x^2-x}{x^2+1}\to1$:
$$\lim=\big(e^{-1}\big)^1=\boxed{\frac1e}$$

## Esercizio 3 — $\frac00$ con traslazione

$$\lim_{x\to\frac12}\frac{\cos(\pi x)}{x-2x^2}$$

Porto l'argomento vicino a $0$: $\pi x=\pi\big(x-\frac12\big)+\frac\pi2$.
$$\cos(\pi x)=\cos\Big(\pi\big(x-\tfrac12\big)\Big)\cos\tfrac\pi2-\sin\Big(\pi\big(x-\tfrac12\big)\Big)\sin\tfrac\pi2=-\sin\Big(\pi\big(x-\tfrac12\big)\Big)\underset{x\to\frac12}{\sim}\pi\Big(\tfrac12-x\Big).$$
Denominatore: $x-2x^2=2x\big(\frac12-x\big)$.
$$\lim_{x\to\frac12}\frac{\pi(\frac12-x)}{2x(\frac12-x)}=\lim_{x\to\frac12}\frac\pi{2x}=\boxed{\pi}$$

## Esercizio 4 — $1^\infty$ con esponenziale

$$\lim_{x\to+\infty}\Big[1+\sin\frac2{x^2}\Big]^{x^3\log\left(1+\frac1{2x}\right)}$$

Riscrivo $f^g=e^{g\log f}$:
$$=\exp\Big(x^3\cdot\underbrace{\log\big(1+\tfrac1{2x}\big)}_{\sim\frac1{2x}}\cdot\underbrace{\log\big(1+\sin\tfrac2{x^2}\big)}_{\sim\sin\frac2{x^2}\sim\frac2{x^2}}\Big)$$
Esponente $\sim x^3\cdot\frac1{2x}\cdot\frac2{x^2}=1$. Quindi
$$\lim=\boxed{e}$$

> [!note] Correzione
> Negli appunti compariva $\sin\frac2x$: l'argomento corretto è $\frac2{x^2}$ (il risultato non cambia).

## Esercizio 5 — limite sinistro

$$\lim_{x\to0^-}\frac{\tan(2x)+4x^5+2^x}{\sin x+x^2}$$

- Numeratore: $\tan0+0+2^0=1$, non è infinitesimo.
- Denominatore: $\sin x+x^2=x+o(x)+x^2=x+o(x)\sim x$ (perché $x^2=o(x)$: $\frac{x^2}x=x\to0$).

$$\lim_{x\to0^-}\frac1x=\frac1{0^-}=\boxed{-\infty}$$

## Esercizio 6 — valore assoluto, limiti destro e sinistro

$$\lim_{x\to2}\frac{\tan(x-2)}{\lvert x^2-4\rvert}\qquad\Big[\tfrac00\Big]$$

$\tan(x-2)\sim x-2$. In un intorno di $2$ si ha $x+2>0$, quindi
$$\lvert x^2-4\rvert=\lvert(x+2)(x-2)\rvert=(x+2)\lvert x-2\rvert=\begin{cases}(x+2)(x-2)&x\to2^+\\(x+2)(2-x)&x\to2^-\end{cases}$$

$$\lim_{x\to2^+}\frac{x-2}{(x+2)(x-2)}=\frac14,\qquad\lim_{x\to2^-}\frac{x-2}{(x+2)(2-x)}=-\frac14 .$$

Limiti destro e sinistro diversi: $\boxed{\nexists\lim_{x\to2}f(x)}$.

## Esercizio 7 — radici e o piccoli

$$\lim_{x\to0}\frac{\sqrt[3]{\sqrt{\lvert x\rvert}+1}-\cos^2x}{\sqrt{\lvert x\rvert}+\log(\cos^2x)}$$

**Numeratore.** Aggiungo e tolgo $1$:
$$\big(1+\lvert x\rvert^{1/2}\big)^{1/3}-1\ +\ \big(1-\cos^2x\big).$$
- $(1+\lvert x\rvert^{1/2})^{1/3}-1\sim\frac13\lvert x\rvert^{1/2}$;
- $1-\cos^2x=(1+\cos x)(1-\cos x)\sim2\cdot\frac{x^2}2=x^2$, e $x^2=o(\lvert x\rvert^{1/2})$.

Quindi numeratore $=\frac13\sqrt{\lvert x\rvert}+o(\lvert x\rvert^{1/2})\sim\frac13\sqrt{\lvert x\rvert}$.

**Denominatore.** $\log(\cos^2x)=\log\big(1+(\cos^2x-1)\big)\sim\cos^2x-1\sim-x^2$:
$$\lvert x\rvert^{1/2}-x^2+o(x^2)=\lvert x\rvert^{1/2}+o(\lvert x\rvert^{1/2})\sim\sqrt{\lvert x\rvert}.$$

$$\lim_{x\to0}\frac{\frac13\sqrt{\lvert x\rvert}}{\sqrt{\lvert x\rvert}}=\boxed{\frac13}$$

## Esercizio 8 — $0\cdot\infty$ con sostituzione

$$\lim_{x\to1^+}\log x\cdot\log(\log x)$$

Pongo $t=\log x$: per $x\to1^+$, $t\to0^+$. Il limite diventa $\lim_{t\to0^+}t\log t$.

Pongo $t=e^u$ ($u=\log t\to-\infty$): $\lim_{u\to-\infty}e^u\cdot u$.

Stima: $e^{y/2}\gg y$ per $y\to+\infty$, quindi $y\le e^{y/2}$ definitivamente; con $y=-u$: per $u<0$, $\lvert u\rvert=-u\le e^{-u/2}$. Allora
$$0\le\lvert e^u u\rvert=e^u\lvert u\rvert\le e^u e^{-u/2}=e^{u/2}\xrightarrow{u\to-\infty}0 .$$
Per i due carabinieri: $\boxed{0}$. (È il caso $\alpha=1$ di $\lim_{x\to0^+}x^\alpha\log x=0$, vedi teoria.)

---

## Da svolgere (consegne dagli appunti)

### Esercizio 9 — Asintoti

$$f(x)=\begin{cases}e^{x\sin\frac1x}-\arctan x&x>0\\1&x=0\\\dfrac{x^3-2x^2+1}{2x^2}&x<0\end{cases}$$
Trovare gli asintoti di $f$.

> [!check]- Soluzione
> - $x\to+\infty$: $x\sin\frac1x=\frac{\sin(1/x)}{1/x}\to1$, quindi $f\to e-\frac\pi2$: **asintoto orizzontale** $y=e-\frac\pi2$.
> - $x\to-\infty$: $f(x)=\frac x2-1+\frac1{2x^2}$. $m=\lim\frac{f(x)}x=\frac12$, $q=\lim\big(f(x)-\frac x2\big)=-1$: **asintoto obliquo** $y=\frac x2-1$.
> - $x\to0^-$: numeratore $\to1$, denominatore $2x^2\to0^+$: $f\to+\infty$, **asintoto verticale sinistro** $x=0$.
> - $x\to0^+$: $x\sin\frac1x\to0$ (infinitesimo × limitata), $f\to e^0-0=1=f(0)$: continua da destra, nessun asintoto.

### Esercizio 10 — Continuità con parametri

Trovare $\alpha,\beta\in\mathbb R$ tali che sia continua in $(-\infty,2\pi)$
$$f(x)=\begin{cases}\alpha\,\dfrac{\sqrt{1+4\lvert x\rvert}-1}{\lvert x\rvert}&x<0\\\beta&x=0\\\dfrac{e^{\sin^2x}-1}{\log(2-\cos x)}&0<x<2\pi\end{cases}$$

> [!check]- Soluzione
> Fuori da $0$ è composizione di funzioni continue ($\log(2-\cos x)\neq0$ perché $\cos x\neq1$ in $(0,2\pi)$). In $0$:
> - $x\to0^-$: $\sqrt{1+4\lvert x\rvert}-1\sim\frac12\cdot4\lvert x\rvert=2\lvert x\rvert$, limite $2\alpha$.
> - $x\to0^+$: $e^{\sin^2x}-1\sim\sin^2x\sim x^2$; $\log(2-\cos x)=\log(1+(1-\cos x))\sim1-\cos x\sim\frac{x^2}2$. Limite $2$.
>
> Serve $2\alpha=\beta=2$: $\boxed{\alpha=1,\ \beta=2}$.

### Esercizio 11 — Continuità al variare di $\alpha$

$$f(x)=\begin{cases}\dfrac{e^{-x^2/3}-\cos x}{\lvert x\rvert^\alpha}&x\neq0\\0&x=0\end{cases}$$
Per quali $\alpha\in\mathbb R$ $f$ è continua in $0$? *(consegna dedotta: negli appunti c'è solo la funzione)*

> [!check]- Soluzione
> $e^{-x^2/3}-\cos x=\big(e^{-x^2/3}-1\big)+\big(1-\cos x\big)=-\frac{x^2}3+o(x^2)+\frac{x^2}2+o(x^2)=\frac{x^2}6+o(x^2)$.
> Quindi $f(x)\sim\frac16\lvert x\rvert^{2-\alpha}$:
> - $\alpha<2$: $f\to0=f(0)$, **continua**;
> - $\alpha=2$: $f\to\frac16\neq0$, discontinuità **eliminabile**;
> - $\alpha>2$: $f\to+\infty$, discontinuità di **2ª specie**.
