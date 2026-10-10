# Falcon West Material — Design Language Specification

> **Retired leftover.** Moved out of the Material root so it is not mistaken for the source of truth.
> Prefer the Claude pack one level up: [`../tokens.json`](../tokens.json), [`../README.md`](../README.md),
> [`../cover.html`](../cover.html), [`../manifest.json`](../manifest.json). If this file disagrees
> with those files, the Claude pack wins.

A complete, image-free description of the Falcon West design language. Every value here is
literal and buildable: hex codes, pixel dimensions, ratios, cubic-bézier curves. Nothing is
left to interpretation, and nothing requires seeing a rendered screen.

The system is **Material Design 2**, retuned for an insurance brand. If a behavior is not
described here, the correct answer is "whatever Material 2 specifies."

**Scope — apps only.** Material is for apps, CRM, Tools, Academy gates, and other serial
team products (`app.falconwest.com`). It does **not** cover falconwest.com or
falconwestenergy.com. Those are separate website systems in `falcon-west/` and
`falcon-west-energy/`. Token roles in [`../tokens.json`](../tokens.json) are the source of truth when this
file and [`specimen.html`](specimen.html) disagree.

**Locked roles (Claude pack):** `--md-primary` = rust-700; decorative = rust-600; navy is
secondary **chrome only** (never a button fill); sky links stay sky on hover; cards /
modals / app bar use `--shape-large` 0; controls use `--shape-small` 4; menus sit at
elevation-8; focus is 2px navy + 2px offset; ink `#080808`; paper `#fcfefe`.

---

## 0. The one-sentence read

White and near-white surfaces, **square cards and large containers** (radius 0), softly-rounded
(4px) controls, rust-orange as the single action color, navy as chrome only (never a button
fill), Raleway throughout, and Material's umbra/penumbra/ambient shadow stack for depth. The
intended impression is **slightly industrial, not friendly-rounded** — a working tool for
professionals, not a consumer app or a marketing site.

---

## 1. Color

### 1.1 Source palette (literal hex)

| Token | Hex | Role |
|---|---|---|
| `--color-rust-800` | `#8a4d25` | Darkest rust. Text on light: 6.63:1 |
| `--color-rust-700` | `#a85f2e` | **Primary.** All text-bearing rust fills. 4.85:1 on white |
| `--color-rust-600` | `#D2793D` | **The logo orange.** 3.23:1 — decorative fill ONLY |
| `--color-rust-400` | `#e0a06e` | Accent on navy (4.67:1 on navy-900) |
| `--color-rust-100` | `#fbe9db` | Brand container background |
| `--color-sky-700` | `#266690` | Info text |
| `--color-sky-600` | `#2d78ad` | Link default |
| `--color-sky-500` | `#3D96D2` | Info border, brand secondary accent |
| `--color-sky-300` | `#9fcbe8` | Accent on navy (6.04:1) |
| `--color-sky-100` | `#e3f1fa` | Info container background |
| `--color-navy-900` | `#15445D` | **Secondary chrome.** App bar, dark surfaces, focus ring. Never a button fill. |
| `--color-navy-700` | `#1e5c7d` | Dark surface variant |
| `--color-ink-900` | `#080808` | Text base (all text opacities derive from this) |
| `--color-charcoal-700` | `#434343` | |
| `--color-charcoal-500` | `#6b6b6b` | |
| `--color-charcoal-300` | `#a3a3a3` | |
| `--color-line-300` | `#8a8a8a` | Interactive bounds (3.41:1) |
| `--color-line-200` | `#dcdcdc` | Decorative dividers (1.35:1) |
| `--color-line-100` | `#ececec` | Surface variant |
| `--color-paper-50` | `#fcfefe` | Page background (a hair cooler than white) |
| `--color-white` | `#ffffff` | Card/surface |
| `--color-success` | `#3f7d4a` | |
| `--color-warning` | `#8a5e10` | |
| `--color-danger` | `#b6432f` | |

### 1.2 Role mapping

