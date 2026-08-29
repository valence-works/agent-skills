# Agent Skills

Reusable agent workflows maintained by Valence Works.

## Skills

### `agentic-program-lead`

Turns a substantial software/product mission into a governed, dependency-aware, agent-executable program and then coordinates implementation through worker agents.

The skill is designed for architecture-heavy, multi-repository or long-running initiatives where one lead agent should own the end-to-end outcome rather than acting as a single giant coding agent.

Core behaviors include:

- repository and architecture discovery before planning;
- a mandatory requirements-interrogation gate before backlog creation;
- canonical PRD, ADR and decision-log governance;
- `Program -> Epic -> Feature -> Task` GitHub decomposition;
- a cross-repository GitHub Project with critical-path and agent-ready views;
- Definition of Ready and Definition of Done;
- bounded spikes for uncertainty;
- worker-agent claiming, handoff and PR discipline;
- end-to-end milestone validation;
- continuous roadmap and architecture governance.

## Installation

Copy the desired skill directory into the skill location supported by your agent, or install it from this repository using the mechanism supported by your Agent Skills-compatible client.

For Codex, a project-local installation can use:

```text
<repo>/.codex/skills/agentic-program-lead/
```

The skill is intentionally portable and keeps project-specific product context out of the reusable methodology. Provide that context separately in the project mission prompt and repository instructions.

## Recommended context hierarchy

```text
Agentic Program Lead skill
        |
        | reusable methodology
        v
Project mission prompt
        |
        | product-specific vision and constraints
        v
Repository AGENTS.md files
        |
        | local engineering conventions
        v
GitHub Tasks
        |
        | bounded implementation work
        v
Worker agents
```
