---
tags:
  - geometria-algebra-lineare
  - spazi-vettoriali
  - sottospazi
  - algebra-lineare
---
## Spazi vettoriali

### Motivazione

Gli stessi "fenomeni algebrici" compaiono in contesti diversi: nei vettori del piano e dello spazio ([[Politecnico/Geometria e Algebra Lineare/Teoria/Vettori geometrici liberi.md|Vettori geometrici liberi]]), negli elementi di $\mathbb R^n$ e $\mathbb C^n$, nelle matrici $m\times n$ (somma e prodotto per scalare, [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]]), nei polinomi, nelle successioni. In tutti questi casi sono definite una **somma** e un **prodotto per scalare** con le stesse proprietà. Isolando queste proprietà si ottiene la nozione astratta di **spazio vettoriale**: dimostrare un teorema una volta sola per ogni spazio vettoriale lo dimostra per tutti questi esempi insieme.

### Definizione

Sia $\mathbb K=\mathbb R$ oppure $\mathbb K=\mathbb C$ (in generale un campo). Un **spazio vettoriale su $\mathbb K$** (o **spazio lineare**) è un insieme $V\neq\varnothing$ con due operazioni:

- **somma**: $V\times V\to V$, $(\vec u,\vec v)\mapsto\vec u+\vec v\in V$;
- **prodotto per scalare**: $\mathbb K\times V\to V$, $(\lambda,\vec v)\mapsto\lambda\vec v\in V$;

(il fatto che il risultato resti **in $V$** è la richiesta di *chiusura* delle operazioni), che soddisfano, per ogni $\vec u,\vec v,\vec w\in V$ e $\lambda,\mu\in\mathbb K$:

| # | Proprietà | Formula |
|---|---|---|
| 1 | commutatività della somma | $\vec u+\vec v=\vec v+\vec u$ |
| 2 | associatività della somma | $(\vec u+\vec v)+\vec w=\vec u+(\vec v+\vec w)$ |
| 3 | esistenza dell'elemento neutro | $\exists\,\vec 0\in V:\ \vec v+\vec 0=\vec v\ \ \forall\vec v$ |
| 4 | esistenza dell'opposto | $\forall\vec v\ \exists\,{-\vec v}:\ \vec v+(-\vec v)=\vec 0$ |
| 5 | distributività rispetto alla somma di vettori | $\lambda(\vec u+\vec v)=\lambda\vec u+\lambda\vec v$ |
| 6 | distributività rispetto alla somma di scalari | $(\lambda+\mu)\vec v=\lambda\vec v+\mu\vec v$ |
| 7 | associatività mista | $\lambda(\mu\vec v)=(\lambda\mu)\vec v$ |
| 8 | neutro del prodotto per scalare | $1\cdot\vec v=\vec v$ |

Gli elementi di $V$ si chiamano **vettori** (qualunque sia la loro natura: matrici, polinomi, funzioni, ...), quelli di $\mathbb K$ **scalari**. Le proprietà 1-4 dicono che $(V,+)$ è un **gruppo abeliano**; 5-8 descrivono la compatibilità con gli scalari.

### Prime conseguenze degli assiomi

Dagli assiomi si deducono subito, per ogni $\vec v\in V$, $\lambda\in\mathbb K$:

1. **Unicità dello zero e dell'opposto.** Se $\vec 0,\vec 0'$ sono entrambi neutri allora $\vec 0=\vec 0+\vec 0'=\vec 0'$. Se $\vec w,\vec w'$ sono entrambi opposti di $\vec v$:
$$
\vec w=\vec w+\vec 0=\vec w+(\vec v+\vec w')=(\vec w+\vec v)+\vec w'=\vec 0+\vec w'=\vec w'.
$$
2. **$0\cdot\vec v=\vec 0$.** Infatti $0\vec v=(0+0)\vec v=0\vec v+0\vec v$; sommando l'opposto di $0\vec v$ a entrambi i membri si ottiene $\vec 0=0\vec v$.
3. **$\lambda\vec 0=\vec 0$.** Analogamente: $\lambda\vec 0=\lambda(\vec 0+\vec 0)=\lambda\vec 0+\lambda\vec 0$.
4. **$(-1)\vec v=-\vec v$.** Infatti $\vec v+(-1)\vec v=(1+(-1))\vec v=0\vec v=\vec 0$, quindi $(-1)\vec v$ è l'opposto di $\vec v$ e, per l'unicità, $=-\vec v$.
5. **Legge di annullamento del prodotto.** $\lambda\vec v=\vec 0\iff\lambda=0$ oppure $\vec v=\vec 0$.

### Esempi fondamentali

1. **$\mathbb K^n$** ($\mathbb R^n$ su $\mathbb R$, $\mathbb C^n$ su $\mathbb C$) con le operazioni componente per componente. Lo zero è $(0,\dots,0)$, l'opposto di $x$ è $-x=(-x_1,\dots,-x_n)$. Per $n=2,3$ coincide (tramite coordinate) con lo spazio dei vettori liberi del piano e dello spazio.

2. **$\mathbb C^n$ come spazio su $\mathbb C$** (stessa costruzione con gli scalari complessi). Notare che *lo stesso insieme* può essere spazio vettoriale su campi diversi: $\mathbb C^n$ è anche spazio su $\mathbb R$, ma è un altro spazio vettoriale.

3. **Spazio delle matrici** $M_{m,n}(\mathbb K):=\{A:\ A\ \text{è una matrice } m\times n \text{ a elementi in } \mathbb K\}$, con somma e prodotto per scalare elemento per elemento. Lo zero è la matrice nulla. È uno spazio vettoriale (le proprietà 1-8 sono quelle elencate in [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]]); si noti che qui il prodotto *tra matrici* non entra nella struttura di spazio vettoriale.

