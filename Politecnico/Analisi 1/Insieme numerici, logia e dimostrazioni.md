## Insieme numerici
### Numeri naturali
$$\mathbb{N} := \{0,1,2,3,4,5,\dots\}$$
Sono i numeri usati per contare. Sono chiusi rispetto a somma e prodotto (la somma/prodotto di due naturali è ancora un naturale), ma non rispetto alla sottrazione: $3-5 \notin \mathbb{N}$. Questo limite motiva l'estensione a $\mathbb{Z}$.

### Numeri interi relativi
$$\mathbb{Z} := \{\dots,-2,-1,0,1,2,\dots\}$$
Estendono $\mathbb{N}$ aggiungendo gli opposti, così ogni sottrazione ha soluzione: $\mathbb{Z}$ è chiuso anche rispetto alla sottrazione. Non è però chiuso rispetto alla divisione: $1 \div 2 \notin \mathbb{Z}$. Da qui nasce $\mathbb{Q}$.

### Numeri razionali
$$\mathbb{Q} := \left\{\frac{m}{n} : m,n \in \mathbb{Z},\ n \neq 0\right\}$$
Sono i rapporti (frazioni) tra due interi con denominatore non nullo. $\mathbb{Q}$ è chiuso rispetto a somma, sottrazione, prodotto e divisione (per elementi non nulli): è un **campo**. Ogni razionale ammette infinite rappresentazioni frazionarie equivalenti (es. $\frac{1}{2}=\frac{2}{4}$).

#### Relazione di inclusione
$$\mathbb{N} \subset \mathbb{Z} \subset \mathbb{Q}$$
Ogni naturale è un intero (con segno positivo) e ogni intero è un razionale (con denominatore $1$): l'inclusione è stretta, cioè ciascun insieme contiene elementi non presenti nel precedente.

## Rappresentazione decimale
Ogni numero razionale, scritto in base 10, ammette uno tra questi tipi di allineamento (sviluppo) decimale:

### Finito
Lo sviluppo si arresta dopo un numero finito di cifre.
$$\frac{1}{2}=0.5$$

### Infinito periodico
Dopo un certo punto le cifre decimali si ripetono indefinitamente in un blocco (periodo).
$$\frac{1}{3}=0.\overline{3}$$

### Infinito non periodico
Lo sviluppo decimale prosegue all'infinito senza mai ripetersi in un blocco periodico. Questo terzo caso **non** corrisponde a nessun numero razionale (un teorema di teoria dei numeri mostra che ogni razionale ha sviluppo finito o periodico): rappresenta i numeri irrazionali, es. $\sqrt{2} = 1.41421356\dots$

## Numeri reali
$$\mathbb{R} := \{\text{allineamenti decimali: finiti, infiniti periodici e infiniti non periodici}\}$$
$\mathbb{R}$ raccoglie tutti e tre i tipi di sviluppo decimale, quindi $\mathbb{Q} \subset \mathbb{R}$. A differenza di $\mathbb{Q}$, $\mathbb{R}$ è **completo** (non ha "buchi": ogni sottoinsieme limitato superiormente ha estremo superiore), proprietà fondamentale per l'Analisi (limiti, continuità).

## Numeri irrazionali
$$\mathbb{R} \setminus \mathbb{Q} = \text{numeri irrazionali}$$
Sono i reali che **non** si possono scrivere come rapporto di due interi, cioè quelli con sviluppo decimale infinito non periodico (es. $\sqrt{2}$, $\pi$, $e$). L'operazione $\setminus$ è la **differenza insiemistica**: $A \setminus B = \{x \in A : x \notin B\}$, cioè gli elementi di $A$ che non appartengono a $B$.

## Radici
L'estrazione di radice è l'operazione inversa dell'elevamento a potenza.

**Definizione.** Dato $a \ge 0$, si dice che $b \ge 0$ è la radice quadrata di $a$, e si scrive $b = \sqrt{a}$, se $b^2 = a$.

