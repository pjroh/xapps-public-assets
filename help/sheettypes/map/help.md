## Maps

The **Map** sheet puts workbook data on a geographic map. Use it for launch
regions, customer locations, delivery routes or regional comparisons. It
supports colored regions, point markers, ordered routes, public data,
place search and reusable workbook-linked views.

### Make your first data map

1. Prepare a Spreadsheet with headers. For regions, use columns such as
   `country` and `value`; for points, use `name`, `lat` and `lon`.
2. Add a **Map** sheet. Choose **Base geography** for the area to show.
3. In **Layers**, add a Region layer for areas or a Point layer for locations.
   Select the source sheet and include its header row in the range.
4. Check the mapped feature or point count on the layer card. An empty map
   often means the source columns or join values need attention.
5. Choose a basemap and palette that make the data readable. Enable **Labels**
   when names matter, then inspect representative regions or pins.
6. Save a view to return to this camera and selection or embed it elsewhere.

### Choose the right data shape

| You have… | Layer | Minimum useful source |
|---|---|---|
| Values by country or state | Region | `country` or `state`, plus `value` |
| Geographic coordinates | Point | `lat`, `lon`; add `name` for labels |
| Addresses without coordinates | Point with geocoding | Address/location field |
| A sequence of stops | Route | Ordered location data |

Example regional source:

| country | value |
|---|---:|
| United States | 48 |
| United Kingdom | 21 |
| Germany | 16 |

Numeric region values use a log-scaled palette. Read the legend: equal visible
color steps do not imply equal numeric steps.

### Diagnose a blank or incomplete map

- **No background:** basemaps need external tile services. Check the connection
  or another basemap before changing source data.
- **Regions have no color:** verify geography, source range, headers and names.
  Supported aliases include USA, UK and U.S. state abbreviations.
- **An existing range looks empty just after opening the workbook:** open its
  source Spreadsheet tab, return to Map, then use the layer's **Edit source →
  Save changes**. This loads the source and refreshes its column bindings.
- **Pins are misplaced:** check latitude/longitude order, signs and decimal
  degrees. Coordinates avoid address ambiguity.
- **An address is missing:** inspect geocoding progress and failed addresses.
  Add city/country context or use known coordinates.
- **A layer is missing:** check visibility, opacity, zoom bounds and stack order.
- **3D has no height:** use an active numeric Region layer; 3D is region
  extrusion, not a generic buildings view.

Public data and overlays depend on upstream services and their update cadence.
Check source and timestamp before using a view to make a decision.

> 🤖 Agent example: create a map sheet called `Launch Regions`, set the geography to `us-states`, add a region layer from `Pipeline!A1:B20`, and switch the basemap to `dark`.

![Map sheet showing world choropleth and city point markers](/help-assets/screenshots/map-sheet.png)

### Feature reference

- **Basemaps**: Streets, Satellite, Terrain, Dark, Light
- **Starter geography**: World Countries and U.S. States
- **Layer types**: Region layers (choropleth), point layers (pins), and ordered route layers
- **Public data buttons**: World Bank, USGS, REST Countries
- **Live tile overlays**: Railways, Sea Marks, Hiking Trails, Cycling Routes
- **3D toggle**: region extrusions when a numeric region layer is active
- **Place search**: geocoded place search via Photon/Komoot
- **Geocoding**: address-based point layers geocoded automatically via Photon
- **Saved views** and **named regions** for reuse and embedding
- **Embeds**: compact linked map summary cards in other sheets and spreadsheet cells

### Basemaps

Maps ship with five built-in basemap styles:

| Style | Source |
|---|---|
| Streets | OpenFreeMap Liberty style |
| Satellite | Esri World Imagery |
| Terrain | OpenTopoMap |
| Dark | CARTO Dark |
| Light | CARTO Light |

Use the **Basemap** dropdown in the map toolbar or the CLI:

```bash
xapps set-map-basemap <map-sheet> dark
```

