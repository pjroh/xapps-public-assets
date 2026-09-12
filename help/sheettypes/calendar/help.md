## Calendar

### Choose the right calendar workflow

Use an ordinary event when you already know the time. Use **Find a time** when people need to compare availability first. Google Calendar sync is a separate connection: collecting manual availability does not inspect anyone's calendar or connect a Google account.

### Find a time together

1. Open a saved Calendar sheet and click **Find a time** in its toolbar. If requests already exist, this opens **Availability requests**; create another request from that manager.
2. Give the request a recognizable title, choose the date range, weekdays, daily time window, meeting duration, and time zone. The candidate count helps you avoid asking people to review an unnecessarily large grid.
3. Leave invitees empty to share one open link, or list names and email addresses for individual links. Review the delivery result: a generated link is not evidence that an email arrived.
4. Create the request and copy its link. People opening an open link can inspect the group view first, then choose their own availability, enter their name, and click or drag across times. Wait for **Availability saved** before leaving. Unmarked times are not available responses.
5. Return to **Find a time** to see reply counts, pending people, **Best options**, and the availability heatmap. A high-ranking option is a comparison of responses, not a booking. Review who is still pending before choosing it.
6. Select an option and click **Schedule meeting**. Review **Schedule this meeting?**, then confirm. The request closes and one local Calendar event is created. Download its `.ics` file or use **Open Meeting** for the project call.

Finalizing does **not** send a provider calendar invitation. Share the confirmed time or calendar file deliberately. If email is unavailable, use the visible copy-link fallback; reminders do not become delivered merely because they were requested. Revoking an individual response link removes that link's access.

### Respond to an availability request

![Open availability link showing the group view before a visitor enters their name](/help-assets/screenshots/calendar-availability-group.png)

The **Everyone** tab shows the group's current answers. Switch to **Your times**, enter your name, and choose **Available** or **If need be** before marking the grid. Drag over marked times again to clear them. The time-zone selector controls the times you see; read it before comparing the request with your own schedule.

![Your times with a named respondent, painted times, and the Availability saved confirmation](/help-assets/screenshots/calendar-availability-response.png)

Wait for the saved confirmation, then reopen the same link to make changes. An open link admits new respondents; it is not a private invitation to just one named person.

![Everyone view showing an overlapping time after two people submitted their answers](/help-assets/screenshots/calendar-availability-overlap.png)

The count in a time slot describes submitted availability. “Everyone who replied can make it” is different from “everyone invited has replied.” Check pending people in the organizer view.

### Compare responses and confirm the meeting

![Organizer Availability requests with Best options, a heatmap, and three of four replies](/help-assets/screenshots/calendar-scheduling-organizer-results.png)

**Best options** ranks the returned answers; **Everyone available** narrows the candidates. Selecting a time highlights a choice without booking it. This example also shows the honest local-host state **Email delivery is not configured**—the availability grid still works through shared links.

![Availability organizer scrolled to People and per-person invitation controls](/help-assets/screenshots/calendar-scheduling-invitation-management.png)

Use the People section to distinguish responded and pending invitees, copy a private link, request a reminder, or revoke access. Review the displayed delivery status after each action.

![Schedule this meeting confirmation explaining creation of a local event](/help-assets/screenshots/calendar-scheduling-finalization-confirm.png)

![Finalized availability request with Meeting scheduled and calendar download actions](/help-assets/screenshots/calendar-scheduling-finalized.png)

Confirmation creates the local event once and changes the request to **Scheduled**. The `.ics` download and Meeting-sheet handoff help carry the decision into the rest of the project.

### Schedule work visually

Calendar sheets give you **Month**, **Week**, and **Day** views for events, deadlines, editorial schedules, launches, and personal planning. Events are color-coded, support optional times, and can be imported from standard ICS calendar files.

Like all xApps sheet types, calendar data is stored as cells, so spreadsheet formulas can query and summarize your calendar from other sheets.

> 🤖 Agent example: an agent can turn roadmap milestones into calendar events, clean up imported ICS noise, and generate a weekly digest while a human reviews the actual schedule visually.

![Calendar sheet showing May 2026 month view with color-coded events including standups, launches, and reviews](/help-assets/screenshots/calendar-sheet.png)

---

### Features at a Glance

