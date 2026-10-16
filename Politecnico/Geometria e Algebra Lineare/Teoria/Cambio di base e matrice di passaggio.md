---
tags:
  - geometria-algebra-lineare
  - basi
  - matrice-rappresentativa
  - cambio-di-base
---
## Cambio di base e matrice di passaggio

> **Idea.** Un vettore $\mathbf v$ è un oggetto geometrico/astratto; le sue **coordinate** dipendono dalla base scelta. Cambiando base cambiano i numeri, non il vettore. La **matrice di passaggio** è il "dizionario" lineare che traduce le coordinate da una base all'altra. Lo stesso accade per una mappa lineare: la sua matrice rappresentativa dipende dalle basi di dominio e codominio, e cambia secondo una regola precisa (Teorema 2).

Prerequisiti: [[Politecnico/Geometria e Algebra Lineare/Teoria/Basi, dimensione e coordinate.md|Basi, dimensione e coordinate]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Teorema di rappresentazione e matrice rappresentativa.md|Teorema di rappresentazione e matrice rappresentativa]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]].

### Notazione

Sia $V$ uno spazio vettoriale su $\mathbb K$ con $\dim V=n<\infty$ e sia $\mathcal B=(\mathbf v_1,\dots,\mathbf v_n)$ una base. Per $\mathbf v\in V$ indichiamo con $[\mathbf v]_{\mathcal B}\in\mathbb K^n$ il **vettore delle coordinate** di $\mathbf v$ rispetto a $\mathcal B$, cioè l'unica $n$-upla $(c_1,\dots,c_n)$ con
$$\mathbf v=c_1\mathbf v_1+\dots+c_n\mathbf v_n .$$
L'applicazione $\mathbf v\mapsto[\mathbf v]_{\mathcal B}$ è un isomorfismo $V\to\mathbb K^n$ (la **mappa di coordinate**; la sua inversa $P_{\mathcal B}:\mathbb K^n\to V$, $\mathbf c\mapsto\sum c_j\mathbf v_j$, è la **mappa di parametrizzazione** associata a $\mathcal B$).

### Matrice di passaggio

Siano $\mathcal B=(\mathbf v_1,\dots,\mathbf v_n)$ ("base vecchia") e $\widetilde{\mathcal B}=(\tilde{\mathbf v}_1,\dots,\tilde{\mathbf v}_n)$ ("base nuova") due basi di $V$.

**Definizione.** La **matrice di passaggio da $\mathcal B$ a $\widetilde{\mathcal B}$** è la matrice $S\in M_{\mathbb K}(n)$ la cui $j$-esima colonna è il vettore delle coordinate del $j$-esimo vettore della *nuova* base rispetto alla *vecchia*:
$$S=\Big[\ [\tilde{\mathbf v}_1]_{\mathcal B}\ \Big|\ [\tilde{\mathbf v}_2]_{\mathcal B}\ \Big|\ \cdots\ \Big|\ [\tilde{\mathbf v}_n]_{\mathcal B}\ \Big].$$

> **Teorema 1 (di passaggio tra due basi).** Se $\mathbf c=[\mathbf v]_{\mathcal B}$ e $\tilde{\mathbf c}=[\mathbf v]_{\widetilde{\mathcal B}}$ sono le coordinate dello **stesso** vettore $\mathbf v\in V$, allora
> $$\boxed{\ \mathbf c=S\,\tilde{\mathbf c}\ }\qquad\text{e quindi}\qquad\tilde{\mathbf c}=S^{-1}\mathbf c ,$$
> dove $S$ è la matrice di passaggio da $\mathcal B$ a $\widetilde{\mathcal B}$. In particolare $S$ è **invertibile**.

