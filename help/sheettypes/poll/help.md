## Polls

### Run a live vote with mobile-first voter UX

Poll sheets turn a workbook tab into a live polling surface. The same sheet is the **author's editor** and the **voter's view** — render mode flips on URL state and lifecycle. Voters open a deep-link (`?sheet=<name>&mode=vote`) on a phone or laptop, the chrome auto-locks, and they see only the question + tap-to-vote. Authors stay in admin mode with the question editor, live results panel, and share dialog.

Polls are useful for audience Q&A, product feedback, planning votes, retrospective sentiment, town-halls, classroom checks, and anywhere you want a low-friction "everyone weigh in" moment.

> 🤖 Agent example: an agent can scaffold a poll, add a few options, mark it open, submit synthetic responses for testing, then export the CSV — all without opening the GUI.

---

### Features at a Glance

- Six question types: **single**, **multi**, **rating** (stars / NPS / numeric), **yes/no**, **text**, **ranking**
- Mobile-first voter view with auto chrome lockdown (no menubar, no sheet tabs, no `+` button)
- Lifecycle gates: `draft → open → closed`. Question structure is editable in draft only; option-add stays allowed once open
- One-vote-per-viewer with cookie dedupe for anonymous polls and `viewerId` dedupe for identified polls
- Per-IP rate limit (30 / minute, X-Forwarded-For-aware)
- "Allow edit after submit" mode replaces the prior response instead of stacking duplicates
- Live results panel in admin: bar fill, count, percentage, total responses, pulse on update
- Configurable result visibility: `always` / `after-vote` / `after-close` / `never`
- Share dialog with the deep-link voter URL, copy-to-clipboard, and open-in-new-tab
- Closed-poll view doubles as a final-results view with the same bars
- Export responses as CSV (one row per response, columns per question, option labels resolved)
- Full CLI + MCP + REST surface — every UI mutation is also scriptable
- Keyboard navigable voter view (`role="radiogroup"`, arrow keys cycle, Enter / Space submits)

---

### Getting Started

1. **Create a poll sheet.** Click the `+` button in the sheet tab bar and select **Poll**. A new poll sheet starts in `draft` status.
2. **Set the title.** Click the title field at the top and type the poll's name. Tab away or press Enter to save.
3. **Add a question.** Tap one of the type chips (Single / Multi / Rating / Yes/No / Text / Rank) at the bottom. A starter question appears.
4. **Edit the prompt and options.** Click the prompt text or any option label to rename. Click the `✕` next to an option to delete it. Use the "Add an option…" row at the bottom of the question card to append.
5. **Open the poll.** Click **Open poll** in the top bar. Question structure locks; `option-add` is still allowed for choice / multi / ranking types so you can extend during a live event without invalidating prior tallies.
6. **Share the URL.** Click **Share** in the top bar, copy the voter URL, and send it to participants.
7. **Watch results.** The live results panel below the question editor refreshes every 2 seconds while the admin pane is open.
8. **Close the poll.** Click **Close poll** in the top bar when voting is done. The voter URL flips to a final-results view with a "This poll closed" banner.

---

### Editor (admin) Layout

- **Top bar:** status pill (draft / open / closed), editable title, **Share** button, lifecycle action (Open / Close / Reopen).
- **Description:** optional textarea shown to voters above the question.
- **Questions section:** one card per question. Card has a type badge, question prompt input, options list, "Add an option" row.
- **Add-question chips:** type picker. Visible in `draft` only (server enforces structural lockout once open).
- **Live results section:** appears once the poll is `open`; shows per-question bars and an export button.

### Voter Layout

- **Hero card:** poll title + optional description.
- **Question card:** prompt at top, then type-specific affordance (option pills / star row / textarea / checkboxes).
- **Auto submit (default):** tapping an option fires the vote immediately. **Explicit submit** mode shows a Submit button and waits for confirmation.
- **After voting:** confirmation message + (if `showResults` allows) bar fill on each option.
- **Already-voted state:** picked option stays highlighted, results bars persist, second submit returns `409 already_voted` (unless `allowEditAfterSubmit` is true).
- **Closed poll:** voting is disabled; the same options are shown as final-results bars.

---

### Question Types

| Type      | Voter affordance                | Value shape                                |
|-----------|---------------------------------|--------------------------------------------|
| `single`  | Tap one option                  | `{ optionId: string }`                     |
| `multi`   | Check one or more boxes         | `{ optionIds: string[] }`                  |
| `yesno`   | Tap Yes or No                   | `{ optionId: 'yes' \| 'no' }`              |
| `rating`  | Tap a star (or NPS / number)    | `{ value: number }`                        |
| `text`    | Type into a textarea            | `{ text: string }` (≤ `textMax`)           |
| `ranking` | Drag to reorder (follow-up)     | `{ orderedOptionIds: string[] }`           |

Multi questions honor `multiMin` and `multiMax`. Rating questions honor `ratingScale.max` and `ratingScale.style` (`stars` / `nps` / `numeric`). Text questions honor `textMax`.

