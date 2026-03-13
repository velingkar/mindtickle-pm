# One-Pager Template

9 sections. 600–1000 words total. See `style-guide.md` for writing rules.

---

## 1. Problem Statement
*3–5 sentences. Active voice. One real signal minimum.*

Who is affected. What breaks for them. What happens if it stays unsolved.
Cite at least one real signal: support tickets, churn data, NPS verbatim, sales objection, interview quote.

**Example:**
> Sales reps can't find the right content during live calls. They improvise — or send the wrong asset. 17 CS tickets flagged this in Q4. Two enterprise renewals cited it as a blocker.

---

## 2. Why Now
*2–4 sentences. State what changed — not just what matters.*

Name the specific trigger: a competitor move, a customer pressure point, a platform capability that just landed, or a strategic shift.
If there's no strong "why now," say so and flag it as a risk in section 7.

**Example:**
> Gong now surfaces content recommendations mid-call. Three prospects mentioned it last quarter. We have the signals data to build this — we just haven't connected it to search yet.

---

## 3. Proposed Solution
*4–6 sentences. User's perspective. No architecture, no jargon.*

Tell the story of what changes for the user. What do they do differently? What's faster, clearer, or less frustrating? Why is this meaningfully better than today?

**Example:**
> When a rep opens a deal room, the top 3 recommended assets appear automatically — ranked by what's worked in similar deals. No search. No guessing. The rep confirms or swaps and moves on.

---

## 4. Goals / Non-Goals

**In scope:**
- [Specific, bounded thing this solves — 1 sentence each]
- [Another bounded goal]
- [Max 4 items]

**Out of scope:**
- [Explicit boundary — what this does NOT address, and briefly why]
- [Another explicit boundary]
- [Max 4 items]

> Non-goals matter as much as goals. They prevent scope creep and set expectations early.

---

## 5. Target Users
*3–4 sentences. One primary segment. Specific enough to sketch their workflow.*

Name the role, company type, and workflow context. Explain why this problem is uniquely painful for them. Name secondary users briefly if relevant — don't conflate them with the primary.

**Example:**
> Primary: Account Executives at mid-market SaaS companies (100–500 seats). They run 5–8 demos a week with limited prep time. Content overload is their biggest complaint. Secondary: Sales managers who review call recordings and want to see what content was used.

---

## 6. Success Metrics

- **North star:** [Single metric proving this worked — include a number and timeframe. E.g., "15% reduction in avg content search time within 60 days of launch."]
- **Leading indicator:** [Something measurable within 30 days that shows we're on track. E.g., "50%+ of reps use recommended content in at least one call in week 1."]
- **Guardrail:** [A metric that must NOT get worse. E.g., "Content-related support tickets do not increase post-launch."]

---

## 7. Risks & Open Questions

- **[Risk name]:** [What could go wrong, and why it matters. E.g., "Recommendation quality depends on enough historical signal data — accounts with <10 closed deals may see poor suggestions."]
- **[Assumption risk]:** [Something we're assuming that's unvalidated. E.g., "We assume reps want automated recommendations — not confirmed with interviews yet."]
- **[Dependency risk]:** [An external dependency that could block or delay. E.g., "Requires the data pipeline team to expose deal-stage metadata by Sprint 2."]

---

## 8. Rough Scope

Break into **3–4 milestones, each ~2 sprints**. Each milestone ships something usable *and* validates a specific outcome.

**Milestone 1 — [Name]** *(Sprints 1–2)*
- **Ships:** [The specific, testable slice delivered at the end of these 2 sprints]
- **Validates:** [What signal or outcome does this milestone confirm?]

**Milestone 2 — [Name]** *(Sprints 3–4)*
- **Ships:** [Next layer of capability]
- **Validates:** [What does completing this unlock internally or for customers?]

**Milestone 3 — [Name]** *(Sprints 5–6)*
- **Ships:** [...]
- **Validates:** [...]

**Milestone 4 — [Name, if needed]** *(Sprints 7–8)*
- **Ships:** [...]
- **Validates:** [...]

> Fewer than 3 milestones? Explain why the work is genuinely self-contained.
> More than 4? That's a signal to scope down or split into separate initiatives.

**Biggest open risk to this plan:** [The one assumption that, if wrong, most changes how this gets sequenced or sized.]

---

## 9. GTM / Validation Plan

- **Internal dogfooding:** [Which internal team — Sales, CS, RevOps — will stress-test this first, and what will they specifically do with it?]
- **Friendly beta:** [5–10 specific customer names or a well-defined segment. Why them?]
- **Minimum signal to proceed:** [Observable, specific threshold — not "positive feedback." E.g., "3 of 5 beta reps use the feature unprompted in week 2 without being asked."]

---

## Style Rules (enforced on final pass)

- Active voice throughout
- No sentence over 20 words without a good reason
- Bullets for evidence, lists, scope, metrics
- No filler words: leverage, seamless, robust, intuitive, holistic, unlock, streamline
- Numbers over adjectives wherever possible
- Unknowns marked as `[TBD — needs: X]`, never invented
