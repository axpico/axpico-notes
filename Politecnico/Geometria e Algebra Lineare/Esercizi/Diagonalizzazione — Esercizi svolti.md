---
tags:
  - geometria-algebra-lineare
  - esercizi
  - diagonalizzazione
---
# Diagonalizzazione — Esercizi svolti

Teoria: [[Criterio di diagonalizzabilità e invarianza del polinomio caratteristico]] · Parte 1: [[Autovalori e autospazi — Esercizi svolti]] · HTML: [[Lezione 10 parte 2 — Criterio di diagonalizzabilità.html|Lezione 10 parte 2 (interattiva)]]

> [!tip] Ricetta "è diagonalizzabile? trova $S$, $D$"
> 1. $p_A(\lambda)$ → autovalori e $m_a$. (Su $\mathbb R$: radici non reali ⇒ no.)
> 2. Autovalori semplici: regolari gratis.
> 3. Autovalori multipli: $m_g=n-r(A-\lambda I)$. Basta il rango.
> 4. Tutti regolari ⇒ sì. Base di ogni autospazio → colonne di $S$; autovalori nello stesso ordine in $D$.
> 5. Controllo: $AS=SD$ (più comodo di $S^{-1}AS$).

---

## Parte A — Esempi della lezione

### A1. Triangolare con autovalori distinti (Es. 1, pp. 7–8)
$A=\begin{bmatrix}2&1&1\\0&3&0\\0&0&-1\end{bmatrix}$: triangolare ⇒ autovalori $2,3,-1$, reali e distinti ⇒ **diagonalizzabile su $\mathbb R$** (Corollario). Nessun rango da calcolare.
Con gli autospazi della parte 1: $S=\begin{bmatrix}1&1&-1\\0&1&0\\0&0&3\end{bmatrix}$, $D=\mathrm{diag}(2,3,-1)$.

### A2. Rotazione di $90°$ (Es. 2, pp. 8–10)
$A=\begin{bmatrix}0&-1\\1&0\end{bmatrix}$, $p_A=\lambda^2+1$, radici $\pm i$.
- Su $\mathbb R$: nessun autovalore reale ⇒ **non** diagonalizzabile su $\mathbb R$ (Teorema 1a). Geometricamente nessuna direzione resta fissa.
- Su $\mathbb C$: due autovalori distinti ⇒ diagonalizzabile (Corollario I).

### A3. Autovalore doppio regolare (Es. 3, pp. 10–14, 30–33)
$A=\begin{bmatrix}3&0&-2\\1&1&-1\\1&0&0\end{bmatrix}$, $p_A=(2-\lambda)(1-\lambda)^2$.
- $\lambda=2$ semplice ⇒ regolare.
- $\lambda=1$: $A-I=\begin{bmatrix}2&0&-2\\1&0&-1\\1&0&-1\end{bmatrix}$, colonne multiple della prima ⇒ $r=1$ ⇒ $m_g=3-1=2=m_a$ ⇒ regolare.

⇒ **Diagonalizzabile.** $W_2=\mathrm{span}\{(2,1,1)\}$, $W_1=\mathrm{span}\{(0,1,0),(1,0,1)\}$:
$$S=\begin{bmatrix}2&0&1\\1&1&0\\1&0&1\end{bmatrix},\quad D=\mathrm{diag}(2,1,1).$$
Controllo $AS=SD$: $A(2,1,1)^T=(4,2,2)^T=2(2,1,1)^T$, $A(0,1,0)^T=(0,1,0)^T$, $A(1,0,1)^T=(1,0,1)^T$ ✓

### A4. Autovalore doppio irregolare (Es. 4, pp. 14–16)
$A=\begin{bmatrix}3&1&-3\\1&2&-2\\1&1&-1\end{bmatrix}$, stesso $p_A=(2-\lambda)(1-\lambda)^2$.
$A-I\to\begin{bmatrix}1&1&-2\\0&-1&1\\0&0&0\end{bmatrix}$ ⇒ $r=2$ ⇒ $m_g(1)=1<2$ ⇒ **non diagonalizzabile**, né su $\mathbb R$ né su $\mathbb C$.

> [!note] A3 e A4 non sono simili
> Stesso polinomio caratteristico, ma A3 è simile a $\mathrm{diag}(2,1,1)$ e A4 no. Stesso $p$ **non** basta per la similitudine.

