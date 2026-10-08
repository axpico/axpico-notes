---
tags:
  - geometria-algebra-lineare
  - fondamenti
  - applicazioni
  - funzioni
---
## Applicazioni (terminologia generale)

### Definizione

Siano $X$ e $Y$ due insiemi. Un'**applicazione** (o **funzione astratta**, o **mappa**) $f:X\to Y$ è una regola che associa a **ogni** elemento $x\in X$ **un unico** elemento di $Y$, indicato $f(x)$. (Definizione informale; formalmente $f$ è un sottoinsieme del prodotto cartesiano $X\times Y$ in cui ogni $x$ compare in esattamente una coppia $(x,y)$.) Quindi: tramite $f$, ad ogni $x\in X$ corrisponde **un unico** $y=f(x)\in Y$.

### Terminologia

| Termine | Significato |
|---|---|
| **dominio** | l'insieme $X$ |
| **codominio** | l'insieme $Y$ |
| **immagine di $x$** (o *valore di $f$ in $x$*) | $f(x)$ |
| **immagine di un sottoinsieme** $A\subseteq X$ | $f(A):=\{f(x):x\in A\}$ |
| **immagine di $f$** | $\operatorname{im}(f):=f(X)$, l'immagine dell'intero dominio |
| **controimmagine di un punto** $y\in Y$ | ogni $x\in X$ tale che $f(x)=y$ |
| **controimmagine di un sottoinsieme** $B\subseteq Y$ | $f^{-1}(B):=\{x\in X:\ f(x)\in B\}$ (l'insieme delle controimmagini dei punti di $B$) |

**Attenzione alla notazione:** $f^{-1}(B)$ è definita per *qualsiasi* $f$ (è solo un insieme) e **non** presuppone che $f$ sia invertibile.

#### Esempio: $f:\mathbb R\to\mathbb R$, $f(x)=x^2$

- $f((-1,1))=[0,1)$; (se invece $A=[-1,1]$ si ha $f(A)=[0,1]$);
- $\operatorname{im}(f)=f(\mathbb R)=[0,+\infty)$;
- le controimmagini di $y=4$ sono $x=2$ e $x=-2$; l'unica controimmagine di $y=0$ è $x=0$; se $y<0$ non ci sono controimmagini;
- $f^{-1}([-2,4))=(-2,2)$ (perché $x^2<4\iff|x|<2$ e $x^2\ge-2$ sempre);
- $f^{-1}([1,4])=[-2,-1]\cup[1,2]$;
- $f^{-1}((-1,0))=\varnothing$ (nessun quadrato è negativo).

### Iniettività, suriettività, biiettività

Per definizione ogni $x\in X$ ha **esattamente una** immagine; invece il **numero di controimmagini** di un $y\in Y$ può variare (zero, una, più di una). Questo porta a tre classi di applicazioni.

**Definizione.** $f:X\to Y$ si dice:

- **iniettiva** se ogni $y\in Y$ ha **al massimo una** controimmagine. Condizione equivalente: $x_1\ne x_2\Rightarrow f(x_1)\ne f(x_2)$ (oppure, per contrapposizione, $f(x_1)=f(x_2)\Rightarrow x_1=x_2$);
- **suriettiva** se ogni $y\in Y$ ha **almeno una** controimmagine. Condizione equivalente: $f(X)=Y$ (immagine = codominio);
- **biiettiva** (o **biunivoca**) se ogni $y\in Y$ ha **esattamente una** controimmagine. Quindi $f$ è biiettiva $\iff$ è iniettiva **e** suriettiva.

#### Esempi

- $g(x)=e^x$, $g:\mathbb R\to\mathbb R$ è **iniettiva** (strettamente crescente), ma non suriettiva ($\operatorname{im}g=(0,+\infty)$); $f(x)=x^2$ **non** è iniettiva ($f(2)=f(-2)$) e **non** è suriettiva ($f(\mathbb R)=[0,+\infty)\ne\mathbb R$).
- $g(x)=x^3-3x$ è **suriettiva** (polinomio di grado dispari: $g(\mathbb R)=\mathbb R$ per il teorema dei valori intermedi, essendo $g\to\pm\infty$ per $x\to\pm\infty$) ma **non** iniettiva ($g(0)=g(\sqrt3)=0$, $g$ ha un massimo e un minimo locali).
- $h(x)=x^3$, $h:\mathbb R\to\mathbb R$ è **biiettiva**; $f(x)=x^2$ e $g(x)=x^3-3x$ non lo sono. (Anche $e^x$ diventa biiettiva se si restringe il codominio a $(0,+\infty)$.)

#### Quadro riassuntivo (diagrammi a frecce)

| Tipo | Controimmagini dei punti di $Y$ |
|---|---|
| biiettiva | ogni $y$ ne ha esattamente una |
| iniettiva ma non suriettiva | alcuni $y$ non ne hanno, gli altri ne hanno una sola |
| suriettiva ma non iniettiva | ogni $y$ ne ha almeno una, qualcuno più di una |
| né iniettiva né suriettiva | alcuni $y$ non ne hanno, alcuni ne hanno più di una |

### Applicazione inversa

Se $f:X\to Y$ è biiettiva, a ogni $y\in Y$ si associa la sua unica controimmagine: si ottiene l'applicazione **inversa** $f^{-1}:Y\to X$, con $f^{-1}(f(x))=x$ e $f(f^{-1}(y))=y$. Si noti il legame con le matrici: l'applicazione $x\mapsto Ax$ di $\mathbb R^n$ in sé è biiettiva **se e solo se** $A$ è invertibile (condizione (v) del Teorema 4 in [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]), e l'inversa è $y\mapsto A^{-1}y$.

### Esercizio: le traslazioni sono biiettive

*Dato un vettore libero $\vec v$ del piano euclideo $E_2$, la traslazione $\tau_{\vec v}:E_2\to E_2$ è iniettiva? suriettiva? nessuna delle due?*

**Soluzione: è biiettiva.** Per definizione $\tau_{\vec v}(A)=B\iff\overrightarrow{AB}=\vec v\iff\overrightarrow{BA}=-\vec v\iff\tau_{-\vec v}(B)=A$. Quindi:

- *suriettiva*: dato un qualunque punto $B$, il punto $A:=\tau_{-\vec v}(B)$ soddisfa $\tau_{\vec v}(A)=B$ (esiste una controimmagine);
- *iniettiva*: se $\tau_{\vec v}(A_1)=\tau_{\vec v}(A_2)=B$ allora $A_1=\tau_{-\vec v}(B)=A_2$ (per l'unicità del punto iniziale, cioè la controimmagine è unica).

L'inversa è $\tau_{\vec v}^{-1}=\tau_{-\vec v}$. (Per $\vec v=\vec 0$ la traslazione è l'identità.)

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Vettori geometrici liberi.md|Vettori geometrici liberi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Matrici quadrate e matrice inversa.md|Matrici quadrate e matrice inversa]]
- [[Politecnico/Analisi 1/Teoria/Funzioni.md|Analisi — Funzioni]]
- [[Politecnico/Geometria e Algebra Lineare/Esercizi/Vettori, spazi vettoriali, sottospazi e applicazioni — Esercizi svolti.md|Esercizi — Vettori, spazi vettoriali, sottospazi e applicazioni]]
