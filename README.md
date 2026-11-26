# stack

Small, sharp skills for AI coding agents.

A skill is a folder with one `SKILL.md`. The file is plain markdown, with a short header that names the skill and says when to use it. The same folder works with Claude, GPT or Codex, Cursor, and other agents. Nothing in the format is tied to one product.

## Skills

| Skill | What it does |
|---|---|
| [codebase-review](skills/codebase-review/SKILL.md) | Score a repository for how easy it is for a coding agent to work in, and propose changes. |

`codebase-review` scores the target against 13 practices. They cover names, layout, what search is allowed to see, file size, shared modules, git state, one schema, the instruction file, a done command, a fresh offline setup, checks for hard rules, and secrets. The default run is a read-only review. The report lists only problems, sorted by severity (Critical, High, Medium, Low). Each row says what is wrong and how to fix it. Critical and High rows also get a short evidence block. Fix mode is opt-in: you name the rows, the skill changes only those, one commit per row, and it runs the done command to check the fix. It does not push or open a pull request unless you ask.

## Install

With the Vercel skills CLI (Node 22.20+):

```
npx skills add 23grach/stack --skill codebase-review
```

Add `-g` for all projects, or `-a claude-code` (and the same flag for other agents) to pick the agent.

Or copy the skill folder into the skills directory your agent already reads. For example:

- `~/.claude/skills/codebase-review`
- `.cursor/skills/codebase-review`
- `.agents/skills/codebase-review`

Or leave the folder where it is and point the agent at [skills/codebase-review/SKILL.md](skills/codebase-review/SKILL.md).

Ask in plain language:

```
Review this repo with codebase-review
```

Pass a path, and a focus directory if you only want part of the tree. To apply fixes after the report, name the rows: `fix 4 and 9`.

## Layout

```
skills/codebase-review/SKILL.md
skills/codebase-review/references/report-template.md
```

`SKILL.md` is the procedure. `references/report-template.md` is the report shape, including a labeled example.

## License

[MIT](LICENSE). Copyright Pavel Grachev, 2026.
