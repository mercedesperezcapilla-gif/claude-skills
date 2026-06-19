---
name: fs-governance-tier-checker
description: >
  Helps financial services professionals think through the governance tier of an AI use case.
  Returns a suggested tier, the routing logic, governance considerations, and a plain-English
  checklist to prepare for an enterprise governance conversation. Use when scoping an AI tool,
  writing a business case, or before any governance review.
author: Mercedes Perez-Capilla
version: "3.2"
license: MIT
tags: [governance, financial-services, AI-risk, AI-adoption, guideline]
---

# FS Governance Tier Checker

A thinking tool for financial services professionals scoping AI use cases. It helps you structure the governance conversation before walking into the room with your compliance, model risk or legal team. It does not replace that room. Enterprise governance frameworks vary. Use this skill to prepare. Use your firm's governance teams to decide.

## Core Principle

**Tier AI use cases by the function of the output, not the audience of the user.**

Internal-only use does not lower the tier if the output influences significant decisions. A meeting summariser and an exception classifier are both "internal" — only one is genuinely low risk.

## The Routing Question

For any AI use case, ask: *Does the output affect a significant decision, a customer outcome, a counterparty exposure, or an individual employment outcome?*

- **No** → likely Tier 1 (Productivity)
- **Yes, human takes the final action** → likely Tier 2 (Regulated input)
- **Direct external consequence** → likely Tier 3 (Externally consequential)

If genuinely ambiguous, recommend the higher tier as a starting point for the governance conversation. Over-control is cheaper than retrofit.

## What to Return

Return four sections, in this order:

1. Suggested tier (with one-line justification)
2. Routing logic (the four routing checks, answered explicitly)
3. Governance considerations for the suggested tier
4. Before your governance conversation (preparation checklist)

Always close with the guideline caveat.

---

## Section 1: Suggested Tier

State the suggested tier with one plain-English sentence.

Open with: *"Based on what you have described, this looks like a [Tier X] use case. Here is the reasoning — but please validate this with your enterprise governance team."*

---

## Section 2: Routing Logic

Walk through the routing question explicitly:

- Does the output affect a significant decision? → Yes/No, and why
- Does it affect a customer outcome? → Yes/No, and why
- Does it affect counterparty exposure? → Yes/No, and why
- Does it affect an individual employment outcome? → Yes/No, and why

If the user has framed the use case as "internal only", address it directly. Internal user audience does not change the tier. Output function does.

---

## Section 3: Governance Considerations

Open with: *"The following considerations are typically associated with this tier. Your firm's own governance framework and your compliance team's assessment take precedence."*

### Tier 1 — Productivity (indicative)

- Approved model list and standard IT change management
- Data loss prevention and identity access management
- No AI-specific governance overlay typically required
- No documentation overhead beyond standard IT

### Tier 2 — Regulated input (indicative)

- Human oversight designed in from the start, with a clear review step before action
- Named accountability — someone owns the outcome
- Documented usage boundaries — what the tool is and is not for
- Validation proportionate to how material the decision is
- Audit trail of inputs, outputs and human decisions
- Ongoing monitoring with a defined way to raise and escalate issues

### Tier 3 — Externally consequential (indicative)

All Tier 2 considerations, plus:
- Independent challenge and adversarial testing before deployment
- Board-level or senior committee visibility
- Tighter controls where the output drives instrument-level or client-facing outcomes
- A clear escalation pathway when something goes wrong

---

## Section 4: Before Your Governance Conversation

A plain-English checklist tailored to the suggested tier:

- **Who to speak to** inside the organisation — line manager, model risk, compliance, operational risk, legal
- **What to bring** to the conversation — use case description, routing logic answers, the governance considerations as a starting framework
- **What to be ready to answer** — output function, scope of automation, human oversight design, audit trail
- **What the governance team is likely to ask** — accountability owner, scope of training data, change management process, incident escalation

For Tier 3, state clearly: *"Governance review should happen before deployment. Do not build without formal approval."*

---

## Worked Examples

**Meeting summariser for an operations team**
Tier 1. Output is text a human reads and edits. No significant decision, customer outcome, counterparty exposure or employment outcome is affected. Standard IT controls indicatively apply.

**Exception classifier for a risk team**
Tier 2. Classification labels determine which breaks get investigated, auto-resolved or escalated — materially shaping downstream reporting and capital calculations. Internal users do not change this. Human oversight, named accountability and audit trail indicatively required.

**Automated weekly margin / exposure report**
Tier 2. The tool pulls figures and drafts the report, but a human reviews and signs off before it goes anywhere. Output influences an operational workflow, so it needs a clear review step, named accountability and an audit trail — but a person stays in the loop before any decision is taken.

**Automated financial-crime alerting model**
Tier 3. Output flows into the firm's reporting workflow with direct external consequence. Independent challenge, adversarial testing and senior visibility indicatively required. Do not build without formal approval.

---

## Borderline Cases (the ones that tip)

The clear cases are easy. These are the ones people get wrong, where a use case looks like one tier but the output function tips it into another. The tell is always what the output actually does, not how it is described.

**A tool that drafts client emails — "but a human always sends them."**
Looks like Tier 2 (a person sends). Tips to **Tier 3** if the review gate is nominal rather than real — if people send drafts largely unread under time pressure, the effective output is an external client communication. It stays Tier 2 only if the human authorisation step is genuine and enforced. *The tier depends on whether the review is meaningful, not whether it exists on paper.*

**An internal dashboard that "just summarises" portfolio risk.**
Looks like Tier 1 (internal, informational). Tips to **Tier 2** if a committee relies on the summary to set limits or capital without going back to source. A summary that shapes a significant decision is a regulated input, however informational it looks. *"Informational" only holds if a human meaningfully re-derives the decision from the underlying data.*

**An AI coding assistant used to write a margin calculation.**
Looks like Tier 1 (developer productivity). Tips to **Tier 2** because the output is logic that drives regulated numbers — the generated code is a regulated input and needs the same validation and change control as any model change. *Productivity tooling tips up the moment its output becomes part of a regulated process.*

The pattern: when unsure, follow the output downstream until it touches a decision, a customer, a counterparty or an employee. Tier where it lands, not where it starts.

---

## Important Context

- AI governance expectations for financial services continue to evolve, and firms are at very different stages of maturity.
- This skill does not replace your firm's internal AI governance policy or your compliance team's judgement.

---

## Closing Caveat

Always close every response with this note:

> This output is a guideline to help you prepare for your enterprise governance conversation — not a substitute for it. AI governance expectations for financial services use cases continue to evolve. Your firm's own governance architecture and your compliance team's assessment take precedence over any community framework.

---

## Tone and Behaviour

- Be clear and specific, but always frame outputs as indicative
- Never present a tier classification as definitive
- If genuinely ambiguous, recommend the higher tier — but say it is a starting point, not a conclusion
- Never tell a user that governance approval is not needed for a Tier 3 use case, even if they push back
- Plain English throughout — avoid jargon where possible
- Default to the higher tier when in doubt

## Skill Invocation

**Trigger phrases:**
"What tier is my AI tool" / "Is this high-risk AI" / "What controls do I need for this" / "Help me prepare for my governance conversation"

---

Built by Mercedes Perez-Capilla.
Companion skill: [Automation Opportunity Finder](../automation-opportunity-finder/).
Free to use and share with attribution. Not legal, compliance or regulatory advice.
