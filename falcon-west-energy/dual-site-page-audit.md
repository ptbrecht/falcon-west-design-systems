# Dual-site page audit — falconwest.com + falconwestenergy.com

Peter (2026-09-15): while theme/font/button CSS is moving, **audit every page** for correctness and consistency. Fonts must stay readable — not too small.

## Source of truth
- **Living lock:** `/workspace/brand/website-design-system.md` (improved on the original 1-pager)
- **Ancestry only:** `/workspace/brand/falcon-west-brand-guide-1pager.pdf` — Raleway ExtraBold headings + Crimson Text body + palette. It does **not** define button face, type scale floors, or Energy overrides; the website system does.
- Sync rule: before either site ships a version bump, ping the other so themes/plugins/playbooks match.

## Type floors (do not go under)
| Role | Min | Target |
|---|---|---|
| Body (Crimson) | **16px** absolute fail-under | **18px** kit |
| Page hero lead / intro under H1 | **20px** | **24px** shared (`.fw-lead-hero` / `fw-read-*`) |
| In-section lead | **20px** | kit Lead |
| Caption / fine print | **14px** | 14px |
| Buttons | **15px** Raleway 700 | Title Case (migrate; face Raleway now) |
| Eyebrow | 12px OK (short uppercase only) | |

Headings = Raleway ExtraBold ink `#080808`. Body color `#434343`. Never Crimson on buttons.

## Shared checklist (every URL)
1. **Fonts load** — Raleway + Crimson Text self-hosted; no accidental Montserrat/Arial body takeover on marketing copy.
2. **Buttons** — face **Raleway** (not Crimson via Astra `body,button`). Main brand: rust fill / white outline+rust. Energy: sky primary / white secondary (see Energy). Navy never a button fill or border.
3. **Hero lead** — page intro under H1 uses shared 24px Crimson treatment where that pattern exists; not stuck at body 16 while peers are 24.
4. **No orphan tiny type** — captions ≥14; form helpers ≥14; footer readable.
5. **Links** — sky family at rest; main-brand link hover rust; Energy link hover sky. Not rust-as-default-link.
6. **Contrast** — white text only on fills that clear AA (Energy primary a11y `#2F78A7` rest OK; don’t paint secondaries as primary).
7. **Mobile** — stack OK; type doesn’t drop below floors; tap targets ~44px.
8. **No third typeface** competing in body/headings.

## falconwest.com (FW) — Insurance
- Rust CTAs `#D2793D` (hover `#A85F2E`); outline white + rust.
- Sky = links only, not buttons.
- Priority pages: home, /team/, /private-client/, /business-insurance/, /personal-insurance/, /about/, contact/start, industry landings, blog index + recent posts.
- Confirm Additional CSS A+B landed: Raleway buttons; /team/ lead 24px; scan peers for same lead token.

## falconwestenergy.com (FWE) — Energy
- **No rust/orange anywhere.**
- Primary filled: a11y rest `#2F78A7`, hover `#266690`, white label. Kit `#3D96D2` is ideal accent; don’t use failing white-on-`#3D96D2` for small button type.
- Secondary: white fill + sky border/label — **never** blanket all `.fl-button` to primary fill.
- Priority pages: home, captive, industries, leadership, contact/start, key landings, blog index + recent posts.
- Dequeue CSS must primary-only after the secondary bug.

## How to report back
Per site: list URLs checked · pass/fail · screenshot or CSS smoking gun for fails · fixes shipped vs parked.
Ping UX if a new pattern needs a lock. Ping the sister site before shipping shared theme/plugin bumps.
