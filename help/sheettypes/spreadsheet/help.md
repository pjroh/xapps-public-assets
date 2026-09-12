## Spreadsheets

### Build your first useful spreadsheet

Use Spreadsheet for calculations and a flexible grid. Choose Records instead when you need typed relational tables, linked records, and several saved views over the same records.

1. Put labels in row 1, such as **Item**, **January**, **February**, **March**, and **Quarter**. Enter numbers as values so they can be calculated; use formatting to display currency or percentages.
2. In E2 enter `=SUM(B2:D2)` and press Enter. Select E2 again: the grid shows the result, while the formula bar shows the expression that produced it. This distinction is useful whenever a number looks wrong.
3. Fill the formula down for other items. Relative references move with each row; use `$B$2` when a reference must stay fixed. Check a second row before filling a large area.
4. Add a total below the data, for example `=SUM(E2:E9)`. Apply number formats to the values and emphasize the header and total row. Formatting changes presentation; it does not repair numbers imported as text.
5. Select the labeled data and use the chart controls to create a chart. Confirm its range includes the intended categories and values. Keep totals out of a category comparison unless you intentionally want a total bar.
6. Save the workbook and reopen the sheet when handing it to someone else. Give the sheet a meaningful name so cross-sheet references remain readable.

### Keep inputs reliable

Use **Data Validation** to constrain expected inputs, such as a status choice or a numeric range. Use **Conditional Formatting** to draw attention to values that meet a rule. They solve different problems: highlighting a bad value does not prevent its entry.

Create a structured table when a region represents records with headers. Table operations can sort its body as a unit; sorting one unrelated column alone risks separating values that belong together. Preview cleanup and import results before applying them, and keep a source copy when transforming data.

### Follow a number across sheets

A formula can reference a supported value in another sheet, for example `='Budget'!E2`. Quote names containing spaces. Start by reading one known cell, then expand the formula; an empty or error result should send you back to the source sheet and reference first. Charts, dashboards, and embeds each have their own supported binding options—being in the same workbook does not make every object a spreadsheet cell.

### Grid work, formulas, and lightweight analysis

Spreadsheet sheets provide a flexible grid for data entry, calculations, formatting, charting, and cross-sheet references. Other sheet types have their own data models and supported bindings; use their dedicated tools when working with records, cards, events, or room-backed collaboration.

> 🤖 Agent example: an agent can import a CSV, normalize headers, build formulas, apply validation, and leave a human-ready review sheet in the same workbook.

![Spreadsheet workspace with formulas, conditional formatting, sparklines, and currency data](/help-assets/screenshots/spreadsheet-sheet.png)

---

### Features at a Glance

- Cell editing with inline and formula-bar input
- 40+ built-in formula functions across Math, Finance, Conditional, Text, Lookup, Date, Charts, and Spatial categories
- Cross-sheet formula references (`='Other Sheet'!A1`)
- Conditional formatting with 12 condition types
- Data validation (list, number, text) including dependent/conditional dropdowns
- Charts (bar, line, pie, scatter) -- floating or anchored in cells
- Sparklines (line, bar) via `=SPARKLINE()`
- Cell comments and images
- Merge/unmerge ranges
- Column field types (checkbox, select, date, rating, progress, email, phone, number)
- Freeze rows and columns
- Import/export fidelity panel plus CSV, TSV, XLSX, ODS, and PDF paths
- Data cleanup panel for trim whitespace, duplicate detection/removal, and split text to columns
- Spreadsheet Assistant panel for explain range, summarize insights, suggest formulas, build tables/charts/pivots, add validations, conditionally format, clean data, and sort/filter with confirmed writes
- External data panel for Connected Sheets-style pasted JSON/CSV and workbook-range extracts
- Timeline view panel for mapping date ranges into printable previews and xApps Timeline sheets
- Macro recorder and safe xApps macro JSON script hooks
- Bulk operations (bulk-set, range formatting)
- Column width and row height control
- Find and Replace
- Filter and sort
- Row detail view (form-style editor for wide sheets)
- Alternating row colors
- Undo/redo
- Virtual scrolling for large datasets (250+ rows)
- Keyboard-driven navigation

---

### Getting Started

1. **Create a spreadsheet sheet.** Click the `+` button in the sheet tab bar and select "Spreadsheet."
2. **Enter data.** Click any cell and start typing. Press `Enter` to confirm and move down, or `Tab` to confirm and move right.
3. **Add a formula.** Type `=` to begin a formula. For example, `=SUM(A1:A10)` sums the first 10 rows of column A.
4. **Format cells.** Use the toolbar to set bold, italic, text color, background color, number format, alignment, and borders.
5. **Insert a chart.** Select a data range, then use the Insert menu or CLI to create a bar, line, pie, or scatter chart.
6. **Share across sheets.** Reference data from other sheets with `='Sheet Name'!CellRef` syntax.

---

### Everyday Editing

| Action | How |
|---|---|
| Type in a cell | Click a cell and start typing |
| Edit existing content | Double-click the cell, or press `F2` |
| Confirm and move down | `Enter` |
| Confirm and move right | `Tab` |
| Cancel editing | `Escape` |
| Select a range | Drag, or click then `Shift`+click |
| Delete cell content | `Delete` or `Backspace` on a selected cell |

Double-clicking a cell selects its content so you can replace it quickly. While editing a formula, you can click cells and ranges to insert references directly.

---

### Formulas

Every formula starts with `=`. xApps evaluates formulas in real time with circular reference detection.

#### Math Functions

| Function | Syntax | Description |
|---|---|---|
| SUM | `SUM(range)` | Adds all numbers in a range |
| AVERAGE | `AVERAGE(range)` | Returns the average of numbers in a range |
| MIN | `MIN(range)` | Returns the smallest number in a range |
| MAX | `MAX(range)` | Returns the largest number in a range |
| COUNT | `COUNT(range)` | Counts numeric cells in a range |
| COUNTA | `COUNTA(range)` | Counts non-empty cells including text |
| ABS | `ABS(number)` | Returns absolute value |
| ROUND | `ROUND(number, digits)` | Rounds to specified decimal places |
| FLOOR | `FLOOR(number)` | Rounds down to nearest integer |
| CEILING | `CEILING(number)` | Rounds up to nearest integer |
| SQRT | `SQRT(number)` | Returns the square root |
| POWER | `POWER(base, exp)` | Returns base raised to exponent |

#### Finance Functions

