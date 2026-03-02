# Project Squad Framework

## What This Is

A portable toolkit for running structured design sprints and technical spikes with Claude. Seven named personas provide diverse perspectives; three commands drive the workflow.

## Commands

| Command | Purpose |
|---------|---------|
| `/init-project-squad` | Bootstrap the framework (run once per project) |
| `/create-sprint` | Run a structured design sprint |
| `/create-spike` | Run a time-boxed investigation spike |

## Architecture

- **Portable Toolkit** (`.squad/`, `.claude/commands/`) — travels unchanged between projects
- **Project Context** (`research/`, `docs/decisions/`) — project-specific, populated by commands

## Key Rules

1. **Do not modify** `.squad/project-squad.md` — it is the portable constant
2. **First 20 Lines** — every output must have YAML frontmatter + TL;DR within 20 lines
3. **Elias Vance always dissents** — his challenge must be recorded even if overruled
4. **One question per spike** — multiple questions = multiple spikes
5. **summary.json is mandatory** — machine-readable output for every sprint and spike
