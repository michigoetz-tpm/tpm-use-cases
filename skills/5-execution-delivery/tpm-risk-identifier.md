---
name: tpm-risk-identifier
description: Use when you need to surface, classify, and assign mitigations to program risks. Triggers on "identify risks", "what could go wrong?", "update the risk register", "risk assessment", "what are our risks?".
---

# /tpm-risk-identifier — Risk Identifier

**Lifecycle Stage:** Execution & Delivery | **Job-to-be-Done:** Surface and classify program risks, link to the Risk Register, and assign mitigations

---

## Overview

Proactively surface risks across six categories — schedule, scope, resource, technical, dependency, and stakeholder — score them by likelihood × impact, and produce an actionable risk register with mitigations, owners, and escalation flags. Risks that aren't written down don't get mitigated. This skill makes the invisible visible.

## When to Use

- Weekly or bi-weekly during execution, as part of health check rhythm
- After epic flags are raised (Stage 3 of `/tpm-workflow-execution-health`)
- At program phase transitions
- When a blocker appears or a dependency slips
- Before a SteerCo or executive update

**When NOT to use:**
- To score overall program health — use `/tpm-program-health` for that
- To assess a single incident in depth — use `/tpm-incident-check`
- For pre-program risk planning — use `/tpm-premortem` at program kickoff

---

## Gated Workflow

```
Phase 1: Intake           →   Phase 2: Surface & Score   →   Phase 3: Register & Act
     │                              │                               │
     ▼                              ▼                               ▼
Gather signals                 Probe all 6 categories         Score L×I
Load existing register         Surface uninvited risks         Assign owners
Note blockers/dependencies     Apply thresholds                Flag escalations
                                                               Define mitigations
```

### Phase 1 — Intake

**Required inputs:**
1. Program name and current phase
2. Brief program description and key workstreams
3. Any risks already identified
4. Recent issues, blockers, or escalations
5. Key dependencies and their current status

**Use escalation thresholds from `domain-context.md`** for scoring boundaries and escalation paths.

### Phase 2 — Surface & Score

Proactively surface risks across all 6 categories even if not explicitly mentioned by the user. Do not wait to be told a risk exists.

**Six risk categories (probe each):**
1. **Schedule** — milestone slippage, critical path compression, velocity below plan
2. **Scope** — creep, ambiguous requirements, late design changes
3. **Resource** — attrition, skill gaps, shared resource contention
4. **Technical** — architecture unknowns, third-party API dependencies, debt accumulation
5. **Dependency** — cross-team blockers, external vendor delays, platform dependencies
6. **Stakeholder** — misaligned expectations, missing decision-makers, sponsor disengagement

**Scoring:**
- Likelihood: 1 (rare) → 5 (almost certain)
- Impact: 1 (negligible) → 5 (program-ending)
- Score = L × I: 1–8 = Low, 9–15 = Medium, 16–25 = High
- Score 16+ requires escalation flag

### Phase 3 — Register & Act

Produce the full risk register. Every risk with Score ≥ 9 must have a mitigation, a contingency, and a named owner. Score 16+ must have an escalation flag and escalation path.

---

## Output Format

```markdown
# Risk Identification: [Program Name]

**Date:** [Date]
**Phase:** [Current phase]
**Risks identified:** [N total — X critical, Y major, Z minor]

---

## Risk Register

| ID | Risk Description | Category | Likelihood | Impact | Score | Status | Owner | Mitigation | Escalation? |
|----|----------------|---------|-----------|--------|-------|--------|-------|-----------|------------|
| R-01 | | Schedule/Scope/Resource/Technical/Dependency/Stakeholder | 1–5 | 1–5 | L×I | Open/Mitigating/Closed | | | Yes/No |

**Score = Likelihood × Impact:** 1–8 = Low, 9–15 = Medium, 16–25 = High

---

## Critical Risks 🔴 (Score 16–25)

### R-0X: [Risk Title]
**Description:** [What could go wrong and why]
**Trigger:** [What event or condition would realize this risk]
**Impact:** [What fails if this risk materializes: schedule / scope / quality / cost]
**Mitigation:** [Specific actions to reduce likelihood or impact]
**Contingency:** [What to do if the risk materializes]
**Owner:** [Name]
**Review date:** [When to reassess]

---

## Medium Risks 🟡 (Score 9–15)

| ID | Risk | Mitigation | Owner | Review Date |
|----|------|-----------|-------|------------|
| | | | | |

---

## Newly Identified Risks (this session)

[Risks surfaced that weren't previously on the radar]

---

## Risk Heat Map

```
    High Impact
        |  🟡 Monitor   |  🔴 Critical   |
        |               |                |
    ────┼───────────────┼────────────────┤
        |  🟢 Accept    |  🟡 Mitigate   |
    Low |               |                |
        └───────────────┴────────────────→
        Low Likelihood              High
```

---

## Recommended Actions (Next 48 Hours)

1. [Specific action for highest-priority risk]
2. [Escalation needed for X risk — path: Y]
```

---

## Common Rationalizations

| Rationalization | Reality |
|---|---|
| "That risk is low probability, not worth documenting" | Unknown probability ≠ low probability. Document with TBD likelihood — naming it enables mitigation. |
| "We already know about that risk, no need to add it" | Known but undocumented risks have no owner, no mitigation, and no review date. Write it down. |
| "We'll address this risk after launch" | Post-launch fixes cost 10× more. If it's real enough to mention, it belongs in the register now. |
| "The team is on it" | "The team is on it" is not a mitigation. What specifically, by when, and what's the contingency? |
| "There are no new risks this week" | Every week of execution introduces new risks. If none surface, the probing wasn't thorough enough. |

---

## Red Flags

- Any risk category left unprobed (especially Stakeholder and Resource — commonly skipped)
- Risks with Score ≥ 16 without an escalation flag
- Mitigations that are vague ("monitor closely", "check in with team")
- No contingency plan on any Critical risk
- Risk register not updated — new session only adds risks, never closes or updates existing ones

---

## Verification

- [ ] All 6 risk categories probed — none skipped
- [ ] Every risk has a Likelihood, Impact, and Score
- [ ] All Score ≥ 16 risks have escalation flag and escalation path from `domain-context.md`
- [ ] Every Score ≥ 9 risk has a named owner, mitigation, and review date
- [ ] At least 1 newly identified risk per session (if none, document why)
- [ ] Risk register output carried into `/tpm-stakeholder-update` for comms

---

## Design Principles Applied
- Risk Visibility: Proactive identification across all 6 risk categories
- Delivery First: Impact scored in terms of delivery consequences
- Context Aware: Thresholds and escalation paths from `domain-context.md`
