## Gallery

### Overview

Gallery sheets are image-first visual collections for inspiration boards, product catalogs, team directories, moodboards, and clipped research. Items are displayed as cards in a responsive masonry grid or as rows in a list table, with support for metadata (title, description, tags), image references, filtering, sorting, grouping, bulk operations, slideshow, drag-drop import, clipboard paste, web clipping, and PDF/CSV export.

> 🤖 Agent example: an agent can assemble a moodboard, tag assets by theme, add supporting links, and prepare a curated review gallery for a human to approve.

![Gallery sheet showing visual reference cards with titles, tags, and image-first browsing](/help-assets/screenshots/gallery-sheet.png)

### Features

- Masonry grid layout with responsive column count
- List/table view with configurable visible fields
- Image items with title, description, tags, image URL, info link, image link
- Live image references from other visual sheets (Gallery, Canvas, Whiteboard, Presentation)
- Tag-based filtering (click a tag to filter)
- Free-text search across title, description, and tags
- Sorting by title (A-Z, Z-A) or tags
- Grouping by tag with labeled sections
- Checkbox-based multi-select with bulk actions (tag, delete, export CSV)
- Cut, copy, paste of selected items
- Detail panel with prev/next navigation and arrow key support
- Detail-panel comments for human feedback on visual evidence
- Fullscreen slideshow with auto-play
- Drag-and-drop reordering of cards
- Drag-and-drop file import from desktop
- Clipboard paste to add images (Ctrl/Cmd+V)
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

### Adding Images

There are several ways to add images to a gallery:

**Upload via editor:** Click + Add, then click or drag an image file onto the drop zone in the editor dialog.

**Drag-drop import from desktop:** Drag one or more image files directly onto the gallery grid. Each file creates a new item with the filename as the title.

**Clipboard paste:** Press `Ctrl/Cmd + V` anywhere in the gallery (when no input is focused) to paste an image from the clipboard. Creates a new item titled "Pasted Image".

**Image URL:** In the editor, paste an image URL (http/https or data: URI) into the Image Source field and press Enter or blur the field to preview.

**Reference existing image:** In the editor, click "Reference existing" to pick a source image from another Gallery, Canvas, Whiteboard, or Presentation sheet. The gallery card shows the source image live -- if the source changes, the card updates too.

**Web Clipper:** Click the Clipper button in the toolbar to set up the bookmarklet. Drag it to your bookmarks bar, then visit any website and click it to clip images into your gallery.

### Views

**Grid view** (default) -- Responsive masonry layout that adjusts column count based on available width. Cards show the image, title, description, and tags based on visible field settings. Cards have checkboxes for multi-select.

**List view** -- Table layout with columns for title, image thumbnail, description, tags, and info link. Rows have checkboxes for multi-select. Columns respect the visible fields configuration.

Toggle between views using the grid/list buttons in the toolbar.

### Visible Fields Configuration

Click the gear icon in the toolbar to choose which fields appear on cards and in the list view:

- Image (default: on)
- Description (default: on)
- Tags (default: on)
- Info Link (default: off)

### Tag Filtering

Click any tag on a card or in the detail panel to filter the gallery to items with that tag. A filter badge appears in the toolbar showing the active tag. Click the X on the badge to clear the filter.

### Search

Type in the search box to filter items by title, description, or tags. Search is debounced (250ms) and preserves cursor position.

### Sorting and Grouping

**Sort options** (via dropdown):

- No sort (default order)
- Title A to Z
- Title Z to A
- Tags (alphabetical)

**Group by tag** (via dropdown): Select a tag to create two sections -- items with that tag and "Other" items.

Note: Drag reordering clears any active sort, since manual order takes priority.

### Detail Panel

Click a card or list row to open a lightbox-style detail panel showing:

- Full-size image
- Title, description, tags
- Info link and image source link
- Clip metadata (brand, price, site name) if available
- Selection text from web clipper if available
- Comments thread and comment composer
- Download, Edit, and Close buttons
- Previous/Next navigation arrows

When an item has an image, the image stays pinned at the top of the detail panel while the title, metadata, and comments scroll beneath it.

### Slideshow

Click the **Slideshow** button in the toolbar to launch a fullscreen carousel of gallery items. Controls:

| Control | Action |
|---|---|
| Left arrow key | Previous item |
| Right arrow key | Next item |
| Space bar | Toggle auto-play (advances every 3 seconds) |
| Escape | Exit slideshow |
| Click outside | Exit slideshow |

