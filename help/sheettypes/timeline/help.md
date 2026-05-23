## Timeline / Gantt Charts

### Overview

Timeline sheets are interactive Gantt-style views for roadmaps, schedules, project plans, and milestone tracking. Tasks appear as horizontal bars plotted over time, with support for progress tracking, dependency arrows, subtasks, assignees, status, filtering, grouping, and auto-scheduling.

> 🤖 Agent example: an agent can create a delivery plan from a spec, add task dependencies and owners, then keep progress and dates aligned while a human reviews the schedule visually.

![Timeline sheet showing a product roadmap with task phases, assignees, status badges, dependency arrows, and milestone diamonds in Week view](/help-assets/screenshots/timeline-sheet.png)

### Features

- Tasks, subtasks, and milestones rendered as color-coded bars
- Start/end date ranges with drag-to-resize
- Progress tracking (0-100%) with visual fill
- Dependency arrows with auto-scheduling
- Assignee and status fields per task
- Zoom levels: Day, Week, Month
- Filtering by search text, status, and assignee
- Grouping by assignee, status, or color (swimlanes)
- Inline rename from the sidebar
- Collapsible parent tasks with subtask counts
- Today line indicator with auto-scroll
- Weekend highlighting (in Day view)
- Overdue and critical-path flags
- Resizable sidebar panel
- Context menu with quick actions
- Drag task bars to move dates, drag handles to resize
- Right-click context menu for status, progress, duplicate, convert
- Home-page hover popover with live task summary

### Getting Started

1. Create a new timeline sheet from the **+ Add Sheet** menu.
2. Click **+ Add task** at the bottom of the sidebar or use `Insert > Add task`.
3. Fill in the task name, start date, end date, and optional fields.
4. Click **Save**. The task bar appears on the chart.
5. Drag the bar left or right to shift dates. Drag the left or right handle to change the duration.
6. Create dependencies by dragging from the dependency handle on one bar to another.

### Task Types

Timeline supports three task types:

- **Task** -- Standard work item rendered as a full horizontal bar (square icon in sidebar). Has start/end dates, progress, color, assignee, status, and all metadata fields.
- **Subtask** -- A child of a parent task. Rendered indented in the sidebar (circle icon) and as a thinner bar on the chart. Subtask dates are clamped within the parent's date range when saved through the editor. Deleting a parent task also deletes all its subtasks.
- **Milestone** -- A single-date event rendered as a diamond. Milestones have no end date or progress. The end date is automatically set equal to the start date. Tasks can be converted to milestones and back via the context menu or `set-task-milestone` command.

### Task Fields

Each task stores these fields:

| Field | Description |
|---|---|
| Title | Display name shown on the bar and sidebar |
| ID | Auto-generated identifier (T1, T2, ...) used for dependency references |
| Type | `task`, `subtask`, or `milestone` |
| Start Date | When the task begins (YYYY-MM-DD) |
| End Date | When the task ends (YYYY-MM-DD) |
| Progress | Completion percentage, 0-100 |
| Color | Hex color for the task bar |
| Assignee | Name of the person responsible |
| Status | One of: `not-started`, `in-progress`, `blocked`, `done`, `completed` |
| Parent | Row number of the parent task (for subtasks) |
| Dependencies | Comma-separated list of task IDs this task depends on |
| Collapsed | Whether a parent task's subtasks are hidden (toggled via the expand/collapse arrow) |

### Progress Tracking

Each task bar displays a filled portion reflecting its completion percentage. You can update progress through:

- The task editor dialog (slider from 0 to 100 in steps of 5)
- The right-click context menu (quick-set to 0%, 25%, 50%, 75%, 100%)
- CLI or API

Setting progress to 100% automatically changes status to `done`. Setting progress above 0 on a `not-started` task changes it to `in-progress`.

### Dependencies

Tasks can be linked with predecessor/successor relationships:

- **Drag-to-link** -- drag from the dependency handle (small circle) on one task bar to another bar to create a dependency arrow.
- **Editor** -- type comma-separated task IDs in the Dependencies field (e.g., `T1, T4, T8`).
- **CLI** -- use `set-task-dependencies <sheet> <id> <dep-id>...` to replace a task's dependencies, or `clear-task-dependencies <sheet> <id>` to remove all.

Dependency arrows render as SVG paths between the linked task bars. When a predecessor and successor have a tight handoff (0-1 day gap), the arrow path adjusts for readability.

### Auto-Scheduling

When a predecessor task moves or changes duration, dependent tasks automatically shift forward to maintain the relationship. This keeps your plan consistent without manual date adjustments.

