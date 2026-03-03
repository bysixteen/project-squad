---
title: "ADR-002 · PWA Web Push with Email Fallback"
type: adr
status: accepted
date: 2026-02-10
spike: "spike-001-push-notifications"
tags: [push-notifications, pwa, notifications, ios, android]
---

**TL;DR:** Use Web Push via a Progressive Web App for notifications. Always send email in parallel. iOS requires home screen installation — prompt after the squad list screen.

---

## Context

Sprint 001 established that Fieldside will be a PWA (no native iOS/Android app for v1). Sprint 002 (Fixture Management) requires a reliable notification channel to inform members of upcoming fixtures and request availability confirmations. Spike 001 investigated whether Web Push via a PWA is viable.

## Decision

**Implement PWA Web Push notifications with mandatory email fallback.**

Every notification flow (fixture reminder, availability request, squad announcement) will:
1. Send a Web Push notification to members with an active push subscription
2. Send an email notification to all members regardless of push subscription status

Web Push is the enhancement. Email is the baseline.

## Consequences

### Positive
- No native app required — PWA push covers ~85% of the user base (Android + desktop + iOS 16.4+ with home screen)
- Email fallback ensures 100% reach regardless of platform
- Implementation is self-contained — no third-party push service required

### Negative
- iOS members must add the app to their home screen to receive push notifications (iOS 16.4+ only)
- ~15% of members (older iOS, pre-16.4) will receive email only
- Subscription expiry is an ongoing maintenance concern

### Conditions
1. iOS home screen prompt must be shown after the squad list screen (not during onboarding)
2. Push sending code must handle `410 Gone` / `404 Not Found` responses and mark expired subscriptions
3. Email is never optional — always send regardless of push subscription status

## Rejected Alternatives

- **Native iOS/Android app:** Out of scope for v1. Single developer, zero budget.
- **SMS notifications:** Out of budget for v1 scale. Twilio costs would exceed the zero-budget constraint.
- **Third-party push service (OneSignal, etc.):** Adds a paid dependency and a third-party data processor (GDPR consideration). Achievable natively with `web-push` npm package.

## References

- `research/spikes/spike-001-push-notifications/output.md` — full investigation and evidence
- `research/spikes/spike-001-push-notifications/summary.json`
- `research/PRINCIPLES.md` — Principle D5 (Email as the Minimum Viable Notification)
