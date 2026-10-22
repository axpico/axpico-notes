---
tags:
  - geometria-algebra-lineare
  - dipendenza-lineare
---
## Dipendenza lineare

↑ [[Politecnico/Geometria e Algebra Lineare/Indice|Indice]] · tappa 4 (Spazi vettoriali) · prima: [[Basi, dimensione e coordinate|Basi, dimensione e coordinate]]

> Fonte: [[06 Dipendenza lineare. Condizioni di una base. Basi di nucleo e di span. Rango di una matrice ed una mappa lineare. Teorema di nullita piu rango.pdf|Lezione 6 (PDF)]] — ALG cap. 4 §7, pp. 177–180, 201–209.
> Programma della lezione: dipendenza lineare · condizioni di una base · basi di nucleo e span · rango di matrice e mappa lineare · teorema di nullità più rango. Queste note coprono le pp. 1–40 (dipendenza lineare e condizioni di una base). Seguito: [[Basi di nucleo, immagine e span|Basi di nucleo, immagine e span]] (pp. 41–62) e [[Rango e teorema di nullità più rango|Rango e teorema di nullità più rango]] (pp. 63–92).

### 1. Motivazione geometrica: quando un'equazione parametrica descrive davvero una retta o un piano?

Dalla Lezione 5 (vedi [[Rette e piani — equazioni parametriche e cartesiane|Rette e piani — equazioni parametriche e cartesiane]]):

- retta: $\vec r=\vec r_0+t\vec a,\ t\in\mathbb R$ (1)
- piano: $\vec r=\vec r_0+t\vec u+s\vec v,\ s,t\in\mathbb R$ (2)

