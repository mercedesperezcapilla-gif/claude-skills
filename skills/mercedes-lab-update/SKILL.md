---
name: mercedes-lab-update
description: >
  Keeps Claude Code teaching content factually correct against Anthropic's live
  documentation. Claude Code changes fast, so any course, tutorial, lesson set, or
  internal guide about it drifts out of date: invented commands, renamed conventions,
  archived MCP packages, stale model ids. This skill reads your content, checks every
  Claude Code claim against the current official docs (never from memory), and returns a
  section-by-section validity report plus the safe fixes. Use before you publish or
  re-share any Claude Code training material. Works on any course or docs repo.
author: Mercedes Perez-Capilla
---

# mercedes-lab-update

Teaching content about a fast-moving tool rots quietly. A lesson that was correct when
written can, months later, tell a learner to run a command that no longer exists, install
a package that has been archived, or follow a file convention that has changed. The reader
hits a wall and loses trust in the whole course.

This skill keeps Claude Code teaching content **honest against the source of truth** —
Anthropic's official documentation at `https://code.claude.com/docs` — and proposes the
fixes. It is the companion to writing the content: write it once, re-run this whenever the
product moves or before you re-share.

> This is different from a docs-vs-code sync. This skill validates content *about Claude
> Code* against *Anthropic's external, live docs*, not a repo against its own code.

## When to use it

- Before publishing or re-sharing a Claude Code course, tutorial, or internal guide.
- After a Claude Code release, when commands, conventions, or models may have changed.
- Periodically (e.g. quarterly) on any "evergreen" Claude Code training material.

## What to check (against the live docs — never from memory)

Read the content (markdown lessons, docs, slides-as-text), then verify every Claude Code
claim by fetching the relevant page under `https://code.claude.com/docs`. Common drift
points, with the facts to confirm each run:

- **Slash commands** are real and current — e.g. `/clear`, `/compact`, `/context`,
  `/memory`, `/skills`, `/agents`, `/init`, `/help`, `/mcp`, plan mode (Shift+Tab). Flag
  any invented command. (A frequent one: there is no `/agent <name>` — subagents
  auto-delegate by description or are asked for by name, and are managed with `/agents`.)
- **Skills** convention: a folder `.claude/skills/<name>/SKILL.md`.
- **Subagents** convention: a single file `.claude/agents/<name>.md` with `name` /
  `description` frontmatter — not a per-agent folder containing an `AGENT.md`.
- **Hooks**: configured in `settings.json`; many events exist (PreToolUse, PostToolUse,
  UserPromptSubmit, Stop, Notification, and more). Don't present a small fixed number as
  the complete set. Tool matchers use real tool names (`Read`, `Write`, `Edit`), not
  invented ones like `WriteFileTool`.
- **MCP**: added with `claude mcp add` (or by asking Claude); configured under
  `mcpServers`. Only name `@modelcontextprotocol/server-*` packages that are still active
  reference servers (filesystem, fetch, git, memory, sequentialthinking, time, everything);
  others (slack, github, gdrive, postgres, sqlite…) are archived or vendor-maintained —
  point to the registry / vendor instead of a dead package name. Re-verify each run.
- **Settings**: `settings.json`, `permissions.allow` / `permissions.deny`, exact tool names.
- **Memory**: project `CLAUDE.md` (`./CLAUDE.md` or `.claude/CLAUDE.md`) and user
  `~/.claude/CLAUDE.md`; `/init` to generate.
- **CLI flags** used in headless examples actually exist (e.g. there is no `--cwd`; use
  `--add-dir` or `cd` into the directory).
- **Model ids**: no superseded ids — check the current latest before flagging.

## Quality pass — garbage out, value in

- Flag filler, duplicated guidance, and dead/orphan files (e.g. content not reachable by
  the site's own router).
- Flag genuine gaps where one accurate tip would materially help a learner.
- **Respect the content's audience.** If the material is deliberately no-code (for business
  users), do not inject developer concepts (token caching, exit codes, env-var plumbing)
  just because the docs mention them. Match the existing altitude.

## Respect the project's own rules

Before changing anything, read the project's `CLAUDE.md` / style guide and obey it —
especially scope rules (e.g. "this course is closed: corrections yes, new lessons no") and
voice. Corrections, factual fixes, and removing dead content are safe. Anything that
changes scope is a proposal for the author, not an edit you make.

## Output

1. A **section-by-section report**: ✅ valid / ⚠️ needs fix, each with the specific issue
   and the official source URL.
2. A **proposed-edits list** (file + change), grouped: factual fixes · removals
   (garbage/dead) · useful additions.
3. **Make the safe corrections** (factual fixes, dead-content removal, title/heading sync).
   For anything touching scope or judgment, list it for the author to approve.
4. Verify the content still builds/renders if it's a live site, then summarise what changed.

## The honesty bar (non-negotiable)

Never validate a Claude Code fact from memory — the product moves faster than any model's
training. Fetch the doc, cite the URL, and if a page can't be reached, say so rather than
guessing. A report that says "couldn't confirm `/foo`, verify manually" is worth more than
a confident wrong tick.
