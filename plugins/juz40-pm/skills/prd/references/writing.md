# Writing a PRD people actually read

The reader is a developer, designer or QA who was not in the conversation. They read the page to build and to check. Every sentence must tell them what happens, when, or what if. A sentence that tells them nothing is water: cut it.

## Sentences

- One sentence, one fact. Short sentences.
- Present tense, active voice, a named actor: «Куратор видит список», not «Будет реализована возможность просмотра списка куратором».
- Numbers, limits, dates, role names, exact screen names. «До 2000 символов», «3 дня после открытия продления», «Asia/Almaty».
- UI texts verbatim in «», in the UI language (usually Kazakh): «Келесі айға статусыңды белгіле».
- Code identifiers in backticks, exactly as in code: `studentGroupMonthlyPayment`.
- Say each fact once. Elsewhere, refer to it: «по R-03», «см. US-02».

## Form

- A table when things are compared, mapped or listed with the same attributes.
- A numbered list for steps and for rules.
- Prose only for «why»: the problem, the reasoning behind a decision.
- Bold for the label at the start of a line («**Кто:**»), not for emphasis inside sentences.
- No section without content. A required block with nothing in it says why: «Не применимо — правка без новых экранов».

## Banned

Delete or rewrite on sight:

- Bureaucratic filler: «в рамках данной задачи», «необходимо реализовать возможность», «осуществляется», «является», «данный», «в целях», «производится», «обеспечить возможность».
- Text about the document itself: «Этот документ фиксирует…», «Ниже представлен…», «В данном разделе описано…».
- Empty quality words: «удобно», «интуитивно», «корректно», «своевременно», «оптимально», «улучшить пользовательский опыт», «повысить вовлечённость» without a number.
- Open lists where the list must be complete: «и т.д.», «и др.», «и прочее».
- Vague placeholders: «TBD», «уточняется», «будет определено позже», «при необходимости». An unknown is an open question with an owner: «не определено (ОВ-4)».
- Hedges on facts: «вероятно», «как правило», «в основном».

## Unknowns and assumptions

- Unknown → open question `ОВ-N` with an owner. Refer to it where the gap is.
- Your assumption the PM has not confirmed → «⚠ предположение — подтвердить у <кого>», and an open question for it.
- Never write a guess as a fact. Never invent a number, a field name or a date.

## Stable IDs

`US-01`, `R-01`, `ОВ-1`, `T-01` never change once published, even when items are deleted (leave the number unused). QA's test cases and Jira issues refer to them.

## Self-check before showing the draft

1. Every block required for the size is there, in the order of `blocks.md`.
2. No banned phrase (search the draft for each).
3. Every acceptance criterion is checkable with yes/no and tagged.
4. Every rule `R-…` names the stories it serves; every story with logic has a rule or is self-contained.
5. Every «не определено» points to an `ОВ-…`; every `ОВ-…` has an owner.
6. Every UI text that matters is quoted verbatim.
7. **Cold read.** Read the draft as a developer who sees it for the first time. Write down every question you would ask before building. Answer each one in the document, or turn it into an open question.
