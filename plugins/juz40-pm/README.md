# juz40-pm

Four skills covering the path from "I have an idea" to "there are tickets in DV".

| Skill | Invoke | Use it when |
|---|---|---|
| `brainstorm` | `/brainstorm` | No agreed solution yet. Widen the option space, kill weak ideas early. |
| `grill` | `/grill` | A plan exists. Interrogate it round by round, then write the decisions into `docs/`. |
| `prd` | `/prd` | Decisions are settled. Write the PRD (Russian) and publish it to Confluence. |
| `jira-tasks` | `/jira-tasks` | A PRD exists. Dry-run a DV epic/story/sub-task tree, then create it. |

They chain, but each works alone, and each one *offers* the next step rather than
invoking it — you stay in control of when work becomes outward-facing.

## Guardrails worth knowing

- `prd` refuses to paper over unsettled decisions: three or more open fundamentals and it
  sends you to `grill` first.
- `prd` shows the draft before publishing to Confluence; `jira-tasks` shows the whole tree
  before creating a single issue.
- `jira-tasks` asks for assignee, estimate and sprint instead of guessing — DV rejects
  issues without them.
- Both Atlassian skills search for an existing page/ticket before creating a duplicate.

## Config

- Confluence space and parent page: `skills/prd/references/confluence.md` — blank on first
  run, fill it in once and later runs stop asking.
- Jira cloud ID, project key, field rules: `skills/jira-tasks/references/jira.md`. Where
  the frontend repo's `jira-workflow` skill disagrees, that skill wins.

## Attribution

The round-based interview method in `grill` is adapted from
[mattpocock/skills](https://github.com/mattpocock/skills) (`grilling`, `grill-with-docs`), MIT.
The PRD section structure in `prd` draws on Anthropic's `product-management` plugin
(`write-spec`), Apache-2.0.
