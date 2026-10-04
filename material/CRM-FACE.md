# CRM face — known Material variant (not a separate system)

**Status:** Documented **face / theme variant** of **Falcon West Material**.
**Not** a fourth design system. **Not** a stand-alone UX brand.

Falcon West ships **three** visual systems in this repo (`material/`,
`falcon-west/`, `falcon-west-energy/`). CRM lives **inside Material**. When
CRM’s paint leans sky (Energy) or runs a real dark shell, that is a
**known exception on top of Material** — tokens, placement, and scoring
still come from this folder.

> **One-liner:** *Falcon West Energy meets Falcon West Material* — sky-leaning
> CTAs (Accent C style), light **and** dark modes, still Material patterns
> and tokens where they apply.

---

## What CRM is / is not

| CRM is | CRM is not |
| --- | --- |
| A **Material face** for `wp-plugin-falcon-west-crm` / app.falconwest.com CRM | A fourth system beside Material / Falcon West / Energy |
| Light + dark **Appearance** (System default) | Permission to invent CRM-only components that ignore [`PATTERNS.md`](PATTERNS.md) |
| Sky-leaning primary actions (**Accent C** style — no rust primary *on this face*) | A new token file that forks `tokens.json` into “CRM Material” |
| Charcoal / paper shells documented in handoff | Marketing-site chrome from `falcon-west/` or `falcon-west-energy/` |
| Same placement locks as other apps | “CRM UX” as a brand name in decks or plugin READMEs |

If a future product needs a different face, document it the same way:
**variant of Material**, with an explicit exception list — never a new
top-level system folder.

---

## System map

```
Falcon West Material          ← system of record (this folder)
├── Default apps / Tools / Intake / Markets / Academy gates
│     rust-700 primary · navy chrome · light theme (dark = navy bands only)
└── CRM face (this doc)       ← known variant
      Accent C sky CTAs · light + dark shells · PATTERNS still score the layout
```

| Layer | CRM uses |
| --- | --- |
| Placement / IA | [`PATTERNS.md`](PATTERNS.md) — Back vs Close, primary trailing, dialogs, forms, lists, empty/error, mobile, focus |
| Token roles | [`tokens.json`](tokens.json) + [`README.md`](README.md) — shapes, elevation, type, ink/paper, focus geometry, link sky |
| Face paint | This file + [`HANDOFF-DEVELOPER.md`](HANDOFF-DEVELOPER.md) + [`light-tokens.md`](light-tokens.md) / [`light-tokens.css`](light-tokens.css) |
| wp-admin desks | [`wordpress-admin-ux.md`](wordpress-admin-ux.md) (Cove overlay) — not this face |

---

## Face recipe — Energy × Material

**Intent:** CRM should feel related to **Falcon West Energy** (sky action
colour, cool confidence) while remaining a **Material** product (square
large surfaces, 4px controls, elevation ladder, Raleway, focus rings,
PATTERNS placement).

| Role | Default Material (other apps) | CRM face |
| --- | --- | --- |
| Contained primary / FAB / ADD | rust-700 `#a85f2e` (`--md-primary`) | **Accent C sky** `#2d78ad` (≈ Energy a11y sky family; hover toward `#266690`) |
| Logo / decorative orange | rust-600 `#D2793D` decorative only | Same — **never** a labeled CRM CTA |
| Links / Drive | sky-600 / sky-700 | Same sky family (on dark charcoal prefer readable `#5aa0cc` for links/icons — see contrast notes in handoff) |
| Navy | Secondary chrome / dark bands | Light sidebar may stay navy; **dark shell chrome is charcoal / black — no navy page/card fills** |
| Page ground (light) | paper `#fcfefe` | Same |
| Dark | Navy band roles only (not a full theme) in default Material | **Real dark Appearance:** charcoal page/surfaces (`#121212` / `#1c1c1c` …) per handoff |
| Shape / type / elevation / focus | Material locks | **Unchanged** — do not round cards; do not invent a CRM type ramp |

**“No rust primary” applies to the CRM face CTAs**, not to Material law for
Tools / Intake / other apps. Claude pack `--md-primary` remains rust-700 for
the system. CRM remaps the **face’s** primary action paint to Accent C; it
does not rewrite `tokens.json` or claim a new brand primary for the house.

Navy is still **never** a button fill on CRM.

---

## Light + dark

CRM ships **Appearance: Dark | Light | System** (default **System** —
`prefers-color-scheme` until the user overrides). Caption:
*“Follows your device until you choose Dark or Light.”*

