# Setup Guide — DH Plugin Suite

## Prerequisites

- Claude Code CLI installed and configured
- A Claude account with access to claude-sonnet-4-6 or later

## Installation

### Option 1: Direct skill symlinks (local development)
```bash
# Navigate to your repo
cd /path/to/repo

# Create symlinks for each skill in ~/.claude/skills/
mkdir -p ~/.claude/skills

ln -s $(pwd)/digital-humanity-skills/dh-explore ~/.claude/skills/dh-explore
ln -s $(pwd)/digital-humanity-skills/dh-write ~/.claude/skills/dh-write
ln -s $(pwd)/digital-humanity-skills/dh-review ~/.claude/skills/dh-review
ln -s $(pwd)/digital-humanity-skills/dh-pipeline ~/.claude/skills/dh-pipeline
```

### Option 2: Plugin registry install
```bash
claude plugin install /path/to/digital-humanity-skills/
```

This reads `.claude-plugin/plugin.json` and registers all four skills.

## Verification

After installation, open a new Claude Code session and run:
```
/dh-explore quick-brief
```

Expected behavior: Claude asks about your research topic, career stage, and corpus. Responds with a draft research question.

To test all four skills:
```bash
# Test dh-explore
/dh-explore quick-brief

# Test dh-write
/dh-write outline

# Test dh-review
/dh-review quick-assess
[paste a paragraph of DH writing]

# Test dh-pipeline
/dh-pipeline status
```

## Configuration

No additional configuration is required. The skills work with Claude's default settings.

**Optional**: If you want the skills to route automatically without explicit `/` invocation, add routing keywords to `.claude/CLAUDE.md` in your project directory. The global routing file is at `digital-humanity-skills/.claude/CLAUDE.md`.

## Updating

To update the skills:
```bash
cd /path/to/repo
git pull
```

Symlinks will automatically point to the updated files — no reinstallation needed.

## Troubleshooting

**Skill not found**: Verify the symlink is in `~/.claude/skills/` and points to a directory containing `SKILL.md`.

**Wrong mode triggered**: Check `MODE_REGISTRY.md` for the exact trigger keyword. Modes are case-sensitive (`quick-brief` not `Quick-Brief`).

**Agent file not read**: If Claude seems to skip an agent, the `Read` instruction in SKILL.md may not be executing. Ensure the relative path from SKILL.md to the agent file is correct.

**Passport not loading**: The DH Material Passport must be pasted in full into the session when resuming. Claude has no persistent memory — the passport text IS the state.

## File Structure Verification

Run this to verify all expected files are present:
```bash
find /path/to/digital-humanity-skills -name "*.md" -o -name "*.json" | sort
```

Expected total: ~108 files across the four skills, shared resources, and docs.
