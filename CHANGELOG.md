# Changelog

## v2.0 — February 2026

**Convergence framework release.** Integrates the theoretical understanding of *why* LLMs produce generic design into the skill system itself, and adds the process structures to escape it.

### New: Convergence theory

- **`ADDENDUM-4-WEB-PRESENCE.md`** — Full theoretical framework on why LLMs revert to statistical mean in design output
- **`SKILL-AUDIT.md`** — Gap analysis from running the full process on AutonoLabs.ai
- **LLM Design Limitations** section added to both brand-skill and frontend-design SKILL.md — honest about what LLMs can and can't do, with the evolutionary process as the prescribed escape

### New: Phase 5.5 — Composition & Visual Identity

Tokens (Phase 5) define materials; composition defines what to build with them. Without this phase, every brand converges to the same layout regardless of tokens.

- **`05A-CompositionIdentity.md`** — Evolutionary diverge/kill/mutate process
- Anti-reference boards, blur test (20% visibility silhouette test)
- Binary kill decisions (no blending — blending is averaging)
- Named convention breaks as mutation mechanism

### Updated: Phase 2 — API key hand-holding

- Added "Before You Start" section with API key requirements table
- Clear guidance that Phases 0-1 work without any image generation
- Inline reminder at the generate step pointing to Modes B/C as alternatives

### Updated: Template placeholders

All hardcoded Sorted.fund hex values replaced with semantic placeholders (`{BG_DEEP}`, `{TEXT_PRIMARY}`, `{BRAND_ACCENT}`, etc.) across:
- `05-DesignSystem.md`
- `06-DesignMdCreation.md`
- `Templates/DESIGN-template.md`

### Updated: README

Complete rewrite with:
- Philosophy section explaining the convergence problem and how this flow addresses it
- ASCII architecture diagram of the full phase pipeline
- Phase 5.5 in the process overview
- Honest framing of LLM limitations up front

---

## v1.1 — February 2026

**Post-audit release.** Every change here comes from running the brand-skill end-to-end on a real project (AutonoLabs) and documenting what broke.

### The core problem

Phases 0-2 are text-native — they work well because LLMs are good at language. Phases 3+ assume the LLM can iteratively design visuals. It can't. This release restructures the visual phases around that limitation.

---

### New files

- **`brand-skill/00-Orchestrator.md`** — Master phase tracker. Defines a `.brand-progress.md` state file that persists across conversations, enforcing sequential phase completion with explicit gate checks. Solves the problem of phase drift and lost context when resuming work.

- **`brand-skill/TOOLS-REQUIRED.md`** — Upfront tooling checklist with install commands and a quick-check script. No more discovering mid-Phase-3 that vtracer isn't installed.

### Phase 3: Mark Development (rewritten)

The biggest change. Phase 3 was fundamentally broken — it asked the LLM to hand-code SVGs and judge the results, but LLMs can't see their own SVG output. Endless blind iteration loops were the result.

**Now two paths:**
- **Path A (Primary):** Generate reference image → trace to SVG with `vtracer` → optimize with `svgo` → render-verify → refine. The LLM works with bitmaps it can see, not SVG code it can't.
- **Path B (Secondary):** Hand-code simple geometric marks. Explicitly scoped to basic shapes only.

**New guardrails:**
- Mandatory render-verify loop after every SVG change (`rsvg-convert` → PNG → present)
- Iteration limit: 5-8 rounds, then stop and pivot approach
- Documented escape hatches: re-generate reference, try freeconvert.com, go back to Phase 2
- "Don't edit traced path data by hand" — re-trace from a modified reference instead

### Phase 4: Wordmark (font exploration added)

Previously jumped straight to creating lockups in Inter 500 without asking. In the AutonoLabs execution, wordmarks were packaged in fonts the user never chose.

**New Step 1a-1c:**
1. Propose 3-4 font candidates with rationale
2. Render font previews as PNGs
3. Get explicit user approval before any lockup work begins

Also added three strategies for working with complex traced marks (group reference, bitmap lockup, separate files) since traced SVGs are often too large to embed in lockup files.

### Phase 5: Design System (template warning)

Added prominent note: all hex values in the template are from the Sorted.fund example. Replace them with your brand's palette. Previously easy to miss, resulting in designs that accidentally inherited another brand's colors.

### Standardized gate checks (all phases)

Every phase now ends with the same sequence:
1. Render/present outputs
2. Ask for explicit approval with a named gate check
3. Update `.brand-progress.md` state file
4. Only proceed when user says yes

Previously, gate checks were inconsistent — some phases had them, some didn't, and none updated a persistent state file.

### README updates

- Added Phase 0 (Emotive Narrative) and Phase 6 (DESIGN.md Creation) to the detailed guide — they existed as workflow files but were missing from the README
- Updated directory structure to reflect new files
- Updated dependencies section to reference TOOLS-REQUIRED.md
- Phase numbering corrected throughout (8 phases, not 6)

---

### Summary of audit items addressed

| # | Issue | Fix |
|---|-------|-----|
| 1 | Phase 3 SVG blindness | Tracing as primary path, render-verify loops |
| 2 | No cross-conversation orchestration | 00-Orchestrator.md + .brand-progress.md state file |
| 3 | Template colors leaked between brands | Warning notes on example values |
| 4 | No visual validation loop | Mandatory render-verify after every SVG change |
| 5 | Phase 4 impractical with traced SVGs | Three lockup strategies for complex marks |
| 6 | Vague/missing gate checks | Standardized across all 8 phases |
| 7 | No iteration limits | 5-8 round cap with documented escape hatches |
| 8 | Ad-hoc tooling discovery | TOOLS-REQUIRED.md with install + validation commands |
| 9 | Font choice skipped in Phase 4 | Mandatory font exploration with rendered previews |
| 10 | Phase drift across conversations | Persistent state file with resume instructions |

---

## v1.0 — February 2026

Initial release. Complete brand development system with anti-AI-slop framework:
- 4 skill systems: brand-skill, art, frontend-design, canvas-design
- 8-phase brand development process (Phases 0-7)
- Art skill with 6 image generation workflows
- Templates and real-world examples (Sorted.fund brand kit)
