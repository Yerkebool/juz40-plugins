# Task class: type, audience, Product complexity

The class decides the path. The lead (ведущий) proposes it at intake, the PM confirms, the owner confirms. Record it in the brief, the Story and the PRD passport as one line: `Фича · студенты · high`.

Re-check the class at the readiness gate and after every loop (`loops.md`). If it changes, the path changes from that point.

## 1. Type: what we write

| Type | When | Discovery | PRD |
|---|---|---|---|
| **Баг** | It worked before, or it works differently from the PRD. | No brainstorm, no PRD. Jira Bug from `../../jira-tasks/templates/bug.md`, then QA `/triage`. | none |
| **Изменение** | Changes existing behaviour. No new screen, no new role. A few days of work. | Short: grill only the required topics. | one page |
| **Фича** | New behaviour or a new screen. One release, one Story. | Full | two pages: for people + for agents |
| **Эпик** | More than one release (versions or stages). One Story per version. | Full | two pages, with «Версии» |

- A «баг» where the PRD says nothing, or where the fix needs new behaviour, is an Изменение or a Фича.
- New screens or a new role make an Изменение a Фича. A second release makes a Фича an Эпик. Many roles or teams alone don't: that is the level (mid, criterion 3).
- Эпик is a document type. Jira has no epics: one Story per version, linked to each other.

## 2. Audience: who sees it

| Audience | Who | What it changes later |
|---|---|---|
| **Студенты** | Students and parents: the people who learn and pay. All parents count towards the 30% of criterion high 2. | Toggle and cohorts on release, load tests, analytics events, metric after release. |
| **Сотрудники** | Методист, куратор, завуч / хэдтичер, профориентолог, менеджер, админка. | Released to everyone at once. No metric after release: one line in the PRD says why. |

If both see it, the audience is **Студенты**.

## 3. Product complexity: low / mid / high

Product risk: how many people it reaches, how close it is to learning and money, how sure we are, how hard it is to undo. It is not delivery effort: backend and frontend set Delivery complexity themselves.

Go from the top and stop at the first level where any line is true. When unsure between two levels, take the higher one. Type and level are independent: an Изменение on the payment page is high; a new staff report can be a Фича · low.

### high — any one is true

1. It changes what happens on the core student path: how a lesson is delivered or counted as done, how a test, a trial ҰБТ or homework is checked and scored, grades, progress and rating, payment, продление, access to the course, the student's main page. A text or layout fix on these screens doesn't count; an optional practice tool for one small stream doesn't either.
2. More than 30% of active students meet it and can't avoid it: every lesson, the main page, a mandatory step or a blocking screen. Or every person in a staff role uses it in daily work and the result reaches students (all methodists creating questions).
3. Users create content: students or parents write text, upload files, chat.
4. Money, personal or children's data, or legal and contract texts change: prices, discounts, payments, renewal statuses and how they are counted.
5. It cannot be undone by a deploy: it migrates or deletes data, or changes how scores, progress or payments are calculated for past records.
6. The problem is a hypothesis with no data behind it, and the type is Фича or Эпик.

### mid — not high, and any one is true

1. New screen, new section or new behaviour (type Фича or Эпик).
2. 10–30% of active students, or one regular process of a staff role.
3. Two or more roles, or both Web and the mobile app.
4. New statuses, scores or entities that other roles or features read, or a new notification (push, SMS, in-app) to students or parents.
5. It changes a rule users already know: a deadline, a limit, a status.

### low — none of the above

One role, one screen, existing behaviour: a text, a sort order, a filter, a column, a button, a default value, a staff report. Up to 10% of students or one staff team. A deploy or a toggle undoes it with no data to fix.

## 4. Examples from Juz40

Real tasks from Confluence SD (2026), classified by these rules. When a new task looks like one of them, start from its class.

