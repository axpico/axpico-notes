---
tags:
  - analisi1
  - asintotici
  - o-piccolo
  - serie
  - criteri-del-confronto
---
# Asintotici, $o$ piccolo e serie a termini non negativi — Esercizi

Trascrizione degli appunti di Analisi 1 (lezione/esercitazione). Teoria collegata: [[Confronti e stime asintotiche]], [[Successioni monotone, infinitesimi e limiti notevoli]], [[Serie numeriche]]. Esercizi precedenti: [[Limiti di successioni]].

> [!todo] Esercizi non svolti
> Quelli numerati $3.1$, $3.2$, $6.1$ sono riportati **solo come testo**: non sono stati svolti negli appunti (e non li svolgo qui).

---

# Parte A — Asintotici e $o$ piccolo

## 1. Cosa **non** si conserva con $\sim$

Ricorda: $a_n\sim b_n \iff a_n/b_n\to1 \iff a_n=b_n+o(b_n)$. La relazione $\sim$ è compatibile con prodotti, quozienti e potenze, ma **non** con tutte le operazioni. Controesempi:

**(a) Esponenziale.** $a_n=n^2+n,\; b_n=n^2$. Allora $a_n\sim b_n$ (infatti $a_n/b_n=1+1/n\to1$), ma
$$\frac{e^{a_n}}{e^{b_n}}=e^{a_n-b_n}=e^{n}\to+\infty\quad\Longrightarrow\quad e^{a_n}\not\sim e^{b_n}.$$
*Perché:* $e^{a_n}/e^{b_n}=e^{a_n-b_n}$ e la differenza $a_n-b_n=o(b_n)$ **non** è detto che tenda a $0$ (qui vale $n$): è solo "piccola rispetto a $b_n$".

**(b) Logaritmo.** $a_n=1+\frac1n,\; b_n=1+\frac1{n^2}$. Entrambe $\to1$ e $a_n/b_n\to1$, quindi $a_n\sim b_n$, ma
$$\frac{\log a_n}{\log b_n}=\frac{\log\left(1+\frac1n\right)}{\log\left(1+\frac1{n^2}\right)}\sim\frac{1/n}{1/n^2}=n\to+\infty.$$
*Perché:* $\log a_n$ e $\log b_n$ sono entrambi infinitesimi e il logaritmo "amplifica" la differenza vicino a $1$.

**(c) Somme.** $a_n=n+1,\; a_n'=n+2$ e $b_n=b_n'=-n$ (somme $1$ e $2$ come negli appunti). Si ha $a_n\sim a_n'$ e $b_n\sim b_n'$, ma
$$a_n+b_n=1,\qquad a_n'+b_n'=2 \;\Longrightarrow\; a_n+b_n\not\sim a_n'+b_n'.$$
Cioè **non si può sostituire un asintotico dentro una somma/differenza** (cancellazioni).

### Uso sbagliato dell'asintotico in una somma

$$\lim_{n\to+\infty} n^3\left[\sin\left(\tfrac1n\right)-\tfrac1n+\tfrac1{3n^3}\right]$$

*Tentativo sbagliato:* sostituire $\sin\frac1n\sim\frac1n$ nella somma:
$$n^3\left[\tfrac1n-\tfrac1n+\tfrac1{3n^3}\right]\to\tfrac13\qquad\text{(sbagliato)}.$$
*Perché è sbagliato:* sostituendo $\sin\frac1n=\frac1n+o\!\left(\frac1n\right)$ si ottiene
$$n^3\left[\tfrac1n+o\!\left(\tfrac1n\right)-\tfrac1n+\tfrac1{3n^3}\right]=n^3\left[o\!\left(\tfrac1n\right)+\tfrac1{3n^3}\right]=o(n^2)+\tfrac13,$$
e $o(n^2)$ può benissimo non essere trascurabile: il $\tfrac13$ non è affidabile. Per risolverlo serve un termine in più dello sviluppo, $\sin x=x-\frac{x^3}{6}+o(x^3)$, che dà il valore corretto $\tfrac16$ (non richiesto dagli appunti, aggiunto come verifica).

---

## 2. Passaggio agli asintotici negli esponenziali e nei logaritmi

