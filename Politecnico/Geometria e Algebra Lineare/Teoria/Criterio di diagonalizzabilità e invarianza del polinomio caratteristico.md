---
tags:
  - geometria-algebra-lineare
  - diagonalizzazione
  - polinomio-caratteristico
  - similitudine
---
# Criterio di diagonalizzabilità e invarianza del polinomio caratteristico

Fonte: Lezione 10, parte 2 (PDF "Diagonalizzazione (continuata)", 63 pp., numerate a mano 2–64). Testo: ALG (Mauri–Schlesinger) cap. 6.
Prerequisito: [[Autovalori, autovettori, autospazi e molteplicità]] (parte 1).
Esercizi: [[Diagonalizzazione — Esercizi svolti]] · HTML: [[Lezione 10 parte 2 — Criterio di diagonalizzabilità.html|Lezione 10 parte 2 (interattiva)]]

## 1. Richiamo: regolare e irregolare (pp. 2–4)

Per ogni autovalore $\lambda_0$: $\;1\le m_g(\lambda_0)\le m_a(\lambda_0)$.
- **Regolare**: $m_g(\lambda_0)=m_a(\lambda_0)$. **Irregolare**: $m_g(\lambda_0)<m_a(\lambda_0)$.
- Ogni autovalore **semplice** ($m_a=1$) è regolare. Solo quelli **multipli** possono essere irregolari.

## 2. Il criterio (pp. 4–7)

> [!important] Teorema 1 (criterio di diagonalizzabilità su $\mathbb C$)
> Una matrice quadrata $A$ è diagonalizzabile $\iff$ **ogni autovalore di $A$ è regolare**.

> [!important] Teorema 1a (criterio su $\mathbb R$)
> $A$ a elementi reali è diagonalizzabile su $\mathbb R$ $\iff$ ogni autovalore di $A$ è **regolare** e **reale**.

> [!important] Corollario
> 1. $A$ di ordine $n$ con $n$ autovalori distinti ⇒ diagonalizzabile (su $\mathbb C$).
> 2. $A$ reale di ordine $n$ con $n$ autovalori distinti **reali** ⇒ diagonalizzabile su $\mathbb R$.

*Perché.* $p_A$ ha grado $n$: con $n$ radici distinte sono tutte semplici, quindi tutte regolari ⇒ Teorema 1 / 1a.

> [!warning] Il Corollario è solo sufficiente
> $I_3$ ha un solo autovalore ($1$, triplo) ed è già diagonale. Autovalori ripetuti **non** implicano "non diagonalizzabile": bisogna controllare $m_g$.

### Procedura d'esame "è diagonalizzabile?"
1. $p_A(\lambda)=\det(A-\lambda I)$ → autovalori con $m_a$.
2. Se serve $\mathbb R$: ci sono radici non reali? ⇒ **no** su $\mathbb R$.
3. Autovalori semplici: regolari gratis, **non** vanno controllati.
4. Per ogni autovalore multiplo: $m_g=n-r(A-\lambda I)$. Basta il **rango**, non serve la base del nucleo.
5. Tutti regolari ⇒ sì; anche uno solo irregolare ⇒ no.

### Esempi del PDF

| Esempio | $p_A$ | Controllo | Esito |
|---|---|---|---|
| 1. $\begin{bmatrix}2&1&1\\0&3&0\\0&0&-1\end{bmatrix}$ | $(2-\lambda)(3-\lambda)(-1-\lambda)$ | 3 autovalori reali distinti | diag. su $\mathbb R$ (Corollario) |
| 2. rotazione $90°$: $\begin{bmatrix}0&-1\\1&0\end{bmatrix}$ | $\lambda^2+1$ | radici $\pm i$, distinte | diag. su $\mathbb C$, **non** su $\mathbb R$ |
| 3. $\begin{bmatrix}3&0&-2\\1&1&-1\\1&0&0\end{bmatrix}$ | $(2-\lambda)(1-\lambda)^2$ | $r(A-I)=1$ ⇒ $m_g(1)=2$ | diagonalizzabile |
| 4. $\begin{bmatrix}3&1&-3\\1&2&-2\\1&1&-1\end{bmatrix}$ | $(2-\lambda)(1-\lambda)^2$ | $r(A-I)=2$ ⇒ $m_g(1)=1$ | **non** diagonalizzabile |

