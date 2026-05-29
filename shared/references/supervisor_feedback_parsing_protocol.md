# Supervisor Feedback Parsing Protocol

*Shared reference — used by both dh-write/revision_coach_agent and dh-review/supervisor_feedback_agent*

## The Challenge

Supervisor and peer reviewer comments in DH fields are often:
- Unstructured (stream of consciousness, not categorized by priority)
- Mixed-register (general impressions + specific edits)
- Discipline-specific (assumes knowledge of field norms)
- Emotionally loaded (discouraging language that may obscure the actual task)
- Implicit (says "this doesn't work" without specifying what to do)

Parsing these comments into an actionable revision plan is a skill. This protocol standardizes the parsing.

## Priority Tier Assignment

### Tier 1 — Must Fix
Required before the paper can be submitted, accepted, or approved. Signals:
- "Missing" / "absent" / "no" — something structurally absent
- "I don't understand" / "unclear" / "confusing" — argument or logic failures
- "This is incorrect" / "this is wrong" — factual or methodological errors
- "You need to" / "this requires" — explicit requirements
- Reviewer recommendation: "Major revisions" or "Reject and resubmit"

### Tier 2 — Should Fix
Expected in revision; significantly improves the paper's chances of acceptance/approval. Signals:
- "I suggest" / "I would recommend" / "consider" — advisory
- "Could be clearer" / "needs development" / "underdeveloped" — expansion needed
- "The literature review should include" — missing engagement
- "This section is weak" — quality improvement without being structural
- Reviewer recommendation: "Minor revisions"

### Tier 3 — Consider
Optional; good if scope permits; often future-work territory. Signals:
- "You might think about" / "it could be interesting"
- "A future paper could explore" / "beyond the scope but"
- Stylistic suggestions not required by venue
- "I'm curious whether" — speculative, not directive

## Parsing Workflow

For each comment in the feedback:
1. Read for emotional content; translate into neutral technical language
2. Identify the type: structural | argument | evidence | methodology | citation | prose
3. Assign tier (1, 2, or 3)
4. Identify the location in the paper (section, paragraph, specific line if possible)
5. Write the action: specific, concrete verb phrase ("Rewrite the introduction to foreground the argument in the first paragraph" not "improve the introduction")
6. Estimate time: rough hours to complete

## Comment Type Taxonomy

| Type | Description | Examples |
|---|---|---|
| Structural | Organization of sections or chapters | "The methods chapter should come before the literature review" |
| Argument | Central claim or its development | "The connection between your computational findings and your historical argument is unclear" |
| Evidence | Support for claims | "You need more primary source evidence in section 3" |
| Methodology | Technical correctness or transparency | "You don't explain why you chose 20 topics for the LDA model" |
| Citation | Missing or incorrect references | "This claim needs citation"; "You're misrepresenting Smith 2019" |
| Prose | Style, clarity, register | "This sentence is too long"; "Avoid passive voice in the introduction" |

## Output Format (per feedback item)

```
[TIER X] [Type] — [Location]
Supervisor said: "[direct quote or close paraphrase]"
Translation: [what they mean in plain language]
Action: [specific task — verb phrase]
Estimated time: [n hours / n minutes]
```

## Aggregated Revision Plan

After all comments are parsed:
1. Group by tier (Tier 1 first)
2. Within Tier 1, sequence by type: Structural → Argument → Evidence → Methodology → Citation → Prose
3. Produce time estimate per tier and total
4. Identify any conflicts (e.g., two reviewers who want opposite changes — surface for researcher decision)