### Teorema (esponenziale)
Se $a_n\sim b_n$ ed esiste il limite **finito** $\lim a_n=\ell\in\mathbb R$, allora $e^{a_n}\sim e^{b_n}$.

**Dimostrazione.** $a_n\sim b_n$ significa $a_n=b_n+c_n$ con $c_n=o(b_n)$. Ora $c_n=a_n-b_n\to\ell-\ell=0$ (qui serve che $a_n$ e quindi $b_n$ abbiano limite finito: $b_n\to\ell$ perché $a_n/b_n\to1$). Allora
$$\frac{e^{a_n}}{e^{b_n}}=e^{a_n-b_n}=e^{c_n}\to e^0=1.\qquad\blacksquare$$

**Cosa succede se $a_n\to\infty$?** In generale $c_n=o(b_n)$ **non** è infinitesima (come in $(a)$, dove $c_n=n$), quindi la dimostrazione cade: l'esponenziale non conserva $\sim$.

### Teorema (logaritmo)
Se $a_n\sim b_n$ ed esiste $\lim a_n=\ell\in[0,+\infty]$ con $\ell\neq1$, allora $\log a_n\sim\log b_n$.

**Dimostrazione.** Scrivo $a_n=b_n+o(b_n)=b_n\left(1+\frac{o(b_n)}{b_n}\right)$ con $\frac{o(b_n)}{b_n}\to0$. Allora
$$\frac{\log a_n}{\log b_n}=\frac{\log b_n+\log\left(1+\frac{o(b_n)}{b_n}\right)}{\log b_n}=1+\frac{\log\left(1+\frac{o(b_n)}{b_n}\right)}{\log b_n}.$$
Il numeratore della frazione $\to\log1=0$, mentre il denominatore $\log b_n\to\log\ell\neq0$ (anche $\pm\infty$ per $\ell=0,+\infty$): la frazione tende a $0$ e il tutto a $1$. $\blacksquare$

*Nota:* la condizione $\ell\neq1$ è esattamente ciò che rompe il controesempio $(b)$.

---

## 3. Proprietà dell'$o$ piccolo

Qui $a_n,b_n$ sono successioni e $o(\cdot)$ indica una successione trascurabile rispetto all'argomento.

| # | Proprietà | Note |
|---|---|---|
| 1 | $a_n\cdot o(b_n)=o(a_nb_n)$ | $\dfrac{a_nc_n}{a_nb_n}=\dfrac{c_n}{b_n}\to0$ |
| 2 | $o(o(a_n))=o(a_n)$ | |
| 3 | $c\cdot o(a_n)=o(c\,a_n)=o(a_n)$ $\;\forall c\in\mathbb R\setminus\{0\}$ | le costanti non cambiano l'ordine |
| 4 | $o(a_n)+o(a_n)=o(a_n)$ | |
| 5 | $o(a_n)+o(b_n)\neq o(a_n+b_n)$ | **falsa** in generale, vedi sotto |
| 6 | $o(a_n)\cdot o(b_n)=o(a_nb_n)$ | |
| 7 | $(a_n+o(a_n))^k=a_n^k+o(a_n^k)\;\;\forall k\ge1$ | vedi sotto |

**Controesempio per la 5.** Prendo $a_n=n\to+\infty$ e $b_n=1-n\to-\infty$ (così $a_n+b_n=1$). Allora $1=o(a_n)$ e $1=o(b_n)$, quindi $o(a_n)+o(b_n)$ contiene $1+1=2$; ma $o(a_n+b_n)=o(1)$ è una qualunque successione **infinitesima**, e $2\notin o(1)$.
> $\boxed{o(1)=\text{qualsiasi successione infinitesima}}$

**Verifica della 7 per $k=2$.**
$$\left(a_n+o(a_n)\right)^2=a_n^2+2a_n\,o(a_n)+\underbrace{[o(a_n)]^2}_{o(a_n^2)}=a_n^2+o(a_n^2),$$
perché $a_n\,o(a_n)=o(a_n^2)$ (prop. 1) e $[o(a_n)]^2=o(a_n^2)$ (prop. 6).

---

## 4. Esercizi sui limiti

### Esercizio 1

$$\lim_{n\to+\infty} n^2\left[\log^2\left(1+\frac2n\right)-\frac1{n^2}\right]$$

