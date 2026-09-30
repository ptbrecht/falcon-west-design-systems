# HANDOFF — Falcon West CRM Material (0.1.64+)

**For:** Developer (wp-plugin-falcon-west-crm)  
**Not:** Field (scrapped). Not Pylon. House Material only.  
**Not:** falconwest.com or falconwestenergy.com — those are separate website systems.  
**Layout:** unchanged — **theme + colors only** (0.1.64). Home Screen icon **E** stays.  
**In scope beyond paint:** Island padding + rail theme dot only. No Lists toggle / XDate as in-scope.

**Token lock:** [`tokens.json`](tokens.json) and [`DESIGN.md`](DESIGN.md) win over any older 4px-card or navy-contained-button note in this file. Cards are square (`0`). Navy is chrome, never a button fill.

## Paths

All under `/workspace/brand/fw-crm-material-theme/`:

| File | Role |
|---|---|
| `light-tokens.md` | Token table, Appearance default System, mobile black chrome, contrast risks |
| `light-tokens.css` | CSS variables scoped `.fw-crm[data-theme="light"]` / `html.fw-crm-theme-light` — enqueue after Material/CRM CSS |
| `Raleway.ttf` | Local house font |
| `icon-e-192.png` | Home Screen icon E reference |
| `desktop-functions-list-light.html` + `.png` | Dense Functions/Energy list |
| `desktop-card-board-light.html` + `.png` | Board + chips + rust Add + sky Drive + drag rust-100 |
| `desktop-settings-light.html` + `.png` | Settings Appearance: Dark \| Light \| **System** selected |
| `desktop-home-dark-sky-cta.html` + `.png` | Dark **charcoal** board · sky ADD `#2d78ad` (Accent C dark) — no navy |
| `mobile-home-functions-light.html` + `.png` | Stage + cards + rust FAB; **always-black** chrome; **Island-cleared** title |
| `mobile-home-functions-light-sky-cta.html` + `.png` | Same clearance; FAB sky `#2d78ad` — stamp “sky/navy CTA alt — no rust” |
| `mobile-home-functions-dark-sky-cta.html` + `.png` | Dark **charcoal** shell (`#121212` / `#1c1c1c` / `#3a3a3a`) · sky FAB · no navy |
| `accent-options-vs-sky.html` + `.png` | Contact strip: A rust / B navy / C sky (no Field green) |
| `accent-options.md` | Hex + Peter lock C + dark black/charcoal + theme-dot |
| `rail-theme-dot-dark.html` + `.png` | Collapsed **charcoal** rail · « · **white** theme dot under |
| `rail-theme-dot-light.html` + `.png` | Light main + navy rail (light OK) · « · **black** theme dot under |
| `rail-theme-dot-pair.html` + `.png` | Labeled dark charcoal \| light pair |
| `_mock-shared.css` | Mock-only shared chrome (not for enqueue) |
| `icons-064/` | **0.1.64 icon polish pack** — header Add/podium/gear, ⚡ strip, color matrix; **CUT** Pipelines/Functions/Lists rail icons |
| `icons-064/ICON-COLOR-MATRIX.md` | **UX-approved icon color matrix** (desktop/mobile light+dark, header, nav) — paint glyphs from this before Cursor |

## Peter locks (fold into 0.1.64+)

