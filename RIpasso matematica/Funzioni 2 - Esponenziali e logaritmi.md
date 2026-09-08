---
date: 2026-09-08
subject: matematica
topic: funzioni
tags:
  - matematica
  - funzioni
  - esponenziali
  - logaritmi
  - equazioni
  - disequazioni
---
# Lezione 7: Funzioni (2) — Warm-up

Corso di ripasso Matematica, laboratorio FDS (MOOC MAT101 Polimi).

## A) Decadimento radioattivo

Un decadimento esponenziale con tempo di dimezzamento $T$ si scrive
$$
N(t) = N_0 \cdot \left(\frac12\right)^{t/T}
$$
dove $N_0$ è la quantità iniziale e $N(t)$ quella rimasta dopo un tempo $t$. Qui $N_0$ e $N(t)$ sono le percentuali di Carbonio-14 sul totale (all'istante della morte l'organismo ha la stessa percentuale dell'atmosfera).

Dati: $T=5730$ anni, $N_0=10^{-12}$, $N(t)=1.2\cdot10^{-13}$.

```desmos-graph
left=-2000; right=30000; top=1.2e-12; bottom=0;
---
N=10^{-12}\left(\frac12\right)^{\frac{t}{5730}}
N=1.2\times10^{-13}
```

Isolo il rapporto e prendo il logaritmo:
$$
\frac{N(t)}{N_0} = \left(\frac12\right)^{t/T} \;\Rightarrow\; 0.12 = \left(\frac12\right)^{t/5730}
$$
$$
\frac{t}{5730} = \log_{1/2}(0.12) = \frac{\ln 0.12}{\ln 0.5} \approx \frac{-2.1203}{-0.6931} \approx 3.059
$$
$$
t \approx 3.059 \times 5730 \approx 17\,528 \text{ anni}
$$

Il fossile ha circa **17.500 anni**.

## B) Equazioni e disequazioni

### 1. $2^{8x} = 4^{\frac1x}$

Stessa base 2: $4^{1/x}=2^{2/x}$, quindi
$$
8x = \frac2x \;\Rightarrow\; 8x^2=2 \;\Rightarrow\; x^2=\frac14 \;\Rightarrow\; x=\pm\frac12
$$
(entrambe accettabili, $x\ne0$).

### 2. $4^{4-x}\cdot 4^{x+7} = 4^{x^2-4x-10}$

Stessa base: sommo gli esponenti a sinistra, $(4-x)+(x+7)=11$:
$$
4^{11} = 4^{x^2-4x-10} \;\Rightarrow\; x^2-4x-21=0 \;\Rightarrow\; x=\frac{4\pm\sqrt{16+84}}{2}=\frac{4\pm10}{2}
$$
$$
x=7 \ \lor\ x=-3
$$

### 3. $3^{2x} - 3^x - 6 = 0$

Sostituzione $t=3^x>0$:
$$
t^2-t-6=0 \;\Rightarrow\; (t-3)(t+2)=0 \;\Rightarrow\; t=3 \ \lor\ t=-2
$$
$t=-2$ scartata (non esiste $x$ con $3^x<0$). Resta $3^x=3$:
$$
x=1
$$

### 4. $16^x \ge \sqrt2$

Stessa base 2: $16^x=2^{4x}$, $\sqrt2=2^{1/2}$:
$$
2^{4x}\ge2^{1/2} \;\Rightarrow\; 4x\ge\frac12 \;\Rightarrow\; x\ge\frac18
$$

### 5. $2^{x-2} < 3^{x-2}$

```desmos-graph
left=-2; right=6; top=10; bottom=-1;
---
y=2^{x-2}
y=3^{x-2}
```
Per esponente positivo ($x>2$) la base maggiore vince: $3^{x-2}>2^{x-2}$, disuguaglianza vera. Per esponente negativo ($x<2$) succede il contrario (basi $<1$ dopo l'elevamento, la base minore dà il valore più grande). Per $x=2$ i due membri sono uguali (entrambi $1$).
$$
x>2
$$

### 6. $\log(x^2-3x+1)=0$

Dominio: $x^2-3x+1>0$. Tolgo il logaritmo:
$$
x^2-3x+1=10^0=1 \;\Rightarrow\; x^2-3x=0 \;\Rightarrow\; x(x-3)=0 \;\Rightarrow\; x=0 \ \lor\ x=3
$$
Entrambi verificano il dominio ($x^2-3x+1=1>0$ per entrambi).
$$
x=0 \ \lor\ x=3
$$

### 7. $\log_3(x-1) + \log_3(x+1) < 3$

Dominio: $x-1>0 \land x+1>0 \;\Rightarrow\; x>1$.
$$
\log_3\big[(x-1)(x+1)\big] < 3 \;\Rightarrow\; x^2-1 < 3^3=27 \;\Rightarrow\; x^2<28 \;\Rightarrow\; -2\sqrt7<x<2\sqrt7
$$
Intersecando col dominio ($x>1$):
$$
1 < x < 2\sqrt7 \quad(\approx 5.29)
$$

### 8. $\log(3x-1) > \log(7-x)$

Dominio: $3x-1>0 \Rightarrow x>\frac13$; $\ 7-x>0 \Rightarrow x<7$.
Log crescente ⇒ confronto diretto tra argomenti:
$$
3x-1 > 7-x \;\Rightarrow\; 4x>8 \;\Rightarrow\; x>2
$$
Intersecando col dominio ($\frac13<x<7$):
$$
2 < x < 7
$$

## C) Quiz

### 1. $7^{2+\log_7 x}$ è uguale, per ogni $x>0$, a...

Spezzo la somma all'esponente:
$$
7^{2+\log_7 x} = 7^2 \cdot 7^{\log_7 x} = 49x
$$
**Risposta: (a) $49x$** — $7^{\log_7 x}=x$ per definizione di logaritmo (funzioni inverse).

### 2. Se $f(x)=5^x$, allora $f(x+1)-f(x)$ è uguale a...

$$
f(x+1)-f(x) = 5^{x+1}-5^x = 5^x\cdot5 - 5^x = 5^x(5-1) = 4\cdot5^x
$$
**Risposta: (d) $4\cdot5^x$**

## Risorse
- [FDS PoliMi](https://linktr.ee/fdspolimi)
