---
title: "Sprint 001: Member Onboarding"
type: sprint-brief
status: complete
date: 2026-03-02
sprint: "001"
personas: [leo, lena, marcus, kira, aris, elias]
depends-on: [sprint-000-foundation]
feeds-into: [sprint-003-fixture-management]
tags: [onboarding, members, auth]
---

**TL;DR:** How does a new member join Fieldside for the first time — and how do we make it fast enough that they don't give up?

---

## Sprint Challenge

The first time a member uses Fieldside is the highest-risk moment in the product. If onboarding is slow, confusing, or requires too much information, they will abandon it and go back to WhatsApp. We need to design an onboarding flow that gets a member from "I've been sent a link" to "I can see my squad and my next fixture" in under 60 seconds.

## Long-Term Goal

Every member of every club using Fieldside completes onboarding on their first attempt, without help from the secretary, and immediately sees something worth coming back for.

## Sprint Questions

1. Can we design a member onboarding flow that completes in under 60 seconds on a mobile device?
2. Will members trust a "join via invite link" model, or will they expect to be able to register independently?
3. Can we collect enough information during onboarding to be useful to the secretary without creating friction for the member?

## Target User

**The Active Member** — a regular player who has been sent an invite link by the club secretary. They are on their phone, probably between training sessions. They have moderate patience and low tolerance for forms.

## Target Moment on the Map

The moment between receiving the invite link and seeing the club dashboard for the first time. This is the make-or-break moment for adoption.

## Project Squad

| Persona | Name | Role in This Sprint |
|---------|------|---------------------|
| Visual Designer | Leo Finch | Onboarding UI and first-impression design |
| Design Engineer | Dr. Lena Petrova | Auth flow and component feasibility |
| Senior Developer | Marcus Thorne | NextAuth.js integration and data model |
| Developer | Kira Sharma | Implementation of the invite-link flow |
| Strategist | Dr. Aris Thorne | User journey mapping and HMW synthesis |
| Client | Elias Vance | Mandatory challenge — is this solving the right problem? |

## How Might We Questions

1. HMW make the invite-link experience feel personal rather than generic?
2. HMW collect the member's name and position without making it feel like a form?
3. HMW show the member something valuable before asking them to do anything?
4. HMW handle the case where the invite link has expired or been used already?
5. HMW design the onboarding so it works on a slow 3G connection?

## Constraints

- NextAuth.js is the auth layer — the onboarding flow must work within its session model.
- No email verification step — it adds friction and the invite link is already a trust signal.
- The secretary must be notified when a member completes onboarding (without having to check).
- GDPR: we can only collect name, email, and playing position at this stage.

## Known Data and Assumptions

- **Assumption:** Members will receive the invite link via WhatsApp or SMS, not email.
- **Assumption:** Most members will complete onboarding on a mobile device.
- **Known:** The invite-link model was chosen in Sprint 000 to avoid open registration and GDPR risks.
- **Known:** The secretary needs to know who has and hasn't completed onboarding.
