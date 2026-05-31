# Automate, Govern, Fund

### The three skills I built for the work that happens around the build

*By Mercedes Perez-Capilla, RepresentAI Financial Services Group*

---

In December and January, I built an entire course on AI automation with Claude Code, start to finish. There wasn't much of a playbook back then. Just plain English and a terminal. And I built it in that order: first the skills, then the materials those skills produced, then the web platform to put it all online.

The skills were specific. A **content-formatter**, so every lesson came out in the same clean structure. A **universal-example-tracker**, so one character, Riley, stayed the same person from the first lesson to the last, instead of a different example in every module. An **automation-opportunity-finder**, to spot which repetitive parts were even worth automating in the first place. The skills came first because the skills were what made the rest fast. ([The story's here](https://ai-course-web.vercel.app/story).)

Building it taught me the thing most people don't expect: the tool is almost never what stops you.

I've spent this year watching people try to adopt AI. Some found Claude and never looked back. It was the first AI experience that actually changed how they worked. Others had the tool sitting right there and still couldn't get moving. Not because the model wasn't good enough. Because of something quieter.

They didn't know what to automate. Or they sensed governance mattered but had no idea when to bring it in. Or they believed in an idea and couldn't get anyone to fund it.

I watched all three play out, often in the same team. And the projects that didn't land were rarely held back by the model. They were held back by the work *around* the build: the part nobody talks about, and the part that's actually harder than the building.

So I wrote three skills for it.

---

## The three conversations

Let me describe the three people these skills are for. You'll recognise at least one of them. You might be one of them.

The first has heard about Claude, done the training, and is genuinely curious. Then they sit down to use it, and freeze. They can't name a single thing in their week worth automating. The tool feels capable. The application feels invisible.

The second is the opposite. They find a workflow, start building, and then the question lands: *"Have you spoken to compliance about this?"* And the whole thing either stalls for good or ships without the conversation it needed.

The third one catches people out just as often. The workflow is clear. The governance is understood. And then they have to walk into a room and ask for the time, the budget, the access. And a good idea dies because nobody framed it as something a decision-maker could say yes to.

Three different people. Same root cause. So, three skills.

---

## 1. Finding what's hiding in your week

The **Automation Opportunity Finder** is a discovery tool. You describe your role, your recurring tasks, the reports you keep rewriting, the things you copy and paste every week. It hands back the best automation to start with, four more ranked by impact, and a flag on which ones need a governance conversation first.

Here's what it taught me: most people badly underestimate how much repetitive work is already buried in their week.

The first workflow it surfaced when I was testing it was a Monday-morning reconciliation summary someone had been rewriting by hand for years. The automation was small. The hard part was noticing the pattern at all. Once it had a name, it was obvious. Before that, it was just Monday.

If you're stuck, there's a fallback that almost always works: *What do you do every Monday morning? What do you do at the end of every month? What do you do before every meeting?* The recurring, time-based stuff is nearly always where to start.

And start small. The skill leans toward things you can stand up quickly in the Claude app, because the point is to *feel* one automation working before you reach for anything bigger. Sophistication can come later. Usefulness has to come first.

---

## 2. The governance conversation before the build

The **FS Governance Tier Checker** is the one I wish I'd had the first time someone asked me whether their tool needed compliance.

Because that's the question I kept hearing: *"Would this require compliance involvement?"* The instinct behind it is right. The reflex underneath it usually isn't. People assume that if a tool is internal, the governance bar is lower.

It isn't. What sets the bar is what the output affects, not who uses it.

A meeting summariser and an exception classifier can both be "internal." Only one is genuinely low risk. The Tier Checker walks you through that distinction in plain English: the suggested tier, the routing logic behind it, the governance considerations that come with it, and a checklist for the conversation with compliance, operational risk or model risk.

It's not a substitute for that conversation. It's what you bring to it.

And here's the honest part: almost every business case I've seen got noticeably stronger the moment the routing logic and the risk assumptions were made explicit *before* the conversation started. The skill defaults to the higher tier when it's unsure, because over-control is almost always cheaper than retrofit.

Governance done early makes things faster, not slower. Governance done late creates the kind of rework nobody budgets for.

---

## 3. Making the case to fund it

The **AI Use Case Business Case Builder** is for the moment after you've decided a tool is worth building, and before you walk in to ask for it.

You describe the workflow, what it costs today, and what the automation would do. It gives you back a one-page case anyone non-technical can read in two minutes: the problem and what the manual version costs, the automation in plain English with what stays human, a transparent ROI you can show your working on, governance sized to the tier, and a clear, bounded ask.

The principle is the one most technical pitches miss. A business case wins on the cost of the status quo, not the cleverness of the tech. Decision-makers don't fund AI. They fund hours recovered, errors avoided, risk reduced.

The worked examples taught me something I didn't expect. The ROI logic stays the same as the stakes rise, but the *ask* changes shape. For a low-risk productivity tool, the ask is "approve the build." For an externally consequential one, the first ask isn't to build at all. It's to approve scoping it, with the right people in the room, before anything gets built.

---

## What it looks like end to end

Here's the actual sequence, with one person running all three.

**You type:** *"I'm an operations analyst. My week is reconciliations, chasing sign-offs, a few recurring reports, and ad hoc data pulls. I don't know which bit is worth automating. What should I start with?"*

The **Automation Opportunity Finder** ranks them and comes back with one you hadn't flagged as the obvious candidate: a Monday exposure summary you rebuild by hand, about four hours, ranked above four others because it's frequent, repetitive and easy to check. It adds one flag: the output feeds a risk workflow, so check the governance tier before you build.

**You type:** *"It's an automated weekly exposure report. A human reviews it before it goes anywhere. What tier is it?"*

The **FS Governance Tier Checker** lands it at Tier 2, Regulated Input. It explains why, and hands you the considerations to raise with your risk or compliance partner, plus what to bring to that conversation.

**You type:** *"Four hours a week, my time costs roughly £55 an hour loaded, the review stays human. Build me the case."*

The **AI Use Case Business Case Builder** returns a one-page case: the cost of the status quo, the automation in plain English, a transparent ROI, governance sized to Tier 2, and a single bounded ask: approve the build.

Three short prompts. You walk into the room with the workflow chosen, the governance understood, and the case already written.

Not every case needs all three at full weight. Say the workflow is turning your own meeting notes into a tidy summary for yourself: nothing customer-facing, no regulated decision, nothing leaving your desk without you. The **Automation Opportunity Finder** still surfaces it, but the **FS Governance Tier Checker** lands it at Tier 1, Productivity, so the governance conversation is light. And the **AI Use Case Business Case Builder** shrinks the case to a line: *"saves me three hours a week, approve the build."* Same three skills, dialled right down. The point isn't ceremony. It's matching the effort to the stakes.

---

## Why these three, in this order

Together they're a sequence: identify the right workflow, understand the governance, fund it with a credible case, then build.

If the opportunity sits in low-risk territory, you move fast. If it touches significant decisions, customer outcomes, or real operational exposure, governance belongs in the design from the start, not bolted on at the end. And either way, nothing gets built unless someone agreed to pay for it.

The order matters. Most AI advice is about learning the tools, and for a lot of people that's the right place to start. If that's you, Anthropic's own [free courses](https://anthropic.skilljar.com) are excellent and go deep. My [course](https://ai-course-web.vercel.app) is a gentler foundation for business professionals: it follows one person from first idea to automation, so the pieces connect instead of arriving as scattered demos. But for those who already have the tool and aren't using it well yet, the missing pieces are upstream: knowing what to build, knowing how to govern it, knowing how to get it funded.

That's the space these skills live in.

---

## What they don't try to do

They're not legal advice, governance approvals, or substitutes for your firm's existing controls. They're thinking tools, meant to help you approach AI adoption more responsibly and more effectively before the formal conversations begin.

The frameworks will change. Expectations around AI governance are still maturing as organisations work out their own and regulations evolve. That's part of why the skills are open and free. A framework doesn't have to be perfect to be useful. It just has to help you ask better questions before you build.

---

## The wider point

The financial services AI conversation often happens at the wrong altitude. Strategy decks, panels, future-state architectures: all of it matters. But adoption usually succeeds or fails somewhere much smaller and more operational.

With the operations analyst trying to win back four hours a week.
With the risk manager unsure whether a use case belongs in governance review.
With the product lead trying to write a business case nobody can argue with.

Those are the conversations these skills were built for. If you're working through any of them in your own organisation, try the skills and tell me where they break. The interesting part of AI adoption was never the demo. It's what happens when real teams put it to work.

---

## Two more, from building the course

Here's the part I didn't plan: two of the skills I built for the course outlived it. The **content-formatter** turns any dense draft into something clean and scannable: a lesson, a memo, a deck. The **universal-example-tracker** keeps one character and one worked example running consistently through any multi-part series, and you swap the persona by editing a single file. I built them for one project and kept reaching for them. They're open and free too, in the same repo.

---

### Get the skills

- **Automation Opportunity Finder** — find your first AI Quick Win
- **FS Governance Tier Checker** — prepare for the conversation with your governance team
- **AI Use Case Business Case Builder** — turn it into a one-page case that gets funded

All three are open and free, at [github.com/mercedesperezcapilla-gif/claude-skills](https://github.com/mercedesperezcapilla-gif/claude-skills).

*Mercedes Perez-Capilla is a Product Lead for Transformation and AI Adoption in financial services. She is a Claude Certified Architect candidate, an IAPP AIGP candidate, and part of the Financial Services group at RepresentAI.*
