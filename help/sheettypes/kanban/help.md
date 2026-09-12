## Kanban Boards

### Run a task from capture to completion

Start with a small board whose lists describe real handoffs. A card is the work to finish; its list is the current stage. Use labels for categories and an assignee for responsibility, rather than creating a new list for every person.

1. Add a card to the first list and give it a concrete outcome, such as “Approve launch copy.” Open the card to add the brief, owner, due date, and checklist.
2. Add the working file or link as an attachment. Use comments for decisions and updates so the next person can understand the handoff without guessing from the title.
3. Click **Save Card** and wait for **Saved**. The editor stays open so you can continue; close it to return to the board. Move the card to the next list when work actually changes stage. Reordering within a list changes its manual position, not its stage.
4. Filter by assignee, label, or due date to review one part of the workload. Clear filters before assuming a card disappeared. Grouping creates swimlanes over the same cards; it does not duplicate the underlying work.
5. Move finished work to your completed list. Archive cards you want out of the active board, and use **Archived items** to review or restore them. Permanent deletion is a separate action for already archived cards.

### Review a board without losing context

![Kanban card editor with title, status, labels, description, and Save Card control](/help-assets/screenshots/kanban-card-editor.png)

*The local example shows legacy assignee text and unavailable room membership controls. A connected room supplies its own identity-backed member choices.*

Open a card to inspect its checklist, attachments, comments, and recorded activity. Assignee text, room members, and watchers serve different purposes: assignment names responsibility; identity-backed members and watchers support collaboration and notifications. A missing notification should be checked in the recipient's inbox and settings, not inferred from an assignee label alone.

For repeated reviews, use the board's saved-view and reporting controls described below. A view presents the existing board; a companion sheet gives you another workbook surface to work with. Check the resulting sheet or view before assuming changes flow in both directions.

### Change several cards together

Select card checkboxes, or Shift-click a range within one list. Review the selected count, then choose **Move to**, **Copy to**, **Add label**, **Assign**, or **Archive**. Copy creates new card IDs; move keeps the existing cards. Use **Clear** or Escape when finished so the next action applies to the intended card. Selection is limited to 20 cards at once.

![Two selected Kanban cards with the Move, Copy, Label, Assign, Archive, and Clear action rail](/help-assets/screenshots/kanban-multi-card-selection.png)

### Drag work across stages

Kanban sheets turn a workbook tab into a visual board with lists (columns), cards, labels, due dates, assignees, checklists, cover images, and first-class file/link attachments. They are ideal for sprint planning, content pipelines, approvals, hiring stages, and any workflow that moves items from one state to another.

Behind the board, every card is stored as spreadsheet cell data, so other sheets can reference and aggregate kanban data with formulas.

> 🤖 Agent example: an agent can seed lists, create cards from a spec, assign owners, and keep requested-by / created-by history aligned while a human reviews priority and due dates.

![Kanban board with active workflow columns and cards](/help-assets/screenshots/kanban-board.png)

---

### Features at a Glance

- Customizable lists (columns) with full-fill color coding
- Cards with title, description, labels, assignee, due date, color, cover image, file/link attachments, checklist, and comments
- Identity-backed card members and watchers, plus a recipient-private durable notification inbox
- Per-sheet field labels, so one board can say "Owner" and another can say "Sales person" while stored card fields stay canonical
- Requested-by and created-by fields for tracking accountability
- Drag-and-drop cards between lists and within lists
- Multi-card selection and bulk Move, Copy, Add label, Assign, and Archive actions
- Drag-and-drop to reorder lists
- Filter bar: search text, assignee, label, and due date filters
- Swimlanes: group by assignee or label
- Card aging: visual fade for cards that have not moved in 3, 7, or 14+ days
- Card cover images (upload or URL)
- Sorting: by title, due date, or status
- Compact card toggle
- Context menus for editing, selecting, and archiving cards
- Cross-sheet formula integration
- Undo/redo support
- CLI and API for full programmatic control

---

### Getting Started

