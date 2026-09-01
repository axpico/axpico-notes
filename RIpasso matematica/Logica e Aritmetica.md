# Logica e Aritmetica

## Esercizio: implicazioni tra proprietà di un quadrilatero

Dato un quadrilatero convesso $Q$ (angoli interni in $(0°,180°)$, somma $=360°$), consideriamo:

- **(a)** $Q$ ha un angolo ottuso (un angolo tra $90°$ e $180°$)
- **(b)** $Q$ ha tre angoli acuti (almeno tre angoli $<90°$)
- **(c)** $Q$ non ha angoli retti (nessun angolo $=90°$)

### Analisi

**(b) ⇒ (c).** Se tre angoli sono acuti, la loro somma è $<270°$ (ciascuno $<90°$), quindi il quarto angolo è $>90°$: non può quindi essere retto. Anche i tre angoli acuti, per definizione, non sono retti. Nessun angolo è retto ⇒ vale (c). *Sempre vera, senza bisogno dell'ipotesi di convessità.*

**(b) ⇒ (a).** Dallo stesso ragionamento: il quarto angolo è $>90°$, e per convessità è $<180°$, quindi è ottuso ⇒ vale (a). *(Se si ammettono quadrilateri concavi, il quarto angolo potrebbe essere un angolo rientrante $>180°$, non ottuso: qui serve l'ipotesi di convessità.)*

**(c) ⇒ (a).** Poiché la somma dei quattro angoli è $360°$, non possono essere tutti $<90°$ (altrimenti la somma sarebbe $<360°$): almeno un angolo è $\ge 90°$. Se (c) vale, quell'angolo non è $=90°$, quindi è $>90°$, e per convessità $<180°$: è ottuso ⇒ vale (a).

**(a) ⇏ (b) e (a) ⇏ (c).** Un solo angolo ottuso non basta a garantire né tre angoli acuti né l'assenza di angoli retti.
- Controesempio a (a) ⇏ (b): $100°,100°,80°,80°$ — (a) vera, ma solo due angoli acuti.
- Controesempio a (a) ⇏ (c): $100°,90°,85°,85°$ — (a) vera, ma c'è un angolo retto (falsa (c)).

**(c) ⇏ (b).** Niente angoli retti non implica tre angoli acuti.
- Controesempio: $91°,91°,89°,89°$ — (c) vera, ma solo due angoli acuti.

### Conclusione

$$\text{(b)} \Rightarrow \text{(c)} \Rightarrow \text{(a)}$$

nessuna delle implicazioni si inverte. (b) è l'ipotesi più forte, (a) la più debole; (a) e (c) non sono equivalenti, e (a)∧(c) non basta a garantire (b) (es.: $100°,95°,100°,65°$: ottuso presente, nessun retto, ma un solo angolo acuto).
