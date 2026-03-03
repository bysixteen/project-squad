---
title: "Sprint 000 · Foundation — Decision"
type: sprint-decision
status: complete
date: 2026-01-15
sprint: "000"
feeds-into: ["sprint-001-onboarding"]
---

**TL;DR:** Foundation established. Tech stack fixed. Initial principles and personas seeded. Secretary-first constraint adopted as the governing rule for all subsequent decisions. Elias had no dissent — the foundation reflected real user concerns accurately.

---

## Decision

We accepted the PROJECT_CONTEXT.md stack and constraints as the foundation for all subsequent sprints. The following were adopted as formal decisions:

1. **Tech stack:** Next.js 14 (App Router) + PostgreSQL via Supabase + Vercel. Rejected: Remix + Fly.io (see DECISIONS.md, D-001).
2. **Auth:** NextAuth.js v5 with magic link email + Google OAuth. Rejected: Clerk (paid beyond v1 scale, see DECISIONS.md, D-002).
3. **Design principle D2 (Secretary-First):** Every feature decision starts with: does this make Sarah's admin work easier?

## Rationale

The secretary is the single point of failure for adoption. If she doesn't use the app, no member ever will. This makes her the product's most critical user — not in volume, but in leverage. Every design decision must be filtered through her experience first.

The zero-budget constraint (Supabase free tier, Vercel hobby, Resend free tier) is real and non-negotiable for v1. Decisions that introduce paid dependencies need explicit justification.

## Rejected Alternatives

- **Remix:** Less team familiarity. No meaningful technical advantage over Next.js for this use case.
- **Firebase:** NoSQL is a poor fit for the relational data model (fixtures, payments, squad membership). Would require significant restructuring when the app grows.
- **Clerk:** Excellent DX but paid beyond 10,000 MAU. Unnecessary complexity for a single-club v1.

## Elias Vance — Foundation Review

Elias confirmed that the three personas (Sarah, Jamie, Dave) accurately reflected the range of users he would expect for a grassroots sports app. He had one note:

> "Make sure Dave is not treated as an edge case. Older, less tech-savvy members are the ones who most need the app to work without explanation — and they're the ones most likely to be left behind if we don't design for them deliberately."

Dave's adoption requirement ("zero training, 60-second path to squad list") was added to the design principles as a measurable constraint, not an aspiration.

**Elias's dissent:** None recorded for Sprint 000.

## Next Action

Run Sprint 001 — Member Onboarding. The most critical and highest-risk user moment is the first one: a member receiving an invite link and reaching the squad list. Sprint 001 targets this moment.