```
--md-primary            = rust-700  #a85f2e   /* text-bearing actions */
--md-primary-variant    = rust-800  #8a4d25
--md-primary-light      = rust-400  #e0a06e
--md-primary-decorative = rust-600  #D2793D   /* logo orange, no-text-on-it only */
--md-on-primary         = #ffffff
--md-secondary          = navy-900  #15445D   /* chrome only — never a button fill */
--md-secondary-variant  =           #0e3247
--md-on-secondary       = #ffffff
--md-background         = paper-50  #fcfefe
--md-surface            = #ffffff
--md-surface-variant    = line-100  #ececec
--md-error              = danger    #b6432f
--md-link               = sky-600   #2d78ad
--md-link-hover         = sky-700   #266690   /* sky stays sky */
```

### 1.3 The rust rule — the single most important constraint

The logo orange `#D2793D` measures **3.23:1** against white. That clears the 3:1 threshold for
non-text graphics but **fails** the 4.5:1 threshold for text. Therefore:

- `#D2793D` is legal for: icons, rules and dividers, chart fills, tint backgrounds, icon-only
  FABs, decorative borders.
- `#D2793D` is **illegal** for: any fill that carries a text label, any text color.
- Any rust that carries text steps down to `#a85f2e` (4.85:1) or `#8a4d25` (6.63:1).
- On navy `#15445D`, `#D2793D` measures **3.24:1 and is banned entirely**; use `#e0a06e`
  (4.67:1) or `#9fcbe8` (6.04:1).

A build that puts white text on `#D2793D` is wrong even though it looks most "on brand."

### 1.4 Text emphasis (Material opacity model)

All light-surface text is `#080808` at an opacity level, never a different hue:

```
--md-text-high      rgba(8,8,8,0.87)   body copy, headings — the default
--md-text-medium    rgba(8,8,8,0.60)   captions, meta, table secondaries ONLY
--md-text-disabled  rgba(8,8,8,0.38)
--md-divider        rgba(8,8,8,0.12)
```

On dark (navy) surfaces: `rgba(255,255,255,1)` / `0.7` / `0.5`.

Medium emphasis is not a styling choice — it is reserved for genuinely secondary content.
Body paragraphs at 0.6 are a defect.

### 1.5 Outlines — two tiers, not one

```
--md-outline        #dcdcdc  1.35:1  DECORATIVE ONLY (dividers, outlined-card edge)
--md-outline-strong #8a8a8a  3.41:1  BOUNDS INTERACTIVE CONTROLS (WCAG 2.2 1.4.11)
```

Inputs, selects and outlined buttons must never use the decorative hairline as their border.

### 1.6 Semantic containers (bg / border / text triples)

Never improvise these per screen.

| Severity | bg | border | text |
|---|---|---|---|
| success | `#e7f2e9` | `#3f7d4a` | `#2f5f37` |
| warning | `#faf0dc` | `#c98a1f` | `#8a5e10` |
| danger | `#f7e4e0` | `#b6432f` | `#8f3323` |
| info | `#e3f1fa` | `#3D96D2` | `#266690` |
| brand | `#fbe9db` | `#D2793D` | `#8a4d25` |

Every triple clears 4.5:1 text-on-bg.

### 1.7 State layers

Material state layers are an overlay of the interaction color at a fixed opacity:

```
hover 0.04   focus 0.12   pressed 0.10   selected 0.08   disabled 0.38
```

Precomputed over rust-700 `rgb(168,95,46)`:

```
--md-layer-primary-hover     rgba(168,95,46,0.04)
--md-layer-primary-focus     rgba(168,95,46,0.12)
--md-layer-primary-pressed   rgba(168,95,46,0.10)
--md-layer-primary-selected  rgba(168,95,46,0.08)
--md-layer-on-primary        rgba(255,255,255,0.16)
--md-layer-on-surface        rgba(8,8,8,0.06)
--md-ripple-light            rgba(255,255,255,0.32)
--md-ripple-dark             rgba(8,8,8,0.16)
```

### 1.8 Links

Sky only, both states. Hover stays sky (`#266690`). Never rust, never navy.

```css
a       { color:#2d78ad; text-decoration:none }
a:hover { color:#266690; text-decoration:underline }
```

### 1.9 Focus indicator — geometry, not a tint

```
--focus-ring-width  2px
--focus-ring-offset 2px
--focus-ring-color  #15445D   (navy)
--focus-ring-color-on-dark #ffffff
```

