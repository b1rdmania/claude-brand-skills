# Tools Required for Brand Skill

## Required

| Tool | Purpose | Install |
|------|---------|---------|
| Node.js | SVGO optimization | `brew install node` or [nodejs.org](https://nodejs.org) |
| SVGO | SVG optimization | `npx svgo@latest` (no install needed) |
| Browser | SVG/HTML preview | Already installed |

## Recommended

| Tool | Purpose | Install |
|------|---------|---------|
| vtracer | PNG-to-SVG bitmap tracing (Phase 3) | `brew install vtracer` |
| potrace | Bitmap tracing (simpler alternative) | `brew install potrace` |
| librsvg | SVG-to-PNG conversion (favicons) | `brew install librsvg` → `rsvg-convert` |

## Platform-Specific

### macOS
- **Quick Look rendering**: `qlmanage -t -s 512 -o /output/dir file.svg` — renders SVGs to PNG for visual verification. Built into macOS.

### Linux
- **librsvg**: `sudo apt-get install librsvg2-bin` → `rsvg-convert`
- **potrace**: `sudo apt-get install potrace`

## Verification

Run these to check your setup:

```bash
# Required
node --version
npx svgo --version

# Recommended
vtracer --version
rsvg-convert --version

# macOS specific
qlmanage -h 2>&1 | head -1
```

## Fonts

The skill does not prescribe default fonts — font selection happens in Phase 4 based on brand personality. However, for rendering font specimens, the system should have access to web fonts via:

- **Google Fonts**: Load via `<link>` in HTML specimens
- **Local install**: For offline work, install chosen fonts via system package manager or font manager

Common fonts used in examples:
- Inter — `https://fonts.google.com/specimen/Inter`
- JetBrains Mono — `https://fonts.google.com/specimen/JetBrains+Mono`
- Avenir Next — System font on macOS
- SF Pro — System font on macOS/iOS

## Image Generation (Phase 2 — Optional)

Phase 2 (Visual Direction) can use AI image generation to explore aesthetic territory before committing to SVG work. Use any text-to-image tool you have access to:

| Tool | How to access |
|------|--------------|
| Gemini | [Google AI Studio](https://aistudio.google.com/) (free tier available) |
| DALL-E | ChatGPT Plus or [OpenAI API](https://platform.openai.com/) |
| Midjourney | [midjourney.com](https://midjourney.com/) |
| Flux / Stable Diffusion | [Replicate](https://replicate.com/) or local install |

**Without image generation:** Phase 2 still works — provide your own reference images or mood boards (Mode B), or skip directly to Phase 3 with more initial SVG variations (Mode C).

**Image generation is not required.** It enhances Phase 2 but every other phase works without it.
