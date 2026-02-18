# InfraSingularity Brand Project - Retrospective

**Project Duration:** 2026-02-11 to 2026-02-13
**Phases Completed:** 0-5 (Audit, Narrative, Philosophy, Mark, Wordmark, Design System)

---

## Problems Encountered & Solutions

### Phase 4: Wordmark Development

#### Problem 1: SVG Letter-Spacing Rendering Bug
**What happened:**
- Created wordmark variants using `letter-spacing` with em units (e.g., `-0.39em`)
- Result: Text completely overlapped and became illegible
- User response: "lol these are all fucked" (with screenshot)

**Root cause:**
- SVG interprets letter-spacing differently than CSS
- Em units in SVG are unreliable and produce broken results
- Should have used pixel values from the start

**Solution:**
- Changed to pixel-based letter-spacing (e.g., `-0.4px`)
- Text rendered correctly

**Learning:**
- **Always use pixel values for SVG text letter-spacing**
- Test SVG text rendering before showing variants
- Don't assume CSS units work the same in SVG

**Workflow improvement needed:**
- Add SVG-specific typography guidelines to Phase 4 workflow
- Include test/validation step before presenting variants

---

#### Problem 2: Text Size Relative to Mark
**What happened:**
- Initial wordmark used 36px text with 32px gap from mark
- User feedback: "it probably needs to be bigger against the logo"
- Had to iterate twice: 36px → 40px and 32px gap → 16px gap

**Root cause:**
- Didn't properly consider optical balance between mark (64px) and text
- Gap was too wide, making lockup feel disconnected
- Text was too small relative to mark prominence

**Solution:**
- Increased text to 40px (closer to mark height)
- Reduced gap to 16px (tighter, more unified lockup)
- Created comparison showing multiple size/spacing options

**Learning:**
- **Default to larger text than you think** - marks often dominate
- **Tighter spacing = more unified lockup** - especially for "density" aesthetics
- **Always show size/spacing variations** - not just one option

**Workflow improvement needed:**
- Phase 4 should include step to create 3-4 lockup spacing/sizing variants
- Provide guidance on optical balance: text should be 60-75% of mark height
- Include spacing ratio guidelines (tight: 0.25x mark height, medium: 0.5x, loose: 0.75x)

---

#### Problem 3: Purple Dot Positioning on "i"
**What happened:**
- Tried to place purple circle on the dot of "i" in "Singularity"
- Couldn't accurately position it relative to font rendering
- User: "F*ck my eyes" - positioning was arbitrary/wrong

**Root cause:**
- SVG circle positioned with absolute coordinates
- Font rendering determines actual glyph position dynamically
- Can't manually position decorative elements on specific font features accurately

**Solution:**
- Abandoned "i" dot variants
- Used purple full stop at END of word instead (easier to position, cleaner)

**Learning:**
- **Don't try to position decorative elements ON font glyphs** in SVG
- **Use simpler, end-of-line accents** instead of mid-word
- If you need glyph-specific decoration, use font editing tools, not SVG

**Workflow improvement needed:**
- Add warning in Phase 4 about decorative element positioning limitations
- Suggest accent placements that work: end-of-word, underlines, separate decorative marks

---

#### Problem 4: Created Too Many Variants
**What happened:**
- Created 12 wordmark variants exploring different weights/combinations
- User: "I feel I'm having to do too much here"
- Wasn't following Phase 4 workflow properly

**Root cause:**
- Didn't read/follow the workflow guideline of "3-4 focused variants"
- Tried to be comprehensive instead of strategic
- Made user do work of narrowing down too many options

**Solution:**
- Acknowledged mistake
- Pivoted to focused approach: 4 variants exploring Light/Medium weights only
- Based on user's stated preference from previous feedback

**Learning:**
- **Follow the workflow guidelines** - they exist for a reason
- **3-4 variants is the sweet spot** - not 10+
- **Focused exploration > comprehensive exploration** - narrow the question first
- Ask user to help narrow direction BEFORE creating many variants

**Workflow improvement needed:**
- Make the "3-4 variants" rule more prominent in Phase 4 workflow
- Add step: "Before creating variants, clarify with user: what variable should we explore?" (weight, style, spacing, etc.)
- Include warning: "More variants = more user work"

---

### Phase 5: Font Pairing

#### Problem 5: First Round Was Generic/Didn't Work
**What happened:**
- Initial pairings: Zilla Slab, Merriweather, Figtree, Playfair Display
- User: "I don't think those work."
- These were "professionally recommended" but felt wrong for the brand

**Root cause:**
- Recommendations were generic "what pairs with geometric sans" advice
- Didn't consider institutional/technical/fintech context
- Didn't research what actual similar brands use
- Serif pairings felt wrong for technical content

**Solution:**
- Started over with deeper research
- Focused on fintech/technical brand typography
- Looked at what Stripe, Figment, Kiln actually use
- Researched fonts specifically for institutional + screen reading

