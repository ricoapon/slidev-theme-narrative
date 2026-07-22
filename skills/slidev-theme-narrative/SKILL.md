---
name: slidev-theme-narrative
description: >-
  Opinionated guidance for authoring a narrative-style slide deck with the
  slidev-theme-narrative Slidev theme — storytelling talks (mentoring, ideas,
  points of view) rather than code demos or dense technical content. Use when
  building, structuring, or reviewing a deck on this theme: choosing mode and
  accent, picking layouts, sourcing and treating imagery, and keeping the slide
  rhythm right. The theme's configuration and API live in the repo README; this
  skill is the taste layer on top of it.
---

# Authoring narrative decks with `slidev-theme-narrative`

This is the opinionated way to *use* the theme. The README documents what the
theme offers (config inputs, layouts, tokens, components); this skill is how to
make a deck with it feel right. It assumes narrative talks — where you tell a
story and the spoken delivery carries the detail — not demo-heavy or reference
decks.

The whole style is one durable system, deliberately constrained. The
constraints are what make decks feel consistent and fast to build, so a deck
doesn't get redesigned from scratch every time. Follow them rather than
inventing per-deck.

---

## 0. Before you build — confirm three choices

A few things are decided fresh per deck. If the user hasn't stated them, **ask
first**:

1. **Mode** — dark or light? (See §3.)
2. **Accent color** — red, blue, green, or something else? (See §3.)
3. **Local-first images?** — will this be presented offline, or online with
   internet? (See §6.)

Everything else here is fixed and does not need to be asked about.

---

## 1. The essence (the non-negotiables)

If a deck follows only these four rules, it already looks right:

1. **Monochrome base, one accent.** Black-and-white (or near) as the
   foundation; a single accent color used *sparingly* for emphasis. Never a
   second accent.
2. **Photography does the heavy lifting.** Big, full-bleed images carry mood
   and mark section breaks.
3. **One idea per slide, almost no text.** A big title and a few short phrases.
   If it reads like a paragraph, it belongs in the spoken delivery, not on the
   slide.
4. **A fixed, small layout vocabulary.** A handful of standard layouts, reused.
   No bespoke layout per slide.

Everything below is the detail behind these four.

---

## 2. What this style is — and is not

**It is:** clean, modern, confident, lightly editorial. Restraint over
decoration. Concretely that means a monochrome surface (mostly black/white/gray),
generous whitespace, large confident titles, and a single accent color
appearing as small touches — an underline, a highlighted word, the active
element of a diagram. Optionally a subtle abstract background tinted with the
accent (see §7). The overall impression should be sleek and intentional.

**It is not:**
- **Dense, text-heavy, dated slides** — bullet lists stacked to the edges, small
  type, no imagery. This is the main failure mode to avoid.
- **Fully illustrated, heavily art-directed decks** — the kind that look
  gorgeous but take days of custom design per slide. The budget here is "sharp
  and fast," not "bespoke artwork."

The aim is to look intentional without spending a designer's week on it.

---

## 3. Color — the two per-deck decisions

Both are real theme inputs (`colorSchema` and `themeConfig.accent` — see the
README for the exact headmatter). You never edit CSS to change them; you choose
them once and write content.

### Decision 1 — Mode: dark or light

Same system either way; pick one per deck. Dark tends to feel cinematic and
image-forward; light feels airy and clean. Both are valid — neither is a
fallback. The exact color values each mode resolves to are in the README.

### Decision 2 — Accent: one color

Exactly **one** accent per deck. Good defaults, each chosen to read well on
*both* dark and light backgrounds:

| Accent | Primary   | Alternative (more energy) | Feel                          |
| ------ | --------- | ------------------------- | ----------------------------- |
| Red    | `#E5484D` | `#EE0000`                 | warm, urgent, confident       |
| Blue   | `#3B82F6` | `#0070F3`                 | calm, technical, trustworthy  |
| Green  | `#30A46C` | `#22C55E`                 | fresh, growth, approachable   |

If the user doesn't care, pick one that fits the topic and say which you chose.
Any other single hue is fine too — the rule is "one accent, used the same
restrained way," not "one of these three."

### Accent rules

- **Max one accent moment per slide** — an underline, one highlighted word, a
  small shape, a rule, or the active state of a diagram. Never two.
- Accent is for *emphasis and identity*, never for large fills or body text.
- The accent is chosen once and used consistently across the whole deck.

In markdown, the theme wires accent to `**bold**` (accent word), `<u>underline</u>`
(accent underline), and links. Reach for those rather than custom styling.

