---
tags:
  - analisi1
  - ripasso
  - esame
---
# Ripasso prima prova in itinere — Analisi 1

Basato sulle 5 prime prove presenti nel vault (2018, 2022, 2023, 2024, 2025) e sul [[Programma di massima e bibliografia.pdf|programma 2026/27]]. Indici: [[Politecnico/Analisi 1/Indice|Indice]] · [[Indice Dimostrazioni|Indice Dimostrazioni]] · [[Formulario AM1 - asintotici.pdf|Formulario asintotici]]

> [!warning] Da verificare
> Le prove del 2024 e del 2025 sono del prof. Punzo, mentre il programma 2026/27 è della prof.ssa Meglioli. Controlla sul sito del corso argomenti, durata, formato e se il formulario è ammesso. Queste prove arrivano fino alle serie, quindi questo ripasso copre le sezioni 1-3.

## 1. Come è fatta la prova

Struttura delle prove 2023-2025 (totale 32 punti):

| Parte | 2023 | 2024 | 2025 |
|---|---|---|---|
| Risposta multipla | 4 domande, 10 pt | 6 domande, 10 pt | 5 domande, 10 pt |
| Teoria | 8 pt, una dimostrazione da 5 | 10 pt, una dimostrazione da 6 | 10 pt, una dimostrazione da 6 |
| Esercizi | 14 pt: complessi + serie | 12 pt: serie con parametro | 12 pt: serie con parametro |

## 2. Cosa esce più spesso

| Argomento | Prove | Anni |
|---|---|---|
| Serie con parametro | 5/5 | 2018, 2022, 2023, 2024, 2025 |
| Sup/inf di un insieme definito da una disequazione | 5/5 | 2018, 2022, 2023, 2024, 2025 |
| Equazioni complesse | 5/5 | 2018, 2022, 2023, 2024, 2025 |
| Carattere o somma di una serie senza parametro | 5/5 | 2018, 2022, 2023, 2024, 2025 |
| Limiti con asintotici | 4/5 | 2018, 2022, 2024, 2025 |
| Definizioni | 4/5 | 2022, 2023, 2024, 2025 |
| Dimostrazione o controesempio | 4/5 | 2022, 2023, 2024, 2025 |
| Vero/falso sui limiti | 3/5 | 2018, 2022, 2023 |
| Divisione $\frac zw$ | 2/5 | 2024, 2025 |
| Funzioni: iniettività, grafici trasformati | 1/5 | 2018 |

**Priorità:**
1. Serie con parametro: vale da sola circa un terzo del punteggio.
2. Permanenza del segno, carabinieri, condizione necessaria e definizioni.
3. Complessi: $z^n=w$, equazioni a fattori, trasformazioni come $iz$.
4. Sup/inf con disequazioni irrazionali e limiti con asintotici.
5. Tutte le altre dimostrazioni ★.

## 3. Definizioni da saper scrivere

**Maggiorante.** $M$ è un maggiorante di $E\subset\mathbb R$ se $x\le M$ per ogni $x\in E$.

**Limitato superiormente.** $E$ ha almeno un maggiorante. Esempi: $(-\infty,1]$ lo è, $\mathbb N$ no.

**Estremo superiore.** $\sup E$ è il minimo dei maggioranti. Se $E$ è non vuoto e limitato superiormente, $L=\sup E$ equivale a:
- $x\le L$ per ogni $x\in E$;
- $\forall\varepsilon>0\ \exists x\in E:\ x>L-\varepsilon$.

Se $E$ non è limitato superiormente, $\sup E=+\infty$.

**Massimo.** $M=\max E$ se $M$ è un maggiorante e $M\in E$.

**Limite finito.** $\displaystyle\lim_{n\to\infty}a_n=l$ se $\forall\varepsilon>0\ \exists N:\ \forall n\ge N,\ |a_n-l|<\varepsilon$.

**Limite infinito.** $\displaystyle\lim_{n\to\infty}a_n=+\infty$ se $\forall M>0\ \exists N:\ \forall n\ge N,\ a_n>M$.

**Equivalenza asintotica.** $a_n\sim b_n$ se $\dfrac{a_n}{b_n}\to1$. Esempio: $n^2+n\sim n^2$.

**Infinito di ordine superiore.** Se $a_n,b_n$ divergono, $a_n$ ha ordine superiore a $b_n$ se $\dfrac{a_n}{b_n}\to\pm\infty$, cioè $\left|\dfrac{b_n}{a_n}\right|\to0$. Esempio: $n^2$ rispetto a $n$.

**o-piccolo.** $a_n=o(b_n)$ se $\dfrac{a_n}{b_n}\to0$.

**Carattere di una serie.** Con $s_n=\sum_{k\le n}a_k$, la serie converge, diverge o è irregolare se $s_n$ ha limite finito, ha limite infinito o non ha limite.

**Convergenza assoluta.** $\sum a_n$ converge assolutamente se $\sum|a_n|$ converge.

## 4. Dimostrazioni

Qui ci sono per intero tutte le 24 dimostrazioni della prima parte. Per lo scritto servono le 14 ★, le altre 10 ★★ sono richieste solo per l'orale.

### Già uscite

#### Permanenza del segno (★) — uscita nel 2023 e nel 2025
[[2.4 Permanenza del segno (★)]]

**Enunciato.** Se $a_n\to L>0$ (anche $L=+\infty$), allora $a_n>0$ definitivamente.

**Dimostrazione.** Se $L$ è finito, prendo $\varepsilon=\frac L2$: esiste $N$ tale che per $n\ge N$ vale $|a_n-L|<\frac L2$, quindi $a_n>L-\frac L2=\frac L2>0$. Se $L=+\infty$, prendo $M=1$: definitivamente $a_n>1>0$. $\blacksquare$

#### Teorema dei due carabinieri (★) — uscito nel 2024
[[2.6 Teorema del confronto (due carabinieri) (★)]]

**Enunciato.** Se $a_n\le c_n\le b_n$ definitivamente e $a_n,b_n\to L$, allora $c_n\to L$.

