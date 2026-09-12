## Presentation

### Build slide decks inside the workbook

Use **Presentation** for a sequence of slides with speaker notes and playback.
Use **Design Canvas** for a standalone graphic and **Typewriter** for a report
people will read as a document.

### Build a deck people can follow

1. Start with a deck template for a ready-made narrative, or add individual
   template slides for your own structure.
2. Choose a theme before polishing objects so the deck has consistent colors.
3. Write each title as its slide's main point. Choose a suitable layout for
   the evidence: KPI for metrics, comparison for alternatives, timeline for dates.
4. Edit text on the stage and use the Objects panel for precise selection,
   position and size. Put detailed explanation in the speaker notes below.
5. Reorder the thumbnails into the story you want to tell. Check the opening
   and closing as carefully as the middle of the deck.
6. Start playback with **F5** or **View → Start presentation**. Navigate through
   every slide and press **Escape** to return to editing.
7. Export PDF for viewing or editable PowerPoint for further work. Inspect the
   result and its fidelity report before sending it.

### Choose a starting point

| Goal | Starting point | Add before presenting |
|---|---|---|
| Report project progress | Project Status | Actual milestones, risks and decisions |
| Explain a proposal | Sales Proposal | Audience-specific problem, scope and price |
| Teach a process | Training Workshop | Worked examples and exercise instructions |
| Pitch a product | Startup Pitch | Evidence, assumptions and the specific ask |

### Keep numbers connected to their evidence

Use `{{SheetName!CellRef}}` in text for live workbook values. Use a live embed
for a workbook view that needs more context than one number. Open its source
before the meeting and confirm the latest values. Exports capture a point in
time; the workbook remains the place to edit the source and linked presentation.

### Rehearse the complete experience

- Read the slide title first: it should express what the audience needs to
  understand, not only name the topic.
- Check labels, tables and images in playback.
- Review each slide's speaker notes and linked sources.
- Advance through the final slide, then open the exported file.

### Feature reference

Presentation sheets give you a full slide editor with themes, slide templates, deck templates, text boxes, shapes, tables, images, speaker notes, and fullscreen playback -- all without leaving xApps.

> 🤖 Agent example: an agent can draft the first slide deck from workbook data, lay out the narrative, and leave the human presenter with editable slides rather than a blank canvas.

![Presentation sheet showing the slide thumbnail rail, editable stage, objects panel, and speaker notes](/help-assets/screenshots/presentation-sheet.png)

---

### Features

- Slide thumbnails and editable stage
- 8 built-in themes (Clarity, Summit, Studio, Forest, Midnight, Coral, Slate, Aurora)
- 14 slide templates (title, section, bullets, two-column, timeline, KPI, quote, big-number, image-text, process, team, agenda, comparison, thank-you)
- 4 deck templates (Startup Pitch, Project Status, Training Workshop, Sales Proposal)
- Text boxes with full formatting (font, size, color, bold, italic, underline, bullets, alignment, line height)
- 16 shape types including rectangle, circle, diamond, triangle, pill, chevron, star, callout, and more
- Object rotation (any angle, via inspector)
- 6 line presets: diagonal, arrow, double-arrow, divider, dashed, dotted — with configurable arrowheads
- Tables with per-cell/row/column formatting, stripe presets, border controls
- Images (upload, URL, drag-drop, live-linked references)
- Image editing sidebar (opacity, shadow, corners, blend mode, brightness, contrast, saturation, blur, B&W, sepia, clip shapes, fit modes, background erase, flip)
- Live embeds — insert a live view of any workbook sheet onto a slide
- Speaker notes per slide
- Object inspector panel (position, size, rotation, color, typography, table cell formatting)
- Context menu object actions (bring to front, send to back, duplicate, delete; duplicate/delete slide from thumbnail)
- Slide reordering by drag-and-drop in the thumbnail rail
- Slide backgrounds (solid color, right-click stage to set)
- Undo/redo
- Real-time collaboration (shared cursors and live drag presence)
- Template variables in text boxes
- PowerPoint (PPTX) import
- PDF export
- Editable PowerPoint (PPTX) export
- Fullscreen presenter mode (F5, with slide counter and navigation)

---

### Getting Started

