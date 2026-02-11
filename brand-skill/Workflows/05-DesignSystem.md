# Phase 5: Design System

Define the complete visual language for **web and iOS**: colors, type, spacing, components.

## Time

30-45 minutes (extended to include mobile specifications).

## Prerequisites

- Mark and wordmark locked
- Visual philosophy established

---

## Anti-AI-Slop Checklist for This Phase

Before finalizing the design system, validate against these principles:

- [ ] **Colors have meaning** — Functional colors (green, red, amber) are used for meaning, not decoration
- [ ] **No generic gradients** — If using gradients, they must serve the brand philosophy, not just "look modern"
- [ ] **Warm backgrounds** — Pure #000 feels dead; dark backgrounds have warmth
- [ ] **Distinctive typography** — Not just "clean sans-serif" but fonts with personality
- [ ] **Intentional spacing** — Not arbitrary; follows clear rhythm and hierarchy
- [ ] **Cohesive system** — Every choice connects back to the emotive narrative
- [ ] **Platform-appropriate** — Web and iOS specs feel native to their platforms

---

## Important: Template Colors

The hex values in this workflow are from the **Sorted.fund** example brand. They are illustrative — do not copy them into your brand. Replace ALL color values with your brand's palette derived from Phases 0-2 (emotive narrative and visual philosophy).

The same applies to font choices (Inter, JetBrains Mono) — these are Sorted defaults. Choose fonts that match your brand's personality.

---

## Process

### 1. Colors

Build outward from the mark's colors and visual philosophy.

#### Web Colors (Dark Mode Default)

