---
tags:
  - analisi1
  - continuità
  - discontinuità
  - teorema-zeri
  - politecnico
---
# Funzioni continue e punti di discontinuità

Fonte: Lezione 13 (4 novembre), AM1 2026-27, + appunti a mano [[Drawing 2026-11-09 08.11.22.excalidraw|lezione del 9/11]].
Prosegue da [[Limiti di funzioni]].

## 1. Definizione

**Def.** Sia $f:A\subseteq\mathbb R\to\mathbb R$, $x_0\in A$ punto di accumulazione per $A$. $f$ è **continua in $x_0$** se
$$\lim_{x\to x_0}f(x)=f(x_0).$$
In termini di $\varepsilon$–$\delta$: $\forall\varepsilon>0\ \exists\delta=\delta(\varepsilon,x_0)>0$ t.c. $\lvert f(x)-f(x_0)\rvert<\varepsilon\ \ \forall x\in A\cap I_\delta(x_0)$.

(Qui non serve escludere $x=x_0$: in $x_0$ vale $\lvert f(x_0)-f(x_0)\rvert=0<\varepsilon$.)

**Def.** $f$ è **continua in $A$** se è continua in ogni $x\in A$.

Tre richieste insieme: $f(x_0)$ esiste, il limite esiste finito, e i due coincidono.

## 2. Continuità delle funzioni elementari

**Proposizione.** Sia $a>0$. Allora $\lim_{x\to0}a^x=a^0=1$, cioè $a^x$ è continua in $x_0=0$.

*Dim.*
- $a=1$: immediato ($1^x=1$).
- $a>1$: fisso $0<\varepsilon<1$ arbitrario. Voglio $-\varepsilon<a^x-1<\varepsilon$, cioè $0<1-\varepsilon<a^x<1+\varepsilon$. Passando al logaritmo (base $e$, crescente):
$$\log(1-\varepsilon)<x\log a<\log(1+\varepsilon)\iff x_1:=\frac{\log(1-\varepsilon)}{\log a}<x<\frac{\log(1+\varepsilon)}{\log a}=:x_2,$$
con $x_1<0<x_2$. Scelgo $\delta:=\min\{-x_1,x_2\}$: se $-\delta<x<\delta$ allora $\lvert a^x-1\rvert<\varepsilon$.
- $0<a<1$: scrivo $a^x=\big(\frac1a\big)^{-x}$ e applico il caso precedente a $\frac1a>1$. $\blacksquare$

**Proposizione.** $a^x$ ($a>0$) è continua in $\mathbb R$: $\lim_{x\to x_0}a^x=a^{x_0}\ \forall x_0\in\mathbb R$.

*Dim.* $a^x-a^{x_0}=a^{x_0}\big(a^{x-x_0}-1\big)$. Con $y=x-x_0\to0$ si ha $a^y-1\to0$ per la proposizione precedente. $\blacksquare$

**Proposizione.** Polinomi e funzioni razionali sono continui nel loro insieme di definizione.

*Dim.* $\lim_{x\to x_0}x=x_0$; per l'algebra dei limiti $\lim x^m=x_0^m$, poi
$$\lim_{x\to x_0}P(x)=a_m x_0^m+a_{m-1}x_0^{m-1}+\dots+a_0=P(x_0),\qquad\lim_{x\to x_0}\frac{P(x)}{Q(x)}=\frac{P(x_0)}{Q(x_0)}\quad(Q(x_0)\neq0).\ \blacksquare$$

**Proposizione.** $\sin x$ e $\cos x$ sono continue in $\mathbb R$.

*Dim.* Formule di prostaferesi:
$$\sin x-\sin x_0=2\sin\Big(\frac{x-x_0}2\Big)\cos\Big(\frac{x+x_0}2\Big),\qquad\cos x-\cos x_0=-2\sin\Big(\frac{x-x_0}2\Big)\sin\Big(\frac{x+x_0}2\Big).$$
Usando $\lvert\sin t\rvert\le\lvert t\rvert$ e $\lvert\cos\rvert,\lvert\sin\rvert\le1$:
$$0\le\lvert\sin x-\sin x_0\rvert\le2\Big\lvert\sin\frac{x-x_0}2\Big\rvert\le2\,\frac{\lvert x-x_0\rvert}2=\lvert x-x_0\rvert\xrightarrow{x\to x_0}0 .$$
Per i due carabinieri $\lvert\sin x-\sin x_0\rvert\to0$, cioè $\sin x\to\sin x_0$. Identico per il coseno. $\blacksquare$

Dimostrazione d'esame: [[4.2 Continuità di sin e cos (★★)]].

