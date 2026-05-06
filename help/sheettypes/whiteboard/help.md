## Whiteboard

### Infinite space for thinking out loud

Whiteboard sheets give you a boundless spatial canvas for brainstorming, system mapping, workshop exercises, user flows, and meeting synthesis. Unlike page-based sheets, the whiteboard extends infinitely in every direction, letting ideas sprawl naturally.

> 🤖 Agent example: an agent can seed a workshop board with sticky notes, structure a decision area, and prepare a thinking space for the human team to move through live.

![Whiteboard sheet showing sticky notes, freeform spatial thinking, and collaborative grouping](/help-assets/screenshots/whiteboard-sheet.png)

---

### Features

- Sticky notes (plain and checklist)
- Text blocks with full formatting
- Shapes: rectangle, rounded rectangle, circle, diamond, triangle, hexagon, star, frame
- Images (upload, URL, drag-drop, and live-linked references)
- Connectors between objects
- Orthogonal/elbow connectors for cleaner diagrams
- Frames for visual grouping
- Multiple pages with independent pan/zoom
- Layer system with visibility and lock controls
- Board search, type filters, and tag filters
- Object tags for find/filter workflows
- Native mind-map nodes with parent/child relationships
- Mind-map connector styles: elbow or curved
- Align and distribute actions for diagram cleanup
- Process templates (SWOT, BMC, Eisenhower, and more)
- Minimap navigation
- Bulk actions (duplicate, delete, lock, unlock)
- SVG export
- Template variables in text content
- Live image embeds from other sheets
- Object locking
- Zoom 10%--400%

---

### Getting Started

1. Create a new sheet and choose **Whiteboard** from the sheet type menu.
2. Double-click empty space to add a sticky note.
3. Use the toolbar or menu to add shapes, text blocks, and images.
4. Drag objects to arrange them freely on the infinite canvas.
5. Use frames to visually group related objects.
6. Add connectors between objects to show relationships.

---

### Objects in Detail

#### Sticky Notes

Double-click empty canvas space to create a sticky note. Double-click an existing sticky to edit its text. Stickies support:

- Custom background color (`--bg` flag in CLI)
- Text color
- Resize via drag handles
- Rotation
- Checklist mode for task-style notes

#### Text Blocks

Freeform text objects with full styling: font size, color, weight, font family, and text alignment (left, center, right). Text blocks support `{{SheetName!CellRef}}` template variable syntax, which resolves to live workbook cell values at render time.

#### Shapes

Eight shape types, each with configurable fill, stroke, stroke width, border style (solid, dashed, dotted), and optional text labels:

| Shape | Description |
|---|---|
| `rect` | Rectangle |
| `rounded-rect` | Rounded rectangle |
| `circle` | Circle / ellipse |
| `diamond` | Diamond / rhombus |
| `triangle` | Triangle |
| `hexagon` | Hexagon |
| `star` | Star |
| `frame` | Transparent grouping frame |

Double-click a shape to edit the text label inside it. Shape text supports font size, color, and weight customization.

#### Images

Add images by:

- Dragging image files directly onto the canvas
- Using the toolbar upload button
- Pasting a URL
- CLI with `add-wb-image`

Image objects support opacity and fit mode (contain, cover) adjustments.

**Live image references:** Link a whiteboard image to a source image from a Gallery, Design Canvas, Whiteboard, or Presentation sheet. The whiteboard object renders the source image live and updates automatically when the source changes.

1. Add or select an image object.
2. Choose **Reference existing**.
3. Pick a source image from another sheet.
4. Apply the change.

If the source is deleted, the whiteboard shows a broken-source state until you relink or replace it.

#### Connectors

Connect any two objects with a connector line. Use the connector tool to draw relationships between stickies, shapes, and other objects.

For cleaner diagrams, connectors now support both straight and orthogonal/elbow routing. Orthogonal connectors render as segmented paths and stay compatible with SVG export.

#### Mind Nodes

`mind-node` is a native whiteboard object type for mind maps. Unlike a template, mind nodes persist explicit parent/child relationships in the board model.

- Root and child nodes are stored as normal whiteboard rows
- Parent/child relationships are saved in object style metadata
- Mind-map connectors render automatically from those relationships
- Mind-map connectors can be switched between elbow and curved rendering
- Branches can be explicitly assigned to the left or right side of the root
- Branches can be collapsed and expanded without deleting descendants
- CLI and API can create nodes and trigger layout without relying on the browser UI

Use mind nodes when you need a real editable mind map rather than a static whiteboard layout.

#### Search, Filters, and Tags

Large boards need navigation. Whiteboard now supports:

- Live text search across object content and tags
- Filter by object type
- Filter by tag
- Per-object tags for board organization and scripted workflows

Search and filter operate on the current board view and hide non-matching objects without deleting them.

