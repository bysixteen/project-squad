---
title: "Sprint 001 · Member Onboarding — Sketches"
type: sprint-sketches
status: complete
date: 2026-01-28
sprint: "001"
---

**TL;DR:** All seven personas responded to the sprint challenge. The key tensions: brand vs. speed (Leo vs. Kira), scope enforcement vs. experience quality (Marcus vs. Rowan), adoption model (Elias vs. the team). Decision in `decision.md`.

---

## Leo Finch — Visual Designer

> The invite link is the first brand impression. The landing page should feel warm and specific to their club — the club name, the club colours, and a single clear action. The onboarding flow should feel like a conversation, not a form. One question per screen. The position selector should be a visual pitch diagram — faster, more engaging, and it immediately signals that this app understands football.

**Signature question:** "Does this feel like us?"

---

## Dr. Lena Petrova — Design Engineer

> NextAuth.js supports custom sign-in pages — we can build the invite-link landing page as a standard Next.js page. The one-question-per-screen pattern is achievable with a simple step-based state machine in React. The secretary notification on completion must use a server action, not a client-side event. Client-side events are unreliable on slow connections. The SVG pitch diagram is buildable but is the most complex element — budget 1.5 days for it.

**Signature question:** "How will we build, test, and maintain this?"

---

## Marcus Thorne — Senior Developer

> We are not building a full user profile system in this sprint. Name, email, and playing position only. The data model decision that matters most: a "member" is not the same as a "user". Keep them separate. A user is an auth identity; a member is a club-specific role. This allows the same person to be a member of multiple clubs without duplicate accounts. If we don't make this separation now, we'll pay for it when the second club signs up.

**Signature question:** "What are we NOT building here?"

---

## Kira Sharma — Developer

> Secretary triggers invite → server creates record in `invites` table with token, expiry, used flag → member taps link → middleware validates token → member completes three steps → server creates `member` record, marks invite used, fires notification. Effort: 3–4 days. The SVG pitch diagram is the wildcard — could be 0.5 days (static SVG with click handlers) or 2 days (animated, responsive). Recommend starting with a simple dropdown list of positions and upgrading the diagram in Sprint 003 if it becomes a pain point.

**Signature question:** "What does the implementation actually look like?"

---

## Dr. Aris Thorne — Strategist

> The real problem is not the onboarding flow — it's adoption. The app has to be useful to the secretary before members join. If the secretary can manage fixtures and track payments on their own, they will have a reason to invite members. If the app only becomes useful once members are on it, we have a chicken-and-egg problem. Sprint 001 solves the member side. Sprint 002 (Fixture Management) must solve the secretary side before we launch to a real club.

**Signature question:** "What is the real problem we are trying to solve?"

---

## Rowan Vale — Craftsman

> The onboarding flow is not just a form — it is the first time a member feels like they belong to the club. The invite link email should feel personal, not automated. The three-step flow should feel like a welcome, not a registration. The completion screen should confirm their place in the squad, not just confirm their account. The secretary notification is a moment of delight for the admin — make it feel like something happened, not like a system event.

**Signature question:** "What does this feel like from beginning to end?"

---

## Elias Vance — Client (Mandatory Dissent)

> I want to challenge the invite-link model directly. The secretary has to do something before any member can join. That's a dependency on the least reliable person in the system — not because Sarah is unreliable, but because she's a volunteer who already has too much to do. The alternative — open registration with a club code — puts the burden on the member, not the secretary. A member who wants to join just enters the code. I'm not saying we're wrong. I'm saying we should define a clear trigger for revisiting this if the bet doesn't pay off.

**Signature question:** "Does this solve a real problem for my users?"

*Note: Elias's challenge was acknowledged and discussed. The team maintained the invite-link model on GDPR grounds. See `decision.md` and `dissent-register.md`.*
