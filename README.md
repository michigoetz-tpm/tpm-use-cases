# TPM AI Playbook

![GitHub stars](https://img.shields.io/github/stars/michigoetz-tpm/tpm-use-cases?style=flat-square)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](https://github.com/michigoetz-tpm/tpm-use-cases/blob/main/LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](https://github.com/michigoetz-tpm/tpm-use-cases/blob/main/CONTRIBUTING.md)
[![Version](https://img.shields.io/badge/version-v0.1-blue?style=flat-square)](https://github.com/michigoetz-tpm/tpm-use-cases/blob/main/CHANGELOG.md)
[![Claude Code Plugin](https://img.shields.io/badge/Claude%20Code-Plugin-5C4EE5?style=flat-square)](https://claude.ai/code)
![Skills](https://img.shields.io/badge/skills-6-informational?style=flat-square)
![Workflows](https://img.shields.io/badge/workflows-1-informational?style=flat-square)

Practical AI skills, workflows, and agents for Technical Program Managers — built as a Claude Code plugin.

This is the companion library for the [2026.AI series on Substack](https://substack.com/@michigoetz). Each article ships with the skills to reproduce the run yourself.

---

## Install

```bash
git clone https://github.com/michigoetz-tpm/tpm-use-cases
cd tpm-use-cases
claude .
```

The `CLAUDE.md` in the root auto-configures all skills. All slash commands become available immediately.

## Setup

1. **Org context** — Create a `domain-context.md` with your org details: structure, tools (Jira, Aha, DataDog), stakeholders, program standards.
2. **Personal context** _(optional)_ — Create a `personal-context.md` with your role, domain, and communication style. Skills adapt accordingly.
3. Start using any skill — they all read your context automatically.

---

## The Delivery Agent — Article 2026.AI.06

Four skills chained into a weekly execution health workflow. Scores program health, flags delivery problems at the epic level, surfaces risks the TPM missed, and drafts a segmented stakeholder update.

```
/tpm-program-health     -> RAG scoring across 6 dimensions
/tpm-epic-checker       -> Delivery flags at the epic level
/tpm-extract-blockers   -> Blocker extraction and classification
/tpm-risk-identifier    -> Risk surfacing and register update
/tpm-stakeholder-update -> Right update to the right audience
        |
tpm-comms-agent         -> Drafts the stakeholder communications
        |
TPM reviews and approves
```

**Run the full workflow:**
```
/tpm-workflow-execution-health
```

Mid-entry is supported — start at any stage if you already have earlier outputs.

---

## TPM Power Questions — Article 2026.AI.07

A library of 30 questions for TPMs, Engineering Managers, Software Engineers, and Product Managers navigating cross-functional programs. Two modes: situational lookup for meeting prep and mid-program diagnosis, and AI governance pre-flight before expanding or trusting an agent.

**Run it:**
```
/tpm-power-questions
```

Works in Claude, ChatGPT, Gemini, or any AI tool. Paste in your situation — the skill routes to the highest-leverage questions for that moment.

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
| `/tpm-power-questions` | 30-question library for cross-functional programs — situational lookup and AI governance pre-flight |

### Agents

| Agent | Role |
|-------|------|
| `tpm-delivery-agent` | Orchestrates the execution health run — chains the four skills in sequence |
| `tpm-comms-agent` | Drafts stakeholder communications from health check findings |

### Workflow

| Workflow | Chain | Output |
|----------|-------|--------|
| `/tpm-workflow-execution-health` | program-health -> epic-checker -> risk-identifier -> stakeholder-update | Health Scorecard + Risk Log + Stakeholder Update |

### Prompts

`/prompts/` — standalone prompts that work across Claude, Gemini, ChatGPT, or any AI tool. No Claude Code required.

---

## Using Your Own Context

1. Create `domain-context.md` with your org structure, tools, and program standards
2. Paste in your Jira export, risk register, or status update when running a skill
3. The skills read whatever is in context — no hardcoded dependencies

---

## Design Principles

1. **Delivery First** — Execution outcomes over documentation
2. **Risk Visibility** — Surface risks early, never bury blockers
3. **Cross-Team Alignment** — Explicitly account for dependencies
4. **Tool-Connected** — Use Jira/Aha/DataDog data when provided
5. **Context Aware** — Apply domain-context.md and personal-context.md when present

---

## Contributing

Contributions welcome — new skills, improvements, feedback. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.

---

## Get In Touch

- **LinkedIn:** [Michael Goetz](https://www.linkedin.com/in/michi-goetz/)
- **GitHub:** [@michigoetz-tpm](https://github.com/michigoetz-tpm)
- **Substack:** [@michigoetz](https://substack.com/@michigoetz?)

---

## License

Licensed under the [MIT License](LICENSE). Use freely, modify openly, share generously.