| Function | Syntax | Description |
|---|---|---|
| PMT | `PMT(rate, nper, pv, [fv], [type])` | Returns a loan or annuity payment; use a per-period rate such as `5%/12` for monthly APR |
| PV | `PV(rate, nper, pmt, [fv], [type])` | Returns present value |
| FV | `FV(rate, nper, pmt, [pv], [type])` | Returns future value |
| NPV | `NPV(rate, value1, [value2], ...)` | Returns net present value |
| IRR | `IRR(values, [guess])` | Returns internal rate of return |

#### Conditional Functions

| Function | Syntax | Description |
|---|---|---|
| IF | `IF(condition, true_val, false_val)` | Returns value based on condition |
| IFERROR | `IFERROR(value, fallback)` | Returns fallback when value evaluates to an error |
| AND | `AND(value1, value2, ...)` | Returns TRUE when all values are truthy |
| OR | `OR(value1, value2, ...)` | Returns TRUE when any value is truthy |
| SUMIF | `SUMIF(range, criteria, [sum_range])` | Sums cells matching a condition |
| COUNTIF | `COUNTIF(range, criteria)` | Counts cells matching a condition |
| SUMIFS | `SUMIFS(sum_range, criteria_range1, criteria1, ...)` | Sums cells matching multiple conditions |
| COUNTIFS | `COUNTIFS(criteria_range1, criteria1, ...)` | Counts cells matching multiple conditions |
| AVERAGEIF | `AVERAGEIF(range, criteria, [average_range])` | Averages cells matching a condition |
| AVERAGEIFS | `AVERAGEIFS(average_range, criteria_range1, criteria1, ...)` | Averages cells matching multiple conditions |

#### Text Functions

| Function | Syntax | Description |
|---|---|---|
| CONCAT | `CONCAT(text1, text2, ...)` | Joins text strings together |
| CONCATENATE | `CONCATENATE(text1, text2, ...)` | Joins text strings together (alias) |
| LEN | `LEN(text)` | Returns the length of a text string |
| UPPER | `UPPER(text)` | Converts text to uppercase |
| LOWER | `LOWER(text)` | Converts text to lowercase |
| TRIM | `TRIM(text)` | Removes leading/trailing spaces |
| LEFT | `LEFT(text, [num_chars])` | Returns the leftmost characters |
| RIGHT | `RIGHT(text, [num_chars])` | Returns the rightmost characters |
| MID | `MID(text, start_num, num_chars)` | Returns characters from the middle of text |

#### Lookup Functions

| Function | Syntax | Description |
|---|---|---|
| VLOOKUP | `VLOOKUP(key, range, col_index)` | Searches first column and returns value from another column |
| INDEX | `INDEX(range, row_num, [column_num])` | Returns a value by row and column position |
| MATCH | `MATCH(lookup_value, lookup_array, [match_type])` | Returns a matching position in a range |

#### Date Functions

| Function | Syntax | Description |
|---|---|---|
| NOW | `NOW()` | Returns current date and time |
| TODAY | `TODAY()` | Returns current date |
| DATE | `DATE(year, month, day)` | Returns a date from year, month, and day |
| YEAR | `YEAR(date)` | Returns the year from a date |
| MONTH | `MONTH(date)` | Returns the month from a date |
| DAY | `DAY(date)` | Returns the day from a date |

#### Chart Functions

| Function | Syntax | Description |
|---|---|---|
| SPARKLINE | `SPARKLINE(range, [type], [color])` | Renders a tiny inline chart. Type: `"line"` (default) or `"bar"`. Color: any hex like `"#0f9d58"`. |

#### Spatial / GEO Functions

These functions work in any spreadsheet cell and are useful alongside Map sheets.

| Function | Syntax | Description |
|---|---|---|
| GEO_DISTANCE | `GEO_DISTANCE(lat1, lon1, lat2, lon2, [unit])` | Haversine distance between two points. Unit: `"mi"` (default) or `"km"`. |
| GEO_BEARING | `GEO_BEARING(lat1, lon1, lat2, lon2)` | Initial bearing in degrees (0-360) from point 1 to point 2. |
| GEO_MIDPOINT | `GEO_MIDPOINT(lat1, lon1, lat2, lon2)` | Returns `"lat,lon"` of the geographic midpoint. |
| GEO_FORMAT | `GEO_FORMAT(lat, lon, [format])` | Formats coordinates. Format: `"dd"` (decimal degrees, default), `"dms"` (degrees/minutes/seconds), or `"dm"`. |

#### Formula Examples

```text
=SUM(B2:B20)
=AVERAGE(C2:C50)
=COUNTIF(A:A, "Overdue")
=IF(C2>100, "Over budget", "OK")
=SUMIFS(D2:D20, A2:A20, "West", C2:C20, ">100")
=PMT(0.05/12, 60, 30000)
=INDEX(B2:D10, MATCH("Widget", A2:A10, 0), 3)
=VLOOKUP("Widget", A1:D100, 4)
=SPARKLINE(E2:E20)
=SPARKLINE(E2:E20, "bar", "#0f9d58")
=GEO_DISTANCE(40.7128, -74.0060, 34.0522, -118.2437)
=GEO_FORMAT(40.7128, -74.0060, "dms")
```

#### Cross-Sheet References

Reference cells on other sheets by prefixing the sheet name in single quotes:

```text
=SUM('Construction Budget'!D2:D50)
=COUNTIF('Sprint Board'!B:B, "Done")
='Q1 Revenue'!F25
```

#### Formula Assist

When you type `=` and begin a formula, the formula assist panel appears, showing:
- A selectable function list with syntax and short descriptions
- Filtering as you type after `=`
- Syntax hint with the current argument highlighted
- Argument suggestions (e.g., sparkline type and color options)

Use the **Insert Function** dialog (from the toolbar) to browse all functions by category (All, Math, Conditional, Text, Lookup, Date, Charts) with descriptions and syntax previews.

#### Browser formula-authoring boundary

The function picker, autocomplete, active-argument hints, and dependency-driven grid repaint are transient browser editing guidance, not separate durable formula APIs. The core formula storage, evaluation, evaluated/raw reads, and formula-bearing writes remain available to automation through the typed Spreadsheet SDK (`getCell`, `getEvaluatedCell`, `readRange`, and `setCell`). For guarded formula authoring, use `spreadsheet-assistant-preview` / `spreadsheet-assistant-apply` with `suggest-formula`; use this Formula Reference for catalog guidance.

---

### Formatting and Structure

![Budget spreadsheet with currency format, conditional formatting highlights, and sparklines](/help-assets/screenshots/spreadsheet-formulas.png)

#### Text Formatting

Use the toolbar or context menu for:
- **Bold** (`Ctrl/Cmd+B`), **Italic** (`Ctrl/Cmd+I`), **Underline** (`Ctrl/Cmd+U`), **Strikethrough**
- Font size (8 through 36pt, selectable from the toolbar)
- Text color (24 swatches + custom)
- Background/fill color (24 swatches + clear option)
- Text alignment (left, center, right)
- Text wrap
- Number formats (general, number, currency, percentage, date, etc.)

