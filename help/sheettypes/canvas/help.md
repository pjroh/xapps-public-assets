## Design Canvas

### A fixed artboard for polished design work

Choose **Design Canvas** for a finished graphic at a known size. Use
**Whiteboard** for a workshop that needs room to grow, or **Presentation** for
a deck you will play slide by slide.

### Make a graphic from start to export

1. Add a **Design Canvas** sheet. Open **Design → Templates** in the left panel and choose a design close
   to your goal, or start with a blank page at your intended artboard size.
2. Replace the headline first. Double-click text to edit it, then use the
   inspector to set its typeface, size and alignment.
3. Add supporting shapes and images. Use uploads for your own assets or
   **Elements** for stock photos and icons. Review provider attribution.
4. Select objects together to align and distribute them. Group a finished
   section so it moves together; lock the background when it is set.
5. Make alternate sizes with **Design → Magic Resize**. Check every new page:
   a tall story and a wide banner usually need different text wrapping.
6. Export the finished page. Open the downloaded result and check the edges,
   text and images at the size your recipient will use.

![Canvas Templates panel showing editable design starting points](/help-assets/screenshots/canvas-templates.png)

### Build a small campaign kit

Keep the launch poster, social post and story in one Canvas sheet as separate
pages. Put shared facts in a Spreadsheet sheet and reference them in text as
`{{Launch Data!B2}}`. Workbook edits then update that text. Keep a Gallery for
approved images; use **Reference existing** when the design should follow
changes to an image there.

| Task | Control or approach | What to check |
|---|---|---|
| Change size | Artboard preset or Magic Resize | Wrapping and cropping on each page |
| Move several elements as one | Group | Select the group before dragging |
| Keep an element in place | Lock | Unlock it before editing |
| Adjust a partly hidden object | Objects panel | Correct object and z-order |
| Update shared copy | Template variable | Source sheet and cell reference |
| Keep an image linked | Reference existing | Source image still exists |

![Canvas headline selected with object editing controls visible](/help-assets/screenshots/canvas-inspector.png)

### Troubleshooting a design

- **An object will not move:** check its lock and active layer. Use the Objects
  panel when another object covers it.
- **The image is cropped:** review Fit and Crop. Cover fills the frame; Contain
  keeps the full image visible.
- **A variable or reference looks wrong:** check the source sheet and cell or
  image. Relink a deleted source.
- **Stock or AI creation is unavailable:** read the panel's provider status.
  Uploaded assets and built-in templates remain useful starting points.
- **A resized page looks crowded:** shorten or rearrange copy on that page;
  proportional scaling cannot make every layout suitable.

### Feature reference

Use Design Canvas when you want a bounded page instead of an infinite board. It is ideal for:

- social graphics
- event posters and flyers
- ads and marketing creatives
- simple diagrams and flow charts
- brand boards and moodboards
- mockups and exported assets

> Agent example: an agent can scaffold a launch graphic, drop in workbook values as template variables, categorize clipped images, and hand the composition to a human for final polish.

![Design Canvas event flyer with editable text, shapes and the Objects panel](/help-assets/screenshots/canvas-sheet.png)

The canvas UI gives you a ruler-edged artboard, a left tool rail, a top toolbar with artboard controls, and a right objects panel that lists every element on the current page.

![Closer view of the event flyer artboard and its text composition](/help-assets/screenshots/canvas-poster.png)

---

### Starter templates

Canvas ships a template library for common design jobs. Open **Design** in the
left rail and browse **Templates**, or use the template commands in the top
**Design** menu. The library includes search, categories, single-page designs
and multi-page starters. **Your templates** holds templates saved or created
in this workbook.

| Template ID | Title | Size |
|---|---|---|
| `social-quote` | Social Quote | 1080 × 1080 |
| `product-promo` | Product Promo | 1080 × 1080 |
| `story-announcement` | Story Announcement | 1080 × 1920 |
| `event-flyer` | Event Flyer | 1080 × 1350 |
| `brand-board` | Brand Board | 1920 × 1080 |
| `moodboard` | Moodboard | 1920 × 1080 |
| `product-launch-deck` | Product Launch Deck | 4 pages |
| `fundraising-pitch-deck` | Fundraising Pitch Deck | 4 pages |
| `marketing-campaign-kit` | Marketing Campaign Kit | 5 pages |

When the current page is empty, the template replaces it in place. When the page already has content, xApps inserts the template as a new page so your work stays intact. Multi-page sets replace the first empty page and append the remaining pages, or insert every page when the current page already has content.

