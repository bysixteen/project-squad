---
title: "Sprint 001 · Member Onboarding — Decision"
type: sprint-decision
status: complete
date: 2026-01-28
sprint: "001"
depends-on: ["sprint-000-foundation"]
feeds-into: ["sprint-002-fixture-management"]
---

**TL;DR:** Proceed with invite-link onboarding model. Three-step flow (name → email → position). User/Member entity separation adopted as a hard architectural constraint. Elias Vance dissented on the invite-link model — recorded with a review trigger.

---

## Decision

**Proceed with invite-link onboarding model.**

The invite-link model was chosen in Sprint 000 provisionally, and the squad confirmed it in this sprint. The GDPR risk of open registration — collecting data from people who may not be genuine club members — is a real constraint, not a hypothetical one.

The onboarding flow is:
1. Member receives invite link (email or WhatsApp from secretary)
2. Landing page: club name, one clear CTA ("Join [Club Name]")
3. Step 1: Full name
4. Step 2: Email address (used for magic link auth)
5. Step 3: Playing position (visual SVG pitch diagram — see scope note below)
6. Completion screen: "Welcome to [Club Name]. You're in the squad."
7. Server action fires: secretary notification sent via email

**The User/Member entity separation is adopted as a core data model decision.** A `user` is an auth identity; a `member` is a club-specific role. See DECISIONS.md D-004.

**Scope decision on the SVG pitch diagram:** Build a simple dropdown list of positions for v1. The SVG pitch diagram is a nice-to-have. If user testing in Sprint 003 shows the position step is a friction point, upgrade it then.

---

## Rationale

- GDPR: Open registration with a club code would collect email addresses from people who may not be club members. Invite-only keeps the data model clean.
- Secretary control: Sarah's fear is unknown people in the group. The invite model is a feature for her, not a compromise.
- Adoption: The three-step flow is achievable in under 60 seconds on a slow mobile connection.

---

## Rejected Alternatives

- **Open registration with club code** — proposed by Elias Vance. Reduces per-member secretary burden but introduces GDPR risk. Logged in dissent register.
- **Full profile on signup** — rejected by Marcus. Collecting bio, photo, and position history in one step creates friction. Minimum viable data only.
- **SVG pitch diagram for position selection** — deferred by team consensus. Builds the dropdown first; upgrade in Sprint 003 if warranted.

---

## Elias Vance — Dissent

> "An invite-link model assumes the secretary is proactive enough to send invites. In practice, they won't. Members will try to sign up independently and hit a wall. We're optimising for a problem we don't have (spam registrations) at the cost of the problem we do have (low adoption)."

**Outcome:** Overruled. Team maintained invite-link on GDPR grounds and secretary-control rationale.

**Logged in dissent register with Review Trigger:** Revisit if user testing in Sprint 002 or later shows that member adoption is below 60% of invited members completing registration.

---

## Next Action

Build the onboarding flow against the `creative-brief.md`. Test with a real invite link in the staging environment before Sprint 002 begins. Adoption rate (invite sent → squad list reached) is the key metric — Sarah to confirm after first real invite batch.
