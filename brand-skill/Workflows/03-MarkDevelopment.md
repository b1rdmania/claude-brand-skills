# Phase 3: Mark Development

Iterate on the logo through SVG code until the user locks a final version.

## Time

20-60 minutes. This is typically the longest phase.

## Prerequisites

- Visual direction confirmed from Phase 2

---

## Process

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

## Gate

User explicitly locks: "That's the one."

---

## Pitfalls

- **Stopping early** — v15 beats v5 almost always
- **Ignoring small sizes** — If it fails at favicon, it fails
- **Over-detailing** — Simpler is better
- **Losing the concept** — Mark should connect to Phase 1's metaphor
- **Inconsistent weights** — Pick a weight, stick to it