1. **Create a kanban sheet.** Click the `+` button in the sheet tab bar and select "Kanban." A default board with "To Do," "Research," "Draft," "In Progress," "Review," and "Done" lists is created — a hand-off pipeline that humans and agents can share.
2. **Add a card.** Click the `+` button in a list header for quick capture, click "+ Add card" at the bottom of any list, or double-click the gap between two cards to insert a new card at that exact position. Fill in the title and optional details, then click Save.
3. **Move or reorder a card.** Drag a card from one list and drop it on another to update its status, or drop it above/below another card in the same list to set a manual order.
4. **Work with multiple cards.** Use the checkbox in the upper-right of a card, or Shift-click another card in the same list to select a range. Use the selected-card action rail or right-click a selected card to move, copy, label, assign, or archive the group. Dragging one selected card moves the selected group.
5. **Add a list.** Click "+ Add list" on the right side of the board, or use Insert > Add list from the menu.
6. **Filter cards.** Use the filter bar at the top to search by text, filter by assignee, label, or due date.
7. **Group cards.** Use the grouping dropdown to create swimlanes by assignee or label.
8. **Customize field labels.** Click "Field labels" on the kanban toolbar to rename card fields for this sheet only.

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
| Card Color | F (col 5) | Hex color used as the card fill with readable text |
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
| Revision | R (col 17) | Monotonic per-card optimistic concurrency revision |
| Idempotency | S (col 18) | Bounded replay receipts for recovery-safe guarded writes |
| Member IDs | T (col 19) | JSON array of stable xApps principal IDs assigned to the card |
| Watcher IDs | U (col 20) | JSON array of stable xApps principal IDs watching the card |
| Member Labels | V (col 21) | JSON object mapping member/watcher principal IDs to display labels |
| Attachments | W (col 22) | JSON array of validated file/link metadata; uploaded bytes remain behind workbook-scoped URLs |

### Card Attachments

The Attachments section in the card editor accepts multiple files through the workbook-scoped upload route and safe `http`/`https` links. Each card stores at most 20 entries with a stable id, kind, name, URL, timestamp, optional uploader, and file MIME type/size. File attachments use the server's sandboxed download response and do not navigate away from the workbook. Removing an entry removes it from the card; uploaded-byte reclamation is a separate storage-retention concern.

### Room Members, Watchers, and Inbox

When the workspace host is connected to a MeshAgent room, the card editor lists only stable principals authorized to view the active saved workbook. Members receive assignment and status/comment notifications; watchers receive later card activity. The toolbar inbox is always filtered to the current trusted principal, persists before direct delivery, retries offline delivery when a route returns, and keeps a durable read cursor across reloads. Legacy Assignee text remains compatible, while new membership writes use stable principal IDs.

### Field Labels

Each kanban sheet can override display labels for card fields without changing the stored API/card JSON keys. For example, a sales board can display "Sales person" for `assignee` and "Close Date" for `due`, while another board continues to display the defaults.

Click "Field labels" on the board toolbar, edit the labels, and Save. Empty labels reset to defaults. The setting is stored on the sheet as `kanbanFieldLabels`; the resolved defaults are exposed as `kanbanResolvedFieldLabels` through the settings API.

### Card Fields

Each kanban sheet can choose which standard card fields are visible and can define its own custom card fields. Use this for domain cards such as CRM opportunities with fields like `startDate`, `stopDate`, `amount`, `account`, or `probability`.

Click "Card fields" on the board toolbar, show or hide any standard field including Title and Status, add or delete custom field definitions, and Save. Standard fields remain stored in canonical row-backed columns for API compatibility, but hidden fields are not rendered in that sheet's card editor. Custom definitions are stored on the sheet as `kanbanCustomFields`, field visibility is stored as `kanbanCardFieldLayout`, and values are stored on each card in `customFields`. These settings are available through the card API, SDK, CLI, toolkit, and MCP.

---

### Lists (Columns)

Lists define the stages of your workflow. Default lists are "To Do," "Research," "Draft," "In Progress," "Review," and "Done," but you can fully customize them.

**Add a list:** Click "+ Add list" on the board or use Insert > Add list.

**Rename lists:** Use Surface > Rename lists to edit all list names as a comma-separated string. Cards in renamed lists are automatically updated.

**Delete a list:** Use Surface > Delete list and type the exact name. Cards in the deleted list remain but become orphaned until reassigned.

