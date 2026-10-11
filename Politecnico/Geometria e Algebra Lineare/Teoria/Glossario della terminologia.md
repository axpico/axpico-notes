---
tags:
  - geometria-algebra-lineare
  - glossario
  - terminologia
---
## Glossario della terminologia (GAL)

Ordine alfabetico per area tematica. Ogni voce rimanda alla nota di teoria dove è sviluppata. Notazione: $\mathbb K$ = campo ($\mathbb R$ o $\mathbb C$), $V,W$ spazi vettoriali, $A\in M_{\mathbb K}(m,n)$ matrice $m\times n$.

---

### 1. Insiemi, logica, notazioni
*Fonte: [[Politecnico/Geometria e Algebra Lineare/Teoria/Insiemi, vettori e sistemi lineari — nozioni di base.md|Insiemi, vettori e sistemi lineari]]*

| Termine | Significato |
|---|---|
| **Insieme** | Collezione di oggetti (elementi) senza ordine né ripetizioni. |
| **Appartenenza $\in$** | $x\in X$: $x$ è un elemento di $X$. Non va confusa con $\subset$. |
| **Inclusione $\subset$ / $\subseteq$** | $A\subseteq B$: ogni elemento di $A$ sta in $B$ ($A$ è sottoinsieme di $B$). |
| **$=$ contro $:=$** | $=$ afferma un'uguaglianza da verificare; $:=$ *definisce* il simbolo a sinistra. |
| **$\mathbb N,\mathbb Z,\mathbb Q,\mathbb R,\mathbb C$** | Insiemi numerici: naturali, interi, razionali, reali, complessi. |
| **$\mathbb R^n$** | Insieme delle $n$-uple ordinate di numeri reali, $(x_1,\dots,x_n)$. |
| **$\mathbb C^n$** | Come $\mathbb R^n$ con componenti complesse. |
| **Quantificatori** | $\forall$ ("per ogni"), $\exists$ ("esiste"), $\exists!$ ("esiste ed è unico"). |
| **Campo $\mathbb K$** | Insieme di scalari con somma e prodotto "ben comportati" (qui $\mathbb R$ o $\mathbb C$). |
| **Scalare** | Elemento del campo $\mathbb K$, per distinguerlo dai vettori. |

---

### 2. Vettori geometrici
*Fonti: [[Politecnico/Geometria e Algebra Lineare/Teoria/Vettori geometrici liberi.md|Vettori geometrici liberi]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi di riferimento nel piano.md|Sistemi di riferimento nel piano]]*

| Termine | Significato |
|---|---|
| **Segmento orientato** | Segmento $AB$ con un verso (da $A$ a $B$): ha punto di applicazione, direzione, verso, lunghezza. |
| **Equivalenza di segmenti orientati** | $AB\sim CD$ se hanno stessa lunghezza, direzione e verso. |
| **Vettore (libero)** | Classe di equivalenza di segmenti orientati; il punto di applicazione non conta. |
| **Rappresentante** | Un segmento orientato della classe: si scrive $\vec v=\overrightarrow{AB}$. |
| **Traslazione** | Applicazione del piano/spazio in sé che sposta ogni punto $P$ in $P+\vec v$. |
| **Somma di vettori** | Regola del parallelogramma (o "punta-coda"). |
| **Vettore opposto** | $-\vec v$: stessa lunghezza e direzione, verso contrario; $\vec v+(-\vec v)=\vec 0$. |
| **Differenza** | $\vec u-\vec v:=\vec u+(-\vec v)$. |
| **Prodotto per scalare** | $\lambda\vec v$: ne cambia la lunghezza di un fattore $\lvert\lambda\rvert$ e il verso se $\lambda<0$. |
| **Vettore nullo** | $\vec 0$: elemento neutro della somma. |
| **Sistema di riferimento** | Un'origine $O$ e una base di vettori: associa a ogni punto delle coordinate. |
| **Coordinate di un punto** | Componenti di $\overrightarrow{OP}$ rispetto alla base del riferimento. |

---

### 3. Matrici e operazioni
*Fonti: [[Politecnico/Geometria e Algebra Lineare/Teoria/Operazioni tra matrici.md|Operazioni tra matrici]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]*