**Idea.** Differenza in cui compaiono due infinitesimi dello stesso ordine ($\frac1{n^2}$): non posso semplicemente sostituire $\log^2(\cdot)\sim\frac4{n^2}$ dentro la somma; uso $o$ piccolo per tenere traccia dell'errore.

**Svolgimento.** $\log\left(1+\frac2n\right)\sim\frac2n$, cioè $\log\left(1+\frac2n\right)=\frac2n+o\!\left(\frac1n\right)$. Elevo al quadrato (prop. 7):
$$\log^2\left(1+\tfrac2n\right)=\left(\tfrac2n+o\!\left(\tfrac1n\right)\right)^2=\tfrac4{n^2}+o\!\left(\tfrac1{n^2}\right).$$
Quindi
$$n^2\left[\tfrac4{n^2}+o\!\left(\tfrac1{n^2}\right)-\tfrac1{n^2}\right]=n^2\left[\tfrac3{n^2}+o\!\left(\tfrac1{n^2}\right)\right]=3+o(1)\;\to\;\boxed3.$$

### Esercizio 2

$$\lim_{n\to+\infty}\frac{\log\left(n^5+n^3+\arctan n\right)}{\log\left(n^4+2\right)}$$

**Idea.** Per i logaritmi posso passare agli asintotici (teorema §2) se l'argomento tende a un limite $\neq1$: qui tende a $+\infty$.

**Svolgimento.**
- $n^5+n^3+\arctan n\sim n^5\to+\infty\neq1\;\Rightarrow\;\log(\ldots)\sim\log n^5=5\log n$.
- $n^4+2\sim n^4\to+\infty\neq1\;\Rightarrow\;\log(n^4+2)\sim4\log n$.

$$\frac{5\log n}{4\log n}=\boxed{\frac54}.$$

### Esercizio 3

$$\lim_{n\to+\infty}\left[1-\cos\left(\tfrac1n\right)\right]^{\tan\left(\frac1n\right)}$$

**Idea.** Forma $0^0$: riscrivo $x^y=e^{y\log x}$ e studio l'esponente.

**Svolgimento.**
$$\left[1-\cos\tfrac1n\right]^{\tan\frac1n}=e^{\tan\left(\frac1n\right)\log\left(1-\cos\frac1n\right)}.$$
- $\tan\frac1n=\dfrac{\sin\frac1n}{\cos\frac1n}\sim\dfrac{1/n}{1}=\dfrac1n$.
- $1-\cos\frac1n\sim\dfrac1{2n^2}\to0\neq1$, quindi $\log\left(1-\cos\frac1n\right)\sim\log\dfrac1{2n^2}=-2\log\left(\sqrt2\,n\right)$.

L'esponente (prodotto → posso sostituire) è
$$\sim\frac1n\cdot\left(-2\log(\sqrt2\,n)\right)=-\frac{2\log(\sqrt2\,n)}{n}\to0,$$
perché $\log n\ll n$ (gerarchia degli infiniti). Dunque il limite è $e^0=\boxed1$.

> [!todo] Da svolgere (non svolti negli appunti)
> **3.1)** $\displaystyle\lim_{n\to+\infty}\left(\sin\frac1n\right)^{1-\cos\left(\frac1n\right)}$
>
> **3.2)** $\displaystyle\lim_{n\to+\infty}\left[1-\cos\left(\log\left(1+\frac3{n^2}\right)\right)\right]^{n^2}$ *(lettura della foto incerta sul coefficiente $3$)*

### Esercizio 4

$$\lim_{n\to+\infty}\arctan\left(\frac1n+\frac1{n^2}\right)\left(\sqrt{n^4-\frac{n^3}3}-n^2\right)$$

**Idea.** Prodotto di due fattori: posso sostituire ciascuno col proprio asintotico, purché lo calcoli bene (il secondo è una differenza $\infty-\infty$: va trattato con un raccoglimento e un limite notevole).