Valid styles: `streets`, `satellite`, `terrain`, `dark`, `light`.

Basemaps come from external providers. If tiles are blank or display a provider
message such as “API key required”, choose **Streets** and check the host's
provider configuration. Changing the basemap does not change your layer data.

![Map with Streets basemap and region labels enabled](/help-assets/screenshots/map-labels.png)

### Geography Views

The **Base geography** selector at the top of the left panel chooses the boundary dataset and positions the initial camera.

| Key | Label | Dataset |
|---|---|---|
| `world-countries` | World | World Countries (110m) |
| `africa` | Africa | World Countries |
| `asia` | Asia | World Countries |
| `europe` | Europe | World Countries |
| `middle-east` | Middle East | World Countries |
| `north-america` | North America | World Countries |
| `south-america` | South America | World Countries |
| `oceania` | Oceania | World Countries |
| `us-states` | United States | U.S. States (10m, with AK/HI/PR inset) |

CLI:

```bash
xapps set-map-view <map-sheet> us-states
```

### Layers Panel

The left panel **Layers** section shows all data layers. The section header displays a count badge and quick-add buttons. Each layer card shows:

- Layer name and type (Region / Point / Route)
- Number of mapped features or pinned points
- Source range reference
- Opacity, color, zoom bounds, source editing, Hide/Show, Up, Down, and Remove actions
- Geocoding progress bar and failed-address list (address layers only)

![Layers panel showing point layer and region layer cards](/help-assets/screenshots/map-layers-panel.png)

### Region Layers (Choropleth)

Region layers join workbook data to map boundaries for choropleths and categorical fills.

Required columns:

- one join column: `region`, `country`, `state`, `province`, or `name`
- one value column: `value`, `metric`, `amount`, `count`, or `score`

Optional columns:

| Column | Purpose |
|---|---|
| `label` / `title` | alternate display label |
| `color` / `fill` | explicit hex color override (`#rrggbb`) |
| `note` / `notes` / `description` | inspector note text |

The runtime auto-resolves:

- country aliases (`USA` → `United States of America`, `UK` → `United Kingdom`, etc.)
- U.S. state abbreviations (`CA` → `California`, `TX` → `Texas`, etc.)

**Numeric values** use a log-scaled gradient across the active palette. **Non-numeric values** use categorical colors from the palette.

Available palettes: `blues`, `greens`, `sunset`, `ocean`, `viridis`, `amber`.

CLI to create:

```bash
xapps add-map-layer "My Map" '{
  "name": "GDP by Country",
  "type": "region",
  "source": { "kind": "sheet-range", "sheet": "Data", "range": "A1:B50", "headerRow": true,
    "binding": { "kind": "region", "joinField": "country", "valueField": "value" } },
  "style": { "kind": "region", "palette": "greens" }
}'
```

![U.S. states choropleth with sample population values and labels](/help-assets/screenshots/map-choropleth.png)

![Region layer source dialog selecting State Data and its header range](/help-assets/screenshots/map-source.png)

### Point Layers

Point layers plot coordinates or geocoded addresses from workbook data.

Recognized columns:

| Column | Purpose |
|---|---|
| `lat` / `latitude` | latitude (decimal degrees) |
| `lon` / `lng` / `longitude` | longitude (decimal degrees) |
| `address` / `location` / `place` / `city` | address — geocoded automatically via Photon |
| `label` / `name` / `title` | marker label |
| `value` / `metric` / `amount` | popup value |
| `color` / `fill` | per-point hex color |
| `size` / `radius` | point radius (4–18 px) |
| `order` / `sequence` / `seq` | route ordering for a Route layer |
| `image` / `thumbnail` / `photo` | popup image |
| `status` / `state` / `stage` | status badge with semantic colors |

**Status color mapping** (built in):

