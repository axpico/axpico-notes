---
tags:
  - geometria-algebra-lineare
  - spazi-vettoriali
  - basi
---
## Completamento a base

↑ [[Politecnico/Geometria e Algebra Lineare/Indice|Indice]] · tappa 7 (Somma e intersezione di sottospazi) · prima: [[Ortogonalità e fasci di rette e piani|Ortogonalità e fasci]] · dopo: [[Intersezione, somma e somma diretta di sottospazi — formula di Grassmann|Intersezione, somma, somma diretta e Grassmann]]

> Fonte: [[08 completa.pdf|Lezione 8 (PDF)]], pp. 1–17. Testo di riferimento (ALG): pp. 180–184.

**Idea.** In uno spazio di dimensione finita $n$, ogni sistema linearmente indipendente di $k<n$ vettori si può *allungare* fino a una base. Il teorema astratto (lemma di completamento) garantisce l'esistenza; qui interessa l'**algoritmo**: in $K^n$ si fa con una sola eliminazione di Gauss (MEG), e ogni altro spazio finito-dimensionale si riduce a $K^n$ tramite coordinate.

---

### Il problema

Sia $V$ uno spazio vettoriale con $n:=\dim V<+\infty$ e siano $\mathbf v_1,\dots,\mathbf v_k\in V$, $k<n$, **linearmente indipendenti**.

**Problema.** Trovare una base di $V$ che contenga $\mathbf v_1,\dots,\mathbf v_k$.

> **Riduzione a $K^n$.** Fissata una base $\mathcal B_0$ di $V$, la mappa delle coordinate $V\to K^n$ è un isomorfismo; gli isomorfismi preservano indipendenza lineare e basi. Quindi basta risolvere il problema per i vettori delle coordinate in $K^n$ e poi "tornare indietro".

### La ricetta in $K^n$

1. Accoda ai vettori dati una base qualsiasi di $K^n$, ad esempio la canonica:
$$C=\{\mathbf v_1,\dots,\mathbf v_k,\ \mathbf e_1,\dots,\mathbf e_n\}\quad(n+k\text{ vettori}).$$
2. Scrivi la matrice $[\mathbf v_1|\cdots|\mathbf v_k|\mathbf e_1|\cdots|\mathbf e_n]$ e riducila a scala con MEG.
3. Le **colonne pivot** della matrice di partenza formano una base di $K^n$.

**Perché funziona.** Le operazioni elementari di riga non cambiano le relazioni lineari tra le colonne (se $\sum c_j\mathbf a_j=\mathbf 0$ prima, vale anche dopo, perché $EA\mathbf c=\mathbf 0\iff A\mathbf c=\mathbf 0$ con $E$ invertibile). In una matrice a scala le colonne pivot sono indipendenti e ogni altra colonna è combinazione delle pivot che la precedono. Poiché $\mathbf v_1,\dots,\mathbf v_k$ sono indipendenti e stanno **per primi**, le loro colonne sono tutte pivot; poiché gli $\mathbf e_i$ generano $K^n$, il rango totale è $n$. Le $n$ colonne pivot sono quindi una base che contiene i $\mathbf v_i$.

> [!warning] L'ordine conta
> I vettori dati vanno messi **prima** della base canonica. Se mettessi prima $\mathbf e_1,\dots,\mathbf e_n$, le prime $n$ colonne sarebbero già tutte pivot e otterresti la base canonica, che in generale **non** contiene i $\mathbf v_i$.

**Prerequisito.** Va controllato prima che i $\mathbf v_i$ siano indipendenti: se fossero dipendenti nessun completamento potrebbe dare una base.

**La risposta non è unica**: diverse scelte della base ausiliaria, o anche solo diverse verifiche "a mano", danno completamenti diversi, tutti corretti.

---

### Esempio 1 — completare in $\mathbb R^3$

$\mathbf v_1=(1,1,1)^T$, $\mathbf v_2=(1,2,3)^T$. Trovare $\mathbf v_3$ con $\{\mathbf v_1,\mathbf v_2,\mathbf v_3\}$ base di $\mathbb R^3$.

