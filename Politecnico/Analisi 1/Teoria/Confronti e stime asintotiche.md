---
tags:
  - analisi1
  - successioni
  - limiti
  - asintotici
  - politecnico
---
Prosegue da [[Successioni monotone, infinitesimi e limiti notevoli]] (vedi in particolare la scala degli infiniti).

Idea: per calcolare un limite non serve conoscere *tutta* la successione, ma solo il suo **comportamento dominante** per $n\to+\infty$. I confronti asintotici rendono preciso cosa significa "dominante" e "trascurabile".

## 1. Confronto tra infiniti

Siano $\{a_n\},\{b_n\}$ due successioni **divergenti** (con $b_n\neq0$).

| Condizione | Significato | Notazione |
|---|---|---|
| $\displaystyle\lim\frac{a_n}{b_n}=0$ | $a_n$ è un infinito di **ordine inferiore** a $b_n$ | $a_n=o(b_n)$ |
| $\displaystyle\lim\frac{a_n}{b_n}=\ell\in\mathbb R\setminus\{0\}$ | $a_n,b_n$ hanno **lo stesso ordine** | |
| $\displaystyle\lim\frac{a_n}{b_n}=\pm\infty$ | $a_n$ è un infinito di **ordine superiore** a $b_n$ | $b_n=o(a_n)$ |
| il limite $\dfrac{a_n}{b_n}$ **non esiste** | $a_n,b_n$ **non confrontabili** | |

Intuizione: il rapporto misura "chi vince la corsa verso $\infty$". Se il rapporto tende a $0$ il denominatore è molto più veloce.

**Gerarchia fondamentale** ($a>1,\ \gamma>0,\ b>0$):
$$(\log_a n)^\gamma\ \ll\ n^b\ \ll\ \alpha^n\ \ll\ n!\ \ll\ n^n\qquad(\alpha>1)$$

## 2. Confronto tra infinitesimi

Siano $\{a_n\},\{b_n\}$ **infinitesime** con $b_n\neq0$ definitivamente.

- $\dfrac{a_n}{b_n}\to0$: $a_n$ è un infinitesimo di **ordine superiore** a $b_n$ (tende a $0$ *più in fretta*);
- $\dfrac{a_n}{b_n}\to\ell\in\mathbb R\setminus\{0\}$: **stesso ordine**;
- $\dfrac{a_n}{b_n}\to\pm\infty$: ordine **inferiore**;
- $\nexists\lim\dfrac{a_n}{b_n}$: **non paragonabili**.

> [!warning] Le parole si invertono
> Per gli **infiniti** $a_n/b_n\to0$ significa "ordine *inferiore*"; per gli **infinitesimi** la stessa condizione significa "ordine *superiore*". In entrambi i casi $a_n=o(b_n)$: ciò che conta è la formula, non l'aggettivo.

**Esempio.** $a_n=\dfrac1{n^2}$, $b_n=\dfrac1n$, entrambe $\to0$.
$$\frac{a_n}{b_n}=\frac{1/n^2}{1/n}=\frac1n\to0\ \Rightarrow\ a_n \text{ è un infinitesimo di ordine superiore a } b_n .$$

## 3. Equivalenza asintotica e "o piccolo"

**Definizione (equivalenza asintotica).** $\{a_n\}$ è **asintotica** (o asintoticamente equivalente) a $\{b_n\}$, e si scrive $a_n\sim b_n$, se
$$\lim_{n\to\infty}\frac{a_n}{b_n}=1 .$$

**Definizione (o piccolo, notazione di Landau).** $a_n=o(b_n)$ ("$a_n$ è un $o$-piccolo di $b_n$") se
$$\lim_{n\to\infty}\frac{a_n}{b_n}=0 .$$

