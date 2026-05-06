## Maps

The **Map** sheet is a geography-first sheet type powered by **MapLibre GL JS**. It supports choropleths, point overlays, public data layers, raster tile overlays, place search, region selection, and workbook-linked map views.

> 🤖 Agent example: create a map sheet called `Launch Regions`, set the geography to `us-states`, add a region layer from `Pipeline!A1:B20`, and switch the basemap to `dark`.

![Map sheet showing U.S. regions with workbook-linked overlays](/help-assets/screenshots/map-sheet.png)

### What Ships Today

- **Basemaps**: Streets, Satellite, Terrain, Dark, Light
- **Starter geography**: World Countries and U.S. States
- **Layer types**: Region layers and point layers
- **Public data buttons**: World Bank, USGS, REST Countries
- **Live tile overlays**: Railways, Sea Marks, Hiking Trails, Cycling Routes
- **3D toggle**: region extrusions when a numeric region layer is active
- **Embeds**: compact linked map summary cards in other sheets and spreadsheet cells

### Basemaps

Maps currently ship with five built-in basemap styles:

| Style | Source |
|---|---|
| Streets | OpenFreeMap Liberty style |
| Satellite | Esri World Imagery |
| Terrain | OpenTopoMap |
| Dark | CARTO Dark |
| Light | CARTO Light |

Use the **Basemap** dropdown in the map toolbar or the CLI command:

```bash
xapps set-map-basemap <map-sheet> <style>
```

Valid styles:

- `streets`
- `satellite`
- `terrain`
- `dark`
- `light`

### Geography Views

The geography selector on the left panel chooses the dataset and initial camera.

Current built-in views:

| Key | Label | Dataset |
|---|---|---|
| `world-countries` | World | World Countries |
| `africa` | Africa | World Countries |
| `asia` | Asia | World Countries |
| `europe` | Europe | World Countries |
| `middle-east` | Middle East | World Countries |
| `north-america` | North America | World Countries |
| `south-america` | South America | World Countries |
| `oceania` | Oceania | World Countries |
| `us-states` | United States | U.S. States |

CLI:

```bash
xapps set-map-view <map-sheet> europe
```

### Region Layers

Region layers join workbook data to map boundaries for choropleths and categorical fills.

Current expectations:

- a source sheet name
- a source range
- one join column such as `region`, `country`, `state`, `province`, or `name`
- one value column such as `value`, `metric`, `amount`, `count`, or `score`

Optional columns recognized by the current runtime:

| Column | Purpose |
|---|---|
| `label` / `title` | alternate display label |
| `color` / `fill` | explicit hex color override |
| `note` / `notes` / `description` | inspector note text |

Built-in matching includes:

- country aliases such as `USA` -> `United States of America`
- U.S. state abbreviations such as `CA` -> `California`

Current palettes:

- `blues`
- `greens`
- `sunset`
- `ocean`
- `viridis`
- `amber`

### Point Layers

Point layers plot coordinates or geocoded addresses from workbook data.

Current supported source patterns:

- explicit latitude / longitude columns
- address-like columns geocoded through **Nominatim**

Recognized point fields:

| Column | Purpose |
|---|---|
| `lat` / `latitude` | latitude |
| `lon` / `lng` / `longitude` | longitude |
| `address` / `location` / `place` / `city` | address-based geocoding |
| `label` / `name` / `title` | marker label |
| `value` / `metric` / `amount` | popup value |
| `color` / `fill` | per-point color |
| `size` / `radius` | point size |
| `order` / `sequence` / `seq` | route ordering |
| `image` / `thumbnail` / `photo` | popup image |
| `status` / `state` / `stage` | popup status badge |

If a point layer includes an `order` or `sequence` column, the current runtime also renders a route line between points.

### Public Data

The **Public Data** section in the left panel can create layers from built-in remote sources.

Current source ids:

| ID | Label |
|---|---|
| `wb-population` | Population (World Bank) |
| `wb-gdp` | GDP (World Bank) |
| `wb-life-expectancy` | Life Expectancy (World Bank) |
| `wb-co2` | CO2 Emissions (World Bank) |
| `wb-internet` | Internet Users % (World Bank) |
| `usgs-earthquakes` | Earthquakes Last 30 Days (USGS) |
| `usgs-earthquakes-all` | All Earthquakes 4.5+ Last 30 Days |
| `restcountries-area` | Country Area (REST Countries) |
| `worldometer-pop` | World Population Live |

Fetched public data is written into the map sheet’s own cells starting in the lower area of the sheet so the layer can be re-rendered from workbook data later.

CLI:

```bash
xapps add-public-data <map-sheet> wb-gdp
```

### Live Overlays

The **Live Overlays** section toggles raster tile overlays on top of the basemap.

Current overlays:

| Overlay | Category | Source |
|---|---|---|
| Railways | Transport | OpenRailwayMap |
| Sea Marks | Maritime | OpenSeaMap |
| Hiking Trails | Outdoors | Waymarked Trails |
| Cycling Routes | Outdoors | Waymarked Trails |

### Search, Selection, and Views

The map canvas supports place search from the top toolbar and region selection directly on the map. The left panel owns layer setup, saved views, named regions, public datasets, and live overlays.

