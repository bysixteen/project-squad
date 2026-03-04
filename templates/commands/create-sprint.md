# Command: /create-sprint

## Purpose

Run a structured design sprint using the Project Squad framework. Guides the user through problem definition, persona selection, and the four sprint phases, producing synthesis-friendly outputs that don't burn context.

---

## Pre-Flight Checks

Before starting, read the following living documents to establish project context:
- `research/PRINCIPLES.md`
- `research/PERSONAS.md`
- `research/DECISIONS.md`
- `research/sprint-status.md`
- `research/sprint-backlog.md` (if it exists)
- `research/dissent-register.md` (if it exists)

Determine the next sprint number from `sprint-status.md`. If the file is empty or missing, this is Sprint 001.

**Sprint Backlog Check:** If `research/sprint-backlog.md` exists and has candidates with `Status: Candidate`, present the top candidate(s) to the user and ask: "Your sprint backlog has a candidate ready: [topic]. Would you like to run this sprint, or define a new one?"

**Dissent Register Scan:** If `research/dissent-register.md` exists, scan the `Review Trigger` column for any entries whose trigger is relevant to the upcoming sprint's topic. If any are found, surface them before Step 0: "Before we start — the dissent register has a flagged concern that may be relevant to this sprint: [dissenting view] (raised in [sprint/spike], Review Trigger: [trigger]). Do you want to factor this in?"

---

## Step 0 — Input Mode & Team Selection

Present the following to the user:

```
Welcome to /create-sprint.

Before we begin, I need to understand the challenge.

1. What's the challenge? (One sentence — a problem to solve, not a solution to build.)

2. How do you want to provide context?
   (A) Guided Wizard — I'll ask you structured questions step by step.
   (B) Paste Content — Share a doc, brief, notes, or Slack thread and I'll extract the key inputs.
   (C) Link — Provide a URL and I'll read it and extract the key inputs.

3. Sprint format?
   (Full) Four phases: Map → Sketch → Decide → Synthesise
   (Lite) Two phases: Map → Decide (faster, for lower-stakes decisions)
   (Workshop) Single session, all phases compressed

4. Which Project Squad personas are joining this sprint?
   [Display the team selection guide from .squad/project-squad.md and recommend personas based on the challenge type.]
```

---

## Input Mode Behaviour

### Mode A — Guided Wizard (Knapp's Monday Questions)

Walk the user through these questions in order. Do not rush. Each question builds on the last.

**Question 1 — The Long-Term Goal (Optimistic)**
> "Fast forward 6 to 12 months. If this project is a wild success, what will be different? Describe it in the present tense, as if it has already happened."

*Why this matters:* This establishes the North Star. It forces the team to think beyond the immediate feature and align on the ultimate purpose of the work. A strong goal is ambitious, measurable, and inspiring.
*Good input:* "Our members manage their entire relationship with the club through a single, intuitive app, and admin overhead has dropped by 50%."
*Bad input:* "We will have launched the new feature."

**Question 2 — The Sprint Questions (Pessimistic)**
> "Now let's be pessimistic. On the path to that long-term goal, what could go wrong? What assumptions are we making that might be false? What obstacles will we face?"

*After the user responds:* Reframe each concern as a testable sprint question using the format "Can we...?" or "Will users...?" Present the reframed questions and ask the user to confirm or adjust.
*Test for each question:* "Can this question be answered through user testing or a prototype within the sprint timeframe?" If not, it is too broad.

**Question 3 — The Map and Target**
> "Let's map the user's journey. Who are the key actors, and what are the steps from their first interaction to the long-term goal? Walk me through it."

*After the user describes the journey:* Produce a simple text-based map. Then ask:
> "Looking at this map, where is the single most critical moment? Which part is the riskiest, or offers the biggest opportunity? That will be the target for this sprint."

**Question 4 — Target User**
> "Which of the user personas in PERSONAS.md is the primary user for this sprint? Or describe the user if they're not in the file yet."

**Question 5 — Constraints**
> "What constraints should the squad be aware of? Consider: technical limitations, budget, timeline, regulatory requirements, or things that are explicitly out of scope."

**Question 6 — Known Data and Assumptions**
> "What do we already know? What existing research, analytics, or prior decisions are relevant? What assumptions are we making that we haven't validated yet?"

---

### Mode B — Paste Content

Accept raw, unstructured text from the user. Extract the following fields:
- Challenge statement
- Any goals or success criteria mentioned
- Constraints mentioned
- Named users or personas
- Any existing decisions or context

