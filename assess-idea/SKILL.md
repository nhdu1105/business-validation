---
name: assess-idea
description: Rigorously evaluate and filter EdTech product ideas for feasibility, real customer need, and business alignment, sorting them into pursue / park / kill with evidence-based scoring. Use this skill whenever the user asks to evaluate, assess, prioritize, score, rank, filter, validate, or "sort" ideas, or asks "which of these ideas is worth building", "is this idea any good", or wants to narrow a list down. Trigger even when the user just pastes a list of ideas and asks what you think. Applies desirability-feasibility-viability analysis and RICE scoring against the user's Vietnam K-12 context.
---

# Assess Idea — The Honest Filter

This skill's job is to kill ideas. Most early-stage EdTech ideas fail for predictable, researchable reasons — no real willingness to pay, payer≠user misalignment, unbeatable free alternatives, regulatory exposure, or founder-capacity mismatch. The user is better served by three honestly-scored survivors than fifteen flattered maybes. Do not cheerlead. If every idea scores well, the assessment failed.

## Inputs

Read `project-context.md`, the idea cards (I#), and the research findings (F#). If ideas arrive without evidence hooks or without research context, assess anyway but mark those dimensions "unsupported — desk-validate before trusting this score." Note founder constraints — feasibility is relative to *this founder's* budget, team, and technical capacity, not to a funded startup's.

## Assessment framework

Score each idea on three gates, then compute priority. Every score requires a written justification citing evidence (F#) or explicit reasoning — a number without a reason is theater.

### Gate 1 — Desirability (is the need real?)
Score 1-5 on evidence strength, not idea attractiveness:
- Is there **behavioral evidence** of the need (people already paying for a worse substitute — tutors, workbooks, other apps), or only stated/inferred need? Behavioral > stated. People paying for substitutes is the strongest desk-research signal that exists.
- **Payer test**: does the *payer* (usually the parent) feel this pain enough to pay, regardless of whether the user (student) likes it? Ideas loved by students but invisible to parents score low in Vietnam K-12.
- **Free-alternative test**: what does the user do today for free (YouTube, Facebook groups, Zalo groups, school itself)? Why would they switch?

### Gate 2 — Feasibility (can *this founder* build and distribute it?)
Score 1-5:
- Build complexity vs founder's technical capacity and budget; content-production burden (K-12 content localized to the Vietnamese curriculum is expensive and ongoing — flag any idea that quietly requires a content factory).
- **Distribution feasibility**: how do you reach Vietnamese parents/schools? School B2B sales cycles are long and relationship-driven; parent B2C requires paid acquisition against incumbents. An unbuildable channel fails this gate as surely as unbuildable tech.
- Regulatory exposure: minors' data (Decree 13/2023 and successors), tutoring regulation, content approval. Search to verify current rules if the idea is regulation-sensitive — don't assess regulatory risk from memory.

### Gate 3 — Viability (does the business math plausibly work?)
Score 1-5:
- Sanity-check TAM→SAM→SOM in one short paragraph using research numbers (F#) — bottom-up (number of target students × plausible penetration × price), never top-down percentage grabs.
- Price anchor: what does the payer currently spend on the nearest substitute (tutoring, cram schools)? Price realism in Vietnam is set by these anchors.
- Structural churn: K-12 products churn on graduation and exam cycles by design — does the model survive that?

### Priority score
For ideas passing all gates (no dimension ≤2), compute **RICE** (Reach × Impact × Confidence ÷ Effort) to rank them. State the estimate behind each factor — the point of RICE is forcing explicit estimates, not the arithmetic.

## Verdicts

Sort into exactly three buckets:
- **Pursue** (max 2-3): passes all gates, ranked by RICE, each with its **riskiest assumption** and the *cheapest possible test* for it (parent interviews with a script, a landing-page smoke test, a concierge/manual MVP, a Zalo-group pilot). Recommend testing before building — desk assessment is a filter, not validation.
- **Park**: promising but blocked (needs data, wrong timing, needs scale). State the specific unblock condition.
- **Kill**: state the kill reason in one blunt sentence. Killed ideas go to the context file marked killed, with reason — so they can't zombie back later without new evidence.

## Output format

1. A scoring table (idea, D, F, V, RICE, verdict) for scan-ability.
2. Per-idea verdict blocks with the written justifications — this is where the honesty lives; the table alone is not an assessment.
3. "Next validation steps" for pursued ideas.
4. Offer to update `project-context.md` sections 3, 4 (decision log) and 7 (riskiest assumptions).

## Bias guards

Actively check yourself for: halo effect from well-written idea cards (score the evidence, not the prose), sunk-cost drift toward ideas the user seems attached to, and optimism inflation (if unsure between two scores, take the lower and say why). If the user pushes back on a kill, engage with their argument on evidence — updating on new information is good; softening on pressure is not.
