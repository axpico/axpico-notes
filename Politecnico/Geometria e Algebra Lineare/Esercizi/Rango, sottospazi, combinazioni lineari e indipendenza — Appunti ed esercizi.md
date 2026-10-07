---
tags:
  - geometria-algebra-lineare
  - esercizi
  - rango
  - kronecker
  - sottospazi
  - combinazioni-lineari
  - indipendenza-lineare
---
## Collegamenti alla teoria

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Sistemi lineari e Rouché-Capelli]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Determinante, sviluppo di Laplace e formula di Cramer.md|Determinante e Laplace]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Combinazioni lineari e sottospazio generato.md|Combinazioni lineari e sottospazio generato]]

---

## 1. Rango e teorema di Kronecker (degli orlati)

### Idea

Il **rango** $\operatorname{rk}(A)$ è l'**ordine massimo di un minore non nullo** di $A$ (un *minore* di ordine $r$ è il determinante di una sottomatrice $r\times r$, ottenuta scegliendo $r$ righe e $r$ colonne). Calcolarlo scorrendo tutti i minori è costoso; il teorema di Kronecker lo evita.

Un **orlato** di un minore $M$ (ordine $r$) è un minore di ordine $r+1$ che contiene $M$: si aggiunge **una riga e una colonna** di $A$.

> **Teorema di Kronecker (o degli orlati).** Sia $A\in M_{m,n}(\mathbb K)$ e sia $M$ un minore di ordine $r$ con $\det M\neq 0$. Se **tutti** gli orlati di $M$ hanno determinante nullo, allora $\operatorname{rk}(A)=r$.

*Perché funziona (idea di dimostrazione).* $\det M\ne0$ implica che le $r$ righe di $M$ sono indipendenti. Se ogni orlato (riga $i$ aggiunta, colonna $j$ aggiunta) ha $\det=0$ per ogni $i,j$, ogni altra riga di $A$ è combinazione delle $r$ righe scelte, quindi lo spazio delle righe ha dimensione $r$.

### Procedura

1. Trova un minore $M$ non nullo di ordine $k$ → subito $\operatorname{rk}(A)\ge k$ (nel foglio: trovato un minore $2\times2$ non nullo ⇒ rango $\ge2$).
2. Calcola gli orlati di $M$ (ce ne sono $(m-k)(n-k)$).
3. Se **uno** è non nullo, riparti da quello (ordine $k+1$). Se **tutti** sono nulli, $\operatorname{rk}(A)=k$ e ci si ferma.

### Completamento — esempio svolto

$$
A=\begin{bmatrix}2&1&0&3\\2&1&-1&0\\0&0&-1&0\end{bmatrix}
$$

Minore scelto (righe 1,2; colonne 2,3): $M=\begin{vmatrix}1&0\\1&-1\end{vmatrix}=-1\neq0\Rightarrow\operatorname{rk}A\ge2$.

Gli orlati aggiungono la riga 3 e una delle colonne rimanenti (1 o 4): sono $(3-2)(4-2)=2$.

- colonna 1: $\begin{vmatrix}2&1&0\\2&1&-1\\0&0&-1\end{vmatrix}=-1\cdot(2\cdot1-1\cdot2)=0$;
- colonna 4: $\begin{vmatrix}1&0&3\\1&-1&0\\0&-1&0\end{vmatrix}=3\cdot\begin{vmatrix}1&-1\\0&-1\end{vmatrix}=3\cdot(-1)=-3\neq0$.

Esiste un orlato non nullo, quindi $\operatorname{rk}A\ge3$; essendo $A$ di 3 righe, $\operatorname{rk}A=3$.

**Attenzione.** Un solo orlato nullo **non** basta per concludere: vanno annullati **tutti**. Qui il primo orlato dava $0$ ma il secondo no.

---

## 2. Spazi vettoriali e sottospazi

### Definizione (ripasso)

Sia $\mathbb K$ un campo (es. $\mathbb R$). Uno **spazio vettoriale** $V$ su $\mathbb K$ è un insieme di "vettori" con due operazioni