**Reorder lists:** Drag a list header and drop it at another position. Lists swap positions visually and in the data.

**Color a list:** Click the color picker in the list header to set a column color. The color appears as a left border on the header and a subtle background tint on the column.

**Collapse a list:** Click the collapse control in a list header to reduce the list to a narrow rail. Click the restore control on the rail to expand it again. Collapsed lists are saved with the board.

### Multi-card Actions

Each card has a visible checkbox in its upper-right corner. Select up to 20 cards at once. Shift-clicking a checkbox or card selects the inclusive range when both cards are in the same list. Press `Escape`, click empty board space, or use **Clear** on the action rail to leave selection mode.

The selected-card action menu supports:

- **Move to** -- move every selected card to a list
- **Copy to** -- copy every selected card into a list with new stable card IDs
- **Add label** -- add an existing or new label without removing other labels
- **Assign** -- assign the group to an existing/new person or make it unassigned
- **Archive** -- safely remove the selected cards from the active board

Right-clicking any selected card opens the same group actions. Dragging a selected card moves the entire selected group while preserving its order. Permanent deletion never appears for active cards; archive the cards first, then manage permanent deletion from **Archived items**.

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
- **Card Color** -- color swatch picker for the card fill
- **Cover Image** -- upload a file or paste a URL; shows a preview
- **Checklist** -- add items, check/uncheck, delete items; progress shown on the card as a fraction (e.g., "3/5")
- **Comments** -- switch to the Comments tab and use Add first comment for a new thread, or add review/progress notes to an existing thread
- **Archive** button (active cards only) -- removes the card from the board without deleting its data
- **Restore to board** and **Delete permanently** (archived cards only); permanent deletion requires an in-page confirmation

To manually prioritize a list without changing statuses, drag a card above or below another card in the same list. The rendered order updates immediately and is saved with the workbook.

### Archived Items

Open the board's **More** menu and choose **Archived items (N)**. This entry is always available, including when the archive is empty. The archived-items manager supports title/detail/label/assignee search and lets you:

- **View** the complete archived card in the normal card inspector
- **Restore** it to its prior list
- **Delete** it permanently after a styled confirmation that names the card
- Select multiple archived cards with the visible checkboxes, then **Restore selected**, **Delete selected**, or **Clear** the selection

Active cards do not expose hard Delete in the board UI. Archive is the non-destructive first step; permanent Delete appears only for archived cards. Bulk permanent deletion names the selected count, requires explicit confirmation, and keeps any cards that fail to delete selected for a safe retry. Archived state, restores, and deletions persist with the saved workbook.

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
- Archive card

When multiple cards are selected, right-clicking a selected card opens the selected-group actions instead.

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

Use global options before the command when targeting a saved workbook:
```
xapps --base-url <workspace-url> --file <WorkbookName> kanban <command>
```

For automated writes, use an explicit `--file`, `--json`, and `--agent` (or `--strict`). Strict mode requires stable card and request ids, provenance, and `--verify`; it always rejects shifting numeric row targets. Guarded update, move, archive, restore, batch, and delete commands also require the card's current `--expected-revision`; retries with the same request id and payload replay the durable receipt, while stale revisions or changed request intent return typed conflicts. `kanban add-card --id TASK-99 --request-id create-TASK-99-1 --created-by agent-id --verify --agent --json` creates the card and reads it back in one public CLI call. If no `--file` is supplied and the active workbook does not contain the board, legacy commands can still search saved workbooks for a Kanban sheet with that name and retry with the resolved file.

Kanban automation follows the public contract in dependency order: the HTTP API is the source capability, the typed SDK wraps that API, and CLI, MCP, and hosted-toolkit commands delegate through the SDK. Agent-facing tool schemas are normalized through the shared OpenAI strict-schema rules before publication.

Room collaboration uses the same dependency order. `kanban-collaboration-status`, `kanban-people`, `kanban-notifications --unread --limit 25`, and `mark-kanban-notification-read <notification-id>` operate on the saved workbook selected by global `--file`. Hosted agents use `kanban_collaboration_status`, `kanban_list_people`, `kanban_list_notifications`, and `kanban_mark_notification_read`. Repeating mark-read with the same stable notification ID is recovery-safe.

