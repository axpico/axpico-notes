---
tags:
  - analisi1
  - successioni
  - limiti
  - politecnico
---
Prosegue da [[Algebra dei limiti e teoremi sui limiti]].

## Confronto per limiti infiniti

**Teorema.** Siano $a_n\le b_n$ per ogni $n$ (o definitivamente).
- Se $a_n\to+\infty$ allora $b_n\to+\infty$ (la minorante diverge ⟹ la maggiorante diverge).
- Se $b_n\to-\infty$ allora $a_n\to-\infty$ (la maggiorante diverge a $-\infty$ ⟹ la minorante diverge).

*Dimostrazione (primo caso).* $a_n\to+\infty$: $\forall M\ \exists\nu$ t.c. $a_n>M\ \forall n>\nu$. Allora $b_n\ge a_n>M$ per $n>\nu$, cioè $b_n\to+\infty$. ∎

> [!warning] Attenzione alla direzione
> Il confronto "spinge" solo verso l'alto con la minorante e verso il basso con la maggiorante. Da $a_n\le b_n$ e $b_n\to+\infty$ **non** si deduce nulla su $a_n$.

## Successioni infinitesime

**Definizione.** $\{a_n\}$ è **infinitesima** se $a_n\to0$.

**Lemma.** $a_n\to0\iff|a_n|\to0$.
*(Dimostrazione: $|a_n-0|=||a_n|-0|$, la condizione $\forall\varepsilon$ è identica.)*

**Teorema (limitata × infinitesima).** Se $\{a_n\}$ è limitata e $\{b_n\}$ è infinitesima, allora $a_nb_n\to0$.

*Dimostrazione.* Per il lemma $|b_n|\to0$. Sia $M$ t.c. $|a_n|\le M\ \forall n$. Allora
$$
0\le|a_nb_n|=|a_n|\,|b_n|\le M|b_n|\xrightarrow[n\to\infty]{}0 .
$$
Per i due carabinieri $|a_nb_n|\to0$ e, per il lemma, $a_nb_n\to0$. ∎

**Esempi.**
- $\dfrac{\sin n}{n}=\sin n\cdot\dfrac1n\to0$: $|\sin n|\le1$ è limitata, $\frac1n$ è infinitesima.
- $a_n=n$, $b_n=\frac1n$: $a_nb_n=1\to1\neq0$. Qui $a_n$ **non è limitata**: l'ipotesi di limitatezza è *necessaria* (non solo sufficiente).

## Teorema sulle successioni monotone

**Teorema.** Ogni successione monotona ammette limite. Più precisamente
- $\{a_n\}$ crescente ⟹ $a_n\to\sup\{a_n\}$ (che è $+\infty$ se non limitata superiormente);
- $\{a_n\}$ decrescente ⟹ $a_n\to\inf\{a_n\}$.

**Dimostrazione ($\{a_n\}$ crescente).**

*Caso limitata superiormente.* Per la completezza di $\mathbb{R}$ (vedi [[Estremo superiore ed estremo inferiore, completezza di ℝ]]) esiste $\lambda:=\sup\{a_n\}\in\mathbb{R}$. Per la caratterizzazione del sup:
$$
\forall\varepsilon>0\ \exists\nu\in\mathbb{N}:\ a_\nu>\lambda-\varepsilon .
$$
Poiché $a_n$ è crescente, $a_n\ge a_\nu$ per ogni $n>\nu$; inoltre $a_n\le\lambda$ per definizione di sup. Dunque
$$
\lambda-\varepsilon<a_\nu\le a_n\le\lambda<\lambda+\varepsilon\quad\forall n>\nu
\ \Rightarrow\ |a_n-\lambda|<\varepsilon\ \ \forall n>\nu,
$$
cioè $a_n\to\lambda$.

*Caso illimitata superiormente.* $\forall M\ \exists\nu$ t.c. $a_\nu>M$ (altrimenti $M$ sarebbe maggiorante). Per monotonia $a_n\ge a_\nu>M\ \forall n>\nu$, cioè $a_n\to+\infty$. ∎

