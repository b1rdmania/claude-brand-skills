# Phase 7: Packaging

Collect everything into a self-contained kit for handoff.

## Time

15-25 minutes (expanded to include raster exports, social assets, and mark variations).

## Prerequisites

- All phases complete
- All assets finalized

---

## Process

### 1. Create Folder

```bash
mkdir ~/Downloads/[brand]-brand-kit
```

### 2. Generate Mark Variations

Before collecting assets, create color variations of the mark for different contexts:

```bash
# White version (for dark backgrounds — replace fill colors with #FFFFFF)
# Edit the SVG to make all paths white, save as:
# [brand]-mark-white.svg

# Dark version (for light backgrounds — replace fill colors with brand's near-black)
# [brand]-mark-dark.svg

# Monochrome version (single neutral color)
# [brand]-mark-mono.svg
```

For traced/complex marks, the simplest approach is to duplicate the SVG and modify fill/stroke colors. For simple geometric marks, adjust the color values directly.

### 3. Export Raster Assets

Generate PNG exports at standard sizes from the SVG source:

```bash
# Mark at multiple sizes
rsvg-convert -w 512 -h 512 [brand]-mark-final.svg -o [brand]-mark-512.png
rsvg-convert -w 256 -h 256 [brand]-mark-final.svg -o [brand]-mark-256.png
rsvg-convert -w 64 -h 64 [brand]-mark-final.svg -o [brand]-mark-64.png

# Favicons
rsvg-convert -w 32 -h 32 [brand]-mark-final.svg -o favicon-32.png
rsvg-convert -w 16 -h 16 [brand]-mark-final.svg -o favicon-16.png
rsvg-convert -w 48 -h 48 [brand]-mark-final.svg -o favicon-48.png

# Apple Touch Icon (180x180 — mark centered on brand background)
# May need to create an SVG with the mark on a colored square background first
rsvg-convert -w 180 -h 180 [brand]-apple-touch-icon.svg -o apple-touch-icon.png

# Android Chrome (192 and 512)
rsvg-convert -w 192 -h 192 [brand]-mark-final.svg -o android-chrome-192.png
rsvg-convert -w 512 -h 512 [brand]-mark-final.svg -o android-chrome-512.png
```

**Without rsvg-convert:** Use `qlmanage -t -s [SIZE] -o . file.svg` on macOS, or open the SVG in a browser and export screenshots at specific sizes.

**Note on icon context:** The mark may need adaptation for icon shapes. Consider:
- Square favicons: Does the mark need padding within a square?
- Circle-masked iOS icons: Does the mark work inside a circle (rounded-rect)?
- Background color: Transparent, brand color, or white? Choose based on the contexts where the icon appears.

### 4. Generate Social Media Assets

Create simple compositions for social sharing:

**OG Image (1200x630):**
Create an SVG with the mark + wordmark centered on the brand background color. Keep it simple — the OG image is a thumbnail, not a poster.

```svg
<svg viewBox="0 0 1200 630" xmlns="http://www.w3.org/2000/svg">
  <rect width="1200" height="630" fill="{BG_DEEP}"/>
  <!-- Center the mark -->
  <g transform="translate(500, 215)">
    <!-- Mark SVG content at ~200px size -->
  </g>
  <!-- Wordmark below or beside -->
  <text x="600" y="480" text-anchor="middle"
    font-family="[Chosen Font]" font-size="32" font-weight="500"
    fill="{TEXT_PRIMARY}">brandname</text>
</svg>
```

```bash
rsvg-convert -w 1200 -h 630 [brand]-og-image.svg -o og-image.png
```

**Profile Avatar (400x400):**
Mark centered on brand background, square format.

```bash
rsvg-convert -w 400 -h 400 [brand]-avatar.svg -o avatar.png
```

### 5. Collect Assets

```bash
cd ~/Downloads

# Mark (SVG + variations)
cp [brand]-mark-final.svg [brand]-brand-kit/
cp [brand]-mark-white.svg [brand]-brand-kit/
cp [brand]-mark-dark.svg [brand]-brand-kit/

# Mark (PNG exports)
cp [brand]-mark-512.png [brand]-brand-kit/
cp [brand]-mark-256.png [brand]-brand-kit/

# Favicons
cp favicon-16.png [brand]-brand-kit/
cp favicon-32.png [brand]-brand-kit/
cp favicon-48.png [brand]-brand-kit/
cp apple-touch-icon.png [brand]-brand-kit/

# Social
cp og-image.png [brand]-brand-kit/
cp avatar.png [brand]-brand-kit/

# Wordmarks
cp [brand]-wordmark-final.svg [brand]-brand-kit/
cp [brand]-wordmark-short.svg [brand]-brand-kit/

# Docs
cp DESIGN.md [brand]-brand-kit/
cp [brand]-emotive-narrative.md [brand]-brand-kit/
cp [brand]-design-guidelines.md [brand]-brand-kit/
cp [brand]-philosophy.md [brand]-brand-kit/
cp [brand]-visual-philosophy.md [brand]-brand-kit/
```

