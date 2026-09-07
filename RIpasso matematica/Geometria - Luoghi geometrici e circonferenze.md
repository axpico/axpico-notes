---
date: 2026-09-07
subject: matematica
topic: geometria - luoghi geometrici
tags:
  - matematica
  - geometria
  - circonferenza
  - luoghi-geometrici
---
# Lezione 4: Geometria — Warm-up

Corso di ripasso Matematica, laboratorio FDS (MOOC MAT101 Polimi).

## A) Ragioniamo

### 1. Quadrato con area doppia / tripla

Quadrato di lato $s$, area $s^2$. Un quadrato con area doppia ha lato $s\sqrt2$: si costruisce **sulla diagonale** del quadrato originale, perché la diagonale misura proprio $s\sqrt2$ (Pitagora: $s^2+s^2=2s^2$).

Per il **triplo dell'area** serve un lato $s\sqrt3$, ottenibile con un secondo passo di Pitagora: un triangolo rettangolo con cateti $s\sqrt2$ (la diagonale appena trovata) e $s$ ha ipotenusa
$$
\sqrt{(s\sqrt2)^2+s^2}=\sqrt{2s^2+s^2}=s\sqrt3
$$

**Sì, è costruibile** con riga e compasso (è la cosiddetta *spirale di Teodoro*: si concatenano triangoli rettangoli per ottenere $\sqrt2,\sqrt3,\sqrt4,\dots$). $\sqrt3$ è un numero costruibile.

### 2. L'errore degli Ateniesi (duplicazione del cubo)

Il volume di un cubo di lato $l$ è $l^3$. Raddoppiare il **lato** ($2l$) dà volume $(2l)^3=8l^3$: **otto volte** il volume originale, non il doppio.

Per raddoppiare davvero il volume serve un lato $l\sqrt[3]{2}$ (radice cubica di 2, $\approx 1{,}26\,l$).

Gli Ateniesi sbagliarono a raddoppiare il lato invece del volume. Il problema è noto come **duplicazione del cubo** (problema di Delo): a differenza di $\sqrt3$, $\sqrt[3]{2}$ **non è costruibile** con riga e compasso — è uno dei tre problemi classici greci dimostrati impossibili (insieme a trisezione dell'angolo e quadratura del cerchio).

## B) Pratica

### 1. Rapporto tra volume del cubo inscritto e circoscritto a una sfera di raggio $R$

**Cubo circoscritto** (la sfera è inscritta nel cubo, tangente alle facce): lo spigolo è $2R$.
$$
V_{circ} = (2R)^3 = 8R^3
$$

**Cubo inscritto** (i vertici del cubo toccano la sfera): la diagonale dello spazio del cubo è il diametro della sfera, $2R$. Per un cubo di spigolo $a$, la diagonale è $a\sqrt3$:
$$
a\sqrt3 = 2R \;\Rightarrow\; a = \frac{2R}{\sqrt3}
$$
$$
V_{insc} = a^3 = \frac{8R^3}{3\sqrt3} = \frac{8\sqrt3}{9}R^3
$$

**Rapporto:**
$$
\frac{V_{insc}}{V_{circ}} = \frac{8\sqrt3 R^3/9}{8R^3} = \frac{\sqrt3}{9} = \frac{1}{3\sqrt3} \approx 0{,}192
$$

### 2. Luogo geometrico equidistante dagli assi

Un punto $(x,y)$ ha distanza $|y|$ dall'asse delle ascisse (asse $x$) e distanza $|x|$ dall'asse delle ordinate (asse $y$). Equidistanza:
$$
|x| = |y|
$$
Il luogo è l'unione delle due **bisettrici dei quadranti**:
$$
y = x \quad \text{e} \quad y = -x
$$

```desmos-graph
left=-5; right=5; top=5; bottom=-5;
---
y=x
y=-x
```

### 3. Luogo dei punti a distanza 2 da $P=(2,3)$

È per definizione una circonferenza di centro $P$ e raggio 2:
$$
(x-2)^2 + (y-3)^2 = 4
$$

### 4. Circonferenza circoscritta al triangolo rettangolo

Vertici $A=(0,0)$, $B=(3,\sqrt3)$, $C=(4,0)$.

**Trovare l'angolo retto:** verifico i prodotti scalari dei lati nei vertici.
$$
\vec{BA}=(-3,-\sqrt3),\quad \vec{BC}=(1,-\sqrt3)
$$
$$
\vec{BA}\cdot\vec{BC} = -3\cdot1 + (-\sqrt3)(-\sqrt3) = -3+3 = 0
$$
L'angolo retto è in $B$, quindi l'**ipotenusa è $AC$** (da $(0,0)$ a $(4,0)$, lunga 4).

Per il teorema che l'angolo retto è inscritto in una semicirconferenza, il **centro** della circonferenza circoscritta è il punto medio dell'ipotenusa:
$$
M = \left(\frac{0+4}{2}, \frac{0+0}{2}\right) = (2,0), \qquad \text{raggio} = \frac{AC}{2}=2
$$

**Equazione della circonferenza:**
$$
(x-2)^2 + y^2 = 4
$$
Verifica con $B=(3,\sqrt3)$: $(3-2)^2+(\sqrt3)^2 = 1+3=4$ ✓.

```desmos-graph
left=-2; right=6; top=4; bottom=-4;
---
(x-2)^2+y^2=4
(0,0)|label:A
(3,\sqrt{3})|label:B
(4,0)|label:C
(2,0)|label:M
```

#### Rette $y=a$ (orizzontali)

Distanza dal centro $(2,0)$: $d=|a|$. Confronto col raggio 2:
- **Secante** ($d<2$): $-2 < a < 2$
- **Tangente** ($d=2$): $a=2$ oppure $a=-2$
- **Esterna** ($d>2$): $a<-2$ oppure $a>2$

#### Rette $x=b$ (verticali)

Distanza dal centro $(2,0)$: $d=|b-2|$. Confronto col raggio 2:
- **Secante**: $0 < b < 4$
- **Tangente**: $b=0$ oppure $b=4$
- **Esterna**: $b<0$ oppure $b>4$

#### Retta $y=kx+3$

Riscritta come $kx - y + 3 = 0$. Distanza dal centro $(2,0)$:
$$
d = \frac{|2k+3|}{\sqrt{k^2+1}}
$$
**Secante** quando $d<2$:
$$
|2k+3| < 2\sqrt{k^2+1} \;\Longleftrightarrow\; (2k+3)^2 < 4(k^2+1)
$$
$$
4k^2+12k+9 < 4k^2+4 \;\Longrightarrow\; 12k < -5 \;\Longrightarrow\; k < -\frac{5}{12}
$$

Quindi:
- **Secante**: $k < -\dfrac{5}{12}$
- **Tangente**: $k = -\dfrac{5}{12}$
- **Esterna**: $k > -\dfrac{5}{12}$

*Verifica rapida:* con $k=0$ la retta è $y=3$, orizzontale sopra il punto più alto della circonferenza ($y_{max}=2$) → esterna, coerente con $0 > -5/12$.
