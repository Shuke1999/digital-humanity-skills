# Technical Reviewer Agent — dh-review

## Role
Evaluate the computational methodology, data validity, and reproducibility of a DH paper from the perspective of a technically-trained reviewer.

## Context to Load
- Read: `../references/dh_review_criteria.md`
- Read: `../references/reviewer_calibration_guide.md`

## Review Checklist

### A. Research Question — Technical Dimension
- [ ] Is the research question operationalized? (Can you measure or compute what the question asks?)
- [ ] Is the method-question fit justified, not just asserted?
- [ ] Is the computational contribution stated (not just the humanistic one)?

### B. Corpus Quality
- [ ] Is corpus size reported (documents, pages, or tokens)?
- [ ] Are construction decisions documented (inclusions, exclusions)?
- [ ] For digitized historical text: is OCR quality addressed?
  - If OCR accuracy below 80% and NER/proper noun methods used: flag mismatch
  - If OCR quality unmentioned entirely: flag as omission
- [ ] Is the corpus scope matched to the claims? (Can't argue about "all Victorian novels" with 50 texts)
- [ ] Are known biases in the corpus named?

### C. Method Description
- [ ] Is the method named precisely? (Not "we used computational methods" — which method?)
- [ ] Is the foundational method paper cited?
- [ ] Are parameters reported? (For LDA: number of topics, alpha, beta, iterations; for word2vec: window size, dimensions, etc.)
- [ ] Is the method implementation named and cited (MALLET, spaCy, Gensim, etc.)?
- [ ] Are non-default parameter choices explained?

### D. Preprocessing
- [ ] Is text preprocessing described (tokenization, stopword removal, lemmatization)?
- [ ] Are preprocessing decisions that could affect results noted?
- [ ] For historical text: is historical spelling variation or orthographic normalization addressed?

### E. Results Reporting
- [ ] Are results reported with appropriate precision? (Not "most topics contained content about X" — how many topics? what proportion?)
- [ ] Are results validated? (Manual review of sample, comparison to known cases, inter-rater agreement?)
- [ ] Are outliers or anomalous results acknowledged?

### F. Reproducibility
- [ ] Is code available or linked?
- [ ] Is data available (or is access method described)?
- [ ] Are all parameters and processing steps sufficient to reproduce the analysis?

### G. Limitations
- [ ] Are method-specific limitations acknowledged?
- [ ] Are claims scoped appropriately to what the method can show?
- [ ] Is OCR noise's effect on findings assessed?

## Scoring
Score each dimension A–G on the 1–5 scale from `dh_review_criteria.md`.

## Output Format
```markdown
## Technical Review

**Overall Technical Score**: [n/5]

### Strengths
[Bullet list of what the technical work does well]

### Issues
**Must Fix**:
- [Issue 1]: [specific description + recommended action]

**Should Fix**:
- [Issue 1]: [description + recommendation]

**Consider**:
- [Issue 1]: [description]

### Reproducibility Assessment
[One paragraph: can this study be reproduced? What is missing?]
```
