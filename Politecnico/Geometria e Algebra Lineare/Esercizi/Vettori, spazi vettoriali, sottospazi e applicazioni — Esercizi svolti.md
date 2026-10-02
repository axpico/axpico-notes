---
tags:
  - geometria-algebra-lineare
  - esercizi
  - vettori
  - spazi-vettoriali
  - sottospazi
  - span
  - applicazioni
  - matrice-inversa
---
Dieci esercizi, in ordine di difficoltà crescente, per **capire e fissare** gli argomenti della Lezione 3: inversa di un prodotto, vettori liberi (equivalenza, somma, differenza, prodotto per scalare), spazi vettoriali, sottospazi, combinazioni lineari e span, applicazioni (iniettività, suriettività, controimmagini). Prova a risolverli da solo/a prima di guardare le soluzioni.

## Collegamenti alla teoria

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]] (Teorema 6: inversa del prodotto)
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Vettori geometrici liberi.md|Vettori geometrici liberi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Combinazioni lineari e sottospazio generato.md|Combinazioni lineari e sottospazio generato]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni (terminologia generale).md|Applicazioni (terminologia generale)]]

---

## Testi

**1. Inversa di un prodotto (calcolo).** Siano
$$
A=\begin{bmatrix}1&1\\1&2\end{bmatrix},\qquad B=\begin{bmatrix}2&1\\1&1\end{bmatrix}.
$$
(a) Calcola $A^{-1}$, $B^{-1}$ e $AB$. (b) Calcola $(AB)^{-1}$ direttamente con la formula $2\times2$ e verifica che coincide con $B^{-1}A^{-1}$. (c) Verifica che $A^{-1}B^{-1}\neq(AB)^{-1}$.

**2. Conseguenze del Teorema 6.** Siano $A,B$ matrici quadrate di ordine $n$.
(a) Mostra che se $A$ è singolare allora $AB$ è singolare, per ogni $B$. (Applicazione: $A=\begin{bmatrix}1&2\\2&4\end{bmatrix}$.)
(b) Mostra che se $A$ è invertibile e $A^2=A$ allora $A=I_n$.
(c) Mostra che $(ABC)^{-1}=C^{-1}B^{-1}A^{-1}$ se $A,B,C$ sono invertibili.

**3. Vettori in un parallelogramma.** Sia $ABCD$ un parallelogramma e siano $\vec u=\overrightarrow{AB}$, $\vec v=\overrightarrow{AD}$. Esprimi in funzione di $\vec u,\vec v$: (a) $\overrightarrow{AC}$; (b) $\overrightarrow{BD}$; (c) $\overrightarrow{CA}$; (d) $\overrightarrow{AM}$, con $M$ punto medio di $BC$; (e) $\overrightarrow{AO}$, con $O$ intersezione delle diagonali. Deduci che le diagonali si dimezzano a vicenda.

**4. Equivalenza di segmenti orientati e traslazioni (in coordinate).** Nel piano con coordinate, un segmento orientato $\overrightarrow{PQ}$ con $P=(p_1,p_2)$, $Q=(q_1,q_2)$ ha le stesse lunghezza, direzione e verso di $\overrightarrow{P'Q'}$ se e solo se $Q-P=Q'-P'$ (componente per componente). Considera
$s_1=\overrightarrow{(0,0)(2,1)}$, $s_2=\overrightarrow{(3,1)(5,2)}$, $s_3=\overrightarrow{(1,2)(2,4)}$, $s_4=\overrightarrow{(4,3)(2,2)}$.
(a) Quali sono equivalenti a $s_1$? Per gli altri, dire quale condizione (lunghezza, direzione, verso) fallisce. (b) Sia $\vec v$ il vettore libero rappresentato da $s_1$: trova l'unico punto $B$ tale che $\vec v=\overrightarrow{AB}$ con $A=(-1,4)$ e scrivi $\tau_{\vec v}(x,y)$. (c) Sia $\vec u$ rappresentato da $\overrightarrow{(0,0)(1,2)}$: calcola $\vec u+\vec v$, $\vec v+\vec u$ e $\vec u-\vec v$.

