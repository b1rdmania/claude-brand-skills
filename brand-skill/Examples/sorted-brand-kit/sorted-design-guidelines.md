# Sorted.fund Design Guidelines

**Version 1.0 — Utility Sublime**

---

## Philosophy

Sorted is invisible infrastructure. The design language reflects this: functional, warm, systematic. The best infrastructure is the kind you forget exists — until you need to check on it. Then it should be clear, confident, and informative.

**Core principles:**
1. **Invisible until needed** — UI disappears into function
2. **Green means go** — Color carries meaning, not decoration
3. **Warm, not cold** — Infrastructure hums with energy
4. **Dense, not cluttered** — Respect developer time and screen
5. **Sorted, not revolutionary** — Quiet confidence, not hype

---

## Logo

### The Mark

A flowing wave with a green terminal dot. Represents:
- Flow through infrastructure (the wave)
- Successful delivery/output (the green dot)
- "Sorted" — handled, complete

**Files:**
- `sorted-mark-final.svg` — Primary mark
- Use at minimum 24px height

### Colors in Mark

| Element | Hex | Usage |
|---------|-----|-------|
| Wave | `#52505a` | Warm gray, infrastructure tone |
| Dot | `#22c55e` | Signal green, active/success |

### Clear Space

Maintain clear space equal to the dot radius around all sides of the mark.

### Don'ts
- Don't rotate the mark
- Don't change the colors
- Don't add effects (shadows, gradients)
- Don't stretch or distort

---

## Wordmark

Three lockup options:

### Horizontal (Primary)
Mark + "sorted" — for headers, navigation

### Horizontal with TLD
Mark + "sorted.fund" — `.fund` in green, ties to the dot

### Monospace Variant
Mark + "sorted" in monospace — for code contexts, API docs

**Typography in wordmark:**
- Sans variant: Inter Medium, -0.02em tracking
- Mono variant: JetBrains Mono Regular, 0.02em tracking

---

## Color Palette

### Backgrounds

| Name | Hex | Usage |
|------|-----|-------|
| Deep | `#0e0e10` | Primary background |
| Warm | `#16151a` | Cards, elevated surfaces |
| Surface | `#201e24` | Inputs, wells |
| Surface Light | `#2a2830` | Hover states |

### Borders

| Name | Hex | Usage |
|------|-----|-------|
| Border | `#37343e` | Default borders |
| Border Light | `#484452` | Emphasized borders |

### Text

| Name | Hex | Usage |
|------|-----|-------|
| Primary | `#e4e1e8` | Headings, important text |
| Secondary | `#a8a2b2` | Body text, descriptions |
| Muted | `#625e6c` | Labels, hints |
| Whisper | `#3a3741` | Disabled, subtle markers |

### Functional Colors

| Name | Hex | Usage |
|------|-----|-------|
| Green (Signal) | `#22c55e` | Success, active, healthy, CTAs |
| Green (Dim) | `#187840` | Secondary green, hover |
| Green (Dark) | `#0f4d2a` | Green backgrounds |
| Amber | `#cf9a37` | Warning, pending |
| Red | `#dc2626` | Error, critical |
| Blue (Cable) | `#5886b0` | Links, info (use sparingly) |

### Infrastructure Accents

| Name | Hex | Usage |
|------|-----|-------|
| Copper | `#b07e58` | Accent, premium elements |
| Copper Dim | `#785640` | Secondary copper |

---

## Typography

### Font Stack

**UI/Interface:**
```css
font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
```

**Code/Data:**
```css
font-family: 'JetBrains Mono', 'SF Mono', 'Fira Code', monospace;
```

### Type Scale

| Name | Size | Weight | Line Height | Usage |
|------|------|--------|-------------|-------|
| Display | 48px | 500 | 1.1 | Hero headlines |
| H1 | 32px | 500 | 1.2 | Page titles |
| H2 | 24px | 500 | 1.3 | Section headers |
| H3 | 18px | 500 | 1.4 | Card titles |
| Body | 15px | 400 | 1.6 | Paragraphs |
| Body Small | 14px | 400 | 1.5 | Secondary text |
| Caption | 12px | 400 | 1.4 | Labels, hints |
| Mono | 14px | 400 | 1.5 | Code, data |
| Mono Small | 12px | 400 | 1.4 | Inline code |

### Labels

Uppercase labels use:
- Font: Inter or mono
- Size: 11-12px
- Weight: 500
- Letter-spacing: 0.08em
- Color: Muted (`#625e6c`)

---

## Spacing

### Base Unit

8px base unit. All spacing derives from this.