> **Percent format displays the stored value × 100** — same convention as Excel and Google Sheets. To display **20%** the cell value must be **0.20**; to display **6.5%** the cell value must be **0.065**. Storing `20` and applying `format: percent` displays **2000%**, not **20%**. The CLI helps with this: `xapps set <sheet> <ref> 20%` (with the trailing `%`) auto-divides by 100, stores 0.20, and applies percent format in one call. The same coercion runs in `bulk-set` per cell. Plain numbers are stored verbatim — pass `20%` (string with `%`), not `20` (number).

#### Borders and Fills

Apply borders and background fills to individual cells or ranges. Alternating row colors can be toggled for readability.

#### Column Width and Row Height

Resize columns by dragging the header border, or set exact values via CLI. Same for row heights.

#### Merge and Unmerge

Select a range and merge it into a single cell. The top-left cell's value is preserved. Unmerge to restore individual cells.

#### Freeze Panes

Freeze rows and/or columns so they stay visible while scrolling. Use the View menu or CLI commands.

#### Comments

Add comments to any cell. Cells with comments show an indicator triangle. View, edit, or delete comments from the dialog or CLI.

#### Images in Cells

Embed images in any cell by URL. Supports fit modes: `contain`, `cover`, or `original`.

#### Smart Chips and Rich Cells

Use **Insert > Insert smart chip...** to create a rich cell object while keeping a plain fallback value for formulas, CSV export, and automation. Select an existing chip cell and use **Format > Smart chips > Edit smart chip...** or the cell context menu to edit its metadata. The dialog changes fields based on the chip type: people show email, files show file name/URL/MIME type, dates show date/calendar ID, dropdown/status chips show allowed values plus a Current value picker, places show address, sheet chips show sheet/range, and links show URL. For dropdown/status chips, edit Allowed values first; the Current value picker is rebuilt from those options before saving. Click a dropdown/status chip or its arrow to choose one of its configured allowed values. Chips render as compact labeled tokens in the grid and can keep URL, email, date, address, sheet/range, color, description, and dropdown option metadata.

#### Zoom

Control the zoom level from the View menu or the zoom control in the status bar. Presets run from 50% to 200% in steps; use **Zoom to Fit** to scale the data area to the available window.

| Action | Shortcut |
|---|---|
| Zoom in | `Ctrl/Cmd+]` |
| Zoom out | `Ctrl/Cmd+[` |
| Reset to 100% | `Ctrl/Cmd+0` |

---

### Row and Column Operations

Right-click a row or column header (or use the Edit menu) to access structural editing:

| Action | How |
|---|---|
| Insert row above / below | Right-click row header → Insert → Row above / below |
| Insert column left / right | Right-click column header → Insert → Column left / right |
| Delete row | Right-click row header → Delete → Row |
| Delete column | Right-click column header → Delete → Column |
| Move row up / down | Right-click row header → Move row up / down |
| Move column left / right | Right-click column header → Move column left / right |

---

### Data Validation

Spreadsheet cells support three validation types:

#### List Validation

Restrict input to a predefined list of options. Optionally show a dropdown.

```json
{
  "type": "list",
  "items": ["Apple", "Banana", "Cherry"],
  "showDropdown": true,
  "reject": true
}
```

#### Dependent/Conditional Dropdowns

One cell's dropdown options change based on another cell's value:

```json
{
  "type": "list",
  "dependsOnRef": "A",
  "optionsByValue": {
    "Residential": ["Paint", "Flooring"],
    "Commercial": ["Permit", "Inspection"]
  },
  "fallbackItems": ["Other"],
  "showDropdown": true,
  "reject": true
}
```

#### Number Validation

Restrict to numeric values with conditions: `between`, `gt` (greater than), `lt` (less than), `eq` (equal).

```json
{
  "type": "number",
  "cond": "between",
  "min": 0,
  "max": 100,
  "reject": true
}
```

#### Text Validation

Restrict text length:

```json
{
  "type": "text",
  "maxLen": 50,
  "reject": true
}
```

---

### Column Field Types

Set column-wide field types to give cells special behavior:

- **checkbox** -- renders a toggle
- **single-select** / **multi-select** -- tag-style pickers
- **date** -- date picker
- **rating** -- star rating
- **progress** -- progress bar
- **email** -- validates email format
- **phone** -- validates phone number format
- **number** -- validates numeric input

---

### Conditional Formatting

Apply visual rules to cell ranges based on their values.

#### Supported Conditions

| Condition | Description |
|---|---|
| `greater` | Greater than a value |
| `less` | Less than a value |
| `equal` | Equal to a value |
| `not-equal` | Not equal to a value |
| `between` | Between two values |
| `contains` | Text contains substring |
| `not-contains` | Text does not contain substring |
| `starts-with` | Text starts with |
| `ends-with` | Text ends with |
| `empty` | Cell is empty |
| `not-empty` | Cell is not empty |
| `duplicate` | Value appears more than once |

Each rule specifies: range, condition, value(s), background color, text color, bold, and italic. Rules can be enabled/disabled individually.

---

### Charts

Create charts from selected data ranges. Supported types:

- **Bar** chart
- **Line** chart
- **Pie** chart
- **Scatter** plot

![Bar chart floating over a budget spreadsheet](/help-assets/screenshots/spreadsheet-chart.png)

#### Chart Placement

- **Floating overlay** -- chart appears on top of the grid
- **Anchored in cells** -- chart is pinned to a target cell range

Chart context menus let you rename, re-anchor, float, or delete a chart.

#### Sparklines

Inline mini-charts rendered directly in a cell:

```text
=SPARKLINE(F2:F12)              -- line sparkline (default)
=SPARKLINE(F2:F12, "bar")       -- bar sparkline
=SPARKLINE(F2:F12, "bar", "#0f9d58")  -- green bar sparkline
```

---

### Data Tools

- **Filter rules** in the toolbar to show/hide rows
- **Find and Replace** within the sheet (`Ctrl/Cmd+Shift+H`)
- **Fill handles** for range autofill -- drag the blue square at the bottom-right of a selection to repeat or continue a series
- **Data cleanup** from the Data menu to preview/apply trim whitespace, duplicate detection/removal, and split text to columns
- **Assistant workflows** from the Data menu to preview and confirm sheet-aware actions such as create table, suggest formula, explain range, clean data, build chart, build pivot, add dropdown/checkbox, conditional formatting, sort/filter, and summarize insights
- **External data** from the Data menu to define workbook-scoped connected sources, preview queries, refresh extracts, and inspect schedule/permission/audit metadata
- **Timeline view** from the Data menu to map table/range rows into dated tasks, preview grouped bars, print the view, and export to an xApps Timeline sheet
- **Row detail view** -- form-style editor for wide sheets with many columns
- **Sort** by column values

