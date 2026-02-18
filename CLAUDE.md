# Claude Brand Skills Repository

Reusable skill system for brand development — from emotive narrative through packaged brand kit. Built to prevent AI-generated design convergence through process structure, not prescriptive prompting.

## Repository Structure

- `brand-skill/` — Complete 8-phase brand development system (Phases 0-7 + 5.5)
- `brand-skill/Workflows/` — Phase workflow files (00-Orchestrator through 07-Packaging)
- `brand-skill/Templates/` — Reusable markdown templates with semantic placeholders
- `brand-skill/Examples/sorted-brand-kit/` — Real-world example brand kit
- `brand-skill/SKILL-AUDIT.md` — Comprehensive audit from AutonoLabs execution
- `brand-skill/ADDENDUM-4-WEB-PRESENCE.md` — Convergence theory and evolutionary design process
- `art/` — Image generation workflows
- `canvas-design/` — Canvas/layout design with bundled fonts
- `frontend-design/` — Frontend design guidelines

## Version: v2.0 (February 2026)

**Convergence framework release.** Adds Phase 5.5 (Composition & Visual Identity) — evolutionary diverge/kill/mutate process to prevent generic layouts. Includes full theoretical framework on why LLMs revert to statistical mean in design.

Key additions:
- Phase 5.5: Composition & Visual Identity (anti-convergence evolutionary process)
- Tracing-first approach for Phase 3 (Mark Development)
- Font exploration step in Phase 4 (Wordmark)
- Color derivation process in Phase 5 (Design System)
- Light mode derivation, contrast validation, social assets, favicon pipeline
- Template placeholders replacing hardcoded Sorted.fund values

See `CHANGELOG.md` for full v2.0 release notes.

## Current Active Project

**InfraSingularity Brand** (`projects/infrasingularity/`)
- Institutional blockchain infrastructure provider
- **Progress: Phases 0-5 COMPLETE. Phase 5.5 IN PROGRESS (2026-02-18)**
  - Phase 2 skipped (integrated into Phase 3)
  - Phase 3: Mark locked (v11d - 25-dot radial starburst)
  - Phase 4: Wordmark locked (Infra Medium + Singularity Light, purple full stop)
  - Phase 5: Design system complete (Outfit + Figtree, full color palette)
  - Phase 5.5: Two-page site in progress
- **Key files:**
  - `phase5.5-composition/splash.html` — **BANKED.** Diagonal split splash (purple left panel + stat blocks right). ENTER → links to main page.
  - `phase5.5-composition/composition-final.html` — Main page. Brutalist design: spec tables, corner marks, protocol manifest, investments grid.
- **Design decisions locked:**
  - Brutalist override: 0 border-radius everywhere (overrides DESIGN.md 8px cards)
  - Sharp institutional aesthetic: hard borders, corner bracket marks, spec tables
  - Hero: `clamp(56px, 8vw, 96px)` Outfit weight 300 (Light) — corrected from previous weight 500
  - Section headers: `LABEL ──────` (flex + 1px rule)
  - Copy rules: sourced-only (current site, Canton NaaS doc, pitch deck). No invented claims. No American marketing punchlines.
  - Wordmark on splash: inlined SVG with purple full stop removed (already white-on-dark; no filter needed)
- **CSS pattern (splash):** purple panel via `clip-path: polygon(0 0, 55% 0, 42% 100%, 0 100%)` + absolute-positioned layers
- **Lessons learned this session:**
  - Don't use `filter: brightness(0) invert(1)` on wordmark SVG — it makes the purple full stop white
  - `justify-content: flex-start` + `flex: 1` on stat blocks is the correct stat-fill pattern
  - All spacing vars must be `--space-X` (not `--spX`) per DESIGN.md
- Notion workspace: `https://www.notion.so/3040d80f5eb781dcaa12dc35497dfdbd`
- Track state: `.brand-progress.md` in project directory

## Completed Reference Project

**AutonoLabs** — Full 8-phase execution used to audit and improve the skill
- Live site: autonomolabs.vercel.app
- Completed all phases including Phase 5.5 (11 page variants, blur test, compositional identity)
- Generated SKILL-AUDIT.md and ADDENDUM-4-WEB-PRESENCE.md from this execution
- Example of evolutionary process: 5 structural variants → kill → 3 mutations → "The Specimen"

## Key Files

**Start here:**
- `brand-skill/Workflows/00-Orchestrator.md` — Master phase tracker, read first
- `brand-skill/SKILL.md` — Brand skill overview and routing
- `brand-skill/TOOLS-REQUIRED.md` — Prerequisites (vtracer, svgo, rsvg-convert)

**Theory:**
- `brand-skill/SKILL-AUDIT.md` — What works, what doesn't, lessons learned
- `brand-skill/ADDENDUM-4-WEB-PRESENCE.md` — Why LLMs converge + how to escape it

**Critical phase:**
- `brand-skill/Workflows/05A-CompositionIdentity.md` — Phase 5.5, prevents generic layouts

## MCP Servers

- **Notion** — `https://mcp.notion.com/mcp` (user scope) — for pushing brand outputs to Notion workspaces for client collaboration and review

## Process Overview (8 Phases)

0. **Emotive Narrative** → Grounding metaphor and emotional context
1. **Discovery** → Philosophy, positioning, visual philosophy
2. **Visual Direction** → Reference images or skip decision
3. **Mark Development** → Logo SVG (tracing-first approach)
4. **Wordmark** → Font exploration + lockups
5. **Design System** → Color derivation, typography, spacing, components
5.5. **Composition & Visual Identity** → Evolutionary diverge/kill/mutate for web presence
6. **DESIGN.md Creation** → Single source of truth
7. **Packaging** → Brand kit with all formats and sizes

Each phase has defined entry criteria, outputs, and gate checks tracked in `.brand-progress.md`.

## Key Principles

**Anti-convergence:**
- LLMs generate from the center of their training distribution
- Prescribing techniques just moves the convergence point
- Only process structure (evolutionary selection) escapes the mean
- Phase 5.5 is the critical anti-convergence layer

**Phase 0 is non-negotiable:**
- Emotive narrative prevents generic drift in all subsequent phases
- Tokens (colors, fonts) are necessary but insufficient
- Composition defines spatial identity — this is where distinctiveness lives

**Honest about LLM limitations:**
- Phases 0-2 (text) play to LLM strengths
- Phases 3+ (visual) require tooling assistance and user selection
- LLMs can't see their SVG output → bitmap tracing for complex marks
- Human taste (outside training distribution) is the selection pressure

## Repository

- **GitHub**: `b1rdmania/claude-brand-skills` on `master`
- Last updated: 2026-02-12 (pulled 14 commits, v2.0 release)
