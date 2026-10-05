# Exercise 2 — Activation / retention / cohort analysis drill

**Time:** ~3 hours. **Deliverable:** one **analysis memo**
for the product's largest active segment — a defensible
**activation event**, an **N ≥ 12-period retention curve**
by cohort, a **NUX funnel step-by-step read**, and a
**feature-adoption-depth** cut on one feature — plus a
one-page diagnosis of what the regime is telling you to
work on next.

## Purpose

Run the six-instrument analytics regime from
[Lecture 2](../lectures/02-analytics-regime-beyond-pmf.md)
against a real segment. The point is not to *produce
charts* — the product-analytics tool produces charts. The
point is to **author definitions** the team will steer by
(what counts as activation, how retention is measured,
which cohort cuts matter) and to **read the instruments
together as a diagnosis**, not as four isolated numbers.

This exercise usually reveals that the north-star you
authored in
[Exercise 1](exercise-01-north-star-and-input-metric-authoring.md)
is not moving in the direction you assumed. That is the
exercise working, not failing.

## What you need before you start

- The metric taxonomy from
  [Exercise 1](exercise-01-north-star-and-input-metric-authoring.md).
  The analysis reads retention *of the north-star behavior*,
  not of any behavior; without the taxonomy, the retention
  question is ambiguous.
