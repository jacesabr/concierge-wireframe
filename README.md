# concierge — the map

one folder that ties together where the design is authored, where it's versioned, and where it's live.

## the three places

| place | what it's for | link |
| --- | --- | --- |
| **Claude Design** | where *you* author / plan the design | https://claude.ai/design/p/9d9350ce-cfce-4dc9-9b1d-e6fc991b045b?file=Website+Chat+Concierge.dc.html |
| **this repo** | canonical file + version history (git = design changelog) | https://github.com/jacesabr/concierge-wireframe |
| **Render (live)** | the published, shareable site | https://concierge-wireframe.onrender.com/ |

## the one rule

`public/index.html` is the **single source of truth**. everything else is a view of it. never edit the live site or the design page expecting it to flow back — edit here, or drop a new export here.

## the sync ritual (the seam)

Claude Design is behind your login — no tool can pull from it — so there's one manual hop:

1. in Claude Design → **Share / export → download the standalone HTML**
2. drop the file into `design/exports/`
3. tell Claude Code **"sync"**

then Claude Code does the rest automatically:
- copies the export → `public/index.html`
- `git commit && git push` → Render auto-deploys
- notes the change in the log + shows you a diff vs the last version

## layout

```
concierge-site/
├─ public/            ← served by Render (publishPath = public). ONLY this is public.
│  └─ index.html      ← canonical live copy of the design
├─ design/            ← NOT served. docs + authoring bridge.
│  ├─ exports/        ← drop Claude Design exports here, newest = latest
│  └─ planning/       ← house-style planning docs (.md + .html twins)
└─ README.md          ← this map
```
