# Tools Required

**Check these before starting the brand process. Install what's missing.**

---

## Quick Check

Run this to verify your setup:

```bash
# Required
rsvg-convert --version 2>/dev/null && echo "rsvg-convert: OK" || echo "rsvg-convert: MISSING"

# Recommended
vtracer --version 2>/dev/null && echo "vtracer: OK" || echo "vtracer: MISSING"
svgo --version 2>/dev/null && echo "svgo: OK" || echo "svgo: MISSING"
```

---

## Required

### rsvg-convert (SVG → PNG rendering)

**Used in:** Phases 3, 4 (render-verify loop, favicon export)

Renders SVGs to PNG at specific sizes. Essential for verifying marks at favicon sizes and presenting visual work to the user.

```bash
# macOS
brew install librsvg

# Ubuntu/Debian
sudo apt-get install librsvg2-bin

# Verify
rsvg-convert --version
```

**Usage:**
```bash
# Render at review size
rsvg-convert -w 512 -h 512 mark.svg -o mark-preview.png

# Render at favicon size
rsvg-convert -w 32 -h 32 mark.svg -o mark-32px.png
```

---

## Recommended

### vtracer (PNG → SVG tracing)

**Used in:** Phase 3 (primary mark development path)

Traces bitmap images to clean SVG paths. The primary tool for converting AI-generated reference images or sketches into production SVG marks.

```bash
# Requires Rust toolchain
cargo install vtracer

# Verify
vtracer --version
```

**Usage:**
```bash
# Basic trace
vtracer --input reference.png --output mark-draft.svg

# With options for cleaner output
vtracer --input reference.png --output mark-draft.svg \
  --colormode binary \
  --filter_speckle 4 \
  --corner_threshold 60 \
  --segment_length 4
```

**If cargo is not installed:**
```bash
# Install Rust toolchain
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source ~/.cargo/env
```

### svgo (SVG optimization)

**Used in:** Phases 3, 4 (cleaning up traced SVGs, reducing file size)

Optimizes SVG files by removing unnecessary metadata, simplifying paths, and reducing file size. Particularly important for traced SVGs which can be bloated.

```bash
npm install -g svgo

# Verify
svgo --version
```

**Usage:**
```bash
# Optimize an SVG
svgo mark-draft.svg -o mark-optimized.svg

# Preview what would change
svgo mark-draft.svg --pretty --indent=2 -o mark-clean.svg
```

---

## Fallback: Manual Conversion

### freeconvert.com (PNG → SVG, browser-based)

**Used when:** vtracer is unavailable, or tracing results need a different approach.

1. Go to https://www.freeconvert.com/png-to-svg
2. Upload the reference PNG
3. Download the resulting SVG
4. Continue with the refinement steps in Phase 3

This is a manual step — use it as a backup when automated tracing isn't working or isn't installed.

---

## Optional

### ImageMagick (image manipulation)

Useful for batch resizing, format conversion, and compositing.

```bash
brew install imagemagick

# Verify
magick --version
```

### Bun (for art skill image generation)

Required only if using the art skill for Phase 2 reference image generation.

```bash
curl -fsSL https://bun.sh/install | bash

# Verify
bun --version
```

---

## What Happens Without These Tools

| Tool Missing | Impact | Workaround |
|-------------|--------|------------|
| rsvg-convert | Can't render SVGs for review | Open SVGs in browser, screenshot manually |
| vtracer | Can't trace PNGs to SVG | Use freeconvert.com or hand-code simple geometry |
| svgo | Traced SVGs may be large/bloated | Manual cleanup or accept larger files |
