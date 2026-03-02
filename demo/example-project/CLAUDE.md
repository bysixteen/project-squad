# Fieldside

## Project Context

Fieldside is a mobile-first web app for community sports clubs. It replaces WhatsApp groups, spreadsheets, and paper sign-up sheets with a single tool for managing memberships, fixtures, and communications.

**Stack:** Next.js 14 (App Router), TypeScript, Tailwind CSS, PlanetScale (Drizzle ORM), Sanity v3, NextAuth.js, Vercel.

## Development Workflow

**Always use `pnpm`, never `npm` or `yarn`.**

Run dev server: `pnpm dev`
Run tests: `pnpm test`
Build: `pnpm build`

---

## Project Squad Framework

**Version:** 1.1.0

### Commands

| Command | Purpose |
|---------|---------|
| `/init-project-squad` | Bootstrap the framework (run once per project) |
| `/create-sprint` | Run a structured design sprint |
| `/create-spike` | Run a time-boxed investigation spike |

### Architecture

- **Portable Toolkit** (`.squad/`, `.claude/commands/`) — travels unchanged between projects
- **Project Context** (`research/`, `docs/decisions/`) — project-specific, populated by commands
- **Specialists** (`.squad/specialists.md`) — optional domain-specific roles, additive only

### Key Rules

1. **Do not modify** `.squad/project-squad.md` — it is the portable constant
2. **First 20 Lines** — every output must have YAML frontmatter + TL;DR within 20 lines
3. **Elias Vance always dissents** — his challenge must be recorded even if overruled
4. **One question per spike** — multiple questions = multiple spikes
5. **summary.json is mandatory** — machine-readable output for every sprint and spike
6. **Specialists are additive** — `.squad/specialists.md` extends the team, never replaces core personas
7. **Dissent has a review trigger** — every entry in `dissent-register.md` must include a Review Trigger condition
