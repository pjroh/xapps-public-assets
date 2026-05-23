## Records Tables

### Airtable-style relational tables in a workbook tab

Records sheets turn a workbook tab into a typed relational table — like Airtable's grid. Each table has a fixed schema (fields with types), every row is a record with a stable id and system audit fields, and tables can link to each other so a record in **Deals** can point to a record in **Contacts** without copy-pasting.

Behind the grid, records persist in the workbook file alongside every other sheet, so the rest of the xApps platform — formulas, dashboards, automations, agents — can read and write the same data.

> 🤖 Agent example: an agent can spin up a CRM table, seed it from a CSV, run a SQL query against it, and hand a filtered view back to a human collaborator via a saved view URL.

---

### Features at a glance

- 19 user field types: text, longText, url, email, number, duration, singleSelect, multiSelect, checkbox, rating, date, person, file, relation, formula, lookup, rollup, count, ai
- 5 auto-stamped system fields: autoNumber, createdAt, createdBy, lastModifiedAt, lastModifiedBy
- Schema editor with quick-start templates (CRM Contacts / Project Tracker / Content Calendar / Bug Tracker / Event)
- Inline cell editing with type-aware inputs
- Sticky column headers + arrow-key / Tab / Enter keyboard navigation
- Drag-to-reorder columns and rows
- Resize columns by dragging the column-edge handle
- Multi-row select (shift-click for ranges) with a bulk-delete actions bar
- In-grid search with highlighted matches
- Named view types: **grid**, **kanban**, **calendar**, **gallery** — saved per-table, switchable from the view chip
- Filter / sort / group on every view, with collapsible row groups + per-group aggregates + Expand all / Collapse all
- Per-field cell colors (background + text) via the Color toolbar popover or the schema editor's Cell colors panel; "Color records by" tints the left bar by a singleSelect option
- Star rating field (1–N stars, click to set, click again to clear)
- Airtable-style 12-color chip palette for singleSelect / multiSelect
- Linked-record picker — click any relation cell to choose target records
- Relation hover previews with target-record display values
- Per-record detail panel with Fields / Activity / Linked tabs + threaded comments
- Per-record history (every cell change, with actor + timestamp)
- Validation (required / unique / type) with structured `422` envelopes
- CSV import with upsert + rollback-on-error
- CSV export with column picker + delimiter choice
- SQL query panel: text editor with autocomplete + Format + saved queries, side-by-side visual builder (tables-as-boxes, drag-to-JOIN ports, INNER/LEFT/RIGHT pill switcher, inline ✕ delete), and a Schema diagram launcher
- SQL grammar: SELECT / DISTINCT / WHERE / GROUP BY / HAVING / ORDER BY / LIMIT / aggregates / CASE / scalar functions / **INNER · LEFT · RIGHT · CROSS JOIN with qualified column refs (`r.Name`)**
- Multi-table per sheet (recs-57) — a single Records sheet can hold multiple tables; the tab strip switches between them, and SQL FROM clauses can reference either the sheet's active table or `Sheet.Table` explicitly
- Formula expression language with autocomplete, field picker, and live preview
- Undo / redo (Ctrl+Z / Ctrl+Y) for cell edits, add row, rating, bulk delete, row reorder, link records
- Per-table tab strip across the top with Rename / Hide / Delete / Restore menu

![Records grid with Airtable-style chrome](/help-assets/screenshots/records-grid.png)

---

### Multiple tables in one sheet

A single Records sheet can hold many tables — switch between them using the **tab strip** across the top of the grid. Each tab is one independent table with its own schema, records, views, and history. Click `+` in the tab strip to create a new table, or right-click any tab to Rename / Hide / Delete it. Hidden tables retain all their data; they re-appear in the same menu as **Restore** entries.

![Multiple tables — Suppliers table active in the same Records sheet](/help-assets/screenshots/records-multi-table.png)

---

### Keyboard shortcuts

| Key | Action |
| --- | --- |
| `Click` | Open cell editor |
| `Enter` | Commit cell edit and move down |
| `Esc` | Cancel cell edit |
| `Tab` / `Shift+Tab` | Next / previous field in row |
| `Arrow keys` | Move focused cell |
| `Ctrl/Cmd + Z` | Undo |
| `Ctrl/Cmd + Y` (or `Ctrl/Cmd + Shift + Z`) | Redo |
| `Shift + Click` (row checkbox) | Select range |

---

### Anatomy of the grid

