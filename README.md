# Claude Brand Skills

**A complete system for building distinctive brand identities with LLMs — designed around the limitations of LLMs.**

---

## The Problem This Solves

LLMs generate output by predicting the most probable next token. This is a statistical averaging operation. The output doesn't *drift* toward the average — it **starts there**, because the average is what the mechanism is optimized to find.

When you ask an LLM to "design a clean, modern brand," it produces the statistical center of every clean, modern brand in its training data. Different colors on the same layout. Different fonts on the same hierarchy. Every instruction specific enough to produce a distinctive result just becomes a new center of convergence.

**This skill system is designed around that limitation.**

### What LLMs Can't Do

- **Can't see their own output.** They write SVG/HTML/CSS as text tokens with no visual feedback loop. They're painting blindfolded.
- **Can't feel tension.** Great design creates productive discomfort. LLMs either produce something comfortable (convergent) or break things randomly.
- **Can't resist coherence.** Deliberately unfinished, misaligned, or rule-breaking design goes against training weights. They'll "fix" anything that looks like an error, even when the error was the point.
- **Don't have taste.** Taste is judgment that isn't reducible to rules. LLMs approximate taste with heuristics, and heuristics are generalizations, and generalizations converge to the mean.

### What LLMs Can Do

- **Emotive narrative** — Beautiful, grounded language that captures a brand's soul
- **Strategic positioning** — Frameworks, voice, personality traits
- **Systematic tokens** — Coherent color, typography, and spacing systems
- **Execution at speed** — Generate 5 structural variants in the time it takes a human to sketch one

### The Escape: Process, Not Instruction

Prescribing techniques doesn't work: "be bold" converges to the average of bold. "Break the grid" converges to the average of grid-breaking. Even "surprise me" converges to the average of surprise.

**The only escape is evolutionary process with human selection pressure:**

```
Generate → Compare → Kill → Mutate → Repeat
   LLM       Human    Human    LLM      ↺
```

The LLM is the hand. The user is the eye. This skill encodes that division throughout.

---

## How It Works

```
                          ┌─────────────────────────────┐
                          │   00-Orchestrator.md        │
                          │   (tracks phase state)      │
                          └──────────┬──────────────────┘
                                     │
    ┌────────────────────────────────┼────────────────────────────────┐
    │              TEXT PHASES (LLM-native — work well)               │
    │                                                                 │
    │  Phase 0: Emotive Narrative                                     │
    │  ├─ Soul of the brand in evocative language                     │
    │  ├─ Human moment, transformation, ethos, personality            │
    │  └─ Creates deep LLM memory → prevents generic drift            │
    │                                                                 │
    │  Phase 1: Discovery                                             │
    │  ├─ Strategic positioning, voice, personality                   │
    │  └─ Core metaphor that organizes all visual choices             │
    │                                                                 │
    │  Phase 2: Visual Direction  ← API keys optional (see below)    │
    │  ├─ AI-generated reference images (Mode A)                      │
    │  ├─ User-provided mood boards (Mode B)                          │
    │  └─ Skip to SVG iteration (Mode C)                              │
    │                                                                 │
    └────────────────────────────────┼────────────────────────────────┘
                                     │
    ┌────────────────────────────────┼────────────────────────────────┐
    │          VISUAL PHASES (LLM-blind — need guardrails)           │
    │                                                                 │
    │  Phase 3: Mark Development                                      │
    │  ├─ Path A: Reference image → vtracer → SVG (primary)          │
    │  ├─ Path B: Hand-coded geometric SVG (simple marks only)        │
    │  ├─ Mandatory render-verify loop (rsvg-convert → PNG)           │
    │  └─ Hard iteration limit: 5-8 rounds, then pivot                │
    │                                                                 │
    │  Phase 4: Wordmark                                              │
    │  ├─ MANDATORY font exploration (3-4 candidates rendered)        │
    │  ├─ User picks font BEFORE any lockup work                      │
    │  └─ Horizontal, stacked, text-only variants                     │
    │                                                                 │
    │  Phase 5: Design System                                         │
    │  ├─ Colors, typography, spacing, components                     │
    │  ├─ Web (CSS) + iOS (SwiftUI) implementations                   │
    │  └─ All values derived from mark — no template defaults          │
    │                                                                 │
    └────────────────────────────────┼────────────────────────────────┘
                                     │
    ┌────────────────────────────────┼────────────────────────────────┐
    │        COMPOSITION PHASE (evolutionary — user drives)          │
    │                                                                 │
    │  Phase 5.5: Composition & Visual Identity                       │
    │  ├─ Tokens (Phase 5) = materials. Composition = the building.   │
    │  ├─ Without this, every brand converges to same layout.         │
    │  │                                                              │
    │  │  The Process:                                                │
    │  │  1. Create anti-reference board (what to avoid)              │
    │  │  2. Generate 3-5 structurally different variants             │
    │  │     (not color swaps — different spatial logic)              │
    │  │  3. User kills variants (no blending — blending = averaging) │
    │  │  4. Mutate survivors with named convention breaks            │
    │  │  5. Repeat until blur test passes                            │
    │  │                                                              │
    │  └─ Blur test: at 20% visibility, layout silhouette must be     │
    │     distinguishable from the anti-references                    │
    │                                                                 │
    └────────────────────────────────┼────────────────────────────────┘
                                     │
    ┌────────────────────────────────┼────────────────────────────────┐
    │              DELIVERY PHASES                                    │
    │                                                                 │
    │  Phase 6: DESIGN.md Creation                                    │
    │  ├─ Single source of truth: narrative + tokens + composition    │
    │  └─ Any LLM can read it → brand stays consistent forever       │
    │                                                                 │
    │  Phase 7: Packaging                                             │
    │  └─ All assets organized → brand-kit/ or .zip                   │
    │                                                                 │
    └─────────────────────────────────────────────────────────────────┘
```

