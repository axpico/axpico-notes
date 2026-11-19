---
tags:
  - geometria-algebra-lineare
  - prodotto-scalare
  - spazi-euclidei
  - ortogonalita
  - basi-ortonormali
---
# Prodotti scalari, spazi euclidei e basi ortonormali

Fonte: Lezione 11 (PDF "Prodotti scalari…", 57 pp.). Testo: ALG (Mauri–Schlesinger) cap. 7 §§2–4, pp. 348–367.
Prerequisito: [[Spazi vettoriali e sottospazi]], [[Basi, dimensione e coordinate]], [[Dipendenza lineare]]. Per il caso geometrico di $\mathbb R^2,\mathbb R^3$ vedi anche [[Vettori geometrici liberi]] e [[Ortogonalità e fasci di rette e piani]]; per il complemento ortogonale vedi [[Intersezione, somma e somma diretta di sottospazi — formula di Grassmann]].

## 1. Forme bilineari (pp. 2–5)

Il **prodotto cartesiano** di due insiemi $X,Y$ è $X\times Y:=\{(x,y):x\in X,\,y\in Y\}$, l'insieme delle coppie ordinate. Esempi: $\mathbb R\times\mathbb R=\mathbb R^2$; $[0,1]\times[0,2]=\{(x,y)\in\mathbb R^2: 0\le x\le 1,\ 0\le y\le 2\}$ è un rettangolo del piano.

> [!important] Definizione (forma bilineare)
> Sia $V$ uno spazio vettoriale su $\mathbb R$. Una **forma bilineare** su $V$ è una mappa $L:V\times V\to\mathbb R$ tale che, per ogni $\underline v_0\in V$ fissato, le due mappe $V\to\mathbb R$
> $$L_1(\underline v):=L(\underline v,\underline v_0),\qquad L_2(\underline v):=L(\underline v_0,\underline v)$$
> sono **lineari**. In parole: $L$ è lineare in ciascuno dei due argomenti, tenendo fermo l'altro.

Conseguenza della linearità: $L(\underline 0,\underline v)=L(\underline v,\underline 0)=0$ per ogni $\underline v$; in particolare $L(\underline 0,\underline 0)=0$ (p. 8).

> [!example] Esempio 1 (p. 4–5): il determinante $2\times2$
> $L\!\left(\begin{bmatrix}x_1\\x_2\end{bmatrix},\begin{bmatrix}y_1\\y_2\end{bmatrix}\right):=\det\begin{bmatrix}x_1&y_1\\x_2&y_2\end{bmatrix}=x_1y_2-x_2y_1$ è bilineare. Verifica sul primo argomento:
> $$L(\alpha\underline x'+\beta\underline x'',\underline y)=(\alpha x_1'+\beta x_1'')y_2-(\alpha x_2'+\beta x_2'')y_1=\alpha L(\underline x',\underline y)+\beta L(\underline x'',\underline y).$$
> Con un argomento analogo si vede la linearità nel secondo argomento.

> [!example] Esempio 2 (pp. 5–6): il prodotto scalare standard di $\mathbb R^n$
> $\langle\underline x,\underline y\rangle=\sum_{i=1}^n x_iy_i$ è una forma bilineare. In più:
> - è **simmetrica**: $\langle\underline x,\underline y\rangle=\langle\underline y,\underline x\rangle$;
> - è **definita positiva**: $\langle\underline x,\underline x\rangle=\sum x_i^2\ge0$, con uguaglianza solo per $\underline x=\underline 0$.

## 2. Prodotto scalare e spazio euclideo (pp. 7–17)

> [!important] Definizione (prodotto scalare = prodotto interno)
> In uno spazio vettoriale $V$ su $\mathbb R$ (non necessariamente $\mathbb R^n$) un **prodotto scalare** è una forma bilineare $L:V\times V\to\mathbb R$ che soddisfa:
> 1. **simmetria**: $L(\underline u,\underline v)=L(\underline v,\underline u)$ per ogni $\underline u,\underline v\in V$;
> 2. **definita positività**: $L(\underline v,\underline v)\ge0$ per ogni $\underline v$, e $L(\underline v,\underline v)=0$ solo se $\underline v=\underline 0$.

