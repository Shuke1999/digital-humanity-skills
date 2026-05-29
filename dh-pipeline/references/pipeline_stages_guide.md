# dh-pipeline Stages Guide

## Overview

The dh-pipeline orchestrates the full DH research lifecycle across 12 stages with 3 mandatory integrity gates. No stage can be skipped once started; the three gate stages cannot be bypassed under any circumstances.

---

## Stage Definitions

### Stage 1: EXPLORE
**Skill**: dh-explore (full mode)
**Input**: Project description from user
**Output**: dh-explore Output Package (RQ Brief + Methodology Blueprint + Corpus Manifest + Literature Briefs + Research Framework)
**Gate to next**: Output Package complete with all six sections

---

### Stage 2: PROPOSE
**Skill**: dh-write (proposal mode)
**Input**: dh-explore Output Package
**Output**: Research proposal draft (dissertation prospectus or grant application)
**Gate to next**: Proposal reviewed and user confirms it reflects their project correctly

---

### Stage 2.5: ETHICS GATE ← MANDATORY
**Agent**: `integrity_verification_agent` (ethics check)
**No skill dispatch — handled directly by the pipeline orchestrator**

This gate cannot be bypassed. The following checklist must be completed before proceeding:

```
ETHICS GATE CHECKLIST

☐ 1. Corpus materials are legally accessible for the intended use
     Evidence: [archive name + license/rights statement]

☐ 2. Copyright status of primary sources verified
     Evidence: [date + rights analysis]

☐ 3. IRB / ethics board review assessed
     Verdict: [Required / Not required — because:]

☐ 4. Indigenous or community materials flagged
     Verdict: [None | Identified — protocols:]

☐ 5. OCR quality documented (if digitized historical sources)
     Evidence: [accuracy estimate + method]

☐ 6. Attribution plan in place for archives, tools, datasets
     Plan: [summary]

☐ 7. Known algorithmic biases identified
     Description: [what biases and how they will be named in the paper]
```

**Gate completion token**: `ETHICS_GATE_PASSED_[project_id]_[timestamp]`
This token is required as input to Stage 3.

---

### Stage 3: METHODOLOGY
**Skill**: dh-explore (methodology-guide mode)
**Input**: Research proposal + Ethics Gate token
**Output**: Refined Methodology Blueprint (if changes since Stage 1)
**Gate to next**: Methodology Blueprint confirmed

---

### Stage 4: WRITE
**Skill**: dh-write (full / thesis / article — selected by user)
**Input**: dh-explore Output Package + Methodology Blueprint
**Output**: Complete draft with `## Draft Complete` header
**Gate to next**: Draft complete

---

### Stage 4.5: INTEGRITY GATE ← MANDATORY
**Agent**: `integrity_verification_agent` (citation + source integrity)
**No skill dispatch — handled directly by the pipeline orchestrator**

```
INTEGRITY GATE CHECKLIST

☐ 1. All in-text citations have bibliography entries
     Checked: [yes / n issues found]

☐ 2. No [UNVERIFIED] citations remain unresolved
     Checked: [yes / n unverified remain — list]

☐ 3. All tools cited in the methods section
     Checked: [yes / missing: list]

☐ 4. All claims connected to cited evidence
     Checked: [yes / n unsupported claims found]

☐ 5. Corpus construction decisions match those in the Corpus Manifest
     Checked: [yes / discrepancies: list]

☐ 6. OCR quality limitations disclosed in Methods section
     Checked: [yes / not yet]

☐ 7. DH Material Passport is current
     Checked: [yes / out of date — what's missing]
```

**Gate completion token**: `INTEGRITY_GATE_PASSED_[project_id]_[timestamp]`
Required for Stage 5.

---

### Stage 5: REVIEW
**Skill**: dh-review (full-review mode)
**Input**: Draft + Integrity Gate token
**Output**: Reviewer Decision + Revision Roadmap
**Gate to next**: Review complete with Revision Roadmap

---

### Stage 5.5: SUPERVISOR FEEDBACK LOOP
**Skill**: dh-review (supervisor-feedback mode)
**Input**: Actual supervisor/advisor comments (if available) OR self-review using Revision Roadmap from Stage 5
**Output**: Parsed Revision Roadmap (Tier 1/2/3)
**Gate to next**: Revision Roadmap approved by researcher

---

### Stage 6: REVISE
**Skill**: dh-write (revision mode)
**Input**: Revision Roadmap from Stage 5.5
**Output**: Revised draft with `## Revision Complete` header
**Gate to next**: Revision complete

---

### Stage 6.5: FINAL GATE ← MANDATORY
**Agent**: `integrity_verification_agent` (final check)

```
FINAL GATE CHECKLIST

☐ 1. All Tier 1 (Must Fix) items from Revision Roadmap are addressed
     Checked: [yes / n remaining — list]

☐ 2. All Tier 2 (Should Fix) items addressed or explicitly deferred with reason
     Checked: [yes / n deferred — list reasons]

☐ 3. Argument is stated in Introduction and Conclusion
     Checked: [yes / no]

☐ 4. DH bridge is explicitly argued (computation supports humanistic claim)
     Checked: [yes / no — location]

☐ 5. All citations verified
     Checked: [yes / remaining issues]

☐ 6. DH Material Passport complete and current
     Checked: [yes / incomplete — what's missing]

☐ 7. Paper is within venue word count limits
     Checked: [yes / over by n words]
```

**Gate completion token**: `FINAL_GATE_PASSED_[project_id]_[timestamp]`
Required for Stage 7.

---

### Stage 7: FINALIZE
**Skill**: dh-write (format-convert mode)
**Input**: Revised draft + Final Gate token
**Output**: Submission-ready formatted document

---

### Stage 8: DOCUMENT
**Agent**: `material_passport_agent` + `state_tracker_agent`
**Input**: All pipeline artifacts
**Output**: Final DH Material Passport export

---

## Gate Enforcement Rules

1. When a user says "skip" or "proceed anyway" at a gate: respond with "This is a mandatory gate. The checklist must be completed before proceeding. Here are the remaining unchecked items: [list]"
2. A gate can be completed in multiple turns — the checklist persists
3. The gate completion token is generated only when all items are checked
4. The pipeline orchestrator records gate completion in the DH Material Passport `gates_passed[]` field

---

## State Recovery

If a pipeline session is interrupted:
1. The `state_tracker_agent` recovers state from the DH Material Passport
2. It identifies the last completed stage from `pipeline_stage` and `gates_passed[]`
3. It presents the user with their current state and asks whether to resume from the last completed stage or restart from a specific stage
4. Restart from any stage is permitted; skipping a mandatory gate is not
