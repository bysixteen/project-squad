# Project Squad Framework
<!-- version: 1.2.0 -->

## What This Is

A portable toolkit for running structured design sprints, workshops, and technical spikes with Claude. Nine named personas provide diverse perspectives; five commands drive the workflow.

## Commands

| Command | Purpose |
|---------|---------|
| `/init-project-squad` | Bootstrap the framework — reads `_meta/PROJECT_CONTEXT.md` and scaffolds all living documents |
| `/create-sprint` | Run a Full or Lite Design Sprint for a specific user moment |
| `/create-workshop` | Run a compressed 2–3 hour sprint when a decision is needed quickly |
| `/create-spike` | Run a time-boxed investigation into a specific unknown |
| `/import-personas` | Import externally-created client personas into `research/PERSONAS.md` |

## Architecture

- **Portable Toolkit** (`.squad/`, `.claude/commands/`) — travels unchanged between projects
- **Project Context** (`research/`, `docs/decisions/`) — project-specific, populated by commands
- **Specialists** (`.squad/specialists.md`) — optional domain-specific roles, additive only

## Key Rules

1. **Do not modify** `.squad/project-squad.md` — it is the portable constant
2. **Read `.squad/project-squad.md` before running any command** — the nine persona names, roles, and signature questions are defined there and must be used verbatim. Never substitute generic roles (Designer, Engineer, Challenger, Scribe, etc.) for the named personas.
3. **First 20 Lines** — every output must have YAML frontmatter + TL;DR within 20 lines
4. **Elias Vance always dissents** — his challenge must be recorded even if overruled
5. **One question per spike** — multiple questions = multiple spikes
6. **`summary.json` is mandatory** — machine-readable output for every sprint, workshop, and spike
7. **Specialists are additive** — they supplement the core squad, never replace a persona
8. **Every dissent entry must have a review trigger** — a condition under which it is revisited
9. **Claude is the facilitator** — process quality, phase transitions, and scope discipline are Claude's responsibility, not a persona's. Use the Phase Transition Protocol defined in each command template.
10. **`/init-project-squad` creates exactly six living documents** — no additional process guides, methodology files, or role descriptions. The sprint process is defined in the command files, not in generated project files.

## Workshop Trigger Conditions

Use `/create-workshop` (not `/create-sprint`) when at least two of the following are true:

1. A decision is needed within 24–48 hours.
2. The team already has a leading option — the workshop stress-tests it, not discovers it.
3. A stakeholder, client, or deadline is forcing a decision before a full sprint is practical.
4. The question is well-defined but the team has not formally aligned on the answer.
5. A previous sprint's synthesis raised a follow-up question that needs a quick answer.

**Do not use `/create-workshop` to shortcut a genuinely complex problem.** If you cannot articulate the decision in one sentence, run a full sprint instead.

## Client Personas

The framework distinguishes between two types of personas:

| Type | Location | Purpose |
|---|---|---|
| **Project Squad Personas** (Leo, Lena, Marcus, etc.) | `.squad/project-squad.md` | Portable archetypes that *think about* the product. Travel unchanged between projects. |
| **Client Personas** | `research/PERSONAS.md` | Real users of *this* product. Project-specific. Created in Sprint 000 or imported via `/import-personas`. |

If you already have research-backed personas (from a previous project, a client workshop, or a UX research report), use `/import-personas` to bring them in rather than recreating them. Elias Vance will speak on behalf of the imported client personas during the Decide phase.

See `examples/client-personas-template.md` for the import format.

## The Validation Boundary

The Project Squad Framework ends at a decision and a synthesis document. It answers: **"Are we building the right thing?"**

What happens after — prototyping, usability testing, stakeholder review — is a delivery concern, not a research concern. The sprint's acceptance criteria (defined in `brief.md`) become the validation checklist for whatever is built next.

See `docs/VALIDATION-BOUNDARY.md` for the full pattern and recommended handoff structure.
