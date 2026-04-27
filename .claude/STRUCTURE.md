# .claude/ Folder Architecture

This document explains what each folder is for and how to use it.

## The Core Principle

Separate concerns across three questions:

| Question | Folder(s) |
|----------|-----------|
| **How should Claude behave?** | `rules/` |
| **What should Claude know?** | `context/`, `schemas/` |
| **Where is the workflow right now?** | `memory/` |

Everything else (`commands/`, `agents/`, `skills/`, `protocols/`) layers on top.

---

## Folder Reference

### `rules/` — How Claude behaves
Modular behavioural instructions. Slow-changing. Committed to git.

**What belongs here:** Anything that tells Claude *how to act* regardless of task.
**What does NOT belong here:** Domain facts (use `context/`), output shapes (use `schemas/`), per-run state (use `memory/`).

### `context/` — What Claude knows
Persistent project knowledge. Domain grounding, not behavioural instruction.

**What belongs here:** Anything Claude needs to *know* — not how to behave, but what the world of this project looks like.

### `schemas/` — What Claude must produce
Output shape definitions. The contract between an agent and whatever consumes its output.

**Rule:** Any agent that produces structured output must reference a schema. Never let output shape be implicit.

### `commands/` — Human-triggered actions
Each `.md` file becomes a `/project:filename` slash command. Use for actions that only run when explicitly requested.

### `agents/` — Subagent personas
Isolated agents with their own role, instructions, and boundaries. Agents do not share state unless passed via `protocols/`.

Each agent must declare: Role, Scope, Input, Output (schema reference), Trigger.

### `skills/` — Auto-invoked workflows
Claude Code triggers these automatically when conditions are met. Each skill is a folder containing a `SKILL.md`.

`skills/index.md` must exist and map conditions to skills explicitly.

### `protocols/` — Agent-to-agent contracts
How agents hand off work to each other. Essential for multi-agent orchestration.

### `memory/` — Runtime state only (gitignored)
The only folder that changes between runs. Contains state for resuming workflows.

**Rules:**
- Keep files small and structured
- `state.json` must be readable in isolation
- Never put instructions or knowledge here

---

## File Checklist

```
[ ] CLAUDE.md is short and points to subfolders
[ ] rules/ contains only behavioural instructions
[ ] context/ contains only domain knowledge
[ ] memory/ is in .gitignore
[ ] settings.local.json is in .gitignore
[ ] Every agent references a schema
[ ] skills/index.md lists all triggers explicitly
[ ] state.json is readable standalone
[ ] No duplication across files
```
