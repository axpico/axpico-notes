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
