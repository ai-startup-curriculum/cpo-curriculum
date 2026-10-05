# Exercise 5 — Engineering scope conflict resolution drill

**Time:** ~2 hours. **Deliverable:** one scope-
conflict resolution memo covering all four moves
from
[Lecture 5](../lectures/05-engineering-scope-conflict.md),
one cost-to-carry worksheet with real (or
plausibly-sourced) numbers, one Shape-Up appetite
spec with a circuit-breaker, and a reviewer's memo
— against a real (or plausible) rewrite-vs-ship
conflict.

## Purpose

Rehearse the four-move framework for engineering
scope conflict — rewrite, refactor-in-place, ship-
and-fix-later, kill — against a *specific*
component where the eng team is pushing for a
rewrite and the roadmap is pushing to keep
shipping. The output is the exact artifact a
founding CPO brings to the CPO / CTO / CEO
scope-conflict conversation.

The target failure mode this exercise rehearses
against is *resolving by authority* — the single
dominant Lecture 5 pattern — and the specific
counter-move is *resolving by evidence*. Done
well, this drill produces a memo you'd
confidently paste into the next consensus
meeting with your eng lead.

## Choosing the conflict

Pick one real "rewrite vs. ship" conflict where
the eng team is pushing to replace or
significantly refactor a component and you're
pushing to ship the next feature on top of it (or
vice versa). In order of preference:

1. **A live scope argument on your team.**
   Highest-value drill; the memo is the real
   artifact.
2. **A dispute from your last role**, or one you
   watched a founding team work through.
3. **A plausible synthetic.** The classic shapes
   (any one works): the auth / session service
   that was spiked in month one and now blocks
   SSO; the payments module that each new SKU
   makes harder to touch; the AI orchestration
   layer that was fine for one agent but strains
   under the second; the data-ingestion
   pipeline whose nightly reruns now take 11
   hours. If you go synthetic, write a one-
   paragraph setup: product shape, component in
   dispute, who's pushing which way, and the
   current roadmap pressure.

Whichever you pick, name the component
specifically (file paths, service names,
dashboards). "Our auth system" is too diffuse;
"`services/auth` — Flask app, Postgres session
table, in-flight PR #482 to add SSO" is the
right size.

## What the artifact bundle must contain

Roughly 4–5 pages. The memo is the primary
artifact; the worksheet and appetite spec feed
into it.

### 1. The scope-conflict resolution memo (2–3 pages)

