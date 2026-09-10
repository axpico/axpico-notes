---
tags: [fisica, elettromagnetismo, ripasso]
---
# Elettromagnetismo — Campo magnetico

## 1. Campo magnetico $\vec B$

Il campo magnetico è generato da cariche in movimento (correnti) e agisce su altre cariche in movimento. A differenza del campo elettrico:
- non esistono monopoli magnetici → le linee di campo sono sempre **chiuse**
- il flusso di $\vec B$ attraverso qualunque superficie chiusa è nullo: $\oint \vec B \cdot d\vec A = 0$
- si misura in **tesla** (T), $1\,T = 1\,\dfrac{Wb}{m^2} = 1\,\dfrac{kg}{A\,s^2}$

## 2. Legge di Biot-Savart

Dà il campo generato da un elemento di filo percorso da corrente $I$:

$$d\vec B = \frac{\mu_0}{4\pi}\frac{I\,d\vec l \times \hat r}{r^2}$$

dove $\mu_0 = 4\pi\times10^{-7}\ T\,m/A$ è la permeabilità magnetica del vuoto, $d\vec l$ l'elemento di filo nella direzione della corrente, $\hat r$ il versore dal filo al punto campo, $r$ la distanza.

**Caso filo rettilineo indefinito** (integrando Biot-Savart su tutto il filo), a distanza $r$:

$$B(r) = \frac{\mu_0 I}{2\pi r}$$

Le linee di campo sono circonferenze concentriche al filo, verso dato dalla regola della mano destra.

```desmos-graph
left=0.1; right=5;
top=0.00001; bottom=0;
---
y=\frac{2\times10^{-7}\cdot 5}{x}
```
*(esempio: $I=5\,A$, $B(r)$ in tesla in funzione di $r$ in metri — nota il decadimento $1/r$)*

## 3. Teorema di Ampère e corrente concatenata

Se il filo **non è rettilineo** (o comunque per geometrie con simmetria), conviene usare il teorema di Ampère invece di integrare Biot-Savart punto per punto:

$$\oint_\gamma \vec B \cdot d\vec l = \mu_0 I_{conc}$$

**Corrente concatenata $I_{conc}$**: è la somma algebrica delle correnti che attraversano una qualsiasi superficie che ha come bordo il percorso chiuso $\gamma$ (curva amperiana). "Concatenata" perché il filo si "aggancia" al cappio chiuso: ogni corrente che buca la superficie conta (con segno dato dalla regola della mano destra rispetto al verso di percorrenza di $\gamma$), quelle che non la attraversano no.

Verifica con il filo rettilineo: scegliendo come amperiana una circonferenza di raggio $r$ centrata sul filo, per simmetria $B$ è costante e tangente alla curva:

$$B\cdot 2\pi r = \mu_0 I \ \Rightarrow\ B = \frac{\mu_0 I}{2\pi r}$$

— stesso risultato di Biot-Savart, ma molto più rapido quando c'è simmetria (solenoide, toroide, filo rettilineo).

## 4. Forza di Lorentz

Forza su una carica $q$ che si muove con velocità $\vec v$ in presenza di campo elettrico e magnetico:

$$\vec F = q\vec E + q\vec v \times \vec B$$

La sola componente magnetica:

$$\vec F_B = q\vec v \times \vec B$$