$$
+:V\times V\to V,\ (\vec u,\vec v)\mapsto\vec u+\vec v\qquad\qquad
\cdot:\mathbb K\times V\to V,\ (\alpha,\vec v)\mapsto\alpha\vec v
$$

che soddisfano gli 8 assiomi (vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]]). Gli esempi dei fogli:

| Spazio | Elementi | Note |
|---|---|---|
| $\mathbb R^n$ | colonne $(x_1,\dots,x_n)^T$ | caso modello |
| $M_{m,n}(\mathbb R)$ | matrici $m\times n$ | somma e prodotto per scalare componente per componente |
| $\mathbb R[x]$ | polinomi $P(x)=\sum_{i=0}^n a_ix^i$ a coefficienti reali | $\mathbb R_n[x]$: grado $\le n$ |

### Sottospazio

Sia $V$ uno spazio vettoriale e $H\subseteq V$. $H$ è un **sottospazio** di $V$ ($H\le V$) se è esso stesso spazio vettoriale con le operazioni indotte. Per verificarlo basta il **criterio di sottospazio**:

1. $\vec 0\in H$ (in particolare $H\ne\varnothing$);
2. **chiusura lineare**: $\forall\,\vec u,\vec v\in H,\ \forall\,\alpha,\beta\in\mathbb K:\ \alpha\vec u+\beta\vec v\in H$.

La (2) equivale alle due condizioni separate: (i) chiusura rispetto alla somma, $\vec u,\vec v\in H\Rightarrow\vec u+\vec v\in H$; (ii) chiusura rispetto al prodotto per scalare, $\alpha\in\mathbb K,\vec u\in H\Rightarrow\alpha\vec u\in H$.

> **Strategia pratica.** Per **dimostrare** che $H\le V$ verifica (1) e (2) in generale. Per **negare** basta **un controesempio**: $\vec 0\notin H$, oppure due elementi/uno scalare che fanno uscire da $H$.

### Esempio A — $H=\{(x,y,z)\in\mathbb R^3\mid x\ge0\}$: NON è sottospazio

- (1) $\vec 0=(0,0,0)$ ha $x=0\ge0$, quindi $\vec 0\in H$ ✓
- (i) somma: se $x_1,x_2\ge0$ allora $x_1+x_2\ge0$ ✓
- (ii) prodotto per scalare: ✗. Prendo $\vec v=(1,0,0)\in H$ e $\lambda=-1<0$: $\lambda\vec v=(-1,0,0)$ ha $x=-1<0$, quindi $\lambda\vec v\notin H$.

Quindi $H\not\le\mathbb R^3$. *Lezione:* contenere lo zero non basta; i semipiani (disuguaglianze) non sono mai sottospazi.

### Esempio B — la sfera $S=\{(x,y,z)\mid x^2+y^2+z^2=1\}$: NON è sottospazio

$\vec 0=(0,0,0)$ ha $0\ne1$, quindi $\vec 0\notin S\Rightarrow S\not\le\mathbb R^3$. (Nei fogli è chiamata $S^3$; in realtà la sfera "ordinaria" in $\mathbb R^3$ è $S^2$, perché ha dimensione 2 come superficie; $S^3$ è la sfera in $\mathbb R^4$. La conclusione non cambia.)

### Esempio C — $V=\left\{\begin{bmatrix}a&b\\b&a\end{bmatrix}\mid a,b\in\mathbb R\right\}\le M_2(\mathbb R)$: è sottospazio

- (1) $a=b=0$ dà la matrice nulla ✓
- (2) Siano $A=\begin{bmatrix}a&b\\b&a\end{bmatrix}$, $B=\begin{bmatrix}c&d\\d&c\end{bmatrix}$, $\alpha,\beta\in\mathbb R$:
$$
\alpha A+\beta B=\begin{bmatrix}\alpha a+\beta c&\alpha b+\beta d\\\alpha b+\beta d&\alpha a+\beta c\end{bmatrix}\in V
$$
(ha la forma $\begin{bmatrix}a'&b'\\b'&a'\end{bmatrix}$ con $a'=\alpha a+\beta c$, $b'=\alpha b+\beta d$) ✓

