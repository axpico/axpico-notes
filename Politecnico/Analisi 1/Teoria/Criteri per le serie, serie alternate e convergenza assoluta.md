---
tags:
  - analisi1
  - serie
  - convergenza
  - politecnico
---
Prosegue da [[Serie numeriche]] (somme parziali, condizione necessaria, serie a termini non negativi, confronto e confronto asintotico).

Idea: il confronto richiede di *trovare* una serie di riferimento. I criteri del **rapporto** e della **radice** la fabbricano da soli: confrontano la serie con una **geometrica** (di cui conosciamo il carattere). Poi si esce dal mondo $a_n\ge0$: **serie alternate** (Leibniz) e **convergenza assoluta**, che riporta il caso generale a quello dei termini non negativi.

## 1. Criterio del rapporto

**Teorema.** Sia $\{a_n\}$ con $a_n>0\ \ \forall n\in\mathbb N$ e supponiamo che esista
$$\lim_{n\to\infty}\frac{a_{n+1}}{a_n}=:\ell\in[0,+\infty]. $$
1. Se $\ell<1\ \Rightarrow\ \displaystyle\sum_{n=1}^{\infty}a_n$ **converge**.
2. Se $\ell>1\ \Rightarrow\ \displaystyle\sum_{n=1}^{\infty}a_n$ **diverge**.

> [!info] Osservazione
> Nel caso 2 vale di più: la serie diverge perché $a_n\not\to0$ (il termine generale **non è infinitesimo**), quindi la condizione necessaria di convergenza non è soddisfatta.

*Dimostrazione.*

**(i) $\ell<1$.** Scelgo $x\in(\ell,1)$ e pongo $\delta:=x-\ell>0$. Per la definizione di limite (con $\varepsilon=\delta$)
$$\exists\,\bar n\in\mathbb N:\quad \frac{a_{n+1}}{a_n}<\ell+\delta=x\qquad\forall n>\bar n,$$
cioè definitivamente $a_{n+1}<x\,a_n$. Iterando:
$$a_{\bar n+1}<x\,a_{\bar n},\qquad a_{\bar n+2}<x\,a_{\bar n+1}<x^2a_{\bar n},\qquad\dots,\qquad a_{\bar n+k}<a_{\bar n}\,x^{k}.$$
Quindi, definitivamente, $a_n< b_n:=a_{\bar n}\,x^{\,n-\bar n}=\big(a_{\bar n}x^{-\bar n}\big)\,x^n$, dove $a_{\bar n}x^{-\bar n}$ è una **costante**. Allora
$$\sum b_n=\text{cost.}\cdot\sum x^n\ \text{ converge perché }x\in(\ell,1)\subset(0,1)$$
(serie geometrica di ragione $x<1$, vedi [[Serie numeriche]] §3). Per il **criterio del confronto** ($0<a_n<b_n$ definitivamente) anche $\sum a_n$ converge.

**(ii) $\ell>1$.** Scelgo $\varepsilon:=\ell-1>0$ (se $\ell=+\infty$ un $\varepsilon$ qualunque, ad es. $\varepsilon=1$ con soglia $2$). Esiste $\bar n$ tale che
$$\ell-\varepsilon<\frac{a_{n+1}}{a_n}\ \Longrightarrow\ \frac{a_{n+1}}{a_n}>1\qquad\forall n>\bar n,$$
cioè $a_{n+1}>a_n$ definitivamente: la successione è **crescente** e positiva, quindi $a_n\ge a_{\bar n+1}>0$ e **non può essere infinitesima**. Ma per la condizione necessaria, se la serie convergesse sarebbe $a_n\to0$: assurdo. Essendo $a_n>0$ la serie è regolare, quindi $\sum a_n=+\infty$. $\blacksquare$

> [!warning] Il caso $\ell=1$ non decide
> Il criterio è **inconcludente** per $\ell=1$: $\sum\frac1n$ (diverge) e $\sum\frac1{n^2}$ (converge) hanno entrambe rapporto $\to1$. Serve un altro criterio (confronto asintotico con $\frac1{n^\alpha}$, ecc.).
> Inoltre, se il limite del rapporto **non esiste** non si può applicare il criterio.

> [!tip] Quando usarlo
> Funziona bene con fattoriali ed esponenziali ($n!$, $a^n$), perché nel rapporto si semplificano quasi tutti i fattori.

### Esempi