**Dimostrazione.** Fissato $\varepsilon>0$, definitivamente valgono $a_n>L-\varepsilon$, $b_n<L+\varepsilon$ e $a_n\le c_n\le b_n$. Quindi
$$L-\varepsilon<a_n\le c_n\le b_n<L+\varepsilon,$$
cioè $|c_n-L|<\varepsilon$. $\blacksquare$

#### Condizione necessaria di convergenza (★) — uscita nel 2022
[[3.1 Condizione necessaria di convergenza (★)]]

**Enunciato.** Se $\sum a_n$ converge a $S$, allora $a_n\to0$.

**Dimostrazione.** $a_n=s_n-s_{n-1}\to S-S=0$. $\blacksquare$

**Non è sufficiente.** Controesempio: $\frac1n\to0$, ma $\sum\frac1n$ diverge.

#### Limitata per infinitesima — uscita nel 2023
Non ha asterisco nel programma attuale, ma è già stata chiesta con dimostrazione.

**Enunciato.** Se $|a_n|\le M$ e $b_n\to0$, allora $a_nb_n\to0$.

**Dimostrazione.** $0\le|a_nb_n|\le M|b_n|\to0$, quindi $|a_nb_n|\to0$ per i carabinieri. Poiché $-|a_nb_n|\le a_nb_n\le|a_nb_n|$, i carabinieri danno $a_nb_n\to0$. $\blacksquare$

### Le altre ★

#### $\sqrt2$ è irrazionale
[[1.2 √2 è irrazionale (★)]]

Per assurdo $\sqrt2=\frac pq$ ridotta ai minimi termini. Allora $p^2=2q^2$ è pari, quindi $p$ è pari: $p=2k$. Sostituendo, $4k^2=2q^2$, cioè $q^2=2k^2$ è pari, quindi $q$ è pari. Allora $p,q$ hanno il fattore comune $2$: assurdo. $\blacksquare$

#### Disuguaglianza di Bernoulli
[[1.4 Disuguaglianza di Bernoulli (★)]]

**Enunciato.** Per $x>-1$ e $n\in\mathbb N$: $(1+x)^n\ge1+nx$.

**Dimostrazione (induzione).** Per $n=0$: $1\ge1$. Se vale per $n$, moltiplico per $1+x>0$:
$$(1+x)^{n+1}\ge(1+nx)(1+x)=1+(n+1)x+nx^2\ge1+(n+1)x.\ \blacksquare$$

#### De Moivre
[[1.7 Formule di de Moivre - prodotto e potenze (★)]]

**Prodotto.**
$$z_1z_2=r_1r_2\big[(\cos\theta_1\cos\theta_2-\sin\theta_1\sin\theta_2)+i(\sin\theta_1\cos\theta_2+\cos\theta_1\sin\theta_2)\big]=r_1r_2\big[\cos(\theta_1+\theta_2)+i\sin(\theta_1+\theta_2)\big].$$

**Potenza (induzione).** Per $n=1$ è ovvia. Se vale per $n$, applico la formula del prodotto a $z^n\cdot z$:
$$z^{n+1}=r^{n+1}\big[\cos((n+1)\theta)+i\sin((n+1)\theta)\big].\ \blacksquare$$

#### Radici $n$-esime
[[1.8 Radici n-esime di un numero complesso (★)]]

**Enunciato.** Se $z=\rho(\cos\varphi+i\sin\varphi)\ne0$, allora $w^n=z$ ha esattamente $n$ soluzioni:
$$w_k=\sqrt[n]\rho\left[\cos\frac{\varphi+2k\pi}n+i\sin\frac{\varphi+2k\pi}n\right],\quad k=0,\dots,n-1.$$

**Dimostrazione.** Sia $w=s(\cos\alpha+i\sin\alpha)$. Per de Moivre, $w^n=s^n(\cos n\alpha+i\sin n\alpha)$. L'uguaglianza con $z$ equivale a $s^n=\rho$ e $n\alpha=\varphi+2k\pi$, cioè $s=\sqrt[n]\rho$ e $\alpha_k=\frac{\varphi+2k\pi}n$. Per $k=0,\dots,n-1$ gli angoli differiscono per meno di $2\pi$, quindi i punti sono distinti. Inoltre $\alpha_{k+n}=\alpha_k+2\pi$, quindi gli altri $k$ ripetono gli stessi punti. $\blacksquare$

#### Unicità del limite
[[2.1 Unicità del limite (★)]]

Per assurdo $a_n\to L_1$ e $a_n\to L_2$ con $L_1\ne L_2$. Sia $\varepsilon=\frac{|L_1-L_2|}2$. Per $n$ grande, $|a_n-L_1|<\varepsilon$ e $|a_n-L_2|<\varepsilon$, quindi
$$|L_1-L_2|\le|L_1-a_n|+|a_n-L_2|<2\varepsilon=|L_1-L_2|.$$
Assurdo. $\blacksquare$

#### Convergente implica limitata
[[2.2 Convergente ⟹ limitata (★)]]

Sia $a_n\to L$. Con $\varepsilon=1$ esiste $N$ tale che $|a_n|\le|a_n-L|+|L|<|L|+1$ per $n\ge N$. Allora $M=\max\{|a_0|,\dots,|a_{N-1}|,|L|+1\}$ soddisfa $|a_n|\le M$ per ogni $n$. $\blacksquare$

#### Regolarità delle successioni monotone
[[2.7 Regolarità delle successioni monotone (★)]]

**Enunciato.** Se $(a_n)$ è crescente, $a_n\to\sup a_n$. Se è decrescente, $a_n\to\inf a_n$.

**Dimostrazione (crescente).** Sia $L=\sup a_n$.
- **$L$ finito:** $L-\varepsilon$ non è un maggiorante, quindi esiste $a_N>L-\varepsilon$. Per $n\ge N$: $L-\varepsilon<a_N\le a_n\le L$.
- **$L=+\infty$:** per ogni $M$ esiste $a_N>M$, quindi $a_n>M$ per $n\ge N$. $\blacksquare$

#### Criterio del confronto
[[3.4 Criterio del confronto (★)]]

**Enunciato.** Se $0\le a_n\le b_n$ definitivamente: $\sum b_n$ convergente implica $\sum a_n$ convergente; $\sum a_n$ divergente implica $\sum b_n$ divergente.

