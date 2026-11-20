---
tags:
  - geometria-algebra-lineare
  - gram-schmidt
  - matrici-ortogonali
  - matrici-simmetriche
  - teorema-spettrale
  - diagonalizzazione
---
# Gram-Schmidt, matrici ortogonali e teorema spettrale

Fonte: Lezione 12 (PDF "Ortogonalizzazione di Gram-Schmidt…", V2022, 54 pp.). Testo: ALG cap. 7 §§4–5, pp. 368–372 e 382–385; cap. 8 §2, pp. 418–421.
Prerequisiti: [[Prodotti scalari, spazi euclidei e basi ortonormali]] (proiezione su una retta, basi ortonormali), [[Autovalori, autovettori, autospazi e molteplicità]], [[Criterio di diagonalizzabilità e invarianza del polinomio caratteristico]], [[Cambio di base e matrice di passaggio]].

## 0. L'idea in parole povere (leggi prima questo)

La lezione mette insieme due cose che conosci già:
- dalla Lezione 11: **perpendicolarità** e **proiezioni** (l'"ombra" di un vettore su una retta);
- dalla Lezione 10: **diagonalizzare** una matrice, cioè trovare una base di autovettori.

Le domande della lezione sono tre.

1. **Gram-Schmidt.** Ho una base "storta", con vettori non perpendicolari. Come la raddrizzo in una base di vettori **a due a due perpendicolari**?
   *Idea:* tieni il primo vettore. A ogni vettore successivo **togli la sua ombra** sui vettori già sistemati. Quello che resta è perpendicolare a tutti loro.
2. **Matrici ortogonali.** Che matrice ottengo mettendo in colonna una base ortonormale (versori perpendicolari)? Una matrice $Q$ con una proprietà comodissima: **l'inversa è la trasposta**, $Q^{-1}=Q^T$. Niente Gauss-Jordan per invertirla.
3. **Teorema spettrale.** Quando posso diagonalizzare una matrice con una base di autovettori **perpendicolari**? Risposta sorprendentemente semplice: **esattamente quando la matrice è simmetrica** ($A^T=A$).

**Le tre idee da portare via:**
- Gram-Schmidt $=$ "sottrai le ombre sui vettori precedenti".
- $Q$ ortogonale $\iff$ colonne ortonormali $\iff$ $Q^TQ=I$ $\iff$ $Q^{-1}=Q^T$.
- $A$ simmetrica $\iff$ esiste base ortonormale di autovettori. In più: autovalori tutti reali, autospazi perpendicolari tra loro.

## 1. Proiezione ortogonale su un sottospazio (pp. 2–4)

**Richiamo.** Proiezione di $\underline v$ sulla retta $W=\mathrm{span}\{\underline w\}$:
$$\underline v_0=\frac{\langle\underline v,\underline w\rangle}{\|\underline w\|^2}\,\underline w.$$
È l'unico punto di $W$ a distanza minima da $\underline v$.

**Generalizzazione.** Se $W$ ha una **base ortogonale** $\{\underline w_1,\dots,\underline w_k\}$, la proiezione su $W$ è la somma delle proiezioni sulle singole rette:
$$\boxed{\underline v_0=\sum_{i=1}^k\frac{\langle\underline v,\underline w_i\rangle}{\|\underline w_i\|^2}\,\underline w_i}$$

**Proprietà chiave.** Il "resto" $\underline v-\underline v_0$ è ortogonale a **ogni** vettore di $W$. Si scrive $\underline v-\underline v_0\perp W$.

> [!warning] Serve una base **ortogonale** di $W$
> Con una base qualsiasi la formula è sbagliata: le ombre si "sovrappongono" e le conti due volte. Per questo serve Gram-Schmidt.

## 2. Algoritmo di Gram-Schmidt (pp. 4–6)

**Problema.** Dati $\underline v_1,\dots,\underline v_k$ linearmente indipendenti, trovare una base ortogonale di $W=\mathrm{span}\{\underline v_1,\dots,\underline v_k\}$.

**Algoritmo.**
1. $\underline w_1:=\underline v_1$.
2. Per $i=1,\dots,k-1$: proietta $\underline v_{i+1}$ sullo spazio dei $\underline w$ già trovati e togli la proiezione.
$$\underline w_{i+1}:=\underline v_{i+1}-\sum_{j=1}^{i}\frac{\langle\underline v_{i+1},\underline w_j\rangle}{\|\underline w_j\|^2}\,\underline w_j$$
3. (Se serve ortonormale) normalizza: $\underline u_i=\underline w_i/\|\underline w_i\|$.

Scritto per esteso per i primi tre:
$$\underline w_1=\underline v_1,\qquad
\underline w_2=\underline v_2-\frac{\langle\underline v_2,\underline w_1\rangle}{\|\underline w_1\|^2}\underline w_1,\qquad
\underline w_3=\underline v_3-\frac{\langle\underline v_3,\underline w_1\rangle}{\|\underline w_1\|^2}\underline w_1-\frac{\langle\underline v_3,\underline w_2\rangle}{\|\underline w_2\|^2}\underline w_2$$

**Perché funziona.** $\underline w_{i+1}$ è il "resto" della proiezione di $\underline v_{i+1}$ sullo span dei precedenti. Per la proprietà della §1 il resto è perpendicolare a quello span, quindi a tutti i $\underline w_1,\dots,\underline w_i$.

> [!tip] Trucchi di calcolo
> - Nelle formule usa sempre i **$\underline w$** (già ortogonali) al denominatore e come direzione, mai i $\underline v$.
> - Puoi moltiplicare un $\underline w_i$ per una costante non nulla per togliere le frazioni (es. $(\tfrac12,-\tfrac12,1)\to(1,-1,2)$). Resta ortogonale agli altri.
> - Controllo finale: tutti i prodotti scalari $\langle\underline w_i,\underline w_j\rangle$, $i\ne j$, devono essere $0$.

### Intuizione grafica in $\mathbb R^2$

$\underline v_1=(3,1)$, $\underline v_2=(2,2)$. Allora $\underline w_1=(3,1)$, ombra di $\underline v_2$ su $\underline w_1$: $\frac{8}{10}(3,1)=(2.4,\,0.8)$. Resto: $\underline w_2=(2,2)-(2.4,0.8)=(-0.4,\,1.2)$. Verifica: $3(-0.4)+1(1.2)=0$.

```desmos-graph
left=-2; right=4;
top=3; bottom=-1;
---
y=\frac{x}{3}
y=-3x|hidden
(3,1)|label:v1 = w1
(2,2)|label:v2
(2.4,0.8)|open|label:ombra di v2 su w1
(-0.4,1.2)|label:w2 = v2 - ombra
```

La retta disegnata è $\mathrm{span}\{\underline w_1\}$. Il segmento da $(2.4,0.8)$ a $(2,2)$ è perpendicolare a essa. $\underline w_2$ è proprio quel segmento, spostato nell'origine.

## 3. Esempio 1 — tre vettori indipendenti in $\mathbb R^4$ (pp. 7–9)

$\underline v_1=(1,0,0,1)$, $\underline v_2=(1,2,0,0)$, $\underline v_3=(1,2,2,1)$.

**Passo 1.** $\underline w_1=(1,0,0,1)$, $\|\underline w_1\|^2=2$.

**Passo 2.** $\langle\underline v_2,\underline w_1\rangle=1$.
$$\underline w_2=(1,2,0,0)-\tfrac12(1,0,0,1)=\left(\tfrac12,\,2,\,0,\,-\tfrac12\right),\qquad\|\underline w_2\|^2=\tfrac14+4+\tfrac14=\tfrac92.$$

**Passo 3.** $\langle\underline v_3,\underline w_1\rangle=2$, $\langle\underline v_3,\underline w_2\rangle=\tfrac12+4-\tfrac12=4$.
$$\underline v_3^{\,0}=\tfrac22\underline w_1+\tfrac{4}{9/2}\underline w_2=(1,0,0,1)+\tfrac89\left(\tfrac12,2,0,-\tfrac12\right)=\left(\tfrac{13}9,\tfrac{16}9,0,\tfrac59\right)$$
$$\underline w_3=\underline v_3-\underline v_3^{\,0}=\left(-\tfrac49,\,\tfrac29,\,2,\,\tfrac49\right)$$

**Controllo.** $\langle\underline w_1,\underline w_2\rangle=\tfrac12-\tfrac12=0$; $\langle\underline w_1,\underline w_3\rangle=-\tfrac49+\tfrac49=0$; $\langle\underline w_2,\underline w_3\rangle=-\tfrac29+\tfrac49-\tfrac29=0$. ✓

## 4. Esempio 2 — cosa succede con vettori dipendenti (pp. 10–12)

Quattro vettori in $\mathbb R^3$ sono sempre dipendenti: $\underline v_1=(1,2,3)$, $\underline v_2=(3,2,1)$, $\underline v_3=(1,1,1)$, $\underline v_4=(0,1,0)$.

- $\underline w_1=(1,2,3)$, $\|\underline w_1\|^2=14$.
- $\langle\underline v_2,\underline w_1\rangle=10$, quindi $\underline w_2=(3,2,1)-\tfrac57(1,2,3)=\left(\tfrac{16}7,\tfrac47,-\tfrac87\right)=\tfrac47(4,1,-2)$. Usiamo $(4,1,-2)$, norma$^2=21$.
- $\underline v_3^{\,0}=\tfrac6{14}(1,2,3)+\tfrac{3}{21}(4,1,-2)=\tfrac37(1,2,3)+\tfrac17(4,1,-2)=(1,1,1)$. Quindi $\boxed{\underline w_3=\underline 0}$.
- $\underline v_4^{\,0}=\tfrac2{14}(1,2,3)+\tfrac1{21}(4,1,-2)=\left(\tfrac13,\tfrac13,\tfrac13\right)$, quindi $\underline w_4=\tfrac13(-1,2,-1)$.

Risultato: $\{\underline w_1,\underline w_2,\underline w_4\}$ è una base ortogonale di $\mathbb R^3$.

> [!note] Regola pratica
> Se a un passo esce $\underline w_j=\underline 0$, allora $\underline v_j$ era combinazione lineare dei precedenti. **Scartalo** e vai avanti. Gram-Schmidt quindi fa anche da test di dipendenza lineare. (La slide non enuncia la regola, la applica.)

## 5. Matrici ortogonali (pp. 13–17)

Metti in colonna una base ortonormale $\{\underline u_1,\dots,\underline u_n\}$ di $\mathbb R^n$: $Q=[\underline u_1|\dots|\underline u_n]$. Allora
$$Q^TQ=I.$$
**Perché.** L'elemento $(i,j)$ di $Q^TQ$ è riga $i$ di $Q^T$ per colonna $j$ di $Q$, cioè $\langle\underline u_i,\underline u_j\rangle=\delta_{ij}$ (vale $1$ se $i=j$, $0$ altrimenti). È esattamente la matrice identità.

**Definizione.** $Q$ quadrata reale è **ortogonale** se $Q^TQ=I$.

**Conseguenze.**
- $Q$ è invertibile e $\boxed{Q^{-1}=Q^T}$.
- Anche $Q^T$ è ortogonale: $QQ^T=I$.

**Proposizione.** Per $Q$ reale $n\times n$ sono equivalenti:
1. $Q$ è ortogonale;
2. le **colonne** di $Q$ sono una base ortonormale di $\mathbb R^n$;
3. le **righe** di $Q$ sono una base ortonormale di $\mathbb R^n$.

**Esempi.**
- $I$ è ortogonale.
- $Q=\begin{bmatrix}3/5&-4/5\\4/5&3/5\end{bmatrix}$: colonne di norma $\sqrt{9/25+16/25}=1$, prodotto scalare $-\tfrac{12}{25}+\tfrac{12}{25}=0$. Ortogonale.

> [!warning] Nome ingannevole
> "Matrice ortogonale" vuol dire colonne **ortonormali**, non solo ortogonali. $\begin{bmatrix}2&0\\0&1\end{bmatrix}$ ha colonne perpendicolari ma **non** è ortogonale: $Q^TQ=\mathrm{diag}(4,1)\ne I$.

Geometricamente una matrice ortogonale è una rotazione o una riflessione: non cambia lunghezze né angoli.

## 6. Diagonalizzazione ortogonale (pp. 17–26)

**Problema.** Dato $L:V\to V$ con $V$ euclideo, trovare una base **ortogonale** di $V$ fatta di autovettori (cioè in cui la matrice di $L$ è diagonale).

**Riduzione a $\mathbb R^n$.**
- Ogni spazio euclideo di dimensione finita ha una base ortonormale: prendi una base qualsiasi, applica Gram-Schmidt, normalizza.
- In coordinate rispetto a una base **ortonormale**, il prodotto scalare di $V$ diventa quello standard di $\mathbb R^n$:
$$\langle\underline v,\underline w\rangle=\sum_{i,j}b_ic_j\langle\underline u_i,\underline u_j\rangle=\sum_i b_ic_i=\langle\underline b,\underline c\rangle.$$
  Con una base non ortonormale questo fallirebbe. Ecco perché si fissa una base ortonormale.
- Quindi basta studiare matrici $A$ $n\times n$ con il prodotto scalare standard.

**Definizione.** $A$ reale quadrata è **ortogonalmente diagonalizzabile** se esiste $Q$ ortogonale tale che
$$Q^TAQ=D\ \text{diagonale}\qquad\Longleftrightarrow\qquad A=QDQ^T.$$
Rispetto alla diagonalizzazione normale ($S^{-1}AS=D$): ora la matrice di passaggio è ortogonale, quindi $S^{-1}$ diventa $Q^T$.

> [!note] Sempre su $\mathbb R$
> Qui non si distingue "su $\mathbb R$ / su $\mathbb C$". $A$ rappresenta un endomorfismo di $\mathbb R^n$: tutto è reale.

## 7. Matrici simmetriche e teorema spettrale (pp. 26–32)

**Definizione.** $A$ quadrata è **simmetrica** se $A^T=A$ (specchiata rispetto alla diagonale principale).
- $\begin{bmatrix}1&0&4\\0&2&5\\4&5&3\end{bmatrix}$ è simmetrica.
- $\begin{bmatrix}0&-1\\1&1\end{bmatrix}$ non lo è.

**Teorema spettrale.** Una matrice reale quadrata $A$ è ortogonalmente diagonalizzabile $\iff$ $A$ è **simmetrica**.

**Dimostrazione di $\Rightarrow$ (quella facile, in programma).** Se $A=QDQ^T$:
$$A^T=(QDQ^T)^T=(Q^T)^TD^TQ^T=QDQ^T=A,$$
perché $D$ diagonale ha $D^T=D$. Il verso $\Leftarrow$ è enunciato senza dimostrazione.

**Conseguenze per $A$ simmetrica.**
1. Tutti gli autovalori di $A$ sono **reali** (senza dimostrazione).
2. Autovettori di autovalori **diversi** sono **ortogonali**: gli autospazi sono perpendicolari a due a due.

**Dimostrazione di 2.** Prima un lemma valido per ogni $A$:
$$\langle A\underline x,\underline y\rangle=(A\underline x)^T\underline y=\underline x^TA^T\underline y=\langle\underline x,A^T\underline y\rangle.$$
Sia $A=A^T$, $A\underline v=\lambda_1\underline v$, $A\underline w=\lambda_2\underline w$, $\lambda_1\ne\lambda_2$. Calcolo $\langle A\underline v,\underline w\rangle$ in due modi:
- direttamente: $\langle\lambda_1\underline v,\underline w\rangle=\lambda_1\langle\underline v,\underline w\rangle$;
- spostando $A$ (lemma, $A^T=A$): $\langle\underline v,A\underline w\rangle=\lambda_2\langle\underline v,\underline w\rangle$.

Quindi $(\lambda_1-\lambda_2)\langle\underline v,\underline w\rangle=0$. Siccome $\lambda_1\ne\lambda_2$, segue $\langle\underline v,\underline w\rangle=0$. $\blacksquare$

> [!tip] Perché la 2 fa risparmiare conti
> In $\mathbb R^3$, se un autospazio è un **piano** $ax+by+cz=0$, l'altro autospazio (una retta) è la sua normale: $\mathrm{span}\{(a,b,c)\}$. **Non serve risolvere il secondo sistema.** Gli Esempi 2 e 3 usano questo trucco.

## 8. Procedura: diagonalizzare ortogonalmente una simmetrica

1. **Verifica** $A^T=A$. Se no, non è ortogonalmente diagonalizzabile: fine.
2. **Autovalori**: radici di $p_A(\lambda)=\det(A-\lambda I)$.
3. **Base di ogni autospazio** $W_\lambda=\ker(A-\lambda I)$.
4. **Ortogonalizza dentro ogni autospazio**:
   - autospazio di dimensione $1$: niente da fare;
   - dimensione $\ge2$: **Gram-Schmidt** sulla sua base.
   Tra autospazi diversi non serve: sono già ortogonali (§7).
5. **Normalizza** ogni vettore.
6. $Q=[\underline u_1|\dots|\underline u_n]$, $D=\mathrm{diag}(\lambda_1,\dots,\lambda_n)$ **nello stesso ordine** delle colonne. Allora $A=QDQ^T$.

> [!warning] Errore tipico
> Applicare Gram-Schmidt a **tutti** gli autovettori insieme, mescolando autospazi diversi. I vettori risultanti sono ortogonali ma **non sono più autovettori**. Gram-Schmidt va fatto **dentro** ogni autospazio separatamente.

## 9. Esempio 1 — autovalori semplici (pp. 32–38)

$L(x,y,z)=(x+y,\ x+y,\ 3z)$. Matrice: $A=\begin{bmatrix}1&1&0\\1&1&0\\0&0&3\end{bmatrix}$, simmetrica, quindi ortogonalmente diagonalizzabile.

**Autovalori** (sviluppo sulla 3ª riga):
$$p_A(\lambda)=(3-\lambda)\begin{vmatrix}1-\lambda&1\\1&1-\lambda\end{vmatrix}=(3-\lambda)\big((1-\lambda)^2-1\big)=(3-\lambda)\lambda(\lambda-2).$$
Autovalori: $0,\ 2,\ 3$, tutti semplici.

**Autospazi.**
- $\lambda=0$: $x+y=0$, $3z=0$, quindi $W_0=\mathrm{span}\{(-1,1,0)\}$.
- $\lambda=2$: $A-2I=\begin{bmatrix}-1&1&0\\1&-1&0\\0&0&1\end{bmatrix}$, cioè $-x+y=0$, $z=0$, quindi $W_2=\mathrm{span}\{(1,1,0)\}$.
- $\lambda=3$: $A-3I=\begin{bmatrix}-2&1&0\\1&-2&0\\0&0&0\end{bmatrix}$, cioè $x=y=0$, quindi $W_3=\mathrm{span}\{(0,0,1)\}$.

Autovalori semplici: gli autovettori sono già ortogonali. Basta normalizzare:
$$\underline u_1=\tfrac1{\sqrt2}(-1,1,0),\quad\underline u_2=\tfrac1{\sqrt2}(1,1,0),\quad\underline u_3=(0,0,1),\qquad D=\mathrm{diag}(0,2,3).$$

## 10. Esempio 2 — autovalore doppio, base già ortogonale (pp. 38–48)

$A_x=\begin{bmatrix}3&0&x\\0&1&0\\2&0&3\end{bmatrix}$. Per quali $x$ è ortogonalmente diagonalizzabile? Trovare $Q$, $D$.

**Quale $x$.** Teorema spettrale: serve $A_x$ simmetrica, quindi $x=2$. Nessun conto sugli autovalori.

**Autovalori** di $A_2$ (Sarrus):
$$\det(A_2-\lambda I)=(1-\lambda)\big((3-\lambda)^2-4\big)=(1-\lambda)(\lambda^2-6\lambda+5)=(1-\lambda)^2(5-\lambda).$$
$\lambda=1$ doppio, $\lambda=5$ semplice.

**$\lambda=1$.** $A_2-I=\begin{bmatrix}2&0&2\\2&0&2\\2&0&2\end{bmatrix}$: una sola equazione $x+z=0$, $y,z$ libere.
$W_1=\mathrm{span}\{(0,1,0),\,(-1,0,1)\}$. Già ortogonali: prodotto scalare $0$.

**$\lambda=5$ senza sistema.** $W_5\perp W_1$, e $W_1$ è il piano $2x+2z=0$. La normale è $(2,0,2)$, quindi $W_5=\mathrm{span}\{(2,0,2)\}$.
Verifica: $A_2(2,0,2)^T=(10,0,10)^T=5\,(2,0,2)^T$. ✓

**Normalizzazione.**
$$Q=\begin{bmatrix}0&-\frac{\sqrt2}2&\frac{\sqrt2}2\\[2pt]1&0&0\\[2pt]0&\frac{\sqrt2}2&\frac{\sqrt2}2\end{bmatrix},\qquad D=\mathrm{diag}(1,1,5).$$

**Osservazioni.**
- La risposta **non è unica**: puoi riordinare le colonne (riordinando $D$ allo stesso modo) o cambiare segno a qualche colonna.
- "Siamo stati fortunati": la base di $W_1$ era già ortogonale. È garantito solo con autovalori semplici. Con autospazi di dimensione $\ge2$ in generale serve Gram-Schmidt (Esempio 3).

## 11. Esempio 3 — autovalore doppio, serve Gram-Schmidt (pp. 48–54)

Base ortonormale di autovettori di $A=\begin{bmatrix}2&-1&-1\\-1&2&1\\-1&1&2\end{bmatrix}$ (simmetrica, quindi esiste).

**Autovalori.** Con $R_3\to R_3-R_2$, raccogliendo $(1-\lambda)$ e semplificando:
$$\det(A-\lambda I)=(1-\lambda)\begin{vmatrix}2-\lambda&-2\\-1&3-\lambda\end{vmatrix}=(1-\lambda)(\lambda^2-5\lambda+4)=(1-\lambda)^2(4-\lambda).$$
$\lambda=1$ doppio, $\lambda=4$ semplice.

**$\lambda=1$.** $A-I=\begin{bmatrix}1&-1&-1\\-1&1&1\\-1&1&1\end{bmatrix}$ si riduce a una sola equazione $x-y-z=0$.
Base: $\underline v_1=(1,1,0)$, $\underline v_2=(1,0,1)$. **Non ortogonale**: $\langle\underline v_1,\underline v_2\rangle=1\ne0$.

**Gram-Schmidt dentro $W_1$.**
$$\underline w_1=(1,1,0),\qquad\underline w_2=(1,0,1)-\tfrac12(1,1,0)=\left(\tfrac12,-\tfrac12,1\right).$$
Verifica: $\tfrac12-\tfrac12+0=0$ ✓. $\underline w_2$ sta ancora in $W_1$: $\tfrac12+\tfrac12-1=0$ ✓.
$$\underline u_1=\tfrac1{\sqrt2}(1,1,0),\qquad\underline u_2=\tfrac{1}{\sqrt{3/2}}\left(\tfrac12,-\tfrac12,1\right)=\tfrac1{\sqrt6}(1,-1,2).$$

**$\lambda=4$ senza sistema.** Normale del piano $x-y-z=0$: $W_4=\mathrm{span}\{(1,-1,-1)\}$.
Verifica: $A(1,-1,-1)^T=(4,-4,-4)^T$ ✓. Normalizzato: $\underline u_3=\tfrac1{\sqrt3}(1,-1,-1)$.

**Risultato.** $\{\underline u_1,\underline u_2,\underline u_3\}$ è base ortonormale di autovettori. Con $Q=[\underline u_1|\underline u_2|\underline u_3]$ si ha $D=\mathrm{diag}(1,1,4)$ (la slide si ferma alla base).

## 12. Riepilogo per l'esame

| Cosa | Formula / fatto |
|---|---|
| Proiezione su $W$ (base ortogonale $\underline w_i$) | $\underline v_0=\sum_i\frac{\langle\underline v,\underline w_i\rangle}{\|\underline w_i\|^2}\underline w_i$ |
| Gram-Schmidt | $\underline w_{i+1}=\underline v_{i+1}-\sum_{j\le i}\frac{\langle\underline v_{i+1},\underline w_j\rangle}{\|\underline w_j\|^2}\underline w_j$ |
| $\underline w_j=\underline 0$ | $\underline v_j$ dipende dai precedenti: scartalo |
| $Q$ ortogonale | $Q^TQ=I$, $Q^{-1}=Q^T$, colonne (e righe) ortonormali |
| Ortog. diagonalizzabile | $A=QDQ^T$, $Q$ ortogonale |
| Teorema spettrale | ortog. diagonalizzabile $\iff A^T=A$ |
| $A$ simmetrica | autovalori reali; autospazi a due a due ortogonali |
| Trucco $\mathbb R^3$ | autospazio piano $ax+by+cz=0$, altro autospazio $\mathrm{span}\{(a,b,c)\}$ |

**Trappole.** "Ortogonale" (matrice) significa colonne ortonormali. Gram-Schmidt va fatto solo dentro ogni autospazio. $D$ va scritta nello stesso ordine delle colonne di $Q$. Il teorema spettrale non dice nulla sulle matrici non simmetriche: una non simmetrica può essere diagonalizzabile (in modo non ortogonale).

Esercizi consigliati (p. 54): ALG §7.3, Esercizi 7.20, 7.22, 7.26; §7.4, Esercizi 7.35, 7.38, 7.40, 7.43; §8.1, Esercizi 8.3, 8.4, 8.5, 8.7, 8.11, 8.22 (ignora le domande sulla decomposizione spettrale).
NB: nel libro di esercizi "prodotto scalare" si chiama **prodotto interno**, e "standard" si chiama **canonico**.

## 13. Mini-quiz di autoverifica

> [!question]- 1. Applica Gram-Schmidt a $\underline v_1=(1,1)$, $\underline v_2=(1,0)$.
> $\underline w_1=(1,1)$. $\underline w_2=(1,0)-\frac12(1,1)=\left(\tfrac12,-\tfrac12\right)$. Verifica: $\tfrac12-\tfrac12=0$.

> [!question]- 2. Gram-Schmidt su $(1,2)$, $(2,4)$: cosa succede?
> $\underline w_2=(2,4)-\frac{10}{5}(1,2)=(0,0)$. Il secondo vettore è multiplo del primo: va scartato.

> [!question]- 3. $\begin{bmatrix}0&1\\1&0\end{bmatrix}$ è ortogonale? Quanto vale la sua inversa?
> Sì: colonne $(0,1),(1,0)$ ortonormali. $Q^{-1}=Q^T=Q$ (scambia le coordinate: rifatto due volte, torni all'inizio).

> [!question]- 4. $\begin{bmatrix}1&2\\0&3\end{bmatrix}$ è ortogonalmente diagonalizzabile?
> No: non è simmetrica. (È comunque diagonalizzabile, ha autovalori distinti $1,3$, ma i suoi autovettori $(1,0)$ e $(1,1)$ non sono perpendicolari.)

> [!question]- 5. $A$ è simmetrica $3\times3$, $W_2$ è il piano $x+2y-z=0$ e l'altro autovalore è $7$. Chi è $W_7$?
> La normale al piano: $W_7=\mathrm{span}\{(1,2,-1)\}$.

> [!question]- 6. Diagonalizza ortogonalmente $A=\begin{bmatrix}2&1\\1&2\end{bmatrix}$.
> $p_A=(2-\lambda)^2-1=(\lambda-1)(\lambda-3)$. $W_1=\mathrm{span}\{(1,-1)\}$, $W_3=\mathrm{span}\{(1,1)\}$: già perpendicolari.
> $Q=\frac1{\sqrt2}\begin{bmatrix}1&1\\-1&1\end{bmatrix}$, $D=\mathrm{diag}(1,3)$.
