---
date: 2026-09-01
subject: matematica
topic: logica e aritmetica
tags:
  - matematica
  - logica
  - condizioni-necessarie-sufficienti
  - connettivi-logici
---
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


## B) Connettivi logici

### 1. "Sono bello e ricco" — negazione di una congiunzione

Lui afferma $P \land Q$ (bello **e** ricco). Lei nega: $\lnot(P \land Q)$.

Per De Morgan: $\lnot(P \land Q) \equiv \lnot P \lor \lnot Q$ — cioè **brutto o povero, eventualmente entrambi** (l'"o" logico è inclusivo).

> [!success] Risposta: (c)
> (a) negherebbe una congiunzione con un'altra congiunzione ($\lnot P \land \lnot Q$): troppo forte, non è ciò che dice "non è vero che...".
> (b) è l'"o esclusivo" (aut aut): esclude il caso "entrambi", che invece la negazione logica ammette.
> (d) non c'entra: la frase nega solo il contenuto dell'affermazione, non parla di amore.

---

### 2. Negazione di affermazioni (quantificatori e connettivi)

Regole usate: $\lnot\exists \equiv \forall\lnot$, $\lnot\forall \equiv \exists\lnot$, De Morgan ($\lnot(A\land B)\equiv \lnot A \lor \lnot B$, $\lnot(A\lor B)\equiv \lnot A \land \lnot B$).

**(a)** "Esiste un punto che non appartiene alla retta $r$, né alla retta $s$."
$\exists x:\ x\notin r \land x\notin s$ → negazione: $\forall x:\ x\in r \lor x\in s$
> **Ogni punto appartiene alla retta $r$ o alla retta $s$ (o a entrambe).**

**(b)** "Per ogni numero reale $x$ si ha $f(x)\ge 5$."
$\forall x:\ f(x)\ge 5$ → negazione: $\exists x:\ f(x) < 5$
> **Esiste un numero reale $x$ per cui $f(x) < 5$.**

**(c)** "Esiste una circonferenza tangente alle rette $r$ ed $s$, ma non alla retta $q$."
$\exists c:\ \tan(c,r) \land \tan(c,s) \land \lnot\tan(c,q)$ → negazione: $\forall c:\ \lnot\tan(c,r) \lor \lnot\tan(c,s) \lor \tan(c,q)$
> **Ogni circonferenza tangente sia a $r$ sia a $s$ è tangente anche a $q$** (ossia: nessuna circonferenza è tangente a $r$ e $s$ senza esserlo anche a $q$).

**(d)** "Il quadrilatero $Q$ e il pentagono $P$ hanno almeno due vertici in comune."
$|V(Q)\cap V(P)| \ge 2$ → negazione: $|V(Q)\cap V(P)| \le 1$
> **$Q$ e $P$ hanno al più un vertice in comune** (nessuno o esattamente uno).

**(e)** "Il numero $p$ è primo, dispari e minore di 10."
$\text{primo} \land \text{dispari} \land p<10$ → negazione (De Morgan): $\lnot\text{primo} \lor \text{pari} \lor p\ge 10$
> **$p$ non è primo, oppure è pari, oppure è maggiore o uguale a 10** (basta che *una sola* delle tre condizioni cada).

**(f)** "L'equazione $a(x)=0$ ha esattamente tre soluzioni reali."
→ negazione: **l'equazione $a(x)=0$ ha un numero di soluzioni reali diverso da tre** (cioè 0, 1, 2, pure 4 o più).

> [!tip] Schema generale
> Negare "esattamente $n$" non vuol dire "nessuna" o "infinite": vuol dire semplicemente "$\ne n$". È un errore comune trasformare la negazione in un'affermazione più forte di quanto serva — regola valida anche per (a)-(e): negare una congiunzione dà un'**disgiunzione** (De Morgan), non un'altra congiunzione.
## C) Divisibilità

### 1. Somma di 3 numeri consecutivi divisibile per 3

$$n + (n+1) + (n+2) = 3n + 3 = 3(n+1)$$

> [!success] Divisibile per 3
> La somma è $3(n+1)$, multiplo di 3 per ogni $n \in \mathbb{N}$: la divisibilità è immediata dalla fattorizzazione, non serve altro.

---

### 2. $N_n = n^5 - n$ divisibile per 5, $n \in \mathbb{N}$

$$n^5 - n = n(n^4-1) = n(n^2-1)(n^2+1) = (n-2)(n-1)n(n+1)(n+2) + 5n(n^2-1)$$

> [!success] Divisibile per 5
> - $(n-2)(n-1)n(n+1)(n+2)$ è un prodotto di 5 interi consecutivi: tra essi ce n'è sempre uno multiplo di 5.
> - $5n(n^2-1)$ è multiplo di 5 per costruzione.
>
> Somma di due multipli di 5 → $N_n$ è multiplo di 5 per ogni $n \in \mathbb{N}$.
>
> *(Alternativa più rapida: per il piccolo teorema di Fermat, $n^5 \equiv n \pmod 5$ per ogni $n$, quindi $n^5-n\equiv 0$.)*

