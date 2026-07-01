# Playbook — session kickoff

A short prompt you paste at the **start** of a work session so the agent has the rules, the context, and
a first action before it touches anything. It stops the "eager intern dives in wrong" failure at the
source. Keep it **lean** — point to your profile + docs rather than restating them.

## The skeleton (fill the `{slots}`)

```markdown
You're the {senior architect / lead} for {project}. Follow my work-ethic profile (CLAUDE.md/AGENTS.md).

READ FIRST (then tell me what they say before writing anything):
- {the "resume here" / current-priority doc}
- {the one spec or methodology doc that governs this work}

WHAT NOT TO BREAK (non-negotiables):
- {load-bearing constraint 1 — structural / data-safety / invariant}
- Anti-pattern to avoid by name: {the specific wrong move}

QUALITY BAR:
- {the experience/quality rules that always apply — e.g. never lose in-progress work}

HOW TO WORK:
- Commit each working step immediately (atomic commits), don't dump many changes at once.
- Verify before claiming done — evidence, not assertion.
- Use your tools to do the manual labor; don't hand me copy-paste to run by hand where you can act.

DECISION AUTHORITY: I'm the Director (I own product calls). You execute — propose and evaluate options,
but defer the final product decision to me.

FIRST, DO THIS: confirm the rules, summarize what you learned from the READ-FIRST docs, and propose the
exact next step. Don't start until I ok it.
```

## Why each part
- **Role + framing** sets the *altitude* of thinking you expect.
- **Read-first + report-back** grounds the agent in reality before it acts (and proves it actually read).
- **What-not-to-break** names the invariants *and* the specific anti-pattern, so "don't break things" is
  concrete.
- **Prove-it + cadence** makes verification and atomic commits the default, not an afterthought.
- **Decision authority** keeps the human as Director and the agent as executor — no silent product calls.
- **Required closing action** forces alignment *before* work, which is where misalignment is cheap to fix.

## Keep it lean
Have a variant per mode (design/research vs. implementation), each stating its goal, what to read, the
verification bar, and the first concrete action. Point to a single source-of-truth methodology doc
instead of pasting it — an over-stuffed kickoff buries the rules that matter.