> [!important] Definizione (spazio euclideo)
> Uno **spazio euclideo** è uno spazio vettoriale $V$ su $\mathbb R$ dotato di un prodotto scalare, cioè una coppia ordinata $(V,L)$. Se il prodotto è chiaro dal contesto si scrive solo $V$ e si indica il prodotto con $\langle\cdot,\cdot\rangle$. Lo stesso simbolo indica prodotti diversi in spazi diversi.

Per mostrare che una forma bilineare simmetrica **non** è un prodotto scalare basta un vettore $\underline x\ne\underline 0$ con $L(\underline x,\underline x)\le 0$.

> [!example] Esempi e controesempi (pp. 8–13)
> 1. $\det[\underline x\,|\,\underline y]$ **non** è un prodotto scalare: non è simmetrica ($L(\underline x,\underline y)=-L(\underline y,\underline x)$).
> 2. $L=\sum x_iy_i$ in $\mathbb R^n$: è un prodotto scalare.
> 3. $L(\underline x,\underline y)=x_1y_1+x_2y_2+\tfrac12(x_1y_2+x_2y_1)$ in $\mathbb R^2$ **è** un prodotto scalare. Bilineare e simmetrica sono chiare; per la positività
>    $$L(\underline x,\underline x)=x_1^2+x_2^2+x_1x_2.$$
>    Se $\underline x=(0,x_2)$, $x_2\ne0$: vale $x_2^2>0$. Se $x_1\ne0$: $L(\underline x,\underline x)=x_1^2(t^2+t+1)$ con $t=x_2/x_1$, e $t^2+t+1>0$ per ogni $t\in\mathbb R$ (discriminante negativo).
> 4. $L(\underline x,\underline y)=x_1y_1+x_2y_2+3(x_1y_2+x_2y_1)$ è bilineare simmetrica ma **non** definita positiva: $L\big((1,1),(1,1)\big)=8>0$ però $L\big((1,-1),(1,-1)\big)=-4<0$.
> 5. $L(\underline x,\underline y)=x_1y_1+x_2y_2+(x_1y_2+x_2y_1)$ è bilineare simmetrica e $L(\underline x,\underline x)=(x_1+x_2)^2\ge0$, ma **non** è definita positiva: $L\big((1,-1),(1,-1)\big)=0$ con $(1,-1)\neq\underline 0$.

> [!warning] Semidefinita non basta
> Nell'esempio 5 si ha $L(\underline x,\underline x)\ge0$ sempre, ma la condizione "$=0$ solo per $\underline x=\underline 0$" cade. Quando si controlla la definita positività bisogna sempre cercare un vettore non nullo che dia $0$ (o un valore negativo).

**Spazi euclidei di dimensione infinita (pp. 12–16).**
- $L^2[a,b]:=\{f:[a,b]\to\mathbb R\ \text{a quadrato integrabili}\}$, cioè $\int_a^b|f(x)|^2dx$ esiste ed è finito. Dall'analisi: se $f,g\in L^2[a,b]$ allora $fg$ è integrabile, e
  $$\langle f,g\rangle:=\int_a^b f(x)g(x)\,dx$$
  è un prodotto scalare. Quindi $L^2[a,b]$ è uno spazio euclideo di dimensione $\infty$.
- **Ogni sottospazio** di uno spazio euclideo è a sua volta euclideo, con il prodotto scalare ereditato. Esempio: $P_n=\{\text{polinomi di grado}\le n\}$ è sottospazio di $L^2[a,b]$, quindi euclideo con $\langle p,q\rangle=\int_a^b p\,q\,dx$. Per valori diversi di $a,b$ si ottengono prodotti scalari **diversi** su $P_n$.

> [!note] Spazi hermitiani (p. 17)
> Su $\mathbb K=\mathbb C$ l'analogo degli spazi euclidei è lo **spazio hermitiano**: teoria simile ma con molte differenze di dettaglio. Nel corso si trattano solo spazi euclidei.

## 3. Norma, distanza e le sue proprietà (pp. 17–21)

Il prodotto scalare permette di introdurre in uno spazio vettoriale concetti geometrici (lunghezza, angolo).

