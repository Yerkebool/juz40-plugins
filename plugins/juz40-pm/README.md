# juz40-pm

Product workflow for the Juz40 team: from an idea to a PRD in Confluence and issues in Jira.

## How to use

Say what you want to build. `feature-flow` takes it from there:

```
brainstorm → grill → readiness check → PRD → Jira
```

You can start in the middle (a Jira key, a draft, notes) and skip stages that are already done. The readiness check is never skipped: nothing vague goes into the PRD as a fact.

When a decision changes later, use `prd-update`.

## Skills

| Skill | Where it comes from | What it does |
|---|---|---|
| `feature-flow` | Ours | Runs the whole flow, keeps the brief, checks readiness, sends vague answers to a second grilling pass |
| `product-brainstorming` | Exact copy from Anthropic's `product-management` plugin | Think through an idea with a sparring partner |
| `grilling` | Exact copy from `mattpocock/skills` | Question a plan until every decision is settled |
| `prd` | Ours | Assembles the PRD from blocks to fit the feature, checks the text, publishes to Confluence |
| `jira-tasks` | Ours | Stories and Sub-tasks in DV from templates (no epics), keys written back into the PRD |
| `prd-update` | Ours | Carries a changed decision through the PRD, Jira, backend contracts and test cases |

## Where the standard lives

| What | File |
|---|---|
| What must be known before writing, sizes, what counts as a vague answer | `skills/feature-flow/references/readiness.md` |
| The brief (handoff between stages) | `skills/feature-flow/references/brief.md` |
| PRD blocks: which are required for which size, triggers, form | `skills/prd/references/blocks.md` |
| How to write without filler, self-check | `skills/prd/references/writing.md` |
| Confluence space and page names | `skills/prd/references/confluence.md` |
| Jira project and rules | `skills/jira-tasks/references/jira.md` |
| Jira description templates | `skills/jira-tasks/templates/` |

To change the team standard, edit these files and bump the version in `.claude-plugin/plugin.json`.

## Not here

Test cases: QA has its own skill. The PRD gives it stable IDs (`US-01`, `R-01`) and names the test-case page `Тест-кейсы: DV-XXXX — <Название> — Full + Edge Cases`.

## Licenses of the copied skills

- `skills/grilling/` — MIT, copyright Matt Pocock. See `skills/grilling/LICENSE`.
- `skills/product-brainstorming/` — Apache-2.0, Anthropic. See `skills/product-brainstorming/LICENSE`.

Both files are unmodified copies.
