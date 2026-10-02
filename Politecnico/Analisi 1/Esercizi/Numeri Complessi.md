---
tags:
  - analisi1
  - numeri-complessi
  - forma-trigonometrica
  - forma-esponenziale
  - radici-n-esime
  - luoghi-geometrici-nel-piano-di-gauss
  - formula-di-de-moivre
  - equazioni-in-c
---

## Richiami teorici

Un numero complesso $z = x+iy$ ($x,y\in\mathbb{R}$) si scrive anche in:

- **forma trigonometrica:** $z = \rho(\cos\theta + i\sin\theta)$, con $\rho = |z| = \sqrt{x^2+y^2}$ e $\theta = \arg(z)$;
- **forma esponenziale:** $z = \rho\, e^{i\theta}$.

Proprietà utili:

$$\arg(z_1 z_2) = \arg(z_1)+\arg(z_2) \pmod{2\pi}, \qquad |z_1 z_2| = |z_1||z_2|$$

**Radici $n$-esime** di $w = \rho(\cos\theta+i\sin\theta)$: le $n$ soluzioni di $z^n = w$ sono

$$z_k = \rho^{1/n}\left[\cos\left(\frac{\theta+2k\pi}{n}\right) + i\sin\left(\frac{\theta+2k\pi}{n}\right)\right], \quad k = 0,1,\dots,n-1$$

(sono i vertici di un poligono regolare di $n$ lati inscritto in una circonferenza di raggio $\rho^{1/n}$).

---

## Esercizio 1 — luogo geometrico

Determinare la natura dell'insieme

$$S = \{z \in \mathbb{C}\setminus\{0\} : \arg(iz) = \tfrac{7}{6}\pi\}$$

tra le opzioni: a) una circonferenza; b) una retta per l'origine; c) una semiretta contenuta nel IV quadrante; d) una semiretta contenuta nel II quadrante.

**Svolgimento.** Scrivo $z=x+iy$. Allora

$$iz = i(x+iy) = -y+ix$$

cioè $iz$ ha parte reale $-y$ e parte immaginaria $x$. Uso la proprietà dell'argomento del prodotto ($i = \cos\frac{\pi}{2}+i\sin\frac{\pi}{2}$, quindi $\arg(i)=\frac{\pi}{2}$):

$$\arg(iz) = \arg(i) + \arg(z) \pmod{2\pi} \ \Longrightarrow\ \arg(z) = \frac{7}{6}\pi - \frac{\pi}{2} = \frac{7\pi-3\pi}{6} = \frac{4\pi}{6} = \frac{2}{3}\pi$$

Quindi

$$S = \left\{ z = \rho\left(\cos\tfrac{2\pi}{3}+i\sin\tfrac{2\pi}{3}\right) : \rho>0 \right\}$$

È l'insieme dei punti con argomento **fissato** e modulo **libero** (esclude l'origine, dove l'argomento non è definito): geometricamente è una **semiretta uscente dall'origine** (esclusa), di inclinazione $\frac{2}{3}\pi = 120°$. Poiché $\frac{\pi}{2}<\frac{2}{3}\pi<\pi$, la semiretta sta nel **secondo quadrante**.

$$\Longrightarrow \quad \textbf{risposta d)}$$

---

## Esercizio 2 — Primo parziale 2018

Risolvi in $\mathbb{C}$ e rappresenta le soluzioni nel piano complesso:

$$(z+\bar z)(z^6+11i) = 0$$

**Svolgimento.** Un prodotto è nullo se e solo se lo è (almeno) uno dei fattori:

$$(z+\bar z)=0 \quad\lor\quad (z^6+11i)=0$$

**Primo fattore:** con $z=x+iy$, $z+\bar z = 2\operatorname{Re}(z) = 2x$. Quindi

$$z+\bar z = 0 \iff \operatorname{Re}(z) = 0 \iff z \text{ è puramente immaginario}$$

Questo dà come soluzioni **tutto l'asse immaginario** (una retta, non un punto isolato).

**Secondo fattore:** $z^6 = -11i$. Scrivo $-11i$ in forma esponenziale: modulo $11$, argomento $\frac{3\pi}{2}$ (sta sul semiasse immaginario negativo):

