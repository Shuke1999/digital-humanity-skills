# Grant Templates Guide — DH Funders

Reference for the `proposal_architect_agent` when operating in `grant-proposal` mode.

---

## NEH Digital Humanities Advancement Grant (DHAG)

**Funder**: National Endowment for the Humanities (US)  
**URL**: neh.gov/grants/odh/digital-humanities-advancement-grants  
**Amounts**: Tier 1: $30k–$75k / Tier 2: $75k–$150k / Tier 3: $150k–$350k  
**Typical project types**: New tool or method development; archival digitization with scholarly framework; DH pedagogy; open-access resource creation

### Required Narrative Sections (in order)

1. **Project Summary** (~150 words)
   - One paragraph describing the project, its significance, and how it advances DH
   - Must be in plain, accessible language (reviewers include non-specialists)

2. **Narrative** (typically 10–15 pages)
   - **Intellectual Significance**: Why does this project matter to humanities scholarship?
   - **Research and Development Questions**: What problems does the project address?
   - **Environmental Scan**: What comparable projects exist? Why is this one necessary?
   - **History of the Project**: Prior work, preliminary results, institutional context
   - **Plan of Work**: Detailed timeline with milestones and responsible personnel
   - **Sustainability**: How will the project persist after the grant period ends?
   - **Final Product and Dissemination**: What will be produced? How will it be shared?

3. **Work Samples / Prototype** (if applicable)
   - Demo or prototype showing technical feasibility

4. **Budget Narrative**
   - Justify each budget line; show cost-sharing if applicable

### Tone and Framing
- Lead with the humanistic question, not the technology
- Show reviewer panel (humanities scholars) that the project advances humanistic understanding, not just technical infrastructure
- Emphasis on open access and public benefit is rewarded
- Avoid jargon from computer science without humanistic contextualization

---

## Andrew W. Mellon Foundation

**URL**: mellon.org  
**Focus**: Arts, humanities, higher education, cultural heritage  
**Process**: Invitation-only for most programs; Letter of Inquiry (LOI) required first  
**DH-relevant programs**: Digital scholarship, archival preservation, scholarly communication

### LOI Structure (1,000–1,500 words)
1. Project title and one-line description
2. The problem or opportunity the project addresses (humanistic framing)
3. Approach and methods
4. How this fits Mellon's strategic priorities
5. Budget estimate and duration
6. Team qualifications (brief)

### Full Proposal (if invited)
- More detailed version of LOI
- Emphasis on feasibility, team expertise, sustainability
- Mellon prefers collaborative projects across institutions

---

## AHRC (Arts and Humanities Research Council, UK)

**URL**: ahrc.ukri.org  
**Process**: Open competition via Je-S portal; responsive mode and themed calls  
**Relevant schemes**: Research Grant, Fellowship, Networking Grant, Collaborative Doctoral Partnership

### Standard Research Grant Structure
1. **Case for Support** (6 pages for small grants; up to 12 for large)
   - Why this research / what the problem is
   - What has already been done (prior work and literature)
   - What you will do and how (methodology)
   - Why your team is best placed to do it
   - Expected outputs and impact
   
2. **Pathways to Impact**
   - Academic impact: contributions to the field
   - Public/cultural impact: how will non-academics benefit?

3. **Data Management Plan** (required for all grants)
   - What data will be generated?
   - How will it be stored, preserved, and shared?

### Key Differences from NEH
- Stronger emphasis on economic and societal impact
- Explicit requirement for pathways to public engagement
- Collaborative grants involving non-academic partners are highly valued

---

## Other DH-Relevant Funders

| Funder | Scheme | Notes |
|--------|--------|-------|
| IMLS (US) | National Leadership Grants for Libraries | Libraries and archives digitization; community access |
| NSF (US) | Humans, Disasters, and the Built Environment; SBE grants | Cross-disciplinary; need strong computational component |
| British Academy (UK) | Small Grants; Newton Fellowships | Literature, history, philosophy; max £10k small grants |
| Leverhulme Trust (UK) | Research Grants | Humanities and social sciences; UK PI required |
| European Research Council | Starting Grant, Consolidator Grant | Competitive; EU-affiliated institution required; frontier research |
| SSRC (US) | Various | Social science DH, area studies, public scholarship |
| Canadian SSHRC | Insight Grant | Canadian PI required; interdisciplinary humanities |
| DFG (Germany) | Research Grants | German PI required; collaborative research centers |

---

## Common Grant Proposal Failure Modes

1. **Leading with technology**: Reviewers from humanities panels are not impressed by the tools. Lead with the scholarly problem the project addresses.

2. **Vague environmental scan**: Failing to show you know the landscape of comparable projects makes reviewers question whether the project is necessary.

3. **Unrealistic work plan**: Milestone timelines should account for realistic project management, hiring delays, and unexpected technical issues. Add 20% buffer.

4. **Sustainability not addressed**: How does the project live after the grant ends? Without an answer, reviewers worry the product will be orphaned.

5. **Ignoring open access requirements**: Most DH funders expect open-access outputs. Plan for this from the start.

6. **Budget mismatches**: Personnel costs must match the work plan. If you say 1.0 FTE for a postdoc, the budget must show salary + benefits for 1.0 FTE.

---

## Agent Instructions for Grant Mode

When `paper_type = grant_proposal`:

1. Ask the user which funder / program they are targeting
2. Retrieve the relevant template from this guide
3. Ask for: project description (1 paragraph), existing preliminary work, team composition, proposed duration and budget range
4. Use `proposal_architect_agent` with grant-specific sections replacing the standard proposal structure
5. Produce a full draft narrative section by section, following funder-specific guidelines
6. Flag budget narrative as a placeholder — the user must verify all figures against institutional rates
