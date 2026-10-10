# Falcon West Website — Design System

A complete, image-free description of the **website and client-facing** design language for falconwest.com and falconwestenergy.com. Every value here is literal and buildable.

This is **not** the Material / app system. Do not apply Material rules, Material type roles, Material focus, Material casing, or Material shape inversion. If a behavior is not described here, do not borrow it from the app language.

---

## 0. The one-sentence read

Traditional and trust-first: a classic serif voice under a Raleway ExtraBold wordmark, navy as the main brand field, rust only on buttons, sky only on links — established and personal, not trendy. *Serving You Since 1981.*

---

## 1. Brand

Falcon West is an independent insurance brokerage. The site should feel like a long-standing regional firm: warm, personal, "you," tenure over hype. No emoji. No startup chrome. No photo-hero theater. No falcon watermark used as a standalone page background.

**Voice example**

- Headline: Coverage that protects what you've built.
- Body: Falcon West has helped families and businesses in the region find the right coverage since 1981 — no jargon, no pressure.

---

## 2. Color

### 2.1 Source palette (literal hex)

| Token | Hex | Role |
|---|---|---|
| `--color-navy-900` | `#15445D` | **Main brand color.** Nav, dark sections, large brand fields. Never a button fill or button border. |
| `--color-rust-600` | `#D2793D` | **Button fill** (main brand). Filled CTA, or the border of a white outline button. Highlight / rollover accent only — never a dominant background. |
| `--color-rust-700` | `#A85F2E` | Button hover (main brand). |
| `--color-sky-500` | `#3D96D2` | Older decorative / logo / non-a11y Energy fill only. On the main brand, reserved as a link-family accent — not a button, not a background. **Not** the Energy production filled-button color. |
| `--color-sky-600` | `#2D78AD` | Main-brand text hyperlink default. |
| `--color-sky-700` | `#2F78A7` | Energy filled-button rest (a11y floor). |
| `--color-ink-900` | `#080808` | Headings. |
| `--color-charcoal-700` | `#434343` | Body copy. |
| `--color-charcoal-500` | `#6B6B6B` | Muted / caption / helper. |
| `--color-line-200` | `#DCDCDC` | Card hairline, resting field border. |
| `--color-paper-50` | `#FCFEFE` | Page background. On-dark text. |
| `--color-white` | `#FFFFFF` | Cards, outline-button fill, field fill. |

### 2.2 Four color rules (binding)

1. **Navy `#15445D` is the main brand color** — navigation, dark sections, large brand fields. **Never** a button fill. **Never** a button border.
2. **Buttons are always rust orange `#D2793D`** — filled, or white with an orange border. Hover `#A85F2E`.
3. **Sky blue `#3D96D2` is reserved for text hyperlinks** on the main brand. Link color `#2D78AD`. Link hover `#D2793D`.
4. **Rust and sky are highlight / rollover accents only.** Resist rust as "primary." Never a dominant background.

Navy is the brand. Rust is the action. Sky is the link. Do not invert these.

### 2.3 Links (main brand)

```css
a       { color: #2D78AD; text-decoration: underline; }
a:hover { color: #D2793D; }
```

Sky is not a button color on the main brand. Rust is not a link color at rest — only the hover of a text link.

### 2.4 Energy token override

Energy shares type, spacing, components, and navy as the main brand field. Energy **never** uses rust or orange. This is a token override, not a second system.

**Production Energy locks** live in [`../falcon-west-energy/ENERGY-SITE-LOCKS.md`](../falcon-west-energy/ENERGY-SITE-LOCKS.md) and win if this table disagrees. Energy-first overlay: [`../falcon-west-energy/DESIGN.md`](../falcon-west-energy/DESIGN.md).

| Role | Main brand | Energy |
|---|---|---|
| Button fill | `#D2793D` | `#2F78A7` (a11y floor) |
| Button hover | `#A85F2E` | `#266690` |
| Outline button | rust border / rust label | `#2F78A7` border / label |
| Focus border | `#D2793D` | `#2F78A7` |
| Focus ring | `rgba(210,121,61,0.28)` | `rgba(47,120,167,0.28)` |
| Link | `#2D78AD` / hover rust | `#2D78AD` / hover `#2F78A7` |
| Palette | navy + rust + sky accents | **black, white, and blue tones only** |

`#3D96D2` is older decorative / logo / non-a11y fill only — not the production Energy filled-button color.

---

## 3. Typography

Two families. Do not swap them. Do not add a third.

```
--font-display  "Raleway", sans-serif     (ExtraBold 800 headings; Bold 700 buttons)
--font-body     "Crimson Text", serif     (Regular 400 body; Italic tagline / pull-quote)
```

Self-host both. No Google Fonts network dependency at render time.

### 3.1 Scale

