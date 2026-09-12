# Meeting Sheet

The Meeting sheet provides a workspace-native video conference surface. It stores the meeting plan, dated sessions, invite history, notes links, and attendance metadata in the workbook while audio and video travel through the active MeshAgent room and LiveKit.

Use Meeting when a call is part of the project record: a review, standup, workshop, customer session, or incident bridge whose notes, participants, and follow-up work belong beside the rest of the workbook.

![Meeting pre-join lobby with microphone, camera, Join, invitation, and dated setup controls](/help-assets/screenshots/meeting-lobby-setup.png)

This is the lobby before joining. The example has no active participants; a successful call also requires the room and media services.

## What Ships Today

- Pre-join lobby for checking the session title, date, breakout room, notes, notes sheet, microphone default, and camera default before joining.
- LiveKit-backed participant stage for microphone, camera, and screen-share sessions through the active MeshAgent room.
- Dated session history in the same sheet, so recurring meetings can keep separate notes, invites, attendance, and timestamps.
- Invite delivery with visible failure states instead of silent "manual link" success when SMTP or room grants are not available.
- CLI, MCP, and hosted MeshAgent toolkit tools for configuring meetings, reading state, recording attendance, inviting participants, and clearing invite history.

## Requirements

- Browser media permissions are required for microphone, camera, and screen share.
- Live media requires a MeshAgent room that can provide LiveKit connection credentials.
- Email invites require SMTP configuration or MeshAgent room mail defaults.
- Room access grants require account-level MeshAgent API credentials; the room participant token is not enough for grant REST calls.

## Browser

- Pre-join lobby with meeting date, title, breakout room, notes, notes sheet, microphone default, and camera default.
- Large adaptive participant stage with active speaker emphasis, participant labels, and media status badges.
- Persistent meeting controls for microphone, camera, screen sharing, joining, and leaving.
- Visible invite panel with a share link, copy action, email invite action, and clear-history action.
- Dated meeting history inside one sheet. Selecting or creating a date switches the active meeting while keeping invites, notes, participants, and timestamps separate for that date.
- Grant-aware unavailable state when the browser cannot reach the MeshAgent room or the room does not expose LiveKit connection credentials.

## Common Workflow

1. Add a Meeting sheet to the workbook.
2. Set the meeting date, title, breakout room, and notes sheet.
3. Copy or send the invite link from the invite panel.
4. Join from the lobby after choosing microphone and camera defaults.
5. Keep notes in the linked Wiki, Typewriter, or other sheet.
6. After the call, review attendance and create Kanban cards or follow-up records in the same workbook.

### Prepare a recurring review

Use one Meeting sheet for a recurring review and choose the appropriate date for each session. Set a specific title and link the notes sheet before joining. Selecting another date changes the session record, including its invites and attendance; it is not a filter over one shared notes field. Confirm the date again before sending an invitation.

In the pre-join lobby, choose your microphone and camera defaults and review the room. Joining requires working media credentials as well as browser permission. If the lobby reports that the room or media connection is unavailable, keep the meeting plan and resolve that prerequisite before asking participants to join.

### Invite, join, and follow up

Copying a meeting link prepares a link to share; it does not send mail or grant access. An email invite has a separate delivery result. Check the visible result and invite history before sending it again, especially after a timeout. Invitees still need the appropriate workbook and room access.

Once joined, use the persistent call controls to mute, toggle the camera, share a screen, or leave. Keep the linked notes in a Wiki or Typewriter sheet and record follow-up tasks in Kanban. After leaving, inspect the session's attendance and notes. Saving the workbook preserves meeting metadata, not an ongoing media session or a recording.

### Troubleshooting the lobby

| Problem | Next step |
|---|---|
| Microphone or camera unavailable | Check the browser's site permission and selected device |
| Joining fails | Check the selected room and the reported media/LiveKit connection error |
| Invite not received | Check the delivery result, recipient address, and mail configuration; a copied link is not email delivery |
| Wrong notes or participants | Confirm the active meeting date and dated session |

## Invites

