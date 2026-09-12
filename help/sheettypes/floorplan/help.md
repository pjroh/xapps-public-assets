## Floor Plan

### Space planning, layout, and interior design

Use **Floor Plan** to arrange a space with measured walls, openings, furniture
and annotations. Keep photographs in Gallery, decisions in Wiki and costs in
Spreadsheet alongside the plan.

### Draw a room in the right order

1. Set the measurement unit and scale before drawing so the rulers and
   furniture dimensions make sense for your project.
2. Choose **Walls** and click successive endpoints to trace the room. Add
   internal walls after the outer outline is clear.
3. Choose **Door** or **Window** and place it near its wall. Openings anchor
   to walls; place the wall first.
4. Drag furniture from the library. Select it to move, resize or rotate it,
   checking its actual dimensions rather than visual size alone.
5. Add room labels and **Measure** lines. Use notes for assumptions and questions.
6. Use **Fit** to review the complete plan. Save the workbook, then export DXF
   for geometry interchange or PNG/print output for a visual review.

![Selected office furniture with editing handles in the floor plan](/help-assets/screenshots/floorplan-selection.png)

### Units, scale and zoom are different

| Control | Changes | Example |
|---|---|---|
| Unit | Measurement system, converting plan coordinates | Feet to meters |
| Scale | Pixels per plan unit | How units map onto the drawing |
| Zoom | Your view of the plan | Inspect a door more closely |
| Furniture dimensions | Object size in plan units | Desk width and depth |

Use measurement annotations to confirm geometry. A higher zoom percentage does
not make a room physically larger.

### Bring in an existing drawing

Use DXF import for vector geometry. Review the preview's converted, ignored and
invalid entities, layers and warnings before applying it. Use a reference image
for a visual starting point, then establish dimensions from known measurements.
A photograph is not a measured floor plan.

### Organize alternatives and handoff

Keep structure, furniture and annotations on useful layers. Hide a layer to
simplify the view or lock it to prevent accidental selection. Duplicate furniture
to explore arrangements, then remove discarded alternatives before export.
The workbook keeps the editable model; PNG/PDF is a visual snapshot and DXF
preserves supported drawing geometry.

### Feature reference

Floor Plan sheets provide a 2D architectural canvas for drawing walls, placing doors and windows, arranging furniture from a built-in library, adding annotations, and exporting to DXF. Everything is drawn to scale with configurable units and snap-to-grid precision.

> 🤖 Agent example: an agent can lay out an initial room plan, place doors and furniture, and leave a scaled arrangement that a human can fine-tune for the real space.

![Floor Plan sheet showing walls, furniture, notes, and a scaled office layout](/help-assets/screenshots/floorplan-sheet.png)

---

### Features

- Wall drawing with configurable thickness
- Doors and windows that snap to walls
- 100+ furniture presets across 12 categories
- Measurement/dimension lines
- Text labels and notes (with collapse/expand)
- Reference images with opacity control
- Live image embeds from other sheets
- Units: feet (ft) or meters (m)
- Configurable scale and wall thickness
- Snap-to-grid and snap-to-geometry
- Layer system with visibility and lock toggles
- Atomic DXF preview/import and workbook-scoped DXF export
- Browser-rendered PNG and browser print / Save as PDF
- Zoom and pan with rulers
- Coordinate readout
- Multi-select, group/ungroup, duplicate
- Rotation for all objects
- Canonical starter templates (Studio Apartment, One Bedroom, Office Suite)

---

### Getting Started

![Sample office floor plan with rooms, furniture, labels, doors, and notes](/help-assets/screenshots/floorplan-layout.png)

1. Create a new sheet and choose **Floor Plan** from the sheet type menu.
2. Select the **Wall** tool and click to place wall endpoints. Walls are drawn as connected segments.
3. Switch to the **Door** or **Window** tool and click near a wall to place openings.
4. Open the **FURNITURE LIBRARY** panel on the right and drag presets onto the canvas.
5. Use the **Measure** tool to add dimension annotations.
6. Set your preferred unit (ft or m) and scale from the settings.

