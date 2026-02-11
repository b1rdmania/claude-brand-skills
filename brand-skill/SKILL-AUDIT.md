# Brand Skill Audit

**Date:** 2026-02-06
**Context:** Full execution of the brand skill for AutonoLabs.ai (Phases 0-7)
**Executor:** Claude Sonnet 4.5 via Claude Code CLI

---

## Implementation Status

**Last updated:** 2026-02-11

All critical and high-severity issues have been resolved. All P0 and P1 gaps have been implemented. Two P2 and one P3 item remain as future work.

| # | Issue | Severity | Status |
|---|-------|----------|--------|
| 1 | Phase 3 SVG hand-coding | Critical | ✅ Implemented |
| 2 | No orchestrator | Critical | ✅ Implemented |
| 3 | No visual validation loop | Critical | ✅ Implemented |
| 4 | Template colors from Sorted | High | ✅ Implemented |
| 5 | Phase 4 lockups with traced SVGs | High | ⚠️ Partial |
| 6 | No iteration limits | High | ✅ Implemented |
| 7 | Gate checks vague | Medium | ✅ Implemented |
| 8 | No tooling requirements | Medium | ✅ Implemented |
| 9 | Anti-slop checklists aspirational | Medium | ⚠️ Partial |
| 10 | Phase 0-2 vs 3+ quality gap | Medium | ✅ Implemented |
| 2.1 | Font exploration | P0 | ✅ Implemented |
| 2.2 | Color derivation process | P0 | ✅ Implemented |
| 2.3 | Real-world mockups | P2 | ❌ Not implemented |
| 2.4 | Favicon/icon export pipeline | P1 | ✅ Implemented |
| 2.5 | Social media assets | P2 | ✅ Implemented |
| 2.6 | Brand guidelines PDF | P3 | ❌ Not implemented |
| 2.7 | Light mode derivation | P0 | ✅ Implemented |
| 2.8 | Accessibility validation | P1 | ✅ Implemented |
| 2.9 | File format variety | P2 | ✅ Implemented |
| A3 | Convergence / composition | Critical | ✅ Implemented |
| §5 | Phase 4 rewrite | P0 | ✅ Implemented |

---

## Executive Summary

The brand skill's text-based phases (0-2: Emotive Narrative, Philosophy, Visual Direction) are strong and play to LLM strengths. Quality drops sharply when the skill hits visual output in Phase 3+. The core issue is an assumption that LLMs can iteratively design SVG visuals by code alone — they can't see their output, leading to long iteration loops with diminishing returns.

Phase 3 consumed 30 SVG iterations without converging on the reference. The user resolved it pragmatically by using an external PNG-to-SVG converter. This is the correct approach, and the skill should formalize it.

---

## Issues by Severity

### Critical

#### 1. Phase 3 SVG Mark Creation Is Fundamentally Flawed for LLMs ✅ IMPLEMENTED

**Problem:** The skill assumes the executor can hand-code SVG paths to match a visual reference image. LLMs cannot see rendered output. Each iteration is a blind guess informed only by coordinate math and the previous code. After 30 iterations, the result still didn't match the reference.

**What happened:** The executor got stuck in an iteration loop — adjusting counter sizes, crossbar positions, and path geometry without being able to verify the visual result. The user correctly identified this: *"You got in a loop; that wasn't great."* The user ultimately solved it themselves with an online PNG-to-SVG converter.

**Fix:**
- Make bitmap tracing the **primary** path for Phase 3, not hand-coding
- Add required tooling: `vtracer` (Homebrew), `potrace` (Homebrew), or an MCP server for SVG conversion
- Hand-coded SVG should be reserved for simple geometric marks only (circles, squares, basic monograms)
- Add explicit guidance: "If the mark involves letterforms, illustrative elements, or complex geometry, use bitmap tracing"

#### 2. No Master Orchestrator / Phase Progression Tracker ✅ IMPLEMENTED

**Problem:** Each phase is a separate markdown file with no mechanism to track which phases are complete, enforce sequential execution, or prevent skipping. The executor jumped from Phase 3 to Phase 5, skipping the lockup portion of Phase 4.

**What happened:** After creating text-only wordmarks (part of Phase 4), the executor read the Phase 5 workflow and began building the design system. The mark+text lockups were never created. The user caught this: *"Hang on, did you skip a phase?"*

**Fix:**
- Add `00-Orchestrator.md` with a checklist the executor must update after each phase
- Each phase should have explicit entry criteria: "Confirm Phase N-1 outputs exist and are approved"
- Include a progress tracker format:
  ```
  - [x] Phase 0: Emotive Narrative → autonomolabs-emotive-narrative.md
  - [x] Phase 1: Philosophy → autonomolabs-philosophy.md
  - [ ] Phase 2: Visual Direction → ...
  ```

#### 3. No Visual Validation Loop ✅ IMPLEMENTED

**Problem:** The skill never specifies how to verify visual output. There's no "render and check" step. The executor had to discover `qlmanage -t -s 512` on macOS as an ad-hoc workaround.

**Fix:**
- Add a `TOOLS-REQUIRED.md` file listing prerequisites
- Include platform-specific render commands:
  - macOS: `qlmanage -t -s 512 -o /tmp file.svg`
  - Or: browser-based preview via `open file.svg`
- Add after every SVG creation step: "Render to PNG, present to user for visual confirmation"