---

## 4. Typography

The theme ships Inter (body) and Fira Code (code) and fixes the type scale, so
you don't set sizes per slide. The authoring discipline on top of it:

- **Big title, tiny support.** Titles are large and confident; supporting text
  is small, short, and in the secondary color. The size contrast *is* the
  design.
- **Sentence case for titles** (not Title Case, not ALL CAPS) — calmer and more
  modern.
- No more than **two visible type sizes** on a normal content slide.
- Avoid light weights over photos — they get thin and hard to read.

---

## 5. Layout vocabulary

These cover ~95% of any talk, and they are all standard theme layouts — no
custom layouts required. Reach for anything else only for a genuine one-off.

| Layout        | Use it for…                                          | Content rule                            |
| ------------- | ---------------------------------------------------- | --------------------------------------- |
| `cover`       | Title slide, section breaks, mood/transition moments | Full-bleed `background:` photo + 1 line |
| `statement`   | One punchy claim                                     | 3–6 words, centered, nothing else       |
| `image-left`  | A concept anchored to a photo                        | Photo left, ≤4 short lines right        |
| `image-right` | Same, mirrored — alternate L/R so it isn't mechanical| Photo right, ≤4 short lines left         |
| `center`      | Lists, steps, structured info, a data/diagram slide  | Short title + a tight structure         |

**Rhythm matters as much as the layouts.** Alternate *breath* (cover /
statement — almost no text) with *substance* (center / image slides). A run of
five text slides in a row is what makes a deck feel boring — break it with a
full-bleed image or a statement slide.

---

## 6. Imagery

Photography is the main design device, so it gets clear rules.

### Default source: Unsplash

**When the user does not provide an image or a source, get photos from
Unsplash.** It is the default source for all photography — no need to ask each
time. Pick high-resolution, landscape-orientation images whose subject fits the
slide, and prefer clean, uncluttered compositions that leave room for a title.

### Local-first? — ask how the deck will be presented

Whether images should be downloaded locally or referenced by URL depends on the
venue, so confirm it once per deck:

- **Offline, or venue/internet uncertain → local-first.** Download images into
  `public/` and reference them as `/name.jpg`. Always works, always exports,
  never breaks mid-talk. Use semantic filenames (`cover.jpg`, `intro.jpg`).
- **Online with reliable internet → remote URLs are fine.** No need to
  download; referencing an Unsplash (or other) URL directly is acceptable.
- **If unsure, default to local-first** — it never fails.

### Treatment

- **Full-bleed for covers/sections** via the layout's `background:` (cover) or
  `image:` (image-left/right) frontmatter — one consistent mechanism, every
  deck.
- **Text over photos needs contrast protection.** Covers apply a scrim
  automatically so light titles stay readable; you don't add your own.
- **Keep photos cohesive by selection, not post-processing.** Pull images that
  already share a mood — similar light, palette, and grain — so the deck feels
  like one piece and the accent stays the only color that pops. If a photo
  clashes, find a better-fitting one rather than filtering it.

---

## 7. The abstract background & custom work — reuse, don't reinvent

For content-heavy or light-mode slides, the theme ships a subtle abstract,
accent-tinted background. **Opt in with `class: abstract-bg`** on the slide —
don't hand-roll one. It reads the deck's mode + accent automatically, so
changing the accent restyles it with nothing to redraw. Keep it subtle: it
lives *behind* content and must never compete with it. One background treatment
per deck.

The same discipline applies to everything custom:

- **Minimize per-deck `styles.css`, custom layouts, and custom components.** The
  bulk of slides should need *none* of these. A deck is near-zero-config: choose
  mode + accent, write content, done.
- **Build a custom component only for the single diagram or interaction a talk
  truly hinges on** — and build it in the same language as everything else
  (monochrome + the one accent, same type scale) so it looks native. It belongs
  in the deck's own `components/`, not in the theme.

---

## 8. Checklists

**Per deck**
- [ ] Mode (dark/light) and one accent chosen up front
- [ ] Local-first decision confirmed for the venue
- [ ] Images sourced (Unsplash by default), treated consistently (scrim / one abstract bg)
- [ ] No slide is a wall of text
- [ ] Cover / statement slides break up the text slides (good rhythm)
- [ ] Little to no custom CSS, layouts, or components

**Per slide**
- [ ] Big title, minimal support text
- [ ] Fits one of the standard layouts
- [ ] ≤ one accent moment
- [ ] Would still make sense with the body text cut in half
