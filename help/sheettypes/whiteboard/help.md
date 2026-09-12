## Whiteboard

### Infinite space for thinking out loud

Choose **Whiteboard** for ideas that need space: a workshop, mind map, user
flow or decision discussion. Use **Design Canvas** for a graphic with a fixed
page size.

### Run a useful workshop

1. Start with a clear prompt, such as “What should we improve before launch?”
   Use a text object for the prompt.
2. Double-click empty space to add a sticky. Write one idea per sticky so
   people can rearrange them independently.
3. Drag related ideas together. Add frames for themes, or start with a process
   template such as SWOT or Eisenhower.
4. Use shapes for decisions and connectors for relationships. Use an anchored
   connector when the line should follow objects as you move them.
5. Add tags to make outcomes searchable. Use **Fit content** to review the whole
   board, then zoom in to read individual clusters.
6. Export the active page as SVG for a portable visual summary. Keep the
   workbook for continued editing and linked data.

### Pick an object for the job

| You want to… | Start with… |
|---|---|
| Collect independent ideas | Sticky notes |
| Show a process or decision | Shapes and anchored connectors |
| Expand a hierarchy | Native mind nodes |
| Name or explain a section | Text |
| Group a visible area | A frame |
| Place research imagery | Upload or Reference existing |

### Grow a mind map

Add a **Mind node** for the central topic, then create child branches. Native
mind nodes retain parent/child relationships, so layout, collapse and branch
side changes operate on the hierarchy. Collapse detail while discussing the
main branches and expand it when you need the underlying ideas. An indented
outline can create a larger map without adding every node separately.

### Navigate without losing your place

**Fit content** brings the current board into view. The zoom input accepts a
percentage and the minimap helps move between distant clusters. Search and
type/tag filters narrow what you see; clear them before concluding an object
has disappeared. Pages keep separate work areas in the same sheet.

![Whiteboard search narrowing the workshop to roadmap content](/help-assets/screenshots/whiteboard-search.png)

### Connect workshop outcomes to the workbook

Move agreed work into Kanban and durable decisions into Wiki; the board remains
the visual context. Use `{{SheetName!CellRef}}` in text for spreadsheet facts
and **Reference existing** for imagery that should follow its source.

### Feature reference

Whiteboard sheets give you a boundless spatial canvas for brainstorming, system mapping, workshop exercises, user flows, and meeting synthesis. Unlike page-based sheets, the whiteboard extends infinitely in every direction, letting ideas sprawl naturally.

> 🤖 Agent example: an agent can seed a workshop board with sticky notes, structure a decision area, and prepare a thinking space for the human team to move through live.

![Whiteboard sheet showing sticky notes, shapes, mind map, and connectors in a collaborative brainstorm](/help-assets/screenshots/whiteboard-sheet.png)

---

### Features

- Sticky notes (plain and checklist)
- Text blocks with full formatting
- Shapes: rectangle, rounded rectangle, circle, diamond, triangle, hexagon, star, frame
- Lines with 9 style variants (solid, dashed, dotted, arrow, double-arrow, and combinations)
- Images (upload, URL, drag-drop, and live-linked references)
- Connectors between objects with straight and orthogonal/elbow routing
- Frames for visual grouping
- Multiple pages with independent pan/zoom
- Layer system with visibility and lock controls
- Board search, type filters, and tag filters
- Object tags for find/filter workflows
- Native mind-map nodes with parent/child relationships
- Mind node metadata: icon, status, assignee, due date, notes, tags
- Mind map outline import (paste indented text to build a whole map)
- AI mind-map generation and branch expansion through the room Assistant
- Mind-map focus mode and presentation frame creation
- Mind-map connector styles: elbow or curved
- Align, distribute, and z-order actions for diagram cleanup
- Style clipboard (copy/paste style between objects)
- Image filters: brightness, blur, contrast, grayscale, saturation, sepia
- Image flip (horizontal and vertical)
- Border styles: solid, dashed, dotted
- Process templates (SWOT, BMC, Eisenhower, and more)
- Minimap navigation
- Bulk actions (duplicate, delete, lock, unlock, group/ungroup)
- SVG export
- Template variables in text content
- Live image embeds from other sheets
- Object locking
- Web Clipper bookmarklet for saving images from any website
- Zoom 10%--400%

