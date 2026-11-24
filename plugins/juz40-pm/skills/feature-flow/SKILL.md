---
name: feature-flow
description: Run Juz40 discovery for a feature or an epic from idea (or a «— контекст» document) to the owner's OK, everything except design — intake and task class (type, audience, Product complexity low/mid/high), brainstorm, grilling with must-ask questions, readiness gate, metric, core PM approval, PRD in Confluence, remarks loops after ПБР / design / QA, owner's OK, Jira sub-tasks. Use when a PM starts any new feature, change or bug ("новая фича", "есть идея", "пришла задача от бизнеса", "надо сделать доку и задачи", "давай с нуля", "вернулись замечания после ПБР / от QA / от дизайнера") or brings a Jira key or a request and wants the whole thing done.
---

# Feature flow

Discovery for every Juz40 task, up to design and around it:

**intake and class → brainstorm → grill → readiness → metric → core PM approval → PRD → design (not here) → remarks loop → owner's OK → Jira sub-tasks**

Design is not part of this skill: `prd-to-design`, SU10 and the designer's review do it. This skill hands off to design and takes the remarks back.

The handoff between stages is the **brief** (`references/brief.md`). Rules:

| What | File |
|---|---|
| Type, audience, Product complexity and what they change | `references/complexity.md` |
| Questions that must be answered at each stage | `references/must-ask.md` |
| What must be known before the PRD | `references/readiness.md` |
| When to go back to brainstorm or grilling | `references/loops.md` |

The stages are a means, not a ritual: skip whatever the brief already settles. Never skip the class and the readiness gate.

Talk to the PM in the language they write in (Russian or Kazakh).

## 0. Intake and class

1. **Context document.** If the task has a «<Название> — контекст» page (search `space = SD AND title ~ "контекст" AND text ~ "<keyword>"`, or the link the person gave), read it first. It is the source of truth for the request: «Что решили» are decisions with their authors, «Границы» is the scope, «Как это видит заказчик» is the customer's scenario (input, not a chosen solution), «Метрика» feeds stage 4, «Открытые вопросы» open the first grilling round. Never ask again what it already answers.
   No context document, and the PM is about to hand the task to someone else to lead → offer `context-doc` first.
2. Ask, in one message, the intake questions (`must-ask.md` §0) that the context document and the message did not answer.
3. Look things up before anything else:
   - Jira DV: the given key, and `project = DV AND text ~ "<keyword>" ORDER BY created DESC` for related work.
   - Confluence SD: the base feature, a previous version, related specs (`space = SD AND text ~ "<keyword>"`).
   Show what you found in at most five lines, with links.
4. **Class.** Propose type, audience and Product complexity by `complexity.md`, naming the criterion that fired: «high — трогает оплату (критерий 1)». The PM confirms. The owner confirms too: if they haven't yet, it is an open question that must close before the owner's OK in stage 8.
5. **Path.** For someone who joins without context, show the path for this class in at most six lines: the stages ahead, what each produces, who approves where. Example: «Фича · студенты · mid: прожарка → метрика → PRD (2 страницы) → макеты → замечания → «ок» оунера → Sub-tasks. Кор PM не нужен».
6. **Баг** → stop here. Load `jira-tasks` in bug mode; QA takes it to `/triage`. No brainstorm, no PRD.
7. **Story.** Find the DV Story for this task. If there is none, load `jira-tasks` in intake mode to create it. Discovery runs under that Story.
8. Pick the entry point and say it in one line:
   - Nothing decided yet, or the level is high → **1. Brainstorm**.
   - The direction is decided («бизнес сказал, делаем X») and the level is low or mid → **2. Grill**.
   - A context document or detailed notes exist → build the brief from them; its open questions go to **2. Grill**, or straight to **3. Readiness** if there are none.
   The PM can jump to any stage at any time.

## 1. Brainstorm

Required for high, optional for low (`complexity.md` §5). Load `product-brainstorming` and follow it, with this framing:

- Let the PM describe the logic freely first. Don't interrupt with structure; take notes into the brief.
- Think in Juz40 terms: roles (Студент, Родитель, Куратор, Завуч / координатор, Методист, Менеджер / админ, Профориентолог), platforms (Web, мобильное приложение), UI language (Kazakh first), the ҰБТ calendar, monthly payments and продление.
- Before converging, every question of `must-ask.md` §1 for the level has an answer in the brief. For high, assumption testing is not optional: name the riskiest assumption and the cheapest check.
- Ideas that are good but not for now go to «Идеи на потом».

Done when the PM names the direction. Show the problem / direction part of the brief in five lines and move on.

## 2. Grill

Load `grilling` and follow it. The root of the design tree is `readiness.md`, in its order. The minimum question set is `must-ask.md` §2 for the level.

- Facts are yours to find, not the PM's. Recommended answers lean on how the platform already works («как в курсе ученика», «как в v1»).
- Every round, put the answers into the brief. Quote the PM's own words for decisions.
- Ask only about the branches the class needs.

## 3. Readiness gate

Check the brief against `readiness.md`, including the class itself. Show:

| Тема | Статус | Что не так |
|---|---|---|

✅ settled · ⚠ vague · ❌ missing · ⛔ contradicts an earlier answer or an existing doc.

- **All ✅** → show the full brief, the PM confirms it, go on.
- **Anything else** → name the loop (`loops.md`) and run the second grilling pass on the gaps only. Each question quotes the vague answer, says why it isn't enough to build from, and offers concrete options with a recommendation.
- Limits and escalation: `loops.md` rules 3 and 4. The PM can say «пиши с открытыми вопросами» at any point, except for high blockers (rule 3).

Never let a vague answer pass into the PRD as a fact.

## 4. Metric

- Load `feature-metrics`, part A, with the brief. Part B (events) runs inside `prd` for the agent page.
- Сотрудники: one line in the brief, «метрика после релиза не нужна: фича для сотрудников».
- High: the baseline is real numbers with a source and a date.
- A baseline that shows the problem is small or absent is a loop signal (`loops.md`).

## 5. Core PM approval — high only

1. Show the brief to the PM as a summary for the core PM, at most 15 lines: class, problem, direction, metric, riskiest assumption, open questions.
2. Load `jira-tasks` in approval mode to create the Sub-task «[PM] Апрув кор PM: берём в работу».
3. Publish the PRD only after the core PM's «да». The PM may let you draft it meanwhile.

## 6. PRD

Load `prd` with the confirmed brief. One page for an Изменение; two pages (for people and for agents) for a Фича and an Эпик.

## 7. Hand off to design

- UI changes → the next step is `prd-to-design`, then the designer's review. Say so and stop here. The PM comes back with the result or with remarks.
- No UI → go to 8.

**Coming back with remarks** (ПБР, the designer, `prd-to-design`, QA `/spec-readiness`): read the PRD and the Story, list the remarks, sort each one by `loops.md`, show the sorting in a table «Замечание | Куда | Почему», and run the loops. After the PRD is published, changes go through `prd-update`.

## 8. Owner's OK

The package is the PRD, the mockups and the test cases. The owner has 2 working days; silence is not consent. High: the core PM approves the package too (Sub-task «[PM] Апрув кор PM: пакет перед разработкой», via `jira-tasks` approval mode).

1. Write the PM a short message for the owner: class, what changes, links to both PRD pages, Figma, test cases, open questions.
2. When the PM reports the OK, record it in both PRD passports: «Согласовано оунером: <имя>, <дата>» (`updateConfluencePage`, `contentFormat: html`), and set both pages' status to «Согласовано оунером <дата>».
3. Unconfirmed class from stage 0 closes here.

## 9. Jira

Load `jira-tasks` with the approved PRD. It fills the Story and creates the Sub-tasks.

## 10. Finish

Give the PM, in a few lines:

- the PRD links and the issue keys;
- what other teams take from here: backend writes `Backend contracts: <Название>` and its own `[BACK]` sub-tasks, QA writes test cases from the User Stories;
- the open questions that still block development, with owners.

## Long tasks

The brief lives in the conversation. Discovery usually spans several sessions (design and QA happen in between): offer to save the brief as `brief-<slug>.md` in the current folder. A new session reads it and the PRD, says where the task is, and continues from that stage.
