## Agent Work

An Agent Work sheet is a **room dataset console** for reviewing objectives, Kanban cards, agent runs, issues, activity, and evidence across saved workbooks you can access. The browser includes management controls such as owner assignment and issue handling. The published agent-facing surface is read-only; use the underlying Kanban operations to change cards.

### Review a project from status to evidence

1. Open **Overview** to identify running agents and unresolved issues. Check the selected room and any active workbook filter before interpreting counts.
2. In **Objectives**, select the workbook you want to review. This scopes the work-item and activity views; it does not switch the contents of a different saved workbook.
3. Open **Work Items** and use **Open only**, **Has agent run**, or **Missing evidence** to narrow the list. Search by the card title or stable ID when you already know the task.
4. Inspect the relevant item and its **Agents** and **Activity** records. Queued or running work is still in progress. A stale heartbeat or expired lease needs investigation even if an older message says the agent started.
5. Open **Evidence** to inspect attachments and completion summaries. Verify that the evidence belongs to the selected item and supports the claimed outcome; a screenshot alone is not proof that a background operation finished.
6. Clear the objective filter when you want to return to room-wide work. Use **Show archived** to find completed objectives removed from the default view.

### Understand an empty or surprising view

| What you see | What to check |
|---|---|
| No objectives | Room connection and dataset readiness, then whether the saved workbook contains indexed Kanban work |
| Fewer cards than expected | Objective scope, search text, owner filters, archive visibility, and the active quick filter |
| A completed card but no run | A human or direct API edit can complete a card without dispatching an agent run |
| A running agent with no recent activity | Heartbeat, lease, and run status; opening this sheet does not restart the agent |
| Missing preview | Whether an attachment was recorded and whether your account can read its bytes |

Use **Datasets** for readiness and row counts before concluding that an empty list means there is no work. Do not create duplicate objectives to repair a filter or connection problem.

![Agent Work navigation and the Room dataset not configured message on a host without a room connection](/help-assets/screenshots/agent-work-availability.png)

This example shows a connection prerequisite, not an empty connected room. Once the host has the required room dataset service, use the same navigation to inspect your authorized work.

Agent Work does **not** store the work itself. It reads and rolls up the central MeshAgent room dataset namespace `xapps/agent-work`; the sheet only stores UI preferences such as active view, search text, owner filter, workbook scope, and archive visibility.

### When to use Agent Work

- You have multiple saved workbooks and want one place to see open work.
- Kanban cards are being handled by people and room agents.
- You need evidence, issues, and completion summaries attached to work items.
- You want a queryable audit trail of card changes, comments, agent events, and evidence links.
- You need to confirm dataset health before trusting agent status reports.

### What it is not

- It is not a replacement for Kanban boards. Kanban remains the place where work items are authored and moved.
- It is not a private agent memory viewer. It shows the room-scoped xApps agent-work dataset that the current user can access.
- It is not a lock manager. Agent claims use `agent_runs` lifecycle, heartbeat, and lease fields; workbook edits still resolve through the workbook save/collab path.

The browser UI has eight views:

- **Overview** — objectives, owners, open issues, running agents, and recent activity at a glance.
- **Objectives** — one card per saved workbook that contains Kanban work, with owner, progress, and open-issue counts.
- **Work Items** — the individual Kanban cards (status, assignee, evidence, last update), filterable and searchable.
- **Issues** — typed problems raised against work items; raise and resolve them here.
- **Activity** — the event stream across card changes, comments, agent events, and evidence links.
- **Agents** — agent run lifecycles (queued / running / completed) with heartbeat and lease state.
- **Evidence** — screenshot/attachment metadata with large image previews.
- **Datasets** — table readiness and row counts; **New query** opens the raw dataset console.

The agent-facing surface is **read-only**. It reads the room-wide workspace Agent Work API under `/api/agent-work/...`, which exposes six read endpoints: `status`, `objectives`, `work-items`, `activity-events`, `agent-runs`, and `attachments`. Owner, issue, archive, and directive **state** is not a separate endpoint — it is derived onto the `objectives` rollup (owner, `open_issues`, `archived`) and into `activity-events` (`owner_assigned` / `issue_raised` / `issue_resolved` / `objective_archived` rows). A focused workbook is passed through the indexed `workbookFile` query/body field; the API itself remains at the app root so one Agent Work sheet can report across every visible workbook.

Agents drive these reads through matching tools on every channel — CLI `agent-work-status` / `agent-work-list-<table>`, MCP `agent_work_status` / `agent_work_list_<table>`, and the `agent_work_*` toolkit — each accepting the same server-side filters (status, assignee, label, event type, actor, date range, text, limit, offset). To **change** work (create cards, move to Done, raise/resolve issues, assign owners, archive), operate on the underlying Kanban workbooks; those mutations roll up into Agent Work automatically. There is no direct agent-work write API.

