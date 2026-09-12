## Gallery

### Overview

Use **Gallery** to collect and review images with titles, tags, links, ratings
and feedback. Use **Repository** for a broader file collection and **Design
Canvas** to compose images into a finished graphic.

### Create a collection that stays useful

1. Name the Gallery for its collection, such as **Launch assets**.
2. Click **+ Add**, upload an image and give it a descriptive title. Add a
   source or product page in Info Link when reviewers need context.
3. Use a small shared set of tags, such as `approved`, `concept` or `product`.
   Put the main category first if you plan to group by primary tag.
4. Open **View** for Grid, Masonry or List, plus density, sorting, grouping and
   **Configure fields…**.
5. Open an item to inspect its image and metadata. Rate it or leave feedback
   so other reviewers can understand the decision.
6. Search and filter to find the final selection. Export metadata as CSV or
   use the visual export for a review handout.

### Choose a view for the task

| Task | View or control | Why it helps |
|---|---|---|
| Compare choices | Grid | Uniform cards make a shortlist easy to scan |
| Review mixed proportions | Masonry | Images keep their natural proportions |
| Clean up metadata | List | Fields line up for comparison |
| Browse by theme | View → Group by → Primary tag | Each item appears under its first tag |
| Find a known item | Search | Matches title, description and tags |
| Review closely | Open the detail panel | Image, links, timestamps and feedback together |

![Gallery search showing Mountain Vista and a filtered result count](/help-assets/screenshots/gallery-search.png)

### Review and reuse an approved asset

Open the item, check its full image and source, add feedback, then set its rating
or tags. In another visual sheet, choose **Reference existing** to reuse it as
a live reference. Upload a separate copy for an independent asset. Removing the
original breaks a live reference until you relink or replace it.

### Understand a missing item

Clear Search, active tags and the minimum rating filter. Sorting changes order;
filtering changes which items are visible. The result count shows when you are
looking at only part of the collection. Confirm the workbook and Gallery sheet
before adding an apparent duplicate.

### Feature reference

### Compare two images

Select exactly two item checkboxes, then choose **Compare** in the selection
bar. **Side by side** helps compare alternatives; **Slider** reveals one image
over the other for before/after review. Close Compare to return to the collection.
The Compare action appears only for a pair of selected items.

![Gallery Compare showing two selected illustrations side by side](/help-assets/screenshots/gallery-compare.png)

### Collections and library maintenance

Use **Collection…** in the selection bar to organize selected items into a named
collection. The left **Collections** rail switches between them; **+ New** makes
a collection and its **⋯** menu renames or deletes it. Removing a collection
does not delete its images. Smart collections can use saved text, tag and
minimum-rating conditions through the automation commands below.

Open **More → Health** to check broken or missing images. Its report offers
**Repair…** or **Add image…** for affected items. Check the item and source before
replacing it. **More** also contains **Slideshow**, **Lightbox** and **Web Clipper**.

**More → Analyze library** requests captions, descriptions and suggested tags
for items without analysis. It depends on configured AI services. Read the
reported status and review generated descriptions and tags before relying on
them. It is separate from the image-health check.

Gallery sheets are image-first visual collections for inspiration boards, product catalogs, team directories, moodboards, and clipped research. Items are displayed as cards in a responsive masonry grid or as rows in a list table, with support for metadata (title, description, tags), image references, filtering, sorting, grouping, bulk operations, slideshow, drag-drop import, clipboard paste, web clipping, and PDF/CSV export.

> 🤖 Agent example: an agent can assemble a moodboard, tag assets by theme, add supporting links, and prepare a curated review gallery for a human to approve.

![Gallery sheet showing 8 image cards with titles, tags, and toolbar controls](/help-assets/screenshots/gallery-sheet.png)

### Features

