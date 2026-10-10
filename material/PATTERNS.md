# Falcon West Material — layout & placement patterns

**Scope:** apps only — CRM, Tools, Academy gates, Intake, Markets, and other
serial products on `app.falconwest.com`. Not falconwest.com or
falconwestenergy.com.

**What this file is:** house rules for **where things go**. Tokens
([`tokens.json`](tokens.json), [`README.md`](README.md)) already lock colour,
type, shape, and elevation. Developer scores plugins against **these**
placement locks.

**Token reminders this layer assumes**

| Role | Lock |
| --- | --- |
| Primary action | rust-700 `--md-primary` (never navy fill; never logo orange `#D2793D` on labeled controls) |
| Chrome | navy-900 `--md-secondary` / `--md-surface-dark` for app bars and dark bands |
| Links | sky-600 / sky-700 — stay sky on hover |
| Large surfaces | `--shape-large` **0** — cards, modals, sheets, banners, app bar |
| Controls | `--shape-small` **4px** |
| Dialogs | `--elevation-24`; menus `--elevation-8`; app bar `--elevation-4` |
| Focus | 2px navy ring, 2px offset (`--focus-ring-*`); fields use 2dp rust active border |

Citations below point at shipping placement patterns in Falcon West plugins
(good structure to keep). Paint that still disagrees with the Claude pack
(rounded sheets, navy CTAs, etc.) is **not** a pattern lock — tokens win.

---

## 1. Page chrome — app bar, title, back vs close, overflow

**Structure (desktop / tablet app shell)**

```
[ leading nav or back ]  Title (+ optional subtitle)     [ search / tools … ] [ primary ] [ overflow ]
```

- App bar is **navy chrome** (or theme-aware top bar per CRM light/dark rules),
  height 56–64px (48px dense), elevation 4, **radius 0**.
- Title is the current view name (pipeline, list, tool). One title — do not
  duplicate the product wordmark as a second H1 in the same bar.
- Actions sit in a trailing cluster; icon-only controls need `aria-label` and a
  full 48px hit target.

**Back vs close**

| Situation | Control | Placement |
| --- | --- | --- |
| Hierarchical / in-app navigation (tool → launcher, detail → list) | **Back** (← label or chevron) | Leading edge of chrome or tool header |
| Overlay / modal / sheet / full-page dismissible layer | **Close** (×) | Top-trailing of that layer — see §2 |
| Ending a session | Sign out | One known place (e.g. Tools launcher only), not every tool view |

**Do**

- Use **Back** for “return one level in the product” — Tools
  `tool_header()` → `← Back to Main` over the page title
  (`wp-plugin-falcon-west-tools`).
- Put overflow (`⋯`) on the trailing edge for secondary / destructive list
  actions — CRM rail list “more” (`fwcrm-list-more`).
- Keep Markets-style full-width navy header + title when the product is a
  single focused surface (`fwmarkets-header`).

**Don’t**

- Use × Close for hierarchical back (loses “where am I going”).
- Put the primary CTA in the leading slot or bury it under overflow.
- Put Sign out on every nested tool view (Tools: one place on the launcher).
- Round the app bar or mix marketing-site hero chrome into app shells.

---

## 2. Close / dismiss — never bury it

**Locks**

1. Dialog / sheet / modal: **× in the top-trailing corner** of the panel header
   (or absolutely positioned top-trailing inside the panel).
2. Full-page overlay / prep sheet: same rule — × top-trailing; optional
   labeled Close in the footer is fine **in addition**, never instead.
3. Scrim / backdrop click may dismiss **non-destructive** layers; Escape must
   dismiss when focus is trapped.
4. Dismiss must be findable in ≤1 glance — never only in a footer overflow,
   never only as “Cancel” without an × on informational dialogs that feel
   like viewers.

**Evidence in-repo**

| Product | Pattern |
| --- | --- |
| CRM card sheet | `fwcrm-modal-x` trailing in `fwcrm-sheet-head` |
| CRM dialogs | backdrop click + Cancel; confirm dialogs still end actions trailing |
| Tools AM Best | `.fwt-ambest-dialog-close` in dialog head, space-between with title |
| Markets Guides | `.fwmarkets-modal__close` `position: absolute; top/right` |
| Intake prep | `.ni-prep-x` absolute top/right + footer Close |

