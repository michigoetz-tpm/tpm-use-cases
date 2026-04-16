# TPM AI Playbook — Claude Code Plugin

This file configures the TPM AI Playbook as a Claude Code plugin.
Add it to your project as `CLAUDE.md` or import it from your own `CLAUDE.md`.

## Setup

Before running skills, create two context files in the repo root:

- `domain-context.md` — Your org structure, tools (Jira, Aha, DataDog), stakeholders, program standards, and RAG thresholds. See `program-context/layer1-always/company-snapshot.md` for a worked example.
- `personal-context.md` _(optional)_ — Your role, seniority, domain, tool preferences, and communication style.

The repo ships with **NovaGrid** as a ready-to-use sandbox. You can run all skills against it without any setup — just open the repo in Claude Code and start.

## Context Files

### NovaGrid sandbox — always available
- `program-context/layer1-always/company-snapshot.md` — NovaGrid company overview, ARR, board mandates
- `program-context/layer1-always/org-chart.md` — Executive team, engineering divisions, escalation paths
- `program-context/layer2-portfolio/program-index.md` — All 7 programs with RAG status and OKR alignment
- `program-context/layer2-portfolio/fy2026-okrs.md` — Company + division OKRs with program-to-OKR mapping
- `program-context/layer2-portfolio/dependency-matrix.md` — Cross-program dependency grid, shared resource conflicts

### Load for specific program work
- `program-context/layer3-programs/shield-master.md` — SHIELD (SOC 2 Type II) program master doc
- `program-context/layer3-programs/nexus-master.md` — NEXUS program master doc
- `program-context/layer3-programs/atlas-master.md` — ATLAS program master doc
- `program-context/layer3-programs/meridian-master.md` — MERIDIAN program master doc
- `program-context/layer3-programs/pulse-master.md` — PULSE program master doc
- `program-context/layer3-programs/horizon-master.md` — HORIZON program master doc
- `program-context/layer3-programs/spark-master.md` — SPARK program master doc

### Load for weekly operations
- `program-context/layer4-weekly/this-week.md` — Current week operating state, open escalations

### Data sources (for skills that consume real data)
- `data-sources/jira/novagrid-jira-export.json` — Jira epics, sprints, blockers
- `data-sources/aha/novagrid-aha-export.json` — Milestone source of truth
- `data-sources/salesforce/novagrid-sfdc-export.json` — Revenue pipeline and at-risk accounts

## Skills

All skills are in `skills/` organized by program lifecycle stage:

### Stage 0 — Meta Skills
- `/tpm-preflight` → `skills/0-meta/tpm-preflight.md`
- `/tpm-data-reconciliation` → `skills/0-meta/tpm-data-reconciliation.md`

### Stage 1 — Program Strategy
- `/tpm-boardroom` → `skills/1-program-strategy/tpm-boardroom.md`

### Stage 2 — Program Initiation
- `/tpm-master-document` → `skills/2-program-initiation/tpm-master-document.md`
- `/tpm-stakeholder-map` → `skills/2-program-initiation/tpm-stakeholder-map.md`
- `/tpm-premortem` → `skills/2-program-initiation/tpm-premortem.md`

### Stage 3 — Planning & Design
- `/tpm-dependency-map` → `skills/3-planning-design/tpm-dependency-map.md`
- `/tpm-timeline-stress-tester` → `skills/3-planning-design/tpm-timeline-stress-tester.md`
- `/tpm-annual-goal-check` → `skills/3-planning-design/tpm-annual-goal-check.md`
- `/tpm-roi-checker` → `skills/3-planning-design/tpm-roi-checker.md`
- `/tpm-epic-breakdown` → `skills/3-planning-design/tpm-epic-breakdown.md`
- `/tpm-roadmap-health-check` → `skills/3-planning-design/tpm-roadmap-health-check.md`

