## Timeline / Gantt Charts

### Plan a project you can keep current

Use Timeline when the important question is when work happens and what depends on what. Kanban is better for moving work through stages; Calendar is better for individual scheduled events. You can keep those views of a project in neighboring sheets.

1. Add a task with a recognizable title and planned start/end dates. Add a milestone for a decision or deadline that should appear as a point in time.
2. Break a large deliverable into work that can be assigned and updated. Set progress on the actual tasks; a colored bar alone does not establish that the work is complete.
3. Add dependencies only where one task truly relies on another. Check the predecessor IDs and direction so the relationship means what you intend.
4. Choose a zoom that shows the whole planning window, then group or filter to review one team or category. Clear filters before interpreting an apparently missing task.
5. Before applying auto-scheduling, review its proposed dates and affected tasks. Dependencies can move more than the selected bar. Keep immovable commitments visible while reviewing the result.
6. Revisit dates and progress during project reviews. Export or share a view only after checking that it includes the intended time window and filters.

### Read the schedule

The sidebar names the work; bars show its timing; milestones mark a date; connectors show dependency relationships. Dragging a task and changing a dependency are different edits. If a date moves unexpectedly, inspect both its direct dates and dependency chain before moving it back.

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
- **Subtask** -- A child of a parent task. Rendered indented in the sidebar (circle icon) and as a thinner bar on the chart. Every guarded mutation clamps subtask dates within the parent's date range. Deleting a parent task also deletes all its subtasks.
- **Milestone** -- A single-date event rendered as a diamond. Milestones have no end date or progress. The end date is automatically set equal to the start date. Tasks can be converted to milestones and back via the context menu or `set-task-milestone` command.

### Task Fields

Each task stores these fields:

| Field | Description |
|---|---|
| Title | Display name shown on the bar and sidebar |
| ID | Auto-generated collaboration-safe identifier (for example `T1-a1b2c3d4e5`) used for dependency references |
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

Auto-scheduling runs in the canonical server task domain after every guarded task mutation, including UI, API, SDK, CLI, MCP, and toolkit writes. Failed schedules roll back without a partial save.

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

### CLI Commands

Timeline registers CLI commands for task authoring, dependency management, milestone conversion, filtered task reads, and summary reports. Use `xapps list --json` as the authoritative machine-readable command inventory.

### API Endpoints

All reads and writes carry `X-XApps-File` plus `X-XApps-Workbook-Storage-Target` for the saved workbook. Read `GET /api/sheets/<sheet>/state` for canonical tasks, revision and fingerprint before authoring. The typed SDK and `timeline-batch` CLI below build the current scheduling request; their `TimelineMutationGuard` contains `expectedRevision`, stable `requestId`, and optional `expectedFingerprint`.

Use stable task IDs for updates/dependencies. Preview a removal or scheduling batch before applying the authorized intent, and use the exact same payload/ID to recover a lost response. Endpoint and body authority lives in `packages/xapps-surface-timeline/src/server-transactions.ts` and `src/public-api.ts`; a raw task-shaped JSON body without those guards is not a valid mutation recipe.

### Agent / AI Workflow Recipes

Choose the authorized saved workbook and its actual storage target before running the examples. Set `XAPPS_API_BASE_URL` to that host. This helper keeps every operation in the same scope (replace the example file and `local` together when needed):

```bash
xapps_scoped() {
  xapps --base-url "${XAPPS_API_BASE_URL:?Set the authorized host URL}" \
    --file 'MyWorkbook.json' --workbook-storage-target local "$@"
}
```

Timeline does not invoke a provider directly. Prepare a schedule from bounded source data using the typed `TimelineBatchOperation[]` contract, including actual task dates and dependency targets.

```bash
xapps_scoped timeline-state Roadmap --json
# Set TIMELINE_REVISION to the returned revision; inspect dependency IDs.
xapps_scoped timeline-batch Roadmap \
  '[{"op":"create","task":{"id":"phase-1","title":"Research","start":"2026-09-07","end":"2026-09-11"}}]' \
  --expected-revision "$TIMELINE_REVISION" --request-id roadmap-phase-1 --dry-run --json
# After reviewing that concrete preview, apply the same intended operation.
xapps_scoped timeline-batch Roadmap \
  '[{"op":"create","task":{"id":"phase-1","title":"Research","start":"2026-09-07","end":"2026-09-11"}}]' \
  --expected-revision "$TIMELINE_REVISION" --request-id roadmap-phase-1 --yes --verify --json
xapps_scoped timeline-state Roadmap --json
```

