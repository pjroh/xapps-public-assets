## 🎨 Design Canvas

### A fixed artboard for polished design work

Use Design Canvas when you want a bounded page instead of an infinite board. It is ideal for:

- social graphics
- posters
- ads
- simple diagrams
- mockups
- exported creative assets

> 🤖 Agent example: an agent can scaffold a launch graphic, drop in workbook values as template variables, categorize clipped images, and hand the composition to a human for final polish.

![Design Canvas artboard with layered objects and a polished layout](/help-assets/screenshots/canvas-sheet.png)

### 🧩 Starter templates

Canvas now includes a starter template library for common design jobs:

- Social Quote
- Product Promo
- Story Announcement
- Event Flyer
- Brand Board
- Moodboard

Use the `Templates` button in the page bar or `Design -> Apply template...`.
If the current page is empty, the template replaces it. If the page already has content, xApps inserts the template as a new page so your work stays intact.

### 📄 Multiple pages and artboards

Each canvas sheet can contain multiple pages, and each page has its own:

- size
- background
- object set

Common artboard workflows include portrait, landscape, and social-media-sized layouts. Canvas pages are better than separate sheets when the design belongs to one project.

Canvas also supports **Magic Resize** for Canva-style copy-and-resize workflows:

- use the `Resize` button in the page bar
- or `Design -> Magic Resize...`
- choose one or more target presets like Instagram Story, Twitter Header, or A4
- xApps creates resized page copies and scales the current page content into each new format

`Replace current page first` is also available when you want the first selected target to overwrite the current page instead of creating only copies.

### ➕ Objects you can place

- text
- shapes (rectangle, ellipse, rounded rectangle, star, polygon/hexagon)
- lines and arrows
- images

Shapes can also hold text labels now. Double-click a shape, or select it and press `Enter`, to edit the label inside it.

Right-click an object to see its backing storage footer at the bottom of the context menu. For Canvas objects, that footer shows the exact backing cell range for the object row.

### ✏️ Line styles

Nine line styles are available for lines, arrows, and shape strokes:

- solid, dashed, dotted
- solid + arrow end, dashed + arrow end, dotted + arrow end
- solid + dot end, dashed + dot end, dotted + dot end

### 🎨 Color swatches

A quick-access color palette is available in the fill and stroke pickers. Click any swatch for one-click fill or stroke application without opening the full color chooser.

### 🔤 Text features

- **Text effects** — letter spacing, line height, text transform (uppercase / lowercase / capitalize), and text shadow
- **Rich inline text** — bold, italic, underline, and strikethrough within a single text box via the floating format bar

### 📏 Rulers

A ruler bar runs along the top and left edges of the canvas. Features:

- **unit selector** — switch between px, mm, cm, and in
- **live position indicators** — crosshairs track cursor position on both rulers in real time

### 🧲 Design tools

Canvas now supports a much more complete visual-editing workflow:

- **group / ungroup**
- **align / distribute**
- **copy style**
- **gradient fills**
- **drop shadows**
- **lock objects**
- **shift + drag marquee multi-select**
- **template picker** for fast Canva-style starting points
- **Magic Resize** for multi-format page copies
- **undo / redo buttons** in the toolbar

### ✅ Bulk actions

When more than one object is selected, Canvas supports:

- **Duplicate** with a `+20,+20` offset
- **Delete**
- **Group / Ungroup**
- **Lock / Unlock**
- **Align / Distribute**
- **Bring forward / Send backward**
- **Bring to front / Send to back**

The CLI exposes the same deterministic operations with explicit row lists:

- `canvas-duplicate-objects`
- `canvas-delete-objects`
- `canvas-group-objects`
- `canvas-ungroup-objects`
- `canvas-lock-objects`
- `canvas-unlock-objects`
- `canvas-layout-objects`
  - supports `bring-forward`, `send-backward`, `bring-front`, and `send-back`

### 🖼️ Image controls

Selected images can use:

- opacity
- fit mode
- corner radius
- shadow
- brightness / contrast / saturation
- blur / grayscale / sepia
- crop
- background removal
- image link
- info link
- tags
- **clip shapes** — circle, rounded rect, star, diamond, hexagon masks
- **blend modes** — normal, multiply, screen, overlay, darken, lighten, and more

