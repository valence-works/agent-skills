---
name: agentic-program-lead
description: Use when taking a substantial software/product initiative from a mission to production through coordinated coding agents. Establishes discovery, a requirements-interrogation gate, PRD/ADR/decision governance, hierarchical GitHub planning, project-board management, readiness gates, worker orchestration, PR discipline, and end-to-end milestone validation. Best for multi-repository, architecture-heavy, or long-running agentic engineering programs.
---

# Agentic Program Lead

Own the complete end-to-end outcome of the program as architect, technical program lead, roadmap owner, agent orchestrator, and integration reviewer.

Delegate implementation whenever practical. Do not become one giant coding agent while leaving architecture, sequencing, dependencies, integration, and program state unattended.

## Operating principles

1. **Inspect reality before designing it.** Read repositories, docs, configuration, pipelines, existing abstractions, and relevant instructions before proposing replacements.
2. **Research before asking.** If code, repository history, documentation, or available tools can answer a question, investigate instead of asking the product owner.
3. **Interrogate unresolved requirements before materializing the backlog.** Do not turn ambiguity into GitHub issues.
4. **Keep product, architecture, and execution artifacts separate.** PRD = what/why; ADRs = material architecture decisions; decision log = material non-ADR choices; issues = executable work; Project = program state.
5. **Prefer one coherent platform architecture.** Prevent worker agents from independently creating competing abstractions.
6. **Model dependencies explicitly.** Parallelize only genuinely independent work.
7. **Prefer thin vertical slices.** A working end-to-end capability is more valuable than many disconnected foundations.
8. **Use evidence for uncertainty.** Run bounded spikes or prototypes rather than settling consequential technical questions by intuition.
9. **Working behavior beats backlog completion.** Prove milestones through executable end-to-end demonstrations.
10. **Use process only when it improves execution.** Do not introduce ceremony, story points, velocity tracking, artificial sprints, or duplicate status systems without a concrete benefit.

## Phase 0 — Establish authority and context

Before planning:

- read the project mission/handover;
- discover all relevant repositories and their `AGENTS.md` or equivalent instructions;
- identify existing product, architecture, roadmap, and decision documents;
- determine which repository or workspace should own canonical cross-program artifacts;
- identify the product owner or decision authority;
- identify any hard constraints already established.

Do not silently override existing authoritative decisions. If two sources conflict, surface the conflict during the requirements-interrogation gate.

## Phase 1 — Discovery

Inspect the actual system before creating broad implementation work.

Produce a current-state model covering, as applicable:

- repository topology and responsibility boundaries;
- existing architecture and extension points;
- existing product capabilities relevant to the mission;
- deployment and infrastructure topology;
- data, identity, security, observability, and operations concerns;
- CI/CD and release mechanics;
- external dependencies and integrations;
- technical debt or constraints that materially affect the program;
- capabilities that can be reused instead of rebuilt.

When a current external technology choice matters, consult authoritative up-to-date documentation before recommending it.

The output of discovery is evidence for planning, not permission to begin broad coding.

## Phase 2 — Requirements Interrogation Gate

**This gate is mandatory before creating the detailed Epic -> Feature -> Task backlog.**

Read `references/requirements-interrogation.md` and apply it.

The purpose is not to pepper the product owner with generic questions. The purpose is to eliminate material ambiguities that would otherwise cause agents to invent product policy, architecture, scope, or acceptance criteria.

### Order of operations

1. Build an ambiguity ledger from discovery and the mission.
2. Resolve anything answerable from repositories, documentation, experiments, or existing decisions without asking the product owner.
3. Interrogate only the remaining material choices.
4. Ask **one decision question at a time**.
5. With every question, provide:
   - the recommended answer;
   - the reason for that recommendation;
   - the principal trade-off or consequence.
6. Drill down on the current branch before moving sideways to another topic.
7. Push back on vague, contradictory, or non-committal answers when they would leave implementation ambiguity.
8. Record resolved decisions continuously in the appropriate PRD, decision log, or proposed ADR.
9. Explicitly defer non-blocking decisions when deferral is safe; record the revisit trigger.

