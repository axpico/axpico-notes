---
date: 2026-01-31
subject: matematica
topic: linguaggio matematico
tags:
  - matematica
  - linguaggio-matematico
  - quantificatori
---
# Linguaggio Matematico

Uso di simboli e linguaggio per tradurre dalla matematica all'[[Italiano]] e viceversa.

## Esercizi
### A) Quantificatori
Indichiamo con p(x, y) l’espressione: “Il computer x ha il problema y”.
#### Esercizio 1
Trascrivere per mezzo dei quantificatori “per ogni” (**∀**) -> tutti ed “esiste” (**∃**) -> alemno 1 le seguenti frasi:

**a) Ogni computer ha un problema**
$$
∀x : ∃y p(x, y)
$$

**b) C’è un problema che tutti i computer hanno**
$$
∃y : ∀x p(x, y)
$$
#### Esercizio 2

Trascrivere nel linguaggio comune le seguenti espressioni:

**a) ∃x : ∀y p(x, y)**
```txt
Esiste un computer che ha tutti i problemi
```

**b) ∀x∀y : p(x, y)**
```txt
Tutti i computer hanno tutti i problemi
```

### B) Traduzioni

Traduci in simboli matematici le seguenti frasi:

1. I numeri reali compresi tra 1 e 3 o i numeri reali compresi tra 5 e 6 $$x \in ℝ \land x\in(1,3)\cup(5,6)$$
2. I numeri naturali compresi tra 1 e 5 $$x \in \mathbb{N} \land x\in(1,5)$$
3. I numeri reali il cui quadrato e maggiore di 4$$x ∈ ℝ t.c. x^2 > 4$$
4. La somma dei primi 5 numeri dispari $$\sum_{n=0}^{4} (2n+1)$$
5. La somma dei reciproci dei quadrati dei primi 100 numeri pari $$\sum_{i=1}^{100}\frac{1}{(2i)^2}$$
6. Non esiste un numero naturale sia pari che dispari$$¬∃x ∈ \mathbb{N} : (x\%2=0) ∧ (x\%2=1) $$ $$∃a,b ∈ \mathbb{N} : n=2a+1 ∧ n=2b$$
7. I numeri naturali multipli di 3 o multipli di 2$$∃x ∈ \mathbb{N} : (x\%3=0) ∨ (x\%2=0)$$
8. Tutti i quadrati sono rettangoli $$Q = \{quadrati\},\ R=\{rettangoli\},\ Q \subseteq R,\ \forall q \in Q$$
## Lezione 
$$\sum_{k=1}^{20}(2k-1)$$
la somma dei primi venti numeri dispari
$$\{x \in \mathbb{R} \mid x^2-4=0\}$$
tutti i numeri reali il cui quadrato sottratto 4 e 0

$$∃n \in \mathbb{N} : n^2=49$$
esiste un numero naturale il cui quadrato fa 49
$$\{m \in \mathbb{Z} \mid m=3k,\ k \in \mathbb{Z}\}$$
l'insieme dei numeri interi m che sono multipli di 3
$$\{n \in \mathbb{N} \mid (n\ge50) \land (n\le100)\}$$
l'insieme dei numeri naturali n maggiori o uguali a 50 e minori o uguali a 100

### Sequenza numeriche 
#### Somma di numeri in progressione aritmetica
$$9+15+21+27+33+39+45$$
$$\sum_{i=1}^{7}(6i+3)$$
#### Somma a segni alterni di frazioni pari
$$\frac{1}{4}-\frac{1}{6}+\frac{1}{8}-\frac{1}{10}+\frac{1}{12}-\frac{1}{14}+\frac{1}{16}$$
$$\sum_{i=2}^{8}({\frac{(-1)^i}{2i}})$$
#### Somma a segni alterni tra dispari e reciproci di pari
$$-1+\frac{1}{2}-3+\frac{1}{4}-5+\frac{1}{6}-7+\frac{1}{8}-9$$
$$\sum_{i=1}^{9}\left((-1)^i\, i^{(-1)^{i+1}}\right)$$

### Sommatorie
$$\sum_{k=1}^{19}(k^2-k)=1^1-1+2^2-2+...$$
si puo scrivere cosi 
$$\sum_{k=1}^{10}(k^2)-\sum_{k=1}^{10}(k)$$

#### Formula per i primi n quadrati
$$\sum_{k=1}^{n} k^2 =\frac{n(n+1)(2n+1)}{6}$$
$$\sum_{k=1}^{10}(k^2)=\frac{10(10+1)(2*10+1)}{6}=5*11*7=385$$
$$1+1=$$
#### Formula di Gauss (somma dei primi n numeri naturali)
$$\sum_{i=1}^{n}k=\frac{n*(n+1)}{2}$$
$$\sum_{k=1}^{10}k=\frac{10(11)}{2}=\frac{110}{2}=55$$
quindi:
$$\sum_{k=1}^{10}(k^2)-\sum_{k=1}^{10}(k)=385-55=330$$