**Learning:**
- **Generic pairing advice doesn't account for brand context**
- **Research competitor/similar brand choices** - they've already solved this problem
- **For technical brands, sans-serif body text is non-negotiable** - serifs reduce screen readability
- Professional recommendations need contextual filtering

**Workflow improvement needed:**
- Phase 5 should include competitor typography research step
- Add industry-specific font research (fintech, technical, consumer, luxury, etc.)
- Provide pre-researched font lists by industry/use case

---

#### Problem 6: Random Font Selection Without Methodology
**What happened:**
- User called me out: "You're just putting random fonts in here. You're not doing any kind of process to check which ones go together. There are various tools, aren't they?"
- I was guessing based on general knowledge, not using systematic tools

**Root cause:**
- Didn't use font pairing tools (Fontpair, Typewolf, Pair & Compare)
- Didn't apply typography methodology (x-height analysis, contrast principles)
- Relied on "fonts I've seen before" instead of research
- No systematic evaluation process

**Solution:**
- Did proper web research to find:
  - Font pairing databases and tools
  - Typography pairing methodology (x-height, weight, contrast)
  - Fintech typography guides (2026 trends, screen optimization)
  - Outfit-specific pairing recommendations from professional resources
- Created 10 evidence-based options with rationales

**Learning:**
- **Always use tools/databases first** - don't guess
- **Have a methodology** - x-height compatibility, contrast analysis, use case fit
- **Show your research sources** - builds trust and allows user to verify
- **Rationale matters** - "why does this work" not just "here are options"

**Workflow improvement needed:**
- **CRITICAL: Add required research step to Phase 5 workflow:**
  1. Search font pairing databases (Fontpair, Typewolf, Google Fonts pairings)
  2. Research industry-specific typography (fintech, tech, etc.)
  3. Apply x-height and contrast methodology
  4. Check what similar brands use
  5. Create evidence-based shortlist (max 10 options)
- Include links to pairing tools in workflow
- Add typography methodology reference doc

---

#### Problem 7: Multiple Rounds of Elimination
**What happened:**
- Created 10 options
- User eliminated: Space Grotesk, Manrope, Space Mono
- Then eliminated: Inter
- Ended with 7, eventually chose Figtree (which was in original list!)

**Root cause:**
- Didn't ask user to help narrow criteria first
- Created broad options without clear filtering principles
- User had to do work of elimination through multiple rounds

**Solution:**
- Eventually landed on Figtree - geometric harmony with Outfit
- Through research process, understood WHY it worked (not just "it looks nice")

**Learning:**
- **Ask user for constraints/preferences upfront**: "Do you want sans-serif only? Should it be geometric or grotesque? Do you want high contrast or cohesion?"
- **Eliminate before creating** - not after
- **Research process was valuable** even though final choice was in original list - we understood the reasoning

**Workflow improvement needed:**
- Add Phase 5 step: "Discuss constraints with user before research"
  - Sans-serif vs serif vs mixed?
  - Geometric cohesion vs contrast?
  - Industry expectations vs distinctive?
  - Primary use case (web, print, technical docs)?
- Use constraints to filter research results
- Present 5-7 options max (not 10+)

---

## What Went Well

### Phase 3: Mark Development
- Iterative process worked well (v10 and v11 series)
- User's feedback on "density IS the brand" was clear direction
- Final v11d successfully evolved original mark without starting over
- Documentation of iterations helped user see the journey

### Phase 4: Wordmark (After Corrections)
- Purple full stop concept was immediately liked
- Size/spacing refinement with multiple options worked well
- Final lockup (Option D: 16px gap, 40px text) was decisive

### Phase 5: Design System
- Comprehensive DESIGN.md was well-received
- Design system specimen HTML was valuable visual reference
- Color derivation from mark felt coherent

### Process
- Sharing to Notion for team review worked smoothly
- Iterative refinement based on feedback was effective
- User's direct feedback ("these are fucked", "too generic") accelerated corrections

---

## Key Learnings for Brand Skill Workflow

### High-Priority Additions:

1. **Phase 4 - SVG Typography Guidelines:**
   - Use pixel values for letter-spacing, not em units
   - Test SVG text rendering before presenting
   - Provide default lockup spacing ratios (tight/medium/loose)
   - Show 3-4 size/spacing variants, not just one
   - Warn about decorative element positioning on glyphs

2. **Phase 5 - Font Pairing Research Protocol:**
   - **REQUIRED:** Use font pairing tools (Fontpair, Typewolf, Pair & Compare)
   - Research competitor/similar brand typography first
   - Apply x-height and contrast methodology
   - Research industry-specific needs (fintech, technical, luxury, etc.)
   - Include rationale with every recommendation ("why this works")
   - Present 5-7 options max, with research sources cited