### Start with AI

Open **Design** in the left rail to use **Start with AI**. Describe the design, pick a format and style, then generate a starting page. When OpenAI is configured on the server, Canvas requests an editable composition plan and places the returned objects on the current page. If OpenAI is unavailable, the panel labels the local starter fallback instead of presenting it as an AI result. Three variants remain available so switching variants replaces the generated object set instead of appending duplicates. After a generated design is placed, enter a refinement request to have OpenAI revise the selected variant using the original prompt and current visible design as context.

The same panel can create an **AI template pack**. Enter a campaign brief, category, target format, count, and style; Canvas asks OpenAI for a structured template plan, passes that copy/color/font direction through the verified template factory, publishes accepted templates into the current workbook, and refreshes the template browser so the new custom templates can be applied immediately.

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

### Stock photos and icons

Open **Elements** and search for terms such as `coffee`, `team`, or `home`. Canvas searches stock photo providers through `/stock/photos`, using Openverse by default and Unsplash/Pexels when `CANVAS_UNSPLASH_ACCESS_KEY` or `CANVAS_PEXELS_API_KEY` are configured. Provider results show real image thumbnails with attribution metadata.

If provider search is unavailable, Canvas shows an explicit source state instead of fake photo tiles. Use **Add URL / upload** to add a photo from your device or a URL, or select an image on the artboard and use **Replace selected** to swap its source while keeping its position.

Inserted provider photos keep attribution, license, source URL, provider, and source image metadata on the image object. Icons use a typed curated Lucide/Tabler/Material catalog, insert as SVG image objects, and retain the selected color, collection, and license metadata.

### SVG import

Drop an SVG file on the artboard, or upload it from the **Uploads** panel. Canvas parses supported SVG primitives into normal editable Canvas objects:

- `rect`
- `circle` / `ellipse`
- `polygon`
- `line`
- `text`

Supported primitives keep fills, strokes, simple transforms, and text styling where the Canvas model can represent them. Complex SVG content such as paths, filters, gradients, and unsupported fragments still imports as an uploaded image object so the artwork is not lost. SVGs dropped onto frame masks continue to behave like images and replace the frame contents.

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

Text objects support detailed typography controls:

| Feature | Values | CSS property |
|---|---|---|
| **Kerning** | `none`, `normal`, `auto` | `font-kerning` |
| **Ligatures** | `none`, `common`, `discretionary`, `all` | `font-feature-settings` |
| **Paragraph spacing** | em value | gap between `\n\n` paragraphs |
| **OpenType features** | raw string e.g. `'ss01' 1, 'tnum' 1` | `font-feature-settings` (wins over Ligatures) |
| **Small caps** | boolean | `font-variant-caps: small-caps` |
| **Hyphens** | `none`, `auto`, `manual` | `hyphens` / `-webkit-hyphens` |

All six are exposed on `add-canvas-text` CLI flags and the `canvas_create_text` MCP argument.

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
| Start with AI | OpenAI-backed editable composition and refinement when `OPENAI_API_KEY`, `XAPPS_OPENAI_API_KEY`, or MeshAgent room credentials are configured; local fallback is labeled |
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

Ruler units and cursor crosshairs, alignment-guide paint, minimap visibility, local pan/zoom, and the active selection are browser-session navigation state. They intentionally have no API, SDK, CLI, MCP, or persistence contract. Durable object geometry and styling remain available through the object state and guarded update contracts below; peer awareness is likewise browser-session-only.

---

### Export

Export designs from **Sheet > Save as**, the API, or the CLI:

| Format | Command | Notes |
|---|---|---|
| SVG | `canvas-export <sheet> svg` | current or all pages; vector output |
| PNG | `canvas-export <sheet> png` | rasterized at artboard resolution |
| JPG | `canvas-export <sheet> jpg --quality 90` | server-rendered raster output |
| PDF | `canvas-export <sheet> pdf` | server-rendered current/all-page PDF |
| CSV | `canvas-export <sheet> csv` | one row per object, useful for diffing |

```bash
xapps canvas-export MySheet png --out poster.png
xapps canvas-export MySheet pdf --all-pages --out campaign.pdf
xapps canvas-export MySheet svg --all-pages --json
```

---

### Command Line Interface

Canvas exposes 52 CLI commands covering collaboration inspection, governed AI runs, typed object inspection/update, object creation, media, live references, manipulation, page and layer management, templates, brand checks, comments, and export.

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

