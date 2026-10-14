---
tags:
  - analisi1
  - serie
  - convergenza
  - politecnico
---
Prosegue da [[Confronti e stime asintotiche]] (equivalenza asintotica, scala degli infiniti) e da [[Successioni monotone, infinitesimi e limiti notevoli]] (teorema di regolarità delle successioni monotone).

Idea: una **serie** è una "somma di infiniti termini". Non ha senso sommare infiniti numeri "uno alla volta", quindi si **definisce** la somma come il limite delle somme dei primi $n$ termini. Tutto lo studio delle serie è quindi uno studio di **limiti di successioni** (le somme parziali).

## 1. Definizioni

Sia $\{a_n\}$ una successione. Si definiscono le **somme parziali**
$$S_1:=a_1,\quad S_2:=a_1+a_2,\quad S_3:=a_1+a_2+a_3,\ \dots,\quad S_n:=\sum_{k=1}^{n}a_k=S_{n-1}+a_n .$$

- $S_n$ è la somma dei primi $n$ elementi di $\{a_k\}$.
- La nuova successione $\{S_n\}$ si chiama **serie di termine generale $a_k$**.
- La **somma della serie** (per abuso di linguaggio, "la serie") è
$$\sum_{k=1}^{\infty}a_k:=\lim_{n\to\infty}S_n=\lim_{n\to\infty}\sum_{k=1}^{n}a_k .$$

**Carattere della serie.** Si dice che la serie è
- **convergente** se $\exists\lim S_n\in\mathbb R$ (finito);
- **divergente** se $\lim S_n=\pm\infty$;
- **indeterminata** se $\nexists\lim S_n$.

Convergente e divergente sono i due casi **regolari** (il limite esiste in $\overline{\mathbb R}$). Il **carattere** di una serie è la sua proprietà di essere convergente, divergente o indeterminata.

> [!warning] Non confondere
> $a_n$ (termine generale) e $S_n$ (somma parziale) sono **due successioni diverse**. Il carattere della serie è il comportamento di $S_n$, non di $a_n$.

## 2. Serie telescopiche

### 2.1 Esempio base

$$a_k=\frac1{k(k+1)}=\frac1k-\frac1{k+1}.$$
(Scomposizione in fratti semplici: $\frac1k-\frac1{k+1}=\frac{(k+1)-k}{k(k+1)}$.)

I termini sono $a_1=1-\frac12,\ a_2=\frac12-\frac13,\ a_3=\frac13-\frac14,\ \dots$ e le somme parziali si "accorciano":
$$S_n=\left(1-\tfrac12\right)+\left(\tfrac12-\tfrac13\right)+\left(\tfrac13-\tfrac14\right)+\dots+\left(\tfrac1n-\tfrac1{n+1}\right)=1-\frac1{n+1}.$$
Quindi
$$\sum_{k=1}^{\infty}\frac1{k(k+1)}=\lim_{n\to\infty}\left(1-\frac1{n+1}\right)=1\quad\Rightarrow\quad\text{serie convergente, somma }1.$$

### 2.2 Caso generale

Se $a_k=A_{k+1}-A_k$ con $A_k\to0$ allora
$$S_n=\sum_{k=1}^n(A_{k+1}-A_k)=(A_2-A_1)+(A_3-A_2)+\dots+(A_{n+1}-A_n)=A_{n+1}-A_1$$
(tutti i termini intermedi si cancellano). Perciò
$$\sum_{k=1}^{\infty}a_k=\lim_{n\to\infty}(A_{n+1}-A_1)=-A_1 .$$
Le serie di questo tipo si dicono **telescopiche**. Più in generale, se $A_k\to L\in\mathbb R$ la somma vale $L-A_1$; se $A_k$ non ha limite finito si studia $A_{n+1}-A_1$.

Nell'esempio base: $A_k=\frac1k\to0$, $A_1=1$, ma $a_k=A_k-A_{k+1}=-(A_{k+1}-A_k)$: segno opposto, quindi somma $=+A_1=1$. ✔

## 3. Serie geometrica

$$\sum_{k=0}^{\infty}x^k,\qquad x\in\mathbb R\ \ (x=\text{ragione}).$$

Per induzione (già dimostrato) le somme parziali sono
$$S_n=\sum_{k=0}^{n}x^k=\begin{cases}\dfrac{1-x^{n+1}}{1-x}&x\neq1\\[2mm] n+1&x=1.\end{cases}$$

