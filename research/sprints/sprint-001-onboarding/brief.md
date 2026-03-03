---
title: "Sprint 001 · Member Onboarding"
type: sprint-brief
status: complete
date: 2026-01-28
sprint: "001"
topic: Member Onboarding
personas: [leo, lena, marcus, kira, aris, rowan, elias]
depends-on: ["sprint-000-foundation"]
feeds-into: ["sprint-002-fixture-management", "spike-001-push-notifications"]
tags: [onboarding, auth, invite-link, member, ux]
---

**TL;DR:** The first time a member uses Fieldside is the highest-risk moment in the product. If onboarding is slow, confusing, or requires too much information, they abandon it and go back to WhatsApp. This sprint designs the flow from "I've been sent a link" to "I can see my squad and my next fixture" in under 60 seconds.

---

## Sprint Challenge

The first time a member uses Fieldside is the highest-risk moment in the product. If onboarding is slow, confusing, or requires too much information, they will abandon it and go back to WhatsApp. We need to design an onboarding flow that gets a member from "I've been sent a link" to "I can see my squad and my next fixture" in under 60 seconds.

**Long-term goal:** 100% of invited members complete onboarding within 48 hours of receiving the invite link, and reach the squad list without needing help from the secretary.

---

## Sprint Questions

1. What is the minimum information we need to collect from a new member to create a useful account?
2. How do we make the onboarding flow feel like a welcome, not a registration form?
3. What does the secretary see when a member completes onboarding?

---

## Target Moment on the Map

The moment between receiving the invite link and seeing the club dashboard for the first time. This is the make-or-break moment for adoption.

---

## Acceptance Criteria

- A member receiving an invite link can reach the squad list in ≤ 60 seconds
- The onboarding flow collects: name, email, playing position
- The secretary receives a notification when a member completes onboarding
- The invite link system prevents re-use (used flag) and expiry
- The data model separates `user` (auth identity) from `member` (club role)
- A `creative-brief.md` is produced for the frontend developer

---

## Personas Participating

All seven. This is a full sprint — the highest-risk user moment warrants the full squad.

**Sprint lead for Map phase:** Dr. Aris Thorne
**Sprint lead for Synthesise phase:** Dr. Aris Thorne
