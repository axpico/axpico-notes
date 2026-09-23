---
tags:
  - analisi1
  - estremo-superiore
  - estremo-inferiore
  - completezza-R
  - radici
  - logaritmi
  - valore-assoluto
  - politecnico
---
## 1. Massimo e minimo di un insieme

**Definizione.** Sia $E \subseteq \mathbb{R}$.

- $M$ si dice **massimo** di $E$ (si scrive $M = \max E$) se
$$
\begin{cases} M \in E \\ M \geq x \quad \forall x \in E \end{cases}
$$
cioè $M$ appartiene all'insieme ed è maggiore o uguale di ogni altro elemento.

- $m$ si dice **minimo** di $E$ (si scrive $m = \min E$) se
$$
\begin{cases} m \in E \\ m \leq x \quad \forall x \in E \end{cases}
$$

Il punto cruciale è che massimo e minimo, se esistono, devono **appartenere all'insieme**. Non tutti gli insiemi li possiedono.

**Esempio.** $E = (0,2]$ (intervallo semiaperto). Il massimo esiste ed è $\max E = 2$ (appartiene a $E$). Il minimo **non esiste**: per ogni candidato $m>0$ in $E$ si trova sempre un elemento più piccolo ancora dentro $E$ (es. $m/2$), quindi nessun elemento di $E$ è minore o uguale a tutti gli altri.

## 2. Maggioranti e minoranti

**Definizione.** Sia $E \subseteq \mathbb{R}$.

(i) $\Lambda \in \mathbb{R}$ si dice **maggiorante** di $E$ se $\Lambda \geq x \ \ \forall x \in E$.

(ii) $\lambda \in \mathbb{R}$ si dice **minorante** di $E$ se $\lambda \leq x \ \ \forall x \in E$.

A differenza del massimo, un maggiorante **non deve appartenere** a $E$: è semplicemente un limite superiore, anche esterno all'insieme. Un insieme può avere infiniti maggioranti (tutto l'intervallo $[2,+\infty)$ per $E=(0,2]$).

**Osservazione.** Se $M$ è il massimo di $E$, allora $M$ è anche un maggiorante, ed è il **più piccolo** tra tutti i maggioranti (il "migliore" possibile). Analogamente per il minimo con i minoranti.

## 3. Estremo superiore e inferiore

**Definizione.** Sia $E \subseteq \mathbb{R}$, $E \neq \emptyset$.

- L'**estremo superiore** di $E$, $\sup E$, è il **minimo dei maggioranti** di $E$.
- L'**estremo inferiore** di $E$, $\inf E$, è il **massimo dei minoranti** di $E$.

L'idea è: quando il massimo/minimo non esiste "dentro" l'insieme, l'estremo superiore/inferiore lo sostituisce come il miglior limite possibile, definito tramite i maggioranti/minoranti (che vivono fuori da $E$ in generale).

**Esempio.** $E = (0,2]$:
- maggioranti: $[2, +\infty)$
- minoranti: $(-\infty, 0]$
- $\sup E = 2$
- $\inf E = 0$

**Osservazione fondamentale.** Se un insieme ammette massimo, allora ammette anche estremo superiore e i due coincidono: $\sup E = \max E$. Lo stesso vale per minimo ed estremo inferiore. In altre parole, l'estremo superiore/inferiore è una **generalizzazione** di massimo/minimo che esiste anche quando questi ultimi non esistono.

### Caratterizzazione (definizione operativa) di sup ed inf

$s = \sup E$ se e solo se valgono **entrambe** le condizioni:

1. $s$ è un maggiorante: $s \geq x \ \ \forall x \in E$;
2. $s$ è il più piccolo maggiorante possibile: $\forall \varepsilon > 0 \ \ \exists x_\varepsilon \in E$ tale che $x_\varepsilon > s - \varepsilon$.

La seconda condizione dice che, per quanto piccolo si scelga $\varepsilon$, si trova sempre un punto di $E$ che supera $s-\varepsilon$: cioè nessun numero più piccolo di $s$ può essere maggiorante, perché "sfugge" un elemento dell'insieme sopra di esso.

Analogamente, $i = \inf E$ se e solo se:

1. $i \leq x \ \ \forall x \in E$;
2. $\forall \varepsilon > 0 \ \ \exists x_\varepsilon \in E$ tale che $x_\varepsilon < i + \varepsilon$.