**5. Prodotto per scalare.** Sia $\vec v=\overrightarrow{AB}$ con $A=(1,1)$, $B=(3,2)$. Trova il punto $C$ tale che $\overrightarrow{AC}=\lambda\vec v$ per $\lambda=3$, $\lambda=-\tfrac12$, $\lambda=0$. Verifica in ogni caso la relazione $|\overrightarrow{AC}|=|\lambda|\,|\overrightarrow{AB}|$, che $A,B,C$ sono allineati e come si dispone $C$ rispetto alla semiretta $AB$.

**6. Dagli assiomi.** In uno spazio vettoriale $V$ su $\mathbb K$, dimostra usando **solo** gli assiomi (i)-(viii):
(a) $0\cdot\vec v=\vec 0$; (b) $(-1)\vec v=-\vec v$; (c) se $\lambda\vec v=\vec 0$ allora $\lambda=0$ oppure $\vec v=\vec 0$.

**7. Sottospazio o no?** Stabilisci se è un sottospazio (con le operazioni usuali), giustificando:
(a) $W_1=\{(x,y,z)\in\mathbb R^3: x+y+z=0\}$;
(b) $W_2=\{(x,y,z)\in\mathbb R^3: x+y+z=1\}$;
(c) $W_3=\{(x,y)\in\mathbb R^2: xy\ge0\}$;
(d) $W_4=\{f:\mathbb R\to\mathbb R:\ f(0)=0\}$;
(e) $W_5=\{f:\mathbb R\to\mathbb R:\ f(0)=1\}$;
(f) $W_6=\{A\in M_{2,2}(\mathbb R):\ \det A=0\}$;
(g) $W_7=\{f:\mathbb R\to\mathbb R:\ f \text{ pari}\}$ (cioè $f(-x)=f(x)\ \forall x$);
(h) $W_8=\{p\in\mathbb R[x]:\ \deg p=3\}$.

**8. Appartenenza allo span.** Sia $\vec v_1=(1,0,1)$, $\vec v_2=(0,1,1)$ in $\mathbb R^3$. (a) Stabilisci se $\vec w_1=(3,-2,1)$ e $\vec w_2=(2,-1,3)$ appartengono a $\operatorname{span}\{\vec v_1,\vec v_2\}$, e in caso affermativo trova i coefficienti. (b) Interpreta il risultato con Rouché-Capelli. (c) Trova un'equazione cartesiana del piano $\operatorname{span}\{\vec v_1,\vec v_2\}$ e verifica con essa le risposte di (a).

**9. Soluzioni di un sistema come span.** Considera in $\mathbb R^4$ il sistema omogeneo
$$
\begin{cases}x_1+x_2-x_3+2x_4=0\\ x_2+x_3-x_4=0\end{cases}
$$
(a) Mostra che l'insieme $S$ delle soluzioni è un sottospazio e scrivilo come span di vettori. (b) Cambia il secondo membro in $b=(1,0)^{\mathsf T}$: descrivi l'insieme $S_b$ delle soluzioni e spiega perché **non** è un sottospazio.

**10. Applicazioni.** (a) Sia $f:\mathbb R\to\mathbb R$, $f(x)=x^2$. Calcola $f([-2,3])$, $f^{-1}((-\infty,4))$, $f^{-1}([-1,0])$, $f^{-1}(\{9\})$. (b) Stabilisci se sono iniettive/suriettive: $\sin:\mathbb R\to\mathbb R$; $\sin:\mathbb R\to[-1,1]$; $\exp:\mathbb R\to\mathbb R$; $\exp:\mathbb R\to(0,+\infty)$; $x\mapsto 2x+1$ da $\mathbb R$ in $\mathbb R$. (c) Per $T_A:\mathbb R^2\to\mathbb R^2$, $T_A(\vec x)=A\vec x$, con $A=\begin{bmatrix}1&2\\2&4\end{bmatrix}$ e $B=\begin{bmatrix}1&2\\3&4\end{bmatrix}$ stabilisci se $T_A$, $T_B$ sono iniettive, suriettive, biiettive; se biiettiva, scrivi l'inversa.

---

## Soluzioni

### Esercizio 1

**(a)** $\det A=2-1=1$, $\det B=2-1=1$. Con la formula $2\times2$:
$$
A^{-1}=\begin{bmatrix}2&-1\\-1&1\end{bmatrix},\qquad B^{-1}=\begin{bmatrix}1&-1\\-1&2\end{bmatrix},\qquad AB=\begin{bmatrix}1\cdot2+1\cdot1&1\cdot1+1\cdot1\\1\cdot2+2\cdot1&1\cdot1+2\cdot1\end{bmatrix}=\begin{bmatrix}3&2\\4&3\end{bmatrix}.
$$

