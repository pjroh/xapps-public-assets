# xapps-public-assets

Public CDN-served assets for the [xApps](https://github.com/pjroh/xApps) platform.
This repo exists so jsDelivr can mirror these files (the main xApps repo is private).

## Layout

```
welcome/        # 16 splash carousel slide PNGs (1920×1080)
help/           # Help content (markdown)
  help.md       # Top-level help index
  sheettypes/   # Per-surface help, one file per sheet type
    kanban/help.md
    spreadsheet/help.md
    timeline/help.md
    ...
```

## CDN URL pattern

```
https://cdn.jsdelivr.net/gh/pjroh/xapps-public-assets@<TAG>/<path>
```

The xApps shell reads two meta tags from the served `index.html`:

```html
<meta name="xapps-welcome-base" content="https://cdn.jsdelivr.net/gh/pjroh/xapps-public-assets@v2.6.9/welcome/">
<meta name="xapps-help-base"    content="https://cdn.jsdelivr.net/gh/pjroh/xapps-public-assets@v2.6.9/help/">
```

Either tag's `content` can be set to `""` to fall back to bundled copies
(if any are present in the deploy).

## Versioning

Tags here track the xApps release that ships pointing at them. Bump
both repos together:

1. Update content here, commit, tag (e.g., `v2.6.9`)
2. Update meta-tag bases in `xApps/packages/xapps-shell-core/src/assets/index.html.template`
3. Tag matching version in xApps
4. Run `tools/cdn-purge.sh` to flush jsDelivr's edge cache (optional — usually picks up new tags within ~30s anyway)

## What's served

| Path | Used by | Loaded |
|---|---|---|
| `welcome/01-why.png` … `16-getstarted.png` | Welcome splash carousel | Lazy (when splash opens) |
| `help/help.md` | Help dialog (top-level) | Lazy (when help opens) |
| `help/sheettypes/<surface>/help.md` | Help dialog (per-surface) | Lazy (when help opens) |

## License

Same as xApps (proprietary, all rights reserved).