For an agent status change, use the atomic transition instead of a separate move, assignment, and comment write: first read `card-json` to obtain the card `revision`, then call `transition-card` with that revision, a durable request id, a typed comment, and `--verify`. The same request id and identical payload safely replays a lost response without duplicating the comment; an out-of-date revision returns a typed conflict instead of overwriting newer work. Hosted/MCP agents use `transition_kanban_card`; MeshAgent agents use `xapps-kanban.kanban_transition_card`. Use `update_card` / `kanban_update_card` for non-workflow field patches.

Agent dispatch follows the same guarded pattern. `request-agent` persists the stable request and Agent Work linkage before dispatch; `agent-request` returns its lifecycle `revision`; retry, cancel, and event commands require that revision plus a durable `--mutation-id`, so a lost response can be replayed without another run or event.

#### Batch Semantic Ops

```bash
printf '{"op":"kanban.addCard","card":{"id":"TASK-99","title":"Draft launch notes","status":"To Do"}}\n' | xapps kanban batch "Sprint Board" --stdin --expected-revision 12
# Output: Applied 1 semantic op
```

The strict batch contract accepts only `kanban.addCard` with a stable `card.id` and `kanban.updateCard` with a stable `cardId`. The server commits the cloned workbook only after every op succeeds; reuse the same ids and workbook revision when recovering an uncertain response.

#### List Cards

```bash
xapps kanban cards "Sprint Board"
# Output:
#   #0 [To Do] Set up CI pipeline
#   #1 [In Progress] Design landing page
#   #2 [Done] Fix login bug

xapps kanban cards "Sprint Board" --status "In Progress"
# Output:
#   #1 [In Progress] Design landing page

xapps kanban list-cards "Sprint Board" --status "In Progress"
# Alias for `cards`; useful when searching for a natural "list cards" command.

xapps kanban cards "Sprint Board" \
  --filter '{"priority":"P1","assignee":"Ada"}' \
  --q "launch" --sort=-due --limit 25 --offset 0 --json
# JSON output is a stable envelope with ok, sheet, count, totalCount, and cards.
```

#### Card JSON

```bash
xapps card-json "Sprint Board" TASK-42
xapps show-card "Sprint Board" TASK-42
# Output:
# {
#   "row": 3,
#   "id": "TASK-42",
#   "title": "Implement search",
#   "status": "To Do",
#   "comments": []
# }
```

`show-card` is an alias for `card-json`; use the stable card id (`TASK-42`) instead of a row number when an agent needs read-back or a later update.

#### Collaboration Email Recovery

```bash
xapps --file "Room Work.json" kanban-collaboration-status --json
xapps --file "Room Work.json" kanban-email-outbox --status retry_wait,unknown --json
xapps --file "Room Work.json" kanban-retry-email <delivery-id> --json
xapps --file "Room Work.json" kanban-recover-email-replies --json
```

These editor-only commands expose sanitized durable state. Use `--allow-ambiguous` only when retrying an `unknown` result and duplicate email is acceptable.

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
xapps kanban add-card "Sprint Board" "Implement search" --list "To Do" --desc "Full-text search for docs" --due 2026-04-15 --labels "feature,P1" --custom-fields '{"startDate":"2026-06-01"}' --id TASK-42 --request-id create-TASK-42-1 --verify --json
# Output includes file, sheet, created, card, requestId, replayed, and verified:true

# Minimal card (uses first list by default):
xapps kanban add-card "Sprint Board" "Quick fix" --request-id quick-fix-1 --verify --json
# Output includes the created card after read-back
```

#### Update a Card

```bash
xapps update-card "Sprint Board" TASK-42 '{"status":"Done","labels":"feature,P1,shipped"}' \
  --expected-revision 4 --request-id update-TASK-42-1 --verify --agent --json
# Output includes card, revision, requestId, replayed, and verified:true

# Cover, attachments, and checklist have discoverable flags as well as JSON-patch support:
xapps update-card "Sprint Board" TASK-42 --cover /uploads/card.png \
  --attachments '[{"id":"spec-1","kind":"link","name":"Release spec","url":"https://example.com/spec","uploadedAt":"2026-07-29T00:00:00.000Z"}]' \
  --checklist '[{"text":"QA signoff","done":false}]' \
  --expected-revision 5 --request-id update-TASK-42-2 --verify --agent --json

