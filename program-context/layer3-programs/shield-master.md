# SHIELD — Program Master Document
*SOC 2 Type II Certification*
*Layer 3 context · Load for SHIELD work · Update cadence: weekly*

---

## Header

| Field | Value |
|-------|-------|
| **Program code** | SHIELD |
| **TPM** | Fatima Al-Hassan |
| **Executive Sponsor** | James Whitfield (CISO) |
| **Phase** | Execution |
| **Priority** | P0 — board mandate |
| **Overall status** | 🔴 Behind |
| **Last updated** | April 13, 2026 |

---

## Objective

Achieve SOC 2 Type II certification by August 2026. 100 controls total. Currently 48 complete, 18 not started. Audit window: August 2026 with Deloitte.

## Why now

Board mandate post-IPO. Enterprise customers in $50M+ pipeline contractually requiring SOC 2 Type II before signing. Two deals ($8M combined) have 90-day deadline clauses — if certification not in progress by May 2026, they walk. Deloitte audit date is fixed — any slip = certification failure.

---

## Control distribution by team (as of April 13, 2026)

| Team | Controls owned | Complete | In progress | Not started |
|------|---------------|----------|-------------|-------------|
| Security & Compliance Eng | 28 | 22 | 6 | 0 |
| Core Infrastructure | 22 | 8 | 12 | 2 |
| Model Serving (NovaAI) | 12 | 3 | 5 | **4 — IAM-blocked** |
| Governance & Catalog | 10 | 5 | 3 | 2 |
| Pipeline Orchestration | 8 | 4 | 3 | 1 |
| Query Engine | 8 | 3 | 4 | 1 |
| Developer Experience | 6 | 2 | 4 | 0 |
| Storage & Indexing | 6 | 1 | 5 | 0 |
| **Total** | **100** | **48** | **42** | **10 (14 IAM-blocked separately)** |

**14 controls remain blocked on NEXUS IAM** — Auth0 contract punted Mar 18, NEXUS M6 now Aug 28. These controls cannot proceed on current path. Parallel path required or Deloitte engagement at risk.

---

## Milestone plan

| Milestone | Description | Target | Status | Owner |
|-----------|-------------|--------|--------|-------|
| M1 | Control gap analysis complete | Jan 2026 | ✅ Done | Fatima A. |
| M2 | All controls assigned to owners | Feb 2026 | ✅ Done | Fatima A. |
| M3 | 70 controls complete | Jun 2026 | 🟡 At risk | James W. |
| M4 | 100 controls complete | Jul 2026 | 🔴 Behind | James W. |
| M5 | Audit evidence package submitted to Deloitte | Jul 2026 | 🟡 At risk | Fatima A. |
| M6 | SOC 2 Type II certification received | Aug 2026 | ⬜ Not started | James W. |

**M3 slipped from May to June** — mandate-driven recovery improved trajectory but starting position (34 complete) required more runway. At 6-8 controls/week, Jun 1 is achievable if IAM-blocked controls are treated separately.

---

## Risk register

| ID | Risk | Likelihood | Impact | Owner | Mitigation | Status |
|----|------|-----------|--------|-------|-----------|--------|
| R-001 | 14 controls blocked on NEXUS IAM — Auth0 punt confirmed, NEXUS M6 now Aug 28 | High | Critical | Sara L. / James W. | Must find parallel path (compensating controls or scope exception with Deloitte) | 🔴 Escalated — no resolution |
| R-002 | Yuki mandate holding but teams risk reverting to roadmap work as sprint pressure builds | Medium | High | Fatima A. | Weekly check-in with each team DRI. Karl to re-confirm mandate at Apr 17 SteerCo. | 🟡 Monitoring |
| R-003 | May 1 SOC2 evidence deadline for Meridian Financial ($4.2M deal) — 90-day legal clause | High | Critical | Fatima A. / Marcus C. | Fatima to confirm evidence package format with Deloitte by Apr 25. Must show 70+ controls in progress by May 1. | 🔴 Active |
| R-004 | August audit date immovable — Deloitte contract fixed ($180K fee) | — | Critical | James W. | No mitigation — must hit date | Constraint |
| R-005 | Security Eng team split across SHIELD + ATLAS + NEXUS | High | High | Karl Bergstrom | ATLAS SSO (M3) closing Apr 25 — will free 25% Sec Eng capacity for SHIELD Wave 3 | 🟡 Resolving |
| R-006 | Model Serving team mandate compliance — 4 non-IAM controls assigned but team stretched | Medium | High | Leo N. | Leo assigned as DRI. Apr 7 Sprint showed 2 controls started. | 🟡 In progress |

---

## Inbound dependencies

| Needs from | What | When | Risk if late |
|-----------|------|------|-------------|
| NEXUS | IAM unification (14 controls require it) | **Aug 28** (slipped from Jul) | 14 controls cannot be completed — Deloitte gap |
| MERIDIAN | v2 API audit logging capability | Apr 2026 | 8 controls now unblocked (MERIDIAN M1 complete Apr 3) |
| PULSE | Pipeline audit trail (Temporal migration) | Aug 2026 | 6 controls at risk |

---

## Outbound dependencies (what SHIELD provides)

| Program | What SHIELD provides | When needed |
|---------|---------------------|-------------|
| ATLAS | SOC 2 evidence package for enterprise deals | May 2026 (deals closing Jun+) |

---

## Stakeholders

| Name | Role | Engagement |
|------|------|-----------|
| James Whitfield | CISO — Executive Sponsor | Weekly |
| Priya Anand | CEO — board accountability | Monthly |
| Yuki Tanaka | VP Eng — team prioritization mandate | Weekly |
| Deloitte | External auditor | Milestone-based |

---

## Latest update (April 13, 2026)

Significant improvement in trajectory since March 11. Yuki Tanaka issued exec mandate March 25 — all 8 teams began controls by March 30. Controls complete: 34 → 48 in 3.5 weeks. All controls now have assigned owners. MERIDIAN M1 completing April 3 unblocked the 8 controls that were waiting on API audit logging — those are now in progress.

Critical open issue: 14 controls remain blocked on NEXUS IAM. Auth0 contract was punted again by James Whitfield on March 18 — NEXUS M6 now targets August 28. Fatima escalated to Karl Bergstrom: without a parallel path or compensating controls agreed with Deloitte, 14 controls cannot complete before the Deloitte evidence package deadline (July 15). Fatima is scheduling a call with Deloitte to explore whether compensating controls or phased attestation is acceptable.

Near-term priority: evidence package format confirmation with Deloitte by April 25, to ensure the May 1 deadline for Meridian Financial's 90-day clause can be met with a credible "in-progress" package.
