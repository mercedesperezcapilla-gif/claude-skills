# claude-skills

Free, open Claude skills for AI automation and governance. Built for highly regulated environments, useful anywhere.

> **Guidance only — not legal, compliance or regulatory advice.** These are thinking tools to help you ask better questions before the formal conversations begin. They name no specific regulation and are not a substitute for your organisation's own controls.

By [@mercedesperezcapilla-gif](https://github.com/mercedesperezcapilla-gif)

Each skill lives in `skills/<skill-name>/` and installs in the Claude app or Claude Code.

---

## Start here: find → govern → fund

Three skills for the work that happens around the build: spotting what is worth automating, working out its governance tier, and making the case to fund it. The story behind them is in [**Automate, Govern, Fund**](Automate-and-Govern-Article.md).

| Skill | What it does | Try saying |
| --- | --- | --- |
| [automation-opportunity-finder](skills/automation-opportunity-finder) | Guided discovery that finds practical automation Quick Wins in your weekly workflow. Returns prioritised opportunities, tooling recommendations (Claude app vs Claude Code), and governance signals. Built for people who don't know where to start. | "I don't know what to automate" |
| [fs-governance-tier-checker](skills/fs-governance-tier-checker) | Works out the governance tier of an AI use case (Tier 1 Productivity, Tier 2 Regulated Input, Tier 3 Externally Consequential) by what the output affects, not who uses it. Returns routing logic, governance considerations, and a pre-meeting checklist. | "What tier is my AI tool?" |
| [ai-use-case-business-case-builder](skills/ai-use-case-business-case-builder) | Turns a scoped use case into a one-page internal business case that wins buy-in: the problem and its current cost, the automation in plain English, a transparent ROI, governance sized to the tier, and a clear ask. | "Help me build the business case for this" |

---

## Course-building skills

The two skills I built while making an AI automation course with Claude Code. They outlived the course and work on any content project.

| Skill | What it does | Try saying |
| --- | --- | --- |
| [content-formatter](skills/content-formatter) | Turns a dense draft into clean, scannable, web-ready content with visual hierarchy, time boxes, success checks and troubleshooting toggles. Has a tone dial: friendly for self-paced learning, professional for regulated or exec material. | "Make this web-ready" |
| [universal-example-tracker](skills/universal-example-tracker) | Keeps one consistent character and worked example running through an entire content series (courses, docs, onboarding) so concepts build on one familiar story. Ships with a swappable default persona you change by editing one file. | "Keep the running example consistent" |

---

## Engineering skills

Skills for the work of building software, not just talking about it.

| Skill | What it does | Try saying |
| --- | --- | --- |
| [doc-sync](skills/doc-sync) | Rebuilds your status or progress doc from what's actually in the repo, and flags (rather than rewrites) anything that's gone stale in your vision or architecture docs. Keeps the writing honest: built isn't deployed, committed isn't merged. Works in any codebase. | "Sync the docs with the code" |
| [claude-code-content-validator](skills/claude-code-content-validator) | Keeps Claude Code teaching content (a course, tutorial, or internal guide) factually correct against Anthropic's live docs. Checks every command, convention, MCP package and model id against the source, flags drift and filler, and returns the safe fixes. Works on any Claude Code content. | "Validate my Claude Code course against the docs" |
| [sdlc-release-validator](skills/sdlc-release-validator) | Validates that a software change has met all required SDLC gates before or after release in a regulated environment. Checks eleven gates — change record, design, code review, developer testing, independent testing, environment consistency, UAT sign-off, bug management, go/no-go, post-release validation, and exceptions. Returns a gate-by-gate status report and a structured sign-off block ready for audit. | "Validate this release" / "Is this ready for production?" |

---

## How to install

### Claude Code (works for every skill)

Copy the skill folder into your Claude Code skills directory:

```
skills/<skill-name>/  →  ~/.claude/skills/<skill-name>/
```

For example:

```
skills/automation-opportunity-finder/  →  ~/.claude/skills/automation-opportunity-finder/
```

Then invoke it by typing `/<skill-name>` in Claude Code, or just describe your task using one of the "Try saying" phrases above.

---

## Adding more skills

Each new skill gets its own folder under `skills/` with a `SKILL.md` file.

---

*Thinking tools to help you approach AI adoption more responsibly before the formal conversations begin. Not legal, compliance or regulatory advice.*