**Completamento:** $V=\operatorname{span}\left\{\begin{bmatrix}1&0\\0&1\end{bmatrix},\begin{bmatrix}0&1\\1&0\end{bmatrix}\right\}$, quindi $\dim V=2$.

### Esempio D — $\mathbb R_{2\mathbb N}[x]$: polinomi con soli esponenti pari $\le\mathbb R[x]$

Sono i polinomi $p(x)=\sum_i\lambda_ix^{2i}$ (solo potenze pari). Siano $p=\sum_{i=1}^n\lambda_ix^{2i}$ e $q=\sum_{j=1}^m\mu_jx^{2j}$ con $n<m$ (altrimenti si scambiano). Allora

$$
\alpha p+\beta q=\sum_{i=1}^{n}(\alpha\lambda_i+\beta\mu_i)\,x^{2i}+\sum_{j=n+1}^{m}\beta\mu_j\,x^{2j}
$$

contiene ancora solo esponenti pari ⇒ è in $\mathbb R_{2\mathbb N}[x]$. Il polinomio nullo (tutti i coefficienti 0) è nell'insieme. Quindi è sottospazio.

> **Completamento — controesempio utile.** I polinomi di grado **esattamente** $n$ non formano un sottospazio: $x^n$ e $-x^n+1$ hanno grado $n$ ma la somma vale $1$ (grado 0). Inoltre $\vec 0$ (polinomio nullo) non ha grado $n$.

---

## 3. Combinazioni lineari, span, chiusura lineare

Sia $(V,\mathbb R)$ spazio vettoriale, $\vec v_1,\dots,\vec v_n\in V$ e $\lambda_1,\dots,\lambda_n\in\mathbb R$. Il vettore

$$
\vec w=\sum_{i=1}^n\lambda_i\vec v_i=\lambda_1\vec v_1+\dots+\lambda_n\vec v_n
$$

è una **combinazione lineare** dei $\vec v_i$ con **coefficienti** $\lambda_i$.

Per $H\subseteq V$ si definisce

$$
\mathcal L(H)=\operatorname{span}(H)=\{\text{tutte le combinazioni lineari finite di elementi di }H\}
$$

detto **chiusura lineare** (o sottospazio generato) di $H$. Proprietà fondamentali:

- $\mathcal L(H)$ è **sempre** un sottospazio di $V$, ed è il **più piccolo** che contiene $H$;
- $H\le V\iff\mathcal L(H)=H$ (un sottoinsieme è un sottospazio esattamente quando contiene già tutte le sue combinazioni lineari).

L'ultima equivalenza dà un secondo metodo per verificare i sottospazi: mostrare che $H$ è lo span di qualcosa.

**Geometria in $\mathbb R^2$:** $\alpha\vec u+\beta\vec v$ è la diagonale del parallelogramma di lati $\alpha\vec u$ e $\beta\vec v$ (disegno nei fogli, con $O$ come origine).

---

## 4. Esercizio: per quale $k$ il vettore è combinazione lineare? (svolto)

**Testo.** Sia $k\in\mathbb R$, $\vec v=\begin{bmatrix}-2\\1\\k\end{bmatrix}\in\mathbb R^3$. Trovare $k$ tale che $\vec v$ si scriva come combinazione lineare di
$$
\vec v_1=\begin{bmatrix}0\\3\\-2\end{bmatrix},\qquad\vec v_2=\begin{bmatrix}-1\\2\\5\end{bmatrix}.
$$

**Impostazione.** Cerco $x_1,x_2$ tali che $x_1\vec v_1+x_2\vec v_2=\vec v$, cioè il sistema $A\vec x=\vec b$ con

$$
\left[\begin{array}{cc|c}0&-1&-2\\3&2&1\\-2&5&k\end{array}\right]
$$