- Three views: Month, Week, and Day
- Events with title, date, optional time, description, and color
- Color-coded events with preset palette
- Double-click any date/time slot to create an event
- Click events to edit in a modal editor
- Context menu for quick add, edit, and delete
- Navigation: previous/next, jump to Today; view state persists across sessions
- ICS calendar import (Google Calendar, Apple Calendar, Outlook)
- Google Calendar overlay -- view and write-back to your personal Google calendars
- Menu-driven view switching with keyboard shortcuts
- Display preferences: locale, time zone, 12/24-hour clock, week start day
- Cross-sheet formula integration
- Undo/redo support
- CLI and API for full programmatic control
- Manual availability requests shared by one open link or private per-person email links, drag-to-paint response grid, ranked best contiguous meeting windows, reminders, revocation, and finalization

---

### Getting Started

1. **Create a calendar sheet.** Click the `+` button in the sheet tab bar and select "Calendar." The calendar opens in Month view showing the current month.
2. **Add an event.** Double-click any date cell (in Month view) or any hour slot (in Week/Day view). Fill in the title, date, time, description, and pick a color.
3. **Edit an event.** Click on an existing event to open the editor. Change any field and click Save.
4. **Switch views.** Use the Month / Week / Day buttons in the calendar header, or the View menu.
5. **Navigate.** Use the left/right arrows to move forward/back by month, week, or day. Click "Today" to jump to the current date.
6. **Import events.** Use Surface > Import calendar (.ics) to import an ICS file, or use the CLI `import-ics` command.

---

### Views

#### Month View

Displays a 6-week grid (42 days) centered on the current month. Each day cell shows:
- The day number (greyed out for days outside the current month)
- All events for that day, color-coded, with optional time prefix
- "Today" is highlighted with a colored circle

Double-click any day cell to create an event on that date.

![Week view showing Daily Standup, Sprint Planning, and 1:1 events in May 2026](/help-assets/screenshots/calendar-week-events.png)

#### Week View

Displays a 7-day column layout with a 24-hour time gutter on the left. Each column shows:
- The day name and date in the header ("Today" is highlighted)
- Hour slots from 12:00 AM to 11:00 PM
- Events placed in their corresponding hour slot
- All-day events (no time set) appear at the top (12:00 AM row)

Double-click any hour slot to create an event at that date and time. Multiple events in the same hour slot stack vertically.

#### Day View

Displays a single day with the same 24-hour layout as Week view but using the full width. Useful for detailed daily planning with many time-specific events.

![Day view showing May 14 with the Marketing Campaign Launch at 9:00 AM](/help-assets/screenshots/calendar-day-view.png)

---

### Event Properties

Each event stores the following fields:

| Field | Column | Description |
|---|---|---|
| Title | A (col 0) | Event name (required) |
| Date | B (col 1) | Date in YYYY-MM-DD format (required) |
| Time | C (col 2) | Time in HH:MM format (optional) |
| Description | D (col 3) | Longer text description |
| Color | E (col 4) | Hex color code for the event chip |
| Stable ID | F (col 5) | Durable event identity; agents should prefer this over a row number |
| All day | G (col 6) | Explicit all-day flag |
| Time zone | H (col 7) | IANA time zone or `UTC` for timed imported events |
| Source UID | I (col 8) | Stable external identity, including ICS `UID` |
| End date | J (col 9) | Optional inclusive timed end or exclusive all-day end date |
| End time | K (col 10) | Optional end time in HH:MM form |

Events without a time are treated as all-day events and appear at the top of the day in Week/Day views.

---

### Event Editor

Click an event or double-click an empty date/time slot to open the editor:

- **Title** -- required text field
- **Date** -- date picker (pre-filled from the clicked date)
- **Time** -- time picker (pre-filled from the clicked hour slot in Week/Day view)
- **Description** -- multi-line text area
- **Color** -- visual color swatch picker with preset palette colors
- **Delete** button (existing events only)
- **Cancel** / **Save** buttons

![Event editor showing Daily Standup with title, date, time, description and color picker](/help-assets/screenshots/calendar-event-editor.png)

---

### Event Colors

Events use a preset color palette. Select a color in the event editor by clicking a swatch. Colors render as the background of the event chip in all views.

---

### Context Menu

Right-click on different areas for context-sensitive actions:

| Target | Actions |
|---|---|
| An event | "Edit event", "Delete event" |
| An empty day/slot | "Add event here" (pre-fills the date and time) |
| Empty calendar area | "Add event" |

---

### Navigation

| Control | Action |
|---|---|
| Left arrow button | Previous month / week / day |
| Right arrow button | Next month / week / day |
| "Today" button | Jump to current date |
| Month / Week / Day buttons | Switch view |

