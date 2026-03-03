---
title: "Fieldside — Client Personas"
type: living-document
status: active
last-updated: 2026-01-28
updated-by: sprint-000-foundation
---

**TL;DR:** Three user archetypes for Fieldside. Sarah (the secretary) is the primary user. Every feature decision should start with: does this make Sarah's admin work easier?

---

## Sarah — The Club Secretary

**Age:** 34
**Role:** Volunteer secretary, Northbrook Sunday FC (28 members)
**Location:** Manchester
**Device:** iPhone 13, Safari

**Goal:** Spend less time on club admin and more time actually playing. Specifically: send one message, confirm the squad, and chase payments — all in under 10 minutes per week.

**Current workflow:**
1. Creates WhatsApp message with fixture details
2. Posts to the club group (40% of members see it within 24 hours)
3. Sends individual follow-up messages to non-responders
4. Updates a Google Sheet with availability
5. Chases subs via a separate WhatsApp message to the group

**Pain points:**
- "I send the same message three times and half the lads still don't see it."
- Chasing subs feels embarrassing and confrontational
- Managing the group chat (adding new members, removing leavers) is unpredictable
- Doesn't know who has actually seen a message vs. ignored it

**Key quote:** *"I don't want an app. I want to stop spending Sunday mornings managing a group chat."*

**Fear:** Any tool that creates more work than it saves will be abandoned within a month. She is the gatekeeper — if she doesn't adopt it, no one does.

**Insight from Sprint 000:** Sarah's primary fear is not poor features — it is admin burden. The invite-link model was adopted because it keeps the secretary in control of membership, reducing her anxiety about unknown people joining.

---

## Jamie — The Club Member

**Age:** 26
**Role:** Centre midfield, Northbrook Sunday FC
**Location:** Salford
**Device:** Android (Samsung Galaxy), Chrome

**Goal:** Know when the match is, confirm he's playing, and not have to remember to pay his subs.

**Current workflow:**
1. Occasionally checks the WhatsApp group
2. Misses messages buried under memes and off-topic chat
3. Gets a direct message from Sarah when he hasn't confirmed
4. Pays subs in cash at the match or via bank transfer when reminded

**Pain points:**
- "The group chat is chaos. I missed a game because I didn't see the message buried in memes."
- Can't remember if he's paid subs or not
- Doesn't know who else is confirmed for the match

**Key quote:** *"Just tell me when it is and I'll be there."*

**Adoption threshold:** Will use an app if it saves him from reading 200 WhatsApp messages. Will not use it if it requires effort or exploration. The onboarding flow must be zero-friction.

**Device note:** Android user — push notifications should work via Web Push without home screen installation. Spike 001 confirms this.

---

## Dave — The Long-Standing Member

**Age:** 47
**Role:** Club treasurer / right back, Northbrook Sunday FC
**Location:** Stretford
**Device:** iPhone SE (2020), Safari — iOS 15 (not yet updated)

**Goal:** Know when and where the game is. Nothing more.

**Pain points:**
- Not comfortable with new technology
- "I don't understand all these apps. Can you not just text me?"
- Has missed two fixtures because he didn't check WhatsApp

**Key insight from Sprint 000:** Dave represents a significant segment of older, less tech-savvy members. The app must work with email as a fallback notification channel — push notifications are not reliable for him (iOS 15 does not support Web Push; Spike 001). SMS is out of budget for v1.

**Adoption threshold:** Will use the app if Sarah explains it once. Will not explore features independently. The "60 seconds to squad list" goal was designed with Dave in mind.

---

## Persona Notes

- These personas were established in Sprint 000 (Foundation) and refined in Sprint 001 (Member Onboarding).
- Elias Vance speaks on behalf of all three personas during the Decide phase of every sprint.
- When a new sprint reveals new insights about any persona, update this file in the Synthesise phase.
- The dissent register entry from Sprint 001 references Sarah and Jamie's adoption risk — see `research/dissent-register.md`.
