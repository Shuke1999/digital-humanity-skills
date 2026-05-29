# Citation Styles for Digital Humanities

## Default Style Selection

| Venue / Discipline | Default Style |
|---|---|
| DHQ, literary DH, historical DH | Chicago Notes-Bibliography (17th ed.) |
| DSH, corpus linguistics, computational DH | Chicago Author-Date or Oxford Notes |
| Cultural Analytics | APA or Chicago Author-Date |
| MLA journal | MLA 9th edition |
| Computer science / ACM | ACM citation style |
| General conference abstract | Follow conference instructions; Chicago if unspecified |

---

## Chicago Notes-Bibliography (DH Humanities Default)

### Standard Journal Article
Note: Firstname Lastname, "Article Title," *Journal Name* volume, no. issue (year): page–page, DOI.

Bibliography: Lastname, Firstname. "Article Title." *Journal Name* volume, no. issue (year): page–page. DOI.

### Standard Monograph
Note: Firstname Lastname, *Book Title: Subtitle* (City: Publisher, Year), page.

Bibliography: Lastname, Firstname. *Book Title: Subtitle*. City: Publisher, Year.

---

## DH-Specific Edge Cases

### Citing a Digitized Text (HathiTrust)
Note: Firstname Lastname, *Title* (City: Publisher, Year), HathiTrust Digital Library, accessed [date], https://hdl.handle.net/[handle].

If OCR quality is relevant to your use: add parenthetical "(OCR text; estimated character accuracy ~85%)"

### Citing a Newspaper Article from a Digital Archive (Chronicling America)
Note: "Article Title," *Newspaper Name* (City), Date, page, *Chronicling America: Historic American Newspapers*, Library of Congress, https://chroniclingamerica.loc.gov/lccn/[lccn]/[date]/ed-[ed]/seq-[seq]/.

Bibliography: "Article Title." *Newspaper Name* (City), Date, p. [page]. *Chronicling America: Historic American Newspapers*. Library of Congress. Accessed [date]. https://...

### Citing a Dataset
Note: Dataset Name, version [n.n], Creator/Institution, Year, repository, DOI.

Example: ECCO (Eighteenth Century Collections Online), Gale, accessed via institutional subscription, 2023.

If you bulk-downloaded: specify the download date and any filtering parameters used.

### Citing a Software Tool
Note: Tool Name, version [n.n], Creator/Organization, Year, URL.

Examples:
- Voyant Tools, Stéfan Sinclair and Geoffrey Rockwell, 2023, https://voyant-tools.org/
- MALLET (Machine Learning for Language Toolkit), Andrew Kachites McCallum, 2002, http://mallet.cs.umass.edu/
- spaCy, Explosion AI, version 3.7, 2023, https://spacy.io/
- AntConc, Laurence Anthony, version 4.2.0, 2023, https://www.laurenceanthony.net/software/antconc/

Cite tools as you would cite any instrument used in your analysis. Omitting tool citations is a common oversight in DH work.

### Citing an API or Digital Collection
Note: *Collection Name*, Institution, accessed [date] via [API/interface], URL.

Example: *Chronicling America: Historic American Newspapers*, Library of Congress, accessed June 2024 via JSON API, https://chroniclingamerica.loc.gov/

### Citing a Repository (Code / Data)
Note: Firstname Lastname, "Repository Name," platform, Year, DOI or URL.

Example: Creator Name, "Project Code Repository," GitHub, 2024, https://github.com/[user]/[repo].

If archived for reproducibility: use Zenodo DOI rather than GitHub URL.

---

## Methods Section Citation Patterns

When citing computational methods in the methods section:

**Topic Modeling (LDA)**:
> "We applied Latent Dirichlet Allocation (Blei, Ng, and Jordan 2003) using MALLET (McCallum 2002) with [n] topics, a Dirichlet α of [value], and [n] iterations."

**Word Embeddings**:
> "Word2Vec embeddings (Mikolov et al. 2013) were trained on the preprocessed corpus using the skip-gram architecture with a window size of [n]."

**Named Entity Recognition**:
> "Named entities were extracted using spaCy's en_core_web_lg model (Honnibal and Montani 2017). Given the OCR noise in our corpus, recall for proper nouns may be underestimated."

---

## Common Citation Errors in DH Work

1. **Citing "Google Books" as the source** when HathiTrust or the original archive holds the canonical copy — cite the archive
2. **Citing a Wikipedia article** instead of the primary source it references
3. **Omitting tool citations** — Voyant, NLTK, and similar tools must be cited
4. **Citing the repository URL** instead of a persistent identifier (DOI, ARK, Handle) — URLs rot
5. **No access date for web resources** — required for all online sources in Chicago style
6. **Citing a corpus without specifying version** when the corpus has changed over time (ECCO, JSTOR DfR)
