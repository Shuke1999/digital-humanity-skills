---
name: dh-refs
description: "Digital humanities citation and reference management — import Zotero/.bib/.ris files, build annotated bibliographies, format citations in Chicago/MLA/APA/Turabian, identify literature gaps. Use when managing sources before writing, or when needing a standalone bibliography. Triggers: bibliography, references, Zotero, .bib file, annotated bibliography, cite, citation format, what am I missing in my reading list."
metadata:
  version: "1.0.0"
  last_updated: "2026-05-29"
  status: active
  data_access_level: redacted
  task_type: open-ended
  related_skills:
    - dh-explore
    - dh-write
    - dh-pipeline
---

# dh-refs — Citation & Reference Management

## What This Skill Does

`dh-refs` handles everything source-related that happens between discovering literature and writing with it:

- **Import**: Accept Zotero RDF, `.bib`, `.ris`, PDF lists, or free-text reading lists — parse into a normalized corpus
- **Annotate**: Generate an annotated bibliography with summary and relevance note per source
- **Format**: Output citations in Chicago Notes-Bibliography, Chicago Author-Date, MLA, APA, or Turabian
- **Gap-check**: Given your research question and existing corpus, identify what types of scholarship are missing
- **Handoff**: Export a DH Bibliography Corpus (CSL-JSON) for seamless import into `dh-write`

## Who It's For

- Anyone building a reading list for a DH project
- Students preparing annotated bibliographies for coursework or comprehensive exams
- Researchers consolidating references from multiple sources before writing
- Writers who need a formatted bibliography without using a full reference manager

---

## Modes and Trigger Keywords

| Mode | Trigger | What Happens |
|------|---------|--------------|
| `build` | `/dh-refs` or `/dh-refs build` | Full pipeline: import sources → normalize → deduplicate → output clean corpus |
| `annotate` | `/dh-refs annotate` | Generate annotated bibliography from existing corpus or pasted sources |
| `format` | `/dh-refs format` | Format existing references into a specified citation style |
| `gap-check` | `/dh-refs gap-check` | Identify missing scholarship given RQ and current corpus |
| `import` | `/dh-refs import` | Import and normalize a Zotero/bib/ris file |

---

## Mode Routing

1. **Always start with intake**: Read `agents/intake_agent.md` and execute it.

2. **Route by mode**:
   - `build` → `intake_agent` → `bibliography_builder_agent` → `gap_analysis_agent`
   - `annotate` → `intake_agent` → `bibliography_builder_agent` → `annotated_bibliography_agent`
   - `format` → `intake_agent` → `citation_formatter_agent`
   - `gap-check` → `intake_agent` → `gap_analysis_agent`
   - `import` → `intake_agent` → `bibliography_builder_agent`

3. **Upstream detection**: If a dh-explore `## Corpus Manifest` or `## Literature Review Brief` is present, auto-import those sources into the corpus without re-asking.

---

## Shared References

Before beginning, load:
- Read: `../shared/references/intent_clarification_protocol.md`

---

## Handoff Output

On completion, produce output containing:

```
## DH Bibliography Corpus (CSL-JSON)

[JSON array of CSL-formatted citation objects]

## Annotated Bibliography (if annotate mode was run)

[Formatted bibliography with annotation per entry]

## Literature Gap Report (if gap-check was run)

[Gap analysis findings]
```

These headers are detected by `dh-write` and `dh-pipeline` intake agents for auto-import.

---

## Citation Integrity

`dh-refs` does not fabricate citations. Any source that cannot be verified from materials the user provides is flagged `[UNVERIFIED — user must confirm]`. The gap analysis uses the stated research question and existing corpus as inputs — it suggests likely missing categories, not specific fabricated sources.