Object and comment mutations are guarded transactions. Normally the CLI reads the current object revision and generates a request id; for an exact retry, supply both `--expected-revision <n>` and `--request-id <stable-id>`.

#### Object inspection and guarded updates

```bash
xapps canvas-list-objects <sheet> --json
xapps canvas-get-object <sheet> <row-or-id> --json
xapps canvas-update-object <sheet> <row-or-id> '<patch-json>' \
  [--expected-revision <n> --request-id <stable-id>] --json
```

The update patch accepts the typed object fields exposed by the SDK, including content, geometry, page/z-order, typography, gradients, shadows, image fit/clip metadata, and other persisted inspector style fields. Identity remains immutable. Without explicit guard flags, the CLI reads the current object revision and creates a request id automatically.

#### Collaboration snapshots

Canvas keeps realtime browser edits in the existing per-object `canvasObjects` Yjs projection. The typed SDK layers a scoped revision cursor over the authoritative `objects:state` response, without adding a second transport:

```bash
xapps canvas-collaboration-snapshot <sheet> --json
xapps canvas-collaboration-resume <sheet> '{"protocolVersion":1,"revision":12,"sheet":"Design"}' --json
```

`getCollaborationSnapshot` returns the complete object snapshot and cursor. `subscribeCollaboration` polls that same guarded route and stops through its explicit `unsubscribe` function or an `AbortSignal`. `resumeCollaboration` rejects a cursor from another sheet. A revision gap or revision rollback returns `resetRequired: true`, telling callers to replace their snapshot; Canvas does not claim a delta history it does not persist. Peer identities and indefinite awareness streams remain session-local browser UI state and are intentionally not exposed to noninteractive CLI or agent tools.

#### Scoped batch authoring

Choose the authorized saved workbook and its actual storage target before running the examples. Set `XAPPS_API_BASE_URL` to that host. This helper keeps every operation in the same scope (replace the example file and `local` together when needed):

```bash
xapps_scoped() {
  xapps --base-url "${XAPPS_API_BASE_URL:?Set the authorized host URL}" \
    --file 'MyWorkbook.json' --workbook-storage-target local "$@"
}
```

Read the current snapshot, choose the returned row targets and set `CANVAS_REVISION` to that snapshot revision. The layout command performs one guarded supported batch:

```bash
xapps_scoped canvas-collaboration-snapshot Design --json
xapps_scoped canvas-layout-objects Design --rows 0,1 --mode align-left \
  --expected-revision "$CANVAS_REVISION" --request-id design-align-1 --json
xapps_scoped canvas-collaboration-snapshot Design --json
```

Use rows only from that same revision; stable object IDs identify later individual edits. Independent reads can run in parallel, but two writes cannot both assume one revision remains current. Keep the exact payload, expected revision and request ID after uncertain delivery; retry that same intent. On a revision conflict, reread and reconcile before creating a new intent and request ID.

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
xapps canvas-templates <sheet>                                # list built-ins plus sheet custom templates
xapps get-canvas-template <sheet> <template-id> [--page-title <title>] [--brand-kit <json>]
xapps register-canvas-template <sheet> [template-json] [--input <path>] [--replace]
xapps render-canvas-template-thumbnail <sheet> <template-id> [--out <file>]
xapps remove-canvas-template <sheet> <template-id>
xapps canvas-template-factory <sheet> --request-id <stable-id> --category <name> --brief <text> \
  [--count <1-60>] [--preset <preset>] [--seed <seed>] [--replace] [--dry-run]
xapps apply-canvas-template <sheet> <template-id> --request-id <stable-id> \
  [--mode <auto|replace|insert>] [--page-title <title>] [--brand-kit <json>]
