---
tags:
  - fisica
  - dinamica
  - meccanica
  - leggi-di-newton
  - piano-inclinato
  - attrito
  - forza-elastica
  - esercizi
subject: Fisica
type: appunti
date: 2026-09-01
---

# Dinamica — Ripasso

> Vedi anche [[claude_skills/Skill Desmos for obsidian.md|Skill Desmos]] per come inserire i grafici in questa nota (plugin community "Desmos" di Nigecat richiesto).

## 1. I tre principi della dinamica (leggi di Newton)

### Primo principio — principio d'inerzia
$$\sum \vec F = 0 \;\Rightarrow\; \vec a = 0$$
Se la risultante delle forze esterne su un corpo è nulla, il corpo mantiene il suo stato di quiete o di moto rettilineo uniforme. Vale solo nei sistemi di riferimento **inerziali**. "Nessuna accelerazione" non vuol dire "nessuna forza": vuol dire che le forze si bilanciano.

### Secondo principio — legge fondamentale della dinamica
$$\sum \vec F = m\,\vec a$$
L'accelerazione è direttamente proporzionale alla risultante delle forze applicate e ha la sua stessa direzione/verso; la costante di proporzionalità inversa è la massa inerziale $m$. È la legge che si usa per **risolvere** i problemi: si scrive $\sum F$ su ogni asse utile e si isola l'incognita.

### Terzo principio — principio di azione e reazione
$$\vec F_{1,2} = -\vec F_{2,1}$$
Se il corpo 1 esercita una forza sul corpo 2, il corpo 2 esercita sul corpo 1 una forza uguale in modulo e direzione, verso opposto. Attenzione: agiscono su **due corpi diversi**, quindi non vanno mai sommate nel bilancio delle forze su un singolo corpo (altrimenti si annullerebbe sempre tutto).

## 2. Piano inclinato: quando seno e quando coseno

Su un piano inclinato di angolo $\theta$ rispetto all'orizzontale, il peso $m\vec g$ (sempre verticale) si scompone in due componenti rispetto agli assi del piano:

- **parallela al piano** (quella che fa scivolare): $F_\parallel = mg\sin\theta$
- **perpendicolare al piano** (quella bilanciata dalla normale): $F_\perp = mg\cos\theta \Rightarrow N = mg\cos\theta$ (se non ci sono altre forze con componente verticale/normale)

**Trucco per non sbagliare seno/coseno:** controlla i casi limite.
- $\theta \to 0°$ (piano quasi piatto): niente deve far scivolare $\Rightarrow \sin 0°=0$ conferma che la parallela usa il seno; tutto il peso è sostenuto dal piano $\Rightarrow \cos 0°=1$ conferma che la normale usa il coseno.
- $\theta \to 90°$ (piano verticale): tutto il peso "cade" $\Rightarrow \sin 90°=1$; il piano non sostiene più nulla $\Rightarrow \cos 90°=0$.

Regola pratica: **seno → componente lungo il piano**, **coseno → componente lungo la normale**, sempre riferiti all'angolo di inclinazione $\theta$ misurato dall'orizzontale. Se una forza è applicata in una direzione diversa (es. orizzontale, come nell'Esercizio 3), va scomposta anch'essa con lo stesso ragionamento rispetto agli stessi assi.

## 3. Forza d'attrito radente

- **Attrito statico**: si oppone al tentativo di mettere in moto un corpo fermo, si "adatta" fino a un massimo:
$$F_{s} \le \mu_s N$$
Il corpo inizia a muoversi solo quando la forza motrice supera $F_{s,max}=\mu_s N$.

- **Attrito dinamico (cinetico)**: agisce quando il corpo è già in moto relativo rispetto alla superficie, ha modulo (circa) costante e verso opposto al moto:
$$F_d = \mu_d N$$
di solito $\mu_d \le \mu_s$.

- **Relazione con la normale**: l'attrito è sempre proporzionale a $N$, la forza che le due superfici si scambiano perpendicolarmente — **non** al peso in generale. Su piano orizzontale $N=mg$; su piano inclinato $N=mg\cos\theta$; se c'è una forza esterna con componente perpendicolare al piano, va inclusa nel bilancio di $N$ (vedi Esercizio 3c).

## 4. Forza elastica (legge di Hooke)

$$\vec F = -k\,\vec x$$
$k$ = costante elastica della molla [N/m], $x$ = allungamento/compressione rispetto alla lunghezza di riposo. Il segno meno indica che è una forza di **richiamo**, sempre diretta verso la posizione di riposo. Nei bilanci di equilibrio spesso si usa solo il modulo $F=kx$.

```desmos-graph
left=-0.2; right=0.2;
top=400; bottom=-400;
---
y=-1730x
```
*(esempio: molla con $k=1730\,N/m$ come nell'Esercizio 2 — l'asse x è l'allungamento in metri, l'asse y la forza in N)*

---

## 5. Esercizi II incontro

> Assunzione usata in tutti i calcoli: $g = 9.8\ m/s^2$.

### Esercizio 1
$m=10\,kg$, carico di rottura fune $F_C=70\,N$.

Peso: $P = mg = 10 \times 9.8 = 98\,N$.

**a)** Per calarla a velocità costante servirebbe $T=P=98\,N > F_C=70\,N$ → **no**, la fune si romperebbe.

