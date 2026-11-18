---
name: jira-tasks
description: Create Jira issues in the DV project — an Epic and/or Stories — from a PRD, a Confluence page or a described feature, using the team's issue templates. Use when the user says "create tickets", "создай эпик", "создай стори", "нарежь задачи", or has just finished a PRD.
---

# Jira tasks

Create an Epic and/or Stories in the **DV** project from the team's templates.

Project settings and rules are in `references/jira.md`. Read it before the first Jira call.

## 1. Read the source

A Confluence PRD link → `getConfluencePage`. A Jira key → `getJiraIssue`. Plain text → use it as given.

Search DV for tickets that already cover this (`searchJiraIssuesUsingJql`) and show the user what you found before proposing new ones.

## 2. Plan the issues

- One **Epic** for the whole feature when it is too big for one Story. One or more **Stories** under it, each a piece a user can see working.
- A small feature is just one Story with no Epic.
- Every file in `templates/` is the description template for one issue type. Its first line is a comment that says which type it is for. Fill the matching template for each issue; keep its headings and order, and remove the comment lines.
- Summaries in Russian, about behaviour the user sees, not about code.

## 3. Show the plan and wait

Show every planned issue: type, summary, filled description. Ask for what Jira needs and you must not guess:

- **Original estimate** for each Story (`2h`, `1d`, `1d 4h`).
- **Sprint**: the active sprint or the backlog.

Create nothing until the user approves the plan.

## 4. Create

- Epic first, then its Stories, with `createJiraIssue`.
- Assignee is the current user (`atlassianUserInfo`) unless the user names someone else.
- Put the PRD link in each description.
- If a call fails, stop and report what was already created. Do not retry blindly.

Finish with the list of created keys and links.
