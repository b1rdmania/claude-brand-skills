# Phase 2: Visual Direction

Explore visual territories before committing to detailed SVG work.

## Time

10-20 minutes depending on exploration rounds.

## Prerequisites

- Phase 1 complete with approved positioning

## Before You Start: API Keys for Image Generation

**Image generation is optional but recommended.** If you want to use Mode A (AI-generated reference images), you'll need at least one of these API keys set as environment variables:

| Model | Env Variable | Get it from |
|-------|-------------|-------------|
| `nano-banana-pro` (recommended) | `GOOGLE_API_KEY` | [Google AI Studio](https://aistudio.google.com/) |
| `nano-banana` / `flux` | `REPLICATE_API_TOKEN` | [Replicate](https://replicate.com/) |
| `gpt-image-1` | `OPENAI_API_KEY` | [OpenAI](https://platform.openai.com/) |

**Don't have API keys? That's fine.** Phases 0 (Emotive Narrative) and 1 (Discovery) work perfectly without any image generation — they're pure text and strategy. When you reach this phase, you can:
- **Mode B**: Supply your own mood boards, screenshots, or reference images
- **Mode C**: Skip image generation entirely and go straight to SVG iteration in Phase 3

See `TOOLS-REQUIRED.md` for full setup details.

---

## Modes

This phase can work three ways:

**Mode A: AI Image Generation** — Generate reference images to explore directions visually. Requires image generation API (Art skill or similar).

**Mode B: User-Provided References** — User supplies mood board, screenshots, or links. You analyze and identify common threads.

**Mode C: Skip to SVG** — Go directly to Phase 3 with expanded initial batch (8-10 variations). Explore directions through code iteration.

---

## Process

### 1. Write Exploration Prompts

Based on the visual philosophy, craft 3-4 prompts that explore different interpretations of the concept.

**Prompt structure:**
```
"Abstract minimalist logo concept: [VISUAL IDEA].
Clean vector style, [BACKGROUND DESCRIPTION].
[PRIMARY ELEMENT] with [ACCENT] suggesting [MEANING].
[STYLE NOTES].
Simple enough for small sizes. No text."
```

**Example set** (for an infrastructure brand):

*Prompt 1 — Connection:*
> "Abstract minimalist logo concept: three conduits meeting at a junction point. Dark charcoal background. Warm gray pipes with bright green accent showing flow direction. Architectural precision. No text."

*Prompt 2 — Flow:*
> "Abstract minimalist logo concept: single curved conduit suggesting smooth passage. Dark background. Metallic gray with green glow at terminus. Plumbing reduced to essence. No text."

*Prompt 3 — Circulation:*
> "Abstract minimalist logo concept: segmented ring showing continuous flow. Dark background. Gray segments with one green active section. Perpetual operation. No text."

*Prompt 4 — Layers:*
> "Abstract minimalist logo concept: horizontal strata with vertical element passing through. Dark background. Gray layers, green vertical showing throughput. Depth and systems. No text."

### 2. Generate Images

> **Need API keys?** This step requires a configured image generation API. If you haven't set one up, check the "Before You Start" section above — or skip to **Mode B** (your own references) or **Mode C** (straight to SVG) below. Everything before this point (Phases 0-1) works without image generation.

**Use any text-to-image tool you have access to:**
- Gemini (Google AI Studio)
- DALL-E / ChatGPT image generation
- Midjourney
- Stable Diffusion / Flux (via Replicate)
- Any other image generation API or tool

**Tips:**
- Keep prompts abstract and specify "no text", "logo concept", "minimalist"
- Square aspect ratio works best for logo references
- Generate at the highest resolution available

**If no image generation available:** Use Mode B (your own references) or Mode C (skip to SVG) below. Both produce equally good results — image generation just speeds up the exploration.

Name files descriptively: `[brand]-ref-1-junction.png`, `[brand]-ref-2-flow.png`, etc.

### 3. Present Options

Show all references with brief explanations:

> **Ref 1 — Junction**
> Three-way meeting point. Suggests routing and connection.
>
> **Ref 2 — Flow**
> Curved path with glowing output. Smooth, uninterrupted.
>
> **Ref 3 — Loop**
> Segmented circle. Continuous operation.
>
> **Ref 4 — Layers**
> Vertical through horizontal. Depth and infrastructure.

### 4. Get Direction

User picks what resonates:
- "The circular one"
- "2 and 4 are interesting"
- "None of these — try something more..."

### 5. Refine If Needed

Generate 2-3 more exploring the chosen territory:

```bash
# Variations on circular direction
bun run ... --prompt "Abstract logo: broken circle with connector bridging the gap..."
```

### 6. Confirm Before Proceeding

> "We're going with [direction]. Ready for SVG work?"

---

## Prompt Guidance

**Do:**
- Stay abstract and geometric
- Specify the background
- Mention "simple" or "favicon-ready"
- Connect to the metaphor from Phase 1
- Describe color relationships

**Avoid:**
- Literal representations (actual gas pumps, literal chains)
- Tech clichés (generic cubes, network nodes, globe imagery)
- Text in the logo
- Over-specifying (leave room for surprise)

---

## Outputs

- Reference images (typically 4-8 PNGs)

## Gate Check

1. Present the chosen reference images / direction to the user
2. Ask: **"Phase 2 Gate Check — Direction confirmed as [chosen direction]. Approved to proceed to Phase 3: Mark Development?"**
3. On approval: update `.brand-progress.md` → Phase 2: COMPLETE
4. Only proceed to Phase 3 when user explicitly approves

---

## Mode B: User-Provided References

If the user has existing references:

### 1. Collect References

Ask user to share:
- Screenshots or images they like
- Links to brands they admire
- Mood boards or Pinterest collections
- Descriptions of what resonates

### 2. Analyze Patterns

Look for common threads:
- Shape language (geometric vs organic)
- Color sensibility (warm, cool, muted, vibrant)
- Density (minimal vs detailed)
- Mood (serious, playful, technical, approachable)

### 3. Synthesize Direction

> "Across your references I see: [pattern 1], [pattern 2], [pattern 3]. Does that match your instinct?"

### 4. Define Constraints

From the analysis, establish:
- Shape direction (curves, angles, or mixed)
- Color territory (palette range)
- Complexity level (minimal, moderate, detailed)

Then proceed to Phase 3 with these constraints.

---

## Mode C: Skip to SVG Exploration

If no image generation is available and user has no references:

### 1. Define Verbal Directions

Based on Phase 1's philosophy, articulate 3-4 distinct approaches in words:

> **Direction A — Geometric precision:** Clean shapes, mathematical relationships, technical feel.
>
> **Direction B — Organic flow:** Curves, natural movement, approachable.
>
> **Direction C — Typographic:** Letterform-based, bold, distinctive.
>
> **Direction D — Abstract symbol:** Conceptual mark representing the core metaphor.

### 2. Get Initial Preference

Ask which direction(s) to explore first.

### 3. Expand Phase 3

Instead of 4-5 initial SVG variations, create 8-10 spanning:
- 3-4 in the primary chosen direction
- 2-3 in secondary direction if mentioned
- 1-2 wildcards

This front-loads the exploration into the SVG phase.

---

## Pitfalls

- **Too literal** — References should be abstract, not icons of what the product does
- **Too many options** — 3-4 directions is enough; more creates decision paralysis
- **Skipping entirely** — Even with a clear idea, some exploration usually reveals better directions
- **Treating references as finals** — They're sketches to find territory, not finished logos