**1)** $\displaystyle\sum_{n=1}^{+\infty}\frac1{n!}$, $\ a_n=\frac1{n!}>0$.
$$\frac{a_{n+1}}{a_n}=\frac{1}{(n+1)!}\cdot\frac{n!}{1}=\frac1{n+1}\xrightarrow{n\to\infty}0\ (=\ell<1).$$
Per il criterio del rapporto la serie **converge**.

## 2. Criterio della radice

**Teorema.** Sia $a_n\ge0\ \ \forall n\in\mathbb N$ e supponiamo che esista
$$\lim_{n\to\infty}\sqrt[n]{a_n}=:\ell\in[0,+\infty].$$
1. Se $\ell<1\ \Rightarrow\ \sum a_n$ **converge**.
2. Se $\ell>1\ \Rightarrow\ \sum a_n$ **diverge**.

*Idea della dimostrazione* (stessa struttura del rapporto). Se $\ell<1$, scelto $x\in(\ell,1)$, definitivamente $\sqrt[n]{a_n}<x$, cioè $a_n<x^n$: confronto con la geometrica di ragione $x<1$. Se $\ell>1$, definitivamente $\sqrt[n]{a_n}>1$, cioè $a_n>1$: il termine generale non è infinitesimo e la serie diverge.

> [!warning] Anche qui $\ell=1$ non decide.

### Esempio

$\displaystyle\sum_{n=1}^{+\infty}\frac n{3^n}$, $\ a_n=\frac n{3^n}$:
$$\sqrt[n]{a_n}=\sqrt[n]{\frac n{3^n}}=\frac{\sqrt[n]{n}}{3}\xrightarrow{n\to\infty}\frac13\ (=\ell<1),$$
perché $\sqrt[n]n\to1$ (limite notevole, vedi [[Successioni monotone, infinitesimi e limiti notevoli]]). Per il criterio della radice la serie **converge**.

> [!info] Rapporto vs radice
> Se esiste $\lim\frac{a_{n+1}}{a_n}=\ell$ allora esiste anche $\lim\sqrt[n]{a_n}=\ell$ (stesso valore): la radice è quindi **almeno altrettanto potente** del rapporto. Il rapporto però è spesso più comodo da calcolare (fattoriali), la radice quando compaiono potenze $n$-esime.

## 3. Serie alternate

Una serie è **a segni alterni** (a valori di segno alterno) se si scrive
$$\sum_{n=0}^{+\infty}(-1)^n a_n,\qquad a_n>0\ \ \forall n.$$

**Teorema (criterio di Leibniz).** Sia $\{a_n\}$ una successione con
- $a_n>0\ \ \forall n\in\mathbb N$;
- $a_n\xrightarrow{n\to\infty}0$ (infinitesima);
- $a_n$ **decrescente**.

Allora $\displaystyle\sum_{n=1}^{\infty}(-1)^n a_n$ è **convergente**.

Inoltre vale la **stima dell'errore**
$$|S_n-S|\le a_{n+1},$$
dove $S_n$ sono le somme parziali e $S=\lim S_n$ è la somma della serie.

> [!note] Perché funziona (idea)
> Le somme parziali pari e dispari "oscillano" attorno a $S$ con ampiezza che diminuisce: le pari sono monotone in un verso, le dispari nell'altro, e la distanza tra le due sottosuccessioni è $a_{n+1}\to0$. L'errore commesso fermandosi a $S_n$ è quindi al più il **primo termine trascurato**.

> [!warning] Le tre ipotesi servono tutte
> Soprattutto la **monotonia**: non basta $a_n\to0$. E Leibniz dà solo la convergenza **semplice**: nulla sulla convergenza assoluta.

### Esempi

**1)** $\displaystyle\sum_{n=1}^{\infty}\frac{(-1)^n}{n}$, $\ a_n=\frac1n$.
- $a_n>0$ perché $\frac1n>0\ \forall n\in\mathbb N$;
- $a_n\to0$ (infinitesima);
- $\frac1{n+1}<\frac1n\iff n<n+1$ $\forall n$: decrescente.

Per il teorema di Leibniz la serie **converge**.