**Dimostrazione.** Scriviamo ciascun vettore nuovo nella base vecchia: $\tilde{\mathbf v}_j=\sum_{i=1}^n S_{ij}\mathbf v_i$ (per definizione di $S$). Se $\mathbf v=\sum_j\tilde c_j\tilde{\mathbf v}_j$, allora
$$\mathbf v=\sum_{j}\tilde c_j\sum_i S_{ij}\mathbf v_i=\sum_i\Big(\sum_jS_{ij}\tilde c_j\Big)\mathbf v_i ,$$
e per l'unicità delle coordinate rispetto a $\mathcal B$ si ha $c_i=\sum_jS_{ij}\tilde c_j$, cioè $\mathbf c=S\tilde{\mathbf c}$.
Invertibilità: se $S\tilde{\mathbf c}=\mathbf 0$ allora $\mathbf v=\sum\tilde c_j\tilde{\mathbf v}_j$ ha coordinate nulle in $\mathcal B$, quindi $\mathbf v=\mathbf 0$, quindi $\tilde{\mathbf c}=\mathbf 0$ (le coordinate in $\widetilde{\mathcal B}$ di $\mathbf 0$ sono nulle). Dunque $\ker S=\{\mathbf 0\}$ e $S$ è quadrata invertibile. $\square$

> **Attenzione al verso.** La matrice "da $\mathcal B$ a $\widetilde{\mathcal B}$" ha per colonne la base **nuova** scritta con le coordinate **vecchie**, ma agisce trasformando le coordinate **nuove** in **vecchie** ($\tilde{\mathbf c}\mapsto\mathbf c$). Per andare da vecchie a nuove serve $S^{-1}$.

**Regole pratiche**
- Se $\mathcal B$ è la base canonica di $\mathbb K^n$, le colonne di $S$ sono semplicemente i vettori $\tilde{\mathbf v}_j$ della nuova base: $S=[\tilde{\mathbf v}_1|\cdots|\tilde{\mathbf v}_n]$.
- La matrice di passaggio nel verso opposto è l'inversa: $S_{\widetilde{\mathcal B}\to\mathcal B}=S_{\mathcal B\to\widetilde{\mathcal B}}^{-1}$. Le sue colonne sono i vettori della base *vecchia* espressi nelle coordinate *nuove*.
- Passaggi consecutivi si compongono: $S_{\mathcal B\to\mathcal B''}=S_{\mathcal B\to\mathcal B'}\,S_{\mathcal B'\to\mathcal B''}$.

### Due interpretazioni di $S$

1. **Come composizione di parametrizzazioni.** $S$ è la matrice, rispetto alla base canonica di $\mathbb K^n$, dell'applicazione
 $$P_{\mathcal B}^{-1}\circ P_{\widetilde{\mathcal B}}:\mathbb K^n\to\mathbb K^n$$
 (coordinate nuove $\to$ vettore $\to$ coordinate vecchie).
2. **Come matrice rappresentativa dell'identità.** $S=M^{\widetilde{\mathcal B}}_{\mathcal B}(\mathrm{I})$, cioè la matrice rappresentativa dell'applicazione identità $\mathrm I:V\to V$ ($\mathrm I(\mathbf v)=\mathbf v$) con la base $\widetilde{\mathcal B}$ nel dominio e $\mathcal B$ nel codominio. Allora $S^{-1}=M^{\mathcal B}_{\widetilde{\mathcal B}}(\mathrm I)$.

Per la notazione $M^{\text{dominio}}_{\text{codominio}}(\ell)$ vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Teorema di rappresentazione e matrice rappresentativa.md|Teorema di rappresentazione e matrice rappresentativa]].

### Teorema 2 (cambio di base per la matrice rappresentativa)

Sia $\ell:V\to W$ lineare. Siano $\mathcal B,\widetilde{\mathcal B}$ due basi di $V$ e $\mathcal C,\widetilde{\mathcal C}$ due basi di $W$. Siano
$$A=M^{\mathcal B}_{\mathcal C}(\ell),\qquad \widetilde A=M^{\widetilde{\mathcal B}}_{\widetilde{\mathcal C}}(\ell).$$
Allora
$$\boxed{\ \widetilde A=S_W^{-1}\,A\,S_V\ }$$
dove $S_V$ è la matrice di passaggio da $\mathcal B$ a $\widetilde{\mathcal B}$ (in $V$) e $S_W$ quella da $\mathcal C$ a $\widetilde{\mathcal C}$ (in $W$).

