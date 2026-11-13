---
tags:
  - geometria-algebra-lineare
  - esercizi
  - autovalori
  - autospazi
---
# Autovalori e autospazi — Esercizi svolti

Teoria: [[Autovalori, autovettori, autospazi e molteplicità]] · HTML: [[Lezione 10 — Autovalori, autovettori e autospazi.html|Lezione 10 (interattiva)]]
Parte A: esempi della Lezione 10 parte 1 (corretti) + esercizi extra. Parte B: esercitazione dell'11-11 (disegno [[Drawing 2026-11-11 15.31.26.excalidraw|11-11 pomeriggio]]).

> [!tip] Ricetta
> 1. $p(\lambda)=\det(A-\lambda I)$ → radici = autovalori, con $m_a$.
> 2. Per ogni $\lambda$: Gauss su $A-\lambda I$ → base di $\ker(A-\lambda I)$, $m_g=n-r(A-\lambda I)$.
> 3. **Controlla** $A\underline x=\lambda\underline x$. Controlli globali: $\operatorname{tr}A=\sum\lambda_i$, $\det A=\prod\lambda_i$.

---

# Parte A — Autovalori, autovettori, autospazi

## A1. Matrice triangolare (Esempio A, pp. 34–38)

$$A=\begin{bmatrix}2&1&1\\0&3&0\\0&0&-1\end{bmatrix}$$

**Autovalori.** Triangolare ⇒ $p(\lambda)=(2-\lambda)(3-\lambda)(-1-\lambda)$ ⇒ $\lambda_1=2,\ \lambda_2=3,\ \lambda_3=-1$, tutti semplici.

**$\lambda=2$.** $A-2I=\begin{bmatrix}0&1&1\\0&1&0\\0&0&-3\end{bmatrix}\to\begin{bmatrix}0&1&1\\0&0&-1\\0&0&0\end{bmatrix}$ ⇒ $y=z=0$, $x$ libera ⇒ $V_2=\mathrm{span}\{(1,0,0)^T\}$.

**$\lambda=3$.** $A-3I=\begin{bmatrix}-1&1&1\\0&0&0\\0&0&-4\end{bmatrix}$ ⇒ $z=0$, $x=y$ ⇒ $V_3=\mathrm{span}\{(1,1,0)^T\}$.

**$\lambda=-1$.** $A+I=\begin{bmatrix}3&1&1\\0&4&0\\0&0&0\end{bmatrix}$ ⇒ $y=0$, $3x+z=0$ ⇒ $V_{-1}=\mathrm{span}\{(-1,0,3)^T\}$.

Controllo: $A(-1,0,3)^T=(-2+3,\,0,\,-3)^T=(1,0,-3)^T=-1\cdot(-1,0,3)^T$ ✓

> [!bug] Il PDF (p. 38) scrive $1+1=2$ al posto di $2+1=3$ in posizione $(1,1)$ e ottiene $(-\tfrac12,0,1)^T$, che non è autovettore: $A(-\tfrac12,0,1)^T=(0,0,-1)^T$.

## A2. Autovalore doppio regolare (Esempio 1, pp. 38–41)

$$A=\begin{bmatrix}3&0&-2\\1&1&-1\\1&0&0\end{bmatrix}$$

**$p(\lambda)$** con Laplace sulla 2ª colonna (un solo elemento non nullo):
$$p(\lambda)=(1-\lambda)\begin{vmatrix}3-\lambda&-2\\1&-\lambda\end{vmatrix}=(1-\lambda)(\lambda^2-3\lambda+2)=(1-\lambda)(\lambda-1)(\lambda-2).$$
Autovalori: $\lambda_1=2$ ($m_a=1$), $\lambda_{2,3}=1$ ($m_a=2$). Controllo: $\operatorname{tr}A=4=2+1+1$ ✓, $\det A=2=2\cdot1\cdot1$ ✓.