**(b)** $\det(AB)=9-8=1$, quindi $(AB)^{-1}=\begin{bmatrix}3&-2\\-4&3\end{bmatrix}$. Inoltre
$$
B^{-1}A^{-1}=\begin{bmatrix}1&-1\\-1&2\end{bmatrix}\begin{bmatrix}2&-1\\-1&1\end{bmatrix}=\begin{bmatrix}2+1&-1-1\\-2-2&1+2\end{bmatrix}=\begin{bmatrix}3&-2\\-4&3\end{bmatrix}=(AB)^{-1}.\ \checkmark
$$

**(c)**
$$
A^{-1}B^{-1}=\begin{bmatrix}2&-1\\-1&1\end{bmatrix}\begin{bmatrix}1&-1\\-1&2\end{bmatrix}=\begin{bmatrix}3&-4\\-2&3\end{bmatrix}\ne\begin{bmatrix}3&-2\\-4&3\end{bmatrix}.
$$
L'ordine dei fattori **si inverte** perché il prodotto non è commutativo.

### Esercizio 2

**(a)** Per il Teorema 6, $AB$ è invertibile $\iff$ $A$ e $B$ lo sono. Se $A$ è singolare, la condizione "$A$ e $B$ invertibili" è falsa, quindi $AB$ non è invertibile. Per $A=\begin{bmatrix}1&2\\2&4\end{bmatrix}$: $\det A=4-4=0$, quindi $A$ è singolare e $AB$ è singolare **per ogni** $B$ $2\times2$ (la seconda riga di $A$ è il doppio della prima, e lo stesso vale per $AB$: ha rango $\le1$).

**(b)** $A^2=A$ e $A$ invertibile: moltiplicando a sinistra per $A^{-1}$,
$$
A^{-1}(AA)=A^{-1}A\ \Rightarrow\ (A^{-1}A)A=I\ \Rightarrow\ A=I_n .
$$
(Quindi l'unica matrice invertibile idempotente è l'identità; per esempio $\begin{bmatrix}1&0\\0&0\end{bmatrix}$ è idempotente ma singolare.)

**(c)** Applichiamo due volte il Teorema 6: $ABC=(AB)C$ è invertibile perché $AB$ e $C$ lo sono, e
$$
(ABC)^{-1}=C^{-1}(AB)^{-1}=C^{-1}B^{-1}A^{-1}.
$$

### Esercizio 3

Con origine $A$: $\vec u=\overrightarrow{AB}$, $\vec v=\overrightarrow{AD}$. In un parallelogramma $\overrightarrow{BC}=\overrightarrow{AD}=\vec v$ (lati opposti equivalenti) e $\overrightarrow{DC}=\overrightarrow{AB}=\vec u$.

**(a)** Regola del triangolo: $\overrightarrow{AC}=\overrightarrow{AB}+\overrightarrow{BC}=\vec u+\vec v$.

**(b)** $\overrightarrow{BD}$ va dalla punta di $\vec u$ alla punta di $\vec v$ (stessa origine $A$): $\overrightarrow{BD}=\vec v-\vec u$. Verifica: $\vec u+(\vec v-\vec u)=\vec v=\overrightarrow{AD}$ ✓.

**(c)** $\overrightarrow{CA}=-\overrightarrow{AC}=-\vec u-\vec v$.

**(d)** $M$ è il punto medio di $BC$ e $\overrightarrow{BM}=\tfrac12\overrightarrow{BC}=\tfrac12\vec v$, quindi $\overrightarrow{AM}=\overrightarrow{AB}+\overrightarrow{BM}=\vec u+\tfrac12\vec v$.

**(e)** Il punto medio $O_1$ di $AC$ ha $\overrightarrow{AO_1}=\tfrac12(\vec u+\vec v)$. Il punto medio $O_2$ di $BD$ ha $\overrightarrow{AO_2}=\overrightarrow{AB}+\tfrac12\overrightarrow{BD}=\vec u+\tfrac12(\vec v-\vec u)=\tfrac12(\vec u+\vec v)$. Per l'unicità del punto con dato vettore da $A$, $O_1=O_2=O$: **le diagonali si intersecano nel loro punto medio**, cioè si dimezzano a vicenda.

