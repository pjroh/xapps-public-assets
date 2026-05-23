## Presentation

### Build slide decks inside the workbook

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

Shapes support fill color, stroke color, stroke width, border style (solid, dashed, dotted), opacity, and optional text labels. Select a shape and press `Enter` or click it again to edit the label text. In the inspector panel, use the **Rotation** field (-360 to 360 degrees) to rotate any shape.

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
| Export as PDF | **Slides > Export as PDF (Print)** |

PPTX import converts slides, text boxes, shapes, and images into editable xApps presentation objects.

---

### CLI Commands

```bash
export XAPPS_API_BASE_URL="https://your-xapps-host"
```

#### slides -- List all slides in a deck

```bash
xapps slides "Pitch Deck"
#   0: slide-abc Title Slide (3 objects)
#   1: slide-def Problem (5 objects)
#   2: slide-ghi Solution (7 objects)
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

#### Recipe 1: Auto-generate a status report deck

An AI agent can read project data from a spreadsheet and build a complete status deck:

```bash
# Create slides from layout templates
xapps add-slide-layout "Status" title --name "Q2 Update"
xapps add-slide-layout "Status" title-body --name "Milestones"

# List slides to get IDs
xapps slides "Status"

# Add KPI text boxes with template variables
xapps add-text-box "Status" slide-abc "Revenue: {{Metrics!B2}}" --x 100 --y 200 --size 44 --color "#0f172a"
xapps add-text-box "Status" slide-abc "Growth: {{Metrics!B3}}" --x 400 --y 200 --size 44 --color "#16a34a"
```

#### Recipe 2: Build a product comparison deck

```bash
# Create comparison slides
xapps add-slide-layout "Compare" two-column --name "Feature Comparison"
xapps slides "Compare"

# Add content to each column
xapps add-text-box "Compare" slide-xyz "Our Product" --x 80 --y 170 --w 400 --h 40 --size 28 --align center
xapps add-text-box "Compare" slide-xyz "Competitor" --x 520 --y 170 --w 400 --h 40 --size 28 --align center

# Add shapes for visual elements
xapps add-shape "Compare" slide-xyz circle --x 250 --y 300 --w 60 --h 60 --fill "#16a34a" --text "A+" --color "#fff"
```

#### Recipe 3: Import and annotate a presentation

```bash
# After PPTX import, list slides and add annotations
xapps slides "Imported Deck"

# Add review comments as text boxes
xapps add-text-box "Imported Deck" slide-abc "REVIEW: Update this metric" --x 600 --y 400 --w 300 --h 40 --size 16 --color "#e11d48"

# Set background on specific slides
xapps set-slide-background "Imported Deck" slide-def "#f8fafc"
```

---

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