**Domanda:** date queste forme, descrivono *sempre* una retta / un piano? La risposta non dipende da $\vec r_0$ (basta traslare l'origine del riferimento, quindi si può porre $\vec r_0=\vec 0$): conta solo la posizione reciproca dei vettori direttori.

**(i) Retta.**
- Se $\vec a=\vec 0$: (1) diventa $\vec r=\vec r_0$, cioè **un solo punto**, non una retta.
- Se $\vec a\ne\vec 0$: esiste un'unica retta per $A\neq B$ con vettori posizione $\vec r_0$ e $\vec r_1=\vec r_0+\vec a$, e la sua equazione parametrica è proprio (1).

> **Conclusione.** (1) descrive una retta $\iff \vec a\neq\vec 0$.

**(ii) Piano** (tre casi):
- $\vec u=\vec v=\vec 0$: si ottiene l'insieme $\{\vec r_0\}$, un punto.
- $\vec u\ne\vec 0$ e $\vec v=\lambda\vec u$ (multiplo di $\vec u$): 
 $$\vec r=\vec r_0+t\vec u+s\lambda\vec u=\vec r_0+(t+\lambda s)\vec u=\vec r_0+\tau\vec u,\quad \tau:=t+\lambda s\in\mathbb R,$$
 che è una **retta**, non un piano (due parametri collassano in uno solo).
- $\vec u\neq\vec 0$ e $\vec v$ **non** multiplo di $\vec u$ (in particolare $\vec v\ne\vec 0$): i tre punti $A,B,C$ di vettori posizione $\vec r_0,\ \vec r_1=\vec r_0+\vec u,\ \vec r_2=\vec r_0+\vec v$ **non sono allineati**, quindi esiste un unico piano $\Pi$ per $A,B,C$, e la sua equazione parametrica è (2).

**Dicotomia riassuntiva.** Per $\vec u,\vec v$ vale esattamente una di:
- (a) uno dei due è multiplo dell'altro (include il caso $\vec u=\vec v=\vec 0$, perché $\vec 0=\lambda\vec 0\ \forall\lambda$);
- (b) nessuno dei due è multiplo dell'altro.

> (2) descrive un piano $\iff$ vale (b). In tal caso $\vec u,\vec v$ si dicono **linearmente indipendenti**; se vale (a), **linearmente dipendenti**.

Questo è il caso particolare ($n=2$ vettori) di un concetto generale.

### 2. Definizione generale

**Definizione.** Vettori $\mathbf v_1,\dots,\mathbf v_n$ di uno spazio vettoriale $V$ su $\mathbb K$ sono **linearmente dipendenti** se
$$\exists\,\mathbf c=(c_1,\dots,c_n)\in\mathbb K^n,\ \mathbf c\neq\mathbf 0\ :\quad c_1\mathbf v_1+\dots+c_n\mathbf v_n=\mathbf 0.$$
Altrimenti, se l'uguaglianza $c_1\mathbf v_1+\dots+c_n\mathbf v_n=\mathbf 0$ vale **solo** per $c_1=\dots=c_n=0$, sono **linearmente indipendenti**.

Punto sottile (livello universitario): la dipendenza riguarda l'esistenza di una combinazione lineare **non banale** che dà $\mathbf 0$. La combinazione banale ($\mathbf c=\mathbf 0$) dà sempre $\mathbf 0$ e quindi non distingue nulla.

**Esempi.**
- $\begin{pmatrix}1\\-2\\3\end{pmatrix},\begin{pmatrix}3\\1\\2\end{pmatrix},\begin{pmatrix}7\\0\\7\end{pmatrix}$ sono dipendenti: $1\cdot\begin{pmatrix}1\\-2\\3\end{pmatrix}+2\begin{pmatrix}3\\1\\2\end{pmatrix}+(-1)\begin{pmatrix}7\\0\\7\end{pmatrix}=\mathbf 0$.
- $\begin{pmatrix}1\\2\end{pmatrix},\begin{pmatrix}0\\0\end{pmatrix}$ sono dipendenti: $0\begin{pmatrix}1\\2\end{pmatrix}+1\begin{pmatrix}0\\0\end{pmatrix}=\mathbf 0$.

### 3. Due criteri rapidi

1. **Se un sistema di vettori contiene $\mathbf 0$, è dipendente.** (Si prende coefficiente $1$ su $\mathbf 0$ e $0$ sugli altri.)
 Esempio: $\mathbf v_1=(1,2,3),\ \mathbf v_2=(0,1,0),\ \mathbf v_3=(1,2,3)$: $1\mathbf v_1+0\mathbf v_2+(-1)\mathbf v_3=\mathbf 0$.
2. **Se un vettore si ripete (due o più volte), il sistema è dipendente.** (Coefficienti $1$ e $-1$ sulle copie, $0$ altrove.) È l'esempio qui sopra con $\mathbf v_1=\mathbf v_3$.

### 4. Proposizione 1 (caratterizzazione della dipendenza)

> **Proposizione 1.** Siano $\mathbf v_1,\dots,\mathbf v_n\in V$. Equivalgono:
> 1. $\mathbf v_1,\dots,\mathbf v_n$ sono linearmente dipendenti;
> 2. almeno uno dei $\mathbf v_j$ è **combinazione lineare degli altri**.

*Dimostrazione.*

**(ii) ⇒ (i).** Sia $\mathbf v_j=\sum_{k\neq j}c_k\mathbf v_k$. Ponendo $c_j:=-1$:
$$\sum_{k=1}^n c_k\mathbf v_k=\sum_{k\ne j}c_k\mathbf v_k+c_j\mathbf v_j=\mathbf v_j-\mathbf v_j=\mathbf 0.$$
Poiché $c_j=-1\neq0$, $\mathbf c\ne\mathbf 0$: i vettori sono dipendenti.

**(i) ⇒ (ii).** Esiste $\mathbf c\ne\mathbf 0$ con $\sum c_k\mathbf v_k=\mathbf 0$. Essendo $\mathbf c\ne\mathbf 0$, esiste $j$ con $c_j\ne0$. Allora $\sum_{k\ne j}c_k\mathbf v_k=-c_j\mathbf v_j$ e, **dividendo per $c_j$** (qui serve che $\mathbb K$ sia un campo),
$$\mathbf v_j=\sum_{k\ne j}\Bigl(-\frac{c_k}{c_j}\Bigr)\mathbf v_k.\qquad\blacksquare$$

> **Attenzione.** (ii) dice "*almeno uno*", non "ciascuno". Esempio: $(1,0),(2,0),(0,1)$ sono dipendenti, ma $(0,1)$ non è combinazione degli altri due.

**Corollario (due vettori).** $\mathbf v_1,\mathbf v_2$ sono dipendenti $\iff$ uno è multiplo dell'altro, cioè $\exists\lambda\in\mathbb K$ con $\mathbf v_1=\lambda\mathbf v_2$ oppure $\mathbf v_2=\lambda\mathbf v_1$. (È esattamente la dicotomia (a)/(b) della sezione 1.)

**Esempi.**
- $\mathbf v_1=\begin{pmatrix}6\\2\\3\end{pmatrix},\ \mathbf v_2=\begin{pmatrix}4\\4/3\\2\end{pmatrix}$ dipendenti perché $\mathbf v_2=\tfrac23\mathbf v_1$. Invece $\mathbf v_1$ e $\mathbf v_3=\begin{pmatrix}3\\1\\2\end{pmatrix}$ sono indipendenti perché le componenti non sono proporzionali: $6:3=2:1\neq3:2$.
- In $V=\{f:\mathbb R\to\mathbb R \text{ differenziabili}\}$, $f(t)=\sin t$ e $g(t)=\cos t$ sono **indipendenti**: non esiste $\lambda\in\mathbb R$ tale che $\sin t=\lambda\cos t$ per ogni $t$ (né $\cos t=\lambda\sin t$ per ogni $t$). Nota: lo spazio è di funzioni, non di "frecce": la teoria vale in ogni spazio vettoriale.

> *Nota del PDF:* nella scansione l'esempio viene detto "linearmente dipendenti" ma la motivazione ("nessuna costante $\lambda$") dimostra l'**indipendenza**: è un lapsus del testo, la conclusione corretta è indipendenti.

### 5. La base canonica è linearmente indipendente

Per ogni $n$, $\{\mathbf e_1,\dots,\mathbf e_n\}$ in $\mathbb K^n$ è indipendente.

*Dimostrazione (per assurdo, via Proposizione 1).* Se fossero dipendenti, esisterebbe $j$ con $\mathbf e_j$ combinazione lineare degli $\mathbf e_k$, $k\ne j$. Ma la $j$-esima componente di ogni $\mathbf e_k$ ($k\neq j$) è $0$, dunque anche quella di ogni loro combinazione lineare è $0$, mentre la $j$-esima componente di $\mathbf e_j$ è $1$. Contraddizione. $\blacksquare$

### 6. Ogni base è linearmente indipendente

**Osservazione.** Il caso precedente è un'istanza del fatto generale: **ogni base** $\mathcal B=\{\mathbf v_1,\dots,\mathbf v_n\}$ di un qualsiasi spazio vettoriale $V$ è un sistema linearmente indipendente.

*Dimostrazione (pp. 19–20).* La combinazione banale dà
 (a) $0\mathbf v_1+\dots+0\mathbf v_n=\mathbf 0$.
Si suppone per assurdo che siano dipendenti: esiste $\mathbf c'\neq\mathbf 0$ con
 (b) $c_1'\mathbf v_1+\dots+c_n'\mathbf v_n=\mathbf 0$.
Quindi lo stesso vettore $\mathbf 0$ si scrive in **due modi distinti** come combinazione lineare di $\mathbf v_1,\dots,\mathbf v_n$. Ma in una base la scrittura di ogni vettore è **unica** (teorema delle coordinate, vedi [[Basi, dimensione e coordinate|Basi, dimensione e coordinate]]): contraddizione. $\blacksquare$

### 7. Teorema 2 (condizioni di essere una base)

In realtà vale un'affermazione più forte.

> **Teorema 2.** Sia $V$ uno spazio vettoriale e $\mathcal B=\{\mathbf v_1,\dots,\mathbf v_n\}\subset V$. Sono equivalenti:
> - (a) $\mathcal B$ è una base di $V$;
> - (b) (b.1) $\mathbf v_1,\dots,\mathbf v_n$ sono linearmente indipendenti **e** (b.2) $\dim V=n$;
> - (c) (c.1) $\mathbf v_1,\dots,\mathbf v_n$ sono linearmente indipendenti **e** (c.2) non esiste alcun $\mathbf u\in V$ tale che $\mathbf u,\mathbf v_1,\dots,\mathbf v_n$ siano linearmente indipendenti (cioè $\mathcal B$ è un sistema indipendente **massimale**).
>
> (Dimostrazione saltata a lezione.)

**Esempi.**
- $\begin{pmatrix}1\\2\end{pmatrix},\begin{pmatrix}2\\1\end{pmatrix}$ sono indipendenti ($1:2\neq2:1$) e $\dim\mathbb R^2=2$: per (b) formano una base di $\mathbb R^2$.
- Due vettori indipendenti di $\mathbb R^3$ (ad es. $\begin{pmatrix}1\\2\\3\end{pmatrix},\begin{pmatrix}3\\2\\1\end{pmatrix}$, non proporzionali) **non** formano una base di $\mathbb R^3$: $\dim\mathbb R^3=3$, quindi nessuna base di $\mathbb R^3$ può avere 2 vettori.

> *Nota:* nella scansione il secondo esempio è parzialmente illeggibile; i vettori qui sopra sono un esempio equivalente.

### 8. Come verificare l'indipendenza in $\mathbb K^m$: il criterio del rango

Serve un metodo per stabilire se $\mathcal B=\{\mathbf v_1,\dots,\mathbf v_n\}$ è dipendente o indipendente. In $V=\mathbb K^m$ c'è un metodo efficace: l'uguaglianza
$$c_1\mathbf v_1+\dots+c_n\mathbf v_n=\mathbf 0$$
è il sistema lineare omogeneo
$$(\ast)\qquad A\mathbf c=\mathbf 0,\qquad A:=[\mathbf v_1|\mathbf v_2|\cdots|\mathbf v_n],\quad \mathbf c=(c_1,\dots,c_n).$$
Per definizione i vettori sono indipendenti $\iff(\ast)$ ha solo la soluzione banale $\iff$ (Rouché–Capelli, vedi [[Sistemi lineari e teorema di Rouché-Capelli|Rouché-Capelli]])

> $$\mathbf v_1,\dots,\mathbf v_n\ \text{indipendenti}\iff r\bigl([\mathbf v_1|\cdots|\mathbf v_n]\bigr)=n\ (=\#\text{vettori}).$$

(Il rango è il numero di righe non nulle della matrice ridotta a scala.)

**Esempio 1 (dipendenti).** $\mathbf v_1=\begin{pmatrix}1\\2\\3\end{pmatrix},\ \mathbf v_2=\begin{pmatrix}1\\1\\1\end{pmatrix},\ \mathbf v_3=\begin{pmatrix}3\\2\\1\end{pmatrix}$:
$$\begin{pmatrix}1&1&3\\2&1&2\\3&1&1\end{pmatrix}\xrightarrow[R_3\to R_3-3R_1]{R_2\to R_2-2R_1}\begin{pmatrix}1&1&3\\0&-1&-4\\0&-2&-8\end{pmatrix}\xrightarrow{R_3\to R_3-2R_2}\begin{pmatrix}1&1&3\\0&-1&-4\\0&0&0\end{pmatrix}.$$
$r(A)=2<3$: **dipendenti**.

> *Nota:* nella trascrizione $\mathbf v_2$ compare come $(1,1,2)^{\mathsf T}$, ma la matrice scritta ha seconda colonna $(1,1,1)^{\mathsf T}$; i calcoli sono coerenti con $(1,1,1)^{\mathsf T}$ (infatti $\mathbf v_1-4\mathbf v_2+\mathbf v_3=\mathbf 0$).

**Esempio 2 (indipendenti).** $\mathbf v_1=\begin{pmatrix}1\\2\\3\end{pmatrix},\ \mathbf v_2=\begin{pmatrix}0\\0\\1\end{pmatrix},\ \mathbf v_3=\begin{pmatrix}3\\2\\1\end{pmatrix}$:
$$\begin{pmatrix}1&0&3\\2&0&2\\3&1&1\end{pmatrix}\xrightarrow[R_3\to R_3-3R_1]{R_2\to R_2-2R_1}\begin{pmatrix}1&0&3\\0&0&-4\\0&1&-8\end{pmatrix}\xrightarrow{R_2\leftrightarrow R_3}\begin{pmatrix}1&0&3\\0&1&-8\\0&0&-4\end{pmatrix}.$$
$r(A)=3=\#$vettori: **indipendenti**. Essendo 3 vettori indipendenti in $\mathbb R^3$ ($\dim=3$), per il Teorema 2 sono anche una **base** di $\mathbb R^3$.

> *Nota:* la matrice scritta ha seconda colonna $(0,0,1)^{\mathsf T}$; i calcoli usano questa.

### 9. Spazi qualsiasi di dimensione finita: si passa alle coordinate

> **Proposizione 2.** Sia $\dim V<\infty$ e $\mathcal B$ una base di $V$. Siano $\mathbf v_1,\dots,\mathbf v_n\in V$ e $\mathbf c_k:=[\mathbf v_k]_{\mathcal B}$ i loro vettori delle coordinate. Allora
> $$\mathbf v_1,\dots,\mathbf v_n\ \text{indipendenti}\iff\mathbf c_1,\dots,\mathbf c_n\ \text{indipendenti}.$$
> (Dimostrazione saltata; segue dal fatto che $\mathbf v\mapsto[\mathbf v]_{\mathcal B}$ è un isomorfismo.)

**Esempio (polinomi).** Stabilire se sono indipendenti
$$f_1(x)=x^2-x+1,\qquad f_2(x)=x^2+x-1,\qquad f_3(x)=x^2+x+1.$$
Stanno in $P_2=\{\text{polinomi di grado}\le2\}$, con base $\mathcal B=\{p_0,p_1,p_2\}$, $p_k(x)=x^k$. Coordinate:
$$\mathbf c_1=\begin{pmatrix}1\\-1\\1\end{pmatrix},\quad\mathbf c_2=\begin{pmatrix}-1\\1\\1\end{pmatrix},\quad\mathbf c_3=\begin{pmatrix}1\\1\\1\end{pmatrix}.$$
$$\begin{pmatrix}1&-1&1\\-1&1&1\\1&1&1\end{pmatrix}\xrightarrow[R_3\to R_3-R_1]{R_2\to R_2+R_1}\begin{pmatrix}1&-1&1\\0&0&2\\0&2&0\end{pmatrix}\xrightarrow{R_2\leftrightarrow R_3}\begin{pmatrix}1&-1&1\\0&2&0\\0&0&2\end{pmatrix}.$$
$r=3$: le coordinate sono indipendenti, quindi (Prop. 2) anche $f_1,f_2,f_3$.

### 10. Spazi di dimensione infinita: Proposizione 3

Se $\dim V=+\infty$ non ci sono basi finite, ma vale:

> **Proposizione 3.** Sia $L:V\to W$ lineare, $\mathbf v_1,\dots,\mathbf v_n\in V$ e $\mathbf w_k:=L(\mathbf v_k)$. Se $\mathbf v_1,\dots,\mathbf v_n$ sono **dipendenti**, allora anche $\mathbf w_1,\dots,\mathbf w_n$ sono **dipendenti**.
>
> Equivalentemente (contronominale): **se le immagini sono indipendenti, i vettori di partenza sono indipendenti.**

*Dimostrazione.* Esiste $\mathbf c\neq\mathbf 0$ con $\sum c_k\mathbf v_k=\mathbf 0$. Applicando $L$ (lineare, $L(\mathbf 0)=\mathbf 0$):
$$\mathbf 0=L\Bigl(\sum c_k\mathbf v_k\Bigr)=\sum c_kL(\mathbf v_k)=\sum c_k\mathbf w_k,\qquad\mathbf c\neq\mathbf 0.\qquad\blacksquare$$

**Esempio.** In $V=C^\infty(\mathbb R)$, $f_1=\cos x$, $f_2=\cos 2x$, $f_3=\sin x$ sono indipendenti.
Si usa $L:V\to\mathbb R^3$, $L(f)=\bigl(f(0),f'(0),f''(0)\bigr)$:
$$L(f_1)=\begin{pmatrix}1\\0\\-1\end{pmatrix},\quad L(f_2)=\begin{pmatrix}1\\0\\-4\end{pmatrix},\quad L(f_3)=\begin{pmatrix}0\\1\\0\end{pmatrix},$$
$$\begin{pmatrix}1&1&0\\0&0&1\\-1&-4&0\end{pmatrix}\xrightarrow{R_3\to R_3+R_1}\begin{pmatrix}1&1&0\\0&0&1\\0&-3&0\end{pmatrix}\xrightarrow{R_2\leftrightarrow R_3}\begin{pmatrix}1&1&0\\0&-3&0\\0&0&1\end{pmatrix}.$$
Rango $3$: le immagini sono indipendenti, quindi (Prop. 3) $f_1,f_2,f_3$ sono indipendenti.

### 11. Tre osservazioni

**Osservazione 1 (sottosistemi).** Ogni sottosistema di un sistema indipendente è indipendente. Equivalentemente: **se un sottosistema è dipendente, tutto il sistema è dipendente.** Basta aggiungere coefficienti $0$ per i vettori mancanti.
Esempio in $\mathbb R^4$: $\mathbf v_1=(1,0,1,0)$, $\mathbf v_2=(1,2,3,4)$, $\mathbf v_3=(1,0,0,0)$, $\mathbf v_4=(0,0,-1,0)$. Da $\mathbf v_1-\mathbf v_3+\mathbf v_4=\mathbf 0$ segue $1\mathbf v_1+0\mathbf v_2-1\mathbf v_3+1\mathbf v_4=\mathbf 0$: tutto il sistema è dipendente.
Analogamente $(1,2,1),(2,4,2),(2,1,2)$ sono dipendenti perché già $\mathbf v_2=2\mathbf v_1$.

**Osservazione 2 (troppi vettori).** Se $\dim V=n<m$, allora $m$ vettori qualsiasi di $V$ sono dipendenti.
*Dimostrazione (per assurdo).* Se $\mathbf v_1,\dots,\mathbf v_m$ fossero indipendenti, per l'Oss. 1 lo sarebbero i primi $n$. Per il Teorema 2 (b) formano allora una base, quindi $\mathbf v_{n+1}$ è combinazione lineare di $\mathbf v_1,\dots,\mathbf v_n$. Per la Prop. 1, $\mathbf v_1,\dots,\mathbf v_{n+1}$ sono dipendenti e quindi, per l'Oss. 1, lo sono anche $\mathbf v_1,\dots,\mathbf v_m$. Contraddizione. $\blacksquare$
Esempio: $(1,0),(1,1),(2,1)$ sono dipendenti: sono 3 vettori in $\mathbb R^2$.

**Osservazione 3 (un solo vettore).** $\{\mathbf v\}$ è indipendente $\iff\mathbf v\neq\mathbf 0$.
*(Perché? Domanda lasciata aperta a lezione.)* Se $\mathbf v=\mathbf 0$, allora $1\cdot\mathbf 0=\mathbf 0$ è una combinazione non banale. Se $\mathbf v\neq\mathbf 0$ e $c\mathbf v=\mathbf 0$ con $c\neq0$, moltiplicando per $c^{-1}$ si ottiene $\mathbf v=\mathbf 0$, assurdo.

### Riepilogo

| Concetto | Contenuto |
|---|---|
| Dipendenti | $\exists\,\mathbf c\ne\mathbf 0$: $\sum c_k\mathbf v_k=\mathbf 0$ |
| Indipendenti | $\sum c_k\mathbf v_k=\mathbf 0\Rightarrow\mathbf c=\mathbf 0$ |
| Contiene $\mathbf 0$ / ripetizioni | $\Rightarrow$ dipendenti |
| Prop. 1 | dipendenti $\iff$ un vettore è comb. lineare degli altri |
| 2 vettori | dipendenti $\iff$ proporzionali |
| Geometria | $\vec u,\vec v$ indipendenti $\iff$ (2) è un piano; $\vec a\ne\vec 0\iff$ (1) è una retta |
| Basi | ogni base è indipendente (e genera) |
| Teorema 2 | base $\iff$ indipendenti e $\#=\dim V$ $\iff$ indipendenti massimali |
| In $\mathbb K^m$ | indipendenti $\iff r([\mathbf v_1\vert\cdots\vert\mathbf v_n])=n$ |
| Prop. 2 | indipendenza $\iff$ indipendenza delle coordinate |
| Prop. 3 | immagini indipendenti $\Rightarrow$ vettori indipendenti |
| Oss. 2 | più di $\dim V$ vettori $\Rightarrow$ dipendenti |
