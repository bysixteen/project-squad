---
title: "Amazon DxD New Expression System — Project Context"
type: project-context
version: "1.0"
date: 2026-03-04
---

# Amazon DxD: New Expression System & Generative Design System Foundations

> This file is read by `/init-project-squad` to pre-populate your living documents.

---

## 1. Project Overview

**Project name:** Amazon DxD: New Expression System & Generative Design System Foundations

**One-line description:** A comprehensive evolution of Amazon's Device Experience Design (DxD) system that introduces a modern expression language, generative adaptive logic, and unified patterns for connected devices.

**Primary goal (the North Star):** Establish a scalable, intelligent design system that enables consistent, adaptive experiences across Amazon's expanding suite of connected devices while empowering generative and AI-driven design capabilities.

**What problem does this solve today?**
- Current DxD design system is mature but static — cannot adapt to device context, capability variance, or emerging use cases
- Design patterns are not flexible enough for the breadth of Amazon's device portfolio (from simple IoT to complex multi-surface experiences)
- Alexa integration across devices lacks a cohesive design framework
- No systematic approach to handling generative design logic at scale

**What is explicitly out of scope?**
- Individual product redesigns or feature implementations beyond the system itself
- Business model changes or commercial strategy
- Technical implementation or engineering architecture (design system + deliverables only)

---

## 2. The Users

**Persona 1: Design System Maintainers & Design Leads**
- **Role:** Design directors, system architects, senior product designers at Amazon
- **Goal:** Have a consistent, documented, and defensible system to scale design across 50+ device types and surfaces
- **Frustration:** Current system complexity grows faster than capability; difficult to enforce consistency without sacrificing flexibility
- **Key quote:** "We need patterns that work for everything from a watch to a smart home hub, but today we're managing different systems."

**Persona 2: Product Designers (Cross-Surface Teams)**
- **Role:** Designers working on specific devices or experiences (Alexa-enabled appliances, Echo devices, wearables, automotive)
- **Goal:** Quickly compose new experiences by combining proven patterns and tokens without reinventing the wheel
- **Frustration:** Current tokens and patterns are too prescriptive or too vague; no guidance on how to adapt for their specific device constraints
- **Key quote:** "I need templates and logic I can trust, and a way to know what's possible on my device."

**Persona 3: Engineers & Implementation Teams**
- **Role:** Engineers translating design system into code across multiple platforms (iOS, Android, web, embedded)
- **Goal:** Have clear, machine-readable specs for tokens, adaptive behaviors, and Alexa integration
- **Frustration:** Designs don't always account for technical constraints; generative logic isn't documented in a way that's implementable
- **Key quote:** "I need to know the rules — when does this pattern adapt? What are the decision trees?"

---

## 3. Design Principles

**Design Principles**
- **Clarity & Recognizability** — The new expression system must feel distinctly Amazon while remaining flexible across device contexts
- **Scalability** — Patterns should work for 1-surface and 50-surface experiences
- **Generativity** — The system should enable machines to compose new experiences, not just document existing ones
- **Accessibility First** — Every pattern must be accessible by default (WCAG AA+)
- **Context Awareness** — Design must adapt to device capability, screen size, input modality, and user context

**Technical Principles**
- **Token-Driven** — All visual and behavioral decisions flow from a single source of truth (tokens)
- **Composability** — Patterns combine to create experiences; patterns don't dictate entire workflows
- **Multi-Surface Consistency** — Same intent, different implementation (Alexa embedded in a smart fridge looks different than Alexa on a screen)
- **Continuous Prototyping** — Design is validated in real device contexts every sprint
- **Explainability** — Design decisions and adaptive logic are documented and defensible

---

## 4. Known Decisions

| Decision | Date | Rationale | Rejected Alternative |
|----------|------|-----------|----------------------|
| 3-month timeline with continuous prototyping | RFP-defined | Time-boxed exploration reduces scope creep; prototyping each phase validates feasibility | Longer exploration phase; full build-out of all surfaces |
| Alexa Agent Embedment as core track | RFP-defined | Alexa is the differentiator across Amazon's device ecosystem; must be a first-class system concern | Treat Alexa integration as secondary feature |
| Multi-surface prototype suite (desktop, mobile, web, + capability-aware variants) | RFP-defined | Covers breadth of device contexts; capability-aware variants test generative logic | Single-surface prototype |

---

## 5. Tech Stack

| Layer | Choice | Notes |
|-------|--------|-------|
| Design System Tooling | [TBD — design tool(s) for system authoring] | Figma, Penpot, or bespoke tool? |
| Token Format | [TBD — JSON/YAML/CSS Variables?] | Need to support design tools, code, and generative logic |
| Documentation | [TBD — design system site] | Internal wiki, Storybook-style, or custom platform? |
| Prototyping Platforms | iOS, Android, Web | For continuous prototyping track (required) |
| Generative Logic Engine | [TBD — rules engine, AI model, or hybrid?] | How does the system generate new compositions? |

---

## 6. Open Questions (Sprint Backlog Seeds)

**System Architecture**
- How does the generative & adaptive logic actually work? Is it rule-based, ML-based, or hybrid?
- What's the decision tree for when and how patterns adapt across device contexts?
- How do we handle conflicts between accessibility, aesthetics, and device constraints?

**Scope & Prioritization**
- Which device categories are in "phase 1" vs. "future"? (e.g., smart speakers, displays, wearables, appliances, automotive)
- What's the MVP for Alexa Agent Embedment? Is it a visual language, interaction model, or both?
- How much of the current DxD system is carried forward vs. redesigned?

**Design Validation**
- What does "continuous prototyping" look like operationally? Which devices/surfaces get prototyped each sprint?
- How will we validate generative logic — through user testing, stakeholder review, or algorithmic validation?

**Handoff & Implementation**
- Who owns implementation after sprint? How prescriptive should the system be for engineers?
- How will the system evolve post-launch? Is there a governance model?

---

## 7. Constraints

**Timeline:** 3 months (with prototyping every phase)

**Budget:** [TBD — see Partner Requirements section]

**Regulatory / compliance:** Accessibility (WCAG AA+ minimum); may have data privacy implications for Alexa integration

**Team:**
- Partner should have senior creative leadership, system design expertise, multi-surface prototyping depth
- Continuous collaboration with Amazon stakeholders expected

**Existing systems:**
- Building on current DxD system (not a greenfield redesign)
- Must integrate with Alexa platform and ecosystem
- Must account for 50+ existing device types

---

## 8. Deliverables

From the RFP:
- **New Expression System** (evolved from internal seeds)
- **System Foundations** — tokens, templates, patterns, motion primitives
- **Generative & Adaptive Behavior Model**
- **High-Fidelity Prototype Suite** (desktop/mobile/web + capability-aware variants)
- **Alexa Agent Embodiment Framework**
- **Leadership Vision Decks**
- **Documentation for designers and engineers**
- **Capability-aware feedback guidance**
- **Blueprint for DDS systemization** (Design Decision System)

---

## 9. Notes

- This RFP is from Amazon's internal design leadership; the partner (you/your org) is being engaged to design the system, not implement it
- "Continuous Prototyping" is a required track — design will be tested in real device contexts each month
- The system must feel evolutionary (not revolutionary) to avoid disrupting existing teams using DxD
- Alexa Agent is a major differentiator for Amazon; its integration into the system is not cosmetic but foundational
- The team will need deep experience with design systems at scale, multi-platform constraints, and generative/adaptive design thinking