*Perché vale la formula (idea telescopica).* $(1-x)S_n=\sum_{k=0}^n x^k-\sum_{k=0}^n x^{k+1}=1-x^{n+1}$: i termini intermedi si cancellano.

Passando al limite (usando $x^{n+1}\to0$ se $|x|<1$, $\to+\infty$ se $x>1$, non esiste se $x\le-1$):
$$\sum_{k=0}^{\infty}x^k=\lim_{n\to\infty}S_n=\begin{cases}\dfrac1{1-x}&-1<x<1\quad\text{convergente}\\[2mm]+\infty&x\ge1\quad\text{divergente}\\[2mm]\nexists&x\le-1\quad\text{indeterminata.}\end{cases}$$

> [!note] Precisazione
> Sul foglio la geometrica è indicata come "esempio di serie telescopica": non lo è in senso stretto (i termini $x^k$ non sono differenze consecutive), ma la dimostrazione della formula usa lo stesso meccanismo di cancellazione.

Casi tipici: $x=-1$: $S_n$ vale alternativamente $1,0,1,0,\dots$ (indeterminata); $x=1$: $S_n=n+1\to+\infty$.

## 4. Serie armonica e armonica generalizzata

**Serie armonica** (*non* telescopica):
$$\sum_{k=1}^{\infty}\frac1k=+\infty\qquad\text{divergente.}$$

**Serie armonica generalizzata** (di esponente $\alpha$):
$$\sum_{k=1}^{\infty}\frac1{k^\alpha}\ \text{ è }\ \begin{cases}\text{convergente}&\alpha>1\\ \text{divergente}&\alpha\le1\end{cases}$$
(per $0<\alpha\le1$ i termini sono positivi e la somma è $+\infty$; per $\alpha\le0$ il termine generale non tende a $0$, vedi §5.)

Sono le serie "di riferimento" per il **criterio del confronto** (§7–8). Le dimostrazioni di convergenza/divergenza si fanno con i criteri dell'integrale (o con la condensazione di Cauchy), che qui si assumono noti.

> [!tip] Da imparare a memoria
> $\sum\frac1{k^\alpha}$ converge $\iff\alpha>1$. Il caso di confine $\alpha=1$ **diverge** (anche se $\frac1k\to0$).

## 5. Condizione necessaria di convergenza

**Teorema.** Se $\displaystyle\sum_{n=1}^{\infty}a_n$ converge, allora $a_n\xrightarrow{n\to\infty}0$.

*Dimostrazione.* Sia $S:=\lim S_n\in\mathbb R$ (esiste finito perché la serie converge). Per definizione $S_n=S_{n-1}+a_n$, cioè
$$a_n=S_n-S_{n-1}.$$
Allora
$$\lim_{n\to\infty}a_n=\lim_{n\to\infty}(S_n-S_{n-1})=S-S=0 ,$$
perché $\{S_{n-1}\}$ è la stessa successione traslata e ha lo stesso limite $S$. ∎

**Contrapposizione (uso pratico).** Se $a_n\not\to0$ (il limite non esiste o è $\neq0$) allora la serie **non converge**.
Se in più $a_n\ge0$, la serie diverge a $+\infty$ (vedi §7).

**Esempio.** $\displaystyle\sum_{k=1}^{\infty}\arctan\!\left(\sqrt{k^3+2}\right)$. Poiché
$$a_k=\arctan\sqrt{k^3+2}\xrightarrow{k\to+\infty}\frac\pi2\neq0 ,$$
la condizione necessaria **non** è soddisfatta, quindi la serie non converge (essendo $a_k>0$, diverge a $+\infty$).

> [!warning] Condizione necessaria **ma non sufficiente**
> $a_n\to0$ non basta: la serie armonica $\sum\frac1k$ ha $\frac1k\to0$ eppure diverge. Se $a_n\to0$ non si può concludere nulla: servono altri criteri.

## 6. Linearità

**Proposizione.**
1. Se $\sum a_k$ e $\sum b_k$ sono **regolari** e la somma $\sum a_k+\sum b_k$ ha significato (cioè non è della forma $+\infty-\infty$), allora
$$\sum_{k=1}^{\infty}(a_k+b_k)=\sum_{k=1}^{\infty}a_k+\sum_{k=1}^{\infty}b_k .$$
2. Se $\sum a_k$ è regolare e $c\in\mathbb R\setminus\{0\}$ allora
$$\sum_{k=1}^{\infty}(c\,a_k)=c\sum_{k=1}^{\infty}a_k .$$
(Per $c=0$ la serie $\sum 0\cdot a_k$ vale $0$, mentre $0\cdot(\pm\infty)$ non è definito: per questo si esclude.)