> [!important] Definizione (norma)
> In uno spazio euclideo $V$ la **norma** di $\underline v\in V$ è
> $$\|\underline v\|:=\sqrt{\langle\underline v,\underline v\rangle}.$$
> Interpretazione geometrica: **lunghezza** del vettore. In $\mathbb R^2$ col prodotto standard, $\underline x=(x,y)$: $\|\underline x\|=\sqrt{x^2+y^2}$.
> La **distanza** tra $\underline u,\underline v$ è $\mathrm{dist}(\underline u,\underline v):=\|\underline v-\underline u\|$. In $\mathbb R^2$, con $\underline u=(x_1,y_1)$, $\underline v=(x_2,y_2)$, si ritrova $\sqrt{(x_2-x_1)^2+(y_2-y_1)^2}$, la distanza tra i due punti.

> [!important] Proprietà della norma (pp. 20–21)
> Valgono, per ogni $\underline u,\underline v\in V$, $\alpha\in\mathbb R$:
> 1. **definita positività**: $\|\underline v\|\ge0$ e $\|\underline v\|=0\iff\underline v=\underline 0$;
> 2. **omogeneità**: $\|\alpha\underline v\|=|\alpha|\,\|\underline v\|$; in particolare $\|-\underline v\|=\|\underline v\|$;
> 3. **disuguaglianza triangolare**: $\|\underline u\pm\underline v\|\le\|\underline u\|+\|\underline v\|$ (dimostrata in §7).

*Perché l'omogeneità:* $\|\alpha\underline v\|=\sqrt{\langle\alpha\underline v,\alpha\underline v\rangle}=\sqrt{\alpha^2\langle\underline v,\underline v\rangle}=|\alpha|\sqrt{\langle\underline v,\underline v\rangle}$.

> [!warning] Modulo del coefficiente
> Il coefficiente esce dalla norma **in valore assoluto**: $\|-3\underline v\|=3\|\underline v\|$, non $-3\|\underline v\|$. Inoltre la norma dipende dal prodotto scalare scelto: lo stesso vettore può avere norme diverse in prodotti diversi.

## 4. Ortogonalità, Carnot e Pitagora (pp. 22–26)

> [!important] Definizione (ortogonalità)
> Due vettori $\underline v,\underline u$ di uno spazio euclideo sono **ortogonali**, $\underline v\perp\underline u$, se $\langle\underline v,\underline u\rangle=0$.
> Il vettore nullo $\underline 0$ è ortogonale a ogni vettore.

> [!important] Teorema 1 (Carnot e Pitagora)
> Sia $V$ euclideo e $\underline u,\underline v\in V$. Allora
> - (i) **Carnot**: $\|\underline u+\underline v\|^2=\|\underline u\|^2+\|\underline v\|^2+2\langle\underline u,\underline v\rangle$;
> - (ii) **Pitagora**: se $\underline u\perp\underline v$, allora $\|\underline u+\underline v\|^2=\|\underline u\|^2+\|\underline v\|^2$.

*Dimostrazione.* (i) Per la bilinearità, prima nel primo e poi nel secondo argomento:
$$\|\underline u+\underline v\|^2=\langle\underline u+\underline v,\underline u+\underline v\rangle=\langle\underline u,\underline u\rangle+\langle\underline u,\underline v\rangle+\langle\underline v,\underline u\rangle+\langle\underline v,\underline v\rangle.$$
Per la simmetria $\langle\underline v,\underline u\rangle=\langle\underline u,\underline v\rangle$, e per definizione di norma si ottiene $\|\underline u\|^2+2\langle\underline u,\underline v\rangle+\|\underline v\|^2$. (ii) Se $\underline u\perp\underline v$ allora $\langle\underline u,\underline v\rangle=0$ e Carnot dà Pitagora. $\blacksquare$

**Perché sono generalizzazioni dei teoremi classici (pp. 24–26).**
- Triangolo rettangolo con cateti $\vec u,\vec v$ e ipotenusa $\vec u+\vec v$: $a=\|\vec u\|$, $b=\|\vec v\|$, $c=\|\vec u+\vec v\|$, e (ii) dà $c^2=a^2+b^2$.
- Triangolo qualsiasi con lati $\vec u,\vec v$ che formano l'angolo $\alpha$ e terzo lato $\vec v-\vec u=(-\vec u)+\vec v$: Carnot dà
  $$c^2=\|\vec u\|^2+\|\vec v\|^2-2\langle\vec u,\vec v\rangle=a^2+b^2-2ab\cos\alpha,$$
  cioè il **teorema del coseno**, usando che nel piano $\langle\vec u,\vec v\rangle=\|\vec u\|\,\|\vec v\|\cos\alpha$.