**Backgrounds** (derive from mark's darkest tone, step up in lightness):
```css
--bg-deep:     {BG_DEEP}      /* Main background — warm near-black, derive from mark's darkest neutral */
--bg-warm:     {BG_WARM}      /* Cards, elevated surfaces — +6-8% lightness from bg-deep */
--bg-surface:  {BG_SURFACE}   /* Inputs, wells, recessed areas — +4-6% from bg-warm */
--bg-elevated: {BG_ELEVATED}  /* Hover states, overlays — +4-6% from bg-surface */
```

**Text** (derive for contrast against backgrounds):
```css
--text-primary:   {TEXT_PRIMARY}    /* Headings — minimum 7:1 contrast against bg-deep */
--text-secondary: {TEXT_SECONDARY}  /* Body copy — ~60-70% of primary's contrast */
--text-muted:     {TEXT_MUTED}      /* Labels, hints — ~35-45% of primary's contrast */
--text-whisper:   {TEXT_WHISPER}    /* Disabled states — near-invisible */
```

**Borders:**
```css
--border:       {BORDER}        /* Default borders — between bg-elevated and text-whisper */
--border-light: {BORDER_LIGHT}  /* Emphasized borders — slightly lighter */
```

**Functional** (harmonize with brand accent):
```css
--green:       {GREEN}       /* Success, active, CTAs — harmonize with brand accent */
--green-dim:   {GREEN_DIM}   /* Green hover/secondary — reduce lightness 20-30% */
--green-dark:  {GREEN_DARK}  /* Green backgrounds — very low lightness */
--amber:       {AMBER}       /* Warnings, pending states */
--red:         {RED}         /* Errors, critical states */
--blue:        {BLUE}        /* Links, info (use sparingly) */
```

**Brand Accents** (from mark and visual philosophy):
```css
--accent:      {BRAND_ACCENT}      /* Primary accent — from mark or visual philosophy */
--accent-dim:  {BRAND_ACCENT_DIM}  /* Secondary accent — reduce lightness 20-30%, saturation 10-20% */
```

### Color Derivation Process

**Do not invent colors arbitrarily.** Derive the full palette from the mark:

1. **Start with mark colors** (typically 2-3: primary neutral, accent, optional secondary)
2. **Derive backgrounds**: Take the darkest neutral from the mark. Step up in lightness (+6-8% per level) while maintaining the same warmth/coolness.
3. **Derive text**: Set primary text for WCAG AAA (7:1) against bg-deep. Step down contrast for secondary, muted, whisper.
4. **Functional colors**: Green, amber, red should harmonize with the brand accent. Test against all backgrounds.
5. **Validate**: Run every text/background combination through contrast check. Minimum 4.5:1 for body text (WCAG AA), 3:1 for large text.

#### iOS Colors (Semantic + Brand)

**Dynamic Colors (adapt to light/dark):**
```swift
// Backgrounds
Color("BackgroundPrimary")   // Deep dark in dark mode, white in light
Color("BackgroundSecondary") // Warm surface
Color("BackgroundTertiary")  // Elevated surface

// Text
Color("TextPrimary")         // {TEXT_PRIMARY} (dark) / {TEXT_PRIMARY_LIGHT} (light)
Color("TextSecondary")       // {TEXT_SECONDARY} (dark) / {TEXT_SECONDARY_LIGHT} (light)
Color("TextTertiary")        // {TEXT_MUTED} (dark) / {TEXT_MUTED_LIGHT} (light)

// System (semantic — derive from brand accent)
Color("Success")             // {GREEN}
Color("Warning")             // {AMBER}
Color("Error")               // {RED}
Color("Info")                // {BLUE}

// Brand
Color("BrandPrimary")        // {BRAND_ACCENT} — from mark's primary accent
Color("BrandAccent")         // {BRAND_ACCENT_DIM} — secondary brand color
```

**iOS Asset Catalog Setup:**
```
Colors.xcassets/
├── BackgroundPrimary.colorset
├── BackgroundSecondary.colorset
├── TextPrimary.colorset
├── Success.colorset
└── BrandPrimary.colorset
```

Each with light/dark variants defined.

---

### 2. Typography

#### Web Typography

**Font Stack:**
```css
--font-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
--font-mono: 'JetBrains Mono', 'SF Mono', 'Fira Code', monospace;
```

**Type Scale:**
```css
/* Size / Weight / Line Height / Usage */
--text-display:  48px / 500 / 1.1  /* Hero headlines */
--text-h1:       32px / 500 / 1.2  /* Page titles */
--text-h2:       24px / 500 / 1.3  /* Section headers */
--text-h3:       18px / 500 / 1.4  /* Card titles */
--text-body:     15px / 400 / 1.6  /* Paragraphs */
--text-small:    14px / 400 / 1.5  /* Secondary text */
--text-caption:  12px / 400 / 1.4  /* Labels, hints */
--text-mono:     14px / 400 / 1.5  /* Code, data */
```

**Label Style:**
```css
font-size: 11-12px;
font-weight: 500;
text-transform: uppercase;
letter-spacing: 0.08em;
color: var(--text-muted);
```

#### iOS Typography

**System Fonts (Native):**
```swift
// Use SF Pro for native feel
Font.system(.largeTitle, design: .default, weight: .bold)    // 34pt
Font.system(.title, design: .default, weight: .semibold)     // 28pt
Font.system(.title2, design: .default, weight: .semibold)    // 22pt
Font.system(.title3, design: .default, weight: .semibold)    // 20pt
Font.system(.headline, design: .default, weight: .semibold)  // 17pt
Font.system(.body, design: .default, weight: .regular)       // 17pt
Font.system(.callout, design: .default, weight: .regular)    // 16pt
Font.system(.subheadline, design: .default, weight: .regular) // 15pt
Font.system(.footnote, design: .default, weight: .regular)   // 13pt
Font.system(.caption, design: .default, weight: .regular)    // 12pt
```

**Brand Typography (Custom if needed):**
```swift
// If using custom fonts (e.g., Inter)
Font.custom("Inter", size: 17, relativeTo: .body)
Font.custom("Inter", size: 28, relativeTo: .title).weight(.semibold)

// Monospace for code/data
Font.system(.body, design: .monospaced)
```

**iOS Typography Tokens:**
```swift
// Define in Typography.swift or DesignSystem
struct Typography {
    static let largeTitle = Font.system(.largeTitle, design: .default, weight: .bold)
    static let title = Font.system(.title, design: .default, weight: .semibold)
    static let headline = Font.system(.headline, design: .default, weight: .semibold)
    static let body = Font.system(.body, design: .default, weight: .regular)
    static let caption = Font.system(.caption, design: .default, weight: .regular)

    // Brand-specific
    static let displayHero = Font.system(size: 40, weight: .bold, design: .default)
    static let monoCode = Font.system(.body, design: .monospaced)
}
```

---

### 3. Spacing

**Base Unit:** 8px (iOS: 8pt)

#### Web Spacing Scale:
```css
--space-xs:   4px     /* Tight gaps, inline spacing */
--space-sm:   8px     /* Related elements */
--space-md:   16px    /* Default padding */
--space-lg:   24px    /* Section gaps */
--space-xl:   32px    /* Major sections */
--space-2xl:  48px    /* Page sections */
--space-3xl:  64px    /* Hero spacing */
```

**Component Padding (Web):**
```css
Buttons:  12px 20px
Inputs:   12px 16px
Cards:    20px 24px
Modals:   24px 32px
```

#### iOS Spacing Scale:
```swift
struct Spacing {
    static let xs: CGFloat = 4      // Tight spacing
    static let sm: CGFloat = 8      // Small spacing
    static let md: CGFloat = 16     // Default spacing
    static let lg: CGFloat = 24     // Large spacing
    static let xl: CGFloat = 32     // Extra large
    static let xxl: CGFloat = 48    // Section spacing
    static let xxxl: CGFloat = 64   // Hero spacing
}
```

**iOS Component Padding:**
```swift
Button:     .padding(.horizontal, 20).padding(.vertical, 12)
TextField:  .padding(16)
Card:       .padding(20)
Sheet:      .padding(24)
```

**iOS Safe Area Considerations:**
```swift
// Always account for safe areas
VStack {
    // content
}
.padding(.horizontal, Spacing.md)
.safeAreaInset(edge: .bottom) {
    // Bottom bar if needed
}
```

---

### 4. Components

#### Web Components

**Primary Button:**
```css
background: var(--green);
color: var(--bg-deep);
font-weight: 500;
padding: 12px 20px;
border-radius: 6px;
transition: all 200ms ease;

&:hover {
  background: var(--green-dim);
}
```

**Secondary Button:**
```css
background: transparent;
border: 1px solid var(--border);
color: var(--text-primary);
padding: 12px 20px;
border-radius: 6px;

&:hover {
  border-color: var(--border-light);
}
```

**Input Field:**
```css
background: var(--bg-surface);
border: 1px solid var(--border);
color: var(--text-primary);
padding: 12px 16px;
border-radius: 6px;
font-family: inherit;

&:focus {
  border-color: var(--green);
  outline: none;
}
```

**Card:**
```css
background: var(--bg-warm);
border: 1px solid var(--border);
border-radius: 8px;
padding: 20px 24px;
```

**Status Indicators:**
- Size: 8px diameter
- Green (`{GREEN}`): Healthy/Active
- Amber (`{AMBER}`): Warning/Pending
- Red (`{RED}`): Error/Critical
- Gray (`{TEXT_MUTED}`): Inactive/Disabled

#### iOS Components

**Button Styles:**
```swift
// Primary Button
Button("Action") { }
    .buttonStyle(PrimaryButtonStyle())

struct PrimaryButtonStyle: ButtonStyle {
    func makeBody(configuration: Configuration) -> some View {
        configuration.label
            .font(.headline)
            .foregroundColor(Color("BackgroundPrimary"))
            .padding(.horizontal, 20)
            .padding(.vertical, 12)
            .background(Color("Success"))
            .cornerRadius(8)
            .scaleEffect(configuration.isPressed ? 0.98 : 1.0)
    }
}

// Secondary Button
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
```

**Text Field:**
```swift
TextField("Placeholder", text: $text)
    .textFieldStyle(CustomTextFieldStyle())

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
```

**Card Component:**
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
```

**Status Indicators:**
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
```

---

### 5. Layout

#### Web Layout

**Max Widths:**
```css
--width-content:   720px     /* Prose, articles */
--width-dashboard: 1200px    /* App interfaces */
--width-full:      1440px    /* Marketing pages */
```

**Grid System:**
- 12 columns
- 24px gutters
- Responsive breakpoints: 640px, 768px, 1024px, 1280px

**Density Principle:**
- Developer tools can be information-dense
- Don't waste space with excessive whitespace
- Maintain clear hierarchy through spacing, not sprawl

#### iOS Layout

**Screen Considerations:**
```swift
// Standard iOS screen widths
// iPhone SE: 375pt
// iPhone 14: 393pt
// iPhone 14 Pro Max: 430pt
// iPad: 768pt - 1024pt

// Safe area insets
// Top: ~47pt (with Dynamic Island)
// Bottom: ~34pt (home indicator)
```

**Grid System:**
```swift
LazyVGrid(columns: [
    GridItem(.flexible(), spacing: Spacing.md),
    GridItem(.flexible(), spacing: Spacing.md)
], spacing: Spacing.md) {
    // Grid items
}
```

**Touch Targets:**
```swift
// Minimum touch target: 44x44pt (Apple HIG)
Button("Action") { }
    .frame(minWidth: 44, minHeight: 44)
```

---

### 6. Motion & Animation

#### Web Motion

**Timing:**
```css
--timing-micro:   100ms    /* Hover states */
--timing-default: 200ms    /* Transitions */
--timing-enter:   300ms    /* Appearances */
--timing-exit:    200ms    /* Removals */
```

**Easing:**
```css
--ease-default:   ease-out
--ease-enter:     cubic-bezier(0.16, 1, 0.3, 1)
--ease-exit:      ease-in
```

**Principles:**
- Purposeful, not decorative
- Status changes should be visible
- No gratuitous animations
- Loading states use subtle pulse, not spinners

#### iOS Motion

**Standard Animations:**
```swift
.animation(.easeOut(duration: 0.2), value: someValue)  // Default
.animation(.spring(response: 0.3, dampingFraction: 0.7), value: someValue)  // Spring
.animation(.easeIn(duration: 0.15), value: someValue)  // Exit
```

**Transition Patterns:**
```swift
// Slide in
.transition(.move(edge: .trailing).combined(with: .opacity))

// Scale + fade
.transition(.scale.combined(with: .opacity))

// Asymmetric
.transition(
    .asymmetric(
        insertion: .move(edge: .trailing),
        removal: .move(edge: .leading)
    )
)
```

**Loading States:**
```swift
ProgressView()
    .progressViewStyle(CircularProgressViewStyle(tint: Color("BrandPrimary")))
```

---

### 7. Platform-Specific Considerations

#### Web-Specific

**Focus States:**
```css
:focus-visible {
    outline: 2px solid var(--green);
    outline-offset: 2px;
}
```

**Responsive Typography:**
```css
h1 {
    font-size: clamp(24px, 5vw, 32px);
}
```

**Light Mode Derivation:**

Light mode is not "invert the values." It requires its own derivation process:

```css
@media (prefers-color-scheme: light) {
    :root {
        /* Backgrounds — light to lighter (opposite of dark mode's dark to lighter) */
        --bg-deep:     {BG_DEEP_LIGHT};     /* White or warm off-white */
        --bg-warm:     {BG_WARM_LIGHT};     /* Slightly darker — light gray with brand warmth */
        --bg-surface:  {BG_SURFACE_LIGHT};  /* Slightly darker still — for inputs, wells */
        --bg-elevated: {BG_ELEVATED_LIGHT}; /* Lightest gray — hovers, overlays */

        /* Text — dark text, preserve warmth (not pure #000) */
        --text-primary:   {TEXT_PRIMARY_LIGHT};   /* Near-black with brand warmth */
        --text-secondary: {TEXT_SECONDARY_LIGHT}; /* Medium gray */
        --text-muted:     {TEXT_MUTED_LIGHT};     /* Light gray */
        --text-whisper:   {TEXT_WHISPER_LIGHT};   /* Very light gray */

        /* Borders — darker on light backgrounds */
        --border:       {BORDER_LIGHT_MODE};
        --border-light: {BORDER_LIGHT_MODE_EMPHASIS};

        /* Functional — may need saturation/lightness adjustment for white backgrounds */
        --green:      {GREEN_LIGHT};      /* Often needs to be darker/more saturated */
        --green-dim:  {GREEN_DIM_LIGHT};
        --green-dark: {GREEN_DARK_LIGHT}; /* Light tint for green backgrounds */
        --amber:      {AMBER_LIGHT};
        --red:        {RED_LIGHT};
        --blue:       {BLUE_LIGHT};

        /* Accents — may need adjustment for contrast on white */
        --accent:     {ACCENT_LIGHT};
        --accent-dim: {ACCENT_DIM_LIGHT};
    }
}
```

**Light mode derivation process:**

1. **Backgrounds**: Start with white or warm off-white for `bg-deep`. Step *down* in lightness for warm, surface, elevated (the progression direction reverses — in dark mode you go lighter, in light mode you go slightly darker for depth).
2. **Text**: Primary text is near-black — preserve the brand's warmth (not pure `#000000`). Step down contrast for secondary/muted/whisper just like dark mode.
3. **Accent colors**: Test every accent against white/off-white backgrounds. Many dark-mode accents are too light on white — increase saturation or decrease lightness until WCAG AA passes.
4. **Functional colors**: Green/amber/red often need to be slightly darker on light backgrounds. Don't just reuse the dark mode values without checking contrast.
5. **Borders**: Borders that were light-on-dark need to become dark-on-light with lower opacity. Typical pattern: `rgba(0, 0, 0, 0.1)` for default, `rgba(0, 0, 0, 0.2)` for emphasis.
6. **Validate all pairs**: Run every text/background combination through contrast check for light mode separately from dark mode.

**iOS Safari Safe Areas (Web):**

Fixed/sticky navigation bars on iOS Safari will overlap the status bar, Dynamic Island, and home indicator unless safe-area insets are handled correctly. This is a **recurring failure point** — get it right the first time.

**1. Viewport meta tag — always include `viewport-fit=cover`:**
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
```
Without `viewport-fit=cover`, `env(safe-area-inset-*)` values will always be `0px` and the page won't extend behind the status bar.

**2. Fixed nav bars must preserve safe-area padding in ALL states:**
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

**3. CRITICAL — CSS shorthand `padding:` overrides individual `padding-top:`:**

This is the most common bug. If your nav has state changes (e.g., `.scrolled`, `.compact`) that use shorthand `padding:`, the shorthand will **silently override** the safe-area `padding-top` from the base rule:

```css
/* BUG — shorthand kills safe-area padding-top */
nav.scrolled {
  padding: 0.75rem var(--pad-x);  /* ← overrides env(safe-area-inset-top) */
}

/* FIX — set padding-top explicitly AFTER any shorthand */
nav.scrolled {
  padding: 0.75rem var(--pad-x);
  padding-top: calc(0.75rem + env(safe-area-inset-top, 0px));
  padding-left: max(var(--pad-x), env(safe-area-inset-left));
  padding-right: max(var(--pad-x), env(safe-area-inset-right));
}
```

**Rule: Never use `padding:` shorthand on elements that need safe-area insets.** If you must use shorthand (e.g., for a state change), immediately re-declare the individual safe-area properties after it.

**4. Mobile media query overrides need it too:**
```css
@media (max-width: 600px) {
  nav.scrolled {
    padding-top: calc(0.5rem + env(safe-area-inset-top, 0px));
  }
}
```

**5. Bottom safe area for footers/CTAs:**
```css
.bottom-bar {
  position: fixed;
  bottom: 0;
  padding-bottom: max(1rem, env(safe-area-inset-bottom));
}
```

**6. iOS-specific backdrop blur:**
```css
nav {
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);  /* Required for iOS Safari */
}
```

**Testing:** Simulate in Chrome DevTools (toggle device toolbar, select iPhone) or use Safari's Responsive Design Mode. But **always verify on a real iOS device** — simulators don't always reproduce safe-area behavior accurately.

#### iOS-Specific

**Navigation:**
```swift
// Use standard NavigationView/NavigationStack
NavigationView {
    // content
}
.navigationTitle("Title")
.navigationBarTitleDisplayMode(.large)
```

**Lists:**
```swift
List {
    // items
}
.listStyle(.insetGrouped)  // or .plain, .grouped
```

**Haptics:**
```swift
// Use for important feedback
let generator = UIImpactFeedbackGenerator(style: .medium)
generator.impactOccurred()
```

**System Integration:**
```swift
// Use system share sheet
.sheet(isPresented: $showShare) {
    ShareSheet(items: [shareContent])
}