**Corollario.** $\tan x$ e $\cot x$ sono continue nel loro insieme di definizione:
$$\lim_{x\to x_0}\tan x=\lim_{x\to x_0}\frac{\sin x}{\cos x}=\frac{\lim\sin x}{\lim\cos x}=\frac{\sin x_0}{\cos x_0}=\tan x_0 .$$

## 3. Funzione composta

> [!important] Teorema (limite della funzione composta)
> Sia $\lim_{x\to x_0}f(x)=y_0$ e sia $g$ continua in $y_0$. Allora
> $$\lim_{x\to x_0}g\big(f(x)\big)=g\Big(\lim_{x\to x_0}f(x)\Big)=g(y_0).$$

**Corollario (continuità della composta).** Se $f$ è continua in $x_0$ e $g$ è continua in $y_0=f(x_0)$, allora $g\circ f$ è continua in $x_0$.

*Dim.* Devo provare $\lim_{x\to x_0}g(f(x))=g(f(x_0))$. Per ipotesi $\lim_{x\to x_0}f(x)=f(x_0)=y_0$; per il teorema precedente (applicabile perché $g$ è continua in $y_0$)
$$\lim_{x\to x_0}g[f(x)]=g\Big[\lim_{x\to x_0}f(x)\Big]=g[f(x_0)].\ \blacksquare$$

**Esempi.** $\lim_{x\to0}\sin(x^2)=\sin\big(\lim x^2\big)=\sin0=0$; $\quad\lim_{x\to0}e^{\tan x+1}=e^{\tan0+1}=e$.