**b)** Occorre farla scendere con un'accelerazione (verso il basso) tale che la tensione richiesta scenda a $F_C$. Preso il basso come verso positivo:
$$mg - T = ma \;\Rightarrow\; T = m(g-a)$$
Imponendo $T \le F_C$:
$$a \ge g - \frac{F_C}{m} = 9.8 - \frac{70}{10} = 2.8\ m/s^2$$
$$\boxed{a_{min} = 2.8\ m/s^2}$$

### Esercizio 2
$m=20\,kg$, $k=1730\,N/m$, angoli $\alpha=60°$ (molla) e $\beta=30°$ (fune) rispetto al soffitto (orizzontale), sui due lati opposti rispetto alla verticale del corpo appeso. Poiché $\alpha+\beta=90°$, molla e fune sono tra loro perpendicolari.

Equilibrio orizzontale e verticale (molla tira da un lato, fune dall'altro):
$$F_{molla}\cos\alpha = T\cos\beta \qquad F_{molla}\sin\alpha + T\sin\beta = mg$$
Risolvendo il sistema:
$$T = \frac{mg}{\cos\beta\tan\alpha+\sin\beta} = \frac{mg}{\frac{\sqrt3}{2}\sqrt3+\frac12}=\frac{mg}{2}$$
$$F_{molla} = \frac{T\cos\beta}{\cos\alpha} = \frac{\sqrt3}{2}\,mg$$

Con $mg = 196\,N$:
$$\boxed{T = 98\ N} \qquad \boxed{F_{molla} \approx 169.7\ N}$$
Allungamento della molla:
$$x = \frac{F_{molla}}{k} = \frac{169.7}{1730} \approx 0.098\ m \approx 9.8\ cm$$

### Esercizio 3
$m=8\,kg$, piano liscio inclinato $\theta=20°$, forza $F$ **orizzontale** (non parallela al piano!) che spinge verso l'alto.

Scomponendo $F$ e il peso lungo il piano: componente utile di $F$ lungo il piano $=F\cos\theta$; componente di $F$ perpendicolare al piano (schiaccia contro il piano) $=F\sin\theta$, quindi $N = mg\cos\theta + F\sin\theta$.

**a) moto uniforme ($a=0$, senza attrito):**
$$F\cos\theta = mg\sin\theta \;\Rightarrow\; F = mg\tan\theta = 8\times9.8\times\tan20° \approx \boxed{28.5\ N}$$

**b) $a=0.2\ m/s^2$ (senza attrito):**
$$F\cos\theta - mg\sin\theta = ma \;\Rightarrow\; F=\frac{ma+mg\sin\theta}{\cos\theta}=\frac{1.6+26.8}{0.940}\approx\boxed{30.2\ N}$$