### First pass workflow

1. Save workbooks as server files so they can be indexed.
2. Create or update Kanban cards in those workbooks.
3. Open Agent Work and confirm the corresponding objectives and work items appear.
4. Assign an owner where accountability matters.
5. Use Issues and Evidence to review blocked or completed work.
6. Archive objectives when the work is done but should remain queryable.

### How objectives and work items get tracked

The model is simple: **one workbook = one objective, and each Kanban card in that workbook = one work item.** You do not create objectives by hand — they roll up automatically from the workbooks you already have.

Indexing happens at the **workbook save**, which every edit path flows through — the Kanban UI (which writes card cells over collab), the HTTP/CLI/MCP card APIs, and the collab sync. So a card created or changed **any** way is captured the moment it is saved; you never have to reconcile or re-import. This is host-level: the data lives in the room dataset, **not** in the Agent Work sheet, so a Kanban board is tracked **whether or not any Agent Work sheet exists** anywhere. Deleting a card removes its work item on the next save.

### Search and filter

A single **search box** (top right) filters the **active view** by text — objectives by name/file on Overview and Objectives, cards by id/title/workbook on Work Items, and so on. It updates as you type.

- **Owner** (Overview, Objectives) — a dropdown to show only objectives owned by selected people, by agents, or unassigned. Each option shows its count; multiple owners can be selected.
- **Work item quick filters** — *All cards*, *Open only* (non-terminal status), *Has agent run*, *Missing evidence*. Each pill shows **how many cards match**, so the filter state is self-evident (e.g. if every card is open and none have evidence, three filters legitimately show the same count). These run server-side against the full set, not just the visible page.
- **Activity filters** — quick filters (comments, evidence, failures, last 24h) plus agent, event type, owner, and date-range controls.
- **Objective scope** — click an objective (or use the title selector) to scope Work Items / Issues / Activity to that one workbook; clear it to go room-wide again.
- **Show archived** — toggle to include archived objectives.

### Objectives, owners, issues, and directives

- **Assign an owner** to an objective (Objectives view) to record who is accountable — a human or an agent.
- **Raise an issue** (Issues view) against a work item with a severity; resolve it when fixed. Issues reconcile from `issue_raised` / `issue_resolved` events, and open counts surface on the objective cards.
- **Send a directive** to queue an `agent_runs` request plus a directive event for a work item — instructing an agent what to do next.

### Realtime updates

The console updates live with **no polling**. The browser joins the room and refetches the active view when the host broadcasts an `agent-work-changed` event after a write. Writes also apply to the host's in-memory store immediately, so a new card or status change typically appears within a second or two of being saved — on localhost and when deployed.

### Archiving objectives

Use **Archive** on an objective to remove it from the default views once its work is finished (it stays queryable behind *Show archived*). Archiving is the intended way to retire an objective — note that simply deleting the workbook or its last card can leave the objective visible if it still has activity history.

### Completion summaries

When a Kanban work card transitions into a terminal status such as `Done`, the recorder emits a `work_item_completed` row in `activity_events`. Backfill/repair emits the same row for historical terminal cards reconstructed from saved workbook JSON. Its `data_json.summary` payload carries the structured completion summary: card id, title, status, workbook file, sheet name, labels, evidence comment count, latest evidence comment, and the companion Wiki section name `Outcome / Completion Summary`.

When a durable narrative is needed, Wiki is the human-readable place to write the outcome, verification, evidence links, risks, and follow-ups. A Wiki is not required merely because an Agent Work rollup exists. Repository tracking is selected by the `AGENTS.md` work-class table. Dispatch tooling owns run identity, lifecycle, heartbeat and lease records; agents use the supported repair path only for a missing or recoverable record and never write dataset rows by hand. The dataset event is the queryable source used by Agent Work Center, CLI, SDK, MCP, and hosted toolkit reads.

### Evidence previews

Overview and Evidence view thumbnails open a large evidence preview. Image bytes still live in `/uploads/...` or the room image dataset; Agent Work rows store only metadata and references.

### Multi-agent concurrency

Multiple agents on different computers can use the same central Agent Work dataset when they connect to the same MeshAgent room and `xapps/agent-work` namespace. `work_items` and `agent_runs` are merged by stable ids and represent latest materialized state; `activity_events` are idempotent event rows. The dataset is not a distributed lock by itself, so active work claims must use `agent_runs` lifecycle, heartbeat, and lease fields, and conflicting workbook/card edits still resolve through the workbook save/collab path.
