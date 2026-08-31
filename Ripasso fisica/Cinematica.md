---
tags: [fisica, cinematica, ripasso]
---
# Cinematica

> Formule riassunte in [[Formulario/Cinematica formule.md]]

## Moto Rettilineo Uniforme (MRU)

Velocità **costante**, traiettoria rettilinea. Nessuna accelerazione ($a=0$).

**Legge oraria:**
$$s(t) = s_0 + v\,t$$

- $s_0$ = posizione iniziale
- $v$ = velocità costante (positiva se il moto è nel verso positivo dell'asse, negativa se contrario)

$$v = \frac{\Delta s}{\Delta t} = \text{costante}$$

## Moto Rettilineo Uniformemente Accelerato (MRUA)

Accelerazione **costante** ($a = \text{cost} \neq 0$). La velocità cambia linearmente nel tempo.

**Legge della velocità:**
$$v(t) = v_0 + a\,t$$

**Legge oraria:**
$$s(t) = s_0 + v_0\,t + \tfrac{1}{2}a\,t^2$$

**Equazione utile senza il tempo** (quando non serve $t$):
$$v^2 = v_0^2 + 2a\,\Delta s$$

Se il moto è decelerato, $a$ ha segno opposto a $v_0$.

## Grafici s(t)

- **MRU**: retta. La pendenza (coefficiente angolare) della retta è la velocità $v$. Pendenza costante → velocità costante.
- **MRUA**: parabola. La concavità è verso l'alto se $a>0$, verso il basso se $a<0$. La pendenza della tangente in un punto è la velocità istantanea in quel punto — cresce (in modulo) nel tempo se il moto accelera, tende a zero nel vertice se il moto decelera fino a fermarsi (vertice = punto di velocità nulla, inversione o arresto).

Esempio: MRU con $s_0=5,\ v=3$ (retta) confrontato con MRUA con $s_0=5,\ v_0=2,\ a=1$ (parabola), stesso istante iniziale:

```desmos-graph
left=0; right=6; top=25; bottom=0;
---
y=5+3x\left\{0\le x\le5\right\}|label:MRU
y=5+2x+0.5x^{2}\left\{0\le x\le5\right\}|label:MRUA
```

## Grafici v(t)

- **MRU**: retta orizzontale (v costante).
- **MRUA**: retta obliqua, pendenza = $a$ (costante). Se decelera, la retta è decrescente fino a incrociare l'asse dei tempi (v=0).

**Area sottesa al grafico v-t = spostamento $\Delta s$.**

Esempio: stessi valori di sopra ($v=3$ per il MRU, $v_0=2,\ a=1$ per il MRUA). L'area colorata sotto la retta del MRUA tra $t=1$ e $t=3$ è proprio $\Delta s$ percorso in quell'intervallo:

```desmos-graph
left=0; right=6; top=8; bottom=0;
---
y=3\left\{0\le x\le5\right\}
y=2+x\left\{0\le x\le5\right\}
0\le y\le2+x\left\{1\le x\le3\right\}
(4,3)|label:MRU
(4.5,6.5)|label:MRUA
(2,1.5)|label:\Delta s
```

Questo vale sempre, non solo nel MRU/MRUA: l'area (con segno: sopra l'asse positiva, sotto negativa) tra la curva $v(t)$ e l'asse dei tempi, tra due istanti $t_1$ e $t_2$, è uguale a $\Delta s = s(t_2)-s(t_1)$, perché $v = ds/dt \Rightarrow \Delta s = \int v\,dt$.

- Nel MRU l'area è un **rettangolo**: $\Delta s = v \cdot \Delta t$.
- Nel MRUA l'area è un **trapezio** (o triangolo se parte da $v=0$): $\Delta s = \dfrac{(v_0+v)}{2}\Delta t$, coerente con $s_0+v_0t+\tfrac12 at^2$.

## Moto del proiettile

Moto in due dimensioni ottenuto componendo:
- un **MRU orizzontale** (nessuna forza orizzontale, si trascura l'attrito dell'aria): $v_x = v_{0x} = \text{cost}$
- un **MRUA verticale** con $a=-g$ (caduta libera): $v_y = v_{0y} - g\,t$