---

## Quick Start

```bash
# Clone
git clone https://github.com/b1rdmania/claude-brand-skills.git

# Tell Claude to use it
"Use the brand-skill to build a complete brand identity for [project].
 Start with Phase 0: create the emotive narrative."
```

### Prerequisites

See `brand-skill/TOOLS-REQUIRED.md` for full details.

**Required:**
- `rsvg-convert` — `brew install librsvg` (SVG rendering)

**Recommended:**
- `vtracer` — `cargo install vtracer` (PNG→SVG tracing for Phase 3)
- `svgo` — `npm install -g svgo` (SVG optimization)

**Image generation (Phase 2, optional):**
- Requires API keys: `GOOGLE_API_KEY`, `REPLICATE_API_TOKEN`, or `OPENAI_API_KEY`
- Phases 0-1 work without any image generation
- Can always use your own reference images (Mode B) or skip to SVG (Mode C)

---

## What's Inside

| Skill | Purpose |
|-------|---------|
| **brand-skill** | Complete 8-phase brand identity system |
| **art** | AI image generation workflows (visualizations, diagrams, illustrations) |
| **frontend-design** | Frontend design guidelines with LLM convergence awareness |
| **canvas-design** | Canvas/layout design workflows |

### Directory Structure

```
claude-brand-skills/
├── README.md
├── CHANGELOG.md
├── brand-skill/
│   ├── SKILL.md                       # Main skill definition
│   ├── 00-Orchestrator.md             # Phase state tracker (read first)
│   ├── TOOLS-REQUIRED.md              # Prerequisites checklist
│   ├── ADDENDUM-4-WEB-PRESENCE.md     # Convergence theory (full framework)
│   ├── SKILL-AUDIT.md                 # Gap analysis from real-world build
│   ├── Workflows/
│   │   ├── 00-EmotiveNarrative.md     # Phase 0: Soul of the brand
│   │   ├── 01-Discovery.md            # Phase 1: Strategy & positioning
│   │   ├── 02-VisualDirection.md      # Phase 2: Reference exploration
│   │   ├── 03-MarkDevelopment.md      # Phase 3: Logo (tracing-first)
│   │   ├── 04-Wordmark.md            # Phase 4: Typography & lockups
│   │   ├── 05-DesignSystem.md         # Phase 5: Tokens (web + iOS)
│   │   ├── 05A-CompositionIdentity.md # Phase 5.5: Evolutionary composition
│   │   ├── 06-DesignMdCreation.md     # Phase 6: Master DESIGN.md
│   │   └── 07-Packaging.md            # Phase 7: Asset delivery
│   ├── Templates/
│   │   ├── DESIGN-template.md
│   │   ├── philosophy-template.md
│   │   ├── visual-philosophy-template.md
│   │   ├── design-guidelines-template.md
│   │   └── readme-template.md
│   └── Examples/
│       └── sorted-brand-kit/          # Real-world example (Sorted.fund)
├── art/
│   ├── SKILL.md
│   ├── Tools/Generate.ts              # Image generation CLI
│   └── Workflows/                     # Visualize, Diagrams, Stats, etc.
├── frontend-design/
│   └── SKILL.md                       # Includes LLM design limitations
└── canvas-design/
    └── SKILL.md
```

