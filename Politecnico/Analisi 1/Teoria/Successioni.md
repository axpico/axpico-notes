---
tags:
  - analisi1
  - successioni
  - limitatezza
  - fattoriale
  - politecnico
---
## Definizione di successione

**Definizione.** Una **successione** è una funzione che ha come dominio $\mathbb{N}$:
$$
a: \mathbb{N} \to \mathbb{R}.
$$

**Notazione.** Anziché scrivere $a(n)$ come per una funzione qualunque, il valore si indica con $a_n$, dove $n$ si dice **indice** (pedice):
$$
a_n = a(n).
$$

**Esempio.** $a_n = n^2$, $n \in \mathbb{N}$.
$$
a_0 = 0, \qquad a_1 = 1, \qquad a_2 = 4, \qquad a_3 = 9, \ \dots
$$

```desmos-graph
left=-1; right=5;
top=10; bottom=-1;
grid=true
---
(0,0)
(1,1)
(2,4)
(3,9)
(4,16)
```

**Terminologia.**
- Gli $a_n$ sono gli **elementi** (o **termini**) della successione.
- La successione si indica come insieme ordinato dei suoi elementi: $\{a_n\}_{n\in\mathbb{N}}$.
- $I_{a_n} := \{\text{valori della successione}\}$ è l'**immagine** della successione, cioè l'insieme (senza ripetizioni, non ordinato) dei valori effettivamente assunti.

**Esempio.** $a_n = (-1)^n$, $n \in \mathbb{N}$.
$$
\{a_n\}_{n\in\mathbb{N}} = \{a_0, a_1, a_2, \dots\} = \{1,-1,1,-1,\dots\}
$$
(successione: sequenza ordinata, con ripetizioni)
$$
I_{a_n} = \{-1,1\}
$$
(immagine: insieme dei valori distinti, senza ordine né ripetizioni).

## Il fattoriale

**Definizione.** La successione **fattoriale** è definita da $a_n = n!$, con
$$
n! := n(n-1)(n-2)\cdots 1, \qquad 0! := 1.
$$
(per convenzione, il fattoriale di $0$ è $1$; è il caso base della definizione ricorsiva $n! = n\cdot(n-1)!$).

**Esempio.**
$$
a_0 = 0! = 1, \qquad a_1 = 1! = 1, \qquad a_2 = 2! = 2, \qquad a_3 = 3! = 6, \qquad a_4 = 4! = 24.
$$

Il fattoriale cresce molto rapidamente (crescita **superesponenziale**): a differenza di $n^k$ o $c^n$, il fattore che moltiplica ad ogni passo ($n$) cresce esso stesso con $n$.

## Limitatezza di una successione

Essendo una successione una particolare funzione $a: \mathbb{N} \to \mathbb{R}$, le nozioni di limitatezza introdotte per le funzioni si applicano identicamente, con $A = \mathbb{N}$.

**Definizione.** $a_n$ è **limitata superiormente** (risp. **inferiormente**) se $I_{a_n} \subseteq \mathbb{R}$ è limitato superiormente (risp. inferiormente), cioè:
$$
\exists\, M \in \mathbb{R} \ \text{t.c.}\ a_n \leq M \quad \forall n \in \mathbb{N} \qquad \text{(limitata superiormente)}
$$
$$
\exists\, m \in \mathbb{R} \ \text{t.c.}\ a_n \geq m \quad \forall n \in \mathbb{N} \qquad \text{(limitata inferiormente)}
$$
$a_n$ è **limitata** se lo è sia superiormente sia inferiormente.

## Esercizio: studio della limitatezza di $a_n = n^3$

Sia $a_n = n^3$, $n \in \mathbb{N}$:
$$
a_0 = 0, \qquad a_1 = 1, \qquad a_2 = 8, \ \dots
$$

- $a_n$ è **limitata inferiormente**: basta prendere $m=0$, poiché $n^3 \geq 0$ per ogni $n \in \mathbb{N}$.
- $a_n$ è **illimitata superiormente**: si vuole verificare che
$$
\forall M \in \mathbb{R}\ \ \exists\, n_0 \in \mathbb{N} \ \text{t.c.}\ a_{n_0} > M.
$$

**Verifica.** Sia $M \in \mathbb{R}$ arbitrario fissato. Si cerca $n$ tale che
$$
n^3 > M \iff n > \sqrt[3]{M}.
$$
Si sceglie
$$
n_0 = \left[\sqrt[3]{M}\right] + 1
$$
(**parte intera** di $\sqrt[3]{M}$, più $1$): essendo $n_0$ un intero e $n_0 > \sqrt[3]{M}$ per costruzione, tale $n_0$ esiste sempre (per ogni $M$ reale, esistono infiniti interi maggiori di $\sqrt[3]{M}$). Infatti:
$$
a_{n_0} = (n_0)^3 = \left(\left[\sqrt[3]{M}\right]+1\right)^3 > M.
$$
Questo dimostra che, per quanto grande si scelga $M$, si trova sempre un termine della successione che lo supera: $a_n$ non è limitata superiormente.


## Monotonia di una successione

