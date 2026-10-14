---
tags: [analisi-1, esame, non-svolti]
---
# Analisi 1 — Appello del 01-02-2022

## Domande a risposta multipla
1. [1] $z=3+\sqrt3\,i$. Allora $\arg(z^{22})=$ (a) $5\pi/3$; (b) $2\pi/3$; (c) $5\pi/6$; (d) $7\pi/6$; (e) nessuna.
2. [1] L'insieme dei punti $z\in\mathbb C$ tali che $|z-3|=|z-i|$ è (a) l'intersezione di due circonferenze; (b) un punto; (c) la retta $\{z\in\mathbb C:\mathrm{Re}\,z=\frac32\}$; (d) l'unione di due rette; (e) nessuna.
3. [1] $\displaystyle\lim_{n\to+\infty}\frac{\log\left(\frac1{n^7}\right)}{\log(1+n^5)}$: (a) $=-\infty$; (b) $=-12$; (c) $=-\frac75$; (d) $=0$; (e) non esiste.
4. [1] $f:I\to\mathbb R$ continua, $J=f(I)$. Possiamo affermare che: (a) se $f$ è strettamente monotona, è invertibile se e solo se $I$ è un intervallo; (b) se $I$ è un intervallo limitato, $f$ assume su $I$ massimo assoluto e minimo assoluto; (c) se $I$ è un intervallo, allora $J$ è un intervallo; (d) se $I=\mathbb R$, allora $J=\mathbb R$; (e) nessuna.
5. [1] $f,g:\mathbb R\to\mathbb R$, con $f$ derivabile una volta e $g$ derivabile due volte in tutto $\mathbb R$. Allora, presi $a<b$, $\int_a^bf(x)g''(x)\,dx=$ (a) $[f(x)g(x)]_a^b-\int_a^bf'(x)g(x)\,dx$; (b) $[f'(x)g'(x)]_a^b-\int_a^bf'(x)g'(x)\,dx$; (c) $[f(x)g'(x)]_a^b-\int_a^bf'(x)g'(x)\,dx$; (d) $[f'(x)g''(x)]_a^b-\int_a^bf'(x)g(x)\,dx$; (e) nessuna.
6. [1] $\displaystyle\int_{-2}^2\frac1{x^{5/3}}\,dx$: (a) non esiste; (b) $=\frac3{\sqrt[3]4}$; (c) $=0$; (d) $=-\frac3{\sqrt[3]4}$; (e) nessuna.
7. [2] $f(x)=e^{x^2}\cos x-1$ (attenzione: **non** ci sono parentesi). È vero che (a) $f(x)\sim x^2$ per $x\to0$; (b) $f(x)\sim\frac{x^2}2$; (c) $f(x)\sim-\frac{x^2}2$; (d) $f(x)=o(x^2)$; (e) nessuna.
8. [2] $F(x)=\displaystyle\int_0^x\frac{|\sin t|}{t^2+1}\,dt$. È vero che (a) $F$ ha infiniti punti di massimo o di minimo locale; (b) $F$ ha infiniti punti angolosi; (c) $F$ è strettamente crescente; (d) $\lim_{x\to+\infty}F(x)=+\infty$; (e) nessuna.
9. [2] Quale delle seguenti affermazioni garantisce la derivabilità di $f$ in $x=0$? (a) $f(0)=0$ e $f(x)=o(x)$ per $x\to0$; (b) $\lim_{x\to0}f(x)=0$; (c) $f$ continua in $x=0$; (d) $f(x)\sim1$ per $x\to0$; (e) $f$ ha un minimo in $x=0$.
10. [2] Nel punto $x=1$, la funzione $f(x)=\begin{cases}2a\log(x)&x>1\\ b\cos(\pi x)+x&x\le1\end{cases}$, con $a,b\in\mathbb R$, risulta (a) continua per qualunque scelta di $a$ e $b$, ma non necessariamente derivabile; (b) continua per infinite coppie $(a,b)$, ma derivabile solo per $(a,b)=(\frac12,1)$; (c) continua se e solo se $(a,b)=(0,1)$; (d) non derivabile qualunque sia la coppia $(a,b)$; (e) continua e derivabile per qualunque scelta di $a$ e $b$.

## Teoria
- **T1** [1] Data una successione di numeri reali $a_n$, definizione di $\lim_{n\to+\infty}a_n=-3$.
- **T2** [2] Enunciare una condizione sufficiente affinché una funzione $f:[a,b]\to\mathbb R$ sia Riemann integrabile. Tale condizione è anche necessaria? In caso affermativo darne dimostrazione, altrimenti fornire un controesempio.
- **T3** [3] Enunciare e dimostrare il teorema del valor medio di Lagrange (se si usa il teorema di Rolle è necessario darne dimostrazione).

## Esercizi
**E1 [5]** Sia $f(x)=x\,\dfrac{\log(|x|)+1}{\log(|x|)-3}$.
- Determinare il dominio, eventuali simmetrie e studiare la continuità di $f$. Determinare gli zeri e il segno di $f$.
- Calcolare i limiti di $f$ al bordo del dominio e determinare tutti gli eventuali asintoti.
- Studiare la derivabilità di $f$ e calcolare la derivata dove possibile.
- Studiare la monotonia di $f$, discutendo la presenza di estremi locali e globali.
- Tracciare un grafico qualitativo della funzione $f$ (non è richiesto lo studio della derivata seconda).

**E2 [4]** Calcolare $\displaystyle\int_1^3x\sqrt{1-(x-2)^2}\,dx.$

**E3 [3]** Studiare la convergenza semplice e assoluta della serie $\displaystyle\sum_{n=1}^\infty(-1)^n\frac{\arctan(n)}{n^\alpha}$, al variare del parametro $\alpha\in[1,+\infty)$.
