## 🗄️ Repository

### Track files with durable metadata, side-by-side previews, and full agent control

The **Repository** sheet type is a document management surface for files plus structured metadata. It combines:

- a filesystem-first browser rooted at the server repository root
- a tracking overlay that attaches durable metadata to files already on disk
- stable file IDs for tracked repository metadata rows
- category-specific metadata fields (Contract, Invoice, HR, Insurance, Proposal, Report, General)
- inline preview for common file types (PDF, images, more)
- API, CLI, and MCP coverage for row records and storage operations
- cloud-mount integration so files can live on `xApps files`, `My xApps storage`, or any connected cloud provider

> 🤖 Agent example: an agent can track an incoming contract, run AI extraction, populate the category fields, flag errors, and leave the human reviewer with the file preview and saved metadata side by side.

![Repository sheet showing filesystem folders, tracked files, and metadata](/help-assets/screenshots/repository-sheet.png)

---

### Features at a Glance

- Filesystem-backed browser with folder hierarchy
- Tracked-vs-untracked distinction so files in storage can graduate into managed records when ready
- Per-category metadata schemas with seven built-in categories (and full schema replacement via API/CLI)
- Stable file IDs that survive row reorder, sheet recreation, and workbook duplication
- Inline preview pane (PDF, images, fallback open/download for everything else)
- Side-panel split: **Preview** tab shows the file; **Metadata** tab shows the structured fields
- Editable `File Description`; everything else (size, type, created-by, created-at, updated-at) is derived/read-only
- Search + filter UI: stale-only filter, category filter, free-text search, clear-filters action
- 11 CLI commands and matching MCP tool set covering every read and mutation
- REST endpoints for file rows + category schema management
- `repo-refresh` and `repo-refresh-all` actions to re-stamp `lastRefreshedAt` after metadata edits

---

### Getting Started

1. **Add a Repository sheet.** Click the `+` button in the sheet tab bar and pick **Repository**. The sheet opens with the filesystem browser visible on the left and the side panel on the right.
2. **Upload or link a file.** Use the **Insert → Upload File** menu (or drop a file onto the sheet) to push it into the storage overlay; or **Insert → Add URL Reference** to record an external link instead.
3. **Pick a category.** When the row is created, the right side panel offers a category dropdown. Picking one (e.g. *Contract*) reveals the category-specific metadata fields (parties, effective date, expiration date, etc.).
4. **Fill in metadata.** Type into the side-panel fields; values write straight to the cell-backed columns and are visible in the grid.
5. **Preview the file.** Click the row; the **Preview** tab in the side panel renders PDFs / images inline, or shows an open/download button.
6. **Refresh after a change.** Use **Data → Refresh Selected Metadata** to re-stamp `lastRefreshedAt`. Use **Refresh All Metadata** for a bulk pass.

---

### Adding Files

- **Upload**: Upload one or more local files into the shared server-owned filesystem overlay and create matching repository rows.
- **Add URL**: Create a repository row that points at an external file URL.
- **New Folder**: Create filesystem folders inside the repository root to organize uploaded files.

Repository is a reflection of the current filesystem state, not a separate opaque file silo. The same tracked metadata remains available if you delete and recreate the visible Repository sheet because the durable metadata overlay lives at the workbook level.

Files that exist in storage but do not yet have repository metadata rows still appear in the Repository UI as `Untracked`. You can track them later to attach categories, descriptions, extraction state, and cell-backed metadata.

### Categories

Each file is assigned a category that controls its metadata schema:

| Category | Fields |
|---|---|
| Contract | Parties, Effective Date, Expiration Date, Value, Renewal Terms, Governing Law |
| Invoice | Vendor, Invoice #, Amount, Due Date, PO Number |
| HR Document | Person, Role, Department |
| Insurance | Provider, Policy #, Coverage, Premium, Expiration |
| Proposal | Client, Value, Due Date, Status |
| Report | Author, Period, Summary |
| General | Notes |

Categories can be replaced through the API, CLI, MCP, or the repository menu.

### Core Columns

Visible columns:

| Column | Field |
|---|---|
| A | Name |
| B | Category |
| C | Source |
| D | File Type |
| E | Size |
| F | URL |
| G | Upload Date |
| H | Status |
| I | Last Refreshed |
| Q | File Description |
| R | Updated At |
| S | Created By |

Hidden automation column:

| Column | Field |
|---|---|
| P | Stable file ID |

### Stable IDs

Repository rows now carry durable IDs. REST, CLI, and MCP all accept `row-or-id` addressing for single-file operations.

Use the ID when:

- agents may reorder or delete rows
- you want durable links between repository items and other sheet objects
- scripts need to revisit the same logical document later

Spreadsheet-style `Sheet!A1` references still apply to normal grid cells. Stable IDs are additive for repository records.

