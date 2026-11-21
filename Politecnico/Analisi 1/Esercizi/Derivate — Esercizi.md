---
tags:
  - analisi1
  - derivate
  - esercizi
  - politecnico
---
# Derivate — Esercizi

Fonte: appunti a mano [[Drawing 2026-11-20 15.01.11.excalidraw|esercitazione del 20/11]].
Teoria: [[Punti di non derivabilità, massimi e minimi relativi]] · [[Teoremi di Rolle e Lagrange, monotonia]].

## 1. Numero di soluzioni al variare di un parametro

Stabilire al variare di $c\in\mathbb R$ il numero di soluzioni reali di
$$x^2=\log x+c .$$

Sia $f(x)=x^2-\log x-c$, $x>0$: le soluzioni sono gli zeri di $f$. $f$ è continua e derivabile su $(0,+\infty)$.
- $x\to0^+$: $f(x)\to+\infty$ (perché $-\log x\to+\infty$);
- $x\to+\infty$: $f(x)\to+\infty$ (gerarchia degli infiniti: $x^2\gg\log x$).

$$f'(x)=2x-\frac1x=\frac{2x^2-1}x .$$
Per $x>0$ il denominatore è positivo, quindi $f'<0$ per $0<x<\frac1{\sqrt2}$, $f'=0$ in $x=\frac1{\sqrt2}$, $f'>0$ per $x>\frac1{\sqrt2}$:
- $f$ strettamente decrescente in $\left(0,\frac1{\sqrt2}\right)$, strettamente crescente in $\left(\frac1{\sqrt2},+\infty\right)$;
- $x=\frac1{\sqrt2}$ è punto di **minimo assoluto**, con
$$f\!\left(\tfrac1{\sqrt2}\right)=\frac12-\log\frac1{\sqrt2}-c=\frac12(1+\log2)-c .$$

Quindi (valori intermedi su ciascun ramo monotono):
| condizione | soluzioni |
|---|---|
| $c<\frac12(1+\log2)$ (min $>0$) | nessuna |
| $c=\frac12(1+\log2)$ (min $=0$) | 1 |
| $c>\frac12(1+\log2)$ (min $<0$) | 2 distinte |

```desmos-graph
left=-0.2; right=2.5;
top=4; bottom=-1;
---
y=x^2-\ln(x)
y=\frac{1}{2}(1+\ln(2))
(0.7071,0.8466)|label:min
```
*(Intersezioni di $y=x^2-\log x$ con la retta orizzontale $y=c$.)*

## 2. Max e min assoluti (monotonia senza derivare)

Stabilire se $f(x)=\left(1+\sqrt{\dfrac x{2-x}}\right)e^{-\sqrt{1-x}}$ ammette max e min assoluti e calcolarli.

**Dominio:**
$$\begin{cases}\frac x{2-x}\ge0\\ x\ne2\\ 1-x\ge0\end{cases}\ \Rightarrow\ \begin{cases}x\in[0,2)\\ x\le1\end{cases}\ \Rightarrow\ [0,1].$$
$f$ è continua sul compatto $[0,1]$ ⇒ (Weierstrass) ha max e min assoluti.

**Metodo 1 (veloce):** $y=1+\sqrt{\frac x{2-x}}$ e $y=e^{-\sqrt{1-x}}$ sono entrambe **crescenti e positive** su $[0,1]$, quindi il prodotto è crescente:
$$\min f=f(0)=1\cdot e^{-1}=\frac1e,\qquad \max f=f(1)=(1+1)\cdot e^0=2 .$$

**Metodo 2:** calcolo di $f'$ e studio del segno (non svolto in aula).

## 3. Max e min assoluti di $x\log|x|$

Determinare max e min assoluti di
$$f(x)=\begin{cases}x\log|x| & x\in[-1,1]\setminus\{0\}\\ 0 & x=0\end{cases}$$

*(Solo il testo era negli appunti; svolgimento completato secondo il metodo del [[Teoremi di Rolle e Lagrange, monotonia|Teoremi di Rolle e Lagrange §1]].)*

- **Continuità in 0:** $x\log|x|\to0$ per $x\to0$ (gerarchia), quindi $f$ è continua su $[-1,1]$ ⇒ max e min esistono.
- **Candidati:**
  1. estremi: $f(\pm1)=0$;
  2. non derivabilità: in $0$, $f'(x)=\log|x|+1\to-\infty$, quindi $f$ non è derivabile (flesso a tangente verticale); $f(0)=0$;
  3. $f'(x)=\log|x|+1=0\iff|x|=\frac1e$: $f\!\left(\frac1e\right)=-\frac1e$, $f\!\left(-\frac1e\right)=\frac1e$.
