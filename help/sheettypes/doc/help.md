## Wiki

### Pages, briefs, SOPs, and knowledge entries

Use **Wiki** for a collection of linked pages: a team handbook, project brief,
decision log or research notebook. Choose **Typewriter** when the main result is
a paginated document with headers, footers and detailed print layout.

### Build your first useful Wiki

1. Add a **Wiki** sheet and give it a topic, such as **Project Handbook**.
2. Start with one overview page. Give it a clear title and short summary;
   both help people find it from the page rail.
3. Click in the body and write the purpose. Type `/` to choose a heading,
   checklist, callout, table, image or embed. Use one heading per main section.
4. Add separate pages for decisions, meeting notes and procedures. Keep related
   pages in this sheet so the page rail remains the common navigation.
5. Connect pages with `[[Page title]]` links. Add a linked sheet in **Settings**
   when the page should lead readers to a board, schedule or spreadsheet.
6. Save the workbook. Reopen the page from its rail entry and check its title,
   links and sections without relying on your explanation.

### Choose the right block

| What the reader needs | Use | Example |
|---|---|---|
| A section they can jump to | Heading 1 or Heading 2 | Decisions, Next steps |
| A task they can tick off | Checklist | Confirm the launch date |
| A key point that stands out | Callout | The review is due Friday |
| A compact comparison | Table | Option, benefit, owner |
| A procedure or command | Code block | A reproducible command sequence |
| Current workbook information | Live data embed | A budget range or registered sheet view |
| Additional detail on demand | Toggle list | Supporting notes |

### Turn meeting notes into a decision record

Start a fresh page, then choose **Settings → Template → Meeting Notes** and
**Apply Template**. Templates replace the active page structure, so apply one
before writing the notes you want to keep. Record the decision, its reason and
the owner of each follow-up. Use a checklist for actions and link the relevant
Kanban or Timeline sheet. Add a summary such as “Approved the September pilot”
so readers can identify the outcome from the rail.

![Wiki page settings showing layout, template, tone, typography and linked pages](/help-assets/screenshots/doc-settings.png)

*Settings applies to the current page. Applying a template and changing page
appearance are separate actions.*

### Find your way around a growing handbook

The page-rail search finds pages by title and summary. **Outline** finds sections
inside the open page. Use Collection layout in **Settings** when readers should
browse a persistent list of pages alongside the reading pane.

![Wiki Outline panel listing the Engineering Process page headings](/help-assets/screenshots/doc-outline.png)

### When something looks wrong

| Symptom | Check |
|---|---|
| A page is missing from the rail | Clear search and confirm the Wiki sheet. |
| The outline is empty | Use heading blocks; bold paragraphs do not become outline entries. |
| A Wiki link cannot find its target | Check the page title and the heading text after `#`. |
| An embed is stale or broken | Open its source, check the range or view, then refresh or relink it. |
| Export is unavailable | Save the workbook first; review fidelity warnings. |
| A template replaced content | Use Undo while the editor has focus; use a new page for future templates. |

### Feature reference

Wiki sheets are the narrative layer of an xApps workbook. They are designed for:

- project briefs
- meeting notes
- SOPs
- research notes
- release notes
- wiki pages that link to the rest of the workbook

> Agent example: an agent can draft a brief, structure sections and tables, pull workbook facts into the page, and leave the human editor with a clean wiki page instead of raw notes.

![Wiki sheet showing the Welcome page of a Team Handbook with heading, callout block, and a sidebar listing five pages](/help-assets/screenshots/doc-sheet.png)

### One Wiki sheet can contain many pages

Each Wiki sheet is a small internal wiki workspace. Keep many related pages inside one Wiki sheet, and use separate Wiki sheets only when you want separate workspaces.

- use the page rail on the left to switch pages inline
- the search box in the rail filters pages by title and summary
- page operations target the active page

![Wiki sidebar showing five pages — Welcome, Onboarding Checklist, Communication Norms, Engineering Process, and Incident Response SOP](/help-assets/screenshots/doc-pages.png)

### Wiki links

Wiki supports internal links:

- `[[Page]]` links to another page
- `[[Page#Section]]` links to a heading inside a page
- `[[#Section]]` links to a heading in the current page
- `[[Page|Label]]` adds custom link text
- `[[Page#Section|Label]]` links to a section with custom link text

When you create a page from selected text, the menu asks for the new page title instead of assuming the highlighted text is the title. The highlighted text remains the inline link label.

### Blocks

Wiki pages are block-based. Current block types include:

- paragraph
- heading 1
- heading 2
- bulleted list
- checklist (todo)
- quote
- code block
- divider
- callout
- toggle list
- image
- table
- live data embed

![Onboarding Checklist page with the first task checked and the remaining tasks ready to complete](/help-assets/screenshots/doc-blocks.png)

### Inline formatting

Text within blocks supports rich inline formatting:

- **bold**, *italic*, underline, strikethrough
- inline code
- hyperlinks

Apply formatting via the floating format bar or keyboard shortcuts (`Ctrl/Cmd + B`, `I`, `U`, etc.).

### Table blocks

Insert a table with the `/table` slash command or the toolbar table button. Tables support:

- header row toggle
- add and delete rows and columns
- `Tab` to navigate between cells

### Image blocks

Image blocks support:

- sizing — small, medium, large, or full width
- alignment — left, center, or right
- caption and accessible alt text
- URL, drag-drop, and paste inputs copied into the workbook upload store before the block references them

### Live data embed blocks

Insert a live data view from another sheet in the workbook using `/embed` or the Insert menu. Sources are validated as spreadsheet ranges or registered sheet views. Typed API/SDK/CLI/toolkit reads report whether the stored source fingerprint is current, stale, missing, or type-mismatched; refresh revalidates it without copying source data into the page.

### Callout blocks

Callout blocks draw attention to key information. They support:

- icon (emoji)
- background color — Blue, Green, Yellow, Red, Purple, Orange, or Gray
- tones via CLI: `info`, `success`, `warn`, `danger`

![Incident Response SOP page showing a callout block with blue background and a Purpose heading](/help-assets/screenshots/doc-callout.png)

### Code blocks

Code blocks support syntax language labels (e.g. `bash`, `javascript`, `python`). The language is preserved on export.

![Engineering Process page showing heading, bullet list, code review checklist, and a bash code block](/help-assets/screenshots/doc-code-block.png)

### Block comments

Hover over a block and click its comment button to open the governed thread panel. Threads have stable server IDs, attributed authors and timestamps, replies, edit/delete permissions, and resolve/reopen state. Changes use the same revision-guarded API as Doc automation, so another client's update is shown before you retry instead of being overwritten.

Agents use `doc-list-comments`, `doc-add-comment`, `doc-edit-comment`, `doc-delete-comment`, `doc-resolve-comment`, `doc-add-comment-reply`, `doc-edit-comment-reply`, and `doc-delete-comment-reply`. Mutations accept `--expected-revision` plus `--request-id` for safe retry.

### Block colors

Apply a background tint to any block for visual emphasis. Useful for highlighting key sections or creating visual groupings. Available tints: None, Blue, Green, Yellow, Red, Purple, Orange, Gray.

### Block reordering

Drag blocks to reorder them within a page.

### Export

- **PDF export** — `Wiki -> Download PDF (.pdf)` returns a real server-produced `application/pdf` artifact
- **DOCX export** — `Wiki -> Download Word (.docx)` returns a real OOXML package with the canonical DOCX MIME type
- Exports require a saved workbook. Data-URI images, links, tables, headings, and lists are supported; unsupported external images and live embeds are reported as fidelity warnings.

### Wiki-style page shell

The Wiki sheet is more than a blank editor. Each page also has:

- a cover tone (Ocean, Amber, Forest, Berry, Slate)
- an accent color
- page summary text
- editable properties panel
- linked pages
- linked sheets
- a live outline generated from headings
- page templates for common wiki page shapes

### Editing flow

The editor is designed to feel like one flowing page instead of a stack of form cards:

- type directly into a block
- press `Enter` on a heading to continue below with a paragraph
- press `Enter` on a checklist item to add the next checklist item
- use `/` inside a text block to open the slash menu
- use markdown-style shortcuts like `#`, `##`, `>`, `-`, `[]`, and ` ``` ` to convert the current block
- use `Ctrl/Cmd + Z` and `Ctrl/Cmd + Shift + Z` to undo and redo Wiki edits while the editor has focus
- hover or focus a block to reveal type and action controls

### Templates

Built-in templates are applied via the Settings panel (gear icon in the page header). Applying a template replaces the current active page structure, so use them early or after confirming a reset. Templates currently include:

- Blank
- Project Brief
- Meeting Notes
- SOP
- Research Note
- Release Notes

### Page styling

The Settings panel (gear icon, top-right of the page) controls page-level style:

- **Layout** — Page (single document) or Collection (sidebar list + reading pane)
- **Font family** — Inter, DM Sans, Work Sans, Merriweather, Playfair Display, Georgia, Source Code Pro
- **Text scale** — Compact (16 px), Standard (18 px), Large (22 px)
- **Page width** — Narrow (760 px), Standard (980 px), Wide (1280 px), Full width
- **Cover tone** — Ocean, Amber, Forest, Berry, Slate
- **Accent color** — any hex color applied to headings and interactive elements

### Collection mode

Switch the layout to Collection in the Settings panel. In collection mode, the page rail expands into a persistent sidebar and the selected page opens in a reading/editing pane on the right. Useful for knowledge bases and document libraries where users browse many pages in one session.

### Properties and linked sheets

Use the **Properties** button (top-right of the page, `#` icon) to add structured metadata without cluttering the reading body. Property keys are auto-typed by name — fields named `status`, `owner`, `date`, `tag`, or `url` get the appropriate icon and display treatment. Common fields include:

- Status
- Owner
- Audience
- Source
- Review cadence

**Linked sheets** (in the Settings panel) let one Wiki page act as the front door to related workbook surfaces, like a timeline, dashboard, floor plan, or spreadsheet.

**Linked pages** connect related wiki pages as named cross-references without using inline `[[...]]` syntax.

### Outline panel

Click the **Outline** button (top-right of the page) to open a live outline built from all heading blocks on the current page. Click any outline item to jump directly to that heading.

### Search

The search box at the top of the page rail filters pages by title and summary as you type. Matches update instantly without leaving the page.

### Great uses inside xApps

Wiki pages work especially well when paired with other sheet types:

- write a project brief, then link to a timeline, kanban board, and dashboard
- keep renovation notes next to a floor plan, gallery, and budget spreadsheet
- store campaign strategy beside a content calendar, presentation, and design canvas

### Assisted writing

Use the shared room **Assistant**, when available, to draft or revise Wiki
content. Name the page, the workbook facts it should use and the result you
want. Review the resulting text and links. Wiki has no separate Writing Copilot
button; automation uses the guarded Doc editing tools described below.

---

### CLI Commands

The Wiki / Doc surface ships 67 CLI commands. They share the same `xapps <command> <sheet> ...` pattern as other xApps surfaces. The `<sheet>` is the wiki sheet name in the active workbook.

Bad input is rejected before mutation. Page and block IDs must be non-empty, non-numeric strings without `/`; `--index` values must be non-negative integers; bool flags accept true/false-style values; JSON options must be the documented object shapes. With `--json`, CLI errors are emitted as structured error envelopes.

Every page, block, link, metadata, and property write uses the guarded atomic mutation API. Mutating commands accept `--expected-revision <n>` and `--request-id <id>`. Omit both flags to have the SDK read the current revision and generate a one-attempt request id, or provide both for deterministic agent retries; supplying only one is rejected. Same-request/same-payload retries return the original result without another save. A stale revision or changed reuse of a request id fails with `409` and zero mutation.

```bash
xapps doc-mutation-state <sheet> [--json]
xapps doc-mutation-outcome <sheet> <requestId> [--json]
```

