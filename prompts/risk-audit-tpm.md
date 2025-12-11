# Risk Audit Prompt for Technical Program Managers

## Overview

A prompt template that analyzes project documents to surface hidden risks before they derail programs. Identifies risks that aren't being tracked, assesses likelihood × impact, and provides early warning indicators for proactive monitoring.

## Use Case

**Problem:** TPMs spend hours in status meetings asking "Any blockers?" and everyone says "all good." Then you hit:
- Vendor approvals no one mentioned
- Key team member leaving during critical phase
- Dependencies on unfinished work from other teams
- Budget approvals still pending
- Assumptions that turn out to be wrong

Traditional risk registers capture obvious risks. Hidden risks live in Slack threads, meeting notes, off-hand comments, and document footnotes.

**Solution:** A structured prompt that analyzes all your project documents together to identify hidden risks, assess their true impact, and provide early warning signs.

**TPM Value:** Move from reactive firefighting to proactive risk monitoring. Surface risks when they're manageable, not when they're crises.

## The Prompt

```
I'm a Technical Program Manager running a risk audit on this program.

Analyze these project documents and tell me:

1. What are the top 5 hidden risks that could derail this program?
   (Not the obvious ones already being tracked - the ones people 
   aren't talking about)

2. Which risks have the highest likelihood AND highest impact?
   (Focus on the dangerous combination - use a 2x2 matrix if helpful)

3. What dependencies are understated or missing?
   (External teams, vendors, approvals, resources, infrastructure)

4. What assumptions are being made that could be wrong?
   (Timeline assumptions, resource availability, technical feasibility,
   budget estimates, stakeholder alignment)

5. What's the earliest warning sign for each top risk?
   (So I can set up monitoring, alerts, or check-ins)

Project Documents: [paste status updates, meeting notes, specs, emails, Slack threads, etc.]
```

## Example: Platform Migration Program

### Input Documents

**Week 1 Status Update:**
```
EKS Migration - Week 1 Update

Progress:
✅ Kickoff meeting completed with all stakeholders
✅ Project charter approved by CTO
✅ Initial EKS cluster design reviewed

Next Week:
- Platform team to start EKS cluster provisioning
- Security team to review mTLS architecture
- Begin team training on Kubernetes basics

Risks:
- None identified yet

Overall Status: 🟢 Green
```

**Week 2 Status Update:**
```
EKS Migration - Week 2 Update

Progress:
✅ Platform team started cluster provisioning (slight delay)
✅ Ordered Kubernetes training for engineering team
✅ Identified first 3 pilot services

Blockers:
- Platform team lead (Sarah) mentioned she might be unavailable 
  in Q2 but will delegate
- Security team hasn't responded to meeting invite yet

Next Week:
- Complete EKS cluster setup
- Finalize security review schedule
- Start Dockerizing pilot services

Overall Status: 🟢 Green
```

**Week 3 Status Update:**
```
EKS Migration - Week 3 Update

Progress:
✅ EKS cluster 80% complete (Platform team working on it)
✅ 12 engineers completed Kubernetes training
✅ First service (image-service) containerized

Updates:
- Sarah confirmed she's going on maternity leave in April
- Security team said they'll "fit in the review when they can"
- Finance approved the project (verbally in hallway)
- Discovered only 2 out of 12 product teams have Docker experience

Next Week:
- Finish EKS cluster
- Start security review (hopefully)
- Containerize notification-service

Overall Status: 🟢 Green
```

**Technical Spec Excerpt:**
```
Cost Analysis:
- Current: $180K/month
- Target: $125K/month  
- Migration cost: $200K
- Parallel run: 3 months (both systems running)
- Payback: 3.6 months

Open Questions:
- AWS budget approval process? (mentioned "approved" in status)
- IP allowlisting for Stripe, Segment, PagerDuty (NOT ADDRESSED YET)
```

### AI Output

**1. Top 5 Hidden Risks:**

