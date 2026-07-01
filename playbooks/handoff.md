# Playbook — handoff / "resume here"

AI sessions forget. Long work outlives a single chat (and a context reset). The fix: at any stopping
point, keep a short **"resume here"** snapshot so the next session — or the next person, or future-you —
picks up cleanly without re-deriving everything.

## What a good handoff contains
- **Current focus (top of file).** The one thing to work on next, in a line or two — the first thing
  anyone reads.
- **State of play.** What's done, what's in flight, what's blocked; the last *verified-good* checkpoint
  (build/tests/deploy status).
- **Next concrete step.** The specific next action — not a vague direction — so work starts immediately.
- **Open decisions awaiting the human.** Product calls only the Director can make, each with a *proposed
  default* so progress isn't blocked waiting on an answer.
- **What-not-to-break reminder.** A pointer to the non-negotiables so the next session doesn't undo them.
- **Spark / backlog capture.** Ideas or anomalies noticed but not acted on, parked with a one-line "why
  later" so nothing is lost between sessions.
- **Pointers, not restatements.** Link the spec/plan/methodology docs — don't duplicate them (single
  source of truth).

## The one discipline that makes it work
**Refresh the handoff in the *same commit* as the change it describes.** A "resume here" that lags the
code is worse than none — it lies confidently. Treat it as part of the change, not a chore for later.

## Two layers
- A durable **spec / methodology artifact** *is* the handoff between phases (design → implementation).
- A living **`RESUME_HERE.md`** (or similar) carries state *across sessions*. Keep it at the repo root,
  short, and current.

## Use it in one line
Before you stop: could a fresh session start productively from this file alone in 30 seconds? If not,
it's not done.
