---
name: content-formatter
description: Transforms dense lesson content into beautiful, web-ready, student-friendly format suitable for Notion, slides, or course platforms. Makes content scannable, visual, and easy to understand. Use when converting lesson content for student delivery.
author: Mercedes Perez-Capilla
version: 1.0
license: MIT
published_via: RepresentAI
---

# Content Formatter for Claude Code Course

## Overview
This skill takes dense, text-heavy lesson content and transforms it into beautiful, scannable, student-friendly format that works perfectly in Notion, Google Slides, or any modern course platform.

## When to Use This Skill
- After lesson-generator creates content
- Lesson content is too dense
- Need web/slide-ready format
- Want student-friendly layout
- Converting for Notion/platform delivery
- Making content scannable and engaging

## Tone Dial (set this first)

Before formatting, pick a tone. The default is **Friendly**, but for regulated, executive, or client-facing material switch to **Professional** so the output reads as sober, not breezy.

| Tone | Use for | Emojis | Voice | Celebration blocks |
|---|---|---|---|---|
| **Friendly** (default) | self-paced courses, onboarding, internal enablement | full emoji key | "You've got this!", "Let's do this together" | yes |
| **Professional** | financial services, exec decks, client/board material, compliance-adjacent docs | none, or a single section marker at most | calm and direct: "Here's what to do", "Confirm it worked" | no |

In **Professional** tone: keep the structure (visual hierarchy, time boxes, success checks, troubleshooting), drop the emoji key and the "🎉 You Did It!" celebration, and replace conversational encouragement with plain, confident instruction. Everything else in this skill still applies.

If the user does not specify a tone, ask once which they want, then proceed.

## Core Transformation Principles

### Visual Hierarchy
Use clear structure with emojis for instant recognition:
- 📘 Lesson titles (h1)
- 🎯 Goals/Objectives (h2)
- ⏱️ Time estimates
- 📋 Steps/Instructions
- ✅ Success criteria
- ⚠️ Troubleshooting
- 💡 Tips/Pro tips
- 🎉 Wins/Celebrations
- 📚 Resources
- 💼 Examples
- 🔧 Tools

### Break Up Walls of Text
- Maximum 3-4 sentences per paragraph
- Use bullet points for lists
- Numbered steps for sequences
- Tables for comparisons
- Code blocks for commands
- Callout boxes for important info

### Student-First Language
**Change technical language:**
- "Execute the following command" → "Type this:"
- "Verify successful completion" → "Check it worked:"
- "In the event of an error" → "If something goes wrong:"
- "Prerequisites" → "Before you start, you'll need:"

**Use conversational tone:**
- "You've got this!"
- "Let's do this together"
- "Here's what's happening..."
- "See how that works?"

### Progressive Disclosure
Use expandable sections for optional content:
````markdown
<details>
<summary>💡 Not sure how to [X]? Click here</summary>

[Additional helpful information]

</details>
````

### Time Boxes Everywhere
Every section needs clear time estimate:
````markdown
## 📋 Step 3: Test Your Skill
⏱️ **Time:** 10 minutes
````

### Success Checkpoints
After EVERY step, tell them how to verify:
````markdown
✅ **You'll know this worked when:**
- Criterion 1 (specific and testable)
- Criterion 2
- Criterion 3
````

## Standard Lesson Page Structure
````markdown
# 📘 Lesson 1.X: [Title]

> 🎯 **What You'll Learn:** [One sentence]
> ⏱️ **Time Required:** X minutes  
> 📦 **What You'll Build:** [Specific deliverable]

---

## 🎬 Watch First (10 min)

[Video embed placeholder]

**Key Points:**
- Point 1
- Point 2
- Point 3

**Next:** [Preview of exercise]

---

## 🎯 Exercise: [Action-Oriented Title]

⏱️ **Total Time:** XX minutes

### What You'll Build
[One clear sentence with emoji icon]

