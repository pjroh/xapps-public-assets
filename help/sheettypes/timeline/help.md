## Timeline / Gantt Charts

### Overview

Timeline sheets are interactive Gantt-style views for roadmaps, schedules, project plans, and milestone tracking. Tasks appear as horizontal bars plotted over time, with support for progress tracking, dependency arrows, subtasks, assignees, status, filtering, grouping, and auto-scheduling.

> 🤖 Agent example: an agent can create a delivery plan from a spec, add task dependencies and owners, then keep progress and dates aligned while a human reviews the schedule visually.

![Timeline sheet showing delivery phases, assignees, dependencies, and progress bars over time](/help-assets/screenshots/timeline-sheet.png)

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
- Today line indicator
- Weekend highlighting (in Day view)
- Overdue and critical-path flags
- Context menu with quick actions
- Drag task bars to move dates, drag handles to resize
- Right-click context menu for status, progress, duplicate, convert

### Getting Started

1. Create a new timeline sheet from the **+ Add Sheet** menu.
2. Click **+ Add task** at the bottom of the sidebar or use `Insert > Add task`.
3. Fill in the task name, start date, end date, and optional fields.
4. Click **Save**. The task bar appears on the chart.
5. Drag the bar left or right to shift dates. Drag the left or right handle to change the duration.
6. Create dependencies by dragging from the dependency handle on one bar to another.

### Task Types

Timeline supports three task types:

- **Task** -- Standard work item rendered as a full horizontal bar. Has start/end dates, progress, and all metadata fields.
- **Subtask** -- A child of a parent task. Rendered indented in the sidebar and as a thinner bar. Subtask dates are clamped within the parent's date range.
- **Milestone** -- A single-date event rendered as a diamond. Milestones have no end date or progress. The end date is automatically set equal to the start date.

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
- **CLI** -- use the `--depends` flag when creating or updating tasks.

Dependency arrows render as SVG paths between the linked task bars. When a predecessor and successor have a tight handoff (0-1 day gap), the arrow path adjusts for readability.

### Auto-Scheduling

When a predecessor task moves or changes duration, dependent tasks automatically shift forward to maintain the relationship. This keeps your plan consistent without manual date adjustments.

Auto-scheduling runs after every task save through the editor or drag interaction.

### Zoom Levels

Switch between three zoom levels using the toolbar buttons or the `View` menu:

| Zoom | Column Width | Best For |
|---|---|---|
| Day | 56px per day | Detailed daily planning, weekend visibility |
| Week | 84px per week | Sprint-level planning (default) |
| Month | 140px per month | High-level roadmaps and quarterly views |

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
- Click the pencil icon to inline-rename a task directly in the sidebar
- Click the collapse/expand toggle on parent tasks to show or hide subtasks
- Each row shows the task icon (square for task, circle for subtask, diamond for milestone), ID badge, assignee badge, status badge, and overdue/critical flags

The sidebar panel width is resizable by dragging the vertical resize handle between the sidebar and the chart area.

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

- Edit task
- Set status (not-started, in-progress, blocked, done, completed)
- Add subtask (inherits parent dates and color)
- Duplicate task
- Convert to milestone / Convert to task
- Set progress (0%, 25%, 50%, 75%, 100%)
- Delete task

Right-clicking on empty space provides:

- Add task
- Add milestone

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