Implemented as `outline: 2px solid #15445D; outline-offset: 2px`. Navy reads against both
white surfaces and rust fills, so there are **no per-variant exceptions** — one ring
everywhere.

**The one exception:** text fields. Their focus state is a 2px `#a85f2e` border replacing the
1px resting border. That border *is* the indicator; text fields do not also take the navy ring.
Inside compact controls (checkbox, radio, tab, accordion header) the offset is negated
(`outline-offset: -2px`) so the ring stays inside the hit area.

---

## 2. Typography

### 2.1 Families

```
--font-display    "Raleway", sans-serif    (variable, weights 100–900, roman + italic)
--font-body       "Raleway", sans-serif
--font-editorial  "Crimson Text", serif    (400/600/700 + italics; long-form editorial only)
```

Raleway carries the entire UI. Crimson Text appears only in editorial long-form prose — never
in application chrome, labels, or controls.

Weights in use: 300 light, 400 regular, 500 medium, 600 display-medium, 700 display-bold,
800 display-heavy.

### 2.2 Type scale

Display sizes are fluid via `clamp()` and capped well below Material's 96/60px defaults.
h1/h2 run at **weight 400**, not Material's 300 — Raleway Light goes thin and washy above 40px.

| Style | size | weight | tracking | line-height |
|---|---|---|---|---|
| h1 | `clamp(2.5rem, 5vw + 1rem, 4rem)` | 400 | −1px | 1.10 |
| h2 | `clamp(2rem, 3.5vw + 1rem, 3rem)` | 400 | −0.5px | 1.10 |
| h3 | `clamp(1.75rem, 2vw + 1rem, 2.25rem)` | 400 | 0 | 1.15 |
| h4 | `clamp(1.5rem, 1.5vw + 1rem, 1.75rem)` | 400 | 0.25px | 1.20 |
| h5 | 24px | 400 | 0 | 1.25 |
| h6 | 20px | 500 | 0.15px | 1.30 |
| subtitle1 | 16px | 500 | 0.15px | 1.50 |
| subtitle2 | 14px | 500 | 0.10px | 1.50 |
| body1 | 16px | 400 | **0px** | 1.50 |
| body2 | 14px | 400 | 0.25px | 1.43 |
| button | 14px | 500 | 1.25px | — (uppercase) |
| caption | 12px | 400 | 0.40px | — |
| overline | 10px | 500 | 1.50px | — (uppercase) |

`body1` tracking is **0**, not Material's 0.5px: that default fights Raleway across a full
paragraph.

Fixed-width contexts that cannot resolve `clamp()` (email, PDF, PPTX, canvas) use the ceiling
values: h1 64px, h2 48px, h3 36px, h4 28px.

### 2.3 Casing

Uppercase with wide tracking is used for exactly three things: **button labels**
(14/500/1.25px), **tab labels** (same), and **overline/eyebrow** text (10/500/1.5px).
Headings and body are never uppercased.

---

## 3. Space and shape

### 3.1 Spacing scale — 4dp baseline grid

```
--space-1   4px      --space-6   32px
--space-2   8px      --space-7   48px
--space-3  12px      --space-8   64px
--space-4  16px      --space-9   96px
--space-5  24px      --space-10 128px
```

Every dimension in a layout is a multiple of 4. `--touch-target: 48px` is the minimum
interactive hit area. `--container-max: 1200px`.

### 3.2 Shape scale — the deliberate inversion

```
--shape-small   4px    controls: buttons, inputs, selects
--shape-large   0px    cards, modals, banners, app bar, alerts
--shape-pill    999px  chips, badges, extended FAB, switch track
--shape-circle  50%    radio, FAB, state-layer haloes
```

`--shape-large` being **smaller** than `--shape-small` is intentional and is the signature of
this system: **cards and other large surfaces are square; controls are softly rounded.** Do
not normalize this. Do not put 4px on a card.

### 3.3 Elevation — Material's three-shadow stack

Each level is umbra + penumbra + ambient, all in `rgba(8,8,8,…)`:

```
0   none
1   0 2px 1px -1px rgba(8,8,8,.20), 0 1px 1px 0 rgba(8,8,8,.14), 0 1px 3px 0 rgba(8,8,8,.12)
2   0 3px 1px -2px rgba(8,8,8,.20), 0 2px 2px 0 rgba(8,8,8,.14), 0 1px 5px 0 rgba(8,8,8,.12)
3   0 3px 3px -2px rgba(8,8,8,.20), 0 3px 4px 0 rgba(8,8,8,.14), 0 1px 8px 0 rgba(8,8,8,.12)
4   0 2px 4px -1px rgba(8,8,8,.20), 0 4px 5px 0 rgba(8,8,8,.14), 0 1px 10px 0 rgba(8,8,8,.12)
6   0 3px 5px -1px rgba(8,8,8,.20), 0 6px 10px 0 rgba(8,8,8,.14), 0 1px 18px 0 rgba(8,8,8,.12)
8   0 5px 5px -3px rgba(8,8,8,.20), 0 8px 10px 1px rgba(8,8,8,.14), 0 3px 14px 2px rgba(8,8,8,.12)
12  0 7px 8px -4px rgba(8,8,8,.20), 0 12px 17px 2px rgba(8,8,8,.14), 0 5px 22px 4px rgba(8,8,8,.12)
16  0 8px 10px -5px rgba(8,8,8,.20), 0 16px 24px 2px rgba(8,8,8,.14), 0 6px 30px 5px rgba(8,8,8,.12)
24  0 11px 15px -7px rgba(8,8,8,.20), 0 24px 38px 3px rgba(8,8,8,.14), 0 9px 46px 8px rgba(8,8,8,.12)
```

Standard assignments: card 1 (8 on hover if interactive), contained button 2 → 4 on
hover/focus, app bar 4, FAB 6 → 8 on hover, **menus elevation-8**, dialogs 16–24.

Depth is expressed by shadow only. Never by a border *and* a shadow on the same element:
an elevated card has no border; an outlined card has `1px solid #dcdcdc` and elevation 0.

---

## 4. Motion

```
--motion-standard    cubic-bezier(0.4, 0, 0.2, 1)
--motion-decelerate  cubic-bezier(0, 0, 0.2, 1)
--motion-accelerate  cubic-bezier(0.4, 0, 1, 1)
--motion-duration-short   150ms
--motion-duration-medium  250ms
--motion-duration-long    375ms
```

Assignments: color/background/border transitions 150ms standard; shadow and layout
(margin, expansion) 250ms standard; entering elements decelerate; exiting elements accelerate.

**Ripple** (contained buttons, FAB): a circle centered on the pointer, diameter
`2 × max(width, height)`, animating `scale(0) → scale(1)` and `opacity .36 → 0` over
480ms `decelerate`, removed after 500ms. Fill is `rgba(255,255,255,0.32)` on dark fills,
`rgba(8,8,8,0.16)` on light.

```css
@keyframes fw-ripple { from{transform:scale(0);opacity:.36} to{transform:scale(1);opacity:0} }
```

**Motion policy:** every animation in this system is decorative — no information is conveyed
by motion alone. Under `prefers-reduced-motion: reduce`, all durations collapse to 1ms and
iteration counts to 1, globally. Consumers must not re-enable motion above that rule.

---

## 5. Component geometry

Exact measurements. All colors below are the tokens defined above.

### 5.1 Button

Variants: `contained` (default), `outlined`, `text`. Aliases `primary/highlight/accent/
filled` → contained; `outline` → outlined; `ghost/link` → text. There is **no navy button
variant.** Navy is chrome, not a fill.

| Size | height | horizontal padding |
|---|---|---|
| sm | 32px | 12px |
| md | 36px | 16px |
| lg | 42px | 24px |

Shared: `min-width: 64px`, `border-radius: 4px`, inline-flex centered, `gap: 8px` for a start
icon, label 14/500/1.25px uppercase Raleway, `white-space: nowrap`.

- **Contained** — bg `#a85f2e` (rust-700 / `--md-primary`), text `#ffffff`, elevation 2;
  hover bg `#8a4d25`, elevation 4; disabled bg `rgba(8,8,8,0.12)`, text `rgba(8,8,8,0.38)`,
  elevation 0. **Navy is not a button fill** — do not map `color="secondary"` or a `navy`
  alias to a contained navy button.