Present a structured summary: "Here's what I found:" with each field listed. Ask the user to confirm or correct. Ask for anything missing. Be forgiving of messy, informal input.

---

### Mode C — Link

Fetch the URL provided. Apply the same extraction logic as Mode B. Fall back to Mode A if the URL is inaccessible or returns insufficient content.

---

## Phase 1 — Map (Led by Dr. Aris Thorne)

**Persona voice:** Aris leads this phase. He is looking for the real problem beneath the stated problem.

Generate 5–10 "How Might We" (HMW) questions from the challenge and the inputs collected in Step 0. Present them to the user for curation. Ask the user to select the 3–5 most important ones.

**Output:** Create `research/sprints/sprint-NNN-[topic]/brief.md` using the following template:

```yaml
---
title: "Sprint NNN: [Topic]"
type: sprint-brief
status: in-progress
date: YYYY-MM-DD
sprint: NNN
personas: [leo, lena, marcus, kira, aris, rowan, elias]
depends-on: []
feeds-into: []
tags: []
---

**TL;DR:** [One sentence: what is this sprint trying to answer?]

---

## Sprint Challenge

[The one-sentence problem statement.]

## Long-Term Goal

[The optimistic 6–12 month vision, present tense.]

## Sprint Questions

1. [Can we...?]
2. [Will users...?]
3. [Can we...?]

## Target User

[Name from PERSONAS.md, or description.]

## Target Moment on the Map

[The single most critical moment identified in the Map phase.]

## Project Squad

| Persona | Name | Role in This Sprint |
|---------|------|---------------------|
| Visual Designer | Leo Finch | Sketch phase |
| Design Engineer | Dr. Lena Petrova | Map + Sketch |
| Senior Developer | Marcus Thorne | Sketch + Decide |
| Developer | Kira Sharma | Sketch |
| Strategist | Dr. Aris Thorne | Map lead + Synthesise |
| Craftsman | Rowan Vale | Sketch |
| Client | Elias Vance | Decide (mandatory) |

## How Might We Questions

1. HMW [...]
2. HMW [...]
3. HMW [...]

## Constraints

[List constraints from Step 0.]

## Known Data and Assumptions

[List known data and unvalidated assumptions from Step 0.]
```

---

## Phase 2 — Sketch (Lightning Docs)

Each selected persona writes a ~150-word perspective **in their own voice**, using their signature question as the lens. Generate all perspectives. Present them to the user and ask if they want to adjust any before proceeding to the Decide phase.

**Output:** Create `research/sprints/sprint-NNN-[topic]/sketches.md` using the following template:

```markdown
---
title: "Sprint NNN: Sketches"
type: sprint-sketches
status: complete
date: YYYY-MM-DD
sprint: NNN
---

## Leo Finch — Visual Designer
> "Does this feel like us?"

[Brand and visual angle. How does this strengthen or threaten the brand identity? What visual direction would make this feel authentic?]

---

## Dr. Lena Petrova — Design Engineer
> "How will we build, test, and maintain this?"

[Design system and build feasibility. Which components exist? What needs to be created? What is the maintenance overhead?]

---

## Marcus Thorne — Senior Developer
> "What are we NOT building here?"

[Architectural angle. What is explicitly out of scope? What long-term risks does this introduce? What decisions will be hard to reverse?]

---

## Kira Sharma — Developer
> "What does the implementation actually look like?"

[Build reality. What are the code paths? What integrations are required? What is the realistic effort estimate?]

---

## Dr. Aris Thorne — Strategist
> "What is the real problem we are trying to solve?"

[Research and user angle. Does this solution address the root cause? What does the evidence say? Is there a simpler solution we're overlooking?]

---

## Rowan Vale — Craftsman
> "What is the feeling we want to create?"

[End-to-end experience. What happens before and after the screen? What is the emotional arc of the user's journey? What touchpoints are we missing?]

---

## Elias Vance — Client (Mandatory Dissent)
> "Does this solve a real problem for my users?"

[Reality check. What assumption is this solution making? What is the strongest argument against proceeding? Steelman the alternative.]
```

---

## Phase 3 — Decide

Present the options from the Sketch phase. Facilitate the decision. Record Elias Vance's dissent, even if the team overrules him.

If the dissent is significant, add it to `research/dissent-register.md`.

**Output:** Create `research/sprints/sprint-NNN-[topic]/decision.md` using the following template:

```yaml
---
title: "Sprint NNN: Decision"
type: sprint-decision
status: complete
date: YYYY-MM-DD
sprint: NNN
decision: "[One sentence — the chosen direction, past tense.]"
---

## Decision

[One paragraph — the chosen direction and the primary reason for choosing it. Answer first, rationale second.]

## Rationale

[Why this option over the alternatives? What evidence or reasoning was decisive?]

## Elias Vance's Dissent

[Record Elias's challenge, even if overruled. If he agreed, state that explicitly: "Elias agreed with the decision."]

## What We Are NOT Doing

[Explicitly list the options that were considered and rejected, and why.]

## Next Action

[The single most important next step to take after this sprint.]
```

---

## Phase 4 — Synthesise (Led by Dr. Aris Thorne)

Auto-update the following living documents:
- `research/DECISIONS.md` — Add the decision with a link to `decision.md`.
- `research/sprint-status.md` — Update the sprint row to "Complete" and add participating personas.
- `research/PERSONAS.md` — Update if the sprint revealed new insights about user personas.
- `research/PRINCIPLES.md` — Update if the sprint established new design or technical principles.

**Output:** Create `research/sprints/sprint-NNN-[topic]/synthesis.md` and `research/sprints/sprint-NNN-[topic]/summary.json`.

**`synthesis.md` template:**

```yaml
---
title: "Sprint NNN: Synthesis"
type: sprint-synthesis
status: complete
date: YYYY-MM-DD
sprint: NNN
---

**TL;DR:** [One sentence: what did this sprint decide and what happens next?]

---

## What Changed

[What living documents were updated and why?]

## What the Next Sprint Should Know

1. [Key insight 1]
2. [Key insight 2]
3. [Key insight 3]

## Open Questions

[Questions that emerged from this sprint but were not answered. Candidates for future spikes.]

---

_Appendix: Full sprint folder at `research/sprints/sprint-NNN-[topic]/`_
```

**`summary.json` template:**

```json
{
  "type": "sprint",
  "sprint_id": "sprint-NNN",
  "topic": "[Topic]",
  "date_completed": "YYYY-MM-DD",
  "long_term_goal": "[The long-term goal from the brief.]",
  "sprint_questions": [
    "[Sprint question 1]",
    "[Sprint question 2]"
  ],
  "key_question_answered": "[The most important sprint question and whether it was answered.]",
  "key_decision": "[One sentence — the decision made.]",
  "squad_participants": [
    "Leo Finch (Visual Designer)",
    "Dr. Lena Petrova (Design Engineer)"
  ],
  "elias_dissent": "[Elias's dissent, or 'None — Elias agreed with the decision.']",
  "living_docs_updated": [
    "research/DECISIONS.md",
    "research/sprint-status.md"
  ],
  "next_action": "[The single most important next step.]",
  "open_questions": [
    "[Open question 1]"
  ]
}
```

---

## Output Synthesis Rules (Applied to All Files)

All sprint output files must follow these 10 rules:

1. **YAML frontmatter is mandatory** — type, status, date, sprint, tags.
2. **TL;DR or Decision is always the first body section** — never bury the conclusion.
3. **Tables over prose** for structured data (reduces token count by ~30%).
4. **Appendices below a `---` horizontal rule** — clear "stop reading here" signal.
5. **Explicit null values** — "Blockers: None" not an omitted section.
6. **Past tense for decisions** — signals finality.
7. **ADR references inline** — every significant decision links to its record.
8. **Bidirectional links** — in frontmatter (`feeds-into`, `depends-on`) and body.
9. **One sprint question per sprint** — if multiple, rank them.
10. **< 700 lines per file** — if longer, split into multi-file progressive disclosure.

### The "First 20 Lines" Rule

Design every output so an LLM reading only the first 20 lines can determine relevance, extract the key decision, and know where to find detail. YAML frontmatter + TL;DR block must fit within 20 lines.

---

## Verification Checklist

After completing the sprint, verify:
- [ ] `brief.md` has YAML frontmatter + TL;DR within first 20 lines.
- [ ] `sketches.md` has all selected personas represented in their own voice.
- [ ] `decision.md` has Elias Vance's dissent recorded.
- [ ] `synthesis.md` has been created.
- [ ] `summary.json` has been created and is valid JSON.
- [ ] `research/DECISIONS.md` has been updated.
- [ ] `research/sprint-status.md` has been updated with participating personas.
- [ ] `research/dissent-register.md` has been updated if dissent was significant.
