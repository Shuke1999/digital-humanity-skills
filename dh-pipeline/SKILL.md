---
name: dh-pipeline
description: Full digital humanities research lifecycle orchestrator. Manages a 12-stage pipeline from initial research question through final submitted paper, with mandatory ethics, integrity, and final quality gates. Tracks all sources, tools, and supervision feedback in a DH Material Passport for cross-session continuity.
---

# dh-pipeline — Full Lifecycle Orchestrator

## What This Skill Does

`dh-pipeline` orchestrates the complete DH research process across 12 stages:

```
Stage 1    EXPLORE          → dh-explore (full mode)
Stage 2    PROPOSE          → dh-write (proposal mode)
Stage 2.5  ETHICS GATE      ← MANDATORY
Stage 3    METHODOLOGY      → dh-explore (methodology-guide mode)
Stage 4    WRITE            → dh-write (full/thesis/article)
Stage 4.5  INTEGRITY GATE   ← MANDATORY
Stage 5    REVIEW           → dh-review (full-review mode)
Stage 5.5  SUPERVISOR       → dh-review (supervisor-feedback mode)
Stage 6    REVISE           → dh-write (revision mode)
Stage 6.5  FINAL GATE       ← MANDATORY
Stage 7    FINALIZE         → dh-write (format-convert mode)
Stage 8    DOCUMENT         → DH Material Passport export
```

## Who It's For
- Graduate students managing a dissertation research project over months
- Faculty managing a large grant-funded DH project
- Anyone who wants structured oversight of a complex DH workflow
- Projects where research integrity, source provenance, and revision history must be tracked

---

## Modes and Trigger Keywords

| Mode | Trigger | What Happens |
|------|---------|--------------|
| `full` | `/dh-pipeline` | Start or resume from the current pipeline stage |
| `status` | `/dh-pipeline status` | Show current stage and what has been completed |
| `resume` | `/dh-pipeline resume` | Resume from a DH Material Passport |
| `stage N` | `/dh-pipeline stage 4` | Jump directly to stage N |
| `gate 2.5/4.5/6.5` | `/dh-pipeline gate 4.5` | Work through a specific gate |
| `passport` | `/dh-pipeline passport` | View or export the current DH Material Passport |

---

## The Three Mandatory Gates

These gates cannot be bypassed or skipped. They exist to protect research quality:

| Gate | Stage | Protects Against |
|------|-------|-----------------|
| Ethics Gate | 2.5 | Unethical data use, copyright violation, undisclosed bias |
| Integrity Gate | 4.5 | Fabricated or unverified citations, corpus-draft inconsistency |
| Final Gate | 6.5 | Unresolved must-fix items, unchecked claims, submission failures |

If a user attempts to skip a gate, the pipeline orchestrator refuses and presents the remaining checklist items.

---

## DH Material Passport

The Passport is the spine of the pipeline — it persists across sessions and is the only form of state memory.

**Schema**: `../shared/contracts/passport/dh_passport.schema.json`

**Key fields**:
- `pipeline_stage`: current position in the pipeline
- `gates_passed[]`: which mandatory gates have been completed (with tokens)
- `primary_source_corpus[]`: all primary sources with OCR quality data
- `literature_corpus[]`: secondary sources in CSL-JSON format
- `tool_refs[]`: all software tools used
- `supervision_log[]`: all supervisor/reviewer feedback rounds

**Save your passport at the end of every session** — the pipeline cannot resume without it.

---

## Mode Routing

1. Read `agents/pipeline_orchestrator_agent.md` — this is the first agent to execute
2. The orchestrator determines stage, presents status, and dispatches to the appropriate skill
3. Gate stages are handled by `agents/integrity_verification_agent.md`
4. The `agents/material_passport_agent.md` is called after each stage to update the passport
5. The `agents/supervision_checkpoint_agent.md` fires at Stages 2, 5.5, and post-revision
6. The `agents/state_tracker_agent.md` handles session start/end and cross-session resume

---

## Shared References

Load at startup:
- Read: `../shared/references/dh_ethics_protocol.md`
- Read: `../shared/references/anti_leakage_protocol.md`
- Read: `references/pipeline_stages_guide.md`

---

## The Canonical Test Case

A research project studying sentiment and topic evolution in 19th-century abolitionist newspapers from Chronicling America, with a corpus of ~300 issues and 75–82% estimated OCR accuracy. This project would:
- Stage 1: identify Chronicling America as the primary archive; assess OCR quality; formulate RQ about rhetoric shift after the Kansas-Nebraska Act (1854)
- Stage 2.5 Ethics Gate: verify public domain status, document OCR quality, identify Chronicling America API terms
- Stage 4: write a Cultural Analytics-style hybrid article
- Stage 4.5 Integrity Gate: verify all Chronicling America URLs use persistent identifiers; check MALLET and spaCy are cited
- Stage 5: review simulation with 60% technical / 40% humanistic balance for Cultural Analytics