Auto-scheduling runs after every task save through the editor or drag interaction.

### Zoom Levels

Switch between three zoom levels using the toolbar buttons (Day / Week / Month) or the `View` menu:

| Zoom | Column Width | Best For |
|---|---|---|
| Day | 56px per day | Detailed daily planning, weekend visibility |
| Week | 84px per week | Sprint-level planning (default) |
| Month | 140px per month | High-level roadmaps and quarterly views |

![Timeline in Month view showing the full roadmap with dependency arrows, milestones as diamonds, and month column headers](/help-assets/screenshots/timeline-zoom-month.png)

Tasks are sorted by start date (top-level tasks first; subtasks appear immediately after their parent). The chart auto-scrolls to keep the current date visible when first loaded.

### Filtering

The toolbar provides three filter controls:

- **Search** -- free-text filter matching task title, ID, or assignee
- **Status dropdown** -- filter to a single status (not-started, in-progress, blocked, done, completed)
- **Assignee dropdown** -- filter to a single assignee

Filters work together (AND logic). A **Clear** button appears when any filter is active. Parent tasks of matching subtasks are automatically included so the hierarchy remains visible.

### Grouping (Swimlanes)

Group tasks into labeled swimlane sections:

- **Group by assignee** -- one swimlane per assigned person, plus "Unassigned"
- **Group by status** -- one swimlane per status value
- **Group by color** -- one swimlane per task color

The group selector is in the toolbar next to the filters.

### Sidebar Interactions

- Click a task row to open the full editor dialog
- Click the pencil (rename) icon that appears on hover to inline-rename a task directly in the sidebar; press **Enter** to confirm or **Escape** to cancel
- Click the collapse/expand arrow on parent tasks to show or hide subtasks; the arrow and subtask count are shown only when subtasks exist
- Each row shows the task icon (square for task, circle for subtask, diamond for milestone), the ID badge (e.g. T1), the assignee name badge, the status badge, and any overdue/critical flags

![Timeline sidebar showing task rows with ID badges, assignee names, status badges, and critical/overdue flags](/help-assets/screenshots/timeline-sidebar.png)

The sidebar panel width is resizable by dragging the vertical resize handle between the sidebar and the chart area. The minimum width is 220px and the maximum leaves at least 220px for the chart.

### Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| Click bar | Open task editor |
| Drag bar horizontally | Move task dates |
| Drag left/right handle | Resize task duration |
| Drag dependency handle | Create dependency link |
| Right-click bar | Open context menu |

### Context Menu Actions

Right-clicking on a task bar provides:

- **Edit task** -- opens the full editor dialog
- **Set status** -- quick-switch to `not-started`, `in-progress`, `blocked`, or `done`; setting `done` also sets progress to 100%
- **Add subtask** -- creates a subtask inheriting the parent's dates and color
- **Duplicate task** -- copies the task with a new ID and appends "(copy)" to the title
- **Convert to milestone / Convert to task** -- toggles the task type; converting to milestone clears the end date and progress
- **Set progress** -- quick-set to 0%, 25%, 50%, 75%, or 100%; setting 100% changes status to `done`
- **Delete task** -- removes the task and all its subtasks

Right-clicking on empty chart space provides:

- **Add task** -- opens the editor for a new task
- **Add milestone** -- immediately creates a milestone for today's date

### Home Page Popover

When you hover over a timeline sheet on the workbook home page, a compact summary popover appears with:

- Total task and milestone count
- Number of completed items
- Number of overdue items
- Average progress percentage with a visual progress bar

This is the same data returned by the `timeline-report` API endpoint, fetched live when you hover.

### CLI Commands

Timeline registers CLI commands for task authoring, dependency management, milestone conversion, filtered task reads, and summary reports. Use `xapps list --json` as the authoritative machine-readable command inventory.

### API Endpoints

**List all tasks:**

```bash
curl -H 'X-XApps-File: MyWorkbook.json' "$XAPPS_API_BASE_URL/api/sheets/MyTimeline/tasks"
```

**Create a task:**

```bash
curl -X POST "$XAPPS_API_BASE_URL/api/sheets/MyTimeline/tasks" \
  -H "Content-Type: application/json" \
  -H 'X-XApps-File: MyWorkbook.json' \
  -d '{"title":"Design Review","start":"2025-04-01","end":"2025-04-03","progress":0,"color":"#34a853","assignee":"Carol","status":"not-started","type":"task","id":"T20"}'
```

**Update a task:**