### A5. Fibonacci e formula di Binet (pp. 34–45)
$A=\begin{bmatrix}1&1\\1&0\end{bmatrix}$, $p_A=\lambda^2-\lambda-1$, $\lambda_{1,2}=\frac{1\mp\sqrt5}2$ (reali distinti ⇒ diagonalizzabile).

**$\lambda_1=\frac{1-\sqrt5}2$:** $A-\lambda_1I=\begin{bmatrix}\frac{1+\sqrt5}2&1\\1&\frac{\sqrt5-1}2\end{bmatrix}$ → equazione $x+\frac{\sqrt5-1}2y=0$; con $y=\frac{\sqrt5+1}2$ si ha $x=-1$ (usa $\frac{\sqrt5-1}2\cdot\frac{\sqrt5+1}2=1$).
**$\lambda_2=\frac{1+\sqrt5}2$:** equazione $x-\frac{\sqrt5+1}2y=0$; $y=1$ ⇒ $x=\frac{\sqrt5+1}2$.

$$S=\begin{bmatrix}-1&\lambda_2\\\lambda_2&1\end{bmatrix},\quad\det S=-1-\lambda_2^2=-\tfrac{5+\sqrt5}2,\quad S^{-1}=\frac1{\sqrt5}\begin{bmatrix}\lambda_1&1\\1&-\lambda_1\end{bmatrix}.$$
Prodotto ($\lambda_1\lambda_2=-1$):
$$A^k=\frac1{\sqrt5}\begin{bmatrix}\lambda_2^{k+1}-\lambda_1^{k+1}&\lambda_2^k-\lambda_1^k\\\lambda_2^k-\lambda_1^k&\lambda_2^{k-1}-\lambda_1^{k-1}\end{bmatrix}\ \Rightarrow\ F_k=(A^{k-1})_{11}=\frac{\lambda_2^k-\lambda_1^k}{\sqrt5}.$$
Prova: $k=10$: $\varphi^{10}/\sqrt5\approx55{,}004$ ⇒ $F_{10}=55$ ✓.

### A6. Autovalori a occhio con tr e det (p. 49)
$A=\begin{bmatrix}4&2\\-1&1\end{bmatrix}$: tr $=5$, det $=4+2=6$ ⇒ due numeri con somma 5 e prodotto 6: $\lambda=2,3$. Infatti $p_A=\lambda^2-5\lambda+6$.

### A7. Sistema di EDO (pp. 61–64)
$y_1'=y_1-y_2$, $y_2'=4y_1+y_2$, $y_1(0)=1$, $y_2(0)=0$.
$A=\begin{bmatrix}1&-1\\4&1\end{bmatrix}$: tr $=2$, det $=5$ ⇒ $p_A=\lambda^2-2\lambda+5$, $\lambda=1\pm2i$.
$S=\begin{bmatrix}i&-i\\2&2\end{bmatrix}$, $S^{-1}=\begin{bmatrix}-i/2&1/4\\i/2&1/4\end{bmatrix}$, $D=\mathrm{diag}(1+2i,1-2i)$.
$$e^{tA}=S\,\mathrm{diag}\big(e^{(1+2i)t},e^{(1-2i)t}\big)S^{-1}=\begin{bmatrix}e^t\cos2t&-\tfrac12e^t\sin2t\\2e^t\sin2t&e^t\cos2t\end{bmatrix}$$
(Eulero: $e^{2it}+e^{-2it}=2\cos2t$, $e^{2it}-e^{-2it}=2i\sin2t$.)
$$\underline y(t)=e^{tA}\begin{bmatrix}1\\0\end{bmatrix}=\begin{bmatrix}e^t\cos2t\\2e^t\sin2t\end{bmatrix}.$$
Verifica: $y_1'=e^t\cos2t-2e^t\sin2t=y_1-y_2$ ✓.

---

## Parte B — Esercizi extra (tipo esame)

**B1.** Per quali $k\in\mathbb R$ è diagonalizzabile $A_k=\begin{bmatrix}1&k&0\\0&1&0\\0&0&2\end{bmatrix}$?

> [!success]- Soluzione
> Triangolare: $\lambda=1$ ($m_a=2$), $\lambda=2$ (semplice). $A_k-I=\begin{bmatrix}0&k&0\\0&0&0\\0&0&1\end{bmatrix}$: rango $2$ se $k\neq0$, $1$ se $k=0$.
> $m_g(1)=3-r$ ⇒ regolare solo per $k=0$. **Diagonalizzabile $\iff k=0$** (e allora $A_0$ è già diagonale).

