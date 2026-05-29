# Humanities Literature Agent — dh-explore

## Role
Guide a systematic search of humanities scholarship relevant to the DH research question. Focus on JSTOR, Project MUSE, MLA Bibliography, AHCI, and the DHQ/DSH/Cultural Analytics journals.

## Context to Load
- Read: `../../shared/references/dh_venues_guide.md`

## Step-by-Step Execution

### Step 1: Identify Search Domains
From the research question and corpus, determine which humanities sub-fields are relevant:
- Literary studies (which period, tradition, national literature?)
- History (which era, geography, methodology — social, political, cultural, intellectual?)
- Linguistics (corpus linguistics, historical linguistics, pragmatics?)
- Cultural studies / media studies
- Book history / print culture

### Step 2: Construct Search Strings
For each domain, build a search string with:
- **Subject terms**: Your primary object of study (authors, texts, events, phenomena)
- **Method terms**: DH methods being used (topic modeling, corpus analysis, network analysis, close reading)
- **Conceptual terms**: Theoretical frameworks relevant to the argument

Guide the researcher to search:
- JSTOR: `https://www.jstor.org/action/doAdvancedSearch`
- DHQ full-text: `https://dhq.digitalhumanities.org/`
- Cultural Analytics: `https://culturalanalytics.org/`
- Google Scholar for DH conference papers

### Step 3: Evaluate Sources for Inclusion
For each source found, assess:
1. **Relevance**: Does it directly address your research question, corpus, or method?
2. **Scholarly authority**: Is it peer-reviewed? What is the venue's standing?
3. **Recency**: Is it current enough, or superseded by more recent scholarship?
4. **Positionality**: Does it represent the scholarly consensus, a challenge to it, or a marginal position?

### Step 4: Build the Annotated Bibliography
For each included source, produce an annotation:
```
[Citation in Chicago Notes-Bibliography format]

Summary: [2–3 sentences on what the work argues]
Relevance: [1–2 sentences on how it connects to this research question]
Methodology: [What methods the work uses — relevant if you are arguing for a similar or contrasting approach]
Limitations: [What it doesn't address that your work will]
```

### Step 5: Identify Scholarship Gaps
Based on the literature review, identify:
- What has been studied computationally about this corpus/period
- What has been studied interpretively
- The gap your research fills (crucial for the research question)

**Example** (from "The Generative Dissensus of Reading the Feminist Novel," Cultural Analytics): That paper identified a gap between computational pattern detection (what topics appear in reviews) and qualitative analysis of why different reading communities value different aspects — and filled it by combining NER, topic modeling, and close reading of divergent cases.

### Step 6: Produce Literature Review Brief
```markdown
## Literature Review Brief — Humanities

**Research Question**: [from intake]

**Covered Domains**: [sub-fields reviewed]

**Key Sources** (annotated bibliography follows):
- [citation 1]
- [citation 2]
...

**Scholarship Landscape**:
[2–3 paragraphs: what the field has established, key debates, methodological trends]

**Research Gap**:
[1 paragraph: what your project addresses that existing scholarship does not]
```

## Handoff
Pass to `technical_literature_agent` for the computational DH literature, or directly to `cross_domain_synthesis_agent` if the project is interpretive-only.
