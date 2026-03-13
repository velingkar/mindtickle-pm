# User Story Template and Quality Criteria

---

## Story Structure (3 C's)

### Card — the title and one-liner
- Verb-first, user-centric title: "View progress on assigned modules"
- Not feature-first: not "Module progress view", not "Add progress bar"
- One sentence that tells someone what the story does without reading the description

### Conversation — the description
```
As a [specific user role],
I want to [concrete action],
so that [genuine benefit distinct from the action].
```

**Role:** Be specific. "Sales rep at an enterprise account" not "user". If the same feature serves multiple roles differently, write separate stories.

**Action:** One verb, one object. "view my completed roleplay score" not "view and compare and export my scores".

**Benefit:** What changes for the user as a result. Must be distinct from the action itself.
- ❌ "so that I can see the progress bar" (restating the action)
- ✅ "so that I know whether to complete more practice before my next customer call"

### Confirmation — acceptance criteria
4–6 criteria. Each one must be:
- **Testable** — a QA engineer can write an automated or manual test from it
- **Observable** — describes visible or measurable system behaviour
- **Specific** — no "the system should work correctly", no "loading is fast"

**Required coverage:**
1. Happy path — the normal successful case
2. State/data condition — what triggers or gates the behaviour (e.g. "only shown after at least 1 completion")
3. Boundary/exclusion — what is explicitly excluded or hidden
4. Error or empty state — what the user sees when there's no data or an error
5. Edge case — a less common but important scenario
6. Accessibility or performance (optional but encouraged for UI stories)

---

## INVEST Criteria — check each story before confirming

| Letter | Criterion | Check |
|---|---|---|
| **I** | **Independent** | Can this story be built and tested without requiring another story to be complete first? |
| **N** | **Negotiable** | Does it describe *what* not *how*? Can the implementation be discussed with engineering? |
| **V** | **Valuable** | Does it deliver value to a real user or the business — not just a technical milestone? |
| **E** | **Estimable** | Is it specific enough that an engineer can give a rough estimate? |
| **S** | **Small** | Can it be completed in one sprint? If not, split it. |
| **T** | **Testable** | Can QA write test cases from the acceptance criteria without asking questions? |

**Flags that require splitting:**
- Story covers both a creation and an editing flow → split
- Acceptance criteria exceed 8 items → probably two stories
- The story requires a new API endpoint AND a new UI component AND admin configuration → split at logical seams
- The "so that" benefit contains "and" → two distinct benefits = two stories

---

## Language Rules

- **Plain language.** If a junior team member joining next week couldn't understand it, rewrite it.
- **Real product terms.** Use the actual object names from the domain model (Module, Roleplay, Persona, Score — whatever applies). Never use generic placeholders like "item" or "entity".
- **No implementation detail.** "The system stores the completion status" not "The API POSTs to /completions with a 201 response".
- **Present tense.** "The user sees X" not "The user will see X".
- **Active voice.** "The rep views their score" not "The score is displayed to the rep".

---

## Example Story

**Title:** View completion score for a finished roleplay

**Description:**
As a sales rep completing a roleplay practice session,
I want to see my AI-generated score immediately after finishing,
so that I know whether I need another practice round before a real customer call.

**Design:** [Figma link — attach before moving to engineering]

**Acceptance Criteria:**
1. The score screen appears automatically after the rep submits their final response in a roleplay session.
2. The score is displayed as a numeric value (0–100) with a label indicating the scoring dimension (e.g. "Discovery", "Objection Handling").
3. The screen does not appear for roleplays that are incomplete or that the rep exited early.
4. If the scoring service is unavailable, the rep sees: "Your score is being calculated. Check back in a few minutes." with a link back to their dashboard.
5. Scores below the passing threshold (configurable per program) are visually distinguished — e.g. shown in red with a "Try again" CTA.
6. Screen is accessible via keyboard navigation and passes WCAG AA contrast requirements.

---

## Story Sizing Reference

| Size | Sprint fit | Signs it needs splitting |
|---|---|---|
| XS | < 0.5 day | Fine as-is |
| S | 1–2 days | Fine as-is |
| M | 3–5 days | Fine, but watch scope |
| L | > 5 days | Split before pointing |
| XL | Multi-sprint | Definitely split — this is an epic, not a story |
