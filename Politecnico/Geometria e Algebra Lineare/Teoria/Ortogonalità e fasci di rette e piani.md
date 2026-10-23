---
tags:
  - geometria-algebra-lineare
  - rette-e-piani
  - ortogonalità
  - fasci
---
## Ortogonalità e fasci di rette e piani

↑ [[Politecnico/Geometria e Algebra Lineare/Indice|Indice]] · tappa 6 (Geometria analitica) · prima: [[Posizione reciproca di rette e piani|Posizione reciproca di rette e piani]]

> Fonte: [[07 Lezione 7 NUOVA (parte 2).pdf|Lezione 7 (parte 2, PDF)]] (Addendum: ortogonalità, pp. 1–15) e [[07 Lezione 7 NUOVA (parte 3).pdf|Lezione 7 (parte 3, PDF)]] (Addendum 2: fasci, pp. 16–30).

**Idea.** Fin qui abbiamo usato solo la struttura *affine* (punti, direzioni, parallelismo). L'ortogonalità richiede una nozione di **angolo**, quindi una metrica: se il riferimento è cartesiano ortonormale, l'angolo retto si legge sulle coordinate tramite il prodotto scalare standard. Un **fascio** è invece una famiglia di rette/piani descritta da un'equazione con parametri: invece di cercare "il" piano, si scrive la famiglia di quelli che soddisfano già alcune condizioni e si impongono le restanti come equazioni nei parametri.

---

### Parte 1 — Ortogonalità

#### Riferimento cartesiano

**Convenzione.** In tutta questa parte le coordinate sono prese rispetto a un **riferimento cartesiano** (ortonormale):
- nel piano $(O,\vec u,\vec v)$ con $|\vec u|=|\vec v|=1$, $\vec u\perp\vec v$;
- nello spazio $(O,\vec v_1,\vec v_2,\vec v_3)$ con $|\vec v_i|=1$ e $\vec v_i\perp\vec v_j$ per $i\ne j$.

**Fatto fondamentale.** Sotto questa convenzione, due vettori non nulli $\vec a,\vec b$ formano un angolo di $90^\circ$ ($\vec a\perp\vec b$) se e solo se i loro vettori delle coordinate $\mathbf x,\mathbf y\in\mathbb R^n$ ($n=2,3$) soddisfano
$$\boxed{\ \mathbf x^T\mathbf y=x_1y_1+\dots+x_ny_n=0\ }$$
cioè il loro **prodotto scalare standard** è nullo.

> **Perché serve il riferimento ortonormale.** Il prodotto scalare geometrico vale $\vec a\cdot\vec b=|\vec a||\vec b|\cos\theta$. Scrivendo $\vec a=\sum x_i\vec v_i$, $\vec b=\sum y_j\vec v_j$ e usando la bilinearità, $\vec a\cdot\vec b=\sum_{i,j}x_iy_j\,(\vec v_i\cdot\vec v_j)$. Se la base è ortonormale, $\vec v_i\cdot\vec v_j=\delta_{ij}$ (1 se $i=j$, 0 altrimenti) e resta $\sum x_iy_i=\mathbf x^T\mathbf y$. In una base qualsiasi compaiono anche i termini misti: la formula "componente per componente" **non** misura l'angolo.

Terminologia: "perpendicolare" = "ortogonale", simbolo $\perp$.

#### Vettore ortogonale a un piano

Sia $\Pi:\ ax+by+cz=d\quad(1)$, con $(a,b,c)\neq\mathbf 0$. Quando un vettore $\vec u$ è perpendicolare a $\Pi$?

1. $\vec u\perp\Pi\iff\vec u\perp\overrightarrow{AB}$ per ogni $A,B\in\Pi$.
2. Se $A,B\in\Pi$, i vettori posizione $\mathbf r_A,\mathbf r_B$ soddisfano (1); sottraendo, $\overrightarrow{AB}=\mathbf r_B-\mathbf r_A$ soddisfa l'**equazione omogenea associata**
$$ax+by+cz=0.\tag{2}$$
3. Il primo membro di (2) è $[x\ y\ z]\begin{pmatrix}a\\b\\c\end{pmatrix}$, quindi $(2)\iff(x,y,z)\perp(a,b,c)$. Dunque ogni $\overrightarrow{AB}$ è ortogonale a $(a,b,c)$.
4. Due vettori non nulli perpendicolari allo stesso piano sono paralleli tra loro.

