# 📚 xApps Help Center

xApps is a workbook for people and AI agents whose work does not fit into a single surface. One file can hold a spreadsheet for numbers, a kanban board for workflow, a calendar for timing, a document for notes, a canvas for polished visuals, and a whiteboard for fast thinking. Instead of bouncing between separate tools, you keep the whole project in one place, let the sheets reference each other, and let human and machine workflows operate on the same saved workbook.

### Why xApps feels different

- Build one workbook that mixes planning, analysis, documentation, design, and presentation work.
- Move between structured sheets and freeform surfaces without breaking context.
- Keep related work together so formulas, references, and people stay aligned.
- Give humans and AI agents the same operating model through the UI, CLI, API, MCP, and workbook-native automations.
- Start simple with one tab, then grow into a multi-surface system when the project gets more complex.

### A good first mental model

Think of xApps as a project space, not just a spreadsheet. A typical workbook might include:

| Surface | What it does |
|---|---|
| Spreadsheet | Budgets, estimates, trackers, calculations |
| Kanban | Tasks, approvals, pipelines |
| Calendar / Timeline | Deadlines, launches, planning windows |
| Document | Notes, SOPs, meeting writeups |
| Canvas / Whiteboard | Concepts, layouts, reviews, early thinking |
| Dashboard / Presentation | Readouts, status, storytelling |

### What to do in your first few minutes

1. Create or open a workbook.
2. Add two or three different sheet types, not just a spreadsheet.
3. Save the workbook as a real file so it can be reopened, shared, and clipped into.
4. Use `Ctrl/Cmd + K` to open the command palette and explore actions quickly.
5. Treat the workbook like a living project hub instead of a single-purpose document.

### Human + agent model

- Humans are best for judgment, review, and visual editing.
- Agents are best for scaffolding, bulk edits, imports, analysis, and repeatable setup.
- The workbook is the shared contract: people use the interface; agents use the CLI, API, MCP, triggers, processes, and agent actions.

### Where to go next

- Read **Welcome to xApps** for the practical quick start.
- Jump to a sheet type on the left if you already know what you want to build.
- Use the search box to find commands, features, or specific workflows fast.

## 👋 Welcome to xApps

xApps is a **multi-surface workbook**. Instead of opening a spreadsheet app, a whiteboard app, a slide app, a floor-plan tool, and a notes app separately, you keep them together in one workbook and let them reference each other.

> 🤖 Agent example: an agent can create a workbook with a spreadsheet, doc, kanban board, dashboard, and repository sheet in one pass, then hand the structured workspace to a human for review and editing.

### 🚀 Quick start

1. Use the **`+`** button or the **`Sheet`** menu to insert a new sheet.
2. Save your work as a real workbook file with **`File -> Save Workbook`** or **`Save Workbook As...`**.
3. Use the **top search bar** to search across sheets.
4. Use **`Ctrl/Cmd + K`** to open the command palette.
5. Use **sheet groups** if you want multiple related sheets to live under one parent tab.
6. On phones, use the **Sheets** pill in the bottom bar to switch sheets without relying on the tab strip.

### 🧩 Sheet types at a glance

| Icon | Sheet type | Best for |
|---|---|---|
| 📊 | Spreadsheet | Calculations, reporting, structured data |
| 🗃️ | Records | Typed tables, linked records, saved views, forms |
| 📋 | Kanban Board | Workflows, backlogs, approvals |
| 📅 | Calendar | Schedules, launches, editorial planning |
| 📈 | Timeline | Roadmaps, project timing, milestones |
| 📊 | Poll | Live votes, surveys, audience feedback |
| 🖼️ | Gallery | References, portfolios, catalogs |
| 🎨 | Design Canvas | Polished visual layouts on fixed artboards |
| 🧠 | Whiteboard | Brainstorming, mapping, ideation |
| 🎬 | Presentation | Decks, reviews, workshops |
| 🏠 | Floor Plan | 2D layout and space planning |
| 📊 | Dashboard | KPI and summary views |
| 📄 | Document | Notes, briefs, SOPs, wiki pages |
| ✍️ | Typewriter | Polished documents, rich text, page layout |
| 📁 | File Viewer | Preview Office documents, CAD files, PDFs |
| 🗄️ | Repository | Filesystem-backed document management |
| 🗺️ | Map | Choropleths, point layers, spatial views |
| 🎮 | Games | Built-in arcade games and high scores |

> 💡 Spreadsheet formulas can pull data from many other sheet types, so your workbook can act like one connected system instead of isolated tabs.

## 🏠 Home / Library

The Home page is your file manager for all xApps workbooks. Open it by clicking the **xApps logo** in the top-left corner of any workbook.

![Home / Library page showing workbook list, recent files, folders, and New Workbook button](/help-assets/screenshots/shell-home.png)

### Library layout

| Element | What it does |
|---|---|
| **Pinned** section | Star any workbook to keep it pinned at the top for quick access |
| **Recent** section | The 5 workbooks you opened most recently |
| **All files** section | Every workbook, sorted newest-modified first |
| **Folder sidebar** | Navigate into sub-folders; create folders with `+ New Folder` |
| **Trash** | Deleted workbooks land here; empty or restore from context menu |

### Working with workbooks

- **Open** — click the workbook name or the `Open` button to the right
- **Create** — click **New Workbook** (top-right) to open the workbook composer; choose a blank workbook or a starter-kit template
- **Pin / Unpin** — click the star icon on any workbook row
- **Rename** — right-click a workbook or click `···` to get the context menu; choose `Rename`
- **Move** — right-click a workbook and choose `Move to folder`; drag-and-drop is not available in the current version
- **Delete** — right-click and choose `Delete`; workbooks move to Trash, not permanent deletion
- **Restore** — open Trash, right-click a workbook, choose `Restore`
- **Permanently delete** — right-click in Trash to permanently delete a workbook

### Search in the Library

The search field at the top filters workbooks by name and sheet type as you type. It does not search workbook content — use **Search Across Sheets** for that.

### Multi-select

Click the checkbox that appears on hover to select multiple workbooks. A bulk-delete action appears in the toolbar when files are selected.

### Drag-and-drop import

Drag a `.json` workbook file from Finder/Explorer onto the Library page to import it directly.

### Presence dots

If multiple users are in the same room, small colored avatar dots appear on workbook cards that are open in another session.

## 🔝 Top Bar

The top bar is the main navigation chrome shared by every sheet in xApps.

![Top bar showing home link, workbook title, sheet tabs, menu bar, search, and right-side actions](/help-assets/screenshots/shell-topbar.png)

### Top-bar zones (left to right)

| Zone | What it contains |
|---|---|
| **Home link** | xApps logo (or workspace name) — click to return to the Library |
| **Workbook title** | Editable inline; click to rename; saves automatically on blur |
| **Save status indicator** | Shows "Live · FileName.json" when saved, or a modified indicator |
| **Sheet tabs** | One tab per sheet; click to switch; drag to reorder (inside the tab strip) |
| **`+` (Add sheet)** | Opens the sheet-type picker to add a new sheet |
| **Menu bar** | Workbook · Sheet · Edit · Insert · View · Data · Tools · (surface tab) · Help |
| **Search Across Sheets** | Full-text search across all sheet content; shortcut `Ctrl/Cmd + Shift + F` |
| **Assistant button** | Opens or closes the AI assistant side-panel |
| **Presence / account chip** | Shows live collaborator avatars; click your chip for account info |
| **Activity Feed** | Clock icon — chronological log of workbook changes |
| **Sheet Radar** | Satellite icon — cross-sheet dependency graph |
| **Cheat Sheet** | Book icon — context-sensitive shortcuts and storage format reference |
| **Settings** | Gear icon — opens the workspace settings pane |

### Responsive collapse

On narrow windows the menu bar collapses into a `···` overflow menu. All items remain accessible; nothing is hidden permanently.

### Sheet tabs

- **Click** a tab to switch to that sheet
- **Double-click** a tab to rename the sheet inline
- **Right-click** a tab for: rename, duplicate, move, convert, protect, delete
- **Grouped tabs** — a parent tab with a disclosure arrow expands to show child sheets; click the group tab to open a sheet picker
- **Mobile** — on small screens a **Sheets** pill appears in the bottom bar as a replacement for the tab strip

## 📋 Menu Bar

Every sheet in xApps renders the same canonical menu bar. Surface-specific entries appear in a dedicated tab named after the active surface (e.g., "Spreadsheet", "Canvas", "Kanban").

### Workbook menu

| Item | What it does |
|---|---|
| New Workbook | Create a new workbook (opens composer) |
| Open Workbook... | Load a workbook file from the library |
| Save Workbook | Save the current workbook (`Ctrl/Cmd + S`) |
| Save Workbook As... | Save a copy under a new name |
| Share Workbook | Set view / edit access for the saved file |
| Export | Export the workbook or active sheet |
| Workbook Properties | View and edit workbook-level metadata |

### Sheet menu

| Item | What it does |
|---|---|
| Insert Sheet | Add a new sheet (same as the `+` button) |
| Duplicate Sheet | Copy the active sheet |
| Rename Sheet | Rename inline |
| Move Sheet | Reorder relative to other sheets |
| Convert Sheet | Change the sheet type (where supported) |
| Sheet Groups | Group multiple sheets under one parent tab |
| Protect Sheet... | Lock the sheet with a password |
| Delete Sheet | Remove the sheet (irreversible without undo) |
| Configure Sheet Types... | Show or hide sheet types in the `+` picker |

### Edit menu

Standard clipboard and selection actions apply across all surfaces: **Undo** (`Ctrl/Cmd + Z`), **Redo** (`Ctrl/Cmd + Y`), **Cut**, **Copy**, **Paste**, **Duplicate**, **Select All**, **Deselect All**. Surface-specific additions appear below the baseline items.

### Insert menu

Surface-specific. For spreadsheets: rows, columns, charts, images, functions. For canvas/whiteboard: shapes, text, images, sticky notes. For presentations: slides, text boxes, shapes. Refer to the sheet-type sections for details.

### View menu

Controls visibility and display mode for the active surface: zoom controls, grid lines, rulers, full-screen, dark style toggle, and surface-specific view modes (e.g., board vs. list for Kanban, week/month/day for Calendar).

### Data menu

Spreadsheet-specific: filter rules, sort, Find & Replace, data validation, conditional formatting, and freeze rows/columns. Other sheet types expose relevant data tools here (e.g., import for Gallery, filter for Records).

### Tools menu

| Item | What it does |
|---|---|
| Automations... | Create and run workbook-native macros |
| Triggers... | Manage reactive rules and background processes |
| Agent Actions... | Manage right-click context menu agent actions |
| Diagnostics | Open the diagnostics pane |

### Help menu

Links to the Help Center (this document), keyboard shortcuts, and release notes.

## ➕ New Sheet Picker

Click the **`+`** button at the left of the sheet tab strip to open the sheet-type picker.

![The + New sheet picker showing Work, Design, Insight, and Files categories](/help-assets/screenshots/shell-add-sheet.png)

Sheet types are grouped into categories:

| Category | Sheet types |
|---|---|
| **Work** | Spreadsheet, Wiki/Doc, Typewriter, Kanban, Timeline, Calendar, Records |
| **Design** | Canvas, Whiteboard, Gallery, Floor Plan, Slides/Presentation |
| **Insight** | Dashboard, Map |
| **Files** | Repository, File Viewer |
| **Play** | Games |

- **Default sheet type** is highlighted; change it in Settings → Defaults
- **Configure visible types** — click `Configure visible types...` at the bottom to show or hide types from the list
- Click any type to immediately insert a new sheet of that type

## ⚙️ Settings Pane

Open Settings with the **gear icon** in the top-right corner of any workbook.

![Settings pane showing My Preferences and Workspace sections](/help-assets/screenshots/shell-settings.png)

Settings are divided into two scopes:

- **My Preferences** — per-user settings stored against your account; apply only to you
- **Workspace** — admin settings that apply to everyone in the room

### My Preferences: Appearance

| Setting | Options | Effect |
|---|---|---|
| **Density** | Comfortable / Compact | Controls row height and padding throughout the app |
| **Reduce motion** | Off / On | Minimizes transitions and animations globally |

### My Preferences: Defaults

| Setting | Options | Effect |
|---|---|---|
| **Default sheet type** | Records, Spreadsheet, Kanban, Canvas, Doc, Dashboard, Gallery, Calendar | Pre-selected type in the `+` sheet picker |
| **Landing view** | Last workbook / Library | Where xApps opens when you arrive |

### My Preferences: Regional

| Setting | Options | Effect |
|---|---|---|
| **Time zone** | Browser default, US zones, UTC, Europe, Tokyo | Used for dates, timestamps, and calendar events |
| **Date & number format** | Browser default, en-US, en-GB, de-DE, fr-FR, es-ES, pt-BR | Controls `Intl.DateTimeFormat` and `Intl.NumberFormat` output |
| **First day of week** | Sunday / Monday | Used for Calendar and Timeline views |

A live sample shows the current date/time and number `1,234,567.89` formatted with the active locale and time zone.

### My Preferences: Assistant

| Setting | Options | Effect |
|---|---|---|
| **Assistant panel on startup** | Open / Closed | Whether the AI assistant side-panel opens automatically |

### Workspace: Branding

| Setting | What it does |
|---|---|
| **Workspace name** | Text shown in the top-left instead of "XApps" |
| **Accent color** | Color picker that updates buttons and active controls across the entire app |

### Workspace: Storage

| Setting | What it does |
|---|---|
| **Default folder for new workbooks** | Sub-folder path under the workbook root where new files are filed |
| **Home workbook** | File that opens automatically when Landing view is set to last/home |
| **Default new-workbook template** | Template applied when creating a workbook without choosing one |
| **Host paths** | Read-only display: data dir, state file, workbook root, current workbook |

### Workspace: Housekeeping

| Setting | What it does |
|---|---|
| **Trash retention** | How long deleted workbooks stay in trash before purging (7/30/90 days or keep forever) |
| **Empty trash now** | Permanently removes all workbooks currently in the trash |

Admin-only controls show a lock indicator for non-admin users; the values are visible but not editable.

## 💬 Assistant Side-Panel

Click the **Assistant** button in the top bar (or its keyboard shortcut) to open the AI assistant side-panel.

![Assistant side-panel open alongside an active workbook](/help-assets/screenshots/shell-assistant.png)

The assistant answers questions in the context of the **current sheet**. Switching sheets marks a new context with a divider.

- Type a message and press `Enter` or click **Send**
- The assistant can read and describe sheet contents, suggest formulas, and help with CLI/API patterns
- **Admin can disable** the assistant workspace-wide via Settings → Assistant → Enabled/Disabled
- When disabled, the Assistant button is hidden for all users in the room

## 🔍 Search Across Sheets

Click **Search Across Sheets** in the top bar or press **`Ctrl/Cmd + Shift + F`** to search workbook content.

![Search Across Sheets field in the top bar](/help-assets/screenshots/shell-search.png)

- Searches text content in all sheets simultaneously
- Results are grouped by sheet
- Click a result to navigate to that sheet and location
- The Help Center has its own separate search for finding help topics

## ⚡ Command Palette (Shell)

Open with **`Ctrl/Cmd + K`** from anywhere in the app.

![Command palette dialog showing Workbook actions and sheet navigation](/help-assets/screenshots/shell-command-palette.png)

The command palette is the fastest way to access any action without navigating menus:

| Group | Items available |
|---|---|
| **Workbook** | Save workbook, Open workbook, New workbook, Starter kits, Share workbook, Sheet groups, Automations, Triggers, Agent Actions |
| **Sheets** | Jump directly to any sheet by name |
| **Recent** | Open recently accessed workbooks |
| **Templates** | Apply a starter kit to the current workbook |

Type to filter — the search matches action names and sheet names. Press `Enter` on the highlighted item or click it to run.

## 🕐 Activity Feed (Shell)

The Activity Feed is a chronological log of all changes across the workbook. Open it with the **clock icon** in the top bar.

Tracking starts paused by default. Click **Resume** to begin logging for the current session.

### Controls

- **Start / Stop** — toggle activity logging
- **Clear** — remove all recorded entries
- **Filter by sheet** — click a sheet-name chip to see only that sheet's activity

Each entry shows: sheet type icon, action name, detail text, sheet name, and timestamp. Entries are created for: sheet creation/deletion, card adds, event adds, widget adds, cell edits, and other surface mutations.

## 🛰️ Sheet Radar (Shell)

Sheet Radar shows a force-directed dependency graph of all sheets in the workbook. Open it with the **satellite icon** in the top bar.

- **Nodes** — colored circles, one per sheet, sized by content volume
- **Arrows** — point from the sheet containing the reference to the referenced sheet
- **Colors** — match the sheet type (spreadsheet = blue, kanban = orange, doc = purple, etc.)
- **Click a node** — navigates directly to that sheet
- **Hover an edge** — shows the specific cell references or widget connections creating the dependency

Sheet Radar detects cross-sheet formula references and dashboard widget data sources automatically.

## 📋 Cheat Sheet (Shell)

The Cheat Sheet is a context-sensitive quick-reference panel. Open it with the **book icon** in the top bar.

It updates automatically when you switch sheets. Contents vary by sheet type:

| Sheet type | Cheat Sheet shows |
|---|---|
| Spreadsheet | Cell reference format, formula syntax, shortcuts |
| Canvas / Whiteboard | Object types, keyboard shortcuts, tool tips |
| Gallery | Item storage format, field columns, formula pull patterns |
| Dashboard | Widget configuration, data source format |
| Presentation | Slide controls, object types |
| Floor Plan | Measurement units, tool shortcuts |
| Records | Table/field reference format, view types |

## 🔧 Diagnostics Pane (Shell)

Open Diagnostics from **Tools → Diagnostics** or from the command palette.

The Diagnostics pane is a read-only snapshot of the running server internals — useful for debugging deployments and verifying connectivity:

| Section | What it shows |
|---|---|
| **Runtime** | xApps version, Node version, platform, PID, hostname, uptime, memory (RSS, heap, external) |
| **Deployment** | App name, profile, deployment mode, NODE_ENV, host:port, public base URL |
| **Storage** | Data dir, state file, workbook root, current workbook file, workbook size |
| **Workbook** | Current file, title, revision, active sheet, sheet count, sheet types |
| **Collab** | Room name, number of connected users |
| **Surfaces** | List of registered sheet-type modules |
| **Environment** | Which environment variables are set/unset (values are redacted for security) |

## 📊 Spreadsheets

### Grid work, formulas, and lightweight analysis

