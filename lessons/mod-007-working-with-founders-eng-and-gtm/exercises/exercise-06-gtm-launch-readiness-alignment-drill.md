# Exercise 6 — GTM launch-readiness alignment drill

**Time:** ~3 hours. **Deliverable:** one six-
function launch-readiness checklist, one go /
no-go meeting plan, one launch-day rhythm plan,
one rollback-and-escalation spec, and a
reviewer's memo — for a real (or plausible)
launch.

## Purpose

Author the full founding-PM launch-readiness
bundle from
[Lecture 6](../lectures/06-gtm-launch-readiness-coordination.md)
for one specific launch. The deliverable is
the exact set of artifacts the CPO owns at a
pre-seed / seed company where there is no
launch manager, no head of marketing, and no
one else running the coordination layer.

The target failure modes this exercise drills
against are the Lecture 6 §"Common failure
modes" patterns — the "we told support in
Slack" launch, the "sales sold it before it
shipped" launch, the "no rollback plan"
launch, and especially the "day-of surprise"
launch where the CEO posted about the feature
on Twitter before the readiness was there. The
counter-move for all of them is the specific,
written readiness coordination this exercise
produces.

## Choosing the launch

Pick one real or plausible launch that qualifies
under
[Lecture 6 §"What 'launch' means at founding-team scale"](../lectures/06-gtm-launch-readiness-coordination.md#what-launch-means-at-founding-team-scale)
— a new customer-facing surface, a pricing /
packaging change, a workflow-breaking change, a
GTM-visible bet, or a feature attached to a
public commitment. In order of preference:

1. **A launch you're actively coordinating.**
   Highest-value drill; the bundle is the real
   artifact.
2. **A launch from your last role**, or one
   you watched a founding team run end-to-end.
3. **A plausible synthetic.** If you need to
   fabricate, pick one of these shapes: a new
   AI feature behind a feature flag with an
   eval gate; a repackaging of the free tier
   (per mod-006); a workflow-breaking change
   to an onboarding flow; a new SKU targeting
   the enterprise segment. Write a one-
   paragraph setup: product, launch surface,
   target customer, approximate team size,
   current GTM shape (self-serve / sales-led /
   hybrid), and the public commitment (if any)
   attached.

Whichever you pick, name the launch date
specifically — real date if real, plausible
date if synthetic. The checklist's deadlines
anchor to this date.

## What the artifact bundle must contain

Roughly 5–6 pages. The checklist is the
primary artifact; the rest wrap around it.

### 1. The six-function readiness checklist (2–3 pages)

The exact shape from
[Lecture 6 §"The launch-readiness checklist — six functions"](../lectures/06-gtm-launch-readiness-coordination.md#the-launch-readiness-checklist--six-functions).
For each of the six functions — product,
marketing, sales, CS, support, telemetry — a
checklist with:

- **Each artifact** named explicitly (per the
  Lecture 6 bullet lists).
- **The owner.** A specific person's name
  (or role if synthetic — "head of CS").
- **The due date** relative to launch (T-14,
  T-7, T-2, T-0).
- **The current status** (ready / in-progress
  / not-started / blocked).
- **The specific gap** if not ready. What's
  missing and what would close it.

Shape (per function):

**Product.** Feature complete against PRD
(including the Lecture 2 under-specification
checklist); eval regime passed if AI-substrate
(threshold met on labeled dataset per Lecture
3 §"Layer 4"); telemetry live; rollout
mechanism chosen; rollback plan drafted.

**Marketing.** Positioning statement (per
April Dunford, *Obviously Awesome* —
[aprildunford.com/obviously-awesome](https://www.aprildunford.com/obviously-awesome/));
customer-facing announcement drafted; external
channel work scheduled; pricing-page update
if the launch changes the SKU ladder.

**Sales.** Pitch update; competitive
positioning update; pricing / discount bounds;
FAQ; 30-minute training session with the CPO
present.

**Customer Success.** Health-signal update;
onboarding update; expansion target-account
list; training session.

**Support.** FAQ; known-issues list;
escalation path (named on-call engineer, named
channel, response-time expectation); expected
volume spike with staffing plan.

**Telemetry.** Launch dashboard (adoption,
activation, retention, error rate, latency,
cost for AI-substrate); alert thresholds;
24h / 72h / 7d check-in cadence.

### 2. The go / no-go meeting plan (half page)

The Lecture 6 §"The go / no-go meeting" shape:

- **Attendees.** CPO, CTO / eng lead, GTM lead
  (named).
- **When.** 24–48 hours before launch.
- **Duration.** 30 minutes.
- **The three questions in order:** checklist
  ready, risks named with mitigations, do we
  go.
- **The written go / no-go note.** Where it's
  logged, what it contains.
- **The "don't ship" script.** The sentence(s)
  the CPO would use to propose a specific
  delay — small, specific, days-not-quarters.
  Per Lecture 6 §"The 'don't ship' muscle."
  Write it in the voice you'd actually use.
- **The escalation to the CEO.** If the CPO
  wants to delay and the CEO wants to ship,
  the Lecture 1 tie-breaker memo path applies.
  Name the trigger that escalates and sketch
  the one-page memo shape.

### 3. The launch-day rhythm plan (half page)

The Lecture 6 §"The launch-day rhythm" five
beats, each specific to this launch:

- **T-2 hours.** The pre-launch check — what
  specifically gets confirmed, by whom.
- **T-0.** The rollout steps in order — who
  flips the flag, who publishes the
  announcement, who updates the pricing page,
  who sends the internal Slack notification.
- **First hour.** What the CPO watches on the
  launch dashboard. The specific alert
  thresholds that trigger a rollback decision.
- **24 / 72 hours.** The 15-minute reviews.
  Attendees, agenda, what triggers an action
  item.
- **7 days.** The written retrospective — the
  specific template, who drafts, who reads.

### 4. The rollback-and-escalation spec (half page)

- **The rollback plan.** Named engineer, named
  steps, target rollback time. The
  Lecture 6 §"Product" rollback item made
  concrete.
- **The on-call rotation.** Who's on-call for
  the first 72 hours. Where support escalates.
- **The known-issues register.** The specific
  list of things we know aren't perfect at
  launch and the workaround we've briefed
  support on. Per Lecture 6's "nothing burns
  support faster than a known issue that
  support finds out about from customers."
- **The press / exec-escalation script.** If a
  prominent customer, press contact, or board
  member hits the broken state, what's the
  response path and who's on it.

## Starter guidance

- **Treat the launch date as fixed-until-it-
  isn't.** The checklist and the T-2 / T-0
  rhythm anchor to a specific date; the "don't
  ship" muscle is the only legitimate way to
  move it. Lecture 6's point about
  calcified-commitment deadlines is the
  framing.
- **Name owners, not teams.** "Head of CS"
  works; "the CS team" is where readiness
  gaps hide. The checklist's leverage comes
  from "Priya owns the training session,
  due T-5" rather than "someone on CS owns
  training."
- **Pre-work the sales training.** Lecture 6
  calls out the "but we sent an email"
  failure explicitly. A 30-minute live
  session with the CPO on it is non-
  optional for strategic-bet launches.
- **Draft the known-issues list honestly.**
  Launches ship with imperfections. The
  known-issues list is where the honest
  version lives. Support reads it before
  launch; the first support ticket referencing
  a known issue gets a workaround, not a
  firefight.
- **Instrument before you ship.** The launch
  dashboard existing *before* T-0 is the
  Lecture 6 fix for the "no launch
  dashboard" failure mode. If telemetry
  isn't ready at T-7, the correct move is
  often to delay, not to launch and
  instrument later.
- **The go / no-go is consensus.** Three
  people, three votes, any no blocks the
  go. Scripting the "don't ship" muscle in
  advance is what makes a no actually
  happen when it needs to.
- **If the launch has a public commitment,
  the Lecture 1 external-communication row
  on the decision-rights map is live.** Make
  sure the public commitment landed with
  CPO input before it was made; if it
  didn't, document the pattern for the
  Lecture 1 escalation path.

## The reviewer's memo

Half a page, written after the artifact bundle.
Answer:

- **Which of the seven Lecture 6 failure
  modes is this launch most at risk of?**
  Named specifically. Point at the checklist
  item or omission that produces the risk.
- **The hardest row on the checklist.** Which
  function's artifacts are least likely to
  be ready by T-2? Why? What would close it?
- **The "don't ship" scenario.** If you had
  to delay, which specific gap would
  justify it, and what's the delay length
  you'd propose? Day-sized? Week-sized?
  Lecture 6 is explicit about small-and-
  specific vs. indefinite.
- **The CEO disagreement scenario.** If the
  CEO wants to ship over your "don't ship"
  objection, the Lecture 1 tie-breaker
  applies. Sketch the one-page memo you'd
  write — one paragraph, not the full memo.
- **The 7-day retro loop.** What's the one
  question the retro should answer that
  wouldn't be visible from the launch
  dashboard alone?

## Acceptance criteria

- Six-function checklist covers all six
  functions, every artifact from Lecture 6
  per function, with named owner, due date,
  current status, and the specific gap for
  anything not ready.
- Go / no-go plan names attendees, duration,
  the three questions, the written note, the
  "don't ship" script in the CPO's voice,
  and the escalation-to-CEO trigger.
- Launch-day rhythm plan has all five beats
  (T-2, T-0, first hour, 24 / 72 hours, 7
  days) with specific actions and owners.
- Rollback-and-escalation spec names the
  rollback plan, on-call rotation, known-
  issues register, and press / exec-
  escalation script.
- Every reference to
  [Lecture 6](../lectures/06-gtm-launch-readiness-coordination.md)
  cites the specific section rather than the
  lecture as a whole.
- Every reference to the GTM operational
  depth defers appropriately to
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum).
- Reviewer's memo answers all five prompts.

## Common failure modes

- **"We told support in Slack" readiness.**
  The support row has an FAQ and a known-
  issues list that are "to be drafted" at
  T-2. Fix: pull them forward to T-7 and
  require the training session.
- **No "don't ship" script.** The go / no-go
  plan lists the three questions but doesn't
  give the CPO the specific sentence they'd
  use to propose a delay. Fix: write the
  sentence in the voice you'd use. The
  Lecture 6 §"The 'don't ship' muscle"
  example is the shape.
- **Rollout mechanism unnamed.** The
  checklist marks rollout as "ready"
  without naming whether it's a feature
  flag, staged rollout, cohort split, or
  100%. Fix: name the mechanism per the
  mod-005 experiment discipline where
  applicable.
- **No eval gate for AI features.** For an
  AI-substrate launch, the eval regime
  passing on the labeled dataset is the
  Lecture 3 §"Layer 4" gate. Fix: the
  product-row has an "eval threshold met"
  line that cites the specific pass number.
- **Launch dashboard is launch-day work.**
  The dashboard goes live T-0 rather than
  T-7. Fix: dashboard at T-7, baseline the
  pre-launch numbers so the launch delta is
  visible.
- **Day-of surprise.** The CEO posts about
  the launch before the readiness checklist
  is complete. Lecture 6 names this
  specifically; the Lecture 1 external-
  communication row prevents it. Fix: the
  readiness bundle includes "CEO has agreed
  to no external posts before go / no-go
  passes."
- **Owner-less items.** The checklist has
  rows without a named owner. Fix: every
  row has a person, not a team.
- **Missing retro.** The 7-day retro is
  mentioned but not scheduled, or scheduled
  without a template. Fix: the Lecture 6
  retro feeds the next launch's checklist;
  the loop only works if the retro happens.

## Source alignment

The six-function readiness framework and the
go / no-go shape derive from
[Lecture 6](../lectures/06-gtm-launch-readiness-coordination.md).
The positioning vocabulary for the marketing
row is April Dunford, *Obviously Awesome: How
to Nail Product Positioning*, Ambient Press,
2019 —
[aprildunford.com/obviously-awesome](https://www.aprildunford.com/obviously-awesome/).
The practitioner reference for the smaller-
startup launch shape is Jason Cohen's writing
on A Smart Bear —
[longform.asmartbear.com](https://longform.asmartbear.com/).
The eval-gate discipline for AI feature
launches is
[Lecture 3 §"Layer 4"](../lectures/03-ai-system-architecture-for-the-founding-cpo.md#layer-4--evaluation)
and
[mod-005 Lecture 6](../../mod-005-metrics-experimentation-and-ai-evals/lectures/06-eval-driven-decisions-for-llm-products.md).
The experiment / rollout vocabulary is
[mod-005 Lecture 4](../../mod-005-metrics-experimentation-and-ai-evals/README.md).
The pricing-page update row anchors to
[mod-006 Lecture 1](../../mod-006-pricing-packaging-and-monetization/lectures/01-pricing-as-a-product-surface.md).
The deep GTM craft this exercise coordinates
with but does not teach is
[startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum)
(level 30). The CPO / CEO tie-breaker
discipline for the "don't ship" escalation
is
[Lecture 1 §"Artifact 3 — The tie-breaker"](../lectures/01-cpo-ceo-working-relationship.md#artifact-3--the-tie-breaker).
