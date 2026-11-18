# Confluence config for Juz40 PRDs

Fill the blanks the first time a user answers them, then this file stops asking.

| Setting | Value |
|---|---|
| Cloud ID | `93b1beb0-c257-47a6-9917-d6c2acd3e5aa` |
| Default space key | _(ask once, then record here)_ |
| Default parent page ID | _(ask once, then record here)_ |
| Body format | `markdown` |
| Page language | Russian |

## Discovering the space

If the default space is blank:

1. `getConfluenceSpaces` → show the user the candidates, ask which one PRDs belong in.
2. `getPagesInConfluenceSpace` on that space → find the parent page PRDs live under (often a "Продукт" / "Спецификации" tree).
3. Write both values into the table above so later runs skip the question.

## Title conventions

- `[PRD] <название фичи>` for new work.
- `[PRD][DV-XXXX] <название фичи>` once a Jira key exists.
- Keep the Jira key in the title — `jira-tasks` and `searchConfluenceUsingCql` both find pages by it.

## Before you publish

- Search first: `searchConfluenceUsingCql` with `text ~ "<feature>"` and `space = <key>`. Update beats duplicate.
- Updating needs the current version number from `getConfluencePage`; a stale version number silently fails or overwrites.
- Publishing is outward-facing. The user approves the draft in chat first, every time.