- Grid and Masonry card layouts with one to eight columns, or automatic density
- List/table view with configurable visible fields
- Image items with title, description, tags, image URL, info link, image link, and 1-5 star rating
- Live image references from other visual sheets (Gallery, Canvas, Whiteboard, Presentation)
- Tag-based filtering (click a tag to filter)
- Star rating filter (show all, or 1★ through 5★ minimum)
- Free-text search across title, description, and tags
- Sorting by title (A-Z or Z-A), date added (newest or oldest), tags, or tag count
- Grouping by primary tag or by star rating
- Checkbox-based multi-select with bulk actions (tag, delete, export CSV)
- Cut, copy, paste of selected items
- Detail panel (lightbox) with prev/next navigation and arrow key support
- Detail-panel comments for human feedback on visual evidence
- Fullscreen lightbox (image-only) and fullscreen slideshow with auto-play
- Drag-and-drop reordering of cards, including across group sections
- Drag-and-drop file import from desktop
- Clipboard paste to add images (Ctrl/Cmd+V)
- Right-click context menu (Add item, Edit item, Delete item)
- Web Clipper bookmarklet for clipping from any website
- Configurable visible fields (image, description, tags, link)
- Export as CSV (via server API) or PDF (print-ready HTML)
- Stable item IDs for API and CLI workflows
- Clip metadata (brand, price, site name, selection text)

### Getting Started

1. Create a new gallery sheet from the **+ Add Sheet** menu.
2. Click **+ Add** or the **+ Add item** card to create your first item.
3. Fill in the title, drop or upload an image, add a description and tags.
4. Click **Add Item** to save. The card appears in the masonry grid.
5. Click any card to open the detail panel with full-size image and metadata.
6. Use the toolbar to search, sort, group, switch views, or start a slideshow.

### Item Fields

Each gallery item stores these fields:

| Field | Column | Description |
|---|---|---|
| Title | A (col 0) | Display name shown on the card |
| Image | B (col 1) | Direct image URL or uploaded file path |
| Description | C (col 2) | Text description or notes |
| Tags | D (col 3) | Comma-separated tag list |
| Info Link | E (col 4) | External URL (e.g., product page) |
| Item ID | F (col 5) | Auto-generated stable identifier |
| Source Ref | G (col 6) | JSON reference to an image in another sheet |
| Image Link | H (col 7) | Direct link to the image source |
| Clip Meta | I (col 8) | JSON metadata from web clipper |
| Rating | J (col 9) | 1-5 star rating |
| Comments | K (col 10) | JSON comment thread |
| Updated At | L (col 11) | Server/browser-managed ISO-8601 time of the latest item content change |

### Adding Images

There are several ways to add images to a gallery:

**Upload via editor:** Click + Add, then click or drag an image file onto the drop zone in the editor dialog.

**Drag-drop import from desktop:** Drag one or more image files directly onto the gallery grid. Each file creates a new item with the filename as the title.

**Clipboard paste:** Press `Ctrl/Cmd + V` anywhere in the gallery (when no input is focused) to paste an image from the clipboard. Creates a new item titled "Pasted Image".

**Image URL:** In the editor, paste an image URL (http/https or data: URI) into the Image Source field and press Enter or blur the field to preview.

**Reference existing image:** In the editor, click "Reference existing" to pick a source image from another Gallery, Canvas, Whiteboard, or Presentation sheet. The gallery card shows the source image live -- if the source changes, the card updates too.

**Web Clipper:** Open **More → Web Clipper** to set up the bookmarklet. Drag it to your bookmarks bar, then visit a website and use it to clip images into the gallery.

### Views

**Grid view** (default) -- Cards with images, titles, descriptions and tags. Open **View** to choose **Grid**, **Masonry** or **List**:

- **Grid layout** -- Fixed-height cards arranged in a uniform grid. All cards have equal height; images are cropped to fill.
- **Masonry layout** -- Cards flow in columns at their natural image height, producing a staggered arrangement. Open **View** and choose **Masonry**.

![Gallery list view showing all items as table rows with thumbnails, descriptions, tags, and links](/help-assets/screenshots/gallery-list-view.png)

**List view** -- Table layout with columns for title, image thumbnail, description, tags, and info link. Rows have checkboxes for multi-select. Columns respect the visible fields configuration.

Choose the layout from **View** in the toolbar.

Open an item's **details** panel to see its latest update date and time. Older items that predate timestamp tracking show **Updated time unavailable** until their content is changed.

![Gallery masonry layout showing staggered image cards at natural heights](/help-assets/screenshots/gallery-masonry.png)

### Grid Column Count

Open **View** in the Gallery toolbar and adjust **Density**. Zero means Auto;
the control supports one through eight columns. Auto adapts to available width.

