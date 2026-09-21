---
tags:
  - geometria-algebra-lineare
---
## 1. Insiemi

Un **insieme** è una collezione, finita o infinita, di oggetti (i suoi *elementi*). Dato un oggetto, l'unica domanda sensata è se esso **appartenga** o meno all'insieme: un insieme classico non tiene conto di ripetizioni né di ordine (a differenza di una *multi-insieme* $\{1,2,2,\dots\}$, in cui le ripetizioni sono ammesse, o di una sequenza/tupla, in cui l'ordine conta).

Un insieme si indica con le parentesi graffe $\{\ \}$. Ci sono due modi principali per definirlo:

- **per elencazione**: $\{1, 2, 3\}$;
- **per proprietà caratteristica** (comprensione):
$$
\{\, x : P(x) \,\} = \{\, \text{espressione} : \text{condizione} \,\}
$$
cioè l'insieme di tutti gli $x$ che soddisfano la condizione $P(x)$. Esempio:
$$
\{x : x^2 < 4\}
$$
è l'insieme di tutti i numeri reali $x$ tali che $x^2<4$, cioè l'intervallo $(-2, 2)$.

Un altro esempio, l'insieme dei numeri dispari:
$$
\{2n+1 : n \in \mathbb{N}\}
$$

### Insiemi numerici fondamentali

| Simbolo | Nome | Nota |
|---|---|---|
| $\mathbb{N}$ | numeri naturali | in questo corso **senza** lo 0 |
| $\mathbb{N}_0$ | numeri naturali | **con** lo 0 |
| $\mathbb{Z}$ | numeri interi | positivi, negativi e zero |
| $\mathbb{Q}$ | numeri razionali | rapporti di interi |
| $\mathbb{R}$ | numeri reali | |
| $\mathbb{C}$ | numeri complessi | $\mathbb{C} := \{ z = x+iy : x,y\in\mathbb{R}\}$ |

Vale la catena di inclusioni $\mathbb{N} \subset \mathbb{N}_0 \subset \mathbb{Z} \subset \mathbb{Q} \subset \mathbb{R} \subset \mathbb{C}$.

## 2. Notazioni fondamentali

### $=$ contro $:=$

- $=$ afferma un **fatto**, un'uguaglianza tra due espressioni già definite.
- $:=$ significa **"uguale per definizione"**: introduce un nuovo simbolo ponendolo uguale a un'espressione nota.

**Esempio.** Poniamo per definizione
$$
a := \sqrt{3+2\sqrt2}.
$$
Questo significa che ogni volta che compare $a$, esso rappresenta quel numero. Si può poi *dimostrare un fatto* su $a$, ad esempio semplificarlo:
$$
a^2 = 3+2\sqrt2 = 1+2\sqrt2+(\sqrt2)^2=(1+\sqrt2)^2, \qquad a>0
$$
quindi (essendo $a>0$ e $1+\sqrt2>0$) si conclude che $a=1+\sqrt2$.

### $\in$ contro $\subset$

- $x \in A$: l'elemento $x$ **appartiene** all'insieme $A$.
- $B \subset A$: l'insieme $B$ è **contenuto** in $A$ (ogni elemento di $B$ è anche elemento di $A$).

Sono concetti di natura diversa: il primo lega un elemento a un insieme, il secondo lega due insiemi.

## 3. Lo spazio $\mathbb{R}^n$

Per $n \in \mathbb{N}$, $\mathbb{R}^n$ indica l'insieme delle **n-uple ordinate** (successioni finite) di $n$ numeri reali qualsiasi $x_1, x_2, \dots, x_n$. In simboli:
$$
\mathbb{R}^n := \{(x_1,x_2,\dots,x_n) : x_1,x_2,\dots,x_n \in \mathbb{R}\}
$$
Ad esempio, lo spazio tridimensionale:
$$
\mathbb{R}^3 := \{(x,y,z) : x,y,z \in \mathbb{R}\}
$$

## 4. Vettori

### Vettori nel piano e nello spazio

Un vettore del piano $\vec a = (x,y) \in \mathbb{R}^2$ si può rappresentare geometricamente come una freccia dall'origine al punto $(x,y)$: esiste una **corrispondenza biunivoca** tra i punti di $\mathbb{R}^2$ e i vettori del piano. Analogamente $\mathbb{R}^3$ è l'insieme dei vettori dello spazio tridimensionale.

I vettori ammettono le seguenti operazioni:

- **somma/differenza** $\vec a \pm \vec b$;
- **moltiplicazione per scalare** $\lambda \vec a$, con $\lambda \in \mathbb{R}$;
- **prodotto scalare** $\vec a \cdot \vec b$.

Le prime due hanno un significato **geometrico** diretto: la somma segue la regola del parallelogramma, $2\vec a$ è il vettore con stessa direzione e verso ma lunghezza doppia, $-\vec a$ è il vettore opposto (stessa lunghezza, verso contrario).

### Formule in coordinate (in $\mathbb{R}^3$)

$$
\vec a \pm \vec b = (a_x \pm b_x,\; a_y \pm b_y,\; a_z \pm b_z)
$$
$$
\lambda \vec a = (\lambda a_x, \lambda a_y, \lambda a_z)
$$
$$
\vec a \cdot \vec b = a_x b_x + a_y b_y + a_z b_z
$$

### Generalizzazione a $\mathbb{R}^n$

Per $x := (x_1,\dots,x_n) \in \mathbb{R}^n$, $y := (y_1,\dots,y_n) \in \mathbb{R}^n$ e $\lambda \in \mathbb{R}$, si definiscono:

$$
x \pm y := (x_1 \pm y_1,\; x_2 \pm y_2,\; \dots,\; x_n \pm y_n)
$$
$$
\lambda x := (\lambda x_1, \dots, \lambda x_n)
$$
$$
x \cdot y := \sum_{k=1}^{n} x_k y_k = x_1y_1 + x_2y_2 + \dots + x_ny_n \qquad \text{(prodotto scalare standard)}
$$

Con queste operazioni, $\mathbb{R}^n$ è uno **spazio vettoriale**.

### Convenzioni di notazione

È importante distinguere scalari e vettori:

- $x$ → un **numero** (scalare);
- $\vec x$ oppure $\mathbf{x}$ → un **vettore**.

### Lo spazio $\mathbb{C}^n$

La stessa costruzione si può ripetere con i numeri complessi al posto dei reali:
$$
\mathbb{C}^n := \{(z_1,z_2,\dots,z_n) : z_1,\dots,z_n \in \mathbb{C}\}
$$
con
$$
z \pm w := (z_1\pm w_1, \dots, z_n \pm w_n) \in \mathbb{C}^n, \qquad \lambda z := (\lambda z_1, \dots, \lambda z_n) \in \mathbb{C}^n.
$$
**Nota:** in $\mathbb{C}^n$ non si definisce (per ora) un prodotto scalare analogo a quello reale.

Per indicare genericamente uno dei due campi si scrive
$$
\mathbb{K} := \mathbb{R} \quad \text{oppure} \quad \mathbb{K} := \mathbb{C}
$$
in modo da poter enunciare risultati validi in entrambi i casi.

## 5. Quantificatori logici

Nel linguaggio matematico si usano due simboli fondamentali:

- **Quantificatore universale** $\forall$ ("per ogni");
- **Quantificatore esistenziale** $\exists$ ("esiste almeno un").

Combinando i due si ottiene il simbolo di **esistenza e unicità**:
$$
\exists! \quad \text{"esiste un unico"}
$$
che afferma non solo che un oggetto con una certa proprietà esiste, ma che è anche l'unico a possederla.

## 6. Sistemi di equazioni lineari

### Definizione

Un sistema di $m$ equazioni lineari nelle $n$ incognite $x_1, x_2, \dots, x_n$ ha la forma generale:
$$
\sum_{j=1}^{n} a_{ij}\, x_j = b_i, \qquad i = 1, \dots, m
$$
dove:

- gli $a_{ij}$ sono i **coefficienti** (costanti, non dipendono dalle $x_j$);
- i $b_i$ sono i **termini noti** (anch'essi costanti);
- ogni incognita compare con **potenza massima 1** (da qui "lineare": nessun $x_j^2$, nessun prodotto $x_ix_j$, nessuna funzione non lineare delle incognite).

### Soluzione del sistema

Una **soluzione** del sistema è un valore delle incognite
$$
x := (x_1, x_2, \dots, x_n)
$$
per cui **tutte** le $m$ equazioni diventano uguaglianze vere simultaneamente.

**Risolvere** un sistema significa determinare l'insieme $S$ di tutte le sue soluzioni. Ci sono esattamente tre casi possibili:

1. $S = \varnothing$ — il sistema è **impossibile** (nessuna soluzione);
2. $S = \{x\}$ — il sistema è **determinato** (soluzione unica);
3. $S = \{\dots\}$ (infiniti elementi) — il sistema è **indeterminato** (infinite soluzioni).

Per trasformare un sistema in uno equivalente (stesso insieme di soluzioni) più semplice da risolvere si usano le **operazioni elementari** sulle equazioni:

(i) scambiare due equazioni tra loro;
(ii) moltiplicare un'equazione per uno scalare non nullo;
(iii) sommare a un'equazione un multiplo di un'altra.

## 7. Metodo di eliminazione di Gauss

L'idea è **associare a un sistema lineare una matrice**, e trasformare il sistema in uno equivalente più semplice lavorando direttamente sulle righe della matrice invece che riscrivendo ogni volta le equazioni.

### 7.1 Matrici: definizioni di base

Una **matrice** $m \times n$ è una tabella rettangolare di numeri (rea\li o complessi) con $m$ **righe** e $n$ **colonne**:
$$
A = [a_{ij}] = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn} \end{bmatrix}
$$
dove $i = 1,\dots,m$ indica la **riga** e $j = 1,\dots,n$ la **colonna**: $a_{ij}$ è l'elemento di posto $(i,j)$.

> **Nota sull'errore comune:** in una matrice $m\times n$ le **righe sono $m$** e le **colonne sono $n$** (non il contrario) — è facile confondersi perché l'indice di riga $i$ compare per primo nel simbolo $a_{ij}$, ma per primo tra le *dimensioni* c'è sempre il numero di righe.

### 7.2 Matrice associata a un sistema (matrice completa)

Dato il sistema lineare generale della sezione precedente,
$$
\sum_{j=1}^n a_{ij}x_j = b_i, \qquad i=1,\dots,m,
$$
gli si associa la **matrice completa** (o *aumentata*) $[A\mid B]$, che affianca alla matrice dei coefficienti $A = [a_{ij}]$ la colonna dei termini noti $B = (b_1,\dots,b_m)$:
$$
[A \mid B] := \left[\begin{array}{cccc|c} a_{11} & a_{12} & \cdots & a_{1n} & b_1 \\ \vdots & & & \vdots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn} & b_m \end{array}\right]
$$
Risolvere il sistema equivale, per costruzione, a lavorare su questa matrice.

