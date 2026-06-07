---
name: doc-sync
description: >
  Keeps your project docs honest about what the code actually does. It rebuilds the
  status or progress file from real facts (what's registered in the code, which
  branches are merged, how far the build has really got, today's date), and for the
  vision or architecture docs it points out what's gone stale and lets you approve the
  change instead of rewriting your prose. Good for when you've merged a few branches,
  shipped a feature, or just suspect the status file is lying. Works in any codebase.
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
   `DESIGN*`, `PRD*`, `SPEC*`, `README*` are curated. A PRD or spec is a special case
   of curated: it's a *proposal* that turns true as the project gets built, so flag
   when its stated status (e.g. "not started", a build-order step, a `Status:` line)
   no longer matches what's shipped — and reconcile it with the snapshot doc — but
   propose the edit rather than rewriting the spec.

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

### 4. Refresh exported twins

If a doc has an exported version generated from it — a PDF, an HTML page, a slide
deck — a stale export is as misleading as a stale doc. After the source changes,
regenerate the twin so the two match. Use the project's own build command if it has
one (e.g. a `docs/md2pdf.py`, a `make docs`, a pandoc invocation); if it doesn't,
flag the exports that are now out of date rather than guessing at a tool. Don't
regenerate a twin for the snapshot doc unless the project clearly publishes one —
snapshots churn, and a PDF of a thing that changes every session is just noise.

### 5. Land the changes

Commit the snapshot refresh, any approved curated edits, and the regenerated
exports. Follow the repo's own workflow — match its branch/PR conventions; don't
push if the project protects its default branch and the user hasn't asked.

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
