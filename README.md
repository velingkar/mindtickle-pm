# mindtickle-pm

A Cowork plugin for Product Managers at MindTickle. Provides two skills for creating and reviewing product one-pagers using a structured 9-section template.

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

## Setup

No external services or environment variables required. This plugin is self-contained.

## Usage Tips

- For `create-one-pager`: the more context you provide upfront, the better the output. Even rough bullet points work — paste in meeting notes, Slack threads, or customer feedback.
- For `review-one-pager`: share the file or paste the doc directly in chat. The skill will confirm what it's reviewing before proceeding.
- Both skills use the same 9-section template, so output from `create-one-pager` can feed directly into `review-one-pager` for a quick quality pass.