**Dimostrazione.** Le somme parziali verificano $s_n^{(a)}\le s_n^{(b)}+C$. Se $\sum b_n$ converge, $s^{(b)}$ è limitata, quindi lo è anche $s^{(a)}$. Essendo a termini non negativi, $\sum a_n$ converge. La seconda parte è la contrapposizione. $\blacksquare$

#### Criterio del confronto asintotico
[[3.5 Criterio del confronto asintotico (★)]]

**Enunciato.** Se $a_n,b_n>0$ e $\frac{a_n}{b_n}\to\ell\in(0,+\infty)$, le due serie hanno lo stesso carattere.

**Dimostrazione.** Con $\varepsilon=\frac\ell2$, definitivamente $\frac\ell2b_n\le a_n\le\frac{3\ell}2b_n$. Applico il confronto nei due versi: le costanti non cambiano il carattere. $\blacksquare$

#### Criterio del rapporto
[[3.6 Criterio del rapporto (★)]]

**Enunciato.** Se $a_n>0$ e $\frac{a_{n+1}}{a_n}\to\ell$: per $\ell<1$ la serie converge, per $\ell>1$ diverge.

**Dimostrazione.**
- **$\ell<1$:** scelgo $x\in(\ell,1)$. Esiste $\bar n$ con $a_{n+1}<xa_n$ per $n\ge\bar n$. Iterando, $a_{\bar n+k}<a_{\bar n}x^k$. La geometrica di ragione $x<1$ converge, quindi per confronto converge anche $\sum a_n$.
- **$\ell>1$:** definitivamente $a_{n+1}>a_n>0$. La successione è crescente e positiva, quindi non è infinitesima. Per la condizione necessaria la serie non converge e, avendo termini positivi, diverge. $\blacksquare$

Per $\ell=1$ il criterio non decide: $\sum\frac1n$ diverge, $\sum\frac1{n^2}$ converge.

#### Convergenza assoluta implica convergenza semplice
[[3.7 Convergenza assoluta ⟹ convergenza semplice (★)]]

Da $-|a_n|\le a_n\le|a_n|$ segue $0\le a_n+|a_n|\le2|a_n|$. Per confronto, $\sum(a_n+|a_n|)$ converge. Allora $a_n=(a_n+|a_n|)-|a_n|$ è differenza di termini di due serie convergenti, quindi $\sum a_n$ converge. $\blacksquare$

### Le ★★ (solo orale, alcune servono come passaggi)

#### Parità dei quadrati
[[1.1 Parità di quadrati (★★)]] — serve per $\sqrt2$

**Enunciato.** $n$ è pari se e solo se $n^2$ è pari.

**Dimostrazione.** ($\Rightarrow$) Se $n=2k$, allora $n^2=2(2k^2)$ è pari. ($\Leftarrow$) Per contrapposizione: se $n=2k+1$, allora $n^2=4k^2+4k+1=2(2k^2+2k)+1$ è dispari. Quindi $n^2$ pari implica $n$ pari. $\blacksquare$

#### Somma dei primi $n$ naturali
[[1.3 Somma dei primi n naturali (★★)]]

**Enunciato.** $\displaystyle\sum_{k=1}^nk=\frac{n(n+1)}2$.

**Dimostrazione (induzione).** Per $n=1$: $1=\frac{1\cdot2}2$. Se vale per $n$:
$$\sum_{k=1}^{n+1}k=\frac{n(n+1)}2+(n+1)=\frac{(n+1)(n+2)}2.\ \blacksquare$$

#### Somma di una progressione geometrica
[[1.5 Somma di una progressione geometrica (★★)]] — serve per la serie geometrica

**Enunciato.** Per $q\ne1$: $\displaystyle\sum_{k=0}^nq^k=\frac{1-q^{n+1}}{1-q}$.

**Dimostrazione.** Sia $S=\sum_{k=0}^nq^k$. Allora $qS=\sum_{k=1}^{n+1}q^k$. Sottraendo, i termini intermedi si cancellano: $S-qS=1-q^{n+1}$. Divido per $1-q\ne0$. $\blacksquare$

#### Disuguaglianza triangolare
[[1.6 Disuguaglianza triangolare (★★)]] — serve per unicità e limitatezza

**Enunciato.** $|a+b|\le|a|+|b|$ per ogni $a,b\in\mathbb R$.

**Dimostrazione.** Sommando $-|a|\le a\le|a|$ e $-|b|\le b\le|b|$ si ottiene $-(|a|+|b|)\le a+b\le|a|+|b|$. Poiché $|y|\le c\iff-c\le y\le c$, la tesi segue. $\blacksquare$

#### Algebra dei limiti: somma e prodotto
[[2.3 Algebra dei limiti - somma e prodotto (★★)]]

**Enunciato.** Se $a_n\to a$ e $b_n\to b$ finiti, allora $a_n+b_n\to a+b$ e $a_nb_n\to ab$.

**Dimostrazione.**
- **Somma:** fissato $\varepsilon>0$, per $n$ grande $|a_n-a|<\frac\varepsilon2$ e $|b_n-b|<\frac\varepsilon2$. Per la triangolare, $|a_n+b_n-a-b|<\varepsilon$.
- **Prodotto:** aggiungendo e togliendo $a_nb$,
$$|a_nb_n-ab|\le|a_n||b_n-b|+|b||a_n-a|.$$
Una successione convergente è limitata, quindi $|a_n|\le M$. Prendendo per $n$ grande entrambi gli scarti minori di $\frac\varepsilon{M+|b|+1}$, il totale è minore di $\varepsilon$. $\blacksquare$

#### Proprietà del confronto
[[2.5 Proprietà del confronto (★★)]]

**Enunciato.** Se $a_n\to a$, $b_n\to b$ e $a_n\le b_n$ definitivamente, allora $a\le b$.

**Dimostrazione.** $c_n=b_n-a_n\to b-a$ per l'algebra dei limiti, e $c_n\ge0$ definitivamente. Se fosse $b-a<0$, la permanenza del segno applicata a $-c_n$ darebbe $c_n<0$ definitivamente: assurdo. Quindi $b-a\ge0$. $\blacksquare$

#### Limiti notevoli: $a^n$ e $\sqrt[n]a$
[[2.8 Limiti notevoli di potenza e radice n-esima (★★)]] — serve per la serie geometrica

