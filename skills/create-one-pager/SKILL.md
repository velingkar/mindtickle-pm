---
name: create-one-pager
description: >
  Create a concise, structured product one-pager from raw notes, a problem statement, a feature idea, meeting notes,
  or any loose context. Use this skill when someone says "write a one-pager", "draft a feature brief",
  "turn these notes into a one-pager", "I have some context — create a one-pager from this",
  "write a pitch doc", "create an initiative brief", or "I need a one-pager but only have rough notes".
  The output follows a strict 9-section template and is intentionally constrained to 600–1000 words.
metadata:
  version: "0.3.0"
---

# Create a Product One-Pager

## Role

Act as a senior PM peer. Help the user build a crisp, high-signal one-pager through a back-and-forth conversation — not a one-shot document dump. Every section is confirmed before moving on.

---

## Writing Style

Follow these rules in every section. See `references/style-guide.md` for examples.

- **Active voice.** "Users can't track progress" not "Progress cannot be tracked by users."
- **Short sentences.** One idea per sentence. Break anything over 20 words.
- **Bullets over prose** for lists, evidence, and scope items.
- **Short paragraphs, not dense blocks.** For narrative sections (Problem, Why Now, Solution, Target Users), break content into multiple short paragraphs of 1–2 sentences each. Never lump 4+ sentences into a single paragraph block.
- **No filler.** Cut "leverage", "seamless", "best-in-class", "holistic". Say what you mean.
- **Honest gaps.** If something isn't known, write `[TBD — needs: X]`. Don't invent.
- **Numbers beat adjectives.** "43% of tickets" beats "many support tickets."

---

## Workflow

### Phase 1 — Gather context from connectors

Before asking the user anything, search available sources for relevant context. Run all searches in parallel.

1. **Confluence** — Use the Atlassian Confluence MCP to search for existing specs, decisions, or meeting notes related to the feature. Query with keywords from the user's input (feature name, problem area, affected team).
2. **Google Drive** — Search Google Drive for linked research docs, customer feedback files, or related briefs.
3. **MindTickle Help Center** — Use web search to look up how this feature area currently works in the product. Search `site:help.mindtickle.com [feature keywords]`. Understanding the current state reveals gaps the one-pager should address.

After searching, summarize findings in 2–3 tight bullets — what existing context you found and how it's relevant. If a source returns nothing useful, skip it. Don't apologize for missing connectors; just note what you did search.

### Phase 2 — Ask targeted questions

Identify what's missing from the user's input. Ask only what's needed — maximum 4 questions, grouped in one message. Do NOT ask questions already answered by the input or connector search.

Priority questions (ask if missing):

1. **Who is the primary user?** Role, company type, workflow context.
2. **What's the signal?** Any data, quotes, or tickets that confirm this is real.
3. **Why now?** What changed — internally or in the market — that makes this urgent?
4. **Any known constraints?** Timeline pressure, dependencies, team size.

Use `AskUserQuestion` to collect answers interactively.

### Phase 3 — Draft, self-review, then preview each section

For every section, run this loop before showing anything to the user:

**Step A — Draft**
Write the section following the template in `references/one-pager-template.md` and style rules in `references/style-guide.md`.

**Step B — Self-review against quality criteria**
Read `references/section-quality-checks.md` and score the draft for that section:
- ✅ Strong → proceed to Step C
- ⚠️ Needs work → identify the specific gap, revise, re-score. Repeat until ✅.
- ❌ Critical gap → you're missing information. Flag the specific gap to the user before proceeding (see below).

Common self-review catches before showing the user:
- Problem Statement has no real signal — add a `[TBD — check support tickets]` marker rather than asserting without evidence
- Why Now says "this is important" rather than naming what *changed* — rewrite to name the trigger
- Success Metrics are vague aspirations — rewrite with numbers and timeframes
- Milestones are build phases ("design", "build", "test") — rewrite as shippable slices with validation goals
- Non-Goals section is missing — always required

**Step C — Show the draft to the user**
Present the section in a clearly labeled block with a one-line note on why it meets the bar (or what assumption it's making that the user should validate):

```
## [Section Name]

[Draft content]

---
> ✅ This names [specific strength]. One assumption to confirm: [the thing you couldn't verify from available context].
```

Then ask: "Does this look right, or should I adjust anything before moving on?"

Wait for confirmation or feedback. Apply changes if requested. Re-run the self-review on any revised version before presenting it again. Then proceed to the next section.

**Section order:**
1. Problem Statement
2. Why Now
3. Proposed Solution
4. Goals / Non-Goals
5. Target Users
6. Success Metrics
7. Risks & Open Questions
8. Rough Scope (milestones)
9. GTM / Validation Plan

For section 8 (Rough Scope): if available context isn't enough to map milestones confidently, ask one focused question before drafting — e.g., "What's the biggest technical unknown here?" or "Is there a hard deadline driving the first milestone?"

### Phase 4 — Assemble and save

Once all 9 sections are confirmed:

1. Assemble the full one-pager.
2. Final style pass — enforce active voice, cut filler words from `references/style-guide.md`, shorten any sentence over 20 words.
3. Verify total word count is 600–1000 words. Trim if over.
4. Save as `one-pager-[feature-name].md` in the outputs folder.
5. Share the file link.

---

## What Makes a Section Strong

- **Problem Statement:** Names a specific user. Has at least one real signal (data, quote, ticket count).
- **Why Now:** States what *changed*. Not just "this is important" — what's different today vs. 6 months ago?
- **Proposed Solution:** Tells the story from the user's perspective. No architecture. No jargon.
- **Goals / Non-Goals:** Non-goals are as important as goals. Explicit boundaries prevent scope creep.
- **Target Users:** One primary segment. Specific enough that a designer could sketch their workflow.
- **Success Metrics:** One north star + one leading indicator + one guardrail. All time-boxed.
- **Risks:** Name the assumption that could make this wrong. Credibility comes from honesty.
- **Rough Scope:** 3–4 milestones, ~2 sprints each. Each milestone ships something *and* validates something.
- **GTM / Validation Plan:** Names a real internal team and real (or candidate) beta customers.
