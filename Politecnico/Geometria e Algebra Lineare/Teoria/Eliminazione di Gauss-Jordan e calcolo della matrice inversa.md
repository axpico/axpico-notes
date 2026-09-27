---
tags:
  - geometria-algebra-lineare
  - matrici
  - gauss-jordan
  - matrice-inversa
---
## Equivalenza per righe

**Definizione.** Due matrici $A$ e $A'$ (della stessa dimensione) si dicono **equivalenti per righe** se $A'$ si può ottenere da $A$ applicando una successione **finita** di **operazioni elementari sulle righe**:

1. **scambio** di due righe;
2. **addizione o sottrazione** a una riga di un multiplo di un'altra riga;
3. **moltiplicazione** di una riga per uno scalare $\lambda \ne 0$.

Ogni operazione elementare è **invertibile** (lo scambio è invertibile da sé, l'addizione di $\lambda$ volte una riga si annulla sottraendo $\lambda$ volte quella riga, la moltiplicazione per $\lambda\ne0$ si annulla moltiplicando per $1/\lambda$): per questo l'equivalenza per righe è davvero una relazione di equivalenza (riflessiva, simmetrica, transitiva) e le matrici equivalenti per righe ad $A$ rappresentano **lo stesso sistema lineare** (le stesse soluzioni) di $A$.

## Forma totalmente ridotta (RREF)

Tra tutte le matrici **a scala** $U$ equivalenti per righe ad $A$ (ottenute cioè con la normale eliminazione di Gauss), ne esiste **un'unica**, indicata $U_0$, che soddisfa in più le condizioni:

- in ogni riga non nulla, il **pivot** (il primo elemento non nullo da sinistra) è uguale a $1$;
- tutti gli elementi nella **stessa colonna** di un pivot, **sopra** di esso, sono uguali a $0$.

(Gli elementi sotto ogni pivot sono già $0$ per definizione di matrice a scala.)

**Definizione.** La matrice $U_0$ così caratterizzata si chiama la **forma (matrice) totalmente ridotta** di $A$ (in inglese *Reduced Row Echelon Form*, RREF). Il teorema di esistenza e unicità garantisce che $U_0$ dipende **solo** da $A$, non dalla particolare sequenza di operazioni elementari usata per ottenerla.

## Algoritmo MEG-J (Metodo di Eliminazione di Gauss-Jordan)

Il **MEG-J** è l'algoritmo che, applicato a una qualunque matrice $A$, produce la sua forma totalmente ridotta $U_0$:

1. si riduce $A$ a scala con l'eliminazione di Gauss "in avanti" (si annullano gli elementi **sotto** ogni pivot, procedendo da sinistra a destra e dall'alto in basso);
2. si normalizza ogni pivot a $1$, dividendo la sua riga per il valore del pivot;
3. si annullano anche gli elementi **sopra** ogni pivot, procedendo questa volta "all'indietro" (da destra a sinistra / dal basso in alto), sottraendo opportuni multipli della riga del pivot.

Il risultato finale è, per il teorema precedente, sempre lo stesso $U_0$, indipendentemente dalle scelte fatte lungo il percorso (ordine delle operazioni, righe usate come pivot in caso di scelte multiple).

## Uso del MEG-J per calcolare $A^{-1}$

Il MEG-J non serve solo a risolvere un singolo sistema $Ax=b$: applicato alla **matrice orlata** (o aumentata) $[A \mid I_n]$, permette di calcolare l'inversa di una matrice quadrata $A$ **quando esiste**.

**Idea.** Come mostrato nella dimostrazione di (v) $\Rightarrow$ (ii) del Teorema 4 (si veda [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]), se $A$ è invertibile la $j$-esima colonna di $A^{-1}$ è la (unica) soluzione $u_j$ del sistema $Ax = e_j$, dove $e_j$ è la $j$-esima colonna di $I_n$. Risolvere **simultaneamente** tutti questi $n$ sistemi equivale a ridurre a scala l'intera matrice orlata $[A\mid I_n]$ trattando ciascuna colonna di $I_n$ come termine noto.

**Procedura.**

1. Si scrive la matrice orlata $[A \mid I_n]$ (dimensione $n \times 2n$).
2. Si applica il MEG-J all'**intera** matrice orlata, usando solo operazioni elementari sulle righe (mai sulle colonne).
3. Se la parte sinistra si riduce a $I_n$, cioè si ottiene $[I_n \mid B]$, allora $A$ è invertibile e $B = A^{-1}$.
4. Se durante la riduzione compare una riga nulla nella parte sinistra (cioè $r(A) < n$), allora $A$ **non è invertibile**: il procedimento si interrompe, coerentemente con il Teorema 4 (iv).

$$
[A \mid I_n] \ \xrightarrow{\ \text{MEG-J}\ }\ [I_n \mid A^{-1}]
$$

Questo metodo è quello usato in pratica (più efficiente della formula generale con i determinanti per matrici di ordine $\ge 3$) ed è l'estensione naturale della formula esplicita valida per matrici $2\times2$ (si veda il Teorema 5 nella nota sulla matrice inversa).

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Sistemi lineari e teorema di Rouché-Capelli.md|Sistemi lineari e teorema di Rouché-Capelli]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Equazioni matriciali.md|Equazioni matriciali]]
