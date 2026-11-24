# The brief

The brief is the handoff between stages. Brainstorm and grilling fill it, the readiness check grades it, `prd` writes the document from it, `jira-tasks` cuts issues from the PRD.

Keep it in the conversation, in this shape. Update it after every round; show it in full only at the readiness check and when the PM asks.

```markdown
# Бриф: <название>

Класс: <Изменение | Фича | Эпик> · <студенты | сотрудники: роль> · <low | mid | high>
Почему такой класс: <какой критерий из complexity.md сработал>
Класс подтвердили: PM <да / нет> · оунер <да / ждём>
Story: <DV-XXXX>
Ведёт: <имя, роль> · PM-партнёр: <имя, если ведёт не PM> · Оунер: <имя> · Кор PM: <имя, только high>
Источник: <ссылка / кто попросил>
Язык документа: RU | KZ

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
| Класс | оунер | | | |
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
```

## Rules

- Write what was said or found, not what you think it should be. A proposal of yours goes in only after the PM accepts it; then it is a decision with the PM as «кто решил».
- A fact you looked up carries its link in «Источники».
- Empty sections stay in the brief as «—» until the readiness check decides whether the class needs them.
