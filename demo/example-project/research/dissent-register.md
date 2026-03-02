# Fieldside — Dissent Register

**Last updated:** 2026-03-02 — Sprint 001 (Member Onboarding)

This document records all significant dissenting opinions raised during sprints and spikes, primarily from Elias Vance (the Mandatory Challenger). Dissent is a feature. Recording it ensures that overruled concerns are not lost and can be revisited.

The `Review Trigger` column specifies the condition under which a dissenting view should be actively revisited. The `/create-sprint` command scans this column before each sprint and surfaces any entries whose trigger matches the upcoming sprint's topic.

| Sprint / Spike | Topic | Dissenting Persona | Dissenting View | Outcome | Review Trigger |
|---|---|---|---|---|---|
| Sprint 001 | Member onboarding — invite-link model | Elias Vance | "An invite-link model assumes the secretary is proactive enough to send invites. In practice, they won't. Members will try to sign up independently and hit a wall. We're optimising for a problem we don't have (spam registrations) at the cost of the problem we do have (low adoption)." | Overruled. Team agreed that open registration creates data quality and GDPR risks that outweigh the adoption concern. Invite links can be shared publicly if needed. | Revisit if user testing in Sprint 003 or later shows that member adoption is below 60% of invited members completing registration. |
