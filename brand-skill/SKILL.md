---
name: Brand
description: Complete brand development system with emotive foundation. Triggers on requests for brand identity, logos, visual systems, or design guidelines. Creates distinctive, anti-AI-slop design from strategy through delivery.
---

# Brand Skill

Build complete brand identities that are coherent, distinctive, and impossible to confuse with generic AI output.

## What Makes This Different

**Anti-AI-Slop Focus:** This process creates brands that are:
- **Emotionally grounded** — Every visual choice connects to human meaning
- **Systematically distinctive** — Coherent systems, not random "modern" aesthetics
- **Intentionally crafted** — Expert-level refinement, not first-draft defaults

**The secret:** Start with **emotive narrative** before any visual work. This creates deep LLM memory that prevents generic drift.

---

## Structure

```
brand-skill/
├── SKILL.md                      # Overview and routing (you are here)
├── Workflows/
│   ├── 00-EmotiveNarrative.md    # Soul of the brand (NEW)
│   ├── 01-Discovery.md            # Strategy and positioning
│   ├── 02-VisualDirection.md      # Reference exploration
│   ├── 03-MarkDevelopment.md      # Logo iteration
│   ├── 04-Wordmark.md             # Typography and lockups
│   ├── 05-DesignSystem.md         # Complete system (web + iOS)
│   ├── 06-DesignMdCreation.md     # Consolidate to DESIGN.md (NEW)
│   └── 07-Packaging.md            # Final delivery
├── Templates/
│   ├── DESIGN-template.md         # Comprehensive DESIGN.md template (NEW)
│   ├── philosophy-template.md
│   ├── visual-philosophy-template.md
│   ├── design-guidelines-template.md
│   └── readme-template.md
└── Examples/
    └── sorted-brand-kit/          # Real-world example
```

---

## Triggers

- "Build a brand for [project]"
- "Create brand guidelines"
- "Design a logo and visual system"
- "I need a complete identity that doesn't look like AI slop"
- "Help me create a design system with iOS and web specs"

---

## The Process (7 Phases)

### Phase 0: Emotive Narrative ⭐ NEW
**Create the soul before the visuals**

**Output:** Beautiful emotive narrative in 4-6 paragraphs
- The human moment (why this matters)
- The transformation (what becomes possible)
- The ethos (values and principles)
- The personality (how it moves through the world)
- The north star (guiding light for decisions)

**Why first:** This becomes the emotional context that every subsequent phase references. It prevents generic "clean and modern" drift by grounding all choices in human meaning.

**Time:** 20-30 minutes

---

### Phase 1: Discovery
**Establish strategic foundation**

**Output:** Brand positioning, voice guidelines
- Positioning statement
- Core metaphor
- Brand personality traits
- Voice and tone principles

**Context-aware:** If you have codebase access, read project files first and draft a positioning hypothesis. Don't open with a questionnaire.

**Time:** 15-20 minutes

---

### Phase 2: Visual Direction
**Generate reference images to find aesthetic territory**

**Output:** Reference images (PNG) exploring directions
- 3-4 prompts exploring different interpretations
- User picks direction(s)
- Generate refinements if needed

**Optional:** Can skip and go straight to SVG iteration (Phase 3)

**Time:** 10-15 minutes

---

### Phase 3: Mark Development
**Iterate on logo through SVG sketches**

**Output:** `[brand]-mark-final.svg`, favicon PNG
- 15-30 iterations typical
- Test at favicon sizes (32px, 16px)
- Lock final version

**Time:** 45-90 minutes

---

### Phase 4: Wordmark
**Pair the mark with typography**

**Output:** `[brand]-wordmark-final.svg`, variants
- Horizontal, stacked, text-only lockups
- Refine alignment through iteration
- Test in real-world contexts

**Time:** 30-45 minutes

---

### Phase 5: Design System ⭐ UPDATED
**Define complete visual language for web AND iOS**

**Output:** `[brand]-design-guidelines.md`
- Colors (web CSS + iOS Swift)
- Typography (web + iOS with Dynamic Type)
- Spacing (unified 8pt/px base)
- Components (web + iOS implementations)
- Motion and animation principles
- Platform-specific considerations

