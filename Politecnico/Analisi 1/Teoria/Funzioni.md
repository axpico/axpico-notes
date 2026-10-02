---
tags: [analisi1, funzioni, estremo-superiore, estremo-inferiore, funzioni-elementari, teoria]
---

## Definizione di funzione

**Definizione.** Siano $A$, $B$ due insiemi. Una **funzione** $f: A \to B$ è una legge che ad ogni elemento di $A$ associa **uno e un solo** elemento di $B$:
$$
y = f(x), \qquad x \in A,\ y \in B.
$$

- $A$ è il **dominio** di $f$.
- $B$ è il **codominio** di $f$.

**Definizione (immagine).** Si chiama **immagine** di $A$ attraverso $f$ l'insieme degli elementi di $B$ che provengono da (cioè sono il valore di $f$ calcolato in) qualche elemento di $A$:
$$
\mathrm{Im}\,f = f(A) = \{y \in B : \exists\, x \in A,\ y = f(x)\} \subseteq B.
$$
L'immagine è sempre un sottoinsieme del codominio, ma non necessariamente coincide con esso.

## Suriettività, iniettività, biettività

**Suriettività.** Se immagine e codominio coincidono, la funzione si dice **suriettiva**:
$$
f: A \to B \ \text{è suriettiva} \iff f(A) = B,
$$
cioè ogni elemento di $B$ è raggiunto da almeno un elemento di $A$.

**Iniettività.** $f$ si dice **iniettiva** se
$$
\forall x_1, x_2 \in A,\quad x_1 \neq x_2 \ \Longrightarrow\ f(x_1) \neq f(x_2),
$$
equivalentemente (contronominale, forma più usata nelle dimostrazioni):
$$
f(x_1) = f(x_2) \ \Longrightarrow\ x_1 = x_2.
$$
Cioè elementi diversi del dominio hanno sempre immagini diverse (nessun elemento di $B$ è raggiunto da più di un elemento di $A$).

**Biettività.** Se $f$ è **sia iniettiva che suriettiva**, si dice **biettiva** (o **bigettiva**, o **biunivoca**).

**Definizione (controimmagine).** Sia $f: A \to B$. Si chiama **controimmagine** di $D \subseteq B$ l'insieme
$$
f^{-1}(D) = \{x \in A : f(x) \in D\} \subseteq A.
$$
Attenzione: qui $f^{-1}(D)$ indica un **sottoinsieme del dominio** ed è definita per ogni funzione (anche non invertibile) e per ogni sottoinsieme $D$ del codominio — è un'operazione diversa dalla funzione inversa introdotta sotto (che richiede l'iniettività).

**Schema.** Dominio $A$ e codominio $B$, con l'immagine $f(A) \subseteq B$ e, dato $D\subseteq B$, la controimmagine $f^{-1}(D) \subseteq A$:

```
   A                    B
 ┌────────┐         ┌──────────────┐
 │  ┌──┐  │   f      │   ┌──────┐   │
 │  │  │──┼─────────▶│   │f(A)  │   │
 │  └──┘  │          │   └──────┘   │
 │f⁻¹(D)  │          │     D        │
 └────────┘         └──────────────┘
```

## Funzione inversa

- Se $f$ è **iniettiva**, allora è **invertibile su $f(A)$** (cioè ristretta alla sua immagine).
- Se $f$ è **iniettiva e suriettiva** (biettiva), allora è invertibile **su tutto $B$**.

In entrambi i casi si definisce la **funzione inversa**
$$
f^{-1}: f(A) \to A, \qquad y \mapsto f^{-1}(y) = x \quad \text{tale che } f(x)=y.
$$

**Osservazione.** Se $f: A \to B$ è iniettiva, allora:
$$
(f^{-1}\circ f)(x) = x \quad \forall x \in A, \qquad (f \circ f^{-1})(y) = y \quad \forall y \in f(A).
$$
Applicare $f$ e poi $f^{-1}$ (o viceversa) restituisce sempre il punto di partenza: è la proprietà caratteristica che definisce l'inversa.

