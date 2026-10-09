---
tags:
  - analisi1
  - limiti-successioni
  - asintotici
  - limiti-notevoli
---
# Limiti di successioni — Esercizi

Teoria collegata: [[Limiti di successioni]], [[Algebra dei limiti e teoremi sui limiti]], [[Successioni monotone, infinitesimi e limiti notevoli]].

## Strumenti usati

**Equivalenza asintotica.** $a_n\sim b_n$ per $n\to+\infty$ se $\dfrac{a_n}{b_n}\to1$. Proprietà chiave:

- è compatibile con **prodotti, quozienti e potenze**: se $a_n\sim a_n'$ e $b_n\sim b_n'$ allora $a_nb_n\sim a_n'b_n'$ e $\frac{a_n}{b_n}\sim\frac{a_n'}{b_n'}$;
- **non** è compatibile con somme e differenze (rischio di cancellazioni: $n+1\sim n$ e $n\sim n$, ma $(n+1)-n=1\not\sim0$). In quei casi si usano sviluppi, razionalizzazione o raccoglimenti.

**Limiti notevoli** (con $\varepsilon_n\to0$):

| Limite | Equivalenza |
|---|---|
| $\dfrac{\sin\varepsilon_n}{\varepsilon_n}\to1$ | $\sin\varepsilon_n\sim\varepsilon_n$ |
| $\dfrac{\log(1+\varepsilon_n)}{\varepsilon_n}\to1$ | $\log(1+\varepsilon_n)\sim\varepsilon_n$ |
| $\dfrac{1-\cos\varepsilon_n}{\varepsilon_n^2}\to\dfrac12$ | $1-\cos\varepsilon_n\sim\frac{\varepsilon_n^2}{2}$ |
| $\dfrac{(1+\varepsilon_n)^a-1}{\varepsilon_n}\to a$ | $\sqrt{1+\varepsilon_n}-1\sim\frac{\varepsilon_n}{2}$ |
| $\left(1+\dfrac{c}{n}\right)^n\to e^c$ | forma $1^\infty$ |

**Gerarchia degli infiniti** ($n\to+\infty$, $a>1$, $\alpha>0$):
$$\log n\;\ll\;n^\alpha\;\ll\;a^n\;\ll\;n!\;\ll\;n^n$$

---

## Esercizio 1 — Forma $\frac00$ con logaritmo e seno

$$\lim_{n\to+\infty}\frac{\log\left(1+\frac{3}{n^2}\right)}{\sin\left(\frac{2}{n^2}\right)}$$

**Idea.** Sia numeratore sia denominatore sono infinitesimi (forma $\frac00$): applico i limiti notevoli. Gli argomenti $\frac3{n^2}$ e $\frac2{n^2}$ tendono a $0$, quindi i notevoli sono applicabili.

**Svolgimento.** Moltiplico e divido per gli argomenti, come sulla lavagna:
$$\frac{\log\left(1+\frac3{n^2}\right)}{\sin\left(\frac2{n^2}\right)}
=\underbrace{\frac{\log\left(1+\frac3{n^2}\right)}{\frac3{n^2}}}_{\to1}\cdot\underbrace{\frac{\frac2{n^2}}{\sin\left(\frac2{n^2}\right)}}_{\to1}\cdot\frac{\frac3{n^2}}{\frac2{n^2}}$$

L'ultimo fattore vale $\dfrac{3}{n^2}\cdot\dfrac{n^2}{2}=\dfrac32$ (costante).

$$\boxed{\dfrac32}$$

> Metodo rapido: $\log(1+\frac3{n^2})\sim\frac3{n^2}$ e $\sin\frac2{n^2}\sim\frac2{n^2}$, quindi il rapporto $\sim\frac{3/n^2}{2/n^2}=\frac32$.

---

## Esercizio 2 — Logaritmi e confronto tra infiniti

$$\lim_{n\to+\infty}\frac{\log\left(\frac1{n^5}\right)+\log\left(\sqrt n\right)}{2\log\left(n^5+n^2\right)}$$

**Idea.** Forma $\frac{-\infty}{+\infty}$. Con le proprietà dei logaritmi tutto si riduce a multipli di $\log n$. L'unico punto delicato è $\log(n^5+n^2)$: si raccoglie il termine dominante.