| Task | Class | Why |
|---|---|---|
| Редизайн сайта v2: покупка, лендинг, SEO | Эпик · студенты · high | several releases; purchase (high 4) |
| Кабинет родителя v3: рейтинг, просадки, офферы | Эпик · студенты · high | third version; offers are money (high 4) |
| Курс для родителей (v1 → v2) | Эпик · студенты · mid | two releases; new section, not the core path |
| Сторис учеников | Фича · студенты · high | content from users (high 3) |
| ИИ Тьютор в чатботе | Фича · студенты · high | learning path; hypothesis without data (high 1, 6) |
| Оқушы статус қою (статус на следующий месяц) | Фича · студенты · high | продление (high 1, 4) |
| Magic Link: вход по ссылке | Фича · студенты · high | access to the course (high 1) |
| Тип вопроса «Сәйкестік» (MATCHING) | Фича · студенты · high | a new scored question type (high 1) |
| Создание вопросов через Claude (MCP) | Фича · сотрудники · high | all methodists; questions reach students (high 2) |
| Сату скидка | Фича · сотрудники · high | discounts are money (high 4) |
| TOEFL ITP тренажёр | Фича · студенты · mid | new screen; optional practice for one stream |
| NPS-опрос для родителей | Фича · студенты · mid | new screen and notification; can be skipped |
| САТУ АНАЛИТИКАСЫ (страница РОП) | Фича · сотрудники · mid | new screen; reads money, doesn't change it |
| Оқушы жауаптарын тексеру: Unicode | Изменение · студенты · high | how answers are checked (high 1) |
| Балл за ссылку на парную работу | Изменение · студенты · high | scores (high 1) |
| Пропуск интро в видеосабақ | Изменение · студенты · high | every lesson (high 1, 2) |
| «Шықты / Ушёл» в статусах продления | Изменение · сотрудники · high | how renewals are counted (high 4) |
| Parent Analytics: отчёт только в кабинете | Изменение · студенты · mid | changes a rule parents know (mid 5) |
| Ивент завуча на несколько групп | Изменение · сотрудники · mid | a regular process of one role (mid 2) |
| Импорт из Excel: жирный текст, картинки | Изменение · сотрудники · low | one role, one tool, existing behaviour |
| Таблицы в вопросах: размер при вставке | Изменение · сотрудники · low | one role, one editor |

Of 28 tasks checked, about half came out high, a third mid, and only staff tools came out low. Most of Juz40's work touches lessons, scores or money, so high is common: the core PM approves a lot. If that is too much for the core PM, require two high criteria instead of one.

## 5. What the class changes in discovery

Middle and low differ only in how deep discovery goes. After the owner's OK their path is the same.

| Step | low | mid | high |
|---|---|---|---|
| Brainstorm | Skip unless the PM wants it | When the direction is not decided | Always. At least assumption testing: the riskiest assumption and the cheapest way to check it |
| Must-ask questions (`must-ask.md`) | ● | ● and ◐ | ● ◐ ★ |
| Grilling | Required topics of the type | All topics of the type | All topics of the type, plus 9 (data), 14 (analytics) and 15 (release) |
| Readiness gate | ⚠ outside problem, solution and rules may become an open question without a second pass | ⚠ in rules and edge cases always gets a second pass | Every ⚠ gets a second pass. A cold read by a separate agent before the gate passes |
| Metric before PRD | Студенты: «сейчас → цель → где смотрим». Сотрудники: one line | Same as low | Студенты: baseline with real numbers, source and date. «Не измерено» is not accepted |
| PM-partner review (§6) | — | When a non-PM leads: the brief before the PRD, the PRD before the owner | Same as mid |
| Core PM approval (§6) | — | — | Twice: «берём в работу» after the brief, and the package before development. Each is a Sub-task. Not needed when the core PM leads the task |
| PRD blocks added on top of the type | — | — | Риски, Релиз, Что проверяем, Данные |
| Release in the PRD | Студенты: the owner decides on toggle and cohorts; write the decision | Same as low | Студенты: toggle OFF by default, cohorts by subject or stream, 3–7 days each. Сотрудники: everyone at once |
| ПБР | The owner decides | The owner decides | The owner decides; recommend holding it |
| Owner's OK | PRD, mockups, test cases | Same | Same, plus core PM |

## 6. Who reviews and approves

The core PM is the **Head of Discovery**. The Discovery department has PMs, designers and AI engineers; the Head of IT is above it.

| Who leads the task | PM-partner review (mid, high) | Core PM approval (high) |
|---|---|---|
| A PM of the Discovery department | — | Head of Discovery |
| Head of Discovery | — | Not needed |
| Not a PM: designer, AI engineer, developer | A PM of the Discovery department: reads the brief before the PRD and the PRD before it goes to the owner; their remarks are loop signals (`loops.md`) | Head of Discovery |

- The PM-partner is the PM the lead works with on this product. The PM-partner reviews; they don't approve. The owner's OK and the core PM's approval stay as in §5.
- The plugin keeps roles, not names. At intake, ask the lead once who the Head of Discovery and the PM-partner are, record the names in the brief, and look up their Jira account IDs with `lookupJiraAccountId`. Never hardcode names or IDs.
