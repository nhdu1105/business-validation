---
name: inspire-idea
description: Generate evidence-grounded product ideas, use cases, and customer-need hypotheses for the user's Vietnam K-12 EdTech platform, based on industry-research findings. Use this skill whenever the user asks for ideas, features, use cases, "what could we build", brainstorming, opportunities, or inspiration for their EdTech platform — even casual prompts like "give me some ideas from that research" or "what problems could we solve for parents". Requires research findings as input; if none exist, direct the user to run industry-research first.
---

# Inspire Idea — Evidence-Grounded Ideation

Generate ideas that are *traceable to evidence*, not brainstorm confetti. The difference between this skill and generic brainstorming: every idea must cite at least one numbered research finding (F#) or documented pain point as its reason to exist. An idea with no evidence hook doesn't get written down — it gets replaced by one that has one.

## Input discipline

Read `project-context.md` and/or the industry-research report first. If neither exists in the conversation, stop and tell the user to run industry-research first (or paste findings) — ideating without evidence produces exactly the un-validated idea pile this pipeline exists to prevent. Also note founder constraints from the context file (budget, team, technical capacity): a solo founder shouldn't receive ideas that require a 20-person content studio, unless clearly flagged as "requires scale."

## How to generate (frameworks, applied not name-dropped)

Work through these lenses in order — they exist to force breadth, because unstructured ideation clusters around the first obvious idea:

1. **Jobs-to-be-Done per actor.** For each actor (student, parent, teacher, school admin, tutor), articulate functional jobs ("pass the grade-10 entrance exam"), emotional jobs ("stop feeling anxious that my child is falling behind"), and social jobs ("be seen as a good parent"). In Vietnam K-12 the parent's emotional/social jobs often drive purchase more than the student's functional job — ideas that serve only the student but ignore the payer tend to die at checkout.
2. **Gap inversion.** Take each gap/barrier finding from the research and invert it: a barrier for incumbents is a wedge for entrants (e.g., if regulation constrained offline tutoring, what compliant substitute does that demand flow into?).
3. **Analogous-market transfer.** Look at what worked in exam-driven K-12 markets (Korea, China pre/post-regulation, India, Japan) and reason explicitly about transferability — mechanism, not surface features. Say *why* it would or wouldn't transfer to Vietnam.
4. **Learning-science first.** Prefer ideas built on mechanisms with strong empirical effect sizes — retrieval practice, spaced repetition, formative feedback loops, mastery learning, tutoring — and be suspicious of ideas whose core loop is engagement theater (streaks, points) without a learning mechanism underneath. Cite the mechanism in the idea card.
5. **Business-model seeds.** For each idea, note the most natural revenue logic (B2C parent subscription, B2B2C school licensing, marketplace take-rate, freemium→paid) even if rough — it prevents ideas that are structurally unmonetizable in Vietnam's willingness-to-pay reality.

Aim for **10–15 ideas across at least 3 different actors** — resist the pull toward "another learning app for students." Include at least one deliberately contrarian or unfashionable idea; the point of breadth is to give assess-idea real choices.

## Idea card format

ALWAYS use this exact card per idea:

```markdown
### [ID: I1] Idea name
- **One-liner**: what it is, in one sentence a parent would understand
- **Target actor & payer**: who uses it / who pays (state if different)
- **Job-to-be-done**: the functional + emotional job it serves
- **Evidence hook**: which findings support it (cite F# + one line why)
- **Learning/behavior mechanism**: the empirically-supported mechanism at its core (or "commercial mechanism" if it's not a learning product)
- **How it works**: 3-4 sentences on the core loop
- **Why now**: what changed (regulation, tech, behavior) that makes this timely
- **Analog**: closest existing example anywhere in the world + transferability note
- **Riskiest assumption**: the single belief that, if wrong, kills the idea
- **Natural business model seed**: one line
```

## Tone and honesty

Be generative here, not judgmental — assessment is assess-idea's job, and prematurely filtering kills good weird ideas. But do not fabricate evidence hooks: if an idea excites you and no finding supports it, mark the evidence hook as "none — intuition only" so assess-idea treats it accordingly. After presenting the cards, offer to record the full list in `project-context.md` section 3 (all ideas status: "unassessed") and suggest running assess-idea next.