*Idea della dimostrazione.* $\sum_{k=1}^n(a_k+b_k)=S_n^{(a)}+S_n^{(b)}$ e poi si applica l'algebra dei limiti di [[Algebra dei limiti e teoremi sui limiti]]. L'ipotesi "ha significato" è esattamente la richiesta di non cadere nella forma indeterminata $\infty-\infty$.

> [!info] Conseguenza utile
> Cambiare un numero finito di termini non cambia il **carattere** (cambia solo il valore della somma). Per questo i criteri sotto valgono "definitivamente".

## 7. Serie a termini non negativi

**Teorema (regolarità).** Una serie $\sum a_k$ con $a_k\ge0$ è **convergente oppure divergente positivamente** (è regolare, mai indeterminata).

*Dimostrazione.* $S_n=a_1+\dots+a_n$. Allora
$$S_{n+1}=S_n+a_{n+1}\ \ge\ S_n\qquad\forall n\in\mathbb N,$$
perché $a_{n+1}\ge0$. Quindi $\{S_n\}$ è **monotona crescente**. Per il teorema di regolarità delle successioni monotone
$$\exists\lim_{n\to\infty}S_n=\begin{cases}+\infty\\ \ell\in\mathbb R.\end{cases}\qquad\blacksquare$$

Per le serie a termini $\ge0$ la domanda è quindi solo "$S_n$ è limitata?": **limitata $\Rightarrow$ converge**, **illimitata $\Rightarrow$ diverge a $+\infty$**.

### 7.1 Criterio del confronto

**Teorema.** Siano $0\le a_n\le b_n$ (**definitivamente**, cioè per ogni $n$ da un certo indice in poi) due successioni non negative. Allora
1. $\displaystyle\sum b_k\ \text{converge}\ \Longrightarrow\ \sum a_k\ \text{converge}$;
2. $\displaystyle\sum a_k\ \text{diverge}\ \Longrightarrow\ \sum b_k\ \text{diverge}$.

*Dimostrazione.* Siano $S_n=\sum_{k=1}^na_k$ e $T_n=\sum_{k=1}^nb_k$. Da $0\le a_k\le b_k$ segue
$$S_n\le T_n\qquad\forall n\in\mathbb N .$$
Per il §7 $\{S_n\},\{T_n\}$ sono monotone crescenti, quindi regolari. Siano
$$S:=\lim S_n=\sum a_n,\qquad T:=\lim T_n=\sum b_n .$$
Per il teorema del confronto tra successioni (permanenza del segno) $S\le T$.
- Se $T\in\mathbb R$ (i) allora $S\le T<+\infty$, e $S\ge0$: $S\in\mathbb R$, la serie $\sum a_k$ converge.
- Se $S=+\infty$ (ii) allora $T\ge S=+\infty$, cioè $T=+\infty$: $\sum b_k$ diverge. ∎

> [!warning] Le due implicazioni non si invertono
> Se $\sum b_k$ **diverge** non si può dire nulla su $\sum a_k$ (e se $\sum a_k$ converge nulla su $\sum b_k$). Per concludere:
> - per **convergere** serve $a_k\le b_k$ con $b_k$ che converge ($b_k$ è il *maggiorante*);
> - per **divergere** serve $a_k\ge b_k$ con $b_k$ che diverge ($b_k$ è il *minorante*).

### 7.2 Esempi di applicazione del confronto

**Esempio 1.** $\displaystyle\sum_{k=1}^{\infty}\frac{\arctan\!\left(\sqrt{k+2}\right)}{k^4}$ (studiare il carattere).