```

`--mode auto` replaces the page if it is empty, inserts a new page otherwise.
Template application and factory publication are server-owned transactions. The complete next page/object or template-pack state is validated before mutation and saved once. Reuse `--request-id` only for an identical retry: an identical request replays the persisted receipt without duplicating objects/templates, while changed reuse is rejected. `canvas-template-factory --dry-run` does not mutate and therefore does not require a request id.
Custom-template registration and removal use the same revision-guarded model through `templates:state` and `templates:mutate`; provider-neutral verified packs publish atomically through `templates:publish`.
Template-set IDs such as `product-launch-deck`, `fundraising-pitch-deck`, and `marketing-campaign-kit` create multiple Canvas pages in one apply operation.
`--brand-kit` accepts a JSON object with color roles (`primary`, `secondary`, `accent`, `background`, `surface`, `text`, `muted`) and font roles (`fontHeading`, `fontBody`) so brandable templates can be recolored when they are applied.
Agent-authored templates use the canonical `canvas-template-doc-v1` shape: `id`, `title`, `category`, `description`, `pages[]`, canvas `objects[]`, optional `tags`, `paletteSlots`, `fontSlots`, and thumbnail metadata. They persist in the workbook sheet and can be applied with the same `apply-canvas-template` command.
`canvas-template-factory` generates a batch of agent-authored template documents, verifies contrast, overlap, text overflow, and meaningful content coverage, then publishes accepted templates through the same sheet template registry. Rejected candidates are returned with reason codes so agents can retry or adjust the brief.

#### Governed AI runs

```bash
xapps canvas-ai-plan <sheet> <run-json>
xapps canvas-ai-status <sheet> [run-id]
xapps canvas-ai-resume|canvas-ai-approve|canvas-ai-apply|canvas-ai-cancel <sheet> <run-id> <transition-json>
```

Runs persist provider response ids, retry state, and stream cursors. Approved output is recorded as complete only with a receipt from an atomic Canvas object, media, template, or template-pack mutation.

#### Brand report

```bash
xapps canvas-brand-report <sheet> --brand-kit <json>
```

The report scans existing Canvas objects for hex colors and text fonts that are outside the supplied Brand Kit. It does not mutate the design; it returns issue rows and suggestions for cleanup.

#### Comments

```bash
xapps canvas-add-comment <sheet> --row <n> --text <text> [--author <name>]
xapps canvas-list-comments <sheet> [--row <n>] [--include-resolved]
xapps canvas-resolve-comment <sheet> --row <n> --comment-id <id>
xapps canvas-delete-comment <sheet> --row <n> --comment-id <id>
```

#### Stock and media

```bash
xapps canvas-search-stock <sheet> <photos|icons> [query] [--limit <1-24>]
xapps canvas-import-media <sheet> <url|upload-ref|path|svg> [--upload|--svg] \
  [--replace <row-or-id> --page-id <id> --x <n> --y <n> --w <n> --h <n>]
xapps canvas-list-media <sheet>
```

Media import is revision-guarded and workbook-scoped. Safe SVG primitives become editable objects; complex safe SVG falls back to a workbook-owned PNG. Active SVG content, unsupported MIME types, oversized files, and invalid or cross-workbook upload references are rejected before the workbook is saved.

#### References, live embeds, and variables

```bash
xapps canvas-discover-references <sheet> [image|embed|variable] [query] [--limit <1-200>]
xapps canvas-resolve-reference <sheet> <image|embed|variable> <source-sheet> <source-id>
xapps canvas-list-references <sheet>
xapps canvas-bind-reference <sheet> <image|embed|variable> <target> <source-sheet> <source-id>
xapps canvas-refresh-reference <sheet> <image|embed|variable> <target>
xapps canvas-unbind-reference <sheet> <image|embed|variable> <target>
```

Reference writes are revision-guarded and workbook-scoped. Live embeds store a sheet view, image bindings keep a typed source reference, and variables write the renderer-compatible `{{Sheet!Cell|format}}` token. Refresh persists resolved or broken metadata; cross-workbook identities are rejected.

#### Export

```bash
xapps canvas-export <sheet> <svg|csv|png|jpg|jpeg|pdf> \
  [--out <file> --all-pages --page <index> --page-id <id> --quality <1-100>]
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

The MCP surface exposes the same 52 supported Canvas operations as the CLI, using canonical `canvas_*` tool names:

`canvas_collaboration_snapshot`, `canvas_collaboration_resume`, `canvas_ai_plan`, `canvas_ai_status`, `canvas_ai_transition`, `canvas_ai_resume`, `canvas_ai_approve`, `canvas_ai_apply`, `canvas_ai_cancel`, `canvas_list_objects`, `canvas_get_object`, `canvas_update_object`, `canvas_list_templates`, `canvas_get_template`, `canvas_template_factory`, `canvas_register_template`, `canvas_remove_template`, `canvas_render_template_thumbnail`, `canvas_apply_template`, `canvas_brand_report`, `canvas_list_pages`, `canvas_set_page`, `canvas_set_artboard`, `canvas_magic_resize`, `canvas_mutate_page`, `canvas_mutate_layer`, `canvas_create_text`, `canvas_create_shape`, `canvas_create_image`, `canvas_duplicate_objects`, `canvas_delete_objects`, `canvas_group_objects`, `canvas_ungroup_objects`, `canvas_lock_objects`, `canvas_unlock_objects`, `canvas_layout_objects`, `canvas_search_stock`, `canvas_import_media`, `canvas_list_media`, `canvas_discover_references`, `canvas_resolve_reference`, `canvas_list_references`, `canvas_bind_reference`, `canvas_refresh_reference`, `canvas_unbind_reference`, `canvas_export_artifact`, `canvas_export_svg`, `canvas_export_csv`, `canvas_add_comment`, `canvas_list_comments`, `canvas_resolve_comment`, `canvas_delete_comment`.

