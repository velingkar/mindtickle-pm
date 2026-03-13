# Clarifying Questions Reference

Templates for Phase 2 questions and guidance on what to ask when inputs are missing.

---

## Phase 2 Question Templates

Use these exact framings where possible. Group related questions. Never ask more than 5–7 at once — prioritise the most blocking unknowns first.

### Scope
> "You've described [N] steps — does the prototype need to show all [N] as clickable screens, or just [subset]?"

> "Should this be a self-contained flow (starts and ends within the prototype) or embedded in a larger navigation shell?"

### Entry point
> "What does the user click or do to arrive at the first screen? (e.g. clicking a button on a listing page, opening a modal from a detail view)"

### Navigation shell
> "Does the prototype need the left sidebar from your existing product? If yes, could you share a screenshot so I match the nav items correctly?"

> "Should there be a topbar or breadcrumb trail? If so, what does it show at each step?"

### Key interactions
> "When the user clicks [X], do they stay on the same page (panel opens), go to a new page, or see a modal overlay?"

> "What happens after [final action]? Does the user return to the listing, see a confirmation, or land somewhere else?"

### Data and content
> "What are the real field names that should appear in this form? Please list the label and input type (text, dropdown, toggle, date, etc.) for each."

> "What are the real object names in your product for [thing]? (e.g. is it a 'Module', 'Program', 'Track'?)"

### Edge cases and states
> "Should I show a loading state when [action] is triggered, or can I jump straight to the result?"

> "What should the empty state look like for [table/list] — a message, an illustration, a CTA?"

> "Are there any conditional fields — things that only appear based on a previous selection?"

### Modals vs pages
> "Does the [step name] appear as a full-page view, a modal overlay, or a slide-in panel?"

---

## What to Ask When Inputs Are Missing

| Missing input | What to ask |
|---|---|
| No context document | "Can you describe the main objects and actions in this product in a few sentences? For example: what are the key nouns (modules, roleplays, personas) and what can users do with them?" |
| No flow description | "Walk me through the flow step by step — what does the user click first, what do they see, and what happens at the end?" |
| No screenshots of existing pages | "Can you share a screenshot of the existing page this flow lives in? I want to match the nav, header, and table patterns so the prototype feels native to your product." |
| No sketch for a new screen | "Can you sketch or describe what this screen should contain? I need to know: what's the heading, what are the main components (form, table, cards?), and what actions are available." |
| Ambiguous interaction | "When the user clicks [X], do they stay on the same page (e.g. a panel opens), go to a new page, or see a modal overlay?" |
| Missing field names | "What fields should appear in this form? Please list the label and input type (text, dropdown, toggle, etc.) for each." |
| Unclear labels / copy | "What should the primary CTA say? And the page/modal title?" |
| Unknown navigation | "What nav items should appear in the sidebar? Should any be highlighted as active during this flow?" |

---

## When to Ask for Visuals

Always ask for a screenshot or visual reference when:
- A screen is described but its layout is genuinely ambiguous
- The prototype needs to match an existing page and no screenshot has been provided
- A component is named (e.g. "a card picker", "a progress stepper") but its content and layout are unclear
- The user references a specific part of the existing product UI

**When asking for visuals, always offer the connector option:**
> "Could you share a screenshot of that page? You can also paste a Confluence page URL or Google Drive link and I'll fetch it directly — no need to download and re-upload."

Do not ask for visuals when the description is clear enough to build from, or when a screenshot wouldn't add meaningful specificity.

---

## Fetching Visuals from Connectors

When the user provides a URL instead of an upload, handle it as follows:

| Source | What to do |
|---|---|
| Confluence page URL | Fetch the page via the Atlassian Confluence MCP. Extract screenshots, flow diagrams, UI mockups, and any attached images. Treat these as direct visual references. |
| Google Drive link (image) | Fetch the image file directly from Google Drive. Analyse it visually — extract layout, navigation pattern, component structure, and typography hierarchy. |
| Google Drive link (doc/Figma export) | Fetch the document. Extract any embedded images and treat them as screenshots. Pull field names, labels, and terminology from the text. |
| MindTickle help article URL | Fetch via web. Screenshots in help articles show the current product UI — use them to match navigation patterns and existing component layouts. |

After fetching, briefly confirm what you extracted:
> "I pulled that Confluence page — I can see a sidebar with [X items] and a table layout with [Y columns]. I'll use that as the navigation reference for the prototype."
