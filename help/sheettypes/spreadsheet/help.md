## Spreadsheets

### Grid work, formulas, and lightweight analysis

Spreadsheet sheets are the analytical core of xApps. They provide a full-featured grid for data entry, calculations, formatting, charting, and cross-sheet references. Every other sheet type in xApps stores its data as cells under the hood, so understanding spreadsheets is fundamental to mastering the entire platform.

> 🤖 Agent example: an agent can import a CSV, normalize headers, build formulas, apply validation, and leave a human-ready review sheet in the same workbook.

![Spreadsheet workspace with formulas, summaries, and formatted tracker rows](/help-assets/screenshots/spreadsheet-sheet.png)

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
- CSV import and export
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

---

### Formatting and Structure

#### Text Formatting

Use the toolbar or context menu for:
- **Bold**, **Italic**
- Text color (24 swatches + custom)
- Background/fill color (24 swatches + clear option)
- Text alignment (left, center, right)
- Text wrap
- Number formats (general, number, currency, percentage, date, etc.)

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
  "dependsOn": "A",
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
- **Find and Replace** within the sheet
- **Fill handles** for range autofill
- **Row detail view** -- form-style editor for wide sheets with many columns
- **Sort** by column values

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
| `Ctrl/Cmd` + `C` | Copy |
| `Ctrl/Cmd` + `V` | Paste |
| `Ctrl/Cmd` + `B` | Bold |
| `Ctrl/Cmd` + `I` | Italic |

---

### CLI Commands

All commands use the pattern:
```
xapps <command> --file <WorkbookName>
```

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
without creating table metadata. To group records, right-click a cell in the
table column you want to group by, then choose **Table > Group by selected
column**. Use **Table > Clear grouping** to remove grouping.

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

# Update sheet settings (freeze panes, column widths, row heights)
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Budget/settings \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"freezeRows":1,"freezeCols":1,"colWidths":{"A":200},"rowHeights":{"0":40}}'
```

---

### Agent/AI Workflow Recipes

#### Recipe 1: Build a formatted budget report from raw data

An AI agent receives a CSV of expense data and needs to create a polished budget sheet.

```bash
# Step 1: Import the raw CSV
xapps import-csv "Q1 Budget" /tmp/expenses.csv

# Step 2: Add a SUM formula at the bottom
xapps set "Q1 Budget" B25 "=SUM(B2:B24)"

# Step 3: Add a header with formatting
xapps range-format "Q1 Budget" A1:D1 '{"bold":true,"bg":"#1a73e8","color":"#ffffff"}'

# Step 4: Add conditional formatting to flag high expenses
xapps add-conditional-format "Q1 Budget" '{"rangeStart":"B2","rangeEnd":"B24","condition":"greater","value":"5000","bgColor":"#f8d7da","textColor":"#721c24","bold":true,"enabled":true}'

# Step 5: Freeze the header row
xapps freeze-panes "Q1 Budget" 1 0

# Step 6: Add a bar chart of expenses
xapps add-chart "Q1 Budget" '{"type":"bar","range":"A1:B24","title":"Q1 Expenses by Category"}'

# Step 7: Export a clean copy
xapps export-csv "Q1 Budget" --out /tmp/q1-budget-final.csv
```

#### Recipe 2: Set up a validated data entry form

An agent needs to create a structured sheet where users pick from dropdowns and values are validated.

```bash
# Step 1: Set column headers
xapps bulk-set "Order Form" A1 '[["Department","Amount","Status","Priority"]]'
xapps range-format "Order Form" A1:D1 '{"bold":true}'

# Step 2: Set column types
xapps col-type "Order Form" 0 '{"type":"single-select","options":["Engineering","Marketing","Sales"]}'

# Step 3: Add validation on Amount (must be 0-10000)
for row in $(seq 2 50); do
  xapps set-validation "Order Form" B${row} '{"type":"number","cond":"between","min":0,"max":10000,"reject":true}'
done

# Step 4: Add dependent dropdown -- Priority depends on Department
for row in $(seq 2 50); do
  xapps set-validation "Order Form" D${row} '{"type":"list","dependsOn":"A","optionsByValue":{"Engineering":["P0","P1","P2"],"Marketing":["High","Medium","Low"],"Sales":["Urgent","Normal"]},"fallbackItems":["Normal"],"showDropdown":true,"reject":true}'
done
```

#### Recipe 3: Cross-sheet dashboard with sparklines

An agent aggregates data from multiple sheets into a summary view.

```bash
# Step 1: Create summary headers
xapps bulk-set "Summary" A1 '[["Sheet","Total","Avg","Trend"]]'
xapps range-format "Summary" A1:D1 '{"bold":true,"bg":"#e8f0fe"}'

# Step 2: Add cross-sheet formulas
xapps set "Summary" A2 "Q1 Revenue"
xapps set "Summary" B2 "=SUM('Q1 Revenue'!B2:B100)"
xapps set "Summary" C2 "=AVERAGE('Q1 Revenue'!B2:B100)"
xapps set-sparkline "Summary" D2 "'Q1 Revenue'!B2:B13" --type bar

xapps set "Summary" A3 "Q2 Revenue"
xapps set "Summary" B3 "=SUM('Q2 Revenue'!B2:B100)"
xapps set "Summary" C3 "=AVERAGE('Q2 Revenue'!B2:B100)"
xapps set-sparkline "Summary" D3 "'Q2 Revenue'!B2:B13" --type bar

# Step 3: Format currency columns
xapps range-format "Summary" B2:C3 '{"format":"currency","decimals":2}'
```

---

### Troubleshooting

**1. Formula returns `#ERROR!`**
Check that all arguments are provided and of the correct type. For GEO functions, ensure you pass exactly 4 numeric coordinates. For VLOOKUP, make sure the key exists in the first column of the range.

**2. Cross-sheet reference returns empty**
Verify the sheet name is exactly correct (case-sensitive) and enclosed in single quotes if it contains spaces: `='My Sheet'!A1`. Also verify the referenced sheet exists in the workbook.

**3. Conditional formatting not showing**
Ensure the rule is enabled (`"enabled": true`). Check that the range (`rangeStart` / `rangeEnd`) actually covers the cells you expect. Use `xapps conditional-formats "Sheet"` to inspect existing rules.

**4. Validation dropdown not appearing**
Set `"showDropdown": true` in the validation JSON. For dependent dropdowns, make sure `dependsOn` references a valid column letter (e.g., `"A"`) and that `optionsByValue` keys match the actual values in that column.

**5. Sparkline not rendering**
Sparklines need numeric data in the referenced range. If cells contain text or are empty, the sparkline may not display. Check the range reference is valid and contains numbers.

**6. CSV import overwrites data**
CSV import replaces the sheet contents starting from A1. If you need to append data, use `bulk-set` with a start reference below existing data instead.

**7. Merged cells cause formula issues**
Formulas referencing a merged range may only see the top-left cell's value. Unmerge before running calculations that need individual cell values.

**8. Frozen panes not visible**
Freeze panes only take effect when you scroll. If you freeze 1 row, scroll down to see row 1 stay pinned. Use `xapps freeze-panes "Sheet" 0 0` or `unfreeze-panes` to reset.

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