> [!warning] Segno nel termine misto
> Carnot per la somma ha $+2\langle\underline u,\underline v\rangle$; per la differenza si sostituisce $\underline v\to-\underline v$ e il segno diventa $-$: $\|\underline u-\underline v\|^2=\|\underline u\|^2+\|\underline v\|^2-2\langle\underline u,\underline v\rangle$. Pitagora vale solo con $\underline u\perp\underline v$; il viceversa vale **per $\|\underline u+\underline v\|$**: se $\|\underline u+\underline v\|^2=\|\underline u\|^2+\|\underline v\|^2$, da Carnot segue $\langle\underline u,\underline v\rangle=0$.

## 5. Proiezione ortogonale su una retta (pp. 26–32)

Sia $W\subseteq V$ sottospazio con $\dim W=1$, $\underline w\ne\underline 0$ in $W$ (quindi $W=\mathrm{span}\{\underline w\}$) e $\underline v\in V\setminus W$.

**Problema:** trovare $\underline v_0\in W$ più vicino a $\underline v$, cioè minimizzare $\|\underline v-\underline v_0\|$ al variare di $\underline v_0\in W$.

**Soluzione.** $\underline v_0\in W\iff\underline v_0=t\underline w$. Per Carnot
$$\|\underline v-t\underline w\|^2=\|\underline v\|^2+\|t\underline w\|^2-2t\langle\underline v,\underline w\rangle=\|\underline v\|^2+\|\underline w\|^2t^2-2\langle\underline v,\underline w\rangle t.$$
Poiché $\underline w\ne\underline 0$, $\|\underline w\|^2>0$: è un polinomio quadratico in $t$ con minimo in
$$t_0=\frac{\langle\underline v,\underline w\rangle}{\|\underline w\|^2}.$$

> [!important] Definizione (proiezione ortogonale su una retta, coefficiente di Fourier)
> $$\underline v_0=t_0\underline w=\frac{\langle\underline v,\underline w\rangle}{\|\underline w\|^2}\,\underline w$$
> è la **proiezione ortogonale** di $\underline v$ sulla retta $W$. Il numero $t_0=\dfrac{\langle\underline v,\underline w\rangle}{\|\underline w\|^2}$ è il **coefficiente di Fourier** di $\underline v$ rispetto a $\underline w$.

> [!important] Osservazione (pp. 31–32)
> Il resto $\underline v-\underline v_0$ è sempre **ortogonale a $W$**:
> $$\langle\underline v-\underline v_0,\underline w\rangle=\langle\underline v,\underline w\rangle-\frac{\langle\underline v,\underline w\rangle}{\|\underline w\|^2}\langle\underline w,\underline w\rangle=0.$$

> [!example] Esempio (pp. 29–31)
> Proiettare $\underline v=\begin{bmatrix}3\\2\end{bmatrix}$ sulla retta $y=x$. La retta passa per l'origine ed è generata da $\underline w=\begin{bmatrix}1\\1\end{bmatrix}$.
> $$t_0=\frac{3\cdot1+2\cdot1}{1^2+1^2}=\frac52,\qquad \underline v_0=\frac52\underline w=\begin{bmatrix}5/2\\5/2\end{bmatrix}.$$
> Controllo: $\underline v-\underline v_0=\begin{bmatrix}1/2\\-1/2\end{bmatrix}$ è ortogonale alla retta $y=x$ (prodotto con $\underline w$: $\tfrac12-\tfrac12=0$).

```desmos-graph
y=x
y=-x+5
```

La retta $y=x$ è $W$; la retta $y=-x+5$ è la perpendicolare per $(3,2)$: interseca $W$ nel punto $(5/2,5/2)$, la proiezione.