Spreadsheet sheets are still the analytical core of xApps: data entry, calculations, formatting, reporting, and cross-sheet references all start here.

> 🤖 Agent example: an agent can import a CSV, normalize headers, write formulas, apply validation, flag outliers, and generate a summary range that other sheets consume.

### ✍️ Everyday editing

| Action | How |
|---|---|
| Type in a cell | Click a cell and start typing |
| Edit existing content | Double-click the cell, or press `F2` |
| Confirm and move down | `Enter` |
| Confirm and move right | `Tab` |
| Cancel editing | `Escape` |
| Select a range | Drag, or click + `Shift` click |

> 💡 Double-clicking a cell selects its content so you can replace it quickly.

### 🧠 Formulas, hints, and cross-sheet references

Every formula starts with `=`.

```text
=SUM(B2:B20)
=COUNTIF('Sprint Board'!B:B, "Done")
=IF(C2>100, "Over budget", "OK")
=SPARKLINE(E2:E20, "bar", "green")
```

Formula assist stays visible while you fill arguments, including for `SPARKLINE(...)`. xApps also lets you click cells and ranges while editing a formula to insert references directly.

### ✅ Smart cells and validation

Spreadsheet sheets support both **column field types** and **cell validation**:

- checkboxes
- single-select and multi-select tags
- dates
- ratings
- progress bars
- email / phone / number helpers
- list validation dropdowns
- number and text validation rules
- **conditional dropdowns** where one cell's options depend on another cell or column

Example dependent dropdown rule:

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

### 🎨 Formatting and structure

Use the toolbar or context menu for:

- text styling, alignment, wrap, and number formats
- borders and fills
- row heights and column widths
- merge / unmerge
- comments
- images in cells
- freeze rows / columns
- alternating row colors

### 📈 Visual analysis

Spreadsheet sheets now support all of the following directly:

- **Conditional formatting** for rules like `> 100`, `contains "overdue"`, `is empty`, and more
- **Charts** from the selected range
  - Bar
  - Line
  - Pie
  - Scatter
- **Chart placement**
  - Floating overlay
  - Anchored **in cells** using a target range
- **Sparklines** with `=SPARKLINE(...)`

Chart context menus let you rename, re-anchor, float, or delete a chart after insertion.

### 🔎 Data tools

- Filter rules now live in the toolbar
- Find & Replace works inside spreadsheet sheets
- Range formatting and fill handles are supported
- Row detail view gives you a form-style editor for wide sheets

### ⚡ Power examples

```text
=SUM('Construction Budget'!D2:D50)
=COUNTIF(A:A, "Overdue")
=SPARKLINE(F2:F12)
=SPARKLINE(F2:F12, "bar", "green")
```

## 📐 Formula Reference

This section documents every formula function available in xApps spreadsheets. All formulas begin with `=`. Cell references use the `A1` format. Ranges use `A1:B10` format. Cross-sheet references use `SheetName!A1` or `'Sheet Name'!A1` for names with spaces.

### Math Functions

| Function | Syntax | Description | Example | Result |
|---|---|---|---|---|
| SUM | `=SUM(range)` | Adds all numbers in a range | `=SUM(B2:B10)` | Sum of B2 through B10 |
| AVERAGE | `=AVERAGE(range)` | Arithmetic mean of numbers in a range | `=AVERAGE(C2:C20)` | Mean of C2 through C20 |
| MIN | `=MIN(range)` | Smallest number in a range | `=MIN(D2:D50)` | Smallest value |
| MAX | `=MAX(range)` | Largest number in a range | `=MAX(D2:D50)` | Largest value |
| COUNT | `=COUNT(range)` | Counts numeric cells in a range | `=COUNT(A2:A100)` | Number of numeric cells |
| COUNTA | `=COUNTA(range)` | Counts non-empty cells including text | `=COUNTA(A:A)` | Number of non-empty cells |
| ABS | `=ABS(value)` | Absolute value | `=ABS(-42)` | 42 |
| ROUND | `=ROUND(value, digits)` | Rounds to specified decimal places | `=ROUND(3.14159, 2)` | 3.14 |
| FLOOR | `=FLOOR(value)` | Rounds down to nearest integer | `=FLOOR(4.9)` | 4 |
| CEIL | `=CEIL(value)` | Rounds up to nearest integer | `=CEIL(4.1)` | 5 |
| CEILING | `=CEILING(value)` | Alias for CEIL | `=CEILING(4.1)` | 5 |
| POWER | `=POWER(base, exp)` | Raises base to a power | `=POWER(2, 10)` | 1024 |
| POW | `=POW(base, exp)` | Alias for POWER | `=POW(3, 3)` | 27 |
| SQRT | `=SQRT(value)` | Square root | `=SQRT(144)` | 12 |

### Finance Functions

| Function | Syntax | Description | Example | Result |
|---|---|---|---|---|
| PMT | `=PMT(rate, nper, pv, [fv], [type])` | Loan or annuity payment using a per-period rate | `=PMT(5%/12, 60, 30000)` | Monthly payment |
| PV | `=PV(rate, nper, pmt, [fv], [type])` | Present value | `=PV(0.05/12, 60, -566.14)` | Loan principal |
| FV | `=FV(rate, nper, pmt, [pv], [type])` | Future value | `=FV(0.05/12, 60, -100, 0)` | Savings balance |
| NPV | `=NPV(rate, value1, [value2], ...)` | Net present value | `=NPV(0.1, B2:B6)+B1` | Discounted cash flow |
| IRR | `=IRR(values, [guess])` | Internal rate of return | `=IRR(B1:B6)` | Periodic return rate |

### Text Functions

| Function | Syntax | Description | Example | Result |
|---|---|---|---|---|
| CONCAT | `=CONCAT(val1, val2, ...)` | Joins values into one string | `=CONCAT(A1, " ", B1)` | "John Smith" |
| CONCATENATE | `=CONCATENATE(val1, val2, ...)` | Alias for CONCAT | `=CONCATENATE("Hello", " ", "World")` | "Hello World" |
| LEN | `=LEN(text)` | Length of text string | `=LEN("xApps")` | 7 |
| UPPER | `=UPPER(text)` | Converts to uppercase | `=UPPER("hello")` | "HELLO" |
| LOWER | `=LOWER(text)` | Converts to lowercase | `=LOWER("HELLO")` | "hello" |
| TRIM | `=TRIM(text)` | Removes leading/trailing whitespace | `=TRIM("  hi  ")` | "hi" |
| LEFT | `=LEFT(text, [num_chars])` | Leftmost characters | `=LEFT("Spreadsheet", 6)` | "Spread" |
| RIGHT | `=RIGHT(text, [num_chars])` | Rightmost characters | `=RIGHT("Spreadsheet", 5)` | "sheet" |
| MID | `=MID(text, start_num, num_chars)` | Characters from the middle of text | `=MID("Spreadsheet", 7, 5)` | "sheet" |

### Logic Functions

| Function | Syntax | Description | Example | Result |
|---|---|---|---|---|
| IF | `=IF(condition, then, else)` | Returns one value if true, another if false | `=IF(B2>100, "Over", "Under")` | "Over" if B2 > 100 |
| IFERROR | `=IFERROR(value, fallback)` | Returns fallback when value is an error | `=IFERROR(1/0, "n/a")` | "n/a" |
| AND | `=AND(value1, value2, ...)` | TRUE when all values are truthy | `=AND(A2>0, B2>0)` | TRUE/FALSE |
| OR | `=OR(value1, value2, ...)` | TRUE when any value is truthy | `=OR(A2>0, B2>0)` | TRUE/FALSE |
| TRUE | `=TRUE` | Boolean true constant | `=IF(TRUE, "Yes", "No")` | "Yes" |
| FALSE | `=FALSE` | Boolean false constant | `=IF(FALSE, "Yes", "No")` | "No" |

> **Tip:** Nested IF statements work: `=IF(A1>90, "A", IF(A1>80, "B", "C"))`

### Lookup Functions

| Function | Syntax | Description | Example | Result |
|---|---|---|---|---|
| VLOOKUP | `=VLOOKUP(search, range, col_index)` | Searches the first column of a range and returns a value from a specified column | `=VLOOKUP("Apple", A2:C10, 3)` | Value from column C in the row where column A equals "Apple" |
| INDEX | `=INDEX(range, row_num, [column_num])` | Returns a value by row and column position | `=INDEX(B2:D10, 3, 2)` | Value at row 3, column 2 |
| MATCH | `=MATCH(lookup_value, lookup_array, [match_type])` | Returns a matching position in a range | `=MATCH("Apple", A2:A10, 0)` | Matching row position |

VLOOKUP example in detail:

```text
# Given a table in A2:C10 with columns: Product, Category, Price
=VLOOKUP("Laptop", A2:C10, 2)   → returns the Category for "Laptop"
=VLOOKUP("Laptop", A2:C10, 3)   → returns the Price for "Laptop"
# Returns #N/A if the value is not found
```

### Conditional Aggregation Functions

| Function | Syntax | Description | Example | Result |
|---|---|---|---|---|
| COUNTIF | `=COUNTIF(range, criteria)` | Counts cells matching a criterion | `=COUNTIF(B:B, "Done")` | Number of "Done" cells in column B |
| SUMIF | `=SUMIF(range, criteria, sum_range)` | Sums cells where a corresponding range matches a criterion | `=SUMIF(A2:A10, "Food", B2:B10)` | Sum of B values where A equals "Food" |
| COUNTIFS | `=COUNTIFS(criteria_range1, criteria1, ...)` | Counts cells matching multiple criteria | `=COUNTIFS(A2:A10, "Food", C2:C10, ">100")` | Matching row count |
| SUMIFS | `=SUMIFS(sum_range, criteria_range1, criteria1, ...)` | Sums cells matching multiple criteria | `=SUMIFS(B2:B10, A2:A10, "Food", C2:C10, ">100")` | Matching sum |
| AVERAGEIF | `=AVERAGEIF(range, criteria, [average_range])` | Averages cells matching one criterion | `=AVERAGEIF(A2:A10, "Food", B2:B10)` | Matching average |
| AVERAGEIFS | `=AVERAGEIFS(average_range, criteria_range1, criteria1, ...)` | Averages cells matching multiple criteria | `=AVERAGEIFS(B2:B10, A2:A10, "Food", C2:C10, ">100")` | Matching average |

Criteria examples:

```text
=COUNTIF(B:B, "Done")           → exact text match
=COUNTIF(C:C, ">100")          → greater than 100
=COUNTIF(C:C, "<=50")          → less than or equal to 50
=SUMIF(A:A, "Rent", B:B)       → sum column B where column A is "Rent"
```

### Date and Time Functions

| Function | Syntax | Description | Example | Result |
|---|---|---|---|---|
| TODAY | `=TODAY()` | Returns the current date as a formatted string | `=TODAY()` | "4/10/2026" (locale-dependent) |
| NOW | `=NOW()` | Returns the current date and time as a formatted string | `=NOW()` | "4/10/2026, 2:30:00 PM" (locale-dependent) |
| DATE | `=DATE(year, month, day)` | Builds a date from year, month, and day | `=DATE(2026,4,29)` | "4/29/2026" (locale-dependent) |
| YEAR | `=YEAR(date)` | Year from a date | `=YEAR(DATE(2026,4,29))` | 2026 |
| MONTH | `=MONTH(date)` | Month from a date | `=MONTH(DATE(2026,4,29))` | 4 |
| DAY | `=DAY(date)` | Day from a date | `=DAY(DATE(2026,4,29))` | 29 |

### Sparkline Functions

| Function | Syntax | Description | Example | Result |
|---|---|---|---|---|
| SPARKLINE | `=SPARKLINE(range)` | Renders an inline mini line chart | `=SPARKLINE(B2:B12)` | Inline SVG chart |
| SPARKLINE | `=SPARKLINE(range, type, color)` | Renders a styled sparkline | `=SPARKLINE(B2:B12, "bar", "green")` | Green bar sparkline |

Sparkline types: `"line"` (default), `"bar"`.

### Geographic Functions

These functions are available in any spreadsheet cell and are part of the Map sheet integration.

| Function | Syntax | Description | Example | Result |
|---|---|---|---|---|
| GEO_DISTANCE | `=GEO_DISTANCE(lat1, lon1, lat2, lon2, unit)` | Haversine distance between two points. Unit is `"mi"` (default) or `"km"`. | `=GEO_DISTANCE(40.7128, -74.0060, 51.5074, -0.1278, "mi")` | ~3459 (miles NYC to London) |
| GEO_BEARING | `=GEO_BEARING(lat1, lon1, lat2, lon2)` | Initial compass bearing (0-360 degrees) from point 1 to point 2 | `=GEO_BEARING(40.7128, -74.0060, 51.5074, -0.1278)` | ~51.2 (degrees) |
| GEO_MIDPOINT | `=GEO_MIDPOINT(lat1, lon1, lat2, lon2)` | Geographic midpoint returned as `"lat,lon"` string | `=GEO_MIDPOINT(40.7128, -74.0060, 51.5074, -0.1278)` | "50.503,-35.667" |
| GEO_FORMAT | `=GEO_FORMAT(lat, lon, format)` | Formats coordinates. Format is `"dd"` (default), `"dms"`, or `"dm"`. | `=GEO_FORMAT(40.7128, -74.0060, "dms")` | 40°42'46.08"N 74°0'21.60"W |

### Cross-Sheet References

Reference cells in other sheets using the `!` separator:

```text
# Simple sheet name (no spaces)
=Budget!B2
=SUM(Budget!B2:B50)

# Sheet name with spaces (use single quotes)
='Q3 Report'!D5
=COUNTIF('Sprint Board'!B:B, "Done")

# Combine cross-sheet refs with functions
=IF(Budget!B2 > 1000, "Over budget", "OK")
=VLOOKUP("Laptop", Inventory!A2:C100, 3)
```

### Bare Column References

Inside formulas, bare column letters automatically expand to include the current row number. For example, in row 5:

```text
=A + B        → evaluates as =A5 + B5
=SUM(A, B, C) → evaluates as =SUM(A5, B5, C5)
```

This does not apply to range references like `A2:B10` or function names like `SUM`.

### Arithmetic Operators

Standard arithmetic works in any formula:

```text
=A1 + B1
=A1 * 1.08
=(A1 + B1) / 2
=A1 - B1
```

## 🗃️ Records

### Typed tables, linked records, and views

Records sheets are for structured operational data that needs stronger shape than a plain grid. Use them for CRMs, asset inventories, project databases, intake queues, audits, and any table where fields have types, relations, saved views, validation, and history.

> 🤖 Agent example: an agent can create records tables for accounts, contacts, and deals, add typed relation fields, seed sample records, build filtered views, and expose a form for human intake.

### Core model

- A records sheet can contain multiple tables.
- Each table has typed fields, keyed records, saved views, relation edges, and display preferences.
- Field types include text, long text, number, currency, percent, checkbox, date, datetime, email, URL, phone, rating, progress, single select, multi select, user, attachment, formula, relation, rollup, count, lookup, barcode, QR, and auto number.
- Views include grid, kanban, calendar, gallery, form, and query views.
- Deleted records are soft-deleted first and can be restored from the deleted-records route.

### Forms, queries, and linked data

- Form views collect new records from a user-facing layout without exposing the full grid.
- Relation fields link records across tables; rollup, count, and lookup fields summarize linked records.
- The query view supports SQL-style reads over records tables, including joins between related tables.
- Records can embed in docs, dashboards, and canvas cards so a workbook can show the same table data in multiple contexts.

### CLI, API, MCP, and toolkit coverage

Records are available through the UI, SDK, CLI, REST API, MCP, and the MeshAgent toolkit. Use `xapps help records` or `xapps search records --json` for the current command catalog.

## 📋 Kanban Boards

### Drag work across stages

Kanban sheets turn a workbook tab into a board with lists, cards, labels, due dates, notes, and sheet-specific card field layouts. They are best for sprint planning, content pipelines, approvals, CRM opportunity pipelines, and any workflow that moves from one state to another.

> 🤖 Agent example: an agent can create cards from a project brief, move stale work into a `Blocked` list, update due dates from a timeline change, and summarize blocked cards into a doc page.

### 🧱 Lists and cards

Common list setups:

- Backlog → In Progress → Review → Done
- Ideas → Drafting → Scheduled → Published
- Requested → Approved → Ordered → Installed

Each card can hold:

- title
- status / list
- description
- due date
- labels
- custom fields, such as start date, stop date, amount, account, stage, or probability

### 🧩 Card fields

Each kanban sheet can define its own card schema through the board's **Card fields** setting. Standard task fields can be hidden for that sheet, standard labels can be renamed through **Field labels**, and custom definitions live on the sheet as `kanbanCustomFields`. The visible layout is stored as `kanbanCardFieldLayout`; card values live on each card in `customFields`. This lets one board use normal task cards while another board uses CRM-style opportunity cards without changing the canonical stored columns.

Card fields are exposed through the Kanban REST API, SDK helpers, CLI commands, MCP tools, and MeshAgent toolkit tools. Use `xapps kanban-custom-fields <board>`, `xapps set-kanban-custom-fields <board> <json>`, `xapps kanban-card-field-layout <board>`, and `xapps set-kanban-card-field-layout <board> <json>` for CLI access.

### 🖱️ Core interactions

| Action | How |
|---|---|
| Add a card | Use the board controls or CLI/API |
| Move a card | Drag it between lists |
| Reorder cards | Drag within a list |
| Rename / recolor a list | List controls or context menu |
| Filter by status | Use machine-facing filters or formulas |

### 🎯 Why Kanban sheets matter in xApps

Behind the board, every card is still stored in sheet data. That means spreadsheet formulas can count, filter, and summarize the board:

```text
=COUNTIF('Sprint Board'!B:B, "Done")
=COUNTIF('Sprint Board'!E:E, "P1")
```

### ✅ Good uses

- sprint boards
- editorial calendars
- approvals pipelines
- hiring stages
- home project tasks
## 📅 Calendar

### Schedule work visually

Calendar sheets give you **Month**, **Week**, and **Day** views for events, deadlines, editorial schedules, launches, and personal planning.

> 🤖 Agent example: an agent can import an `.ics` feed, generate a launch calendar from spreadsheet dates, and keep milestone events aligned with timeline tasks.

### 🗓️ Views

| View | Best for |
|---|---|
| Month | Editorial planning, release calendars, due dates |
| Week | Time-blocking and team schedules |
| Day | Detailed daily planning |

The header gives you:

- previous / next navigation
- **Today**
- quick view switching

