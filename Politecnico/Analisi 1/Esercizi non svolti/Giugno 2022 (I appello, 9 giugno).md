---
tags: [analisi-1, esame, non-svolti]
---
# Analisi 1 — Appello del 09-06-2022 (prof. D. D. Monticelli)

## Domande a risposta multipla
1. [2] $a_n,b_n$ tali che $a_n\sim b_n$ per $n\to+\infty$. Quale fra le seguenti affermazioni **NON è** necessariamente vera? a) $a_n-b_n\to0$; b) $b_n^4\sim a_n^4$; c) $7a_n\sim7b_n$; d) $\frac{a_n}{b_n}\to1$; e) $a_n=b_n+o(b_n)$.
2. [2] $F(x)=\displaystyle\int_0^x\sqrt[3]{e^{2t}-1}\,dt$: a) non è derivabile in $x=0$; b) ha un flesso in $x=0$; c) ha un minimo locale in $x=0$; d) ha un massimo locale in $x=0$; e) nessuna.
3. [2] Quale tra le funzioni seguenti ha un grafico compatibile con il grafico in figura vicino a (cioè in un intorno di) $x=0$? *(Figura: parabola con minimo nell'origine.)* a) $x\sin x^{\frac23}$; b) $x\log(x+1)$; c) $x^{-\frac12}\arctan x$; d) $(e^x-1)^{\frac13}x^{\frac23}$; e) nessuna.
4. [2] $\alpha\in\mathbb R$ e $\lambda=\displaystyle\lim_{x\to0}\frac{2\cos x+e^{x^2}-3}{x^\alpha}$. Allora $\lambda$ esiste finito ed è diverso da 0 se e solo se a) $\alpha=1$; b) $\alpha=2$; c) $\alpha=3$; d) $\alpha=4$; e) nessuna.
5. [1] Quale di queste successioni tende a $e$ per $n\to\infty$? a) $e^{\frac{\log n}n}$; b) $e^{n\log\left(1+\frac1n\right)}$; c) $e^{\sqrt n}$; d) $\left(1+\frac1{n^2}\right)^n$; e) nessuna.
6. [1] L'equazione $|z|=\bar z$ descrive nel piano complesso a) una circonferenza; b) una retta; c) una semiretta; d) una parabola; e) nessuna.
7. [1] $f$ strettamente monotona su un intervallo $I$. È vero che (a) se $I=\mathbb R$, $f$ è sempre illimitata; (b) se $I=[a,b)$, $f(a)=\min f$ oppure $f(a)=\max f$; (c) $f$ deve essere continua su $I$; (d) se $I=[a,b)$, deve essere $f(a)=\min f$; (e) nessuna.
8. [1] $A=\left\{\frac1e\right\}\cup\left\{\frac1n:n\in\mathbb N,n\ge1\right\}$. Allora a) $\inf A$ non esiste in $\mathbb R^*=\mathbb R\cup\{\pm\infty\}$; b) $\inf A=\min A$; c) $\inf A=0$; d) $\inf A=\frac1e$; e) $\inf A=-\infty$.
9. [1] $(-1+i)^{18}$ è uguale a a) $-2^9i$; b) $2^9$; c) $-2^9$; d) $2^8\sqrt2-2^8\sqrt2i$; e) $-2^8\sqrt2+2^8\sqrt2i$.
10. [1] $\displaystyle\sum_{n=1}^\infty\frac{\arctan n}{n^\alpha\sin\frac1n}$ converge se e solo se a) $\alpha>-1$; b) $\alpha>0$; c) $\alpha>1$; d) $\alpha>2$; e) nessuna.

## Teoria
- **T1** (1) Data $f:(a,b)\to\mathbb R$ e $x_0\in(a,b)$, definizione di $\lim_{x\to x_0^-}f(x)=-\infty$.
- **T2** (2) Enunciare il criterio di convergenza assoluta per serie. Tale condizione è anche necessaria? In caso di risposta affermativa darne dimostrazione, altrimenti fornire un controesempio.
- **T3** (3) Enunciare e dimostrare il Teorema del Test di Monotonia (solo nel caso di funzioni monotone crescenti).

## Esercizi
**E1 [5]** Sia $f(x)=|x|\sqrt[3]{\dfrac x{x-2}}$.
- Determinare il dominio e studiare la continuità di $f$. Determinare gli zeri e il segno di $f$.
- Calcolare i limiti di $f$ al bordo del dominio e determinare gli eventuali asintoti orizzontali e verticali (non si richiede di determinare eventuali asintoti obliqui).
- Studiare la derivabilità di $f$ e calcolare la derivata dove possibile.
- Studiare la monotonia di $f$, discutendo la presenza di estremi locali e globali.
- Tracciare un grafico qualitativo della funzione $f$ (non è richiesto lo studio della derivata seconda).

**E2 [4]** Calcolare $\displaystyle\int_{e^2}^{e^3}\frac{dx}{x(1-\log x)(\log x)^2}.$

**E3 [3]** Stabilire se il seguente integrale generalizzato esista finito: $\displaystyle\int_1^\infty\frac{(\log x)^{\frac12}}{e^x-e}\,dx.$