`POST /api/sheets/<meeting>/invites` attempts email delivery and/or room access granting. Its returned invite may instead have `delivery: "manual-link"` on a local server without either transport; that record is not proof of delivery or access. In MeshAgent rooms, outbound delivery uses room/runtime SMTP configuration such as `SMTP_HOST`, `SMTP_PORT`, `SMTP_FROM`, `SMTP_REPLY_TO`, `SMTP_USERNAME`, and `SMTP_PASSWORD`; `SMTP_URL` is also supported, and the same keys may be prefixed with `MESHAGENT_` or `XAPPS_MEETING_INVITE_` for room-specific configuration. When xApps runs inside a MeshAgent room with `MESHAGENT_TOKEN`, the invite route can default the transport to `mail.meshagent.com`, but the provisioned sender mailbox must still be supplied explicitly through `SMTP_FROM` (and optionally `SMTP_REPLY_TO`); xApps does not assume that a generic mailbox exists. Room access grants are separate and require `MESHAGENT_INVITE_API_KEY` or `MESHAGENT_API_KEY` with `MESHAGENT_PROJECT_ID` and `MESHAGENT_ROOM`/`MESHAGENT_ROOM_URL`; the room participant token is not used for account-level room-grant REST calls. In a MeshAgent room, SMTP configuration or delivery failure returns a visible invite error instead of silently recording a manual-link success.

## CLI

The recipes use an existing authorized `MyWorkbook.json` in `local` storage. Replace that file and storage target together for your actual workbook, and set `XAPPS_API_BASE_URL` to its authorized host. Commands that extract structured receipts also require `jq`.

```bash
xapps_scoped() {
  xapps --base-url "${XAPPS_API_BASE_URL:?Set the authorized host URL}" \
    --file 'MyWorkbook.json' --workbook-storage-target local "$@"
}
```

Read or prepare the meeting independently of sending invitations:

```bash
xapps_scoped meeting-status Meeting --json
xapps_scoped meeting-configure Meeting --date 2026-09-15 --title "Design Review" \
  --breakout-room design --notes "Review launch blockers" --notes-sheet Notes \
  --default-microphone --no-default-camera --json
xapps_scoped meeting-attendance Meeting --json
```

For an explicitly authorized invitation, choose the intended recipient and set `XAPPS_PUBLIC_BASE_URL` to this same host's recipient-reachable public base URL (including any deployment prefix). Construct the link from the same workbook, sheet and storage target used by the CLI scope; do not copy a link to another workbook:

```bash
MEETING_LINK=$(node -e 'const [base,file,sheet,target]=process.argv.slice(1); const u=new URL(base.replace(/\/$/, "")+"/w/"+encodeURIComponent(file)+"/sheet/"+encodeURIComponent(sheet)); u.searchParams.set("storageTarget",target); process.stdout.write(u.href);' \
  "${XAPPS_PUBLIC_BASE_URL:?Set the authorized public URL}" MyWorkbook.json Meeting local)
xapps_scoped meeting-invite Meeting --email teammate@example.com --link "$MEETING_LINK" \
  --json > meeting-invite-receipt.json
jq '{delivery:.invite.delivery,accessGranted:.invite.accessGranted,message:.invite.message}' meeting-invite-receipt.json
xapps_scoped meeting-status Meeting --json
```

Report `smtp`, room access granted, `manual-link`, or failure exactly as returned. An HTTP success or stored invite does not establish delivery. There is no advertised idempotency guard for `meeting-invite`; after uncertain delivery, reconcile the invite history and transport outcome before another send. Do not invent a request-ID flag or silently resend.

Clearing invite history is a separate removal operation. Only when that exact cleanup was requested or already authorized:

```bash
xapps_scoped meeting-clear-invites Meeting --json
xapps_scoped meeting-status Meeting --json
```

## MCP

- `meeting_get_state`
- `meeting_configure`
- `meeting_invite`
- `meeting_clear_invites`

## MeshAgent Toolkit

The surface contributes sheet-state tools plus native meeting tools:

- `meeting_get_state`
- `meeting_configure`
- `meeting_record_attendance`
- `meeting_invite`
- `meeting_clear_invites`

## Data Contract

Workbook state stores:

- `meetingTitle`
- `meetingDate`
- `meetingBreakoutRoom`
- `meetingNotes`
- `meetingNotesSheet`
- `meetingDefaultCamera`
- `meetingDefaultMicrophone`
- `meetingStatus`
- `meetingLastJoinedAt`
- `meetingLastEndedAt`
- `meetingLastInviteLink`
- `meetingInvitees`
- `meetingParticipantsSnapshot`
- `meetingSessions`
- `meetingActiveSessionId`

Live media state is intentionally not persisted in the workbook.
