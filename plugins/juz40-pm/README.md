# juz40-pm

Four skills.

| Skill | Where it comes from | What it does |
|---|---|---|
| `product-brainstorming` | Exact copy from Anthropic's `product-management` plugin | Think through an idea with a sparring partner |
| `grilling` | Exact copy from `mattpocock/skills` | Question a plan until every decision is settled |
| `prd` | Ours | Fill a PRD template and publish it to Confluence |
| `jira-tasks` | Ours | Create an Epic and Stories in DV from templates |

## Templates

Each template is one markdown file. Its first line is a comment that tells Claude when to use it.

```
skills/prd/templates/
  new-feature.md     <- the feature does not exist yet
  rework.md          <- an existing feature is being changed or rebuilt

skills/jira-tasks/templates/
  epic.md
  story.md
```

The four files in there now are drafts. Replace their contents with the team's real
templates and keep the first comment line.

To add another PRD type, add a file to `skills/prd/templates/` with its own first line,
for example `<!-- Use when: a small improvement to an existing screen. -->`. Nothing else
needs to change.

## Settings

- Confluence space and parent page: `skills/prd/references/confluence.md`
- Jira project and rules: `skills/jira-tasks/references/jira.md`

## Licenses of the copied skills

- `skills/grilling/` — MIT, copyright Matt Pocock. See `skills/grilling/LICENSE`.
- `skills/product-brainstorming/` — Apache-2.0, Anthropic. See `skills/product-brainstorming/LICENSE`.

Both files are unmodified copies.
