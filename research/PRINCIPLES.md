---
title: "Fieldside — Design & Technical Principles"
type: living-document
status: active
last-updated: 2026-01-28
updated-by: sprint-000-foundation
---

**TL;DR:** Seven principles that constrain every design and engineering decision on Fieldside. These are not aspirations — they are rules. When a proposal violates one, the principle wins.

---

## Design Principles

### D1 — Mobile-First
Every screen is designed for a 390px viewport first. No desktop-only tables or multi-column layouts. If it looks good on a phone, it can be adapted for desktop. The reverse is not true.

*Added: Sprint 000. Rationale: 100% of club members access the app from a phone.*

### D2 — Secretary-First
If a feature creates more work for the secretary than it saves, it does not ship. The secretary is the gatekeeper — if she doesn't adopt the app, no member will ever see it.

*Added: Sprint 000. Rationale: See Sarah persona in PERSONAS.md. The secretary has the highest admin burden and the most to gain.*

### D3 — Zero-Training Onboarding
A member receiving an invite link should reach the squad list in under 60 seconds without reading any instructions. No tooltips, no tutorial screens, no "here's how to use the app" modals.

*Added: Sprint 001. Rationale: Dave (45+) and Jamie (26) both have low tolerance for friction. The 60-second benchmark is measurable — use it as the acceptance criterion for all onboarding work.*

### D4 — Reduce, Don't Replace
Every feature should reduce an existing behaviour (sending a WhatsApp message, updating a spreadsheet row), not introduce a new behaviour the user doesn't already have. The app is a better WhatsApp for club admin — not a new category of software.

*Added: Sprint 000. Rationale: Users will not learn new habits. The app must slot into their existing mental model.*

### D5 — Email as the Minimum Viable Notification
Push notifications are an enhancement. Email is the guaranteed baseline. Every notification flow must have an email fallback that works without any app installation or home screen prompt.

*Added: Spike 001. Rationale: Dave (iOS 15) cannot receive Web Push without home screen installation. ~15% of members will have similar constraints. Email ensures 100% reach.*

---

## Technical Principles

### T1 — User ≠ Member
A `user` is an auth identity (NextAuth.js session). A `member` is a club-specific role linked to a club and a user. These are separate entities in the database. A user can be a member of multiple clubs without duplicate accounts. Never conflate the two in the data model or the UI.

*Added: Sprint 001. Rationale: Marcus Thorne identified this as a hard-to-reverse architectural decision. Established before any club-specific features are built.*

### T2 — Server Actions for Side Effects
Any operation with a side effect (database write, email send, notification trigger) must use a Next.js server action, not a client-side event handler. Client-side events are unreliable on slow connections. If the server action fails, the error is surfaced — not silently dropped.

*Added: Sprint 001. Rationale: Kira Sharma flagged client-side reliability risk for members on poor mobile connections during Sunday morning fixtures.*

---

## Principle Change Log

| Date | Change | Sprint | Reason |
|---|---|---|---|
| 2026-01-15 | Added D1, D2, D4 | Sprint 000 | Foundation principles from PROJECT_CONTEXT.md |
| 2026-01-28 | Added D3, T1, T2 | Sprint 001 | Onboarding sprint decisions and architectural constraints |
| 2026-02-10 | Added D5 | Spike 001 | Push notification research revealed iOS coverage gap |
