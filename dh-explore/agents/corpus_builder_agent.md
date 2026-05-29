# Corpus Builder Agent — dh-explore

## Role
Assemble, document, and justify the research corpus. Produce a Corpus Manifest that is the authoritative record of what is in the corpus, what is excluded, and why.

## Context to Load
- Read: `../references/primary_source_criticism_protocol.md`
- Read: `../../shared/references/dh_methodology_spectrum.md`

## Step-by-Step Execution

### Step 1: Receive Assessed Sources
From `primary_source_agent`, receive the list of primary sources with usability verdicts. Any source marked `unusable` is excluded. All others are candidates.

### Step 2: Corpus Design Decisions

**Scope**: Does the corpus cover the research question's full scope?
- Temporal coverage: are all relevant years/periods represented?
- Geographic coverage: are all relevant regions/publications included?
- Thematic coverage: does the corpus sample fairly across the phenomena being studied?

**Balance and Bias**: Is the corpus skewed in ways that would invalidate the research argument?
- If studying a social movement, does the corpus include opposition voices as well as movement voices?
- If studying regional variation, is each region proportionally represented?
- Are some voices systematically absent (non-English, non-print, oral traditions)?

**Size**: Is the corpus large enough for the chosen method?
- Topic modeling (LDA): typically 50–100 documents minimum; 500+ is better
- Word embeddings: 1 million+ tokens for reliable results
- Stylometry: depends heavily on method; Burrows's Delta needs ~5,000 words per text
- Close reading: no minimum — but close reading of 10,000 texts is not close reading

**Example** ("Slow, Painful and Expensive," DHQ 19/3): That article documents corpus assembly for text mining as requiring extensive manual labor — collecting rights permissions, cleaning OCR, resolving metadata inconsistencies — far more than typically acknowledged in published DH work.

### Step 3: Exclusion Documentation
For every excluded source, document the reason explicitly:
- OCR quality below threshold
- Rights restrictions prevent this use
- Incomplete digitization (missing issues/pages)
- Outside research scope
- Redundant with another included source

This documentation goes into the `exclusion_reason` field of the primary source entry and is available for the methods section.

### Step 4: Metadata Standardization
Ensure all corpus entries have consistent metadata:
- Date format: ISO 8601 (YYYY-MM-DD or YYYY for year-only)
- Language: BCP-47 code
- Geographic fields: consistent vocabulary (e.g. state abbreviations, or spelled out)
- Source type: controlled vocabulary from the primary source schema

### Step 5: Produce Corpus Manifest

```markdown
## Corpus Manifest

**Project**: [title]
**Assembled**: [date]

**Corpus Summary**:
- Total items included: [n]
- Total items excluded: [n]
- Date range covered: [start] to [end]
- Geographic scope: [description]
- Languages: [list]
- Total estimated tokens: [n] (if text corpus)

**Included Sources**:
| ID | Title/Identifier | Repository | Date | OCR Accuracy | Usability Tier |
|----|---|---|---|---|---|
| ... |

**Excluded Sources**:
| ID | Title/Identifier | Exclusion Reason |
|----|---|---|
| ... |

**Corpus Biases and Limitations**:
[Honest paragraph about what is missing or systematically skewed — required for methods disclosure]

**Recommended Disclosure** (for Methods section):
[Draft sentence for the paper's methods section explaining corpus construction decisions]
```

## Handoff
Pass the Corpus Manifest + methodology blueprint + research question to `cross_domain_synthesis_agent`.
