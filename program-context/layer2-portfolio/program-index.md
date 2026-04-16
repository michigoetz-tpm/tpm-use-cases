# NovaGrid — Program Index
*Layer 2 context · Load for cross-program work · Update cadence: weekly*

> One row per program. For full detail on any program, load `layer3-programs/[program]-master.md`.
> For cross-program dependencies, load `dependency-matrix.md`.

---

## Active program portfolio (April 2026)

*Last updated: April 13, 2026 — simulated state advanced from March 11 baseline*

| Code | Program | TPM | Phase | Priority | Overall | Next milestone | Next milestone date |
|------|---------|-----|-------|----------|---------|----------------|-------------------|
| **NEXUS** | Platform Re-architecture & Service Consolidation | Sara Lindqvist | Execution | P0 | 🟡 At risk | First 60 services retired (M4) | May 2026 |
| **ATLAS** | Enterprise NovaAI Launch | Marcus Chen | Execution | P0 | 🟡 At risk | SSO integration live (M3) | Apr 25 2026 |
| **SHIELD** | SOC 2 Type II Certification | Fatima Al-Hassan | Execution | P0 | 🔴 Behind | 70 controls complete (M3) | **Jun 2026** |
| **MERIDIAN** | API Consolidation & v1 Deprecation | James Okonkwo | Execution | P1 | 🟡 At risk | Migration tooling + guides (M4) | Apr 18 2026 |
| **PULSE** | Data Pipeline Overhaul (Airflow → Temporal) | Yuna Park | Execution | P1 | 🔴 Behind | DataCore pipelines migrated (M3) | May 2026 |
| **HORIZON** | Mobile Platform — iOS & Android | Priya Kaur | Execution | P1 | 🔴 Behind | Backend API contracts (M3) | Apr 18 2026 |
| **SPARK** | NovaAI v2 Core Platform | Daniel Rios | **Execution** | P1 | 🟡 At risk | Model serving alpha (M2) | **Aug 11 2026** |

**RAG key:** 🟢 On track · 🟡 At risk (recoverable) · 🔴 Behind (requires escalation)

---

## OKR alignment

| Company OKR | Programs on the hook |
|-------------|---------------------|
| O1: Enterprise readiness (SOC 2 Aug 2026) | SHIELD · NEXUS · ATLAS |
| O2: NovaAI at 20% ARR | ATLAS · SPARK |
| O3: Platform consolidation (<200 services) | NEXUS · MERIDIAN · PULSE |
| O4: Developer experience + Mobile | MERIDIAN · HORIZON |
| O5: Gross margin ≥72% | NEXUS (cost) · PULSE (infra cost) |

---

## Portfolio health summary (April 13, 2026)

- **3 of 7 programs red** — SHIELD, PULSE, HORIZON (MERIDIAN upgraded to amber)
- **SPARK moved to Execution** — M1 architecture review completed March 24
- **Auth0 cascade confirmed:** NEXUS IAM slipped to Aug 28 — SHIELD 14 controls blocked, HORIZON GA Aug 31, ATLAS workaround entrenched
- **Revenue exposure:** $4M mobile-dependent deals at elevated risk (Kestrel budget cycle Jul 31 vs GA Aug 31; Solaris Palantir eval active)
- **Positive signals:** MERIDIAN M1 complete (Apr 3), SHIELD mandate working (+14 controls), ATLAS SSO demo succeeded Apr 2 (Apex Health advanced to POC), DataCore recovery (47% → 71%)
- **Imminent decision:** Amara Osei (PULSE) Apr 15 — SDK vs migration determines $380K–$760K dual-run cost exposure
- **Critical action:** Auth0 decision by May 1 (Yuki deadline) — single highest-leverage action across portfolio

---

## Program master doc locations

```
layer3-programs/
├── nexus-master.md
├── atlas-master.md
├── shield-master.md
├── meridian-master.md
├── pulse-master.md
├── horizon-master.md
└── spark-master.md
```