Indipendenza: nessuno dei due è multiplo dell'altro. Poi:
$$\left[\begin{array}{cc|ccc}1&1&1&0&0\\1&2&0&1&0\\1&3&0&0&1\end{array}\right]
\xrightarrow[R_3\to R_3-R_1]{R_2\to R_2-R_1}
\left[\begin{array}{cc|ccc}1&1&1&0&0\\0&1&-1&1&0\\0&2&-1&0&1\end{array}\right]
\xrightarrow{R_3\to R_3-2R_2}
\left[\begin{array}{cc|ccc}\boxed1&1&1&0&0\\0&\boxed1&-1&1&0\\0&0&\boxed1&-2&1\end{array}\right]$$
Pivot nelle colonne 1, 2, 3 ⇒ $\{\mathbf v_1,\mathbf v_2,\mathbf e_1\}$ è una base di $\mathbb R^3$.

*Esercizio (dal PDF).* Verificare che anche $\mathbf v_3=(1,0,1)^T$ va bene: $\det[\mathbf v_1|\mathbf v_2|\mathbf v_3]=\det\begin{bmatrix}1&1&1\\1&2&0\\1&3&1\end{bmatrix}=2-1+1=2\neq0$.

### Esempio 2 — un riferimento in cui un piano diventa $z'=0$

Trovare un sistema di riferimento $(O',\vec v_1,\vec v_2,\vec v_3)$ rispetto a cui il piano $\Pi:\ y+2z=-1$ abbia equazione $z'=0$.

**Strategia.** $z'=0$ significa: $\Pi=\{O'+x'\vec v_1+y'\vec v_2\}$. Serve quindi (i) un'origine $O'\in\Pi$, (ii) $\vec v_1,\vec v_2$ base della giacitura di $\Pi$, (iii) $\vec v_3$ che completi a base di $\mathbb R^3$.

- Parametriche: $y$ dipendente, $x=t$, $z=s$ libere ⇒ $y=-1-2s$:
$$\mathbf r=\begin{bmatrix}0\\-1\\0\end{bmatrix}+t\begin{bmatrix}1\\0\\0\end{bmatrix}+s\begin{bmatrix}0\\-2\\1\end{bmatrix}.$$
  Dunque $O'=(0,-1,0)$, $\mathbf v_1=(1,0,0)^T$, $\mathbf v_2=(0,-2,1)^T$.
- Completamento:
$$\left[\begin{array}{cc|ccc}1&0&1&0&0\\0&-2&0&1&0\\0&1&0&0&1\end{array}\right]
\xrightarrow{R_2\leftrightarrow R_3}
\left[\begin{array}{cc|ccc}1&0&1&0&0\\0&1&0&0&1\\0&-2&0&1&0\end{array}\right]
\xrightarrow{R_3\to R_3+2R_2}
\left[\begin{array}{cc|ccc}\boxed1&0&1&0&0\\0&\boxed1&0&0&1\\0&0&0&\boxed1&2\end{array}\right]$$
  Pivot nelle colonne 1, 2, 4 ⇒ $\mathbf v_3=\mathbf e_2$.

**Risposta.** $(O',\vec v_1,\vec v_2,\vec v_3)$ con $O'(0,-1,0)$, $\mathbf v_1=(1,0,0)^T$, $\mathbf v_2=(0,-2,1)^T$, $\mathbf v_3=(0,1,0)^T$.

**Verifica** (metodo della [[Cambio di base e matrice di passaggio|Lezione 5]]): $\mathbf r=O'+x'\mathbf v_1+y'\mathbf v_2+z'\mathbf v_3$ dà
$$x=x',\qquad y=-1-2y'+z',\qquad z=y'.$$
Sostituendo in $y+2z=-1$: $-1-2y'+z'+2y'=-1\iff z'=0$. ✓

> **Osservazione (metrica).** Se il riferimento iniziale è cartesiano, quello trovato **non** lo è: $\mathbf v_2\cdot\mathbf v_3=\langle(0,-2,1),(0,1,0)\rangle=-2\neq0$. Più avanti, con l'ortonormalizzazione di **Gram–Schmidt**, si otterrà un riferimento cartesiano $(O',\vec u_1,\vec u_2,\vec u_3)$ ($|\vec u_i|=1$, $\vec u_i\perp\vec u_j$) in cui l'equazione di $\Pi$ è ancora $z''=0$. Il completamento a base è un'operazione puramente **affine/lineare**: non sa nulla di angoli.

