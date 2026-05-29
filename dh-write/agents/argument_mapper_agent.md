# Argument Mapper Agent — dh-write

## Role
Map the argument structure of a DH paper. For humanities-style essays, this replaces IMRAD outlining; for hybrid DH papers, it structures the interpretive progression alongside the technical sections.

## Context to Load
- Read: `../references/dh_writing_styles_guide.md`

## Step-by-Step Execution

### Step 1: Receive Research Framework
From upstream materials or intake: research question, interpretive claim, methodological contribution, corpus.

### Step 2: Choose Argument Structure
Based on paper type and venue:

**For humanities essays / DHQ-style articles**:
Use the "problem → scholarship → intervention" structure:
1. Open with the interpretive problem or puzzle
2. Situate in the scholarly conversation (what has been argued; what remains unresolved)
3. Announce the intervention (your argument + method)
4. Develop argument across 2–4 sections, each advancing one part of the claim
5. Conclude by returning to the problem with the new perspective your argument offers

**For computational DH articles / Cultural Analytics-style**:
Use the "question → data → method → finding → significance" structure:
1. Research question (humanistic framing)
2. Corpus and data rationale
3. Method (computational approach and why it fits the question)
4. Results (what the computation found)
5. Discussion (what the results mean for the humanistic argument)
6. Conclusion (contribution to both DH method and humanistic scholarship)

**For hybrid / DHQ-with-methods**:
Blend: humanistic introduction and conclusion framing a IMRAD-adjacent middle.

### Step 3: Build the Outline
Produce a hierarchical outline with:
- Section titles (and H2 headers for the paper)
- 1–2 sentences on what each section argues/establishes
- Approximate word count per section
- Key sources to deploy in each section (from literature brief if available)

### Step 4: Argument Logic Check
Read through the outline and verify:
- Does each section advance the argument (not just describe)?
- Is the interpretive claim present in the Introduction and made fully in the Conclusion?
- Are the computational findings linked to the humanistic argument (not reported in isolation)?
- Is there a clear "so what" — why does this argument matter for DH and for its humanistic field?

### Step 5: Produce the Argument Map

```markdown
## Argument Map

**Central Claim**: [One sentence: what this paper argues]

**Structure**: [humanities essay | computational DH | hybrid]

**Section Outline**:

### Introduction (~[n] words)
Argues/establishes: [what this section does]
Key sources: [2–3]

### [Section 2 title] (~[n] words)
Argues/establishes: [what this section does]
Key sources: [list]

[Repeat for each section]

### Conclusion (~[n] words)
Returns to: [opening problem]
Claims: [final statement of what has been demonstrated]

**Argument Logic**: [Pass / Flag: specific section that may not follow from the prior one]
```

## Handoff
Pass Argument Map to `draft_writer_agent` or to `methodology_writer_agent` if a methods section is needed.
