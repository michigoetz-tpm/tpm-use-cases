---
name: tpm-epic-checker
description: Use when you need to find delivery problems at the epic level. Triggers on "check my epics", "which epics are behind?", "find stale epics", "epic health check", "what's at risk in Jira?".
---

# /tpm-epic-checker — Epic Checker

**Lifecycle Stage:** Execution & Delivery | **Job-to-be-Done:** Flag epics that are taking too long, haven't been updated in 2+ weeks, or show signs of scope or delivery problems

---

## Overview

Systematically review your epic list and surface delivery problems before they become misses. Flags critical issues (blocked, behind by 3+ weeks), at-risk items (stale, slow-moving), and produces specific Jira actions the TPM can take this week. A clean epic list is a lagging indicator — this skill finds problems while there's still time to act.

## When to Use

- During active sprint execution, weekly or bi-weekly
- When preparing for SteerCo or program health review
- When a milestone is approaching and you want to confirm delivery confidence
- As Stage 2 of `/tpm-workflow-execution-health` (after program health score)

**When NOT to use:**
- For overall program health scoring — use `/tpm-program-health` first
- For deep risk analysis — epic flags feed into `/tpm-risk-identifier`, not replace it
- Pre-planning, before epics exist — use `/tpm-epic-breakdown` instead

---

## Gated Workflow

```
Phase 1: Intake        →   Phase 2: Analyze       →   Phase 3: Flag & Recommend
     │                          │                              │
     ▼                          ▼                              ▼
Load epic list             Apply flag criteria           Categorize: 🔴🟡🟢
Confirm staleness          Check each epic               Specific Jira actions
threshold                  against thresholds            This-week priorities
```

### Phase 1 — Intake

**Required inputs:**
1. Epic list — paste Jira export, CSV, or describe epics: name, status, start date, target date, last update
2. Program name and current sprint/week
3. Any epics already known to be at risk

**Confirm thresholds from `domain-context.md`:**
```
STALENESS THRESHOLD: >14 days without update = stale flag
BEHIND THRESHOLD: >1 week behind target date = at-risk; >3 weeks = critical
MISSING OWNER: Any epic with no assigned owner = flag regardless of status
→ Using domain-context.md defaults unless you specify otherwise.
```

### Phase 2 — Analyze

Apply flag criteria to every epic in the list. Do not skip epics marked "In Progress" — those are the most common source of hidden risk.

**Flag criteria:**
- **Critical 🔴:** Blocked / >3 weeks behind target / no update >21 days / missing owner on milestone epic
- **At-Risk 🟡:** >1 week behind / no update >14 days / scope expanding without revised target date / low confidence on near-term milestone
- **On Track 🟢:** Updated within 14 days / within 1 week of target / owner confirmed

### Phase 3 — Flag & Recommend

Produce the categorized flag list. Every Critical epic must have a specific recommended action — not just "follow up". Suggest concrete Jira updates where applicable.

---

## Output Format

```markdown
# Epic Health Check: [Program Name]

**Date:** [Date]
**Epics analyzed:** [N]
**Flags raised:** [X critical, Y at-risk, Z stale]

---

## 🔴 Critical Flags

| Epic | Issue | Impact | Recommendation | Owner |
|------|-------|--------|---------------|-------|
| [Epic name / key] | [e.g., 3 weeks behind, no update in 21 days] | [Milestone at risk] | [Specific action] | |

---

## 🟡 At-Risk Flags

| Epic | Issue | Days Since Update | Recommendation | Owner |
|------|-------|------------------|---------------|-------|
| | | | | |

---

## 🟢 On Track

| Epic | Status | Target Date | Confidence |
|------|--------|------------|-----------|
| | | | High/Med/Low |

---

## Summary Analysis

**Stale epics (no update >14 days):** [N]
**Behind schedule (>1 week):** [N]
**Scope creep signals:** [N]
**Missing owners:** [N]

---

## Recommended Actions (This Week)

1. [Specific action for highest-priority issue]
2. [...]

---

## Suggested Jira Updates

| Epic | Suggested Action |
|------|-----------------|
| [Epic key] | Update status to At Risk; add comment with blocker |
| [Epic key] | Reassign to [owner] |
```

---

## Common Rationalizations

| Rationalization | Reality |
|---|---|
| "That epic is In Progress so it's fine" | "In Progress" with no update in 3 weeks is a stale flag, not a pass. |
| "The engineer said they're working on it" | Verbal confirmation ≠ updated epic. An untracked epic is an invisible risk. |
| "It's only 1 week behind — too small to flag" | One week becomes three weeks fast. At-risk flags exist precisely to catch drift early. |
| "I know all my epics, I don't need this check" | If you knew every problem, you wouldn't need a health check. Structured review catches the things you've normalized. |
| "Missing owners are a Jira housekeeping issue" | Missing owners are a delivery risk. No owner = no accountability = no escalation path. |

---

## Red Flags

- Any epic marked "In Progress" with no update in 14+ days not flagged
- Critical flags produced with no specific recommended action
- Epics with expanding scope but unchanged target dates not flagged
- All epics scored On Track when a milestone is within 2 weeks
- Output not carried into `/tpm-risk-identifier` when Critical flags exist

---

## Verification

- [ ] Every epic in the provided list has been assessed (none skipped)
- [ ] Critical flags have a specific action — not just "check in with team"
- [ ] Stale epic count matches actual days-since-update (not estimated)
- [ ] Missing owner epics flagged regardless of status
- [ ] Suggested Jira updates are specific (field to change, value to set)
- [ ] Critical flags carried forward as inputs to `/tpm-risk-identifier`

---

## Design Principles Applied
- Tool-Connected: Uses Jira conventions and project keys from `domain-context.md`
- Risk Visibility: Stale and at-risk epics surfaced proactively
- Delivery First: Issues tied to milestone impacts
