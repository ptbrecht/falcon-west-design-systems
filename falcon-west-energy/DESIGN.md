# Falcon West Energy — website overlay

**This folder is falconwestenergy.com only.** Navy is the brand field. **Sky a11y filled buttons** are `#2F78A7` / hover `#266690`. **Never rust or orange on Energy UI.**

**Production truth:** [`ENERGY-SITE-LOCKS.md`](ENERGY-SITE-LOCKS.md) wins if this file or the shared main-brand spec disagrees.

Shared type, spacing, shape, and component geometry live in [`../falcon-west/DESIGN.md`](../falcon-west/DESIGN.md). Use that file for Crimson / Raleway scale, radii, cards, and fields. **Do not** use its rust button recipes, rust focus, rust tabs, or rust outline buttons on Energy.

This is **not** Material. Do not apply Material tokens, square-card / app-bar rules, navy focus rings, or rust-700 as “primary.” App / CRM language: [`../material/README.md`](../material/README.md) and [`../material/tokens.json`](../material/tokens.json).

---

## 0. The one-sentence read

Traditional and trust-first, Energy-colored: Crimson body under a Raleway ExtraBold wordmark, navy as the brand field, **sky a11y fills on buttons**, sky on links — black, white, and blue only.

---

## 1. Color (Energy only)

| Role | Hex | Notes |
|---|---|---|
| Navy brand field | `#15445D` | Nav, dark sections. **Never** a button fill or button border. |
| **Filled primary (a11y)** | `#2F78A7` | Production rest fill. White label. |
| **Filled hover (a11y)** | `#266690` | Production hover fill. White label. |
| Outline / secondary | white fill + 1.5px `#2F78A7` + sky label | Hover: fill `#2F78A7`, white label. |
| Text link | `#2D78AD` | Hover `#2F78A7` (sky stays sky). |
| Sky 500 (decorative) | `#3D96D2` | Older decorative / logo / non-a11y fill **only**. Not the production filled-button color. |
| Ink / body / muted | `#080808` / `#434343` / `#6B6B6B` | Same as main brand. |
| Line / paper / white | `#DCDCDC` / `#FCFEFE` / `#FFFFFF` | Same as main brand. |

### Binding rules

1. **Never rust or orange** (`#D2793D`, `#A85F2E`, or any orange) on Energy UI.
2. **Filled buttons use the a11y pair** `#2F78A7` / `#266690`. Do not ship white-on-`#3D96D2` as a small labeled primary.
3. **`#3D96D2` is not the production button fill.** Logo mark and decorative accent only (see ENERGY-SITE-LOCKS Applications icon).
4. **Navy is chrome, not a control.** Never a button fill or button border.
5. **Never blanket all `.fl-button` as primary.**
6. If this table and [`ENERGY-SITE-LOCKS.md`](ENERGY-SITE-LOCKS.md) disagree, **locks win**.

---

## 2. Buttons / CTAs

Height 44px, horizontal padding 22px, radius 6px, Raleway Bold 15px Title Case — same geometry as the main brand, Energy color only.

- **Filled** — background `#2F78A7`, text `#FCFEFE`. Hover `#266690`.
- **Outline** — background `#FFFFFF`, text `#2F78A7`, `1.5px solid #2F78A7`. Hover fill `#2F78A7`, hover text paper-50.
- **Ghost** — transparent, text `#2F78A7`, no border. Hover text `#266690`.

Application CTAs: `https://app.falconwest.com/welcome-energy/` only (never `/welcome` or `/start-energy`).

---

## 3. Focus

2px sky a11y border + soft 3px sky ring — **not** rust, **not** the Material navy ring:

```
border: 2px solid #2F78A7;
box-shadow: 0 0 0 3px rgba(47,120,167,0.28);
```

---

## 4. Shared type and layout

Reuse [`../falcon-west/DESIGN.md`](../falcon-west/DESIGN.md) §3 (type), §4 (shape / surface), §6.1 (navy nav as a brand field), §6.3 (fields), §6.5 (cards). Swap every rust / orange token for the Energy sky pair above.

Tabs: Raleway Bold Title Case; active text and 2px underline in `#2F78A7` (not rust). Badges may use navy or sky `#3D96D2` as a decorative chip — never as a button.

Label the surface **Falcon West Energy Insurance Solutions**.

---

## 5. Prohibitions

1. Rust or orange anywhere on Energy UI.
2. `#3D96D2` as the production filled-button color.
3. Navy as a button fill or button border.
4. Blanket `.fl-button` → primary fill.
5. Material rules (navy focus, uppercase 14/500 buttons, rust-700 primary, 4px/0 shape inversion).
6. A third typeface, or Montserrat leftover.
7. Gradients, photo heroes, textures, glassmorphism, or a falcon watermark as a standalone background.

---

## 6. Relationship to Material

Material lives in [`../material/README.md`](../material/README.md) / [`../material/tokens.json`](../material/tokens.json). It is a working tool for professionals. This overlay is the Energy marketing site. They share a name and a palette family. They do not share type roles, button geometry, focus, or shape. Do not reconcile them into one system.
