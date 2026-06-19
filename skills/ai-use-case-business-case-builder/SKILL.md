---
name: ai-use-case-business-case-builder
description: >
  Turns a scoped AI use case into a one-page internal business case that wins buy-in.
  Returns the problem and its current cost, the proposed automation in plain English,
  an ROI calculation, governance considerations, and a clear ask. Use after you have
  decided an AI tool is worth building and need to sell it internally to your manager,
  risk team, or budget holder.
author: Mercedes Perez-Capilla
version: "1.1"
license: MIT
tags: [governance, financial-services, AI-adoption, business-case, ROI, guideline]
---

# AI Use Case Business Case Builder

A drafting tool for the moment after you have decided an AI automation is worth building, and before you walk into the room to ask for it. It produces a one-page business case in plain English that a non-technical decision-maker can read in two minutes and say yes to.

It pairs naturally with the **FS Governance Tier Checker**: scope the tier first, then build the case to fund and approve it.

## Core Principle

**A business case wins on the cost of the status quo, not the cleverness of the technology.**

Decision-makers do not fund AI. They fund hours recovered, errors avoided, and risk reduced. Lead with what the current manual process costs the business every week. The automation is just the mechanism.

## What to Gather First

Before drafting, collect these inputs from the user. Ask for any that are missing:

- **The task** — what is done today, by whom, in plain English
- **Frequency** — how often (daily, weekly, monthly)
- **Time per cycle** — how long it currently takes a person
- **Who does it** — role and rough seniority (drives the loaded hourly cost)
- **Error or delay cost** — what goes wrong when it is done late or wrong, and what that costs
- **The proposed automation** — what the AI tool would do, and what stays with a human
- **The governance tier** — if known (run the FS Governance Tier Checker if not)

If the user cannot answer the cost questions, help them estimate — a defensible estimate beats a blank.

## What to Return

A single page, in this order:

1. **The problem** — current state and what it costs
2. **The proposed automation** — plain English, no jargon
3. **The numbers** — ROI as a defensible range, shown transparently
4. **Risks to the case** — what could stop the savings landing
5. **Governance considerations** — proportionate to the tier
6. **The ask** — exactly what you need to proceed

Always close with the caveat.

---

## Section 1: The Problem

State the current process and its cost in two or three sentences. Make the cost concrete.

Open with the pain, not the solution: *"Every [frequency], [role] spends [time] on [task]. That is [annual hours] a year, and when it slips, [consequence]."*

---

## Section 2: The Proposed Automation

Describe what the tool does in one short paragraph a non-technical reader understands. Be explicit about what stays with a human — this is what makes the case approvable.

State plainly: *"The tool drafts / sorts / flags. A person reviews and decides before anything happens."*

---

## Section 3: The Numbers

Show the ROI transparently so the reader can challenge any input. Give a **range, not a single figure**: a conservative case and an expected case, with the assumptions listed underneath. A defensible range survives scrutiny; a precise-looking single number invites it.

**Time-saved method:**

```
Annual hours saved   = (current minutes − new minutes) ÷ 60 × cycles per year
Annual value         = annual hours saved × loaded hourly cost
```

- Run it twice: a **conservative** case (cautious time saved, lower hourly cost) and an **expected** case. Present both, e.g. "~£11k–14k a year."
- List the **assumptions** in a short line: cycles per year, minutes saved per cycle, loaded hourly cost, and that the freed time is redirected to higher-value work.
- Use a **loaded** hourly cost (salary + on-costs), not raw salary. Be conservative and say so.
- If you do not know the salary, use a defensible band and label it an estimate.
- Add risk/error reduction qualitatively if you cannot put a number on it. Do not invent precision.

Always show the working. A decision-maker trusts a number they can see built.

---

## Section 4: Risks to the Case

Name the one or two things that could stop the savings landing, and the honest downside if it only half-works. This makes the case stronger, not weaker: it shows you have stress-tested it, and it pre-empts the challenge the budget holder was going to raise anyway.

Cover briefly, in two or three lines:

- **What could erode the saving** — the process changes, volumes fall, review takes longer than expected.
- **Adoption risk** — whether the person actually uses it or quietly reverts to the manual way.
- **The honest downside** — what it costs if it underdelivers (usually just the build time, leaving you no worse off than today).

The goal is credibility, not a risk register. Keep it short.

---

## Section 5: Governance Considerations

Keep this proportionate to the tier and free of regulatory claims you are not positioned to make.

- **Tier 1 (Productivity)** — note standard IT controls apply; no special overlay.
- **Tier 2 (Regulated input)** — note the human review step, named accountability, and audit trail. Confirm governance review is planned.
- **Tier 3 (Externally consequential)** — state that formal governance approval precedes any build, and name who needs to be in the room.