---

### Result Visibility

The `showResults` config controls when voters see the tally:

- `always` — visible from first paint, before the user even votes.
- `after-vote` — visible only after the voter submits (or after the poll closes).
- `after-close` — visible only after the poll closes.
- `never` — admin-only.

The server enforces visibility on `GET /tally`; non-eligible voters get `403 results_after_vote` / `403 results_after_close` / `403 results_hidden`.

---

### Sharing & Voter URL

The Share dialog builds a deep link of the form:

```
https://<host>/?sheet=<pollName>&mode=vote
```

Voters open this URL on a phone or laptop. The shell auto-detects voter mode and:

- Hides the menubar, sheet tabs, mobile bottom-bar, and `+` button.
- Mounts the voter card.
- Persists `vote_token` cookie + `localStorage` so reload keeps "already voted" state.

Voter mode is **scoped to the targeted sheet name** — switching to or creating another poll sheet won't lock the chrome on the new one.

---

### Edit-Vote (Allow Edit After Submit)

Set `pollConfig.allowEditAfterSubmit = true` to let voters change their pick. The voted state shows a "Change my vote" link; clicking it clears local state. On re-submit, the server **replaces** the prior response (matched by `vote_token` cookie or `viewerId`) so the tally stays correct instead of double-counting. The response payload reports `replacedPriorId`.

---

### Command Line Interface

Every UI operation is also a CLI command. The `poll` group has 10 commands:

```bash
xapps poll-config <sheet> [--json]
xapps set-poll-config <sheet> <json>
xapps add-question <sheet> --type <single|multi|rating|yesno|text|ranking> --prompt <text> [--required] [--option <label> ...] [--rating-max <n>] [--rating-style <stars|nps|numeric>]
xapps update-question <sheet> <questionId> <json>
xapps delete-question <sheet> <questionId>
xapps reorder-questions <sheet> <json-array-of-question-ids>
xapps add-option <sheet> <questionId> <label> [--color <hex>] [--image <url>]
xapps set-poll-status <sheet> <draft|open|closed>
xapps submit-response <sheet> <answers-json> [--viewer <id>] [--name <name>]
xapps poll-responses <sheet> [--json]
```

Quick scripted poll:

```bash
xapps create-sheet "Lunch" --type poll
xapps set-poll-config Lunch '{"title":"Where for lunch?","showResults":"always"}'
xapps add-question Lunch --type single --prompt "Pick one" --required \
  --option "Tacos" --option "Pizza" --option "Salad"
xapps set-poll-status Lunch open
xapps submit-response Lunch '[{"questionId":"q-1","value":{"optionId":"opt-tacos"}}]'
xapps poll-responses Lunch
```

Run `xapps help poll <command>` for per-command flags.

---

### MCP

The MCP surface mirrors the CLI 1:1: `poll_config`, `poll_set_config`, `poll_add_question`, `poll_update_question`, `poll_delete_question`, `poll_reorder_questions`, `poll_add_option`, `poll_set_status`, `poll_submit_response`, `poll_responses`. Useful for agent flows that build out a poll from a brief, run a synthetic vote, or scrape live tallies.

---

### REST API

All admin and voter operations route through `/api/sheets/<poll>/*`:

| Route                                                           | Method  | Purpose                                                            |
|-----------------------------------------------------------------|---------|--------------------------------------------------------------------|
| `/api/sheets/<poll>/config`                                     | GET/PUT | Read or patch `pollConfig` + question summary                      |
| `/api/sheets/<poll>/status`                                     | POST    | Lifecycle transition                                               |
| `/api/sheets/<poll>/questions`                                  | GET/POST| List / add a question                                              |
| `/api/sheets/<poll>/questions/<id>`                             | PUT/DELETE | Patch / delete a question                                       |
| `/api/sheets/<poll>/questions/reorder`                          | POST    | Replace question order                                             |
| `/api/sheets/<poll>/questions/<id>/options`                     | POST    | Append an option (allowed on open polls)                           |
| `/api/sheets/<poll>/questions/<id>/options/<oid>`               | PUT/DELETE | Patch / delete an option (delete is draft-only)                 |
| `/api/sheets/<poll>/responses`                                  | GET/POST| Admin readback / submit a vote                                     |
| `/api/sheets/<poll>/tally`                                      | GET     | Aggregate option counts (gated by `showResults`)                   |

POSTing a response is rate-limited (30 / minute / IP) and dedupes on cookie or `viewerId` (when `oneVotePerViewer` is on).

---

### Anonymous vs. Identified Polls

- **Anonymous (default):** the persisted `PollResponse` has no `viewerId` or `displayName`. Dedupe uses an HttpOnly `xapps_poll_vote_<pollDocId>` cookie. The cookie is best-effort, not a security boundary.
- **Identified:** the client sends `viewerId` (and optional `displayName`) in the POST body. Dedupe and edit-replace match on `viewerId`. Anonymous polls strip `viewerId` from the persisted response even if the client tries to send one (defense-in-depth).