---

### Tools

![Floor Plan toolbar showing drawing, opening, annotation, unit and ruler controls](/help-assets/screenshots/floorplan-toolbar.png)

| Tool | Key | Use |
|---|---|---|
| Select | Default | Click to select, drag to move, Shift-click for multi-select |
| Wall | Toolbar | Click to place wall endpoints, creating connected segments |
| Door | Toolbar | Click near a wall to place a door opening |
| Window | Toolbar | Click near a wall to place a window opening |
| Text | Toolbar | Click to place a text label |
| Note | Toolbar | Click to place a collapsible note |
| Measure | Toolbar | Click two points to create a dimension line |
| Line | Toolbar | Draw polylines on the canvas |
| Rectangle | Toolbar | Draw rectangular shapes |
| Circle | Toolbar | Draw circle shapes |

---

### Addressable Geometry and Automation

Walls, room labels, measurements, polylines (including imported lines and rectangles), circles, arcs, ellipses, splines, and block inserts have stable object IDs and support list, get, create, update, delete, duplicate, translate, and atomic batch operations. DXF block definitions remain supporting import data; each visible insert is addressed by its own immutable ID and `blockName`.

```bash
xapps floorplan-objects "My Plan" --kind circle --json
xapps floorplan-create-geometry "My Plan" circle --data '{"cx":10,"cy":8,"radius":3}'
xapps floorplan-translate-object "My Plan" <object-id> --dx 2 --dy -1
xapps floorplan-batch-objects "My Plan" --operations '[{"op":"create","object":{"kind":"wall","x1":0,"y1":0,"x2":12,"y2":0}}]'
```

Mutation commands accept `--request-id`, `--expected-revision`, and `--expected-fingerprint` for exact replay and conflict-safe automation.

Doors and windows use stable wall anchors and must be placed or moved through the opening commands. Measurements and precision settings have matching typed commands:

```bash
xapps add-door "My Plan" --x 5 --y 0 --w 3
xapps floorplan-move-opening "My Plan" <opening-id> --x 8 --y 0
xapps add-measurement "My Plan" --x1 0 --y1 0 --x2 3 --y2 4
xapps clear-measurements "My Plan"
xapps set-floorplan-ruler-scale "My Plan" 2.5
xapps floorplan-convert-coordinates "My Plan" --from-unit ft --to-unit m --values 1,10 --json
```

---

### Walls, Doors, and Windows

#### Walls

Walls are drawn as line segments between two points. Key properties:

- **Wall thickness** -- configurable globally via settings (default 0.4 units)
- Walls connect at endpoints for clean room outlines
- Wall segments snap to grid intersections and nearby geometry

#### Doors

Doors are placed by clicking near a wall. Properties:

- **Width** (w) -- default 3 units
- **Rotation** -- 0, 90, 180, or 270 degrees
- Door swing arc is rendered automatically

#### Windows

Windows work like doors and snap to nearby walls. Properties:

- **Width** (w) -- default 4 units
- **Rotation** -- matches wall orientation

---

### Furniture Library

112 furniture presets organized into 12 categories. The UI, API, SDK, CLI, MCP, and hosted toolkit all read this same canonical catalog:

