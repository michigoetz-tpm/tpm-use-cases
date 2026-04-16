# This Week — TPM Operating State
*Layer 4 · Weekly rhythm file · Updated by portfolio-monitor agent + TPM*
*Update cadence: daily during active programs · Replace content each Monday*

---

## Week of April 13, 2026

### SteerCo this week
**Date/time:** Friday April 17, 10:00 CET
**Chair:** Karl Bergstrom
**Prep status:** 🟡 In progress
**Pre-read sent:** Yes — Karl distributed Apr 14 (see agenda below)
**Decisions needed:**
1. Auth0 / NEXUS IAM fallback path authorization — Yuki Tanaka must decide by May 1 or program is unblocked to proceed with Auth0-only build
2. PULSE FlowEngine prioritization — Amara's SDK vs migration decision (Apr 15) outcome to be ratified or escalated
3. Kestrel Media emergency call outcome (Apr 15) — CRO to brief on deal status and partial delivery option

---

### Top 3 escalations requiring decisions this week

| # | Escalation | Decision needed from | Deadline | Consequence if missed |
|---|-----------|---------------------|----------|-----------------------|
| 1 | Auth0 contract — CISO punted Mar 18 (third delay). NEXUS IAM Aug 28 confirmed. 14 SHIELD controls blocked, HORIZON GA Aug 31, $4M mobile deals at risk. Need authorization for Auth0-only IAM fallback. | Yuki Tanaka (authorize fallback) + James Whitfield (CISO — final decision) | May 1 | IAM blocked until Aug 28. SHIELD M4 infeasible. Deloitte certification gap. |
| 2 | PULSE FlowEngine — Amara Osei's SDK vs migration call (expected Apr 15). If SDK wins: PULSE M4 slips to Aug 12, $380K additional dual-run cost, 6 SHIELD controls at risk. | Amara Osei | Apr 15 | PULSE M4 slips 6 weeks. Dual-run cost overrun $380K. |
| 3 | Kestrel Media ($1.6M) — HORIZON GA Aug 31 vs budget cycle Jul 31. Partial delivery option (dashboard + alerts by Jul, no SSO) under evaluation. Emergency call Apr 15. | CRO + Rachel Lim (CPO) | Apr 15 | Deal moves to 2027 budget cycle. $1.6M lost in FY2026. |

---

### Program master doc health

| Program | TPM | Last updated | Status | Action needed |
|---------|-----|-------------|--------|--------------|
| NEXUS | Sara Lindqvist | Apr 13 | 🟡 At risk | Sara scoping Auth0-only IAM fallback — initial estimate due Apr 18 |
| ATLAS | Marcus Chen | Apr 13 | 🟡 At risk | SSO (M3) closing Apr 25. Confirm Apex Health POC kickoff date. |
| SHIELD | Fatima Al-Hassan | Apr 13 | 🔴 Behind | Deloitte call booked Apr 18. Meridian Financial evidence format — Dmitri Volkov contacted Apr 14. |
| MERIDIAN | James Okonkwo | Apr 13 | 🟡 At risk | Migration tooling (M4) final stretch — Apr 18 target. |
| PULSE | Yuna Park | Apr 13 | 🔴 Behind | Watching Amara Apr 15 decision. SteerCo slot requested if outcome is SDK-first. |
| HORIZON | Priya Kaur | Apr 13 | 🔴 Behind | Kestrel emergency call Apr 15. Partial delivery scope being drafted. |
| SPARK | Daniel Rios | Apr 13 | 🟡 At risk | VantagePoint roadmap commitment doc — Jun 1 deadline. Daniel started outline Apr 14. |

---

### This week's focus (max 5 items)

- [x] Karl distributes Apr 17 SteerCo pre-read — Auth0, Amara decision, Kestrel on agenda (done Apr 14)
- [x] Fatima books Deloitte call for Apr 18 (done Apr 14 EOD)
- [ ] Amara Osei PULSE decision — Apr 15
- [ ] Kestrel Media emergency call — Apr 15 (CRO + Nina Ross + Priya Kaur)
- [ ] Sara Lindqvist: Auth0-only IAM fallback scoping estimate — Apr 18

