---
title: "Sprint 001 · Member Onboarding — Creative Brief"
type: creative-brief
status: complete
date: 2026-01-28
sprint: "001"
feeds-into: ["sprint-002-fixture-management"]
---

**TL;DR:** Build the invite-link onboarding flow. Three steps. Under 60 seconds. Feels like a welcome, not a form. This brief is the acceptance criteria for the frontend build.

---

## What We're Building

A member onboarding flow that takes a new club member from receiving an invite link to seeing the squad list in under 60 seconds.

---

## Target User

**Jamie** — a club member receiving an invite link from the club secretary. He's on Android, in a hurry, and has low tolerance for friction. He will abandon the flow if it asks for too much.

**Dave** — older member, iPhone SE, Safari. Less comfortable with new technology. The flow must be self-explanatory — no tooltips, no modal explanations.

---

## The Problem We're Solving

New members have no way to join the club without going through a WhatsApp conversation with the secretary. There is no self-service path. The invite link is the self-service path — but only if it's fast enough that members don't abandon it mid-flow.

---

## The Solution

**Invite-link onboarding — three steps, one question per screen.**

1. **Landing screen:** Club name prominently displayed. One CTA: "Join [Club Name]". No other content. The URL contains the invite token — middleware validates it silently before the screen renders.

2. **Step 1 — Name:** "What's your name?" Single text input. Auto-focus. No asterisks, no "required" labels — it's the only field.

3. **Step 2 — Email:** "What's your email?" Used for magic link authentication. Help text: "We'll use this to send you fixture updates." No password field.

4. **Step 3 — Position:** "Where do you play?" Dropdown list of positions (GK, CB, RB, LB, CDM, CM, CAM, RW, LW, ST). Simple and fast for v1.

5. **Completion screen:** "Welcome to [Club Name]. You're in the squad." Member's name displayed. Link to the squad list. No account settings, no onboarding tutorial.

**Background:** Server action fires on step 3 completion. Creates `member` record. Marks invite token as used. Sends email notification to secretary: "[Jamie Rodriguez] has joined the squad."

---

## Design Direction

- **Tone:** Warm, direct, specific to the club. The club's name appears on every screen.
- **Layout:** One element per screen. No navigation. No back button visible until step 2.
- **Typography:** Large primary text (28px+). Single input per screen. Large tap targets.
- **Progress:** Simple step indicator (1/3, 2/3, 3/3). Not a progress bar — just a number.
- **Error states:** Inline, plain English. "That email doesn't look right" not "Invalid email format".

---

## Success Criteria

1. A member receiving an invite link on mobile can reach the completion screen in ≤ 60 seconds
2. The completion screen shows the member's name and a link to the squad list
3. The secretary receives an email notification within 30 seconds of the member completing step 3
4. An expired or already-used invite link shows a clear error: "This invite link has expired. Ask your secretary for a new one."
5. The flow works on Safari iOS (iPhone SE, iOS 15+) and Chrome Android
6. No JavaScript errors on slow 3G connections

---

## What This Is NOT

- Not a full user profile builder (photo, bio, shirt number — later sprints)
- Not an account settings flow
- Not a tutorial or app walkthrough
- Not a password-based auth flow (magic link only for members)

---

## Constraints

- **Tech:** Next.js server actions for all side effects. No client-side event handlers for database writes or email sends.
- **Data:** `user` and `member` are separate entities. Never conflate them. See DECISIONS.md D-004.
- **GDPR:** Do not store any data before the member completes step 3. If they abandon at step 2, no record is created.
- **Invite token:** Must be validated server-side before the landing screen renders (middleware). A tampered or missing token shows a 404 — do not show an error that reveals the invite system structure.

---

## Handoff Notes

- See `sketches.md` for full persona perspectives on this sprint
- See `decision.md` for the invite-link model rationale and Elias's dissent
- The SVG pitch diagram is deferred — build the dropdown and note the upgrade path in a code comment