#### Diagramming Utilities

Whiteboard now includes diagram cleanup actions for selected objects:

- Align left / center / right
- Align top / middle / bottom
- Distribute horizontally
- Distribute vertically

These actions are available from the **Arrange** menu and can also be invoked via CLI/API on the same row-backed object model.

#### Frames

Frames are transparent grouping rectangles. Use them to visually section off areas of the whiteboard, like columns in a Kanban or quadrants in a SWOT analysis. Template objects use locked frames as background panels.

---

### Pages

Whiteboard sheets support multiple pages, each with independent pan and zoom state:

- Add, rename, delete, and duplicate pages via tabs at the bottom
- Page overview shows all pages at a glance for quick navigation
- Switch pages to keep different thinking spaces separate within one sheet
- Each page stores its own panX, panY, and zoom level

---

### Layers

Each page has a layer stack for organizing objects:

- Create, rename, reorder, and delete layers via the Layer Manager dialog
- Toggle visibility per layer to hide distracting content
- Lock a layer to prevent accidental edits to its objects
- The default layer is **Content** and cannot be deleted
- Each object lives on one layer; move objects between layers as needed
- Process templates create their own locked layer so template backgrounds can be toggled independently
- Object counts are shown per layer in the manager

---

### Minimap

- The minimap in the lower-right can be collapsed to a compact **Map** pill and reopened from the same spot.
- Click the minimap to jump the viewport.
- Drag the **View** grip inside the minimap viewport for easier navigation.
- Use the corner handles on the minimap viewport to zoom by resizing the visible frame.

---

### Process Templates

Ready-made frameworks available from the **Whiteboard** menu:

| Template | Category | Description |
|---|---|---|
| SWOT Analysis | Strategy | Strengths, Weaknesses, Opportunities, Threats |
| Business Model Canvas | Strategy | 9-section Osterwalder business model |
| User Journey Map | Design | Map user touchpoints across stages |
| Empathy Map | Design | What users think, feel, say, do |
| Lean Canvas | Strategy | Lightweight startup planning canvas |
| RACI Matrix | Governance | Responsible, Accountable, Consulted, Informed |
| Risk Matrix | Risk | Impact vs. probability grid |
| Stakeholder Map | Governance | Map stakeholder influence and interest |
| Eisenhower Matrix | Productivity | Urgent vs. Important prioritization grid |
| Sprint Retrospective | Agile | What went well, what didn't, action items |
| Pros & Cons | Decision | Weigh advantages and disadvantages |
| Kanban Board | Agile | To Do, In Progress, Done columns |

Templates insert within the current visible area. Background panels and labels are locked; stickies are unlocked and editable.

---

### Template Variables

Text blocks and sticky notes support live template variables:

```
{{Sales!B2}}           -- resolves to the value of cell B2 on the Sales sheet
{{Metrics!A1|number}}  -- with format hint
```

Variables update at render time, keeping whiteboard content in sync with workbook data.

---

### Keyboard Shortcuts

| Action | Shortcut |
|---|---|
| Add sticky note | Double-click empty space |
| Edit sticky / text | Double-click the object |
| Edit shape label | Double-click the shape |
| Add mind node | `Shift + M` |
| Add mind-map child | `Tab` on selected mind node |
| Add mind-map sibling | `Shift + Tab` on selected mind node |
| Collapse / expand branch | `Space` on selected mind node |
| Move branch left | `Alt + Left` |
| Move branch right | `Alt + Right` |
| Multi-select | `Shift` + click or `Shift` + drag marquee |
| Select all on page | `Ctrl/Cmd + A` |
| Search board | `Ctrl/Cmd + F` |
| Duplicate selection | `Ctrl/Cmd + D` |
| Delete selection | `Delete` or `Backspace` |
| Undo | `Ctrl/Cmd + Z` |
| Move selected | Arrow keys |
| Deselect | `Escape` |

---

### Bulk Actions

When more than one object is selected, the whiteboard bulk bar supports:

- **Duplicate** with a `+30, +30` offset
- **Delete**
- **Lock / Unlock**
- **Clear selection**

Right-click an object to see its backing storage footer at the bottom of the context menu, showing the exact backing cell range for the object row.

---

### CLI Commands

All CLI commands use the standard prefix. Set `XAPPS_API_BASE_URL` to your server URL.

```bash
export XAPPS_API_BASE_URL="https://your-xapps-host"
```

#### set-whiteboard-view -- Update viewport

```bash
xapps set-whiteboard-view "My Board" --zoom 150 --pan-x 200 --pan-y 100
# Output: Whiteboard view updated
```

#### add-sticky -- Add a sticky note

```bash
xapps add-sticky "My Board" "Review Q3 goals" --x 100 --y 200 --bg "#fff475"
# Output: Whiteboard object created (0, id=wb-m1abc-x9y2z3)
```

