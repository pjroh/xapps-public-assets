# 📚 xApps Help Center

## Workbook and Service Basics

xApps brings your project's data, tasks, writing, designs, and files into a workbook with different kinds of sheets. Start with the job you need to do, add the sheets that support it, and return to the same saved workbook as the project grows.

Workbook content and connected services have different homes. Spreadsheet cells, boards, documents, and sheet configuration save with the workbook. **Chat conversations and Agent Work records belong to the connected room.** Live meetings and Terminal processes depend on their services; saving a workbook does not save a running call or shell process.

### Find your next step

| I want to… | Open this guide | What you will learn |
|---|---|---|
| Start a project | Your First Workbook | Create, choose storage, add sheets, and reopen |
| Choose between similar sheets | Choose the Right Sheet | Spreadsheet or Records; Wiki or Typewriter; Canvas or Whiteboard |
| Track delivery | Kanban Boards | Cards, owners, stages, checklists, and evidence |
| Schedule with other people | Calendar | Events and Find a time availability requests |
| Analyze a dataset | Records / Spreadsheets | Typed records, views, relations, formulas, and charts |
| Find missing work | Find and Recover Your Work | Storage location, search, Trash, and Version History |
| Collaborate in a room | Work Together | Workbook access, human Chat, Assistant, and Agent Work |

Use the Help search field for a feature or task. Choose a result in the left column, then use **On this page** to jump within a long guide. Screenshots illustrate the controls discussed immediately beside them; sample workbook names and data are examples.

### One roof, one file

Most tools each own one slice of the work and make you stitch the slices together by hand — export here, re-import there, copy a number from the spreadsheet into the slide, keep five tabs in sync. xApps collapses that. A single workbook can hold:

- **Numbers and data** — Spreadsheet, Records, Dashboard
- **Work and timing** — Kanban, Calendar, Timeline, Poll
- **Writing and knowledge** — Wiki, Typewriter
- **Visual and spatial work** — Design Canvas, Whiteboard, Gallery, Presentation, Floor Plan, Map
- **Files and operations** — Repository, File Viewer, Meeting, Terminal, Agent Work

Workbook-backed sheets save together. Supported formulas and references connect their data; connected room services keep their own durable records. You can start with one tab and add other sheets when the project needs them.

### Agent-friendly by design — a first-class priority, not bolted on

xApps treats AI agents as first-class operators. **Published durable operations are available through the supported CLI, REST API, MCP, MeshAgent toolkit and workbook automation contracts against the same saved workbook.** Browser-session gestures, provider availability and explicit manifest opt-outs have narrower boundaries. The file is the contract: humans use the interface, agents use the programmatic surfaces, and both read and write the same state.

- **Discoverable** — `xapps search <terms>`, `xapps help <group>`, and `xapps list --json` expose the full, machine-readable command catalog for every sheet type.
- **Verifiable** — use the command’s advertised guards and `--verify` where supported; `--json` gives structured output but does not by itself prove persistence.
- **Uniform** — supported durable operations share semantic contracts across their published channels; session-only controls remain in the browser.
- **Composable** — triggers, processes, and agent actions let machine workflows run inside the workbook, right next to the people.

For agent discovery, search the relevant surface, inspect its current command schema, then open its help page below. Package `surface.manifest.json` capability flags and named opt-outs define availability; `tools/surface-area/README.md` explains coverage accounting. Supply the saved workbook file and effective storage target before reading or writing. This Help Center remains product reference material; repository process lives in `AGENTS.md`.

That is why an agent can scaffold an entire multi-surface workspace — spreadsheet, doc, kanban, dashboard, repository — in a single pass, then hand a finished, structured project to a human for judgment and polish.

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
| Meeting / Terminal / Agent Work | Calls, command sessions, agent runs, evidence |

### What to do in your first few minutes

1. Create or open a workbook.
2. Add two or three different sheet types, not just a spreadsheet.
3. Save the workbook as a real file so it can be reopened, shared, clipped into, and protected with Workbook Access.
4. Choose **Room**, **Private**, or **Shared** access intentionally. Private and Shared workbooks live only in **MeshAgent room storage** and require a stable authenticated principal; Mac/PC storage supports Room-visible workbooks.
5. Use `Ctrl/Cmd + K` to open the command palette and explore actions quickly.
6. Treat the workbook like a living project hub instead of a single-purpose document.

### Human + agent model

- Humans are best for judgment, review, and visual editing.
- Agents are best for scaffolding, bulk edits, imports, analysis, and repeatable setup.
- The workbook is the shared contract: people use the interface; agents use the CLI, API, MCP, triggers, processes, and agent actions.

### Native mobile gateway and Deployment Center

The native xApps client uses the authenticated, versioned `/api/mobile/v1` gateway for room-scoped work. It reuses the selected MeshAgent project and room, installation identity, and the room service already connected to xApps; it does not ask the phone to hold room credentials or create a second room connection.

Deployment Center reads fresh authority before showing service status, bounded operational logs, approved artifact metadata, or deployment actions. Preview is a separate step from deploy, restart, or rollback, and every mutation carries the visible deployment and authority revisions plus one stable request id. Retrying the exact request converges on the same durable receipt; changing a previously used request is rejected. References returned to the app are identifiers that require fresh authorization, never signed URLs, provider responses, credentials, or full log streams.

The served operations are:

- `GET /api/mobile/v1/deployments/authority` — fresh project, room, and service capability authority.
- `GET /api/mobile/v1/deployments` — authorized deployment inventory.
- `GET /api/mobile/v1/deployments/{deploymentId}` — one focused deployment projection.
- `POST /api/mobile/v1/deployments/{deploymentId}/intents/{requestId}` — an idempotent preview or authorized lifecycle intent whose URL, header, and body request ids must match.

Deployment changes publish a content-free `deployment_center` realtime invalidation. The app then refreshes only Deployment Center instead of reloading the workbook, Chat, files, or room bootstrap.

### Where to go next

- Read **Welcome to xApps** for the practical quick start.
- Jump to a sheet type on the left if you already know what you want to build.
- Use the search box to find commands, features, or specific workflows fast.

## Your First Workbook

### Create something you can return to

1. Open **Home / Library** with the xApps logo. Choose **New Workbook**.
2. Give the workbook a recognizable project name. Choose a blank workbook or a starter template, then the sheets you actually need.
3. Check the storage destination. **Mac/PC** belongs to the connected host or available computer; **MeshAgent room storage** belongs to the selected room. Identical filenames in different destinations are different workbooks.
4. Choose the access mode. **Room** is visible to the room. **Private** and **Shared** require MeshAgent room storage and an authenticated account. Shared access needs the intended members.
5. Create the workbook. Add or switch sheets through the sheet navigator and **+** control. Give sheets useful names such as Budget, Delivery, and Brief.
6. Make a small change, allow the save to finish, return to Library, and reopen the same file from the same destination. Confirm your change is there before inviting others or beginning a large import.

### A useful first project: a launch plan

Start with three sheets. In **Wiki**, write the brief and success criteria. In **Kanban**, add a card for each deliverable with an owner, due date, and checklist. In **Spreadsheet**, track the budget and calculate totals. Add **Calendar** or **Timeline** when dates become important; add **Gallery**, **Repository**, or **Presentation** when you have assets or a review to share.

The sheets are separate views of related work. A Kanban card does not automatically become a Calendar event, and a table does not automatically become a dashboard. Use each sheet's documented data binding, reference, or automation controls when you want a connection.

### Return to the introduction

Use **Help → Welcome tour** to reopen the guided start. You can skip it at any time. Completing or skipping it is remembered by this browser; opening a direct link to an existing workbook does not require stepping through it.

## Choose the Right Sheet

| Your starting material | Choose | Choose the alternative when… |
|---|---|---|
| Numbers and calculations | Spreadsheet | Use Records for typed fields, linked records, forms, and saved views |
| A structured collection | Records | Use Spreadsheet for cell-by-cell formulas and freeform grids |
| Tasks moving through stages | Kanban | Use Timeline for overlapping dates and milestones |
| Events and finding a time | Calendar | Use Meeting for the actual call, lobby, notes, and attendance |
| A knowledge base with pages | Wiki | Use Typewriter for a polished document with page layout |
| A poster or fixed layout | Design Canvas | Use Whiteboard for an open workspace of ideas and connections |
| A story told slide by slide | Presentation | Use Dashboard for widgets tied to changing data |
| Images to browse and review | Gallery | Use Repository for managed source files and metadata |
| A document to inspect | File Viewer | Use Typewriter to author text; preview does not imply source-file editing |
| Geographic data | Map | Use Floor Plan for walls, rooms, and furniture |
| A conversation with people | Chat | Use Assistant for an AI request; use Agent Work to inspect dispatched work |
| A command session | Terminal | Its process runs on the host or selected connector, not inside the workbook file |

Other choices include **Poll** for voting and **Games** for the built-in arcade. The Add Sheet menu is the current catalog. A sheet may require a configured service even when it is available to add.

## Find and Recover Your Work

### A workbook is missing from Library

