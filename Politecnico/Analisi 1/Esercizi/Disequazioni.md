---
tags:
  - analisi1
  - disequazioni
  - disequazioni-irrazionali
  - disequazioni-logaritmiche
  - disequazioni-goniometriche
  - dominio-funzioni
---

# Disequazioni — Analisi 1

## 1) $x+1>\sqrt{-x^2-2x}$

**Condizione di esistenza** (radicando $\ge 0$):
$$-x^2-2x\ge 0 \;\Longrightarrow\; x^2+2x\le 0 \;\Longrightarrow\; -2\le x\le 0$$

Poiché il radicale è sempre $\ge 0$, se $x+1<0$ la disuguaglianza è impossibile. Serve quindi anche $x+1\ge 0 \Rightarrow x\ge -1$.

Con $x\ge -1$ si può elevare al quadrato:
$$(x+1)^2 > -x^2-2x \;\Longrightarrow\; x^2+2x+1+x^2+2x>0 \;\Longrightarrow\; 2x^2+4x+1>0$$

Radici: $x=\dfrac{-4\pm\sqrt{16-8}}{4}=\dfrac{-2\pm\sqrt{2}}{2}$
$$x_1=\frac{-2-\sqrt2}{2},\qquad x_2=\frac{-2+\sqrt2}{2}$$

La parabola è $>0$ per $x<x_1$ oppure $x>x_2$. Intersecando con $-1\le x\le 0$ (CE $\cap\; x\ge-1$):

$$\boxed{S=\left(\frac{-2+\sqrt2}{2}\,,\;0\right]}$$

---

## 2) $\dfrac{\log_{1/2}(x^2-1)}{2^x-\frac{1}{2\sqrt2}}>0$

**CE:** $x^2-1>0 \Rightarrow x<-1 \;\lor\; x>1$

Una frazione è positiva quando numeratore e denominatore hanno **lo stesso segno**.

**Numeratore** (base $\tfrac12<1$, quindi $\log$ decrescente): $\log_{1/2}(u)>0 \iff 0<u<1$.
$$x^2-1<1 \Longrightarrow x^2<2 \Longrightarrow -\sqrt2<x<\sqrt2$$
Intersecato con la CE: numeratore $>0$ su $(-\sqrt2,-1)\cup(1,\sqrt2)$; numeratore $<0$ su $x<-\sqrt2 \;\lor\; x>\sqrt2$.

**Denominatore:** $\dfrac{1}{2\sqrt2}=2^{-3/2}$, quindi
$$2^x>2^{-3/2}\Longrightarrow x>-\frac32$$
denominatore $>0$ per $x>-\frac32$, $<0$ per $x<-\frac32$.

**Stesso segno (entrambi positivi):** $(-\sqrt2,-1)\cup(1,\sqrt2)$, già dentro $x>-3/2$.

**Stesso segno (entrambi negativi):** numeratore $<0$ ($x<-\sqrt2\;\lor\;x>\sqrt2$) $\cap$ denominatore $<0$ ($x<-3/2$) $= x<-\dfrac32$ (perché $-\tfrac32<-\sqrt2$).

$$\boxed{S=\left\{x<-\frac32\right\}\cup(-\sqrt2,-1)\cup(1,\sqrt2)}$$

---

## 3) $2\cos^2(x)+5\sin(x)-3>2\sin(x)$

Sostituzione $\cos^2x=1-\sin^2x$:
$$2(1-\sin^2x)+5\sin x-3>2\sin x \;\Longrightarrow\; 2-2\sin^2x+5\sin x-3>2\sin x$$

Con $t=\sin x$:
$$-2t^2+3t-1>0 \;\Longrightarrow\; 2t^2-3t+1<0$$

Radici: $t=\dfrac{3\pm1}{4}\Rightarrow t_1=\dfrac12,\; t_2=1$, quindi $2t^2-3t+1<0$ per
$$\frac12<t<1 \;\Longrightarrow\; \frac12<\sin x<1$$