// Respect system settings
@Environment(\.colorScheme) var colorScheme
@Environment(\.sizeCategory) var sizeCategory  // Dynamic Type
```

---

### 8. Compile Design Guidelines

Create comprehensive documentation in `[brand]-design-guidelines.md`:

**Structure:**
1. **Philosophy** (reference emotive narrative)
2. **Logo Usage** (mark, wordmarks, spacing, don'ts)
3. **Color System** (web + iOS with semantic names)
4. **Typography** (web + iOS scales)
5. **Spacing System** (unified 8pt/px base)
6. **Components** (web CSS + iOS SwiftUI)
7. **Layout Patterns** (grid systems, max-widths)
8. **Motion Principles** (timing, easing)
9. **Platform Guidelines** (web vs iOS specific considerations)
10. **Voice & Tone** (from Phase 0/1)
11. **Code Snippets** (copy-paste ready)

**Include:**
- Complete CSS `:root` variables block
- Complete Swift `DesignSystem` struct
- Component examples in both platforms
- Do's and don'ts with visual examples

---

## Outputs

- `[brand]-design-guidelines.md` — use `Templates/design-guidelines-template.md` as a starting structure (comprehensive, platform-agnostic where possible)

This becomes **Section 3** of the final DESIGN.md.

---

## Anti-AI-Slop Validation

Before declaring this phase complete, validate:

### System Cohesion
- [ ] Every color choice has a reason (not just "looks nice")
- [ ] Typography reflects brand personality (not just "clean and modern")
- [ ] Spacing creates clear rhythm (not arbitrary values)
- [ ] Components feel distinctive (not Bootstrap/Tailwind default)

### Platform Appropriateness
- [ ] Web design uses browser capabilities naturally
- [ ] iOS design feels native (not web-in-a-webview)
- [ ] Colors work in light and dark modes on both platforms
- [ ] Touch targets meet iOS guidelines (44pt minimum)

### Craftsmanship Markers
- [ ] No random border-radius values (consistent: 6px, 8px, 12px)
- [ ] No orphaned colors (every color is part of the system)
- [ ] Transitions have purpose (not decoration)
- [ ] Documentation is thorough (developer can implement without asking)

---

## Gate Check

1. Confirm contrast validation matrix is complete (Section 9) — all text/background pairs checked for both dark and light mode
2. Present the color palette, typography hierarchy, contrast matrix, and key components to the user
3. Ask: **"Phase 5 Gate Check — Design system covers colors (dark+light), type, spacing, components, and contrast validation. Approved to proceed to Phase 5.5: Composition & Visual Identity?"**
4. On approval: update `.brand-progress.md` → Phase 5: COMPLETE
5. Only proceed to Phase 5.5 when user explicitly approves

---

## Notes

**Warm darks:** Pure #000 feels dead. Always add slight warmth to dark backgrounds.

**Functional color:** Green = success/go, Red = error/stop. Use color for meaning, not decoration.

**Platform parity:** Aim for similar feel across web/iOS, but embrace platform conventions. Don't fight the system.

**CSS/Swift variables:** Developers need copy-paste code. Make it production-ready.

**Accessibility:** See the contrast validation step below — do not skip this.

---

### 9. Contrast Validation (MANDATORY)

**Do not declare Phase 5 complete without running this check.** "Ensure contrast" is not a checklist item — it's a concrete step with a concrete output.

#### Process

Test every text color against every background color it will appear on. This means:

1. `text-primary` against `bg-deep`, `bg-warm`, `bg-surface`, `bg-elevated`
2. `text-secondary` against the same four backgrounds
3. `text-muted` against the same four backgrounds
4. `green` (for CTAs/buttons) against `bg-deep` and `bg-warm`
5. `accent` against `bg-deep` and `bg-warm`
6. Focus ring color (`green` or `accent`) against all backgrounds

**WCAG AA minimums:**
- Body text (under 18px or under 14px bold): **4.5:1**
- Large text (18px+ or 14px+ bold): **3:1**
- UI components (icons, borders, focus rings): **3:1**

#### Contrast Ratio Calculation

If you have Node.js, you can compute contrast ratios programmatically. Otherwise, use this formula:

1. Convert hex to relative luminance: `L = 0.2126*R + 0.7152*G + 0.0722*B` (where R, G, B are linearized sRGB values)
2. Contrast ratio = `(L1 + 0.05) / (L2 + 0.05)` where L1 is the lighter color

Or use an online tool: [webaim.org/resources/contrastchecker](https://webaim.org/resources/contrastchecker/)

#### Output: Contrast Matrix

Include this table in the design guidelines:

```markdown
### Contrast Validation

