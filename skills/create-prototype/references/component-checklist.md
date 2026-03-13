# Component Checklist

Run this checklist before submitting any prototype. Every item must pass.

---

## Interactions

- [ ] Every button either navigates to a screen, opens a modal, or performs a visible state change
- [ ] Every modal has a close or back action
- [ ] Every tab or nav item is clickable and changes the visible content
- [ ] At least one "happy path" is fully clickable end-to-end without hitting a dead end
- [ ] Dropdowns and pickers open and show selectable options
- [ ] Form fields are controlled inputs — the user can type in them

## Navigation

- [ ] Active nav item is visually highlighted (accent border-left + accent background)
- [ ] Breadcrumbs (if present) are correct for each screen
- [ ] Back buttons lead to the correct previous screen
- [ ] Browser-style back is not relied upon — all navigation is managed by `screen` state

## Visual Design

- [ ] Background is `#f5f0e8` (not white, not grey)
- [ ] Borders are `2px solid #1a1a1a` (thick, hand-drawn — not `1px`, not rounded)
- [ ] Box shadows are offset (`3px 3px 0 #1a1a1a`) — not blurred
- [ ] Border radius is `3px` — not `8px`, not `12px`
- [ ] No broken `<img>` tags — all placeholders use hatching pattern + emoji
- [ ] Annotations (if used) are max 1–2 per screen, prefixed with ✎

## Content

- [ ] Real product labels, field names, and object names used throughout — no Lorem ipsum, no "Name", "Label 1", "Item 2" placeholders
- [ ] Any `[TBD]` markers are flagged to the user before submitting

## Code

- [ ] Single file, default export, no required props
- [ ] All state in `useState` / `useReducer` — no `localStorage`
- [ ] `screen` state variable controls navigation
- [ ] No external libraries beyond those available in the Cowork React sandbox (recharts, lucide-react, lodash, d3, Tailwind core utilities)
