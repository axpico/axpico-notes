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
###  A) Quantificatori
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

**a)  ∃x : ∀y p(x, y)**
```txt
Esiste un computer che ha tutti i problemi 
```

**b)  ∀x∀y : p(x, y)**
```txt
Tutti i computer hanno tutti i problemi  
```

###  B) Traduzioni

Traduci in simboli matematici le seguenti frasi:

1. I numeri reali compresi tra 1 e 3 o i numeri reali compresi tra 5 e 6s $$x ∈ ℝ ∧x∈(1,3)U(5,6)$$
2. I numeri naturali compresi tra 1 e 5$$x∈ \mathbb{N}  ∧x∈(1,5)$$
3. I numeri reali il cui quadrato e maggiore di 4$$x ∈ ℝ t.c. x^2 > 4$$
4. La somma dei primi 5 numeri dispari $$\sum_{n=0}^{4} (2n+1)$$
5. La somma dei reciproci dei quadrati dei primi 100 numeri pari $$\sum_{i=1}^{100}\frac{1}{(2i)^2}$$
6. Non esiste un numero naturale sia pari che dispari$$¬∃x ∈ \mathbb{N} : (x\%2=0) ∧ (x\%2=1) $$ $$∃a,b ∈ \mathbb{N} : n=2a+1 ∧ n=2b$$
7. I numeri naturali multipli di 3 o multipli di 2$$∃x ∈ \mathbb{N} : (x\%3=0) ∨ (x\%2=0)$$
8. Tutti i quadrati sono rettangoli $$Q = \{quadrati\},\ R=\{rettangoli\},\ Q \subseteq R VqEQ.$$


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
$$9+15+21+27+33+39+45$$
$$\sum_{i=1}^{7}(6i+3)$$
$$\frac{1}{4}-\frac{1}{6}+\frac{1}{8}-\frac{1}{10}+\frac{1}{12}-\frac{1}{14}+\frac{1}{16}$$
$$\sum_{i=2}^{8}(\frac{(-1)^i}{2i})$$
$$-1+\frac{1}{2}-3+\frac{1}{4}-5+\frac{1}{6}-7+\frac{1}{8}-9$$
$$\sum_{i=1}^{9}\left((-1)^i\, i^{(-1)^{i+1}}\right)$$


## Risorse
- [FDS PoliMi](https://linktr.ee/fdspolimi)
- [warmup](https://fds.mate.polimi.it/wp-content/uploads/2025/08/warmup01_linguaggio.pdf)