# PRD blocks

A PRD is assembled from blocks. Some are required for the type; the rest go in only when their trigger fires. Blocks always appear in the order below. Number the sections from 1 in the final document, skipping the lead and the passport.

**Where blocks live:**

- **Изменение:** one page with every block it needs (`../templates/izmenenie.md`).
- **Фича, Эпик:** two pages. The **PRD для людей** (`../templates/people.md`) carries blocks 1 Проблема, 2 Цель, 3 Решение, 4 Что меняется (as «Кого касается»), 5 Сценарий (as «Как это работает», 5–7 steps), 18 Не входит (as «Чего не будет»), 26 Решения, 27 Открытые вопросы, in its own plain form. The **PRD для агентов** (`../templates/feature.md`, `../templates/epic.md`) carries every other block, and links to the parent for those eight instead of repeating them. Block 5 goes on the agent page too only when the 5–7 steps are not enough to build from.

Legend: **И** = Изменение, **Ф** = Фича, **Э** = Эпик. ● required · ○ only when the trigger fires · — never.

**Added by the class** (`../../feature-flow/references/complexity.md`), for any type:

- **high:** 13 Данные, 21 Релиз, 23 Что проверяем, 25 Риски.
- **Студенты:** 16 Аналитика when the goal has a metric; 21 Релиз when there is a toggle or cohorts.
- **Сотрудники:** 2 Цель says in one line why there is no metric after release.

| # | Block | И | Ф | Э | Trigger (for ○) |
|---|---|---|---|---|---|
| 0 | Лид | ● | ● | ● | |
| 0 | Паспорт | ● | ● | ● | |
| 1 | Проблема | ● | ● | ● | |
| 2 | Цель | ● | ● | ● | |
| 3 | Решение | ● | ● | ● | |
| 4 | Что меняется и что нет | ● | ● | ● | |
| 5 | Сценарий | ○ | ● | ● | И: the change alters a sequence of steps |
| 6 | Экраны и элементы | ○ | ○ | ○ | UI changes and the design alone does not say how elements behave |
| 7 | User Stories | ● | ● | ● | QA writes test cases from them, so every type has at least one |
| 8 | Правила и логика | ○ | ● | ● | И: any rule beyond what the AC say |
| 9 | Роли и доступ | ○ | ○ | ● | more than one role, or anyone must not see or do something |
| 10 | Сроки и периоды | ○ | ○ | ○ | behaviour depends on dates, deadlines, weeks, months, schedules |
| 11 | Справочники и маппинги | ○ | ○ | ○ | there is a list of values, statuses, reasons, or a mapping between two lists |
| 12 | Краевые случаи | ○ | ● | ● | И: an edge case that is not already an AC |
| 13 | Данные | ○ | ○ | ● | new data is stored, or existing data is read in a new way |
| 14 | Что переиспользуем | — | ○ | ○ | the feature is built on existing APIs, modules or screens |
| 15 | Старые данные и совместимость | ○ | ○ | ○ | existing records, old versions or old clients are affected |
| 16 | Аналитика | — | ○ | ● | the goal has a metric, or a new user action must be counted |
| 17 | Версии | — | — | ● | |
| 18 | Не входит | ○ | ● | ● | И: someone could expect more than is done |
| 19 | Ответственные | ○ | ● | ● | И: more than one person besides the PM |
| 20 | Зависимости | ○ | ● | ● | И: something must exist first |
| 21 | Релиз | — | ○ | ● | toggle, pilot, deployment order, backend and frontend must ship together |
| 22 | Вехи | — | ○ | ● | Ф: there is a target date or a pilot date |
| 23 | Что проверяем | — | ○ | ● | a risky rule, a calculation, or a regression area worth naming |
| 24 | Пример на реальных данных | — | ○ | ○ | numbers or calculations must match production; a real case shows them |
| 25 | Риски | — | ○ | ● | a deadline, a dependency or a capacity risk |
| 26 | Решения | ○ | ○ | ○ | decisions were taken by someone other than the PM, or changed an earlier assumption |
| 27 | Открытые вопросы | ● | ● | ● | |
| 28 | Идеи на потом | — | ○ | ○ | the brainstorm parked ideas |
| 29 | Сообщение пользователям | — | ○ | ○ | users see something new and should be told |
| 30 | Задачи в Jira | ● | ● | ● | filled by `jira-tasks`; until then «Будут созданы после согласования» |
| 31 | История изменений | — | ○ | ● | Ф: the document is an update of an existing one |

## Block rules

### Лид
One or two sentences in bold above the passport: what we do and for whom. Someone who reads only this knows what the page is about.

### Паспорт
A two-column table. Rows:

| Поле | Значение |
|---|---|
| Статус | Черновик · На согласовании · Согласовано оунером <дата> · В разработке · Выпущено (see `confluence.md`) |
| Класс | Фича · студенты · high |
| Продукт и платформы | Juz40: кабинет родителя (Web, App), кабинет куратора (Web) |
| Ведущий (PM) | name |
| Оунер | name |
| Кор PM | name (high only) |
| Заказчик | name or «не определён (ОВ-N)» |
| Согласовано оунером | «имя, дата» or «нет» |
| Апрув кор PM | «✅ имя, дата, DV-XXXX» (high only) |
| Стори | DV-XXXX (several for an Эпик) |
| PRD для людей / PRD для агентов | link to the other page of the pair (Фича, Эпик) |
| Дизайн | Figma link per role, or «без дизайна — …» |
| Связанные документы | base feature, previous version |
| Backend contracts | child page `Backend contracts: <Название>` (backend team) |
| Тест-кейсы | child page `Тест-кейсы: DV-XXXX — <Название> — Full + Edge Cases` (QA) |
| Обновлён | date |

