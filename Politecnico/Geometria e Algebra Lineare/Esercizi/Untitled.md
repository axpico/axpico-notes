# Sistemi lineari — Teoria ed esercizi

## 1. Definizioni

Un **sistema lineare** di $m$ equazioni in $n$ incognite $x_1,\dots,x_n$ è un insieme di condizioni

$$
\begin{cases}
A_1(x_1,\dots,x_n) = b_1\\
\vdots\\
A_m(x_1,\dots,x_n) = b_m
\end{cases}
$$

dove ogni $A_i$ è un **polinomio lineare** (di primo grado, senza termini misti né potenze) nelle incognite. Si distingue:

- la **matrice dei coefficienti** $A \in M_{m,n}(\mathbb{R})$: contiene solo i coefficienti delle incognite;
- la **matrice completa** (o *aumentata*) $A' = (A\,|\,b) \in M_{m,n+1}(\mathbb{R})$: la matrice dei coefficienti a cui si affianca la colonna dei termini noti $b$.

Il sistema si scrive in forma matriciale come

$$
A\underline{x} = \underline{b}, \qquad \underline{x}=\begin{pmatrix}x_1\\\vdots\\x_n\end{pmatrix} \in \mathbb{R}^n
$$

Se $\underline{b} = \underline{0}$ il sistema si dice **omogeneo**: $A\underline{x}=\underline 0$.

**Esempio illustrativo** (solo per fissare la notazione, non richiede soluzione):

$$
\begin{cases}
3x+2y+z\phantom{+0t}=2\\
x+y\phantom{+0z}+t=5\\
3x\phantom{+0y}+2z-5t=0
\end{cases}
\quad\Longrightarrow\quad
A=\begin{pmatrix}3&2&1&0\\1&1&0&1\\3&0&2&-5\end{pmatrix},\;
\underline b=\begin{pmatrix}2\\5\\0\end{pmatrix},\;
\underline x=\begin{pmatrix}x\\y\\z\\t\end{pmatrix}
$$

## 2. Metodo di eliminazione di Gauss (MEG)

Per studiare un sistema si riduce la matrice completa $A'$ a **scala** tramite operazioni elementari sulle righe (scambio, somma di un multiplo di una riga a un'altra, moltiplicazione per uno scalare non nullo): queste operazioni non cambiano l'insieme delle soluzioni. Il numero di **pivot** (elementi non nulli iniziali di ogni riga non nulla nella forma a scala) determina il **rango** della matrice.

## 3. Teorema di Rouché–Capelli

Dato $A\underline x = \underline b$ con $A\in M_{m,n}(\mathbb{R})$:

$$
\exists \text{ soluzioni} \iff \text{rk}(A) = \text{rk}(A'\,)
$$

Se le soluzioni esistono, l'insieme delle soluzioni ha

$$
\infty^{\,n-\text{rk}(A)} \quad \text{soluzioni, con } n-\text{rk}(A) \text{ parametri liberi.}
$$

In particolare se $\text{rk}(A)=n$ (numero di incognite) la soluzione è **unica** ($\infty^0$).

---

## Esercizio 1

Discutere il sistema

$$
\begin{cases}
x - y \phantom{+2z}= 3\\
3x - y + z = 10\\
-x + 5y + 2z = 1
\end{cases}
$$

**Matrice dei coefficienti** $A$ e **matrice completa** $A'$:

$$
A=\begin{pmatrix}1&-1&0\\3&-1&1\\-1&5&2\end{pmatrix}
\qquad
A'=\left(\begin{array}{ccc|c}1&-1&0&3\\3&-1&1&10\\-1&5&2&1\end{array}\right)
$$

Riduzione di $A'$ ($R_2 \to R_2-3R_1$, $R_3\to R_3+R_1$):

$$
\left(\begin{array}{ccc|c}1&-1&0&3\\0&2&1&1\\0&4&2&4\end{array}\right)
\xrightarrow{R_3\to R_3-2R_2}
\left(\begin{array}{ccc|c}1&-1&0&3\\0&2&1&1\\0&0&0&2\end{array}\right)
$$

Osservazioni sulla forma a scala finale:

- nella parte dei **coefficienti** i pivot sono in colonna 1 e colonna 2 → $\text{rk}(A)=2$;
- l'ultima riga $(0\;0\;0\mid 2)$ ha invece il pivot nella colonna dei termini noti → $\text{rk}(A')=3$.

Poiché $\text{rk}(A)=2 \ne \text{rk}(A')=3$, per Rouché-Capelli **il sistema è impossibile** (nessuna soluzione). La riga $0=2$ è infatti una contraddizione esplicita.

> *(Nella brutta copia i due ranghi erano stati confusi in un unico calcolo — qui sono tenuti separati come richiede il teorema.)*

---

## Esercizio 2

Discutere il sistema nelle incognite $x,y,z,t$:

$$
\begin{cases}
x+2y+z\phantom{+3t}=3\\
-3x-4y-z+3t=0\\
2x+2y+3z-3t=-6\\
3x+10y+3z+3t=1
\end{cases}
$$

$$
A'=\left(\begin{array}{cccc|c}
1&2&1&0&3\\
-3&-4&-1&3&0\\
2&2&3&-3&-6\\
3&10&3&3&1
\end{array}\right)
$$