cat patch.json | xapps update-card "Sales Pipeline" OPP-42 @- \
  --expected-revision 2 --request-id update-OPP-42-1 --verify --agent --json
```

#### Archive, Restore, and Bulk Actions

```bash
xapps archive-card "Sprint Board" TASK-42 --expected-revision 6 \
  --request-id archive-TASK-42-1 --verify --agent --json
xapps archived-cards "Sprint Board" --json
xapps restore-card "Sprint Board" TASK-42 --expected-revision 7 \
  --request-id restore-TASK-42-1 --verify --agent --json

xapps bulk-cards "Sprint Board" assign '["TASK-42","TASK-43"]' \
  --expected-revisions '{"TASK-42":8,"TASK-43":3}' \
  --assignee codex-agent --request-id assign-wave-1 --json
```

`bulk-cards` supports `move`, `copy`, `label`, `assign`, `archive`, `restore`, and `delete`. It validates every stable id and expected revision before saving once; any validation or persistence failure leaves the whole batch unchanged. Permanent bulk deletion additionally requires `--yes`.

#### Atomic Agent Transition

```bash
# Read the current per-card revision before a guarded transition.
xapps card-json "Sprint Board" TASK-42 --json

xapps transition-card "Sprint Board" TASK-42 "In Progress" \
  --expected-revision 4 \
  --request-id task-42-start-20260710 \
  --message "Picked up implementation." \
  --author codex-agent \
  --type progress \
  --assignee codex-agent \
  --verify --agent --json
# Output includes card, comment, revision, requestId, replayed, and verified:true.
```

Retry the exact command with the same `--request-id` after a lost response; it returns `replayed:true` and does not append a second comment. If another writer updated the card first, refresh `card-json` and decide how to handle the returned revision conflict.

#### Durable Agent Request

```bash
xapps request-agent "Sprint Board" TASK-42 codex "Implement and verify this card." \
  --expected-revision 5 --request-id agent-TASK-42-1 --author orchestrator --json

xapps agent-request "Sprint Board" TASK-42 agent-TASK-42-1 --json
xapps add-agent-request-event "Sprint Board" TASK-42 agent-TASK-42-1 \
  --expected-revision 1 --mutation-id agent-TASK-42-running-1 \
  --status running --message "Implementation started." --json
```

#### Delete a Card

```bash
# Preview the exact stable-id target first.
xapps delete-card "Sprint Board" TASK-42 --dry-run --json

# Deletion requires both explicit confirmation and authoritative read-back.
xapps delete-card "Sprint Board" TASK-42 --yes --verify --expected-revision 9 \
  --request-id delete-TASK-42-1 --agent --json
# Output includes deleted:true, readback.deleted:true, and verified:true.
```

#### Card Comments

```bash
xapps card-comments "Sprint Board" TASK-42 --json
# Output:
#   #0 2026-05-03T10:15:00.000Z Alice: Ready for review.

xapps add-card-comment "Sprint Board" TASK-42 "Ready for review." --author Alice --type progress \
  --expected-revision 9 --request-id comment-TASK-42-1 --verify --json

# Images and same-workbook card/range embeds use the same guarded mutation.
xapps add-card-comment "Sprint Board" TASK-42 --author Alice --type evidence \
  --images-json '["/uploads/evidence.png"]' \
  --embeds-json '[{"version":1,"scope":"same-workbook","kind":"spreadsheet-range","sheetId":"sheet:grid","ref":{"rangeA1":"A1:B2"}}]' \
  --expected-revision 10 --request-id evidence-TASK-42-1 --json
```

#### List Management

**List all lists:**
```bash
xapps lists "Sprint Board" --json
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

Use `kanban-board` to read the board workflow revision. `set-kanban-board` updates compact/grouping appearance, while `update-list` sets color, collapsed state, and WIP limit. Supply `--expected-revision` plus `--request-id` for replay-safe writes.

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
xapps delete-list "Sprint Board" "Peer Review" --move-cards-to "Done"
# Output: List deleted: Peer Review
```

**Reorder lists:**
```bash
xapps reorder-lists "Sprint Board" '["Backlog","To Do","In Progress","Done"]'
# Output: Lists reordered on Sprint Board
```

`reorder-cards <board> <list> <ids-json>` replaces one list's manual order using stable card ids and requires both board and per-card revision guards.

---

### API Endpoints

```bash
# List all cards
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/cards