**Svolgimento.**

*Numeratore:*
$$\log n^{-5}+\log n^{1/2}=-5\log n+\tfrac12\log n=-\tfrac92\log n$$

*Denominatore:* raccolgo $n^5$:
$$2\log\left(n^5(1+n^{-3})\right)=2\left[5\log n+\log(1+n^{-3})\right]=10\log n+2\log(1+n^{-3})$$
Poiché $\log(1+n^{-3})\to0$ mentre $\log n\to+\infty$, il denominatore è $\sim10\log n$.

$$\frac{-\frac92\log n}{10\log n}\;\to\;\boxed{-\dfrac{9}{20}}$$

> Lettura della foto: ho interpretato l'esponente come $n^5$. Se fosse un altro esponente $k$, il risultato sarebbe $\dfrac{-k+\frac12}{10}$.

---

## Esercizio 3 — Radice $n$-esima di una torre di potenze

$$\lim_{n\to+\infty}\frac{1}{\sqrt[n]{2^{2^n}}}\left[n\log\left(\left(\frac{n+3}{n}\right)^2\right)\right]$$

**Idea.** Il limite è un prodotto di due fattori con comportamento diverso: uno converge, l'altro diverge. Si studiano separatamente.

**Svolgimento.**

*Parentesi quadra.* $\log(x^2)=2\log x$ e $\frac{n+3}{n}=1+\frac3n$:
$$n\log\left(\left(1+\tfrac3n\right)^2\right)=2n\log\left(1+\tfrac3n\right)\sim2n\cdot\frac3n=6$$

*Radice.* $\sqrt[n]{2^{2^n}}=\left(2^{2^n}\right)^{1/n}=2^{2^n/n}$. Per la gerarchia degli infiniti $\frac{2^n}{n}\to+\infty$, quindi $2^{2^n/n}\to+\infty$.

$$\frac{6}{+\infty}\to\boxed{0}$$

> Ho letto il radicando come la torre $2^{2^n}$. Se fosse $2^n$, la radice varrebbe $2$ e il limite $\frac62=3$. Controlla sulla lavagna.

---

## Esercizio 4 — Radice quadrata e seno al quadrato

$$\lim_{n\to+\infty}\frac{\sqrt{1+\sin^2\!\left(\frac{1}{n^4+1}\right)}-1}{\frac{1}{4n^8+5n^2}}$$

**Idea.** Numeratore e denominatore sono entrambi infinitesimi. Uso gli equivalenti asintotici passo a passo, dall'argomento più interno verso l'esterno.

**Svolgimento.**

1. $\frac1{n^4+1}\to0$, quindi $\sin\frac1{n^4+1}\sim\frac1{n^4+1}\sim\frac1{n^4}$.
2. Elevando al quadrato (le potenze rispettano $\sim$): $\sin^2(\cdot)\sim\frac1{n^8}=:x_n\to0$.
3. $\sqrt{1+x_n}-1\sim\frac{x_n}{2}$, quindi il numeratore $\sim\frac1{2n^8}$.
4. Denominatore: $\frac1{4n^8+5n^2}\sim\frac1{4n^8}$ (il termine di grado maggiore domina).

$$\frac{1/(2n^8)}{1/(4n^8)}=2\quad\Rightarrow\quad\boxed{2}$$

---

## Esercizio 5 (Limite 7) — Differenze di radici: razionalizzazione

$$\lim_{n\to+\infty}\frac{\sqrt{n^3-n^2-1}-\sqrt{n^3-n^2+n}}{n-\sqrt{n^2-n}}$$

**Idea.** Sia il numeratore sia il denominatore sono **differenze di quantità che divergono** ($\infty-\infty$): non si possono usare gli asintotici sulla differenza. Si **razionalizza** con $(a-b)=\dfrac{a^2-b^2}{a+b}$.

**Numeratore.**
$$\frac{(n^3-n^2-1)-(n^3-n^2+n)}{\sqrt{n^3-n^2-1}+\sqrt{n^3-n^2+n}}=\frac{-n-1}{\sqrt{n^3-n^2-1}+\sqrt{n^3-n^2+n}}$$
Il denominatore di questa frazione è $\sim2n^{3/2}$, il numeratore $\sim-n$, quindi
$$\text{Num}\sim\frac{-n}{2n^{3/2}}=-\frac1{2\sqrt n}$$