Use **Save Current View** in the left panel or **View -> Save current view...** to capture the current camera and selected regions as a reusable **Saved View**. Use **Draw region** to create reusable **Named Regions** from a dragged rectangle on the map.

### Saved Views

Use **Save Current View** in the left panel or **View → Save current view...** to capture:

- the current geography
- the current viewport and zoom
- the current selected regions
- the current basemap

Saved views are listed in the left panel and can be:

- applied back onto the map sheet
- deleted
- chosen later from the generic **Embed Sheet View** dialog in other sheets

### Named Regions

Use **New Region Box** in the left panel, the View menu, or the map context menu to drag a rectangle over the current map. The runtime stores:

- the saved bounding box
- the current basemap
- the current camera state
- the current selected regions
- the active overlays

Named regions are listed in the left panel and can be:
Named regions are managed from the **Named Regions** manager and can be:

- searched
- re-applied to the source map sheet
- renamed
- deleted
- chosen later from the generic **Embed Sheet View** dialog in other sheets

### Place Search

The toolbar **Search places...** box geocodes through Nominatim and flies the camera to the chosen place.

### 3D

The toolbar **3D** toggle currently enables `fill-extrusion` rendering when:

- 3D is enabled
- an active region layer is present
- that region layer has numeric values

The camera pitches to show the extrusion view. Turning 3D off returns the pitch to top-down.

### Labels and Legend

- **Labels** can be toggled from the toolbar or the View menu.
- **Legend** is shown for the active region layer when legend visibility is enabled.
- The legend toggle is currently exposed through the View menu and config state.

### Context Menu

Right-clicking the map currently provides:

| Action | Description |
|---|---|
| Fit map to view | Fly back to the default overview |
| Reset pitch & bearing | Return to top-down |
| Clear selection | Clear selected regions |
| Copy coordinates | Copy the right-click location |
| Send location to spreadsheet | Reverse-geocode and append `lat`, `lon`, and `address` to a spreadsheet |

### Embedding

Maps can be inserted into other surfaces, but the current embed implementation is a **linked summary card**, not a fully interactive live map instance.

Current embed behavior:

- **Spreadsheet cells** can insert a compact map preview
- **Canvas / Whiteboard / Presentation / Floor Plan / Docs** can render a linked map summary card
- clicking the summary opens the source map sheet
- the embed picker can target the **whole map**, a **saved view**, or a **named region**

The current embed summary shows:

- region count
- data-bound region count
- point count
- saved view name and selected region count, when embedding a saved view

### Menu Actions

Current menu contributions:

- **Insert**
  - Add region layer
  - Add point layer
- **View**
  - Toggle legend
  - Toggle labels
  - Save current view...
  - Fit map to view
- **Data**
  - Clear manual region fills

### Spreadsheet Formulas

These spatial formulas are available in spreadsheet cells:

| Formula | Description |
|---|---|
| `=GEO_DISTANCE(lat1, lon1, lat2, lon2, "mi")` | distance in miles or kilometers |
| `=GEO_BEARING(lat1, lon1, lat2, lon2)` | initial bearing in degrees |
| `=GEO_MIDPOINT(lat1, lon1, lat2, lon2)` | midpoint as `lat,lon` |
| `=GEO_FORMAT(lat, lon, "dd")` | coordinate formatting |

### REST API

Current map REST routes:

```text
GET    /api/sheets/:name/config
PUT    /api/sheets/:name/config
GET    /api/sheets/:name/layers
POST   /api/sheets/:name/layers
GET    /api/sheets/:name/layers/:id
PUT    /api/sheets/:name/layers/:id
DELETE /api/sheets/:name/layers/:id
```

Current config route fields:

- `mapBaseGeography`
- `mapPalette`
- `mapLegendVisible`
- `mapLabelsVisible`
- `mapRegionSearch`
- `mapViewMode`
- `mapZoom`
- `mapPanX`
- `mapPanY`
- `mapSelectedRegionIds`
- `mapManualFills`
- `mapBasemap`
- `map3DEnabled`

### CLI

Current CLI commands:

```text
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

Current MCP tools:

```text
get_map_config
update_map_config
list_map_layers
create_map_layer
update_map_layer
delete_map_layer
```

### Current Stored State

The current runtime uses these sheet-level fields:

- `mapBaseGeography`
- `mapLayers`
- `mapSelectedRegionIds`
- `mapRegionSearch`
- `mapViewMode`
- `mapLegendVisible`
- `mapLabelsVisible`
- `mapPalette`
- `mapManualFills`
- `mapActiveLayerId`
- `mapBasemap`
- `mapGlCenter`
- `mapGlZoom`
- `mapGlPitch`
- `mapGlBearing`
- `map3DEnabled`
- `mapPOIVisible`
- `mapActiveOverlays`
- `mapZoomLayers`

### Limits of the Current Implementation

The current map sheet is already useful, but a few things are not there yet:

- uploaded GeoJSON / shapefile ingestion UI
- full live interactive embeds in other sheets
- true layer editing forms beyond JSON/config and source-range flows
- richer provider registry for custom tile and terrain sources
- explicit timeline/time-slider mapping workflows

If you need those, treat this help page as the description of what is shipped now, not the full future map vision.
