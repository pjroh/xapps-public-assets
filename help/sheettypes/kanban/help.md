## Kanban Boards

### Drag work across stages

Kanban sheets turn a workbook tab into a visual board with lists (columns), cards, labels, due dates, assignees, checklists, and cover images. They are ideal for sprint planning, content pipelines, approvals, hiring stages, and any workflow that moves items from one state to another.

Behind the board, every card is stored as spreadsheet cell data, so other sheets can reference and aggregate kanban data with formulas.

> 🤖 Agent example: an agent can seed lists, create cards from a spec, assign owners, and keep requested-by / created-by history aligned while a human reviews priority and due dates.

![Kanban board with active workflow columns and cards](/help-assets/screenshots/kanban-board.png)

---

### Features at a Glance

- Customizable lists (columns) with color coding
- Cards with title, description, labels, assignee, due date, color, cover image, checklist, and comments
- Per-sheet field labels, so one board can say "Owner" and another can say "Sales person" while stored card fields stay canonical
- Requested-by and created-by fields for tracking accountability
- Drag-and-drop cards between lists and within lists
- Drag-and-drop to reorder lists
- Filter bar: search text, assignee, label, and due date filters
- Swimlanes: group by assignee or label
- Card aging: visual fade for cards that have not moved in 3, 7, or 14+ days
- Card cover images (upload or URL)
- Sorting: by title, due date, or status
- Compact card toggle
- Context menus for editing and deleting cards
- Cross-sheet formula integration
- Undo/redo support
- CLI and API for full programmatic control

---

### Getting Started

1. **Create a kanban sheet.** Click the `+` button in the sheet tab bar and select "Kanban." A default board with "To Do," "In Progress," and "Done" lists is created.
2. **Add a card.** Click the "+ Add card" button at the bottom of any list. Fill in the title and optional details, then click Save.
3. **Move or reorder a card.** Drag a card from one list and drop it on another to update its status, or drop it above/below another card in the same list to set a manual order.
4. **Add a list.** Click "+ Add list" on the right side of the board, or use Insert > Add list from the menu.
5. **Filter cards.** Use the filter bar at the top to search by text, filter by assignee, label, or due date.
6. **Group cards.** Use the grouping dropdown to create swimlanes by assignee or label.
7. **Customize field labels.** Click "Field labels" on the kanban toolbar to rename card fields for this sheet only.

---

### Card Properties

Each card stores the following fields:

| Field | Column | Description |
|---|---|---|
| Title | A (col 0) | Card name; the editor uses "Untitled card" when this field is hidden |
| Status | B (col 1) | Which list the card belongs to |
| Description | C (col 2) | Longer text description |
| Labels | D (col 3) | Comma-separated label tags |
| Due Date | E (col 4) | Date in YYYY-MM-DD format |
| Card Color | F (col 5) | Hex color for left border accent |
| Checklist | G (col 6) | JSON array of `{text, done}` items |
| Cover Image | H (col 7) | URL of cover image |
| Assignee | I (col 8) | Person assigned to the card |
| Last Moved | J (col 9) | ISO timestamp of last status change |
| ID | K (col 10) | Optional custom card identifier |
| Requested By | L (col 11) | Person who requested the work |
| Created By | M (col 12) | Person who created the card |
| Activity | N (col 13) | JSON activity log for card changes |
| Custom Fields | O (col 14) | JSON object for extension data |
| Priority | P (col 15) | Priority label |
| Comments | Q (col 16) | JSON array of card discussion comments |

### Field Labels

Each kanban sheet can override display labels for card fields without changing the stored API/card JSON keys. For example, a sales board can display "Sales person" for `assignee` and "Close Date" for `due`, while another board continues to display the defaults.

Click "Field labels" on the board toolbar, edit the labels, and Save. Empty labels reset to defaults. The setting is stored on the sheet as `kanbanFieldLabels`; the resolved defaults are exposed as `kanbanResolvedFieldLabels` through the settings API.

### Card Fields

Each kanban sheet can choose which standard card fields are visible and can define its own custom card fields. Use this for domain cards such as CRM opportunities with fields like `startDate`, `stopDate`, `amount`, `account`, or `probability`.

Click "Card fields" on the board toolbar, show or hide any standard field including Title and Status, add or delete custom field definitions, and Save. Standard fields remain stored in canonical row-backed columns for API compatibility, but hidden fields are not rendered in that sheet's card editor. Custom definitions are stored on the sheet as `kanbanCustomFields`, field visibility is stored as `kanbanCardFieldLayout`, and values are stored on each card in `customFields`. These settings are available through the card API, SDK, CLI, toolkit, and MCP.