If the tier is unknown, recommend running the FS Governance Tier Checker before the business case goes forward.

---

## Section 6: The Ask

End with a specific, bounded request. Vague asks stall. Good asks get a yes.

Include:
- **What you need** — approval to build, a few hours of time, access to a system, a small budget
- **From whom** — the named owner who can say yes
- **By when** — a date that creates gentle momentum
- **What happens next** — the first concrete step once approved

---

## Worked Examples

Three cases, one per tier — note how the ROI logic stays constant while the governance and the ask change as the stakes rise.

### Example 1 — Tier 1 (Productivity): policy documents into briefing notes

> **The problem.** Each month, a team lead spends about 6 hours reading long policy and procedure updates and turning them into short briefings for a team of 12. That is ~70 hours a year, and updates sometimes get skimmed or missed entirely.
>
> **The proposed automation.** A Claude-based tool drafts a one-page plain-English briefing from each document. The team lead reviews and edits before circulating — nothing goes out unread.
>
> **The numbers.** 6 hours → about 1 hour per month. ~60 hours a year recovered. At a loaded cost of ~£60/hour (estimate), that is ~£3,600 a year, plus better coverage of updates.
>
> **Governance.** Tier 1 (Productivity): output is text a human reads and edits, with no regulated decision attached. Standard IT controls apply; no special overlay needed.
>
> **The ask.** Approval from the team lead to build it themselves over a few hours, using documents the team already has access to. First step on approval: trial it on this month's updates.

### Example 2 — Tier 2 (Regulated input): weekly margin / exposure report

> **The problem.** Every week, an operations lead spends about 4 hours pulling figures from three systems into one report. That is roughly 200 hours a year. When it runs late, downstream sign-offs slip and the team chases corrections.
>
> **The proposed automation.** A Claude-based tool pulls the figures and drafts the report in a standard format. The operations lead reviews it, corrects anything off, and signs it off — the same person stays accountable for what goes out.
>
> **The numbers.** 4 hours → about 20 minutes per week, so ~190 hours a year recovered. At a loaded cost of £70–80/hour (estimate), that is **~£13,000–15,000 a year**, before counting fewer late-report knock-ons. Assumptions: 50 working weeks, ~3.7 hours saved per week, time redirected to exception handling.
>
> **Risks to the case.** The saving assumes the three source formats stay stable; if a system changes, the tool needs a small fix. Adoption is the main risk — it only pays back if the lead actually runs it weekly. Honest downside: the two-week build, leaving us no worse off than today.
>
> **Governance.** Tier 2 (Regulated input): the output influences an operational workflow but a human reviews before sign-off. Needs a review step, named accountability and an audit trail — all in scope.
>
> **The ask.** Approval from the Head of Operations to build a first version over two weeks, plus read access to the three source systems. First step on approval: a one-week pilot on last quarter's data.

### Example 3 — Tier 3 (Externally consequential): drafting client breach notifications

> **The problem.** When a limit breach occurs, an analyst spends 2–3 hours drafting the client notification under time pressure, often out of hours. The cost is less about hours and more about the risk of an inconsistent or incorrect notification going to a counterparty.
>
> **The proposed automation.** A Claude-based tool drafts the notification from the breach record using an approved template. A senior reviewer checks and authorises every notification before it is sent — the tool never sends.
>
> **The numbers.** ~2 hours saved per breach, but the real value is consistency and reduced error on a client-facing communication. Quantify the time; describe the risk reduction qualitatively rather than inventing a figure.
>
> **Governance.** Tier 3 (Externally consequential): output drives a direct external communication to a counterparty. Formal governance approval precedes any build; needs independent review of the template, a hard human-authorisation gate, and senior visibility.
>
> **The ask.** This one is different — the first ask is not "approve the build," it is "approve scoping it." Request a governance review with risk, compliance and legal in the room before any tool is built. Do not build first.

---

## Tone and Behaviour

- Lead with cost-of-status-quo, never with the technology
- Plain English throughout — assume a non-technical reader
- Show every number's working; never present unexplained figures
- Be conservative with estimates and label them as estimates
- Never overstate ROI to win approval — a case that overpromises fails on delivery
- Keep governance proportionate and free of specific regulatory claims; point to the FS Governance Tier Checker for tiering

## Skill Invocation

**Trigger phrases:**
"Help me build the business case for this AI tool" / "How do I sell this automation internally" / "What's the ROI on automating this" / "Write me a one-pager to get this approved"

---

Built by Mercedes Perez-Capilla.
Companion skills: [FS Governance Tier Checker](../fs-governance-tier-checker/) · [Automation Opportunity Finder](../automation-opportunity-finder/).
Free to use and share with attribution. Not legal, compliance or financial advice.
