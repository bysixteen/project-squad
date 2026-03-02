# Fieldside — Design & Technical Principles

**Last updated:** 2026-03-02 — Sprint 000 (Foundation)
**Next review:** Sprint 002

This document captures the core principles that guide design and technical decisions on this project. It is a living document, updated at the end of each sprint.

---

## Design Principles

**Admin-first, member-second.** The club secretary's experience is the primary constraint on every design decision. If a feature creates admin overhead, it will not be adopted, regardless of how good it is for members. Every new feature must be evaluated from the secretary's perspective first.

**Mobile-first.** The vast majority of users will access Fieldside on a phone. All UI decisions start from the smallest screen. Desktop is a secondary consideration and should degrade gracefully, not the other way around.

**No onboarding friction.** A new member should be able to join a club and see value within 60 seconds of first use. Any flow that requires more than three steps to complete is a candidate for simplification.

**Offline-tolerant.** Community clubs often play in areas with poor mobile signal. Core features — viewing fixtures, checking membership status, seeing the squad list — must work or degrade gracefully without connectivity. This is a hard constraint, not a nice-to-have.

---

## Technical Principles

**pnpm only.** Never use `npm` or `yarn`. This is a hard rule to ensure consistent lockfile behaviour across the team.

**No new dependencies without a spike.** Before adding any new package or third-party service, run a spike to evaluate the trade-offs. The cost of a dependency is not just its bundle size — it is the maintenance burden, the upgrade path, and the risk of abandonment.

**GDPR by default.** Member data is sensitive. Any feature that collects, stores, or processes personal data must be reviewed for GDPR compliance before it ships. When in doubt, collect less.

**Drizzle for all database access.** No raw SQL queries in application code. All database interactions go through Drizzle ORM to ensure type safety and consistent query patterns.

---

## What "Good" Looks Like on This Project

A well-executed piece of work on Fieldside is one that a non-technical club secretary can use without reading any documentation, that works reliably on a mid-range Android phone on a 3G connection, and that does not create any new admin tasks for the person running the club. If it passes those three tests, it is good.