4. **Polinomi.** Un polinomio (a coefficienti reali) è
$$
p(x)=a_0+a_1x+a_2x^2+\dots+a_nx^n,\qquad a_i\in\mathbb R,
$$
di grado $\le n$ (il **grado** è il massimo $k$ con $a_k\ne0$; il polinomio nullo si tratta a parte). La somma di due polinomi (si sommano i coefficienti dello stesso grado) e il prodotto di un polinomio per un numero $\lambda$ (si moltiplicano tutti i coefficienti per $\lambda$) sono ancora polinomi. Quindi:
   - $\mathbb R[x]:=\{\text{tutti i polinomi in } x \text{ a coefficienti reali}\}$ è uno spazio vettoriale (di dimensione infinita);
   - $\mathbb R_n[x]:=\{p\in\mathbb R[x]:\ \deg p\le n\}$ è uno spazio vettoriale, ed è contenuto in $\mathbb R[x]$.

   **Attenzione:** l'insieme dei polinomi di grado **esattamente** $n$ **non** è uno spazio vettoriale: ad esempio $x^n$ e $-x^n+x$ hanno grado $n$ ma la loro somma $x$ ha grado $1$ (la somma esce dall'insieme). Non contiene nemmeno il polinomio nullo.

5. **Spazio delle successioni.** L'insieme delle successioni reali $(a_k)_{k\ge0}$ con somma e prodotto per scalare termine a termine,
$$
(a_k)+(b_k):=(a_k+b_k),\qquad\lambda(a_k):=(\lambda a_k),
$$
è uno spazio vettoriale (di dimensione infinita). Lo zero è la successione identicamente nulla. Lo stesso vale per lo spazio delle funzioni $f:X\to\mathbb R$ con operazioni punto per punto.

6. **Funzioni a valori in $\mathbb K$.** Sia $S\ne\varnothing$ un insieme. L'insieme delle funzioni $f:S\to\mathbb K$ è uno spazio vettoriale su $\mathbb K$ rispetto alle operazioni *punto per punto*:
   - $(f+g)(x):=f(x)+g(x)\ \ \forall x\in S$;
   - $(\lambda f)(x):=\lambda f(x)\ \ \forall x\in S,\ \forall\lambda\in\mathbb K$.

   Lo zero è la funzione identicamente nulla, l'opposto di $f$ è $-f$. Le successioni (esempio 5) sono il caso $S=\mathbb N$, e $\mathbb K^n$ il caso $S=\{1,\dots,n\}$.

7. **Funzioni a valori in uno spazio vettoriale.** Il campo $\mathbb K$ si identifica con $\mathbb K^1$, quindi è esso stesso uno spazio vettoriale su $\mathbb K$: l'esempio 6 si generalizza. Se $S\ne\varnothing$ e $V$ è uno spazio vettoriale su $\mathbb K$, le applicazioni $f:S\to V$ formano un (altro) spazio vettoriale su $\mathbb K$, con somma e prodotto per scalare definiti punto per punto come sopra (le operazioni a destra sono quelle di $V$).

8. **Spazio banale** $\{\vec 0\}$: è l'unico spazio con un solo elemento. Inoltre $\mathbb R^n$, i vettori liberi del piano e quelli dello spazio euclideo sono esempi di spazio vettoriale su $\mathbb R$, mentre $\mathbb C^n$ lo è su $\mathbb C$.

