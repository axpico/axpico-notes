---
tags:
  - geometria-algebra-lineare
  - diagonalizzazione
  - autovalori
  - autovettori
  - autospazi
---
# Autovalori, autovettori, autospazi e molteplicità

Fonte: Lezione 10, parte 1 (PDF "Diagonalizzazione Ver.2024", 53 pp.). Testo: ALG pp. 296–301, 305–312.
Prerequisiti: [[Similitudine, potenze e interpretazione geometrica del determinante]] · [[Cambio di base e matrice di passaggio]] · [[Teorema di rappresentazione e matrice rappresentativa]] · [[Rango e teorema di nullità più rango]].
Esercizi: [[Autovalori e autospazi — Esercizi svolti]] · HTML: [[Lezione 10 — Autovalori, autovettori e autospazi.html|Lezione 10 (interattiva)]]

## 0. Il problema (pp. 2–4)

Dato un endomorfismo $L:V\to V$ ($\dim V=n<\infty$), trovare una base $\mathcal B$ di $V$ (**se esiste!**) in cui la matrice rappresentativa di $L$ sia **diagonale**.

Se $\mathcal B=\{\underline v_1,\dots,\underline v_n\}$ è una tale base e $A=\mathrm{diag}(\lambda_1,\dots,\lambda_n)$, la colonna $j$ di $A$ è il vettore delle coordinate di $L(\underline v_j)$, cioè $\lambda_j\underline e_j$:
$$L(\underline v_j)=\lambda_j\underline v_j .$$
**Quindi diagonalizzare = trovare vettori non nulli $\underline v$ e scalari $\lambda$ con $L(\underline v)=\lambda\underline v$.**

## 1. Autovalori e autovettori di un endomorfismo (pp. 5–10)

> [!important] Definizione
> $L:V\to V$ lineare, $\underline v\in V$, $\lambda\in\mathbb K$. Se $\underline v\neq\underline 0$ e $L(\underline v)=\lambda\underline v$:
> - $\lambda$ è un **autovalore** di $L$;
> - $\underline v$ è un **autovettore** di $L$ relativo a $\lambda$.

Un autovettore è un vettore **non nullo** che $L$ manda in un suo multiplo: $L$ lo "allunga/accorcia/ribalta" senza cambiarne la direzione.

> [!warning] $\underline 0$ vs $0$
> - $\underline 0$ **non** è mai un autovettore (per definizione).
> - Lo scalare $\lambda=0$ **può** essere un autovalore.

**Esempio (proiezione).** $L(x,y,z)=(x,y,0)$. $\underline v=(0,0,1)$: $L(\underline v)=\underline 0=0\cdot\underline v$ ⇒ autovettore relativo a $\lambda=0$.

**In generale:** $\lambda=0$ è autovalore $\iff\ker L\neq\{\underline 0\}$, e gli autovettori relativi a $0$ sono i vettori non nulli di $\ker L$.

### Esempi in dimensione infinita (solo cultura)
- $V=C^\infty(\mathbb R)$, $L(f)=f'$. Autovettori: soluzioni non banali di $f'=\lambda f$, cioè $f(x)=c\,e^{\lambda x}$ con $c\neq0$. **Ogni** $\lambda\in\mathbb R$ è autovalore.
- $V=C(\mathbb R)$, $L(f)(x)=x\,f(x)$. Se $xf(x)=\lambda f(x)$ $\forall x$, allora $f(x)=0$ per $x\neq\lambda$, e per continuità $f\equiv0$. ⇒ **nessun autovettore.**
- Fisica: i livelli di energia di un atomo sono gli autovalori dell'**operatore hamiltoniano**; gli autovettori sono gli **stati stazionari**.

## 2. Dal caso astratto alle matrici (pp. 11–28)

Fissata una base $\mathcal B_0$ di $V$, sia $A\in M_{\mathbb K}(n,n)$ la matrice rappresentativa di $L$.

> [!important] Teorema 1
> Sono equivalenti:
> 1. $L$ è diagonalizzabile;
> 2. $A$ è simile **su $\mathbb K$** a una diagonale: $\exists S$ invertibile a coefficienti in $\mathbb K$ con
> $$S^{-1}AS=D .$$
>
> In tal caso, se $\underline x_j$ è la $j$-esima colonna di $S$ e $\lambda_j=d_{jj}$:
> $$A\underline x_j=\lambda_j\underline x_j .$$

