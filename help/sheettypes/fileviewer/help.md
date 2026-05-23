## File Viewer

### Preview uploaded files inside a workbook

File Viewer sheets let you upload and preview documents, spreadsheets, presentations, drawings, and images without leaving the workbook. Each file is mirrored into the sheet grid so agents, formulas, and other workbook tools can reference file metadata.

> 🤖 Agent example: an agent can load a markdown spec, inspect the live preview, switch into source editing, and keep the file readable for humans while preserving machine-facing workbook references.

![File Viewer showing a live document preview inside the workbook shell with Markdown file active and the file list on the left](/help-assets/screenshots/fileviewer-sheet.png)

---

### Features

- Preview 20+ file formats inline
- File list management (add, remove, set active)
- Spreadsheet mirror refs (columns A--E per file)
- Page rail navigation for multi-page documents
- Section rail for Markdown headings
- Zoom controls
- Inline text editing for Markdown, JSON, JS, Python, and plain text files
- Text content read/write API for programmatic file editing
- Template variables in text content
- Cross-sheet cell formula access to file metadata
- Cell ref API for programmatic spreadsheet mirror reads
- File upload via drag-and-drop, file picker, or HTTP POST to `/api/uploads`
- PDF native rendering with thumbnail page rail
- XLSX rendering with sheet tabs and styled cells
- DOCX rendering with bullet and paragraph support
- DXF architectural drawing preview
- Cloud file pointers (Google Drive, OneDrive, opaque references)
- Visual regression testing framework

---

### Supported Formats

| Category | Extensions |
|---|---|
| Spreadsheets | `.xlsx`, `.xls`, `.ods`, `.csv` |
| Documents | `.docx`, `.md`, `.markdown`, `.pdf` |
| Presentations | `.pptx` |
| Drawings | `.dxf` |
| Images | `.png`, `.jpg`, `.jpeg`, `.gif`, `.webp`, `.svg`, `.bmp`, `.avif`, `.tif`, `.tiff` |
| Editable text | `.md`, `.markdown`, `.txt`, `.text`, `.json`, `.js`, `.mjs`, `.cjs`, `.py` |

---

### Getting Started

1. Create a new sheet and choose **File Viewer** from the sheet type menu.
2. Upload a file by clicking the **Upload Files** button, dragging a file onto the viewer, or using the CLI `add-viewer-file` command.
3. The file appears in the file list on the left. Click it to preview.
4. Use the page rail (for PDFs, DOCX, PPTX) or section rail (for Markdown) to navigate within the file.
5. For editable text files (Markdown, JSON, JS, Python, plain text), click **Edit source** in the toolbar to open the inline editor.
6. Reference file metadata from any other sheet using cell formulas.

---

### File Management

Each File Viewer sheet maintains a list of files. One file at a time is the **active file**, which is displayed in the preview pane.

- **Add files** via upload, URL, or the CLI `add-viewer-file` command
- **Remove files** via the file list context menu or the CLI `remove-viewer-file` command
- **Set active file** by clicking in the file list or using `set-active-viewer-file`
- Files persist in the workbook JSON and can be managed programmatically

---

### Spreadsheet Mirror Refs

Each file is mirrored into the sheet grid so that formulas and agents can reference file metadata:

| Column | Field | Example |
|---|---|---|
| A | File name | `report.xlsx` |
| B | File type/extension | `xlsx` |
| C | File size (bytes) | `245760` |
| D | Source URL | `/uploads/report-abc.xlsx` |
| E | File ID | `fv-m1abc123` |

Row numbering is 1-based: the first file maps to `A1:E1`, the second to `A2:E2`, and so on.

The active preview shows its mirrored range in the toolbar (e.g., `A1:E1`) and its source cell (e.g., `D1`).

#### Cross-sheet formula access

Reference file metadata from any other sheet:

```
='Viewer'!A1       -- returns the filename of the first file
='Viewer'!C1       -- returns the file size in bytes
='Viewer'!D1       -- returns the source URL
```

---

### Preview Rendering

#### XLSX / XLS / ODS / CSV

Spreadsheet files render as styled HTML tables with:

- Multiple sheet tabs (for multi-sheet workbooks)
- Cell styles: fonts, colors, borders, number formats
- Merged cells
- Column and row sizing

