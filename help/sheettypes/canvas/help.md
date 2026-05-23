## Design Canvas

### A fixed artboard for polished design work

Use Design Canvas when you want a bounded page instead of an infinite board. It is ideal for:

- social graphics
- event posters and flyers
- ads and marketing creatives
- simple diagrams and flow charts
- brand boards and moodboards
- mockups and exported assets

> Agent example: an agent can scaffold a launch graphic, drop in workbook values as template variables, categorize clipped images, and hand the composition to a human for final polish.

![Design Canvas artboard showing an event flyer with shapes, text, images, and the objects panel open on the right](/help-assets/screenshots/canvas-sheet.png)

The canvas UI gives you a ruler-edged artboard, a left tool rail, a top toolbar with artboard controls, and a right objects panel that lists every element on the current page.

![Full canvas workspace with toolbar, layer rail, artboard, objects panel, and minimap](/help-assets/screenshots/canvas-poster.png)

---

### Starter templates

Canvas ships a template library for common design jobs. Apply a template from the **Design** menu or the **Templates** button in the page bar.

| Template ID | Title | Size |
|---|---|---|
| `social-quote` | Social Quote | 1080 × 1080 |
| `product-promo` | Product Promo | 1080 × 1080 |
| `story-announcement` | Story Announcement | 1080 × 1920 |
| `event-flyer` | Event Flyer | 1080 × 1350 |
| `brand-board` | Brand Board | 1920 × 1080 |
| `moodboard` | Moodboard | 1920 × 1080 |

When the current page is empty, the template replaces it in place. When the page already has content, xApps inserts the template as a new page so your work stays intact.

---

### Multiple pages and artboards

Each canvas sheet contains multiple pages. Every page has its own size, background color, and object set. Canvas pages are better than separate sheets when all the designs belong to one project.

**Artboard presets** set the page to a standard size instantly:

| Preset | Dimensions |
|---|---|
| `instagram-post` | 1080 × 1080 |
| `instagram-story` | 1080 × 1920 |
| `twitter-header` | 1500 × 500 |
| `presentation-16x9` | 1920 × 1080 |
| `a4-portrait` | 794 × 1123 |
| `a4-landscape` | 1123 × 794 |
| `letter-portrait` | 816 × 1056 |
| `letter-landscape` | 1056 × 816 |
| `custom` | freeform |

**Magic Resize** is the Canva-style multi-format workflow: choose one or more target presets (Instagram Story, Twitter Header, A4, etc.) and Canvas creates resized page copies, scaling all objects to fit each new format. Use **Design > Magic Resize** or the `Resize` button in the page bar. The `replace` mode overwrites the current page with the first selected preset instead of creating a copy.

---

### Objects you can place

- **Text** — free-form text box with full typography controls
- **Shapes** — rect, circle, triangle, star, polygon (hexagon), rounded-rect
- **Lines and arrows** — 9 line-style variants (see below)
- **Images** — by URL, by local file upload (`--upload`), or by live reference to another sheet

Double-click any shape (or select it and press `Enter`) to edit its text label in place.

Right-click any object to see its backing storage row at the bottom of the context menu.

---

### Line styles

Nine line/arrow variants are available for `line`-type objects and shape strokes:

| CLI name | Appearance |
|---|---|
| `line` | solid line |
| `arrow` | solid + arrow end |
| `double-arrow` | solid + both ends |
| `dashed-line` | dashed line |
| `dashed-arrow` | dashed + arrow end |
| `dotted-line` | dotted line |
| `dotted-arrow` | dotted + arrow end |
| `dot-dash-line` | dot-dash line |
| `dot-dash-arrow` | dot-dash + arrow end |

---

### Text features

- Bold, italic, underline, and strikethrough via the floating inline format bar
- Letter spacing, line height, text transform (uppercase / lowercase / capitalize)
- Text shadow (see Drop shadow section)
- Text background color

#### Typography depth

Canvas exposes the full PCMag wishlist on every text object:

| Feature | Values | CSS property |
|---|---|---|
| **Kerning** | `none`, `normal`, `auto` | `font-kerning` |
| **Ligatures** | `none`, `common`, `discretionary`, `all` | `font-feature-settings` |
| **Paragraph spacing** | em value | gap between `\n\n` paragraphs |
| **OpenType features** | raw string e.g. `'ss01' 1, 'tnum' 1` | `font-feature-settings` (wins over Ligatures) |
| **Small caps** | boolean | `font-variant-caps: small-caps` |
| **Hyphens** | `none`, `auto`, `manual` | `hyphens` / `-webkit-hyphens` |

All six are exposed on `add-canvas-text` CLI flags and the `create_canvas_text` MCP argument.

#### Template variables

Text objects support live template variables: `{{SheetName!CellRef}}`. At render time the variable resolves to the current cell value, giving you data-driven designs that stay in sync with workbook data automatically.

---

### Color swatches

A quick-access swatch palette lives in the fill and stroke pickers. Click any swatch for one-click application without opening the full color chooser.

---

### Gradient fills

Shapes support linear and radial gradient fills. Set gradient type, two stop colors, and rotation angle in the inspector's **Fill** section.

---

### Drop shadow controls

Shadows are available on text, shapes, lines, and images with full `{x, y, blur, color}` control:

- **X / Y** — horizontal and vertical offset in pixels (negatives allowed)
- **Blur** — softness in pixels (0 = sharp)
- **Color** — any CSS color; defaults to `rgba(0,0,0,0.3)`

The inspector groups the four sub-inputs under one labeled section:
- Text: **Text shadow** in the Effects tab
- Shapes / lines: **Shadow** in the Transform tab
- Images: **Shadow** in the Image Transform tab

```bash
# Legacy scalar (quick blur preset)
xapps add-canvas-shape MySheet rect --shadow 12

# Full structured drop shadow
xapps add-canvas-shape MySheet rect \
  --shadow-x 4 --shadow-y 8 --shadow-blur 16 --shadow-color "#0f172a"
```

Stored on `style.shadow` (`style.textShadow` for text effects). Legacy number values still render unchanged.

---

### Image controls

Selected images expose these controls in the inspector:

| Control | Effect |
|---|---|
| Opacity | 0–100% |
| Fit mode | `contain`, `cover`, `fill`, `stretch`, `original` |
| Corner radius | rounds corners |
| Shadow | x/y/blur/color drop shadow |
| Brightness / Contrast | photo adjustments |
| Saturation | color richness |
| Blur | Gaussian blur |
| Grayscale | 0–100% |
| Sepia | 0–100% |
| Flip H / V | mirror horizontally or vertically |
| Crop | inline drag crop |
| Background removal | AI-powered (requires `OPENAI_API_KEY`) |
| Image link | clickable URL on the object |
| Info link | metadata URL |
| Tags | keyword labels for search |
| Clip shape | circle, rounded rect, star, diamond, hexagon masks |
| Blend mode | normal, multiply, screen, overlay, darken, lighten, and more |

Right-click a canvas image and choose **Categorize image** to run AI-generated tagging (tags are stored on the object and shown in the inspector Summary pane).

#### Live image references

An image object can point at an image in another visual sheet instead of storing a separate URL:

1. Add or select an image object.
2. Choose **Reference existing**.
3. Pick a source image from a Gallery, Canvas, Whiteboard, or Presentation sheet.
4. Apply the change.

The canvas object renders the source image live and updates when the source changes. If the source is deleted the object shows a broken-source state until you relink or replace it.

---

### Inspector sidebar

The right-side inspector has tabbed sections that update when you select an object:

- **Style** — fill, stroke, opacity, gradient
- **Transform** — x, y, width, height, rotation, shadow
- **Effects** — blur, brightness, contrast, saturation, sepia, grayscale, blend mode, clip shape
- **Typography** — font, size, color, weight, align, kerning, ligatures, small caps, hyphens, paragraph spacing, OpenType features
- **Links** — image link, info link (with copy-formula button for spreadsheet reference)
- **Tags** — keyword tags + AI categorize button
- **Review comments** — add, resolve, reopen, and delete inline feedback threads

![Objects panel showing all canvas objects on the current page with type icons and z-order controls](/help-assets/screenshots/canvas-objects-panel.png)

---