| Termine                                     | Significato                                                                                                                                                                                    |                         |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- |
| **Matrice $m\times n$**                     | Tabella con $m$ **righe** e $n$ **colonne**; $a_{ij}$ è l'elemento di posto $(i,j)$.                                                                                                           |                         |
| **Dimensione**                              | La coppia $m\times n$ (prima le righe).                                                                                                                                                        |                         |
| **Matrice riga / colonna**                  | Matrice con una sola riga ($1\times n$) / una sola colonna ($m\times 1$): rappresentano i vettori.                                                                                             |                         |
| **Somma, differenza, prodotto per scalare** | Definiti componente per componente (matrici della stessa dimensione).                                                                                                                          |                         |
| **Trasposta $A^{\mathsf T}$**               | Matrice $n\times m$ che scambia righe e colonne: $(A^{\mathsf T})_{ij}=a_{ji}$.                                                                                                                |                         |
| **Prodotto riga per colonna**               | $(AB)_{ij}=\sum_k a_{ik}b_{kj}$.                                                                                                                                                               |                         |
| **Compatibilità**                           | $AB$ esiste solo se colonne di $A$ = righe di $B$. Il prodotto in generale **non è commutativo**.                                                                                              |                         |
| **Matrice quadrata di ordine $n$**          | Matrice $n\times n$.                                                                                                                                                                           |                         |
| **Diagonale principale**                    | Gli elementi $a_{11},\dots,a_{nn}$.                                                                                                                                                            |                         |
| **Matrice diagonale**                       | Quadrata con zeri fuori dalla diagonale principale: $\operatorname{diag}(\lambda_1,\dots,\lambda_n)$.                                                                                          |                         |
| **Matrice triangolare**                     | Quadrata con zeri sotto (superiore) o sopra (inferiore) la diagonale.                                                                                                                          |                         |
| **Matrice identità $I_n$**                  | Diagonale con tutti $1$; elemento neutro del prodotto: $AI=IA=A$.                                                                                                                              |                         |
| **Matrice inversa $A^{-1}$**                | $B$ con $AB=BA=I_n$; se esiste è **unica**.                                                                                                                                                    |                         |
| **Invertibile / non singolare**             | Matrice quadrata che ammette inversa.                                                                                                                                                          |                         |
| **Singolare**                               | Matrice quadrata non invertibile.                                                                                                                                                              |                         |
| **Equazione matriciale**                    | Equazione con incognita matrice: $AX=B\Rightarrow X=A^{-1}B$; $YA=C\Rightarrow Y=CA^{-1}$ (se $A$ invertibile). Vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Equazioni matriciali.md\|Equazioni matriciali]]. |

---

### 4. Sistemi lineari e Gauss
*Fonti: [[Politecnico/Geometria e Algebra Lineare/Teoria/Insiemi, vettori e sistemi lineari — nozioni di base.md|nozioni di base]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Rouché-Capelli]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Eliminazione di Gauss-Jordan e calcolo della matrice inversa.md|Gauss-Jordan]]*

