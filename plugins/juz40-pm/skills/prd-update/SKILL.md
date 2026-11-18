---
name: prd-update
description: Change a published Juz40 PRD when a decision changes — find every block, rule, story and AC the change touches, update the page with a decision record and change history, and bring the linked Jira issues, backend contracts and QA test cases in line. Use when the user says "поменялось решение", "обнови доку", "заказчик теперь хочет", "бэк не может сделать так", "после созвона решили", or gives a PRD link together with a change.
---

# PRD update

A PRD goes stale the moment a decision changes in chat, on a call or in a Jira comment. This skill makes the change once and carries it everywhere it lands.

Uses the same block rules as `prd` (`../prd/references/blocks.md`, `../prd/references/writing.md`) and the same Jira settings as `jira-tasks` (`../jira-tasks/references/jira.md`).

## 1. Read the current state

- The PRD: `getConfluencePage` with `contentFormat: html`. HTML keeps inline comments, macros and smart links when the page is written back; markdown would lose them.
- Its child pages: `getConfluencePageDescendants`. Note whether `Backend contracts: …` and `Тест-кейсы: …` exist.
- Its Jira issues: from the passport and «Задачи в Jira»; read each with `getJiraIssue`, including status.

## 2. Pin down the change

Ask, unless already said: **what** changes, **who** decided, **when**, **why**. Treat vague answers as in grilling: «примерно», «как-нибудь», «разработчики решат» are not decisions. Offer concrete options with a recommendation.

If development has already started on what changes (an issue In Progress or Done), say so plainly: the change has a cost, and someone has to agree to it.

## 3. Find everything it touches

Go through the whole page, not just the obvious section:

- Solution, «Что меняется и что нет», scenario, screens.
- Every `US-…` and acceptance criterion, every `R-…`, edge cases, data, versions, «Не входит».
- Open questions the change answers (close them) and new ones it raises (add them).
- Other rules that now contradict the new one.

Outside the page:

- Jira issues whose description or AC quote a changed `US-…` or `R-…`.
- The backend contracts page, if it exists and the change touches data or API.
- The QA test-case page, if it exists: list the `US-…` / `R-…` IDs whose test cases need a rerun.

## 4. Show the impact and wait

Show one table:

| Где | Было | Станет |
|---|---|---|

Then the outside impact: which issues change and how, which teams need to know. Apply nothing until the PM approves.

## 5. Apply

**PRD** (`updateConfluencePage`, `contentFormat: html`, built from the HTML you just read):

- Change the affected blocks. Keep IDs stable: a removed story or rule leaves its number unused; never renumber.
- Add a row to «Решения» (create the block if missing): «Вопрос | Решение | Кто решил | Когда».
- Add a row to «История изменений» (create it if missing): date, author, what changed with the IDs.
- Update «Обновлён» in the passport.

**Jira** (after the same approval):

- Open issues: update the description and AC with `editJiraIssue`.
- Issues already Done that the change reverses: don't rewrite history; propose a new Story or Sub-task instead.

**Other teams' pages** (backend contracts, test cases): never edit them. Offer a footer comment on each that names the changed IDs; post it only on the PM's yes.

## 6. Report

In a few lines: what changed on the page, which issues were updated or created, which comments were posted. Then a short message the PM can paste into the team chat: what changed, why, which IDs, who needs to act.