> [!warning] Dividere per $\|\underline w\|^2$, non per $\|\underline w\|$
> La formula ha $\|\underline w\|^2$ al denominatore (e $\underline w$ al numeratore). Dividere per $\|\underline w\|$ è corretto solo se si usa un versore: con $\|\underline w\|=1$ la formula diventa $\underline v_0=\langle\underline v,\underline w\rangle\underline w$. Un versore è un vettore di norma $1$ (p. 56).

## 6. Disuguaglianza di Cauchy–Schwarz–Bunjakovskij (pp. 33–37)

> [!important] Teorema 2 (Schwarz, o Cauchy–Schwarz–Bunjakovskij, C.S.B.)
> Per ogni $\underline v,\underline w$ di uno spazio euclideo
> $$|\langle\underline v,\underline w\rangle|\le\|\underline v\|\cdot\|\underline w\|.$$
> L'uguaglianza vale **se e solo se** $\underline v,\underline w$ sono **linearmente dipendenti**.

*Dimostrazione.*
- **Caso 1: $\underline w=\underline 0$.** Allora i due vettori sono dipendenti e $\langle\underline v,\underline w\rangle=0=\|\underline v\|\,\|\underline w\|$: vale (con uguaglianza).
- **Caso 2: $\underline w\ne\underline 0$.** Scomponiamo $\underline v=\underline v_0+\underline v_\perp$ con $\underline v_0=\frac{\langle\underline v,\underline w\rangle}{\|\underline w\|^2}\underline w\parallel\underline w$ e $\underline v_\perp=\underline v-\underline v_0\perp\underline w$ (§5). Poiché $\underline v_0\perp\underline v_\perp$, per Pitagora
  $$\|\underline v\|^2=\|\underline v_0\|^2+\|\underline v_\perp\|^2\ \ge\ \|\underline v_0\|^2\quad\Rightarrow\quad\|\underline v\|\ge\|\underline v_0\|.\tag{1}$$
  Per omogeneità
  $$\|\underline v_0\|=\frac{|\langle\underline v,\underline w\rangle|}{\|\underline w\|^2}\|\underline w\|=\frac{|\langle\underline v,\underline w\rangle|}{\|\underline w\|}\le\|\underline v\|.$$
  Moltiplicando per $\|\underline w\|>0$ si ottiene la C.S.B.
- **Uguaglianza.** Vale se e solo se vale in (1), cioè $\|\underline v_\perp\|=0$, cioè (def. positiva) $\underline v_\perp=\underline 0$, cioè $\underline v=\underline v_0\in\mathrm{span}\{\underline w\}$, cioè $\underline v,\underline w$ dipendenti. $\blacksquare$

> [!important] Definizione (angolo tra due vettori non nulli)
> $$\widehat{(\underline v,\underline w)}:=\arccos\frac{\langle\underline v,\underline w\rangle}{\|\underline v\|\cdot\|\underline w\|}\in[0,\pi].$$
> La C.S.B. garantisce che l'argomento dell'$\arccos$ sta in $[-1,1]$, quindi la definizione ha senso. Segue che $\underline v\perp\underline w\iff$ angolo $=\pi/2$ (per vettori non nulli).

> [!warning] Servono vettori non nulli
> L'angolo è definito solo per $\underline v,\underline w\ne\underline 0$ (altrimenti si divide per $0$). Inoltre vale $\langle\underline v,\underline w\rangle=\pm\|\underline v\|\|\underline w\|$ (angolo $0$ o $\pi$) **se e solo se** i vettori sono paralleli.

## 7. Dimostrazione della disuguaglianza triangolare (pp. 38–39)

Per Carnot e poi C.S.B. ($\langle\underline u,\underline v\rangle\le\|\underline u\|\|\underline v\|$):
$$\|\underline u+\underline v\|^2=\|\underline u\|^2+\|\underline v\|^2+2\langle\underline u,\underline v\rangle\le\|\underline u\|^2+\|\underline v\|^2+2\|\underline u\|\|\underline v\|=(\|\underline u\|+\|\underline v\|)^2.$$
Poiché le norme sono $\ge0$, estraendo la radice: $\|\underline u+\underline v\|\le\|\underline u\|+\|\underline v\|$.
Versione con la differenza: $\|\underline u-\underline v\|=\|\underline u+(-\underline v)\|\le\|\underline u\|+\|-\underline v\|=\|\underline u\|+\|\underline v\|$.

