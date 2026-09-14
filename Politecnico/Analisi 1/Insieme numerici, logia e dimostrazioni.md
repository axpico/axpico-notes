## Numeri naturali
$$\mathbb{N} := \{0,1,2,3,4,5,\dots\}$$
Sono i numeri usati per contare. Sono chiusi rispetto a somma e prodotto (la somma/prodotto di due naturali è ancora un naturale), ma non rispetto alla sottrazione: $3-5 \notin \mathbb{N}$. Questo limite motiva l'estensione a $\mathbb{Z}$.

## Numeri interi relativi
$$\mathbb{Z} := \{\dots,-2,-1,0,1,2,\dots\}$$
Estendono $\mathbb{N}$ aggiungendo gli opposti, così ogni sottrazione ha soluzione: $\mathbb{Z}$ è chiuso anche rispetto alla sottrazione. Non è però chiuso rispetto alla divisione: $1 \div 2 \notin \mathbb{Z}$. Da qui nasce $\mathbb{Q}$.

## Numeri razionali
$$\mathbb{Q} := \left\{\frac{m}{n} : m,n \in \mathbb{Z},\ n \neq 0\right\}$$
Sono i rapporti (frazioni) tra due interi con denominatore non nullo. $\mathbb{Q}$ è chiuso rispetto a somma, sottrazione, prodotto e divisione (per elementi non nulli): è un **campo**. Ogni razionale ammette infinite rappresentazioni frazionarie equivalenti (es. $\frac{1}{2}=\frac{2}{4}$).

### Relazione di inclusione
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

## Richiami alla logica 
Affermazioni vere o false connesse con connettivi logici P e Q proposizioni o affermazioni
connettivi logici

### Implicazioni
$$P => Q$$
se $P: x > 5$ e $Q: x > 3$ allora $P => Q$ e $P \not{=>} Q$

### Equivalenza
$$P <=> Q$$
### Conttraposizione
$$$$