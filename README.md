# slidev-theme-narrative

A monochrome, one-accent, photography-forward [Slidev](https://sli.dev) theme.

The whole style is one durable system: a monochrome surface (black / white / grey),
generous whitespace, large confident titles, big full-bleed photography, and a
**single** accent colour used sparingly. Mode (dark/light) and the accent are the
only per-deck inputs — choose them, write content, done. No per-deck CSS, layouts,
or components should be needed.

## Usage

In a deck living next to this folder, point the headmatter at it:

```yaml
---
theme: ./theme
colorSchema: dark          # or: light
themeConfig:
  accent: '#E5484D'        # the one accent for the whole deck
---
```

That's the entire configuration. Both decisions are real inputs:

| Input                  | Values                                    |
| ---------------------- | ----------------------------------------- |
| `colorSchema`          | `dark` (cinematic) · `light` (airy)       |
| `themeConfig.accent`   | any single hex colour (e.g. red / blue / green) |

Suggested accents that read well on both modes:
`#E5484D` red · `#3B82F6` blue · `#30A46C` green.

## Colour tokens

The theme exposes CSS variables you rarely need to touch directly. They react to
mode and accent automatically:

`--bg` · `--bg-alt` · `--text` · `--text-secondary` · `--hairline` · `--accent`

## Typography

- **Inter** (bundled, offline-safe) for everything, **Fira Code** for code.
- Big title, tiny support — the size contrast is the design. Sentence case titles.
- Accent shows up as: `**bold**` → accent word, `<u>underline</u>` → accent
  underline, links → accent. Keep it to one accent moment per slide.

## Layouts

All five are drop-in — no custom layouts required in a deck.

| Layout        | For…                                                | Frontmatter        |
| ------------- | --------------------------------------------------- | ------------------ |
| `cover`       | Title, section breaks, mood moments                 | `background: /x.jpg` (+ `class: grayscale`) |
| `statement`   | One punchy claim (3–6 words)                         | —                  |
| `center`      | Lists, steps, structured info, diagrams             | —                  |
| `image-left`  | A concept anchored to a photo                        | `image: /x.jpg` (+ `class: grayscale`) |
| `image-right` | Mirror of `image-left` — alternate L/R               | `image: /x.jpg`    |
| `default`     | Plain padded content                                 | —                  |

Covers apply a scrim automatically so light titles stay readable over any photo.

## Components

The theme ships one small, generic building block; anything talk-specific belongs
in the deck's own `components/` folder, not here.

- `<Kicker>…</Kicker>` — the small uppercase eyebrow above a title.

## Utilities

- `class: abstract-bg` on a slide — a subtle accent-tinted abstract background
  (auto-derived from the chosen mode + accent). One background treatment per deck.
- `.kicker`, `.accent`, `.muted` helper classes.
- Markdown ordered lists (`1.` / `2.`) render with accent numerals out of the box,
  so simple numbered takeaways need no component.

## Offline

Fonts are self-hosted via `@fontsource`, so a built deck presents with no network.
