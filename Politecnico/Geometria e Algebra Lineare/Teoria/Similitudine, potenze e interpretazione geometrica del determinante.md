---
tags:
  - geometria-algebra-lineare
  - determinante
  - matrici-simili
  - ipervolume
---
# Similitudine, potenze e interpretazione geometrica del determinante

Fonte: Lezione 9, parte 3 (pp. 14–43). Esercizi assegnati: ALG §5.4, es. 5.18, 5.23, 5.27.
Prerequisito: [[Applicazioni dei determinanti — Binet, inversa, Cramer, Kronecker]].

## 1. Potenze di una matrice quadrata

**Def.** Per $A$ quadrata e $n\in\mathbb N_0$:
$$A^0:=I,\qquad A^n:=\underbrace{AA\cdots A}_{n\text{ volte}}\ (n>0).$$
Se $A$ è invertibile: $A^{-n}:=(A^{-1})^n=\underbrace{A^{-1}\cdots A^{-1}}_{n\text{ volte}}$.

Valgono $A^nA^m=A^mA^n=A^{n+m}$ e $(A^n)^m=A^{nm}$. Per Binet:
$$\boxed{\det(A^n)=(\det A)^n}$$

> [!warning]
> In generale $(AB)^n\neq A^nB^n$ (il prodotto non è commutativo).

## 2. Matrici simili

**Def.** $A,B$ di ordine $n$ sono **simili** se $\exists S$ invertibile di ordine $n$ con
$$B=S^{-1}AS .$$

**Proprietà (è una relazione di equivalenza).**
1. **Simmetrica.** $B=S^{-1}AS\Rightarrow A=SBS^{-1}=S_1^{-1}BS_1$ con $S_1:=S^{-1}$.
2. **Riflessiva.** $A=I^{-1}AI$ ($S=I$).
3. **Transitiva.** $B=S^{-1}AS$, $C=S_1^{-1}BS_1\Rightarrow C=S_1^{-1}S^{-1}ASS_1=(SS_1)^{-1}A(SS_1)$, con $S_2:=SS_1$ invertibile.

> [!important] Teorema 4 (determinante di matrici simili)
> Se $A$ e $B$ sono simili, $\det A=\det B$.

*Dim.* $B=S^{-1}AS$; per Binet $\det B=\det(S^{-1})\det A\det S=\frac1{\det S}\det A\det S=\det A$. $\blacksquare$

**Osservazione (similitudine e potenze).** Se $B=S^{-1}AS$ allora
$$B^n=S^{-1}A^nS\quad\forall n\in\mathbb N_0,\qquad B^{-1}=S^{-1}A^{-1}S\ \ (A\ \text{invertibile}).$$
*Dim.* Induzione: per $n=0$ è $I=I$; se vale per $n$,
$B^{n+1}=BB^n=(S^{-1}AS)(S^{-1}A^nS)=S^{-1}A(SS^{-1})A^nS=S^{-1}A^{n+1}S$.
Inversa: $B^{-1}=(S^{-1}AS)^{-1}=S^{-1}A^{-1}(S^{-1})^{-1}=S^{-1}A^{-1}S$. $\blacksquare$

Utilità: se $A$ è simile a una matrice "semplice" (es. diagonale), le sue potenze si calcolano facilmente (diagonalizzazione, prossime lezioni).

### Esempio: Fibonacci

Le potenze descrivono processi in cui la stessa azione si ripete. $F_0=0$, $F_1=1$, $F_{k+1}=F_k+F_{k-1}$.

Con $\underline u_k:=\begin{bmatrix}F_k\\F_{k-1}\end{bmatrix}$:
$$\underline u_{k+1}=\begin{bmatrix}F_k+F_{k-1}\\F_k\end{bmatrix}=\begin{bmatrix}1&1\\1&0\end{bmatrix}\begin{bmatrix}F_k\\F_{k-1}\end{bmatrix}=A\underline u_k,\qquad A:=\begin{bmatrix}1&1\\1&0\end{bmatrix}.$$
Quindi, partendo da $\underline u_1=\begin{bmatrix}1\\0\end{bmatrix}$:
$$\boxed{\begin{bmatrix}F_k\\F_{k-1}\end{bmatrix}=A^{k-1}\begin{bmatrix}1\\0\end{bmatrix}}$$
Una formula esplicita per $A^{k-1}$ (e quindi per $F_k$) arriverà con la diagonalizzazione.

