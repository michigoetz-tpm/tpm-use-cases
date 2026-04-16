# /tpm-extract-blockers — Blocker Extraction

**Lifecycle Stage:** Execution & Delivery
**Job-to-be-Done:** Extract and classify blockers from status updates, meeting notes, or Jira — and suggest owners and escalation paths

---

## Instructions

Read `domain-context.md` and `personal-context.md` before starting.

Use escalation paths from `domain-context.md`.

---

## Interaction Flow

**Step 1 — Intake**

Paste:
1. Status updates, standup notes, Jira comments, or meeting notes
2. Program name and current phase
3. Any blockers already known / being tracked

**Step 2 — Extract & Classify**

---

## Output Format

```markdown
# Blocker Report: [Program Name]

**Date:** [Date]
**Source:** [Status update / Meeting notes / Jira export]
**Blockers found:** [N total — X critical, Y major, Z minor]

---

## Critical Blockers 🔴
*(Program-stopping — need immediate escalation)*

### Blocker 1: [Title]
**Description:** [What is blocked and why]
**Impact:** [What cannot proceed / what deadline is at risk]
**Root cause:** [Technical / dependency / decision / resource / external]
**Current owner:** [Name/Team]
**Recommended action:** [Specific next step]
**Escalation path:** [Per domain-context.md]
**Escalation needed by:** [Date/time]

---

## Major Blockers 🟡
*(Significant impact — needs resolution within 1–3 days)*

### Blocker 2: [Title]
[same format]

---

## Minor Blockers 🟢
*(Low impact — track and monitor)*

| # | Blocker | Impact | Owner | Target Resolution |
|---|---------|--------|-------|------------------|
| 1 | | | | |

---

## Blocker Summary Table

| # | Blocker | Severity | Root Cause | Owner | Days Open | Escalation? |
|---|---------|---------|-----------|-------|-----------|------------|
| 1 | | 🔴🟡🟢 | | | | Yes/No |

---

## Recommended Actions (Next 24 Hours)

1. [Most urgent action]
2. [...]
```

---

## Design Principles Applied
- Risk Visibility: Blockers classified by severity with escalation paths
- Delivery First: Impact on delivery dates made explicit
- Tool-Connected: Escalation paths from domain-context.md
