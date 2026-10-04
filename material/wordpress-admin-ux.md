# Falcon West — WordPress admin UX (Cove overlay)

**Scope:** wp-admin screens for Falcon West plugins (Tools, Intake, Markets,
CRM settings desks, Academy, and future serial plugins). **Not** the public
portal, **not** CRM’s app shell, **not** falconwest.com / falconwestenergy.com.

**House reference:** `wp-plugin-falcon-west-tools` — the **Cove WP Admin
Overlay** (`.fw-admin` + twin `fw-admin.css` / `fw-admin-unsaved.js` shared
byte-identical with FW Intake). Copy patterns from Tools; keep Intake twin
in lockstep when the overlay file changes.

This is **WordPress admin host chrome with a Falcon West house overlay** —
not a Material app shell. Keep `#wpadminbar`, `#adminmenu`, Screen Options,
core list tables, and the gray canvas. Paint and hierarchy live under
`.wrap.fw-admin` only.

**Related:** Material tokens ([`tokens.json`](tokens.json),
[`README.md`](README.md)) supply the hex roles; app placement lives in
[`PATTERNS.md`](PATTERNS.md). CRM’s *app* face is a Material variant —
[`CRM-FACE.md`](CRM-FACE.md) — separate from this wp-admin doc.

---

## 1. What this is / is not

| Is | Is not |
| --- | --- |
| WP menu, submenu, `.wrap`, `.form-table`, `.notice`, `.button` | Full Material app bar / rail / FAB chrome |
| Scoped overlay under `.fw-admin` | Restyling `#wpadminbar` or `#adminmenu` |
| Rust-700 primary **admin** CTAs | Logo orange `#D2793D` on labeled buttons |
| Sky links inside plugin content | Navy fills on buttons, tabs, or switches |
| One Save on Type S settings screens | Auto-save, second competing Save, invented leave-guard copy |

---

## 2. Menu & settings structure

**Tools model (house reference)**

- One top-level menu (`FW Tools`, Dashicons hammer, position ~58).
- Visible submenu in a stable order; **Health last**.
- Reference labels (Tools): **Settings → Templates → Activity → Transfers →
  Costs → Health**.
- First submenu reuses the top-level slug so “Settings” is the landing desk.
- Retired / folded desks stay as **hidden** slugs under parent `''` (empty
  string — never `null`) and **redirect** to Settings (or the right live
  desk). Bookmarks must not 404.
- Capability: lowest capability of any submenu on the top-level so staff
  still see the menu; Settings itself may refuse non-admins politely.

**Do**

- One product → one top-level menu (or a clear shared parent). Collapse
  micro-tools into Settings panels rather than new top-level items.
- Put operational desks (Activity, Transfers, Costs) as siblings; put
  diagnostics as **Health** last.
- Redirect retired slugs; do not leave dead menu entries.

**Don’t**

- Spawn a new top-level for every feature.
- Put Health in the middle of the list.
- Register hidden pages with `null` parent (PHP 8.1+ `plugin_basename`
  footgun).
- Use the multicolour CRM quad mark as a wp-admin menu icon (Dashicon /
  mono glyph only — see CRM handoff glyph locks).

---

## 3. Page chrome under `.wrap.fw-admin`

```
.wrap.fw-admin
  h1                    ← one page title (ink + optional 4px navy left rule)
  p.description         ← what this desk is for
  settings_errors()     ← WP notices after save
  [data-fw-unsaved-notice]  ← Type S dirty warning (hidden until dirty)
  form[data-fw-unsaved]     ← Type S only
    … Heading + Toggle panels / tables …
    submit_button( 'Save Settings' )   ← ONE primary Save, bottom
```

