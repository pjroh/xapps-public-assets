## Records Tables

### Build a table people can use

Records is for repeated things with consistent fields: contacts, inventory, requests, deals, or assets. Start with one table and a clear name. Add another table when it represents a different kind of thing, not merely a filtered subset.

1. Create a table from a suitable template or define its fields. Use text for identifiers that must retain leading zeros, numbers for calculations, and select fields for controlled categories.
2. Add a few representative records before importing a large file. Open one record's detail panel and check that the important information is easy to read and edit.
3. Choose a view for the task: a grid for detailed editing, a form for entering one record, a board for stages, a calendar for dates, or a pivot for summaries. Different views still refer to the same table data.
4. Apply a filter and sort for a useful question, such as “Which active deals close this month?” Save the view so colleagues can repeat the same review.
5. Import CSV after reviewing the field mapping and preview. Confirm record counts and a few values afterward. Upsert can update matching records, so review its match field carefully instead of assuming every row is new.

### Connect related tables

For an inventory workbook, keep **Inventory** and **Suppliers** as separate tables. Add a relation field on Inventory pointing to Suppliers, then use the relation picker to select the supplier record. A lookup displays a related value; a rollup summarizes related values; a count answers how many related records there are. A copied supplier name is ordinary text and will not become a relationship automatically.

### Answer a question with Query

Click **Analyze** to open **Query records**. Start with a bounded read such as `SELECT * FROM Inventory LIMIT 50`, using the actual table name. Click **Run** and wait for the result grid or a visible error. The query editor, visual builder, and schema diagram help you describe the read; the displayed rows are a result, not another editable copy of your source table.

If the query fails, check the exact table and field names, selected workbook, and SQL message. Do not interpret an empty result as missing data until you have removed restrictive filters and checked the source table. Qualified names such as `Sheet.Table` help distinguish tables in a larger workbook.

### Recover a record or find a hidden table

Clear filters and check the active table first. Hiding a table preserves it; its menu can restore visibility. Deleted records use soft-delete and Trash. Review the recovery controls before recreating records, which would give them new identities and may break intended relations. Use the record's activity/history to understand edits, and Undo/Redo for supported recent actions.

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
- Typed saved views: **grid**, **form**, **kanban**, **calendar**, **gallery**, **pivot**, **timeline**, and **gantt** — saved per-table and switchable from the view chip
- Filter / sort / group on every view, with collapsible row groups + per-group aggregates + Expand all / Collapse all
- Per-field cell colors (background + text) via the Color toolbar popover or the schema editor's Cell colors panel; "Color records by" tints the left bar by a singleSelect option
- Star rating field (1–N stars, click to set, click again to clear)
- Airtable-style 12-color chip palette for singleSelect / multiSelect
- Linked-record picker — click any relation cell to choose target records
- Relation hover previews with target-record display values
- Per-record detail panel with Fields / Activity / Linked tabs + a chronological comment log
- Per-record history (every cell change, with actor + timestamp)
- Validation (required / unique / type) with structured `422` envelopes
- CSV import with upsert + rollback-on-error
- CSV export with column picker + delimiter choice
- SQL query panel: text editor with autocomplete + Format + saved queries, side-by-side visual builder (tables-as-boxes, drag-to-JOIN ports, INNER/LEFT/RIGHT pill switcher, inline ✕ delete), and a Schema diagram launcher
- SQL grammar: SELECT / DISTINCT / WHERE / GROUP BY / HAVING / ORDER BY / LIMIT / aggregates / CASE / scalar functions / **INNER · LEFT · RIGHT · CROSS JOIN with qualified column refs (`r.Name`)**
- Multiple tables per sheet — a single Records sheet can hold multiple tables; the left navigation switches between them, and SQL FROM clauses can reference either the sheet's active table or `Sheet.Table` explicitly
- Formula expression language (~68 functions across text/logic/math/date/regex/array/record) with autocomplete, field picker, and live preview
- Undo / redo (Ctrl+Z / Ctrl+Y) for cell edits, add row, rating, bulk delete, row reorder, link records
- Table navigation with Rename / Hide / Delete / Restore actions

CSV preview, import, and export use the same server contracts from the browser, SDK, CLI, MCP, and hosted tools. CLI equivalents are `records-preview-csv <sheet> <file>`, `records-import-csv <sheet> <file>`, and `records-export-csv <sheet>`; add `--table-id` for an explicit table and pair `--expected-revision` with `--request-id` for replay-safe imports.