Esempio: $a = 25 \Rightarrow b = 5$, poiché $5^2 = 25$, quindi $\sqrt{25} = 5$.

**Teorema.** $\sqrt{2} \notin \mathbb{Q}$, cioè $\sqrt{2} \in \mathbb{R} \setminus \mathbb{Q}$: $\sqrt{2}$ è irrazionale.

## Rappresentazione geometrica di $\mathbb{R}$
$\mathbb{R}$ si rappresenta geometricamente come una **retta orientata** (retta reale): fissati un'origine ($0$) e un'unità di misura, ogni numero reale corrisponde a uno e un solo punto della retta, e viceversa (corrispondenza biunivoca punti-numeri). I razionali sono densi sulla retta ma non la riempiono: gli irrazionali, come $\sqrt{2}$, occupano i "punti mancanti". Geometricamente $\sqrt{2}$ si costruisce come ipotenusa di un triangolo rettangolo isoscele di cateti unitari ($1^2+1^2=2$ per il teorema di Pitagora) e si riporta sulla retta reale con un compasso, cadendo tra $1$ e $2$.

## Richiami di logica
Una **proposizione** (o affermazione) è un enunciato a cui si può assegnare univocamente un valore di verità: vero (V) o falso (F). Indicando con $P$ e $Q$ due proposizioni, i **connettivi logici** permettono di combinarle in proposizioni composte.

### Implicazione
$$P \Rightarrow Q$$
Si legge "$P$ implica $Q$": se $P$ è vera allora anche $Q$ è vera. $P$ è detta **antecedente**, $Q$ **conseguente**. L'implicazione è falsa solo nel caso in cui $P$ sia vera e $Q$ falsa; in tutti gli altri casi è vera (in particolare, $P$ falsa rende $P \Rightarrow Q$ vera indipendentemente da $Q$).

Esempio: siano $P: x > 5$ e $Q: x > 3$.
- $P \Rightarrow Q$ è vera: se $x>5$ allora certamente $x>3$.
- $Q \not\Rightarrow P$ (implicazione inversa, o **inversa**): è falsa, perché $Q$ vera non garantisce $P$ vera. Controesempio: $x=4$ rende $Q$ vera ma $P$ falsa.

### Equivalenza
$$P \Leftrightarrow Q$$
Si legge "$P$ se e solo se $Q$" (doppia implicazione): equivale a $(P \Rightarrow Q) \wedge (Q \Rightarrow P)$, cioè $P$ e $Q$ sono sempre entrambe vere o entrambe false.

### Contronominale (contrapposizione)
$$\left(P \Rightarrow Q\right) \iff \left(\overline{Q} \Rightarrow \overline{P}\right)$$
La **contronominale** di $P \Rightarrow Q$ è $\overline{Q} \Rightarrow \overline{P}$: la negazione del conseguente implica la negazione dell'antecedente. Contronominale e implicazione originale sono **logicamente equivalenti** (stesso valore di verità), e spesso è più agevole dimostrare la contronominale.

