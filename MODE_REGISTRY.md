# MODE_REGISTRY — Digital Humanity Skills Suite

Single source of truth for all modes across all five skills.

---

## dh-explore — Research & Discovery

| Mode | Trigger Keyword | Agents Executed | Output | Oversight |
|------|----------------|-----------------|--------|-----------|
| `full` | `/dh-explore` or `/dh-explore full` | All 10 agents in sequence | Full dh-explore Output Package | High — intake clarification + socratic dialogue |
| `quick-brief` | `/dh-explore quick-brief` | intake → research_question_agent | Research Question Brief only | Low |
| `socratic` | `/dh-explore socratic` | intake → socratic_mentor_agent → research_question_agent | Draft RQ via guided dialogue | Medium |
| `archive-survey` | `/dh-explore archive-survey` | intake → digital_archive_agent → primary_source_agent → corpus_builder_agent | Archive Survey + Corpus Manifest | Medium |
| `methodology-guide` | `/dh-explore methodology-guide` | intake → methodology_advisor_agent | Methodology Blueprint | Low |
| `lit-review-humanities` | `/dh-explore lit-review-humanities` | intake → humanities_literature_agent | Humanities Literature Review Brief | Low |
| `lit-review-technical` | `/dh-explore lit-review-technical` | intake → technical_literature_agent | Technical Literature Review Brief | Low |

**Handoff output**: dh-explore Output Package (RQ Brief + Methodology Blueprint + Corpus Manifest + Literature Briefs + Research Framework)

---

## dh-write — Writing & Drafting

| Mode | Trigger Keyword | Agents Executed | Output | Oversight |
|------|----------------|-----------------|--------|-----------|
| `full` | `/dh-write` or `/dh-write full` | intake → argument_mapper → methodology_writer → draft_writer → citation → abstract | Complete draft + abstract + bibliography | High |
| `article` | `/dh-write article` | Same as full, with journal article structure | Journal article draft | High |
| `proposal` | `/dh-write proposal` | intake → proposal_architect → citation | Research proposal / prospectus | Medium |
| `grant-proposal` | `/dh-write grant-proposal` | intake → proposal_architect (grant mode) → citation | Grant application (NEH/Mellon/AHRC) | High |
| `thesis` | `/dh-write thesis` | intake → thesis_architect → draft_writer | Chapter plan + draft | High |
| `qualifying-paper` | `/dh-write qualifying-paper` | intake → thesis_architect (qual mode) → argument_mapper → draft_writer | Qualifying / comprehensive exam paper | High |
| `conference-paper` | `/dh-write conference-paper` | intake → argument_mapper (compressed) → abstract | Conference abstract | Low |
| `book-review` | `/dh-write book-review` | intake → argument_mapper (book-review mode) → draft_writer | Academic book review 500–1500 words | Medium |
| `close-reading` | `/dh-write close-reading` | intake → close_reading_agent | Close reading section | Low |
| `revision` | `/dh-write revision` | intake → revision_coach_agent | Revision Roadmap | Medium |
| `response-to-reviewers` | `/dh-write response-to-reviewers` | intake → revision_coach_agent (response-letter mode) | Point-by-point reviewer response letter | Medium |
| `citation-check` | `/dh-write citation-check` | intake → citation_agent | Formatted bibliography | Low |
| `outline` | `/dh-write outline` | intake → socratic_mentor → argument_mapper | Argument map / outline | Medium |
| `format-convert` | `/dh-write format-convert` | formatter_agent | Submission-ready document | Low |

**Handoff output**: Draft with `## Draft Complete` header (detected by dh-review intake)

---

## dh-review — Feedback & Review