Records automations use the same layered contract. `records-list-automations`, `records-add-automation`, `records-update-automation`, `records-test-automation`, `records-automation-runs`, and `records-automation-effects` delegate to the typed Records SDK. Guarded mutations pair `--expected-revision` with `--request-id`; exact retries replay without running actions twice. Run/effect entries persist stable request, trace, run, and effect identities. Webhook URLs are checked against local/private targets, sensitive headers are rejected, secrets are redacted from reads, and ambiguous interrupted delivery requires explicit `records-retry-automation-effect --allow-ambiguous` recovery.

![Records grid with Airtable-style chrome](/help-assets/screenshots/records-grid.png)

---

### Multiple tables in one sheet

A single Records sheet can hold many tables — switch between them in **Tables** in the left navigation. Each table has its own schema, records, views, and history. Use the `+` beside **Tables** or **New table** to add one. Its menu offers Rename / Hide / Delete. Hidden tables retain their data and can be restored.

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

- **Left navigation** — Tables switches the active table; Views chooses a saved view. The Build actions open New table, New view, View options, Fields, Analyze, Import, Interfaces, and Automations. Table menus manage names, visibility, and removal.
- **Toolbar** — Hide fields, Filter, Group, Sort, Color, Row height, Share view, and More control the current view. **Edit fields** opens Field Manager; **Import CSV** opens import; **Analyze** opens Query records. **Search records** searches the table. The context line below identifies the active table and view.
- **Header row** (sticky) — one `<th>` per visible field with type icon + name + sort arrow. Each header is draggable for reorder; the 6px handle on the right edge drags column width. The `▾` caret in the header opens the field options menu.
- **Body** — one row per record. The `#R-NNN` autonumber lives in a sticky left column; the per-row checkbox lives in another sticky column to its left.
- **Group header rows** — when the active view is grouped, the body is partitioned by the group fields' display values. Grouping nests up to 3 levels ("Group by … then by … then by …"); each header row carries a field-name eyebrow, a colored value pill, a Count, and per-column aggregates aligned under their columns (honoring the summary-bar picks, else the type default). The chevron toggles collapse (deeper levels are indented and tinted).
- **Add-row strip + footer** — `+ Add a record` at the bottom inserts a record and focuses the first editable cell. The footer chips show the live record count plus per-field aggregates (Σ on numbers, true-count on checkboxes, won/done/closed counts on selects).

---

### Creating a table

Two paths:

1. Add a Records sheet from the workbook's sheet picker. Inside Records, use **New table** or the `+` beside **Tables** to create another table, and **Edit fields** to define its schema or start from a template.
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
- **rollup** — aggregate a field across linked records. Aggregators: `sum`, `avg`, `median`, `range`, `min`, `max`, `count`, `distinctCount`, `unique` (distinct values joined), `concat`, `percentChecked` (% truthy), `and`/`or` (all/any truthy), `earliestDate`/`latestDate`.
- **count** — count linked records.

**Conditional lookup / rollup / count** — each of these accepts an optional `options.filter` (a view-filter shape: `{ conjunction, clauses|children }`) evaluated against each *linked* record, so the field includes only the linked records that match. E.g. a rollup with `filter: { clauses: [{ field: "Status", op: "eq", value: "done" }] }` sums only the linked records whose Status is done; a count with the same filter counts only those. Clause field refs resolve by field id or name on the linked table; a filter that matches nothing yields `0` for count/sum and blank for lookup. Set it via the field options on create/patch (API, CLI `records-add-field`, MCP) — it recomputes on the next read.
- **formula** — derived value from an expression with a ~68-function library (autocomplete shows signatures). Errors render in red. Functions by category:
  - **Logical**: `IF`, `SWITCH`, `AND`, `OR`, `NOT`, `XOR`, `ISERROR`, `ISBLANK`, `BLANK`, `TRUE`, `FALSE`
  - **Text**: `CONCAT`, `LEN`, `UPPER`, `LOWER`, `TRIM`, `CONTAINS`, `LEFT`, `RIGHT`, `MID`, `FIND`, `SEARCH`, `SUBSTITUTE`, `REPLACE`, `REPT`, `PROPER`, `T`, `VALUE`, `ENCODE_URL_COMPONENT`
  - **Regex**: `REGEX_MATCH`, `REGEX_EXTRACT`, `REGEX_REPLACE` (JS regex; escape backslash classes as `\\w` inside a string)
  - **Math**: `ABS`, `ROUND`, `SUM`, `AVG`, `COUNT`, `MIN`, `MAX`, `MOD`, `POWER`, `SQRT`, `EXP`, `LN`, `LOG`, `INT`, `TRUNC`, `SIGN`, `CEILING`, `FLOOR`, `ROUNDUP`, `ROUNDDOWN`, `EVEN`, `ODD`, `ISEVEN`, `ISODD`
  - **Date/time**: `NOW`, `TODAY`, `DATEADD`, `DATETIME_DIFF`, `DATETIME_FORMAT`, `DATETIME_PARSE`, `DATESTR`, `TIMESTR`, `YEAR`, `MONTH`, `DAY`, `HOUR`, `MINUTE`, `SECOND`, `WEEKDAY`, `WEEKNUM`, `IS_BEFORE`, `IS_AFTER`, `IS_SAME`, `WORKDAY`
  - **Array** (over the argument list): `ARRAYJOIN`, `ARRAYUNIQUE`, `ARRAYCOMPACT`
  - **Record**: `RECORD_ID`, `CREATED_TIME`, `LAST_MODIFIED_TIME`