```bash
curl -X PUT "$XAPPS_API_BASE_URL/api/sheets/MyTimeline/tasks/T20" \
  -H "Content-Type: application/json" \
  -H 'X-XApps-File: MyWorkbook.json' \
  -d '{"progress":50,"status":"in-progress"}'
```

**Delete a task:**

```bash
curl -X DELETE "$XAPPS_API_BASE_URL/api/sheets/MyTimeline/tasks/T20" \
  -H 'X-XApps-File: MyWorkbook.json'
```

### Agent / AI Workflow Recipes

**Recipe 1: Build a project plan from a list of deliverables**

Given a spreadsheet with deliverable names and estimated durations, an agent can read the spreadsheet data and create timeline tasks programmatically:

```bash
# 1. Read deliverables from spreadsheet
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Deliverables/cells

# 2. Create tasks with staggered dates and dependencies
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Roadmap/tasks \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"title":"Phase 1: Research","start":"2025-04-01","end":"2025-04-14","type":"task","id":"T1"}'

curl -X POST $XAPPS_API_BASE_URL/api/sheets/Roadmap/tasks \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"title":"Phase 2: Build","start":"2025-04-15","end":"2025-05-09","type":"task","id":"T2","deps":"T1"}'

# 3. Add subtasks under each phase
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Roadmap/tasks \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"title":"User interviews","start":"2025-04-01","end":"2025-04-07","type":"subtask","parent":"0","id":"T3"}'
```

**Recipe 2: Daily standup status updater**

An agent can read current task statuses and update progress based on external signals:

```bash
# List all tasks to find in-progress work
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Sprint/tasks

# Update progress on active tasks
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Sprint/tasks/T5 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"progress":80,"status":"in-progress"}'

# Mark completed tasks as done
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Sprint/tasks/T3 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"progress":100,"status":"done"}'
```

**Recipe 3: Generate a milestone summary for a dashboard**

Read timeline tasks to extract milestones and write summary data to a spreadsheet for dashboard consumption:

```bash
# Fetch all tasks
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Roadmap/tasks

# Filter milestones from the response and write to a spreadsheet
# for a dashboard widget to display
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Summary/cells/A1 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"value":"Milestone"}'
```

### Troubleshooting

**Task bar does not appear on the chart**
Make sure both start and end dates are set and in YYYY-MM-DD format. Tasks without valid dates render only in the sidebar.

**Dependency arrow is missing**
Verify the dependency reference uses the correct task ID (e.g., T1, not the row number). Check that the referenced task exists and has valid dates. Both the source and target tasks must be visible in the current view.

**Auto-scheduling did not move dependent tasks**
Auto-scheduling only triggers when saving through the editor or a drag interaction. Direct cell edits and CLI updates do not trigger auto-scheduling on the client side.

**Subtask dates extend beyond the parent**
Subtask dates are clamped to the parent's range when saved through the editor. If dates were set via API before the parent existed, re-save the subtask through the editor to clamp them.

**Weekend stripes are not showing**
Weekend highlighting only appears in **Day** zoom level. Switch to Day view using the toolbar or `View > Day view`.

**Sidebar is too narrow or too wide**
Drag the vertical resize handle between the sidebar and chart area to adjust. The minimum width is 220px.

**Filters return no tasks**
Search, status, and assignee filters combine with AND logic. Clear all filters using the Clear button to see all tasks, then apply one filter at a time.

### Tips & Tricks

- Use milestones for key dates (launches, deadlines, reviews) and tasks for work items with duration.
- Right-click a task bar for quick status changes and progress updates without opening the full editor.
- Group by assignee to create a team workload view showing who is doing what.
- Use the context menu's "Add subtask" to quickly break down a task -- the subtask inherits the parent's dates and color.
- Duplicate a task to create similar items quickly, then adjust dates and assignees.
- The today line auto-scrolls into view when the timeline renders, so you always see where you are.
- Combine Timeline with a Dashboard sheet to build a milestone summary widget that reads from timeline data.

### Works Well With

- Calendar for day-level scheduling
- Spreadsheet for budget or status rollups
- Dashboard for milestone summaries
- Kanban for sprint-level task management

---

### Command Line Interface

Timeline ships eight CLI commands covering task authoring, dependency management, milestone helpers, and a one-shot board summary. Every UI mutation is also a scriptable CLI / MCP call.

