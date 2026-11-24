# The brief

The brief is the handoff between stages and the memory of discovery. Brainstorm and grilling fill it, the readiness gate grades it, `prd` writes the PRD from it.

It lives in Confluence as the page «<Название> — бриф», not in the chat. Anyone can open it and see where the task is: the lead, the PM-partner, the owner, a new chat, another agent. Where it lives, when to save it and how to resume from it: `state.md`.

In the chat, show only what changed. At the readiness gate, give the link and the key decisions in at most ten lines; the full text is on the page.

## Template

Copy of Confluence «Шаблон: Бриф» (page `869957671`, in «Шаблоны документации»). If they differ, Confluence wins.

```markdown
**Где мы** · обновлено <дата, время, Asia/Almaty> · <кто>
**Этап:** <номер и название этапа feature-flow, например «2. Прожарка, раунд 3»>
**Сделано:** <одна строка>
**Дальше:** <следующий шаг одной строкой>
**Ждём:** <кого и что, с какой даты — или «никого»>

| Поле | Значение |
|---|---|
| Класс | <Изменение / Фича / Эпик> · <студенты / сотрудники: роль> · <low / mid / high> — <какой критерий сработал> |
| Класс подтвердили | ведущий <да / нет> · оунер <да / ждём> |
| Ведёт | <имя, роль> |
| PM-партнёр | <имя — если ведёт не PM> |
| Оунер | <имя> |
| Кор PM | <имя — только high> |
| Story | <DV-XXXX> |
| Контекст | <ссылка на «… — контекст» или «нет»> |
| PRD | <ссылки, когда есть> |
| Дизайн | <Figma, когда есть> |
| Язык документа | RU / KZ |

## Открытый раунд
<Вопросы последнего раунда, на которые ещё нет ответа: дословно, с рекомендацией. Ответов нет — «нет».>

## Проблема
- Кто: …
- Что сейчас: …
- Цена: …
- Источник: …

## Цель
- …
- Метрика: сейчас → цель → где смотрим

## Решение
- …
- Отказались: … — потому что …
- Главное допущение и как проверяем (high): …

## Роли и объём
| Роль | Экран / раздел | Что меняется | Что не меняется |
|---|---|---|---|

Платформы: …

## Сценарий
1. …

## Правила
- …

## Краевые случаи
- …

## Данные
- …

## Дизайн
- …

## Не входит
- … — потому что …

## Ответственные
| Роль в команде | Кто |
|---|---|

## Зависимости
- …

## Аналитика, версии, релиз
- …

## Решения
| Вопрос | Решение | Кто решил | Когда |
|---|---|---|---|

## Открытые вопросы
| # | Вопрос | Кто отвечает | К какому сроку |
|---|---|---|---|

## Апрувы
| Что | Кто | Решение | Когда | Где записано |
|---|---|---|---|---|
| Класс | оунер | | | бриф |
| Бриф (mid, high, ведёт не PM) | PM-партнёр | | | бриф |
| Берём в работу (high) | кор PM | | | Sub-task DV-… |
| Пакет: PRD, макеты, тест-кейсы | оунер (+ кор PM для high) | | | паспорт PRD |

## Петли
| Когда | Сигнал | Куда вернулись | Что поменялось |
|---|---|---|---|

## Идеи на потом
- …

## Источники
- <ссылки на Jira и Confluence, которые использовались>

## Журнал
| Когда | Кто | Этап | Что сделали |
|---|---|---|---|
```

## Rules

- Write what was said or found, not what you think it should be. A proposal of yours goes in only after the person accepts it; then it is a decision with them as «кто решил». Quote their words for decisions.
- A fact you looked up carries its link in «Источники».
- Empty sections stay as «—» until the readiness gate decides whether the class needs them.
- Students and parents are named by account ID and role only: never a name with a phone number or an email.
- «Журнал» gets one row per checkpoint, not per message: what was done, in one line.
- After the PRD is published, the PRD is the source of truth. The brief keeps «Где мы», «Петли», «Апрувы» and «Журнал» up to date; decisions change only through `prd-update`.
