# Primary Source Criticism Protocol

## Overview

Primary source criticism is the humanistic practice of evaluating a source's authenticity, reliability, and suitability for scholarly use before incorporating it into a research argument. In DH, this practice must be extended to cover the digital mediation of the source.

---

## The Two-Layer Criticism Framework

Every digital primary source has two layers that must be evaluated independently:

### Layer 1: The Original Document
Standard historical/literary criticism:
1. **Authorship**: Who created this? Is authorship verified or attributed?
2. **Date**: When was it created? Is the date confirmed or estimated?
3. **Authenticity**: Is this the genuine artifact, or a copy, forgery, or later reproduction?
4. **Provenance**: Where has this document been? What is its custody chain?
5. **Bias**: What perspective does this source represent? Whose voices are absent?
6. **Context**: What was the social/political/cultural context of production?

### Layer 2: The Digital Object
DH-specific criticism:
1. **Digitization source**: Which institution digitized this, and when?
2. **OCR quality**: What is the character accuracy rate? (See thresholds in `dh_methodology_spectrum.md`)
3. **Completeness**: Is the digital version complete, or are pages/sections missing?
4. **Alteration**: Was the original document altered during digitization (cropping, contrast, transcription errors)?
5. **Rights and access**: What license governs the digital object? Does it match the original's rights status?
6. **Persistence**: Is the URL stable? Is there a persistent identifier (DOI, ARK, Handle)?

---

## OCR Quality Assessment in Practice

From "Mining for the Meanings of a Murder: The Impact of OCR Quality on the Use of Digitized Historical Newspapers" (DHQ):

> "One newspaper's scans yielded only 65% accuracy, and the substantial labor required to improve accuracy meant these scans were too poor to incorporate."

**Assessment workflow:**
1. Request a sample of ~100 words from the corpus
2. Manually verify against a high-quality scan or physical source
3. Calculate character error rate (CER): `(substitutions + insertions + deletions) / total characters`
4. Accuracy = 1 - CER
5. Classify by usability tier (see methodology spectrum)
6. Document method used (`manual_sample`, `reported_by_archive`, etc.) in the primary source entry

**Common OCR failure modes in historical text:**
- Long s (ſ) misread as f
- Ligatures (æ, œ) broken or replaced
- Typeface-specific degradation (blackletter, script fonts)
- Water damage / foxing / marginalia interference
- Column boundary errors in newspaper layout
- Hyphenation at line breaks creating phantom words

---

## Provenance Hierarchy

For DH research, prioritize sources in this order when multiple digitizations exist:

1. **Original physical document** (if accessible)
2. **Archival microfilm scan** (pre-digital; generally high quality)
3. **Institutional digitization** (library/archive with documented quality standards)
4. **Crowd-sourced transcription** (Wikisource, Transcribe Bentham) — verify against original
5. **Commercial digitization** (Google Books, subscription databases) — check rights and quality
6. **Unknown origin scans** — use only with explicit provenance caveat

---

## Primary Source Entry Checklist

Before adding a source to the corpus, complete these fields in the primary source entry schema:

- [ ] `title` and `source_type` set
- [ ] `repository.name` and `repository.url` recorded
- [ ] `repository.item_id` (persistent identifier) recorded
- [ ] `date_range` verified against scholarly consensus
- [ ] `language` confirmed
- [ ] `digitization.ocr_accuracy_estimate` recorded (or `unknown` with note)
- [ ] `digitization.ocr_accuracy_method` documented
- [ ] `rights.copyright_status` verified
- [ ] `usability_assessment` set based on OCR threshold table
- [ ] `provenance_notes` completed for any authenticity questions
- [ ] Decision to include or exclude documented with reason

---

## Worked Example: 19th-Century Abolitionist Newspapers

Using Chronicling America's collection of abolitionist-era newspapers as a corpus:

1. **Layer 1 criticism**: These newspapers have known editorial bias (pro-abolition) — appropriate for research on abolitionist rhetoric; not representative of the broader press
2. **Layer 2 criticism**: Chronicling America OCR for pre-1865 papers is typically 75–85% accurate; column boundaries often misaligned
3. **Usability**: Suitable for keyword-in-context, frequency analysis, and LDA topic modeling — but proper noun recognition (NER) will require post-correction
4. **Rights**: All pre-1928 content is US public domain; Chronicling America's metadata is CC0

This is the primary use case for the `historical-agent` codebase in this repository.