## 8. Sistemi ortogonali e indipendenza lineare (pp. 39–43)

> [!important] Definizione (sistema ortogonale)
> Un sistema $S=\{\underline v_1,\dots,\underline v_k\}$ in uno spazio euclideo è **ortogonale** se $\underline v_i\perp\underline v_j$ per ogni $i\ne j$.

> [!important] Teorema 3 (indipendenza lineare di un sistema ortogonale)
> Ogni sistema ortogonale composto da vettori **non nulli** è linearmente indipendente.

*Dimostrazione.* Per assurdo sia $S$ dipendente: esiste $\underline c\ne\underline 0$ con $\sum_{i=1}^k c_i\underline v_i=\underline 0$ (3). Sia $c_j\ne0$. Facendo il prodotto scalare di (3) con $\underline v_j$: da un lato $\langle\underline 0,\underline v_j\rangle=0$; dall'altro, per linearità e ortogonalità, $\sum_i c_i\langle\underline v_i,\underline v_j\rangle=c_j\|\underline v_j\|^2$. Dunque $c_j\|\underline v_j\|^2=0$ con $c_j\ne0$, quindi $\underline v_j=\underline 0$: contraddizione con l'ipotesi di vettori non nulli. $\blacksquare$

> [!important] Corollario
> Se $\dim V=n$, ogni sistema ortogonale di $n$ vettori **non nulli** è una **base** di $V$.
> (Basta ricordare che $n$ vettori indipendenti in uno spazio di dimensione $n$ sono una base: criterio di una base, Teorema 2 di Lezione 5. Vedi [[Basi, dimensione e coordinate]].)

> [!warning] Non nulli, e il numero giusto
> Se un vettore del sistema è nullo, il sistema è ortogonale ma dipendente. E un sistema ortogonale con **meno** di $n$ vettori non è una base: è solo indipendente e può essere completato (vedi [[Completamento a base]]).

> [!example] Esempi (pp. 45–48)
> - In $\mathbb R^4$: $\underline v_1=(1,2,0,0)$, $\underline v_2=(2,-1,1,-1)$, $\underline v_3=(0,0,1,1)$. I tre prodotti: $\langle\underline v_1,\underline v_2\rangle=2-2+0+0=0$, $\langle\underline v_1,\underline v_3\rangle=0$, $\langle\underline v_2,\underline v_3\rangle=0+0+1-1=0$. Sistema ortogonale (quindi indipendente), ma **non base** di $\mathbb R^4$: servirebbero $4$ vettori.
> - In $L^2[0,2\pi]$: $f_1=\sin x$, $f_2=\sin2x$, $f_3=\sin3x$ sono ortogonali; ad esempio, con la formula di prostaferesi $\sin x\sin2x=\tfrac12(\cos x-\cos3x)$,
>   $$\langle f_1,f_2\rangle=\int_0^{2\pi}\tfrac12(\cos x-\cos3x)\,dx=0,$$
>   analogamente $\langle f_1,f_3\rangle=\int_0^{2\pi}\tfrac12(\cos2x-\cos4x)dx=0$ e $\langle f_2,f_3\rangle=\int_0^{2\pi}\tfrac12(\cos x-\cos5x)dx=0$. In particolare sono linearmente indipendenti.

## 9. Basi ortogonali e ortonormali (pp. 43–49)

> [!important] Definizione (base ortogonale, base ortonormale)
> Una base $\mathcal B=\{\underline v_1,\dots,\underline v_n\}$ di uno spazio euclideo è **ortogonale** se è un sistema ortogonale ($\underline v_i\perp\underline v_j$ per $i\ne j$). È **ortonormale** se inoltre $\|\underline v_i\|=1$ per ogni $i$; equivalentemente
> $$\langle\underline v_i,\underline v_j\rangle=\begin{cases}0&i\ne j,\\1&i=j.\end{cases}$$

Esempio: la base canonica di $\mathbb R^n$ col prodotto standard è ortonormale.

**Normalizzazione (p. 45).** Se $\mathcal B$ è ortogonale, ponendo $\underline u_i:=\frac1{\|\underline v_i\|}\underline v_i$ si ottiene una base **ortonormale** $\tilde{\mathcal B}=\{\underline u_1,\dots,\underline u_n\}$ (si divide ogni vettore per la propria norma).

