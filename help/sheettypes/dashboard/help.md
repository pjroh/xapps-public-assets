## Dashboard

### Overview

Dashboard sheets turn workbook data into styled widget surfaces for executive summaries, KPI snapshots, launch status boards, revenue tracking, and at-a-glance reporting. Widgets pull live data from other sheets in the workbook and render it as cards, charts, tables, text blocks, gauges, treemaps, and progress rings. Dashboards support full surface styling, two layout modes, drag-to-move, drag-to-resize, and a 12-24 column grid system.

> 🤖 Agent example: an agent can read source metrics from spreadsheets, create KPI and gauge widgets, and leave a polished executive readout for a human to refine instead of starting from an empty dashboard.

![Dashboard sheet showing KPI, gauge, treemap, and narrative widgets driven by workbook data](/help-assets/screenshots/dashboard-sheet.png)

### Features

- Nine widget types: KPI Card, Bar Chart, Line Chart, Donut/Pie Chart, Progress Ring, Data Table, Text Block, Treemap, Gauge
- Live data binding from spreadsheet cell ranges
- Template variables in text widgets (e.g., `{{SheetName!A1}}`)
- 12-column grid layout (configurable 8-24 columns)
- Freeform grid and packed/dense layout modes
- Surface styling: background color, grid line color, column density, row height
- Widget styling: accent color, background color, border color
- Widget sizing in grid units (width x height)
- Drag-to-move widgets by their header
- Drag-to-resize widgets via corner handle
- Pack Widgets to compress layout automatically
- Auto-placement of new widgets in open grid slots
- Dark and light surface themes with automatic contrast adaptation
- Inline markdown rendering in text widgets

### Getting Started

1. Create a new dashboard sheet from the **+ Add Sheet** menu.
2. Click **+ Add Widget** in the toolbar.
3. Select a widget type (e.g., KPI Card).
4. Configure the title, source sheet, and data range.
5. Adjust appearance (accent, background, border colors) and size.
6. Click **Add Widget**. The widget appears in the grid.
7. Drag the widget header to reposition, or drag the corner handle to resize.
8. Click **Surface** to customize the board background, grid lines, and layout mode.

### Widget Types

#### KPI Card

A single executive metric with optional prefix, suffix, and trend indicator.

- **Data Range**: A single cell (e.g., `B2`) from the source sheet provides the headline number.
- **Prefix**: Text before the value (e.g., `$`).
- **Suffix**: Text after the value (e.g., `%`, `M`).
- **Trend**: Freeform trend text (e.g., `+12%`, `-3.2pp`).

Example: A KPI card titled "Monthly Revenue" reading cell B12 from the "Financials" sheet, with prefix `$` and suffix `M`, showing `$4.2M` with trend `+8%`.

#### Bar Chart

Side-by-side category comparison using labeled vertical bars.

- **Labels Range**: Cell range for category names (e.g., `A2:A10`).
- **Values Range**: Cell range for numeric values (e.g., `B2:B10`).
- Bars are colored using the widget's accent color with automatic palette variation.

#### Line Chart

Track movement over time with a connected line and data points.

- **Labels Range**: Cell range for X-axis labels (e.g., `A2:A12` for months).
- **Values Range**: Cell range for Y-axis values (e.g., `B2:B12`).
- Line color uses the widget's accent color.

#### Donut / Pie Chart

Show share-of-total breakdowns as proportional arc segments.

- **Labels Range**: Cell range for segment names.
- **Values Range**: Cell range for segment values.
- Colors cycle through a built-in palette.

#### Progress Ring

Visualize completion toward a goal as a circular arc.

- **Data Range**: A single cell providing the current value.
- **Max Value**: The goal value (default: 100).
- The ring fills proportionally (value / max) using the accent color.

#### Data Table

Pull structured rows from a spreadsheet range and display as a compact table.

- **Data Range**: A rectangular range (e.g., `A1:D20`). The first row becomes headers.
- Rows are limited to 50 by default (configurable via `maxRows` in config).

#### Text Block

Narrative notes, commentary, calls to action, and analysis.

