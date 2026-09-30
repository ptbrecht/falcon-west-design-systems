# Falcon West CRM — Material light tokens (0.1.64)

**Product:** `wp-plugin-falcon-west-crm` (Tools → Falcon West CRM).  
**Scope:** House **Material** light face only. Not Field (scrapped). Not Pylon.  
**Layout:** unchanged — paint + theme only. Home Screen icon **E** stays.

**Sources:** `/workspace/brand/material-design-language.md`, `/workspace/brand/crm-tools-material-direction.md`.  
**Peter locks (0.1.64):** Appearance default = **System**; mobile status/safe-area **always black**; desktop header **theme-aware** (light chrome in Light).

---

## Settings → Appearance (0.1.64)

| Option | Behavior |
|---|---|
| **Dark** | Existing dark shell (today’s face). |
| **Light** | This token set — `.fw-crm[data-theme="light"]` or `html.fw-crm-theme-light`. |
| **System** | **Default.** Follows `prefers-color-scheme` until the user overrides. Light OS → Light tokens; Dark OS → Dark shell. |

Segmented control order: **Dark | Light | System**. Ship with **System** selected until the user picks Dark or Light.

Caption under control (Settings mock / UI copy):  
*“Follows your device until you choose Dark or Light.”*

---

## Mobile chrome lock (always black)

On phone (Dynamic Island / notch / status bar / safe-area top):

| Layer | Color | Notes |
|---|---|---|
| Status + safe-area + mobile top bar | `#000000` (ink `#080808` OK as near-black) | **Always**, even when `theme=light` |
| Content below that chrome | Light tokens (paper / white / navy chips / rust CTA) | Light paint starts **only below** the black chrome |

- Edge-to-edge black under the island — no light bleed into status blur.
- **Island clearance (P0):** black chrome height ≥ `safe-area-inset-top` + title row. Titles must **not** sit under the island.
- Use generous `padding-top` inside the black bar (island ~47–54px + ~8–12px nudge) so “Falcon West” / menu / search sit fully below the pill.

CSS hint: `.fwcrm-mobile-chrome` → `padding-top: max(54px, calc(env(safe-area-inset-top, 47px) + 12px))`; `theme-color` / meta status bar style black on mobile.

Accent compare (Peter hold rust; UX B/C): see `accent-options.md` + `accent-options-vs-sky.png`.

---

## Desktop header (theme-aware)

Horizontal **top bar** follows theme — **not** always-black, **not** always-navy.

| Mode | Top header | Notes |
|---|---|---|
| **Light** | Paper `#fcfefe` or white `#fff`; ink text `rgba(8,8,8,0.87)`; borders `#dcdcdc` / `#8a8a8a` | Search + segmented controls light-outlined; rust ADD stays |
| **Dark** | Dark chrome (existing dark shell) | Unchanged dark header |
| Sidebar (left nav) | May remain Material navy `#15445D` | Only the **horizontal** top bar flips to light |

Do **not** keep navy on the desktop top bar in Light. Do **not** invent always-black on desktop.

---

## Light token table (literal)

| Role | Token | Hex / value |
|---|---|---|
| bg / page | `--md-background` / paper-50 | `#fcfefe` |
| surface / cards | `--md-surface` | `#ffffff` |
| surface-variant | `--md-surface-variant` | `#ececec` |
| text high | `--md-text-high` | `rgba(8,8,8,0.87)` · ink `#080808` |
| text muted | `--md-text-medium` | `rgba(8,8,8,0.60)` |
| text disabled | `--md-text-disabled` | `rgba(8,8,8,0.38)` |
| border decorative | `--md-outline` | `#dcdcdc` |
| border interactive | `--md-outline-strong` | `#8a8a8a` |
| desktop top bar (Light) | `--fwcrm-chrome` | `#fcfefe` / `#fff` + ink `rgba(8,8,8,0.87)` + borders `#dcdcdc`/`#8a8a8a` |
| sidebar (left nav) / COMMERCIAL chip | `--md-secondary` navy | `#15445D` |
| mobile status / safe-area / top bar | `--fwcrm-mobile-chrome` | `#000000` (always) |
| CTA fill (labeled) | `--md-primary` rust-700 | `#a85f2e` |
| CTA / on-primary text | `--md-on-primary` | `#ffffff` |
| decorative / logo orange | `--md-primary-decorative` rust-600 | `#D2793D` — never text-bearing |
| navy chrome | `--md-secondary` | `#15445D` — **never a button fill** |
| links / Drive (prefer) | `--md-link` sky-600 | `#2d78ad` |
| links hover | `--md-link-hover` sky-700 | `#266690` — sky stays sky |
| lock-link (legacy dark) | `--md-link-lock` | `#5aa0cc` — see note |
| PERSONAL chip | bg / text | `#e3f1fa` / `#266690` |
| COMMERCIAL chip | bg / text | `#15445D` / `#ffffff` |
| field rest border | | `#8a8a8a` 1px |
| field focus | | 2px `#a85f2e` |
| warning / danger | | `#8a5e10` / `#b6432f` |
| drag highlight | rust-100 | `#fbe9db` |
| logo orange | rust-600 | `#D2793D` — **decorative only**, never text-bearing fill |

