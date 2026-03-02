---
title: "Sprint 000: Foundation"
type: sprint-brief
status: complete
date: 2026-03-02
sprint: "000"
personas: [leo, lena, marcus, kira, aris, rowan, elias]
depends-on: []
feeds-into: [sprint-001-member-onboarding]
tags: [foundation, setup]
---

**TL;DR:** Foundation sprint to establish shared context, document known constraints, and align the squad on what "good" looks like for Fieldside before any feature work begins.

---

## Sprint Challenge

Community sports clubs are drowning in admin. The tools they use — WhatsApp, spreadsheets, paper — were not designed for this job, and the people running clubs are volunteers who cannot afford to spend their weekends on admin.

## Long-Term Goal

In 12 months, a club secretary running Fieldside spends less than 30 minutes per week on club admin. Members know when they're playing, whether they've paid, and who else is in the squad — without ever having to ask. Lapsed members find their way back because re-engagement is frictionless.

## Sprint Questions

1. Do we have a shared understanding of who our primary users are and what they actually need?
2. Do we have a shared understanding of what "good" looks like on this project?
3. Are there existing constraints or decisions that should be documented before we start building?

## Target User

All three personas — Club Secretary, Active Member, Casual/Lapsed Member. Foundation sprint covers the full landscape.

## Target Moment on the Map

Not applicable — foundation sprint establishes baseline context rather than targeting a specific user moment.

## Project Squad

| Persona | Name | Role in This Sprint |
|---------|------|---------------------|
| Visual Designer | Leo Finch | Brand and tone review |
| Design Engineer | Dr. Lena Petrova | Technical constraints |
| Senior Developer | Marcus Thorne | Architecture decisions |
| Developer | Kira Sharma | Implementation reality |
| Strategist | Dr. Aris Thorne | Research synthesis |
| Craftsman | Rowan Vale | End-to-end experience |
| Client | Elias Vance | Reality check |

## How Might We Questions

1. HMW make the secretary's weekly admin routine feel effortless rather than burdensome?
2. HMW ensure members always have the information they need without having to ask?
3. HMW design for the lapsed member without making the active member's experience worse?
4. HMW build something that works reliably in a muddy field with poor signal?
5. HMW make the system self-sustaining so it doesn't depend on the secretary remembering to do things?

## Constraints

- Budget is minimal — no paid third-party services unless essential and cheap.
- MVP must be deployable within 8 weeks.
- GDPR compliance is required.
- The secretary is the only admin — the system cannot require technical knowledge to operate.

## Known Data and Assumptions

- **Assumption:** Club secretaries are the primary adoption blocker. If they don't use it, members won't either.
- **Assumption:** Most members will access the app on a phone, not a desktop.
- **Known:** Next.js 14, PlanetScale, Sanity, and NextAuth.js are the agreed stack.
- **Known:** pnpm is the required package manager.
