# Phase 4: Wordmark & Lockups

Pair the mark with typography to create complete logo lockups.

## Time

10-20 minutes.

## Prerequisites

- Mark locked from Phase 3

---

## Process

### 1. Font Exploration (MANDATORY)

**Do not skip this step.** The user should choose their font before seeing a wordmark. Presenting a wordmark in a font they never selected is a decision made for them, not with them.

#### 1a. Select Candidates

Based on the brand personality (Phase 0-1), select 3-5 candidate fonts. Go beyond the safe defaults — use the emotive narrative and visual philosophy to guide choices.

| Personality | Font Direction | Examples beyond defaults |
|-------------|----------------|--------------------------|
| Technical/Dev | Monospace | JetBrains Mono, Berkeley Mono, IBM Plex Mono |
| Modern/Neutral | Geometric sans | Geist, Satoshi, General Sans |
| Enterprise | Neutral sans | Neue Haas Grotesk, Aktiv Grotesk |
| Friendly | Humanist sans | Work Sans, Source Sans, DM Sans |
| Premium | Light weight sans or serif | Avenir Next, Canela, GT Sectra |
| Brutalist | Heavy/Display | Clash Display, Cabinet Grotesk, Space Grotesk |
| Editorial | Serif or slab | Playfair Display, Lora, Roboto Slab |

**Do not default to Inter or JetBrains Mono unless the brand personality specifically calls for them.** These are the LLM convergence choices — the statistical center of "safe developer font."

#### 1b. Render Font Specimens

For each candidate font, render the brand name in SVG or HTML at wordmark size:

```html
<!-- Quick specimen rendering -->
<div style="font-family: 'Avenir Next'; font-size: 28px; font-weight: 300; letter-spacing: -0.01em;">
  brandname
</div>
<div style="font-family: 'Avenir Next'; font-size: 28px; font-weight: 500; letter-spacing: -0.01em;">
  brandname
</div>
<div style="font-family: 'Avenir Next'; font-size: 28px; font-weight: 600; letter-spacing: -0.01em;">
  brandname
</div>
```

Show 2-3 weights per font. Present side by side with brief rationale for each option.

#### 1c. User Selects

Present the specimens and ask: "Which font and weight feels right for this brand?" User picks one direction. Only then proceed to wordmark creation.

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
    fill="{TEXT_PRIMARY}"
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
<tspan fill="{BRAND_ACCENT}">.tld</tspan>
```
Ties to mark's accent. Use the brand's primary accent color from Phase 5.

**Muted:**
```svg
<tspan fill="{TEXT_MUTED}">.tld</tspan>
```
De-emphasizes extension. Use the brand's muted text color from Phase 5.

**Same as name:**
Treats it as unified word.

---

## Outputs

- `[brand]-wordmark-final.svg` — Primary horizontal
- `[brand]-wordmark-short.svg` — Compact variant
- `[brand]-wordmark-stacked.svg` — If needed

## Gate Check

1. Present all wordmark variants to the user
2. Ask: **"Phase 4 Gate Check — Font chosen, lockups aligned. Approved to proceed to Phase 5: Design System?"**
3. On approval: update `.brand-progress.md` → Phase 4: COMPLETE
4. Only proceed to Phase 5 when user explicitly approves

---

## Pitfalls

- **Mathematical vs optical** — Centered by numbers often looks wrong
- **Too tight** — Need breathing room
- **Mismatched weight** — Mark should feel balanced with text
- **Wrong font weight** — Too bold = clunky, too light = weak
- **Single context** — Test at different sizes and backgrounds