**Includes iOS specifications:**
- SwiftUI components
- Asset Catalog setup
- Dynamic Type support
- Safe area handling
- Touch target guidelines

**Time:** 30-60 minutes

---

### Phase 6: DESIGN.md Creation ⭐ NEW
**Consolidate everything into one master reference**

**Output:** `DESIGN.md` (comprehensive, living document)

**Contains:**
1. Emotive Narrative (from Phase 0)
2. Strategic Foundation (from Phase 1)
3. Visual Philosophy (from Phase 1/2)
4. Logo System (from Phase 3/4)
5. Design Tokens (colors, type, spacing — web + iOS)
6. Components (implementation for web + iOS)
7. Implementation Guidelines (platform-specific specs)
8. Anti-AI-Slop Principles (quality validation)

**Why critical:** Single source of truth. Any LLM can read DESIGN.md and understand the complete brand — preventing generic drift forever.

**Time:** 20-30 minutes

---

### Phase 7: Packaging
**Collect assets for handoff**

**Output:** `[brand]-brand-kit/` folder (or .zip)
- All final assets organized
- Quick-start README
- DESIGN.md as master reference

**Time:** 10-15 minutes

---

## Total Time Investment

- **Fast track:** 3-4 hours (clear direction, minimal iteration)
- **Full process:** 5-7 hours (exploration and refinement)
- **Complex brands:** 8+ hours (multiple concepts, extensive iteration)

---

## Key Outputs

### During Process
- `[brand]-emotive-narrative.md` (Phase 0)
- `[brand]-philosophy.md` (Phase 1)
- `[brand]-visual-philosophy.md` (Phase 1/2)
- Reference images (Phase 2)
- `[brand]-mark-final.svg` + favicon (Phase 3)
- `[brand]-wordmark-*.svg` (Phase 4)
- `[brand]-design-guidelines.md` (Phase 5)

### Final Deliverable
- **`DESIGN.md`** — The single source of truth (Phase 6)
- **Brand kit folder** — All assets packaged (Phase 7)

---

## Anti-AI-Slop Framework

### What This Prevents

❌ Generic "clean and modern" aesthetics
❌ Purple-to-blue gradients without reason
❌ Rounded corners everywhere "because friendly"
❌ Copy-paste component libraries without customization
❌ Random spacing/sizing not from a system
❌ Arbitrary design decisions "because it looks nice"

### How It Prevents This

✅ **Emotive narrative** grounds every choice in meaning
✅ **Visual philosophy** defines a specific aesthetic movement
✅ **Systematic tokens** (8px spacing, named colors, consistent radii)
✅ **Decision testing framework** (every choice must answer "why")
✅ **Validation checklists** (coherence, craft, distinctiveness)
✅ **DESIGN.md** embeds the philosophy so future work stays coherent

---

## Guidelines

### On Iteration

Don't aim for perfection on the first try. The process is:
- Generate options
- Get reaction
- Refine
- Repeat

Version 15 is usually much better than version 3.

### On User Input

You bring expertise; they bring taste. Present options with your reasoning, but let them choose. Use `AskUserQuestion` when you genuinely need direction, not for validation.

### On Emotive Foundation

**Phase 0 is not optional.** Skipping it leads to soulless design. The narrative creates:
- Deep LLM memory (prevents generic drift)
- Decision framework (test choices against the narrative)
- Emotional coherence (visual system expresses the story)

### On Testing

Logos exist at multiple sizes: hero (200px+), app icon (64px), favicon (32px, 16px). Test all of them. If it falls apart small, simplify.

### On Color

Dark backgrounds should have warmth — pure #000 feels lifeless. Functional colors (green for success, red for error) carry meaning; don't use them decoratively.

### On Platform Specificity

**Web and iOS should feel like "the same brand" but native to their platforms:**
- Web can be more expressive (gradients, shadows)
- iOS should use system conventions (SF Pro, native navigation)
- Color palette and spacing rhythm stay identical
- Components recognizably "the same" but platform-appropriate

### On Quality

Avoid generic patterns: purple-blue gradients, overly rounded shapes, meaningless geometric decorations. Create something distinctive that the brand can own.

