# Jira settings — DV project

| Setting | Value |
|---|---|
| Cloud ID | `93b1beb0-c257-47a6-9917-d6c2acd3e5aa` |
| Project key | `DV` |
| Issue types | `Epic`, `Story`, `Task`, `Sub-task`, `Bug` |
| Statuses | `To Do`, `In Progress`, `Done` |
| Content format | `markdown` |
| Summary language | Russian |

## Rules

- Assignee is required — DV rejects unassigned issues. Get the current user with `atlassianUserInfo`; never hardcode an account ID.
- Original estimate is required. Always ask the user; never guess.
- Active sprint: `searchJiraIssuesUsingJql` with `project = DV AND sprint in openSprints()`.
- Need a custom field? Look it up with `getJiraIssueTypeMetaWithFields`; never invent a field ID.

## JQL

- Possible duplicates: `project = DV AND text ~ "<keyword>" ORDER BY created DESC`
- Children of an epic: `project = DV AND parent = DV-XXXX`