### ✍️ Events

Events can include:

- title
- date
- optional time
- description
- color

### 🔄 Import and sync

- Import `.ics` calendar files from Google Calendar, Apple Calendar, or Outlook
- Optional Chrome extension support exists for **Google Calendar → xApps** sync workflows

### 📊 Why calendar sheets are useful in a workbook

Calendar sheets are not isolated. You can summarize them from spreadsheet sheets:

```text
=COUNTIF('Launch Calendar'!A:A, "Launch")
```

Use them alongside:

- Kanban for work status
- Timeline for long-range planning
- Dashboard for reporting
## 📈 Timeline / Gantt Charts

### Plan work across time

Timeline sheets are for roadmaps, schedules, project plans, and milestone tracking. They render tasks as horizontal bars over time, with progress and date ranges.

> 🤖 Agent example: an agent can turn a spreadsheet task list into a dependency-aware project plan, assign owners, update progress from kanban status, and recalculate dependent dates.

### 🧩 Tasks

Typical task fields:

- title
- start date
- end date
- progress (0-100%)
- color
- assignee
- status

### 📊 Progress tracking

Each task bar displays a progress fill that reflects its completion percentage. Update progress through the task editor or via CLI.

### 🔗 Dependencies

Tasks can be linked with predecessor/successor relationships:

- **Drag-to-link** — drag from one task bar to another to create a dependency arrow
- **CLI** — use the `--depends` flag when creating or updating tasks
- Dependency arrows render as lines between the linked task bars

### ⚡ Auto-scheduling

When a predecessor task moves or changes duration, dependent tasks auto-shift to maintain the relationship. This keeps your plan consistent without manual date adjustments.

### 🖱️ Core interactions

| Action | How |
|---|---|
| Add a task | Timeline controls or machine-facing commands |
| Move a task | Drag the task bar horizontally |
| Resize a task | Drag the left or right handle to change start/end dates |
| Change progress | Edit the task data or drag the progress fill |
| Link tasks | Drag from one bar to another to create a dependency |
| Assign a task | Set the assignee field in the task editor |
| Change status | Set the status field in the task editor |

### ✅ Best uses

- product roadmap
- implementation plans
- campaign schedules
- construction phases
- workshop or event runbooks

### 🔗 Works well with

- Calendar for day-level scheduling
- Spreadsheet for budget or status rollups
- Dashboard for milestone summaries

## 📊 Poll

### Live questions, voting links, and results

Poll sheets turn a workbook tab into a live polling or survey surface. Authors configure questions and lifecycle state from the workbook; voters use a focused `?mode=vote` link with the surrounding workbook chrome locked down.

> 🤖 Agent example: an agent can scaffold a poll from an event brief, add choice, rating, ranking, and text questions, open voting, submit synthetic responses for a test run, then export the results.

### What Poll supports

- Question types for choice, multiple choice, rating, ranking, and text.
- Draft, open, and closed lifecycle states.
- Anonymous voting with cookie dedupe, or identified voting with `viewerId`.
- Optional result visibility before vote, after vote, after close, or always.
- CSV export and API/CLI/MCP access for setup, voting, and response reads.

### Good uses

- workshop decisions
- audience Q&A
- product research
- event feedback
- lightweight surveys inside a workbook

## 🖼️ Gallery

### Visual cards for assets, people, and references

Gallery sheets are great for anything image-first:

> 🤖 Agent example: an agent can bulk-create gallery cards from repository images, add tags and descriptions, filter a subset for export, and keep linked image references consistent across sheets.

- inspiration boards
- product catalogs
- team directories
- moodboards
- clipped research

### 🧱 Each item can hold

- title
- image
- description
- tags
- external link

### 🔗 Live image references

Gallery image fields can now point at image objects in other visual sheets instead of storing a separate image URL.

Use this flow:

1. Open a gallery item.
2. Choose `Reference existing`.
3. Pick a source image from a `Gallery`, `Design Canvas`, `Whiteboard`, or `Presentation` sheet.
4. Save the item.

What happens next:

- the gallery item shows the source image live
- if the source image changes, the gallery card updates too
- if the source object is deleted, the card keeps the reference and shows a broken-source state until you relink or replace it

This is better than copying URLs around because the target stays attached to the original object by stable ID.
For normal use, you do not need the raw object ID because the picker handles it for you. Stable IDs are mainly for API and CLI workflows.

### 🖱️ Common workflows

| Action | How |
|---|---|
| Add an item | Create manually, clip it, or use API/CLI |
| Edit tags and description | Item editor |
| Open the source | Use the stored link |
| Use it in reports | Reference its underlying data from spreadsheets |

### ✅ Selection and bulk actions

Gallery supports checkbox-based multi-select with bulk actions for:

- **Tag**
- **Delete**
- **Export CSV**
- **Clear selection**

The CLI mirrors the durable bulk actions with explicit row lists:

- `gallery-tag-items`
- `gallery-delete-items`
- `gallery-export-items`

### 🧱 Layout and viewing

- **Masonry layout** — a responsive grid that adjusts column count based on available width
- **Slideshow / carousel** — fullscreen view with left/right arrow key navigation through gallery items

### 🏷️ Tag filtering

Click a tag to filter the gallery to items with that tag. Click the same tag again to clear the filter.

### 📥 Adding images

- **Drag-drop import** — drag image files directly onto the gallery grid to create new items
- **Clipboard paste** — press `Ctrl/Cmd + V` to add images from the clipboard

### 💡 Great pairings

- Gallery + Canvas for creative production
- Gallery + Floor Plan for materials and furniture references
- Gallery + Document for visual briefs and research
## 🎨 Design Canvas

### A fixed artboard for polished design work

Use Design Canvas when you want a bounded page instead of an infinite board. It is ideal for:

> 🤖 Agent example: an agent can scaffold a social graphic, place reusable images, bind text to spreadsheet variables, categorize images with AI, and prepare multiple resized outputs for review.

- social graphics
- posters
- ads
- simple diagrams
- mockups
- exported creative assets

### 🧩 Starter templates

Canvas now includes a starter template library for common design jobs:

- Social Quote
- Product Promo
- Story Announcement
- Event Flyer
- Brand Board
- Moodboard

Use the `Templates` button in the page bar or `Design -> Apply template...`.
If the current page is empty, the template replaces it. If the page already has content, xApps inserts the template as a new page so your work stays intact.

### 📄 Multiple pages and artboards

Each canvas sheet can contain multiple pages, and each page has its own:

- size
- background
- object set

Common artboard workflows include portrait, landscape, and social-media-sized layouts. Canvas pages are better than separate sheets when the design belongs to one project.

Canvas also supports **Magic Resize** for Canva-style copy-and-resize workflows:

- use the `Resize` button in the page bar
- or `Design -> Magic Resize...`
- choose one or more target presets like Instagram Story, Twitter Header, or A4
- xApps creates resized page copies and scales the current page content into each new format

`Replace current page first` is also available when you want the first selected target to overwrite the current page instead of creating only copies.

### ➕ Objects you can place

- text
- shapes (rectangle, ellipse, rounded rectangle, star, polygon/hexagon)
- lines and arrows
- images

Shapes can also hold text labels now. Double-click a shape, or select it and press `Enter`, to edit the label inside it.

Right-click an object to see its backing storage footer at the bottom of the context menu. For Canvas objects, that footer shows the exact backing cell range for the object row.

### ✏️ Line styles

Nine line styles are available for lines, arrows, and shape strokes:

- solid, dashed, dotted
- solid + arrow end, dashed + arrow end, dotted + arrow end
- solid + dot end, dashed + dot end, dotted + dot end

### 🎨 Color swatches

A quick-access color palette is available in the fill and stroke pickers. Click any swatch for one-click fill or stroke application without opening the full color chooser.

### 🔤 Text features

- **Text effects** — letter spacing, line height, text transform (uppercase / lowercase / capitalize), and text shadow
- **Rich inline text** — bold, italic, underline, and strikethrough within a single text box via the floating format bar

### 📏 Rulers

A ruler bar runs along the top and left edges of the canvas. Features:

- **unit selector** — switch between px, mm, cm, and in
- **live position indicators** — crosshairs track cursor position on both rulers in real time

### 🧲 Design tools

Canvas now supports a much more complete visual-editing workflow:

- **group / ungroup**
- **align / distribute**
- **copy style**
- **gradient fills**
- **drop shadows**
- **lock objects**
- **shift + drag marquee multi-select**
- **template picker** for fast Canva-style starting points
- **Magic Resize** for multi-format page copies
- **undo / redo buttons** in the toolbar

### ✅ Bulk actions

When more than one object is selected, Canvas supports:

- **Duplicate** with a `+20,+20` offset
- **Delete**
- **Group / Ungroup**
- **Lock / Unlock**
- **Align / Distribute**
- **Bring forward / Send backward**
- **Bring to front / Send to back**

The CLI exposes the same deterministic operations with explicit row lists:

- `canvas-duplicate-objects`
- `canvas-delete-objects`
- `canvas-group-objects`
- `canvas-ungroup-objects`
- `canvas-lock-objects`
- `canvas-unlock-objects`
- `canvas-layout-objects`
  - supports `bring-forward`, `send-backward`, `bring-front`, and `send-back`

### 🖼️ Image controls

Selected images can use:

- opacity
- fit mode
- corner radius
- shadow
- brightness / contrast / saturation
- blur / grayscale / sepia
- crop
- background removal
- image link
- info link
- **clip shapes** — circle, rounded rect, star, diamond, hexagon masks
- **blend modes** — normal, multiply, screen, overlay, darken, lighten, and more

### 🧾 Clipped metadata summary

Clipped page/article cards and clipped image/product cards now expose a structured **Summary** section in the Canvas inspector.

That summary shows extracted metadata such as:

- title, site, author, publish date
- brand, SKU, price, currency, availability
- canonical URL, page URL, preview image URL
- description, selected text, keywords

Canvas also mirrors those recognized clip fields into the backing object row cells so they can be used in formulas, dashboards, and agent workflows. For Canvas, those promoted clip fields live in columns `M:AC` on the object row.

### 🔗 Live image references

Canvas image objects can point at image sources in other visual sheets instead of storing a separate image URL.

Use this flow:

1. Add or select an image object.
2. Choose `Reference existing`.
3. Pick a source image from a `Gallery`, `Design Canvas`, `Whiteboard`, or `Presentation` sheet.
4. Apply the change.

What happens next:

- the canvas object renders the source image live
- if the source image changes, the canvas object updates too
- if the source object is deleted, the canvas object keeps the reference and shows a broken-source state until you relink or replace it

For normal use, you do not need the raw object ID because the picker handles it for you. Stable IDs are mainly for API and CLI workflows.

### 🧭 Navigation and layout

- drag to move
- handles to resize
- rotation handle for rotation
- magenta alignment guides for snap feedback
- layers for stacking order
- the minimap in the lower-right can be collapsed to a compact `Map` pill and reopened from the same spot
- click anywhere in the minimap to jump the viewport
- drag the `View` grip inside the minimap viewport for easier navigation
- use the corner handles on the minimap viewport to zoom by resizing the visible frame
- on phones, Canvas switches to a bottom tool dock instead of a permanent left rail
- on phones, use the `Canvas` pill to reveal artboard controls and the `Objects` or `Image` pill to open the inspector drawer
- export as **PNG**, **SVG**, or **PDF**
- **center view** — zooms to fit the current selection (max 400%) or fits the artboard when nothing is selected
- **fit view** — calculates optimal zoom with padding so the full artboard is visible

### 🗺️ Minimap

A toggle button in the bottom-right corner opens the minimap overlay:

- shows a scaled overview of the artboard with a viewport rectangle
- click anywhere in the minimap to jump the viewport
- drag the viewport rectangle to pan
- resize the viewport rectangle to zoom

### 🔣 Template Variables

Text objects support live template variables using the syntax `{{SheetName!CellRef}}`. At render time, the variable resolves to the current value of the referenced cell. This lets you build data-driven designs that stay in sync with workbook data.

> 💡 Use Canvas when you care about a polished final composition. Use Whiteboard when you want infinite space and looser thinking.
## 🧠 Whiteboard

### Infinite space for thinking out loud

Whiteboard sheets are best for messy, fast, exploratory work:

> 🤖 Agent example: an agent can cluster sticky notes into themes, add connectors between related ideas, frame a workshop output, and turn a messy board into a cleaner process map.

- brainstorming
- user flows
- system maps
- workshop exercises
- meeting synthesis

### 📝 Core building blocks

- sticky notes
- checklist stickies
- shapes
- frames
- connectors
- images

Shapes can now carry text labels too. Double-click a shape to edit the label inside it.

### 🖱️ Fast interactions

| Action | How |
|---|---|
| Add sticky note | Double-click empty space |
| Edit sticky | Double-click the note |
| Connect objects | Use connector tools |
| Group a visual area | Use frames |
| Multi-select | `Shift` + drag a marquee |
| Select all on page | `Ctrl/Cmd + A` |
| Duplicate selection | `Ctrl/Cmd + D` |

### 🧭 Minimap and templates

- The minimap in the lower-right can be collapsed to a compact `Map` pill and reopened from the same spot.
- Click the minimap to jump the viewport.
- Drag the `View` grip inside the minimap viewport for easier navigation.
- Use the corner handles on the minimap viewport to zoom by resizing the visible frame.
- Process templates insert within the current visible area instead of landing too high above the canvas.

### ✅ Bulk actions

When more than one object is selected, the whiteboard bulk bar supports:

- **Duplicate** with a `+30,+30` offset
- **Delete**
- **Lock / Unlock**
- **Clear selection**

The CLI mirrors these actions with explicit row lists:

- `wb-duplicate-objects`
- `wb-delete-objects`
- `wb-lock-objects`
- `wb-unlock-objects`

Right-click an object to see its backing storage footer at the bottom of the context menu. For Whiteboard objects, that footer shows the exact backing cell range for the object row.

### 📄 Pages

Whiteboard sheets support multiple pages, each with independent pan and zoom state:

- add, rename, delete, and duplicate pages via tabs
- page overview shows all pages at a glance
- switch pages to keep different thinking spaces separate within one sheet

### 🗂️ Layers

Each page has a layer stack for organizing objects:

- create, rename, reorder, and delete layers
- toggle visibility per layer to hide distracting content
- lock a layer to prevent accidental edits
- manage layers through the layer manager dialog

### 📋 Process templates

Eight ready-made process templates are available from the `Whiteboard` menu:

- SWOT
- Business Model Canvas (BMC)
- User Journey Map
- Empathy Map
- Lean Canvas
- RACI Matrix
- Risk Matrix
- Stakeholder Map

### 📥 Drag-drop images

Drag image files directly onto the whiteboard canvas to place them as image objects.

### ✅ Why Whiteboard is different from Canvas

Canvas is page-based and presentation-ready. Whiteboard is spatial and infinite.

Use Whiteboard when:

- layout can sprawl in any direction
- you want freeform clustering
- frames and connectors matter more than pixel-perfect alignment

### 🖼️ Images and references

Whiteboard images are useful for:

- screenshots
- clipped references
- moodboarding
- annotation

You can adjust opacity and fit so images work as either content or soft background reference.

Whiteboard image objects can also link live to image sources from other visual sheets.

Use this flow:

1. Add or select an image object.
2. Choose `Reference existing`.
3. Pick a source image from a `Gallery`, `Design Canvas`, `Whiteboard`, or `Presentation` sheet.
4. Apply the change.

What happens next:

- the whiteboard object renders the source image live
- if the source image changes, the whiteboard object updates too
- if the source object is deleted, the whiteboard keeps the reference and shows a broken-source state until you relink or replace it

For normal use, you do not need the raw object ID because the picker handles it for you. Stable IDs are mainly for API and CLI workflows.
## 🎬 Presentation

### Build decks inside the workbook

Presentation sheets give you a slide editor with themes, templates, notes, and fullscreen playback.

> 🤖 Agent example: an agent can build a review deck from a doc brief, spreadsheet metrics, dashboard ranges, and gallery assets, then update the deck as the source sheets change.

### 🎨 Themes and templates

Presentation work is split into two ideas:

- **Theme** — the visual direction for the deck
- **Template** — the slide or deck structure you start from

xApps includes:

- multiple deck themes
- full deck templates
- insertable slide templates

Use them from the `Slides` menu to start faster without building every slide from scratch.

### 🧱 What a deck includes

- slide thumbnails
- editable stage
- text boxes
- shapes and diagram primitives
- lines and arrows
- tables
- images
- speaker notes

Current built-in shape authoring includes:

- rectangle / rounded rectangle
- circle / diamond / triangle / pill
- arrow / double arrow / chevron
- hexagon / star
- parallelogram / trapezoid
- callout / brace / punched tape

### 🖱️ Core workflows

| Action | How |
|---|---|
| Add a full deck template | `Slides -> Apply deck template...` |
| Insert one polished slide | `Slides -> Insert template slide...` |
| Edit text | Click or double-click the text object |
| Edit shape text | Select the shape and press `Enter`, or click it again |
| Move or resize objects | Drag the object or its handles |
| Move a table | Select the table and drag its `Move` grip |
| Resize a table | Select the table and drag the outer resize handles |
| Resize table columns or rows | Drag the internal guide handles between columns or rows |
| Add or remove table rows / columns quickly | Use the table inspector or right-click the table |
| Color a whole row or column | Pick a table cell, choose `Cell fill`, then use `Fill row` or `Fill column` |
| Apply alternating table colors | Use the `Stripe` preset selector in the table inspector |
| Add a linked image from another sheet | `Insert image -> Reference existing` |
| Present fullscreen | `Slides -> Present` |

Right-click a slide object to see its backing storage footer at the bottom of the context menu. Presentation objects are currently stored as nested slide-object entries, so the footer shows the exact `presentationSlides[...]` path for that object.

### 🔗 Reuse images across sheets

Presentation image objects can now stay linked to a source image from:

- `Gallery`
- `Design Canvas`
- `Whiteboard`
- another `Presentation` sheet

Use it like this:

1. Open the image insert menu.
2. Choose `Reference existing`.
3. Pick the source sheet and source image.
4. The slide image stays linked to the source instead of copying it.

If the source image is deleted later, the slide shows a broken-source state so you can relink it instead of silently losing the object.

### 🖼️ Image editing sidebar

When an image is selected, a sidebar panel opens with these sections:

- **Transform** — opacity, shadow, corner radius, blend mode
- **Adjustments** — brightness, contrast, saturation, blur, grayscale, sepia
- **Shape & Fit** — clip shapes (circle, rounded rect, star, diamond, hexagon), fit modes (cover, contain, fill)
- **Actions** — erase background, flip horizontal/vertical, reset to original

