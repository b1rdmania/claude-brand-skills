# Phase 6: Packaging

Collect everything into a self-contained kit for handoff.

## Time

5-10 minutes.

## Prerequisites

- All phases complete
- All assets finalized

---

## Process

### 1. Create Folder

```bash
mkdir ~/Downloads/[brand]-brand-kit
```

### 2. Collect Assets

```bash
cd ~/Downloads

# Mark
cp [brand]-mark-final.svg [brand]-brand-kit/
cp [brand]-favicon.png [brand]-brand-kit/

# Wordmarks
cp [brand]-wordmark-final.svg [brand]-brand-kit/
cp [brand]-wordmark-short.svg [brand]-brand-kit/

# Docs
cp [brand]-design-guidelines.md [brand]-brand-kit/
cp [brand]-philosophy.md [brand]-brand-kit/
cp [brand]-visual-philosophy.md [brand]-brand-kit/
```

### 3. Write README

Quick-start doc for anyone picking up the kit:

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

### 4. Verify Contents

```bash
ls -la [brand]-brand-kit/
```

Expected:
```
[brand]-brand-kit/
├── README.md
├── [brand]-mark-final.svg
├── [brand]-favicon.png
├── [brand]-wordmark-final.svg
├── [brand]-wordmark-short.svg
├── [brand]-design-guidelines.md
├── [brand]-philosophy.md
└── [brand]-visual-philosophy.md
```

### 5. Zip

```bash
zip -r [brand]-brand-kit.zip [brand]-brand-kit/
```

### 6. Deliver

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
- [ ] Mark SVG
- [ ] Favicon PNG
- [ ] Primary wordmark SVG
- [ ] Design guidelines MD

**Recommended:**
- [ ] Short wordmark SVG
- [ ] Philosophy docs
- [ ] Visual reference/canvas

---

## Handoff Standard

The package should be usable without further questions. Someone should be able to:
1. Unzip
2. Read README
3. Implement

If they need to ask questions, documentation is incomplete.

---

## Outputs

- `~/Downloads/[brand]-brand-kit/`
- `~/Downloads/[brand]-brand-kit.zip`
