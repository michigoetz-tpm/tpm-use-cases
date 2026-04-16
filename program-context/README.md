# program-context/

Four-layer context architecture for NovaGrid. Load the right layer for the right task.

---

## Architecture

```
program-context/
├── layer1-always/          ← Auto-loaded every session (via CLAUDE.md)
│   ├── company-snapshot.md     Company, financials, strategy
│   ├── org-chart.md            Executive team, eng org, TPM assignments, escalation path
│   ├── tech-stack.md           Languages, tools, migration states, TPM friction notes
│   └── skill-testing-scenarios.md  Raw test inputs (meeting notes, Jira data, risk register)
│
├── layer2-portfolio/       ← Load for cross-program work
│   ├── program-index.md        One row per program — RAG status, next milestone, TPM
│   ├── dependency-matrix.md    Cross-program dependency grid + active risks
│   └── fy2026-okrs.md          Company + division OKRs mapped to programs
│
├── layer3-programs/        ← Load only the program(s) you're working on
│   ├── nexus-master.md         Platform Re-architecture (P0, 🟡 At risk)
│   ├── atlas-master.md         Enterprise NovaAI Launch (P0, 🟡 At risk)
│   ├── shield-master.md        SOC 2 Type II (P0, 🔴 Behind)
│   ├── meridian-master.md      API Consolidation (P1, 🔴 Behind)
│   ├── pulse-master.md         Data Pipeline Overhaul (P1, 🔴 Behind)
│   ├── horizon-master.md       Mobile Platform (P1, 🟡 At risk)
│   └── spark-master.md         NovaAI v2 (P1, 🟡 In review)
│
└── layer4-weekly/          ← Updated weekly by portfolio-monitor agent
    └── this-week.md            SteerCo prep, top escalations, doc health table
```

---

## When to load what

| Task | Load |
|------|------|
| Any single-program skill | Layer 1 + that program's master doc |
| Cross-program dependency work | Layer 1 + Layer 2 + relevant program master docs |
| Portfolio health check | Layer 1 + Layer 2 + all program master docs |
| Weekly SteerCo prep | Layer 1 + Layer 2 + Layer 4 |
| Onboarding or orientation | Layer 1 only |

---

## How to invoke in Claude Code

```
@program-context/layer1-always/company-snapshot.md
@program-context/layer1-always/org-chart.md
@program-context/layer3-programs/shield-master.md

Run /tpm-escalation-brief for the Auth0 contract situation.
```

---

## Update cadence

| Layer | Cadence | Who updates |
|-------|---------|-------------|
| Layer 1 | Quarterly (or on major org/tech changes) | Head TPM |
| Layer 2 | Weekly (program-index, dep-matrix) | TPMs + portfolio-monitor agent |
| Layer 3 | Weekly (each program master doc) | Program TPM |
| Layer 4 | Weekly (Monday) + post-SteerCo | portfolio-monitor agent |