| Termine | Significato |
|---|---|
| **Sistema lineare** | $m$ equazioni nelle $n$ incognite con incognite di grado $1$: $\sum_j a_{ij}x_j=b_i$. |
| **Coefficienti $a_{ij}$** | Costanti che moltiplicano le incognite. |
| **Termini noti $b_i$** | Costanti a destra dell'uguale. |
| **Soluzione** | $n$-upla che soddisfa tutte le equazioni; $S$ = insieme delle soluzioni. |
| **Impossibile** | $S=\varnothing$. |
| **Determinato** | Una sola soluzione. |
| **Indeterminato** | Infinite soluzioni. |
| **Sistemi equivalenti** | Hanno lo stesso insieme di soluzioni. |
| **Sistema omogeneo** | $A\underline x=\underline 0$; ha sempre la soluzione banale $\underline 0$. |
| **Sistema quadrato** | $m=n$ (tante equazioni quante incognite). |
| **Matrice dei coefficienti $A$** | Contiene solo i coefficienti. |
| **Matrice completa (aumentata) $[A\mid B]$** | $A$ con affiancata la colonna dei termini noti. |
| **Operazioni elementari** | (i) scambio di due righe; (ii) moltiplicazione di una riga per $\lambda\neq0$; (iii) somma a una riga di un multiplo di un'altra. |
| **Equivalenza per righe** | $A\sim A'$ se si passa dall'una all'altra con operazioni elementari. |
| **Matrice a scala (per righe)** | Righe nulle in fondo, zeri iniziali strettamente crescenti nelle righe non nulle. |
| **Pivot** | Primo elemento non nullo di una riga non nulla di una matrice a scala. |
| **Variabile libera** | Incognita di una colonna **senza** pivot: fa da parametro nella soluzione. |
| **Variabile dipendente (pivotale)** | Incognita di una colonna con pivot. |
| **Rango $r(A)$** | Numero di pivot di una qualunque scala di $A$; ben definito. |
| **Teorema di Rouché–Capelli** | Il sistema è possibile $\iff r(A)=r([A\mid B])$; in tal caso le soluzioni dipendono da $n-r$ parametri liberi: $v_0+t_1v_1+\dots+t_{n-r}v_{n-r}$. |
| **Soluzione particolare $v_0$** | Una soluzione qualsiasi del sistema completo. |
| **Forma totalmente ridotta (RREF)** | Scala con pivot tutti $=1$ e zeri anche **sopra** ogni pivot; unica per ogni $A$. |
| **MEG-J** | Metodo di Eliminazione di Gauss-Jordan: porta $A$ alla RREF; applicato a $[A\mid I]$ dà $[I\mid A^{-1}]$. |

---

### 5. Determinante
*Fonti: [[Politecnico/Geometria e Algebra Lineare/Teoria/Determinante, sviluppo di Laplace e formula di Cramer.md|Determinante e Laplace]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari quadrati e teorema di Cramer.md|Cramer]]*

| Termine | Significato |
|---|---|
| **Determinante $\det A$** | Numero associato a una matrice quadrata; $\det A\neq0\iff A$ invertibile. |
| **Minore complementare $A_{ij}$** | Sottomatrice $(n-1)\times(n-1)$ ottenuta cancellando riga $i$ e colonna $j$. |
| **Complemento algebrico (cofattore) $C_{ij}$** | $(-1)^{i+j}\det A_{ij}$. |
| **Sviluppo di Laplace** | Calcolo di $\det A$ lungo una riga o colonna: $\det A=\sum_j a_{ij}C_{ij}$. |
| **Regola/Teorema di Cramer** | Se $\det A\neq0$, $x_i=\det A_i/\det A$, con $A_i$ = $A$ con la colonna $i$ sostituita da $B$. |
| **Matrice dei cofattori / aggiunta** | Costruita con i $C_{ij}$; $A^{-1}=\frac1{\det A}\,C^{\mathsf T}$. |
| **Minore di ordine $k$** | Determinante di una sottomatrice quadrata $k\times k$; il rango è l'ordine massimo di un minore non nullo. |

---

### 6. Spazi vettoriali
*Fonti: [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Combinazioni lineari e sottospazio generato.md|Combinazioni lineari]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Basi, dimensione e coordinate.md|Basi, dimensione e coordinate]]*