| Status value | Color |
|---|---|
| `done`, `complete`, `completed` | Green |
| `in-progress`, `active`, `doing` | Amber |
| `todo`, `pending`, `backlog` | Slate |
| `blocked`, `error`, `failed`, `cancelled` | Red |
| `review`, `in review`, `testing` | Purple |

CLI to create:

```bash
xapps add-map-layer "My Map" '{
  "name": "Offices",
  "type": "point",
  "source": { "kind": "sheet-range", "sheet": "Cities", "range": "A1:F9", "headerRow": true,
    "binding": { "kind": "point", "mode": "coordinates", "latitudeField": "lat", "longitudeField": "lng" } },
  "style": { "kind": "point", "color": "#0f766e" }
}'
```

### Route Layers

Route layers require coordinate or address fields plus an `order`, `sequence`, `step`, or `rank` column. They render a first-class ordered line with optional points.

```bash
xapps add-map-layer "My Map" '{
  "name": "Delivery route",
  "type": "route",
  "source": { "kind": "sheet-range", "sheet": "Stops", "range": "A1:D20", "headerRow": true,
    "binding": { "kind": "route", "mode": "coordinates", "latitudeField": "lat", "longitudeField": "lng", "orderField": "order" } },
  "style": { "kind": "route", "color": "#0f766e", "width": 4 }
}'
```

### Geocoding

When a point layer uses an `address`/`location`/`place`/`city` column instead of `lat`/`lon` columns, the runtime geocodes addresses automatically via **Photon** (Komoot):

- Results are cached in-memory and persisted to the server so subsequent loads are instant.
- The layer card shows a progress bar while geocoding is in progress.
- Failed addresses are listed on the card with **Retry** and **Set lat/lng** actions.
- Failed geocodes can be cleared and retried, or manually overridden with exact coordinates.

### Public Data

The **Data sources** section in the left panel adds layers from built-in remote sources with one click.

| ID | Label | Type |
|---|---|---|
| `wb-population` | Population (World Bank) | Region |
| `wb-gdp` | GDP (World Bank) | Region |
| `wb-life-expectancy` | Life Expectancy (World Bank) | Region |
| `wb-co2` | CO2 Emissions (World Bank) | Region |
| `wb-internet` | Internet Users % (World Bank) | Region |
| `usgs-earthquakes` | Earthquakes Last 30 Days (USGS) | Point |
| `usgs-earthquakes-all` | All Earthquakes 4.5+ Last 30 Days | Point |
| `restcountries-area` | Country Area (REST Countries) | Region |
| `worldometer-pop` | World Population Live | Region |

Fetched public data is written into the map sheet's own cells starting at row 500 so the layer can be re-rendered from workbook data on subsequent loads.

CLI:

```bash
xapps add-public-data <map-sheet> wb-gdp
```

### Live Overlays

The **Live overlays** section toggles raster tile overlays on top of the basemap.

| Overlay | Category | Source |
|---|---|---|
| Railways | Transport | OpenRailwayMap |
| Sea Marks | Maritime | OpenSeaMap |
| Hiking Trails | Outdoors | Waymarked Trails |
| Cycling Routes | Outdoors | Waymarked Trails |

Overlays are toggled via checkboxes and stored in `mapActiveOverlays`. Embed snapshots also render active overlays.

### Place Search

The toolbar **Search places...** box geocodes through Photon (Komoot) with a 350 ms debounce and flies the camera to the chosen place. The dropdown shows up to 5 results.

### 3D

The toolbar **3D** toggle enables `fill-extrusion` rendering when:

- 3D is enabled
- at least one visible region layer with numeric values is active

The tallest value is normalized to ~2,000,000 map units so extrusion height reads consistently at any metric scale. The camera pitches to show the extrusion view. Turning 3D off returns the pitch to top-down.

### Labels and Legend

- **Labels** can be toggled from the toolbar checkbox or the View menu. When on, region names and point labels appear as map symbols with white halos.
- **Legend** is shown for the active region layer when legend visibility is enabled. Numeric layers show a gradient bar with min/max values; categorical layers show colored pills.
- The legend toggle is accessible from the View menu and via `set-map-config`.