- **Outlined** — transparent bg, text `#a85f2e`, **border `1px solid #a85f2e`** (the border
  bounds an interactive control, so it must clear 3:1 — never the `#dcdcdc` hairline).
  Horizontal padding reduces by 1px to compensate for the border. Hover adds
  `rgba(168,95,46,0.04)`.
- **Text** — transparent, text `#a85f2e`, padding `0 8px`, min-width 64px, same hover layer.

Focus (all variants): `outline: 2px solid #15445D; outline-offset: 2px`.

### 5.2 ButtonRow

The only sanctioned way to lay out sibling buttons. Flex, `gap: 16px`, wraps by default,
`align: start | center | end` → `justify-content: flex-start | center | flex-end`.
`equalWidth` switches to `grid-auto-flow: column; grid-auto-columns: 1fr; width: fit-content`
so a short label and a long one produce matched widths; alignment then uses auto margins.

**Order convention:** the primary (contained) action sits **rightmost**; secondary
(outlined/text) actions sit to its left.

### 5.3 Card

`background:#ffffff`, `border-radius: 0` (`--shape-large`), `padding: 16px` (or 0 when
unpadded), `color: rgba(8,8,8,0.87)`, shadow transition 250ms standard.
- `elevated` (default): elevation 1, no border. `interactive` raises to elevation 8 on hover.
- `outlined`: `1px solid #dcdcdc`, elevation 0.

### 5.4 Input (text field)

Height **56px** in both variants; `border-radius: 4px`; text 16px Raleway,
`color: rgba(8,8,8,0.87)`.

- **Outlined** (default): transparent bg; resting border `1px solid #8a8a8a`, padding `0 14px`.
  Focus → `2px solid #a85f2e`, padding `0 13px` (compensating so text does not shift).
  Error → `#b6432f` at the same weights.
- **Filled**: bg `rgba(8,8,8,0.06)` → `rgba(8,8,8,0.09)` on focus; no side/top borders;
  bottom border `1px #8a8a8a` → `2px #a85f2e`; radius `4px 4px 0 0`; padding `20px 12px 6px`.

**Floating label** — floats when focused, when the field has a value, or when a placeholder is
present. Outlined: `left 14px → 10px`, `top 18px → −8px`, `font-size 16px → 12px`, with
`background:#ffffff` and `padding: 0 4px` so it notches the border. Filled: `left 12px` fixed,
`top 18px → 8px`, same size change. Color: `rgba(8,8,8,0.6)` resting, `#a85f2e` focused,
`#b6432f` error. Transition 150ms standard. Required fields append ` *` to the label.

**Helper / error text**: 12px, tracking 0.4px, `padding: 4px 14px 0`,
`rgba(8,8,8,0.6)` or `#b6432f`.

### 5.5 Select

Identical box to the outlined Input (56px, 4px radius, 1px `#8a8a8a` → 2px `#a85f2e`), with
`appearance: none`, right padding 40px (39px focused), and a CSS-triangle caret:
`width:0; height:0; border-left:5px solid transparent; border-right:5px solid transparent;
border-top:5px solid rgba(8,8,8,0.6)`, absolutely positioned `right:14px; top:24px`.
Background is `#ffffff` (outlined) or `rgba(8,8,8,0.06)` (filled). Label z-index 1 so the
notch sits above the border.

### 5.6 Checkbox

40×40px circular state-layer halo (hover fill `rgba(168,95,46,0.04)`) containing an 18×18px
box with `border-radius: 2px`.
- Unchecked: `2px solid rgba(8,8,8,0.87)`, transparent fill.
- Checked / indeterminate: no border, fill `#a85f2e`.
- Checkmark: a 5×9px element with `border-right: 2px` and `border-bottom: 2px` in white,
  `transform: rotate(45deg) translate(-1px,-1px)`.
- Indeterminate: a 10×2px white bar.
Label 16px, `gap: 4px` from the halo. Focus ring inside (`outline-offset: -2px`).

### 5.7 Radio

