# [Project Name]

## What this project is

[One paragraph describing the project purpose, tech stack, and primary language. Replace this with your actual project description.]

## Key conventions

| Resource | Location |
|----------|----------|
| Behavioural rules | `.claude/rules/` |
| Domain knowledge | `.claude/context/` |
| Output schemas | `.claude/schemas/` |
| Slash commands | `.claude/commands/` |
| Agents | `.claude/agents/` |
| Auto-triggered skills | `.claude/skills/` |
| Agent protocols | `.claude/protocols/` |
| Runtime state | `.claude/memory/state.json` |

## Read first for task types

- **Code tasks**: `.claude/rules/code-style.md`
- **Content tasks**: `.claude/rules/brand-voice.md` + `.claude/context/`
- **Reviews**: `.claude/commands/review.md`
- **Deployments**: `.claude/commands/deploy.md`

## Quick start

1. Read this file for project overview
2. Check `.claude/memory/state.json` for current workflow state
3. Follow rules in `.claude/rules/` for all outputs
4. Reference schemas in `.claude/schemas/` for structured outputs

---

*See `.claude/STRUCTURE.md` for full architecture documentation.*
