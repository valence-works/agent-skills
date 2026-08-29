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

### `sipke-voice`

Writes or rewrites prose in Sipke Schoorstra's voice — documentation, release notes, READMEs, commit subjects, and issue or pull request bodies. It changes how prose reads, never what it claims.

The rules were mined from a corpus rather than asserted: 50 commit subjects, `AGENTS.md`, `README.md`, ~36,000 words of `docs/wiki/`, and the release notes of `valence-works/groundwork-v2`. Each of the 14 rules carries quoted evidence in `references/voice-profile.md`, alongside measured baselines — median 13 words per sentence with 27% at eight or fewer, 42 uses of "rather than" against 5 of "instead of", and zero occurrences of the assistant-isms the skill's Never list bans. `references/before-after.md` rewrites six real passages, every "after" verbatim from the corpus.

`SKILL.md` records what the corpus does not cover — blog posts, talks, email, replies to users — rather than extrapolating to them.

## Installation

Copy the desired skill directory into the skill location supported by your agent, or install it from this repository using the mechanism supported by your Agent Skills-compatible client.

Codex reads skills from a repository at `<repo>/.agents/skills/NAME/` or `<repo>/.codex/skills/NAME/`, and for the current user at `~/.agents/skills/NAME/`:

```bash
mkdir -p ~/.agents/skills
cp -R skills/sipke-voice ~/.agents/skills/
```

`$CODEX_HOME/skills` also still loads, but Codex marks it a deprecated user location kept for backward compatibility, so prefer `~/.agents/skills`.

Claude Code reads the same directory unmodified, from `~/.claude/skills/NAME/` or
`<repo>/.claude/skills/NAME/`. Both tools take a `---`-delimited YAML frontmatter block
and match a task against its `description`, which only Codex requires to be non-empty.

They differ on where the name comes from. Codex uses a non-empty frontmatter `name` when
one is present, capped at 64 characters, and falls back to the containing directory only
when it is absent; Claude Code names personal and project skills from the directory. So a
`name` that disagrees with its directory is the one field that does not travel — it
renames the skill in Codex and is ignored for that purpose in Claude Code. Keep the two
equal, as the skills here do, and the same directory behaves identically in both.

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