The slideshow counter shows the current position (e.g., "3 / 12").

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

### Drag-to-Reorder

In grid view, drag a card and drop it on another card to swap their positions. The drop target shows a visual indicator (top or bottom highlight). Reordering clears any active sort setting.

### Export

**CSV export:** Use `File > Export as CSV` or the bulk action bar's Export CSV button. The export is performed server-side and downloads a CSV file with all item fields.

**PDF export:** Use `File > Export as PDF (Print)` to generate a print-ready HTML page with gallery cards that opens the browser print dialog.

### Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Escape` | Clear selection (if items selected) or clear filters |
| `Delete` / `Backspace` | Delete selected items (with confirmation) |
| `Ctrl/Cmd + V` | Paste image from clipboard as new item |
| Left Arrow (in detail) | Previous item |
| Right Arrow (in detail) | Next item |
| Escape (in detail) | Close detail panel |
| Left/Right Arrow (in slideshow) | Navigate slides |
| Space (in slideshow) | Toggle auto-play |
| Escape (in slideshow) | Exit slideshow |

### CLI Commands

All CLI commands require `--file <WorkbookName>` and the gallery sheet name.

Pass `--json` for agent-friendly success output. Gallery CLI validation rejects malformed row lists, ids, ratings, JSON payloads, unsafe media/link URLs, missing flag values, duplicate rows, and invalid tag/comment payloads before sending a request.

**List items:**

```
xapps items MyGallery --file MyWorkbook.json
```

Expected output:

```
  #0 gal-abc123 Product Shot A [design, hero]
  #1 gal-def456 Team Photo [people, office]
  #2 gal-ghi789 Logo Concept [branding]
```

**Read one item:**

```
xapps item MyGallery gal-abc123 --file MyWorkbook.json
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

**Add an item:**

```
xapps add-item MyGallery "New Logo" \
  --image "https://cdn.example.com/logo.png" \
  --desc "Final approved logo" \
  --tags "branding,final" \
  --info-link "https://brand.example.com" \
  --image-link "https://cdn.example.com/logo.png" \
  --rating 5 \
  --file MyWorkbook.json
```

Expected output:

```
Item created (row 3, id=gal-xyz789)
```

**Update an item:**

```
xapps update-item MyGallery gal-abc123 \
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
xapps delete-item MyGallery gal-abc123 --file MyWorkbook.json
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

Expected output (CSV text):

```
title,image,description,tags,infoLink,imageLink
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

**List all items:**

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/MyGallery/items
```

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

**Export CSV:**

```bash
# All items
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/MyGallery/csv

# Specific rows
curl -H 'X-XApps-File: MyWorkbook.json' "$XAPPS_API_BASE_URL/api/sheets/MyGallery/csv?rows=0,1,2"
```

### Agent / AI Workflow Recipes

**Recipe 1: Auto-categorize gallery items with AI**

An agent reads all gallery items, analyzes their titles and descriptions, and adds appropriate tags:

```bash
# 1. Fetch all items
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Assets/items

# 2. For each item, analyze content and add tags
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Assets/items/gal-abc123 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"tags":"ui, mobile, dark-mode, hero"}'

# 3. Repeat for all items that need categorization
```

**Recipe 2: Build a product catalog from a spreadsheet**

Given a spreadsheet with product names, image URLs, and prices, populate a gallery:

```bash
# 1. Read product data from spreadsheet
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Products/cells

# 2. Create gallery items for each product
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Catalog/items \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"title":"Widget Pro","image":"https://cdn.store.com/widget-pro.jpg","description":"Our flagship widget - $49.99","tags":"widgets,flagship","infoLink":"https://store.com/widget-pro"}'

# 3. Bulk tag items by category
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Catalog/items/batch \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"action":"tag","rows":[0,1,2,3],"tag":"in-stock"}'
```

**Recipe 3: Export gallery data for external reporting**

Extract gallery items as CSV for use in external tools:

```bash
# Export all items as CSV
curl -o gallery-export.csv \
  "$XAPPS_API_BASE_URL/api/sheets/Assets/csv"

# Export only items tagged "approved" (filter by rows first)
# 1. Get items and filter client-side
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Assets/items
# 2. Export specific rows
curl -o approved.csv \
  "$XAPPS_API_BASE_URL/api/sheets/Assets/csv?rows=0,2,5"
```

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