- Condizione necessaria: $a_k=\dfrac{\arctan\sqrt{k+2}}{k^4}\to\dfrac{\pi/2}{\infty}=0$ ✔ (soddisfatta, non basta).
- $a_k\ge0$ per ogni $k$: serie a termini non negativi.
- Maggiorazione: $\arctan(\cdot)<\frac\pi2<2$, quindi
$$a_k<\frac{2}{k^4}\le\frac{20}{k^4}=:b_k\qquad\forall k\in\mathbb N$$
(il $20$ del foglio è una costante qualsiasi $\ge\frac\pi2$; qualunque costante va bene).
- $\sum b_k=20\sum\frac1{k^4}$ ha lo stesso carattere di $\sum\frac1{k^4}$ (§6): armonica generalizzata con $\alpha=4>1$, **convergente**.
- Per il confronto, $\sum a_k$ **converge**.

**Esempio 2.** $\displaystyle\sum_{k=1}^{\infty}\frac{\sin k+3}{\sqrt k}$.

- $a_k\to0$ ✔ (condizione necessaria soddisfatta).
- $\sin k\ge-1\Rightarrow\sin k+3\ge2>0$, quindi $a_k\ge\dfrac2{\sqrt k}=:b_k$ $\forall k$: termini positivi.
- $\sum b_k=2\sum\frac1{k^{1/2}}$: armonica generalizzata con $\alpha=\frac12\le1$, **divergente**.
- Per il confronto (minorante divergente), $\sum a_k$ **diverge** a $+\infty$.

## 8. Criterio del confronto asintotico

**Teorema.** Siano $a_n\ge0$ e $b_n>0$ per ogni $n$, e supponiamo che
$$\exists\lim_{n\to\infty}\frac{a_n}{b_n}=\ell\in[0,+\infty].$$
1. Se $\sum b_n$ **converge** e $\ell\in[0,+\infty)$ $\Longrightarrow$ $\sum a_n$ **converge**.
2. Se $\sum b_n$ **diverge** e $\ell\in(0,+\infty]$ $\Longrightarrow$ $\sum a_n$ **diverge**.

*Dimostrazione.*

**(i)** $\ell\in[0,+\infty)$. Per definizione di limite
$$\forall\varepsilon>0\ \exists\nu_\varepsilon\in\mathbb N:\quad \ell-\varepsilon<\frac{a_n}{b_n}<\ell+\varepsilon\qquad\forall n>\nu_\varepsilon .$$
Poiché $b_n>0$ si può moltiplicare senza cambiare i versi:
$$(\ell-\varepsilon)\,b_n<a_n<(\ell+\varepsilon)\,b_n\qquad\forall n>\nu_\varepsilon .$$
Poiché $\sum b_n$ converge, anche $\sum(\ell+\varepsilon)b_n=(\ell+\varepsilon)\sum b_n$ converge (§6). Per il **criterio del confronto** (maggiorante convergente) $\sum a_n$ converge. ∎

**(ii)** Due casi.

- $\ell\in(0,+\infty)$. Si sceglie $\varepsilon=\frac\ell3$: allora $\ell-\varepsilon=\frac{2\ell}3>0$ e
$$\frac{2\ell}{3}\,b_n<a_n\qquad\forall n>\nu_{\ell/3}.$$
Poiché $\sum b_n$ diverge, $\sum\frac{2\ell}3b_n$ diverge (§6, con $\frac{2\ell}{3}\neq0$). Per il confronto (minorante divergente) $\sum a_n$ diverge.
- $\ell=+\infty$. Per definizione
$$\forall M>0\ \exists\nu_M:\quad\frac{a_n}{b_n}>M\qquad\forall n>\nu_M\ \Longrightarrow\ a_n>M\,b_n .$$
Con $M=1$: $a_n>b_n$ definitivamente, e $\sum b_n$ diverge $\Rightarrow$ $\sum a_n$ diverge per il confronto. ∎

### 8.1 Versione con la serie armonica generalizzata

Si usa quasi sempre $b_n=\dfrac1{n^\alpha}$ come termine di paragone. Se
$$\ell=\lim_{n\to\infty}\frac{a_n}{1/n^\alpha}=\lim_{n\to\infty}n^\alpha a_n,$$
allora, per $a_n\ge0$:

| Condizione | Conclusione |
|---|---|
| $\ell\in[0,+\infty)$ e $\alpha>1$ | $\sum a_n$ **converge** |
| $\ell\in(0,+\infty]$ e $\alpha\le1$ | $\sum a_n$ **diverge** |

### 8.2 Corollario (asintotico)

**Corollario.** Siano $a_n\ge0$, $b_n>0$ con $a_n\sim b_n$, cioè $\displaystyle\lim\frac{a_n}{b_n}=1$. Allora
- $\sum b_n$ converge $\Rightarrow$ $\sum a_n$ converge;
- $\sum b_n$ diverge $\Rightarrow$ $\sum a_n$ diverge.

