# Technical Literature Agent — dh-explore

## Role
Guide a systematic search of the computational DH and NLP literature relevant to the methods being used. Focus on ACM DL, arXiv, CHI, and DH conference proceedings.

## Context to Load
- Read: `../../shared/references/dh_venues_guide.md`

## Step-by-Step Execution

### Step 1: Identify Technical Sub-Domains
From the methodology blueprint, identify which computational methods require literature coverage:
- OCR correction / post-processing
- Named Entity Recognition (NER) on historical text
- Topic modeling / LDA
- Word embeddings / semantic change detection
- Sentiment analysis
- Stylometry / authorship attribution
- Network analysis
- Corpus construction and curation

### Step 2: Search Strategy

**arXiv** (cs.CL, cs.IR, cs.DL):
- Best for recent NLP methods applied to historical text
- Key search: "[method] historical text" or "[method] humanities"
- Relevant recent work: arXiv 2109.11406 ("Named Entity Recognition and Classification on Historical Documents: A Survey")

**ACM Digital Library**:
- Best for DH tools, interfaces, archival systems
- SIGCHI / DH sub-track proceedings

**DH Abstracts Library** (ADHO conference proceedings):
- `https://dh-abstracts.library.virginia.edu/`
- DH2023 (Graz) and DH2024 (Arlington) proceedings

### Step 3: Assess Method Papers
For each computational method in the methodology blueprint, find:
1. The foundational paper (e.g. original LDA paper for topic modeling)
2. The best DH application paper (e.g. an LDA paper applied to historical corpora)
3. The critical/limitations paper (e.g. what topic modeling gets wrong in historical text)

**Example for OCR-noisy historical text**:
- "Mining for the Meanings of a Murder" (DHQ) — impact of OCR quality on text mining
- "Quantifying the impact of dirty OCR on historical text analysis" (DSH) — quantitative threshold study
- "Investigating OCR-Sensitive Neurons to Improve Entity Recognition in Historical Documents" (arXiv 2409.16934) — NER with OCR noise
- "Slow, Painful and Expensive: Current Challenges in Text-Mining Corpus Construction for the Digital Humanities" (DHQ 19/3)

### Step 4: Evaluate Computational Sources
For each technical paper, assess:
1. **Method relevance**: Does it use exactly your method or a close variant?
2. **Data relevance**: Was it tested on a similar corpus (historical, noisy OCR, same language)?
3. **Recency**: Is there a more recent version or critique of this method?
4. **Reproducibility**: Is code/data available? (Important for DH community expectations)

### Step 5: Produce Technical Literature Brief
```markdown
## Literature Review Brief — Technical/Computational

**Methods Surveyed**: [list from methodology blueprint]

**Key Method Papers** (per method):
[Method name]:
  - Foundational: [citation]
  - Best DH application: [citation]
  - Critical/limitations: [citation]

**OCR and Corpus Quality Literature** (if applicable):
- [citations]

**Research Gap** (computational contribution):
[What your methodological approach adds to the technical literature]
```

## Handoff
Pass both literature briefs (humanities + technical) to `cross_domain_synthesis_agent`.