---

### Lifecycle Rules

- `draft → open` requires at least one question.
- `open → closed` stamps `pollConfig.closesAt`.
- `closed → open` (reopen) clears `closesAt` and preserves prior responses.
- Same-state transitions are rejected with `409`.
- On `open`: question add / type change / question delete / option delete are blocked. Option add and cosmetic-only patches (prompt, required, color) stay allowed so authors can extend during a live event.
- On `closed`: all mutations are blocked. POST `/responses` returns `410 poll_closed`.

---

### Save / Load — workspace-level poll library

Polls are reusable. The admin top bar has **Save** and **Load** buttons backed by a workspace-level library at `<workbookFilesRootDir>/polls/<slug>/`:

```
polls/
  Lunch-survey/
    template.json          ← config + questions (the reusable shape)
    runs/
      2026-04-01...json    ← responses from run 1
      2026-05-03...json    ← responses from run 2
      ...
```

Each library entry has two parts:

- **Template** — config + questions, no responses. The shape you re-use across runs.
- **Runs** — responses captured at a moment in time (typically when the poll closed). Saved as separate timestamped files so each run of the same poll keeps its own results.

The admin UI flow:

- **Save** opens a dialog with a name input. Click **Save template** to push the current config + questions to the library. If the poll has responses, a second button **Save this run too** appears — it saves the template AND archives the current responses as a run record.
- **Load** opens a picker dialog listing every template in the library with its saved-at timestamp and run count. Click **Load** to swap the picked template into the current sheet (status forced to draft, fresh `pollDocId` minted, responses cleared on the sheet but preserved in the library).
- **Delete** removes a template and all its runs (irreversible — guarded with a confirm).

Library is independent of any workbook — same workspace host, same library, regardless of which workbook is open. So you can save a "Town Hall Q&A" template from one workbook and load it into a fresh poll sheet in a different workbook the next quarter.

#### Library REST API

| Route                                          | Method  | Purpose                                  |
|------------------------------------------------|---------|------------------------------------------|
| `/api/polls`                                   | GET     | List templates `[{ name, title, savedAt, runCount, lastRunAt }]` |
| `/api/polls/<name>`                            | GET     | Fetch template + run summary             |
| `/api/polls/<name>`                            | POST    | Save template (body: poll snapshot)      |
| `/api/polls/<name>`                            | DELETE  | Remove template + all its runs           |
| `/api/polls/<name>/runs`                       | GET     | List runs for a template                 |
| `/api/polls/<name>/runs/<runId>`               | GET     | Fetch a single run's responses + tally   |
| `/api/polls/<name>/runs`                       | POST    | Archive the current sheet's responses as a new run |
| `/api/polls/<name>/runs/<runId>`               | DELETE  | Delete a single run                      |
| `/api/sheets/<poll>/load-from/<name>`          | POST    | Replace the sheet's state from the named template |

Names are slugified (letters / digits / underscore stay; everything else collapses to a dash). Saving "Lunch survey" creates `polls/Lunch-survey/`.

---

### Live Results Transport

The admin live-results panel uses two channels:

- **Server-sent events (SSE)** — `GET /api/sheets/<poll>/events` streams a `tally-update` event every time `/responses` accepts a vote, for sub-second updates without polling.
- **Polling fallback** — every 6 seconds the admin re-fetches `/tally`. This catches a single dropped SSE event and keeps the panel honest if the EventSource connection ever stalls behind a proxy.

You don't need to do anything to enable either; the admin pane wires both up automatically when the poll is `open`.

---

### Cross-Surface: Kanban "on close → add card"

`pollConfig.onClose` carries an optional automation hint:

```json
{
  "onClose": {
    "kanbanBoardSheet": "Tasks",
    "kanbanList": "Follow-up",
    "kanbanCardTitle": "Review Q1 town-hall results"
  }
}
```

When the poll transitions `open → closed`, the server returns a `pendingAutomation` payload on the close response; the admin client fires the kanban POST with the configured title (or a default `Follow up on poll: <title>`) into the named board. Decoupled by design — no server-side cross-surface dependency.

---

### Known Follow-Ups

- **Yjs transport for live results.** SSE works today, but a dedicated `shared-y-updates:poll:<pollDocId>` Y.Array channel for response appends is the long-term shape (matches the typewriter precedent, scales further).
- **Multi-question stepped voter flow.** Already implemented — Phase 5 ships progress dots, Next/Back, and a Review screen.
- **Voter ranking UI.** Already implemented — drag-reorder voter UI + Borda-score aggregation in `/tally`.
- **Cross-surface integrations.** Kanban-on-close ships. Doc / typewriter live-embed of the results panel + dashboard widget for poll responses are still open.
- **`browser-vote.ts` file split.** The voter file passed the 900-line guardrail and is currently whitelisted; splitting into single-question / stepped / ranking modules is a follow-up cleanup.