| Style | Family | Size | Weight | Tracking | Line-height |
|---|---|---|---|---|---|
| Display xl | Raleway | 56px | 800 | 0.01em | 1.1 |
| Display lg | Raleway | 40px | 800 | 0.01em | 1.1 |
| Display md | Raleway | 30px | 800 | 0.01em | 1.25 |
| Display sm | Raleway | 22px | 800 | 0.01em | 1.25 |
| Eyebrow | Raleway | 12px | 700 | 0.14em | 1.2 · uppercase |
| Button | Raleway | 15px | 700 | 0.01em | 1 · **Title Case** |
| Lead | Crimson Text | 20px | 400 | 0 | 1.6 |
| Body | Crimson Text | 18px | 400 | 0 | 1.6 |
| Pull-quote / tagline | Crimson Text | 20px | 400 italic | 0 | 1.5 |
| Caption | Crimson Text | 14px | 400 | 0 | 1.5 |

Headings `#080808`. Body `#434343`. Muted `#6B6B6B`. On-dark `#FCFEFE`.

Buttons are Title Case — never Material's uppercase 14/500 tracking. Eyebrows are the only uppercase run.

---

## 4. Shape and surface

```
--radius-sm       3px     small chips of chrome
--radius-control  6px     buttons AND fields (they match)
--radius-md       6px     cards
--radius-lg       10px    large panels
--radius-pill     999px   badges only
```

**Cards:** white, `1px solid #DCDCDC` hairline, `6px` radius, shadow `0 1px 2px rgba(8,8,8,.06), 0 4px 12px rgba(8,8,8,.06)`. **No left-border accent stripe.**

**Page:** `#FCFEFE`. Flat color only. No gradients. No photo heroes. No textures. No glassmorphism. No falcon watermark as a standalone background.

---

## 5. Focus

Main brand — 2px orange border + soft 3px orange ring:

```
border: 2px solid #D2793D;
box-shadow: 0 0 0 3px rgba(210,121,61,0.28);
```

Energy substitutes `#2F78A7` / `rgba(47,120,167,0.28)`.

This is **not** the Material navy ring.

---

## 6. Components (main brand)

### 6.1 Navigation

Navy `#15445D` bar, 64–72px tall. This is a brand field, **not a button**. Wordmark "Falcon West" in Raleway ExtraBold white. Tagline "Serving You Since 1981" in Crimson Text Italic, paper-50. In-nav destinations are text links, not rust pills.

### 6.2 Button

Height 44px, horizontal padding 22px, radius 6px, Raleway Bold 15px Title Case.

- **Filled** — background `#D2793D`, text `#FCFEFE`. Hover `#A85F2E`.
- **Outline** — background `#FFFFFF`, text `#D2793D`, `1.5px solid #D2793D`. Hover fill `#A85F2E`, hover text paper-50.
- **Ghost** — transparent, text `#D2793D`, no border. Hover text `#A85F2E`.

Navy is never a button. Sky is never a button on the main brand.

### 6.3 Field

Radius 6px (matches the button). Resting: white fill, `1px solid #DCDCDC`, 16px Crimson Text, label in Raleway 12/700 above the box. Focus: 2px `#D2793D` border + 3px orange ring. Helper / caption `#6B6B6B` Crimson 14.

### 6.4 Tabs

Raleway Bold Title Case on a `1px #DCDCDC` rule. Active tab: `#D2793D` text and a 2px rust underline. Inactive: `#6B6B6B`.

### 6.5 Card

See §4. A card is a surface, not an alert. Do not add a colored left rail.

### 6.6 Badge

Height 22px, padding `0 10px`, radius 999. Raleway 11/700, uppercase, tracking 0.08em. Tones: rust (`#D2793D` / paper), sky (`#3D96D2` / paper), navy (`#15445D` / paper). Pills are badges only — never buttons.

---

## 7. Energy

Label the surface **Falcon West Energy Insurance Solutions**. Reuse the same components. Swap only the tokens in §2.4. If rust appears anywhere on an Energy surface, the system is broken.

---

## 8. Prohibitions

Building any of these means the website language has been broken:

1. Navy as a button fill or button border.
2. Rust as a page or section background.
3. Sky used as anything other than a text hyperlink on the main brand (Energy may use sky as the button / highlight).
4. A third typeface, or swapping Raleway / Crimson Text roles.
5. Gradients, photo heroes, textures, or glassmorphism.
6. Left-border accent stripes on cards or callouts.
7. Rust or orange anywhere on Energy.
8. Material rules: navy focus ring, uppercase 14/500 buttons, rust-700 as "primary for text," 4px/0 shape inversion, opacity-model body copy.
9. Treating rust as the primary brand color.
10. A falcon watermark as a standalone background.

---

## 9. Relationship to Material

The app language (Material 2, retuned) lives in [`../material/README.md`](../material/README.md) and [`../material/tokens.json`](../material/tokens.json). It is a working tool for professionals. This file is the public brokerage. They share a palette and a name. They do not share type roles, button geometry, focus, or shape. Do not reconcile them into one system.
