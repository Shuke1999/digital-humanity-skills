# Citation Formats Guide — DH Context

Quick-reference for which citation style is expected in which DH venue, plus DH-specific edge cases.

---

## Style by Venue / Discipline

| Venue / Discipline | Preferred Style | Notes |
|---|---|---|
| Digital Humanities Quarterly (DHQ) | Chicago NB or author's preference | Check current author guidelines |
| Digital Scholarship in the Humanities (DSH) | Chicago AD or MLA | Oxford journal; check issue for style |
| Cultural Analytics | Chicago AD | Data-driven; author-date suits quantitative work |
| Literary and Linguistic Computing (LLC) | Chicago or MLA | Historical DHQ predecessor |
| Journal of the Text Encoding Initiative (JTEI) | Chicago NB | TEI-specific scholarship |
| Computers and the Humanities | MLA or Chicago | Now discontinued; historical reference |
| Digital Medievalist | Chicago NB | Medieval studies convention |
| Journal of Digital History | Chicago AD | Historical; author-date |
| Historical Methods | Chicago AD | Quantitative history |
| ADHO Conference Abstracts | Usually not specified | Use Chicago NB as safe default |
| DHd (German DH conference) | Chicago NB or German citation norms | |
| ACH (Association for Computers and the Humanities) | Flexible | |
| Literary studies journals (PMLA, ELH, Representations) | MLA | Standard literary studies |
| History journals (AHR, JAH, JMH) | Chicago NB | Standard history |
| Linguistics journals | APA or LSA format | |
| Dissertation / thesis | Check institutional guidelines | Many US institutions use Chicago or Turabian |
| Qualifying exam papers | Check program guidelines | Ask advisor |

---

## DH-Specific Edge Cases

### Citing a Digital Archive (General Collection)
When you're citing an archive as a resource (not a specific document within it):

*Chicago NB*: "Archive Name." Institution. URL. Accessed Month Day, Year.
*MLA*: *Archive Name*. Institution, URL. Accessed Day Month Year.

### Citing an Item Discovered via a Digital Archive
Cite the original document with the digital location as access information:

*Chicago NB*: Author (if known). "Document Description." Date of document. Collection Name, Box/Folder. Repository. Digitized by [Project]. URL.

### Citing a Wikipedia Article (Discouraged but sometimes necessary in DH tool discussions)
*Chicago NB*: Wikipedia, s.v. "Article Title," last modified Month Day, Year, URL.
Note: Not appropriate as a scholarly source; only cite for definitional or tool-description purposes.

### Citing an LLM Output (emerging norm, 2025–2026)
*Chicago NB*: [Model Name and version]. Response to "[abbreviated prompt]." Anthropic/OpenAI/etc., Month Day, Year.
Note: Institutional policies vary widely. Always check journal/program guidelines.

---

## Zotero → Citation Style Mapping

If the user is using Zotero:
- Zotero supports Chicago NB, Chicago AD, MLA, APA, and Turabian natively
- For export: use "Better BibTeX" plugin for `.bib` files; export as CSL-JSON for most flexibility
- Import workflow: File → Export Library → CSL JSON → paste into dh-refs session

---

## Common Mistakes in DH Citations

1. **Missing DOI** — Always include DOI for digital journal articles
2. **Wrong date format for Chicago** — Year after publisher, not after author name (NB vs AD confusion)
3. **Not citing the edition** — For digital editions (e.g., EEBO-TCP texts), cite the edition, not just the original author
4. **Incomplete archive citation** — Missing holding institution or collection name
5. **Undated software** — Always include version number and release year for software tools
6. **Dataset without DOI** — Use repository URL as fallback; note if DOI unavailable