(colonne = $\vec v_1,\vec v_2$; ultima colonna = $\vec v$). Per **Rouché-Capelli** il sistema ammette soluzione $\iff\operatorname{rk}(A)=\operatorname{rk}(A|b)$.

**Eliminazione di Gauss (MEG)** — il foglio diceva *DA SVOLGERE*:

1. Scambio $R_1\leftrightarrow R_2$: $\left[\begin{array}{cc|c}3&2&1\\0&-1&-2\\-2&5&k\end{array}\right]$.
2. $R_3\to R_3+\tfrac23R_1$ (oppure $3R_3+2R_1$): $\left[\begin{array}{cc|c}3&2&1\\0&-1&-2\\0&\tfrac{19}{3}&k+\tfrac23\end{array}\right]$.
3. $R_3\to R_3+\tfrac{19}{3}R_2$: $\left[\begin{array}{cc|c}3&2&1\\0&-1&-2\\0&0&k+\tfrac23-\tfrac{38}{3}\end{array}\right]$, cioè ultima riga $\left[0\ 0\mid k-12\right]$.

Nel foglio, con moltiplicazioni intere, l'ultima riga compare come $[0\ 0\mid 3k-36]$ (stessa condizione moltiplicata per 3).

- $\operatorname{rk}(A)=2$ (due pivot).
- $\operatorname{rk}(A|b)=2\iff3k-36=0\iff\boxed{k=12}$; altrimenti $\operatorname{rk}(A|b)=3$ e **nessuna** soluzione.

**Verifica diretta.** Dalla seconda riga: $-x_2=-2\Rightarrow x_2=2$. Dalla prima: $3x_1+2\cdot2=1\Rightarrow x_1=-1$. Terza riga originale: $-2(-1)+5\cdot2=12=k$ ✓. Quindi

$$
\vec v=-\vec v_1+2\vec v_2\quad\text{per }k=12.
$$

**Metodo alternativo (determinante).** $\vec v\in\operatorname{span}\{\vec v_1,\vec v_2\}$ con $\vec v_1,\vec v_2$ indipendenti $\iff\det[\vec v_1\ \vec v_2\ \vec v]=0$. Sviluppando:

$$
\begin{vmatrix}0&-1&-2\\3&2&1\\-2&5&k\end{vmatrix}
=1\cdot\begin{vmatrix}3&1\\-2&k\end{vmatrix}-2\begin{vmatrix}3&2\\-2&5\end{vmatrix}
=(3k+2)-2(15+4)=3k-36
$$

che si annulla per $k=12$ ✓ (coerente col foglio).

**Interpretazione geometrica.** $\operatorname{span}\{\vec v_1,\vec v_2\}$ è un **piano per l'origine** in $\mathbb R^3$ (il rettangolo inclinato disegnato nei fogli). Il vettore $\vec v=(-2,1,k)$ vive su una retta parallela all'asse $z$ al variare di $k$; sta nel piano **solo** per $k=12$.

---

## 5. Dipendenza e indipendenza lineare

### Definizione

Siano $\vec v_1,\dots,\vec v_n\in V$. Considero l'equazione

$$
\sum_{i=1}^n\lambda_i\vec v_i=\lambda_1\vec v_1+\dots+\lambda_n\vec v_n=\vec 0.
$$

- Se l'**unica** soluzione è $\lambda_1=\dots=\lambda_n=0$, i vettori sono **linearmente indipendenti**.
- Se esiste una soluzione con **almeno un** $\lambda_i\neq0$, sono **linearmente dipendenti**.

**Equivalenza utile:** $\vec v_1,\dots,\vec v_n$ sono dipendenti $\iff$ almeno uno è combinazione lineare degli altri. (Se $\lambda_j\ne0$: $\vec v_j=-\sum_{i\ne j}\frac{\lambda_i}{\lambda_j}\vec v_i$.)

