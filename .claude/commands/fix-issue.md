# /project:fix-issue

Fix a reported issue or bug.

## Purpose
Diagnose and fix a specific issue.

## Required inputs
- Issue description OR issue number/URL

## Preconditions
- Issue must be reproducible or well-documented

## Process
1. Understand the issue
2. Locate relevant code
3. Identify root cause
4. Implement fix following `.claude/rules/code-style.md`
5. Add/update tests
6. Verify fix resolves issue

## Output
- Summary of changes made
- Files modified
- Test results
- Ready for `/project:review`