| Category | Count | Preset IDs (CLI) |
|---|---|---|
| Stairs | 4 | `stair-straight`, `stair-l`, `stair-spiral`, `ramp` |
| Living Room | 13 | `sofa-3`, `sofa-2`, `armchair`, `ottoman`, `coffee-table`, `side-table`, `tv-stand`, `tv-wall`, `bookshelf`, `fireplace`, `console-table`, `rug`, `piano` |
| Bedroom | 8 | `bed-king`, `bed-queen`, `bed-single`, `crib`, `nightstand`, `dresser`, `wardrobe`, `vanity` |
| Kitchen | 9 | `counter-l`, `counter`, `fridge`, `stove`, `sink-k`, `island`, `dishwasher`, `microwave`, `bar-stool` |
| Bathroom | 6 | `bathtub`, `shower`, `toilet`, `sink-b`, `double-vanity`, `towel-rack` |
| Office | 7 | `desk`, `standing-desk`, `office-chair`, `conf-table`, `filing-cabinet`, `whiteboard-w`, `printer` |
| Dining | 6 | `dining-table-rect`, `dining-table-round`, `dining-chair`, `buffet`, `bar-cart`, `high-chair` |
| Lighting | 6 | `floor-lamp`, `table-lamp`, `ceiling-light`, `chandelier`, `recessed`, `wall-sconce` |
| Electrical | 5 | `outlet`, `switch`, `thermostat`, `smoke-det`, `ceiling-fan` |
| Appliances | 4 | `washer`, `dryer`, `water-heater`, `hvac-vent` |
| Plants & Outdoor | 39 | `potted-plant`, `potted-plant-lg`, `tree`, `tree-large`, `palm-tree`, `bush`, `hedge-row`, `flower-bed`, `lawn`, `garden-path`, `patio`, `pergola`, `gazebo`, `fence-section`, `fence-gate`, `pond`, `fountain`, `fire-pit`, `pool`, `hot-tub`, `grill`, `outdoor-kitchen`, `driveway`, `hammock`, `swing-set`, `trampoline`, `shed`, `lounge-chair`, `garden-bench`, and more |
| Storage | 5 | `closet-rod`, `shelving`, `storage-bench`, `shoe-cabinet`, `coat-rack` |

Each furniture preset has an ID, default width and height (in plan units), and an SVG rendering. Drag items from the **FURNITURE LIBRARY** panel on the right, or use the CLI `add-furniture` command with the preset ID.

```bash
xapps floorplan-furniture                              # list all presets
xapps floorplan-furniture --search table --category Office
```

---

### Units, Scale, and Wall Thickness

| Setting | Description | Default |
|---|---|---|
| Unit | `ft` (feet) or `m` (meters); changing it converts plan coordinates | ft |
| Scale | Pixels-per-unit conversion factor | 20 |
| Wall thickness | Width of wall segments in plan units | 0.4 |

Change units and scale via the settings panel or CLI:

```bash
xapps set-floorplan-unit "My Plan" m
xapps set-floorplan-scale "My Plan" 25
xapps set-wall-thickness "My Plan" 0.3
```

Rulers along the top and left edges show measurements in the active unit. A coordinate readout at the cursor shows the current position in plan units as you move across the canvas.

---

### Snap System

Objects snap to nearby geometry for precise placement:

- Wall edges and endpoints
- Grid intersections
- Midpoints of walls and objects
- Nearby geometry edges
- Door and window positions along walls

Snap indicators appear as you drag objects near alignment targets.

---

### Annotations

#### Text Labels

Add text labels for room names, dimensions, or callouts. Text properties:

- Font family, size, weight, style, decoration
- Text color and background color
- Position (x, y), size (w, h), rotation

#### Notes

Collapsible note objects with a title and body text. Notes can be:

- **Attached** to another object by ID (offset from the parent)
- Opened or collapsed for space management
- Styled with custom font, color, and background

Notes attached to objects open immediately when created.

#### Measure Lines

Dimension lines between two points showing the distance in the current unit. Use the Measure tool to click two points and create a measurement annotation.

#### Images

Reference images for blueprints, site photos, or overlays. Images support:

- Opacity control (0--1) for subtle background references
- Rotation
- Upload from file or URL

---

### Layers

Floor Plan supports a per-layer visibility and lock system:

- Create, rename, and delete layers
- Toggle visibility to show/hide groups of objects
- Lock layers to prevent accidental edits
- When importing DXF files, the importer creates matching layers automatically so you can toggle architectural layers on and off
- Useful for separating structural, furniture, electrical, and annotation layers

