---
title: "Fieldside — Project Context"
type: project-context
version: "1.0"
date: 2026-03-02
---

# Fieldside — Project Context

This file is read by `/init-project-squad` to pre-populate the living documents. It is the single source of truth for project-level context during setup.

---

## Project Overview

**Project name:** Fieldside
**One-line description:** A mobile-first web app for community sports clubs to manage memberships, fixtures, and communications.
**Primary goal:** Replace the patchwork of WhatsApp groups, spreadsheets, and paper sign-up sheets that most grassroots clubs currently use with a single, simple tool that works for both club admins and members.

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Next.js 14 (App Router), TypeScript, Tailwind CSS |
| Backend | Next.js API Routes |
| Database | PlanetScale (MySQL) via Drizzle ORM |
| CMS | Sanity v3 (for club news and announcements) |
| Auth | NextAuth.js |
| Hosting | Vercel |
| Package manager | pnpm |

**Key workflow note:** Always use `pnpm`, never `npm` or `yarn`.

---

## Known User Personas

### Persona 1: The Club Secretary

A volunteer who manages the club's admin — registrations, fixture scheduling, communications, and fee collection. Usually not technical. Has been doing this job for years and has strong opinions about what works. Deeply suspicious of new tools that create more work.

**Goal:** Spend less time on admin so they can focus on the club itself.
**Frustrations:** Chasing people for payments, manually updating fixture lists, answering the same questions over and over in WhatsApp.
**Key quote:** "I just need it to work. I don't have time to learn something complicated."

### Persona 2: The Active Member

A regular player who wants to know when training is, confirm their attendance, and pay their subs without hassle. Uses their phone for everything. Doesn't think about the club outside of match days.

**Goal:** Stay informed and organised with minimal effort.
**Frustrations:** Missing fixture updates buried in a long WhatsApp thread, not knowing if they've paid, having to ask the secretary for information they should be able to find themselves.
**Key quote:** "I just want to know when I'm playing and whether I owe anything."

### Persona 3: The Casual / Lapsed Member

Someone who used to play regularly but has drifted. Might come back if re-engagement is easy. Currently invisible to the club because there's no system to track them.

**Goal:** Low-friction way to re-engage when the time is right.
**Frustrations:** Feels awkward reaching out after a long absence. Doesn't know what's changed at the club.
**Key quote:** "I'd probably come back if someone just made it easy."

---

## Known Principles

- **Admin-first, member-second:** The secretary's experience is the primary constraint. If it creates admin work, it won't be adopted.
- **Mobile-first:** The vast majority of users will access the app on a phone. Desktop is secondary.
- **No onboarding friction:** Members should be able to join and see value within 60 seconds of first use.
- **Offline-tolerant:** Clubs often play in areas with poor signal. Core features must work or degrade gracefully without connectivity.

---

## Known Constraints

- Budget is minimal — no paid third-party services unless they are essential and cheap.
- The club secretary is the only person who will manage the system. It cannot require technical knowledge to operate.
- GDPR compliance is required — member data must be handled carefully.
- The MVP must be deployable within 8 weeks.

---

## Persona-to-Team Mapping (Optional)

| Squad Persona | Real Team Member | Review Responsibility |
|---------------|-----------------|----------------------|
| Leo Finch (Visual Designer) | — | Brand and UI review |
| Dr. Lena Petrova (Design Engineer) | — | Component and system review |
| Marcus Thorne (Senior Developer) | — | Architecture review |
| Kira Sharma (Developer) | — | Implementation review |
| Dr. Aris Thorne (Strategist) | — | Research and synthesis |
| Rowan Vale (Craftsman) | — | End-to-end experience |
| Elias Vance (Client) | — | Mandatory challenge |
