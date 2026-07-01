# Memory — give your agent continuity across sessions

**The problem:** every new chat, the agent forgets who you are, how you like to work, and every
decision you made last time. You re-explain yourself constantly.

**The fix:** a tiny, plain-text memory. One folder, one index file, and one file per fact. The agent
reads the index when a session starts and writes new facts as it learns them. No database, no service —
just markdown you (and the agent) can read.

> **Honest framing (same spirit as the rest of this kit):** this is a **convention the agent follows**,
> not a built-in that auto-remembers. It works because your profile *tells* the agent to read and write
> these files — see "Wire it in" below. If your tool supports a session-start hook, you can make the
> read automatic; otherwise the agent does it because the profile says so.

---

## How it works

```
memory/
  MEMORY.md               ← the index: one line per fact, loaded at session start
  <slug>.md               ← one fact per file (create as many as you need)
  memory-file.template.md ← copy this to start a new fact
```

- **One fact per file.** Small and focused beats one giant file. The filename is a short kebab-case
  slug (e.g. `prefers-terse-replies.md`).
- **`MEMORY.md` is the index** — one line per fact: `- [Title](slug.md) — one-line hook`. This is what
  the agent loads every session, so keep each line short (under ~200 chars). Detail lives in the fact
  file, never in the index.
- **Each fact file has frontmatter** so the agent can judge relevance at a glance (see the template).

## The four kinds of memory (the `type` field)

| Type | What it captures | Example |
|---|---|---|
| `user` | Who you are — role, expertise, preferences | "Beginner at SQL; define jargon" |
| `feedback` | How the agent should work — a correction or a confirmed approach | "Always show me the test output, don't just say it passed" |
| `project` | Ongoing goals/constraints not obvious from the files | "We're pre-launch; no breaking API changes until March" |
| `reference` | Pointers to external things (URLs, dashboards, tickets) | "Staging dashboard: <url>" |

For `feedback` and `project`, add a **Why:** line and a **How to apply:** line — future-you (and the
agent) needs the reason, not just the rule. Link related facts with `[[other-slug]]`.

## Wire it in (one paste)

Add this block to your profile (`CLAUDE.md` / `AGENTS.md`) so the agent actually uses the folder:

```markdown
## Memory
At the start of each session, read `memory/MEMORY.md` and treat each linked fact as background context.
When you learn something durable about me, my preferences, or this project that isn't already in the
code, write it as a new `memory/<slug>.md` file (frontmatter per `memory/memory-file.template.md`) and
add a one-line pointer to `memory/MEMORY.md`. Before saving, check for an existing file that already
covers it and update that instead of duplicating. Delete a memory if it turns out to be wrong. Don't
store what the code, README, or git history already records.
```

## Keeping it healthy
- **Don't store what the repo already says** (file structure, past fixes, anything in git history) —
  memory is for what's *not* recoverable from the code.
- **One line in the index, real content in the file.** If the index bloats, the session-start load
  gets expensive.
- **Prune.** A wrong memory is worse than none — the agent will trust it. Delete stale facts.
- **Keep it private if it's personal.** If your memory holds personal specifics, don't commit it to a
  public repo — add `memory/*.md` (except the template + this README) to `.gitignore`.