**Font:** Raleway (UI + display). Fallback: Inter / system-ui. Shared: [`../fonts/Raleway.ttf`](../fonts/Raleway.ttf).  
**Radii (Claude lock):** `--shape-large` **0** for cards / modals / app bar; `--shape-small` **4px** for controls. Menus at elevation-8. Focus: 2px navy + 2px offset.  
**Source of truth:** [`tokens.json`](tokens.json) + [`DESIGN.md`](DESIGN.md).

---

## Lock-link sky note

Current dark CSS uses `--fwcrm-sky-600: #5aa0cc` (readable on dark charcoal).

| Color | On `#ffffff` | Verdict |
|---|---|---|
| `#2d78ad` (Material sky-600) | **~4.77:1** | Prefer for body links / Drive on light — clears AA normal text |
| `#5aa0cc` (dark lock-link) | **~2.86:1** | **Fails** AA body text on white |
| `#266690` (sky-700) | ~6.20:1 | Hover / PERSONAL chip text OK |

**Recommendation:** Light theme links → `#2d78ad` (hover `#266690`). Keep `#5aa0cc` for lock icons / non-text glyphs only if needed — not labeled link text.

---

## Contrast risks (light vs dark)

| Pair | Approx ratio | Risk |
|---|---|---|
| `#5aa0cc` on white | 2.86:1 | **Fail AA** body — do not use for Drive/links in Light |
| Muted `rgba(8,8,8,0.60)` on white | ~5.3:1 effective | OK for captions/meta only — never body paragraphs |
| Disabled `rgba(8,8,8,0.38)` | ~2.6:1 | Intentional disabled; not for readable content |
| Decorative `#dcdcdc` on white | ~1.35:1 | Dividers/card edges only — never control bounds |
| Interactive `#8a8a8a` on white | ~3.45:1 | Meets non-text UI (≥3:1); use for field/button outlines |
| Rust-700 `#a85f2e` + white label | ~4.84:1 | **AA OK** for CTA |
| Logo orange `#D2793D` + white | ~3.21:1 | **Fail** text — decorative / icon only |
| White on navy `#15445D` | ~10.4:1 | Sidebar / COMMERCIAL chip OK |
| Ink on light top bar `#fcfefe` | ~19.8:1 | Desktop Light header OK |
| White on mobile black `#000` | 21:1 | Mobile top chrome OK |
| Ink on paper | ~19.8:1 | Fine |
| Warning `#8a5e10` / danger `#b6432f` on white | ~5.7 / ~5.5 | OK for captions |

**Dark shell:** sky `#5aa0cc` works on dark; remapping sky is the main Light breakage — do not inherit `#5aa0cc` for body links.

---

## CSS enqueue

After Material / existing CRM CSS:

```html
<link rel="stylesheet" href="…/light-tokens.css">
```

Scope: `.fw-crm[data-theme="light"]` **or** `html.fw-crm-theme-light`.  
For System: set `data-theme` from `matchMedia('(prefers-color-scheme: light)')` until user override is stored.

---

## Hard locks

- Appearance default = **System**.
- Mobile status/safe-area/top bar = **always `#000`**, light paint only below.
- Desktop header = **theme-aware**: light chrome in Light; dark chrome in Dark. Sidebar may stay navy. Not always-black on desktop.
- No Field forest / Field orange `#FF5700`. No inventing Field green.
- Navy never a CTA / button fill; rust-700 only labeled primary.
- Logo orange never on buttons with text.
- Cards are square (`0`). Controls are `4px`. Do not use the old 4px-card rule.
