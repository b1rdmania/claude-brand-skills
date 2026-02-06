# Claude Skills Library

**A reusable collection of specialized workflows for brand development, image generation, and design work.**

Created for use with Claude Code and exportable to any project.

---

## 📦 What's Inside

This skills library contains four specialized skill systems:

| Skill | Purpose | When to Use |
|-------|---------|-------------|
| **brand-skill** | Complete brand identity development | Building a brand from scratch: logo, design system, guidelines |
| **art** | AI image generation workflows | Creating visualizations, diagrams, illustrations, reference images |
| **frontend-design** | Frontend design guidelines | Avoiding generic aesthetics, building distinctive interfaces |
| **canvas-design** | Canvas/layout design workflows | Designing layouts and compositions |

---

## 🎨 The Brand Development Process

The **brand-skill** is a complete **7-phase system** for building professional brand identities **with anti-AI-slop principles**.

### What Makes This Different

**Starts with emotion, not visuals.** Phase 0 creates an emotive narrative that gives LLMs deep memory — preventing generic "clean and modern" drift.

**Accounts for LLM blindness.** Phase 3 uses bitmap tracing (vtracer) as the primary path for logo development — because LLMs can't see their own SVG output. Render-verify loops and iteration limits prevent endless blind refinement.

**Orchestrated with state tracking.** A progress file (`.brand-progress.md`) persists across conversations, enforcing sequential phase completion with explicit gate checks.

**Result:** Brands that are coherent, distinctive, and impossible to confuse with AI slop.

### Process Overview

```
          00-Orchestrator.md    → Read first. Tracks phase state.
          TOOLS-REQUIRED.md     → Verify prerequisites before starting.

Phase 0: Emotive Narrative     → Soul of the brand in beautiful language
Phase 1: Discovery             → Strategic foundation & positioning
Phase 2: Visual Direction      → Reference images exploring directions
Phase 3: Mark Development      → Logo via tracing (vtracer) or hand-coded SVG
Phase 4: Wordmark              → Typography and lockups
Phase 5: Design System         → Complete system (web + iOS)
Phase 6: DESIGN.md             → Consolidate everything to master file
Phase 7: Packaging             → Final deliverable kit
```

### Final Output

**DESIGN.md** — A comprehensive, single-source-of-truth document containing:
- Emotive narrative (the soul)
- Strategic positioning
- Visual philosophy
- Complete design system (web + iOS)
- Implementation specs
- Anti-AI-slop validation

### Time Investment

- **Fast track:** 2-3 hours (with clear direction)
- **Full process:** 4-6 hours (including exploration and iteration)
- **Complex brands:** 8+ hours (multiple concepts, extensive iteration)

### What You Get

A complete brand kit including:
- ✅ Brand philosophy and positioning documents
- ✅ Logo mark (SVG, scalable, tested at all sizes)
- ✅ Typography system and lockup variants
- ✅ Complete design system (colors, spacing, components)
- ✅ Design guidelines documentation
- ✅ All assets packaged and ready to use

---

## 🚀 How to Use These Skills

### Option 1: In a Specific Project

Copy the skills folder into your project's `.claude/` directory:

```bash
# From your project root:
mkdir -p .claude/skills
cp -r ~/Claude\ Skills/* ./.claude/skills/
```

Then tell Claude:

> "Use the brand-skill to build a complete brand identity for [project name]"

### Option 2: Global Installation

Keep skills in `~/Claude Skills/` and reference them when needed:

> "I have brand development workflows at ~/Claude Skills/brand-skill/. Let's use those to build a brand for [project]."

### Option 3: Ad-Hoc Usage

Point Claude to specific workflow files:

> "Follow the process in ~/Claude Skills/brand-skill/Workflows/03-MarkDevelopment.md to iterate on a logo"

---

## 📖 Brand Development Detailed Guide

### Phase 0: Emotive Narrative (10-15 min)

**Goal:** Capture the soul of the brand in evocative language before any strategic work.

**Process:**
- Write a short narrative that captures the feeling of using the product
- Focus on sensory language, metaphor, and emotional resonance
- This becomes the "north star" that prevents generic drift in later phases

**Outputs:**
- `[brand]-emotive-narrative.md` — The brand's soul in prose

**Example prompt:**
> "Start Phase 0 of the brand process. Write an emotive narrative for [project] — it should feel like [adjectives]."

---

### Phase 1: Discovery (15-20 min)

**Goal:** Establish strategic foundation before any visual work.

**Two approaches:**
- **Research-first (preferred):** If Claude has access to your codebase, it will read your project files and draft a positioning hypothesis
- **Question-based:** If working blind, Claude will ask targeted questions

**Outputs:**
- `[brand]-philosophy.md` — Brand essence, voice, principles
- `[brand]-visual-philosophy.md` — Aesthetic movement and visual approach

**Example prompt:**
> "Start Phase 1 of the brand process. My project is called [name] and it [brief description]."

---

### Phase 2: Visual Direction (10-15 min)

**Goal:** Generate reference images to explore visual territory before committing to detailed work.

