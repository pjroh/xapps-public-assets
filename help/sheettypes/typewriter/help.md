# Typewriter sheet

Typewriter is the document editor for reports, proposals, letters and polished
meeting notes. Write on a paginated page, style text and tables, add headers
and footers, review comments, and export a document people can read or edit.
Use **Wiki** when you want a collection of linked knowledge pages instead.

![Typewriter](/help-assets/screenshots/typewriter-sheet.png)

Start with the workflow below. The feature reference follows it; the final CLI
section is generated from the same command catalog as the installed xApps CLI.

## Quick start

1. Open or create a workbook in xApps.
2. Click **+ Add sheet** and pick **Typewriter**. Give the sheet a useful name,
   such as **Project Proposal**.
3. Write a title and a short opening paragraph. Use the paragraph-style
   dropdown for headings so the document has a real structure.
4. **`Cmd-S`** saves the entire workbook. Per-sheet "Save as…" lives under
   **Sheet → Save as…** (HTML, Markdown, DOCX).
5. Add a table, image or workbook embed from **Insert** when it helps explain
   the content. Use **Page setup** to choose page size and margins.
6. Use **Sheet → Import/export fidelity report…** before exporting layout-heavy
   documents. It summarizes what HTML, Markdown, DOCX, PDF, TXT, JSON, RTF,
   and ODT can preserve, and calls out browser-only or unsupported paths.
7. Use **Tools → Writing tools…** to review spelling, grammar, style, citation
   markers, and local assistant drafts before sharing a document.
8. Use **Tools → Keyboard shortcuts…** or `Ctrl-/` from the editor to search
   Typewriter commands and launch keyboard-first review, insert, and document
   tools.
9. Use **Print** for visual PDF output, or **Sheet → Save as** for an editable
   interchange format. Open the result and check its layout before sharing.

## Start from a template or reuse your own material

Open **Insert → Templates and reusable blocks…**. Preview a meeting note,
proposal, decision log or status update before inserting it. **Insert** adds the
selected material; **Use as document** replaces the document, so use that action
when you intend to start over. You can also save selected text as a reusable
block for standard introductions, approval sections or recurring meeting agendas.

![Typewriter Templates and reusable blocks library](/help-assets/screenshots/typewriter-templates.png)

## Take a proposal from draft to review

1. State the proposed outcome in the title and opening paragraph.
2. Apply Heading 1/2 styles to Scope, Schedule, Cost and Decision. Insert a
   table of contents when the document grows long.
3. Add a live spreadsheet embed for figures that should follow workbook changes,
   or choose Snapshot to keep a reviewed version until you refresh it.
4. Select wording that needs discussion and choose **Edit → Add comment…**.
   Open **Comments…** to return to those passages during review.
5. Use **Find and replace…** for consistent names and terminology. Check a
   match before replacing every occurrence.
6. Open **Writing tools…**, inspect suggestions and explicitly apply the ones
   you want. The built-in tools use local rules; they do not verify facts.
7. Review **Version history…** and save an interchange copy before handing the
   finished document to someone who will edit it outside xApps.

## Choose an export for the recipient

| Recipient needs | Choose | Expect |
|---|---|---|
| A fixed visual document | Print / Save as PDF | Viewing and printing; not an editable source |
| Editable Word content | DOCX | Word editing with reported conversion limits |
| Rich web content | HTML | Rich styling and supported document structure |
| Portable text with headings | Markdown | Typography and page layout are reduced |
| Text only | Plain text | No layout, styles or embedded views |
| An xApps document backup | Typewriter JSON | Structured document data |

![Typewriter import and export fidelity report for the current document](/help-assets/screenshots/typewriter-fidelity.png)

*The fidelity report considers the current document. Check it again after adding
complex tables, images, review metadata or live embeds.*

## Solve common document problems

