---
name: Art
description: AI image generation tool. Use when you need to generate reference images, illustrations, or visual content from text prompts.
---

# Art Skill — Image Generation

A CLI tool for generating images from text prompts using multiple AI models. Used by the brand-skill in Phase 2 (Visual Direction) and Phase 3 (Mark Development) for reference image generation.

## The Tool

`Tools/Generate.ts` — A multi-model image generation CLI that supports:

| Model | Flag | API Key | Best for |
|-------|------|---------|----------|
| Gemini (nano-banana-pro) | `--model nano-banana-pro` | `GOOGLE_API_KEY` | Best quality, text rendering |
| Replicate (nano-banana) | `--model nano-banana` | `REPLICATE_API_TOKEN` | Faster iteration |
| Flux | `--model flux` | `REPLICATE_API_TOKEN` | High quality, stylistic variety |
| GPT Image | `--model gpt-image-1` | `OPENAI_API_KEY` | Alternative generation |

## Setup

1. Install bun runtime: `curl -fsSL https://bun.sh/install | bash`
2. Set at least one API key as an environment variable
3. Run with: `bun run Tools/Generate.ts --model [MODEL] --prompt "[PROMPT]" --output ~/Downloads/output.png`

## Usage

```bash
# Basic generation
bun run Tools/Generate.ts \
  --model nano-banana-pro \
  --prompt "Abstract minimalist logo concept: [description]. Clean vector style, dark background. No text." \
  --size 2K \
  --aspect-ratio 1:1 \
  --output ~/Downloads/brand-ref-1.png

# With background removal (useful for marks)
bun run Tools/Generate.ts \
  --model nano-banana-pro \
  --prompt "[PROMPT]" \
  --size 2K \
  --remove-bg \
  --output ~/Downloads/mark-reference.png

# With reference image for style consistency
bun run Tools/Generate.ts \
  --model nano-banana-pro \
  --prompt "[PROMPT]" \
  --reference-image existing-mark.png \
  --size 2K \
  --output ~/Downloads/variation.png
```

## Flags

| Flag | Options | Default | Purpose |
|------|---------|---------|---------|
| `--model` | nano-banana-pro, nano-banana, flux, gpt-image-1 | nano-banana-pro | Image generation model |
| `--prompt` | text | (required) | The generation prompt |
| `--size` | 1K, 2K, 4K | 2K | Output resolution |
| `--aspect-ratio` | 1:1, 16:9, 9:16, 21:9 | 1:1 | Image dimensions |
| `--output` | path | ~/Downloads/output.png | Output file path |
| `--remove-bg` | (flag) | off | Remove background after generation |
| `--thumbnail` | (flag) | off | Generate both transparent + background versions |
| `--reference-image` | path (repeatable) | none | Style/content reference images |
| `--creative-variations` | number | 1 | Generate multiple variations |

## In the Brand Process

**Phase 2 — Visual Direction (Mode A):**
Generate 3-4 reference images exploring different visual interpretations of the brand concept. Square aspect ratio, high resolution, abstract/minimalist prompts.

**Phase 3 — Mark Development (Path A):**
Generate high-contrast reference images for bitmap tracing with vtracer. Use `--remove-bg` for clean marks. Trace the result to SVG.

## Tips

- Always output to `~/Downloads/` first for preview
- Square (1:1) aspect ratio works best for logo references
- Include "no text" in prompts for logo/mark references
- Use `--remove-bg` when generating marks for tracing
- Keep prompts abstract: "minimalist logo concept" not "a logo for my company"
- `nano-banana-pro` handles text rendering best if you need labels
