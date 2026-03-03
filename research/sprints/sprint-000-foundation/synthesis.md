---
title: "Sprint 000 · Foundation — Synthesis"
type: sprint-synthesis
status: complete
date: 2026-01-15
sprint: "000"
depends-on: []
feeds-into: ["sprint-001-onboarding"]
---

**TL;DR:** Foundation established. The secretary-first constraint and zero-budget rules are now in place. Sprint 001 is ready to begin — the onboarding flow is the highest-priority and highest-risk first user moment.

---

## What Changed

- `research/PERSONAS.md` — Created. Sarah, Jamie, Dave documented with goals, pain points, and key quotes.
- `research/PRINCIPLES.md` — Created. D1 (Mobile-First), D2 (Secretary-First), D4 (Reduce, Don't Replace) established.
- `research/DECISIONS.md` — Created. D-001 (tech stack) and D-002 (auth) logged with rejected alternatives.
- `research/sprint-backlog.md` — Created. Seven candidates seeded from PROJECT_CONTEXT.md open questions.
- `research/sprint-status.md` — Created. Sprint 000 logged as complete.

---

## What the Next Sprint Should Know

1. **Secretary-first is the governing constraint.** Every feature decision must start with: does this make Sarah's life easier? If it doesn't, it needs exceptional justification.

2. **Dave is not an edge case.** Older, less tech-savvy members must be considered from the start, not retrofitted later. The 60-second path to squad list is a hard benchmark.

3. **The tech stack is fixed for v1.** Next.js + Supabase + Vercel + NextAuth.js. No new dependencies without justification. Zero-budget constraint is real.

4. **Elias has no historic dissents to surface.** The dissent register is empty. Sprint 001's Decide phase will be the first opportunity for dissent.

5. **Sprint 001 is the highest-risk sprint.** The onboarding moment is make-or-break for adoption. If a new member hits friction here, they never return.

---

## Open Questions for Future Sprints

- How does the secretary generate and manage invite links? (Part of Sprint 001 or Sprint 002?)
- What happens when an invite link expires? (Needs a clear UX — "link expired, ask your secretary" — before Sprint 001 ships.)
- Does the secretary need to see which members have accepted their invite? (Sprint 002 scope.)

---

## Ideas for the Backlog

| Idea | Source | Priority | Target Sprint |
|---|---|---|---|
| Secretary dashboard for tracking invite link status | Dr. Aris Thorne | Should | Sprint 002 |
| Expired invite link UX | Rowan Vale | Must | Sprint 001 |
| Club branding on invite landing page (club name, colours) | Leo Finch | Should | Sprint 001 |
