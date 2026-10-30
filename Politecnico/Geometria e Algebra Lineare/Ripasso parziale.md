---
tags:
  - geometria-algebra-lineare
  - ripasso
---
# GAL — Ripasso per il parziale

↑ [[Politecnico/Geometria e Algebra Lineare/Indice|Indice]]

Tutti gli argomenti, con formule, metodi e trappole. Ogni sezione rimanda alla teoria completa.

## Cosa studiare prima

Priorità ricavate dalle due prove in itinere ([[Prova in itinere 11-11-2025|11-11-2025]] e [[Prova in itinere 13-11-2024 (Parte A)|13-11-2024]]). Sono solo due prove, quindi è un'indicazione e non una garanzia.

| Priorità | Argomento | Sezione |
|---|---|---|
| Alta | Mappa lineare: base dell'immagine, nucleo, controimmagine | 1 |
| Alta | Matrice rappresentativa con basi non canoniche | 2 |
| Alta | Intersezione e somma di sottospazi, Grassmann | 3 |
| Alta | Posizione reciproca di rette | 4 |
| Alta | Rette e piani: passare tra parametrica e cartesiana | 5 |
| Alta | Sistemi con parametro, rango, Rouché-Capelli | 6 |
| Media | Inversa, dimensioni dei prodotti | 7 |
| Media | Coordinate rispetto a una base | 8 |
| Media | Riconoscere un sottospazio | 9 |
| Bassa | Determinante e Cramer come teoria a sé | 10 |
| Bassa | Cambio di base con la formula completa | 11 |
| Bassa | Ortogonalità e fasci (non compaiono nelle due prove) | 12 |

---

## 1. Applicazioni lineari

Teoria: [[Applicazioni lineari, nucleo e immagine]], [[Basi di nucleo, immagine e span]], [[Rango e teorema di nullità più rango]]. Esempio completo: [[Parte B simulata — Esercizio svolto]].

**Lineare** significa $L(\lambda\mathbf u+\mu\mathbf v)=\lambda L(\mathbf u)+\mu L(\mathbf v)$. Test rapido: se $L(\mathbf 0)\ne\mathbf 0$, oppure compaiono $x^2$, $xy$ o costanti, non è lineare.

**Nullità più rango.**
$$\boxed{\dim\ker L+\dim\operatorname{Im}L=\dim(\text{dominio})}$$

**Iniettiva e suriettiva.**
- Iniettiva $\iff\ker L=\{\mathbf 0\}\iff r(L)=\dim V$.
- Suriettiva $\iff r(L)=\dim W$.

**Solo dalle dimensioni**, con $L:V\to W$:

| Caso | Conclusione sicura |
|---|---|
| $\dim V>\dim W$ | non è iniettiva |
| $\dim V<\dim W$ | non è suriettiva |
| $\dim V=\dim W$ | iniettiva $\iff$ suriettiva $\iff$ isomorfismo |

Il contrario non è garantito: con $\dim V<\dim W$, $L$ può essere iniettiva oppure no.

**Base dell'immagine.**
1. Calcola le immagini di una base del dominio, in coordinate.
2. Mettile in colonna e riduci per righe.
3. Prendi le colonne pivot **della matrice di partenza**.

**Base del nucleo.** Risolvi $A\mathbf x=\mathbf 0$ e assegna a turno 1 a una variabile libera e 0 alle altre.

**Controimmagine.** Le soluzioni di $L(\mathbf v)=p$ sono: vuote se $p\notin\operatorname{Im}L$, altrimenti $\mathbf v_0+\ker L$. Con $\dim\ker L=1$ si ottiene una retta.

**Uguaglianza tra polinomi.** $L(\mathbf v)=F(\mathbf v)$ si risolve uguagliando i coefficienti potenza per potenza. L'insieme ottenuto è il sottospazio $\ker(L-F)$.

**Trappola.** $\mathbf 0\in\ker L$ sempre, e il teorema usa la dimensione del **dominio**, non del codominio.

---

## 2. Matrice rappresentativa

Teoria: [[Teorema di rappresentazione e matrice rappresentativa]].

**Dimensioni.** Se $\dim V=n$ e $\dim W=m$, la matrice è $m\times n$: righe dall'arrivo, colonne dalla partenza.

**Ricetta.**
1. Calcola $L(\mathbf v_j)$ per ogni vettore della base di partenza.
2. Scrivi ogni immagine in coordinate rispetto alla base di **arrivo**.
3. Mettile in colonna, nell'ordine dato.