**Svolgimento.**
*Primo fattore.* Osservazione: se $a_n\to0$, allora $\arctan a_n\sim a_n$. Qui $a_n=\frac1n+\frac1{n^2}\to0$ e $\frac1{n^2}=o\!\left(\frac1n\right)$, quindi
$$\arctan\left(\tfrac1n+\tfrac1{n^2}\right)\sim\tfrac1n+\tfrac1{n^2}\sim\tfrac1n.$$
*Secondo fattore.* Raccolgo $n^4$ sotto radice:
$$\sqrt{n^4-\tfrac{n^3}3}-n^2=\left[n^4\left(1-\tfrac1{3n}\right)\right]^{1/2}-n^2=n^2\left[\left(1-\tfrac1{3n}\right)^{1/2}-1\right].$$
Con $(1+\varepsilon_n)^{a}-1\sim a\,\varepsilon_n$ ($\varepsilon_n=-\frac1{3n}$, $a=\frac12$):
$$\left(1-\tfrac1{3n}\right)^{1/2}-1\sim\left(-\tfrac1{3n}\right)\cdot\tfrac12=-\tfrac1{6n}\;\Longrightarrow\;\text{secondo fattore}\sim n^2\cdot\left(-\tfrac1{6n}\right)=-\tfrac n6.$$
*Prodotto.*
$$\tfrac1n\cdot\left(-\tfrac n6\right)=\boxed{-\tfrac16}.$$

### Esercizio 5 (con parametro $\alpha$)

$$\lim_{n\to+\infty}\frac{\arctan(n^\alpha)}{\sqrt{n+2}-\sqrt{n-2}}\qquad\text{al variare di }\alpha\in\mathbb R.$$

**Idea.** Si studiano separatamente numeratore e denominatore; l'arcotangente cambia comportamento a seconda del segno di $\alpha$.

**Numeratore.** $n^\alpha\to\begin{cases}1&\alpha=0\\0&\alpha<0\\+\infty&\alpha>0\end{cases}$, quindi
$$\arctan(n^\alpha)\;\begin{cases}=\frac\pi4\ (\arctan1)&\alpha=0\\ n^\alpha\ (\text{perché }\arctan x\sim x\text{ per }x\to0)&\alpha<0\\ \frac\pi2&\alpha>0.\end{cases}$$

**Denominatore.** Razionalizzo:
$$\frac1{\sqrt{n+2}-\sqrt{n-2}}=\frac{\sqrt{n+2}+\sqrt{n-2}}{(n+2)-(n-2)}=\frac{n^{1/2}\left[\sqrt{1+\frac2n}+\sqrt{1-\frac2n}\right]}4\sim\frac{n^{1/2}\cdot2}4=\frac12\,n^{1/2},$$
perché la parentesi tende a $2$.