**Esempio (2 equazioni, 2 incognite).** Il sistema
$$
\begin{cases} x_1 - x_2 = 2 \\ x_1 = 3 \end{cases}
$$
ha matrice completa
$$
[A\mid B] = \begin{bmatrix} 1 & -1 & 2 \\ 1 & 0 & 3 \end{bmatrix}
$$
(prima colonna: coefficienti di $x_1$; seconda: coefficienti di $x_2$; terza, dopo la barra: termini noti).

### 7.3 Operazioni elementari sulle righe

Per trasformare $[A\mid B]$ in una matrice più semplice **senza cambiare l'insieme delle soluzioni** si usano esattamente le stesse tre operazioni (i)–(iii) viste per le equazioni nella sezione 6, ora applicate alle **righe** della matrice:

(i) scambiare due righe: $R_i \leftrightarrow R_j$;
(ii) moltiplicare una riga per uno scalare non nullo: $R_i \to \lambda R_i,\ \lambda \neq 0$;
(iii) sommare a una riga un multiplo di un'altra: $R_i \to R_i + \lambda R_j$.

Ognuna di queste equivale a manipolare le equazioni corrispondenti, quindi non altera l'insieme delle soluzioni del sistema.

### 7.4 Matrice a scala (per righe) e pivot

**Definizione.** Sia $A$ una matrice $m\times n$. Per ogni riga $i$, sia $\ell_i$ il numero di zeri consecutivi con cui inizia la riga (quindi $\ell_i = n$ se la riga è tutta nulla). $A$ si dice **matrice a scala per righe** se:

- le eventuali righe interamente nulle sono tutte nelle ultime posizioni;
- per le righe non nulle vale $\ell_1 < \ell_2 < \cdots < \ell_r$ (i "gradini" degli zeri iniziali crescono strettamente scendendo).

Il primo elemento non nullo di ciascuna riga non nulla si chiama **pivot**.

**Teorema (esistenza dell'algoritmo di Gauss).** Ogni matrice $A$ può essere trasformata in una matrice a scala $U$ mediante un numero finito di operazioni elementari (i)–(iii) sulle righe. (La matrice $U$ non è unica, ma il numero di pivot che si ottiene sì — vedi rango, sotto.)

### 7.5 Rango di una matrice

**Definizione.** Se $U$ è una matrice a scala, il suo **rango** $r(U)$ è il numero di pivot di $U$, ossia il numero di righe non nulle di $U$.

Per una matrice qualsiasi $A$, si definisce
$$
r(A) := r(U)
$$
dove $U$ è una qualunque matrice a scala ottenuta da $A$ tramite operazioni elementari. Il rango è **ben definito**, cioè non dipende dalla particolare sequenza di operazioni scelta per arrivare a $U$.

### 7.6 Esempio svolto

Consideriamo il sistema di 4 equazioni nelle incognite $x_1,x_2,x_3,x_4$:
$$
\begin{cases}
x_1 - x_2 + 2x_3 + 3x_4 = 2 \\
x_1 - x_2 + 2x_3 + 7x_4 = 6 \\
x_1 + 2x_2 + 2x_3 + x_4 = 6 \\
x_1 + 2x_2 + 2x_3 + 5x_4 = 10
\end{cases}
\quad\Longrightarrow\quad
[A\mid B] = \begin{bmatrix} 1 & -1 & 2 & 3 & 2 \\ 1 & -1 & 2 & 7 & 6 \\ 1 & 2 & 2 & 1 & 6 \\ 1 & 2 & 2 & 5 & 10 \end{bmatrix}
$$

Eliminiamo $x_1$ dalle righe 2, 3, 4 usando $R_1$ come pivot:
$$
R_2 \to R_2 - R_1,\quad R_3 \to R_3 - R_1,\quad R_4 \to R_4 - R_1
\;\Longrightarrow\;
\begin{bmatrix} 1 & -1 & 2 & 3 & 2 \\ 0 & 0 & 0 & 4 & 4 \\ 0 & 3 & 0 & -2 & 4 \\ 0 & 3 & 0 & 2 & 8 \end{bmatrix}
$$
La riga 2 ha uno zero proprio nella colonna che vorremmo usare come pivot successivo: si **scambiano** $R_2$ e $R_3$ (operazione (i)) per portare in seconda posizione una riga con pivot in colonna 2:
$$
R_2 \leftrightarrow R_3
\;\Longrightarrow\;
\begin{bmatrix} 1 & -1 & 2 & 3 & 2 \\ 0 & 3 & 0 & -2 & 4 \\ 0 & 0 & 0 & 4 & 4 \\ 0 & 3 & 0 & 2 & 8 \end{bmatrix}
$$
Eliminiamo il termine in colonna 2 dalla riga 4, poi la riga risultante coincide con $R_3$ e si annulla:
$$
R_4 \to R_4 - R_2 \;\Longrightarrow\; R_4 = (0,0,0,4\mid 4);\qquad R_4 \to R_4 - R_3 \;\Longrightarrow\; R_4 = (0,0,0,0\mid 0)
$$
Matrice a scala finale:
$$
[U\mid B'] = \begin{bmatrix} 1 & -1 & 2 & 3 & 2 \\ 0 & 3 & 0 & -2 & 4 \\ 0 & 0 & 0 & 4 & 4 \\ 0 & 0 & 0 & 0 & 0 \end{bmatrix}, \qquad r(A) = 3
$$
I pivot sono nelle colonne di $x_1, x_2, x_4$; la colonna di $x_3$ **non ha pivot**: $x_3$ è una **variabile libera**.

Il sistema a scala corrispondente è
$$
\begin{cases}
x_1 - x_2 + 2x_3 + 3x_4 = 2 \\
3x_2 - 2x_4 = 4 \\
4x_4 = 4 \\
0 = 0
\end{cases}
$$
e si risolve per **sostituzione a ritroso**, dall'ultima equazione utile verso la prima:
$$
x_4 = 1, \qquad x_2 = \frac{4+2x_4}{3} = 2, \qquad x_1 = 2 + x_2 - 2x_3 - 3x_4 = 1 - 2x_3
$$
Posto $x_3 = t$, con $t \in \mathbb{K}$ **qualsiasi**, si ottiene una soluzione del sistema per ogni valore di $t$:
$$
x = (x_1,x_2,x_3,x_4) = (1-2t,\; 2,\; t,\; 1) \in \mathbb{K}^4
$$
Insieme delle soluzioni:
$$
S = \{\, (1-2t,\, 2,\, t,\, 1) : t \in \mathbb{K} \,\}
$$
(sistema **indeterminato**, con $\infty^1$ soluzioni: un solo parametro libero).

### 7.7 Conclusioni: sistema impossibile, determinato o indeterminato

Per risolvere un sistema lineare basta ridurre a scala la sua matrice completa:
$$
[A\mid B] \xrightarrow{\text{operazioni elementari}} [U\mid B']
$$
e leggere la situazione direttamente sui pivot di $[U\mid B']$:

- **Sistema impossibile** ($S=\varnothing$) $\iff$ nell'ultima colonna (quella dei termini noti) c'è un pivot, cioè esiste una riga del tipo
$$
(0,0,\dots,0 \mid c), \qquad c \neq 0
$$
(un'equazione "$0 = c$" con $c\neq 0$, evidentemente falsa).
- Se il sistema **non** è impossibile (nessun pivot nell'ultima colonna), allora è **possibile**, e si distinguono due casi guardando le colonne di $A$ (cioè escludendo l'ultima):
  - **determinato** ($S=\{x\}$, soluzione unica) $\iff$ **ogni** colonna di $A$ contiene un pivot, cioè $r(A) = n$ (numero di incognite): nessuna variabile libera;
  - **indeterminato** (infinite soluzioni) $\iff$ **esiste almeno una** colonna di $A$ senza pivot: le incognite corrispondenti a quelle colonne sono variabili libere, e parametrizzano l'insieme $S$ (come $x_3=t$ nell'esempio sopra).