---

### High

#### 4. Template Colors Are From a Different Brand ✅ IMPLEMENTED

**Problem:** The Phase 5 (Design System) workflow contains hardcoded CSS/Swift values using a cool purple palette (`#0e0e10`, `#e4e1e8`, `#22c55e`). These are not placeholders — they look like final values. The executor must manually identify which are template values and replace them, which is error-prone.

**What happened:** Every color in the Phase 5 template had to be mapped to AutonoLabs' warm palette (`#1A1916`, `#D4D2CA`, `#4A7C59`). Some template values (like `#22c55e` for green) are significantly different from the brand green (`#4A7C59`). Without careful attention, template colors could leak into the final output.

**Fix:**
- Replace all hardcoded hex values in templates with semantic placeholders:
  ```css
  --bg-deep: {BG_PRIMARY};    /* Main background */
  --green:   {BRAND_ACCENT};  /* From mark accent color */
  ```
- Or add a clear header: "ALL COLOR VALUES BELOW ARE EXAMPLES. Replace with values derived from the mark and visual philosophy."

#### 5. Phase 4 Lockups Are Impractical With Traced SVGs ⚠️ PARTIAL

**Problem:** The Phase 4 workflow assumes the mark is a clean, hand-coded SVG that can be embedded into a lockup via `<g transform="translate(...)">`. The actual mark is a 158KB traced file with dozens of complex paths. Embedding it into a lockup creates unwieldy files.

**Fix:**
- Add guidance for traced/complex marks: "If the mark SVG exceeds 10KB, reference it as a separate file rather than inlining"
- Consider lockups as composite assets (mark image + text SVG side by side) rather than single SVG files
- Add SVGO optimization as a required step before lockup creation

#### 6. No Iteration Limits or Escape Hatches ✅ IMPLEMENTED

**Problem:** Phase 3 has no guidance on when to stop iterating and change approach. The executor kept refining the same approach for 30 rounds because the skill's implicit message is "keep going until it matches."

**What happened:** The user had to intervene: *"I'm wary that we've done 30 of these, so it may just be too difficult a task."*

**Fix:**
- Add explicit iteration limits: "If the mark isn't converging after 5-8 iterations, consider:"
  1. Simplifying the design (fewer elements, simpler geometry)
  2. Switching to bitmap tracing
  3. Using an external design tool and importing
  4. Presenting current best to user for direction change
- Add a "pivot checklist" that triggers after N iterations without convergence

---

### Medium

#### 7. Gate Checks Are Vague ✅ IMPLEMENTED

**Problem:** Each phase ends with something like "User confirms alignment and variants" but doesn't specify the mechanism. Should the executor render a PNG? Describe it? List the files? The lack of specificity leads to gates being skipped or performed inconsistently.

**Fix:**
- Standardize gate format:
  ```
  ## Gate Check
  1. List all output files with descriptions
  2. Render SVG outputs to PNG at 512px
  3. Present renders to user
  4. Get explicit "approved" or feedback
  5. Do not proceed to Phase N+1 until approved
  ```

#### 8. No Tooling Requirements Document ✅ IMPLEMENTED

**Problem:** The skill assumes tools are available but never lists them. During execution, the following were needed and discovered ad-hoc:
- `qlmanage` (macOS SVG rendering)
- `npx svgo` (SVG optimization)
- `vtracer` / `potrace` (bitmap tracing — not installed, would have prevented the 30-iteration problem)
- Font availability (Inter, JetBrains Mono — SVG `<text>` elements depend on installed fonts)

**Fix:**
- Add `TOOLS-REQUIRED.md`:
  ```
  ## Required
  - Node.js (for npx svgo)
  - qlmanage or browser (SVG preview)

  ## Recommended
  - vtracer: `brew install vtracer` (PNG-to-SVG tracing)
  - potrace: `brew install potrace` (bitmap tracing)
  - svgo: `npx svgo@latest` (SVG optimization)

  ## Fonts
  - Inter (install via Google Fonts or system package)
  - JetBrains Mono (install via JetBrains or Homebrew Cask)

  ## Optional MCP Servers
  - SVGMaker MCP (real-time SVG rendering)
  - SVG Converter MCP (format conversion)
  ```

#### 9. Anti-AI-Slop Checklists Are Aspirational, Not Actionable ⚠️ PARTIAL

**Problem:** Checklist items like "Colors have meaning" and "Components feel distinctive" are good principles but subjective. There's no way to objectively verify them during execution. They serve as vibes, not gates.

**Fix:**
- Split into verifiable and aspirational:
  - Verifiable: "Every color in the system is used in at least one component" / "WCAG AA contrast ratios met for all text/background pairs"
  - Aspirational: Keep as design principles, but don't frame them as checkboxes

#### 10. Phase 0-2 vs 3+ Quality Gap ✅ IMPLEMENTED

**Problem:** Phases 0-2 (narrative, philosophy, visual direction) are text generation tasks — LLM strengths. Phase 3+ requires spatial reasoning, visual design, and iterative refinement of visual output — LLM weaknesses. The skill doesn't acknowledge this gap or adjust its approach.

**Fix:**
- Add a note at Phase 3: "From this point, the skill enters visual production. Expect to rely more heavily on external tools and user feedback. LLM-generated SVG is a starting point, not a final product."
- Consider splitting Phase 3 into:
  - 3a: Design brief (text — LLM strength)
  - 3b: SVG production (tooling-assisted — use tracing, optimization tools)
  - 3c: Refinement (user-driven iteration with renders)

