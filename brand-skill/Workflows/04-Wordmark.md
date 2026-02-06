# Phase 4: Wordmark & Lockups

Pair the mark with typography to create complete logo lockups.

## Time

10-20 minutes.

## Prerequisites

- Mark locked from Phase 3
- Know whether the mark is **hand-coded** (clean SVG, few paths) or **traced** (complex paths from vtracer/freeconvert)

---

## Mark Complexity Check

Before starting, check the mark file:

```bash
wc -c [brand]-mark-final.svg
```

- **Under ~5KB:** Clean/hand-coded. Embed directly into lockup SVGs (standard approach below).
- **Over ~5KB:** Likely traced with complex paths. Use the "Working with Traced Marks" section.

---

## Process

### 1. Pick Typography

Match font to brand personality:

| Personality | Font Direction |
|-------------|----------------|
| Technical/Dev | Monospace (JetBrains Mono, SF Mono) |
| Modern/Neutral | Geometric sans (Inter, Geist) |
| Enterprise | Neutral sans (Inter, Helvetica) |
| Friendly | Humanist sans (Work Sans) |
| Premium | Light weight sans or serif |

**Safe defaults:**
- **Inter** — Works everywhere, very legible
- **JetBrains Mono** — Developer/technical feel

### 2. Create Variants

Build 3-4 options:

**Name only:**
Mark + "brandname"

**Full domain:**
Mark + "brandname.com" (possibly with colored TLD)

**Monospace variant:**
Mark + "brandname" in mono

### 3. Align

This takes iteration. Considerations:

**Vertical:**
- Mark center vs text baseline
- Mark center vs text x-height
- Optical center (often different from mathematical)

**Horizontal:**
- Gap between mark and text
- Too tight feels cramped, too loose feels disconnected

**Scale:**
- Mark should balance with text weight
- May need to scale mark from original size

**Iterate with small adjustments:**
```svg
<g transform="translate(4, 6)">  <!-- Try 4,8 or 6,6 -->
<text x="58" y="36">  <!-- Try x="60" y="38" -->
```

### 4. Build the System

Create lockups for different contexts:

**Horizontal (primary)**
- Mark left, text right
- Headers, navigation, wide spaces

**Stacked**
- Mark above, text below
- Square formats, avatars

**Text-only**
- Name without mark
- Footers, inline mentions

---

## SVG Structure

```svg
<svg viewBox="0 0 [WIDTH] 56" fill="none" xmlns="http://www.w3.org/2000/svg">
  <!-- Mark (positioned) -->
  <g transform="translate([X], [Y])">
    [MARK PATHS]
  </g>

  <!-- Text -->
  <text
    x="[X]"
    y="[Y]"
    font-family="Inter, sans-serif"
    font-size="24"
    font-weight="500"
    fill="#e4e1e8"
  >
    brandname
  </text>
</svg>
```

**Width calculation:**
Mark width + gap + text width + padding

---

## Typography Settings

**Inter (default):**
```
font-family: "Inter", -apple-system, sans-serif
font-size: 22-28px
font-weight: 500
letter-spacing: -0.01em to -0.02em
```

**JetBrains Mono (technical):**
```
font-family: "JetBrains Mono", monospace
font-size: 20-24px (runs wider)
font-weight: 400
letter-spacing: 0 to 0.02em
```

---

## TLD Treatment

If including domain extension:

**Accent color:**
```svg
<tspan fill="#22c55e">.fund</tspan>
```
Ties to mark's accent.

**Muted:**
```svg
<tspan fill="#625e6c">.fund</tspan>
```
De-emphasizes extension.

**Same as name:**
Treats it as unified word.

---

## Working with Traced Marks

When the mark SVG is complex (traced from bitmap, dozens of paths, 10KB+), embedding it directly into a lockup SVG is impractical. Use one of these approaches:

### Approach 1: Group Reference (Simple)

Keep the mark paths in a `<g>` group and scale/translate the entire group:

```svg
<svg viewBox="0 0 [WIDTH] 56" fill="none" xmlns="http://www.w3.org/2000/svg">
  <!-- Mark: scaled down from original viewBox -->
  <g transform="translate([X], [Y]) scale(0.4)">
    <!-- Paste all mark paths here -->
  </g>

  <!-- Text -->
  <text x="[X]" y="[Y]" font-family="Inter, sans-serif" font-size="24" font-weight="500" fill="#e4e1e8">
    brandname
  </text>
</svg>
```

The `scale()` factor depends on the mark's original viewBox vs the lockup height. Calculate: `target_height / original_viewBox_height`.

### Approach 2: Bitmap Lockup → Re-trace

When the SVG is too unwieldy to embed:

1. Render the mark to PNG at the size needed for the lockup
2. Create the wordmark text as a separate SVG, render to PNG
3. Composite them together at the bitmap level (ImageMagick):
   ```bash
   # Render mark at lockup size
   rsvg-convert -h 48 [brand]-mark-final.svg -o mark-for-lockup.png

   # Create text SVG and render
   rsvg-convert -h 48 text-only.svg -o text-for-lockup.png

   # Composite horizontally with gap
   magick mark-for-lockup.png text-for-lockup.png +append -gravity center [brand]-wordmark-composite.png
   ```
4. If you need the lockup as SVG, trace the composite:
   ```bash
   vtracer --input [brand]-wordmark-composite.png --output [brand]-wordmark-final.svg
   ```

### Approach 3: Text-Only SVG + Separate Mark

Create lockups as instructions rather than single files:
- `[brand]-mark-final.svg` — The mark
- `[brand]-wordmark-textonly.svg` — Just the text
- Usage docs: "Place mark left, text right, gap of Xpx, vertically centered"

This is pragmatic when the combined SVG would be impractically large.

---

## Render and Verify

**After every lockup version, render and present:**

```bash
rsvg-convert -w 512 [brand]-wordmark-v1.svg -o wordmark-v1-preview.png
open wordmark-v1-preview.png
```

Never present SVG code as the final result. Always show the rendered output.

---

## Outputs

- `[brand]-wordmark-final.svg` — Primary horizontal
- `[brand]-wordmark-short.svg` — Compact variant
- `[brand]-wordmark-stacked.svg` — If needed

## Gate Check

1. Render all wordmark variants at 512px width
2. Present renders to the user
3. Ask: **"Phase 4 Gate Check — Wordmark lockups rendered above. Approved to proceed to Phase 5: Design System?"**
4. On approval: update `.brand-progress.md` → Phase 4: COMPLETE
5. Only proceed to Phase 5 when user explicitly approves

---

## Pitfalls

- **Mathematical vs optical** — Centered by numbers often looks wrong
- **Too tight** — Need breathing room
- **Mismatched weight** — Mark should feel balanced with text
- **Wrong font weight** — Too bold = clunky, too light = weak
- **Single context** — Test at different sizes and backgrounds