**Enunciato.** (i) $a^n\to+\infty$ se $a>1$, $a^n\to0$ se $|a|<1$. (ii) $\sqrt[n]a\to1$ per ogni $a>0$.

**Dimostrazione.**
- **$a>1$:** per Bernoulli, $a^n=(1+(a-1))^n\ge1+n(a-1)\to+\infty$.
- **$|a|<1$, $a\ne0$:** $|a|^n=\dfrac1{(1/|a|)^n}\to0$. Se $a=0$ è banale.
- **$\sqrt[n]a$ con $a>1$:** sia $h_n=\sqrt[n]a-1>0$. Per Bernoulli, $a=(1+h_n)^n\ge1+nh_n$, quindi $0<h_n\le\frac{a-1}n\to0$. Per i carabinieri, $h_n\to0$.
- **$\sqrt[n]a$ con $a<1$:** $\sqrt[n]a=\dfrac1{\sqrt[n]{1/a}}\to1$. Se $a=1$ è banale. $\blacksquare$

#### Confronto tra infiniti
[[2.9 Confronto tra infiniti (★★)]]

**Criterio del rapporto per successioni.** Se $b_n>0$ e $\frac{b_{n+1}}{b_n}\to\ell<1$, allora $b_n\to0$.

*Dimostrazione.* Scelgo $q\in(\ell,1)$. Definitivamente $b_{n+1}\le qb_n$, quindi $b_n\le b_Nq^{n-N}\to0$.

**Enunciato.** Per $a>1$ e $k>0$: $\frac{n^k}{a^n}\to0$ e $\frac{a^n}{n!}\to0$.

**Dimostrazione.** Applico il criterio ai due rapporti:
$$\frac{(n+1)^k/a^{n+1}}{n^k/a^n}=\frac1a\left(1+\frac1n\right)^k\to\frac1a<1,\qquad\frac{a^{n+1}/(n+1)!}{a^n/n!}=\frac a{n+1}\to0<1.\ \blacksquare$$

#### Carattere delle serie a termini non negativi
[[3.2 Carattere delle serie a termini non negativi (★★)]] — serve per il confronto

**Enunciato.** Se $a_n\ge0$, $\sum a_n$ converge oppure diverge a $+\infty$, e converge se e solo se $(s_n)$ è limitata.

**Dimostrazione.** $s_{n+1}=s_n+a_{n+1}\ge s_n$, quindi $(s_n)$ è crescente. Per la regolarità delle monotone, converge a $\sup s_n$ se è limitata, altrimenti tende a $+\infty$. $\blacksquare$

#### Serie geometrica
[[3.3 Serie geometrica (★★)]] — serve per il rapporto

**Enunciato.** $\sum_{n\ge0}q^n$ converge se e solo se $|q|<1$, con somma $\frac1{1-q}$. Diverge a $+\infty$ se $q\ge1$. È irregolare se $q\le-1$.

**Dimostrazione.** Per $q\ne1$, $s_n=\frac{1-q^{n+1}}{1-q}$.
- $|q|<1$: $q^{n+1}\to0$, quindi $s_n\to\frac1{1-q}$.
- $q>1$: $q^{n+1}\to+\infty$, quindi $s_n\to+\infty$.
- $q=1$: $s_n=n+1\to+\infty$.
- $q\le-1$: $q^{n+1}$ oscilla senza tendere a un limite, quindi $s_n$ non ha limite. $\blacksquare$

## 5. Metodi per gli esercizi

### Serie con parametro
Teoria: [[Serie numeriche]] · [[Criteri per le serie, serie alternate e convergenza assoluta]]

Se la serie ha la forma $\sum q^nb_n$, dove $q$ dipende dal parametro e $b_n>0$ non è esponenziale, dividi in cinque casi:

| Caso | Cosa fare | Risultato tipico |
|---|---|---|
| $\lvert q\rvert<1$ | rapporto su $\lvert a_n\rvert$, che tende a $\lvert q\rvert$ | converge assolutamente |
| $q=1$ | studia $\sum b_n$ con confronto o asintotici | dipende da $b_n$ |
| $q=-1$ | prima $\sum b_n$, poi Leibniz | dipende da $b_n$ |
| $q>1$ | i termini non tendono a $0$ | diverge a $+\infty$ |
| $q<-1$ | i termini oscillano e non tendono a $0$ | irregolare |

Alla fine **traduci i casi nel parametro**: per esempio, se $q=\log\alpha$, allora $|q|<1$ diventa $\frac1e<\alpha<e$. Controlla anche il dominio del parametro.

**Esempio:** $\displaystyle\sum_{n\ge1}\frac{x^n}{\sqrt n}$.
- $|x|<1$: il rapporto tende a $|x|<1$, quindi converge assolutamente.
- $x=1$: $\sum\frac1{\sqrt n}$ diverge, perché $p=\frac12\le1$.
- $x=-1$: $\frac1{\sqrt n}$ è decrescente e infinitesima, quindi per Leibniz converge, ma non assolutamente.
- $x>1$: $\frac{x^n}{\sqrt n}\to+\infty$, quindi diverge a $+\infty$.
- $x<-1$: i termini oscillano con modulo che tende a $+\infty$, quindi è irregolare.

### Carattere di una serie

1. **$a_n\to0$?** Se no, la serie non converge.
2. **Serie nota?**
   - Geometrica: $\sum_{n\ge0}q^n=\frac1{1-q}$ per $|q|<1$.
   - Armonica generalizzata: $\sum\frac1{n^p}$ converge se e solo se $p>1$.
   - Telescopica: scrivi $s_n$ e semplifica.
3. **Termini $\ge0$?** Non può essere irregolare. Usa:
   - asintotici e confronto, con potenze di $n$;
   - rapporto, se ci sono $n!$, $n^n$ o $a^n$;
   - radice, se tutto è elevato alla $n$.
4. **Segno variabile?** Prova la convergenza assoluta. Se fallisce, usa Leibniz: $b_n\ge0$ decrescente e infinitesima implica che $\sum(-1)^nb_n$ converge.