### Before You Start

**You'll need:**
- [ ] Requirement 1
- [ ] Requirement 2
- [ ] Requirement 3

**Example outputs:**
[Show what success looks like]

---

## 📋 Step 1: [Action Verb + Task]

⏱️ **Time:** X minutes

**What you're doing:**
[2-3 sentence context]

**Instructions:**
1. [Specific action]
2. [Specific action]
3. [Specific action]

**Command to run:**
```bash
[command here]
```

**What this does:**
[Plain English explanation]

> 💡 **Pro Tip:** [Helpful insight]

✅ **Success Check:**
- [ ] Verification 1
- [ ] Verification 2

---

## 📋 Step 2: [Action Verb + Task]

[Continue same pattern...]

---

## ✅ Overall Success Criteria

By the end of this exercise, you should have:
- [ ] Deliverable 1 (specific)
- [ ] Deliverable 2 (specific)
- [ ] Deliverable 3 (specific)

**Quick test:**
[Simple way to verify everything works]

---

## ⚠️ Troubleshooting

<details>
<summary>Issue 1: [Specific Problem]</summary>

**Symptom:** What you'll see/experience

**Cause:** Why this happens

**Fix:**
1. Step to solve
2. Step to solve
3. Step to solve

**Prevention:** How to avoid this

</details>

<details>
<summary>Issue 2: [Specific Problem]</summary>

[Same format...]

</details>

<details>
<summary>Issue 3: [Specific Problem]</summary>

[Same format...]

</details>

---

## 🎉 You Did It!

You just [specific accomplishment]!

**Why this matters:**
[Business impact in 2 sentences]

**Time saved:**
[If applicable: X hours/week or other metric]

**Next up:**
Lesson X.Y: [Title] - [One sentence teaser]

---

## 💼 How This Works Across Industries

### Financial Services
[Name] used this same approach for [specific task]. Result: [outcome]

### Healthcare  
[Name] used this same approach for [specific task]. Result: [outcome]

### Sales/Operations
[Name] used this same approach for [specific task]. Result: [outcome]

**The pattern:**
[Universal principle that applies everywhere]

---

## 📚 Resources & Help

### Need Help?
- 💬 **Community:** [your channel / forum link]
- 🕐 **Office Hours:** [day and time]
- 📧 **Email:** [your support email]

### Templates
- [Template name with description](link)
- [Template name with description](link)

### Documentation
- [Doc name with description](link)
- [Doc name with description](link)

### Video Timestamp Guide
- [0:23] - [Topic with timestamp for quick reference]
- [1:45] - [Topic]
- [3:12] - [Topic]

---

## 📝 Notes for Notion Setup

**Page properties to add:**
- Status: Not Started | In Progress | Complete
- Time: [X] minutes
- Week: Week [X]
- Deliverable: [What they build]

**Use Notion features:**
- **Toggle blocks** for troubleshooting
- **Callout blocks** for tips/warnings  
- **Code blocks** with language syntax
- **Columns** for side-by-side comparisons
- **Database views** for resources
````

## Formatting Patterns

### Code Blocks
Always include language identifier and explanation:
````markdown
**Command:**
```bash
mkdir -p .claude/skills/my-skill
```

**What it does:**
Creates a new folder where Claude looks for skills

**Why this matters:**
Claude automatically loads skills from this location
````

### Callout Boxes
````markdown
> 💡 **Pro Tip:** You can check your skill loaded by typing `/skills`

> ⚠️ **Warning:** Don't use tabs in YAML files, only spaces

> 🎉 **Celebration:** Your first skill is live! This is a big moment.

> ⚙️ **Technical Note:** [For those who want deeper understanding]
````

### Comparison Tables
````markdown
| When to Use | Skill | Agent | Both |
|-------------|-------|-------|------|
| Repeatable task | ✅ | | |
| Need isolation | | ✅ | |
| Complex workflow | | | ✅ |
| Fresh context needed | | ✅ | |
````