**Con basi canoniche.** Le colonne sono le immagini dei vettori canonici.

**Uso.**
$$[L(\mathbf v)]_{\mathcal C}=M^{\mathcal B}_{\mathcal C}(L)\,[\mathbf v]_{\mathcal B}$$

La matrice lavora **solo sulle coordinate**. Quindi per calcolare $L(\mathbf v)$ devi fare il giro: vettore, poi coordinate in $\mathcal B$, poi matrice, poi di nuovo vettore. Schema: [[Giro matrice rappresentativa.svg]].

**Esempio.** $\mathcal B=\{(1,0),(1,1)\}$, $M=\begin{bmatrix}1&2\\0&1\end{bmatrix}$. Allora $(3,1)$ ha coordinate $(2,1)$, $M(2,1)^T=(4,1)^T$, e $F(3,1)=4(1,0)+(1,1)=(5,1)$.

**Composizione.** $M(g\circ f)=M(g)M(f)$.

**Trappola.** Il risultato di $M[\mathbf v]_{\mathcal B}$ è ancora in coordinate, non è il vettore.

---

## 3. Somma e intersezione di sottospazi

Teoria: [[Intersezione, somma e somma diretta di sottospazi — formula di Grassmann]]. Tutti i casi con figura: [[Due sottospazi in R1, R2, R3.html]].

**Grassmann.**
$$\boxed{\dim(U+W)=\dim U+\dim W-\dim(U\cap W)}$$

**Somma.** $U+W$ è lo span dei generatori uniti. La sua dimensione è il rango della matrice con tutti i generatori.

**Intersezione**, secondo come sono dati:

| $U$ | $W$ | Metodo |
|---|---|---|
| equazioni | equazioni | metti tutte le equazioni in un solo sistema |
| span | equazioni | prendi il vettore generico di $U$ e sostituiscilo nelle equazioni di $W$ |
| span | span | uguaglia i vettori generici, oppure trova prima le equazioni di uno dei due |

**Esempio span e span.** $U=\operatorname{span}\{(1,0,1),(0,1,1)\}$ e $W=\operatorname{span}\{(1,1,0),(0,0,1)\}$. I generici sono $(\alpha,\beta,\alpha+\beta)$ e $(\gamma,\gamma,\delta)$. Uguagliando: $\alpha=\beta=\gamma$ e $\delta=2\alpha$. Quindi $U\cap W=\operatorname{span}\{(1,1,2)\}$, dimensione 1. Grassmann dà $\dim(U+W)=2+2-1=3$.

**Se $\dim H=1$:** $H\cap K$ è $H$ se il generatore di $H$ sta in $K$, altrimenti è $\{\mathbf 0\}$.

**Somma diretta.** $U\oplus W$ significa $U\cap W=\{\mathbf 0\}$, e allora $\dim(U+W)=\dim U+\dim W$.

**Complemento.** $U$ tale che $U\oplus W=V$. Ha dimensione $\dim V-\dim W$ e non è unico. Si trova completando a base una base di $W$.

**Complemento ortogonale.** $W^\perp$ contiene i vettori ortogonali a tutti i generatori di $W$. Vale $\dim W^\perp=n-\dim W$. Il piano $ax+by+cz=0$ ha come $W^\perp$ la retta $\operatorname{span}(a,b,c)$.

**Controlli rapidi.**
- $\dim(U+W)\le n$ e $\dim(U\cap W)\le\min(\dim U,\dim W)$.
- Due piani per l'origine in $\mathbb R^3$ si tagliano almeno in una retta.

**Trappola.** Tre generatori non significano dimensione 3: riduci sempre prima.

---

## 4. Posizione reciproca

Teoria: [[Posizione reciproca di rette e piani]]. Interattivo: [[Lezione 7 — Rette, piani, ortogonalità e fasci.html]].

**Due rette, due domande:** le direzioni sono proporzionali? Hanno un punto in comune?

| Direzioni | Punto comune | Posizione |
|---|---|---|
| proporzionali | sì | coincidenti |
| proporzionali | no | parallele in senso stretto |
| non proporzionali | sì | incidenti |
| non proporzionali | no | sghembe (solo in $\mathbb R^3$) |

**Metodo.**
1. Metti entrambe in forma parametrica, con **due parametri diversi**.
2. Confronta le direzioni. Se sono proporzionali, controlla un solo punto.
3. Altrimenti uguaglia le componenti e risolvi il sistema.

**Con il rango**, per $[\mathbf a_1|-\mathbf a_2]\binom ts=\mathbf r_2-\mathbf r_1$:

| $r(A)$ | $r([A\vert\mathbf b])$ | Posizione |
|---|---|---|
| 2 | 2 | incidenti |
| 2 | 3 | sghembe |
| 1 | 1 | coincidenti |
| 1 | 2 | parallele |

**Due piani:** $r(A)=2$ si tagliano in una retta. $r(A)=1$ e $r([A|\mathbf b])=2$ paralleli. Entrambi 1, coincidenti.

**Retta $\mathbf r_0+t\mathbf a$ e piano $ax+by+cz=d$:** sostituisci la parametrica nell'equazione.

| Risultato in $t$ | Posizione |
|---|---|
| soluzione unica | incidente |
| equazione impossibile | parallela |
| sempre vera | contenuta |

---

## 5. Rette e piani

Teoria: [[Rette e piani — equazioni parametriche e cartesiane]]. Guida: [[Lezione 7 — Guida con esempi.html]].

| Oggetto | Parametrica | Cartesiana |
|---|---|---|
| retta in $\mathbb R^2$ | $\mathbf r_0+t\mathbf a$ | 1 equazione |
| retta in $\mathbb R^3$ | $\mathbf r_0+t\mathbf a$ | 2 equazioni indipendenti |
| piano in $\mathbb R^3$ | $\mathbf r_0+t\mathbf u+s\mathbf v$ | 1 equazione |

**Numero di equazioni** = dimensione dello spazio − numero di parametri.

**Da cartesiana a parametrica.** Riduci il sistema e dai un parametro a ogni variabile libera.

**Da parametrica a cartesiana.** Ricava i parametri e sostituiscili.

Esempio: $(1,0,0)+s(1,1,0)+t(0,1,1)$ dà $x=1+s$, $y=s+t$, $z=t$. Quindi $s=x-1$, $t=z$, e $x-y+z=1$.

**Passa per l'origine?** Una retta o un piano è un sottospazio solo se il termine noto è zero.

**Controllo.** Il punto deve soddisfare l'equazione, e le direzioni devono dare 0 a primo membro.

---

## 6. Rango e sistemi lineari

Teoria: [[Sistemi lineari e teorema di Rouché-Capelli]], [[Rango e teorema di nullità più rango]].

**Rango.** Numero di pivot della forma a scala. Equivale a:
$$r(A)=\dim\operatorname{Col}A=\dim\operatorname{Row}A=\text{massimo ordine di un minore non nullo},\qquad r(A)\le\min(m,n).$$

**Rouché-Capelli**, per $A\mathbf x=\mathbf b$ con $n$ incognite:

| Condizione | Soluzioni |
|---|---|
| $r(A)<r([A\vert\mathbf b])$ | nessuna |
| $r(A)=r([A\vert\mathbf b])=n$ | una sola |
| $r(A)=r([A\vert\mathbf b])<n$ | infinite, con $n-r$ parametri |

Le soluzioni hanno la forma: soluzione particolare + soluzioni dell'omogeneo. Un sistema omogeneo ha sempre almeno $\mathbf x=\mathbf 0$.

**Sistema con parametro, quadrato.**
1. Calcola $\det A$ in funzione di $k$ e fattorizzalo.
2. Dove $\det A\ne0$ la soluzione è unica.
3. Sostituisci ogni valore critico di $k$ e riduci $[A|\mathbf b]$.

**Esempio.** $x+ky+z=1,\ kx+y+z=1,\ x+y+kz=1$. Vale $\det A=-(k-1)^2(k+2)$.
- $k\ne1,-2$: soluzione unica.
- $k=1$: una sola equazione, $x+y+z=1$, quindi infinite soluzioni con 2 parametri.
- $k=-2$: sommando le equazioni si ottiene $0=3$, quindi nessuna soluzione.

**Trappola.** Non dividere per un'espressione in $k$ senza controllare quando si annulla.

---

## 7. Matrici

Teoria: [[Operazioni tra matrici]], [[Matrici quadrate e matrice inversa]], [[Eliminazione di Gauss-Jordan e calcolo della matrice inversa]], [[Equazioni matriciali]].

**Prodotto.** $A_{m\times n}B_{p\times q}$ esiste solo se $n=p$, e il risultato è $m\times q$. La trasposta scambia le dimensioni: $A\in M(m,n)\Rightarrow A^T\in M(n,m)$.