#### Embed Sheet View

Insert a live read-only preview of any range from any sheet in the workbook into a cell. Use **Insert > Embed sheet view...** to open the dialog, pick a sheet and a range, then confirm. The embedded view renders a compact table that updates when the source data changes. This is useful for building dashboards where a cell area displays a summary from a different sheet without needing formulas.

Agents can discover and resolve destination-aware, same-workbook range descriptors with `xapps spreadsheet-embed-sources <sheet>` and `xapps spreadsheet-resolve-embed <sheet> <descriptor-json>`; descriptors use stable source/destination sheet identities, ranges are limited to 200 cells, and the consuming surface owns placeholder persistence. Version review, naming, range/sheet restore, and copy commands use the same typed Spreadsheet SDK contract as MCP and hosted tools.

---

### Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Enter` | Confirm edit, move down |
| `Tab` | Confirm edit, move right |
| `Escape` | Cancel editing |
| `F2` | Enter edit mode on selected cell |
| `Delete` / `Backspace` | Clear cell content |
| Arrow keys | Navigate between cells |
| `Shift` + Arrow | Extend selection |
| `Shift` + Click | Select range from current cell |
| `Ctrl/Cmd` + `Z` | Undo |
| `Ctrl/Cmd` + `Y` | Redo |
| `Ctrl/Cmd` + `X` | Cut |
| `Ctrl/Cmd` + `C` | Copy |
| `Ctrl/Cmd` + `V` | Paste |
| `Ctrl/Cmd` + `B` | Bold |
| `Ctrl/Cmd` + `I` | Italic |
| `Ctrl/Cmd` + `U` | Underline |
| `Ctrl/Cmd` + `Shift` + `H` | Find and Replace |
| `Ctrl/Cmd` + `Alt` + `M` | Insert Comment |
| `Ctrl/Cmd` + `Shift` + `F` | Search all sheets |
| `Ctrl/Cmd` + `]` | Zoom in |
| `Ctrl/Cmd` + `[` | Zoom out |
| `Ctrl/Cmd` + `0` | Reset zoom to 100% |
| `Alt` + `ArrowUp` | Switch to previous sheet |
| `Alt` + `ArrowDown` | Switch to next sheet |

---

### CLI Commands

All commands use the pattern:
```
xapps <command> --file <WorkbookName>
```
Add `--json` when an agent needs a machine-readable success envelope with `ok`, `message`, and command-specific fields.

#### Cell Operations

**Read a cell:**
```bash
xapps get "Budget" A1
# Output: 1500
```
Formula cells are returned as their evaluated result; the stored formula text stays available as API `rawValue`.

**Write a cell:**
```bash
xapps set "Budget" A1 "=SUM(B2:B20)"
# Output: A1 = =SUM(B2:B20)
```

**Clear a cell:**
```bash
xapps clear "Budget" A1
# Output: Cleared A1
```

**Read a range:**
```bash
xapps range "Budget" A1:C5
# Output (tab-separated rows):
# Name    Q1    Q2
# Alice   1500  1800
# Bob     1200  1400
```

**Bulk write a 2D array:**
```bash
xapps bulk-set "Budget" A1 '[["Name","Q1","Q2"],["Alice",1500,1800],["Bob",1200,1400]]'
# Output: Wrote 3 rows x 3 columns at A1:C3
```

`bulk-set` is one atomic Spreadsheet transaction. Omit both guard flags for
an automatic revision read and generated request id, or supply both when a
caller may need to retry after losing the response:
```bash
xapps spreadsheet batch-state "Budget" --json
xapps bulk-set "Budget" A1 '[["Name","Amount"],["Rent",2000]]' \
  --expected-revision 4 --request-id budget-import-2026-07-13 --json
```

**Guarded atomic semantic batch:**
```bash
xapps spreadsheet batch-state "Budget" --json
printf '{"op":"spreadsheet.formatCell","ref":"A1","format":{"bg":"#ff0000"}}\n' | \
  xapps spreadsheet batch "Budget" --stdin \
    --expected-revision 4 --request-id budget-format-2026-07-13 --json
# Output includes revision, requestId, replayed, applied, and changed.
```

The batch validates every operation before committing, persists the entire
change once, and leaves the sheet unchanged if validation or persistence
fails. Retrying the exact same `requestId`, revision, and payload returns the
persisted receipt without applying twice. Reusing the id with different intent
or submitting a stale revision returns a conflict. Supported operations are
`spreadsheet.setCell`, `clearCell`, `formatCell`, `setRange`, `formatRange`,
`setColumnWidth`, and `setRowHeight`.

#### Formatting

**Format a single cell:**
```bash
xapps format "Budget" A1 '{"bold":true,"color":"#d93025"}'
# Output: Formatted A1
```

**Format a range:**
```bash
xapps range-format "Budget" A1:C1 '{"bold":true,"bg":"#e8f0fe"}'
# Output: Formatted range A1:C1
```

Normal `format` and `range-format` JSON uses cell format keys such as `bg` for
background color, `color` for text color, `format` for number format, and
`decimals` for precision. Conditional formatting rules use their own rule keys:
`bgColor` and `textColor`.

The normal format payload is strict. Unknown keys are rejected before changes
are saved. Do not use `fill`, `fill.color`, `bgColor`, `textColor`, or
`numberFormat` with `format` or `range-format`; use `bg`, `color`, `format`,
and `decimals` instead.

> **`format: percent` is a multiplier.** A cell formatted as `percent` displays
> `value × 100` followed by `%`. Store `0.20` to display `20%`, or pass `"20%"`
> as a string to `set` / `bulk-set` and the CLI will auto-divide by 100 and
> apply percent format. Storing the integer `20` with `format: percent` will
> display `2000%`.

#### Column Types

**List column field types:**
```bash
xapps columns "Budget"
# Output: JSON array of column type definitions
```

**Set a column field type:**
```bash
xapps col-type "Budget" 0 '{"type":"email"}'
# Output: Column 0 type set
```

#### Data Validation

**Get cell validation:**
```bash
xapps validation "Budget" B2
```

**Set cell validation:**
```bash
xapps set-validation "Budget" B2 '{"type":"list","items":["Yes","No"],"showDropdown":true,"reject":true}'
# Output: Validation set on B2
```

**Clear cell validation:**
```bash
xapps clear-validation "Budget" B2
# Output: Validation cleared on B2
```

#### Conditional Formatting

