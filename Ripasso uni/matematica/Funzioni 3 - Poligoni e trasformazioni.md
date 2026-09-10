---
date: 2026-09-09
subject: matematica
topic: funzioni
tags:
  - matematica
  - funzioni
  - geometria
  - trasformazioni
---
# Lezione 8: Funzioni (3) — Warm-up

Corso di ripasso Matematica, laboratorio FDS (MOOC MAT101 Polimi).

## A) Poligoni regolari

Un poligono regolare di $n$ lati di lunghezza $l$ si scompone in $n$ triangoli isosceli congruenti, con vertice nel centro e base $l$. L'altezza di ciascun triangolo (l'**apotema** $a$) si trova dividendo a metà l'angolo al centro $\frac{2\pi}{n}$:
$$
\tan\!\left(\frac{\pi}{n}\right) = \frac{l/2}{a} \;\Rightarrow\; a = \frac{l}{2\tan(\pi/n)}
$$

L'area di un triangolo è $\frac{1}{2}\cdot l \cdot a$, e ce ne sono $n$:
$$
A(n) = n \cdot \frac12 \cdot l \cdot a = \frac{n\,l^2}{4\tan(\pi/n)} = \frac{n\,l^2}{4}\cot\!\left(\frac{\pi}{n}\right)
$$

Verifica: per $n\to\infty$, $A(n) \to \pi r^2$ con $r$ = raggio del cerchio circoscritto (il poligono tende al cerchio); per $n=4$, $l$=lato del quadrato, $A(4)=l^2$ ✓ ($\cot(\pi/4)=1$).

Grafico di $A(n)$ per $l=1$ (n trattato come variabile continua per visualizzare l'andamento):
```desmos-graph
left=2; right=20; top=4; bottom=0;
---
A=\frac{n}{4}\cot\left(\frac{\pi}{n}\right)
```
Si vede che l'area cresce con $n$ e si stabilizza verso $\pi/4\approx0.785$ (l'area del cerchio di raggio $1/2$ inscritto... in realtà qui il lato è fisso, quindi il poligono "si apre" e l'area cresce senza limite finito in questa parametrizzazione — il punto interessante è la crescita monotona verso $n\to\infty$).

## B) Trasformazioni di funzioni

Regole generali (con $f(x)$ funzione di partenza, $k>1$):

| Trasformazione | Effetto |
|---|---|
| $f(kx)$ | compressione orizzontale, fattore $1/k$ |
| $f(x/k)$ | dilatazione orizzontale, fattore $k$ |
| $k\,f(x)$ | dilatazione verticale, fattore $k$ |
| $f(x-c)$ | traslazione orizzontale di $+c$ |
| $f(x)+c$ | traslazione verticale di $+c$ |
| $f(x+c)-c'$ | traslazione orizzontale di $-c$ e verticale di $-c'$ |

Esempio applicato a $f(x)=x^3-x$ (scelta arbitraria, buona perché ha massimo e minimo locali visibili):

```desmos-graph
left=-4; right=4; top=6; bottom=-6;
---
f(x)=x^3-x
g(x)=f(3x)
h(x)=f(x/2)
```
$f(3x)$ "schiaccia" il grafico verso l'asse y (fattore $1/3$); $f(x/2)$ lo allarga (fattore $2$).

```desmos-graph
left=-4; right=4; top=15; bottom=-15;
---
f(x)=x^3-x
g(x)=5f(x)
```
$5f(x)$ stira verticalmente di un fattore 5 (stessi zeri, picchi 5 volte più alti).

```desmos-graph
left=-3; right=5; top=6; bottom=-6;
---
f(x)=x^3-x
g(x)=f(x-1)
```
$f(x-1)$ trasla il grafico di 1 verso destra.

```desmos-graph
left=-4; right=4; top=8; bottom=-6;
---
f(x)=x^3-x
g(x)=f(x)+2
```
$f(x)+2$ trasla il grafico di 2 verso l'alto.

```desmos-graph
left=-6; right=2; top=6; bottom=-8;
---
f(x)=x^3-x
g(x)=f(x+2)-1
```
$f(x+2)-1$: trasla di 2 verso sinistra e di 1 verso il basso (le due traslazioni sono indipendenti, si applicano nell'ordine che si preferisce).

## C) Reminder

Sul forum del MOOC MAT101, nella sezione discussione, puoi confrontarti con i tuoi colleghi e il tutor del Polimi riguardo questi esercizi di Warm-up.

## Risorse
- [FDS PoliMi](https://linktr.ee/fdspolimi)