*Dim.*
- **(i)⇒(ii).** $\mathcal B$ base in cui $L$ ha matrice $D$; $S$ = matrice di passaggio da $\mathcal B_0$ a $\mathcal B$. Per il teorema del cambio di base $D=S^{-1}AS$; gli elementi di $S$ sono coordinate ⇒ stanno in $\mathbb K$.
- **(ii)⇒(i).** Le colonne $\underline x_j$ di $S$ sono coordinate (rispetto a $\mathcal B_0$) di vettori $\underline v_j=\sum_i s_{ij}\underline u_i$. $S$ invertibile ⇒ $r(S)=n$ ⇒ colonne indipendenti ⇒ i $\underline v_j$ sono indipendenti ⇒ $\mathcal B=\{\underline v_j\}$ è una base. La matrice di passaggio $\mathcal B_0\to\mathcal B$ è $S$, quindi la matrice di $L$ in $\mathcal B$ è $S^{-1}AS=D$.
- **(iii).** Da $S^{-1}AS=D$ segue $A=SDS^{-1}$. Poiché $S^{-1}\underline x_j=\underline e_j$ e $D\underline e_j=\lambda_j\underline e_j$:
$$A\underline x_j=SDS^{-1}\underline x_j=SD\underline e_j=\lambda_jS\underline e_j=\lambda_j\underline x_j.\ \blacksquare$$

> [!note] Definizione (matrice diagonalizzabile)
> $A\in M_{\mathbb K}(n,n)$ è **diagonalizzabile su $\mathbb K$** se esistono $S$ invertibile e $D$ diagonale, entrambe in $M_{\mathbb K}(n,n)$, con $S^{-1}AS=D$.
> (Il PDF a p. 14 scrive $SAS^{-1}=D$: è equivalente, basta scambiare $S$ con $S^{-1}$. Usa $S^{-1}AS=D$: così **le colonne di $S$ sono gli autovettori**.)

**$\mathbb R$ vs $\mathbb C$.** Diagonalizzabile su $\mathbb R$ ⇒ diagonalizzabile su $\mathbb C$, ma non viceversa. "Diagonalizzabile" senza specificare = su $\mathbb C$.

> [!note] Definizione (autovalore/autovettore di una matrice)
> $\lambda\in\mathbb C$ è **autovalore** di $A$ se $\exists\,\underline x\in\mathbb C^n$, $\underline x\neq\underline 0$, con $A\underline x=\lambda\underline x$. Tale $\underline x$ è un **autovettore** relativo a $\lambda$.

**Conseguenze del Teorema 1.**
- $L$ diagonalizzabile $\iff$ $A$ diagonalizzabile su $\mathbb K$.
- Autovalori di $L$ = autovalori di $A$ che stanno in $\mathbb K$.
- Autovettori di $L$ ↔ autovettori di $A$ (questi sono le loro coordinate).
- $$\boxed{A\text{ diagonalizzabile su }\mathbb K\iff\mathbb K^n\text{ ha una base di autovettori di }A}$$
  con $S=[\underline x_1|\cdots|\underline x_n]$ (autovettori in colonna) e $D=\mathrm{diag}(\lambda_1,\dots,\lambda_n)$ (autovalori nello **stesso ordine**).

## 3. Come si trovano: autospazio e polinomio caratteristico (pp. 29–34)

> [!important] Proposizione 1
> $\lambda\in\mathbb K$ è autovalore di $A$ $\iff\ker(A-\lambda I)\neq\{\underline 0\}$. In tal caso gli autovettori relativi a $\lambda$ sono $\ker(A-\lambda I)\setminus\{\underline 0\}$.

*Dim.* $A\underline x=\lambda\underline x\iff A\underline x=\lambda I\underline x\iff(A-\lambda I)\underline x=\underline 0$. Quindi gli autovettori sono le soluzioni non nulle del sistema omogeneo, che esistono $\iff$ il nucleo non è banale. $\blacksquare$

> [!note] Definizione (autospazio)
> $V_\lambda:=\ker(A-\lambda I)$ è l'**autospazio** relativo all'autovalore $\lambda$. È un sottospazio (contiene $\underline 0$ e tutti gli autovettori di $\lambda$).

**Condizione col determinante.** $(A-\lambda I)\underline x=\underline 0$ ha soluzioni non banali $\iff r(A-\lambda I)<n\iff$
$$\boxed{\det(A-\lambda I)=0}$$

> [!important] Proposizione 2 + Definizione
> $p(\lambda):=\det(A-\lambda I)$ è un polinomio di grado $n$, il **polinomio caratteristico** di $A$. Gli autovalori sono le sue radici, e su $\mathbb C$:
> $$p(\lambda)=(\lambda_1-\lambda)(\lambda_2-\lambda)\cdots(\lambda_n-\lambda).$$

**Matrici triangolari:** $\det(A-\lambda I)=\prod(a_{ii}-\lambda)$ ⇒ gli autovalori sono gli **elementi diagonali**.

### Procedura (ricetta d'esame)
1. Calcola $p(\lambda)=\det(A-\lambda I)$ (Laplace sulla riga/colonna con più zeri, oppure operazioni di riga per raccogliere un fattore).
2. Trova le radici ⇒ autovalori con molteplicità.
3. Per ogni $\lambda$: riduci $A-\lambda I$ con Gauss, risolvi il sistema omogeneo ⇒ base di $V_\lambda$.
4. **Controllo:** verifica $A\underline x=\lambda\underline x$ per ogni vettore trovato.