**Risk #1: Sarah (Platform Lead) Going on Maternity Leave Mid-Migration**
- **Context:** Mentioned casually in Week 2 ("might be unavailable"), confirmed in Week 3 (April = middle of Phase 2)
- **Why Hidden:** Status shows "will delegate" but no delegation plan exists
- **Why Dangerous:** She's the only person who knows the EKS setup. No knowledge transfer has started. Phase 2 is complex (stateful services).
- **Likelihood:** HIGH (confirmed event) | **Impact:** HIGH (blocks critical path)

**Risk #2: Finance "Approved Verbally in Hallway"**
- **Context:** Week 3 mentions "Finance approved the project (verbally in hallway)"
- **Why Hidden:** No PO, no budget code, no written approval
- **Why Dangerous:** Parallel run costs $360K (3 months × $120K extra). Spec shows $200K migration cost but doesn't call out parallel run separately. Finance might not know about the $360K.
- **Likelihood:** MEDIUM (might be real approval) | **Impact:** HIGH (program halts if funding pulled)

**Risk #3: Security Team "Will Fit It In"**
- **Context:** Week 2 "hasn't responded to meeting invite," Week 3 "will fit in the review when they can"
- **Why Hidden:** No escalation, treated as minor scheduling issue
- **Why Dangerous:** Security review blocks entire migration (can't deploy without mTLS approval). Spec mentions Security team has 6-week backlog. "When they can" could be months.
- **Likelihood:** HIGH (already showing avoidance) | **Impact:** HIGH (blocks critical path)

**Risk #4: Only 2/12 Teams Have Docker Experience**
- **Context:** Discovered in Week 3, mentioned casually
- **Why Hidden:** Spec assumes teams can "Dockerize services" (2-3 weeks per service)
- **Why Dangerous:** 10 teams need to learn Docker + containerize services. First team already took full week for one service. 35 services to go. Timeline assumes expertise that doesn't exist.
- **Likelihood:** HIGH (already manifesting) | **Impact:** MEDIUM (delays but manageable)

**Risk #5: IP Allowlisting "NOT ADDRESSED YET"**
- **Context:** In spec under "Open Questions," not in status updates
- **Why Hidden:** Treated as technical detail, not program risk
- **Why Dangerous:** Stripe, Segment, PagerDuty require static IPs. Kubernetes uses ephemeral IPs. Requires vendor contract renegotiation (4-8 weeks per vendor) + legal involvement + possible NAT Gateway (adds cost/latency).
- **Likelihood:** HIGH (will definitely surface) | **Impact:** MEDIUM (delays but has workarounds)

**2. Highest Likelihood × Impact (2×2 Matrix):**

```
HIGH IMPACT
    │
    │  [Risk #1: Sarah Leave]    [Risk #3: Security]
    │  [Risk #2: Finance]
    │
    │  [Risk #5: IP Allow]        [Risk #4: Docker Skills]
    │
    └──────────────────────────────────────────
                                    HIGH LIKELIHOOD
```

**Immediate attention required:**
1. Sarah's maternity leave (HIGH/HIGH)
2. Security team engagement (HIGH/HIGH)
3. Finance written approval (MEDIUM/HIGH)

**3. Understated/Missing Dependencies:**

**Missing:**
- **Knowledge Transfer Plan:** Sarah leaving but no successor identified, no documentation started
- **Security Team Capacity:** Not on their roadmap, no commitment, treating as "when we can"
- **Written Finance Approval:** Verbal approval is not a dependency closure
- **Vendor Legal Timelines:** IP allowlisting requires procurement/legal, not mentioned
- **Training Ramp-Up Time:** Teams learning Docker mid-migration not accounted for

**Understated:**
- **Platform Team Capacity:** "Slight delay" in Week 2, Sarah's leave in Week 3 = resource constraint
- **Cross-Team Coordination:** Only 2/12 teams ready, 10 need hand-holding
- **Parallel Run Cost:** $360K called out in spec but not in finance approval conversation

**4. Wrong Assumptions:**

**Assumption #1: "Sarah will delegate"**
- **Reality Check:** No delegation plan, no backup identified, knowledge not documented
- **Risk:** Leaves in 6 weeks, middle of complex phase

**Assumption #2: "Finance approved the project"**
- **Reality Check:** Verbal hallway conversation ≠ budget commitment
- **Risk:** No PO, no budget code, parallel run cost not explicit

**Assumption #3: "Teams can Dockerize services in 2-3 weeks"**
- **Reality Check:** Only 2/12 teams have Docker experience, first service took 1 week
- **Risk:** Timeline assumes expertise that doesn't exist

**Assumption #4: "Security will fit it in"**
- **Reality Check:** They haven't responded to meeting invite, "when they can" = no commitment
- **Risk:** Could delay by 2+ months if not escalated

**Assumption #5: "Timeline is realistic"**
- **Reality Check:** Spec says "may need 8-9 months" but project shows 6 months
- **Risk:** Setting up for failure/scope creep

**Assumption #6: "Technical risks = program risks"**
- **Reality Check:** IP allowlisting is treated as technical footnote, it's a vendor/legal/timeline risk
- **Risk:** Will surface late when contracts need renegotiation

**5. Earliest Warning Signs (Monitoring/Alerts):**

**Risk #1: Sarah's Leave**
- **Warning Sign:** No calendar invites for knowledge transfer sessions by end of this week
- **Monitoring:** Check if successor is identified and documentation started
- **Action Trigger:** If no progress by Week 4, escalate to VP Eng

**Risk #2: Finance Approval**
- **Warning Sign:** No PO number or budget code assigned by Week 4
- **Monitoring:** Ask finance for written approval email with specific numbers
- **Action Trigger:** If no written approval by Week 5, halt spend on contractors

**Risk #3: Security Engagement**
- **Warning Sign:** No calendar invite accepted for security review by Week 4
- **Monitoring:** Escalate to Security Architect directly (skip team queue)
- **Action Trigger:** If no commitment by Week 5, get CTO to prioritize

**Risk #4: Docker Skills Gap**
- **Warning Sign:** Second team takes >2 weeks to containerize one service
- **Monitoring:** Track actual time per service vs. estimated
- **Action Trigger:** If >2 weeks, hire Docker contractors or extend timeline

**Risk #5: IP Allowlisting**
- **Warning Sign:** No vendor outreach initiated by Week 4
- **Monitoring:** Get list of affected vendors, start conversations NOW
- **Action Trigger:** If any vendor says "contract change needed," loop in legal immediately

**Risk #6: Timeline Realism (Meta-Risk)**
- **Warning Sign:** 3 consecutive weeks with "slight delays"
- **Monitoring:** Track actual progress vs. plan weekly
- **Action Trigger:** If >20% behind by Week 8, re-baseline timeline with stakeholders

## When to Use This Prompt

### Program Lifecycle
- **Week 1:** After kickoff, analyze all project docs to find risks before they manifest
- **Monthly:** Paste last 4 weeks of status updates, find emerging patterns
- **Before Exec Reviews:** Don't get blindsided by questions about risks you didn't see
- **Mid-Program Health Check:** When everything feels "too smooth"
- **Post-Incident:** After a surprise blocker, audit docs to see if signals were there

### Trigger Conditions
- Multiple "green" status updates in a row (complacency risk)
- Off-hand comments in meetings ("Sarah mentioned she might be unavailable")
- Vague commitments ("Security will fit it in when they can")
- Assumptions presented as facts ("Teams can Dockerize services")
- Dependencies marked "handled" without evidence

### Input Sources

**Best results when you include:**
- Status updates (last 2-4 weeks)
- Project specs and design docs
- Meeting notes (especially side conversations)
- Slack threads about the project
- Email threads with decisions/commitments
- Budget/finance discussions
- Org announcements (team changes, priorities)

**Pro Tip:** Include the "everything is fine" content. Hidden risks live in documents that look green.

## Customization

### For Different Risk Types

**For Resource Risks:**
Add: "Which team members or roles are single points of failure? Who has knowledge that isn't documented or shared?"

**For Vendor/External Dependencies:**
Add: "Which external dependencies have the longest lead times? What vendor/legal processes could delay us?"

**For Budget/Financial Risks:**
Add: "What cost assumptions could be wrong? Where is budget approval still informal or pending?"

**For Technical Risks:**
Add: "What technical assumptions need validation? What could we discover late that forces redesign?"

**For Political/Stakeholder Risks:**
Add: "What stakeholder misalignments exist? Where do different teams have conflicting priorities?"

### For Program Stage

**Early Stage (Weeks 1-4):**
Focus on: Dependencies, assumptions, resource gaps

**Mid-Stage (Execution):**
Focus on: Emerging patterns, team capacity, vendor delays

**Late Stage (Final Push):**
Focus on: Burnout risks, scope creep, post-launch support

## Tips for Best Results

### Input Quality
1. **More context = better analysis:** Paste 3-4 weeks of docs, not just one update
2. **Include "boring" documents:** Hidden risks live in routine status updates
3. **Don't pre-filter:** Let AI find the patterns, don't decide what's relevant
4. **Include side conversations:** Slack threads, meeting notes, hallway comments
5. **Add dates:** Helps AI track when things were first mentioned

### Interpreting Output
1. **Validate with team:** AI surfaces patterns, you confirm with reality
2. **Prioritize by likelihood × impact:** Focus on top-right quadrant first
3. **Set up monitoring:** Use early warning signs to track proactively
4. **Don't panic:** Finding risks early = you have time to mitigate
5. **Document decisions:** Track which risks you're accepting vs. mitigating

### Common Patterns AI Finds

**The "Mentioned Once" Risk:**
Something mentioned casually weeks ago, never followed up (e.g., Sarah's leave)

**The "Verbal Approval" Risk:**
Handshake agreements without documentation (e.g., finance "approval")

**The "When They Can" Risk:**
Vague commitments without specific dates (e.g., security review)

**The "Assumes Expertise" Risk:**
Timeline based on skills that don't exist (e.g., Docker knowledge)

**The "Footnote" Risk:**
Critical items buried in spec appendices (e.g., IP allowlisting)

**The "Too Smooth" Risk:**
Multiple green updates in a row = something's not being reported

## Expected Time Savings

**Before:**
- Weekly 1-hour risk review meetings (all stakeholders)
- Manual scanning of status updates
- Reactive discovery when risks become blockers
- Total: 2-3 hours per week + firefighting time

**After:**
- 5-minute prompt run (paste docs, read output)
- Proactive mitigation before risks escalate
- Targeted check-ins on specific risks only
- Total: 5 minutes + focused mitigation time

**Savings: ~2.5 hours per week, plus avoided firefighting**

## Limitations

- AI identifies patterns in text; political/cultural risks require human judgment
- Output quality depends on input quality (GIGO - garbage in, garbage out)
- Can't predict truly black swan events (vendor bankruptcy, org restructure)
- May flag false positives (treat as "things to validate" not "confirmed risks")
- Works best with written documentation; verbal-only cultures need notes

## Related Prompts

- **Technical Spec Translator** - Understand technical specs for program implications
- **Stakeholder Update Generator** - Turn findings into exec-friendly updates
- **Dependency Mapper** - Extract and visualize cross-team dependencies

## Real-World Results

**Case Study: Platform Migration**
- Week 3 audit surfaced Sarah's maternity leave risk
- Started knowledge transfer immediately (6 weeks before leave)
- Hired contractor as backup
- Migration continued smoothly when Sarah left

**Case Study: Product Launch**
- Monthly audit found vendor contract renewal pending
- Vendor required 4-week notice for changes
- Would have expired 2 weeks before launch
- Caught with 6 weeks to spare

**Case Study: Infrastructure Upgrade**
- Audit found "Security approved" was verbal only
- Formal review revealed PCI compliance gap
- Would have failed audit post-launch
- Fixed before go-live

---

*Part of the TPM AI Use Cases collection by Michi Götz*