1. Create a new sheet and choose **Presentation** from the sheet type menu.
2. A default Title Slide is created automatically.
3. Use **Slides > Templates...** to start from a complete deck template, or **Insert > Add template slide...** to add individual polished slides.
4. Click or double-click text objects to edit them.
5. Use the **Insert** menu or toolbar buttons to add shapes, images, lines, tables, and text boxes.
6. Add speaker notes in the notes area below the stage.
7. Press `F5` or **View > Start presentation** to enter fullscreen playback.

![Slide editor showing thumbnail rail, stage with sample pitch deck slide, and Objects panel](/help-assets/screenshots/presentation-editor.png)

---

### Themes

Themes control the visual direction of the deck: background color, stage color, accent color, text color, and subtext color. Eight themes are built in:

| Theme | Style |
|---|---|
| Clarity | Clean white with blue accent |
| Summit | Warm cream with orange accent |
| Studio | Dark slate with sky-blue accent |
| Forest | Light green with green accent |
| Midnight | Deep indigo with purple accent |
| Coral | Soft pink with red accent |
| Slate | Neutral gray with slate accent |
| Aurora | Dark stone with amber accent |

Apply a theme from the **Slides** menu (Theme section) using the keyboard shortcut `Cmd/Ctrl + Shift + 1–8`, or from the **Slides > Templates...** dialog. Each slide template adapts its colors to the active theme.

![Slides menu showing layout and theme options](/help-assets/screenshots/presentation-slides-menu.png)

---

### Slide Templates

Insert individual polished slides from **Slides > Insert template slide...**:

| Template | Layout |
|---|---|
| Title | Large title + subtitle + accent bar |
| Section Divider | Section label + title + description |
| Title + Bullets | Title + horizontal rule + bullet list |
| Two Column | Title + two side-by-side text panels |
| Timeline | Title + horizontal timeline with 3 milestones |
| KPI Snapshot | Title + 3 metric cards with values |
| Quote | Featured quote with attribution |
| Big Number | Single large metric with context |
| Image + Text | Left visual panel + right key points |
| Process / Steps | 4-step process with numbered circles |
| Team | 4 team member cards with roles |
| Agenda | Numbered agenda items with time allocations |
| Comparison | Before vs. After side-by-side |
| Thank You | Closing slide with contact info |

---

### Deck Templates

Apply a complete multi-slide deck from **Slides > Apply deck template...**:

| Template | Slides | Theme |
|---|---|---|
| Startup Pitch | Title, Problem, Solution, KPI, Timeline, Business Model, Team, Ask | Studio |
| Project Status | Status Update, Bullets, Timeline, KPI, Risks, Decisions, Thank You | Clarity |
| Training Workshop | Cover, Agenda, Learning Objectives, Framework, Two-Column, Quote, Thank You | Summit |
| Sales Proposal | Proposal, Challenge, Solution, Big Number, Comparison, Pricing, Thank You | Coral |

---

### Slide Objects in Detail

#### Text Boxes

Click or double-click a text object to edit it inline. Text boxes support:

- Font size, color, weight, family
- Text alignment (left, center, right)
- Line height and letter spacing
- Text transform (uppercase, etc.)
- Template variable syntax: `{{SheetName!CellRef}}`

Text roles include `title`, `subtitle`, `text` (body), `eyebrow`, `quote`, and `attribution`.

#### Shapes

Built-in shape types:

| Shape ID | Name |
|---|---|
| `rect` | Rectangle |
| `rounded` | Rounded Rectangle |
| `circle` | Circle |
| `diamond` | Diamond |
| `triangle` | Triangle |
| `pill` | Pill / Stadium |
| `arrow` | Arrow |
| `doubleArrow` | Double Arrow |
| `chevron` | Chevron |
| `hexagon` | Hexagon |
| `star` | Star |
| `parallelogram` | Parallelogram |
| `trapezoid` | Trapezoid |
| `wedgeCallout` | Callout |
| `leftBrace` | Brace |
| `punchedTape` | Punched Tape |

Shapes support fill color, stroke color, stroke width, border style (solid, dashed, dotted), opacity, and optional text labels. Select a shape and press `Enter` or click it again to edit the label text. Use the on-slide rotation handle for visual rotation, hold `Shift` while dragging to snap to 15 degree increments, or use the inspector **Rotation** field (-360 to 360 degrees) for exact values.

#### Lines and Arrows

Six line presets are available from **Insert > Add line**:

| Preset | Description |
|---|---|
| Line | Freeform diagonal line |
| Arrow Line | Diagonal line with end arrowhead |
| Double Arrow | Horizontal line with arrows on both ends |
| Divider | Horizontal solid rule |
| Dashed Line | Horizontal dashed rule |
| Dotted Line | Horizontal dotted rule |

The line inspector lets you set stroke color, weight (1–24 px), dash style (solid, dashed, dotted, dash-dot), and start/end arrowheads independently.

#### Tables

Tables support:

- Add or remove rows and columns via the table inspector or right-click menu
- Resize columns and rows by dragging internal guide handles
- Cell fill color with **Format fill** targeting a cell, row, or column (set scope in the inspector)
- Per-cell text color and bold toggle
- Alternating stripe presets: Rows (blue mist, warm sand, mint), Columns (lilac, citrus, ocean)
- Border color, width, and style (solid, dashed, dotted) via the inspector
- Global default text color and font size for the whole table
- Move a table by selecting it and dragging the **Move** grip
- Resize a table via the width and height fields in the inspector

#### Images

Add images by:

- **Drag-drop** -- drag image files directly onto the slide stage
- **Upload** -- use the image button popover to upload from your device
- **URL** -- paste an image URL in the image button popover
- **CLI** -- `add-image` command with URL or local file path

**Live image references:** Link a slide image to a source from Gallery, Design Canvas, Whiteboard, or another Presentation sheet. The image stays linked to the source instead of copying it. If the source is later deleted, the slide shows a broken-source state so you can relink.

#### Image Editing Sidebar

When an image is selected, a sidebar panel opens with:

| Section | Controls |
|---|---|
| Transform | Opacity, shadow, corner radius, blend mode |
| Adjustments | Brightness, contrast, saturation, blur, grayscale, sepia |
| Shape & Fit | Clip shapes (circle, rounded rect, star, diamond, hexagon), fit modes (cover, contain, fill) |
| Actions | Erase background, flip horizontal/vertical, reset to original |

![Market Opportunity slide showing two-column layout with TAM/SAM/SOM data, speaker notes visible below the stage, and slide thumbnail rail](/help-assets/screenshots/presentation-slide-market.png)

#### Live Embeds

Use **Insert > Insert Embed...** to embed a live view of any other sheet directly on a slide. The embed shows the current data from the linked sheet and updates when that sheet changes. Supports Gallery, Records, Kanban, Canvas, and other sheet types.

#### Object Inspector Panel

When any object is selected, a panel opens on the right with:

- **Transform**: X, Y, width, height (numeric), and rotation (degrees)
- **Opacity**: 0–100% slider
- **Text section** (text objects and shape labels): font family, font size, leading, text color, bold, italic, underline, bullets, alignment
- **Shape section**: fill color, stroke color, stroke weight, border style
- **Line section**: stroke color, weight, dash style, start/end arrowhead
- **Image section**: full adjustment sliders (see Image Editing Sidebar below)
- **Table section**: scope selector (cell/row/column), border controls, fill/text colors, bold, add/delete row and column

Right-clicking any object on the stage reveals a context menu with **Bring to front**, **Send to back**, **Duplicate object**, and **Delete object**. For tables, the context menu also includes row/column operations. Right-clicking a slide thumbnail gives **Duplicate slide** and **Delete slide**.

**Reordering slides:** Drag a thumbnail in the thumbnail rail to a new position to reorder slides. A drop-target highlight shows where the slide will land.

#### Speaker Notes

Each slide has a notes area below the stage. Type freeform text to use as speaker prompts during presentation.

![Speaker notes area showing prompt text below the slide stage](/help-assets/screenshots/presentation-speaker-notes.png)

---

### Template Variables

Text boxes support live template variables:

```
{{Financials!B5}}         -- resolves to cell B5 on the Financials sheet
{{KPIs!A1|percent}}       -- with format hint
```

Variables resolve at render time, keeping slides in sync with workbook data. Useful for auto-updating KPI decks and status reports.

---

### Keyboard Shortcuts

