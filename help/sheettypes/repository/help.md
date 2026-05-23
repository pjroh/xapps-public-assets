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

![Repository sheet showing the Library list with color-coded category badges across all seven built-in categories](/help-assets/screenshots/repository-sheet.png)

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

![Repository preview tab showing a tracked file's download fallback for a URL-based document](/help-assets/screenshots/repository-preview.png)

- PDFs preview inline.
- Images preview inline.
- Other file types show a download/open fallback.
- The right-side panel has **Preview** and **Metadata** tabs.

![Repository Metadata tab showing stable ID, cell locations, category, file description, and repository actions including Analyze and Untrack](/help-assets/screenshots/repository-metadata.png)

The **Metadata** tab shows:
- Row and cell-range location (e.g. `Row 1`, `A1:AA1`)
- Stable file ID (e.g. `repo-d420d7f3-…`)
- Tracking badge (`Tracked` / `Untracked`)
- **File Name** (A) and **Category** (B) — category is editable from a dropdown
- **Status** (H) — `tracked`, `pending`, `processed`, `reviewed`, `error`
- **File Description** (Q) — editable free-text description
- Repository Actions: **Open in File Viewer**, **Analyze**, **Untrack**
- Tracking State, Tagging State, Extraction State, Created By
- Time Created and Time Updated
- Category-specific metadata fields (e.g. Parties, Effective Date, Expiration Date for a Contract)

`File Description` is editable. Derived fields such as creator, created time, updated time, file type, and file size are read-only.
Storage-only files show `Untracked` state until you explicitly track them.

### Menu

Repository contributes:

- **Insert**: Upload File, Add URL Reference, New Folder, New Top-Level Folder
- **Data**: Track Selected File, Track Selected Folder Recursively, Untrack Selected File, Rename Selected File, Refresh Selected Metadata, Refresh Source, Track & Analyze Selected, Clear Selected Error, Remove Selected File, Edit Category Schemas
- **View**: Open Selected File, Open Selected in File Viewer, Hide/Show Side Panel, Show Stale Files Only, Clear Search & Filters, **Toggle Data View** (switch between the Repository browser and the raw backing spreadsheet)

**Toggle Data View** reveals the underlying spreadsheet grid — useful for bulk-editing cells, applying formulas, or auditing the raw cell state of every tracked file. A blue banner appears at the top of the data view with a reminder to toggle back.

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

**CLI notes:**
- Use `--workbook "MyFile.json"` or `--file "MyFile.json"` to target a specific workbook when the CLI default isn't the workbook you intend.
- `--category` in `add-repo-file` accepts lowercase category IDs: `contract`, `invoice`, `hr`, `insurance`, `proposal`, `report`, `general`. The category can also be changed later via `update-repo-file`.
- `update-repo-file` patches top-level file properties (name, category, description, status). Use `set-repo-file-metadata` to patch category-specific fields by field name (e.g. `{"Parties":"...", "Effective Date":"..."}`) or by column letter (e.g. `{"J":"...", "K":"..."}`). The field-name form requires the category to already be set correctly on the file row.
- `repo-refresh` / `repo-refresh-all` stamp `lastRefreshedAt` only; they do not re-download or re-analyze content.

**Example — add a contract and set metadata:**
```bash
xapps --file MyRepo.json add-repo-file Library https://example.com/msa.pdf \
  --name "Vendor MSA 2024" --category contract
xapps --file MyRepo.json set-repo-file-metadata Library repo-<id> \
  '{"Parties":"ACME Corp","Effective Date":"2024-01-01","Expiration Date":"2026-12-31"}'
```

### MCP Tools

`list_repo_files`, `get_repo_file`, `add_repo_file`, `update_repo_file`, `remove_repo_file`, `list_repo_categories`, `update_repo_categories`, `refresh_repo_file`, `refresh_all_repo_files`

### Storage Access Note

Repository storage browsing is mount-backed now. The Repository UI reads and mutates `xApps files`, `My xApps storage`, and connected cloud providers through `/api/cloud`, while `/api/sheets/:name/files*` manages tracked metadata rows only.

That said, `/repository/...` asset URLs are still capability-style URLs, not password-protected document access. Treat them as shareable file links, not as strong access control for sensitive documents.

---

### Search & Filter

![Free-text search filtering the library to show only files matching "Contract"](/help-assets/screenshots/repository-search.png)

The header bar exposes:

- **Free-text search** — matches against name + description + category-specific fields.
- **Stale-only toggle** — show only rows whose `lastRefreshedAt` is older than a configurable threshold (helps catch documents that have drifted out of sync with their source). Access via **View → Show Stale Files Only**.
- **Category filter** — narrow to a single category at a time (All Categories, Contract, Invoice, HR Document, Insurance, Proposal, Report, General).
- **File filter** — show All Files, only Tracked, or only Untracked files.
- **Clear search & filters** — reset to the full list (also exposed under **View → Clear Search & Filters**).

The active query is part of the URL hash so a search stays bookmarkable.

---

### Common Workflows

- **Onboarding a new vendor.** Drop their MSA + insurance certificate into a folder, set categories *Contract* and *Insurance*, fill effective dates and expiration. Use a Spreadsheet sheet's `=COUNTIFS('Repo'!B:B,"Contract")` to surface contract counts on a dashboard.
- **Quarterly contract audit.** Filter by category=Contract, sort by Expiration Date asc, walk the top of the list. The stable file IDs mean follow-up tasks linked from a Kanban board still resolve back to the right document next quarter.
- **AI metadata extraction.** Upload a PDF, run an extraction agent against the file URL, then `set-repo-file-metadata` writes the extracted fields back. The human reviewer sees the document preview alongside the populated metadata for spot-checking.
- **Cross-workbook archive.** Repository rows travel with the workbook file, but the underlying storage lives in the workspace's mount tree. Detaching a workbook still preserves the metadata rows (the file URLs may break — keep that in mind if you're packing up for offline use).