- **Text Content**: Free-form text entered in a textarea.
- Supports **template variables** using the `{{SheetName!CellRef}}` syntax. For example, `Revenue is {{Financials!B12}}` resolves to the live cell value.
- Supports inline markdown rendering for basic formatting.
- No data source sheet or range needed.

#### Treemap

Finviz-style proportional heatmap with labeled rectangles sized by value and colored by a secondary metric.

- **Labels Range**: Cell range for rectangle labels (e.g., `A2:A50`).
- **Size Values Range**: Cell range for sizing each rectangle (e.g., `B2:B50`).
- **Color Values Range**: Cell range for coloring each rectangle (e.g., `C2:C50`).
- **Min Color**: Color for the lowest value (default: red `#d93025`).
- **Neutral Color**: Color for mid-range values (default: gray `#555555`).
- **Max Color**: Color for the highest value (default: green `#34a853`).
- Default size: 12 columns wide, 4 rows tall (full-width).

#### Gauge

SVG semi-circular speedometer dial with animated needle.

- **Data Range**: A single cell providing the current value.
- **Min Value**: Lower bound of the gauge range (default: 0).
- **Max Value**: Upper bound of the gauge range (default: 100).
- **Prefix**: Text before the displayed value (e.g., `$`).
- **Suffix**: Text after the displayed value (default: `%`).
- Default color threshold zones: red (0-33%), yellow (33-66%), green (66-100%).
- Default size: 3 columns wide, 3 rows tall.

### Data Binding

Widgets read live data from other sheets in the workbook. The data source configuration has two parts:

1. **Source Sheet**: Select any other sheet in the workbook (spreadsheet, timeline, calendar, etc.).
2. **Data Range / Labels Range / Values Range**: Standard cell range notation (e.g., `A1`, `B2:B10`, `A1:D20`).

Data is read fresh each time the dashboard renders. When source data changes, the dashboard reflects it on the next render cycle.

#### Range Notation

- Single cell: `B2`
- Column range: `B2:B10`
- Rectangular range: `A1:D20`
- Ranges reference the source sheet, not the dashboard sheet.

### Template Variables

Text widgets support live data references using double-brace syntax:

```
Revenue this quarter: {{Financials!B12}}
Pipeline count: {{Pipeline!A1}}
Status: {{Status!C3}}
```

Each `{{SheetName!CellRef}}` is resolved to the current cell value at render time.

### Surface Styling

Click **Surface** in the toolbar to open the surface editor:

| Setting | Description | Range |
|---|---|---|
| Surface Background | Board background color | Any hex color |
| Grid Line Color | Color of the underlying grid lines | Any hex color |
| Layout Mode | Freeform Grid or Packed/Dense | Toggle |
| Columns | Number of grid columns | 8-24 |
| Row Height | Height of each grid row in pixels | 36-160 |

The dashboard automatically adapts text colors, border tones, and widget defaults based on the surface luminance. Dark surfaces get light text; light surfaces get dark text.

### Layout Modes

**Freeform Grid** (default): Widgets are placed on the grid at specific positions. You can leave gaps and whitespace between widgets for a more editorial, presentation-style layout.

**Packed / Dense**: Widgets are compressed together to eliminate gaps. The packing algorithm sorts widgets by area (largest first) and places them into the first available slot. Use packed mode for dense market-board, operations wall, or control-room layouts.

Click **Pack Widgets** in the toolbar to run the packing algorithm at any time, even in freeform mode.

### Widget Styling

Each widget has individual style controls in the widget editor:

| Setting | Description |
|---|---|
| Accent Color | Primary color for charts, rings, and KPI emphasis |
| Widget Background | Fill color of the widget card |
| Border Color | Outline color of the widget card |

Darker widget backgrounds pair well with darker dashboard surfaces. The text color inside each widget automatically adjusts for contrast.

### Widget Sizing and Placement

- **Width**: Number of grid columns the widget spans (1 to max columns).
- **Height**: Number of grid rows the widget spans (1 to 12).
- New widgets are auto-placed in the first open grid slot.
- Treemaps default to full-width (12 columns, 4 rows).
- Gauges default to 3 columns, 3 rows.
- All other widgets default to 3 columns, 2 rows.

### Drag-to-Move