---

### Getting Started

1. Create a new sheet and choose **Whiteboard** from the sheet type menu.
2. Double-click empty space to add a sticky note.
3. Use the toolbar or menu to add shapes, text blocks, and images.
4. Drag objects to arrange them freely on the infinite canvas.
5. Use frames to visually group related objects.
6. Add connectors between objects to show relationships.

![Whiteboard left toolbar showing select, sticky, text, mind, image, shapes, connector, marquee, and pen tool buttons](/help-assets/screenshots/whiteboard-toolbar.png)

The left toolbar buttons (top to bottom): **Undo/Redo**, **Select**, **Sticky**, **Text**, **Mind node**, **Image**, **Shapes flyout** (rect, rounded-rect, circle, diamond, triangle, hexagon, star, frame), **Connector flyout** (straight/orthogonal variants with arrow and line-style options), **Line flyout** (9 line styles), **Marquee select**, **Delete selection**.

---

### Objects in Detail

#### Sticky Notes

Double-click empty canvas space to create a sticky note. Double-click an existing sticky to edit its text. Stickies support:

- Custom background color (`--bg` flag in CLI)
- Text color
- Resize via drag handles
- Rotation
- Checklist mode for task-style notes
- Shadow effect (toggled from the inspector panel)

![Colorful sticky notes and shapes on the brainstorm board](/help-assets/screenshots/whiteboard-sticky-notes.png)

#### Text Blocks

Freeform text objects with full styling: font size, color, weight, font family, and text alignment (left, center, right). Text blocks support `{{SheetName!CellRef}}` template variable syntax, which resolves to live workbook cell values at render time.

#### Shapes

Eight shape types, each with configurable fill, stroke, stroke width, border style (solid, dashed, dotted), and optional text labels.

![Whiteboard filtered to rounded rectangle shapes for High Priority, Medium Priority and Backlog](/help-assets/screenshots/whiteboard-shapes.png)

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

Public automation uses the same stored representation and guarded object revision as the UI:

- `add-wb-image` mirrors a local file or HTTP(S) URL into workbook-scoped `/uploads/` storage before inserting it.
- `wb-list-media` lists stored images, clips, and live references with the current revision.
- `wb-add-image-reference` inserts a typed live source reference.
- `wb-insert-clip` stores source/capture metadata with an uploaded image.
- `wb-remove-media` removes the image object and its persisted media metadata.

Agent tools expose the matching `whiteboard_create_image`, `whiteboard_list_media`, `whiteboard_create_image_reference`, `whiteboard_insert_clip`, and `whiteboard_remove_media` operations. New guarded image writes reject raw external URLs: upload or import them first so reload never depends on an ephemeral browser URL.

Image objects support:

- Opacity control (0--1)
- Fit mode: contain, cover, fill, none, scale-down
- Image filters: brightness, contrast, blur, grayscale, saturation, sepia
- Flip horizontal and flip vertical
- Clickable image links (`imageLink` style property)
- Border style and stroke control (same as shapes)

**Live image references:** Link a whiteboard image to a source image from a Gallery, Design Canvas, Whiteboard, or Presentation sheet. The whiteboard object renders the source image live and updates automatically when the source changes.

1. Add or select an image object.
2. Choose **Reference existing**.
3. Pick a source image from another sheet.
4. Apply the change.

If the source is deleted, the whiteboard shows a broken-source state until you relink or replace it.

#### Lines

The **Line** tool draws freeform line segments that are not semantically bound to other objects. Lines have independent endpoints you can reposition at any time.

Line style options (selectable in the inspector or from the toolbar flyout):

| Style | Description |
|---|---|
| `solid` | Plain solid line |
| `dashed` | Evenly dashed line |
| `dotted` | Dotted line |
| `dot-dash` | Alternating dot and dash |
| `arrow` | Solid line with arrowhead |
| `double-arrow` | Arrowhead on both ends |
| `dashed-arrow` | Dashed line with arrowhead |
| `dotted-arrow` | Dotted line with arrowhead |
| `dot-dash-arrow` | Dot-dash line with arrowhead |

