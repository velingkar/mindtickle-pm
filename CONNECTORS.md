# Connectors

Both skills search external sources before drafting or reviewing. Here's what's used and how to set each one up.

---

## Confluence (Atlassian)

**Used for:** Existing feature specs, past decisions, meeting notes, prior research.

**How it works:** The skills use the Atlassian Confluence MCP tools directly. No placeholders — these are hardcoded references to the real connector.

**Setup:** Connect your Atlassian account in Cowork → Settings → Connectors. Once connected, Confluence search works automatically.

---

## Google Drive

**Used for:** Linked research docs, customer feedback files, prior one-pager versions.

**How it works:** The skills search Google Drive directly. Connect your Google account in Cowork → Settings → Connectors → Google Drive.

---

## MindTickle Help Center

**Used for:** Understanding how a feature area currently works in the product before drafting or reviewing. Gaps between current state and the proposed change are often where one-pagers fall flat.

**How it works:** Uses web search with `site:help.mindtickle.com` — no connector needed. Works out of the box.

---

## MindTickle Compass *(pending setup)*

**Used for:** Querying MindTickle's internal knowledge — git repos, architecture decisions, and Confluence — through a single conversational interface. Particularly useful for understanding technical constraints and existing implementations before scoping milestones.

**How it works:** Compass is a MindTickle-internal chatbot. Once connection details (URL, API key, or MCP server) are available, add them here and update Phase 1 of both skills to query Compass alongside the other sources.

**Status:** Not yet wired up — access method TBD. When ready, queries should look like: "What does our codebase currently support for [feature area]?" and "Are there existing Confluence pages on [topic]?"

---

## What happens with missing connectors

The skills don't warn you about unavailable connectors. They search what's available and move on. You won't see "I don't have X connected" messages — the search either finds something useful or it doesn't.
