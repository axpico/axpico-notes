---

## name: obsidian-advanced-canvas description: Usa questa skill quando devi creare, modificare o correggere Canvas Obsidian (.canvas) sfruttando le funzionalità del plugin community "Advanced Canvas" (Developer-Mike/obsidian-advanced-canvas). Attivala per richieste tipo "creami un canvas/flowchart", "aggiungi una presentazione al canvas", "collega questi nodi con una freccia tratteggiata", "esporta il canvas come immagine", "crea un portal/gruppo collassabile", o quando nel vault compare/deve comparire un file `.canvas` con nodi, edge, gruppi, template, frontmatter o stili avanzati.

# Plugin Advanced Canvas per Obsidian

Potenzia il Canvas nativo di Obsidian (formato JSON Canvas) con: frontmatter, integrazione nel grafo/backlink, forme flowchart, stili edge, modalità presentazione, portals, gruppi collassabili, export immagine avanzato e altro. Repo: [Developer-Mike/obsidian-advanced-canvas](https://github.com/Developer-Mike/obsidian-advanced-canvas) (plugin id community: `advanced-canvas`).

## Concetti chiave

- **Nodo**: elemento del canvas (testo, file, gruppo, link).
- **Edge**: connessione tra due nodi (non "freccia" per evitare confusione con l'arrow-head).
- **Il file `.canvas` è JSON puro** — non va editato a mano se non necessario; preferisci sempre l'UI o istruzioni per l'utente, a meno che venga chiesto esplicitamente di generare/patchare il JSON.

## Frontmatter nel canvas

Il plugin abilita proprietà YAML anche nei file `.canvas`, accessibili dall'icona "info" in alto a destra nella vista canvas. Usi tipici: `tags`, `aliases`, `cssclasses` (per styling custom della vista).

## Edge automatici da frontmatter

Se una nota ha la proprietà `canvas-edges` con link ad altri file, Advanced Canvas crea automaticamente gli edge tra i corrispondenti nodi file nel canvas.

## Link ed embed di un singolo nodo

Sintassi wikilink standard con l'ID del nodo dopo `#` (ottieni l'ID con il comando *Advanced Canvas: Copy wikilink to node*):

```
[[nome-canvas#id-nodo]]    ← link
![[nome-canvas#id-nodo]]   ← embed del contenuto del nodo
```

## Forme dei nodi (flowchart)

Dal popup menu (nodo selezionato) si imposta la forma: Terminal, Process, Decision, Input/Output, On-page Reference, Predefined Process, Document, Database.

## Stili di bordo e testo

- Bordo: `dotted` (puntinato), `dashed` (tratteggiato), `invisible`.
- Allineamento testo: sinistra, centro, destra.

## Stili degli edge

- **Path style**: dotted, short-dashed, long-dashed.
- **Arrow style**: triangle outline, halved triangle, thin triangle, diamond, diamond outline, circle, circle outline, blunted.
- **Pathfinding**: default, straight, squared, A*.
- **Floating edges**: l'edge sceglie automaticamente il lato di aggancio più adatto (trascina verso la drop zone interna al nodo).
- **Flip edge**: inverte la direzione con un click dal popup menu.

## Modalità presentazione

1. Marca il primo nodo come slide iniziale (popup menu o card menu).
2. Collega le slide successive con edge; se un nodo ha più edge in uscita, numerale per definire l'ordine di navigazione.
3. Comandi: *Advanced Canvas: Start presentation* (avvio), `ESC` (esci), *Advanced Canvas: Continue presentation* (riprendi dall'ultima slide), frecce/PageUp/PageDown per navigare (compatibile con telecomandi).
4. In presentazione il canvas è in readonly (si applicano le funzioni "Better Readonly").

## Template di nodo

Con **un solo nodo selezionato**: *Advanced Canvas: Save node as template* → scegli un'icona → il template compare nel card menu per riutilizzo rapido. Rimozione: click destro sul template nel card menu → Remove.

## Portals

Incorpora un altro canvas come nodo file, poi clicca l'icona "porta" nel popup menu per aprirlo come portal navigabile, con edge verso l'esterno.

## Gruppi collassabili

I gruppi possono essere espansi/collassati per organizzare canvas complessi.

## Focus mode ed edge highlight

- **Focus mode**: sfoca tutti i nodi tranne quello selezionato.
- **Edge highlight**: evidenzia gli edge collegati al nodo selezionato (personalizzabile via CSS sulla classe `.is-focused`).
- **Edge selection**: seleziona gli edge collegati al/ai nodo/i selezionato/i; con l'opzione "Select Edge By Direction" attiva, puoi selezionare solo entranti o uscenti.

## PDF annotation

- Parametro `pinned=true` su un embed PDF per mostrare/annotare una sola pagina.
- Comando *Advanced Canvas: Insert PDF for annotation*: crea un nodo per pagina (aspect ratio bloccato).
- Comando *Advanced Canvas: Pin PDF page*: fissa la pagina corrente di un embed PDF.

## Export immagine

Comando *Advanced Canvas: Export canvas as image* → PNG/SVG, con trasparenza, "Privacy Mode" e "Show Logo" (incluso logo Advanced Canvas).

## Encapsulate selection

Seleziona uno o più nodi → click destro → *Encapsulate selection* (o comando da palette): sposta la selezione in un nuovo canvas e crea un link di ritorno nel canvas originale.

## Ricerca nel canvas

`Ctrl+F` / `Cmd+F` (comando *Search current file*) apre una ricerca testuale nativa su tutti i nodi del canvas corrente.

## Colori e stili custom via CSS

- **Colori custom in palette**: snippet CSS con `--canvas-color-X: <colore>;` (X = indice > 6, quelli 1-6 sono di Obsidian).
- **Attributi di stile custom per nodi/edge**: si definiscono con un commento YAML in un file CSS (`@advanced-canvas-node-style` o `@advanced-canvas-edge-style`), poi si stilizzano via `.canvas-node[data-<chiave>="<valore>"]`. Richiede sempre un'opzione con `value: null`. I breakpoint variabili di rendering (`--variable-breakpoint`, range 1 a -4) si impostano allo stesso modo ma vengono cachati: serve riaprire il canvas dopo modifiche CSS.

## Impostazioni utili (tutte disattivabili)

Allineamento automatico alla griglia, dimensioni di default per nodi testo/file, dimensione minima nodo, disattivazione scaling font su zoom, readonly avanzato (blocco posizione/zoom/popup menu mantenendo zoom-to-selection).

## Checklist quando generi/assisti su un canvas

1. Verifica che il plugin community **Advanced Canvas** sia installato/abilitato prima di assumere che una feature (forme, presentazione, portal, ecc.) funzioni — se l'utente lamenta che non succede nulla, il problema è quasi sempre plugin mancante, non l'uso scorretto.
2. Per flowchart, usa le forme dedicate (Decision, Process, ecc.) invece di note testuali semplici.
3. Per presentazioni, ricordati di numerare gli edge quando un nodo ha più uscite, altrimenti l'ordine di navigazione è ambiguo.
4. Se l'utente chiede di editare il file `.canvas` direttamente, ricorda che è JSON: mantieni struttura valida (`nodes`, `edges`, id univoci) — meglio comunque suggerire di operare dall'UI quando possibile.
5. Per styling permanente (colori, attributi custom, breakpoint), serve uno snippet CSS abilitato in Impostazioni → Aspetto → CSS snippets, non l'editor del canvas.

## Fonte

Documentazione ufficiale: [github.com/Developer-Mike/obsidian-advanced-canvas](https://github.com/Developer-Mike/obsidian-advanced-canvas) (README, verificato via ricerca web — plugin community id `advanced-canvas`, ultima versione nota 7.0.0).
---
