---
tags:
  - analisi1
  - derivate
  - calcolo-differenziale
  - politecnico
---
# Teoremi di Rolle e Lagrange, monotonia

Fonte: appunti a mano [[Drawing 2026-11-18 10.28.05.excalidraw|lezione del 18/11]].
Prosegue da [[Punti di non derivabilità, massimi e minimi relativi]].

## 1. Ricerca di max e min assoluti su $[a,b]$

Sia $f:[a,b]\to\mathbb R$ continua. Per il [[Funzioni continue e punti di discontinuità|teorema di Weierstrass]] esistono $M=\max_{[a,b]}f$ e $m=\min_{[a,b]}f$, cioè $\exists x_m,x_M\in[a,b]$ t.c. $f(x_M)=M$, $f(x_m)=m$. Due possibilità:
1. $x_m,x_M\in\{a,b\}$ (estremi dell'intervallo);
2. $x_m,x_M\in(a,b)$ (interni):
   - $f$ non è derivabile in $x_m$ e/o $x_M$, oppure
   - $f$ è derivabile lì, e allora per [[Punti di non derivabilità, massimi e minimi relativi#4. Teorema di Fermat|Fermat]] $f'(x_m)=0$ e/o $f'(x_M)=0$.

> [!important] Metodo
> **Candidati:** (1) gli estremi $a,b$; (2) i punti di non derivabilità; (3) i punti interni con $f'(x)=0$.
> **Calcolo:** valuto $f$ nei candidati e confronto: il valore più grande è il max assoluto, il più piccolo il min assoluto.

**Esempio.** $f:[-3,3]\to\mathbb R$, $f(x)=e^{1-x^2}$. Continua su $[-3,3]$ ⇒ (Weierstrass) ammette max e min assoluti.
1. Estremi: $x_{1,2}=\pm3$.
2. Punti di non derivabilità: nessuno.
3. $f'(x)=-2x\,e^{1-x^2}=0\iff x_3=0$.

$f(\pm3)=e^{-8}$, $f(0)=e$. Quindi $\max_{[-3,3]}f=e$ (in $x=0$), $\min_{[-3,3]}f=e^{-8}$ (in $x=\pm3$).

## 2. Teorema di Rolle

> [!important] Teorema (Rolle)
> Sia $f:[a,b]\to\mathbb R$ continua in $[a,b]$, derivabile in $(a,b)$, con $f(a)=f(b)$. Allora
> $$\exists\,\xi\in(a,b)\ \text{t.c.}\ f'(\xi)=0 .$$

*Dim.* $f$ continua su $[a,b]$ ⇒ (Weierstrass) esistono $M=\max f$ in $x_M$ e $m=\min f$ in $x_m$.
- **Caso 1:** $x_m,x_M\in\{a,b\}$. Poiché $f(a)=f(b)$, $m=M$, quindi $f$ è costante su $[a,b]$ e $f'(x)=0$ $\forall x\in(a,b)$.
- **Caso 2:** almeno uno tra $x_m,x_M$ è interno. $f$ è derivabile nei punti interni ed è un punto di estremo, quindi per Fermat $f'(x_m)=0$ e/o $f'(x_M)=0$. $\blacksquare$

Versione d'esame: [[5.6 Teorema di Rolle (★)]].

> [!warning] Oss. — le ipotesi servono
> 1. **Dominio intervallo:** $A=[a,b]\cup[c,d]$ con $b<c$: si può avere $f(a)=f(d)$ e $f'(x)\ne0$ $\forall x\in A$ (es. una retta crescente su $[a,b]$ e un ramo decrescente su $[c,d]$).
> 2. **Derivabilità in tutto $(a,b)$:** $f(x)=|x|$ su $[-1,1]$: $f(-1)=f(1)=1$, continua, ma non derivabile in $0$, e $f'(x)=\pm1\ne0$ $\forall x\in(-1,1)\setminus\{0\}$. Rolle non si applica.

## 3. Teorema di Lagrange (valor medio)

> [!important] Teorema (Lagrange)
> Sia $f:[a,b]\to\mathbb R$ continua in $[a,b]$ e derivabile in $(a,b)$. Allora $\exists\,\xi\in(a,b)$ t.c.
> $$f(b)-f(a)=f'(\xi)(b-a).$$

**Significato geometrico:** la tangente a $G_f$ in $(\xi,f(\xi))$ è parallela alla secante per $(a,f(a))$ e $(b,f(b))$, di pendenza $m=\frac{f(b)-f(a)}{b-a}$.

```desmos-graph
left=-0.5; right=4;
top=10; bottom=-0.5;
---
y=x^2
y=3x
y=3(x-1.5)+2.25
(0,0)|label:a
(3,9)|label:b
(1.5,2.25)|label:ξ
```

*Dim.* Sia (funzione $f$ meno la secante)
$$g(x)=f(x)-\left[f(a)+\frac{f(b)-f(a)}{b-a}(x-a)\right],\qquad x\in[a,b].$$
- $g$ è continua in $[a,b]$ e derivabile in $(a,b)$;
- $g(a)=f(a)-f(a)=0$, $g(b)=f(b)-f(a)-\frac{f(b)-f(a)}{b-a}(b-a)=0$.

Per Rolle $\exists\xi\in(a,b)$ t.c. $g'(\xi)=0$. Poiché $g'(x)=f'(x)-\dfrac{f(b)-f(a)}{b-a}$:
$$f'(\xi)=\frac{f(b)-f(a)}{b-a}\iff f(b)-f(a)=f'(\xi)(b-a).\qquad\blacksquare$$

Versione d'esame: [[5.7 Teorema di Lagrange (★)]].

## 4. Applicazioni: funzioni a derivata nulla

> [!important] Teorema
> Sia $f:I\to\mathbb R$, $I$ **intervallo**, continua e derivabile in $I$. Se $f'(x)=0$ $\forall x\in I$, allora $f$ è costante in $I$.

*Dim.* Siano $x_1<x_2$ in $I$. $[x_1,x_2]\subseteq I$ (perché $I$ è un intervallo), $f$ è continua in $[x_1,x_2]$ e derivabile in $(x_1,x_2)$. Per Lagrange $\exists\xi\in(x_1,x_2)$:
$$f(x_2)-f(x_1)=\underbrace{f'(\xi)}_{=0}(x_2-x_1)=0\ \Rightarrow\ f(x_2)=f(x_1).$$
Per l'arbitrarietà di $x_1,x_2$, $f$ è costante. $\blacksquare$

> [!warning] Oss. — serve che $I$ sia un intervallo
> 1. $I=[0,1]\cup[2,3]$, $f=1$ su $[0,1]$, $f=2$ su $[2,3]$: $f'=0$ su $I$ ma $f(\frac12)=1\ne2=f(\frac52)$.
> 2. $f(x)=\arctan x+\arctan\frac1x$ su $I=\mathbb R\setminus\{0\}$: $f'(x)=0$ $\forall x\in I$, ma $f(1)=\frac\pi2$, $f(-1)=-\frac\pi2$. È costante **su ciascun intervallo** $(-\infty,0)$ e $(0,+\infty)$ (vedi [[Derivate — Esercizi#5. Identità con le derivate|esercizio 5a]]).

## 5. Test di monotonia

> [!important] Teorema (test di monotonia)
> Sia $f$ derivabile in un **intervallo** $I$. Allora
> $$f\ \text{crescente in }I\iff f'(x)\ge0\quad\forall x\in I,$$
> $$f\ \text{decrescente in }I\iff f'(x)\le0\quad\forall x\in I.$$

*Dim.* (crescente)
- ($\Rightarrow$) $f$ crescente: $x_1\le x_2\Rightarrow f(x_1)\le f(x_2)$, quindi numeratore e denominatore del rapporto incrementale hanno lo stesso segno:
$$\frac{f(x)-f(x_0)}{x-x_0}\ge0\quad\forall x,x_0\in I,\ x\ne x_0 .$$
Poiché $f$ è derivabile, per la permanenza del segno $f'(x_0)=\lim_{x\to x_0}\frac{f(x)-f(x_0)}{x-x_0}\ge0$.
- ($\Leftarrow$) Siano $x_1<x_2$ in $I$. $[x_1,x_2]\subseteq I$ e $f$ è derivabile in $(x_1,x_2)$, quindi per Lagrange $\exists\xi\in(x_1,x_2)$:
$$\frac{f(x_2)-f(x_1)}{x_2-x_1}=f'(\xi)\ge0\ \Rightarrow\ f(x_2)\ge f(x_1).$$
Per l'arbitrarietà di $x_1,x_2$, $f$ è crescente. $\blacksquare$

Versione d'esame: [[5.8 Test di monotonia e funzioni costanti (★)]].

> [!warning] Oss.
> 1. **Serve l'intervallo:** $f(x)=x$ su $(0,1)$, $f(x)=x-3$ su $(2,3)$: $f'=1>0$ ovunque, ma $f(\frac12)=\frac12>-\frac12=f(\frac52)$, quindi $f$ non è crescente sull'unione.
> 2. $f'(x)>0$ $\forall x\in I$ $\Rightarrow$ $f$ **strettamente** crescente in $I$. Il viceversa è **falso**: $f(x)=x^3$ è strettamente crescente ma $f'(0)=0$.

## 6. Classificazione dei punti critici

Sia $f:I\to\mathbb R$ derivabile, $x_0\in I$ con $f'(x_0)=0$. Studio il **segno di $f'$** intorno a $x_0$:

| segno di $f'$ (sx → dx) | monotonia | $x_0$ è |
|---|---|---|
| $-\ \to\ +$ | ↘ ↗ | **minimo relativo** |
| $+\ \to\ -$ | ↗ ↘ | **massimo relativo** |
| $+\ \to\ +$ oppure $-\ \to\ -$ | ↗ ↗ / ↘ ↘ | **flesso a tangente orizzontale** |

Versione d'esame: [[5.9 Natura dei punti stazionari (★★)]].

**Esercizio.** $f(x)=2x^3-6x$: trovare i punti critici e classificarli.
$$f'(x)=6x^2-6=6(x+1)(x-1)=0\iff x=\pm1 .$$
$f'>0$ per $x<-1$ e $x>1$, $f'<0$ per $-1<x<1$. Quindi:
- $x=-1$ punto di **massimo relativo**, $x=1$ punto di **minimo relativo**;
- $f$ crescente in $(-\infty,-1)$ e in $(1,+\infty)$, decrescente in $(-1,1)$.

```desmos-graph
left=-3; right=3;
top=6; bottom=-6;
---
y=2x^3-6x
(-1,4)|label:max rel
(1,-4)|label:min rel
```

## 7. Limite della derivata

> [!important] Teorema
> Sia $f:[a,b]\to\mathbb R$ continua in $[a,b]$ e derivabile in $(a,b)\setminus\{x_0\}$, $x_0\in(a,b)$. Se esiste finito
> $$\lim_{x\to x_0}f'(x)=L\in\mathbb R ,$$
> allora $f$ è derivabile in $x_0$ e $f'(x_0)=L$.

*Dim.*
- **Destra:** per $h>0$, $f$ è continua in $[x_0,x_0+h]$ e derivabile in $(x_0,x_0+h)$. Per Lagrange $\exists\xi_h\in(x_0,x_0+h)$:
$$f'(\xi_h)=\frac{f(x_0+h)-f(x_0)}h .$$
Per $h\to0^+$, $\xi_h\to x_0^+$, quindi $\displaystyle\lim_{h\to0^+}\frac{f(x_0+h)-f(x_0)}h=\lim_{\xi\to x_0^+}f'(\xi)=L$.
- **Sinistra:** per $h<0$, stesso argomento su $[x_0+h,x_0]$: $\exists\eta_h\in(x_0+h,x_0)$ t.c.
$$f'(\eta_h)=\frac{f(x_0)-f(x_0+h)}{x_0-(x_0+h)}=\frac{f(x_0+h)-f(x_0)}h ,$$
e per $h\to0^-$, $\eta_h\to x_0^-$, quindi il limite sinistro del rapporto incrementale vale $L$.

I limiti destro e sinistro del rapporto incrementale sono finiti e uguali, quindi $f$ è derivabile in $x_0$ con $f'(x_0)=L$. $\blacksquare$

Versione d'esame: [[5.10 Limite della derivata e derivabilità (★★)]].

> [!note] Oss.
> Lo stesso argomento dà, separatamente: se $\lim_{x\to x_0^+}f'(x)=L_1$ allora $f'_+(x_0)=L_1$; se $\lim_{x\to x_0^-}f'(x)=L_2$ allora $f'_-(x_0)=L_2$, con $L_1,L_2\in\mathbb R\cup\{\pm\infty\}$.
> Se $L_1$ e/o $L_2$ sono $\pm\infty$, oppure $L_1\ne L_2$, allora $f$ **non** è derivabile in $x_0$.
> Attenzione: se $\lim f'$ **non esiste** non si può concludere nulla (es. $x^2\sin\frac1x$, vedi [[Punti di non derivabilità, massimi e minimi relativi#2. Funzione derivata|§2 della lezione precedente]]).

**Esercizio.** Determinare $\alpha,\beta\in\mathbb R$ t.c. $\exists f'(0)$, dove
$$f(x)=\begin{cases}\alpha x^2+\beta x & x\ge0\\ x^3+x & x<0\end{cases}$$
1. **Continuità in 0:** $\lim_{x\to0^+}(\alpha x^2+\beta x)=0$ e $\lim_{x\to0^-}(x^3+x)=0=f(0)$ $\forall\alpha,\beta$: $f$ è sempre continua in $0$.
2. **Derivabilità:** $f'(x)=2\alpha x+\beta$ per $x>0$, $f'(x)=3x^2+1$ per $x<0$:
$$\lim_{x\to0^+}f'(x)=\beta,\qquad\lim_{x\to0^-}f'(x)=1 .$$
Per il teorema, $f$ è derivabile in $0$ $\iff\beta=1$, $\forall\alpha\in\mathbb R$.

Verifica col rapporto incrementale: $\lim_{h\to0^+}\frac{\alpha h^2+\beta h}h=\beta$, $\lim_{h\to0^-}\frac{h^3+h}h=1$. Stesso risultato: $\exists f'(0)\iff\beta=1$.

## Collegamenti
- Teoria precedente: [[Punti di non derivabilità, massimi e minimi relativi]] · [[Derivate]]
- Esercizi: [[Derivate — Esercizi]]
- Dimostrazioni: [[5.6 Teorema di Rolle (★)|5.6]] · [[5.7 Teorema di Lagrange (★)|5.7]] · [[5.8 Test di monotonia e funzioni costanti (★)|5.8]] · [[5.9 Natura dei punti stazionari (★★)|5.9]] · [[5.10 Limite della derivata e derivabilità (★★)|5.10]]
- Appunti a mano: [[Drawing 2026-11-18 10.28.05.excalidraw]]
