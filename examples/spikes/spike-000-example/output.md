---
title: "Spike 000: Example Spike — Output Template Reference"
type: spike-output
status: template
date: YYYY-MM-DD
spike-type: technical
timebox: "2 days"
question: "[Replace with the specific question this spike answered.]"
answer: "[One-sentence answer — yes/no/option chosen/recommendation.]"
confidence: high | medium | low
consumer: "[The story or decision that is now unblocked.]"
adr: "[Path to ADR if one was produced, or 'None'.]"
tags: [template]
---

**Answer:** [One sentence — the conclusion, stated directly. Never bury this. It is the first thing a reader or LLM should see.]

---

## Recommendation

[What should the team do next, based on this answer? One to three sentences. Be direct. If the answer is "use Option A", say "Use Option A" — not "we suggest considering Option A."]

## Evidence

[Comparison tables, benchmark data, proof-of-concept results. Use tables over prose. The goal is to show the work, not to re-argue the conclusion.]

| Option | Pros | Cons | Verdict |
|--------|------|------|---------|
| [Option A] | [Strength 1], [Strength 2] | [Weakness 1] | **Chosen** — [one-line reason] |
| [Option B] | [Strength 1] | [Weakness 1], [Weakness 2] | Rejected — [one-line reason] |
| [Option C] | [Strength 1] | [Weakness 1] | Rejected — [one-line reason] |

### Persona Perspectives

**Dr. Lena Petrova — Design Engineer**
> "[Her signature question: 'How will we build, test, and maintain this?']"

[Her finding — 2–4 sentences from her lens. What does this mean for the existing architecture and tooling? What would be hard to maintain?]

**Marcus Thorne — Senior Developer**
> "[His signature question: 'What are we NOT building here?']"

[His finding — 2–4 sentences from his lens. What are the long-term architectural implications? What would be hard to reverse?]

**Kira Sharma — Developer**
> "[Her signature question: 'What does the implementation actually look like?']"

[Her finding — 2–4 sentences from her lens. What are the actual code paths, integration points, and effort estimates?]

## Constraints Discovered

[Things the team did not know before the spike that are now important constraints. List as bullet points. These should be logged in `research/DECISIONS.md` if they affect future work.]

- [Constraint 1 — e.g., "Option A requires a minimum plan tier that costs £X/month."]
- [Constraint 2 — e.g., "Option B does not support webhook retries, which is a hard requirement."]

## Decision

[The chosen option, stated in past tense. E.g., "We decided to use Option A. See ADR at `docs/decisions/001-[topic].md`."]

---

_Appendix: Raw Research_

> Everything below this line is raw research notes. This is the "stop reading here" signal for LLMs and reviewers. The answer, recommendation, and evidence above are the only sections that need to be read.

### Source 1: [Source Name / URL]

[Raw notes, quotes, and data from this source.]

### Source 2: [Source Name / URL]

[Raw notes, quotes, and data from this source.]

### Proof-of-Concept Results

[If a proof-of-concept was built, include the results here. Code snippets, screenshots, or benchmark outputs.]
