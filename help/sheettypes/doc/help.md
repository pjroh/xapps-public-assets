## 📄 Wiki

### Pages, briefs, SOPs, and knowledge entries

Wiki sheets are the narrative layer of an xApps workbook. They are designed for:

- project briefs
- meeting notes
- SOPs
- research notes
- release notes
- wiki pages that link to the rest of the workbook

> 🤖 Agent example: an agent can draft a brief, structure sections and tables, pull workbook facts into the page, and leave the human editor with a clean wiki page instead of raw notes.

![Wiki sheet showing a structured page with heading, narrative blocks, and embedded table content](/help-assets/screenshots/doc-sheet.png)

### ✍️ One Wiki sheet can contain many pages

Each Wiki sheet is a small internal wiki workspace. Keep many related pages inside one Wiki sheet, and use separate Wiki sheets only when you want separate workspaces.

- use the page rail to switch pages inline
- page operations target the active page
- legacy `docTitle` / `docBlocks` fields still mirror the active page for compatibility

### 🔗 Wiki links

Wiki supports internal links:

- `[[Page]]` links to another page
- `[[Page#Section]]` links to a heading inside a page
- `[[#Section]]` links to a heading in the current page
- `[[Page|Label]]` adds custom link text
- `[[Page#Section|Label]]` links to a section with custom link text

When you create a page from selected text, the menu asks for the new page title instead of assuming the highlighted text is the title. The highlighted text remains the inline link label.

### 🧱 Blocks

Wiki pages are block-based. Current block types include:

- paragraph
- heading 1
- heading 2
- bulleted list
- checklist
- quote
- code block
- divider
- callout
- toggle list
- image

### 📝 Inline formatting

Text within blocks supports rich inline formatting:

- **bold**, **italic**, **underline**, **strikethrough**
- **inline code**
- **hyperlinks**

Apply formatting via the floating format bar or keyboard shortcuts (`Ctrl/Cmd + B`, `I`, `U`, etc.).

### 📊 Table blocks

Insert a table with the `/table` slash command. Tables support:

- header row toggle
- add and delete rows and columns
- `Tab` to navigate between cells

### 🖼️ Image blocks

Image blocks support:

- sizing — small, medium, large, or full width
- alignment — left, center, or right
- drag-drop and paste to insert images directly

### 💬 Block comments

Hover over any block to reveal the comment button. Comments support threaded discussions per block for feedback and review.

### 🎨 Block colors

Apply a background tint to any block for visual emphasis. Useful for highlighting key sections or creating visual groupings.

### ↕️ Block reordering

Drag blocks to reorder them within a page.

### 📤 Export

- **PDF export** — toolbar button or `Wiki` menu
- **DOCX export** — toolbar button or `Wiki` menu (Word-compatible HTML)

### 🧠 Wiki-style page shell

The Wiki sheet is more than a blank editor. Each page also has:

- a cover tone
- an accent color
- page summary text
- editable properties
- linked sheets
- a live outline generated from headings
- page templates for common wiki page shapes

### ⚡ Editing flow

The editor is designed to feel like one flowing page instead of a stack of form cards:

- type directly into a block
- press `Enter` on a heading to continue below with a paragraph
- press `Enter` on a checklist item to add the next checklist item
- use `/` inside a text block to open the slash menu
- use markdown-style shortcuts like `#`, `##`, `>`, `-`, `[]`, and ``` to convert the current block
- use `Ctrl/Cmd + Z` and `Ctrl/Cmd + Shift + Z` to undo and redo Wiki edits while the editor has focus
- hover or focus a block to reveal type and action controls

### 🪄 Templates

Built-in templates currently include:

- Project Brief
- Meeting Notes
- SOP
- Research Note
- Release Notes

Templates replace the current active page structure, so use them early or after confirming a reset.

### 🎨 Page styling

Wiki pages support page-level controls for:

- font family
- text scale
- page width
- cover tone
- accent color
- icon
- title
- summary

### 🏷️ Properties and linked sheets

Use the page-header **Properties** control to turn a freeform page into a structured wiki entry without putting the metadata editor in the reading body. Common fields include:

- status
- owner
- audience
- source
- review cadence

Linked sheets let one Wiki page act as the front door to related workbook surfaces, like a timeline, dashboard, floor plan, or spreadsheet.

### 🔗 Great uses inside xApps

Wiki pages work especially well when paired with other sheet types:

- write a project brief, then link to a timeline, kanban board, and dashboard
- keep renovation notes next to a floor plan, gallery, and budget spreadsheet
- store campaign strategy beside a content calendar, presentation, and design canvas

---

### 💻 CLI Commands

The Wiki / Doc surface ships 23 CLI commands. They share the same `xapps <command> <sheet> ...` pattern as the spreadsheet/kanban/canvas surfaces. The `<sheet>` is the wiki sheet name in the active workbook.

Bad input is rejected before mutation. Page and block IDs must be non-empty, non-numeric strings without `/`; `--index` values must be non-negative integers; bool flags accept true/false-style values; JSON options must be the documented object shapes. With `--json`, CLI errors are emitted as structured error envelopes.

#### Pages

```bash
xapps doc-add-page <sheet> <title> [--icon <emoji>] [--summary <text>] [--index <n>] [--set-active]
xapps doc-list-pages <sheet> [--json]
xapps doc-get-page <sheet> <pageId> [--json]
xapps doc-rename-page <sheet> <pageId> --title <title> [--icon <emoji>] [--summary <text>]
xapps doc-delete-page <sheet> <pageId>
xapps doc-set-active-page <sheet> <pageId>
```

#### Page links (cross-page references)

```bash
xapps doc-add-page-link <sheet> <pageId> <targetPageId>... [--by-title <title>]
xapps doc-remove-page-link <sheet> <pageId> <targetPageId> [--by-title <title>]
xapps doc-list-page-links <sheet> <pageId> [--json]
```

`--by-title` resolves a target by exact title match (case-insensitive). Errors on ambiguity; pass the page ID directly to disambiguate.

#### Blocks

`<type>` must be one of: `paragraph`, `heading1`, `heading2`, `bulleted`, `todo`, `quote`, `code`, `divider`, `callout`, `toggle`, `image`, `table`, `live-embed`.
`--props` must be a JSON object. `--checked` accepts `true`, `false`, `1`, `0`, `yes`, `no`, `on`, or `off`.

```bash
xapps doc-add-block <sheet> <pageId> --type <type> [--text <t>] [--checked] [--props <json>] [--index <n>]
xapps doc-list-blocks <sheet> <pageId> [--json]
xapps doc-update-block <sheet> <pageId> <blockId> [--text <t>] [--type <t>] [--checked <bool>] [--props <json>]
xapps doc-delete-block <sheet> <pageId> <blockId>
xapps doc-reorder-block <sheet> <pageId> <blockId> --index <n>
```

#### Metadata

```bash
xapps doc-get-meta <sheet> [--json]
xapps doc-set-meta <sheet> [--title <t>] [--icon <e>] [--summary <s>] [--accent-color <c>] [--page-width <w>] [--text-scale <n>] [--mode <m>] [--font-family <f>]
xapps doc-set-property <sheet> <key>=<value>...
xapps doc-list-properties <sheet> [--json]
xapps doc-clear-property <sheet> <key>
```

`--accent-color` must be `#RRGGBB`; `--page-width` must be `760px`, `980px`, `1280px`, `100%`, or a positive pixel width; `--text-scale` must be `16`, `18`, or `22`; `--mode` must be `page` or `collection`.

