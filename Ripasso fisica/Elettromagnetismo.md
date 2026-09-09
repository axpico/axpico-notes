# Esercizi VII incontro - Circuiti elettrici

## Formule di base

**[[Legge di Ohm]]:** V = I·R

**Resistenza di un filo:** R = ρ·L/A, con A = π·r² = π·d²/4 (ρ = resistività, dipende dal materiale)

**[[Densità di corrente]]:** J = I/A

**Serie (resistori):**
- stessa corrente I in tutti gli elementi
- R_eq = R1 + R2 + ...
- la ddp si "divide" proporzionalmente a R: V1/V2 = R1/R2

**Parallelo (resistori):**
- stessa ddp V ai capi di ogni ramo
- 1/R_eq = 1/R1 + 1/R2 + ...
- la corrente si divide: I1/I2 = R2/R1 (inversamente alle resistenze)

**Generatore reale:** V_ai_capi = ε − I·r_interna (r = resistenza interna); cortocircuito → R_esterna=0 → I = ε/r

**Condensatori — serie:** 1/C_eq = 1/C1+1/C2+... , stessa carica Q su ogni armatura, la ddp si divide
**Condensatori — parallelo:** C_eq = C1+C2+..., stessa ddp V, la carica si divide: Q = C·V

**[[Potenza]]:** P = V·I = I²·R = V²/R

---

## 1. R1, R2 serie/parallelo

**Serie (6V):** stessa corrente in R1 e R2 → V1/V2 = R1/R2. V1=4V ⇒ V2=2V ⇒ **R1 = 2·R2**

**Parallelo (stessa batteria 6V):** ogni resistenza vede tutta la ddp (6V) ⇒
R2 = V/I2 = 6/0,45 = **13,3 Ω**
R1 = 2·R2 = **26,7 Ω**

*Verifica:* in serie R_tot=40Ω, I=6/40=0,15A, V1=0,15·26,7=4V ✓

---

## 2. Lampadine e fusibile

Corrente massima erogabile: I_max = 5 A a V = 220 V ⇒ P_max = V·I_max = 220·5 = **1100 W**

n° lampadine = 1100/75 = 14,67 → **massimo 14 lampadine**

Schema: nell'impianto domestico le lampadine sono in **parallelo** (ognuna vede sempre 220V, si può accendere/spegnere una senza spegnere le altre), il fusibile è in **serie** sulla linea principale prima delle diramazioni:

```
Rete 220V ──[fusibile 5A]──┬──[lampadina]──┐
                            ├──[lampadina]──┤
                            ├──[lampadina]──┤ (tutte in parallelo)
                            └── ... ────────┘
```

---

## 3. Rapporto dei raggi

R = ρL/(πr²), stesso L. Dato R1 = 2·R2:

R1/R2 = (ρ1/ρ2)·(r2²/r1²) = 2

r2²/r1² = 2·ρ2/ρ1 = 2 · (2,475·10⁻⁷ / 2,75·10⁻⁸) = 2·9 = 18

**r2/r1 = √18 ≈ 4,24** → cioè r1/r2 ≈ 0,236 (il filo 1, più conduttivo, ha raggio ~4,24 volte più piccolo del filo 2)

---

## 4. Filo di rame + filo di ferro in serie

A = π(d/2)² = π·(0,001)² = 3,1416·10⁻⁶ m²

R_Cu = ρ_Cu·L/A = 1,7·10⁻⁸·10 / 3,1416·10⁻⁶ = **0,0541 Ω**
R_Fe = ρ_Fe·L/A = 1,0·10⁻⁷·10 / 3,1416·10⁻⁶ = **0,318 Ω**

Sono uniti (stesso filo, stessa corrente) → **serie**: R_tot = 0,372 Ω

I = V/R_tot = 100/0,372 = **268,5 A** (stessa in entrambi, essendo in serie)

V_Cu = I·R_Cu = 268,5·0,0541 = **14,5 V**
V_Fe = I·R_Fe = 268,5·0,318 = **85,5 V** (somma = 100V ✓)

J = I/A = 268,5/3,1416·10⁻⁶ = **8,55·10⁷ A/m²** (uguale per entrambi: stessa sezione, stessa corrente)

---

## 5. Anelli di nichel-cromo

Quando un anello chiuso di resistenza totale R viene collegato al circuito in due punti diametralmente opposti, la corrente si divide nei due semianelli (ciascuno R/2) che sono **in parallelo** tra loro:

R_anello_effettiva = (R/2 · R/2)/(R/2+R/2) = **R/4**

Se i due anelli (R1, R2) sono collegati in serie fra loro e col generatore, come da figura:

**R_sistema = R1/4 + R2/4 = (R1+R2)/4**

---

## 6. Circuito con R2=60Ω, R3=240Ω

*Manca la figura con i valori delle correnti per calcolare i numeri esatti — completare quando disponibile.*

Metodo:
- se R2 e R3 sono **in parallelo**, hanno la stessa ddp: V = I2·R2 = I3·R3 → puoi trovare l'incognita mancante a partire da una corrente nota
- la corrente totale che entra nel parallelo è I_tot = I2 + I3 (nodo, legge di Kirchhoff delle correnti)
- una volta nota V del parallelo, se c'è un'altra R in serie usa V_tot = V_serie + V_parallelo

---

## 7. Batteria 12V, r=0,5Ω

**a)** Cortocircuito (R_esterna=0): I = ε/r = 12/0,5 = **24 A**

**b)** Con I=2A: V_R = ε − I·r = 12 − 2·0,5 = **11 V**
R = V_R/I = 11/2 = **5,5 Ω**

**c)** Per sfruttare al meglio la fem (minimizzare le perdite sulla resistenza interna) serve **R >> r**, cioè correnti basse rispetto al cortocircuito: quasi tutta la ddp del generatore cade sull'utilizzatore invece che dissiparsi internamente. (Nota: R=r dà la massima *potenza* trasferita, ma non la massima efficienza — sono due condizioni diverse.)

---

## 8. Filo tagliato in n parti, poi in parallelo

Ogni parte, essendo 1/n della lunghezza, ha resistenza R/n (R ∝ L).
n resistenze uguali R/n in parallelo: R_eq = (R/n)/n = **R/n²**

320/n² = 5 → n² = 64 → **n = 8 parti**

---

## 9. Condensatori tra a e b, V=150V, C=1μF

*Manca la figura con la topologia dei condensatori — completare quando disponibile.*

Metodo generale:

- **Se tutti in serie:** stessa carica Q su tutti; C_eq = 1/(Σ1/Ci); Q = C_eq·150; poi V_i = Q/C_i
- **Se tutti in parallelo:** stessa ddp 150V su ognuno; Q_i = C_i·150
- **Se misto** (es. due in serie, il gruppo in parallelo con un terzo): calcola prima il gruppo serie (stessa Q, V si divide), poi applica il parallelo (stessa V, Q = C·V per ogni ramo)