### Preview and Metadata

![Repository preview pane showing a tracked file rendered alongside the filesystem-backed browser](/help-assets/screenshots/repository-preview.png)

- PDFs preview inline.
- Images preview inline.
- Other file types show a download/open fallback.
- The right-side panel now has `Preview` and `Metadata` tabs.
- The metadata tab shows tracking state, extraction state, cell locations when available, stable ID, status, category, created/updated timestamps, file type, file size, description, and category-specific fields.
- `File Description` is editable. Derived fields such as creator, created time, updated time, file type, and file size are read-only.
- Storage-only files show `Untracked` state until you explicitly track them.

### Menu

Repository contributes:

- **Insert**: Upload File, Add URL Reference, New Folder
- **Data**: Refresh Selected Metadata, Refresh All Metadata, Remove Selected File, Edit Category Schemas
- **View**: Open Selected File, Toggle Side Panel, Toggle Data View, toggle stale-only filtering, Clear Search & Filters

### REST API

```text
GET    /api/sheets/:name/files
POST   /api/sheets/:name/files
GET    /api/sheets/:name/files/:rowOrId
PUT    /api/sheets/:name/files/:rowOrId
DELETE /api/sheets/:name/files/:rowOrId
PUT    /api/sheets/:name/files/:rowOrId/refresh
POST   /api/sheets/:name/files/refresh-all

GET    /api/sheets/:name/categories
PUT    /api/sheets/:name/categories
```

### CLI

```text
xapps repo-files <sheet>
xapps repo-file <sheet> <row-or-id>
xapps repo-file-metadata <sheet> <row-or-id>
xapps add-repo-file <sheet> <url> [--name <name>] [--category <cat>] [--id <id>]
xapps update-repo-file <sheet> <row-or-id> <json>
xapps set-repo-file-metadata <sheet> <row-or-id> <json>
xapps remove-repo-file <sheet> <row-or-id>
xapps repo-categories <sheet>
xapps set-repo-categories <sheet> <json>
xapps repo-refresh <sheet> <row-or-id>
xapps repo-refresh-all <sheet>
```

### MCP Tools

`list_repo_files`, `get_repo_file`, `add_repo_file`, `update_repo_file`, `remove_repo_file`, `list_repo_categories`, `update_repo_categories`, `refresh_repo_file`, `refresh_all_repo_files`

### Storage Access Note

Repository storage browsing is mount-backed now. The Repository UI reads and mutates `xApps files`, `My xApps storage`, and connected cloud providers through `/api/cloud`, while `/api/sheets/:name/files*` manages tracked metadata rows only.

That said, `/repository/...` asset URLs are still capability-style URLs, not password-protected document access. Treat them as shareable file links, not as strong access control for sensitive documents.

---

### Search & Filter

The header bar exposes:

- **Free-text search** — matches against name + description + category-specific fields.
- **Stale-only toggle** — show only rows whose `lastRefreshedAt` is older than a configurable threshold (helps catch documents that have drifted out of sync with their source).
- **Category filter** — narrow to a single category at a time.
- **Clear search & filters** — reset to the full list (also exposed under **View → Clear Search & Filters**).

The active query is part of the URL hash so a search stays bookmarkable.

---

### Common Workflows

- **Onboarding a new vendor.** Drop their MSA + insurance certificate into a folder, set categories *Contract* and *Insurance*, fill effective dates and expiration. Use a Spreadsheet sheet's `=COUNTIFS('Repo'!B:B,"Contract")` to surface contract counts on a dashboard.
- **Quarterly contract audit.** Filter by category=Contract, sort by Expiration Date asc, walk the top of the list. The stable file IDs mean follow-up tasks linked from a Kanban board still resolve back to the right document next quarter.
- **AI metadata extraction.** Upload a PDF, run an extraction agent against the file URL, then `set-repo-file-metadata` writes the extracted fields back. The human reviewer sees the document preview alongside the populated metadata for spot-checking.
- **Cross-workbook archive.** Repository rows travel with the workbook file, but the underlying storage lives in the workspace's mount tree. Detaching a workbook still preserves the metadata rows (the file URLs may break — keep that in mind if you're packing up for offline use).

---

### Known Follow-Ups

- **Custom categories beyond the built-in seven** — `set-repo-categories` already accepts arbitrary schemas, but the side-panel UI assumes the built-in shapes; a generic category-builder dialog would let users define their own.
- **Bulk metadata edit** — currently per-row; multi-select + bulk-set-metadata would speed up annotated batches.
- **Version history** — only the latest version of each file is tracked; capturing prior versions inline (or via cloud-storage version IDs where supported) is a natural extension.
- **Full-text PDF search** — preview is rendered today, but the contents aren't indexed. Server-side OCR + a search index would unlock real document search.
