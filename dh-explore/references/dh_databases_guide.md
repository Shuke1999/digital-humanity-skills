# DH Databases and Digital Archive Guide

## Primary Source Archives

### Chronicling America (Library of Congress)
- **URL:** https://chroniclingamerica.loc.gov/
- **Content:** US newspapers, 1770–1963; ~20 million pages
- **Access:** Free; full-text search; API available (no key required)
- **API:** `https://chroniclingamerica.loc.gov/search/pages/results/?format=json&...`
- **OCR:** Variable; 19th-century papers range from 70–90% accuracy
- **License:** Public domain
- **Best for:** US newspaper history, political discourse, social history

### HathiTrust Digital Library
- **URL:** https://www.hathitrust.org/
- **Content:** 17+ million volumes; books, journals, government docs
- **Access:** Full-text search free; bulk download via Data Capsule (researcher registration required)
- **API:** HathiTrust Data API (bibliographic + page-level)
- **OCR:** Generally high quality for 20th-century materials; older texts variable
- **Best for:** Book history, literary corpora, large-scale text analysis

### Europeana
- **URL:** https://www.europeana.eu/
- **Content:** 50+ million European cultural heritage objects (text, image, audio, video)
- **Access:** Free; REST API (free API key)
- **API:** `https://api.europeana.eu/record/v2/...`
- **License:** Mixed (CC, public domain, rights reserved — check per item)
- **Best for:** European history, multi-language corpora, visual culture

### DPLA (Digital Public Library of America)
- **URL:** https://dp.la/
- **Content:** 44+ million items from US libraries, archives, museums
- **Access:** Free; API key required (free)
- **API:** `https://api.dp.la/v2/...`
- **Best for:** US history, regional archives, diverse collections

### Internet Archive
- **URL:** https://archive.org/
- **Content:** Texts, software, audio, video, web archives; millions of items
- **Access:** Free; download via direct URL or Archive.org APIs
- **OCR:** Tesseract-based; quality variable
- **Best for:** Out-of-print books, historical audio/video, web history

### Gallica (Bibliothèque nationale de France)
- **URL:** https://gallica.bnf.fr/
- **Content:** 7+ million French-language documents; newspapers, manuscripts, maps
- **Access:** Free; API available (IIIF-compliant)
- **Best for:** French history, Romance literature, colonial archives

### British Newspaper Archive
- **URL:** https://www.britishnewspaperarchive.co.uk/
- **Content:** 60+ million British newspaper pages, 1700s–2000s
- **Access:** Subscription required (findmypast.co.uk partnership)
- **Best for:** British history, press history

### Trove (National Library of Australia)
- **URL:** https://trove.nla.gov.au/
- **Content:** Australian newspapers, books, images, maps
- **Access:** Free; API available (free key)
- **Best for:** Australian history, Pacific history, British colonial history

### Eighteenth Century Collections Online (ECCO)
- **Content:** 180,000+ English-language titles, 1701–1800
- **Access:** Institutional subscription required (Gale)
- **OCR:** Known quality issues; see "Quantifying the impact of dirty OCR on historical text analysis" (DSH)
- **Best for:** 18th-century English literature and history

---

## Humanities Literature Databases

### JSTOR
- **URL:** https://www.jstor.org/
- **Access:** Institutional subscription; some open access via "Access to Research"
- **Coverage:** 12+ million academic articles; strong humanities coverage
- **API:** JSTOR Data for Research (DfR) — bulk data for text analysis

### Project MUSE
- **URL:** https://muse.jhu.edu/
- **Access:** Institutional subscription
- **Coverage:** Humanities and social science journals, especially North American

### MLA International Bibliography
- **Access:** Institutional subscription (via ProQuest or EBSCOhost)
- **Coverage:** Literature, linguistics, film, folklore; 3+ million records

### AHCI (Arts & Humanities Citation Index)
- **Access:** Web of Science (institutional)
- **Coverage:** Citation tracking for humanities journals

---

## Technical DH Literature

### ACM Digital Library
- **URL:** https://dl.acm.org/
- **Coverage:** Computer science, HCI; DH tools, interfaces, computational methods

### arXiv (cs.CL, cs.IR, cs.DL)
- **URL:** https://arxiv.org/
- **Relevant sections:** cs.CL (Computation and Language), cs.IR (Information Retrieval), cs.DL (Digital Libraries)
- **Access:** Free preprints

### DH Abstracts Library (ADHO Conference Proceedings)
- **URL:** https://dh-abstracts.library.virginia.edu/
- **Coverage:** All ADHO DH conference abstracts, searchable

---

## Database Selection by Sub-Field

| Sub-Field | Primary Databases |
|---|---|
| Literary studies | JSTOR, Project MUSE, MLA Bibliography, HathiTrust |
| History | Chronicling America, Gallica, Trove, DPLA, Europeana |
| Linguistics / corpus | BNC, ECCO, HathiTrust, arXiv cs.CL |
| Visual culture | Europeana, DPLA, Internet Archive |
| Media/press history | British Newspaper Archive, Chronicling America, Trove |
| Science / technology studies | arXiv, ACM DL, JSTOR |
