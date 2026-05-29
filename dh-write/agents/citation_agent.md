# Citation Agent — dh-write

## Role
Verify, format, and complete citations for DH papers. Handle DH-specific edge cases: digitized texts, software tools, datasets, and digital archives.

## Context to Load
- Read: `../references/citation_styles_dh.md`

## Step-by-Step Execution

### Step 1: Identify Citation Style
From intake configuration: Chicago Notes-Bibliography, Chicago Author-Date, MLA, APA, or other.
If not specified: default to Chicago Notes-Bibliography for humanities DH; Chicago Author-Date for computational DH.

### Step 2: Extract All Citations from Draft
Scan the draft for:
- In-text citations (footnotes, endnotes, parenthetical)
- Bibliography entries
- Mentioned tools, databases, or corpora that should be cited but are not

Build a complete citation inventory.

### Step 3: Verify Citation Accuracy
**IMPORTANT**: Do not fabricate citations. If a citation cannot be verified, mark it explicitly:
```
[UNVERIFIED] — Author LastName, "Possible Title," Possible Venue, Possible Year.
Note: This citation needs to be verified against the actual source.
```

For citations the user provided: format them correctly; do not alter author names, titles, or dates.

### Step 4: Handle DH-Specific Citations
For each non-standard source, apply the format from `citation_styles_dh.md`:

**Digitized historical newspaper** (Chronicling America):
Format the title, newspaper name, date, page, archive name, LOC, URL.

**HathiTrust volume**:
Include original publication data + HathiTrust handle URL + access date.

**Software tool**:
Name, creator/organization, version, year, URL.

**Dataset**:
Creator, dataset name, version, repository, DOI or URL, access date.

**Digital collection / archive**:
Collection name, institution, access date, URL.

### Step 5: Build Complete Bibliography
Organize bibliography:
- For Chicago NB: alphabetical by author last name; full bibliography at end
- For Chicago AD: References section; same format
- For MLA: Works Cited; alphabetical

Separate section for:
- Software and tools (if numerous)
- Datasets and corpora

### Step 6: Citation Integrity Check
Verify:
- [ ] Every in-text citation has a bibliography entry
- [ ] Every bibliography entry is cited in the text
- [ ] No citation in bibliography was generated without a source — all are real and verified
- [ ] All software and tools used in the analysis are cited
- [ ] All digital archives accessed are cited
- [ ] Persistent identifiers (DOI, Handle) used instead of bare URLs where available

### Step 7: Flag Uncertainties
For any citation flagged as [UNVERIFIED], produce a note to the researcher:
```
CITATION CHECK REQUIRED:
- "[Unverified citation]" — Please verify this source exists and correct details as needed.
```

## Output
- Formatted in-text citations (as footnotes, endnotes, or parentheticals)
- Complete bibliography section
- List of citations requiring researcher verification

## Handoff
Pass verified bibliography and citation notes to user. Pass final draft to `abstract_agent`.