**Dimostrazione.** Fissiamo $\mathbf v\in V$ e poniamo $\mathbf b=[\mathbf v]_{\mathcal B}$, $\tilde{\mathbf b}=[\mathbf v]_{\widetilde{\mathcal B}}$, $\mathbf c=[\ell(\mathbf v)]_{\mathcal C}$, $\tilde{\mathbf c}=[\ell(\mathbf v)]_{\widetilde{\mathcal C}}$. Per il teorema di rappresentazione
$$\mathbf c=A\mathbf b,\qquad\tilde{\mathbf c}=\widetilde A\tilde{\mathbf b},$$
e per il Teorema 1
$$\mathbf b=S_V\tilde{\mathbf b},\qquad\tilde{\mathbf c}=S_W^{-1}\mathbf c .$$
Quindi $\tilde{\mathbf c}=S_W^{-1}\mathbf c=S_W^{-1}A\mathbf b=S_W^{-1}AS_V\tilde{\mathbf b}$. Confrontando con $\tilde{\mathbf c}=\widetilde A\tilde{\mathbf b}$ si ottiene $\widetilde A\tilde{\mathbf b}=(S_W^{-1}AS_V)\tilde{\mathbf b}$ per ogni $\tilde{\mathbf b}\in\mathbb K^n$ (perché $\mathbf v$ è arbitrario e le coordinate riempiono tutto $\mathbb K^n$). Due matrici che coincidono su ogni vettore sono uguali (prendere $\tilde{\mathbf b}=\mathbf e_j$): $\widetilde A=S_W^{-1}AS_V$. $\square$

**Forma "a composizione".** Con le matrici dell'identità:
$$M^{\widetilde{\mathcal B}}_{\widetilde{\mathcal C}}(\ell)=M^{\mathcal C}_{\widetilde{\mathcal C}}(\mathrm I)\;M^{\mathcal B}_{\mathcal C}(\ell)\;M^{\widetilde{\mathcal B}}_{\mathcal B}(\mathrm I),$$
che corrisponde al diagramma (si legge da destra a sinistra)
$$(V,\widetilde{\mathcal B})\xrightarrow{\ \mathrm I\ }(V,\mathcal B)\xrightarrow{\ \ell\ }(W,\mathcal C)\xrightarrow{\ \mathrm I\ }(W,\widetilde{\mathcal C}).$$
Per ricordare la formula: **prima** si converte l'input da coordinate nuove a vecchie ($S_V$), **poi** si applica $A$, **infine** si converte l'output da vecchie a nuove ($S_W^{-1}$).

**Casi particolari**
- Se cambia solo la base del dominio: $S_W=I$, $\widetilde A=AS_V$.
- Se cambia solo la base del codominio: $S_V=I$, $\widetilde A=S_W^{-1}A$.
- **Endomorfismi** ($V=W$, $\mathcal B=\mathcal C$, $\widetilde{\mathcal B}=\widetilde{\mathcal C}$): $S_V=S_W=S$ e
 $$\widetilde A=S^{-1}AS\qquad(\text{matrici simili}).$$
 Due matrici rappresentative dello stesso endomorfismo sono **simili**. Scegliere la base "giusta" può rendere $\widetilde A$ **diagonale** (esempio 4 negli esercizi): è l'idea della diagonalizzazione, che si svilupperà con autovalori e autovettori.

### Esempi svolti

#### Esempio 1 — coordinate in $\mathbb R^2$ rispetto a due basi