`doc-mutation-state` returns the revision and active page id needed for a guarded write. `doc-mutation-outcome` retrieves the durable original result after a disconnect or restart.

#### Pages

```bash
xapps doc-add-page <sheet> <title> [--icon <emoji>] [--summary <text>] [--index <n>] [--set-active] [--id <pageId>]
xapps doc-list-pages <sheet> [--json]
xapps doc-get-page <sheet> <pageId> [--offset <n>] [--limit <n>] [--json]
xapps doc-rename-page <sheet> <pageId> --title <title> [--icon <emoji>] [--summary <text>]
xapps doc-delete-page <sheet> <pageId>
xapps doc-set-active-page <sheet> <pageId>
xapps doc-reorder-page <sheet> <pageId> --index <n>
```

`--id` on `doc-add-page` is a true idempotent upsert key: when a page with that id already exists, the call updates it in place (fields the call omits are preserved, `--index` is ignored) instead of erroring. JSON output carries `created` / `updated` markers.

#### Templates, collections, search, and outline

```bash
xapps doc-list-templates <sheet> [--json]
xapps doc-get-template <sheet> <templateId> [--json]
xapps doc-apply-template <sheet> <templateId> <pageId>
xapps doc-get-collection <sheet> [--json]
xapps doc-configure-collection <sheet> --sheets <json-array> [--active-sheet <name>]
xapps doc-search <sheet> <query> [--offset <n>] [--limit <n>] [--json]
xapps doc-outline <sheet> <pageId> [--json]
```

Template application, page reordering, and collection configuration use the same guarded revision/request-id contract as other Doc writes. Search returns stable page/block locations with deterministic pagination; outline returns heading levels, block IDs, and positions.

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
xapps doc-add-block <sheet> <pageId> --type <type> [--text <t>] [--checked] [--props <json>] [--index <n>] [--id <blockId>]
xapps doc-list-blocks <sheet> <pageId> [--offset <n>] [--limit <n>] [--json]
xapps doc-update-block <sheet> <pageId> <blockId> [--text <t>] [--type <t>] [--checked <bool>] [--props <json>]
xapps doc-delete-block <sheet> <pageId> <blockId>
xapps doc-reorder-block <sheet> <pageId> <blockId> --index <n>
```

`--id` on `doc-add-block` is a true idempotent upsert key: when a block with that id already exists on the page, the call updates it in place — position preserved, `--index` ignored — instead of creating a duplicate id. JSON output carries `created` / `updated` markers. Block ids are unique per page; a write that would introduce a duplicate id is rejected with `doc_duplicate_block_id` (409).

`doc-list-blocks` and `doc-get-page` accept `--offset <n>` / `--limit <n>` to window blocks **server-side** (the page GET takes `?offset=&limit=` query params, mirroring the MCP resources convention). The JSON output carries the pre-window total — `totalCount` on `doc-list-blocks`, `page.blocksTotal` on `doc-get-page` — so agents can page through long documents without fetching everything.

#### Images and live embeds

```bash
xapps doc-upload-image <file-or-url> [--name <filename>] [--json]
xapps doc-list-media <sheet> [--page <pageId>] [--json]
xapps doc-insert-image <sheet> <pageId> <uploads-url> [--size small|medium|large|full] [--align left|center|right] [--alt <text>] [--caption <text>]
xapps doc-update-image <sheet> <pageId> <blockId> [--src <uploads-url>] [--size <size>] [--align <align>] [--alt <text>] [--caption <text>]
xapps doc-remove-image <sheet> <pageId> <blockId>
xapps doc-insert-live-embed <sheet> <pageId> --source-sheet <sheet> [--kind range|sheet-view] [--range <A1:D10>] [--sheet-type <type>] [--options-json <json>]
xapps doc-update-live-embed <sheet> <pageId> <blockId> [source options]
xapps doc-refresh-live-embed <sheet> <pageId> <blockId>
xapps doc-remove-live-embed <sheet> <pageId> <blockId>
```

Image commands accept only durable `/uploads/<file>` references; use `doc-upload-image` first for local bytes or remote URLs. Removing an image detaches the block and reports whether the shared asset became orphaned, but retains the asset until an explicit workbook asset-cleanup flow. Live embeds keep reference metadata and a source fingerprint, never a copied snapshot.

#### Rich editing and tables

These typed commands use the same revision-guarded, one-save transaction as page/block writes. Inline offsets address rendered text; mark IDs and inserted block IDs are stable retry targets. Invalid ranges, block types, and table coordinates reject the full transaction without partial edits.

```bash
xapps doc-format-inline <sheet> <pageId> <blockId> --start <n> --end <n> --mark <bold|italic|underline|strikethrough|code> [--mark-id <id>]
xapps doc-link-inline <sheet> <pageId> <blockId> --start <n> --end <n> --href <url> [--mark-id <id>]
xapps doc-remove-inline-mark <sheet> <pageId> <blockId> <markId>
xapps doc-insert-rich-block <sheet> <pageId> --type <type> [--text <text>] [--after-block <id>] [--id <id>]
xapps doc-convert-block <sheet> <pageId> <blockId> --type <type>
xapps doc-set-callout <sheet> <pageId> <blockId> [--icon <emoji>] [--background <hex>]
xapps doc-set-toggle <sheet> <pageId> <blockId> [--body <text>] [--open <bool>]
xapps doc-set-code <sheet> <pageId> <blockId> [--language <name>] [--text <code>]
xapps doc-set-block-background <sheet> <pageId> <blockId> --color <hex-or-empty>
xapps doc-set-checklist <sheet> <pageId> <blockId> --checked <bool>
xapps doc-set-table-cell <sheet> <pageId> <blockId> --row <n> --column <n> --text <text>
xapps doc-insert-table-row <sheet> <pageId> <blockId> --index <n> [--values <json>]
xapps doc-delete-table-row <sheet> <pageId> <blockId> --index <n>
xapps doc-insert-table-column <sheet> <pageId> <blockId> --index <n> [--values <json>]
xapps doc-delete-table-column <sheet> <pageId> <blockId> --index <n>
xapps doc-set-table-header <sheet> <pageId> <blockId> --enabled <bool>
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
xapps doc-import-markdown <sheet> <pageId> --input ./article.md
# Single-page replace
xapps doc-import-markdown <sheet> <pageId> --input ./article.md --replace
# Multi-page wiki import — split on # headings, two-pass [[Title]] resolution
xapps doc-import-markdown <sheet> --multi --input ./constitution.md --replace-pages --yes --request-id constitution-v3
# Pipe Markdown via stdin
cat note.md | xapps doc-import-markdown <sheet> <pageId>