> [!example] Esempio svolto (pp. 48–49)
> In $\mathbb R^3$: $\underline v_1=(2,1,1)$, $\underline v_2=(-1,1,1)$, $\underline v_3=(0,-1,1)$.
> - Sono $3$ vettori non nulli e $\langle\underline v_1,\underline v_2\rangle=-2+1+1=0$, $\langle\underline v_1,\underline v_3\rangle=0-1+1=0$, $\langle\underline v_2,\underline v_3\rangle=0-1+1=0$. Essendo $\dim\mathbb R^3=3$, per il Corollario è una **base ortogonale**.
> - Norme: $\|\underline v_1\|=\sqrt6$, $\|\underline v_2\|=\sqrt3$, $\|\underline v_3\|=\sqrt2$. Normalizzando:
> $$\underline u_1=\begin{bmatrix}\sqrt6/3\\ \sqrt6/6\\ \sqrt6/6\end{bmatrix},\quad \underline u_2=\begin{bmatrix}-\sqrt3/3\\ \sqrt3/3\\ \sqrt3/3\end{bmatrix},\quad \underline u_3=\begin{bmatrix}0\\ -\sqrt2/2\\ \sqrt2/2\end{bmatrix}$$
> formano una base **ortonormale** di $\mathbb R^3$.

> [!warning] Ortogonale non è ortonormale
> $\{\underline v_i\}$ ortogonale richiede solo prodotti nulli; per l'ortonormalità servono anche norme $=1$. Trappola tipica: dimenticare di normalizzare, oppure normalizzare con $\|\underline v\|^2$ invece di $\|\underline v\|$.

## 10. Coordinate rispetto a una base ortogonale (pp. 50–56)

Vantaggio enorme delle basi ortogonali: le coordinate si trovano **senza risolvere un sistema lineare**. Questo conta per spazi di dimensione grande (esempio citato: la compressione MP3 passa dalla base canonica di $\mathbb R^n$, tipicamente $n=576$, a un'altra base utile per l'analisi psicoacustica; la nuova base è ortogonale).

> [!important] Teorema 4 (coordinate rispetto a una base ortogonale)
> Sia $\mathcal B=\{\underline v_1,\dots,\underline v_n\}$ una base ortogonale di $V$ euclideo. Le coordinate $\underline c=(c_1,\dots,c_n)$ di $\underline v\in V$ rispetto a $\mathcal B$ coincidono con i **coefficienti di Fourier** di $\underline v$ rispetto a $\underline v_1,\dots,\underline v_n$:
> $$c_i=\frac{\langle\underline v,\underline v_i\rangle}{\|\underline v_i\|^2}.$$
> Se $\mathcal B$ è **ortonormale**, la formula si semplifica in $c_j=\langle\underline v,\underline v_j\rangle$.

*Dimostrazione.* Sia $\underline v=\sum_{i=1}^nc_i\underline v_i$. Per ogni $j$,
$$\langle\underline v,\underline v_j\rangle=\Big\langle\sum_ic_i\underline v_i,\underline v_j\Big\rangle=\sum_ic_i\langle\underline v_i,\underline v_j\rangle=c_j\|\underline v_j\|^2,$$
perché l'unico termine non nullo è $i=j$ (ortogonalità). Gli elementi di una base sono non nulli, quindi $\|\underline v_j\|\ne0$ e si può dividere: $c_j=\langle\underline v,\underline v_j\rangle/\|\underline v_j\|^2$. $\blacksquare$