For an already authorized schedule change, preview/review is an implementation step and does not require another conversational approval. The canonical task domain validates parent/dependency relationships; do not copy row offsets from an old snapshot. Read the final dates, dependencies, revision and fingerprint before reporting the schedule complete. Keep the exact payload, expected revision and request ID after uncertain delivery; retry that same intent. On a revision conflict, reread and reconcile before creating a new intent and request ID.

### Troubleshooting

**Task bar does not appear on the chart**
Make sure both start and end dates are set and in YYYY-MM-DD format. Tasks without valid dates render only in the sidebar.

**Dependency arrow is missing**
Verify the dependency reference uses the correct task ID (e.g., T1, not the row number). Check that the referenced task exists and has valid dates. Both the source and target tasks must be visible in the current view.

**Auto-scheduling did not move dependent tasks**
Confirm that every dependency uses a live stable task ID and that the requested dates fit inside any parent range. UI, API, SDK, CLI, MCP, and toolkit task mutations all run the same scheduler; invalid or cyclic plans return a typed error and leave the saved plan unchanged.

**Subtask dates extend beyond the parent**
Use a guarded task mutation to repair legacy raw-cell data. All current task mutation interfaces clamp subtask dates to the parent range before committing.

**Weekend stripes are not showing**
Weekend highlighting only appears in **Day** zoom level. Switch to Day view using the toolbar or `View > Day view`.

**Sidebar is too narrow or too wide**
Drag the vertical resize handle between the sidebar and chart area to adjust. The minimum width is 220px.

**Filters return no tasks**
Search, status, and assignee filters combine with AND logic. Clear all filters using the Clear button to see all tasks, then apply one filter at a time.

Zoom, grouping, and task collapse are shared planning state. Search/status/assignee filters and sidebar width are per-tab viewport state: they survive reload in that tab but are not written to the workbook or shared with other users.

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

Timeline ships typed CLI commands covering task authoring, dependency management, view settings, and reporting. Shared mutations use revision/request guards.

```bash
xapps tasks <sheet> [--status <status>] [--assignee <name>] [--search <text>] [--type <task|subtask|milestone>] [--json]
xapps add-task <sheet> <title> [--start <YYYY-MM-DD>] [--end <YYYY-MM-DD>] [--progress <n>] [--type <task|subtask|milestone>] [--parent <id>] [--assignee <name>] [--status <s>] [--color <hex>] [--id <task-id>]
xapps update-task <sheet> <row-or-id> <json>                                                                # patch any subset of fields
xapps delete-task <sheet> <row-or-id>
xapps set-task-dependencies <sheet> <row-or-id> <task-id>...                                                # replace deps array
xapps clear-task-dependencies <sheet> <row-or-id>
xapps set-task-collapsed <sheet> <row-or-id> <true|false>
xapps set-task-milestone <sheet> <row-or-id> [--at <YYYY-MM-DD>]                                            # type=milestone, end=start, progress=100
xapps timeline-report <sheet> [--horizon-days <n>] [--status <status>] [--assignee <name>] [--type <task|subtask|milestone>] [--json]
xapps update-timeline-settings <sheet> '{"timelineZoom":"week","timelineGroupBy":"assignee"}'
xapps set-timeline-grouping <sheet> <none|assignee|status|color>
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

The report prints something like `5 items (4 tasks, 1 milestone); 1 complete; 0 overdue; 46% avg progress.` -- a standup-ready summary you can pipe into a Slack post or commit hook. `--json` returns the typed shape: `{ ok, sheet, asOf, horizonEnd, horizonDays, filters, itemCount, taskCount, milestoneCount, completedCount, overdueCount, overdueTasks[], upcomingMilestoneCount, upcomingMilestones[], averageProgress, summary }`; `done` and `completed` are equivalent report filters.

### MCP

The MCP surface mirrors these operations, including `timeline_set_task_collapsed`, `timeline_update_settings`, `timeline_set_zoom`, and `timeline_set_grouping`. It does not expose generic whole-sheet mutation.

### REST API

| Route                                                | Method  | Purpose                                       |
|------------------------------------------------------|---------|-----------------------------------------------|
| `/api/sheets/<timeline>/tasks`                       | GET     | List all tasks                                |
| `/api/sheets/<timeline>/tasks`                       | POST    | Create a task or milestone                    |
| `/api/sheets/<timeline>/tasks/<row-or-id>`           | GET     | Read one task                                 |
| `/api/sheets/<timeline>/tasks/<row-or-id>`           | PUT     | Patch a task (any subset of fields)           |
| `/api/sheets/<timeline>/tasks/<row-or-id>`           | DELETE  | Remove a task                                 |
| `/api/sheets/<timeline>/settings`                    | GET/PUT | Read/update guarded shared zoom and grouping  |
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
