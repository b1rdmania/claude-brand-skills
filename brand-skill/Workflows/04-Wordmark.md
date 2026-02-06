# Phase 4: Wordmark & Lockups

Pair the mark with typography to create complete logo lockups.

## Time

10-20 minutes.

## Prerequisites

- Mark locked from Phase 3

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

## Outputs

- `[brand]-wordmark-final.svg` — Primary horizontal
- `[brand]-wordmark-short.svg` — Compact variant
- `[brand]-wordmark-stacked.svg` — If needed

## Gate

User confirms alignment and variants.

---

## Pitfalls

- **Mathematical vs optical** — Centered by numbers often looks wrong
- **Too tight** — Need breathing room
- **Mismatched weight** — Mark should feel balanced with text
- **Wrong font weight** — Too bold = clunky, too light = weak
- **Single context** — Test at different sizes and backgrounds
