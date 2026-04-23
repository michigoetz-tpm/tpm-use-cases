# Changelog

All notable changes to the TPM AI Playbook are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [v0.2] - 2026-04-22

### Added - TPM Power Questions (Article 2026.AI.07)

**Skills**
- `tpm-power-questions` - 30-question library for cross-functional programs. Two modes: situational lookup (meeting prep, mid-program diagnosis, retros, stakeholder reviews) and AI governance pre-flight (before expanding or trusting an agent output)

**Repo**
- `README.md` - New article section for 2026.AI.07, `/tpm-power-questions` added to skills table, skills badge updated to 6
- `CLAUDE.md` - `/tpm-power-questions` registered as slash command

---

## [v0.1] - 2026-04-16

### Added - The Delivery Agent (Article 2026.AI.06)

**Skills**
- `tpm-program-health` - Multi-dimensional program health scorecard (RAG across 6 dimensions)
- `tpm-epic-checker` - Epic-level delivery monitoring and staleness detection
- `tpm-extract-blockers` - Blocker extraction, classification by severity, owner suggestion
- `tpm-risk-identifier` - Risk surfacing, register update, likelihood/impact classification
- `tpm-stakeholder-update` - Stakeholder-segmented communications (exec / team / cross-functional)

**Agents**
- `tpm-delivery-agent` - Orchestrates the four-skill execution health run
- `tpm-comms-agent` - Drafts stakeholder communications from delivery findings

**Workflows**
- `tpm-workflow-execution-health` - Full 4-stage weekly execution health run with mid-entry support

**Repo**
- `CLAUDE.md` - Claude Code plugin configuration (one-stop install)
- `CONTRIBUTING.md` - Contribution guidelines
- `README.md` - Badges, install instructions, and skill reference