Use the inspector panel to adjust stroke color, weight, and line style after placing a line.

#### Connectors

Connect any two objects with a connector line. Use the connector tool to draw relationships between stickies, shapes, and other objects.

Connectors support:

- **Straight routing** -- direct line between endpoints
- **Orthogonal/elbow routing** -- segmented right-angle paths for cleaner diagrams
- Arrow heads (toggled per connector)
- Line style: solid, dashed, or dotted
- Stroke color and width
- Compatibility with SVG export in both routing modes

A connector anchors to the source object. When the source moves, the connector route updates automatically.

#### Mind Nodes

`mind-node` is a native whiteboard object type for mind maps. Unlike a template, mind nodes persist explicit parent/child relationships in the board model.

- Root and child nodes are stored as normal whiteboard rows
- Parent/child relationships are saved in object style metadata
- Mind-map connectors render automatically from those relationships
- Mind-map connectors can be switched between elbow and curved rendering
- Branches can be explicitly assigned to the left or right side of the root
- Branches can be collapsed and expanded without deleting descendants
- Selected branches can be focused while sibling branches collapse out of the way
- Presentation frames can be generated around the full map and first-level branches
- CLI and API can create nodes and trigger layout without relying on the browser UI
- The Assistant can use MeshAgent room whiteboard tools to create or expand editable mind maps

Use mind nodes when you need a real editable mind map rather than a static whiteboard layout.

**AI-assisted maps.** Choose **AI Mind Map** from the Whiteboard menu or right-click a mind node and choose **Expand with AI**. The request is sent to the room Assistant with the active workbook, sheet, selected node, and branch outline, and asks the Assistant to use the xApps Whiteboard toolkit to create normal editable mind-node objects.

Whiteboard does not invoke an AI provider directly. It has no surface-local model endpoint, provider client, AI CLI command, or AI agent tool. The browser action only hands context to the shared MeshAgent room Assistant; any resulting edits return through the normal guarded Whiteboard tools, revisions, and persistence paths. Provider execution and resumable provider-run state therefore remain owned by the shared Assistant/provider layer.

**Presentation readiness.** Select a mind node and choose **Create Presentation Frames** to add frames around the full map and each first-level branch. These frames provide a ready path for walkthroughs, screenshots, PNG/PDF export, and later slide preparation.

**Mind node metadata.** Each mind node has an optional Details dialog (toolbar button or right-click) where you can set:

- **Icon** -- a single emoji or character shown on the node
- **Status** -- a workflow status (no status, in progress, done, blocked, etc.)
- **Assignee** -- owner name for planning boards
- **Due date** -- a date picker for scheduling
- **Notes** -- a free-text area for context, decisions, or next steps
- **Tags** -- comma-separated tags for search and filtering

**Mind map outline import.** Import an entire mind map from a bulleted or indented text outline. Use two spaces or a tab to create the next level. Select an existing mind node first to append the outline under that branch; otherwise a new root is created automatically.

```
- Launch plan
  - Research users
  - Draft milestones
- Risks
  - Staffing
  - Scope
```

Access the import dialog from the **Whiteboard** menu or the mind-map toolbar.

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

#### Guarded object CRUD and connectors

```bash
xapps wb-create-object "My Board" --object-json '{"type":"sticky","content":"API-created","w":180,"h":120}'
xapps wb-get-object "My Board" wb-stable-id
xapps wb-update-object "My Board" wb-stable-id --updates-json '{"content":"Updated"}'
xapps wb-create-connector "My Board" wb-source-id wb-target-id --page page-1 --routing elbow
xapps wb-update-connector "My Board" wb-connector-id --end wb-new-target-id
xapps wb-delete-object "My Board" wb-stable-id
```

Writes read the current object revision automatically. Supply both `--expected-revision` and `--request-id` only when replaying an exact mutation.

#### Guarded pages, layers, and frames

