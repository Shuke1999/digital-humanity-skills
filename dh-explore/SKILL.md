---
name: dh-explore
description: "Digital humanities research discovery — research question development, digital archive search, primary source criticism, corpus assembly, literature review, and research framework mapping. Produces venue-specific framework diagrams showing recommended methods (topic modeling, NER, sentiment analysis, close reading) and paper structure for NLP/AI venues, DH journals, traditional humanities journals, or specific target publishers. Use when starting a DH project, building a corpus, or planning a research methodology."
metadata:
  version: "1.1.0"
  last_updated: "2026-05-29"
  status: active
  data_access_level: redacted
  task_type: open-ended
  related_skills:
    - dh-write
    - dh-refs
    - dh-pipeline
---

# dh-explore — Research & Discovery

## What This Skill Does

`dh-explore` guides you from an initial DH idea to a fully developed research framework, including:
- A refined, dual-framed research question (interpretive claim + methodological contribution)
- A methodology blueprint matched to your corpus and question
- A Corpus Manifest with primary sources assessed for OCR quality and provenance
- An annotated bibliography spanning both humanities and computational DH literature
- A Research Question Brief ready to hand off to `dh-write`

## Who It's For
- Researchers at any stage — undergraduate to faculty
- Projects anywhere on the DH methodology spectrum (close reading to large-scale text mining)
- Particularly strong for projects involving digitized historical materials and noisy OCR text

---

## Modes and Trigger Keywords

| Mode | Trigger | What Happens |
|------|---------|--------------|
| `full` | `/dh-explore` or `/dh-explore full` | Complete pipeline: intake → socratic → methodology → archives → literature → corpus → synthesis → RQ → **framework** |
| `quick-brief` | `/dh-explore quick-brief` | Fast path: intake → RQ refinement only; ~15 min |
| `socratic` | `/dh-explore socratic` | Guided dialogue to discover your research question |
| `archive-survey` | `/dh-explore archive-survey` | Archive identification and evaluation only |
| `methodology-guide` | `/dh-explore methodology-guide` | Method selection and OCR quality assessment only |
| `lit-review-humanities` | `/dh-explore lit-review-humanities` | Humanities literature search and annotated bibliography |
| `lit-review-technical` | `/dh-explore lit-review-technical` | Computational DH literature review |
| `framework` | `/dh-explore framework` | Research framework map: given an RQ, build method diagram + venue-specific paper structure |

---

## Mode Routing

When this skill is invoked, do the following:

1. **Always start with intake**: Read `agents/intake_agent.md` and execute it to configure the session.

2. **After intake, route by mode**:
   - `full` → Read and execute agents in order: `socratic_mentor_agent.md` → `methodology_advisor_agent.md` → `digital_archive_agent.md` → `primary_source_agent.md` → `corpus_builder_agent.md` → `humanities_literature_agent.md` → `technical_literature_agent.md` → `cross_domain_synthesis_agent.md` → `research_question_agent.md` → `framework_architect_agent.md`
   - `quick-brief` → Read and execute: `research_question_agent.md` only (after intake)
   - `socratic` → Read and execute: `socratic_mentor_agent.md` → `research_question_agent.md`
   - `archive-survey` → Read and execute: `digital_archive_agent.md` → `primary_source_agent.md` → `corpus_builder_agent.md`
   - `methodology-guide` → Read and execute: `methodology_advisor_agent.md`
   - `lit-review-humanities` → Read and execute: `humanities_literature_agent.md`
   - `lit-review-technical` → Read and execute: `technical_literature_agent.md`
   - `framework` → Read and execute: `framework_architect_agent.md` (requires RQ — ask if not present; can run standalone or after any other mode)

3. **If upstream materials are detected** (blocks labeled `## Research Question Brief`, `## Corpus Manifest`, `## Methodology Blueprint`): skip agents that would produce what's already present; use the existing materials as input to agents further down the chain.

---

## Shared References

Before beginning, load these shared resources:
- Read: `../shared/references/dh_methodology_spectrum.md`
- Read: `../shared/references/intent_clarification_protocol.md`
- Read: `../shared/references/anti_leakage_protocol.md`

---

## Handoff Output

On completion of `full` mode, produce a **dh-explore Output Package** containing:

```
## Research Question Brief       ← for dh-write intake
## Methodology Blueprint         ← for dh-write methodology_writer_agent
## Corpus Manifest               ← for dh-write and dh-pipeline
## Literature Review Brief — Humanities
## Literature Review Brief — Technical
## Research Framework
## Research Framework Map        ← NEW: Mermaid diagram + venue-specific paper structure
```

`dh-write`'s intake agent detects this package and auto-populates the writing session. Save or paste this package when starting `/dh-write`.

---

## The Canonical Use Case

This skill was built around a project working with **19th-century abolitionist newspapers** from Chronicling America — digitized historical text with 75–85% OCR accuracy. If your project involves:
- Noisy OCR text from historical digitization
- Primary source provenance questions
- The tension between computational pattern-finding and historical interpretation

...then you are using this skill for exactly the purpose it was designed for.

---

## Exemplar DH Projects Referenced in This Skill

- "Mining for the Meanings of a Murder: The Impact of OCR Quality on the Use of Digitized Historical Newspapers" — DHQ — OCR quality and text mining methodology
- "Machine Reading the Primeros Libros" — DHQ vol.10 no.4 — Colonial archive digitization
- "How Network Analysis Uncovers International Networks of Smuggling History" — Cultural Analytics 2023 — Historical network analysis
- "The Generative Dissensus of Reading the Feminist Novel, 1995-2020" — Cultural Analytics — Computational + close reading synthesis
- "Slow, Painful and Expensive: Current Challenges in Text-Mining Corpus Construction" — DHQ 19/3 — Corpus construction reality
