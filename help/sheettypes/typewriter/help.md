# Typewriter sheet

Word-processing surface backed by Tiptap v3 (ProseMirror) with `y-prosemirror`
collaboration, lazy-loaded into a typewriter sheet on first render. Visual
language clones Google Docs: GDocs-style toolbar + ruler, page-chrome
pagination with headers/footers, an Insert menu, right-click context menus,
HTML/Markdown/DOCX export, DOCX/Markdown/TXT import, and surface embeds for spreadsheet ranges,
kanban boards, dashboards, and charts.

![Typewriter](/help-assets/screenshots/typewriter-sheet.png)

This document is the authoritative reference. It mirrors the live runtime —
the CLI section is generated from the same metadata `xapps typewriter
<command> --help` reads at runtime, so you cannot drift the two.

## Quick start

1. Open or create a workbook in xApps.
2. Click **+ Add sheet** and pick **Typewriter**. The shell mounts the
   typewriter host inside the sheet container and lazy-loads `editor-bundle.js`
   on first render (~750 KB gzipped). Subsequent typewriter sheets re-use the
   cached bundle.
3. Type. Multi-user collaboration runs through the workbook's existing Y.Doc
   via a per-sheet `Y.XmlFragment` keyed by `typewriterDocId`.
4. **`Cmd-S`** saves the entire workbook. Per-sheet "Save as…" lives under
   **Sheet → Save as…** (HTML, Markdown, DOCX).
5. The persisted document is a ProseMirror JSON tree on the sheet under
   `typewriterDoc`. Settings (page size, margins, headers/footers, page
   numbering) live on `typewriterSettings`.

## Toolbar reference

![Typewriter toolbar](/help-assets/screenshots/typewriter-toolbar.png)

The toolbar is a single 40 px row with `flex-wrap: nowrap` and horizontal
overflow scroll for narrow viewports. Sections are separated by thin
dividers. Hover state is rounded; active state highlights when the cursor
sits inside the relevant mark/node.

