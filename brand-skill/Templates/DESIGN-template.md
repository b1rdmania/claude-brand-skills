# [Brand Name]: Design System

> **The complete visual and strategic reference for [Brand]**
>
> This document contains everything needed to understand, build, and maintain the [Brand] identity — from emotional essence to implementation details.

<!-- TEMPLATE NOTE: All color hex values in this document are semantic placeholders
     (e.g. {BG_DEEP}, {TEXT_PRIMARY}, {GREEN}, {BRAND_ACCENT}).
     Replace every {PLACEHOLDER} with the brand's actual hex values from Phase 5. -->

---

## Table of Contents

1. [Emotive Narrative](#1-emotive-narrative)
2. [Strategic Foundation](#2-strategic-foundation)
3. [Visual Philosophy](#3-visual-philosophy)
4. [Logo System](#4-logo-system)
5. [Design Tokens](#5-design-tokens)
6. [Components](#6-components)
7. [Implementation Guidelines](#7-implementation-guidelines)
8. [Anti-AI-Slop Principles](#8-anti-ai-slop-principles)
9. [Quick Reference](#quick-reference)

---

## 1. Emotive Narrative

### The Human Moment

[Opening scene that illustrates the need — visceral and specific]

### The Deeper Truth

[What this moment reveals about the human condition or state of things]

### The Transformation

[What becomes possible when this project exists — focus on human change]

### The Ethos

[The values and principles that guide this]

### The Personality

[How this project moves through the world — voice and energy]

### The North Star

[The guiding light for hard decisions]

---

## 2. Strategic Foundation

### Positioning

[Brand] is [what] for [who], delivering [benefit]. Unlike [alternative], we [unique approach].

**Target Audience:** [Who this is for, specifically]

**Primary Use Case:** [The main problem/need this addresses]

### Core Metaphor

[The organizing idea that guides everything — e.g., "invisible infrastructure," "lens for clarity," "quiet confidence"]

**Why this metaphor:**
[Explain how it captures the essence]

### Brand Personality

- **[Trait]:** [Why this matters, evidence from the project]
- **[Trait]:** [Reasoning and manifestation]
- **[Trait]:** [Reasoning and manifestation]
- **[Trait]:** [Reasoning and manifestation]
- **[Trait]:** [Reasoning and manifestation]

### Voice & Tone

**How [Brand] speaks:**

- [Principle with explanation]
- [Principle with explanation]
- [Principle with explanation]

**Language we use:**
- [Term] — [why/when]
- [Term] — [why/when]
- [Term] — [why/when]

**Language we avoid:**
- [Generic term] — [why it doesn't fit]
- [Problematic term] — [why it doesn't fit]
- [Buzzword] — [why it doesn't fit]

**Example phrases:**

✅ Good:
- "[Example that captures the voice]"
- "[Example showing the tone]"
- "[Example of key messaging]"

❌ Avoid:
- "[Generic marketing speak]" — [Why this doesn't fit our voice]
- "[Overly technical jargon]" — [Why this alienates users]
- "[Hype-driven claim]" — [Why this breaks trust]

### Key Messages

**Tagline:** [Concise brand promise]

**Value Proposition:** [The core benefit in one sentence]

**Elevator Pitch:** [30-second explanation of what this is and why it matters]

---

## 3. Visual Philosophy: [Movement Name]

> "[One-sentence essence of the aesthetic]"

### The Philosophy

[4-6 paragraphs articulating the visual worldview — how form, space, color, composition express the brand's essence]

**Paragraph 1:** [Space and form treatment]

**Paragraph 2:** [Color approach and meaning]

**Paragraph 3:** [Typography and information density]

**Paragraph 4:** [Material quality and texture]

**Paragraph 5:** [Rhythm and composition]

**Paragraph 6:** [The overall experience]

### Core Design Principles

1. **[Principle Name]** — [What it means in practice]
2. **[Principle Name]** — [Explanation and application]
3. **[Principle Name]** — [Explanation and application]
4. **[Principle Name]** — [Explanation and application]
5. **[Principle Name]** — [Explanation and application]

### Aesthetic References

This visual language draws from:

- **[Movement/Designer]** — [What we're borrowing: color/form/attitude]
- **[Movement/Designer]** — [The specific influence]
- **[Movement/Designer]** — [How it manifests in our work]
- **[Movement/Designer]** — [The connection]

### What This IS

- [Characteristic] — [How it appears]
- [Characteristic] — [Manifestation]
- [Characteristic] — [Expression]
- [Characteristic] — [Implementation]

### What This ISN'T

- [Anti-pattern] — [Why we avoid this]
- [Anti-pattern] — [What we do instead]
- [Anti-pattern] — [The principle behind the avoidance]

---

## 4. Logo System

### The Mark

[Description of what the mark represents — meaning, symbolism, connection to brand essence]

**Visual elements:**
- [Element]: [What it represents]
- [Element]: [Meaning]
- [Colors]: [Symbolism]

**Files:**
- `[brand]-mark-final.svg` — Primary mark (scalable)
- `[brand]-favicon-32.png` — 32px favicon
- `[brand]-favicon-16.png` — 16px favicon

**Minimum sizes:**
- **Web:** 24px height minimum
- **Print:** 0.5 inch height minimum
- **Never smaller** — below minimum the mark loses clarity

### Wordmarks

#### Horizontal Lockup
**Usage:** Headers, navigation, wide formats
**File:** `[brand]-wordmark-horizontal.svg`

[Visual example or description]

#### Stacked Lockup
**Usage:** Square formats, app icons, social avatars
**File:** `[brand]-wordmark-stacked.svg`

[Visual example or description]

#### Text-Only
**Usage:** Inline references, footer, compact spaces
**File:** `[brand]-wordmark-textonly.svg`

[Visual example or description]

### Clear Space

Maintain clear space equal to [X] around all sides of the mark.

**Rule:** No text, graphics, or other elements within this zone.

[Diagram showing clearance zones]

### Color Variations

**Full Color:** Primary usage on light/dark backgrounds
**Monochrome:** When color isn't available
**White on Dark:** For dark backgrounds (#FFFFFF)
**Dark on Light:** For light backgrounds ([brand dark color])

### Usage Guidelines

**Do:**
- ✅ Use on backgrounds with sufficient contrast (4.5:1 minimum)
- ✅ Maintain proportions when scaling
- ✅ Use provided SVG files for sharpness
- ✅ Center-align the mark in layouts when appropriate

**Don't:**
- ❌ Rotate or distort the mark
- ❌ Change colors outside provided variations
- ❌ Add effects (shadows, outlines, gradients, glows)
- ❌ Place on busy or patterned backgrounds
- ❌ Stretch horizontally or vertically
- ❌ Recreate or trace the mark

---

## 5. Design Tokens

### 5.1 Colors

#### Web (CSS Variables)

```css
:root {
  /* Backgrounds */
  --bg-deep:     #[hex];     /* Main background */
  --bg-warm:     #[hex];     /* Cards, elevated surfaces */
  --bg-surface:  #[hex];     /* Inputs, wells, recessed areas */
  --bg-elevated: #[hex];     /* Hover states, overlays */

  /* Text */
  --text-primary:   #[hex];  /* Headings, important text */
  --text-secondary: #[hex];  /* Body copy, descriptions */
  --text-muted:     #[hex];  /* Labels, hints, de-emphasized */
  --text-whisper:   #[hex];  /* Disabled states */

  /* Borders */
  --border:       #[hex];    /* Default borders */
  --border-light: #[hex];    /* Emphasized borders */

  /* Functional */
  --green:      #[hex];      /* Success, active, healthy, CTAs */
  --green-dim:  #[hex];      /* Green hover/secondary */
  --green-dark: #[hex];      /* Green backgrounds */
  --amber:      #[hex];      /* Warnings, pending states */
  --red:        #[hex];      /* Errors, critical states */
  --blue:       #[hex];      /* Links, info (use sparingly) */

  /* Brand Accents */
  --accent:     #[hex];      /* Brand accent color */
  --accent-dim: #[hex];      /* Accent hover/secondary */
}
```

**Color Meanings:**

| Color | Hex | Meaning | Usage |
|-------|-----|---------|-------|
| **Green** | `#[hex]` | Success, Go, Active | CTAs, success states, health indicators — functional, not decorative |
| **Amber** | `#[hex]` | Warning, Pending | Caution states, pending operations, things needing attention |
| **Red** | `#[hex]` | Error, Stop, Critical | Error states, destructive actions, critical warnings |
| **Blue** | `#[hex]` | Info, Links | Informational elements, hyperlinks (use sparingly) |
| **Accent** | `#[hex]` | Brand moment | Strategic brand emphasis, premium elements |

**Light Mode:**

```css
@media (prefers-color-scheme: light) {
    :root {
        /* Backgrounds — step DOWN in lightness (opposite of dark mode) */
        --bg-deep:     #[hex];     /* White or warm off-white */
        --bg-warm:     #[hex];     /* Light gray with brand warmth */
        --bg-surface:  #[hex];     /* Slightly darker — inputs, wells */
        --bg-elevated: #[hex];     /* Lightest gray — hovers */

        /* Text — preserve warmth (not pure #000) */
        --text-primary:   #[hex];  /* Near-black */
        --text-secondary: #[hex];  /* Medium gray */
        --text-muted:     #[hex];  /* Light gray */
        --text-whisper:   #[hex];  /* Very light gray */

        /* Borders */
        --border:       #[hex];
        --border-light: #[hex];

        /* Functional — adjusted for white backgrounds */
        --green:      #[hex];
        --green-dim:  #[hex];
        --green-dark: #[hex];      /* Light tint for green backgrounds */
        --amber:      #[hex];
        --red:        #[hex];
        --blue:       #[hex];

        /* Accents */
        --accent:     #[hex];
        --accent-dim: #[hex];
    }
}
```

**Contrast Validation:**

| Text Color | Background | Ratio | AA Body (4.5:1) | AA Large (3:1) |
|-----------|-----------|-------|-----------------|----------------|
| text-primary (`#[hex]`) | bg-deep (`#[hex]`) | X:1 | PASS/FAIL | PASS/FAIL |
| text-primary (`#[hex]`) | bg-warm (`#[hex]`) | X:1 | PASS/FAIL | PASS/FAIL |
| text-secondary (`#[hex]`) | bg-deep (`#[hex]`) | X:1 | PASS/FAIL | PASS/FAIL |
| text-secondary (`#[hex]`) | bg-warm (`#[hex]`) | X:1 | PASS/FAIL | PASS/FAIL |
| text-muted (`#[hex]`) | bg-deep (`#[hex]`) | X:1 | PASS/FAIL | PASS/FAIL |
| text-muted (`#[hex]`) | bg-warm (`#[hex]`) | X:1 | PASS/FAIL | PASS/FAIL |
| green (`#[hex]`) | bg-deep (`#[hex]`) | X:1 | PASS/FAIL | PASS/FAIL |
| accent (`#[hex]`) | bg-deep (`#[hex]`) | X:1 | PASS/FAIL | PASS/FAIL |

*Run this matrix for both dark mode and light mode tokens. All body text pairs must pass 4.5:1. Muted text used only at large sizes may pass at 3:1 — document this explicitly.*

**Principles:**
- Green = success/go (functional meaning, not decoration)
- Use color strategically (10-20% of elements, not everything)
- Warm backgrounds (never pure #000000)
- All text/background pairs validated for WCAG AA contrast

#### iOS (Swift + Asset Catalog)

```swift
// In Color+Extensions.swift
extension Color {
    // Backgrounds
    static let backgroundPrimary = Color("BackgroundPrimary")
    static let backgroundSecondary = Color("BackgroundSecondary")
    static let backgroundTertiary = Color("BackgroundTertiary")

    // Text
    static let textPrimary = Color("TextPrimary")
    static let textSecondary = Color("TextSecondary")
    static let textTertiary = Color("TextTertiary")

    // System/Functional
    static let success = Color("Success")  // #[hex]
    static let warning = Color("Warning")  // #[hex]
    static let error = Color("Error")      // #[hex]

    // Brand
    static let brandPrimary = Color("BrandPrimary")
    static let brandAccent = Color("BrandAccent")
}
```

**Asset Catalog Setup:**

Each color has light/dark variants:

| Color | Dark Mode | Light Mode |
|-------|-----------|------------|
| BackgroundPrimary | `#[hex]` | `#[hex]` |
| BackgroundSecondary | `#[hex]` | `#[hex]` |
| BackgroundTertiary | `#[hex]` | `#[hex]` |
| TextPrimary | `#[hex]` | `#[hex]` |
| TextSecondary | `#[hex]` | `#[hex]` |
| TextTertiary | `#[hex]` | `#[hex]` |
| Success | `#[hex]` | `#[hex]` |
| Warning | `#[hex]` | `#[hex]` |
| Error | `#[hex]` | `#[hex]` |
| BrandPrimary | `#[hex]` | `#[hex]` |
| BrandAccent | `#[hex]` | `#[hex]` |

---

### 5.2 Typography

#### Web Typography

**Font Stack:**
```css
--font-sans: '[Primary Font]', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
--font-mono: '[Mono Font]', 'SF Mono', 'Fira Code', 'Courier New', monospace;
```

**Type Scale:**

| Token | Size | Weight | Line Height | Letter Spacing | Usage |
|-------|------|--------|-------------|----------------|-------|
| `display` | 48px | 500 | 1.1 | -0.02em | Hero headlines, major impact |
| `h1` | 32px | 500 | 1.2 | -0.01em | Page titles |
| `h2` | 24px | 500 | 1.3 | 0 | Section headers |
| `h3` | 18px | 500 | 1.4 | 0 | Subsection headers, card titles |
| `body` | 15px | 400 | 1.6 | 0 | Body copy, paragraphs |
| `body-small` | 14px | 400 | 1.5 | 0 | Secondary text, captions |
| `caption` | 12px | 400 | 1.4 | 0 | Labels, hints, metadata |
| `mono` | 14px | 400 | 1.5 | 0 | Code, data, technical content |

**Label Style:**
```css
.label {
  font-size: 11-12px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--text-muted);
}
```

#### iOS Typography

**System Fonts (Native):**
```swift
struct Typography {
    // Display
    static let largeTitle = Font.system(.largeTitle, design: .default, weight: .bold)      // 34pt
    static let title = Font.system(.title, design: .default, weight: .semibold)             // 28pt
    static let title2 = Font.system(.title2, design: .default, weight: .semibold)           // 22pt
    static let title3 = Font.system(.title3, design: .default, weight: .semibold)           // 20pt

    // Body
    static let headline = Font.system(.headline, design: .default, weight: .semibold)       // 17pt
    static let body = Font.system(.body, design: .default, weight: .regular)                // 17pt
    static let callout = Font.system(.callout, design: .default, weight: .regular)          // 16pt
    static let subheadline = Font.system(.subheadline, design: .default, weight: .regular)  // 15pt

    // Small
    static let footnote = Font.system(.footnote, design: .default, weight: .regular)        // 13pt
    static let caption = Font.system(.caption, design: .default, weight: .regular)          // 12pt
    static let caption2 = Font.system(.caption2, design: .default, weight: .regular)        // 11pt

    // Specialty
    static let monoBody = Font.system(.body, design: .monospaced)
    static let monoCaption = Font.system(.caption, design: .monospaced)
}
```

**Custom Fonts (if needed):**
```swift
// If using custom fonts like Inter
Font.custom("Inter", size: 17, relativeTo: .body)
Font.custom("Inter", size: 28, relativeTo: .title).weight(.semibold)
```

**Dynamic Type Support:**
```swift
Text("Content")
    .font(.body)
    .dynamicTypeSize(.medium...(.accessibility3))  // Limit range if needed
```

---

### 5.3 Spacing

**Base Unit:** 8px (web) / 8pt (iOS)

**Scale:**

| Token | Web | iOS | Usage |
|-------|-----|-----|-------|
| `xs` | 4px | 4pt | Tight inline spacing, icon gaps |
| `sm` | 8px | 8pt | Related elements, list item spacing |
| `md` | 16px | 16pt | Default padding, comfortable spacing |
| `lg` | 24px | 24pt | Section gaps, card spacing |
| `xl` | 32px | 32pt | Major section separation |
| `2xl` | 48px | 48pt | Page-level sections |
| `3xl` | 64px | 64pt | Hero spacing, large whitespace |

**CSS Variables:**
```css
:root {
  --space-xs: 4px;
  --space-sm: 8px;
  --space-md: 16px;
  --space-lg: 24px;
  --space-xl: 32px;
  --space-2xl: 48px;
  --space-3xl: 64px;
}
```

**Swift Struct:**
```swift
struct Spacing {
    static let xs: CGFloat = 4
    static let sm: CGFloat = 8
    static let md: CGFloat = 16
    static let lg: CGFloat = 24
    static let xl: CGFloat = 32
    static let xxl: CGFloat = 48
    static let xxxl: CGFloat = 64
}
```

**Component Padding:**

| Component | Web | iOS |
|-----------|-----|-----|
| Buttons | `12px 20px` | `12pt vertical, 20pt horizontal` |
| Inputs | `12px 16px` | `16pt all sides` |
| Cards | `20px 24px` | `20pt all sides` |
| Modals/Sheets | `24px 32px` | `24pt all sides` |

---

### 5.4 Radii

**Consistent rounding:**

| Token | Value | Usage |
|-------|-------|-------|
| `sm` | 4px/pt | Small elements, tags |
| `md` | 6px/pt | Buttons, inputs |
| `lg` | 8px/pt | Cards, containers |
| `xl` | 12px/pt | Large cards, modals |
| `full` | `9999px` | Pills, circular elements |

---

### 5.5 Shadows (Web Only)

**Elevation system:**

```css
--shadow-sm:  0 1px 2px rgba(0,0,0,0.1);
--shadow-md:  0 4px 6px rgba(0,0,0,0.15);
--shadow-lg:  0 10px 15px rgba(0,0,0,0.2);
--shadow-xl:  0 20px 25px rgba(0,0,0,0.25);
```

**Usage:**
- Use sparingly (not every card)
- Indicate elevation/hierarchy
- Subtle in dark mode

**iOS Note:** Use native `.shadow()` modifier minimally — iOS prefers flat design

---

## 6. Components

### 6.1 Buttons

#### Web

**Primary Button:**
```css
.button-primary {
  background: var(--green);
  color: var(--bg-deep);
  font-weight: 500;
  font-size: 15px;
  padding: 12px 20px;
  border-radius: 6px;
  border: none;
  cursor: pointer;
  transition: all 200ms ease-out;
}

.button-primary:hover {
  background: var(--green-dim);
}

.button-primary:active {
  transform: scale(0.98);
}

.button-primary:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
```

**Secondary Button:**
```css
.button-secondary {
  background: transparent;
  border: 1px solid var(--border);
  color: var(--text-primary);
  font-weight: 500;
  padding: 12px 20px;
  border-radius: 6px;
  transition: all 200ms ease-out;
}

.button-secondary:hover {
  border-color: var(--border-light);
  background: var(--bg-surface);
}
```

**Ghost Button:**
```css
.button-ghost {
  background: transparent;
  border: none;
  color: var(--text-secondary);
  padding: 12px 20px;
}

.button-ghost:hover {
  color: var(--text-primary);
}
```

#### iOS

```swift
// Primary Button Style
struct PrimaryButtonStyle: ButtonStyle {
    @Environment(\.isEnabled) var isEnabled

    func makeBody(configuration: Configuration) -> some View {
        configuration.label
            .font(.headline)
            .foregroundColor(Color("BackgroundPrimary"))
            .padding(.horizontal, 20)
            .padding(.vertical, 12)
            .background(isEnabled ? Color("Success") : Color("Success").opacity(0.5))
            .cornerRadius(8)
            .scaleEffect(configuration.isPressed ? 0.98 : 1.0)
    }
}

// Secondary Button Style
struct SecondaryButtonStyle: ButtonStyle {
    func makeBody(configuration: Configuration) -> some View {
        configuration.label
            .font(.headline)
            .foregroundColor(Color("TextPrimary"))
            .padding(.horizontal, 20)
            .padding(.vertical, 12)
            .background(Color.clear)
            .overlay(
                RoundedRectangle(cornerRadius: 8)
                    .stroke(Color("TextTertiary"), lineWidth: 1)
            )
            .opacity(configuration.isPressed ? 0.7 : 1.0)
    }
}

// Usage
Button("Primary Action") { }
    .buttonStyle(PrimaryButtonStyle())

Button("Secondary Action") { }
    .buttonStyle(SecondaryButtonStyle())
```

---

### 6.2 Inputs

#### Web

**Text Input:**
```css
.input {
  background: var(--bg-surface);
  border: 1px solid var(--border);
  color: var(--text-primary);
  font-family: var(--font-sans);
  font-size: 15px;
  padding: 12px 16px;
  border-radius: 6px;
  width: 100%;
  transition: border-color 200ms ease;
}

.input:focus {
  border-color: var(--green);
  outline: none;
}

.input::placeholder {
  color: var(--text-muted);
}

.input:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
```

**Textarea:**
```css
.textarea {
  /* Same as .input */
  min-height: 120px;
  resize: vertical;
  font-family: var(--font-sans);
  line-height: 1.6;
}
```

#### iOS

```swift
// Custom TextField Style
struct CustomTextFieldStyle: TextFieldStyle {
    func _body(configuration: TextField<Self._Label>) -> some View {
        configuration
            .padding(16)
            .background(Color("BackgroundSecondary"))
            .cornerRadius(8)
            .overlay(
                RoundedRectangle(cornerRadius: 8)
                    .stroke(Color("TextTertiary").opacity(0.3), lineWidth: 1)
            )
    }
}

// Usage
TextField("Placeholder", text: $text)
    .textFieldStyle(CustomTextFieldStyle())

// TextEditor (multiline)
TextEditor(text: $text)
    .padding(16)
    .frame(minHeight: 120)
    .background(Color("BackgroundSecondary"))
    .cornerRadius(8)
```

---

### 6.3 Cards

#### Web

```css
.card {
  background: var(--bg-warm);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 20px 24px;
  transition: border-color 200ms ease;
}

.card:hover {
  border-color: var(--border-light);
}

.card-clickable {
  cursor: pointer;
}

.card-clickable:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-md);
}
```

#### iOS

```swift
struct Card<Content: View>: View {
    let content: Content

    init(@ViewBuilder content: () -> Content) {
        self.content = content()
    }

    var body: some View {
        VStack(alignment: .leading, spacing: Spacing.md) {
            content
        }
        .padding(20)
        .background(Color("BackgroundSecondary"))
        .cornerRadius(12)
        .shadow(color: Color.black.opacity(0.1), radius: 10, y: 4)
    }
}

// Usage
Card {
    Text("Title")
        .font(.headline)
    Text("Description")
        .font(.body)
        .foregroundColor(Color("TextSecondary"))
}
```

---

### 6.4 Status Indicators

#### Web

```css
.status-indicator {
  width: 8px;
  height: 8px;
  border-radius: 50%;
}

.status-active { background: var(--green); }
.status-warning { background: var(--amber); }
.status-error { background: var(--red); }
.status-inactive { background: var(--text-muted); }
```

```html
<div class="status-indicator status-active"></div>
```

#### iOS

```swift
struct StatusIndicator: View {
    enum Status {
        case active, warning, error, inactive
    }

    let status: Status

    var color: Color {
        switch status {
        case .active: return Color("Success")
        case .warning: return Color("Warning")
        case .error: return Color("Error")
        case .inactive: return Color("TextTertiary")
        }
    }

    var body: some View {
        Circle()
            .fill(color)
            .frame(width: 8, height: 8)
    }
}

// Usage
StatusIndicator(status: .active)
```

---

[Continue with additional components: modals, lists, navigation, etc.]

---

## 7. Implementation Guidelines

### 7.1 Web Implementation

#### Responsive Breakpoints

```css
/* Mobile first approach */
.element {
  /* Mobile styles (base) */
}

@media (min-width: 640px) {
  /* sm - small tablets */
}

@media (min-width: 768px) {
  /* md - tablets */
}

@media (min-width: 1024px) {
  /* lg - laptops */
}

@media (min-width: 1280px) {
  /* xl - desktops */
}

@media (min-width: 1536px) {
  /* 2xl - large desktops */
}
```

#### Dark/Light Mode

```css
/* Default (dark mode) — replace placeholders with brand-specific hex values */
:root {
  --bg-deep: {BG_DEEP};
  --text-primary: {TEXT_PRIMARY};
  /* ... all dark mode tokens from Section 5.1 */
}

/* Light mode override — full token set, not abbreviated */
@media (prefers-color-scheme: light) {
  :root {
    --bg-deep: #[hex];          /* White or warm off-white */
    --bg-warm: #[hex];          /* Light gray with brand warmth */
    --bg-surface: #[hex];       /* Slightly darker */
    --bg-elevated: #[hex];      /* Lightest gray */
    --text-primary: #[hex];     /* Near-black with warmth */
    --text-secondary: #[hex];
    --text-muted: #[hex];
    --text-whisper: #[hex];
    --border: #[hex];
    --border-light: #[hex];
    --green: #[hex];            /* May need adjustment for white backgrounds */
    --green-dim: #[hex];
    --amber: #[hex];
    --red: #[hex];
    --accent: #[hex];
    --accent-dim: #[hex];
  }
}
```

**Every token must have a light mode value.** Do not use `/* ... */` — incomplete light mode is a common failure point.

#### Focus States

```css
/* Remove default outline */
:focus {
  outline: none;
}

/* Custom focus ring for keyboard navigation */
:focus-visible {
  outline: 2px solid var(--green);
  outline-offset: 2px;
  border-radius: 4px;
}
```

#### Performance

```css
/* Animate only transform and opacity (GPU accelerated) */
.element {
  transition: transform 200ms ease-out, opacity 200ms ease-out;
}

/* Avoid animating: width, height, top, left, margin, padding */

/* Use will-change sparingly */
.element-that-animates-frequently {
  will-change: transform;
}
```

#### iOS Safari Safe Areas

Fixed navigation bars on iOS Safari will overlap the status bar and Dynamic Island unless safe-area insets are explicitly handled. This is a common failure point.

**Viewport meta tag (required):**
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
```

**Fixed nav with safe-area awareness:**
```css
nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  padding-top: max(1.5rem, env(safe-area-inset-top));
  padding-left: max(var(--pad-x), env(safe-area-inset-left));
  padding-right: max(var(--pad-x), env(safe-area-inset-right));
}
```

**CRITICAL: CSS shorthand `padding:` overrides `padding-top:`.**
If the nav has state changes (`.scrolled`, `.compact`) that use shorthand `padding:`, re-declare the safe-area properties after:

```css
/* Shorthand kills the base safe-area padding-top — re-declare it */
nav.scrolled {
  padding: 0.75rem var(--pad-x);
  padding-top: calc(0.75rem + env(safe-area-inset-top, 0px));
}
```

**Bottom safe area for fixed footers:**
```css
.bottom-bar {
  position: fixed;
  bottom: 0;
  padding-bottom: max(1rem, env(safe-area-inset-bottom));
}
```

**iOS backdrop blur:**
```css
nav {
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);  /* Required for iOS Safari */
}
```

---

### 7.2 iOS Implementation

#### Navigation Patterns

```swift
// Standard Navigation
NavigationView {
    ContentView()
        .navigationTitle("Title")
        .navigationBarTitleDisplayMode(.large)
}

// Navigation with toolbar
NavigationView {
    ContentView()
        .toolbar {
            ToolbarItem(placement: .navigationBarTrailing) {
                Button("Action") { }
            }
        }
}
```

#### System Integration

```swift
// Respect color scheme
@Environment(\.colorScheme) var colorScheme

if colorScheme == .dark {
    // Dark mode specific
}

// Support Dynamic Type
@Environment(\.sizeCategory) var sizeCategory

Text("Content")
    .font(.body)
    .dynamicTypeSize(.medium...(.accessibility3))

// Haptic feedback
let generator = UIImpactFeedbackGenerator(style: .medium)
generator.impactOccurred()

// Share sheet
.sheet(isPresented: $showShare) {
    ShareSheet(items: [shareContent])
}
```

#### Safe Areas

```swift
VStack {
    // Content
}
.padding(.horizontal, Spacing.md)
.safeAreaInset(edge: .bottom) {
    // Bottom bar that respects home indicator
    BottomBar()
}
.ignoresSafeArea(.keyboard)  // When keyboard should push content
```

#### Lists

```swift
// Use native list styles
List {
    Section("Header") {
        ForEach(items) { item in
            ItemRow(item: item)
        }
    }
}
.listStyle(.insetGrouped)  // Most common

// Or custom ScrollView for more control
ScrollView {
    LazyVStack(spacing: Spacing.md) {
        ForEach(items) { item in
            ItemRow(item: item)
        }
    }
    .padding()
}
```

---

### 7.3 Cross-Platform Consistency

**Aim for similar feel, not pixel-perfect matching.**

| Aspect | Web | iOS |
|--------|-----|-----|
| **Colors** | Identical hex values | Identical hex (in Asset Catalog) |
| **Spacing** | 8px base | 8pt base |
| **Typography** | Custom fonts OK | Prefer system fonts |
| **Shadows** | Use liberally | Use sparingly |
| **Navigation** | Custom nav | Use NavigationView |
| **Animations** | CSS transitions | SwiftUI animations |

**Platform Philosophy:**
- Web can be more expressive (gradients, shadows, custom animations)
- iOS should feel native (system fonts, native navigation, platform conventions)
- Both should feel like "the same brand" but appropriate to their platform

---

## 8. Anti-AI-Slop Principles

> **This brand exists to avoid generic, soulless design. Every decision should be intentional, connected to the emotive narrative, and distinctively [Brand].**

### Core Principles

#### 1. No Generic Patterns

❌ **Avoid:**
- Purple-to-blue gradients without narrative reason
- Overly rounded shapes everywhere (30px+ border-radius on everything)
- Random "clean and modern" aesthetics
- Copy-paste from Dribbble without adaptation
- Following trends instead of brand philosophy

✅ **Instead:**
- Every gradient must serve the visual philosophy
- Border-radius follows system (4, 6, 8, 12px)
- "Clean and modern" is never enough — what ELSE is it?
- Learn from references but create something distinctive
- Follow the emotive narrative, not trends

#### 2. Color Carries Meaning

❌ **Avoid:**
- Coloring everything for "visual interest"
- Using success/warning/error colors decoratively
- Random accent colors not in the system
- Gradients everywhere without purpose

✅ **Instead:**
- Green = go/success, Red = stop/error, Amber = caution
- Strategic color use (10-20% of elements get color)
- Every color in the system has a name and purpose
- Gradients only if the visual philosophy calls for them

#### 3. Craftsmanship Markers

❌ **Avoid:**
- Arbitrary border-radius values (17px, 23px, etc.)
- Random spacing that breaks 8px grid
- Orphaned colors not in design system
- Inconsistent rounding across components

✅ **Instead:**
- Consistent rounding: 4, 6, 8, 12px (or from your system)
- All spacing from defined scale (4, 8, 16, 24, 32, 48px)
- Every color is named and in the system
- Pattern consistency proves intentionality

#### 4. Typography with Personality

❌ **Avoid:**
- "Clean sans-serif" with no character
- Body copy too small to read (<14px)
- All-caps everywhere
- Random font weights not in scale

✅ **Instead:**
- Font choices reflect brand personality
- Readable sizes (15-16px body minimum)
- Clear hierarchy through scale, not just size
- Consistent weights (400, 500, 600 — not random)

#### 5. Distinctive, Not Derivative

❌ **Avoid:**
- Copying Stripe/Linear/Vercel verbatim
- Following Tailwind UI defaults without customization
- "Inspired by" that's really "copied from"
- Every site looking like every other site

✅ **Instead:**
- Learn from references but synthesize into something new
- Customize component libraries to match brand
- Visual language specific to [Brand]
- Could this ONLY be [Brand]? If not, it's too generic

### Decision Testing Framework

**Before implementing any design element, ask:**

1. **Narrative Test**
   > "Does this express our emotive narrative?"
   > If you can't connect it back to Section 1, it's arbitrary.

2. **Meaning Test**
   > "Why this color/size/spacing and not another?"
   > If the answer is "it looks nice," find the real reason.

3. **Distinctive Test**
   > "Could this only be [Brand], or any modern app?"
   > If it's interchangeable, it's generic.

4. **Platform Test**
   > "Does this feel native to web/iOS?"
   > Fighting platform conventions creates friction.

5. **Craft Test**
   > "Does this look like expert work or default settings?"
   > Details matter: alignment, spacing, consistency.

**If you can't answer these, the choice is arbitrary. Revise.**

### Validation Checklist

**Before considering design work complete:**

#### Visual Cohesion
- [ ] Every color in use is in the design system
- [ ] All spacing values are from the defined scale
- [ ] Border radius is consistent (not random values)
- [ ] Typography uses defined scale (not arbitrary sizes)
- [ ] Shadows follow elevation system (if used)

#### Brand Expression
- [ ] Reflects the emotive narrative (testable)
- [ ] Embodies the visual philosophy
- [ ] Feels distinctively [Brand]
- [ ] Not interchangeable with competitors

#### Platform Quality
- [ ] Web design uses modern CSS appropriately
- [ ] iOS design feels native (not web-in-webview)
- [ ] Components work across screen sizes
- [ ] Touch targets meet platform guidelines (44pt iOS)
- [ ] Focus states work for keyboard navigation (web)

#### Craftsmanship
- [ ] No elements overlap unintentionally
- [ ] Perfect alignment on grid
- [ ] Consistent visual weight and rhythm
- [ ] Looks like expert-level work
- [ ] Every detail refined

**If any checkbox fails, revise before shipping.**

### Red Flags

**Stop immediately if you see:**

🚩 Random gradients added "for visual interest"
🚩 Spacing that doesn't follow 8px rhythm
🚩 Colors not in the design system
🚩 "Clean and modern" as the only descriptor
🚩 Copy-paste from component library without customization
🚩 Decisions made "because it looks good" without reasoning
🚩 Border-radius values like 17px, 23px, 37px (arbitrary)
🚩 All-caps text everywhere
🚩 Body text smaller than 14px
🚩 Every surface has a drop shadow

### Remember

**Generic is easy. Distinctive takes intention.**

Every design choice should be:
1. **Intentional** — chosen for a reason
2. **Systematic** — part of a coherent system
3. **Meaningful** — connected to brand narrative
4. **Crafted** — refined to expert level

This is how you avoid AI slop.

---

## Quick Reference

### Colors (Web)
```css
--bg-deep: #[hex];  --text-primary: #[hex];  --green: #[hex];
```

### Spacing
`4, 8, 16, 24, 32, 48, 64px`

### Typography
**Web:** [Font Name] (UI), [Mono Font] (code)
**iOS:** SF Pro (system fonts preferred)

### Border Radius
`4, 6, 8, 12px` (consistent, not random)

### Key Principle
[One sentence from the North Star]

### Design Testing Question
> "Does this express our emotive narrative and feel distinctively [Brand]?"

---

**Last Updated:** [Date]
**Version:** 1.0
**Maintained By:** [Team/Person]

---

*This is a living document. Update as the design system evolves. Every change should maintain coherence with the emotive narrative.*