![File Viewer rendering a CSV file as a styled table with column headers and row data](/help-assets/screenshots/fileviewer-upload.png)

#### DOCX

Word documents render with:

- Paragraph styles and formatting
- Bullet and numbered lists
- Images and embedded media
- Text-based page cards in the page rail for reliable navigation

Note: The DOCX renderer requires JSZip to be loaded before docx-preview. This is handled automatically.

#### PPTX

PowerPoint files render slide-by-slide with a page rail for thumbnail navigation.

#### PDF

PDF files render natively in the browser via embed. The page rail shows clickable thumbnails for quick navigation through large documents.

#### Markdown

Markdown files render as formatted HTML with:

- Heading-based section rail for quick navigation
- Section highlighting tracks scroll position
- Full CommonMark support

For editable text files (`.md`, `.json`, `.js`, `.py`, `.txt`), an **Edit** button opens a source editor alongside the preview. Changes auto-save after editing.

#### DXF

DXF architectural drawings render as SVG with layer support.

#### Images

Image files render inline at the current zoom level. All common raster and vector formats are supported.

---

### Page Rail

Paged previews show a page rail next to the preview:

| File Type | Rail Style |
|---|---|
| PDF | Thumbnail images per page |
| DOCX | Text-based page cards |
| PPTX | Slide thumbnails |
| Markdown | Section headings |

- Click a thumbnail or section to jump to that page/heading
- The selected item follows the main preview as you scroll
- The rail can be collapsed for more preview space

---

### Inline Text Editor

For editable text files (Markdown, JSON, JavaScript, Python, plain text):

1. Click the **Edit** button in the preview toolbar.
2. A source editor opens alongside the rendered preview.
3. Edit the source text directly.
4. Changes auto-save with a brief debounce delay.
5. The preview updates live as you edit.
6. Click **Close** to dismiss the editor.

The editor shows a language label (e.g., "Markdown source", "JSON source") and a save status indicator.

![File Viewer split view showing source editing alongside the rendered preview](/help-assets/screenshots/fileviewer-editor.png)

---

### Template Variables

Text content in File Viewer supports template variables using the syntax `{{SheetName!CellRef}}`. Variables resolve to the current cell value at render time.

---

### Zoom

Use the zoom controls in the toolbar to adjust the preview size:

- Zoom in and out with buttons or keyboard
- Current zoom percentage is displayed and editable
- Zoom state persists per viewer session

---

### CLI Commands

```bash
export XAPPS_API_BASE_URL="https://your-xapps-host"
```

#### viewer-files -- List all files in a viewer sheet

```bash
xapps viewer-files "Docs"
#   fv-abc report.xlsx (xlsx, 245760 bytes) [A1:E1] source=D1
#   fv-def readme.md (md, 4096 bytes) [A2:E2] source=D2
```

#### add-viewer-file -- Add a file by URL

```bash
xapps add-viewer-file "Docs" "/uploads/report-2024.xlsx" "Q4 Report"
# File added (id=fv-ghi789): Q4 Report

xapps add-viewer-file "Docs" "https://example.com/spec.pdf" "API Spec"
# File added (id=fv-jkl012): API Spec
```

#### remove-viewer-file -- Remove a file

```bash
xapps remove-viewer-file "Docs" fv-abc
# File fv-abc removed
```

#### active-viewer-file -- Show the active file

```bash
xapps active-viewer-file "Docs"
# Active: fv-def readme.md (md) [A2:E2] source=D2
```

#### set-active-viewer-file -- Set the active file

```bash
xapps set-active-viewer-file "Docs" fv-def
# Active file set to: fv-def readme.md
```

#### viewer-meta -- Show viewer metadata

```bash
xapps viewer-meta "Docs"
# Files: 2
# Active: fv-def readme.md
# Ref: A2:E2
# Source: D2
# Zoom: 100%
```

---

### API Endpoints