### Visible Fields Configuration

Open **View → Configure fields…** to choose which fields appear on cards and in the list view:

- Image (default: on)
- Description (default: on)
- Tags (default: on)
- Info Link (default: off)

### Tag Filtering

Click any tag on a card or in the detail panel to filter the gallery to items with that tag. A filter badge appears in the toolbar showing the active tag. Click the X on the badge to clear the filter.

### Search

Type in the search box to filter items by title, description, or tags. Search is debounced (250ms) and preserves cursor position.

### Rating Filter

Open **Filter → Minimum rating** to limit the visible set to a minimum rating:

| Option | Shows |
|---|---|
| All ★ | All items regardless of rating |
| 5★ | Only 5-star items |
| 4★+ | Items rated 4 or 5 stars |
| 3★+ | Items rated 3, 4, or 5 stars |
| 2★+ | Items rated 2 stars or higher |
| 1★+ | Items with a rating of at least one star |

Click the stars directly on a card to set or change an item's rating. Ratings persist immediately.


### Sorting and Grouping

**Sort options** (under **View → Sort by**):

- No sort (default order)
- Name (A → Z)
- Name (Z → A)
- Date Added (newest first)
- Date Added (oldest first)
- Tags (alphabetical by first tag)
- Tag Count (items with the most tags first)

**Group by** (under **View → Group by**):

- **Primary tag (first tag)** -- Groups items into labeled sections by primary tag. The first tag in an item's tag list is its primary tag; later tags remain available for filtering but do not create additional copies of the item in other sections. Items with no tag appear under "Other". A **+ Add** button in each group header creates a new item pre-assigned to that tag.
- **Rating** -- Groups items into five sections (5 Stars through 1 Star).

Drag items between group sections to reassign their primary tag (or rating) without opening the editor.

![Gallery items grouped by primary tag with labeled section headers and item counts](/help-assets/screenshots/gallery-grouping.png)

Note: Drag reordering clears any active sort, since manual order takes priority.

### Detail Panel

Click a card body (or list row), or click the **⋯** info button on a card, to open the detail panel showing:

- Full-size image pinned at the top (scrolls independently from metadata)
- Title, description, and tags with an adjacent **Edit tags** / **+ Add tag** action
- Info link and image source link
- Clip metadata (brand, price, site name) if available
- Selection text from web clipper if available
- Latest update date and time
- Comments thread and comment composer
- Download, Edit, and Close buttons
- Previous/Next navigation arrows
- Max Size control on the image for near-full-viewport review

![Gallery detail panel showing Mountain Vista image and item metadata](/help-assets/screenshots/gallery-detail.png)

![Gallery comments showing review feedback and the comment composer](/help-assets/screenshots/gallery-comments.png)

When an item has an image, the image stays pinned at the top of the detail panel while the title, metadata, and comments scroll beneath it.

### Lightbox

Click the image thumbnail on any card (or the **Lightbox** button in the toolbar) to open a fullscreen image-only lightbox view. The lightbox shows the full-resolution image and supports:

- Left/Right arrow keys to navigate between items
- Max Size / Fit View toggle to hide metadata chrome and use the available viewport
- M key to toggle Max Size
- Escape or click outside to close

The Lightbox differs from the Detail Panel: it shows only the image with no metadata or comments, optimized for visual review.

### Slideshow

Click the **Slideshow** button in the toolbar to launch a fullscreen carousel of gallery items. Controls:

| Control | Action |
|---|---|
| Left arrow key | Previous item |
| Right arrow key | Next item |
| Space bar | Toggle auto-play using the persisted slideshow interval |
| Escape | Exit slideshow |
| Click outside | Exit slideshow |

The slideshow counter shows the current position (e.g., "3 / 12"). The persisted `slideshow` settings control `autoplay`, `loop`, and `intervalMs` (500-60,000 ms; playback clamps intervals below one second to one second). Reduced-motion mode disables autoplay and announces that state in the dialog.

### Selection and Bulk Actions

Gallery supports checkbox-based multi-select. When 2 or more items are selected, a bulk action bar appears with:

- **Tag...** -- Prompts for a tag name and adds it to all selected items
- **Delete** -- Deletes all selected items (with confirmation dialog)
- **Export CSV** -- Exports selected items as CSV through the server API
- **Clear** -- Deselects all items

### Cut, Copy, Paste

Available via the **Edit** menu:

- **Select All** -- Selects all items matching current filters
- **Deselect All** -- Clears selection
- **Cut** -- Copies selected items to the internal clipboard and marks them for removal on paste
- **Copy** -- Copies selected items to the internal clipboard
- **Paste** -- Inserts clipboard items as new gallery entries
- **Delete Selected** -- Deletes selected items

### Context Menu

Right-click any card to open a context menu with:

- **Add item** -- Opens the item editor to create a new item
- **Edit item** -- Opens the editor for the card you right-clicked
- **Delete item** -- Deletes the card immediately (with undo support)

Right-clicking empty space (outside any card) shows only "Add item".

### Drag-to-Reorder

In grid or list view, drag a card and drop it before or after another card to reorder. The drop target shows a visual indicator (top or bottom highlight). Reordering clears any active sort setting.

When grouping is active, drag a card and drop it into a different group section to reassign it to that tag or rating without opening the editor.

### Export

**CSV export:** Use `File > Export as CSV` or the bulk action bar's Export CSV button. The export is performed server-side and downloads a CSV file with all item fields.

**PDF export:** Use `File > Export as PDF (Print)` to generate a print-ready HTML page with gallery cards that opens the browser print dialog.

### Keyboard Shortcuts

| Shortcut | Context | Action |
|---|---|---|
| `Escape` | Grid/list | Clear multi-selection (if selected) or clear active filters |
| `Delete` / `Backspace` | Grid/list | Delete selected items (confirmation dialog) |
| `Ctrl/Cmd + V` | Grid/list | Paste image from clipboard as new item |
| `Left Arrow` | Detail panel | Previous item |
| `Right Arrow` | Detail panel | Next item |
| `Escape` | Detail panel | Close detail panel |
| `Left Arrow` | Lightbox / Slideshow | Previous item |
| `Right Arrow` | Lightbox / Slideshow | Next item |
| `Space` | Slideshow | Toggle auto-play (3-second interval) |
| `Escape` | Lightbox / Slideshow | Exit |

### CLI Commands

All gallery item commands require the gallery sheet name. Use `--file <WorkbookName>` when the command should target a saved workbook instead of the currently loaded workbook.

Pass `--json` for agent-friendly success output. Gallery CLI validation rejects malformed row lists, ids, ratings, JSON payloads, unsafe media/link URLs, missing flag values, duplicate rows, and invalid tag/comment payloads before sending a request.

For discovery, run `xapps search --json gallery <intent> --limit 3` or `xapps help gallery <command>`. Use the exact invocation from help/search. Do not synthesize hyphenated names such as `gallery-items` or `gallery-add-item`; group scope is a separate token, for example `xapps gallery items`.

Recommended agent forms:

```bash
xapps gallery items <sheet> --json
xapps gallery-query-items <sheet> [--q <text>] [--tag <tag>] [--min-rating <0-5>] [--group <tag|rating>] [--sort <field>] [--order <asc|desc>] --json
xapps gallery-settings <sheet> --json
xapps set-gallery-settings <sheet> '<json>' --request-id <id> --expected-revision <n> --json
xapps gallery-batch <sheet> '<json>' --request-id <id> --expected-revision <n> --json
xapps gallery-ingest <sheet> <title> --source-type <data-url|remote-url|upload-ref> --source <value> --request-id <id> --expected-revision <n> --json
xapps gallery-create-export <sheet> <csv|print-html> [--ids <id-csv>] [--file-name <name>] --request-id <id> --expected-revision <n> --json
xapps gallery item <sheet> <row-or-id> --json
xapps gallery add-item <sheet> <title> --image <url-or-path> [--upload] --verify --json
xapps gallery update-item <sheet> <row-or-id> '<json>' --verify --json
xapps gallery delete-item <sheet> <row-or-id> --json
xapps gallery-item-comments <sheet> <row-or-id> --json
xapps add-gallery-item-comment <sheet> <row-or-id> "<message>" --author <name> --type <kind> --json
xapps gallery-tag-items <sheet> --rows <row-csv> --tag <text> --json
xapps gallery-delete-items <sheet> --rows <row-csv> --json
xapps gallery-export-items <sheet> [--rows <csv>] [--out <file>] --json
xapps gallery-health <sheet> --json
xapps gallery-collections <sheet> --json
xapps gallery-collection-create <sheet> <title> [--items <id-csv>] [--smart '<json>'] [--id <id>] --json
xapps gallery-collection-update <sheet> <id> '<json>' --json
xapps gallery-collection-delete <sheet> <id> --json
xapps gallery-analyze-item <sheet> <row-or-id> --request-id <id> --expected-revision <n> --json
```