| Element | Lock |
| --- | --- |
| Root | `.wrap.fw-admin` on every visible plugin admin screen that opts into Cove |
| `h1` | One per screen; ink `#080808`; 23px / weight 400; optional `border-left: 4px solid` navy `#15445D` + 12px pad |
| `h2` / `h3` | Ink; 14px/600 and 13px/600 — section labels, not a second page title |
| Help / muted | `rgba(8,8,8,0.60)` — `.description` / `.fw-admin__muted` |
| Content links | sky-600 `#2d78ad` → hover sky-700 `#266690` (not buttons / nav-tabs) |
| Primary button | `.button-primary` → rust-700 `#a85f2e` / hover rust-800 `#8a4d25` / white label |
| Focus on primary | White + navy ring (`0 0 0 1px #fff, 0 0 0 3px #15445D`) — not a wash |
| Tabs (when used) | Active = rust text + 2px rust underline; **never** a navy fill |
| Cards / postboxes | White surface, 1px `#c3c4c7` (or `--md-outline`) border |
| Fonts | **WP admin fonts** — no Raleway / Crimson in wp-admin overlay |

Enqueue `fw-admin.css` only on your plugin’s hooks / page slugs. Twin file
with Intake: edit both or neither.

---

## 4. Cards & Heading + Toggle panels

**Cards**

- Prefer `.fw-admin__card` or WP `.postbox` — white, 1px border, modest
  padding (12×16). Square / soft WP corners; do not invent Material
  elevation stacks in admin.
- Status text: `.fw-admin__ok` / `__danger` / `__warning` (success /
  danger / warning tokens).

**Heading + Toggle panels (Tools Settings / Health; Intake Settings)**

- Native `<details class="fwt-settings-panel">` (or Intake twin class).
- **Independent** panels; **all closed on first paint** unless a panel
  must show a notice the admin needs immediately.
- Open state remembered in **page-owned** `localStorage` (Settings and
  Health never share one key).
- Panels **only wrap** — do not move fields between sections when adding
  chrome; keep names, sanitizers, and the one Save.
- Panel chrome may live in a page-local `<style>` using
  `var(--token, #hex)` — **do not** casually edit the shared
  `fw-admin.css` for one-off panel layout.

**Do:** collapse long Settings into panels; keep field identity stable.
**Don’t:** accordion that fights the one-form Save; one-open-only panels
on Settings (Templates / Forms Library accordion is a different pattern).

---

## 5. Toggles & switches

| Control | Spec |
| --- | --- |
| Featured on/off | `.fw-admin__switch` — **36×20**; track gray off / **rust-700 on**; white thumb; navy focus ring |
| Checkboxes | `accent-color` rust-700 |
| Unlock-gated secrets | Disabled until **Unlock**; Save of other fields must not wipe a locked value |

**Don’t:** navy or sky as the switch “on” fill in wp-admin; oversized
Material 56px fields; logo orange on the track.

---

## 6. Notices

- Keep **WP notice shape** (`.notice`, `.notice-success` / `error` /
  `warning`). Overlay only retints the left border to house success /
  danger / warning.
- After save: `settings_errors()` / standard updated notice.
- Type S dirty line: inline warning under the `h1`,
  `data-fw-unsaved-notice`, hidden until dirty — copy **You have unsaved
  changes.** (informational; not a second Save).
- Errors that block an action (e.g. Unlock required) go through
  `add_settings_error` before output.

**Don’t:** toast-only critical failures; invent a Material snackbar host
inside wp-admin; restyle notices into full-bleed app banners.

---

## 7. Save, leave guard, and sticky bars

### Type S (settings that persist options) — house default

Tools Settings and Intake Settings / AgencyZoom:

1. **One** `<form method="post" data-fw-unsaved>`.
2. **One** primary `submit_button( 'Save Settings' )` at the **bottom**.
3. Leave guard (`fw-admin-unsaved.js`, twin-locked):
   - Dirty on `input` / `change` (skip button/submit/reset and
     `[data-fw-unsaved-ignore]`).
   - Cleared on `submit`.
   - Admin-link leave: exact confirm copy
     **You have unsaved changes. Leave without saving?**
   - `beforeunload` backstop (browser owns that wording).
4. No auto-save. No second Save. No alternate leave-guard copy.

Libraries (Templates, Forms Library) use per-row / per-card saves — they
are **not** Type S; overlay tokens only, no leave guard unless a real
options form appears.

### Sticky bars

- **Default:** no floating sticky Save — bottom `submit_button` is enough
  when the form is short or panels collapse.