> **Conclusione.** $\vec u\perp\Pi:\ ax+by+cz=d\iff\vec u$ è un **multiplo di $\mathbf n=(a,b,c)$**. Il vettore dei coefficienti si chiama **vettore normale** al piano.

**Lettura in chiave di algebra lineare.** Le direzioni del piano formano il sottospazio $\ker\,[a\ b\ c]$, di dimensione $3-1=2$ (nullità + rango). Il vettore normale genera il suo **complemento ortogonale**, di dimensione 1. Ne seguono i due criteri operativi:

| Condizione | Criterio sulle coordinate |
|---|---|
| $\vec v\perp\Pi$ (retta di direzione $\vec v$ **ortogonale** a $\Pi$) | $\vec v=\lambda(a,b,c)$ |
| $\vec v\parallel\Pi$ (retta di direzione $\vec v$ **parallela** a $\Pi$, in senso largo) | $a v_x+b v_y+c v_z=0$, cioè $\vec v$ risolve la (2) |

Parallela "in senso largo" comprende anche il caso $\ell\subset\Pi$. Per il **senso stretto** ($\ell\cap\Pi=\emptyset$) basta verificare in più che un punto di $\ell$ **non** stia su $\Pi$. Se invece $\vec v$ non risolve la (2), la retta non è parallela e quindi incontra $\Pi$ in **un unico punto** (cfr. [[Posizione reciproca di rette e piani|Parte 4 retta–piano]]).

**Esempio 1 (quale retta è ortogonale, quale parallela?).**
$$\ell_1:\ \mathbf r=\begin{pmatrix}1\\0\\1\end{pmatrix}+t\begin{pmatrix}1\\1\\-2\end{pmatrix},\quad\ell_2:\ \mathbf r=\begin{pmatrix}1\\2\\3\end{pmatrix}+t\begin{pmatrix}1\\1\\1\end{pmatrix},\quad\ell_3:\ \mathbf r=\begin{pmatrix}1\\1\\2\end{pmatrix}+t\begin{pmatrix}1\\0\\1\end{pmatrix},\qquad\Pi:\ 2z-x-y=2.$$
- Forma standard: $-x-y+2z=2$, quindi $\mathbf n=(-1,-1,2)$.
- **Ortogonalità.** Tra $\vec v_1=(1,1,-2)$, $\vec v_2=(1,1,1)$, $\vec v_3=(1,0,1)$, solo $\vec v_1=-\mathbf n$ è multiplo di $\mathbf n$. Quindi $\ell_1\perp\Pi$, mentre $\ell_2\not\perp\Pi$ e $\ell_3\not\perp\Pi$.
- **Parallelismo.** Equazione omogenea associata: $-x-y+2z=0\quad(3)$.
  - $\vec v_2$: $-1-1+2=0$ ✓, quindi $\ell_2\parallel\Pi$ in senso largo. Anzi in **senso stretto**: $(1,2,3)\in\ell_2$ ma $-1-2+6=3\neq2$, cioè $(1,2,3)\notin\Pi$.
  - $\vec v_1$: $-1-1-4=-6\neq0$; $\vec v_3$: $-1+0+2=1\neq0$. Quindi $\ell_1$ ed $\ell_3$ **non** sono parallele a $\Pi$ e lo intersecano in un unico punto (per $\ell_1$ è ovvio: una retta ortogonale a un piano lo buca sempre).

**Esempio 2 (retta per un punto, ortogonale a un piano).** Trovare le equazioni cartesiane di $\ell\perp\Pi:\ x+y+z=1$ passante per $P(0,1,2)$.
- La direzione di $\ell$ è il vettore normale $\vec v=(1,1,1)$, quindi
$$\ell:\ \mathbf r=\mathbf r_P+t\vec v=\begin{pmatrix}0\\1\\2\end{pmatrix}+t\begin{pmatrix}1\\1\\1\end{pmatrix}\iff\begin{cases}x=t\\y=1+t\\z=2+t\end{cases}\quad t\in\mathbb R.$$
- Si elimina il parametro ($t=x$): $y=1+x$, $z=2+x$, cioè
$$\boxed{\ \ell:\ x-y+1=x-z+2=0\ }$$
(due equazioni indipendenti: una retta nello spazio ha codimensione 2).