---

### REST API

Canvas operations route through `/api/sheets/<canvas>/*`:

| Endpoint | Method | Purpose |
|---|---|---|
| `/api/sheets/<sheet>/settings` | GET / PUT | page list, artboard preset, background |
| `/api/sheets/<sheet>/objects` | GET / POST | list or create objects |
| `/api/sheets/<sheet>/objects:state` | GET | read the guarded object revision and complete object list |
| `/api/sheets/<sheet>/objects:mutate` | POST | guarded object CRUD, atomic batch, and comment mutations with replay receipts |
| `/api/sheets/<sheet>/stock/photos` / `stock/icons` | GET | typed stock photo or curated icon search |
| `/api/sheets/<sheet>/media` / `media/<assetId>` | GET | workbook media asset and object-reference readback |
| `/api/sheets/<sheet>/media:import` | POST | guarded secure image/SVG add or replace with rollback |
| `/api/sheets/<sheet>/reference-sources` | GET | discover typed image, live-embed, and variable sources in the active workbook |
| `/api/sheets/<sheet>/references:resolve` | POST | resolve one typed source without mutation |
| `/api/sheets/<sheet>/references` | GET / POST | list bindings or bind a source with revision/idempotency guards |
| `/api/sheets/<sheet>/references/<target>` | PUT / DELETE | replace or remove a binding; `/refresh` persists resolved/broken state |
| `/api/sheets/<sheet>/objects/batch` | POST | bulk delete, duplicate, group, lock, layout |
| `/api/sheets/<sheet>/templates` | GET / POST | list built-in and sheet custom templates; register an agent-authored template document |
| `/api/sheets/<sheet>/templates/ai` | POST | create a brief-driven OpenAI template pack, verify accepted templates, and publish them as sheet custom templates |
| `/api/sheets/<sheet>/templates:apply` | POST | atomically apply a built-in or custom template with a stable `requestId`; identical retries replay without another save |
| `/api/sheets/<sheet>/templates:factory` | POST | generate/verify a template pack and atomically publish it with one save; `publish:false` performs a dry run |
| `/api/sheets/<sheet>/templates/<id>` | GET / DELETE | fetch a template or multi-page template-set instance; remove a custom template; optional `brandKit` query JSON applies brand tokens |
| `/api/sheets/<sheet>/templates/<id>/thumbnail` | GET | render a template thumbnail SVG; `?format=json` returns JSON-wrapped SVG for MCP/toolkit callers |
| `/api/sheets/<sheet>/brand-report` | POST | audit colors and fonts against a Brand Kit |
| `/api/sheets/<sheet>/svg` | GET | export current page as SVG |
| `/api/sheets/<sheet>/pdf` | GET | export all pages as server-rendered PDF; `page`/`pageId` limits to one page |
| `/api/sheets/<sheet>/jpg` | GET | export current page as JPEG; accepts `quality=1..100`, `page`, and `pageId` |
| `/api/sheets/<sheet>/png` | GET | export one page as PNG; accepts `page` or `pageId` |
| `/api/sheets/<sheet>/csv` | GET | export object list as CSV |
| `/api/sheets/<sheet>/export-artifacts` | POST | strict typed SVG/CSV/PNG/JPEG/PDF manifest with digest and optional base64 bytes |
| `/api/sheets/<sheet>/magic-resize` | POST | create multi-format page copies |
| `/api/uploads` | POST | workbook-scoped image upload; Canvas uses purpose `canvas-image` and a 20 MB limit |

---

### Known follow-ups

- **Layered lock groups** — lock is per-object today; a group-wide lock that travels with group membership would simplify large compositions.
- **Style presets / saved themes** — save the current artboard's color palette and font stack as a reusable theme across pages.
- **Brand kit persistence** — pull colors, fonts, and logos from a workbook-level "Brand" sheet instead of requiring each command/tool call to pass JSON.
- **Snap to other objects** — currently snaps to artboard edges and grid; a unified snap engine across all object pairs would smooth heavier layouts.