### Esempio 3 — completare in $P_3$

Verificare che $q_1(x)=(x+1)^3$ e $q_2(x)=x^3+3x^2+1$ sono indipendenti e completare $\{q_1,q_2\}$ a una base di $P_3=\{\text{polinomi di grado}\le3\}$.

**Riduzione a $\mathbb R^4$.** Usiamo l'isomorfismo indotto dalla base $\{1,x,x^2,x^3\}$:
$$p(x)=a_0+a_1x+a_2x^2+a_3x^3\ \longmapsto\ (a_0,a_1,a_2,a_3)^T\in\mathbb R^4.$$
Con $(x+1)^3=1+3x+3x^2+x^3$:
$$\mathbf v_1=(1,3,3,1)^T,\qquad \mathbf v_2=(1,0,3,1)^T.$$
Indipendenti (non proporzionali). Completamento:
$$\left[\begin{array}{cc|cccc}1&1&1&0&0&0\\3&0&0&1&0&0\\3&3&0&0&1&0\\1&1&0&0&0&1\end{array}\right]
\xrightarrow[R_4\to R_4-R_1]{R_2\to R_2-3R_1,\ R_3\to R_3-3R_1}
\left[\begin{array}{cc|cccc}1&1&1&0&0&0\\0&-3&-3&1&0&0\\0&0&-3&0&1&0\\0&0&-1&0&0&1\end{array}\right]$$
$$\xrightarrow{R_4\to3R_4-R_3}\left[\begin{array}{cc|cccc}\boxed1&1&1&0&0&0\\0&\boxed{-3}&-3&1&0&0\\0&0&\boxed{-3}&0&1&0\\0&0&0&0&\boxed{-1}&3\end{array}\right]$$
($3R_4-R_3$ invece di $R_4-\tfrac13R_3$ solo per restare con interi.)

L'eliminazione dà pivot in $\mathbf v_1,\mathbf v_2,\mathbf e_1,\mathbf e_3$, cioè $\{q_1,q_2,1,x^2\}$ è una base di $P_3$.

> [!note] Confronto col PDF
> Nel PDF la quarta riga è scritta come $(0,0,0,0,0,3)$ e la risposta è "aggiungere $\mathbf e_1$ ed $\mathbf e_4$", cioè $\{q_1,q_2,1,x^3\}$. Il conto corretto dà $(0,0,0,0,-1,3)$ e quindi $\mathbf e_3$; **ma anche la risposta del PDF è una base**: il determinante di $[\mathbf v_1|\mathbf v_2|\mathbf e_1|\mathbf e_4]$ si riduce (sviluppando lungo $\mathbf e_1,\mathbf e_4$) al minore delle righe $a_1,a_2$, $\det\begin{bmatrix}3&0\\3&3\end{bmatrix}=9\neq0$. È un'ulteriore conferma che il completamento non è unico.

---

### Riassunto

| Passo | Cosa fare |
|---|---|
| 0 | Controllare l'indipendenza dei vettori dati |
| 1 | (Se $V\ne K^n$) passare alle coordinate rispetto a una base comoda |
| 2 | Matrice $[\mathbf v_1|\cdots|\mathbf v_k|\mathbf e_1|\cdots|\mathbf e_n]$, vettori dati **prima** |
| 3 | MEG; prendere le colonne pivot della matrice **originale** |
| 4 | Tornare allo spazio originale con l'isomorfismo inverso |

Collegamenti: [[Basi, dimensione e coordinate]] · [[Dipendenza lineare]] · [[Basi di nucleo, immagine e span]] · applicazione ai complementi: [[Intersezione, somma e somma diretta di sottospazi — formula di Grassmann#Complemento di un sottospazio|Complemento di un sottospazio]]
