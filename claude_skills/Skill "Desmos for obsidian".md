---

## name: obsidian-desmos description: Usa questa skill quando devi inserire, modificare o correggere grafici Desmos in note Obsidian (file .md) tramite il plugin "Desmos" (Nigecat/obsidian-desmos). Attivala per richieste tipo "aggiungi un grafico a questa nota", "graficami questa funzione in Obsidian", "correggi questo blocco desmos-graph", o quando nel file .md compare/deve comparire un blocco `desmos-graph`.

# Plugin Desmos per Obsidian

Il plugin renderizza grafici Desmos interattivi (statici nel export) direttamente dentro le note Obsidian, tramite blocchi di codice con linguaggio `desmos-graph` (2D) o `desmos-graph-3d` (3D, richiede il plugin separato `obsidian-desmos-3d`).

## Sintassi base

Blocco minimo — solo equazioni in formato LaTeX:

````markdown
```desmos-graph
y=x
```
````

Più equazioni, una per riga:

````markdown
```desmos-graph
y=\sin(x)
y=\frac{1}{x}
```
````

## Struttura con impostazioni

Il blocco è diviso in due sezioni separate da `---`:

- **sopra**: impostazioni (opzionali), coppie `chiave=valore` separate da newline o `;`
- **sotto**: equazioni/punti in LaTeX

````markdown
```desmos-graph
left=0; right=100;
top=10; bottom=-10;
---
y=\sin(x)
```
````

### Impostazioni disponibili

|Chiave|Descrizione|
|---|---|
|`left`, `right`, `top`, `bottom`|Limiti degli assi (bounds del grafico)|
|`width`, `height`|Dimensioni in px dell'immagine renderizzata|
|`grid`|`true`/`false` — mostra/nasconde la griglia|
|`degreeMode`|`radians` (default) o `degrees` — modalità trigonometrica|

**Regola importante (parser doppio):** le impostazioni sopra il `---` usano sintassi matematica semplice (mathjs, es. `x^0.5`), mentre le equazioni/punti sotto il `---` richiedono LaTeX vero e proprio (es. `\pi`, `\sqrt{x}`, `\frac{a}{b}`). Non mischiare le due sintassi tra le due sezioni.

## Punti e etichette

I punti si scrivono come coordinate, con flag opzionali separati da `|`:

````markdown
```desmos-graph
(0,0)|label:(0,0)
(5,4)|open|label:This is a label
```
````

- `label:<testo>` — aggiunge un'etichetta (funziona solo sui punti, **non** sulle equazioni)
- `open` — rende il punto "aperto" (cerchio vuoto) invece che pieno

## Nascondere equazioni

Utile per grafici di derivate/costruzioni ausiliarie che non vuoi visualizzare ma che servono al calcolo:

````markdown
```desmos-graph
y=x^2
y=2x|hidden
```
````

## Grafici 3D (plugin separato)

Se è installato anche `obsidian-desmos-3d`, si usa lo stesso schema ma con linguaggio `desmos-graph-3d`:

````markdown
```desmos-graph-3d
z=x^2+y^2
```
````

## CSS

Tutti i grafici hanno la classe `.desmos-graph`, utile per snippet CSS custom (es. centrare il grafico nella pagina):

```css
.desmos-graph {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
```

## Checklist quando generi un blocco per l'utente

1. Le equazioni vanno **sempre** in LaTeX (`\sin`, `\frac{}{}`, `\sqrt{}`, `\pi`, ecc.), mai in notazione Python/mathjs.
2. Se servono bound custom (utile per grafici fisici — es. moto in un intervallo di tempo specifico), aggiungi la sezione impostazioni con `---`.
3. Per fisica, imposta `degreeMode=radians` esplicitamente solo se l'utente lavora in gradi (`degrees`) — di default è già radianti, coerente con le formule fisiche standard.
4. Se il grafico contiene più curve da confrontare (es. posizione vs velocità vs accelerazione), mettile come equazioni separate nello stesso blocco, una per riga.
5. Verifica che il plugin sia installato (community plugin "Desmos" di Nigecat) prima di assumere che il rendering funzioni — se l'utente lamenta che il blocco non si renderizza, il problema è quasi sempre plugin non installato/non abilitato, non sintassi.

## Fonte

Documentazione ufficiale: https://github.com/Nigecat/obsidian-desmos (README)