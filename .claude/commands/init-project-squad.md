# Command: /init-project-squad

## Purpose

Bootstrap the Project Squad framework in the current project. This command creates the full directory scaffold, copies the Portable Toolkit, and generates the Project Context templates. Run this once per project.

---

## Pre-Flight Checks

Before creating anything, perform these checks:

1. **Check for existing scaffold:** Does a `.squad/` or `research/` directory already exist?
   - If yes: Inform the user — "This project appears to already have a Project Squad framework. Running this command again will not overwrite existing files, but will add any missing ones. Proceed? (y/n)"
   - If no: Proceed immediately.

2. **Confirm project name:** Ask the user: "What is the name of this project? This will be used to pre-fill documentation headers."

---

## Execution Steps

### Step 1 — Create Directories

Create the following directories (skip if they already exist):

```
.squad/
.claude/commands/
research/
research/sprints/
research/spikes/
docs/
docs/decisions/
```

### Step 2 — Copy Portable Toolkit

Copy the following files from the toolkit source to the project (do not overwrite if they already exist):

- `.squad/project-squad.md` — The seven persona definitions. This file is the portable constant.
- `.claude/commands/create-sprint.md` — The sprint command.
- `.claude/commands/create-spike.md` — The spike command.

### Step 3 — Generate Project Context Scaffold

Create the following files using the templates below. If a file already exists, skip it.

**`research/PRINCIPLES.md`** — See template in this file.
**`research/PERSONAS.md`** — See template in this file.
**`research/DECISIONS.md`** — See template in this file.
**`research/sprint-status.md`** — See template in this file.
**`research/dissent-register.md`** — See template in this file.

### Step 4 — Confirm and Guide

Print the following success message:

```
✓ Project Squad framework initialized for: [PROJECT NAME]

Files created:
  .squad/project-squad.md
  .claude/commands/create-sprint.md
  .claude/commands/create-spike.md
  research/PRINCIPLES.md
  research/PERSONAS.md
  research/DECISIONS.md
  research/sprint-status.md
  research/dissent-register.md

Next steps:
  1. Customize research/PERSONAS.md with your project's user personas.
  2. Add any known design or technical principles to research/PRINCIPLES.md.
  3. Run /create-sprint to start your first sprint.
  4. Run /create-spike when you encounter a question that needs investigation.

The Project Squad personas in .squad/project-squad.md are portable archetypes — do not modify them.
```

---

## File Templates

### Template: `research/PRINCIPLES.md`

```markdown
# [PROJECT NAME] — Design & Technical Principles

**Last updated:** [DATE] — Sprint 000 (Foundation)
**Next review:** Sprint 002

This document captures the core principles that guide design and technical decisions on this project. It is a living document, updated at the end of each sprint.

---

## Design Principles

_Add project-specific design principles here. Examples:_
- _Accessibility is not optional — every feature must meet WCAG 2.1 AA._
- _Mobile-first: design for the smallest screen first._

## Technical Principles

_Add project-specific technical principles here. Examples:_
- _No new dependencies without a spike to evaluate the trade-offs._
- _All new components must be added to the design system._

## What "Good" Looks Like on This Project

_Describe the quality bar. What does a well-executed piece of work look like here?_
```

### Template: `research/PERSONAS.md`

```markdown
# [PROJECT NAME] — User Personas

**Last updated:** [DATE] — Sprint 000 (Foundation)
**Next review:** Sprint 002

> **Note:** These are the project's *user* personas — the real people who will use the product. They are distinct from the Project Squad personas (the seven archetypes in `.squad/project-squad.md`).

---

## Persona 1: [Name]

**Role:** [e.g., New Member, Club Admin, Casual Visitor]
**Goal:** [What are they trying to achieve?]
**Frustrations:** [What gets in their way?]
**Key Quote:** [A sentence that captures their perspective.]

---

## Persona 2: [Name]

_Add more personas as needed._
```

### Template: `research/DECISIONS.md`

```markdown
# [PROJECT NAME] — Decision Log

**Last updated:** [DATE] — Sprint 000 (Foundation)

This document is a high-level log of significant decisions made during sprints and spikes. For full rationale, follow the ADR links.

| # | Decision | Sprint / Spike | Date | ADR |
|---|----------|----------------|------|-----|
| — | _No decisions yet._ | — | — | — |
```

### Template: `research/sprint-status.md`

```markdown
# [PROJECT NAME] — Sprint Status

**Last updated:** [DATE]

| Sprint # | Topic | Date | Status | Personas | Folder |
|----------|-------|------|--------|----------|--------|
| 000 | Foundation | [DATE] | Complete | All | `research/sprints/sprint-000-foundation/` |
```

### Template: `research/dissent-register.md`

```markdown
# [PROJECT NAME] — Dissent Register

**Last updated:** [DATE] — Sprint 000 (Foundation)

This document records all significant dissenting opinions raised during sprints and spikes, primarily from Elias Vance (the Mandatory Challenger). Dissent is a feature. Recording it ensures that overruled concerns are not lost and can be revisited.

| Sprint / Spike | Topic | Dissenting Persona | Dissenting View | Outcome |
|---|---|---|---|---|
| — | _No dissent recorded yet._ | — | — | — |
```