Il caso decrescente si ottiene applicando il risultato a $-a_n$.

> [!tip] Cosa dice davvero
> Una successione **crescente e limitata** converge (non serve conoscere il limite a priori). È il primo strumento per provare l'*esistenza* di un limite senza calcolarlo.

## Il numero di Nepero

Si considera $a_n=\left(1+\dfrac1n\right)^n$. Si dimostra (via Bernoulli / disuguaglianza AM-GM) che è **crescente** e **limitata superiormente** (da $3$). Per il teorema precedente ammette limite, che per definizione è
$$
e:=\lim_{n\to\infty}\left(1+\frac1n\right)^n=\sup_n\left(1+\frac1n\right)^n,\qquad e\in\mathbb{R}\setminus\mathbb{Q},\ \ e\approx2{,}718 .
$$

## Limiti notevoli di successioni

### (a) Successione geometrica $a^n$

$$
\lim_{n\to\infty}a^n=\begin{cases}+\infty & a>1\\ 1 & a=1\\ 0 & -1<a<1\\ \nexists & a\le-1\end{cases}
$$

*Dimostrazione.*
- **$a>1$.** Pongo $x=a-1>0$. Per la **disuguaglianza di Bernoulli** ($(1+x)^n\ge1+nx$ per $x>-1$, $n\in\mathbb{N}$, vedi [[Insieme numerici, logia e dimostrazioni]]):
$$
a^n=(1+x)^n\ge1+nx=1+n(a-1)\xrightarrow[n\to\infty]{}+\infty,
$$
e per il confronto $a^n\to+\infty$.
- **$a=1$,** $1^n=1\to1$.
- **$-1<a<1$, $a\ne0$.** $|a^n|=|a|^n=\dfrac{1}{(1/|a|)^n}$ e $1/|a|>1$, quindi $(1/|a|)^n\to+\infty$ per il caso 1 ⟹ $|a|^n\to0$ ⟹ $a^n\to0$ (lemma). Per $a=0$ è banale.
- **$a\le-1$.** Considero due sottosuccessioni:
$$
a^{2k}\to\begin{cases}1&a=-1\\+\infty&a<-1\end{cases},\qquad
a^{2k+1}\to\begin{cases}-1&a=-1\\-\infty&a<-1\end{cases}
$$
Limiti diversi lungo due sottosuccessioni ⟹ il limite non esiste. ∎

### (b) Radice $n$-esima

Sia $a>0$. Allora $\displaystyle\lim_{n\to\infty}\sqrt[n]{a}=1$.

*Dimostrazione.*
- **$a\ge1$.** Pongo $b_n:=\sqrt[n]{a}-1\ge0$. Per Bernoulli:
$$
a=(1+b_n)^n\ge1+nb_n\ \Rightarrow\ 0\le b_n\le\frac{a-1}{n}\to0 .
$$
Per i due carabinieri $b_n\to0$, cioè $\sqrt[n]{a}\to1$.
- **$0<a<1$.** $\frac1a>1$ e $\sqrt[n]{a}=\dfrac{1}{\sqrt[n]{1/a}}\to\dfrac11=1$. ∎

*Osservazione.* Per ogni $b\in\mathbb{R}$: $\displaystyle\lim_{n\to\infty}\sqrt[n]{n^b}=\lim\left(\sqrt[n]{n}\right)^b=1$ (si usa $\sqrt[n]{n}\to1$).

### (c) Generalizzazione del limite di Nepero

Se $a_n\to\pm\infty$, allora per ogni $\alpha\in\mathbb{R}$
$$
\left(1+\frac{\alpha}{a_n}\right)^{a_n}\xrightarrow[n\to\infty]{}e^{\alpha}.
$$
(È una forma indeterminata $1^{\infty}$.)

