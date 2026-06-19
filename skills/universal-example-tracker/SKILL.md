---
name: universal-example-tracker
description: Keeps ONE consistent character and worked example running through an entire content series — courses, documentation, onboarding flows, or any multi-part lesson sequence — so concepts build on one familiar story instead of a new scenario each time. Ships with a default persona (Riley Harper's Weekly Margin Report) that is fully swappable from a single source of truth. Use when creating or reviewing multi-part content to keep the running example, persona, and story progression consistent.
author: Mercedes Perez-Capilla
version: 2.0
license: MIT
tags: [course-design, narrative-consistency, instructional-design, examples]
---

# Universal Example Tracker

## Overview
This skill keeps a single, concrete character and example running through a learner's entire journey, so concepts build on one familiar story instead of a new scenario in every lesson. Students follow ONE person's complete automation journey from first idea to shared, production-ready toolkit.

The default character is **Riley Harper**. She is defined once, here. Every lesson references this profile rather than inventing its own example, and that single source of truth is the whole point of the skill.

### Quick swap (the persona is not fixed to finance)

Riley is just the shipped default. To use this skill for any other domain, edit only the Character Profile and Task sections below, and every lesson inherits the change. For example:

> **Maya Lawson**, Head of Customer Support at a SaaS company, who automates her **weekly support-ticket trends report** (about 3 hours every Friday). Same arc: identify it, build it, add intelligence, schedule it with a review gate, secure and share it.

Drop Maya (or your own persona) into the two sections below and the whole series re-points to her. Nothing else needs to change.

## Why Universal Examples Matter

### The problem without one
- **Lesson 1.1:** "Let's say you want to automate a report..."
- **Lesson 1.2:** "Imagine you have a data validation task..."
- **Lesson 1.3:** "Consider a client update workflow..."
- **Result:** cognitive overload — the learner can't see how the pieces connect.

### The solution with a universal example
- **Lesson 1.1:** Riley identifies her weekly margin report (4 hours every Monday).
- **Lesson 1.2:** Riley builds a skill for it.
- **Lesson 1.3:** Riley plans and organises the workflow.
- **Lesson 1.4:** Riley sets up her project files and definitions.
- **Lesson 1.5:** Riley tests it and calculates the ROI.
- **Module 2:** Riley adds intelligence with an agent.
- **Module 3:** Riley makes it run on a schedule, with a review gate.
- **Module 4:** Riley secures it, packages it, and shares it with her team.
- **Result:** one clear narrative arc — easy to follow, easy to remember.

## The Universal Example: Riley's Story

### Character Profile
- **Name:** Riley Harper
- **Role:** Operations Director, mid-sized financial services firm
- **Domain:** derivatives clearing and margin operations
- **Experience:** 15 years in operations; leads a team of 12
- **Coding background:** none before the course — she learns by building
- **Location:** London
- **Reports to / works with:** Marcus Webb (Head of Risk Operations), James Okafor (Project Manager), Clara Singh (Compliance)

**Why Riley works as the running example**
- A senior, credible operator — not a beginner who needs hand-holding.
- A clear, measurable problem with a hard accuracy bar (margin numbers don't forgive errors).
- A regulated context, so governance, audit trails and human review are part of the story, not an afterthought.
- Room to grow in complexity across four modules.
- A genuine role model: diligent, calm under a recurring deadline, careful about controls, and someone who brings her team along rather than hoarding the win.

### The Task: Weekly Margin Report

**Official name:** "Weekly Margin & Exposure Summary"

**Current manual process — about 4 hours every Monday morning:**

1. **Data gathering (~90 min)**
   - Pull Initial Margin (IM) and Variation Margin (VM) positions per counterparty from the margin system.
   - Export net exposure figures.
   - Pull the week's margin calls.

2. **Reconciliation & calculation (~90 min)**
   - Reconcile internal figures against clearing and custodian data.
   - Calculate net exposure per counterparty.
   - Categorise each margin call: **Open / Disputed / Settled / Failed**.
   - Flag positions by risk status: **Watch / Restricted / Breached**.

3. **Report creation (~45 min)**
   - Build the summary tables.
   - Highlight disputed and failed calls, and any breaches.
   - Write plain-English commentary for the Head of Risk Operations.

4. **Distribution (~15 min)**
   - Send to Marcus Webb (Head of Risk Operations), cc Clara Singh (Compliance).
   - File the report for audit.

**Pain points**
- It eats the first half of every Monday.
- It's the same process every single week.
- The reconciliation and categorisation are repetitive but unforgiving — one copy-paste slip and the numbers are wrong.
- It crowds out the judgement work: the disputed calls and near-breaches that actually need an experienced operator's attention.

**Riley's take (the role-model framing):**
> "Four hours every Monday on a report that has to be exactly right — margin numbers don't forgive mistakes. I'd rather spend that time on the calls that genuinely need judgement, and trust a consistent, reviewed process for the rest. Automating it isn't about doing less. It's about putting my attention where it counts."

### The Automation Solution

**After automation — about 20 minutes every Monday:**

1. **Automated (0 minutes of Riley's time):**
   - A scheduled run gathers IM/VM and exposure data via MCP.
   - An agent reconciles the figures and flags exceptions (disputed calls, failed calls, near-breaches).
   - A formatted draft report is generated.

2. **Riley's work (~20 minutes):**
   - Reviews the draft and the flagged exceptions.
   - Adds judgement and commentary on the items that need it.
   - Approves and sends — **she stays in the loop on every send.**

The human review gate is deliberate and stays in the story: in a regulated environment, the report goes out because Riley signed it off, not because a script decided it was fine.

### Results & ROI

- **Time:** ~4 hours → ~20 minutes every Monday
- **Frequency:** weekly (52 times a year)
- **Annual time saved:** ~190 hours
- **Implied value:** ~£13,875 a year
- **Quality:** more consistent, fewer manual errors, a clean audit trail
- **Strategic value:** Riley redirects the reclaimed time to the disputes and risk calls that need an experienced operator — and to coaching her team to build their own automations.

> Headline for lessons: **4 hours → 20 minutes → ~£13,875/year**, with a human still signing off every report.

### How Riley Progresses Through the Course

**Module 1: Foundation**
- **L1.1:** Riley identifies the weekly margin report as her Quick Win.
- **L1.2:** Riley creates a `weekly-margin-report` skill.
- **L1.3:** Riley plans and organises the workflow with the planning command.
- **L1.4:** Riley sets up her project files and margin definitions.
- **L1.5:** Riley tests with last week's data and calculates the ROI.

**Module 2: Intelligence**
- **L2.1:** Riley learns where an agent genuinely helps — exception analysis.
- **L2.2:** Riley creates a `margin-exception-analyzer` agent.
- **L2.3:** Riley's report skill now calls the exception agent.
- **L2.4:** Riley adds a CLAUDE.md with margin definitions (IM/VM, call and risk statuses).
- **L2.5:** Riley combines report generation and exception analysis into one workflow.

**Module 3: Automation**
- **L3.1:** Riley schedules a Monday-morning run — with a review gate, not blind auto-send.
- **L3.2:** Riley adds a file-watching hook for data drops.
- **L3.3:** Riley connects to the source system via MCP, removing manual exports.
- **L3.4:** Riley's reviewed pipeline runs end to end.
- **L3.5:** Riley reviews and approves each Monday in about 20 minutes.

**Module 4: Production (Secure)**
- **L4.1:** Riley packages her work as a `margin-reporting-toolkit`.
- **L4.2:** The toolkit bundles the skill, agent, hooks, and a README.
- **L4.3:** Riley runs a security review before sharing anything.
- **L4.4:** Riley shares it with her team — and documents where a human must stay in the loop.
- **L4.5:** Riley writes up the ROI and the judgement calls automation should never own.

## Parallel Examples for Cross-Industry Learning

Riley is the PRIMARY example. To show the pattern travels, offer short parallel paths in callouts or sidebars — each a capable professional, none tied to a named real-world employer:

### Healthcare: Dr. Sarah Patel
- **Role:** Hospital Operations Director
- **Task:** daily patient census and bed-utilisation report
- **Before:** ~2 hours every morning → **After:** ~5 minutes
- **Same arc as Riley**, with patient data, run daily instead of weekly, and the same insistence on human review of anything clinical.

### Education: Tom Reyes
- **Role:** Head of Department, secondary school
- **Task:** weekly cover-lesson and resource pack
- **Before:** ~3 hours every Friday → **After:** ~25 minutes
- **Same arc as Riley**, applied to teaching materials, with a teacher reviewing every pack before it reaches a classroom.

### How to show parallel examples
```markdown
## Main walkthrough: Riley's margin report
[Detailed step-by-step using Riley]

---

### How this looks in other fields
**Healthcare — Dr. Patel:** same process, for a daily patient census report.
**Education — Tom:** same process, for a weekly cover-lesson pack.

**The pattern:** find repetitive, reviewable work; automate the repetition; keep the human on the judgement and the final sign-off.
```

## Consistency Checklist (use when reviewing lessons)
- Is the running character **Riley Harper** — same role, same firm, same task — in every lesson?
- Is the task always the **weekly margin report** (not a different example per module)?
- Are the headline numbers consistent: **4 hours → 20 minutes → ~£13,875/year**?
- Is a **human review/sign-off** still present wherever something is sent or actioned?
- Are real employer names absent? (Use "a mid-sized financial services firm", never a specific bank.)
- Do parallel examples stay in callouts, so Riley remains the spine of the story?

## Skill Invocation
**Trigger phrases:** "keep the example consistent", "make sure it's Riley not a new character", "check the running example across lessons", "is the story consistent", "align the lessons to one persona".

**To swap the persona:** change only this file's Character Profile and Task sections. Every lesson references this profile, so one edit updates the whole course.

---

*Built by Mercedes Perez-Capilla. Free to use and share with attribution. Not legal, compliance or regulatory advice.*