- **Tab strip** (top) — one tab per records table in the workbook. The active tab is the white "lifted" tab. The caret on each tab opens a menu with Rename / Hide table (keep data) / Delete table…; hidden tables show up as Restore entries in the same menu. Click `+` to create a new table.
- **Toolbar** (above the tab strip) — Undo / Redo at the far left, then the active **view chip** (e.g. "Grid view") and a collaborator avatar. The middle group has Hide fields, Filter, Group, Sort, Color, Row height, Share view, and More. The right group has Edit fields (schema editor), Import CSV, Query (SQL panel), and a global search input.
- **Header row** (sticky) — one `<th>` per visible field with type icon + name + sort arrow. Each header is draggable for reorder; the 6px handle on the right edge drags column width. The `▾` caret in the header opens the field options menu.
- **Body** — one row per record. The `#R-NNN` autonumber lives in a sticky left column; the per-row checkbox lives in another sticky column to its left.
- **Group header rows** — when the active view has a `groupBy`, the body is partitioned by that field's display value. The chevron toggles collapse; counts + numeric Σ aggregates render on the group row.
- **Add-row strip + footer** — `+ Add a record` at the bottom inserts a record and focuses the first editable cell. The footer chips show the live record count plus per-field aggregates (Σ on numbers, true-count on checkboxes, won/done/closed counts on selects).

---

### Creating a table

Two paths:

1. From any workbook, click `+` on the records tab strip → enter a name → the new sheet opens in **schema mode** with the quick-start template panel.
2. From the CLI: `xapps records-create-table "Deals"`.

Quick-start templates seed the schema with 4–5 starter fields you can edit or delete after. Click the `×` in the header (or press `Esc`) to dismiss the schema editor and start with a blank table.

![Schema editor with field list and type options](/help-assets/screenshots/records-schema-editor.png)

**Schema editor actions:**
- **Add a field** — click `+ Name a new field…` at the bottom of the list. Pick a type, configure options (choices, format, max stars, etc.), then click Done.
- **Rename / change type** — click any row in the list to expand it. Destructive type changes (e.g. text → number) show a warning.
- **Reorder fields** — drag the six-dot handle on the left of any field row.
- **Required / Unique** — toggle the **Req** and **Unique** checkboxes on any field row.
- **Cell colors** — expand a field row to reveal the **Cell colors** panel (background + text swatches). These tint every cell of that column.
- **Delete a field** — expand the row and click the trash icon. Deletes the field from every record.
- **Tab color** — right-click a table tab → **Set tab color** (or CLI: `xapps records-set-table-color <sheet> <tableId> <color>`) to visually distinguish tables in the strip.

---

### Field types — when to use what

- **text** / **longText** — short or multi-line free-form strings.
- **url** / **email** — strings with format validation + click-to-open / mail-to.
- **number** — numeric with `int / decimal / currency / percent` format + decimals option. Aggregated in the footer.
- **duration** — seconds; renders as `H:MM:SS`.
- **singleSelect** / **multiSelect** — pick from a named option set, each with a color from the Airtable-style palette.
- **checkbox** — true / false; toggled with a single click in the cell.
- **rating** — 1–N stars (default 5); click a star to set, click the same star again to clear.
- **date** — ISO date with optional time-of-day.
- **person** — pick from the workbook's collaborators.
- **file** — file or image upload (multiple allowed).
- **relation** — link to records in another records table. Click the relation cell to open the picker.
- **lookup** — pull a field from a linked record.
- **rollup** — aggregate a field across linked records.
- **count** — count linked records.
- **formula** — derived value from an expression; supports `IF / AND / OR / NOT / CONCAT / LEN / UPPER / LOWER / TRIM / CONTAINS / ABS / ROUND / SUM / AVG / COUNT / MIN / MAX / NOW / TODAY`. Errors render in red.
- **ai** — value produced by an AI agent on a per-record basis. Configure a prompt template that can reference other fields in the record (e.g. `Summarize this product: {{Notes}}`). The result is cached; re-run manually by clicking the cell or via the AI executor panel. Useful for auto-generating descriptions, classifications, or translations.

System fields (`#`, `createdAt`, `createdBy`, `lastModifiedAt`, `lastModifiedBy`) are auto-stamped and read-only.

**Footer aggregates** — the footer row at the bottom of the grid shows live aggregates per column: `Σ` sum and count for number fields, true-count for checkboxes, and won/done/closed-option counts for singleSelect fields. The total record count appears at the far left.

---

### Views — types + filter / sort / group

A view is a saved configuration on a table. Each view has a **type** that decides how the records are visualized, plus shared filter/sort/group settings.

**View types**

