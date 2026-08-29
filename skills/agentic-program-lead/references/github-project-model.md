# GitHub Project Model

Prefer one cross-repository Project for a coherent program.

## Recommended fields

### Status

- Backlog
- Ready
- In Progress
- In Review
- Blocked
- Done

### Type

- Epic
- Feature
- Task
- Bug
- Spike
- ADR

### Phase / Milestone

Use the actual roadmap stages. Do not encode phases as extra issue hierarchy.

### Area / Workstream

Use a small stable taxonomy representing real ownership or architecture boundaries.

### Priority

- P0 — blocks the current critical path or addresses an urgent correctness/security issue
- P1 — important to the current/next milestone
- P2 — valuable but non-blocking
- P3 — later/opportunistic

### Agent State

Example values:

- Not Ready
- Agent Ready
- Assigned
- Review Required

Keep this distinct from normal workflow Status when it helps orchestration.

## Recommended views

### Roadmap

Group by Phase/Milestone and show Epics/Features. Useful for product-owner visibility.

### Execution

Board by Status for currently actionable work.

### Critical Path

Filter to work that currently blocks the next executable milestone.

### Agent Queue

Filter to leaf Tasks where:

- Status = Ready;
- Agent State = Agent Ready;
- dependencies are satisfied.

### Workstreams

Group by Area to detect overloaded or drifting subsystems.

### Blocked

Show all blocked work and require each item to identify the blocking issue, decision, or external condition.

## Maintenance rules

- The program lead updates the Project as part of normal orchestration, not in periodic cleanup batches.
- Do not use the Project as a second specification system. Canonical detail belongs in PRD, ADRs, decisions, and issues.
- Avoid decorative fields that are not used to make scheduling or architecture decisions.