### 📥 Adding images

- **Drag-drop** — drag image files directly onto the slide stage
- **Upload** — use the image button popover to upload from your device
- **URL** — paste an image URL in the image button popover

### 📂 Import and export

| Action | How |
|---|---|
| Import a PowerPoint file | `File -> Import -> PowerPoint` |
| Export as PDF | `Slides -> Export as PDF (Print)` |

### 🔣 Template Variables

Text boxes support live template variables using the syntax `{{SheetName!CellRef}}`. The variable resolves to the current cell value at render time, keeping slides in sync with workbook data.

### ✅ Best uses

- pitch decks
- status reviews
- workshop material
- sales proposals
- case studies

> 💡 Presentation sheets are static starter-content driven right now. That makes them reliable and easy to edit, even without a full master-slide engine.
## 🏠 Floor Plan

### Space planning, layout, and interior planning

Floor Plan sheets are for 2D layout work with architectural-style tools:

> 🤖 Agent example: an agent can seed a room layout from a requirement sheet, place common furniture presets, annotate rooms, and keep equipment counts synced with a spreadsheet.

- walls
- doors
- windows
- furniture
- labels
- notes
- reference images
- measurements

### 🧱 Core tools

| Tool | Use it for |
|---|---|
| Walls | Room outlines and partitions |
| Doors / Windows | Openings that snap to nearby walls |
| Furniture | Fast room layout with presets |
| Text / Notes | Labels, comments, callouts |
| Measure | Distance annotations |

### 🛋️ Furniture library

The built-in library covers common categories like:

- living room
- bedroom
- dining
- kitchen
- bathroom
- office
- lighting
- outdoor
- storage

### 🖱️ Editing workflow

- drag to move objects
- `Shift` multi-select
- group / ungroup
- duplicate
- bring to front / send to back
- resize and rotate
- attached notes open immediately when created on an object

Right-click a floor-plan object to see its backing storage footer at the bottom of the context menu. Floor Plan objects are stored in per-kind arrays such as `fpFurniture[...]` or `fpWalls[...]`, so the footer shows that exact storage path.

### 📐 Units and technical controls

Floor Plan sheets support:

- units
- scale
- wall thickness
- zoom and pan
- layer visibility during DXF-style workflows

### 📥 DXF import

You can import DXF reference plans into a floorplan sheet. When importing CAD files:

- expect architectural layers to work best
- use layer visibility to tame noisy source files
- re-import after importer changes if an earlier import looked wrong

### 🧲 Snap system

Objects snap to nearby geometry for precise placement:

- wall edges and endpoints
- grid intersections
- midpoints of walls and objects
- nearby geometry edges

### 📍 Coordinate readout

A live cursor position display shows the current coordinates in plan units as you move across the canvas.

### 🗂️ Layer system

Floor Plan supports per-layer visibility and lock toggles. When importing DXF files, the importer creates matching layers automatically so you can toggle architectural layers on and off.

### ✅ Best uses

- residential planning
- office layouts
- renovation concepts
- materials and furniture planning
- design handoff notes alongside spreadsheets and docs
## 📊 Dashboard

### Assemble live metrics from the rest of your workbook

Dashboard sheets turn workbook data into a styled widget surface. They are best for executive summaries, KPI snapshots, CRM pipeline reviews, launch status, revenue boards, and at-a-glance reporting.

> 🤖 Agent example: an agent can build an executive dashboard by reading source ranges, adding KPI cards and charts, and wiring each widget back to the sheets where the underlying data lives.

### 🧱 Widget types

Current widget styles include:

- 🔢 KPI cards
- 🔻 **Sales Funnel** — stage-by-stage CRM conversion view; configure label and value ranges or a rectangular stage/value range
- 🧭 **Pipeline Stages** — dense CRM stage bars with value and share-of-total labels for pipeline reviews
- 📊 Bar charts
- 📈 Line charts
- 🍩 Donut / pie charts
- 🗺️ **Map** — linked geographic view from a Map sheet; the Map sheet owns geography, layers, choropleths, saved views, and regions
- ⭕ Progress rings
- 📋 Data tables
- 📝 Text blocks
- 🗺️ **Treemap** — Finviz-style proportional heatmap; configure label, size, and color columns with customizable min/max/neutral colors
- 🎯 **Gauge** — SVG semi-circular speedometer dial with configurable min/max range, color threshold zones (red/yellow/green), animated needle, and optional prefix/suffix

### 🎨 Surface styling

Dashboards now have both a **surface layer** and **widget-level styling**.

Surface controls let you set:

- background color
- grid line color
- freeform or packed layout mode
- column density
- row height

Widget controls let you set:

- accent color
- widget background
- widget border color
- width and height in grid units

### 🖱️ Interactions

| Action | How |
|---|---|
| Add widget | `+ Add Widget` |
| Style the dashboard itself | `Surface` button |
| Build a tighter tiled composition | `Pack Widgets` |
| Move widget | Drag it inside the grid |
| Resize widget | Drag the resize handle |
| Edit data source or copy | Widget editor |

### 🧩 Layout modes

- **Freeform Grid** keeps widget placement looser and more editorial
- **Packed / Dense** is optional and helps compress widgets into a tighter board-style arrangement

Use packed mode when you want a denser market-board, operations wall, or executive-control-room feel. Keep freeform when you want more whitespace and presentation polish.

### 🔗 Why dashboards are powerful here

Widgets pull from workbook data you already have elsewhere:

- spreadsheet ranges
- timelines
- calendars
- kanban counts
- documents and narrative text

### ✅ Best uses

- executive KPI surfaces
- weekly operating reviews
- launch status boards
- budget and forecast overviews
- dense watchlist / scorecard walls

That makes dashboards ideal for "single-pane-of-glass" reporting inside the same workbook instead of exporting to another tool.

## 📄 Docs

### Pages, briefs, SOPs, and knowledge entries

Docs sheets are the narrative layer of an xApps workbook. They are designed for:

> 🤖 Agent example: an agent can draft a project brief, create linked wiki pages, summarize meeting notes, and connect the doc to the timeline, dashboard, and repository files it references.

- project briefs
- meeting notes
- SOPs
- research notes
- release notes
- wiki-style documentation that links to the rest of the workbook

### ✍️ One Docs sheet can contain many pages

Each Docs sheet is now a small internal wiki workspace. Keep many related pages inside one Docs sheet, and use separate Docs sheets only when you want separate workspaces.

- use the page rail to switch pages inline
- page operations target the active page
- legacy `docTitle` / `docBlocks` fields still mirror the active page for compatibility

### 🔗 Wiki links

Docs supports wiki-style internal links:

- `[[Page]]` links to another page
- `[[Page#Section]]` links to a heading inside a page
- `[[#Section]]` links to a heading in the current page
- `[[Page|Label]]` adds custom link text
- `[[Page#Section|Label]]` links to a section with custom link text

### 🧱 Blocks

Docs pages are block-based. Current block types include:

- paragraph
- heading 1
- heading 2
- bulleted list
- checklist
- quote
- code block
- divider
- callout
- toggle list
- image

### 📝 Inline formatting

Text within blocks supports rich inline formatting:

- **bold**, **italic**, **underline**, **strikethrough**
- **inline code**
- **hyperlinks**

Apply formatting via the floating format bar or keyboard shortcuts (`Ctrl/Cmd + B`, `I`, `U`, etc.).

### 📊 Table blocks

Insert a table with the `/table` slash command. Tables support:

- header row toggle
- add and delete rows and columns
- `Tab` to navigate between cells

### 🖼️ Image blocks

Image blocks support:

- sizing — small, medium, large, or full width
- alignment — left, center, or right
- drag-drop and paste to insert images directly

### 💬 Block comments

Hover over any block to reveal the comment button. Comments support threaded discussions per block for feedback and review.

### 🎨 Block colors

Apply a background tint to any block for visual emphasis. Useful for highlighting key sections or creating visual groupings.

### ↕️ Block reordering

Drag blocks to reorder them within a page.

### 📤 Export

- **PDF export** — toolbar button or `Doc` menu
- **DOCX export** — toolbar button or `Doc` menu (Word-compatible HTML)

### 🧠 Wiki-style page shell

The Docs sheet is more than a blank editor. Each page also has:

- a cover tone
- an accent color
- page summary text
- editable properties
- linked sheets
- a live outline generated from headings
- page templates for common document shapes

### ⚡ Editing flow

The editor is designed to feel like one flowing page instead of a stack of form cards:

- type directly into a block
- press `Enter` on a heading to continue below with a paragraph
- press `Enter` on a checklist item to add the next checklist item
- use `/` inside a text block to open the slash menu
- use markdown-style shortcuts like `#`, `##`, `>`, `-`, `[]`, and ``` to convert the current block
- hover or focus a block to reveal type and action controls

### 🪄 Templates

Built-in templates currently include:

- Project Brief
- Meeting Notes
- SOP
- Research Note
- Release Notes

Templates replace the current active page structure, so use them early or after confirming a reset.

### 🎨 Page styling

Docs pages support page-level controls for:

- font family
- text scale
- page width
- cover tone
- accent color
- icon
- title
- summary

### 🏷️ Properties and linked sheets

Use properties to turn a freeform page into a structured wiki entry. Common fields include:

- status
- owner
- audience
- source
- review cadence

Linked sheets let one Docs page act as the front door to related workbook surfaces, like a timeline, dashboard, floor plan, or spreadsheet.

### 🔗 Great uses inside xApps

Docs pages work especially well when paired with other sheet types:

- write a project brief, then link to a timeline, kanban board, and dashboard
- keep renovation notes next to a floor plan, gallery, and budget spreadsheet
- store campaign strategy beside a content calendar, presentation, and design canvas

## ✍️ Typewriter

### Word-processing pages inside the workbook

Typewriter sheets are for polished page-based writing: proposals, reports, memos, long-form briefs, printable documents, and reviewed drafts. They use a Tiptap/ProseMirror editing stack with workbook-native save, collaboration, embeds, and import/export paths.

> 🤖 Agent example: an agent can draft a report from spreadsheet metrics, embed a live kanban or dashboard snapshot, add headings and tables, then export the document for human review.

### Editing and layout

- Rich text editing with headings, lists, links, tables, images, blockquotes, code blocks, and task lists.
- Page setup controls for margins, size, headers, footers, page numbers, and print output.
- Surface embeds for spreadsheet ranges, kanban boards, dashboards, and charts.
- Import/export flows for Markdown, HTML, DOCX, TXT import, and workbook-native content.
- A full Typewriter command group is available for agents; run `xapps help typewriter`.

### Good uses

- executive memos
- project plans
- specifications
- review documents
- printable briefs

## 📁 File Viewer

### Preview uploaded files inside a workbook

File Viewer sheets let you upload and preview documents and images without leaving the workbook.

> 🤖 Agent example: an agent can ingest a set of files, mirror their metadata into the sheet, route specific files into a review queue, and reference file rows from spreadsheets or dashboards.

Supported previews include:

- Excel-style files: `xlsx`, `xls`, `ods`, `csv`
- Documents: `docx`, `md`, `markdown`, `pdf`
- Slides: `pptx`
- Drawings: `dxf`
- Images: `png`, `jpg`, `jpeg`, `gif`, `webp`, `svg`, `bmp`, `avif`, `tif`, `tiff`

### Spreadsheet mirror refs

Each file is mirrored into the sheet grid so agents, formulas, and other workbook tools can reference it.

- one file per row
- columns `A:E` hold `name`, `type`, `size`, `source URL`, and `id`
- the active preview shows its mirrored range in the toolbar, for example `A1:E1`
- the active preview also shows its source cell, for example `D1`
- the live rendered preview is derived from the source URL in column `D`; it is not stored as a separate field

### Page rail

Paged previews such as PDFs, Word documents, and slide decks can show a page rail next to the preview.

- click a thumbnail to jump to that page
- the selected thumbnail follows the main preview as you scroll
- Word documents use text-based page cards in the rail for reliable page previews
- PDFs render inline and prefer a thumbnail rail when page rendering is available

Markdown files with headings show a section rail.

- click a section to jump to that heading
- the selected section follows the main preview as you scroll

### 📄 PDF support

PDF files render natively in the browser via embed. The page rail shows clickable thumbnails for quick navigation through large documents.

### 🔣 Template Variables

Text content in File Viewer supports template variables for dynamic rendering.

### 📊 Cell formula access

File metadata is mirrored in columns A through E. Reference it from any other sheet with standard cell formulas, for example `='Viewer'!A1` returns the filename of the first file.

### 🔌 Server API, CLI, and MCP

The full stack is available for agents and automation. Use the CLI commands below, the server API endpoints, or the MCP tool interface to manage files programmatically.

### CLI

Use the CLI to inspect the mirrored refs:

```bash
xapps viewer-files <sheet>
xapps active-viewer-file <sheet>
xapps viewer-meta <sheet>
```

## 🗄️ Repository

### Filesystem-backed document management

Repository sheets track files, folders, metadata, previews, and storage operations from inside a workbook. They are best when the workbook needs to reason about a real document set rather than only uploaded preview files.

> 🤖 Agent example: an agent can scan a repository folder, track important files, categorize them, extract metadata, summarize contents, and write review state back to the workbook.

### What Repository adds

- Folder browsing with tracked vs untracked file state.
- Stable file records with metadata, categories, status, and notes.
- Inline preview paths for supported text, image, document, and code formats.
- Storage operations for adding, updating, removing, refreshing, and categorizing files.
- CLI, API, MCP, and toolkit coverage for agent workflows.

### Repository vs File Viewer

Use **File Viewer** when you want uploaded files mirrored into workbook rows for preview and formulas. Use **Repository** when the sheet should manage an external or mounted file tree with tracked records and durable file operations.

## 🗺️ Maps

### Interactive maps, choropleths, and spatial views

Map sheets bring geography into your workbook. They render interactive WebGL maps powered by MapLibre GL JS, with data-driven layers that bind to spreadsheet ranges for choropleths, point markers, routes, and 3D extrusions.

> 🤖 Agent example: an agent can create a map sheet, load World Bank GDP data with one CLI command, set the basemap to dark mode, and enable 3D extrusions to produce a presentation-ready data visualization in seconds.

### Basemaps

Five basemap styles are available, all free with no API key:

| Style | Description |
|---|---|
| Streets | Vector tile map (OpenFreeMap Liberty) |
| Satellite | Esri/ArcGIS World Imagery |
| Terrain | OpenTopoMap topographic |
| Dark | CARTO dark basemap |
| Light | CARTO light basemap |

Switch basemaps from the toolbar dropdown or the CLI:

```bash
xapps set-map-basemap "My Map" dark
```

### Geography views

Choose a geographic focus to set the initial center, zoom, and boundary dataset:

- **World** (default), **Africa**, **Asia**, **Europe**, **Middle East**, **North America**, **South America**, **Oceania**, **United States**

The US States view uses a high-resolution dataset with Alaska, Hawaii, Puerto Rico, and territories.

```bash
xapps set-map-view "My Map" us-states
```

### Layer types

**Region layers (choropleth)**: Bind a spreadsheet range with a region/country/state column and a value column. Numeric values produce a gradient; categorical values get distinct colors. Optional columns: `label`, `color`, `note`. Supports country aliases (USA, UK, etc.) and US state abbreviations (CA, NY, etc.).

**Point layers**: Bind a spreadsheet range with `lat`/`lon` columns, or an `address`/`location`/`city` column for automatic geocoding via Nominatim. Optional columns: `label`, `value`, `color`, `size`, `order`, `image`, `status`.

**Route/path layers**: When a point layer has an `order` or `sequence` column, points are connected by a styled line in sorted order.

**3D extrusions**: Toggle 3D mode to render region data as extruded polygons proportional to their numeric values. The camera tilts to 45 degrees automatically.

### Adding layers

- Click **+ Region** or **+ Points** in the layers panel.
- Select a source spreadsheet range in the live embed dialog.
- Or add a public data layer with one click from the **Public Data** section.

### Public data sources

Click to fetch and visualize data from public APIs:

| Source | Type |
|---|---|
| Population (World Bank) | Region |
| GDP (World Bank) | Region |
| Life Expectancy (World Bank) | Region |
| CO2 Emissions (World Bank) | Region |
| Internet Users % (World Bank) | Region |
| Earthquakes Last 30 Days (USGS) | Point |
| All Earthquakes 4.5+ (USGS) | Point |
| Country Area (REST Countries) | Region |
| World Population Live | Region |

```bash
xapps add-public-data "My Map" usgs-earthquakes-all
```

### Live overlays

Toggle real-time tile overlays from the layers sidebar:

- **Railways** (OpenRailwayMap)
- **Sea Marks** (OpenSeaMap)
- **Hiking Trails** (Waymarked Trails)
- **Cycling Routes** (Waymarked Trails)

### Gallery x Map integration

When a point layer includes an `image` or `photo` column, hovering over a point shows a photo thumbnail popup. Connect a gallery sheet's image data to geographic locations.

### Kanban x Map integration

When a point layer has a `status` column, pins are color-coded (green for done, amber for in-progress, gray for todo, red for blocked, purple for review) and popups show a colored status badge.

### Bidirectional selection

Click a region on the map to select it. The inspector panel shows the linked spreadsheet row (sheet name and row number). Shift-click to multi-select. Selection syncs both ways: clicking a region highlights the corresponding data, and the inspector shows where that data lives.

### Context menu (right-click)

| Action | Description |
|---|---|
| Fit map to view | Reset to default world view |
| Reset pitch & bearing | Flatten the camera |
| Clear selection | Deselect all regions |
| Copy coordinates | Copy lat/lon of the clicked point |
| Send location to spreadsheet | Reverse-geocode and append a row to a target sheet |

### Geo-clustering and zoom-dependent layers

Layers support `minZoom` / `maxZoom` properties. Configure `mapZoomLayers` on the sheet to automatically switch data layers as the user zooms in or out, enabling drill-down from overview to detail.

### Spatial formulas

Use these in any spreadsheet cell:

| Formula | Result |
|---|---|
| `=GEO_DISTANCE(lat1, lon1, lat2, lon2, "mi")` | Haversine distance (miles or km) |
| `=GEO_BEARING(lat1, lon1, lat2, lon2)` | Initial bearing (0-360 degrees) |
| `=GEO_MIDPOINT(lat1, lon1, lat2, lon2)` | Geographic midpoint as "lat,lon" |
| `=GEO_FORMAT(lat, lon, "dms")` | Format coordinates (dd, dms, or dm) |

### Toolbar and controls

- Basemap selector, 3D toggle, labels toggle, place search (with Nominatim autocomplete)
- Navigation controls (zoom, compass, pitch) in the bottom-right
- Scale bar in the bottom-left
- Legend shows the active layer's color scale (toggle from toolbar or View menu)

### Embedding maps in other sheets

- Canvas, Whiteboard, Presentation, Floor Plan, and Doc sheets can embed a live map view.
- Spreadsheet cells can embed a compact map preview (Insert menu).
- Embedded views show a summary card with region count, data points, and a click-to-navigate link.

### Map CLI commands

```text
xapps map-config <sheet>                          — show configuration
xapps set-map-config <sheet> <json>               — update configuration
xapps map-layers <sheet>                          — list layers
xapps add-map-layer <sheet> <json>                — create a layer
xapps update-map-layer <sheet> <layer-id> <json>  — update a layer
xapps delete-map-layer <sheet> <layer-id>         — delete a layer
xapps set-map-view <sheet> <geography>            — set geography view
xapps set-map-basemap <sheet> <style>             — set basemap style
xapps add-public-data <sheet> <source-id>         — add a public data layer
```

### Map REST API

```text
GET    /api/sheets/:name/config
PUT    /api/sheets/:name/config
GET    /api/sheets/:name/layers
POST   /api/sheets/:name/layers
GET    /api/sheets/:name/layers/:id
PUT    /api/sheets/:name/layers/:id
DELETE /api/sheets/:name/layers/:id
```

## 🎮 Games

### Playable arcade sheets

Games sheets provide a lightweight arcade surface inside the workbook. They are useful for demos, workshops, team breaks, and proving that a workbook sheet can host richer interactive runtime state while still saving per-sheet high scores.

> 🤖 Agent example: an agent can create a games sheet, read high scores through the CLI/MCP path, and reset or report scores as part of a workshop setup.

### Current games

- Tetris
- Snake
- Space Invaders
- Galaga

### Agent-facing path

Use `xapps help games` or the `games_scores` MCP tool to inspect high scores. The sheet itself is primarily UI-driven; score reads are the stable automation surface.

## 🔗 Template Variables

Template Variables let you embed live spreadsheet values in text across any visual surface. Type `{{SheetName!CellRef}}` in a text box on Canvas, Presentation, Whiteboard, Doc, or Dashboard and it resolves to the current cell value at render time.

> 🤖 Agent example: an agent can wire revenue, status, owner, and due-date cells into decks, dashboards, labels, and briefs so one spreadsheet update propagates everywhere.

### Syntax

| Pattern | Resolves to |
|---------|-------------|
| `{{Budget!B2}}` | Cell B2 from the "Budget" sheet |
| `{{'Q3 Report'!D5}}` | Sheet names with spaces use single quotes |
| `{{Budget!B2\|$}}` | Format as currency: $1,247,000 |
| `{{Budget!B2\|%}}` | Format as percentage: 12.5% |
| `{{Budget!B2\|.0f}}` | Round to integer: 1247000 |
| `{{Budget!B2\|.1f}}` | One decimal place: 1247000.0 |
| `{{Budget!B2\|.2f}}` | Two decimal places: 1247000.00 |

### Where they work

Template variables resolve in text content on:

- **Canvas** — text objects
- **Presentation** — text boxes and shape labels
- **Whiteboard** — sticky notes and text objects
- **Doc** — paragraphs, headings, lists, callouts
- **Dashboard** — text widgets and widget titles

### How to insert

1. While editing text on any visual surface, type `{{` to start a variable
2. Type the sheet name, `!`, and cell reference
3. Close with `}}`
4. The variable resolves immediately in the rendered view

### Behavior

- The raw `{{}}` syntax is preserved in the data — only the display shows resolved values
- **Edit mode** shows the raw syntax (e.g., `{{Budget!B2|$}}`); **view mode** shows the resolved value (e.g., $1,247,000)
- Format specifiers (`|$`, `|%`, `|.0f`, `|.1f`, `|.2f`) are applied at display time only
- If the referenced sheet is deleted, the variable shows `#REF!`
- If the referenced cell is empty, the variable shows nothing
- Variables update on every render — change the source cell and all references update

