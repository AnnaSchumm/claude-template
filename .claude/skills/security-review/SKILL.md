---
name: security-review
description: >
  Automatically triggered security audit for authentication and security-related
  code changes. Invokes the security-auditor agent and produces a security report.
---

# Security Review Skill

## Trigger Conditions
- Any file in `/auth`, `/security`, or matching `*auth*` is modified
- PR targets `main` or `master` branch
- Manual invocation

## Workflow

1. **Identify scope**
   - List all modified files
   - Filter to security-relevant files

2. **Invoke security-auditor agent**
   - Pass file list to `.claude/agents/security-auditor.md`
   - Request full security scan

3. **Generate report**
   - Output follows `.claude/schemas/security-report.json`
   - Save to `.claude/memory/last-security-report.json`

4. **Determine action**
   - If critical/high vulnerabilities: block and alert
   - If medium/low: warn but allow proceed
   - If none: approve

## Output
- Security report (schema: `security-report.json`)
- Pass/fail status
- Remediation guidance if issues found