I logaritmi crescono meno di qualunque potenza: per esempio $\log n\le n^{1/2}$ definitivamente, quindi $\frac{\log n}{n^2}\le\frac1{n^{3/2}}$ e $\sum\frac{\log n}{n^2}$ converge.

**Radice.** Se $a_n\ge0$ e $\sqrt[n]{a_n}\to\ell$: per $\ell<1$ la serie converge, per $\ell>1$ diverge, per $\ell=1$ il criterio non decide.

### Numeri complessi
Teoria: [[Politecnico/Analisi 1/Teoria/Numeri complessi|Numeri complessi]] · Esercizi: [[Politecnico/Analisi 1/Esercizi/Numeri Complessi|Numeri Complessi]]

**Formule.**
$$\frac zw=\frac{z\bar w}{|w|^2},\qquad z\bar z=|z|^2,\qquad z+\bar z=2\,\mathrm{Re}(z),\qquad z-\bar z=2i\,\mathrm{Im}(z)$$
$$z^n=r^n\big[\cos(n\theta)+i\sin(n\theta)\big],\qquad z_k=\sqrt[n]R\,e^{i\frac{\varphi+2k\pi}n},\quad k=0,\dots,n-1$$

**Trovare $\theta$.** Se $z$ è su un asse, l'angolo si legge: $0$, $\frac\pi2$, $\pi$, $\frac32\pi$. Altrimenti trova $\alpha$ da $\left|\frac ba\right|$:

| $\left\lvert\frac ba\right\rvert$ | $\frac1{\sqrt3}$ | $1$ | $\sqrt3$ |
|---|---|---|---|
| $\alpha$ | $\frac\pi6$ | $\frac\pi4$ | $\frac\pi3$ |

Poi guarda il quadrante:

| $a$ | $b$ | Quadrante | $\theta$ |
|---|---|---|---|
| $+$ | $+$ | I | $\alpha$ |
| $-$ | $+$ | II | $\pi-\alpha$ |
| $-$ | $-$ | III | $\pi+\alpha$ |
| $+$ | $-$ | IV | $2\pi-\alpha$ |

**Risolvere $z^n=w$.**
1. Trova $R$ e $\varphi$ di $w$.
2. Raggio: $\sqrt[n]R$.
3. Primo angolo: $\frac\varphi n$.
4. Passo: $\frac{2\pi}n$, fino ad avere $n$ soluzioni.

Le soluzioni sono i vertici di un poligono regolare. Se $w$ è una potenza, come $(2+2i)^6$, calcolala prima con de Moivre.

**Forme ricorrenti.**

| Forma | Come si tratta |
|---|---|
| $(\dots)(\dots)=0$ | risolvi ogni fattore e unisci le soluzioni |
| $z\bar z=k$, con $k>0$ | circonferenza $\lvert z\rvert=\sqrt k$ |
| $z+\bar z=k$ | retta verticale $\mathrm{Re}(z)=\frac k2$ |
| $\frac z{\bar z}=c$ | con $z=re^{i\theta}$ vale $\frac z{\bar z}=e^{2i\theta}$, che ha modulo $1$ |
| $(z-a)^n=w$ | poni $u=z-a$, poi trasla: $z=u+a$ |
| $\arg(iz)=\beta$ | $\arg z=\beta-\frac\pi2$: è una semiretta senza l'origine |
| $B=\{iz\}$ | rotazione di $+\frac\pi2$ |
| $B=\{-2iz\}$ | rotazione di $-\frac\pi2$ e modulo moltiplicato per $2$ |

### Sup e inf di un insieme

**Passi.**
1. Scrivi le condizioni di esistenza.
2. Risolvi la disequazione e scrivi l'insieme come unione di intervalli.
3. Leggi sup e inf; è massimo o minimo solo se il punto appartiene all'insieme.

**Disequazioni irrazionali.**
$$\sqrt f<g\iff f\ge0,\ g>0,\ f<g^2$$
$$\sqrt f\ge g\iff(g<0,\ f\ge0)\ \text{ oppure }\ (g\ge0,\ f\ge g^2)$$
$$\sqrt f<\sqrt g\iff f\ge0,\ f<g$$

Con un valore assoluto, dividi nei casi $x\ge0$ e $x<0$, oppure usa $|x|=\sqrt{x^2}$.

**Insiemi definiti da una successione.** Separa $n$ pari e $n$ dispari se c'è $(-1)^n$, poi usa la monotonia:

| Andamento | Sup | Inf |
|---|---|---|
| Crescente | limite | primo termine |
| Decrescente | primo termine | limite |

Il limite è l'estremo a cui la successione si avvicina, quindi di solito non è raggiunto.

### Limiti con asintotici
Teoria: [[Confronti e stime asintotiche]] · [[Successioni monotone, infinitesimi e limiti notevoli]]

Con $\varepsilon_n\to0$:

$$\sin\varepsilon_n\sim\varepsilon_n,\quad\tan\varepsilon_n\sim\varepsilon_n,\quad\arctan\varepsilon_n\sim\varepsilon_n,\quad1-\cos\varepsilon_n\sim\frac{\varepsilon_n^2}2$$
$$e^{\varepsilon_n}-1\sim\varepsilon_n,\quad\log(1+\varepsilon_n)\sim\varepsilon_n,\quad(1+\varepsilon_n)^\alpha-1\sim\alpha\varepsilon_n$$

**Regole.**
- Si sostituiscono in prodotti, quozienti e potenze, **non nelle somme**.
- Se $a_n\to\ell\ne0$ finito, allora $a_n\sim\ell$. Per esempio $\arctan n\to\frac\pi2$ resta $\frac\pi2$.
- Differenza di radici: $\sqrt{a_n}-\sqrt{b_n}=\dfrac{a_n-b_n}{\sqrt{a_n}+\sqrt{b_n}}$.
- Se $a_n\to1$, allora $\log a_n\sim a_n-1$.
- Gerarchia: $\log n\ll n^k\ll a^n\ll n!\ll n^n$, con $k>0$ e $a>1$.

**Esempio:**
$$n^2\left(1-\cos\frac1n\right)\sim n^2\cdot\frac1{2n^2}=\frac12$$

## 6. Trappole delle domande a risposta multipla