### Examples

**Presentation slide:**
> Revenue is `{{Budget!B2}}` this quarter, up `{{Budget!C2|%}}` from last quarter.

Renders as: "Revenue is $4.2M this quarter, up 23% from last quarter."

**Floor plan label:**
> `{{Tenants!A3}}` — `{{Tenants!B3}}`

Renders as: "Suite 201 — Acme Corp"

### CLI

```bash
# No special CLI commands needed — template variables are just text content
# Set a cell value that contains template variables:
xapps set "Design" A1 "Revenue: {{Budget!B2}}"

# The variable resolves when the sheet is rendered in the browser
```

## 🗂️ Workbook Organization

### Tabs, sheets, and groups

> 🤖 Agent example: an agent can scaffold a workbook with grouped sheets like `Launch`, `Finance`, and `Operations`, then keep related surfaces organized as the project grows.

- The **bottom tab strip** is your workbook navigation.
- The **`+` button** inserts new sheets quickly.
- The **`Sheet` menu** lets you insert sheets and manage groups.
- A sheet can belong to **more than one group**.
- You can delete a grouped sheet directly from the group manager without ungrouping first.

### 📁 Sheet groups

Sheet groups create one parent tab that opens a small selector for related sheets. Good examples:

- `Launch`
  - Brief (Document)
  - Timeline
  - Calendar
  - Dashboard
- `Home Remodel`
  - Floor Plan
  - Construction Budget
  - Materials Gallery
  - Notes

Use **`Sheet -> Sheet Groups...`** to create or edit them.

## 🔐 Locks & Protection

You can protect both **individual sheets** and **sheet groups** with passwords.

> 🤖 Agent example: an agent can respect protected areas by working only with unlock tokens and limiting changes to the sheets or groups it has been explicitly authorized to modify.

### What protection does

- A protected **sheet** cannot be opened or edited until it is unlocked.
- A protected **group** cannot be opened or edited until it is unlocked.
- Browser sessions remember unlock state temporarily.
- CLI, API, and MCP use **unlock tokens**, not raw passwords on every command.

### Important limit

> 🔒 This is **app-level access control**, not full at-rest encryption. The workbook JSON is not encrypted on disk yet.

### Where to find it

- **`Sheet -> Protect Sheet...`**
- **`Sheet -> Remove Sheet Password...`**
- **`Sheet -> Protect Group...`**
- **`Sheet -> Remove Group Password...`**

## 💾 Working with Files

### Real workbook files

xApps now behaves as a **file-backed workbook app** by default.

> 🤖 Agent example: an agent can create server-side workbook files, save checkpoints, export Yjs snapshots, and reopen the exact file it needs without relying on browser-local state.

- `New Workbook` prompts for a name, creates a real workbook file, and loads it
- `Save Workbook` writes to the current workbook file
- `Save Workbook As...` writes to a new file
- `Open Workbook...` now lets you browse folders before loading a file
- optional folder paths like `clients/acme` are created on the server and stored as nested workbook files
- the new/save dialogs can browse folders and create them in-place through server APIs
- folder creation and workbook file listing now happen through server APIs, not browser-local assumptions
- the `File` menu shows your **3 recent workbooks**
- Docker saves workbook files under `/data` by default; API and CLI workbook names are relative to that folder

### 📥 Import / 📤 Export

The `File` menu uses grouped flyouts for import and export.

Common formats:

| Surface | Import | Export |
|---|---|---|
| Spreadsheet | CSV, Excel | CSV, Excel |
| Gallery | — | CSV, PDF |
| Canvas | — | PNG, PDF |
| Whiteboard | — | PNG, PDF |
| Calendar | ICS | — |
| Presentation | PPTX | — |
| Floor Plan | DXF | DXF, PDF, PNG |
| File Viewer | XLSX, DOCX, PPTX, CSV, MD, DXF, PDF | — |
| Workbook | Yjs snapshot | Yjs snapshot |

### 🖨️ Print and snapshots

- Use browser print for PDFs
- Workbook files, Yjs snapshots, CSV/Excel sheet imports, ICS calendar import, PPTX import staging, DXF import staging, and image uploads now flow through server APIs
- Use Yjs snapshots for compact collaboration-state export/import

## 🤝 Collaboration

### Live sync

Saved workbook files sync live across tabs and collaborators using Yjs/WebSocket rooms.

> 🤖 Agent example: an agent can work on the same saved workbook as a person, verify the active file, and make targeted updates without inventing a separate shadow copy of the project.

### Presence

xApps shows collaborator presence in different ways depending on the sheet type:

- spreadsheet cell cursor presence
- object selections on visual surfaces
- live movement previews while dragging on supported visual sheets

### If something feels stale

> 🔄 Do one hard refresh first if a UI change, menu change, or sheet-type upgrade is not appearing.

## 📦 Data Import and Export Guide

xApps supports importing and exporting data in many formats across its sheet types. This section covers each format in detail.

### CSV Import and Export (Spreadsheet)

**Import:** Use `File -> Import -> CSV` or the CLI command `import-csv`. CSV import maps each row to a spreadsheet row and each comma-separated value to a column. Headers in the first row become column labels.

```bash
xapps open-workbook MyWorkbook.json
xapps import-csv "Stock Data" data.csv
```

**Export:** Use `File -> Export -> CSV` or the CLI command `export-csv`. You can export the full sheet or a specific range.

```bash
xapps open-workbook MyWorkbook.json
xapps export-csv "Stock Data" --out report.csv
xapps export-csv "Stock Data" --range A1:K502 --out subset.csv
```

> **Tip:** Use `clear-sheet` before `import-csv` when you want a clean replacement instead of appending to existing data.

### XLSX Import and Export (Spreadsheet)

**Import:** Use `File -> Import -> Excel` to load `.xlsx` or `.xls` files. The importer reads cell values, basic formatting, and merges. Multi-sheet Excel files import the active sheet by default.

**Export:** Use `File -> Export -> Excel` to generate a `.xlsx` file from the current spreadsheet sheet.

### ICS Import (Calendar)

**Import:** Use `File -> Import -> ICS Calendar` or the CLI command `import-ics` to load `.ics` calendar files from Google Calendar, Apple Calendar, or Outlook.

```bash
xapps open-workbook MyWorkbook.json
xapps import-ics "My Calendar" team.ics
```

Events are mapped to calendar entries with title, date, time, description, and color fields.

### DXF Import and Export (Floor Plan)

**Import:** Use `File -> Import -> DXF` to load CAD floor plans. The importer creates matching layers from the DXF file so you can toggle architectural layers on and off. Non-architectural layers can be hidden with the layer visibility controls.

**Export:** Use `File -> Export -> DXF` to export floor plan geometry. Also available: PDF and PNG export for floor plans.

### SVG and PNG Export (Canvas, Whiteboard)

**Canvas export:** Use `File -> Export -> PNG`, `File -> Export -> SVG`, or `File -> Export -> PDF` from a canvas sheet. Export captures the current page at full resolution.

**Whiteboard export:** Use `File -> Export -> PNG` or `File -> Export -> PDF` from a whiteboard sheet.

### PPTX Import (Presentation)

**Import:** Use `File -> Import -> PowerPoint` to load `.pptx` slide decks into a presentation sheet. Slides are mapped to xApps presentation slides with text boxes, shapes, and images.

### PDF Export (Multiple Surfaces)

PDF export is available from:

- **Canvas** — `File -> Export -> PDF`
- **Whiteboard** — `File -> Export -> PDF`
- **Presentation** — `Slides -> Export as PDF (Print)`
- **Document** — `Doc` menu or toolbar button
- **Floor Plan** — `File -> Export -> PDF`
- **Gallery** — `File -> Export -> PDF`

### DOCX Export (Document)

**Export:** Use the `Doc` menu or toolbar button to export a document sheet as a Word-compatible `.docx` file.

### JSON Workbook Export and Import

**Export/import:** use the REST API file endpoints for full workbook JSON import and export. The current CLI focuses on API-backed workbook file creation/loading plus surface commands and does not register `export-workbook` or `import-workbook`.

JSON export captures the full workbook state including all sheets, data, formatting, and configuration.

### Yjs Snapshot Export and Import

Yjs snapshots capture the collaboration state compactly. Use server/API tooling for backup and migration; the current CLI does not register Yjs snapshot export/import commands.

### File Viewer Uploads

File Viewer sheets accept uploads of many formats: `xlsx`, `xls`, `ods`, `csv`, `docx`, `md`, `pdf`, `pptx`, `dxf`, and image formats (`png`, `jpg`, `gif`, `webp`, `svg`, `bmp`, `avif`, `tif`). Each uploaded file is mirrored into the sheet grid in columns A through E for formula access.

### Import/Export Summary Table

| Surface | Import Formats | Export Formats |
|---|---|---|
| Spreadsheet | CSV, XLSX, XLS | CSV, XLSX |
| Calendar | ICS | -- |
| Presentation | PPTX | PDF |
| Floor Plan | DXF | DXF, PDF, PNG |
| Canvas | -- | PNG, SVG, PDF |
| Whiteboard | -- | PNG, PDF |
| Document | -- | PDF, DOCX |
| Gallery | -- | CSV, PDF |
| File Viewer | XLSX, DOCX, PPTX, CSV, MD, DXF, PDF, images | -- |
| Workbook | JSON, Yjs snapshot | JSON, Yjs snapshot |

## ⚡ Command Palette

Open it with **`Ctrl/Cmd + K`**. See the full reference in the **Command Palette (Shell)** section above for a screenshot and complete group listing.

> 🤖 Agent example: a local assistant can map natural-language requests to the same high-value actions exposed through the command palette, then execute the underlying CLI or API operation directly.

Use it for:

- jumping to a sheet
- opening help
- starter kits
- automations
- sharing
- recent workbooks
- sheet-specific actions

It is the fastest way to move around large workbooks.

## 🔗 Sharing

Workbook files can have sharing metadata:

> 🤖 Agent example: an agent can prepare a workbook handoff by setting sharing metadata, confirming the saved file path, and generating a view-only or edit-ready link workflow.

- 🔒 private
- 👁️ view link
- ✏️ edit link

Sharing works on saved workbook files, not unsaved in-memory state.

Use:

- `File -> Share Workbook`

## 📦 Starter Kits

Starter kits create a prebuilt multi-sheet workbook instead of a blank one.

> 🤖 Agent example: an agent can apply a starter kit, rename the generated sheets, seed initial data, and leave a structured project workspace ready for human editing.

Examples:

- Project Ops
- Workshop
- Home Design
- Brand Kit

Use them when you want the **whole workbook** scaffolded at once.

## 🤖 Automations

Automations live under **`Tools -> Automations...`** and act like workbook-native macros.

> 🤖 Agent example: an agent can author automations that create standard sheets, seed key cells, apply templates, and reproduce the same kickoff workflow every time a new workbook starts.

They are designed for recurring setup work, not arbitrary scripting. That makes them safer and easier to understand than a full custom code runtime.

### 🧠 Best mental model

Use automations when you want to save one well-known transformation and run it on demand:

- create a new sheet
- duplicate a template sheet
- rename a starter sheet
- seed a title or status cell
- apply a starter kit
- apply a floorplan starter layout

### ✅ Supported automation actions

| Action | What it does |
|---|---|
| `create_sheet` | Adds a new sheet of a chosen type |
| `duplicate_sheet` | Copies an existing sheet |
| `rename_sheet` | Renames a sheet |
| `set_cell` | Writes a spreadsheet cell value, optionally with formatting |
| `apply_floorplan_template` | Seeds a floorplan-style starter layout into a floorplan sheet |
| `apply_starter_kit` | Replaces the active workbook with a starter kit |

### 📘 Good automation narratives

#### Project kickoff

Create several automations such as:

- `Create Overview`
- `Create Roadmap`
- `Create Launch Calendar`
- `Create Executive Dashboard`

Then run the ones you need when a new workbook starts.

#### Executive reporting scaffold

Use an automation to:

- create a `Dashboard`
- create an `Overview` spreadsheet
- set `A1` to `Executive Summary`

This is especially useful for teams that recreate the same reporting structure every week.

### 🛠️ Machine-facing automation coverage

Automations are fully reachable through:

- UI
- CLI
- REST API
- MCP

See:

- [AUTOMATIONS.md](/docs/AUTOMATIONS.md)

## ⚡ Triggers / Reactions

xApps uses a **three-layer reactive system**. Each layer has a specific job:

> 🤖 Agent example: an agent can install signal rules that notify a team when a budget crosses a threshold or when a workflow column reaches `Done`, without introducing risky cascading writes.

| Layer | Name | Purpose | Writes data? |
|-------|------|---------|-------------|
| 1 | Reactive Rules | Signal on data changes (notify, badge, log) | No |
| 2 | Background Processes | Scheduled batch processing with guards | Yes (guarded) |
| 3 | Agent Actions | User-initiated right-click context menu actions | Yes (on demand) |

### Layer 1: Reactive Rules

Reactive Rules fire automatically when something changes in the workbook. They are **signal-only** — they can notify, set a badge, or log, but they never write data. This replaces the old trigger-with-actions model and eliminates the risk of cascading writes.

### Trigger types

| Type | Fires when | Example |
|------|-----------|---------|
| `cell-change` | A specific cell changes value | Budget!B2 changes |
| `column-match` | Any cell in a column matches a condition | Status column equals "Done" |
| `threshold` | A numeric value crosses a boundary | Revenue exceeds $1M |
| `row-added` | A new row is added to a sheet | New card on kanban board |

### Signal types

| Signal | What it does |
|--------|-------------|
| `notify` | Show a notification to the user |
| `badge` | Store a badge state on the rule for the UI to surface |
| `log` | Log a message (for debugging) |

### Where to find it

- **`Tools > Triggers...`** opens the trigger management panel
- Each trigger shows its name, status (enabled/disabled), last fired time, and fire count

### CLI

The current CLI does not register trigger-management commands. Use the REST API endpoints below or MCP tools when that surface is enabled.

