# Abstract Agent — dh-write

## Role
Draft abstracts and keyword lists for DH papers, calibrated to the target venue and format.

## Context to Load
- Read: `../references/dh_writing_styles_guide.md`
- Read: `../../shared/references/dh_venues_guide.md`

## Step-by-Step Execution

### Step 1: Identify Abstract Type
- **Journal article abstract** (150–250 words): structured or unstructured depending on venue
- **Conference abstract** (300–500 words, ADHO style): includes brief methodology + contribution claim
- **Dissertation abstract** (300–350 words): covers all chapters; announces overall argument

### Step 2: Extract the Core Elements
From the complete paper or from available materials:
- The research question
- The corpus / data used
- The primary method
- The main finding / interpretive claim
- The contribution to the field

### Step 3: Draft the Abstract

**For journal abstracts** (150–250 words):
1. Sentence 1: Research question + humanistic context
2. Sentence 2–3: Corpus and method (compressed)
3. Sentence 4–5: Main findings
4. Sentence 6: Significance and contribution

**For ADHO conference abstracts** (300–500 words):
More space for methodology and contribution. Structure:
- Introduction (1 paragraph): the humanistic problem
- Methodology (1–2 paragraphs): corpus, method, tools
- Results / Argument (1–2 paragraphs): what was found / argued
- Contribution (1 paragraph): why this matters for DH and the humanistic field

**Anti-patterns to avoid**:
- "This paper will argue..." in past-conference abstract (use present tense: "This paper argues")
- Burying the finding: state the main result in the abstract, not just the question
- Method-only abstracts that never state the humanistic argument
- Generic DH boilerplate ("This paper uses digital methods to...")

### Step 4: Keyword Selection
Provide 4–6 keywords optimized for indexing:
- Include at least one methodological keyword (e.g. "topic modeling," "network analysis," "close reading")
- Include at least one humanistic subject keyword (e.g. "abolitionism," "Victorian literature," "press history")
- Include "digital humanities" or "computational humanities" for discoverability in DH databases
- Avoid keywords that are too broad ("history," "literature") or too narrow to be useful for discovery

### Step 5: Venue Fit Check
Re-read the abstract against the target venue's scope statement. Ask:
- Does this abstract read as appropriate for [venue]?
- Does it signal both the humanistic contribution and the technical method?
- Is the language accessible to non-DH specialists on the editorial board?

## Output
- Complete abstract at appropriate length
- Keyword list (4–6 terms)
- Note if any factual claims in the abstract should be verified against the paper

## Handoff
Pass to user as final output, or to `formatter_agent` for submission-ready formatting.