Check the selected storage destination, room, folder, and search text first. Clear a filter before assuming a file was removed. A workbook in room storage will not appear under an unrelated Mac/PC destination. Private or Shared files are visible only with the required account and access.

### A sheet or an edit is missing

Confirm the workbook name and storage target, then use the sheet navigator and search. Check whether the sheet is grouped or hidden. If the wrong content is visible, wait for loading or saving to settle before retrying a change. Record any displayed error; repeatedly importing or pasting can create duplicate work.

Open **Version History** to inspect saved snapshots. Preview the relevant version and use **Restore this sheet** only after confirming the target sheet and content. A sheet restore affects the focused sheet; it does not restore live Terminal processes or room Chat history. For a deleted workbook, check **Trash** in Library and restore the intended file instead of creating a replacement with the same name.

### A feature is unavailable

| Symptom | Check first |
|---|---|
| Calendar cannot connect to Google | Whether the host has Google configured and your account is connected |
| Meeting cannot join | Room connection, media service availability, and browser microphone/camera permissions |
| Terminal has no connector | Connector online state, selected stable identity, target command, and storage capability |
| Assistant cannot complete a request | Provider/agent availability and the request's visible error or approval state |
| Chat cannot load | Selected room, authenticated account, and the connection/request error |
| Agent Work is empty | Room/dataset readiness, workbook scope, filters, and whether work has been indexed |

Use **Diagnostics** when the problem persists. Include the action, workbook and storage destination, visible error, and approximate time when asking for support. Keep credentials and private conversation content out of shared reports.

## Work Together

### Choose the right conversation

**Chat / xChat** is for human collaboration: channels, direct messages, threads, files, reactions, and search in the connected room. **Assistant** is the AI panel for requesting help with the workbook. **Agent Work** shows tracked objectives, work items, runs, issues, and evidence. An online terminal connector is a separate capability; its presence does not prove a Chat participant or AI provider is ready.

### Share a workbook deliberately

Choose **Workbook Access**, confirm the file and destination, and select the appropriate Room, Private, or Shared access. Send colleagues a link to the saved workbook they can access. A copied link does not grant membership or change permissions. Room Chat has its own conversation scope; copying the workbook does not copy the room's messages.

### Review an agent's result

Give the agent a concrete outcome and identify the saved workbook and storage target. Inspect the resulting sheets, review evidence and any reported failures, and distinguish completed work from queued or running work. For bulk changes, verify a small representative result before expanding the request. Use the surface's current CLI/API reference when automating; examples are not permission to change unrelated data.

## 👋 Welcome to xApps

xApps is a **multi-surface workbook**. Instead of opening a spreadsheet app, a whiteboard app, a slide app, a floor-plan tool, and a notes app separately, you keep them together in one workbook and let them reference each other.

> 🤖 Agent example: an agent can create a workbook with a spreadsheet, doc, kanban board, dashboard, and repository sheet in one pass, then hand the structured workspace to a human for review and editing.

### 🚀 Quick start

1. Use the **`+`** button or the **`Sheet`** menu to insert a new sheet.
2. Save your work as a real workbook file with **`File -> Save Workbook`** or **`Save Workbook As...`**.
3. Use **Workbook Access** to keep the file room-visible, owner-only private, or limited to selected members.
4. Use the **top search bar** to search across sheets.
5. Use **`Ctrl/Cmd + K`** to open the command palette.
6. Use **sheet groups** if you want multiple related sheets to live under one parent tab.
7. On phones, use the **Sheets** pill in the bottom bar to switch sheets without relying on the tab strip.

### 🧩 Sheet types at a glance

| Icon | Sheet type | Best for |
|---|---|---|
| 📊 | Spreadsheet | Calculations, reporting, structured data |
| 🗃️ | Records | Typed tables, linked records, saved views, forms |
| 📋 | Kanban Board | Workflows, backlogs, approvals |
| 📅 | Calendar | Schedules, launches, editorial planning |
| 📈 | Timeline | Roadmaps, project timing, milestones |
| 📊 | Poll | Live votes, surveys, audience feedback |
| 💬 | Chat | Channels, DMs, threads, files, agents, reactions, and Huddles |
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
| 🎥 | Meeting | Workspace-native video calls with notes and attendance |
| 🖥️ | Terminal | A real xterm.js terminal session inside the workbook |
| 🗂️ | Agent Work | Room-wide objectives, agent runs, issues, activity, and evidence |
| 🎮 | Games | Built-in arcade games and high scores |

> 💡 Spreadsheet formulas can pull data from many other sheet types, so your workbook can act like one connected system instead of isolated tabs.

> 💬 The dedicated [Chat Sheet / xChat guide](sheettypes/chat/help.md) covers conversations, threads, files, search, privacy, agents, and Huddles (voice/video hangouts), with screenshots and practical workflows.

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
- **Choose access** — the composer offers **Room**, **Private**, and **Shared** modes. Choosing Private or Shared selects **MeshAgent room storage** and disables Mac/PC storage for that create. These modes also require a stable authenticated principal; if the host cannot identify you, create as Room or connect through the room/IAP identity first.
- **Pin / Unpin** — click the star icon on any workbook row
- **Rename** — right-click a workbook or click `···` to get the context menu; choose `Rename`
- **Move** — right-click a workbook and choose `Move to folder`; drag-and-drop is not available in the current version
- **Delete** — right-click and choose `Delete`; workbooks move to Trash, not permanent deletion
- **Restore** — open Trash, right-click a workbook, choose `Restore`
- **Permanently delete** — right-click in Trash to permanently delete a workbook

Deleting a folder moves its planned workbook children to Trash and keeps their attachments recoverable. If a child changes or a new child appears during deletion, the operation preserves that content and reports a conflict or pending finalization. Restore uses the original nested path when available, otherwise a collision-safe sibling; it keeps access and attachments but gives the restored workbook a fresh creation identity. Old queued automation deliveries do not silently restart as part of that restored identity.

Home retains the deletion or restore request id while an operation is pending. A lost response does not prove that nothing changed: retry the same intent to reconcile its durable receipt. CLI automation can supply `delete-workbook <file> --storage-target <target> --request-id <id> --yes`, with optional `--expected-source-creation-nonce`, `--expected-source-fingerprint`, and `--expected-source-revision` guards. MCP `delete_file` accepts the corresponding `storageTarget`, `requestId`, and source guards. Ordinary files go to Trash; permanent deletion applies only to existing Trash entries. The explicit REST contracts are `POST /api/files/{file}/delete`, `POST /api/folders/{folder}/delete`, and `POST /api/files/{file}/restore`.

After reopening Home, use the pending-operation resume control to finish an interrupted deletion or restore. It reuses the original request and requires the server's existing operation record; it does not silently start a new operation against a replacement workbook. A conflict keeps the pending intent and explains the problem. API callers can use `resumeOnly=true` on those POST routes for the same no-new-plan guarantee; current access and source checks still apply.

### Search in the Library

The search field at the top filters workbooks by name and sheet type as you type. It does not search workbook content — use **Search Across Sheets** for that.

### Multi-select

Click the checkbox that appears on hover to select multiple workbooks. A bulk-delete action appears in the toolbar when files are selected.

### Access filters

The Library has an **Access** filter for **All**, **Room**, **Private**, and **Shared**. Private workbooks you do not own or belong to are hidden from the list instead of showing a disabled card.

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
| **Assistant button** | Opens or closes the AI assistant chat panel |
| **Presence / account chip** | Shows live collaborator avatars; click your chip for account info |
| **Version History** | Circular-arrow icon — browse saved versions, preview prior sheet state, and restore the focused sheet |
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
| Workbook Access... | Set Room, Private, or Shared access for the saved file |
| Version History | Browse saved versions and restore the focused sheet from a prior version |
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

Spreadsheet-specific: filter rules, sort, Find & Replace, data cleanup, External data, Timeline view, Macros & scripts, data validation, conditional formatting, and freeze rows/columns. Other sheet types expose relevant data tools here (e.g., import for Gallery, filter for Records).

### Tools menu

| Item | What it does |
|---|---|
| Automations... | Create and run workbook-native macros |
| Triggers... | Manage reactive rules and background processes |
| Agent Actions... | Manage right-click context menu agent actions |
| Diagnostics | Open the diagnostics and runtime-health pane |

### Help menu

Choose **Help for this sheet** to open the guide for the active sheet. The command palette offers the same action. **Help Center** opens the full searchable reference, and **Welcome tour** reopens the guided start.

Empty Dashboard, Gallery, Records, and File Viewer sheets include an optional guide beside their first-content controls. Close the guide to continue where you left off: add a widget, gallery item, or field, or choose a document to upload.

## 🔐 Workbook Access

Workbook Access controls who can discover and open saved workbook files.

| Mode | Who can see/open it |
|---|---|
| **Room** | Anyone with access to the workspace room |
| **Private** | The owner only |
| **Shared** | The owner plus selected people with Viewer, Editor, or Admin roles |

