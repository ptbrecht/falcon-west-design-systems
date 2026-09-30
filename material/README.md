# Falcon West Material

Material Design 2 retuned for insurance **apps** — CRM, Tools, Academy gates, serial products. **Not** falconwest.com or falconwestenergy.com. Those stay in the website folders.

Token roles live in [`tokens.json`](tokens.json). Guidance lives in [`DESIGN.md`](DESIGN.md). If an older specimen or CRM note disagrees, the JSON + DESIGN win.

| File | Role |
|---|---|
| [tokens.json](tokens.json) | Locked Claude roles (primary, decorative, shape, elevation, focus) |
| [DESIGN.md](DESIGN.md) | Spec (colors, type, shape, elevation, components) |
| [specimen.html](specimen.html) / [specimen.png](specimen.png) | Visual specimen (`specimen.html` is current; PNG is the earlier seed shot) |
| [light-tokens.css](light-tokens.css) / [light-tokens.md](light-tokens.md) | Light-theme CSS variables |
| [password-gate.md](password-gate.md) | Academy / app.falconwest.com gate page |
| [HANDOFF-DEVELOPER.md](HANDOFF-DEVELOPER.md) | CRM paint notes — defer to tokens.json on shape/navy |

**Locks:** rust-700 primary · rust-600 decorative · navy chrome-only (no navy button fill) · square cards (0) · 4px controls · menus elevation-8 · 2px navy focus + 2px offset · ink `#080808` · paper `#fcfefe` · sky links stay sky.
