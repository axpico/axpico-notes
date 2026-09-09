---
tags: [fisica, ripasso, esercizi, elettrostatica, campo-elettrico, condensatori, potenziale]
---
# Esercizi VI incontro

## Formule necessarie

**[[Legge di Coulomb]] / campo di carica puntiforme**
$$F = k\frac{q_1 q_2}{r^2} \qquad E = k\frac{q}{r^2} \qquad k = \frac{1}{4\pi\varepsilon_0} \approx 8.99\times10^9\ \text{N·m}^2/\text{C}^2$$
Il campo di più cariche si somma vettorialmente (sovrapposizione); su un asse comune conviene lavorare con i moduli e il verso.

**[[Potenziale Elettrico]]**
$$V = k\frac{q}{r} \qquad \Delta V = -\int \vec E \cdot d\vec l \qquad E_x = -\frac{dV}{dx}$$
Il campo è l'opposto della pendenza del grafico $V(x)$: dove $V$ è costante, $E=0$; dove $V$ è lineare, $E$ è costante e uniforme nel tratto.

**Energia potenziale di un sistema di cariche**
$$U = k\sum_{i<j}\frac{q_i q_j}{r_{ij}}$$
è anche il lavoro necessario per assemblare le cariche partendo da distanza infinita.

**Condensatore piano**
$$C = \varepsilon_0\frac{A}{d} \qquad Q = CV$$
Con carica $Q$ fissa (batteria scollegata): $V=Q/C$ cambia se cambia $C$, ma $Q$ resta costante.

