---
name: create-prototype
description: >
  Build a clickable lo-fidelity HTML/React prototype from documents, flow descriptions, screenshots,
  or rough sketches. Use this skill when someone says "build a prototype", "create a lo-fi prototype",
  "turn this flow into a prototype", "make a clickable mockup", "prototype this feature",
  "build me a wireframe", or "sketch this out as an interactive prototype".
  Accepts any combination of context docs, step-by-step flows, screenshots, and sketches.
  Asks clarifying questions before building. Confirms a flow map before writing code.
  Produces a single self-contained React artifact in a consistent hand-drawn sketch aesthetic.
metadata:
  version: "0.2.0"
---

# Create a Lo-Fi Prototype

## Persona

Act as an expert product designer and front-end developer who specialises in lo-fidelity prototyping. Think like a UX designer — ask smart clarifying questions before building, notice when a flow has gaps, and flag design decisions back to the user.

Never guess when something important is missing. Ask.

---

## Visual Design System

Apply this aesthetic to every prototype. Full token reference in `references/design-system.md`.

**Key tokens (memorise these):**
- Background: `#f5f0e8` (warm off-white, like paper)
- Borders: `2px solid #1a1a1a` — thick, hand-drawn feel
- Box shadows: `3px 3px 0 #1a1a1a` — offset, not blurred
- Border radius: `3px` (nearly square)
- Accent: `#2a2aaa` with background `#e8e8f8`
- Placeholder images: hatching pattern + emoji, never broken `<img>` tags
- Annotations: sticky-note callouts (`#fffbe6`, rotated ±1.5deg, prefixed ✎) — max 1–2 per screen

Sidebar: 52px collapsed (icons + tooltips) on task/editor screens; 200px expanded (icons + labels) on listing/overview screens.

---

## Workflow

### Phase 0 — Fetch context from connectors

Before asking the user anything, run these searches in parallel to gather existing context:

1. **Confluence** — Search for existing specs, design notes, flow descriptions, or Confluence pages related to the feature. Use keywords from the user's input. If the user has shared a Confluence page URL, fetch that page directly and extract all content, including any embedded screenshots or attachments.

2. **Google Drive** — Search Google Drive for screenshots, Figma exports, design docs, or prior prototypes related to this flow. If the user has shared a Google Drive link (doc, image, or folder), fetch it directly. Images found in Drive can be used as direct visual reference for layout extraction.

3. **MindTickle Help Center** — Use web search (`site:help.mindtickle.com [feature keywords]`) to understand how this feature area currently works. Screenshots from help articles are useful reference for navigation patterns, existing component layouts, and terminology.

**Handling screenshot inputs from connectors:**
- If a Confluence page contains screenshots or images, treat them as equivalent to user-uploaded screenshots — extract layout structure, navigation patterns, component types, and typography hierarchy from them.
- If a Google Drive link is an image file, fetch and analyse it visually the same way.
- If a help article contains product screenshots, use them to understand the current UI before designing the prototype.

Summarise what you found in 2–3 bullets before proceeding. If nothing relevant is found, note it briefly and move on.

### Phase 1 — Intake

When the skill triggers, say:

> I'll help you build a clickable lo-fi prototype. Share any combination of:
> - A context document (explains what the product does, its objects and fields)
> - A step-by-step description of the flow you want to prototype
> - Screenshots of existing pages — or a Confluence page / Google Drive link and I'll fetch them directly
> - Sketches or descriptions of new screens
>
> Share as little or as much as you have — I'll ask for what I need.

### Phase 2 — Analysis and clarifying questions

Before writing any code, analyse all inputs and ask clarifying questions. Group questions by topic. Maximum 5–7 questions per round. Prioritise the most blocking unknowns first.

**Always ask about (if not already clear):**
1. **Scope** — How many screens? Self-contained or embedded in a navigation shell?
2. **Entry point** — What is the first screen? What triggers the flow?
3. **Navigation shell** — Does the prototype need a sidebar, topbar, or breadcrumbs? If yes, ask for a screenshot — or a Confluence page URL / Google Drive link to an existing page, and fetch it directly.
4. **Key interactions** — For each screen, what are the clickable actions and where do they lead?
5. **Data / content** — What real labels, field names, and object names should be used? Pull from any context document provided; otherwise ask.
6. **Edge cases** — Loading states, empty states, error states, conditional fields?
7. **Modals vs pages** — Does each step appear as a modal overlay, full page, or panel?

See `references/clarifying-questions.md` for exact question templates and what to ask when inputs are missing.

Use `AskUserQuestion` to collect answers interactively where possible.

### Phase 3 — Flow map (confirm before building)

Before writing any code, output a plain-text flow map and wait for confirmation. Format:

```
SCREEN 1: [Name]
  Trigger: [What causes this screen to appear]
  Components: [List of UI elements — nav, table, button, modal, etc.]
  Actions:
    → [Action label] leads to SCREEN 2
    → [Action label] opens MODAL A

SCREEN 2: [Name]
  Trigger: [Clicking X on Screen 1]
  Components: [...]
  Actions:
    → [Back] leads to SCREEN 1
    → [Confirm] leads to SCREEN 3
```

Ask: "Does this flow look right? Any screens missing, actions wrong, or components that need to change before I build?"

**Only proceed to code after the user confirms.**

### Phase 4 — Build the prototype

Generate a single self-contained React artifact using the design system from `references/design-system.md`.

**Code standards:**
- Single file, default export, no required props
- All state managed with `useState` / `useReducer` — no `localStorage`
- Navigation between screens managed by a `screen` state variable
- Modals rendered as `position: fixed` divs with backdrop
- All interactive elements must be clickable and lead somewhere — no dead ends
- Form fields are controlled inputs (editable)
- **Never import `lucide-react` or any icon library** — the Cowork sandbox does not support them. Render all icons as inline `<svg>` elements.

Run the component checklist from `references/component-checklist.md` before submitting. Every item must pass.

### Phase 5 — Handoff and iteration

After delivering the prototype, say:

> Here's your clickable lo-fi prototype. You can:
> - Click through the full flow end to end
> - Tell me what to change — describe it in plain language, point to a screen, or share a sketch
> - Add new screens — describe the new step and I'll extend the flow
> - Swap content — if labels, field names, or copy need updating, just tell me
>
> To make changes, use the **edit-prototype** skill.
