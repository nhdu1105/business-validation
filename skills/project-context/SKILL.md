---
name: project-context
description: Initialize, read, or update the project-context.md file that serves as the single source of truth for the user's Vietnam K-12 EdTech platform project. Use this skill whenever the user starts a new session on their EdTech project, uploads or mentions project-context.md, asks "where are we", wants a project status summary, or whenever any other EdTech pipeline skill (industry-research, inspire-idea, assess-idea, review-business-model, create-backlog) produces output that should be saved into project memory. Also use it when the user makes a decision (picking an idea, confirming a business model, killing a direction) that future sessions need to remember.
---

# Project Context — Pipeline Memory

This skill maintains `project-context.md`, the single source of truth for the user's EdTech venture. Claude sessions have no memory between conversations, so this file is how the pipeline (research → ideation → assessment → business model → backlog) carries decisions forward. Every other skill in the pipeline reads this file as input and appends to it as output.

## Why this matters

Without a shared context file, each skill re-derives assumptions from scratch, contradicts earlier decisions, and forces the user to re-explain their project every session. With it, the assess-idea skill knows which research findings exist, the backlog skill knows which business model was chosen, and nothing gets silently lost. Treat the file as append-mostly: decisions get updated, but history and rationale are preserved so the user can always see *why* something was decided.

## The canonical file structure

When initializing a new project, create `project-context.md` with exactly this skeleton (fill in what is known, mark the rest `TBD`):

```markdown
# EdTech Platform — Project Context
Last updated: [date] · Stage: [exploring | validating | building]

## 1. Venture snapshot
- Segment: K-12, Vietnam
- One-line direction: [TBD until an idea is chosen]
- Founder constraints: [budget, team, timeline, technical capacity — ask if unknown]

## 2. Key research findings (from industry-research)
[Numbered findings F1, F2, ... — one line each + evidence grade A/B/C + source]

## 3. Idea shortlist (from inspire-idea + assess-idea)
| ID | Idea | Status (pursue/park/killed) | Why |

## 4. Decisions log
[Dated entries: what was decided, by whom, on what evidence]

## 5. Business model (from review-business-model)
[Chosen model summary, or TBD]

## 6. Backlog status (from create-backlog)
[Link/summary of confirmed backlog items, or TBD]

## 7. Open questions & riskiest assumptions
[What still needs validating before building]
```

## Workflow

1. **Session start**: If the user uploaded `project-context.md`, read it fully before doing anything else and give a 3-4 sentence "here's where we are" recap. If they mention the project but no file exists, offer to initialize one — ask only for founder constraints (budget range, team size, technical capacity, timeline), since everything else fills in as the pipeline runs.
2. **After any pipeline skill produces output**: Distill the output into the relevant section. Findings become numbered `F#` entries so later skills can cite them ("Idea 3 addresses F2 and F7"). Do not paste whole reports in — the context file must stay under ~2 pages or it stops being useful. Full reports live as separate output files.
3. **When the user makes a decision**: Record it in the Decisions log with the date and the one-line rationale. Killed ideas stay in the table marked killed — resurrection attempts should have to argue against the original kill reason.
4. **Always output the full updated file** (not a diff) as a downloadable `project-context.md` so the user can save it to their Claude Project or re-upload it next session.

## Rules

- Never invent findings, decisions, or constraints that aren't in the conversation or the existing file. If a section is unknown, keep it `TBD` — a wrong "fact" in project memory poisons every downstream skill.
- Evidence grades travel with findings: A = peer-reviewed or official government statistics, B = reputable industry/consulting reports, C = journalism or single-company claims. Downstream skills weight findings by grade.
- If the uploaded file conflicts with what the user says now, flag the conflict and ask which is current rather than silently overwriting.
