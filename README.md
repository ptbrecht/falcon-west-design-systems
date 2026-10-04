# Falcon West design systems

**Three separate systems.** Do not mix them. Do not invent tokens.

This PR (Phase 3 Step 0) lands **`material/`** on `main`. Website systems and the writing pack stay on [`cursor/design-systems-seed-f27f`](https://github.com/ptbrecht/falcon-west-design-systems/tree/cursor/design-systems-seed-f27f) until they are promoted separately.

- **`material/`** — Falcon West Material for **apps / CRM / Tools / serial products only**. Not the marketing sites.
- **`falcon-west/`** — falconwest.com website system (rust buttons). *Not on this branch.*
- **`falcon-west-energy/`** — falconwestenergy.com (same website system; sky buttons, never rust). *Not on this branch.*

This repo is specs, specimens, tokens, fonts, and brand-guide assets — no WordPress, plugin, or CRM app source.

```
README.md
fonts/                      # Raleway for Material UI
assets/logos/app/           # app / CRM marks referenced by Material handoff
material/                   # apps / CRM / Tools / serial products ONLY
```

Shared Material typeface: [`fonts/Raleway.ttf`](fonts/Raleway.ttf).

---

## `material/` — Falcon West Material (apps only)

Material Design 2 retuned for insurance tools. **Not falconwest.com. Not falconwestenergy.com.**

Locked source (Claude pack), copied byte-identical from `cursor/design-systems-seed-f27f`:

- [`material/tokens.json`](material/tokens.json) — token roles (as shipped)
- [`material/README.md`](material/README.md) — guidance (opening edited for this repo’s scope)
- [`material/cover.html`](material/cover.html) — cover (as shipped)
- [`material/manifest.json`](material/manifest.json) — manifest (as shipped)

`--md-primary` is rust-700. Decorative / logo orange is rust-600. Navy is secondary chrome (app bar, nav, dark bands) — not a marketing brand field and not a button fill. Sky links stay sky on hover. Cards / modals / app bar are `--shape-large` 0. Controls are `--shape-small` 4. Menus sit at elevation-8. Focus is 2px navy + 2px offset. Ink `#080808`. Paper `#fcfefe`.

The earlier UX `DESIGN.md` / `specimen.html` are leftover seed. **Claude’s files win** if they disagree.

Also in `material/`:

- [`material/PATTERNS.md`](material/PATTERNS.md) — app layout / placement locks (Developer scoring)
- [`material/wordpress-admin-ux.md`](material/wordpress-admin-ux.md) — wp-admin Cove overlay (Tools house reference; not Material app chrome)
- [`material/CRM-FACE.md`](material/CRM-FACE.md) — CRM as a **known Material face / theme variant** (Energy × Material, Accent C sky; **not** a fourth system)
- [`material/HANDOFF-DEVELOPER.md`](material/HANDOFF-DEVELOPER.md) — implement locks
- [`material/light-tokens.css`](material/light-tokens.css) / [`material/light-tokens.md`](material/light-tokens.md)
- [`material/password-gate.md`](material/password-gate.md)

---

## Which system?

| Surface | System |
|---|---|
| app.falconwest.com, CRM, Tools, Academy gates, serial products | **Material** (this branch) |
| falconwest.com | **Falcon West** website (rust buttons) — still on the seed branch |
| falconwestenergy.com | **Falcon West Energy** website (sky buttons, never rust) — still on the seed branch |

---

## Assets on this branch

| Path | What |
|---|---|
| [`assets/logos/app/falcon-west-app-logo.png`](assets/logos/app/falcon-west-app-logo.png) | CRM / app quad mark (sky / white / rust / navy) |
| [`assets/logos/app/apps-logo-mark.svg`](assets/logos/app/apps-logo-mark.svg) | App quad mark (SVG) |
| [`assets/logos/app/apps-logo-mark-oneline.svg`](assets/logos/app/apps-logo-mark-oneline.svg) | App quad mark, one-line SVG |
| [`assets/logos/app/collide-icon-128.png`](assets/logos/app/collide-icon-128.png) | Collide icon (Chuck-craft source reference, not a Falcon West mark) |