$R_2\to R_2+3R_1$, $R_3\to R_3-2R_1$, $R_4\to R_4-3R_1$:

$$
\left(\begin{array}{cccc|c}
1&2&1&0&3\\
0&2&-1&3&9\\
0&-2&1&-3&-12\\
0&4&0&3&-8
\end{array}\right)
$$

$R_3\to R_3+R_2$, $R_4\to R_4-2R_2$:

$$
\left(\begin{array}{cccc|c}
1&2&1&0&3\\
0&2&-1&3&9\\
0&0&0&0&-3\\
0&0&2&-3&-26
\end{array}\right)
\xrightarrow{R_3\leftrightarrow R_4}
\left(\begin{array}{cccc|c}
1&2&1&0&3\\
0&2&-1&3&9\\
0&0&2&-3&-26\\
0&0&0&0&-3
\end{array}\right)
$$

L'ultima riga si legge $0=-3$: è **sempre falsa**, indipendentemente da come si continua la riduzione. Quindi:

$$
\text{rk}(A)=3 \ne \text{rk}(A')=4 \quad\Longrightarrow\quad \text{sistema impossibile.}
$$

---

## Esercizio 3 (matrice parametrica — solo discussione del rango)

$$
A' =
\left(\begin{array}{cccc|c}
1&2&-1&-1&0\\
2&5&2&-2&0\\
-1&-1&5&3&1\\
3&8&5&-1&1\\
3&9&0&1&\alpha
\end{array}\right)
$$

Dopo la riduzione con MEG si ottiene:

$$
\left(\begin{array}{cccc|c}
1&2&-1&-1&0\\
0&1&4&0&0\\
0&0&0&2&1\\
0&0&0&0&\alpha-2\\
0&0&0&0&0
\end{array}\right)
$$

- Nella parte dei coefficienti i pivot sono sempre 3 (colonne 1, 2, 4): $\text{rk}(A)=3$ per ogni $\alpha$.
- Se $\alpha \ne 2$: la quarta riga $(0\;0\;0\;0\mid \alpha-2)$ è un pivot in più $\Rightarrow \text{rk}(A')=4$.
- Se $\alpha = 2$: la quarta riga si annulla del tutto $\Rightarrow \text{rk}(A')=3$.

**Conclusione:**

$$
\begin{cases}
\alpha \ne 2: & \text{rk}(A)=3,\ \text{rk}(A')=4 \Rightarrow \text{nessuna soluzione}\\[4pt]
\alpha = 2: & \text{rk}(A)=\text{rk}(A')=3 \Rightarrow \infty^{4-3}=\infty^1 \text{ soluzioni}
\end{cases}
$$

> *(Nella brutta copia compariva "$\alpha=0$" per il secondo caso: è un errore di trascrizione, la condizione corretta — coerente col calcolo $\alpha-2$ — è $\alpha=2$.)*

**Bonus — soluzione esplicita per $\alpha=2$.** Dalle righe ridotte (incognite $x_1,x_2,x_3,x_4$):

$$
\begin{cases}
x_1+2x_2-x_3-x_4=0\\
x_2+4x_3=0\\
2x_4=1
\end{cases}
$$

Ponendo $x_3=t$ (parametro libero): $x_4=\tfrac12$, $x_2=-4t$, $x_1=-2x_2+x_3+x_4 = 8t+t+\tfrac12=9t+\tfrac12$. Quindi

$$
\underline x = \begin{pmatrix}1/2\\0\\0\\1/2\end{pmatrix} + t\begin{pmatrix}9\\-4\\1\\0\end{pmatrix}, \quad t\in\mathbb{R}.
$$

---

## Esercizio 4 (sistema parametrico completo)

Discutere al variare di $\alpha \in \mathbb{R}$:

$$
\begin{cases}
x - y + \alpha z = -1\\
\alpha x \phantom{-y}+ 2z = -2\\
\phantom{\alpha x -}\, y + z = -1
\end{cases}
$$

$$
A' = \left(\begin{array}{ccc|c}1&-1&\alpha&-1\\ \alpha&0&2&-2\\0&1&1&-1\end{array}\right)
$$

$R_2 \to R_2-\alpha R_1$:

$$
R_2 = (0,\; \alpha,\; 2-\alpha^2,\; \alpha-2)
$$

Scambio $R_2\leftrightarrow R_3$ (per avere un pivot "comodo" in seconda riga):

$$
\left(\begin{array}{ccc|c}1&-1&\alpha&-1\\0&1&1&-1\\0&\alpha&2-\alpha^2&\alpha-2\end{array}\right)
\xrightarrow{R_3\to R_3-\alpha R_2}
\left(\begin{array}{ccc|c}1&-1&\alpha&-1\\0&1&1&-1\\0&0&-(\alpha^2+\alpha-2)&2\alpha-2\end{array}\right)
$$

Il terzo pivot esiste (ed è non nullo) se e solo se

$$
\alpha^2+\alpha-2 \ne 0 \iff (\alpha+2)(\alpha-1)\ne 0 \iff \alpha \ne -2 \ \text{ e } \ \alpha \ne 1.
$$

### Caso $\alpha \ne -2,\, 1$: 3 pivot, soluzione unica

$\text{rk}(A)=\text{rk}(A')=3=n \Rightarrow \infty^0$ soluzioni (unica).

Risolvendo per sostituzione all'indietro (da $y=-1-z$, sostituendo nelle altre due equazioni ed eliminando $z$):

$$
z = \frac{-2}{\alpha+2}, \qquad y = \frac{-\alpha}{\alpha+2}, \qquad x = \frac{-2}{\alpha+2}.
$$

(si nota $x=z$; verificabile per sostituzione diretta nelle 3 equazioni originali).

### Caso $\alpha = 1$

La matrice diventa

$$
\left(\begin{array}{ccc|c}1&-1&1&-1\\0&1&1&-1\\0&0&0&0\end{array}\right)
$$

$\text{rk}(A)=\text{rk}(A')=2 \Rightarrow \infty^{3-2}=\infty^1$ soluzioni (una retta di soluzioni).

Dalla seconda riga: $y=-1-z$. Dalla prima: $x = -1+y-z = -1+(-1-z)-z = -2-2z$.

Ponendo $z=t$:

$$
\underline x = \begin{pmatrix}x\\y\\z\end{pmatrix} = \begin{pmatrix}-2\\-1\\0\end{pmatrix} + t\begin{pmatrix}-2\\-1\\1\end{pmatrix}, \quad t\in\mathbb{R}
$$

*(Verifica: sostituendo $x=-2-2t,\,y=-1-t,\,z=t$ nella prima equazione $x-y+z=(-2-2t)-(-1-t)+t=-1$ ✓. Nella brutta copia i segni di $x$ e $y$ erano invertiti: qui sono stati ricontrollati per sostituzione diretta.)*

### Caso $\alpha=-2$

$$
\left(\begin{array}{ccc|c}1&-1&-2&-1\\0&1&1&-1\\0&0&0&-4\end{array}\right)
$$

Ultima riga $0=-4$: contraddizione. $\text{rk}(A)=2 \ne \text{rk}(A')=3 \Rightarrow$ **nessuna soluzione**.

### Riepilogo Esercizio 4

| $\alpha$ | $\text{rk}(A)$ | $\text{rk}(A')$ | Soluzioni |
|---|---|---|---|
| $\alpha \notin \{-2,1\}$ | 3 | 3 | $\infty^0$ (unica), formule sopra |
| $\alpha = 1$ | 2 | 2 | $\infty^1$, retta sopra |
| $\alpha = -2$ | 2 | 3 | nessuna |

---

## Esercizio 5 — Dimostrazione

> Dimostrare che una matrice $A \in M_{2,m}(\mathbb{R})$ con $\text{rk}(A) \le 1$ ha necessariamente: **o la prima riga è nulla, o la seconda riga è multipla della prima.**

**Dimostrazione.** Siano $r_1, r_2 \in \mathbb{R}^m$ le due righe di $A$.

- Se $\text{rk}(A) = 0$: per definizione lo spazio delle righe è $\{\underline 0\}$, quindi $r_1 = r_2 = \underline 0$. In particolare la prima riga è nulla (primo caso soddisfatto banalmente).

- Se $\text{rk}(A) = 1$: lo spazio generato dalle righe, $\text{Span}(r_1,r_2)$, ha dimensione $1$. Distinguiamo due sottocasi:
  - Se $r_1 = \underline 0$: la tesi è verificata (primo caso).
  - Se $r_1 \ne \underline 0$: allora $r_1$ da solo genera già un sottospazio di dimensione $1$, cioè $\text{Span}(r_1) \subseteq \text{Span}(r_1,r_2)$ e $\dim\text{Span}(r_1)=1=\dim\text{Span}(r_1,r_2)$. Due sottospazi uno contenuto nell'altro con la stessa dimensione (finita) coincidono, quindi $\text{Span}(r_1,r_2)=\text{Span}(r_1)$. In particolare $r_2 \in \text{Span}(r_1)$, cioè esiste $\lambda \in \mathbb{R}$ tale che $r_2 = \lambda\, r_1$ (secondo caso).

In ogni caso ($\text{rk}(A)=0$ oppure $\text{rk}(A)=1$, cioè $\text{rk}(A)\le 1$) vale: $r_1=\underline 0$ oppure $r_2 = \lambda r_1$ per qualche $\lambda \in \mathbb{R}$. $\blacksquare$

*Osservazione:* l'ipotesi $\text{rk}(A)\le 1$ è essenziale — se $\text{rk}(A)=2$ le righe sono linearmente indipendenti, quindi né $r_1=\underline 0$ né $r_2$ può essere multipla di $r_1$.