- **grid** — the default. Dense Airtable-style rows and columns.
- **kanban** — records become cards on columns keyed by a singleSelect field.
- **calendar** — records placed on dates, driven by a date field.
- **gallery** — large-card layout driven by an attachment / image field.
- **form** — add or edit one record at a time with a custom field layout.
- **pivot** — a cross-tab that groups rows/columns and aggregates a value (see below).

Switching views replaces the toolbar's view chip label and re-renders the body. The view list lives in the view chip dropdown; **Manage saved views…** opens a reorder/rename/delete modal.

**Shared view config (applies to every type)**

- **Filter** — boolean expression over fields (e.g. `Status = "Won" AND Amount > 1000`).
- **Sort** — one field + direction.
- **Group by** — partition rows by a field's value; the group header row shows count + numeric aggregates and is collapsible. Expand all / Collapse all controls live above the body when a group is set.
- **Hidden fields** — per-view list of fields to hide.

Views persist per-table inside the workbook (`recordsTables[<id>].views[]`).

![View chip dropdown showing saved views and quick-action buttons](/help-assets/screenshots/records-views.png)

**Managing saved views:**
- Click the view chip (e.g. "Grid view") to open the view list.
- **New saved view…** — pick a type and give it a name. Opens to the active type immediately.
- **Manage saved views…** — opens a modal to reorder, rename, or delete views.
- The active filter/sort/group for the current view is shown in the toolbar.
- `xapps records-add-view <sheet> <view-json>` and `xapps records-update-view <sheet> <viewId> <patch-json>` are the CLI equivalents.

**Filtering records:**

The Filter panel (toolbar → Filter) adds row conditions to the active view. Conditions are ANDed together. Each condition picks a field, an operator (`=`, `≠`, `contains`, `is empty`, `>`, `<`, `≥`, `≤`, `in`), and a value. The condition count badge on the Filter button lights up when filters are active.

![Filter panel with no-filter-applied state and Add filter button](/help-assets/screenshots/records-filter.png)

---

### Pivot views (cross-tab)

A **pivot** view summarizes a table into a cross-tab: pick one or more **Row** dimensions (down the side), zero or more **Column** dimensions (across the top), and a **Value** that's aggregated for every row/column intersection. It re-runs the underlying query on every render, so the cross-tab is always live — never a stale snapshot.

**Creating one** — view chip → **New saved view…** → **Pivot**, or pick Pivot in the new-view modal. A new pivot opens the **Configure** panel immediately.

