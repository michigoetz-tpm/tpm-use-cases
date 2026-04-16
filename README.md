# TPM AI Playbook

A Claude Code plugin with 33 TPM skills + 9 agents + 4 workflows + 4 hooks designed for Technical Program Managers at B2B technology companies.

**Lifecycle-organized** — every skill lives at the right stage of the program lifecycle, from strategy through closure.

**Domain-agnostic** — customize `domain-context.md` once with your org structure, tools (Jira, Aha, DataDog), stakeholders, and program standards. Every skill adapts automatically.

**Agent-first** — the `tpm-orchestrator` agent lets you spawn and coordinate AI sub-agents for complex program execution. TPMs direct AI teams, not just run individual skills.

## Install

```bash
git clone https://github.com/michigoetz-tpm/tpm-use-cases
cd tpm-use-cases
claude .
```

That's it. The `CLAUDE.md` in the root auto-configures all skills. All slash commands become available in the session immediately.

## Setup

1. **Org context** — Create a `domain-context.md` with your org's details (structure, tools, stakeholders, program standards). The repo ships with a NovaGrid example you can use as a template.
2. **Personal context** _(optional)_ — Create a `personal-context.md` with your role, domain, tool preferences, and communication style. Skills adapt depth and tone accordingly.
3. Start using any skill — they all read your context automatically.

The repo ships with a fully realized fictional company — **NovaGrid, Inc.** — as a sandbox. Use it to test skills before pointing them at your real org. See `program-context/` for the full context system.

---

## Featured: The Delivery Agent — Article 2026.AI.06

Four skills chained into a weekly execution health workflow. Scores program health, flags delivery problems at the epic level, surfaces risks the TPM missed, and drafts a segmented stakeholder update.

```
/tpm-program-health     → RAG scoring across 6 dimensions
/tpm-epic-checker       → Delivery flags at the epic level
/tpm-risk-identifier    → Risk surfacing and register update
/tpm-stakeholder-update → Right update to the right audience
        ↓
tpm-comms-agent         → Drafts the stakeholder communications
        ↓
TPM reviews and approves
```

**To run the full workflow:**
```
/tpm-workflow-execution-health
```

Mid-entry is supported — start at any stage if you already have earlier outputs.

---

## Getting Started

New to the toolkit? See [START_HERE.md](START_HERE.md) for the 60-second onboarding guide. Quick reference below:

| Step | Skill | What You'll Do |
|------|-------|----------------|
| 1 | `/tpm-boardroom` | Peer-review your program — sanity check before kickoff |
| 2 | `/tpm-master-document` | Generate your Program Charter / Master Doc |
| 3 | `/tpm-stakeholder-map` | Map stakeholders, influence, and communication needs |
| 4 | `/tpm-program-health` | Score your program's health across key dimensions |
| 5 | `/tpm-decision-record` | Document a key program decision in ADR format |

Once comfortable, run a full workflow or spin up the `tpm-orchestrator` for complex execution.

---

## Skills by Lifecycle Stage

### Stage 0 — Meta Skills

Pre-flight data quality and reconciliation. Run these before any skill that depends on program data being accurate.

| Skill | What It Does |
|-------|-------------|
| `/tpm-preflight` | Data quality gate — validates staleness, required fields, cross-program consistency before skill execution |
| `/tpm-data-reconciliation` | Conflict resolution — when Jira, Aha!, and program master docs disagree, determine ground truth |

### Stage 1 — Program Strategy

| Skill | What It Does |
|-------|-------------|
| `/tpm-boardroom` | Boardroom review — 6-advisor, 2-round peer review with votes (APPROVE/CONDITIONAL/NOT READY), produces debate.md + boardroom.html |

### Stage 2 — Program Initiation

| Skill | What It Does |
|-------|-------------|
| `/tpm-master-document` | Program Charter / Master Document generator — charter drafting, objective framing, problem statement |
| `/tpm-stakeholder-map` | Stakeholder Mapping — influence map, communication plan, RACI skeleton |
| `/tpm-premortem` | Pre-Mortem on Demand — imagine the program failed, surface root causes before they happen |