# Export
xapps doc-export-markdown <sheet> [<pageId>] [--out path.md]
xapps doc-export-artifact <sheet> <docx|pdf> --out artifact.ext [--scope page|all] [--page-id id] [--verify]
```

The Markdown source flag is `--input` (or stdin). The global `--file` flag selects the **target workbook** — it cannot name the Markdown source.

In single-page mode, omitting `<pageId>` imports into the sheet's **active page**; the output echoes the resolved page id (`usedActivePage: true` in JSON). Pass an explicit `<pageId>` to target any other page.
Single-page append preserves every existing block ID, allocates new `block-N` IDs from the page's monotonic `nextBlockId`, and treats the parsed Markdown as the stable request intent. Repeating the identical command with the same `--request-id` after a dropped response returns `replayed: true` without appending the content twice; changed Markdown under that ID is rejected without modifying the page.

#### JSON import / export

```bash
xapps doc-import-doc-json <sheet> bundle.json [--replace-pages --yes|--replace-all --yes] [--upsert-by-title] [--request-id id] [--json]
cat bundle.json | xapps doc-import-doc-json <sheet> --stdin --json
xapps doc-import-doc-json --schema --json
xapps doc-export-doc-json <sheet> [--out bundle.json]
```

The JSON shape is `{ meta?: {...}, pages: [{ id?, title, icon?, summary?, properties?, linkedPages?, blocks: [{ type, text, checked?, props?, rows? }] }] }`.
Import is one API transaction: it validates every page title, optional page ID, cross-link, block, table row, boolean, metadata field, and property object before changing the live sheet, then persists all pages with one save. A late conflict leaves the previous document unchanged. `--request-id` supplies a stable idempotency key; retry the exact same command and payload after a dropped response to receive `replayed: true` without another write. Reusing that ID with changed content is rejected.
Use `--schema --json` to print the accepted block types and a minimal valid manifest — it is a static output and needs no configured API base URL. Valid block types include `heading1`, `heading2`, `paragraph`, `bulleted`, `todo`, `quote`, `divider`, `code`, `callout`, `toggle`, `image`, and `table`.
Use `--replace-all --yes` as the agent-friendly form for replacing the complete existing page set; `--yes` is mandatory because unmatched pages are deleted. The first existing page ID is reused so imports cannot trip the server's "Page ID cannot be changed" guard. Use `--upsert-by-title` when the incoming manifest should update matching pages by title while preserving their existing page IDs.

Prefer `doc-import-doc-json` over `doc-import-markdown` when you need explicit block types — the markdown importer collapses ambiguous content into single paragraphs, while the JSON importer preserves the exact block type for every item.

The Wiki menu also provides **Import Markdown or JSON** and **Export Markdown or JSON**. Imports validate and preview before committing through the same atomic server API, require a second confirmation before replacement, and expose an idempotent replay receipt. Source may be pasted or loaded from workbook files; dropped files are stored there first. Exports read saved server state and can be copied or saved back to workbook files.

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

### Agent recipe — build a wiki from one Markdown file

Choose the authorized saved workbook and its actual storage target before running the examples. Set `XAPPS_API_BASE_URL` to that host. This helper keeps every operation in the same scope (replace the example file and `local` together when needed):

```bash
xapps_scoped() {
  xapps --base-url "${XAPPS_API_BASE_URL:?Set the authorized host URL}" \
    --file 'MyWorkbook.json' --workbook-storage-target local "$@"
}
```

Create a new workbook only when needed; for an existing workbook, use its existing Wiki sheet. Creation uses lifecycle `--storage-target` and authoring uses `--workbook-storage-target`.

```bash
xapps --base-url "$XAPPS_API_BASE_URL" create-workbook MyWorkbook \
  --storage-target local --sheet doc:Encyclopedia