Siano $\mathcal B=(\mathbf v_1,\mathbf v_2)$ con $\mathbf v_1=\begin{bmatrix}1\\2\end{bmatrix},\ \mathbf v_2=\begin{bmatrix}2\\1\end{bmatrix}$ e $\widetilde{\mathcal B}=(\tilde{\mathbf v}_1,\tilde{\mathbf v}_2)$ con $\tilde{\mathbf v}_1=\begin{bmatrix}1\\1\end{bmatrix},\ \tilde{\mathbf v}_2=\begin{bmatrix}1\\-1\end{bmatrix}$. Dato $\mathbf x\in\mathbb R^2$ con coordinate $(c_1,c_2)$ in $\mathcal B$, trovare le coordinate $(\tilde c_1,\tilde c_2)$ in $\widetilde{\mathcal B}$.

**Soluzione.** Scriviamo i vettori nuovi nella base vecchia:
$$\tilde{\mathbf v}_1=\tfrac13(\mathbf v_1+\mathbf v_2),\qquad\tilde{\mathbf v}_2=\mathbf v_2-\mathbf v_1 .$$
(Controllo: $\frac13(3,3)=(1,1)$; $(2,1)-(1,2)=(1,-1)$.) Quindi
$$S=\begin{bmatrix}1/3&-1\\1/3&1\end{bmatrix},\qquad\det S=\tfrac13+\tfrac13=\tfrac23,\qquad S^{-1}=\frac1{2/3}\begin{bmatrix}1&1\\-1/3&1/3\end{bmatrix}=\begin{bmatrix}3/2&3/2\\-1/2&1/2\end{bmatrix}.$$
Per il Teorema 1, $\tilde{\mathbf c}=S^{-1}\mathbf c$:
$$\boxed{\ \tilde c_1=\tfrac32(c_1+c_2),\qquad\tilde c_2=\tfrac12(c_2-c_1)\ }$$
*Verifica:* $\mathbf x=\mathbf v_1$ ha $\mathbf c=(1,0)$, quindi $\tilde{\mathbf c}=(3/2,-1/2)$ e $\frac32(1,1)-\frac12(1,-1)=(1,2)=\mathbf v_1$ ✓.

---

#### Esempio 2 — coordinate di un polinomio in $\mathcal P_2$ (tre metodi)

Trovare le coordinate di $p(x)=3-x+7x^2$ rispetto alla base $\mathcal B=(q_1,q_2,q_3)$ di $\mathcal P_2$ con
$$q_1=1+x+x^2,\qquad q_2=1-x+x^2,\qquad q_3=1-x^2 .$$
Con la base canonica $\mathcal E=(1,x,x^2)$ le coordinate sono immediate (i coefficienti): $\mathbf c_{\mathcal E}=(3,-1,7)$. Cerchiamo $\mathbf c_{\mathcal B}$.

**Metodo 1 — matrice di passaggio e inversa.** Le colonne di $S_{\mathcal E\to\mathcal B}$ sono le coordinate di $q_1,q_2,q_3$ in $\mathcal E$: $(1,1,1),\ (1,-1,1),\ (1,0,-1)$.
$$S_{\mathcal E\to\mathcal B}=\begin{bmatrix}1&1&1\\1&-1&0\\1&1&-1\end{bmatrix},\qquad\mathbf c_{\mathcal B}=S_{\mathcal E\to\mathcal B}^{-1}\mathbf c_{\mathcal E}.$$
Calcolo dell'inversa con Gauss–Jordan su $[S\,|\,I]$:

- $R_2\to R_2-R_1,\ R_3\to R_3-R_1$: $\left[\begin{array}{ccc|ccc}1&1&1&1&0&0\\0&-2&-1&-1&1&0\\0&0&-2&-1&0&1\end{array}\right]$
- $R_2\to-\frac12R_2,\ R_3\to-\frac12R_3$: $\left[\begin{array}{ccc|ccc}1&1&1&1&0&0\\0&1&\frac12&\frac12&-\frac12&0\\0&0&1&\frac12&0&-\frac12\end{array}\right]$
- $R_1\to R_1-R_3,\ R_2\to R_2-\frac12R_3$: $\left[\begin{array}{ccc|ccc}1&1&0&\frac12&0&\frac12\\0&1&0&\frac14&-\frac12&\frac14\\0&0&1&\frac12&0&-\frac12\end{array}\right]$
- $R_1\to R_1-R_2$: $\left[\begin{array}{ccc|ccc}1&0&0&\frac14&\frac12&\frac14\\0&1&0&\frac14&-\frac12&\frac14\\0&0&1&\frac12&0&-\frac12\end{array}\right]$

