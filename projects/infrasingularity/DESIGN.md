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

### Dim Colour Borders (Phase 5.5)

Section-coded border system — functional colours at reduced opacity. Used as 2px borders on all content blocks.

```css
--border-accent: rgba(107, 79, 236, 0.35)   /* Purple — hero, infrastructure */
--border-green:  rgba(76, 175, 140, 0.30)   /* Green — protocols */
--border-amber:  rgba(245, 158, 66, 0.28)   /* Amber — the model */
--border-blue:   rgba(91, 158, 255, 0.28)   /* Blue — investments */
```

Matching background fills (3% tint):

```css
--fill-accent: rgba(107, 79, 236, 0.03)
--fill-green:  rgba(76, 175, 140, 0.03)
--fill-amber:  rgba(245, 158, 66, 0.03)
--fill-blue:   rgba(91, 158, 255, 0.03)
```

**Rationale:** Unifies visual language between splash page (full-saturation coloured borders on stat blocks) and main page (same colour system at ~30% opacity). Each content section is colour-coded without competing with the content.

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
border-radius: 0;
transition: all 0.2s;

hover: background: var(--accent-glow);
active: background: var(--accent-dim);
```

**Primary Amber (main CTA):**
```css
background: var(--amber);
color: #000000;
padding: var(--space-4) var(--space-10);
font-size: 14px;
font-weight: 600;
border-radius: 0;

hover: background: var(--amber-dim);
```

**Secondary:**
```css
background: transparent;
color: var(--text-secondary);
border: 1px solid var(--border-light);
border-radius: 0;

hover: border-color: var(--accent);
       color: var(--text-primary);
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
border-radius: 0;
font-size: var(--font-size-body);

focus: border-color: var(--accent);
       outline: 0 0 0 3px rgba(107, 79, 236, 0.15);
```

### Cards

```css
background: var(--fill-accent);   /* or fill-green/amber/blue per section */
border: 2px solid var(--border-accent);   /* dim colour border per section */
border-radius: 0;
padding: var(--space-5);

hover: border-color opacity +10%;
```

---

## Border Radius

**Web override (Phase 5.5 — brutalist direction):** `border-radius: 0` on all components. Hard edges throughout.

```css
/* Web */
--radius-sm:   0
--radius-md:   0
--radius-lg:   0
--radius-xl:   0
--radius-full: 9999px   /* Pills only — avatars, tags if needed */
```

**Non-web (documents, presentations):**
```css
--radius-sm:  4px
--radius-md:  6px
--radius-lg:  8px
--radius-xl:  12px
```

**Rationale:** Zero border-radius reinforces the institutional, geometric, dense aesthetic. Rounds are approachable — IS is precise. Brutalist hard edges align with the "Gravitational Density" visual philosophy.

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
- Color: White text
- File: is-wordmark-lockup-final.svg

---

## Web Composition Patterns (Phase 5.5)

### Section Header

```css
display: flex;
align-items: center;
gap: var(--space-5);
margin-bottom: var(--space-8);
```

```html
<div class="sh">
  <span class="sh-label">SECTION NAME</span>
  <div class="sh-rule"></div>
</div>
```

- Label: 11px, weight 600, `--tracking-wide` (0.1em), uppercase, `--accent` colour
- Rule: `flex: 1`, 1px, `--border` colour

### Data/Spec Tables

Two-column bordered tables with dark key column:

```css
/* Outer */
border: 2px solid var(--border-[colour]);
background: var(--fill-[colour]);

/* Row dividers */
border-bottom: 1px solid var(--border-[colour]);

/* Key column */
grid-template-columns: 200px 1fr;   /* or 260px for model tables */
border-right: 1px solid var(--border-[colour]);
background: [fill-colour at 4% opacity];
font-size: 11px; font-weight: 600; letter-spacing: 0.08em; text-transform: uppercase;
```

### Numbered Row Index

For multi-row tables (The Model pattern):

```css
grid-template-columns: 48px [key-col] 1fr;

