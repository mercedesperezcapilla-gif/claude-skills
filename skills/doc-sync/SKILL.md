---
name: doc-sync
description: >
  Keeps a project's "north-star" documentation honest and in sync with the actual
  repository. Regenerates SNAPSHOT docs (a STATUS / PROGRESS / "current state" file)
  from live repo facts — registered modules, git branch and merge state, build-phase
  ticks, last-updated date — and FLAGS, never silently rewrites, drift in CURATED
  narrative docs (vision / architecture / design). Make sure to use this skill
  whenever the user wants to update, refresh, or sync project docs; mentions a
  STATUS / PROGRESS / "where are we" file; asks "are the docs up to date" or notices
  docs drifting from the code; or has just merged branches, finished a feature, or
  changed the build phases — even if they don't say the word "doc-sync". Works in any
  codebase and any language.
author: Mercedes Perez-Capilla
---

# doc-sync

Documentation rots because it is written once and edited by hand. This skill keeps it
true to the repo with a simple rule: **automate the snapshot, human-curate the
narrative.** Those are two different kinds of document and they must be treated
differently — collapsing them is how doc-sync tools either go stale or quietly
mangle carefully-written prose.

## The two kinds of doc

- **Snapshot docs** — a `STATUS.md`, `PROGRESS.md`, or "current state" section. These
  answer *"what exists right now?"*. They decay every working session and are safe to
  **regenerate from facts**. doc-sync rewrites these.
- **Curated docs** — a vision / "why" doc, an architecture / "how" doc, a README
  narrative. These are deliberate prose that change rarely. doc-sync **never rewrites
  them unprompted** — it only *flags* discrepancies and proposes edits for the user to
  approve. Auto-editing prose is how you degrade the best writing in the repo.

If you are unsure which bucket a doc is in, ask. When in doubt, treat it as curated
(flag-only) — the cost of a missed flag is lower than the cost of garbling prose.

## How the user configures it

Look for configuration in this order; if none exists, ask the user which docs are
snapshot vs curated and offer to write a `.doc-sync.json`.

1. **`.doc-sync.json`** at the repo root:
   ```json
   {
     "snapshot": ["STATUS.md"],
     "curated": ["docs/VISION.md", "ARCHITECTURE.md"],
     "facts": {
       "components": "grep -nE 'id=\"' src/registry.ts",
       "phases": "STATUS.md"
     }
   }
   ```
   `facts.components` is any read-only command that lists the project's registered
   units (compositions, routes, plugins, services — whatever this project enumerates).
   Omit it if the project has no such registry.
2. **Inline markers** — a doc containing `<!-- doc-sync: snapshot -->` near the top is
   treated as a snapshot; `<!-- doc-sync: curated -->` as curated.
3. **Defaults** — `STATUS.md` / `PROGRESS.md` are snapshot; `VISION*`, `ARCHITECTURE*`,
   `DESIGN*`, `README*` are curated.

## Workflow

### 1. Gather live facts (read-only only)

Never mutate the repo while gathering. Collect whatever the project actually has:

- **Registered units** — run the project's `facts.components` command, or infer it
  (e.g. `grep` the route/registry/manifest file). Count and name them.
- **Branch + merge state** — `git branch`, `git branch --merged <default>`,
  `git status -sb`, `git log --oneline -15`. Distinguish merged vs open branches.
- **Build / phase state** — read the snapshot doc's own phase list and check each
  claim against reality (does the code/dir it references exist?).
- **Optional sanity** — a typecheck / lint / test command if the project has a fast
  one, to mark "green" honestly.

### 2. Regenerate the snapshot doc

Rewrite the snapshot doc to match the facts. Update tables, the branch/backlog
section, phase ticks, and the **"Last updated"** date to today. Preserve the doc's
existing structure and voice — you are refreshing values, not redesigning the file.

### 3. Flag drift in curated docs (do not rewrite)

Compare each curated doc against the facts — e.g. does an architecture doc's component
table still match what's registered? Do the phases agree? **List the specific
discrepancies and proposed edits, then ask before applying any.** Apply only what the
user approves.

### 4. Land the changes

Commit the snapshot refresh (and any approved curated edits). Follow the repo's own
workflow — match its branch/PR conventions; don't push if the project protects its
default branch and the user hasn't asked.

## The honesty bar (non-negotiable)

The whole point is a doc you can trust. Overclaiming destroys that faster than
staleness does. Hold these distinctions in every edit, and prefer the weaker verb when
unsure:

**Examples:**
- `built` ≠ `deployed` — code exists vs it's live for users.
- `committed` ≠ `merged` — on a branch vs on the default branch.
- `wired` ≠ `working` ≠ `shipped` — connected vs verified vs released.
- `passing locally` ≠ `passing in CI`.
- `designed` ≠ `implemented`.

If a claim can't be backed by a fact you gathered, soften it or drop it. A status doc
that admits "not started" where true is worth more than one that rounds up.

## Why it's split this way

A snapshot doc is a *function of the repo state* — regenerating it is correct and
cheap. A vision or architecture doc is *authored intent* — a model rewriting it on
every sync would slowly flatten its meaning. Keeping the human in the loop for prose,
and only for prose, is what makes this safe to run often.