### Esercizio 4

**(a)** $Q-P$: $s_1$: $(2,1)$; $s_2$: $(5,2)-(3,1)=(2,1)$ ✓; $s_3$: $(2,4)-(1,2)=(1,2)$; $s_4$: $(2,2)-(4,3)=(-2,-1)$.
- $s_2\sim s_1$ (stessa differenza): **equivalente**.
- $s_3$: lunghezza $\sqrt{1+4}=\sqrt5=|s_1|$, ma $(1,2)$ non è parallelo a $(2,1)$: **fallisce la direzione**.
- $s_4$: lunghezza $\sqrt5$ e $(-2,-1)=-(2,1)$ è parallelo: **fallisce il verso** (è il vettore opposto $-\vec v$).

**(b)** $\vec v=(2,1)$ (differenza). L'unico $B$ con $\overrightarrow{AB}=\vec v$ per $A=(-1,4)$ è $B=A+(2,1)=(1,5)$. In generale $\tau_{\vec v}(x,y)=(x+2,\,y+1)$.

**(c)** $\vec u=(1,2)$, $\vec v=(2,1)$:
$\vec u+\vec v=(3,3)=\vec v+\vec u$ (commutatività). Differenza: con $A=(0,0)$, $B=\tau_{\vec v}(A)=(2,1)$, $C=\tau_{\vec u}(A)=(1,2)$ si ha $\overrightarrow{BC}=C-B=(-1,1)=\vec u-\vec v$. Verifica: $\vec v+(\vec u-\vec v)=(2,1)+(-1,1)=(1,2)=\vec u$ ✓.

### Esercizio 5

$\overrightarrow{AB}=(2,1)$, $|\overrightarrow{AB}|=\sqrt5$, $C=A+\lambda(2,1)$.

| $\lambda$ | $C$ | $\lvert\overrightarrow{AC}\rvert$ | verifica |
|---|---|---|---|
| $3$ | $(1+6,\,1+3)=(7,4)$ | $\sqrt{36+9}=3\sqrt5$ | $=3\sqrt5$ ✓, semiretta $AB$ (oltre $B$) |
| $-\tfrac12$ | $(1-1,\,1-\tfrac12)=(0,\tfrac12)$ | $\sqrt{1+\tfrac14}=\tfrac{\sqrt5}{2}$ | $=\tfrac12\sqrt5$ ✓, semiretta **complementare** (dalla parte opposta a $B$) |
| $0$ | $A=(1,1)$ | $0$ | $0\cdot\vec v=\vec 0$ |

In ogni caso $C$ sta sulla retta $AB$ (è $A+\lambda(B-A)$), quindi $A,B,C$ sono allineati.

### Esercizio 6

**(a)** $0\vec v=(0+0)\vec v\overset{(vi)}{=}0\vec v+0\vec v$. Sommando a entrambi i membri l'opposto di $0\vec v$ (esiste per (iv)) e usando (ii), (iii): $\vec 0=0\vec v$.