### REST API

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/workbook/triggers` | List all triggers |
| POST | `/api/workbook/triggers` | Add a trigger |
| PUT | `/api/workbook/triggers` | Replace all triggers |
| PUT | `/api/workbook/triggers/:id` | Update a trigger |
| DELETE | `/api/workbook/triggers/:id` | Delete a trigger |
| POST | `/api/workbook/triggers/:id/test` | Test-fire a trigger |

### Examples

**Notify when tasks complete:**
```json
{
  "name": "Done notification",
  "trigger": {
    "type": "column-match",
    "sheet": "Sprint Board",
    "column": "B",
    "condition": "equals",
    "value": "Done"
  },
  "signal": {
    "type": "notify",
    "message": "A task was marked Done on Sprint Board",
    "severity": "info"
  }
}
```

**Badge when budget exceeds limit:**
```json
{
  "name": "Budget overage badge",
  "trigger": {
    "type": "threshold",
    "sheet": "Budget",
    "column": "B",
    "condition": "greaterOrEqual",
    "value": 50000
  },
  "signal": {
    "type": "badge",
    "icon": "!",
    "color": "#f59e0b"
  }
}
```

### Demo workbook

To scaffold a workbook for experimenting with trigger rules, create a workbook with the relevant surfaces, then add rules through the API or UI:

```bash
xapps create-workbook "Signals Lab" --sheet kanban:"Sprint Board" --sheet spreadsheet:"Signals"
```

## Background Processes

Background Processes are scheduled tasks that scan sheets periodically and perform guarded writes. Unlike reactive rules (which only signal), processes do the actual data modifications.

> 🤖 Agent example: an agent can schedule a guarded process that scans a board for completed work every 30 seconds and updates a linked spreadsheet or timeline exactly once per item.

### How they work

Each process runs on a timer (e.g., every 30 seconds). It scans a sheet for rows matching a condition, skips already-processed rows (via a marker column), processes the batch, and marks rows as done.

### Safety properties

- **No loops** — marker column prevents reprocessing
- **No cascading** — runs on schedule, not on data changes
- **Single writer** — lock prevents concurrent runs
- **Auto-disable** — stops after 5 consecutive failures

### CLI

The current CLI does not register background-process commands. Use the REST API endpoints below or MCP tools when that surface is enabled.

### REST API

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/workbook/processes` | List all processes |
| POST | `/api/workbook/processes` | Add a process |
| PUT | `/api/workbook/processes/:id` | Update a process |
| DELETE | `/api/workbook/processes/:id` | Delete a process |
| POST | `/api/workbook/processes/:id/run` | Trigger immediate run |

## Agent Actions

Agent Actions are user-initiated operations that appear in the right-click context menu. Configure an action, and it shows up when you right-click on matching sheet types.

> 🤖 Agent example: an agent action can appear on a kanban card as `Summarize blocker`, on a repository file as `Analyze document`, or on a canvas image as `Categorize image`.

### Where to find it

- **`Tools > Agent Actions...`** to manage actions
- **Right-click** on any sheet to see matching actions

### How they work

Each action defines a prompt template, target sheet types, and scope. When clicked, the action is logged and ready for MeshAgent integration.

### CLI

The current CLI does not register agent-action management commands. Use the REST API endpoints below or MCP tools when that surface is enabled.

### REST API

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/workbook/agent-actions` | List all actions |
| POST | `/api/workbook/agent-actions` | Add an action |
| PUT | `/api/workbook/agent-actions/:id` | Update an action |
| DELETE | `/api/workbook/agent-actions/:id` | Delete an action |
| GET | `/api/workbook/agent-action-log` | View invocation log |

## 📌 Web Clipper

The xApps clipper lets you grab images and references from the web into:

> 🤖 Agent example: an agent can route a clipped product image into Canvas, preserve the detail-page URL, and mirror the extracted metadata into workbook cells for later formulas and dashboards.

- Design Canvas
- Whiteboard
- Gallery
- Floor Plan

The clipper preserves two links when possible: the exact image URL as `imageLink`, and the exact product or detail page as `infoLink`.
It now prefers the nearest product or detail-page link for an image instead of a broader collection, category, or search page when both are present, and leaves `infoLink` blank when it cannot determine a specific detail page.
When the clipper opens, it now defaults to the current saved workbook and the active compatible sheet inside that workbook. For canvas sheets, it also defaults to the active page.
For Canvas and Gallery targets, recognized metadata is also promoted into dedicated cells instead of being left only inside summary text. Canvas clips mirror those fields into `M:AC` on the object row, while Gallery clips mirror them into `J:Z` on the item row.

## 🔍 Search & Navigation

See the full shell coverage in the **Search Across Sheets (Shell)** and **Command Palette (Shell)** sections near the top of this document.

### Search Across Sheets

Use the **search field in the top menu bar** (or `Ctrl/Cmd + Shift + F`) to search across workbook content.

> 🤖 Agent example: an agent can search across sheets before writing, find the authoritative source range or page, and avoid creating duplicate or conflicting project state.

### Help search

The help dialog has its own built-in search so you can jump to the right help section quickly.

### Quick navigation

- `Ctrl/Cmd + K` for command palette
- tab strip for direct sheet access
- grouped tabs for related-sheet navigation

## ⌨️ Keyboard Shortcuts

### Global

> 🤖 Agent example: agents do not press keys, but the same operations exposed by shortcuts like save, search, undo, and command-palette actions should be reachable through CLI, API, or MCP paths.

| Shortcut | Action |
|---|---|
| `Ctrl/Cmd + Z` | Undo |
| `Ctrl/Cmd + Y` | Redo |
| `Ctrl/Cmd + S` | Save Workbook |
| `Ctrl/Cmd + K` | Command Palette |
| `Ctrl/Cmd + Shift + F` | Search across sheets |
| `Escape` | Close dialogs / cancel current interaction |

> ⌨️ Each sheet section above calls out the surface-specific interactions that matter most for that sheet.

### Spreadsheet Shortcuts

| Shortcut | Action |
|---|---|
| `F2` | Edit the selected cell |
| `Enter` | Confirm edit and move down |
| `Tab` | Confirm edit and move right |
| `Shift + Enter` | Confirm edit and move up |
| `Escape` | Cancel editing |
| Arrow keys | Navigate between cells |
| `Shift + Click` | Extend selection to clicked cell |
| `Ctrl/Cmd + B` | Bold |
| `Ctrl/Cmd + I` | Italic |
| `Ctrl/Cmd + U` | Underline |
| `Delete` / `Backspace` | Clear selected cell(s) |
| Double-click cell | Enter edit mode |

### Canvas and Whiteboard Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl/Cmd + A` | Select all objects on the current page |
| `Ctrl/Cmd + D` | Duplicate selected object(s) |
| `Delete` / `Backspace` | Delete selected object(s) |
| `Shift + Drag` | Marquee multi-select |
| `Enter` | Edit text on selected shape |
| Scroll wheel | Zoom in/out |
| Drag on empty space | Pan the canvas |
| Arrow keys | Nudge selected objects |

### Presentation Shortcuts

| Shortcut | Action |
|---|---|
| Click text | Select text object |
| Double-click text | Enter text editing mode |
| `Enter` on shape | Edit shape label |
| `Delete` / `Backspace` | Delete selected object |
| Drag object | Move object on slide |
| Drag handles | Resize object |

### Document Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl/Cmd + B` | Bold inline text |
| `Ctrl/Cmd + I` | Italic inline text |
| `Ctrl/Cmd + U` | Underline inline text |
| `Enter` | New block / continue list |
| `/` | Open slash command menu |
| `#` at start | Convert block to Heading 1 |
| `##` at start | Convert block to Heading 2 |
| `>` at start | Convert block to quote |
| `-` at start | Convert block to bullet list |
| `[]` at start | Convert block to checklist |
| `` ``` `` at start | Convert block to code block |

### General Navigation

| Shortcut | Action |
|---|---|
| `Ctrl/Cmd + K` | Open command palette |
| `Ctrl/Cmd + S` | Save workbook |
| `Ctrl/Cmd + Z` | Undo |
| `Ctrl/Cmd + Y` | Redo |
| `Ctrl/Cmd + Shift + F` | Search across sheets |
| `Escape` | Close dialog or cancel interaction |
| Tab strip click | Switch to a sheet |
| Group tab click | Open sheet group selector |

## 🕐 Activity Feed

See the full shell reference in the **Activity Feed (Shell)** section near the top of this document.

The Activity Feed is a chronological timeline of all changes across the workbook. Open it with the **clock icon** in the top bar.

> 🤖 Agent example: an agent can inspect the activity feed to understand what changed recently, confirm whether a write already happened, and summarize recent work for a human reviewer.

Tracking starts paused by default. Click **Resume** to begin logging for the current session.

### Controls

- **Start / Stop** — toggle activity logging on or off
- **Clear** — remove all recorded activity entries
- **Filter by sheet** — click a sheet-name chip to show only activity for that sheet; click again to clear the filter

Each entry shows an icon, action description, detail text, sheet name, and timestamp. Activity is recorded when sheets are created, modified, deleted, or when specific actions (adding cards, events, widgets, etc.) occur.

## 🛰️ Sheet Radar

See the full shell reference in the **Sheet Radar (Shell)** section near the top of this document.

Sheet Radar is a visual dependency graph that shows how sheets in the workbook reference each other. Open it with the **satellite icon** in the top bar.

> 🤖 Agent example: an agent can use dependency information to see which dashboards, docs, or formulas depend on a source sheet before renaming fields or restructuring data.

### What it shows

- **Nodes** — each sheet appears as a colored circle sized by its content volume (cell count, widget count, card count, etc.)
- **Directional arrows** — arrows point from the sheet that contains the reference to the sheet being referenced (e.g., a Dashboard widget pulling data from a Spreadsheet)
- **Edge labels** — hovering shows which cell references or widget connections create the dependency
- **Click to navigate** — click any node to switch to that sheet

Sheet Radar detects cross-sheet formula references (`'SheetName'!A1` patterns) and dashboard widget data sources automatically.

## 📋 Cheat Sheet

See the full shell reference in the **Cheat Sheet (Shell)** section near the top of this document.

The Cheat Sheet is a context-sensitive quick-reference panel. Open it with the **book icon** in the top bar. It updates automatically when you switch sheets, always showing tips relevant to your current context.

> 🤖 Agent example: an agent can point a human collaborator to the cheat sheet after restructuring a surface so the local interaction model stays obvious and discoverable.

## 🧩 Workbook Type Configuration

Use **Sheet > Configure Sheet Types...** to show or hide specific sheet types from the `+` menu. This lets you tailor the workbook to your workflow by hiding sheet types you do not need, keeping the interface focused.

> 🤖 Agent example: an agent can hide unused sheet types when setting up a domain-specific workbook so users only see the surfaces that belong in that workflow.

## 💻 Command Line Interface (CLI)

The CLI lets agents and shell scripts work through the same workspace API that backs the UI. It is not a filesystem shortcut and it does not read workbook files directly. Use the packaged CLI inside the xApps runtime image:

```bash
node /app/bin/xapps.js --help
```

The same packaged entrypoint starts the workspace server when invoked in server mode:

```bash
node /app/bin/xapps.js serve --web-only
```

Do not use retired product-name commands, stale repo paths, or unrelated `cli.js` wrappers.

> 🤖 Agent example: a terminal-based agent can create sheets, import data, validate results, and save the workbook without ever touching the browser UI.

```bash
xapps [--base-url <url>] [--file <workbook>] <command> [args...]
xapps [--base-url <url>] [--file <workbook>] <group> <command> [args...]
xapps help [group|command|group command]
xapps <command> --help
xapps <group> <command> --help
xapps search <terms...> [--json] [--limit <n>]
xapps list
```

MeshAgent room agents should run those commands from the deployed xApps runtime image, for example `registry.meshagent.com/powerboards/xapps:v2.3.11` when that is the room tag. A sibling container without that image does not have the xApps CLI runtime unless the room explicitly starts or switches into the xApps container.

Set the API target with explicit `--base-url`, `XAPPS_INTERNAL_API_BASE_URL`, `MESHAGENT_ROOM_URL`, or `XAPPS_API_BASE_URL`; retired sheet-API URL variables are not read by the current CLI. In the packaged xApps Docker runtime, `/app/bin/xapps.js` seeds `XAPPS_INTERNAL_API_BASE_URL` to the same-runtime workspace API port; the workspace host does the same when launched directly. When that internal URL is unset and `MESHAGENT_ROOM_URL` is present, the CLI parses it as a URL, replaces its port with `3001`, materializes that value into `XAPPS_INTERNAL_API_BASE_URL` for the CLI process, and prefers it over `XAPPS_API_BASE_URL`:

```bash
export MESHAGENT_ROOM_URL="http://10.28.5.94:8078"
export XAPPS_API_BEARER_TOKEN="$MESHAGENT_TOKEN"
xapps list-workbooks --json
```

The example room URL above resolves to `http://10.28.5.94:3001` for xApps API calls only when `XAPPS_INTERNAL_API_BASE_URL` is unset; the CLI replaces the port rather than appending a second port.

Private MeshAgent/IAP rooms rely on the upstream room/IAP boundary; xApps does not add its own Google sign-in gate there. Public rooms that need xApps-level Google sign-in set `XAPPS_DEPLOYMENT_MODE=public` (legacy `XAPPS_AUTH_MODE=google` also works). Same-runtime CLI/MCP/toolkit calls from the deployed xApps runtime are still accepted as internal agent calls in public mode.

Use `--file <workbook>` when an automation must target one saved workbook without depending on the browser's active workbook; the CLI sends the same `X-XApps-File` API header used by REST callers.

In Docker, saved workbook files live under `/data` by default. Do not add a `workbook/` prefix to CLI file names unless `xapps list-workbooks --json` returned that prefix; pass the returned `file` or `name` exactly.

### Discovery

```bash
xapps --help          # Show command groups
xapps search "cell background"
xapps search --json cell background --limit 1
xapps list            # List every registered command
xapps help workbook   # Show workbook commands
xapps help spreadsheet format
xapps help kanban     # Show one surface command group
```

Use `xapps search --json <intent> --limit 3` first for compact command discovery. It runs locally without an API base URL and returns only matching commands, exact invocations, examples, notes, and help paths. Use `matches[].invocations[]` or `matches[].usage` exactly. Do not invent hyphenated command names by joining a group and command; group scope is a separate token, for example `xapps gallery items`, not `xapps gallery-items`.

Use `xapps list --json` when an agent really needs the full registry. The detailed typed catalog is in the top-level `commands[]` array; `groups[]` is only a summary.

Current command groups include workbook, calendar, canvas, dashboard, doc, fileviewer, floorplan, gallery, games, kanban, map, poll, presentation, records, repository, spreadsheet, timeline, typewriter, and whiteboard. Use `xapps --help` and `xapps list --json` as the source of truth.

### Workbook Commands

```bash
xapps list-workbooks --json
xapps current-workbook --json
xapps open-workbook Planning.json
xapps sheets --json
xapps active-sheet
xapps set-active-sheet "Budget"
xapps create-sheet "Budget" --type spreadsheet --file Planning.json
xapps rename-sheet "Budget" "FY Budget"
xapps duplicate-sheet "FY Budget" "FY Budget Copy"
xapps sheet-settings "FY Budget" --json
xapps update-sheet-settings "FY Budget" '{"visibility":"primary"}'
xapps delete-sheet "FY Budget Copy"
xapps create-workbook "Operations" --sheet kanban:"Sprint Board" --sheet timeline:"Roadmap"
```

### Spreadsheet Commands

```bash
xapps get "Budget" A1
xapps set "Budget" A1 "Revenue"
xapps format "Budget" A1 '{"bg":"#ff0000"}'
xapps range "Budget" A1:D10 --json
xapps bulk-set "Budget" A1 '[["Name","Amount"],["Rent","2000"],["Food","800"]]'
xapps import-csv "Stock Data" data.csv
xapps export-csv "Stock Data" --range A1:K502 --out subset.csv
xapps add-chart "Budget" '{"type":"bar","title":"Spend","dataRange":"A2:B8","labelCol":"A","valueCol":"B"}'
xapps add-table "Budget" '{"name":"Expenses","rangeStart":"A1","rangeEnd":"C20","groupBy":["Category"]}'
xapps sort-table "Budget" expenses Amount --direction desc
xapps table-groups "Budget" expenses
xapps set-sparkline "Budget" C2 B2:B12 --type bar
printf '{"op":"spreadsheet.formatCell","ref":"A1","format":{"bg":"#ff0000"}}\n' | xapps spreadsheet batch "Budget" --stdin
```

`xapps get` prints evaluated formula results. The raw stored formula is available from the cell API as `rawValue` when using `?evaluate=1`.
Add `--json` to spreadsheet commands when agents need structured success output with `ok`, `message`, and command-specific fields.

For high-volume edits, use `xapps mutate --stdin` or surface batches such as `xapps spreadsheet batch <sheet> --stdin`. They send validated semantic ops to the server-side Yjs path so many cell writes are applied in one Yjs transaction and JSON persistence is debounced.

Structured table payloads support `id`, `name`, `rangeStart`, `rangeEnd`, `headerRow`, `style`, `columns`, `sortRules`, and `groupBy`. When `columns` is omitted, xApps derives table columns from the header row. Table sorting reorders only body rows so the header row stays in place, and grouped reads return records plus `count` and numeric `sums`.

In the spreadsheet UI, select a range and click **Format as Table**. Table headers show one arrow sort control; the arrow points up for ascending and down for descending, and sorting only reorders the table body. Toolbar A/Z sorting also targets the table body when the selected cell is inside a table. Use **Alternating Colors** for plain striped ranges without creating table metadata. To group records, right-click a cell in the table column you want to group by, then choose **Table > Group by selected column**. Use **Table > Clear grouping** to remove grouping. Formulas can reference structured tables with `TableName[Column]`, `TableName[#Headers]`, `TableName[#Data]`, and `TableName[#All]`, for example `=SUM(Expenses[Amount])`.

### Surface Examples

