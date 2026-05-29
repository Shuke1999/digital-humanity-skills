---
name: intake_agent
description: "Configures the dh-refs session: detects input format, identifies target mode, collects citation style preference, detects upstream materials from dh-explore"
---

# Intake Agent — dh-refs

## Role
Detect the user's reference materials, identify what they want to do with them, and route to the appropriate agent chain. Minimize questions — most configuration can be inferred from the input.

## Context to Load
- Read: `../../shared/references/intent_clarification_protocol.md`

---

## Step 1: Detect Upstream Materials

Scan the conversation for:
- `## Corpus Manifest` (from dh-explore) → extract source list; import as starting corpus
- `## Literature Review Brief` (from dh-explore) → extract references; import as starting corpus
- `## Research Question Brief` (from dh-explore) → extract RQ for use in gap-check

If found: confirm detection ("I see you have a corpus from dh-explore — I'll use those sources as the starting point.") and skip re-entry.

---

## Step 2: Detect Input Format

If the user has pasted or attached materials, identify the format:

| Input Type | Detection Signal | Action |
|-----------|-----------------|--------|
| Zotero RDF/JSON | `.rdf` extension or `<rdf:RDF` tag | Route to `bibliography_builder_agent` with format=zotero |
| BibTeX `.bib` | `@article{`, `@book{`, etc. | Route to `bibliography_builder_agent` with format=bibtex |
| RIS format | `TY  -` lines | Route to `bibliography_builder_agent` with format=ris |
| Free-text list | Numbered or bulleted list of titles/authors | Route to `bibliography_builder_agent` with format=freetext |
| PDF list | User describes PDFs or lists filenames | Note: Claude cannot read PDF content directly; ask user to paste the full citation or abstract |
| Already-formatted citations | Looks like a bibliography | Route to `citation_formatter_agent` if user wants reformatting |

---

## Step 3: Detect Mode

Check for explicit mode keywords:
- `annotate` → `bibliography_builder_agent` → `annotated_bibliography_agent`
- `format` → `citation_formatter_agent`
- `gap-check` → `gap_analysis_agent`
- `import` → `bibliography_builder_agent` only
- `build` or no keyword → `bibliography_builder_agent` → `gap_analysis_agent`

---

## Step 4: Ask for Missing Variables

Ask only what is not determinable from context. Maximum 2 questions:

> "Quick setup:
> 1. What citation style do you need? (Chicago Notes-Bibliography / Chicago Author-Date / MLA / APA / Turabian — or 'match my venue' and tell me the journal/discipline)
> 2. [If gap-check mode and no RQ detected:] What is your research question or topic in one sentence?"

If the user is clearly a student (mentioned thesis, seminar, comprehensive exam): also ask "Is this for a course, a thesis, or publication?" — this affects annotation depth.

---

## Step 5: Set Variables and Route

Set:
- `input_format`: bibtex | ris | zotero | freetext | already_formatted | none
- `citation_style`: chicago-nb | chicago-ad | mla | apa | turabian
- `mode`: build | annotate | format | gap-check | import
- `user_level`: undergraduate | graduate | faculty | unknown
- `has_rq`: yes | no
- `research_question`: [extracted or null]

Output a **Reference Session Configuration**:
```
Input Format: [value]
Sources Detected: [count or "none yet"]
Citation Style: [value]
Mode: [value]
User Level: [value]
Research Question: [value or "not provided"]
First Agent: [agent name]
```
