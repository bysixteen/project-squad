---
title: "Fieldside — Decision Log"
type: living-document
status: active
last-updated: 2026-02-10
---

**TL;DR:** Append-only log of every significant decision made on Fieldside. Includes the rejected alternative — that is the part that gets forgotten.

---

## D-001 · Tech Stack — Next.js + Supabase + Vercel

**Sprint:** 000 · Foundation
**Date:** 2026-01-15
**Decision:** Use Next.js 14 (App Router), PostgreSQL via Supabase, and Vercel for hosting.
**Rationale:** Team familiarity with Next.js. Supabase provides a managed PostgreSQL instance with a generous free tier, suitable for v1. Vercel's edge deployment integrates seamlessly. The stack is simple enough for one developer to maintain.
**Rejected alternative:** Remix + Fly.io — less team familiarity with Remix; Fly.io requires more infrastructure knowledge.
**Source:** `research/sprints/sprint-000-foundation/decision.md`

---

## D-002 · Auth — NextAuth.js v5 (Magic Link + Google OAuth)

**Sprint:** 000 · Foundation
**Date:** 2026-01-15
**Decision:** Use NextAuth.js v5 with magic link email authentication as primary, Google OAuth as optional.
**Rationale:** Magic links eliminate password management for club members who may not use the app regularly. No passwords to forget. Google OAuth provides a faster path for members who prefer it.
**Rejected alternative:** Clerk — paid beyond 10,000 monthly active users; unnecessary complexity for v1 scale.
**Source:** `research/sprints/sprint-000-foundation/decision.md`

---

## D-003 · Onboarding — Invite-Link Model

**Sprint:** 001 · Member Onboarding
**Date:** 2026-01-28
**Decision:** Members join via a secretary-generated invite link. The link creates a record in the `invites` table (token, expiry, used flag). On tap, the member completes a 3-step flow: name → email → playing position. The server creates a `member` record and marks the invite used.
**Rationale:** Prevents unknown people joining the club without secretary approval. GDPR risk of open registration (collecting data from non-members) is a real constraint. The secretary's control over membership reduces her anxiety about the onboarding process.
**Rejected alternative:** Open registration with a club code — proposed by Elias Vance. Would reduce per-member secretary burden but introduces GDPR risk and removes secretary control. Logged in dissent register with a review trigger.
**Source:** `research/sprints/sprint-001-onboarding/decision.md`

---

## D-004 · Data Model — User ≠ Member

**Sprint:** 001 · Member Onboarding
**Date:** 2026-01-28
**Decision:** A `user` is a NextAuth.js auth identity. A `member` is a club-specific role linked to both a `club` and a `user`. These are separate database entities. One user can be a member of multiple clubs.
**Rationale:** Without this separation, a player in two clubs would need two accounts. The separation is a hard-to-reverse architectural decision — establishing it before any club-specific features are built prevents expensive refactoring later.
**Rejected alternative:** Single `user` table with a `club_id` field — simpler initially but breaks multi-club support. Would require a migration once the second club signs up.
**Source:** `research/sprints/sprint-001-onboarding/decision.md` — Marcus Thorne's sketch.

---

## D-005 · Push Notifications — PWA Web Push with Email Fallback

**Spike:** 001 · Push Notifications
**Date:** 2026-02-10
**Decision:** Implement Web Push via a PWA (Progressive Web App). Cover ~85% of the user base (Android + desktop + iOS 16.4+ with home screen installation). Always maintain email as a fallback notification channel.
**Rationale:** Native apps are out of scope for v1. Web Push provides sufficient coverage for the majority of members. The iOS constraint (home screen installation required) is mitigated by prompting at the right moment in the onboarding flow (after the member sees the squad list — the emotional payoff).
**Rejected alternative:** Push notifications via a third-party service (e.g. OneSignal) — adds a paid dependency for something achievable natively. SMS — out of budget for v1 scale.
**Conditions:**
1. Add iOS home screen prompt after the squad list screen (not before — wait for the emotional payoff).
2. Email fallback is mandatory, not optional. Push is the enhancement; email is the baseline.
3. Build subscription expiry detection from the start.
**Source:** `research/spikes/spike-001-push-notifications/output.md`

---

## Decision Index

| ID | Topic | Sprint/Spike | Date |
|---|---|---|---|
| D-001 | Tech Stack | Sprint 000 | 2026-01-15 |
| D-002 | Auth | Sprint 000 | 2026-01-15 |
| D-003 | Onboarding Model | Sprint 001 | 2026-01-28 |
| D-004 | User ≠ Member Data Model | Sprint 001 | 2026-01-28 |
| D-005 | Push Notifications | Spike 001 | 2026-02-10 |
