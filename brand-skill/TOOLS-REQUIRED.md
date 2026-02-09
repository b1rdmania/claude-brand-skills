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

## Image Generation (Phase 2 — Optional but recommended)

Phase 2 (Visual Direction) can use AI image generation to explore aesthetic territory before committing to SVG work. This uses the **Art skill's** `Generate.ts` tool, which supports multiple models.

**API keys required** (set as environment variables):

| Model | Env Variable | Provider | Best for |
|-------|-------------|----------|----------|
| `nano-banana-pro` | `GOOGLE_API_KEY` | Google/Gemini | Best quality, text rendering, reference images |
| `nano-banana` | `REPLICATE_API_TOKEN` | Replicate | Faster iteration, slightly lower quality |
| `flux` | `REPLICATE_API_TOKEN` | Replicate (Black Forest Labs) | Alternative high-quality generation |
| `gpt-image-1` | `OPENAI_API_KEY` | OpenAI | Alternative generation |

**Without API keys:** Phase 2 still works — the user can provide their own reference images or mood boards, or you can skip directly to Phase 3 with more initial SVG variations (8-10 instead of 4-5).

**The Art skill is not required for the brand skill to function.** It enhances Phase 2 but every other phase works without it.

## Optional MCP Servers

If available, these enhance the workflow:
- **SVGMaker MCP** — Real-time SVG rendering in-context
- **SVG Converter MCP** — Format conversion without external tools
- **Image generation MCP** — Alternative to Art skill for Phase 2 reference generation