**$\lambda=2$.** $A-2I=\begin{bmatrix}1&0&-2\\1&-1&-1\\1&0&-2\end{bmatrix}\to\begin{bmatrix}1&0&-2\\0&-1&1\\0&0&0\end{bmatrix}$ ⇒ $x=2z$, $y=z$ ⇒ $V_2=\mathrm{span}\{(2,1,1)^T\}$. Controllo: $A(2,1,1)^T=(4,2,2)^T$ ✓

**$\lambda=1$.** $A-I=\begin{bmatrix}2&0&-2\\1&0&-1\\1&0&-1\end{bmatrix}$: rango 1, unica equazione $x-z=0$, libere $y,z$.
- $(y,z)=(1,0)\Rightarrow(0,1,0)^T$; $(y,z)=(0,1)\Rightarrow(1,0,1)^T$.

$V_1=\mathrm{span}\{(0,1,0)^T,(1,0,1)^T\}$, $m_g(1)=2=m_a(1)$ ⇒ **regolare**. Entrambi gli autovalori sono regolari.

## A3. Autovalore doppio irregolare (Esempio 2, pp. 41–46)

$$A=\begin{bmatrix}3&1&-3\\1&2&-2\\1&1&-1\end{bmatrix}$$

**$p(\lambda)$.** $R_1\to R_1-R_3$, $R_2\to R_2-R_3$ (non cambiano il determinante):
$$\begin{vmatrix}2-\lambda&0&\lambda-2\\0&1-\lambda&\lambda-1\\1&1&-1-\lambda\end{vmatrix}=(2-\lambda)(1-\lambda)\begin{vmatrix}1&0&-1\\0&1&-1\\1&1&-1-\lambda\end{vmatrix}$$
e l'ultimo determinante vale $(-1-\lambda)+1+1=1-\lambda$. Quindi $p(\lambda)=(2-\lambda)(1-\lambda)^2$: stesso polinomio dell'A2!

**$\lambda=2$.** $A-2I=\begin{bmatrix}1&1&-3\\1&0&-2\\1&1&-3\end{bmatrix}\to\begin{bmatrix}1&1&-3\\0&-1&1\\0&0&0\end{bmatrix}$ ⇒ $y=z$, $x=2z$ ⇒ $V_2=\mathrm{span}\{(2,1,1)^T\}$. Controllo: $A(2,1,1)^T=(4,2,2)^T$ ✓

> [!bug] Il PDF (p. 43) mette $-1$ in posizione $(2,2)$ invece di $2-2=0$ e trova $(5,1,2)^T$: falso, $A(5,1,2)^T=(10,3,4)^T\neq(10,2,4)^T$.

**$\lambda=1$.** $A-I=\begin{bmatrix}2&1&-3\\1&1&-2\\1&1&-2\end{bmatrix}\to\begin{bmatrix}1&1&-2\\0&-1&1\\0&0&0\end{bmatrix}$ ⇒ $y=z$, $x=z$ ⇒ $V_1=\mathrm{span}\{(1,1,1)^T\}$.

$m_g(1)=1<m_a(1)=2$ ⇒ $\lambda=1$ **irregolare**. Ci sono solo 2 autovettori indipendenti in $\mathbb R^3$ ⇒ nessuna base di autovettori ⇒ $A$ **non** è diagonalizzabile.

## A4. Trappola: Gauss non conserva gli autovalori (pp. 46–47)

Ridurre la matrice dell'A3: $\begin{bmatrix}3&1&-3\\1&2&-2\\1&1&-1\end{bmatrix}\to\cdots\to\begin{bmatrix}1&1&-1\\0&1&-1\\0&0&-2\end{bmatrix}$. Sulla diagonale si legge $1,1,-2$, ma gli autovalori di $A$ sono $2,1,1$. **Mai** ridurre $A$ prima di calcolare $p(\lambda)$.

## A5–A8. Esercizi extra

**A5.** $A=\begin{bmatrix}4&1\\2&3\end{bmatrix}$. Trova autovalori e autospazi, e se possibile $S$, $D$.