Layer, stable-id arrange, and viewport operations are available through the API, SDK, CLI, MCP, and hosted toolkit with guarded replay semantics:

```bash
xapps floorplan-layers "My Plan" --json
xapps floorplan-add-layer "My Plan" Furniture --color "#2563eb"
xapps floorplan-update-layer "My Plan" Furniture --rename FF&E --locked false
xapps floorplan-move-to-layer "My Plan" FF&E --ids <id>,<id>
xapps floorplan-arrange "My Plan" group --ids <id>,<id>
xapps floorplan-arrange "My Plan" translate --ids <id>,<id> --dx 2 --dy -1
xapps floorplan-delete-layer "My Plan" FF&E --destination Default
xapps set-floorplan-viewport "My Plan" --scale 0.08 --center-x 10 --center-y 6
```

Viewport scale and center are durable plan state. The cursor coordinate readout is session-local derived state.

---

### DXF Import and Export

#### Import

Choose **File → Import DXF…** to upload the source and request a server-side preview. The preview reports converted, ignored, and invalid entities and layers plus the exact replace diff; Cancel is read-only. Apply binds the exact DXF text to the preview identity, current revision, and fingerprint, then saves atomically and reloads the persisted plan. Invalid supported entities and sources with no convertible content are blocked before mutation.

The browser flow uses explicit **Replace** semantics. Automation can choose `replace` or `merge`: replace clears every object collection, imported block definition, and current layer before applying the converted source; merge preserves existing objects, layers, block definitions, and viewport while appending converted content. Apply supports request replay, revision/fingerprint conflict detection, and persistence rollback.

DXF `LINE`, `LWPOLYLINE`, `POLYLINE`, `SOLID`, and `3DFACE` entities become editable Floor Plan polylines. Import does not infer semantic walls from layer names or colors. Arcs, circles, ellipses, splines, inserts, text, dimensions, blocks, and layers use their matching supported Floor Plan forms; unsupported/non-printing content is reported as ignored instead of silently dropped.

```bash
xapps floorplan-preview-dxf "My Plan" source.dxf --mode replace --json
xapps floorplan-apply-dxf "My Plan" source.dxf --mode replace --preview-id <preview-id> --json
```

#### Export

DXF export is a workbook-scoped server artifact with `application/dxf`, a deterministic attachment filename, and API/SDK/CLI/MCP/toolkit parity:

```bash
xapps floorplan-export-dxf "My Plan" --out floorplan.dxf
```

PNG and PDF have an explicit browser-only boundary. **Export PNG…** renders the current SVG in the browser and sends the generated PNG through the workbook download path. **Print / Save as PDF…** opens an uploaded print HTML view and invokes the browser print dialog; the browser's **Save as PDF** option produces the PDF. The server, SDK, CLI, MCP, and toolkit do not advertise or return generated PNG/PDF bytes.

---

### Floor Plan Templates

Three built-in templates provide starting points:

| Template | Description |
|---|---|
| Studio Apartment | Single room with kitchen, bath, and living area |
| One Bedroom | Bedroom, kitchen, living room, bathroom |
| Office Suite | Conference room, desk clusters, reception area |

Templates include walls, doors, windows, pre-placed furniture, and a default viewport. Choosing one opens a deterministic replace preview before anything changes. Cancel is read-only; Apply uses the preview token and atomically clears every existing object collection, imported block definition, and custom layer before saving the canonical template. Automation can instead choose `merge`, which preserves all existing collections, layers, block definitions, and viewport while appending template walls, openings, and furniture.

```bash
xapps floorplan-templates "My Plan" --json
xapps floorplan-preview-template "My Plan" studio --mode replace --json
xapps floorplan-apply-template "My Plan" studio --mode replace --approval-token <token-from-preview>
```

