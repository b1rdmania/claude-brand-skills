# Brand Skill — Phase Orchestrator

Use this to track progress through the brand development process. Each phase has defined entry criteria, outputs, and gates. Do not skip phases unless the user explicitly requests it.

---

## Phase Progression

| Phase | Name | Entry Criteria | Output | Gate |
|-------|------|----------------|--------|------|
| 0 | Emotive Narrative | User brief or project context | `[brand]-emotive-narrative.md` | User approves narrative |
| 1 | Discovery | Phase 0 complete | `[brand]-philosophy.md`, `[brand]-visual-philosophy.md` | User confirms positioning |
| 2 | Visual Direction | Phase 1 complete | Reference images or skip decision | User picks direction(s) |
| 3 | Mark Development | Phase 2 complete (or explicit skip) | `[brand]-mark-final.svg`, favicon PNG | User locks mark: "That's the one" |
| 4 | Wordmark | Phase 3 complete | `[brand]-wordmark-*.svg` variants | User confirms font, alignment, and variants |
| 5 | Design System | Phase 4 complete | `[brand]-design-guidelines.md` | User reviews tokens, no template defaults remain |
| 5.5 | Composition | Phase 5 complete | Structural variants deployed, compositional identity documented | Blur test passes, user selects direction |
| 6 | DESIGN.md | Phase 5.5 complete | `DESIGN.md` | Single file captures everything |
| 7 | Packaging | Phase 6 complete | `[brand]-brand-kit/` or `.zip` | All assets present and organized |

---

## Creating `.brand-progress.md`

At the start of every brand engagement, create `.brand-progress.md` in the project directory by copying the checklist below. This is the living progress tracker — update it at each gate check by marking phases complete with `[x]`.

## Checklist

Mark phases as you complete them:

```
[ ] Phase 0: Emotive Narrative
    → Output: [brand]-emotive-narrative.md
    → Gate: User says narrative captures the soul

[ ] Phase 1: Discovery
    → Output: [brand]-philosophy.md
    → Output: [brand]-visual-philosophy.md
    → Gate: User confirms positioning and aesthetic direction

[ ] Phase 2: Visual Direction
    → Output: Reference images (or decision to skip)
    → Gate: User picks direction(s) to explore

[ ] Phase 3: Mark Development
    → Output: [brand]-mark-final.svg
    → Output: [brand]-favicon.png (32px)
    → Gate: User locks final mark
    → WATCH: If not converging by v8-v10, pivot to bitmap tracing

[ ] Phase 4: Wordmark
    → Output: Font specimen comparison (MANDATORY before creating wordmark)
    → Output: Tracking + case treatment comparison
    → Output: [brand]-wordmark-final.svg (horizontal)
    → Output: [brand]-wordmark-short.svg (compact)
    → Output: [brand]-wordmark-stacked.svg (if needed)
    → Gate: User confirms font, tracking, case treatment, alignment, and size testing

[ ] Phase 5: Design System
    → Output: [brand]-design-guidelines.md
    → Output: Contrast validation matrix (dark + light mode)
    → Gate: All colors derived from mark (no template defaults)
    → Gate: Light mode fully specified (not hand-waved with "...")
    → Gate: Contrast validation passes (WCAG AA minimum)

[ ] Phase 5.5: Composition & Visual Identity
    → Output: 3-5 structural variants deployed to comparison page
    → Output: Surviving direction with mutations applied
    → Output: Compositional identity documentation
    → Gate: Blur test passes
    → Gate: User confirms composition is distinctive

[ ] Phase 6: DESIGN.md Creation
    → Output: DESIGN.md (single source of truth)
    → Gate: Contains emotive narrative, tokens, composition identity, anti-references

[ ] Phase 7: Packaging
    → Output: Mark variations (white, dark, mono SVGs)
    → Output: Mark PNGs (512, 256, 64px)
    → Output: Favicons (16, 32, 48px) + apple-touch-icon (180px)
    → Output: Social assets (OG image 1200x630, avatar 400x400)
    → Output: [brand]-brand-kit/ folder or .zip
    → Output: Quick-start README
    → Gate: All final assets present and organized
```

---

## Common Phase-Skip Scenarios

| User says | Action |
|-----------|--------|
| "I already have a logo" | Skip Phase 2-3, start at Phase 4 |
| "Skip to design system" | Ensure Phase 0-1 are done (even briefly), skip 2-4 |
| "I just need a landing page" | Do Phase 0-1 quickly, skip to Phase 5.5 (Composition) |
| "I have a full brand, just need the DESIGN.md" | Skip to Phase 6, but read existing brand assets first |

**Never skip Phase 0** unless the user has an existing emotive narrative or equivalent. The narrative is what prevents generic drift in every subsequent phase.

---

## When Things Go Wrong

| Problem | Solution |
|---------|----------|
| Mark not converging (v10+) | Switch to bitmap tracing (Phase 3 Path B) |
| User hates all variants | Go back to Phase 2, explore different direction |
| Design system feels generic | Check: did you derive from mark or copy template? |
| Web pages all look the same | You skipped Phase 5.5 (Composition). Go back. |
| User disengaged | You're iterating without their input. Stop and ask for direction. |
| Scope creep | Check which phase you're in. Finish current before expanding. |
