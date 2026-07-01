# Playbook — feature workflow: two modes, plan-first

Most output quality is decided *before* any code — by the plan. This workflow optimizes for plan
quality, then execution discipline.

## Two session modes (the written spec is the handoff between them)
- **Design & Research** — *diverge → validate → decide.* Turn a fuzzy idea into a validated, prioritized
  spec + a decision log. **No production code.** Optimize for thinking quality.
- **Implementation** — *test-first → ship.* Turn an *approved* spec into tested, deployed work. Optimize
  for execution discipline.

## Right-size it (bias to action)
Only run a Design session if you answer **"no"** to either: (1) *Do I already know exactly what to
build?* or (2) *Is the evidence it'll work uncontested?* If both are "yes," skip straight to
implementation. Design sessions are for genuinely uncertain / evidence-heavy work — not a tax on every
small change.

## The counter-intuitive order: plan → research → implement
Researching *first* anchors you to existing solutions and you design within what you happened to find.
Instead:
0. **Orient** (optional ~5-min scan — only if the domain is unfamiliar).
1. **Diverge / first-principles plan** — generate options and a draft design from the *problem itself*
   before deep reading; write each option's assumptions down.
2. **Research to validate, challenge & expand** — read *adversarially*: for each key assumption, hunt for
   evidence it's *wrong* and for alternatives you missed.
3. **Converge** — revise, kill options the evidence kills, record decisions + confidence.
4. Optional **second targeted pass** on the single riskiest remaining assumption.
5. **Implement** (separate session).

## Research-quality rules (raise signal, cut noise)
- **Decision-linked questions only** — "Should we X or Y *for our context*?", never "Tell me about Z." If
  a finding wouldn't change a decision, don't research it.
- **Adversarial** — look for where the technique *fails*; steelman the alternative.
- **Grade the evidence** — prefer systematic reviews / primary sources over blog summaries; record
  *effect size + direction + confidence*, not just "it helps."
- **Triangulate** — ≥2 independent credible sources before adopting a claim; flag thin/contested evidence.
- **Transfer check** — does the evidence actually apply to *your* users/context?
- **Separate truth from decision** — research says what's *likely true*; product judgment + your
  non-negotiables decide what you *build*.
- **Assumption & confidence log** — per decision: the assumption, evidence strength, what would change
  your mind.
- **Time-box each question; output a decision record, not a literature dump. Stop when the load-bearing
  assumptions are triangulated and more reading no longer changes the call.**

## Prioritize into a roadmap, not a list
Score candidates roughly **Impact × Confidence ÷ Effort**. Deep-spec only the top 1–2; park the rest with
a one-line "why later." Sanity-check the winners against your non-negotiables.

**Keep it alive:** update this workflow when a tactic demonstrably pays off; prune what stopped earning
its place. A methodology that can't change becomes cargo-cult.
