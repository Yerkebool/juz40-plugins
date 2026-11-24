---
name: context-doc
description: Write a Juz40 context document «<Название> — контекст» in Confluence — the request and the facts, not the solution — so a PM can hand a feature or an epic to its owner, who then runs feature-flow. Use when the PM says "контекстный документ", "контекст-док", "передать фичу", "передаю оунеру", "оформи запрос", or has a request from methodists, curators, sales or the business that someone else will lead.
---

# Context document

The PM writes it and hands it to the feature's owner. From then on the owner leads: brainstorm, PRD, design, tasks (`feature-flow`). The document stays the source of truth about the request. It holds the request and the facts, never the solution.

Template: `templates/context.md` (a copy of Confluence «Шаблон: Контекстный документ», page `869007362`; if they differ, Confluence wins). Example: «TOEFL ITP тренажёр — контекст» (page `869072898`). Writing rules: `../prd/references/writing.md`. Confluence settings: `../prd/references/confluence.md`.

Talk to the PM in the language they write in.

## 1. Collect

1. Take what the PM gave: messages from the customer, a call summary, a Jira key, a link.
2. Ask in one message only what is missing for the template: who asks (name and role), the owner (by name), what is needed and for whom, why now, the metric or «не измерено».
3. Look up «Что уже есть» yourself: existing features, data and docs in Confluence SD and Jira DV that the request builds on. Each item is a link with one line on why it matters here.

## 2. Write

Fill `templates/context.md` from top to bottom.

- «Как это видит заказчик»: the scenario per role as the customer described it, in their terms. Your ideas don't go here.
- «Что решили»: only what someone actually decided, with who and when.
- A solution nobody asked for, or a guess → «Открытые вопросы», with who knows the answer.
- Title: `<Название> — контекст`.

## 3. Check

The «Проверка перед передачей» list of the template: reads in 2 minutes; no decisions the customer didn't make; every link says why it is there; the metric is filled in or honestly «не измерено»; the owner is named. Plus the banned-phrase search from `writing.md`.

## 4. Show, publish, hand over

1. Show the draft in chat. Apply the PM's edits. Publish only after an explicit OK.
2. Search first (`space = SD AND title ~ "<keyword>"`); don't create a second page for the same request. Propose the parent the PM uses for this product. `createConfluencePage`, `contentFormat: markdown`. Status «Черновик».
3. Write the PM a short message for the owner: what is needed, the link, the open questions, and the next step — «запусти `feature-flow` с этой ссылкой». When the PM has sent it, the status becomes «Передан оунеру <дата>»; when the owner accepts, «Принят оунером <дата>».

Later changes to the request are written into this page («Что решили», «Открытые вопросы») and dated in «Обновлён». Once a PRD exists, decisions that change it go through `prd-update`.
