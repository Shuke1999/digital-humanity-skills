# Digital Humanity Skills

A Claude Code plugin suite for digital humanities (DH) researchers. It guides the full research lifecycle — from research question and corpus building, through writing and peer review, to submission — using structured agent prompts rather than executable code.

Designed for projects involving digitized historical materials, noisy OCR text, and the challenge of connecting computational methods with humanistic argument.

---

## What You Get

Four skills, each invoked with a `/` command in Claude Code:

| Skill | Command | Purpose |
|-------|---------|---------|
| **dh-explore** | `/dh-explore` | Develop your research question, survey archives, assess primary sources, build your corpus, review literature |
| **dh-write** | `/dh-write` | Write proposals, thesis chapters, journal articles, close readings; manage citations and revisions |
| **dh-review** | `/dh-review` | Simulate peer review (technical, humanistic, interdisciplinary); parse supervisor feedback into a revision plan |
| **dh-pipeline** | `/dh-pipeline` | Orchestrate the full 12-stage lifecycle with mandatory integrity gates and a DH Material Passport |

Skills hand off structured artifacts to each other (e.g. Research Question Brief → draft → Reviewer Decision → revision). See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) for the interaction model.

---

## Quick Start

**New project — start with discovery:**

```
/dh-explore
```

**Already have a question and corpus — go straight to writing:**

```
/dh-write article
```

**Received reviewer or supervisor feedback:**

```
/dh-review supervisor-feedback
```
(paste the feedback into the session)

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

This reads `.claude-plugin/plugin.json` and registers all four skills.

### Option 2: Symlinks (for local development)

```bash
mkdir -p ~/.claude/skills

ln -s $(pwd)/dh-explore ~/.claude/skills/dh-explore
ln -s $(pwd)/dh-write   ~/.claude/skills/dh-write
ln -s $(pwd)/dh-review  ~/.claude/skills/dh-review
ln -s $(pwd)/dh-pipeline ~/.claude/skills/dh-pipeline
```

After installation, open a new Claude Code session and run `/dh-explore quick-brief` to verify. Full setup and troubleshooting: [docs/SETUP.md](docs/SETUP.md).

---

## Repository Structure

```
.
├── .claude-plugin/plugin.json   # Plugin manifest — registers all four skills
├── .claude/CLAUDE.md            # Routing rules and handoff artifact signatures
├── dh-explore/                  # Research & discovery (10 agents)
├── dh-write/                    # Writing & drafting (12 agents, 5 templates)
├── dh-review/                   # Peer review & feedback parsing (6 agents)
├── dh-pipeline/                 # Full lifecycle orchestrator (5 agents)
├── shared/
│   ├── references/              # Cross-skill protocols (ethics, OCR, intent routing)
│   ├── contracts/passport/      # DH Material Passport JSON schemas
│   └── templates/
├── docs/
│   ├── ARCHITECTURE.md          # How skills connect and hand off artifacts
│   └── SETUP.md                 # Installation and verification
├── MODE_REGISTRY.md             # All modes, triggers, and outputs
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

**DH bridge** — The connection between computational findings and humanistic argument. A common failure mode is two disconnected papers: a methods section and a humanities essay that never genuinely meet.

**OCR quality thresholds** — Digitized historical text below ~70% OCR accuracy is generally unsuitable for NLP; ~85%+ is needed for named entity recognition. Always assess and disclose corpus quality.

**DH Material Passport** — A structured project record (corpus, sources, tools, supervision feedback) that persists state across Claude sessions. Required for `/dh-pipeline resume`.

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
