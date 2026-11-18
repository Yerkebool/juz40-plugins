# juz40-plugins

Marketplace repo for the Juz40 team's Claude Code plugins.

## Install

```
/plugin marketplace add Yerkebool/juz40-plugins
/plugin install juz40-pm@juz40-plugins
```

The repo is private, so this works only for GitHub accounts that have access to it.

## Plugins

| Plugin | What it does |
|---|---|
| `juz40-pm` | Product workflow: brainstorm → grill → PRD in Confluence → Jira epics and stories |

## Layout

```
.claude-plugin/marketplace.json   <- the catalogue (one entry per plugin)
plugins/<name>/
  .claude-plugin/plugin.json      <- the plugin manifest
  skills/<skill>/SKILL.md         <- one skill = one folder + SKILL.md
  skills/<skill>/references/       <- loaded on demand, keeps SKILL.md short
```

A plugin can also ship `commands/`, `agents/`, `hooks/` and `.mcp.json`. This one is skills only.

## Changing a skill

Edit the `SKILL.md` and bump `version` in `plugins/<name>/.claude-plugin/plugin.json`.
Locally installed marketplaces pick changes up on restart; for the GitHub flow, push and
`/plugin update juz40-pm@juz40-plugins`.