```bash
xapps wb-pages "My Board"
xapps wb-page-mutate "My Board" create --title "Roadmap"
xapps wb-layer-mutate "My Board" add Planning --page-id page-stable-id
xapps wb-frame-mutate "My Board" create --page-id page-stable-id --layer Planning --title "Q3" --x 80 --y 80 --w 640 --h 360
xapps wb-frame-mutate "My Board" reorder wb-frame-id --index 0
```

Page, layer, and frame writes share one guarded workspace revision. Duplicate/delete and ordering changes commit once, roll back on validation or save failure, and preserve the active page and layer.

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

The command resolves row `5` to its stable node id, reads the current graph revision, and commits the complete layout in one rollback-safe transaction.

#### wb-set-mind-side -- Assign a branch to the left or right

```bash
xapps wb-set-mind-side "My Board" 7 left
# Output: Set mind-map branch side on 7 to left
```

The side change and resulting root layout persist together; a stale concurrent edit is rejected instead of partially overwriting the map.

#### wb-set-mind-collapse -- Collapse or expand a branch

```bash
xapps wb-set-mind-collapse "My Board" 7 true
xapps wb-set-mind-collapse "My Board" 7 false
```

#### Guarded mind-map I/O and metadata

```bash
xapps wb-mind-export "My Board" 7 --format json
xapps wb-mind-import "My Board" --mode merge --document-json '{"version":1,"nodes":[{"key":"root","content":"Launch"}]}' --expected-revision 4 --request-id import-launch-v1
xapps wb-mind-search "My Board" --status blocked --tag launch
xapps wb-mind-set-metadata "My Board" 7 --status blocked --assignee Ada --due-date 2026-08-01 --tags launch,p1 --expected-revision 5 --request-id metadata-launch-v1
```

Exported version-1 documents round-trip through atomic merge or replace imports. Missing ids are derived deterministically from page and node key. Import, metadata, collapse, and connector-style writes share the guarded graph revision and replay contract; invalid cycles, dangling or cross-page parents, stale revisions, and late save failures leave the graph unchanged.

#### Guarded template transactions and data binding

```bash
xapps wb-templates "My Board"
xapps wb-template-preview "My Board" swot --instance-id launch-swot --variables-json '{"title":"Launch SWOT"}' --bindings-json '{"section1":{"sheet":"Metrics","cell":"B2"}}'
xapps wb-template-apply "My Board" swot --instance-id launch-swot --variables-json '{"title":"Launch SWOT"}'
xapps wb-template-replace "My Board" launch-swot proscons --variables-json '{"title":"Ship decision"}'
```

Preview is mutation-free and returns the exact deterministic object plan and fingerprint. Apply/replace use one guarded template revision, persist instance provenance and live `{{Sheet!A1}}` bindings, replay identical request ids, and restore the exact sheet snapshot when validation or saving fails.

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

#### Guarded object state and atomic mutation

`GET objects:state` returns stable objects plus the current revision. `POST objects:mutate` accepts guarded create, update, delete, or an `operations` batch; validation and save failures leave the sheet unchanged.

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/My%20Board/objects:state

curl -X POST $XAPPS_API_BASE_URL/api/sheets/My%20Board/objects:mutate \
  -H 'X-XApps-File: MyWorkbook.json' -H 'Content-Type: application/json' \
  -d '{"action":"create","expectedRevision":0,"requestId":"create-1","object":{"type":"connector","style":{"pageId":"page-1","anchors":{"start":{"kind":"row","row":"source-id"},"end":{"kind":"row","row":"target-id"}}}}}'
