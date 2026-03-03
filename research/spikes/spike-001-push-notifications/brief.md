---
title: "Spike 001 · Push Notifications"
type: spike-brief
status: complete
date: 2026-02-05
spike: "S-001"
topic: Push Notifications without a Native App
personas: [lena, marcus, kira, elias]
depends-on: ["sprint-001-onboarding"]
feeds-into: ["sprint-002-fixture-management"]
tags: [push-notifications, pwa, ios, android, web-push]
---

**TL;DR:** One question. Can we deliver reliable push notifications to club members using a web app (PWA), without building a native iOS/Android app? This question blocks Sprint 002 (Fixture Management) — we need to know before designing the fixture notification flow.

---

## The Question

**Can we deliver reliable push notifications to club members using a web app (PWA), without building a native iOS/Android app?**

---

## Why This Question Matters

Sprint 001 decided on a PWA-first approach (no native app for v1). Push notifications are critical for fixtures: "Your game is on Saturday at 10am, please confirm availability." If push notifications don't work reliably via a PWA, we need to fall back to email only — which means redesigning the notification flow in Sprint 002.

This question must be answered before Sprint 002 begins, or we risk building a fixture notification system on an assumption that turns out to be wrong.

---

## Spike Qualification Test

| Question | Answer |
|---|---|
| Is this a real unknown that cannot be resolved by a quick search? | Yes — PWA push notification support varies significantly by platform and OS version. The devil is in the iOS details. |
| Is the answer needed before the next sprint can proceed? | Yes — Sprint 002 fixture management depends on knowing the notification approach. |
| Can this be answered in a time-boxed investigation (1–4 hours)? | Yes — browser compatibility tables and MDN docs are authoritative. |

**Result: Qualified.** Run as a spike.

---

## Acceptance Criteria (Knowledge Outcomes)

- We know whether Web Push works on Android without app installation
- We know the iOS constraint (version, home screen installation requirement)
- We know the approximate developer effort to implement Web Push in a Next.js app
- We have a clear recommendation: proceed, proceed with conditions, or do not proceed
- We have identified a fallback notification strategy if Web Push coverage is insufficient

---

## Timebox

4 hours

---

## Investigation Angles

- **Dr. Lena Petrova:** MDN Web Push API documentation, Next.js PWA implementation patterns
- **Kira Sharma:** Browser compatibility tables (Can I Use), developer effort estimate, service worker constraints
- **Marcus Thorne:** iOS version landscape for grassroots sports club users, long-term maintenance implications
- **Elias Vance:** User experience implications — what happens when push fails silently? What does the fallback feel like?

---

## Known Starting Points

- Web Push API exists and is supported on Chrome (Android + desktop)
- iOS 16.4+ added home screen PWA push support
- Many club members may be on older iOS versions (see Dave persona in PERSONAS.md — iOS 15)
- Email is the confirmed fallback (Principle D5, added during this spike)