**2)** $\displaystyle\sum_{n=1}^{\infty}(-1)^n\arctan\!\left(\frac1{\sqrt n}\right)$, $\ a_n=\arctan\!\left(\frac1{\sqrt n}\right)$. Uso Leibniz perché è una serie alternata.
- $a_n>0$ $\forall n$ (l'arcotangente di un numero positivo è positiva);
- $a_n\to0$: $\arctan\frac1{\sqrt n}\to\arctan0=0$;
- $a_n$ decrescente: $a_{n+1}<a_n\iff\arctan\frac1{\sqrt{n+1}}<\arctan\frac1{\sqrt n}$. Vera, si confrontano gli **argomenti** perché $\arctan$ è **crescente** e quindi conserva l'ordine:
$$\frac1{\sqrt{n+1}}<\frac1{\sqrt n}\iff\sqrt{n+1}>\sqrt n .$$

Per Leibniz la serie **converge**.

## 4. Convergenza assoluta

**Definizione.** Sia $\{a_n\}$ una successione (di segno qualunque). Si dice che
$$\sum_{n=1}^{\infty}a_n\ \text{ converge assolutamente}\quad\text{se}\quad\sum_{n=1}^{\infty}|a_n|\ \text{ converge.}$$
(Altrimenti "convergere" nel senso di §[[Serie numeriche]] 1 si dice anche **convergenza semplice**.)

**Teorema.** Una serie assolutamente convergente è anche convergente (semplicemente):
$$\text{convergenza assoluta}\ \Longrightarrow\ \text{convergenza semplice}.$$

*Dimostrazione.* Supponiamo $\sum|a_n|<+\infty$. Per ogni $n$
$$-|a_n|\le a_n\le|a_n|\quad\Longrightarrow\quad 0\le a_n+|a_n|\le2|a_n|\qquad\forall n\in\mathbb N .$$
- $a_n+|a_n|\ge0$: la serie $\sum(a_n+|a_n|)$ è a **termini non negativi**, quindi si può applicare il criterio del confronto.
- $a_n+|a_n|\le2|a_n|$, e $\sum2|a_n|=2\sum|a_n|<+\infty$ per ipotesi (linearità).

Per il **criterio del confronto**, $\sum(a_n+|a_n|)$ converge. Infine
$$\sum_{n=1}^{\infty}a_n=\sum_{n=1}^{\infty}\Big(\underbrace{a_n+|a_n|}_{\text{converge}}-\underbrace{|a_n|}_{\text{converge}}\Big)$$
è differenza di due serie convergenti, quindi converge (**algebra dei limiti**/linearità di §6 di [[Serie numeriche]]). $\blacksquare$

> [!warning] Il viceversa è falso
> La convergenza semplice **non** implica quella assoluta. Esempio: $\displaystyle\sum_{n=1}^{\infty}\frac{(-1)^n}{n}$ converge (Leibniz) ma
> $$\sum_{n=1}^{\infty}\left|\frac{(-1)^n}{n}\right|=\sum_{n=1}^{\infty}\frac1n\ \text{ è la serie armonica, che diverge.}$$
> Una serie che converge semplicemente ma non assolutamente si dice **condizionatamente convergente**.

> [!tip] Strategia
> Per una serie con segni qualunque: studio prima $\sum|a_n|$ con i criteri per i termini $\ge0$ (confronto, rapporto, radice). Se converge, ho finito. Se diverge, provo Leibniz (se alternata) o altri argomenti.

## 5. Esercizio riepilogativo (con parametro)

**Studiare il carattere della serie**
$$\sum_{n=1}^{\infty}\frac{(\tan\alpha)^n}{n^2}\log n\qquad\text{al variare di }\alpha\in\left(-\frac\pi2,\frac\pi2\right).$$

La funzione $\tan$ è crescente su $\left(-\frac\pi2,\frac\pi2\right)$ con $\tan(\pm\frac\pi4)=\pm1$: i valori $\alpha=\pm\frac\pi4$ separano i casi $|\tan\alpha|<1$, $=1$, $>1$.

**Passo 1: condizione necessaria.** $a_n=\dfrac{(\tan\alpha)^n}{n^2}\log n$.

- **$\tan\alpha>1\iff\alpha>\frac\pi4$.** L'esponenziale batte il polinomio: $\lim a_n=+\infty$. Il termine generale non è infinitesimo, la serie non converge; essendo $a_n>0$ **diverge positivamente** $\ \forall\alpha\in\left(\frac\pi4,\frac\pi2\right)$.
- **$\tan\alpha<-1\iff\alpha<-\frac\pi4$.** Il fattore $(\tan\alpha)^n=(-1)^n|\tan\alpha|^n$ cambia segno e $|a_n|\to+\infty$, quindi $\nexists\lim a_n$ (in particolare $a_n\not\to0$): la serie **non converge** (è indeterminata).

**Passo 2: $-\frac\pi4<\alpha<\frac\pi4$.** Qui $|\tan\alpha|<1$ e $(\tan\alpha)^n$ è infinitesimo, quindi
$$\lim a_n=\lim\frac{(\tan\alpha)^n\log n}{n^2}=0$$
(condizione necessaria soddisfatta, ma **non basta**). Studio la **convergenza assoluta**:
$$\sum|a_n|=\sum\frac{|\tan\alpha|^n\log n}{n^2},\qquad\text{serie a termini non negativi.}$$
Applico il **criterio del rapporto**:
$$\lim_{n\to\infty}\frac{|a_{n+1}|}{|a_n|}=\lim_{n\to\infty}|\tan\alpha|\cdot\frac{n^2}{(n+1)^2}\cdot\frac{\log(n+1)}{\log n}=|\tan\alpha|<1,$$
perché $\frac{n^2}{(n+1)^2}\to1$ e $\frac{\log(n+1)}{\log n}\to1$. Quindi $\sum|a_n|<+\infty$: la serie **converge assolutamente**, dunque converge.

**Passo 3: gli estremi $\alpha=\pm\frac\pi4$.** Qui $|\tan\alpha|=1$ e il rapporto $\to1$ non decide: si studia a parte.

- **$\alpha=\frac\pi4$** ($\tan\alpha=1$): $\displaystyle\sum_{n=1}^{\infty}\frac{\log n}{n^2}$, termini $\ge0$. Scelgo $p$ con $1<p<2$ e $b_n=\frac1{n^p}$ (serie armonica generalizzata **convergente**):
$$\lim_{n\to\infty}\frac{\log n/n^2}{1/n^p}=\lim_{n\to\infty}\frac{\log n}{n^{2-p}}=0\qquad(2-p>0,\ \text{il logaritmo è dominato da ogni potenza}).$$
Per il **confronto asintotico** ($a_n=o(b_n)$, $\sum b_n$ converge) la serie **converge**.
- **$\alpha=-\frac\pi4$** ($\tan\alpha=-1$): $\displaystyle\sum_{n=1}^{\infty}(-1)^n\frac{\log n}{n^2}$. Converge **assolutamente** perché $\sum\left|(-1)^n\frac{\log n}{n^2}\right|=\sum\frac{\log n}{n^2}$ è la serie appena studiata. (In alternativa si può usare Leibniz.)

**Conclusione.**
$$\begin{array}{c|c}
\alpha & \text{carattere}\\\hline
\left(-\frac\pi2,-\frac\pi4\right) & \text{non converge (}a_n\text{ non ha limite, indeterminata)}\\
\left[-\frac\pi4,\frac\pi4\right] & \text{converge (assolutamente)}\\
\left(\frac\pi4,\frac\pi2\right) & \text{diverge a }+\infty
\end{array}$$

> [!tip] Schema mentale
> 1. condizione necessaria ($a_n\to0$?); 2. convergenza assoluta con rapporto/radice/confronto; 3. casi di confine studiati **a mano**; 4. se assoluta fallisce e la serie è alternata, Leibniz.

## Riepilogo

| Strumento | Ipotesi | Conclusione |
|---|---|---|
| **Rapporto** | $a_n>0$, $\frac{a_{n+1}}{a_n}\to\ell$ | $\ell<1$ converge; $\ell>1$ diverge; $\ell=1$ ? |
| **Radice** | $a_n\ge0$, $\sqrt[n]{a_n}\to\ell$ | $\ell<1$ converge; $\ell>1$ diverge; $\ell=1$ ? |
| **Leibniz** | $\sum(-1)^na_n$, $a_n>0$, $a_n\downarrow0$ | converge, $\lvert S_n-S\rvert\le a_{n+1}$ |
| **Convergenza assoluta** | $\sum\lvert a_n\rvert<\infty$ | $\sum a_n$ converge (non vale il viceversa) |

## Collegamenti
- [[Serie numeriche]]
- [[Successioni monotone, infinitesimi e limiti notevoli]]
- [[Confronti e stime asintotiche]]
- Dimostrazioni: 3.6 (rapporto) e 3.7 (assoluta ⟹ semplice) in [[Indice Dimostrazioni]]
