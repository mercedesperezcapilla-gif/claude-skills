# doc-sync

Keep a project's north-star docs honest and in sync with the actual repo — without a
bot quietly mangling your best prose.

Documentation rots because it's written once and edited by hand. `doc-sync` fixes that
with one rule: **automate the snapshot, human-curate the narrative.**

- **Snapshot docs** (a `STATUS.md`, `PROGRESS.md`, a "current state" section) answer
  *"what exists right now?"*. They decay every session, so doc-sync **regenerates**
  them from live repo facts — registered components, git branch/merge state,
  build-phase ticks, last-updated date.
- **Curated docs** (vision / "why", architecture / "how", README narrative) are
  deliberate prose. doc-sync **never rewrites them** — it only *flags* drift and
  proposes edits for you to approve.

Baked in is a non-negotiable **honesty bar**: *built ≠ deployed*, *committed ≠ merged*,
*wired ≠ working ≠ shipped*. A status doc you can trust beats one that rounds up.

## Install

**Claude Code:** copy the folder into your skills directory —
```
skills/doc-sync/  →  ~/.claude/skills/doc-sync/
```
Then type `/doc-sync`, or just describe the task (see below).

## Try saying

- "Update the docs — we just merged a few branches."
- "Is STATUS.md still accurate?"
- "Sync the project docs with the code."
- "Refresh the status file and tell me if the architecture doc is out of date."

## Configure (optional)

Drop a `.doc-sync.json` at your repo root to tell it which docs are which:

```json
{
  "snapshot": ["STATUS.md"],
  "curated": ["docs/VISION.md", "ARCHITECTURE.md"],
  "facts": { "components": "grep -nE 'id=\"' src/registry.ts" }
}
```

No config? It falls back to sensible defaults (`STATUS`/`PROGRESS` = snapshot;
`VISION`/`ARCHITECTURE`/`DESIGN`/`README` = curated) and asks when unsure.

Works in any codebase, any language.