- **ai** — governed, cached AI value produced per record. Configure a prompt template such as `Summarize this product: {{Notes}}`; the cell exposes Run/Retry and its durable status. Successful structured output is written atomically with citations and provenance; blocked or invalid output does not replace the prior value.

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
- **timeline** / **gantt** — records laid out by configured start/end and label fields.

Switching views replaces the toolbar's view chip label and re-renders the body. The view list lives in the view chip dropdown; **Manage saved views…** opens a reorder/rename/delete modal.

**Shared view config (applies to every type)**

- **Filter** — boolean expression over fields (e.g. `Status = "Won" AND Amount > 1000`).
- **Sort** — one field + direction.
- **Group by** — partition rows by a field's value; the group header shows count + per-column aggregates and is collapsible. Group by up to 3 fields for nested subgroups (the Group popover shows an ordered "Group by … then by …" stack with per-level field selects, remove, and "+ Add subgroup"). Expand all / Collapse all flip every group at every level. Saved views store the chain as `view.config.groupByFieldIds`; the legacy single-field `groupBy` still loads.
- **Hidden fields** — per-view list of fields to hide.
- **Color records by** — save a singleSelect field whose option color becomes each grid row's left accent.

Views persist per-table inside the workbook (`recordsTables[<id>].views[]`).

![View chip dropdown showing saved views and quick-action buttons](/help-assets/screenshots/records-views.png)

**Managing saved views:**
- Click the view chip (e.g. "Grid view") to open the view list.
- **New saved view…** — pick a type and give it a name. Opens to the active type immediately.
- **Manage saved views…** — opens a modal to reorder, rename, or delete views.
- The active filter/sort/group for the current view is shown in the toolbar.
- `xapps records-add-view`, `records-get-view`, `records-update-view`, and `records-pivot-drill` expose the same typed contracts through the CLI; MCP and hosted tools use the matching underscore names.

**Filtering records:**

The Filter panel (toolbar → Filter) adds row conditions to the active view. Each condition picks a field, an operator (`=`, `≠`, `contains`, `is empty`, `>`, `<`, `≥`, `≤`, `in`), and a value; the panel's And/Or selector sets how sibling conditions combine. The condition count badge on the Filter button lights up when filters are active.

**Nested condition groups.** "+ Add condition group" inserts a group — a bracketed sub-list with its own And/Or — so filters like `Status = "Won" AND (Owner = "Maya" OR Owner = "Aki")` compose directly. Groups nest up to 3 levels deep, with at most 50 conditions in total.

Saved views store this as `view.filter`. Two shapes are accepted, never combined: legacy flat `{ conjunction, clauses: [{field, op, value}] }`, or nested `{ conjunction, children: [...] }` where each child is a clause or a `{ conjunction, children }` group. Existing flat filters keep working unchanged; the same evaluator drives the grid, saved-view activation, and embed resolution.

**Conditional record coloring.** The Color popover's "Color records by conditions" section holds ordered rules — each rule pairs a bar color with a condition (`When <field> <op> <value>`); the first matching rule paints the record's left color bar and beats the select-field coloring below it. Rules reorder with ↑/↓ and persist per table; saved views store them as `view.config.colorRules: [{ color: "#rrggbb", filter: <view.filter shape> }]` (up to 10 rules, filters may use nested condition groups via the API).

