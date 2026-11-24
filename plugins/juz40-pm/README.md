# juz40-pm

Product discovery for the Juz40 team: from a request to an approved PRD in Confluence and issues in Jira, for a change, a feature or an epic. Everything except design itself.

## How to use

A PM who hands a task to someone else writes the context document first (`context-doc`). Whoever leads the task says what to build, or gives the context link, and `feature-flow` takes it from there:

```
intake and class → brainstorm → grill → readiness → metric → core PM (high) → PRD
→ design (prd-to-design, not here) → remarks loop → owner's OK → Jira sub-tasks
```

You can start in the middle (a Jira key, a draft, notes, remarks after ПБР or QA) and skip stages that are already done. The brief lives in Confluence («<Название> — бриф») and is saved at every checkpoint: in any chat, «продолжим DV-XXXX» picks the task up where it stopped. The class and the readiness gate are never skipped: nothing vague goes into the PRD as a fact.

When a decision changes later, use `prd-update`.

## Task class

Every task gets a class at intake: **type** (Баг / Изменение / Фича / Эпик), **audience** (студенты / сотрудники) and **Product complexity** (low / mid / high). The type decides which PRD template is used; the audience decides toggle, cohorts and metric; the level decides how deep discovery goes and who approves. Criteria: `skills/feature-flow/references/complexity.md`.

## Skills

| Skill | Where it comes from | What it does |
|---|---|---|
| `feature-flow` | Ours | Runs discovery: class, must-ask questions, loops back to brainstorm or grilling, readiness gate, metric, approvals |
| `product-brainstorming` | Exact copy from Anthropic's `product-management` plugin | Think through an idea with a sparring partner |
| `grilling` | Exact copy from `mattpocock/skills` | Question a plan until every decision is settled |
| `context-doc` | Ours | «<Название> — контекст»: the request and facts, handed by the PM to the owner |
| `feature-metrics` | Ours | Metric before the PRD, analytics events, verdict after release |
| `prd` | Ours | PRD from templates by type: one page for an Изменение; «PRD для людей» + «PRD для агентов» for a Фича or an Эпик |
| `jira-tasks` | Ours | Story at intake, core PM approval Sub-tasks, Story and discipline Sub-tasks after the owner's OK, Bugs |
| `prd-update` | Ours | Carries a changed decision through both PRD pages, Jira, backend contracts and test cases |

**Эпик** is a document type. Jira has no epics: an Эпик is one Story per version, linked to each other.

The Juz40 must-ask questions live in `feature-flow`, not in the copied skills: start with `feature-flow`, not with `/grilling` or `/product-brainstorming` directly.

## Where the standard lives

| What | File |
|---|---|
| Type, audience, Product complexity low / mid / high, what they change | `skills/feature-flow/references/complexity.md` |
| Must-ask questions: intake, brainstorm, before the PRD | `skills/feature-flow/references/must-ask.md` |
| The brief in Confluence: checkpoints, resume from any chat | `skills/feature-flow/references/state.md` |
| When to go back to brainstorm or grilling, limits, re-approval | `skills/feature-flow/references/loops.md` |
| What must be known before writing, vague answers | `skills/feature-flow/references/readiness.md` |
| The brief (handoff between stages) | `skills/feature-flow/references/brief.md` |
| Context document template | `skills/context-doc/templates/context.md` |
| PRD templates by type | `skills/prd/templates/` |
| Confluence page tree, statuses, approvals | `skills/prd/references/confluence.md` |
| PRD blocks: required by type and class, triggers, form | `skills/prd/references/blocks.md` |
| How to write without filler, self-check | `skills/prd/references/writing.md` |
| Jira project and rules | `skills/jira-tasks/references/jira.md` |
| Jira templates: Story, Sub-task, approval, Bug | `skills/jira-tasks/templates/` |

To change the team standard, edit these files and bump the version in `.claude-plugin/plugin.json`.

## Not here

- Design: `prd-to-design`, SU10, the designer's review.
- Test cases: QA has its own skills. The PRD gives them stable IDs (`US-01`, `R-01`) and names the test-case page `Тест-кейсы: DV-XXXX — <Название> — Full + Edge Cases`.
- Delivery complexity: set by backend and frontend.

## Licenses of the copied skills

- `skills/grilling/` — MIT, copyright Matt Pocock. See `skills/grilling/LICENSE`.
- `skills/product-brainstorming/` — Apache-2.0, Anthropic. See `skills/product-brainstorming/LICENSE`.

Both files are unmodified copies.
