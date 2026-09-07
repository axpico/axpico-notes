---
tags: [fisica, ripasso, termodinamica, calorimetria, gas-ideali, entropia, cicli-termodinamici]
---
# Termodinamica

## Dilatazione termica

$$\Delta L = L_0\,\lambda\,\Delta T \qquad \Delta V = V_0\,\gamma\,\Delta T \ (\gamma \approx 3\lambda \text{ per solidi isotropi})$$

Un materiale si allunga (o accorcia) linearmente con la variazione di temperatura. $\lambda$ è il coefficiente di dilatazione lineare, caratteristico del materiale.

## Calore e capacità termica

$$Q = m\,c\,\Delta T = C\,\Delta T$$

$c$ = calore specifico (J/kg·K o cal/g·K, caratteristico della sostanza), $C=mc$ = capacità termica dell'oggetto (J/K, dipende anche dalla massa).

**Equilibrio calorimetrico** (sistema isolato, nessuna dispersione con l'esterno): il calore ceduto dai corpi più caldi è uguale, in modulo, al calore assorbito dai corpi più freddi.

$$\sum_i Q_i = 0$$

## Cambiamenti di stato

$$Q = m\,\lambda$$

$\lambda$ = calore latente (di fusione, vaporizzazione, ecc.), positivo se il sistema assorbe calore (es. fusione, vaporizzazione), negativo se lo cede (es. solidificazione, condensazione). Durante il cambiamento di stato la temperatura resta costante.

## Gas ideali

$$pV = nRT \qquad R = 8.314\ \text{J/(mol·K)}$$

Energia interna di un gas ideale monoatomico (dipende solo da $T$):

$$U = \frac32 nRT \qquad \Delta U = \frac32 nR\,\Delta T = \frac32\,\Delta(pV)$$

(quest'ultima forma è comoda quando si conoscono $p$ e $V$ negli stati iniziale/finale, senza dover ricavare $n$ o $T$ separatamente.)

## Primo principio della termodinamica

$$\Delta U = Q - W \qquad W = \int p\,dV$$

$W$ = lavoro fatto **dal** gas (positivo se il gas si espande). Nel piano $p$-$V$, $W$ è l'area sottesa dalla curva della trasformazione.

### Trasformazioni notevoli (gas ideale)

| Trasformazione | Vincolo | Lavoro $W$ | Calore $Q$ |
| --- | --- | --- | --- |
| Isocora | $V=\text{cost}$ | $0$ | $\Delta U = nC_V\Delta T$ |
| Isobara | $p=\text{cost}$ | $p\,\Delta V$ | $nC_p\Delta T$ |
| Isoterma | $T=\text{cost}$ | $nRT\ln(V_f/V_i)$ | $=W$ (poiché $\Delta U=0$) |
| Adiabatica | $Q=0$ | $-\Delta U$ | $0$ |

**Calori molari** (gas monoatomico): $C_V = \tfrac32 R$, $C_p = C_V+R = \tfrac52 R$ (relazione di Mayer: $C_p-C_V=R$).

## Secondo principio ed entropia

$$\Delta S = \int \frac{dQ_{rev}}{T}$$

Per una trasformazione reversibile a temperatura costante (es. un cambiamento di stato):

$$\Delta S = \frac{Q}{T}$$

## Cicli termodinamici e rendimento

In un ciclo, $\Delta U_{ciclo}=0$, quindi $Q_{netto}=W_{netto}$. Il rendimento è il rapporto tra il lavoro utile ottenuto e il calore fornito al sistema (solo la parte assorbita):

$$\eta = \frac{W_{netto}}{Q_{assorbito}} = 1 - \frac{|Q_{ceduto}|}{Q_{assorbito}}$$

---

# Esercizi IV incontro

## 6. Dilatazione termica di un viadotto

**Dati**: $L_0=2000$ m, $T_{inv}=-10°C$, $T_{est}=40°C$, $\lambda=1.5\times10^{-5}\ \text{K}^{-1}$.

$$\Delta L = L_0\,\lambda\,\Delta T = 2000\cdot1.5\times10^{-5}\cdot50 = \boxed{1.5\ \text{m}}$$

$$L_{estate} = 2000+1.5 = 2001.5\ \text{m}$$

Nella realtà si usano **giunti di dilatazione**: interrompono la struttura in campate separate con spazi che assorbono l'allungamento, evitando che si generino tensioni interne pericolose.

## 7. Calore specifico di un metallo (calorimetro)

**Dati**: $m_{metallo}=100$ g a $100°C$, $m_{acqua}=500$ g a $20°C$, $T_{eq}=22°C$, $c_{acqua}=1$ cal/(g·K).

Bilancio calorimetrico: calore ceduto dal metallo = calore assorbito dall'acqua.

$$m_{met}\,c_{met}\,(100-22) = m_{acqua}\,c_{acqua}\,(22-20)$$
$$0.1\,c_{met}\cdot78 = 0.5\cdot4186\cdot2 = 4186\ \text{J}$$

$$\boxed{c_{met} = \frac{4186}{7.8} \approx 537\ \text{J/(kg·K)} \approx 0.128\ \text{cal/(g·K)}}$$

## 8. Potenza di un frigorifero (raffreddamento + congelamento)

**Dati**: $m=20$ g acqua, $T_i=20°C \to T_f=-15°C$ (congelando completamente), $\Delta t=30$ min, $\lambda_{sol}=-335$ kJ/kg, $c_{acqua}=1$ cal/g·K $=4186$ J/(kg·K), $c_{ghiaccio}=2090$ J/(kg·K).

Tre fasi:

1. Raffreddamento acqua $20\to0°C$: $Q_1 = 0.02\cdot4186\cdot20 = 1674\ \text{J}$
2. Solidificazione a $0°C$: $Q_2 = 0.02\cdot335000 = 6700\ \text{J}$
3. Raffreddamento ghiaccio $0\to-15°C$: $Q_3 = 0.02\cdot2090\cdot15 = 627\ \text{J}$

$$Q_{tot} = 1674+6700+627 = 9001\ \text{J}$$

$$\boxed{P = \frac{Q_{tot}}{\Delta t} = \frac{9001}{1800} \approx 5.0\ \text{W}}$$

---

# Esercizi V incontro

## 1. Calorimetria: proiettile di rame in acqua

**Dati**: $m_{Cu}=75$ g a $312°C$, $m_{acqua}=220$ g a $T_a=20°C$, capacità termica del recipiente $C_r=45$ cal/K, $c_{acqua}=1$ cal/(g·K), $c_{Cu}\approx0.092$ cal/(g·K) (valore tabulato del rame — non essendo dato dal testo).

Bilancio calorimetrico (calore ceduto dal rame = calore assorbito da acqua + recipiente):

$$m_{Cu}c_{Cu}(312-T_{eq}) = (m_{acqua}c_{acqua}+C_r)(T_{eq}-20)$$
$$6.9\,(312-T_{eq}) = 265\,(T_{eq}-20)$$
$$2152.8 - 6.9T_{eq} = 265T_{eq} - 5300$$
$$7452.8 = 271.9\,T_{eq}$$

$$\boxed{T_{eq} \approx 27.4°C}$$

## 2. Espansione con $p=p_0(V_0/V)^2$

**Dati**: 1 mole gas monoatomico, $T_0=300$ K a $V_0$, si espande fino a $V=2V_0$ secondo $p=p_0(V_0/V)^2$.

**a)** A $V=2V_0$: $p = p_0/4$. Uso $pV=nRT$ (con $n=1$):

$$T = T_0\cdot\frac{pV}{p_0V_0} = T_0\cdot\frac{(p_0/4)(2V_0)}{p_0V_0} = T_0\cdot\frac12$$

$$\boxed{T = 150\ \text{K}}$$

**b)** Energia interna (monoatomico, $C_V=\tfrac32R$):

