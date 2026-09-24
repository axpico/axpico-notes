## 1. Conversione decimale → binario

**Metodo delle divisioni successive per 2**: dividi il numero per 2, annoti il resto, ripeti sul quoziente finché non arrivi a 0. Le cifre binarie sono i resti letti dal basso verso l'alto (dall'ultimo al primo).

Esempio: 13₁₀ → 2
- 13 ÷ 2 = 6 resto **1**
- 6 ÷ 2 = 3 resto **0**
- 3 ÷ 2 = 1 resto **1**
- 1 ÷ 2 = 0 resto **1**

Leggendo dal basso: 13₁₀ = **1101₂**

**Parte frazionaria**: si moltiplica ripetutamente per 2, si prende la parte intera come cifra, si continua sulla parte frazionaria residua.

Esempio: 0,625₁₀
- 0,625 × 2 = 1,25 → cifra **1**
- 0,25 × 2 = 0,5 → cifra **0**
- 0,5 × 2 = 1,0 → cifra **1**, resto 0 → stop

0,625₁₀ = **0,101₂**

## 2. Conversione binario → decimale

Somma delle potenze di 2 corrispondenti alle cifre a 1, con posizione che parte da 0 a destra della virgola (potenze negative a destra).

1101₂ = 1·2³ + 1·2² + 0·2¹ + 1·2⁰ = 8+4+0+1 = **13₁₀**

0,101₂ = 1·2⁻¹ + 0·2⁻² + 1·2⁻³ = 0,5 + 0 + 0,125 = **0,625₁₀**

## 3. Base 16 (esadecimale)

Sistema posizionale in base 16: 16 simboli (0-9, poi A=10, B=11, C=12, D=13, E=14, F=15). Usato per scrivere in modo compatto i numeri binari, perché **1 cifra esadecimale = esattamente 4 bit** (2⁴=16): la conversione binario↔hex è quindi immediata, cifra per cifra, senza bisogno di passare per il decimale.

**Binario → esadecimale**: raggruppa i bit a 4 a 4 partendo da destra (aggiungendo zeri a sinistra se serve), poi converti ogni gruppo nella cifra hex corrispondente.

Esempio: 1101101₂ → raggruppa: `0110 1101` → **6D₁₆**

**Esadecimale → binario**: operazione inversa, ogni cifra hex diventa un gruppo di 4 bit.

Esempio: A3₁₆ → A=1010, 3=0011 → **10100011₂**

**Decimale → esadecimale**: divisioni successive per 16, stesso procedimento del punto 1 ma con resti da 0 a 15 (10-15 → A-F), letti dal basso.

Esempio: 187₁₀
- 187 ÷ 16 = 11 resto **11 (B)**
- 11 ÷ 16 = 0 resto **11 (B)**

187₁₀ = **BB₁₆**

**Esadecimale → decimale**: somma delle cifre moltiplicate per le potenze di 16 corrispondenti.

BB₁₆ = 11·16¹ + 11·16⁰ = 176+11 = **187₁₀**

## 4. Complemento a 1

Si ottiene invertendo tutti i bit (0↔1) di un numero binario su n bit. È il modo storico di rappresentare i negativi: il bit più significativo (MSB) indica il segno (0 positivo, 1 negativo), gli altri bit vanno complementati per leggere il valore assoluto del negativo.

Esempio (8 bit), −5:
- 5 = 00000101
- complemento a 1 = **11111010**

**Difetto**: esistono due rappresentazioni dello zero (00000000 e 11111111), e le somme richiedono un "riporto circolare" (end-around carry) — scomodo in hardware.

## 5. Complemento a 2

Si ottiene: complemento a 1 + 1. È lo standard usato da tutti i processori moderni per gli interi con segno, perché lo zero è unico e le sottrazioni si riconducono a somme senza correzioni particolari.

Esempio (8 bit), −5:
- 5 = 00000101
- compl. a 1 = 11111010
- +1 → **11111011** = −5 in complemento a 2

**Verifica**: il bit più significativo ha peso negativo. Per 8 bit:
11111011 = −128 + 64+32+16+8+2+1 = −128+123 = **−5** ✓

Range rappresentabile su n bit: da −2^(n−1) a 2^(n−1) − 1 (es. 8 bit: da −128 a +127).

**Per tornare dal complemento a 2 al valore assoluto** del negativo: si ricomplementa (complemento a 1 + 1), operazione involutiva.

## 6. Overflow e underflow

**Overflow** (interi, complemento a 2): si verifica quando il risultato di un'operazione non entra nel numero di bit disponibili, cioè esce dal range rappresentabile [−2^(n−1), 2^(n−1)−1]. Si riconosce facilmente sommando due numeri con lo **stesso segno** e ottenendo un risultato con il **segno opposto**.

Esempio (4 bit, range −8..+7): 5 + 5 = 0101 + 0101 = 1010 = **−6** (risultato assurdo: overflow, perché 10 non entra in 4 bit con segno).