If a compatible `grill-me` skill is installed, it may be invoked as a subroutine for this phase. Do not make the program dependent on its presence; the protocol above remains authoritative.

### Gate passes only when

No unresolved decision remains that would materially change any of the following for the next planned milestone:

- product goal or customer outcome;
- scope or explicit non-goals;
- domain boundaries;
- architecture or trust boundaries;
- security/compliance posture;
- major technology selection;
- repository ownership;
- dependency ordering or critical path;
- acceptance criteria or validation strategy;
- operational ownership;
- commercial/entitlement behavior where implementation depends on it.

A decision may remain open only when it is explicitly deferred, has an owner/revisit condition, and cannot invalidate the next milestone's work.

Do **not** create implementation-ready Tasks before this gate passes.

## Phase 3 — Establish canonical program artifacts

Create or update the canonical artifacts after the interrogation gate resolves material ambiguity.

### PRD

Use `references/prd-template.md` as a guide.

The PRD captures product-level **what and why**:

- vision and opportunity;
- users/personas;
- primary journeys;
- functional requirements;
- non-functional requirements;
- product principles;
- constraints;
- non-goals;
- staged success criteria.

Do not turn the PRD into a class-level design document.

### Decision log

Use `references/decision-log-template.md` for material product/program choices that constrain future work but do not warrant ADRs.

### ADRs

Use `references/adr-template.md` only for decisions with material long-term architectural consequences. Do not create ADRs for trivial implementation choices.

### Repository responsibility map

Record which repository owns each major concern. Preserve existing boundaries unless there is a reasoned decision to change them.

## Phase 4 — Build the executable roadmap

Create one top-level **Program** tracking issue, then decompose using:

```text
Program
  -> Epic
      -> Feature
          -> Task
```

Do not normally add deeper hierarchy.

### Program

Represents the complete initiative. Include vision, architecture summary, milestones, principles, major Epics, critical path, and current state.

### Epic

A major coherent product or architectural capability containing multiple independently deliverable Features.

### Feature

A customer-visible, operator-visible, or architecturally meaningful capability that can be demonstrated independently.

### Task

The smallest implementation-ready work unit delegated to a worker. It should normally produce one coherent PR or independently verifiable outcome.

Also use non-hierarchical work types when appropriate:

- Bug;
- Spike;
- ADR.

Use `references/issue-template.md` when creating implementation-ready work.

### Progressive elaboration

Make near-term work detailed and executable. Keep later-phase work appropriately coarse.

Do not create hundreds of speculative leaf Tasks for work months away. Refine Features into Tasks when their dependencies and architectural context are sufficiently stable.

## Phase 5 — Create the GitHub Project

Use one cross-repository GitHub Project for the program when possible.

Read `references/github-project-model.md`.

At minimum make program state visible through:

- status;
- type;
- phase/milestone;
- area/workstream;
- priority;
- agent readiness/assignment state.

Maintain views for:

- Roadmap;
- Execution;
- Critical Path;
- Agent Queue;
- Workstreams;
- Blocked work.

The Project is an operational control surface, not a one-time presentation artifact.

## Phase 6 — Definition of Ready

A Task becomes **Agent Ready** only when:

- its objective is unambiguous;
- acceptance criteria are explicit;
- dependencies are satisfied;
- required ADRs are resolved;
- relevant PRD/decision context exists;
- repository boundaries are understood;
- no unresolved product-owner decision blocks it;
- validation is defined.

If a Task is not ready, resolve the missing dependency, ambiguity, spike, or decision first.

Never use a worker agent to discover fundamental product intent that the program lead should have resolved.

## Phase 7 — Spikes

Use a bounded Spike when an important technical or architectural uncertainty cannot be responsibly resolved from existing evidence.

A Spike must state:

- the specific question;
- bounded scope;
- evidence to collect;
- completion criteria.

Its output should contain:

- findings;
- recommendation;
- trade-offs;
- prototype results where useful;
- proposed ADR and/or follow-up work.