**Denominatore.**
$$\frac{n^2-(n^2-n)}{n+\sqrt{n^2-n}}=\frac{n}{n+\sqrt{n^2-n}}\sim\frac{n}{2n}\to\frac12$$

**Rapporto.**
$$\frac{-\frac1{2\sqrt n}}{\frac12}=-\frac1{\sqrt n}\to\boxed0$$

---

## Esercizio 6 (Limite 9) — Fattoriali

$$\lim_{n\to+\infty}\frac{n!\,\sqrt n\,\sin\left(\frac1n\right)}{(n+1)!-n!}$$

**Idea.** Si usa $(n+1)!=(n+1)\,n!$ per raccogliere $n!$ e semplificarlo.

**Svolgimento.**

- Denominatore: $(n+1)!-n!=n!\,(n+1-1)=n\cdot n!$.
- Numeratore: $\sin\frac1n\sim\frac1n$, quindi $\sim n!\cdot n^{1/2}\cdot n^{-1}=n!\,n^{-1/2}$.

$$\frac{n!\,n^{-1/2}}{n\cdot n!}=n^{-3/2}\to\boxed0$$

---

## Esercizio 7 (Limite 10) — Forma $1^\infty$

$$\lim_{n\to+\infty}\left(\frac{n^2+3n}{n^2+n+1}\right)^{3n}$$

**Idea.** La base tende a $1$ e l'esponente a $+\infty$: forma indeterminata $1^\infty$. Si scrive la base come $1+a_n$ con $a_n\to0$ e si usa
$$(1+a_n)^{b_n}=e^{b_n\log(1+a_n)}\sim e^{a_nb_n}\quad\text{(se }a_n\to0\text{)}.$$

**Svolgimento.**
$$\frac{n^2+3n}{n^2+n+1}=1+\frac{2n-1}{n^2+n+1}$$
$$a_nb_n=3n\cdot\frac{2n-1}{n^2+n+1}\to\frac{6n^2}{n^2}=6$$

$$\boxed{e^6}$$

---

## Esercizio 8 (Limite 11) — Radice $n$-esima di una somma

$$\lim_{n\to+\infty}\sqrt[n]{3^n+\left(1+\frac{2\log2}{n}\right)^{n^2}}$$

