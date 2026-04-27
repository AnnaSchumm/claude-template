# Agent Input/Output Specification

This document defines how agents communicate with each other.

## Core Principles

1. **Explicit contracts**: Every agent must define its input and output schemas
2. **No implicit state**: Agents share state only through handoffs
3. **Fail-safe**: If an agent fails, the handoff includes fallback instructions

## Handoff Flow

```
Agent A completes work
    ↓
Agent A creates handoff payload (follows handoff-format.json)
    ↓
Orchestrator validates payload against schema
    ↓
Orchestrator invokes Agent B with payload
    ↓
Agent B produces output (follows its output schema)
    ↓
Output saved to memory/ or returned to orchestrator
```

## Required Fields for Every Handoff

| Field | Purpose |
|-------|---------|
| `handoff_id` | Track and debug the handoff |
| `from.agent` | Who initiated |
| `from.task_completed` | What was done |
| `to.agent` | Who receives |
| `to.task_requested` | What to do next |
| `payload` | Data needed for the task |
| `timestamp` | When handoff occurred |

## Success Criteria

Every handoff should include `success_criteria` in the payload:
- Specific, measurable outcomes
- Used by receiving agent to know when done
- Used by orchestrator to validate completion

## Error Handling

If an agent cannot complete:
1. Return partial results if any
2. Include error description
3. Suggest alternative approach
4. Orchestrator checks `fallback` field for backup agent

## Example Handoff

```json
{
  "handoff_id": "abc-123",
  "from": {
    "agent": "research-agent",
    "task_completed": "Identified files related to authentication"
  },
  "to": {
    "agent": "security-auditor",
    "task_requested": "Audit these files for vulnerabilities"
  },
  "payload": {
    "files": ["src/auth/login.ts", "src/auth/session.ts"],
    "context": {
      "recent_changes": true,
      "focus_areas": ["input validation", "session handling"]
    },
    "success_criteria": [
      "All files scanned",
      "Vulnerabilities categorized by severity",
      "Remediation provided for each issue"
    ]
  },
  "priority": "high",
  "timestamp": "2024-01-15T10:30:00Z"
}
```
