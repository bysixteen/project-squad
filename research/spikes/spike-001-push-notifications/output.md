---
title: "Spike 001 · Push Notifications — Output"
type: spike-output
status: complete
date: 2026-02-10
spike: "S-001"
confidence: medium
depends-on: ["sprint-001-onboarding"]
feeds-into: ["sprint-002-fixture-management"]
adr: "docs/decisions/002-push-notifications.md"
---

**Answer:** Yes, with caveats. Web Push via a PWA is viable for Android and desktop. iOS 16.4+ requires home screen installation. ~85% coverage achievable. Email fallback is mandatory.

**Recommendation:** Proceed with PWA Web Push. Build with three conditions (see below). Do not ship push-only notifications — email must always be sent in parallel.

**Confidence:** Medium — the technology is proven, but the iOS home screen prompt conversion rate is unknown for this user demographic.

---

## Recommendation

Proceed with PWA Web Push notifications. The approach covers approximately 85% of the Fieldside user base:

- Android (all modern versions): Full Web Push support without home screen installation
- Desktop (Chrome, Firefox, Edge): Full Web Push support
- iOS 16.4+: Web Push supported if the app has been added to the home screen
- iOS < 16.4: No Web Push support — email only

**Three conditions on the recommendation:**

1. **Add the iOS home screen prompt to the onboarding flow — after the member has seen the squad list (the emotional payoff), not before.** Prompting before they've seen value will result in instant dismissal.

2. **Always maintain a fallback notification channel (email). Push notifications are a convenience layer, not the primary communication channel.** Every push notification must have an email equivalent that sends regardless of push subscription status.

3. **Build subscription expiry detection and re-prompt from the start.** An expired subscription that silently fails is worse than no push at all. When a push fails with a `410 Gone` response, mark the subscription as expired and prompt re-subscription on the member's next login.

---

## Evidence

### Android Coverage
Web Push via Service Worker is fully supported on Chrome Android (all modern versions), Samsung Internet, and Firefox Android without any home screen installation requirement. No user action needed beyond granting notification permission.

### Desktop Coverage
Chrome, Firefox, and Edge all support Web Push. Safari on macOS 13+ added support in 2023.

### iOS Coverage
- **iOS < 16.4:** No PWA push notification support. ~15% of club members (Dave's demographic) likely on iOS 15 or earlier.
- **iOS 16.4+:** PWA push supported, but **only if the app has been added to the home screen**. Safari web pages (non-installed PWA) cannot receive push notifications even on iOS 16.4+.
- **Practical implication:** An iOS user who visits the site in Safari without adding it to the home screen will never receive push notifications, regardless of iOS version.

### Implementation Effort (Next.js)
- Service worker setup: 0.5 days (using `next-pwa` or manual service worker)
- Push subscription flow (VAPID keys, subscription endpoint storage): 1 day
- Push sending endpoint (server action): 0.5 days
- iOS home screen prompt component: 0.5 days
- Subscription expiry handling: 0.5 days
- **Total: 3–3.5 days**

Email fallback (already partially in scope for notifications generally) adds ~0.5 days.

**Total estimate: 3.5–4 days including email fallback.**

---

## Elias Vance — Spike Perspective

> "My concern is the iOS user who adds the app to their home screen, then removes it three weeks later. Their push subscription becomes invalid and they stop receiving notifications — and they don't know why. We need a fallback (email or SMS) for users whose push subscription lapses. Don't ship push-only notifications."

Note: Elias's concern became **Condition 02** on the recommendation — not a dissent, but a condition. This is the difference between a challenge that changes the outcome and one that is overruled.

---

## Platform Support Table

| Platform | Browser | Web Push | Requires Home Screen | Notes |
|---|---|---|---|---|
| Android | Chrome | Full | No | Fully supported |
| Android | Firefox | Full | No | Fully supported |
| iOS 16.4+ | Safari (installed PWA) | Full | Yes | Must be on home screen |
| iOS < 16.4 | Any | None | N/A | Email only |
| Desktop | Chrome | Full | No | Fully supported |
| Desktop | Firefox | Full | No | Fully supported |
| Desktop | Edge | Full | No | Fully supported |

---

## Impact on Sprint 002

Sprint 002 (Fixture Management) can proceed on the basis that:
- Push notifications will work for Android members and iOS members who install the PWA
- Email notifications will work for all members
- The fixture notification flow should trigger both push + email in parallel
- iOS home screen prompt is Sprint 002 scope (onboarding flow addition)

This spike unblocks Sprint 002. The fixture management sprint can begin.

---

*Raw research notes and browser specification references are below the stop line. The recommendation and evidence above are what matters.*

---

## Raw Research Notes

### Web Push API — MDN
The Push API and Notifications API together enable Web Push. A service worker is required to receive push events when the app is not open. The service worker handles the `push` event and calls `self.registration.showNotification()`.

### VAPID (Voluntary Application Server Identification)
VAPID keys identify the application server to the push service. They are required by all modern push services. Generated once and stored as environment variables (`NEXT_PUBLIC_VAPID_PUBLIC_KEY`, `VAPID_PRIVATE_KEY`).

### iOS Home Screen Requirement (Source: Apple developer docs, 2023)
"Web Push is available for web apps added to the Home Screen on iOS 16.4 and iPadOS 16.4 and later." Web pages in Safari, even on iOS 16.4+, cannot receive push notifications. The distinction is between a web app (added to home screen) and a web page (open in Safari).

### Subscription Expiry
Push subscriptions expire or become invalid when:
- The user revokes notification permission
- The user removes the PWA from their home screen (iOS)
- The browser clears site data
- The push service returns a `410 Gone` or `404 Not Found` response

All push sending code must handle these responses and mark the subscription as expired in the database.