**Idea.** La radice $n$-esima di una somma di due termini positivi si comporta come la radice del termine dominante. Bisogna stabilire quale dei due domina, e per farlo serve capire il secondo termine, che è una forma $1^\infty$ delicata (l'esponente è $n^2$, non $n$).

**Svolgimento.** Con $\log(1+x)=x-\frac{x^2}2+o(x^2)$ e $x=\frac{2\log2}{n}$:
$$\left(1+\tfrac{2\log2}{n}\right)^{n^2}=\exp\left(n^2\left[\tfrac{2\log2}{n}-\tfrac{2\log^22}{n^2}+o\!\left(\tfrac1{n^2}\right)\right]\right)=\exp\left(2n\log2-2\log^22+o(1)\right)$$

Quindi il secondo termine è $\sim4^n\,e^{-2\log^22}$, che domina su $3^n$. Raccolgo:
$$\sqrt[n]{4^n\,e^{-2\log^22}(1+o(1))}=4\cdot\left(e^{-2\log^22}(1+o(1))\right)^{1/n}\to4\cdot1$$

$$\boxed4$$

> **Attenzione.** Fermarsi al primo ordine, $(1+\frac cn)^{n^2}\approx e^{cn}$, qui funziona perché la radice $n$-esima elimina la costante moltiplicativa. In generale però **non** è un'equivalenza asintotica: $(1+\frac cn)^{n^2}\sim e^{cn-c^2/2}$, e la costante $e^{-c^2/2}$ va tenuta (con $c=2\log2$ vale $e^{-2\log^22}$).

---

## Esercizio 9 (Limite 13) — Discussione al variare di $\alpha\in\mathbb R$

$$\lim_{n\to+\infty}\frac{\sin\left(\frac{2}{\sqrt n}\right)\log\left(1+\frac1n\right)}{\sqrt n\left[1-\cos\left(\frac4n\right)\right]^\alpha}$$

**Idea.** Si sostituiscono gli equivalenti asintotici e si riduce tutto a un'unica potenza $n^{\beta(\alpha)}$. Il segno di $\beta$ decide il limite. (Il parametro è all'esponente di un'espressione positiva, quindi gli equivalenti sono applicabili: $a_n\sim b_n\Rightarrow a_n^\alpha\sim b_n^\alpha$.)

**Svolgimento.**

- Numeratore: $\sin\frac2{\sqrt n}\sim\frac2{\sqrt n}$, $\log(1+\frac1n)\sim\frac1n$, quindi $\sim2n^{-3/2}$.
- $1-\cos\frac4n\sim\frac12\left(\frac4n\right)^2=\frac8{n^2}$.
- Denominatore: $\sqrt n\cdot\left(\frac8{n^2}\right)^\alpha=8^\alpha n^{\frac12-2\alpha}$.

$$\frac{2n^{-3/2}}{8^\alpha n^{1/2-2\alpha}}=\frac2{8^\alpha}\,n^{2\alpha-2}$$

| $\alpha$ | esponente $2\alpha-2$ | limite |
|---|---|---|
| $\alpha>1$ | $>0$ | $+\infty$ |
| $\alpha=1$ | $=0$ | $\dfrac28=\boxed{\dfrac14}$ |
| $\alpha<1$ | $<0$ | $0$ |

---

## Esercizio 10 — Parametro $\alpha$ in $e^{\alpha n}$ e fattore oscillante

$$\lim_{n\to+\infty}\frac{(e^{2n}-1)\cos^3(n)}{n\,e^{\alpha n}}$$

**Idea.** Il fattore $\cos^3 n$ **non ha limite** ma è **limitato**: $|\cos^3n|\le1$. Quindi serve il teorema "infinitesimo × limitato = infinitesimo" quando il resto tende a $0$, mentre se il resto diverge l'oscillazione si propaga al risultato.

Poiché $e^{2n}-1\sim e^{2n}$, la successione vale circa $\dfrac{e^{(2-\alpha)n}}{n}\cos^3 n$.

**Caso $\alpha\ge2$.** $\dfrac{e^{(2-\alpha)n}}{n}\to0$ (per $\alpha=2$ resta $\frac1n$). Infinitesimo per limitata:
$$\left|\frac{e^{(2-\alpha)n}}{n}\cos^3n\right|\le\frac{e^{(2-\alpha)n}}{n}\to0\quad\Rightarrow\quad\boxed0$$
(teorema del confronto sul valore assoluto).

**Caso $\alpha<2$.** $\dfrac{e^{(2-\alpha)n}}{n}\to+\infty$ per la gerarchia degli infiniti, ma $\cos^3n$ oscilla. La successione $\{n\bmod2\pi\}$ è **densa** in $[0,2\pi]$ (perché $\pi$ è irrazionale), quindi esistono infiniti $n$ con $\cos n>\frac12$ e infiniti con $\cos n<-\frac12$.

- Lungo i primi: $\cos^3n>\frac18$ e la successione $\to+\infty$.
- Lungo i secondi: $\cos^3n<-\frac18$ e la successione $\to-\infty$.

Due sottosuccessioni con limiti diversi: **il limite non esiste**.

---

## Riepilogo

| # | Limite | Tecnica | Risultato |
|---|---|---|---|
| 1 | $\frac{\log(1+3/n^2)}{\sin(2/n^2)}$ | notevoli | $\frac32$ |
| 2 | rapporto di logaritmi | proprietà dei $\log$ + raccoglimento | $-\frac9{20}$ |
| 3 | torre di potenze | gerarchia degli infiniti | $0$ |
| 4 | radice e $\sin^2$ | asintotici | $2$ |
| 5 | differenze di radici | razionalizzazione | $0$ |
| 6 | fattoriali | raccoglimento di $n!$ | $0$ |
| 7 | $1^\infty$ | $e^{a_nb_n}$ | $e^6$ |
| 8 | radice $n$-esima | termine dominante + sviluppo | $4$ |
| 9 | parametro $\alpha$ | asintotici + discussione | $+\infty,\ \frac14,\ 0$ |
| 10 | parametro $\alpha$, $\cos^3n$ | limitato × infinitesimo / sottosuccessioni | $0$ o non esiste |
