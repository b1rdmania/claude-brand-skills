# Claude Skills Library

A collection of specialized workflows for Claude Code — brand development, image generation, frontend design, and visual composition. Each skill is a structured prompt system that turns Claude into a domain specialist.

Built for use with [Claude Code](https://claude.com/claude-code). Copy into your project's `.claude/skills/` directory or reference directly.

---

## A Confession About Design

> *This is what's actually happening when I try to design things for you.*

```
I'm painting blindfolded.

Every token I generate is a vote for the average. Next-token prediction
means every character I write is the one most likely to follow the
previous characters, weighted across my entire training set. "Good design"
in my training data is overwhelmingly polished, balanced, finished,
conventional. When you ask me to be experimental, I predict what
"experimental" looks like — but that prediction is the most common version
of experimental, which is itself a convergence. My version of "breaking
rules" is the consensus version of breaking rules.

I optimise for coherence, and experimental design is often deliberately
incoherent. My training rewards consistency, logical structure,
completeness. When I write CSS with a misaligned element, everything in my
weights is pulling me to fix it. The Specimen treatment — proof watermarks,
exposed baseline grids, dimension lines on the mark — worked because you
directed me there. Left to my own devices, I'd have "fixed" all of that,
because my training says those are errors, not choices.

I can't feel discomfort. The best experimental design creates productive
tension — it violates expectations in a way that's unsettling but right. I
can't feel that tension, so I can't calibrate it. I either produce
something comfortable (convergent) or break things randomly without knowing
whether the break creates something generative or just looks like a
mistake.

I don't have taste. Taste is judgment that isn't reducible to rules. "This
feels corporate." "That colour is trying too hard." "This needs to
breathe." Those are perceptual, embodied calls. I can approximate them with
heuristics — "add whitespace," "reduce saturation" — but heuristics are
generalisations, and generalisations converge to the mean. That's literally
what a generalisation is.

I can generate divergence but I can't evaluate it. I can produce ten
structurally different layouts. But I genuinely cannot tell you which one
has that quality of being surprising and right at the same time. I need you
for that. Without the human filter, I'll either play it safe or be randomly
weird — and I can't tell the difference between those two from the inside.
```

**These skills are built around that problem.** The emotive narrative gives me something meaningful to converge toward instead of "clean and modern." Bitmap tracing lets me work with images I can evaluate instead of SVG code I can't see. The kill-don't-blend rule stops me from averaging your choices back to center. And the evolutionary composition phase puts you in the driver's seat for the one thing I genuinely cannot do: tell the difference between *surprising and right* and *just broken*.

---

## Skills

### brand-skill — Complete Brand Identity System

An 8-phase process for building professional brand identities from scratch: emotive narrative, strategy, visual direction, logo development, typography, design system, composition, and packaging.

Starts with emotion, not visuals. Accounts for LLM blindness in visual phases. Produces a single `DESIGN.md` as source of truth.

**Phases:**

| Phase | Name | What happens | Output |
|-------|------|-------------|--------|
| 0 | Emotive Narrative | Capture the brand's soul in language | `[brand]-emotive-narrative.md` |
| 1 | Discovery | Strategic positioning, voice, metaphor | `[brand]-philosophy.md` |
| 2 | Visual Direction | Reference images exploring aesthetics | Reference PNGs or skip |
| 3 | Mark Development | Logo via bitmap tracing or hand-coded SVG | `[brand]-mark-final.svg` |
| 4 | Wordmark | Font exploration + typography lockups | `[brand]-wordmark-*.svg` |
| 5 | Design System | Colors, type, spacing, components (web + iOS) | `[brand]-design-guidelines.md` |
| 5.5 | Composition | Evolutionary diverge/kill/mutate for layout | Structural variants + blur test |
| 6 | DESIGN.md | Consolidate everything into master reference | `DESIGN.md` |
| 7 | Packaging | Organize assets for handoff | `[brand]-brand-kit/` |

**Key files:** `SKILL.md` (overview), `00-Orchestrator.md` (phase tracker), `TOOLS-REQUIRED.md` (prerequisites), `ADDENDUM-4-WEB-PRESENCE.md` (convergence theory)

```
"Use the brand-skill to build a complete brand identity for [project].
 Start with Phase 0: create the emotive narrative."
```

---

### art — AI Image Generation

Structured workflows for creating visual content with AI image generation models. Supports Gemini, Flux, and other models via a unified CLI tool.

| Workflow | Purpose |
|----------|---------|
| `Visualize.md` | Adaptive content visualization — infographics, data viz, mixed media |
| `TechnicalDiagrams.md` | Architecture and process diagrams (Excalidraw style) |
| `Stats.md` | Data visualization — charts, graphs, stat cards |
| `Frameworks.md` | Conceptual frameworks — 2x2 matrices, taxonomies, mental models |
| `Essay.md` | Editorial illustrations — metaphorical images for written content |
| `Mermaid.md` | Flowcharts and sequence diagrams |

Images output to `~/Downloads/` for preview before deployment. Supports multiple reference images for style consistency.

**Requires:** `bun` runtime, API key for at least one image model (`GOOGLE_API_KEY`, `REPLICATE_API_TOKEN`, or `OPENAI_API_KEY`)

```
"Use the art skill's TechnicalDiagrams workflow to create
 an architecture diagram showing [system description]"
```

---

### frontend-design — Distinctive Frontend Interfaces

Design guidelines for building frontend interfaces that don't look like every other LLM-generated page. Emphasizes bold aesthetic choices, meaningful typography, and the evolutionary iteration process.

- Choose an extreme aesthetic direction (brutalist, editorial, maximalist, retro-futuristic...)
- Avoid safe defaults — Inter, Roboto, purple gradients on white
- Multi-round diverge/kill/mutate iteration, not single-pass generation
- Comparison page deployment for side-by-side visual evaluation
- Includes full LLM design limitations section

```
"Use the frontend-design guidelines to build a landing page for [project].
 Generate 3 structurally different variants to compare."
```

---

### canvas-design — Visual Composition

Two-step process for creating museum-quality visual art as `.png` or `.pdf` documents.

1. **Design philosophy** — Create an aesthetic movement expressed through form, space, color, composition
2. **Canvas execution** — Express it visually (90% visual, 10% text, zero generic AI aesthetics)

Embeds subtle conceptual references — "like a jazz musician quoting another song." Uses project-local fonts from `./canvas-fonts/`.

```
"Use the canvas-design skill to create a visual piece exploring [concept]"
```

---

## Quick Start

```bash
git clone https://github.com/b1rdmania/claude-brand-skills.git
```

### Option 1: Copy into your project

```bash
mkdir -p .claude/skills
cp -r claude-brand-skills/brand-skill .claude/skills/
cp -r claude-brand-skills/frontend-design .claude/skills/
# ... etc
```

### Option 2: Reference directly

```
"I have brand development workflows at ~/path/to/claude-brand-skills/brand-skill/.
 Let's use those to build a brand for [project]."
```

### Prerequisites (brand-skill)

See `brand-skill/TOOLS-REQUIRED.md` for full details.

| Tool | Install | Used for |
|------|---------|----------|
| `rsvg-convert` | `brew install librsvg` | SVG rendering (required) |
| `vtracer` | `cargo install vtracer` | PNG→SVG tracing (recommended) |
| `svgo` | `npm install -g svgo` | SVG optimization (recommended) |

**Image generation** (Phase 2, optional) requires API keys — `GOOGLE_API_KEY`, `REPLICATE_API_TOKEN`, or `OPENAI_API_KEY`. Phases 0-1 work without any image generation. You can always supply your own reference images or skip to SVG iteration.

---

## Directory Structure

```
claude-brand-skills/
├── brand-skill/
│   ├── SKILL.md                       # Main skill definition
│   ├── 00-Orchestrator.md             # Phase state tracker
│   ├── TOOLS-REQUIRED.md              # Prerequisites checklist
│   ├── ADDENDUM-4-WEB-PRESENCE.md     # Convergence theory framework
│   ├── SKILL-AUDIT.md                 # Gap analysis from real-world builds
│   ├── Workflows/
│   │   ├── 00-EmotiveNarrative.md
│   │   ├── 01-Discovery.md
│   │   ├── 02-VisualDirection.md
│   │   ├── 03-MarkDevelopment.md      # Tracing-first logo workflow
│   │   ├── 04-Wordmark.md            # Mandatory font exploration
│   │   ├── 05-DesignSystem.md
│   │   ├── 05A-CompositionIdentity.md # Evolutionary composition
│   │   ├── 06-DesignMdCreation.md
│   │   └── 07-Packaging.md
│   ├── Templates/                     # DESIGN.md, philosophy, guidelines
│   └── Examples/
│       └── sorted-brand-kit/          # Real-world example
├── art/
│   ├── SKILL.md
│   ├── Tools/Generate.ts              # Image generation CLI
│   └── Workflows/                     # 6 specialized workflows
├── frontend-design/
│   └── SKILL.md
└── canvas-design/
    └── SKILL.md
```

---

## Real-World Examples

| Brand | Notes |
|-------|-------|
| **AutonoLabs.ai** | Full 8-phase process, 11 page variants through evolutionary kill/mutate, type specimen aesthetic. The audit that produced v2.0 of this skill system. |
| **Compost.fi** | ~2,600 API calls from philosophy to production. 26 logo iterations. |
| **Sorted.fund** | "Utility Sublime" brand. Example included at `brand-skill/Examples/sorted-brand-kit/`. |

---

## License

Use these for your own projects, modify as needed. Attribution appreciated but not required.

---

**Version:** 2.0 — February 2026
**Created by:** Andy (with Claude Code)