> [!example] Esempio svolto (pp. 55–56)
> In $\mathbb R^2$, base ortonormale $\mathcal B=\left\{\begin{bmatrix}\sqrt2/2\\ \sqrt2/2\end{bmatrix},\begin{bmatrix}\sqrt2/2\\ -\sqrt2/2\end{bmatrix}\right\}$, vettore $\underline x=\begin{bmatrix}3\\2\end{bmatrix}$. Base ortonormale, quindi $c_j=\langle\underline x,\underline v_j\rangle$:
> $$c_1=3\tfrac{\sqrt2}2+2\tfrac{\sqrt2}2=\frac{5\sqrt2}2,\qquad c_2=3\tfrac{\sqrt2}2-2\tfrac{\sqrt2}2=\frac{\sqrt2}2.$$
> Verifica: $\frac{5\sqrt2}2\begin{bmatrix}\sqrt2/2\\ \sqrt2/2\end{bmatrix}+\frac{\sqrt2}2\begin{bmatrix}\sqrt2/2\\ -\sqrt2/2\end{bmatrix}=\begin{bmatrix}5/2\\5/2\end{bmatrix}+\begin{bmatrix}1/2\\-1/2\end{bmatrix}=\begin{bmatrix}3\\2\end{bmatrix}$.
> Si noti il legame con §5: $\tfrac52(1,1)$ è proprio la proiezione di $(3,2)$ sulla retta $y=x$. Il confronto con il metodo generale [[Cambio di base e matrice di passaggio]] mostra il risparmio: niente matrice inversa.

> [!warning] Formula solo per basi ortogonali
> $c_i=\langle\underline v,\underline v_i\rangle/\|\underline v_i\|^2$ **non** vale per una base qualsiasi: se i vettori non sono ortogonali tra loro i termini $i\ne j$ non si annullano e si deve risolvere il sistema. Inoltre, con base ortogonale non normalizzata, non dimenticare il denominatore $\|\underline v_i\|^2$.

## 11. Riepilogo per l'esame

**Cosa saper dimostrare:** Carnot e Pitagora (bilinearità + simmetria), C.S.B. (proiezione + Pitagora, con caso di uguaglianza), disuguaglianza triangolare (Carnot + C.S.B.), indipendenza di un sistema ortogonale (prodotto con $\underline v_j$), formula delle coordinate (idem).

**Formule da ricordare.**
| Cosa | Formula |
|---|---|
| Norma | $\|\underline v\|=\sqrt{\langle\underline v,\underline v\rangle}$ |
| Distanza | $\|\underline v-\underline u\|$ |
| Carnot | $\|\underline u+\underline v\|^2=\|\underline u\|^2+\|\underline v\|^2+2\langle\underline u,\underline v\rangle$ |
| C.S.B. | $\lvert\langle\underline v,\underline w\rangle\rvert\le\|\underline v\|\|\underline w\|$ |
| Angolo | $\arccos\dfrac{\langle\underline v,\underline w\rangle}{\|\underline v\|\|\underline w\|}$ |
| Proiezione su $\underline w$ | $\dfrac{\langle\underline v,\underline w\rangle}{\|\underline w\|^2}\underline w$ |
| Coordinate in base ortogonale | $c_i=\dfrac{\langle\underline v,\underline v_i\rangle}{\|\underline v_i\|^2}$ (ortonormale: $\langle\underline v,\underline v_i\rangle$) |

**Procedure rapide.**
1. *"È un prodotto scalare?"* Controlla bilinearità, simmetria (scambia $x\leftrightarrow y$), definita positività: calcola $L(\underline x,\underline x)$; riscrivilo come somma di quadrati o cerca un controesempio con $\underline x\ne\underline 0$ che dia $\le0$.
2. *"È una base ortogonale/ortonormale?"* Conta i vettori ($=\dim V$), controlla che siano non nulli e a due a due ortogonali (tutte le coppie), poi le norme per l'ortonormalità.
3. *"Normalizza una base ortogonale."* $\underline u_i=\underline v_i/\|\underline v_i\|$.
4. *"Coordinate in base ortogonale."* Un prodotto scalare e una divisione per componente; verifica ricomponendo $\sum c_i\underline v_i$.
5. *"Proiezione su una retta."* Genera la retta con $\underline w$, calcola $t_0$ e $\underline v_0=t_0\underline w$; controlla $\langle\underline v-\underline v_0,\underline w\rangle=0$.

**Trappole riassunte.** Semidefinita $\ne$ definita; l'angolo richiede vettori non nulli; ortogonale $\ne$ ortonormale; formula delle coordinate valida solo per basi ortogonali; $\|\alpha\underline v\|=|\alpha|\|\underline v\|$; nella proiezione il denominatore è $\|\underline w\|^2$.

Esercizi consigliati (p. 57): ALG §7.1, Esercizi 7.1, 7.2, 7.10 (p. 385); §7.2, Esercizi 7.11–7.17.
