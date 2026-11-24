---
name: prd
description: Write a Juz40 PRD in Confluence from the team's templates by task type — one page for an Изменение; «PRD для людей» plus its child «PRD для агентов» for a Фича or an Эпик — with blocks added by the class (audience, Product complexity), in tight text without filler, and publish it to the SD space. Use when the user says "write a PRD", "спека", "напиши доку", "документ в Confluence", or after the feature-flow brief is confirmed. Not for creating Jira tickets (use jira-tasks).
---

# PRD

Turn a confirmed brief into PRD pages in Confluence.

| What | File |
|---|---|
| Page tree, which template, statuses, approvals | `references/confluence.md` |
| Templates by type | `templates/izmenenie.md`, `templates/people.md` (PRD для людей), `templates/feature.md` and `templates/epic.md` (PRD для агентов) |
| What each block holds, triggers, blocks added by the class | `references/blocks.md` |
| How to write, self-check | `references/writing.md` |

## 1. Get a confirmed brief

- Coming from `feature-flow`: the PM has confirmed the brief. Read it from the brief page «<Название> — бриф» in Confluence, not from memory of the chat.
- Called directly with notes, a Jira key, a Confluence page or a chat: don't write from raw material. Load `feature-flow` and start it at its readiness gate (stage 3) with that material. Come back here with the confirmed brief.
- Changing a published PRD because a decision changed: use `prd-update` instead.
- High and the core PM has not said «берём в работу» yet: you may draft, but don't publish (`feature-flow` stage 5).

## 2. Plan the document

1. Take the class from the brief: type, audience, level.
2. Pick the templates by type (`references/confluence.md`). An Изменение gets one page; a Фича and an Эпик get «PRD для людей» and «PRD для агентов».
3. For the agent page (or the single page): every ● block of the template, every block the class adds (`blocks.md`, top), and every ○ block whose trigger fires in the brief. Blocks that live on the people page are not repeated there (`blocks.md`, «Where blocks live»).
4. Show the PM the outline: the pages, and for each the numbered section titles in the final order; for each ○ block, a one-line reason. Example: «Сроки и периоды — блокировка страницы зависит от даты открытия продления».
5. Wait for an OK or changes. It takes one message; don't skip it.

## 3. Write

- PRD для людей first: it fixes why, what, what we don't do, decisions and open questions. Then PRD для агентов, which builds on it and refers to its `ОВ-N`. The two pages never say different things about the same fact.
- Block «Аналитика»: load `feature-metrics`, part B, for the events.
- Follow `blocks.md` for the content and form of each block, and `writing.md` for every sentence.
- Language: the brief's document language (Russian by default; Kazakh if the PM works in Kazakh). UI texts stay in the UI language.
- Use only what is in the brief and its sources. A gap you find while writing is an open question, never a guess.
- Titles: `<Название>` for PRD для людей (or the single page), `PRD для агентов: <Название>` for the agent page. The Story key goes in the passport.

## 4. Check

Run the self-check at the end of `writing.md`, including the cold read and the page-for-people check. Fix what it finds before the PM sees anything.

## 5. Show and wait

Show the drafts in chat: PRD для людей first, then PRD для агентов. Apply the PM's edits. Publish only after an explicit OK.

## 6. Publish

- Search first: `space = SD AND title ~ "<keyword>"`. If a page for this task exists, don't create a second one: rewrite it with `getConfluencePage` and `updateConfluencePage`, both with `contentFormat: html` so inline comments and macros survive, and add a row to «История изменений».
- Where it goes: find the PM's recent pages (`space = SD AND creator = currentUser() AND type = page ORDER BY created DESC`) and propose the same parent folder or page. Ask once if unclear.
- `createConfluencePage` with `contentFormat: markdown`: PRD для людей (or the single page) first, then PRD для агентов as its child. Then update each passport so the two pages link each other.
- If a «<Название> — контекст» page exists, put the PRD next to it and link it from the passport.
- Move the brief page under PRD для людей (`updateConfluencePage` with `parentId`), link the PRD from the brief, and save the brief: «Где мы: 6. PRD опубликован», next step design or the owner's OK.
- Status: «Черновик». It becomes «На согласовании» when the package goes to the owner (`feature-flow` stage 8).

Finish with the page URLs. Then hand back to `feature-flow` if it is driving; otherwise say the next step: `prd-to-design` if there is UI, otherwise the owner's OK.
