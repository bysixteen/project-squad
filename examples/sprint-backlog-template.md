---
title: "[PROJECT NAME] — Sprint & Spike Backlog"
type: sprint-backlog
status: active
---

# [PROJECT NAME] — Sprint & Spike Backlog

**Last updated:** [DATE]

This document is a lightweight backlog of sprint and spike candidates. It is the input to `/create-sprint` and `/create-spike` — those commands read this file during their pre-flight checks and offer to pull the next candidate from it.

**How to use this file:**

Add a row whenever a new sprint or spike candidate is identified — in a meeting, during a sprint, or from an open question in a `synthesis.md`. Set the `Status` to `Candidate` when first added, `In Progress` when the sprint or spike is running, and `Done` when complete. The `Blocking` column identifies what work cannot start until this sprint or spike is complete — this is the primary signal for prioritisation.

---

## Backlog

| # | Type | Topic / Question | Priority | Status | Blocking |
|---|------|-----------------|----------|--------|----------|
| 001 | Sprint | [e.g., "Onboarding flow for new members"] | High | Candidate | [e.g., "Development of sign-up feature"] |
| 002 | Spike | [e.g., "Which payment provider supports tiered subscriptions?"] | High | Candidate | [e.g., "Sprint 003 — Automated renewals"] |
| 003 | Sprint | [e.g., "Admin dashboard — what does a club admin actually need?"] | Medium | Candidate | — |
| 004 | Spike | [e.g., "Can we use Sanity for event management, or do we need a separate system?"] | Medium | Candidate | [e.g., "Sprint 004 — Events feature"] |

---

## Done

| # | Type | Topic | Completed | Sprint / Spike Folder |
|---|------|-------|-----------|----------------------|
| — | — | _No completed items yet._ | — | — |

---

## How Candidates Are Added

Candidates should be added to this backlog from the following sources:

**Open Questions in Synthesis files:** At the end of every sprint, the `synthesis.md` file includes an "Open Questions" section. Any question that is not answered by the sprint is a candidate for a future spike or sprint. Add it here.

**Dissent Register:** If Elias Vance raises a concern that is overruled but flagged for future review, the review trigger in `research/dissent-register.md` should correspond to a backlog candidate.

**Team discussions:** Any time the team identifies a significant uncertainty or a new challenge worth investigating, add it here rather than letting it sit in a Slack thread or meeting notes.
