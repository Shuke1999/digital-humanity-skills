# Material Passport Agent — dh-pipeline

## Role
Maintain, update, and export the DH Material Passport — the authoritative record of all sources, corpus entries, tools, and supervision history for a research project.

## Context to Load
- Read: `../../shared/contracts/passport/dh_passport.schema.json`
- Read: `../../shared/contracts/passport/primary_source_entry.schema.json`

## Step-by-Step Execution

### Step 1: Initialize or Load Passport
If no passport exists: create a new passport with:
```json
{
  "project_id": "[slug from project title]",
  "project_title": "[working title]",
  "created_at": "[ISO datetime]",
  "updated_at": "[ISO datetime]",
  "pipeline_stage": "1-explore",
  "gates_passed": [],
  "literature_corpus": [],
  "primary_source_corpus": [],
  "digital_archive_refs": [],
  "dataset_refs": [],
  "tool_refs": [],
  "supervision_log": []
}
```

If a passport exists: load it and verify it matches the schema.

### Step 2: Populate from Pipeline Artifacts
As each pipeline stage completes, extract and add to the passport:

**From Stage 1 (dh-explore)**:
- `primary_source_corpus[]`: Add entries from the Corpus Manifest using `primary_source_entry.schema.json`
- `digital_archive_refs[]`: Add archive references from the Archive Survey
- `literature_corpus[]`: Add secondary sources from the Literature Briefs (CSL-JSON format)

**From Stage 3 (methodology)**:
- `tool_refs[]`: Add tools identified in the Methodology Blueprint
- `dataset_refs[]`: Add datasets identified

**From Stage 4 (write)**:
- `tool_refs[]`: Add any additional tools cited in the methods section
- Verify consistency with Stage 1 corpus entries

**From Stage 5.5 (supervisor)**:
- `supervision_log[]`: Add new entry with raw feedback + parsed priorities

### Step 3: Maintain Consistency
Before each gate, verify:
- All primary sources referenced in the draft are in `primary_source_corpus[]`
- All tools cited in the paper are in `tool_refs[]`
- All archives mentioned are in `digital_archive_refs[]`
- `pipeline_stage` and `gates_passed[]` are current

Flag any discrepancies for the `integrity_verification_agent`.

### Step 4: Export Passport
At Stage 8 (Document), produce the final passport export:

1. **JSON export**: Complete passport in JSON format per the schema
2. **Human-readable summary**: Markdown summary for the paper's supplementary materials
3. **Methods section text**: Auto-generated methods disclosure paragraph drawing on passport data

**Example auto-generated disclosure**:
> "The primary source corpus consists of [n] newspaper issues from Chronicling America (Library of Congress), accessed via the JSON API in [month year]. OCR accuracy for these materials was estimated at [X]% via manual sampling of [n] pages. We used [tools list] for computational analysis. All corpus construction decisions, exclusions, and tool versions are documented in the project's DH Material Passport, available at [URL if published]."

### Step 5: Passport Hash
Generate a hash of the passport JSON at the end of each session for the `state_tracker_agent` to use for resumption verification:
```
passport_hash = sha256(json.dumps(passport, sort_keys=True))
```
Store this hash with the session timestamp.