Click and drag a widget's header bar to reposition it on the grid. The widget snaps to grid columns and rows. If the dashboard is in packed mode, the pack algorithm re-runs after the move.

### Drag-to-Resize

Click and drag the bottom-right resize handle to change a widget's size. The widget snaps to grid column and row boundaries. Minimum size is 1x1.

### Keyboard Shortcuts

Dashboard interaction is primarily mouse-driven. Widget editing uses the standard dialog keyboard behavior:

| Shortcut | Action |
|---|---|
| Click widget edit button | Open widget editor |
| Click widget delete button | Delete widget |
| Escape | Close editor overlay |
| Click outside overlay | Close editor overlay |

### Menu Contributions

**Insert menu:**
- Add widget

**View menu:**
- Pack Widgets -- compress layout
- Reset Layout -- rearrange all widgets into a uniform 4-wide grid

**Surface menu:**
- Surface settings... -- open the surface editor
- Pack widgets -- compress layout

### CLI Commands

All CLI commands require `--file <WorkbookName>` and the dashboard sheet name.

**List widgets:**

```
xapps widgets MyDashboard --file MyWorkbook.json
```

Expected output:

```
  0: w-abc123 kpi Monthly Revenue
  1: w-def456 bar Sales by Region
  2: w-ghi789 progress Sprint Completion
  3: w-jkl012 text Executive Summary
```

**Read one widget:**

```
xapps widget MyDashboard w-abc123 --file MyWorkbook.json
```

Expected output (JSON):

```json
{
  "id": "w-abc123",
  "type": "kpi",
  "title": "Monthly Revenue",
  "gridX": 0,
  "gridY": 0,
  "gridW": 3,
  "gridH": 2,
  "dataSource": {
    "sheetName": "Financials",
    "range": "B12"
  },
  "config": {
    "prefix": "$",
    "suffix": "M",
    "trend": "+8%"
  },
  "style": {
    "accentColor": "#2563eb",
    "bgColor": "#ffffff",
    "borderColor": "#dbe4ef"
  }
}
```

**Create a KPI widget:**

```
xapps add-widget MyDashboard \
  '{"type":"kpi","title":"Total Users","dataSource":{"sheetName":"Metrics","range":"B2"},"config":{"prefix":"","suffix":"K","trend":"+15%"},"gridW":3,"gridH":2}' \
  --file MyWorkbook.json
```

Expected output:

```
Dashboard widget created: w-mno345
```

**Create a bar chart widget:**

```
xapps add-widget MyDashboard \
  '{"type":"bar","title":"Sales by Region","dataSource":{"sheetName":"Sales","range":"B2:B6"},"config":{"labelRange":"A2:A6","valueRange":"B2:B6"},"gridW":6,"gridH":3}' \
  --file MyWorkbook.json
```

**Create a text widget with template variables:**

```
xapps add-widget MyDashboard \
  '{"type":"text","title":"Status Update","config":{"content":"Pipeline: {{Pipeline!A1}} deals worth {{Pipeline!B1}}. Next milestone: {{Roadmap!C2}}."},"gridW":4,"gridH":2}' \
  --file MyWorkbook.json
```

**Create a treemap widget:**

```
xapps add-widget MyDashboard \
  '{"type":"treemap","title":"Market Cap Heatmap","dataSource":{"sheetName":"Stocks","range":"A1"},"config":{"tmLabels":"A2:A50","tmSizes":"B2:B50","tmColors":"C2:C50","tmMinColor":"#d93025","tmNeutral":"#555555","tmMaxColor":"#34a853"},"gridW":12,"gridH":4}' \
  --file MyWorkbook.json
```

**Create a gauge widget:**

```
xapps add-widget MyDashboard \
  '{"type":"gauge","title":"CPU Usage","dataSource":{"sheetName":"Monitoring","range":"B1"},"config":{"gaugeMin":0,"gaugeMax":100,"gaugePrefix":"","gaugeSuffix":"%"},"gridW":3,"gridH":3}' \
  --file MyWorkbook.json
```

**Create a progress ring widget:**

```
xapps add-widget MyDashboard \
  '{"type":"progress","title":"Sprint Progress","dataSource":{"sheetName":"Sprint","range":"D1"},"config":{"max":100},"gridW":3,"gridH":2}' \
  --file MyWorkbook.json
```

