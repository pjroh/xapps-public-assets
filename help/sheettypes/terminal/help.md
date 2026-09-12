## Terminal

The Terminal sheet renders a real browser terminal with xterm.js. It gives a workbook an operational shell for local commands or a MeshAgent-relayed PTY from a remote Mac connector.

Use Terminal when the project needs command-line work in the same context as the rest of the workbook: running a repo command, operating Codex or Claude through a controlled connector, checking deployment state, or giving an agent a visible shell target during a room session.

![Terminal setup dialog over the workbook terminal; configure a session before connecting](/help-assets/screenshots/terminal-sheet.png)

### Before you connect

Decide **where the command will run** and **where its output files should go**. Local terminal mode runs on the xApps host. A MeshAgent tunnel uses the selected remote connector. The workbook stores setup and tab preferences; a live shell process runs outside the workbook and does not survive a host or connector restart.

| Choice | Use it for | Check before starting |
|---|---|---|
| Local terminal | Tools installed on the xApps host | Host execution permissions and working directory |
| MeshAgent tunnel | Codex or Claude on an authorized remote computer | Online connector identity, target command, and room |
| Mac local output | Files on the connected Mac | The selected connector advertises that storage capability |
| Room output | Files available in the selected room | The connector exposes an authorized room-storage path |

### Keep different tasks in different tabs

![Terminal before connection, showing the selected command, local host mode, storage target, and per-tab setup control](/help-assets/screenshots/terminal-before-connect.png)

Create a tab for each distinct command context. Give it a recognizable name, select it, and use its setup control before connecting. New tabs inherit the shared setup; an **Active tab** override belongs only to that tab. Check the working directory and output destination after switching tabs, particularly when two connectors have similar display names.

When a session disconnects, inspect its visible state before starting a replacement. A transport reconnect can resume an existing live session; restarting a stopped host cannot reconstruct its old process. Preserve useful output or generated files in the intended storage destination as you work.

### If setup cannot continue

An empty connector list means no matching connector is currently available to this picker. Run the advertised connector command on the intended computer, refresh the picker, and choose its stable identity. Disabled storage choices indicate missing advertised capability. Do not paste credentials into a worksheet or substitute another room's token to make the control selectable.

### What This Bridge Enables

The MeshAgent Terminal bridge is for the case where xApps is deployed in MeshAgent, but the useful Codex installation, repo checkout, credentials, and local tools live on your Mac. The Mac runs an outbound connector into the `xapps` room. Deployed xApps can then open a Terminal Sheet and ask that connector to start Codex on the Mac. The browser still talks to deployed xApps, but the PTY process is running locally on the Mac.

The reverse direction matters too: once Codex is running on the Mac through this bridge, xApps passes it workbook context, the active working directory, the selected storage target, and the connector-visible room storage path when configured. That lets local Mac Codex write normal Mac files when you choose Mac local storage, or write files intended for the MeshAgent room when the connector advertises a room-storage mount.

Example outcomes:

- A MeshAgent-deployed xApps workbook can open a live Terminal tab backed by `~/Projects/xApps` on the Mac.
- A Terminal tab can start local Mac Codex with per-tab flags such as `--model gpt-6-astra`.
- A local Mac Codex session can save generated output into Mac-local paths, or into MeshAgent room storage when that storage path is exposed to the connector.
- A room-visible connector lets xApps decide whether Mac local and room storage targets are actually available instead of showing destinations that cannot work.

### Safety Model

- The browser terminal is an interactive session, not a workbook data table.
- MeshAgent injects the selected room's token into the connector runtime; xApps never asks for or stores a token override.
- Local mode starts a PTY on the current xApps host.
- MeshAgent mode relays a PTY from a named remote connector through the room; the Mac dials out and does not open inbound ports.
- Access to private workbooks does not automatically grant access to every terminal connector. Treat terminal connector permissions as a separate operational boundary.

### What Works Now

