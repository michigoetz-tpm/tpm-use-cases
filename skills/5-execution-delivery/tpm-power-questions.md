---
name: tpm-power-questions
description: Surface the right TPM Power Question for any program situation. Use this skill whenever anyone — TPM, Engineering Lead, Product Manager — is preparing for a meeting, navigating a blocked program, running a retro, managing stakeholders, or deciding how much to trust an AI agent's output. Trigger phrases include: "what should I ask in this meeting?", "how do I surface this?", "the program feels off but I can't name it", "we're about to expand what the agent does", "I don't know how to push back without derailing this", "help me prepare for this review." Always run this skill before generating ad-hoc questions — it maps situation to the highest-leverage questions for cross-functional program contexts.
---

# /tpm-power-questions — Power Questions

**Lifecycle Stage:** Execution & Delivery
**Job-to-be-Done:** Surface the highest-leverage question for any program situation — meeting prep, mid-program diagnosis, blocked execution, retros, stakeholder reviews, and AI governance decisions

---

## Instructions

Read `domain-context.md` and `personal-context.md` before starting.

---

## Overview

A library of 30 questions for TPMs, Engineering Leads, and Product Managers navigating cross-functional programs. Organized by situation. Delivered based on what is actually happening, not a generic list.

Run a short workflow to identify the right mode, the right bucket, and the right questions before returning anything.

---

## Workflow

```
Describe situation
       |
       v
Is AI / an agent involved in this situation?
       |
      YES --> Mode 2: AI Governance Pre-flight (see below)
       |
       NO
       |
       v
What is the immediate need?
       |
  +---------+-----------+-----------+
  |         |           |           |
PREP     STUCK      RETRO      REVIEW
  |         |           |           |
  v         v           v           v
Alignment  Execution  Learning  Stakeholder
Scope      Blockers   Retro     Communication
Priority   Risk
```

**Mode 1: Situational lookup** — for meeting prep, mid-program diagnosis, retros, stakeholder reviews
**Mode 2: AI governance pre-flight** — for any situation where an agent is producing outputs, being expanded, or informing decisions

If the situation is ambiguous after reading the input, ask one question: "Is this about preparing for something, unblocking something, or reviewing something?"

---

## Mode 1: Situational Lookup

### Step 1: Identify the bucket

| Bucket | Trigger signals |
|--------|----------------|
| Alignment & Ownership | Teams have different answers, nobody owns the outcome, accountability is unclear, decisions keep getting re-litigated |
| Scope & Definition | Done is fuzzy, scope is growing, requirements keep shifting, milestones feel soft |
| Priority & Trade-offs | Everything is urgent, capacity is maxed, something needs to be cut, leadership wants it all |
| Risk & Dependency | Gut says it's going to break, dependency on another team, pre-mortem needed, timeline feels optimistic |
| Execution & Blockers | Team is stuck, standups feel performative, nothing is moving, blockers aren't surfacing |
| Stakeholders & Communication | Steering committee, exec review, sponsor 1:1, status update, not sure how leadership will react |
| Retrospective & Learning | Retro coming up, same problems repeating, want better retro questions than start/stop/continue |
| Scale & Strategy | This feels tactical not strategic, solving the wrong problem, platform vs. feature debate, 12-month horizon |

One situation can map to multiple buckets. Pull from all that apply.

### Step 2: Identify the role (infer from context, don't ask)

| Role signals | What changes |
|-------------|--------------|
| TPM signals: "my program", "cross-functional", "portfolio", "workstreams", "I'm coordinating" | Return questions focused on accountability, cross-team dynamics, escalation |
| Engineering Lead signals: "my team", "architecture", "technical debt", "engineers are flagging" | Return questions focused on technical risk, team needs, dependency ownership |
| PM signals: "roadmap", "customer", "product decision", "backlog priority" | Return questions focused on goal alignment, scope definition, stakeholder measurement |

If role is unclear, infer from the situation and proceed. Do not ask.

### Step 3: Return questions

Default: 3-5 questions. Return more only if explicitly asked.

**Output format varies by need:**

Pre-meeting prep (time pressure — someone is about to walk into a room):
- Questions only, no framing. Fast.