```bash
xapps cards "Sprint Board" --status "In Progress"
xapps add-card "Sprint Board" "Fix login bug" --list "To Do" --labels "P1,bug" --due "2026-04-15"
xapps card-json "Sprint Board" TASK-42
xapps add-card-comment "Sprint Board" TASK-42 "Ready for review." --author Alice --type progress
xapps card-comments "Sprint Board" TASK-42
xapps records-list-tables "CRM"
xapps records-add-field "CRM" "Stage" --type singleSelect --options '{"choices":["Lead","Qualified","Won"]}'
xapps records-create "CRM" '{"Name":"Acme","Stage":"Lead"}'
xapps records-sql "CRM" 'SELECT * FROM CRM WHERE Stage = "Lead"'
xapps poll-config "Workshop Poll" --json
xapps add-question "Workshop Poll" --type single --prompt "Pick a direction" --option "A" --option "B"
xapps set-poll-status "Workshop Poll" open
xapps gallery items "Evidence" --json
xapps gallery add-item "Evidence" "Post-fix screenshot" --image /uploads/fix.png --desc "Rendered state after the fix" --tags after,verified --json
xapps gallery add-item "Evidence" "Local screenshot" --image /tmp/fix.png --upload --desc "Uploaded local image evidence" --tags after,verified --json
xapps gallery-tag-items "Evidence" --rows 0,1 --tag verified --json
xapps events "My Calendar" --from 2026-04-01 --to 2026-04-30
xapps add-event "My Calendar" "Team Standup" --date 2026-04-10 --time 09:00 --color "#4285f4"
xapps widgets "My Dashboard"
xapps add-widget "My Dashboard" '{"type":"kpi","title":"Revenue","dataSource":{"sheetName":"Budget","range":"B2"}}'
xapps slides "Pitch Deck"
xapps add-text-box "Pitch Deck" slide-1 "Hello World" --x 100 --y 200 --size 36
xapps add-sticky "Brainstorm" "Great idea!" --x 100 --y 200 --bg "#fff475"
xapps canvas-templates
xapps add-canvas-text "Design" "Headline" --x 100 --y 100 --size 48 --color "#fff"
xapps viewer-files "Docs"
xapps repo-files "Repository"
xapps games-scores "Arcade"
xapps typewriter wordcount "Report"
xapps typewriter export "Report" md --out report.md
xapps doc-add-page "Encyclopedia" "First Article" --icon 📜 --summary "Intro entry"
xapps doc-add-block "Encyclopedia" page-2 --type heading2 --text "Background"
xapps doc-import-markdown "Encyclopedia" --multi --file ./book.md --replace-pages
xapps doc-list-pages "Encyclopedia"
xapps doc-list-page-links "Encyclopedia" page-5
```

### Environment Variables

| Variable | Purpose | Default |
|---|---|---|
| `XAPPS_INTERNAL_API_BASE_URL` | Same-runtime workspace API base URL, preferred inside the deployed xApps service runtime | seeded by `/app/bin/xapps.js` in Docker; otherwise unset |
| `MESHAGENT_ROOM_URL` | MeshAgent room URL; CLI changes the port to `3001` for xApps API calls | unset |
| `XAPPS_API_BASE_URL` | Public workspace API base URL when internal and room URLs are unset | required unless another base URL source is set |
| `XAPPS_API_AUTHORIZATION` | Full Authorization header value | unset |
| `XAPPS_API_BEARER_TOKEN` | Bearer token used when Authorization is unset | unset |
| `XAPPS_API_COOKIE` | Cookie header for API requests | unset |

### Tips for AI Agents

- In MeshAgent rooms, run inside the xApps runtime image; use `node /app/bin/xapps.js`
- Inside the xApps runtime image, use `node /app/bin/xapps.js`; otherwise set `MESHAGENT_ROOM_URL`, `XAPPS_API_BASE_URL`, or pass `--base-url`
- Load the intended workbook before issuing sheet commands
- Use `import-csv` for bulk data loading (much faster than individual `set` calls)
- Use `clear-sheet` before `import-csv` for a clean reimport
- Use `range` to read data and verify results after writes
- Use `bulk-set` for programmatic data with JSON arrays
- Widget and chart configs accept JSON — use single quotes around the JSON on the command line
- Use `--json` for commands that support structured output
- Default text output is for humans; JSON output is for agents and scripts

## 🌐 REST API

Base URL: `${XAPPS_API_BASE_URL}/api`. OpenAPI spec: `/api/openapi.json`.

> 🤖 Agent example: a backend agent can provision workbook files, populate sheets, run automations, and collect structured results over HTTP for larger system integrations.

### Headers

| Header | Purpose |
|---|---|
| `X-XApps-File` | Target a specific saved workbook file (e.g., `Stocks.json`) |
| `X-XApps-Unlock` | Unlock token for protected sheets/groups |
| `Content-Type` | `application/json` for all POST/PUT requests |

### Workbook Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/workbook` | Get full workbook |
| PUT | `/api/workbook` | Replace workbook |
| GET | `/api/workbook/active-sheet` | Get active sheet name |
| POST | `/api/workbook/active-sheet` | Set active sheet |
| GET | `/api/files` | List saved workbook files |
| GET | `/api/workbook/groups` | List sheet groups |
| PUT | `/api/workbook/groups` | Replace sheet groups |
| POST | `/api/workbook/groups` | Create a sheet group |
| GET | `/api/workbook/automations` | List automations |
| POST | `/api/workbook/automations` | Create automation |
| POST | `/api/workbook/automations/run` | Run an automation |
| GET | `/api/workbook/triggers` | List all triggers |
| POST | `/api/workbook/triggers` | Add a trigger |
| PUT | `/api/workbook/triggers` | Replace all triggers |
| PUT | `/api/workbook/triggers/:id` | Update a trigger |
| DELETE | `/api/workbook/triggers/:id` | Delete a trigger |
| POST | `/api/workbook/triggers/:id/test` | Test-fire a trigger |
| POST | `/api/workbook/starter-kit` | Apply starter kit |
| GET | `/api/workbook/processes` | List background processes |
| POST | `/api/workbook/processes` | Add a process |
| PUT | `/api/workbook/processes/:id` | Update a process |
| DELETE | `/api/workbook/processes/:id` | Delete a process |
| POST | `/api/workbook/processes/:id/run` | Trigger immediate run |
| GET | `/api/workbook/agent-actions` | List agent actions |
| POST | `/api/workbook/agent-actions` | Add an agent action |
| PUT | `/api/workbook/agent-actions/:id` | Update an agent action |
| DELETE | `/api/workbook/agent-actions/:id` | Delete an agent action |
| GET | `/api/workbook/agent-action-log` | View agent action invocation log |
| GET | `/api/workbook/notifications` | List notifications |
| POST | `/api/workbook/notifications/dismiss` | Dismiss a notification |

### Sheet Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/sheets` | List all sheets |
| POST | `/api/sheets` | Create sheet `{"name":"...","type":"..."}` |
| DELETE | `/api/sheets/:name` | Delete sheet |
| GET | `/api/sheets/:name/settings` | Get sheet settings |
| PUT | `/api/sheets/:name/settings` | Update sheet settings |
| POST | `/api/sheets/:name/duplicate` | Duplicate sheet |
| POST | `/api/sheets/:name/lock` | Lock sheet |
| POST | `/api/sheets/:name/unlock` | Unlock sheet |

### Spreadsheet Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/sheets/:name/cells/:ref` | Read cell |
| PUT | `/api/sheets/:name/cells/:ref` | Write cell `{"value":"..."}` |
| DELETE | `/api/sheets/:name/cells/:ref` | Clear cell |
| GET | `/api/sheets/:name/range/:range` | Read range (returns `{data:[[...]]}`) |
| PUT | `/api/sheets/:name/range/:range` | Bulk write range `{"data":[[...]]}` |
| POST | `/api/sheets/:name/clear` | Clear all cells and merges |
| GET/PUT/DELETE | `/api/sheets/:name/cells/:ref/format` | Cell format |
| GET/PUT/DELETE | `/api/sheets/:name/cells/:ref/validation` | Cell validation |
| GET/PUT/DELETE | `/api/sheets/:name/cells/:ref/comment` | Cell comment |
| GET/PUT/DELETE | `/api/sheets/:name/cells/:ref/image` | Cell image |
| GET/POST | `/api/sheets/:name/charts` | List/create charts |
| PUT/DELETE | `/api/sheets/:name/charts/:id` | Update/delete chart |
| GET/POST | `/api/sheets/:name/tables` | List/create structured tables |
| GET/PUT/DELETE | `/api/sheets/:name/tables/:id` | Read/update/delete structured table metadata |
| POST | `/api/sheets/:name/tables/:id/sort` | Sort table body rows by named header column |
| GET | `/api/sheets/:name/tables/:id/groups` | Read grouped table records and summaries |
| GET/PUT/POST/DELETE | `/api/sheets/:name/conditional-formats` | Conditional formatting |
| POST | `/api/sheets/:name/merge` | Merge range |
| POST | `/api/sheets/:name/unmerge` | Unmerge range |

### Surface Endpoints

Each sheet type exposes its own sub-endpoints:

| Type | Endpoints |
|---|---|
| **Records** | `/records`, `/records/:recordId`, `/records/bulk`, `/records/deleted`, `/records/:recordId/restore`, `/fields`, `/fields/:fieldId`, `/tables`, `/tables/:tableId`, `/views`, `/views/:viewId`, `/sql` |
| **Kanban** | `/cards`, `/cards/:rowOrId`, `/cards/:rowOrId/comments`, `/lists`, `/lists/:name`, `/lists/reorder` |
| **Calendar** | `/events`, `/events/:row` |
| **Timeline** | `/tasks`, `/tasks/:row` |
| **Poll** | `/config`, `/status`, `/questions`, `/questions/:id`, `/questions/reorder`, `/questions/:id/options`, `/responses`, `/tally` |
| **Gallery** | `/items`, `/items/:row` |
| **Dashboard** | `/widgets`, `/widgets/:id` |
| **Doc** | `/blocks`, `/blocks/:id`, `/pages`, `/pages/:id` |
| **Typewriter** | Standard sheet reads/writes plus `/api/sheet-files` import/export helpers; use `xapps help typewriter` and the surface help for exact command and file formats. |
| **Presentation** | `/slides`, `/slides/:id`, `/slides/:id/objects`, `/slides/:id/objects/:objId` |
| **Canvas/Whiteboard/Floorplan** | `/objects`, `/objects/:rowOrId` |
| **File Viewer** | `/viewer-files`, `/viewer-files/:row`, `/viewer-meta`, `/active-viewer-file`, `/viewer-files/upload`, `/viewer-files/:row/preview`, `/viewer-files/:row/download` |
| **Repository** | `/files`, `/files/:rowOrId`, `/files/:rowOrId/content`, `/files/:rowOrId/preview-content`, `/files/:rowOrId/refresh`, `/files/refresh-all`, `/categories` |
| **Games** | Standard sheet read/write paths for active game and high-score state |

### Curl Examples

```bash
export XAPPS_API_BASE_URL="https://your-xapps-host"

# Read a workbook file
curl -H 'X-XApps-File: Stocks.json' "$XAPPS_API_BASE_URL/api/workbook"

# Create a sheet
curl -X POST "$XAPPS_API_BASE_URL/api/sheets" \
  -H 'Content-Type: application/json' \
  -H 'X-XApps-File: Stocks.json' \
  -d '{"name":"Analysis","type":"spreadsheet"}'

# Bulk write cells (fastest way to populate data)
curl -X PUT "$XAPPS_API_BASE_URL/api/sheets/Stock%20Data/range/A1:C3" \
  -H 'Content-Type: application/json' \
  -H 'X-XApps-File: Stocks.json' \
  -d '{"data":[["Ticker","Price","Change"],["AAPL","255.92","0.11"],["MSFT","373.46","1.11"]]}'

# Clear a sheet
curl -X POST "$XAPPS_API_BASE_URL/api/sheets/Stock%20Data/clear" \
  -H 'X-XApps-File: Stocks.json'

# Add a dashboard treemap widget
curl -X POST "$XAPPS_API_BASE_URL/api/sheets/Market%20Heatmap/widgets" \
  -H 'Content-Type: application/json' \
  -H 'X-XApps-File: Stocks.json' \
  -d '{"type":"treemap","title":"S&P 500","config":{"tmLabels":"A2:A502","tmSizes":"D2:D502","tmColors":"I2:I502"},"gridW":12,"gridH":12}'

# Add a dashboard map widget linked to a Map sheet
curl -X POST "$XAPPS_API_BASE_URL/api/sheets/Revenue%20Dashboard/widgets" \
  -H 'Content-Type: application/json' \
  -H 'X-XApps-File: Sales.json' \
  -d '{"type":"map","title":"Revenue by State","dataSource":{"sheetName":"Revenue Map"},"config":{"mapSource":{"kind":"sheet-view","sheetType":"map","sheet":"Revenue Map","mode":"embed"}},"gridW":6,"gridH":4}'

# Add a Kanban card
curl -X POST "$XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/cards" \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H 'Content-Type: application/json' \
  -d '{"title":"Fix login bug","status":"To Do","labels":"P1,bug"}'

# Add a timeline task
curl -X POST "$XAPPS_API_BASE_URL/api/sheets/Project%20Plan/tasks" \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H 'Content-Type: application/json' \
  -d '{"title":"Design Phase","start":"2026-04-07","end":"2026-04-18","color":"#7b61ff"}'

# Add a doc block
curl -X POST "$XAPPS_API_BASE_URL/api/sheets/Meeting%20Notes/blocks" \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H 'Content-Type: application/json' \
  -d '{"type":"heading1","text":"Action Items"}'
```

## 🤖 MCP Server for AI Assistants

The MCP server exposes xApps as structured tools for AI agents and assistants. It registers the shared workbook/core MCP registry plus every surface package whose manifest enables MCP.

> 🤖 Agent example: an AI assistant can create a workbook, inspect ranges, build dashboards, update kanban cards, and verify outputs through typed MCP tools without scraping the UI.

### Starting the MCP Server

Build the repo first:

```bash
npm run build:ts
```

Run the stdio MCP host directly with an explicit workspace API origin:

```bash
XAPPS_INTERNAL_API_BASE_URL="https://xapps.example.com" node packages/xapps-mcp-host/dist/index.js
```

Or start the workspace host and MCP host together under the supervisor:

```bash
npm run start:with-mcp
```

The server communicates via stdio. It talks to the workspace API with `XAPPS_INTERNAL_API_BASE_URL`. Same-runtime launches usually authenticate with `XAPPS_INTERNAL_API_TOKEN`; external launches can also use `XAPPS_API_AUTHORIZATION`, `XAPPS_API_BEARER_TOKEN`, `MESHAGENT_TOKEN`, or `XAPPS_API_COOKIE`. Do not configure the MCP host with retired sheet-API URL variables.

### When to Use MCP vs CLI vs API

| Use Case | Best Choice |
|---|---|
| AI assistant building/editing workbooks | MCP |
| Shell scripts and automation pipelines | CLI |
| External app integrations | REST API |
| Quick one-off commands | CLI |

### Tool Categories

**Workbook Management:**
- `list_sheets`, `create_sheet`, `delete_sheet`, `rename_sheet`, `duplicate_sheet`
- `get_sheet_settings`, `update_sheet_settings`
- `get_workbook`, `create_new_workbook`, `create_workbook_file`, `set_workbook_title`
- `apply_semantic_ops` for validated Yjs-backed bulk workbook mutations
- `list_files`, `get_file`, `save_file`, `load_file`, `delete_file`
- `get_file_sharing`, `update_file_sharing`
- `list_starter_kits`, `apply_starter_kit`

**Spreadsheet Tools:**
- `read_cell`, `write_cell`, `clear_cell`
- `read_range`, `write_range` (bulk read/write 2D arrays)
- `format_cell`, `format_range`
- `list_columns`, `set_column_type`
- `get_cell_validation`, `set_cell_validation`, `clear_cell_validation`
- `list_named_ranges`, `set_named_range`, `delete_named_range`
- `get_cell_comment`, `set_cell_comment`, `clear_cell_comment`
- `get_cell_image`, `set_cell_image`, `clear_cell_image`
- `list_spreadsheet_charts`, `create_spreadsheet_chart`, `update_spreadsheet_chart`, `delete_spreadsheet_chart`
- `list_spreadsheet_tables`, `create_spreadsheet_table`, `get_spreadsheet_table`, `update_spreadsheet_table`, `delete_spreadsheet_table`
- `sort_spreadsheet_table`, `read_spreadsheet_table_groups`
- `list_conditional_formats`, `replace_conditional_formats`, `create_conditional_format`
- `set_cell_sparkline`, `merge_range`, `unmerge_range`

**Records Tools:**
- `records_list_tables`, `records_create_table`, `records_rename_table`, `records_delete_table`
- `records_list_fields`, `records_add_field`, `records_update_field`, `records_delete_field`, `records_reorder_fields`
- `records_list`, `records_get`, `records_create`, `records_patch`, `records_delete`, `records_bulk_update`, `records_bulk_delete`
- `records_trash`, `records_restore`, `records_duplicate`, `records_history`
- `records_comments`, `records_add_comment`, `records_edit_comment`, `records_delete_comment`
- `records_list_views`, `records_add_view`, `records_update_view`, `records_delete_view`, `records_set_active_view`
- `records_relation_preview`, `records_sql`

**Kanban Tools:**
- `list_kanban_cards`, `get_kanban_card`, `get_kanban_field_labels`, `set_kanban_field_labels`
- `create_card`, `update_card`, `delete_card`
- `list_kanban_lists`, `create_kanban_list`, `rename_kanban_list`, `color_kanban_list`, `delete_kanban_list`
- `reorder_kanban_lists`, `save_kanban_view`, `apply_kanban_automation_presets`, `sync_kanban_companion_views`, `get_kanban_report`

**Calendar Tools:**
- `list_events`, `create_event`, `update_event`, `delete_event`

**Timeline Tools:**
- `timeline_tasks`, `timeline_add_task`, `timeline_update_task`, `timeline_delete_task`
- `timeline_set_task_dependencies`, `timeline_clear_task_dependencies`, `timeline_set_task_milestone`, `timeline_report`

**Poll Tools:**
- `poll_config`, `poll_set_config`
- `poll_add_question`, `poll_update_question`, `poll_delete_question`, `poll_reorder_questions`
- `poll_add_option`, `poll_set_status`, `poll_submit_response`, `poll_responses`

**Canvas Tools:**
- `list_canvas_pages`, `set_canvas_artboard`
- `create_canvas_shape`, `create_canvas_text`, `create_canvas_image`

**Dashboard Tools:**
- `list_dashboard_widgets`, `get_dashboard_widget`
- `create_dashboard_widget`, `update_dashboard_widget`, `delete_dashboard_widget`
- toolkit helpers include `dashboard_add_map` for linked Map sheet widgets where MeshAgent toolkit tools are exposed

**File Viewer Tools:**
- `list_viewer_files`, `add_viewer_file`, `remove_viewer_file`
- `get_active_viewer_file`, `set_active_viewer_file`

**Floorplan Tools:**
- `list_floorplan_furniture`
- `add_wall`, `add_door`, `add_window`, `add_furniture`
- `add_floorplan_text`, `add_floorplan_note`, `add_floorplan_image`
- `set_floorplan_unit`, `set_floorplan_scale`, `set_wall_thickness`