3. **Phase 5 - User Constraints Discussion:**
   - Before font research, discuss with user:
     - Sans-serif vs serif preference?
     - Cohesion vs contrast approach?
     - Primary use case (web, print, technical)?
     - Industry expectations to match or avoid?
   - Use constraints to filter research results
   - Reduces elimination rounds

4. **General - Variant Discipline:**
   - Enforce "3-4 focused variants" rule across all phases
   - Ask user to narrow exploration variable before creating variants
   - Quality > quantity - strategic exploration > comprehensive exploration

### Medium-Priority Additions:

5. **Phase 4 - Lockup Spacing Guidelines:**
   - Text should be 60-75% of mark height for optical balance
   - Gap ratios: tight (0.25x), medium (0.5x), loose (0.75x) of mark height
   - Default to tighter spacing for "density" aesthetics
   - Always show 3 spacing options

6. **Phase 5 - Industry Font Research Library:**
   - Pre-compiled lists:
     - Fintech/banking typography (institutional, trustworthy)
     - Tech/SaaS typography (modern, readable)
     - Luxury brand typography (elegant, distinctive)
     - Technical/developer tools (monospace considerations)
   - Include actual brand examples
   - Update yearly based on trends

7. **All Phases - Validation Steps:**
   - Add "validate before presenting" steps
   - Test SVGs, check responsive sizing, verify color contrast
   - Reduces user-facing errors

---

## Recommendations for Brand Skill Updates

### Immediate (High Impact):

1. **Add to Phase 4 Workflow (Wordmark & Lockups):**
   ```markdown
   ## SVG Typography Rules
   - ⚠️ ALWAYS use pixel values for letter-spacing (e.g., -0.4px), NEVER em units
   - Test SVG rendering before presenting variants
   - Create 3-4 lockup variants showing size and spacing options

   ## Lockup Spacing Guidelines
   - Text size: 60-75% of mark height for optical balance
   - Gap ratios: tight (0.25x mark height), medium (0.5x), loose (0.75x)
   - Default to tighter for "density" aesthetics, looser for "breathing room"

   ## Decorative Elements
   - ⚠️ Don't position decorative elements ON font glyphs (e.g., "i" dots)
   - Use end-of-line accents, underlines, or separate marks instead
   ```

2. **Add to Phase 5 Workflow (Design System):**
   ```markdown
   ## Font Pairing Research Protocol (REQUIRED)

   ### Step 1: Discuss Constraints with User
   - Sans-serif vs serif preference for body text?
   - Cohesion (similar style) vs contrast (serif + sans)?
   - Primary use case: web UI, technical docs, print, mixed?
   - Industry context: fintech, tech, luxury, creative?

   ### Step 2: Research (All Required)
   - [ ] Check font pairing databases (Fontpair, Typewolf, Google Fonts pairings)
   - [ ] Research competitor/similar brand typography
   - [ ] Apply x-height and contrast methodology
   - [ ] Look up industry-specific typography guides (fintech, tech, etc.)

   ### Step 3: Create Evidence-Based Shortlist
   - Max 5-7 options (NOT 10+)
   - Include rationale for each ("why this works")
   - Cite research sources (builds trust)
   - Show visual comparisons

   ### Font Pairing Tools:
   - Fontpair: https://www.fontpair.co/
   - Typewolf: https://www.typewolf.com/
   - Pair & Compare: https://www.pairandcompare.net/
   - Google Fonts Pairing: https://www.figma.com/google-fonts/

   ### Typography Methodology:
   - X-height compatibility: Similar x-heights create cohesion
   - Contrast: Different styles (serif + sans) create hierarchy
   - Weight variation: Same font family with different weights
   - Use case: Sans-serif essential for technical/screen reading
   ```

3. **Create New Reference Doc: `TYPOGRAPHY-RESEARCH.md`**
   - Industry font recommendations (fintech, tech, luxury, etc.)
   - Font pairing methodology deep dive
   - Links to research tools
   - Case studies of successful brand typography

### Future Improvements:

4. **Phase 5.5 Enhancement (Composition):**
   - Could help prevent font issues by showing system in context earlier
   - Validates typography choices with real layouts

5. **Validation Checklist (All Phases):**
   - Add pre-delivery checklist: SVG rendering, color contrast, responsive sizing
   - Reduces user-facing bugs

---

## Conclusion

**What worked:**
- Iterative feedback loops
- User's direct communication about problems
- Research-driven solutions
- Documentation of process

**What needs improvement:**
- Font pairing methodology (now added)
- SVG-specific technical knowledge (now documented)
- Following variant discipline (now emphasized)
- Pre-work to narrow options (now in workflow)

**Impact:**
Despite problems, we delivered a strong brand system. The issues were primarily process/methodology, not creative direction. These learnings will make Phase 5 (font pairing) and Phase 4 (SVG wordmarks) significantly smoother for future projects.

The user's willingness to call out problems directly ("you're just guessing", "these are fucked") accelerated corrections and improved the final output.

---

**Document Status:** Retrospective complete - ready to integrate learnings into brand skill workflow.
