# Command: /create-spike

## Purpose

Run a structured, time-boxed investigation to reduce excess uncertainty before committing to development. A spike produces knowledge, not features. It answers a specific question so that a decision can be made or a story can be estimated.

---

## Pre-Flight Checks

Before starting, read the following living documents:
- `research/DECISIONS.md`
- `research/sprint-status.md`
- `research/sprint-backlog.md` (if it exists)

Determine the next spike number from the spikes folder.

**Sprint Backlog Check:** If `research/sprint-backlog.md` exists and has spike candidates with `Status: Candidate`, present the top candidate(s) to the user and ask: "Your sprint backlog has a spike candidate ready: [topic]. Would you like to investigate this, or define a new spike?"

---

## Step 0 — The Spike Qualification Test

Before proceeding, run this three-question test to confirm that a spike is the right tool. If the answers don't qualify, suggest a regular task or story instead.

Present the following:

```
Before we start, let's confirm this is the right tool for the job.

A spike is for excess uncertainty — a genuine blocker to estimation or decision-making.
It is not for normal uncertainty, which is part of every development task.

Answer these three questions:

1. Can you confidently estimate the effort required to complete this work?
   (If YES → this is probably a regular task, not a spike.)

2. Is this uncertainty actively blocking a decision or a larger piece of work?
   (If NO → this may not be urgent enough for a spike.)

3. Is the primary goal to gain knowledge, not to ship a feature?
   (If NO → this is a feature, not a spike.)
```

**If the answers qualify (No / Yes / Yes):** Proceed to Step 1.
**If the answers don't qualify:** Respond with: "Based on your answers, this looks like a regular development task rather than a spike. A spike is specifically for excess uncertainty that blocks estimation or decision-making. I'd recommend creating a standard user story instead. Would you like to proceed as a spike anyway, or shall we reframe this as a task?"

---

## Step 1 — Input Mode

```
How do you want to provide context for this spike?

(A) Guided Wizard — I'll walk you through the Question Formulation Framework.
(B) Paste Content — Share notes, a Slack thread, or a brief and I'll extract the key inputs.
(C) Link — Provide a URL and I'll read it and extract the key inputs.
```

---

## Input Mode Behaviour

### Mode A — Guided Wizard (Question Formulation Framework)

Walk the user through this framework to build a precise, answerable spike question:

```
Step 1: We need to decide: [DECISION]
Step 2: We cannot decide because we don't know: [UNCERTAINTY]
Step 3: This spike will answer: [QUESTION — specific, testable, time-boxed]
Step 4: Once answered, we will be able to: [NEXT ACTION — what gets unblocked]
```

After the framework, collect:

**Spike Type:**
> "What type of spike is this?"
> - Technical (feasibility, architecture, integration)
> - Functional (how a feature should behave)
> - Design (visual direction, UX approach)
> - Research (user needs, market context)

**Acceptance Criteria (Knowledge Outcomes, NOT task lists):**
> "How will you know the spike is complete? Define knowledge outcomes, not deliverables."
> Examples:
> - "We will know whether [X] is technically feasible."
> - "We will have decided between [A] and [B]."
> - "We will have a [prototype / ADR / comparison matrix] showing [X]."

**Timebox:**
> "How long should this spike run? Default is 2 days. Suggest based on complexity."
> Rule: The timebox should be proportional to the uncertainty. If you can't answer the question in 2 days, the question is probably too broad — split it into two spikes.

**Constraints:**
> "What constraints apply? Tech stack, budget, compliance, team skills."

**Known Options:**
> "Are there specific options to compare (A vs. B), or should the spike discover the options?"

**What We Already Know:**
> "What prior decisions or ruled-out options are relevant? Don't re-investigate what's already settled."

**Expected Output Format:**
> "What format should the spike produce?"
> - ADR (Architecture Decision Record)
> - Comparison matrix
> - Proof-of-concept
> - Recommendation document
> - Benchmark report

**Consumer:**
> "Who needs this answer? What story, decision, or sprint is waiting on this spike?"

---

### Mode B — Paste Content

