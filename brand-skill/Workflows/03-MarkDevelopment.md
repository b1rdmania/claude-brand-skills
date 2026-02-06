# Phase 3: Mark Development

Develop the logo mark through tracing, hand-coding, or a combination of both.

## Time

20-60 minutes. This is typically the longest phase.

## Prerequisites

- Visual direction confirmed from Phase 2
- Tools verified (see `TOOLS-REQUIRED.md`): rsvg-convert required, vtracer recommended

---

## The Core Problem

LLMs cannot see their own SVG output. Iterating on complex shapes by editing SVG code blind leads to endless loops that never converge. This phase accounts for that limitation by offering two paths:

- **Path A (Tracing):** Generate or source a reference image, trace it to SVG, then refine
- **Path B (Hand-coded):** Build simple geometric marks directly in SVG code

Choose the path that fits the mark's complexity. Most marks with curves, organic shapes, or detailed geometry should use Path A.

---

## Path A: Reference → Trace → Refine (Primary)

**Use when:** The mark has curves, organic shapes, detailed geometry, or needs to match a visual reference from Phase 2.

### 1. Get a Reference Image

Start with a clean, high-contrast reference:

**From Phase 2 AI generation:**
```bash
# If using the art skill
bun run ~/.claude/skills/art/Tools/Generate.ts \
  --model nano-banana-pro \
  --prompt "Minimalist logo mark: [concept]. Black on white background. Simple, clean, geometric. No text." \
  --size 2K \
  --aspect-ratio 1:1 \
  --output ~/Downloads/[brand]-mark-ref.png
```

**From user:** Ask the user for a sketch, screenshot, or reference image.

**From earlier iteration:** Use a rendered PNG from a previous attempt as the new reference.

### 2. Trace to SVG

**With vtracer (recommended):**
```bash
# Basic trace — good starting point
vtracer --input [brand]-mark-ref.png --output [brand]-mark-draft.svg

# For cleaner output (fewer paths, smoother curves)
vtracer --input [brand]-mark-ref.png --output [brand]-mark-draft.svg \
  --colormode binary \
  --filter_speckle 4 \
  --corner_threshold 60 \
  --segment_length 4

# For color logos
vtracer --input [brand]-mark-ref.png --output [brand]-mark-draft.svg \
  --colormode color \
  --filter_speckle 4 \
  --color_precision 6
```

**With freeconvert.com (fallback):**
1. Go to https://www.freeconvert.com/png-to-svg
2. Upload the reference PNG
3. Download the resulting SVG
4. Save as `[brand]-mark-draft.svg`

### 3. Optimize the Traced SVG

Traced SVGs are often bloated. Clean them up:

```bash
# Optimize with svgo (if available)
svgo [brand]-mark-draft.svg -o [brand]-mark-v1.svg

# Or manually: open the SVG, remove unnecessary metadata, simplify viewBox
```

Key cleanup tasks:
- Set a clean viewBox (e.g., `viewBox="0 0 64 64"` or `viewBox="0 0 128 128"`)
- Remove unnecessary `<metadata>`, `<defs>`, empty groups
- Adjust colors to match brand palette
- Remove background shapes (keep only the mark)

### 4. Render and Verify

**This step is mandatory after every SVG change.**

```bash
# Review size (512px)
rsvg-convert -w 512 -h 512 [brand]-mark-v1.svg -o [brand]-mark-v1-preview.png
open [brand]-mark-v1-preview.png

# Favicon size (32px) — always test this
rsvg-convert -w 32 -h 32 [brand]-mark-v1.svg -o [brand]-mark-v1-32px.png
open [brand]-mark-v1-32px.png
```

Present both renders to the user:
> **Mark v1** — [Description of what this version looks like]
> Rendered at 512px and 32px. How does this look?

### 5. Refine

Based on user feedback, adjust the SVG:
- Simplify paths for small-size readability
- Adjust colors
- Modify proportions
- Remove or add elements

**After every change:** Re-render and verify (Step 4). Never present un-rendered SVG code as "the result."

### 6. Iteration Limits

**If the mark isn't converging after 5-8 refinement rounds:**

1. **Stop.** Don't keep editing SVG paths hoping to get closer.
2. **Assess the problem:**
   - If the shape is wrong: generate a new reference image and re-trace
   - If the trace quality is poor: try freeconvert.com for a different trace
   - If the concept isn't working: go back to Phase 2 for new directions
3. **Tell the user:** "The current approach isn't converging. I recommend [specific alternative]."

**Never:** Loop endlessly refining SVG code. The LLM cannot see the output — blind iteration past 5-8 rounds is wasted effort.

---

## Path B: Hand-Coded Geometric Marks

**Use when:** The mark is simple geometry — circles, lines, rectangles, basic compositions. The kind of mark you could describe precisely in coordinates.

### 1. Initial Batch (v1-v5)

Create 4-5 SVG variations exploring the chosen direction.

```svg
<svg viewBox="0 0 64 64" fill="none" xmlns="http://www.w3.org/2000/svg">
  <!-- Content -->
</svg>
```

Use 64x64 viewBox consistently.

**Vary across:**
- Shape interpretation (curved vs angular)
- Proportions (compact vs extended)
- Stroke weight (thin vs bold)
- Accent placement (where does color go?)