#### List files

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Docs/files
# [{"id":"fv-abc","name":"report.xlsx","ext":"xlsx","size":245760,"src":"/uploads/report-abc.xlsx","cellRange":"A1:E1","sourceCellRef":"D1"}, ...]
```

#### Add a file

```bash
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Docs/files \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"name":"spec.pdf","src":"https://example.com/spec.pdf","ext":"pdf","size":0}'
# {"file":{"id":"fv-xyz","name":"spec.pdf",...}}
```

#### Remove a file

```bash
curl -X DELETE -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Docs/files/fv-abc
# {"id":"fv-abc"}
```

#### Get the active file

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Docs/active
# {"activeFile":{"id":"fv-def","name":"readme.md","ext":"md",...}}
```

#### Set the active file

```bash
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Docs/active \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"id":"fv-def"}'
# {"activeFile":{"id":"fv-def","name":"readme.md"}}
```

#### Get viewer metadata

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Docs/meta
# {"fileCount":2,"activeFile":{"id":"fv-def","name":"readme.md"},"activeRef":{"cellRange":"A2:E2","sourceCellRef":"D2"},"zoom":100}
```

#### Get a single file

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Docs/files/fv-abc
# {"id":"fv-abc","name":"report.xlsx","ext":"xlsx","size":245760,"src":"/uploads/report-abc.xlsx","cellRange":"A1:E1","sourceCellRef":"D1"}
```

#### Read text content of a file

Reads the raw text of an uploaded editable text file (`.md`, `.json`, `.js`, `.py`, `.txt`, etc.):

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Docs/files/fv-def/content
# {"ok":true,"id":"fv-def","ext":"md","editable":true,"text":"# Hello World\n...","contentLength":1024}
```

Returns `415 Unsupported Media Type` for binary formats (XLSX, DOCX, PDF, images).

#### Write text content of a file

Saves new text content for an uploaded editable text file. Auto-updates the file size in the spreadsheet mirror:

```bash
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Docs/files/fv-def/content \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"text":"# Updated Heading\n\nNew content here."}'
# {"ok":true,"id":"fv-def","editable":true,"size":38}
```

#### Read a spreadsheet mirror cell

Returns the value mirrored into a cell of the sheet grid:

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Docs/cells/A1
# {"ref":"A1","value":"report.xlsx"}

curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Docs/cells/C2
# {"ref":"C2","value":4096}
```

#### Upload a file asset

Upload raw file bytes. The server writes the file and returns its workbook-relative URL, which you then pass to `add-viewer-file` or the POST `/api/sheets/.../files` endpoint:

```bash
curl -X POST $XAPPS_API_BASE_URL/api/uploads \
  -H "X-XApps-Upload-Name: readme.md" \
  -H "Content-Type: text/plain; charset=utf-8" \
  --data-binary @readme.md
# {"ok":true,"name":"readme.md","url":"/uploads/readme.md"}

# Then register it with the sheet:
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Docs/files \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"name":"readme.md","src":"/uploads/readme.md","ext":"md","size":0}'
```

---

### Cloud File Pointers

File Viewer supports cloud-backed file references in addition to uploaded local files. A cloud file pointer stores a reference to a file on a connected provider (e.g. Google Drive, OneDrive) without copying the bytes into the workbook.

Cloud pointers have a `cloudPointer` object in the file record with:

| Field | Description |
|---|---|
| `visibility` | `"private-reference"`, `"provider-shared"`, `"workbook-copy"`, or `"opaque-reference"` |
| `ref.provider` | Cloud provider identifier |
| `ref.mountId` | Mount/drive identifier |
| `ref.itemId` | File item identifier on the provider |
| `ref.pathHint` | Human-readable path hint |
| `capabilities` | Array of strings (e.g. `["write"]`) |

An **opaque reference** (`visibility: "opaque-reference"`) stores only a `pointerId` without provider credentials — useful for workbooks shared across users with different provider access. The viewer shows a prompt to connect the provider when attempting to preview.

When a cloud pointer has `write` capability and a valid parent item ID, the inline editor's **Save** action writes back to the cloud provider, not just the local upload directory.

---

### Agent / AI Workflow Recipes

#### Recipe 1: Document inventory and analysis

An agent uploads multiple files, then reads their metadata for analysis:

```bash
# Add files
xapps add-viewer-file "Library" "/uploads/contract-v1.pdf" "Contract v1"
xapps add-viewer-file "Library" "/uploads/contract-v2.pdf" "Contract v2"
xapps add-viewer-file "Library" "/uploads/requirements.docx" "Requirements"

# List and inspect
xapps viewer-files "Library"
xapps viewer-meta "Library"

# Reference from a spreadsheet formula:
# ='Library'!A1  -> "Contract v1"
# ='Library'!C1  -> file size for comparison
```