---

### AI Analysis

The **Analyze** button in the Metadata tab (and **Data → Track & Analyze Selected**) submits the file for AI extraction. The analysis extracts:

- Detected category and confidence score
- Title and summary
- Key parties
- Key dates and key values
- Key terms (tags)
- Extracted fields mapped to the category schema

AI analysis requires an OpenAI API key configured on the server. When the key is unavailable, the button is still present but the request will return an error. Extraction results are stored in the backing sheet's AI analysis columns (T–AA range) and are visible in the Metadata panel after a successful run.

After analysis, the Extraction State field in the Metadata panel transitions from `Tracked` to `Processed`.

---

### Data View

The **Toggle Data View** menu item (under **View**) switches the Repository surface to display the raw backing spreadsheet. This is the same spreadsheet that stores all tracked-file rows, category fields, and stable IDs.

Use Data View when you need to:
- Apply a formula to a column across all files
- Inspect raw cell values for debugging
- Use Spreadsheet-style filtering or conditional formatting on the repository data

A blue banner at the top of the grid confirms you are in Data View. Toggle back via the same menu item.

---

### Known Follow-Ups

- **Custom categories beyond the built-in seven** — `set-repo-categories` already accepts arbitrary schemas, but the side-panel UI assumes the built-in shapes; a generic category-builder dialog would let users define their own.
- **Bulk metadata edit** — currently per-row; multi-select + bulk-set-metadata would speed up annotated batches.
- **Category filter limitation** — the Category dropdown in the toolbar filters by the storage-browser path; URL-based files (added via `add-repo-file`) appear in the tracked-files list but may not respond to the Category filter when the cloud source is active. Use the free-text search box as an alternative.
- **Version history** — only the latest version of each file is tracked; capturing prior versions inline (or via cloud-storage version IDs where supported) is a natural extension.
- **Full-text PDF search** — preview is rendered today, but the contents aren't indexed. Server-side OCR + a search index would unlock real document search.