$$-11i = 11\,e^{i\frac{3\pi}{2}} = 11\left(\cos\tfrac{3\pi}{2}+i\sin\tfrac{3\pi}{2}\right)$$

Applico il corollario delle radici $n$-esime con $n=6$, $\rho=11$, $\theta=\frac{3\pi}{2}$:

$$z_k = \sqrt[6]{11}\left[\cos\left(\frac{3\pi/2+2k\pi}{6}\right)+i\sin\left(\frac{3\pi/2+2k\pi}{6}\right)\right] = \sqrt[6]{11}\left[\cos\left(\frac{\pi}{4}+\frac{k\pi}{3}\right)+i\sin\left(\frac{\pi}{4}+\frac{k\pi}{3}\right)\right],\quad k=0,\dots,5$$

$$z_0 = \sqrt[6]{11}\left(\cos\tfrac{\pi}{4}+i\sin\tfrac{\pi}{4}\right),\ \ z_1=\sqrt[6]{11}\left(\cos\tfrac{7\pi}{12}+i\sin\tfrac{7\pi}{12}\right),\ \ \dots,\ \ z_5 = \sqrt[6]{11}\left(\cos\tfrac{23\pi}{12}+i\sin\tfrac{23\pi}{12}\right)$$

**Rappresentazione:** le 6 radici sono i vertici di un esagono regolare inscritto nella circonferenza di raggio $\sqrt[6]{11}$; l'insieme delle soluzioni totali è quell'esagono **unito** all'intero asse immaginario (la retta verticale per l'origine).

---

## Esercizio 3

Risolvi in $\mathbb{C}$:

$$\frac{i}{z^2} = (1+i)\,\bar z\,|z|$$

**Svolgimento.** C.E.: $z\ne 0$. Scrivo $z=r e^{i\theta}$ ($r>0$), e passo alla forma esponenziale dei coefficienti: $i=e^{i\pi/2}$, $1+i=\sqrt2\,e^{i\pi/4}$. Ricordo che $\bar z = re^{-i\theta}$ e $|z|=r$:

$$\frac{e^{i\pi/2}}{r^2e^{2i\theta}} = \sqrt2\,e^{i\pi/4}\cdot r e^{-i\theta}\cdot r$$

Moltiplico entrambi i membri per $r^2$:

$$e^{i(\pi/2-2\theta)} = \sqrt2\, r^4\, e^{i(\pi/4-\theta)}$$

Uguaglio **modulo** e **argomento** (mod $2\pi$) dei due membri:

$$\begin{cases} 1 = \sqrt2\, r^4 \\ \dfrac{\pi}{2}-2\theta \equiv \dfrac{\pi}{4}-\theta + 2k\pi, \quad k\in\mathbb{Z}\end{cases}$$

Dalla prima: $r^4 = \dfrac{1}{\sqrt2} = 2^{-1/2} \Rightarrow r = 2^{-1/8}$ (unica soluzione reale positiva, come richiesto dal modulo).

Dalla seconda: $\dfrac{\pi}{2}-\dfrac{\pi}{4} = \theta + 2k\pi \Rightarrow \theta = \dfrac{\pi}{4} + 2k\pi$, cioè un solo valore modulo $2\pi$: $\theta=\dfrac{\pi}{4}$.

**Unica soluzione:**

$$z = 2^{-1/8}\left(\cos\tfrac{\pi}{4}+i\sin\tfrac{\pi}{4}\right) = 2^{-1/8}\cdot\frac{1+i}{\sqrt2} = \frac{1+i}{2^{5/8}}$$

---

## Esercizio 4 — forma trigonometrica ed esponenziale

Esprimi in forma trigonometrica ed esponenziale:

**a)** $z=i$

$$|z|=1,\quad \arg(z)=\frac{\pi}{2} \ \Longrightarrow\ z=\cos\tfrac{\pi}{2}+i\sin\tfrac{\pi}{2} = e^{i\pi/2}$$

**b)** $z=\dfrac{1}{3i-3}$

Pongo $w=3i-3=-3+3i$ (denominatore), così $z=1/w$.

$$|w|=\sqrt{(-3)^2+3^2}=\sqrt{18}=3\sqrt2,\qquad \arg(w)=\frac{3\pi}{4}\ \text{(secondo quadrante)}$$

