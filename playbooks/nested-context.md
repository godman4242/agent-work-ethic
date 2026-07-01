# Playbook — nested context (folder-local rules)

**Most agent mistakes are context failures, not reasoning failures** — it edits in the wrong place,
breaks a convention, or duplicates a helper because it couldn't see the local rules of *that* corner of
the codebase. A single root instruction file can't hold every folder's specifics without becoming a
wall nobody reads.

**The fix:** put a small **folder-local instruction file** in your densest / highest-churn directories.
Many agents (e.g. Claude Code with nested `CLAUDE.md`) **auto-load** the file for the folder they're
working in — so the right rules arrive exactly when needed, and the root file stays lean.

## What goes in a folder-local file
Keep it a *map*, not a catalogue. For that folder:
- **Purpose** — what this folder is responsible for, in a line.
- **Local rules / invariants** — the "don't do X here" specific to this area.
- **How to test it** — the exact command to verify a change in this folder.
- **Landmines** — the non-obvious coupling ("edit A, not B, for feature C"), pinned dependencies, gotchas.

## Rules of thumb
- **Cite symbols, not line numbers** — line numbers rot on the next edit; a function/constant name
  doesn't.
- **Complement the root, don't duplicate it** — point to the root for global rules; only add what's
  *local*.
- **Only where it pays** — the 2–3 folders with the most complexity or the most regressions. A file in
  every folder is overhead that invites rot.
- **A map, not a novel** — if it's longer than a screen, you're documenting too much.

## Payoff
A fresh session editing that folder references the local rule *without you pasting it* — that's the test
that it's working. It's the cheapest, highest-leverage way to stop the "edited in the wrong place / broke
a convention" class of mistake.
