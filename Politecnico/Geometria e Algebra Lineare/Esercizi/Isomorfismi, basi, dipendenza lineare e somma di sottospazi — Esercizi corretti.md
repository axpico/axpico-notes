---
tags:
  - geometria-algebra-lineare
  - esercizi
  - isomorfismo-canonico
  - indipendenza-lineare
  - basi
  - somma-diretta
---
## Collegamenti alla teoria

- [[Spazi vettoriali e sottospazi|Spazi vettoriali e sottospazi]]
- [[Combinazioni lineari e sottospazio generato|Combinazioni lineari e sottospazio generato]]
- [[Basi, dimensione e coordinate|Basi, dimensione e coordinate]]
- [[Applicazioni lineari, nucleo e immagine|Applicazioni lineari, nucleo e immagine]]

> Pagina ottenuta correggendo e completando gli appunti manoscritti (Excalidraw, 14/10/2026). Dove l'originale conteneva una svista o una scrittura ambigua, è segnalato in **Nota di correzione**.

---

## 0. Richiami teorici

### Applicazione lineare

Siano $V,W$ spazi vettoriali su $\mathbb R$. Una funzione $f:V\to W$ è **lineare** se

$$
\forall u,v\in V:\; f(u+v)=f(u)+f(v),\qquad \forall u\in V,\ \forall\lambda\in\mathbb R:\; f(\lambda u)=\lambda f(u).
$$

(additività + omogeneità). Equivalente: $f(\lambda u+\mu v)=\lambda f(u)+\mu f(v)$.

### Spazi isomorfi a $\mathbb R^n$

Se $\dim V=n$, allora $V\cong\mathbb R^n$. Esempi canonici di spazi di dimensione $n$:

| Spazio | Dimensione |
|---|---|
| $\mathbb R^n$ | $n$ |
| $M_{p,q}(\mathbb R)$ | $pq$ (se $pq=n$, è isomorfo a $\mathbb R^n$) |
| $\mathbb R_{n-1}[t]$ (polinomi di grado $\le n-1$) | $n$ |

### Isomorfismo canonico

Un **isomorfismo** è un'applicazione lineare **biiettiva**; $\varphi\in\operatorname{Iso}(V,W)$ significa $V\xrightarrow{\ \varphi\ }W$ lineare e invertibile, con inversa $\varphi^{-1}$ ancora lineare:

$$
\varphi\circ\varphi^{-1}=\mathrm{id}_W,\qquad \varphi^{-1}\circ\varphi=\mathrm{id}_V .
$$

Perché è utile: un isomorfismo **conserva** combinazioni lineari, indipendenza, span, dimensione. Quindi per studiare la dipendenza lineare di matrici o polinomi basta "tradurli" in vettori di $\mathbb R^n$ e lavorare con il rango.

---

## 1. Isomorfismo canonico $M_{2,3}(\mathbb R)\to\mathbb R^6$

Si "legge" la matrice per righe e si incolonnano gli elementi:

$$
\begin{bmatrix}a&b&c\\a'&b'&c'\end{bmatrix}\in M_{2,3}(\mathbb R)\ \longmapsto\ (a,b,c,a',b',c')^T\in\mathbb R^6 .
$$

È lineare (somma e prodotto per scalare agiscono entrata per entrata) e biiettiva (si ricostruisce la matrice rileggendo i 6 numeri), quindi è un isomorfismo; in particolare $\dim M_{2,3}(\mathbb R)=6$.