---

## What Worked Well

1. **Phases 0-2 produced strong output.** The emotive narrative, philosophy, and visual philosophy documents were high quality and set clear creative direction without feeling generic.

2. **The anti-AI-slop principle is valuable.** Even if the checklists are hard to verify, the overall framing ("if it could be any generic SaaS brand, we failed") kept the output distinctive.

3. **Phase 5 template structure is comprehensive.** Web + iOS, CSS variables + Swift tokens, components + layout + motion. The structure is right even if the template values need swapping.

4. **The phased approach itself is sound.** Moving from narrative → philosophy → visual direction → mark → wordmark → system → documentation → packaging is a logical creative funnel. The issue is execution tooling, not the architecture.

5. **Font recommendations were solid.** Inter + JetBrains Mono is a strong, practical pairing that matched the brand's "Systematic Warmth" identity.

---

## Recommended Additions

| File | Purpose | Status |
|------|---------|--------|
| `00-Orchestrator.md` | Master checklist, phase tracker, entry/exit criteria | ✅ Created |
| `TOOLS-REQUIRED.md` | Prerequisites, installation commands, MCP servers | ✅ Created |
| `RENDER-VERIFY.md` | Standard process for rendering SVGs and presenting to user | ✅ Incorporated into Phase 3 |
| `ITERATION-LIMITS.md` | When to pivot approaches, escape hatches, escalation paths | ✅ Incorporated into Phase 3 |

---

## Summary

The skill's architecture is good. Its tooling assumptions and visual production workflow are its weak points. The highest-leverage fixes are:

1. **Add bitmap tracing to Phase 3** (eliminates the 30-iteration problem)
2. **Add an orchestrator** (prevents phase skipping)
3. **Add a render-and-verify step** (closes the visual feedback loop)

These three changes would have saved roughly 60-70% of the time spent on Phase 3 and prevented the Phase 4 skip.

---

## Follow-Up: Comprehensive Gap Analysis

**Date:** 2026-02-06
**Context:** Deep read of all 8 workflow files, 5 templates, example kit, and SKILL.md
**Focus:** Wordmark iteration gap + overall completeness for professional-grade output

---

### 1. Wordmark Iteration Gap (Phase 4)

#### What the workflow says

Phase 4 (`04-Wordmark.md`) covers: picking a font family from a personality table, creating 3-4 lockup variants (name-only, full domain, monospace), aligning mark + text through coordinate adjustments, and building horizontal/stacked/text-only lockups. The gate check is a single line: "User confirms alignment and variants."

#### What it does not say

The workflow is missing nearly the entire typographic exploration and feedback loop that a professional designer would follow. Specifically:

**A. No font exploration step.** The workflow jumps straight from a personality-to-font-direction table to "create variants." There is no step that says: "Present 3-5 font options to the user, rendered at wordmark size, for comparison." The executor picks a font (or defaults to Inter/JetBrains Mono) and proceeds. The user never sees alternatives. In the AutonoLabs execution, this meant the user received wordmarks in a font they never chose.

**B. No weight/style comparison.** Even within a single font family, the difference between Regular (400), Medium (500), SemiBold (600), and Light (300) is significant for wordmark character. The workflow mentions `font-weight: 500` as a default but never asks the executor to show the user weights side-by-side. A professional process would render the brand name at 3-4 weights and let the user react.

**C. No letter-spacing exploration.** The workflow mentions tracking values (-0.01em to -0.02em for Inter, 0 to 0.02em for mono) as static settings. In practice, wordmark letter-spacing is one of the most carefully tuned parameters. The user should see tight vs. normal vs. loose spacing rendered and choose.

**D. No case treatment exploration.** Should the wordmark be lowercase ("autonomolabs"), Title Case ("AutonoLabs"), or UPPERCASE ("AUTONOMOLABS")? The workflow doesn't raise this question. It defaults to whatever the executor assumes.

**E. No feedback loop between font rendering and mark pairing.** The workflow's iteration guidance is limited to "Iterate with small adjustments" on `translate()` and `<text>` coordinates. This is positional refinement only. There is no step for: "Show the user the wordmark next to the mark. Does the typographic weight feel balanced with the mark's visual weight? Does the font personality match the mark's personality?"

**F. No size testing for wordmarks.** Phase 3 has explicit size testing (256px, 64px, 32px, 16px). Phase 4 has none. Wordmarks need to be tested at navigation size (~32px height), hero size (~64px+ height), and favicon-adjacent sizes. A wordmark that looks elegant at 64px may be illegible at 24px.

**G. The gate check is the weakest of any phase.** Compare:
- Phase 0: "Does this capture the soul of what we're building? Does it feel true?"
- Phase 3: "User explicitly locks: 'That's the one.'" with a 9-item quality checklist
- Phase 4: "User confirms alignment and variants." -- no checklist, no rendering requirement, no explicit approval language

#### Recommended additions to Phase 4

