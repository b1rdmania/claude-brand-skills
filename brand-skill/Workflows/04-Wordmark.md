# Phase 4: Wordmark & Lockups

Pair the mark with typography to create complete logo lockups.

## Time

10-20 minutes.

## Prerequisites

- Mark locked from Phase 3

---

## ⚠️ SVG Typography Rules (CRITICAL)

**Letter-spacing in SVG:**
- ✅ **ALWAYS use pixel values** (e.g., `letter-spacing="-0.4"`)
- ❌ **NEVER use em units** (e.g., `letter-spacing="-0.4em"`)
- SVG interprets letter-spacing differently than CSS
- Em units will cause text to overlap and become illegible

**Before presenting variants:**
- Test SVG rendering in browser or with `rsvg-convert`
- Verify text is readable and spacing is correct
- Catch errors before user sees them

**Decorative elements:**
- ⚠️ **Don't position decorative elements ON font glyphs** (e.g., coloring the dot of "i")
- Font rendering is dynamic - you can't accurately position elements on specific glyph features in SVG
- Use end-of-line accents, underlines, or separate decorative marks instead
- Example: purple dot at END of word ✅, purple dot on "i" tittle ❌

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

### 2. Typographic Refinement

With the font and weight chosen, explore spacing and case treatment before creating lockups.

#### 2a. Tracking (Letter-Spacing)

Render the brand name at 3 tracking values in the chosen font:

```html
<div style="font-family: '[Chosen Font]'; font-size: 28px; font-weight: [weight]; letter-spacing: -0.02em;">
  brandname  <!-- Tight -->
</div>
<div style="font-family: '[Chosen Font]'; font-size: 28px; font-weight: [weight]; letter-spacing: 0em;">
  brandname  <!-- Normal -->
</div>
<div style="font-family: '[Chosen Font]'; font-size: 28px; font-weight: [weight]; letter-spacing: 0.04em;">
  brandname  <!-- Loose -->
</div>
```

Tight tracking feels technical and dense. Loose tracking feels editorial and premium. Normal is safe — and safe often means convergent. Present all three and let the user choose.

#### 2b. Case Treatment

Show the brand name in 3 case treatments:

- **lowercase:** `autonomolabs` — relaxed, approachable, modern
- **Title Case:** `AutonoLabs` — proper, established, formal
- **UPPERCASE:** `AUTONOMOLABS` — authoritative, loud, institutional

Present with brief rationale for each. The user selects. Do not default to whatever the company already uses without showing alternatives — they may never have considered it.

#### 2c. User Confirms

Present spacing + case options and ask: "Which tracking and case treatment feels right?" Only then proceed to lockup creation.

### 3. Create Lockup Spacing/Sizing Variants

**Before creating final variants, show 3-4 spacing and sizing options:**

Create a comparison showing different gap and text size combinations. Example:
- Option A: 24px gap, 36px text (medium spacing, moderate size)
- Option B: 20px gap, 40px text (tighter gap, larger text)
- Option C: 16px gap, 40px text (tight spacing, larger text - "density")
- Option D: 32px gap, 36px text (loose spacing, moderate size)

Present visually and let user select which feels most balanced. This prevents having to redo sizing later.

### 4. Create Final Variants

Once spacing/sizing is locked, build 3-4 lockup options:

**Name only:**
Mark + "brandname"

**Full domain:**
Mark + "brandname.com" (possibly with colored TLD)

**Monospace variant:**
Mark + "brandname" in mono (if brand uses monospace)

**Accent element:**
Consider subtle accent elements (e.g., colored dot, underline, bracket) if they support the brand concept

### 5. Align

This takes iteration. Considerations:

**Vertical:**
- Mark center vs text baseline
- Mark center vs text x-height
- Optical center (often different from mathematical)

**Horizontal:**
- Gap between mark and text
- Too tight feels cramped, too loose feels disconnected
- **Gap ratio guidelines:**
  - Tight spacing (density aesthetic): 0.25x mark height (e.g., 16px gap for 64px mark)
  - Medium spacing (balanced): 0.5x mark height (e.g., 32px gap for 64px mark)
  - Loose spacing (breathing room): 0.75x mark height (e.g., 48px gap for 64px mark)

**Scale:**
- Mark should balance with text weight
- May need to scale mark from original size
- **Text size guideline:** 60-75% of mark height for optical balance
  - Example: 64px mark → 40-48px text
  - Smaller text makes mark dominate; larger text can overwhelm mark

**Iterate with small adjustments:**
```svg
<g transform="translate(4, 6)">  <!-- Try 4,8 or 6,6 -->
<text x="58" y="36">  <!-- Try x="60" y="38" -->
```

### 5. Build the System

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

These are **reference ranges**, not defaults. Use the font chosen in Step 1 above.

**Sans-serif (geometric/humanist):**
```
font-family: "[Chosen Font]", -apple-system, sans-serif
font-size: 22-28px
font-weight: 500
letter-spacing: -0.01em to -0.02em
```

**Monospace (if chosen):**
```
font-family: "[Chosen Mono Font]", monospace
font-size: 20-24px (monospace runs wider)
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

### 7. Size Testing

Render all lockup variants at three sizes:

| Context | Height | What to check |
|---------|--------|---------------|
| Hero | 200px+ | Does the weight and spacing look elegant at display size? |
| Navigation | 40px | Is the brand name fully legible? Is the mark still recognizable? |
| Compact | 24px | Can you still read it? If not, which variant works best at this size? |

```bash
# Render at different sizes using rsvg-convert
rsvg-convert -h 200 [brand]-wordmark-final.svg -o wordmark-hero.png
rsvg-convert -h 40 [brand]-wordmark-final.svg -o wordmark-nav.png
rsvg-convert -h 24 [brand]-wordmark-final.svg -o wordmark-compact.png
```

If any variant is illegible at nav or compact size:
- Try reducing letter-spacing
- Try a heavier weight
- Consider a simplified variant (text-only) for small contexts
- Note which variant to use at which size in the design guidelines

---

## Quality Checks

Before locking the wordmark:

- [ ] Font personality matches mark personality (not just "clean" — distinctive)
- [ ] Typographic weight balances with mark's visual weight
- [ ] Reads clearly at navigation size (40px height)
- [ ] Reads clearly at hero size (200px+ height)
- [ ] Letter-spacing feels intentional (not the font's default tracking)
- [ ] Mark + text gap is optically comfortable (not mathematically centered)
- [ ] Lockup works on both dark and light backgrounds
- [ ] User has seen and approved font choice (from Step 1 specimens)
- [ ] User has seen and approved tracking + case treatment (from Step 2)
- [ ] All variants render correctly as SVG

---

## Outputs

- `[brand]-wordmark-final.svg` — Primary horizontal
- `[brand]-wordmark-short.svg` — Compact variant
- `[brand]-wordmark-stacked.svg` — If needed

## Gate Check

1. Present all wordmark variants at hero, nav, and compact sizes
2. Walk through the quality checklist above with the user
3. Ask: **"Phase 4 Gate Check — Font chosen, lockups aligned, size-tested. Approved to proceed to Phase 5: Design System?"**
4. On approval: update `.brand-progress.md` → Phase 4: COMPLETE
5. Only proceed to Phase 5 when user explicitly approves

---

## Pitfalls

- **Mathematical vs optical** — Centered by numbers often looks wrong
- **Too tight** — Need breathing room
- **Mismatched weight** — Mark should feel balanced with text
- **Wrong font weight** — Too bold = clunky, too light = weak
- **Single context** — Test at different sizes and backgrounds