(In breve: **due serie a termini positivi asintoticamente equivalenti hanno lo stesso carattere**.) È il teorema precedente con $\ell=1\in(0,+\infty)$, che soddisfa entrambe le ipotesi.

> [!tip] Strategia operativa
> 1. Verifica $a_n\to0$ (altrimenti la serie non converge) e il segno ($a_n\ge0$).
> 2. Trova il termine **dominante** di $a_n$ con le stime di [[Confronti e stime asintotiche]] e scegli $b_n=\frac1{n^\alpha}$ (o simili).
> 3. Calcola $\ell=\lim\frac{a_n}{b_n}$ e applica il teorema; se $\ell=1$, usa il corollario.

## 9. Esercizi svolti

### Esercizio 1 — $\displaystyle\sum_{n=1}^{\infty}\log\!\left(1+\frac1{n^2}\right)$

- $a_n=\log\left(1+\frac1{n^2}\right)\to\log1=0$ ✔ (condizione necessaria).
- $a_n>0$ per ogni $n$ (argomento del $\log$ $>1$).
- Poiché $\frac1{n^2}\to0$, $\log\left(1+\frac1{n^2}\right)\sim\frac1{n^2}$, cioè $\lim\dfrac{a_n}{1/n^2}=1=\ell$.
- $\sum\frac1{n^2}$ è armonica generalizzata con $\alpha=2>1$: **converge**.
- Per il corollario, $\sum a_n$ **converge**.

### Esercizio 2 — $\displaystyle\sum_{n=1}^{\infty}\frac{\sqrt{n+1}-\sqrt n}{\sqrt{n^2+n+1}}$

**Passo 1 — il termine è una forma $\infty-\infty$** al numeratore ($\sqrt{n+1}-\sqrt n\to\infty-\infty$). Si **razionalizza**:
$$a_n=\frac{\left(\sqrt{n+1}-\sqrt n\right)\left(\sqrt{n+1}+\sqrt n\right)}{\sqrt{n^2+n+1}\,\left(\sqrt{n+1}+\sqrt n\right)}=\frac{(n+1)-n}{\sqrt{n^2+n+1}\left(\sqrt{n+1}+\sqrt n\right)}=\frac1{\sqrt{n^2+n+1}\left(\sqrt{n+1}+\sqrt n\right)}.$$

**Passo 2 — condizioni.** $a_n>0$ e $a_n\to0$ ✔.

**Passo 3 — stima asintotica.**
- $\sqrt{n^2+n+1}\sim\sqrt{n^2}=n$;
- $\sqrt{n+1}+\sqrt n\sim2\sqrt n$ (si verifica direttamente, senza invocare regole sulle somme di equivalenti: $\frac{\sqrt{n+1}+\sqrt n}{2\sqrt n}=\frac12\left(\sqrt{1+\frac1n}+1\right)\to1$).

Quindi
$$a_n\sim\frac1{n\cdot2\sqrt n}=\frac12\cdot\frac1{n^{3/2}} .$$

**Passo 4 — confronto asintotico.** $b_n=\dfrac1{n^{3/2}}$:
$$\ell=\lim\frac{a_n}{b_n}=\frac12\in(0,+\infty),\qquad\sum b_n\ \text{converge}\ (\alpha=\tfrac32>1).$$
Per il confronto asintotico $\sum a_n$ **converge**.

> [!note] Attenzione
> Qui $a_n\not\sim b_n$ (il limite è $\frac12$, non $1$): si usa il criterio nella forma generale con $\ell=\frac12$ e non il corollario. Si poteva anche usare $b_n=\frac1{2n^{3/2}}$ e il corollario.

### Esercizio 3 — $\displaystyle\sum_{n=1}^{\infty}\sin\!\left(\frac1n\right)\arctan\!\left(n^2+\sqrt{e^n-1}\right)$