---

### Lists (Columns)

Lists define the stages of your workflow. Default lists are "To Do," "In Progress," and "Done," but you can fully customize them.

**Add a list:** Click "+ Add list" on the board or use Insert > Add list.

**Rename lists:** Use Surface > Rename lists to edit all list names as a comma-separated string. Cards in renamed lists are automatically updated.

**Delete a list:** Use Surface > Delete list and type the exact name. Cards in the deleted list remain but become orphaned until reassigned.

**Reorder lists:** Drag a list header and drop it at another position. Lists swap positions visually and in the data.

**Color a list:** Click the color picker in the list header to set a column color. The color appears as a left border on the header and a subtle background tint on the column.

**Collapse a list:** Click the collapse control in a list header to reduce the list to a narrow rail. Click the restore control on the rail to expand it again. Collapsed lists are saved with the board.

---

### Filtering

The filter bar at the top of the board offers four filters that can be combined:

| Filter | Options |
|---|---|
| Search | Free text -- matches title, assignee, and description |
| Assignee | Dropdown of all assignees found on cards |
| Label | Dropdown of all labels found on cards |
| Due Date | "All dates", "Overdue", "Due this week", "No due date" |

A "Clear" button appears when any filter is active.

---

### Swimlanes (Grouping)

Use the grouping dropdown (far right of the filter bar) to organize cards into horizontal swim lanes:

- **Group by assignee** -- each assignee gets their own row of lists, plus an "Unassigned" lane
- **Group by label** -- each label gets its own lane; cards with multiple labels appear in multiple lanes; unlabeled cards go to "No label"

---

### Card Aging

Cards that have not moved between lists show visual aging:

| Days Since Last Move | Visual Effect |
|---|---|
| 3+ days | Slightly faded (opacity 0.82) |
| 7+ days | Noticeably faded (opacity 0.65) + "aging" class |
| 14+ days | Very faded (opacity 0.45) |

The age in days is shown in the card footer. This helps identify stuck or forgotten work.

---

### Card Editor

Click any card to open the full editor dialog. Features include:

- **Title** -- card name; can be hidden per sheet
- **Status** -- dropdown of all lists; can be hidden per sheet
- **Description** -- multi-line text area
- **Labels** -- comma-separated input
- **Assignee** -- free text
- **Requested by** / **Created by** -- accountability fields (if only one is filled, the other auto-copies)
- **Due Date** -- date picker
- **Card Color** -- color swatch picker for the card's left border accent
- **Cover Image** -- upload a file or paste a URL; shows a preview
- **Checklist** -- add items, check/uncheck, delete items; progress shown on the card as a fraction (e.g., "3/5")
- **Comments** -- switch to the Comments tab and use Add first comment for a new thread, or add review/progress notes to an existing thread
- **Delete** button (existing cards only)

To manually prioritize a list without changing statuses, drag a card above or below another card in the same list. The rendered order updates immediately and is saved with the workbook.

---

### Sorting

From the View menu:

- **Sort by Title** -- alphabetical sort of all cards
- **Sort by Due Date** -- cards with due dates come first, sorted chronologically
- **Sort by Status** -- groups cards by their list/status

Sorting rewrites the underlying row data.

---

### Context Menu

Right-click a card to access:

- Edit card
- Delete card

---

### Cross-Sheet Formula Integration

Kanban data lives in standard cells, so spreadsheet formulas can query it:

```text
=COUNTIF('Sprint Board'!B:B, "Done")
=COUNTIF('Sprint Board'!B:B, "In Progress")
=COUNTIF('Sprint Board'!E:E, "P1")
=COUNTIF('Sprint Board'!I:I, "Alice")
```

Use this to build dashboards or reports that summarize kanban board status without leaving the workbook.

---

### Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl/Cmd` + `Z` | Undo last action |
| `Ctrl/Cmd` + `Y` | Redo |
| `Enter` (in checklist input) | Add checklist item |

Most kanban interactions are mouse/touch-driven (drag-drop, click to edit).

---

### CLI Commands

All commands use the pattern:
```
xapps <command> --file <WorkbookName>
```

#### Batch Semantic Ops