| Section | Buttons / dropdowns | Notes |
|---|---|---|
| **History** | Undo (`Cmd-Z`) · Redo (`Cmd-Shift-Z` / `Cmd-Y`) | Standard ProseMirror history. |
| **Print** | Print (`Cmd-P`) | Routes to `browser-print.ts` which generates an `@page` CSS document. The CLI cannot print. |
| **Zoom** | Zoom dropdown (`50% / 75% / 90% / 100% / 125% / 150% / 200%`) | Applied via CSS `transform: scale()` on the editor host. *Status-bar zoom slider is queued for V2.1.14.* |
| **Paragraph style** | Title · Subtitle · Heading 1–6 · Normal text | Title/Subtitle collapse to H1/H2 in Markdown round-trip. |
| **Font family** | Inter / Roboto / Georgia / Times / Courier / Arial / Verdana / etc. | Stored as `fontFamily` mark; lost on Markdown export. |
| **Font size** | `+`/`−` stepper, numeric input | Stored as `fontSize` mark; lost on Markdown export. |
| **Inline marks** | **B** (`Cmd-B`) · *I* (`Cmd-I`) · <u>U</u> (`Cmd-U`) · ~~S~~ (`Cmd-Shift-X`) · text color · highlight color · clear formatting | Strike uses `Cmd-Shift-X`. Color pickers are GDocs-style 10-column swatch grids backed by `browser-color-picker.ts`. |
| **Link** | Link button (`Cmd-K`) | Opens `browser-link-dialog.ts` modal with URL + display text + open-in-new-tab toggle. Inline popover appears when the cursor is on a link. |
| **Alignment** | Left / Center / Right / Justify | Backed by `@tiptap/extension-text-align`. |
| **Line spacing** | 1.0 / 1.15 / 1.5 / 2.0 / 2.5 / 3.0 / Custom… | Custom prompts for an arbitrary multiplier. |
| **Lists** | Bullet (`Cmd-Shift-8`) · Numbered (`Cmd-Shift-7`) · Checklist · Indent / Outdent | 5-level depth-cycled bullet glyphs (`•`, `◦`, `▪`, `▫`, `‣`). Tab/Shift-Tab in lists adjusts depth. |
| **Insert** kebab + Insert menu | All 18 entries — see [Insert menu](#insert-menu-v2111) | The kebab also exposes "Import from file…" / "Export as…". |
| **Tables (when active)** | Floating toolbar above active table — see [Tables](#tables) | Only renders when the cursor sits inside a table. |

### Keyboard shortcuts in the toolbar

The toolbar honours `Cmd-K` (link) and `Cmd-P` (print) on document capture
phase, ahead of the browser's native handlers. Bold / italic / underline /
strike route through Tiptap's StarterKit defaults.

## Insert menu (V2.1.11)

The menubar exposes an **Insert** slot wired through shell-core's generic
`MENU_SLOT_ORDER`. The 18 entries:

| Group | Id | Label | Shortcut |
|---|---|---|---|
| Media | `typewriter-insert-image` | Image… | — |
| | `typewriter-insert-link` | Link… | `Ctrl-K` |
| Tables / embeds | `typewriter-insert-table` | Table… | — |
| | `typewriter-insert-embed` | Sheet embed… | — |
| Page chrome | `typewriter-insert-header` | Header | — |
| | `typewriter-insert-footer` | Footer | — |
| | `typewriter-insert-page-numbers` | Page numbers… | — |
| | `typewriter-insert-page-break` | Page break | — |
| Inline atoms | `typewriter-insert-hr` | Horizontal line | — |
| | `typewriter-insert-special-chars` | Special characters… | — |
| | `typewriter-insert-bookmark` | Bookmark… | — |
| | `typewriter-insert-cross-reference` | Cross-reference… | — |
| | `typewriter-insert-toc` | Table of contents | — |
| Lists | `typewriter-insert-bullet-list` | Bullet list | `Ctrl-Shift-8` |
| | `typewriter-insert-ordered-list` | Numbered list | `Ctrl-Shift-7` |
| | `typewriter-insert-task-list` | Checklist | — |
| Code / quote | `typewriter-insert-code-block` | Code block | — |
| | `typewriter-insert-blockquote` | Blockquote | — |

### Behaviours

- **Image…** opens the image popover (Upload / By URL / Search the web stub).
- **Link…** opens the link modal (also bound to `Cmd-K`).
- **Table…** opens the 10×10 grid picker.
- **Sheet embed…** opens the Insert Embed dialog (snapshot mode).
- **Header / Footer** toggle the page-chrome region with the cursor inside it.
- **Page numbers…** opens the page-numbering subdialog (placement, alignment,
  template).
- **Page break** inserts a `pageBreak` Tiptap node; renders as `page-break-before:
  always` for print/HTML/DOCX.
- **Horizontal line** inserts `<hr>`.
- **Special characters…** opens a Unicode picker (block + grid).
- **Bookmark…** opens the bookmark dialog (slug-validated).
- **Cross-reference…** opens the cross-reference dialog. *Live navigation is
  in-flight; the cross-ref dialog ships, but heading nodes don't yet emit
  `id="heading-{slug}"` — see Known limitations.*
- **Table of contents** inserts a `tableOfContents` node; export-time
  exporters crawl headings to inline a TOC.
- **Bullet / Numbered / Checklist** start the corresponding list at the cursor.
- **Code block / Blockquote** wrap the current paragraph.

## Tables

Backed by `@tiptap/extension-table` (resizable columns) and the
`browser-table-*` modules. Two tiers of features:

### Tier 1 — basics

- **Insert** via the kebab "Insert table" or `Insert → Table…`. 10×10 grid
  picker, optional header row checkbox.
- **Merge / Split cells** through the right-click context menu when a
  CellSelection is active.
- **Header row toggle** in the floating table toolbar.
- **Header column toggle** (Tier 1+ extension; sibling of header row).
- **Row drag-resize** via a `contenteditable=false` resize handle — stores
  per-row `minHeight`.
- **Distribute rows / columns evenly** (right-click → Distribute…).

### Tier 2 — round-out

- **Cell background color** with localStorage swatch recents.
- **Vertical alignment** (top / middle / bottom).
- **Cell padding** stepper (0–64 px).
- **Per-side borders** (top / right / bottom / left) with color, weight, and
  style — backed by `browser-table-borders.ts`.
- **Paragraph ↔ Table conversion** (right-click → Convert to/from table). Uses
  tab characters as the column separator.

### Right-click menu sections

The table context menu groups actions: **Selection** (cut/copy/paste,
align), **Cells** (merge/split, padding, borders, bg color), **Rows**
(insert above/below, distribute, header toggle, drag-resize hint),
**Columns** (insert before/after, distribute, header toggle), and **Table**
(insert/delete, convert to/from paragraphs).

## Surface embeds (V2.1.2 + V2.1.8)

Drag a spreadsheet cell range, kanban list, dashboard widget, or chart
into the typewriter document. The surface registers an embed renderer with
`XAppsSheetRegistry.registerEmbedRenderer(kind, renderer)` (shell-core
generic API; zero kind-aware branching in the shell). Drops are routed
through a ProseMirror PM-plugin drop-handler that reads the embed payload
from a synthetic `text/x-xapps-embed` MIME and inserts a `surfaceEmbed`
atom node.

### Insert Embed dialog

`Insert → Sheet embed…` opens the dialog. Pick the source surface, narrow
to a sheet (and a cell range, for spreadsheets). The current default is
**Snapshot mode** — the embed renders a frozen JSON-serialized snapshot of
the source. **Live mode** is reserved for V2.x when the workbook collab
runtime exposes the per-sheet Y.Doc accessor.

### Persistence

The embed node carries `attrs = { kind, sheetId, range?, mode }`. On
serialization to Markdown, embeds emit `[Embed: <kind>]` placeholder text
(lossy). HTML round-trip preserves the node; DOCX round-trip preserves
the placeholder text.

## Import / Export

The Sheet menu exposes server-backed **Open** / **Replace** for workbook
documents and explicit import rows for external Word, Markdown, and text
files.

### HTML — lossless

- Export wraps `editor.getHTML()` in a standalone HTML5 document with an
  inline print-grade stylesheet (no external assets).
- Import accepts pasted or file-loaded HTML; routed through Tiptap's
  built-in HTML parser, which round-trips every extension's
  `parseHTML`/`renderHTML` rules.

### Markdown — partly lossy

- Export uses a hand-rolled CommonMark+GFM serializer
  (`browser-import-export-md.ts`). 666 lines, ~6 KB; chosen over
  `prosemirror-markdown` to avoid pulling in `markdown-it` (~165 KB). GFM
  pipe tables, fenced code, link/inline emphasis, headings (H1–H6), and
  task lists are preserved.
- Import accepts Markdown via paste-detect heuristic OR explicit "Import
  from file…". Conservative paste detection keeps regular HTML pasted from
  the web on Tiptap's HTML path.

### Plain text — import-only

- Import accepts `.txt` / `.text` files from **Sheet → Open → Import Text
  file (.txt)**. Text is escaped into paragraphs with hard line breaks, so
  literal markup remains text instead of becoming DOM.

#### Markdown round-trip lossy fields

| Lost field | Preserved by |
|---|---|
| Font color, highlight, family, size | HTML, DOCX |
| `link.target=_blank` | HTML, DOCX |
| Text alignment | HTML, DOCX |
| Line spacing | HTML, DOCX |
| Indent levels | HTML, DOCX |
| Heading variants (Title / Subtitle) | HTML, DOCX |
| List `listStyleType` | HTML, DOCX |
| First-line / left / right indent and tab stops | HTML, DOCX |
| Surface embeds (round-trip) | HTML preserves node; Markdown emits `[Embed: kind]` text |

`underline` is preserved via inline `<u>`. Tables flatten cell content to
inline (block-level cells collapse to one line; nested tables are dropped).

### DOCX — faithful preview + editable fallback

- Default **Sheet → Open → Import Word document (.docx)** uploads the
  original Word file and inserts a Typewriter `docxPreview` node rendered
  with `docx-preview`. This preserves the source page geometry, table
  layout, fonts, colors, borders, headers/footers, and spacing far better
  than semantic HTML conversion. The preview is view-only.
- **Import Word as editable text (.docx)** keeps the Mammoth conversion
  path for users who need editable paragraphs/tables inside Typewriter.
  That path is intentionally semantic and can lose Word layout details.
- DOCX export is still powered by `docx` in the lazy `docx-bundle.js` and
  serializes the editable Typewriter document tree.

### Round-trip fidelity matrix

| Format | Headings | Inline marks | Lists | Tables | Images | Embeds | Page chrome | Color/font |
|---|---|---|---|---|---|---|---|---|
| HTML | ✓ | ✓ | ✓ | ✓ | ✓ | node preserved | ✓ | ✓ |
| Markdown | H1–H6 only | bold/italic/underline/strike/code/link | ✓ (incl. tasklist) | GFM pipe | ✓ (alt+src) | placeholder text | ✗ | ✗ |
| DOCX preview | source layout | source layout | source layout | source layout | source layout | source file | source page | source styles |
| DOCX editable | ✓ | ✓ | ✓ | ✓ | ✓ | placeholder | partial | ✓ |

## Page setup (V2.2)

Visual pagination, headers / footers, auto page numbering, custom page
size, margins, and `@page`-CSS print/PDF — all rebuilt in V2.1.11.

- **Visual pagination** — `browser-pagination.ts` measures page heights
  off the editor scroll and shifts content into virtual pages. The
  current page index, page count, and per-page first-block id are
  exposed via a `pageInfo` event for the queued status bar (V2.1.14).
- **Headers / footers** — `header.enabled` / `footer.enabled` settings.
  Each carries an independent ProseMirror JSON document. Optional
  `differentFirstPage` and `differentEvenOdd` toggles add
  `firstPageContent` and `evenPageContent` documents.
- **Auto page numbering** — `pageNumbering.{ enabled, placement, align,
  format, startAt?, suppressOnFirstPage? }`. Format is a template with
  `{X}` (current) and `{Y}` (total). Defaults: `Page {X} of {Y}`,
  `placement=footer`, `align=center`.
- **Page size** — five presets (`letter`, `legal`, `a4`, `a3`, `tabloid`)
  plus a custom `{ widthPx, heightPx }` shape (px @ 96 DPI). The CLI
  accepts `WxH` in inches and converts to px.
- **Margins** — stored as `{ top, right, bottom, left }` integer px @ 96
  DPI. The page-setup dialog exposes a 2×2 input grid.
- **Print / PDF** — `browser-print.ts` writes an `@page` CSS document
  carrying the selected page size, margins, and orientation. `Cmd-P`
  intercepts before the browser's native handler.

### Page Setup dialog

Opens via the kebab → Page setup… or `Insert → Header / Footer / Page
numbers…`. Sticky-header / scrollable-body / sticky-footer layout with
`max-height: min(90vh, 800px)`; works at 1024×600, 1024×900, 1200×768
viewports. Smoke covers viewport-aware layout.

## Workbook + Sheet menu (V2.1.9)

The menubar splits into **Workbook** and **Sheet** dropdowns:

```
Workbook ▸                         Sheet ▸
  New workbook…                      New current sheet…
  Open workbook…                     ─
  Save              Cmd-S            Open ▸
  Save As…                             Open in new sheet…
  ─                                    Replace current sheet content…
  Recent workbooks ▸                   Import Word document (.docx)
  ─                                    Import Word as editable text (.docx)
  Close workbook                       Import Markdown (.md)
                                       Import Text file (.txt)
                                     Save
                                     Save as ▸
                                       Typewriter document
                                       HTML
                                       Markdown
                                       DOCX
                                     ─
                                     Recent files ▸
                                     ─
                                     Sheet settings…
```

- **`Cmd-S`** stays on workbook save. Per-sheet save has no shortcut by
  design (avoids breaking muscle memory across surfaces). If demand
  surfaces, a `Cmd-Shift-Alt-S` chord is the future home.
- **Recent files** is per-surface localStorage; the typewriter list
  defaults to "Open in new sheet" (the safe path).
- The generic shell-core `XAppsRecentFiles` and `registerImportFileExtension`
  hooks back the menu items; surfaces self-publish without the shell
  needing to know about typewriter formats.

## Right-click context menu (V2.1.6)

Sectioned, context-aware actions. The menu varies based on the cursor /
selection:

- **Anywhere** — Cut / Copy / Paste / Paste plain (`Cmd-Shift-V`).
- **Inside text** — Bold / Italic / Underline shortcuts; font color;
  highlight color; clear formatting; Look up "…" (browser dictionary).
- **On a link** — Edit link (`Cmd-K`), Open link (`Cmd-Click`), Remove
  link, Copy link.
- **In a list** — Increase / decrease indent (`Tab` / `Shift-Tab`);
  switch list style.
- **In a table** — full Table sub-menu (see [Tables](#tables)).
- **On an image** — Replace, Align L/C/R, Resize, Remove.

The `shortcutHint()` helper formats key combos OS-aware (`⌘` on macOS,
`Ctrl` elsewhere).

## Keyboard shortcuts table

| Shortcut | Action |
|---|---|
| `Cmd-B` | Bold |
| `Cmd-I` | Italic |
| `Cmd-U` | Underline |
| `Cmd-Shift-X` | Strikethrough |
| `Cmd-K` | Insert / edit link |
| `Cmd-Z` | Undo |
| `Cmd-Shift-Z` / `Cmd-Y` | Redo |
| `Cmd-S` | Save workbook |
| `Cmd-P` | Print / PDF |
| `Cmd-A` | Select all |
| `Cmd-Shift-7` | Numbered list |
| `Cmd-Shift-8` | Bullet list |
| `Tab` (in list) | Increase list depth |
| `Shift-Tab` (in list) | Decrease list depth |
| `Tab` (in table) | Move to next cell (or insert row at end) |
| `Shift-Tab` (in table) | Move to previous cell |
| `Cmd-Shift-V` | Paste plain text |
| `Cmd-Click` (on link) | Open link in new tab |
| `Cmd-+` / `Cmd--` | Zoom in / out (toolbar) |
| `Esc` (in dialog) | Close dialog |
| `Enter` (in dialog) | Confirm primary action |

Heading shortcuts go through Tiptap StarterKit defaults
(`Cmd-Alt-1`…`Cmd-Alt-6`) but the GDocs-style **Paragraph style**
dropdown is the canonical UI.

## Status bar (V2.1.14)

![Typewriter status bar](/help-assets/screenshots/typewriter-status-bar.png)

The status bar is a persistent 32 px strip pinned to the bottom of the
typewriter host. It never overlaps the page — `browser-status-bar.ts`
appends it to the host element outside the page-chrome area.

### Left cluster — document statistics

| Slot | Content | Interaction |
|---|---|---|
| **Page indicator** | `Page N of M` | Click to scroll to a specific page (queued; currently cosmetic). |
| **Counts** | `N words · N chars` | Click to open a **Document statistics** popover with all six counters (see below). |
| **Reading time** | `~N min` | Hidden when the host is narrower than 250 px. Hidden at 0 words. |

The counts popover exposes:

| Counter | Notes |
|---|---|
| Words | Tokenised by ProseMirror text nodes, split on Unicode whitespace. |
| Characters | Includes spaces and punctuation. |
| Characters (excl. spaces) | Strips all Unicode whitespace before counting. |
| Paragraphs | Counts `paragraph` nodes, not list items or heading nodes. |
| Reading time | 225 wpm rate, rounded up to the nearest minute. |

Counts are debounced 250 ms after each editor `update` event so rapid
typing doesn't thrash the DOM.

### Right cluster — view controls

| Slot | Control | Notes |
|---|---|---|
| **Focus** | Toggle button | Adds `xapps-typewriter-host--focus` class. The toolbar, ruler, and menubar hide via CSS; the page fills the viewport. Click **Focus** again to restore. |
| **View** | Dropdown (`Page` / `Web` / `Print`) | Sets `data-view-mode` on the host element. Page = paginated chrome; Web = continuous scroll, no margins; Print = @page preview layout. |
| **Zoom** | `−` slider `+` label | Applies `transform: scale(N)` with `transform-origin: top center` on the `.xapps-typewriter-page` element. Range 50–200 % in 10 % steps. The toolbar zoom dropdown mirrors the same value. |

### Focus mode

Focus mode is Typewriter's distraction-free writing mode. Activating it:

1. Hides the toolbar, ruler, and menubar (CSS class toggle — no DOM
   removal, so keyboard shortcuts continue to work).
2. Expands the page area to fill the full host height.
3. Keeps the status bar visible so you retain word count and zoom
   without breaking focus.

Focus state is persisted on `typewriterSettings.viewState.focus` so it
survives sheet navigation and reloads.

## CLI commands

The xApps CLI surface is generated from the same metadata
`xapps typewriter <command> --help` reads at runtime. Edit
`packages/xapps-surface-typewriter/src/cli/commands.ts`, then re-run
`tools/test-typewriter-help-content.ts` (or `npm run sync:assets` after
build) to regenerate this section.

The CLI runs inside the shell-core `xapps` entrypoint and auto-registers
through the surface manifest's `runtime.cli=true` flag. All commands need
either `--base-url <url>`, `MESHAGENT_ROOM_URL`, or `XAPPS_API_BASE_URL`
to reach the workspace API.

<!-- typewriter-cli:start -->

> This block is generated from the same `TYPEWRITER_CLI_COMMANDS` array that
> backs the `xapps typewriter <command> --help` runtime. Edit
> `packages/xapps-surface-typewriter/src/cli/commands.ts`, then re-run
> `tools/test-typewriter-help-content.ts` (or `npm run sync:assets` after build)
> to regenerate. Do not hand-edit between the start/end markers.

### `xapps typewriter export`

Export a typewriter document to html, md, txt, or json.

**Usage:**

```
xapps typewriter export <sheet> <format> [--out <path>]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<format>` | yes | One of html, md, txt, json. (docx is UI-only — see notes.) |
| `[--out <path>]` | no | Write the exported body to this file path; otherwise print to stdout. |

**Notes:**

- json emits the raw ProseMirror document; html emits a <body>-fragment ready to wrap; md emits CommonMark with GFM tables.
- DOCX export is browser-only because the docx library ships in a lazy editor bundle. Use the live app's Export menu for DOCX.

**Examples:**

```sh
xapps typewriter export "Draft" md --out draft.md
xapps typewriter export "Draft" json
```

### `xapps typewriter import`

Replace a typewriter document with the contents of a file.

**Usage:**

```
xapps typewriter import <sheet> <path> [--format html|md|txt|json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<path>` | yes | Local file path to import. Format is inferred from the extension unless --format is set. |
| `[--format html|md|txt|json]` | no | Force the import format when the extension is ambiguous or wrong. |

**Notes:**

- Import REPLACES the document. To merge, export to md, edit locally, and import the merged file.
- DOCX import is UI-only (mammoth ships in the lazy docx bundle). Use the live app's Import menu for DOCX.

**Examples:**

```sh
xapps typewriter import "Draft" notes.md
xapps typewriter import "Draft" pasted.html --format html
```

### `xapps typewriter wordcount`

Print word, character, and paragraph counts as JSON.

**Usage:**

```
xapps typewriter wordcount <sheet>
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |

**Notes:**

- Output shape: { words, characters, charactersNoSpaces, paragraphs, headings, readingTimeMinutes }.
- Reading time uses the standard 225 wpm rate, rounded up.

**Examples:**

```sh
xapps typewriter wordcount "Draft"
```

### `xapps typewriter set-page-size`

Set the page size preset (letter|legal|a4|a3|tabloid) or a custom WxH in inches.

**Usage:**

```
xapps typewriter set-page-size <sheet> <size> [portrait|landscape]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<size>` | yes | Preset name (letter|legal|a4|a3|tabloid) or custom dimensions like 8.5x11 (inches). |
| `[portrait|landscape]` | no | Optional orientation override. |

**Notes:**

- Custom sizes are stored as pixels at 96 DPI; the page-setup dialog rounds to the nearest integer.

**Examples:**

```sh
xapps typewriter set-page-size "Draft" a4
xapps typewriter set-page-size "Draft" 8.5x11 landscape
```

### `xapps typewriter set-margins`

Set page margins; each value accepts a unit suffix (in/cm/mm), defaulting to inches.

**Usage:**

```
xapps typewriter set-margins <sheet> <top> <right> <bottom> <left>
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<top>` | yes | Top margin like 1, 1in, 2.54cm, or 25mm. Unitless values are inches. |
| `<right>` | yes | Right margin (same syntax as <top>). |
| `<bottom>` | yes | Bottom margin (same syntax as <top>). |
| `<left>` | yes | Left margin (same syntax as <top>). |

**Notes:**

- Margins are stored as integer pixels at 96 DPI; the dialog and CLI round on save.

**Examples:**

```sh
xapps typewriter set-margins "Draft" 1 1 1 1
xapps typewriter set-margins "Draft" 25mm 25mm 25mm 25mm
```

### `xapps typewriter set-page-numbers`

Enable auto page numbering with placement, alignment, and a {X}/{Y} template.

**Usage:**

```
xapps typewriter set-page-numbers <sheet> [--placement header|footer] [--align left|center|right] [--format <template>]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `[--placement header|footer]` | no | Where to render numbers; defaults to footer. |
| `[--align left|center|right]` | no | Horizontal alignment within the header/footer; defaults to center. |
| `[--format <template>]` | no | Template with {X} (current page) and {Y} (total pages); defaults to "Page {X} of {Y}". |

**Notes:**

- Page numbering is rendered by `browser-pagination.ts` at print/PDF time and live in the page-chrome view.

**Examples:**

```sh
xapps typewriter set-page-numbers "Draft"
xapps typewriter set-page-numbers "Draft" --placement header --align right --format "{X}"
```

### `xapps typewriter insert-embed`

Append a surface embed (spreadsheet-range, kanban, dashboard, chart) to the document.

**Usage:**

```
xapps typewriter insert-embed <sheet> <kind> <ref> [--mode snapshot|live]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<kind>` | yes | One of spreadsheet-range, kanban, dashboard, chart. |
| `<ref>` | yes | For spreadsheet-range, "<sheetId>!A1:B5". For kanban/dashboard/chart, the source sheet id. |
| `[--mode snapshot|live]` | no | Embed mode; defaults to snapshot. Live mode is reserved for V2.x. |

**Notes:**

- Embeds are inserted at the end of the document. Use the in-app Insert Embed dialog for cursor-aware placement.

**Examples:**

```sh
xapps typewriter insert-embed "Draft" spreadsheet-range "Budget!A1:C5"
xapps typewriter insert-embed "Draft" kanban "Sprint Board"
```

### `xapps typewriter list-embeds`

Enumerate embedded surfaces in a typewriter document (kind, ref, mode).

**Usage:**

```
xapps typewriter list-embeds <sheet>
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |

**Notes:**

- Output is tab-separated: kind, ref, mode. Useful for scripting bulk audits.

**Examples:**

```sh
xapps typewriter list-embeds "Draft"
```

### `xapps typewriter outline`

Print the document outline (block index, type, level, alignment, text) as JSON.

**Usage:**

```
xapps typewriter outline <sheet>
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |

**Notes:**

- The 0-based "index" in each entry is what the granular edit commands (set-block, format-block, set-align, delete-block, insert-paragraph) target.

**Examples:**

```sh
xapps typewriter outline "Draft"
```

### `xapps typewriter append-paragraph`

Append a paragraph (optionally with text) to the end of the document.

**Usage:**

```
xapps typewriter append-paragraph <sheet> [text]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `[text]` | no | Paragraph text. Omit for an empty paragraph. |

**Examples:**

```sh
xapps typewriter append-paragraph "Draft" "A new closing line."
```

### `xapps typewriter insert-paragraph`

Insert a paragraph at a 0-based block index (clamped to the document length).

**Usage:**

```
xapps typewriter insert-paragraph <sheet> <index> [text]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<index>` | yes | 0-based block position from `outline`. Use the length to append. |
| `[text]` | no | Paragraph text. Omit for an empty paragraph. |

**Examples:**

```sh
xapps typewriter insert-paragraph "Draft" 0 "New first line."
```

### `xapps typewriter delete-block`

Delete the block at a 0-based index (see `outline`).

**Usage:**

```
xapps typewriter delete-block <sheet> <index>
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<index>` | yes | 0-based block position from `outline`. |

**Examples:**

```sh
xapps typewriter delete-block "Draft" 3
```

### `xapps typewriter set-block`

Change a block to paragraph, heading, blockquote, or codeBlock (keeps its text).

**Usage:**

```
xapps typewriter set-block <sheet> <index> <type> [--level <1-6>]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<index>` | yes | 0-based block position from `outline`. |
| `<type>` | yes | paragraph | heading | blockquote | codeBlock. |
| `[--level <1-6>]` | no | Heading level (1-6) when <type> is heading; defaults to 1. |

**Examples:**

```sh
xapps typewriter set-block "Draft" 0 heading --level 1
xapps typewriter set-block "Draft" 2 blockquote
```

### `xapps typewriter set-align`

Set a block’s text alignment.

**Usage:**

```
xapps typewriter set-align <sheet> <index> <left|center|right|justify>
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<index>` | yes | 0-based block position from `outline`. |
| `<align>` | yes | left | center | right | justify. |

**Examples:**

```sh
xapps typewriter set-align "Draft" 0 center
```

### `xapps typewriter format-block`

Apply inline marks (bold,italic,underline,strike,code) to all text in a block.

**Usage:**

```
xapps typewriter format-block <sheet> <index> <marks> [--mode add|remove|set]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<index>` | yes | 0-based block position from `outline`. |
| `<marks>` | yes | Comma-separated subset of bold,italic,underline,strike,code. |
| `[--mode add|remove|set]` | no | add (default) toggles marks on, remove strips them, set replaces the block’s marks exactly. |

**Examples:**

```sh
xapps typewriter format-block "Draft" 0 bold,italic
xapps typewriter format-block "Draft" 0 bold --mode remove
```

### `xapps typewriter replace-text`

Plain-text find/replace across the document (all matches by default).

**Usage:**

```
xapps typewriter replace-text <sheet> <find> [replace] [--first]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<find>` | yes | Exact substring to find. |
| `[replace]` | no | Replacement text. Omit to delete matches. |
| `[--first]` | no | Replace only the first occurrence instead of all. |

**Examples:**

```sh
xapps typewriter replace-text "Draft" "Q3" "Q4"
xapps typewriter replace-text "Draft" "TODO" "" --first
```

<!-- typewriter-cli:end -->

## Known limitations and lossy round-trips

- **Markdown round-trip drops typography** — color, highlight, font family/
  size, alignment, line-spacing, indent levels, list-style variants, first-
  line/left/right indent, and custom tab stops. Use HTML or DOCX for
  fidelity.
- **Surface embeds in Markdown** flatten to `[Embed: <kind>]` placeholder
  text. HTML preserves the embed node so an HTML round-trip survives.
- **DOCX export from CLI is unsupported.** The `docx` library ships in the
  lazy browser bundle. CLI export covers `html`, `md`, `txt`, and `json`.
- **Cross-reference live navigation is in-flight.** The Cross-reference
  dialog ships in V2.1.11, but heading nodes don't yet emit
  `id="heading-{slug}"`, so generated cross-refs render as plain text on
  click.
- **Ruler interactivity** is V2.1.12 territory. V2.1.11 ships a reflect-
  only ruler — markers track cursor position; dragging tabs/indent
  triangles is not yet wired. Check `typewrite.md` Status table for the
  current state.
- **Live-mode embeds** are deferred. Dropping a spreadsheet range into a
  typewriter doc creates a snapshot, not a live binding. Live-mode lands
  when the workbook collab runtime exposes a per-sheet Y.Doc accessor.
- **Yjs duplicate-import warning.** The lazy editor bundle ships its own
  `yjs` instance; the workbook collab runtime carries another. Tiptap's
  Collaboration extension still works but Yjs constructor checks across
  instances are unreliable. Resolves when `XAppsCollab.getYDoc()` lands.
- **Tiptap StarterKit duplicate extension names.** StarterKit v3 already
  includes `Underline` and `Link`; the bundle imports both explicitly.
  Harmless dedup at runtime but should be cleaned up.

## Where things live

| Concern | Source |
|---|---|
| State factory + `applySettings` allow-list | `packages/xapps-surface-typewriter/src/state.ts` + `src/server.ts` |
| Public-API contract | `packages/xapps-surface-typewriter/src/public-api.ts` |
| Surface entrypoint (manifest, builder, asset map) | `packages/xapps-surface-typewriter/src/index.ts` |
| Eager client (state-hook globals + lazy trigger) | `src/runtime/client.ts` |
| Lazy editor bundle entry | `src/runtime/browser-editor.ts` |
| Toolbar | `src/runtime/browser-toolbar*.ts` |
| Ruler (reflect-only) | `src/runtime/browser-ruler*.ts` |
| Insert menu wiring | `src/runtime/browser-menu-handlers.ts` + `src/runtime/browser-insert-extensions.ts` |
| Insert dialogs (image / link / embed / bookmark / cross-ref / special chars) | `src/runtime/browser-{image,link-dialog,insert-embed-dialog,bookmark-dialog,special-chars}.ts` |
| Tables | `src/runtime/browser-table*.ts` |
| Surface embed mechanism | `src/runtime/browser-surface-embed.ts` + `src/runtime/browser-insert-embed-snapshots.ts` |
| HTML / Markdown import-export | `src/runtime/browser-import-export-{html,md}.ts` |
| DOCX import-export | `src/runtime/browser-docx-{serializer,importer,bundle,loader}.ts` |
| Page chrome (header/footer, page numbering) | `src/runtime/browser-page-{chrome,setup,setup-dialog,pagination,print}.ts` |
| Right-click context menu | `src/runtime/browser-context-menu*.ts` |
| Color picker | `src/runtime/browser-color-picker.ts` |
| Icon registry | `src/runtime/browser-icons.ts` |
| Editor styles | `src/runtime/styles.css` |
| **CLI command catalog (single source of truth)** | `src/cli/commands.ts` |
| CLI handlers + serializer | `src/cli/index.ts` + `src/cli/serializer.ts` |
| help.md generator | `src/cli/help-render.ts` |
| Live design / status doc | `typewrite.md` (repo root) |