Le due componenti sono **indipendenti** e si sommano vettorialmente.

**Caso lancio orizzontale** (velocità iniziale tutta orizzontale, da altezza $h$):
$$x(t) = v_0\,t \qquad y(t) = h - \tfrac{1}{2}g\,t^2$$

Tempo di caduta (quando $y=0$): $t_c = \sqrt{\dfrac{2h}{g}}$

Gittata: $x_{max} = v_0\, t_c$

Traiettoria: parabola.

Esempio: lancio orizzontale da $h=20$ m con $v_0=15$ m/s (traiettoria $y(x) = h - \frac{g}{2v_0^2}x^2$):

```desmos-graph
left=0; right=32; top=22; bottom=0;
---
y=20-\frac{9.8}{2\cdot15^{2}}x^{2}\left\{0\le x\le30.3\right\}
(0,20)|label:sgancio
(30.3,0)|label:atterraggio
```

## Moto circolare uniforme (MCU)

Moto su una circonferenza con **modulo della velocità costante** (la direzione cambia continuamente, quindi c'è comunque accelerazione).

- Velocità angolare: $\omega = \dfrac{\Delta\theta}{\Delta t} = \text{cost}$ [rad/s]
- Periodo $T$ = tempo per un giro completo: $T = \dfrac{2\pi}{\omega}$ [s]
- Frequenza $f = \dfrac{1}{T}$ [Hz] = numero di giri al secondo, $\omega = 2\pi f$
- Velocità tangenziale (lineare): $v = \omega r$, sempre tangente alla traiettoria
- **Accelerazione centripeta** (dovuta al cambio di direzione, non di modulo), diretta verso il centro:
$$a_c = \frac{v^2}{r} = \omega^2 r$$

Legge oraria angolare: $\theta(t) = \theta_0 + \omega t$ (analoga a MRU ma con angoli).

Esempio: traiettoria circolare di raggio $r=3$, punto $P$ a $\theta=0{,}7$ rad con il vettore velocità (tangente, perpendicolare al raggio):

```desmos-graph
left=-4; right=4; top=4; bottom=-4;
---
x^{2}+y^{2}=9
(0,0)|label:O
(3\cos(0.7),3\sin(0.7))|label:P
(3\cos(0.7)-1.5\sin(0.7)t,3\sin(0.7)+1.5\cos(0.7)t)\left\{0\le t\le1\right\}
```

## Piano inclinato

Corpo su un piano inclinato di angolo $\alpha$ rispetto all'orizzontale. La forza peso $mg$ si scompone in due componenti (assi paralleli e perpendicolari al piano):

- Componente **parallela al piano** (fa scivolare il corpo lungo il piano): $F_{\parallel} = mg\sin\alpha$
- Componente **perpendicolare al piano** (schiaccia il corpo contro il piano, bilanciata dalla reazione normale $N$): $F_{\perp} = mg\cos\alpha = N$ (in assenza di altre forze verticali)

Se si trascura l'attrito, l'accelerazione lungo il piano è:
$$a = g\sin\alpha$$

(indipendente dalla massa). Con attrito (coefficiente dinamico $\mu_d$), scendendo:
$$a = g(\sin\alpha - \mu_d\cos\alpha)$$

Esempio geometrico con $\alpha=30°$ (piano lungo $d=5$): scomposizione del peso $mg$ nella componente parallela $mg\sin\alpha$ e perpendicolare $mg\cos\alpha$:

```desmos-graph
left=-1; right=6; top=4; bottom=-1;
---
y=0\left\{0\le x\le4.33\right\}
y=0.577x\left\{0\le x\le4.33\right\}
(2.6,1.5-2t)\left\{0\le t\le1\right\}
(2.6-0.866t,1.5-0.5t)\left\{0\le t\le1\right\}
(2.6+0.866t,1.5-1.5t)\left\{0\le t\le1\right\}
(2.6,1.5)|label:blocco
(2.6,-0.5)|label:mg
(1.73,1.0)|label:mg\sin\alpha
(3.47,0)|label:mg\cos\alpha
```

---

# Esercizi

## Esercizio 1 — Incrocio treni

Treno 3580: passa davanti alla stazione di Monza a velocità costante $v_1 = 72\text{ km/h} = 20\text{ m/s}$ (istante $t=0$, posizione $x=0$ = stazione).
Treno 4580: viaggia in direzione opposta, a $t=0$ si trova a $d=100\text{ m}$ dalla stazione e rallenta con $a=1{,}2\text{ m/s}^2$ per fermarsi in stazione.

**a) Velocità del treno 4580 a 100 m dalla stazione**

