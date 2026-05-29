# Reviewer Calibration Guide

## Purpose

Different DH venues weight technical and humanistic contributions differently. This guide calibrates the review emphasis for each venue type so the review simulation matches what a real reviewer at that venue would prioritize.

---

## Venue Calibration Presets

### DHQ (Digital Humanities Quarterly)
**Balance**: 35% technical / 65% humanistic
**Technical reviewers look for**:
- Methodology is clearly described (not necessarily deeply technical)
- Corpus construction decisions are justified
- Computational claims are not overstated
- Tools and methods are cited

**Humanistic reviewers look for**:
- Argument is humanistically significant (not just "we applied X to Y")
- Prior scholarship engaged seriously
- Interpretive claims supported by evidence
- Writing quality meets humanistic prose standards

### DSH — Digital Scholarship in the Humanities (Oxford)
**Balance**: 55% technical / 45% humanistic
**Technical reviewers look for**:
- Method is reproducible
- Parameters reported
- Results include appropriate statistical context
- Comparison to baselines or prior work

**Humanistic reviewers look for**:
- Research question matters to the humanistic field
- Findings are interpreted, not just reported
- The paper "so what" is clear

### Cultural Analytics
**Balance**: 65% technical / 35% humanistic
**Technical reviewers look for**:
- Rigorous quantitative methods
- Code/data availability (strong expectation)
- Clear operationalization of humanistic concepts
- Statistical validity

**Humanistic reviewers look for**:
- The computational analysis illuminates something genuinely important about culture/literature/history
- Not reducible to pure method paper

### ADHO DH Conference (Long Paper)
**Balance**: 50% technical / 50% humanistic
**Mixed DH community review**: reviewers may come from either tradition
- Method must be intelligible to humanists
- Argument must be legible to technical reviewers
- Contribution to DH community must be stated explicitly

### Dissertation (Committee Review)
**Balance**: varies by committee composition; ask the researcher
- If committee includes both humanists and a computational DH member: 50/50
- Humanistic committee with one DH member: 30% technical / 70% humanistic
- Computational DH committee: 60% technical / 40% humanistic

---

## Review Weight Adjustments

Ask the researcher before running the review:
1. What is the target venue?
2. Who are the likely reviewers (humanists? computational DH specialists? mixed?)
3. What feedback do they most need? (Argument? Methods? Writing?)

Use this to weight the review simulation accordingly.

---

## Common DH Review Failure Modes

These are the issues that most often lead to rejection or major revision at DH venues:

| Failure Mode | Typical Venue | Reviewer Comment |
|---|---|---|
| No humanistic argument | All venues | "What does this mean? Why does it matter?" |
| Method without question-fit | All | "Why was this method chosen over alternatives?" |
| Corpus construction undocumented | Technical | "The corpus construction is opaque and unrepeatable" |
| OCR quality unaddressed | All | "The authors do not discuss the quality of their digitized sources" |
| Tools uncited | All | "Software tools must be cited" |
| Computation reported but not interpreted | Humanistic | "The results section lacks interpretive engagement" |
| Interpretive claims unsupported | Technical | "The authors claim X but the data shows Y" |
| Missing literature (humanities) | DHQ, DSH | "Significant scholarship on [topic] is not engaged" |
| Missing literature (computational) | CA, DSH | "Prior computational work on this type of corpus is not discussed" |
