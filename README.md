# xapps-splash-assets

Static image assets for the [xApps](https://github.com/pjroh/xApps) welcome
splash carousel. Served from this public repo via [jsDelivr](https://www.jsdelivr.com/)
so the main xApps docker image doesn't need to bundle them.

## Why a separate repo

The main xApps repo is private. jsDelivr can only mirror public repos.
The 16 splash slide PNGs live here, in their own public repo, so they can
be CDN-distributed without making the rest of xApps public.

## CDN URLs

Pin to a tagged version (`@vX.Y.Z`):

```
https://cdn.jsdelivr.net/gh/pjroh/xapps-splash-assets@v2.6.7/welcome/01-why.png
https://cdn.jsdelivr.net/gh/pjroh/xapps-splash-assets@v2.6.7/welcome/02-hook.png
...
https://cdn.jsdelivr.net/gh/pjroh/xapps-splash-assets@v2.6.7/welcome/16-getstarted.png
```

The xApps shell reads the base URL from `<meta name="xapps-welcome-base">`
in the served `index.html`. Set it to the directory above (with trailing slash).

## Slides

| File | Beat |
|---|---|
| `01-why.png`         | Golden Circle — Why we built xApps |
| `02-hook.png`        | 9 apps in → 1 workbook out |
| `03-promise.png`     | One workbook, every shape of work |
| `04-kanban.png`      | Kanban — move work, not paragraphs |
| `05-timeline.png`    | Timeline — time, finally readable |
| `06-doc.png`         | Doc — knowledge that survives |
| `07-gallery.png`     | Gallery — visual evidence, sortable |
| `08-dashboard.png`   | Dashboard — status at a glance |
| `09-poll.png`        | Poll — async decisions |
| `10-calendar.png`    | Calendar — recurring rhythm |
| `11-whiteboard.png`  | Whiteboard — spatial thinking |
| `12-spreadsheet.png` | Spreadsheet — numbers that talk |
| `13-typewriter.png`  | Typewriter — long-form thinking |
| `14-multiplayer.png` | Multiplayer, always on |
| `15-agentic.png`     | AI as a teammate, not a chatbox |
| `16-getstarted.png`  | Pick your way in |

## Versioning

Tags here track the xApps release that ships them. When the splash
content changes:

1. Re-render the PNGs in xApps
2. Copy them here and tag matching the new xApps version
3. Bump `<meta name="xapps-welcome-base">` in xApps to point at the new tag

## License

Same as xApps (proprietary, all rights reserved).