⚠️ Da non confondere con:
- **inversa** $Q \Rightarrow P$ — non equivalente a $P \Rightarrow Q$;
- **contraria** $\overline{P} \Rightarrow \overline{Q}$ — non equivalente a $P \Rightarrow Q$ (equivale invece all'inversa).

Esempio (stesso $P,Q$ di sopra): $\overline{P}: x \le 5$ e $\overline{Q}: x \le 3$. La contronominale $\overline{Q} \Rightarrow \overline{P}$ afferma "se $x \le 3$ allora $x \le 5$", vera — coerentemente con il fatto che $P \Rightarrow Q$ era vera.

## Dimostrazioni
Un **teorema** è un enunciato del tipo Ipotesi $\Rightarrow$ Tesi, dove l'**ipotesi** è l'antecedente (ciò che si assume vero) e la **tesi** è il conseguente (ciò che si vuole provare):
$$\text{Ipotesi} \Rightarrow \text{Tesi}$$
**Dimostrare** il teorema significa provare che questa implicazione è vera, tipicamente concatenando una catena di implicazioni logiche vere già note (definizioni, assiomi, teoremi precedenti):
$$\text{Ipotesi} \Rightarrow \dots \Rightarrow \text{Tesi}$$

> [!info] Terminologia
> - **Lemma** = risultato ausiliario, usato come "mattone" nella dimostrazione di un teorema più importante.
> - **Proposizione** = teorema di importanza secondaria (minore rispetto a un teorema "principale").
> - **Corollario** = conseguenza immediata di un teorema, che segue con poco lavoro aggiuntivo.

Esistono tre schemi dimostrativi principali: la dimostrazione **diretta**, quella **indiretta** (per assurdo o per contrapposizione) e la dimostrazione **per induzione**.

### Dimostrazione diretta
Si parte dall'ipotesi, la si sostituisce/manipola algebricamente, e si arriva alla tesi senza mai negare le proposizioni in gioco: Ipotesi $\Rightarrow \dots \Rightarrow$ Tesi, senza passare per il "falso".

#### Esempio: definizione di pari e dispari
$$n \in \mathbb{Z} \text{ si dice \textbf{pari} se } \exists\, h \in \mathbb{Z}: n =2h$$
$$n \in \mathbb{Z} \text{ si dice \textbf{dispari} se } \exists\, h \in \mathbb{Z}: n =2h+1$$
$0$ è pari per questa definizione ($h=0$).
- se $n = 6$: $6=2h \Rightarrow h = \frac{6}{2} = 3 \in \mathbb{Z}$, quindi $6$ è pari.
- se $n = 9$: $9=2h+1 \Rightarrow h = \frac{9-1}{2} = 4 \in \mathbb{Z}$, quindi $9$ è dispari.

#### Proposizione: parità di $n^2$
**(i)** $n$ pari $\Rightarrow n^2$ pari.

Per ipotesi $n$ è pari, quindi per definizione $\exists h \in \mathbb{Z} : n = 2h$. Sostituendo nella tesi:
$$n^2 = (2h)^2 = 4h^2 = 2\underbrace{(2h^2)}_{=:k \in \mathbb{Z}}$$
Si è quindi trovato $k \in \mathbb{Z}$ tale che $n^2 = 2k$: per definizione, $n^2$ è pari.

**(ii)** $n$ dispari $\Rightarrow n^2$ dispari.

Per ipotesi $n$ è dispari, quindi per definizione $\exists h \in \mathbb{Z} : n = 2h+1$. Sostituendo nella tesi:
$$n^2 = (2h+1)^2 = 4h^2+4h+1 = 2\underbrace{(2h^2+2h)}_{=:k \in \mathbb{Z}}+1 = 2k+1$$
Si è quindi trovato $k \in \mathbb{Z}$ tale che $n^2 = 2k+1$: per definizione, $n^2$ è dispari.

In entrambi i casi si è partiti dall'ipotesi (definizione di pari/dispari), la si è sostituita nell'espressione della tesi ($n^2$) e la si è manipolata algebricamente fino a raccogliere un fattore $2$: questo è lo schema tipico della dimostrazione diretta. Questa proposizione ($n$ pari $\Leftrightarrow n^2$ pari) verrà riutilizzata più sotto come "lemma" nella dimostrazione per assurdo dell'irrazionalità di $\sqrt2$.

### Dimostrazione indiretta
Anziché dimostrare direttamente Ipotesi $\Rightarrow$ Tesi, si dimostra una proposizione logicamente equivalente, più semplice da trattare.

#### Per assurdo
Si suppone vera l'ipotesi e **falsa la tesi** (se ne assume la negazione), e si deduce logicamente una contraddizione (un assurdo). Poiché l'ipotesi è vera per assunzione, la contraddizione può derivare solo dall'aver negato la tesi: la tesi deve quindi essere vera.

##### Esempio: $\sqrt{2}$ è irrazionale
**Teorema.** $\sqrt{2} \in \mathbb{R} \setminus \mathbb{Q}$ (cioè $\sqrt{2} \notin \mathbb{Q}$).

**Dimostrazione (per assurdo).** Neghiamo la tesi e affermiamo che $\sqrt{2} \in \mathbb{Q}$: allora $\exists\, m,n \in \mathbb{Z}$ tali che $\sqrt{2} = \frac{m}{n}$, con $m,n$ **primi tra loro** (frazione ridotta ai minimi termini — sempre possibile per la generalità della rappresentazione frazionaria).

Elevando al quadrato:
$$2 = \frac{m^2}{n^2} \quad \Rightarrow \quad m^2 = 2n^2$$

Quindi $m^2$ è pari; per la proposizione precedente ($n$ pari $\Leftrightarrow$ $n^2$ pari), anche $m$ è pari: $\exists\, k \in \mathbb{Z} : m = 2k$.

Sostituendo:
$$2n^2 = m^2 = (2k)^2 = 4k^2 \quad \Rightarrow \quad n^2 = 2k^2$$

quindi anche $n^2$ è pari, e dunque $n$ è pari.

Ma allora $m$ e $n$ sono entrambi pari, cioè ammettono $2$ come divisore comune: **assurdo**, poiché per ipotesi $m$ e $n$ erano primi tra loro (nessun divisore comune eccetto $1$). L'assurdo nasce dall'aver negato la tesi, quindi la tesi è vera: $\sqrt{2} \notin \mathbb{Q}$. $\blacksquare$

#### Per contrapposizione
Si dimostra la **contronominale** $\overline{Q} \Rightarrow \overline{P}$ al posto di $P \Rightarrow Q$: essendo le due logicamente equivalenti (vedi sopra), provare l'una prova anche l'altra. A differenza della dimostrazione per assurdo, qui non si cerca una contraddizione: si costruisce una normale dimostrazione diretta, ma sull'implicazione negata e invertita.

##### Esempio: $n$ dispari $\Rightarrow n^2$ dispari, per contrapposizione
Poniamo:
- $P$: "$n$ è dispari"
- $Q$: "$n^2$ è dispari"

vogliamo $P \Rightarrow Q$. Le negazioni sono:
- $\overline{P}$: "$n$ è pari"
- $\overline{Q}$: "$n^2$ è pari"

Per contrapposizione basta dimostrare $\overline{Q} \Rightarrow \overline{P}$, cioè "$n^2$ pari $\Rightarrow n$ pari" — equivalente alla proposizione già dimostrata sopra per via diretta. Dato che $\overline{Q} \Rightarrow \overline{P}$ è vera, per la regola della contronominale anche $P \Rightarrow Q$ è vera: $n$ dispari $\Rightarrow n^2$ dispari. $\blacksquare$

### Dimostrazione per induzione
Si usa quando la tesi va provata per **tutti** i numeri naturali $n$ (o per tutti gli $n \ge n_0$), cioè per un'affermazione $P(n)$ che dipende da $n \in \mathbb{N}$. Si basa sul **principio di induzione**, che riduce una verifica su infiniti casi a due soli passi:

1. **Passo base**: si verifica che $P(n_0)$ è vera (tipicamente $n_0 = 0$ o $n_0=1$).
2. **Passo induttivo**: si assume vera $P(n)$ per un generico $n \ge n_0$ (**ipotesi induttiva**) e si dimostra che allora è vera anche $P(n+1)$.

Se entrambi i passi valgono, il principio di induzione garantisce che $P(n)$ è vera per ogni $n \ge n_0$: il passo base "accende" il primo caso, e il passo induttivo lo propaga da un naturale al successivo, come tessere di un domino che cadono in sequenza.



