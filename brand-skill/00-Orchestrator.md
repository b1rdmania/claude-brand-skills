# Brand Process Orchestrator

**Read this file first. It controls phase progression and prevents skipping steps.**

---

## How This Works

The brand process has 8 phases (0-7). Each phase must be completed and approved before the next begins. Progress is tracked in a state file that persists across conversations.

### Starting a New Brand

1. Check tooling: Read `TOOLS-REQUIRED.md` and verify prerequisites
2. Create the state file in the project directory (see format below)
3. Begin Phase 0

### Resuming an Existing Brand

1. Read the project's `.brand-progress.md`
2. Find the current phase (the first one not marked COMPLETE)
3. Read that phase's workflow file
4. Continue from where it left off

---

## Phase Progression

```
Phase 0: Emotive Narrative    → 00-EmotiveNarrative.md
Phase 1: Discovery            → 01-Discovery.md
Phase 2: Visual Direction     → 02-VisualDirection.md
Phase 3: Mark Development     → 03-MarkDevelopment.md
Phase 4: Wordmark & Lockups   → 04-Wordmark.md
Phase 5: Design System        → 05-DesignSystem.md
Phase 6: DESIGN.md Creation   → 06-DesignMdCreation.md
Phase 7: Packaging            → 07-Packaging.md
```

**Rules:**
- Complete phases in order. Do not skip.
- Each phase ends with a gate check (see below).
- Do not start Phase N+1 until Phase N's gate check passes.
- Update `.brand-progress.md` after every gate check.

**Exceptions:**
- User explicitly says "skip Phase N" — note the skip in the state file.
- User says "start at Phase N" — mark prior phases as SKIPPED with a note.

---

## State File Format

Create `.brand-progress.md` in the project's brand output directory at the start of the process:

```markdown
# Brand Progress: [Brand Name]

Started: [Date]
Last Updated: [Date]

## Phase 0: Emotive Narrative — PENDING
Output files:
Notes:

## Phase 1: Discovery — PENDING
Output files:
Notes:

## Phase 2: Visual Direction — PENDING
Output files:
Notes:

## Phase 3: Mark Development — PENDING
Output files:
Notes:

## Phase 4: Wordmark & Lockups — PENDING
Output files:
Notes:

## Phase 5: Design System — PENDING
Output files:
Notes:

## Phase 6: DESIGN.md Creation — PENDING
Output files:
Notes:

## Phase 7: Packaging — PENDING
Output files:
Notes:
```

**Status values:** PENDING | IN PROGRESS | COMPLETE | SKIPPED

When updating a phase:
- Set status to IN PROGRESS when starting
- List output files as they're created
- Add notes about decisions, direction changes, user feedback
- Set status to COMPLETE only after the gate check passes

---

## Standardized Gate Check

Every phase ends with this exact sequence:

### 1. Present the Outputs

**For text phases (0, 1, 5, 6):**
- Show the key content to the user (summary or full text)

**For visual phases (2, 3, 4):**
- Render all SVGs to PNG at review size:
  ```bash
  rsvg-convert -w 512 -h 512 [file].svg -o [file]-preview.png
  ```
- Open for user review:
  ```bash
  open [file]-preview.png
  ```
- For marks, also render at favicon sizes:
  ```bash
  rsvg-convert -w 32 -h 32 [file].svg -o [file]-32px.png
  ```

### 2. Ask for Explicit Approval

Use this exact format:

> **Phase [N] Gate Check**
>
> Outputs: [list files created]
>
> Ready to proceed to Phase [N+1]: [Phase Name]?
>
> Please confirm with "approved" or give feedback.

### 3. Update State File

On approval:
```markdown
## Phase [N]: [Name] — COMPLETE
Output files: [list]
Notes: Approved [date]. [Any relevant notes]
```

On feedback:
```markdown
## Phase [N]: [Name] — IN PROGRESS
Output files: [list so far]
Notes: Feedback received: [summary]. Iterating.
```

### 4. Proceed or Iterate

- "Approved" → Start next phase
- Feedback → Address it, re-present, re-check the gate
- "Start over" → Reset phase status to IN PROGRESS, begin fresh

---

## Quick Reference: What Each Phase Produces

| Phase | Key Outputs | Gate Criteria |
|-------|------------|---------------|
| 0 | `[brand]-emotive-narrative.md` | Narrative resonates, feels true |
| 1 | `[brand]-philosophy.md`, `[brand]-visual-philosophy.md` | Direction feels right |
| 2 | Reference images (3-4 PNGs) | Direction chosen |
| 3 | `[brand]-mark-final.svg`, favicon PNGs | Mark works at all sizes |
| 4 | `[brand]-wordmark-final.svg`, variants | Lockups aligned and balanced |
| 5 | `[brand]-design-guidelines.md` | System feels coherent |
| 6 | `DESIGN.md` | All 8 sections complete |
| 7 | `[brand]-brand-kit/` folder | Everything packaged |

---

## Handling Problems

### "This phase isn't working"

- Note the problem in `.brand-progress.md`
- Check the workflow file for escape hatches (Phase 3 has specific iteration limits)
- If stuck after the workflow's suggested limit, ask the user how to proceed

### "I want to go back to an earlier phase"

- Update the current phase to PENDING
- Update the target phase to IN PROGRESS
- Note the reason: "Returning to Phase N because [reason]"

### "Can we skip this phase?"

- Only skip if the user explicitly requests it
- Mark as SKIPPED with reason
- Note any implications for later phases

---

## At Conversation Start

**Always do this when resuming brand work:**

1. Read `.brand-progress.md` from the project directory
2. Identify the current phase
3. Read that phase's workflow file
4. Tell the user: "Resuming [Brand] — currently on Phase [N]: [Name]. [Brief status.]"