# Read guarded board/list workflow state
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/board

# Filter, search, sort, and page cards. `filter` is a URL-encoded JSON object.
curl -H 'X-XApps-File: MyWorkbook.json' "$XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/cards?filter=%7B%22priority%22%3A%22P1%22%7D&q=launch&sort=-due&limit=25&offset=0"

# Create a card
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Sprint%20Board/cards \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"title":"New task","status":"To Do","description":"Details here","labels":"bug","due":"2026-04-15","assignee":"Bob","customFields":{"startDate":"2026-06-01"},"id":"TASK-99","requestId":"create-TASK-99-1"}'

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

The recipes use an existing authorized `MyWorkbook.json` in `local` storage. Replace that file and storage target together for your actual workbook, and set `XAPPS_API_BASE_URL` to its authorized host. Commands that extract structured receipts also require `jq`.

```bash
xapps_scoped() {
  xapps --base-url "${XAPPS_API_BASE_URL:?Set the authorized host URL}" \
    --file 'MyWorkbook.json' --workbook-storage-target local "$@"
}
```

These examples use an existing `Sprint 7` Kanban sheet with `To Do`, `In Progress` and `Done` among its six default lists. Read the list result before seeding; if the board uses custom stages, select an existing intended stage. Do not add default lists again: duplicate names return `409`. Product boards may use custom stages; repository work follows the canonical `AGENTS.md` work-class and stage rules. Dispatch tooling owns run records.

#### Seed one task and read it back

```bash
xapps_scoped kanban lists "Sprint 7" --json
xapps_scoped kanban add-card "Sprint 7" "Update API docs" \
  --list "To Do" --labels docs,P2 --id DOCS-1 \
  --created-by sprint-agent --request-id seed-docs-1 --agent --verify --json
xapps_scoped kanban card-json "Sprint 7" DOCS-1 --json
```

#### Pick up an authorized task, then update its metadata

```bash
xapps_scoped kanban card-json "Sprint 7" DOCS-1 --json > docs-card-before.json
CARD_REVISION=$(jq -er '.card.revision' docs-card-before.json)
xapps_scoped kanban transition-card "Sprint 7" DOCS-1 "In Progress" \
  --assignee sprint-agent --expected-revision "$CARD_REVISION" \
  --request-id docs-pickup-1 --message "Implement the authorized API documentation update." \
  --author sprint-agent --type progress --agent --verify --json > docs-pickup-receipt.json

# Refresh before a distinct subsequent write; do not reuse the pre-transition revision.
xapps_scoped kanban card-json "Sprint 7" DOCS-1 --json > docs-card-current.json
CARD_REVISION=$(jq -er '.card.revision' docs-card-current.json)
xapps_scoped kanban update-card "Sprint 7" DOCS-1 '{"labels":"docs,P2,api"}' \
  --expected-revision "$CARD_REVISION" --request-id docs-labels-1 --agent --verify --json
```

A status report is a read: use `kanban cards "Sprint 7" --status "In Progress" --json` through the same scoped helper and draft the summary. Reporting does not authorize a simulated status change. Move a card to Done only after its actual acceptance and, for repository changes, required publication evidence exists; a priority label is not completion evidence. Use the same guarded transition shape with a current card revision and an `evidence` comment for that final intent.

Keep every prepared payload, revision, request ID and receipt until verification completes. After uncertain delivery, retry the identical mutation with its original guard; do not rerun the preparation steps with a fresh revision. On `409`, reread, reconcile and create a new ID only for a newly decided intent. Read commands can run independently; writes against shared state run sequentially or as one atomic batch.

### Troubleshooting

**1. Card not appearing on the board**
A card must have a non-empty stored title (column A). If a sheet hides Title in the card editor, new cards use "Untitled card" automatically. If the title cell is empty, the card is invisible. Also verify the card's status (column B) matches one of the board's list names exactly.