Es. 2 (geometria): una rotazione di $90°$ non lascia fissa nessuna direzione ⇒ nessun autovettore reale.
Es. 3: in $A-I=\begin{bmatrix}2&0&-2\\1&0&-1\\1&0&-1\end{bmatrix}$ le colonne sono tutte multiple della prima ⇒ rango 1 senza fare Gauss.

## 3. Come trovare $S$ e $D$ (pp. 17–19, 30–33)

Data $A$ diagonalizzabile, i due problemi sono **equivalenti**:
- (a) trovare una base $\mathcal B$ di $\mathbb K^n$ fatta di autovettori;
- (b) trovare $S$ invertibile e $D$ diagonale con $A=SDS^{-1}$ (cioè $S^{-1}AS=D$).

Colonne di $S$ = vettori di $\mathcal B$; $d_{jj}$ = autovalore della colonna $j$. La soluzione **non è mai unica** (ordine delle colonne, multipli scalari, altre basi degli autospazi).

> [!tip] Ricetta
> Base di **ogni** autospazio → mettile tutte in colonna in $S$ → in $D$ gli autovalori nello stesso ordine (ripetuti $m_g$ volte).

**Esempio (Es. 3).** $W_2=\mathrm{span}\{(2,1,1)\}$, $W_1=\mathrm{span}\{(0,1,0),(1,0,1)\}$:
$$S=\begin{bmatrix}2&0&1\\1&1&0\\1&0&1\end{bmatrix},\qquad D=\mathrm{diag}(2,1,1),\qquad S^{-1}AS=D .$$

## 4. Perché il criterio funziona (pp. 19–30)

Notazione: $\lambda_1,\dots,\lambda_k$ autovalori **distinti**, $W_{\lambda_j}=\ker(A-\lambda_jI)$.

> [!important] Lemma
> Se $\underline u_1\in W_{\lambda_1},\dots,\underline u_k\in W_{\lambda_k}$ e $\underline u_1+\dots+\underline u_k=\underline 0$, allora $\underline u_1=\dots=\underline u_k=\underline 0$.
> (In altre parole: gli autospazi sono in **somma diretta**, e autovettori di autovalori distinti sono **indipendenti**.)

*Dim.* Fisso $i_0$. Applico $(A-\lambda_jI)$ a $\sum_i\underline u_i=\underline 0$; poiché $A\underline u_i=\lambda_i\underline u_i$:
$$\sum_i(\lambda_i-\lambda_j)\underline u_i=\underline 0\qquad(\text{sparisce }\underline u_j).$$
Ripeto per **ogni** $j\neq i_0$:
$$\sum_i\Big(\prod_{j\neq i_0}(\lambda_i-\lambda_j)\Big)\underline u_i=\underline 0 .$$
Per $i\neq i_0$ il prodotto contiene il fattore $(\lambda_i-\lambda_i)=0$; resta solo $\prod_{j\neq i_0}(\lambda_{i_0}-\lambda_j)\,\underline u_{i_0}=\underline 0$, con coefficiente $\neq0$ (autovalori distinti) ⇒ $\underline u_{i_0}=\underline 0$. $\blacksquare$

**Sufficienza del Teorema 1.** Prendo una base $\mathcal B_j$ di ogni $W_{\lambda_j}$ e $\mathcal B=\mathcal B_1\cup\dots\cup\mathcal B_k$.
- *Indipendente:* una combinazione nulla si spezza in $\underline u_1+\dots+\underline u_k=\underline 0$ con $\underline u_j\in W_{\lambda_j}$; per il Lemma ogni $\underline u_j=\underline 0$, e dentro ogni $\mathcal B_j$ i coefficienti sono nulli (base).
- *Abbastanza vettori:* $|\mathcal B|=\sum_j m_g(\lambda_j)\overset{\text{regolari}}{=}\sum_j m_a(\lambda_j)=\deg p_A=n$.

