# DH Ethics Protocol

## Overview

Digital humanities research involves unique ethical considerations at the intersection of computational methods and humanistic inquiry. This protocol outlines required checkpoints.

---

## 1. Data Provenance and Copyright

### Digitized Historical Collections
- Confirm the digitization source and its terms of use (HathiTrust, Europeana, Internet Archive, DPLA each have different conditions)
- Works published before 1928 (US) are generally public domain; international variation applies
- Digitized editions may carry new copyright claims on the digital object even if the underlying text is public domain
- When scraping or bulk-downloading, check `robots.txt` and API rate limits; respect institutional data agreements

### Living Subjects and Contemporary Collections
- If your corpus includes social media, contemporary interviews, or digital-born content by living people, IRB or ethics board review may be required
- Anonymize or pseudonymize where appropriate, especially for marginalized communities
- "Public data" is not automatically "ethical to analyze" — consider contextual integrity

### Indigenous and Community Archives
- Consult CARE Principles (Collective Benefit, Authority to Control, Responsibility, Ethics) for Indigenous cultural heritage materials
- Some materials have community-specific access restrictions even when technically digitized

---

## 2. Dataset and Model Ethics

### Training Data Provenance
- If using a language model or classifier, disclose what it was trained on and whether that training data included content similar to your corpus
- Document whether OCR models were trained on comparable historical typefaces/fonts

### Algorithmic Bias
- Statistical methods can amplify historical biases present in the archive
- Topic models may obscure marginalized voices if the corpus under-represents them
- Name it explicitly when it occurs; do not treat bias as a limitation to be buried in footnotes

---

## 3. Attribution and Citation

- Cite digitization sources as scholarly actors (archives, librarians, digitization projects) not just "the internet"
- Software tools used analytically (Voyant Tools, AntConc, MALLET, NLTK) must be cited
- Datasets used must be cited with version, access date, and persistent identifier where available

---

## 4. Reproducibility and Transparency

- Document corpus assembly decisions (what was excluded and why)
- Share code, parameter settings, and preprocessing decisions
- For historical corpora with OCR noise: disclose error rate estimates, any manual correction, and what impact errors may have had on findings

---

## 5. Ethics Gate Checklist (for dh-pipeline Stage 2.5)

Before proceeding past the proposal stage, confirm:

- [ ] Corpus materials are legally accessible for the intended use
- [ ] Copyright status of primary sources verified
- [ ] Data consent requirements assessed (IRB if applicable)
- [ ] Indigenous/community materials flagged and protocols identified
- [ ] OCR quality documented if applicable
- [ ] Attribution plan in place for archives, tools, datasets
- [ ] Known algorithmic biases named in the methodology