| Affermazione | Vera? | Perché |
|---|---|---|
| $\lvert a_n\rvert\to\lambda$ implica $a_n\to\pm\lambda$ | No | $a_n=(-1)^n$ non ha limite, ma $\lvert a_n\rvert\to1$ |
| $\lvert a_n\rvert\to\lambda$ implica $(a_n)$ limitata | Sì | $\lvert a_n\rvert$ converge, quindi è limitata |
| $a_n\to0$ implica $\frac1{a_n}$ diverge | No | $a_n=\frac{(-1)^n}n$ dà $\frac1{a_n}=(-1)^nn$, senza limite |
| $a_n\to0$ implica $\lvert a_n\rvert\to0$ e $a_n^2\to0$ | Sì | sono sempre infinitesime |
| $a_n\to0$ implica $\sum a_n$ converge | No | $\sum\frac1n$ diverge |
| $\sup E\in E$ sempre | No | $\sup[0,1)=1\notin[0,1)$ |
| $z^n=w\ne0$ ha $n$ soluzioni distinte | Sì | teorema delle radici |
| $f(n)=3n+5$ su $\mathbb N$ è biunivoca | No | è iniettiva, ma non suriettiva: l'inversa è definita solo sull'immagine |

**Ordine dei quantificatori:** nella definizione di sup, prima $\forall\varepsilon$, poi $\exists a$. Scambiandoli, il significato cambia.

**Serie alternate:** $\sum\frac{(-1)^n}{q^n}$ è una geometrica di ragione $-\frac1q$. Non serve Leibniz, e la somma si calcola con la formula.

## 7. Formulario

### Algebra

**Prodotti notevoli e scomposizioni.**
$$(a\pm b)^2=a^2\pm2ab+b^2,\qquad a^2-b^2=(a-b)(a+b)$$
$$(a\pm b)^3=a^3\pm3a^2b+3ab^2\pm b^3$$
$$a^3+b^3=(a+b)(a^2-ab+b^2),\qquad a^3-b^3=(a-b)(a^2+ab+b^2)$$
$$(a+b)^n=\sum_{k=0}^n\binom nka^{n-k}b^k,\qquad\binom nk=\frac{n!}{k!\,(n-k)!}$$

**Secondo grado.** Per $ax^2+bx+c=0$, con $\Delta=b^2-4ac$:
$$x_{1,2}=\frac{-b\pm\sqrt\Delta}{2a},\qquad ax^2+bx+c=a(x-x_1)(x-x_2)$$

| $\Delta$ | Soluzioni | Segno del trinomio |
|---|---|---|
| $\Delta>0$ | due reali distinte | segno di $a$ fuori da $[x_1,x_2]$, opposto dentro |
| $\Delta=0$ | una doppia | segno di $a$, nullo in $x_1$ |
| $\Delta<0$ | due complesse coniugate | sempre segno di $a$ |

**Biquadratica.** Per $x^4+bx^2+c=0$, poni $t=x^2$.

**Potenze e radici.**
$$a^ma^n=a^{m+n},\quad\frac{a^m}{a^n}=a^{m-n},\quad(a^m)^n=a^{mn},\quad a^{-n}=\frac1{a^n},\quad a^{m/n}=\sqrt[n]{a^m},\quad\sqrt{x^2}=|x|$$

**Logaritmi** (con $a,b,c>0$ e $a\ne1$).
$$\log_a(bc)=\log_ab+\log_ac,\quad\log_a\frac bc=\log_ab-\log_ac,\quad\log_ab^k=k\log_ab,\quad\log_ab=\frac{\log b}{\log a},\quad a^{\log_ab}=b$$

### Disequazioni

**Valore assoluto**, con $c>0$:
$$|x|<c\iff-c<x<c,\qquad|x|>c\iff x<-c\ \text{ oppure }\ x>c$$
$$|a+b|\le|a|+|b|,\qquad|ab|=|a||b|$$

**Irrazionali:**
$$\sqrt f<g\iff f\ge0,\ g>0,\ f<g^2$$
$$\sqrt f\ge g\iff(g<0,\ f\ge0)\ \text{ oppure }\ (g\ge0,\ f\ge g^2)$$
$$\sqrt f<\sqrt g\iff f\ge0,\ f<g$$

**Fratte:** porta tutto a sinistra e studia il segno di numeratore e denominatore. Il denominatore deve essere diverso da $0$.

**Esponenziali e logaritmiche:** con base $a>1$ il verso resta uguale, con $0<a<1$ si inverte. L'argomento del logaritmo deve essere positivo.

**Condizioni di esistenza:** denominatore $\ne0$, radice di indice pari con radicando $\ge0$, argomento del logaritmo $>0$.

### Funzioni

**Definizioni.**
- **Iniettiva:** $x_1\ne x_2\Rightarrow f(x_1)\ne f(x_2)$.
- **Suriettiva:** l'immagine coincide con il codominio.
- **Biunivoca:** iniettiva e suriettiva, quindi invertibile.
- **Pari:** $f(-x)=f(x)$. **Dispari:** $f(-x)=-f(x)$.

**Trasformazioni del grafico**, con $a>0$:

| Funzione | Effetto sul grafico di $f$ |
|---|---|
| $f(x+a)$ | traslazione a sinistra di $a$ |
| $f(x-a)$ | traslazione a destra di $a$ |
| $f(x)+a$ | traslazione in alto di $a$ |
| $f(x)-a$ | traslazione in basso di $a$ |
| $f(-x)$ | simmetria rispetto all'asse $y$ |
| $-f(x)$ | simmetria rispetto all'asse $x$ |
| $\lvert f(x)\rvert$ | la parte sotto l'asse $x$ viene ribaltata sopra |
| $f(\lvert x\rvert)$ | si tiene la parte con $x\ge0$ e la si riflette rispetto all'asse $y$ |

### Trigonometria

| $\theta$ | $0$ | $\frac\pi6$ | $\frac\pi4$ | $\frac\pi3$ | $\frac\pi2$ | $\pi$ | $\frac32\pi$ |
|---|---|---|---|---|---|---|---|
| $\cos\theta$ | $1$ | $\frac{\sqrt3}2$ | $\frac{\sqrt2}2$ | $\frac12$ | $0$ | $-1$ | $0$ |
| $\sin\theta$ | $0$ | $\frac12$ | $\frac{\sqrt2}2$ | $\frac{\sqrt3}2$ | $1$ | $0$ | $-1$ |
| $\tan\theta$ | $0$ | $\frac1{\sqrt3}$ | $1$ | $\sqrt3$ | non esiste | $0$ | non esiste |