> [!success]- Soluzione
> $p(\lambda)=(4-\lambda)(3-\lambda)-2=\lambda^2-7\lambda+10=(\lambda-2)(\lambda-5)$.
> - $\lambda=5$: $A-5I=\begin{bmatrix}-1&1\\2&-2\end{bmatrix}$ ⇒ $x=y$ ⇒ $V_5=\mathrm{span}\{(1,1)^T\}$.
> - $\lambda=2$: $A-2I=\begin{bmatrix}2&1\\2&1\end{bmatrix}$ ⇒ $y=-2x$ ⇒ $V_2=\mathrm{span}\{(1,-2)^T\}$.
>
> Due autovalori semplici ⇒ base di autovettori: $S=\begin{bmatrix}1&1\\1&-2\end{bmatrix}$, $D=\mathrm{diag}(5,2)$, $S^{-1}AS=D$.

**A6.** $A=\begin{bmatrix}1&1\\0&1\end{bmatrix}$. Calcola $m_a$ e $m_g$ di ogni autovalore.

> [!success]- Soluzione
> Triangolare ⇒ $\lambda=1$ con $m_a=2$. $A-I=\begin{bmatrix}0&1\\0&0\end{bmatrix}$, rango 1 ⇒ $m_g=2-1=1$, $V_1=\mathrm{span}\{(1,0)^T\}$. Irregolare ⇒ non diagonalizzabile.

**A7.** $A=\begin{bmatrix}0&-1\\1&0\end{bmatrix}$ (rotazione di $90°$). Ha autovalori reali?

> [!success]- Soluzione
> $p(\lambda)=\lambda^2+1$: nessuna radice reale ⇒ nessun autovettore in $\mathbb R^2$ (una rotazione di $90°$ non lascia fissa nessuna direzione). Su $\mathbb C$: $\lambda=\pm i$, con $V_i=\mathrm{span}\{(i,1)^T\}$, $V_{-i}=\mathrm{span}\{(-i,1)^T\}$. Diagonalizzabile su $\mathbb C$, non su $\mathbb R$.

**A8.** $A=\begin{bmatrix}1&2&0\\2&1&0\\0&0&3\end{bmatrix}$. Autovalori, autospazi, molteplicità.

> [!success]- Soluzione
> Laplace sulla 3ª riga: $p(\lambda)=(3-\lambda)\big[(1-\lambda)^2-4\big]=(3-\lambda)(\lambda-3)(\lambda+1)$ ⇒ $\lambda=3$ ($m_a=2$), $\lambda=-1$ ($m_a=1$).
> - $\lambda=3$: $A-3I=\begin{bmatrix}-2&2&0\\2&-2&0\\0&0&0\end{bmatrix}$, rango 1 ⇒ $x=y$, $z$ libera ⇒ $V_3=\mathrm{span}\{(1,1,0)^T,(0,0,1)^T\}$, $m_g=2$ ⇒ regolare.
> - $\lambda=-1$: $A+I=\begin{bmatrix}2&2&0\\2&2&0\\0&0&4\end{bmatrix}$ ⇒ $z=0$, $y=-x$ ⇒ $V_{-1}=\mathrm{span}\{(1,-1,0)^T\}$.
>
> Tutti regolari: $S=\begin{bmatrix}1&0&1\\1&0&-1\\0&1&0\end{bmatrix}$, $D=\mathrm{diag}(3,3,-1)$.

---

# Parte B — Esercitazione 11-11 (pomeriggio)

## B1. Cramer

$$\begin{cases}x-y=3\\y+z=1\\x-z=3\end{cases}\qquad A=\begin{bmatrix}1&-1&0\\0&1&1\\1&0&-1\end{bmatrix},\ \underline b=\begin{bmatrix}3\\1\\3\end{bmatrix}$$

Promemoria: $A\in M_n(\mathbb R)$, $\exists!$ soluzione $\iff|A|\neq0$, e $x_i=\dfrac{|A_i|}{|A|}$ con $A_i$ = $A$ con la colonna $i$ sostituita da $\underline b$.