.model-index:
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--accent);
  opacity: 0.5;
```

### Background Mark (Ghost Element)

IS mark v11d used as large low-opacity background element:

```html
<svg class="bg-mark" style="position:absolute; width:[size]; height:[size]; opacity:[0.07-0.09]; pointer-events:none;" viewBox="0 0 64 64">
  <!-- v11d circles -->
</svg>
```

- Sizes used: 800px (hero), 480px (section), 320px (CTA)
- Opacity range: 7–9%
- Colour: `#6B4FEC` (accent purple)
- Placement: varied — centred, offset right, bleeding off-edge

### Section Colour Coding

| Section | Border var | Fill var |
|---|---|---|
| Hero / Infrastructure | `--border-accent` | `--fill-accent` |
| Protocols | `--border-green` | `--fill-green` |
| The Model | `--border-amber` | `--fill-amber` |
| Investments | `--border-blue` | `--fill-blue` |

### Nav

```css
position: fixed; height: 56px;
background: rgba(10,13,16,0.92);
backdrop-filter: blur(12px);
border-bottom: 1px solid var(--border);
```

- Logo: wordmark lockup SVG, 24px height
- Links: 13px, weight 500, `--text-muted` default → `--text-primary` hover
- CTA link: bordered, uppercase, 12px weight 600

---

## Platform Notes

**Web:**
- Dark mode default
- Light mode optional for documents
- Support Safari, Chrome, Firefox latest 2 versions

---

## iOS Implementation

### Colors — Asset Catalog

Create `Colors.xcassets/` with the following colorsets (each with light/dark variants):

```
Colors.xcassets/
├── BackgroundPrimary.colorset    // #0A0D10 dark / #FFFFFF light
├── BackgroundSecondary.colorset  // #12161A dark / #F7F7F8 light
├── BackgroundTertiary.colorset   // #1A1F24 dark / #EFEFF1 light
├── BackgroundElevated.colorset   // #23292F dark / #E8E8EA light
├── TextPrimary.colorset          // #F5F5F7 dark / #0A0D10 light
├── TextSecondary.colorset        // #C4C6CB dark / #3D4147 light
├── TextTertiary.colorset         // #6E7178 dark / #6E7178 light
├── BrandPrimary.colorset         // #6B4FEC (both modes — darken to #5A3FCC for light)
├── BrandAccent.colorset          // #8B6FFF dark / #513AC0 light
├── Success.colorset              // #4CAF8C dark / #3A8A6E light
├── Warning.colorset              // #F59E42 dark / #C77E34 light
├── Error.colorset                // #E85D5D dark / #C44A4A light
├── Info.colorset                 // #5B9EFF dark / #4780D6 light
└── BorderDefault.colorset        // rgba(45,51,57,1) dark / rgba(0,0,0,0.1) light
```

**SwiftUI color references:**
```swift
Color("BackgroundPrimary")
Color("BrandPrimary")
Color("Success")
// etc.
```

---

### Typography — iOS

**Body text:** SF Pro (system default — do not override)
**Display headings:** Outfit (load as custom font if using in app)
**Monospace:** SF Mono (system) or JetBrains Mono for data/addresses

```swift
struct Typography {
    // System (SF Pro) — body, UI
    static let largeTitle  = Font.system(.largeTitle,  design: .default, weight: .bold)
    static let title       = Font.system(.title,       design: .default, weight: .semibold)
    static let title2      = Font.system(.title2,      design: .default, weight: .semibold)
    static let headline    = Font.system(.headline,    design: .default, weight: .semibold)
    static let body        = Font.system(.body,        design: .default, weight: .regular)
    static let callout     = Font.system(.callout,     design: .default, weight: .regular)
    static let footnote    = Font.system(.footnote,    design: .default, weight: .regular)
    static let caption     = Font.system(.caption,     design: .default, weight: .regular)

    // Brand (Outfit) — display headings only
    static let displayHero = Font.custom("Outfit-Light",  size: 40)   // weight 300
    static let displayH1   = Font.custom("Outfit-Medium", size: 32)   // weight 500
    static let displayH2   = Font.custom("Outfit-Medium", size: 24)   // weight 500

    // Monospace — technical data, addresses, indices
    static let mono        = Font.system(.body, design: .monospaced)
    static let monoCaption = Font.system(.caption, design: .monospaced)
}
```

