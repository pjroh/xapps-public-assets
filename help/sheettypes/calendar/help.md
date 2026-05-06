## Calendar

### Schedule work visually

Calendar sheets give you **Month**, **Week**, and **Day** views for events, deadlines, editorial schedules, launches, and personal planning. Events are color-coded, support optional times, and can be imported from standard ICS calendar files.

Like all xApps sheet types, calendar data is stored as cells, so spreadsheet formulas can query and summarize your calendar from other sheets.

> 🤖 Agent example: an agent can turn roadmap milestones into calendar events, clean up imported ICS noise, and generate a weekly digest while a human reviews the actual schedule visually.

![Calendar sheet showing a month view with launch events and color-coded planning windows](/help-assets/screenshots/calendar-sheet.png)

---

### Features at a Glance

- Three views: Month, Week, and Day
- Events with title, date, optional time, description, and color
- Color-coded events with preset palette
- Double-click any date/time slot to create an event
- Click events to edit
- Context menu for quick add, edit, and delete
- Navigation: previous/next, jump to Today
- ICS calendar import (Google Calendar, Apple Calendar, Outlook)
- Menu-driven view switching
- Cross-sheet formula integration
- Undo/redo support
- CLI and API for full programmatic control

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
- All events for that day, color-coded, with optional time
- "Today" is highlighted

Double-click any day cell to create an event on that date.

#### Week View

Displays a 7-day column layout with a 24-hour time gutter on the left. Each column shows:
- The day name and date in the header ("Today" is highlighted)
- Hour slots from 00:00 to 23:00
- Events placed in their corresponding hour slot
- All-day events (no time set) appear at the top (hour 0)

Double-click any hour slot to create an event at that date and time.

#### Day View

Displays a single day with the same 24-hour layout as Week view but using the full width. Useful for detailed daily planning with many time-specific events.

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

The importer parses VEVENT entries and creates one row per event with title, date, time, and description mapped to the standard columns.

### Google Calendar Sync

When the host is configured with Google OAuth, calendar sheets can show a per-viewer Google Calendar overlay and write events back to the signed-in viewer's Google account. Shared workbook data stays in the workbook; Google sessions, private source selections, and Google event links are stored outside workbook JSON and keyed by the current viewer identity.

For deployed MeshAgent rooms, store the Google OAuth client values as room secrets for the xApps service identity: `xapps-google-client-id` and `xapps-google-client-secret`. Public MeshAgent URLs automatically read those credentials and store each viewer's Google session in room secrets when a MeshAgent room connection is available; localhost keeps using local OAuth env values plus the encrypted local token file. Each viewer still completes their own Google OAuth connection, so Alice sees Alice's calendars and Bob sees Bob's calendars in the same workbook.

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
# Output:
#   #0 2026-04-10 09:00 - Sprint planning
#   #1 2026-04-11 - Design review
#   #2 2026-04-15 14:30 - Product launch
```

#### Add an Event

```bash
xapps add-event "Team Calendar" "Sprint planning" --date 2026-04-10 --time 09:00 --desc "Backlog grooming + sprint goals" --color "#1a73e8"
# Output: Event created (row 0)

# With a custom ID:
xapps add-event "Team Calendar" "Product launch" --date 2026-04-15 --time 14:30 --id LAUNCH-1
# Output: Event created (row 1, id=LAUNCH-1)

# All-day event (no time):
xapps add-event "Team Calendar" "Company holiday" --date 2026-04-20
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
```

#### Import ICS

```bash
xapps import-ics "Team Calendar" /path/to/google-calendar.ics
# Output: Imported 47 events into Team Calendar
```

---

### API Endpoints

```bash
# List all events
curl -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/events

# List events in a date range
curl -H 'X-XApps-File: MyWorkbook.json' "$XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/events?from=2026-04-01&to=2026-04-30"

# Create an event
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/events \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"title":"Sprint planning","date":"2026-04-10","time":"09:00","description":"Backlog grooming","color":"#1a73e8"}'

# Update an event (by row number)
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/events/0 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"title":"Sprint planning (moved)","time":"10:00"}'

# Update by custom ID
curl -X PUT $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/events/LAUNCH-1 \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"date":"2026-04-16"}'

# Delete an event
curl -X DELETE -H 'X-XApps-File: MyWorkbook.json' $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/events/0

# Import ICS file content
curl -X POST $XAPPS_API_BASE_URL/api/sheets/Team%20Calendar/ics \
  -H 'X-XApps-File: MyWorkbook.json' \
  -H "Content-Type: application/json" \
  -d '{"ics":"BEGIN:VCALENDAR\nBEGIN:VEVENT\nSUMMARY:Test\nDTSTART:20260410T090000\nEND:VEVENT\nEND:VCALENDAR"}'
```

---

### Agent/AI Workflow Recipes

#### Recipe 1: Populate a release calendar from milestones

An AI agent receives a list of release milestones and creates a calendar for the team.

```bash
# Step 1: Create events for each milestone
xapps add-event "Release Calendar" "Alpha release" --date 2026-04-15 --desc "Internal alpha build" --color "#ff9800" --id ALPHA
xapps add-event "Release Calendar" "Beta release" --date 2026-05-01 --desc "Public beta" --color "#2196f3" --id BETA
xapps add-event "Release Calendar" "RC1" --date 2026-05-15 --desc "Release candidate 1" --color "#9c27b0" --id RC1
xapps add-event "Release Calendar" "GA Launch" --date 2026-06-01 --time "09:00" --desc "General availability" --color "#4caf50" --id GA

# Step 2: Verify the calendar
xapps events "Release Calendar"
# Output:
#   #0 ALPHA 2026-04-15 - Alpha release
#   #1 BETA 2026-05-01 - Beta release
#   #2 RC1 2026-05-15 - RC1
#   #3 GA 2026-06-01 09:00 - GA Launch
```

#### Recipe 2: Import and clean up an ICS export

An agent imports a calendar from Google Calendar and removes past events.

```bash
# Step 1: Import the ICS file
xapps import-ics "Imported Cal" /tmp/google-export.ics
# Output: Imported 120 events into Imported Cal

# Step 2: List events to find past ones
xapps events "Imported Cal" --to 2026-04-09

# Step 3: Delete past events by row number
xapps delete-event "Imported Cal" 0
xapps delete-event "Imported Cal" 1
# ... (repeat for each past event)

# Step 4: Verify remaining events
xapps events "Imported Cal" --from 2026-04-10
```

#### Recipe 3: Generate a weekly digest from calendar data

An agent reads the calendar for the current week and produces a summary.

```bash
# Step 1: Query this week's events
xapps events "Team Calendar" --from 2026-04-06 --to 2026-04-12
# Output:
#   #0 2026-04-07 09:00 - Standup
#   #1 2026-04-08 14:00 - Design review
#   #2 2026-04-10 09:00 - Sprint planning
#   #3 2026-04-10 - All-hands (all-day)

# Step 2: Use the output to compose a digest email or Slack message
# (Agent uses the event list to format a human-readable summary)
```

---

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
