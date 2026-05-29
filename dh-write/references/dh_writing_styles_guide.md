# DH Writing Styles Guide

## The Two Writing Traditions in DH

DH work spans two distinct prose traditions. Knowing which one your venue expects — and how to navigate hybrid papers — is as important as knowing your argument.

---

## Humanities Prose

**Characteristics**:
- Argument driven by interpretation and evidence; no "results" section
- First person is often accepted; author's interpretive voice is visible
- Dense citation; engagement with scholarly conversation is performed on the page
- Claims are qualified, hedged, and situated in relation to prior scholarship
- Evidence is quoted, close-read, and contextualized rather than statistically summarized
- Long-form paragraphs; no bullet lists or section headers in body text (in traditional venues)

**Structure** (humanities essay / DHQ-style):
1. Introduction — situation, problem, argument claim
2. Background — scholarly context, prior work, theoretical framework
3. [2–4 thematic sections] — evidence, interpretation, argument development
4. Conclusion — what has been established, implications, limits

**Tone**: Confident but qualified. "This suggests" not "This proves." "I argue" not "The data shows."

---

## Technical/Computational Prose (DH variant)

**Characteristics**:
- IMRAD-adjacent: Introduction, Methods, Results, Discussion
- Methodology described with enough precision for reproducibility
- Quantitative results reported with appropriate statistics
- Claims grounded in dataset characteristics and method limitations
- Often includes tables, figures, code snippets

**Structure** (Cultural Analytics / DSH-style):
1. Introduction — research question, contribution, paper structure
2. Related Work — prior computational + humanistic literature
3. Data — corpus description, preprocessing, quality notes
4. Methods — computational method, parameters, implementation
5. Results — quantitative findings
6. Discussion — interpretation of results; humanistic significance
7. Conclusion

**Tone**: Precise and hedged differently — "The model identified X clusters; we interpret cluster 3 as representing Y."

---

## Hybrid DH Prose (Most Common)

The most effective DH papers weave both styles. Typical pattern:
- Introduction and Conclusion: humanities argumentative prose
- Methods and Results: technical precision
- Discussion: interpretive prose explaining what the computation means for the humanistic argument

**Example** (Cultural Analytics, Nagasaki smuggling networks): The introduction poses a historical question in humanistic terms; the methods section describes network construction precisely; the discussion interprets centrality measures in terms of historical power and agency; the conclusion makes an argument about early modern trade criminality.

---

## Choosing Your Style

| If writing for... | Use... |
|---|---|
| DHQ | Humanities prose with methods section |
| DSH | IMRAD-adjacent with interpretive discussion |
| Cultural Analytics | Technical methods + interpretive discussion |
| DH2024 conference abstract | 300–500 words; hybrid; state method and contribution |
| Dissertation chapter | Depends on committee; ask advisor; default to humanities |
| Research proposal | Humanities intro + technical methods plan |
| Close-reading essay | Pure humanities prose |

---

## Transition Phrases for Hybrid Writing

**From computation to interpretation**:
- "These patterns suggest that..."
- "We interpret this clustering as evidence of..."
- "The computational finding is consistent with the historical argument that..."
- "The algorithm identifies X; the humanistic significance of X is..."

**From interpretation back to evidence**:
- "This interpretive claim is supported computationally by..."
- "The quantitative results substantiate the claim that..."
- "To test this interpretation, we examined..."

---

## Hedging Vocabulary

Required when computational methods are used on imperfect historical corpora:

- "OCR noise in the corpus may affect [specific analysis]; we estimate character accuracy at [X]% based on [sampling method]"
- "Topic modeling identifies statistical co-occurrence patterns, not historical causation"
- "Our corpus over-represents [X]; conclusions should not be generalized to [broader domain]"
- "Named entity recognition on pre-correction OCR text has reduced recall for proper nouns"
