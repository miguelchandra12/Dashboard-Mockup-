# MAPTECH dashboard mockups — source

## Files

    Brand Affinity.dc.html
    Membership Penetration.dc.html
    Affordability Promo Effectiveness.dc.html
    EDM Campaign Performance.dc.html
    support.js                                  runtime that renders the tables
    pasted-1788876927300-0-mtsr4v2y-7y6p.png    MAPTECH logo
    _ds/broadsheet-.../styles.css               design system tokens + components
    _ds/broadsheet-.../_ds_bundle.js            design system components

Keep the folder structure exactly as it is — the HTML files reference
`support.js`, the logo, and `_ds/` by relative path.

## These must be served over HTTP, not opened from disk

Double-clicking an HTML file opens it as `file://`, and the browser then
blocks the page from loading `support.js`. The page renders its headers and
empty tables, and the buttons do nothing. This is a browser security rule,
not a problem with the files.

Serve the folder instead. From inside this folder:

    python3 -m http.server 8000

Then open <http://localhost:8000> and click through to any of the four files.
Filters, tabs, and Details buttons all work.

Node alternative, if you prefer:

    npx serve .

## Putting them on a real site

Upload the whole folder to any static host — Netlify, Vercel, S3, GitHub
Pages, or a plain Apache/nginx directory. No build step, no server-side code.
The four HTML files are the entry points.

## If you cannot serve over HTTP

Use the standalone versions instead (`export/standalone/`). Each is a single
file with everything inlined, so it works from `file://` too and is just as
interactive. The trade-off is that the CSS and JS are no longer separate
files you can edit.