**Teorema (caratterizzazione per successioni).** $f$ è continua in $x_0\in A$ $\iff$ $\forall\{x_n\}\subseteq A$ con $x_n\to x_0$: $\lim_n f(x_n)=f(x_0)$. (Teorema ponte, vedi [[Limiti di funzioni#4. Teorema ponte (limiti di funzioni ↔ limiti di successioni)|Limiti di funzioni]].)

## 4. Funzione inversa

> [!important] Teorema (continuità della funzione inversa)
> Sia $I\subseteq\mathbb R$ un **intervallo** e $f:I\to\mathbb R$ continua e invertibile in $I$. Allora $f(I)$ è un intervallo e $f^{-1}:f(I)\to I$ è continua su $f(I)$.

**L'ipotesi "$I$ intervallo" è necessaria.** Controesempio:
$$f(x)=\begin{cases}x&0\le x<1\\x-1&2\le x\le3\end{cases}\qquad D=[0,1)\cup[2,3]\ \text{(non è un intervallo)}.$$
$f$ è continua in $D$ e invertibile, con $f(D)=[0,2]$ e
$$f^{-1}(x)=\begin{cases}x&0\le x<1\\x+1&1\le x\le2\end{cases}$$
ma $f^{-1}$ **non è continua** in $x=1$: $\lim_{x\to1^-}f^{-1}(x)=1\neq2=f^{-1}(1)=\lim_{x\to1^+}f^{-1}(x)$.

**Conseguenza.** Le inverse delle funzioni circolari ($\arcsin,\arccos,\arctan$) sono continue nei loro domini, e $\log_a x$ ($a>0$, $a\neq1$) è continua in $(0,+\infty)$.

Riassunto: **tutte le funzioni elementari sono continue dove sono definite**, e così somme, prodotti, quozienti e composizioni.

## 5. Punti di discontinuità

**Def.** $f:D\subseteq\mathbb R\to\mathbb R$, $x_0\in D$ di accumulazione per $D$. $x_0$ è **punto di discontinuità** per $f$ se $f$ non è continua in $x_0$, cioè $\lim_{x\to x_0}f(x)\neq f(x_0)$ (o il limite non esiste).

| Caso | Limiti $x\to x_0^\pm$ | Nome |
|---|---|---|
| 1 | esistono **finiti** ma **diversi** | 1ª specie (di **salto**) |
| 2 | esistono, ma almeno uno è $\pm\infty$ | 2ª specie |
| 3 | almeno uno **non esiste** | 3ª specie |
| 4 | esistono finiti e **uguali** a $\ell$, ma $f(x_0)\neq\ell$ | **eliminabile** |

> [!note] Convenzioni
> In molti testi i casi 2 e 3 sono raccolti insieme come "2ª specie". Qui si segue la numerazione del corso.

### Caso 1 — salto
$\lim_{x\to x_0^-}f=\ell_1\neq\ell_2=\lim_{x\to x_0^+}f$. Il **salto** di $f$ in $x_0$ è
$$s(x_0)=\Big\lvert\lim_{x\to x_0^+}f(x)-\lim_{x\to x_0^-}f(x)\Big\rvert .$$
**Esempio.** $f(x)=[x]$ (parte intera), $x_0=1$: $\lim_{x\to1^-}[x]=0$, $\lim_{x\to1^+}[x]=1=[1]=f(1)$, $s(1)=1$.

### Caso 2 — 2ª specie
**Esempio.** $f(x)=\begin{cases}e^{1/x}&x\neq0\\0&x=0\end{cases}$, $D=\mathbb R$: $\lim_{x\to0^-}f=0$, $\lim_{x\to0^+}f=+\infty$. $x_0=0$ è di 2ª specie.

(Per $f(x)=\frac1x$ invece $0\notin D=\mathbb R\setminus\{0\}$: non si parla di discontinuità in $0$, $f$ è continua nel suo dominio.)

### Caso 3 — 3ª specie
**Esempio.** $f(x)=\begin{cases}\sin\frac1x&x\neq0\\1&x=0\end{cases}$, $x_0=0$: $\lim_{x\to0^\pm}\sin\frac1x$ non esiste (si dimostra come per $\cos\frac1x$ col teorema ponte). Quindi $0$ è di 3ª specie.

### Caso 4 — eliminabile
$\lim_{x\to x_0}f(x)=\ell$ ma $f(x_0)\neq\ell$. Si "ripara" ridefinendo $f$ in un solo punto:
$$\tilde f(x)=\begin{cases}f(x)&x\in D\setminus\{x_0\}\\\ell&x=x_0\end{cases}\qquad\Rightarrow\ \tilde f\ \text{continua in }x_0 .$$
**Esempio.** $f(x)=[\operatorname{sgn}(x)]^2$, $x_0=0$: $\lim_{x\to0^\pm}f=1$ ma $f(0)=0$. Discontinuità eliminabile; $\tilde f(x)\equiv1$ è continua in $\mathbb R$.

### Prolungamento (estensione) continuo
**Oss.** Se $x_0\notin D$ ma $\lim_{x\to x_0^+}f=\ell=\lim_{x\to x_0^-}f$, posso definire
$$\tilde f(x)=\begin{cases}f(x)&x\in D\\\ell&x=x_0\end{cases}$$
che è continua in $x_0$: si chiama **estensione (o prolungamento) continuo** di $f$ in $x_0$.

**Esempio.** $f(x)=\frac{\sin x}x$ su $\mathbb R\setminus\{0\}$: $\lim_{x\to0^\pm}f=1$, quindi
$$\tilde f(x)=\begin{cases}\dfrac{\sin x}x&x\neq0\\1&x=0\end{cases}$$
è continua in $\mathbb R$.

```desmos-graph
left=-15; right=15; top=1.5; bottom=-0.5;
---
y=\frac{\sin(x)}{x}
(0,1)
```

## 6. Permanenza del segno (per funzioni continue)

> [!important] Teorema
> Sia $f:A\to\mathbb R$ continua e $x_0\in A$. Se $f(x_0)>c$ (per qualche $c\in\mathbb R$) allora $\exists\delta>0$ t.c.
> $$f(x)>c\qquad\forall x\in I_\delta(x_0)\cap A .$$

*Idea della dim.* Applico la permanenza del segno per i limiti a $f(x)-c$: è continua e $\lim_{x\to x_0}(f(x)-c)=f(x_0)-c>0$.

**La continuità serve.** $f(x)=\frac12+\operatorname{sgn}(x)$ non è continua in $0$; $f(0)=\frac12>0$, ma in ogni intorno di $0$ ci sono $x<0$ con $f(x)=-\frac12<0$.

## 7. Teorema di esistenza degli zeri

> [!important] Teorema (esistenza degli zeri)
> Sia $f$ continua su $[a,b]$ con $f(a)<0$ e $f(b)>0$. Allora $\exists x_0\in(a,b)$ t.c. $f(x_0)=0$.
> (Stessa cosa se $f(a)>0>f(b)$: basta considerare $-f$.)

**Dimostrazione (metodo di bisezione, come a lezione).**
Sia $c=\frac{a+b}2$ il punto medio.
- Se $f(c)=0$: $x_0=c$ e ho finito.
- Se $f(c)>0$: pongo $a_1=a$, $b_1=c$, così $f(a_1)<0<f(b_1)$.
- Se $f(c)<0$: pongo $a_1=c$, $b_1=b$, così $f(a_1)<0<f(b_1)$.

Ripeto su $[a_1,b_1]$ con $c_1=\frac{a_1+b_1}2$, e così via. Se a un passo $f(c_n)=0$ ho finito ($x_0=c_n$). Altrimenti costruisco tre successioni:
- $\{a_n\}$ estremi sinistri, $\{b_n\}$ estremi destri, $\{c_n\}$ punti medi,

con $f(c_n)>0\Rightarrow a_{n+1}=a_n,\ b_{n+1}=c_n$ e $f(c_n)<0\Rightarrow a_{n+1}=c_n,\ b_{n+1}=b_n$. Per costruzione:
1. $f(a_n)<0$ e $f(b_n)>0$ per ogni $n$;
2. $\{a_n\}$ è monotona **crescente**, $\{b_n\}$ monotona **decrescente**;
3. $a\le a_n<b_n\le b$ per ogni $n$: sono **limitate**;
4. $b_n-a_n=\dfrac{b-a}{2^n}$ (ogni passo dimezza l'intervallo).

Per il teorema di regolarità delle successioni monotone (e la limitatezza) $\exists\lim a_n=\xi\in\mathbb R$, e per confronto $a\le\xi\le b$. Da (4):
$$\lim_n b_n=\lim_n\Big(a_n+\frac{b-a}{2^n}\Big)=\xi .$$
Per il teorema ponte e la continuità di $f$ in $\xi$:
$$\lim_n f(a_n)=f(\xi)\le0,\qquad\lim_n f(b_n)=f(\xi)\ge0$$
(permanenza del segno per successioni, perché $f(a_n)<0$ e $f(b_n)>0$). Quindi $f(\xi)=0$, e $\xi\neq a,b$ perché $f(a),f(b)\neq0$: $x_0=\xi$ è il punto cercato. $\blacksquare$

Dimostrazione alternativa (con il sup) e esercizi: [[4.3 Teorema di esistenza degli zeri (★)]].

> [!tip] Bisezione = algoritmo
> La dimostrazione è costruttiva: dopo $n$ passi lo zero sta in un intervallo lungo $\frac{b-a}{2^n}$. È il metodo numerico di bisezione.

**Osservazioni.**
1. Se $f$ è **strettamente monotona**, lo zero è **unico**.
2. **Serve che il dominio sia un intervallo.** $f:[-1,0]\cup[1,2]\to\mathbb R$, $f=-1$ su $[-1,0]$, $f=2$ su $[1,2]$: $f$ è continua, $f(-1)<0<f(2)$, ma non si annulla mai.
3. **Serve la continuità.** $f(x)=\frac12+\operatorname{sgn}(x)$ su $[-1,1]$: $f(-1)=-\frac12<0$, $f(1)=\frac32>0$, ma $\nexists x_0\in(-1,1)$ con $f(x_0)=0$.
4. **Intervallo illimitato.** Se $f$ è continua in $[a,+\infty)$, $f(a)<0$ e $\lim_{x\to+\infty}f(x)>0$ (anche $+\infty$), per la permanenza del segno $\exists x_1>a$ con $f(x_1)>0$. Applico il teorema su $[a,x_1]$: esiste lo zero.

## 8. Teorema dei valori intermedi

> [!important] Teorema (valori intermedi)
> Una funzione continua su un intervallo $I$ assume **tutti** i valori compresi tra $\inf_I f$ e $\sup_I f$:
> $$\forall y_0\in\Big(\inf_I f,\ \sup_I f\Big)\ \ \exists x_0\in I\ \text{t.c.}\ f(x_0)=y_0 .$$

**Oss.** L'immagine di un intervallo tramite una funzione continua è un intervallo: $f(I)$ è un intervallo.

*Dim.* Siano $m=\inf_I f$, $M=\sup_I f$ e $y_0\in(m,M)$.
- $y_0>m$ ⇒ (def. di inf) $\exists a\in I$ con $f(a)<y_0$;
- $y_0<M$ ⇒ (def. di sup) $\exists b\in I$ con $f(b)>y_0$.

Pongo $g(x)=f(x)-y_0$: è continua in $I$ e $g(a)<0<g(b)$. Poiché $I$ è un intervallo, contiene tutto il segmento tra $a$ e $b$; per il teorema degli zeri (su $[a,b]$, o $[b,a]$ se $b<a$) $\exists x_0$ con $g(x_0)=0$, cioè $f(x_0)=y_0$. $\blacksquare$

Versione d'esame: [[4.4 Teorema dei valori intermedi (★)]]. Prossimo: [[4.5 Teorema di Weierstrass (★)]].

## Collegamenti
- Teoria precedente: [[Limiti di funzioni]]
- Esercizi: [[Limiti di funzioni — Esercizi]] (sezione continuità)
- Appunti a mano: [[Drawing 2026-11-09 08.11.22.excalidraw]]
