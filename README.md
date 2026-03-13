# mindtickle-pm `v0.3.0`

A Cowork plugin for Product Managers at MindTickle. Provides five skills covering one-pager creation and review, lo-fi prototyping, and user story writing — all wired to internal knowledge sources via built-in connector support.

## Skills

### `create-one-pager`
Drafts a product one-pager from raw inputs — notes, a problem statement, a feature idea, meeting notes, or any loose context.

**Trigger phrases:**
- "Write a one-pager for X"
- "Turn these notes into a one-pager"
- "Draft a feature brief from this"
- "I have some context — create a one-pager from this"
- "Write a pitch doc / initiative brief"

**Output:** A 600–1000 word Markdown one-pager saved to the outputs folder, covering Problem, Why Now, Proposed Solution, Goals/Non-Goals, Target Users, Success Metrics, Risks, Rough Scope, and GTM/Validation Plan.

---

### `review-one-pager`
Reviews an existing one-pager, provides section-by-section critique, and produces a cleaned-up revised version.

**Trigger phrases:**
- "Review my one-pager"
- "What's missing from this one-pager?"
- "Improve / clean up this feature brief"
- "Give me feedback on this one-pager"
- "Strengthen this brief"

**Input:** A file path to an existing one-pager, or paste the content directly.

**Output:**
1. A section-by-section critique with ✅ / ⚠️ / ❌ ratings and specific suggestions
2. A revised version saved as `one-pager-[feature-name]-revised.md`

---

### `create-prototype`
Builds a clickable lo-fidelity HTML/React prototype from documents, flow descriptions, screenshots, or rough sketches. Asks clarifying questions before building, confirms a flow map before writing code, and produces a single self-contained React artifact in a consistent hand-drawn sketch aesthetic.

**Trigger phrases:**
- "Build a prototype for X"
- "Create a lo-fi prototype"
- "Turn this flow into a prototype"
- "Make a clickable mockup"
- "Sketch this out as an interactive prototype"
- "Build me a wireframe"

**Input:** Any combination of one-pagers, step-by-step flow descriptions, screenshots, Confluence pages, or Google Drive links.

**Output:** A self-contained React prototype using the plugin's hand-drawn design system (warm off-white background, thick borders, offset shadows).

---

### `edit-prototype`
Modifies an existing lo-fi prototype while maintaining design system consistency. Classifies changes as cosmetic, structural, behavioural, or content-related, and flags downstream effects before editing.

**Trigger phrases:**
- "Edit / update the prototype"
- "Change the [X] screen"
- "Add / remove a screen from the prototype"
- "The button should go to X instead"
- "Here's the code — change Y"
- "Extend the flow / add a new step"

**Input:** The existing prototype code (React or HTML) plus a plain-language description of the changes needed.

**Output:** Updated prototype code with a summary of what changed.

---

### `create-user-stories`
Creates user stories from a one-pager, meeting notes, flow descriptions, screenshots, or sketches. Scopes to a milestone, lists stories for confirmation, then fleshes out each one interactively before optionally exporting to Jira.

**Trigger phrases:**
- "Write user stories for X"
- "Break this into stories / backlog items"
- "Create Jira tickets from this"
- "Write acceptance criteria"
- "Turn this one-pager into stories"
- "Break this milestone into stories"

**Input:** Any combination of one-pagers, PRDs, meeting notes, flow descriptions, or screenshots.

**Output:** User stories following the 3 C's (Card, Conversation, Confirmation) and INVEST criteria, with descriptions and acceptance criteria. Optionally exported to Jira.

---

## Connectors

All five skills search external sources before drafting or producing output. Here's what's used and how to set each one up.

### Confluence (Atlassian)
**Used for:** Existing feature specs, past decisions, meeting notes, prior research, and design docs.

**Setup:** Connect your Atlassian account in Cowork → Settings → Connectors. Once connected, Confluence search works automatically across all skills.

### Google Drive
**Used for:** Linked research docs, customer feedback files, Figma exports, prior one-pager versions, and prototype screenshots.

**Setup:** Connect your Google account in Cowork → Settings → Connectors → Google Drive.

### MindTickle Help Center
**Used for:** Understanding how a feature area currently works in the product before drafting, prototyping, or writing stories.

**How it works:** Uses web search with `site:help.mindtickle.com` — no connector setup required. Works out of the box.

### MindTickle Compass *(pending setup)*
**Used for:** Querying MindTickle's internal knowledge — git repos, architecture decisions, and Confluence — through a single conversational interface. Useful for understanding technical constraints before scoping milestones.

**Status:** Not yet wired up — access method TBD. When ready, add the connection details (URL, API key, or MCP server) and update Phase 0 of each skill to query Compass alongside the other sources.

> **Note:** Skills don't warn you about unavailable connectors. They search what's available and move on silently.

---

## Setup

No environment variables required for the three core connectors (Confluence, Google Drive, Help Center). Connect your Atlassian and Google accounts once in Cowork Settings, and all five skills will use them automatically.

## Usage Tips

- **create-one-pager → review-one-pager:** Output from `create-one-pager` feeds directly into `review-one-pager` for a quick quality pass — both use the same 9-section template.
- **create-one-pager → create-user-stories:** A finished one-pager is the ideal input for `create-user-stories`. Share the file path and it will pull milestone structure and requirements automatically.
- **create-prototype → edit-prototype:** Use `create-prototype` for the first build, then `edit-prototype` for all subsequent changes. Don't re-run `create-prototype` to make edits — it's slower and loses change history.
- The more context you provide upfront, the better the output. Even rough bullet points work — paste in meeting notes, Slack threads, or customer feedback.
- For prototypes and user stories, Confluence page URLs and Google Drive links work just as well as uploaded files — the skills fetch them directly.
