L'equazione $x^2 + 1 = 0$ **non ha soluzioni in $\mathbb{R}$** (perché $x^2 \geq 0$ sempre). Si introduce quindi l'**unità immaginaria**:

**Definizione.** $i$ è un numero tale che $i^2 = -1$.

Con questo simbolo, $x^2 + 1 = 0 \Rightarrow x^2 = -1$, con soluzioni $x_1 = i$, $x_2 = -i$. Verifica:
$$
(x_1)^2 = (i)^2 = -1, \qquad (x_2)^2 = (-i)^2 = (-1)^2(i)^2 = -1.
$$

**Definizione (numero complesso).** Un numero complesso è un'espressione della forma
$$
z = a + ib, \qquad a, b \in \mathbb{R}
$$
detta **forma algebrica**. Si chiama:
- $a = \mathrm{Re}(z)$ **parte reale**
- $b = \mathrm{Im}(z)$ **parte immaginaria**

L'insieme dei numeri complessi si indica con $\mathbb{C}$.

### Somma

Per $z = a+ib$, $w = c+id \in \mathbb{C}$ (con $a,b,c,d \in \mathbb{R}$):
$$
z + w = (a+c) + i(b+d).
$$
Si sommano cioè separatamente le parti reali e le parti immaginarie: $\mathrm{Re}(z+w) = a+c$, $\mathrm{Im}(z+w) = b+d$.

### Prodotto

$$
z \cdot w = (a+bi)(c+di) = ac + adi + cbi + bdi^2 = ac + i(bc+ad) - bd = (ac - bd) + i(bc+ad),
$$
usando $i^2 = -1$. Quindi
$$
\mathrm{Re}(zw) = ac - bd, \qquad \mathrm{Im}(zw) = bc + ad.
$$

### Opposto

L'opposto rispetto alla somma di $z = a+ib$ è $-z = -a - bi$ (cambia segno a entrambe le parti).

### Inverso (rispetto al prodotto) e coniugato

Dato $z = a+ib \neq 0$, si cerca $w$ tale che $zw = 1$: $w = z^{-1}$.

Si introduce il **coniugato**: per $z = a+ib \in \mathbb{C}$,
$$
\bar{z} = a - ib \in \mathbb{C}
$$
(si cambia il segno solo alla parte immaginaria).

Il coniugato serve a "razionalizzare" il denominatore: moltiplicando numeratore e denominatore per $\bar z$,
$$
z^{-1} = \frac{1}{a+ib} = \frac{a - ib}{(a+ib)(a-ib)} = \frac{a-ib}{a^2+b^2},
$$
perché $(a+ib)(a-ib) = a^2 - (ib)^2 = a^2 + b^2 \in \mathbb{R}$ (il prodotto di $z$ per il suo coniugato è sempre reale e non negativo). Esplicitamente:
$$
z^{-1} = \frac{a}{a^2+b^2} + i\, \frac{-b}{a^2+b^2}, \qquad \underbrace{\frac{a}{a^2+b^2}}_{\mathrm{Re}} , \ \underbrace{\frac{-b}{a^2+b^2}}_{\mathrm{Im}}.
$$

Questa costruzione (moltiplicare per il coniugato per eliminare la parte immaginaria dal denominatore) è la tecnica standard per dividere numeri complessi ed è l'analogo della "razionalizzazione" con le radici quadrate nei numeri reali.

### Proprietà del coniugato

Per $z = a+ib \in \mathbb{C}$:

1. $z \cdot \bar z = a^2+b^2 \in \mathbb{R}_{\geq 0}$
2. $\dfrac{1}{z} = \dfrac{\bar z}{a^2+b^2} = \dfrac{\bar z}{z \bar z}$

**Oss.** Il coniugato del coniugato restituisce il numero di partenza: $\overline{\bar z} = z$.

### Modulo in $\mathbb{C}$

**Definizione.** Il **modulo** di $z = a+ib$ è
$$
|z| = \sqrt{a^2+b^2} \in \mathbb{R}_{\geq 0}.
$$

Dalla definizione di modulo e dalla proprietà 1 sopra segue subito
$$
z \cdot \bar z = |z|^2, \qquad \frac{\bar z}{a^2+b^2} = \frac{\bar z}{|z|^2}.
$$

**Proprietà del modulo.** Per ogni $z \in \mathbb{C}$:

1. $|z| \geq 0$
2. $|z| = 0 \iff z = 0$ (cioè $a = b = 0$)
3. $|\mathrm{Re}(z)| = |a| \leq |z|$
4. $|\mathrm{Im}(z)| = |b| \leq |z|$
5. $z + \bar z = 2a = 2\,\mathrm{Re}(z)$
6. $z - \bar z = 2ib = 2i\,\mathrm{Im}(z)$

Le proprietà 3–4 seguono dal fatto che $a^2 \leq a^2+b^2$ e $b^2 \leq a^2+b^2$; le proprietà 5–6 si verificano sommando/sottraendo direttamente $z = a+ib$ e $\bar z = a-ib$.

### Divisione

Dati $z, w \in \mathbb{C}$ con $w \neq 0$, dividere per $w$ significa moltiplicare per il suo inverso:
$$
\frac{z}{w} = z \cdot w^{-1} = z \cdot \frac{\bar w}{|w|^2}.
$$

**Esempio.**
$$
\frac{1-2i}{1+i} = (1-2i)\frac{1-i}{2} = \frac{1 - i - 2i + 2i^2}{2} = \frac{-1-3i}{2} = -\frac{1}{2} - \frac{3}{2}i.
$$

**Oss. (disuguaglianza triangolare).** $|z+w| \leq |z| + |w|$ per ogni $z,w \in \mathbb{C}$.

## Rappresentazione dei numeri complessi

### Piano complesso (di Argand-Gauss)

Un numero complesso $z = a+ib$ si può rappresentare come il punto $(a,b)$ del piano cartesiano, dove l'asse orizzontale è l'**asse reale** ($\mathrm{Re}\,z$) e l'asse verticale è l'**asse immaginario** ($\mathrm{Im}\,z$). Il modulo $|z| = \sqrt{a^2+b^2}$ è geometricamente la distanza del punto $z$ dall'origine, cioè la lunghezza del vettore che va da $0$ a $z$.

**Esempio grafico:** il punto $z = 1+i$ nel piano di Argand-Gauss, con il segmento (vettore) dall'origine e la circonferenza di raggio $|z|=\sqrt2$ che mostra il modulo:

```desmos-graph
left=-2.5; right=2.5;
top=2.5; bottom=-2.5;
grid=true
---
(1,1)|label:z=1+i
y=x\left\{0\le x\le1\right\}
x^{2}+y^{2}=2
```

### Forma trigonometrica

Dato $z = x+iy \neq 0$, ponendo $r = |z| = \sqrt{x^2+y^2}$ e $\theta$ l'angolo (in radianti) formato dal vettore $z$ con l'asse reale positivo, si ha
$$
x = r\cos\theta, \qquad y = r\sin\theta,
$$
da cui la **forma trigonometrica**:
$$
z = r(\cos\theta + i\sin\theta).
$$

$\theta$ si chiama **argomento** di $z$. Scegliendo $\theta \in [0, 2\pi)$ si parla di **argomento principale**, calcolabile come
$$
\theta = \arctan\!\left(\frac{y}{x}\right) \quad (x>0), \qquad \theta = \arctan\!\left(\frac{y}{x}\right) + \pi \quad (x<0).
$$
(Per $x=0$ si ha $\theta = \pi/2$ se $y>0$, $\theta = 3\pi/2$ se $y<0$.)

**Esercizio.** Passare $z = 1+i$ dalla forma algebrica a quella trigonometrica:
$$
r = \sqrt{1^2+1^2} = \sqrt2, \qquad \theta = \arctan(1) = \frac{\pi}{4},
$$
$$
z = \sqrt2\left(\cos\frac{\pi}{4} + \sin\frac{\pi}{4}\,i\right).
$$

### Prodotto in forma trigonometrica

Siano $z = r(\cos\theta+i\sin\theta)$ e $w = R(\cos\varphi+i\sin\varphi)$. Usando le formule di addizione di seno e coseno:
$$
z\cdot w = rR\big[(\cos\theta\cos\varphi - \sin\theta\sin\varphi) + i(\sin\theta\cos\varphi+\cos\theta\sin\varphi)\big] = rR\big[\cos(\theta+\varphi) + i\sin(\theta+\varphi)\big].
$$

**Il modulo del prodotto è il prodotto dei moduli, e l'argomento del prodotto è la somma degli argomenti.**

**Interpretazione geometrica.** Moltiplicare $z$ per $w = R(\cos\varphi+i\sin\varphi)$ equivale a:
- **ruotare** $z$ di un angolo $\varphi$ (in senso antiorario), e
- **riscalare** $z$ di un fattore $R$: se $R>1$ si ha una **dilatazione**, se $R<1$ una **compressione**.

