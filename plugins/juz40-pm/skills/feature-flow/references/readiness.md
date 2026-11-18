# Readiness: what must be known before the PRD

Used twice: as the root of the grilling design tree, and as the gate before writing.

## Size

Decide the size early; it sets which topics are required.

| Size | When | Required topics |
|---|---|---|
| **Изменение** | Changes existing behaviour. A few days of work. No new screens, no new role. | 1, 2, 3, 4, 7, 8, 12 |
| **Фича** | New behaviour or a new screen. One release, one Story. | 1–13 |
| **Большая фича** | Several versions or stages, several roles or teams. One Story per version. | 1–15 |

New screens or a new role make an «Изменение» a «Фича». Several releases make a «Фича» a «Большая фича».

For an Изменение, topic 3 needs no dropped alternative, and topic 6 is needed only when the change alters a sequence of steps. Any other topic becomes required for any size as soon as the feature touches it (a new stored field → 9, a rollout toggle → 15).

## Topics

Each topic is **settled** only when every point under it is true.

1. **Проблема.** Who suffers. What happens today, as a fact (a process, a number, a screen), not an opinion. What it costs: hours, money, errors, lost students, or an explicit «не измерено». Source: who asked (заказчик, data, PM hypothesis).
2. **Цель.** What will be observably different after release, for whom. A metric with «сейчас → цель → где смотрим», or an explicit reason there is none.
3. **Решение.** The chosen approach in a few sentences. At least one alternative that was dropped, with the reason.
4. **Объём.** Every screen or section that changes, per role. What explicitly does **not** change. Platforms: Web, mobile app, admin.
5. **Роли и доступ.** Every affected role: what they see and what they can do. Who must not see or do what.
6. **Сценарий.** The happy path end to end, step by step, from the entry point to the result.
7. **Правила.** Every business rule is concrete: numbers, limits, dates, who and when. Every UI text that matters is given verbatim, in the UI language.
8. **Краевые случаи.** The ones that apply: empty state, error, no access, two people editing, old data, date boundaries, the user leaves halfway, repeated action.
9. **Данные.** What new data is stored. Where existing data comes from. What happens to old records.
10. **Дизайн.** A Figma link, or «нужен дизайн» with who does it, or «без дизайна» with why.
11. **Не входит.** What people might expect but is not in this release, with the reason.
12. **Ответственные.** PM, заказчик / согласующий, design, backend, frontend, mobile, QA: a name or «не назначен».
13. **Зависимости.** What must exist before work starts; related DV issues.
14. **Метрики и аналитика.** Events to log, if the goal has a metric.
15. **Версии и релиз.** What goes in each version or stage. Feature toggle, pilot group, order of deployment, what happens on rollback.

Platform specifics count as part of the topic they touch: if mobile is in scope, the scenario and rules must say how mobile behaves.

## Vague answers

These mark an answer ⚠ even when the PM sounds sure:

- Hedging: «наверное», «думаю», «скорее всего», «примерно», «вроде».
- Deferring: «потом решим», «по ситуации», «разработчики решат», «на усмотрение».
- Pointing without content: «как обычно», «как сейчас», «стандартно», «как в другом месте» — look up how it actually works, then confirm it with the PM.
- Open lists where the list must be complete: «и т.д.», «и другие», «всякое такое».
- Quality words without a measure: «удобно», «быстро», «понятно», «корректно», «красиво».
- A number that is needed but missing: a limit, a deadline, a threshold, a count.
- The answer repeats the question or answers a different one.

## Contradictions

Mark ⛔ when an answer conflicts with an earlier answer, with the previous version of the feature, with an existing Confluence spec, or with how the platform works. Say which two things conflict and ask which one wins.
