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

*(continua nella prossima lezione con il metodo di eliminazione di Gauss)*
