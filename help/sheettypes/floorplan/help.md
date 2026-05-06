## Floor Plan

### Space planning, layout, and interior design

Floor Plan sheets provide a 2D architectural canvas for drawing walls, placing doors and windows, arranging furniture from a built-in library, adding annotations, and exporting to DXF. Everything is drawn to scale with configurable units and snap-to-grid precision.

> 🤖 Agent example: an agent can lay out an initial room plan, place doors and furniture, and leave a scaled arrangement that a human can fine-tune for the real space.

![Floor Plan sheet showing walls, furniture, notes, and a scaled studio layout](/help-assets/screenshots/floorplan-sheet.png)

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
- DXF import and export
- Zoom and pan with rulers
- Coordinate readout
- Multi-select, group/ungroup, duplicate
- Rotation for all objects
- Floor plan templates (Studio, 2-Bedroom, Open Office)

---

### Getting Started

1. Create a new sheet and choose **Floor Plan** from the sheet type menu.
2. Select the **Wall** tool and click to place wall endpoints. Walls are drawn as connected segments.
3. Switch to the **Door** or **Window** tool and click near a wall to place openings.
4. Open the furniture panel and drag presets onto the canvas.
5. Use the **Measure** tool to add dimension annotations.
6. Set your preferred unit (ft or m) and scale from the settings.

---

### Tools

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

Over 100 furniture presets organized into 12 categories:

| Category | Example Items |
|---|---|
| Stairs | Straight Staircase, L-Shape Staircase, Spiral Staircase, Ramp |
| Living Room | 3-Seat Sofa, 2-Seat Sofa, Armchair, Ottoman, Coffee Table, Side Table, TV Stand, Wall TV, Bookshelf, Fireplace, Console Table, Area Rug, Upright Piano |
| Bedroom | King Bed, Queen Bed, Single Bed, Crib, Nightstand, Dresser, Wardrobe, Vanity Desk |
| Kitchen | L Counter, Counter, Refrigerator, Stove/Oven, Kitchen Sink, Kitchen Island, Dishwasher, Microwave, Bar Stool |
| Bathroom | Bathtub, Shower, Toilet, Bathroom Sink, Double Vanity, Towel Rack |
| Office | Desk, Standing Desk, Office Chair, Conference Table, Filing Cabinet, Whiteboard, Printer |
| Dining | Rect Table (6), Round Table (4), Dining Chair, Buffet/Sideboard, Bar Cart, High Chair |
| Lighting | Floor Lamp, Table Lamp, Ceiling Light, Chandelier, Recessed Light, Wall Sconce |
| Electrical | Outlet, Light Switch, Thermostat, Smoke Detector, Ceiling Fan |
| Appliances | Washer, Dryer, Water Heater, HVAC Vent |
| Plants & Outdoor | Potted Plant, Large Planter, Tree, Palm Tree, Bush, Hedge Row, Flower Bed, Lawn Area, Garden Path, Patio, Pergola, Gazebo, Fence, Pool, Hot Tub, BBQ Grill, Outdoor Kitchen, Hammock, Swing Set, and more |
| Storage | Closet Rod, Shelving Unit, Storage Bench, Shoe Cabinet, Coat Rack |

Each furniture preset has an ID, default width and height (in plan units), and an SVG rendering. Drag items from the panel or use the CLI `add-furniture` command with the preset ID.

---

### Units, Scale, and Wall Thickness

| Setting | Description | Default |
|---|---|---|
| Unit | `ft` (feet) or `m` (meters) | ft |
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

---

### DXF Import and Export

#### Import

Import DXF reference plans into a floor plan sheet from the File menu:

- Architectural layers work best
- Use layer visibility to tame noisy source files
- The importer creates matching layers from the DXF file
- Re-import after importer changes if an earlier import looked wrong
- Imported colored walls are auto-converted to polylines

#### Export

Export your floor plan as a DXF file for use in CAD software:

```bash
xapps floorplan-export-dxf "My Plan" --out floorplan.dxf
```

