---
name: dh-review
description: Digital humanities peer review simulation and supervisor feedback parsing. Simulates technical, humanistic, and interdisciplinary reviewer perspectives calibrated to your target venue. Parses unstructured supervisor feedback into a structured revision roadmap. The DH-specific "bridge review" evaluates whether your computational and humanistic work genuinely connect.
---

# dh-review — Feedback & Review

## What This Skill Does

`dh-review` provides two types of assistance:

1. **Review simulation**: Evaluates your DH paper from three perspectives — technical (methodology, data, reproducibility), humanistic (argument, scholarship, interpretation), and interdisciplinary (the DH bridge). Also includes devil's advocate challenge.

2. **Feedback parsing**: Transforms unstructured supervisor, advisor, or peer reviewer comments into a prioritized, actionable revision roadmap.

## Who It's For
- Graduate students preparing to submit a paper and wanting pre-submission review
- Researchers who have received supervisor or reviewer feedback and need help prioritizing the revision
- Anyone wanting to stress-test their DH argument before exposing it to real reviewers

---

## Modes and Trigger Keywords

| Mode | Trigger | What Happens |
|------|---------|--------------|
| `full-review` | `/dh-review` or `/dh-review full-review` | Complete multi-perspective review (all 4 review agents) |
| `supervisor-feedback` | `/dh-review supervisor-feedback` | Parse supervisor/reviewer comments → revision roadmap |
| `technical-focus` | `/dh-review technical-focus` | Computational methodology and reproducibility review only |
| `humanities-focus` | `/dh-review humanities-focus` | Humanistic argument and scholarly engagement review only |
| `interdisciplinary` | `/dh-review interdisciplinary` | DH bridge review only — does the paper justify being DH? |
| `quick-assess` | `/dh-review quick-assess` | Rapid high-level assessment; ~10 minutes |

---

## Mode Routing

1. **Always start with intake**: Read `agents/intake_agent.md` to detect input type and configure review balance.

2. **Route by mode**:
   - `full-review`: Execute all four review agents in sequence, then compile the **Reviewer Decision**
   - `supervisor-feedback`: Execute `supervisor_feedback_agent.md` only
   - `technical-focus`: Execute `technical_reviewer_agent.md` only
   - `humanities-focus`: Execute `humanities_reviewer_agent.md` only
   - `interdisciplinary`: Execute `interdisciplinary_reviewer_agent.md` only
   - `quick-assess`: Execute all four agents; limit each to 150 words; compile a condensed report

---

## Review Calibration

Before the review, read `references/reviewer_calibration_guide.md` and set the technical/humanistic weight ratio based on the target venue. The balance shifts from 35/65 (DHQ) to 65/35 (Cultural Analytics).

---

## The Reviewer Decision (Full Review Output)

After `full-review`, produce a single consolidated output:

```markdown
## Reviewer Decision

**Paper**: [title]
**Target Venue**: [venue]
**Review Date**: [date]

**Overall Recommendation**: [Accept (minor revisions) | Minor Revisions | Major Revisions | Reject/Resubmit]

**Scores**:
| Criterion | Score (1–5) |
|---|---|
| Research Question Quality | [n] |
| Corpus Integrity | [n] |
| Methodological Soundness | [n] |
| Interpretive Depth | [n] |
| Scholarly Engagement | [n] |
| DH Bridge | [n] |
| **Overall** | **[n]** |

**Summary**: [2–3 paragraph integrated review — synthesis of all three reviewer perspectives]

**Revision Roadmap**: [Tier 1 / Tier 2 / Tier 3 items, consolidated from all reviewers]
```

---

## Handoff

After `full-review`: the **Reviewer Decision** + **Revision Roadmap** is detected by `dh-write`'s intake agent when passed into a `revision` mode session.

After `supervisor-feedback`: the **Revision Roadmap** is detected by `dh-write revision` mode.

In `dh-pipeline`, Stage 5.5 uses this skill's `supervisor-feedback` mode to process advisor feedback between review rounds.