**Esempio 3 (due rette incidenti e ortogonali).** Verificare che
$$\ell_1:\ \mathbf r=\begin{pmatrix}1\\3\\2\end{pmatrix}+t\begin{pmatrix}1\\2\\1\end{pmatrix},\qquad\ell_2:\ \mathbf r=\begin{pmatrix}1\\0\\2\end{pmatrix}+s\begin{pmatrix}1\\-1\\1\end{pmatrix}$$
sono incidenti e formano un angolo retto.
- **Incidenza.** Si impone $\mathbf r_1+t\vec v_1=\mathbf r_2+s\vec v_2$, cioè $t\vec v_1+s(-\vec v_2)=\mathbf r_2-\mathbf r_1$:
$$t\begin{pmatrix}1\\2\\1\end{pmatrix}+s\begin{pmatrix}-1\\1\\-1\end{pmatrix}=\begin{pmatrix}0\\-3\\0\end{pmatrix},\qquad\left(\begin{array}{cc|c}1&-1&0\\2&1&-3\\1&-1&0\end{array}\right)\xrightarrow[R_3\to R_3-R_1]{R_2\to R_2-2R_1}\left(\begin{array}{cc|c}\boxed1&-1&0\\0&\boxed3&-3\\0&0&0\end{array}\right).$$
  $r(A)=r([A|\mathbf b])=2=\#$incognite, quindi c'è soluzione unica e le rette sono **incidenti**. Esplicitamente $s=-1$, $t=-1$, e il punto è $(1,3,2)-(1,2,1)=(0,1,1)$ (controllo: $(1,0,2)-(1,-1,1)=(0,1,1)$ ✓).
- **Ortogonalità.** $\vec v_1\cdot\vec v_2=[1\ 2\ 1]\begin{pmatrix}1\\-1\\1\end{pmatrix}=1-2+1=0$, quindi $\vec v_1\perp\vec v_2$ e $\ell_1\perp\ell_2$.

> **Attenzione.** Nello spazio "ortogonali" si riferisce alle **direzioni**: due rette sghembe possono avere direzioni ortogonali. Per questo l'esercizio chiede di verificare *separatamente* incidenza (Rouché–Capelli) e ortogonalità (prodotto scalare).

---

### Parte 2 — Fasci di rette e piani

**Definizione.** Un **fascio** di rette (o di piani) è un insieme di rette (o piani) descritto da una o più equazioni contenenti uno o più **parametri**.

**Esempio (fascio di rette per un punto, nel piano).** Le rette per $P(2,1)$ sono
$$a(x-2)+b(y-1)=0,\qquad(a,b)\neq(0,0)\ \ (a^2+b^2\neq0).$$
I parametri sono **omogenei**: $(a,b)$ e $(\lambda a,\lambda b)$, con $\lambda\neq0$, danno la stessa retta. Il fascio dipende quindi da *un solo* grado di libertà effettivo, la direzione del vettore normale $(a,b)$.

#### (1) Fascio dei piani paralleli a un piano dato

Sia $\Pi_0:\ ax+by+cz=d$. Allora $\Pi_0\perp\mathbf u:=(a,b,c)$, quindi il fascio dei piani $\parallel\Pi_0$ coincide con il fascio dei piani $\perp\mathbf u$.

Il piano per $P_0(x_0,y_0,z_0)$ ortogonale a $\mathbf u$ è il luogo dei $P(x,y,z)$ con $\overrightarrow{P_0P}\perp\mathbf u$:
$$[x-x_0\ \ y-y_0\ \ z-z_0]\begin{pmatrix}a\\b\\c\end{pmatrix}=0\iff a(x-x_0)+b(y-y_0)+c(z-z_0)=0\iff ax+by+cz=g,$$
con $g:=ax_0+by_0+cz_0$. Facendo variare $P_0$, $g$ assume ogni valore reale:

> $$\boxed{\ \text{piani}\parallel\Pi_0:\quad ax+by+cz=g,\qquad g\in\mathbb R\ \text{parametro}\ }$$
> Stessi coefficienti $(a,b,c)$ di $\Pi_0$, termine noto libero. È un **fascio improprio** (i piani non hanno punti in comune).