**Process:**
- Generate 3-4 reference images exploring different interpretations
- Review and pick a direction
- Refine if needed

**Outputs:**
- Reference images (PNG) showing visual directions

**Example prompt:**
> "Generate visual direction references based on the philosophy we created"

---

### Phase 3: Mark Development (20-60 min)

**Goal:** Develop the logo mark through tracing or hand-coded SVG.

**Two paths:**
- **Path A (Primary):** Generate reference image → trace to SVG with vtracer → refine
- **Path B:** Hand-code simple geometric marks directly in SVG

**Process:**
- Generate or source a reference image
- Trace to SVG (vtracer or freeconvert.com)
- Render and verify at multiple sizes (rsvg-convert)
- Refine with iteration limit: 5-8 rounds, then pivot
- Test at favicon sizes (32px, 16px)
- Lock final version

**Outputs:**
- `[brand]-mark-final.svg` — Production logo
- Favicon PNG exports

**Example prompt:**
> "Start Phase 3. I have a reference image at [path]. Trace it and let's refine from there."

**Tips:**
- LLMs can't see SVG output — always render to PNG before presenting
- If refinement isn't converging after 5-8 rounds, change approach
- Use freeconvert.com as a fallback for tracing

---

### Phase 4: Wordmark (30-45 min)

**Goal:** Pair the mark with typography to create lockup systems.

**Process:**
- Choose font direction (sans, serif, mono)
- Create horizontal, stacked, and text-only variants
- Refine alignment through iteration
- Test in real-world contexts (nav, footer, headers)

**Outputs:**
- `[brand]-wordmark-final.svg`
- Lockup variants (horizontal, stacked, text-only)

**Example prompt:**
> "Create wordmark lockups for the final logo"

---

### Phase 5: Design System (30-60 min)

**Goal:** Define the complete visual language.

**Covers:**
- Color palette (backgrounds, text, functional colors, accents)
- Typography (font families, type scale, weights, line heights)
- Spacing (base unit, scale from xs to 3xl)
- Components (buttons, inputs, cards, borders, shadows)
- Motion (timing, easing)

**Outputs:**
- `[brand]-design-guidelines.md` — Comprehensive guidelines with CSS variables

**Example prompt:**
> "Create the design system with colors, typography, spacing, and components"

---

### Phase 6: DESIGN.md Creation (15-20 min)

**Goal:** Consolidate everything into a single master reference document.

**Process:**
- Pull from all previous phase outputs
- Create comprehensive DESIGN.md with brand narrative, visual system, and implementation specs
- Single-source-of-truth for anyone implementing the brand

**Outputs:**
- `DESIGN.md` — Complete brand reference document

**Example prompt:**
> "Create the DESIGN.md consolidating everything from Phases 0-5"

---

### Phase 7: Packaging (10-15 min)

**Goal:** Package everything for delivery or handoff.

**Process:**
- Collect all final assets
- Create quick-start README
- Organize into clean folder structure
- Zip for delivery (optional)

**Outputs:**
- `[brand]-brand-kit/` folder with all assets
- `[brand]-brand-kit.zip` (optional)

**Example prompt:**
> "Package the complete brand kit for delivery"

---

## 🎯 Brand Process Example Commands

### Starting Fresh

```
"Use the brand-skill at ~/Claude Skills/brand-skill/ to build a complete
brand identity for my project. The project is called [name] and it's a
[brief description]. Start with Phase 1: Discovery."
```

### Resuming Mid-Process

```
"Continue Phase 3 of the brand process. Here's the feedback on v1-v5:
[your feedback]. Create the next iteration batch."
```

### Skipping Phases

```
"I already have a logo. Skip to Phase 5 and create a design system
that complements this mark: [describe or reference logo]."
```

---

## 🖼️ Art Skill: Image Generation

The **art** skill provides structured workflows for AI image generation.

### Available Workflows

| Workflow | Purpose | Output |
|----------|---------|--------|
| `Visualize.md` | Adaptive content visualization | Infographics, data viz, mixed media |
| `TechnicalDiagrams.md` | Architecture and process diagrams | Excalidraw-style technical diagrams |
| `Stats.md` | Data visualization | Charts, graphs, quantitative displays |
| `Frameworks.md` | Conceptual frameworks | 2x2 matrices, taxonomies, mental models |
| `Essay.md` | Editorial illustrations | Metaphorical images for written content |
| `Mermaid.md` | Flowcharts and diagrams | Mermaid-compatible diagram generation |

### Usage Example

```
"Use the TechnicalDiagrams workflow from ~/Claude Skills/art/ to create
an architecture diagram showing [system description]"
```

### Dependencies

The art skill uses a CLI tool for image generation:
- Location: `~/.claude/skills/art/Tools/Generate.ts`
- Models: Supports Gemini (nano-banana-pro), Flux, and others
- Output: PNG images to specified location or ~/Downloads

---

## 🎨 Frontend Design Skill

Provides aesthetic guidelines to avoid generic "AI slop" patterns.

**Emphasizes:**
- Distinctive visual language
- Avoiding purple gradients, overly rounded shapes
- Meaningful color use (functional vs decorative)
- Professional typography
- Density and information hierarchy

