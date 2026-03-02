---
title: "Sprint 001: Synthesis — Member Onboarding"
type: sprint-synthesis
status: complete
date: 2026-03-02
sprint: "001"
decision: "Invite-link model with one-question-per-screen flow. User and Member are separate database entities."
---

**TL;DR:** The invite-link onboarding flow is the right approach. Build it in three steps (name, position, confirm), store progress server-side, and land the member on the squad list. The real risk is not the flow — it's whether the secretary will send the invites. Watch adoption rates closely.

---

## What We Decided

The member onboarding flow will use an invite-link model with a three-step, one-question-per-screen design. The flow ends with the member landing on the squad list with their name highlighted — the emotional payoff that makes the first session feel worthwhile.

The User/Member entity separation is adopted as a core data model decision. A `user` is an auth identity; a `member` is a club-specific role. This enables multi-club support without duplicate accounts.

---

## Why This, Not That

The main alternative considered was open registration with a club code. The team rejected it on GDPR grounds: open registration means collecting data from people who may not be genuine club members, with no mechanism to verify intent. The invite-link model ensures that every person who joins has been explicitly invited by the club secretary.

Elias Vance challenged this reasoning — his view is that we are optimising for a GDPR risk that may be smaller than the adoption risk created by secretary dependency. His dissent is recorded and a review trigger has been set.

---

## Key Insights from the Sketch Phase

**The first screen is a brand moment.** The landing page a member hits when they tap the invite link is the first brand impression. It should show the club name and a single clear action — not a generic Fieldside splash screen. Leo's instinct here is right.

**One question per screen is the right pattern.** It feels like a conversation, not a form. It works on mobile. It allows us to save progress after each step. The pitch diagram for position selection is a strong differentiator — it's faster than a dropdown and immediately signals that the app understands the sport.

**The secretary notification is critical.** The secretary needs to know when a member completes onboarding without having to check. This must be a server-side event, not a client-side one, to be reliable on slow connections.

**Onboarding progress must be server-side.** If a member closes the browser mid-flow, the invite token is still valid. Progress must be stored in the database against the token so the member can resume without starting over.

---

## What We Are Not Building in This Sprint

- Full user profile (no photos, bio, or social links — name, email, and position only)
- Secretary invite management UI (invite generation is a hardcoded server action for now)
- Multi-club support (the data model supports it, but the UI does not need to expose it yet)

---

## Risks and Open Questions

**Risk — Secretary adoption:** The invite-link model depends on the secretary proactively sending invites. If they don't, members can't join. This is the highest-risk assumption in the product. We should track the ratio of invites sent to invites completed and revisit the onboarding model if adoption is below 60%.

**Open question — Multi-team clubs:** A football club with men's, women's, and youth teams needs a way to manage multiple squads. The User/Member separation supports this, but we haven't designed the UI for it. This should be a backlog candidate for a future sprint.

**Open question — Invite expiry:** How long should an invite link be valid? The team did not resolve this. Recommendation: 7 days, with the secretary able to resend from the admin panel.

---

## Living Documents Updated

- `research/DECISIONS.md` — Decision 004 added: invite-link onboarding model
- `research/dissent-register.md` — Elias's challenge to the invite-link model recorded with review trigger
- `research/sprint-status.md` — Sprint 001 marked complete
- `docs/decisions/003-onboarding-model.md` — Full ADR written

---

## Next Sprint Recommendation

Aris raised a valid point: the secretary has no reason to invite members until the app is useful to them independently. The next sprint should be **fixture management** (backlog item 003) rather than anything member-facing. A secretary who can manage fixtures in Fieldside has a reason to invite their squad. A secretary who can only send invites does not.