The same list/get/preview/apply contract is available through the API, SDK, MCP, and hosted toolkit. Apply also accepts the standard request-id, revision, and fingerprint guards for safe replay, conflict detection, and rollback.

---

### Keyboard Shortcuts

| Action | Shortcut |
|---|---|
| Select tool | Click toolbar or press `Escape` to return to select |
| Multi-select | `Shift` + click |
| Duplicate selected | `Ctrl/Cmd + D` |
| Delete selected | `Delete` or `Backspace` |
| Undo | `Ctrl/Cmd + Z` |
| Pan canvas | Middle mouse button drag |
| Zoom | Scroll wheel or zoom input |

Toolbar controls, catalog items, canvas objects, object-property dialogs, and Layer Manager are keyboard reachable. Dialogs focus their first control, `Escape` closes them, and focus returns to the stable-id object or opener. Unavailable live embeds are announced as status messages. At widths up to 768px, the furniture catalog becomes a usable bottom strip and the toolbar scrolls horizontally instead of clipping controls.

---

### CLI Commands

```bash
export XAPPS_API_BASE_URL="https://your-xapps-host"
```

#### floorplan-furniture -- List all furniture presets

```bash
xapps floorplan-furniture
#   sofa-3    Living Room   3-Seat Sofa     7x3
#   sofa-2    Living Room   2-Seat Sofa     5x3
#   armchair  Living Room   Armchair        3x3
#   ...
```

#### add-wall -- Add a wall segment

```bash
xapps add-wall "My Plan" --x1 0 --y1 0 --x2 20 --y2 0
# Object created (0, id=wall-abc123)
```

#### add-door -- Add a door

```bash
xapps add-door "My Plan" --x 10 --y 0 --w 3 --rotation 0
# Object created (1, id=door-def456)
```

#### add-window -- Add a window

```bash
xapps add-window "My Plan" --x 5 --y 0 --w 4 --rotation 0
# Object created (2, id=window-ghi789)
```

#### add-furniture -- Place a furniture preset

```bash
xapps add-furniture "My Plan" bed-queen --x 12 --y 8 --rotation 90
# Object created (3, id=furn-jkl012)

xapps add-furniture "My Plan" sofa-3 --x 5 --y 14 --rotation 0
# Object created (4, id=furn-mno345)
```

#### add-floorplan-text -- Add a text label

```bash
xapps add-floorplan-text "My Plan" "Master Bedroom" --x 14 --y 12 --size 1.8 --color "#1f2937"
# Object created (5, id=text-pqr678)
```

#### add-floorplan-note -- Add a note

```bash
xapps add-floorplan-note "My Plan" "Electrical" --text "Add outlet near desk" --x 8 --y 10 --open
# Object created (6, id=note-stu901)

# Attach to an object
xapps add-floorplan-note "My Plan" "Measurement" --text "Verify wall length" --attached-id wall-abc123
# Object created (7, id=note-vwx234)
```

#### add-floorplan-image -- Add a reference image

```bash
# Local and remote inputs are materialized into the active workbook upload namespace.
xapps add-floorplan-image "My Plan" ./blueprint.png --upload --x 0 --y 0 --w 30 --h 20 --opacity 0.3
# Object created (8, id=img-yza567)
```

#### Typed annotations and sibling-sheet embeds

```bash
xapps floorplan-annotations "My Plan" --json
xapps floorplan-create-annotation "My Plan" label --data '{"x":12,"y":8,"name":"Office"}'

xapps floorplan-live-embed-sources "My Plan" --json
xapps floorplan-add-live-embed "My Plan" sheet-data --mode snapshot --range A1:D20 --x 4 --y 4 --w 18 --h 12
xapps floorplan-refresh-live-embed "My Plan" embed-abc123
xapps floorplan-open-live-embed "My Plan" embed-abc123 --json
```

