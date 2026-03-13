# Section Quality Checks

Per-section self-review criteria for use during drafting (Phase 3, Step B).
Score each section ✅ Strong / ⚠️ Needs work / ❌ Critical gap before showing it to the user.

---

## 1. Problem Statement

✅ Strong if ALL of:
- Names a specific user (role + context, not "users" or "customers")
- States what breaks or fails for them — not a feature request
- Includes at least one real signal (ticket count, churn data, quote, sales objection)
- States consequence of staying unsolved
- 3–5 sentences, active voice

⚠️ Revise if:
- User segment is vague ("all users", "our customers")
- No signal — just assertion
- Describes a solution, not a problem
- More than 6 sentences

❌ Block and ask user if:
- No user segment identifiable from any context
- No signal whatsoever and user can't provide one → mark `[TBD — needs: ticket data / customer interviews]`

---

## 2. Why Now

✅ Strong if:
- Names a *specific trigger*: competitor move, customer pressure, new platform capability, internal deadline, or market shift
- Explains what would be lost by waiting
- 2–4 sentences

⚠️ Revise if:
- Says "this is important" or "there is demand" without naming what changed
- Trigger is internal-only ("leadership priority") with no external validation

❌ Block and ask user if:
- No "why now" exists at all → don't invent one; write `[TBD — no urgency trigger identified; flag as risk]` and add it to Risks

---

## 3. Proposed Solution

✅ Strong if:
- Written from the user's perspective ("A rep opens X and sees Y")
- No architecture, infrastructure, or engineering implementation detail
- Explains what's meaningfully better vs. today
- 4–6 sentences

⚠️ Revise if:
- Describes the feature ("we will build X") instead of the user experience
- Contains jargon or technical terms a non-eng stakeholder would need explained
- Doesn't say why it's better than the current state

---

## 4. Goals / Non-Goals

✅ Strong if:
- 2–4 in-scope items, each specific and bounded (not "improve UX")
- 2–4 explicit non-goals with a one-phrase reason each
- Non-goals prevent obvious scope creep questions

⚠️ Revise if:
- Goals are vague ("make it easier for users")
- Non-goals are just negative restatements of goals
- Non-goals missing entirely ← most common gap

---

## 5. Target Users

✅ Strong if:
- Primary user named: role + company type + workflow context
- Explains *why this problem is uniquely painful* for this segment
- Secondary users mentioned separately, not conflated
- Specific enough for a designer to sketch their workflow

⚠️ Revise if:
- "All users" or "our customers" — too broad
- No explanation of why this segment, not another
- Primary and secondary users conflated

---

## 6. Success Metrics

✅ Strong if all three present:
- **North star:** single metric + number + timeframe (e.g., "15% reduction in X within 60 days")
- **Leading indicator:** measurable within 30 days of launch
- **Guardrail:** a metric that must not get worse

⚠️ Revise if:
- More than 4 metrics listed with no clear north star
- Metrics are aspirational ("improve engagement") — rewrite with numbers
- No timeframe on any metric
- Guardrail missing

❌ Block and ask user if:
- No measurable outcome exists at all → ask: "What would prove this worked in 90 days?"

---

## 7. Risks & Open Questions

✅ Strong if:
- 2–3 honest, named risks — at least one assumption risk
- Each risk names the consequence if it materializes
- At least one of: technical risk, adoption risk, assumption risk

⚠️ Revise if:
- Risks read like they were sanitized ("standard delivery risk")
- Only technical risks — no "we don't actually know if users want this"
- No consequence stated — just "X might be hard"

❌ Never write: "No significant risks identified." Always find at least one honest uncertainty.

---

## 8. Rough Scope (Milestones)

✅ Strong if:
- 3–4 milestones, each ~2 sprints
- Each milestone has: what ships + what it validates
- Milestones are independently testable or shippable (not "design phase", "build phase")
- One open risk to the milestone plan stated explicitly

⚠️ Revise if:
- Milestones are build phases, not shippable slices
- No validation goal per milestone — just a delivery description
- Single t-shirt size with no breakdown

❌ Block and ask user if:
- Not enough context to map 3 milestones → ask: "What's the single most important thing to ship first?"

---

## 9. GTM / Validation Plan

✅ Strong if:
- Internal dogfooding team named specifically (not "the sales team" — which team, who)
- Beta customers named or segment precisely defined
- Minimum signal is observable and specific (not "positive feedback")

⚠️ Revise if:
- "We'll do a beta" with no specifics
- Minimum signal is vague
- Missing entirely ← most skipped section — always include it

---

## Overall self-review before Phase 4

Before assembling, verify:
- [ ] No section scored ⚠️ or ❌ that hasn't been resolved or explicitly marked TBD
- [ ] Every TBD marker names *who* needs to provide the missing information
- [ ] No filler words remain (see `style-guide.md` cut list)
- [ ] Total word count is 600–1000 words
