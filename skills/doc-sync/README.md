# doc-sync

Docs rot because you write them once and then edit them by hand, badly, when you
remember to. doc-sync keeps them honest with one rule: regenerate the parts that are
just facts, and leave the writing to you.

Two kinds of doc, treated differently:

- Status and progress files answer "what's true right now?", and that changes every
  session. doc-sync rebuilds these from the repo itself: what's registered in the
  code, which branches are merged, how far the build has got, today's date.
- Vision and architecture docs are writing, not data. doc-sync won't touch the prose.
  It tells you what's gone out of date and proposes the edit; you decide.

It also holds a line on honesty, because a status doc that rounds up is worse than no
status doc at all. Built isn't deployed. Committed isn't merged. Wired isn't working,
and working isn't shipped. If a claim isn't backed by something it found in the repo,
it softens it or drops it.

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