### 2. Render and Verify

**Mandatory after every version.** Same as Path A Step 4:

```bash
rsvg-convert -w 512 -h 512 mark-v1.svg -o mark-v1-preview.png
rsvg-convert -w 32 -h 32 mark-v1.svg -o mark-v1-32px.png
open mark-v1-preview.png
```

### 3. Present and Iterate

Show rendered versions with brief descriptions:

> **v1** — [What this explores]. Rendered at 512px and 32px.
> **v2** — [What this explores]
> **v3** — [Different interpretation]

| They say | You do |
|----------|--------|
| "v3 is good" | Make 3-4 refinements of v3 |
| "v2 or v4" | Find common thread, create hybrids |
| "v3 but bolder" | Increase stroke weight, scale up |
| "v3 but simpler" | Remove elements, reduce detail |
| "None of these" | Go back to Phase 2 or try new approach |

### 4. Iteration Limits (Same as Path A)

If not converging after 5-8 rounds: stop, reassess, pivot. Consider switching to Path A (generate a reference of what you're trying to achieve, then trace it).

---

## SVG Techniques (Path B Reference)

**Organic curves:**
```svg
<path
  d="M16 16 Q 16 32, 32 32 Q 48 32, 48 48"
  stroke="#52505a"
  stroke-width="8"
  stroke-linecap="round"
  fill="none"
/>
```

**Basic shapes:**
```svg
<circle cx="48" cy="48" r="6" fill="#22c55e"/>
<rect x="10" y="30" width="44" height="10" rx="4" fill="#52505a"/>
```

**Arcs:**
```svg
<path
  d="M8 40 A24 24 0 0 1 56 40"
  stroke="#52505a"
  stroke-width="8"
  stroke-linecap="round"
  fill="none"
/>
```

**Key settings:**
- `stroke-linecap="round"` — Softer endpoints
- `fill="none"` — For stroke-only paths
- `rx` on rects — Rounded corners

---

## Working with Complex Traced SVGs

Traced SVGs can be large (100KB+) with dozens of paths. Tips:

**Simplify with svgo:**
```bash
svgo [brand]-mark-v1.svg -o [brand]-mark-v1-clean.svg --pretty
```

**Manual simplification:**
- Remove paths that are background artifacts
- Merge paths with the same fill color
- Replace complex curves with simpler approximations (only for hand-editable marks)

**When the SVG is too complex to edit by hand:**
- Don't try to edit individual path data points
- Instead: render to PNG, modify the PNG concept (new reference image), re-trace
- This is the "generate → trace → refine at bitmap level → re-trace" loop

---

## Mark Categories

**Flowing/Organic** → Usually Path A
- Curves, waves, S-shapes
- Suggests movement, continuity

**Geometric** → Usually Path B
- Circles, squares, precise angles
- Suggests stability, precision

**Abstract Symbol** → Path A or B depending on complexity
- Simplified representation of concept

**Letterform** → Path A recommended
- Based on brand initial
- Typography-based marks are hard to hand-code well

---

## Quality Checks

Before locking, render at all sizes and verify:

```bash
rsvg-convert -w 256 -h 256 [brand]-mark-final.svg -o preview-256.png
rsvg-convert -w 64 -h 64 [brand]-mark-final.svg -o preview-64.png
rsvg-convert -w 32 -h 32 [brand]-mark-final.svg -o preview-32.png
rsvg-convert -w 16 -h 16 [brand]-mark-final.svg -o preview-16.png
```

- [ ] Reads at 256px (hero)
- [ ] Reads at 64px (app icon)
- [ ] Reads at 32px (favicon)
- [ ] Reads at 16px (tiny favicon)
- [ ] Works as silhouette (single color test)
- [ ] No disappearing details
- [ ] Colors are intentional
- [ ] Weights are consistent
- [ ] Optically balanced

---

## Lock and Export

User says: "That's it" / "Lock this one" / "Perfect"

```bash
# Save final mark
cp [brand]-mark-v[n].svg [brand]-mark-final.svg

# Export favicon
rsvg-convert -w 32 -h 32 [brand]-mark-final.svg -o [brand]-favicon.png
```

---

## Outputs

- `[brand]-mark-v[n].svg` — Iterations
- `[brand]-mark-final.svg` — Locked version
- `[brand]-favicon.png` — 32px export
- `[brand]-mark-*-preview.png` — Rendered previews (can be cleaned up)

## Gate Check

1. Render the final mark at 512px, 32px, and 16px
2. Present all three renders to the user
3. Ask: **"Phase 3 Gate Check — Mark renders at 512px, 32px, and 16px shown above. Approved to proceed to Phase 4: Wordmark?"**
4. On approval: update `.brand-progress.md` → Phase 3: COMPLETE
5. Only proceed to Phase 4 when user explicitly approves

---

## Pitfalls

- **Blind SVG iteration** — The #1 failure mode. If you can't see the output, you can't refine it. Always render.
- **No iteration limit** — Set a hard limit of 5-8 rounds. After that, change approach.
- **Ignoring small sizes** — If it fails at favicon, it fails
- **Over-detailing** — Simpler is better, especially for traced marks
- **Losing the concept** — Mark should connect to Phase 1's metaphor
- **Editing complex traced paths by hand** — Don't. Re-trace from a modified reference instead.
