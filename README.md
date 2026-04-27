# Claude Code Template

A structured `.claude/` folder architecture for consistent, auditable, handoff-ready Claude Code projects.

## Quick Start

1. Clone this repo into your project (or copy the files)
2. Edit `CLAUDE.md` with your project details
3. Customize files in `.claude/` for your needs
4. Start using Claude Code

## Structure

```
your-project/
├── CLAUDE.md                  ← Entry point (edit this first)
├── CLAUDE.local.md            ← Personal overrides (gitignored)
└── .claude/
    ├── STRUCTURE.md           ← Architecture documentation
    ├── settings.json          ← Shared permissions
    ├── settings.local.json    ← Personal permissions (gitignored)
    ├── settings.env.json      ← Environment config
    ├── commands/              ← Slash commands (/project:*)
    ├── agents/                ← Subagent definitions
    ├── rules/                 ← Behavioural instructions
    ├── context/               ← Domain knowledge
    ├── schemas/               ← Output formats
    ├── skills/                ← Auto-triggered workflows
    ├── protocols/             ← Agent-to-agent contracts
    └── memory/                ← Runtime state (gitignored)
```

## Folder Purpose

| Folder | Question it answers | Changes |
|--------|---------------------|---------|
| `rules/` | How should Claude behave? | Rarely |
| `context/` | What should Claude know? | Occasionally |
| `schemas/` | What must Claude produce? | Occasionally |
| `commands/` | What can a human trigger? | Rarely |
| `agents/` | Who does what autonomously? | Occasionally |
| `skills/` | What triggers automatically? | Rarely |
| `protocols/` | How do agents talk to each other? | Rarely |
| `memory/` | Where is the workflow right now? | Every run |

## Included Examples

### Commands
- `/project:review` — Code review
- `/project:deploy` — Deployment workflow
- `/project:fix-issue` — Bug fix workflow

### Agents
- `code-reviewer.md` — Reviews code quality
- `research-agent.md` — Investigates and synthesizes
- `security-auditor.md` — Security vulnerability scanning

### Rules
- `code-style.md` — Coding conventions
- `brand-voice.md` — Writing guidelines
- `api-conventions.md` — API design patterns

### Skills
- `security-review/` — Auto-triggered security audit
- `deploy/` — Deployment workflow

## Usage

Copy this template to a new project:

```bash
cp -r claude-template/.claude your-project/.claude
cp claude-template/CLAUDE.md your-project/
cp claude-template/CLAUDE.local.md your-project/
```

Or clone and customize:

```bash
git clone https://github.com/YOUR_USERNAME/claude-template.git
cd claude-template
# Edit files as needed
```

## Customization

1. **CLAUDE.md**: Update project description and key conventions
2. **rules/**: Add project-specific coding standards
3. **context/**: Add domain knowledge for your project
4. **schemas/**: Define output formats your agents produce
5. **commands/**: Add project-specific slash commands

## License

MIT — Use freely in your projects.

---

*Based on the .claude/ folder architecture pattern.*