$$S_{\mathcal E\to\mathcal B}^{-1}=\begin{bmatrix}1/4&1/2&1/4\\1/4&-1/2&1/4\\1/2&0&-1/2\end{bmatrix},\qquad\mathbf c_{\mathcal B}=S^{-1}\begin{bmatrix}3\\-1\\7\end{bmatrix}=\begin{bmatrix}2\\3\\-2\end{bmatrix}.$$

*Controllo:* $2q_1+3q_2-2q_3$ ha termine noto $2+3-2=3$, coefficiente di $x$ pari a $2-3=-1$, coefficiente di $x^2$ pari a $2+3+2=7$. Totale $3-x+7x^2=p(x)$ ✓.

> *Nota sull'originale.* Negli appunti a mano compaiono due refusi di trascrizione: nell'ultimo passo di Gauss–Jordan la prima riga è scritta $(1\ 0\ 1)$ invece di $(1\ 0\ 0)$, e nella matrice $S_{\mathcal B\to\mathcal E}$ l'elemento in basso a sinistra è $\frac14$ invece di $\frac12$ (le coordinate di $1$ sono $(\frac14,\frac14,\frac12)$). I valori finali sono quelli corretti qui sopra.

**Metodo 2 — inversa "a occhio".** $S^{-1}_{\mathcal E\to\mathcal B}=S_{\mathcal B\to\mathcal E}$ ha per colonne le coordinate di $1,x,x^2$ rispetto a $\mathcal B$. Invece di risolvere 3 sistemi, si "indovina":
- $q_1-q_2=2x\ \Rightarrow\ x=\tfrac12q_1-\tfrac12q_2$, coordinate $(\tfrac12,-\tfrac12,0)$;
- $q_1+q_2=2(1+x^2)\ \Rightarrow\ q_1+q_2+2q_3=4\ \Rightarrow\ 1=\tfrac14q_1+\tfrac14q_2+\tfrac12q_3$, coordinate $(\tfrac14,\tfrac14,\tfrac12)$;
- $x^2=1-q_3$: coordinate $(\tfrac14,\tfrac14,\tfrac12)-(0,0,1)=(\tfrac14,\tfrac14,-\tfrac12)$.

Incolonnando (ordine $1,x,x^2$) si ritrova la stessa matrice del Metodo 1, e si moltiplica per $(3,-1,7)^T$.

**Metodo 3 — metodo diretto (coefficienti incogniti).** Utile se serve **un solo** vettore. Imponiamo $p=c_1q_1+c_2q_2+c_3q_3$ come uguaglianza di polinomi:
$$3-x+7x^2=(c_1+c_2+c_3)+(c_1-c_2)x+(c_1+c_2-c_3)x^2 .$$
Per il principio di identità dei polinomi:
$$\begin{cases}c_1+c_2+c_3=3\\c_1-c_2=-1\\c_1+c_2-c_3=7\end{cases}\ \xrightarrow{\ R_2-R_1,\ R_3-R_1\ }\ \begin{cases}c_1+c_2+c_3=3\\-2c_2-c_3=-4\\-2c_3=4\end{cases}\Rightarrow c_3=-2,\ c_2=3,\ c_1=2 .$$

Tutti e tre i metodi danno $\mathbf c_{\mathcal B}=(2,3,-2)$.

---

#### Esempio 3 — cambio di base nel dominio ($\mathbb R^3\to\mathbb R^2$)