---

### Floor Plan Templates

Three built-in templates provide starting points:

| Template | Description |
|---|---|
| Studio Apartment | Single room with kitchen, bath, and living area |
| One Bedroom | Bedroom, kitchen, living room, bathroom |
| Office Suite | Conference room, desk clusters, reception area |

Templates include walls, doors, windows, and pre-placed furniture.

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
xapps add-floorplan-image "My Plan" ./blueprint.png --upload --x 0 --y 0 --w 30 --h 20 --opacity 0.3
# Object created (8, id=img-yza567)
```

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

---

### API Endpoints

#### Create a floor plan object

```bash
# Add a wall
curl -X POST $XAPPS_API_BASE_URL/api/sheets/My%20Plan/objects \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"kind":"wall","x1":0,"y1":0,"x2":20,"y2":0}'

# Add furniture
curl -X POST $XAPPS_API_BASE_URL/api/sheets/My%20Plan/objects \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"kind":"furniture","id":"sofa-3","name":"3-Seat Sofa","x":5,"y":14,"w":7,"h":3,"rotation":0}'

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

#### List furniture presets

```bash
curl $XAPPS_API_BASE_URL/api/meta/floorplan/furniture
```

---

### Agent / AI Workflow Recipes

#### Recipe 1: Generate an office layout from a requirements list

An agent reads desk count and room requirements from a spreadsheet, then builds the floor plan:

```bash
# Draw outer walls
xapps add-wall "Office" --x1 0 --y1 0 --x2 30 --y2 0
xapps add-wall "Office" --x1 30 --y1 0 --x2 30 --y2 20
xapps add-wall "Office" --x1 30 --y1 20 --x2 0 --y2 20
xapps add-wall "Office" --x1 0 --y1 20 --x2 0 --y2 0

# Add entrance
xapps add-door "Office" --x 15 --y 20 --w 3

# Place desks in a row
for i in 0 1 2 3; do
  xapps add-furniture "Office" desk --x $((3 + i * 7)) --y 8
  xapps add-furniture "Office" office-chair --x $((4 + i * 7)) --y 11
done

# Label the room
xapps add-floorplan-text "Office" "Open Workspace" --x 12 --y 4 --size 2
```

#### Recipe 2: Annotate an imported blueprint

```bash
# After DXF import, add notes to key areas
xapps add-floorplan-note "Office" "Fire Exit" --text "Verify exit width meets code" --x 28 --y 18 --open
xapps add-floorplan-note "Office" "Server Room" --text "Needs dedicated HVAC" --x 25 --y 5

# Add measurement lines for verification
# Export annotated version
xapps floorplan-export-dxf "Office" --out annotated-office.dxf
```

#### Recipe 3: Furniture layout optimization

An agent can try multiple furniture arrangements and export each for comparison:

```bash
# Layout A: Traditional
xapps add-furniture "Living" sofa-3 --x 5 --y 10
xapps add-furniture "Living" coffee-table --x 7 --y 14
xapps add-furniture "Living" tv-stand --x 5 --y 18
xapps floorplan-export-dxf "Living" --out layout-a.dxf

# Clear and try Layout B
xapps add-furniture "Living" sofa-3 --x 3 --y 12 --rotation 90
xapps add-furniture "Living" armchair --x 10 --y 10
```

---

### Troubleshooting

**Door or window not snapping to a wall.**
Doors and windows snap to nearby walls. Place them close to an existing wall segment. If the wall is too far away, the opening will be placed at the click position without wall attachment.

**Furniture appears too large or too small.**
Check the current unit and scale settings. If you switched from feet to meters (or vice versa) after placing objects, existing items keep their original size values. Adjust scale or re-place items as needed.

**DXF import shows too many layers and lines.**
Architectural DXF files can be noisy. Use the layer visibility toggles to hide non-essential layers (hatching, dimensions, annotation layers from the source). The importer creates matching layers from the DXF file.

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
