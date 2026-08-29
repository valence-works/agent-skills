# GitHub Issue Quality Standard

Use the smallest template appropriate to the work type. Do not add sections that provide no value.

## Program issue

```markdown
# <Program name>

## Vision
<End-state outcome.>

## Product / architecture summary
<Concise context and links to canonical PRD/ADRs.>

## Milestones
- [ ] <Milestone>
- [ ] <Milestone>

## Epics
- [ ] <Epic link>

## Critical path
<Current blockers and sequence.>

## Program status
<Concise current state, next milestone, major risks/decisions.>
```

## Epic

```markdown
## Objective
<Major coherent capability.>

## Context
<Why it matters and governing PRD/ADRs.>

## Outcomes / Features
- [ ] <Feature link>

## Constraints / non-goals
<Only material boundaries.>

## Dependencies
<Blocking Epics/ADRs/decisions.>

## Completion criteria
<Observable conditions for Epic completion.>
```

## Feature

```markdown
## Objective
<Independently demonstrable customer/operator/architecture capability.>

## Context
<Why this capability exists.>

## Scope
- ...

## Non-goals
- ...

## Architecture constraints
<Relevant ADRs, contracts, boundaries.>

## Dependencies
- ...

## Tasks
- [ ] <Task link>

## Acceptance criteria
- [ ] <Observable behavior>

## Validation
<How the Feature is demonstrated end-to-end or in integration.>
```

## Task

```markdown
## Objective
<One coherent implementation outcome.>

## Context
<Enough local context to execute without rediscovering the whole program.>

## Scope
- ...

## Non-goals
- ...

## Architecture constraints
- <ADR / contract / boundary>

## Dependencies
- <issue / prerequisite>

## Affected repositories
- `owner/repo`

## Acceptance criteria
- [ ] <Objective, observable criterion>
- [ ] ...

## Validation
- <test/build/deployment/integration behavior to verify>
```

A Task is not Agent Ready if any section exposes a material unresolved decision.
