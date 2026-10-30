---
tags:
  - geometria-algebra-lineare
  - esercizi
  - applicazioni-lineari
  - nucleo-immagine
  - intersezione-sottospazi
  - posizione-reciproca
---
Esercizio sul modello della Parte B della prova in itinere (11-11-2025). Non è un testo d'esame: è una simulazione. Prova a risolverlo prima di guardare le soluzioni.

## Collegamenti alla teoria

- [[Applicazioni lineari, nucleo e immagine|Applicazioni lineari, nucleo e immagine]]
- [[Basi di nucleo, immagine e span|Basi di nucleo, immagine e span]]
- [[Rango e teorema di nullità più rango|Rango e teorema di nullità più rango]]
- [[Sistemi lineari e teorema di Rouché-Capelli|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Intersezione, somma e somma diretta di sottospazi — formula di Grassmann|Intersezione, somma e somma diretta di sottospazi]]
- [[Posizione reciproca di rette e piani|Posizione reciproca di rette e piani]]

---

## Testo

Sia $L:\mathbb R^3\to\mathbb R[t]_{\le2}$ definita da
$$
L\begin{pmatrix}a\\b\\c\end{pmatrix}=(a-b)+(b-c)t+(a-c)t^2 .
$$

**a)** Trovare una base di $\operatorname{Im}L$ e la dimensione di $\ker L$.

**b)** Data $F\begin{pmatrix}a\\b\\c\end{pmatrix}=b+(b-c)t+(a+b)t^2$, trovare una base di $H=\{v\in\mathbb R^3: L(v)=F(v)\}$.

**c)** Dato $K=\operatorname{span}\left\{\begin{pmatrix}1\\1\\0\end{pmatrix},\begin{pmatrix}1\\0\\-1\end{pmatrix}\right\}$, trovare una base di $H\cap K$.

**d)** Verificare che $\ell_1=\{v\in\mathbb R^3: L(v)=1+t+2t^2\}$ è una retta. Determinare la posizione reciproca con la retta $\ell_2:\ \mathbf r=\begin{pmatrix}0\\0\\1\end{pmatrix}+u\begin{pmatrix}1\\-1\\0\end{pmatrix}$, $u\in\mathbb R$.

**e)** Per quali $p=c_0+c_1t+c_2t^2$ l'insieme $\{v\in\mathbb R^3: L(v)=p\}$ è non vuoto?

---

## Soluzioni

**Idea di fondo.** Un polinomio $c_0+c_1t+c_2t^2$ è identificato dalle sue coordinate $(c_0,c_1,c_2)^T$ rispetto alla base $\{1,t,t^2\}$. Così i conti sui polinomi diventano conti in $\mathbb R^3$. Due polinomi sono uguali se e solo se hanno tutti i coefficienti uguali: da qui nascono tutti i sistemi dell'esercizio.

### a) Immagine e nucleo

$\operatorname{Im}L$ è generata dalle immagini della base canonica, perché per linearità
$$
L\begin{pmatrix}a\\b\\c\end{pmatrix}=a\,L(e_1)+b\,L(e_2)+c\,L(e_3).
$$

**Passo 1: immagini della base canonica.**

| Vettore | $a-b$ | $b-c$ | $a-c$ | Polinomio | Coordinate |
|---|---|---|---|---|---|
| $e_1$ | $1$ | $0$ | $1$ | $1+t^2$ | $(1,0,1)^T$ |
| $e_2$ | $-1$ | $1$ | $0$ | $-1+t$ | $(-1,1,0)^T$ |
| $e_3$ | $0$ | $-1$ | $-1$ | $-t-t^2$ | $(0,-1,-1)^T$ |

**Passo 2: riduzione.** Si mettono le coordinate in colonna e si riduce per righe:
$$
\begin{bmatrix}1&-1&0\\0&1&-1\\1&0&-1\end{bmatrix}
\xrightarrow{R_3-R_1}
\begin{bmatrix}1&-1&0\\0&1&-1\\0&1&-1\end{bmatrix}
\xrightarrow{R_3-R_2}
\begin{bmatrix}1&-1&0\\0&1&-1\\0&0&0\end{bmatrix}.
$$
I pivot sono nelle colonne 1 e 2, quindi il rango è 2.

**Passo 3: base.** Si prendono le colonne dei pivot **della matrice di partenza**, perché le operazioni sulle righe cambiano le colonne:
$$
\mathcal B_{\operatorname{Im}L}=\{1+t^2,\ -1+t\}.
$$
Verifica: $-t-t^2=-(1+t^2)-(-1+t)$, quindi il terzo polinomio è superfluo.

**Nucleo.** Per il teorema di nullità più rango, $\dim\ker L=3-2=1$. Calcolo diretto, imponendo $L(v)=0$:
$$
\begin{cases}a-b=0\\ b-c=0\\ a-c=0\end{cases}\iff a=b=c,
$$
dove la terza equazione è implicata dalle prime due. Quindi $\ker L=\operatorname{span}\{(1,1,1)^T\}$.