**Collegamento fondamentale.**
$$a_n\sim b_n\iff a_n=b_n+o(b_n)\iff\lim\frac{a_n-b_n}{b_n}=0 .$$
*Dimostrazione.* $\dfrac{a_n-b_n}{b_n}=\dfrac{a_n}{b_n}-1$, che tende a $0$ se e solo se $\dfrac{a_n}{b_n}\to1$. ∎

Leggi: "$a_n$ è uguale a $b_n$ più un errore trascurabile *rispetto a $b_n$*".

**Gerarchia in notazione $o$** ($b>0,\ \gamma>0,\ \alpha>1$):
- $(\log_\alpha n)^\gamma=o(n^b)$ — infatti $\dfrac{(\log_\alpha n)^\gamma}{n^b}\to0$;
- $n^b=o(\alpha^n)$;
- $\alpha^n=o(n!)$;
- $n!=o(n^n)$.

## 4. Proprietà di $\sim$

$\sim$ è una **relazione di equivalenza**:
- **riflessiva**: $a_n\sim a_n$;
- **simmetrica**: $a_n\sim b_n\Rightarrow b_n\sim a_n$;
- **transitiva**: $a_n\sim b_n,\ b_n\sim c_n\Rightarrow a_n\sim c_n$.

(Seguono dalle proprietà del limite del rapporto: p.es. transitività da $\frac{a_n}{c_n}=\frac{a_n}{b_n}\cdot\frac{b_n}{c_n}\to1\cdot1$.)