### Layers and z-order

The right panel lists every object on the current page grouped by type. Arrow controls next to each row move the object forward or backward in the stacking order. The layer system also supports named layers (set on `style.layer`) for visibility and lock grouping.

**Z-order commands:**

```bash
xapps canvas-layout-objects MySheet --rows 3,5 --mode bring-front
xapps canvas-layout-objects MySheet --rows 3,5 --mode send-back
xapps canvas-layout-objects MySheet --rows 3,5 --mode bring-forward
xapps canvas-layout-objects MySheet --rows 3,5 --mode send-backward
```

---

### Grouping

Select two or more objects and group them so they move, resize, and lock together:

```bash
xapps canvas-group-objects MySheet --rows 2,3,4
xapps canvas-ungroup-objects MySheet --rows 2,3,4
```

Groups carry a shared `groupId` in `style.groupId`. Provide `--group-id` to assign a stable id; omit it and a timestamped id is generated automatically.

---

### Align and distribute

Select multiple objects and align or distribute them relative to each other:

| Mode | Effect |
|---|---|
| `align-left` | left-align to leftmost object |
| `align-center` | center horizontally |
| `align-right` | right-align to rightmost object |
| `align-top` | top-align to topmost object |
| `align-middle` | center vertically |
| `align-bottom` | bottom-align to bottommost object |
| `distribute-h` | equal horizontal spacing |
| `distribute-v` | equal vertical spacing |

```bash
xapps canvas-layout-objects MySheet --rows 2,3,4 --mode align-center
xapps canvas-layout-objects MySheet --rows 2,3,4 --mode distribute-h
```

---

### Bulk object actions

When more than one object is selected, Canvas supports:

- **Duplicate** with a +20, +20 pixel offset
- **Delete**
- **Group / Ungroup**
- **Lock / Unlock**
- **Align / Distribute**
- **Bring forward / Send backward / Bring to front / Send to back**

The toolbar exposes these as toolbar buttons; the CLI exposes identical deterministic operations with explicit row lists.

---

### Locking objects

Lock objects so they cannot be moved or resized accidentally. Locked objects still render and export.

```bash
xapps canvas-lock-objects MySheet --rows 1,2
xapps canvas-unlock-objects MySheet --rows 1,2
```

---

### Object comments (review workflow)

Every canvas object can carry a thread of review comments. Comments are displayed in the inspector and also show as an on-canvas badge count at the object's top-right corner.

![Canvas workspace with comments visible in the objects panel](/help-assets/screenshots/canvas-comments.png)

**Inspector** — select an object and use the "Review comments" section to add, resolve, reopen, or delete comments. New comments are stamped with the signed-in user's display name; fallback is "Anonymous".

**On-canvas pin** — when an object has at least one unresolved comment a small badge with the open count appears. Resolving the last open comment hides the badge. Clicking the badge selects the object and expands the inspector.

```bash
xapps canvas-add-comment MySheet --row 5 --text "Check contrast" [--author "Alex Kim"]
xapps canvas-list-comments MySheet [--row 5] [--include-resolved]
xapps canvas-resolve-comment MySheet --row 5 --comment-id <id>
xapps canvas-delete-comment MySheet --row 5 --comment-id <id>
```

`canvas-list-comments` prints `row\tid\tauthor\tcreatedAt\tstatus\ttext` — grep-friendly. Pass `--json` for structured output.

---

### Clipped metadata (Summary pane)

Canvas objects created from web clips carry structured metadata stored in `style.clipMeta`. The inspector shows a collapsible **Summary** section with:

- title, site, author, publish date
- brand, SKU, price, currency, availability, discount
- canonical URL, page URL, preview image URL
- description, selected text, keywords

Metadata is also promoted to columns `M:AC` on the backing object row, so formulas, dashboards, rules, and agents can read it directly from cells:

| Column | Field |
|---|---|
| M | title (`clipTitle`) |
| N | page title |
| O | product name |
| P | site name |
| Q | author |
| R | publish date |
| S | brand |
| T | SKU |
| U | price |
| V | currency |
| W | availability |
| X | canonical URL |
| Y | page URL |
| Z | preview image URL |
| AA | description |
| AB | selected text |
| AC | keywords |