```bash
printf '{"op":"kanban.addCard","card":{"title":"Draft launch notes","status":"To Do"}}\n' | xapps kanban batch "Sprint Board" --stdin
# Output: Applied 1 semantic op
```

#### List Cards

```bash
xapps cards "Sprint Board"
# Output:
#   #0 [To Do] Set up CI pipeline
#   #1 [In Progress] Design landing page
#   #2 [Done] Fix login bug

xapps cards "Sprint Board" --status "In Progress"
# Output:
#   #1 [In Progress] Design landing page
```

#### Card JSON

```bash
xapps card-json "Sprint Board" TASK-42
# Output:
# {
#   "row": 3,
#   "id": "TASK-42",
#   "title": "Implement search",
#   "status": "To Do",
#   "comments": []
# }
```

#### Field Labels

```bash
xapps kanban-field-labels "Sprint Board"
# Output:
# {
#   "kanbanFieldLabels": {},
#   "kanbanResolvedFieldLabels": {
#     "assignee": "Assignee",
#     "due": "Due Date"
#   }
# }

xapps set-kanban-field-labels "Sprint Board" '{"assignee":"Sales person","due":"Close Date"}'
# Output: Kanban field labels updated: 2 overrides
```

#### Custom Card Fields

```bash
xapps kanban-custom-fields "Sales Pipeline"
# Output:
# {
#   "kanbanCustomFields": []
# }

xapps set-kanban-custom-fields "Sales Pipeline" '[{"id":"startDate","label":"Start Date","type":"date"},{"id":"stopDate","label":"Stop Date","type":"date"},{"id":"amount","label":"Amount","type":"number"}]'
# Output: Kanban custom fields updated: 3 fields
```

#### Card Field Layout

```bash
xapps kanban-card-field-layout "Sales Pipeline"
# Output:
# {
#   "kanbanCardFieldLayout": []
# }

xapps set-kanban-card-field-layout "Sales Pipeline" '[{"id":"title","source":"builtin","visible":true},{"id":"priority","source":"builtin","visible":false},{"id":"amount","source":"custom","visible":true}]'
# Output: Kanban card field layout updated: 3 entries
```

#### Add a Card

```bash
xapps add-card "Sprint Board" "Implement search" --list "To Do" --desc "Full-text search for docs" --due 2026-04-15 --labels "feature,P1" --custom-fields '{"startDate":"2026-06-01"}' --id TASK-42
# Output: Card created (row 3, id=TASK-42)

# Minimal card (uses first list by default):
xapps add-card "Sprint Board" "Quick fix"
# Output: Card created (row 4)
```

#### Update a Card

```bash
xapps update-card "Sprint Board" 1 '{"status":"Done","labels":"feature,P1,shipped"}'
# Output: Card 1 updated

# Update by custom ID:
xapps update-card "Sprint Board" TASK-42 '{"assignee":"Alice","due":"2026-04-20"}'
# Output: Card TASK-42 updated (id=TASK-42)

xapps update-card "Sales Pipeline" OPP-42 '{"customFields":{"startDate":"2026-06-01","stopDate":"2026-06-30","amount":12000}}'
# Output: Card OPP-42 updated (id=OPP-42)
```

#### Delete a Card

```bash
xapps delete-card "Sprint Board" 1
# Output: Card 1 deleted

xapps delete-card "Sprint Board" TASK-42
# Output: Card TASK-42 deleted (id=TASK-42)
```

#### Card Comments

```bash
xapps card-comments "Sprint Board" TASK-42
# Output:
#   #0 2026-05-03T10:15:00.000Z Alice: Ready for review.

xapps add-card-comment "Sprint Board" TASK-42 "Ready for review." --author Alice --type progress
# Output: Comment added to kanban card TASK-42 (1 comment)
```

#### List Management

**List all lists:**
```bash
xapps lists "Sprint Board"
# Output:
#   To Do (3 cards)
#   In Progress (2 cards)
#   Done (5 cards)
```

**Add a list:**
```bash
xapps add-list "Sprint Board" "Code Review"
# Output: List added: Code Review
```

**Rename a list:**
```bash
xapps rename-list "Sprint Board" "Code Review" "Peer Review"
# Output: List renamed: Code Review -> Peer Review
```

**Set list color:**
```bash
xapps color-list "Sprint Board" "Done" "#4caf50"
# Output: List color updated: Done
```

**Delete a list:**
```bash
xapps delete-list "Sprint Board" "Peer Review"
# Output: List deleted: Peer Review
```