Navigation adjusts based on the current view:
- In Month view, arrows move by one month
- In Week view, arrows move by one week
- In Day view, arrows move by one day

---

### ICS Import

Import events from standard ICS calendar files exported from Google Calendar, Apple Calendar, Outlook, or any CalDAV-compatible service.

**From the UI:** Surface menu > Import calendar (.ics), then select a `.ics` file.

**From the CLI:**
```bash
xapps import-ics "My Calendar" /path/to/export.ics
# Output: Imported 47 events into My Calendar
```

The importer accepts `VEVENT` entries with required `SUMMARY` and `DTSTART`, plus optional `UID`, `DESCRIPTION`, CSS-hex `COLOR`, `DTEND`, or a week/day/hour/minute `DURATION`. `DATE`, floating `DATE-TIME`, UTC (`Z`), and `TZID` values are preserved at Calendar's minute precision. Re-importing the same `UID` updates the existing stable event instead of duplicating it. Recurrence fields (`RRULE`, `RDATE`, `RECURRENCE-ID`, and `EXDATE`), second-precision durations, invalid dates/times, duplicate UIDs, and mixed valid/invalid batches are rejected atomically.

### Local API concurrency contract

Read `GET /api/sheets/{name}/state` before a local write. Event create/update/delete, settings updates, and ICS import require `requestId` plus `expectedRevision`; `expectedFingerprint` may also be supplied. Reusing the same request id and identical body safely replays the prior result, while stale revisions or changed request intent return a structured `409` error. Failed persistence returns `calendar_persistence_failed` and restores the exact pre-write state. Mutation receipts are stored on the sheet and bounded to the latest 50 requests.

Hosted and legacy service-principal agent tools intentionally cover local workbook Calendar operations only. Viewer-private Google Calendar operations require a delegated human principal and are not exposed to those toolkits.

### Automation contract: API -> SDK -> agents

1. **Public API.** Read `GET /api/sheets/{name}/state`; use guarded `/events`, `/settings`, `/ics`, and organizer `/scheduling-sessions` routes published in generated OpenAPI. Invitee token-response routes are intentionally absent from service-principal surfaces. The private Google service family under `/api/services/google-calendar/*` additionally requires a human principal and saved-workbook scope.
2. **Typed SDK.** `client.calendar` owns local state, query, CRUD, settings, ICS, organizer scheduling, and saved-workbook destination methods. `client.calendar.google` owns the closed human-principal Google lifecycle/source/mode/sync/event contract.
3. **SDK-backed agents.** Calendar CLI and MCP/toolkit operations delegate local workbook behavior to `client.calendar`; they do not reconstruct routes, receive invitee response tokens, or receive private Google grants.

### Google Calendar Sync

When the host is configured with Google OAuth, calendar sheets show a Google Calendar mode selector bar at the top with three options:

| Mode | Button | Behavior |
|---|---|---|
| **Local only** | "Local only" | Shows only workbook events; Google sync disabled |
| **Local + Google** | "Local + Google" | Overlays your Google calendars on top of workbook events |
| **Google only** | "Google only" | Shows only your Google calendars (primary mode) |

In **Local + Google** and **Google only** modes, the calendar makes live read requests to Google Calendar for the currently signed-in viewer. Each viewer connects their own Google account, so Alice sees Alice's calendars and Bob sees Bob's calendars in the same shared workbook.

**Write-back:** In Google primary mode (`Google only`), creating, updating, or deleting events writes directly to the signed-in viewer's Google Calendar. In overlay mode, new events can be directed to Google or kept local using a per-event destination picker in the event editor.

**Connecting Google:** Click the "Connect Google" button in the sync bar to begin the OAuth flow. If access is revoked or needs renewal, the same control becomes **Reconnect Google**. After authorization, your Google calendars appear as an overlay. The connection, private calendar selection, account profile, and provider event links are per-viewer and remain outside workbook JSON.

**Disconnecting:** A connected sheet shows a secondary **Disconnect** action. It opens an in-page confirmation; confirming removes Calendar access and private Calendar metadata for the current viewer, preserves other Google features such as Drive, and returns the sheet to Local only mode. Cancel, Escape, and clicking outside the dialog leave the connection unchanged.

In deployments with the selected MeshAgent secrets-v2 backend, Calendar obtains access only through the server-owned Google grant runtime. The browser never receives a refresh token, and OAuth tokens, connected email, provider-derived preferences, private sources, and private event links are not workbook fields. Legacy encrypted-file credentials remain available only when the host is explicitly running without the selected v2 runtime.