### Disuguaglianza fondamentale per i limiti trigonometrici

Per $0<|x|<\dfrac\pi2$ vale
$$
\cos x<\frac{\sin x}{x}<1 .
$$

```desmos-graph
left=-0.3; right=1.6;
top=1.5; bottom=-0.4;
---
a=0.9
x^2+y^2=1
y=\tan(a)x\left\{0\le x\le1\right\}
x=1\left\{0\le y\le\tan(a)\right\}
(0,0)|label:O
(1,0)|label:A
(\cos(a),\sin(a))|label:B
(1,\tan(a))|label:D
```

Nel grafico $x=a=0.9$ rad: $\sin x$ = altezza di $B$, $\tan x$ = altezza di $D$ (segmento $AD$ sulla tangente $x=1$).

*Dimostrazione (geometrica, $0<x<\frac\pi2$).* Nella circonferenza goniometrica, siano $A=(1,0)$ e $B$ il punto di angolo $x$. Confronto tre aree (triangolo $OAB$ ⊂ settore circolare $OAB$ ⊂ triangolo $OAD$):
$$
\underbrace{\text{Area}(\triangle OAB)}_{\frac{\sin x}{2}}<\underbrace{\text{Area(settore }OAB)}_{\frac x2}<\underbrace{\text{Area}(\triangle OAD)}_{\frac{\tan x}{2}}
$$
dove $D$ è l'intersezione della retta $OB$ con la tangente in $A$. Moltiplicando per $2$: $\sin x<x<\tan x$. Poiché $0<x<\frac\pi2$, $\sin x>0$ e si può dividere:
$$
1<\frac{x}{\sin x}<\frac1{\cos x}\iff\cos x<\frac{\sin x}{x}<1
$$
(i reciproci invertono le disuguaglianze perché tutti i termini sono positivi). Poiché $\cos x$, $\sin x$ e $x$ sono rispettivamente pari, dispari, dispari, il rapporto $\frac{\sin x}{x}$ è **pari**: la disuguaglianza vale anche su $\left(-\frac\pi2,0\right)$. ∎

### (d) Limiti con seno e coseno

Sia $a_n\to0$, $a_n\ne0$.

**1.** $\sin a_n\to0$.
*Dim.* Da $|\sin x|\le|x|$ (conseguenza di $\frac{\sin x}{x}<1$): $0\le|\sin a_n|\le|a_n|\to0$, carabinieri. ∎

**2.** $\cos a_n\to1$.
*Dim.* Definitivamente $\cos a_n>0$ (permanenza del segno, perché $a_n\to0$ e $\cos$ è continua in $0$ con valore $1$) e $\cos a_n\le1$. Allora $1-\cos a_n\ge0$ e
$$
1-\cos a_n=\frac{(1-\cos a_n)(1+\cos a_n)}{1+\cos a_n}=\frac{\sin^2a_n}{1+\cos a_n}\le\sin^2a_n ,
$$
dato che $1+\cos a_n>1$. Inoltre $\sin^2a_n=\sin a_n\cdot\sin a_n\to0\cdot0=0$. Per i due carabinieri $0\le1-\cos a_n\le\sin^2a_n\to0$, quindi $\cos a_n\to1$. ∎

**3.** $\displaystyle\frac{\sin a_n}{a_n}\to1$.
*Dim.* Dalla disuguaglianza fondamentale $\cos a_n<\frac{\sin a_n}{a_n}<1$, con $\cos a_n\to1$ per il punto 2: carabinieri. ∎

**4.** $\displaystyle\frac{1-\cos a_n}{a_n^2}\to\frac12$.
*Dim.* Moltiplico e divido per $1+\cos a_n$:
$$
\frac{1-\cos a_n}{a_n^2}=\frac{\sin^2a_n}{a_n^2}\cdot\frac{1}{1+\cos a_n}=\left(\frac{\sin a_n}{a_n}\right)^2\cdot\frac1{1+\cos a_n}\to1^2\cdot\frac12=\frac12 . ∎
$$

