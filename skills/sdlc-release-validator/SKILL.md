---
name: sdlc-release-validator
description: >
  Validates that a software change has met all required SDLC gates before or after
  release in a regulated financial services environment. Checks change record linkage,
  design documentation, code review, developer testing, independent test execution,
  environment consistency, UAT sign-off, bug management, go/no-go approval,
  post-release validation, and exceptions or manual interventions. Returns a
  gate-by-gate status report and a structured sign-off block suitable for audit.
  Use before a release to check readiness, after a release to confirm completeness,
  or during a review to evidence what was done.
author: Mercedes Perez-Capilla
version: "1.1"
license: MIT
tags: [sdlc, release-management, change-management, financial-services, governance, audit]
---

# SDLC Release Validator

A validation tool for software releases in regulated environments. It works through every required gate systematically, surfaces what is missing or incomplete, and produces a structured sign-off record suitable for audit or regulatory review.

It is designed for the person responsible for release readiness — a delivery lead, BA, change manager, or risk partner — who needs to confirm that all the right things happened before or after a change went to production.

## Core Principle

**Evidence beats intention.** "We always do X" is not the same as "here is the evidence that X was done for this change." The validator asks for evidence at every gate, not assurances.

## How to Use

Give the skill a description of the change — a Jira link, a summary of what was released, or a paste of the ticket. It will work through the gates, ask for anything missing, and return the full report.

If the user says "validate this release" or "run the SDLC check" with no further context, ask for:
1. Change reference (ticket ID or description)
2. Release date and environment (UAT / Production)
3. System or component affected

**Also ask:** What type of change is this?
- **Minor** — low risk, small scope, well-understood (some gates may be waivable)
- **Standard** — planned release following full SDLC process (all gates apply)
- **Significant** — affects regulatory reporting, risk calculations, client-facing outputs, or external messaging (all gates mandatory, no waivers without documented approval)
- **Emergency** — hotfix under time pressure (document which gates were skipped and why)

Change type determines which gates are mandatory vs. waivable. State the type at the top of the report.

---

## The Thirteen Gates

Work through these in order. For each gate, determine the status from the information provided — only ask a follow-up question if the gate cannot be assessed from what has been given.

---

### Gate 1 — Change Record

**What to check:**
- Is there a linked change ticket (e.g. Jira, ServiceNow)?
- Is the objective of the change clearly stated?
- Is the scope (what changed, what did not) documented?

**Pass:** Ticket exists, objective is clear, scope is defined.
**Partial:** Ticket exists but objective or scope is vague.
**Fail:** No ticket, or objective cannot be determined.

---

### Gate 2 — Design Agreement