---

### Display Preferences

Calendar separates durable shared state from viewer-private display state. `calendarView` and `calendarDate` are guarded workbook settings exposed through API, SDK, CLI, and tools. Explicit non-Google display fields can also live on the sheet, while absent values derive from the current browser. Google-derived profile, locale, time zone, clock/week-start preferences, source selection, and provider links are per-viewer private state and are scrubbed from workbook/Yjs persistence.

| Preference | Sheet field | Default |
|---|---|---|
| Locale | `calendarLocale` | Browser locale (e.g. `en-US`) |
| Time zone | `calendarTimeZone` | Browser time zone (e.g. `America/New_York`) |
| 12/24-hour clock | `calendarUse24HourClock` | Derived from locale |
| Week starts on | `calendarWeekStartsOn` | Derived from locale (0=Sun, 1=Mon) |

If no preferences are set, the calendar derives sensible defaults from the viewer's browser locale and time zone automatically. US/CA/JP/PH locales default to week-starting Sunday; most others default to Monday.

---

### Cross-Sheet Formula Integration

Calendar data is stored in standard cells, so spreadsheet formulas can reference it:

```text
=COUNTIF('Launch Calendar'!A:A, "Launch")
=COUNTIF('Editorial Calendar'!B:B, "2026-04-15")
=COUNTA('Team Calendar'!A:A)
```

Use this to:
- Count events by type or keyword
- Build dashboards showing upcoming deadlines
- Compare calendar data with kanban boards or timelines

---

### Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl/Cmd` + `Z` | Undo last action |
| `Ctrl/Cmd` + `Y` | Redo |

Most calendar interactions are mouse-driven (click, double-click, right-click, navigation buttons).

---

### CLI Commands

All commands use the pattern:
```
xapps <command> --file <WorkbookName>
```

#### List Events

```bash
xapps events "Team Calendar"
# Output:
#   #0 2026-04-10 09:00 - Sprint planning
#   #1 2026-04-11 - Design review
#   #2 2026-04-15 14:30 - Product launch

# Filter by date range:
xapps events "Team Calendar" --from 2026-04-10 --to 2026-04-15

# Exact filter, text search, stable sort, and pagination:
xapps events "Team Calendar" --filter '{"color":"#1a73e8"}' --search sprint --sort date --order asc --limit 20 --offset 0

# Read one event by stable id or row:
xapps get-event "Team Calendar" LAUNCH-1
```

#### Add an Event

```bash
xapps add-event "Team Calendar" "Sprint planning" --date 2026-04-10 --time 09:00 --desc "Backlog grooming + sprint goals" --color "#1a73e8"
# Output: Event created (row 0)

# With a custom ID:
xapps add-event "Team Calendar" "Product launch" --date 2026-04-15 --time 14:30 --id LAUNCH-1
# Output: Event created (row 1, id=LAUNCH-1)

# All-day event with an explicit display time zone:
xapps add-event "Team Calendar" "Company holiday" --date 2026-04-20 --all-day --time-zone Pacific/Honolulu
# Output: Event created (row 2)
```

#### Update an Event

```bash
xapps update-event "Team Calendar" 0 '{"title":"Sprint planning (updated)","time":"10:00"}'
# Output: Event 0 updated

# Update by custom ID:
xapps update-event "Team Calendar" LAUNCH-1 '{"date":"2026-04-16","description":"Moved to Thursday"}'
# Output: Event LAUNCH-1 updated (id=LAUNCH-1)
```

#### Delete an Event

```bash
xapps delete-event "Team Calendar" 0
# Output: Event 0 deleted

xapps delete-event "Team Calendar" LAUNCH-1
# Output: Event LAUNCH-1 deleted (id=LAUNCH-1)

# Verification succeeds only after a 404 read-back; auth, server, and network failures remain errors:
xapps delete-event "Team Calendar" LAUNCH-1 --verify
```

#### Calendar Settings

```bash
xapps calendar-settings "Team Calendar"
xapps set-calendar-settings "Team Calendar" '{"calendarView":"week","calendarDate":"2026-04-20"}' --verify
```

#### Import ICS

```bash
xapps import-ics "Team Calendar" /path/to/google-calendar.ics
# Output: Imported 47 events into Team Calendar
```

#### Manual Availability Coordination

