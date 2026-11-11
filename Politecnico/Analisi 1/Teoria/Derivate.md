---
tags:
  - analisi1
  - derivate
  - calcolo-differenziale
  - politecnico
---
# Derivate

Fonte: appunti a mano [[Drawing 2026-11-11 10.12.34.excalidraw|lezione dell'11/11]].
Prosegue da [[Funzioni continue e punti di discontinuità]].

## 1. Definizione di derivata

**Def.** Sia $f:(a,b)\to\mathbb R$ e $x_0\in(a,b)$. $f$ è **derivabile in $x_0$** se esiste **finito** il limite del **rapporto incrementale**
$$f'(x_0):=\lim_{h\to0}\frac{f(x_0+h)-f(x_0)}{h}.$$

Notazioni equivalenti: $f'(x_0)=Df(x_0)=\dfrac{df}{dx}(x_0)$ (notazione di Leibniz).

**Scrittura equivalente.** Ponendo $x=x_0+h$ (cioè $h=x-x_0$, e $h\to0\iff x\to x_0$):
$$f'(x_0)=\lim_{x\to x_0}\frac{f(x)-f(x_0)}{x-x_0}.$$

$f$ è **derivabile in $I$** se è derivabile in ogni punto di $I$; in tal caso $x\mapsto f'(x)$ è la **funzione derivata**.

## 2. Significato geometrico

Una retta (non verticale) ha equazione $y=mx+q$, con $m$ = **coefficiente angolare**. La retta per $(x_0,y_0)$ e $(x_1,y_1)$ ha
$$m=\frac{y_1-y_0}{x_1-x_0}.$$

Con $y_0=f(x_0)$, $y_1=f(x_1)$, la **retta secante** al grafico per i due punti è
$$y=\frac{f(x_1)-f(x_0)}{x_1-x_0}\,(x-x_0)+f(x_0),$$
e il suo coefficiente angolare è proprio il rapporto incrementale. Facendo $x_1\to x_0$ la secante tende alla **retta tangente**:

> [!important] $f'(x_0)$ è il coefficiente angolare della retta tangente al grafico $G_f$ nel punto $(x_0,f(x_0))$:
> $$y=f(x_0)+f'(x_0)(x-x_0).$$

Esempio: $f(x)=x^2$, $x_0=1$, $x_1=2$. Secante $y=3(x-1)+1$, tangente $y=2(x-1)+1$.

```desmos-graph
left=-1; right=3;
top=5; bottom=-1;
---
y=x^2
y=3(x-1)+1
y=2(x-1)+1
(1,1)|label:x_0
(2,4)|label:x_1
```

## 3. Differenziabilità

**Def.** Sia $f:(a,b)\to\mathbb R$, $x_0\in(a,b)$. $f$ è **differenziabile in $x_0$** se $\exists\lambda\in\mathbb R$ t.c.
$$f(x)=f(x_0)+\lambda(x-x_0)+o(x-x_0)\qquad(x\to x_0).$$
($o$ piccolo per funzioni: [[Limiti di funzioni#7. Infinitesimi e infiniti|Limiti di funzioni §7]].)

Cioè: vicino a $x_0$, $f$ si approssima con una funzione affine (la tangente) a meno di un errore infinitesimo di ordine superiore a $x-x_0$.

> [!important] Teorema
> Sia $f:I\to\mathbb R$, $I$ intervallo, $x_0$ interno a $I$. Allora
> $$f\ \text{differenziabile in }x_0\iff f\ \text{derivabile in }x_0,$$
> e in tal caso $\lambda=f'(x_0)$.

*Dim.* Con $h=x-x_0$ la definizione diventa $f(x_0+h)-f(x_0)=\lambda h+o(h)$ per $h\to0$.
- ($\Rightarrow$) Dividendo per $h\ne0$: $\dfrac{f(x_0+h)-f(x_0)}h=\lambda+\dfrac{o(h)}h\to\lambda$. Quindi $f$ è derivabile e $f'(x_0)=\lambda$.
- ($\Leftarrow$) Se $f'(x_0)=\lambda$, la funzione $\omega(h)=\dfrac{f(x_0+h)-f(x_0)}h-\lambda\to0$; allora $f(x_0+h)-f(x_0)-\lambda h=h\,\omega(h)=o(h)$. $\blacksquare$

Versione d'esame: [[5.3 Differenziabilità ⟺ derivabilità (★)]].

## 4. Derivabile ⇒ continua

> [!important] Teorema
> Sia $f:I\to\mathbb R$, $x_0$ interno a $I$. Se $f$ è derivabile in $x_0$, allora $f$ è continua in $x_0$.

*Dim.* Per $x\ne x_0$:
$$f(x)-f(x_0)=\frac{f(x)-f(x_0)}{x-x_0}\,(x-x_0)\xrightarrow{x\to x_0}f'(x_0)\cdot0=0$$
per l'algebra dei limiti. Dunque $\lim_{x\to x_0}f(x)=f(x_0)$. $\blacksquare$

Versione d'esame: [[5.1 Derivabile ⟹ continua (★)]].

> [!warning] Il viceversa è falso
> $f(x)=|x|$ è continua in $0$ ma non derivabile: il rapporto incrementale $\frac{|h|}h$ vale $1$ per $h>0$ e $-1$ per $h<0$, quindi non ha limite (punto angoloso).

## 5. Derivate delle funzioni elementari

Calcolate dalla definizione ($h\to0$), usando i [[Limiti di funzioni#6. Limiti notevoli|limiti notevoli]] $\frac{\sin h}h\to1$, $\frac{1-\cos h}{h^2}\to\frac12$, $\frac{e^h-1}h\to1$, $\frac{\log(1+t)}t\to1$:

- **Costante** $c\in\mathbb R$: $\dfrac{c-c}h=0\to0$, quindi $Dc=0$.
- **Identità**: $\dfrac{(x+h)-x}h=1\to1$, quindi $Dx=1$.
- **Potenza** $x^n$, $n\in\mathbb N$: $(x+h)^n=x^n+nx^{n-1}h+\sum_{k\ge2}\binom nk x^{n-k}h^k$, quindi
$$\frac{(x+h)^n-x^n}h=nx^{n-1}+O(h)\to nx^{n-1}.$$
Ad esempio $D x^2=2x$: $\dfrac{(x+h)^2-x^2}h=\dfrac{2xh+h^2}h=2x+h\to2x$.
- **Seno**: con la formula di addizione $\sin(x+h)=\sin x\cos h+\cos x\sin h$,
$$\frac{\sin(x+h)-\sin x}h=\sin x\,\underbrace{\frac{\cos h-1}h}_{\to0}+\cos x\,\underbrace{\frac{\sin h}h}_{\to1}\to\cos x ,$$
dove $\frac{\cos h-1}h=-h\cdot\frac{1-\cos h}{h^2}\to-0\cdot\frac12=0$.
- **Coseno**: analogamente con $\cos(x+h)=\cos x\cos h-\sin x\sin h$, $D\cos x=-\sin x$.
- **Esponenziale**: $\dfrac{e^{x+h}-e^x}h=e^x\,\dfrac{e^h-1}h\to e^x$.
- **Logaritmo** $\log_a x$ ($x>0$):
$$\frac{\log_a(x+h)-\log_a x}h=\frac{\log_a\!\big(1+\frac hx\big)}{\frac hx}\cdot\frac1x\to\frac{\log_a e}{x}=\frac1{x\ln a},$$
perché, con $t=\frac hx\to0$ e il cambio di base $\log_a(1+t)=\frac{\ln(1+t)}{\ln a}$: $\frac{\log_a(1+t)}t=\frac1{\ln a}\cdot\frac{\ln(1+t)}t\to\frac1{\ln a}=\log_a e$.
In particolare $D\ln x=\dfrac1x$.

Versione d'esame (sin, $x^n$, $e^x$): [[5.2 Derivate di alcune funzioni elementari (★★)]].

## 6. Regole di derivazione

> [!important] Teorema (algebra delle derivate)
> Siano $f,g$ derivabili in $x$. Allora:
> 1. $f\pm g$ è derivabile in $x$ e $D[f\pm g]=Df\pm Dg$;
> 2. $f\cdot g$ è derivabile in $x$ e $D[fg]=g\,Df+f\,Dg$;
> 3. se $g(x)\ne0$, $\dfrac fg$ è derivabile in $x$ e $D\!\left[\dfrac fg\right]=\dfrac{g\,Df-f\,Dg}{g^2}$.

*Dim.*
1. Somma: per l'algebra dei limiti
$$\frac{f(x+h)+g(x+h)-[f(x)+g(x)]}h=\frac{f(x+h)-f(x)}h+\frac{g(x+h)-g(x)}h\to Df(x)+Dg(x).$$
2. Prodotto: aggiungo e tolgo $f(x)g(x+h)$:
$$\frac{f(x+h)g(x+h)-f(x)g(x)}h=\frac{f(x+h)-f(x)}h\,g(x+h)+f(x)\,\frac{g(x+h)-g(x)}h\to f'(x)g(x)+f(x)g'(x),$$
usando $g(x+h)\to g(x)$ perché $g$ derivabile ⇒ continua (§4).
3. Quoziente: prima $\dfrac1g$:
$$\frac{\frac1{g(x+h)}-\frac1{g(x)}}h=-\frac{g(x+h)-g(x)}h\cdot\frac1{g(x+h)g(x)}\to-\frac{g'(x)}{g(x)^2};$$
poi $\dfrac fg=f\cdot\dfrac1g$ e la regola del prodotto. $\blacksquare$

Versione d'esame: [[5.4 Algebra delle derivate - prodotto e quoziente (★★)]].

Conseguenza: $D[c\,f]=c\,Df$ (prodotto con $Dc=0$), quindi la derivata è **lineare**.

**Esempio (tangente).**
$$D\tan x=D\frac{\sin x}{\cos x}=\frac{\cos x\cos x+\sin x\sin x}{\cos^2x}=\frac1{\cos^2x}=1+\tan^2x .$$

## 7. Derivata della funzione composta

> [!important] Teorema (regola della catena)
> Sia $g$ derivabile in $x$ e $f$ derivabile in $g(x)$. Allora $f\circ g$ è derivabile in $x$ e
> $$D[(f\circ g)(x)]=f'(g(x))\cdot g'(x).$$

**Esempi.** $f(x)=x^2$, $g(x)=\sin x$:
- $(f\circ g)(x)=(\sin x)^2\ \Rightarrow\ D=2\sin x\cos x$;
- $(g\circ f)(x)=\sin(x^2)\ \Rightarrow\ D=2x\cos(x^2)$.

Nota: $f\circ g\ne g\circ f$ in generale, quindi l'ordine conta (vedi [[Funzioni#Funzione composta|Funzione composta]]; continuità della composta: [[Funzioni continue e punti di discontinuità#3. Funzione composta|§3]]).

## 8. Derivata della funzione inversa

> [!important] Teorema
> Sia $I$ un intervallo e $f:I\to\mathbb R$ continua e invertibile (quindi $f^{-1}$ è continua su $f(I)$, per il [[Funzioni continue e punti di discontinuità#4. Funzione inversa|teorema di continuità dell'inversa]]). Se $f$ è derivabile in $x$ interno a $I$ con $f'(x)\ne0$, allora $f^{-1}$ è derivabile in $y=f(x)$ e
> $$D[f^{-1}](y)=\frac1{f'(x)}\Bigg|_{x=f^{-1}(y)} .$$

Geometricamente: il grafico di $f^{-1}$ è il simmetrico di quello di $f$ rispetto a $y=x$, quindi la tangente ha pendenza reciproca. Se $f'(x)=0$ la tangente a $f^{-1}$ è verticale e $f^{-1}$ non è derivabile.

**Esempi.**
- **Esponenziale** $a^x$ ($a>0$, $a\ne1$), inversa di $\log_a y$:
$$D[a^x]=\frac1{D[\log_a y]}\Bigg|_{y=a^x}=\frac{y}{\log_a e}\Bigg|_{y=a^x}=\frac{a^x}{\log_a e}=a^x\ln a ,$$
perché $\log_a e=\dfrac1{\ln a}$. Per $a=e$: $D[e^x]=e^x$.
- **Potenza reale** $x^\alpha$, $\alpha\in\mathbb R$, $x>0$: scrivo $x^\alpha=e^{\alpha\ln x}$ e uso la regola della catena:
$$D[x^\alpha]=e^{\alpha\ln x}\cdot\frac\alpha x=x^\alpha\,\frac\alpha x=\alpha x^{\alpha-1}.$$
- **Arcoseno** ($\arcsin:[-1,1]\to[-\frac\pi2,\frac\pi2]$, inversa di $\sin$ ristretto, vedi [[Funzioni#d) Funzioni circolari inverse|funzioni circolari inverse]]):
$$D[\arcsin x]=\frac1{\cos y}\Bigg|_{y=\arcsin x}.$$
Per $y\in(-\frac\pi2,\frac\pi2)$ è $\cos y>0$, quindi $\cos y=+\sqrt{1-\sin^2y}$ e
$$D[\arcsin x]=\frac1{\sqrt{1-\sin^2(\arcsin x)}}=\frac1{\sqrt{1-x^2}},\qquad x\in(-1,1).$$
In $x=\pm1$ non è derivabile (tangente verticale, perché $\cos(\pm\frac\pi2)=0$).
- **Arcocoseno** (inversa di $\cos$ su $[0,\pi]$, dove $\sin y>0$ all'interno):
$$D[\arccos x]=\frac1{-\sin y}\Bigg|_{y=\arccos x}=-\frac1{\sqrt{1-x^2}},\qquad x\in(-1,1).$$
- **Arcotangente** (inversa di $\tan$ su $(-\frac\pi2,\frac\pi2)$):
$$D[\arctan x]=\frac1{1+\tan^2y}\Bigg|_{y=\arctan x}=\frac1{1+x^2},\qquad x\in\mathbb R .$$

## 9. Tabella riassuntiva

| $f(x)$ | $f'(x)$ | dove |
|---|---|---|
| $c$ | $0$ | $\mathbb R$ |
| $x^\alpha$ | $\alpha x^{\alpha-1}$ | $x>0$ (per $\alpha\in\mathbb N$: $\mathbb R$) |
| $e^x$ | $e^x$ | $\mathbb R$ |
| $a^x$ | $a^x\ln a$ | $\mathbb R$ |
| $\ln x$ | $\dfrac1x$ | $x>0$ |
| $\log_a x$ | $\dfrac1{x\ln a}$ | $x>0$ |
| $\sin x$ | $\cos x$ | $\mathbb R$ |
| $\cos x$ | $-\sin x$ | $\mathbb R$ |
| $\tan x$ | $\dfrac1{\cos^2x}=1+\tan^2x$ | $x\ne\frac\pi2+k\pi$ |
| $\arcsin x$ | $\dfrac1{\sqrt{1-x^2}}$ | $(-1,1)$ |
| $\arccos x$ | $-\dfrac1{\sqrt{1-x^2}}$ | $(-1,1)$ |
| $\arctan x$ | $\dfrac1{1+x^2}$ | $\mathbb R$ |

## Collegamenti
- Teoria precedente: [[Funzioni continue e punti di discontinuità]]
- o-piccolo e limiti notevoli: [[Limiti di funzioni]] · [[Confronti e stime asintotiche]]
- Funzione inversa e composta: [[Funzioni]]
- Dimostrazioni: [[5.1 Derivabile ⟹ continua (★)|5.1]] · [[5.2 Derivate di alcune funzioni elementari (★★)|5.2]] · [[5.3 Differenziabilità ⟺ derivabilità (★)|5.3]] · [[5.4 Algebra delle derivate - prodotto e quoziente (★★)|5.4]]
- Appunti a mano: [[Drawing 2026-11-11 10.12.34.excalidraw]]
