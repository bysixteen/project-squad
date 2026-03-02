---
title: "Spike 001: Can we deliver push notifications without a native app?"
type: spike-brief
status: complete
date: 2026-03-02
spike: "001"
question: "Can we deliver reliable push notifications to club members using a web app (PWA), without building a native iOS/Android app?"
depends-on: [sprint-001-member-onboarding]
feeds-into: [sprint-003-fixture-management]
tags: [notifications, pwa, mobile]
---

**TL;DR:** Investigate whether Web Push (PWA) is a viable alternative to native push notifications for fixture reminders and squad announcements.

---

## The Question

**Can we deliver reliable push notifications to club members using a web app (PWA), without building a native iOS/Android app?**

This is a single, specific question. If the answer is yes, we can ship fixture reminders and squad announcements as part of the web app. If the answer is no, we need to either accept that notifications will be email/SMS only, or commit to building a native app — a significant scope increase.

---

## Why This Is a Spike

This question cannot be estimated without investigation. The answer depends on:
- Browser support for the Web Push API across iOS and Android
- Whether iOS Safari's recent PWA support changes are production-ready
- The reliability of push delivery compared to native notifications
- The complexity of implementing a service worker and push subscription flow

Without this investigation, we cannot estimate the effort for the fixture reminders feature, and we cannot make a confident decision about whether to build a native app.

---

## Spike Qualification

| Question | Answer |
|----------|--------|
| Can you confidently estimate the effort required? | No — browser support is the unknown |
| Is this uncertainty actively blocking a decision? | Yes — blocks Sprint 003 fixture reminders |
| Is the primary goal to gain knowledge, not to ship a feature? | Yes |

**Result: Spike is qualified.**

---

## Time Box

Maximum 4 hours of investigation. This spike should produce a clear yes/no recommendation, not a prototype.

---

## What "Done" Looks Like

A spike output document (`output.md`) that answers the question with a clear recommendation, supported by evidence from browser compatibility data and any relevant technical testing. A `summary.json` for machine-readable output.

---

## Investigator

Dr. Lena Petrova (Design Engineer) — primary investigator, with Marcus Thorne (Senior Developer) as reviewer.