$$w = 3\sqrt2\left(\cos\tfrac{3\pi}{4}+i\sin\tfrac{3\pi}{4}\right) = 3\sqrt2\,e^{i3\pi/4}$$

Per il reciproco: $\left|\tfrac1w\right| = \tfrac{1}{|w|}$ e $\arg\!\left(\tfrac1w\right)=-\arg(w)$:

$$z = \frac{1}{w} = \frac{1}{3\sqrt2}\,e^{-i3\pi/4} = \frac{1}{3\sqrt2}\left[\cos\tfrac{3\pi}{4}-i\sin\tfrac{3\pi}{4}\right]$$

**Verifica in forma algebrica:** $z=\dfrac{1}{-3+3i}=\dfrac{-3-3i}{(-3)^2+3^2}=\dfrac{-3-3i}{18}=-\dfrac16-\dfrac16 i$ ✓ (coerente con il valore trovato sopra).

---

## Esercizio 5 — potenze con De Moivre

Dato $z = \dfrac{\sqrt3}{2}-\dfrac{i}{2}$, calcola $z^6$ e $z^{22}$.

**Riconoscimento dell'angolo:** $|z|=\sqrt{\left(\tfrac{\sqrt3}{2}\right)^2+\left(\tfrac12\right)^2}=\sqrt{\tfrac34+\tfrac14}=1$, e $\tfrac{\sqrt3}{2}=\cos\!\left(-\tfrac{\pi}{6}\right)$, $-\tfrac12=\sin\!\left(-\tfrac{\pi}{6}\right)$, quindi

$$z = \cos\!\left(-\tfrac{\pi}{6}\right)+i\sin\!\left(-\tfrac{\pi}{6}\right) = e^{-i\pi/6}$$

**Formula di De Moivre:** $z^n = r^n(\cos(n\theta)+i\sin(n\theta))$, qui $r=1$.

$$z^6 = \cos\!\left(-\tfrac{\pi}{6}\cdot 6\right)+i\sin\!\left(-\tfrac{\pi}{6}\cdot 6\right) = \cos(-\pi)+i\sin(-\pi) = -1$$

Per $z^{22}$ conviene scomporre l'esponente sfruttando $z^6=-1$: $22 = 18+4 = 6\cdot3+4$, quindi

$$z^{22} = (z^6)^3\cdot z^4 = (-1)^3\cdot z^4 = -z^4$$

$$z^4 = \cos\!\left(4\cdot\left(-\tfrac{\pi}{6}\right)\right)+i\sin\!\left(4\cdot\left(-\tfrac{\pi}{6}\right)\right) = \cos\!\left(-\tfrac{2\pi}{3}\right)+i\sin\!\left(-\tfrac{2\pi}{3}\right) = -\tfrac12-i\tfrac{\sqrt3}{2}$$

$$z^{22} = -z^4 = \tfrac12+i\tfrac{\sqrt3}{2} = \cos\tfrac{\pi}{3}+i\sin\tfrac{\pi}{3} = e^{i\pi/3}$$

**Variante (segnata "per casa" in rosso nelle foto):** stesso esercizio con $z=\dfrac{4i}{\sqrt3+i}$.

Razionalizzo: $z = \dfrac{4i(\sqrt3-i)}{(\sqrt3)^2+1^2} = \dfrac{4\sqrt3\,i+4}{4} = 1+\sqrt3\,i$.

$$|z|=\sqrt{1+3}=2,\qquad \arg(z)=\arctan(\sqrt3)=\frac{\pi}{3} \ \Longrightarrow\ z = 2\left(\cos\tfrac{\pi}{3}+i\sin\tfrac{\pi}{3}\right)=2e^{i\pi/3}$$

$$z^6 = 2^6\,e^{i\,6\cdot\pi/3} = 64\,e^{i2\pi} = 64$$

$$z^{22} = 2^{22}\,e^{i\,22\pi/3}$$

Riduco l'angolo modulo $2\pi$: $\dfrac{22\pi}{3} - 6\pi = \dfrac{22\pi-18\pi}{3}=\dfrac{4\pi}{3}$, quindi

$$z^{22} = 2^{22}\left(\cos\tfrac{4\pi}{3}+i\sin\tfrac{4\pi}{3}\right) = 2^{22}\left(-\tfrac12-i\tfrac{\sqrt3}{2}\right) = -2^{21}\left(1+i\sqrt3\right)$$