- $\sin x=\tfrac12 \Rightarrow x=\tfrac{\pi}{6}+2k\pi \;\lor\; x=\tfrac{5\pi}{6}+2k\pi$
- $\sin x=1 \Rightarrow x=\tfrac{\pi}{2}+2k\pi$ (va **escluso**, disuguaglianza stretta)

$$\boxed{\frac{\pi}{6}+2k\pi < x < \frac{5\pi}{6}+2k\pi,\quad x\neq\frac{\pi}{2}+2k\pi,\quad k\in\mathbb Z}$$

---

## 4) $\sqrt{\log^2(x)-3\log(x)+2} > 2(\log(x)-1)$

**CE:** $x>0$ e $\log^2x-3\log x+2\ge 0 \iff (\log x-1)(\log x-2)\ge0 \iff \log x\le1 \;\lor\;\log x\ge2$

Sostituzione $t=\log x$: $\sqrt{t^2-3t+2}>2(t-1)$.

**Caso A — $2(t-1)<0$, cioè $t<1$:** il radicale (sempre $\ge0$) è automaticamente maggiore di un numero negativo. Tutto l'intervallo $t<1$ è compatibile con la CE ($t\le1$) → **soluzione valida**.

**Caso B — $2(t-1)\ge0$, cioè $t\ge1$:** si può elevare al quadrato:
$$t^2-3t+2 > 4(t-1)^2 = 4t^2-8t+4 \;\Longrightarrow\; 3t^2-5t+2<0$$
Radici $t=\dfrac{5\pm1}{6}\Rightarrow t=\dfrac23,\,1$, quindi $3t^2-5t+2<0$ per $\dfrac23<t<1$.
Intersecato con $t\ge1$: **insieme vuoto**.

Quindi l'unica soluzione è quella del Caso A:
$$\log x<1 \Longrightarrow 0<x<e$$

$$\boxed{S=(0,\,e)}$$

---

## 5) $\log_2\!\big(\arctan(x)+4\big) \ge \cos^2(x)$

**CE:** $\arctan(x)+4>0$ sempre vera $\forall x\in\mathbb R$ (poiché $\arctan x\in(-\tfrac\pi2,\tfrac\pi2)$, quindi $\arctan x+4 > 4-\tfrac\pi2>0$).

Per ogni $x$: $\arctan x + 4 > 4-\dfrac{\pi}{2}>2$, quindi
$$\log_2(\arctan x+4) > \log_2 2 = 1 \ge \cos^2 x$$
(l'ultima disuguaglianza vale perché $\cos^2x\le1$ sempre).

Dunque la disuguaglianza è **sempre verificata**:
$$\boxed{S=\mathbb R}$$

---

## 6) Dominio di $f(x)=\dfrac{\big[\log(\sqrt{x}+\sqrt{|1-x|})\big]^{5/2}}{e^{\sin(x^5)}}$

**Condizioni:**
1. $\sqrt x$ richiede $x\ge0$.
2. Il denominatore $e^{\sin(x^5)}$ è sempre $>0$ per ogni $x\in\mathbb R$ ⇒ nessuna restrizione.
3. L'esponente $5/2$ (radice quadrata) richiede la base non negativa: $\log(\sqrt x+\sqrt{|1-x|})\ge0 \iff \sqrt x+\sqrt{|1-x|}\ge1$.

**Verifica per $0\le x\le 1$** (qui $|1-x|=1-x$): elevando al quadrato (lecito, entrambi i membri $\ge0$)
$$\big(\sqrt x+\sqrt{1-x}\big)^2 = 1+2\sqrt{x(1-x)} \ge 1 \quad\text{sempre vero}$$
→ **tutto** l'intervallo $[0,1]$ è accettabile.

**Verifica per $x>1$** (qui $|1-x|=x-1$): $\sqrt x>1$ già da solo, quindi $\sqrt x+\sqrt{x-1}>1$ sempre vero
→ **tutto** l'intervallo $(1,+\infty)$ è accettabile.

Unendo i due casi con la condizione 1 ($x\ge0$):

$$\boxed{D=[0,+\infty)}$$
*