**Usage:**
```
"Use the frontend-design guidelines to review this component and suggest improvements"
```

---

## 📂 Directory Structure

```
~/Claude Skills/
├── README.md                          ← You are here
├── brand-skill/
│   ├── SKILL.md                       # Main skill definition
│   ├── 00-Orchestrator.md             # Phase state tracker (read first)
│   ├── TOOLS-REQUIRED.md              # Prerequisites checklist
│   ├── Workflows/
│   │   ├── 00-EmotiveNarrative.md
│   │   ├── 01-Discovery.md
│   │   ├── 02-VisualDirection.md
│   │   ├── 03-MarkDevelopment.md      # Tracing-first logo workflow
│   │   ├── 04-Wordmark.md
│   │   ├── 05-DesignSystem.md
│   │   ├── 06-DesignMdCreation.md
│   │   └── 07-Packaging.md
│   ├── Templates/                     # Reusable templates
│   │   ├── philosophy-template.md
│   │   ├── visual-philosophy-template.md
│   │   ├── design-guidelines-template.md
│   │   └── readme-template.md
│   └── Examples/
│       └── sorted-brand-kit/          # Real-world example
│           ├── README.md
│           ├── sorted-philosophy.md
│           ├── sorted-design-guidelines.md
│           └── sorted-utility-sublime-philosophy.md
├── art/
│   ├── SKILL.md
│   ├── Tools/
│   │   └── Generate.ts                # Image generation CLI
│   └── Workflows/
│       ├── Visualize.md
│       ├── TechnicalDiagrams.md
│       ├── Stats.md
│       ├── Frameworks.md
│       ├── Essay.md
│       └── Mermaid.md
├── frontend-design/
│   └── SKILL.md
└── canvas-design/
    └── SKILL.md
```

---

## 💡 Tips for Success

### Working with Claude

1. **Be specific about phase** — "Start Phase 3" is clearer than "make a logo"
2. **Give directional feedback** — "Too playful, more serious" is better than "I don't like it"
3. **Iterate freely** — Version 15 is usually much better than version 3
4. **Test at scale** — Logos must work at 16px (favicon) and 200px (hero)
5. **Trust the process** — Each phase builds on the previous

### Brand Development

- **Start with research** — If Claude has codebase access, let it research first
- **Find the metaphor** — Strong brands have a central organizing idea
- **Color carries meaning** — Functional colors (green = success) shouldn't be decorative
- **Avoid generic patterns** — Purple gradients, overly rounded shapes, meaningless geometry
- **Test small sizes** — If the logo falls apart at 32px, simplify

### Image Generation

- **Use the right workflow** — Each has specific strengths
- **Provide context** — The more detail in your prompt, the better the output
- **Iterate** — First generation is a starting point, not the final product
- **Background matters** — Specify if you need transparent, white, or colored backgrounds

---

## 🔄 Updating Skills

When you improve a workflow or create new ones:

```bash
# Copy updates back to the library
cp -r ./path/to/project/.claude/skills/* ~/Claude\ Skills/

# Or copy specific skills
cp -r ./path/to/project/.claude/skills/brand-skill ~/Claude\ Skills/
```

---

## 📋 Real-World Examples

This skills library was used to create:

1. **Compost.fi** — Complete brand identity
   - Process documented at: `compost.fi/process.html`
   - ~2,600 API calls from philosophy to production
   - 26 logo iterations, full design system

2. **Sorted.fund** — "Utility Sublime" brand
   - Example included at: `brand-skill/Examples/sorted-brand-kit/`
   - Shows warm infrastructure aesthetic
   - Dense, functional design language

Both examples show the full 8-phase process in action.

---

## 🛠️ Dependencies

### Brand Skill

See `brand-skill/TOOLS-REQUIRED.md` for full details. Key requirements:

- **Required:** `rsvg-convert` (librsvg) — `brew install librsvg`
- **Recommended:** `vtracer` for PNG→SVG tracing — `cargo install vtracer`
- **Recommended:** `svgo` for SVG optimization — `npm install -g svgo`
- **Fallback:** freeconvert.com for browser-based tracing

### General
- Claude Code CLI (for running workflows)
- Access to Claude API (Sonnet 4.5 or Opus 4.5)

### Art Skill (Optional)
- Google Gemini API key (for image generation)
- Bun runtime (for Generate.ts)

---

## 📞 Need Help?

**Starting a new brand:**
```
"I want to build a brand using the brand-skill at ~/Claude Skills/.
My project is [description]. Walk me through Phase 1."
```

**Just need a logo:**
```
"Skip to Phase 3 of brand-skill. I need a logo for [project].
The brand should feel [adjectives]."
```

**Creating visualizations:**
```
"Use the Visualize workflow from ~/Claude Skills/art/ to create
an infographic showing [data/concept]."
```

---

## 📝 License

These workflows are personal tools. Use them for your own projects, modify them as needed, share with your team. Attribution appreciated but not required.

---

**Last Updated:** February 2026
**Version:** 1.1
**Created by:** Andy (with Claude Code)