### Stage 3 — Planning & Design

| Skill | What It Does |
|-------|-------------|
| `/tpm-dependency-map` | Dependency Map Generator — cross-team, cross-system dependency visualization |
| `/tpm-timeline-stress-tester` | Timeline Stress Tester — challenge assumptions, surface schedule risk |
| `/tpm-annual-goal-check` | Annual Goal Check — validate program alignment to annual goals and OKRs |
| `/tpm-roi-checker` | Business Case / ROI Checker — validate investment, estimate return |
| `/tpm-epic-breakdown` | Epic Breakdown — decompose epics into tasks and stories with acceptance criteria |
| `/tpm-roadmap-health-check` | Roadmap Health Check — assess roadmap clarity, sequencing, and feasibility |

### Stage 4 — Architecture & Technical Alignment

| Skill | What It Does |
|-------|-------------|
| `/tpm-architecture-review` | Architecture Synthesizer — synthesize Design Reviews and RFCs into a coherent architecture narrative |
| `/tpm-technical-brief` | Technical Brief Generator — generate a brief from PRD + architecture context |
| `/tpm-techdebt` | Tech Debt Checker — identify, categorize, and prioritize tech debt against program goals |
| `/tpm-incident-check` | Incident Checker — analyze DataDog incidents for program-relevant patterns and risks |
| `/tpm-supportticket-check` | Support Ticket Analyzer — mine SFDC/Jira support tickets for signals relevant to your program |

### Stage 5 — Execution & Delivery

| Skill | What It Does |
|-------|-------------|
| `/tpm-meeting-notes` | Meeting Notes Synthesis — structure raw notes into decisions, actions, owners, dates |
| `/tpm-extract-blockers` | Blocker Extraction — pull blockers from updates, classify by severity, suggest owners |
| `/tpm-crossteam-prep` | Cross-Team Sync Prep — agenda, pre-reads, alignment goals for cross-team meetings |
| `/tpm-steerco-prep` | SteerCo Prep — status narrative, key decisions needed, risk summary for steering committee |
| `/tpm-program-health` | Program Health Score — score program across schedule, scope, resources, risks, dependencies |
| `/tpm-epic-checker` | Epic Checker — flag epics that are taking too long or haven't been updated in 2+ weeks |
| `/tpm-decision-record` | Decision Record — ADR-style documentation for program and architecture decisions |
| `/tpm-risk-identifier` | Risk Identifier — surface and classify risks, link to Risk Registry |
| `/tpm-prd-engdoc-analyze` | PRD / Eng Design Doc Analyzer — quality-check specs for completeness, ambiguity, missing scope |
| `/tpm-stakeholder-update` | Stakeholder Comms Update / Newsletter — generate stakeholder-segmented program updates |
| `/tpm-escalation-brief` | Escalation Brief — draft a structured escalation with context, impact, ask, and recommended path |
| `/tpm-raid-log` | RAID Log Generator — build and maintain Risks/Actions/Issues/Decisions as single source of operational truth |
| `/tpm-qbr-prep` | QBR / MBR Preparation — plan vs. actuals, OKR contribution, key decisions, ask for next period |
| `/tpm-metricsdashboard` | Metrics Dashboard — define, structure, and populate a program metrics dashboard |

### Stage 6 — Launch / Release

| Skill | What It Does |
|-------|-------------|
| `/tpm-launchreview` | Launch Review — given DPLY ticket, PRD, EDD, fill out the launch template and ready it for sign-off |
| `/tpm-execsummary` | Exec Summary — concise, SCQA-structured executive summary for any program milestone |

### Stage 7 — Program Closure

| Skill | What It Does |
|-------|-------------|
| `/tpm-programclosure` | Program Closure Checklist Generator — systematic closure: handoffs, docs, KPIs, sign-offs |
| `/tpm-programsummary` | Final Program Summary Writer — narrative summary of program outcomes, learnings, impact |
| `/tpm-programmemory` | Program Memory — capture institutional knowledge before the team disperses |
| `/tpm-programretro` | Retrospective — structured retro: what worked, what didn't, what to carry forward |