### b) Il sottospazio $H$

$H$ contiene i vettori su cui $L$ e $F$ danno lo stesso polinomio. Si uguagliano i coefficienti:
$$
\begin{cases}
a-b=b & \text{(costante)}\\
b-c=b-c & (t)\\
a-c=a+b & (t^2)
\end{cases}
\iff
\begin{cases}a=2b\\ c=-b\end{cases}
$$
La seconda equazione è sempre vera e non dà condizioni. Restano due condizioni su tre variabili, quindi $b$ è libera:
$$
v=\begin{pmatrix}2b\\b\\-b\end{pmatrix}=b\begin{pmatrix}2\\1\\-1\end{pmatrix},
\qquad
\mathcal B_H=\left\{\begin{pmatrix}2\\1\\-1\end{pmatrix}\right\},\quad \dim H=1 .
$$
Verifica: $L(2,1,-1)^T=F(2,1,-1)^T=1+2t+3t^2$.

### c) L'intersezione $H\cap K$

$H\cap K\subseteq H$ e $\dim H=1$, quindi ci sono solo due possibilità: $H\cap K=H$ se $(2,1,-1)^T\in K$, altrimenti $H\cap K=\{0\}$.

Si cerca una combinazione lineare dei generatori di $K$:
$$
\alpha\begin{pmatrix}1\\1\\0\end{pmatrix}+\beta\begin{pmatrix}1\\0\\-1\end{pmatrix}=\begin{pmatrix}2\\1\\-1\end{pmatrix}
\iff
\begin{cases}\alpha+\beta=2\\ \alpha=1\\ -\beta=-1\end{cases}
$$
La seconda e la terza danno $\alpha=\beta=1$. La prima è il controllo: $1+1=2$, vera. Quindi $(2,1,-1)^T\in K$ e
$$
H\cap K=H,\qquad \mathcal B_{H\cap K}=\left\{\begin{pmatrix}2\\1\\-1\end{pmatrix}\right\}.
$$

### d) La retta $\ell_1$ e la posizione reciproca

**$\ell_1$ è una retta.** Si uguagliano i coefficienti di $L(v)$ e di $1+t+2t^2$:
$$
\begin{cases}a-b=1\\ b-c=1\\ a-c=2\end{cases}
$$
La terza è la somma delle prime due, quindi il sistema è compatibile, ha rango 2 e una variabile libera. Con $c=s$ si ottiene $b=1+s$ e $a=2+s$:
$$
\ell_1:\ \begin{pmatrix}a\\b\\c\end{pmatrix}=\begin{pmatrix}2\\1\\0\end{pmatrix}+s\begin{pmatrix}1\\1\\1\end{pmatrix},\quad s\in\mathbb R .
$$
Verifica: $L(2,1,0)^T=1+t+2t^2$.

La direzione è il generatore di $\ker L$: le soluzioni di $L(v)=p$ sono sempre una soluzione particolare più il nucleo.

**Parallelismo.** Da $(1,-1,0)^T=\lambda(1,1,1)^T$ seguirebbe $\lambda=1$ e $\lambda=-1$: impossibile. Le rette non sono parallele.

**Intersezione.** Si usano due parametri diversi, perché il punto comune può trovarsi a valori diversi sulle due rette:
$$
\begin{pmatrix}2+s\\1+s\\s\end{pmatrix}=\begin{pmatrix}u\\-u\\1\end{pmatrix}
\iff
\begin{cases}2+s=u\\ 1+s=-u\\ s=1\end{cases}
$$
Da $s=1$ si ha $u=3$, e la seconda equazione diventa $2=-3$: impossibile. Le rette non si incontrano.

Non sono parallele e non si incontrano, quindi $\ell_1$ e $\ell_2$ sono **sghembe**.

### e) La condizione su $p$

L'insieme è non vuoto se e solo se $p\in\operatorname{Im}L$, cioè se è compatibile il sistema
$$
\begin{cases}a-b=c_0\\ b-c=c_1\\ a-c=c_2\end{cases}
$$
Sommando le prime due si ottiene $a-c=c_0+c_1$. La terza dice $a-c=c_2$. Quindi il sistema è compatibile se e solo se
$$
c_0+c_1=c_2 .
$$
Se la condizione vale, la terza equazione è ridondante e ci sono infinite soluzioni. Se non vale, l'insieme è vuoto.

| $p$ | $c_0+c_1$ | $c_2$ | Insieme |
|---|---|---|---|
| $1+t+2t^2$ | $2$ | $2$ | non vuoto: è $\ell_1$ |
| $1+t+t^2$ | $2$ | $1$ | vuoto |

Controllo con il punto a): una condizione su 3 coefficienti dà dimensione $3-1=2=\dim\operatorname{Im}L$. Inoltre i polinomi della base la soddisfano: $1+t^2$ dà $1+0=1$ e $-1+t$ dà $-1+1=0$.
