---
name: jira-tasks
description: Decompose a PRD, a Confluence page or a described feature into Jira work in the DV project — an Epic, Stories, and per-role sub-tasks ([BACK]/[FRONT]/[QA]/[DESIGN]) — with a dry-run tree the user approves before anything is created. Use when the user says "create tickets", "декомпозируй", "make an epic", "нарежь задачи", or finishes a PRD. For a single ticket off the current branch's diff, the repo's own create-jira-ticket skill is the better fit.
---

# Jira tasks

Turn a written feature into a Jira tree in the **DV** project. Creating issues is outward-facing and awkward to undo, so this skill is **dry-run first, always**.

Config and field rules live in `references/jira.md`. Read it before the first MCP call.

## 1. Read the source

Accept any of: a Confluence PRD URL, a local markdown file, a Jira key to decompose, or a plain description.

- Confluence URL → `getConfluencePage`. Pull problem, requirements with their P0/P1/P2 levels, roles, edge cases, open questions.
- Jira key → `getJiraIssue`, plus its existing children, so you extend the tree rather than duplicate it.
- Plain description → if it has no requirements list, say so and offer `prd` first. Tickets cut from a vague description get rewritten within a week.

Then check for duplicates: `searchJiraIssuesUsingJql` over the DV project for the feature's keywords. Show anything that already exists before proposing new issues.

## 2. Build the tree (in chat, nothing created yet)

**Mapping:**

| PRD element | Jira |
|---|---|
| The feature as a whole | `Epic` — only if the work spans more than ~2 sprints or several modules; otherwise skip the epic and make Stories |
| A user-facing capability (one row of §5/§6) | `Story` |
| The work one role does for that capability | `Sub-task`, prefixed `[BACK]` / `[FRONT]` / `[QA]` / `[DESIGN]` |
| A P2 / future consideration | nothing — it stays in the PRD |

**Rules for good decomposition:**

- **Stories are vertical slices**, not layers. "Куратор видит задолженность группы" is a story; "добавить таблицу в БД" is a sub-task inside it.
- **Summaries in Russian, business-oriented**, describing user-facing behaviour, not code. Match the house style: *«Разрешить пробелы в поле ФИО родителя»*, not *«Убрать директиву appTrimInput»*.
- **A story that cannot be finished in one sprint must be split.** Say which axis you split on (role, period, entity scope).
- **`[BACK]` before `[FRONT]`.** Frontend sub-tasks depend on the backend sibling; record that with `createIssueLink` (`Blocks` / `is blocked by`) so the daily-report priority rule can see it.
- Each sub-task description carries: what changes, acceptance criteria from the PRD, affected modules (link `docs/structure/modules/...`), and the Figma link if there is one.
- Copy the PRD's acceptance criteria into the Story description verbatim. Do not paraphrase ACs — paraphrasing is how requirements drift.

**Present the whole tree as an indented list with issue type, summary, assignee and estimate per node, plus the links you intend to create.** Then ask for approval. Edits are cheap here and expensive after creation.

## 3. Mandatory fields — ask before creating

The DV project rejects issues missing these, and guessing them is worse than asking:

- **Assignee** — resolve the current user via `atlassianUserInfo`, cache for the session, never hardcode an account ID. For sub-tasks owned by another role, ask who takes them, or leave the role prefix and assign to the current user only for `[BACK]`/`[FRONT]` work the user does themselves.
- **Original estimate** — ask per story, Jira format (`30m`, `2h`, `1d`, `1d 4h`). Never default or guess.
- **Sprint** — resolve the active DV sprint via JQL `project = DV AND sprint in openSprints()`, cache it. Ask whether this work goes into the active sprint or the backlog; a whole epic landing in the current sprint is usually wrong.

## 4. Create

Only after explicit approval of the tree.

1. Epic (if any) → Stories → Sub-tasks, parents before children.
2. Link each Story to the Confluence PRD; put the PRD URL in the Epic description too.
3. Create the `[BACK]` → `[FRONT]` blocking links.
4. Create issues one at a time and report keys as they appear. If a call fails, **stop** and report what exists so far — do not retry blindly and do not leave a half-built tree unreported.

## 5. Report

Give the user: the epic/story keys with their summaries, the PRD link, anything you skipped and why, and the open questions from the PRD that still have no owner. Offer to run the repo's `gitflow` skill to start a branch on the first ticket.
