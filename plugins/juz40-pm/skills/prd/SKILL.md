---
name: prd
description: Write a Juz40 PRD in Confluence, assembled from the team's blocks to fit the feature (passport, problem, solution, scope, user stories, rules, owners, dependencies and whatever else the feature needs), in tight text without filler, and publish it to the SD space. Use when the user says "write a PRD", "спека", "напиши доку", "документ в Confluence", or after the feature-flow brief is confirmed. Not for creating Jira tickets (use jira-tasks).
---

# PRD

Turn a confirmed brief into a PRD page in Confluence. Blocks and when to use them: `references/blocks.md`. How to write: `references/writing.md`. Confluence settings: `references/confluence.md`.

## 1. Get a confirmed brief

- Coming from `feature-flow`: the PM has confirmed the brief. Go on.
- Called directly with notes, a Jira key, a Confluence page or a chat: don't write from raw material. Load `feature-flow` and start it at its readiness check (stage 3) with that material. Come back here with the confirmed brief.
- Changing a published PRD because a decision changed: use `prd-update` instead.

## 2. Plan the document

1. Take the size from the brief (Изменение / Фича / Большая фича).
2. Take every block marked ● for that size in `references/blocks.md`, plus every ○ block whose trigger fires in the brief.
3. Show the PM the outline: numbered section titles in the final order, and for each ○ block a one-line reason. Example: «Сроки и периоды — блокировка страницы зависит от даты открытия продления».
4. Wait for an OK or changes. It takes one message; don't skip it.

## 3. Write

- Follow `references/blocks.md` for the content and form of each block, and `references/writing.md` for every sentence.
- Language: the brief's document language (Russian by default; Kazakh if the PM works in Kazakh). UI texts stay in the UI language.
- Use only what is in the brief and its sources. A gap you find while writing is an open question, never a guess.
- Title: `DV-XXXX — <Название>` when the Story exists, otherwise `<Название>`.

## 4. Check

Run the self-check at the end of `references/writing.md`, including the cold read. Fix what it finds before the PM sees anything.

## 5. Show and wait

Show the full draft in chat. Apply the PM's edits. Publish only after an explicit OK.

## 6. Publish

- Search first: `space = SD AND title ~ "<keyword>"`. If a page for this feature exists, don't create a second one: rewrite it with `getConfluencePage` and `updateConfluencePage`, both with `contentFormat: html` so inline comments and macros survive, and add a row to «История изменений».
- Where it goes: find the PM's recent pages (`space = SD AND creator = currentUser() AND type = page ORDER BY created DESC`) and propose the same parent folder or page. Ask once if unclear.
- `createConfluencePage` with `contentFormat: markdown`, status stays DRAFT in the passport.

Finish with the page URL. Then offer `jira-tasks`, unless `feature-flow` is driving, in which case hand back to it.