**Do:** ≥40px hit target on × (44px on touch); `aria-label="Close"`.
**Don’t:** hide dismiss behind long scroll; rely on browser chrome alone;
put destructive “Delete” where Close should be.

---

## 3. Primary action placement

**Locks**

1. **One contained rust primary per view** (or per dialog). More than one means
   the hierarchy is wrong — demote extras to outlined / text.
2. Primary sits **trailing** (end of reading direction):
   - App bar: last in the actions cluster (CRM Add is trailing).
   - Dialog / sheet footer: last in the actions row
     (`justify-content: flex-end` — CRM `.fwcrm-dialog-actions`,
     `.fwcrm-actions`).
   - Forms: end of the submit row (Intake `.ni-btn-row-right`).
3. **Destructive** is never the contained rust primary. Use text / outlined
   danger, or a separate confirm step. Keep it visually apart from Confirm
   (often leading of the pair, or behind overflow until confirmed).
4. Tool-style screens may pin a sticky primary row to the bottom of the
   container so short viewports still show the action (Material DESIGN §6;
   CRM mobile sticky foot).

**Do:** Cancel (text) → Confirm (contained) left-to-right in LTR.
**Don’t:** navy filled buttons; dual contained rust; primary on the leading
edge “for balance.”

---

## 4. Dialogs / sheets

**Anatomy**

```
┌─ panel (shape-large 0, elev-24, surface) ─────────────┐
│ Title … … … … … … … … … … … … … … … … … … … … [×]   │  header
│ optional tabs / status strip                         │
│ body (scrolls)                                       │
│ …                                                    │
│ footer: status?          [Cancel]  [Primary]         │  actions trailing
└──────────────────────────────────────────────────────┘
        ↑ scrim / backdrop (ink ~55–64% or navy-tinted)
```

**Locks**

| Rule | Detail |
| --- | --- |
| Structure | Header (title + ×) → body → footer actions |
| Focus | Open → focus first meaningful control (or title if static); **trap Tab** inside; restore focus to opener on close (Markets Guides; CRM `focusFirst` / `trapTab`) |
| Scrim | Dimmed backdrop; click-dismiss only when safe |
| Button order | **Cancel then Confirm** (text, then contained). CRM `reasonDialog`, `soldDialog`, reopen, etc. append `[cancel, confirm]` into flex-end rows |
| Sheets vs dialogs | Sheets = large task UI (CRM card). Dialogs = short decisions. Same close + action rules |
| Shape | `--shape-large` **0** for new work (Claude pack). Do not invent marketing radii |

**Do:** `role="dialog"`, `aria-modal="true"`, `aria-labelledby` on the title.
**Don’t:** primary-only dialogs with no way out; untrapped focus; rounded
“card modals” as the house default.

---

## 5. Forms

**Locks**

1. **Label above the field** (block label, not placeholder-only). Intake
   `.ni-field label`; password-gate; CRM field stacks.
2. **Error text directly under the failing control** (`.ni-error`, field-level
   status). Pair with error border — colour is never the sole signal.
3. Page-level / step error **banner above** the fields or above the action row
   (`role="alert"`) — Intake `.ni-error-banner`.
4. **Submit** at the end of the form flow, trailing (or full-width on narrow
   gates). Multi-step: primary “Next” / “Submit” trailing; secondary paths
   outlined or muted, not a second contained primary.
5. Hint / helper text sits under the label or under the field, medium emphasis
   only — never as the only label.

**Do:** 48px min control height on touch; 16px input text (avoids iOS zoom).
**Don’t:** placeholder-as-label; errors only in a toast far from the field;
navy submit fills.

---

## 6. Lists / tables

**Locks**

1. **Row primary action** = open the row (whole-row hit or clear name link).
2. **Secondary / destructive row actions** sit trailing on the row or in a
   trailing overflow (`⋯`) — CRM list more; note Edit then Delete.
3. If the table scrolls vertically, **sticky header** is allowed and preferred
   for wide sheets — CRM `.fwcrm-table--sheet thead th { position: sticky }`.
   Sticky header keeps the same surface fill as the table chrome so rows do
   not show through.
4. Horizontal overflow scrolls the table region; do not squash columns below
   readable width without a scroll parent.