Questa è la definizione **rigorosa tramite $\varepsilon$**, molto usata nelle dimostrazioni: permette di dimostrare che un certo numero è sup/inf senza dover "indovinare" o enumerare tutti i maggioranti.

## 4. Insiemi limitati e proprietà di completezza

**Definizione.** $E \subseteq \mathbb{R}$ si dice **limitato superiormente** se ammette almeno un maggiorante. Si dice **limitato inferiormente** se ammette almeno un minorante. Si dice **limitato** se è limitato sia superiormente che inferiormente (equivalentemente, se inf e sup sono entrambi finiti).

**Esempio.** $E = [1, +\infty)$ è limitato inferiormente (es. $-6$ è un minorante) ma **non** è limitato superiormente.

Quando un insieme non è limitato superiormente si scrive per convenzione $\sup E = +\infty$; se non è limitato inferiormente, $\inf E = -\infty$. Formalmente:

- $E$ non è limitato superiormente $\iff \forall \Lambda \in \mathbb{R} \ \exists x \in E : x > \Lambda$
- $E$ non è limitato inferiormente $\iff \forall \lambda \in \mathbb{R} \ \exists x \in E : x < \lambda$

### Teorema di completezza di ℝ

**Teorema (completezza).** Qualunque sottoinsieme $E \subseteq \mathbb{R}$ non vuoto ammette **sempre** estremo superiore ed estremo inferiore in $\mathbb{R}$ (eventualmente $\pm\infty$ se non limitato).

Questa è una proprietà **strutturale** dei numeri reali, non ovvia: distingue $\mathbb{R}$ da $\mathbb{Q}$, che **non** è completo.

**Controesempio in ℚ.** Sia
$$
A = \{x \in \mathbb{Q} : x^2 \leq 2\} \subseteq \mathbb{Q}.
$$
- In $\mathbb{R}$, $A$ ammette estremo superiore: $\sup A = \sqrt{2}$, che è un maggiorante.
- In $\mathbb{Q}$, invece, $A$ **non ammette** estremo superiore, perché $\sqrt{2} \notin \mathbb{Q}$, e non esiste alcun razionale che faccia da minimo maggiorante.

Questo mostra concretamente che la proprietà di completezza **non vale in $\mathbb{Q}$**: ci sono "buchi" (i numeri irrazionali) che rendono $\mathbb{Q}$ incompleto rispetto all'ordine. La completezza di $\mathbb{R}$ è ciò che garantisce, ad esempio, l'esistenza di $\sqrt{2}$, $\pi$, $e$, ecc.

## 5. Radici n-esime, potenze razionali, esponenziali e logaritmi

**Teorema (esistenza e unicità della radice n-esima).** Siano $y \geq 0$, $n \in \mathbb{N}$, $n \geq 1$. Allora esiste un unico numero reale $x \geq 0$ tale che
$$
y = x^n.
$$
Si scrive $x = \sqrt[n]{y}$ ("radice n-esima di $y$").

Questo teorema è di nuovo una conseguenza della completezza di $\mathbb{R}$: si dimostra costruendo $x$ come estremo superiore di un opportuno insieme di numeri reali $\{t \geq 0 : t^n \leq y\}$.

**Potenze con esponente razionale.** Se $r = \frac{m}{n} \in \mathbb{Q}$, con $m \in \mathbb{Z}$, $n \in \mathbb{N}$, $n \neq 0$, e $a > 0$, si definisce
$$
a^r = a^{m/n} = \sqrt[n]{a^m}.
$$

**Osservazione (segno).** Se $n = 2k+1$ è dispari, la radice n-esima si può estendere anche ad $a$ negativo (perché $x \mapsto x^n$ è biettiva su tutto $\mathbb{R}$ quando $n$ è dispari); se $n$ è pari questo non è possibile su $\mathbb{R}$ (serve $a \geq 0$).

**Teorema (esistenza del logaritmo).** Siano $a > 0$, $a \neq 1$, $y > 0$. Allora esiste un **unico** $x \in \mathbb{R}$ tale che
$$
a^x = y.
$$
Tale $x$ si chiama **logaritmo in base $a$ di $y$**, e si scrive $x = \log_a y$.

La scelta usuale è $a = e$ (numero di Nepero), nel qual caso si scrive semplicemente $\log y$ (logaritmo naturale, spesso indicato $\ln y$).

## 6. Valore assoluto (modulo)

**Definizione.** Per $x \in \mathbb{R}$, il **valore assoluto** (o modulo) di $x$ è
$$
|x| := \begin{cases} x & \text{se } x \geq 0 \\ -x & \text{se } x < 0 \end{cases}
$$
Il segno è sempre scelto in modo che il risultato sia non negativo.