```

Connector targets must exist on the connector page. Deleting an anchored object also deletes its dependent connector objects.

#### Guarded Whiteboard templates

`GET whiteboard-templates` discovers templates and variables; `GET whiteboard-templates:state` reads persisted instances and revision; `POST whiteboard-templates:preview` returns a deterministic plan; and `POST whiteboard-templates:apply` atomically applies or replaces it.

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

The recipes use an existing authorized `MyWorkbook.json` in `local` storage. Replace that file and storage target together for your actual workbook, and set `XAPPS_API_BASE_URL` to its authorized host. Commands that extract structured receipts also require `jq`.

```bash
xapps_scoped() {
  xapps --base-url "${XAPPS_API_BASE_URL:?Set the authorized host URL}" \
    --file 'MyWorkbook.json' --workbook-storage-target local "$@"
}
```

The shared Assistant/provider layer owns model work; Whiteboard mutations use the normal deterministic object contract. This example uses an existing `Architecture` Whiteboard and `Evidence` Gallery in the same scoped workbook. It creates two named service boxes and their connector atomically, then retains the exported SVG as a durable Gallery attachment.

#### Prepare and review one stable-ID diagram batch

```bash
xapps_request() {
  curl --fail-with-body --silent --show-error \
    -H 'X-XApps-File: MyWorkbook.json' -H 'X-XApps-Workbook-Storage-Target: local' "$@"
}
xapps_request "$XAPPS_API_BASE_URL/api/sheets/Architecture/objects:state" > architecture-before.json
WHITEBOARD_REVISION=$(jq -er '.revision' architecture-before.json)
cat > architecture-operations.json <<'JSON'
[{"action":"create","object":{"id":"arch-api","type":"rounded-rect","content":"API","x":100,"y":100,"w":220,"h":100,"style":{"fill":"#dbeafe"}}},{"action":"create","object":{"id":"arch-store","type":"rounded-rect","content":"Storage","x":450,"y":100,"w":220,"h":100,"style":{"fill":"#dcfce7"}}},{"action":"create","object":{"id":"arch-api-store","type":"connector","style":{"anchors":{"start":{"kind":"row","row":"arch-api","side":"right"},"end":{"kind":"row","row":"arch-store","side":"left"}},"arrow":true}}}]
JSON
jq -n --argjson revision "$WHITEBOARD_REVISION" --slurpfile ops architecture-operations.json \
  '{action:"batch",expectedRevision:$revision,requestId:"architecture-diagram-1",operations:$ops[0]}' \
  > architecture-request.json
```

Inspect the current objects and prepared request first. The connector anchor field is named `row`, but its value here is the stable object ID accepted by the object contract; the server resolves it within this same atomic batch.

#### Apply and read the actual saved objects

```bash
xapps_request -X POST -H 'Content-Type: application/json' \
  --data-binary @architecture-request.json \
  "$XAPPS_API_BASE_URL/api/sheets/Architecture/objects:mutate" > architecture-receipt.json
jq -e '.ok == true and .requestId == "architecture-diagram-1"' architecture-receipt.json
xapps_scoped wb-get-object Architecture arch-api --json
xapps_scoped wb-get-object Architecture arch-store --json
xapps_scoped wb-get-object Architecture arch-api-store --json
xapps_request "$XAPPS_API_BASE_URL/api/sheets/Architecture/objects:state" > architecture-after.json
xapps_scoped wb-export-svg Architecture --out architecture.svg
xapps_request "$XAPPS_API_BASE_URL/api/sheets/Architecture/objects:state" > architecture-export-state.json
jq -e --slurpfile before architecture-after.json \
  ' .revision == $before[0].revision ' architecture-export-state.json
```

#### Upload the exported bytes and retain the attachment receipt

```bash
xapps_request -X POST -H 'Content-Type: image/svg+xml' -H 'X-XApps-Upload-Name: architecture.svg' \
  --data-binary @architecture.svg "$XAPPS_API_BASE_URL/api/uploads" > architecture-upload.json
ARCHITECTURE_UPLOAD_URL=$(jq -er '.url' architecture-upload.json)
xapps_scoped gallery-settings Evidence --json > architecture-gallery-before.json
GALLERY_REVISION=$(jq -er '.revision' architecture-gallery-before.json)
SOURCE_REVISION=$(jq -er '.revision' architecture-after.json)
xapps_scoped gallery-ingest Evidence "Architecture diagram" --id architecture-svg-1 \
  --source-type upload-ref --source "$ARCHITECTURE_UPLOAD_URL" \
  --desc "SVG exported from MyWorkbook.json / Architecture at object revision $SOURCE_REVISION" \
  --expected-revision "$GALLERY_REVISION" --request-id architecture-attachment-1 --json \
  > architecture-attachment-receipt.json
