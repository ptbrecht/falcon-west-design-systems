# Falcon West Material — password / gate page (app.falconwest.com)

For Academy and other app.falconwest.com gated pages. **Not** the falconwest.com marketing password form (`fw-post-password-*.css`), which uses website tokens and logo orange on navy.

## Branding strings
- Product line: **Falcon West Material**
- Product: **Falcon West Academy** (when the gate is Academy-specific)
- Avoid: website-only phrases, “Clickable Coverage,” generic “Password Protected” as the H1

## Layout
1. Full-viewport **paper-50** `#FCFEFE` (or `#fcfefe`) page ground — not a navy wash. Navy is chrome only.
2. Optional thin top chrome bar: navy-900 `#15445D`, 48–56px, wordmark left in white (or Academy mark).
3. Centered **surface** card: white `#FFFFFF`, **radius 0** (large surface), elevation 2 (MD2 umbra stack), max-width 420–480px, padding 32px.
4. Inside card, top to bottom:
   - Eyebrow: `FALCON WEST MATERIAL` — Raleway 12/700, letter-spacing 0.08em, rust-700 `#A85F2E` or charcoal-500
   - Title: `Falcon West Academy` (or page title) — Raleway 24/500, ink `#080808`
   - One-line help: Raleway 14/400, charcoal-700 `#434343`
   - Password field
   - Primary button

## Field
- Height 48px, radius **4px**, fill white, border 1px `#DCDCDC`
- Label above (not placeholder-only): Raleway 12/700, ink
- Value: Raleway 16/400, ink (16px avoids iOS zoom)
- Focus: border 2px navy-900 `#15445D` **or** rust-700; ring `0 0 0 3px` at ~28% of that color
- Placeholder if used: charcoal-500 `#6B6B6B`

## Primary button
- Fill **rust-700 `#A85F2E`** (never logo orange `#D2793D` — fails text contrast)
- Text white, Raleway 14/500, uppercase, letter-spacing ~1.25px, **no underline**
- Height 48px, radius 4px, full width of card
- Hover: rust-800 `#8A4D25`
- Focus-visible: 2px navy outline, 2px offset

## Do / don’t
- Do keep navy as the top bar / focus ring only.
- Don’t put white text on logo orange, or rust text on navy.
- Don’t use website Crimson Text on this gate (Material = Raleway throughout).
- Don’t reuse the centered navy panel from falconwest.com Additional CSS.

## Reference tokens
| Role | Hex |
|---|---|
| paper-50 | `#FCFEFE` |
| surface | `#FFFFFF` |
| ink | `#080808` |
| navy chrome | `#15445D` |
| rust primary (text-bearing) | `#A85F2E` |
| rust hover | `#8A4D25` |
| logo orange (decorative only) | `#D2793D` |
