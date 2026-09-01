## A) Condizioni necessarie e sufficienti
### 1. Quadrilateri — relazioni tra proprietà degli angoli

Dato un quadrilatero convesso $Q$ (angoli interni in $(0°,180°)$, somma $=360°$):

- **(a)** $Q$ ha un angolo ottuso (un angolo tra $90°$ e $180°$)
- **(b)** $Q$ ha tre angoli acuti (almeno tre angoli $<90°$)
- **(c)** $Q$ non ha angoli retti (nessun angolo $=90°$)

#### Analisi

> [!success] (b) ⇒ (c)
> Se tre angoli sono acuti, la loro somma è $<270°$ (ciascuno $<90°$), quindi il quarto angolo è $>90°$: non può essere retto. Anche i tre angoli acuti, per definizione, non sono retti ⇒ vale (c).
> *Sempre vera, senza bisogno dell'ipotesi di convessità.*

> [!success] (b) ⇒ (a)
> Il quarto angolo è $>90°$ e, per convessità, $<180°$: è quindi ottuso ⇒ vale (a).
> *(Con quadrilateri concavi il quarto angolo potrebbe essere rientrante, $>180°$, non ottuso: qui serve la convessità.)*

> [!success] (c) ⇒ (a)
> La somma dei quattro angoli è $360°$, quindi non possono essere tutti $<90°$ (altrimenti la somma sarebbe $<360°$): almeno un angolo è $\ge 90°$. Se vale (c), quell'angolo non è $=90°$, dunque è $>90°$ e, per convessità, $<180°$: è ottuso ⇒ vale (a).

> [!failure] (a) ⇏ (b) e (a) ⇏ (c)
> Un solo angolo ottuso non basta a garantire né tre angoli acuti né l'assenza di angoli retti.
> - Controesempio a (a) ⇏ (b): $100°,100°,80°,80°$ — (a) vera, ma solo due angoli acuti.
> - Controesempio a (a) ⇏ (c): $100°,90°,85°,85°$ — (a) vera, ma c'è un angolo retto (falsa (c)).

> [!failure] (c) ⇏ (b)
> Nessun angolo retto non implica tre angoli acuti.
> - Controesempio: $91°,91°,89°,89°$ — (c) vera, ma solo due angoli acuti.

#### Conclusione

$$\text{(b)} \Rightarrow \text{(c)} \Rightarrow \text{(a)}$$

Nessuna implicazione si inverte. (b) è l'ipotesi più forte, (a) la più debole; (a) e (c) non sono equivalenti, e (a)∧(c) non basta a garantire (b) — es. $100°,95°,100°,65°$: ottuso presente, nessun retto, ma un solo angolo acuto.

---

### 2. Triangoli isosceli

Un triangolo è isoscele se ha (almeno) due lati uguali, equivalentemente (almeno) due angoli uguali. Quali delle seguenti condizioni sono **necessarie**, quali **sufficienti**?

| # | Condizione | Necessaria | Sufficiente |
|---|---|:---:|:---:|
| (a) | T è equilatero | no | sì |
| (b) | T ha due angoli uguali | **sì** | **sì** |
| (c) | T è rettangolo | no | no |
| (d) | T ha due angoli uguali e di ampiezza $<60°$ | no | sì |
| (e) | Esistono due lati il cui quoziente è un intero | sì | no |

**(a) T è equilatero — sufficiente, non necessaria.**
Equilatero ⇒ isoscele (l'equilatero è un caso particolare, con tutti e tre i lati uguali). Ma un isoscele non equilatero (es. lati $5,5,3$) resta isoscele: quindi non è necessaria.

**(b) T ha due angoli uguali — necessaria e sufficiente** (condizione equivalente).
Isoscele ⇒ i due angoli opposti ai lati uguali sono uguali (teorema del triangolo isoscele) ⇒ necessaria. Viceversa, due angoli uguali ⇒ i lati opposti sono uguali (teorema inverso) ⇒ T è isoscele ⇒ sufficiente.

**(c) T è rettangolo — né necessaria né sufficiente.**
Un isoscele non è per forza rettangolo (es. equilatero, angoli tutti $60°$). Un rettangolo non è per forza isoscele (es. $3,4,5$, scaleno).

**(d) T ha due angoli uguali e di ampiezza $<60°$ — sufficiente, non necessaria.**
È un caso particolare di (b), quindi sufficiente. Non necessaria: un isoscele può avere i due angoli uguali $>60°$, es. $70°,70°,40°$ — isoscele, ma gli angoli uguali non sono $<60°$.

**(e) Esistono due lati il cui quoziente è un intero — necessaria, non sufficiente.**
Necessaria: se T è isoscele, i due lati uguali hanno quoziente $=1$ (intero) ⇒ vale (e). Non sufficiente: controesempio $2,4,5$ (triangolo valido, $4/2=2$ intero) ma scaleno, non isoscele.


## B)  Connettivi logici