---

### Open decisions (not yet escalated)

| Decision | Owner | In limbo since | Impact if unresolved |
|---------|-------|---------------|---------------------|
| Auth0 contract — renewal or Auth0-only IAM fallback | James Whitfield (CISO) / Yuki Tanaka | Mar 18 (27 days) | 14 SHIELD controls, HORIZON GA, ATLAS debt, $4M deals |
| PULSE FlowEngine: SDK launch vs migration priority | Amara Osei | Mar 7 (38 days) | M4 Jul vs Aug, $380K dual-run |
| MERIDIAN SMB resourcing — 434 customers, no support team | Ingrid Solvang | Mar 11 (34 days) | v1 EoL Sep 2026 infeasible without support |
| ATLAS SLA monitoring (M6) — Core Infra deprioritization | Yuki Tanaka | Feb 2026 (2+ months) | Cannot credibly commit 99.5% SLA for enterprise GA |

---

### Portfolio monitor last run

**Last run:** 2026-04-13T09:30:00Z (simulation)
**Next scheduled:** 2026-04-17 (post-SteerCo refresh)
**Output:** simulation-log.json entry #1
**Data quality flags from last run:** This-week.md was template only — now populated.

---

## April 14 Daily Log

### Actions completed today

| Action | Owner | Status | Note |
|--------|-------|--------|------|
| Book Deloitte call (compensating controls question) | Fatima Al-Hassan | Done | Call confirmed Apr 18, 14:00 CET. James Whitfield CC'd. |
| Contact Dmitri Volkov re: Meridian Financial legal format | Fatima Al-Hassan | Done | Dmitri responded — connecting Fatima with Yvonne Tran (Meridian Financial VP Data Eng) Apr 15. |
| Apr 17 SteerCo pre-read distributed | Karl Bergstrom | Done | Pre-read sent to all TPMs + directors. 3 agenda items: Auth0 authorization, Amara decision outcome, Kestrel status. |
| Assign non-IAM Wave 3 controls to Sprint-11 | Leo Nakamura | Done | 5 non-IAM controls formally assigned in Jira. SHIELD-3 can now advance on non-blocked work. |
| Auth0-only IAM fallback scoping kickoff | Sara Lindqvist | In progress | Sara + Ingrid Solvang working session Apr 14 afternoon. Early signal: Auth0-only path may deliver IAM by Jun 30 (vs Aug 28 current). Formal estimate Apr 18. |
| VantagePoint roadmap doc — outline started | Daniel Rios | In progress | Daniel drafted outline: M4 (Vector Store Jun), M2 alpha (Aug 11), downstream dates TBD. Sharing with Leo for review Apr 17. |

### Signals worth tracking

- **Sara's Auth0-only fallback early estimate is significant.** If Jun 30 delivery is confirmed Apr 18, it recovers the 14 SHIELD controls by Jul 1 (M4 feasible), HORIZON GA moves back to Jul 31 (original date), and Kestrel + Solaris deals restabilize. This is the most important piece of information coming out of the week.
- **Yuna Park flagged informally to Karl:** If Amara's Apr 15 decision is SDK-first, Yuna wants a formal SteerCo slot Apr 17 to present the escalation brief. Karl confirmed.
- **Priya Kaur sent Luca Ferraro (Kestrel) a pre-call note** — outlined the partial delivery option (dashboard + pipeline alerts + push notifications via polling as interim, no SSO). Luca's response pending.

---

## How to use this file

**Monday morning:** Portfolio-monitor agent updates the program health table.
TPM fills in SteerCo prep status and top 3 escalations.

**During the week:** Check the open decisions table. If something has been
in limbo for 5+ days, it goes on the escalation list.

**Friday (pre-SteerCo):** Verify prep status is checkmark.
Decisions needed column feeds directly into the SteerCo agenda.

**To update via agent:**
```
@program-context/layer4-weekly/this-week.md
@agents/portfolio-monitor.md

Update this week's operating file from the latest program master docs.
Populate: program health table, stale doc flags, open decision count.
```
