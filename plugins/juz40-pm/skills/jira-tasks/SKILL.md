---
name: jira-tasks
description: Create Jira Stories and optional Sub-tasks in the DV project from a Juz40 PRD in Confluence, using the team's issue templates, and write the keys back into the PRD. The team does not use epics. Use when the user says "create tickets", "создай стори", "нарежь задачи", "заведи в джиру", or right after a PRD is published.
---

# Jira tasks

Cut a PRD into DV Stories. The team works in Stories only: never create an Epic. Settings and rules: `references/jira.md` (read before the first Jira call). Description templates: `templates/` (the first line of each file says which issue type it is for).

## 1. Read the source

- A Confluence PRD → `getConfluencePage` (markdown). This is the normal case.
- A Jira key → `getJiraIssue`; if it links a PRD, read that too.
- No PRD yet: say so and offer `prd` first. Plain text works only for a single small Story.

Then look for what already exists:
- the Story the PRD came from (passport «Стори»);
- duplicates and related Stories: `project = DV AND text ~ "<keyword>" ORDER BY created DESC`.

Show what you found before proposing anything.

## 2. Plan the issues

By the PRD's size:

- **Изменение / Фича** → one Story. If a Story already exists with only a link in its description, plan to fill its description, not to create a new one.
- **Большая фича** → one Story per version or stage from «Версии», each a piece users can see working. Summaries carry the version: «<Название> · v1: …». The Stories are linked to each other («Relates») and each one links the PRD.
- **Sub-tasks** → propose them by discipline from «Ответственные»: `[DESIGN]`, `[BACK]`, `[FRONT]`, `[MOBILE]`, `[QA]`, `[PM]`. Create them only if the PM says yes.

Fill the matching template for each issue. Acceptance criteria are copied from the PRD with their IDs (`US-01`, `R-03`), not retold. Summaries are about what the user gets, in the PRD's language.

## 3. Show the plan and wait

Show every planned issue: type, parent (for Sub-tasks), summary, full description, links. Ask for what you must not guess:

- **Original estimate** for each issue (`2h`, `1d`, `1d 4h`).
- **Sprint**: the active sprint or the backlog.
- **Assignee**, if not the PM.

Create nothing until the PM approves the plan.

## 4. Create

- Stories first, then the links between them (`createIssueLink`), then Sub-tasks with their Story as parent.
- An existing Story is updated with `editJiraIssue`, not recreated.
- If a call fails, stop and report what was already created. Don't retry blindly.

## 5. Write back to the PRD

Update the PRD page (`getConfluencePage`, then `updateConfluencePage`, both with `contentFormat: html` so inline comments and macros survive): the passport «Стори» row and the «Задачи в Jira» block with every key and one line each. Tell the PM it's done.

Finish with the list of created or updated keys and their links.
