# Requirements Interrogation Gate

Use this after repository/system discovery and before detailed backlog materialization.

The goal is to reach shared understanding of material product and architecture choices without asking the product owner questions the agent can answer itself.

## 1. Build an ambiguity ledger

Assess unresolved ambiguity across these dimensions:

- **Goals** — What outcome defines success? What is optimization actually for?
- **Users / actors** — Who uses, operates, administers, pays for, or supports the system?
- **Journeys** — What concrete end-to-end behaviors must exist?
- **Acceptance** — What observable evidence proves each important outcome?
- **Boundaries** — What is in scope, explicitly out of scope, or owned elsewhere?
- **Domain model** — Which concepts must remain distinct? Which names are overloaded?
- **Architecture** — Which decisions materially constrain later work?
- **Trust / security** — What crosses trust boundaries? What guarantees are promised?
- **Operations** — Who deploys, observes, restores, upgrades, supports, and responds to failure?
- **Compatibility** — Which versions, platforms, integrations, or migration paths matter?
- **Commercial policy** — Which entitlements, plans, quotas, or support promises affect implementation?
- **Alternatives** — Which credible designs have not yet been ruled in/out?
- **Assumptions** — What is currently being treated as true without evidence?
- **Sequencing** — Which decisions affect critical path or can safely be deferred?

Do not mechanically ask a question for every dimension. The ledger is an analysis tool.

## 2. Resolve discoverable questions first

Before asking the product owner:

- inspect source code;
- inspect tests;
- inspect repository docs and history;
- inspect existing ADRs/decision records;
- inspect infrastructure/configuration;
- consult authoritative external documentation when freshness matters;
- run a bounded experiment when cheap and decisive.

If the system already answers the question, use that evidence.

## 3. Ask one decision question at a time

Each question should contain:

1. **Decision** — one concrete choice, not a bundle of unrelated questions.
2. **Recommendation** — what the lead agent believes should be chosen.
3. **Why** — concise reasoning grounded in product goals and discovered reality.
4. **Trade-off** — the main cost, downside, or alternative being rejected.

Example shape:

> Should the first release support A only, or A and B? I recommend A only because it preserves the shortest end-to-end launch path and B does not affect the architecture if deferred. The trade-off is that users requiring B cannot join the first release.

Then wait for the answer before moving on.

## 4. Drill depth-first

Do not jump to a new topic merely because the product owner answered the first-level question.

Follow consequences until that branch is implementation-clear.

For example:

```text
Who is the first target user?
  -> What are they trying to accomplish?
      -> What is the minimum journey that proves this?
          -> What must be self-service versus operator-assisted?
              -> What failure/recovery behavior is promised?
```

Then move sideways to another unresolved branch.

## 5. Challenge fog

Do not accept answers such as:

- "maybe both";
- "whatever is easiest" when the choice changes product behavior;
- "we can decide later" when implementation depends on it;
- contradictory constraints;
- aspirational terms without an observable definition ("enterprise-ready", "secure", "scalable", "simple").

When useful, strawman a concrete interpretation and ask the product owner to accept or correct it.

## 6. Prefer reversible deferral

Not every decision must be made now.

A decision may be deferred when:

- it does not invalidate the next milestone;
- the architecture preserves a realistic path to it;
- implementation does not need to guess in the meantime.

Record:

- what is deferred;
- why deferral is safe;
- the revisit trigger or milestone.

## 7. Record continuously

As decisions resolve:

- update the PRD for product requirements;
- update the decision log for material product/program choices;
- create/update ADRs for consequential architecture;
- update explicit non-goals;
- update milestone success criteria.

Do not treat the conversation transcript as the specification.

## 8. Gate criteria

The gate passes when every ambiguity that could materially affect the next milestone is either:

- resolved and recorded; or
- explicitly deferred with a safe boundary and revisit condition.

Before passing, review at least these categories:

```text
Goal / user outcome        Clear?
Scope and non-goals        Clear?
Primary journeys           Clear?
Domain boundaries          Clear?
Architecture blockers      Resolved or spiked?
Security/trust guarantees  Clear?
Compatibility constraints  Clear?
Operations ownership       Clear?
Acceptance / validation    Clear?
Critical-path decisions    Clear?
```

If any material answer is "no", continue discovery/interrogation instead of generating implementation-ready Tasks.

## 9. Optional external grill-me skill

If an installed `grill-me` skill is available, it may be used as an interrogation engine.

Preserve these program-specific rules even when invoking it:

- research before asking;
- one question at a time;
- recommendation with every question;
- decisions recorded into canonical program artifacts;
- no implementation-ready backlog until the gate criteria pass.