#### add-wb-text -- Add a text block

```bash
xapps add-wb-text "My Board" "Project Alpha" --x 300 --y 50 --size 36 --color "#1e3a5f"
# Output: Whiteboard object created (1, id=wb-m1abd-a8b7c6)
```

#### add-wb-shape -- Add a shape

Supported shapes: `rect`, `rounded-rect`, `circle`, `diamond`, `triangle`, `hexagon`, `star`, `frame`.

```bash
xapps add-wb-shape "My Board" hexagon --x 400 --y 300 --w 200 --h 180 --fill "#2196F3" --content "Core Service"
# Output: Whiteboard object created (2, id=wb-m1abe-d5e4f3)
```

#### add-wb-mind-node -- Add a native mind-map node

```bash
xapps add-wb-mind-node "My Board" "Root idea" --x 180 --y 220
xapps add-wb-mind-node "My Board" "Left branch" --parent wb-root-123 --map wb-root-123 --side left
# Output: Whiteboard object created (5, id=wb-m1abf-k2m8n4)
```

#### wb-find -- Search whiteboard objects

```bash
xapps wb-find "My Board" --query architecture --tag api
# Output: matching whiteboard rows
```

#### wb-tag-objects -- Add or replace tags on whiteboard objects

```bash
xapps wb-tag-objects "My Board" 4 7 9 --tags api,system
# Output: tagged 3 objects
```

#### wb-layout-objects -- Align or distribute selected objects

```bash
xapps wb-layout-objects "My Board" align-left 4 7 9
xapps wb-layout-objects "My Board" distribute-v 4 7 9
```

#### wb-layout-mind-map -- Re-layout a native mind map

```bash
xapps wb-layout-mind-map "My Board" 5
# Output: whiteboard mind map laid out
```

#### wb-set-mind-side -- Assign a branch to the left or right

```bash
xapps wb-set-mind-side "My Board" 7 left
# Output: Set mind-map branch side on 7 to left
```

#### wb-set-mind-collapse -- Collapse or expand a branch

```bash
xapps wb-set-mind-collapse "My Board" 7 true
xapps wb-set-mind-collapse "My Board" 7 false
```

#### add-wb-image -- Add an image

```bash
# From URL
xapps add-wb-image "My Board" "https://example.com/diagram.png" --x 500 --y 100 --w 320 --h 240

# From local file (uploaded)
xapps add-wb-image "My Board" ./screenshot.png --upload --x 500 --y 100
# Output: Whiteboard object created (3, id=wb-m1abf-g2h1i0)
```

#### wb-duplicate-objects -- Duplicate objects by row

```bash
xapps wb-duplicate-objects "My Board" --rows 0,1,2
# Output: Duplicated whiteboard objects: 4, 5, 6
```

#### wb-delete-objects -- Delete objects by row

```bash
xapps wb-delete-objects "My Board" --rows 3,4
# Output: Deleted whiteboard objects: 3, 4
```

#### wb-lock-objects / wb-unlock-objects -- Lock or unlock objects

```bash
xapps wb-lock-objects "My Board" --rows 0,1
# Output: Locked whiteboard objects: 0, 1

xapps wb-unlock-objects "My Board" --rows 0,1
# Output: Unlocked whiteboard objects: 0, 1
```

#### wb-export-svg -- Export active page as SVG

```bash
xapps wb-export-svg "My Board" --out board.svg
# Output: Whiteboard SVG written to /path/to/board.svg

# To stdout
xapps wb-export-svg "My Board"
# Output: <svg ...>...</svg>
```

---

### API Endpoints

All endpoints are under `/api/sheets/{sheetName}/`.

#### Get all objects

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/My%20Board/objects
```

#### Create an object

```bash
curl -X POST $XAPPS_API_BASE_URL/api/sheets/My%20Board/objects \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"type":"sticky","x":100,"y":100,"w":180,"h":140,"content":"New idea","style":{"bg":"#fff475"}}'
```

#### Batch operations (duplicate, delete, lock, unlock)

```bash
curl -X POST $XAPPS_API_BASE_URL/api/sheets/My%20Board/objects/batch \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"action":"duplicate","rows":[0,1]}'
```

#### Update viewport settings

```bash
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/My%20Board/settings \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"wbZoom":150,"wbPanX":200,"wbPanY":100}'
```

#### Export SVG

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/My%20Board/svg -o board.svg
```

---

### Agent / AI Workflow Recipes

#### Recipe 1: Generate a SWOT analysis from spreadsheet data

An AI agent can read strengths, weaknesses, opportunities, and threats from a spreadsheet, then populate a whiteboard SWOT layout:

```bash
# 1. Create sticky notes for each strength
xapps add-sticky "SWOT Board" "Strong brand recognition" --x 100 --y 150 --bg "#A5D6A7"
xapps add-sticky "SWOT Board" "Loyal customer base" --x 320 --y 180 --bg "#C8E6C9"

# 2. Add weaknesses
xapps add-sticky "SWOT Board" "High operating costs" --x 650 --y 150 --bg "#EF9A9A"

# 3. Export for review
xapps wb-export-svg "SWOT Board" --out swot-review.svg
```

#### Recipe 2: Build a system architecture diagram

```bash
# Create service boxes
xapps add-wb-shape "Arch Board" rounded-rect --x 100 --y 200 --w 180 --h 100 --fill "#E3F2FD" --content "API Gateway"
xapps add-wb-shape "Arch Board" rounded-rect --x 400 --y 200 --w 180 --h 100 --fill "#E8F5E9" --content "Auth Service"
xapps add-wb-shape "Arch Board" rounded-rect --x 400 --y 400 --w 180 --h 100 --fill "#FFF3E0" --content "Database"

# Add labels
xapps add-wb-text "Arch Board" "System Architecture v2" --x 200 --y 50 --size 32
```

#### Recipe 3: Meeting notes synthesis

After a meeting, an agent can summarize key points onto sticky notes grouped by topic:

```bash
# Group header
xapps add-wb-shape "Retro" frame --x 50 --y 50 --w 600 --h 400

# Key decisions
xapps add-sticky "Retro" "Move launch to Q3" --x 80 --y 120 --bg "#90CAF9"
xapps add-sticky "Retro" "Hire 2 more engineers" --x 300 --y 120 --bg "#90CAF9"

# Action items
xapps add-sticky "Retro" "Draft updated timeline by Friday" --x 80 --y 300 --bg "#A5D6A7"
```

---

### Troubleshooting

**Objects not visible after adding them.**
Check that the target layer is visible. Open the Layer Manager and confirm the layer has the eye icon active. Also verify the objects are within the current viewport by checking the minimap.

**Template inserted too far from the current view.**
Templates insert at the center of the current viewport. If you scrolled far from origin, zoom to fit first, then insert the template.

**Stale data after switching pages.**
Each page has independent pan/zoom state. If objects seem missing, ensure you are on the correct page tab. The page tabs are at the bottom of the whiteboard.

**Cannot edit a locked object.**
Right-click the object and check if it is locked. Use the bulk bar Unlock action or the CLI `wb-unlock-objects` command to unlock it. Template background panels are locked by default.

**SVG export is missing some objects.**
SVG export renders only the active page. Switch to the desired page before exporting. Also verify that hidden layers are not excluding objects you expect to see.

**Image reference shows broken state.**
The source image on the linked sheet was deleted. Select the image object, choose **Reference existing** again, and pick a new source.

**Double-click creates a sticky instead of editing a shape.**
Double-clicking empty space creates a sticky. To edit a shape's label, double-click directly on the shape itself.

---

### Tips & Tricks

- Use the Eisenhower Matrix template for personal task triage during sprint planning.
- Lock template background panels so they do not accidentally move while you rearrange stickies.
- Export SVG snapshots to embed whiteboard diagrams in documents or presentations.
- Use template variables (`{{Sales!B2}}`) in text blocks to create live-updating status boards.
- Assign each major topic its own layer, then toggle visibility to focus on one area at a time.
- Use the minimap corner handles to zoom -- it is faster than scroll-zooming for large jumps.
- Combine frames with connectors to create structured flowcharts with clear visual boundaries.

---

### Grouping Objects

Lock several objects together so they move, resize, and select as one:

```bash
xapps wb-group-objects <sheet> --rows <csv> [--group-id <id>]
xapps wb-ungroup-objects <sheet> --rows <csv>
```

Pass row indexes or stable IDs. `--group-id` lets agents reference an existing group; omitted, a fresh group ID is minted. Ungrouping leaves the underlying objects intact — only the group membership is cleared. Useful when an agent assembles a "card" composed of a frame + sticky + connector and wants the human to drag the whole thing as a unit.

---

### Mind Maps

Whiteboard ships a lightweight mind-map mode where stickies become nodes and connectors auto-route between them:

```bash
xapps wb-link-mind-nodes <sheet> <parent-row-or-id> <child-row-or-id> [--side <left|right>]
xapps wb-set-mind-connector-style <sheet> <row-or-id> <elbow|curved>
```

`wb-link-mind-nodes` adds a parent → child edge; `--side` controls whether the child sits to the left or right of the parent (the default auto-balances). `wb-set-mind-connector-style` swaps a single connector between right-angled `elbow` lines and smooth `curved` ones, useful when you want one critical edge to stand out.

The mind-map flavor reuses the standard whiteboard layer / connector machinery, so you can mix mind-map nodes with other whiteboard objects on the same canvas.
