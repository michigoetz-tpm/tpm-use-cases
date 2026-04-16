# data-sources/

Synthetic data representing NovaGrid's external tool integrations. All files are JSON in realistic API response format — structured to mirror what a real Jira Cloud, Aha! Roadmaps, or Salesforce export would return.

---

## Files

```
data-sources/
├── jira/
│   └── novagrid-jira-export.json     # Epics, sprints, blockers, team capacity
│                                     # Coverage: SHIELD, PULSE, MERIDIAN
│                                     # (NEXUS, ATLAS, HORIZON, SPARK tracked in Linear)
├── aha/
│   └── novagrid-aha-export.json      # All 7 programs — milestone SoT for TPMs
│                                     # Milestone %, dates, RAG, feature list
├── salesforce/
│   └── novagrid-sfdc-export.json     # Enterprise pipeline with program dependencies
│                                     # 8 accounts, 8 opportunities, revenue-at-risk
├── preflight-override-log.json       # Written by tpm-preflight skill when TPM overrides a block
└── simulation-log.json               # Written by portfolio-simulator.md on each run
```

---

## How these relate to program master docs

Data flows in one direction: external tools → data files → program master docs → portfolio dashboard.

```
Jira / Linear  ──┐
Aha! Roadmaps  ──┼──► data-sources/   ──► program-context/layer3-programs/[program]-master.md
Salesforce     ──┘                          ↑
                                    TPM reconciles weekly
                                    (Aha! is not auto-updated by engineers)
```

TPMs update their program master docs weekly using these data sources as inputs. The data files are updated either manually (weekly export paste) or via `agents/portfolio-simulator.md` for scenario planning and testing.

---

## Simulation

To advance the portfolio state to a future date for practice or scenario planning:

```
Run agents/portfolio-simulator.md
Target date: [YYYY-MM-DD]
```

The simulator applies realistic, tension-aware changes to all three data files and updates the corresponding program master docs. See `agents/portfolio-simulator.md` for full logic.

---

## Data quality notes

- **Aha! lag:** Aha! milestone % may lag Jira/Linear by 5–7 days. TPMs reconcile weekly.
- **Jira/Linear split:** 9 teams use Linear (NEXUS, ATLAS, HORIZON, SPARK). 6 teams use Jira (SHIELD, PULSE, MERIDIAN, DataCore-Infra). Cross-program status requires manual reconciliation.
- **Salesforce:** Revenue-at-risk figures reflect TPM-confirmed program status as of export date. AE probability assessments are independent.
- **simulation-log.json:** Created on first simulator run. Contains full history of all simulations.

---

## Write permissions

| File | Who can write |
|------|--------------|
| `jira/novagrid-jira-export.json` | Only `agents/portfolio-simulator.md` |
| `aha/novagrid-aha-export.json` | Only `agents/portfolio-simulator.md` |
| `salesforce/novagrid-sfdc-export.json` | Only `agents/portfolio-simulator.md` |
| `preflight-override-log.json` | Only `skills/0-meta/tpm-preflight.md` |
| `simulation-log.json` | Only `agents/portfolio-simulator.md` |

All other files: read-only.

---

## Current state (2026-03-11)

| Source | Programs covered | Last updated | Quality |
|--------|-----------------|-------------|---------|
| Jira | SHIELD, PULSE, MERIDIAN | 2026-03-11 | 🟢 Current |
| Aha! | All 7 programs | 2026-03-11 | 🟡 5-day lag vs Jira |
| Salesforce | 8 enterprise accounts | 2026-03-11 | 🟢 Current |