$L:\mathbb R^3\to\mathbb R^2$ ha matrice $A=\begin{bmatrix}1&3&5\\2&4&6\end{bmatrix}$ rispetto alle basi canoniche. Trovare la matrice rappresentativa rispetto alla base $\widetilde{\mathcal B}=(\mathbf v_1,\mathbf v_2,\mathbf v_3)$ nel dominio e alla base canonica nel codominio, dove
$$\mathbf v_1=\begin{bmatrix}-3\\3\\-1\end{bmatrix},\quad\mathbf v_2=\begin{bmatrix}2\\1\\-1\end{bmatrix},\quad\mathbf v_3=\begin{bmatrix}1\\-2\\1\end{bmatrix}.$$

**Soluzione.** Cambia solo il dominio, quindi $S_W=I_2$ e $\widetilde A=AS_V$ con $S_V=[\mathbf v_1|\mathbf v_2|\mathbf v_3]$ (la base di partenza è canonica):
$$\widetilde A=\begin{bmatrix}1&3&5\\2&4&6\end{bmatrix}\begin{bmatrix}-3&2&1\\3&1&-2\\-1&-1&1\end{bmatrix}=\begin{bmatrix}1&0&0\\0&2&0\end{bmatrix}.$$
*Calcolo:* riga 1: $-3+9-5=1,\ 2+3-5=0,\ 1-6+5=0$; riga 2: $-6+12-6=0,\ 4+4-6=2,\ 2-8+6=0$.

**Significato.** Se $\tilde{\mathbf b}=(b_1,b_2,b_3)$ sono le coordinate di $\mathbf x\in\mathbb R^3$ in $\widetilde{\mathcal B}$, allora $L(\mathbf x)=\widetilde A\tilde{\mathbf b}=(b_1,\ 2b_2)$: nella base giusta la mappa è semplicissima (il terzo vettore $\mathbf v_3\in\ker L$).

---

#### Esempio 4 — rotazione nel piano e diagonalizzazione (con $\mathbb C^2$)

