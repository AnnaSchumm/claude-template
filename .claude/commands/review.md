# /project:review

Review code changes before committing.

## Purpose
Perform a thorough code review of staged or specified changes.

## Required inputs
- File paths OR staged changes (default: staged)

## Preconditions
- Changes must exist to review

## Process
1. Read all changed files
2. Check against rules in `.claude/rules/code-style.md`
3. Identify issues: bugs, security, performance, style
4. Provide actionable feedback

## Output
Markdown report with:
- Summary of changes
- Issues found (categorized by severity)
- Suggested fixes
- Approval status (approve/request-changes)