**Formule.**
$$(AB)^T=B^TA^T,\qquad (AB)^{-1}=B^{-1}A^{-1},\qquad (A^{-1})^{-1}=A$$
$$\begin{bmatrix}a&b\\c&d\end{bmatrix}^{-1}=\frac1{ad-bc}\begin{bmatrix}d&-b\\-c&a\end{bmatrix}\qquad(ad-bc\ne0)$$

**Inversa con Gauss-Jordan.** Riduci $[A\,|\,I]$ fino a $[I\,|\,A^{-1}]$. Se a sinistra compare una riga nulla, $A$ non è invertibile.

**Equazioni matriciali** con $A$ invertibile:
$$AX=B\Rightarrow X=A^{-1}B,\qquad YA=C\Rightarrow Y=CA^{-1}.$$

**Sistema quadrato.** Se $A$ è invertibile, $A\mathbf x=\mathbf b$ ha l'unica soluzione $\mathbf x=A^{-1}\mathbf b$.

**Trappole.**
- $AB\ne BA$ in generale, quindi il lato su cui moltiplichi conta.
- $(AB)^{-1}\ne A^{-1}B^{-1}$: l'ordine si inverte.

---

## 8. Indipendenza, basi e coordinate

Teoria: [[Dipendenza lineare]], [[Basi, dimensione e coordinate]], [[Completamento a base]].

**Indipendenza.** $\mathbf v_1,\dots,\mathbf v_k$ sono indipendenti se $\sum c_i\mathbf v_i=\mathbf 0$ solo con tutti i $c_i=0$. In pratica:
$$\text{indipendenti}\iff r([\mathbf v_1|\cdots|\mathbf v_k])=k.$$

**Fuori da $\mathbb K^n$.** Con polinomi o matrici, passa alle coordinate: l'indipendenza si conserva.

**Base.** Insieme indipendente che genera. Se $\dim V=n$, bastano $n$ vettori indipendenti. Più di $n$ vettori sono sempre dipendenti.

**Coordinate.** $[\mathbf v]_{\mathcal B}=(c_1,\dots,c_n)$ se $\mathbf v=\sum c_i\mathbf v_i$. Si trovano risolvendo un sistema.

**La base che torna spesso.** Rispetto a $\{1+x^2,\ x,\ 1-x^2\}$, il polinomio $c_0+c_1x+c_2x^2$ ha coordinate
$$\alpha=\frac{c_0+c_2}2,\qquad\beta=c_1,\qquad\gamma=\frac{c_0-c_2}2.$$

**Completare a base.** Metti in colonna i vettori dati, poi la base canonica: $[\mathbf v_1|\cdots|\mathbf v_k|\mathbf e_1|\cdots|\mathbf e_n]$. Riduci e prendi le colonne pivot della matrice di partenza. I vettori dati vanno messi **per primi**.

**Esempio.** Completare $(1,1,0),(0,1,1)$ in $\mathbb R^3$: i pivot sono nelle colonne 1, 2, 3, quindi si aggiunge $\mathbf e_1$.

---

## 9. Spazi vettoriali e sottospazi

Teoria: [[Spazi vettoriali e sottospazi]], [[Combinazioni lineari e sottospazio generato]].

**Dimensioni da sapere.**

| Spazio | Dimensione |
|---|---|
| $\mathbb R^n$ | $n$ |
| $M(m,n)$ | $mn$ |
| $\mathbb R[x]_{\le n}$ | $n+1$ |

**Criterio.** $W\subseteq V$ è sottospazio se contiene $\mathbf 0$ ed è chiuso per somma e per prodotto per scalare.

**Test veloce.** Controlla prima lo zero: se manca, hai finito. Se la condizione non è lineare, cerca un controesempio.

| Sottoinsieme | Sottospazio? | Motivo |
|---|---|---|
| soluzioni di $A\mathbf x=\mathbf 0$ | sì | è un nucleo |
| soluzioni di $A\mathbf x=\mathbf b$, $\mathbf b\ne\mathbf 0$ | no | manca lo zero |
| $\{A=A^T\}$ | sì | |
| $\{\operatorname{tr}A=0\}$ | sì | |
| $\{\operatorname{tr}A=1\}$ | no | manca lo zero |
| $\{\det A=0\}$ | no | non è chiuso per somma |
| $\{\operatorname{rk}A<3\}$ in $M(3,3)$ | no | non è chiuso per somma |
| $\{\operatorname{rk}A=0\}$ | sì | è solo la matrice nulla |
| $\{x,y\ge0\}$ | no | $\lambda=-1$ fa uscire |
| $U\cup W$ | in generale no | |
| $U\cap W$ e $U+W$ | sì | |

---

## 10. Determinante e Cramer