| Token | Value | Usage |
|-------|-------|-------|
| xs | 4px | Tight gaps |
| sm | 8px | Related elements |
| md | 16px | Default padding |
| lg | 24px | Section gaps |
| xl | 32px | Major sections |
| 2xl | 48px | Page sections |
| 3xl | 64px | Hero spacing |

### Component Padding

- Buttons: 12px 20px
- Inputs: 12px 16px
- Cards: 20px 24px
- Modals: 24px 32px

---

## Components

### Buttons

**Primary (Green)**
```css
background: #22c55e;
color: #0e0e10;
font-weight: 500;
padding: 12px 20px;
border-radius: 6px;
```

**Secondary (Outline)**
```css
background: transparent;
border: 1px solid #37343e;
color: #e4e1e8;
padding: 12px 20px;
border-radius: 6px;
```

**Ghost**
```css
background: transparent;
color: #a8a2b2;
padding: 12px 20px;
```

### Inputs

```css
background: #201e24;
border: 1px solid #37343e;
color: #e4e1e8;
padding: 12px 16px;
border-radius: 6px;
font-family: inherit; /* or mono for code inputs */
```

Focus state: `border-color: #22c55e;`

### Cards

```css
background: #16151a;
border: 1px solid #37343e;
border-radius: 8px;
padding: 20px 24px;
```

### Status Indicators

Small dots indicating system status:
- Size: 8px diameter
- Green (`#22c55e`): Healthy/Active
- Amber (`#cf9a37`): Warning/Pending
- Red (`#dc2626`): Error/Critical
- Gray (`#625e6c`): Inactive/Disabled

---

## Layout

### Max Widths

| Context | Width |
|---------|-------|
| Content | 720px |
| Dashboard | 1200px |
| Full | 1440px |

### Grid

12-column grid with 24px gutters.

### Density

Sorted uses **functional density** — information-rich but organized:
- Minimize whitespace between related elements
- Use borders/backgrounds to group, not excessive spacing
- Tables and lists should be scannable
- Every element earns its space

---

## Motion

### Timing

| Type | Duration | Easing |
|------|----------|--------|
| Micro | 100ms | ease-out |
| Default | 200ms | ease-out |
| Enter | 300ms | ease-out |
| Exit | 200ms | ease-in |

### Principles

- Motion is purposeful, not decorative
- Status changes should be visible (color transitions)
- No gratuitous animations
- Loading states use subtle pulse, not spinners

---

## Voice & Tone

### Writing Style

- Brief, confident, not arrogant
- Technical but accessible
- No marketing superlatives
- No exclamation points

### Examples

**Good:**
- "Transaction complete"
- "One API call. Zero wallet friction."
- "Balance: 1,247.89 USDC"

**Avoid:**
- "Awesome! Your transaction was successful!"
- "Revolutionary gasless infrastructure solution"
- "Balance: You have 1,247.89 USDC remaining in your account"

---

## Code Examples

### CSS Variables

```css
:root {
  /* Backgrounds */
  --bg-deep: #0e0e10;
  --bg-warm: #16151a;
  --bg-surface: #201e24;
  --bg-surface-light: #2a2830;

  /* Borders */
  --border: #37343e;
  --border-light: #484452;

  /* Text */
  --text-primary: #e4e1e8;
  --text-secondary: #a8a2b2;
  --text-muted: #625e6c;
  --text-whisper: #3a3741;

  /* Functional */
  --green: #22c55e;
  --green-dim: #187840;
  --amber: #cf9a37;
  --red: #dc2626;

  /* Accents */
  --copper: #b07e58;
  --blue: #5886b0;

  /* Spacing */
  --space-xs: 4px;
  --space-sm: 8px;
  --space-md: 16px;
  --space-lg: 24px;
  --space-xl: 32px;

  /* Typography */
  --font-sans: 'Inter', -apple-system, sans-serif;
  --font-mono: 'JetBrains Mono', 'SF Mono', monospace;

  /* Radii */
  --radius-sm: 4px;
  --radius-md: 6px;
  --radius-lg: 8px;
}
```

---

## Files Checklist

- [ ] `sorted-mark-final.svg` — Primary mark
- [ ] `sorted-wordmark-horizontal.svg` — Mark + "sorted"
- [ ] `sorted-wordmark-full.svg` — Mark + "sorted.fund"
- [ ] `sorted-favicon.svg` — Mark only, optimized for 16-32px
- [ ] `sorted-og-image.png` — 1200×630 for social sharing

---

*Utility Sublime: The beauty of things that disappear into function.*