**Per-column summary bar.** The grid's sticky footer row shows one aggregate per column, aligned under its column — record count pinned at the left. Click any footer cell to pick the aggregate: Count, Empty, Filled, Unique, % Empty/Filled/Unique everywhere; Sum, Avg, Median, Min, Max, Range on numeric columns; Earliest/Latest on dates; Checked/Unchecked/% Checked on checkboxes; or None. Defaults mirror the old chips (Sum on numbers, Checked on checkboxes). Aggregates compute over the filtered rows only, format per the column (currency, percent), persist per table, and saved views store them as `view.config.summaries: { <fieldId>: "<agg>" }`.

**Color as data across views.** The same row color (conditional rules first, then color-by-select) carries into every view of the table: kanban cards get a left color edge, calendar chips a left bar, gallery cards a top accent strip, and timeline/gantt bars take the record's color instead of the rotation palette. The Color popover's "Tint select cells" toggle additionally washes singleSelect grid cells with their option's pastel background (`view.config.selectCellTint`).

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

Under the hood the pivot config is compiled to a `GROUP BY` query and run through the same SQL engine as the **Query** tool, then reshaped client-side. The config persists at `views[<id>].config.pivot` with resolved `expr` + `label` per dimension. Cell drill-down posts its row/column selection to the saved-view route, so the server rebuilds the underlying-record query from the validated pivot config rather than accepting browser-authored SQL.

---

### Per-record detail panel

Click the **autonumber button** (`1`, `2`, …) in the left column of any row to open the record's detail panel in a side drawer.

![Record detail panel showing all field values, Comments, Activity, and Linked tabs](/help-assets/screenshots/records-detail-panel.png)

The detail panel has four tabs:

- **Fields** — all field values in a stacked form layout. Every field is editable inline. Click **Open in form** (top-right) to open the record in a full-page form view.
- **Comments** — a flat chronological discussion log on that record. `@name` remains plain comment text; server-side threading, reactions, and mention parsing are not part of this contract. Supports edit and delete of your own comments.
- **Activity** — per-field change log (who changed what, old → new value, timestamp). Filter by field id via CLI: `xapps records-history <sheet> <recordId> [--field-id <fieldId>]`.
- **Linked** — records in other tables that link to this record (backlinks from relation fields).

**Duplicate a record** — in the row's right-click context menu or via CLI: `xapps records-duplicate <sheet> <recordId>`. Creates a new record with the same field values; relation links are not copied.

---

### Linking records

1. Add a `relation` field; in the schema editor pick the target table.
2. In the grid, click any cell of that field — the linked-record picker opens.
3. Type to search the target table, check the records you want to link, click Apply. Multi-link supported via the field's options.
4. Lookup / rollup / count fields can then pull data from the linked rows.

Hovering a relation cell shows a tooltip with the target records' primary-field values (recs-13).

Agents can use `records-list-links`, `records-link`, and `records-unlink`; guarded writes accept `--expected-revision` with a stable `--request-id` so retries do not duplicate links.

---

### Bulk operations

- **Select rows** — header checkbox toggles all; per-row checkboxes; `Shift+Click` selects a range.
- **Bulk delete** — the floating bar at the bottom shows the count + a red Delete button. Undo restores them.
- **Bulk update** — via SDK / CLI: `xapps records-bulk-update <table> <ids> --patch '{...}'`.
- **Batch create / patch** — one persisted request for mixed creates and updates: `xapps records-batch <table> '[{"type":"create","fields":{...}},{"type":"patch","recordId":"rec_...","fields":{...}}]'`.
- **Batch add fields** — one persisted schema request for an ordered set of non-relation fields: `xapps records-add-fields <sheet> '[{"name":"Title","type":"text","primary":true},{"name":"Status","type":"singleSelect","options":{"options":[]}}]'`. Quick-start templates use this path, so selecting a template saves and syncs once instead of once per field.
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

Queries run with bounded input, join, intermediate-memory, result and execution
budgets. A small `LIMIT` does not make an unbounded join safe: overly broad
queries fail with `records_sql_budget_exceeded` instead of partial results.
Reduce the source data or simplify the join. If query capacity is busy, retry
after an active query completes. These failures do not modify workbook data.

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

A destination surface can persist a Records embed after you pick its source table, saved view, fields, order, and row limit. The versioned descriptor is bound to the open workbook file and destination sheet; missing/deleted targets render a visible error instead of reading a different workbook. Agents can discover stable choices with `records-list-embed-sources <sheet>` and validate/read back a descriptor with `records-resolve-embed <descriptor-json>`; the matching SDK and tool methods are `listEmbedSources` / `resolveEmbed` and `records_list_embed_sources` / `records_resolve_embed`.

