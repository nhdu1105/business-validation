---
name: create-backlog
description: Turn validated EdTech platform ideas and the chosen business model into a prioritized product backlog, and — after the user confirms which items to build — generate a Claude Code-ready implementation spec document. Use this skill whenever the user asks to create a backlog, user stories, epics, an MVP scope, a development plan, a PRD, a spec, "what should we build first", or asks for a document that Claude Code can use to build the product. This is a strict two-phase skill where phase 1 outputs the backlog list for confirmation, and phase 2 (only after explicit user confirmation) outputs the implementation spec.
---

# Create Backlog — From Decisions to Buildable Spec

Translate everything upstream (pursued idea, business model, constraints) into (1) a prioritized backlog the user confirms, then (2) a spec document Claude Code can implement without guessing. The two-phase gate is strict because the spec is expensive to produce and expensive to redo — never generate phase 2 until the user has explicitly confirmed the backlog scope.

## Inputs

Read `project-context.md` — the pursued idea (I#), business model (section 5), founder constraints, and riskiest assumptions. If no idea has been pursued or no business model chosen, say which upstream step is missing; a backlog for an unvalidated idea is a beautifully organized waste of time, but proceed if the user insists (mark the backlog "pre-validation").

---

## Phase 1 — The backlog

### Structure

Organize as **Epics → User stories**, where every story earns its place by tracing to the product's core loop, the business model's requirements, or a riskiest-assumption test:

```markdown
## Epic E1: [name] — why it exists (traces to I#/model/assumption)
| ID | User story | Acceptance criteria (testable) | Priority | Effort | Depends on |
| S1 | As a [actor], I want [action], so that [outcome] | Given/When/Then, 2-4 criteria | M/S/C/W | S/M/L | — |
```

- **Prioritize with MoSCoW** (Must/Should/Could/Won't-now) and draw an explicit **MVP line**: the Musts must form a complete loop for ONE actor achieving ONE job end-to-end. An MVP that half-serves three actors serves nobody.
- Include the unglamorous epics the business model forces: auth/accounts (remember parent-account ↔ child-profile structure if payer≠user), payments/entitlements matching the chosen revenue model (Vietnamese payment rails, not card-only), Vietnamese-language UI, minors' data-privacy compliance basics, and an analytics event spine (or the riskiest assumptions can never be measured).
- Resist scope gravity: if the Must list exceeds roughly 12-15 stories, challenge it — what can move below the MVP line and still leave the core loop intact?

### Phase 1 output and the gate

Present the backlog, state the MVP line and the reasoning, list open product decisions the spec will need answered (e.g., "web app or mobile-first? Zalo Mini App?"), then **stop and ask the user to confirm scope** (confirm all Musts / edit / re-scope). Do not proceed on silence or ambiguity.

---

## Phase 2 — The Claude Code spec (only after confirmation)

The audience is Claude Code implementing without you in the room. Everything ambiguous becomes a guess; everything unstated becomes an omission. Write `SPEC.md` as a downloadable file with exactly this structure:

```markdown
# [Product name] — Implementation Spec
## 1. Product overview & core loop (3-4 sentences + the ONE user journey the MVP must nail)
## 2. Tech stack (recommended, with one-line rationale each — respect founder capacity; boring beats clever)
## 3. Data model (entities, fields with types, relationships — explicit parent↔child-account structure if applicable)
## 4. Features, per confirmed backlog story:
   ### S# — [story name]
   - Behavior description (unambiguous prose)
   - Acceptance criteria (Given/When/Then — copied and sharpened from backlog)
   - UI notes (screen, key states: empty/loading/error)
   - API surface if applicable (endpoint, method, request/response shape)
## 5. Non-functional requirements (Vietnamese locale/UTF-8 throughout, mobile-first, target devices, performance floor, minors' data handling)
## 6. Out of scope (explicit — everything below the MVP line, so Claude Code doesn't helpfully build it)
## 7. Build order (sequence respecting dependencies; each step ends in something runnable)
## 8. Seed/sample data description (realistic Vietnamese K-12 examples: grade levels, subject names, sample exercises)
```

Spec-writing rules:
- Recommend a concrete, mainstream stack suited to the founder's capacity (e.g., a single well-supported full-stack framework + managed DB + managed auth) unless the user has stated preferences — and ask about stated preferences before phase 2 if unknown.
- Every acceptance criterion must be checkable by running the app. "User-friendly onboarding" is not a criterion; "a new parent account reaches the child's first exercise in ≤3 screens" is.
- Where a product decision was left open in phase 1 and the user didn't decide, choose the simplest option and record it in a `## Decisions made in this spec` note at the top so nothing is silently assumed.
- Keep learning-mechanism fidelity: if the product's core is, say, spaced repetition, specify the actual scheduling rule (even a simple one) — don't leave the empirically-important mechanism as "TBD algorithm."

Close by offering to update `project-context.md` section 6 with backlog status and the spec filename.