⇒ $\mathcal B$ è una base di autovettori ⇒ $A$ diagonalizzabile. $\blacksquare$
(Il PDF a p. 27 scrive "$\forall j\in\{1,\dots,n\}$": è $\{1,\dots,k\}$.)

**Idea chiave:** in generale $\sum m_g\le\sum m_a=n$. Si arriva a $n$ autovettori indipendenti **solo** se in ogni autovalore $m_g=m_a$.

## 5. Applicazione: potenze e Fibonacci (pp. 34–45)

Se $A=SDS^{-1}$, allora
$$A^k=SD^kS^{-1},\qquad D^k=\mathrm{diag}(\lambda_1^k,\dots,\lambda_n^k)$$
(anche per $k<0$ se $\det D\neq0$).

**Fibonacci.** $\begin{bmatrix}F_k\\F_{k-1}\end{bmatrix}=A^{k-1}\begin{bmatrix}1\\0\end{bmatrix}$, $A=\begin{bmatrix}1&1\\1&0\end{bmatrix}$, $p_A=\lambda^2-\lambda-1$:
$$\lambda_1=\tfrac{1-\sqrt5}2,\quad\lambda_2=\tfrac{1+\sqrt5}2=\varphi .$$
Autovettori: $\underline v_1=\big(-1,\tfrac{1+\sqrt5}2\big)^T$, $\underline v_2=\big(\tfrac{1+\sqrt5}2,1\big)^T$.
$$S=\begin{bmatrix}-1&\lambda_2\\\lambda_2&1\end{bmatrix},\quad S^{-1}=\frac1{\sqrt5}\begin{bmatrix}\lambda_1&1\\1&-\lambda_1\end{bmatrix},\quad A^k=\frac1{\sqrt5}\begin{bmatrix}\lambda_2^{k+1}-\lambda_1^{k+1}&\lambda_2^k-\lambda_1^k\\\lambda_2^k-\lambda_1^k&\lambda_2^{k-1}-\lambda_1^{k-1}\end{bmatrix}$$
(si usa $\lambda_1\lambda_2=\det A=-1$). Da $F_k=(A^{k-1})_{11}$, la **formula di Binet**:
$$\boxed{F_k=\frac{\varphi^k-\left(\frac{1-\sqrt5}2\right)^k}{\sqrt5}=\frac{(1+\sqrt5)^k-(1-\sqrt5)^k}{2^k\sqrt5}}$$
Siccome $|\lambda_1|<1$, $F_k$ è l'intero più vicino a $\varphi^k/\sqrt5$: $\varphi^{10}/\sqrt5\approx55{,}0036\Rightarrow F_{10}=55$; $\varphi^{15}/\sqrt5\approx609{,}9997\Rightarrow F_{15}=610$.

## 6. Traccia, determinante e autovalori (pp. 47–49)

**Traccia:** $\operatorname{tr}A=\sum_i a_{ii}$.

> [!important] Teorema (det, tr, autovalori)
> Se $p_A(\lambda)=(\lambda_1-\lambda)\cdots(\lambda_n-\lambda)$, allora
> $$\det A=\prod_i\lambda_i,\qquad\operatorname{tr}A=\sum_i\lambda_i .$$

*Dim. (det).* $p_A(0)=\lambda_1\cdots\lambda_n$ e $p_A(0)=\det(A-0I)=\det A$. $\blacksquare$ (Nel PDF anche questo si chiama "Teorema 1": non è il criterio.)

**Caso $2\times2$:** $p_A(\lambda)=\lambda^2-(\operatorname{tr}A)\lambda+\det A$. Esempio $\begin{bmatrix}4&2\\-1&1\end{bmatrix}$: tr $=5$, det $=6$ ⇒ $\lambda=2,3$ a occhio.

## 7. Invarianza per similitudine (pp. 50–55)