Add «Целевой релиз» when there is a date. A missing value is written as what is missing and why, never left blank.

### Проблема
Four labelled lines: **Кто** · **Что сейчас** (facts) · **Почему это плохо** (the cost, with numbers when known) · **Источник**. A table with «Проблема | Почему это плохо» when there are more than three problems.

### Цель
What is different after release, for whom, in one to three bullets. Then «Метрика: сейчас → цель → где смотрим», or a table for several metrics. If there is no metric, one line on why.

### Решение
The approach in a few bullets: what the user gets, not how the code works. Then **Рассматривали и отказались:** … — потому что ….

### Что меняется и что нет
A table: «Раздел / экран | Меняется? | Что будет». Rows that do **not** change are as important as the ones that do. For an Изменение, write this block as: **Срабатывает только если:** numbered conditions · **В остальных случаях:** … · **Что не меняется:** ….

### Сценарий
Numbered steps from entry point to result. One actor per step, named. Branches as sub-steps.

### Экраны и элементы
Per screen, a table «Элемент | Правило». Only behaviour the design does not show: what is shown when, where it leads, what states exist.

### User Stories
One sub-heading per story: `US-01 · Название`. Then a table:

| Роль | … |
|---|---|
| Действие | хочу … |
| Ценность | чтобы … |
| Критерии приёмки | numbered list |
| Версия | v1 (Эпик only) |

Each acceptance criterion is checkable with yes/no and starts with a tag: **[Happy path]**, **[Состояние]**, **[Ограничение]**, **[Edge]**, **[Regress]**, **[Нельзя]** (what must not happen). Every story has at least one [Edge] or [Нельзя]. An Изменение usually has one or two stories; for it, «Ценность» may be one line.

### Правила и логика
Numbered rules `R-01`, `R-02`, …. Each rule is one statement with its numbers and ends with the stories it serves: «(US-01, US-03)». A rule that is not served by any story is either a missing story or not needed.

### Роли и доступ
A table «Роль | Видит | Может | Не может».

### Сроки и периоды
A table «Период | Когда начинается и заканчивается | Что видит пользователь | Что делает другая роль». State the time zone when it matters (Asia/Almaty).

### Справочники и маппинги
The full list, never «и т.д.». A mapping is a two-column table. Say who maintains the list (code seed or admin panel).

### Краевые случаи
A list, each item «Ситуация → что происходит». Only cases not already covered by an AC; link to the rule when there is one.

### Данные
What new data is stored and its meaning, in a table «Поле | Тип | Что это». Names are proposals until the contracts page fixes them; say so once. Contract details belong on the `Backend contracts` page, not here.

### Что переиспользуем
A table «Что | Где (эндпоинт, модуль, экран)». Then what is built new.

### Старые данные и совместимость
What happens to existing records, old versions of the feature, and old app versions. What is not migrated.

### Аналитика
A table «Событие | Когда срабатывает | Свойства | Где смотрим».

### Версии
A table «Версия | Что входит | Почему здесь». v1 is the minimum on which the hypothesis is checked. Each version becomes one Story in Jira.

### Не входит
A list, each item **«…» — потому что …**.

### Ответственные
A table «Сторона | За что отвечает | Кто». Rows for those involved: PM, заказчик, дизайн, бэкенд, фронт, мобильное приложение, QA. «Не назначен» is a valid value and also an open question.

### Зависимости
A table «Что нужно | Зачем | Кто | Статус (ЕСТЬ / НЕТ / НЕ ПРОВЕРЕНО)». Then related DV issues as links.

### Релиз
Order of deployment, toggles, pilot group, what ships together, what happens if it must be rolled back. If mobile is in scope, say whether web waits for it.

- **Студенты · high:** toggle OFF by default; cohorts by subject or stream, in order, 3–7 days each; the owner decides each move to the next cohort.
- **Студенты · low, mid:** the owner's decision on toggle and cohorts, in one line.
- **Сотрудники:** «Сразу всем после решения оунера о релизе».

### Вехи
A table «Этап | Оценка | Дата» (design, contract, backend, frontend / mobile, QA and release). «Не оценено» is a valid value. Then one line: **Что можно делать независимо от бэкенда:** ….

### Что проверяем
Three lines, not test cases: **Ключевые сценарии** · **Регресс: что не должно сломаться рядом** · **Главный риск корректности**. QA's test cases are a separate page.

### Пример на реальных данных
One or two real cases with the expected numbers, so developers and QA can check the calculation against production. Identify people by account ID or role only: never a name with a phone number, an email or other contact data. Say where the numbers come from and as of which date.

### Риски
A list, each risk with what we do about it.

### Решения
A table «Вопрос | Решение | Кто решил | Когда». Decisions taken during grilling go here when the PM wants a record of them.

### Открытые вопросы
A table «# | Вопрос | Кто отвечает | Статус (ОТКРЫТ / ЗАКРЫТ)». Number them `ОВ-1`, `ОВ-2` and refer to them from other blocks: «не определено (ОВ-3)». If there are none, write «Нет».

### Идеи на потом
A short list from the brainstorm. Not a promise.

### Сообщение пользователям
The announcement text in Kazakh as a quote, one per audience (оқушы, ата-ана, куратор). If not ready: «Готовим после утверждения дизайна».

### Задачи в Jira
The Stories and their sub-tasks with keys and one line each; for an Эпик, which version each Story delivers. Filled by `jira-tasks`.

### История изменений
A table «Дата | Автор | Что изменилось».