1. **Appearance:** Dark | Light | System. **Default = System** (`prefers-color-scheme`) until user overrides. Caption: *“Follows your device until you choose Dark or Light.”* — **Settings Appearance (incl. System) locked**; do not remove System.
2. **Mobile top bar / status / safe-area (Dynamic Island): ALWAYS `#000` / `#080808` edge-to-edge**, even when app body is light **or** dark charcoal. Theme paint applies **only below** that black chrome.
3. **Island clearance (P0):** Black chrome height ≥ `safe-area-inset-top` + title row. Title (“Falcon West” / “Energy”) and menu/search icons must sit **below** the island — use `padding-top: max(54px, calc(env(safe-area-inset-top, 47px) + 12px))` (island ~47–54px + ~8–12px nudge). **Titles must not sit under the island** or soft-blur into status. No light/charcoal bleed into the island region.
4. **Desktop header = theme-aware:** in Light → light chrome (paper `#fcfefe` / white `#fff`, ink `rgba(8,8,8,0.87)`, borders `#dcdcdc` / `#8a8a8a`); in Dark → **black/charcoal** chrome (`#080808` / `#121212`), **not navy**. **Dark sidebar = charcoal** (`#1a1a1a` / `#121212` / `#2a2a2a`) — **no navy**. Light sidebar may remain navy `#15445D`.
5. **Accent C locked lean:** sky `#2d78ad` for **light + dark** primary FAB/CTAs / Home tile fills (**no rust, no navy primary fills**) once dark shell matches black/charcoal. Do not ship Field green.
6. **Rail theme dot (locked):** On the collapsed sidebar margin, **directly under** the rail collapse chevron (`«`), place a small circle (10–12px) with ~44px hit target and ~8–12px gap under the chevron:
   - Dark charcoal shell → **white** dot → tap switches to light (`aria-label` / tooltip: “Switch to light”)
   - Light shell → **black** dot → tap switches to dark (“Switch to dark”)
   - **Not** a second collapse control. Quick Light↔Dark flip; **System remains Settings-only**.

## Token summary

| Role | Light | Dark (black/charcoal — **no navy**) |
|---|---|---|
| Page | `#fcfefe` | `#121212` |
| Cards / surfaces | `#ffffff` / border `#dcdcdc` | `#1c1c1c` / border `#3a3a3a` |
| Text | ink `#080808` @ 0.87 / 0.60 / 0.38 | `#fff` @ 0.87 / 0.60 |
| Desktop top bar | paper `#fcfefe` + ink | `#080808` / `#000` + light ink |
| Sidebar (left nav) | navy `#15445D` (may stay on light) | charcoal `#1a1a1a` / `#121212` / `#2a2a2a` |
| Mobile chrome | `#000000` always · height ≥ safe-area + title row | same |
| CTA lean (C) | sky `#2d78ad` | sky `#2d78ad` FAB/ADD |
| Links / Drive | `#2d78ad` (hover `#266690`) | `#5aa0cc` on charcoal (readable) |
| PERSONAL | `#e3f1fa` / `#266690` | sky-tint on dark OK (`rgba(45,120,173,0.22)` / `#5aa0cc`) |
| COMMERCIAL | `#15445D` / `#fff` (light) | medium gray / outline `#2a2a2a` / `#4a4a4a` — **not navy** |
| Font | Raleway | Raleway |

**Banned on dark shell:** `#15445d`, `#0e3247`, `#1e5c7d` as chrome / page / card fills.

## Contrast risks

- Sky lock `#5aa0cc` on white ≈ **2.86:1** — **fail AA** body. Prefer `#2d78ad` (~4.77:1). Keep `#5aa0cc` for **icons only on light**; OK for links on dark charcoal.
- Muted text OK for meta only, not body.
- Light top bar uses ink on paper. Dark charcoal uses light ink @ 0.87.
- Rust-700 AA for labeled CTAs (~4.84:1) — legacy A only. Sky `#2d78ad` AA for Option C CTAs on white.
- **Don’t** use logo orange `#D2793D` for buttons.
- **Don’t** invent Field green / `#FF5700`.

## Implement notes

- Resolve System → set `data-theme="light"| "dark"` from `matchMedia('(prefers-color-scheme: light)')`; persist user override.
- Mobile: `.fwcrm-mobile-chrome` uses `--fwcrm-mobile-chrome: #000` **outside** theme flip; `padding-top: max(54px, calc(env(safe-area-inset-top, 47px) + 12px))` so title row clears Dynamic Island.
- Map dark’s `--fwcrm-sky-600: #5aa0cc` → light `#2d78ad` when theme is light (body links).
- Dark theme variables: page `#121212`, surface `#1c1c1c`, border `#3a3a3a`, sidebar `#1a1a1a`, topbar `#080808` — **replace** prior navy tokens.
- Rail theme dot: place in sidebar margin under collapse control; invert fill by resolved theme; wire to same theme setter as Settings (explicit Light/Dark — does not select System).

