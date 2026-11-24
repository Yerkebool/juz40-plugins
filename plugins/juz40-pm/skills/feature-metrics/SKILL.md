---
name: "feature-metrics"
description: "Set and check a Juz40 feature's success metric: baseline → target → where we look before the PRD, analytics events for the PRD, and the post-release verdict."
---

# Метрика фичи

Three moments in the workflow:

- **A. Требования** (step 1): what we measure, the number today, the target.
- **B. PRD для агентов**: analytics events that let us compute it.
- **C. После релиза** (step 15): the numbers against the target, and a verdict.

Talk to the PM in the language they write in. Never invent a number: a missing baseline is «не измерено», a missing target is an open question.

## A. Метрика цели (до PRD)

1. **One main metric** and at most two **guard metrics**: what must not get worse (for example продление, жалобы, время на уроках).
2. For each metric write:
   - **Формула:** what is divided by what, over which period. «DAU = уникальные ученики, открывшие приложение за день».
   - **Кто считается:** all students, paying students only, App only, a pilot group.
   - **Сейчас:** the current value. Find it yourself if the session has analytics access (GA4 or another analytics connector, a dashboard link from the PM). Otherwise «не измерено» plus who measures it by when, as an open question.
   - **Цель:** the PM's number and a date. A target without a date is not a target.
   - **Где смотрим:** a report or dashboard link. No report yet → who builds it, as an open question.
3. **Гипотеза** in one line: «Если ‹что делаем›, то ‹метрика› вырастет с ‹N› до ‹N› к ‹дата›, потому что ‹почему›».
4. Juz40 seasonality: the ҰБТ calendar and monthly payment cycles move activity. Name the season the target is set for.

Output: the line «Как поймём, что сработало» for the human PRD, the metrics for the brief, and open questions for every gap.

## B. События в PRD для агентов

1. Search existing events for this area first and reuse their names.
2. New events: `object_action`, snake_case, past tense (`story_published`), unless the team already has another convention.
3. Table «Событие | Когда срабатывает | Свойства | Платформа (Web, App) | Кто шлёт (клиент или сервер)».
4. Check: the main and guard metrics can be computed from these events plus data that already exists. If one can't, add the missing event.

## C. Итог после релиза

1. **Когда:** the date from the PRD. No date → propose two full weeks after release to everyone, and confirm with the PM.
2. **Как сравниваем:** the same period length before and after, the same segment. Note what else happened in that window: holidays, ҰБТ dates, other releases.
3. Table «Метрика | Было | Цель | Стало | Итог».
4. **Вердикт:** «сработало» (target reached), «частично», «не сработало», or «хуже» (a guard metric got worse).
5. **Следующий шаг:** оставить, доработать или откатить. The skill proposes; the owner decides.
6. Write the result into the human PRD as a section «Итог после релиза» and as a comment on the Story in DV.