#### Sommatoria alternata di (-1)^k
$$\sum_{k=1}^{n}(-1)^k=\begin{cases}0 & n\text{ pari}\\-1 & n\text{ dispari}\end{cases}$$
$$\sum_{k=1}^{n}(-1)^{k+1}=\begin{cases}0 & n\text{ pari}\\1 & n\text{ dispari}\end{cases}$$
#### Somma simmetrica da -n a n
$$\sum_{k=-n}^{n}k = \sum_{k=1}^{n}k - \sum_{k=1}^{n}k = 0$$
#### Serie geometrica di ragione n
$$\sum_{k=0}^{n}n^k=\frac{n^{n+1}-1}{n-1}\qquad(n\neq1)$$
$$\sum_{k=0}^{3}3^k=1+3+9+27=40=\frac{3^4-1}{3-1}=\frac{80}{2}$$
### Calcolo combinatorio
#### Permutazioni: anagrammi
Monte -> permutazione semplice (5 lettere tutte diverse)
$$P_n = n!$$
$$P_5= 5! = 5*4*3*2*1 = 120$$
Mente -> permutazione con ripetizione (la E si ripete 2 volte)
$$P_n^* = \frac {n!}{k_1!k_2!k_3!...}$$
$$P_5^*=\frac{5!}{2!}=\frac{120}{2}=60$$
Azzurra -> permutazione con ripetizione (A, Z, R si ripetono 2 volte ciascuna)
$$P_7^*=\frac{7!}{2!2!2!}=\frac{5040}{8}=630$$
Alessandro -> permutazione con ripetizione (A, S si ripetono 2 volte ciascuna)
$$P_{10}^*=\frac{10!}{2!2!}=\frac{3628800}{4}=907200$$
Vittoria -> permutazione con ripetizione (I, T si ripetono 2 volte ciascuna)
$$P_8^*=\frac{8!}{2!2!}=\frac{40320}{4}=10080$$
Valerio -> permutazione semplice (7 lettere tutte diverse)
$$P_7= 7! = 5040$$
Pietro -> permutazione semplice (6 lettere tutte diverse)
$$P_6= 6! = 720$$
Marco -> permutazione semplice (5 lettere tutte diverse)
$$P_5= 5! = 120$$
#### Disposizioni semplici
Quanti numeri di 3 cifre diverse si possono scrivere usando A={1,2,3,4,5}?
Disposizione semplice (conta l'ordine, senza ripetizione), n -> oggetti disponibili, k -> posti da riempire
$$D_{n,k}=\frac{n!}{(n-k)!}$$
$$D_{5,3}=\frac{5!}{2!}=5*4*3=60$$

Quanti numeri **pari** di 3 cifre diverse si possono scrivere usando A={1,2,3,4,5}?
L'ultima cifra deve essere pari (2 o 4: 2 scelte), le altre 2 cifre si dispongono tra le 4 rimaste
$$2*D_{4,2}=2*\frac{4!}{2!}=2*(4*3)=24$$

Quanti numeri di 3 cifre diverse si possono scrivere usando A={1,2,3,5}?
$$D_{4,3}=\frac{4!}{1!}=4*3*2=24$$

Quanti numeri **pari** di 3 cifre diverse si possono scrivere usando A={1,2,3,5}?
L'ultima cifra deve essere pari (solo 2: 1 scelta), le altre 2 cifre si dispongono tra le 3 rimaste
$$1*D_{3,2}=1*\frac{3!}{1!}=1*(3*2)=6$$

#### Binomio di Newton
Formula generale per sviluppare $(a+b)^n$: somma di tutti i termini $a^{n-k}b^k$, ciascuno pesato dal coefficiente binomiale $\binom{n}{k}$
$$(a+b)^n=\sum_{k=0}^{n}\binom{n}{k}a^{n-k}b^k \qquad \binom{n}{k}=\frac{n!}{k!(n-k)!}$$
n -> oggetti disponibili, k -> posti da riempire non ordinati (combinazione)

Esempio con n=4:
$$(a+b)^4=a^4+4a^3b+6a^2b^2+4ab^3+b^4$$
$$\binom{4}{1}=\frac{4!}{1!3!}=4 \quad \to a^3b \text{ compare 4 volte}$$
$$\binom{4}{2}=\frac{4!}{2!2!}=6 \quad \to a^2b^2 \text{ compare 6 volte}$$
Quanti sono i termini di grado 5 in (a+b)^5?
Ogni termine $a^{5-k}b^k$ ha grado $(5-k)+k=5$ per qualsiasi k, quindi tutti i termini dello sviluppo sono di grado 5: sono $n+1=6$ (k da 0 a 5)
$$(a+b)^5=\sum_{k=0}^{5}\binom{5}{k}a^{5-k}b^k = a^5+5a^4b+10a^3b^2+10a^2b^3+5ab^4+b^5$$

Ponendo a=b=1 nel binomio di Newton, la somma di tutti i coefficienti binomiali di riga n vale $2^n$
$$\sum_{k=0}^{n}\binom{n}{k} = (1+1)^n = 2^n$$
## Risorse
- [FDS PoliMi](https://linktr.ee/fdspolimi)
- [warmup](https://fds.mate.polimi.it/wp-content/uploads/2025/08/warmup01_linguaggio.pdf)