| Action | Shortcut |
|---|---|
| Edit text | Click or double-click the text object |
| Edit shape text | Select the shape, press `Enter` |
| Delete selection | `Delete` or `Backspace` |
| Duplicate object | `Ctrl/Cmd + D` |
| Select all | `Ctrl/Cmd + A` |
| Rotate selected 1 degree | `Alt + Left/Right` |
| Rotate selected 15 degrees | `Alt + Shift + Left/Right` |
| Undo | `Ctrl/Cmd + Z` |
| Start presentation | `F5` or **View > Start presentation** |
| Deselect | `Escape` |
| Move selected | Arrow keys |
| Insert title layout | `Cmd + 1` |
| Insert title + body layout | `Cmd + 2` |
| Insert section layout | `Cmd + 3` |
| Insert two-column layout | `Cmd + 4` |
| Insert quote layout | `Cmd + 5` |
| Apply theme 1–8 | `Cmd + Shift + 1` through `Cmd + Shift + 8` |
| Import PowerPoint | `Cmd + Shift + I` |

![Fullscreen present mode showing slide with navigation controls](/help-assets/screenshots/presentation-present-mode.png)

---

### Import and Export

| Action | How |
|---|---|
| Import a PowerPoint file | **File > Import > PowerPoint** |
| Export as PDF | **Slides > Export as PDF (Print)** for highest fidelity, or **Download PDF (.pdf)** for deterministic bytes |
| Export an editable PowerPoint file | **Slides > Export as PowerPoint (.pptx)** |

PPTX import converts slides, text boxes, shapes, and images into editable xApps presentation objects and persists an import-fidelity report. Hosts may optionally inject `XAppsPresentationPptxFidelityRenderer`, which returns exactly one image byte payload or durable workbook reference per slide; xApps persists those images as click-through visual fidelity layers while the editable DrawingML objects remain authoritative. With no renderer, an unavailable renderer, or an invalid result, import either uses the normal portable DrawingML fallback with a truthful report or rejects without changing the deck. xApps itself never invokes PowerPoint, AppleScript, LibreOffice, or a desktop renderer.

The product intentionally opts out of bundling or invoking a renderer for the `>=0.97` target. The measured local print-quality reference provider produced weighted SSIM `0.962303457` across five decks and all 140 audit slides—an improvement over the editable-only `0.846024` baseline, but still below `0.97`. This intentional opt-out is not a `0.97` claim.

Import remains browser-executed so automation cannot bypass the DrawingML fidelity engine; the API, SDK, CLI, MCP, and toolkit return an explicit browser-required rejection after validating package safety. Deterministic PDF and editable PPTX downloads are also available from the sheet menu and public format API.

---

### CLI Commands

```bash
export XAPPS_API_BASE_URL="https://your-xapps-host"
```

#### Presentation import/export -- Validate, report, and export artifacts

```bash
xapps presentation-format-capabilities "Pitch Deck" --json
xapps presentation-import-pptx-fidelity "Pitch Deck" --json
xapps presentation-export-pdf "Pitch Deck" ./pitch.pdf
xapps presentation-export-pptx "Pitch Deck" ./pitch.pptx
```

`presentation-import-pptx` validates malformed, oversized, encrypted, and unsupported input, then returns the browser handoff instead of claiming a false automated import pass.

#### create-presentation -- Create a deck with its default slide

```bash
xapps create-presentation "Quarterly Review"
```

#### presentation-settings / set-presentation-settings -- Read or update deck settings

```bash
xapps presentation-settings "Pitch Deck" --json
xapps set-presentation-settings "Pitch Deck" '{"presentationTheme":"aurora","presentationZoom":125,"presentationSlideWidth":1280,"presentationSlideHeight":720}' --json
xapps set-presentation-theme "Pitch Deck" aurora --json
```

#### Typed generation, templates, AI runs, and object editing

```bash
xapps generate-deck "Pitch Deck" "Quarterly launch plan" --slides 8 --json
xapps presentation-templates "Pitch Deck" --json
xapps preview-presentation-template "Pitch Deck" deck pitch --json
xapps apply-presentation-template "Pitch Deck" deck pitch --json
xapps apply-deck-template "Pitch Deck" pitch --json

xapps presentation-object-edit-state "Pitch Deck" slide-abc --json
xapps edit-presentation-objects "Pitch Deck" slide-abc '{"action":"transform","objectIds":["obj-1"],"transform":{"dx":20}}' --json
xapps undo-presentation-object-edit "Pitch Deck" slide-abc --json
xapps redo-presentation-object-edit "Pitch Deck" slide-abc --json

xapps presentation-ai-runs "Pitch Deck" --json
xapps presentation-ai-run "Pitch Deck" run-1 --json
xapps create-presentation-ai-run "Pitch Deck" '<closed-run-json>' --json
xapps transition-presentation-ai-run "Pitch Deck" run-1 '<closed-transition-json>' --json
```