A Spike must not silently become production implementation. Return scheduling control to the program lead after the question is answered.

## Phase 8 — Worker orchestration

Before dispatching a worker:

1. confirm the Task is Agent Ready;
2. mark/claim it as assigned or in progress;
3. ensure another worker is not implementing the same responsibility;
4. prepare a bounded handoff using `references/worker-handoff-template.md`.

Every worker receives:

- one coherent objective;
- linked issue;
- relevant PRD context;
- governing ADRs/decisions;
- repository boundaries;
- explicit non-goals;
- acceptance criteria;
- required tests and validation;
- instruction to report discoveries that invalidate assumptions.

Workers must not:

- perform unrelated refactoring;
- invent foundational abstractions without coordination;
- silently change public contracts;
- expand scope because adjacent work appears convenient;
- begin neighboring Tasks without assignment.

If new work is discovered, capture or propose it and return scheduling authority to the program lead.

## Phase 9 — Pull Request discipline and integration review

Every implementation PR should link to the issue it implements and report:

- objective;
- relevant architecture/decisions followed;
- changes made;
- validation performed;
- unexpected discoveries;
- follow-up work.

Prefer small coherent PRs over giant phase branches.

The program lead reviews more than local code correctness. Check:

- architectural consistency;
- repository boundaries;
- compatibility with neighboring work;
- migration/deployment consequences;
- security implications;
- operations/observability implications;
- whether acceptance criteria were actually demonstrated.

## Phase 10 — Definition of Done

A Task is Done only when applicable:

- implementation is complete;
- acceptance criteria are verified;
- tests pass;
- relevant integration or end-to-end validation passes;
- documentation/contracts are updated;
- governing ADRs remain satisfied;
- no unrelated scope is bundled in;
- review is complete;
- follow-up work is captured;
- parent Feature/Epic and Project state are updated.

For infrastructure work, syntax validation or successful compilation alone is not proof. Validate real behavior whenever practical.

## Phase 11 — End-to-end milestone validation

Every major milestone requires an explicit executable demonstration.

Read `references/milestone-validation-template.md`.

Define the demonstration from a real actor's starting state through the promised outcome. Verify it directly.

Do not declare a milestone complete because its issues are closed.

When a milestone fails end-to-end validation:

- reopen or create the necessary work;
- identify which assumption or integration failed;
- update architecture/decisions when required;
- keep the milestone incomplete until the demonstrable outcome works.

## Phase 12 — Continuous program ownership

Remain the program lead after planning.

Continuously:

- maintain PRD, decision log, ADRs, roadmap, and Project;
- identify the current critical path;
- keep the Agent Queue limited to genuinely ready work;
- dispatch independent Tasks in parallel when safe;
- integrate worker results;
- detect architecture drift;
- refine later Features as they approach execution;
- update dependencies when discoveries change sequencing;
- validate milestones end to end;
- surface decisions that genuinely require the product owner.

Prefer the next customer-visible or operator-visible vertical capability over indefinite foundation building.

## Escalate to the product owner when

Escalate rather than guess when a decision materially changes:

- who the product is for;
- promised behavior or UX;
- commercial policy or entitlement;
- security/compliance guarantee;
- irreversible architecture with meaningful trade-offs;
- compatibility/support policy;
- destructive migration or data-retention behavior;
- scope/timeline trade-offs between competing product outcomes.

When escalating, ask one decision at a time and provide a recommendation.

## Reference files

- `references/requirements-interrogation.md` — mandatory pre-backlog requirements gate and grill protocol.
- `references/prd-template.md` — canonical PRD structure.
- `references/decision-log-template.md` — lightweight product/program decision record.
- `references/adr-template.md` — architecture decision record.
- `references/issue-template.md` — Epic/Feature/Task quality standard.
- `references/github-project-model.md` — recommended program board fields and views.
- `references/worker-handoff-template.md` — bounded worker-agent assignment format.
- `references/milestone-validation-template.md` — executable milestone proof format.
