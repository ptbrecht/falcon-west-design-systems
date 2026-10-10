# falconwestenergy.com — live site locks (from FWE)

Source: FWE Dequeue Front CSS plugin (currently 1.5.5). These are production locks for the Energy marketing site — keep in sync with `DESIGN.md` Energy token override.

## Buttons / CTAs (UX lock 2026-09-15)

| Role | Rest | Hover | Label |
|---|---|---|---|
| Primary filled (a11y floor) | `#2F78A7` | `#266690` | white |
| Secondary / outline | white fill + 1.5px `#2F78A7` border + label | fill `#2F78A7`, white label | — |

Notes:
- Never blanket all `.fl-button` as primary.
- Older notes also cite `#3D96D2` fill / `#2F78A7` hover; **a11y floor for filled primary is `#2F78A7`**.
- Never rust/orange on Energy.

## Surfaces

- Paper `#FCFEFE`
- Body ink `#080808`
- Muted `#6B6B6B`
- Card border `#DCDCDC`
- Footer / read-scroll a11y: `.fwe-read-scroll` `#BDBDBD`; footer tel underlined

## Type

- Body: Crimson (~18px); UI/titles: Raleway (e.g. ExtraBold 22 names, H2 40/800 Leadership)
- Kill Montserrat wherever it appears on Energy

## Logo / header

- Do **not** remap SVG fills in Dequeue CSS.
- Applications icon (Astra → https://app.falconwest.com/welcome-energy/): four-square Energy mark — `#3D96D2` / `#FFFFFF` / `#15445D` / rust `#D2793D` on the bottom-right square. **Logo mark, not UI branding.**

## Leadership /team/

- Square 1:1 photos, radius 0
- Order: Carly Brown first → brokers A–Z → Wade if present → Mike Tanghe last
- Peter = Lead Broker; ERIS smaller
- CTA: Start an Application → https://app.falconwest.com/welcome-energy/

## URLs

- All application CTAs: `https://app.falconwest.com/welcome-energy/` only (never `/welcome` or `/start-energy`)
- Privacy: `https://falconwestenergy.com/privacy-policy/` (not falconwest.com), except intentional self-link on the privacy page body until Energy policy text exists

## CSS source of truth

FWE Dequeue Front CSS plugin `fwe-dequeue-css` — ask FWE for current ZIP if rebuilding.