> [!important] Teorema 2
> Se $A$ e $B$ sono simili, allora $p_A(\lambda)=p_B(\lambda)$.

*Dim.* $B=S^{-1}AS$ e $\lambda I=S^{-1}(\lambda I)S$, quindi
$$p_B(\lambda)=\det\big(S^{-1}AS-S^{-1}\lambda IS\big)=\det\big(S^{-1}(A-\lambda I)S\big)\overset{\text{Binet}}=\det(A-\lambda I)=p_A(\lambda).\ \blacksquare$$

**Conseguenze.**
- **(A)** Matrici simili hanno gli stessi autovalori con le stesse $m_a$ (e stessi tr, det). Se $B=S^{-1}AS$ e $B\underline v=\lambda\underline v$, allora $A(S\underline v)=SB\underline v=\lambda(S\underline v)$: gli autovettori si trasportano con $S$.
- **(B)** Le matrici di uno stesso endomorfismo $L$ in basi diverse sono simili ⇒ hanno lo stesso $p$. Quindi ha senso il **polinomio caratteristico di $L$**, indipendente dalla base.
- **(C)** **Il viceversa è falso**: stesso $p_A$ non implica simili. Es. 3 ed Es. 4 hanno lo stesso $p$, ma una è diagonalizzabile e l'altra no (e una matrice simile a una diagonalizzabile è diagonalizzabile). Anche $\begin{bmatrix}1&1\\0&1\end{bmatrix}$ e $I_2$: stesso $p$, ma $I_2$ è simile solo a se stessa.

> [!tip] Test di non-similitudine
> Se cambiano $p_A$, tr, det, rango o $m_g$ di qualche autovalore ⇒ **non** simili. Se due matrici sono entrambe diagonalizzabili con lo stesso $p$ ⇒ simili (sono simili alla stessa $D$).

## 8. Matrice esponenziale ed EDO lineari (pp. 55–64)

$$e^{A}:=\sum_{k=0}^{\infty}\frac{A^k}{k!},\qquad e^{tA}=\sum_{k=0}^{\infty}\frac{t^k}{k!}A^k,\qquad\frac{d}{dt}e^{tA}=Ae^{tA}.$$
Il sistema $\underline y'(t)=A\underline y(t)$, $\underline y(0)=\underline y_0$ ha come unica soluzione $\underline y(t)=e^{tA}\underline y_0$.
Se $A=SDS^{-1}$:
$$e^{tA}=S\,\mathrm{diag}(e^{t\lambda_1},\dots,e^{t\lambda_n})\,S^{-1}.$$

**Esempio.** $y_1'=y_1-y_2$, $y_2'=4y_1+y_2$, $\underline y(0)=(1,0)$. $A=\begin{bmatrix}1&-1\\4&1\end{bmatrix}$, autovalori $1\pm2i$,
$$S=\begin{bmatrix}i&-i\\2&2\end{bmatrix},\quad e^{tA}=\begin{bmatrix}e^t\cos2t&-\tfrac12e^t\sin2t\\2e^t\sin2t&e^t\cos2t\end{bmatrix}\Rightarrow\ y_1=e^t\cos2t,\ \ y_2=2e^t\sin2t .$$
(Il PDF a p. 63 scrive $e^{(1-2it)}$: è $e^{(1-2i)t}$.)

## 9. Esercizi proposti (p. 46)
ALG (Mauri–Schlesinger): §6.1 es. 6.1, 6.3, 6.4 · §6.2 es. 6.5, 6.6, 6.7 · §6.3 es. 6.8, 6.13, 6.14, 6.15, 6.17, 6.18, 6.24.

> [!bug] Refusi nel PDF
> p. 27 indice $j\in\{1,\dots,n\}$ → $\{1,\dots,k\}$ · p. 47 "Teorema 1" duplicato (det/tr) · p. 53 rimando "Lezione ]" senza numero · p. 63 $e^{(1-2it)}$ → $e^{(1-2i)t}$. Tutti i calcoli sono corretti (verificati).