**Esempio.** Fascio dei piani paralleli a $\Pi_0:\ x+y+z=1$, e piano del fascio che contiene la retta $\ell:\ x+2y-1=x+2z+1=0$.
- Fascio: $x+y+z=g$.
- $\ell\subset\Pi\iff\ell\cap\Pi$ ha **infiniti** punti. Il sistema è
$$\begin{cases}x+2y=1\\x+2z=-1\\x+y+z=g\end{cases}\qquad\left(\begin{array}{ccc|c}1&2&0&1\\1&0&2&-1\\1&1&1&g\end{array}\right)\xrightarrow[R_3\to R_3-R_1]{R_2\to R_2-R_1}\left(\begin{array}{ccc|c}1&2&0&1\\0&-2&2&-2\\0&-1&1&g-1\end{array}\right)\xrightarrow{R_3\to R_3-\frac12R_2}\left(\begin{array}{ccc|c}1&2&0&1\\0&-2&2&-2\\0&0&0&g\end{array}\right).$$
- $r(A)=2$ sempre. Se $g\neq0$, $r([A|\mathbf b])=3$: nessuna soluzione ($\ell$ parallela al piano ma non contenuta). Se $g=0$, $r=2<3$: infinite soluzioni.
- **Risposta:** $\Pi:\ x+y+z=0$.
- *Controllo.* La direzione di $\ell$ si ottiene da $\ker\begin{pmatrix}1&2&0\\1&0&2\end{pmatrix}$ ed è $\propto(2,-1,-1)$, ortogonale a $(1,1,1)$ ✓. Il punto $(-1,1,0)\in\ell$ soddisfa $x+y+z=0$ ✓.

#### (2) Fascio dei piani passanti per una retta

Data la retta (in forma cartesiana)
$$\ell:\ a_1x+b_1y+c_1z+d_1=a_2x+b_2y+c_2z+d_2=0,$$
il **fascio proprio** di asse $\ell$ è
$$\boxed{\ p\,(a_1x+b_1y+c_1z+d_1)+q\,(a_2x+b_2y+c_2z+d_2)=0,\qquad p^2+q^2\neq0\ }$$

> **Perché funziona (e perché li dà tutti).**
> - *Ogni piano del fascio contiene $\ell$:* se $P\in\ell$ annulla entrambe le parentesi, annulla anche la loro combinazione. Serve $(p,q)\ne(0,0)$; inoltre la combinazione ha coefficienti $(x,y,z)$ non tutti nulli perché le due normali sono indipendenti (altrimenti $\ell$ non sarebbe una retta).
> - *Ogni piano $\Pi$ contenente $\ell$ è del fascio:* il sistema $\{E_1,E_2,E_\Pi\}$ ha le stesse infinite soluzioni di $\{E_1,E_2\}$, quindi per Rouché–Capelli $r([A|\mathbf b])=r(A)=2$. Allora la riga completa di $E_\Pi$ è combinazione lineare delle righe di $E_1,E_2$: è esattamente $pE_1+qE_2$.

**Esempio.** Piano per $\ell:\ x+2y-1=x+2z+1=0$ e per $P_0(1,2,3)$.
- Fascio: $p(x+2y-1)+q(x+2z+1)=0$.
- Si impone il passaggio per $P_0$: $p(1+4-1)+q(1+6+1)=0\iff4p+8q=0\iff p+2q=0$.
- Basta **una** soluzione non nulla (le altre sono proporzionali e danno lo stesso piano): $p=2$, $q=-1$.
$$2(x+2y-1)-(x+2z+1)=0\iff\boxed{\ x+4y-2z=3\ }$$
- *Controllo.* $P_0$: $1+8-6=3$ ✓. Il punto $(-1,1,0)\in\ell$: $-1+4-0=3$ ✓.

> **Caso degenere.** Se il punto imposto sta già su $\ell$, l'equazione nei parametri diventa $0=0$: tutti i piani del fascio passano per esso e il problema non ha soluzione unica, coerentemente col fatto che una retta e un suo punto non individuano un piano.

#### (3) Esempio misto: fascio per un punto e due condizioni

Piano $\Pi$ **parallelo** alla retta $\ell_0:\ 3x-y-z=x-z+2=0$ e passante per $P(1,0,-1)$ e $Q(1,1,0)$.