---

## The Philosophy in Detail

### Why "emotive narrative first"

Phase 0 creates a rich emotional context that gets loaded into every subsequent LLM call. Without it, the LLM falls back to its statistical center: "clean and modern." With it, every decision can be tested: *does this serve the narrative?*

The narrative doesn't prevent convergence on its own — but it prevents *arbitrary* convergence. The brand converges toward something meaningful rather than something generic.

### Why "tracing, not hand-coding"

LLMs write SVG as text tokens. They cannot see the result. Hand-coding complex marks leads to endless blind iteration — 30+ rounds that never converge because the LLM is refining code, not shapes.

Tracing inverts this: start with an image the LLM *can* evaluate, convert to SVG mechanically (vtracer), then refine. The creative judgment happens on bitmaps. The vector conversion is mechanical.

### Why "kill, don't blend"

When users see 5 variants and like elements from #2 and #4, the natural instinct is to blend them. But blending is averaging — it moves the result back toward the statistical center. The evolutionary process demands binary decisions: alive or dead.

The surviving variant gets mutated (pushed further from center), not merged with the dead ones.

### Why "composition, not just tokens"

A brand can have the most distinctive color palette, typography, and spacing system in the world. Put those tokens into a standard hero-features-testimonial-CTA layout and it looks like every other well-designed page.

**Tokens are materials. Composition is the building.** Phase 5.5 exists because without it, every brand built with this skill would produce excellent ingredients arranged identically.

### Why DESIGN.md

Traditional brand systems scatter knowledge across Figma files, PDF guidelines, and people's heads. Knowledge degrades over time. New team members approximate. The brand drifts.

DESIGN.md is a single file that any LLM can read and maintain consistency from. It embeds the emotive narrative (preventing generic drift), the compositional identity (preventing layout convergence), and the implementation specs (preventing token approximation).

**It's the insurance policy against the very convergence problem this skill was built to solve.**

---

## Real-World Examples

This skill system was used to create:

1. **AutonoLabs.ai** — Agentic venture studio brand
   - Full 8-phase process including Phase 5.5 composition
   - 11 page variants through evolutionary kill/mutate process
   - Avenir Next weight system, AL monogram, type specimen aesthetic
   - The audit that produced v2.0 of this skill

2. **Compost.fi** — "Quiet Infrastructure" brand
   - ~2,600 API calls from philosophy to production
   - 26 logo iterations, full design system

3. **Sorted.fund** — "Utility Sublime" brand
   - Example included at `brand-skill/Examples/sorted-brand-kit/`
   - Warm infrastructure aesthetic, dense functional design language

---

## Example Commands

**Starting fresh:**
```
"Use the brand-skill to build a complete brand identity for [project].
 Start with Phase 0: create the emotive narrative."
```

**Resuming mid-process:**
```
"Continue Phase 3 of the brand process. Here's feedback on v1-v5:
 [your feedback]. Create the next iteration batch."
```

**Already have a logo:**
```
"I already have a logo. Skip to Phase 5 and create a design system
 (web + iOS) that complements this mark: [describe logo]."
```

**Just need the master doc:**
```
"We've completed Phases 0-5. Now create the master DESIGN.md file
 that consolidates everything into one comprehensive reference."
```

---

## License

These workflows are personal tools. Use them for your own projects, modify as needed. Attribution appreciated but not required.

---

**Version:** 2.0 — February 2026
**Created by:** Andy (with Claude Code)

*"Love in action is a harsh and dreadful thing compared to love in dreams." — Dostoevsky*
