# Workflow: Execution Health Check

**Stages:** 4
**Cadence:** Weekly or bi-weekly during active execution
**Output:** Health Scorecard + Risk Log + Stakeholder Update
**Mid-entry:** Yes — start at any stage

---

## Overview

This workflow is your weekly execution pulse. Run it every week or bi-week to catch delivery drift before it becomes a miss, surface risks before they become blockers, and keep stakeholders informed without ceremony.

```
Stage 1: /tpm-program-health    → Score overall program health
    ↓   [Output: Health Scorecard + RAG]
Stage 2: /tpm-epic-checker      → Check epic-level delivery health
    ↓   [Output: Epic flags + stale/at-risk list]
Stage 3: /tpm-risk-identifier   → Surface and update risks
    ↓   [Output: Updated Risk Register]
Stage 4: /tpm-stakeholder-update → Send the right update to the right people
    ↓   [Output: Stakeholder Update / Newsletter]
```

---

## Stage 1 — Program Health Score

**Skill:** `/tpm-program-health`
**Goal:** Get a multi-dimensional health snapshot

**Inputs needed:**
- Brief status across schedule, scope, resources, risks, dependencies, stakeholders
- Any recent incidents or escalations

**Key output to carry forward:** Health scorecard findings → inform epic check focus areas

---

## Stage 2 — Epic Checker

**Skill:** `/tpm-epic-checker`
**Goal:** Find delivery problems at the epic level

**Inputs needed:**
- Jira epic export or description (name, status, last update, target date)
- Health scorecard (Stage 1) to focus attention

**Key output to carry forward:** Flagged epics and blockers → feed into risk identification

---

## Stage 3 — Risk Identifier

**Skill:** `/tpm-risk-identifier`
**Goal:** Surface new risks and update existing ones

**Inputs needed:**
- Epic flags (Stage 2)
- Current risk register (if exists)
- Any cross-team dependency updates

**Key output to carry forward:** Updated risk register + critical actions → inform stakeholder update

---

## Stage 4 — Stakeholder Update

**Skill:** `/tpm-stakeholder-update`
**Goal:** Communicate the right level of detail to the right audience

**Inputs needed:**
- Health scorecard (Stage 1)
- Epic status (Stage 2)
- Risk updates (Stage 3)
- Audience list from domain-context.md

**Output:** Stakeholder-segmented update ready to send

---

## Workflow Complete

**Artifacts produced:**
1. `Program Health Report` — Multi-dimensional scorecard
2. `Epic Health Check` — Flagged epics with owners and actions
3. `Risk Identification` — Updated risk register
4. `Stakeholder Update` — Ready-to-send communications

**Time to run:** ~30–45 minutes
**Next run:** In 1–2 weeks (set a recurring reminder)