**List rules:**
```bash
xapps conditional-formats "Budget"
```

**Add a rule:**
```bash
xapps add-conditional-format "Budget" '{"rangeStart":"B2","rangeEnd":"B50","condition":"greater","value":"1000","bgColor":"#d4edda","textColor":"#155724","bold":true,"enabled":true}'
# Output: Conditional format added to Budget
```

**Replace all rules:**
```bash
xapps set-conditional-formats "Budget" '[{"rangeStart":"A1","rangeEnd":"A100","condition":"empty","bgColor":"#f8d7da","textColor":"#721c24","enabled":true}]'
# Output: Conditional formats replaced on Budget
```

**Clear all rules:**
```bash
xapps clear-conditional-formats "Budget"
# Output: Conditional formats cleared on Budget
```

#### Comments

**Get a comment:**
```bash
xapps comment "Budget" A1
```

**Set a comment:**
```bash
xapps set-comment "Budget" A1 "Needs review by finance team"
# Output: Comment set on A1
```

**Clear a comment:**
```bash
xapps clear-comment "Budget" A1
# Output: Comment cleared on A1
```

#### Images

**Get cell image:**
```bash
xapps image "Budget" D5
```

**Set cell image:**
```bash
xapps set-image "Budget" D5 "https://example.com/logo.png" --fit cover
# Output: Image set on D5
```

**Clear cell image:**
```bash
xapps clear-image "Budget" D5
# Output: Image cleared on D5
```

#### Smart Chips and Rich Cells

**Get rich cell metadata:**
```bash
xapps rich-cell "Budget" B2
```

**Set a link chip:**
```bash
xapps set-rich-cell "Budget" B2 '{"type":"link","label":"Project plan","value":"Project plan","url":"https://example.com/plan","color":"#2563eb"}'
# Output: Rich cell value set on B2
```

**Clear rich cell metadata:**
```bash
xapps clear-rich-cell "Budget" B2
# Output: Rich cell value cleared on B2
```

#### Charts

**List charts:**
```bash
xapps charts "Budget"
```

**Add a chart:**
```bash
xapps add-chart "Budget" '{"type":"bar","range":"A1:B10","title":"Revenue"}'
# Output: chart_abc123 (or "Chart created")
```

**Update a chart:**
```bash
xapps update-chart "Budget" chart_abc123 '{"title":"Updated Revenue"}'
# Output: Chart chart_abc123 updated
```

**Delete a chart:**
```bash
xapps delete-chart "Budget" chart_abc123
# Output: Chart chart_abc123 deleted
```

#### Structured Tables

Structured tables are sheet-level metadata over a cell range. Payloads support
`id`, `name`, `rangeStart`, `rangeEnd`, `headerRow`, `style`, `columns`,
`sortRules`, and `groupBy`. When `columns` is omitted, xApps derives column
names from the header row cells.

In the UI, select a range and click **Format as Table** in the spreadsheet
toolbar. Table headers show one arrow sort control; the arrow points up for
ascending and down for descending, and sorting only reorders the table body.
Toolbar A/Z sorting still targets the table body when the selected cell is
inside a structured table. Use **Alternating Colors** for plain striped ranges
without creating table metadata. To group records, select a cell in the table
column you want to group by, then choose **Data > Table > Group by selected
column** or right-click the cell and choose **Table > Group by selected
column**. Use **Data > Table > Clear grouping** or **Table > Clear grouping**
to remove grouping.

Structured table references are available in formulas:
`=SUM(Expenses[Amount])`, `=COUNTA(Expenses[#Headers])`,
`=COUNT(Expenses[#Data])`, and `Expenses[#All]`.

**List tables:**
```bash
xapps tables "Budget"
```

**Add a table:**
```bash
xapps add-table "Budget" '{"name":"Expenses","rangeStart":"A1","rangeEnd":"C20","groupBy":["Category"]}'
# Output: expenses
```

**Get one table:**
```bash
xapps table "Budget" expenses
```

**Update a table:**
```bash
xapps update-table "Budget" expenses '{"style":"banded","groupBy":["Category","Owner"]}'
# Output: Table expenses updated
```

**Sort a table body by a header column:**
```bash
xapps sort-table "Budget" expenses "Amount" --direction desc
# Output: Table expenses sorted by Amount
```

Sorting only reorders table body rows. The header row is preserved.

**Read grouped records and summaries:**
```bash
xapps table-groups "Budget" expenses
xapps table-groups "Budget" expenses --columns Category,Owner
```

Grouped responses include records plus a summary with `count` and numeric
column `sums`.

**Delete a table:**
```bash
xapps delete-table "Budget" expenses
# Output: Table expenses deleted
```

#### Sparklines

**Set a sparkline formula:**
```bash
xapps set-sparkline "Budget" F2 B2:B12 --type bar
# Output: F2 = =SPARKLINE(B2:B12, "bar")
```

#### Merge/Unmerge

**Merge a range:**
```bash
xapps merge "Budget" A1:C1
# Output: Merged A1:C1
```

**Unmerge a range:**
```bash
xapps unmerge "Budget" A1:C1
# Output: Unmerged A1:C1
```

#### Layout

**Set column width:**
```bash
xapps set-column-width "Budget" A 200
# Output: Column A width set to 200
```

**Set row height:**
```bash
xapps set-row-height "Budget" 1 40
# Output: Row 1 height set to 40
```

**Freeze panes:**
```bash
xapps freeze-panes "Budget" 1 2
# Output: Frozen 1 row(s) and 2 column(s)
```
The two numeric arguments are counts: frozen rows first, frozen columns second.
Use zero for either side when only rows or only columns should stay pinned.

**Unfreeze panes:**
```bash
xapps unfreeze-panes "Budget"
# Output: Frozen panes removed
```

#### CSV Import/Export

**Import CSV:**
```bash
xapps import-csv "Budget" /path/to/data.csv
# Output: Imported CSV into Budget from /path/to/data.csv (150 lines)
```

**Export CSV:**
```bash
xapps export-csv "Budget"
# Output: (CSV rows printed to stdout)

xapps export-csv "Budget" --range A1:C10 --out export.csv
# Output: Exported 10 rows to export.csv
```

#### Excel Import/Export

Import and export Excel `.xlsx` files from the **File** menu (**Import Excel/ODS...** / **Export Excel...**) in the UI. Round-trip fidelity is best-effort: cell values, basic formats, and formulas are preserved; advanced workbook-native features such as smart chips, saved filter views, slicers, protected ranges, threaded comments, and pivot/table metadata need review after interchange.

#### Import/Export Fidelity

Use **Spreadsheet > Open > Import/export fidelity...** before sending a sheet to another app. The panel scans the active Spreadsheet and shows:

- A recommendation for the safest interchange path.
- Counts for formulas, formats, rules, tables, charts, rich cells, and comments.
- Format-specific expectations for `.xss`, `.xlsx`, `.ods`, `.csv`, `.tsv`, and PDF.
- Import actions for file import, opening a saved sheet copy, or replacing the current sheet.
- Export actions for XLSX, ODS, CSV, TSV, and PDF.

Use `.xss` workbook copies for lossless xApps round-trip. Use XLSX/ODS for spreadsheet interchange when formulas and basic layout matter. Use CSV/TSV for plain grid values only. Use PDF when the target is review or printing rather than editable data.

Agents can request the same report:

```bash
xapps fidelity-report "Budget"
xapps fidelity-report "Budget" --format tsv --json
```

#### Rich client file-fidelity boundary

XLSX/ODS package parsing and generation and PDF/print rendering remain rich client-side workflows because they require user-selected bytes, browser SheetJS, DOM/print layout, or an external office renderer. CSV import/export and the machine-readable fidelity report remain available to automation through `XAppsSpreadsheetClient.importCsv` / `exportCsv`, the matching CLI and agent tools, and `fidelity-report`. Keep `.xss` as the lossless source of truth; use the browser **File** menu and visually review XLSX/ODS/PDF handoff output.

#### Assistant Workflows

Use **Data > Assistant workflows...** to preview Spreadsheet-native actions over the selected range. The panel is deterministic and confirmation-based: it inspects headers, values, formulas, blanks, numeric columns, and common values, then proposes a concrete action. Read-only workflows explain or summarize the range. Write workflows require pressing **Apply** and use the same protected-range checks as other Spreadsheet edits.

Supported workflows:

- Create table from the selected range.
- Suggest formulas such as `SUM`, `AVERAGE`, `COUNT`, `MIN`, or `MAX` into a target cell.
- Explain a range or summarize insights, including numeric totals and common values.
- Clean data with trim whitespace, duplicate detection/removal, or split text to columns.
- Build chart and pivot metadata from inferred label/value columns.
- Add dropdown or checkbox-style validation.
- Apply conditional formatting to inferred numeric columns.
- Sort/filter the selected data range.

Use **Data > Pivot table...** for the AI Pivot Analyst. The panel infers the selected table, runs a source preflight, generates an editable pivot plan from a prompt, previews the result without writing to the workbook, and then **Apply to grid** writes the pivot output into the grid, closes the panel, selects the written output range, and persists the AI plan metadata with the workbook.

After a pivot exists, reopen the panel from a pivot output cell to use the workflow actions: preview/apply source repairs, preview/apply a refinement prompt, explain the selected pivot value from source rows, refresh dependent pivots, save or suggest reusable pivot recipes, preview a source model, create or publish a dashboard block, and save AI governance metadata for recovery/audit.

Agents and scripts can preview or apply the same proposals:

```bash
xapps spreadsheet-assistant-preview "Budget" summarize-insights A1:D20 --json
xapps spreadsheet-assistant-preview "Budget" suggest-formula A1:D20 --aggregate sum --target E21 --json
xapps run-spreadsheet-assistant "Budget" create-table A1:D20 --table "Budget table" --confirm
xapps run-spreadsheet-assistant "Budget" add-dropdown D2:D20 --items "Ready,Blocked,Done" --confirm
```

#### Data Cleanup

Use **Data > Data cleanup...** to preview cleanup changes before applying them to the selected range. The panel supports:

- Trim whitespace with optional inner-whitespace collapse.
- Detect duplicates by all selected columns or a comma-separated key column list.
- Remove duplicates while keeping the first matching row and compacting unique rows inside the selected range.
- Split text to columns with comma, semicolon, tab, space, or custom delimiters.

Applied cleanup batches are pushed onto the Spreadsheet undo stack. Agents and scripts can use the same cleanup engine through the CLI or REST API:

```bash
xapps data-cleanup "Budget" trim-whitespace A2:D200 --apply
xapps data-cleanup "Budget" detect-duplicates A1:D200 --keys A,B --has-header --json
xapps data-cleanup "Budget" remove-duplicates A1:D200 --keys A,B --has-header --apply
xapps data-cleanup "Budget" split-text-to-columns C2:C200 --delimiter comma --apply
```

#### External Data Connectors & Scheduled Refresh

Use **Data > External data...** to create workbook-scoped connected data sources, preview query output, refresh extracts into the grid, cancel the next refresh, and inspect schedule, permission, and audit metadata. Supported deterministic connectors are:

- Inline JSON arrays of objects or array tables.
- Pasted CSV text with a header row.
- Same-workbook ranges using the first row as headers.

External data sources can filter, sort, select columns, limit rows, and add calculated columns (`concat`, `add`, `subtract`, `multiply`, `divide`, `uppercase`, `lowercase`, and `literal`). Refresh writes are added to the Spreadsheet undo stack in the browser, protected ranges are enforced server-side, and optional confirmation gates write blocked/success/cancelled audit entries. The scheduled-refresh fields are stored as metadata for automation; they do not fetch arbitrary URLs from the server.

Agents and scripts can manage connected data sources through CLI or REST:

```bash
xapps spreadsheet-external-data-sources "Budget"
xapps create-spreadsheet-external-data-source "Budget" "Sales feed" '{"connectorType":"inline-json","source":{"text":"[{\"Product\":\"Desk\",\"Revenue\":320}]"},"extract":{"targetRangeStart":"A1"}}'
xapps preview-spreadsheet-external-data-source "Budget" sales-feed
xapps refresh-spreadsheet-external-data-source "Budget" sales-feed --confirm
xapps cancel-spreadsheet-external-data-refresh "Budget" sales-feed
xapps delete-spreadsheet-external-data-source "Budget" sales-feed
```

#### Timeline Views

Use **Data > Timeline view...** to create Google Sheets-style timeline views from project tables or selected ranges. A timeline view stores a source range, field mappings for title/start/end/progress/status/group/color/assignee/id, grouping and color fields, print settings, and an optional target xApps Timeline sheet. The panel previews date bars directly in Spreadsheet and can print the current preview or export rows into a full Timeline sheet.

Date fields accept ISO dates, common date strings, or spreadsheet serial dates. Progress values accept numbers from 0-1, 0-100, or percent strings. Exported Timeline sheets use the existing xApps Timeline task column contract so downstream Timeline tools can read the generated tasks.

Agents and scripts can manage timeline views through CLI or REST:

```bash
xapps spreadsheet-timeline-views "Budget"
xapps create-spreadsheet-timeline-view "Budget" "Launch timeline" A1:H20 '{"title":"Task","start":"Start","end":"End","progress":"Progress","status":"Status","group":"Phase","color":"Status","assignee":"Owner","id":"Id"}' --group-by Phase --color-by Status --scale week --target-sheet "Launch Timeline"
xapps preview-spreadsheet-timeline-view "Budget" launch-timeline
xapps export-spreadsheet-timeline-view "Budget" launch-timeline --target-sheet "Launch Timeline"
xapps delete-spreadsheet-timeline-view "Budget" launch-timeline
```

#### Macro Recorder & Script Automation

Use **Data > Macros & scripts...** to record changes in the selected range, save the current selection as a reusable macro, run saved macros, and inspect safe script-hook metadata plus recent audit results. Spreadsheet macros use declarative xApps macro JSON instead of arbitrary browser code. Supported steps are:

- Set a cell value and safe formatting keys.
- Clear a cell.
- Run a data-cleanup operation.

Macro records also include trigger metadata (`manual`, `on-edit`, `on-open`, or `schedule`), optional confirmation gates, allowed-editor metadata, last-run state, run count, and a bounded audit log. Protected ranges are enforced before a macro mutates cells. Browser runs are added to the Spreadsheet undo stack.

Agents and scripts can manage the same macro records through CLI or REST:

```bash
xapps spreadsheet-macros "Budget"
xapps create-spreadsheet-macro "Budget" "Fill report" '[{"type":"set-cell","ref":"A1","value":"Report"}]' --require-confirmation
xapps run-spreadsheet-macro "Budget" fill-report --confirm
xapps delete-spreadsheet-macro "Budget" fill-report
```

#### Version History & Range Review

Use **Data > Version history & range review...** or right-click a selection and choose **Review range history...** to compare the selected range with a saved workbook version. The panel shows named versions, author attribution, changed cell counts, changed ranges, a hide/show unchanged rows toggle, selected-range restore, sheet restore, and a make-copy action.

```bash
xapps spreadsheet-version-review "Budget.json" "2026-07-04T06-10-00-000Z" "Budget" A1:F40
xapps name-version "Budget.json" "2026-07-04T06-10-00-000Z" "Quarter close baseline"
xapps restore-version-range "Budget.json" "2026-07-04T06-10-00-000Z" "Budget" B2:D20
xapps make-version-copy "Budget.json" "2026-07-04T06-10-00-000Z" "Budget baseline copy"
```

#### Paste Special

When pasting from the clipboard, the **Edit** menu provides two targeted paste modes:

- **Paste values only** — pastes evaluated cell values, stripping all formulas and formatting
- **Paste formatting only** — applies source formatting to the target cells without changing values

#### Clear Sheet

**Erase all cell data:**
```bash
xapps clear-sheet "Budget"
# Output: Sheet "Budget" cleared -- all cells and merges removed
```

---

### API Endpoints

All endpoints are relative to the server URL (e.g., `$XAPPS_API_BASE_URL`).

```bash
# Read a cell as stored
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Budget/cells/A1

# Read a formula cell as an evaluated value, with rawValue carrying the stored formula
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Budget/cells/A1?evaluate=1

# Write a cell
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Budget/cells/A1 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"value":"=SUM(B2:B20)"}'

# Delete/clear a cell
curl -X DELETE -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Budget/cells/A1

# Read a range
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Budget/range/A1:C5

# Write a range (bulk)
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Budget/range/A1:C3 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"data":[["Name","Q1","Q2"],["Alice",1500,1800]]}'

# Format a cell
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Budget/cells/A1/format \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"bold":true,"color":"#d93025"}'

# Format a range
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Budget/range/A1:C1/format \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"bold":true,"bg":"#e8f0fe"}'

# Set cell validation
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Budget/cells/B2/validation \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"type":"list","items":["Yes","No"],"showDropdown":true,"reject":true}'

# Get conditional formats
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Budget/conditional-formats

# Add conditional format rule
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Budget/conditional-formats \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"rangeStart":"B2","rangeEnd":"B50","condition":"greater","value":"1000","bgColor":"#d4edda","textColor":"#155724","enabled":true}'

# Set cell comment
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Budget/cells/A1/comment \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"comment":"Needs review"}'

# Set cell image
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Budget/cells/D5/image \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"src":"https://example.com/logo.png","fit":"contain"}'

# List charts
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Budget/charts

# Add a chart
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Budget/charts \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"type":"bar","range":"A1:B10","title":"Revenue"}'

# Add a structured table
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Budget/tables \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"name":"Expenses","rangeStart":"A1","rangeEnd":"C20","groupBy":["Category"]}'

# Sort the table body by a named header column
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Budget/tables/expenses/sort \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"column":"Amount","direction":"desc"}'

# Read grouped table records and summaries
curl -H 'X-XApps-File: MyWorkbook.json' \
  "$XAPPS_API_BASE_URL/api/sheets/Budget/tables/expenses/groups"

# Merge a range
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Budget/merge \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"startRow":0,"startCol":0,"endRow":0,"endCol":2}'

# Import CSV
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Budget/csv \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: text/csv; charset=utf-8" \
  --data-binary @data.csv

# Export CSV
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Budget/csv

# Export CSV with range filter
curl -H 'X-XApps-File: MyWorkbook.json' "$XAPPS_API_BASE_URL/api/sheets/Budget/csv?range=A1:C10"

# Import TSV
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Budget/tsv \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: text/tab-separated-values; charset=utf-8" \
  --data-binary @data.tsv

# Export TSV with range filter
curl -H 'X-XApps-File: MyWorkbook.json' "$XAPPS_API_BASE_URL/api/sheets/Budget/tsv?range=A1:C10"

# Preview data cleanup
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Budget/cleanup/preview \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"operation":"remove-duplicates","range":"A1:D200","keyColumns":["A","B"],"hasHeader":true}'

# Apply data cleanup
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Budget/cleanup/apply \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"operation":"trim-whitespace","range":"A2:D200"}'

# Create a safe Spreadsheet macro
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Budget/macros \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"name":"Fill report","permissions":{"requireConfirmation":true},"steps":[{"type":"set-cell","ref":"A1","value":"Report","format":{"bold":true,"bg":"#e8f0fe"}}]}'

# Run a Spreadsheet macro
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Budget/macros/fill-report/run \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"acknowledgePermissions":true}'

# Update sheet settings (freeze panes, column widths, row heights)
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Budget/settings \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"freezeRows":1,"freezeCols":1,"colWidths":{"A":200},"rowHeights":{"0":40}}'
```

---

### Agent/AI Workflow Recipes

Choose the authorized saved workbook and its actual storage target before running the examples. Set `XAPPS_API_BASE_URL` to that host. This helper keeps every operation in the same scope (replace the example file and `local` together when needed):

