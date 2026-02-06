# Phase 6: DESIGN.md Creation

**Consolidate all brand work into one comprehensive master reference document.**

This is the single source of truth that any agent can read to understand every aspect of the brand, from emotional essence to implementation details.

---

## Purpose

Create `DESIGN.md` — a complete, living document that contains:
- The soul of the brand (emotive narrative)
- Strategic positioning
- Visual philosophy and aesthetic direction
- Complete design system (web + iOS)
- Implementation specifications
- Anti-AI-slop principles
- Usage guidelines

**Time:** 20-30 minutes
**Output:** `DESIGN.md` (comprehensive reference document)

---

## Why DESIGN.md Matters

**Single source of truth:** One file that answers every design question.

**Agent memory:** Any LLM reading this will deeply understand:
- What this brand means
- How it should look and feel
- Why choices were made
- How to implement it correctly

**Anti-generic insurance:** Embedding the philosophy prevents:
- Generic "clean and modern" drift
- Arbitrary color/spacing choices
- Copy-paste component libraries
- Loss of brand coherence over time

**Handoff ready:** Designer leaves, dev takes over, DESIGN.md keeps everything consistent.

---

## Structure

DESIGN.md has **8 major sections:**

```
# [Brand]: Design System

## 1. Emotive Narrative
   The soul and humanity of the brand

## 2. Strategic Foundation
   Positioning, voice, personality

## 3. Visual Philosophy
   Aesthetic movement and principles

## 4. Logo System
   Mark, wordmarks, usage guidelines

## 5. Design Tokens
   Colors, typography, spacing (web + iOS)

## 6. Components
   UI patterns and implementation (web + iOS)

## 7. Implementation Guidelines
   Platform-specific specifications

## 8. Anti-AI-Slop Principles
   Quality standards and validation
```

---

## Building the Document

### Section 1: Emotive Narrative

**Source:** `[brand]-emotive-narrative.md` (Phase 0)

Copy the complete narrative verbatim. This sets the emotional context for everything that follows.

**Include:**
- The Human Moment
- The Deeper Truth
- The Transformation
- The Ethos
- The Personality
- The North Star

**Why first:** Every design decision should be testable against this narrative.

---

### Section 2: Strategic Foundation

**Source:** `[brand]-philosophy.md` (Phase 1)

