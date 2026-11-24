# Confluence: settings and page template

| Setting | Value |
|---|---|
| Cloud ID | `93b1beb0-c257-47a6-9917-d6c2acd3e5aa` |
| Space key | `SD` (Juz40 LMS Platform) |
| Body format | `markdown` for new pages; `html` for every update of an existing page (keeps inline comments and macros) |
| Team templates | page «Шаблоны документации» (`724140033`): «Шаблон: Контекстный документ», «Шаблон: PRD для людей», «Шаблон: PRD для агентов — Фича», «Шаблон: PRD для агентов — Эпик», «Шаблон: Изменение», «Шаблон: Backend contracts» |

If a team template in Confluence and a template in `../templates/` disagree, the Confluence one wins: say so to the PM and offer to align the plugin.

## Page tree of one task

```
<раздел продукта или папка ведущего>
├── <Название> — контекст                          PM · до discovery, передаётся ведущему (не всегда)
└── <Название>                                     ведущий · PRD для людей (Изменение: единственная страница)
    ├── PRD для агентов: <Название>                ведущий · Фича, Эпик
    ├── Backend contracts: <Название>              бэк, по своему шаблону
    ├── Тест-кейсы: DV-XXXX — <Название> — Full + Edge Cases   QA
    └── «Как работает» (feature-changelog)         ведущий, через 30 дней после выкатки на 100%
```

- **PRD для людей** is the parent and the entry point: links in Jira, chats and Figma point to it. It holds why, what changes for whom, what we don't do, open questions and decisions. It reads in 3 minutes.
- **PRD для агентов** holds everything needed to build and test: User Stories with AC, rules, roles, data, analytics, release. It does not repeat the parent: it links to it and to its `ОВ-N`.
- **Изменение:** one page from `../templates/izmenenie.md`; contracts and test cases are its children.
- The pages link each other, the contracts and the test cases from the passport, even before those exist.
- The Story key goes in the passport, not in the title.

## Which template

| Type | PRD для людей | PRD для агентов |
|---|---|---|
| Изменение | — | `../templates/izmenenie.md` (one page for both) |
| Фича | `../templates/people.md` | `../templates/feature.md` |
| Эпик | `../templates/people.md` | `../templates/epic.md` |

The templates are skeletons in block order. What each block holds and when an optional block goes in: `blocks.md`.

**Эпик** is a document type, not a Jira issue type. In Jira an Эпик is one Story per version, linked to each other; never create a Jira Epic.

## Status in the passport

| Status | When | Who sets it |
|---|---|---|
| Черновик | Being written, or reworked after a loop | ведущий |
| На согласовании | The package went to the owner (and the core PM for high) | ведущий |
| Согласовано оунером <дата> | The owner's OK is recorded | ведущий, after the owner's word |
| В разработке | Development started | ведущий or coordinator |
| Выпущено | On prod for everyone | ведущий |

A loop that changes meaning after «Согласовано оунером» puts the page back to «На согласовании» (`../../feature-flow/references/loops.md`, rule 6). Both pages of a pair always have the same status.

## Approvals

Recorded in the passport, never only in chat: «Согласовано оунером: <имя>, <дата>». The core PM's approval also carries its Sub-task key. A changed approval keeps the old one in «История изменений».
