## Richiami teorici

Dato $\emptyset \neq S \subseteq \mathbb{R}$ e $z \in \mathbb{R}$, si ha $z = \sup(S)$ se e solo se:

1. $z$ è un **maggiorante** di $S$: $\forall x \in S,\ x \le z$;
2. $z$ è il **più piccolo** dei maggioranti: $\forall y \in \mathbb{R},\ y \neq z$, se $\forall x \in S,\ x \le y$ allora $z \le y$.

Equivalentemente, la condizione (2) si riformula in modo più operativo così:

$$\forall \varepsilon > 0 \ \exists x \in S \ \text{t.c.} \ x > z - \varepsilon$$

(analogamente per $\inf(S)$, con maggiorante → minorante e disuguaglianze invertite).

Nelle dimostrazioni seguenti si usa spesso l'**assioma di Archimede**: $\mathbb{N} \subseteq \mathbb{R}$ è illimitato superiormente, quindi per ogni $c \in \mathbb{R}$ esiste $m \in \mathbb{N}$ tale che $m > c$.

---

## Esercizio 1

$$S = \left\{ \frac{n-1}{n} : n \in \mathbb{N} \setminus \{0\} \right\} = \left\{0, \tfrac{1}{2}, \tfrac{2}{3}, \tfrac{3}{4}, \dots \right\}$$

**inf/min:** $\inf(S) = \min(S) = 0$ (raggiunto per $n=1$).

**sup:** dimostriamo che $\sup(S) = 1$.

Poiché $1 \notin S$ (non esiste $n \in \mathbb{N}\setminus\{0\}$ tale che $\frac{n-1}{n} = 1$), segue che $\nexists \max(S)$.

Verifichiamo le due condizioni della definizione di sup:

**(1)** $\dfrac{n-1}{n} < 1 \ \forall n \in \mathbb{N}\setminus\{0\}$, poiché $n-1 < n$ è sempre vera. ⇒ $1$ è maggiorante.

**(2)** Fissiamo $\varepsilon > 0$. Vogliamo trovare $m \in \mathbb{N}\setminus\{0\}$ tale che

$$\frac{m-1}{m} > 1-\varepsilon$$

$$m - 1 > m - m\varepsilon \quad\Longrightarrow\quad m\varepsilon > 1 \quad\Longrightarrow\quad m > \frac{1}{\varepsilon}$$

Un tale $m$ esiste sicuramente perché $\mathbb{N}$ è illimitato superiormente (Archimede).

$$\Longrightarrow \quad \sup(S) = 1$$

---

## Esercizio 2 (variante con segno alternato)

$$S = \left\{ (-1)^n \frac{n-1}{n} : n \in \mathbb{N}\setminus\{0\} \right\} = \left\{0, \tfrac{1}{2}, -\tfrac{2}{3}, \tfrac{3}{4}, -\tfrac{4}{5}, \dots \right\}$$

Dimostriamo che $\inf(S) = -1$ (per simmetria, $\sup(S) = 1$, con lo stesso argomento dell'Esercizio 1 ristretto agli $n$ pari; nessuno dei due valori è raggiunto ⇒ $\nexists \max(S)$, $\nexists \min(S)$).

**(1)** $(-1)^n \dfrac{n-1}{n} \ge -1 \ \forall n$: per $n$ pari il termine è $\ge 0 > -1$; per $n$ dispari il termine è $-\dfrac{n-1}{n} \ge -1 \iff \dfrac{n-1}{n} \le 1$, sempre vero. ⇒ $-1$ è minorante.

**(2)** Fissato $\varepsilon > 0$, cerchiamo (tra gli $n$ dispari) $m$ tale che

$$-\frac{m-1}{m} < -1 + \varepsilon \quad\Longleftrightarrow\quad \frac{m-1}{m} > 1-\varepsilon$$

che è la stessa disequazione dell'Esercizio 1, risolta da $m > \dfrac{1}{\varepsilon}$ (Archimede garantisce l'esistenza di un tale $m$ dispari).