**Include:**
- **Positioning statement** (2-3 sentences: what this is, who it's for)
- **Core metaphor** (the organizing idea)
- **Brand personality traits** (3-5 with evidence/reasoning)
- **Voice and tone principles**
  - How [Brand] speaks
  - Language to use
  - Language to avoid
  - Example phrases (good and bad)
- **Key messaging**
  - Value propositions
  - Taglines
  - Elevator pitch

**Format as:**
```markdown
## 2. Strategic Foundation

### Positioning

[Brand] is [what] for [who], delivering [benefit]. Unlike [alternative], we [unique approach].

### Core Metaphor

[The organizing idea that guides everything — e.g., "invisible infrastructure," "lens for clarity"]

### Brand Personality

- **[Trait]:** [Why this matters, evidence from the project]
- **[Trait]:** [Reasoning]
- **[Trait]:** [Reasoning]

### Voice & Tone

**How [Brand] speaks:**
- [Principle with example]
- [Principle with example]

**Language we use:**
[List of preferred terms]

**Language we avoid:**
[List of generic/problematic terms]

**Example phrases:**
✅ "[Good example]"
❌ "[Bad example - why it's wrong]"
```

---

### Section 3: Visual Philosophy

**Source:** `[brand]-visual-philosophy.md` (Phase 1/2)

**Include:**
- **Aesthetic movement name** (e.g., "Utility Sublime")
- **Philosophy paragraphs** (the complete visual worldview)
- **Design principles** (5-7 core rules)
- **Reference aesthetic** (movements, designers, examples that inspired this)
- **What this IS and ISN'T**

**Format as:**
```markdown
## 3. Visual Philosophy: [Movement Name]

[4-6 paragraphs articulating the visual philosophy]

### Core Design Principles

1. **[Principle]** — [What it means in practice]
2. **[Principle]** — [Explanation]
3. **[Principle]** — [Explanation]
...

### Aesthetic References

This draws from:
- [Movement/designer/example]
- [Movement/designer/example]
- [Movement/designer/example]

### What This IS

- [Characteristic]
- [Characteristic]
- [Characteristic]

### What This ISN'T

- [Anti-pattern to avoid]
- [Anti-pattern to avoid]
- [Anti-pattern to avoid]
```

---

### Section 4: Logo System

**Source:** Final logo files + usage notes

**Include:**
- **The Mark**
  - Description and meaning
  - File references
  - Minimum sizes
- **Wordmark Variants**
  - Horizontal lockup
  - Stacked lockup
  - Text-only variant
  - When to use each
- **Clear Space**
  - Minimum clearance rules
- **Usage Guidelines**
  - Do's and don'ts
  - Color variations (full color, monochrome, white on dark)
- **File Locations**

**Format as:**
```markdown
## 4. Logo System

### The Mark

[Description of what the mark represents]

**Files:**
- `[brand]-mark-final.svg` — Primary mark
- `[brand]-favicon.png` — 32px, 16px favicons

**Minimum sizes:**
- Web: 24px height
- Print: 0.5 inch height
- Never smaller

### Wordmarks

**Horizontal:** Mark + text, for headers and navigation
**Stacked:** Mark above text, for square formats
**Text-only:** Just the wordmark, for inline references

**Files:**
- `[brand]-wordmark-horizontal.svg`
- `[brand]-wordmark-stacked.svg`
- `[brand]-wordmark-textonly.svg`

### Clear Space

Maintain clear space equal to [X]px around all sides of the mark.

[Diagram showing clearance]

### Usage Guidelines

**Do:**
- ✅ Use on backgrounds with sufficient contrast
- ✅ Maintain proportions when scaling
- ✅ Use provided color variations

**Don't:**
- ❌ Rotate or distort the mark
- ❌ Change colors outside provided variations
- ❌ Add effects (shadows, outlines, gradients)
- ❌ Place on busy backgrounds
```

---

### Section 5: Design Tokens

**Source:** `[brand]-design-guidelines.md` (Phase 5)

**Include complete token specifications for web and iOS:**

#### 5.1 Colors

**Format as:**
```markdown
## 5. Design Tokens

### 5.1 Colors

#### Web (CSS Variables)

```css
:root {
  /* Backgrounds */
  --bg-deep: #0e0e10;
  --bg-warm: #16151a;
  --bg-surface: #201e24;

  /* Text */
  --text-primary: #e4e1e8;
  --text-secondary: #a8a2b2;
  --text-muted: #625e6c;

  /* Borders */
  --border: #37343e;
  --border-light: #484452;

  /* Functional */
  --green: #22c55e;
  --green-dim: #187840;
  --amber: #cf9a37;
  --red: #dc2626;

  /* Brand Accents */
  --copper: #b07e58;
}
```

**Color Meanings:**
- **Green (#22c55e):** Success, active states, CTAs — functional, not decorative
- **Amber (#cf9a37):** Warnings, pending states
- **Red (#dc2626):** Errors, critical states
- **Copper (#b07e58):** Premium accents, brand moments

#### iOS (Swift)

```swift
// In Assets.xcassets/Colors/

extension Color {
    static let backgroundPrimary = Color("BackgroundPrimary")
    static let backgroundSecondary = Color("BackgroundSecondary")
    static let textPrimary = Color("TextPrimary")
    static let textSecondary = Color("TextSecondary")
    static let success = Color("Success")  // #22c55e
    static let brandAccent = Color("BrandAccent")  // #b07e58
}
```

[Table showing light/dark mode values for each color]
```

#### 5.2 Typography

**Format as:**
```markdown
### 5.2 Typography

#### Web

**Font Stack:**
```css
--font-sans: 'Inter', -apple-system, sans-serif;
--font-mono: 'JetBrains Mono', 'SF Mono', monospace;
```

**Type Scale:**

| Name | Size | Weight | Line Height | Usage |
|------|------|--------|-------------|-------|
| Display | 48px | 500 | 1.1 | Hero headlines |
| H1 | 32px | 500 | 1.2 | Page titles |
| H2 | 24px | 500 | 1.3 | Section headers |
| Body | 15px | 400 | 1.6 | Paragraphs |
| Caption | 12px | 400 | 1.4 | Labels |
| Mono | 14px | 400 | 1.5 | Code, data |

#### iOS

**System Fonts (Native):**
```swift
struct Typography {
    static let largeTitle = Font.system(.largeTitle, design: .default, weight: .bold)
    static let title = Font.system(.title, design: .default, weight: .semibold)
    static let headline = Font.system(.headline, design: .default, weight: .semibold)
    static let body = Font.system(.body, design: .default, weight: .regular)
    static let caption = Font.system(.caption, design: .default, weight: .regular)
}
```

**Respect Dynamic Type:**
```swift
Text("Content")
    .font(.body)
    .dynamicTypeSize(.medium...(.accessibility3))
```
```

#### 5.3 Spacing

**Format as:**
```markdown
### 5.3 Spacing

**Base Unit:** 8px (web) / 8pt (iOS)

**Scale:**

| Token | Web | iOS | Usage |
|-------|-----|-----|-------|
| xs | 4px | 4pt | Tight gaps |
| sm | 8px | 8pt | Related elements |
| md | 16px | 16pt | Default padding |
| lg | 24px | 24pt | Section gaps |
| xl | 32px | 32pt | Major sections |
| 2xl | 48px | 48pt | Page sections |

**Component Padding:**
- Buttons: 12px vertical, 20px horizontal
- Inputs: 12px vertical, 16px horizontal
- Cards: 20-24px all sides

**iOS Touch Targets:**
Minimum 44x44pt per Apple HIG
```

---

### Section 6: Components

**Source:** `[brand]-design-guidelines.md` (Phase 5)

**Include implementation for both web and iOS:**

**Format as:**
```markdown
## 6. Components

### 6.1 Buttons

#### Web

**Primary Button:**
```css
.button-primary {
  background: var(--green);
  color: var(--bg-deep);
  font-weight: 500;
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
```

**Secondary Button:**
```css
.button-secondary {
  background: transparent;
  border: 1px solid var(--border);
  color: var(--text-primary);
  padding: 12px 20px;
  border-radius: 6px;
}
```

#### iOS

```swift
struct PrimaryButton: ButtonStyle {
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

// Usage
Button("Action") { }
    .buttonStyle(PrimaryButton())
```

[Continue for all major components: inputs, cards, status indicators, etc.]
```

---

### Section 7: Implementation Guidelines

**Platform-specific considerations and patterns**

**Format as:**
```markdown
## 7. Implementation Guidelines

### 7.1 Web Implementation

**Responsive Breakpoints:**
```css
/* Mobile first */
@media (min-width: 640px) { /* sm */ }
@media (min-width: 768px) { /* md */ }
@media (min-width: 1024px) { /* lg */ }
@media (min-width: 1280px) { /* xl */ }
```

**Dark Mode:**
```css
@media (prefers-color-scheme: light) {
    :root {
        --bg-deep: #ffffff;
        --text-primary: #1a1a1a;
        /* ... light mode overrides */
    }
}
```

**Focus States:**
```css
:focus-visible {
    outline: 2px solid var(--green);
    outline-offset: 2px;
}
```

**Animation Performance:**
- Use `transform` and `opacity` for animations (GPU accelerated)
- Avoid animating `width`, `height`, `top`, `left`
- Use `will-change` sparingly

### 7.2 iOS Implementation

**Navigation Patterns:**
```swift
NavigationView {
    // content
}
.navigationTitle("Title")
.navigationBarTitleDisplayMode(.large)
```

**System Integration:**
```swift
// Respect system color scheme
@Environment(\.colorScheme) var colorScheme

// Support Dynamic Type
@Environment(\.sizeCategory) var sizeCategory

// Haptic feedback for key interactions
let generator = UIImpactFeedbackGenerator(style: .medium)
generator.impactOccurred()
```

**Safe Areas:**
```swift
VStack {
    // content
}
.safeAreaInset(edge: .bottom) {
    // Bottom bar
}
.ignoresSafeArea(.keyboard)  // When needed
```

### 7.3 Cross-Platform Consistency

**Aim for similar feel, not pixel-perfect matching:**
- Web can use more gradients/shadows (performant)
- iOS should feel native (use system fonts, native navigation)
- Color palette should be identical
- Spacing rhythm should be consistent (8pt/px base)
- Components should be recognizably "the same" but platform-appropriate
```

---

### Section 8: Anti-AI-Slop Principles

**The quality standards and validation checklist**

**Format as:**
```markdown
## 8. Anti-AI-Slop Principles

This brand exists to avoid generic, soulless design. Every decision should be intentional, connected to the emotive narrative, and distinctively **[Brand]**.

### Core Principles

1. **No generic patterns**
   - ❌ Purple-to-blue gradients without reason
   - ❌ Overly rounded shapes everywhere
   - ❌ Random "clean and modern" aesthetics
   - ✅ Every gradient/radius choice has narrative justification

2. **Color carries meaning**
   - ❌ Coloring everything for "visual interest"
   - ❌ Using success colors decoratively
   - ✅ Green = go/success, Red = stop/error, Amber = caution
   - ✅ Strategic color use (10-20% of elements)

3. **Craftsmanship markers**
   - ❌ Arbitrary border-radius values
   - ❌ Random spacing that breaks the 8px grid
   - ❌ Orphaned colors not in the system
   - ✅ Consistent rounding (6px, 8px, 12px)
   - ✅ All spacing from the defined scale
   - ✅ Every color named and systematic

4. **Typography with personality**
   - ❌ "Clean sans-serif" with no character
   - ❌ Body copy that's too small to read
   - ❌ All-caps everything
   - ✅ Font choices reflect brand personality
   - ✅ Readable sizes (15-16px body minimum)
   - ✅ Clear hierarchy (not just "make it bigger")

5. **Distinctive, not derivative**
   - ❌ Copying Stripe/Linear/Vercel verbatim
   - ❌ Following Dribbble trends
   - ❌ "Inspired by" that's really "copied from"
   - ✅ Learning from references but creating something new
   - ✅ Visual language specific to **[Brand]**

### Decision Testing

Before implementing any design element, ask:

1. **Narrative test:** "Does this express our emotive narrative?"
2. **Meaning test:** "Why this color/size/spacing and not another?"
3. **Distinctive test:** "Could this only be **[Brand]**, or any modern app?"
4. **Platform test:** "Does this feel native to web/iOS?"
5. **Craft test:** "Does this look like expert work or default settings?"

If you can't answer these, the choice is arbitrary. Revise.

### Validation Checklist

Before considering design work complete:

**Visual Cohesion:**
- [ ] Every color in use is in the design system
- [ ] All spacing values are from the defined scale
- [ ] Border radius is consistent (6px, 8px, or 12px)
- [ ] Typography uses defined scale (not random sizes)

**Brand Expression:**
- [ ] Reflects the emotive narrative
- [ ] Embodies the visual philosophy
- [ ] Feels distinctively **[Brand]**
- [ ] Not interchangeable with competitors

**Platform Quality:**
- [ ] Web design uses modern CSS appropriately
- [ ] iOS design feels native (not web-in-webview)
- [ ] Components work across screen sizes
- [ ] Touch targets meet platform guidelines

**Craftsmanship:**
- [ ] No elements overlap
- [ ] Perfect alignment on grid
- [ ] Consistent visual weight
- [ ] Looks like expert-level work

If any checkbox fails, revise before shipping.

### Red Flags

Stop immediately if you see:
- Random gradients added "for interest"
- Spacing that doesn't follow 8px rhythm
- Colors not in the system
- "Clean and modern" as the only descriptor
- Copy-paste from component library without customization
- Decisions made "because it looks good" without reasoning

**Remember:** Generic is easy. Distinctive takes intention.
```

---

## Assembly Process

### Step 1: Gather All Source Files

Collect:
- `[brand]-emotive-narrative.md` (Phase 0)
- `[brand]-philosophy.md` (Phase 1)
- `[brand]-visual-philosophy.md` (Phase 1/2)
- `[brand]-mark-final.svg` (Phase 3)
- `[brand]-wordmark-*.svg` (Phase 4)
- `[brand]-design-guidelines.md` (Phase 5)

### Step 2: Create DESIGN.md

Start with template structure (see template file).

### Step 3: Populate Each Section

Copy content from source files, reformatting for the unified structure.

**Key points:**
- Keep emotive narrative verbatim (Section 1)
- Consolidate strategic content (Section 2)
- Merge visual philosophy (Section 3)
- Extract and format logo guidelines (Section 4)
- Convert design guidelines to token format (Section 5-7)
- Add comprehensive anti-slop section (Section 8)

### Step 4: Add Navigation

Include table of contents at top:

```markdown
# [Brand]: Design System

## Table of Contents

1. [Emotive Narrative](#1-emotive-narrative)
2. [Strategic Foundation](#2-strategic-foundation)
3. [Visual Philosophy](#3-visual-philosophy)
4. [Logo System](#4-logo-system)
5. [Design Tokens](#5-design-tokens)
6. [Components](#6-components)
7. [Implementation Guidelines](#7-implementation-guidelines)
8. [Anti-AI-Slop Principles](#8-anti-ai-slop-principles)

---
```

### Step 5: Add Quick Reference Section

At the very bottom, add:

```markdown
---

## Quick Reference

**Colors (Web):**
```css
--bg-deep: #0e0e10; --text-primary: #e4e1e8; --green: #22c55e;
```

**Spacing:** 4, 8, 16, 24, 32, 48px

**Typography:** Inter (UI), JetBrains Mono (code)

**Key Principle:** [One sentence from the north star]

---

*Last updated: [Date]*
*Version: 1.0*
```

### Step 6: Validate Completeness

Check that DESIGN.md answers:
- [ ] Why does this brand exist? (Narrative)
- [ ] What personality does it have? (Strategy)
- [ ] How should it look and feel? (Visual philosophy)
- [ ] What does the logo mean? (Logo system)
- [ ] What colors/fonts/spacing do I use? (Tokens)
- [ ] How do I build buttons/cards/inputs? (Components)
- [ ] How do I implement on web/iOS? (Guidelines)
- [ ] How do I avoid making this generic? (Anti-slop)

If any question is unanswered, the document is incomplete.

---

## Output

**File:** `DESIGN.md`
**Location:** Project root (or `docs/DESIGN.md`)
**Size:** Typically 300-500 lines (comprehensive but readable)

---

## Usage

Once DESIGN.md exists, it becomes the reference for all design decisions:

**For developers:**
> "Check DESIGN.md for color tokens and component specs"

**For designers:**
> "Read DESIGN.md to understand the brand's emotive foundation"

**For LLMs:**
> "Read DESIGN.md to understand the complete design system before making any changes"

**For stakeholders:**
> "DESIGN.md is the single source of truth for our brand"

---

## Maintenance

DESIGN.md is a living document:

**Update when:**
- Brand narrative evolves
- New components are added
- Platform guidelines change (iOS updates)
- Design system matures

**Version control:**
- Commit to git
- Include in project documentation
- Reference in README

**Keep it synchronized:**
- If you update a color, update DESIGN.md
- If you add a component, document it here
- If philosophy shifts, revise Section 1

---

## Gate Check

Before moving to Phase 7 (Packaging), validate:

1. **Completeness:** All 8 sections filled out thoroughly
2. **Coherence:** Each section connects to the narrative
3. **Usability:** Can a new designer/developer use this immediately?
4. **Accuracy:** All code snippets are copy-paste ready
5. **Clarity:** No ambiguous "use your judgment" without guidance

Get user approval on the complete DESIGN.md before packaging.

---

## Why This Is Critical

**Without DESIGN.md:** Brand guidelines are scattered across multiple files, knowledge lives in people's heads, design drift happens slowly, generic patterns creep in.

**With DESIGN.md:** One file keeps everything coherent. New team members onboard instantly. LLMs maintain consistency. The brand stays distinctive.

**This is the anti-AI-slop insurance policy.**