**Compatibilità con le operazioni.** Se $a_n\sim a_n'$ e $b_n\sim b_n'$ (con $b_n,b_n'\neq0$ definitivamente):

| Operazione | Vale? | Perché |
|---|---|---|
| prodotto: $a_nb_n\sim a_n'b_n'$ | Sì | $\frac{a_nb_n}{a_n'b_n'}=\frac{a_n}{a_n'}\frac{b_n}{b_n'}\to1$ |
| quoziente: $\frac{a_n}{b_n}\sim\frac{a_n'}{b_n'}$ | Sì | idem |
| potenza: $(a_n)^\alpha\sim(a_n')^\alpha$, $\alpha\in\mathbb R$ | Sì | (per $a_n,a_n'>0$ definitivamente) |
| somma/differenza: $a_n\pm b_n\sim a_n'\pm b_n'$ | No | possibili cancellazioni |
| esponenziale: $e^{a_n}\sim e^{a_n'}$ | No | l'errore additivo diventa moltiplicativo |
| $a_n^{b_n}\sim(a_n')^{b_n'}$ | No | idem |

**Controesempi.**
- Somma: $n+1\sim n$ e $-n\sim-n$, ma $(n+1)+(-n)=1\not\sim0=n+(-n)$.
- Esponenziale: $n+1\sim n$, ma $\dfrac{e^{n+1}}{e^n}=e\not\to1$.

**Osservazione (cosa può fare $a_n\sim a_n'$).** Se $a_n\sim a_n'$ si verifica **una** di queste:
1. entrambe convergono allo stesso $\ell\in\mathbb R$ (anche $\ell=0$, p.es. $\frac1n\sim\frac1n$);
2. entrambe divergono con lo **stesso segno**;
3. sono entrambe irregolari.

Quindi $\sim$ **conserva il comportamento** (convergenza, divergenza): per questo si può sostituire un'espressione con una più semplice equivalente per calcolare un limite.

**Nota.** $a_n\sim b_n\Rightarrow a_n-b_n=o(b_n)$ (non $o(1)$ in generale!).

## 5. Algebra degli $o$ piccolo

Per $c\in\mathbb R\setminus\{0\}$:
- $o(a_n)=-o(a_n)$ e $o(a_n)+o(a_n)=o(a_n)$ (il segno e il numero di addendi non contano);
- $c\cdot o(a_n)=o(c\,a_n)=o(a_n)$;
- $a_n\cdot o(b_n)=o(a_nb_n)$;
- se $b_n=o(a_n)$ allora $o(a_n)+o(b_n)=o(a_n)$ — **domina il più grande**.

Esempi:
- $o\!\left(\tfrac1n\right)+o\!\left(\tfrac1{n^2}\right)=o\!\left(\tfrac1n\right)$;
- $o(n)+o(n^2)=o(n^2)$.

*Dimostrazione del secondo (schema).* Se $x_n/n\to0$ e $y_n/n^2\to0$ allora $\dfrac{x_n+y_n}{n^2}=\dfrac{x_n}{n}\cdot\dfrac1n+\dfrac{y_n}{n^2}\to0$. ∎

## 6. Equivalenze notevoli ($n\to+\infty$)

Dai limiti notevoli, con $\varepsilon_n\to0$:

| Equivalenza | Forma con $o$ |
|---|---|
| $\sin\frac1n\sim\frac1n$ | $\sin\frac1n=\frac1n+o\!\left(\frac1n\right)$ |
| $e^{1/n}-1\sim\frac1n$ | $e^{1/n}=1+\frac1n+o\!\left(\frac1n\right)$ |
| $\log\!\left(1+\frac1n\right)\sim\frac1n$ | $\log(1+\frac1n)=\frac1n+o\!\left(\frac1n\right)$ |

In generale $\sin\varepsilon_n\sim\varepsilon_n$, $e^{\varepsilon_n}-1\sim\varepsilon_n$, $\log(1+\varepsilon_n)\sim\varepsilon_n$, $(1+\varepsilon_n)^a-1\sim a\varepsilon_n$.

> [!important] Quando posso usarli
> Solo se l'**argomento è infinitesimo** ($\varepsilon_n\to0$), e **mai** dentro somme/differenze di termini dello stesso ordine (vedi §4): in quei casi serve l'uso esplicito di $o$ (sviluppo) oppure razionalizzazione/raccoglimento.

## 7. Esempi svolti (tutti i passaggi)

### Esempio 1 — polinomi con termini "rumorosi"

$$a_n=\frac{3n^3+2n^2-\sin(n^2)}{5n^3+n+\arctan n}\qquad\text{Calcolare }\lim_{n\to\infty}a_n.$$

**Passo 1 — individuare i termini trascurabili.** Si confronta ogni addendo con la potenza dominante $n^3$.
- $2n^2=o(n^3)$, perché $\dfrac{2n^2}{n^3}=\dfrac2n\to0$;
- $\sin(n^2)=o(n^3)$, perché $\left|\dfrac{\sin(n^2)}{n^3}\right|\le\dfrac1{n^3}\to0$ (seno limitato per 1);
- $n=o(n^3)$, perché $\dfrac n{n^3}=\dfrac1{n^2}\to0$;
- $\arctan n=o(n^3)$, perché $|\arctan n|\le\dfrac\pi2$ e quindi $\left|\dfrac{\arctan n}{n^3}\right|\le\dfrac{\pi}{2n^3}\to0$.

**Passo 2 — usare l'algebra degli $o$** (somma di $o(n^3)$ è $o(n^3)$):
$$a_n=\frac{3n^3+o(n^3)}{5n^3+o(n^3)}.$$

**Passo 3 — raccogliere $n^3$:**
$$a_n=\frac{n^3\left(3+\frac{o(n^3)}{n^3}\right)}{n^3\left(5+\frac{o(n^3)}{n^3}\right)}=\frac{3+o(1)}{5+o(1)}.$$

**Passo 4 — limite.** $o(1)\to0$, quindi $a_n\to\dfrac35$. (Equivalentemente: $a_n\sim\dfrac{3n^3}{5n^3}=\dfrac35$.)

---

### Esempio 2 — radici, seno ed esponenziale

$$a_n=\frac{\left(\sqrt[3]{n+1}-\sqrt[3]{n}\right)\sin\frac1{n^2}}{1-e^{2/n}}$$

**Passo 1 — analisi delle forme.** Il fattore $\sqrt[3]{n+1}-\sqrt[3]{n}$ è una differenza di due infiniti ($\infty-\infty$): sostituire $\sqrt[3]{n+1}\sim\sqrt[3]{n}$ darebbe $\sim0$, che è privo di senso (un'equivalenza non può avere $0$ a denominatore). Va quindi **raccolto**.

**Passo 2 — raccoglimento.**
$$\sqrt[3]{n+1}=n^{1/3}\left(1+\tfrac1n\right)^{1/3}\ \Rightarrow\ \sqrt[3]{n+1}-\sqrt[3]{n}=n^{1/3}\left[\left(1+\tfrac1n\right)^{1/3}-1\right].$$

**Passo 3 — equivalenza notevole** $(1+\varepsilon_n)^{a}-1\sim a\,\varepsilon_n$ con $\varepsilon_n=\frac1n\to0$, $a=\frac13$:
$$\left(1+\tfrac1n\right)^{1/3}-1\sim\frac1{3n}\ \Rightarrow\ \sqrt[3]{n+1}-\sqrt[3]{n}\sim n^{1/3}\cdot\frac1{3n}=\frac13\,n^{-2/3}.$$

**Passo 4 — seno.** $\frac1{n^2}\to0$, quindi $\sin\frac1{n^2}\sim\frac1{n^2}=n^{-2}$.

**Passo 5 — denominatore.** $1-e^{2/n}=-\left(e^{2/n}-1\right)$ e, essendo $\frac2n\to0$, $e^{2/n}-1\sim\frac2n$. Quindi $1-e^{2/n}\sim-\frac2n=-2n^{-1}$.

**Passo 6 — prodotto e quoziente** (qui le equivalenze sono lecite):
$$a_n\sim\frac{\frac13 n^{-2/3}\cdot n^{-2}}{-2n^{-1}}=-\frac16\,n^{-\frac23-2+1}=-\frac16\,n^{-5/3}.$$

**Passo 7 — limite.** L'esponente $-\frac53<0$, quindi $n^{-5/3}\to0$ e, poiché $\sim$ conserva il comportamento, $a_n\to0$ (da valori negativi).

---

### Esempio 3 — composizione di infinitesimi

$$\lim_{n\to\infty}\frac{e^{\sin[\log(1+\frac1n)]}-1}{1/n}.$$

**Passo 1 — numeratore, strato più esterno.** Sia $x_n=\sin\!\left[\log\!\left(1+\frac1n\right)\right]$. Poiché $\frac1n\to0$, $\log(1+\frac1n)\to0$ e $x_n\to0$. Con $\varepsilon_n=x_n\to0$ vale $e^{x_n}-1\sim x_n$.

**Passo 2 — strato intermedio.** $y_n=\log(1+\frac1n)\to0$, quindi $\sin y_n\sim y_n$, cioè $x_n\sim\log(1+\frac1n)$.

**Passo 3 — strato interno.** $\frac1n\to0$, quindi $\log(1+\frac1n)\sim\frac1n$.

**Passo 4 — transitività** di $\sim$:
$$e^{\sin[\log(1+\frac1n)]}-1\sim\sin\!\left[\log\!\left(1+\tfrac1n\right)\right]\sim\log\!\left(1+\tfrac1n\right)\sim\frac1n.$$

**Passo 5 — quoziente.** Il rapporto è $\sim\dfrac{1/n}{1/n}=1$, quindi il limite vale $1$.

---

### Esempio 4 — differenza di radici cubiche ($\infty-\infty$)

$$\lim_{n\to\infty}\left[\left(n^3+n^2\right)^{1/3}-\left(n^3-n^2\right)^{1/3}\right].$$

**Passo 1 — perché non basta $\sim$.** $(n^3\pm n^2)^{1/3}\sim n$ per entrambi, ma sono sottratti: sostituendo si troverebbe "$n-n=0$", che è **falso** (vedi risultato). L'equivalenza perde il termine successivo, che qui è proprio quello che conta.

**Passo 2 — raccoglimento di $n^3$.**
$$\left(n^3\pm n^2\right)^{1/3}=\left[n^3\left(1\pm\tfrac1n\right)\right]^{1/3}=n\left(1\pm\tfrac1n\right)^{1/3}.$$

**Passo 3 — sviluppo con $o$.** Da $(1+\varepsilon)^a-1\sim a\varepsilon$ segue $(1+\varepsilon)^a=1+a\varepsilon+o(\varepsilon)$. Con $a=\frac13$ e $\varepsilon=\pm\frac1n$:
$$\left(1+\tfrac1n\right)^{1/3}=1+\frac1{3n}+o\!\left(\tfrac1n\right),\qquad\left(1-\tfrac1n\right)^{1/3}=1-\frac1{3n}+o\!\left(\tfrac1n\right).$$

**Passo 4 — differenza.**
$$\left(1+\tfrac1n\right)^{1/3}-\left(1-\tfrac1n\right)^{1/3}=\frac2{3n}+o\!\left(\tfrac1n\right)$$
(si usa $o(\frac1n)-o(\frac1n)=o(\frac1n)$).

**Passo 5 — moltiplicare per $n$:**
$$n\left[\frac2{3n}+o\!\left(\tfrac1n\right)\right]=\frac23+n\cdot o\!\left(\tfrac1n\right)=\frac23+o(1)\longrightarrow\frac23.$$

---

### Esempio 5 — logaritmi e combinazione di fattori

$$\lim_{n\to\infty}\frac{n^3\,\left[\log(n^2+7)-2\log n\right]\ \log\!\left(1+\sin\frac1{n^2}\right)}{e^{1/(3n)}-1}.$$

**Passo 1 — il fattore tra parentesi quadre è una differenza** ($\infty-\infty$): non si può sostituire. Si **combinano** i logaritmi:
$$\log(n^2+7)-2\log n=\log(n^2+7)-\log n^2=\log\frac{n^2+7}{n^2}=\log\!\left(1+\frac7{n^2}\right).$$

**Passo 2 — equivalenza.** $\frac7{n^2}\to0$, quindi $\log\!\left(1+\frac7{n^2}\right)\sim\dfrac7{n^2}$.

**Passo 3 — secondo logaritmo.** $\sin\frac1{n^2}\to0$, quindi $\log\!\left(1+\sin\frac1{n^2}\right)\sim\sin\frac1{n^2}$; inoltre $\sin\frac1{n^2}\sim\frac1{n^2}$. Per transitività $\log\!\left(1+\sin\frac1{n^2}\right)\sim\dfrac1{n^2}$.

**Passo 4 — denominatore.** $\frac1{3n}\to0$, quindi $e^{1/(3n)}-1\sim\dfrac1{3n}$.

**Passo 5 — prodotto e quoziente.**
$$\text{rapporto}\ \sim\ \frac{n^3\cdot\frac7{n^2}\cdot\frac1{n^2}}{\frac1{3n}}=\frac{\frac7n}{\frac1{3n}}=\frac7n\cdot3n=21.$$

**Passo 6 — limite.** Il rapporto è equivalente alla costante $21$, quindi converge a $21$.

## Riepilogo operativo

1. Identifica la parte **dominante** di ogni fattore (gerarchia degli infiniti, equivalenze notevoli).
2. Sostituisci con equivalenti **solo** in prodotti, quozienti, potenze.
3. Se compare una **somma/differenza** con possibile cancellazione: raccogli, razionalizza o scrivi gli $o$.
4. Composizioni: dall'interno verso l'esterno, con argomento infinitesimo.

## Collegamenti
- [[Successioni monotone, infinitesimi e limiti notevoli]]
- [[Algebra dei limiti e teoremi sui limiti]]