$|A|=1\cdot(-1-0)-(-1)(0-1)=-1-1=-2\neq0$.
$$x=-\tfrac12\begin{vmatrix}3&-1&0\\1&1&1\\3&0&-1\end{vmatrix}=-\tfrac12(-7)=\tfrac72,\quad y=-\tfrac12\begin{vmatrix}1&3&0\\0&1&1\\1&3&-1\end{vmatrix}=-\tfrac12(-1)=\tfrac12,\quad z=-\tfrac12\begin{vmatrix}1&-1&3\\0&1&1\\1&0&3\end{vmatrix}=\tfrac12.$$
Controllo: $\tfrac72-\tfrac12=3$ ✓, $\tfrac12+\tfrac12=1$ ✓, $\tfrac72-\tfrac12=3$ ✓.

## B2. Sistema con $\infty^3$ soluzioni (Cramer con parametri)

$$\begin{cases}x_1-x_3+2x_5=1\\x_2+x_4=2\\2x_1-x_2+x_6=3\end{cases}\qquad A=\begin{bmatrix}1&0&-1&0&2&0\\0&1&0&1&0&0\\2&-1&0&0&0&1\end{bmatrix}$$

Il minore sulle colonne $1,2,6$ è $\begin{vmatrix}1&0&0\\0&1&0\\2&-1&1\end{vmatrix}=1\neq0$ ⇒ $r(A)=3$ ⇒ $\infty^{6-3}=\infty^3$ soluzioni, con $x_3,x_4,x_5$ parametri liberi. Si porta a destra la parte libera:
$$\underline b'=\begin{bmatrix}1+x_3-2x_5\\2-x_4\\3\end{bmatrix}$$
e Cramer sulle colonne $1,2,6$ (determinante $=1$):
$$x_6=\begin{vmatrix}1&0&1+x_3-2x_5\\0&1&2-x_4\\2&-1&3\end{vmatrix}=3-2x_3-x_4+4x_5,$$
$$x_1=1+x_3-2x_5,\qquad x_2=2-x_4 .$$
(Nel disegno c'è scritto $-2x_3$ dentro $\underline b'$: va $-2x_5$.)

## B3. Applicazione lineare $f:\mathbb R^4\to\mathbb R^3$

$\underline v_1=(4,-2,6)$, $\underline v_2=(0,4,4)$, $\underline v_3=(-1,2,0)$, con
$$f(1,0,1,0)=\underline v_1,\quad f(\,?\,)=\underline v_2,\quad f(0,1,0,0)=\underline v_3,\quad f(2,0,-1,-3)=\underline v_3 .$$
1. Matrice di $f$ rispetto alle basi canoniche; basi di $\ker f$ e $\operatorname{Im}f$.
2. $W\le\mathbb R^4$ di equazione $x_1+3x_3+x_4=0$: base di $W$, di $f(W)$, di $\ker f\cap W$.

> [!warning] Dato ambiguo
> Nel disegno il secondo vettore è scritto di nuovo $(1,0,1,0)$, che è impossibile (avrebbe due immagini diverse). Qui si assume **$(1,0,-1,0)$** (rende i quattro vettori una base). Se il testo vero è diverso, cambia la parte 1; il metodo resta identico.

**1. Matrice.** Servono $f(\underline e_i)$ (le colonne). Con $\underline e_1+\underline e_3\mapsto\underline v_1$ e $\underline e_1-\underline e_3\mapsto\underline v_2$:
$$f(\underline e_1)=\tfrac12(\underline v_1+\underline v_2)=(2,1,5),\quad f(\underline e_3)=\tfrac12(\underline v_1-\underline v_2)=(2,-3,1),\quad f(\underline e_2)=(-1,2,0).$$
Da $(2,0,-1,-3)=2\underline e_1-\underline e_3-3\underline e_4$: $3f(\underline e_4)=2(2,1,5)-(2,-3,1)-(-1,2,0)=(3,3,9)$ ⇒ $f(\underline e_4)=(1,1,3)$.
$$A=\begin{bmatrix}2&-1&2&1\\1&2&-3&1\\5&0&1&3\end{bmatrix}\xrightarrow{\text{rref}}\begin{bmatrix}1&0&\tfrac15&\tfrac35\\0&1&-\tfrac85&\tfrac15\\0&0&0&0\end{bmatrix}$$
$r(A)=2$.
- $\operatorname{Im}f=\mathrm{span}\{(2,1,5),(-1,2,0)\}$ (colonne pivot), $\dim=2$; equazione cartesiana $2x+y-z=0$.
- $\dim\ker f=4-2=2$: $\ker f=\mathrm{span}\{(-1,8,5,0),(-3,-1,0,5)\}$.

