---
name: tpm-program-health
description: Use when you need a multi-dimensional health snapshot of a program in execution. Triggers on "how is the program doing?", "give me a health check", "what's the RAG status?", "weekly health score", "program status check".
---

# /tpm-program-health — Program Health Score

**Lifecycle Stage:** Execution & Delivery | **Job-to-be-Done:** Score program health across key dimensions and produce an actionable health report

---

## Overview

Score your program across six dimensions — schedule, scope, resources, risks, dependencies, and stakeholders — and produce a structured health report with RAG status, trend direction, and concrete next actions. A health check without recommendations is diagnostic theater; this skill produces both the diagnosis and the prescription.

## When to Use

- Weekly or bi-weekly during active execution
- Before a SteerCo, exec update, or stakeholder communication
- When you sense something is off but can't articulate where
- As Stage 1 of `/tpm-workflow-execution-health`

**When NOT to use:**
- Pre-program or initiation phase — use `/tpm-premortem` instead
- When you need epic-level delivery detail — follow with `/tpm-epic-checker`
- When a single risk needs deep analysis — use `/tpm-risk-identifier` directly

---

## Gated Workflow

```
Phase 1: Intake        →   Phase 2: Score        →   Phase 3: Report
     │                          │                          │
     ▼                          ▼                          ▼
Gather signals             RAG each dimension         Generate scorecard
Confirm context            Set trend direction        Write narrative
Surface unknowns           Flag dimension gaps        Assign actions
```

### Phase 1 — Intake

Collect program signals across all six dimensions. Surface gaps before scoring.

**Required inputs:**
1. Program name and current phase
2. Brief status across: schedule, scope, resources, risks, dependencies, stakeholders
3. Any recent incidents, escalations, or scope changes
4. Upcoming milestones in the next 2–4 weeks

**Surface unknowns explicitly before proceeding:**
```
DIMENSIONS I CANNOT SCORE WITHOUT MORE INFORMATION:
- Resources: No staffing data provided — will mark Amber/Unknown
- Stakeholders: No recent check-in data — flagging as gap
→ Confirm or provide additional context, or I will proceed with Amber for unknown dimensions.
```

Do not silently default unknown dimensions to Green. Missing data is a risk — it scores Amber.

### Phase 2 — Score

Score each dimension using RAG thresholds from `domain-context.md`.

**Scoring rules:**
- **Green:** Confident, on track, no action needed — cite a specific data point
- **Amber:** At risk, needs attention, action required
- **Red:** Blocked, failing, needs escalation
- **When in doubt: Amber.** Defaulting to Green without evidence is the single most common failure mode in health checks.
- **Overall = worst dimension (or weighted).** One Red dimension makes the overall Amber at minimum.
- **Trend is mandatory:** Always set direction — ↑ improving / ↓ deteriorating / → stable. A stable Amber is a different signal than an Amber that was Green last week.

### Phase 3 — Report

Generate the scorecard. Every Amber or Red dimension must have a specific action, a named owner, and a due date before the report is complete.

---

## Output Format

```markdown
# Program Health Report: [Program Name]

**Date:** [Date]
**Phase:** [Initiation / Planning / Execution / Launch / Closure]
**Overall Health:** 🔴 Red / 🟡 Amber / 🟢 Green

---

## Health Scorecard

| Dimension | Score | Trend | Key Finding |
|-----------|-------|-------|-------------|
| Schedule | 🔴🟡🟢 | ↑↓→ | |
| Scope | 🔴🟡🟢 | ↑↓→ | |
| Resources | 🔴🟡🟢 | ↑↓→ | |
| Risks | 🔴🟡🟢 | ↑↓→ | |
| Dependencies | 🔴🟡🟢 | ↑↓→ | |
| Stakeholders | 🔴🟡🟢 | ↑↓→ | |
| **Overall** | **🔴🟡🟢** | ↑↓→ | |

---

## Dimension Details

### Schedule 🔴🟡🟢
**Status:** [On track / At risk / Behind]
**Next milestone:** [Name] — [Date] — [Confidence: High/Med/Low]
**Issues:** [...]

### Scope 🔴🟡🟢
**Status:** [Stable / Creeping / Reduced]
**Recent changes:** [...]
**Issues:** [...]

### Resources 🔴🟡🟢
**Status:** [Fully staffed / Gaps / At risk]
**Issues:** [...]

### Risks 🔴🟡🟢
**Open risks:** [N critical, M major]
**Top risk:** [Name] — [Mitigation status]

### Dependencies 🔴🟡🟢
**Blocked dependencies:** [N]
**At-risk dependencies:** [N]
**Most critical:** [Name] — [Status]

### Stakeholders 🔴🟡🟢
**Alignment:** [Aligned / Mixed / Misaligned]
**Key concern:** [...]

---

## Actions Required

| Priority | Action | Owner | By When |
|---------|--------|-------|---------|
| 🔴 Must | | | |
| 🟡 Should | | | |

---

## Narrative (for stakeholder communication)

> [2–3 sentence narrative suitable for async status update or SteerCo opening]
```

---

## Key Concepts

- **Four core dimensions (minimum):** Schedule, Scope, Dependencies, Team. Resources and Stakeholders added for longer-horizon programs.
- **RAG scoring:** Green = confident, on track. Amber = at risk, needs attention. Red = blocked, needs escalation.
- **Overall = worst dimension (or weighted):** If Dependencies are Red but everything else is Green, the program is Amber at best.
- **Trend matters as much as score:** Always include trend direction (↑↓→).
- **Recommendations required:** Every Amber/Red dimension must have a concrete next action.

---

## Common Rationalizations

| Rationalization | Reality |
|---|---|
| "Things feel good so it's Green" | "Feels good" is not a score. Cite a specific data point or score Amber. |
| "I'll skip Stakeholders — it's a soft dimension" | Stakeholder misalignment kills programs. Skipping it creates a blind spot that surfaces at launch. |
| "No data for that dimension, so I'll skip it" | No data = unknown = Amber. Missing data is itself a risk. |
| "Trend doesn't matter if the score is Green" | A Green trending down is next week's Amber. Trend tells you where you're heading. |
| "A health check without actions is still useful" | Diagnosis without prescription is theater. Every Amber/Red must have an action and an owner. |

---

## Red Flags

- Any dimension scored Green without citing a specific signal or data point
- Overall health set better than the worst individual dimension
- No trend direction set on any dimension
- Amber or Red dimensions with no recommended action or named owner
- Report completed but not shared with stakeholders

---

## Verification

- [ ] All 6 dimensions scored with explicit justification (not assumption)
- [ ] Trend direction set on every dimension (↑↓→)
- [ ] Overall health equals worst dimension — not better
- [ ] Every Amber/Red dimension has a named owner and due date
- [ ] Narrative block completed (2–3 sentences, pasteable into Slack/email)
- [ ] Scorecard findings carried forward to `/tpm-epic-checker` if running full workflow

---

## Composes With

- `/tpm-dependency-map` — Dependencies dimension inputs from the dep map
- `/tpm-risk-identifier` — Risks dimension inputs from the risk register
- `/tpm-stakeholder-update` — health scorecard narrative feeds into stakeholder updates
- `/tpm-steerco-prep` — health summary is the opening of every SteerCo deck
- `/tpm-workflow-execution-health` — Stage 1 of the weekly health check workflow

---

## Design Principles Applied
- Risk Visibility: Multi-dimensional scoring makes hidden risks visible
- Delivery First: Health tied to upcoming milestones and delivery dates
- Cross-Team Alignment: Dependencies dimension explicitly tracked