**Create a data table widget:**

```
xapps add-widget MyDashboard \
  '{"type":"table","title":"Top Accounts","dataSource":{"sheetName":"Accounts","range":"A1:D10"},"gridW":6,"gridH":3}' \
  --file MyWorkbook.json
```

**Update a widget:**

```
xapps update-widget MyDashboard w-abc123 \
  '{"title":"Monthly Revenue (Updated)","config":{"trend":"+12%"}}' \
  --file MyWorkbook.json
```

Expected output:

```
Dashboard widget w-abc123 updated
```

**Delete a widget:**

```
xapps delete-widget MyDashboard w-abc123 --file MyWorkbook.json
```

Expected output:

```
Dashboard widget w-abc123 deleted
```

### API Endpoints

**List all widgets:**

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/MyDashboard/widgets
```

**Read one widget:**

```bash
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/MyDashboard/widgets/w-abc123
```

**Create a widget:**

```bash
curl -X POST $XAPPS_API_BASE_URL/api/sheets/MyDashboard/widgets \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{
    "type": "kpi",
    "title": "Conversion Rate",
    "dataSource": {"sheetName": "Funnel", "range": "C5"},
    "config": {"suffix": "%", "trend": "+2.1pp"},
    "gridW": 3,
    "gridH": 2,
    "style": {"accentColor": "#34a853"}
  }'
```

**Update a widget:**

```bash
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/MyDashboard/widgets/w-abc123 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"title": "Revenue (Q2)", "config": {"trend": "+15%"}}'
```

**Delete a widget:**

```bash
curl -X DELETE -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/MyDashboard/widgets/w-abc123
```

### Agent / AI Workflow Recipes

**Recipe 1: Build an executive dashboard from scratch**

An agent can create a complete KPI dashboard by reading data from existing sheets and adding widgets programmatically:

```bash
# 1. Create KPI cards for key metrics
curl -X POST $XAPPS_API_BASE_URL/api/sheets/ExecBoard/widgets \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"type":"kpi","title":"ARR","dataSource":{"sheetName":"Finance","range":"B2"},"config":{"prefix":"$","suffix":"M","trend":"+22%"},"gridW":3,"gridH":2}'

curl -X POST $XAPPS_API_BASE_URL/api/sheets/ExecBoard/widgets \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"type":"kpi","title":"Active Users","dataSource":{"sheetName":"Metrics","range":"B3"},"config":{"suffix":"K","trend":"+15%"},"gridW":3,"gridH":2}'

# 2. Add a revenue trend line chart
curl -X POST $XAPPS_API_BASE_URL/api/sheets/ExecBoard/widgets \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"type":"line","title":"Revenue Trend","dataSource":{"sheetName":"Finance","range":"B2:B13"},"config":{"labelRange":"A2:A13","valueRange":"B2:B13"},"gridW":6,"gridH":3}'

# 3. Add a text block for narrative context
curl -X POST $XAPPS_API_BASE_URL/api/sheets/ExecBoard/widgets \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"type":"text","title":"Weekly Update","config":{"content":"ARR grew to {{Finance!B2}}M this quarter. Pipeline has {{Pipeline!A1}} active deals. Next board meeting: {{Calendar!B1}}."},"gridW":6,"gridH":2}'
```

**Recipe 2: Monitoring dashboard with gauges and progress rings**

Build a system monitoring or project health dashboard:

```bash
# CPU gauge
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Monitor/widgets \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"type":"gauge","title":"CPU","dataSource":{"sheetName":"Infra","range":"B1"},"config":{"gaugeMin":0,"gaugeMax":100,"gaugeSuffix":"%"},"gridW":3,"gridH":3}'

# Memory gauge
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Monitor/widgets \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"type":"gauge","title":"Memory","dataSource":{"sheetName":"Infra","range":"B2"},"config":{"gaugeMin":0,"gaugeMax":64,"gaugeSuffix":"GB"},"gridW":3,"gridH":3}'