5. Links inside cells stay **sky**.

**Do:** one obvious open affordance per row; keep density consistent.
**Don’t:** icon-only row actions without labels; sticky headers that jump
alignment; put Delete as the only visible trailing control without confirm.

---

## 7. Empty / error / loading placement

| State | Placement | Tone |
| --- | --- | --- |
| **Loading** | Inline near the content it replaces (CRM topbar `.fwcrm-loading`; mobile boot message in content well). Progress for long jobs in the dialog body | Medium emphasis; not a blocking full-viewport wash unless first paint |
| **Empty** | In the list/board content well, short sentence, medium text — CRM `.fwcrm-empty`, mobile `.fwcrm-m-empty`, Markets `.fwmarkets-empty` / modal empty copy | Explain next step when there is one (“Add a lead…”) |
| **Error** | Inline under field; banner above form/actions for submit failures; sheet/dialog status line in the footer for in-sheet saves | Danger tokens + text; `role="alert"` when it needs attention |

**Do:** empty and error replace or sit inside the content region — same column
as the data.
**Don’t:** toast-only failures for form validation; empty states in the app bar;
skeleton loaders that never resolve to empty/error.

---

## 8. Mobile vs desktop

| Concern | Desktop | Mobile |
| --- | --- | --- |
| Top chrome | Theme-aware or navy app bar | **Black / ink edge-to-edge** under status / Dynamic Island (CRM mobile lock); title below safe-area |
| Nav | Sidebar / rail + topbar | Menu opens nav; compact top bar; stage selectors may sit under the bar |
| Dialogs | Centered modal | May dock as bottom sheet (`align-items: flex-end`, full width) — CRM dialogs ≤ narrow breakpoints |
| Primary | Trailing in bar / footer | Sticky bottom action bar and/or FAB; respect `safe-area-inset-bottom` |
| Close × | Top-trailing | Same; bump hit target (~44px) |
| Tables | Sticky header + H-scroll | Prefer list cards / stacked rows over tiny multi-column grids |

**Do:** keep Back vs Close semantics identical across breakpoints.
**Don’t:** light paint bleeding into the island/status region; hide dismiss on
small screens; use desktop hover-only for essential actions.

---

## 9. Focus / keyboard

**Locks**

1. **Tab order follows visual order** (leading → trailing, top → bottom). Do
   not invent a focus order that skips the × or jumps past Cancel to Confirm
   first unless Confirm is the only action.
2. **Focus ring from tokens:** `outline: var(--focus-ring-width) solid
   var(--focus-ring-color); outline-offset: var(--focus-ring-offset)` — navy
   on light surfaces; white on navy/dark chrome. Prefer `:focus-visible`.
3. Text fields: **2dp rust active border is the indicator** — do not add a
   second navy ring on the same focused field.
4. Overlays: focus trap + Escape-to-dismiss + restore focus to opener.
5. Skip decorative year bars / pure visuals (`aria-hidden`) so they are not
   in the tab order (Tools year bar).

**Do:** keyboard users can reach Close and Cancel without a mouse.
**Don’t:** wash/tint as “focus”; remove outlines; trap focus without Escape.

---

## Quick scoring checklist (for Developer)

Score a plugin screen against this file — not against marketing sites.

- [ ] App chrome: title clear; Back vs Close correct; overflow trailing
- [ ] Overlay dismiss: × top-trailing; not buried
- [ ] One rust primary; trailing; destructive separate
- [ ] Dialog: header / body / footer; Cancel → Confirm; trap + restore focus
- [ ] Forms: label above; error under field; submit at end trailing
- [ ] Lists: row open + trailing secondary; sticky header only if scroll needs it
- [ ] Empty / error / loading in the content well
- [ ] Mobile safe-area + sticky actions when needed
- [ ] Tab order = visual order; token focus rings

## Specimen

Component paint for scoring still renders in the retired leftover
[`retired/specimen.html`](retired/specimen.html). If that page disagrees with
[`tokens.json`](tokens.json), [`README.md`](README.md), [`cover.html`](cover.html),
or [`manifest.json`](manifest.json), the Claude pack wins. This file is the
placement contract those components must obey when composed into screens.
Password / Academy gate layout: [`password-gate.md`](password-gate.md).
