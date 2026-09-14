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
Ipotesi -> antecedente
tesi -> consegunte
utilizzo di implicazione logiche per arrivare a testi 
$$\text{Ipotesi} => \text{Tesi}$$
la dimostrazione prova questa implicazione 
3 tipi di dimostrazione 
### Diretta
### Indiretta
#### Assurdo
#### Contrapposizione
### Induzione N 
solo numerrare oggetti 