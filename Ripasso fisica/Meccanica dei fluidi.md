---
tags: [fisica, ripasso, meccanica-dei-fluidi, statica-dei-fluidi, idrodinamica]
---
# Meccanica dei fluidi

## Pressione

$$p = \frac{F}{A}$$

Unità SI: Pa (pascal) = N/m². Utile anche l'atmosfera: 1 atm ≈ 1.013×10⁵ Pa.

## Legge di Pascal

In un fluido in equilibrio racchiuso in un recipiente, una variazione di pressione applicata in un punto si trasmette **inalterata** in ogni altro punto del fluido. Conseguenza pratica: nel torchio idraulico, due pistoni comunicanti soddisfano

$$\frac{F_A}{A_A} = \frac{F_B}{A_B}$$

Con superfici diverse si amplifica una forza modesta in una forza molto più grande (a scapito dello spostamento, per conservazione dell'energia).

## Legge di Stevino

$$\Delta p = \rho\, g\, \Delta h$$

In un fluido in quiete la pressione cresce linearmente con la profondità. È la base dei manometri a colonna di liquido: confrontando i livelli nei due rami di un tubo a U si risale alla pressione incognita.

- Se il livello è più alto nel ramo **aperto** all'atmosfera: $p_{gas} = p_{atm} + \rho g \Delta h$
- Se il livello è più alto nel ramo **collegato al gas**: $p_{gas} = p_{atm} - \rho g \Delta h$

## Principio di Archimede

$$F_A = \rho_{fluido}\, g\, V_{immerso}$$

Un corpo immerso (parzialmente o totalmente) riceve una spinta verso l'alto pari al peso del fluido spostato. Confrontando spinta e peso:

| Condizione | Comportamento |
| --- | --- |
| $F_A > P$ | il corpo sale, poi galleggia con $V_{immerso}$ ridotto finché $F_A=P$ |
| $F_A < P$ | il corpo affonda |
| $F_A = P$ | equilibrio (fluttua, oppure galleggia stabilmente) |

Per un corpo che galleggia, l'equilibrio impone $\rho_{fluido}\,g\,V_{sommerso} = m\,g$, cioè $V_{sommerso} = m/\rho_{fluido}$ — indipendente dalla densità del corpo.

## Equazione di continuità

$$Q = A\,v = \text{costante}$$

In un condotto senza perdite la portata volumetrica si conserva: dove la sezione si restringe la velocità aumenta (e viceversa).

## Equazione di Bernoulli

$$p + \frac12 \rho v^2 + \rho g h = \text{costante}$$

lungo una linea di flusso di un fluido ideale (non viscoso, incomprimibile). Lega pressione, velocità di flusso e quota.

---

# Esercizi IV incontro

## 1. Torchio idraulico

**Dati**: raggio pistone A $r_A=4$ cm, forza applicata $F_A=490$ N, massa da sollevare $m=6000$ kg.

Legge di Pascal: $F_A/A_A = F_B/A_B$, con $A=\pi r^2$.

$$A_A = \pi(0.04)^2 = 5.027\times10^{-3}\ \text{m}^2$$
$$F_B = mg = 6000\cdot9.8 = 58800\ \text{N}$$
$$A_B = A_A\cdot\frac{F_B}{F_A} = 5.027\times10^{-3}\cdot\frac{58800}{490} = 0.603\ \text{m}^2$$

$$\boxed{r_B = \sqrt{A_B/\pi} \approx 0.438\ \text{m} = 43.8\ \text{cm}}$$

## 2. Galleggiante cubico + cubo sospeso

**Dati**: cubo 1 (galleggiante) $L_1=10$ cm, $m_1=0.2$ kg; cubo 2 (sospeso, in acqua) $L_2=5$ cm, $m_2=0.3$ kg. Densità del cubo 2: $0.3\text{ kg}/125\text{ cm}^3 = 2.4$ g/cm³ > 1 → affonda completamente, resta appeso sotto il galleggiante.

Sistema completo, [[Principio di Archimede|spinta]] totale = peso totale:

$$V_{1,sub} + V_2 = \frac{m_1+m_2}{\rho_{acqua}} = \frac{0.5}{1000} = 500\ \text{cm}^3$$

Con $V_2=125\ \text{cm}^3$ (completamente immerso) → $V_{1,sub}=375\ \text{cm}^3$.

$$h_{emerso} = L_1 - L_1\frac{V_{1,sub}}{L_1^3} = 10 - 10\cdot\frac{375}{1000} = \boxed{6.25\ \text{cm}}$$

Tensione (equilibrio del cubo 2 sospeso, spinta + tensione = peso):

$$F_{A,2} = \rho g V_2 = 1000\cdot9.8\cdot125\times10^{-6} = 1.225\ \text{N}$$
$$P_2 = m_2 g = 0.3\cdot9.8 = 2.94\ \text{N}$$
$$\boxed{T = P_2 - F_{A,2} = 1.715\ \text{N}}$$

(verifica sul cubo 1: $F_{A,1}=\rho g V_{1,sub}=3.675$ N, $P_1=1.96$ N, $T=F_{A,1}-P_1=1.715$ N ✓)

## 3. Tappo di sughero fissato al fondo

**Dati**: $m=200$ g, $\rho_{sughero}=900$ kg/m³ → $V = m/\rho = 2.222\times10^{-4}\ \text{m}^3$.

**a)** Completamente immerso e fissato: la spinta supera il peso, il filo tira verso il basso.

