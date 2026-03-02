# Project Squad Framework

A portable toolkit for running structured design sprints and technical spikes with AI assistance. Built for use with Claude.

---

## What This Is

The Project Squad Framework is a set of Claude commands, persona definitions, and living document templates that enable any project to run structured, synthesis-friendly sprints and spikes. It is designed to be:

- **Portable** — set up in any project with a single command.
- **Context-efficient** — every output is structured so an LLM can extract key decisions from the first 20 lines without reading the full document.
- **Persona-driven** — seven named archetypes provide diverse perspectives and prevent groupthink.
- **Lift-and-shift ready** — the Portable Toolkit travels unchanged between projects; only the Project Context is project-specific.

---

## Quick Start

### Option A: Copy into an existing project

1. Copy `.squad/` and `.claude/commands/` into your project root.
2. Open Claude Code in your project directory.
3. Run `/init-project-squad`.
4. Customise `research/PERSONAS.md` with your project's user personas.
5. Run `/create-sprint` to start your first sprint.

### Option B: Manual setup

1. Copy `.squad/` and `.claude/commands/` into your project root.
2. Copy `examples/` contents to the appropriate locations:
   - `examples/sprints/` → `research/sprints/`
   - `examples/spikes/` → `research/spikes/`
   - `examples/decisions/` → `docs/decisions/`
3. Create the living documents manually (see templates in `init-project-squad.md`).

---

## The Three Commands

| Command | Purpose |
|---------|---------|
| `/init-project-squad` | Bootstrap the framework in a new project. Run once per project. |
| `/create-sprint` | Run a structured design sprint. Supports Guided Wizard, Paste, and Link input modes. |
| `/create-spike` | Run a time-boxed investigation to reduce excess uncertainty. Includes a Spike Qualification Test. |

---

## The File Structure

Once initialised, your project will have:

```
.squad/
└── project-squad.md              ← Portable Constant: 7 persona definitions

.claude/commands/
├── init-project-squad.md         ← Scaffolding command
├── create-sprint.md              ← Sprint command
└── create-spike.md               ← Spike command

research/                         ← Project Context (project-specific)
├── PRINCIPLES.md                 ← Design & technical principles
├── PERSONAS.md                   ← Project user personas
├── DECISIONS.md                  ← Decision log
├── sprint-status.md              ← Sprint history
├── dissent-register.md           ← Dissent log
├── sprints/
│   └── sprint-NNN-[topic]/
│       ├── brief.md
│       ├── sketches.md
│       ├── decision.md
│       ├── synthesis.md
│       └── summary.json          ← Machine-readable summary
└── spikes/
    └── spike-NNN-[topic]/
        ├── brief.md
        ├── output.md
        └── summary.json          ← Machine-readable summary

docs/decisions/
└── NNN-[topic].md                ← Architecture Decision Records (ADRs)
```

---

## The Two-Layer Architecture

### Layer 1: Portable Toolkit (project-agnostic)

The files in `.squad/` and `.claude/commands/` are the portable constant. They travel unchanged between projects. **Do not modify them per-project.**

### Layer 2: Project Context (project-specific)

The files in `research/` and `docs/decisions/` are project-specific. They start empty (or from templates) and are populated as sprints and spikes run. The `/create-sprint` and `/create-spike` commands read these files at the start of each session and update them at the end.

---

## The Project Squad Personas

Seven portable archetypes. They travel unchanged between projects.

| # | Name | Role | Signature Question |
|---|------|------|-------------------|
| 1 | Leo Finch | Visual Designer | "Does this feel like us?" |
| 2 | Dr. Lena Petrova | Design Engineer | "How will we build, test, and maintain this?" |
| 3 | Marcus Thorne | Senior Developer | "What are we NOT building here?" |
| 4 | Kira Sharma | Developer | "What does the implementation actually look like?" |
| 5 | Dr. Aris Thorne | Strategist | "What is the real problem we are trying to solve?" |
| 6 | Rowan Vale | Craftsman | "What is the feeling we want to create?" |
| 7 | Elias Vance | Client (External) | "Does this solve a real problem for my users?" |

**The Mandatory Dissent Rule:** Elias Vance must always be included in the Decide phase. His dissent — even if overruled — must be recorded in `research/dissent-register.md`.

---

## Sprint Input Modes

The `/create-sprint` command supports three input modes:

| Mode | When to Use |
|------|------------|
| **(A) Guided Wizard** | You want structured questions based on Jake Knapp's Monday Questions (Long-Term Goal, Sprint Questions, Map and Target) |
| **(B) Paste Content** | You have a brief, notes, Slack thread, or document to share — Claude extracts the key inputs |
| **(C) Link** | You have a URL to a document — Claude fetches and extracts the key inputs |

---

## Spike Qualification Test

Before every spike, the `/create-spike` command runs a three-question test:

1. **Can you confidently estimate the effort?** (If YES → regular task, not a spike)
2. **Is this uncertainty actively blocking a decision?** (If NO → not urgent enough)
3. **Is the primary goal knowledge, not a feature?** (If NO → it's a feature, not a spike)

This prevents the most common spike anti-pattern: using spikes for normal uncertainty.

---

## Output Synthesis Rules

All sprint and spike outputs follow these rules to prevent context burning:

1. YAML frontmatter is mandatory on every file.
2. TL;DR or Answer is always the first body section.
3. Tables over prose for structured data.
4. Appendices below a `---` horizontal rule.
5. Explicit null values — "Blockers: None" not an omitted section.
6. Past tense for decisions — signals finality.
7. ADR references inline for significant decisions.
8. Bidirectional links in frontmatter (`feeds-into`, `depends-on`).
9. One question per spike.
10. < 700 lines per file — split if longer.

### The "First 20 Lines" Rule

Every output file is designed so an LLM reading only the first 20 lines can determine relevance, extract the key decision, and know where to find detail. YAML frontmatter + TL;DR block must fit within 20 lines.

---

## Deploying to a New Project

### Quick deploy

```bash
# From your project root
cp -r /path/to/project-squad/.squad .
cp -r /path/to/project-squad/.claude/commands/create-sprint.md .claude/commands/
cp -r /path/to/project-squad/.claude/commands/create-spike.md .claude/commands/
cp -r /path/to/project-squad/.claude/commands/init-project-squad.md .claude/commands/
```

Then run `/init-project-squad` in Claude Code to generate the project context scaffold.

### What to customise

After deploying, the only files you need to customise are the living documents in `research/`:

1. **`research/PERSONAS.md`** — Add your project's user personas (not the Project Squad personas — those are portable).
2. **`research/PRINCIPLES.md`** — Add your project's design and technical principles.
3. **`research/DECISIONS.md`** — Add any existing technical decisions.

The first sprint should always be Sprint 000 (Foundation) to establish the baseline context.

---

## References

- [The Sprint Book — Jake Knapp](https://www.thesprintbook.com/the-design-sprint)
- [Spikes — Mountain Goat Software](https://www.mountaingoatsoftware.com/blog/spikes)
