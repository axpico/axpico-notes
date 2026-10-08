---
tags:
  - geometria-algebra-lineare
  - spazi-vettoriali
  - combinazioni-lineari
  - span
---
## Combinazioni lineari e sottospazio generato

### Combinazione lineare

**Definizione.** Sia $V$ uno spazio vettoriale su $\mathbb K$. Un vettore $\vec w\in V$ è una **combinazione lineare** dei vettori $\vec v_1,\dots,\vec v_n\in V$ se esistono scalari $\alpha_1,\dots,\alpha_n\in\mathbb K$ tali che

$$
\vec w=\sum_{j=1}^n\alpha_j\vec v_j=\alpha_1\vec v_1+\alpha_2\vec v_2+\dots+\alpha_n\vec v_n .
$$

**Esempio 1.** $\vec w=(1,2,3)\in\mathbb R^3$ è combinazione lineare di $\vec v_1=(1,0,1)$ e $\vec v_2=(0,1,1)$: infatti
$$
\vec v_1+2\vec v_2=(1,0,1)+(0,2,2)=(1,2,3)=\vec w
$$
(coefficienti $\alpha_1=1$, $\alpha_2=2$). Trovare i coefficienti equivale a risolvere un **sistema lineare** nelle incognite $\alpha_j$: $\vec w$ è combinazione lineare di $\vec v_1,\dots,\vec v_n\in\mathbb K^m$ se e solo se il sistema con matrice completa $[\vec v_1\mid\cdots\mid\vec v_n\mid\vec w]$ è risolvibile, cioè (Rouché-Capelli) se e solo se $r([\vec v_1\cdots\vec v_n])=r([\vec v_1\cdots\vec v_n\mid\vec w])$. Si veda [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Sistemi lineari e teorema di Rouché-Capelli]].

**Esempio 2 (spazio delle funzioni).** In $V=\{f:\mathbb R\to\mathbb R\}$ la funzione $f(x)=x^3$ **non** è combinazione lineare di $g_1(x)=x^2$, $g_2(x)=x^4$, $g_3(x)=\cos x$. Infatti $g_1,g_2,g_3$ sono funzioni **pari** ($g(-x)=g(x)$), quindi ogni loro combinazione lineare $\alpha_1g_1+\alpha_2g_2+\alpha_3g_3$ è ancora una funzione pari (le funzioni pari sono un sottospazio), mentre $x^3$ è dispari e non nulla, quindi non è pari.

### Sottospazio generato da un insieme finito

Sia $E=\{\vec v_1,\dots,\vec v_n\}\ne\varnothing$ un sottoinsieme finito di $V$. Consideriamo due combinazioni lineari degli elementi di $E$:

$$
\vec u=\alpha_1\vec v_1+\dots+\alpha_n\vec v_n,\qquad \vec v=\beta_1\vec v_1+\dots+\beta_n\vec v_n .
$$

Allora, per le proprietà (i)-(viii) degli spazi vettoriali (commutatività, associatività e distributività),

$$
\vec u+\vec v=(\alpha_1+\beta_1)\vec v_1+\dots+(\alpha_n+\beta_n)\vec v_n,
$$

che è ancora una combinazione lineare degli elementi di $E$; e per ogni $\lambda\in\mathbb K$

$$
\lambda\vec u=(\lambda\alpha_1)\vec v_1+\dots+(\lambda\alpha_n)\vec v_n
$$

è ancora una combinazione lineare degli elementi di $E$. Abbiamo dimostrato:

### Proposizione 1

*Sia $V$ uno spazio vettoriale su $\mathbb K$ e siano $\vec v_1,\dots,\vec v_n\in V$. Allora l'insieme delle loro combinazioni lineari*

$$
W:=\{\alpha_1\vec v_1+\dots+\alpha_n\vec v_n:\ \alpha_1,\dots,\alpha_n\in\mathbb K\}
$$

*è un sottospazio di $V$.*

*Dimostrazione.* $W\ne\varnothing$ (contiene $\vec 0=0\vec v_1+\dots+0\vec v_n$ e ogni $\vec v_j$) ed è chiuso per somma e prodotto per scalare per quanto appena visto: è un sottospazio per definizione. $\blacksquare$

Il sottospazio $W$ si chiama **sottospazio generato** da $\vec v_1,\dots,\vec v_n$, oppure **span lineare** di questi vettori, e si indica

$$
\operatorname{span}\{\vec v_1,\dots,\vec v_n\}.
$$

**Osservazioni.**

1. È il **più piccolo** sottospazio contenente $\vec v_1,\dots,\vec v_n$: ogni sottospazio $W'$ che li contiene contiene anche tutte le loro combinazioni lineari (per chiusura rispetto a somma e prodotto per scalare), quindi $W\subseteq W'$.
2. In $\mathbb R^3$: lo span di un vettore $\vec v\ne\vec 0$ è la **retta** per l'origine di direzione $\vec v$; lo span di due vettori non paralleli è il **piano** per l'origine che li contiene. Nell'Esempio 1, $\operatorname{span}\{(1,0,1),(0,1,1)\}=\{(a,b,a+b)\}=\{x+y-z=0\}$ e infatti $(1,2,3)$ vi appartiene ($1+2-3=0$), mentre $(1,2,4)$ no.
3. Se $\vec w\in\operatorname{span}\{\vec v_1,\dots,\vec v_n\}$ allora lo span non cambia aggiungendo $\vec w$ all'elenco.

### Osservazione: soluzioni dei sistemi lineari

Per il teorema di Rouché-Capelli, l'insieme delle soluzioni di un sistema **omogeneo** $A\vec x=\vec 0$ in $n$ incognite è $\{\vec 0\}$ (se $r(A)=n$) oppure lo **span lineare di un numero finito di vettori** di $\mathbb K^n$ (i vettori che moltiplicano i parametri liberi: sono $n-r(A)$). In entrambi i casi l'insieme delle soluzioni è un **sottospazio di $\mathbb K^n$** (per la Proposizione 1; il caso $\{\vec 0\}$ è lo span del vettore nullo, il sottospazio banale).

Invece, se $\vec b\ne\vec 0$, l'insieme delle soluzioni di $A\vec x=\vec b$ **non** è un sottospazio di $\mathbb K^n$. *Perché?* Perché $\vec 0$ **non** è una soluzione ($A\vec 0=\vec 0\ne\vec b$), mentre ogni sottospazio contiene il vettore nullo (si veda [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]]). Per esempio le soluzioni di $x+y=1$ in $\mathbb R^2$ sono una retta che non passa per l'origine. (Si tratta di un **sottospazio affine**: soluzione particolare + soluzioni dell'omogeneo associato.)

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Vettori geometrici liberi.md|Vettori geometrici liberi]]
- [[Politecnico/Geometria e Algebra Lineare/Esercizi/Vettori, spazi vettoriali, sottospazi e applicazioni — Esercizi svolti.md|Esercizi — Vettori, spazi vettoriali, sottospazi e applicazioni]]
- [[Politecnico/Geometria e Algebra Lineare/Esercizi/Rango, sottospazi, combinazioni lineari e indipendenza — Appunti ed esercizi.md|Esercizi — Rango, sottospazi, combinazioni lineari]]