**Controlli veloci:** $\operatorname{tr}A=\sum\lambda_i$ e $\det A=\prod\lambda_i$ (con molteplicità).

## 4. Errori tipici (pp. 46–50)

> [!warning] Gauss NON conserva gli autovalori
> Non ridurre $A$ e poi leggere gli autovalori sulla diagonale. Esempio 2: $A$ ha autovalori $2,1,1$; una sua ridotta $\begin{bmatrix}1&1&-1\\0&1&-1\\0&0&-2\end{bmatrix}$ ha $-2,1,1$. Gauss si usa su $A-\lambda I$ **dopo** aver fissato $\lambda$.

- **Verifica sempre** $A\underline x=\lambda\underline x$ (il PDF stesso sbaglia due autospazi, vedi sotto: questo controllo li avrebbe trovati).
- Un autospazio **non è mai banale**: se ti viene $\ker(A-\lambda I)=\{\underline 0\}$, o $\lambda$ non è autovalore o hai sbagliato i conti.
- $\dim V_\lambda=\#$ variabili libere $=n-r(A-\lambda I)$ (nullità + rango).

## 5. Molteplicità (pp. 50–53)

> [!important] Definizioni
> Sia $\lambda_0$ autovalore di $A$.
> - **Molteplicità algebrica** $m_a(\lambda_0)$: molteplicità di $\lambda_0$ come radice di $p(\lambda)$.
> - **Molteplicità geometrica** $m_g(\lambda_0):=\dim\ker(A-\lambda_0I)=n-r(A-\lambda_0I)$.
> - $\lambda_0$ **semplice** se $m_a=1$, **multiplo** se $m_a>1$.
> - $\lambda_0$ **regolare** se $m_g=m_a$, **irregolare** se $m_g<m_a$.

> [!important] Proposizione 3
> $$1\le m_g(\lambda_0)\le m_a(\lambda_0)$$
> In particolare **ogni autovalore semplice è regolare**. (senza dimostrazione)

Quindi i controlli servono solo sugli autovalori **multipli**. (Il criterio di diagonalizzabilità vero e proprio — tutti regolari + tutti in $\mathbb K$ — arriva nella parte 2.)

## 6. Esempi del PDF (riassunto)

| Matrice | $p(\lambda)$ | Autovalori ($m_a$) | Autospazi | $m_g$ |
|---|---|---|---|---|
| A: $\begin{bmatrix}2&1&1\\0&3&0\\0&0&-1\end{bmatrix}$ | $(2-\lambda)(3-\lambda)(-1-\lambda)$ | $2,3,-1$ (tutti 1) | $(1,0,0)$; $(1,1,0)$; $(-1,0,3)$ | 1,1,1 |
| Es.1: $\begin{bmatrix}3&0&-2\\1&1&-1\\1&0&0\end{bmatrix}$ | $(2-\lambda)(1-\lambda)^2$ | $2\,(1)$, $1\,(2)$ | $(2,1,1)$; $\{(0,1,0),(1,0,1)\}$ | 1, **2** → regolari |
| Es.2: $\begin{bmatrix}3&1&-3\\1&2&-2\\1&1&-1\end{bmatrix}$ | $(2-\lambda)(1-\lambda)^2$ | $2\,(1)$, $1\,(2)$ | $(2,1,1)$; $(1,1,1)$ | 1, **1** → $\lambda=1$ irregolare |

Es.1 ed Es.2 hanno **lo stesso** polinomio caratteristico ma comportamento diverso: gli autovalori da soli non bastano, serve $m_g$.

> [!bug] Errori nel PDF (verificati)
> - **p. 38, Esempio A, $\lambda=-1$:** l'elemento $(1,1)$ di $A+I$ è $2+1=3$, non $2$. Corretto: $V_{-1}=\mathrm{span}\{(-1,0,3)^T\}$ (il PDF dà $(-\tfrac12,0,1)^T$, che **non** è autovettore).
> - **p. 43, Esempio 2, $\lambda=2$:** l'elemento $(2,2)$ di $A-2I$ è $2-2=0$, non $-1$. Corretto: $V_2=\mathrm{span}\{(2,1,1)^T\}$ (il PDF dà $(5,1,2)^T$: $A(5,1,2)^T=(10,3,4)^T\neq2(5,1,2)^T$). La dimensione 1 resta giusta.
> - Lapsus minori: p. 8 "autovalori" per "autovettori"; p. 41 "non sono generatori, ma anche…" = "non solo sono generatori, ma anche…"; p. 51 $\lambda$ per $\lambda_0$.
