# Falcon West design systems

**Three separate systems.** Do not mix them. Do not invent tokens.

- **`material/`** — Falcon West Material for **apps / CRM / Tools / serial products only**. Not the marketing sites.
- **`falcon-west/`** — falconwest.com website system (rust buttons).
- **`falcon-west-energy/`** — falconwestenergy.com (same website system; sky buttons, never rust).

This repo is specs, specimens, tokens, fonts, brand-guide assets, and a writing pack — no WordPress, plugin, or CRM app source.

```
README.md
fonts/                      # shared Raleway + Crimson Text
assets/                     # updated logos + brand style guide
material/                   # apps / CRM / Tools / serial products ONLY
falcon-west/                # falconwest.com — rust buttons
falcon-west-energy/         # falconwestenergy.com — sky buttons, never rust
writing/                    # gold + draft writing pack + PL gold PDFs
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
- **Sky filled buttons (a11y):** `#2F78A7` / hover `#266690`
- `#3D96D2` is older decorative / logo / non-a11y fill only — **not** the production filled-button color
- Links stay sky

**Production locks** ([`falcon-west-energy/ENERGY-SITE-LOCKS.md`](falcon-west-energy/ENERGY-SITE-LOCKS.md)) override Energy `DESIGN.md` if they disagree.

Start here: [`falcon-west-energy/ENERGY-SITE-LOCKS.md`](falcon-west-energy/ENERGY-SITE-LOCKS.md) · [`falcon-west-energy/DESIGN.md`](falcon-west-energy/DESIGN.md) · [`falcon-west-energy/energy-colors.html`](falcon-west-energy/energy-colors.html)

---

## Which system?

| Surface | System |
|---|---|
| app.falconwest.com, CRM, Tools, Academy gates, serial products | **Material** |
| falconwest.com | **Falcon West** website (rust buttons) |
| falconwestenergy.com | **Falcon West Energy** website (sky buttons, never rust) |

---

## Assets

Updated logos and the brand style guide only. No Originals, carriers, rugby, Misprint/Wingman fonts, or letterhead.

| Path | What |
|---|---|
| [`assets/logos/falcon-west/`](assets/logos/falcon-west/) | Updated Falcon West marks (PNG/JPG/favicon + Source Files) |
| [`assets/logos/falcon-west-energy/`](assets/logos/falcon-west-energy/) | Updated Energy marks |
| [`assets/logos/app/falcon-west-app-logo.png`](assets/logos/app/falcon-west-app-logo.png) | CRM / app quad mark (sky / white / rust / navy) |
| [`assets/logos/app/apps-logo-mark.svg`](assets/logos/app/apps-logo-mark.svg) | App quad mark (SVG) |
| [`assets/logos/app/apps-logo-mark-oneline.svg`](assets/logos/app/apps-logo-mark-oneline.svg) | App quad mark, one-line SVG |
| [`assets/logos/app/collide-icon-128.png`](assets/logos/app/collide-icon-128.png) | Collide icon (Chuck-craft source reference, not a Falcon West mark) |
| [`assets/brand-guide/Falcon West Brand Style Guide.pdf`](assets/brand-guide/Falcon%20West%20Brand%20Style%20Guide.pdf) | Brand style guide |

---

## Writing

Stand-alone pack in [`writing/`](writing/), separate from the three visual systems.

**Gold** = Peter-locked or long-standing house rule. **Draft** = Writing seed; pending Peter mark before brand law.

| File | Status | For |
|---|---|---|
| [`writing/chuck-style.md`](writing/chuck-style.md) | **gold** | Insights / newsletter craft, shared across both sites |
| [`writing/personal-lines.md`](writing/personal-lines.md) | draft | Personal Lines on **falconwest.com** |
| [`writing/commercial-lines.md`](writing/commercial-lines.md) | draft | Commercial Lines on **falconwest.com** |
| [`writing/energy.md`](writing/energy.md) | draft | Energy on **falconwestenergy.com** |
| [`writing/email-persona.md`](writing/email-persona.md) | **gold** | Peter’s outbound email voice |
| [`writing/insights-publish.md`](writing/insights-publish.md) | **gold** (meta + checklist); HTML contacts draft | Meta pack, checklist, newsletter, ownership |
| [`writing/forbidden-phrases-and-locks.md`](writing/forbidden-phrases-and-locks.md) | **gold** | Never invent / fairy dust / persona / site locks |
| [`writing/topic-whitespace.md`](writing/topic-whitespace.md) | draft | Do-not-retread + open topics |
| [`writing/coverage-scene.md`](writing/coverage-scene.md) | draft | Coverage Scene hotspot one-liner locks |

Personal Lines **gold standard** (prefer over the seed markdown):

- [`writing/personal-lines/The_Language_of_Insuring_Successful_Families_and_Individuals.pdf`](writing/personal-lines/The_Language_of_Insuring_Successful_Families_and_Individuals.pdf)
- [`writing/personal-lines/The_Language_of_Insuring_Successful_Families_and_Individuals_Research_Paper.pdf`](writing/personal-lines/The_Language_of_Insuring_Successful_Families_and_Individuals_Research_Paper.pdf)
