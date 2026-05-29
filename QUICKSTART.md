# Digital Humanity Skills — Quick Start

## What This Is

A four-skill Claude Code plugin suite for the complete digital humanities research lifecycle:

| Skill | Command | What It Does |
|-------|---------|-------------|
| `dh-explore` | `/dh-explore` | Develop your research question, find archives, assess primary sources, build your corpus |
| `dh-write` | `/dh-write` | Write proposals, thesis chapters, journal articles, close readings |
| `dh-review` | `/dh-review` | Simulate peer review; parse supervisor feedback into revision plans |
| `dh-pipeline` | `/dh-pipeline` | Manage the full research lifecycle with integrity gates and a Material Passport |

---

## Installation

### Option 1: Symlinks (recommended for development)
```bash
# From this repo root:
ln -s $(pwd)/digital-humanity-skills/dh-explore ~/.claude/skills/dh-explore
ln -s $(pwd)/digital-humanity-skills/dh-write ~/.claude/skills/dh-write
ln -s $(pwd)/digital-humanity-skills/dh-review ~/.claude/skills/dh-review
ln -s $(pwd)/digital-humanity-skills/dh-pipeline ~/.claude/skills/dh-pipeline
```

### Option 2: Plugin install (if using the gstack plugin registry)
```bash
# Install as a plugin:
claude plugin install ./digital-humanity-skills/
```

---

## First Use

### Starting a new DH project:
```
/dh-explore
```
The intake agent will ask 3 questions and configure your session.

### Already have a research question and corpus? Go directly to writing:
```
/dh-write article
```

### Received reviewer or supervisor feedback?
Paste the feedback and run:
```
/dh-review supervisor-feedback
```

### Managing a dissertation or large project?
Use the full pipeline:
```
/dh-pipeline
```
Keep your DH Material Passport between sessions.

---

## The Canonical Test Project

If you want to see how the suite works, start with this scenario:

> "I want to study how the rhetoric of the abolitionist movement changed in US newspapers between the Kansas-Nebraska Act (1854) and the start of the Civil War (1861), using newspapers from Chronicling America. I plan to combine topic modeling with close reading of key editorials."

Run `/dh-explore full` with this description. The suite will:
1. Help you develop the dual-framed research question
2. Guide you to the right Chronicling America collections
3. Assess OCR quality thresholds for the 1850s newspaper collection
4. Recommend LDA topic modeling + close reading as the hybrid methodology
5. Identify relevant scholarship from DHQ, Cultural Analytics, and historical literature

---

## Key Concepts

**Dual-framed research question**: Every DH research question should have (1) an interpretive claim about culture/history/literature and (2) a methodological contribution that DH makes possible.

**OCR quality thresholds**: Digitized historical text below 70% accuracy is generally unusable for NLP; 85%+ for named entity recognition. Always assess and disclose.

**DH bridge**: The connection between computational findings and humanistic argument. The most common DH paper failure is having two separate papers (a methods paper + a humanities essay) that don't genuinely connect.

**DH Material Passport**: The stateful record of your project — corpus entries, sources, tools, supervision feedback. Save it between sessions for the pipeline to resume correctly.

---

## Exemplar Papers Referenced in This Suite

These real papers are embedded in agent prompts as worked examples:

- "Mining for the Meanings of a Murder" — DHQ — OCR quality and text mining
- "Machine Reading the Primeros Libros" — DHQ 10/4 — Colonial archive digitization
- "How Network Analysis Uncovers Smuggling History" — Cultural Analytics 2023
- "The Generative Dissensus of Reading the Feminist Novel" — Cultural Analytics
- "Slow, Painful and Expensive" — DHQ 19/3 — Corpus construction realities
- NER Historical Documents Survey — arXiv 2109.11406

---

## For More Information

- `docs/ARCHITECTURE.md` — How the four skills connect and how agents interact
- `docs/SETUP.md` — Detailed installation and configuration
- `MODE_REGISTRY.md` — All modes, trigger keywords, and outputs across all skills
- `shared/references/` — Cross-skill reference documents
