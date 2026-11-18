---
name: prd
description: Write a PRD for a Juz40 feature from one of the team's templates and publish it as a Confluence page. Use when the user says "write a PRD", "спека", "документ в Confluence", or wants a feature or a change to an existing feature written up. Not for creating Jira tickets (use jira-tasks).
---

# PRD

Fill one of the team's PRD templates and publish it to Confluence.

## 1. Pick the template

Every file in `templates/` is one PRD type. The first line of each file is a comment that says when to use it. Read those first lines and pick the one that fits the request. If two fit or none fits, ask the user which one.

## 2. Collect the content

Read the chosen template to see what it needs. Then:

- Look up facts yourself: the `docs/` vault (start at `docs/README.md`), existing Jira tickets, existing Confluence pages.
- Ask the user only for decisions and for things you cannot find.
- Never invent a business rule or a number. What is unknown goes into the template's open-questions section.

## 3. Fill the template

- Keep the template's headings and their order exactly. Do not add or drop sections; write «не применимо» in a section that has nothing.
- Remove the template's comment lines and placeholder hints from the result.
- Write in Russian. Keep code identifiers as they are in code (`stream`, `studentGroupMonthlyPayment`).

## 4. Show the draft and wait

Show the full draft in chat. Publish only after the user approves it.

## 5. Publish to Confluence

Settings are in `references/confluence.md`.

- Search first (`searchConfluenceUsingCql`). If a page for this feature exists, update it instead of creating a second one.
- New page: `createConfluencePage`. Existing page: `getConfluencePage`, then `updateConfluencePage`.

Finish with the page URL, and offer `jira-tasks` to create the tickets.