The inspector shows a copy-formula button next to each field so you can paste the reference directly into a spreadsheet cell.

---

### Rulers

A ruler bar runs along the top and left edges of the artboard:

- **Unit selector** — switch between px, mm, cm, and in
- **Live position indicators** — crosshairs track cursor position on both rulers in real time

---

### Navigation and viewport

- Drag to pan, pinch or scroll to zoom
- Handles to resize, rotation handle to rotate
- Magenta alignment guides snap to other objects and artboard edges
- **Center view** — zooms to fit the current selection (max 400%) or fits the artboard when nothing is selected
- **Fit view** — calculates optimal zoom with padding so the full artboard is visible
- **Minimap** — toggle button in the lower-right corner opens a scaled overview with a viewport rectangle; click anywhere to jump the viewport; drag the viewport rectangle to pan; resize the rectangle to zoom
- On mobile, Canvas switches to a bottom tool dock; use the **Canvas** pill for artboard controls and the **Objects** pill for the inspector drawer

---

### Export

Export the current page from **File > Export** or via the CLI:

| Format | Command | Notes |
|---|---|---|
| SVG | `canvas-export-svg` | vector, self-contained |
| PNG | toolbar / menu | rasterized at artboard resolution |
| PDF | toolbar / menu | print-ready, correct page orientation |
| CSV | `canvas-export-csv` | one row per object, useful for diffing |

```bash
xapps canvas-export-svg MySheet --out poster.svg
xapps canvas-export-csv MySheet --out objects.csv
```

---

### Command Line Interface

Canvas exposes 22 CLI commands covering object creation, manipulation, page management, templates, comments, and export.

#### Object creation

```bash
xapps add-canvas-text <sheet> <text> \
  [--x <n> --y <n> --w <n> --h <n> --size <n> --color <hex> --font <family>
   --opacity <n> --page-id <id> --clip-meta <json>
   --shadow-x <n> --shadow-y <n> --shadow-blur <n> --shadow-color <css>
   --kerning <none|normal|auto> --ligatures <none|common|discretionary|all>
   --paragraph-spacing <em> --font-features <raw> --small-caps
   --hyphens <none|auto|manual>]

xapps add-canvas-shape <sheet> <shape> \
  [--x <n> --y <n> --w <n> --h <n> --fill <hex> --stroke <hex>
   --opacity <n> --rotation <deg> --content <text> --page-id <id>
   --shadow <n> | --shadow-x <n> --shadow-y <n> --shadow-blur <n> --shadow-color <css>]

xapps add-canvas-image <sheet> <url-or-path> \
  [--upload] [--x <n> --y <n> --w <n> --h <n> --fit <mode> --page-id <id>
   --image-link <url> --info-link <url> --clip-meta <json>
   --shadow <n> | --shadow-x <n> --shadow-y <n> --shadow-blur <n> --shadow-color <css>]
```

`<shape>` accepts: `rect`, `circle`, `triangle`, `star`, `polygon`, `rounded-rect`, `line`, `arrow`, `double-arrow`, `dashed-line`, `dashed-arrow`, `dotted-line`, `dotted-arrow`, `dot-dash-line`, `dot-dash-arrow`.

`--fit` accepts: `contain`, `cover`, `fill`, `stretch`, `original`.

`--upload` reads a local file and uploads it to `/api/uploads` before creating the object.

#### Object manipulation

```bash
xapps canvas-duplicate-objects <sheet> --rows <csv>
xapps canvas-delete-objects <sheet> --rows <csv>
xapps canvas-group-objects <sheet> --rows <csv> [--group-id <id>]
xapps canvas-ungroup-objects <sheet> --rows <csv>
xapps canvas-lock-objects <sheet> --rows <csv>
xapps canvas-unlock-objects <sheet> --rows <csv>
xapps canvas-layout-objects <sheet> --rows <csv> --mode <mode>
```

`--mode` for layout: `align-left`, `align-center`, `align-right`, `align-top`, `align-middle`, `align-bottom`, `distribute-h`, `distribute-v`, `bring-forward`, `send-backward`, `bring-front`, `send-back`.

