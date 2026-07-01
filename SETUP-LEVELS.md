# Setup levels — climb to a top-tier agent setup without drowning

**The honest version of "get me a 99th-percentile setup."** A great setup isn't a pile of files — it's
a few disciplines, *enforced*, added one at a time so you actually adopt them. Start at Level 1. Add the
next level only when the current one feels automatic. You can stop at any level and still be better off.

> **What "99th percentile" honestly means here.** These levels put your **setup** (the harness around
> the agent) in the top few percent — most people run an agent with *none* of this. What a repo can't
> hand you instantly is **skill** (spotting when the agent is wrong, taste). That grows with use. So:
> elite *setup* on day one; the *judgment* compounds as you go. Don't let anyone sell you "instant
> expert" — this is "instant good scaffolding," which is the part you can actually install.

---

## Level 1 — Profile (advisory) · 30 seconds
**What:** drop a work-ethic profile into your project so the agent works like a disciplined senior.
**Do:** copy [`profile/reference.md`](profile/reference.md) (or a [`ready-made/`](profile/ready-made/)
archetype) into your project as `CLAUDE.md` / `AGENTS.md`.
**You now get:** outcome-first replies, decide-and-flag, numbered VERIFY steps.
**Gap it leaves:** the rules fade as the chat grows, and the agent forgets everything next session.

## Level 2 — Enforced · +2 minutes
**What:** a hook (a tiny script the agent runs every turn) that re-injects the contract so it never
fades.
**Do:** follow [`INSTALL.md`](INSTALL.md) section B — install `hooks/ship-bar.sh` and wire it via
`hooks/settings-snippet.json`.
**You now get:** the discipline holds on turn 50 the same as turn 1.
**Gap it leaves:** still no memory across sessions.

## Level 3 — Continuity (memory) · +5 minutes
**What:** a lightweight file-based memory so the agent remembers your preferences, decisions, and
project facts **across sessions** — no re-explaining yourself every time.
**Do:** see [`memory/README.md`](memory/README.md) — create the `memory/` folder and paste one snippet
into your profile so the agent reads and writes it.
**You now get:** the single biggest jump — the agent stops being an amnesiac.
**Gap it leaves:** "done" is still the agent's word, not a verified fact.

## Level 4 — "Done = green" (commit gate) · +5 minutes *(coding projects)*
**What:** a pre-commit hook that runs your build/test/lint and **blocks the commit on failure**, so
"done" means *verified*, not *claimed*. (Skip if you're not writing code.)
**Do:** *(shipping as a template next — see the roadmap below.)*
**You now get:** the agent can't tell you it's done when it's broken.

## Level 5 — Playbooks · ongoing
**What:** the process habits that separate good from elite — a planning framework, lean session
kickoffs, folder-local rules (nested `CLAUDE.md`), and a handoff routine so long work survives a
context reset.
**Do:** *(shipping as `playbooks/` next — see the roadmap below.)*

---

## Roadmap (what's shipping into these levels)
- **Level 4 template** — a portable `.githooks/pre-commit` (build → test → lint, with a docs-only
  fast-path) + one line to install it.
- **`playbooks/`** — planning framework, lean-kickoff template, nested-`CLAUDE.md` pattern, handoff/
  `RESUME_HERE` discipline. Each a one-page, optional habit.
- **One-command installer** — `install.sh` that sets up every level you choose, once the tiers above
  land.
- **More ready-made archetypes** — `beginner`, `senior-fast-shipper` alongside `adhd-friendly`.

**Design rule for all of it:** every level is *optional* and *self-contained*. Adding a level must
never make Level 1 harder to understand. Low cognitive load is the product, not a nice-to-have.