**What to check:**
- Was the design agreed before development started?
- Is the agreed design documented (in the ticket, a design doc, a decision record)?
- Did the right people sign off on the design (BA, tech lead, risk, or whoever is required by the team's process)?

**Pass:** Design documented and agreed pre-development.
**Partial:** Design exists but agreement is informal or undocumented.
**Fail:** No design documentation, or development started before design was agreed.

---

### Gate 3 — Code Review

**What to check:**
- Was the code reviewed before it was merged?
- Is the review evidenced (pull request, peer review comment, approval in ticket)?
- Did the reviewer note any significant findings, and were they addressed?

**Pass:** Code review evidenced with approval recorded.
**Partial:** Review happened but is not formally evidenced.
**Fail:** No code review, or code was merged without approval.

---

### Gate 4 — Developer Testing

**What to check:**
- Did the developer who built the change test it?
- Is testing evidence recorded (test results, screenshots, log output, test data used)?
- Were all environments covered in the developer's testing scope?

**Pass:** Developer testing evidenced with results recorded.
**Partial:** Testing done but evidence is incomplete or informal.
**Fail:** No developer testing evidence.

---

### Gate 5 — Independent Testing

**What to check:**
- Were test cases executed by someone other than the developer who built the change?
- Are the test cases documented (what was tested, expected result, actual result)?
- Did the independent tester cover the key scenarios, not just the happy path?

**Pass:** Independent test execution evidenced with test cases and results.
**Partial:** Independent testing done but test cases are not documented, or coverage is narrow.
**Fail:** Only the developer tested the change — no independent execution.

> This gate exists because the developer is the least likely person to find problems with their own code. Independent testing is the control, not a formality.

---

### Gate 6 — Environment Consistency

**What to check:**
- Was the same package or build deployed across all environments (dev, UAT, production)?
- If any environment received a different version, is it documented and explained?

**Pass:** Same package confirmed across all environments.
**Partial:** Consistency not fully confirmed, or one environment differed with a documented reason.
**Fail:** Different versions in different environments with no explanation.

---

### Gate 7 — UAT Sign-Off

**What to check:**
- Did business or operations users test the change in UAT?
- Is sign-off formally recorded — by whom, on what date, against what criteria?
- If UAT was waived, is the waiver documented and approved by the right person?

**Pass:** UAT sign-off recorded with named approver and date.
**Partial:** UAT done but sign-off is informal, undated, or the approver is unclear.
**Fail:** No UAT, and no documented waiver.

---

### Gate 8 — Bug Management

**What to check:**
- Were any bugs raised during testing?
- For each bug: was it resolved before release, formally accepted as a known issue, or tolerated with a documented rationale?
- Is there a record of the decision for each bug — not just its status?

**Pass:** All bugs have a documented outcome (fixed / accepted / tolerated with rationale).
**Partial:** Some bugs are unresolved or lack a documented decision.
**Fail:** Bugs exist with no recorded outcome or decision.

> An accepted or tolerated bug is not a failed gate — but an undocumented one is.

---

### Gate 9 — Go/No-Go Decision

**What to check:**
- Was there a go/no-go meeting or decision before the release?
- Are the participants, decision, and any conditions recorded?
- If the go/no-go was async (email, chat), is that record preserved?

**Pass:** Go/no-go decision recorded with participants and outcome.
**Partial:** Decision was made but not formally recorded, or participants are unclear.
**Fail:** No go/no-go decision documented.

---

### Gate 10 — Post-Release Validation

**What to check:**
- Was validation performed after the release went live?
- What was checked, and by whom?
- Were any issues identified during post-release validation, and how were they handled?

**Pass:** Post-release validation evidenced with scope and outcome recorded.
**Partial:** Some validation done but scope is unclear or not recorded.
**Fail:** No post-release validation performed or documented.

---

### Gate 11 — Exceptions and Manual Interventions

**What to check:**
- Were any manual interventions made during or after the release window (e.g. config changes, data fixes, process overrides)?
- Were any out-of-hours decisions taken that were not part of the original plan?
- Is each exception documented, attributed to a named person, and approved?
- **Integration and message flow decisions:** if any message feeds, API connections, or system integrations were enabled, disabled, or modified during the release window — is there a record of who made the call, what triggered it, and who approved it? Decisions made under time pressure (e.g. re-enabling a feed the morning after a release) are especially likely to go undocumented — flag these explicitly.

**Pass:** No exceptions, or all exceptions documented, attributed, and approved.
**Partial:** Exceptions occurred but documentation is incomplete.
**Fail:** Exceptions occurred with no record or approval.
**N/A:** Release was clean with no interventions required.

---

### Gate 12 — Rollback Plan

**What to check:**
- Was a rollback/backout procedure defined before the release went live?
- Is it documented — steps, owner, estimated time to execute?
- Who has authority to invoke it, and how is that decision made?
- If the rollback was invoked, is that documented separately with the reason?

**Pass:** Rollback plan documented with named owner and steps, defined before release.
**Partial:** A rollback approach exists but is informal, undocumented, or was defined after the release started.
**Fail:** No rollback plan. "We'd figure it out" is not a plan.
**N/A:** Change is fully reversible by design with no specific procedure needed (document why).

> Auditors and regulators will always ask: "What was your backout plan?" If it isn't documented before the release, it doesn't count.

---

### Gate 13 — Impact Communication

**What to check:**
- Were all upstream and downstream teams notified before the release window?
- If the change affects client-facing outputs, counterparty data, or regulatory reporting — was the relevant risk or compliance team notified (not just included in UAT)?
- Is there a record of who was told, when, and through what channel?

**Pass:** All impacted parties notified before release, with a record.
**Partial:** Some teams notified but not all, or notification happened after the release started.
**Fail:** Change went to production without affected teams being informed.
**N/A:** Change is fully internal with no downstream impact (document why).

---

## What to Return

Return two sections in this order.

---

### Section 1: Gate-by-Gate Status Report

Use this format for each gate:

```
## Gate [N] — [Name]
Status: ✅ Pass | ⚠️ Partial | ❌ Fail | ➖ N/A

Evidence: [What was provided or confirmed]
Gap (if any): [What is missing or incomplete]
Action required: [What needs to happen to close the gap — only if Partial or Fail]
```

Follow the thirteen gates in order. Do not skip a gate — if there is no information, mark it as ❌ Fail and state what evidence is needed.

After the thirteen gates, add a summary:

```
## Summary
Change type:      Minor | Standard | Significant | Emergency
Gates passed:     X / 13
Gates partial:    X
Gates failed:     X
Gates N/A:        X

Release readiness: READY | CONDITIONAL | NOT READY

[One or two sentences on the overall picture — what is solid, what needs to close before sign-off.]
```

**Readiness thresholds:**
- **READY** — all gates Pass or N/A
- **CONDITIONAL** — one or more gates Partial, with clear actions identified
- **NOT READY** — one or more gates Fail, or a Partial with no clear path to resolution

---

### Section 2: Structured Sign-Off Block

Produce a sign-off record suitable for attachment to the change ticket or audit file:

```
## Release Sign-Off Record

Change reference:     [ticket ID / description]
System / component:   [what was released]
Release date:         [date]
Environment:          [UAT / Production / other]

Validated by:         [name of person running this check]
Validation date:      [today's date]
Validation method:    SDLC Release Validator (Claude skill)

Gate summary:
  ✅ Passed:   [list gate names]
  ⚠️ Partial:  [list gate names — with agreed actions and owners]
  ❌ Failed:   [list gate names]
  ➖ N/A:      [list gate names]

Overall status:       READY / CONDITIONAL / NOT READY

Notes:
[Any material context — waivers, known issues accepted, conditions for sign-off]

Sign-off (for human completion):
Approved by: ___________________   Role: ___________________   Date: ___________
```

The sign-off block is a record of what was validated and by what method. The final human signature line is intentional — in a regulated environment, automated validation supports human sign-off; it does not replace it.

---

## Tone and Behaviour

- Be specific about what evidence is present and what is absent — never vague
- Do not infer a pass from absence of evidence of a problem; require positive evidence
- If something was done informally, flag it as Partial, not Pass — informal is not the same as undocumented
- If the user pushes back on a Fail or Partial, explain the reason rather than softening the grade
- Keep the report factual and audit-ready — avoid hedging language

---

## Skill Invocation

**Trigger phrases:**
"Validate this release" / "Run the SDLC check" / "Has this change met all the gates?" / "Can you check our release evidence?" / "Is this ready to go to production?" / "Help me evidence this change for audit"

---

Built by Mercedes Perez-Capilla.
Free to use and share with attribution. Not legal, compliance or regulatory advice.
Governance frameworks vary by firm — validate the gates against your own change management policy before use.