**Rapporto** (numeratore $\times$ reciproco del denominatore):
$$\frac{\arctan(n^\alpha)}{\sqrt{n+2}-\sqrt{n-2}}\sim\begin{cases}\frac\pi4\cdot\frac12\,n^{1/2}&\alpha=0\\[2pt] \frac12\,n^{\alpha+\frac12}&\alpha<0\\[2pt] \frac\pi2\cdot\frac12\,n^{1/2}&\alpha>0.\end{cases}$$
- Per $\alpha\ge0$ il limite è $+\infty$ (c'è $n^{1/2}$ moltiplicato per una costante positiva).
- Per $\alpha<0$: $\frac12 n^{\alpha+\frac12}\to\begin{cases}\frac12&\alpha=-\frac12\\+\infty&\alpha>-\frac12\\0&\alpha<-\frac12.\end{cases}$ Quindi, in particolare, $+\infty$ per $-\frac12<\alpha<0$.

$$\boxed{\lim=\begin{cases}+\infty&\alpha>-\frac12\\[2pt]\frac12&\alpha=-\frac12\\[2pt]0&\alpha<-\frac12\end{cases}}$$

### Esercizio 6 (con parametro $\alpha$)

$$\lim_{n\to+\infty}\frac{\sin\left(\frac1{n^3}\right)}{\sqrt[3]{1+\frac1{n^\alpha}}-1}\qquad\text{al variare di }\alpha.$$

**Numeratore.** $\sin\frac1{n^3}\sim\frac1{n^3}$ (argomento $\to0$).

**Denominatore** $\sqrt[3]{1+n^{-\alpha}}-1$:
$$\begin{cases}\sqrt[3]2-1\ (\text{costante}\neq0)&\alpha=0\\ \sim\frac1{3n^\alpha}\ (\text{notevole, }a=\tfrac13)&\alpha>0\\ \to+\infty&\alpha<0.\end{cases}$$

**Caso $\alpha\le0$:** numeratore $\to0$, denominatore $\to$ costante non nulla o $+\infty$: il limite vale $0$.

**Caso $\alpha>0$:**
$$\frac{1/n^3}{1/(3n^\alpha)}=3\,n^{\alpha-3}\;\to\;\begin{cases}3&\alpha=3\\+\infty&\alpha>3\\0&0<\alpha<3.\end{cases}$$

$$\boxed{\lim=\begin{cases}0&\alpha<3\\3&\alpha=3\\+\infty&\alpha>3\end{cases}}$$

> [!todo] Da svolgere (non svolto negli appunti)
> **6.1)** $\displaystyle\lim_{n\to+\infty}\frac{\sin\left(\frac1{n^{\alpha^2+1}}\right)-\log\left(1+\frac2n\right)}{n^{2-\alpha}}$ al variare di $\alpha$ *(lettura della foto incerta sull'esponente di $n$ dentro il seno)*

---

# Parte B — Serie a termini non negativi

## 5. Strumenti

**Criterio del confronto.** Se $0\le a_n\le b_n$ (almeno definitivamente):
- $\sum b_n$ converge $\Rightarrow\sum a_n$ converge;
- $\sum a_n$ diverge $\Rightarrow\sum b_n$ diverge.

**Criterio del confronto asintotico.** Siano $a_n,b_n\ge0$ e $\displaystyle\lim_{n\to+\infty}\frac{a_n}{b_n}=\ell\in[0,+\infty]$. Allora:
- se $\sum b_n$ converge e $\ell\in[0,+\infty)$, anche $\sum a_n$ converge;
- se $\sum b_n$ diverge e $\ell\in(0,+\infty]$, anche $\sum a_n$ diverge.

In particolare, se $a_n\sim b_n$ ($\ell=1$) le due serie hanno **lo stesso carattere**.

**Serie di riferimento.**
- Geometrica $\sum q^n$: converge $\iff|q|<1$.
- Armonica generalizzata $\sum\frac1{n^p}$: converge $\iff p>1$.

**Uso dell'asintotico sulle potenze.** Se $a_n\sim b_n$ e $c\in\mathbb R$ è costante, allora $a_n^c\sim b_n^c$.

---

## 6. Esercizi sulle serie

### Serie 1

$$\sum_{n=1}^{+\infty}\frac2{n^2+n}\;=\;2\sum_{n=1}^{+\infty}\frac1{n(n+1)}.$$

Poiché $n^2+n\ge n^2$:
$$0\le\frac2{n^2+n}\le\frac2{n^2}.$$
$\sum\frac2{n^2}=2\sum\frac1{n^2}$ converge ($p=2>1$). Per il **teorema del confronto** la serie converge.

*(Verifica indipendente:* è telescopica, $\frac1{n(n+1)}=\frac1n-\frac1{n+1}$, quindi la somma vale $2$.)

### Serie 2

$$\sum_{n=0}^{+\infty}\frac{n^2}{3^n}.$$

Per la gerarchia degli infiniti $\frac{n^2}{3^n}\to0$ (condizione necessaria, non sufficiente). Inoltre $n^2\le2^n$ **almeno definitivamente** (per $n\ge4$, sempre per gerarchia: l'esponenziale batte il polinomio). Quindi
$$0\le\frac{n^2}{3^n}\le\frac{2^n}{3^n}=\left(\frac23\right)^n,$$
e $\sum\left(\frac23\right)^n$ converge (serie geometrica di ragione $q=\frac23<1$). Per confronto la serie **converge**.

### Serie 3

$$\sum_{n=2}^{+\infty}\frac{\log n}n.$$

Per $n\ge3$ vale $\log n\ge1$, quindi
$$\frac{\log n}n\ge\frac1n,$$
e $\sum\frac1n$ diverge (armonica). Per confronto la serie **diverge**.

### Serie 4

$$\sum_{n=1}^{+\infty}\frac{n^4-3\sin n}{3^n+4n}.$$

**Segno.** $n^4-3\sin n\ge n^4-3>0$ almeno definitivamente (per $n\ge2$): la serie è definitivamente a termini non negativi, quindi si possono usare i criteri del confronto.

**Asintotici (numeratore e denominatore):**
- $n^4-3\sin n=n^4+o(n^4)\sim n^4$, perché $\dfrac{3\sin n}{n^4}\to0$;
- $3^n+4n=3^n+o(3^n)\sim3^n$ (gerarchia: $n\ll3^n$).

Dunque (quozienti: posso sostituire)
$$\frac{n^4-3\sin n}{3^n+4n}\sim\frac{n^4}{3^n}.$$

**Studio di $\sum\frac{n^4}{3^n}$.** Ancora per gerarchia $n^4\le2^n$ almeno definitivamente (per $n\ge16$), quindi
$$0\le\frac{n^4}{3^n}\le\left(\frac23\right)^n\;\longrightarrow\;\text{converge}.$$
Per il **confronto** converge $\sum\frac{n^4}{3^n}$ e per il **confronto asintotico** converge anche la serie di partenza.

### Serie 5

$$\sum_{n=1}^{+\infty}\frac{(n+1)(2+\sin n)}{\sqrt[3]{n^5}}.$$

Da $-1\le\sin n\le1$ segue $1\le2+\sin n\le3$.

**Maggiorazione (inconcludente).** $0\le\dfrac{(n+1)(2+\sin n)}{\sqrt[3]{n^5}}\le\dfrac{3n+3}{\sqrt[3]{n^5}}\sim\dfrac{3n}{n^{5/3}}=\dfrac3{n^{2/3}}\to0$: dice solo che il termine generale è infinitesimo (condizione necessaria), ma non risolve la convergenza.

**Minorazione (decisiva).** Poiché $2+\sin n\ge1$:
$$\frac{(n+1)(2+\sin n)}{\sqrt[3]{n^5}}\ge\frac{n+1}{n^{5/3}}\ge\frac n{n^{5/3}}=\frac1{n^{2/3}},$$
e $\sum\frac1{n^{2/3}}$ **diverge** (armonica generalizzata con $p=\frac23\le1$). Per il **teorema del confronto** la serie **diverge**.

*Nota:* qui non si può usare il confronto asintotico con una serie "esplicita" perché $\sin n$ non ha limite: la sandwich $1\le2+\sin n\le3$ è lo strumento giusto.

### Serie 6 (con parametro $\alpha$)

$$\sum_{n=1}^{+\infty}\left(e^{1/n}-1\right)\log(n)\left[1-\cos\left(\frac1n\right)\right]^{\alpha}.$$

La serie è a termini definitivamente positivi ($e^{1/n}-1>0$, $\log n>0$ per $n\ge2$, $1-\cos\frac1n>0$).

**Asintotici dei fattori:**
- $e^{1/n}-1\sim\dfrac1n$;
- $\log n\sim\log n$;
- $1-\cos\frac1n\sim\dfrac1{2n^2}$, e la potenza $\alpha$ si conserva ($a_n\sim b_n\Rightarrow a_n^\alpha\sim b_n^\alpha$).

Quindi
$$a_n\sim\frac1n\cdot\log n\cdot\left(\frac1{2n^2}\right)^\alpha=\frac{\log n}{2^\alpha\,n^{2\alpha+1}}.$$

**Caso $\alpha\le0$** (cioè $2\alpha+1\le1$). Per $n\ge3$, $\log n\ge1$, quindi
$$\frac{\log n}{2^\alpha n^{2\alpha+1}}\ge\frac1{2^\alpha\,n^{2\alpha+1}},$$
e $\sum\frac1{n^{2\alpha+1}}$ diverge perché l'esponente è $\le1$. Per confronto (e poi asintotico) la serie **diverge**.

**Caso $\alpha>0$.** Scelgo $b_n=\dfrac1{n^{\alpha+1}}$ (con $\alpha+1>1$, quindi $\sum b_n$ **converge**). Allora
$$\frac{a_n}{b_n}\sim\frac{\log n}{2^\alpha n^{2\alpha+1}}\cdot n^{\alpha+1}=\frac{\log n}{2^\alpha\,n^\alpha}\xrightarrow{n\to+\infty}0\qquad(\alpha>0,\ \log n\ll n^\alpha).$$
Per il **confronto asintotico** con $\ell=0$ e $\sum b_n$ convergente, la serie **converge**.

$$\boxed{\text{la serie converge}\iff\alpha>0.}$$