**c) moto uniforme con attrito $\mu=0.2$** ($N = mg\cos\theta+F\sin\theta$, attrito verso il basso del piano perché il moto è verso l'alto):
$$F\cos\theta - mg\sin\theta - \mu(mg\cos\theta+F\sin\theta)=0$$
$$F = \frac{mg(\sin\theta+\mu\cos\theta)}{\cos\theta-\mu\sin\theta} = \frac{78.4\times0.530}{0.871}\approx\boxed{47.7\ N}$$

### Esercizio 4 — Macchina di Atwood
$m_1=0.1\,kg$, $m_2=0.2\,kg$, filo ideale su carrucola ideale.

Per $m_2$ (scende) e $m_1$ (sale), stesso modulo di accelerazione $a$ e stessa tensione $T$:
$$m_2 g - T = m_2 a \qquad T - m_1 g = m_1 a$$
Sommando le due equazioni:
$$a = \frac{(m_2-m_1)g}{m_1+m_2} = \frac{0.1\times9.8}{0.3} \approx \boxed{3.27\ m/s^2}$$
$$T = m_1(g+a) = 0.1\times(9.8+3.27) \approx \boxed{1.31\ N}$$
*(verifica: $m_2(g-a)=0.2\times6.53\approx1.31\,N$ ✓)*

### Esercizio 5 — Centro di massa
⚠️ Manca la figura con la disposizione dei mattoncini: non posso ricavare un numero senza sapere quanti sono e come sono impilati/allineati. Metodo generale una volta note le coordinate $(x_i,y_i)$ del centro di ciascun mattoncino (ognuno di massa $m$, lati $L$ e $L/2$):
$$x_{cm} = \frac{\sum_i m_i x_i}{\sum_i m_i} \qquad y_{cm} = \frac{\sum_i m_i y_i}{\sum_i m_i}$$
Se mi descrivi/allghi la figura (posizione di ogni mattoncino rispetto all'origine) calcolo subito il valore numerico.

### Esercizio 6 — Forza in funzione del tempo
⚠️ Manca il grafico $F(t)$: senza i valori di forza e durata non posso integrare. Metodo generale — [[Teorema dell'impulso]]:
$$\Delta \vec v = \frac{1}{m}\int_0^t \vec F\,dt' = \frac{\text{area sotto il grafico } F\text{-}t}{m}$$
Con $m=1\,kg$ e $v_0=2\,m/s$: calcola l'area sotto la curva fino a ciascun istante ($t=3,4,5\,s$), dividi per $m$, sommala (con segno, secondo la direzione della forza) a $v_0$. Dammi i valori/la forma del grafico e lo risolvo numericamente.

### Esercizio 7 — Oscillatore, grafico posizione-tempo
⚠️ Manca il grafico $x(t)$ della molla. Metodo generale, $m=4\,kg$:
- La forza elastica è $F=-kx$ (o $F=ma=-m\omega^2 x$): è **massima** dove lo spostamento dalla posizione di equilibrio è **massimo** (ai picchi/valli del grafico, cioè agli estremi dell'oscillazione, dove anche l'accelerazione è massima).
- È **nulla** dove il grafico attraversa la posizione di equilibrio (velocità massima lì, spostamento nullo).
- Il valore massimo si ottiene da $F_{max}=m\omega^2 A$, con $A$ = ampiezza letta sul grafico e $\omega=2\pi/T_{osc}$ ($T_{osc}$ = periodo letto sul grafico).
Con i valori numerici del grafico (ampiezza e periodo) applico la formula.

### Esercizio 8 — Piano inclinato con attrito e massa appesa
Assumo la configurazione standard: $m_A$ su un [[Piano inclinato]] scabro (angolo $\alpha$), collegata tramite fune e carrucola ideali a una massa $m_B$ appesa verticalmente. $m_A=0.5\,kg$, $\alpha=20°$, $\mu_s=0.3$.

Il sistema resta **fermo** finché l'[[Attrito statico]] riesce a compensare lo squilibrio tra $m_B g$ e la componente del peso di $A$ lungo il piano, $m_Ag\sin\alpha$. I due casi limite:

- **$m_B$ troppo piccola** → $A$ tende a scivolare verso il basso, attrito verso l'alto del piano:
$$m_A g\sin\alpha = m_{B,min}\,g + \mu_s m_A g\cos\alpha$$
$$m_{B,min} = m_A(\sin\alpha-\mu_s\cos\alpha) = 0.5\times(0.342-0.282)\approx\boxed{0.030\ kg\ (30\ g)}$$

- **$m_B$ troppo grande** → $A$ tende a salire, attrito verso il basso del piano:
$$m_{B,max}\,g = m_Ag\sin\alpha + \mu_s m_A g\cos\alpha$$
$$m_{B,max} = m_A(\sin\alpha+\mu_s\cos\alpha) = 0.5\times(0.342+0.282)\approx\boxed{0.312\ kg\ (312\ g)}$$

Il sistema **si mette in movimento** per $m_B < 30\,g$ (A scivola giù) oppure $m_B > 312\,g$ (B scende, A sale); resta fermo per $30\,g \le m_B \le 312\,g$.

### Esercizio 9 — Disco su Air Hockey
$m=0.2\,kg$, $\vec F_1=(2,3)$, $\vec F_2=(4,-6)$, $\vec F_3=(-5,0)$ N, nessun attrito.

Risultante:
$$F_x = 2+4-5=1\ N \qquad F_y = 3-6+0=-3\ N$$
$$|\vec F| = \sqrt{1^2+3^2}=\sqrt{10}\approx3.16\ N$$
$$a = \frac{|\vec F|}{m} = \frac{3.16}{0.2}\approx\boxed{15.8\ m/s^2}$$
Angolo rispetto all'asse x: $\theta=\arctan\!\left(\frac{-3}{1}\right)\approx\boxed{-71.6°}$ (cioè 71.6° sotto l'asse x, quarto quadrante).

```desmos-graph
left=-8; right=8;
top=8; bottom=-8;
width=400; height=400;
---
y=\frac{3}{2}x\left\{0\le x\le2\right\}|label:F_1
y=-\frac{3}{2}x\left\{0\le x\le4\right\}|label:F_2
y=0\left\{-5\le x\le0\right\}|label:F_3
y=-3x\left\{0\le x\le1\right\}|label:Risultante
```