Mid-program diagnostic (something feels wrong but isn't named):
- Questions plus one line on what each is trying to surface.

Retro facilitation:
- Questions in sequence. Each one builds on the last.

---

## Mode 1: Full Question Library

### Alignment & Ownership

| # | Question | When to ask |
|---|----------|-------------|
| 1 | What problem are we solving, and is every team working on the same version of it? | When requirements feel inconsistent across workstreams |
| 2 | Who owns the outcome, not the task? | When accountability feels diffuse |
| 3 | Who makes the final call when teams disagree, and do they know that's their role? | When decisions stall or escalate sideways |
| 4 | Whose absence from this decision will create a problem later? | Before any major alignment meeting or decision |

### Scope & Definition

| # | Question | When to ask |
|---|----------|-------------|
| 5 | What does done mean, and who signs off on it? | Before committing to any milestone |
| 6 | What have we never explicitly agreed is out of scope? | When scope creep starts |
| 7 | Are we still solving the original problem, or did the goal quietly shift? | When delivery is moving but confidence in the direction is dropping |

### Priority & Trade-offs

| # | Question | When to ask |
|---|----------|-------------|
| 8 | Why is this the priority now, and what is deprioritized as a result? | When priority changes cascade across the program |
| 9 | What can we defer without touching the critical path? | When capacity hits a ceiling |
| 10 | What are we trading off, and does leadership understand it the same way the team does? | During scope or timeline negotiation |

### Risk & Dependency

| # | Question | When to ask |
|---|----------|-------------|
| 11 | Where is this program most likely to break, and who in the room knows but hasn't said it? | During risk review or pre-mortem |
| 12 | Which dependencies are owned by teams who don't know we depend on them? | Before scheduling milestones |
| 13 | What is the one thing that would break the timeline that we are not talking about? | Before any major phase commitment |
| 14 | How does this change land on the other programs in the portfolio? | When a change request comes in |

### Execution & Blockers

| # | Question | When to ask |
|---|----------|-------------|
| 15 | What is actually blocked today, not at risk, blocked? | During standups or daily check-ins |
| 16 | Which pending decision has the longest blast radius across teams? | When multiple workstreams stall simultaneously |
| 17 | What do you need from me, from leadership, or from another team to move? | When a team lead seems stuck or hesitant |
| 18 | What is the highest-leverage forcing function that would unblock the most right now? | When the team is stuck across multiple workstreams |

### Stakeholders & Communication

| # | Question | When to ask |
|---|----------|-------------|
| 19 | What is each stakeholder group actually measuring this program against? | Before a steering committee or exec review |
| 20 | What did leadership hear when we committed to this, and is that still what we are delivering? | Before any stakeholder update |
| 21 | Who needs to be in the room before this decision sticks? | Before any decision that will need re-litigating |
| 22 | Whose yes in this group means nothing without someone else's yes? | When alignment feels complete but fragile |

### Retrospective & Learning

| # | Question | When to ask |
|---|----------|-------------|
| 23 | What did this program reveal about how we actually work, not how we think we work? | During retrospectives |
| 24 | What slowed us down in ways that were not visible until it happened? | After a slip or near-miss |
| 25 | What are we doing because we have always done it, and what would happen if we just stopped? | When process overhead is slowing delivery |
| 29 | What did we know but not say — and why? | When retros stay surface-level and the real slowdowns never make it into the output |

### Scale & Strategy

| # | Question | When to ask |
|---|----------|-------------|
| 26 | What happens to other programs if we do not deliver this? | When evaluating urgency or pushback from leadership |
| 27 | Are we building the right thing, or just building it efficiently? | When delivery is fast but confidence in the direction is dropping |
| 28 | What does the engineering team need that nobody has asked for yet? | When engineers seem disengaged or flagging concerns quietly |
| 30 | What would have to be true for this to still be the right priority in six months? | When the program direction is set but the assumptions under it have not been revisited |

---

## Mode 2: AI Governance Pre-flight

Use when: an agent is producing outputs that inform decisions, an automated workflow is being expanded, someone is deciding how much to trust an AI output, or after any agent output that nobody questioned.

This mode returns all five governance questions as a sequential pre-flight. Not a lookup — a structured review before a decision.

Work through them in order. Each one gates the next.

| # | Question | What it surfaces |
|---|----------|-----------------|
| G1 | Which decisions in this program are we comfortable delegating to an agent, and which require a human in the loop? | The accountability boundary. Defines where agent authority stops before it acts, not after something goes wrong. |
| G2 | What is the source of truth for this program's status, and is it current enough for an agent to act on? | Data currency. An agent treats all data as equally fresh. The TPM knows which teams go dark before they escalate. |
| G3 | What assumption is this agent making that we have not validated? | The invisible input gap. The agent cannot model what it is missing. It only processes what it has. |
| G4 | What does this agent not know about how this team actually works? | Institutional knowledge gap. Org charts are formal authority. Real decision flow is learned over months. The agent acts on the org chart. |
| G5 | If this agent acts on bad data, what breaks, and who finds out how fast? | The feedback loop. The agent produces confident text regardless of input quality. The TPM has to design the human catch layer. |

If any answer surfaces a gap — an unvalidated assumption, a data source that is not current, a decision boundary that has not been set — that gap becomes a blocker before the agent is expanded or trusted.

Document the answer to each. The governance questions are only useful if the answers are written down.

---

## Output Rules

- No em dashes
- No filler ("Here are some questions to consider!")
- Lead with the questions, not with setup prose
- Pre-meeting prep: questions only, no framing — someone is about to walk into a room
- Diagnostic: questions plus one line on what each surfaces
- Governance pre-flight: all five in sequence, with "what it surfaces" column
- If the situation is genuinely ambiguous: ask one question before proceeding
