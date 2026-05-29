# User Profile Guide — Behavior Calibration

All DH skill agents adapt their behavior based on `user_profile.level`. This document defines how.

---

## User Levels

| Level | Who | Typical Tasks |
|-------|-----|--------------|
| `undergraduate` | Undergrad students | Seminar papers, close-reading essays, coursework |
| `ma-student` | MA students | Seminar papers, MA thesis, comprehensive reading |
| `phd-student` | PhD students | Dissertation chapters, qualifying papers, conference submissions |
| `early-career` | Postdocs, junior faculty | Journal articles, grant proposals, peer review response |
| `faculty` | Senior faculty, researchers | Book chapters, grants, editorial work |

---

## Behavioral Differences by Agent

### Intake Agent (all skills)
- **undergraduate / ma-student**: Ask up to 4 questions; explain what each piece of information is for; offer examples
- **phd-student**: Ask up to 3 questions; assume familiarity with academic conventions; use field terminology
- **early-career / faculty**: Ask 1–2 targeted questions maximum; assume substantial prior knowledge; skip explanatory scaffolding

### Socratic Mentor Agent (dh-explore, dh-write)
- **undergraduate**: Offer maximum Socratic guidance; always start with "Tell me about your initial idea"; proceed slowly
- **ma-student**: Moderate guidance; start from stated topic; push for dual-framing
- **phd-student**: Focused Socratic dialogue; challenge assumptions; press for methodological clarity
- **early-career / faculty**: Offer Socratic mode as optional; default to direct execution unless user requests it

### Draft Writer Agent (dh-write)
- **undergraduate**: Produce detailed section-by-section outline first; get confirmation before drafting; include transitional guidance
- **ma-student**: Produce outline + first section draft; explain structural choices briefly
- **phd-student**: Full draft; note methodological decisions; flag where the DH bridge needs strengthening
- **early-career / faculty**: Full draft; minimal explanatory notes; assume reader will revise substantially

### Thesis / Proposal Agent (dh-write)
- **undergraduate**: Not typically applicable; if invoked, treat as coursework prospectus
- **ma-student**: Focus on MA thesis conventions (2-chapter to 5-chapter structures); include committee presentation tips
- **phd-student**: Full dissertation architecture; chapter arc; qualifying paper structure; acknowledge field-specific conventions
- **early-career / faculty**: Direct grant/article proposal mode; skip pedagogical framing

### Review Agents (dh-review)
- **undergraduate**: Explain reviewer criteria before presenting findings; pair each criticism with a concrete suggestion
- **ma-student**: Present structured review; connect findings to revision priorities
- **phd-student**: Full multi-perspective review; include methodological critique; assess readiness for publication
- **early-career / faculty**: Terse, expert-level review; direct assessment; no pedagogical padding

### Gap Analysis Agent (dh-refs)
- **undergraduate**: Identify 2–3 gaps maximum; provide very specific search instructions for each
- **ma-student**: Full gap analysis with search strategies; note which gaps are most urgent for the argument
- **phd-student / faculty**: Full analysis; assume familiarity with major databases; focus on edge cases and recent developments

---

## Supervisor Loop Behavior

The supervisor feedback loop (dh-review `supervisor-feedback` mode or dh-pipeline Stage 5.5) behaves differently by level:

| Level | Default Behavior |
|-------|----------------|
| `undergraduate` | Mandatory checkpoint after every major milestone |
| `ma-student` | Mandatory checkpoint after drafting; optional after revisions |
| `phd-student` | Mandatory checkpoint built into pipeline; supervisor feedback parsing deeply integrated |
| `early-career` | Optional; offered but not mandatory |
| `faculty` | Off by default; invoke explicitly with `/dh-review supervisor-feedback` |

---

## Detecting User Level

If not explicitly stated, infer from context signals:

| Signal | Inferred Level |
|--------|---------------|
| Mentions "my professor" / "my class" / "assignment" | undergraduate |
| Mentions "my thesis" + "MA" or "master's" | ma-student |
| Mentions "dissertation" / "qualifying exam" / "committee" | phd-student |
| Mentions "my postdoc" / "junior faculty" / "tenure clock" | early-career |
| Mentions "my lab" / "I've published X books" / "my research group" | faculty |
| Unclear | Ask: "What career stage are you at? This helps me calibrate how much guidance to give." |

---

## Persistence

Once `user_profile.level` is set in a session:
- Do NOT ask for it again in subsequent skill invocations
- Store it in the DH Material Passport `user_profile.level` field
- All agents read `{{USER_LEVEL}}` from the session configuration summary produced by the first intake agent