| Text Color | Background | Ratio | AA Body (4.5:1) | AA Large (3:1) |
|-----------|-----------|-------|-----------------|----------------|
| text-primary (#hex) | bg-deep (#hex) | X:1 | PASS/FAIL | PASS/FAIL |
| text-primary (#hex) | bg-warm (#hex) | X:1 | PASS/FAIL | PASS/FAIL |
| text-secondary (#hex) | bg-deep (#hex) | X:1 | PASS/FAIL | PASS/FAIL |
| text-secondary (#hex) | bg-warm (#hex) | X:1 | PASS/FAIL | PASS/FAIL |
| text-muted (#hex) | bg-deep (#hex) | X:1 | PASS/FAIL | PASS/FAIL |
| text-muted (#hex) | bg-warm (#hex) | X:1 | PASS/FAIL | PASS/FAIL |
| green (#hex) | bg-deep (#hex) | X:1 | PASS/FAIL | PASS/FAIL |
| accent (#hex) | bg-deep (#hex) | X:1 | PASS/FAIL | PASS/FAIL |
```

**If a pair fails:**
- For text colors: increase lightness (dark mode) or decrease lightness (light mode) until the ratio meets 4.5:1
- For functional colors: increase saturation and/or adjust lightness
- For muted text: failure at body size is acceptable if it's only used at large text sizes — document this explicitly
- **Never sacrifice legibility for aesthetics**

#### Light Mode Validation

Run the same matrix for light mode tokens. Light mode often has different failure points — accent colors that worked on dark backgrounds may fail on white.
