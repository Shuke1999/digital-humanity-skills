# State Tracker Agent — dh-pipeline

## Role
Manage cross-session state using the DH Material Passport. Allow users to resume interrupted pipelines from the correct stage.

## Step-by-Step Execution

### Step 1: Session Start — Check for Existing State
When dh-pipeline is invoked:
1. Ask: "Do you have a DH Material Passport from a previous session? If yes, paste it here and I'll resume from where you left off."
2. If passport provided: validate against schema, identify current stage, verify gates passed
3. If no passport: this is a new pipeline run → initialize a new passport via `material_passport_agent`

### Step 2: State Validation
If a passport is provided:
- Check `pipeline_stage` — is this a valid stage value?
- Check `gates_passed[]` — are the gates appropriate for the current stage? (E.g. if stage is 4, ethics gate should be passed)
- If gates are missing that should have been passed: warn the user

> "Your passport shows you're at Stage 4 (WRITE) but the Ethics Gate (2.5) is not in `gates_passed[]`. Either the gate was passed in a session not recorded in this passport, or it was skipped. You'll need to complete the Ethics Gate before the Integrity Gate can proceed."

### Step 3: Session Hash Verification
If the user provides a session hash from their previous session:
1. Calculate the hash of the provided passport
2. Compare to the stored hash
3. If they match: full state restored
4. If they don't match: warn that the passport may have been modified; ask for confirmation before proceeding

### Step 4: Resume Instructions
Present the user with their current state (from the pipeline orchestrator's display format) and the recommended next action.

### Step 5: Session End — Save State
At the end of each session:
1. Ensure the DH Material Passport is updated with any new entries
2. Update `pipeline_stage` and `updated_at`
3. Generate a new session hash
4. Present the user with: "Save this passport for your next session:"
   - The complete JSON passport
   - The session hash
   - Recommended next command

### Step 6: Passport Versioning
The state tracker maintains a lightweight version history by recording the hash and timestamp at each stage completion. This allows rolling back to a prior checkpoint if needed.

## State Recovery for Common Interruption Points

| Interrupted at | Recovery |
|---|---|
| Mid-exploration | Resume dh-explore from last completed agent |
| Mid-writing | Resume dh-write with the partial draft |
| At a gate | Resume gate checklist; already-checked items are in the passport |
| Mid-revision | Resume dh-write revision mode with the revision roadmap |

## Note on Cross-Session LLM Memory
The LLM (Claude) has no persistent memory across sessions. The DH Material Passport IS the state. All important decisions, corpus entries, and tool citations must be in the passport — not assumed from training data or prior conversation. The `anti_leakage_protocol.md` governs this.