xapps_scoped doc-import-markdown Encyclopedia --multi --input ./encyclopedia.md --request-id encyclopedia-content-1 --json
xapps_scoped doc-list-pages Encyclopedia --json
# Use a stable page ID returned by the import/list response.
xapps_scoped doc-get-page Encyclopedia "$IMPORTED_PAGE_ID" --json
```

`Encyclopedia` is the sheet; `MyWorkbook.json` is the saved file. Author useful narrative early in a bulk import and read back page/block content. For repeatable updates to existing pages, prefer the JSON upsert recipe below; replacement options delete unmatched pages and require that intended replacement scope.

### Agent recipe — build a multi-page wiki from a JSON manifest

Choose the authorized saved workbook and its actual storage target before running the examples. Set `XAPPS_API_BASE_URL` to that host. This helper keeps every operation in the same scope (replace the example file and `local` together when needed):

```bash
xapps_scoped() {
  xapps --base-url "${XAPPS_API_BASE_URL:?Set the authorized host URL}" \
    --file 'MyWorkbook.json' --workbook-storage-target local "$@"
}
```

Prepare `handbook.json` with stable page IDs, explicit block types and cross-links using `doc-import-doc-json --schema --json`. Use the existing `Handbook` sheet in the scoped workbook.

```bash
xapps_scoped doc-import-doc-json Handbook handbook.json \
  --upsert-by-title --request-id handbook-content-1 --json
xapps_scoped doc-list-pages Handbook --json
xapps_scoped doc-get-page Handbook page-1 --json
```

Preserve the exact request ID and file content after an uncertain response. Upsert preserves page identity while updating matching titles; review title changes before importing so they do not accidentally create new pages. Read the imported blocks, not only page counts, before reporting the narrative complete.
