---
tags: [analisi-1, esame, non-svolti]
---
# Analisi 1 — Esame del 13-01-2022

> Nel PDF alcuni quesiti erano cerchiati in rosso per la sola seconda prova in itinere (domande 4, 5, 6, 8, 9 della parte multipla; teoria 1 e 4; esercizi 1 e 2...). Qui sono riportati tutti.

## Domande a risposta multipla
1. [1] L'equazione $|z^5|-3^5=0$ ha in $\mathbb C$ (a) solo le soluzioni $z=\pm3$ e $z=\pm3i$; (b) esattamente 5 soluzioni distinte; (c) infinite soluzioni; (d) solo le soluzioni $z=\pm3$; (e) nessuna.
2. [1] $z\in\mathbb C$. A meno di multipli di $2\pi$, $\arg\frac1z=$ (a) $\frac1{\arg\bar z}$; (b) $\arg\bar z$; (c) $\frac1{\arg z}$; (d) $\arg z$; (e) nessuna.
3. [1] $\displaystyle\lim_{x\to+\infty}\frac{\log(1+x)-\sin x}{\sqrt[3]x+x^2}$: (a) $=-\infty$; (b) $=+\infty$; (c) $=-\frac12$; (d) $=0$; (e) non esiste.
4. [1] $f$ convessa su $\mathbb R$. Allora (a) se esiste, $f'$ è crescente; (b) $\lim_{x\to+\infty}f(x)=+\infty$; (c) esiste $\min_{\mathbb R}f$; (d) se esiste, $f''(x)>0$ $\forall x\in\mathbb R$; (e) nessuna.
5. [1] $I=\int_0^1f(x)\,dx$. Allora $\int_0^{1/3}f(3x)\,dx$ (a) $=3I$; (b) $=\frac19I$; (c) $=I$; (d) $=9I$; (e) nessuna.
6. [1] $f(x)=(x-\sinh x)^7$ su $\mathbb R$. È vero che, per $K$ opportuno, (a) $f(x)\sim Kx^{21}$ per $x\to0$; (b) $f(x)\sim Kx^7$ per $x\to0$; (c) $f(x)\sim Kx^{10}$ per $x\to0$; (d) $f(x)\sim Kx^7$ per $x\to+\infty$; (e) nessuna.
7. [2] L'insieme delle soluzioni della disequazione $3+x>\sqrt{x^2-1}$ è (a) $(-\infty,-1]\cup[1,+\infty)$; (b) $(-\frac53,-1)\cup(1,+\infty)$; (c) $[-\frac53,-1]\cup[1,+\infty)$; (d) $(-\frac53,+\infty)$; (e) $(-\frac53,-1]\cup[1,+\infty)$.
8. [2] $f\in C^0(\mathbb R)$. Se $\int_0^2f(x)\,dx=2$, si può dedurre che (a) $f(x)\ge0$ su $[0,2]$; (b) $\int_0^2(f(x))^2dx=4$; (c) $\int_{-2}^0f(-x)\,dx=-2$; (d) l'equazione $f(x)=1$ ha almeno una soluzione in $[0,2]$; (e) nessuna.
9. [2] L'integrale $\displaystyle\int_0^2\frac{2x+3}{(x^2+x)^\alpha}\,dx$ esiste finito (a) $\forall\alpha\in\mathbb R$; (b) $\iff\alpha<1$; (c) $\iff\alpha>\frac12$; (d) $\iff\alpha<\frac12$; (e) $\iff\alpha<2$.
10. [2] Data la serie $\sum_{n=1}^{+\infty}(-1)^n\frac{\log(1+n)}{n^2+1}$ e posto $a_n=\frac{\log(1+n)}{n^2+1}$, è vero che (a) la serie converge semplicemente ma non assolutamente; (b) la serie è irregolare; (c) $a_n\sim\frac1n$ per $n\to+\infty$; (d) la serie converge assolutamente; (e) nessuna.

## Teoria
1. [1] Dare la definizione di primitiva di una funzione $f:I\to\mathbb R$, con $I\subset\mathbb R$ intervallo.
2. [2] Enunciare una condizione necessaria affinché la serie di numeri reali $\sum_{n=1}^\infty a_n$ converga (non è richiesta la dimostrazione). Tale condizione è anche sufficiente? In caso affermativo dimostrarlo, in caso negativo fornire un controesempio.
3. [1] Data una successione di numeri reali $a_n$, dare la definizione di $\lim_{n\to+\infty}a_n=5$.
4. [2] Enunciare e dimostrare il teorema di Fermat.

## Esercizi
**Es. 1 [4]** Data $f(x)=1+(\log(1+x))^2-e^{x^2}$, determinare $K,n$ tali che $f(x)\sim Kx^n$ per $x\to0$. *(Solo per appello completo:)* discutere al variare di $\alpha\in\mathbb R$ la convergenza/divergenza della serie
$$\sum_{n=1}^\infty\frac{1+\left(\log\left(1+\frac{\sqrt2}n\right)\right)^2-e^{\frac2{n^2}}}{n^\alpha\sin\left(\frac1{\sqrt n}\right)}.$$

**Es. 2 [4]** Calcolare $\displaystyle\int_{1/2}^1\frac1{x^2}\arctan\left(\frac1x\right)dx.$

**Es. 3 [4]** Sia $f(x)=(x^3-|x|)^{\frac13}$.
- Determinare il dominio di $f$ e studiarne la continuità. Calcolare i limiti di $f$ al bordo del dominio. Trovare eventuali asintoti. Determinare gli zeri di $f$ e il segno di $f$.
- Studiare la derivabilità di $f$, calcolare la derivata dove possibile, e classificare i punti di non derivabilità.
- Studiare la monotonia di $f$, discutendo la presenza di estremi locali e globali.
- Tracciare un grafico qualitativo della funzione $f$ (non è richiesto lo studio della derivata seconda).