**Esempio diretto** (la matrice dell'appunto ha 3 righe e 2 colonne, quindi è in $M_{3,2}(\mathbb R)\cong\mathbb R^6$):

$$
\begin{bmatrix}2&5\\1&1\\3&-1\end{bmatrix}\xmapsto{\ \varphi\ }(2,5,1,1,3,-1)^T .
$$

**Esempio inverso:**

$$
(2,0,0,-1,-1,7)^T\xmapsto{\ \varphi^{-1}\ }\begin{bmatrix}2&0\\0&-1\\-1&7\end{bmatrix}.
$$

> **Nota di correzione.** L'appunto scrive $V=M_{2,3}(\mathbb R)$ ma poi usa matrici $3\times2$: lo spazio giusto è $M_{3,2}(\mathbb R)$. Il procedimento è identico; il punto essenziale è fissare una volta per tutte l'**ordine di lettura** (per righe), altrimenti $\varphi$ e $\varphi^{-1}$ non sono l'una l'inversa dell'altra.

### Polinomi

$$
p(t)=\sum_{i=0}^{3}\lambda_i t^i=\lambda_0+\lambda_1t+\lambda_2t^2+\lambda_3t^3\in\mathbb R_3[t]\ \longmapsto\ (\lambda_0,\lambda_1,\lambda_2,\lambda_3)^T\in\mathbb R^4 .
$$

Isomorfismo: $\dim\mathbb R_3[t]=4$. Con questo isomorfismo, **dipendenza lineare di polinomi = dipendenza lineare dei vettori dei coefficienti**: se $\varphi\in\operatorname{Iso}(V,W)$ e $u,v\in V$, allora $u,v$ sono dipendenti $\iff\varphi(u),\varphi(v)$ sono dipendenti.

---

## 2. Polinomi dipendenti al variare di $k$

**Testo.** Sia $k\in\mathbb R$ e siano in $\mathbb R_2[t]$

$$
P_1(t)=t^2,\qquad P_2(t)=kt-1,\qquad P_3(t)=2t^2+k-1 .
$$

Per quali $k$ sono linearmente dipendenti?

### Svolgimento 1 — direttamente dalla definizione

Cerchiamo $a,b,c$ tali che $aP_1+bP_2+cP_3=0$ (polinomio nullo):

$$
at^2+b(kt-1)+c(2t^2+k-1)=(a+2c)\,t^2+(bk)\,t+\big((k-1)c-b\big)=0 .
$$

Due polinomi sono uguali se hanno gli stessi coefficienti, quindi:

$$
\begin{cases}a+2c=0\\ bk=0\\ -b+(k-1)c=0\end{cases}
\qquad
A=\begin{bmatrix}1&0&2\\0&k&0\\0&-1&k-1\end{bmatrix}.
$$

È un sistema omogeneo quadrato $3\times3$. Per Rouché–Capelli ha $\infty^{\,3-\operatorname{rk}A}$ soluzioni:

- $\operatorname{rk}A=3$ → $\infty^0$: solo la soluzione banale → **indipendenti**;
- $\operatorname{rk}A<3$ → soluzioni non banali → **dipendenti**.

$$
\det A=1\cdot\big(k(k-1)-0\big)=k(k-1)=0\iff k=0\ \text{ o }\ k=1 .
$$

### Svolgimento 2 — con l'isomorfismo $\varphi:\mathbb R_2[t]\to\mathbb R^3$, $at^2+bt+c\mapsto(a,b,c)^T$

$$
P_1\mapsto\begin{bmatrix}1\\0\\0\end{bmatrix},\quad
P_2\mapsto\begin{bmatrix}0\\k\\-1\end{bmatrix},\quad
P_3\mapsto\begin{bmatrix}2\\0\\k-1\end{bmatrix}.
$$

Questi tre vettori, messi in colonna, danno **la stessa matrice $A$**: i polinomi sono dipendenti se e solo se $\operatorname{rk}A<3$, cioè $\det A=0$.

### Verifica diretta

- $k=0$: $P_2=-1$, $P_3=2t^2-1$ ⇒ $P_3=2P_1+P_2$ ✔
- $k=1$: $P_2=t-1$, $P_3=2t^2$ ⇒ $P_3=2P_1$ ✔

> **Risultato.** $P_1,P_2,P_3$ sono linearmente dipendenti $\iff k\in\{0,1\}$.

---

## 3. Tre matrici dipendenti in $M_2(\mathbb R)$ (caso con parametro)

**Testo.** Sia $k\in\mathbb R$ e

$$
A=\begin{bmatrix}k&0\\-2&1\end{bmatrix},\quad
B=\begin{bmatrix}k&3k\\1&k\end{bmatrix},\quad
C=\begin{bmatrix}1&2\\0&1\end{bmatrix}.
$$

Determinare i $k$ per cui $A,B,C$ sono dipendenti.

> **Nota di correzione.** Nell'appunto $A$ compare come $\begin{bmatrix}k&0\\-2&1\end{bmatrix}$ e il sistema che ne segue ($-2x+y=0$ dalla riga 2, colonna 1) è coerente con questa lettura; $B$ ha $3k$ in alto a destra (si vede dalla seconda equazione $3ky+2z=0$). Uso queste letture.

### Impostazione

$xA+yB+zC=0$, con $x,y,z\in\mathbb R$:

$$
\begin{bmatrix}kx&0\\-2x&x\end{bmatrix}+
\begin{bmatrix}ky&3ky\\y&ky\end{bmatrix}+
\begin{bmatrix}z&2z\\0&z\end{bmatrix}
=\begin{bmatrix}kx+ky+z&3ky+2z\\-2x+y&x+ky+z\end{bmatrix}=\begin{bmatrix}0&0\\0&0\end{bmatrix}.
$$

Uguagliando le quattro entrate (4 equazioni, 3 incognite):

$$
\begin{cases}kx+ky+z=0\\3ky+2z=0\\-2x+y=0\\x+ky+z=0\end{cases}
\qquad
D=\begin{bmatrix}k&k&1\\0&3k&2\\-2&1&0\\1&k&1\end{bmatrix}.
$$

Le matrici sono dipendenti $\iff$ il sistema ha soluzioni non banali $\iff\operatorname{rk}D<3$ $\iff$ **tutti i minori $3\times3$ di $D$ sono nulli**.

### Minori $3\times3$

Per Kronecker non serve calcolarli tutti: basta prenderne uno e controllare gli altri solo dove serve. I quattro minori (righe indicate) sono:

$$
M_{124}=\begin{vmatrix}k&k&1\\0&3k&2\\1&k&1\end{vmatrix}
=k(3k-2k)-k(0-2)+1(0-3k)=k^2+2k-3k=k(k-1),
$$

$$
M_{234}=\begin{vmatrix}0&3k&2\\-2&1&0\\1&k&1\end{vmatrix}
=-3k(-2-0)+2(-2k-1)=6k-4k-2=2(k-1).
$$

Servono **entrambi** nulli: $M_{124}=0\Rightarrow k\in\{0,1\}$; $M_{234}=0\Rightarrow k=1$. L'unico candidato è $k=1$.

Verifica sugli altri due minori per $k=1$:

- $M_{134}$ ha righe 1 e 4 uguali ($[1\ 1\ 1]$) ⇒ $0$.
- $M_{123}=\begin{vmatrix}1&1&1\\0&3&2\\-2&1&0\end{vmatrix}=1(0-2)-1(0+4)+1(0+6)=0$.

Tutti nulli ⇒ $\operatorname{rk}D<3$. Inoltre il minore $2\times2$ (righe 2,4; colonne 2,3) $=\begin{vmatrix}3&2\\1&1\end{vmatrix}=1\ne0$, quindi $\operatorname{rk}D=2$ e il sistema ha $\infty^{3-2}=\infty^1$ soluzioni.

### Relazione esplicita per $k=1$

Da $-2x+y=0\Rightarrow y=2x$; da $3y+2z=0\Rightarrow z=-3x$. Con $x=1$: $(x,y,z)=(1,2,-3)$.

$$
A+2B-3C=\begin{bmatrix}1&0\\-2&1\end{bmatrix}+\begin{bmatrix}2&6\\2&2\end{bmatrix}-\begin{bmatrix}3&6\\0&3\end{bmatrix}=\begin{bmatrix}0&0\\0&0\end{bmatrix}\ \checkmark
$$

> **Risultato.** $A,B,C$ sono dipendenti $\iff k=1$ (per $k\ne1$ sono indipendenti, $\operatorname{rk}D=3$).

---

## 4. Tre matrici numeriche: dipendenti o indipendenti?

**Testo.**

$$
A=\begin{bmatrix}1&2\\-1&0\end{bmatrix},\quad
B=\begin{bmatrix}1&0\\0&-1\end{bmatrix},\quad
C=\begin{bmatrix}-1&2\\-1&2\end{bmatrix}.
$$

> **Nota di correzione.** Nell'appunto l'ultima entrata di $C$ è ambigua; dalle equazioni scritte ($2z-y=0$ nell'entrata $(2,2)$) segue $C_{22}=2$.

### Svolgimento

$$
xA+yB+zC=\begin{bmatrix}x+y-z&2x+2z\\-x-z&2z-y\end{bmatrix}=0
\ \Longrightarrow\
\begin{cases}x+y-z=0\\2x+2z=0\\-x-z=0\\2z-y=0\end{cases}
$$

(la 2ª e la 3ª equazione sono proporzionali). Da $x=-z$ e $y=2z$ la 1ª diventa $-z+2z-z=0$ ✔ e la 4ª $2z-2z=0$ ✔. Quindi le soluzioni sono

$$
(x,y,z)=t\,(-1,2,1),\quad t\in\mathbb R\qquad(\infty^1\ \text{soluzioni}).
$$

Matrice dei coefficienti $\begin{bmatrix}1&1&-1\\2&0&2\\-1&0&-1\\0&-1&2\end{bmatrix}$ ha rango $2<3$.

**Verifica:** $-A+2B+C=\begin{bmatrix}-1&-2\\1&0\end{bmatrix}+\begin{bmatrix}2&0\\0&-2\end{bmatrix}+\begin{bmatrix}-1&2\\-1&2\end{bmatrix}=0$ ✔

> **Risultato.** $A,B,C$ sono **linearmente dipendenti**: $C=A-2B$.

---

## 5. Insiemi generatori, indipendenza, basi

Sia $V$ uno spazio vettoriale e $X\subseteq V$.

- $X$ è un **insieme generatore** di $V$ se ogni $v\in V$ è combinazione lineare di elementi di $X$: $\exists\,x_1,\dots,x_p\in X$, $\lambda_i\in\mathbb R$ con $v=\sum_{i=1}^p\lambda_ix_i$. Si scrive $V=\langle X\rangle=\mathcal L(X)$.
- $X$ è **indipendente** se i vettori di $X$ sono (finiti sottoinsiemi) linearmente indipendenti.
- $X$ è una **base** di $V$ se è generatore **e** indipendente.

**Esempio in $\mathbb R^2$.** $u_1=\begin{bmatrix}1\\0\end{bmatrix}$, $u_2=\begin{bmatrix}0\\1\end{bmatrix}$: ogni $(x,y)^T=x\,u_1+y\,u_2$, e $u_1,u_2$ sono indipendenti ⇒ $X=\{u_1,u_2\}$ è la **base canonica**.

Conseguenza: se $X$ è una base, ogni vettore si scrive in modo **unico** come combinazione lineare di $X$ (coordinate), e $\dim V=|X|$.

---

## 6. Base di $V=\{(x,\,y,\,x+y,\,x-y)\in\mathbb R^4\mid x,y\in\mathbb R\}$

### Passo 1 — Scomporre il generico vettore

$$
v=\begin{bmatrix}x\\y\\x+y\\x-y\end{bmatrix}
=x\begin{bmatrix}1\\0\\1\\1\end{bmatrix}+y\begin{bmatrix}0\\1\\1\\-1\end{bmatrix}=x\,v_1+y\,v_2 .
$$

Quindi $V=\langle v_1,v_2\rangle$ e $X=\{v_1,v_2\}$ è un **insieme generatore**. ($V$ è un sottospazio: è lo span di due vettori.)

### Passo 2 — Indipendenza

$$
A=\begin{bmatrix}1&0\\0&1\\1&1\\1&-1\end{bmatrix},\qquad
\begin{vmatrix}1&0\\0&1\end{vmatrix}=1\ne0
$$

C'è un minore di ordine 2 non nullo, e non esistono minori di ordine $>2$ (ci sono solo 2 colonne) ⇒ $\operatorname{rk}A=2$ ⇒ $v_1,v_2$ indipendenti.

> **Risultato.** $\{v_1,v_2\}$ è una **base** di $V$ e $\dim V=2$.

---

## 7. Sottospazi $U,V\subseteq\mathbb R^4$: generatori, dimensione, somma

**Testo.**

$$
U=\left\{x\in\mathbb R^4\ \middle|\ x_1-x_3=0,\ x_2+x_4=0\right\},\qquad
V=\left\{x\in\mathbb R^4\ \middle|\ x_1+x_4=0,\ x_2-x_4=0\right\}.
$$

(i) Trovare un insieme generatore di $U$ e di $V$.
(ii) Calcolare $\dim U$ e $\dim V$.
(iii) Stabilire se $U+V$ è somma diretta, dare una rappresentazione cartesiana e determinarne una base.

### (i) Generatori

**$U$:** $x_1=x_3,\ x_2=-x_4$, con $x_3,x_4$ liberi.

$$
u=\begin{bmatrix}x_3\\-x_4\\x_3\\x_4\end{bmatrix}
=x_3\begin{bmatrix}1\\0\\1\\0\end{bmatrix}+x_4\begin{bmatrix}0\\-1\\0\\1\end{bmatrix}
\ \Rightarrow\ U=\Big\langle\begin{bmatrix}1\\0\\1\\0\end{bmatrix},\begin{bmatrix}0\\-1\\0\\1\end{bmatrix}\Big\rangle .
$$

**$V$:** $x_1=-x_4,\ x_2=x_4$, con $x_3,x_4$ liberi.

$$
v=\begin{bmatrix}-x_4\\x_4\\x_3\\x_4\end{bmatrix}
=x_3\begin{bmatrix}0\\0\\1\\0\end{bmatrix}+x_4\begin{bmatrix}-1\\1\\0\\1\end{bmatrix}
\ \Rightarrow\ V=\Big\langle\begin{bmatrix}0\\0\\1\\0\end{bmatrix},\begin{bmatrix}-1\\1\\0\\1\end{bmatrix}\Big\rangle .
$$

> **Nota di correzione.** Nell'appunto, dopo il calcolo per $V$, compare per errore la scritta "$U=\langle\dots\rangle$": quella è la base di **$V$**.

### (ii) Dimensioni

Ranghi delle matrici dei generatori (colonne):

$$
\begin{bmatrix}1&0\\0&-1\\1&0\\0&1\end{bmatrix}:\ \operatorname{rk}=2,\qquad
\begin{bmatrix}0&-1\\0&1\\1&0\\0&1\end{bmatrix}:\ \operatorname{rk}=2 .
$$

Generatori indipendenti ⇒ sono basi ⇒ $\dim U=2$, $\dim V=2$. Coerente con il conteggio $\dim=n-\#\text{equazioni indipendenti}=4-2=2$.

### (iii) La somma $U+V$

**Intersezione.** $x\in U\cap V$ soddisfa tutte e quattro le equazioni:

$$
\begin{cases}x_1=x_3\\x_2=-x_4\\x_1=-x_4\\x_2=x_4\end{cases}
\Rightarrow x_2=-x_4=x_4\Rightarrow x_2=x_4=0\Rightarrow x_1=0,\ x_3=0 .
$$

Quindi $U\cap V=\{0\}$ ⇒ **la somma è diretta**: $U+V=U\oplus V$.

**Dimensione** (formula di Grassmann): $\dim(U+V)=\dim U+\dim V-\dim(U\cap V)=2+2-0=4$.
Poiché $U+V\subseteq\mathbb R^4$ ha dimensione 4, si ha $U+V=\mathbb R^4$.

**Verifica con il determinante.** Matrice che ha per righe i quattro generatori:

$$
\begin{vmatrix}1&0&1&0\\0&-1&0&1\\0&0&1&0\\-1&1&0&1\end{vmatrix}.
$$

La riga 3 è $e_3$: sviluppando secondo di essa resta (a meno del segno) $\begin{vmatrix}1&0&0\\0&-1&1\\-1&1&1\end{vmatrix}=1\cdot(-1-1)=-2\ne0$ ⇒ i 4 vettori sono indipendenti ✔.

**Rappresentazione cartesiana.** $U+V=\mathbb R^4$, quindi **nessuna equazione** (la rappresentazione cartesiana è vuota: ogni $(x_1,\dots,x_4)$ appartiene a $U+V$).

**Base.** Una base di $U\oplus V$ è l'unione delle basi:

$$
\mathcal B=\left\{\begin{bmatrix}1\\0\\1\\0\end{bmatrix},\begin{bmatrix}0\\-1\\0\\1\end{bmatrix},\begin{bmatrix}0\\0\\1\\0\end{bmatrix},\begin{bmatrix}-1\\1\\0\\1\end{bmatrix}\right\}
$$

(oppure, equivalentemente, la base canonica di $\mathbb R^4$).

> **Risultato.** $\dim U=\dim V=2$; $U\cap V=\{0\}$; $U+V=U\oplus V=\mathbb R^4$, con base $\mathcal B$.

---

## Riepilogo dei metodi

| Problema | Strumento |
|---|---|
| Vettori/polinomi/matrici dipendenti? | isomorfismo con $\mathbb R^n$ → rango della matrice delle coordinate |
| Dipendenza con parametro $k$ | $\det=0$ (quadrata) oppure tutti i minori di ordine massimo nulli (Kronecker) |
| Base di $\{\text{vettori con formula}\}$ | scomporre in $\sum(\text{parametro})\cdot(\text{vettore fisso})$, poi rango |
| Base di sottospazio da equazioni | parametri liberi → generatori; rango → indipendenza |
| $U+V$ diretta? | $U\cap V=\{0\}$ $\iff\dim(U+V)=\dim U+\dim V$ |
