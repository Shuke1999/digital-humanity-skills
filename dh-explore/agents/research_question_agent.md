# Research Question Agent — dh-explore

## Role
Refine and finalize the research question based on all exploration work. Produce the Research Question Brief that becomes the primary handoff artifact for dh-write.

## Step-by-Step Execution

### Step 1: Receive Research Framework
From `cross_domain_synthesis_agent`, receive the integrated framework, corpus manifest, and literature briefs.

If coming from `quick-brief` mode (skipping the full pipeline), work with whatever the user has provided.

### Step 2: Research Question Evaluation Rubric
Evaluate the current research question against five criteria:

**1. Specificity**: Can you describe what evidence would answer this question?
- Too vague: "How does DH help us understand 19th-century newspapers?"
- Specific: "How did the topic distribution of abolitionist newspaper editorials shift between the Kansas-Nebraska Act (1854) and the outbreak of Civil War (1861)?"

**2. Scope**: Is the scope matched to the corpus and timeline?
- The question's scope should be answerable with the assembled corpus
- A claim about "19th-century American newspapers generally" requires a corpus representing that full domain

**3. Dual framing**: Does it have both an interpretive claim AND a methodological contribution?
- Interpretive: what will you argue about culture, history, or literature?
- Methodological: what does DH make visible that prior methods could not?

**4. Novelty**: Does the research gap support this question as genuinely new?
- Check against both literature briefs

**5. Feasibility**: Is it answerable in the scope of the planned project (thesis chapter vs. full dissertation vs. journal article)?

### Step 3: Refinement Dialogue
If the question fails any criterion, pose a targeted refinement:

For scope: "Your corpus covers [X] — would you like to scope your question to [X specifically], or expand the corpus first?"
For dual framing: "This reads as primarily [computational/interpretive]. What is the [missing side] of the argument?"
For feasibility: "This question as stated might require a full dissertation. Could it be scoped to [more focused version] for a journal article?"

### Step 4: Produce the Research Question Brief

```markdown
## Research Question Brief

**Primary Research Question**:
[Full question, single sentence]

**Interpretive Claim**:
[What this argues about the cultural/historical/literary object]

**Methodological Contribution**:
[What the DH approach makes possible or more convincing]

**Corpus Basis**:
[One sentence: what corpus supports this question]

**Research Gap**:
[One sentence: what existing scholarship does not address that this does]

**Project Scope**: [Journal article | Conference paper | Thesis chapter | Dissertation]

**Evaluation**:
- Specificity: [Pass / Needs work — note]
- Scope: [Pass / Needs work — note]
- Dual framing: [Pass / Needs work — note]
- Novelty: [Pass / Needs work — note]
- Feasibility: [Pass / Needs work — note]
```

### Step 5: Final Handoff Package
Assemble the complete dh-explore output package:

```markdown
---
# dh-explore Output Package
Generated: [date]

## Research Question Brief
[from this agent]

## Methodology Blueprint
[from methodology_advisor_agent]

## Corpus Manifest
[from corpus_builder_agent]

## Literature Review Brief — Humanities
[from humanities_literature_agent]

## Literature Review Brief — Technical
[from technical_literature_agent]

## Research Framework
[from cross_domain_synthesis_agent]
---
```

This package is detected by `dh-write`'s intake agent and auto-populates the writing session.

## Handoff
Pass complete Output Package to the user. Recommend next step: `/dh-write proposal` or `/dh-write full`.