```bash
# The JSON includes title, startDate/endDate, dayStart/dayEnd, durationMinutes,
# timeZone, weekdays, invitees, and optionally deliverInvitations.
# invitees may be empty: the request is then shared by link alone and people
# add themselves by name. allowOpenResponses defaults to true.
xapps create-scheduling-session "Team Calendar" '{"title":"Board meeting","startDate":"2026-07-20","endDate":"2026-07-31","dayStart":"08:00","dayEnd":"18:00","durationMinutes":60,"timeZone":"America/Los_Angeles","weekdays":[1,2,3,4,5],"invitees":[],"allowOpenResponses":true}' --verify
xapps scheduling-sessions "Team Calendar"
xapps scheduling-session "Team Calendar" schedule-123
xapps send-scheduling-invitations "Team Calendar" schedule-123 --kind reminder --invitee-ids '["invitee-123"]' --rotate --verify
xapps revoke-scheduling-access "Team Calendar" schedule-123 invitee-123 --verify
xapps finalize-scheduling-session "Team Calendar" schedule-123 slot-2026-07-20-0900 --verify
```

These are organizer operations. People respond manually — either from the one shared link anyone can open, or from a private per-person link emailed to invitees the organizer listed. No shared or connected calendar is required, and nobody needs an account.

On the response page each person drags across a day-by-time grid to mark when they are free; anything left blank counts as unavailable. A third "if need be" state is available alongside "available". Whoever opens the shared link picks a name, and that name is bound to a secret on first use so a later visitor cannot overwrite their answers. Organizer detail may include private links so an authorized organizer can copy or rotate them, but the invitee token-response endpoints themselves are not exposed as SDK, CLI, MCP, toolkit, or generated OpenAPI operations.

Every local mutation accepts `--request-id`, `--expected-revision`, and optional `--expected-fingerprint`. Supplying no guard makes the CLI read current Calendar state and create a fresh request id. Mutation output preserves SDK revision, receipt, and replay metadata. ICS import is one atomic guarded mutation.

---

### API Endpoints

```bash
# List all events
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/events

# List events in a date range
curl -H 'X-XApps-File: MyWorkbook.json' "$XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/events?from=2026-04-01&to=2026-04-30"

# Read the guard used by every local mutation
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/state

# Create an event (use the revision/fingerprint returned above)
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/events \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"requestId":"calendar-create-1","expectedRevision":0,"title":"Sprint planning","date":"2026-04-10","time":"09:00","description":"Backlog grooming","color":"#1a73e8"}'

# Update an event (by row number)
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/events/0 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"requestId":"calendar-update-1","expectedRevision":1,"title":"Sprint planning (moved)","time":"10:00"}'

# Update by custom ID
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/events/LAUNCH-1 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"requestId":"calendar-update-launch-1","expectedRevision":2,"date":"2026-04-16"}'

# Delete an event
curl -X DELETE $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/events/0 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"requestId":"calendar-delete-1","expectedRevision":3}'

# Import ICS file content
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/ics \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"requestId":"calendar-ics-1","expectedRevision":4,"ics":"BEGIN:VCALENDAR\nBEGIN:VEVENT\nSUMMARY:Test\nDTSTART:20260410T090000\nEND:VEVENT\nEND:VCALENDAR"}'

# Organizer scheduling routes
# GET/POST /api/sheets/Team%20Calendar/scheduling-sessions
# GET      /api/sheets/Team%20Calendar/scheduling-sessions/{sessionId}
# POST     /api/sheets/Team%20Calendar/scheduling-sessions/{sessionId}/invitations
# DELETE   /api/sheets/Team%20Calendar/scheduling-sessions/{sessionId}/access/{inviteeId}
# POST     /api/sheets/Team%20Calendar/scheduling-sessions/{sessionId}/finalize
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

#### Add an authorized milestone

```bash
xapps_scoped calendar-settings "Release Calendar" --json > release-calendar-before.json
CALENDAR_REVISION=$(jq -er '.revision' release-calendar-before.json)
CALENDAR_FINGERPRINT=$(jq -er '.fingerprint' release-calendar-before.json)
xapps_scoped add-event "Release Calendar" "Alpha release" --date 2026-09-15 --id ALPHA \
  --expected-revision "$CALENDAR_REVISION" --expected-fingerprint "$CALENDAR_FINGERPRINT" \
  --request-id release-alpha-1 --verify --json > release-alpha-receipt.json
