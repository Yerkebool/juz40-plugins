---
name: feature-flow
description: Take a Juz40 feature from idea to Jira in one guided flow — brainstorm the logic, grill it until nothing is vague, check readiness, write the PRD in Confluence, create the Jira issues. Use when a PM starts any new feature or change ("новая фича", "есть идея", "пришла задача от бизнеса", "надо сделать доку и задачи", "давай с нуля") or brings a Jira key or a request and wants the whole thing done.
---

# Feature flow

One flow for every feature: **brainstorm → grill → readiness check → PRD → Jira**. Each stage hands the next one a single artifact, the **brief** (`references/brief.md`). The stages are a means, not a ritual: skip whatever the brief already settles, but never skip the readiness check.

Talk to the PM in the language they write in (Russian or Kazakh).

## 0. Start

1. Ask one line: what is the feature and where did it come from (Jira key, Confluence link, a message from the business, the PM's own idea).
2. Look things up before asking anything else:
   - Jira DV: the given key, and `project = DV AND text ~ "<keyword>" ORDER BY created DESC` for related work.
   - Confluence SD: the base feature, a previous version, related specs (`searchConfluenceUsingCql`, `space = SD AND text ~ "<keyword>"`).
   Show what you found in at most five lines, with links.
3. Pick the entry point and say it in one line:
   - Nothing decided yet → **1. Brainstorm**.
   - The direction is decided ("бизнес сказал, делаем X") → **2. Grill**.
   - Detailed notes or a draft doc exist → build the brief from them, go to **3. Readiness check**.
   The PM can jump to any stage at any time.
4. Start the brief.

## 1. Brainstorm

Load the `product-brainstorming` skill and follow it, with this framing:

- Let the PM describe the logic freely first. Don't interrupt with structure; take notes into the brief.
- Think in Juz40 terms: roles (Студент, Родитель, Куратор, Завуч / координатор, Методист, Менеджер / админ, Профориентолог), platforms (Web, мобильное приложение), UI language (Kazakh first), the ҰБТ calendar, monthly payments and продление.
- Converge on: the problem, the chosen direction, the alternatives dropped and why. Ideas that are good but not for now go to the brief's «Идеи на потом», so nothing is lost.

Done when the PM names the direction. Show the brief's problem / direction part in five lines and move on.

## 2. Grill

Load the `grilling` skill and follow it. Use `references/readiness.md` as the root of the design tree, in its order: problem and goal → roles and scope → scenario → rules → edge cases → data → owners, dependencies, release.

- Facts are yours to find, not the PM's: how the platform works now, what the previous version did, who owns what. Use Jira and Confluence. Recommended answers lean on how the platform already works ("как в курсе ученика", "как в v1").
- Every round, put the answers into the brief. Quote the PM's own words for decisions.
- Ask only about the branches the chosen size needs (see sizes in `references/readiness.md`). A small change does not get grilled on analytics and release.

## 3. Readiness check (gate)

Check the brief against `references/readiness.md`. Show the result as a table:

| Тема | Статус | Что не так |
|---|---|---|

✅ settled · ⚠ vague · ❌ missing · ⛔ contradicts an earlier answer or an existing doc.

- **All ✅** → show the full brief, ask the PM to confirm it, go to 4.
- **Anything else** → **second grilling pass** on the gaps only. Each question quotes the vague answer, says why it's not enough to build from, and offers concrete options with your recommendation.
- After the second pass, check again. A third pass only if the PM wants one. Whatever is still open becomes an open question with an owner and a date. The PM can say «пиши с открытыми вопросами» at any point.

Never let a vague answer pass into the PRD as a fact.

## 4. PRD

Load the `prd` skill and give it the confirmed brief. It plans the document from blocks, writes it, checks it, shows it, and publishes it after the PM's OK.

## 5. Jira

Load the `jira-tasks` skill and give it the published PRD. It plans the Stories and Sub-tasks, asks for estimates and sprint, creates the issues after the PM's OK, and writes the keys back into the PRD.

## 6. Finish

Give the PM, in a few lines:

- the PRD link and the issue keys;
- what other teams take from here: backend writes `Backend contracts: <Название>` as a child page, QA writes `Тест-кейсы: DV-XXXX — <Название> — Full + Edge Cases` from the PRD;
- the open questions that still block development, with owners.

## Long features

The brief lives in the conversation. If the work may not finish in one session, offer to save it as `brief-<slug>.md` in the current folder; a new session continues from that file at the readiness check.