**Remember:** Generic is easy. Distinctive takes intention.

---

## Dependencies

### Image Generation (Optional)

Phase 2 can use AI image generation for reference exploration. Options:

1. **Art skill** — If you have the Art skill installed, use its Generate.ts tool
2. **Manual references** — User provides mood board images or links
3. **Skip to SVG** — Go directly to Phase 3, iterate on concepts through code

If skipping image generation, start Phase 3 with more initial variations (8-10 instead of 4-5).

### SVG to PNG Conversion

For favicon generation, you need `rsvg-convert`:

```bash
# macOS
brew install librsvg

# Ubuntu/Debian
sudo apt-get install librsvg2-bin

# Check installation
rsvg-convert --version
```

**Alternative:** If unavailable, use online converter or ask user to export.

### Fonts

Uses system fonts by default. For web fonts:
- **Inter** — `https://fonts.google.com/specimen/Inter`
- **JetBrains Mono** — `https://fonts.google.com/specimen/JetBrains+Mono`

For iOS: SF Pro (system font) is preferred for native feel.

---

## Workflow Files

Each phase has detailed instructions in `Workflows/`:

- `00-EmotiveNarrative.md` — Create the soul and emotional foundation ⭐ NEW
- `01-Discovery.md` — Full discovery process with context-aware mode
- `02-VisualDirection.md` — Reference image generation guide
- `03-MarkDevelopment.md` — SVG iteration techniques
- `04-Wordmark.md` — Typography pairing and alignment
- `05-DesignSystem.md` — Token and component definitions (web + iOS) ⭐ UPDATED
- `06-DesignMdCreation.md` — Consolidate to master DESIGN.md ⭐ NEW
- `07-Packaging.md` — Asset collection and handoff

Read the relevant workflow file when executing each phase.

---

## The DESIGN.md Advantage

**Why this matters:**

Traditional brand systems:
- Scattered across multiple files
- Knowledge lives in people's heads
- Design drift happens over time
- Generic patterns creep in

**With DESIGN.md:**
- ✅ One file, complete system
- ✅ Any LLM can read and maintain consistency
- ✅ Emotive narrative embedded (prevents generic drift)
- ✅ Platform-specific implementations (web + iOS)
- ✅ Anti-AI-slop validation built in
- ✅ Onboarding is instant
- ✅ Brand stays distinctive forever

**This is the insurance policy against generic design.**

---

## Example Usage

### Starting Fresh

```
"Use the brand-skill to build a complete brand identity for [project].
Start with Phase 0: create the emotive narrative that captures the soul
of what we're building."
```

### Resuming Mid-Process

```
"Continue Phase 3 of the brand process. Here's feedback on v1-v5:
[your feedback]. Create the next iteration batch."
```

### Skipping Phases

```
"I already have a logo. Skip to Phase 5 and create a design system
(web + iOS) that complements this mark: [describe logo]."
```

### Final Consolidation

```
"We've completed Phases 0-5. Now create the master DESIGN.md file
that consolidates everything into one comprehensive reference."
```

---

## Quality Standards

Every brand created with this skill should:

1. **Have emotional depth** (not just visual style)
2. **Be systematically coherent** (not random choices)
3. **Feel distinctive** (not generic/interchangeable)
4. **Work cross-platform** (web + iOS implementations)
5. **Be implementable** (copy-paste ready code)
6. **Stay consistent** (DESIGN.md prevents drift)

**If it could be any "clean and modern" brand, we failed.**

---

## Real-World Examples

This skills library was used to create:

1. **Compost.fi** — "Quiet Infrastructure" brand
   - Process documented at: `compost.fi/process.html`
   - ~2,600 API calls from philosophy to production
   - 26 logo iterations, full design system

2. **Sorted.fund** — "Utility Sublime" brand
   - Example included at: `Examples/sorted-brand-kit/`
   - Warm infrastructure aesthetic
   - Dense, functional design language

Both show the full 7-phase process in action, with distinctive results.

---

*Last Updated: February 2026 — Version 2.0*
*Now with emotive narrative foundation, iOS specifications, and DESIGN.md consolidation*