| Termine                                   | Significato                                                                                                                                   |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **Spazio vettoriale su $\mathbb K$**      | Insieme $V$ con somma e prodotto per scalare che soddisfano gli assiomi (associatività, commutatività, neutro, opposto, distributività, ...). |
| **Vettore** (senso astratto)              | Elemento di uno spazio vettoriale (anche matrici, funzioni, polinomi).                                                                        |
| **Sottospazio vettoriale $W\le V$**       | Sottoinsieme non vuoto, chiuso per somma e prodotto per scalare (contiene $\mathbf 0$).                                                       |
| **Chiusura**                              | Somma o multiplo di elementi di $W$ restano in $W$.                                                                                           |
| **Combinazione lineare**                  | $\alpha_1\vec v_1+\dots+\alpha_n\vec v_n$ con $\alpha_i\in\mathbb K$.                                                                         |
| **Sottospazio generato / span**           | $\operatorname{span}(\vec v_1,\dots,\vec v_n)$: insieme di tutte le combinazioni lineari; il **più piccolo** sottospazio che le contiene.     |
| **Insieme di generatori**                 | Vettori il cui span è $V$ ("generano $V$").                                                                                                   |
| **Linearmente indipendenti**              | $\sum\lambda_i\mathbf v_i=\mathbf 0\Rightarrow$ tutti $\lambda_i=0$.                                                                          |
| **Linearmente dipendenti**                | Esiste una combinazione non banale uguale a $\mathbf 0$: un vettore dipende dagli altri.                                                      |
| **Base $\mathcal B$**                     | Lista ordinata di vettori indipendenti che generano $V$.                                                                                      |
| **Coordinate $[\mathbf v]_{\mathcal B}$** | Coefficienti dell'unica scrittura di $\mathbf v$ nella base.                                                                                  |
| **Base canonica**                         | $\mathbf e_1,\dots,\mathbf e_n$ di $\mathbb K^n$.                                                                                             |
| **Dimensione $\dim V$**                   | Numero di elementi di una (qualunque) base (Steinitz); $\dim\{\mathbf 0\}=0$.                                                                 |
| **Dimensione finita**                     | $V$ ha una base finita.                                                                                                                       |
| **Matrici elementari $E_{ij}$**           | Base di $M_{\mathbb K}(m,n)$; da cui $\dim M_{\mathbb K}(m,n)=mn$.                                                                            |
| **Matrice simmetrica**                    | $A^{\mathsf T}=A$; le $2\times2$ formano un sottospazio di dimensione $3$.                                                                    |

---

### 7. Applicazioni e mappe lineari
*Fonti: [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni (terminologia generale).md|Applicazioni (terminologia generale)]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni lineari, nucleo e immagine.md|Applicazioni lineari, nucleo e immagine]], [[Politecnico/Geometria e Algebra Lineare/Teoria/Teorema di rappresentazione e matrice rappresentativa.md|Matrice rappresentativa]]*

| Termine | Significato |
|---|---|
| **Applicazione (funzione) $f:X\to Y$** | Regola che a ogni $x\in X$ associa un unico $f(x)\in Y$. |
| **Dominio / codominio** | $X$ / $Y$. |
| **Immagine di $x$** | $f(x)$. |
| **Controimmagine** | $f^{-1}(B)=\{x\in X: f(x)\in B\}$. |
| **Immagine dell'applicazione $\operatorname{im}f$** | $\{f(x):x\in X\}\subseteq Y$. |
| **Iniettiva** | $f(x)=f(x')\Rightarrow x=x'$ (immagini distinte per elementi distinti). |
| **Suriettiva** | $\operatorname{im}f=Y$ (ogni elemento di $Y$ è raggiunto). |
| **Biiettiva** | Iniettiva e suriettiva: ammette inversa $f^{-1}$. |
| **Composizione $g\circ f$** | Si applica prima $f$, poi $g$. |
| **Applicazione (mappa) lineare** | $\ell(\alpha\mathbf u+\beta\mathbf v)=\alpha\ell(\mathbf u)+\beta\ell(\mathbf v)$. |
| **Nucleo $\ker\ell$** | $\{\mathbf v\in V:\ell(\mathbf v)=\mathbf 0\}$; sottospazio di $V$. |
| **Immagine $\operatorname{im}\ell$** | $\ell(V)$; sottospazio di $W$. |
| **Criterio di iniettività** | $\ell$ iniettiva $\iff\ker\ell=\{\mathbf 0\}$. |
| **Isomorfismo** | Mappa lineare biiettiva; $V\cong W\iff\dim V=\dim W$. |
| **Teorema di rappresentazione** | Ogni mappa lineare $\mathbb K^n\to\mathbb K^m$ è $\mathbf x\mapsto A\mathbf x$ per una matrice $A$. |
| **Matrice rappresentativa** | La $A$ sopra: le **colonne** sono le immagini dei vettori della base canonica. |
| **Teorema rango–nullità** | $\dim V=\dim\ker\ell+\dim\operatorname{im}\ell$. |
| **Nullità** | $\dim\ker\ell$. |

---

### Simboli utili

| Simbolo | Lettura |
|---|---|
| $\iff$ | "se e solo se" |
| $\Rightarrow$ | "implica" |
| $\cong$ | "è isomorfo a" |
| $\le$ (tra spazi) | "è sottospazio di" |
| $\operatorname{span}$ | sottospazio generato |
| $\square$ | fine dimostrazione |