- Terminal sheet type appears in the add-sheet menu.
- xterm.js renders inside the workbook sheet and accepts keyboard input.
- Setup tunnel dialog captures the target command, per-tab **Optional parameters**, stable remote connector id, MeshAgent room URL, and working directory. Duplicate display names remain distinguishable by id, target, storage capability, freshness, and online state.
- Setup tunnel dialog captures whether generated files should go to xApps host storage, MeshAgent room storage, or Mac local storage; Mac and room targets are enabled only when a live matching connector advertises that capability.
- Terminal sheets keep a shared default setup, and each tab can override that setup after you edit its active-tab settings or save the tunnel dialog for that tab.
- Generated connector commands rely on the selected room's MeshAgent-injected runtime environment and contain no token override.
- Local mode starts a PTY on the current xApps host.
- MeshAgent mode relays an interactive PTY from the Mac connector through the room.
- Setup and connect failures stay visible and do not claim unsaved or unconnected state. Dialogs trap focus, restore it on close, and Terminal tabs support roving keyboard focus plus keyboard rename/close actions.

### CLI

Terminal CLI commands require an explicit saved-workbook scope: `--file <workbook> --storage-target <local|meshagent-room|mac-local>`. Use `terminal-state`, `terminal-config`, `terminal-settings-set`, `terminal-theme-set`, and the `terminal-tab-*` commands for guarded configuration. Use `terminal-connectors` and `terminal-select-connector` for connector discovery and selection.

Session lifecycle commands are `terminal-sessions`, `terminal-start`, `terminal-read`, `terminal-attach`, `terminal-input`, `terminal-resize`, and `terminal-close`. Session network calls require `--timeout-ms`; reads require an explicit `--after-seq` reconnect cursor and `--max-bytes`; input requires a retry-safe `--input-seq`; closing requires `--yes`. `terminal-start` accepts only governed `codex` or `claude` connector targets and reports the matching cleanup command.

### Common Workflow

1. Add a Terminal sheet.
2. Select the tab you want to configure.
3. Choose **Local terminal** when the xApps host itself should run the command, or **Setup tunnel** when a remote Mac should provide the PTY.
4. For MeshAgent tunnel mode, select `codex` or `claude` as the target command.
5. Add per-tab **Optional parameters** when this tab needs extra Codex or Claude startup arguments.
6. Run the generated connector command on the remote Mac. It updates immediately for the selected target and intentionally keeps per-tab parameters out of connector-wide argument variables.
7. Refresh the connector list and select the exact stable connector id. Display labels are descriptive only and are never used as identity.
8. Choose Mac local storage for files on the Mac, or MeshAgent room storage when the live connector advertises a connector-visible room-storage path.
9. Use the sheet as the visible terminal for the workbook session.

New tabs start from the sheet's shared Terminal setup. Once you change **Active tab** settings, **Flags**, or save **Setup tunnel** for a tab, that tab stores its own setup override. Other tabs keep using the shared default or their own override.

### Remote Mac Setup Pattern

1. Create or open a Terminal sheet.
2. Choose **Setup tunnel**.
3. Select **MeshAgent tunnel to remote Mac**.
4. Choose the target command: `codex` or `claude`.
5. Enter any per-tab **Optional parameters**. Blank means no extra per-tab arguments.
6. Run the displayed command on the remote Mac. Codex output includes `XAPPS_CODEX_ARGS='exec --json'`; Claude output includes `XAPPS_CLAUDE_COMMAND=claude` and `XAPPS_CLAUDE_ARGS='-p --output-format stream-json --verbose'`.
7. Refresh the picker and select the newly online stable connector id before saving.

The Mac connector dials out to the MeshAgent room. No inbound ports are opened on the Mac, so the machine can sit behind NAT or a firewall anywhere with internet access.

For the long-form setup reference, see `docs/TerminalSetup for Mac.md`.

### Deployed Transport Requirement (Slow Typing Fix)

The browser terminal prefers a WebSocket
(`/api/sheets/<ref>/terminal/sessions/<id>/ws`) and only falls back to
HTTP polling when the WebSocket cannot attach. On a private MeshAgent
deployment the deploy MUST use `--validation-mode=cookie`: browser
WebSockets cannot send Authorization headers, so a cookie-validated edge
is the only way the upgrade can authenticate. Without that flag the edge
rejects the upgrade, the terminal silently degrades to HTTP polling
after the attach timeout, and every keystroke pays the polling interval —
the terminal "works" but feels slow. This is deploy configuration, not
an xApps bug; the xApps host accepts the terminal WebSocket with exactly
the same credentials as HTTP requests (see
`tools/test-terminal-ws-auth-postures.ts` and the deploy-flag notes in
`docs/MESHAGENT.md`).

Run the canonical MacCodex launcher on the Mac that should provide Terminal, Mac/PC files, and Chat:

```sh
cd ~/Projects/xApps
npm run connector:codex
```