- modulo: $F = qvB\sin\theta$ ($\theta$ angolo tra $\vec v$ e $\vec B$)
- direzione: perpendicolare sia a $\vec v$ che a $\vec B$ (regola della mano destra, invertita se $q<0$)
- **non compie mai lavoro** sulla carica, perché è sempre perpendicolare a $\vec v$ → cambia la direzione del moto ma non il modulo della velocità (né l'energia cinetica).

## 5. Moto di una carica in campo magnetico uniforme

Se $\vec v \perp \vec B$: la forza di Lorentz è centripeta costante in modulo → **moto circolare uniforme**.

Uguagliando forza magnetica e forza centripeta:

$$qvB = \frac{mv^2}{r} \ \Rightarrow\ r = \frac{mv}{qB} \quad (\text{raggio di ciclotrone})$$

$$T = \frac{2\pi r}{v} = \frac{2\pi m}{qB} \quad (\text{periodo, indipendente da } v!)$$

Se $\vec v$ ha anche una componente parallela a $\vec B$, quella componente non risente di forza (perché $\vec v_\parallel \times \vec B = 0$) → si somma un moto rettilineo uniforme lungo $\vec B$: il risultato è un **moto elicoidale**.

```desmos-graph
left=-3; right=3;
top=3; bottom=-3;
width=400; height=400;
---
x=2\cos(t)
y=2\sin(t)
```
*(traiettoria circolare della carica vista nel piano perpendicolare a $\vec B$, $t$ da 0 a $2\pi$)*

## 6. Forza di Laplace (forza su un filo percorso da corrente)

È la forza di Lorentz applicata a tutte le cariche in moto ordinato in un filo, sommata su un tratto di filo di lunghezza $\vec l$ (vettore nel verso della corrente) immerso in campo $\vec B$ uniforme:

$$\vec F = I\,\vec l \times \vec B$$

- modulo: $F = BIl\sin\theta$
- massima quando filo e campo sono perpendicolari, nulla se paralleli
- per un elemento infinitesimo: $d\vec F = I\,d\vec l \times \vec B$ (utile per contorni non rettilinei)

## 7. Spira percorsa da corrente in un campo magnetico

Una spira piana di area $A$, percorsa da corrente $I$, ha **momento di dipolo magnetico**:

$$\vec m = I A\,\hat n$$

($\hat n$ normale alla spira, verso dato dalla regola della mano destra rispetto al verso di percorrenza della corrente).

Immersa in campo uniforme $\vec B$:
- **forza risultante nulla** (le forze di Laplace sui lati opposti si cancellano)
- ma **momento torcente non nullo**, che tende ad allineare $\vec m$ con $\vec B$:

$$\vec \tau = \vec m \times \vec B \qquad \tau = mB\sin\theta = IAB\sin\theta$$

- energia potenziale di orientamento: $U = -\vec m \cdot \vec B$, minima (equilibrio stabile) quando $\vec m \parallel \vec B$.

Questo è il principio di funzionamento di motori elettrici e strumenti a bobina mobile (galvanometri).

```desmos-graph
left=0; right=6.3; top=1.2; bottom=-1.2;
---
y=\sin(x)|label:\tau=mB\sin(\theta)
```
*(andamento del momento torcente $\tau$ sulla spira in funzione dell'angolo $\theta$ tra $\vec m$ e $\vec B$: massimo a $90°$, nullo a $0°$ e $180°$)*

---

# Esercizi VIII incontro

## 1. Periodo indipendente dalla velocità

Per una carica $q$ che si muove con $\vec v \perp \vec B$, la [[Forza di Lorentz]] $qvB$ è centripeta:

$$qvB=\frac{mv^2}{r}\ \Rightarrow\ r=\frac{mv}{qB}$$

Il periodo è:

$$T=\frac{2\pi r}{v}=\frac{2\pi}{v}\cdot\frac{mv}{qB}=\frac{2\pi m}{qB}$$

La $v$ si semplifica: $T$ dipende solo da $m$, $q$, $B$ (costanti per elettroni in uno stesso campo), **non da $v$**. Quindi tutti gli elettroni, qualunque sia la loro velocità, completano un giro nello stesso tempo (velocità maggiore → raggio maggiore, ma proporzionalmente, così il periodo resta uguale). $\blacksquare$

## 2. Carica vicino a un filo percorso da corrente

Dati: $i=500\,mA=0.5\,A$, $r=0.5\,m$, $v=10\,m/s$, $F=14\times10^{-12}\,N$.

**a) Campo B:**

$$B=\frac{\mu_0 i}{2\pi r}=\frac{4\pi\times10^{-7}\cdot 0.5}{2\pi\cdot 0.5}=2\times10^{-7}\,T$$

Direzione: $\vec B$ circonda il filo (circonferenze concentriche), quindi è sempre **perpendicolare al filo**. Poiché la carica si muove parallelamente al filo, $\vec v \parallel$ filo e $\vec B \perp$ filo $\Rightarrow \theta = 90°$ tra $\vec v$ e $\vec B$. Verso dato dalla regola della mano destra rispetto al verso di $i$.

**b) Carica:**

$$F=qvB\sin\theta = qvB \ (\theta=90°)$$
$$q=\frac{F}{vB}=\frac{14\times10^{-12}}{10\cdot 2\times10^{-7}}=7\times10^{-6}\,C = 7\,\mu C$$

Direzione forza: $\vec F=q\vec v\times\vec B$ è radiale (perpendicolare sia a $\vec v$ che a $\vec B$); per carica positiva che si muove nello stesso verso della corrente il comportamento è come tra due correnti parallele equiverse → **forza attrattiva verso il filo**.

## 3. Spettrometro di massa — isotopi di uranio

$v=1.05\times10^5\,m/s$, $B=0.750\,T$, $q=e=1.6\times10^{-19}\,C$ (ionizzazione singola).

$$r=\frac{mv}{qB}$$

$$r_{235}=\frac{3.90\times10^{-25}\cdot1.05\times10^5}{1.6\times10^{-19}\cdot0.750}=0.341\,m$$
$$r_{238}=\frac{3.95\times10^{-25}\cdot1.05\times10^5}{1.6\times10^{-19}\cdot0.750}=0.346\,m$$

Dopo mezza orbita ciascuno ha percorso un semicerchio: la separazione tra i due punti di arrivo è la differenza dei **diametri**:

$$d=2(r_{238}-r_{235})=2(0.346-0.341)\approx 8.8\times10^{-3}\,m \approx 8.8\,mm$$

## 4. Solenoide