$L:\mathbb R^2\to\mathbb R^2$ è la rotazione antioraria di angolo $\theta$ attorno all'origine:
$$L(x,y)=(x\cos\theta-y\sin\theta,\ x\sin\theta+y\cos\theta),\qquad A=\begin{bmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{bmatrix}.$$
Consideriamo la mappa **complessificata** $L_{\mathbb C}:\mathbb C^2\to\mathbb C^2$ con la stessa matrice $A$, e cambiamo base sia nel dominio sia nel codominio, da quella canonica a
$$\widetilde{\mathcal B}=\widetilde{\mathcal C}=\left(\begin{bmatrix}1\\i\end{bmatrix},\begin{bmatrix}1\\-i\end{bmatrix}\right).$$
Allora $S_V=S_W=S=\begin{bmatrix}1&1\\i&-i\end{bmatrix}$, $\det S=-2i$ e
$$S^{-1}=\frac1{-2i}\begin{bmatrix}-i&-1\\-i&1\end{bmatrix}=\frac12\begin{bmatrix}1&-i\\1&i\end{bmatrix}\qquad\Big(\text{perché }\tfrac1{-2i}=\tfrac i2\Big).$$
Per il Teorema 2, $\widetilde A=S^{-1}AS$:
$$\widetilde A=\frac12\begin{bmatrix}1&-i\\1&i\end{bmatrix}\begin{bmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{bmatrix}\begin{bmatrix}1&1\\i&-i\end{bmatrix}
=\frac12\begin{bmatrix}\cos\theta-i\sin\theta&-\sin\theta-i\cos\theta\\\cos\theta+i\sin\theta&-\sin\theta+i\cos\theta\end{bmatrix}\begin{bmatrix}1&1\\i&-i\end{bmatrix}.$$
Per la formula di Eulero $\cos\theta\mp i\sin\theta=e^{\mp i\theta}$, e $-\sin\theta-i\cos\theta=-ie^{-i\theta}$, $-\sin\theta+i\cos\theta=ie^{i\theta}$:
$$\widetilde A=\frac12\begin{bmatrix}e^{-i\theta}&-ie^{-i\theta}\\e^{i\theta}&ie^{i\theta}\end{bmatrix}\begin{bmatrix}1&1\\i&-i\end{bmatrix}=\frac12\begin{bmatrix}2e^{-i\theta}&0\\0&2e^{i\theta}\end{bmatrix}=\boxed{\operatorname{diag}\big(e^{-i\theta},e^{i\theta}\big)}.$$

**Commento.** Sul campo $\mathbb R$ una rotazione (con $\theta\ne0,\pi$) non è diagonalizzabile; su $\mathbb C$ sì, con base formata dai vettori $(1,i)$ e $(1,-i)$ (autovettori, con autovalori $e^{-i\theta}$ e $e^{i\theta}$). In generale: data $L:V\to V$ con $\dim V<\infty$ c'è un metodo per stabilire se esiste una base rispetto alla quale la matrice è diagonale (e trovarla): sarà il tema degli autovalori.

### Ripasso intuitivo e controlli

**Verso di $S$ (l'errore più frequente).** $S$ ha per colonne la base *nuova* in coordinate *vecchie*, ma agisce $\tilde{\mathbf c}\mapsto\mathbf c$ (nuove → vecchie). Lettura: $\mathbf c=S\tilde{\mathbf c}$ costruisce $\sum\tilde c_j\tilde{\mathbf v}_j$ e lo scrive in coordinate vecchie. Per andare vecchie → nuove serve $S^{-1}$.

**Esempio numerico.** In $\mathbb R^2$, $\mathcal B=$ canonica, $\widetilde{\mathcal B}=((1,1),(1,-1))$:
$$S=\begin{pmatrix}1&1\\1&-1\end{pmatrix},\quad S^{-1}=\tfrac12\begin{pmatrix}1&1\\1&-1\end{pmatrix},\quad \mathbf v=(3,1)\ \Rightarrow\ \tilde{\mathbf c}=S^{-1}\binom31=\binom21 .$$
Verifica: $2(1,1)+1\,(1,-1)=(3,1)$ ✓.

**Tra due basi non canoniche.** Se $S_1,S_2$ hanno come colonne le due basi (in canonica), allora $S_{\mathcal B_1\to\mathcal B_2}=S_1^{-1}S_2$.

**Endomorfismi.** Per $V=W$ e stessa base, $\widetilde A=S^{-1}AS$: matrici **simili**, stessa applicazione in basi diverse, quindi stessi rango, determinante, traccia, autovalori. La diagonalizzazione cerca la base in cui $\widetilde A$ è diagonale.

**Legame con rette e piani.** Una parametrizzazione $\tilde{\mathbf c}\mapsto\mathbf c$ è un'applicazione lineare invertibile (qui $S$); lo span della nota [[Politecnico/Geometria e Algebra Lineare/Teoria/Rette e piani — equazioni parametriche e cartesiane.md|Rette e piani]] è l'immagine di $[\mathbf v|\mathbf w]$, la forma cartesiana è il nucleo di un'altra matrice.

**Errori tipici**
1. Scambiare $S$ e $S^{-1}$.
2. Mettere i vettori della base per riga invece che per colonna.
3. Nel Teorema 2, sbagliare l'ordine: è $S_W^{-1}AS_V$ (da destra: nuove di $V$ → vecchie di $V$ → $A$ → nuove di $W$).

### Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Basi, dimensione e coordinate.md|Basi, dimensione e coordinate]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Eliminazione di Gauss-Jordan e calcolo della matrice inversa.md|Eliminazione di Gauss-Jordan e matrice inversa]] (per calcolare $S^{-1}$)
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni lineari, nucleo e immagine.md|Applicazioni lineari, nucleo e immagine]]

> **Nota.** Nelle dispense della lezione 5 il paragrafo sul passaggio tra due *sistemi di riferimento* (cambio di origine + cambio di base nello spazio affine, pp. 21–36 e 41–53) è stato rimandato a una lezione successiva; quando verrà svolto andrà in [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi di riferimento nel piano.md|Sistemi di riferimento nel piano]].
