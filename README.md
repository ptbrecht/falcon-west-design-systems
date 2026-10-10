# Falcon West design systems

**Three separate systems.** Do not mix them. Do not invent tokens.

This repo is the source of truth for Falcon West UX, brand, and writing: specs, specimens, tokens, fonts, brand-guide assets, and the writing pack. No WordPress, plugin, or CRM app source.

`ptbrecht/falcon-west-design-systems` is this same repository, renamed to [ptbrecht/design-systems](https://github.com/ptbrecht/design-systems).

```
README.md
fonts/                      # Raleway (all systems) + Crimson Text (websites)
assets/                     # logos + brand style guide
material/                   # apps / CRM / Tools / serial products ONLY
falcon-west/                # falconwest.com — rust buttons
falcon-west-energy/         # falconwestenergy.com — sky buttons, never rust
writing/                    # voice.md source of truth + gold/draft pack + PL gold PDFs
```

Shared typefaces live in [`fonts/`](fonts/).

---

## 1. `material/` — Falcon West Material (apps only)

Material Design 2 retuned for insurance tools. **Not falconwest.com. Not falconwestenergy.com.**

Locked source (Claude pack):

- [`material/tokens.json`](material/tokens.json) — token roles
- [`material/README.md`](material/README.md) — guidance
- [`material/cover.html`](material/cover.html) — cover
- [`material/manifest.json`](material/manifest.json) — manifest

`--md-primary` is rust-700. Decorative / logo orange is rust-600. Navy is secondary chrome (app bar, nav, dark bands) — not a marketing brand field and not a button fill. Sky links stay sky on hover. Cards / modals / app bar are `--shape-large` 0. Controls are `--shape-small` 4. Menus sit at elevation-8. Focus is 2px navy + 2px offset. Ink `#080808`. Paper `#fcfefe`.

The earlier UX spec and specimen are leftover seed. They live in [`material/retired/`](material/retired/) and are not the source of truth. **Claude’s files win** if they disagree.

Also in `material/`:

- [`material/PATTERNS.md`](material/PATTERNS.md) — app layout / placement locks (Developer scoring)
- [`material/wordpress-admin-ux.md`](material/wordpress-admin-ux.md) — wp-admin Cove overlay (Tools house reference; not Material app chrome)
- [`material/CRM-FACE.md`](material/CRM-FACE.md) — CRM as a **known Material face / theme variant** (Energy × Material, Accent C sky; **not** a fourth system)
- [`material/HANDOFF-DEVELOPER.md`](material/HANDOFF-DEVELOPER.md) — implement locks
- [`material/light-tokens.css`](material/light-tokens.css) / [`material/light-tokens.md`](material/light-tokens.md)
- [`material/password-gate.md`](material/password-gate.md)

---

## 2. `falcon-west/` — falconwest.com website system

The brokerage marketing site. **A separate system from Material.**

- Navy `#15445D` is the brand field — never a button fill or button border
- **Rust `#D2793D` buttons** (hover `#A85F2E`)
- Sky is for text links, not buttons
- Crimson Text editorial + Raleway wordmark / chrome

Start here: [`falcon-west/DESIGN.md`](falcon-west/DESIGN.md) · [`falcon-west/specimen.html`](falcon-west/specimen.html) · [`falcon-west/README.md`](falcon-west/README.md)

---

## 3. `falcon-west-energy/` — falconwestenergy.com

Same website system as Falcon West, with **sky as the action color**. **Never rust or orange.**

- Navy remains the brand field
- **Sky filled buttons (a11y):** `#2F78A7` / hover `#266690`
- `#3D96D2` is older decorative / logo / non-a11y fill only — **not** the production filled-button color
- Links stay sky

**Production locks** ([`falcon-west-energy/ENERGY-SITE-LOCKS.md`](falcon-west-energy/ENERGY-SITE-LOCKS.md)) override Energy `DESIGN.md` if they disagree.

Start here: [`falcon-west-energy/ENERGY-SITE-LOCKS.md`](falcon-west-energy/ENERGY-SITE-LOCKS.md) · [`falcon-west-energy/DESIGN.md`](falcon-west-energy/DESIGN.md) · [`falcon-west-energy/energy-colors.html`](falcon-west-energy/energy-colors.html)

`falcon-west-energy/specimen.html` is the Energy specimen (a11y sky buttons). `falcon-west-energy/specimen.png` is a byte-identical copy of the Falcon West render and is not an Energy proof.

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
| [`assets/logos/falcon-west/`](assets/logos/falcon-west/) | Falcon West marks (PNG/JPG/favicon + Source Files) |
| [`assets/logos/falcon-west-energy/`](assets/logos/falcon-west-energy/) | Energy marks |
| [`assets/logos/app/falcon-west-app-logo.png`](assets/logos/app/falcon-west-app-logo.png) | CRM / app quad mark (sky / white / rust / navy) |
| [`assets/logos/app/apps-logo-mark.svg`](assets/logos/app/apps-logo-mark.svg) | App quad mark (SVG) |
| [`assets/logos/app/apps-logo-mark-oneline.svg`](assets/logos/app/apps-logo-mark-oneline.svg) | App quad mark, one-line SVG |
| [`assets/logos/app/collide-icon-128.png`](assets/logos/app/collide-icon-128.png) | Collide icon (Chuck-craft source reference, not a Falcon West mark) |
| [`assets/brand-guide/Falcon West Brand Style Guide.pdf`](assets/brand-guide/Falcon%20West%20Brand%20Style%20Guide.pdf) | One-page brand style guide. Ancestry only: it does not set button face or type floors. Preview: [`falcon-west/brand-guide-1pager.png`](falcon-west/brand-guide-1pager.png). |

---

## Fonts

| File | Role |
|---|---|
| [`fonts/Raleway.ttf`](fonts/Raleway.ttf) | Material UI; website wordmark and chrome |
| [`fonts/CrimsonText-Regular.ttf`](fonts/CrimsonText-Regular.ttf), [`fonts/CrimsonText-Italic.ttf`](fonts/CrimsonText-Italic.ttf), [`fonts/CrimsonText-SemiBold.ttf`](fonts/CrimsonText-SemiBold.ttf) | Website editorial. Not used in Material. |

Do not add a third typeface or swap these roles.

---

## Writing

Stand-alone pack in [`writing/`](writing/), separate from the three visual systems. Index: [`writing/README.md`](writing/README.md).

### Voice and copy

Source of truth: [`writing/voice.md`](writing/voice.md). Chuck Yates body, Harry Dry headlines, Peter’s teaching voice. It does not replace the lane, lock, or publish files.

Two house rules:

- Headlines are Harry Dry-style: 2–6 words, concrete.
- AI is never personified. Refer to AI as a tool or a program.

**Gold** = Peter-locked or long-standing house rule. **Draft** = writing seed; pending Peter’s mark before it is brand law.

| File | Status | For |
|---|---|---|
| [`writing/voice.md`](writing/voice.md) | **gold** | Voice and copy source of truth |
| [`writing/chuck-style.md`](writing/chuck-style.md) | **gold** | Falcon West application of that craft. Defers to `voice.md` on headlines and AI. |
| [`writing/personal-lines.md`](writing/personal-lines.md) | draft | Personal Lines on **falconwest.com** |
| [`writing/commercial-lines.md`](writing/commercial-lines.md) | draft | Commercial Lines on **falconwest.com** |
| [`writing/energy.md`](writing/energy.md) | draft | Energy on **falconwestenergy.com** |
| [`writing/email-persona.md`](writing/email-persona.md) | **gold** | Peter’s outbound email voice |
| [`writing/insights-publish.md`](writing/insights-publish.md) | **gold** (meta + checklist + `<hr />` dividers); HTML contacts draft | Meta pack, checklist, newsletter, ownership |
| [`writing/forbidden-phrases-and-locks.md`](writing/forbidden-phrases-and-locks.md) | **gold** | Never invent / fairy dust / persona / site locks |
| [`writing/topic-whitespace.md`](writing/topic-whitespace.md) | draft | Do-not-retread + open topics |
| [`writing/coverage-scene.md`](writing/coverage-scene.md) | draft | Coverage Scene hotspot one-liner locks |
| [`writing/private-client-select-ideas.md`](writing/private-client-select-ideas.md) | draft | Idea extraction only. Not Falcon West claims. |

Personal Lines **gold standard** (prefer over the seed markdown):

- [`writing/personal-lines/The_Language_of_Insuring_Successful_Families_and_Individuals.pdf`](writing/personal-lines/The_Language_of_Insuring_Successful_Families_and_Individuals.pdf)
- [`writing/personal-lines/The_Language_of_Insuring_Successful_Families_and_Individuals_Research_Paper.pdf`](writing/personal-lines/The_Language_of_Insuring_Successful_Families_and_Individuals_Research_Paper.pdf)