Accept raw, unstructured text. Extract:
- The core question
- The decision being blocked
- Any known options
- Constraints mentioned
- The consumer (what's waiting on this)

Present a structured summary and ask the user to confirm or correct.

---

### Mode C — Link

Fetch the URL. Apply the same extraction logic as Mode B. Fall back to Mode A if inaccessible.

---

## Step 2 — Persona Assignment

Based on the spike type, suggest the appropriate Project Squad personas from `.squad/project-squad.md`:

| Spike Type | Recommended Personas |
|---|---|
| Technical | Dr. Lena Petrova, Marcus Thorne, Kira Sharma |
| Functional | Dr. Lena Petrova, Dr. Aris Thorne, Kira Sharma |
| Design | Leo Finch, Rowan Vale, Dr. Lena Petrova |
| Research | Dr. Aris Thorne, Elias Vance |

Ask the user to confirm or adjust the selection.

---

## Step 3 — Investigation Phase

Each assigned persona contributes their investigation angle to the brief. Generate these perspectives in the persona's voice.

**Output:** Create `research/spikes/spike-NNN-[topic]/brief.md` using the following template:

```yaml
---
title: "Spike NNN: [Question]"
type: spike-brief
status: in-progress
date: YYYY-MM-DD
spike-type: technical | functional | design | research
timebox: "2 days"
question: "[The specific question this spike will answer.]"
consumer: "[Story or decision waiting on this answer.]"
personas: [lena, marcus, kira]
depends-on: []
feeds-into: []
tags: []
---

**TL;DR:** [One sentence: what question is this spike answering and why does it matter?]

---

## The Question

[The specific, testable question this spike will answer.]

## Why We Need to Know

We need to decide: [DECISION]
We cannot decide because: [UNCERTAINTY]
Once answered, we will be able to: [NEXT ACTION]

## Acceptance Criteria

- We will know whether [X].
- We will have decided between [A] and [B].
- We will have a [output format] showing [X].

## Timebox

[N days. Start: YYYY-MM-DD. End: YYYY-MM-DD.]

## Constraints

[List constraints.]

## Known Options

[List known options, or "Options to be discovered during investigation."]

## What We Already Know

[Prior decisions, ruled-out options, existing research.]

---

## Investigation Angles

### [Persona Name] — [Persona Role]
> "[Signature question]"

[Their investigation angle — what they will look at, what questions they will try to answer from their specific lens.]

### [Persona Name] — [Persona Role]
> "[Signature question]"

[Their investigation angle.]
```

---

## Step 4 — Spike Output (Answer-First Structure)

After the investigation is complete, produce the final output file. The answer must come first. Never bury the conclusion.

**Output:** Create `research/spikes/spike-NNN-[topic]/output.md` using the following template:

```yaml
---
title: "Spike NNN: [Question] — Output"
type: spike-output
status: complete
date: YYYY-MM-DD
spike-type: technical | functional | design | research
timebox: "2 days"
question: "[The specific question.]"
answer: "[One-sentence answer — yes/no/option chosen/recommendation.]"
confidence: high | medium | low
consumer: "[Story or decision that is now unblocked.]"
adr: "[Path to ADR if one was produced, or 'None'.]"
tags: []
---

**Answer:** [One sentence — the conclusion, stated directly.]

---

## Recommendation

[What should the team do next, based on this answer?]

## Evidence

[Comparison tables, benchmark data, proof-of-concept results. Use tables over prose.]

| Option | Pros | Cons | Verdict |
|--------|------|------|---------|
| [A] | ... | ... | [Chosen / Rejected] |
| [B] | ... | ... | [Chosen / Rejected] |

## Constraints Discovered

[Things we didn't know before the spike that the team needs to be aware of.]

## Decision

[The chosen option, stated in past tense. Link to ADR if produced.]

---

_Appendix: Raw Research_

[Full notes, links, and raw data below this line. This is the "stop reading here" signal for LLMs.]
```

**`summary.json` template:**

```json
{
  "type": "spike",
  "spike_id": "spike-NNN",
  "topic": "[Topic]",
  "spike_type": "technical | functional | design | research",
  "date_completed": "YYYY-MM-DD",
  "question": "[The specific question this spike answered.]",
  "answer": "[One-sentence answer.]",
  "confidence": "high | medium | low",
  "summary_of_findings": "[2-3 sentences summarising what was discovered.]",
  "adr_reference": "[Path to ADR, or 'None'.]",
  "unblocked_work": "[The story, decision, or sprint that is now unblocked.]",
  "constraints_discovered": [
    "[Constraint 1]"
  ],
  "squad_participants": [
    "Dr. Lena Petrova (Design Engineer)",
    "Marcus Thorne (Senior Developer)"
  ]
}
```

---

## Output Synthesis Rules

All spike output files must follow the same 10 rules as sprint outputs (see `create-sprint.md`). Key rules for spikes:

- **One question per spike.** If you have multiple questions, create multiple spikes.
- **Answer is always the first body section.** Never bury the conclusion.
- **Raw research goes below the `---` rule.** This is the "stop reading here" signal.
- **ADR reference is mandatory** if a significant technical decision was made.
- **`summary.json` is mandatory.** This is the machine-readable summary for future context.

---

## Verification Checklist

After completing the spike, verify:
- [ ] `brief.md` has YAML frontmatter + TL;DR within first 20 lines.
- [ ] `output.md` has the Answer as the first body section.
- [ ] `output.md` has raw research below a `---` horizontal rule.
- [ ] `summary.json` has been created and is valid JSON.
- [ ] `research/DECISIONS.md` has been updated if a decision was made.
- [ ] ADR has been created in `docs/decisions/` if a significant technical decision was made.
- [ ] The spike branch (if used) has NOT been merged to `main` or `dev`.