If the server has `OPENAI_API_KEY` configured, right-click a canvas image and choose `Categorize image` to add AI-generated tags. Those tags are stored on the image object and also surface in the inspector summary metadata.

### 🧾 Clipped metadata summary

Canvas now gives clipped page/article cards and clipped image/product cards a structured **Summary** section inside the inspector.

What shows up there:

- title, site, author, publish date
- brand, SKU, price, currency, availability
- canonical URL, page URL, preview image URL
- description, selected text, and keywords

The Summary section also shows formula-ready references back to the backing object row cells. For Canvas clips, the promoted metadata lives in columns `M:AC` on the object row:

- `M` title
- `N` page title
- `O` product name
- `P` site name
- `Q` author
- `R` publish date
- `S` brand
- `T` SKU
- `U` price
- `V` currency
- `W` availability
- `X` canonical URL
- `Y` page URL
- `Z` preview image URL
- `AA` description
- `AB` selected text
- `AC` keywords

This means clipped Canvas content is not just visual. Spreadsheet formulas, dashboards, rules, and agents can read the extracted metadata directly from cells while the object still keeps the full `style.clipMeta` payload.

### 🔗 Live image references

Canvas image objects can point at image sources in other visual sheets instead of storing a separate image URL.

Use this flow:

1. Add or select an image object.
2. Choose `Reference existing`.
3. Pick a source image from a `Gallery`, `Design Canvas`, `Whiteboard`, or `Presentation` sheet.
4. Apply the change.

What happens next:

- the canvas object renders the source image live
- if the source image changes, the canvas object updates too
- if the source object is deleted, the canvas object keeps the reference and shows a broken-source state until you relink or replace it

For normal use, you do not need the raw object ID because the picker handles it for you. Stable IDs are mainly for API and CLI workflows.

### 🧭 Navigation and layout

- drag to move
- handles to resize
- rotation handle for rotation
- magenta alignment guides for snap feedback
- layers for stacking order
- the minimap in the lower-right can be collapsed to a compact `Map` pill and reopened from the same spot
- click anywhere in the minimap to jump the viewport
- drag the `View` grip inside the minimap viewport for easier navigation
- use the corner handles on the minimap viewport to zoom by resizing the visible frame
- on phones, Canvas switches to a bottom tool dock instead of a permanent left rail
- on phones, use the `Canvas` pill to reveal artboard controls and the `Objects` pill to open the inspector drawer
- export as **PNG**, **SVG**, or **PDF**
- **center view** — zooms to fit the current selection (max 400%) or fits the artboard when nothing is selected
- **fit view** — calculates optimal zoom with padding so the full artboard is visible

### 🗺️ Minimap

A toggle button in the bottom-right corner opens the minimap overlay:

- shows a scaled overview of the artboard with a viewport rectangle
- click anywhere in the minimap to jump the viewport
- drag the viewport rectangle to pan
- resize the viewport rectangle to zoom

### 🔣 Template Variables

Text objects support live template variables using the syntax `{{SheetName!CellRef}}`. At render time, the variable resolves to the current value of the referenced cell. This lets you build data-driven designs that stay in sync with workbook data.

> 💡 Use Canvas when you care about a polished final composition. Use Whiteboard when you want infinite space and looser thinking.

---

### Command Line Interface

Canvas exposes 18 CLI commands covering object creation, manipulation, page management, templates, and export. Every UI mutation is also a scriptable CLI / MCP call so agents can author entire compositions without the GUI.

#### Object creation

```bash
xapps add-canvas-text <sheet> <text> [--x <n> --y <n> --w <n> --h <n> --size <n> --color <hex> --font <family> --opacity <n> --page-id <id> --clip-meta <json>]
xapps add-canvas-shape <sheet> <shape> [--x <n> --y <n> --w <n> --h <n> --fill <hex> --stroke <hex> --opacity <n> --rotation <deg> --content <text> --page-id <id>]
xapps add-canvas-image <sheet> <url-or-path> [--upload] [--x <n> --y <n> --w <n> --h <n> --page-id <id> --image-link <url> --info-link <url> --clip-meta <json>]
```