xapps_scoped gallery item Evidence architecture-svg-1 --json > architecture-attachment-after.json
jq '.item | {id,image,description}' architecture-attachment-after.json
```

If the revision check changes during export, regenerate the export from a fresh snapshot before uploading it; do not repeat the already completed diagram mutation. The upload response and Gallery item are separate receipts: a local export path is not an attachment. The upload step names the object with `X-XApps-Upload-Name`; `upload-ref` ingestion consumes its returned URL and does not accept `--name`. Retain both receipts and the exact mutation request. An uncertain upload is not covered by the object/Gallery request IDs; reconcile its returned durable URL before retrying the attachment step. Inspect the exported/rendered diagram when visual quality is part of the deliverable; the transaction receipts establish saved state only.

Keep every prepared payload, revision, request ID and receipt until verification completes. After uncertain delivery, retry the identical mutation with its original guard; do not rerun the preparation steps with a fresh revision. On `409`, reread, reconcile and create a new ID only for a newly decided intent. Read commands can run independently; writes against shared state run sequentially or as one atomic batch.

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

![Native mind-map nodes with curved connectors showing Product Strategy root, Q3 Features, Q4 Roadmap, Tech Debt, and Team Growth branches](/help-assets/screenshots/whiteboard-mind-map.png)

```bash
xapps wb-link-mind-nodes <sheet> <parent-row-or-id> <child-row-or-id> [--side <left|right>]
xapps wb-set-mind-connector-style <sheet> <row-or-id> <elbow|curved>
```

`wb-link-mind-nodes` atomically moves the complete child subtree, canonicalizes its map id, and lays out the destination root; `--side` controls whether the child sits to the left or right of the parent (the default auto-balances). `wb-set-mind-connector-style` swaps a single connector between right-angled `elbow` lines and smooth `curved` ones, useful when you want one critical edge to stand out.

The mind-map flavor reuses the standard whiteboard layer / connector machinery, so you can mix mind-map nodes with other whiteboard objects on the same canvas.

---

### Web Clipper

The Web Clipper lets you save images from any external website directly into a whiteboard (or Gallery) sheet without leaving the browser.

**Setup:**

1. Open the whiteboard and click the **Web Clipper** button in the toolbar (bookmark icon).
2. A dialog opens with a blue **"Clip to XApps"** bookmarklet button.
3. Drag that button to your browser's bookmarks bar.

**Usage:**

1. Visit any website with images you want to capture.
2. Click **Clip to XApps** in your bookmarks bar.
3. Click any image on the page to select it.
4. Confirm the destination workbook and sheet, then click **Clip**.
5. The image is downloaded and added to your whiteboard at the current viewport position.

The clipper defaults to the last saved workbook and active compatible sheet. It works from any website because the bookmarklet runs in the context of the current tab and posts back to your xApps host.

---

### Inspector Panel

The right sidebar inspector changes contextually based on the selected object type:

| Object type | Inspector tabs |
|---|---|
| Sticky note | Style (color, text color, font size), Transform (rotation) |
| Text block | Text (color, size, bold), Transform (rotation) |
| Shape / mind node | Appearance (fill, border, style, width), Text (label color, size), Transform (rotation) |
| Line | Stroke (color, weight, style/arrow type), Transform (rotation) |
| Connector | Stroke (color, weight, style), Routing (straight/orthogonal), Arrow head toggle |
| Frame | Transform (rotation) |
| Image | Image (replace, flip H/V), Placement (fit mode), Transform (rotation, opacity, corner radius, shadow), Adjustments (brightness, contrast, saturation, blur, grayscale, sepia) |

**Multi-selection inspector.** When two or more objects are selected, the inspector shows a combined panel with:

- Tags (apply/clear across selection)
- Fill and border color for mixed selections
- Border style and width
- Text color
- Align/distribute and z-order dropdowns
- Connect button (when exactly two objects are selected)
- Lock / Unlock buttons
- Paste Style (if the style clipboard has content)

**Style clipboard.** Use **Copy Style** on any single object to store its visual properties. Then select one or more other objects and click **Paste Style** to apply the same fill, border, color, and font settings. Available for stickies, shapes, text blocks, and mind nodes.
