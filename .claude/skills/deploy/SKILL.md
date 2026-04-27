---
name: deploy
description: >
  Deployment workflow skill. Handles pre-deploy checks, environment configuration,
  deployment execution, and post-deploy verification.
---

# Deploy Skill

## Trigger Conditions
- `/project:deploy` command invoked
- Manual deployment request

## Required Input
- `environment`: dev | staging | prod

## Workflow

1. **Pre-flight checks**
   - Verify no uncommitted changes
   - Verify all tests passing
   - Check environment config exists in `.claude/settings.env.json`

2. **Environment setup**
   - Load config for target environment
   - Validate required environment variables
   - For prod: require explicit confirmation

3. **Build**
   - Run project build command
   - Verify build succeeds

4. **Deploy**
   - Execute deployment for target environment
   - Create rollback point

5. **Verify**
   - Health check deployed service
   - Smoke test critical endpoints

6. **Record**
   - Update `.claude/memory/state.json` with deployment record
   - Log to `.claude/memory/run-log.md`

## Output
- Deployment status (success/failure)
- Environment URL
- Rollback instructions
- Deployment timestamp

## Rollback
If deployment fails:
1. Automatically attempt rollback
2. Report failure reason
3. Preserve logs for debugging
