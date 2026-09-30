# Falcon West design systems

**Three separate systems.** Do not mix them. Do not invent tokens.

- **`material/`** — Falcon West Material for **apps / CRM / Tools / serial products only**. Not the marketing sites.
- **`falcon-west/`** — falconwest.com website system (rust buttons).
- **`falcon-west-energy/`** — falconwestenergy.com (same website system; sky buttons, never rust).

This repo is specs, specimens, tokens, fonts, brand-guide assets, and writing seed — no WordPress, plugin, or CRM app source.

```
README.md
fonts/                      # shared Raleway + Crimson Text
material/                   # apps / CRM / Tools / serial products ONLY
falcon-west/                # falconwest.com — rust buttons
falcon-west-energy/         # falconwestenergy.com — sky buttons, never rust
writing/                    # copy seed for Peter’s review (not visual systems)
```

Shared typefaces live in [`fonts/`](fonts/).

---

## 1. `material/` — Falcon West Material (apps only)

Material Design 2 retuned for insurance tools. **Not falconwest.com. Not falconwestenergy.com.**

Locked source (Claude pack):

- [`material/tokens.json`](material/tokens.json) — token roles (as shipped)
- [`material/README.md`](material/README.md) — guidance (opening edited for this repo’s scope)
- [`material/cover.html`](material/cover.html) — cover (as shipped)
- [`material/manifest.json`](material/manifest.json) — manifest (as shipped)

`--md-primary` is rust-700. Decorative / logo orange is rust-600. Navy is secondary chrome (app bar, nav, dark bands) — not a marketing brand field and not a button fill. Sky links stay sky on hover. Cards / modals / app bar are `--shape-large` 0. Controls are `--shape-small` 4. Menus sit at elevation-8. Focus is 2px navy + 2px offset. Ink `#080808`. Paper `#fcfefe`.

The earlier UX `DESIGN.md` / `specimen.html` are leftover seed. **Claude’s files win** if they disagree.

---

## 2. `falcon-west/` — falconwest.com website system

The brokerage marketing site. **A separate system from Material.**

- Navy `#15445D` is the brand field — never a button fill or button border
- **Rust `#D2793D` buttons** (hover `#A85F2E`)
- Sky is for text links, not buttons
- Crimson Text editorial + Raleway wordmark / chrome

Start here: [`falcon-west/DESIGN.md`](falcon-west/DESIGN.md) · [`falcon-west/specimen.html`](falcon-west/specimen.html) · [`falcon-west/brand-guide-1pager.pdf`](falcon-west/brand-guide-1pager.pdf)

---

## 3. `falcon-west-energy/` — falconwestenergy.com

Same website system as Falcon West, with **sky as the action color**. **Never rust or orange.**

- Navy remains the brand field
- **Sky buttons:** `#3D96D2` / hover `#2F78A7`
- Links stay sky

Start here: [`falcon-west-energy/DESIGN.md`](falcon-west-energy/DESIGN.md) · [`falcon-west-energy/energy-colors.html`](falcon-west-energy/energy-colors.html)

---

## Which system?

| Surface | System |
|---|---|
| app.falconwest.com, CRM, Tools, Academy gates, serial products | **Material** |
| falconwest.com | **Falcon West** website (rust buttons) |
| falconwestenergy.com | **Falcon West Energy** website (sky buttons, never rust) |

---

## Writing

Seed for **Peter’s review** — not locked brand law yet. Lives in [`writing/`](writing/), separate from the three visual systems.

| File | For |
|---|---|
| [`writing/personal-lines.md`](writing/personal-lines.md) | Personal Lines on **falconwest.com** |
| [`writing/commercial-lines.md`](writing/commercial-lines.md) | Commercial Lines on **falconwest.com** |
| [`writing/energy.md`](writing/energy.md) | Energy on **falconwestenergy.com** |
| [`writing/chuck-style.md`](writing/chuck-style.md) | Insights / newsletter craft, shared across both sites |
