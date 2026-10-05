# Exercise 6 — Ship-velocity anti-pattern diagnosis

**Time:** ~2 hours. **Deliverable:** one anti-pattern
diagnosis of a real (or plausible synthetic) team's
cadence — a five-slot scorecard against the Lecture 6
anti-patterns, named structural counter-moves for each
present pattern, a DORA-shaped cadence check, a monthly
cadence-retro agenda, and a reviewer's memo on the
diagnosis you least wanted to write.

## Purpose

Apply the diagnostic lens from
[Lecture 6](../lectures/06-ship-velocity-anti-patterns.md)
to the cadence you authored in Exercises 1–2 and the
PRD / Figma / iteration-loop work from Exercises 3–5.
The lecture argues that the five anti-patterns —
**planning theatre, PRD gestation, design-debt-in-
review, spec-then-hand-off, the "agile" waterfall** —
are structural, not cultural, and that the move is to
design each *out* of the cadence rather than observe
them in a retrospective. This exercise forces you to
look at your own cadence design (and, if you have one,
your current team's actual rhythm) and name which
anti-patterns the design would and would not survive
contact with reality.

## Use the team from Exercises 1–5

Do not rescope. The target of the diagnosis is the
cadence you authored in
[Exercise 1](exercise-01-dual-track-cadence-authoring-for-one-team.md)
with the delivery operating model from
[Exercise 2](exercise-02-shape-up-vs-weekly-kanban-choice-drill.md),
producing the PRDs from
[Exercise 3](exercise-03-prd-in-amazon-6-pager-shape.md),
with the pixel-and-microcopy discipline from
[Exercise 4](exercise-04-figma-mockup-and-microcopy-drill.md),
and (if applicable) the AI-substrate iteration loop
from
[Exercise 5](exercise-05-agentic-ux-iteration-loop-drill.md).
If your team is real, also diagnose the *actual*
current rhythm as a parallel column — the delta between
"the cadence we designed" and "what we currently do" is
where the anti-patterns live.

## What the diagnosis must contain

Three to four pages. Adopt the shape from
[Lecture 6](../lectures/06-ship-velocity-anti-patterns.md),
in the following order.

### 1. Team context recap (quarter page — consumed)

- **Team shape** consumed from Exercise 1 (trio,
  engineering headcount, product surface, discovery
  maturity).
- **Operating model** consumed from Exercise 2 (Shape
  Up or weekly-ship kanban, with named cycle /
  WIP-limit).
- **Current-state diagnosis** (if real team) — one
  sentence on what the current rhythm actually looks
  like today, not the designed one.

Not a repeat of Exercise 1; a reference anchor.

### 2. The five-anti-pattern scorecard (one and a half pages)

For each of the five
[Lecture 6 anti-patterns](../lectures/06-ship-velocity-anti-patterns.md),
score **present / incipient / absent** against the
designed cadence (and, if applicable, the real
current cadence as a second column). For every
*present* and *incipient* score, cite the specific
evidence — a ritual, an artifact, a measurable
behavior — not an impression.

The five:

- **Planning theatre.** Are the same decisions being
  re-discussed in successive planning meetings? Look
  at the last three planning artifacts (if real) or
  the designed cadence's planning rituals (if
  synthetic) and count topic recurrence.
- **PRD gestation.** How long does a PRD stay in
  active draft? Who comments, when? Is the ship or
  the doc the deliverable? For your Exercise 3
  six-pager, how long did it take to draft and how
  many revisions did it absorb before silent reading?
- **Design-debt-in-review.** Does a "design debt" or
  "polish backlog" exist? When mockups turn into
  implementations, how often do they match? Does the
  Exercise 4 pre-ship walk actually get run, or is
  it an item on the checklist that gets skipped under
  deadline pressure?
- **Spec-then-hand-off.** Is the team organized by
  trio or by function? Are there "design review" or
  "PRD sign-off" meetings separate from the regular
  trio rhythm? Is the CPO functioning as a specifier
  rather than as a trio member?
