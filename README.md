# Digital Humanity Skills

A Claude Code plugin suite for digital humanities (DH) researchers and students. It guides the full research lifecycle — from research question and corpus building, through writing and peer review, to submission — using structured agent prompts rather than executable code.

Designed for projects anywhere on the DH spectrum: digitized historical archives, literary corpus analysis, cultural analytics, digital editions, and the challenge of connecting computational methods with humanistic argument. Works for anyone from undergraduate to faculty.

---

## What You Get

Five skills, each invoked with a `/` command in Claude Code:

| Skill | Command | Purpose |
|-------|---------|---------|
| **dh-explore** | `/dh-explore` | Develop your research question, survey digital archives, assess primary sources, build your corpus, review literature, generate a venue-specific research framework map |
| **dh-write** | `/dh-write` | Write proposals, grant applications, thesis chapters, journal articles, book reviews, response-to-reviewers letters, close readings |
| **dh-review** | `/dh-review` | Simulate peer review (technical, humanistic, interdisciplinary); parse supervisor feedback into a structured revision plan |
| **dh-refs** | `/dh-refs` | Import Zotero/.bib/.ris sources, build annotated bibliographies, format citations, identify literature gaps |
| **dh-pipeline** | `/dh-pipeline` | Orchestrate the full 13-stage lifecycle with mandatory integrity gates and a DH Material Passport |

Skills hand off structured artifacts to each other (Research Question Brief → corpus → draft → Reviewer Decision → revision). See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) for the interaction model.

---

## Quick Start

**New project — start with discovery:**
```
/dh-explore
```

**Have a research question, need a method + paper structure plan:**
```
/dh-explore framework
```
Tell it your RQ and target venue (ACL / DHQ / PMLA / specific journal) — it builds a Mermaid diagram of recommended methods and a section-by-section paper structure.

**Already have sources — build your bibliography first:**
```
/dh-refs annotate
```
(paste your Zotero export, .bib file, or reading list)

**Ready to write:**
```
/dh-write article
/dh-write thesis
/dh-write grant-proposal
```

**Received reviewer or supervisor feedback:**
```
/dh-review supervisor-feedback
/dh-write response-to-reviewers
```
(paste the comments into the session)

**Dissertation or long-term project — use the full pipeline:**
```
/dh-pipeline
```

For a worked example and first-run walkthrough, see [QUICKSTART.md](QUICKSTART.md).

---

## Installation

**Prerequisites:** [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI installed and configured.

### Option 1: Plugin install (recommended)

From this repository root:

```bash
claude plugin install .
```

This reads `.claude-plugin/plugin.json` and registers all five skills.

### Option 2: Symlinks (for local development)

```bash
mkdir -p ~/.claude/skills

ln -s $(pwd)/dh-explore  ~/.claude/skills/dh-explore
ln -s $(pwd)/dh-write    ~/.claude/skills/dh-write
ln -s $(pwd)/dh-review   ~/.claude/skills/dh-review
ln -s $(pwd)/dh-refs     ~/.claude/skills/dh-refs
ln -s $(pwd)/dh-pipeline ~/.claude/skills/dh-pipeline
```

After installation, open a new Claude Code session and run `/dh-explore quick-brief` to verify. Full setup and troubleshooting: [docs/SETUP.md](docs/SETUP.md).

---

## Repository Structure

```
.
├── .claude-plugin/plugin.json   # Plugin manifest — registers all five skills
├── .claude/CLAUDE.md            # Routing rules and handoff artifact signatures
├── dh-explore/                  # Research & discovery (11 agents, 8 modes)
├── dh-write/                    # Writing & drafting (12 agents, 14 modes, 5 templates)
├── dh-review/                   # Peer review & feedback parsing (6 agents)
├── dh-refs/                     # Citation & reference management (5 agents)
├── dh-pipeline/                 # Full lifecycle orchestrator (5 agents)
├── shared/
│   ├── references/              # Cross-skill protocols (ethics, user profiles, intent routing)
│   ├── contracts/passport/      # DH Material Passport JSON schemas
│   └── templates/
├── docs/
│   ├── ARCHITECTURE.md          # How skills connect and hand off artifacts
│   └── SETUP.md                 # Installation and verification
├── MODE_REGISTRY.md             # All 34 modes, triggers, and outputs across 5 skills
└── QUICKSTART.md                # First-use guide and canonical test project
```

Each skill directory contains:

- `SKILL.md` — mode routing; dispatches to agent files in sequence
- `agents/` — self-contained prompt documents for each agent role
- `references/` — skill-specific reference material

There is no build step. Skills are markdown instructions that Claude reads and follows at runtime.

---

## Key Concepts

**Dual-framed research question** — Every DH question should combine (1) an interpretive claim about culture, history, or literature and (2) a methodological contribution that DH makes possible.

**DH bridge** — The connection between computational findings and humanistic argument. A common failure mode is two disconnected sections — a methods section and a humanities argument — that never genuinely meet.

**OCR quality thresholds** — Digitized historical text below ~70% OCR accuracy is generally unsuitable for NLP; ~85%+ is needed for named entity recognition. Always assess and disclose corpus quality.

**DH Material Passport** — A structured project record (corpus, sources, tools, supervision feedback) that persists state across Claude sessions. Required for `/dh-pipeline resume`.

**User levels** — All skills adapt to your career stage. The first skill you run will ask once; after that, the level is remembered for the session. Levels: undergraduate → MA student → PhD student → early-career → faculty.

**Handoff artifacts** — Each skill produces structured output (Research Question Brief, Corpus Manifest, Research Framework Map, Annotated Bibliography, Draft, Reviewer Decision) that downstream skills detect and import automatically — no re-entry needed.

**Research Framework Map** — Output of `/dh-explore framework`: a Mermaid flowchart + method recommendations + venue-specific paper structure, differentiated for NLP/AI conferences, DH journals, traditional humanities journals, or a named target publisher.

---

## Documentation

| Document | Contents |
|----------|----------|
| [QUICKSTART.md](QUICKSTART.md) | Installation, first commands, canonical test scenario |
| [MODE_REGISTRY.md](MODE_REGISTRY.md) | Every mode, trigger keyword, and output across all skills |
| [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) | Skill interaction model, handoff protocol, design decisions |
| [docs/SETUP.md](docs/SETUP.md) | Detailed install, verification, troubleshooting |

---

## License

See repository license file if present. Contributions and issue reports welcome.
