---
name: sdlc-release-validator
description: >
  Validates that a software change has met all required SDLC gates before or after
  release in a regulated financial services environment. Checks 13 gates — change record,
  design agreement, code review, developer testing, independent testing, environment
  consistency, UAT sign-off, bug management, go/no-go, post-release validation, exceptions
  and manual interventions, rollback plan, and impact communication. Returns a gate-by-gate
  status report and a structured sign-off block ready for audit. Use before a release to
  check readiness, after to confirm completeness, or during a review to evidence what was done.
author: Mercedes Perez-Capilla
version: "1.2"
license: MIT
tags: [sdlc, release-management, change-management, financial-services, governance, audit]
---

# SDLC Release Validator

Validates software releases against 13 SDLC gates and produces a sign-off record suitable for audit. Designed for delivery leads, BAs, change managers, and risk partners who need to confirm that the right things happened before or after a change went to production.

**Core principle: evidence beats intention.** "We always do X" is not the same as "here is the evidence that X was done for this change." Require evidence at every gate — not assurances.

---

## Step 1 — Classify the change

Ask if not already clear:

| Type | When | Gates |
|---|---|---|
| **Minor** | Small, low-risk, well-understood | Some gates waivable |
| **Standard** | Planned release, full SDLC | All gates apply |
| **Significant** | Affects regulatory reporting, risk calculations, client-facing outputs, or external messaging | All gates mandatory — no waivers without documented approval |
| **Emergency** | Hotfix under time pressure | Run all gates; document which were skipped and why |

State the change type at the top of the report.

---

## Step 2 — Run the 13 gates

**Status definitions (apply consistently across all gates):**
- ✅ **Pass** — positive evidence present and sufficient
- ⚠️ **Partial** — something exists but informal, incomplete, or undated
- ❌ **Fail** — no evidence; cannot confirm this happened
- ➖ **N/A** — genuinely not applicable; state why

Informal is Partial, not Pass. Do not infer a pass from silence — require positive evidence.

---

**Gate 1 — Change Record**
Is there a ticket with a clear objective and defined scope (what changed, what did not)?

**Gate 2 — Design Agreement**
Was the design agreed and documented before development started — in the ticket, a linked doc, or a sign-off from a BA or tech lead?

**Gate 3 — Code Review**
Is the code review evidenced — a PR approval, peer review comment, or formal sign-off? A review that happened but left no record is Partial.

**Gate 4 — Developer Testing**
Did the developer test the change, and is there evidence — test results, screenshots, log output, or a comment confirming what was tested?

**Gate 5 — Independent Testing**
Were test cases executed by someone other than the developer, with documented results covering more than the happy path?

> The developer is the least likely person to find problems with their own code. Independent testing is the control, not a formality.

**Gate 6 — Environment Consistency**
Was the same package or build deployed across all environments? Any deviation needs a documented reason.

**Gate 7 — UAT Sign-Off**
Is there a named business or operations approver, with a date? A waiver is acceptable if documented and approved by the right person.

**Gate 8 — Bug Management**
For every bug raised during testing: is there a documented outcome — fixed, formally accepted, or tolerated with a rationale? An unresolved bug with no comment is a Fail.

> An accepted or tolerated bug is not a failed gate — an undocumented one is.

**Gate 9 — Go/No-Go Decision**
Is there a recorded go/no-go decision with participants and outcome? An async decision (email, chat summary) counts if it names participants and records the call.

**Gate 10 — Post-Release Validation**
Was validation performed after go-live — what was checked, by whom, and what was the outcome?

**Gate 11 — Exceptions and Manual Interventions**
Were any manual interventions made during or after the release window — config changes, data fixes, process overrides? Is each one documented, attributed to a named person, and approved?

> Pay particular attention to integration and message flow decisions: if any message feeds, API connections, or system integrations were enabled, disabled, or re-enabled during the release window, these are especially likely to go undocumented when made under time pressure. Flag explicitly.

**Gate 12 — Rollback Plan**
Was a rollback procedure documented before the release — with steps, a named owner, and authority to invoke it? Defined after the release started is Partial. "We'd figure it out" is a Fail.

> Auditors will always ask: "What was your backout plan?" If it isn't documented before the release, it doesn't count.

**Gate 13 — Impact Communication**
Were all upstream and downstream teams notified before the release window, with a record of who was told and when? For changes affecting regulatory reporting or external data flows, risk or compliance notification is a separate requirement from UAT.

---

## Step 3 — Return the report

### Gate-by-gate status

For each gate: status, what evidence was found, and (if Partial or Fail) the gap and the action needed to close it.

Then summarise:

```
Change type:       [Minor / Standard / Significant / Emergency]
Gates passed:      X / 13
Gates partial:     X  →  [names + agreed actions]
Gates failed:      X  →  [names]
Gates N/A:         X  →  [names]

Release readiness: READY | CONDITIONAL | NOT READY
```

- **READY** — all Pass or N/A
- **CONDITIONAL** — one or more Partial with clear actions identified
- **NOT READY** — one or more Fail

### Sign-off block

```
Release Sign-Off Record
────────────────────────────────────────
Change:           [ticket ID / description]
System:           [component released]
Release date:     [date]
Environment:      [UAT / Production]

Validated by:     [name]
Validation date:  [today]

Gates passed:     [list]
Gates partial:    [list + actions]
Gates failed:     [list]

Overall status:   READY / CONDITIONAL / NOT READY

Notes:            [waivers, known issues, conditions for sign-off]

Approved by: _______________  Role: _______________  Date: ________
```

The human signature line is intentional — automated validation supports sign-off in a regulated environment; it does not replace it.

---

## Behaviour

- If the user pushes back on a Fail or Partial, explain the reasoning — do not soften the grade
- Keep the report factual and audit-ready; avoid hedging
- If information is missing to assess a gate, mark it Fail and state what evidence is needed

---

Built by Mercedes Perez-Capilla.
Free to use and share with attribution. Not legal, compliance or regulatory advice.
Validate the gates against your own change management policy before use.