- **The "agile" waterfall.** What is the deploy
  frequency (DORA, consumed from the CTO)? Does the
  team talk about a "launch date" that structures
  the quarter? Is there a discovery *phase* or a
  design *phase* preceding build?

For each anti-pattern score, write one to three
sentences of specific evidence. Not "we might have
some planning theatre" — "the Q3 planning doc has
been in Notion untouched for six weeks; the same two
roadmap items have been 'decided' in each of the
last three monthlies."

A scorecard is **honest** or it is useless. The CPO
job is not to produce a report card that passes
inspection; it is to find the anti-patterns before
they strangle the cadence.

### 3. The named structural counter-moves (one page)

For every anti-pattern scored **present** or
**incipient**, name the specific structural counter-
move you are putting into the cadence. Not "we'll be
disciplined." A rule, a ritual change, a deleted
meeting, or a redefined deliverable.

Each counter-move must have:

- **The move.** The concrete change ("delete the
  monthly product planning meeting"; "move the PRD
  silent reading from async comments to a 30-minute
  in-person Thursday ritual"; "add a mandatory
  mid-cycle design review at week 3 of every Shape
  Up bet"; "trio members are named per bet with
  attendance tracked at the Thursday sync").
- **The lecture discipline it enforces.** Which
  Lecture 1–5 discipline is this move making
  structural? ("This enforces the
  [Lecture 1 trio discipline](../lectures/01-dual-track-discovery-delivery-cadence.md#what-the-founding-cpo-does-personally)
  that absence from the Thursday sync triggers
  renegotiation.")
- **The observable.** What a reviewer could *see*
  that would tell them the counter-move is working.
  ("Deploy frequency ≥1x per week per DORA, measured
  at the Friday review"; "No PRD older than two
  weeks in active draft at any point in the
  quarter.")
- **The failure signal.** What would tell you the
  counter-move itself has failed, so you can
  re-design before the anti-pattern re-establishes.
  ("If the Thursday sync is cancelled twice in a
  month without a Monday-interview-cancelled
  counterbalance, trio collapse is forming — audit.")

Produce one counter-move per present / incipient
anti-pattern. If an anti-pattern is absent in both
columns, do not invent a counter-move for it.

### 4. The DORA cadence check (quarter page — consumed)

The engineering-side measurement regime the CPO
consumes from
[cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum).
From
[Lecture 6](../lectures/06-ship-velocity-anti-patterns.md#what-the-cto-owns-that-the-cpo-consumes),
ask the CTO (or the eng lead, or your plausible
synthetic eng lead) for:

- **Deploy frequency.** How often does the team ship
  code to production? Weekly, monthly, quarterly?
- **Lead time for changes.** How long between a
  commit and that commit being in production?
- **Change failure rate.** What percentage of
  changes cause an incident, rollback, or hotfix?
- **MTTR.** When something breaks, how long until it
  is restored?

Note the numbers against the cadence you designed. A
Shape-Up-designed cadence that produces one deploy
per quarter is misaligned at a structural level
regardless of what the Shape Up ritual claims. A
weekly-kanban-designed cadence with a two-week lead
time means commits are getting stuck somewhere; the
operating model is downstream of the pipeline.

If the CTO cannot produce the numbers, note that too
— the measurement regime itself is missing and the
CPO cannot do the cadence check. Cite the
[cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)
boundary.

### 5. The monthly cadence retro (half page)

Author the monthly cadence retrospective ritual from
[Lecture 6](../lectures/06-ship-velocity-anti-patterns.md#the-retro-that-actually-works):

- **Cadence of the retro.** Monthly, not per sprint
  (sprint retros ritualize the operating model;
  cadence retros audit the model itself).
- **Attendees.** The trio plus the eng lead plus (if
  the team has one) the CTO.
- **The one-and-only rule.** Every retro finding
  becomes a *specific change to the cadence*. Not a
  Jira ticket. Not an aspiration. A ritual that
  moves, gets added, gets deleted, or gets re-scoped.
  If the finding does not map to a cadence change,
  the finding is fluff.
- **The agenda.** Three questions:
    1. Which of the five anti-patterns from Lecture 6
       showed signs this month? (The scorecard from
       Section 2, re-scored.)
    2. Which previous counter-moves are working, and
       which are decorative?
    3. Which cadence change goes into effect this
       week, and who owns the change?
- **The anti-ritual rule.** The retro is itself a
  ritual that can degrade into ceremony. If three
  consecutive retros produce no cadence change, the
  retro itself has become theatre; cancel it, redesign
  it, or move it to quarterly.

### 6. Diagnostic reflection (quarter page)

A paragraph on the anti-pattern you least wanted to
diagnose honestly in your team (or your designed
cadence). Why was it uncomfortable? What political,
emotional, or inherited-habit reason made it hard to
score accurately? This is the surface a founding-CPO
job interview will test; writing the paragraph
rehearses the muscle.

## Starter guidance

- **Score honestly.** The exercise is worthless if the
  scorecard reads as "we did Exercise 1 so well that
  no anti-patterns can appear." Every designed cadence
  has at least one incipient anti-pattern; the honest
  diagnosis names it.
- **Cite evidence, not impression.** A score of
  "incipient PRD gestation" with no specific example
  is a guess; a score of "incipient PRD gestation —
  the Exercise 3 six-pager took eight hours to draft
  and absorbed four reviewers' async comments before
  the silent-reading ritual" is a diagnosis.
- **Consume DORA from the CTO, do not re-derive.**
  Deploy frequency, lead time, change-failure rate,
  MTTR — these are level-25 work owned by the CTO.
  Ask for the numbers; do not build the dashboard
  yourself.
- **Counter-moves are structural, not cultural.**
  "We'll be disciplined about the Thursday sync" is
  not a counter-move. "Attendance at the Thursday
  sync is tracked; two misses in a row triggers
  renegotiation of the trio" is a counter-move.
- **The absent column is informative.** If an
  anti-pattern is genuinely absent in your designed
  cadence, say so and name what in the design makes
  it absent. The absence is often the thing that
  needs to be preserved under future pressure.
- **If your team is real, run the exercise against
  the real rhythm, not the aspirational one.** The
  cadence you *designed* in Exercise 1 is one column;
  the rhythm the team *runs* today is the other. The
  gap is where the diagnosis bites.
- **Expect the fifth anti-pattern (agile waterfall)
  to be present in some form at most teams you join.**
  It is the degenerate form; its presence is not a
  team-failure signal, it is a cadence-redesign
  signal.

## The reviewer's memo

Half a page, written after the scorecard and the
counter-move design. Answer:

- **Which anti-pattern was present that you did not
  expect?** The uncomfortable finding — the one that
  reveals your designed cadence is quietly wrong on
  something you thought it was right on.
- **Which counter-move will face the most political
  resistance?** From whom (the founder-CEO, the eng
  lead, a specific engineer, your own habit)? What
  is the shape of the argument you would need to
  have to put the counter-move in place?
- **Which Lecture 1–5 discipline is doing the most
  anti-pattern-blocking work?** If you could keep
  only one of the Lecture 1–5 disciplines
  (dual-track rhythm, operating-model choice,
  six-pager form, pixel-and-microcopy, AI iteration
  loop), which one would preserve the most
  anti-pattern immunity? Why?

## Acceptance criteria

- Team context recap cites Exercise 1 shape, Exercise
  2 operating model, and (if real) a one-sentence
  current-state description.
- Scorecard scores all five anti-patterns on
  present / incipient / absent, with specific
  evidence (not impression) for every non-absent
  score, in both designed and current-state columns
  (if the team is real).
- Every present or incipient score has a named
  structural counter-move with the move, the
  Lecture 1–5 discipline, the observable, and the
  failure signal.
- DORA cadence check cites consumed numbers (or
  flags the measurement regime as missing).
- Monthly cadence-retro ritual is authored with
  cadence, attendees, agenda, the one-and-only
  rule, and the anti-ritual rule.
- Diagnostic reflection paragraph names the
  anti-pattern you least wanted to diagnose
  honestly.
- Reviewer's memo answers all three prompts.

## Common failure modes

- **Universal-absence scoring.** Every anti-pattern
  marked absent. The scorecard is not credible;
  every designed cadence has at least one incipient
  pattern.
- **Evidence-free scoring.** "Incipient planning
  theatre" with no citation. A score without
  evidence is a guess.
- **Cultural counter-moves.** "We'll be more
  disciplined about X" as the counter-move. Lecture
  6's whole argument is that the move is
  structural, not cultural; counter-moves have to
  change the cadence mechanically.
- **DORA-skipping.** Not consulting the CTO for
  deploy frequency, lead time, change-failure rate,
  MTTR. The deploy-frequency number is the fastest
  diagnostic for the "agile" waterfall; skipping it
  wastes the exercise.
- **Retro-as-ceremony.** The monthly cadence retro
  authored as a status meeting with no
  cadence-change rule. The whole point of the retro
  is that findings become cadence changes.
- **Blame-shaped diagnoses.** Diagnoses that name a
  specific person as the problem ("the founder-CEO
  keeps extending Shape Up appetites"). Anti-
  patterns are structural; the diagnosis names the
  structure, and the counter-move changes it.
- **Scorecard-for-praise.** The exercise written as
  "look at how well our designed cadence prevents
  anti-patterns." The exercise exists to find
  patterns you missed, not to validate the ones you
  caught.
- **Deferral-dodging.** Diagnosing an anti-pattern
  without naming the political cost of removing it.
  Many of these counter-moves will fight a founder-
  CEO habit, a legacy process, or a stakeholder
  expectation — naming the fight is the exercise.

## Source alignment

The anti-pattern catalogue derives from Ryan Singer,
*Shape Up: Stop Running in Circles and Ship Work
that Matters*, Basecamp, 2019 —
[basecamp.com/shapeup](https://basecamp.com/shapeup) —
Chapter 1 (planning-ritual anti-pattern) and Chapter
13 (hills / in-flight review); from Marty Cagan,
*Inspired: How to Create Tech Products Customers
Love* (2nd ed.), Wiley, 2017, Chapter 8 ("faux
agile") —
[svpg.com/inspired](https://www.svpg.com/inspired-how-to-create-products-customers-love/);
and from Marty Cagan with Chris Jones, *Empowered*,
Wiley, 2020, Chapters 8–10 (empowered trio as
counter to functional-org hand-offs) —
[svpg.com/empowered](https://www.svpg.com/empowered-ordinary-people-extraordinary-products/).
The six-pager anti-gestation discipline derives from
Jeff Bezos, "2004 Letter to Shareholders" —
[aboutamazon.com/news/company-news/2004-letter-to-shareholders](https://www.aboutamazon.com/news/company-news/2004-letter-to-shareholders) —
and Colin Bryar & Bill Carr, *Working Backwards*,
St. Martin's, 2021, Chapter 4 —
[workingbackwards.com](https://www.workingbackwards.com/).
The DORA cadence-check consumption boundary derives
from Nicole Forsgren, Jez Humble & Gene Kim,
*Accelerate: The Science of Lean Software and
DevOps*, IT Revolution, 2018 —
[itrevolution.com/product/accelerate](https://itrevolution.com/product/accelerate/) —
and the ongoing program at
[dora.dev](https://dora.dev/); the SRE-side regime
is level-25 work owned by
[cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum).
Don Reinertsen, *The Principles of Product
Development Flow*, Celeritas, 2009 —
[celeritaspublishing.com](https://celeritaspublishing.com/product/the-principles-of-product-development-flow/) —
is the general argument for frequent-small
commitment rituals the counter-moves rest on. The
monthly cadence-retro form derives from Esther
Derby & Diana Larsen, *Agile Retrospectives: Making
Good Teams Great*, Pragmatic Bookshelf, 2006 —
[pragprog.com/titles/dlret](https://pragprog.com/titles/dlret/agile-retrospectives/) —
re-shaped for the cadence-not-sprint scope
Lecture 6 argues for.
