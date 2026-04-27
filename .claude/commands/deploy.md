# /project:deploy

Deploy the project to a target environment.

## Purpose
Execute deployment workflow with safety checks.

## Required inputs
- `environment`: dev | staging | prod

## Preconditions
- All tests passing
- No uncommitted changes
- For prod: requires explicit confirmation

## Process
1. Verify preconditions
2. Load environment config from `.claude/settings.env.json`
3. Run build process
4. Execute deployment
5. Verify deployment success
6. Update `.claude/memory/state.json` with deployment record

## Output
- Deployment status
- Environment URL
- Rollback instructions if needed

## Safety
- Prod deployments require `require_confirmation_before_deploy: true`
- Always create rollback point before deploying