$d=12\,cm \Rightarrow$ circonferenza $=\pi d = 0.377\,m$; $L=0.55\,m$; $I=4\,A$; $B=25\,G=2.5\times10^{-3}\,T$.

Spire per unità di lunghezza:

$$B=\mu_0 n I \ \Rightarrow\ n=\frac{B}{\mu_0 I}=\frac{2.5\times10^{-3}}{4\pi\times10^{-7}\cdot4}\approx 497\,\text{spire/m}$$

Numero totale di spire:

$$N=n\cdot L \approx 497\cdot0.55\approx 274\,\text{spire}$$

Lunghezza totale di filo (ogni spira è una circonferenza di diametro 12 cm):

$$\ell = N\cdot\pi d \approx 274\cdot0.377\approx 103\,m$$

## 5. Due fili paralleli che si respingono

$d=5\,cm=0.05\,m$, $I_2=3I_1$, $F/L = 2\times10^{-6}\,N/cm = 2\times10^{-4}\,N/m$. (Repulsione ⇒ correnti in versi opposti.)

**a) Correnti:**

$$\frac{F}{L}=\frac{\mu_0}{2\pi}\frac{I_1 I_2}{d}=2\times10^{-7}\cdot\frac{3I_1^2}{d}$$

$$2\times10^{-4}=2\times10^{-7}\cdot\frac{3I_1^2}{0.05}\ \Rightarrow\ I_1^2=\frac{2\times10^{-4}\cdot0.05}{6\times10^{-7}}\approx16.7$$

$$I_1\approx4.08\,A \qquad I_2=3I_1\approx12.2\,A$$

**b) e c) Terzo filo senza forza:** sì, è possibile: va posto dove il campo magnetico risultante dei primi due fili è nullo. Poiché le correnti sono antiparallele, questo punto **non è tra i due fili** (lì i campi si sommano) ma **esternamente, dalla parte del filo con corrente minore** ($I_1$). Imponendo $B_1=B_2$:

$$\frac{I_1}{x}=\frac{I_2}{x+d}\ \Rightarrow\ x=\frac{I_1 d}{I_2-I_1}=\frac{I_1 d}{2I_1}=\frac{d}{2}=2.5\,cm$$

Il terzo filo va posto a $2.5\,cm$ dal filo con corrente $I_1$, dalla parte opposta rispetto a $I_2$ (quindi a $7.5\,cm$ dal filo con $I_2$). In quel punto qualunque $I_3$ non risente di forza netta.

## 6. Campo nel vertice libero di un triangolo equilatero

$I=3\,A$ in entrambi i fili (uscenti dal foglio), lato $L=2\,m$.

Ogni filo genera nel vertice opposto (distanza $=L=2\,m$):

$$B=\frac{\mu_0 I}{2\pi L}=2\times10^{-7}\cdot\frac{3}{2}=3\times10^{-7}\,T$$

Con corrente uscente dal foglio, $\vec B$ in un punto è perpendicolare al segmento filo–punto, ruotato di 90° in senso antiorario. Scomponendo i due contributi (ciascuno inclinato di 30° rispetto alla base, per la geometria del triangolo equilatero) e sommando vettorialmente, le componenti perpendicolari alla base si cancellano e quelle parallele alla base si sommano:

$$B_{tot}=2\cdot B\cos(30°)=2\cdot3\times10^{-7}\cdot\frac{\sqrt3}{2}=\sqrt3\cdot3\times10^{-7}\approx5.2\times10^{-7}\,T$$

Direzione: **parallela al lato che congiunge i due fili**, verso l'esterno del triangolo (uscente oltre uno dei due vertici sorgente, dal lato opposto rispetto al terzo vertice).

## 7. Momento meccanico sulla spira

$AB=10\,cm=0.1\,m$, $BC=20\,cm=0.2\,m$, $I=5\,A$, $B=2\,T$, spira parallela alle linee di campo ($\Rightarrow \vec m \perp \vec B$, $\theta=90°$).

$$A_{spira}=AB\cdot BC=0.1\cdot0.2=0.02\,m^2$$
$$m=IA=5\cdot0.02=0.1\,A\cdot m^2$$
$$\tau=mB\sin\theta=0.1\cdot2\cdot1=0.2\,N\cdot m$$

Direzione: asse di rotazione perpendicolare sia a $\vec m$ che a $\vec B$ (quindi giacente nel piano della spira, parallelo ai lati), verso dato da $\vec\tau=\vec m\times\vec B$, tale da far ruotare la spira per allineare $\vec m$ con $\vec B$ (in questa configurazione il momento è massimo, essendo $\theta=90°$).

**Dispositivo:** è il principio del **motore elettrico in corrente continua** (e dello strumento a bobina mobile/galvanometro): la coppia $\vec\tau$ fa ruotare la spira; un commutatore (spazzole) inverte periodicamente il verso della corrente ogni mezzo giro così che la coppia continui a spingere nello stesso senso, mantenendo la rotazione continua.