The exact shape from
[Lecture 5 §"The scope-conflict resolution memo"](../lectures/05-engineering-scope-conflict.md#the-scope-conflict-resolution-memo).
Seven sections:

- **The surface at issue** (one paragraph).
  Which component, where it lives, what it
  does, who touches it.
- **The eng position** (one paragraph). What
  the eng team wants to do (typically rewrite
  or deep refactor), the cost-to-carry evidence
  they cite, and the bounded appetite they'd
  commit to.
- **The product position** (one paragraph).
  What the CPO wants to do (typically ship
  next), the roadmap commitment or opportunity
  backing it, and the cost of pausing on this
  surface.
- **The four moves considered.** One paragraph
  each: *rewrite, refactor-in-place, ship-and-
  fix-later, kill.* Each paragraph names which
  Lecture 5 "when it's right" conditions apply
  (or don't) *for this specific case*. Kill
  included *even if obviously wrong* — per
  Lecture 5, naming it is the discipline.
- **The recommended move** (one paragraph).
  With the specific evidence that supports it,
  from the Lecture 5 "evidence each move
  demands" rubric.
- **The out-condition.** For a rewrite, the
  Shape-Up circuit-breaker (see Artifact 3
  below). For ship-and-fix-later, the named
  fix with trigger and owner. For refactor-in-
  place, the measurable improvement over time.
  For kill, the customer-notification story.
- **The specific commitment.** Named engineer,
  named PM, named date, named artifact. Not a
  team; a person.

### 2. The cost-to-carry worksheet (1 page)

From [Lecture 5 §"Cost-to-carry as the load-
bearing evidence"](../lectures/05-engineering-scope-conflict.md#cost-to-carry-as-the-load-bearing-evidence).
The four categories:

| Category | Metric | Current estimate | How it was estimated | Error-bar reasoning |
|---|---|---|---|---|
| Direct cost | Engineer-hours per week spent maintaining the component | … | Incident log, bug backlog, on-call diary | ±X% because … |
| Marginal cost | Hours added to each new feature on top of this surface | … | Last 5 features vs. previous 5; cycle-time trend | ±X% because … |
| Risk cost | Expected cost of incidents, security exposure, compliance breaches attributable to this component | … | Incident count × severity, breach-cost estimate | ±X% because … |
| Opportunity cost | Roadmap items that can't be built on the current version | … | Named mod-002 queue items blocked by this surface | ±X% because … |

- **At least one row has real numbers** from
  the team you're drilling against. The others
  can be plausibly-sourced estimates (practice-
  grounded, not fabricated).
- **Wide error bars are fine.** Lecture 5 is
  explicit: *"wide error bars are fine; no
  numbers at all is the failure to avoid."*
  Name the error bar and explain it.
- **The one-line verdict.** Does annualized
  cost-to-carry exceed the cost of the rewrite
  (including opportunity cost of the eng team's
  time during the rewrite) inside the appetite
  the team can commit to? Yes / no / unclear,
  with the one-sentence reason.

### 3. The Shape-Up appetite and circuit-breaker (half page)

If the recommended move is *rewrite* or a bounded
*refactor-in-place*, the appetite from
[Lecture 5 §"The Shape Up circuit-breaker"](../lectures/05-engineering-scope-conflict.md#the-shape-up-circuit-breaker):

- **The appetite.** "Two weeks," "six weeks."
  Named concretely. Ryan Singer, *Shape Up*,
  Basecamp, 2019 —
  [basecamp.com/shapeup/1.2-chapter-03](https://basecamp.com/shapeup/1.2-chapter-03)
  — is the source vocabulary.
- **What fits inside the appetite** (one
  paragraph). The eng team's shaping work —
  what will and won't be in the rewrite scope.
- **The three circuit-breaker outcomes** at the
  appetite's end:
  - **Ship:** roadmap resumes on the new
    version.
  - **Close — short extension (≤25% of the
    original appetite).**
  - **Not close — stop.** The team evaluates
    and resumes the current version. This is
    the design, not the failure mode.
- **The named roadmap commitments at risk**
  during the appetite window. Which mod-003
  bets slip, by how much, with the mitigation.

If the recommended move is *ship-and-fix-later*,
replace this section with the named-fix spec:

- The specific fix in one paragraph.
- The scheduled date and trigger (per Lecture 5
  — "when we have time" is not a trigger).
- The named owner.
- The written-not-verbal debt acknowledgement
  that goes with it.

If the recommended move is *kill*, replace this
section with the customer-notification spec:

- Who gets notified, when, and how.
- The deprecation window.
- The confirmed maintenance-cost saving.

If the recommended move is *refactor-in-place*,
replace this section with the refactor spec:

- The named structural improvements (specific
  changes with estimated impact).
- The refactor-percentage commitment per sprint
  / cycle (Lecture 5 cites a ~15–25% range as
  a practitioner rule of thumb).
- The measurable improvement over time —
  cost-to-carry trending down, feature-cycle
  time trending down, or an equivalent metric.

## Starter guidance

- **Name the conflict specifically.** "There's
  tension on the backend" is useless; the
  memo's leverage comes from naming the file,
  the service, the PR, the slipped roadmap
  commitment.
- **Fill all four moves even when one is
  obviously right.** Lecture 5 §"When each
  move is right" is explicit: naming all four
  forces the choice off *"binary"* and onto
  *"which evidence supports which."* Kill
  especially — most memos skip it.
- **Push for the cost-to-carry numbers.**
  Lecture 5's "no numbers, no rewrite" is the
  load-bearing claim. If the team doesn't have
  the numbers, the drill reveals the missing-
  evidence state — which *is* the correct
  input to the memo.
- **The appetite is bounded.** Lecture 5
  explicitly warns against "as long as it
  takes." Pick a concrete appetite — two
  weeks, six weeks, one quarter — and commit
  to the circuit-breaker.
- **Reference cto-curriculum mod-105** for
  cost-to-carry depth. Lecture 5 defers the
  measurement methodology to that curriculum;
  the exercise consumes the numbers rather
  than deriving them.
- **Use the Lecture 4 influence craft.** The
  conversation around the memo lands best
  with the "let me try to convince you"
  script, not with authority. The memo makes
  the case; the script delivers it.
- **Resist authority resolution.** The
  Lecture 5 anti-pattern #1 is *"CPO wins by
  rank"* or *"CTO wins by rank."* The memo's
  job is to replace both with evidence.

## The reviewer's memo

Half a page, written after the artifact bundle.
Answer:

- **If the eng lead reads this memo, which
  claim will they push back on hardest?** The
  cost-to-carry estimate? The appetite? The
  recommended move? What evidence would you
  bring to their pushback?
- **If the CEO reads this memo as a Lecture 1
  tie-breaker** (because you and the eng lead
  disagree on the recommended move), is the
  memo decidable? Does it name both proposed
  answers and the evidence on each side
  clearly enough for the CEO to decide?
- **Which of the six Lecture 5 failure modes
  does your current draft most risk?**
  Authority resolution, unbounded rewrite,
  silent debt acceptance, kill-as-taboo,
  refactor-in-place-as-slogan, second-system
  syndrome. Point at the sentence or omission.
- **The 6-months-later check.** If the
  recommended move is taken, what does
  success look like six months from now? What
  would signal the move was wrong? Both
  questions should be answerable from the
  memo, not from memory.

## Acceptance criteria

- Memo covers all seven sections including
  all four moves (kill explicitly named even
  when obviously wrong), the recommended move
  with evidence, the out-condition, and the
  specific named-person commitment.
- Cost-to-carry worksheet names a metric,
  estimate, estimation method, and error bar
  for all four cost categories; at least one
  row has real numbers.
- Appetite / fix / notification / refactor
  spec matches the recommended move (one of
  the four) and is specific enough that the
  team could start on Monday.
- The verdict line in the cost-to-carry
  worksheet is yes / no / unclear with a one-
  sentence reason.
- Every reference to
  [Lecture 5](../lectures/05-engineering-scope-conflict.md)
  cites the specific section rather than the
  lecture as a whole.
- Every reference to the cost-to-carry depth
  points at
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)
  mod-105 or equivalent engineering-depth
  reference.
- Reviewer's memo answers all four prompts.

## Common failure modes

- **Three moves considered, kill omitted.**
  Lecture 5's "kill is under-considered"
  warning applied to this memo. Fix: name
  kill even when obviously wrong; the
  discipline is in naming it.
- **No numbers in the cost-to-carry
  worksheet.** Lecture 5 is explicit — no
  numbers, no rewrite. Fix: either populate
  the worksheet with real-or-plausibly-
  sourced estimates with named error bars,
  or make the memo's conclusion "we need
  the numbers before we can decide."
- **Unbounded rewrite.** The recommended
  rewrite has no circuit-breaker, or the
  circuit-breaker is "we'll see how it
  goes." Fix: name the three outcomes
  explicitly, including the *stop* outcome
  as a design.
- **Ship-and-fix-later without the named
  fix.** The memo defaults to ship-and-fix-
  later without specifying what gets fixed,
  by whom, when. Fix: Lecture 5 §"Ship-and-
  fix-later is right when..." is the
  checklist; apply it.
- **Refactor-in-place as slogan.** The memo
  recommends refactor-in-place without
  naming specific structural improvements or
  a percentage commitment. Fix: Lecture 5's
  refactor-in-place rubric is explicit;
  apply it.
- **Memo is a position, not a decision
  package.** The memo argues for one move
  only, without surfacing the honest case
  for the alternatives. Fix: each of the
  four move paragraphs steel-mans the move,
  then the recommendation picks among them.
- **Missing out-condition.** The memo
  recommends a move without naming what
  triggers a re-visit. Fix: every
  recommended move has an out-condition —
  the circuit-breaker, the trigger-for-fix,
  the measurable-improvement-check, the
  kill-notification-window.

## Source alignment

The four-move framework and the cost-to-carry
discipline derive from
[Lecture 5](../lectures/05-engineering-scope-conflict.md).
The cost-to-carry measurement methodology is
[cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)
mod-105. The appetite / circuit-breaker vocabulary
is Ryan Singer, *Shape Up: Stop Running in Circles
and Ship Work That Matters*, Basecamp, 2019,
Chapters 3 and 14 —
[basecamp.com/shapeup](https://basecamp.com/shapeup).
The second-system / "plan to throw one away"
grounding is Fred Brooks, *The Mythical Man-Month*
(anniversary edition), Addison-Wesley, 1995 —
[informit.com](https://www.informit.com/store/mythical-man-month-the-essays-on-software-engineering-9780201835953).
The queue-competition framing for rewrites as
bets is
[mod-002](../../mod-002-opportunity-assessment-and-prioritization/README.md).
The CPO / CTO / CEO tie-breaker discipline when
this memo doesn't resolve the dispute is
[Lecture 1](../lectures/01-cpo-ceo-working-relationship.md#artifact-3--the-tie-breaker)
and the interpersonal craft of delivering it is
[Lecture 4](../lectures/04-influence-without-authority.md#the-let-me-try-to-convince-you-script).