#### Markdown import / export

```bash
# Single-page import — append blocks to an existing page
xapps doc-import-markdown <sheet> <pageId> --file ./article.md
# Single-page replace
xapps doc-import-markdown <sheet> <pageId> --file ./article.md --replace
# Multi-page wiki import — split on # headings, two-pass [[Title]] resolution
xapps doc-import-markdown <sheet> --multi --file ./constitution.md --replace-pages
# Pipe Markdown via stdin
cat note.md | xapps doc-import-markdown <sheet> <pageId>

# Export
xapps doc-export-markdown <sheet> [<pageId>] [--out path.md]
```

#### JSON import / export

```bash
xapps doc-import-doc-json <sheet> bundle.json [--replace-pages]
xapps doc-export-doc-json <sheet> [--out bundle.json]
```

The JSON shape is `{ meta?: {...}, pages: [{ title, icon?, summary?, blocks: [{ type, text, checked?, props? }] }] }`.
Import validates page titles, optional page IDs, linked page arrays, block types, table rows, boolean fields, and property objects before creating or replacing pages.

#### Markdown mapping (single source of truth)

| Markdown source | Block type | Notes |
|---|---|---|
| `# Title` | `heading1` (or page boundary in multi-page mode) | |
| `## Subtitle` | `heading2` | |
| `### Subsection` | `heading2` with `props.subhead = '###'` | Round-trips back to ### on export |
| `> quote` | `quote` | Consecutive `>` lines merge with `\n` separators |
| `- item` / `* item` | `bulleted` | Indentation maps to `props.indent` |
| `- [ ] task` / `- [x] task` | `todo` (`checked` true/false) | Uppercase X also accepted |
| `1. item` | `bulleted` with `props.numbered: true` | |
| `---` / `***` / `___` | `divider` | |
| ` ```lang ` ... ` ``` ` | `code` (`props.language = lang`) | |
| `:::callout [tone]\nbody\n:::` | `callout` (`props.tone`) | Tones: `info`, `success`, `warn`, `danger` (default `info`) |
| `:::toggle Title\nbody\n:::` | `toggle` (`props.summary = "Title"`) | |
| `![alt](src)` (alone) | `image` (`text=src`, `props.alt=alt`) | |
| `[[Page Title]]` / `[Page Title](#page-id)` | inline link | Auto-populates `linkedPages` on the importing page |
| empty line + plain text | `paragraph` | Default fallback |

Frontmatter (single-page or per-page in multi-page mode) sets icon, summary, properties, and explicit linkedPages:

```
---
icon: 📜
summary: Short description
linkedPages:
  - page-2
  - page-3
properties:
  Author: James Madison
---
# Page Title
```

### 🤖 Agent recipe — build a wiki from one Markdown file

```bash
# Create a fresh workbook with a Wiki sheet
xapps create-workbook MyWiki --sheet doc:Encyclopedia

# Author content as a single Markdown file with # per page; the importer
# splits, applies frontmatter, and resolves [[Title]] cross-references in
# two passes.
xapps doc-import-markdown MyWiki --multi --file ./encyclopedia.md --replace-pages

# Verify
xapps doc-list-pages MyWiki
xapps doc-list-page-links MyWiki page-2
```

This replaces what previously took dozens of HTTP POSTs with two CLI calls.