# Sprint progress ring
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Monitor/widgets \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"type":"progress","title":"Sprint","dataSource":{"sheetName":"Sprint","range":"E1"},"config":{"max":100},"gridW":3,"gridH":2}'

# Error rate table
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Monitor/widgets \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"type":"table","title":"Recent Errors","dataSource":{"sheetName":"Logs","range":"A1:D20"},"gridW":6,"gridH":3}'
```

**Recipe 3: Financial heatmap with treemap widget**

Create a Finviz-style stock or sector performance view:

```bash
# Populate a spreadsheet with stock data first, then add the treemap
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Markets/widgets \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{
    "type": "treemap",
    "title": "S&P 500 Heatmap",
    "dataSource": {"sheetName": "Stocks", "range": "A1"},
    "config": {
      "tmLabels": "A2:A50",
      "tmSizes": "B2:B50",
      "tmColors": "C2:C50",
      "tmMinColor": "#d93025",
      "tmNeutral": "#555555",
      "tmMaxColor": "#34a853"
    },
    "gridW": 12,
    "gridH": 5
  }'
```

### Troubleshooting

**Widget shows "Configure data source"**
The widget's source sheet or data range is not set. Edit the widget and select a source sheet and enter the appropriate range. For charts, both label range and value range are required.

**Widget shows "No data"**
The source sheet exists but the specified range is empty. Verify that the range contains data in the source sheet. Check that the sheet name matches exactly (case-sensitive).

**KPI card shows 0 or blank**
The data range should point to a single cell containing a number. Ensure the source sheet cell has a value. If using formulas in the source cell, verify they evaluate correctly.

**Template variables not resolving in text widget**
Template variables use the syntax `{{SheetName!CellRef}}`. Ensure the sheet name and cell reference are correct. The sheet name is case-sensitive and must match exactly.

**Widgets overlap after adding a new one**
In freeform grid mode, auto-placement finds the first open slot but may not always avoid visual overlap on narrow screens. Use **Pack Widgets** to compress the layout, or manually drag widgets to reposition them.

**Dark surface makes widget text unreadable**
The dashboard automatically adapts text colors based on surface and widget background luminance. If a custom widget background causes contrast issues, adjust the widget background color in the widget editor to be lighter or darker.

**Treemap appears blank**
Treemap requires three ranges: labels, sizes, and colors. The sizes must be positive numbers. Ensure the source sheet has data in all three ranges and that size values are numeric and greater than zero.

**Gauge needle stuck at minimum**
The gauge reads a single cell value. Ensure the data range points to a cell with a numeric value within the configured min/max range. If the value is text, the gauge interprets it as 0.

**Packed layout looks wrong after resize**
After resizing a widget in packed mode, the pack algorithm re-runs. If the result looks unexpected, try **Pack Widgets** again or switch to freeform grid for manual control.

**Bar/line chart has no bars or line**
Both the labels range and values range must be specified. Values must be numeric. If the ranges have different lengths, the shorter one determines the number of data points.

### Tips & Tricks

- Start with 3-4 KPI cards across the top row, then add charts and tables below for a classic executive dashboard layout.
- Use the Surface editor to create dark-themed dashboards for control rooms or presentations -- set a dark surface background and the dashboard auto-adapts all widget colors.
- Text widgets with template variables are great for narrative context -- write sentences that reference live data cells.
- Treemap widgets work best at full width (12 columns). Give them 4-5 rows of height for readability.
- Use the gauge widget for any bounded metric: CPU usage, satisfaction scores, budget utilization.
- Progress rings are simpler than gauges and work well for completion percentages.
- Packed mode creates dense, Finviz-style board layouts. Combine with more columns (16-20) and shorter row heights (50-60px) for maximum density.
- Data table widgets automatically use the first row of the range as column headers.
- Duplicate a widget by creating a new one with the same configuration -- there is no built-in duplicate button, but the CLI makes this easy by copying the JSON.
- Combine dashboards with spreadsheet formulas (SUM, AVERAGE, COUNT) to create derived metrics that widgets can display.

### Works Well With

- Spreadsheet for data aggregation and formula-based metrics
- Timeline for milestone tracking and project status
- Kanban for task count and status distribution
- Calendar for upcoming event summaries
- Document for detailed analysis and narrative