---

### Agent integration

Every records operation is reachable from four layers, all mirrored:

- **SDK** — `createXAppsClient(...).records.addField(...)`, `addFields(...)`, and related `client.records.*` helpers. Pass `{ tableId: "tbl_..." }` to target a specific Records table instead of the active table.
- **CLI** — `xapps records-add-field <sheet> ...` and `xapps records-add-fields <sheet> <fields-json>`; table-scoped commands accept `--table-id <id>`. The CLI also covers saved queries, forms, links, record/view reorder, table metadata, and dependency-aware schema operations (`records-integrity-plan` / `records-integrity-undo`).
- **MCP** — `records_*` tools expose the same SDK-backed surface, including `records_add_fields`, `records_batch`, `records_submit_form`, `records_list_queries`, and `records_schema_health`.
- **meshAgent toolkit** — the `xapps-records` toolkit publishes first-class `records_*` functions. If only the core workbook toolkit is visible, run `workbook_search(["records"])` then `workbook_command_schema("records-batch")` to find the right Records tool and schema before falling back.

Formula and AI execution use the same contract at every layer: `records-formula-parse`, `records-formula-preview`, `records-formula-recalculate`, `records-ai-run`, `records-ai-status`, and `records-ai-retry` (underscore names in MCP/toolkit). AI retries require the current run revision plus a stable mutation id, so reconnects can safely replay without duplicate writeback.

For repository work, select tracking from the canonical `AGENTS.md` work-class table; Git-only operations and small fixes have lighter paths. When a Kanban card is required, stamp it with stable `--created-by <agent-id>` and use the guarded scoped card contract. Using Records alone does not mandate a tracking workbook.

---

### Validation & errors

Mutations that fail validation return a `422` envelope with a `details.violations` array (field id + violation type + message). The grid surfaces validation errors as red borders on the offending cells (recs-23 work in progress). At the API layer, the envelope is the canonical contract; SDK / CLI / MCP all surface the same shape.

---

### Undo / redo

The toolbar's Undo / Redo buttons (and `Ctrl/Cmd+Z` / `Ctrl/Cmd+Y`) revert record-level mutations. Field/table deletion is dependency-aware: preview with `records-integrity-plan`, use explicit cascade repair when dependencies exist, and restore the persisted workbook-wide snapshot with `records-integrity-undo`.

---

### Coloring records & cells

The Color toolbar button opens a popover with three sections:

1. **Color a column** — per-field background + text swatches. Click any swatch to PATCH the field's `options.bgColor` / `options.fgColor`. The schema editor's Cell colors panel (expand a row to see it) writes to the same store.
2. **Color records by** — pick a singleSelect field; each row gets a left-bar tint that matches the selected option's color.
3. **Clear all** — removes every field's bg/fg + the color-by selection.

Both color paths persist on the field's `options`, sync via Y.js, and survive a hard reload.

---

### Storage shape

A records sheet stores its data inside a `recordsTables[]` array — one entry per table in the left navigation. Each entry has:

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
| `comments` | Per-record chronological comments. |
| `aiRuns` / `aiRunReceipts` | Bounded durable AI lifecycle and idempotent retry ledger. |

At the sheet level: `activeTableId` points to the table currently shown in the grid; selecting another table changes this. Legacy single-table sheets migrate into a single `recordsTables[]` entry on first load.

Soft-deleted records keep their data and can be restored via the trash list (`/records/deleted` → `/records/<id>/restore`).

#### Field keys (id-canonical)

A record's `fields` object is stored keyed by **field id** (`fld_…`) — the single canonical key. Field ids are stable across renames; field names are not, so id is what the grid, sort, filter, and SQL all read.

For convenience, every write path — `POST/PATCH /records`, `/records/batch`, the SDK (`createRecord` / `patchRecord` / `batchRecords`), CLI (`records-create` / `records-patch` / `records-batch`), MCP (`records_create` / `records_patch` / `records_batch`), the meshAgent toolkit, bulk-update, CSV import, and form submit — accepts a `fields` map keyed by **either** field id **or** field name. Name keys are normalized to the field-id key before the record is persisted (when both are supplied for the same field, the id value wins). Legacy records that were stored name-keyed are migrated to id keys the first time their table loads. Reads still tolerate either key, but new writes are always id-canonical.