**2.** $W$: $x_1=-3x_3-x_4$ ⇒ base $\{(0,1,0,0),(-3,0,1,0),(-1,0,0,1)\}$, $\dim W=3$.
- Immagini: $(-1,2,0)$, $(-4,-6,-14)$, $(-1,0,-2)$; rango 2 ⇒ $f(W)=\mathrm{span}\{(-1,2,0),(-1,0,-2)\}=\operatorname{Im}f$.
- $\ker f\cap W$: aggiungi l'equazione di $W$ al sistema $A\underline x=\underline 0$ ⇒ $\mathrm{span}\{(-4,-3,-1,7)\}$, $\dim=1$.
- Coerenza: $\dim f(W)=\dim W-\dim(\ker f\cap W)=3-1=2$ ✓.

## B4. Matrice di un'applicazione e coordinate

Se $\mathcal B=(\underline v_1,\dots,\underline v_n)$ e $f(\underline v_i)=\underline w_i$, $f$ è determinata. Es.: $f(\underline e_1+\underline e_3)=4\underline e_1'-2\underline e_2'+6\underline e_3'$ è proprio $f(1,0,1,0)=\underline v_1$ scritto nelle basi canoniche.

## B5. Relazioni di equivalenza

Relazione su $X$: $R\subseteq X\times X$. È **di equivalenza** se:
1. **riflessiva**: $a\sim a$ $\forall a\in X$;
2. **simmetrica**: $a\sim b\Rightarrow b\sim a$;
3. **transitiva**: $a\sim b,\ b\sim c\Rightarrow a\sim c$.

**Similitudine.** $A\sim B$ se $\exists P$, $|P|\neq0$, con $B=P^{-1}AP$. È di equivalenza:
- riflessiva: $A=I^{-1}AI$;
- simmetrica: $A=PBP^{-1}=(P^{-1})^{-1}B(P^{-1})$;
- transitiva: $B=P^{-1}AP$, $C=Q^{-1}BQ$ ⇒ $C=Q^{-1}P^{-1}APQ=(PQ)^{-1}A(PQ)$.

È il motivo per cui ha senso parlare di "classe" di matrici che rappresentano lo stesso endomorfismo, e di diagonalizzazione (trovare la diagonale nella classe di $A$).

**Esempio su $X=\{1,2,3,4,5\}$.** $R=\{(1,1),(2,2),(3,3),(5,5),(1,2),(2,1),(1,3),(3,1),(2,3),(3,2),(1,5),(5,1)\}$.
Non è di equivalenza: manca $(4,4)$ (non riflessiva) e, da $(5,1),(1,2)$, manca $(5,2)$ (non transitiva). La più piccola relazione di equivalenza che la contiene ha classi $\{1,2,3,5\}$ e $\{4\}$.

**Grafo e matrice.** $a$–$b$–$d$ collegati, $c$ ed $e$ isolati: la matrice ha $1$ sulla diagonale (riflessiva), è simmetrica, e i blocchi $\{a,b,d\}$, $\{c\}$, $\{e\}$ sono "tutti 1" (transitiva). Classi: $\{a,b,d\},\{c\},\{e\}$.

**Congruenza modulo $n$ su $\mathbb Z$.** $a\equiv b\pmod n\iff a-b=hn$, $h\in\mathbb Z$.
1. $a-a=0\cdot n$ ✓
2. $a-b=hn\Rightarrow b-a=(-h)n$ ✓
3. $a-b=hn$, $b-c=kn\Rightarrow a-c=(h+k)n$ ✓