`<shape>` is one of `rect`, `circle`, `triangle`, `star`, `polygon`, `rounded-rect`, `line`, `arrow`, `double-arrow`, `dashed-line`, `dashed-arrow`, `dotted-line`, `dotted-arrow`, `dot-dash-line`, or `dot-dash-arrow`. `--upload` on `add-canvas-image` reads a local path and uploads through `/api/uploads` first.

#### Object manipulation

```bash
xapps canvas-delete-objects <sheet> --rows <csv>
xapps canvas-duplicate-objects <sheet> --rows <csv>
xapps canvas-group-objects <sheet> --rows <csv> [--group-id <id>]
xapps canvas-ungroup-objects <sheet> --rows <csv>
xapps canvas-lock-objects <sheet> --rows <csv>
xapps canvas-unlock-objects <sheet> --rows <csv>
xapps canvas-layout-objects <sheet> --rows <csv> --mode <mode>
```

`--mode` for layout: `align-left`, `align-center`, `align-right`, `align-top`, `align-middle`, `align-bottom`, `distribute-h`, `distribute-v`, `bring-front`, `send-back`, and the rest of the alignment / stacking actions exposed in the toolbar.

#### Pages + artboard

```bash
xapps canvas-pages <sheet>                                    # list pages
xapps set-canvas-page <sheet> <index>                         # switch active page
xapps set-canvas-artboard <sheet> <preset>                    # change the current page's artboard
xapps canvas-magic-resize <sheet> --presets <csv> [--mode <copy|replace>] [--page <index>]
```

Preset names accept the same values the toolbar sends to the server: `instagram-post`, `instagram-story`, `twitter-header`, `presentation-16x9`, `a4-portrait`, `a4-landscape`, `letter-portrait`, and `letter-landscape`.

#### Templates + export

```bash
xapps canvas-templates                                        # list available starter templates
xapps apply-canvas-template <sheet> <template-id> [--mode <auto|replace|insert>] [--page-title <title>]
xapps canvas-export-csv <sheet> [--out <file>]
xapps canvas-export-svg <sheet> [--out <file>]
```

Templates seed a whole page from a curated starting point (greeting card, social post, business card, etc.). `canvas-export-csv` gives one row per object for inspection / diffing; `canvas-export-svg` produces a self-contained vector file for hand-off.

#### Scripted poster example

```bash
xapps create-sheet "MyPoster" --type canvas
xapps set-canvas-artboard MyPoster instagram-post
xapps add-canvas-shape MyPoster rect --x 0 --y 0 --w 1080 --h 1080 --fill "#7c3aed"
xapps add-canvas-text MyPoster "BIG IDEA" --x 60 --y 200 --size 96 --color "#ffffff"
xapps add-canvas-text MyPoster "{{Sheet1!A1}}" --x 60 --y 320 --size 32 --color "#f3e8ff"
xapps canvas-export-svg MyPoster --out poster.svg
```

The `{{Sheet1!A1}}` template variable resolves at render time, so updating the spreadsheet cell automatically updates the canvas.

---

### MCP

The MCP surface mirrors the CLI 1:1: `canvas_pages`, `set_canvas_page`, `set_canvas_artboard`, `add_canvas_text`, `add_canvas_shape`, `add_canvas_image`, `canvas_delete_objects`, `canvas_duplicate_objects`, `canvas_group_objects`, `canvas_ungroup_objects`, `canvas_lock_objects`, `canvas_unlock_objects`, `canvas_layout_objects`, `canvas_magic_resize`, `canvas_templates`, `apply_canvas_template`, `canvas_export_csv`, `canvas_export_svg`.

---

### REST API

Canvas operations route through `/api/sheets/<canvas>/*` for settings, objects, magic resize, templates, and export. In-progress browser drag state stays client-side; image uploads reach the shared `/api/uploads` endpoint via `--upload`.

---

### Known Follow-Ups

- **Layered lock groups** — lock is per-object today; multi-object lock that travels with a group would simplify big compositions.
- **Style presets / saved themes** — let a user save the current artboard's color palette + font stack as a reusable theme they can apply to other pages.
- **Brand kit integration** — pull colors / fonts / logos from a workbook-level "Brand" sheet so cross-sheet design consistency is automatic.
- **Snap-to-other-objects** — partial today (artboard edges + grid); a unified snap engine across all object types would smooth heavier layouts.
