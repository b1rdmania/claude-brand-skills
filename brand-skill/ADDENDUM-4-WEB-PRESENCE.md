# ADDENDUM 4: THE CONVERGENCE PROBLEM — WHY LLMs REVERT TO MEAN IN DESIGN

**Date:** 2026-02-07
**Context:** Observed after executing the full brand skill for three different brands, all producing visually indistinguishable web presences

---

## The Problem

Build a landing page for a venture studio. Build one for a composting platform. Build one for a quantitative fund. Give each its own color palette, its own type system, its own emotive narrative, its own design philosophy. Run the full seven-phase brand skill on each.

The three pages will be interchangeable.

Same hero structure. Same visual weight. Same rhythm. Same spatial logic. Different logos, different hex values, same page. You could swap the logos between them and nothing would feel wrong. This is not a hypothetical — it was confirmed empirically during the AutonoLabs build.

---

## Why This Happens

An LLM generates output by predicting the most probable next token. This is a statistical operation. The output doesn't drift toward the average — it starts there and stays there, because the average is what the mechanism is optimized to find.

"Dark tech landing page" has a remarkably tight center in the training data. Thin display type, left-aligned. Muted subhead. Accent-colored CTA. Horizontal dividers. Card grids. Footer columns. This isn't the model being lazy. It's the model being accurate: this IS what the statistical center of "good dark tech landing page" looks like. The problem is that the center is shared. Every brand that asks for "good" gets the same good.

Design tokens don't change this. Tokens define what materials to use — which colors, which fonts, which spacing values. They don't define what to build with those materials. The LLM takes the tokens, applies them to the statistical center of the relevant page category, and produces a well-dressed version of the same default layout. Three brands with three completely different token sets still converge to the same composition, because the composition comes from the distribution, not the tokens.

The gap is between ingredients and cooking. The skill produces excellent ingredients. It has no opinion about the meal.

---

## Why Prescribing Solutions Makes It Worse

The instinct is to fix convergence by telling the model what to do differently. Add specific techniques. Prescribe particular disruptions. Give it a framework: "do this, then break it in these ways."

This fails — and understanding why it fails is the entire point of this addendum.

When you prescribe a technique, you define a new target distribution. The model converges to the center of that distribution instead. Tell it "add typographic disruptions" and it will generate the average of typographic disruptions across its training data. Tell it "use asymmetric layout" and it will generate the most probable version of asymmetric layout. You haven't escaped the convergence problem. You've moved it.

This is recursive. Any instruction specific enough to produce a distinctive result is specific enough to become a new center. "Be bold" converges to the average of bold. "Break the grid" converges to the average of grid-breaking. Even "surprise me" converges to the average of surprise — which is, by definition, unsurprising.

The problem isn't that the model lacks good techniques. It's that the mechanism of next-token prediction is fundamentally a centring operation. You cannot instruct your way out of a statistical property of the system. A prompt that says "don't converge" will converge on what not-converging looks like.

---

## What The Mechanism Cannot Do

It helps to be precise about the limitation. An LLM can execute any individual design decision with competence. It can set type beautifully. It can build a grid. It can apply a color palette with sophistication. It can write CSS that does exactly what you describe.

What it cannot do is *choose* which decisions to make. Choice — in the design sense, the act of selecting one possibility over others based on taste, context, and intent — requires a vantage point outside the distribution. The model is inside the distribution. It can tell you what's most probable. It cannot tell you what's most interesting, because interestingness is defined relative to an observer, and the model is not an observer. It's a function.

This is why two LLM-generated pages can use completely different colors, different fonts, different copy, and still feel identical. The *decisions* are the same. Which element goes where, how much space around it, what rhythm the sections follow, where the eye moves, what's big and what's small — these compositional choices all resolve to the same center because the model has no reason to choose otherwise. It has been asked to build a good page, and this is what a good page most probably looks like.

Human designers solve this by having opinions that come from outside the problem. They've seen a building they liked, or a poster from the 1960s, or the way a particular restaurant menu uses space. They import structural ideas from unrelated domains and apply them in ways that feel fresh because the combination is rare. An LLM can do this if told to — but the *telling* is the creative act. The model is the hand, not the eye.

---

## The Only Escape Is Process, Not Instruction

If convergence is a property of the mechanism, and if prescribing techniques just moves the convergence point, then the solution cannot live inside the prompt. It has to live in the process wrapped around the prompt.

The distinction: instead of telling the model *how* to be distinctive (which it will average), you structure a process where distinctiveness can emerge through iteration and selection. You don't describe the destination. You create conditions where the destination reveals itself.

This means generating multiple structurally different outputs, not as variations on a theme but as genuinely independent directions. It means putting them in front of a human who can react viscerally — not "tell me what you want" but "here are five things, which ones do you hate?" It means killing directions entirely rather than blending them, because blending is averaging and averaging is convergence. It means exploring within a surviving direction rather than across all of them, because depth in one direction produces more surprise than breadth across many.

The human's role shifts. They are not the brief-writer. They are not describing what they want, because any description will be averaged by the model. They are the selector. They see outputs and make binary decisions: alive or dead. Their taste — which exists outside the training distribution — is the selection pressure that pushes the output away from the mean.

This is essentially evolutionary. Generate diversity. Apply selection pressure. Mutate within the survivors. Select again. The result is not something anyone designed. It's something that emerged from a process that systematically prevented convergence at every step.

---

## What This Means For The Skill

The brand skill's first seven phases are a pipeline: narrative feeds philosophy, philosophy feeds visual direction, visual direction feeds the mark, and so on. This linearity works for those phases because each is a refinement of the previous one.

But when the skill reaches the web presence — the moment tokens become a visible page — a pipeline guarantees convergence. Each step in a linear process collapses possibility. Brief becomes tokens, tokens become layout, layout becomes page. At every transition, the model selects the most probable interpretation, and the most probable interpretation is the average.

The skill needs to shift from pipeline to tree at this stage. Not a prescribed set of branches — that would just be a more complex pipeline — but a structural commitment to generating multiple possibilities, comparing them visually, and letting human selection drive the direction. The specific branches will be different for every brand. They should be. The point is not which branches exist but that branching happens at all.

During the AutonoLabs session, five named directions were generated from cross-category references, deployed to a comparison page, and evaluated visually. Two were killed. The surviving direction was explored through three sub-variants, each pushing a different dimension of disruption. Elements from the sub-variants were selectively pulled back into the main direction. The final page bore no resemblance to the generic first attempt — not because anyone prescribed what it should look like, but because the process systematically prevented it from looking like the default.

That process — not its specific outputs — is what the skill needs to encode. The outputs will be different every time. The process of divergence, comparison, selection, and mutation is what makes them different.

---

*The convergence problem is not a bug in LLMs. It is their central operating principle applied to a domain where the center is not the goal. No instruction can override it. Only a process that treats the model as a generator — and the human as a selector — can produce output that doesn't look like everything else.*