| Mode | Trigger Keyword | Agents Executed | Output | Oversight |
|------|----------------|-----------------|--------|-----------|
| `full-review` | `/dh-review` or `/dh-review full-review` | intake → technical_reviewer + humanities_reviewer + interdisciplinary_reviewer + devil_advocate | Reviewer Decision + Revision Roadmap | High |
| `supervisor-feedback` | `/dh-review supervisor-feedback` | intake → supervisor_feedback_agent | Structured Revision Roadmap | Medium |
| `technical-focus` | `/dh-review technical-focus` | intake → technical_reviewer_agent | Technical Review | Low |
| `humanities-focus` | `/dh-review humanities-focus` | intake → humanities_reviewer_agent | Humanities Review | Low |
| `interdisciplinary` | `/dh-review interdisciplinary` | intake → interdisciplinary_reviewer_agent | DH Bridge Review | Low |
| `quick-assess` | `/dh-review quick-assess` | intake → all 4 review agents (condensed) | Quick assessment (150 words per reviewer) | Low |

**Handoff output**: Reviewer Decision + Revision Roadmap (detected by dh-write revision mode)

---

## dh-pipeline — Full Lifecycle Orchestrator

| Mode | Trigger Keyword | Description |
|------|----------------|-------------|
| `full` | `/dh-pipeline` | Start or resume from current stage |
| `status` | `/dh-pipeline status` | Show pipeline stage and completion status |
| `resume` | `/dh-pipeline resume` | Resume from a pasted DH Material Passport |
| `stage N` | `/dh-pipeline stage 4` | Jump to a specific stage |
| `gate N` | `/dh-pipeline gate 4.5` | Work through a specific mandatory gate |
| `passport` | `/dh-pipeline passport` | View or export the DH Material Passport |

**Mandatory gates**: 2.5 (Ethics), 4.5 (Integrity), 6.5 (Final) — cannot be bypassed

---

## dh-refs — Citation & Reference Management

| Mode | Trigger Keyword | Agents Executed | Output | Oversight |
|------|----------------|-----------------|--------|-----------|
| `build` | `/dh-refs` or `/dh-refs build` | intake → bibliography_builder → gap_analysis | DH Bibliography Corpus (CSL-JSON) + Literature Gap Report | Medium |
| `annotate` | `/dh-refs annotate` | intake → bibliography_builder → annotated_bibliography | Annotated Bibliography | Medium |
| `format` | `/dh-refs format` | intake → citation_formatter | Formatted bibliography in target style | Low |
| `gap-check` | `/dh-refs gap-check` | intake → gap_analysis | Literature Gap Report | Low |
| `import` | `/dh-refs import` | intake → bibliography_builder (import only) | Normalized CSL-JSON corpus | Low |

**Handoff output**: `## DH Bibliography Corpus (CSL-JSON)` + `## Annotated Bibliography` + `## Literature Gap Report` (detected by dh-write and dh-pipeline intakes)

---

## Keyword Routing Summary

| User Says | Routes To |
|---|---|
| `/dh-explore` | dh-explore, full mode |
| `/dh-write` | dh-write, full mode |
| `/dh-review` | dh-review, full-review mode |
| `/dh-refs` | dh-refs, build mode |
| `/dh-pipeline` | dh-pipeline, full mode |
| "help me find archives" | dh-explore, archive-survey |
| "help me choose a method" | dh-explore, methodology-guide |
| "help me write my proposal" | dh-write, proposal |
| "help me write a grant" | dh-write, grant-proposal |
| "help me outline my article" | dh-write, outline |
| "write a book review" | dh-write, book-review |
| "respond to reviewers" | dh-write, response-to-reviewers |
| "help with my qualifying paper" | dh-write, qualifying-paper |
| "build my bibliography / manage references" | dh-refs, build |
| "format my citations" | dh-refs, format |
| "what am I missing in my reading list" | dh-refs, gap-check |
| "review my paper" | dh-review, full-review |
| "parse my supervisor's comments" | dh-review, supervisor-feedback |
| "format my paper for submission" | dh-write, format-convert |
| "where am I in the pipeline" | dh-pipeline, status |
