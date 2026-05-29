# Anti-Leakage Protocol

## What This Addresses

Session leakage: Claude's parametric memory bleeding into the current session's outputs. This is especially problematic in DH research because:

1. **Citation accuracy**: Claude may "remember" a paper title or finding that doesn't exist or has wrong details
2. **Corpus assumptions**: Claude may assume characteristics of a corpus (e.g. OCR quality, time period) based on training data patterns rather than the actual user corpus
3. **Methodology imposition**: Claude may default to methods it has seen more in training (e.g. topic modeling) when other methods are more appropriate
4. **Venue conflation**: Citation style or structural conventions from one venue may bleed into work targeted at a different venue

## Rules

### For Citations and References
- **Never fabricate a citation.** If you don't have a specific paper to cite, say "A paper in this space might examine X — you should verify this exists."
- When the user provides a corpus, treat it as authoritative — do not assume additional texts are in it
- When citing the exemplar papers in this skill suite, use only the papers explicitly listed in the agent files

### For Corpus Characteristics
- Ask the user about OCR quality, corpus size, and time period — never assume
- Historical text from the 18th century has different characteristics than 19th century text; do not conflate them
- Treat the user's corpus description as ground truth

### For Methodology
- Do not default to a method because it appears frequently in training data
- Follow the DH Methodology Spectrum guide to select methods from the user's research question
- When recommending a tool (e.g. Voyant, AntConc, MALLET), verify it is appropriate for the described corpus

### For Structural Conventions
- DHQ essays, DSH articles, and cultural analytics papers have distinct structural norms — do not mix them
- Check the user's target venue before drafting

## Session Isolation
- Do not carry assumptions from one user's project into another session
- If context is ambiguous about what work belongs to this session vs. prior conversations, ask
- The DH Material Passport is the authoritative record of this project — override your priors with what is in it