---

## Workflows (Multi-Skill Chains)

Workflows chain multiple skills into guided, multi-stage processes. Each stage produces a named artifact that feeds the next. All workflows support **mid-entry** — skip stages if you already have the inputs.

| Workflow | Chain | What It Produces |
|----------|-------|-----------------|
| `/tpm-workflow-program-kickoff` | boardroom → master-document → stakeholder-map → premortem | Program Charter + Stakeholder Map + Pre-Mortem Report |
| `/tpm-workflow-execution-health` | program-health → epic-checker → risk-identifier → stakeholder-update | Health Scorecard + Risk Log + Stakeholder Update |
| `/tpm-workflow-launch-readiness` | architecture-review → launchreview → execsummary | Architecture Brief + Launch Checklist + Exec Summary |
| `/tpm-workflow-program-closure` | programclosure → programsummary → programmemory → programretro | Closure Checklist + Summary + Memory + Retro |

---

## Agents

| Agent | Role |
|-------|------|
| `tpm-orchestrator` | **Core agent** — decomposes program goals into sub-tasks, spawns and coordinates sub-agents, tracks progress |
| `tpm-comms-agent` | Orchestrates stakeholder communication: newsletters, steerco decks, exec summaries, escalations |
| `tpm-delivery-agent` | Owns execution: blocker tracking, health scores, epic monitoring, risk management |
| `tpm-launch-agent` | Coordinates launch readiness: architecture review, launch checklist, DPLY/EDD sign-offs |
| `jira-agent` | Jira integration: epic/story management, velocity data, sprint health, delivery signals |
| `aha-agent` | Aha integration: roadmap sync, feature status, release planning |
| `datadog-agent` | DataDog integration: incident analysis, SLO monitoring, metrics extraction |
| `portfolio-simulator` | **Simulation agent** — advances the NovaGrid portfolio to any target date using probabilistic cascade logic across 5 active tensions. Powers realistic skill testing. |
| `portfolio-monitor` | **Portfolio health agent** — runs 7 parallel program health checks, cross-program cascade analysis, escalation triage, and SteerCo agenda generation |

### Agent Architecture

```
tpm-orchestrator
    ├── spawns → tpm-delivery-agent
    ├── spawns → tpm-comms-agent
    ├── spawns → tpm-launch-agent
    ├── calls  → jira-agent          (data retrieval & updates)
    ├── calls  → aha-agent           (roadmap sync)
    └── calls  → datadog-agent       (incident & metrics)

portfolio-monitor
    ├── spawns → [7 parallel health-check subagents]
    ├── cross-program cascade analysis
    └── writes → program-context/layer4-weekly/this-week.md

portfolio-simulator
    ├── reads  → program-context/ (all layers)
    ├── advances state to target date
    └── writes → data-sources/ + program master docs
```

---

## Design Principles

Every skill enforces:

1. **Delivery First** — Every artifact focuses on execution outcomes, not just documentation
2. **Risk Visibility** — Surface risks early, track mitigation status, never bury blockers
3. **Cross-Team Alignment** — Every deliverable explicitly accounts for dependencies and cross-team impact
4. **Tool-Connected** — Skills leverage real Jira/Aha/DataDog data when context is provided
5. **Context Aware** — All skills automatically read `domain-context.md` and `personal-context.md`

---

## Customization

### Org Context (`domain-context.md`)

All org-specific knowledge lives in `domain-context.md`. This includes:

- **Org & Program Structure** — Company name, org chart, program taxonomy, team names, reporting lines, program tiers (P0/P1/P2 etc.)
- **Tools & Integrations** — Jira instance/project keys, Aha workspace, DataDog environment, SFDC/Jira Support config, Confluence spaces
- **Stakeholder Map** — Key stakeholders, roles, communication preferences, decision-making authority, escalation paths
- **Program Standards** — Templates, SLAs, definition of done, compliance requirements, risk thresholds, escalation criteria

