# Falcon West design systems

Three separate design systems. **Do not mix them.** Do not invent tokens. This repo is specs, specimens, CSS tokens, fonts, and brand-guide assets only — no WordPress, plugin, or CRM app source.

```
README.md
fonts/                      # shared Raleway + Crimson Text
material/                   # Falcon West Material
falcon-west/                # falconwest.com brokerage site
falcon-west-energy/         # falconwestenergy.com
```

Shared typefaces live in [`fonts/`](fonts/). Specimens that reference `fonts/` locally expect those files next to the HTML; use this folder as the source of truth.

---

## 1. `material/` — Falcon West Material

Material Design 2 retuned for insurance: paper surfaces, rust-700 text-bearing actions, navy chrome, Raleway, ink `#080808` (never `#000000`).

- White and near-white (paper-50) surfaces
- Square large containers; 4px controls
- **Rust-700 `#a85f2e`** is the only rust legal on a fill that carries a text label
- Logo orange rust-600 `#D2793D` is decorative only — it fails 4.5:1 for text
- Navy `#15445D` is chrome (app bar, dark surfaces, focus), not a marketing brand field
- Raleway throughout

**Use on** apps, CRM, Tools, Academy gates, and other serial team products (`app.falconwest.com`). **Not** marketing sites.

Start here: [`material/DESIGN.md`](material/DESIGN.md) · [`material/specimen.html`](material/specimen.html) · [`material/light-tokens.css`](material/light-tokens.css)

---

## 2. `falcon-west/` — falconwest.com website system

The brokerage marketing site. **Separate from Material.** Do not apply Material type roles, focus, casing, or shape inversion.

- Navy `#15445D` is the brand field (nav, dark sections) — never a button fill or button border
- Rust `#D2793D` is the button color (hover `#A85F2E`)
- Sky `#2D78AD` / `#3D96D2` is for text links, not buttons
- Crimson Text for editorial; Raleway for the wordmark and UI chrome

Navy is the brand. Rust is the action. Sky is the link.

Start here: [`falcon-west/DESIGN.md`](falcon-west/DESIGN.md) · [`falcon-west/specimen.html`](falcon-west/specimen.html) · [`falcon-west/brand-guide-1pager.pdf`](falcon-west/brand-guide-1pager.pdf)

---

## 3. `falcon-west-energy/` — falconwestenergy.com

The same website system as Falcon West, with sky as the action color. **Never rust or orange.** Palette is black, white, and blue tones only.

- Navy remains the brand field
- Button fill `#3D96D2`, hover `#2F78A7`
- Links stay sky; hover is sky, not rust
- Type, spacing, and components match the website system — this is a token override, not a second language

Start here: [`falcon-west-energy/DESIGN.md`](falcon-west-energy/DESIGN.md) (§2.4 and §7 are Energy) · [`falcon-west-energy/energy-colors.html`](falcon-west-energy/energy-colors.html) · [`falcon-west-energy/specimen.html`](falcon-west-energy/specimen.html)

---

## Which system?

| Surface | System |
|---|---|
| app.falconwest.com, CRM, Tools, Academy gates, serial products | **Material** |
| falconwest.com | **Falcon West** website |
| falconwestenergy.com | **Falcon West Energy** website (sky override) |
