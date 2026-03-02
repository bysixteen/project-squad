# Changelog

All notable changes to the Project Squad framework are documented here. This file allows projects using the framework to understand what has changed between versions and decide when to update.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/). Versions use [Semantic Versioning](https://semver.org/): `MAJOR.MINOR.PATCH`.

- **MAJOR** — breaking changes to command behaviour or output format.
- **MINOR** — new features, templates, or commands that are backwards-compatible.
- **PATCH** — fixes, clarifications, and documentation improvements.

---

## [1.1.0] — 2026-03-02

### Added

- `examples/spikes/spike-000-example/output.md` — Complete example of a finished spike output, demonstrating the Answer-First structure, evidence tables, persona perspectives, and raw research appendix. Previously only `brief.md` existed.
- `examples/spikes/spike-000-example/summary.json` — Machine-readable spike summary example, matching the format produced by `/create-spike`.
- `CHANGELOG.md` — This file. Enables projects to track which version of the framework they are running.
- `.squad/specialists.md` — Optional specialist roles file for teams that need domain-specific expertise beyond the core seven personas. Additive — does not modify the portable constant.
- `examples/sprint-retrospective-template.md` — Lightweight retrospective template for use at the end of a Full Design Sprint.
- `examples/sprint-backlog-template.md` — Lightweight backlog for managing sprint and spike candidates across a project.

### Changed

- `DEPLOY.md` — Added a `CLAUDE.md` Merge Guide section explaining how to combine Project Squad rules with a project's own technical context.
- `DEPLOY.md` — Added version tracking guidance.
- `.claude/commands/init-project-squad.md` — Pre-flight check now reads `_meta/PROJECT_CONTEXT.md` if it exists, using its content to pre-populate living documents automatically.
- `.claude/commands/init-project-squad.md` — Now generates `research/sprint-backlog.md` as part of the Project Context scaffold.
- `.claude/commands/create-sprint.md` — Pre-flight check now scans `research/dissent-register.md` for entries with a matching Review Trigger before starting a new sprint.
- `.claude/commands/create-sprint.md` — Pre-flight check now reads `research/sprint-backlog.md` and offers to pull the next candidate from it.
- `.claude/commands/create-spike.md` — Pre-flight check now reads `research/sprint-backlog.md` and offers to pull the next spike candidate from it.
- `research/dissent-register.md` template — Added `Review Trigger` column to enable active revisiting of overruled concerns.

---

## [1.0.0] — 2026-02-01

### Added

- Initial release of the Project Squad framework.
- `.squad/project-squad.md` — Seven persona definitions (the portable constant).
- `.claude/commands/init-project-squad.md` — Scaffolding command.
- `.claude/commands/create-sprint.md` — Full Design Sprint command with Knapp's Monday Questions.
- `.claude/commands/create-spike.md` — Technical spike command with Qualification Test and Question Formulation Framework.
- `CLAUDE.md` — AI context file with key rules.
- `DEPLOY.md` — Human-readable deployment guide.
- `README.md` — Project overview and quick start.
- `examples/sprints/sprint-000-foundation/` — Foundation sprint template.
- `examples/spikes/spike-000-example/brief.md` — Spike brief template.
- `examples/decisions/000-adr-template.md` — ADR template.
- `examples/project-context-template.md` — Project context template.