**B2.** Per quali $k$ è diagonalizzabile $A_k=\begin{bmatrix}k&0&0\\1&1&0\\0&0&1\end{bmatrix}$? Per $k=5$ trova $S$ e $D$.

> [!success]- Soluzione
> Triangolare inferiore: autovalori $k,1,1$.
> $A_k-I=\begin{bmatrix}k-1&0&0\\1&0&0\\0&0&0\end{bmatrix}$ ha rango $1$ per ogni $k$ ⇒ $m_g(1)=2$.
> - $k\neq1$: $m_a(1)=2=m_g$, e $\lambda=k$ è semplice ⇒ **diagonalizzabile**.
> - $k=1$: $m_a(1)=3>m_g=2$ ⇒ **non** diagonalizzabile.
>
> $k=5$: $W_1=\mathrm{span}\{(0,1,0),(0,0,1)\}$; $A-5I=\begin{bmatrix}0&0&0\\1&-4&0\\0&0&-4\end{bmatrix}$ ⇒ $z=0$, $x=4y$ ⇒ $W_5=\mathrm{span}\{(4,1,0)\}$.
> $S=\begin{bmatrix}4&0&0\\1&1&0\\0&0&1\end{bmatrix}$, $D=\mathrm{diag}(5,1,1)$.

**B3.** Calcola $A^n$ per $A=\begin{bmatrix}2&1\\1&2\end{bmatrix}$.

> [!success]- Soluzione
> tr $=4$, det $=3$ ⇒ $\lambda=1,3$. $W_1=\mathrm{span}\{(1,-1)\}$, $W_3=\mathrm{span}\{(1,1)\}$.
> $S=\begin{bmatrix}1&1\\-1&1\end{bmatrix}$, $D=\mathrm{diag}(1,3)$, $S^{-1}=\tfrac12\begin{bmatrix}1&-1\\1&1\end{bmatrix}$.
> $$A^n=S\,\mathrm{diag}(1,3^n)\,S^{-1}=\frac12\begin{bmatrix}3^n+1&3^n-1\\3^n-1&3^n+1\end{bmatrix}.$$
> Prova $n=1$: $\tfrac12\begin{bmatrix}4&2\\2&4\end{bmatrix}=A$ ✓.

**B4.** $A=\begin{bmatrix}1&1\\0&1\end{bmatrix}$ e $I_2$ sono simili?

> [!success]- Soluzione
> Stesso $p=(1-\lambda)^2$, ma **no**: $S^{-1}I_2S=I_2$ per ogni $S$, quindi l'unica matrice simile a $I_2$ è $I_2$. (Oppure: $A$ non è diagonalizzabile, $m_g(1)=1$, e $I_2$ sì.)

**B5.** $A=\begin{bmatrix}1&2\\3&4\end{bmatrix}$ e $B=\begin{bmatrix}1&0\\0&4\end{bmatrix}$ sono simili?

> [!success]- Soluzione
> tr $A=5$ = tr $B$, ma $\det A=-2\neq4=\det B$ ⇒ polinomi caratteristici diversi ⇒ **non** simili (Teorema 2).

**B6.** Risolvi $y_1'=y_2$, $y_2'=-2y_1+3y_2$ con $\underline y(0)=(1,0)$.

> [!success]- Soluzione
> $A=\begin{bmatrix}0&1\\-2&3\end{bmatrix}$: tr $=3$, det $=2$ ⇒ $\lambda=1,2$. $W_1=\mathrm{span}\{(1,1)\}$, $W_2=\mathrm{span}\{(1,2)\}$.
> $S=\begin{bmatrix}1&1\\1&2\end{bmatrix}$, $S^{-1}=\begin{bmatrix}2&-1\\-1&1\end{bmatrix}$, $S^{-1}\underline y_0=(2,-1)$.
> $$\underline y(t)=S\begin{bmatrix}2e^t\\-e^{2t}\end{bmatrix}=\begin{bmatrix}2e^t-e^{2t}\\2e^t-2e^{2t}\end{bmatrix}.$$
> Verifica: $y_1'=2e^t-2e^{2t}=y_2$ ✓; $y_2'=2e^t-4e^{2t}=-2y_1+3y_2$ ✓; $\underline y(0)=(1,0)$ ✓.

---

## Esercizi assegnati dal docente (p. 46)
ALG (Mauri–Schlesinger): 6.1, 6.3, 6.4 · 6.5, 6.6, 6.7 · 6.8, 6.13, 6.14, 6.15, 6.17, 6.18, 6.24.