$$F_A = \rho_{acqua}\,g\,V = 1000\cdot9.8\cdot2.222\times10^{-4} = 2.178\ \text{N}$$
$$P = mg = 0.2\cdot9.8 = 1.96\ \text{N}$$
$$\boxed{T = F_A - P = 0.218\ \text{N}}$$

**b)** Filo tagliato, appena immerso: $a = (F_A-P)/m$, equivalente a

$$\boxed{a = g\left(\frac{\rho_{acqua}}{\rho_{sughero}} - 1\right) = 9.8\left(\frac{1000}{900}-1\right) \approx 1.09\ \text{m/s}^2}\ \text{(verso l'alto)}$$

**c)** A galleggiamento, $F_A=P$:

$$V_{sommerso} = \frac{m}{\rho_{acqua}} = \frac{0.2}{1000} = 200\ \text{cm}^3$$
$$\boxed{V_{emerso} = 222.2 - 200 = 22.2\ \text{cm}^3}$$

## 4. Canna per innaffiare

**Dati**: canna $d=2$ cm ($r=1$ cm), $v_{canna}=1$ m/s; spruzzatore con 20 fori $d_{foro}=0.20$ cm ($r=0.1$ cm).

[[Equazione di continuità|Continuità]]: $Q = A\,v$ costante.

$$A_{canna} = \pi(0.01)^2 = 3.1416\times10^{-4}\ \text{m}^2 \Rightarrow Q = 3.1416\times10^{-4}\ \text{m}^3/\text{s}$$
$$A_{foro} = \pi(0.001)^2 = 3.1416\times10^{-6}\ \text{m}^2,\quad 20\ A_{foro} = 6.283\times10^{-5}\ \text{m}^2$$

$$\boxed{v_{fori} = Q/A_{tot} = 5\ \text{m/s}}$$

Getto orizzontale da $h=1$ m (moto parabolico, $v_0=5$ m/s):

$$t = \sqrt{2h/g} = \sqrt{2/9.8} = 0.452\ \text{s}$$
$$\boxed{d = v_0\,t = 5\cdot0.452 \approx 2.26\ \text{m}}$$

## 5. Manometro a mercurio

Senza la figura/il valore del dislivello non si può dare il numero, ma il metodo (Stevino) è:

- se il mercurio è più alto nel ramo **aperto**: $p_{gas} = p_{atm} + \rho_{Hg}\,g\,\Delta h$
- se è più alto nel ramo **collegato al gas**: $p_{gas} = p_{atm} - \rho_{Hg}\,g\,\Delta h$

con $\rho_{Hg}=13\,600$ kg/m³. Basta sostituire $\Delta h$ per ottenere il valore numerico.