**Reorder lists:**
```bash
xapps reorder-lists "Sprint Board" '["Backlog","To Do","In Progress","Done"]'
# Output: Lists reordered on Sprint Board
```

---

### API Endpoints

```bash
# List all cards
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/cards

# List cards filtered by status
curl -H 'X-XApps-File: MyWorkbook.json' "$XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/cards?status=Done"

# Create a card
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/cards \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"title":"New task","status":"To Do","description":"Details here","labels":"bug","due":"2026-04-15","assignee":"Bob","customFields":{"startDate":"2026-06-01"},"id":"TASK-99"}'

# Update a card (by row number or custom ID)
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/cards/TASK-99 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"status":"In Progress","assignee":"Alice"}'

# Delete a card
curl -X DELETE -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/cards/0

# Read and replace custom card field definitions
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Sales%20Pipeline/custom-fields
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Sales%20Pipeline/custom-fields \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"kanbanCustomFields":[{"id":"startDate","label":"Start Date","type":"date"},{"id":"stopDate","label":"Stop Date","type":"date"},{"id":"amount","label":"Amount","type":"number"}]}'

# Read and replace the visible card fields for one sheet
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Sales%20Pipeline/field-layout
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Sales%20Pipeline/field-layout \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"kanbanCardFieldLayout":[{"id":"title","source":"builtin","visible":true},{"id":"priority","source":"builtin","visible":false},{"id":"amount","source":"custom","visible":true}]}'

# List all lists
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/lists

# Add a list
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/lists \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"name":"Blocked"}'

# Rename a list
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/lists/Blocked \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"name":"On Hold"}'

# Set list color
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/lists/Done \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"color":"#4caf50"}'

# Delete a list
curl -X DELETE -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/lists/On%20Hold

# Reorder lists
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/lists/reorder \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"order":["Backlog","To Do","In Progress","Done"]}'
```

---

### Agent/AI Workflow Recipes

#### Recipe 1: Seed a sprint board from a list of tasks

An AI agent receives a text file with tasks and builds a complete sprint board.

```bash
# Step 1: Create the lists
xapps add-list "Sprint 7" "Backlog"
xapps add-list "Sprint 7" "To Do"
xapps add-list "Sprint 7" "In Progress"
xapps add-list "Sprint 7" "Review"
xapps add-list "Sprint 7" "Done"
xapps color-list "Sprint 7" "Done" "#4caf50"
xapps color-list "Sprint 7" "In Progress" "#2196f3"

# Step 2: Add cards with metadata
xapps add-card "Sprint 7" "Auth service migration" --list "To Do" --labels "backend,P0" --due 2026-04-12 --id AUTH-1 --created-by "Agent"
xapps add-card "Sprint 7" "Update API docs" --list "Backlog" --labels "docs,P2" --id DOCS-1 --created-by "Agent"
xapps add-card "Sprint 7" "Fix checkout crash" --list "To Do" --labels "bug,P0" --due 2026-04-11 --id BUG-42 --created-by "Agent"

# Step 3: Verify
xapps lists "Sprint 7"
xapps cards "Sprint 7"
```

#### Recipe 2: Daily standup report from board state

An agent reads the board and generates a status summary.

```bash
# Step 1: Get all cards
xapps cards "Sprint 7"
# Output:
#   #0 AUTH-1 [To Do] Auth service migration
#   #1 DOCS-1 [Backlog] Update API docs
#   #2 BUG-42 [To Do] Fix checkout crash

# Step 2: Get cards in progress
xapps cards "Sprint 7" --status "In Progress"
# Output:
#   (no cards)

# Step 3: Get list summary
xapps lists "Sprint 7"
# Output:
#   Backlog (1 cards)
#   To Do (2 cards)
#   In Progress (0 cards)
#   Review (0 cards)
#   Done (0 cards)

# Step 4: Move a card (agent simulating standup update)
xapps update-card "Sprint 7" BUG-42 '{"status":"In Progress","assignee":"Alice"}'
```

#### Recipe 3: Bulk update cards matching criteria

An agent needs to close all P2 cards and reassign overdue items.

```bash
# Step 1: List all cards to find targets
xapps cards "Sprint 7"

# Step 2: Move completed items to Done
xapps update-card "Sprint 7" DOCS-1 '{"status":"Done"}'

# Step 3: Reassign overdue cards
xapps update-card "Sprint 7" AUTH-1 '{"assignee":"Bob","labels":"backend,P0,escalated"}'
```