---

## Esercizio 6 — calcolo del modulo

Calcola $|z|$ per $z = -2i(3+i)(2+4i)(1+i)$.

**Proprietà usata:** $|z_1 z_2\cdots z_n| = |z_1||z_2|\cdots|z_n|$ (il modulo di un prodotto è il prodotto dei moduli — molto più rapido che espandere tutto in forma algebrica).

$$|{-2i}|=2,\quad |3+i|=\sqrt{10},\quad |2+4i|=\sqrt{20}=2\sqrt5,\quad |1+i|=\sqrt2$$

$$|z| = 2\cdot\sqrt{10}\cdot 2\sqrt5\cdot\sqrt2 = 2\cdot(\sqrt2\sqrt5)\cdot(2\sqrt5)\cdot\sqrt2 = 2\cdot2\cdot(\sqrt2\cdot\sqrt2)\cdot(\sqrt5\cdot\sqrt5) = 8\cdot5 = 40$$

**Variante (in rosso):** modulo di $z = \dfrac{(3+4i)(-1+2i)}{(-1-i)(3-i)}$.

Stessa proprietà, estesa al quoziente ($|z_1/z_2|=|z_1|/|z_2|$):

$$|3+4i|=5,\ \ |{-1+2i}|=\sqrt5,\ \ |{-1-i}|=\sqrt2,\ \ |3-i|=\sqrt{10}$$

$$|z| = \frac{5\cdot\sqrt5}{\sqrt2\cdot\sqrt{10}} = \frac{5\sqrt5}{\sqrt{20}} = \frac{5\sqrt5}{2\sqrt5} = \frac52$$

---

## Esercizio 7 — risolvi in forma algebrica

$$z\bar z - z + \frac{i}{4} = 0$$

**Svolgimento.** Pongo $z=a+bi$, quindi $\bar z = a-bi$ e $z\bar z = a^2+b^2$:

$$a^2+b^2-(a+bi)+\frac{i}{4}=0 \ \Longrightarrow\ (a^2+b^2-a) + i\left(\frac14-b\right) = 0$$

Un numero complesso è nullo se e solo se **sono nulle sia la parte reale sia quella immaginaria**:

$$\begin{cases} a^2+b^2-a = 0 \\[2pt] \dfrac14-b=0 \end{cases} \ \Longrightarrow\ b=\frac14,\quad a^2-a+\frac{1}{16}=0$$

Risolvo per $a$ (formula ridotta, $\Delta/4 = \frac14-\frac1{16}=\frac{3}{16}$):

$$a = \frac{1\pm\sqrt{3}/2}{2} = \frac12 \pm \frac{\sqrt3}{4}$$

**Soluzioni:**

$$z_1 = \left(\frac12-\frac{\sqrt3}{4}\right)+\frac14 i, \qquad z_2 = \left(\frac12+\frac{\sqrt3}{4}\right)+\frac14 i$$

**Variante (in rosso, per confronto):** risolvi $z^2+z+1=0$.

Qui è un'equazione **polinomiale** in $z$ (non in $a,b$): uso la formula risolutiva classica, $\Delta = 1-4=-3<0$:

$$z = \frac{-1\pm\sqrt{-3}}{2} = \frac{-1\pm i\sqrt3}{2} = -\frac12 \pm \frac{\sqrt3}{2}i$$

Sono le radici cubiche primitive dell'unità (soluzioni di $z^3=1$ diverse da $1$).

---

## Esercizio 8 — forma algebrica

Esprimi in forma algebrica:

**a)** $z=(2+3i)^2$

$$z = 4 + 12i + 9i^2 = 4+12i-9 = -5+12i$$

**b)** $z=\dfrac{3-i}{3+i}$

Razionalizzo moltiplicando per il coniugato del denominatore:

$$z = \frac{(3-i)^2}{(3+i)(3-i)} = \frac{9-6i+i^2}{9+1} = \frac{8-6i}{10} = \frac45-\frac35 i$$

---

## Collegamenti

- [[Politecnico/Analisi 1/Teoria/Numeri complessi.md|Analisi — Numeri complessi]]
- [[Politecnico/Analisi 1/Teoria/Insieme numerici, logia e dimostrazioni.md|Analisi — Insiemi numerici, logica e dimostrazioni]]