### (e) Limiti con esponenziale e logaritmo

Sia $a_n\to0$, $a_n\ne0$.

**1.** $\displaystyle(1+a_n)^{1/a_n}\to e$.
*Dim.* Pongo $b_n:=\frac1{a_n}\to\pm\infty$. Allora $(1+a_n)^{1/a_n}=\left(1+\frac1{b_n}\right)^{b_n}\to e$ per (c) con $\alpha=1$. ∎

**2.** $\displaystyle\frac{\log(1+a_n)}{a_n}\to1$.
*Dim.* $\dfrac{\log(1+a_n)}{a_n}=\log\left[(1+a_n)^{1/a_n}\right]\to\log e=1$ (continuità del logaritmo). ∎

**3.** $\displaystyle\frac{e^{a_n}-1}{a_n}\to1$.
*Dim.* Pongo $b_n:=e^{a_n}-1\to0$ (e $b_n\neq0$). Allora $a_n=\log(1+b_n)$ e
$$
\frac{e^{a_n}-1}{a_n}=\frac{b_n}{\log(1+b_n)}=\frac{1}{\frac{\log(1+b_n)}{b_n}}\to\frac11=1
$$
per il punto 2 applicato a $b_n$. ∎

**4.** $\displaystyle\frac{(1+a_n)^\alpha-1}{a_n}\to\alpha$, $\alpha\in\mathbb{R}$.
*Dim.* $(1+a_n)^\alpha=e^{\alpha\log(1+a_n)}$. Con $t_n:=\alpha\log(1+a_n)\to0$:
$$
\frac{(1+a_n)^\alpha-1}{a_n}=\frac{e^{t_n}-1}{t_n}\cdot\frac{t_n}{a_n}=\frac{e^{t_n}-1}{t_n}\cdot\alpha\frac{\log(1+a_n)}{a_n}\to1\cdot\alpha\cdot1=\alpha .
$$
(Se $\alpha=0$ il limite è banalmente $0$.) ∎

### (f) Rapporto tra polinomi

Siano
$$
P(n)=a_kn^k+\dots+a_0\ (a_k\ne0),\qquad Q(n)=b_hn^h+\dots+b_0\ (b_h\ne0).
$$
Per $k,h\ge1$ il limite $\frac{P(n)}{Q(n)}$ è in generale una FI $\frac{\pm\infty}{\pm\infty}$. Si **raccoglie il monomio di grado massimo** a numeratore e denominatore:
$$
\frac{P(n)}{Q(n)}=\frac{n^k\left(a_k+a_{k-1}\frac1n+\dots+\frac{a_0}{n^k}\right)}{n^h\left(b_h+b_{h-1}\frac1n+\dots+\frac{b_0}{n^h}\right)}
=n^{k-h}\cdot\frac{a_k+o(1)}{b_h+o(1)} .
$$
Il comportamento è dominato da $n^{k-h}\frac{a_k}{b_h}$:
$$
\lim_{n\to\infty}\frac{P(n)}{Q(n)}=\begin{cases}+\infty & k>h,\ \ \frac{a_k}{b_h}>0\\ -\infty & k>h,\ \ \frac{a_k}{b_h}<0\\ \dfrac{a_k}{b_h} & k=h\\ 0 & k<h\end{cases}
$$
**Esempio.**
$$
\lim_{n\to\infty}\frac{n^5+n^4-2n^2}{-2n^3-n^2-2n}:\quad k=5>h=3,\ \ \frac{a_k}{b_h}=\frac{1}{-2}<0\ \Rightarrow\ -\infty .
$$

### Criterio del rapporto

**Teorema.** Sia $a_n>0$ e $b_n:=\dfrac{a_{n+1}}{a_n}$. Se $b_n\to b<1$, allora $a_n\to0$.

