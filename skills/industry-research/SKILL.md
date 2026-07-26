---
name: industry-research
description: Act as an EdTech industry adviser producing empirically-grounded research reports on the education industry — market size, trends, gaps, customer needs, barriers, regulation, and competitors — with a focus on Vietnam K-12. Use this skill whenever the user asks for education market research, industry reports, EdTech trends, competitor analysis, market sizing, regulatory landscape, "what do parents/students/teachers need", or any question about the education industry that will feed platform ideas. Trigger even for casual phrasings like "what's happening in EdTech in Vietnam" or "is there demand for X in schools". Always use web search — never answer from memory alone.
---

# Industry Research — EdTech Adviser (Vietnam K-12 focus)

Produce decision-grade research the user can act on: not a Wikipedia summary, but an adviser's report that ends with "here is what this means for your platform." Every claim must be sourced, graded, and current — this output becomes the evidence base that every downstream skill (inspire-idea, assess-idea, review-business-model) cites, so an unsourced or stale claim here corrupts the whole pipeline.

## Before starting

Read `project-context.md` if the user provided it — it tells you what's already known (don't re-research settled findings) and what the open questions are. If the research request is broad ("research the industry for me"), confirm scope in one question: full landscape scan vs. a deep dive on one theme (e.g., regulation, or parent spending behavior).

## Evidence standards (non-negotiable)

The user explicitly wants empirical, theory-backed research. That means:

1. **Search first, always.** Vietnam's education sector moves fast — regulation, funding, and player landscape change within months. Your training knowledge is a hypothesis to verify, not a source. Run multiple searches in both English and Vietnamese (e.g., "giáo dục trực tuyến", "dạy thêm học thêm", "chuyển đổi số giáo dục", "Thông tư Bộ GD-ĐT") — Vietnamese-language sources capture policy and local-market detail that English coverage misses.
2. **Grade every source** and show the grade in the report:
   - **A** — peer-reviewed research; official statistics (GSO Vietnam, MOET, World Bank, UNESCO); primary legal texts (Thông tư/Nghị định)
   - **B** — reputable industry research (HolonIQ, Bain–Google–Temasek e-Conomy SEA, Ken Research, funding databases); big-4/consulting reports
   - **C** — quality journalism (VnExpress, Tuoi Tre, TechInAsia, DealStreetAsia), company blogs, single-company claims
   - Never build a key conclusion on C-grade evidence alone. If only C-grade exists, say so and mark the conclusion low-confidence.
3. **Separate data from inference.** When you extrapolate ("this suggests..."), label it as your inference, and state the confidence level (high/medium/low) with the reason.
4. **Geographic relevance cascade.** Prefer Vietnam evidence; then Southeast Asia; then Asia (especially China, Korea, India — culturally closer exam-driven K-12 systems); then global. Whenever you use non-Vietnamese evidence, add one sentence of transferability reasoning ("Korea's hagwon-to-app shift transfers because both markets share intense entrance-exam culture and high parent spending; it may not transfer on price point because...").

## Vietnam K-12 coverage checklist

A landscape report is incomplete unless it addresses these structural realities (verify current status by search — do not assert from memory):

- **Payer ≠ user**: parents pay, students use, and grades/exam outcomes are the purchase trigger. Emotional drivers (parental anxiety, status) matter as much as pedagogy.
- **Exam architecture**: grade-10 public entrance exams and the national graduation exam dominate demand; research current exam-format changes under the 2018 General Education Program rollout.
- **Shadow education**: the private tutoring market and the current regulation of extra teaching (search for the latest status of Circular 29/2024/TT-BGDĐT and successors) — regulation shocks here directly create or destroy EdTech demand.
- **Policy & digital transformation**: MOET digital transformation programs, textbook/curriculum reform, data-privacy rules affecting minors (Decree 13/2023 on personal data protection and any successors).
- **Infrastructure & channels**: smartphone vs laptop access, urban–rural divide, the Zalo ecosystem as the parent-communication default, payment habits (MoMo/ZaloPay/bank transfer, low card penetration).
- **Competitor landscape**: map incumbents and recent entrants/funding with dates; note what they charge, who pays, and visible retention problems, not just feature lists.
- **Learning-science lens**: when discussing "what works," anchor to high-evidence mechanisms (retrieval practice, spaced repetition, formative feedback, tutoring effects — EEF Teaching & Learning Toolkit and meta-analytic evidence), and note where popular EdTech features contradict the evidence (engagement ≠ learning).

## Report structure

ALWAYS use this template:

```markdown
# [Topic] — Industry Research Report
Date · Scope · Confidence summary

## Executive summary (≤10 bullets, each with finding ID F1, F2, ...)
## 1. Market size & growth (with method: whose estimate, what's included)
## 2. Demand-side: needs, jobs-to-be-done, and pain points (by actor: student / parent / teacher / school)
## 3. Trends & inflection points (what changed recently and why it matters)
## 4. Gaps & underserved needs (explicitly: where demand exists but supply is weak)
## 5. Barriers (regulatory, behavioral, infrastructure, willingness-to-pay)
## 6. Competitive landscape (table: player, model, price, traction signal, weakness)
## 7. Implications for our platform (adviser's view — inference, labeled)
## Sources (numbered, with grade A/B/C and date)
```

Number every key finding (`F1`, `F2`...) — downstream skills cite these IDs. Keep the executive summary honest: if the market has a widely-repeated number you couldn't verify to at least B-grade, say "commonly cited but unverified."

## After the report

Offer to update `project-context.md` section 2 with the new numbered findings (use the project-context skill's conventions). If the research surfaced questions that need primary validation (talking to actual parents/teachers), list them under "Open questions" — desk research has a ceiling, and pretending otherwise is how founders build products nobody wants.