**Dynamic Type:** Use `.relativeTo:` for custom fonts to support accessibility scaling:
```swift
Font.custom("Outfit-Medium", size: 32, relativeTo: .title)
```

---

### Spacing — iOS

8pt base unit (matches web 8px exactly):

```swift
struct Spacing {
    static let xs:   CGFloat = 4    // Tight — icon gaps
    static let sm:   CGFloat = 8    // Small — related elements
    static let md:   CGFloat = 16   // Default — component padding
    static let lg:   CGFloat = 24   // Large — section gaps
    static let xl:   CGFloat = 32   // Extra large
    static let xxl:  CGFloat = 48   // Section spacing
    static let xxxl: CGFloat = 64   // Hero spacing
}
```

**Touch targets:** Minimum 44×44pt (Apple HIG requirement)
```swift
Button("Action") { }
    .frame(minWidth: 44, minHeight: 44)
```

**Safe areas:**
```swift
VStack { /* content */ }
    .padding(.horizontal, Spacing.md)
    .safeAreaInset(edge: .bottom) {
        // Bottom bar content if needed
    }
```

---

### Components — SwiftUI

#### Buttons

```swift
// Primary — brand accent (purple)
struct PrimaryButtonStyle: ButtonStyle {
    func makeBody(configuration: Configuration) -> some View {
        configuration.label
            .font(.headline)
            .foregroundColor(.white)
            .padding(.horizontal, 20)
            .padding(.vertical, 12)
            .background(Color("BrandPrimary"))
            .cornerRadius(4)   // minimal — matches institutional direction
            .scaleEffect(configuration.isPressed ? 0.98 : 1.0)
            .animation(.easeOut(duration: 0.1), value: configuration.isPressed)
    }
}

// CTA — amber (for primary conversion actions)
struct CTAButtonStyle: ButtonStyle {
    func makeBody(configuration: Configuration) -> some View {
        configuration.label
            .font(.system(.headline, design: .default, weight: .semibold))
            .foregroundColor(Color("BackgroundPrimary"))
            .padding(.horizontal, Spacing.xxl)
            .padding(.vertical, Spacing.md)
            .background(Color("Warning"))
            .cornerRadius(0)   // brutalist — zero radius for CTAs
            .opacity(configuration.isPressed ? 0.85 : 1.0)
    }
}

// Secondary — bordered
struct SecondaryButtonStyle: ButtonStyle {
    func makeBody(configuration: Configuration) -> some View {
        configuration.label
            .font(.headline)
            .foregroundColor(Color("TextSecondary"))
            .padding(.horizontal, 20)
            .padding(.vertical, 12)
            .overlay(
                Rectangle()  // sharp corners — no RoundedRectangle
                    .stroke(Color("BorderDefault"), lineWidth: 1)
            )
            .opacity(configuration.isPressed ? 0.7 : 1.0)
    }
}
```

#### Text Field

```swift
struct ISTextFieldStyle: TextFieldStyle {
    func _body(configuration: TextField<Self._Label>) -> some View {
        configuration
            .padding(Spacing.md)
            .background(Color("BackgroundTertiary"))
            .overlay(
                Rectangle()
                    .stroke(Color("BorderDefault"), lineWidth: 1)
            )
            .foregroundColor(Color("TextPrimary"))
    }
}
```

#### Card

