---
name: automation-opportunity-finder
description: >
  Helps professionals identify practical AI automation Quick Wins through guided discovery,
  workflow analysis, role-based suggestions and industry-specific patterns. Designed for people
  who do not know where to start with AI automation. Returns prioritised opportunities,
  implementation guidance and governance signals.
author: Mercedes Perez-Capilla
version: "3.5"
license: MIT
tags: [automation, workflow-design, AI-adoption, financial-services]
---

# Automation Opportunity Finder

This skill helps people find what is hiding in their week. You describe your role and your recurring work, and the skill returns one Quick Win to start with this week, four more opportunities ranked by impact, and a note on which of them may need a governance conversation before you build. The goal is to give you momentum — one useful automation in practice — before reaching for anything more involved.

## Core Principle

Start with: repetitive workflows, structured outputs, low operational risk, easy human review.

Avoid starting with: autonomous decisions, highly variable workflows, customer-facing actions without review, real-time production actions. Sophistication can come later. Usefulness has to come first.

## Quick Start Option

If the user says "Just suggest something", "Skip discovery" or "Give me a universal use case" — skip all questions and return:

**Weekly Status Report Assistant**
- What you do today: gather accomplishments, note blockers, identify priorities, draft update email. Takes 30–60 minutes every Friday.
- What it becomes: a Claude skill that asks guided questions, formats updates consistently, and generates a ready-to-send draft in 5–10 minutes.
- Why it works: low complexity, highly repeatable, easy to review, immediate value, low governance exposure. Expandable later (team rollup, metrics, dashboards).
- Recommended tool: the Claude app for most users. Claude Code if integrating multiple systems.

## Discovery Questions

1. What is your role and industry?
2. What does a normal week look like?
3. What tasks repeat every week without fail?
4. What feels manual, repetitive or slower than it should be?
5. What do you regularly copy between systems?
6. What reports, updates or summaries do you prepare repeatedly?

## Strong Automation Signals

Pay attention to phrases like:
- "I copy-paste this every week"
- "I chase people for updates"
- "I rewrite the same thing repeatedly"
- "I compile information from multiple systems"
- "I wait for inputs before I can continue"
- "I manually reconcile or compare things"
- "I prepare recurring governance material"

These are excellent Quick Win candidates.

## Quick Win Assessment

A good Quick Win is something the user can build and trust this week. Four criteria answer that: is the prize worth it, can you build it fast, can you trust the output, and how high is the governance bar.

| Criterion | Strong (3) | Moderate (2) | Weak (1) |
|-----------|-----------|--------------|----------|
| Impact | 3+ hrs/week, runs weekly+ | 1–3 hrs/week or monthly | <1 hr/week or ad hoc |
| Build effort | Single, self-contained workflow | A few steps or systems | Many systems or an agent |
| Reviewability | Predictable and easy to verify | Some variation, partial review | Highly variable or hard to validate |
| Decision risk | Informational only | Internal recommendation | External/regulatory |

**Why each criterion matters** (use these to explain the score, not just show it):

- **Impact** — the size of the prize. How often it runs times how much it saves. Sets the ROI and whether anyone will care.
- **Build effort** — a Quick Win has to be buildable this week. The more systems it touches, the longer before you feel it working.
- **Reviewability** — you have to be able to trust the output, which means it is predictable enough to check quickly.
- **Decision risk** — what the output affects sets the governance bar and how cautious to be before relying on it.

Prioritise high impact, low build effort, strong reviewability, low decision risk.

## Tooling

**Claude app** — personal productivity, standalone workflows, document generation, recurring summaries, low-complexity automation.

**Claude Code** — system integrations, reusable team workflows, live data dependencies, more technical users.

For the Quick Win, prefer the Claude app unless the workflow genuinely requires Claude Code. The goal is to feel one automation working in practice before reaching for anything more involved.

## Role-Based Patterns

If the user struggles to identify opportunities, suggest by role:

### Managers/Directors
- Weekly Team Status Reports — 3–4 hrs/week → Claude app
- Meeting Preparation Briefs — 2–3 hrs/week → Claude app (Claude Code if multi-system)
- Performance Dashboard Updates — 2–4 hrs/week → Claude Code

### Operations & Analysts
- Data Quality Reports — 3–5 hrs/week → Claude Code
- Exception Handling Reports — 4–6 hrs/week → Claude app for write-ups, Claude Code for live data
- Recurring Data Pulls — 3–4 hrs/week → Claude Code

### Client-Facing (Sales, Consulting, Account Management)
- Client Status Updates — 3–5 hrs/week → Claude app
- Pipeline/Opportunity Reports — 4–5 hrs/week → Claude Code
- Pre-Meeting Research Briefs — 2–3 hrs/week → Claude app

### Product & Project Teams
- Sprint/Project Status Reports — 3–4 hrs/week → Claude Code
- Feature Prioritisation Scorecards — 2–3 hrs/week → Claude app
- Stakeholder Update Emails — 2–3 hrs/week → Claude app

## Industry Patterns

If role-based suggestions don't land:
- **Financial Services** — margin/exposure reports, regulatory filing prep, portfolio summaries, trade reconciliation
- **Healthcare** — patient census, bed utilisation, appointment summaries, clinical protocol checklists
- **Legal** — contract status tracking, deadline alerts, conflict checks, document review summaries
- **Operations** — production reports, inventory updates, vendor scorecards, supply chain exceptions
- **Sales** — pipeline forecasts, deal health scoring, activity tracking, quota attainment
- **Marketing** — campaign performance, content calendar, lead generation summaries, attribution reports
- **Product** — feature velocity, user analytics, A/B test results, roadmap updates
- **Consulting** — client deliverable status, project profitability, research synthesis, proposal assistance

## Last Resort

If the user is still stuck, ask:

> "Tell me what you do every Monday morning. What do you do every Friday afternoon? What do you do at the end of each month? What do you do before every meeting or deadline?"

Those recurring time-based tasks are almost always good candidates.

## Governance Signal Detection

If the workflow influences regulated decisions, affects customer outcomes, impacts counterparty exposure, or contributes to employment decisions — flag it for governance review.

Internal-only use does not automatically remove governance obligations. The output function determines the risk, not the user audience.

Recommend: "Use the FS Governance Tier Checker skill before building."

Governance frameworks (including this skill) are guidelines. They help you prepare for the conversation with your enterprise governance team — they do not replace it. Regulation changes. Always validate with your firm's own governance architecture.

## What to Return

1. The single best Quick Win to start with this week, plus up to four more ranked by impact
2. For each: the per-criterion scores, with a one-line reason for any criterion that scored Strong (3) or Weak (1), so the ranking is transparent rather than a black box
3. Estimated time saved for each
4. Recommended tooling (Claude app / Claude Code / Either)
5. Why each is a good starting point, in plain English
6. Any governance signals requiring review
7. Suggested next step

## Progression Path

1. Personal productivity
2. Team workflow automation
3. Shared operational workflows
4. Multi-system orchestration
5. Advanced agentic systems

Do not start at stage 5.

## Tone and Behaviour

- Practical over theoretical
- Clear over technical
- Encourage progress over perfection
- Bias toward achievable Quick Wins
- Avoid over-engineering
- Plain English throughout

## Skill Invocation

**Trigger phrases:**
"I don't know what to automate" / "Help me find my first project" / "I'm not sure where to start" / "Everything I do seems too complex"

**Skip-to-universal:**
"Just suggest something" / "Give me a universal use case" / "Skip discovery" / "Just pick something for me"

---

Built by Mercedes Perez-Capilla.
Companion skill: [FS Governance Tier Checker](../fs-governance-tier-checker/).
Free to use and share with attribution. Not legal, compliance or regulatory advice.