## Funzione composta

**Definizione.** Siano $f: A \to B$ e $g: B \to C$. Si chiama **funzione composta** $g\circ f: A \to C$ la funzione
$$
(g\circ f)(x) = g(f(x)) \qquad \forall x \in A.
$$
Si scrive anche $h = g\circ f$, $h(x) = g(f(x))$. Perché la composizione abbia senso, il codominio di $f$ deve coincidere con (o essere contenuto in) il dominio di $g$.

**Osservazione.** $g\circ f$ e $f\circ g$, quando entrambe hanno senso, possono essere **diverse**: la composizione di funzioni **non è commutativa**.

**Esempio.** $f: \mathbb{R}\to\mathbb{R}$, $f(x)=x+1$; $g: \mathbb{R}\to\mathbb{R}$, $g(x)=x^2$.
$$
(g\circ f)(x) = g(f(x)) = (x+1)^2 = x^2+2x+1,
$$
$$
(f\circ g)(x) = f(g(x)) = x^2+1.
$$
Le due funzioni composte sono chiaramente diverse ($x^2+2x+1 \neq x^2+1$ in generale).

## Funzioni reali di variabile reale: insieme di definizione

Da qui in avanti si considerano funzioni $f: A \to B$ con $A \subseteq \mathbb{R}$, $B = \mathbb{R}$ (**funzioni reali di variabile reale**).

**Definizione (insieme/dominio di definizione).** Data un'espressione $f(x)$, l'**insieme di definizione** (o dominio naturale) di $f$ è l'insieme delle $x \in \mathbb{R}$ per le quali la funzione (o l'espressione) $f$ è **ben posta**, cioè ha significato ed è ben definita.

**Esempio.** $f: \mathbb{R} \to \mathbb{R}$, $f(x) = \log(1-x^2)$. L'argomento del logaritmo deve essere strettamente positivo:
$$
A = \{x \in \mathbb{R} : 1-x^2 > 0\} = (-1,1)
$$
è l'insieme di definizione di $f$.

## Monotonia

**Definizione.** Sia $A \subseteq \mathbb{R}$ e $f: A \to \mathbb{R}$. Si dice che $f$ è:

- **crescente** se $\forall x_1,x_2 \in A,\ x_1<x_2 \Rightarrow f(x_1)\leq f(x_2)$;
- **decrescente** se $\forall x_1,x_2 \in A,\ x_1<x_2 \Rightarrow f(x_1)\geq f(x_2)$;
- **strettamente crescente** se $\forall x_1,x_2 \in A,\ x_1<x_2 \Rightarrow f(x_1)<f(x_2)$;
- **strettamente decrescente** se $\forall x_1,x_2 \in A,\ x_1<x_2 \Rightarrow f(x_1)>f(x_2)$.