**Proprietà immediate:**
- $|x| \geq 0 \ \ \forall x \in \mathbb{R}$
- $|x| = 0 \iff x = 0$
- $|x| = \max\{x, -x\}$
- $|x| = |-x|$
- $x \leq |x|$ e $-x \leq |x|$

### Teorema (disuguaglianza triangolare)

$$
\forall a, b \in \mathbb{R}: \quad |a+b| \leq |a| + |b|.
$$

**Dimostrazione.** Per ogni $a,b \in \mathbb{R}$ valgono
$$
a \leq |a|, \qquad b \leq |b|,
$$
sommando membro a membro:
$$
a + b \leq |a| + |b|. \tag{1}
$$
Analogamente
$$
-a \leq |a|, \qquad -b \leq |b|,
$$
sommando:
$$
-a - b \leq |a| + |b|, \quad \text{cioè} \quad -(a+b) \leq |a| + |b|. \tag{2}
$$
Ma $|a+b| = \max\{a+b,\ -(a+b)\}$, e sia $(1)$ che $(2)$ dicono che entrambi i candidati del massimo sono $\leq |a|+|b|$; quindi anche il maggiore dei due lo è:
$$
|a+b| = \max\{a+b, -(a+b)\} \leq |a| + |b|. \qquad \blacksquare
$$

**Osservazione.** Vale anche la disuguaglianza (spesso detta triangolare "inversa"):
$$
\big| |a| - |b| \big| \leq |a+b| \quad \forall a, b \in \mathbb{R},
$$
(dimostrazione lasciata come esercizio, tipicamente applicando la disuguaglianza triangolare a $a = (a+b) + (-b)$ e simmetrico).

## 7. Esercizio: sup, inf, max, min di un insieme definito da una disequazione irrazionale

**Testo.** Sia $A = \{x \in \mathbb{R} : x > \sqrt{6-x}\}$. Determinare $\sup A$, $\inf A$ e, se esistono, $\max A$, $\min A$.

**Risoluzione.** Una disequazione con una radice al secondo membro, $x > \sqrt{6-x}$, richiede attenzione al segno di $x$ prima di elevare al quadrato: elevare al quadrato è un'operazione **reversibile solo tra quantità dello stesso segno** (non negative). Si distinguono quindi due casi, a seconda che $x$ possa o meno essere confrontato direttamente con una radice (sempre $\geq 0$):

$$
x > \sqrt{6-x} \iff
\begin{cases} 6-x \geq 0 & \text{(dominio della radice)} \\[4pt]
\begin{cases} x < 0 \\ \text{impossibile} \end{cases} \quad \vee \quad
\begin{cases} x \geq 0 \\ x^2 > 6-x \end{cases}
\end{cases}
$$

Il ramo $x<0$ è impossibile perché per $x<0$ si avrebbe $x < 0 \leq \sqrt{6-x}$, quindi la disequazione $x>\sqrt{6-x}$ non può mai valere. Resta solo il ramo $x\geq0$, dove elevare al quadrato è lecito:
$$
\begin{cases} x \geq 0 \\ x \leq 6 \\ x^2 + x - 6 > 0 \end{cases}
$$
L'ultima disequazione si fattorizza come $(x-2)(x+3)>0$, verificata per $x<-3$ oppure $x>2$. Intersecando con $x\geq0$ e $x\leq6$:
$$
\begin{cases} x \geq 0 \\ x \leq 6 \\ x<-3 \ \vee\ x>2 \end{cases} \iff 2 < x \leq 6.
$$

Quindi
$$
A = (2, 6].
$$

**Sup, inf, max, min.**
- $6 \in A$ ed è maggiorante di $A$ $\Rightarrow$ $\max A = \sup A = 6$.
- $\inf A = 2$: è un minorante ($2 \leq x\ \forall x\in A$) ed è il più grande possibile (per ogni $\varepsilon>0$ esiste $x_\varepsilon = 2+\varepsilon/2 \in A$ con $x_\varepsilon < 2+\varepsilon$, coerentemente con la caratterizzazione di $\inf$ vista sopra).
- $\min A$ **non esiste**: $2 \notin A$ (l'intervallo è aperto in $2$), quindi nessun elemento di $A$ può essere il più piccolo (per ogni candidato in $A$ se ne trova sempre uno più vicino a $2$, ma ancora dentro $A$).

