# AutonoLabs Brand Skills Project

## What this is
Brand identity kit and landing page for AutonoLabs.ai — an agentic venture studio based in Melbourne. Built entirely with Claude Code using custom brand skills.

## Live deployment
- **URL**: autonomolabs.vercel.app (domain autonolabs.ai connected by Eli)
- **GitHub**: AutonoLabs/AutonoLabs (13 static HTML files on main branch)
- **Current index.html**: V5 Exhibition with Specimen treatment — full thesis, 8 scroll-snap rooms, type specimen quirks (baseline grids, dimension lines, callout annotations, margin notes, crosshatch grids, registration marks, PROOF watermark, color bar)

## Brand tokens
- **Colors**: #1A1916 (bg), #D4D2CA (text), #4A7C59 (green), #C49A3C (amber), #B84040 (red)
- **Typography**: Avenir Next (200-500 weights) + JetBrains Mono
- **Mark**: AL monogram in `brand-output/ref6-var2-shared-stroke-optimized-transparent.svg`

## Project structure
- `brand-skill/` — The skill itself (SKILL.md, Workflows 00-07, Templates, Examples, SKILL-AUDIT.md, ADDENDUM-4-WEB-PRESENCE.md)
- `brand-output/` — All generated assets (SVGs, HTML pages, markdown docs, font specimens)
- `brand-output/deploy/` — Production files deployed to Vercel (self-contained HTML with base64-inlined SVGs)
- `brand-output/deploy/compare.html` — Index of all design variants

## Design variants (in deploy/)
- **V0 (v0-studio-v3.html)** — Control Room / Bloomberg terminal style
- **V1 (v1-broadsheet.html)** — Newspaper editorial layout (too dense)
- **V2 (v2-terminal.html)** — Terminal/BBS aesthetic (too dense)
- **V3 (v3-exhibition.html)** — Museum exhibition layout (best structure)
- **V3A (v3a-colour-rupture.html)** — Exhibition + strategic colour moments
- **V3B (v3b-misprint.html)** — Exhibition + misregistered/ghost type
- **V3C (v3c-specimen.html)** — Exhibition + type foundry annotations (most distinctive)
- **V4 (v4-dossier.html)** — Studio dossier variant
- **V4 (v4-exhibition.html)** — Exhibition refined (heavier weights, colour moments)
- **V5 (v5-exhibition.html)** — Full thesis + Specimen treatment (CURRENT LIVE PAGE)
- **V5 (v5-control-room.html)** — Full thesis in Bloomberg terminal style

## Key lessons learned
- LLMs cannot hand-code SVG to match visual references — use bitmap tracing tools (vtracer, potrace) instead
- SVGO via `npx svgo@latest` for SVG optimization
- `qlmanage -t -s 512 -o /output/dir file.svg` renders SVGs to PNG on macOS
- Deploy files must be self-contained (base64 data URIs) since Vercel only serves the deploy directory
- See `brand-skill/ADDENDUM-4-WEB-PRESENCE.md` for the philosophical framework on why LLMs converge to statistical mean in design — the key insight is that prescribing techniques just moves the convergence point; only process structure (evolutionary diverge/compare/kill/mutate) can escape it

## Completed work (7 phases)
1. Emotive narrative
2. Discovery & visual direction
3. Mark development (AL monogram)
4. Wordmark (autonomolabs.ai with green .ai)
5. Design system (typography scale, colour palette)
6. Design guidelines markdown
7. Packaging (zip to ~/Downloads)

Plus: skill audit, 4 addenda, 11 page variants, full thesis copy, GitHub deployment

## Team
- Andy — founder
- Eli (@b1rdmania on GitHub) — connecting domain + Vercel
