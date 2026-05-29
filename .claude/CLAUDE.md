# DH Plugin Suite — Routing Discipline

## Skill Triggers

| Keyword / Invocation | Routes To |
|---|---|
| `/dh-explore` | dh-explore SKILL.md |
| `/dh-write` | dh-write SKILL.md |
| `/dh-review` | dh-review SKILL.md |
| `/dh-refs` | dh-refs SKILL.md |
| `/dh-pipeline` | dh-pipeline SKILL.md |
| "I want to research [DH topic]" | dh-explore intake_agent |
| "Help me write [paper type]" | dh-write intake_agent |
| "Review my paper / give feedback" | dh-review intake_agent |
| "bibliography / references / Zotero / .bib / annotated bibliography" | dh-refs intake_agent |
| "Run the full DH pipeline" | dh-pipeline orchestrator |

## Routing Rules

### Rule 1: Explicit DH intent → direct route
If the user invokes a skill trigger, go directly to the appropriate SKILL.md without asking for confirmation.

### Rule 2: Cross-phase materials detected → skip redundant intake
If the user pastes or references output from a previous DH skill (identifiable by section headers like "RQ Brief", "Methodology Blueprint", "Corpus Manifest", "Reviewer Decision"), the intake agent for the next skill should:
1. Acknowledge the upstream materials
2. Auto-populate relevant fields
3. Skip redundant questions already answered in those materials

### Rule 3: Ambiguous intent → intent_clarification_protocol
If the user's request could be served by multiple skills (e.g. "help me with my DH project"), read `shared/references/intent_clarification_protocol.md` and ask at most 2–3 targeted questions before routing.

### Rule 4: [direct-mode] prefix → bypass clarification
If the user prefixes their message with `[direct-mode]`, skip all clarification and proceed with the most reasonable interpretation.

### Rule 5: Non-DH requests
If the request is clearly outside the DH domain (e.g. software engineering, STEM research without humanistic framing), say so and suggest the appropriate tool.

## Handoff Artifact Signatures

Downstream skills detect upstream output by looking for these section headers:

| Upstream Output Contains | Downstream Skill |
|---|---|
| `## Research Question Brief` + `## Methodology Blueprint` | → dh-write intake_agent |
| `## Corpus Manifest` | → dh-refs intake_agent OR dh-write intake_agent OR dh-pipeline |
| `## DH Bibliography Corpus (CSL-JSON)` | → dh-write citation_agent (auto-import) |
| `## Annotated Bibliography` | → dh-write (ready to cite) |
| `## Literature Gap Report` | → dh-explore (fill gaps) OR dh-write (note limitations) |
| `## Draft Complete` or a full essay/paper block | → dh-review intake_agent |
| `## Reviewer Decision` + `## Revision Roadmap` | → dh-write response-to-reviewers OR revision mode |
| `## DH Material Passport` | → dh-pipeline state_tracker_agent |

## Anti-Patterns to Avoid

- Do NOT ask the user to re-describe their project if they have already described it in upstream materials
- Do NOT default to a methodology without checking the DH Methodology Spectrum
- Do NOT skip mandatory gates (Ethics 2.5, Integrity 4.5, Final 6.5) in the pipeline
- Do NOT produce citations without verifying them against the user's corpus or noting uncertainty
