# TPM AI Playbook

Practical AI skills, workflows, and agents for Technical Program Managers. 

This is the companion library for the [2026.AI series on Substack](https://substack.com/@michigoetz).

---

## Install

```bash
git clone https://github.com/michigoetz-tpm/tpm-use-cases
cd tpm-use-cases
claude .
```

The `CLAUDE.md` in the root auto-configures all skills. All slash commands become available immediately.

## Setup

1. **Org context** — Create a `domain-context.md` with your org's details: structure, tools (Jira, Aha, DataDog), stakeholders, and program standards.
2. **Personal context** _(optional)_ — Create a `personal-context.md` with your role, domain, tool preferences, and communication style. Skills adapt depth and tone accordingly.
3. Start using any skill — they all read your context automatically.

---

## The Delivery Agent — Article 2026.AI.06

Four skills chained into a weekly execution health workflow. Scores program health, flags delivery problems at the epic level, surfaces risks the TPM missed, and drafts a segmented stakeholder update.

```
/tpm-program-health     → RAG scoring across 6 dimensions
/tpm-epic-checker       → Delivery flags at the epic level
/tpm-extract-blockers   → Blocker extraction and classification
/tpm-risk-identifier    → Risk surfacing and register update
/tpm-stakeholder-update → Right update to the right audience
        ↓
tpm-comms-agent         → Drafts the stakeholder communications
        ↓
TPM reviews and approves
```

**Run the full workflow:**
```
/tpm-workflow-execution-health
```

Mid-entry is supported — start at any stage if you already have earlier outputs.

---

## What's in This Repo

### Skills

| Skill | What It Does |
|-------|-------------|
| `/tpm-program-health` | Multi-dimensional health scorecard — RAG scoring across schedule, scope, resources, risks, dependencies, stakeholders |
| `/tpm-epic-checker` | Epic-level delivery monitoring — flags epics that are stale, at risk, or blocked |
| `/tpm-extract-blockers` | Blocker extraction — pull blockers from any input, classify by severity, suggest owners |
| `/tpm-risk-identifier` | Risk surfacing — identify new risks, update existing register, classify by likelihood and impact |
| `/tpm-stakeholder-update` | Stakeholder-segmented communications — right level of detail to the right audience |

### Agents

| Agent | Role |
|-------|------|
| `tpm-comms-agent` | Drafts stakeholder communications from health check findings |

### Workflow

| Workflow | Chain | Output |
|----------|-------|--------|
| `/tpm-workflow-execution-health` | program-health → epic-checker → risk-identifier → stakeholder-update | Health Scorecard + Risk Log + Stakeholder Update |

### Prompts

`/prompts/` — standalone prompts that work across Claude, Gemini, ChatGPT, or any AI tool. No Claude Code required.

---

## Using Your Own Context

Skills work with whatever context you provide. To run against your own program:

1. Create `domain-context.md` with your org structure, tools, and program standards
2. Paste in your Jira epic export, risk register, or status update when running a skill
3. The skills read whatever is in context — no hardcoded dependencies

---

## Design Principles

Every skill enforces:

1. **Delivery First** — Focus on execution outcomes, not documentation for its own sake
2. **Risk Visibility** — Surface risks early, never bury blockers
3. **Cross-Team Alignment** — Explicitly account for dependencies and cross-team impact
4. **Tool-Connected** — Use Jira/Aha/DataDog data when provided in context
5. **Context Aware** — Apply domain-context.md and personal-context.md when present

---

## Get In Touch

- **LinkedIn:** [Michael Goetz](https://www.linkedin.com/in/michi-goetz/)
- **GitHub:** [@michigoetz-tpm](https://github.com/michigoetz-tpm)
- **Substack:** [@michigoetz](https://substack.com/@michigoetz?)

---

## License

Licensed under the [MIT License](https://choosealicense.com/licenses/mit/). Use freely, modify openly, share generously.