**Configure panel** (also reachable from the pivot's ⚙ Configure button):

- **Rows** / **Columns** — add field chips that become the cross-tab's row groups and column headers. Multiple row fields nest into collapsible groups with subtotals.
- **Values** — choose an aggregate (**Count**, **Sum**, **Avg**, **Min**, **Max**) and, for everything but Count, the field to aggregate. Count uses `COUNT(*)`.
- **Related tables (JOIN)** — JOIN another table in the same sheet (INNER / LEFT / RIGHT) on a field pair. Once joined, its fields become pickable for Rows, Columns, Values, and Filters — so a value can be summed across a relationship.
- **Filters** — limit which records feed the pivot (`=`, `≠`, `>`, `<`, `≥`, `≤`, contains).
- **Number format** — Plain or Currency.

**Reading it** — every row carries a row total, every column a column total, and the bottom-right cell is the grand total. Totals honor the aggregate: **Sum**/**Count** add, **Min**/**Max** reduce to the true min/max, and **Avg** shows the mean of the visible cells (a cross-tab approximation, not the population mean). With multiple row dimensions, the first dimension becomes a collapsible group header (▾ / ▸) with its own subtotal.

**Drill-down** — click any value cell to expand the underlying records behind that intersection (up to 500), shown in a panel below the cross-tab.

Under the hood the pivot config is compiled to a `GROUP BY` query and run through the same SQL engine as the **Query** tool, then reshaped client-side. The config persists at `views[<id>].config.pivot` with resolved `expr` + `label` per dimension. The pure SQL/reshape logic lives in `pivot-core.ts` (unit-tested); the browser renderer mirrors it.

---

### Per-record detail panel

Click the **autonumber button** (`1`, `2`, …) in the left column of any row to open the record's detail panel in a side drawer.

![Record detail panel showing all field values, Comments, Activity, and Linked tabs](/help-assets/screenshots/records-detail-panel.png)

The detail panel has four tabs:

- **Fields** — all field values in a stacked form layout. Every field is editable inline. Click **Open in form** (top-right) to open the record in a full-page form view.
- **Comments** — threaded discussion on that record. Type `@name` to mention a collaborator. Supports edit and delete of own comments.
- **Activity** — per-field change log (who changed what, old → new value, timestamp). Filter by field id via CLI: `xapps records-history <sheet> <recordId> [--field-id <fieldId>]`.
- **Linked** — records in other tables that link to this record (backlinks from relation fields).

**Duplicate a record** — in the row's right-click context menu or via CLI: `xapps records-duplicate <sheet> <recordId>`. Creates a new record with the same field values; relation links are not copied.

---

### Linking records (recs-24)

1. Add a `relation` field; in the schema editor pick the target table.
2. In the grid, click any cell of that field — the linked-record picker opens.
3. Type to search the target table, check the records you want to link, click Apply. Multi-link supported via the field's options.
4. Lookup / rollup / count fields can then pull data from the linked rows.

Hovering a relation cell shows a tooltip with the target records' primary-field values (recs-13).

---

### Bulk operations

- **Select rows** — header checkbox toggles all; per-row checkboxes; `Shift+Click` selects a range.
- **Bulk delete** — the floating bar at the bottom shows the count + a red Delete button. Undo restores them.
- **Bulk update** — via SDK / CLI: `xapps records-bulk-update <table> <ids> --patch '{...}'`.
- **Find / replace** — toolbar → Edit → Find and replace, or `Ctrl/Cmd + H`. Supports per-field scoping, case-sensitivity, and a **dry-run preview** that shows matches before committing. CLI: `xapps records-find-replace <sheet> --find <text> --replace <text> [--case-sensitive] [--field-ids <csv>] [--dry-run]`.

---

### Soft-delete and trash

Deleting a record sends it to the trash — the data is retained. To review or restore deleted records:

- **UI** — the trash is accessible from the sheet's More menu or by navigating to `/records/deleted`.
- **CLI** — `xapps records-trash <sheet>` lists soft-deleted records; `xapps records-restore <sheet> <recordId>` restores one.
- **Permanent delete** — hard-delete is not exposed in the UI; use the API endpoint `DELETE /api/sheets/<sheet>/records/<id>?hard=true` for permanent removal.

---

### Form view

A **form** view lets users add or edit records one at a time through a custom field layout — useful for data entry, surveys, or controlled intake flows.

Creating one: view chip → **New saved view…** → **Form**.

The form editor lets you:
- Drag fields to reorder them within the form.
- Hide individual fields (a hidden field is not shown to the form submitter but is still part of the record).
- Set a field as **required** directly in the form layout.
- Add descriptive text between fields.

Submitting the form creates a new record. The **+ Add via form** button at the bottom of the grid (next to `+ Add record`) opens the active form view inline for quick entry.

---

### Importing & exporting CSV

- **Import** — Toolbar → Import CSV → drop a file. The wizard auto-detects BOM / encoding, lets you map columns to fields, choose insert-or-upsert mode (with a match-key field), and rolls back on the first error so partial imports never half-corrupt the table.
- **Export** — Toolbar → Query → Export CSV. Choose columns, delimiter (`,` / `;` / Tab / `|`), include-system-cols toggle. Output uses UTF-8 BOM so Excel opens it cleanly.

---

### Query (SQL)

The Query panel opens a SQL editor with syntax highlighting + autocomplete + Format + saved queries. Supports a subset of SQL:

![SQL query panel with query, Run button, and result grid](/help-assets/screenshots/records-sql-panel.png)

```
SELECT Name, Status, COUNT(*), SUM(Amount)
FROM Deals
WHERE Status IN ('Qualification', 'Proposal')
GROUP BY Status
HAVING COUNT(*) > 2
ORDER BY SUM(Amount) DESC
LIMIT 50
```

Plus DISTINCT, AS aliases, CASE expressions, and scalar functions (`UPPER / LOWER / LENGTH / COALESCE`). The result panel can be exported as CSV directly. Saved queries persist per-table — pick **Save as…** to name and recall a query.

**JOIN support**

The parser supports `INNER`, `LEFT [OUTER]`, `RIGHT [OUTER]`, and `CROSS JOIN` with an optional `ON <predicate>`. Use a table alias to disambiguate qualified column refs:

```
SELECT r.Name, o.Total
FROM Records r
INNER JOIN Orders o
  ON r.Name = o.Customer
LIMIT 100
```

When two records sheets exist in the same workbook, the join target can be either bare (`JOIN Orders`) or `Sheet.Table` qualified (`JOIN "MyWorkbook.tbl_xxx"`). Unmatched rows in `LEFT JOIN` emit nulls on the right side; `RIGHT JOIN` mirrors that on the left.

**Visual builder**

The Builder tab on the same panel renders the query as drag/drop boxes. Each FROM/JOIN'd table appears as a box with its fields; drag a port between two field rows to add a JOIN. JOIN pills between boxes show the type (`INNER` / `LEFT` / `RIGHT`); click the pill to switch type, or click the inline ✕ to delete. Both tabs share the same SQL string — edits round-trip between them.

**Schema diagram**

The Schema diagram launcher in the Query dialog opens a read-only ER view of every records table in the workbook with relation arrows between them.

---

### Embed in other surfaces

A records grid can be embedded inside a `doc` page, a `dashboard` tile, or a `canvas` card via the records embed component. Pick the table + view; the embed renders the same grid surface and shares live data + collab.

---

### Agent integration

Every records operation is reachable from four layers, all mirrored:

- **SDK** — `createRecordsClient(host).addField(...)` etc.
- **CLI** — `xapps records-add-field <table> ...`
- **MCP** — `records.addField` tool, same args.
- **meshAgent toolkit** — the same set, registered as `recordsSurface.xappsToolkit` so agents in the same workspace pick them up.

Agents should track every engagement as a Kanban card and stamp it with `--created-by <agent-id>` so changes can be audited.

---

### Validation & errors

Mutations that fail validation return a `422` envelope with a `details.violations` array (field id + violation type + message). The grid surfaces validation errors as red borders on the offending cells (recs-23 work in progress). At the API layer, the envelope is the canonical contract; SDK / CLI / MCP all surface the same shape.

---

### Undo / redo

The toolbar's Undo / Redo buttons (and `Ctrl/Cmd+Z` / `Ctrl/Cmd+Y`) revert the last record-level mutation: cell edits, checkbox toggles, add row, rating, bulk delete, row reorder, linking records. Schema-level changes (add / remove / rename field) are not in the undo stack yet — those go through the schema editor and have their own confirm-on-destructive prompts.

---

### Coloring records & cells

The Color toolbar button opens a popover with three sections:

1. **Color a column** — per-field background + text swatches. Click any swatch to PATCH the field's `options.bgColor` / `options.fgColor`. The schema editor's Cell colors panel (expand a row to see it) writes to the same store.
2. **Color records by** — pick a singleSelect field; each row gets a left-bar tint that matches the selected option's color.
3. **Clear all** — removes every field's bg/fg + the color-by selection.

Both color paths persist on the field's `options`, sync via Y.js, and survive a hard reload.

---

### Storage shape

A records sheet stores its data inside a `recordsTables[]` array — one entry per tab in the strip. Each entry has:

| Field | Purpose |
| --- | --- |
| `id` | Stable table id (also the SQL table reference for `FROM Sheet.<id>` queries). |
| `name` | Tab label. |
| `fields` | Ordered array of field definitions. |
| `records` | `{ recordId: { fields, __autoNumber, __deletedAt? } }` map. |
| `views` | Saved views array (each with `type: 'grid' | 'kanban' | 'calendar' | 'gallery' | 'form' | 'pivot'` + config). Pivot views store their cross-tab spec at `config.pivot`. |
| `primaryFieldId` | Field marked as the table's primary key. |
| `nextId` | Counter used to mint sequential autoNumbers. |
| `hiddenFields` | Per-table hidden-field ids. |
| `links` | Edge table: `{ targetTableId: { targetRecordId: { sourceRecordId: true } } }`. |
| `history` | Per-record change log. |
| `comments` | Per-record comment threads. |

At the sheet level: `activeTableId` points to the table currently shown in the grid; switching tabs in the strip flips this. Legacy single-table sheets (pre-recs-57) auto-migrate into a single `recordsTables[]` entry on first load.

Soft-deleted records keep their data and can be restored via the trash list (`/records/deleted` → `/records/<id>/restore`).

#### Field keys (id-canonical)

A record's `fields` object is stored keyed by **field id** (`fld_…`) — the single canonical key. Field ids are stable across renames; field names are not, so id is what the grid, sort, filter, and SQL all read.

For convenience, every write path — `POST/PATCH /records`, the SDK (`createRecord` / `patchRecord`), CLI (`records-create` / `records-patch`), MCP (`records_create` / `records_patch`), the meshAgent toolkit, bulk-update, CSV import, and form submit — accepts a `fields` map keyed by **either** field id **or** field name. Name keys are normalized to the field-id key before the record is persisted (when both are supplied for the same field, the id value wins). Legacy records that were stored name-keyed are migrated to id keys the first time their table loads. Reads still tolerate either key, but new writes are always id-canonical.
