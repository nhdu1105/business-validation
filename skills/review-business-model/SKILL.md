---
name: review-business-model
description: Design and evaluate business models for the user's Vietnam K-12 EdTech platform based on the functions and ideas already chosen — revenue model selection, Business Model Canvas, pricing, and unit economics. Use this skill whenever the user asks about business models, monetization, revenue, pricing, "how do we make money", subscription vs freemium vs B2B, unit economics, CAC/LTV, or asks to review or stress-test how the product will be commercially viable. Trigger even for casual phrasings like "how should we charge for this" or "would schools pay for it".
---

# Review Business Model — Commercial Architecture

Recommend a business model that fits the *chosen* product ideas and Vietnam K-12 market reality — not a generic SaaS playbook. The core structural fact shaping everything: **the payer (parent or school) is usually not the user (student)**, so value must be legible to the payer, and pricing is anchored to what payers already spend on substitutes (tutoring), not to Western SaaS norms.

## Inputs

Read `project-context.md` — especially the pursued ideas (I#), research findings (F#), and founder constraints. If no idea has been chosen yet, say the model can only be sketched per-candidate-idea, and either do that or suggest finishing assess-idea first. Search for current data where the model depends on it (competitor pricing, payment-method adoption, school procurement rules) rather than asserting from memory.

## Step 1 — Generate 2-3 candidate models

Draw candidates from the EdTech revenue patterns that actually operate in Vietnam/SEA, matched to the product's actors:

- **B2C parent subscription** (monthly/term/annual; term-based aligns with school calendar and exam cycles)
- **Freemium → paid** (free layer for acquisition; be explicit about what converts — in K-12 the converter is usually exam-linked value, not convenience)
- **B2B2C school licensing** (school pays per-student; long relationship-driven sales cycles, procurement realities, but near-zero churn once in)
- **Marketplace / take-rate** (connecting tutors–students–parents; supply-side cold-start is the hard part, and tutoring regulation applies — verify current rules)
- **Hybrid** (e.g., free teacher tools as distribution → parent-paid premium; this "teacher-as-channel" pattern deserves consideration because teacher trust drives parent adoption in Vietnam)
- Treat pure advertising to minors as effectively off the table (regulatory + trust + unit-economics reasons); say so if the user raises it.

For each candidate, one paragraph: how money flows, who the buyer really is, and the single hardest thing about making it work.

## Step 2 — Compare and recommend

Compare candidates on: fit with the chosen idea's core loop, payer willingness-to-pay evidence (F#), sales/distribution feasibility for this founder, churn structure (graduation churn is built into K-12 — models that survive it monetize per-exam-cycle or expand across grades), and regulatory exposure. Recommend one primary model (possibly with a phase-2 evolution) and say plainly why the others lost.

## Step 3 — Business Model Canvas for the recommended model

Fill a full Business Model Canvas (customer segments, value propositions per segment — one for payer, one for user, they differ; channels; customer relationships; revenue streams; key resources; key activities; key partnerships; cost structure). Vietnam-specific blocks to get right:

- **Channels**: Zalo (parent communication default), Facebook groups, teacher referral, school partnerships, app stores; state which channel is the *primary* acquisition bet and why.
- **Payments**: MoMo/ZaloPay/bank transfer/carrier billing; card penetration is low — a checkout that assumes cards is a silent conversion killer.
- **Cost structure**: flag Vietnamese-curriculum content production as an ongoing cost line, not a one-time build, if the product needs it.

## Step 4 — Unit economics sketch

Build a simple, honest bottom-up sketch with stated assumptions (ranges, not false precision):
price (anchored to substitute spend) → gross margin → CAC by channel (estimate with reasoning) → expected lifetime given structural churn → LTV → LTV:CAC. If the sketch only works with heroic assumptions, say so — a model that needs 5% freemium conversion and 3-year retention in a graduation-churn market is a fantasy, and this skill's value is saying that before code gets written.

## Output structure

```markdown
# Business Model Review — [product name]
## 1. Candidate models considered (with the hard problem of each)
## 2. Recommendation & reasoning
## 3. Business Model Canvas (recommended model)
## 4. Pricing logic & anchors
## 5. Unit economics sketch (assumptions labeled)
## 6. Top 3 commercial risks & how to de-risk cheaply
```

Close by offering to update `project-context.md` section 5 and the decision log, and note that the chosen model constrains the backlog (e.g., B2B2C requires an admin/reporting surface; subscriptions require billing + entitlements) — which is exactly what create-backlog reads next.