## 3. Interpretazione geometrica: area ($n=2$)

Due vettori $\vec u=(u_1,u_2)$, $\vec v=(v_1,v_2)$ **linearmente indipendenti** (non nulli e non collineari) formano un parallelogramma $\Pi$.

**Orientamento.** Si fissa il verso positivo da $Ox$ a $Oy$ (antiorario nel riferimento standard).

> [!important] Proposizione
> Se il raggio di $\vec v$ si ottiene ruotando quello di $\vec u$ in senso **antiorario**:
> $$\det[\vec u|\vec v]=\begin{vmatrix}u_1&v_1\\u_2&v_2\end{vmatrix}=\operatorname{area}(\Pi).$$
> Se la rotazione è **oraria**: $\det[\vec u|\vec v]=-\operatorname{area}(\Pi)$ (basta scambiare $\vec u$ e $\vec v$).

*Dim (antiorario).* Sia $\vec u':=\vec u-\lambda\vec v$ con $\lambda$ scelto in modo che $\vec u'\parallel Ox$ (cioè $u_2'=0$). Il parallelogramma $\Pi'$ di $\vec u',\vec v$ ha la stessa area di $\Pi$ (stessa base $\vec v$, stessa altezza: si "fa scivolare" il lato $\vec u$ parallelamente a $\vec v$), e la sua area è base $u_1'$ per altezza $v_2$. Per la proprietà (iii) (colonne):
$$\det[\vec u|\vec v]=\det[\vec u-\lambda\vec v|\vec v]=\begin{vmatrix}u_1'&v_1\\0&v_2\end{vmatrix}=u_1'v_2=\operatorname{area}(\Pi')=\operatorname{area}(\Pi).\ \blacksquare$$

**Corollario.** Per $\vec u,\vec v$ indipendenti nel piano: $\operatorname{area}(\Pi)=\big\lvert\det[\vec u|\vec v]\big\rvert$. (Se dipendenti: area $0$ = det $0$.)

**Esempio.** Area del triangolo $A(1,2)$, $B(2,3)$, $C(3,1)$. Con $\vec u=C-A=(2,-1)$, $\vec v=B-A=(1,1)$:
$$\operatorname{area}(\triangle ABC)=\frac12\operatorname{area}(ABB'C)=\frac12\left\lvert\begin{vmatrix}2&1\\-1&1\end{vmatrix}\right\rvert=\frac12\lvert2+1\rvert=\frac32 .$$

## 4. Volume e ipervolume ($n\ge3$)

Siano $\underline v_1,\dots,\underline v_n\in\mathbb R^n$ e $\Pi$ il parallelepipedo $n$-dimensionale che formano:
$$\boxed{\det[\underline v_1|\cdots|\underline v_n]=\pm\operatorname{Vol}_n(\Pi)}$$
Il segno dipende dall'**orientamento** di $(\underline v_1,\dots,\underline v_n)$. Per $n=3$: terna **destrorsa** (regola della mano destra) $+$, **sinistrorsa** $-$.

### Determinante di un endomorfismo

**Def.** Un **endomorfismo** di $V$ è una mappa lineare $L:V\to V$. Se $\dim V<\infty$, fissata una base $\mathcal B$ e detta $A$ la matrice rappresentativa di $L$ rispetto a $\mathcal B$ (in dominio e codominio):
$$\det(L):=\det(A).$$

**Oss.** Non dipende dalla base: se $\tilde A$ rappresenta $L$ in un'altra base $\tilde{\mathcal B}$, allora $\tilde A=S^{-1}AS$ ($S$ matrice di passaggio, vedi [[Cambio di base e matrice di passaggio]]): $A$ e $\tilde A$ sono **simili**, quindi $\det\tilde A=\det A$ (Teorema 4).

### Ipervolume

- **Ipercubo** $K_n(a):=\{(x_1,\dots,x_n):0\le x_i\le a\}$: $\operatorname{Vol}_n(K_n(a)):=a^n$.
- Per $K\subset\mathbb R^n$ qualsiasi: si fissa $\varepsilon>0$ e si usa la griglia di ipercubi
$$\{\varepsilon k_i\le x_i\le\varepsilon(k_i+1),\ i=1,\dots,n\},\quad k_i\in\mathbb Z,$$
ognuno di ipervolume $\varepsilon^n$. Siano $N(\varepsilon)$ = # ipercubi **contenuti** in $K$, $M(\varepsilon)$ = # ipercubi che **intersecano** $K$. Allora $N(\varepsilon)\varepsilon^n\le\operatorname{Vol}_n(K)\le M(\varepsilon)\varepsilon^n$.

**Def.** Se $V_1:=\lim_{\varepsilon\to0}N(\varepsilon)\varepsilon^n$ e $V_2:=\lim_{\varepsilon\to0}M(\varepsilon)\varepsilon^n$ esistono finiti e **coincidono**, $\operatorname{Vol}_n(K):=V_1=V_2$ è l'**ipervolume** di $K$.

(Non ogni $K$ limitato ha ipervolume ben definito: in esempi "cattivi" $V_1\neq V_2$.)

> [!important] Teorema 5 (determinante = fattore di scala dell'ipervolume)
> Sia $L:\mathbb R^n\to\mathbb R^n$ lineare e $K\subset\mathbb R^n$ con $\operatorname{Vol}_n(K)$ ben definito. Allora
> $$\operatorname{Vol}_n\big(L(K)\big)=\lvert\det L\rvert\cdot\operatorname{Vol}_n(K).$$

*Idea della dim. (non richiesta all'esame).* Ogni ipercubo della griglia è il parallelepipedo di $\varepsilon\underline e_1,\dots,\varepsilon\underline e_n$; la sua immagine è il parallelepipedo di $\varepsilon L(\underline e_1),\dots,\varepsilon L(\underline e_n)$, di ipervolume $\lvert\det[\varepsilon L(\underline e_1)|\cdots]\rvert=\varepsilon^n\lvert\det L\rvert$. Quindi
$$N(\varepsilon)\varepsilon^n\lvert\det L\rvert\le\operatorname{Vol}_n(L(K))\le M(\varepsilon)\varepsilon^n\lvert\det L\rvert,$$
e per $\varepsilon\to0$ entrambi gli estremi tendono a $\lvert\det L\rvert\operatorname{Vol}_n(K)$. $\blacksquare$

**Esempio (ellisse).** $L(x,y)=(ax,by)$ manda il disco unitario $\mathbb D$ nell'ellisse di semiassi $a,b$:
$$\operatorname{Vol}_2(L(\mathbb D))=\left\lvert\begin{vmatrix}a&0\\0&b\end{vmatrix}\right\rvert\cdot\pi=\pi ab .$$

**Esempio (ellissoide).** $L(x,y,z)=(ax,by,cz)$ sulla palla unitaria $\mathbb B$ ($\operatorname{Vol}_3=\frac43\pi$):
$$\operatorname{Vol}_3(L(\mathbb B))=\lvert abc\rvert\cdot\frac43\pi=\frac43\pi abc .$$

```desmos-graph
left=-4; right=4; top=3; bottom=-3;
---
x^2+y^2=1
\frac{x^2}{9}+\frac{y^2}{4}=1
```

## Collegamenti
- Precedente: [[Applicazioni dei determinanti — Binet, inversa, Cramer, Kronecker]]
- [[Teorema di rappresentazione e matrice rappresentativa]] · [[Cambio di base e matrice di passaggio]] · [[Vettori geometrici liberi]]
- PDF: [[09 parte 3. Similitudine e potenze di una matrice quadrata. Ipervolumi e determinanti.pdf|Parte 3]]
