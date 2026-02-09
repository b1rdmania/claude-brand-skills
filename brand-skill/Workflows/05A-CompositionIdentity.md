# Phase 5.5: Composition & Visual Identity

Define how this brand **uniquely occupies space**. Tokens define materials; this phase defines what to build with them.

## Time

60-120 minutes. This is the most important phase for distinctiveness.

## Prerequisites

- Design system tokens from Phase 5
- Emotive narrative from Phase 0
- Visual philosophy from Phase 1

---

## Why This Phase Exists

Phases 0-5 produce excellent ingredients: a grounding narrative, a color palette, a type system, a mark. But ingredients don't prevent convergence. Three brands with completely different tokens will produce the same page if the LLM chooses the layout — because the LLM will always choose the statistical center of "good page in this category."

Composition is where identity lives: how content is structured, how the eye moves, what's big and what's small, what rhythm the sections follow, where space is generous and where it's dense. **This is the only layer that makes a brand visually recognizable**, and it's the one layer an LLM cannot produce on its own.

This phase uses an evolutionary process where the LLM generates structural diversity and the human selects for distinctiveness. The human's taste — which exists outside the training distribution — is the selection pressure that pushes the output away from the mean.

---

## Process

### 1. Gather References From the User

Before generating anything, ask the user for:

- **Reference images or sites they're drawn to** — especially from outside the same industry. A restaurant menu layout applied to a fintech page is more distinctive than any "experimental fintech" prompt.
- **What they hate** — "I hate card grids" is more useful than "make it interesting" because it eliminates a convergence attractor.
- **Non-digital references** — architecture, print design, film stills, physical objects, packaging. These import structural ideas from outside the web design distribution.

If the user has no references, generate 5 wildly different structural approaches and use their reactions as the starting signal.

### 2. Create Anti-Reference Board

Name 3-5 specific sites or patterns to explicitly avoid. These are the convergence attractors for this brand category.

Example for a fintech brand:
```
ANTI-REFERENCES (what we are NOT):
1. Stripe.com — elegant but everyone copies it
2. Any site with a hero + 3-column features + testimonials + CTA footer
3. Dark gradients with floating UI screenshots
4. Card grids with icons and 2-line descriptions
5. "Trusted by" logo bars
```

This gives the LLM explicit negative constraints, which are more useful than positive instructions.

### 3. Generate Divergent Variants

Create 3-5 structurally different page variants. **Not color/font swaps — fundamentally different spatial logic.**

Each variant must:
- **Name what convention it fights** — e.g., "fights: centered layouts, even spacing, card grids"
- **Reference an inspiration outside the industry** — e.g., "inspired by: museum exhibition walls" or "inspired by: Bloomberg terminal" or "inspired by: newspaper broadsheet"
- **Be a complete page** (hero through footer) using the brand's tokens from Phase 5
- **Be deployed to HTML** so the user can view in a browser

**Critical rules:**
- Each variant must be structurally incompatible with the others (you couldn't blend them)
- At least one variant should feel uncomfortable or "wrong" — that's often where distinctiveness lives
- Do not refine any variant. First pass only. Polish comes later.

Deploy all variants plus a comparison/index page so the user can view them side by side.

### 4. Kill

Present variants to user. They make binary decisions:

- **Alive** — something about this works
- **Dead** — kill it

Rules:
- **No blending.** "Take the header from V2 and the body from V4" is averaging. Kill one, keep the other.
- **Kill the safe ones.** If a variant feels familiar and comfortable, it's probably convergent. The user's discomfort with a variant is often a signal that it's actually distinctive.
- **One survivor is ideal.** Two survivors maximum. More than two means the filter isn't harsh enough.

### 5. Mutate Within Survivor

Take the surviving direction and introduce 2-3 deliberate **named breaks** — specific violations of design convention. Each break should:

- **Be named** — e.g., "The Misprint" (misregistered type), "The Specimen" (exposed baseline grids), "Colour Rupture" (single strategic colour moment)
- **Fight one specific expectation** — pixel perfection, consistent alignment, finished polish, even spacing
- **Be reversible** — if it doesn't work, remove just that break

Deploy the mutated variants for the user to evaluate.

### 6. Select and Refine

User picks which breaks work and which don't. Now — and only now — refine:
- Typography hierarchy (weight, size, line-height)
- Colour moments (strategic, not systematic)
- Spacing and rhythm
- Content hierarchy
- Responsive behavior

### 7. Document the Composition

Record the compositional identity for DESIGN.md (Phase 6):

```markdown
## Compositional Identity

### Structure
[How sections are organized — e.g., "full-viewport scroll-snap rooms" or "asymmetric editorial columns"]

### What This Brand Fights
[Named conventions this brand deliberately violates — e.g., "card grids, centered layouts, even spacing"]

### Signature Devices
[1-2 visual devices unique to this brand — e.g., "exposed baseline grids," "dimension line annotations," "single-word colour moments"]

### Spatial Logic
[How space is used — e.g., "generous vertical space between sections, dense within sections" or "asymmetric margins, left-heavy"]

### Anti-References
[What this brand must never look like]
```

---

## The Blur Test

At 20% visibility (squint or blur the screenshot), the page's layout silhouette should be **distinguishable from the anti-references**. If a blurred screenshot of your page could be mistaken for a blurred screenshot of Stripe, the composition isn't distinctive enough. Go back to step 5 and introduce more structural breaks.

---

## Outputs

- 3-5 divergent variant HTML files
- Comparison/index page for side-by-side viewing
- Surviving direction with mutations applied
- Compositional identity documentation (for Phase 6)

## Gate

User confirms the composition is distinctive and ready for DESIGN.md documentation. The blur test passes.

---

## What the LLM Should Tell the User

At the start of this phase, be transparent:

> "This is the phase where my limitations are most visible. I'll generate structurally different layouts, but I genuinely can't tell which one is distinctive vs. which one is just competently average. That's your call. Your references, your gut reactions, and your willingness to kill the safe options are what make this work. I'm the generator — you're the filter."

---

## Pitfalls

- **Blending survivors** — This is averaging. Kill one, keep one.
- **Refining too early** — Polish before selection locks in the convergent direction
- **Not enough structural difference** — Color/font swaps aren't variants. Different spatial logic is.
- **Skipping anti-references** — Without knowing what to avoid, the LLM will produce it
- **Ego attachment to any variant** — including the user's. If all variants feel comfortable, none are distinctive enough.

---

## Real-World Example: AutonoLabs

During the AutonoLabs brand build, five named directions were generated:
1. **The Control Room** — Bloomberg terminal, dashboard panels
2. **The Broadsheet** — Newspaper editorial, column layout
3. **The Terminal** — BBS/htop, monospace-heavy, dense
4. **The Exhibition** — Museum walls, Swiss typographic posters
5. **The Dossier** — Intelligence briefing, classified document feel

User killed Broadsheet (too dense) and Terminal (too dense). Exhibition survived. Three sub-mutations were generated within Exhibition:
- **Colour Rupture** — strategic single-colour moments breaking monochrome
- **The Misprint** — misregistered ghost type, offset slugs
- **The Specimen** — type foundry annotations, dimension lines, proof watermarks

The Specimen — the variant that looked most "unfinished" — was selected. The final page bore no resemblance to any default tech landing page. Not because anyone prescribed what it should look like, but because the process systematically prevented convergence at every step.