```
### Font Exploration (new section, before "Create Variants")

1. Select 3-5 candidate fonts based on the personality table
2. Render the brand name in each font at wordmark size (SVG or PNG)
3. Show at 2-3 weights per font (e.g., Light, Regular, Medium)
4. Present to user with brief rationale for each
5. User selects font + weight direction

### Spacing & Case Exploration (new section)

1. With chosen font, render the brand name at 3 tracking values
2. Show lowercase, Title Case, and UPPERCASE treatments
3. Present side by side
4. User selects preferred treatment

### Wordmark Quality Checks (replace current gate)

Before locking:
- [ ] Font personality matches mark personality
- [ ] Typographic weight balances with mark visual weight
- [ ] Reads clearly at navigation size (32px height)
- [ ] Reads clearly at hero size (64px+ height)
- [ ] Letter-spacing feels intentional (not default)
- [ ] Mark + text gap is optically comfortable
- [ ] Lockup works on both dark and light backgrounds
- [ ] User has seen and approved font choice (not just alignment)
```

---

### 2. Overall Completeness Assessment

The skill produces: an emotive narrative, a philosophy document, a visual philosophy document, a mark SVG, wordmark SVGs, a design guidelines markdown, a DESIGN.md consolidation, and a packaged brand kit folder. This is a solid foundation, but it falls short of what a professional brand agency would deliver. Below is a category-by-category gap analysis.

---

#### 2.1 Font Exploration and Testing ✅ IMPLEMENTED

**Current state:** Phase 4 has a table mapping personality to font direction and lists two "safe defaults" (Inter, JetBrains Mono). Phase 5 defines a type scale. Neither phase involves showing the user rendered font specimens.

**Gap:** There is no step in the entire workflow that shows the user what their chosen fonts actually look like in context. No specimen rendering, no weight comparison, no pairing visualization. The executor picks fonts based on the personality table and moves on. The user's first encounter with their brand's typography is the finished wordmark or the design guidelines document.

**What's needed:**
- A font specimen step (Phase 4 or new sub-phase) that renders 3-5 candidate fonts at display, body, and caption sizes
- Weight comparison renders (Light through Bold) for the selected font
- A pairing visualization showing the primary font + monospace font together in a realistic layout snippet
- Explicit user approval of the font pairing before proceeding to design system

---

#### 2.2 Color Derivation Process ✅ IMPLEMENTED

**Current state:** Phase 5 says "Build outward from the mark's colors and visual philosophy" and then immediately provides a complete hardcoded palette (the Sorted palette). The workflow never explains *how* to derive a full palette from mark colors.

**Gap:** The color derivation process is entirely missing. The workflow jumps from "mark has 2-3 colors" to "here are 20+ color tokens." A professional process would include:

- **Background derivation:** How to take the mark's darkest tone and derive 4 background levels (deep, warm, surface, elevated) with consistent warmth
- **Text color derivation:** How to derive 4 text levels that maintain WCAG AA contrast against each background
- **Functional color selection:** How to choose a green, amber, red, and blue that harmonize with the brand's accent color (not just using Tailwind defaults like `#22c55e`)
- **Accent extension:** How to derive dim/dark variants from the primary accent (e.g., dim = 60% saturation at lower lightness, dark = 30% lightness for backgrounds)
- **Light mode derivation:** How to invert the palette for light mode while preserving brand character (see section 2.7 below)

**What's needed:** A "Color Derivation Guide" section in Phase 5 that walks through the process step-by-step, with formulas or heuristics for each color role. Something like:

```
### Color Derivation Process

1. Start with mark colors (typically 2-3: primary neutral, accent, optional secondary)
2. Derive backgrounds:
   - bg-deep: Darkest neutral from mark, or nearby warm near-black
   - bg-warm: +6-8% lightness from bg-deep, maintain warmth
   - bg-surface: +4-6% lightness from bg-warm
   - bg-elevated: +4-6% lightness from bg-surface
3. Derive text:
   - text-primary: High-contrast against bg-deep (minimum 7:1 ratio)
   - text-secondary: ~60-70% of primary's contrast
   - text-muted: ~35-45% of primary's contrast
   - text-whisper: Near-invisible, for disabled states
4. Select functional colors:
   - Green: Should harmonize with brand accent; test against all backgrounds
   - Amber/Red/Blue: Standard functional meanings, adjusted for warmth
5. Extend accent:
   - accent-dim: Reduce lightness 20-30%, reduce saturation 10-20%
   - accent-dark: For accent-colored backgrounds, very low lightness
6. Validate all pairs: Run every text color against every background for WCAG AA
```

---

#### 2.3 Real-World Application Mockups ❌ NOT IMPLEMENTED

**Current state:** The skill produces SVG assets and markdown documentation. No workflow step creates mockups showing how the brand looks in context.

**Gap:** A professional brand kit includes mockups that show the brand applied to real surfaces. The current skill produces abstract tokens and components but never demonstrates them in use. This means the user cannot evaluate whether their brand *works* until they (or someone else) builds something with it.

**What's needed (new Phase 5.5 or addition to Phase 5):**
- **Website header mockup:** Navigation bar with logo, menu items, CTA button -- rendered as an SVG or HTML screenshot
- **App icon mockup:** The mark placed inside iOS/Android icon shapes with proper padding and background color
- **Business card mockup:** Front and back, showing mark, wordmark, and typography in a print context
- **Dashboard snippet:** A small data table or card layout using the design system's colors, fonts, spacing, and components
- **Dark-on-light and light-on-dark:** The same mockup rendered in both modes

This does not need to be pixel-perfect. Even a simple SVG or HTML layout rendered to PNG would give the user something concrete to react to. The skill's current output is entirely abstract until someone implements it.