- **Access to real or plausible-synthetic event data.**
  Options, in preference order:
  1. The product's actual event stream, via a product
     analytics tool (Amplitude, Mixpanel, PostHog, Heap)
     or warehouse (BigQuery, Snowflake, Postgres).
  2. A **synthetic events CSV** of 90+ days you generate
     for a plausible product shape (a 100-line Python
     script that samples signups, activations, repeat
     actions, and churn gives you enough to practice
     against). Posting the generator script with the
     deliverable is a plus — the generator is where you
     exercise *definitional* discipline.
  3. The event dataset shipped with your analytics tool's
     tutorial (Amplitude's demo project, Mixpanel's
     "mp-template," PostHog's hogflix) — adequate for
     practice but note the fabrication in the memo.
- Enough SQL to run the queries from
  [Lecture 3 — The five SQL patterns](../lectures/03-analytics-stack-and-sql-against-events.md#the-five-sql-patterns)
  without help. If you don't have it, do
  [Lecture 3's inline SQL drill](../lectures/03-analytics-stack-and-sql-against-events.md#the-inline-sql-drill)
  first.

## What the analysis memo must contain

Six to eight pages, structured in the order below. Author
each section against the Lecture 2 instrument it names.

### 1. Segment definition (half page)

- **The segment**, named precisely — "US self-serve
  Growth-plan signups, Q2 2026 forward" is a segment;
  "all users" is not. State the dimensions you're cutting
  on (plan, geo, source, device, lifecycle) and why this
  segment is the one the roadmap is pointed at.
- **Segment size**, in users / teams / accounts at the
  time of the read. Any analysis of a segment smaller
  than ~500 units will be noisy; call this out if your
  real data is below that.
- **Why this segment and not another.** The CPO move: the
  largest segment is usually the right first read; a
  minority segment is worth analyzing when the strategy
  says so (mod-003), not reflexively.

### 2. Activation event, defined (one page)

Follow the seven-step authoring protocol from
[Lecture 2 — Instrument 2 — Activation](../lectures/02-analytics-regime-beyond-pmf.md#instrument-2--activation).

- **The activation event itself**, written as a specific
  AND-conjunction with a time window: *"invited ≥1
  teammate AND created ≥1 document AND returned on ≥1
  distinct day — all within 14 days of signup."* Not a
  single-event activation; most useful activation
  definitions are small conjunctions.
- **The retention gap** that justifies it: for the
  reference cohort, users who activated retain at X% at
  day 90, users who didn't retain at Y%. The *gap*
  (X − Y) is what makes activation predictive. If the
  gap is < 20 percentage points, the definition is weak;
  revise.
- **Validation on a fresh cohort.** Run the activated vs.
  non-activated retention check on a cohort *different*
  from the one you used to pick the definition. If the
  gap collapses, the definition over-fit; name the
  problem and the next iteration.
- **The window justification.** Why 7 / 14 / 30 days —
  this must match the product's natural use frequency
  per Lecture 2.
- **Known lies.** Which of the three Lecture 2 activation
  failure modes you considered (correlation-causation
  trap, window trap, definition drift) and how you
  handled each.

### 3. Retention curves by cohort (one to two pages)

Build the retention table from
[Lecture 3 — Pattern 3 — Cohort retention](../lectures/03-analytics-stack-and-sql-against-events.md#pattern-3--cohort-retention),
then chart it.

- **Minimum 12 periods of retention** per cohort (12
  weeks for a weekly-use product; 12 months for a
  monthly-use product). Pick the period that matches
  the product's natural cadence per Lecture 2.
- **At least four overlapping cohorts** on the same
  chart, so cohort-over-cohort movement is visible. A
  single-cohort retention line is unreadable.
- **One quantitative read of the asymptote** per
  cohort — the level the curve flattens to. If a cohort
  hasn't flattened yet, say so; don't extrapolate.
- **The three Lecture 2 questions, answered**:
  - Is the newest cohort's curve above or below older
    cohorts'?
  - Which segment's curve is highest, which is lowest?
  - What's the gap between behavioral retention and
    revenue retention? (If B2B — Instrument 6 below.)
- **Which retention variant you're using** (N-day,
  rolling N-day, unbounded, range) per
  [Lecture 2 — Practical variants](../lectures/02-analytics-regime-beyond-pmf.md#instrument-3--retention-curves-and-cohort-analysis).
  State it; defend it.
- **The three Lecture 2 retention lies, checked**:
  no blended retention line passed off as per-cohort;
  behavioral retention separated from billing
  retention; period matched to product cadence.

### 4. NUX funnel step-by-step (one page)

- **The onboarding funnel** from first landing / signup
  through the activation event, step by step, over the
  last 30 days of signups. Use
  [Lecture 3 — Pattern 2 — Funnel conversion](../lectures/03-analytics-stack-and-sql-against-events.md#pattern-2--funnel-conversion-ordered)
  for the query shape.
- **Denominators at every step.** The Lecture 2
  Instrument 1 point: a funnel without denominators is
  a story, not an analysis.
- **The largest-drop step**, identified. Lecture 2's
  rule-of-thumb thresholds: no single step should lose
  more than ~20% of the surviving population; no
  top-to-activation should lose more than ~60%.
- **Segmentation of the drop.** Is the drop uniform or
  concentrated in one source / browser / region /
  device?
- **Time-in-step**, for users who did convert. A step
  where successful users spent > 5 minutes is a UX
  problem, not a motivation problem.
- **One qualitative read.** If you have session
  recordings or support tickets, cite one specific
  observation that explains the drop at the largest step.
  If you don't, name what you would ask the data team
  for.

### 5. Feature-adoption depth on one feature (one page)

Pick one feature — ideally one the roadmap is considering
investing in, or one Exercise 3 might A/B-test. Compute
all four Lecture 2 depth metrics:

- **Adoption breadth (D0).** % of segment-active users
  who used the feature at least once.
- **Adoption stickiness.** DAU/MAU of the *feature*,
  conditional on having used it in the last month.
- **Adoption depth.** For users who used it more than
  once, median uses per week / month.
- **Adoption impact (retention lift).** Do feature
  adopters retain better than non-adopters? State the
  gap *and* name the Lecture 2 correlation-causation
  caveat — this is a correlation, not a causal effect;
  the A/B or quasi-experiment from
  [Lecture 4](../lectures/04-experimentation-at-pre-seed-to-series-a.md)
  or
  [Lecture 5](../lectures/05-quasi-experimental-methods-when-ab-fails.md)
  is the causal read.

Use [Lecture 3 — Pattern 4 — Feature adoption
depth](../lectures/03-analytics-stack-and-sql-against-events.md#pattern-4--feature-adoption-depth)
for the query shape.

**Classify the feature** per Lecture 2:
- *demo feature* (high breadth, low depth) — people
  tried it, no one adopted;
- *niche feature* (low breadth, high depth) — small
  group loves it; roadmap question is promote or let-be;
- *core feature* (high breadth, high depth) — the
  product's working surface;
- *dead feature* (low breadth, low depth) — kill it or
  rebuild.

### 6. Revenue-per-account cohort — B2B only (half page)

If your product is B2B, add a **revenue-per-account cohort
curve** per
[Lecture 2 — Instrument 6](../lectures/02-analytics-regime-beyond-pmf.md#instrument-6--revenue-per-account-cohorts-for-b2b).
Group accounts by month of first paid subscription; plot
*cohort revenue in month N since first paid*. State
whether each cohort is flat (no expansion), rising
(expansion), or declining (contraction). If you can
compute **net revenue retention**, do so.

Skip this section for a pure consumer product; note the
skip and why.

### 7. Diagnosis — reading the instruments together (one page)

Walk the five-step diagnosis regime from
[Lecture 2 — Reading the instruments together](../lectures/02-analytics-regime-beyond-pmf.md#reading-the-instruments-together--a-diagnosis-regime):

1. Which direction has the **north-star** moved
   (reference the Exercise 1 taxonomy)?
2. Which **input metric** moved to produce the
   north-star move — or, if no input moved, where
   the north-star move came from?
3. For the moving input, which **funnel step** is
   the change concentrated in?
4. For the moving funnel step, which **segment**?
5. For the moving segment, did the change **stick**
   in the retention / cohort curve? Guardrails
   intact?

End the diagnosis with **one concrete recommendation**
for what Exercise 3 (the A/B) should test, or — if the
data says A/B isn't the right instrument —
[Exercise 4 (the eval suite)](exercise-04-llm-eval-suite-authoring-for-one-agent.md)
or
[Lecture 5's quasi-experimental fallback](../lectures/05-quasi-experimental-methods-when-ab-fails.md).

## Starter guidance

- **Define activation before measuring retention.** The
  retention curve of "users who activated" and "users who
  didn't" is the one that matters; without an activation
  definition, retention aggregates two populations and
  the curve lies.
- **Chart per-cohort retention, not blended.** Blended
  retention is the single most common lie in this
  module. If the chart has one line, it's wrong.
- **Match the period to the cadence.** Weekly retention
  on a monthly-use product shows fake churn; monthly
  retention on a daily-use product masks real churn.
  Lecture 2 is emphatic.
- **Behavioral retention first, billing retention
  separately.** Billing retention can hide a product in
  the terminal phase of use decline; show both and
  flag the divergence.
- **For B2B, read account-scope *and* user-scope.** User
  DAU can thrive inside accounts that are about to
  churn, and vice versa. Both are needed.
- **If you only have 100 users of real data**, say so
  and run the analysis anyway — the practice is the
  point. Add a sensitivity note on where the sample
  bites.

## Acceptance criteria

- The **segment** is named precisely (dimensions, size,
  rationale).
- The **activation event** is stated as an
  AND-conjunction with a time window, backed by a
  retention gap ≥ 20 pp on the reference cohort, and
  **validated on a fresh cohort**.
- The **retention table** covers ≥ 4 cohorts × ≥ 12
  periods, per-cohort (not blended), with the retention
  variant named and defended; the three Lecture 2 lies
  are each checked.
- The **NUX funnel** is step-by-step with denominators,
  largest-drop step identified, segmentation of the drop,
  and one qualitative read.
- The **feature-adoption-depth cut** computes all four
  Lecture 2 metrics (breadth, stickiness, depth, impact)
  and classifies the feature into one of the four
  patterns.
- For B2B: the **revenue-per-account cohort curve** is
  present; NRR is computed if possible.
- The **diagnosis** walks the five-step regime end to
  end and ends in one concrete next-exercise
  recommendation.

## Common failure modes

- **Blended-retention curve.** A single retention line
  that averages all cohorts. Delete and re-run per-cohort.
- **Activation-as-signup.** "Activated = created an
  account" is not activation. Activation is the
  behavior that *predicts long-term retention*; if
  signup doesn't predict it (and it rarely does), signup
  isn't activation.
- **Over-fit activation definition.** The definition was
  picked on cohort A and never validated on cohort B;
  the gap collapses in production. The seven-step
  Lecture 2 protocol has the fresh-cohort check for a
  reason.
- **Funnel without denominators.** "100 signups, 60
  activated, 20 shared" with no step-conversion rates.
  The pattern you want is the step rate (60/100 = 60%,
  20/60 = 33%) and the Lecture 2 rules of thumb.
- **Breadth-only feature adoption.** Reporting breadth
  without depth. A feature with 90% breadth and 1%
  stickiness is a *demo* feature; breadth alone would
  call it a win.
- **B2B taxonomized at the user scope.** Account-level
  churn hiding behind user-level activity. Lecture 2
  Instrument 6 is why.
- **Correlation sold as causation.** "Users who used
  feature X retain 2× better" treated as "feature X
  caused the retention lift." It's a correlation; the
  causal read is Lecture 4 or Lecture 5.
- **Diagnosis as narrative.** The write-up tells a
  story about why the metric moved without walking the
  five-step regime. The regime is what distinguishes
  diagnosis from narration.

## Source alignment

The activation / retention / cohort / NUX / feature-depth
instruments derive from the Reforge Growth Series
([reforge.com/programs](https://www.reforge.com/programs)),
the Amplitude product-analytics docs — specifically the
retention-analysis guide
([amplitude.com/docs/analytics/charts/retention-analysis](https://amplitude.com/docs/analytics/charts/retention-analysis/retention-analysis-overview))
— and Mixpanel's analogous docs
([mixpanel.com/learn/retention-cohort-analysis](https://mixpanel.com/learn/retention-cohort-analysis/)).
The Facebook *seven-friends-in-ten-days* activation
example is cited in Andrew Chen, *The Cold Start Problem*,
Harper Business, 2021 —
[andrewchen.com/the-cold-start-problem-book](https://andrewchen.com/the-cold-start-problem-book/).
The B2B net-revenue-retention framing derives from
Bessemer Venture Partners' *State of the Cloud* —
[bvp.com/atlas](https://www.bvp.com/atlas) — and the
SaaStr archive at
[saastr.com](https://www.saastr.com/).