Select the Terminal connector whose display name is `local-mac-codex`; xApps stores and routes by its stable connector id. The same launcher supervises a separate process-backed `MacCodex` Chat participant. Chatbot selection and Chat-sheet `@MacCodex` appear only while that routable Chat participant is online; connector presence alone never creates a stale Chat target. Chat threads use room dataset storage by default so they remain resumable.

### Automation and Transport Limits

- Public API, SDK, CLI, MCP, and hosted-tool session starts accept only the governed `codex` or `claude` targets. They do not expose an arbitrary-shell command field.
- Every automation call is scoped to an explicit saved workbook, storage target, and Terminal sheet. Execute permission and workbook/session ownership are checked again for session reads and mutations; unauthorized sessions use no-leak not-found responses.
- Settings mutations use revision/fingerprint guards and durable request ids. Input uses a positive retry-safe `inputSeq`; output uses a monotonic `afterSeq` cursor and explicit byte limit.
- Connector identity is a stable id with signed, ordered heartbeats. Offline, stale, duplicate-label, replayed, out-of-order, and ownership-conflict cases fail closed.
- Live PTY processes and replay buffers are bounded host/connector memory. They survive a transient WebSocket or HTTP transport reconnect while the session lives, but not a host or connector process restart. Workbook configuration, tab state, history, mutation receipts, connector identity, and registry ordering watermarks persist separately.

### Codex Startup Flags

When you type `connect`, the Terminal sheet does not parse anything after the word `connect`. Instead, xApps starts a new interactive PTY from the active tab's saved setup. The startup flags come from the Terminal settings panel and from connector environment defaults.

The normal per-tab workflow is:

1. Click the gear beside the active Terminal tab.
2. Keep **Target command** set to `Codex`.
3. Put one-run or per-tab startup flags in **Optional parameters**.
4. Save setup and type `connect` in the Terminal sheet.

The Surface menu's **Terminal → Settings → Active tab → Flags** field edits the same saved value.

For example, this **Flags** value selects a model while retaining the operator’s approval and sandbox configuration:

```sh
--model gpt-6-astra
```

With the Mac connector command shown above, that launches the interactive Terminal session as if the Mac ran:

```sh
codex --model gpt-6-astra
```

The current Codex CLI uses `--ask-for-approval` (not the retired `--approval-mode`). Set an approval or sandbox override only when the operator chose it; changing models does not authorize changing those controls. Check installed `codex --help` and account model availability before configuring a tab.

The flags are saved on the Terminal sheet tab. Different tabs can use different flags, so one tab can use `--model gpt-6-astra` while another uses `--model <another-available-model>`.

Connector environment variables are broader defaults. Use them when every interactive Codex session through that Mac connector should start the same way:

```sh
-e XAPPS_TERMINAL_CODEX_COMMAND=codex \
-e XAPPS_TERMINAL_CODEX_ARGS='--model gpt-6-astra' \
```

With that connector default and no per-tab model override, the Mac starts:

```sh
codex --model gpt-6-astra
```

Use `XAPPS_TERMINAL_CODEX_COMMAND` when you need a different executable path, for example:

```sh
-e XAPPS_TERMINAL_CODEX_COMMAND=/opt/homebrew/bin/codex
```

Keep these two Codex env families separate:

- `XAPPS_TERMINAL_CODEX_COMMAND` and `XAPPS_TERMINAL_CODEX_ARGS` are for interactive Terminal Sheet sessions started by typing `connect`.
- `XAPPS_CODEX_ARGS='exec --json'` is for non-interactive agent request execution, such as Kanban/card agent dispatch. It is not where Terminal Sheet per-connect flags go.

Examples:

```text
Interactive Terminal tab:
  Terminal Settings → Active tab → Flags = --model gpt-6-astra
  Terminal prompt → connect

Connector-wide interactive default:
  -e XAPPS_TERMINAL_CODEX_ARGS='--model gpt-6-astra'

Non-interactive card/request execution:
  -e XAPPS_CODEX_ARGS='exec --json'
```

For room-backed files, set `XAPPS_TERMINAL_FILE_STORAGE_TARGET=meshagent-room`
and `XAPPS_TERMINAL_FILE_STORAGE_PATH` to the connector-visible room-storage
path. The connector passes the target and path into the PTY environment so the
terminal agent can place generated files consistently.

```text
xApps Terminal sheet -> MeshAgent room -> Mac daemon -> node-pty -> codex / claude / shell
```
