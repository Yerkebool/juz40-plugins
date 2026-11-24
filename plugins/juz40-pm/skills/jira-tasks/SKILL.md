---
name: jira-tasks
description: Create and fill Juz40 Jira issues in the DV project from the team's templates — the Story at intake, approval Sub-tasks for the core PM, the Story description and discipline Sub-tasks after the owner's OK on the PRD, and Bugs. Writes the keys back into the PRD. The team does not use epics. Use when the user says "create tickets", "создай стори", "нарежь задачи", "заведи в джиру", "заведи баг", or when feature-flow calls it.
---

# Jira tasks

DV works in Stories and Sub-tasks, plus Bugs. Never create an Epic. Settings and rules: `references/jira.md` (read before the first Jira call). Templates: `templates/` (the first line of each says what it is for).

## Modes

| Mode | When | Creates | Template |
|---|---|---|---|
| **Intake** | `feature-flow` stage 0, the task has no Story | One Story with a short description | `story-intake.md` |
| **Approval** | High: core PM approval of the brief or the package | A Sub-task under the Story | `approval.md` |
| **After the owner's OK** | The PRD is «Согласовано оунером» | Fills the Story; Sub-tasks by discipline; Stories per version for an Эпик | `story.md`, `subtask.md` |
| **Bug** | It worked before or works differently from the PRD | One Bug | `bug.md` |

## 1. Read the source

- **Intake:** the brief (class, owner, one-line description).
- **Approval:** the brief or the PRD, and the Story.
- **After the owner's OK:** the PRD (`getConfluencePage`, markdown): PRD для агентов for a Фича or an Эпик, the single page for an Изменение. Check the passport: status «Согласовано оунером» and the owner's approval recorded. If not, say so and stop: Sub-tasks are cut only after the owner's OK.
- **Bug:** what the PM or QA reported; the PRD of the feature, if there is one, to quote the broken `US-…` or `R-…`.

Then look for what already exists: the Story (passport «Стори»), duplicates and related issues (`project = DV AND text ~ "<keyword>" ORDER BY created DESC`). Show what you found before proposing anything.

## 2. Plan the issues

**Intake:** one Story. Summary: what the user gets, in the PM's language.

**Approval:** one Sub-task, «[PM] Апрув кор PM: берём в работу» or «[PM] Апрув кор PM: пакет перед разработкой», assigned to the core PM.

**After the owner's OK:**

- **Изменение / Фича** → fill the existing Story's description from `story.md` with `editJiraIssue`; don't create a second Story.
- **Эпик** → the intake Story becomes v1; one more Story per later version from «Версии», each a piece users can see working. Summaries carry the version: «<Название> · v2: …». Link the Stories to each other («Relates»); each links the PRD.
- **Sub-tasks** → by discipline from «Ответственные», using `subtask.md`: `[DESIGN]` only if there is UI and it is not done yet, `[FRONT]`, `[MOBILE]`, `[QA]`, `[PM]` (metric after release, for students). Don't create `[BACK]`: backend creates its own Sub-tasks from the contracts page. Create a `[BACK]` placeholder only if the PM asks.
- Acceptance criteria are copied from the PRD with their IDs (`US-01`, `R-03`), not retold.

**Bug:** one Bug from `bug.md`. Severity from its impact; ask the PM if unsure.

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

After the owner's OK mode and the Approval mode, update the PRD (`getConfluencePage`, then `updateConfluencePage`, both with `contentFormat: html` so inline comments and macros survive):

- the passport «Стори» row (and «Апрув кор PM» with the Sub-task key);
- the «Задачи в Jira» block with every key and one line each.

In the after-the-owner's-OK mode, also close the brief: «Где мы: Discovery закрыт ‹дата›», one row in «Журнал».

Finish with the list of created or updated keys and their links.