**Geometria.** In $\mathbb R^2$: due vettori indipendenti = non allineati; un terzo vettore $\vec v_3$ è sempre combinazione di $\vec v_1,\vec v_2$ (sono dipendenti). In $\mathbb R^3$: tre vettori sono dipendenti se **complanari**.

### Criterio col rango

Sia $A$ la matrice che ha i vettori come **righe** (o come colonne: il rango non cambia). Allora

$$
\vec v_1,\dots,\vec v_n\text{ indipendenti}\iff\operatorname{rk}(A)=n.
$$

Perché un sistema omogeneo $A\vec\lambda=\vec0$ ha solo la soluzione banale esattamente quando il rango eguaglia il numero di incognite.

### Esempi

**Indipendenti.** $\alpha\begin{bmatrix}1\\0\\0\end{bmatrix}+\beta\begin{bmatrix}0\\1\\0\end{bmatrix}+\gamma\begin{bmatrix}0\\0\\1\end{bmatrix}=\begin{bmatrix}\alpha\\\beta\\\gamma\end{bmatrix}=\vec 0\Rightarrow\alpha=\beta=\gamma=0$ (base canonica).

**Dipendenti** (esempio del foglio, vettori ricostruiti con coefficienti $\alpha=-2,\beta=-3,\gamma=1$):

$$
-2\begin{bmatrix}1\\0\\1\end{bmatrix}-3\begin{bmatrix}2\\1\\3\end{bmatrix}+1\begin{bmatrix}8\\3\\11\end{bmatrix}=\begin{bmatrix}-2-6+8\\0-3+3\\-2-9+11\end{bmatrix}=\begin{bmatrix}0\\0\\0\end{bmatrix}
$$

con coefficienti non tutti nulli ⇒ dipendenti. *(Nota: nel foglio i numeri del terzo vettore erano poco leggibili; ho scelto quelli che rendono vera la relazione.)*

---

## 6. Esercizio con parametro: quando sono indipendenti? (svolto)

**Testo.** Per $k\in\mathbb R$ considero i vettori di $\mathbb R^4$ (scritti come righe)

$$
\vec v_1=(0,1,1,2),\quad\vec v_2=(-1,0,1,2),\quad\vec v_3=(1,2,k,k+1).
$$

Per quali $k$ sono linearmente indipendenti?

**Metodo 1: eliminazione di Gauss.** Matrice con i vettori come righe:

$$
A=\begin{bmatrix}0&1&1&2\\-1&0&1&2\\1&2&k&k+1\end{bmatrix}
$$

- $R_1\leftrightarrow R_2$: $\begin{bmatrix}-1&0&1&2\\0&1&1&2\\1&2&k&k+1\end{bmatrix}$;
- $R_3\to R_3+R_1$: $\begin{bmatrix}-1&0&1&2\\0&1&1&2\\0&2&k+1&k+3\end{bmatrix}$;
- $R_3\to R_3-2R_2$: $\begin{bmatrix}-1&0&1&2\\0&1&1&2\\0&0&k-1&k-1\end{bmatrix}$.

Il terzo pivot esiste $\iff k-1\neq0$. Dunque

- $k\ne1$: $\operatorname{rk}A=3$ ⇒ **indipendenti**;
- $k=1$: $\operatorname{rk}A=2$ ⇒ **dipendenti**.

**Metodo 2: Kronecker.** Il minore $\begin{vmatrix}0&1\\-1&0\end{vmatrix}=1\ne0$ (righe 1,2; colonne 1,2) dà $\operatorname{rk}A\ge2$. Orlato con riga 3 e colonna 3:

$$
\begin{vmatrix}0&1&1\\-1&0&1\\1&2&k\end{vmatrix}
=-1\cdot\begin{vmatrix}-1&1\\1&k\end{vmatrix}+1\cdot\begin{vmatrix}-1&0\\1&2\end{vmatrix}
=-(-k-1)+(-2)=k-1.
$$

