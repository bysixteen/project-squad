# /create-workshop

**Purpose:** Run a compressed, time-boxed design sprint when a decision is needed quickly and the full sprint format is not appropriate.

**Time:** 2–3 hours (vs. half-day for a Full Sprint)

**Output:** A `workshop.md` synthesis document and `summary.json` — same machine-readable format as a sprint, compatible with all pre-flight checks.

---

## Workshop vs. Sprint — When to use which

| Situation | Use |
|---|---|
| High-stakes decision, complex solution space, first time exploring this territory | `/create-sprint` (Full) |
| Lower-stakes refinement, constrained solution space, team already aligned on direction | `/create-sprint` (Lite) |
| **Time pressure, alignment needed fast, decision partially formed, stakeholder deadline** | `/create-workshop` |
| Specific technical unknown blocking progress | `/create-spike` |

**The Workshop Trigger Conditions.** Use `/create-workshop` when at least two of the following are true:

1. A decision is needed within 24–48 hours.
2. The team already has a leading option — the workshop is to stress-test it, not discover it.
3. A stakeholder, client, or deadline is forcing a decision before a full sprint is practical.
4. The question is well-defined but the team has not formally aligned on the answer.
5. A previous sprint's synthesis raised a follow-up question that needs a quick answer.

**Do not use `/create-workshop` to shortcut a genuinely complex problem.** If you cannot articulate the decision in one sentence, run a full sprint instead.

---

## Pre-flight Check

Before running the workshop, read:

1. `research/PERSONAS.md` — who are we designing for?
2. `research/PRINCIPLES.md` — what constraints apply?
3. `research/DECISIONS.md` — what has already been decided that is relevant?
4. `research/dissent-register.md` — are there any overruled concerns with a review trigger that matches this topic?
5. `research/sprint-backlog.md` — is this workshop addressing a backlog candidate?

Report a one-paragraph context summary to the user before proceeding.

---

## Step 1 — Define the Decision

A workshop has one job: produce a decision. Ask the user:

> "What is the one decision this workshop needs to produce?"

The answer must be a binary or multiple-choice decision, not an open-ended question. If it is open-ended, suggest a full sprint instead.

**Good workshop decisions:**
- "Should we use Option A or Option B for [feature]?"
- "Do we proceed with [approach] or pause for more research?"
- "Which of these three designs do we move forward with?"

**Not a workshop decision (run a sprint instead):**
- "How should we approach [feature]?"
- "What should [feature] look like?"

Once confirmed, record:

```yaml
decision_question: "[The decision, phrased as a question with a finite answer set]"
options: ["[Option A]", "[Option B]", "[Option C if applicable]"]
deadline: "YYYY-MM-DD"
trigger: "[Which trigger condition(s) applied — see above]"
```

---

## Step 2 — Compressed Map (15 minutes)

Skip the full journey map. Instead, answer three questions only:

1. **Who is affected?** (Reference `PERSONAS.md` — name the primary persona.)
2. **What is the moment?** (The specific user moment this decision affects.)
3. **What is the risk of getting it wrong?** (One sentence — what breaks if we choose badly?)

Output these three answers as a `## Context` block in the workshop document.

---

## Step 3 — Rapid Perspectives (30 minutes)

Assign three to four personas from the core squad. In a workshop, you do not need all seven. Recommended selection:

| Always include | Include if relevant |
|---|---|
| Elias Vance (Mandatory Dissent) | Leo Finch (if visual/brand decision) |
| Dr. Aris Thorne (strategic framing) | Dr. Lena Petrova (if technical decision) |
| Marcus Thorne (scope/constraints) | Kira Sharma (if implementation detail) |

For each assigned persona, generate a **single paragraph** in their voice. No sketches. No extended exploration. Just their immediate reaction to the decision question and the options on the table.

**Format:**

```markdown
### [Persona Name] — [Role]
> "[Signature question]"

[One paragraph — their position on the decision, in their voice.]
```

---

## Step 4 — Decide (15 minutes)

Present the options with the persona perspectives alongside them. Ask the user:

> "Based on these perspectives, which option do you want to proceed with?"

If the user is undecided, ask Elias Vance to cast the deciding question:

> "Elias asks: 'Which of these options most directly solves the problem for [primary persona]?' Does that change your view?"

Record the decision. If Elias's perspective was overruled, log it in `research/dissent-register.md` with a review trigger.

---

## Step 5 — Synthesise

**Output:** Create `research/sprints/workshop-NNN-[topic]/workshop.md` using the following template:

```yaml
---
title: "Workshop NNN: [Decision Question]"
type: workshop
status: complete
date: YYYY-MM-DD
decision_question: "[The decision question]"
decision: "[The chosen option — one sentence, past tense]"
options_considered: ["[Option A]", "[Option B]"]
trigger: "[Workshop trigger condition(s)]"
personas: [aris, marcus, elias]
feeds-into: []
depends-on: []
tags: []
---

**TL;DR:** [One sentence: what was decided and why.]

---

## Context

**Who is affected:** [Primary persona name and one-sentence description]
**The moment:** [The specific user moment this decision affects]
**Risk of getting it wrong:** [One sentence]

## Decision

**We chose:** [Option chosen]

**Rationale:** [2–3 sentences — why this option, what made it the right call]

**Rejected:** [Option(s) not chosen and the one-line reason for each]

## Persona Perspectives

### [Persona Name] — [Role]
> "[Signature question]"

[Their paragraph]

### [Persona Name] — [Role]
> "[Signature question]"

[Their paragraph]

### Elias Vance — Client (External) ⚠️ MANDATORY DISSENT
> "Does this solve a real problem for my users?"

[His paragraph — even if aligned, he must articulate why the chosen option serves the user]

## Conditions and Risks

[Any conditions on the decision — "This holds unless X". Any risks to monitor.]

## Next Action

[What happens next as a result of this decision.]
```

**`summary.json` template:**

```json
{
  "type": "workshop",
  "workshop_id": "workshop-NNN",
  "topic": "[Topic]",
  "date_completed": "YYYY-MM-DD",
  "decision_question": "[The decision question]",
  "decision": "[The chosen option — one sentence]",
  "options_considered": ["[Option A]", "[Option B]"],
  "trigger": "[Workshop trigger condition(s)]",
  "rationale": "[2–3 sentence rationale]",
  "elias_dissent": "[Elias's position — 'Aligned' or summary of concern]",
  "dissent_logged": true,
  "next_action": "[What happens next]",
  "squad_participants": [
    "Dr. Aris Thorne (Strategist)",
    "Marcus Thorne (Senior Developer)",
    "Elias Vance (Client)"
  ]
}
```

---

## Output Synthesis Rules

Workshop outputs follow the same 10 rules as sprint and spike outputs. Key rules:

- **TL;DR is always the first body section.**
- **Decision is stated in past tense** — signals finality.
- **Elias Vance must always appear**, even in a compressed format.
- **`summary.json` is mandatory** — future sprint pre-flights read this.
- **If a significant technical decision was made**, create an ADR in `docs/decisions/`.

---

## Verification Checklist

After completing the workshop, verify:

- [ ] `workshop.md` has YAML frontmatter + TL;DR within first 20 lines.
- [ ] Decision is stated in past tense.
- [ ] Elias Vance's perspective is included.
- [ ] Dissent (if any) is logged in `research/dissent-register.md` with a review trigger.
- [ ] `summary.json` has been created and is valid JSON.
- [ ] `research/DECISIONS.md` has been updated.
- [ ] `research/sprint-status.md` has been updated.
- [ ] ADR created in `docs/decisions/` if a significant technical decision was made.