| Mode | Shell summary |
| --- | --- |
| Light | Paper / white surfaces; ink emphasis; desktop top bar theme-aware light; sidebar may remain navy |
| Dark | Black / charcoal shell (**no navy** as page, card, or dark sidebar fill); sky Accent C CTAs; lighter sky for links on charcoal |
| Mobile top chrome | **Always black** edge-to-edge under status / Dynamic Island — even in Light; theme paint starts **below** that chrome |

Implement detail, Island clearance, rail theme-dot, and allowlists:
[`HANDOFF-DEVELOPER.md`](HANDOFF-DEVELOPER.md).

### Open product call — dark face vs paper

Material’s README states there is **no full dark theme** in the default
token pack (only dark surface **roles** for navy bands). CRM already runs a
**real dark Appearance**. Whether the long-term CRM dark face stays
**charcoal paper-on-dark** (current handoff) or migrates toward a
**paper-tinted / softer** dark is an **open product call** — do not invent a
third dark without Peter. Until then, ship charcoal per handoff; document
deltas here when the call lands.

---

## Patterns still win

CRM must keep scoring against [`PATTERNS.md`](PATTERNS.md):

- Back vs Close; × top-trailing on sheets/dialogs
- One contained primary per view, **trailing**
- Dialog header / body / footer; Cancel → Confirm
- Forms: label above; errors under field
- Lists: row open + trailing overflow; sticky header only when scroll needs it
- Mobile safe-area; sticky foot / FAB when needed
- Focus: token ring geometry (or field active border) — no wash-as-focus

Accent C changes **paint**, not placement. A sky ADD in the trailing cluster
is still the same pattern as a rust ADD on Tools.

---

## Do / Don’t

**Do**

- Call this the **CRM face** or **CRM Material variant** in specs and PRs.
- Cross-link [`PATTERNS.md`](PATTERNS.md) and [`tokens.json`](tokens.json) from
  any CRM UX note.
- Keep Accent C AA (`#2d78ad` on white ≈ 4.77:1); keep `#5aa0cc` off body text
  on light.
- Strip ⚡ / “lightning CRM” ornament; quad mark = favicon + in-app logo only.

**Don’t**

- Create `crm/` as a sibling design system in this repo.
- Say “CRM design system” in external copy.
- Fork placement rules that contradict PATTERNS “because CRM is different.”
- Use rust-700 and Accent C sky as **competing** primaries on the same CRM
  view — one contained primary.
- Ship Field green / random oranges / navy CTAs.
- Restyle wp-admin with this face — admin uses
  [`wordpress-admin-ux.md`](wordpress-admin-ux.md).

---

## Developer score checklist (CRM face)

Use **in addition to** the [`PATTERNS.md`](PATTERNS.md) checklist.

- [ ] Documented as Material **face / variant** — not a fourth system
- [ ] Placement matches PATTERNS (Back/Close, trailing primary, dialogs, focus)
- [ ] Token roles (shape 0 cards, 4px controls, elevation, type, ink/paper) intact
- [ ] CRM primary actions = Accent C sky `#2d78ad` (no rust primary on this face)
- [ ] Logo orange never on labeled CTAs; navy never a button fill
- [ ] Appearance Dark | Light | System; default System
- [ ] Dark shell charcoal/black — no navy page/card/sidebar fills
- [ ] Mobile chrome always black + Island clearance
- [ ] Light/dark desktop top bar theme-aware per handoff
- [ ] No separate CRM token brand; face notes point here + HANDOFF
- [ ] Open call on dark-vs-paper dark face acknowledged if changing dark paint

---

## Pointers

| Doc | Role |
| --- | --- |
| [`PATTERNS.md`](PATTERNS.md) | Placement locks (all apps, including CRM) |
| [`tokens.json`](tokens.json) / [`README.md`](README.md) | Material token law |
| [`HANDOFF-DEVELOPER.md`](HANDOFF-DEVELOPER.md) | CRM implement locks (0.1.64+ allowlist, rail dot, icons) |
| [`light-tokens.md`](light-tokens.md) | Light face token table |
| [`wordpress-admin-ux.md`](wordpress-admin-ux.md) | wp-admin Cove overlay (separate from this face) |
| [`../falcon-west-energy/ENERGY-SITE-LOCKS.md`](../falcon-west-energy/ENERGY-SITE-LOCKS.md) | Energy site sky locks (marketing) — kinship only; CRM is not the Energy website |