- **Confronto:** $\max f=\frac1e$ in $x=-\frac1e$, $\min f=-\frac1e$ in $x=\frac1e$.

```desmos-graph
left=-1.2; right=1.2;
top=0.6; bottom=-0.6;
---
y=x\ln(\operatorname{abs}(x))
(-0.3679,0.3679)|label:max
(0.3679,-0.3679)|label:min
```

## 4. Disuguaglianza con Lagrange

Dimostrare che $\forall a,b\in\mathbb R$: $\ |\sin b-\sin a|\le|b-a|$.

- Se $a=b$ è ovvia.
- Se $a<b$ (il caso $a>b$ è simmetrico): $f(x)=\sin x$ è derivabile su $\mathbb R$ con $f'(x)=\cos x$, quindi si applica Lagrange su $[a,b]$: $\exists\xi\in(a,b)$ t.c.
$$\frac{\sin b-\sin a}{b-a}=\cos\xi\ \Rightarrow\ \frac{|\sin b-\sin a|}{|b-a|}=|\cos\xi|\le1 .$$
Quindi $|\sin b-\sin a|\le|b-a|$. $\blacksquare$

## 5. Identità con le derivate

Idea: se $f'=0$ su un **intervallo**, $f$ è costante lì ([[Teoremi di Rolle e Lagrange, monotonia#4. Applicazioni: funzioni a derivata nulla|teorema]]); la costante si trova valutando in un punto comodo.

**a)** $\arctan x+\arctan\dfrac1x=\begin{cases}\frac\pi2 & x>0\\ -\frac\pi2 & x<0\end{cases}$

Sia $f(x)=\arctan x+\arctan\frac1x$, $\mathrm{Dom}f=(-\infty,0)\cup(0,+\infty)$.
$$f'(x)=\frac1{1+x^2}+\frac1{1+\frac1{x^2}}\cdot\left(-\frac1{x^2}\right)=\frac1{1+x^2}-\frac{x^2}{x^2+1}\cdot\frac1{x^2}=0 .$$
Il dominio **non** è un intervallo: esistono due costanti $c_1,c_2$ con $f=c_1$ su $(0,+\infty)$ e $f=c_2$ su $(-\infty,0)$.
- $x=1$: $c_1=f(1)=2\arctan1=2\cdot\frac\pi4=\frac\pi2$;
- $f$ è dispari, quindi $c_2=f(-1)=-f(1)=-\frac\pi2$. $\blacksquare$

**b)** $\arccos x+\arcsin x=\dfrac\pi2\quad\forall x\in[-1,1]$

Sia $g(x)=\arccos x+\arcsin x$, $\mathrm{Dom}\,g=[-1,1]$ ($\arcsin:[-1,1]\to[-\frac\pi2,\frac\pi2]$, $\arccos:[-1,1]\to[0,\pi]$). $g$ è continua su $[-1,1]$ e derivabile su $(-1,1)$.

Ricordo (derivata dell'inversa): se $f$ è continua e invertibile, derivabile in $x_0$ con $f'(x_0)\ne0$, allora $(f^{-1})'(y_0)=\frac1{f'(x_0)}$ con $y_0=f(x_0)$. Applicato a $\cos:[0,\pi]\to[-1,1]$ e $\sin:[-\frac\pi2,\frac\pi2]\to[-1,1]$ dà ([[Derivate#8. Derivata della funzione inversa|Derivate §8]]):
$$D\arccos x=-\frac1{\sqrt{1-x^2}},\qquad D\arcsin x=\frac1{\sqrt{1-x^2}} .$$

*(Da qui completato: negli appunti lo svolgimento si interrompe.)*
Quindi $g'(x)=0$ su $(-1,1)$, che è un intervallo ⇒ $g$ è costante su $(-1,1)$, e per continuità anche su $[-1,1]$. Valutando in $0$:
$$g(0)=\arccos0+\arcsin0=\frac\pi2+0=\frac\pi2 .\qquad\blacksquare$$

## Collegamenti
- Teoria: [[Punti di non derivabilità, massimi e minimi relativi]] · [[Teoremi di Rolle e Lagrange, monotonia]] · [[Derivate]]
- Appunti a mano: [[Drawing 2026-11-20 15.01.11.excalidraw]]