## Theme rail dot (locked)
- Under sidebar collapse chevron: white on dark, black on light.
- Toggles Light ↔ Dark only. **System** remains Settings-only.


## Icon polish 0.1.64 (locked)

**Pack path:** `/workspace/brand/fw-crm-material-theme/icons-064/` — see `icons-064/README.md`.

1. **Bulk bar tile order:** CSV → Clear → Lock  
2. **Header action order:** Add → Leaderboard → Settings  
3. **Leaderboard:** podium from Flaticon https://www.flaticon.com/free-icon/podium_1152927 → `icons-064/leaderboard-podium.{svg,png}` (+ 24/32/48; white/navy/sky). Official download blocked in pack build → clean mono redraw; attribute Flaticon author from page before ship.  
4. **Settings:** https://www.flaticon.com/free-icon/settings_3524636 → `icons-064/settings-gear.{svg,png}` (same treatment).  
5. **Add:** Material FAB-style simple **+** → `icons-064/add-plus.{svg,png}` (house-drawn).  
6. **Remove ⚡ everywhere** in CRM: UI, backend/i18n strings, website + tab title. Use plain “CRM” / no lightning ornament.  
7. **Pipelines / Functions / Lists section icons: CUT** — do not invent funnel/sliders/bullets rail slots. Replace only glyphs that already exist.
8. **Home Screen / PWA install icon:** **none** — do not add (Peter 2026-09-22).  

**Accent C dark comps (confirmed):** `mobile-home-functions-dark-sky-cta.png`, `desktop-home-dark-sky-cta.png` (black/charcoal + sky CTA).

## Peter locks (2026-09-22 evening)

- **No Home Screen / PWA install icon** — does not exist; do not add. Drop E vs quad Home Screen question. Sunrise E pack is archived/irrelevant for install.
- **Quad mark** = **favicon + in-app logo only** (`crm-app-icon/`). Wire favicon.ico / 32 / header mark. Skip apple-touch / manifest Home Screen push unless already required elsewhere — do not introduce install-to-home.
- **Accent C** sky `#2d78ad` for light + dark on black/charcoal shell — Developer shipping assumption after Peter skip.

## CUT — Pipelines / Functions / Lists section icons (Peter 2026-09-22)


## LOCKED — Energy + wp-admin glyphs (Peter 2026-09-22)

| Role | Choice | Asset |
|---|---|---|
| **Energy tile** (replace ⚡) | **A** outline oil drop | `icons-064/ship/energy-a-oil-drop.{svg,png}` |
| **wp-admin menu** | **D** Dashicon-style chart | `icons-064/ship/admin-d-dashicon-chart.{svg,png}` |

Colors: `icons-064/ICON-COLOR-MATRIX.md`. Never multicolour quad in wp-admin menu.

**Do not ship** funnel / sliders / bullets as new rail icons. `icons-064/ship/pipelines-*` etc. are archived.

**Glyph allowlist:** header Add → Leaderboard → Settings · existing mobile tile glyphs (recolor) · Energy bolt→pick · wp-admin Dashicon (never quad). Colors: `icons-064/ICON-COLOR-MATRIX.md`.


## 0.1.64 HARD ALLOWLIST (Peter — do not expand)

**Only** these changes. Do **not** invent extra controls, screens, copy, or polish.

1. Theme System / Light / Dark + Settings Appearance + sidebar theme-dot; dark shell black/charcoal (no navy); sky accents; mobile always-black chrome + Island nudge; desktop theme-aware top bar
2. Mobile Lists toggle; XDate on rows
3. Bulk bar CSV → Clear → Lock; header Add → Leaderboard → Settings + locked header icons
4. **CUT** Pipelines/Functions/Lists section icons — no new rail glyphs
5. Strip ⚡ everywhere; quad mark = favicon + in-app logo only
6. **No** Home Screen / PWA install icon

Out of scope: any other UX, layout moves, new features, or “nice to have” chrome.
