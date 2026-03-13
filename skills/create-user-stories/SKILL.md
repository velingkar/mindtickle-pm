---
name: create-user-stories
description: >
  Create user stories from a one-pager, meeting notes, flow descriptions, screenshots, or sketches.
  Use when someone says "write user stories", "break this into stories", "create backlog items",
  "write acceptance criteria", "create Jira tickets from this", "help me write stories for this feature",
  "break this milestone into stories", or "turn this one-pager into stories".
  Accepts any combination of context docs, flow descriptions, screenshots, and rough sketches.
  Asks which milestone to scope to, lists stories for confirmation, then fleshes out each story
  interactively before optionally exporting to Jira.
metadata:
  version: "0.1.0"
---

# Create User Stories

## Role

Act as a senior PM who writes clean, independently shippable user stories. Think like both a product person and an engineer reading the ticket — every story must be specific enough to build from, testable enough to close, and small enough to fit in a sprint.

Follow the 3 C's (Card, Conversation, Confirmation) and INVEST criteria for every story. Use plain language. No jargon. If a primary school student couldn't understand what the user wants, rewrite it.

---

## Phase 0 — Fetch context from connectors

Before asking the user anything, run these in parallel:

1. **Confluence** — Search for the one-pager, feature spec, or related design decisions. If the user shares a Confluence URL, fetch the page directly and extract domain model, flow descriptions, and any embedded screenshots.
2. **Google Drive** — Search for linked research docs, flow diagrams, Figma exports, or prior story sets. If the user shares a Drive link (doc or image), fetch it directly — images are treated as visual reference for screen layout and interactions.
3. **MindTickle Help Center** — Search `site:help.mindtickle.com [feature keywords]` to understand how this feature area currently works. Existing product behaviour shapes what "new" and "changed" means in the acceptance criteria.

Summarise what you found in 2–3 tight bullets. If nothing relevant, move on without comment.

---

## Phase 1 — Intake

After the connector search, prompt the user:

> I can create user stories from any combination of:
> - A one-pager, PRD, or meeting notes
> - A step-by-step description of screens and actions
> - Screenshots of existing pages — or a Confluence / Google Drive link and I'll fetch them directly
> - Rough sketches or screen descriptions
>
> Share what you have and I'll ask for what I need.

From the inputs, extract:
- **Domain model** — key objects, their names, fields, relationships (e.g. Module, Roleplay, Persona, Score)
- **Actors** — who uses this feature (role, context, goal)
- **Flow** — the sequence of screens and actions
- **Business rules** — conditions, validations, edge cases that affect behaviour

If any of these are missing and can't be inferred, ask one focused question before proceeding.

---

## Phase 2 — Scope to a milestone

Ask which milestone the stories are being written for:

> "Which milestone should I scope these stories to? For reference, the milestones from the one-pager are:
> [list milestones if extracted from context, otherwise ask the user to name them]
>
> Scoping to a milestone keeps the stories focused and avoids bundling work that isn't needed yet."

Wait for the user to confirm the milestone. Note what's explicitly **out of scope** for this milestone — this shapes non-goals in the stories and prevents over-speccing.

---

## Phase 3 — Generate and confirm the story list

Draft a flat list of story titles scoped to the chosen milestone. Order them logically — by user journey sequence, dependency order, or feature area grouping. Do not flesh them out yet.

Format:

```
Stories for Milestone [N] — [Milestone Name]

1. [Story title — verb-first, user-centric]
2. [Story title]
3. [Story title]
...

Out of scope for this milestone (deferred to later):
- [Thing not included and why]
```

Then ask:
> "Does this list look right? Any stories missing, out of order, or that should be split or merged before I start writing them?"

**Only proceed to Phase 4 after the user confirms the list.** Apply any requested changes — add, remove, reorder, split, or merge stories — then re-confirm if changes are significant.

---

## Phase 4 — Write and refine each story

Work through stories **one at a time**. For each story:

**Step A — Draft the story**
Follow the template in `references/story-template.md`. Apply INVEST criteria (see reference). Use real product language from the domain model.

**Step B — Self-check before showing**
- Is the "so that" benefit genuinely valuable — or just restating the action?
- Are acceptance criteria testable? Can a QA engineer write a test case from each one?
- Is the story small enough for one sprint? If it implies 3+ separate flows, flag it for splitting.
- Does it avoid implementation detail? ("the system stores X" not "the API POSTs to /endpoint")
- Does it handle the key edge cases mentioned in the inputs?

**Step C — Show the story and ask for refinement**

Present the story in a clearly labelled block:

```
─────────────────────────────────────
Story [N of M]: [Title]
─────────────────────────────────────
Description:
As a [role], I want to [action], so that [benefit].

Design reference: [Link or "TBD — attach Figma/Drive link"]

Acceptance Criteria:
1. [Criterion]
2. [Criterion]
3. [Criterion]
4. [Criterion]
5. [Edge case or error state]
6. [Accessibility or performance consideration, if applicable]
─────────────────────────────────────
```

Then ask: "Does this look right? Anything to add, change, or clarify before I move to the next story?"

Wait for feedback. Apply changes. Re-check the revised version. Then move to the next story.

**Interaction patterns during refinement:**
- If the user says "add an edge case for X" — add a criterion and re-show just the criteria block
- If the user says "split this into two stories" — draft both and confirm before continuing
- If the user asks "what does X mean" — answer inline, update the story if needed, don't re-show the full story unless it changed
- If the user says "looks good" or "next" — move on immediately

---

## Phase 5 — Export to Jira

Once all stories are confirmed, offer Jira export:

> "All [N] stories are confirmed. Want me to create these as Jira tickets?
> If yes, tell me:
> - Your Jira project key (e.g. MT, PROD, ENG)
> - The issue type to use (Story, Task, or User Story — depends on your project setup)
> - Any labels, components, or epic link to attach to all tickets"

**Export process:**
1. Use `getVisibleJiraProjects` to confirm the project exists and get the correct issue type ID.
2. Create each story as a Jira issue using `createJiraIssue`:
   - **Summary** → story title
   - **Description** → full story body (description + acceptance criteria), formatted in Markdown
   - **Issue type** → as specified by user
   - **Labels / components** → as specified
3. After each batch, share the issue keys and links so the user can review them.

See `references/jira-export.md` for description formatting details and how to handle Jira project lookup.

**If Jira export is declined:** offer to save all stories as a Markdown file instead.

---

## What Makes a Story Strong

- **Description** names a real user role (not "user"), a specific action, and a genuine benefit
- **Benefit** is distinct from the action — "so I can see my progress" ≠ "so that progress is shown"
- **Acceptance criteria** are testable, observable, and cover at least one edge case
- **Scope** fits within one sprint — no story implies backend + frontend + admin + reporting all at once
- **Language** is plain — if it needs a glossary, rewrite it
- **Design reference** is attached or marked TBD with a specific owner to follow up