#### Pages and artboard

```bash
xapps canvas-pages <sheet>                                    # list pages
xapps set-canvas-page <sheet> <index>                         # switch active page
xapps set-canvas-artboard <sheet> <preset>                    # resize current page
xapps canvas-magic-resize <sheet> --presets <csv> \
  [--mode <copy|replace>] [--page <index>]
```

#### Templates

```bash
xapps canvas-templates                                        # list all templates
xapps apply-canvas-template <sheet> <template-id> \
  [--mode <auto|replace|insert>] [--page-title <title>]
```

`--mode auto` replaces the page if it is empty, inserts a new page otherwise.

#### Comments

```bash
xapps canvas-add-comment <sheet> --row <n> --text <text> [--author <name>]
xapps canvas-list-comments <sheet> [--row <n>] [--include-resolved]
xapps canvas-resolve-comment <sheet> --row <n> --comment-id <id>
xapps canvas-delete-comment <sheet> --row <n> --comment-id <id>
```

#### Export

```bash
xapps canvas-export-svg <sheet> [--out <file>]
xapps canvas-export-csv <sheet> [--out <file>]
```

#### Scripted poster example

```bash
xapps create-sheet "MyPoster" --type canvas
xapps set-canvas-artboard MyPoster instagram-post
xapps add-canvas-shape MyPoster rect \
  --x 0 --y 0 --w 1080 --h 1080 --fill "#7c3aed"
xapps add-canvas-text MyPoster "BIG IDEA" \
  --x 60 --y 200 --size 96 --color "#ffffff" --bold
xapps add-canvas-text MyPoster "{{Sheet1!A1}}" \
  --x 60 --y 320 --size 32 --color "#f3e8ff"
xapps add-canvas-image MyPoster "https://picsum.photos/seed/hero/600/400" \
  --x 60 --y 440 --w 960 --h 560 --fit cover \
  --shadow-x 0 --shadow-y 12 --shadow-blur 32 --shadow-color "rgba(0,0,0,0.4)"
xapps canvas-export-svg MyPoster --out poster.svg
```

The `{{Sheet1!A1}}` template variable resolves at render time, so updating the spreadsheet cell automatically updates the canvas.

---

### MCP

The MCP surface mirrors the CLI 1:1:

`canvas_pages`, `set_canvas_page`, `set_canvas_artboard`, `canvas_magic_resize`, `canvas_templates`, `apply_canvas_template`, `add_canvas_text`, `add_canvas_shape`, `add_canvas_image`, `canvas_duplicate_objects`, `canvas_delete_objects`, `canvas_group_objects`, `canvas_ungroup_objects`, `canvas_lock_objects`, `canvas_unlock_objects`, `canvas_layout_objects`, `canvas_export_svg`, `canvas_export_csv`, `canvas_add_comment`, `canvas_list_comments`, `canvas_resolve_comment`, `canvas_delete_comment`.

---

### REST API

Canvas operations route through `/api/sheets/<canvas>/*`:

| Endpoint | Method | Purpose |
|---|---|---|
| `/api/sheets/<sheet>/settings` | GET / PUT | page list, artboard preset, background |
| `/api/sheets/<sheet>/objects` | GET / POST | list or create objects |
| `/api/sheets/<sheet>/objects/batch` | POST | bulk delete, duplicate, group, lock, layout |
| `/api/sheets/<sheet>/svg` | GET | export current page as SVG |
| `/api/sheets/<sheet>/csv` | GET | export object list as CSV |
| `/api/sheets/<sheet>/magic-resize` | POST | create multi-format page copies |
| `/api/uploads` | POST | upload image files (used by `--upload`) |

---

### Known follow-ups

- **Layered lock groups** — lock is per-object today; a group-wide lock that travels with group membership would simplify large compositions.
- **Style presets / saved themes** — save the current artboard's color palette and font stack as a reusable theme across pages.
- **Brand kit integration** — pull colors, fonts, and logos from a workbook-level "Brand" sheet for automatic cross-sheet consistency.
- **Snap to other objects** — currently snaps to artboard edges and grid; a unified snap engine across all object pairs would smooth heavier layouts.
