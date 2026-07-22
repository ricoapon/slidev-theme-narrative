# Test deck

A minimal Slidev deck for developing and previewing the theme locally. It links
the theme straight from the parent directory, so there is no packing or
publishing step — edits to the theme show up live.

## Setup (once)

The theme is consumed as a linked local dependency (`"@ricoapon/slidev-theme-narrative": "file:.."`
in `package.json`), which npm installs as a symlink to the repo root. You need
the theme's own dependencies (the bundled fonts) present too, so install in both
places once:

```bash
# from the repo root — installs the theme's font dependencies
npm install

# from this test/ directory — installs Slidev and links the theme
cd test
npm install
```

## Run

```bash
npm run dev
```

Because the theme is symlinked, edits to its `styles/`, `layouts/`, and
`components/` **hot-reload instantly** — no rebuild, no reinstall, no `npm pack`.

One caveat: this deck's **headmatter** (`theme`, `colorSchema`, `themeConfig` —
including the `accent`) is only read when the server starts. After changing it,
restart `npm run dev` to see the effect.

## Build / export

```bash
npm run build     # static site into dist/
npm run export    # PDF
```