Same 40×40px halo. Ring 20×20px, `2px solid`, circular. Inner dot 10×10px, scaling
`scale(0) → scale(1)` over 150ms standard. Ring and dot are `#a85f2e` when checked,
`rgba(8,8,8,0.87)` when not, `rgba(8,8,8,0.38)` when disabled.

### 5.8 Switch

58×40px control region. Track 34×14px, pill radius, positioned `left: 10px`:
off `rgba(8,8,8,0.45)`, on `#e0a06e` (rust-400), disabled `rgba(8,8,8,0.12)`.
Thumb halo 36×36px circle sliding `left: 2px → 22px` over 150ms standard, carrying a 20×20px
circular thumb with elevation 1: off `#ffffff`, on `#a85f2e`, disabled `#bdbdbd`.
Label `gap: 8px`.

### 5.9 Chip

Height 32px, `padding: 0 12px`, pill radius, `gap: 8px`, text 14px/0.25px tracking.
- Resting: bg `#ececec`, text `rgba(8,8,8,0.87)`, `1px solid transparent`.
- Hover (clickable): bg `rgba(8,8,8,0.12)`.
- Selected: bg `rgba(168,95,46,0.08)`, text `#8a4d25`, `1px solid #a85f2e`.
Optional delete affordance is a `×` glyph at 16px, opacity 0.6.

### 5.10 Badge

Height 20px, `padding: 0 8px`, pill radius, overline type (10/500/1.5px uppercase).
Tones map straight to the semantic container pairs: primary/rust → brand, sky → info, plus
success, warning, danger; `navy` is `#15445D` with white text.

### 5.11 Alert

`display:flex; align-items:flex-start; gap:12px; padding:12px 16px`, **`border-radius: 0`**
(large shape), and a **4px left border** in the severity's border color. Background and text
come from the severity triple.
Leading icon: 20×20px circle in the border color, white glyph, 12px/700, `margin-top: 2px`.
Glyphs: info `i`, success `✓`, warning `!`, danger `!`, brand `★`.
Title subtitle2 (14/500/0.1px), body body2 (14/400/0.25px/1.43), action block `margin-top:10px`.
Dismiss is a 24×24px button, hover `rgba(8,8,8,0.06)`, radius 4px.
`role="alert"` for danger and warning; `role="status"` otherwise.

### 5.12 FAB

- Regular 56×56px, mini 40×40px, `border-radius: 50%`, icon 22px.
- Extended: same height, `padding: 0 20px`, pill radius, label 14/500/1.25px uppercase,
  `gap: 12px`.
- Elevation 6 → 8 on hover.
- **Fill differs by variant, by the rust rule:** icon-only uses the true logo orange
  `#D2793D` (hover `#a85f2e`) because a white icon on it is a non-text graphic at 3.23:1;
  extended carries a label so it steps down to `#a85f2e` (hover `#8a4d25`).

### 5.13 AppBar

Height 64px (48px dense), `padding: 0 16px`, `display:flex; align-items:center; gap:16px`,
elevation 4, `position: relative; z-index: 2`.
Default color `secondary` → bg `#15445D`, text `#ffffff`. `surface` → bg `#ffffff`,
text `rgba(8,8,8,0.87)`.
Logo image 32px tall (24px dense). Title is h6 (20/500/0.15px). A `flex: 1` spacer pushes the
actions `<nav>` right; actions sit in a flex row with `gap: 8px`.

### 5.14 Tabs

Tab strip is a flex row over a `1px solid rgba(8,8,8,0.12)` bottom rule. Each tab:
`min-height: 48px; min-width: 90px; padding: 0 16px`, label 14/500/1.25px uppercase,
`border-bottom: 2px solid` — `#a85f2e` when active, transparent otherwise — with
`margin-bottom: -1px` so the indicator covers the divider. Active text `#a85f2e`;
inactive `rgba(8,8,8,0.6)`. Hover layer `rgba(168,95,46,0.04)`. `fullWidth` gives each tab
`flex: 1`. Panel padding `16px 0`, body1.

### 5.15 Accordion