**Library management:** `gallery-health` scans every item's image source —
`/uploads/` files are stat'd, embedded data URLs are validated, remote URLs get
a HEAD probe — and returns `{ checked, healthy, broken, missing, unverified,
duplicates }`; `duplicates` groups items whose image bytes share a sha256.

`gallery-collections` lists collections with a server-computed `count`. A
collection is a stored set (`itemIds`), a smart filter (`smart` with any of
`tags`, `minRating`, `q`), or both — a stored id always matches, and the smart
filter ANDs its conditions across the remaining items. `gallery-collection-update`
takes `itemIds` (replace), `addItemIds`, `removeItemIds`, `title`, `coverItemId`,
and `smart`; `gallery-collection-delete` removes only the collection, never its
items.

`gallery-analyze-item` runs the room vision model over one item's image and
returns `{ ai: { caption, description, tags, ocr } }`. It requires a room
LLM/vision proxy, so it is unavailable on a host with no room session.

**List items:**

```
xapps gallery items MyGallery --file MyWorkbook.json
```

Expected output:

```
  #0 gal-abc123 Product Shot A [design, hero]
  #1 gal-def456 Team Photo [people, office]
  #2 gal-ghi789 Logo Concept [branding]
```

**Read one item:**

```
xapps gallery item MyGallery gal-abc123 --file MyWorkbook.json
```

Expected output (JSON with all fields):

```json
{
  "row": 0,
  "id": "gal-abc123",
  "title": "Product Shot A",
  "image": "/uploads/product-a.png",
  "description": "Main hero image for landing page",
  "tags": "design, hero",
  "infoLink": "https://example.com/product-a",
  "imageLink": "/uploads/product-a.png"
}
```

**Query items and persisted view settings:**

```bash
xapps gallery-query-items MyGallery --q hero --tags design,approved --min-rating 4 --group tag --sort title --order asc --json
xapps gallery-settings MyGallery --json
xapps set-gallery-settings MyGallery '{"layout":"masonry","search":"hero","slideshow":{"autoplay":false,"loop":true,"intervalMs":5000}}' \
  --request-id settings-001 --expected-revision 12 --json
```

**Guarded batch, ingestion, and artifact export:**

```bash
xapps gallery-batch MyGallery '{"action":"reorder","ids":["gal-a","gal-b"]}' \
  --request-id reorder-001 --expected-revision 12 --json
xapps gallery-ingest MyGallery "Remote reference" --source-type remote-url \
  --source https://cdn.example.com/reference.png --request-id ingest-001 --expected-revision 13 --json
xapps gallery-create-export MyGallery csv --ids gal-a,gal-b --file-name approved.csv \
  --request-id export-001 --expected-revision 14 --json
```

**Add an item:**

```
xapps gallery add-item MyGallery "New Logo" \
  --image "https://cdn.example.com/logo.png" \
  --desc "Final approved logo" \
  --tags "branding,final" \
  --info-link "https://brand.example.com" \
  --image-link "https://cdn.example.com/logo.png" \
  --rating 5 \
  --verify \
  --json \
  --file MyWorkbook.json
```

For a local image file, add `--upload`; the CLI uploads it through `/api/uploads` first and stores the returned workbook-relative URL:

```bash
xapps gallery add-item MyGallery "Local Screenshot" \
  --image "/tmp/screenshot.png" \
  --upload \
  --desc "Rendered state after the fix" \
  --tags "after,verified" \
  --verify \
  --json \
  --file MyWorkbook.json
```

With `--verify --json`, output includes the created row/id, uploaded URL when applicable, and the read-back item record:

```json
{
  "ok": true,
  "id": "gal-xyz789",
  "uploadedUrl": "/uploads/screenshot.png",
  "verified": true,
  "item": {
    "id": "gal-xyz789",
    "image": "/uploads/screenshot.png"
  }
}
```

**Update an item:**

```
xapps gallery update-item MyGallery gal-abc123 \
  '{"title":"Product Shot A (Updated)","tags":"design, hero, featured","rating":5}' \
  --file MyWorkbook.json
```

Expected output:

```
Item gal-abc123 updated (id=gal-abc123)
```

**List item comments:**

```
xapps gallery-item-comments MyGallery gal-abc123 --file MyWorkbook.json
```

Expected output:

```
  #0 2026-05-03T00:00:00.000Z Parsa: Looks good from here.
```

**Add an item comment:**

```
xapps add-gallery-item-comment MyGallery gal-abc123 \
  "Looks good from here." --author "Parsa" --type "feedback" \
  --file MyWorkbook.json
```

Expected output:

```
Comment added to gallery item gal-abc123 (1 comment)
```

**Delete an item:**

```
xapps gallery delete-item MyGallery gal-abc123 --file MyWorkbook.json
```

Expected output:

```
Item gal-abc123 deleted (id=gal-abc123)
```

**Bulk tag items:**

```
xapps gallery-tag-items MyGallery \
  --rows 0,1,2 --tag "approved" --file MyWorkbook.json
```

Expected output:

```
Tagged gallery items (approved): 0, 1, 2
```

**Bulk delete items:**

```
xapps gallery-delete-items MyGallery \
  --rows 3,4 --file MyWorkbook.json
```

Expected output:

```
Deleted gallery items: 3, 4
```

**Export items as CSV:**

```
xapps gallery-export-items MyGallery --file MyWorkbook.json
```

Expected legacy `/csv` output (CSV text):

```
Title,Image,Description,Tags,InfoLink,ImageLink
Product Shot A,/uploads/product-a.png,Main hero image,"design, hero",https://example.com/product-a,/uploads/product-a.png
Team Photo,/uploads/team.jpg,Annual team photo,"people, office",,/uploads/team.jpg
```

**Export specific rows to a file:**

```
xapps gallery-export-items MyGallery \
  --rows 0,1 --out ./export.csv --file MyWorkbook.json
```

Expected output:

```
Gallery CSV written to /Users/you/export.csv
```

### API Endpoints

Gallery API validation errors return JSON with `ok:false`, a machine-readable `code`, an `error`/`message` string, and field-level `details`. Mutating endpoints reject invalid payloads before saving.

All mutating routes accept `requestId` and `expectedRevision`. A stale revision returns `409`; retrying the same request id with the identical payload replays the saved receipt, while reusing it for a different payload is rejected.

The browser may additionally send `expectedRowValues` with `expectedRevision` and `expectedWorkbookRevision` when it atomically claims a stable ID for a legacy row. The server applies the claim only when all 12 captured raw row values still match and both the Gallery and workbook revisions are unchanged, preventing any concurrent reorder—including an identical-row replacement—from redirecting the edit to another item. Editor mutations carry stable request IDs so a lost response can be replayed without duplicating a claim, update, or delete.

Item reads include `updatedAt` as a canonical ISO-8601 string. Create, update, comment, and batch-tag operations advance the stored timestamp and return the resulting value (batch tagging returns `updatedAtByRow`). Legacy items return an empty string until their next content change; clients cannot set this server-managed field directly.

**List all items:**

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/MyGallery/items
```

Add `q`/`search`, `tag`/`tags`, `minRating`, `filter`, `group`/`groupBy`, `sort`, `order`/`sortDir`, `limit`, or `offset` for the typed list-query envelope (`{ok,items,totalCount,groups?}`). With no contract query parameters the route preserves the legacy bare-array response.

**Read one item:**

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/MyGallery/items/gal-abc123
```

**Create an item:**

```bash
curl -X POST $XAPPS_API_BASE_URL/api/sheets/MyGallery/items \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"title":"Wireframe","image":"https://cdn.example.com/wire.png","description":"Homepage wireframe v3","tags":"ux,wireframe","imageLink":"https://cdn.example.com/wire.png","infoLink":"https://figma.com/file/abc"}'
```

