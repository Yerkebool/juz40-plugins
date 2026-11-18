---
name: prd
description: Write a PRD / feature spec for a Juz40 feature and publish it as a Confluence page. Use when the user says "write a PRD", "спека", "spec this out", "сделай документ в Confluence", or hands over a grilled plan, a brainstorm outcome or a raw feature request that needs a written document. Not for exploring an idea (use brainstorm) and not for creating tickets (use jira-tasks).
---

# PRD

Turn an idea, a grilled plan or a stakeholder request into a PRD, and publish it to Confluence.

## 0. Check the input is ready

A PRD written over unsettled decisions is fiction. Before writing, scan the input for unanswered questions about roles, scope unit, time/period handling, money and rollout (the list in the `grill` skill). If **three or more** are unanswered, stop and say so: offer to run `grill` first, or to write the PRD with those listed explicitly under *Open questions*. The user chooses. Never invent an answer to make the document look finished.

## 1. Gather context

Ask only for what you cannot find yourself:

- The problem and who has it (if not already given).
- Target Confluence space and parent page (see `references/confluence.md`).
- Related Jira key, if this continues existing work.
- Figma links, if design exists.

Find the rest yourself:

- `docs/README.md` → `docs/context/index.md` → the relevant leaf note, for why existing behaviour is the way it is.
- `docs/structure/modules/<name>.md` for the modules this touches.
- `graphify query "<question>"` for cross-module relationships. Do not grep the vault.
- Jira: `searchJiraIssuesUsingJql` for prior tickets on the same area.
- Confluence: `searchConfluenceUsingCql` for an existing page on this feature — if one exists, **update it instead of creating a duplicate**.

## 2. Write the PRD

Use `references/prd-template.md`. Rules that matter more than the template:

- **Language: Russian**, like the team's Jira tickets and Confluence pages. Domain identifiers stay verbatim from code (`studentGroupMonthlyPayment`, `stream`, `quizbank`).
- **Problem before solution.** If you cannot state who hurts and how often, the PRD is not ready.
- **Goals are outcomes, not outputs.** "Куратор видит долг по группе за 10 секунд" — not "добавить экран задолженности".
- **Non-goals are mandatory.** At least three, each with a one-line reason. This is the section that saves the sprint.
- **Requirements are P0/P1/P2** with acceptance criteria in Given/When/Then. Be ruthless about P0: if everything is P0, nothing is.
- **Every requirement names its roles.** Who sees it, who must not.
- **Edge cases get their own section**, and for Juz40 it must cover: closed periods, transferred/withdrawn students, mid-period joins, retries and idempotency for anything financial, and the blast radius of any notification.
- **Open questions carry an owner** (backend / frontend / design / PM / data) and a blocking-or-not flag.
- Link to source files and vault notes instead of pasting code. No code dumps.

Show the full draft in chat and get the user's edits **before** publishing. Publishing is outward-facing; do not skip this.

## 3. Publish to Confluence

Read `references/confluence.md` for the cloud ID, space and parent-page conventions, and record there anything you had to ask for the first time.

- Create: `createConfluencePage` with `cloudId`, `spaceKey`, `parentId`, `title`, `body` as markdown.
- Update an existing page: `getConfluencePage` first (you need the current version number), then `updateConfluencePage`.
- Title convention: `[PRD] <фича>` — and if the work already has a Jira key, `[PRD][DV-XXXX] <фича>`.
- Ask before publishing to a space the user has not named in this session.

After publishing, report the page URL.

## 4. Hand off

Offer two follow-ups, do not run them yourself:

- **`jira-tasks`** — decompose this PRD into a DV epic, stories and per-role sub-tasks, linked back to this page.
- A `docs/context/business/<topic>.md` note if the PRD settled business rules that outlive this feature. The PRD is the pitch; the vault is the memory.
