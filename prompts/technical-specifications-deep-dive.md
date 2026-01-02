# Technical Specifications for Technical Program Managers

## Overview

A prompt template that translates dense technical specifications into actionable program management insights. Extracts dependencies, risks, and smart questions without requiring deep technical expertise.

## Use Case

**Problem:** TPMs receive complex technical specifications (Kubernetes migrations, database sharding, API rewrites, etc.) and need to quickly understand:
- What could block the program
- Which teams need coordination  
- What questions demonstrate TPM competence

Reading the full spec and Googling terms wastes time. Asking engineers basic questions wastes their time and undermines credibility.

**Solution:** A structured prompt that extracts program-relevant insights from any technical document in 30 seconds.

**TPM Value:** Show up to technical meetings asking the RIGHT questions—ones that surface hidden risks and demonstrate you understand program implications (not implementation details).

## The Prompt
```
I'm a Technical Program Manager coordinating this [migration/project]. 
I need to understand program risks, not implementation details.

Analyze this technical spec and tell me:

1. What's the one-sentence business case? (Why are we doing this?)

2. What are the 3 highest-risk dependencies for program execution?
   (Focus on what could derail timeline or require escalation)

3. What cross-team coordination will be most painful?
   (Where will miscommunication cause problems?)

4. What questions should I ask in the kickoff meeting to show I 
   understand the real risks? (Not "what is X" questions - 
   questions that make engineers respect the TPM role)

5. What's not mentioned in this spec that I should be worried about?
   (Hidden risks, unstated assumptions, political landmines)

Technical Spec: [paste your spec here]
```

## Example: Kubernetes Migration

### Input Document
```
Technical Design: EKS Migration & Service Mesh Implementation

Background:
Current: 47 services on EC2 with Consul for service discovery
Target: Amazon EKS with Istio service mesh

Why Now:
- EC2 scaling delays (15-20 min)
- Manual deployments causing bottlenecks
- No centralized observability
- Cost reduction: $180K/month → $120K/month

Architecture Changes:
- EC2 ASG → EKS with Kubernetes HPA
- Consul → Istio service mesh
- Application logs → Centralized (Fluentd → CloudWatch)
- HAProxy → Istio ingress gateway

Migration Strategy:
- Strangler pattern (gradual service migration)
- Blue/green per service
- 6-month timeline, 8 services/month
- EC2 parallel for 3 months

Dependencies:
- Platform: EKS cluster provisioning (4 weeks) - BLOCKS ALL
- Security: mTLS review (2 weeks) - HIGH RISK
- SRE: Runbook updates, oncall training
- Product teams: Dockerize, update CI/CD

Risks:
- 6 services need stateful redesign
- Database connection pooling required
- IP allowlisting breaks third-party integrations
- Only 3/12 engineers know Kubernetes

Performance:
- Deployment: 45 min → 5 min
- Scaling: 15-20 min → 30 sec
- Potential 10-15% latency increase during cutover

Cost:
- Current: $180K/month
- Target: $120K/month
- Migration: $200K (contractors, tooling)
```

### AI Output

**1. Business Case:**
Cut infrastructure costs 33% ($60K/month) while reducing deployment time from 45 minutes to 5 minutes.

**2. Top 3 Program Risks:**

**Risk #1: Platform Team 4-Week Block**
EKS cluster is critical path. If Platform is busy, entire 6-month timeline slips.
→ Action: Confirm capacity THIS WEEK. Get executive air cover if needed.

**Risk #2: 6 Services Need Redesign (Understated)**
"Stateful services need redesign" could be 3-6 months of architecture work not in timeline.
→ Action: Demand list of 6 services in kickoff. Assess feasibility.

**Risk #3: 75% Team Has No Kubernetes Experience**
Only 3/12 engineers trained. First migration will be a learning disaster.
→ Action: Propose training sprint OR contractor pairing for first 2 services.

**3. Painful Coordination:**

**Security's mTLS Review (Hidden Minefield)**
"2-week review" is optimistic. mTLS affects every service call. Security is understaffed.

**IP Allowlisting Breaks Integrations**
Third-party tools use IP allowlists. Pod IPs are ephemeral. This breaks AFTER migration.

**4. Smart Questions for Kickoff:**

❌ Don't ask: "What is Kubernetes?"
✅ Ask: "What's our rollback strategy if first service causes production issues?"

❌ Don't ask: "Why Istio?"
✅ Ask: "The 6 services needing redesign—are they identified? What's the effort? Is that in the 6-month timeline?"

❌ Don't ask: "What's mTLS?"
✅ Ask: "Security review is 2 weeks. Have we engaged them? What's their actual SLA?"

✅ Killer question: "Third-party integrations use IP allowlisting. Pod IPs change. NAT gateway strategy or contract renegotiation?"

**5. Not in Spec (But Should Worry You):**

🚨 No data migration strategy mentioned
🚨 Running both systems = no cost savings until month 4
🚨 No rollback plan
🚨 8 services/month with 75% untrained team = aggressive

## Use Cases

This prompt works for any technical specification:

### Cloud Migrations
- AWS → GCP
- On-premise → Cloud
- Multi-cloud strategies

### Architecture Changes
- Monolith → Microservices
- Database sharding
- API gateway implementations
- Cache layer additions

### Infrastructure Updates
- CI/CD pipeline changes
- Observability tooling
- Service mesh implementations
- Container orchestration

### Data Platform
- Data warehouse migrations
- Stream processing architectures
- ETL → ELT transformations

## Customization

Adjust the prompt based on your context:

**For early-stage discussions:**
Add: "What assumptions are we making that need validation?"

**For vendor evaluations:**
Add: "What are the build vs. buy trade-offs not mentioned?"

**For compliance-heavy projects:**
Add: "What regulatory or security considerations are understated?"

**For distributed teams:**
Add: "What timezone or communication challenges will slow this down?"

## Tips for Best Results

1. **Paste the entire spec** - Don't summarize; let AI extract what matters
2. **Use with any LLM** - Works in ChatGPT, Claude, Gemini
3. **Iterate on questions** - If output is too technical, add "Keep it program-focused, not implementation-focused"
4. **Save the output** - Use for meeting prep and stakeholder updates
5. **Share with team** - Helps everyone align on program risks vs. technical risks

## Expected Time Savings

**Before:**
- 20-30 min reading spec
- 10-15 min Googling terms
- 15-20 min formulating questions
- Total: 45-65 minutes

**After:**
- 30 seconds running prompt
- 2 minutes reading output
- Total: 2.5 minutes

**Savings: ~45-60 minutes per technical spec**

## Limitations

- AI may miss company-specific context (team dynamics, past failures)
- Political considerations require human judgment
- Some technical decisions need deeper dive (AI flags when to dig deeper)
- Works best with written specs (less effective with verbal discussions)

## Related Prompts

- **Risk Audit Prompt** - Identify hidden program risks
- **Stakeholder Update Generator** - Turn technical updates into exec-friendly summaries
- **Dependency Mapper** - Extract cross-team dependencies from project plans

---

*Part of the TPM AI Use Cases collection by Michi Götz*
