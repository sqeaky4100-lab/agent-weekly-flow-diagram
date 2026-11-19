# Weekly Flow Diagram

Static archive of the weekly **Weekly Flow – Combined Diagram**, one
self-contained page per week. The site root opens on the newest diagram.

## Layout

```
index.html                  generated redirect to the newest diagram
diagrams/*.html             one self-contained diagram per file, per week
diagrams.json               generated list of diagrams (date, path, title)
favicon.svg                 site icon
scripts/build-index.mjs     regenerates index.html and diagrams.json
vercel.json                 cache headers for static hosting
```

Each diagram is a standalone page with its own CSS and script inlined, so it can
be opened, emailed, or archived on its own. The index script only reads from
them; it never rewrites them.

## Adding a week

1. Drop the new file into `diagrams/`, named with its week-start date, e.g.
   `diagrams/weekly_flow_2026-11-23.html`. Any filename containing `YYYY-MM-DD`
   or `YYYYMMDD` works; `<meta name="diagram:date" content="YYYY-MM-DD">` in the
   page overrides the filename.
2. Run `npm run index` to regenerate `diagrams.json` and `index.html`.
3. Commit and push. If the repo is connected to Vercel, it redeploys on push.

## Local preview

```bash
npm run dev     # builds the index, serves on http://localhost:4000
```

## Deploying

No build step and no dependencies. On Vercel: framework preset **Other**, build
command empty, output directory the repo root.
