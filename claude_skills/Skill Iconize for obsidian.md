---
name: obsidian-iconize
description: Usa questa skill quando devi assegnare, cambiare o rimuovere icone a file/cartelle in Obsidian tramite il plugin Iconize (obsidian-icon-folder), o quando devi verificare quale icona ha un file. Attivala per richieste tipo "metti un'icona a questa nota/cartella", "che icona ha questo file?", "togli l'icona", "icona nel titolo/tab".
---

# Plugin Iconize per Obsidian

Plugin ID: `obsidian-icon-folder`. Config e icone assegnate stanno in:
`.obsidian/plugins/obsidian-icon-folder/data.json`

## Come sono salvate le icone

Due meccanismi, **non** mescolarli:

1. **`data.json` (default)** — chiave = percorso vault-relative del file/cartella, valore = ID icona.
   ```json
   "Politecnico/Geometria e Algebra Lineare/Indice.md": "LiInfo"
   ```
2. **Frontmatter** — solo se `iconInFrontmatterEnabled: true` nei settings. Campi: `icon` e `iconColor`.
   ```yaml
   ---
   icon: LiInfo
   iconColor: "#ff0000"
   ---
   ```
   Con questa opzione spenta (default qui) il frontmatter viene ignorato.

## Formato ID icona

| Prefisso | Pack | Esempio |
|---|---|---|
| `Li` | Lucide (nativo) | `LiInfo`, `LiBookOpen`, `LiCalculator` |
| `Fa`/`Fas`/`Far` | FontAwesome | `FaSolidHome` |
| `Ri`, `Bs`, `Io`... | altri pack | secondo pack installato |
| emoji | Unicode | `📘` |

Lucide: nome kebab-case → PascalCase con prefisso `Li` (`book-open` → `LiBookOpen`). Nomi in https://lucide.dev/icons.

## Procedure

**Leggere l'icona di un file**: cerca il percorso in `data.json` (Grep sul nome file). Se assente, controlla il frontmatter del file (`icon:`). Non puoi vedere il rendering, solo la config.

**Assegnare / cambiare**:
1. Chiudi o avvisa l'utente: Obsidian sovrascrive `data.json` dal suo stato in memoria. Meglio modificare con Obsidian chiuso, oppure chiedere all'utente di farlo via UI.
2. Aggiungi/modifica la riga `"percorso": "IDIcona"` (JSON valido: virgole, niente trailing comma).
3. Dopo modifica: ricarica Obsidian (`Ctrl+R`) o disabilita/riabilita il plugin.

**Rimuovere**: cancella la riga della chiave.

**Rinomina/spostamento file**: se si sposta un file col filesystem, la chiave in `data.json` si rompe. Muovi sempre via Obsidian (CLI `move`), così Iconize aggiorna il percorso.

**Via UI (consigliato all'utente)**: tasto destro su file/cartella → *Change icon* → cerca → scegli. Per cambiare colore: *Change color*.

## Settings utili (in `data.json` → `settings`)

- `iconsInNotesEnabled` — icone inline nel testo con `:nome:` (identifier `iconIdentifier`, default `:`).
- `iconsInLinksEnabled` — mostra icone nei `[[link]]`.
- `iconInTabsEnabled` — icona nei tab.
- `iconInTitleEnabled` / `iconInTitlePosition` — icona sopra/accanto al titolo della nota.
- `iconInFrontmatterEnabled` — usa il frontmatter come sorgente.
- `rules` — assegnazione automatica per regex/cartella (es. tutte le note di una cartella).

## Troubleshooting

- Icona non appare → pack Lucide non caricato (`lucideIconPackType`), ID sbagliato, o Obsidian non ricaricato.
- Icona sparisce dopo rename → chiave orfana in `data.json`, correggi il percorso.
- Modifica a `data.json` persa → Obsidian era aperto e l'ha sovrascritto.
- Icona nel frontmatter ignorata → `iconInFrontmatterEnabled` è `false`.