```bash
xapps tasks <sheet> [--status <status>] [--assignee <name>] [--search <text>] [--type <task|subtask|milestone>] [--json]
xapps add-task <sheet> <title> [--start <YYYY-MM-DD>] [--end <YYYY-MM-DD>] [--progress <n>] [--type <task|subtask|milestone>] [--parent <id>] [--assignee <name>] [--status <s>] [--color <hex>] [--id <task-id>]
xapps update-task <sheet> <row-or-id> <json>                                                                # patch any subset of fields
xapps delete-task <sheet> <row-or-id>
xapps set-task-dependencies <sheet> <row-or-id> <task-id>...                                                # replace deps array
xapps clear-task-dependencies <sheet> <row-or-id>
xapps set-task-milestone <sheet> <row-or-id> [--at <YYYY-MM-DD>]                                            # type=milestone, end=start, progress=100
xapps timeline-report <sheet> [--horizon-days <n>] [--status <status>] [--assignee <name>] [--type <task|subtask|milestone>] [--json]
```

Quick end-to-end example -- author a five-task roadmap, wire dependencies, get the report:

```bash
xapps create-sheet "Roadmap" --type timeline
xapps add-task Roadmap "Design phase"  --start 2026-05-01 --end 2026-05-14 --progress 100 --status completed   --id phase-design
xapps add-task Roadmap "Build server"  --start 2026-05-08 --end 2026-05-21 --progress 80  --status in-progress --id task-server
xapps add-task Roadmap "Build CLI+MCP" --start 2026-05-15 --end 2026-05-28 --progress 50  --status in-progress --id task-cli
xapps add-task Roadmap "Tests + docs"  --start 2026-05-22 --end 2026-06-04 --progress 0   --status not-started --id task-tests
xapps add-task Roadmap "v0.2 release"  --start 2026-06-05 --end 2026-06-05 --type milestone --color "#7c3aed"  --id v02-launch
xapps set-task-dependencies Roadmap task-server  phase-design
xapps set-task-dependencies Roadmap task-cli     phase-design task-server
xapps set-task-dependencies Roadmap task-tests   task-cli
xapps set-task-dependencies Roadmap v02-launch   task-tests
xapps timeline-report Roadmap
```

The report prints something like `5 items (4 tasks, 1 milestone); 1 complete; 0 overdue; 46% avg progress.` -- a standup-ready summary you can pipe into a Slack post or commit hook. `--json` returns the structured shape: `{ ok, taskCount, milestoneCount, overdueCount, completedCount, averageProgress, overdueTasks[], upcomingMilestones[], filters, horizonDays, summary }`.

### MCP

The MCP surface mirrors the CLI 1:1: `timeline_tasks`, `timeline_add_task`, `timeline_update_task`, `timeline_delete_task`, `timeline_set_task_dependencies`, `timeline_clear_task_dependencies`, `timeline_set_task_milestone`, `timeline_report`. Useful for agents that need to translate a planning conversation into a Gantt chart, or read out current state in a periodic standup loop.

### REST API

| Route                                                | Method  | Purpose                                       |
|------------------------------------------------------|---------|-----------------------------------------------|
| `/api/sheets/<timeline>/tasks`                       | GET     | List all tasks                                |
| `/api/sheets/<timeline>/tasks`                       | POST    | Create a task or milestone                    |
| `/api/sheets/<timeline>/tasks/<row-or-id>`           | GET     | Read one task                                 |
| `/api/sheets/<timeline>/tasks/<row-or-id>`           | PUT     | Patch a task (any subset of fields)           |
| `/api/sheets/<timeline>/tasks/<row-or-id>`           | DELETE  | Remove a task                                 |
| `/api/sheets/<timeline>/timeline-report`             | GET     | One-shot summary                              |

Tasks accept either a 1-based row index or a stable id (column J) for `<row-or-id>`. The persisted dependencies field is a CSV in column H, but the API normalizes `string[]` / CSV input on PUT and POST.

### Task field reference

| Field          | Type     | Notes                                                                 |
|----------------|----------|-----------------------------------------------------------------------|
| `id`           | string   | Stable id; minted with `T` prefix on POST when omitted               |
| `title`        | string   | Required on POST                                                      |
| `start`, `end` | string   | `YYYY-MM-DD`. For milestones, `end` should equal `start`              |
| `progress`     | 0-100    | Integer; clamped to range                                             |
| `type`         | string   | `task` (default), `subtask`, or `milestone`                           |
| `parent`       | string   | Parent task id for subtasks                                           |
| `dependencies` | string[] | Each entry is another task's id; persisted as a CSV string in col H  |
| `assignee`     | string   | Free-text owner                                                       |
| `status`       | string   | `not-started` / `in-progress` / `blocked` / `done` / `completed`     |
| `color`        | string   | Hex (e.g. `#7c3aed`) -- overrides the default bar color               |
