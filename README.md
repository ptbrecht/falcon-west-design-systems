# Falcon West design systems

**Three separate systems.** Do not mix them. Do not invent tokens. Material does **not** cover the marketing sites.

This repo is specs, specimens, CSS/JSON tokens, fonts, and brand-guide assets only — no WordPress, plugin, or CRM app source.

```
README.md
fonts/                      # shared Raleway + Crimson Text
material/                   # apps / CRM / Tools / serial products ONLY
falcon-west/                # falconwest.com — rust buttons
falcon-west-energy/         # falconwestenergy.com — sky buttons, never rust
```

Shared typefaces live in [`fonts/`](fonts/). Specimens that reference `fonts/` locally expect those files next to the HTML; use this folder as the source of truth.

---

## 1. `material/` — Falcon West Material (apps only)

Material Design 2 retuned for insurance tools. **Scope lock: apps, CRM, Tools, Academy gates, and other serial products** (`app.falconwest.com`). **Not** falconwest.com. **Not** falconwestenergy.com.

Token roles (Claude pack — source of truth in [`material/tokens.json`](material/tokens.json)):

- `--md-primary` = rust-700 `#a85f2e` (text-bearing actions)
- `--md-primary-decorative` = rust-600 `#D2793D` (logo orange, decorative only)
- `--md-secondary` = navy `#15445D` — **chrome only, never a button fill**
- Sky links stay sky on hover (`#2d78ad` → `#266690`)
- `--shape-large` **0** for cards, modals, app bar
- `--shape-small` **4** for controls
- Menus at elevation-8
- Focus: 2px navy + 2px offset
- Ink `#080808` · paper `#fcfefe`

Do not apply Material type roles, focus, casing, or shape to the website folders.

Start here: [`material/DESIGN.md`](material/DESIGN.md) · [`material/tokens.json`](material/tokens.json) · [`material/specimen.html`](material/specimen.html)

---

## 2. `falcon-west/` — falconwest.com website system

The brokerage marketing site. **A separate system from Material.**

- Navy `#15445D` is the brand field (nav, dark sections) — never a button fill or button border
- **Rust `#D2793D` buttons** (hover `#A85F2E`)
- Sky `#2D78AD` / `#3D96D2` is for text links, not buttons
- Crimson Text for editorial; Raleway for the wordmark and UI chrome

Navy is the brand. Rust is the action. Sky is the link.

Start here: [`falcon-west/DESIGN.md`](falcon-west/DESIGN.md) · [`falcon-west/specimen.html`](falcon-west/specimen.html) · [`falcon-west/brand-guide-1pager.pdf`](falcon-west/brand-guide-1pager.pdf)

---

## 3. `falcon-west-energy/` — falconwestenergy.com

The same website system as Falcon West, with **sky as the action color**. **Never rust or orange.** Palette is black, white, and blue tones only.

- Navy remains the brand field
- **Sky buttons:** fill `#3D96D2`, hover `#2F78A7`
- Links stay sky; hover is sky, not rust
- Type, spacing, and components match the website system — this is a token override, not a second language

Start here: [`falcon-west-energy/DESIGN.md`](falcon-west-energy/DESIGN.md) (§2.4 and §7 are Energy) · [`falcon-west-energy/energy-colors.html`](falcon-west-energy/energy-colors.html) · [`falcon-west-energy/specimen.html`](falcon-west-energy/specimen.html)

---

## Which system?

| Surface | System |
|---|---|
| app.falconwest.com, CRM, Tools, Academy gates, serial products | **Material** |
| falconwest.com | **Falcon West** website (rust buttons) |
| falconwestenergy.com | **Falcon West Energy** website (sky buttons, never rust) |

Material never owns the two marketing domains. The two website folders never inherit Material card radius, navy-as-primary, or uppercase 14/500 buttons.