$$\Longrightarrow \quad \inf(S) = -1$$

---

## Esercizio 3

$$S = \left\{ \log(1+3x) : x \in \mathbb{R}, \ |x-2| \le \sqrt{x} \right\}$$

**Dominio:** serve $x \ge 0$ (c.e. per $\sqrt{x}$). Con $x\ge0$, elevando al quadrato:

$$|x-2| \le \sqrt{x} \iff (x-2)^2 \le x \iff x^2 - 4x + 4 \le x \iff x^2 - 5x + 4 \le 0$$

> Correzione: il passaggio va a $x^2-5x+4\le 0$ (non $x^2-3x+4$), raccogliendo $-4x - x = -5x$.

Le radici di $x^2-5x+4=0$ sono $x=1,\ x=4$, quindi $(x-1)(x-4)\le 0 \iff 1 \le x \le 4$.

$$S = \{\log(1+3x) : x \in [1,4]\}$$

Per $x \in [1,4]$, $1+3x > 0$, quindi $f(x) = \log(1+3x)$ è ben definita. Inoltre:

- $y = 1+3x$ è strettamente crescente;
- $y = \log(t)$ è strettamente crescente;

⇒ la composizione $f(x) = \log(1+3x)$ è strettamente crescente su $[1,4]$.

$$\inf(S) = \min(S) = f(1) = \log(4)$$
$$\sup(S) = \max(S) = f(4) = \log(13)$$

---

## Esercizio 4

$$S = \{x \in \mathbb{R} : x>0,\ \cos(1/x) = 0\}$$

$$\cos(t) = 0 \iff t = \frac{\pi}{2} + k\pi = \frac{\pi(1+2k)}{2}, \ k \in \mathbb{Z}$$

$$\cos(1/x) = 0 \iff \frac{1}{x} = \frac{\pi(1+2k)}{2} \iff x = \frac{2}{\pi(1+2k)}, \ k\in\mathbb{Z}$$

Poiché serve $x>0$, occorre $1+2k>0$, cioè $k \ge 0$, quindi $k \in \mathbb{N}$:

$$S = \left\{ \frac{2}{\pi(1+2k)} : k \in \mathbb{N} \right\}$$

All'aumentare di $k$, il termine $a_k = \dfrac{2}{\pi(1+2k)}$ diminuisce (più precisamente, se $n>m$ allora $a_n < a_m$).

**Sup/max:** il massimo si ha per $k=0$: $\ a_0 = \dfrac{2}{\pi} = \max(S) = \sup(S)$.

**Inf:** dimostriamo che $\inf(S) = 0$ (non raggiunto ⇒ $\nexists \min(S)$).

**(1)** $0 < a_k \ \forall k \in \mathbb{N}$ ⇒ $0$ è minorante; inoltre $0 \notin S$ perché $\dfrac{2}{\pi(1+2k)} \neq 0\ \forall k$.

**(2)** Fissato $\varepsilon>0$, cerchiamo $m \in \mathbb{N}$ tale che $a_m < \varepsilon$:

$$\frac{2}{\pi(1+2m)} < \varepsilon \iff 1+2m > \frac{2}{\pi\varepsilon} \iff m > \frac{1}{\pi\varepsilon} - \frac{1}{2}$$

Un tale $m$ esiste sicuramente perché $\mathbb{N}$ è illimitato superiormente.

$$\Longrightarrow \quad \inf(S) = 0, \quad \nexists \min(S)$$

---

## Per casa (da svolgere)

**Esercizio 5.**

$$S = \{a \in \mathbb{R} : \log(x^2 - 2ax + a) \text{ è definito su tutto } \mathbb{R}\}$$

*(spazio per lo svolgimento)*

<br><br><br>

**Esercizio 6.**

$$S = \left\{ x \in \mathbb{R}\setminus\{2\} : \frac{2x+1}{x-2} - \frac{5}{2(x+2)} < \frac{1}{2} \right\}$$

*(spazio per lo svolgimento)*

<br><br><br>