#### Recipe 2: Visual regression testing pipeline

File Viewer serves as ground truth for import fidelity testing:

```bash
# Add the original file
xapps add-viewer-file "Regression" "/uploads/report.xlsx" "Original XLSX"

# Set it as active for screenshot comparison
xapps set-active-viewer-file "Regression" fv-abc

# Use Playwright to screenshot the rendered preview
# Compare against native import rendering
# See tests/e2e/visual-compare.spec.js for the full framework
```

#### Recipe 3: Markdown documentation hub

```bash
# Add documentation files
xapps add-viewer-file "Docs" "/uploads/api-guide.md" "API Guide"
xapps add-viewer-file "Docs" "/uploads/changelog.md" "Changelog"
xapps add-viewer-file "Docs" "/uploads/architecture.md" "Architecture"

# Set active for inline editing
xapps set-active-viewer-file "Docs" fv-api-guide

# The Markdown section rail lets readers jump between headings
# The inline editor allows direct edits that auto-save
```

---

### Troubleshooting

**File preview is blank or shows a loading spinner that never resolves.**
Check that the file source URL is valid and accessible. For uploaded files, verify the upload exists in the `/uploads/` directory. Try removing and re-adding the file.

**XLSX file shows unstyled cells or missing formatting.**
Complex Excel styles (conditional formatting, custom themes, merged ranges spanning many cells) may not render fully. The renderer handles standard fonts, colors, borders, and number formats. Very large workbooks may render slowly.

**DOCX bullets or paragraphs render incorrectly.**
The DOCX renderer requires JSZip to load before docx-preview. If bullet rendering fails, try refreshing the page. Some advanced Word features (tracked changes, SmartArt, embedded OLE objects) are not fully supported.

**PDF page rail thumbnails are not showing.**
PDF rendering relies on the browser's native embed capability. Some browsers or configurations may not support thumbnail generation. The main PDF content should still render correctly.

**Markdown section rail does not appear.**
The section rail requires the Markdown file to contain headings (`#`, `##`, etc.). Plain text files without headings will not show a section rail.

**Cannot edit a file in the inline editor.**
Only files with editable text extensions are supported: `.md`, `.markdown`, `.txt`, `.text`, `.json`, `.js`, `.mjs`, `.cjs`, `.py`. Binary formats (XLSX, DOCX, PDF, images) cannot be edited inline.

**File metadata not accessible from formulas.**
Verify the sheet name in your formula matches exactly (case-sensitive). The mirror ref is `='SheetName'!A1` for the first file's name, `='SheetName'!D1` for its source URL, etc. Column mapping: A=name, B=type, C=size, D=source, E=id.

**Upload API returns 400 "Upload JSON body must include a non-empty `url` field."**
This happens when the `Content-Type` header is `application/json`. The `/api/uploads` endpoint treats `application/json` as a remote-URL proxy request. Use `text/plain`, `text/markdown`, `text/csv`, `application/octet-stream`, or another non-JSON content type when uploading file bytes directly.

**Content API returns 409 "Only uploaded local files can be opened as text through the workbook API."**
The `/content` endpoint only reads files from the local `/uploads/` directory. Cloud file pointers must be fetched through the cloud provider API (`/api/cloud/...`), not the content endpoint.

---

### Tips & Tricks

- Use File Viewer as a document hub within a workbook, keeping specs, contracts, and reference materials alongside your data sheets.
- Reference file metadata in spreadsheet formulas to build automated document tracking dashboards.
- The inline text editor makes File Viewer a lightweight code/documentation editor for Markdown, JSON, and script files.
- For large PDFs, use the page rail thumbnails to navigate quickly instead of scrolling through all pages.
- The visual regression testing framework (`tests/e2e/visual-compare.spec.js`) uses File Viewer as ground truth when comparing native import rendering against expected output.
- Zoom in on complex spreadsheet files to read small text or verify cell formatting details.
- Use the CLI to batch-add files programmatically when setting up a document library for a team workbook.