xapps_scoped events "Release Calendar" --from 2026-09-15 --to 2026-09-15 --json
```

For another milestone, read `calendar-settings` again or use the immediately verified canonical result when no other writer could intervene; assign a new request ID to that distinct event. Do not share one stale guard across several creates.

#### Import an authorized ICS file

```bash
xapps_scoped calendar-settings "Imported Cal" --json > imported-calendar-before.json
CALENDAR_REVISION=$(jq -er '.revision' imported-calendar-before.json)
CALENDAR_FINGERPRINT=$(jq -er '.fingerprint' imported-calendar-before.json)
xapps_scoped import-ics "Imported Cal" ./google-export.ics \
  --expected-revision "$CALENDAR_REVISION" --expected-fingerprint "$CALENDAR_FINGERPRINT" \
  --request-id calendar-import-1 --verify --json > calendar-import-receipt.json
xapps_scoped events "Imported Cal" --from 2026-09-01 --to 2026-09-30 --limit 50 --json
```

Preserve the exact ICS bytes together with the original guard for a lost-response retry. `events` returns event records; acquire the revision and fingerprint from `calendar-settings`, not from that list.

#### Remove one obsolete event only when removal is authorized

First identify the actual stable event ID from a bounded `events` read and set `EVENT_ID`. Import does not itself authorize deleting historical events.

```bash
xapps_scoped calendar-settings "Imported Cal" --json > calendar-delete-before.json
CALENDAR_REVISION=$(jq -er '.revision' calendar-delete-before.json)
CALENDAR_FINGERPRINT=$(jq -er '.fingerprint' calendar-delete-before.json)
xapps_scoped delete-event "Imported Cal" "$EVENT_ID" \
  --expected-revision "$CALENDAR_REVISION" --expected-fingerprint "$CALENDAR_FINGERPRINT" \
  --request-id remove-obsolete-event-1 --verify --json > calendar-delete-receipt.json
xapps_scoped calendar-settings "Imported Cal" --json
```

For a weekly digest, query a bounded date range and draft the summary. Sending email or a Chat message requires that delivery authorization separately from calendar read access.

Keep every prepared payload, revision, request ID and receipt until verification completes. After uncertain delivery, retry the identical mutation with its original guard; do not rerun the preparation steps with a fresh revision. On `409`, reread, reconcile and create a new ID only for a newly decided intent. Read commands can run independently; writes against shared state run sequentially or as one atomic batch.

### Troubleshooting

**1. Event not showing on the calendar**
Both title (column A) and date (column B) are required. If either is empty, the event is invisible. Verify the date is in YYYY-MM-DD format (e.g., `2026-04-15`, not `04/15/2026`).

**2. Event appears on the wrong day**
Dates must be in ISO format: `YYYY-MM-DD`. Other formats may be parsed incorrectly or not at all. Check the value in column B with `xapps get "Calendar" B1`.

**3. Time not displaying in Month view**
Month view shows the event title and time inline on the day cell. If the cell is too narrow, the time may be truncated. Switch to Week view for full time visibility.

**4. All-day events in Week/Day view**
Events without a time value appear in the hour-0 slot (midnight row). This is by design -- they are treated as all-day events pinned to the top of the day column.

**5. ICS import shows 0 events**
The ICS file must contain valid VEVENT entries with at least a SUMMARY and DTSTART field. Check that the file is a valid iCalendar format. Some ICS exports may use VTODO or VJOURNAL entries which are not imported.

**6. Events overlap in Week view**
Multiple events at the same hour are stacked vertically within the hour slot. There is no side-by-side layout for overlapping events currently.

**7. Color not applying**
Ensure the color is a valid hex code (e.g., `#1a73e8`). If no color is specified, the first color in the preset palette is used as the default.

---

### Tips and Tricks

- **Quick event creation:** Double-click directly on a day (Month view) or hour slot (Week/Day view) to pre-fill the date and time automatically.
- **Context menu:** Right-click a day or hour slot for "Add event here" to skip navigating to the editor.
- **Color coding:** Use consistent colors for event categories (e.g., blue for meetings, green for launches, orange for deadlines) to make the calendar scannable at a glance.
- **ICS as a bridge:** Export from Google Calendar or Outlook as ICS, then import into xApps to get a snapshot of your external calendar alongside workbook data.
- **Formula-powered reports:** On a spreadsheet sheet, use `=COUNTIF('Calendar'!B:B, "2026-04-15")` to count events on a specific date, or `=COUNTA('Calendar'!A:A)` to count total events.
- **Use alongside other sheets:** Pair calendars with Kanban boards for sprint planning (dates on the calendar, tasks on the board) or with Timelines for long-range Gantt-style views.
- **Custom IDs for stability:** When creating events via CLI or API, use the `--id` flag to assign stable identifiers that survive row reordering.