### Decision Trees
````markdown
**Not sure which to use?**

Start here: Is this task done weekly or more?
├─ YES → Is it always the same steps?
│  ├─ YES → Use a SKILL ✅
│  └─ NO → Use SKILL + AGENT
└─ NO → Just ask Claude directly
````

### Before/After Comparisons
````markdown
## The Transformation

**Before (Manual Process):**
1. Step that takes forever
2. Step that's error-prone
3. Step that's boring

⏱️ **Time:** 5 hours

**After (Automated):**
1. Run skill
2. Review output
3. Done!

⏱️ **Time:** 10 minutes

💰 **Savings:** 4 hours 50 minutes per week = 250 hours/year
````

## Quality Checklist

Before delivering formatted content, verify:

**Visual:**
- [ ] Clear h1/h2/h3 hierarchy
- [ ] Emojis used consistently  
- [ ] Visual separators (---) between sections
- [ ] No walls of text (3-4 sentence max)
- [ ] Code blocks have language tags

**Scannability:**
- [ ] Can understand page in 10-second scan
- [ ] Main sections jump out
- [ ] Steps are clearly numbered
- [ ] Success criteria highly visible

**Student Experience:**
- [ ] Conversational tone throughout
- [ ] Action verbs in all headers
- [ ] Specific, not vague instructions
- [ ] Encouraging language
- [ ] Celebrates progress

**Completeness:**
- [ ] Time estimate on every section
- [ ] Success criteria after every step
- [ ] Troubleshooting expanded with details
- [ ] Next steps are clear
- [ ] Resources linked

**Web-Ready:**
- [ ] Works in Notion
- [ ] Works in slides (can extract)
- [ ] Proper markdown syntax
- [ ] All links functional
- [ ] Mobile-friendly (short lines)

## Special Formatting for Different Platforms

### For Notion:
- Use toggle blocks for optional content
- Use callout blocks for tips/warnings
- Use synced blocks for repeated content
- Add page properties (Status, Time, Week)
- Use database for resources

### For Google Slides:
- One concept per slide
- Minimal text (5-7 bullets max)
- Large fonts (24pt minimum)
- High contrast
- Lots of whitespace

### For Course Platforms (Teachable, Thinkific):
- Use platform's native callout boxes
- Embed videos at top
- Use accordion/collapse for troubleshooting
- Add progress indicators
- Include downloadable PDFs of key content

## Integration with Other Skills

**Works with:**
- **universal-example-tracker:** Ensures examples stay consistent while formatting (companion skill in this repo)

*Note: `lesson-generator` and `course-material-creator` below are illustrative of an upstream content pipeline; they are not published skills in this repo. This formatter works on any draft you give it, from any source.*

- **lesson-generator (illustrative):** Takes its output and beautifies it
- **course-material-creator (illustrative):** Follows its quality standards

**Workflow:**
1. lesson-generator creates content (dense)
2. universal-example-tracker ensures Riley flows through
3. content-formatter makes it beautiful (this skill)
4. Result: Publication-ready content

## Examples

### Input (dense, text-heavy)

> To create a skill you must first make a directory in the correct location where the tool looks for skills, then add a definition file containing the required metadata fields, and finally verify that it loaded successfully before attempting to use it in a session.

### Output (formatted, student-friendly)

```markdown
## 📋 Step 1: Create Your Skill Folder
⏱️ **Time:** 2 minutes

**Type this:**
\`\`\`bash
mkdir -p .claude/skills/my-skill
\`\`\`

**What it does:** Creates the folder where Claude looks for your skills.

✅ **You'll know it worked when:**
- [ ] The folder `.claude/skills/my-skill` exists
- [ ] Typing `/skills` lists your new skill
```

**The transformation:** one dense sentence becomes a timed, scannable step with a copy-paste command and a success check — the same content, made doable.