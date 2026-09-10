---
date: 2026-09-07
subject: matematica
topic: trigonometria
tags:
  - matematica
  - trigonometria
  - identita-trigonometriche
  - equazioni-trigonometriche
---
# Lezione 5: Trigonometria — Warm-up

Corso di ripasso Matematica, laboratorio FDS (MOOC MAT101 Polimi).

## A) Altezze vertiginose

Dati: distanza dalla montagna $d = 5{,}2\text{ km}$, angolo di elevazione $\theta = 30°$.

Il triangolo formato da osservatore, base della montagna e cima è rettangolo (assumendo terreno piatto e trascurando l'altezza degli occhi), quindi:
$$
\tan\theta = \frac{\text{altezza}}{d} \;\Longrightarrow\; \text{altezza} = d\cdot\tan\theta
$$
$$
\text{altezza} = 5200 \cdot \tan(30°) = 5200 \cdot \frac{1}{\sqrt3} \approx 5200 \cdot 0{,}5774 \approx 3002\text{ m}
$$

**La montagna è alta circa 3000 m: Alice aveva ragione!**

## B) Pratica

### Riscrivere come combinazione di $\cos\alpha, \sin\alpha$

Formule di riduzione usate: $\cos(\pi-\alpha)=-\cos\alpha$, $\sin(\pi/2+\alpha)=\cos\alpha$, $\cos(\alpha-\pi/2)=\sin\alpha$, $\sin(\pi+\alpha)=-\sin\alpha$, e la formula di addizione $\cos(a\pm b), \sin(a\pm b)$.

**1.** $\cos(\pi-\alpha) + \sin\left(\dfrac{\pi}{2}+\alpha\right) - 2\sin\left(\dfrac{\pi}{3}+\alpha\right)$

$$
\cos(\pi-\alpha) = -\cos\alpha, \qquad \sin\left(\frac\pi2+\alpha\right)=\cos\alpha
$$
$$
\sin\left(\frac\pi3+\alpha\right) = \sin\frac\pi3\cos\alpha+\cos\frac\pi3\sin\alpha = \frac{\sqrt3}{2}\cos\alpha+\frac12\sin\alpha
$$
Sommando:
$$
-\cos\alpha+\cos\alpha - 2\left(\frac{\sqrt3}{2}\cos\alpha+\frac12\sin\alpha\right) = -\sqrt3\cos\alpha - \sin\alpha
$$

**2.** $\sin\alpha + \cos\left(\alpha-\dfrac{\pi}{2}\right) + \sin(\pi+\alpha) + 3\cos\left(\dfrac{\pi}{4}-\alpha\right)$

$$
\cos\left(\alpha-\frac\pi2\right)=\sin\alpha, \qquad \sin(\pi+\alpha)=-\sin\alpha
$$
$$
\cos\left(\frac\pi4-\alpha\right)=\cos\frac\pi4\cos\alpha+\sin\frac\pi4\sin\alpha=\frac{\sqrt2}{2}(\cos\alpha+\sin\alpha)
$$
Sommando:
$$
\sin\alpha+\sin\alpha-\sin\alpha+3\cdot\frac{\sqrt2}{2}(\cos\alpha+\sin\alpha) = \left(1+\frac{3\sqrt2}{2}\right)\sin\alpha + \frac{3\sqrt2}{2}\cos\alpha
$$

> ponytail: il testo originale è arrivato via OCR con le frazioni spezzate su più righe; ho ricostruito gli angoli più plausibili ($\pi/2,\pi/3,\pi/4$). Il procedimento (formule di riduzione + addizione, poi raccogliere $\cos\alpha$ e $\sin\alpha$) resta lo stesso qualunque sia l'angolo esatto.

### Verificare le identità

**1.** $\dfrac{\sin^3x+\cos^3x}{1-\sin x\cos x} = \sin x+\cos x$

Fattorizzo la somma di cubi ($a^3+b^3=(a+b)(a^2-ab+b^2)$):
$$
\sin^3x+\cos^3x = (\sin x+\cos x)(\sin^2x-\sin x\cos x+\cos^2x) = (\sin x+\cos x)(1-\sin x\cos x)
$$
(uso $\sin^2x+\cos^2x=1$). Dividendo per $(1-\sin x\cos x)$ (non nullo) resta $\sin x+\cos x$. ✓

**2.** $\sin(2\alpha)\cos\alpha + 2\sin^3\alpha = 2\sin\alpha$

$$
\sin(2\alpha)=2\sin\alpha\cos\alpha \;\Rightarrow\; \text{LHS} = 2\sin\alpha\cos^2\alpha + 2\sin^3\alpha = 2\sin\alpha(\cos^2\alpha+\sin^2\alpha) = 2\sin\alpha
$$ ✓

**3.** $\dfrac{1}{2-\sin^2x} = \dfrac{1+\tan^2x}{2+\tan^2x}$

Uso $\sin^2x=1-\cos^2x$ nel primo membro:
$$
\frac{1}{2-\sin^2x} = \frac{1}{2-(1-\cos^2x)} = \frac{1}{1+\cos^2x}
$$
Nel secondo membro, $1+\tan^2x = \dfrac{1}{\cos^2x}$ e $2+\tan^2x = \dfrac{2\cos^2x+\sin^2x}{\cos^2x} = \dfrac{\cos^2x+1}{\cos^2x}$ (perché $2\cos^2x+\sin^2x=\cos^2x+(\cos^2x+\sin^2x)=\cos^2x+1$):
$$
\frac{1+\tan^2x}{2+\tan^2x} = \frac{1/\cos^2x}{(1+\cos^2x)/\cos^2x} = \frac{1}{1+\cos^2x}
$$
I due membri coincidono. ✓

### Equazioni e disequazioni trigonometriche

**1.** $\sin x=\dfrac12$
$$
x = \frac\pi6+2k\pi \quad\lor\quad x=\pi-\frac\pi6=\frac{5\pi}{6}+2k\pi,\quad k\in\mathbb Z
$$

**2.** $\cos x=-\dfrac{\sqrt2}{2}$
$$
x = \frac{3\pi}{4}+2k\pi \quad\lor\quad x=-\frac{3\pi}{4}+2k\pi,\quad k\in\mathbb Z
$$

**3.** $\sin x\le 1$

Il seno vale al massimo 1, quindi la disuguaglianza è **sempre vera**:
$$
x\in\mathbb R
$$

**4.** $\cos(2x)\ge 1$

Il coseno vale al massimo 1, quindi serve l'uguaglianza $\cos(2x)=1$:
$$
2x = 2k\pi \;\Rightarrow\; x = k\pi,\quad k\in\mathbb Z
$$