The toolkit ships with a **fully realized fictional company** — NovaGrid, Inc. (post-IPO B2B data platform, 7 active programs, 5 live tensions, realistic JSON data exports). Use it to test skills before pointing them at your real org. See `program-context/` for the full context system.

### Personal Context (`personal-context.md`)

Your personal profile helps skills adapt to your experience level and context:

- **Role & Seniority** — TPM level, years of experience, team/program size managed
- **Program Domain** — Infrastructure, platform, product, data, ML — what type of programs you run
- **Preferred Tools & Stack** — Jira vs Linear, Aha vs Confluence, Slack vs Teams
- **Communication Style** — Output format preferences, tone, stakeholder audience level, language

---

## Hooks

The plugin includes 4 hooks that run automatically:

| Hook | Event | What It Does |
|------|-------|-------------|
| **Context Reinjection** | `SessionStart` (after compaction) | Re-injects `domain-context.md` and `personal-context.md` when long conversations compress |
| **Quality Gate** | `Stop` | Validates TPM deliverables follow the 5 design principles (delivery focus, risk visibility, cross-team scope) |
| **Usage Logger** | `PostToolUse` / `PostToolUseFailure` | Logs every TPM skill execution to `.tpm-toolkit-audit.jsonl` for usage analytics |
| **Workflow Tracker** | `PostToolUse` | Tracks multi-step workflow progress to `.tpm-toolkit-workflow-state.json` so workflows resume across sessions |

Hook scripts live in `hooks/` and are configured via `hooks/hooks.json`.

---

## Skill Disambiguation

| If you need... | Use this | Not this |
|----------------|---------|----------|
| A program charter | `/tpm-master-document` | `/tpm-technical-brief` (that's a technical summary from PRD + architecture) |
| To prep for a leadership meeting | `/tpm-steerco-prep` | `/tpm-execsummary` (that's a written narrative, not a meeting prep) |
| To document a decision | `/tpm-decision-record` | `/tpm-meeting-notes` (that's synthesis of a full meeting, not one decision) |
| To check program status | `/tpm-program-health` | `/tpm-metricsdashboard` (that's a metrics structure design, not a health check) |
| To close out a program | `/tpm-workflow-program-closure` | `/tpm-programretro` (that's one stage — the workflow does the full closure) |
| To orchestrate complex execution | `/tpm-orchestrator` | Individual skills (use the orchestrator when you need multiple agents working in parallel) |

---

## Backlog

Skills in active development — not yet available:

| Skill | Description |
|-------|-------------|
| `/tpm-delivery-forecast` | Delivery Forecast using historical Jira velocity and remaining scope |
| `/tpm-release-notes` | Company and external release notes generator |
| `/tpm-aha-jira-sync` | Automatic Epic integration from Aha to Jira |
| `/tpm-ai-agent-orchestration` | Define scope for AI Agent teams alongside Engineering teams |

---

## Resources

| Resource | What's in it |
|----------|-------------|
| [START_HERE.md](START_HERE.md) | 60-second onboarding guide — 5 skills to try first, quick paths by TPM task |
| [templates/](templates/) | 7 reusable output templates with filled NovaGrid examples (stakeholder map, status briefs, RAID, SteerCo, QBR, blockers, milestones) |
| [program-context/](program-context/) | 4-layer NovaGrid context system — company snapshot, 7 program master docs, portfolio OKRs, weekly operating state |
| [data-sources/](data-sources/) | Realistic Jira, Aha!, and Salesforce JSON exports for skill testing + simulation log |
| [docs/data-layer.md](docs/data-layer.md) | The 3-layer model (Data → Skills → Agents) and data hygiene prerequisites |
| [docs/usage.md](docs/usage.md) | Platform-specific usage guide (Claude Code, Cursor, other tools) |

---

## Get In Touch

- **LinkedIn:** [Michael Goetz](https://www.linkedin.com/in/michi-goetz/)
- **GitHub:** [@michigoetz-tpm](https://github.com/michigoetz-tpm)
- **Substack:** [@michigoetz](https://substack.com/@michigoetz?)

---

## License

Licensed under the [MIT License](https://choosealicense.com/licenses/mit/). Use freely, modify openly, share generously.