```bash
xapps_scoped() {
  xapps --base-url "${XAPPS_API_BASE_URL:?Set the authorized host URL}" \
    --file 'MyWorkbook.json' --workbook-storage-target local "$@"
}
```

Use bounded ranges and a semantic batch for related values, formulas and formatting; do not issue one network request per cell for bulk authoring.

```bash
xapps_scoped spreadsheet batch-state "Q1 Budget" --json
# Set BUDGET_REVISION to the returned revision.
xapps_scoped spreadsheet batch "Q1 Budget" \
  '{"ops":[{"op":"spreadsheet.setrange","range":"A1:B3","data":[["Category","Amount"],["Travel",1200],["Supplies",300]]},{"op":"spreadsheet.setcell","ref":"B4","value":"=SUM(B2:B3)"},{"op":"spreadsheet.formatrange","range":"A1:B1","format":{"bold":true}}]}' \
  --expected-revision "$BUDGET_REVISION" --request-id budget-seed-1 --json
xapps_scoped get "Q1 Budget" B4 --json
xapps_scoped export-csv "Q1 Budget" --range A1:B4 --out q1-budget-final.csv
```

These amounts illustrate the schema; replace them with validated source values before creating a real report. The supported batch operations are defined by `SpreadsheetBatchOperation` and `spreadsheet-batch-transactions.ts`; validation, charts and other commands are not implicitly batch operations. Read back stored formulas and their computed values through the advertised read contracts, and check the final bounded export. Keep the exact payload, expected revision and request ID after uncertain delivery; retry that same intent. On a revision conflict, reread and reconcile before creating a new intent and request ID.

### Troubleshooting

**1. Formula returns `#ERROR!`**
Check that all arguments are provided and of the correct type. For GEO functions, ensure you pass exactly 4 numeric coordinates. For VLOOKUP, make sure the key exists in the first column of the range.

**2. Cross-sheet reference returns empty**
Verify the sheet name is exactly correct (case-sensitive) and enclosed in single quotes if it contains spaces: `='My Sheet'!A1`. Also verify the referenced sheet exists in the workbook.

**3. Conditional formatting not showing**
Ensure the rule is enabled (`"enabled": true`). Check that the range (`rangeStart` / `rangeEnd`) actually covers the cells you expect. Use `xapps conditional-formats "Sheet"` to inspect existing rules.

**4. Validation dropdown not appearing**
Set `"showDropdown": true` in the validation JSON. For dependent dropdowns, make sure `dependsOnRef` references a valid column letter (e.g., `"A"`) and that `optionsByValue` keys match the actual values in that column.

**5. Sparkline not rendering**
Sparklines need numeric data in the referenced range. If cells contain text or are empty, the sparkline may not display. Check the range reference is valid and contains numbers.

**6. CSV import overwrites data**
CSV import replaces the sheet contents starting from A1. If you need to append data, use `bulk-set` with a start reference below existing data instead.

**7. Merged cells cause formula issues**
Formulas referencing a merged range may only see the top-left cell's value. Unmerge before running calculations that need individual cell values.

**8. Frozen panes not visible**
Freeze panes only take effect when you scroll. If you freeze 1 row, scroll down to see row 1 stay pinned. Use `xapps freeze-panes "Sheet" 0 0` or `unfreeze-panes` to reset.

---

### Status Bar

The status bar at the bottom of the spreadsheet shows live statistics for the current selection. When multiple cells are selected, the status bar displays:

- **Count** -- number of non-empty cells in the selection
- **Sum** -- sum of all numeric values
- **Average** -- mean of all numeric values
- **Median** -- median of all numeric values
- **Min** and **Max** -- smallest and largest numeric values

For a single cell, the status bar shows the cell reference and zoom controls. The status bar can be hidden via the View menu.

---

### Tips and Tricks

- **Quick formula insertion:** Use the function browser (toolbar) to search all 40+ functions by name or category, then double-click to insert.
- **Click-to-reference:** While editing a formula, click any cell or drag a range to insert its reference automatically.
- **Sparkline colors:** Use the SPARKLINE argument suggestions that appear while typing -- built-in colors include Blue (#1a73e8), Green (#0f9d58), Red (#d93025), Orange (#f9ab00), and Purple (#9334e6).
- **GEO formulas in spreadsheets:** You can calculate distances and bearings between GPS coordinates without leaving the spreadsheet. Combine with Map sheet data for powerful spatial analysis.
- **Virtual scrolling:** Sheets with 250+ rows automatically enable virtual scrolling for smooth performance. You should not notice any difference in behavior.
- **Alternating row colors:** Toggle this from the formatting menu for improved readability on data-heavy sheets.
- **Row detail view:** For sheets with many columns, the row detail view provides a vertical form layout so you can see all fields for a single row without horizontal scrolling.
- **Bulk operations:** When populating a sheet programmatically, prefer `bulk-set` over individual `set` calls -- it is significantly faster for large datasets.

### Named Ranges

Named ranges are workbook-scoped pointers to a sheet+range, so formulas can reference `Revenue` instead of `'Q1 Sales'!B2:B25`. Useful when:

- A cross-sheet formula would otherwise embed a fragile cell range that breaks the moment someone inserts a row.
- Multiple sheets need to share the same lookup table; a single name is easier to update than every reference.
- You want self-documenting formulas (`=SUMIF(Region,"West",Sales)` reads better than `=SUMIF('Data'!A2:A100,"West",'Data'!E2:E100)`).

CLI:

```bash
xapps named-ranges                                # list all workbook-scoped named ranges
xapps set-named-range <name> <sheet> <range>      # create or update a named range
xapps delete-named-range <name>                   # remove a named range
```

Names follow the standard rules: must start with a letter, max 64 chars, no spaces or punctuation outside underscore. Names that collide with reserved tokens (`Sheet1`, `A1`, function names) are rejected at create time. Updating a name is idempotent — re-running `set-named-range` with the same name overwrites the prior pointer.

### Named Functions

Named functions are workbook-scoped reusable formulas with named arguments and descriptions. They appear in the function picker and formula autocomplete, and formulas can call them like built-ins:

```text
=GROSS_MARGIN(revenue, cost)
```

CLI:

```bash
xapps named-functions                                      # list all workbook-scoped named functions
xapps set-named-function <name> <args-csv> <formula>       # create or update a named function
xapps set-named-function GROSS_MARGIN "revenue,cost" "=(revenue-cost)/revenue" --desc "Returns gross margin percent"
xapps delete-named-function <name>                         # remove a named function
```

Named function names and argument placeholders must start with a letter or underscore and may contain letters, digits, and underscores. The formula may be saved with or without a leading `=`.
