## Maps

The **Map** sheet is a geography-first sheet type powered by **MapLibre GL JS**. It supports choropleths, point overlays, public data layers, raster tile overlays, place search, region selection, and workbook-linked map views.

> 🤖 Agent example: create a map sheet called `Launch Regions`, set the geography to `us-states`, add a region layer from `Pipeline!A1:B20`, and switch the basemap to `dark`.

![Map sheet showing world choropleth and city point markers](/help-assets/screenshots/map-sheet.png)

### What Ships Today

- **Basemaps**: Streets, Satellite, Terrain, Dark, Light
- **Starter geography**: World Countries and U.S. States
- **Layer types**: Region layers (choropleth) and point layers (pins / routes)
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

![Map with dark basemap and region labels enabled](/help-assets/screenshots/map-dark-labels.png)

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

- Layer name and type (Region layer / Point layer / Addresses → pins)
- Number of mapped features or pinned points
- Source range reference
- Hide/Show, Up, Down, Remove actions
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
  "source": { "sheet": "Data", "range": "A1:B50" },
  "style": { "palette": "greens" }
}'
```

![U.S. states choropleth with sunset palette and labels](/help-assets/screenshots/map-choropleth.png)

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
| `order` / `sequence` / `seq` | route ordering — enables a connecting line |
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

If an `order` column is present the runtime renders a connecting route line between points in ascending order.

CLI to create:

```bash
xapps add-map-layer "My Map" '{
  "name": "Offices",
  "type": "point",
  "source": { "sheet": "Cities", "range": "A1:F9" },
  "style": { "color": "#0f766e" }
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
GET    /api/sheets/:name/config
PUT    /api/sheets/:name/config
GET    /api/sheets/:name/layers
POST   /api/sheets/:name/layers
GET    /api/sheets/:name/layers/:id
PUT    /api/sheets/:name/layers/:id
DELETE /api/sheets/:name/layers/:id
```

Config fields accepted by `PUT /api/sheets/:name/config`:

- `mapBaseGeography` — geography view key
- `mapBasemap` — basemap style key
- `mapPalette` — default palette name
- `mapLegendVisible` — boolean
- `mapLabelsVisible` — boolean
- `map3DEnabled` — boolean
- `mapViewMode` — `choropleth` or others
- `mapZoom`, `mapPanX`, `mapPanY` — camera numbers
- `mapSelectedRegionIds` — array of feature ID strings
- `mapManualFills` — map of feature ID → hex color

### CLI

```bash
xapps map-config <sheet>
xapps set-map-config <sheet> <json>
xapps map-layers <sheet>
xapps add-map-layer <sheet> <json>
xapps update-map-layer <sheet> <layer-id> <json>
xapps delete-map-layer <sheet> <layer-id>
xapps set-map-view <sheet> <geography>
xapps set-map-basemap <sheet> <style>
xapps add-public-data <sheet> <source-id>
```

### MCP

```text
get_map_config
update_map_config
list_map_layers
create_map_layer
update_map_layer
delete_map_layer
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
- Layer editing is done via JSON / source-range flows; there is no graphical layer-form editor.
- Custom tile provider and terrain source registry is not exposed.
- Time-slider / temporal mapping workflows are not yet implemented.