Private and Shared workbooks can be created only in **MeshAgent room storage** and require a **stable authenticated principal**. Mac/PC storage supports Room-visible creation only. If you see the notice "A stable authenticated principal is required to create a private workbook," the app can run but cannot yet attach the new private file to a durable user identity. Connect through the MeshAgent room/IAP identity, sign in where configured, or create the workbook as Room-visible.

Private workbooks also force link sharing off. If a workbook contains public or legacy upload references, xApps attempts to migrate safe assets into workbook-scoped uploads before making it private; unresolved assets are listed in the Workbook Access dialog.

Owners and admins can open **Workbook Access** from the command palette or Workbook menu to change access mode, add members, review pending access requests, and approve or deny requesters.

## ➕ New Sheet Picker

Click the **`+`** button at the left of the sheet tab strip to open the sheet-type picker.

![The + New sheet picker showing Work, Design, Insight, and Files categories](/help-assets/screenshots/shell-add-sheet.png)

Sheet types are grouped into categories:

| Category | Sheet types |
|---|---|
| **Work** | Spreadsheet, Wiki, Typewriter, Kanban, Timeline, Calendar, Records, Agent Work Center, Meeting, Terminal |
| **Design** | Canvas, Whiteboard, Gallery, Floor Plan, Slides/Presentation |
| **Insight** | Dashboard, Map |
| **Files** | Repository, File Viewer |
| **Play** | Games |
| **Other** | Poll |

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
| **Default sheet type** | Manifest-provided defaultable sheet types, including Records, Spreadsheet, Kanban, Design Canvas, Wiki, Dashboard, Gallery, Calendar, and Agent Work | Pre-selected type in the `+` sheet picker |
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
| **Assistant panel on startup** | Open / Closed | Whether the AI assistant chat panel opens automatically |

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

### Workspace: Version History

![Settings pane showing Version history retention controls](/help-assets/screenshots/shell-settings-version-history.png)

| Setting | What it does |
|---|---|
| **Save version history** | Enables or disables app-native save snapshots for workbook files |
| **Keep up to** | Maximum snapshots retained per workbook before older entries are pruned |
| **Keep for** | Age-based retention window for snapshots |
| **Collapse rapid edits** | Coalesces saves within a short interval so typing does not create one version per keystroke |

### Workspace: Housekeeping

| Setting | What it does |
|---|---|
| **Trash retention** | How long deleted workbooks stay in trash before purging (7/30/90 days or keep forever) |
| **Empty trash now** | Permanently removes all workbooks currently in the trash |

Admin-only controls show a lock indicator for non-admin users; the values are visible but not editable.

## 🕘 Version History

Version History is app-native time travel for saved workbook files. Open it with the **circular-arrow icon** in the top bar or from **More → Version history**.

![Version history panel showing current version, saved snapshots, focused sheet preview, and Restore this sheet action](/help-assets/screenshots/shell-version-history.png)

### What it shows

| Area | What it means |
|---|---|
| **Current version** | The live workbook state you are editing now |
| **Saved versions** | Snapshots written on save, shown newest first with timestamp and revision |
| **Focused sheet preview** | The active sheet as it existed in the selected version |
| **Older / Newer** | Step through snapshots without leaving the panel |
| **Restore this sheet** | Restore only the focused sheet from the selected version |

Selecting a prior version opens a **read-only preview**. For sheet-focused preview, xApps swaps the active sheet into its older state while sibling sheets stay current, matching what restore will do. Closing the panel or choosing **Current version** exits the preview.

### Restore behavior

- Restore is **two-step**: click **Restore this sheet**, then confirm in the panel.
- Restore is **non-destructive**: the server snapshots the current state first, then applies the selected sheet version.
- Restore affects only the focused sheet when the sheet exists and differs in the selected snapshot.
- Private and Shared workbook access rules also protect version listing, preview, and restore routes.

### Retention and automation

Admins configure retention in **Settings → Version history**. The server stores history sidecars next to workbook files and prunes them using the workspace policy.