$$\Delta U = \frac32 R\,\Delta T = 1.5\cdot8.314\cdot(150-300)$$

$$\boxed{\Delta U \approx -1871\ \text{J}}$$

## 3. Solido caldo in gas adiabatico rigido

**Dati**: recipiente rigido adiabatico, $n=2$ mol gas monoatomico, $p_0=2\times10^5$ Pa, $T_0=300$ K; solido con $C=30$ J/K a $T_s=800$ K introdotto nel recipiente.

Il recipiente è isolato (adiabatico verso l'esterno) e rigido: tutto il calore ceduto dal solido va al gas.

$$C(T_s-T_f) = nC_V(T_f-T_0), \qquad nC_V = 2\cdot\tfrac32\cdot8.314 = 24.94\ \text{J/K}$$
$$30(800-T_f) = 24.94(T_f-300)$$
$$31482.6 = 54.94\,T_f \Rightarrow T_f \approx 573\ \text{K}$$

Volume costante (recipiente rigido) → $p/T=\text{cost}$:

$$\boxed{p_f = p_0\cdot\frac{T_f}{T_0} = 2\times10^5\cdot\frac{573}{300} \approx 3.82\times10^5\ \text{Pa}}$$

## 4. Calori molari incogniti: $\Delta T$ da due riscaldamenti

**Dati**: $n=2$ mol, a $V$ costante $Q_V=217$ J, a $p$ costante $Q_p=300$ J per la stessa $\Delta T$.

$$Q_p - Q_V = n(C_p-C_V)\Delta T = nR\,\Delta T$$

(relazione di Mayer, valida per **qualunque** gas ideale, indipendentemente dalla composizione)

$$300-217 = 2\cdot8.314\cdot\Delta T$$

$$\boxed{\Delta T = \frac{83}{16.628} \approx 5.0\ \text{K}}$$

## 5. Espansione lineare nel piano p-V

**Dati**: gas monoatomico, retta da $(V_1,p_1)$ a $(V_2,p_2)=(10\ \text{cm}^3, 4\times10^5\ \text{Pa})$, con $V_1=\tfrac23V_2=6.667\ \text{cm}^3$, $p_1=2p_2=8\times10^5$ Pa.

Lavoro = area del trapezio sotto la retta:

$$W = \frac{p_1+p_2}{2}(V_2-V_1) = \frac{1.2\times10^6}{2}\cdot3.333\times10^{-6} = \boxed{2.0\ \text{J}}$$

Variazione di energia interna (monoatomico, $\Delta U=\tfrac32\Delta(pV)$):

$$p_1V_1 = 5.333\ \text{J},\quad p_2V_2 = 4.0\ \text{J}$$
$$\Delta U = 1.5\cdot(4.0-5.333) = \boxed{-2.0\ \text{J}}$$

Primo principio:

$$\boxed{Q = \Delta U + W = -2.0+2.0 = 0\ \text{J}}$$

## 6. Variazione di entropia nella vaporizzazione

**Dati**: 2 L acqua a $100°C$ ($m=2000$ g, densità $\approx1$ g/cm³), calore latente di vaporizzazione $c_e=540$ cal/g, $T=373$ K.

$$Q = m\,c_e = 2000\cdot540 = 1\,080\,000\ \text{cal}$$

$$\Delta S = \frac{Q}{T} = \frac{1\,080\,000}{373} \approx 2895\ \text{cal/K}$$

$$\boxed{\Delta S \approx 2895\ \text{cal/K} \approx 1.21\times10^4\ \text{J/K}}$$

## 7. Ciclo con due isocore e due isobare

**Dati**: $p_A=8$ atm, $p_D=4$ atm, $V_A=2$ L, $V_B=6$ L. Ciclo rettangolare nel piano $p$-$V$: A$(8\text{atm},2\text{L})\to$B$(8\text{atm},6\text{L})\to$C$(4\text{atm},6\text{L})\to$D$(4\text{atm},2\text{L})\to$A, gas monoatomico.

Uso $1\ \text{atm·L}=101.325$ J. Tabella di $pV$ (in atm·L) nei 4 stati: A$=16$, B$=48$, C$=24$, D$=8$.

**a)** AB isobara (espansione, $p=8$ atm):

