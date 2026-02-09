# Phase 3: Mark Development

Iterate on the logo until the user locks a final version.

## Time

20-90 minutes. This is typically the longest phase.

## Prerequisites

- Visual direction confirmed from Phase 2

---

## LLM Honesty: Know Your Limits Here

**Be transparent with the user:** LLMs struggle with mark development because they write SVG as text tokens without seeing the visual result. For simple geometric marks (circles, squares, basic monograms), hand-coded SVG works. For anything with complex curves, letterforms, or illustrative elements, hand-coding will likely fail — expect 5-8 iterations before pivoting to bitmap tracing.

Tell the user upfront: "I can hand-code geometric marks well. For complex shapes, I'll try a few iterations, but if it's not converging we should switch to tracing from a reference image — that's faster and produces better results."

---

## Approach Selection

Choose the right approach based on mark complexity:

### Path A: Hand-coded SVG (geometric marks)

Best for: circles, squares, basic monograms, simple abstract shapes, stroke-based marks.

Use this when the mark is **geometrically describable** — you could explain the construction with compass and ruler.

### Path B: Bitmap tracing (complex marks)

Best for: letterforms, illustrative elements, organic shapes, anything with complex curves.

**Process:**
1. Generate or obtain a reference image (from Phase 2, or user provides)
2. Trace with a vector tool:

   **Option A: Local tools (best quality, smallest files)**
   ```bash
   # vtracer (recommended — better curve handling)
   brew install vtracer
   vtracer --input mark-reference.png --output mark-traced.svg

   # OR potrace (simpler, good for high-contrast images)
   brew install potrace
   potrace -s mark-reference.bmp -o mark-traced.svg
   ```

   **Option B: Browser-based (no install needed)**
   If vtracer/potrace aren't available or aren't producing good results, use [freeconvert.com/png-to-svg](https://www.freeconvert.com/png-to-svg):
   - Upload the reference PNG
   - Download the traced SVG
   - Copy the SVG content into your file

   Browser-traced SVGs will be larger than locally-traced ones — that's fine. **Fidelity to the reference image matters more than file size.** The mark needs to look right first. You can optimize later with SVGO, but don't sacrifice visual accuracy for smaller files.

3. Optimize with SVGO:
   ```bash
   npx svgo@latest mark-traced.svg -o mark-optimized.svg
   ```
   **Note:** If SVGO optimization visibly degrades the mark (lost details, simplified curves), keep the unoptimized version. A 150KB SVG that looks right beats a 30KB SVG that doesn't.

4. Manually refine paths if needed (adjust viewBox, clean up artifacts)
5. Render to verify: `qlmanage -t -s 512 -o /tmp mark-optimized.svg`

### Path C: Hybrid

Start with hand-coded SVG. If not converging after 5-8 iterations, pivot to bitmap tracing. Don't burn 30 iterations trying to hand-code something that tracing would solve in minutes.

---

## Process (Hand-coded Path)

### 1. Initial Batch (v1-v5)

Create 4-5 SVG variations exploring the chosen direction.

**SVG setup:**
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

### 2. Convert for Preview

**With rsvg-convert:**
```bash
# Full size
rsvg-convert -w 256 -h 256 mark-v1.svg -o mark-v1.png

# Favicon size — always test this
rsvg-convert -w 32 -h 32 mark-v1.svg -o mark-v1-favicon.png
```

**Without rsvg-convert:**
- Open SVG in browser, use DevTools to screenshot at specific sizes
- Use online converter (svgtopng.com, cloudconvert.com)
- Ask user to export from Preview/Figma/other tool
- For size testing, zoom browser to approximate pixel sizes

If it doesn't work at 32px, simplify.

### 3. Present Batch

Show versions with brief descriptions:

> **v1** — [What this explores]
> **v2** — [What this explores]
> **v3** — [Different interpretation]

Ask: "Which direction? Or try something else?"

### 4. Read Feedback

| They say | You do |
|----------|--------|
| "v3 is good" | Make 3-4 refinements of v3 |
| "v2 or v4" | Find common thread, create hybrids |
| "v3 but bolder" | Increase stroke weight, scale up |
| "v3 but simpler" | Remove elements, reduce detail |
| "None of these" | Go back to Phase 2 or try new approach |
| "Maybe weird" | Identify what's off, adjust |

### 5. Iterate (v6-v15)

Refine based on feedback:
- Adjust curves
- Change proportions
- Modify weights
- Shift color placement
- Simplify for small sizes

### 6. Polish (v16-v25+)

Once direction is locked, focus on:
- Optical balance (mathematical center often looks wrong)
- Consistent stroke weights
- Color value tuning
- Size testing

### 7. Lock

User says: "That's it" / "Lock this one" / "Perfect"

Save as `[brand]-mark-final.svg`

---

## SVG Techniques

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
<circle cx="48" cy="48" r="6" fill="{BRAND_ACCENT}"/>
<rect x="10" y="30" width="44" height="10" rx="4" fill="{TEXT_MUTED}"/>
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

## Mark Categories

**Flowing/Organic**
- Curves, waves, S-shapes
- Suggests movement, continuity
- Works for: process, data, infrastructure

**Geometric**
- Circles, squares, precise angles
- Suggests stability, precision
- Works for: finance, security, enterprise

**Abstract Symbol**
- Simplified representation of concept
- Suggests meaning, identity
- Works for: distinctive recognition

**Letterform**
- Based on brand initial
- Suggests identity, recognition
- Works for: consumer brands, memorable names

---

## Quality Checks

Before locking:

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

## Outputs

- `[brand]-mark-v[n].svg` — Iterations
- `[brand]-mark-final.svg` — Locked version
- `[brand]-favicon.png` — 32px export

## Gate Check

1. Present the final mark at multiple sizes (256px, 64px, 32px) to the user
2. Ask: **"Phase 3 Gate Check — Mark locked as final. Approved to proceed to Phase 4: Wordmark?"**
3. On approval: update `.brand-progress.md` → Phase 3: COMPLETE
4. Only proceed to Phase 4 when user explicitly approves

---

## Iteration Limits and Escape Hatches

**Do not iterate indefinitely.** If the mark isn't converging, change approach rather than grinding.

| Iteration count | Action |
|----------------|--------|
| v1-v5 | Initial exploration — expect nothing final |
| v6-v10 | Direction should be clear. If not, revisit Phase 2. |
| v11-v15 | Should be refining, not still exploring. If still exploring, **pivot approach.** |
| v16+ | Only justified for polish on a locked direction. If still searching at v16, stop and either: switch to bitmap tracing, simplify the concept, or ask user to provide a reference image to trace. |

**Escape hatches:**
1. **Simplify the concept.** If a complex mark isn't working, try a simpler version of the same idea.
2. **Switch to bitmap tracing.** Generate a reference image, trace it, optimize. This is not a failure — it's the right tool for the job.
3. **Use an external tool.** Ask the user to sketch something (even rough) and photograph it. Trace the photo.
4. **Present current best.** Show the user the best iteration so far and ask: "Is this close enough to refine, or should we try a completely different concept?"

---

## Render and Verify (MANDATORY)

After every SVG creation, render to verify visually:

```bash
# macOS (Quick Look)
qlmanage -t -s 512 -o /tmp mark-v1.svg
open /tmp/mark-v1.svg.png

# Browser
open mark-v1.svg

# Favicon size test
qlmanage -t -s 32 -o /tmp mark-v1.svg
```

Never present an SVG to the user without rendering it first. You cannot see what you've written — the render is how you check.

---

## Pitfalls

- **Grinding past v15 without changing approach** — This is the #1 failure mode. Pivot, don't grind.
- **Not rendering** — You can't see SVG as text. Always render.
- **Ignoring small sizes** — If it fails at favicon, it fails
- **Over-detailing** — Simpler is better
- **Losing the concept** — Mark should connect to Phase 1's metaphor
- **Inconsistent weights** — Pick a weight, stick to it
