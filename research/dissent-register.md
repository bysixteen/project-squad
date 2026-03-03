---
title: "Fieldside — Dissent Register"
type: living-document
status: active
last-updated: 2026-01-28
---

**TL;DR:** Overruled concerns from Elias Vance, recorded with review triggers. The `/create-sprint` pre-flight scans the Review Trigger column before each sprint.

---

| Sprint / Spike | Topic | Dissenting Persona | Dissenting View | Outcome | Review Trigger |
|---|---|---|---|---|---|
| Sprint 001 | Invite-Link Onboarding Model | Elias Vance | "An invite-link model assumes the secretary is proactive enough to send invites. In practice, they won't. Members will try to sign up independently and hit a wall. We're optimising for a problem we don't have (spam registrations) at the cost of the problem we do have (low adoption)." | Overruled. Team maintained invite-link on GDPR grounds. Secretary control over membership was judged more important than reducing per-invite effort. | Revisit if user testing in Sprint 002 or later shows that member adoption is below 60% of invited members completing registration. |

---

## How this register works

- This file is read by `/create-sprint` before each sprint begins.
- If a Review Trigger condition matches the upcoming sprint's topic, the entry is surfaced: *"Before we start — the dissent register has a flagged concern that may be relevant to this sprint."*
- Every entry must have a Review Trigger — a specific, testable condition under which the overruled concern is revisited.
- Dissent from Elias that is incorporated into the decision (as a condition, not overruled) is noted in the sprint's `decision.md` but does not appear here.

---

## Sprint 001 Entry — Full Record

**Sprint:** 001 · Member Onboarding
**Date recorded:** 2026-01-28
**Dissenting persona:** Elias Vance (speaking on behalf of Jamie and Sarah)

**Full dissent:**
> "I want to challenge the invite-link model directly. The secretary has to do something before any member can join. That's a dependency on the least reliable person in the system — not because Sarah is unreliable, but because she's a volunteer who already has too much to do. The alternative — open registration with a club code — puts the burden on the member, not the secretary. A member who wants to join just enters the code. I'm not saying we're wrong. I'm saying we should define a clear trigger for revisiting this if the bet doesn't pay off."

**Team response:** Acknowledged the concern. Maintained the invite-link decision on two grounds: (1) GDPR risk of collecting data from people who may not be genuine club members, (2) the secretary's control over membership was identified as a feature (Sarah's fear is unknown people in the group), not a bug.

**Review Trigger:** Revisit if user testing in Sprint 002 or later shows that member adoption is below 60% of invited members completing registration. Also revisit if Sarah reports that generating invite links is creating more admin work than it saves.
