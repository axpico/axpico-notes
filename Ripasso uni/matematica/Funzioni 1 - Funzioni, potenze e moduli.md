---
date: 2026-09-07
subject: matematica
topic: funzioni
tags:
  - matematica
  - funzioni
  - potenze
  - valore-assoluto
  - disequazioni
---
# Lezione 6: Funzioni (1) — Warm-up

Corso di ripasso Matematica, laboratorio FDS (MOOC MAT101 Polimi).

## A) Funzioni

Un'equazione in $x,y$ rappresenta una **funzione** $y=f(x)$ solo se per ogni $x$ del dominio esiste **al massimo un** $y$ associato (test della retta verticale). È **invertibile** solo se, in più, ogni $y$ del codominio proviene da **un solo** $x$ (test della retta orizzontale, cioè iniettività).

| Equazione | Funzione? | Invertibile? | Inversa | Note |
|---|---|---|---|---|
| $x^2+y^2+4x-2y-4=0$ | **No** | — | — | Circonferenza: $(x+2)^2+(y-1)^2=9$, centro $(-2,1)$, raggio 3. Una $x$ dà due $y$ |
| $\dfrac{x^2}{4}-\dfrac{y^2}{3}=-1$ | **No** | — | — | Iperbole ($\dfrac{y^2}{3}-\dfrac{x^2}{4}=1$), asse trasverso verticale: due $y$ per ogni $x$ nel dominio |
| $y^2-x+1=0$ | **No** | — | — | $x=y^2+1$: è funzione di $y$, non di $x$ (parabola "sdraiata") |
| $x^2-y-4=0$ | **Sì**, $y=x^2-4$ | **No** (su $\mathbb R$) | — | Parabola: $x$ e $-x$ danno stesso $y$. Invertibile solo restringendo a $x\ge0$ o $x\le0$ |
| $x^2-y^2=1$ | **No** | — | — | $y=\pm\sqrt{x^2-1}$: due valori di $y$, dominio $|x|\ge1$ |
| $xy=2$ | **Sì**, $y=\dfrac2x$ ($x\ne0$) | **Sì** | $y=\dfrac2x$ | È **la propria inversa** (involuzione): $f(f(x))=x$ |
| $\log x-3y+1=0$ | **Sì**, $y=\dfrac{\log x+1}{3}$ ($x>0$) | **Sì** | $x=e^{3y-1}$ | Strettamente crescente ⇒ biettiva dal dominio $x>0$ a tutto $\mathbb R$ |
| $y=x^2$ | **Sì** | **No** (su $\mathbb R$) | — | Stesso motivo di $y=x^2-4$: non iniettiva |
| $y^3+x-2=0$ | **Sì**, $y=\sqrt[3]{2-x}$ | **Sì** | $x=2-y^3$ | Radice cubica: monotona decrescente su tutto $\mathbb R$, quindi biettiva |
| $y=\sin x$ | **Sì** | **No** (su $\mathbb R$) | — | Periodica: non iniettiva. Invertibile solo su $[-\pi/2,\pi/2]$ ⇒ $\arcsin x$ |
| $y=\sin x\cdot e^{\cos x}$ | **Sì** | **No** | — | Periodica (periodo $2\pi$): non iniettiva |
| $y=x\log x-\arctan x$ | **Sì** ($x>0$) | Non elementare | — | Dominio $x>0$; nessuna forma chiusa semplice per l'inversa |

## B) Potenze

**$a^b$ è una potenza (cioè un numero reale ben definito) per ogni $a,b\in\mathbb R$?** No.

- **$a>0$**: sempre definita, per qualunque $b$ reale (via $a^b=e^{b\ln a}$).
- **$a=0$**: definita solo se $b>0$ (vale $0$); per $b=0$ è **indeterminata** ($0^0$), per $b<0$ **non definita** (divisione per 0).
- **$a<0$**: definita in $\mathbb R$ solo se $b$ è intero (o razionale con denominatore dispari, es. $\sqrt[3]{\cdot}$); per $b$ generico (es. irrazionale o radice pari) **non è reale**.

| | $a>0$ | $a=0$ | $a<0$ |
|---|---|---|---|
| $b>0$ | $2^3=8$ | $0^2=0$ | $(-2)^3=-8$ (ok, $b$ intero); $(-2)^{1/2}$ non reale |
| $b=0$ | $2^0=1$ | $0^0$ **indeterminato** | $(-2)^0=1$ |
| $b<0$ | $2^{-3}=\frac18$ | $0^{-1}$ **non definito** | $(-2)^{-3}=-\frac18$ (ok, $b$ intero) |

## C) Moduli

### 1. Disequazioni con modulo (approccio grafico)

Idea grafica: disegnare $y=|f(x)|$ e la retta orizzontale del termine noto, poi guardare dove il grafico sta sotto/sopra la retta.

**$|x|<3$**
```desmos-graph
left=-6; right=6; top=6; bottom=-1;
---
y=\operatorname{abs}\left(x\right)
y=3
```
Soluzione: dove il grafico del modulo è sotto la retta orizzontale.
$$
-3 < x < 3
$$

**$|x+2|<5$**
```desmos-graph
left=-10; right=8; top=8; bottom=-1;
---
y=\operatorname{abs}\left(x+2\right)
y=5
```
$$
-5<x+2<5 \;\Rightarrow\; -7<x<3
$$

**$|2x-4|>3$**
```desmos-graph
left=-3; right=8; top=8; bottom=-1;
---
y=\operatorname{abs}\left(2x-4\right)
y=3
```
Qui si cerca dove il grafico del modulo è **sopra** la retta orizzontale:
$$
2x-4>3 \;\lor\; 2x-4<-3 \;\Rightarrow\; x>\frac72 \;\lor\; x<\frac12
$$

**$|3-x|<-1$**
```desmos-graph
left=-4; right=10; top=6; bottom=-3;
---
y=\operatorname{abs}\left(3-x\right)
y=-1
```
Un modulo sta sempre a $y\ge0$, non scende mai sotto la retta $y=-1$:
$$
\text{nessuna soluzione} \;\Rightarrow\; \varnothing
$$

### 2. Insiemi numerici in notazione modulo

Un intervallo simmetrico $(c-r,c+r)$ si scrive $|x-c|<r$; il suo complementare $|x-c|>r$.

- **$-3<x<1$**: centro $c=\dfrac{-3+1}{2}=-1$, raggio $r=2$
$$
|x+1|<2
$$

- **$\varnothing$**: un modulo non può mai essere negativo, quindi basta chiedere che sia $<0$
$$
|x|<0
$$

- **$-\infty<x<-5 \;\lor\; 1<x<+\infty$**: è il complementare di $[-5,1]$, centro $c=\dfrac{-5+1}{2}=-2$, raggio $r=3$
$$
|x+2|>3
$$

- **$\mathbb R$**: il modulo è sempre $\ge0$, condizione sempre vera
$$
|x|\ge0
$$