1. **Piani per $P$** (stella di piani, 3 parametri omogenei):
$$a(x-1)+by+c(z+1)=0\iff ax+by+cz=a-c,\qquad a^2+b^2+c^2\neq0.\tag{2}$$
2. **Passaggio per $Q$** ($x=1,y=1,z=0$): $a+b=a-c\Rightarrow c=-b$. Si ottiene il fascio dei piani per $P$ e $Q$ (cioè per la retta $PQ$):
$$ax+by-bz=a+b,\qquad a^2+b^2\neq0.\tag{3}$$
3. **Parallelismo a $\ell_0$.** In senso stretto si chiede che $\ell_0\cap\Pi=\emptyset$, cioè che il sistema sia **incompatibile**:
$$\begin{cases}x-z=-2\\3x-y-z=0\\ax+by-bz=a+b\end{cases}\qquad\left(\begin{array}{ccc|c}1&0&-1&-2\\3&-1&-1&0\\a&b&-b&a+b\end{array}\right)\xrightarrow[R_3\to R_3-aR_1]{R_2\to R_2-3R_1}\left(\begin{array}{ccc|c}1&0&-1&-2\\0&-1&2&6\\0&b&a-b&3a+b\end{array}\right)\xrightarrow{R_3\to R_3+bR_2}\left(\begin{array}{ccc|c}\boxed1&0&-1&-2\\0&\boxed{-1}&2&6\\0&0&a+b&3a+7b\end{array}\right).$$
   - Se $a+b\neq0$: soluzione unica, cioè $\ell_0$ e $\Pi$ si incontrano in un punto. Va escluso.
   - Quindi $a+b=0$. In tal caso il sistema è incompatibile $\iff3a+7b\neq0$. Con $a=-b$ questo diventa $4b\neq0$, cioè $b\neq0$.

   > ⚠️ Nel PDF (p. 29) l'ultimo termine noto è scritto $3a+6b$: è un errore di calcolo, perché $(3a+b)+6b=3a+7b$. La conclusione non cambia: con $a=-b$ si ottiene comunque la condizione $b\neq0$.
4. Quindi $(a,b)=(t,-t)$ con $t\in\mathbb R\setminus\{0\}$. Sostituendo in (3): $tx-ty+tz=0\iff t(x-y+z)=0$ e, poiché $t\neq0,$
$$\boxed{\ \Pi:\ x-y+z=0\ }$$
- *Controllo.* $P$: $1-0-1=0$ ✓; $Q$: $1-1+0=0$ ✓. Direzione di $\ell_0$: $\ker\begin{pmatrix}3&-1&-1\\1&0&-1\end{pmatrix}\ni(1,2,1)$, e $(1,-1,1)\cdot(1,2,1)=0$ ✓ (la direzione di $\ell_0$ è parallela a $\Pi$). Il punto $(0,-2,2)\in\ell_0$ dà $0+2+2=4\neq0$, quindi $\ell_0\not\subset\Pi$ ✓.

> **Metodo alternativo (più rapido).** La normale $\mathbf n$ di $\Pi$ deve essere ortogonale sia alla direzione $(1,2,1)$ di $\ell_0$ sia a $\overrightarrow{PQ}=(0,1,1)$. Risolvendo $n_1+2n_2+n_3=0$ e $n_2+n_3=0$ si trova $\mathbf n\propto(1,-1,1)$; imponendo il passaggio per $P$ si ottiene $x-y+z=0$. Il metodo dei fasci resta utile quando le condizioni sono date in forma cartesiana o dipendono da parametri.

---

### Riepilogo

| Obiettivo | Strumento |
|---|---|
| $\vec a\perp\vec b$ | $\mathbf x^T\mathbf y=0$ (solo in riferimento cartesiano) |
| retta $\perp$ piano $ax+by+cz=d$ | direzione $\propto(a,b,c)$ |
| retta $\parallel$ piano | direzione risolve $ax+by+cz=0$ (+ un punto fuori dal piano per il senso stretto) |
| piani $\parallel\Pi_0$ | $ax+by+cz=g$ |
| piani per la retta $E_1=E_2=0$ | $pE_1+qE_2=0$, $(p,q)\ne(0,0)$ |
| piani per un punto $P_0$ | $a(x-x_0)+b(y-y_0)+c(z-z_0)=0$ |
| imporre "contiene $\ell$" / "parallelo a $\ell$" / "incidente" | sistema $\ell\cap\Pi$: infinite / nessuna / unica soluzione |

## Collegamenti

- HTML interattivo: [[Lezione 7 — Rette, piani, ortogonalità e fasci.html|Lezione 7 completa]]

- [[Posizione reciproca di rette e piani|Posizione reciproca di rette e piani]]
- [[Rette e piani — equazioni parametriche e cartesiane|Rette e piani — equazioni parametriche e cartesiane]]
- [[Sistemi lineari e teorema di Rouché-Capelli|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Vettori geometrici liberi|Vettori geometrici liberi]]
- [[Rango e teorema di nullità più rango|Rango e teorema di nullità più rango]]
