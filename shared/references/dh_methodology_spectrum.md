# DH Methodology Spectrum

Digital humanities research occupies a continuum between two poles. Neither is superior — the research question determines the appropriate position.

## The Spectrum

```
COMPUTATIONAL (Technical Pole)              INTERPRETIVE (Humanistic Pole)
─────────────────────────────────────────────────────────────────────────
Corpus-scale analysis                       Single-text close reading
Quantitative pattern detection              Qualitative meaning-making
Reproducible / algorithmic                  Interpretive / argumentative
Tool-mediated                               Scholar-mediated
Statistical significance                    Interpretive salience
Distant reading (Moretti)                   Close reading
```

## Deciding Where to Sit

### Choose computational-leaning when:
- Your evidence base is 100+ documents
- You are looking for patterns, trends, or anomalies across a corpus
- Your claims require statistical support
- The humanistic question can be operationalized (e.g. "authorship attribution", "sentiment shift over time")
- Reproducibility is important for your venue (CHI, CSCW, ACL-DH tracks)

### Choose interpretive-leaning when:
- You are arguing for the meaning of a specific text, artifact, or historical moment
- The evidence is qualitative, contextual, or archival
- Your claim cannot be operationalized without distorting it
- Your venue is a humanities journal (DHQ, New Literary History, Representations)

### The DH Sweet Spot (Hybrid):
Most strong DH work uses computation to generate a finding and interpretation to explain why it matters.

**Example pattern** (from "How Network Analysis Uncovers International Networks of Smuggling History," Cultural Analytics 2023):
1. Build network graph from archival records
2. Apply network metrics (centrality, clustering)
3. Use humanistic historical analysis to interpret what the network structure means about power and criminality

**Example pattern** (from "The Generative Dissensus of Reading the Feminist Novel," Cultural Analytics):
1. Collect interpretive communities (MLA Bibliography, Amazon, Goodreads)
2. Apply topic modeling + NER to each corpus
3. Close-read the divergences to argue about how literary canons form

## Common Methodological Errors

| Error | Description |
|-------|-------------|
| Computational determinism | Treating statistical output as self-evident truth without interpretation |
| Interpretive isolationism | Ignoring available computational evidence that could ground or challenge claims |
| Method-first research | Choosing a method (e.g. topic modeling) and finding a dataset to fit it |
| Unexamined corpus construction | Treating a digitized archive as neutral rather than as itself a scholarly artifact |
| OCR opacity | Using a noisy digitized corpus without disclosing or analyzing OCR error rates |

## OCR Quality Thresholds (for historical corpus work)

Derived from "Mining for the Meanings of a Murder" (DHQ) and "Quantifying the impact of dirty OCR on historical text analysis" (DSH):

| OCR Accuracy | Usability |
|---|---|
| 95%+ | Full text mining, NER, topic modeling |
| 85–94% | Text mining viable; NER and proper noun detection degraded |
| 70–84% | Keyword-in-context, frequency counts viable; model fine-tuning needed |
| 65–69% | Marginal; substantial pre-processing required |
| <65% | Generally unusable for computational analysis without major OCR correction |

When OCR accuracy is unknown, disclose this as a methodological limitation and estimate from a sample.
