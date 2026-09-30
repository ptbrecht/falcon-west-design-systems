# Falcon West Material

The design language for Falcon West **apps, CRM, Tools, Academy gates, and other
serial products** (`app.falconwest.com`). It does **not** cover falconwest.com or
falconwestenergy.com — those are separate website systems in `falcon-west/` and
`falcon-west-energy/`.

It is **Material Design 2** — not M3 — because M2's elevation, state-layer and type
models match how these products are actually built, and because the components are
being ported into WordPress rather than pulled from a framework.

This folder's `tokens.json`, `cover.html`, and `manifest.json` are the locked
Claude pack (as shipped). They are Material truth when they disagree with the
earlier UX `DESIGN.md` / specimen.

It ships as a token layer in the `falconwest/mu-core` MU-plugin: an entry point
`styles.css` that imports five token files.

```
styles.css
  @import "tokens/fonts.css";
  @import "tokens/elevation.css";
  @import "tokens/colors.css";
  @import "tokens/typography.css";
  @import "tokens/spacing.css";
```

The stylesheet is **tokens only** — there are no component classes in it. This
system is the reference for those tokens; the plugin remains the shipping source
of truth.

## The three rules that get broken most

**1. The logo orange cannot carry text.** `color-rust-600` (#d2793d) is the mark's
orange. It measures 3.21:1 on white and 3.24:1 on navy — it fails in both
directions. It is a decorative fill: icons, rules, chart fills, tints, icon-only
buttons. The moment a label lands on it or next to it, step down to
`md-primary` (rust-700, 4.84:1) or `md-primary-variant` (rust-800, 6.63:1).
`md-primary-decorative` exists so this is a deliberate choice rather than an
accident.

**2. Rust is primary; navy is secondary.** Buttons, selection and state layers are
rust. App bars, nav and dark bands are navy. The deprecated `--brand-primary`
alias means *navy*, which is the opposite of what its name suggests — see the
deprecation table below before touching it.

**3. Sky is for links.** `link-color` and `link-hover` are the only places
`color-sky-600` and `color-sky-700` belong. Links stay sky on hover; they never
turn rust. `color-sky-500` is available as a decorative and chart fill, and as
the info-container border, but not as a general accent.

## Colour

One theme: **Light**. The palette is a warm rust and a cool navy over near-neutral
greys, on a faintly cool off-white ground. Whites are toned, not pure — the page is
`color-paper-50` (#fcfefe) and cards are white, so a card reads as raised before any
shadow is applied. Ink is `color-ink-900` (#080808), never #000; every elevation
shadow is mixed from it.

Emphasis on light grounds is M2 opacity, not separate greys: `md-text-high` (87%)
for body and headings, `md-text-medium` (60%) for captions, meta and table
secondaries only, `md-text-disabled` (38%) for inactive controls.

Two greys do the outlining, and the distinction matters:

| token | ratio on white | what it may do |
| --- | --- | --- |
| `md-outline` | 1.37:1 | dividers, outlined-card edges — decorative only |
| `md-outline-strong` | 3.45:1 | the border of an input, select or outlined button |

Using `md-outline` to bound a control is the most common accessibility failure in
this system. It fails WCAG 2.2 1.4.11 by a wide margin.

### There is no dark theme

This needs saying plainly, because the name suggests otherwise. What exists is a
**dark surface role set** — navy used as a dark ground, with its own accents and
emphasis levels:

```
md-surface-dark            navy-900   white on it: 10.41:1
md-surface-dark-variant    navy-700   the raised step
md-on-surface-dark         white
md-accent-on-dark          rust-400   4.67:1 on navy
md-accent-on-dark-alt      sky-300    6.04:1 on navy
md-outline-on-dark         24% white  decorative, 1.99:1
md-outline-strong-on-dark  60% white  controls, 4.85:1
md-text-medium-dark        70% white  6.01:1
md-text-disabled-dark      50% white  3.90:1, disabled only
```

That set is for a navy band inside a light page — a footer, a hero, a nav rail. It
is **not** a dark mode. There is no `prefers-color-scheme` block, no `[data-theme]`
override, and no dark value for `md-background`, `md-surface`, `md-surface-variant`
or any semantic container. A product that needs a real dark mode needs those
defined first, and it should be built on the navy ground this set already
establishes rather than on a neutral black — a near-black ground would make the
logo orange, which already fails on navy at 3.24:1, fail harder.

### Semantic containers

Four background / border / text triples: success, warning, danger, info, plus a
brand triple in rust. Every text-on-fill pairing clears 4.5:1. Three of the
borders do not clear 3:1 on their own fill — `semantic-warning-border` (2.60:1),
`semantic-brand-border` (2.72:1) and `semantic-info-border` (2.81:1). They are
container edges, which is fine, but do not reuse them to bound a control.

### Focus

Focus is **geometry, not a tint**: a 2px navy ring at a 2px offset. Navy reads at
10.41:1 against white surfaces, and the offset is what makes it work over a rust
button too — the ring lands on the surface behind, not on the fill. Drawn inset on
a rust-700 fill it measures 2.15:1 and fails, so `focus-ring-offset` is not a
decorative value. Text fields are the documented exception: their 2dp rust-700
active border is itself the indicator.

The deprecated `--focus-ring` alias points at a 12% wash. A wash is not a focus
indicator.

## Type

**Raleway** carries the entire Material type scale, as a variable font across
weights 100–900 with a matching italic. **Crimson Text** is vendored alongside it
for editorial long-form and is available as the `editorial` family; no scale style
uses it, so a consumer opts into it deliberately.

Two departures from stock M2, both intentional:

- Display sizes are fluid and capped far below M2's 96px / 60px, which nothing here
  would ship. `h1` runs `clamp(2.5rem, 5vw + 1rem, 4rem)`; static equivalents are
  declared for email, PDF, PPTX and canvas, and those are the values recorded in
  this system.
- `h1` and `h2` run at weight 400 rather than M2's 300. Raleway Light goes thin and
  washy above 40px.
- `body1` tracking is 0, not M2's 0.5px — that default fights Raleway across a full
  paragraph.

`caption` at 12px is the floor for anything a user has to read.

## Space and shape

A 4dp baseline grid, `space-1` through `space-10` (4px to 128px). Content maxes at
`container-max` 1200px. Any control is at least `touch-target` 48px of hit area,
however small it is drawn.

The shape scale is where this system stops looking like default Material:

```
shape-large    0px    cards, modals, banners, sheets, app bar
shape-small    4px    buttons, inputs, selects, chips, menus
shape-medium   4px
shape-pill     999px  toggles and pills only
shape-circle   50%    avatars, FABs, status dots
```

Large surfaces are **square**. Controls are softly rounded. `shape-large` being
smaller than `shape-small` is not a bug — square cards against 4dp buttons is the
intended slightly-industrial read, and it is the fastest way to tell Falcon West
Material apart from a stock Material theme. Do not round the cards.

## Elevation and motion

M2 umbra / penumbra / ambient shadows at dp 0, 1, 2, 3, 4, 6, 8, 12, 16 and 24 —
M2 defines no others, so the gaps are correct. All three layers are mixed from
ink-900. Cards rest at `elevation-1`, the app bar at `elevation-4`, menus and open
selects at `elevation-8`, dialogs at `elevation-24`, and nothing sits above a
dialog.

Motion tokens live in the plugin but cannot be recorded in this system, which has
no motion family. For reference:

```
--motion-standard      cubic-bezier(0.4,0,0.2,1)
--motion-decelerate    cubic-bezier(0,0,0.2,1)
--motion-accelerate    cubic-bezier(0.4,0,1,1)
--motion-duration-short   150ms
--motion-duration-medium  250ms
--motion-duration-long    375ms
```

There is also an `fw-ripple` keyframe (scale 0→1, opacity .36→0). The system's
motion policy is explicit and worth keeping: **every transition and animation is
decorative — no information is conveyed by motion alone.** A global
`prefers-reduced-motion` rule collapses all of it to 1ms, and consumers must not
re-enable motion above that rule.

## Iconography

The system defines no icon set. Icons take their colour from the text they sit
with, and an icon-only button is the one place the logo orange may fill a control —
because nothing is written on it. Give every icon-only button an `aria-label`, and
the full 48px `touch-target` regardless of the glyph's drawn size.

## Deprecated aliases — remove after 2027-02-01

These exist only so pre-Material screens keep rendering. **Do not use them in new
work, and do not repoint them.** `--brand-primary` means navy; flipping it to
`--md-primary` would silently turn every navy surface orange. Migrate consumers to
the `md-*` roles explicitly instead. They are recorded here rather than as live
tokens so that nothing new picks them up by browsing this system.

| deprecated | points at |
| --- | --- |
| `--brand-primary` | `--md-secondary` |
| `--brand-primary-hover` | `--md-secondary-variant` |
| `--brand-highlight` | `--md-primary` |
| `--brand-highlight-hover` | `--md-primary-variant` |
| `--brand-accent` | `--color-sky-500` |
| `--brand-accent-hover` | `--color-sky-600` |
| `--brand-rollover` | `--color-sky-500` |
| `--brand-navy` | `--color-navy-900` |
| `--text-heading` | `--md-text-high` |
| `--text-body` | `--md-text-high` |
| `--text-muted` | `--md-text-medium` |
| `--text-on-dark` | `--md-text-high-dark` |
| `--text-on-brand` | `--md-on-primary` |
| `--surface-page` | `--md-background` |
| `--surface-card` | `--md-surface` |
| `--surface-navy` | `--md-surface-dark` |
| `--surface-sunken` | `--md-surface-variant` |
| `--border-default` | `--md-outline` |
| `--border-strong` | `--md-outline-strong` |
| `--button-fill` | `--md-primary` |
| `--button-fill-hover` | `--md-primary-variant` |
| `--focus-border` | `--md-primary` |
| `--focus-ring` | `--md-layer-primary-focus` (deprecated on its own terms — a 12% wash is not a focus indicator) |
| `--shadow-card` | `--elevation-1` |
| `--shadow-elevated` | `--elevation-8` |
| `--size-display-xl` | `--md-h2-size` |
| `--size-display-lg` | `--md-h3-size` |
| `--size-display-md` | `--md-h4-size` |
| `--size-display-sm` | `--md-h5-size` |
| `--size-body-lg` | `--md-subtitle1-size` |
| `--size-body-md` | `--md-body1-size` |
| `--size-body-sm` | `--md-body2-size` |
| `--size-caption` | `--md-caption-size` |
| `--lh-tight` · `--lh-heading` · `--lh-body` | 1.1 · 1.25 · 1.5 |
| `--tracking-display` | 0px |
| `--tracking-eyebrow` | `--md-overline-tracking` |
| `--radius-sm` · `--radius-md` · `--radius-lg` | `--shape-small` · `--shape-medium` · `--shape-large` |
| `--radius-pill` · `--radius-control` | `--shape-pill` · `--shape-small` |

## What this system does not yet hold

Recorded so nobody assumes it was checked and found absent.

**Fonts.** No font binaries. The plugin self-hosts `Raleway-Variable.ttf`,
`Raleway-Italic-Variable.ttf` and six Crimson Text statics under
`assets/fonts/`, with paths declared relative to `tokens/`. Both families are
also on Google Fonts, which is what previews here load.

**Logos and icons.** No assets. Nothing in this system approximates the Falcon
West mark — where a logo would go, use plain type and a note.

**Components.** No component bundle. A separate handoff bundle
(`design_handoff_falcon_west_wordpress`) holds 15 React reference components; the
plan is to port it into mu-core as a CSS component layer plus PHP render helpers.
Until that lands, this system is tokens and guidance.

**A dark theme**, as described above.
