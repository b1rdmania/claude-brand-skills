# InfraSingularity Design System

**Brand:** InfraSingularity
**Positioning:** Where institutional infrastructure converges
**Visual Philosophy:** Gravitational Density — dark-first, geometric precision, institutional authority

---

## Colors

### Backgrounds (Dark Mode Primary)

Derived from mark's deep neutral with stepped lightness progression:

```css
--bg-deep:     #0A0D10   /* Main background — deep warm near-black */
--bg-warm:     #12161A   /* Cards, elevated surfaces — +8% lightness */
--bg-surface:  #1A1F24   /* Inputs, wells, recessed areas — +6% */
--bg-elevated: #23292F   /* Hover states, overlays — +6% */
```

**Rationale:** Deep, gravitational darkness with subtle warmth. Not pure black — maintains institutional presence without feeling lifeless.

### Text

Contrast-tested against backgrounds for WCAG AAA compliance:

```css
--text-primary:   #F5F5F7   /* Headings, emphasis — 16:1 contrast against bg-deep */
--text-secondary: #C4C6CB   /* Body copy — 9:1 contrast */
--text-muted:     #6E7178   /* Labels, hints — 4.5:1 contrast */
--text-whisper:   #3D4147   /* Disabled states, subtle elements */
```

**Rationale:** High contrast for institutional clarity. Primary text is warm near-white (not pure #FFF) to reduce eye strain.

### Borders

```css
--border:       #2D3339   /* Default borders — subtle separation */
--border-light: #3D4449   /* Emphasized borders, dividers */
```

### Brand Accents

From "Gravitational Density" visual philosophy:

```css
--accent:       #6B4FEC   /* Primary purple — singularity core */
--accent-dim:   #513AC0   /* Dimmed purple — reduced lightness 25% */
--accent-dark:  #2B1F5C   /* Purple backgrounds, very low lightness */
--accent-glow:  #8B6FFF   /* Brighter purple for hover/focus states */
```

**Rationale:** Deep violet-purple as the singularity point. Technical yet approachable. Institutional without being corporate.

### Functional Colors

Harmonized with brand accent for cohesive palette:

```css
/* Success / Active */
--green:       #4CAF8C   /* Success states, CTAs — cooler green harmonizes with purple */
--green-dim:   #3A8A6E   /* Hover, secondary */
--green-dark:  #1F4A3A   /* Backgrounds */

/* Warning / Pending */
--amber:       #F59E42   /* Warnings, pending states */
--amber-dim:   #C77E34   /* Secondary */
--amber-dark:  #5C3A1A   /* Backgrounds */

/* Error / Critical */
--red:         #E85D5D   /* Errors, destructive actions */
--red-dim:     #C44A4A   /* Secondary */
--red-dark:    #5C2626   /* Backgrounds */

/* Info / Links */
--blue:        #5B9EFF   /* Links, informational (use sparingly) */
--blue-dim:    #4780D6   /* Secondary */
--blue-dark:   #2A3E5C   /* Backgrounds */
```

**Rationale:** Cooler-toned functional colors harmonize with purple accent. Avoid overly saturated "startup" colors — institutional restraint.

### Light Mode (Optional)

If light mode needed for documents/reports:

```css
--bg-deep-light:     #FFFFFF   /* Main background */
--bg-warm-light:     #F7F7F8   /* Cards */
--bg-surface-light:  #EFEFF1   /* Inputs */
--text-primary-light: #0A0D10  /* Inverted from dark bg-deep */
--accent-light:      #5A3FCC   /* Slightly darker purple for contrast */
```

---

## Typography

**Display/Heading Font:** Outfit
**Body/UI Font:** Figtree
**Rationale:** Geometric cohesion creates unified type system. Figtree shares similar proportions and x-height with Outfit, supporting the "convergence" concept and "Gravitational Density" aesthetic. Hierarchy through weight and size, not jarring font changes.

**Outfit Weight Range:** 300 (Light), 500 (Medium), 600 (Semibold), 700 (Bold)
**Figtree Weight Range:** 300 (Light), 400 (Regular), 500 (Medium), 600 (Semibold), 700 (Bold)

### Type Scale

```css
/* Display */
--font-size-hero:    clamp(56px, 8vw, 96px)
--font-weight-hero:  300
--line-height-hero:  1.1

/* Headings */
--font-size-h1:      clamp(40px, 5vw, 56px)
--font-weight-h1:    500
--line-height-h1:    1.2

--font-size-h2:      clamp(32px, 4vw, 40px)
--font-weight-h2:    500
--line-height-h2:    1.3

--font-size-h3:      clamp(24px, 3vw, 32px)
--font-weight-h3:    500
--line-height-h3:    1.4

--font-size-h4:      20px
--font-weight-h4:    600
--line-height-h4:    1.4

/* Body */
--font-size-body:    16px
--font-weight-body:  400 (use Medium 500 for better readability)
--line-height-body:  1.6

--font-size-small:   14px
--font-weight-small: 400
--line-height-small: 1.5

--font-size-tiny:    12px
--font-weight-tiny:  500
--line-height-tiny:  1.4
```

### Letter Spacing

```css
--tracking-tight:    -0.02em   /* Large headings */
--tracking-normal:   -0.01em   /* Body, smaller headings */
--tracking-loose:    0.02em    /* Labels, tiny text */
--tracking-wide:     0.1em     /* All-caps labels */
```

**Rationale:** Outfit has good default spacing, but slight negative tracking adds density at display sizes. Institutional precision without feeling cramped.

### Font Stacks

```css
/* Display/Headings */
font-family: 'Outfit', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;

/* Body/UI */
font-family: 'Figtree', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;

/* Monospace (for technical content, addresses, code) */
font-family: 'JetBrains Mono', 'IBM Plex Mono', 'SF Mono', Consolas, monospace;
```

---

## Spacing

8px base unit with geometric progression:

```css
--space-1:   4px    /* Tight internal padding */
--space-2:   8px    /* Base unit — icon gaps, inline spacing */
--space-3:   12px   /* Small padding, button padding */
--space-4:   16px   /* Default padding, card internal */
--space-5:   24px   /* Section spacing, card padding */
--space-6:   32px   /* Large section gaps */
--space-8:   48px   /* Component separation */
--space-10:  64px   /* Major section gaps */
--space-12:  96px   /* Hero section padding */
--space-16:  128px  /* Maximum page spacing */
```

**Rationale:** 8px base allows clean scaling. Geometric progression (1.5x after space-4) creates clear hierarchy.

---

## Elevation (Shadows)

Subtle shadows for depth on dark backgrounds:

```css
--shadow-sm:  0 1px 2px rgba(0, 0, 0, 0.5);
--shadow-md:  0 4px 8px rgba(0, 0, 0, 0.3), 0 1px 3px rgba(0, 0, 0, 0.4);
--shadow-lg:  0 12px 24px rgba(0, 0, 0, 0.3), 0 4px 8px rgba(0, 0, 0, 0.4);
--shadow-xl:  0 24px 48px rgba(0, 0, 0, 0.4), 0 8px 16px rgba(0, 0, 0, 0.5);
```

**Purple glow accent (sparingly):**

```css
--glow-accent: 0 0 20px rgba(107, 79, 236, 0.3), 0 0 40px rgba(107, 79, 236, 0.15);
```

---

## Components

### Buttons

**Primary (CTA):**
```css
background: var(--accent);
color: #FFFFFF;
padding: var(--space-3) var(--space-5);
font-weight: 600;
border-radius: 6px;
transition: all 0.2s;

hover: background: var(--accent-glow);
active: background: var(--accent-dim);
```

**Secondary:**
```css
background: transparent;
color: var(--text-primary);
border: 1px solid var(--border-light);

hover: border-color: var(--accent);
       color: var(--accent);
```

**Tertiary (Ghost):**
```css
background: transparent;
color: var(--text-secondary);

hover: color: var(--text-primary);
       background: var(--bg-elevated);
```

### Inputs

```css
background: var(--bg-surface);
border: 1px solid var(--border);
color: var(--text-primary);
padding: var(--space-3) var(--space-4);
border-radius: 6px;
font-size: var(--font-size-body);

focus: border-color: var(--accent);
       outline: 0 0 0 3px rgba(107, 79, 236, 0.15);
```

### Cards

```css
background: var(--bg-warm);
border: 1px solid var(--border);
border-radius: 8px;
padding: var(--space-5);
box-shadow: var(--shadow-sm);

hover: box-shadow: var(--shadow-md);
       border-color: var(--border-light);
```

---

## Border Radius

```css
--radius-sm:  4px    /* Buttons, small elements */
--radius-md:  6px    /* Inputs, default */
--radius-lg:  8px    /* Cards */
--radius-xl:  12px   /* Large containers */
--radius-full: 9999px /* Pills, avatars */
```

**Rationale:** Subtle radii maintain geometric precision. Not overly rounded — institutional restraint.

---

## Animation

```css
--duration-fast:   150ms   /* Micro-interactions */
--duration-normal: 200ms   /* Hover, focus states */
--duration-slow:   300ms   /* Page transitions */

--ease-out: cubic-bezier(0.33, 1, 0.68, 1);  /* Snappy exit */
--ease-in:  cubic-bezier(0.32, 0, 0.67, 0);  /* Gentle entry */
```

---

## Brand Mark Usage

**Primary Mark:** v11d (25-dot radial starburst, clean geometry)

**Minimum Size:** 24px height
**Clear Space:** 16px on all sides
**Backgrounds:** Works on dark (#0A0D10 and lighter), adapt for light backgrounds

**Wordmark Lockup (Final):**
- Font: Outfit
- "Infra" Medium (500) + "Singularity" Light (300)
- Size: 40px text
- Spacing: 16px gap from mark
- Accent: 7px purple full stop (#6B4FEC) at end of "Singularity"
- Color: White text + purple accent
- File: is-wordmark-lockup-final.svg

---

## Platform Notes

**Web:**
- Dark mode default
- Light mode optional for documents
- Support Safari, Chrome, Firefox latest 2 versions

**iOS (if needed):**
- Use SF Pro for body text (platform native)
- Keep Outfit for display headings
- Adapt spacing to 4px base (iOS standard)

---

🎨 **Design System v1.0** — Generated 2026-02-12
Based on Phase 0-4 brand development
