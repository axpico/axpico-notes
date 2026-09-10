---
tags: [fisica, ripasso, energia, [[Lavoro]], urti, quantità-di-moto]
---
# Energia e gravitazione

## Lavoro

$$W = \int F\, dx$$

Forma generale, valida anche se $F$ varia lungo il percorso (es. una molla): si somma il contributo $F\,dx$ tratto per tratto.

Se $\vec F$ è **costante**, il [[Lavoro]] è il prodotto scalare tra forza e spostamento:

$$W = \vec F \cdot \Delta \vec x = F\,\Delta x \cos\alpha$$

dove $F$ e $\Delta x$ sono i moduli di forza e spostamento, e $\alpha$ è l'angolo tra $\vec F$ e lo spostamento (il prodotto scalare "pesa" solo la componente della forza lungo lo spostamento — la parte perpendicolare non compie [[Lavoro]]):

| Angolo $\alpha$ | Segno di $W$ | Significato |
| --- | --- | --- |
| $0 \le \alpha < \pi/2$ | $W>0$ | lavoro motore |
| $\alpha = \pi/2$ | $W=0$ | forza perpendicolare allo spostamento, nessun lavoro |
| $\pi/2 < \alpha \le \pi$ | $W<0$ | lavoro resistente |

**Teorema dell'energia cinetica**: $W_{tot} = \Delta E_k$

## Potenza

$$P = \frac{W}{t} \qquad \text{(istantanea: } P = \frac{dW}{dt} = \vec F \cdot \vec v\text{)}$$

Quanto lavoro viene fatto per unità di tempo. La forma istantanea serve quando velocità/forza cambiano nel tragitto (es. es. 3).

## Energia cinetica

$$E_k = \frac12 m v^2$$

Energia associata al moto. Cresce col quadrato della velocità: raddoppiare $v$ significa quadruplicare $E_k$.

## Energia potenziale gravitazionale

$$U_g = mgh$$

$h$ è la quota rispetto a un livello di riferimento scelto a piacere (solo le differenze di $U_g$ contano fisicamente).

## Energia potenziale elastica

$$E_e = \frac12 k x^2$$

con $x$ = allungamento/compressione rispetto alla posizione di riposo della molla. Come $E_k$, è sempre $\ge 0$ e cresce col quadrato di $x$.

## Conservazione dell'energia

Energia meccanica:

$$E_m = E_k + U$$

- **Forze conservative** (gravità, forza elastica): il lavoro non dipende dal percorso, solo da punto iniziale e finale → definiscono un'energia potenziale.
- **Forze non conservative / dissipative** (attrito, resistenza dell'aria): dissipano energia meccanica in calore.

$$\Delta E_m = W_{nc}$$

La variazione di energia meccanica è uguale al lavoro fatto dalle forze non conservative (es. l'attrito toglie energia, $W_{nc}<0$, quindi $E_m$ diminuisce).

Se agiscono **solo** forze conservative, $E_m$ è costante ($\Delta E_m = 0$): è il caso "senza attrito" usato in quasi tutti gli esercizi sotto.

## Urti

- **Urto elastico**: si conservano sia la quantità di moto sia l'energia cinetica.
- **Urto anelastico**: si conserva solo la quantità di moto; parte di $E_k$ si trasforma in altre forme (calore, deformazione).
- **Urto completamente anelastico**: i corpi restano uniti dopo l'urto (v finale comune).

## Quantità di moto

$$\vec q = m \vec v$$

Vettoriale (stessa direzione di $\vec v$). In un sistema isolato (nessuna forza esterna, es. durante un urto) si conserva:

$$\sum \vec q_{i} = \sum \vec q_{f}$$

A differenza dell'energia cinetica, la quantità di moto totale si conserva **sempre** in un urto, anche quando è anelastico — è questo che rende risolvibili gli urti senza sapere quanta energia si dissipa.

## Proprietà — riepilogo

| Grandezza | Simbolo | Formula | Unità SI | Tipo |
| --- | --- | --- | --- | --- |
| Lavoro | $W$ | $\int F\,dx$ , o $F\Delta x\cos\alpha$ | J (joule) | scalare |
| Potenza | $P$ | $W/t$ | W (watt) | scalare |
| Energia cinetica | $E_k$ | $\frac12 mv^2$ | J | scalare, $\ge 0$ |
| Energia pot. gravitazionale | $U_g$ | $mgh$ | J | scalare |
| Energia pot. elastica | $E_e$ | $\frac12 kx^2$ | J | scalare, $\ge 0$ |
| Energia meccanica | $E_m$ | $E_k+U$ | J | scalare |
| Quantità di moto | $\vec q$ | $m\vec v$ | kg·m/s | vettoriale |

---

# Esercizi III incontro

## 1. Pallottola nel mattoncino

**Dati**: $m=10\text{ g}=0.01\text{ kg}$, $v=100\text{ m/s}$, $M=9.990\text{ kg}$ ferma, $\mu=0.4$ (attrito), la pallottola resta conficcata (urto completamente anelastico).

Conservazione della [[Quantità di moto]] durante l'urto ($m+M = 10.000$ kg):

$$v' = \frac{mv}{m+M} = \frac{0.01\cdot100}{10} = 0.1\ \text{m/s}$$

Dopo l'urto il blocco decelera per attrito: $a = \mu g = 0.4\cdot9.8 = 3.92\ \text{m/s}^2$.

$$d = \frac{v'^2}{2a} = \frac{0.1^2}{2\cdot3.92} \approx 1.3\times10^{-3}\ \text{m} \approx 1.3\ \text{mm}$$

## 2. Slitta e respingente

**Dati**: $h=8$ m, tratto orizzontale $L=10$ m, molla ideale (respingente) orizzontale.

**a)** Se tutto il tratto orizzontale è ghiacciato (senza attrito), non c'è alcuna dissipazione: la molla è una forza conservativa, quindi restituisce integralmente l'[[Energia cinetica]] ricevuta, qualunque sia $k$. La slitta torna sempre in cima al pendio con la stessa energia di partenza.

→ **Qualsiasi valore di $k>0$ va bene** (l'attrito nullo, non la costante elastica, è ciò che garantisce il ritorno in quota).

**b)** Ora il tratto orizzontale ha attrito $\mu$ ovunque tranne che nell'intorno immediato della molla (dove avviene l'urto elastico, senza perdite). La slitta percorre $L$ andando e $L$ tornando ($2L=20$ m) con attrito, poi risale il pendio (ghiacciato) fermandosi a $h/2$.

Bilancio energetico:

$$mgh - \mu m g (2L) = mg\frac{h}{2}$$

$$\mu = \frac{h - h/2}{2L} = \frac{h}{4L} = \frac{8}{40} = 0.2$$

## 3. Cassa di viveri (Pordoi → Sass Pordoi)

**Dati**: $m=10$ kg, $\Delta h = 2950-2239=711$ m.

**a)** Funivia, $t=4\text{ min}=240$ s, attriti trascurati. La cassa parte e arriva ferma (ΔEk=0), quindi il [[Lavoro]] del pavimento sulla cassa compensa esattamente quello della gravità:

$$W = mg\Delta h = 10\cdot9.8\cdot711 \approx 6.97\times10^4\ \text{J}$$

$$P = \frac{W}{t} = \frac{69678}{240} \approx 290\ \text{W}$$

Questa **non** coincide con la [[Potenza]] erogata dal motore dell'impianto: il motore deve sollevare/muovere anche la cabina, i cavi, gli altri passeggeri, ecc. — la cassa da sola è solo una piccola frazione del carico totale.

**b)** Mulo, $P\approx100$ W:

$$t = \frac{W}{P} = \frac{69678}{100} \approx 697\ \text{s} \approx 11.6\ \text{min}$$

(valore puramente energetico: nella realtà un mulo impiega molto di più, perché parte della sua [[Potenza]] serve a muovere sé stesso e a vincere attriti lungo il sentiero — qui si trascura tutto tranne il dislivello).

## 4. Giro della morte (loop)

Pallina che striscia senza attrito e senza rotolare: condizione minima in cima al loop (raggio $R$) è che la gravità fornisca esattamente la forza centripeta:

$$mg = \frac{mv_{top}^2}{R} \ \Rightarrow\ v_{top}^2 = gR$$

Conservazione dell'energia dall'altezza di partenza $h$ (rispetto alla base) alla cima del loop (quota $2R$):

$$mgh = mg(2R) + \frac12 m v_{top}^2 = 2mgR + \frac12 mgR$$

$$\boxed{h_{min} = \frac{5}{2}R}$$

## 5. Urto tra tre automobili

Metodo: la [[Quantità di moto]] totale si conserva (sistema isolato durante l'urto):

$$\vec q_{tot} = m_A\vec v_A + m_B\vec v_B + m_C\vec v_C$$

$$\vec v_{f} = \frac{\vec q_{tot}}{m_A+m_B+m_C}, \qquad m_A+m_B+m_C = 3100\ \text{kg}$$

Modulo e direzione di $\vec v_f$ si ottengono sommando vettorialmente i tre $m_i\vec v_i$ secondo gli angoli mostrati in figura (serve la geometria esatta dell'incrocio, non riportata qui — applica la formula sopra con le componenti $x,y$ di ciascuna velocità).

## 6. Massa del Sole

Orbita circolare, forza gravitazionale = forza centripeta:

$$\frac{GM_\odot m}{r^2} = \frac{4\pi^2 r}{T^2}m \ \Rightarrow\ M_\odot = \frac{4\pi^2 r^3}{GT^2}$$

Con $r=1.5\times10^{11}$ m, $T=1\text{ anno}\approx3.156\times10^7$ s, $G=6.674\times10^{-11}\ \text{N m}^2/\text{kg}^2$:

$$M_\odot \approx 2.0\times10^{30}\ \text{kg}$$

## 7. Gravità sulla ISS

$$g(h) = g_0\left(\frac{R_t}{R_t+h}\right)^2$$

Con $R_t=6380$ km, $h=400$ km:

$$g(h) = 9.8\left(\frac{6380}{6780}\right)^2 \approx 8.7\ \text{m/s}^2$$

Cioè circa l'89% della gravità superficiale: **non è affatto trascurabile**. Il "galleggiamento" di Samantha Cristoforetti non è assenza di gravità, ma **caduta libera continua**: la ISS e tutto ciò che contiene accelerano verso la Terra alla stessa velocità mentre orbitano, quindi non c'è forza normale relativa percepita (assenza di peso apparente), non assenza di $g$.