### Elevamento a potenza — Formula di De Moivre

Per $z = r(\cos\theta+i\sin\theta) \in \mathbb{C}$ e $n \in \mathbb{N}$, applicando $n$ volte la formula del prodotto:
$$
z^n = r^n\big(\cos(n\theta) + i\sin(n\theta)\big).
$$

### Forma esponenziale — Identità di Eulero

Si definisce, per $\theta \in \mathbb{R}$,
$$
e^{i\theta} = \cos\theta + i\sin\theta \qquad \text{(identità di Eulero)}.
$$
Un numero complesso $z = r(\cos\theta+i\sin\theta)$ si scrive quindi in **forma esponenziale** come
$$
z = re^{i\theta}.
$$
Con $w = Re^{i\varphi}$, prodotto e potenza diventano particolarmente semplici:
$$
z\cdot w = rR\,e^{i(\theta+\varphi)}, \qquad z^n = r^n e^{in\theta}.
$$

## Teorema fondamentale dell'algebra

**Teorema (fondamentale dell'algebra).** Un'equazione polinomiale
$$
a_n z^n + a_{n-1}z^{n-1} + \dots + a_1 z + a_0 = 0, \qquad a_i \in \mathbb{C} \ \ \forall i=0,\dots,n, \ \ a_n \neq 0,
$$
ammette **esattamente $n$ soluzioni in $\mathbb{C}$**, purché contate con la loro **molteplicità**. Il numero $n$ è il **grado** dell'equazione.

Questo teorema è ciò che garantisce, in particolare, che ogni numero complesso $w \neq 0$ abbia esattamente $n$ radici $n$-esime distinte (sono le $n$ soluzioni dell'equazione $z^n - w = 0$, di grado $n$): è il risultato che rende sensato ed esaustivo il calcolo fatto sotto.

## Radici $n$-esime di un numero complesso

**Definizione.** Dato $w \in \mathbb{C}$ e $n \in \mathbb{N}$, un numero $z \in \mathbb{C}$ è una **radice $n$-esima** di $w$ se
$$
z^n = w.
$$

Scrivendo $w = Re^{i\varphi}$ e cercando $z = re^{i\theta}$ tale che $z^n = w$:
$$
r^n e^{in\theta} = Re^{i\varphi} \quad\Longrightarrow\quad r^n = R, \quad n\theta = \varphi + 2k\pi, \ k \in \mathbb{Z}.
$$
Da cui
$$
r = \sqrt[n]{R} \quad \text{(radice reale positiva)}, \qquad \theta = \frac{\varphi}{n} + \frac{2k\pi}{n}, \quad k \in \mathbb{Z}.
$$
Al variare di $k$ in $\mathbb{Z}$ gli angoli $\theta$ si ripetono con periodo $n$ (perché $2\pi$ periodico), quindi bastano $n$ valori consecutivi di $k$ per ottenere tutte le soluzioni distinte, ad es. $k \in \{0,1,\dots,n-1\}$.

**Teorema.** Sia $w = Re^{i\varphi} \in \mathbb{C}$, $w \neq 0$. Allora le radici $n$-esime di $w$ sono **esattamente $n$**, distinte tra loro, e sono date da
$$
z_k = r\,e^{i\theta_k}, \qquad r = \sqrt[n]{R}, \qquad \theta_k = \frac{\varphi}{n} + \frac{2k\pi}{n}, \qquad k = 0,1,\dots,n-1.
$$

Geometricamente, le $n$ radici sono i vertici di un **poligono regolare di $n$ lati** inscritto nella circonferenza di raggio $r = \sqrt[n]{R}$ centrata nell'origine.

**Esempio grafico:** le 6 radici seste dell'unità ($w=1$, $R=1$, $\varphi=0$), cioè $z_k = \cos\frac{2k\pi}{6} + i\sin\frac{2k\pi}{6}$ per $k=0,\dots,5$, disposte sulla circonferenza unitaria:

```desmos-graph
left=-1.6; right=1.6;
top=1.6; bottom=-1.6;
grid=true
---
x^{2}+y^{2}=1
(1,0)|label:k=0
(0.5,0.866)|label:k=1
(-0.5,0.866)|label:k=2
(-1,0)|label:k=3
(-0.5,-0.866)|label:k=4
(0.5,-0.866)|label:k=5
```

## Esercizio riepilogativo

**Testo.**
1. Determinare le soluzioni in $\mathbb{C}$ di
$$
\left[z^3 - (1+\sqrt3\,i)^9\right]\big(z+\bar z + 1\big) = 0
$$
e rappresentarle nel piano complesso.
2. Detto $A$ l'insieme delle soluzioni, rappresentare l'insieme $B = \{w \in \mathbb{C} : w = iz,\ z\in A\}$.

Un prodotto di due fattori è nullo se e solo se **almeno uno dei due fattori è nullo**: l'equazione si spezza quindi in due equazioni indipendenti, le cui soluzioni vanno poi riunite (unione degli insiemi di soluzioni).

### Primo fattore: $z^3 = (1+\sqrt3\,i)^9$

Si porta $1+\sqrt3\,i$ in forma trigonometrica: $a=1$, $b=\sqrt3 \Rightarrow$ modulo $2$, argomento $\arctan(\sqrt3)=\frac{\pi}{3}$ (primo quadrante), quindi $1+\sqrt3\,i = 2e^{i\pi/3}$. Per De Moivre:
$$
(1+\sqrt3\,i)^9 = \left(2e^{i\pi/3}\right)^9 = 2^9 e^{i\,9\cdot\pi/3} = 512\,e^{i3\pi} = 512\,e^{i\pi}
$$
(perché $e^{i3\pi} = e^{i\pi}$, essendo $e^{i\theta}$ periodica di periodo $2\pi$). Si deve dunque risolvere
$$
z^3 = w, \qquad w = 512\,e^{i\pi} \quad (R=512,\ \varphi=\pi).
$$
Radici cubiche: $r = \sqrt[3]{512} = 8$, $\theta_k = \dfrac{\pi}{3}+\dfrac{2k\pi}{3}$, $k=0,1,2$:
$$
\theta_0=\frac{\pi}{3}, \qquad \theta_1 = \pi, \qquad \theta_2 = \frac{5}{3}\pi.
$$
$$
z_0 = 8\left(\cos\tfrac{\pi}{3}+i\sin\tfrac{\pi}{3}\right) = 4+4\sqrt3\,i,
$$
$$
z_1 = 8\left(\cos\pi+i\sin\pi\right) = -8,
$$
$$
z_2 = 8\left(\cos\tfrac{5}{3}\pi+i\sin\tfrac{5}{3}\pi\right) = 4-4\sqrt3\,i.
$$
Questi tre punti sono, come sempre per le radici $n$-esime, i vertici di un **triangolo equilatero** inscritto nella circonferenza di raggio $8$ centrata nell'origine.

### Secondo fattore: $z + \bar z + 1 = 0$

Con $z = a+ib$ ($a,b\in\mathbb{R}$): $\bar z = a - ib$, quindi $z+\bar z = 2a$ (Proprietà 5 del coniugato, vista sopra), e l'equazione diventa
$$
2a + 1 = 0 \ \Longrightarrow\ a = -\frac12.
$$
Le soluzioni sono quindi **tutti** i numeri complessi con parte reale $-\tfrac12$:
$$
z = -\frac12 + ib, \qquad \forall b \in \mathbb{R},
$$
cioè geometricamente la **retta verticale** $\mathrm{Re}(z) = -\tfrac12$ nel piano di Argand-Gauss.

### Insieme delle soluzioni $A$

$$
A = \left\{z\in\mathbb{C} : \mathrm{Re}(z) = -\tfrac12\right\} \ \cup\ \{z_0,\, z_1,\, z_2\}.
$$
I tre punti $z_0,z_1,z_2$ non appartengono alla retta (hanno parte reale $4,-8,4$), quindi $A$ è geometricamente **una retta verticale più tre punti isolati** (i vertici del triangolo equilatero calcolato sopra).

```desmos-graph
left=-11; right=8;
top=8; bottom=-8;
grid=true
---
x=-\frac12
(4,6.93)|label:z_0
(-8,0)|label:z_1
(4,-6.93)|label:z_2
```

### Insieme $B = \{w = iz : z \in A\}$

Moltiplicare per $i = 1\cdot e^{i\pi/2}$ **ruota di $\frac{\pi}{2}$** (in senso antiorario) e lascia invariato il modulo (Interpretazione geometrica del prodotto, vista sopra: $R=1$, quindi nessun riscalamento).

**Trasformazione della retta.** Se $z = -\tfrac12+ib$ ($b\in\mathbb{R}$):
$$
w = iz = i\left(-\tfrac12+ib\right) = -\frac{i}{2} + i^2 b = -b - \frac{i}{2}.
$$
Al variare di $b\in\mathbb{R}$, la parte reale $-b$ assume **tutti** i valori reali, mentre $\mathrm{Im}(w) = -\tfrac12$ resta fissa: la retta verticale ruota di $90°$ e diventa la **retta orizzontale**
$$
\mathrm{Im}(w) = -\frac12, \qquad w = a - \frac{i}{2},\ \ a\in\mathbb{R}.
$$

**Trasformazione dei tre punti** (stesso modulo $8$, argomento aumentato di $\frac{\pi}{2}$):
$$
w_0 = i z_0 = 8\,e^{i(\pi/3+\pi/2)} = 8\,e^{i5\pi/6} = -4\sqrt3+4i,
$$
$$
w_1 = i z_1 = 8\,e^{i(\pi+\pi/2)} = 8\,e^{i3\pi/2} = -8i,
$$
$$
w_2 = i z_2 = 8\,e^{i(5\pi/3+\pi/2)} = 8\,e^{i\pi/6} = 4\sqrt3+4i.
$$

$$
B = \left\{w\in\mathbb{C} : \mathrm{Im}(w) = -\tfrac12\right\} \ \cup\ \{w_0,\, w_1,\, w_2\}.
$$

```desmos-graph
left=-11; right=11;
top=8; bottom=-11;
grid=true
---
y=-\frac12
(-6.93,4)|label:w_0
(0,-8)|label:w_1
(6.93,4)|label:w_2
```

### Esempio: radici quadrate di un numero complesso

Calcolare $z \in \mathbb{C}$ tale che $z^2 = w$, con $w = -1+\sqrt3\,i$.

**1. Forma trigonometrica di $w$.** Con $a=-1$, $b=\sqrt3$:
$$
R = |w| = \sqrt{1+3} = 2.
$$
Il punto $(-1,\sqrt3)$ è nel secondo quadrante ($a<0$, $b>0$); l'angolo di riferimento è $\arctan\frac{\sqrt3}{1} = \frac{\pi}{3}$, quindi
$$
\varphi = \pi - \frac{\pi}{3} = \frac{2}{3}\pi.
$$
Dunque
$$
w = 2e^{i\frac{2}{3}\pi} = 2\left[\cos\!\left(\tfrac{2}{3}\pi\right) + i\sin\!\left(\tfrac{2}{3}\pi\right)\right].
$$

**2. Radici quadrate ($n=2$).** Si cerca $z = re^{i\theta}$ con $z^2=w$:
$$
r = \sqrt{R} = \sqrt2, \qquad \theta_k = \frac{\varphi}{2} + \frac{2k\pi}{2} = \frac{\pi}{3} + k\pi, \qquad k=0,1.
$$
$$
\theta_0 = \frac{\pi}{3}, \qquad \theta_1 = \frac{\pi}{3}+\pi = \frac{4}{3}\pi.
$$

**3. Le due radici.**
$$
z_0 = \sqrt2\,e^{i\pi/3} = \sqrt2\left(\cos\tfrac{\pi}{3}+i\sin\tfrac{\pi}{3}\right) = \sqrt2\left(\tfrac12+\tfrac{\sqrt3}{2}i\right) = \frac{\sqrt2}{2} + \frac{\sqrt6}{2}i,
$$
$$
z_1 = \sqrt2\,e^{i4\pi/3} = \sqrt2\left(\cos\tfrac{4\pi}{3}+i\sin\tfrac{4\pi}{3}\right) = \sqrt2\left(-\tfrac12-\tfrac{\sqrt3}{2}i\right) = -\frac{\sqrt2}{2} - \frac{\sqrt6}{2}i.
$$

Coerentemente con il teorema, $z_1 = -z_0$ (le due radici quadrate sono sempre opposte, essendo $\theta_1 = \theta_0 + \pi$, cioè una rotazione di $\pi$ = cambio di segno).

---

## Collegamenti

- [[Politecnico/Analisi 1/Teoria/Insieme numerici, logia e dimostrazioni.md|Analisi — Insiemi numerici, logica e dimostrazioni]]
- [[Politecnico/Analisi 1/Teoria/Funzioni.md|Analisi — Funzioni]]
- [[Politecnico/Analisi 1/Esercizi/Numeri Complessi.md|Esercizi — Numeri complessi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Insiemi, vettori e sistemi lineari — nozioni di base.md|Insiemi, vettori e sistemi lineari — nozioni di base]]