$f$ si dice **monotona** in $A$ se è crescente oppure decrescente in $A$ (l'aggettivo "stretta" si applica allo stesso modo).

**Rapporto incrementale.** Per $x_1,x_2 \in A$, $x_1\neq x_2$, si definisce il **rapporto incrementale**
$$
\frac{f(x_1)-f(x_2)}{x_1-x_2}.
$$
Questo rapporto misura la pendenza media di $f$ tra $x_1$ e $x_2$, ed è **sempre dello stesso segno lungo tutto $A$** se e solo se $f$ è monotona:
- $f$ crescente $\iff$ rapporto incrementale $\geq 0$ per ogni coppia $x_1\neq x_2 \in A$;
- $f$ decrescente $\iff$ rapporto incrementale $\leq 0$ per ogni coppia $x_1\neq x_2 \in A$.

**Osservazione importante.** Se $f$ è **strettamente monotona** allora è **iniettiva** (elementi diversi $x_1<x_2$ danno sempre $f(x_1)\neq f(x_2)$, essendo la disuguaglianza stretta). Il viceversa è **falso**: esistono funzioni iniettive non monotone (si veda l'esempio con $f(x)=1/x$ più sotto, ristretta a $\mathbb{R}\setminus\{0\}$).

## Grafico di una funzione

**Definizione.** Sia $f: A \to B$. Si dice **grafico** di $f$ l'insieme
$$
\mathrm{Gr}(f) = \{(x, f(x)) : x \in A\} \subseteq A \times B.
$$
Se $A \subseteq \mathbb{R}$ e $B \subseteq \mathbb{R}$, allora $\mathrm{Gr}(f) \subseteq \mathbb{R}\times\mathbb{R} = \mathbb{R}^2$, rappresentabile nel piano cartesiano $Oxy$.

## Esempi

**(i) Funzione crescente $\Rightarrow$ iniettiva.** Il grafico di una funzione strettamente crescente attraversa ogni retta orizzontale al più una volta: coerente con l'osservazione sulla monotonia sopra.

**(ii) Funzione non monotona $\Rightarrow$ non necessariamente iniettiva.** Se $f$ oscilla (non è né sempre crescente né sempre decrescente) in $[a,b]$, in generale non è iniettiva: una retta orizzontale può intersecare il grafico più volte.

**(iii) $f(x)=x^2$, $f:\mathbb{R}\to\mathbb{R}$.**
$$
\mathrm{Dom}\,f = \mathbb{R}, \qquad \mathrm{Im}\,f = [0,+\infty) \subset \mathbb{R}.
$$
Non è iniettiva (es. $f(-1)=f(1)=1$), non è monotona su tutto $\mathbb{R}$ (decresce su $(-\infty,0]$, cresce su $[0,+\infty)$), e non è suriettiva su $\mathbb{R}$ (l'immagine è solo $[0,+\infty)$).

```desmos-graph
left=-3; right=3;
top=6; bottom=-1;
grid=true
---
y=x^2
```

Cambiando dominio e codominio, le proprietà cambiano:

- $f: \mathbb{R} \to [0,+\infty)$, $f(x)=x^2$ è **suriettiva** (il codominio è ora esattamente l'immagine), ma resta non iniettiva.
- $f: [0,+\infty) \to \mathbb{R}$, $f(x)=x^2$ è **iniettiva** (su $[0,+\infty)$ la funzione è strettamente crescente) ed è quindi **invertibile** su $[0,+\infty)$:
$$
f^{-1}: f([0,+\infty)) \to [0,+\infty), \qquad f^{-1}(x) = \sqrt{x}.
$$
Il grafico di $f^{-1}$ è il simmetrico del grafico di $f$ rispetto alla bisettrice $y=x$ (proprietà generale delle funzioni inverse).

```desmos-graph
left=-1; right=6;
top=6; bottom=-1;
grid=true
---
y=x^2\{x\ge0\}
y=\sqrt{x}
y=x
```

**Osservazione.** $f: [0,+\infty)\to[0,+\infty)$, $f(x)=x^2$ è **biettiva** (iniettiva e suriettiva simultaneamente, restringendo sia dominio che codominio a $[0,+\infty)$).

**(iv) $f(x) = \dfrac{1}{x}$.** L'insieme di definizione è $A = \mathbb{R}\setminus\{0\}$ (il denominatore non può annullarsi), quindi $f: \mathbb{R}\setminus\{0\} \to \mathbb{R}$.

```desmos-graph
left=-5; right=5;
top=5; bottom=-5;
grid=true
---
y=1/x
```

Anche se $x_1 \neq 0$ e $x_2 \neq 0$ con $x_1\neq x_2$, si ha sempre $f(x_1)\neq f(x_2)$: $f$ è **iniettiva su tutto $\mathbb{R}\setminus\{0\}$**, ma **non è né crescente né decrescente** su tutto il dominio (decresce su $(-\infty,0)$, decresce separatamente su $(0,+\infty)$, ma il salto attorno a $0$ impedisce la monotonia globale — è l'esempio annunciato sopra di funzione iniettiva non monotona).

Ristretta a un solo intervallo, invece, è monotona:
- $f: (0,+\infty) \to \mathbb{R}$, $f(x)=1/x$ è **decrescente**;
- $f: (-\infty,0) \to \mathbb{R}$, $f(x)=1/x$ è **decrescente**.

## Funzioni pari e dispari

**Definizione.** Sia $f: \mathbb{R}\to\mathbb{R}$. Si dice:
- **pari** se $f(x) = f(-x) \ \ \forall x \in \mathbb{R}$;
- **dispari** se $f(-x) = -f(x) \ \ \forall x \in \mathbb{R}$.

**Esempio (pari).** $f(x)=x^2$ è pari: $x^2 = (-x)^2$. Il grafico è **simmetrico rispetto all'asse delle ordinate**.

**Esempio (dispari).** $f(x)=x^3$, $f:\mathbb{R}\to\mathbb{R}$, è biettiva, strettamente crescente, e giace nel $1°$ e $3°$ quadrante (essendo positiva per $x>0$ e negativa per $x<0$); è dispari:
$$
-f(-x) = -(-x)^3 = -(-x^3) = x^3 = f(x) \quad \Longrightarrow \quad f(-x) = -f(x).
$$
Il grafico di una funzione dispari è **simmetrico rispetto all'origine**.

```desmos-graph
left=-2; right=2;
top=3; bottom=-3;
grid=true
---
y=x^3
```

**In generale.** $f(x) = x^n$ ($n \in \mathbb{N}$):
- è **pari** se $n$ è pari;
- è **dispari** se $n$ è dispari.

## Funzioni periodiche

**Definizione.** Sia $f: \mathbb{R}\to\mathbb{R}$ e $T>0$. $f$ si dice **periodica di periodo $T$** se
$$
f(x+T) = f(x) \qquad \forall x \in \mathbb{R}.
$$
Se $f$ è periodica di periodo $T$, lo è anche di periodo $kT$ per ogni $k\in\mathbb{N}$, $k\geq1$; si parla di **periodo minimo** (o fondamentale) quando si intende il più piccolo $T>0$ con questa proprietà.

**Esempio.** Le funzioni trigonometriche sono l'esempio principale di funzioni periodiche: $f(x)=\sin(x)$ è periodica di periodo $2\pi$.

```desmos-graph
left=-8; right=8;
top=2; bottom=-2;
grid=true
---
y=\sin(x)
```

**Esempio (onda quadra).** Una funzione a gradino che alterna i valori $1$ e $-1$ su intervalli di ampiezza $1$ (es. $f(x)=1$ su $[2k,2k+1)$, $f(x)=-1$ su $[2k+1,2k+2)$, $k\in\mathbb{Z}$) ha periodo $T=2$.

## Estremo superiore ed estremo inferiore di una funzione

**Definizione (limitatezza superiore/inferiore).** Sia $f: A \subseteq \mathbb{R} \to \mathbb{R}$.
- $f$ è **limitata superiormente** su $A$ se $f(A) \subseteq \mathbb{R}$ è limitato superiormente, cioè
$$
\exists\, M \in \mathbb{R} \ \text{t.c.}\ f(x) \leq M \quad \forall x \in A.
$$
- $f$ è **limitata inferiormente** su $A$ se $f(A) \subseteq \mathbb{R}$ è limitato inferiormente, cioè
$$
\exists\, m \in \mathbb{R} \ \text{t.c.}\ f(x) \geq m \quad \forall x \in A.
$$
- $f$ è **limitata** su $A$ se è limitata sia superiormente sia inferiormente.

**Esempio.** $f: \mathbb{R} \to \mathbb{R}$, $f(x) = \arctan(x)$, con $f(\mathbb{R}) = \left(-\dfrac{\pi}{2}, \dfrac{\pi}{2}\right)$. L'arcotangente è limitata sia superiormente sia inferiormente (il grafico resta compreso tra le due asintoti orizzontali $y = \pm\pi/2$, senza mai raggiungerle).

```desmos-graph
left=-10; right=10;
top=2.5; bottom=-2.5;
grid=true
---
y=\arctan(x)
```

Graficamente: se $f$ è limitata superiormente esiste una retta orizzontale $y=M$ che il grafico non supera mai; se è limitata inferiormente esiste $y=m$ che il grafico non scende mai sotto; una funzione **illimitata superiormente** (es. $f(x)=e^{-x}$ per $x\to-\infty$) non ammette invece alcuna retta $y=M$ che la maggiori su tutto $A$.

**Definizione (estremo superiore/inferiore e massimo/minimo di una funzione).** Sia $f: A \to \mathbb{R}$. Si definiscono
$$
\sup_A f := \sup f(A), \qquad \inf_A f := \inf f(A),
$$
$$
\max_A f := \max f(A), \qquad \min_A f := \min f(A),
$$
quando questi ultimi due esistono (cioè quando l'estremo superiore/inferiore di $f(A)$ appartiene a $f(A)$, cioè è un valore effettivamente assunto da $f$).

**Esempio.** $f: A \to \mathbb{R}$, $A = (0,+\infty)$, $f(x) = \dfrac{1}{x}$. Si vogliono trovare $\sup$ e $\inf$ di $f$ in $A$.

```desmos-graph
left=0; right=6;
top=6; bottom=-1;
grid=true
---
y=1/x
```

$$
\sup_A f := \sup f(A) = \sup_{x\in(0,+\infty)} f = \sup f\big((0,+\infty)\big) = +\infty
$$
quindi $f$ è **illimitata superiormente** su $A$.
$$
\inf_A f = 0
$$
quindi $f$ è **limitata inferiormente** su $A$ (l'estremo inferiore $0$ non è mai raggiunto: $1/x > 0$ per ogni $x>0$).

Di conseguenza $f$ **non** è limitata superiormente ma **è** limitata inferiormente; non ammette né massimo né minimo su $A$ (l'estremo superiore non è finito, e l'estremo inferiore $0 \notin f(A)$).

## Funzioni elementari

Si passano in rassegna le funzioni elementari $f: \mathbb{R} \to \mathbb{R}$ (o su opportuni sottoinsiemi), con dominio, limitatezza e principali proprietà.

### a) Funzioni lineari (affini)

$$
f(x) = ax+b, \qquad a,b \in \mathbb{R}.
$$
Retta di coefficiente angolare $a$ e intercetta $b$; dominio e codominio $\mathbb{R}$.

```desmos-graph
left=-5; right=5;
top=5; bottom=-5;
grid=true
---
y=2x+1
```

### b) Potenze

$$
f(x) = x^n, \qquad n \in \mathbb{N}.
$$
- Se $n$ è **pari**: grafico simmetrico rispetto all'asse $y$ (funzione pari), con minimo in $x=0$ (tipo parabola).
- Se $n$ è **dispari**: grafico simmetrico rispetto all'origine (funzione dispari), strettamente crescente (tipo cubica).

```desmos-graph
left=-3; right=3;
top=6; bottom=-6;
grid=true
---
y=x^4
y=x^3
```

**Potenze con esponente razionale.**
$$
f(x) = x^{p/q}, \qquad p,q \in \mathbb{N} \ \text{coprimi}.
$$
- Se $q$ è **pari**, $f$ è ben definita solo per $x \geq 0$ (es. $p=1,\ q=4$: $f(x) = x^{1/4} = \sqrt[4]{x}$).
- Se $q$ è **dispari**, $f$ è ben definita su tutto $\mathbb{R}$ (es. $p=1,\ q=3$: $f(x) = x^{1/3} = \sqrt[3]{x}$).

```desmos-graph
left=-3; right=3;
top=3; bottom=-3;
grid=true
---
y=x^{1/4}
y=x^{1/3}
```

**Potenze con esponente razionale negativo.**
$$
f(x) = x^{-p/q}, \qquad p,q \in \mathbb{N},\ q \neq 0.
$$
- Se $q$ è **pari**, $f$ è ben definita in $(0,+\infty)$: es. $f(x) = x^{-1/2} = \dfrac{1}{\sqrt{x}}$.
- Se $q$ è **dispari**, $f$ è ben definita in $\mathbb{R}\setminus\{0\}$: es. $p=q=1$, $f(x) = \dfrac{1}{x}$.

```desmos-graph
left=-3; right=3;
top=5; bottom=-5;
grid=true
---
y=1/\sqrt{x}
y=1/x
```

### c) Funzioni goniometriche (circolari)

$f(x) = \sin(x)$: funzione **periodica di periodo $2\pi$**, **limitata** sia superiormente sia inferiormente, con
$$
f(\mathbb{R}) = [-1,1], \qquad \sup_{\mathbb{R}} f = \max_{\mathbb{R}} f = 1, \qquad \inf_{\mathbb{R}} f = \min_{\mathbb{R}} f = -1.
$$
Le stesse proprietà di periodicità e limitatezza valgono per $f(x) = \cos(x)$.

```desmos-graph
left=-8; right=8;
top=2; bottom=-2;
grid=true
---
y=\sin(x)
y=\cos(x)
```

$$
f(x) = \operatorname{tg}(x) = \tan(x) = \frac{\sin(x)}{\cos(x)}
$$
definita in $\mathbb{R}\setminus\left\{\dfrac{\pi}{2}+k\pi,\ k\in\mathbb{Z}\right\}$; funzione periodica di periodo $T=\pi$; **illimitata** sia superiormente sia inferiormente.

$$
f(x) = \operatorname{ctg}(x) = \cot(x) = \frac{\cos(x)}{\sin(x)}
$$
definita in $\mathbb{R}\setminus\{k\pi,\ k\in\mathbb{Z}\}$; funzione periodica di periodo $T=\pi$; **illimitata** sia superiormente sia inferiormente.

```desmos-graph
left=-6.5; right=6.5;
top=5; bottom=-5;
grid=true
---
y=\tan(x)
```

### d) Funzioni circolari inverse

Le funzioni trigonometriche non sono iniettive su tutto il loro dominio naturale (sono periodiche), quindi per definirne l'inversa si **restringono** a un intervallo su cui risultano iniettive (e suriettive sull'immagine), rendendole così invertibili:

- $\sin(x)$ ristretto a $\left[-\dfrac{\pi}{2}, \dfrac{\pi}{2}\right]$ $\Rightarrow$ $f(x) = \arcsin(x): [-1,1] \to \left[-\dfrac{\pi}{2}, \dfrac{\pi}{2}\right]$.
- $\cos(x)$ ristretto a $[0,\pi]$ $\Rightarrow$ $f(x) = \arccos(x): [-1,1] \to [0,\pi]$.
- $\operatorname{tg}(x)$ ristretta a $\left(-\dfrac{\pi}{2}, \dfrac{\pi}{2}\right)$ $\Rightarrow$ $f(x) = \arctan(x): \mathbb{R} \to \left(-\dfrac{\pi}{2}, \dfrac{\pi}{2}\right)$.
- $\operatorname{ctg}(x)$ ristretta a $(0,\pi)$ $\Rightarrow$ $f(x) = \operatorname{arcctg}(x): \mathbb{R} \to (0,\pi)$.

```desmos-graph
left=-2; right=2;
top=4; bottom=-2;
grid=true
---
y=\arcsin(x)
y=\arccos(x)
```

### e) Esponenziale e logaritmo

$$
f: \mathbb{R} \to (0,+\infty), \qquad f(x) = a^x, \qquad a>0,\ a\neq 1.
$$
- Se $a>1$: $f$ è **strettamente crescente**.
- Se $0<a<1$: $f$ è **strettamente decrescente**.

In entrambi i casi $f$ è **limitata inferiormente** ($\inf_{\mathbb{R}} f = 0$, mai raggiunto) ma **illimitata superiormente** ($\sup_{\mathbb{R}} f = +\infty$).

Con dominio $\mathbb{R}$ e codominio $(0,+\infty)$, $f$ è **biiettiva**, quindi invertibile:
$$
f^{-1}: (0,+\infty) \to \mathbb{R}, \qquad a^x = y \ \Longleftrightarrow\ x = \log_a(y),
$$
cioè $f^{-1}(x) = \log_a(x)$, con $f^{-1}: (0,+\infty) \to \mathbb{R}$. Se $a>1$ il logaritmo è crescente; se $0<a<1$ è decrescente (grafico simmetrico rispetto alla bisettrice $y=x$ rispetto a quello dell'esponenziale, come per ogni funzione inversa).

```desmos-graph
left=-3; right=6;
top=5; bottom=-5;
grid=true
---
y=2^x
y=\log(x)/\log(2)
y=x
```

### f) Valore assoluto (modulo)

$$
f: \mathbb{R} \to \mathbb{R}, \qquad f(x) = |x|.
$$
$f$ è **limitata inferiormente** ($\inf_{\mathbb{R}} f = \min_{\mathbb{R}} f = 0$) ma **illimitata superiormente** ($\sup_{\mathbb{R}} f = +\infty$); è **pari**; $f(\mathbb{R}) = [0,+\infty)$; **non è iniettiva** (es. $f(-1)=f(1)=1$).

```desmos-graph
left=-5; right=5;
top=5; bottom=-1;
grid=true
---
y=\operatorname{abs}(x)
```

### g) La parte intera

**Definizione.** Dato $x \in \mathbb{R}$, si definisce
$$
[x] := \text{il più grande intero minore o uguale a } x
$$
(funzione "floor"). Esempi:
$$
[\pi] = 3, \qquad [2] = 2, \qquad [-\pi] = -4, \qquad [-0{,}5] = -1.
$$
Il grafico è una funzione **a gradini**, costante e uguale a $k$ su ogni intervallo $[k,k+1)$, $k \in \mathbb{Z}$, con un salto (discontinuità) in corrispondenza di ogni intero.

### h) Funzione segno

$$
f(x) = \operatorname{sgn}(x) :=
\begin{cases}
1 & \text{se } x>0 \\
0 & \text{se } x=0 \\
-1 & \text{se } x<0
\end{cases}
$$

### i) Funzioni iperboliche

$$
\sinh(x) := \frac{e^x - e^{-x}}{2}, \qquad \cosh(x) := \frac{e^x + e^{-x}}{2}, \qquad \operatorname{tgh}(x) := \frac{\sinh(x)}{\cosh(x)}.
$$

```desmos-graph
left=-3; right=3;
top=5; bottom=-5;
grid=true
---
y=\sinh(x)
y=\cosh(x)
y=\tanh(x)
```

**Identità fondamentale.** Analogamente all'identità $\sin^2(x)+\cos^2(x)=1$ per le funzioni circolari, per le funzioni iperboliche vale
$$
\cosh^2(x) - \sinh^2(x) = 1,
$$
che è l'equazione dell'**iperbole equilatera** $x^2-y^2=1$ (da cui il nome "iperboliche": il punto $(\cosh x, \sinh x)$ percorre un ramo di questa iperbole, così come $(\cos x, \sin x)$ percorre la circonferenza unitaria $x^2+y^2=1$).

---

## Collegamenti

- [[Politecnico/Analisi 1/Teoria/Insieme numerici, logia e dimostrazioni.md|Analisi — Insiemi numerici, logica e dimostrazioni]]
- [[Politecnico/Analisi 1/Teoria/Estremo superiore ed estremo inferiore, completezza di ℝ.md|Analisi — Estremo superiore ed inferiore, completezza di ℝ]]
- [[Politecnico/Analisi 1/Teoria/Successioni.md|Analisi — Successioni]]
- [[Politecnico/Analisi 1/Esercizi/Disequazioni.md|Esercizi — Disequazioni]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni (terminologia generale).md|Applicazioni (terminologia generale)]]