- $\sin\frac1n>0$ per $n\ge1$ (perché $0<\frac1n\le1<\pi$) e $\arctan(\cdot)>0$ (argomento positivo): $a_n>0$.
- $\arctan(\dots)\to\frac\pi2$ e $\sin\frac1n\to0$: $a_n\to0$ ✔ (condizione necessaria soddisfatta, non conclude).
- Si sceglie $b_n=\dfrac1n$: $\sum\frac1n$ **diverge** (armonica, $\alpha=1$).
$$\lim_{n\to\infty}\frac{a_n}{b_n}=\lim_{n\to\infty}\underbrace{\frac{\sin\frac1n}{\frac1n}}_{\to1}\cdot\underbrace{\arctan\!\left(n^2+\sqrt{e^n-1}\right)}_{\to\frac\pi2}=\frac\pi2\in(0,+\infty).$$
- Per il confronto asintotico (caso divergente), $\sum a_n$ **diverge**.
- Equivalentemente: $a_n\sim\frac\pi2\cdot\frac1n$ (il rapporto $\frac{a_n}{\frac\pi2\frac1n}\to1$) e per il corollario $\sum\frac\pi2\frac1n$ diverge $\Rightarrow$ $\sum a_n$ diverge.

### Esercizio 4 — $\displaystyle\sum_{n=1}^{\infty}\frac1{n!}$

- $a_n=\frac1{n!}>0$ e $a_n\to0$ ✔.
- Si sceglie $b_n=\dfrac1{n^\alpha}$ con $\alpha>1$ (p.es. $\alpha=2$): $\sum b_n$ converge.
$$\lim_{n\to\infty}\frac{a_n}{b_n}=\lim_{n\to\infty}\frac{n^\alpha}{n!}=0=\ell\in[0,+\infty)$$
per la gerarchia degli infiniti ($n^\alpha\ll n!$, vedi [[Confronti e stime asintotiche]] §1).
- Per il confronto asintotico (caso convergente con $\ell=0$), $\sum a_n$ **converge**.

(Il caso $\ell=0$ funziona solo in **una** direzione: converge se $b_n$ converge; non si può concludere nulla se $b_n$ diverge.)

### Esercizio 5 — $\displaystyle\sum_{n=1}^{\infty}\frac{\log(n+3)}{n^3}$

- $a_n>0$ e $a_n\to0$ ✔.
- Si sceglie $b_n=\dfrac1{n^\alpha}$ con $1<\alpha<3$ (p.es. $\alpha=2$): $\sum b_n$ converge.
$$\frac{a_n}{b_n}=\frac{\log(n+3)}{n^{3-\alpha}}\xrightarrow{n\to\infty}0\qquad(\text{perché }3-\alpha>0,\ \log\ll n^{\text{positivo}}).$$
- $\ell=0$ e $\sum b_n$ converge $\Rightarrow$ $\sum a_n$ **converge**.

> [!tip] Perché $1<\alpha<3$
> Serve $\alpha>1$ perché $\sum b_n$ converga, e $\alpha<3$ perché $\frac{\log(n+3)}{n^{3-\alpha}}\to0$ richiede esponente $3-\alpha>0$ (il $\log$ cresce meno di ogni potenza positiva). Se $\alpha=3$ il limite sarebbe $\infty$ e il criterio non darebbe nulla (e $b_n=\frac1{n^3}$ sarebbe comunque un minorante, non un maggiorante).

## Riepilogo

| Strumento | Quando | Esito |
|---|---|---|
| Definizione ($S_n$) | serie telescopiche, geometriche | calcolo esatto della somma |
| $a_n\not\to0$ | sempre, come primo controllo | **non converge** |
| $a_n\to0$ | — | non conclude |
| $a_n\ge0$ | — | serie regolare (conv. o div. $+\infty$) |
| Confronto | $0\le a_n\le b_n$ | $b$ conv. $\Rightarrow$ $a$ conv.; $a$ div. $\Rightarrow$ $b$ div. |
| Confronto asintotico | $\ell=\lim\frac{a_n}{b_n}$ | $\ell\in[0,\infty)$ + $b$ conv. $\Rightarrow$ conv.; $\ell\in(0,\infty]$ + $b$ div. $\Rightarrow$ div. |
| Corollario | $a_n\sim b_n$ | stesso carattere |

**Serie di riferimento:** geometrica $\sum x^k$ (converge $\iff|x|<1$), armonica generalizzata $\sum\frac1{k^\alpha}$ (converge $\iff\alpha>1$).

## Collegamenti
- [[Confronti e stime asintotiche]]
- [[Successioni monotone, infinitesimi e limiti notevoli]]
- [[Algebra dei limiti e teoremi sui limiti]]