REST routes:

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/files/:file/versions` | List available versions |
| GET | `/api/files/:file/versions/:id` | Preview a saved workbook snapshot |
| GET | `/api/files/:file/versions/:id/spreadsheet-review?sheet=Sheet1&range=A1:C10` | Review Spreadsheet changed cells, changed ranges, author/name metadata, and unchanged-row visibility for a version |
| POST | `/api/files/:file/versions/:id/name` | Name a saved version |
| POST | `/api/files/:file/versions/:id/restore-range` | Restore one Spreadsheet range from a snapshot |
| POST | `/api/files/:file/versions/:id/restore-sheet` | Restore one named sheet from a snapshot |
| POST | `/api/files/:file/versions/:id/make-copy` | Create a workbook copy from a snapshot |
| POST | `/api/files/:file/versions/:id/restore` | Restore a whole workbook snapshot |

> 🤖 Agent example: an agent can list versions, name the close baseline, review changed ranges for `Budget!A1:F40`, restore only the selected range after a human confirms, or make a workbook copy from that version.

## 💬 Assistant Chat Panel

Click the **Assistant** button in the top bar (or its keyboard shortcut) to open the AI assistant chat panel. The panel is a conversation with a MeshAgent room agent that always has the **current workbook and sheet** as context.

![Assistant chat panel open alongside an active workbook](/help-assets/screenshots/shell-assistant.png)

- Type a message and press `Enter` or click **Send**. The composer placeholder reminds you what you are messaging, for example `Message @assistant about Wiki...`.
- Switching sheets mid-conversation stamps a **context divider** in the log, so answers stay tied to the sheet they were about.
- The assistant can read and describe sheet contents, suggest formulas, help with CLI/API/MCP patterns, and act on your workbook through the composer **`+`** menu.
- Close the panel with the **×** button in the header or by pressing **Escape**.
- **Admin can disable** the assistant workspace-wide via Settings → Assistant → Enabled/Disabled. When disabled, the Assistant button is hidden for everyone in the room.

> The chat panel loads on demand — the first time you open it, xApps fetches the chat bundle, so the very first open can take a moment.

### Panel anatomy

| Area | What it holds |
|---|---|
| **Header** | The 💬 assistant avatar, the agent name / picker, a live status line (`Connected`, `Connecting`, or `Working`), a **`＋ New`** button, a **`Threads (n)`** switcher, and the close button |
| **Thread bar** | The **Private / Room** space switcher, the current thread title (click it to switch threads), and an at-a-glance scope color |
| **Message log** | Your conversation, grouped by sheet context, with an inline **Activity** toggle at the bottom |
| **Composer** | The message box, the **`+`** actions menu, attachment pills, and the **Send** button |

### Private and Room chat spaces

The thread bar has a two-button switcher: **`🔒 Private`** and **`👥 Room`**. These are two **distinct spaces**, and the switcher **navigates** between them — it never converts a thread from one space to the other.

- **`🔒 Private`** — "only you and the agent can see it." A private chat can never become room-visible by flipping the switch.
- **`👥 Room`** — "visible to everyone in this room."
- A short explainer line under the switcher restates which space you are in.
- The panel also gives each space an **ambient color** (a green treatment for Room, a neutral treatment for Private) so you can tell at a glance where you are.
- Clicking the other space opens your most-recent thread there, or starts a fresh thread if that space is empty. Your current thread stays put in its own space.

### Threads: create, switch, rename, delete

Every workbook keeps its own set of saved assistant threads (up to 50).

- **New thread** — click **`＋ New`** in the header (starts a thread in the current space).
- **Switch** — open **`Threads (n)`** in the header, or click the current thread title in the thread bar. Both dropdowns list threads in two captioned sections, **`🔒 Private`** then **`👥 Room`**. Click a thread to reopen it; its agent binding is shown as an `@handle` badge.
- **Rename** — click the **`✎`** pencil on a thread row. The title becomes an inline field; press **Enter** to save or **Escape** to cancel.
- **Delete** — click the **`×`** on a thread row. It arms to **`Delete?`** and waits about 3 seconds for a confirming second click before removing the thread (no browser pop-up). Deleting the active thread falls back to another thread in the same space.

### Unread markers

Threads updated since you last looked show an **unread dot** before their title, and the **`Threads`** switcher shows a small unread count next to the caret. Unread state is a per-browser viewing cue — simply opening a thread marks it read. The thread you are viewing is never flagged unread.

### The composer "+" actions menu

The **`+`** button next to the message box opens a single-level **Actions** menu that turns the conversation into workbook writes. Each row shows a verb, its destination, and a **tier badge**:

| Action | Where it goes | Tier |
|---|---|---|
| **Summarize** | Replies in the thread | **INSTANT** |
| **Create task** | → Tasks (Kanban), opens a prefilled draft | **FORM** |
| **Wiki page** | → Wiki, opens a prefilled draft | **FORM** |
| **Log evidence** | → Gallery, opens a prefilled draft | **FORM** |
| **Dashboard** | → Dashboard, the agent proposes a layout | **IN CHAT** |

Below a divider, **Attach files** opens the file picker (you can also just paste into the message box).

The tiers behave differently on purpose:

- **INSTANT** — Summarize runs immediately and drops a receipt in the log.
- **FORM** — Task / Wiki / Evidence open a **docked draft card** above the composer, prefilled and ready. While a draft is docked the composer is parked (`Finish or cancel the draft above to keep chatting…`); press **Enter** to create, **Escape** to cancel. Submitting writes to the destination sheet and leaves a receipt.
- **IN CHAT** — Dashboard is delegated to the agent as a normal turn; the agent proposes a draft in the thread and waits for your approval before writing.

**Act on a specific reply.** Each assistant reply has a hover pill, **`⚡ Act on this reply`**. Click it to open the same `+` menu scoped to that exact reply — the chosen action's draft is prefilled from that reply's text and carries a "from the agent's reply" provenance chip. Without scoping, actions use the latest reply.

**Receipts and Undo.** Completed actions leave a receipt row (`✓` done, `✕` error) with a title, detail, and an **Open** link to what was created. Task, Wiki page, and evidence receipts also show an **Undo** button that deletes the created item and flips the receipt to **Undone** (`↩`). Summaries and dashboard widgets are not undoable.

### Inline Activity (no tabs)

The panel has **no tab strip** — there is no separate Chat / Actions / Activity / Threads tab. Everything lives in one scrolling conversation. At the bottom of the log a small **`⚙ Activity`** pill (with a count) expands an inline diagnostic panel showing the connected **MeshAgent room** capability card (room agents and toolkits available) plus recent tool calls and events. The expanded/collapsed state is remembered.

> The specific tools an agent can use depend on what the connected MeshAgent room provides; the Activity panel is where you can see the toolkits and agents currently available to the assistant.

**Approvals always surface.** When an agent wants to run a tool that needs sign-off, a blocking card appears inline (even with Activity collapsed) with **Approve**, **Edit** (adjust the response first), and **Reject**.

### Picking and mentioning agents

When a room exposes more than one agent, the header agent name becomes a **picker**. Choosing a different agent saves the current thread under its existing owner, shows **Connecting**, and temporarily disables the composer. Once the target agent is bound, xApps opens a clean thread for that agent; the previous conversation stays in **Threads** with its own `@agent` badge. If the bind fails, the current agent and conversation stay in place.

Plain messages always follow the agent shown in the picker. A leading `@agent` mention is an explicit target for that message. Reopening a saved thread restores its saved agent and history together, so an Assistant conversation cannot appear under a MacCodex header (or vice versa).

Reconnect recovery keeps the saved thread's canonical agent owner together with its path. If a saved thread's agent cannot bind, xApps leaves the current header, conversation, and controls in place instead of showing the target history under the wrong agent.

### Long-running turns and switching away

The assistant is built to survive slow, tool-heavy turns and thread switching:

- **Per-thread live turns.** Each thread runs its own conversation. Switch to another thread or agent while a reply is streaming and the first turn keeps running in the background; the unread dot updates and you see it live when you return.
- **Two-stage watchdog.** Any agent activity resets the timer, so a genuinely long answer is not killed. After ~45s of true silence you either see `Still working — this step is taking a while…` (if connected) or a dropped-connection notice; a hard stall (~5 min of silence) fails the turn and forces a reconnect.
- **Turn controls.** While a turn runs, **Stop** interrupts it and **Regenerate** re-runs the last answer.
- **Redirect a streaming answer.** While an answer is streaming and steerable, the Send button becomes **Redirect** (`Redirect the active answer...`) so typed text steers the in-flight turn instead of starting a new one.
- **Recovery notices.** If saved history does not replay after a reconnect, the thread shows a recovery notice and lets you keep going or start fresh.

### Attachments

Add files to a message three ways: the **`+` → Attach files** row, the paste shortcut (paste an image or file straight into the message box), or drag into the picker. Each attachment shows a pill with a thumbnail/icon, name, size, and status (**Uploading** → **Ready**, or an error). Send is blocked until uploads finish. Images the agent sends back render inline with a **Download** link, and assistant replies render Markdown.

### Thread persistence and visibility

Assistant history is scoped to the workbook in the URL. xApps keeps three coordinated layers:

- a **local per-browser cache** of full conversation bodies for instant same-browser restore, and
- a **thin shared workbook index** with agent name, thread path, title, timestamp, and Private/Room visibility, plus
- a **durable server thread store** behind `/api/workbook/assistant-threads` that retains full bodies in the room dataset or owner-scoped atomic filesystem sidecars.

The agent's own room/dataset thread is the source of truth for message bodies; a fresh browser replays them from there. Switching workbook routes saves the old workbook's threads and hydrates the new workbook's set, so each workbook restores its own Private and Room threads, active thread, and inline-Activity state when you return. A merge guard prevents a thin server entry from wiping a cached conversation. If durable storage is damaged, xApps keeps the browser copy visible and pauses automatic save retries instead of looping errors. Retryable failures resume after a real thread change; nonretryable corruption stays paused until storage is repaired and explicitly retried.

Maintainers: staged deployment, health checks, legacy backfill, recovery, and data-preserving rollback for the shared Assistant/Chat Sheet Agent Session layer are documented in [`docs/AGENT_SESSION_ROLLOUT.md`](AGENT_SESSION_ROLLOUT.md).

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
| **Workbook** | Save workbook, Open workbook, New workbook, Starter kits, Workbook Access, Sheet groups, Automations, Triggers, Agent Actions |
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

## 🔧 Diagnostics Pane and Runtime Health (Shell)

Open Diagnostics with the **diagnostics icon** in the top bar. On narrow layouts, use the top-bar overflow menu and choose **Diagnostics**. It is also reachable from the command palette.

The Diagnostics pane is a read-only snapshot of the running server internals — useful for debugging deployments, checking room connectivity, and confirming which capabilities are active.

![Diagnostics pane showing runtime, deployment, workbook, MeshAgent toolkit, surfaces, and redacted environment status](/help-assets/screenshots/shell-diagnostics-pane.png)

| Section | What it shows |
|---|---|
| **Runtime** | xApps version, Node version, platform, PID, hostname, uptime, memory (RSS, heap, external) |
| **Deployment** | App name, profile, deployment mode, NODE_ENV, host:port, public base URL |
| **Storage** | Data dir, state file, workbook root, current workbook file, workbook size |
| **Workbook** | Current file, title, revision, active sheet, sheet count, sheet types |
| **Collab** | Room name, Yjs doc name, and whether the live collab room is open |
| **MeshAgent toolkit** | Whether the workspace host attempted to publish room toolkits, the room name, published toolkit count, names, and last error |
| **Agent workbook scope** | Whether room assistants can see the current workbook through this host or only through the room/cloud toolkit |
| **Agent terminal messaging** | Connector count, room-agent count, dispatch count, phase, last event, and connector/room-agent status |
| **Surfaces** | List of registered sheet-type modules |
| **Environment** | Which environment variables are set/unset (values are redacted for security) |

The pane loads from `GET /api/diag`. It is workbook-ACL gated before returning workbook details and uses a default-deny environment allowlist: safe path/mode values can be shown, but secret-shaped keys such as tokens, cookies, OAuth secrets, and API keys are reported only as `set` or `unset`.

### Health and diagnostics endpoints

| Endpoint | Purpose |
|---|---|
| `GET /healthz` | Lightweight unauthenticated liveness probe for orchestrators. Returns `ok`, `status: "healthy"`, Yjs metrics, and Google Calendar session count without workbook details. |
| `GET /readyz` | Unauthenticated traffic-readiness probe. Returns `503` with `state: "starting"` before startup completes, `200` while ready, and `503` with `state: "draining"` plus `Retry-After: 1` as soon as graceful shutdown begins. Keep liveness pointed at `/healthz`; use `/readyz` only where the platform supports a distinct readiness probe. |
| `GET /status` / `GET /liveness` | Gated host status with app name, install mode, builder flag, persistence state, public base URL, and workbook summary. |
| `GET /api/diag` | Full Diagnostics pane payload for the current workbook scope. |
| `GET /api/meta/capabilities` | Generated capability payload used by agents, diagnostics, CLI discovery, OpenAPI/help tooling, and MeshAgent toolkit setup. |
| `POST /api/client-errors` | Browser error-reporting sink. Startup/runtime failures are posted here even from stale tabs before file scoping, so operators can diagnose blank screens or boot failures. |

### Agent Work and operator recovery

Agent Work has its own diagnostics because it spans workbooks and machines through the `xapps/agent-work` room dataset.

| Check | Command |
|---|---|
| Agent Work dataset health | `xapps agent-work status --json` |
| Work-item, activity, run, and attachment queries | `xapps agent-work work-items --json`, `xapps agent-work activity-events --json`, `xapps agent-work agent-runs --json`, `xapps agent-work attachments --json` |
| Rebuild missing Agent Work rows from saved Kanban cards | `npm run agent-work:backfill -- --file <Workbook.json> --json` |
| Repair workbook access metadata | `npm run workbook-acl:repair -- --file <Workbook.json>` |

The backfill command plans by default. Use its documented write mode only when connected to the intended MeshAgent room and after reading the plan.

### Repo health gates

For maintainers and agents, the repo-level health checks that keep help, capability discovery, and surface coverage honest are:

```bash
npm run check
npm run check:coverage-manifest
npm run report:coverage
tools/scorecard-audit.sh --quick
npm run test:smoke:diagnostics-endpoint
npm run test:smoke:diagnostics-pane-ui
npm run test:smoke:healthz-metrics
npm run test:smoke:client-error-capture
```

`npm run check:coverage-manifest` verifies the checked-in coverage manifest, while `npm run report:coverage` produces the current coverage report. `tools/scorecard-audit.sh --quick` is the architecture/modularity scorecard used after architecture-facing changes.

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
- one or more room-identity members and optional watchers
- up to 20 card-level file or link attachments
- custom fields, such as start date, stop date, amount, account, stage, or probability

### 🧩 Card fields

Each kanban sheet can define its own card schema through the board's **Card fields** setting. Standard task fields can be hidden for that sheet, standard labels can be renamed through **Field labels**, and custom definitions live on the sheet as `kanbanCustomFields`. The visible layout is stored as `kanbanCardFieldLayout`; card values live on each card in `customFields`. This lets one board use normal task cards while another board uses CRM-style opportunity cards without changing the canonical stored columns.

Card fields are exposed through the Kanban REST API, SDK helpers, CLI commands, MCP tools, and MeshAgent toolkit tools. Use `xapps kanban-custom-fields <board>`, `xapps set-kanban-custom-fields <board> <json>`, `xapps kanban-card-field-layout <board>`, and `xapps set-kanban-card-field-layout <board> <json>` for CLI access.

On a MeshAgent-room-connected workspace, card members use stable xApps principal identities instead of free-form names. Members are responsible for the card; watchers receive updates without becoming the legacy primary assignee. Assignment, status, comment, and `@Display Name` mention events are written to a private durable inbox before the host attempts direct online delivery. Offline recipients see the same unread items after reconnecting. The browser reads `/api/kanban-collaboration/people` and `/api/kanban-collaboration/notifications` in the active saved-workbook scope; inbox rows and read acknowledgements are always pinned to the current authenticated principal, and participant delivery ids are never returned to the browser. When the room dataset is unavailable, shared Kanban editing remains usable and the collaboration controls show an honest unavailable state.

For automated writes, use an explicit saved workbook (`--file <Workbook.json>`), `--json`, `--verify`, and `--agent` (or `--strict`). Strict mode requires stable card ids and provenance and always rejects numeric row targets. For an agent workflow transition, read `card-json` to get the card `revision`, then use `transition-card` with `--expected-revision`, a durable `--request-id`, a typed comment, and `--verify`. The same request id and payload safely replay a lost response without duplicating evidence; a stale revision returns a conflict rather than overwriting newer work. REST callers use `POST /api/sheets/{name}/cards/{cardId}/transition`; hosted agents use `transition_kanban_card` (MCP) or `xapps-kanban.kanban_transition_card` (MeshAgent toolkit). Use ordinary update tools for non-workflow field patches.

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

Calendar also supports manual availability coordination. An organizer creates a request, enters invitee email addresses, and sends each person a private response link. Invitees mark each proposed time Available, Maybe, or Unavailable without connecting or sharing a calendar. The organizer sees ranked aggregate results, can send reminders, rotate or revoke links, and finalize one slot into a Calendar event.

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
- When Google Calendar is available, use **Connect Google** (or **Sign in with Google** when the host requests authentication), complete the official Google consent flow, then use **Sync**. The saved workbook and Calendar sheet are restored after the redirect.
- Google Calendar access is optional. Local Calendar events continue to work when Google is disconnected or unavailable.
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

Canvas now includes a starter template library for common design jobs, with search, categories, single-page designs, and multi-page deck starters:

- Social Quote
- Product Promo
- Story Announcement
- Event Flyer
- Brand Board
- Moodboard
- Product Launch Deck
- Fundraising Pitch Deck
- Marketing Campaign Kit

Use the `Templates` button in the page bar or `Design -> Apply template...`.
If the current page is empty, the template replaces it. If the page already has content, xApps inserts the template as a new page so your work stays intact. Template sets create several Canvas pages in one apply operation.

### Start with AI

Open **Templates** in the left rail to describe a design, choose a format and style, and generate a starting page. Canvas creates normal editable objects, shows assistant progress, and lets you switch among generated variants without appending duplicate object sets.

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

### Stock photos and icons

Open **Elements** and search for terms such as `coffee`, `team`, or `home`. Canvas searches stock photo providers through `/stock/photos`, using Openverse by default and Unsplash/Pexels when `CANVAS_UNSPLASH_ACCESS_KEY` or `CANVAS_PEXELS_API_KEY` are configured. Provider results show real image thumbnails with attribution metadata.

If provider search is unavailable, Canvas shows an explicit source state instead of fake photo tiles. Use **Add URL / upload** to add a photo from your device or a URL, or select an image on the artboard and use **Replace selected** to swap its source while keeping its position.

Inserted provider photos keep attribution, license, source URL, provider, and source image metadata on the image object. Icons use the local Iconify-compatible fallback set, insert as SVG image objects, and retain the selected color, collection, and license metadata.

### SVG import

Drop an SVG file on the Canvas artboard, or upload it from **Uploads**. Supported SVG primitives (`rect`, `circle`/`ellipse`, `polygon`, `line`, `text`) become normal editable Canvas objects with fills, strokes, simple transforms, and text styling where the Canvas object model supports them. Complex paths, filters, gradients, and other unsupported fragments still import as uploaded image objects so the artwork is preserved.

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

- `canvas-list-objects`, `canvas-get-object`, `canvas-update-object` for typed inspection and guarded single-object edits
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
- Native **xApps storage**, room-mounted storage, and other non-Google sources use the room/IAP identity and do not require Google sign-in. Repository exposes one canonical native root beneath the configured data directory; connect Google only when you want a Google Drive source.
- **Google Drive** remains visible as an optional Repository source when it is disconnected. After signing in, **Connect** uses the shared per-feature Google consent flow; disconnecting Drive preserves an independently connected Calendar.

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

## 🎥 Meeting

### Workspace-native video calls

Meeting sheets add a video-conference surface to the workbook. They store the meeting plan, dated sessions, invite history, notes links, and attendance metadata in the sheet, while live audio and video travel through the active MeshAgent room and LiveKit.

> 🤖 Agent example: an agent can scaffold a meeting sheet for a specific date, pre-fill the title, breakout room, and notes sheet, generate the invite link, and email invites — then a human joins and runs the call.

### What it provides

- **Pre-join lobby** — meeting date, title, breakout room, notes, notes-sheet link, and microphone/camera defaults before joining.
- **Participant stage** — adaptive grid with active-speaker emphasis, participant labels, and media-status badges.
- **Controls** — microphone, camera, screen sharing, join, and leave.
- **Invite panel** — share link, copy action, email-invite action, and clear-history.
- **Dated history** — multiple meetings (by date) in one sheet; switching dates keeps each meeting's invites, notes, participants, and timestamps separate.
- **Grant-aware unavailable state** — a clear message when the browser cannot reach the MeshAgent room or the room exposes no LiveKit credentials.

Live audio/video requires browser media permission and a MeshAgent room with LiveKit credentials; outside that, the sheet shows the lobby and the unavailable state. Email invites require SMTP configuration with an explicitly provisioned sender mailbox; MeshAgent room credentials may supply transport defaults but never invent a mailbox identity. Use `xapps help meeting` for the command catalog.

## 🖥️ Terminal

### A real terminal inside the workbook

Terminal sheets render a live browser terminal (xterm.js) as a workbook surface. They support local host PTY sessions and MeshAgent-relayed PTY sessions from a named remote Mac connector.

> 🤖 Agent example: an agent can stand up a terminal sheet, capture the tunnel target command and MeshAgent room URL in the setup dialog, and hand a connected shell to a human operator.

### What it provides

- **Terminal sheet type** in the add-sheet menu; `xterm.js` renders inside the sheet and accepts keyboard input.
- **Local mode** starts a PTY on the current xApps host.
- **MeshAgent mode** relays an interactive PTY from the Mac connector through the room; the Mac dials out and does not open inbound ports.
- **Setup-tunnel dialog** captures the target command, remote Mac label, MeshAgent room URL, and working directory. The connector relies only on the selected room's MeshAgent-injected runtime token; xApps accepts no token override.

Treat terminal connector permissions as a separate operational boundary. Access to a private workbook does not automatically grant access to every terminal connector.

Use `xapps help terminal` for the command catalog.

## 🧭 Agent Work Center

Agent Work Center is a room dataset console for cross-workbook agent work. It reads the central `xapps/agent-work` dataset namespace and shows Kanban work items, activity events, agent runs, evidence metadata, completion summaries, and dataset health.

Use it when several workbooks or several agents need one shared view of active work. Workbook Kanban cards remain the editable source; Agent Work Center is the query and monitoring layer.

It is not a replacement for Kanban, a private agent memory viewer, or a distributed lock manager. Agent claims use `agent_runs` lifecycle, heartbeat, and lease fields; workbook edits still resolve through workbook save/collab behavior.

### What it provides

- **Overview** for rollups, recent evidence, recent completion summaries, and activity.
- **Work Items** for card-level rows, owning workbook links, evidence counts, and completion summary detail.
- **Activity** for filtered event streams, including evidence and failure quick filters.
- **Agents** for request lifecycle, routing, heartbeat, and lease state.
- **Evidence** for image and attachment metadata with large preview on thumbnail click.
- **Datasets** for table counts, index readiness, and query previews.

### Completion summaries

When a tracked Kanban card moves to `Done`, `Complete`, or `Completed`, Agent Work emits a `work_item_completed` activity event with structured `data_json.summary` fields. The Wiki should still carry the human-readable outcome, verification, evidence links, risks, and follow-ups; the dataset row is the queryable record used by Agent Work Center, CLI, SDK, MCP, and hosted toolkit reads.

Operational rollout and recovery notes live in `docs/agent-work-rollout-notes.md`.

### Multi-agent use

Multiple agents on different computers can share one Agent Work Center when they connect to the same MeshAgent room and dataset namespace. Latest card/run state is merged by stable ids, activity history is event-based, and active claims depend on `agent_runs` heartbeat and lease data. The dataset is not a distributed lock, so conflicting card edits still resolve through workbook save/collab behavior.

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
| Spreadsheet | CSV, TSV, Excel, ODS | CSV, TSV, Excel, ODS, PDF |
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
- Workbook files, Yjs snapshots, CSV/TSV/Excel/ODS sheet imports, ICS calendar import, PPTX import staging, DXF import staging, and image uploads now flow through server APIs
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

### CSV and TSV Import and Export (Spreadsheet)

**Import:** Use `File -> Import -> CSV`, `Spreadsheet -> Open -> Import/export fidelity`, or the CLI command `import-csv`. CSV import maps each row to a spreadsheet row and each comma-separated value to a column. TSV uses the same server-backed replacement path with tab-separated values.

```bash
xapps open-workbook MyWorkbook.json
xapps import-csv "Stock Data" data.csv
```

**Export:** Use `File -> Export -> CSV`, `File -> Export -> TSV`, or the CLI command `export-csv`. You can export the full sheet or a specific range.

```bash
xapps open-workbook MyWorkbook.json
xapps export-csv "Stock Data" --out report.csv
xapps export-csv "Stock Data" --range A1:K502 --out subset.csv
```

> **Tip:** Use `clear-sheet` before `import-csv` when you want a clean replacement instead of appending to existing data.

### Spreadsheet Fidelity, XLSX, ODS, and PDF

Use `Spreadsheet -> Open -> Import/export fidelity` before moving a Spreadsheet to another app. The panel reports which features are lossless, partial, values-only, or print-only for `.xss`, XLSX, ODS, CSV, TSV, and PDF, then offers matching import and export actions.

**Import:** Use `File -> Import -> Excel/ODS` to load `.xlsx`, `.xls`, or `.ods` files. The importer reads cell values, basic formatting, and merges. Multi-sheet files import the active sheet by default.

**Export:** Use `File -> Export -> Excel`, `File -> Export -> ODS`, or `File -> Export -> PDF` from the current spreadsheet sheet. Agents can request the same analysis with `xapps fidelity-report "Sheet Name" --json`.

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
- **Spreadsheet** — `File -> Export -> PDF`
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
| Spreadsheet | CSV, TSV, XLSX, XLS, ODS | CSV, TSV, XLSX, ODS, PDF |
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
- workbook access
- recent workbooks
- sheet-specific actions

It is the fastest way to move around large workbooks.

## 🔐 Workbook Access

Saved workbook files have Workbook Access metadata:

> 🤖 Agent example: an agent can prepare a workbook handoff by setting Shared access, confirming the saved file path, and adding the right reviewers before handing the workbook back to a human.

- **Room** — visible to everyone in the workspace room
- **Private** — visible only to the owner
- **Shared** — visible to the owner plus selected people

Workbook Access works on saved workbook files, not unsaved in-memory state. Private and Shared access requires a stable authenticated principal so the owner and selected-person grants can be tied to durable identities.

Use:

- `Workbook -> Workbook Access...`
- command palette: `Workbook access`

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
| POST | `/api/webhooks/:hookId` | Fire a webhook rule on the host's bound workbook |

Webhook callers authenticate with `X-XApps-Webhook-Secret` (or `?secret=`).
For safe retries, send a stable `X-XApps-Request-Id` and the same JSON intent.
While its receipt is retained, an authenticated retry returns `replayed: true`
without firing again; reusing the key with different JSON returns 409. Object
key order is ignored, but array order matters. Missing or blank keys make each
call a separate event. Current rule enablement and secret are checked even on
retries. Only the newest 256 receipts per rule are retained; deleting/resetting
the rule or its receipts ends that protection. Ordinary per-rule edits preserve
receipts when `metadata.webhookRequests` is omitted. An acknowledgement error
does not prove that the event was unsaved: retry with the same key, or reconcile
source state before resending an unkeyed call. This is event admission, not proof
of external provider delivery. See the [webhook contract](/docs/contracts/platform-modules.md#webhook-admission-and-replay).

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

The help dialog has its own built-in search so you can jump to the right help section quickly. It searches section titles, section content, and platform aliases, so feature terms like `diagnostics`, `healthz`, `client errors`, `versions`, `versioning`, `chatbot`, `settings`, and `workbook acl repair` surface the relevant help even when the exact phrase is not the section title.

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

MeshAgent room agents should run those commands from the deployed xApps runtime image, for example `registry.meshagent.com/powerboards/xapps:v2.9.56` when that is the room tag. A sibling container without that image does not have the xApps CLI runtime unless the room explicitly starts or switches into the xApps container.

Set the API target with explicit `--base-url`, `XAPPS_INTERNAL_API_BASE_URL`, `MESHAGENT_ROOM_URL`, or `XAPPS_API_BASE_URL`; retired sheet-API URL variables are not read by the current CLI. In the packaged xApps Docker runtime, `/app/bin/xapps.js` seeds `XAPPS_INTERNAL_API_BASE_URL` to the same-runtime workspace API port; the workspace host does the same when launched directly. When that internal URL is unset and `MESHAGENT_ROOM_URL` is present, the CLI parses it as a URL, replaces its port with `3001`, materializes that value into `XAPPS_INTERNAL_API_BASE_URL` for the CLI process, and prefers it over `XAPPS_API_BASE_URL`:

```bash
export MESHAGENT_ROOM_URL="http://192.0.2.10:8078"
export XAPPS_API_BEARER_TOKEN="$MESHAGENT_TOKEN"
xapps list-workbooks --json
```

The example room URL above resolves to `http://192.0.2.10:3001` for xApps API calls only when `XAPPS_INTERNAL_API_BASE_URL` is unset; the CLI replaces the port rather than appending a second port.

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