Teoria: [[Determinante, sviluppo di Laplace e formula di Cramer]], [[Sistemi lineari quadrati e teorema di Cramer]].

**Laplace** lungo la riga $i$: $\det A=\sum_j(-1)^{i+j}a_{ij}\det A_{ij}$, dove $A_{ij}$ è $A$ senza riga $i$ e colonna $j$. Scegli la riga o la colonna con più zeri.

**Proprietà.**
- $\det A^T=\det A$ e $\det(AB)=\det A\det B$ (Binet).
- $\det(\lambda A)=\lambda^n\det A$, non $\lambda\det A$.
- Scambiare due righe cambia il segno. Sommare a una riga un multiplo di un'altra non cambia nulla.
- Due righe proporzionali o una riga nulla danno $\det A=0$.
- Una matrice triangolare ha come determinante il prodotto della diagonale.

**Criterio.** $A$ quadrata è invertibile $\iff\det A\ne0\iff r(A)=n$.

**Cramer.** Se $\det A\ne0$: $x_i=\dfrac{\det A_i}{\det A}$, dove $A_i$ è $A$ con la colonna $i$ sostituita da $\mathbf b$.

---

## 11. Cambio di base

Teoria: [[Cambio di base e matrice di passaggio]]. Interattivo: [[Cambio di base.html]].

**Matrice di passaggio** $S$ da $\mathcal B$ a $\widetilde{\mathcal B}$: le colonne sono i vettori **nuovi** in coordinate **vecchie**.
$$\mathbf c=S\tilde{\mathbf c},\qquad\tilde{\mathbf c}=S^{-1}\mathbf c.$$

**Matrice rappresentativa.**
$$\widetilde A=S_W^{-1}AS_V,\qquad\text{per un endomorfismo}\quad\widetilde A=S^{-1}AS.$$

Si legge da destra: converti l'input da nuove a vecchie, applica $A$, converti l'output da vecchie a nuove.

**Trappola.** $S$ va "da $\mathcal B$ a $\widetilde{\mathcal B}$" come nome, ma trasforma le coordinate nuove in vecchie.

---

## 12. Ortogonalità e fasci

Teoria: [[Ortogonalità e fasci di rette e piani]].

**Prodotto scalare** in riferimento cartesiano: $\mathbf x\cdot\mathbf y=\mathbf x^T\mathbf y$, e $\mathbf x\perp\mathbf y\iff\mathbf x\cdot\mathbf y=0$.

**Normale.** Il piano $ax+by+cz=d$ ha normale $\mathbf n=(a,b,c)$.

| Obiettivo | Condizione |
|---|---|
| retta $\perp$ piano | direzione proporzionale a $\mathbf n$ |
| retta $\parallel$ piano | $\mathbf n\cdot\mathbf a=0$ |
| piani $\perp$ | $\mathbf n_1\cdot\mathbf n_2=0$ |
| piani $\parallel$ | $\mathbf n_1$ proporzionale a $\mathbf n_2$ |

**Fasci di piani.**
- Paralleli a $ax+by+cz=d$: $ax+by+cz=g$, con $g$ libero.
- Per la retta $E_1=E_2=0$: $pE_1+qE_2=0$, con $(p,q)\ne(0,0)$.
- Per il punto $P_0$: $a(x-x_0)+b(y-y_0)+c(z-z_0)=0$.

**Esempio.** Piano per la retta $x+y-z-1=0,\ x-z=0$ e per $(1,2,0)$. Il punto dà $2p+q=0$. Con $p=1,\ q=-2$ si ottiene $-x+y+z-1=0$.

**Trappola.** Rette sghembe possono avere direzioni ortogonali: ortogonali non vuol dire incidenti.

---

## Trucchi per il test

- **Sostituisci i valori delle opzioni.** Se le risposte citano già $k=1$ o $k=-2$, provali senza calcolare il determinante.
- **Inversa a crocette.** Moltiplica $A$ per l'opzione e controlla una sola colonna: ne escludi subito molte.
- **Matrice rappresentativa.** Prima controlla le dimensioni $m\times n$, poi calcola una sola colonna, la più discriminante.
- **Coordinate.** Ricombina ogni opzione con la base e guarda se ritrovi il vettore.
- **"Sicuramente".** Domande su iniettiva o suriettiva: confronta le dimensioni e basta.
- **Rette.** Confronta prima le direzioni: spesso restano solo due opzioni.
- **Parte B.** Verifica ogni risultato sostituendolo nel testo. Costa poco e trova quasi tutti gli errori.