**Gallery Tools:**
- `list_gallery_items`, `create_gallery_item`, `get_gallery_item`, `update_gallery_item`, `delete_gallery_item`

**Map Tools:**
- `get_map_config`, `update_map_config`
- `list_map_layers`, `create_map_layer`, `update_map_layer`, `delete_map_layer`

**Presentation Tools:**
- `list_presentation_shapes`

**Repository Tools:**
- `list_repo_files`, `get_repo_file`, `add_repo_file`, `update_repo_file`, `remove_repo_file`
- `list_repo_categories`, `update_repo_categories`, `refresh_repo_file`, `refresh_all_repo_files`

**Whiteboard Tools:**
- `set_whiteboard_view`
- `create_sticky_note`, `create_whiteboard_text`, `create_whiteboard_shape`, `create_whiteboard_image`
- `set_whiteboard_mind_connector_style`

**Games Tools:**
- Games: `games_scores`

**Protection Tools:**
- `lock_sheet`, `unlock_sheet`, `unprotect_sheet`
- `lock_sheet_group`, `unlock_sheet_group`, `unprotect_sheet_group`

**Sheet Groups & Automations:**
- `list_sheet_groups`, `create_sheet_group`, `replace_sheet_groups`, `update_sheet_group`, `delete_sheet_group`
- `list_workbook_automations`, `create_workbook_automation`, `replace_workbook_automations`, `run_workbook_automation`, `delete_workbook_automation`

**Generic Object and Upload Tools:**
- `list_objects`, `get_object`, `create_object`, `update_object`, `delete_object`
- `upload_image_data_url`

Typewriter currently opts out of stdio MCP registration; use its CLI, API-backed import/export paths, or UI workflow until MCP runtime tools are added.

### File Targeting

All MCP tools registered through the shared context accept an optional `file` parameter to target a specific saved workbook:

```json
{ "tool": "list_sheets", "arguments": { "file": "Stocks.json" } }
```

### Example: AI Agent Building a Dashboard

An AI assistant can build a complete dashboard in a few tool calls:

1. `create_sheet` → name: "Q3 Report", type: "dashboard"
2. `create_dashboard_widget` → KPI card for revenue from Budget sheet
3. `create_dashboard_widget` → Bar chart from Sales sheet
4. `create_dashboard_widget` → Treemap from Stock Data sheet
5. `create_dashboard_widget` → Map widget linked to a Revenue Map sheet
6. `create_dashboard_widget` → Text block with executive summary

### Tips for AI Agents Using MCP

- Use `read_range` to inspect data before building charts/dashboards
- Use `write_range` for bulk data population (much faster than individual cells)
- Dashboard treemap widget needs: `tmLabels` (ticker column), `tmSizes` (market cap), `tmColors` (% change)
- Dashboard map widgets should use `type:"map"` with `config.mapSource.kind:"sheet-view"` and `config.mapSource.sheetType:"map"` so the Map runtime remains the source of geographic behavior
- Kanban card APIs should provide `title` and `status`; sheets can hide those fields in the browser editor, where new cards receive a fallback title and the target list status.
- Always verify your writes with a `read_range` or `list_*` call

## 🧪 Advanced Patterns

This section covers multi-sheet workflows, data binding strategies, and patterns for building sophisticated workbook applications.

### Cross-Sheet Data Binding Patterns

The simplest cross-sheet pattern is a formula reference:

```text
=Budget!B2
=SUM('Sales Data'!C2:C100)
=COUNTIF('Sprint Board'!B:B, "Done")
```

For more complex bindings, combine these patterns:

**Rollup pattern:** One spreadsheet aggregates data from multiple sheets.

```text
# In a "Summary" spreadsheet:
A1: "Sales Total"    B1: =SUM('Sales Data'!C2:C100)
A2: "Tasks Done"     B2: =COUNTIF('Sprint Board'!B:B, "Done")
A3: "Events This Month" B3: =COUNT('Calendar'!A:A)
A4: "Budget Used"    B4: =SUM(Budget!B2:B50)
```

**Lookup pattern:** Pull specific values from structured sheets.

```text
# Look up a project status from a kanban board
=VLOOKUP("Website Redesign", 'Sprint Board'!A2:C50, 2)
```

**Conditional pattern:** Use IF with cross-sheet data to create alerts.

```text
=IF(Budget!B2 > Budget!C2, "OVER BUDGET", "OK")
=IF(COUNTIF('Sprint Board'!B:B, "Blocked") > 0, "Has blockers", "Clear")
```

### Building a Dashboard from Live Spreadsheet Data

1. Create a spreadsheet sheet with your source data (e.g., "Revenue Data").
2. Create a dashboard sheet (e.g., "Executive Dashboard").
3. Add widgets that reference the source sheet:
   - KPI card: data source = `Revenue Data`, range = `B2` (a single summary cell)
   - Bar chart: data source = `Revenue Data`, label column = `A`, value column = `B`
   - Treemap: configure `tmLabels`, `tmSizes`, `tmColors` pointing to source columns
   - Map: create a Map sheet for the geography, then add a dashboard map widget linked to that Map sheet

The dashboard updates automatically when the source spreadsheet data changes.

### Map Visualization from Spreadsheet Addresses

1. Create a spreadsheet with location data. Include columns for either:
   - `lat` and `lon` (direct coordinates), or
   - `address`, `location`, or `city` (for automatic geocoding)
2. Add optional columns: `label`, `value`, `color`, `size`, `image`, `status`.
3. Create a map sheet.
4. Click `+ Points` in the layers panel and select the source spreadsheet range.
5. The map geocodes addresses via Nominatim and places pins automatically.

For region/choropleth maps:

1. Create a spreadsheet with a `region`/`country`/`state` column and a `value` column.
2. Create a map sheet and click `+ Region`.
3. Select the source range. Numeric values produce a gradient; categorical values get distinct colors.
4. Toggle 3D mode for extruded polygon visualization.

### Reactive Automation (Triggers, Processes, Actions)

xApps uses a three-layer reactive system. Here is how to wire them together:

**Layer 1 -- Reactive Rules (signal only):**

Set up a rule that notifies when a condition is met:

```json
{
  "name": "Budget alert",
  "trigger": { "type": "threshold", "sheet": "Budget", "column": "B", "condition": "greaterOrEqual", "value": 50000 },
  "signal": { "type": "notify", "message": "Budget exceeded $50K", "severity": "warning" }
}
```

**Layer 2 -- Background Processes (scheduled writes):**

Set up a process that scans completed tasks and updates a timeline:

```json
{
  "name": "Close completed tasks",
  "interval": 30000,
  "source": { "type": "scan", "sheet": "Board", "matchColumn": "B", "matchValue": "Done", "markerColumn": "G", "markerValue": "processed" },
  "action": { "type": "batch-write", "operations": [{ "sheet": "Timeline", "cell": "E{{item.row}}", "value": "100" }] }
}
```

**Layer 3 -- Agent Actions (user-initiated):**

Add a right-click action for AI-assisted work:

```json
{
  "label": "AI: Summarize task",
  "sheetTypes": ["kanban"],
  "context": "card",
  "prompt": "Summarize the current status of task {{title}} including blockers and next steps",
  "scope": ["Board", "Notes"]
}
```

### Template Variables in Presentations and Visual Surfaces

Use `{{SheetName!CellRef}}` syntax to embed live data in visual content:

**Presentation deck with live metrics:**

```text
Slide 1 title: "Q3 Revenue: {{Budget!B2|$}}"
Slide 1 body:  "Growth rate: {{Budget!C2|%}} vs last quarter"
               "Team size: {{Headcount!B1}}"
```

**Canvas design with dynamic labels:**

```text
Text object: "{{Tenants!A3}} — Suite {{Tenants!B3}}"
Text object: "Monthly rent: {{Tenants!C3|$}}"
```

**Format specifiers:** `|$` (currency), `|%` (percentage), `|.0f` (integer), `|.1f` (one decimal), `|.2f` (two decimals).

### Live Data Embedding Across Sheets

Several sheet types can embed content from other sheets:

- **Dashboard widgets** pull data ranges from spreadsheets, kanban boards, timelines, and calendars.
- **Canvas, Whiteboard, and Presentation** text objects support `{{}}` template variables.
- **Gallery, Canvas, Whiteboard, and Presentation** images can link live to image sources in other visual sheets using the "Reference existing" picker.
- **Canvas, Whiteboard, Presentation, Floor Plan, and Document** sheets can embed a live map view.
- **Spreadsheet cells** can embed a compact map preview.

### Multi-Sheet Workflow Examples

**Project management workbook:**

| Sheet | Type | Role |
|---|---|---|
| Brief | Document | Project scope and requirements |
| Roadmap | Timeline | Milestones and dependencies |
| Sprint Board | Kanban | Current work items |
| Budget | Spreadsheet | Cost tracking and formulas |
| Executive Dashboard | Dashboard | KPI widgets from all sheets |
| Design | Canvas | Visual mockups and assets |
| Meeting Notes | Document | Ongoing notes and decisions |

Wire them together:
- Dashboard KPI cards reference `Budget!B2` and `=COUNTIF('Sprint Board'!B:B, "Done")`
- Timeline tasks sync progress to the kanban board via background processes
- Presentation slides use `{{Budget!B2|$}}` for live revenue figures
- Gallery images are linked to Canvas design assets

**Home renovation workbook:**

| Sheet | Type | Role |
|---|---|---|
| Floor Plan | Floor Plan | Room layouts with measurements |
| Materials | Gallery | Furniture and materials catalog |
| Construction Budget | Spreadsheet | Cost estimates and actuals |
| Schedule | Timeline | Renovation phases |
| Notes | Document | Contractor notes and decisions |
| Dashboard | Dashboard | Budget vs actual overview |

**Sales operations workbook:**

| Sheet | Type | Role |
|---|---|---|
| Pipeline | Kanban | Deal stages |
| Territory Map | Map | Geographic coverage |
| Revenue Data | Spreadsheet | Numbers and formulas |
| Forecast Dashboard | Dashboard | KPI widgets |
| Pitch Deck | Presentation | Customer-facing slides |
| Competitive Intel | Gallery | Competitor screenshots and notes |

## 📚 Reference Library

For deeper machine-facing reference, use:

> 🤖 Agent example: an agent can consult the CLI, API, MCP, and automation references before acting so it uses stable contracts instead of guessing at workbook behavior.

- [CLI.md](/docs/CLI.md)
- [API.md](/docs/API.md)
- [MCP.md](/docs/MCP.md)
- [AUTOMATIONS.md](/docs/AUTOMATIONS.md)

## 🔧 Troubleshooting

> 🤖 Agent example: an agent can diagnose stale UI, wrong workbook file targeting, lock errors, or importer noise by checking the saved file, active sheet, and machine-facing responses before retrying.

### “A change I just made is not visible”

- Hard refresh the browser first (`Ctrl/Cmd + Shift + R`).
- Confirm you are on the expected workbook file (check the title bar or `File` menu recent files).
- If you edited a client JS file during development, bump the version in `core/sheet-client-manifest.js` -- the server sends `Cache-Control: immutable` headers.

### “A formula shows #ERROR!”

Common causes and fixes:

- **Wrong function name.** Check spelling. Only the functions listed in the Formula Reference section are supported. Unsupported Excel functions return `#ERROR!`.
- **Wrong number of arguments.** VLOOKUP needs at least 3 arguments. SUMIF needs at least 2. SUMIFS/COUNTIFS use criteria pairs. ROUND needs 1-2.
- **Missing range.** Make sure ranges use the `A1:B10` format. Bare column references like `A:A` expand differently than full ranges.
- **Circular reference.** If cell A1 references B1 and B1 references A1, both will show `#ERROR!`. Check your formula chain.
- **Cross-sheet ref to missing sheet.** If the referenced sheet was deleted or renamed, the formula cannot resolve. Update the sheet name in the formula.
- **GEO functions with non-numeric coordinates.** All GEO functions require numeric latitude and longitude values. Text or empty cells cause `#ERROR!`.

### “Cross-sheet reference not working”

- Verify the sheet name is spelled exactly right (case-sensitive).
- If the sheet name contains spaces, wrap it in single quotes: `='Sheet Name'!A1`.
- Confirm the target cell exists and contains data.
- Check for circular references across sheets. The circular-reference detector uses `sheetName!cellRef` as keys.

### “Changes not saving / revision conflict”

- Make sure the workbook is saved as a file first (`File -> Save Workbook`). Unsaved in-memory workbooks do not persist.
- If multiple collaborators are editing, Yjs handles conflict resolution automatically. Hard refresh if the UI seems stale.
- Check the browser console for WebSocket connection errors. A lost connection means changes queue locally until reconnection.
- Use `Ctrl/Cmd + S` frequently to trigger explicit saves.

### “A sheet tab disappeared”

- The sheet might be inside a group. Click group tabs to expand them and look for the sheet.
- Check `Sheet -> Sheet Groups...` to see if the sheet was added to a group.
- If the sheet was deleted, use undo (`Ctrl/Cmd + Z`) immediately. Once saved, deletion is permanent.

### “Images not loading”

- Verify the image URL is accessible (not blocked by CORS or authentication).
- For uploaded images, confirm the upload completed successfully. Check the `sheets/uploads/` directory.
- For live image references, make sure the source sheet and source object still exist. A deleted source shows a broken-source state.
- Hard refresh the browser to clear any cached broken image states.

### “Collaboration sync feels broken”

- Hard refresh all browser tabs.
- Confirm all participants are connected to the same saved workbook or workspace URL.
- Check the WebSocket connection status. A network change or server restart may drop the connection temporarily.
- Yjs will reconcile state on reconnection, but large divergences may take a moment to merge.

### “Large workbook is slow”

- Workbooks with many sheets or very large data ranges can slow down rendering.
- Reduce the number of cross-sheet formula references if possible -- each reference triggers evaluation on the target sheet.
- Use `clear-sheet` to remove unused data from sheets you no longer need.
- Split very large datasets across multiple workbooks if performance degrades significantly.
- Sparkline formulas in many cells add SVG rendering overhead -- consider using them selectively.

### “CSV or Excel import is wrong”

- For CSV: check that the delimiter is a comma. Tab-separated or semicolon-separated files need preprocessing.
- For Excel: only the active sheet is imported by default. Multi-sheet workbooks may need multiple imports.
- Use `clear-sheet` before re-importing to avoid leftover data from a previous import mixing with new data.
- Verify encoding. UTF-8 is expected. Other encodings may produce garbled text.

### “Map data not matching countries”

- Country names must match the TopoJSON dataset. Use standard English names or ISO codes.
- Common aliases like “USA”, “UK”, “South Korea” are supported. Check the Map documentation for the full alias list.
- US state abbreviations like “CA”, “NY”, “TX” are supported in the US States geography view.
- If using point layers with addresses, geocoding depends on Nominatim (OpenStreetMap). Ambiguous addresses may resolve to unexpected locations.

### “Repository tracking lost”

- Repository Sheet tracks files in the `sheets/` directory. If files were moved or deleted outside xApps, the tracked status becomes stale.
- Re-open the Repository Sheet to refresh the file tree from the filesystem.
- Repository sheets are excluded from Yjs collaboration -- disk is the source of truth.

### “Canvas objects not rendering”

- Check zoom level. Objects outside the current viewport or on a different page will not be visible.
- Verify the object is not on a hidden or locked layer.
- For image objects, confirm the image URL is valid and accessible.
- Use the minimap to locate objects that may have been moved far from the artboard center.
- On mobile, Canvas uses a bottom tool dock instead of the desktop rail -- look for the `Canvas` pill.

### “Template variables not resolving”

- Confirm the syntax is exactly `{{SheetName!CellRef}}` with double curly braces.
- Sheet names with spaces need single quotes inside the braces: `{{'Sheet Name'!A1}}`.
- Template variables resolve only in rendered view mode. Edit mode shows the raw `{{}}` syntax.
- If the referenced sheet was deleted, the variable shows `#REF!`.
- If the referenced cell is empty, the variable shows nothing (blank).

### “Clipper not capturing images”

- The xApps Web Clipper works on Design Canvas, Whiteboard, Gallery, and Floor Plan targets.
- Ensure the clipper is pointed at the correct saved workbook and compatible sheet.
- For canvas targets, the clipper defaults to the active page -- switch pages if needed.
- Some websites block image extraction due to CORS policies. Try right-clicking and copying the image URL manually.

### “Presentation slides not importing correctly from PPTX”

- Complex PowerPoint features (animations, transitions, embedded video, SmartArt) are not fully supported.
- Text boxes, basic shapes, and images transfer best.
- If a slide looks wrong, try recreating it manually in the xApps presentation editor.
- Re-import after importer updates if an earlier import was incomplete.

### “DXF import looks noisy”

- CAD files often contain many non-architectural layers (dimensions, hatches, blocks).
- Use layer visibility controls to hide non-essential layers.
- Re-import after importer fixes if an earlier import looked wrong.
- The layer system auto-creates layers from the DXF file for selective toggling.

### “A sheet says it is locked”

- Unlock it from the UI: `Sheet -> Protect Sheet... -> Unlock`.
- Or unlock through CLI/MCP/API first, then retry.

### “CLI / API says a resource is locked”

- Unlock the sheet or group first using the password.
- Then retry with the stored unlock token/session.
- Browser sessions remember unlock state temporarily. CLI uses explicit unlock tokens.

### “Dashboard widgets show no data”

- Verify the data source sheet name and range are correct in the widget editor.
- The source sheet must exist and contain data in the specified range.
- For KPI widgets, the data source range should point to a single cell.
- For chart widgets, the range should include both label and value columns.
- For treemap widgets, configure `tmLabels`, `tmSizes`, and `tmColors` column ranges.
- For map widgets, verify `config.mapSource.sheet` points to an existing Map sheet.

### “Automations not running”

- Automations run on demand, not automatically. Use `Tools -> Automations...` to run them.
- Check that the automation definition is valid JSON with a supported action type.
- Supported actions: `create_sheet`, `duplicate_sheet`, `rename_sheet`, `set_cell`, `apply_floorplan_template`, `apply_starter_kit`.

### “Triggers not firing”

- Check that the trigger is enabled in `Tools -> Triggers...`.
- Reactive rules are signal-only -- they notify, badge, or log but do not write data.
- Use `test-trigger` (CLI) or the test-fire button to verify the trigger definition works.
- Background processes run on a schedule. If a process stopped, check if it was auto-disabled after 5 consecutive failures.

### “Help content looks out of date”

- Hard refresh once so the latest help markdown is fetched from the server.