Current command groups include workbook, agent-work, calendar, canvas, dashboard, doc, fileviewer, floorplan, gallery, games, kanban, map, meeting, poll, presentation, records, repository, spreadsheet, terminal, timeline, typewriter, and whiteboard. Use `xapps --help` and `xapps list --json` as the source of truth.

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
xapps create-workbook "Private Ops" --sheet kanban:Tasks --access private
xapps create-workbook "Shared Ops" --sheet kanban:Tasks --storage ma --access shared --member editor@example.com:editor
xapps list-workbooks --storage localhost --json
xapps list-workbooks --storage ma --json
xapps workbook-access "Shared Ops.json" --storage ma --json
xapps set-workbook-access "Shared Ops.json" --access shared --member reviewer@example.com:viewer --storage ma
```

`xapps sheets --json` returns each sheet's user-facing `name`, `type`, and `shorthand` such as `kanban:Sprint Board`. Surface commands accept either the sheet name or the type-prefixed shorthand.
`create-workbook` auto-suffixes on a name collision (`"Operations"` → `Operations 2.json`); the `--json` output always carries the final name in `file` plus `renamed` / `requestedFile` / `requestedTitle` markers, and `--exact` refuses a collision with the typed `workbook_file_exists` error (409) instead. Workbook file commands accept `--storage`, `--storage-location`, or `--storage-target` with `local|localhost|ma|meshagent-room|mac|mac-local`. If MA storage is unavailable, verify room credentials and run the host through `meshagent room connect`; canonical MA hosts use the Room Storage API and never a room mount. If Mac storage is unavailable, start a Mac connector in the room advertising `mac-local`; MA xApps uses that connector for bounded workbook operations and does not access the Mac filesystem directly. Workbook ACL privacy uses `create-workbook --access ...`, `workbook-access`, and `set-workbook-access`, not link-sharing metadata. `--member` accepts `email@example.com:editor` or `principal-id:viewer`; valid roles are `viewer`, `editor`, and `admin`, and `--member` can be repeated.

### Spreadsheet Commands

```bash
xapps get "Budget" A1
xapps set "Budget" A1 "Revenue"
xapps format "Budget" A1 '{"bg":"#ff0000"}'
xapps range "Budget" A1:D10 --json
xapps bulk-set "Budget" A1 '[["Name","Amount"],["Rent","2000"],["Food","800"]]'
xapps import-csv "Stock Data" data.csv
xapps export-csv "Stock Data" --range A1:K502 --out subset.csv
xapps fidelity-report "Stock Data" --format xlsx --json
xapps data-cleanup "Stock Data" remove-duplicates A1:K502 --keys A,B --has-header --apply
xapps spreadsheet-external-data-sources "Stock Data"
xapps create-spreadsheet-external-data-source "Stock Data" "Sales feed" '{"connectorType":"inline-json","source":{"text":"[{\"Product\":\"Desk\",\"Revenue\":320}]"},"extract":{"targetRangeStart":"A1"}}'
xapps refresh-spreadsheet-external-data-source "Stock Data" sales-feed --confirm
xapps spreadsheet-timeline-views "Stock Data"
xapps create-spreadsheet-timeline-view "Stock Data" "Launch timeline" A1:H20 '{"title":"Task","start":"Start","end":"End","progress":"Progress","status":"Status","group":"Phase"}' --group-by Phase --target-sheet "Launch Timeline"
xapps export-spreadsheet-timeline-view "Stock Data" launch-timeline --target-sheet "Launch Timeline"
xapps spreadsheet-macros "Stock Data"
xapps create-spreadsheet-macro "Stock Data" "Fill report" '[{"type":"set-cell","ref":"A1","value":"Report"}]' --require-confirmation
xapps run-spreadsheet-macro "Stock Data" fill-report --confirm
xapps add-chart "Budget" '{"type":"bar","title":"Spend","dataRange":"A2:B8","labelCol":"A","valueCol":"B"}'
xapps add-table "Budget" '{"name":"Expenses","rangeStart":"A1","rangeEnd":"C20","groupBy":["Category"]}'
xapps sort-table "Budget" expenses Amount --direction desc
xapps table-groups "Budget" expenses
xapps named-functions
xapps set-named-function GROSS_MARGIN "revenue,cost" "=(revenue-cost)/revenue" --desc "Returns gross margin percent"
xapps set-rich-cell "Budget" B2 '{"type":"link","label":"Project plan","value":"Project plan","url":"https://example.com/plan"}'
xapps set-sparkline "Budget" C2 B2:B12 --type bar
printf '{"op":"spreadsheet.formatCell","ref":"A1","format":{"bg":"#ff0000"}}\n' | xapps spreadsheet batch "Budget" --stdin
```

`xapps get` prints evaluated formula results. The raw stored formula is available from the cell API as `rawValue` when using `?evaluate=1`.
Add `--json` to spreadsheet commands when agents need structured success output with `ok`, `message`, and command-specific fields.

For high-volume edits, use `xapps mutate --stdin` or surface batches such as `xapps spreadsheet batch <sheet> --stdin`. They send validated semantic ops to the server-side Yjs path so many cell writes are applied in one Yjs transaction and JSON persistence is debounced.

Because collab (Yjs) persistence is debounced (~5 seconds), a host restart inside that window can revert recent writes. Run `xapps flush` (respects `--file`) after write-heavy work and before stopping or restarting the host — it force-persists the pending debounced save immediately, replacing the old "sleep 3-5 seconds before restart" workaround.

Structured table payloads support `id`, `name`, `rangeStart`, `rangeEnd`, `headerRow`, `style`, `columns`, `sortRules`, and `groupBy`. When `columns` is omitted, xApps derives table columns from the header row. Table sorting reorders only body rows so the header row stays in place, and grouped reads return records plus `count` and numeric `sums`.

Named functions are workbook-scoped reusable formulas. They can be created from the Spreadsheet Data menu or with `xapps set-named-function <name> <args-csv> <formula>`, then called from cells like built-in functions.

Smart chips are rich cell objects with a plain fallback value for formulas, CSV export, and automation. Use **Insert > Insert smart chip...** or `xapps set-rich-cell <sheet> <ref> <json>` to create people, file, date, dropdown/status, place, sheet-reference, or link chips with metadata such as URL, email, date, address, sheet/range, color, description, and dropdown options. The dialog changes fields based on the selected chip type, including allowed values plus a Current value picker for dropdown/status chips. For dropdown/status chips, edit Allowed values first; the Current value picker is rebuilt from those options before saving. Click a dropdown/status chip or its arrow to choose one of its configured allowed values. Select an existing chip cell and use **Format > Smart chips > Edit smart chip...** or the cell context menu to edit it. Use `xapps rich-cell <sheet> <ref>` to inspect metadata and `xapps clear-rich-cell <sheet> <ref>` to remove it.

In the spreadsheet UI, select a range and click **Format as Table**. Table headers show one arrow sort control; the arrow points up for ascending and down for descending, and sorting only reorders the table body. Toolbar A/Z sorting also targets the table body when the selected cell is inside a table. Use **Alternating Colors** for plain striped ranges without creating table metadata. To group records, select a cell in the table column you want to group by, then choose **Data > Table > Group by selected column** or right-click the cell and choose **Table > Group by selected column**. Use **Data > Table > Clear grouping** or **Table > Clear grouping** to remove grouping. Formulas can reference structured tables with `TableName[Column]`, `TableName[#Headers]`, `TableName[#Data]`, and `TableName[#All]`, for example `=SUM(Expenses[Amount])`.

### Surface Examples

```bash
xapps cards "Sprint Board" --status "In Progress"
xapps list-cards "Sprint Board" --status "In Progress"
xapps add-card "Sprint Board" "Fix login bug" --list "To Do" --labels "P1,bug" --due "2026-04-15"
xapps card-json "Sprint Board" TASK-42
xapps transition-card "Sprint Board" TASK-42 "In Progress" --expected-revision 4 --request-id task-42-start --message "Picked up work" --author codex-agent --type progress --verify --agent --json
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
xapps scheduling-sessions "My Calendar"
xapps create-scheduling-session "My Calendar" '{"title":"Board meeting","startDate":"2026-07-20","endDate":"2026-07-31","dayStart":"08:00","dayEnd":"18:00","durationMinutes":60,"timeZone":"America/Los_Angeles","weekdays":[1,2,3,4,5],"invitees":[{"email":"alex@example.com"}],"deliverInvitations":true}' --verify
xapps send-scheduling-invitations "My Calendar" schedule-123 --kind reminder --rotate --verify
xapps finalize-scheduling-session "My Calendar" schedule-123 slot-123 --verify
xapps widgets "My Dashboard"
xapps add-widget "My Dashboard" '{"type":"kpi","title":"Revenue","dataSource":{"sheetName":"Budget","range":"B2"}}'
xapps slides "Pitch Deck"
xapps add-text-box "Pitch Deck" slide-1 "Hello World" --x 100 --y 200 --size 36
xapps add-sticky "Brainstorm" "Great idea!" --x 100 --y 200 --bg "#fff475"
xapps canvas-templates
xapps register-canvas-template "Design" --input ./launch-template.json --replace
xapps render-canvas-template-thumbnail "Design" launch-template --out launch-template.svg
xapps remove-canvas-template "Design" launch-template
xapps canvas-template-factory "Design" --category Fundraising --brief "Neighborhood arts fundraiser" --count 20 --replace
xapps apply-canvas-template "Design" report-summary --brand-kit '{"primary":"#2563eb","fontHeading":"Inter","fontBody":"Inter"}'
xapps apply-canvas-template "Design" fundraising-pitch-deck --mode insert
xapps canvas-brand-report "Design" --brand-kit '{"colors":["#2563eb","#111827","#ffffff"],"fonts":["Inter"]}'
xapps add-canvas-text "Design" "Headline" --x 100 --y 100 --size 48 --color "#fff"
xapps viewer-files "Docs"
xapps repo-files "Repository"
xapps games-scores "Arcade"
xapps typewriter wordcount "Report"
xapps typewriter export "Report" md --out report.md
xapps doc-add-page "Encyclopedia" "First Article" --icon 📜 --summary "Intro entry"
xapps doc-add-page "Encyclopedia" "First Article" --id intro --summary "Idempotent upsert: same --id updates the page in place"
xapps doc-add-block "Encyclopedia" page-2 --type heading2 --text "Background"
xapps doc-add-block "Encyclopedia" page-2 --type callout --text "Same --id updates this block in place" --id status-note
xapps doc-import-markdown "Encyclopedia" --multi --input ./book.md --replace-pages --yes
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
| `X-XApps-Allow-File-Create` | Explicitly permit workbook creation on file create/write routes |
| `X-XApps-Workbook-Operation` | Use `move` with `X-XApps-Source-File` on workbook file rename/move writes |
| `X-XApps-Source-File` | Source workbook file for access-preserving rename/move writes |
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
| GET | `/api/workbook/assistant-threads` | Read workbook-persisted Assistant threads |
| PUT | `/api/workbook/assistant-threads` | Merge Assistant thread snapshots |
| GET | `/api/workbook/assistant-threads/:id` | Read one Assistant thread |
| PUT | `/api/workbook/assistant-threads/:id` | Upsert one Assistant thread |
| DELETE | `/api/workbook/assistant-threads/:id` | Delete one Assistant thread |
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
| POST | `/api/sheets/:name/cleanup/preview` | Preview trim whitespace, duplicate, or split-text cleanup |
| POST | `/api/sheets/:name/cleanup/apply` | Apply undo-safe data cleanup operations |
| GET/POST/PUT | `/api/sheets/:name/macros` | List, create, or replace safe Spreadsheet macros |
| GET/PUT/DELETE | `/api/sheets/:name/macros/:id` | Read, update, or delete a Spreadsheet macro |
| POST | `/api/sheets/:name/macros/:id/run` | Run a Spreadsheet macro with confirmation/protection checks and audit logging |
| GET/POST/PUT | `/api/sheets/:name/timeline-views` | List, create, or replace Spreadsheet timeline views |
| GET/PUT/DELETE | `/api/sheets/:name/timeline-views/:id` | Read, update, or delete a Spreadsheet timeline view |
| POST | `/api/sheets/:name/timeline-views/:id/preview` | Preview timeline tasks and grouped bars |
| POST | `/api/sheets/:name/timeline-views/:id/export-timeline-sheet` | Export a Spreadsheet timeline view to an xApps Timeline sheet |
| GET/PUT/DELETE | `/api/sheets/:name/cells/:ref/format` | Cell format |
| GET/PUT/DELETE | `/api/sheets/:name/cells/:ref/validation` | Cell validation |
| GET/PUT/DELETE | `/api/sheets/:name/cells/:ref/comment` | Cell comment |
| GET/PUT/DELETE | `/api/sheets/:name/cells/:ref/rich-value` | Rich cell/smart chip metadata |
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
| GET | `/api/sheets/:name/cells:batch` | Read the current revision and fingerprint before a guarded batch |
| POST | `/api/sheets/:name/cells:batch` | Apply one all-or-nothing semantic batch transaction |

### Guarded Transaction Endpoints

Some write families are **atomic and replay-safe**: they validate every
operation, persist the whole change once, and leave the sheet untouched when
anything fails. Each takes two guards — `--expected-revision`, the revision you
read immediately before writing, and `--request-id`, a stable id that makes a
retry return the original result instead of applying the change twice.

| Surface | Read the revision | Apply the change | CLI |
|---|---|---|---|
| **Spreadsheet** | `GET /api/sheets/:name/cells:batch` | `POST /api/sheets/:name/cells:batch` | `xapps spreadsheet batch-state`, `xapps spreadsheet batch` |
| **Doc pages** | `GET /api/sheets/:name/document/mutations` | `POST /api/sheets/:name/document/mutations` | `xapps doc-mutation-state`, `xapps doc-mutation-outcome` |
| **Doc comments** | `GET /api/sheets/:name/pages/:pageId/blocks/:blockId/comments` | `POST`/`PATCH`/`DELETE` on the same family | `xapps doc-list-comments`, `xapps doc-add-comment`, `xapps doc-add-comment-reply`, `xapps doc-resolve-comment` |

`GET /api/sheets/:name/document/mutations/:requestId` (`doc-mutation-outcome`)
returns the durable original result of a Doc mutation after a disconnect or a
restart, so a caller that lost the response can recover it instead of guessing.

```bash
xapps spreadsheet batch-state "Budget" --json
xapps doc-list-comments "Spec" --json
xapps doc-add-comment-reply "Spec" thread-1 "Agreed" \
  --expected-revision 4 --request-id spec-reply-1 --json
```

### Surface Endpoints

Each sheet type exposes its own sub-endpoints:

| Type | Endpoints |
|---|---|
| **Records** | `/records`, `/records/:recordId`, `/records/bulk`, `/records/deleted`, `/records/:recordId/restore`, `/fields`, `/fields/batch`, `/fields/:fieldId`, `/tables`, `/tables/:tableId`, `/views`, `/views/:viewId`, `/sql` |
| **Kanban** | `/cards`, `/cards/:rowOrId`, `/cards/:rowOrId/comments`, `/lists`, `/lists/:name`, `/lists/reorder` |
| **Calendar** | `/events`, `/events/:row`, `/scheduling-sessions`, `/scheduling-sessions/:id`, `/scheduling-sessions/:id/invitations`, `/scheduling-sessions/:id/access/:inviteeId`, `/scheduling-sessions/:id/finalize` |
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
- `records_list_tables`, `records_create_table`, `records_get_table`, `records_update_table`, `records_rename_table`, `records_delete_table`
- `records_list_fields`, `records_add_field`, `records_add_fields`, `records_update_field`, `records_delete_field`, `records_reorder_fields`
- `records_list`, `records_get`, `records_create`, `records_patch`, `records_delete`, `records_reorder`, `records_batch`, `records_bulk_update`, `records_bulk_delete`
- `records_trash`, `records_restore`, `records_duplicate`, `records_history`
- `records_comments`, `records_add_comment`, `records_edit_comment`, `records_delete_comment`
- `records_list_views`, `records_add_view`, `records_update_view`, `records_delete_view`, `records_set_active_view`, `records_get_active_view`, `records_reorder_views`
- `records_submit_form`, `records_list_queries`, `records_add_query`, `records_get_query`, `records_update_query`, `records_delete_query`, `records_get_active_query`, `records_set_active_query`
- `records_schema_dependencies`, `records_schema_health`, `records_schema_audit`, `records_schema_undo`, `records_schema_repair`
- `records_relation_preview`, `records_sql`

**Kanban Tools:**
- `list_kanban_cards`, `get_kanban_card`, `get_kanban_field_labels`, `set_kanban_field_labels`
- `create_card`, `update_card`, `transition_kanban_card`, `delete_card`
- `list_kanban_lists`, `create_kanban_list`, `rename_kanban_list`, `color_kanban_list`, `delete_kanban_list`
- `reorder_kanban_lists`, `save_kanban_view`, `apply_kanban_automation_presets`, `sync_kanban_companion_views`, `get_kanban_report`

**Calendar Tools:**
- `calendar_state`, `list_events`, `get_event`, `create_event`, `update_event`, `delete_event`, `get_settings`, `update_settings`, `import_ics`
- `list_scheduling_sessions`, `get_scheduling_session`, `create_scheduling_session`, `send_scheduling_invitations`, `revoke_scheduling_access`, `finalize_scheduling_session`

Scheduling tools are organizer-only. The public invitee token-response endpoints are deliberately excluded from service-principal tool catalogs; authorized organizer detail can still return private links for copy, rotation, and revocation.

**Timeline Tools:**
- `timeline_tasks`, `timeline_add_task`, `timeline_update_task`, `timeline_delete_task`
- `timeline_set_task_dependencies`, `timeline_clear_task_dependencies`, `timeline_set_task_milestone`, `timeline_report`

**Poll Tools:**
- `poll_config`, `poll_set_config`
- `poll_add_question`, `poll_update_question`, `poll_delete_question`, `poll_reorder_questions`
- `poll_add_option`, `poll_set_status`, `poll_submit_response`, `poll_responses`

**Canvas Tools:**
- `canvas_list_objects`, `canvas_get_object`, `canvas_update_object`
- `canvas_list_pages`, `canvas_set_page`, `canvas_set_artboard`, `canvas_mutate_page`, `canvas_mutate_layer`
- `canvas_create_shape`, `canvas_create_text`, `canvas_create_image`
- `canvas_duplicate_objects`, `canvas_delete_objects`, `canvas_group_objects`, `canvas_ungroup_objects`
- `canvas_lock_objects`, `canvas_unlock_objects`, `canvas_layout_objects`
- `canvas_add_comment`, `canvas_list_comments`, `canvas_resolve_comment`, `canvas_delete_comment`

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

### “How long are Chat messages kept?”

- Chat message retention defaults to **2 weeks** for every new or unconfigured room scope.
- In a Chat sheet, open **Preferences → Room & administration → Message retention** to choose 1 day, 1 week, 2 weeks, 30 days, 90 days, 1 year, or Forever.
- The policy applies to every Chat sheet that uses the same room scope because those sheets share one room dataset.
- Expired messages and their reactions are permanently pruned. Referenced room files are not deleted.
- If saving or pruning fails, the dialog stays open and shows a retry action; Chat does not hide the affected messages before the durable delete succeeds.

### “Do my Chat preferences and unread position follow me?”

- Sort/manual order, mute, stars, hidden channels, notification preferences, and read position update locally without waiting for storage, then roam for the authenticated room identity.
- Appearance offers both **Use room colors** and **Use my colors**. Room administrators save the shared default in **Room & administration**; a personal override affects only that identity.
- Preference edits, including notification controls, are staged until **Save**. **Cancel**, Escape, backdrop click, and close discard the draft and restore any live color preview.
- The right-side room-members pane can be collapsed from the conversation header and its state follows the identity.
- Chat coalesces changes into whole-state background saves instead of persisting every click or message delta, so preference storage does not delay sending or agent startup.
- The selected channel and selected agent model remain local to the current device/workbook.
- If roaming persistence is unavailable, Chat keeps the local state usable and retries unsaved state on a later lifecycle flush or reload.

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