- **When sticky is needed** (very long single form, or a mobile-narrow
  admin viewport): pin a **WP-style** sticky row to the bottom of the
  content column (Save trailing; secondary text/outlined leading). Still
  inside `.fw-admin`; still `.button-primary` rust — **not** a Material
  app bottom bar, FAB, or navy chrome strip.
- Sticky is for **reachability**, not a second information architecture.

**Do:** one primary Save; Unlock for dangerous fields; sticky only when
scroll proves Save falls below the fold.
**Don’t:** sticky Material app chrome; duplicate Save in the admin bar;
auto-save that races Unlock.

---

## 8. Hierarchy & consistency across plugins

**Hierarchy**

1. WP host chrome (menu / admin bar) — untouched.
2. Plugin `h1` — one task name.
3. Panels / cards — sections.
4. `.form-table` rows — fields.
5. One primary action — Save / Start / etc.

**Cross-plugin consistency checklist**

| Concern | Expectation |
| --- | --- |
| Overlay CSS | Same Cove tokens; Tools ↔ Intake twin md5 when shipping shared file |
| Leave guard | Same `fw-admin-unsaved.js` + same confirm copy |
| Menu icon | Dashicon / mono — never multicolour quad in admin menu |
| Primary CTA | rust-700 labeled buttons |
| Links | sky; stay sky on hover |
| Health | Last submenu when the product has a Health desk |
| Completion | Prefer house done-card pattern (`fwt_done_card`: icon + short heading + exit actions) over spinners for queued work |

New plugins should **fork the Tools pattern**, not invent a fourth admin
skin. Markets / CRM / Academy admin desks should feel like the same
house once `.fw-admin` is on the wrap.

---

## 9. Do / Don’t (quick)

**Do**

- Scope every kit rule under `.fw-admin`.
- Use `var(--token, #hex)` with the locked house hex as fallback.
- Keep WP field heights, Title Case button labels, Screen Options.
- Redirect retired slugs; remember panel open state per page.

**Don’t**

- Touch `#wpadminbar`, `#adminmenu`, core screens, portal, or mail/PDF
  chrome from this overlay.
- Load Raleway / Crimson in wp-admin.
- Use navy or `#D2793D` as a filled labeled CTA.
- Ship a separate “admin design system” folder of tokens that diverge
  from Material roles — overlay **consumes** Material hex roles inside
  WP chrome.

---

## 10. Developer score checklist (wp-admin)

Score a plugin admin screen against this file (and Tools as the living
specimen). Apps / CRM front-end still score against [`PATTERNS.md`](PATTERNS.md).

- [ ] Root is `.wrap.fw-admin`; overlay enqueued only on this plugin’s pages
- [ ] `#wpadminbar` / `#adminmenu` unchanged
- [ ] One `h1`; navy left rule OK; no second page title
- [ ] Primary `.button-primary` is rust-700 / hover rust-800; no logo orange fill
- [ ] Content links sky-600 → sky-700; tabs not navy-filled
- [ ] Cards / panels: white + 1px border; panels closed by default (unless notice)
- [ ] Switches 36×20 rust-on; checkboxes accent rust
- [ ] Notices keep WP shape; semantic left borders only
- [ ] Type S: one form `data-fw-unsaved`, one bottom Save, leave-guard copy exact
- [ ] Unsaved notice under `h1` only while dirty
- [ ] Sticky Save (if any) is WP-style bottom row — not Material app chrome
- [ ] Menu: Health last when present; retired slugs redirect; Dashicon mono icon
- [ ] Twin Intake/Tools overlay files stay identical when either changes
- [ ] No Raleway/Crimson; no portal CSS leaked into admin

---

## Evidence (Tools)

| Asset / type | Role |
| --- | --- |
| `assets/css/fw-admin.css` | Cove overlay kit |
| `assets/js/fw-admin-unsaved.js` | Type S leave guard |
| `includes/class-fwt-admin.php` | Menu tree + enqueue gate |
| `includes/class-fwt-admin-panels.php` | Heading + Toggle panels |
| `includes/class-fwt-master-settings.php` | Settings Type S form + Unlock |
| `includes/fwt-done-card.php` | Completion card helper |

Intake mirrors the overlay and leave guard; treat divergence as a bug.
