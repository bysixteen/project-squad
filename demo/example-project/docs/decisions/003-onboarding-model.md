---
id: "003"
title: "Member onboarding model: invite-link vs. open registration"
status: accepted
date: 2026-03-02
sprint: sprint-001-member-onboarding
deciders: [Leo Finch, Dr. Lena Petrova, Marcus Thorne, Kira Sharma, Dr. Aris Thorne, Elias Vance]
dissent: Elias Vance
---

**TL;DR:** We use an invite-link model for member onboarding. The secretary generates a link; the member taps it and completes a three-step flow. Open registration was rejected on GDPR grounds.

---

## Context

Fieldside needs a way for members to join a club. Two models were considered during Sprint 001:

1. **Invite-link model:** The secretary generates a unique link per member (or a single link for the whole squad). The member taps the link and completes onboarding. No account exists before the link is tapped.

2. **Open registration with club code:** Members can register independently by searching for their club and entering a code. The secretary posts the code once (e.g., in WhatsApp) and does not need to manage individual invites.

## Decision

We adopt the **invite-link model**.

## Rationale

The primary constraint is GDPR. Open registration means collecting personal data (name, email) from anyone who finds or guesses the club code. There is no mechanism to verify that the registrant is a genuine club member. The invite-link model ensures that every account created has been explicitly authorised by the club secretary, who is the data controller for their club's member data.

A secondary consideration is data quality. Open registration creates the risk of duplicate accounts, test accounts, and accounts from people who are no longer members. The invite-link model keeps the member list clean because the secretary controls who is invited.

## Consequences

**Positive:** GDPR compliance is simpler. Member data is clean. The secretary has explicit control over who joins.

**Negative:** The secretary must take an action (generate and send an invite) before any member can join. This creates a dependency on secretary proactivity that is the primary adoption risk for the product.

## Dissent — Elias Vance

Elias argued that the invite-link model optimises for a GDPR risk that may be smaller than the adoption risk it creates. His proposed alternative (club-code open registration) would reduce per-member secretary burden significantly. The team acknowledged the concern but maintained the invite-link decision.

**Review trigger:** Revisit this decision if user testing shows that member adoption is below 60% of invited members completing registration, or if the secretary consistently fails to send invites within 48 hours of a new member joining the club.

## Alternatives Considered

| Option | Rejected because |
|--------|-----------------|
| Open registration with club code | GDPR risk — no mechanism to verify registrant is a genuine member |
| Email-only invitation | Higher friction than a link — requires the secretary to have every member's email address |
| Admin-created accounts | Highest secretary burden — admin must create each account manually |