$$\sin^2\theta+\cos^2\theta=1,\qquad\tan\theta=\frac{\sin\theta}{\cos\theta}$$
$$\cos(-\theta)=\cos\theta,\qquad\sin(-\theta)=-\sin\theta$$
$$\cos(\alpha\pm\beta)=\cos\alpha\cos\beta\mp\sin\alpha\sin\beta,\qquad\sin(\alpha\pm\beta)=\sin\alpha\cos\beta\pm\cos\alpha\sin\beta$$
$$\sin2\theta=2\sin\theta\cos\theta,\qquad\cos2\theta=\cos^2\theta-\sin^2\theta$$

### Numeri complessi

**Forme.**
$$z=a+ib=r(\cos\theta+i\sin\theta)=re^{i\theta}$$
$$r=|z|=\sqrt{a^2+b^2},\qquad a=r\cos\theta,\qquad b=r\sin\theta,\qquad\cos\theta=\frac ar,\qquad\sin\theta=\frac br$$

**Unità immaginaria.**
$$i^2=-1,\qquad i^3=-i,\qquad i^4=1,\qquad\frac1i=-i,\qquad e^{i\pi}=-1,\qquad e^{i\pi/2}=i$$

Per $i^n$ conta il resto di $n$ diviso $4$: resto $0\to1$, resto $1\to i$, resto $2\to-1$, resto $3\to-i$.

**Operazioni.**
$$(a+ib)+(c+id)=(a+c)+i(b+d)$$
$$(a+ib)(c+id)=(ac-bd)+i(ad+bc)$$
$$\frac1z=\frac{\bar z}{|z|^2},\qquad\frac zw=\frac{z\bar w}{|w|^2}$$

**Coniugato.**
$$\bar z=a-ib,\quad\overline{\bar z}=z,\quad\overline{z+w}=\bar z+\bar w,\quad\overline{zw}=\bar z\,\bar w,\quad\bar z=re^{-i\theta}$$
$$z\bar z=|z|^2,\quad\mathrm{Re}(z)=\frac{z+\bar z}2,\quad\mathrm{Im}(z)=\frac{z-\bar z}{2i},\quad\frac z{\bar z}=e^{2i\theta}$$

**Modulo.**
$$|zw|=|z||w|,\quad\left|\frac zw\right|=\frac{|z|}{|w|},\quad|z^n|=|z|^n,\quad|\bar z|=|z|,\quad|z+w|\le|z|+|w|$$

**Forma esponenziale.** Con $z=re^{i\theta}$ e $w=Re^{i\varphi}$:
$$zw=rRe^{i(\theta+\varphi)},\qquad\frac zw=\frac rRe^{i(\theta-\varphi)},\qquad z^n=r^ne^{in\theta}$$

**Radici $n$-esime** di $w=Re^{i\varphi}\ne0$:
$$z_k=\sqrt[n]R\,e^{i\frac{\varphi+2k\pi}n},\qquad k=0,\dots,n-1$$

Radici dell'unità: $z_k=e^{i\frac{2k\pi}n}$.

**Angolo $\theta\in[0,2\pi)$,** con $\alpha=\arctan\left|\frac ba\right|$:

| $a$ | $b$ | Quadrante | $\theta$ |
|---|---|---|---|
| $+$ | $+$ | I | $\alpha$ |
| $-$ | $+$ | II | $\pi-\alpha$ |
| $-$ | $-$ | III | $\pi+\alpha$ |
| $+$ | $-$ | IV | $2\pi-\alpha$ |
| $0$ | $+$ | asse immaginario positivo | $\frac\pi2$ |
| $0$ | $-$ | asse immaginario negativo | $\frac32\pi$ |
| $+$ | $0$ | asse reale positivo | $0$ |
| $-$ | $0$ | asse reale negativo | $\pi$ |

**Equazioni.**
- $az^2+bz+c=0$ con coefficienti reali e $\Delta<0$: $z=\dfrac{-b\pm i\sqrt{|\Delta|}}{2a}$.
- Un polinomio di grado $n$ ha esattamente $n$ radici in $\mathbb C$, contate con molteplicità.

**Luoghi nel piano.**

| Condizione | Figura |
|---|---|
| $\lvert z-z_0\rvert=r$ | circonferenza di centro $z_0$ e raggio $r$ |
| $\lvert z-z_0\rvert<r$ | cerchio senza bordo |
| $\mathrm{Re}(z)=k$ | retta verticale |
| $\mathrm{Im}(z)=k$ | retta orizzontale |
| $\arg z=\beta$ | semiretta dall'origine, origine esclusa |

**Trasformazioni.** Moltiplicare per $Re^{i\varphi}$ ruota di $\varphi$ e moltiplica il modulo per $R$. In particolare $i=e^{i\pi/2}$, $-i=e^{i\frac32\pi}$, $-1=e^{i\pi}$. Sommare $z_0$ trasla, $\bar z$ è la simmetria rispetto all'asse reale.

### Limiti

**Forme indeterminate.**
$$+\infty-\infty,\qquad0\cdot\infty,\qquad\frac00,\qquad\frac\infty\infty,\qquad1^\infty,\qquad0^0,\qquad\infty^0$$

**Forme non indeterminate:**
$$\frac c{\pm\infty}=0,\qquad\frac{c}{0^+}=+\infty\ (c>0),\qquad+\infty+\infty=+\infty,\qquad\infty\cdot\infty=\infty$$

**Limiti notevoli.**
$$\left(1+\frac1n\right)^n\to e,\qquad\left(1+\frac an\right)^n\to e^a,\qquad\sqrt[n]a\to1\ (a>0),\qquad\sqrt[n]n\to1$$
$$a^n\to\begin{cases}+\infty&a>1\\1&a=1\\0&|a|<1\\\text{non esiste}&a\le-1\end{cases}\qquad\qquad\arctan n\to\frac\pi2$$

