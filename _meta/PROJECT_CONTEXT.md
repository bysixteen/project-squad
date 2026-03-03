---
title: "Fieldside — Project Context"
type: project-context
status: active
date: 2026-01-15
version: 1.0.0
---

**TL;DR:** Fieldside is a community sports club management app for grassroots football clubs. It replaces WhatsApp groups and spreadsheets with a lightweight, mobile-first tool for secretaries and members.

---

## 1. Project Overview

**Name:** Fieldside

**One-line description:** A mobile-first app that helps grassroots football club secretaries manage their squad, fixtures, and payments — and keeps members informed without the chaos of WhatsApp.

**North Star goal:** Every member of a grassroots football club can see their next fixture, confirm availability, and pay their subs in under 60 seconds — without the secretary having to chase anyone.

**Problem it solves today:** Club secretaries manage 20–40 members across WhatsApp, a spreadsheet for payments, and a shared calendar. Information is lost in chat threads. Members miss fixtures because they didn't see the message. Payments are tracked in a notebook. The secretary spends 3–5 hours per week on admin that should take 30 minutes.

**Explicitly out of scope (v1):**
- Live match scoring and statistics
- League table management (separate system)
- Multi-sport (football only for v1)
- In-app payments (payment tracking only, not processing)
- Public club pages / recruitment

---

## 2. The Users

### Sarah — The Club Secretary
- **Role:** Volunteer secretary for a 30-person Sunday league club
- **Goal:** Spend less time on admin and more time actually playing
- **Frustration:** "I send the same message three times and half the lads still don't see it. And chasing subs is embarrassing."
- **Key behaviour:** Manages everything from her phone. Doesn't want to learn a new tool — wants it to feel like an upgrade from WhatsApp, not a replacement.
- **Fear:** Admin burden. Any tool that creates more work than it saves will be abandoned within a month.

### Jamie — The Club Member
- **Role:** Regular player, mid-20s, works full time
- **Goal:** Know when the match is, confirm he's playing, and not have to remember to pay
- **Frustration:** "The group chat is chaos. I missed a game because I didn't see the message buried in memes."
- **Key behaviour:** Will use an app if it saves him from reading 200 WhatsApp messages. Won't use it if it requires effort.

### Dave — The Long-Standing Member
- **Role:** Older member (45+), less tech-savvy
- **Goal:** Just wants to know when and where the game is
- **Frustration:** "I don't understand all these apps. Can you not just text me?"
- **Key behaviour:** Will use the app if the secretary explains it once. Will not explore features independently.

---

## 3. Squad Mapping

| Persona | Real-world counterpart |
|---|---|
| Leo Finch (Visual Designer) | N/A — AI persona |
| Dr. Lena Petrova (Design Engineer) | N/A — AI persona |
| Marcus Thorne (Senior Developer) | N/A — AI persona |
| Kira Sharma (Developer) | N/A — AI persona |
| Dr. Aris Thorne (Strategist) | N/A — AI persona |
| Rowan Vale (Craftsman) | N/A — AI persona |
| Elias Vance (Client) | Speaks on behalf of Sarah, Jamie, and Dave |

---

## 4. Design Principles (Initial)

1. **Mobile-first:** Every screen is designed for a 390px viewport first. No desktop-only tables or layouts.
2. **Secretary-first:** If a feature creates more work for the secretary than it saves, it doesn't ship.
3. **Zero-training onboarding:** A member receiving an invite link should reach the squad list in under 60 seconds without reading any instructions.
4. **Reduce, don't replace:** Features should reduce an existing behaviour (WhatsApp message, spreadsheet row) not introduce a new behaviour the user doesn't already have.

---

## 5. Known Decisions

| Decision | Rationale | Rejected alternative |
|---|---|---|
| Next.js (App Router) + Vercel | Team familiarity, edge deployment, built-in server actions | Remix (less team experience) |
| PostgreSQL via Supabase | Managed, free tier sufficient for v1, good Next.js integration | Firebase (NoSQL, less suitable for relational data like fixtures/payments) |
| Invite-link onboarding (provisionally) | Reduces spam registrations, gives secretary control over membership | Open registration with club code (to be confirmed in Sprint 001) |

---

## 6. Tech Stack

- **Framework:** Next.js 14 (App Router)
- **Auth:** NextAuth.js v5
- **Database:** PostgreSQL via Supabase
- **Hosting:** Vercel
- **Styling:** Tailwind CSS
- **Email:** Resend

---

## 7. Open Questions (Sprint Candidates)

| Question | Type | Priority |
|---|---|---|
| How does a member join? What is the onboarding flow? | Sprint | Must — Sprint 001 |
| Can we send push notifications via a PWA without a native app? | Spike | Must — blocks Sprint 003 |
| How does a secretary create and publish a fixture? | Sprint | Must — Sprint 003 |
| How does a member confirm availability for a fixture? | Sprint | Must — Sprint 004 |
| How does a secretary track subs payments? | Sprint | Should — Sprint 005 |
| Which payment provider supports low-volume recurring subscriptions at minimal cost? | Spike | Should — before Sprint 005 |
| How do we re-engage members who haven't confirmed availability in 2+ fixtures? | Sprint | Could — Sprint 007 |

---

## 8. Constraints

- **Solo developer:** All implementation is by one developer (Sarah's brother, a junior developer). Architecture must be simple and maintainable by one person.
- **Zero budget for v1:** Supabase free tier, Vercel hobby plan, Resend free tier. No paid services until there are 10+ clubs.
- **GDPR:** Users are UK-based. Email addresses are PII. Must not expose them in any URL or share them with third parties.
- **Timeline:** MVP for one live club by end of Q1 2026.

---

## 9. Sprint Notes for AI

- Always treat Sarah (secretary) as the primary user. If a feature doesn't make her life easier, reconsider it.
- The User/Member entity separation is a hard constraint established in Sprint 001: a `user` is an auth identity, a `member` is a club-specific role.
- Never suggest features that require the user to leave the app to complete a task (e.g., "just email them" is not a solution).
- Elias speaks on behalf of Sarah, Jamie, and Dave in every Decide phase.