Usando $v^2 = v_0^2 - 2a\,d$ con $v=0$ (si ferma in stazione):
$$v_0 = \sqrt{2ad} = \sqrt{2\cdot 1{,}2 \cdot 100} = \sqrt{240} \approx 15{,}5\text{ m/s} \;(\approx 55{,}8\text{ km/h})$$

**b) Distanza e istante dell'incrocio**

Assi: stazione = origine, treno 3580 si muove in verso positivo ($x_1(t)=20t$), treno 4580 parte da $x=100$ m muovendosi verso la stazione decelerando:
$$x_2(t) = 100 - 15{,}5\,t + 0{,}6\,t^2$$

Incrocio quando $x_1(t)=x_2(t)$:
$$20t = 100 - 15{,}5t + 0{,}6t^2 \;\Rightarrow\; 0{,}6t^2 - 35{,}5t + 100 = 0$$

Risolvendo (radice accettabile, l'altra cade dopo che il treno 4580 si è già fermato):
$$t \approx 2{,}97\text{ s}, \qquad x \approx 20\cdot 2{,}97 \approx 59{,}3\text{ m dalla stazione}$$

**c) Grafici qualitativi**

- $s(t)$: treno 3580 → retta con pendenza costante $+20$ m/s. Treno 4580 → parabola decrescente (concava verso l'alto) che parte da 100 m e arriva a 0 con tangente orizzontale a $t\approx 12{,}9$ s (istante di arresto, $t=v_0/a$). Le due curve si incrociano a $t\approx 2{,}97$ s, $s\approx 59{,}3$ m.
- $v(t)$: treno 3580 → retta orizzontale a $+20$ m/s. Treno 4580 → retta decrescente in modulo (accelerazione negativa) che parte da $-15{,}5$ m/s e arriva a 0 in $t\approx 12{,}9$ s.

Grafico $s(t)$ con i valori numerici (il punto di incrocio è evidenziato):

```desmos-graph
left=0; right=14; top=105; bottom=0;
---
y=20x\left\{0\le x\le14\right\}
y=100-15.49x+0.6x^{2}\left\{0\le x\le12.9\right\}
(2.97,59.3)|label:incrocio
```

Grafico $v(t)$ (treno 4580: velocità negativa perché va verso la stazione, cresce linearmente fino a 0):

```desmos-graph
left=0; right=14; top=25; bottom=-20;
---
y=20\left\{0\le x\le14\right\}
y=-15.49+1.2x\left\{0\le x\le12.9\right\}
```

## Esercizio 2 — Legge oraria $x(t)=k_1t+k_2t^3$

Dati: $k_1=-6$, $k_2=2$.

**a) Unità di misura**

Perché $x$ sia in metri: $[k_1]=$ m/s, $[k_2]=$ m/s³.

**b) $v(2\text{s})$, $a(2\text{s})$ e velocità scalare media tra 0 e 2 s**

$$v(t) = k_1 + 3k_2t^2 = -6+6t^2 \;\Rightarrow\; v(2) = -6+24 = 18\text{ m/s}$$
$$a(t) = 6k_2 t = 12t \;\Rightarrow\; a(2) = 24\text{ m/s}^2$$

Velocità scalare media = distanza totale percorsa / tempo. Attenzione: $v(t)=0$ per $t=1$ s (inversione del moto), quindi bisogna sommare i tratti:
- $x(0)=0$, $x(1)=-6+2=-4$ m, $x(2)=-12+16=4$ m
- distanza 0→1 s: $|{-4}-0|=4$ m; distanza 1→2 s: $|4-(-4)|=8$ m; totale $=12$ m

