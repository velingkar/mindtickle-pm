# Jira Export Reference

Instructions for exporting confirmed user stories to Jira using the Atlassian MCP.

---

## Pre-export Checklist

Before creating any Jira issues:
- [ ] All stories in the batch are confirmed by the user
- [ ] User has provided a Jira project key
- [ ] User has specified the issue type (Story, Task, or User Story)
- [ ] Any labels, components, or epic link have been noted

---

## Step 1 — Validate the project

Use `getVisibleJiraProjects` to confirm the project exists and retrieve available issue types.

```
getVisibleJiraProjects(cloudId, searchString: [project key])
```

If the project isn't found, ask the user to check the key and try again.
Use `getJiraProjectIssueTypesMetadata` to find the correct issue type ID for the project.

---

## Step 2 — Format the description

Jira descriptions use Atlassian Document Format (ADF) or Markdown depending on the project. Use `contentFormat: "markdown"` for all story descriptions.

Format each story body as follows:

```markdown
**As a** [user role], **I want to** [action], **so that** [benefit].

---

**Design reference:** [link or "TBD"]

---

**Acceptance Criteria**

1. [Criterion]
2. [Criterion]
3. [Criterion]
4. [Criterion]
5. [Criterion]
6. [Criterion — if applicable]
```

---

## Step 3 — Create issues

Use `createJiraIssue` for each story. Map fields as follows:

| Story field | Jira field |
|---|---|
| Story title | `summary` |
| Full description block | `description` |
| Issue type from user | `issueTypeName` |
| Project key from user | `projectKey` |
| Labels (if provided) | `additional_fields.labels` |
| Epic link (if provided) | `additional_fields.customfield_10014` (or relevant epic link field) |

**Create stories in the confirmed order.** Do not batch all at once — create one, confirm the returned issue key, then create the next. This avoids silent failures.

---

## Step 4 — Report results

After each story is created, capture the issue key and URL. When all are done, present a summary:

```
✅ Created [N] stories in [PROJECT]:

[MT-101] View completion score for a finished roleplay
  → https://mindtickle.atlassian.net/browse/MT-101

[MT-102] Retry a roleplay from the score screen
  → https://mindtickle.atlassian.net/browse/MT-102

[MT-103] ...
```

---

## Error Handling

| Error | What to do |
|---|---|
| Project not found | Ask user to verify the project key. Use `getVisibleJiraProjects` to list available projects. |
| Issue type not valid | Use `getJiraProjectIssueTypesMetadata` to show available types for that project and ask user to pick one. |
| Missing required field | Ask the user for the missing value — don't guess or leave it blank. |
| Rate limit / timeout | Pause, inform the user, and offer to retry from the failed story onward. |

---

## Fallback — Markdown export

If the user declines Jira export or Jira is unavailable, save all confirmed stories as a single Markdown file:

```
one-pager-[feature-name]-stories-milestone-[N].md
```

Format: one H2 heading per story, with description and acceptance criteria beneath. Include a header row listing the milestone name, total story count, and date.
