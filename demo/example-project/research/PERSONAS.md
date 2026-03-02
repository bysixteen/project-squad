# Fieldside — User Personas

**Last updated:** 2026-03-02 — Sprint 000 (Foundation)
**Next review:** Sprint 002

> **Note:** These are Fieldside's *user* personas — the real people who will use the product. They are distinct from the Project Squad personas (the seven archetypes in `.squad/project-squad.md`).

---

## Persona 1: The Club Secretary

**Role:** Volunteer club administrator
**Goal:** Spend less time on admin so they can focus on the club itself — the people, the sport, and the community.
**Frustrations:** Chasing people for payments via WhatsApp. Manually updating fixture lists in a spreadsheet and then re-posting them in three different places. Answering the same questions over and over ("When's training?" "Have I paid my subs?"). Being the single point of failure for all club information.
**Key Quote:** "I just need it to work. I don't have time to learn something complicated."

**Design implication:** Every admin-facing feature must be operable by someone with no technical background. If it requires a manual step, it will be forgotten. Automation is the primary lever for reducing secretary burden.

---

## Persona 2: The Active Member

**Role:** Regular player, attends most training sessions and matches
**Goal:** Stay informed and organised with minimal effort. Know when training is, confirm attendance, pay subs — all without having to ask anyone.
**Frustrations:** Missing fixture updates buried in a 200-message WhatsApp thread. Not knowing whether they've paid their subs for the season. Having to message the secretary for information that should be self-service.
**Key Quote:** "I just want to know when I'm playing and whether I owe anything."

**Design implication:** The member-facing experience must surface the three most important pieces of information immediately on login: next fixture, attendance status, and payment status. Everything else is secondary.

---

## Persona 3: The Casual / Lapsed Member

**Role:** Former regular who has drifted away from the club
**Goal:** Low-friction way to re-engage when the time is right. Does not want to make a big commitment — just wants to dip a toe back in.
**Frustrations:** Feels awkward reaching out after a long absence. Doesn't know what's changed at the club, who's still there, or whether they'd be welcome back. The barrier to re-engagement feels higher than it actually is.
**Key Quote:** "I'd probably come back if someone just made it easy."

**Design implication:** The re-engagement flow must be passive and non-committal. A lapsed member should be able to see upcoming fixtures and the current squad without logging in. The ask to re-join should come after they've seen something worth coming back for.
