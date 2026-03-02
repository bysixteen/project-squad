---
title: "Spike 001: Output — Push Notifications Without a Native App"
type: spike-output
status: complete
date: 2026-03-02
spike: "001"
question: "Can we deliver reliable push notifications to club members using a web app (PWA), without building a native iOS/Android app?"
answer: "Yes, with caveats. Web Push via a PWA is viable for Android and desktop. iOS support is available from iOS 16.4+ but requires the user to add the app to their home screen first. For a community sports club audience, this is an acceptable constraint — but it must be communicated clearly during onboarding."
recommendation: proceed-with-pwa-push
confidence: medium
---

**TL;DR:** Web Push works on Android and desktop. iOS requires home screen installation (iOS 16.4+). For a club audience, this is acceptable. Proceed with PWA push notifications, but add a home screen prompt to the onboarding flow for iOS users.

---

## Answer

**Yes, with caveats.** Web Push via a PWA is viable for Fieldside's use case, but iOS support requires the user to add the app to their home screen. This is a one-time friction point that can be addressed in the onboarding flow.

---

## Evidence

### Browser Support

| Platform | Browser | Web Push Support | Notes |
|----------|---------|-----------------|-------|
| Android | Chrome | Full | Service Worker + Push API fully supported |
| Android | Firefox | Full | Supported |
| Android | Samsung Internet | Full | Supported |
| iOS 16.4+ | Safari | Partial | Requires "Add to Home Screen" — push not available in browser tab |
| iOS < 16.4 | Safari | None | Not supported |
| iOS | Chrome / Firefox | None | Third-party browsers on iOS cannot use push (WebKit restriction) |
| Desktop | Chrome, Firefox, Edge | Full | Fully supported |

**Key finding:** Approximately 85–90% of Android users will receive push notifications without any additional steps. iOS users on 16.4+ can receive push, but only after adding the app to their home screen. iOS users below 16.4 (estimated ~15% of iOS users as of early 2026) cannot receive push notifications at all.

### Reliability

Web Push delivery is handled by the browser vendor's push service (Google FCM for Chrome, Mozilla's service for Firefox, Apple's APNs for Safari). Delivery rates are generally comparable to native push for active users. The main reliability gap is that push subscriptions expire or become invalid when users clear browser data — this requires a re-subscription flow.

### Implementation Complexity

| Component | Effort | Notes |
|-----------|--------|-------|
| Service Worker registration | Low | ~1 day — standard boilerplate |
| Push subscription flow | Low-Medium | ~1–2 days — includes permission prompt UX |
| Server-side push sending | Low | ~0.5 days — `web-push` npm package handles this |
| iOS home screen prompt | Medium | ~1 day — requires detecting iOS and showing a custom prompt |
| Re-subscription handling | Medium | ~1 day — detect invalid subscriptions and re-prompt |
| **Total estimate** | **4.5–5.5 days** | Includes all components |

### Persona Perspectives

**Dr. Lena Petrova (Design Engineer):** "The service worker architecture is straightforward. The iOS home screen prompt is the UX challenge — we need to explain why they need to do this without making it feel like a bug. I'd recommend showing the prompt at the end of onboarding, not as a blocking step."

**Marcus Thorne (Senior Developer):** "The `web-push` library is well-maintained and handles VAPID key management. The main risk is subscription management at scale — we need a database table for push subscriptions and a job to clean up expired ones. Not complex, but it needs to be designed properly."

**Elias Vance (Client):** "My concern is the iOS user who adds the app to their home screen, then removes it three weeks later. Their push subscription becomes invalid and they stop receiving notifications — and they don't know why. We need a fallback (email or SMS) for users whose push subscription lapses. Don't ship push-only notifications."

---

## Recommendation

**Proceed with Web Push via PWA.** The coverage is sufficient for a community sports club audience (most members will be on Android or iOS 16.4+), and the implementation complexity is manageable within the existing sprint structure.

**Conditions on the recommendation:**

1. Add an iOS home screen prompt to the onboarding flow. It should appear after the member has completed onboarding and seen the squad list — after the emotional payoff, not before.
2. Always maintain a fallback notification channel (email). Push notifications are a convenience layer, not the primary communication channel.
3. Build subscription management (expiry detection and re-prompt) from the start, not as a follow-up. An expired subscription that silently fails is worse than no push at all.

**What we are NOT recommending:** Building a native iOS/Android app to solve the notification problem. The coverage gap on iOS is real but not large enough to justify the cost and complexity of a native app at this stage.

---

## What This Unblocks

Sprint 003 (Fixture Management) can now include fixture reminder notifications as a feature. The implementation estimate for the notification component is 4.5–5.5 days, which should be factored into the Sprint 003 scope.

---

## Raw Research

### Sources Consulted

- MDN Web Docs — Push API browser compatibility table (accessed 2026-03-02)
- Apple Developer Documentation — "Sending web push notifications in web apps and browsers" (iOS 16.4 release notes)
- `web-push` npm package documentation (v3.6.x)
- Can I Use — Web Push API coverage data

### iOS Version Distribution (Estimated, Early 2026)

Based on publicly available Apple device analytics:
- iOS 17+: ~65% of active iOS devices
- iOS 16.4–16.x: ~20% of active iOS devices
- iOS < 16.4: ~15% of active iOS devices

**Implication:** Approximately 85% of iOS users can receive Web Push if they add the app to their home screen. The 15% on older iOS versions cannot receive push at all — email fallback is essential for this group.

---

_Spike completed within the 4-hour time box. Recommendation is ready for review._