$$v_{scalare\,media} = \frac{12\text{ m}}{2\text{ s}} = 6\text{ m/s}$$

(diversa dalla velocità media vettoriale $\Delta x/\Delta t = 4/2 = 2$ m/s)

**c) Accelerazione quando $v=0$**

$v=0 \Rightarrow -6+6t^2=0 \Rightarrow t=1$ s $\Rightarrow a(1) = 12$ m/s².

## Esercizio 3 — Lancio pacco viveri

Quota $h=35$ m, distanza orizzontale da coprire $d=100$ m, attrito trascurato.

**a) Velocità $v_0$ dell'aereo**

Tempo di caduta: $t=\sqrt{2h/g}=\sqrt{70/9{,}8}\approx 2{,}67$ s

$$v_0 = \frac{d}{t} = \frac{100}{2{,}67} \approx 37{,}4\text{ m/s}$$

**b) Velocità finale del pacco**

- Componente orizzontale (invariata): $v_x = 37{,}4$ m/s
- Componente verticale: $v_y = g\,t = 9{,}8\cdot 2{,}67 \approx 26{,}2$ m/s

$$v_{fin} = \sqrt{v_x^2+v_y^2} = \sqrt{37{,}4^2+26{,}2^2} \approx 45{,}7\text{ m/s}$$

Traiettoria del pacco:

```desmos-graph
left=0; right=105; top=38; bottom=0;
---
y=35-0.0035x^{2}\left\{0\le x\le100\right\}
(0,35)|label:sgancio
(100,0)|label:villaggio
```

## Esercizio 4 — Sorpasso auto

$v_A = 70\text{ km/h} = 19{,}44$ m/s, $v_B = 90\text{ km/h}=25$ m/s (costante), distanza iniziale $d=60$ m (A dietro B), A accelera con $a_A=1{,}5\text{ m/s}^2$.

Posizioni: $x_A(t)=19{,}44t+0{,}75t^2$, $x_B(t)=60+25t$

**a) Istante del sorpasso** ($x_A=x_B$):
$$0{,}75t^2 - 5{,}56t - 60 = 0 \;\Rightarrow\; t \approx 13{,}4\text{ s}$$

**b) Velocità di A al sorpasso**
$$v_A(t) = 19{,}44 + 1{,}5\cdot 13{,}4 \approx 39{,}5\text{ m/s} \;(\approx 142\text{ km/h})$$

## Esercizio 5 — Bisettrice del triangolo (geometria)

Formula data per la bisettrice dell'angolo opposto al lato $a$:
$$l_a = \frac{2}{b+c}\sqrt{bc\,p\,(p-a)}$$

con $p$ semiperimetro. È la formula classica della lunghezza della bisettrice (si ricava dal teorema di Stewart), ed è **valida** ogni volta che $a,b,c$ formano un triangolo, cioè se valgono le disuguaglianze triangolari. In particolare serve $p-a>0$, cioè $b+c>a$, perché altrimenti l'argomento della radice sarebbe negativo: questa condizione è automaticamente garantita dalla disuguaglianza triangolare, quindi la formula è sempre corretta per un triangolo reale.

## Esercizio 6 — Lancette dell'orologio

**a) Periodo, frequenza, velocità angolare**

- Lancetta dei minuti: $T=3600$ s, $f=1/3600\approx 2{,}78\times10^{-4}$ Hz, $\omega = 2\pi/3600 \approx 1{,}745\times10^{-3}$ rad/s
- Lancetta delle ore: $T=43200$ s (12 h), $f\approx 2{,}31\times10^{-5}$ Hz, $\omega \approx 1{,}454\times10^{-4}$ rad/s

**b) Sovrapposizione dopo le ore 3**

Alle 3:00 la lancetta delle ore è a $90°$, quella dei minuti a $0°$. Velocità angolari: minuti $6°/$min, ore $0{,}5°/$min → velocità relativa $5{,}5°/$min.

$$t = \frac{90°}{5{,}5°/\text{min}} \approx 16{,}36\text{ min} \approx 16\text{ min } 22\text{ s}$$

Le lancette si sovrappongono alle **3:16:22** circa.