### 6. Write README

Use `Templates/readme-template.md` as a starting structure. Quick-start doc for anyone picking up the kit:

```markdown
# [Brand] Brand Kit

## Quick Start

**Concept:** [One sentence on the brand essence]

**Colors:**
- Background: `#hex`
- Surface: `#hex`
- Text: `#hex`
- Accent: `#hex`

**Fonts:**
- UI: [Font] (500 headings, 400 body)
- Code: [Font]

---

## Files

### Logo
- `[brand]-mark-final.svg` — Mark
- `[brand]-favicon.png` — Favicon

### Wordmarks
- `[brand]-wordmark-final.svg` — Full lockup
- `[brand]-wordmark-short.svg` — Compact

### Docs
- `[brand]-design-guidelines.md` — Complete system
- `[brand]-philosophy.md` — Brand narrative

---

## Principles

1. **[Principle]** — [Brief]
2. **[Principle]** — [Brief]
3. **[Principle]** — [Brief]

---

## CSS

\`\`\`css
:root {
  --bg-deep: #hex;
  --text-primary: #hex;
  --accent: #hex;
  /* ... */
}
\`\`\`

---

*[Tagline]*
```

### 7. Verify Contents

```bash
ls -la [brand]-brand-kit/
```

Expected:
```
[brand]-brand-kit/
├── README.md
├── DESIGN.md
├── [brand]-mark-final.svg
├── [brand]-mark-white.svg
├── [brand]-mark-dark.svg
├── [brand]-mark-512.png
├── [brand]-mark-256.png
├── favicon-16.png
├── favicon-32.png
├── favicon-48.png
├── apple-touch-icon.png
├── og-image.png
├── avatar.png
├── [brand]-wordmark-final.svg
├── [brand]-wordmark-short.svg
├── [brand]-emotive-narrative.md
├── [brand]-design-guidelines.md
├── [brand]-philosophy.md
└── [brand]-visual-philosophy.md
```

### 8. Zip

```bash
zip -r [brand]-brand-kit.zip [brand]-brand-kit/
```

### 9. Deliver

> "Done. `~/Downloads/[brand]-brand-kit.zip` has everything:
> - Mark + favicon
> - Wordmark variants
> - Full design system
> - Brand philosophy
> - Quick-start README
>
> Ready for handoff."

---

## Checklist

**Required:**
- [ ] README.md
- [ ] DESIGN.md (master reference — Phase 6 output)
- [ ] Mark SVG (full color)
- [ ] Mark SVG (white version)
- [ ] Mark SVG (dark version)
- [ ] Mark PNG (512px)
- [ ] Mark PNG (256px)
- [ ] Favicon PNGs (16px, 32px, 48px)
- [ ] Apple Touch Icon (180px)
- [ ] Primary wordmark SVG
- [ ] Emotive narrative MD (Phase 0 output)
- [ ] Design guidelines MD

**Recommended:**
- [ ] Short wordmark SVG
- [ ] OG image (1200x630 PNG)
- [ ] Profile avatar (400x400 PNG)
- [ ] Android Chrome icons (192px, 512px)
- [ ] Philosophy docs
- [ ] Visual philosophy docs
- [ ] Compositional identity docs (Phase 5.5 output)

---

## Handoff Standard

The package should be usable without further questions. Someone should be able to:
1. Unzip
2. Read README
3. Implement

If they need to ask questions, documentation is incomplete.

---

## Gate Check

1. Verify all files are present (run the checklist above)
2. Present the kit contents to the user
3. Ask: **"Phase 7 Gate Check — Brand kit packaged with all assets. Process complete?"**
4. On approval: update `.brand-progress.md` → Phase 7: COMPLETE

---

## Outputs

- `~/Downloads/[brand]-brand-kit/`
- `~/Downloads/[brand]-brand-kit.zip`
