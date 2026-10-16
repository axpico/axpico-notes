---
tags:
  - geometria-algebra-lineare
  - dipendenza-lineare
---
## Dipendenza lineare

↑ [[Politecnico/Geometria e Algebra Lineare/Indice|Indice]] · tappa 4 (Spazi vettoriali) · prima: [[Politecnico/Geometria e Algebra Lineare/Teoria/Basi, dimensione e coordinate|Basi, dimensione e coordinate]]

> Fonte: [[Politecnico/Geometria e Algebra Lineare/06 Dipendenza lineare. Condizioni di una base. Basi di nucleo e di span. Rango di una matrice ed una mappa lineare. Teorema di nullita piu rango.pdf|Lezione 6 (PDF)]] — ALG cap. 4 §7, pp. 177–180, 201–209.
> Programma della lezione: dipendenza lineare · condizioni di una base · basi di nucleo e span · rango di matrice e mappa lineare · teorema di nullità più rango. **Queste note coprono solo le pp. 1–19 (dipendenza lineare).**

### 1. Motivazione geometrica: quando un'equazione parametrica descrive davvero una retta o un piano?

Dalla Lezione 5 (vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Rette e piani — equazioni parametriche e cartesiane.md|Rette e piani — equazioni parametriche e cartesiane]]):

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

*Impostazione della dimostrazione (p. 19 — la scansione si interrompe qui).* La combinazione banale dà
 (a) $0\mathbf v_1+\dots+0\mathbf v_n=\mathbf 0$.
Si suppone per assurdo che siano dipendenti: esiste $\mathbf c'\neq\mathbf 0$ con
 (b) $c_1'\mathbf v_1+\dots+c_n'\mathbf v_n=\mathbf 0$.

*Conclusione (completamento mio, non presente nelle pagine lette).* (a) e (b) sono due scritture diverse dello **stesso** vettore $\mathbf 0$ come combinazione degli elementi di $\mathcal B$. Ma, per il teorema delle coordinate (vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Basi, dimensione e coordinate.md|Basi, dimensione e coordinate]]), in una base la scrittura di ogni vettore è **unica**: contraddizione. $\blacksquare$

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