**2. CLI or toolkit says "Unknown board"**
Pass `--file <Workbook.json>` when you know the saved workbook. If you do not know the file, run `xapps find-workbook --sheet "Board" --type kanban --json`; `kanban add-card --verify --json` can also auto-resolve a saved workbook when no explicit file was supplied.

**3. Drag and drop not working**
Ensure you are dragging from the card body, not from the color picker or other interactive elements inside the card. Column drag requires starting from the column header area, not from cards within it.

**4. Cards appear in the wrong list**
The status value in column B must exactly match a list name (case-sensitive). Use `xapps kanban cards "Board"` to inspect card statuses and `xapps kanban lists "Board"` to see list names.

**5. Filter returns no results**
Filters are combined with AND logic. If you set both an assignee and a label filter, only cards matching both appear. Use the "Clear" button to reset all filters.

**6. Card aging shows unexpected values**
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
- **Bulk seeding:** Inspect existing lists with the scoped `kanban lists <board> --json` command before adding cards. New boards already have six default lists; adding a duplicate name returns `409`. For an authorized custom stage that is missing, read `kanban-board <board> --json` and pass its `.revision` to `add-list` as `--expected-revision`, together with a unique `--request-id`. Read the board back after a list write and refresh its workflow revision before another distinct write.
- **Default list:** Set `--list` explicitly when seeding cards. If omitted, the current first list is used; a newly added list is appended. To intentionally change the default, use guarded `reorder-lists` with the complete desired list order, a fresh board workflow revision and a unique request ID, then read `kanban-board` back to confirm the order.

---

### Reports, Saved Views, and Companion Sheets

Beyond the per-card commands, kanban ships three workflow primitives.

#### `kanban-report` — board snapshot for agent / standup loops

```bash
xapps kanban-report <board> [--detailed] [--json]
```

Prints a one-line summary by default. `--detailed` (or `--json`) returns list names, card ids, titles, statuses, last move timestamps, evidence counts, and hints for cards missing evidence or overdue. For a tracked engagement, use this report against the assigned board, then read the assigned card for its current revision and acceptance criteria. Follow canonical `AGENTS.md` work-class rules: Git-only, operational and small-fix work do not require tracking unless the user explicitly requests it.

#### Saved-view lifecycle

```bash
xapps kanban-views <board> [--json]
xapps save-kanban-view <board> <name> [--id <id>] [--search <text>] [--assignee <name>] [--priority <value>] [--label <label>] [--due overdue|this-week|this-month|no-date] [--group-by none|assignee|label|priority] [--column-dimension status|label|assignee] [--collapsed-columns-json <json>]
xapps update-kanban-view <board> <view-id> [--name <name>] [view flags]
xapps apply-kanban-view <board> <view-id>
xapps delete-kanban-view <board> <view-id> --yes
```

These commands list, create/replace, rename/update, apply, and delete complete saved views through the typed SDK. Applying a view restores its filter, grouping, column dimension, and collapsed columns. Add `--expected-revision <n> --request-id <id>` for durable guarded replay.

#### `sync-kanban-views` — fan kanban data into Calendar / Timeline / Dashboard

```bash
xapps sync-kanban-views <board> [--kind all|calendar|timeline|dashboard] [--json]
```

Materializes companion sheets from the kanban board:

- **Calendar** — every card with a `due` date as a calendar event.
- **Timeline** — every card as a same-day item using `due` (or today) with status-derived progress.
- **Dashboard** — a board-summary text widget and a cards-by-status table.

The sync is a one-way materialization. Re-running it refreshes sync-owned cells while preserving user-owned companion cells.

#### `kanban-automation` — opt-in board behaviors

```bash
xapps kanban-automation <board> <preset>... [--json]
xapps kanban-automation <board> --list [--json]
xapps kanban-automation <board> --replace-json '<rule-array>' [--json]
```

Applies one or more named automations to the board. Built-in presets:

| Preset | What it does |
|---|---|
| `done_label` | Adds the `done` label when a card moves to `Done` |
| `checklist_done` | Moves a card to `Done` when every checklist item is complete |
| `review_priority` | Sets priority to `High` when a card moves to `Review` |

Multiple presets compose and are deduplicated. Use `--replace-json '[]'` to clear all rules.
