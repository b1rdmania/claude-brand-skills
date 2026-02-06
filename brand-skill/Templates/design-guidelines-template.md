# [Brand] Design System

**v1.0 — [Movement Name]**

---

## Foundation

[2-3 sentences on what drives this brand's visual identity]

**Guiding ideas:**
1. **[Concept]** — [What it means in practice]
2. **[Concept]** — [What it means in practice]
3. **[Concept]** — [What it means in practice]
4. **[Concept]** — [What it means in practice]
5. **[Concept]** — [What it means in practice]

---

## Mark

### About

[What the mark represents and its key visual components]

**Assets:**
- `[brand]-mark-final.svg` — Main mark
- Minimum size: 24px tall

### Mark Colors

| Part | Hex | Note |
|------|-----|------|
| [Part] | `#hex` | [Context] |
| [Part] | `#hex` | [Context] |

### Breathing Room

Leave space equal to [measurement] on all sides.

### Avoid

- Rotating
- Recoloring
- Adding shadows or gradients
- Stretching
- Placing on cluttered backgrounds

---

## Wordmark

### Options

**Full:** Mark + "[complete name or domain]"
**Short:** Mark + "[abbreviated name]"
**Standalone:** "[name]" without mark

### Wordmark Type

- Family: [Font name]
- Weight: [Weight]
- Letter-spacing: [Value]

---

## Colors

### Backgrounds

| Token | Hex | Where |
|-------|-----|-------|
| Deep | `#hex` | Base layer |
| Warm | `#hex` | Cards, surfaces |
| Surface | `#hex` | Inputs, recesses |
| Elevated | `#hex` | Hovers |

### Borders

| Token | Hex | Where |
|-------|-----|-------|
| Border | `#hex` | Standard dividers |
| Border Light | `#hex` | Emphasized dividers |

### Text

| Token | Hex | Where |
|-------|-----|-------|
| Primary | `#hex` | Headlines, key content |
| Secondary | `#hex` | Body copy |
| Muted | `#hex` | Hints, captions |
| Whisper | `#hex` | Disabled elements |

### Status Colors

| Token | Hex | Where |
|-------|-----|-------|
| [Accent] | `#hex` | Success, CTAs |
| [Accent Dim] | `#hex` | Hover states |
| Amber | `#hex` | Warnings |
| Red | `#hex` | Errors |
| Blue | `#hex` | Links, information |

### Brand Tones (Optional)

| Token | Hex | Where |
|-------|-----|-------|
| [Tone] | `#hex` | [Context] |
| [Tone Dim] | `#hex` | [Context] |

---

## Type

### Families

**Interface:**
```css
font-family: '[Font]', -apple-system, BlinkMacSystemFont, sans-serif;
```

**Monospace:**
```css
font-family: '[Font]', 'SF Mono', monospace;
```

### Scale

| Level | Size | Weight | Leading | Context |
|-------|------|--------|---------|---------|
| Display | 48px | 500 | 1.1 | Heroes |
| H1 | 32px | 500 | 1.2 | Page titles |
| H2 | 24px | 500 | 1.3 | Sections |
| H3 | 18px | 500 | 1.4 | Cards |
| Body | 15px | 400 | 1.6 | Prose |
| Small | 14px | 400 | 1.5 | Supporting text |
| Caption | 12px | 400 | 1.4 | Labels |
| Mono | 14px | 400 | 1.5 | Code |

### Labels

- 11-12px
- Weight 500
- ALL CAPS
- 0.08em tracking
- Muted color

---

## Spacing

### Base: 8px

| Token | Value | Context |
|-------|-------|---------|
| xs | 4px | Tight spacing |
| sm | 8px | Related items |
| md | 16px | Standard padding |
| lg | 24px | Section gaps |
| xl | 32px | Large gaps |
| 2xl | 48px | Page sections |
| 3xl | 64px | Hero areas |

### Component Padding

- Buttons: 12px 20px
- Inputs: 12px 16px
- Cards: 20px 24px
- Modals: 24px 32px

---

## Components

### Buttons

**Primary**
```css
background: var(--[accent]);
color: var(--bg-deep);
font-weight: 500;
padding: 12px 20px;
border-radius: 6px;
```

**Secondary**
```css
background: transparent;
border: 1px solid var(--border);
color: var(--text-primary);
padding: 12px 20px;
border-radius: 6px;
```

**Ghost**
```css
background: transparent;
color: var(--text-secondary);
padding: 12px 20px;
```

### Inputs

```css
background: var(--bg-surface);
border: 1px solid var(--border);
color: var(--text-primary);
padding: 12px 16px;
border-radius: 6px;
```

On focus: `border-color: var(--[accent]);`

### Cards

```css
background: var(--bg-warm);
border: 1px solid var(--border);
border-radius: 8px;
padding: 20px 24px;
```

### Status Dots

- 8px diameter
- Active: [accent color]
- Caution: Amber
- Problem: Red
- Off: Muted

---

## Layout

### Widths

| Type | Max |
|------|-----|
| Content | 720px |
| Dashboard | 1200px |
| Full | 1440px |

### Grid

12 columns, 24px gaps.

---

## Motion

### Durations

| Type | Time | Curve |
|------|------|-------|
| Micro | 100ms | ease-out |
| Default | 200ms | ease-out |
| Enter | 300ms | ease-out |
| Exit | 200ms | ease-in |

### Guidelines

- Movement serves purpose
- State changes are perceptible
- Nothing purely decorative

---

## Language

### Character

[Short description of how the brand speaks]

### Good

- "[Example]"
- "[Example]"

### Bad

- "[Example]"
- "[Example]"

---

## Tokens

```css
:root {
  /* Backgrounds */
  --bg-deep: #hex;
  --bg-warm: #hex;
  --bg-surface: #hex;
  --bg-elevated: #hex;

  /* Borders */
  --border: #hex;
  --border-light: #hex;

  /* Text */
  --text-primary: #hex;
  --text-secondary: #hex;
  --text-muted: #hex;
  --text-whisper: #hex;

  /* Status */
  --[accent]: #hex;
  --[accent]-dim: #hex;
  --amber: #hex;
  --red: #hex;

  /* Brand */
  --[tone]: #hex;

  /* Spacing */
  --space-xs: 4px;
  --space-sm: 8px;
  --space-md: 16px;
  --space-lg: 24px;
  --space-xl: 32px;

  /* Type */
  --font-sans: '[Font]', -apple-system, sans-serif;
  --font-mono: '[Font]', monospace;

  /* Corners */
  --radius-sm: 4px;
  --radius-md: 6px;
  --radius-lg: 8px;
}
```

---

*[Movement Name]: [Tagline]*
