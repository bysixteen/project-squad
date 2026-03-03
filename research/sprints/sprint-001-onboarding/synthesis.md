---
title: "Sprint 001 · Member Onboarding — Synthesis"
type: sprint-synthesis
status: complete
date: 2026-01-28
sprint: "001"
depends-on: ["sprint-000-foundation"]
feeds-into: ["sprint-002-fixture-management", "spike-001-push-notifications"]
---

**TL;DR:** Invite-link onboarding decided. User/Member entity separation is now a hard constraint. Elias's dissent is logged with a review trigger. The creative brief is ready for the frontend developer. The biggest open question: can we send push notifications without a native app? Run Spike 001 before Sprint 002 begins.

---

## What Changed

- `research/sprints/sprint-001-onboarding/decision.md` — Decision recorded: invite-link model confirmed, User/Member separation adopted.
- `research/sprints/sprint-001-onboarding/creative-brief.md` — Frontend spec produced. Success criteria ready for validation.
- `research/DECISIONS.md` — D-003 (Invite-link onboarding) and D-004 (User/Member separation) appended.
- `research/PRINCIPLES.md` — D3 (Zero-Training Onboarding) and T1 (User≠Member), T2 (Server Actions) added.
- `research/dissent-register.md` — Elias Vance entry added with review trigger.
- `research/sprint-status.md` — Sprint 001 marked complete.

---

## What the Next Sprint Should Know

1. **The User/Member separation is non-negotiable.** Any feature that touches authentication or club membership must respect this boundary. A `user` is a NextAuth.js identity. A `member` is a club role. See T1 in PRINCIPLES.md.

2. **The invite-link model is provisional.** Elias's dissent is in the register. If adoption testing shows < 60% completion rate, the model is revisited. Sarah should report back after the first real invite batch.

3. **The SVG pitch diagram is deferred.** Build the dropdown. Don't build the diagram. A code comment should note the upgrade path.

4. **The secretary notification is a must-have.** The server action that fires when a member completes onboarding is a key part of the experience for Sarah. Do not ship without it.

5. **Push notifications are an open question.** Can we send reliable push notifications via a PWA without a native app? This question blocks Sprint 003 (fixtures, where notifications are critical). Run Spike 001 before Sprint 002 begins.

---

## Open Questions

- Can we deliver reliable push notifications via a PWA? (→ Spike 001, blocks Sprint 003)
- What happens to an invite link that is never used? Does it expire? (→ Edge case, Sprint 001 follow-up)
- Does the secretary need to see invite link analytics (sent, opened, completed)? (→ Sprint 002 scope)

---

## Elias's Dissent — Sprint 001 Summary

Elias challenged the invite-link model on adoption grounds. The team overruled him on GDPR and secretary-control grounds. His concern is in the dissent register with a clear review trigger: revisit if adoption falls below 60%.

> "I'm not saying we're wrong. I'm saying we should define a clear trigger for revisiting this if the bet doesn't pay off."

We did. See `research/dissent-register.md`.