Each item is a `#ffffff` surface at elevation 1, **radius 0** (same as cards), no margin
when collapsed. When open it lifts to elevation 2 and gains `margin: 16px 0` — transitioning
over 250ms standard. That vertical separation *is* the open affordance. Do not round the
open panel.
Header: full width, `min-height: 48px`, `padding: 12px 24px`, subtitle1 (16/500/0.15px),
space-between, hover layer `rgba(8,8,8,0.06)`. Caret is a CSS triangle
(`border-left/right: 5px transparent; border-top: 6px solid rgba(8,8,8,0.6)`) rotating
0° → 180° over 250ms. Body: `padding: 0 24px 20px`, body1.

---

## 6. Layout rules

1. **4px grid.** Every margin, padding, gap, width and height resolves to a multiple of 4.
2. **`--container-max: 1200px`** for centered page content.
3. **Flex/grid with `gap`** for all sibling groups — never margins on individual children,
   never whitespace-based inline spacing.
4. **Multi-column regions use `auto-fit`**, e.g.
   `grid-template-columns: repeat(auto-fit, minmax(280px, 1fr))`, so they reflow rather than
   crush at narrow widths. Fixed 3-up/2-up grids are a defect.
5. **Page background is `#fcfefe`; cards are `#ffffff`.** The 2-value difference is the whole
   figure/ground separation on light screens — do not flatten them to the same white.
6. **Sticky action bars.** In tool-style screens, the primary action row stays pinned to the
   bottom of its container so it survives short viewports.
7. **Navy is chrome, rust is action.** Navy fills the app bar and dark bands — **never a
   button fill or button border.** Rust-700 marks the one thing the user should do next on a
   given screen. More than one contained rust button visible at once means the hierarchy is
   wrong.

---

## 7. Accessibility contract

- Text contrast ≥ 4.5:1; large text (≥24px, or ≥19px bold) ≥ 3:1.
- Non-text UI bounds and graphics ≥ 3:1 (WCAG 2.2 §1.4.11) — this is why
  `--md-outline-strong` exists and why `--md-outline` may not bound a control.
- Every interactive element has a hit area of at least 48×48px, even when its painted box is
  smaller (checkbox: 18px box inside a 40px halo inside 48px of row).
- Focus is always visible and always the same: 2px navy, 2px offset (white on dark; the 2px
  rust border on text fields).
- Color is never the sole carrier of meaning: alerts pair color with an icon and a text
  label; validation pairs the red border with error text.
- Motion is decorative only and fully collapses under `prefers-reduced-motion`.
- Uppercase runs are limited to short labels (buttons, tabs, overlines), never sentences.

---

## 8. Prohibitions

Building any of these means the design language has been broken:

1. White (or any) text on `#D2793D`.
2. `#D2793D` anywhere on a navy surface.
3. Rounding cards, modals, banners, app bar, or alerts — they are square, `--shape-large` 0.
4. Rounding controls past 4px (except intentionally-pill chips, badges, extended FABs).
5. Navy as a button fill (contained, outlined, or text). Navy is chrome only.
6. A decorative `#dcdcdc` hairline bounding an input, select, or outlined button.
7. Body copy at `--md-text-medium` (0.6 opacity).
8. Rust or navy links — links are sky, in both states (hover stays sky).
9. A tint or background wash used as a focus indicator instead of the 2px navy ring.
10. Border *and* shadow on the same surface.
11. Any font other than Raleway in application chrome; Crimson Text outside editorial prose.
12. New one-off colors. If a screen needs a color, it exists in §1 or it is not needed.
13. Re-pointing the deprecated aliases (`--brand-primary` etc.). `--brand-primary` means
    **navy**; flipping it to `--md-primary` would silently turn every navy surface orange.
    Migrate consumers to the `md-*` roles explicitly instead. These aliases are removed
    after **2027-02-01**.

---

## 9. Implementation order

1. Import the token files in this order — `fonts`, `elevation`, `colors`, `typography`,
   `spacing` — into a single `styles.css`. Everything downstream is `var(--token)`.
2. Self-host Raleway as a variable font (`100–900`, roman + italic) and Crimson Text at
   400/600/700 + italics, all `font-display: swap`.
3. Build the primitives in §5 in this order: Button → Input/Select → Card → AppBar → the rest.
   Each takes its values from tokens only; no literal hex in component code.
4. Compose screens from §6.