*Idea della dimostrazione.* Sia $b<q<1$. Definitivamente $\frac{a_{n+1}}{a_n}<q$, quindi per $n>\nu$: $a_n<q^{n-\nu}a_\nu=C\,q^n$ con $C=a_\nu q^{-\nu}$. Poiché $q^n\to0$ per (a), per carabinieri $a_n\to0$. ∎

### (g) Gerarchia degli infiniti: potenza, esponenziale, fattoriale

**1.** $\displaystyle\lim_{n\to\infty}\frac{n^b}{\alpha^n}=0$, $b>0$, $\alpha>1$ (FI $\frac\infty\infty$).
*Dim.* Con $a_n=\frac{n^b}{\alpha^n}$:
$$
\frac{a_{n+1}}{a_n}=\frac{(n+1)^b}{\alpha^{n+1}}\cdot\frac{\alpha^n}{n^b}=\left(1+\frac1n\right)^b\frac1\alpha\to\frac1\alpha<1 ,
$$
quindi $a_n\to0$ per il criterio del rapporto. ∎

**2.** $\displaystyle\lim_{n\to\infty}\frac{\alpha^n}{n!}=0$, $\alpha>1$.
*Dim.* $a_n=\frac{\alpha^n}{n!}$:
$$
\frac{a_{n+1}}{a_n}=\frac{\alpha^{n+1}}{(n+1)!}\cdot\frac{n!}{\alpha^n}=\frac{\alpha}{n+1}\to0<1 .
$$
(Nelle note a mano compare $\frac{1}{\alpha(n+1)}$: è un refuso, il rapporto corretto è $\frac{\alpha}{n+1}$; la conclusione non cambia.) ∎

**3.** $\displaystyle\lim_{n\to\infty}\frac{n!}{n^n}=0$.
*Dim.* $a_n=\frac{n!}{n^n}$:
$$
\frac{a_{n+1}}{a_n}=\frac{(n+1)!}{(n+1)^{n+1}}\cdot\frac{n^n}{n!}=\frac{(n+1)\,n^n}{(n+1)^{n+1}}=\left(\frac{n}{n+1}\right)^n=\frac{1}{\left(1+\frac1n\right)^n}\to\frac1e<1 . ∎
$$

### (h) Logaritmo contro potenza

Sia $a>1$, $b>0$. Allora $\displaystyle\lim_{n\to\infty}\frac{\log_an}{n^b}=0$.

*Dimostrazione.*
1. **Lemma:** $2^x>x\ \ \forall x>0$. Infatti, con $[x]$ parte intera, $2^x\ge2^{[x]}=(1+1)^{[x]}\ge1+[x]>x$ (Bernoulli e definizione di parte intera).
2. Applico $\log_a$ (crescente perché $a>1$): $\log_ax<x\log_a2$ per ogni $x>0$.
3. Scelgo $x=n^{b/2}$:
$$
\frac b2\log_an=\log_a\left(n^{b/2}\right)<n^{b/2}\log_a2\ \Rightarrow\ \log_an<\frac2b\log_a2\cdot n^{b/2} .
$$
4. Divido per $n^b>0$:
$$
0<\frac{\log_an}{n^b}<\frac2b\log_a2\cdot\frac{n^{b/2}}{n^b}=\frac2b\log_a2\cdot\frac1{n^{b/2}}\xrightarrow[n\to\infty]{}0 .
$$
Per i due carabinieri $\dfrac{\log_an}{n^b}\to0$. ∎

## Riepilogo: scala degli infiniti

$$
\log_an\ \ll\ n^b\ \ll\ \alpha^n\ \ll\ n!\ \ll\ n^n\qquad(a,\alpha>1,\ b>0)
$$
dove $x_n\ll y_n$ significa $\dfrac{x_n}{y_n}\to0$.

---

## Collegamenti

- [[Algebra dei limiti e teoremi sui limiti]]
- [[Limiti di successioni]]
- [[Successioni]]
- [[Estremo superiore ed estremo inferiore, completezza di ℝ]]
