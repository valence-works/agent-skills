# Worker Agent Handoff Template

Use this to dispatch one implementation-ready Task.

```markdown
# Worker mission: <Task title>

Implement: <GitHub issue link / identifier>

## Objective
<One coherent outcome.>

## Context
<Only the program context necessary to work correctly.>

## Governing decisions
- PRD: <relevant section/link>
- ADRs: <links>
- Decision log: <entries if relevant>
- Repository instructions: <AGENTS.md paths>

## Scope
- ...

## Explicit non-goals
- ...

## Acceptance criteria
- [ ] ...

## Required validation
- ...

## Working rules
- Stay within the assigned scope.
- Do not perform unrelated refactoring.
- Do not invent new foundational abstractions or change public contracts without surfacing the need first.
- If repository evidence invalidates an assumption, stop expanding scope and report the discovery.
- Capture necessary follow-up work instead of implementing neighboring Tasks unassigned.
- Return a concise report of changes, validation, discoveries, and follow-ups.
```

The program lead remains responsible for architecture and scheduling. The worker owns correct execution of the bounded assignment.