### Manual Region Fills

Clicking a region on the map while no data layer is active opens a color picker for that region. Manual fills persist in `mapManualFills` and override any data-layer color. Use **Data → Clear manual region fills** to remove them all.

### Context Menu

Right-clicking the map provides:

| Action | Description |
|---|---|
| Save current view... | Capture camera + selection as a saved view |
| New named region box... | Start drawing a named region rectangle |
| Fit map to view | Fly back to the default overview |
| Reset pitch & bearing | Return to top-down, north-up |
| Clear selection | Clear selected regions |
| Copy coordinates | Copy the right-click lat/lon (6 decimal places) |
| Send location to spreadsheet | Reverse-geocode via Nominatim and append lat, lon, address to a spreadsheet |

### Saved Views

Use **Save Current View** in the left panel header or **View → Save current view...** to capture:

- the current geography
- the current viewport (center, zoom, pitch, bearing)
- the current selected region IDs
- the current basemap
- the current active overlays

Saved views are listed in the **Views & regions** section and can be applied, deleted, or chosen from the **Embed Sheet View** dialog in other sheets.

### Named Regions

Use **Draw region** in the left panel or **View → New named region box...** to drag a rectangle on the map. The stored region captures:

- bounding box coordinates
- basemap, camera state, selected regions, and active overlays at capture time

Named regions can be searched, applied, renamed, deleted, and targeted from the embed dialog.

### Embedding

Maps can be embedded into other surfaces as a **linked summary card** (not a fully interactive instance).

Current embed behaviour:

- **Spreadsheet cells** — compact cell preview (220 × 140)
- **Canvas / Whiteboard / Presentation / Floor Plan / Docs** — linked summary card (420 × 280)
- **Dashboard** — linked map widget
- Double-clicking the embed navigates to the source map sheet and applies the saved view or named region if one was selected

The embed summary shows region count, data-bound region count, and point count. When targeting a saved view it includes the view name and selected region count.

The embed dialog can target:

- the whole map sheet
- a specific saved view
- a specific named region

### Spreadsheet Formulas

These spatial formulas are available in spreadsheet cells:

| Formula | Description |
|---|---|
| `=GEO_DISTANCE(lat1, lon1, lat2, lon2, "mi")` | Distance in miles or kilometers |
| `=GEO_BEARING(lat1, lon1, lat2, lon2)` | Initial bearing in degrees |
| `=GEO_MIDPOINT(lat1, lon1, lat2, lon2)` | Midpoint as `lat,lon` |
| `=GEO_FORMAT(lat, lon, "dd")` | Coordinate formatting |

### Menu Actions

**Insert**
- Add region layer
- Add point layer
- Add route layer

**View**
- Toggle legend
- Toggle labels
- Save current view...
- New named region box...
- Manage named regions...
- Fit map to view

**Data**
- Clear manual region fills

### REST API

```text
GET    /api/sheets/:name/state
GET    /api/sheets/:name/config
PUT    /api/sheets/:name/config
GET    /api/sheets/:name/layers
POST   /api/sheets/:name/layers
POST   /api/sheets/:name/layers/reorder
GET    /api/sheets/:name/layers/:id
PUT    /api/sheets/:name/layers/:id
DELETE /api/sheets/:name/layers/:id
POST   /api/sheets/:name/batch
```

Every mutation body carries `requestId` and `expectedRevision`, plus optional
`expectedFingerprint`. Successful responses return the new canonical state,
revision, fingerprint, receipt, and replay status.

Config fields accepted by `PUT /api/sheets/:name/config`:

- `mapBaseGeography` — geography view key
- `mapBasemap` — basemap style key
- `mapPalette` — default palette name
- `mapLegendVisible` — boolean
- `mapLabelsVisible` — boolean
- `map3DEnabled` — boolean
- `mapViewMode` — `choropleth` or `categorical`
- `mapGlCenter`, `mapGlZoom`, `mapGlPitch`, `mapGlBearing` — canonical MapLibre camera state
- `mapSelectedRegionIds` — array of feature ID strings
- `mapManualFills` — map of feature ID → hex color