| Symptom | Check |
|---|---|
| Toolbar and menu disappeared | Turn off **Focus** in the status bar. |
| Pages or margins look different | Check Page/Web/Print view, zoom and Page setup. |
| A heading is absent from navigation | Apply a heading style; bold text alone is not a heading. |
| A table control is missing | Click inside the table; table tools follow the current selection. |
| A pasted document lost styling | Check the source format and fidelity report; Markdown carries less styling than HTML or DOCX. |
| An embed seems old | Check Live versus Snapshot, the source sheet, and Refresh snapshot. |
| A review suggestion cannot apply | Confirm edit access and rerun analysis after changing its source text. |
| Export/import is unavailable | Save the workbook and check its access permissions and format support. |

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
| **Zoom** | Zoom dropdown (`50% / 75% / 90% / 100% / 125% / 150% / 200%`) | Applied via CSS `transform: scale()` on the editor host. The status-bar zoom control mirrors this value. |
| **Paragraph style** | Title · Subtitle · Heading 1–6 · Normal text | Title/Subtitle collapse to H1/H2 in Markdown round-trip. |
| **Font family** | Inter / Roboto / Georgia / Times / Courier / Arial / Verdana / etc. | Stored as `fontFamily` mark; lost on Markdown export. |
| **Font size** | `+`/`−` stepper, numeric input | Stored as `fontSize` mark; lost on Markdown export. |
| **Inline marks** | **B** (`Cmd-B`) · *I* (`Cmd-I`) · <u>U</u> (`Cmd-U`) · ~~S~~ (`Cmd-Shift-X`) · text color · highlight color · clear formatting | Strike uses `Cmd-Shift-X`. Color pickers are GDocs-style 10-column swatch grids backed by `browser-color-picker.ts`. |
| **Link** | Link button (`Cmd-K`) | Opens `browser-link-dialog.ts` modal with URL + display text + open-in-new-tab toggle. Inline popover appears when the cursor is on a link. |
| **Alignment** | Left / Center / Right / Justify | Backed by `@tiptap/extension-text-align`. |
| **Line spacing** | 1.0 / 1.15 / 1.5 / 2.0 / 2.5 / 3.0 / Custom… | Custom prompts for an arbitrary multiplier. |
| **Lists** | Bullet (`Cmd-Shift-8`) · Numbered (`Cmd-Shift-7`) · Checklist · Indent / Outdent | 5-level depth-cycled bullet glyphs (`•`, `◦`, `▪`, `▫`, `‣`). Tab/Shift-Tab in lists adjusts depth. |
| **Insert** kebab + Insert menu | All 18 entries — see [Insert menu](#insert-menu) | The kebab also exposes "Import from file…" / "Export as…". |
| **Tables (when active)** | Floating toolbar above active table — see [Tables](#tables) | Only renders when the cursor sits inside a table. |

### Keyboard shortcuts in the toolbar

The toolbar honours `Cmd-K` (link), `Cmd-P` (print), `Ctrl-/` (shortcut
finder), and Typewriter-specific `Ctrl-Alt-*` review/tool routes on document
capture phase, ahead of the browser's native handlers. Bold / italic /
underline / strike route through Tiptap's StarterKit defaults.

## Insert menu

The menubar exposes an **Insert** slot wired through shell-core's generic
`MENU_SLOT_ORDER`. The 19 entries:

| Group | Id | Label | Shortcut |
|---|---|---|---|
| Media | `typewriter-insert-image` | Image… | — |
| | `typewriter-insert-link` | Link… | `Ctrl-K` |
| Smart insert | `typewriter-smart-insert` | Smart insert… | `@` |
| Templates | `typewriter-insert-template-blocks` | Templates and reusable blocks… | — |
| Tables / embeds | `typewriter-insert-table` | Table… | — |
| | `typewriter-insert-embed` | Sheet embed… | — |
| Page chrome | `typewriter-insert-header` | Header | — |
| | `typewriter-insert-footer` | Footer | — |
| | `typewriter-insert-page-numbers` | Page Number | — |
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
- **Smart insert…** opens the keyboard-first `@` palette at a word boundary.
  It inserts a fixed, human-readable date or an actionable reference to another
  sheet in the current workbook. Sheet references can be opened by mouse or
  keyboard. Ordinary `@` characters inside text, including email addresses,
  remain literal text.
- **Templates and reusable blocks…** opens a document template library with
  preview, Insert, and Use as document actions. Built-ins include meeting
  notes, decision logs, proposals, summaries, and status updates. The same
  dialog can save the current selection as a custom reusable block that
  persists with the workbook-backed Typewriter sheet and can be inserted again
  after reload.
- **Table…** opens the 10×10 grid picker.
- **Sheet embed…** opens the Insert Embed dialog with Live and Snapshot modes.
- **Header / Footer** open a Word-style built-in gallery. Pick a template,
  choose Edit Header/Footer, or remove the region; editing happens in the page
  band itself with the contextual Header & Footer ribbon visible. Saved header
  and footer content renders on each page as a non-editable preview until the
  user double-clicks a header/footer band or chooses an edit command.
- **Page Number** opens a Word-style menu with Page Number, Format Page
  Numbers, and Remove Page Numbers. Page Number opens a dialog for position,
  alignment, first-page visibility, and number format.
- **Page break** inserts a `pageBreak` Tiptap node; renders as `page-break-before:
  always` for print/HTML/DOCX.
- **Horizontal line** inserts `<hr>`.
- **Special characters…** opens a Unicode picker (block + grid).
- **Bookmark…** opens the bookmark dialog (slug-validated).
- **Cross-reference…** opens the cross-reference dialog. Heading targets emit
  stable `id="heading-{slug}"` anchors, so same-document references and TOC
  entries scroll to the target.
- **Table of contents** inserts a `tableOfContents` node; export-time
  exporters crawl headings to inline a TOC, and the in-editor entries are
  clickable.
- **Bullet / Numbered / Checklist** start the corresponding list at the cursor.
- **Code block / Blockquote** wrap the current paragraph.

## Edit and review workflows

The Edit menu and toolbar expose Word-familiar document review utilities:

| Id | Label | Behaviour |
|---|---|---|
| `typewriter-find-replace` | Find and replace… | In-page find/replace panel with next/previous, replace current, replace all, and match-case. |
| `typewriter-add-comment` | Add comment… | Adds a persisted inline review comment mark to the selected text. |
| `typewriter-show-comments` | Comments… | Lists review comments and jumps back to the referenced text. |
| `typewriter-word-count` | Word count… | Opens the in-page document statistics dialog; no browser alert fallback. |

## Tables

Backed by `@tiptap/extension-table` (resizable columns) and the
`browser-table-*` modules. Two tiers of features:

### Table structure

- **Insert** via the kebab "Insert table" or `Insert → Table…`. 10×10 grid
  picker, optional header row checkbox.
- **Merge / Split cells** through the right-click context menu when a
  CellSelection is active.
- **Header row toggle** in the floating table toolbar.
- **Header column toggle** (independent of the header row).
- **Row drag-resize** via a `contenteditable=false` resize handle — stores
  per-row `minHeight`.
- **Distribute rows / columns evenly** (right-click → Distribute…).

### Cell appearance

- **Cell background color** with localStorage swatch recents.
- **Vertical alignment** (top / middle / bottom).
- **Cell padding** stepper (0–64 px).
- **Per-side borders** (top / right / bottom / left) with color, weight, and
  style — backed by `browser-table-borders.ts`.
- **Paragraph ↔ Table conversion** (right-click → Convert to/from table). Uses
  tab characters as the column separator.

### Automation parity

`POST /document/ops`, the typed SDK, `xapps typewriter apply-ops`, and the
strict Typewriter toolkit expose the same atomic table operations: insert,
row/column CRUD, merge/split, headers, resize/distribute, cell styling and
borders, and paragraph/table conversion. Table coordinates are 0-based.

### Right-click menu sections

The table context menu groups actions: **Selection** (cut/copy/paste,
align), **Cells** (merge/split, padding, borders, bg color), **Rows**
(insert above/below, distribute, header toggle, drag-resize hint),
**Columns** (insert before/after, distribute, header toggle), and **Table**
(insert/delete, convert to/from paragraphs).

## Surface embeds

Bring a spreadsheet cell range, Kanban list, Dashboard widget or chart into
your document using **Insert → Sheet embed…**. Supported sources also allow
dragging their content into the document. An embed keeps the source recognizable
without requiring you to rebuild the same information as a table or image.

### Insert Embed dialog

`Insert → Sheet embed…` opens the dialog. Pick the source surface, narrow
to a sheet (and a cell range, for spreadsheets), then choose **Live** or
**Snapshot** mode. Live same-workbook embeds refresh from the source sheet
when the document opens and when workbook changes arrive. Snapshot embeds
keep their saved export fallback until the user clicks **Refresh snapshot**.
External workbook embeds render the saved snapshot as a portable fallback.

### Exporting embeds

Markdown and DOCX use placeholder text for embeds. HTML preserves the embed
and its latest saved snapshot. Review the exported document before sending it,
especially when the recipient cannot open the source workbook.

## Import / Export

The Sheet menu exposes server-backed **Open** / **Replace** for workbook
documents and explicit import rows for external Word, Markdown, and text
files.

### HTML — rich document interchange

HTML preserves supported formatting, tables and embed snapshots. Paste rich
HTML content into the editor, or use the available file import commands.
Export produces an HTML document with its formatting stylesheet. Linked images
can still require access to their source; check them in the recipient's context.

### Markdown — partly lossy

- Export preserves headings, links, emphasis, fenced code, task lists and
  simple pipe tables. Page styling and embedded workbook views need richer
  formats; see the table below.
- Use the Markdown import command for a `.md` file. Recognizable Markdown
  pasted into the editor can also be converted; ordinary rich HTML paste
  keeps its formatting.

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

### DOCX — editable import

- Default **Sheet → Open → Import editable Word document (.docx)** converts
  the Word file into editable Typewriter content. The converter renders the
  DOCX through `docx-preview`, then flattens the resolved DOM into
  ProseMirror-friendly HTML so text, headings, tables, links, colors,
  fonts, spacing, and list markers remain writable.
- DOCX import always creates editable Typewriter content; there is no
  read-only import mode.
- DOCX export is still powered by `docx` in the lazy `docx-bundle.js` and
  serializes the editable Typewriter document tree.

### Round-trip fidelity matrix

HTML, Markdown, plain text, and JSON use the same saved-workbook server
interchange contract in the browser, CLI, SDK, and hosted toolkit. Imports are
sanitized, limited to 5 MB, revision/request guarded, and replace the document
atomically. Browser exports download the server attachment URL directly.

| Format | Headings | Inline marks | Lists | Tables | Images | Embeds | Page chrome | Color/font |
|---|---|---|---|---|---|---|---|---|
| HTML | ✓ | ✓ | ✓ | ✓ | ✓ | node preserved | ✓ | ✓ |
| Markdown | H1–H6 only | bold/italic/underline/strike/code/link | ✓ (incl. tasklist) | GFM pipe | ✓ (alt+src) | placeholder text | ✗ | ✗ |
| DOCX editable | ✓ | ✓ | ✓ | ✓ | ✓ | placeholder | partial | ✓ |

### Fidelity report

**Sheet → Import/export fidelity report…** opens an in-page report based on the
server's current ProseMirror document and `typewriterSettings`. It flags document
signals such as tables, images, live surface embeds, page chrome, rich styling,
and review metadata, then maps them to each export path:

- **JSON** is the lossless xApps backup and compatibility-fixture path.
- **HTML** is the richest CLI/browser interchange format outside DOCX.
- **Markdown** is portable but intentionally drops page chrome, typography,
  most layout styling, live embeds, and rich image/container data.
- **DOCX** is available through the live browser plus bounded API, SDK, CLI,
  MCP/toolkit import/export paths. Encrypted and legacy binary Word files are
  rejected; fidelity losses are reported explicitly.
- **PDF** uses browser Print and is visual output, not editable document data.
- **TXT** is plain text extraction.
- **RTF** and **ODT** are explicit unsupported interchange formats. Use DOCX,
  HTML, Markdown, or JSON depending on the fidelity need.

## Writing tools

**Tools → Writing tools…** opens an in-page review surface for document text.
Analysis is deterministic and server-owned: no document text is sent to an AI
provider. The browser, typed SDK, CLI, and hosted tools share the same saved-
workbook `/writing-tools/analysis`, `/preview`, and `/apply` contracts.

- **Spelling** uses a small built-in typo dictionary for common mistakes.
- **Grammar** catches repeated words and extra spacing.
- **Style** suggests simpler replacements for verbose phrases such as
  "in order to" or "due to the fact that".
- **Citation** flags evidence claims such as "according to..." and can insert
  `[citation needed]`, an inline author/year citation, or a bibliography entry.
- **Local assistant** produces summary, outline, and selected-range rewrite
  plans. Preview never mutates. **Insert result** explicitly approves a plan;
  apply requires its fingerprint, unchanged source, current revision, and a
  replay-safe request id.

Editing actions respect the active workbook access state. View-only users can
inspect suggestions and drafts but cannot apply changes.

Agents use `typewriter writing-analyze`, `writing-preview`, and
`writing-apply`, or the matching `typewriter_*_writing*` hosted tools. Apply
rejects tampered plans, stale revisions, changed source text, and reused request
ids with different intent.

## Keyboard shortcuts and command palette

**Tools → Keyboard shortcuts…** opens a searchable Typewriter command finder.
The search field receives focus on open, filters rows as the user types, and
each visible row can be activated with the keyboard or pointer.

The shell command palette also receives Typewriter-owned items through the
surface registry hook. Searching for commands such as "writing tools",
"comment", "mobile offline", "smart insert", "version history", or
"fidelity" runs the same handlers as the menubar and shortcut dialog.

Editor-scoped routes added for Google Docs parity:

| Shortcut | Action |
|---|---|
| `Ctrl-/` | Open Keyboard shortcuts |
| `Ctrl-Alt-M` | Add comment to selected text |
| `Ctrl-Alt-Shift-M` | Show threaded comments |
| `Ctrl-Alt-W` | Open Writing tools |
| `Ctrl-Alt-O` | Open Mobile/offline readiness |
| `Ctrl-Alt-P` | Open Publish/admin readiness |
| `Ctrl-Alt-I` | Open Smart insert |
| `Ctrl-Alt-T` | Open Templates and reusable blocks |
| `Ctrl-Alt-V` | Open Version history |
| `Ctrl-Alt-F` | Open Import/export fidelity report |
| `Ctrl-Alt-S` | Open Word count |

## Mobile/offline readiness

**Tools → Mobile/offline readiness…** opens an in-page strategy surface for
P2 mobile and offline parity. It does not pretend that full offline editing is
complete; instead it makes the readiness contract visible and testable.

The dialog reports:

- **Form factor** from the current viewport and touch capability: Desktop,
  Tablet, or Phone.
- **Network** from `navigator.onLine`, with a Recheck action that updates when
  the browser is placed into offline mode.
- **Mobile layout** rules for toolbar scroll, stacked rails, constrained
  dialogs, and reachable primary actions.
- **Offline cache** posture for IndexedDB/Yjs update storage and service-worker
  shell caching when a deployment registers one.
- **Conflict resolution** strategy: queue local Yjs updates while offline,
  replay on reconnect, and keep the shared-y-updates channel as the merge
  authority instead of replacing JSON snapshots.
- **Reconnect behavior** requirements: show pending sync, flush autosave and
  collab updates on reconnect, then clear pending state only after server
  acknowledgement.
- **Verification matrix** for 1440px desktop, 760px narrow web, 390px phone
  width, browser offline simulation, and future reconnect convergence gates.

The checked-in smoke covers both the pure strategy analyzer and the visible
dialog at desktop, offline, and 390px phone widths.

## Publish/admin readiness

**Tools → Publish/admin readiness…** opens an in-page enterprise decision
surface for P2 publish, admin, security, and ecosystem parity. It makes the
current contract explicit instead of implying that public publishing,
e-signature, external connector, audit-log, or encryption-at-rest work is
complete.

The dialog reports:

- **Role, export policy, admin surface, and workbook scope** from the active
  workbook access state.
- **Publish to web** as planned architecture: signed public route, admin
  publish/unpublish controls, snapshot lifecycle, cache invalidation, and
  iframe policy.
- **E-signature** as a product/legal decision: provider, signer identity,
  audit trail, retention, and document-lock semantics.
- **Download restrictions** as ready Typewriter behavior: export, print, and
  file actions are gated through workbook access state.
- **Audit/admin controls** as a partial platform surface: sharing roles exist,
  but publish changes, export attempts, signature events, and policy edits
  need durable admin events and review surfaces.
- **Encryption posture** as a platform security decision: HTTPS is not enough;
  at-rest encryption, key management, backup, residency, and publish/signature
  blocking rules need a written policy.
- **External integrations and ecosystem hooks** as two tracks: xApps-native
  smart insert, command palette entries, and live surface embeds are ready;
  Google Workspace-style add-ons, Drive/Calendar/Gmail hooks, DLP, and
  marketplace connectors need an API, consent, revocation, and audit contract.

The checked-in smokes cover the pure analyzer, the visible dialog, command
palette discoverability, `Ctrl-Alt-P`, and narrow layout without document
horizontal overflow.

## Page setup

Visual pagination, headers / footers, auto page numbering, custom page
size, margins, and `@page`-CSS print/PDF.

- **Visual pagination** — `browser-pagination.ts` measures page heights
  off the editor scroll and shifts content into virtual pages. The
  current page index, page count, and per-page first-block id are
  exposed via a `pageInfo` event for the status bar.
- **Headers / footers** — authored in-place in the page margin bands, not in
  Page setup. `header` / `footer` each carry an independent ProseMirror JSON
  document. Optional `differentFirstPage` and `differentEvenOdd` toggles add
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

Opens via the Sheet menu Page setup command. It owns page geometry, margin
sizes, header/footer distances, header/footer show/hide toggles, and page
number settings; header/footer authoring stays in the page bands. Sticky-header /
scrollable-body / sticky-footer layout with
`max-height: min(90vh, 800px)`; works at 1024×600, 1024×900, 1200×768
viewports. Smoke covers viewport-aware layout.

## Workbook + Sheet menu

The menubar splits into **Workbook** and **Sheet** dropdowns:

```
Workbook ▸                         Sheet ▸
  New workbook…                      New current sheet…
  Open workbook…                     ─
  Save              Cmd-S            Open ▸
  Save As…                             Open in new sheet…
  ─                                    Replace current sheet content…
  Recent workbooks ▸                   Import editable Word document (.docx)
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
                                     Version history…
                                     Import/export fidelity report…
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

## Right-click context menu

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
- **On an image** — Replace, Align L/C/R, Resize, Remove, and Text wrapping (Break text, Wrap left, Wrap right, In line with text). "In line with text" converts the block image into an inline `imageInline` node inside the paragraph so text flows on both sides; choosing any block wrap mode converts it back, splitting the paragraph around the image. Alignment and resize handles apply to block images only.

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
| `Ctrl-/` | Open Keyboard shortcuts |
| `Ctrl-Alt-M` | Add comment |
| `Ctrl-Alt-Shift-M` | Show comments |
| `Ctrl-Alt-W` | Writing tools |
| `Ctrl-Alt-O` | Mobile/offline readiness |
| `Ctrl-Alt-I` | Smart insert |
| `Ctrl-Alt-T` | Templates and reusable blocks |
| `Ctrl-Alt-V` | Version history |
| `Ctrl-Alt-F` | Import/export fidelity report |
| `Ctrl-Alt-S` | Word count |
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

## Status bar

![Typewriter status bar](/help-assets/screenshots/typewriter-status-bar.png)

The status bar is a persistent 32 px strip pinned to the bottom of the
typewriter host. It never overlaps the page — `browser-status-bar.ts`
appends it to the host element outside the page-chrome area.

### Left cluster — document statistics

| Slot | Content | Interaction |
|---|---|---|
| **Page indicator** | `Page N of M` | Shows the current page and total page count. |
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

The top **View → View mode** flyout mirrors the status-bar selector, exposing
**Page**, **Web**, and **Print preview** through the same persisted view state.
Changing either control updates the other immediately.

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

Headless edits use block indices from `outline`; range commands use exact
`[from, to)` text offsets within one block. Mutations are revision-guarded,
request-idempotent, and atomic. Interactive undo/redo remains local to the
browser editor session and is not exposed as a public transaction API.

View/query automation uses `view`, `set-view`, `outline --filter`, `find`,
`replace-query`, and `statistics`. Page/Web/Print, Focus, zoom, document tabs,
and navigation-rail collapse are durable settings; outline filters, the active
find match, and exact rendered page count are browser-session-only. The
statistics contract reports exact page count as browser-only.

<!-- typewriter-cli:start -->

> This block is generated from the same `TYPEWRITER_CLI_COMMANDS` array that
> backs the `xapps typewriter <command> --help` runtime. Edit
> `packages/xapps-surface-typewriter/src/cli/commands.ts`, then re-run
> `tools/test-typewriter-help-content.ts` (or `npm run sync:assets` after build)
> to regenerate. Do not hand-edit between the start/end markers.

### `xapps typewriter export`

Export a typewriter document to docx, html, md, txt, or json.

**Usage:**

```
xapps typewriter export <sheet> <format> [--out <path>] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<format>` | yes | One of docx, html, md, txt, json. |
| `[--out <path>]` | no | Write the exported body to this file path; otherwise print to stdout. |

**Notes:**

- json emits the raw ProseMirror document; html emits a <body>-fragment ready to wrap; md emits CommonMark with GFM tables.
- DOCX is binary and requires --out <path>; HTML/Markdown/TXT/JSON may print to stdout.

**Examples:**

```sh
xapps typewriter export "Draft" md --out draft.md
xapps typewriter export "Draft" docx --out draft.docx
xapps typewriter export "Draft" json
```

### `xapps typewriter import`

Replace a typewriter document with the contents of a file.

**Usage:**

```
xapps typewriter import <sheet> <path> [--format docx|html|md|txt|json] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<path>` | yes | Local file path to import. Format is inferred from the extension unless --format is set. |
| `[--format docx|html|md|txt|json]` | no | Force the import format when the extension is ambiguous or wrong. |

**Notes:**

- Import REPLACES the document. To merge, export to md, edit locally, and import the merged file.
- DOCX import is size-limited, rejects encrypted/legacy packages, and replaces the document atomically.

**Examples:**

```sh
xapps typewriter import "Draft" notes.md
xapps typewriter import "Draft" draft.docx --verify
xapps typewriter import "Draft" pasted.html --format html
```

### `xapps typewriter fidelity-report`

Report import/export fidelity risks and supported/browser-only/unsupported paths.

**Usage:**

```
xapps typewriter fidelity-report <sheet> [format] [--format html|md|docx|pdf|txt|json|rtf|odt] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `[format]` | no | Optional format focus: html, md/markdown, docx, pdf, txt, json, rtf, or odt. |
| `[--format <format>]` | no | Alternative flag form for selecting the focused format. |
| `[--json]` | no | Emit the structured report object instead of human-readable text. |

**Notes:**

- DOCX is available through server-safe API/SDK/CLI/toolkit paths; PDF remains browser print-only; RTF and ODT are explicit unsupported interchange formats.
- Use this before Markdown/TXT export when a document contains tables, images, page chrome, review metadata, or live surface embeds.

**Examples:**

```sh
xapps typewriter fidelity-report "Draft"
xapps typewriter fidelity-report "Draft" markdown
xapps typewriter fidelity-report "Draft" --format docx --json
```

### `xapps typewriter wordcount`

Print word, character, and paragraph counts as JSON.

**Usage:**

```
xapps typewriter wordcount <sheet> [--json]
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
xapps typewriter set-page-size <sheet> <size> [portrait|landscape] [--request-id <id> --expected-revision <n>] [--verify] [--json]
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
xapps typewriter set-margins <sheet> <top> <right> <bottom> <left> [--request-id <id> --expected-revision <n>] [--verify] [--json]
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
xapps typewriter set-page-numbers <sheet> [--placement header|footer] [--align left|center|right] [--format <template>] [--start-at <n>] [--suppress-first] [--disable] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `[--placement header|footer]` | no | Where to render numbers; defaults to footer. |
| `[--align left|center|right]` | no | Horizontal alignment within the header/footer; defaults to center. |
| `[--format <template>]` | no | Template with {X} (current page) and {Y} (total pages); defaults to "Page {X} of {Y}". |
| `[--start-at <n>]` | no | Positive starting page number; defaults to 1. |
| `[--suppress-first]` | no | Do not render a number on the first page. |
| `[--disable]` | no | Disable page numbering. |

**Notes:**

- Page numbering is rendered by `browser-pagination.ts` at print/PDF time and live in the page-chrome view.

**Examples:**

```sh
xapps typewriter set-page-numbers "Draft"
xapps typewriter set-page-numbers "Draft" --placement header --align right --format "{X}"
```

### `xapps typewriter discover-embed-sources`

Discover same-workbook Spreadsheet, Kanban, and Dashboard embed sources.

**Usage:**

```
xapps typewriter discover-embed-sources <sheet> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |

### `xapps typewriter insert-embed`

Insert a typed same-workbook surface embed at a block position.

**Usage:**

```
xapps typewriter insert-embed <sheet> <spreadsheet-range|kanban-board|kanban-column|kanban-card|dashboard-widget> <reference-json> [--mode snapshot|live] [--position <position>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<kind>` | yes | One of spreadsheet-range|kanban-board|kanban-column|kanban-card|dashboard-widget. |
| `<reference-json>` | yes | JSON reference with sheetId and exact range/column/card/widget selector. |
| `[--mode snapshot|live]` | no | Snapshot (default) or live refresh behavior. |
| `[--position <position>]` | no | Zero-based block index or end; omit to append. |

**Examples:**

```sh
xapps typewriter insert-embed "Draft" spreadsheet-range "Budget!A1:C5" --mode live
xapps typewriter insert-embed "Draft" kanban-card '{"sheetId":"Board","cardId":"card-1"}'
```

### `xapps typewriter list-embeds`

List typed embeds with stable ids and source status.

**Usage:**

```
xapps typewriter list-embeds <sheet> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |

### `xapps typewriter get-embed`

Read one typed embed by stable id.

**Usage:**

```
xapps typewriter get-embed <sheet> <embed-id> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<embed-id>` | yes | Stable embed id from list-embeds. |

### `xapps typewriter update-embed`

Update an embed reference, mode, or block position.

**Usage:**

```
xapps typewriter update-embed <sheet> <embed-id> [--kind <kind> --reference <json>] [--mode snapshot|live] [--position <position>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<embed-id>` | yes | Stable embed id. |
| `[--kind <kind> --reference <json>]` | no | Replacement typed reference; supply kind with reference. |
| `[--mode snapshot|live]` | no | Replacement refresh behavior. |
| `[--position <position>]` | no | Zero-based block index or end. |

### `xapps typewriter remove-embed`

Remove one typed embed by stable id.

**Usage:**

```
xapps typewriter remove-embed <sheet> <embed-id> [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<embed-id>` | yes | Stable embed id. |

### `xapps typewriter refresh-embed`

Refresh a live or snapshot embed from its same-workbook source.

**Usage:**

```
xapps typewriter refresh-embed <sheet> <embed-id> [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<embed-id>` | yes | Stable embed id. |

### `xapps typewriter open-embed-reference`

Resolve the saved-route target for an embed source.

**Usage:**

```
xapps typewriter open-embed-reference <sheet> <embed-id> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<embed-id>` | yes | Stable embed id. |

### `xapps typewriter smart-items`

List Today and real sibling-sheet Smart Insert items.

**Usage:**

```
xapps typewriter smart-items <sheet> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |

### `xapps typewriter insert-smart-item`

Insert a currently available Smart Insert item at a block boundary.

**Usage:**

```
xapps typewriter insert-smart-item <sheet> <item-id> [position|end] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<item-id>` | yes | Id returned by smart-items. |
| `[position|end]` | no | 0-based block boundary; defaults to end. |

### `xapps typewriter templates`

List five built-in templates and saved reusable blocks.

**Usage:**

```
xapps typewriter templates <sheet> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |

### `xapps typewriter template-preview`

Preview a built-in template or reusable block.

**Usage:**

```
xapps typewriter template-preview <sheet> <template-id> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<template-id>` | yes | Built-in or custom template id. |

### `xapps typewriter apply-template`

Insert a template at a block boundary or replace the document.

**Usage:**

```
xapps typewriter apply-template <sheet> <template-id> <insert|replace> [position|end] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<template-id>` | yes | Built-in or custom template id. |
| `<insert|replace>` | yes | Application mode. |
| `[position|end]` | no | Insert position; ignored for replace. |

### `xapps typewriter save-reusable-block`

Save selected ProseMirror nodes as a reusable block.

**Usage:**

```
xapps typewriter save-reusable-block <sheet> <name> <content-json> [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<name>` | yes | Unique reusable block name. |
| `<content-json>` | yes | JSON array of selected ProseMirror nodes. |

### `xapps typewriter rename-reusable-block`

Rename a saved reusable block.

**Usage:**

```
xapps typewriter rename-reusable-block <sheet> <block-id> <name> [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<block-id>` | yes | Saved reusable block id. |
| `<name>` | yes | New unique name. |

### `xapps typewriter delete-reusable-block`

Delete a saved reusable block.

**Usage:**

```
xapps typewriter delete-reusable-block <sheet> <block-id> [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<block-id>` | yes | Saved reusable block id. |

### `xapps typewriter media`

List scoped images with stable path ids and fallback status.

**Usage:**

```
xapps typewriter media <sheet> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |

### `xapps typewriter insert-image`

Upload or import and insert a workbook-scoped image.

**Usage:**

```
xapps typewriter insert-image <sheet> <path|url|upload-ref> [position|end] [--alt <text> --width <px> --height <px> --align left|center|right --wrap break|wrap-left|wrap-right --kind block|inline] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<path|url|upload-ref>` | yes | Local image, HTTP(S) URL, or durable /uploads/ reference. |
| `[position|end]` | no | 0-based block boundary; defaults to end. |

### `xapps typewriter edit-image`

Replace, describe, resize, align, wrap, or convert a scoped image.

**Usage:**

```
xapps typewriter edit-image <sheet> <media-id> [--source <path|url|upload-ref> --alt <text> --width <px> --height <px> --align left|center|right --wrap break|wrap-left|wrap-right --kind block|inline] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<media-id>` | yes | Stable path id returned by media. |

### `xapps typewriter remove-image`

Remove a scoped image from a Typewriter document.

**Usage:**

```
xapps typewriter remove-image <sheet> <media-id> [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<media-id>` | yes | Stable path id returned by media. |

### `xapps typewriter navigation`

List bookmarks, cross-references, TOCs, and broken/stale diagnostics.

**Usage:**

```
xapps typewriter navigation <sheet> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |

### `xapps typewriter create-bookmark`

Create a named bookmark with a stable identity at an exact text offset.

**Usage:**

```
xapps typewriter create-bookmark <sheet> <name> <index> [offset] [--id <bookmark-id>] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<name>` | yes | Unique non-reserved bookmark name. |
| `<index>` | yes | 0-based text block index. |
| `[offset]` | no | Text offset; defaults to 0. |

### `xapps typewriter rename-bookmark`

Rename a stable bookmark and refresh automatic reference labels.

**Usage:**

```
xapps typewriter rename-bookmark <sheet> <bookmark-id> <name> [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<bookmark-id>` | yes | Stable bookmark id. |
| `<name>` | yes | New unique name. |

### `xapps typewriter delete-bookmark`

Delete a bookmark while preserving broken-reference diagnostics.

**Usage:**

```
xapps typewriter delete-bookmark <sheet> <bookmark-id> [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<bookmark-id>` | yes | Stable bookmark id. |

### `xapps typewriter insert-cross-reference`

Insert a stable cross-reference to an existing bookmark.

**Usage:**

```
xapps typewriter insert-cross-reference <sheet> <bookmark-id> <index> <offset> [text] [--id <reference-id>] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<bookmark-id>` | yes | Target bookmark id. |
| `<index>` | yes | 0-based text block index. |
| `<offset>` | yes | Exact text offset. |
| `[text]` | no | Optional custom label; defaults to the bookmark name. |

### `xapps typewriter update-cross-reference`

Retarget or relabel an existing cross-reference.

**Usage:**

```
xapps typewriter update-cross-reference <sheet> <reference-id> [--bookmark-id <id> --text <label>] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<reference-id>` | yes | Stable cross-reference id. |
| `[--bookmark-id <id> --text <label>]` | no | At least one update field is required. |

### `xapps typewriter insert-toc`

Insert a generated TOC snapshot from non-empty headings.

**Usage:**

```
xapps typewriter insert-toc <sheet> <index> [--id <toc-id>] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<index>` | yes | 0-based block insertion index. |

### `xapps typewriter refresh-toc`

Refresh a generated TOC after heading edits.

**Usage:**

```
xapps typewriter refresh-toc <sheet> <toc-id> [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<toc-id>` | yes | Stable TOC id. |

### `xapps typewriter insert-structure`

Insert a special character or structural block through the guarded SDK.

**Usage:**

```
xapps typewriter insert-structure <sheet> <special-character|code-block|blockquote|horizontal-rule|page-break> <index> [value] [--offset <n>] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<kind>` | yes | special-character | code-block | blockquote | horizontal-rule | page-break. |
| `<index>` | yes | Block index or insertion boundary. |
| `[value]` | no | Character or optional code/quote text. |

### `xapps typewriter set-header-footer`

Configure a rich header or footer with optional first-page and even-page variants.

**Usage:**

```
xapps typewriter set-header-footer <sheet> <header|footer> <on|off> [--content <doc-json> --different-first --first-content <doc-json> --different-even --even-content <doc-json> --from-edge <px>] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |
| `<header|footer>` | yes | Page region to configure. |
| `<on|off>` | yes | Enable or disable the region. |

### `xapps typewriter set-ruler`

Set paragraph ruler indents and typed tab stops at an exact block index.

**Usage:**

```
xapps typewriter set-ruler <sheet> <index> [--first-line <pt|null> --left <pt|null> --right <pt|null> --tab-stops <json|null>] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |
| `<index>` | yes | 0-based paragraph or heading index. |

### `xapps typewriter view`

Read durable Page/Web/Print, focus, zoom, document-tab, and navigation-rail state.

**Usage:**

```
xapps typewriter view <sheet> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |

### `xapps typewriter set-view`

Atomically patch durable Typewriter view and document-navigation settings.

**Usage:**

```
xapps typewriter set-view <sheet> [--mode page|web|print --focus true|false --zoom 50..200 --navigation expanded|collapsed --active-tab <id> --doc-tabs <json>] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |

### `xapps typewriter find`

Return typed find matches with stable text-node paths and offsets.

**Usage:**

```
xapps typewriter find <sheet> <query> [--case-sensitive --overlap] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |
| `<query>` | yes | Literal text to find. |

### `xapps typewriter statistics`

Read word, character, paragraph, heading, reading-time, and honest page statistics.

**Usage:**

```
xapps typewriter statistics <sheet> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |

### `xapps typewriter replace-query`

Atomically replace one selected find match or every non-overlapping match.

**Usage:**

```
xapps typewriter replace-query <sheet> <query> [replacement] [--one --match-index <n> --case-sensitive] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |
| `<query>` | yes | Literal text to replace. |
| `[replacement]` | no | Replacement text; omit to delete. |

### `xapps typewriter review-state`

List Typewriter review mode, permissions, comments, suggestions, and immutable provenance.

**Usage:**

```
xapps typewriter review-state <sheet> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |

### `xapps typewriter review-action`

Apply a guarded comment, suggestion, reaction, assignment, resolution, or review-mode action through the typed SDK.

**Usage:**

```
xapps typewriter review-action <sheet> <action> [--mode editing|suggesting|viewing --anchor <json> --text <text> --comment-id <id> --suggestion-id <id> --reply-id <id> --reaction <name> --active true|false --assignee <json|null> --done true|false] [--actor-id <id> --actor-name <name>] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |
| `<action>` | yes | Closed action discriminator; use --help for the supported list. |
| `[--anchor <json> --text <text>]` | no | Range/node anchor and content for create actions. |
| `[--comment-id <id> --suggestion-id <id>]` | no | Stable target id for lifecycle actions. |

**Notes:**

- Create anchors use {"path":[0,0],"from":0,"to":5,"quote":"Hello"}; stale or deleted anchors fail with 409.
- The CLI always sends explicit actor identity; actor-id defaults to xapps-cli.

### `xapps typewriter history-state`

List durable Typewriter snapshots, restore activity, actors, and permissions.

**Usage:**

```
xapps typewriter history-state <sheet> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |

### `xapps typewriter history-action`

Create or restore a durable guarded Typewriter snapshot through the typed SDK.

**Usage:**

```
xapps typewriter history-action <sheet> <snapshot_create|snapshot_restore> [--name <name> --snapshot-id <id>] [--actor-id <id> --actor-name <name>] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |
| `<action>` | yes | snapshot_create or snapshot_restore. |
| `[--name <name> --snapshot-id <id>]` | no | Snapshot creation name or stable snapshot target. |

**Notes:**

- The CLI always sends explicit actor identity; actor-id defaults to xapps-cli.

### `xapps typewriter writing-analyze`

Analyze spelling, grammar, style, citations, summary, outline, and rewrite drafts without mutation.

**Usage:**

```
xapps typewriter writing-analyze <sheet> [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |

**Examples:**

```sh
xapps typewriter writing-analyze "Draft" --json
```

### `xapps typewriter writing-preview`

Create a deterministic, fingerprinted writing plan without changing the document.

**Usage:**

```
xapps typewriter writing-preview <sheet> <suggestion|summary|outline|rewrite> [--suggestion-id <id>] [--block-index <n> --from <n> --to <n>] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |
| `<kind>` | yes | suggestion, summary, outline, or rewrite. |
| `[--suggestion-id <id>]` | no | Server analysis suggestion id for suggestion plans. |
| `[--block-index <n> --from <n> --to <n>]` | no | Required non-empty text range for rewrite plans. |

**Examples:**

```sh
xapps typewriter writing-preview "Draft" suggestion --suggestion-id spelling-1 --json
xapps typewriter writing-preview "Draft" rewrite --block-index 0 --from 0 --to 42 --json
```

### `xapps typewriter writing-apply`

Explicitly approve and atomically apply a server-issued writing plan.

**Usage:**

```
xapps typewriter writing-apply <sheet> <plan-json> [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact Typewriter sheet name. |
| `<plan-json>` | yes | Unmodified plan object returned by writing-preview. |

**Notes:**

- The SDK forces approved=true; stale revisions, changed source text, tampered plans, and request-id conflicts are rejected.

**Examples:**

```sh
xapps typewriter writing-apply "Draft" "$PLAN_JSON" --verify --json
```

### `xapps typewriter outline`

Print the document outline, heading jump targets, and optional filtered result as JSON.

**Usage:**

```
xapps typewriter outline <sheet> [--filter <text>] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |

**Notes:**

- Without --filter, output remains the block array used by granular edits. With --filter, output includes filtered blocks and heading jump targets.

**Examples:**

```sh
xapps typewriter outline "Draft"
```

### `xapps typewriter apply-ops`

Atomically apply a non-empty JSON array from the typed Typewriter document-op union.

**Usage:**

```
xapps typewriter apply-ops <sheet> <ops-json> [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name from `xapps sheets`. |
| `<ops-json>` | yes | JSON array of typed document operations; the whole batch commits or rolls back. |

**Examples:**

```sh
xapps typewriter apply-ops "Draft" '[{"op":"set_paragraph_style","index":0,"style":"title"}]'
```

### `xapps typewriter append-paragraph`

Append a paragraph (optionally with text) to the end of the document.

**Usage:**

```
xapps typewriter append-paragraph <sheet> [text] [--request-id <id> --expected-revision <n>] [--verify] [--json]
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

Insert a paragraph at an exact 0-based block boundary from 0 through the document length.

**Usage:**

```
xapps typewriter insert-paragraph <sheet> <index> [text] [--request-id <id> --expected-revision <n>] [--verify] [--json]
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
xapps typewriter delete-block <sheet> <index> [--request-id <id> --expected-revision <n>] [--verify] [--json]
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
xapps typewriter set-block <sheet> <index> <type> [--level <1-6>] [--request-id <id> --expected-revision <n>] [--verify] [--json]
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
xapps typewriter set-align <sheet> <index> <left|center|right|justify> [--request-id <id> --expected-revision <n>] [--verify] [--json]
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
xapps typewriter format-block <sheet> <index> <marks> [--mode add|remove|set] [--request-id <id> --expected-revision <n>] [--verify] [--json]
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

### `xapps typewriter set-style`

Set paragraph, Title, Subtitle, or Heading 1–6 style on a text block.

**Usage:**

```
xapps typewriter set-style <sheet> <index> <style> [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<index>` | yes | 0-based block index from `outline`. |
| `<style>` | yes | paragraph | title | subtitle | heading-1 | heading-2 | heading-3 | heading-4 | heading-5 | heading-6 |

**Examples:**

```sh
xapps typewriter set-style "Draft" 0 title
```

### `xapps typewriter format-range`

Apply marks, font, size, color, highlight, or link to a deterministic block-text range.

**Usage:**

```
xapps typewriter format-range <sheet> <index> <from> <to> [--marks <csv> --mode add|remove|set] [--font-family <value>] [--font-size <value>] [--color <value>] [--highlight <value>] [--link <value>] [--new-tab] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<index>` | yes | 0-based block index from `outline`. |
| `<from>` | yes | Inclusive 0-based text offset. |
| `<to>` | yes | Exclusive text offset; must be greater than from. |

**Examples:**

```sh
xapps typewriter format-range "Draft" 0 0 8 --marks bold --font-size 18 --color "#1f2937" --link https://example.com --new-tab
```

### `xapps typewriter set-line-spacing`

Set or reset line spacing on a block.

**Usage:**

```
xapps typewriter set-line-spacing <sheet> <index> <spacing> [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<index>` | yes | 0-based block index. |
| `<spacing>` | yes | A 0.5–10 line-height multiple, or reset. |

**Examples:**

```sh
xapps typewriter set-line-spacing "Draft" 1 1.5
```

### `xapps typewriter adjust-indent`

Indent or outdent a block by one or more levels.

**Usage:**

```
xapps typewriter adjust-indent <sheet> <index> <indent|outdent> [amount] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<index>` | yes | 0-based block index. |
| `<direction>` | yes | indent | outdent. |
| `[amount]` | no | Integer levels, default 1. |

**Examples:**

```sh
xapps typewriter adjust-indent "Draft" 1 indent 2
```

### `xapps typewriter set-list`

Convert a block or existing list between bullet, ordered, checklist, and plain blocks.

**Usage:**

```
xapps typewriter set-list <sheet> <index> <bullet|ordered|checklist|none> [--style <style>] [--checked true|false] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<index>` | yes | 0-based block index. |
| `<list-type>` | yes | bullet | ordered | checklist | none. |

**Examples:**

```sh
xapps typewriter set-list "Draft" 2 checklist --checked false
```

### `xapps typewriter insert-break`

Insert a horizontal rule or page break at a block boundary.

**Usage:**

```
xapps typewriter insert-break <sheet> <index> <horizontal|page> [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<index>` | yes | Insertion index from 0 through the block count. |
| `<break-type>` | yes | horizontal | page. |

**Examples:**

```sh
xapps typewriter insert-break "Draft" 3 page
```

### `xapps typewriter replace-range`

Replace one deterministic block-text range while preserving the first selected run’s marks.

**Usage:**

```
xapps typewriter replace-range <sheet> <index> <from> <to> [text] [--request-id <id> --expected-revision <n>] [--verify] [--json]
```

**Arguments:**

| Argument | Required | Description |
|---|---|---|
| `<sheet>` | yes | Exact typewriter sheet name. |
| `<index>` | yes | 0-based block index. |
| `<from>` | yes | Inclusive 0-based text offset. |
| `<to>` | yes | Exclusive text offset. |
| `[text]` | no | Replacement text; omit to delete the range. |

**Examples:**

```sh
xapps typewriter replace-range "Draft" 0 0 5 "Launch"
```

### `xapps typewriter replace-text`

Plain-text find/replace across the document (all matches by default).

**Usage:**

```
xapps typewriter replace-text <sheet> <find> [replace] [--first] [--request-id <id> --expected-revision <n>] [--verify] [--json]
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
- **DOCX import/export is public and bounded.** API, SDK, CLI, MCP/toolkit,
  and browser flows share the same package validation and fidelity report.
- **RTF and ODT are unsupported.** The fidelity report documents this product
  decision and points users to DOCX, HTML, Markdown, or JSON alternatives.
- **PDF is browser print-only.** The CLI/server path does not generate PDFs;
  use Typewriter → Print in the live app for visual PDF output.
- **Writing tools are local heuristics.** The current implementation is a
  deterministic spelling/grammar/style/citation assistant, not a remote LLM,
  live translation engine, or voice typing system.
- **Surface embed export** uses the latest saved snapshot fallback. Live
  embeds continue to refresh inside the app, but Markdown/DOCX exports remain
  placeholder-based.
- **Publish/admin readiness is a decision surface.** Download restrictions and
  xApps-native ecosystem hooks are implemented, but public publish URLs,
  e-signature envelopes, admin audit retention, external connectors, and
  encryption-at-rest/KMS commitments remain platform work.
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
| Smart insert and chips | `src/runtime/browser-smart-insert.ts` |
| Insert dialogs (image / link / embed / bookmark / cross-ref / special chars) | `src/runtime/browser-{image,link-dialog,insert-embed-dialog,bookmark-dialog,special-chars}.ts` |
| Find / review / stats dialogs | `src/runtime/browser-{find-replace,review-comments,document-stats-dialog}.ts` |
| Writing tools | `src/writing-tools.ts`, `src/runtime/browser-writing-tools.ts` |
| Keyboard shortcuts and command finder | `src/runtime/browser-keyboard-shortcuts.ts`, `src/runtime/browser-menu-handlers.ts` |
| Mobile/offline readiness | `src/mobile-offline-strategy.ts`, `src/runtime/browser-mobile-offline-readiness.ts` |
| Publish/admin readiness | `src/publish-admin-ecosystem.ts`, `src/runtime/browser-publish-admin-readiness.ts` |
| Tables | `src/runtime/browser-table*.ts` |
| Surface embed mechanism | `src/runtime/browser-surface-embed.ts` + `src/runtime/browser-insert-embed-snapshots.ts` |
| HTML / Markdown import-export | `src/runtime/browser-import-export-{html,md}.ts` |
| Import/export fidelity report | `src/import-export-fidelity.ts`, `src/runtime/browser-import-export-fidelity.ts` |
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