Annotation and embed mutations use the same request-id, revision, and fingerprint guards as other Floor Plan mutations. Reference images must already exist under the active workbook's `/uploads/workbooks/<creationNonce>/images/` namespace. Embed discovery returns supported sibling sheets only; refresh reports `available`, `empty`, or `unavailable` while retaining the last typed snapshot.

#### set-floorplan-unit -- Set measurement units

```bash
xapps set-floorplan-unit "My Plan" m
# Floorplan unit set: m
```

#### set-floorplan-scale -- Set the view scale

```bash
xapps set-floorplan-scale "My Plan" 25
# Floorplan scale updated
```

#### set-wall-thickness -- Set wall thickness

```bash
xapps set-wall-thickness "My Plan" 0.3
# Wall thickness updated
```

#### floorplan-export-dxf -- Export as DXF

```bash
xapps floorplan-export-dxf "My Plan" --out office.dxf
# Floorplan DXF written to /path/to/office.dxf

# To stdout
xapps floorplan-export-dxf "My Plan"
# Output: (DXF text)
```

#### floorplan-preview-dxf / floorplan-apply-dxf -- Preview and atomically import DXF

```bash
xapps floorplan-preview-dxf "My Plan" office.dxf --mode replace --json
# Inspect previewId, converted/ignored/invalid counts, layers, diff, and warnings.

xapps floorplan-apply-dxf "My Plan" office.dxf --mode replace --preview-id <preview-id> --json
# Optional exact replay/conflict controls:
# --request-id <id> --expected-revision <n> --expected-fingerprint <sha256>
```

Apply must receive the same file bytes, source filename, mode, and current preview identity. Use `--mode merge` in both commands to preserve existing plan content.

---

### API Endpoints

#### Create a floor plan object

```bash
# Add a wall
curl -X POST $XAPPS_API_BASE_URL/api/sheets/My%20Plan/objects \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"kind":"wall","x1":0,"y1":0,"x2":20,"y2":0}'

# Add furniture (read /state first and use its revision/fingerprint)
curl -X POST $XAPPS_API_BASE_URL/api/sheets/My%20Plan/furniture/placements \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"requestId":"place-sofa-1","expectedRevision":0,"presetId":"sofa-3","x":5,"y":14,"rotation":0}'

# Add a door
curl -X POST $XAPPS_API_BASE_URL/api/sheets/My%20Plan/objects \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"kind":"door","x":10,"y":0,"w":3,"rotation":0}'
```

#### Update floor plan settings

```bash
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/My%20Plan/settings \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"fpUnit":"m","fpScale":25,"fpWallThickness":0.3}'
```

#### Export DXF

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/My%20Plan/dxf -o floorplan.dxf
```

DXF import uses `POST /api/sheets/{name}/dxf/import/preview` followed by `POST /api/sheets/{name}/dxf/import/apply`. Both carry the active `X-XApps-File` workbook scope; apply adds `requestId`, `expectedRevision`, `expectedFingerprint`, and the exact `previewId`, `dxf`, `sourceName`, and `mode` from preview.

#### List furniture presets

```bash
curl $XAPPS_API_BASE_URL/api/meta/floorplan/furniture

# Sheet-scoped search/category/recent ordering
curl "$XAPPS_API_BASE_URL/api/sheets/My%20Plan/furniture/catalog?search=table&category=Office"
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

Floor Plan has no surface-local provider client. Any generated design uses shared provider governance and returns through deterministic guarded spatial contracts.

Use the existing `Office` Floor Plan sheet. Read its canonical `/state` to confirm units before authoring; the example boundary measures 30 by 20 in that current unit system. Changing a unit label does not resize existing objects. Prepare and review this entire batch before applying it:

```bash
curl --fail-with-body --silent --show-error \
  -H 'X-XApps-File: MyWorkbook.json' -H 'X-XApps-Workbook-Storage-Target: local' \
  "$XAPPS_API_BASE_URL/api/sheets/Office/state" > office-before.json
FLOORPLAN_REVISION=$(jq -er '.revision' office-before.json)
FLOORPLAN_FINGERPRINT=$(jq -er '.fingerprint' office-before.json)
jq '.state.settings' office-before.json
cat > office-boundary.json <<'JSON'
[{"op":"create","object":{"id":"office-north","kind":"wall","x1":0,"y1":0,"x2":30,"y2":0}},{"op":"create","object":{"id":"office-east","kind":"wall","x1":30,"y1":0,"x2":30,"y2":20}},{"op":"create","object":{"id":"office-south","kind":"wall","x1":30,"y1":20,"x2":0,"y2":20}},{"op":"create","object":{"id":"office-west","kind":"wall","x1":0,"y1":20,"x2":0,"y2":0}}]
JSON
```

After checking the actual settings and intended geometry, apply the authorized layout once:

```bash
xapps_scoped floorplan-batch-objects Office --operations "$(cat office-boundary.json)" \
  --expected-revision "$FLOORPLAN_REVISION" --expected-fingerprint "$FLOORPLAN_FINGERPRINT" \
  --request-id office-boundary-1 --json > office-boundary-receipt.json
xapps_scoped floorplan-objects Office --json
xapps_scoped floorplan-object Office office-north --json
xapps_scoped floorplan-export-dxf Office --out office-boundary.dxf
```

Use the returned stable object IDs for later revisions. Additional furniture, openings or annotations are distinct intents: read fresh state and invoke their advertised guarded domain command, or include supported typed objects in a reviewed batch. Do not append an unguarded placement loop. Compare alternatives in separately named sheets and retain the original geometry; an add command never clears the previous arrangement.

Keep every prepared payload, revision, request ID and receipt until verification completes. After uncertain delivery, retry the identical mutation with its original guard; do not rerun the preparation steps with a fresh revision. On `409`, reread, reconcile and create a new ID only for a newly decided intent. Read commands can run independently; writes against shared state run sequentially or as one atomic batch.

### Troubleshooting

**Door or window not snapping to a wall.**
Doors and windows snap to nearby walls. Place them close to an existing wall segment. If the wall is too far away, the opening will be placed at the click position without wall attachment.

**Furniture appears too large or too small.**
Check the current unit and scale settings. If you switched from feet to meters (or vice versa) after placing objects, existing items keep their original size values. Adjust scale or re-place items as needed.

**DXF import shows too many layers and lines.**
Architectural DXF files can be noisy. Inspect the preview's ignored/invalid counts and warnings before Apply, then use layer visibility to hide non-essential imported layers. Imported CAD lines intentionally remain thin editable polylines rather than becoming semantic walls.

**Cannot select or move an object.**
The object may be on a locked layer. Open the layer manager and unlock the relevant layer. Also check that you are using the Select tool (not Wall or another drawing tool).

**Wall segments do not connect cleanly.**
Ensure wall endpoints meet precisely. Use snap-to-grid to align endpoints. Drawing walls as connected segments (click-click-click) produces cleaner joins than separate disconnected segments.

**Rulers show wrong units.**
Verify the unit setting with `set-floorplan-unit`. Rulers and the coordinate readout both use the active unit.

**Zoom is too far in or out after import.**
Reset zoom via the zoom input in the toolbar. Enter a percentage (e.g., 100%) or use the scroll wheel to adjust.

---

### Tips & Tricks

- Use the opacity setting on reference images to trace over blueprints or site photos.
- Place electrical fixtures (outlets, switches, smoke detectors) on a dedicated "Electrical" layer so they can be toggled on and off independently.
- Use notes attached to furniture items to record material specifications, costs, or vendor info.
- Export DXF after each major revision to maintain a CAD-compatible history.
- The coordinate readout helps verify exact placement when precision matters more than visual alignment.
- Use the outdoor furniture category for landscape planning: pools, patios, pergolas, fire pits, and garden paths are all available.
- Middle mouse button panning is the fastest way to navigate large floor plans.
