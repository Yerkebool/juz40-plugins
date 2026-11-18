# Jira config — DV project (Juz40)

| Setting | Value |
|---|---|
| Cloud ID | `93b1beb0-c257-47a6-9917-d6c2acd3e5aa` |
| Project key | `DV` |
| Issue types | `Epic`, `Story`, `Task`, `Sub-task`, `Bug` |
| Workflow statuses | `To Do`, `In Progress`, `Done` — there is no In Review |
| Content format | `markdown` |
| Summary language | Russian, business-oriented |

If the repo already has a `jira-workflow` skill (it exists in `juz40-front/.claude/skills/`), prefer calling it for ticket fetch, transitions, worklogs and sub-task creation instead of reimplementing the MCP plumbing here. This file is the fallback, and the two must not disagree — if they do, `jira-workflow` wins.

## Hard rules

- **Assignee is mandatory.** Resolve the current user with `atlassianUserInfo` once per session and cache. Never hardcode an account ID.
- **Original estimate is mandatory.** Ask the user. Format: `w` / `d` / `h` / `m` (`1d` = 8h, `1w` = 5d).
- **Sprint.** New work joins the active sprint only when the user says so. Resolve it via `searchJiraIssuesUsingJql` on `project = DV AND sprint in openSprints()`.
- **Never invent a custom field.** Look it up with `getJiraIssueTypeMetaWithFields` first.
- **Do not transition tickets owned by other roles.** `[BACK]`, `[QA]`, `[DESIGN]`, `[PM]` sub-tasks are read-only unless the user owns them.
- **MR titles come from the Jira summary verbatim**: `[DV-XXXX] <summary>`.

## Sub-task prefixes

`[BACK]` backend · `[FRONT]` frontend · `[QA]` testing · `[DESIGN]` design · `[PM]` product
`[BUG]` prefixes a sub-task that fixes a defect inside a parent story.

## Useful JQL

- Duplicates: `project = DV AND text ~ "<keyword>" ORDER BY created DESC`
- Active sprint: `project = DV AND sprint in openSprints()`
- Epic children: `project = DV AND parent = DV-XXXX`