$$W_{AB} = p_A(V_B-V_A) = 8\cdot4 = 32\ \text{atm·L} \approx \boxed{3242\ \text{J}}$$

**b)** BC isocora ($V=6$ L, $W=0$, quindi $Q_{BC}=\Delta U_{BC}$):

$$\Delta U_{BC} = \frac32(pV_C-pV_B) = 1.5\cdot(24-48) = -36\ \text{atm·L}$$

$$\boxed{Q_{BC} \approx -3648\ \text{J}}\ \text{(calore ceduto dal gas)}$$

**c)** Rendimento: servono tutte e 4 le trasformazioni.

| Tratto | $W$ (atm·L) | $\Delta U$ (atm·L) | $Q=\Delta U+W$ (atm·L) |
| --- | --- | --- | --- |
| AB (isobara) | 32 | 48 | 80 |
| BC (isocora) | 0 | −36 | −36 |
| CD (isobara) | −16 | −24 | −40 |
| DA (isocora) | 0 | 12 | 12 |

$$W_{netto} = 32+0-16+0 = 16\ \text{atm·L},\qquad Q_{assorbito} = 80+12 = 92\ \text{atm·L}$$

$$\boxed{\eta = \frac{W_{netto}}{Q_{assorbito}} = \frac{16}{92} \approx 0.174 = 17.4\%}$$