---

#### 2.4 Favicon and App Icon Generation ✅ IMPLEMENTED

**Current state:** Phase 3 mentions `[brand]-favicon.png` as an output (32px) and has size testing checkboxes for 256px, 64px, 32px, and 16px. Phase 7 (Packaging) includes the favicon in the file list. The design-guidelines template mentions `sorted-og-image.png` (1200x630 for social) in a checklist but the workflow never describes how to create it.

**Gap:** The skill produces a single 32px favicon PNG. A professional brand kit needs:

- **favicon.ico:** Multi-resolution ICO file (16px + 32px + 48px) for legacy browser support
- **favicon-16.png, favicon-32.png, favicon-48.png:** Individual PNGs for modern browsers
- **apple-touch-icon.png:** 180x180 for iOS home screen bookmarks
- **android-chrome-192.png, android-chrome-512.png:** For Android PWA manifest
- **og-image.png:** 1200x630 for Open Graph / social sharing (mentioned in the Sorted example checklist but never addressed in any workflow)
- **App icon at required sizes:** 1024x1024 master, with masked/unmasked variants for iOS and Android

The skill also has no guidance on how to adapt the mark for icon contexts. The mark may need to be redrawn or simplified differently for a circle-masked iOS icon vs. a square favicon vs. a rounded-rectangle Android icon. Phase 3 tests sizes but doesn't produce the actual export set.

**What's needed:**
- An "Icon & Favicon Export" step in Phase 7 (Packaging) or as a Phase 4.5
- Explicit list of required sizes and formats
- Guidance on mark adaptation for different icon shapes (circle mask, rounded rect, square)
- Background color guidance for icon contexts (transparent vs. brand color vs. white)

---

#### 2.5 Social Media Asset Templates ✅ IMPLEMENTED

**Current state:** Not addressed anywhere in the skill. The Sorted example checklist mentions `sorted-og-image.png` but no workflow produces it or any social templates.

**Gap:** Modern brands need social media assets from day one:

- **Open Graph image:** 1200x630 (Facebook, LinkedIn, Twitter/X link previews)
- **Twitter/X header:** 1500x500
- **Profile avatar:** Square, typically mark-only, at high resolution
- **Instagram/social post template:** 1080x1080 with brand colors, fonts, and mark placement
- **GitHub social preview:** 1280x640

These are straightforward compositions using the existing mark, wordmark, colors, and typography. An LLM can generate these as SVGs and export to PNG. The skill should include a step that produces at least the OG image and a profile avatar, since these are needed before any public launch.

**What's needed:** A "Social Assets" section in Phase 7 or a new Phase 6.5 that generates at minimum:
- OG image (mark + wordmark centered on brand background)
- Profile avatar (mark on brand background, square, exportable at 400x400+)
- Template guidance for common social formats

---

#### 2.6 Brand Guidelines PDF Generation ❌ NOT IMPLEMENTED

**Current state:** The skill produces `DESIGN.md` and `[brand]-design-guidelines.md` as markdown files. No PDF is generated.

**Gap:** Markdown is excellent for developer consumption and LLM ingestion. It is poor for stakeholder handoff, investor presentations, or sharing with non-technical collaborators. A professional brand kit includes a visual PDF that presents the brand identity with proper layout, rendered logo examples, color swatches, and typography specimens.

**Realistic assessment:** Generating a well-designed PDF from an LLM is a non-trivial problem. Options include:
- Generating HTML with inline styles and converting via `wkhtmltopdf` or Puppeteer
- Using a LaTeX template
- Using a markdown-to-PDF tool like `pandoc` with a custom template
- Generating a simple PDF via a Node.js library like `pdfkit`

**What's needed:** This is a "nice to have" rather than critical. The skill could include:
- A `brand-guidelines.html` template that renders the design system visually (color swatches, font specimens, logo display)
- A conversion step: `npx puppeteer-cli screenshot brand-guidelines.html brand-guidelines.pdf`
- Or simply a note in Phase 7: "For stakeholder-facing PDF, render the HTML guidelines template to PDF"

---

#### 2.7 Light Mode Derivation Process ✅ IMPLEMENTED

**Current state:** Phase 5 mentions light mode in passing:
- CSS: `@media (prefers-color-scheme: light) { --bg-deep: #ffffff; --text-primary: #1a1a1a; }` with a "..." comment
- iOS: Dark/light mode values referenced but not specified
- The anti-slop checklist says "Colors work in light and dark modes on both platforms"

The actual light mode palette is never derived. The workflow provides a complete dark mode palette with 20+ tokens and then hand-waves light mode as "override all color tokens."

**Gap:** Light mode is not just "invert the values." A professional light mode derivation involves:

- **Background inversion:** bg-deep becomes white or warm off-white, but bg-warm, bg-surface, and bg-elevated need to become progressively *darker* shades of light gray (the opposite of dark mode's progression)
- **Text inversion:** text-primary becomes near-black, but the warmth character should be preserved (not pure `#000000`)
- **Accent preservation:** The brand's green/accent color often needs adjustment for light backgrounds (darker or more saturated to maintain contrast)
- **Border adjustment:** Borders that were light-on-dark need to become dark-on-light with different opacity characteristics
- **Functional color adjustment:** Green/amber/red may need slight saturation or lightness changes to maintain legibility on white backgrounds

**What's needed:** A "Light Mode Derivation" section in Phase 5 that:
1. Provides the full set of light mode tokens (not just 2 examples with "...")
2. Explains the derivation logic (backgrounds go light-to-lighter instead of dark-to-lighter)
3. Specifies the actual hex values for every token in light mode
4. Validates contrast ratios for light mode combinations
5. Notes where accent colors need adjustment

---

#### 2.8 Accessibility Validation ✅ IMPLEMENTED

**Current state:** Phase 5 ends with a note: "Ensure color contrast meets WCAG AA (4.5:1 for body text, 3:1 for large text)." The anti-slop checklist says "Sufficient contrast (WCAG AA: 4.5:1 for body, 3:1 for large text)." The DESIGN template includes a "4.5:1 minimum" note in logo usage guidelines.

**Gap:** Accessibility is mentioned as a principle but never verified. There is no step in any workflow that actually checks contrast ratios. The executor is told to "ensure" compliance but given no mechanism to do so. This is aspirational, not operational.

In the Sorted example, the palette uses `#a8a2b2` (text-secondary) on `#0e0e10` (bg-deep). That pair has a contrast ratio of approximately 7.4:1 -- passing. But `#625e6c` (text-muted) on `#16151a` (bg-warm) is approximately 3.1:1 -- which passes for large text but fails for body text. Without actual checking, these issues go unnoticed.

**What's needed:**
- A contrast-checking step in Phase 5 that tests every text/background combination
- Either a tool requirement (e.g., `npx wcag-contrast-checker`) or a manual process (the executor computes relative luminance and contrast ratio for each pair)
- A contrast matrix in the design guidelines output:

```
### Contrast Validation Matrix

| Text Color | Background | Ratio | WCAG AA (body) | WCAG AA (large) |
|-----------|-----------|-------|----------------|-----------------|
| text-primary (#e4e1e8) | bg-deep (#0e0e10) | 13.8:1 | PASS | PASS |
| text-secondary (#a8a2b2) | bg-deep (#0e0e10) | 7.4:1 | PASS | PASS |
| text-muted (#625e6c) | bg-warm (#16151a) | 3.1:1 | FAIL | PASS |
| green (#22c55e) | bg-deep (#0e0e10) | 6.2:1 | PASS | PASS |
```

- Remediation guidance: "If a pair fails, adjust the lighter color's lightness until it passes"
- Focus state visibility check: "Is the focus ring color (#22c55e) visible against all background colors?"

---

#### 2.9 File Format Variety and Export Pipeline ✅ IMPLEMENTED

**Current state:** The skill produces SVGs for marks and wordmarks, a single 32px favicon PNG, and markdown documents. Phase 7 collects these into a folder and zips it.

**Gap:** A professional brand kit includes multiple export formats and sizes. The current output is SVG-only for vector assets and single-size for raster assets.

**What's needed in the packaging phase:**

```
### Required Exports

Mark:
- [brand]-mark-final.svg (vector, scalable)
- [brand]-mark-512.png (high-res raster)
- [brand]-mark-256.png (standard raster)
- [brand]-mark-64.png (app icon size)
- [brand]-mark-white.svg (white version for dark backgrounds)
- [brand]-mark-dark.svg (dark version for light backgrounds)

Wordmarks:
- [brand]-wordmark-horizontal.svg
- [brand]-wordmark-horizontal-512.png
- [brand]-wordmark-stacked.svg (if applicable)
- [brand]-wordmark-textonly.svg

Favicons:
- favicon.ico (16+32+48 multi-res)
- favicon-16.png
- favicon-32.png
- apple-touch-icon.png (180x180)

Social:
- og-image.png (1200x630)
- avatar.png (400x400)

Documents:
- DESIGN.md
- [brand]-design-guidelines.md
- [brand]-philosophy.md
- [brand]-visual-philosophy.md
- README.md
```

The skill should also include the `rsvg-convert` commands (or equivalent) to produce all PNG exports from the SVG sources, rather than leaving it to the user.

---

### 3. Summary: Priority-Ranked Gaps

| Priority | Gap | Effort | Impact | Status |
|----------|-----|--------|--------|--------|
| **P0** | Phase 4 font exploration/feedback loop | Low | High | ✅ Implemented |
| **P0** | Color derivation process (dark mode) | Medium | High | ✅ Implemented |
| **P0** | Light mode derivation process | Medium | High | ✅ Implemented |
| **P1** | Accessibility contrast checking | Low | High | ✅ Implemented |
| **P1** | Favicon/icon export pipeline | Low | Medium | ✅ Implemented |
| **P1** | Wordmark size testing + gate check | Low | Medium | ✅ Implemented |
| **P2** | Real-world application mockups | Medium | High | ❌ Future work |
| **P2** | Social media assets (OG image, avatar) | Low | Medium | ✅ Implemented |
| **P2** | File format variety (PNG exports at sizes) | Low | Medium | ✅ Implemented |
| **P3** | Brand guidelines PDF | High | Medium | ❌ Future work |
| **P3** | Mark color variations (white, dark) | Low | Low | ✅ Implemented |

---

### 4. Observations on Skill Architecture

**What the skill gets right that most brand processes do not:**

1. The emotive narrative as Phase 0 is genuinely innovative. It gives the LLM a durable emotional context that prevents generic drift across later phases. This is the skill's strongest architectural decision.

2. The anti-AI-slop framework is well-conceived. The "decision testing" questions ("Does this express our emotive narrative?" / "Could this only be [Brand]?") are the right questions, even if the current checklists mix verifiable and aspirational items.

3. The phased progression from meaning to visuals to system to documentation is sound creative architecture. Most brand processes either skip the meaning (jumping to aesthetics) or skip the system (stopping at a logo).

**What the skill gets wrong architecturally:**

1. The skill assumes the executor is a designer who happens to be an LLM. It is not. The workflows for Phases 0-2 (text generation) are excellent because they play to LLM strengths. The workflows for Phases 3-5 (visual production) need to be restructured around the assumption that the executor cannot see its own output and cannot make aesthetic judgments visually. Every visual decision needs to be presented to the user, not made by the executor.

2. The skill has no concept of "progressive disclosure of options." A professional designer would show the client a curated set of options at every decision point (3 font options, 3 color palette directions, 3 layout approaches). The current skill makes most of these decisions implicitly. Phase 2 (Visual Direction) is the only phase that explicitly presents options. Phases 4 and 5 should follow the same pattern.

3. The templates and examples are too tightly coupled to the Sorted brand. The design-guidelines template, the DESIGN template, and the Phase 5 workflow all contain Sorted's actual hex values. While the audit already flagged this (Issue #4), the deeper problem is that the example is the only reference the executor has for "what good looks like." A second example with a fundamentally different aesthetic (warm, light-mode-first, serif-based, organic instead of geometric) would dramatically improve the skill's versatility.

---

### 5. Specific Recommendations for Phase 4 Rewrite ✅ IMPLEMENTED

Phase 4 has been rewritten with all recommended steps. The current `04-Wordmark.md` includes: mandatory font exploration (Step 1), typographic refinement with tracking and case treatment (Step 2), variant creation (Step 3), alignment (Step 4), lockup system (Step 5), size testing at hero/nav/compact (Step 6), a 10-item quality checklist, and a strengthened gate check.

The original recommended structure (preserved below for reference):

```
# Phase 4: Wordmark & Lockups

## Step 1: Font Exploration
- Select 3-5 candidate fonts based on personality direction
- Render brand name in each font at 3 weights
- Present specimens to user
- User selects font + weight

## Step 2: Typographic Refinement
- Render brand name in selected font at 3 tracking values
- Show case treatments (lowercase, Title Case, UPPERCASE)
- Present to user
- User selects treatment

## Step 3: Mark + Text Pairing
- Create initial lockup combining mark + chosen typography
- Render at 3 sizes (hero, navigation, compact)
- Present to user
- Iterate on spacing, alignment, scale balance

## Step 4: Variant System
- Horizontal lockup (mark left, text right)
- Stacked lockup (mark above, text below)
- Text-only (no mark)
- Short variant (abbreviated name if applicable)

## Step 5: Size Testing
- Render all variants at hero (200px+), nav (40px), and compact (24px) sizes
- Verify legibility at each size

## Quality Checks
[Full checklist as described in section 1 above]

## Gate
User has seen and approved:
- [ ] Font choice (from presented options)
- [ ] Weight and tracking
- [ ] Case treatment
- [ ] Lockup alignment and spacing
- [ ] All variants at all sizes
```

---

### 6. What "Professional-Grade" Would Require Beyond This Skill

Even with all the above gaps filled, the skill would produce a strong *startup-grade* brand kit -- sufficient for a launch, developer documentation, and basic marketing. To reach *agency-grade*, additional capabilities would be needed that are likely outside the scope of an LLM-driven skill:

- **Custom lettering / logotype:** Hand-drawn or custom-modified letterforms for the wordmark (requires a human designer or specialized AI tool)
- **Brand illustration system:** A defined illustration style with sample assets (spot illustrations, icons, patterns)
- **Photography direction:** Art direction for brand photography (lighting, color treatment, subject matter, composition guidelines)
- **Print specifications:** CMYK color values, Pantone matches, bleed/trim guidelines
- **Motion/video brand:** Intro animations, transitions, video title card templates
- **Audio branding:** Sonic logo, notification sounds, hold music guidelines
- **Environmental/spatial:** Signage specifications, booth design, physical space guidelines

These are worth acknowledging as "beyond current scope" rather than trying to add them. The skill's sweet spot is digital brand identity for startups and developer tools, and it should aim to be the best at that rather than trying to replace a full-service agency.

---

## Addendum 3: The Convergence Problem — Why Every Page Looks the Same ✅ IMPLEMENTED

> **Resolution:** This was addressed by adding Phase 5.5: Composition & Visual Identity (`05A-CompositionIdentity.md`) — an evolutionary diverge/kill/mutate process where the LLM generates structural diversity and the user selects for distinctiveness. Also added `ADDENDUM-4-WEB-PRESENCE.md` with the full theoretical framework, and a comprehensive LLM Design Limitations section in `SKILL.md`. The proposed phase addition below was implemented as described.

**Date:** 2026-02-06 (post-deployment)
**Trigger:** After executing the full brand skill for AutonoLabs.ai and deploying the landing page, it was visually indistinguishable from two other sites (sorted.fund, compost.fi) built by the same process. Same layout, same rhythm, same visual weight. Three brands, one page.

### Root Cause

LLMs generate from the center of their training distribution. "Good dark tech landing page" has a very tight center: left-aligned hero, thin display font, muted subtext, green/accent CTA button, arrow link, horizontal dividers, card grids. The brand skill produces **tokens** (colors, fonts, spacing) but not **composition** — so when you hand those tokens to an LLM and say "build a page," it defaults to the statistical average of what "good" looks like across its training data.

The design system is all ingredients, no recipe. Three kitchens with the same ingredients make the same dish.

### The Missing Layer: Composition

Between "design tokens" and "build the page," there is an entire creative layer the skill skips: **how this brand uniquely occupies space.** This is the difference between a brand you recognize from a blurred screenshot and a brand that could be anyone.

The skill needs to add a **Composition Phase** (between current Phase 5 and Phase 6) that defines:

#### 1. Anti-Reference Board (Mandatory)

Not just inspiration — explicit anti-patterns with named targets:

- "This must NOT look like [specific site]"
- "If you can swap in another company's logo and the page still works, it has failed"
- **The blur test:** Reduce the page to 20% visibility. Can you tell it apart from Linear/Stripe/Vercel? No? Reject it.

This forces the LLM to actively check its output against known patterns and reject convergence.

#### 2. Signature Visual Device (Mandatory)

Every memorable brand has 1-2 visual moves that are *theirs*:

| Brand | Signature Device |
|-------|-----------------|
| Stripe | Gradient mesh backgrounds |
| Linear | Motion blur, velocity lines |
| Vercel | Geometric triangle, black/white precision |
| Bloomberg | Dense terminal grid, data-first |
| Notion | Illustration system, warm playfulness |

The skill should **require** identification of a brand's signature device before any layout work begins. Not "what colors" — "what is the one visual thing that makes this brand recognizable from across a room?"

#### 3. Cross-Category References (Mandatory)

The skill currently draws references from the same category (other tech sites), which guarantees convergence. It should **require at least 3 references from outside the brand's category:**

- Editorial print layouts (magazine spreads, newspaper front pages)
- Architectural portfolios
- Financial terminals and trading interfaces
- Museum exhibition design
- Scientific paper layouts
- Control room / mission control displays
- Airport/transit information systems

These break the LLM out of "tech landing page" pattern matching by introducing structural ideas from domains with fundamentally different layout traditions.

#### 4. Compositional Constraints with Teeth

Not "use a grid" but rules that **rule out the default:**

- "No section may be a simple centered single-column stack"
- "Every viewport-height must contain at least one element that breaks the grid"
- "The page rhythm should feel like [specific non-tech reference], not a marketing brochure"
- "Minimum information density: N distinct data points visible above the fold"
- "At least one section must use asymmetric layout"

These constraints are valuable precisely because they prevent the LLM from reaching for the easiest pattern.

#### 5. Visual Tension Expression

Good brands have internal tensions. The skill should identify them and require the layout to **express** them visually, not resolve them:

- AutonoLabs: *systematic vs warm, quiet vs infrastructure, patient vs ambitious*
- Express this as: warm organic display type COLLIDING with hard monospace data grids, generous negative space NEXT TO dense information blocks, soft colors containing sharp technical content

The temptation is always to harmonize tensions into smooth generic aesthetics. The skill should resist this explicitly.

#### 6. Multiple Radical Layouts (Mandatory)

Instead of generating one layout, the skill should require:

1. Generate 3-4 **structurally different** approaches (not color/font variants — fundamentally different spatial compositions)
2. Name each approach (e.g., "The Terminal," "The Lab Notebook," "The Gallery," "The Control Room")
3. Explicitly select the most distinctive one that still works
4. Document why the others were rejected

This forces exploration before convergence.

#### 7. The Density Mandate

If the brand philosophy says "dense, not minimal" and "organized complexity," the skill should **enforce** this:

- Require a minimum element count per viewport
- Show real data, real numbers, real status indicators — not just marketing prose
- Allow whitespace to be intentional, not the default

The LLM default is minimal because minimal is safe. The skill must override this when the brand calls for density.

### Proposed Phase Addition

Insert between current Phase 5 (Design System) and Phase 6 (DESIGN.md):

**Phase 5.5: Composition & Visual Identity**

Inputs: Brand philosophy, design tokens, anti-references
Outputs:
- Anti-reference board (3-5 named sites/patterns to avoid)
- Signature visual device (1-2, with rationale)
- Cross-category reference board (3+ non-tech references)
- Compositional constraints (5+ specific layout rules)
- Visual tension map (brand tensions → spatial expressions)
- 3-4 named layout approaches with selection rationale

Gate: Must pass the blur test — at 20% visibility, the layout silhouette must be distinguishable from the top 5 anti-references.

### Severity

**Critical.** This is arguably the highest-severity issue in the skill because it means the entire 7-phase process — all the philosophy, all the token work, all the careful font selection — produces output that is visually indistinguishable from a site that skipped all of it. The tokens are necessary but insufficient. Without composition, the brand has no spatial identity.

### Impact on LLM Design Capabilities

This finding has implications beyond this one skill:

- LLMs will always converge to the distributional center unless actively constrained away from it
- "Good taste" prompting produces the average of good taste, which is generic
- Distinctiveness requires **explicit structural constraints** that rule out the default
- The most valuable design instructions for LLMs are negative ("never do X") rather than positive ("try to be distinctive")
- Cross-domain reference injection is the single highest-leverage intervention for breaking pattern convergence