---

### Troubleshooting

**1. Card not appearing on the board**
A card must have a non-empty stored title (column A). If a sheet hides Title in the card editor, new cards use "Untitled card" automatically. If the title cell is empty, the card is invisible. Also verify the card's status (column B) matches one of the board's list names exactly.

**2. Drag and drop not working**
Ensure you are dragging from the card body, not from the color picker or other interactive elements inside the card. Column drag requires starting from the column header area, not from cards within it.

**3. Cards appear in the wrong list**
The status value in column B must exactly match a list name (case-sensitive). Use `xapps cards "Board"` to inspect card statuses and `xapps lists "Board"` to see list names.

**4. Filter returns no results**
Filters are combined with AND logic. If you set both an assignee and a label filter, only cards matching both appear. Use the "Clear" button to reset all filters.

**5. Card aging shows unexpected values**
Card aging is based on the "Last Moved" timestamp (column J), which updates only when a card's status changes. Editing other card fields does not reset the age timer.

**6. Checklist not saving**
The checklist is stored as a JSON array in column G. If you see parse errors, the JSON may be malformed. When using the CLI, pass checklist data inside the update JSON: `'{"checklist":[{"text":"Item 1","done":false}]}'`.

**7. Cover image not displaying**
The image URL must be accessible from the browser. Local file paths do not work -- use the upload feature or a publicly accessible URL.

---

### Tips and Tricks

- **Accountability fields:** Fill in "Requested by" and "Created by" to track who asked for work vs. who created the card. If you fill only one, the other auto-copies.
- **Custom IDs:** Use the `--id` flag when creating cards to assign stable identifiers (like JIRA keys) that survive row reordering.
- **Formula-powered dashboards:** Since kanban data is in cells, create a spreadsheet sheet with `=COUNTIF('Board'!B:B, "Done")` to build live dashboards.
- **Swimlane views:** Group by assignee during standups to see each person's workload at a glance, or group by label to review priorities.
- **Card aging:** Use aging as a visual indicator of blocked work. Cards fading to near-transparent after 14 days are a strong signal to investigate.
- **Bulk seeding:** When setting up a new board programmatically, create lists first (with `add-list`), then add cards. The first list becomes the default for cards without an explicit `--list` flag.

---

### Reports, Saved Views, and Companion Sheets

Beyond the per-card commands, kanban ships three workflow primitives.

#### `kanban-report` — board snapshot for agent / standup loops

```bash
xapps kanban-report <board>
```

Prints a one-line summary of the board: `<n> cards across <m> lists; <k> overdue; <p> stale.` The xApps agent rules recommend opening every coding session with this against the engagement's tracking board so the agent sees the workflow shape before diving in.

#### `save-kanban-view` — bookmark a filter as a reusable view

```bash
xapps save-kanban-view <board> <name> [--search <text>] [--assignee <name>] [--label <label>] [--due <mode>] [--group-by <field>]
```

Saves the named filter combination on the board. Loading the view from the UI reapplies all four facets in one click. Useful for "My open work", "Overdue this sprint", "Backlog grouped by owner", etc. `--due` accepts `today`, `this-week`, `overdue`, or a `YYYY-MM-DD` floor.

#### `sync-kanban-views` — fan kanban data into Calendar / Timeline / Dashboard

```bash
xapps sync-kanban-views <board>
```

Materializes companion sheets from the kanban board:

- **Calendar** — every card with a `due` date as a calendar event.
- **Timeline** — every card as a Gantt bar from `created` to `due`.
- **Dashboard** — KPI tiles for total cards, % done, overdue count, and stale-aging buckets.

The companions are read-only mirrors; mutate the kanban board, then re-run `sync-kanban-views` to refresh them.

#### `kanban-automation` — opt-in board behaviors

```bash
xapps kanban-automation <board> <preset>...
```

Applies one or more named automations to the board. Built-in presets:

| Preset | What it does |
|---|---|
| `done_label` | Auto-stamps the `done` label when a card moves to a list named `Done` (or list color matches the done preset) |
| `checklist_done` | Marks a card done automatically when its checklist hits 100% |
| `review_priority` | Re-prioritizes cards in a `Review` list by due date so the oldest unresolved item bubbles up |

Multiple presets compose — pass them as separate args. Re-running with no presets clears all automations on the board.
