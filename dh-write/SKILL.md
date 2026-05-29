---
name: dh-write
description: "Digital humanities writing and drafting — research proposals, thesis chapters, journal articles, conference papers, grant applications, response-to-reviewers letters, close-reading essays, citation management, and revision coaching. Handles both humanities prose and computational DH writing conventions. Triggers: write paper, write proposal, write thesis, write chapter, write grant, draft, revise, conference paper, journal article, response to reviewers, close reading, format paper, book review, qualifying paper."
metadata:
  version: "1.1.0"
  last_updated: "2026-05-29"
  status: active
  data_access_level: redacted
  task_type: open-ended
  related_skills:
    - dh-explore
    - dh-review
    - dh-refs
    - dh-pipeline
---

# dh-write — Writing & Drafting

## What This Skill Does

`dh-write` supports all DH writing tasks:
- Research proposals (grant applications, dissertation prospectus)
- **Grant applications** (NEH DHAG, Mellon Foundation, AHRC, other funders)
- Thesis and dissertation chapter planning and drafting
- **PhD qualifying / comprehensive exam papers**
- Journal articles (DHQ, DSH, Cultural Analytics styles)
- Conference abstracts (ADHO, CHI format)
- **Response-to-reviewers letters** (point-by-point response to journal/conference reviewers)
- **Book reviews** (500–1500 words, DH venue conventions)
- Close-reading essays and textual analysis
- Citation formatting with DH-specific edge cases (digitized texts, tools, datasets)
- Parsing supervisor feedback into a structured revision roadmap
- Document formatting for submission

## Who It's For
- Undergraduates writing papers and close-reading essays
- Graduate students preparing proposals, thesis chapters, qualifying papers, and articles
- Faculty writing for DH journals, conferences, and grant applications
- Researchers who need to bridge technical findings with humanistic argument
- Anyone managing supervisor/reviewer feedback or responding to journal reviewers

---

## Modes and Trigger Keywords

| Mode | Trigger | What Happens |
|------|---------|--------------|
| `full` | `/dh-write` | Full pipeline: intake → argument map → draft → citation → abstract |
| `proposal` | `/dh-write proposal` | Research proposal or dissertation prospectus |
| `grant-proposal` | `/dh-write grant-proposal` | Grant application (NEH DHAG, Mellon, AHRC templates) |
| `thesis` | `/dh-write thesis` | Dissertation/thesis chapter planning and drafting |
| `qualifying-paper` | `/dh-write qualifying-paper` | PhD qualifying / comprehensive exam paper |
| `article` | `/dh-write article` | Journal article (select venue style) |
| `conference-paper` | `/dh-write conference-paper` | Conference abstract + short paper |
| `book-review` | `/dh-write book-review` | Academic book review (500–1500 words) |
| `close-reading` | `/dh-write close-reading` | Textual analysis / close reading only |
| `revision` | `/dh-write revision` | Parse supervisor feedback → revision roadmap |
| `response-to-reviewers` | `/dh-write response-to-reviewers` | Point-by-point response letter to journal/conference reviewers |
| `citation-check` | `/dh-write citation-check` | Citation formatting and bibliography only |
| `outline` | `/dh-write outline` | Argument map / outline only |
| `format-convert` | `/dh-write format-convert` | Convert/format for submission |

---

## Mode Routing

1. **Always start with intake**: Read `agents/intake_agent.md` and execute it.

2. **Route by mode**:
   - `full` or `article`: intake → `argument_mapper_agent.md` → `methodology_writer_agent.md` → `draft_writer_agent.md` → `citation_agent.md` → `abstract_agent.md`
   - `proposal`: intake → `proposal_architect_agent.md` → `citation_agent.md`
   - `grant-proposal`: intake → `proposal_architect_agent.md` (grant mode) → `citation_agent.md`
   - `thesis`: intake → `thesis_architect_agent.md` → `draft_writer_agent.md`
   - `qualifying-paper`: intake → `thesis_architect_agent.md` (qualifying mode) → `argument_mapper_agent.md` → `draft_writer_agent.md`
   - `close-reading`: intake → `close_reading_agent.md`
   - `revision`: intake → `revision_coach_agent.md`
   - `response-to-reviewers`: intake → `revision_coach_agent.md` (response-letter mode)
   - `book-review`: intake → `argument_mapper_agent.md` (book-review mode) → `draft_writer_agent.md`
   - `citation-check`: intake → `citation_agent.md`
   - `outline`: intake → `socratic_mentor_agent.md` → `argument_mapper_agent.md`
   - `conference-paper`: intake → `argument_mapper_agent.md` (condensed) → `abstract_agent.md`
   - `format-convert`: `formatter_agent.md`

3. **Upstream materials detection**: Check for a dh-explore Output Package. If `## Research Question Brief`, `## Methodology Blueprint`, or `## Corpus Manifest` sections are present, auto-populate intake — skip asking questions already answered.

---

## Shared References

Before beginning, load:
- Read: `../shared/references/dh_methodology_spectrum.md`
- Read: `../shared/references/anti_leakage_protocol.md`
- Read: `../shared/references/user_profile_guide.md` (apply user level calibration throughout)

---

## Handoff Output

On completion of a full draft or article mode, produce output containing a `## Draft Complete` header. This signals to `dh-review`'s intake agent that the paper is ready for review.

---

## Citation Integrity Note

This skill does not fabricate citations. Any citation that cannot be verified from materials the user has provided is marked `[UNVERIFIED]`. The citation agent checks all citations against this standard. Never trust a citation in a dh-write output without verifying it against the original source.

---

## Supervisor Feedback Note

The `revision_coach_agent` shares its feedback parsing protocol with `dh-review`'s `supervisor_feedback_agent`. If you use both `/dh-write revision` and `/dh-review supervisor-feedback`, the feedback parsing logic is the same — the dh-review version provides additional multi-perspective reviewer simulation alongside the feedback parsing.