### Sottospazi vettoriali

Non tutti i **sottoinsiemi** di uno spazio vettoriale sono a loro volta spazi vettoriali. Quelli che lo sono (con le stesse operazioni di $V$) si chiamano **sottospazi**.

**Definizione.** Sia $V$ uno spazio vettoriale su $\mathbb K$. Un sottoinsieme $W\subseteq V$ si dice **sottospazio vettoriale** di $V$ (si scrive $W\le V$, nell'appunto $W<V$) se:

1. $W\ne\varnothing$ (equivalentemente $\vec 0\in W$);
2. $W$ è **chiuso rispetto alla somma**: $\vec u,\vec v\in W\Rightarrow\vec u+\vec v\in W$;
3. $W$ è **chiuso rispetto al prodotto per scalare**: $\lambda\in\mathbb K,\ \vec v\in W\Rightarrow\lambda\vec v\in W$.

In altre parole: nel sottoinsieme $W$ si può fare somma e prodotto per scalare *senza uscirne*. Le due condizioni di chiusura si riassumono in una sola:

$$
\lambda\vec u+\mu\vec v\in W\qquad\forall\ \vec u,\vec v\in W,\ \forall\lambda,\mu\in\mathbb K .
$$

**Teorema (criterio dei sottospazi).** Se $W\le V$ allora $W$, con le operazioni indotte da $V$, è esso stesso uno spazio vettoriale. Viceversa, se $W\subseteq V$ è chiuso per somma e prodotto per scalare ed è non vuoto, è un sottospazio.

*Dimostrazione.* Le proprietà 1, 2, 5, 6, 7, 8 valgono in $W$ perché valgono in tutto $V$ (sono uguaglianze tra elementi di $V$, e gli elementi di $W$ sono elementi di $V$). Restano le proprietà di esistenza: $\vec 0\in W$ perché $W\ne\varnothing$, quindi esiste $\vec w\in W$ e $0\cdot\vec w=\vec 0\in W$ per la chiusura; l'opposto di $\vec v\in W$ è $(-1)\vec v\in W$ ancora per la chiusura. $\blacksquare$

#### Esempi e controesempi (in $\mathbb R^2$)

- **Sottospazio:** la retta per l'origine $W=\{(x,y):\ y=2x\}$. Infatti $(0,0)\in W$; se $(a,2a),(b,2b)\in W$ allora $(a+b,\,2(a+b))\in W$ e $\lambda(a,2a)=(\lambda a,2\lambda a)\in W$.
- **Non sottospazio:** la retta $\{(x,y):\ y=2x+1\}$, che non passa per l'origine ($\vec 0\notin W$).
- **Non sottospazio:** il primo quadrante $\{(x,y):\ x,y\ge0\}$: è chiuso per la somma, ma **non** per il prodotto per scalare (moltiplicando per $\lambda=-1$ si esce).
- **Non sottospazio:** l'unione dei due assi coordinati $\{xy=0\}$: $(1,0)+(0,1)=(1,1)\notin W$.

**Sottospazi banali.** Ogni spazio $V$ ha sempre almeno due sottospazi: $\{\vec 0\}$ e $V$ stesso.

**Osservazione (ogni sottospazio contiene l'origine).** Se $W$ è un sottospazio di $V$, per definizione $W\ne\varnothing$, quindi contiene un vettore $\vec u$ e, per la chiusura rispetto al prodotto per scalare, $\lambda\vec u\in W$ per ogni $\lambda\in\mathbb K$. Ponendo $\lambda=0$:

$$
\vec 0=0\cdot\vec u\in W .
$$

**Ogni sottospazio contiene il vettore nullo**: è il criterio più rapido per escludere che un insieme sia un sottospazio (se $\vec 0\notin W$, allora $W$ non lo è).

#### Altri esempi in $\mathbb R^3$ e negli spazi di funzioni

- **Esempio 1 (piano coordinato).** $W:=\{(x,y,0):\ x,y\in\mathbb R\}$ è un sottospazio di $\mathbb R^3$: $W\subseteq\mathbb R^3$, $W\neq\varnothing$; se $\vec u=(u_1,u_2,u_3),\vec v=(v_1,v_2,v_3)\in W$ allora $u_3=v_3=0$ e $\vec u+\vec v=(u_1+v_1,u_2+v_2,0)\in W$; analogamente $\lambda\vec u\in W$.
- **Esempio 2 (sfera unitaria).** $W:=\{(x,y,z):\ x^2+y^2+z^2=1\}$ è un sottoinsieme non vuoto di $\mathbb R^3$ ma **non** un sottospazio: viola la chiusura per prodotto per scalare ($\vec u=(1,0,0)\in W$ ma $2\vec u=(2,0,0)\notin W$). Non contiene neanche l'origine.
- **Esempio 3 (sottospazio banale).** Per ogni spazio vettoriale $V$, $W:=\{\vec 0\}$ è un sottospazio, detto **sottospazio banale** (come $V$ stesso).
- **Esempio 4 (funzioni differenziabili).** Sia $V:=\{\text{funzioni } f:\mathbb R\to\mathbb R\}$ (spazio vettoriale su $\mathbb R$ con le operazioni punto per punto) e $W:=\{f:\mathbb R\to\mathbb R\ \text{differenziabili}\}$. Se $f,g\in W$ e $\lambda\in\mathbb R$, allora $f+g$ e $\lambda f$ sono differenziabili: $W$ è un sottospazio di $V$.
- **Esempio 5 (piani in $\mathbb R^3$).** Sia $W:=\{(x,y,z)\in\mathbb R^3:\ ax+by+cz=d\}$ con $a^2+b^2+c^2\ne0$ (il piano di equazione data).
  - Se $d\ne0$, $W$ **non** è un sottospazio, perché $\vec 0=(0,0,0)\notin W$.
  - Se $d=0$, $W$ è un sottospazio: $\vec 0\in W$; se $\vec u=(x_1,y_1,z_1)$ e $\vec v=(x_2,y_2,z_2)$ sono in $W$, cioè $ax_1+by_1+cz_1=0$ e $ax_2+by_2+cz_2=0$, sommando $a(x_1+x_2)+b(y_1+y_2)+c(z_1+z_2)=0$, quindi $\vec u+\vec v\in W$; e $a(\lambda x_1)+b(\lambda y_1)+c(\lambda z_1)=\lambda\cdot0=0$, quindi $\lambda\vec u\in W$.

  **Conclusione:** un piano di $\mathbb R^3$ è un sottospazio di $\mathbb R^3$ **se e solo se passa per l'origine**. (Analogamente per le rette.)

Per la costruzione del più piccolo sottospazio contenente dei vettori assegnati (span) si veda [[Politecnico/Geometria e Algebra Lineare/Teoria/Combinazioni lineari e sottospazio generato.md|Combinazioni lineari e sottospazio generato]].

#### Esempi importanti

1. **Soluzioni di un sistema omogeneo.** Per $A\in M_{m,n}(\mathbb K)$ l'insieme
$$
\ker A=\{x\in\mathbb K^n:\ Ax=0\}
$$
è un sottospazio di $\mathbb K^n$: se $Ax=0$ e $Ay=0$ allora $A(\lambda x+\mu y)=\lambda Ax+\mu Ay=0$ (per le proprietà del prodotto matrice-vettore). Al contrario, l'insieme delle soluzioni di un sistema **non omogeneo** $Ax=b$, $b\ne0$, **non** è un sottospazio (non contiene $0$): si veda [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Sistemi lineari e teorema di Rouché-Capelli]].
2. **Polinomi di grado $\le n$** sono un sottospazio di $\mathbb R[x]$: $\mathbb R_0[x]\le\mathbb R_1[x]\le\mathbb R_2[x]\le\cdots\le\mathbb R[x]$.
3. **Matrici simmetriche** $\{A\in M_{n,n}:\ A^{\mathsf T}=A\}$ e **matrici diagonali** (e **triangolari superiori**) sono sottospazi di $M_{n,n}(\mathbb K)$. Le matrici **invertibili** *non* sono un sottospazio (non contengono la matrice nulla e la somma di invertibili può non esserlo, ad esempio $I+(-I)=0$).
4. **Intersezione.** Se $W_1,W_2\le V$ allora $W_1\cap W_2\le V$ (basta verificare la chiusura, che segue da quella di entrambi). L'**unione** invece in generale non è un sottospazio (si veda l'esempio dei due assi).

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Vettori geometrici liberi.md|Vettori geometrici liberi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Insiemi, vettori e sistemi lineari — nozioni di base.md|Insiemi, vettori e sistemi lineari — nozioni di base]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Combinazioni lineari e sottospazio generato.md|Combinazioni lineari e sottospazio generato]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni (terminologia generale).md|Applicazioni (terminologia generale)]]
- [[Politecnico/Analisi 1/Teoria/Numeri complessi.md|Analisi — Numeri complessi]]
