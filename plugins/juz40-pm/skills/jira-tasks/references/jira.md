# Jira settings — DV project

| Setting | Value |
|---|---|
| Cloud ID | `93b1beb0-c257-47a6-9917-d6c2acd3e5aa` |
| Project key | `DV` |
| Issue types we create | `Story`, `Sub-task`, `Bug` (check the exact type names with `getJiraProjectIssueTypesMetadata` before the first call) |
| Statuses | `To Do`, `In Progress`, `Done` |
| Content format | `markdown` |
| Summary language | the PRD's language (Russian by default) |

## Rules

- Assignee is required — DV rejects unassigned issues. Get the current user with `atlassianUserInfo`; never hardcode an account ID. Look up anyone else with `lookupJiraAccountId`.
- Original estimate is required. Always ask the PM; never guess.
- No epics. The team works in Stories only; never create an Epic. Stories of one Эпик are tied together with issue links (`createIssueLink`, the «Relates» type; check the exact name with `getIssueLinkTypes`).
- Active sprint: `searchJiraIssuesUsingJql` with `project = DV AND sprint in openSprints()`.
- Need a custom field? Look it up with `getJiraIssueTypeMetaWithFields`; never invent a field ID.
- Sub-task summaries start with the discipline in brackets: `[DESIGN]`, `[BACK]`, `[FRONT]`, `[MOBILE]`, `[QA]`, `[PM]` — the team's existing convention. `[BACK]` Sub-tasks come from backend's contracts page, not from this skill.
- The class goes into every Story description as the line «Класс: <тип> · <аудитория> · <уровень>», so it is visible without opening the PRD.
- Approvals of the core PM are Sub-tasks assigned to the core PM (`templates/approval.md`). The owner's OK is recorded in the PRD passport, not in Jira.

## JQL

- Possible duplicates: `project = DV AND text ~ "<keyword>" ORDER BY created DESC`
- Sub-tasks of a story: `project = DV AND parent = DV-XXXX AND issuetype = Sub-task`
