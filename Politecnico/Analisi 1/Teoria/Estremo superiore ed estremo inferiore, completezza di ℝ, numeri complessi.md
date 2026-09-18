---
tags: [analisi1, estremo-superiore, estremo-inferiore, completezza-R, radici, logaritmi, valore-assoluto, numeri-complessi, politecnico]
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

## 7. Numeri complessi

L'equazione $x^2 + 1 = 0$ **non ha soluzioni in $\mathbb{R}$** (perché $x^2 \geq 0$ sempre). Si introduce quindi l'**unità immaginaria**:

**Definizione.** $i$ è un numero tale che $i^2 = -1$.

Con questo simbolo, $x^2 + 1 = 0 \Rightarrow x^2 = -1$, con soluzioni $x_1 = i$, $x_2 = -i$. Verifica:
$$
(x_1)^2 = (i)^2 = -1, \qquad (x_2)^2 = (-i)^2 = (-1)^2(i)^2 = -1.
$$

**Definizione (numero complesso).** Un numero complesso è un'espressione della forma
$$
z = a + ib, \qquad a, b \in \mathbb{R}
$$
detta **forma algebrica**. Si chiama:
- $a = \mathrm{Re}(z)$ **parte reale**
- $b = \mathrm{Im}(z)$ **parte immaginaria**

L'insieme dei numeri complessi si indica con $\mathbb{C}$.

### Somma

Per $z = a+ib$, $w = c+id \in \mathbb{C}$ (con $a,b,c,d \in \mathbb{R}$):
$$
z + w = (a+c) + i(b+d).
$$
Si sommano cioè separatamente le parti reali e le parti immaginarie: $\mathrm{Re}(z+w) = a+c$, $\mathrm{Im}(z+w) = b+d$.

### Prodotto

$$
z \cdot w = (a+bi)(c+di) = ac + adi + cbi + bdi^2 = ac + i(bc+ad) - bd = (ac - bd) + i(bc+ad),
$$
usando $i^2 = -1$. Quindi
$$
\mathrm{Re}(zw) = ac - bd, \qquad \mathrm{Im}(zw) = bc + ad.
$$

### Opposto

L'opposto rispetto alla somma di $z = a+ib$ è $-z = -a - bi$ (cambia segno a entrambe le parti).

### Inverso (rispetto al prodotto) e coniugato

Dato $z = a+ib \neq 0$, si cerca $w$ tale che $zw = 1$: $w = z^{-1}$.

Si introduce il **coniugato**: per $z = a+ib \in \mathbb{C}$,
$$
\bar{z} = a - ib \in \mathbb{C}
$$
(si cambia il segno solo alla parte immaginaria).

Il coniugato serve a "razionalizzare" il denominatore: moltiplicando numeratore e denominatore per $\bar z$,
$$
z^{-1} = \frac{1}{a+ib} = \frac{a - ib}{(a+ib)(a-ib)} = \frac{a-ib}{a^2+b^2},
$$
perché $(a+ib)(a-ib) = a^2 - (ib)^2 = a^2 + b^2 \in \mathbb{R}$ (il prodotto di $z$ per il suo coniugato è sempre reale e non negativo). Esplicitamente:
$$
z^{-1} = \frac{a}{a^2+b^2} + i\, \frac{-b}{a^2+b^2}, \qquad \underbrace{\frac{a}{a^2+b^2}}_{\mathrm{Re}} , \ \underbrace{\frac{-b}{a^2+b^2}}_{\mathrm{Im}}.
$$

Questa costruzione (moltiplicare per il coniugato per eliminare la parte immaginaria dal denominatore) è la tecnica standard per dividere numeri complessi ed è l'analogo della "razionalizzazione" con le radici quadrate nei numeri reali.