**Gerarchia degli infiniti**, con $k>0$ e $a>1$:
$$\log n\ll n^k\ll a^n\ll n!\ll n^n$$

**Asintotici**, con $\varepsilon_n\to0$:

| Espressione | Equivalente |
|---|---|
| $\sin\varepsilon_n,\ \tan\varepsilon_n,\ \arcsin\varepsilon_n,\ \arctan\varepsilon_n$ | $\varepsilon_n$ |
| $1-\cos\varepsilon_n$ | $\frac{\varepsilon_n^2}2$ |
| $e^{\varepsilon_n}-1$ | $\varepsilon_n$ |
| $\log(1+\varepsilon_n)$ | $\varepsilon_n$ |
| $(1+\varepsilon_n)^\alpha-1$ | $\alpha\varepsilon_n$ |
| $\sinh\varepsilon_n,\ \tanh\varepsilon_n$ | $\varepsilon_n$ |
| $\cosh\varepsilon_n-1$ | $\frac{\varepsilon_n^2}2$ |
| $\log a_n$, se $a_n\to1$ | $a_n-1$ |
| polinomio in $n$ | termine di grado massimo |
| $n!$ | $e^{-n}n^n\sqrt{2\pi n}$ |
| $\log n!$ | $n\log n$ |
| $\sum_{k=1}^n\frac1k$ | $\log n$ |

**Tecniche.**
$$\sqrt{a_n}-\sqrt{b_n}=\frac{a_n-b_n}{\sqrt{a_n}+\sqrt{b_n}},\qquad a_n^{b_n}=e^{b_n\log a_n}$$

**o-piccolo.**
$$o(a_n)\pm o(a_n)=o(a_n),\qquad c\cdot o(a_n)=o(a_n),\qquad a_n\cdot o(b_n)=o(a_nb_n),\qquad a_n\sim b_n\iff a_n=b_n+o(b_n)$$

### Serie

**Serie di riferimento.**

| Serie | Carattere |
|---|---|
| $\sum_{n\ge0}q^n$ | converge a $\frac1{1-q}$ se $\lvert q\rvert<1$; diverge se $q\ge1$; irregolare se $q\le-1$ |
| $\sum_{n\ge k}q^n$ | se $\lvert q\rvert<1$, vale $\frac{q^k}{1-q}$ |
| $\sum\frac1n$ | diverge |
| $\sum\frac1{n^p}$ | converge se e solo se $p>1$ |
| $\sum\frac1{n^p\log^qn}$ | converge se $p>1$; diverge se $p<1$; se $p=1$ converge se e solo se $q>1$ |
| $\sum(b_n-b_{n+1})$ | telescopica: $s_n=b_1-b_{n+1}$, partendo da $n=1$ |
| $\sum_{n\ge1}\frac1{n(n+1)}$ | telescopica, somma $1$ |

**Somme finite.**
$$\sum_{k=1}^nk=\frac{n(n+1)}2,\qquad\sum_{k=0}^nq^k=\frac{1-q^{n+1}}{1-q}\quad(q\ne1)$$

**Criteri.**

| Criterio | Ipotesi | Conclusione |
|---|---|---|
| Condizione necessaria | $\sum a_n$ converge | $a_n\to0$ |
| Confronto | $0\le a_n\le b_n$ | $\sum b_n$ conv. $\Rightarrow\sum a_n$ conv.; $\sum a_n$ div. $\Rightarrow\sum b_n$ div. |
| Confronto asintotico | $a_n,b_n>0$, $\frac{a_n}{b_n}\to\ell\in(0,+\infty)$ | stesso carattere |
| Rapporto | $a_n>0$, $\frac{a_{n+1}}{a_n}\to\ell$ | $\ell<1$ conv.; $\ell>1$ div.; $\ell=1$ nessuna informazione |
| Radice | $a_n\ge0$, $\sqrt[n]{a_n}\to\ell$ | $\ell<1$ conv.; $\ell>1$ div.; $\ell=1$ nessuna informazione |
| Leibniz | $b_n\ge0$ decrescente, $b_n\to0$ | $\sum(-1)^nb_n$ converge |
| Convergenza assoluta | $\sum\lvert a_n\rvert$ converge | $\sum a_n$ converge |

Se $\frac{a_n}{b_n}\to0$ e $\sum b_n$ converge, con termini positivi, converge anche $\sum a_n$. Se $\frac{a_n}{b_n}\to+\infty$ e $\sum b_n$ diverge, diverge anche $\sum a_n$.

**Linearità:** $\sum(\alpha a_n+\beta b_n)=\alpha\sum a_n+\beta\sum b_n$, se le due serie convergono.

### Induzione e Bernoulli

**Induzione:** se $P(n_0)$ è vera e $P(n)\Rightarrow P(n+1)$, allora $P(n)$ è vera per ogni $n\ge n_0$.

**Bernoulli:** $(1+x)^n\ge1+nx$ per $x>-1$.

## 8. Prove da fare

Falle a tempo, dalla più recente, e correggi solo alla fine:

- [ ] [[Novembre 2025]] · [[Novembre 2025.pdf|PDF]]
- [ ] [[Novembre 2024]] · [[Novembre 2024-Soluzioni.pdf|PDF con soluzioni]]
- [ ] [[Novembre 2023 (prima prova parziale)]] · [[Prima Prova Parziale 6-11-23.pdf|PDF]]
- [ ] [[Novembre 2022 (I prova in itinere)]] · [[Novembre 22.pdf|PDF]]
- [ ] [[Novembre 2018 (primo parziale)]] · [[PrimoParziale 2018.pdf|PDF]]

**Controllo finale:**

- [ ] So scrivere a memoria tutte le definizioni della sezione 3
- [ ] So dimostrare a memoria permanenza del segno, carabinieri e condizione necessaria
- [ ] So dimostrare tutte le altre ★
- [ ] So trovare $\theta$ senza guardare le tabelle
- [ ] So risolvere $z^n=w$ e disegnare le soluzioni
- [ ] So distinguere i cinque casi di una serie con parametro
- [ ] So applicare Leibniz controllando tutte le ipotesi
- [ ] So risolvere disequazioni irrazionali e leggere sup, inf, max e min
- [ ] So calcolare limiti con gli asintotici, senza usarli nelle somme