```swift
struct ISCard<Content: View>: View {
    let borderColor: Color
    let fillColor: Color
    let content: Content

    init(
        borderColor: Color = Color("BrandPrimary").opacity(0.35),
        fillColor: Color = Color("BrandPrimary").opacity(0.03),
        @ViewBuilder content: () -> Content
    ) {
        self.borderColor = borderColor
        self.fillColor = fillColor
        self.content = content()
    }

    var body: some View {
        VStack(alignment: .leading, spacing: Spacing.md) {
            content
        }
        .padding(Spacing.lg)
        .background(fillColor)
        .overlay(
            Rectangle()
                .stroke(borderColor, lineWidth: 2)
        )
    }
}

// Section variants — matches web colour coding
// Infrastructure/Hero: Color("BrandPrimary").opacity(0.35)
// Protocols:           Color("Success").opacity(0.30)
// The Model:           Color("Warning").opacity(0.28)
// Investments:         Color("Info").opacity(0.28)
```

#### Status Indicator

```swift
struct StatusIndicator: View {
    enum Status { case active, warning, error, inactive }
    let status: Status

    var color: Color {
        switch status {
        case .active:   return Color("Success")
        case .warning:  return Color("Warning")
        case .error:    return Color("Error")
        case .inactive: return Color("TextTertiary")
        }
    }

    var body: some View {
        Circle().fill(color).frame(width: 8, height: 8)
    }
}
```

---

### Motion — iOS

```swift
// Default interaction
.animation(.easeOut(duration: 0.2), value: someValue)

// Spring — for state reveals
.animation(.spring(response: 0.3, dampingFraction: 0.7), value: someValue)

// Transitions
.transition(.move(edge: .trailing).combined(with: .opacity))  // slide in
.transition(.opacity)  // simple fade

// Loading
ProgressView()
    .progressViewStyle(CircularProgressViewStyle(tint: Color("BrandPrimary")))
```

**Haptics (important interactions only):**
```swift
let impact = UIImpactFeedbackGenerator(style: .medium)
impact.impactOccurred()
```

---

### Layout — iOS

**Colour scheme:**
```swift
@Environment(\.colorScheme) var colorScheme  // respect system setting
```

**Navigation:**
```swift
NavigationStack {
    // content
}
.navigationTitle("InfraSingularity")
.navigationBarTitleDisplayMode(.large)
```

**Screen widths (reference):**
- iPhone SE: 375pt
- iPhone 14: 393pt
- iPhone 14 Pro Max: 430pt
- iPad: 768–1024pt

**Grid:**
```swift
LazyVGrid(columns: [
    GridItem(.flexible(), spacing: Spacing.md),
    GridItem(.flexible(), spacing: Spacing.md)
], spacing: Spacing.md) { /* items */ }
```

---

### iOS Safari (Web on iOS)

See Web Composition Patterns → nav for backdrop blur. Key rules:

- Never put `overflow-x: hidden` on `html` element — use `body`
- Always set `html { background-color: #0A0D10; }` — hardcoded hex, not CSS variable
- Add `<meta name="theme-color" content="#0A0D10">` for status bar tinting
- Use `-webkit-backdrop-filter` alongside `backdrop-filter` for nav blur
- `env(safe-area-inset-bottom)` works in Safari; `env(safe-area-inset-top)` does NOT in regular browsing (PWA only)
- Always test on a real iOS device — simulators don't reproduce status bar rendering

---

## Border Radius — Platform Summary

| Platform | Radius | Rationale |
|---|---|---|
| Web | `0` everywhere | Brutalist direction — hard institutional edges |
| iOS components (web) | `0` for CTAs, `4px` for inputs | Minimal — preserves native feel |
| iOS native (SwiftUI) | `4px` buttons, `0` CTAs | Sharp but not jarring on iOS |
| iOS system | Use `.cornerRadius(8)` for sheets/modals only | Respect platform conventions |

---

🎨 **Design System v2.1** — Updated 2026-02-18
v1.0 based on Phase 0–5 brand development
v2.0 adds Phase 5.5 web composition patterns: brutalist direction, dim colour border system, 0 border-radius override, section coding, background mark usage
v2.1 adds full iOS implementation: Asset Catalog, SwiftUI components, Dynamic Type, spacing struct, motion, iOS Safari guidance
