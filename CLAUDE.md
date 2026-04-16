# TPM AI Playbook — Claude Code Plugin

This file configures the TPM AI Playbook as a Claude Code plugin.

## Setup

Before running skills, create these context files in the repo root:

- `domain-context.md` — Your org structure, tools (Jira, Aha, DataDog), stakeholders, program standards, and RAG thresholds.
- `personal-context.md` _(optional)_ — Your role, seniority, domain, tool preferences, and communication style.

## Skills

### Stage 5 — Execution & Delivery (The Delivery Agent)
- `/tpm-program-health` → `skills/5-execution-delivery/tpm-program-health.md`
- `/tpm-epic-checker` → `skills/5-execution-delivery/tpm-epic-checker.md`
- `/tpm-extract-blockers` → `skills/5-execution-delivery/tpm-extract-blockers.md`
- `/tpm-risk-identifier` → `skills/5-execution-delivery/tpm-risk-identifier.md`
- `/tpm-stakeholder-update` → `skills/5-execution-delivery/tpm-stakeholder-update.md`

## Workflows
- `/tpm-workflow-execution-health` → `workflows/tpm-workflow-execution-health.md`

## Agents
- `tpm-comms-agent` → `agents/tpm-comms-agent.md`

## Design Principles

When generating any TPM deliverable, always enforce:

1. **Delivery First** — Focus on execution outcomes, not documentation for its own sake
2. **Risk Visibility** — Surface risks early, never bury blockers
3. **Cross-Team Alignment** — Explicitly account for dependencies and cross-team impact
4. **Tool-Connected** — Use Jira/Aha/DataDog data when provided in context
5. **Context Aware** — Apply domain-context.md and personal-context.md when present
