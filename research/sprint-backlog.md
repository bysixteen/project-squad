---
title: "Fieldside — Sprint Backlog"
type: living-document
status: active
last-updated: 2026-02-10
---

**TL;DR:** Ranked candidates for upcoming sprints and spikes. Read by every pre-flight check. The next sprint is the one at the top of the Must column.

---

## Backlog

| # | Type | Topic | Priority | Status | Notes |
|---|---|---|---|---|---|
| 002 | Sprint | Fixture Management — how does a secretary create and publish a fixture? | Must | Ready | Unblocked. Elias dissent review trigger from Sprint 001 may fire if adoption data is available. |
| 003 | Sprint | Availability Confirmation — how does a member confirm they're playing? | Must | Ready | Depends on Sprint 002 for fixture data model. |
| S-002 | Spike | Payment Provider — which provider supports low-volume recurring subscriptions at minimal cost? | Should | Ready | Run before Sprint 004 to avoid sunk-cost architecture. |
| 004 | Sprint | Subs Tracking — how does a secretary track and chase membership payments? | Should | Blocked | Blocked on S-002 (payment provider decision). |
| 005 | Sprint | Admin Dashboard — what does a secretary need to see at a glance? | Should | Candidate | Can begin once Sprints 002–004 are complete and the core data model is established. |
| 006 | Sprint | Re-engagement — how do we bring lapsed members back? | Could | Candidate | Low priority for v1. Only relevant once there are lapsed members. |
| 007 | Sprint | Push Notification Opt-In Flow — iOS home screen prompt timing and copy | Could | Candidate | Spike 001 flagged this as a follow-up. Not blocking for v1. |

---

## Completed

| # | Type | Topic | Completed | Sprint / Spike |
|---|---|---|---|---|
| 000 | Sprint | Foundation | 2026-01-15 | sprint-000-foundation |
| 001 | Sprint | Member Onboarding | 2026-01-28 | sprint-001-onboarding |
| S-001 | Spike | Push Notifications | 2026-02-10 | spike-001-push-notifications |

---

## How to use this file

- Before running a sprint or spike, check the backlog for relevant open questions or dependency notes.
- When a sprint completes, move it to the Completed table and update the status of any candidates it unblocks.
- Add candidates when a sprint's `ideas.md` or `synthesis.md` surfaces new questions.
- Elias Vance's review triggers in `dissent-register.md` can promote a candidate to Must if the trigger condition fires.