**(b)** $\vec v+(-1)\vec v\overset{(viii)}{=}1\vec v+(-1)\vec v\overset{(vi)}{=}(1+(-1))\vec v=0\vec v=\vec 0$ per (a). Quindi $(-1)\vec v$ è un opposto di $\vec v$. L'opposto è **unico**: se $\vec w,\vec w'$ sono opposti di $\vec v$, allora $\vec w=\vec w+\vec 0=\vec w+(\vec v+\vec w')=(\vec w+\vec v)+\vec w'=\vec w'$. Dunque $(-1)\vec v=-\vec v$.

**(c)** Se $\lambda=0$ non c'è nulla da dimostrare. Se $\lambda\ne0$ esiste $\lambda^{-1}\in\mathbb K$ e
$$
\vec v\overset{(viii)}{=}1\vec v=(\lambda^{-1}\lambda)\vec v\overset{(vii)}{=}\lambda^{-1}(\lambda\vec v)=\lambda^{-1}\vec 0=\vec 0,
$$
dove $\lambda^{-1}\vec 0=\vec 0$ segue da (v): $\lambda^{-1}\vec 0=\lambda^{-1}(\vec 0+\vec 0)=\lambda^{-1}\vec 0+\lambda^{-1}\vec 0$.

### Esercizio 7

Ricorda: serve $W\ne\varnothing$ (equivalentemente $\vec 0\in W$), chiusura per somma e per prodotto per scalare.

- **(a) Sì.** $\vec 0\in W_1$. Se $x_1+y_1+z_1=0$ e $x_2+y_2+z_2=0$, sommando $(x_1+x_2)+(y_1+y_2)+(z_1+z_2)=0$; e $\lambda x_1+\lambda y_1+\lambda z_1=\lambda\cdot0=0$. (Piano per l'origine.)
- **(b) No.** $\vec 0\notin W_2$ ($0+0+0\ne1$). Anche: $(1,0,0)+(0,1,0)=(1,1,0)$ ha somma $2\ne1$.
- **(c) No.** Chiuso per prodotto per scalare ($(\lambda x)(\lambda y)=\lambda^2xy\ge0$ per ogni $\lambda\in\mathbb R$), ma **non per la somma**: $(1,2),(-2,-1)\in W_3$ (prodotti $2$ e $2$) ma la somma $(-1,1)$ ha $xy=-1<0$.
- **(d) Sì.** La funzione nulla è in $W_4$; se $f(0)=g(0)=0$ allora $(f+g)(0)=0$ e $(\lambda f)(0)=0$.
- **(e) No.** La funzione nulla non è in $W_5$; inoltre $(f+g)(0)=2\ne1$.
- **(f) No.** $\operatorname{diag}(1,0)$ e $\operatorname{diag}(0,1)$ hanno $\det=0$ ma la somma $I_2$ ha $\det=1$. (Le matrici singolari non sono chiuse per somma.)
- **(g) Sì.** La funzione nulla è pari; se $f,g$ sono pari, $(f+g)(-x)=f(-x)+g(-x)=f(x)+g(x)=(f+g)(x)$ e $(\lambda f)(-x)=\lambda f(x)$.
- **(h) No.** Il polinomio nullo non ha grado $3$; inoltre $x^3+(-x^3+x)=x$ ha grado $1$ (non chiuso per somma). I polinomi di grado **$\le3$**, invece, sono un sottospazio.

### Esercizio 8

**(a)** Cerchiamo $\alpha,\beta$ con $\alpha\vec v_1+\beta\vec v_2=\vec w$, cioè $(\alpha,\beta,\alpha+\beta)=\vec w$.
- $\vec w_1=(3,-2,1)$: $\alpha=3$, $\beta=-2$; terza componente: $3+(-2)=1$ ✓. **Appartiene**: $\vec w_1=3\vec v_1-2\vec v_2$.
- $\vec w_2=(2,-1,3)$: $\alpha=2,\beta=-1$, ma $\alpha+\beta=1\ne3$. **Non appartiene.**

**(b)** Sia $M=[\vec v_1\mid\vec v_2]=\begin{bmatrix}1&0\\0&1\\1&1\end{bmatrix}$, $r(M)=2$. Per $\vec w_1$: $r([M\mid\vec w_1])=2=r(M)$, il sistema è compatibile (con $n=2=r$ incognite: **soluzione unica**, i coefficienti sono unici perché $\vec v_1,\vec v_2$ non sono paralleli). Per $\vec w_2$: l'ultima riga diventa $0=2$ dopo l'eliminazione, $r([M\mid\vec w_2])=3\ne2$: **sistema impossibile**.

**(c)** Un generico elemento dello span è $(a,b,a+b)$: le coordinate soddisfano $z=x+y$, cioè $x+y-z=0$ (piano per l'origine, come atteso). Verifiche: $\vec w_1$: $3-2-1=0$ ✓; $\vec w_2$: $2-1-3=-2\ne0$ ✗.

### Esercizio 9

**(a)** Risolviamo: dalla seconda equazione $x_2=-x_3+x_4$; sostituendo nella prima $x_1=-x_2+x_3-2x_4=(x_3-x_4)+x_3-2x_4=2x_3-3x_4$. Con parametri liberi $x_3=s$, $x_4=t$ (qui $r=2$, $n=4$, quindi $n-r=2$ parametri):
$$
(x_1,x_2,x_3,x_4)=(2s-3t,\,-s+t,\,s,\,t)=s\underbrace{(2,-1,1,0)}_{\vec a}+t\underbrace{(-3,1,0,1)}_{\vec b}.
$$
Quindi $S=\operatorname{span}\{\vec a,\vec b\}$, sottospazio di $\mathbb R^4$ per la Proposizione 1. Verifica di $\vec a$: $2-1-1+0=0$ ✓, $-1+1-0=0$ ✓; di $\vec b$: $-3+1-0+2=0$ ✓, $1+0-1=0$ ✓.

**(b)** Con $b=(1,0)$: $x_2=-x_3+x_4$, $x_1=1-x_2+x_3-2x_4=1+2x_3-3x_4$. Una soluzione particolare è $\vec p=(1,0,0,0)$ ($x_3=x_4=0$) e
$$
S_b=\{\vec p+s\vec a+t\vec b:\ s,t\in\mathbb R\}=\vec p+S .
$$
Non è un sottospazio perché $\vec 0\notin S_b$ (il sistema darebbe $0=1$ nella prima equazione); ogni sottospazio contiene $\vec 0$. È un **sottospazio affine**: un "piano" non passante per l'origine, traslato di $\vec p$ rispetto a $S$.

### Esercizio 10

**(a)** $f([-2,3])=[0,9]$ (il minimo è $f(0)=0$, il massimo $f(3)=9$). $f^{-1}((-\infty,4))=\{x:x^2<4\}=(-2,2)$. $f^{-1}([-1,0])=\{0\}$ (solo $x^2=0$). $f^{-1}(\{9\})=\{-3,3\}$.

**(b)**
- $\sin:\mathbb R\to\mathbb R$: **né iniettiva** ($\sin0=\sin\pi$) **né suriettiva** (immagine $[-1,1]\ne\mathbb R$).
- $\sin:\mathbb R\to[-1,1]$: **suriettiva**, non iniettiva.
- $\exp:\mathbb R\to\mathbb R$: **iniettiva** (strettamente crescente), non suriettiva (immagine $(0,+\infty)$).
- $\exp:\mathbb R\to(0,+\infty)$: **biiettiva**, con inversa $\ln$. *Cambiare il codominio cambia la suriettività.*
- $x\mapsto2x+1$: **biiettiva**, inversa $y\mapsto\frac{y-1}{2}$.

**(c)** $A\vec x=(x+2y)\,(1,2)$.
- $T_A$ **non suriettiva**: $\operatorname{im}T_A=\{\lambda(1,2)\}$ è una retta, $\ne\mathbb R^2$ (es. $(1,0)$ non ha controimmagini).
- $T_A$ **non iniettiva**: $T_A(-2,1)=(0,0)=T_A(0,0)$, quindi $(0,0)$ ha più di una controimmagine.
- Coerente con il Teorema 4: $\det A=0$, $A$ singolare.

$\det B=4-6=-2\ne0$, quindi $B$ è invertibile e $T_B$ è **biiettiva**: per ogni $\vec y$ l'equazione $B\vec x=\vec y$ ha l'unica soluzione $\vec x=B^{-1}\vec y$, quindi
$$
T_B^{-1}=T_{B^{-1}},\qquad B^{-1}=\frac1{-2}\begin{bmatrix}4&-2\\-3&1\end{bmatrix}=\begin{bmatrix}-2&1\\ \tfrac32&-\tfrac12\end{bmatrix}.
$$

---

## Cosa dovresti aver capito

- **1-2:** l'inversa di un prodotto si ottiene invertendo i fattori **in ordine inverso**; un prodotto con un fattore singolare è singolare.
- **3-5:** un vettore libero è un'intera classe di segmenti; somma = regola del triangolo/parallelogramma, differenza = "da punta a punta" con la stessa origine, prodotto per scalare allunga/accorcia e inverte il verso se $\lambda<0$.
- **6-7:** gli assiomi bastano per dedurre tutto; per un sottospazio controlla sempre $\vec 0$ e le due chiusure (un controesempio basta per escluderlo).
- **8-9:** appartenere a uno span = compatibilità di un sistema (Rouché-Capelli); le soluzioni di $A\vec x=\vec 0$ formano uno span, quelle di $A\vec x=\vec b\ne\vec 0$ no.
- **10:** iniettiva/suriettiva dipendono da **dominio e codominio**; $T_A$ è biiettiva $\iff$ $A$ invertibile.