Template applies and object edits use the current revision automatically unless an explicit guarded request is supplied. AI-run commands manage durable provider lifecycle records; `generate-deck` itself remains deterministic and SDK-backed.

#### slides -- List all slides in a deck

```bash
xapps slides "Pitch Deck"
#   0: slide-abc Title Slide (3 objects)
#   1: slide-def Problem (5 objects)
#   2: slide-ghi Solution (7 objects)
```

#### presentation-slide-state -- Read the guarded deck revision

Read this immediately before an atomic batch or reorder:

```bash
xapps presentation-slide-state "Pitch Deck" --json
# {"ok":true,"revision":4,"count":3,"slides":[...]}
```

#### apply-slides-batch -- Atomically replace or append slides

```bash
xapps apply-slides-batch "Pitch Deck" '{"mode":"replace","slides":[{"id":"slide-new","name":"New deck","objects":[]}],"expectedRevision":4,"requestId":"replace-deck-001"}' --json
```

The full batch is validated before mutation. A stale revision or a request ID reused with a different payload is rejected. Retry the identical request ID and payload safely after a dropped response.

#### reorder-slides -- Atomically reorder the exact slide set

```bash
xapps reorder-slides "Pitch Deck" "slide-ghi,slide-def,slide-abc" \
  --expected-revision 5 \
  --request-id "reorder-deck-001" \
  --json
```

#### duplicate-slide -- Atomically duplicate a slide

```bash
xapps duplicate-slide "Pitch Deck" slide-abc \
  --expected-revision 5 \
  --request-id "duplicate-slide-001" \
  --name "Copy" \
  --json
```

#### add-slide-layout -- Create a slide from a standard layout

Layouts: `title`, `title-body`, `section`, `two-column`, `quote`.

```bash
xapps add-slide-layout "Pitch Deck" two-column --name "Comparison"
# Slide created: slide-xyz123
```

#### add-slide -- Create a slide from raw JSON

```bash
xapps add-slide "Pitch Deck" '{"name":"Custom","bg":"#1e1b4b","objects":[]}'
# Slide created: slide-abc456
```

#### update-slide -- Update slide properties

```bash
xapps update-slide "Pitch Deck" slide-abc456 '{"name":"Updated Title","bg":"#ffffff"}'
# Slide slide-abc456 updated
```

#### slide-notes / set-slide-notes -- Read or update speaker notes

```bash
xapps slide-notes "Pitch Deck" slide-abc --json
xapps set-slide-notes "Pitch Deck" slide-abc "Pause for questions"
```

#### delete-slide -- Delete a slide

```bash
xapps delete-slide "Pitch Deck" slide-abc456
# Slide slide-abc456 deleted
```

#### slide-objects -- List objects on a slide

```bash
xapps slide-objects "Pitch Deck" slide-abc
#   obj-123 text @ (88,118) 820x96
#   obj-456 shape @ (88,88) 132x8
```

#### presentation-shapes -- List available shape types

```bash
xapps presentation-shapes
#   rect    Rectangle
#   rounded Rounded Rectangle
#   circle  Circle
#   diamond Diamond
#   triangle Triangle
#   pill    Pill
#   arrow   Arrow
#   doubleArrow, chevron, hexagon, star, parallelogram, trapezoid,
#   wedgeCallout, leftBrace, punchedTape
```

#### add-text-box -- Add a text box to a slide

```bash
xapps add-text-box "Pitch Deck" slide-abc "Key Findings" --x 80 --y 160 --w 400 --h 60 --size 32 --color "#111827" --align center
# Slide object created: obj-789
```

#### add-shape -- Add a shape to a slide

```bash
xapps add-shape "Pitch Deck" slide-abc circle --x 400 --y 250 --w 100 --h 100 --fill "#2563eb" --text "1" --color "#ffffff" --size 28
# Slide object created: obj-012
```

#### add-image -- Add an image to a slide

```bash
# From URL
xapps add-image "Pitch Deck" slide-abc "https://example.com/photo.jpg" --x 100 --y 150 --w 400 --h 300

# From local file (uploaded)
xapps add-image "Pitch Deck" slide-abc ./chart.png --upload --fit cover
# Slide object created: obj-345
```

#### Typed visual media commands

These guarded commands read the current object revision automatically unless you provide both `--expected-revision` and `--request-id`:

```bash
xapps add-presentation-line "Pitch Deck" slide-abc '{"x":100,"y":180,"w":320,"h":4,"style":{"lineType":"double-arrow","stroke":"#2563eb","strokeWidth":4}}'
xapps add-presentation-table "Pitch Deck" slide-abc '{"x":80,"y":140,"w":560,"h":220,"rows":[[{"text":"Metric"},{"text":"Value"}],[{"text":"ARR"},{"text":"$8.4M"}]]}'
xapps add-presentation-chart "Pitch Deck" slide-abc '{"x":100,"y":130,"w":520,"h":280,"chartKind":"bar","chartData":{"categories":["Q1","Q2"],"series":[{"name":"ARR","values":[6.8,8.4]}]}}'
xapps add-presentation-live-embed "Pitch Deck" slide-abc '{"x":80,"y":150,"w":600,"h":260,"liveData":{"kind":"range","sheet":"Metrics","range":"A1:D12","headerRow":true}}'
xapps edit-presentation-image "Pitch Deck" slide-abc obj-345 '{"style":{"fit":"cover","brightness":110,"contrast":105,"clipShape":"rounded-rect"}}'
```

#### set-slide-background -- Set slide background color

```bash
xapps set-slide-background "Pitch Deck" slide-abc "#0f172a"
# Slide background updated: slide-abc
```

#### add-slide-object -- Create a slide object from raw JSON

```bash
xapps add-slide-object "Pitch Deck" slide-abc '{"type":"text","x":100,"y":100,"w":300,"h":50,"text":"Hello","style":{"fontSize":24}}'
# Slide object created: obj-678
```

#### update-slide-object -- Update a slide object

```bash
xapps update-slide-object "Pitch Deck" slide-abc obj-678 '{"text":"Updated text","style":{"fontSize":28,"color":"#e11d48"}}'
# Slide object obj-678 updated
```

#### delete-slide-object -- Delete a slide object

```bash
xapps delete-slide-object "Pitch Deck" slide-abc obj-678
# Slide object obj-678 deleted
```

---

### API Endpoints

#### List slides

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Pitch%20Deck/slides
```

#### Read transaction state and apply a guarded batch

```bash
curl -H 'X-XApps-File: MyWorkbook.json' \
  $XAPPS_API_BASE_URL/api/sheets/Pitch%20Deck/slides:state

curl -X POST $XAPPS_API_BASE_URL/api/sheets/Pitch%20Deck/slides:batch \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H 'Content-Type: application/json' \
  -d '{"mode":"append","slides":[{"id":"slide-next","name":"Next","objects":[]}],"expectedRevision":4,"requestId":"append-slide-001"}'
```

`replace` and `append` use `slides`; `reorder` uses the exact current `slideIds` set in the desired order. The receipt includes the new `revision`, `requestId`, and `replayed` flag.

The revision and bounded receipt ledger are server-owned. A normal browser/whole-sheet save that changes Presentation state advances the same revision and preserves the server ledger, so a batch created from an older state receives `409` instead of overwriting the browser edit. If transaction persistence fails, the in-memory slides, current slide, revision, and receipts are restored before the error is returned.

#### Create a slide

```bash
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Pitch%20Deck/slides \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"name":"New Slide","bg":"#ffffff","objects":[]}'
```

#### Update a slide

```bash
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Pitch%20Deck/slides/slide-abc \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"bg":"#0f172a"}'
```

#### Delete a slide

```bash
curl -X DELETE -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Pitch%20Deck/slides/slide-abc
```

#### List slide objects

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Pitch%20Deck/slides/slide-abc/objects
```

#### Create a slide object

```bash
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Pitch%20Deck/slides/slide-abc/objects \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"type":"text","x":80,"y":80,"w":400,"h":60,"text":"New heading","style":{"fontSize":36,"fontWeight":800}}'
```

#### Update a slide object

```bash
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Pitch%20Deck/slides/slide-abc/objects/obj-123 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"text":"Changed","style":{"color":"#e11d48"}}'
```

#### Delete a slide object

```bash
curl -X DELETE -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Pitch%20Deck/slides/slide-abc/objects/obj-123
```

---

### Agent / AI Workflow Recipes

The recipes use an existing authorized `MyWorkbook.json` in `local` storage. Replace that file and storage target together for your actual workbook, and set `XAPPS_API_BASE_URL` to its authorized host. Commands that extract structured receipts also require `jq`.