**Update an item:**

```bash
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/MyGallery/items/gal-abc123 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"tags":"design, hero, approved"}'
```

**Delete an item:**

```bash
curl -X DELETE -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/MyGallery/items/gal-abc123
```

**Comments:**

```bash
# List comments
curl -H 'X-XApps-File: MyWorkbook.json' \
  $XAPPS_API_BASE_URL/api/sheets/MyGallery/items/gal-abc123/comments

# Add a comment
curl -X POST $XAPPS_API_BASE_URL/api/sheets/MyGallery/items/gal-abc123/comments \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"message":"Looks good from here.","author":"Parsa","type":"feedback"}'
```

**Batch operations:**

```bash
# Bulk tag
curl -X POST $XAPPS_API_BASE_URL/api/sheets/MyGallery/items/batch \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"action":"tag","rows":[0,1,2],"tag":"reviewed"}'

# Bulk delete
curl -X POST $XAPPS_API_BASE_URL/api/sheets/MyGallery/items/batch \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"action":"delete","rows":[3,4]}'
```

The typed batch contract also supports stable-id `copy`, `duplicate`, `group`, `reorder`, and `move` mutations through the same `/items/batch` route.

**View settings and ingestion:**

```bash
# Read or atomically patch layout/filter/sort/group/visible-fields/slideshow settings
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/MyGallery/settings
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/MyGallery/settings \
  -H 'X-XApps-File: MyWorkbook.json' -H 'Content-Type: application/json' \
  -d '{"layout":"masonry","slideshow":{"autoplay":false,"loop":true,"intervalMs":5000},"requestId":"settings-001","expectedRevision":12}'

# Materialize a data URL, remote URL, or existing upload reference and create its item
curl -X POST $XAPPS_API_BASE_URL/api/sheets/MyGallery/ingest \
  -H 'X-XApps-File: MyWorkbook.json' -H 'Content-Type: application/json' \
  -d '{"title":"Reference","source":{"type":"remote-url","value":"https://cdn.example.com/reference.png"},"requestId":"ingest-001","expectedRevision":13}'
```

**Export CSV:**

```bash
# All items
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/MyGallery/csv

# Specific rows
curl -H 'X-XApps-File: MyWorkbook.json' "$XAPPS_API_BASE_URL/api/sheets/MyGallery/csv?rows=0,1,2"

# Canonical schema: ID,Title,Image,Description,Tags,InfoLink,ImageLink,Rating,UpdatedAt
curl -H 'X-XApps-File: MyWorkbook.json' "$XAPPS_API_BASE_URL/api/sheets/MyGallery/csv?ids=gal-a,gal-b&schema=canonical"
```

`GET /csv` keeps the six-column legacy schema by default (`Title,Image,Description,Tags,InfoLink,ImageLink`). `schema=canonical` adds stable `ID`, `Rating`, and `UpdatedAt`. Both forms neutralize spreadsheet-formula prefixes.

**Durable export artifact:**

```bash
curl -X POST $XAPPS_API_BASE_URL/api/sheets/MyGallery/exports \
  -H 'X-XApps-File: MyWorkbook.json' -H 'Content-Type: application/json' \
  -d '{"format":"csv","ids":["gal-a","gal-b"],"fileName":"approved.csv","requestId":"export-001","expectedRevision":14}'
```

Artifact export accepts `csv` or `print-html`. CSV uses the canonical nine fields above; `print-html` contains printable cards with image, title, description, and tags. PDF bytes are intentionally not generated server-side: the UI opens the safe print HTML and invokes the browser print flow.

### Automation boundary

The public API, typed `client.gallery.*` SDK, 16 CLI commands, 13 hosted Gallery tools, and MCP adapters cover durable item, comment, query, settings, collection, ingestion, and export operations. Browser gesture state—current focus, local selection/clipboard, drag pointer state, and lightbox/slideshow playback—is intentionally UI-only; the underlying items and persisted view/slideshow settings remain available to automation.

### Agent / AI Workflow Recipes

Choose the authorized saved workbook and its actual storage target before running the examples. Set `XAPPS_API_BASE_URL` to that host. This helper keeps every operation in the same scope (replace the example file and `local` together when needed):