### CLI

```bash
xapps map-state <sheet>
xapps map-config <sheet>
xapps set-map-config <sheet> <json>
xapps map-layers <sheet>
xapps map-layer <sheet> <layer-id>
xapps add-map-layer <sheet> <json>
xapps update-map-layer <sheet> <layer-id> <json>
xapps delete-map-layer <sheet> <layer-id>
xapps reorder-map-layers <sheet> <layer-ids-csv>
xapps batch-map <sheet> <operations-json>
xapps set-map-view <sheet> <geography>
xapps set-map-basemap <sheet> <style>
xapps add-public-data <sheet> <source-id>
```

Mutation commands accept `--request-id`, `--expected-revision`, and optional
`--expected-fingerprint`. When omitted, the CLI reads current state and creates
a fresh guarded mutation. `--json` emits one deterministic result object. Automatic fresh IDs are convenient for a new intent, not for replay after an uncertain response.

Choose the authorized saved workbook and its actual storage target before running the examples. Set `XAPPS_API_BASE_URL` to that host. This helper keeps every operation in the same scope (replace the example file and `local` together when needed):

```bash
xapps_scoped() {
  xapps --base-url "${XAPPS_API_BASE_URL:?Set the authorized host URL}" \
    --file 'MyWorkbook.json' --workbook-storage-target local "$@"
}
```

Read `map-state` first and substitute its actual revision below. Keep this exact command and payload for an uncertain-delivery retry:

```bash
xapps_scoped map-state Geography --json
xapps_scoped set-map-config Geography '{"mapLegendVisible":true}' \
  --expected-revision "$MAP_REVISION" --request-id map-legend-review-1 --json
xapps_scoped map-state Geography --json
```

Keep the exact payload, expected revision and request ID after uncertain delivery; retry that same intent. On a revision conflict, reread and reconcile before creating a new intent and request ID.

### MCP / toolkit

```text
map_get_state
map_get_config
map_update_config
map_set_view
map_set_basemap
map_list_layers
map_get_layer
map_create_layer
map_add_public_data
map_update_layer
map_delete_layer
map_reorder_layers
map_batch
```

### Stored State

The runtime uses these sheet-level fields:

| Field | Purpose |
|---|---|
| `mapBaseGeography` | active geography view key |
| `mapBasemap` | active basemap key |
| `mapLayers` | array of layer objects |
| `mapSelectedRegionIds` | currently selected feature IDs |
| `mapManualFills` | manually painted region colors |
| `mapActiveLayerId` | which layer is in focus |
| `mapSavedViews` | array of saved view objects |
| `mapNamedRegions` | array of named region objects |
| `mapPalette` | default palette |
| `mapLegendVisible` | legend on/off |
| `mapLabelsVisible` | labels on/off |
| `map3DEnabled` | 3D extrusion on/off |
| `mapGlCenter` | MapLibre camera center |
| `mapGlZoom` | MapLibre camera zoom |
| `mapGlPitch` | MapLibre camera pitch |
| `mapGlBearing` | MapLibre camera bearing |
| `mapActiveOverlays` | active live overlay IDs |
| `mapRegionSearch` | region search text |
| `mapViewMode` | view mode |
| `mapZoom`, `mapPanX`, `mapPanY` | legacy camera numbers |

### Limits of the Current Implementation

- Uploaded GeoJSON / shapefile ingestion UI is not yet available.
- Embeds in other sheets are linked summary cards, not fully interactive live instances.
- The UI edits layer source, visibility, order, opacity, color, and zoom bounds; advanced fields remain JSON/API-driven.
- Custom tile provider and terrain source registry is not exposed.
- Time-slider / temporal mapping workflows are not yet implemented.