**Definizione.** Una successione $\{a_n\}$ è:
- **strettamente crescente** se $a_n < a_{n+1}\ \ \forall n\in\mathbb{N}$;
- **strettamente decrescente** se $a_n > a_{n+1}\ \ \forall n\in\mathbb{N}$;
- **crescente** se $a_n \le a_{n+1}\ \ \forall n\in\mathbb{N}$;
- **decrescente** se $a_n \ge a_{n+1}\ \ \forall n\in\mathbb{N}$.

$a_n$ è **monotona** se vale una delle 4 definizioni; se vale una delle due *strette*, è **strettamente monotona**.

> [!note] Perché basta confrontare termini consecutivi
> Per le successioni (dominio $\mathbb{N}$, discreto) la monotonia si verifica sul passo $n\to n+1$: per induzione/transitività da $a_n<a_{n+1}$ per ogni $n$ segue $a_n<a_m$ per ogni $m>n$. Per una funzione su un intervallo servirebbe invece il confronto tra ogni coppia di punti.

**Esempi.**
1. $a_n = n^3$ è strettamente crescente. Si verifica $n^3 < (n+1)^3$:
$$
(n+1)^3 - n^3 = 3n^2+3n+1 > 0 \quad \forall n\in\mathbb{N}. \ \checkmark
$$
2. $b_n = \dfrac1n$ ($n\ge1$) è strettamente decrescente:
$$
\frac1n > \frac1{n+1} \iff n+1 > n \quad \text{vero } \forall n\in\mathbb{N},\ n\ge1.
$$
3. $c_n = (-1)^n$ non è né crescente né decrescente ($1,-1,1,-1,\dots$ sale e scende) $\Rightarrow$ **non monotona**.

## Estremi di una successione

Le nozioni di $\max,\min,\sup,\inf$ (vedi [[Estremo superiore ed estremo inferiore, completezza di ℝ]]) si applicano all'**immagine** $I_{a_n}=\{a_n : n\in\mathbb{N}\}$:
$$
\max\{a_n\} := \max I_{a_n}, \quad \min\{a_n\} := \min I_{a_n}, \quad \sup\{a_n\} := \sup I_{a_n}, \quad \inf\{a_n\} := \inf I_{a_n}.
$$

**Definizioni operative** (equivalenti):

| Estremo | Condizioni |
|---|---|
| $\max\{a_n\}=M$ | (i) $a_n\le M\ \ \forall n$; (ii) $\exists\, n_0\in\mathbb{N}$ t.c. $a_{n_0}=M$ |
| $\min\{a_n\}=m$ | (i) $a_n\ge m\ \ \forall n$; (ii) $\exists\, n_0\in\mathbb{N}$ t.c. $a_{n_0}=m$ |
| $\sup\{a_n\}=\Lambda$ | (i) $a_n\le \Lambda\ \ \forall n$; (ii) $\forall\varepsilon>0\ \ \exists\, n_\varepsilon\in\mathbb{N}$ t.c. $a_{n_\varepsilon}>\Lambda-\varepsilon$ |
| $\inf\{a_n\}=\lambda$ | (i) $a_n\ge \lambda\ \ \forall n$; (ii) $\forall\varepsilon>0\ \ \exists\, n_\varepsilon\in\mathbb{N}$ t.c. $a_{n_\varepsilon}<\lambda+\varepsilon$ |

In (ii) per $\sup$: $\Lambda$ è il *più piccolo* maggiorante, quindi $\Lambda-\varepsilon$ non è più maggiorante, cioè qualche termine lo supera. Se poi il valore $\Lambda$ è *assunto* da un termine, allora $\sup=\max$.

### Esempio: $b_n = \dfrac1n$, $n\ge1$

```desmos-graph
left=-0.5; right=8;
top=1.3; bottom=-0.3;
grid=true
---
(1,1)
(2,0.5)
(3,0.3333)
(4,0.25)
(5,0.2)
(6,0.1667)
(7,0.1429)
y=0|hidden
```

- $\sup = \max = 1$: $a_1 = 1$ e $\frac1n\le1\ \forall n\ge1$ (il candidato $M=1$ è assunto in $n=1$).
- $\inf = 0$ ma **non è minimo**.

**Verifica di $\inf\{b_n\}=0$.**
1. (i) $\frac1n > 0 \ \ \forall n\in\mathbb{N}$, quindi $0$ è minorante. ✓
2. (ii) Sia $\varepsilon>0$ arbitrario; si cerca $n_\varepsilon$ con $\frac1{n_\varepsilon}<\varepsilon \iff n_\varepsilon>\frac1\varepsilon$. Si sceglie
$$
n_\varepsilon = \left[\tfrac1\varepsilon\right] + 1,
$$
che è un naturale $>\frac1\varepsilon$. Dunque $\forall\varepsilon>0\ \exists\, n_\varepsilon$ t.c. $a_{n_\varepsilon}<\varepsilon = 0+\varepsilon$ $\Rightarrow$ $\inf\{b_n\}=0$. ✓

$0$ **non appartiene** all'immagine (nessun $n$ dà $\frac1n=0$), quindi **non esiste il minimo**.

> [!tip] Modo alternativo
> $\inf\{b_n\}$ si può vedere come l'estremo superiore dell'insieme dei minoranti di $I_{b_n}$, cioè $(-\infty,0]$: $\inf = \max(-\infty,0] = 0$.

**Continua in** [[Limiti di successioni]].