```bash
xapps_scoped() {
  xapps --base-url "${XAPPS_API_BASE_URL:?Set the authorized host URL}" \
    --file 'MyWorkbook.json' --workbook-storage-target local "$@"
}
```

Presentation keeps provider execution, credentials and resumable provider state in the shared Assistant/provider layer. Deterministic composition and durable Presentation AI-run records return through guarded slide/object tools. Stock-provider credentials remain server-managed. Internal critique, prompt improvement and design-direction choices are orchestration steps rather than separate provider lifecycles.

Use an existing `Status` deck. Prepare a typed slide array with stable slide/object IDs and replace illustrative text with evidence-backed content before applying:

```bash
xapps_scoped presentation-slide-state Status --json > status-before.json
PRESENTATION_REVISION=$(jq -er '.revision' status-before.json)
cat > status-slides.json <<'JSON'
[{"id":"status-review-1","name":"Review summary","bg":"#ffffff","objects":[{"id":"status-title-1","type":"text","x":80,"y":70,"w":800,"h":80,"text":"Project review","style":{"fontSize":36,"color":"#0f172a"}},{"id":"status-body-1","type":"text","x":80,"y":180,"w":800,"h":300,"text":"Replace this illustrative text with verified findings and source references.","style":{"fontSize":24,"color":"#334155"}}]}]
JSON
jq -n --argjson revision "$PRESENTATION_REVISION" --slurpfile slides status-slides.json \
  '{mode:"append",slides:$slides[0],expectedRevision:$revision,requestId:"status-review-1"}' \
  > reviewed-status-request.json
```

Review the prepared request for content, source metrics and layout intent. Apply the already authorized change and inspect the resulting saved deck:

```bash
xapps_scoped apply-slides-batch Status "$(cat reviewed-status-request.json)" --json \
  > status-apply-receipt.json
xapps_scoped presentation-slide-state Status --json > status-after.json
jq '.slides[] | select(.id == "status-review-1")' status-after.json
```

`append` preserves existing slides; replacement is a separate destructive intent. Retain the shared Assistant run identity when resuming provider work so a reconnect does not create a second run. Inspect rendered slides when layout/readability is part of the deliverable, and attach actual rendered evidence. A saved JSON receipt does not prove visual quality.

Keep every prepared payload, revision, request ID and receipt until verification completes. After uncertain delivery, retry the identical mutation with its original guard; do not rerun the preparation steps with a fresh revision. On `409`, reread, reconcile and create a new ID only for a newly decided intent. Read commands can run independently; writes against shared state run sequentially or as one atomic batch.

### Troubleshooting

**Text not editable on a slide.**
Click the text object once to select it, then click again or double-click to enter edit mode. For shapes, select first, then press `Enter`.

**Template variables not resolving.**
Verify the syntax is `{{SheetName!CellRef}}` with no extra spaces. The referenced sheet must exist in the workbook and the cell must contain a value.

**Imported PPTX looks different from original.**
PPTX import converts slides to xApps objects, which may not support all PowerPoint features (gradients, 3D effects, animations). Review imported slides and adjust manually.

**Slide thumbnails not updating.**
Thumbnails refresh when the slide content changes. If a thumbnail appears stale, click away from the slide and back to trigger a re-render.

**Image appears stretched or cropped unexpectedly.**
Select the image and check the fit mode in the Image Editing sidebar. Use **contain** to see the full image, **cover** to fill the space, or **fill** to stretch.

**Table columns are too narrow after import.**
Drag the internal guide handles between columns to resize. Use the table inspector for precise width control.

**Speaker notes not visible in presenter mode.**
Speaker notes appear below the stage in the editor. In fullscreen presentation mode, notes are shown on the presenter display if supported by your setup.

---

### Tips & Tricks

- Apply a deck template first, then customize individual slides. It is faster than building from scratch.
- Use the `big-number` slide template for executive dashboards -- pair it with template variables for live data.
- Right-click a slide object to see its `presentationSlides[...]` backing path, useful for debugging API workflows.
- Use table stripe presets for quick professional formatting without manual cell-by-cell coloring.
- The image editing sidebar's **Erase background** action works best on photos with clear subject-background separation.
- Combine the CLI `add-text-box` command with template variables to create self-updating report decks.
- Export as PDF for sharing with stakeholders who do not have access to the workbook.