Nota: un riporto (carry) fuori dal bit più significativo non implica overflow (l'hardware lo tollera in aritmetica senza segno); il segnale corretto di overflow nel complemento a 2 è "carry in" ≠ "carry out" sull'ultimo bit, oppure, più semplicemente, il cambio di segno inatteso descritto sopra.

**Overflow e underflow (virgola mobile, IEEE 754)**: qui i due termini hanno un significato diverso, legato all'**esponente**:
- **Overflow**: il risultato è troppo **grande** in modulo per essere rappresentato (l'esponente richiesto supera il massimo codificabile) → il valore diventa **∞** (infinito, rappresentazione speciale IEEE 754).
- **Underflow**: il risultato è troppo **piccolo** in modulo, più vicino a zero di quanto i bit di esponente permettano di rappresentare in forma normalizzata → si perde precisione (numeri "denormalizzati") o il valore collassa a **0**.

In sintesi: negli interi (complemento a 2) esiste solo l'overflow (uscita dal range da un lato o dall'altro); in virgola mobile overflow e underflow sono i due lati opposti del range dinamico dell'esponente (troppo grande / troppo vicino a zero).

## 7. Codice ASCII

Standard che associa a ciascun carattere (lettere, cifre, simboli, comandi di controllo) un numero intero su 7 bit (0–127), poi tipicamente memorizzato su un byte (8 bit, con bit più significativo a 0 nell'ASCII standard).

Esempi utili da ricordare:
- cifre '0'–'9' → 48–57 (codice = 48 + valore numerico)
- lettere maiuscole 'A'–'Z' → 65–90
- lettere minuscole 'a'–'z' → 97–122 (= maiuscola + 32)
- caratteri di controllo (0–31): es. CR=13, LF=10, ESC=27

Per convertire un carattere: si cerca il suo codice nella tabella ASCII e si converte quel numero in binario con il metodo del punto 1.

## 8. Rappresentazione in virgola fissa

Il numero binario ha un punto (virgola) implicito in una posizione **fissa e prestabilita**: n bit per la parte intera, m bit per la parte frazionaria, decisi a priori dal formato.

Esempio: formato Q4.4 (4 bit interi, 4 frazionari) su 8 bit: `0011.1010` = 3 + 0,625 = 3,625.

**Vantaggi**: aritmetica semplice ed efficiente (uguale a quella degli interi, spostando solo l'interpretazione).
**Limiti**: range e precisione fissi e limitati — non adatta a numeri molto grandi e molto piccoli insieme.

## 9. Rappresentazione in virgola mobile (floating point, standard IEEE 754)

Il numero è rappresentato come:

**valore = (−1)^segno × 1,mantissa × 2^(esponente − bias)**

Tre campi (formato singola precisione, 32 bit):
- **1 bit di segno** (S)
- **8 bit di esponente** (E), con bias = 127 (per compensare il fatto che l'esponente è memorizzato senza segno)
- **23 bit di mantissa** (M), con "1" implicito non memorizzato (notazione normalizzata)

Esempio, convertire 13,625₁₀:
1. Binario: 13,625 = 1101,101₂
2. Normalizza: 1,101101 × 2³
3. Segno S=0; Esponente E = 3+127 = 130 = 10000010₂; Mantissa M = 101101000...0 (23 bit, dopo l'1 implicito)
4. Rappresentazione: `0 10000010 10110100000000000000000`

**Vantaggio** rispetto alla virgola fissa: range dinamico enorme (numeri molto grandi e molto piccoli) mantenendo un numero fisso di cifre significative — a costo di precisione variabile e di arrotondamenti (errori di rappresentazione tipici del floating point).

## 10. Indirizzo MAC (Media Access Control)

Identificatore fisico a **48 bit (6 byte)** assegnato a un'interfaccia di rete (scheda Ethernet, Wi-Fi), scritto convenzionalmente come **12 cifre esadecimali** raggruppate a coppie separate da `:` o `-`.

Esempio: `3C:22:FB:A1:9E:07`

Struttura:
- **primi 3 byte (24 bit)** = **OUI** (Organizationally Unique Identifier), assegnato dall'IEEE al produttore della scheda di rete (es. Apple, Intel, ecc.)
- **ultimi 3 byte (24 bit)** = identificatore univoco assegnato dal produttore a quella specifica interfaccia

Ogni byte è quindi convertibile in binario con lo stesso metodo del punto 1: un esadecimale si converte a gruppi di 4 bit (1 cifra hex = 4 bit), es. `3C` = 0011 1100₂.

Due bit del primo byte (i due meno significativi, letti da destra) hanno significato speciale:
- **bit U/L** (Universal/Local, secondo bit da destra): 0 = indirizzo assegnato globalmente dall'IEEE, 1 = indirizzo modificato/assegnato localmente
- **bit I/G** (Individual/Group, bit meno significativo): 0 = indirizzo unicast (una singola interfaccia), 1 = indirizzo multicast/broadcast (es. `FF:FF:FF:FF:FF:FF` è il broadcast Ethernet)

A differenza dell'indirizzo IP (livello di rete, logico e può cambiare), il MAC address è un identificatore di **livello 2 (data link)** del modello OSI, tipicamente fisso e "cablato" nella scheda di rete (anche se oggi molti sistemi operativi lo randomizzano per privacy).