Per $k\ne1$ è non nullo ⇒ $\operatorname{rk}A=3$ (massimo possibile con 3 righe). Per $k=1$ occorre controllare anche l'altro orlato (colonna 4): $\begin{vmatrix}0&1&2\\-1&0&2\\1&2&2\end{vmatrix}=-1\cdot(-2-2)+2\cdot(-2)=4-4=0$, quindi $\operatorname{rk}A=2$ (qui il foglio scrive: "$=\dots=k\ne1$", cioè stessa condizione).

**Verifica a $k=1$:** $\vec v_3=(1,2,1,2)=2\vec v_1-\vec v_2$, infatti $2(0,1,1,2)-(-1,0,1,2)=(1,2,1,2)$ ✓ ⇒ dipendenti.

---

## 7. Tre vettori: $\vec v$ è somma di $\vec v_1,\vec v_2$

Se $\vec v=\vec v_1+\vec v_2$ (o in generale combinazione lineare di $\vec v_1,\vec v_2$), allora

$$
\vec v,\vec v_1,\vec v_2\text{ sono linearmente dipendenti}\iff\operatorname{rk}[\vec v\ \vec v_1\ \vec v_2]=2\iff\det[\vec v\ \vec v_1\ \vec v_2]=0
$$

(l'ultima equivalenza vale per tre vettori in $\mathbb R^3$). Nell'esercizio della sezione 4 questo è il motivo per cui la condizione "$\vec v$ combinazione di $\vec v_1,\vec v_2$" è equivalente a $\det=0\iff k=12$.

---

## Riepilogo: quale strumento usare?

| Domanda | Strumento | Condizione |
|---|---|---|
| Qual è il rango di $A$? | Kronecker (orlati) o Gauss | minore non nullo + tutti gli orlati nulli / numero di pivot |
| $H$ è sottospazio? | criterio: $\vec0\in H$ + chiusura lineare | un controesempio basta per negare |
| $\vec w\in\operatorname{span}\{\vec v_i\}$? | $\operatorname{rk}(A)=\operatorname{rk}(A\mid\vec w)$ (Rouché-Capelli) | sistema $\sum x_i\vec v_i=\vec w$ risolubile |
| $\vec v_1,\dots,\vec v_n$ indipendenti? | $\operatorname{rk}[\vec v_1\dots\vec v_n]=n$ | per $n$ vettori in $\mathbb R^n$: $\det\ne0$ |
| Dipendenza al variare di $k$ | Gauss con parametro, pivot $\ne0$ | studiare quando un pivot si annulla |

## Esercizi per allenarsi

1. Calcola il rango di $B=\begin{bmatrix}1&2&0&1\\2&4&1&3\\3&6&1&4\end{bmatrix}$ con Kronecker.
2. Stabilisci se $W=\{(x,y,z)\in\mathbb R^3: x=2y\}$ è sottospazio; se sì, trova due generatori.
3. Trova per quali $k$ il vettore $(1,k,2)$ appartiene a $\operatorname{span}\{(1,0,1),(0,1,1)\}$.
4. Per quali $k$ i vettori $(1,1,k),(1,k,1),(k,1,1)$ sono indipendenti? (Suggerimento: $\det=-(k-1)^2(k+2)$.)

### Soluzioni sintetiche

1. $R_3=R_1+R_2$ ⇒ $\operatorname{rk}B=2$. Minore non nullo: $\begin{vmatrix}1&0\\2&1\end{vmatrix}=1$ (righe 1,2; colonne 1,3) e orlati nulli perché $R_3=R_1+R_2$.
2. Sì: $\vec0\in W$ e $x=2y$ è una condizione lineare omogenea (chiusa). $W=\operatorname{span}\{(2,1,0),(0,0,1)\}$.
3. $x_1(1,0,1)+x_2(0,1,1)=(x_1,x_2,x_1+x_2)=(1,k,2)\Rightarrow x_1=1,x_2=k,\ 1+k=2\Rightarrow k=1$.
4. $\det\ne0\iff k\ne1$ e $k\ne-2$: indipendenti per $k\notin\{1,-2\}$.
