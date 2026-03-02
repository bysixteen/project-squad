---
title: "Sprint 001: Sketches — Member Onboarding"
type: sprint-sketches
status: complete
date: 2026-03-02
sprint: "001"
---

## Leo Finch — Visual Designer
> "Does this feel like us?"

The invite link is the first brand impression. Right now it's a raw URL — that's a missed opportunity. The landing page a member hits when they tap the link should feel warm and specific to their club: the club name, the club colours if we have them, and a single clear action. Not a generic "Welcome to Fieldside" splash screen.

The onboarding flow itself should feel like a conversation, not a form. One question per screen, large tap targets, no keyboard unless absolutely necessary. The playing position selector should be a visual grid of positions on a pitch diagram — it's faster, it's more engaging, and it immediately signals that this app understands football.

The first screen after onboarding completes should be the squad list with the member's own name highlighted. That moment of "I'm in the squad" is the emotional payoff we're designing toward.

---

## Dr. Lena Petrova — Design Engineer
> "How will we build, test, and maintain this?"

NextAuth.js supports custom sign-in pages, which means we can build the invite-link landing page as a standard Next.js page and pass the token through the auth flow. The invite token needs to be stored in the database with an expiry and a "used" flag — this is a straightforward Drizzle schema addition.

The one-question-per-screen pattern Leo is proposing is achievable with a simple step-based state machine in React. No library needed — just a `currentStep` state and a `next()` function. The pitch diagram position selector will need an SVG component, which I can build as a reusable design system component.

The secretary notification on completion is the trickiest part. We should use a database trigger or a server action that fires after the final onboarding step, not a client-side event. Client-side events are unreliable on slow connections.

---

## Marcus Thorne — Senior Developer
> "What are we NOT building here?"

We are not building a full user profile system in this sprint. Name, email, and playing position only. No profile photos, no bio, no social links. Those can come later, and adding them now will bloat the onboarding flow and delay the sprint.

We are also not building the invite management UI for the secretary in this sprint. The secretary needs to be able to send invites, but that's a separate flow. For Sprint 001, we can hardcode invite generation as a server action triggered from the admin panel — ugly, but it unblocks member onboarding without requiring the full admin UI.

The data model decision that matters most here is whether a "member" is the same as a "user" or a separate entity. My recommendation: keep them separate. A user is an auth identity; a member is a club-specific role. This allows the same person to be a member of multiple clubs without creating duplicate accounts.

---

## Kira Sharma — Developer
> "What does the implementation actually look like?"

The invite-link flow in practice: secretary triggers invite generation → server creates a record in `invites` table with `token`, `club_id`, `email` (optional), `expires_at`, `used_at` → server sends the link (initially via a copy-paste URL, later via email/SMS) → member taps link → Next.js middleware validates the token → if valid, redirects to onboarding flow with token in session → member completes three steps (name, position, confirm) → server creates `member` record, marks invite as used, fires secretary notification.

Effort estimate: 3–4 days for a developer who knows the stack. The SVG pitch diagram is the wildcard — if we build it from scratch it could take a day; if we find a suitable open-source component it's a few hours.

One risk: if the member closes the browser mid-onboarding, the invite token is still valid but the session is lost. We need to handle the "resume onboarding" case — probably by storing progress in the database against the token, not in client state.

---

## Dr. Aris Thorne — Strategist
> "What is the real problem we are trying to solve?"

The real problem is not the onboarding flow — it's adoption. A beautifully designed onboarding flow that nobody completes is worthless. The question we should be asking is: what is the secretary's incentive to send the invite links in the first place?

The answer is that the app has to be useful to the secretary *before* members join. If the secretary can use Fieldside to manage fixtures and track payments on their own, they will have a reason to invite members. If the app only becomes useful once members are on it, we have a chicken-and-egg problem.

This is an argument for building the fixture management feature in parallel with member onboarding, not after it. I'd recommend we flag this as a risk in the synthesis and consider whether Sprint 002 should be fixture management rather than whatever is next in the backlog.

---

## Elias Vance — Client (Mandatory Dissent)
> "Does this solve a real problem for my users?"

I want to challenge the invite-link model directly. The team chose it in Sprint 000 to avoid open registration, but I don't think we've stress-tested the assumption that open registration is actually a problem.

The strongest argument against invite links: the secretary has to do something before any member can join. That's a dependency on the least reliable person in the system. If the secretary forgets to send invites, or sends them to the wrong people, or the links expire before members tap them, the entire onboarding flow fails — and the secretary gets blamed.

The alternative — open registration with a club code — puts the burden on the member, not the secretary. A member searches for their club, enters a code (which the secretary posts in WhatsApp once), and joins. The secretary doesn't have to do anything per-member.

I'm not saying we're wrong to choose invite links. I'm saying we should be honest that we're making a bet on secretary proactivity, and we should define a clear trigger for revisiting this decision if that bet doesn't pay off.
