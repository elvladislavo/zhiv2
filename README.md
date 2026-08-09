# Zhyvitsa — Website

Marketing site for Zhyvitsa, a floristry & event decoration studio in Warsaw.
Static HTML/CSS/JS, bilingual (Polish default, English at `/en`).

## Structure

```
.
├── index.html              Polish homepage (default / root)
├── en/
│   └── index.html          English homepage
├── assets/
│   ├── css/
│   │   └── style.css       All site styling (design tokens, layout, components)
│   ├── js/
│   │   ├── vine-geometry.js  Math module: stem curve + vortex-spiral generation
│   │   └── main.js           App wiring: header, nav, scroll reveals, vine animation
│   └── images/              Reserved for future photography (currently unused —
│                             gallery and hero visuals are CSS-generated)
└── README.md
```

Both `index.html` files share the same `assets/` folder via relative paths
(`assets/...` from the root, `../assets/...` from `en/`), so styling and
behavior stay in sync across languages — only the copy differs.

## Running locally

The JS is loaded as ES modules (`<script type="module">`), which browsers
block from `file://` due to CORS. Serve the folder over HTTP instead, e.g.:

```bash
# Python
python3 -m http.server 8000

# Node
npx serve .
```

Then open `http://localhost:8000/`.

## Notes on the vine animation

`vine-geometry.js` is a self-contained, dependency-free module: it builds an
organically curved "stem" path and a set of "vortex-spiral" branch paths
anchored to it. `main.js` renders these into each `.vine-bg[data-vine]`
mount point and drives their reveal via scroll position — see the doc
comments at the top of `vine-geometry.js` for the underlying math.
