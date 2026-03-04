# Changelog

All notable changes to the Project Squad framework are documented here. This file allows projects using the framework to understand what has changed between versions and decide when to update.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/). Versions use [Semantic Versioning](https://semver.org/): `MAJOR.MINOR.PATCH`.

- **MAJOR** — breaking changes to command behaviour or output format.
- **MINOR** — new features, templates, or commands that are backwards-compatible.
- **PATCH** — fixes, clarifications, and documentation improvements.

---

## [0.9.0] — 2026-03-04

### Added

- Phase Transition Protocol in `/create-sprint` and `/create-workshop` — silent quality gates between phases that catch scope drift, incomplete outputs, or reframed questions before they cascade.
- **Riley Tanaka — Quality Assurance Specialist** in `.squad/specialists.md`. Signature question: "How will we know this actually worked?" Ensures acceptance criteria are measurable before crossing the validation boundary.
- Acceptance Criteria Quality Check in creative brief phase — applies Riley Tanaka's testability lens even when Riley is not a sprint participant.
- Validation Recommendation section in spike output for medium/low confidence results — defines what evidence would raise confidence and the cheapest test to run.
- `feeds-from` frontmatter in sprint output templates (`sketches.md`, `decision.md`, `synthesis.md`) — makes the phase-to-phase data chain self-documenting.
- Elias Vance now explicitly references client personas from `research/PERSONAS.md` by name during Sketch and Decide phases.

### Changed

- `CLAUDE.md` — Added Key Rule 9: Claude is the facilitator. Added Key Rule 10: init creates exactly six living documents.
- Workshop persona selection table updated to reference Key Rule 4 (Elias mandatory dissent).
- Version numbers reset to 0.x.y (semver pre-release) — the framework is still in active development and not yet committed to backwards compatibility.

---

## [0.8.0] — 2026-03-04

### Added

- **Nara Shin — UX Researcher** (persona #8). The Evidence Hunter. Signature question: "What does the evidence say?" Leads evidence gathering in Map phase, validates solutions against external research.
- **Ines Alvarez — UX Designer** (persona #9). The Interaction Architect. Signature question: "Where will users get stuck?" Leads interaction design in Sketch phase, evaluates usability and task completion.
- Functional Spike type added to Team Selection Guide (Ines, Lena, Kira).
- Research Checkpoint (Question 7) added to `/create-sprint` Map phase — Dr. Aris Thorne asks for evidence before committing to a pattern.

### Changed

- `.squad/project-squad.md` — Expanded from 7 to 9 core personas.
- Team Selection Guide updated: Nara included in research-heavy sprints and Research Spikes. Ines included in UX/experience, Brand, and Design Spikes.
- All framework files updated to reference nine personas (previously seven).

### Breaking

- **Persona count changed from 7 to 9.** Projects using the framework should update their `CLAUDE.md` and any hardcoded persona references. Full Sprint teams should now include all 9 personas.

---

## [0.7.0] — 2026-03-02

### Added

- `examples/spikes/spike-000-example/output.md` — Complete example of a finished spike output, demonstrating the Answer-First structure, evidence tables, persona perspectives, and raw research appendix. Previously only `brief.md` existed.
- `examples/spikes/spike-000-example/summary.json` — Machine-readable spike summary example, matching the format produced by `/create-spike`.
- `CHANGELOG.md` — This file. Enables projects to track which version of the framework they are running.
- `.squad/specialists.md` — Optional specialist roles file for teams that need domain-specific expertise beyond the core personas. Additive — does not modify the portable constant.
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

## [0.1.0] — 2026-02-01

### Added

- Initial release of the Project Squad framework.
- `.squad/project-squad.md` — Nine persona definitions (the portable constant).
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