```bash
xapps_scoped() {
  xapps --base-url "${XAPPS_API_BASE_URL:?Set the authorized host URL}" \
    --file 'MyWorkbook.json' --workbook-storage-target local "$@"
}
```

Read the needed page or tag filter, inspect the actual content and retain stable item IDs before classification.

```bash
xapps_scoped gallery-settings Assets --json
# Set GALLERY_REVISION to the returned revision.
xapps_scoped gallery-query-items Assets --limit 50 --offset 0 --json
# Advance offset only while more relevant items remain.
xapps_scoped gallery-batch Assets \
  '{"action":"tag","ids":["gal-abc123","gal-def456"],"tags":["approved"],"mode":"add"}' \
  --expected-revision "$GALLERY_REVISION" --request-id gallery-approved-1 --json
xapps_scoped gallery-query-items Assets --tag approved --limit 50 --offset 0 --json
```

Obtain `GALLERY_REVISION` from the current guarded Gallery state before applying; replace the example IDs with returned stable IDs. Use one supported batch per shared classification, never a per-item loop with a shared stale revision. For new imagery, upload the bytes through the scoped upload path, retain the returned durable URL and original source/capture provenance, then add the item. Local `/tmp` paths and temporary provider links are not durable gallery evidence. Export only the intended bounded selection; browser-only crop/slideshow/navigation controls remain UI actions. Keep the exact payload, expected revision and request ID after uncertain delivery; retry that same intent. On a revision conflict, reread and reconcile before creating a new intent and request ID.

### Troubleshooting

**Images do not appear on cards**
Verify the image URL is accessible. If using a direct URL, ensure it starts with `http://`, `https://`, or `/uploads/`. If using a reference, check that the source image still exists in the referenced sheet.

**Broken source reference badge on a card**
The referenced image object in the source sheet was deleted or moved. Open the item editor and either click "Reference existing" to pick a new source, or click "Use direct image" and paste a URL.

**Drag-and-drop import does nothing**
Only image files are accepted (JPEG, PNG, GIF, WebP, SVG, etc.). Non-image files are silently ignored. Check that the file type is recognized as an image.

**Tag filter shows no items**
Tags are comma-separated and case-sensitive. Ensure the tag you clicked exactly matches what is stored. Click the X on the filter badge to clear and see all items.

**Search does not find an item**
Search matches against title, description, and tags only. It does not search info links or image URLs. The search is case-insensitive.

**Slideshow shows "No items"**
The slideshow uses the current filtered item set. If filters are active and match nothing, there are no items to display. Clear filters first.

**CSV export is empty**
If exporting selected rows, ensure at least one item is selected. If no items exist in the gallery, the CSV will contain only headers.

**Clipboard paste creates an item but with no image**
The paste handler only processes image data from the clipboard, not text URLs. To add an image from a URL, use the editor dialog's Image Source field.

### Tips & Tricks

- Use the Web Clipper to quickly save reference images from any website without downloading them manually.
- Tag items consistently (e.g., "approved", "draft", "v2") to create useful filtered views later.
- Use grouping by tag to visually organize items into labeled sections.
- Drag cards to reorder them manually when you need a specific visual arrangement.
- Switch to list view for a compact overview when working with large collections.
- Use the detail panel's arrow keys to quickly browse through items without closing and reopening.
- Combine Gallery with a Dashboard sheet to show item counts or tag distributions.
- Reference images from a Canvas or Whiteboard sheet to keep the gallery in sync with design work.

### Works Well With

- Canvas for creative production
- Floor Plan for materials and furniture references
- Document for visual briefs and research
- Dashboard for item count and tag distribution widgets
- Spreadsheet for structured metadata and cross-referencing

### Mobile and Touch

On phones, Grid and Masonry use one readable column, while List becomes a
stack of labeled item cards instead of a wide table. Toolbar controls and
primary dialog actions remain touch-sized and within the viewport.

Use the visible Up and Down controls on a card or list item to change its
position without dragging. The new order is saved and remains after reload;
pointer users can continue to drag items on larger screens.

The item editor uses one vertical scroll area on a phone. Its image drop zone
is also a keyboard button: focus it and press Enter or Space to choose an
image. Upload errors appear inside the editor instead of opening a native
browser alert.
