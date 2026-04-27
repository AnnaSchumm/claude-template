# Skills Index

This file maps trigger conditions to skills. Skills auto-invoke when conditions are met.

## Trigger Map

| Condition | Skill | Description |
|-----------|-------|-------------|
| Files in `/auth`, `/security`, or `*auth*` modified | `security-review` | Run security audit on auth-related changes |
| PR targeting `main` or `master` branch | `security-review` | Security check before merge to main |
| `/project:deploy` command invoked | `deploy` | Execute deployment workflow |
| New dependency added to package.json | `dependency-check` | Audit new dependencies |

## Active Skills

- [security-review/](security-review/) — Security audit workflow
- [deploy/](deploy/) — Deployment workflow

## Adding New Skills

1. Create a folder: `.claude/skills/your-skill/`
2. Add `SKILL.md` inside with skill definition
3. Add trigger condition to this index
4. Test trigger conditions work as expected