**Energia cinetica <-> [[Lavoro]] elettrico**
$$\Delta K = q\Delta V \qquad (\text{per l'elettrone } q=-e,\ 1\ eV = e\cdot 1\ V)$$

**[[Teorema di Gauss]]**
$$\oint \vec E \cdot d\vec A = \frac{Q_{int}}{\varepsilon_0}$$
Si sceglie una superficie gaussiana con la stessa simmetria della distribuzione di carica (qui: cilindro coassiale al filo).

---

1. Due cariche puntiformi, una di $4\ \mu C$ e l'altra di $-9\ \mu C$, sono poste sull'asse x rispettivamente a $x = 50\ cm$ e a $x = 0\ cm$. Esiste sull'asse x un punto in cui il [[Campo Elettrico]] è nullo? Se sì, ricavalo.

   **Soluzione.** Cariche di segno opposto: tra di loro i due campi puntano nello stesso verso (si sommano, non si annullano mai). Il punto nullo può esistere solo fuori dal segmento, dal lato della carica più debole in modulo ($q_1=4\mu C$), cioè per $x>50\ cm$. Sia $d$ la distanza dalla carica da $4\mu C$ (quindi distanza dalla carica da $-9\mu C$ è $0.5+d$):
   $$k\frac{4}{d^2}=k\frac{9}{(0.5+d)^2} \;\Rightarrow\; 2(0.5+d)=3d \;\Rightarrow\; d=1\ m$$
   Punto nullo a $x = 0.5+1 = 1.5\ m$ (150 cm), oltre la carica positiva. Verifica: $E_1=k\cdot4\mu C/1^2$, $E_2=k\cdot9\mu C/1.5^2=k\cdot4\mu C/1$ → uguali. ✓

2. Un [[Condensatore Piano]] di capacità $C$ viene caricato con una batteria ad una certa ddp, poi viene scollegato dalla batteria. Come cambiano la capacità, la ddp e la carica accumulata sulle armature, se la distanza fra le armature dimezza?

   **Soluzione.** $C=\varepsilon_0 A/d$: dimezzando $d$, $C$ **raddoppia** ($C'=2C$). Scollegato dalla batteria non c'è più un percorso per far fluire carica: $Q$ **resta costante** (isolata). Di conseguenza $V=Q/C$ **si dimezza** ($V'=V/2$).

3. Il [[Potenziale Elettrico]] a una distanza $r$ da una carica puntiforme $q$ è pari a $V = 155\ V$, mentre il modulo del [[Campo Elettrico]] è pari a $E = 2240\ N/C$. Trova il valore di $q$ ed $r$.

   **Soluzione.** Da $V=kq/r$ ed $E=kq/r^2$: dividendo, $V/E = r$.
   $$r = \frac{155}{2240} \approx 0.0692\ m = 6.92\ cm$$
   $$q = \frac{Vr}{k} = \frac{155\times0.0692}{8.99\times10^9} \approx 1.19\times10^{-9}\ C = 1.19\ nC$$

4. Il grafico a lato fornisce il [[Potenziale Elettrico]] di un sistema in funzione della posizione lungo l'asse x. Trova il [[Campo Elettrico]] nelle regioni 1, 2, 3, 4.

   **Soluzione (metodo).** $E_x = -dV/dx$: in ogni regione dove $V(x)$ è un segmento rettilineo, $E_x$ è costante e vale meno la pendenza di quel segmento:
   $$E_x = -\frac{\Delta V}{\Delta x} = -\frac{V_{fine}-V_{inizio}}{x_{fine}-x_{inizio}}$$
   Regole pratiche: $V$ crescente $\Rightarrow E_x<0$ (campo verso $-x$); $V$ decrescente $\Rightarrow E_x>0$; $V$ costante (tratto piatto) $\Rightarrow E_x=0$. Non ho i valori numerici del grafico originale (immagine non allegata): calcola la pendenza di ciascuno dei 4 tratti con i punti del tuo grafico e applica la formula sopra. Esempio illustrativo del metodo (non i tuoi dati):

```desmos-graph
left=0; right=8; top=6; bottom=-2; grid=true;
---
y=\left\{0<x<2:2x\right\}
y=\left\{2<x<4:4\right\}|hidden
y=\left\{2\le x\le4:4\right\}
y=\left\{4<x<6:-2x+12\right\}
y=\left\{6\le x\le8:0\right\}
```
   In questo esempio: regione 1 ($0$-$2$, pendenza $+2$) → $E_x=-2$; regione 2 ($2$-$4$, piatta) → $E_x=0$; regione 3 ($4$-$6$, pendenza $-2$) → $E_x=+2$; regione 4 ($6$-$8$, piatta) → $E_x=0$. Sostituisci con i tuoi valori reali per il risultato corretto.

5. Quale è il [[Lavoro]] necessario per posizionare tre cariche $q_1 = q$, $q_2 = 2q$, $q_3 = 3q$ ai vertici di un triangolo equilatero di lato $L$.

   **Soluzione.** Il [[Lavoro]] per assemblare le cariche partendo da distanza infinita è l'energia potenziale del sistema; con lato $L$ uguale per tutte le coppie:
   $$W = U = k\frac{q_1q_2+q_1q_3+q_2q_3}{L} = k\frac{2q^2+3q^2+6q^2}{L} = \frac{11kq^2}{L}$$

6. È possibile costruire un [[Condensatore Piano]] di capacità 1 Farad? Spiega, motivando.

   **Soluzione.** In linea di principio sì ($C=\varepsilon_0 A/d$ non ha limiti matematici), ma in pratica no con un [[Condensatore Piano]] "normale": $\varepsilon_0\approx8.85\times10^{-12}$, quindi per $C=1\ F$ con $d=1\ mm$ servirebbe $A=C d/\varepsilon_0 \approx 1.1\times10^8\ m^2$ (oltre 100 km²) — improponibile. Ridurre $d$ non aiuta oltre un certo limite: sotto una certa distanza si ha la **scarica per rottura dielettrica** (scintilla tra le armature). Per questo i condensatori da 1 F reali (i "supercondensatori") non sono piani: usano elettrodi porosi ad altissima area superficiale e un doppio strato elettrico a distanza molecolare, non la geometria piana ideale.

7. Un elettrone è lanciato tra le armature di un condensatore con una [[Energia cinetica]] iniziale di 300 eV.
   a) Quale deve essere la d.d.p. e la polarità delle armature per arrestarlo in prossimità della seconda armatura?
   b) Quale deve essere la d.d.p. e la polarità delle armature perché raddoppi la sua energia?
   c) Quale deve essere la d.d.p. e la polarità delle armature perché raddoppi la sua velocità?

   **Soluzione.** L'elettrone (carica $-e$) è attratto verso l'armatura positiva e respinto da quella negativa: accelera muovendosi verso l'armatura $+$, decelera muovendosi verso l'armatura $-$.

   a) Per fermarlo deve perdere tutta l'[[Energia cinetica]] iniziale: $e\Delta V = 300\ eV \Rightarrow \Delta V = 300\ V$. Deve decelerare, quindi l'armatura di ingresso (da cui parte) è **positiva**, quella di arrivo (dove si ferma) è **negativa**.

   b) Deve raddoppiare l'energia: $K_f = 600\ eV$, guadagno $\Delta K = 300\ eV \Rightarrow \Delta V = 300\ V$. Deve accelerare: armatura di ingresso **negativa**, armatura di arrivo **positiva**.

   c) Se raddoppia la velocità, poiché $K\propto v^2$, l'energia finale è $4\times300 = 1200\ eV$: guadagno $\Delta K = 900\ eV \Rightarrow \Delta V = 900\ V$. Stessa polarità del punto b): ingresso **negativo**, arrivo **positivo**.

8. Determina, utilizzando il [[Teorema di Gauss]], le caratteristiche del [[Campo Elettrico]] generato da un filo rettilineo indefinitamente esteso con distribuzione lineare di carica $\lambda = Q/L$.

   **Soluzione.** Simmetria cilindrica: il campo è radiale (perpendicolare al filo) e ha lo stesso modulo a parità di distanza $r$ dal filo. Superficie gaussiana: cilindro coassiale di raggio $r$ e altezza $h$.
   - Sulle basi $\vec E \perp d\vec A$ → flusso nullo.
   - Sulla superficie laterale $\vec E \parallel d\vec A$ e $E$ costante → flusso $= E\cdot(2\pi r h)$.

   Carica interna: $Q_{int} = \lambda h$. Applicando Gauss:
   $$E\cdot 2\pi r h = \frac{\lambda h}{\varepsilon_0} \;\Rightarrow\; E = \frac{\lambda}{2\pi\varepsilon_0 r}$$
   Il campo è radiale (uscente se $\lambda>0$, entrante se $\lambda<0$), decresce come $1/r$ (non $1/r^2$ come una carica puntiforme, per via della simmetria cilindrica), e diverge per $r\to0$.

```desmos-graph
left=0.1; right=5; top=10; bottom=0; grid=true;
---
y=\frac{1}{2\pi x}
```
