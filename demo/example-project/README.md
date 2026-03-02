# Fieldside — Example Project

> **This is a demonstration project.** It exists to show the Project Squad framework in action with realistic content. Fieldside is fictional. Read this branch to understand how the framework works before deploying it to a real project.

---

## What This Is

Fieldside is a fictional mobile-first web app for community sports clubs. It was chosen as the demo project because it has:

- A clear primary user with a real frustration (the club secretary)
- A genuine technical uncertainty (push notifications without a native app)
- A design decision worth debating (invite-link vs. open registration)
- A realistic tech stack (Next.js, PlanetScale, Sanity, NextAuth.js)

None of this is real. The code does not exist. The personas are invented. The decisions are illustrative.

---

## How to Read This Branch

The framework flow runs in this order:

### 1. Setup — What `/init-project-squad` produces

| File | What it is |
|------|-----------|
| `_meta/PROJECT_CONTEXT.md` | The input file you create before running init. Pre-populates the living documents. |
| `CLAUDE.md` | The merged CLAUDE.md — project context at the top, Project Squad rules at the bottom. |
| `research/PRINCIPLES.md` | Core design and technical principles, pre-populated from PROJECT_CONTEXT.md. |
| `research/PERSONAS.md` | User personas (not squad personas), pre-populated from PROJECT_CONTEXT.md. |
| `research/DECISIONS.md` | Decision log — starts empty, grows with each sprint. |
| `research/sprint-status.md` | Running log of all sprints and spikes. |
| `research/sprint-backlog.md` | Backlog of sprint and spike candidates. |
| `research/dissent-register.md` | Every overruled dissent, with a Review Trigger. |

### 2. Sprint 000 — Foundation

`research/sprints/sprint-000-foundation/`

The foundation sprint establishes shared context before any feature work begins. It produces:
- `brief.md` — the sprint question and constraints
- `summary.json` — machine-readable output

### 3. Sprint 001 — Member Onboarding

`research/sprints/sprint-001-member-onboarding/`

A real feature sprint. It produces:
- `brief.md` — the sprint question and constraints
- `sketches.md` — each persona's perspective in their own voice
- `decision.md` — what was decided and why, including Elias's dissent
- `synthesis.md` — the full synthesis with risks and next actions
- `summary.json` — machine-readable output

### 4. Spike 001 — Push Notifications

`research/spikes/spike-001-push-notifications/`

A technical investigation spike. It produces:
- `brief.md` — the single question and the spike qualification test
- `output.md` — the answer, evidence, and recommendation (Answer-First structure)
- `summary.json` — machine-readable output

### 5. ADR — Onboarding Model Decision

`docs/decisions/003-onboarding-model.md`

A full Architecture Decision Record for the invite-link vs. open registration decision, including Elias's dissent and the review trigger.

---

## What the Framework Looks Like in Practice

**The pre-flight check in action:** Before Sprint 001, the `/create-sprint` command reads `research/sprint-backlog.md` and finds "Member onboarding flow" as the top candidate. It also reads `research/dissent-register.md` — but at this point the register is empty, so nothing is surfaced.

**The PROJECT_CONTEXT.md shortcut:** Because `_meta/PROJECT_CONTEXT.md` was created before running `/init-project-squad`, the living documents were pre-populated with real content rather than placeholder text. The init command read the personas, principles, and constraints from the context file and used them directly.

**Elias's mandatory dissent:** In Sprint 001, Elias challenged the invite-link model. The team overruled him — but his dissent is recorded in `research/dissent-register.md` with a specific review trigger (adoption below 60%). If Sprint 003 or later hits that trigger, the `/create-sprint` pre-flight will surface it automatically.

**The spike qualification test:** Spike 001 passed all three qualification questions (can't estimate effort, actively blocking a decision, goal is knowledge not a feature). This is what a qualified spike looks like. If any of those answers had been different, the framework would have redirected to a regular task.

---

## Key Things to Notice

1. **Every output starts with YAML frontmatter and a TL;DR within 20 lines.** This is the First 20 Lines rule. It means any document can be scanned in seconds.

2. **Elias always dissents — even when he agrees.** In Sprint 000, he agreed with the approach. In Sprint 001, he challenged the invite-link model. In the spike, he raised a risk that became a condition on the recommendation. His role is to find the flaw, not to block progress.

3. **summary.json is the connective tissue.** Every sprint and spike produces a `summary.json`. These files are what the `/create-sprint` pre-flight reads to understand the project's history without loading every document into context.

4. **The dissent register has teeth.** The review trigger on Elias's Sprint 001 dissent is not decorative. The `/create-sprint` command will surface it when Sprint 003 (fixture management) runs, because that sprint will generate data on member adoption.

5. **The backlog drives the next sprint.** The `sprint-backlog.md` is updated after every sprint and spike. When you run `/create-sprint` next, it reads the backlog and offers the top candidate — you don't have to remember what comes next.