### Stage 4 — Architecture & Technical Alignment
- `/tpm-architecture-review` → `skills/4-architecture-alignment/tpm-architecture-review.md`
- `/tpm-technical-brief` → `skills/4-architecture-alignment/tpm-technical-brief.md`
- `/tpm-techdebt` → `skills/4-architecture-alignment/tpm-techdebt.md`
- `/tpm-incident-check` → `skills/4-architecture-alignment/tpm-incident-check.md`
- `/tpm-supportticket-check` → `skills/4-architecture-alignment/tpm-supportticket-check.md`

### Stage 5 — Execution & Delivery (The Delivery Agent)
- `/tpm-meeting-notes` → `skills/5-execution-delivery/tpm-meeting-notes.md`
- `/tpm-extract-blockers` → `skills/5-execution-delivery/tpm-extract-blockers.md`
- `/tpm-crossteam-prep` → `skills/5-execution-delivery/tpm-crossteam-prep.md`
- `/tpm-steerco-prep` → `skills/5-execution-delivery/tpm-steerco-prep.md`
- `/tpm-program-health` → `skills/5-execution-delivery/tpm-program-health.md`
- `/tpm-epic-checker` → `skills/5-execution-delivery/tpm-epic-checker.md`
- `/tpm-decision-record` → `skills/5-execution-delivery/tpm-decision-record.md`
- `/tpm-risk-identifier` → `skills/5-execution-delivery/tpm-risk-identifier.md`
- `/tpm-prd-engdoc-analyze` → `skills/5-execution-delivery/tpm-prd-engdoc-analyze.md`
- `/tpm-stakeholder-update` → `skills/5-execution-delivery/tpm-stakeholder-update.md`
- `/tpm-escalation-brief` → `skills/5-execution-delivery/tpm-escalation-brief.md`
- `/tpm-raid-log` → `skills/5-execution-delivery/tpm-raid-log.md`
- `/tpm-qbr-prep` → `skills/5-execution-delivery/tpm-qbr-prep.md`
- `/tpm-metricsdashboard` → `skills/5-execution-delivery/tpm-metricsdashboard.md`
- `/tpm-power-questions` → `skills/5-execution-delivery/tpm-power-questions.md`

### Stage 6 — Launch / Release
- `/tpm-launchreview` → `skills/6-launch-release/tpm-launchreview.md`
- `/tpm-execsummary` → `skills/6-launch-release/tpm-execsummary.md`

### Stage 7 — Program Closure
- `/tpm-programclosure` → `skills/7-program-closure/tpm-programclosure.md`
- `/tpm-programsummary` → `skills/7-program-closure/tpm-programsummary.md`
- `/tpm-programmemory` → `skills/7-program-closure/tpm-programmemory.md`
- `/tpm-programretro` → `skills/7-program-closure/tpm-programretro.md`

## Workflows
- `/tpm-workflow-program-kickoff` → `workflows/tpm-workflow-program-kickoff.md`
- `/tpm-workflow-execution-health` → `workflows/tpm-workflow-execution-health.md`
- `/tpm-workflow-launch-readiness` → `workflows/tpm-workflow-launch-readiness.md`
- `/tpm-workflow-program-closure` → `workflows/tpm-workflow-program-closure.md`

## Agents
- `/tpm-orchestrator` → `agents/tpm-orchestrator.md`
- `/tpm-comms-agent` → `agents/tpm-comms-agent.md`
- `/tpm-delivery-agent` → `agents/tpm-delivery-agent.md`
- `/tpm-launch-agent` → `agents/tpm-launch-agent.md`
- `/jira-agent` → `agents/jira-agent.md`
- `/aha-agent` → `agents/aha-agent.md`
- `/datadog-agent` → `agents/datadog-agent.md`
- `portfolio-simulator` → `agents/portfolio-simulator.md`
- `portfolio-monitor` → `agents/portfolio-monitor.md`

## Design Principles

When generating any TPM deliverable, always enforce:

1. **Delivery First** — Focus on execution outcomes, not documentation for its own sake
2. **Risk Visibility** — Surface risks early, never bury blockers
3. **Cross-Team Alignment** — Explicitly account for dependencies and cross-team impact
4. **Tool-Connected** — Use Jira/Aha/DataDog data when provided in context
5. **Context Aware** — Always apply domain-context.md and personal-context.md when present
