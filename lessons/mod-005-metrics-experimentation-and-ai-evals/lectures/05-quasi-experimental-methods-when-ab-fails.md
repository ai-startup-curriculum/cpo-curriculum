# Lecture 5 — When A/B fails: holdouts, diff-in-diff, interrupted-time-series

## The setup

Lecture 4's decision tree ended on a specific failure
mode: you computed the MDE, the required sample is
out of reach in a reasonable window, and running the
A/B anyway would be four weeks of noise around zero.
This is not an edge case at pre-seed → Series-A. It is
the *modal* case. Most product changes a founding CPO
wants to ship cannot be evaluated by a well-powered
per-user A/B in a useful window.

The response is not to give up on causal inference. It
is to reach for three families of design the academic
econometrics literature (Angrist & Pischke's *Mostly
Harmless Econometrics*; Athey and Imbens on modern
causal-inference practice) has developed for exactly
this: **holdout / geo splits**, **difference-in-
differences (DiD)**, and **interrupted time-series
(ITS)**. Each trades experimental purity for
statistical power against the whole population, and
each has a specific set of assumptions that fail in
specific ways.

This lecture teaches the shapes, the assumptions each
requires, when to prefer which, and how to defend the
result of each against the "but did the treatment
really cause it?" pushback that will come from every
technical founder-CEO who reads a Kohavi book excerpt
and asks why you didn't run an A/B.

## Design 1 — Holdout / geo split

A **holdout** is the simplest quasi-experimental design:
ship the change to 90–95% of the population and hold
5–10% back as an unchanged control. Read the aggregate
metric difference between the two groups over a longer
window than an A/B would use.

The most common variant, especially for products with
long-cycle metrics or heavy network effects, is a
**geo split**: ship in the US, hold Canada as control
(or ship to the West Coast, hold the East). Countries
or regions are quasi-random assignments in the sense
that their pre-treatment metric levels can be modeled
and compared.

**When holdouts work well:**

- The metric is aggregate (retention, revenue,
  net-promoter score) and slow-moving.
- The change is expensive or slow to un-ship — a
  pricing change, a re-architecture, a rebrand — so
  A/B at the user level is infeasible.
- Network effects exist and per-user randomization
  contaminates the control (marketplace, social,
  messaging products).

**When holdouts fail:**

- The control group is small relative to the treatment
  and picks up too much noise. A 5% holdout of a
  10,000-user product is 500 users; the aggregate is
  noisy.
- Selection effects: US vs. Canada differ on more than
  the treatment — the observed difference conflates
  the treatment with the underlying geographic /
  demographic differences.
- The holdout is time-bounded and the metric doesn't
  move in the window.

**How to strengthen the design:**

- **Match the holdout on pre-period metrics.** Pick a
  holdout region whose pre-treatment metric level
  matches the treatment region. Uber's classic paper
  on switchback experiments for marketplace products
  is worth reading here
  ([Chamandy, "Experimentation in a Ridesharing
  Marketplace," Lyft engineering blog, 2016](https://eng.lyft.com/experimentation-in-a-ridesharing-marketplace-b39db027a66e)).
- **Report the pre-period parallel-trends check.** If
  the two groups were moving on the same trend
  pre-launch and the treatment group deviated
  post-launch while the control kept trending, that
  is causal evidence — which shades directly into
  diff-in-diff.

## Design 2 — Difference-in-differences (DiD)

**Difference-in-differences** is the workhorse of
quasi-experimental analysis. The idea, in one
sentence: measure the *change* in the metric for the
treatment group over time, subtract the *change* in
the metric for the control group over the same time.
The subtraction cancels out the parts of the change
that are shared (seasonality, macro trends), leaving
the treatment-specific effect.

Formally, for a treated group *T* and a control group
*C*, and two periods *pre* and *post*:

```
DiD = (E[Y_T,post] - E[Y_T,pre]) - (E[Y_C,post] - E[Y_C,pre])
```

The estimate is the treatment effect — under the
critical assumption that, absent the treatment, both
groups would have moved on parallel trends.

The Angrist & Pischke textbook (Chapter 5) is the
canonical reference for the design and its assumptions
([Angrist & Pischke, *Mostly Harmless Econometrics*,
Princeton, 2009, Chapter 5](https://www.mostlyharmlesseconometrics.com/)).
Card and Krueger's *Myth and Measurement* (the New
Jersey minimum-wage study) is the canonical worked
example
([Card & Krueger, *Myth and Measurement*, Princeton,
1997](https://press.princeton.edu/books/paperback/9780691048239/myth-and-measurement)).

**When DiD works well for a founding CPO:**

- The product has multiple segments, geos, or plan
  tiers that can serve as parallel treatment and
  control groups.
- The change can be rolled out to one segment at a
  time (feature-flagged at the account level, say),
  with a natural comparison group in a similar
  segment that didn't receive it yet.
- You have pre-launch data going back at least as long
  as the post-launch window (needed to check parallel
  trends).

**When DiD fails:**

- The **parallel-trends assumption** is violated:
  treated and control groups were on divergent
  pre-trends, so the observed post-treatment
  divergence would have happened anyway.
- **Anticipation effects:** the treated group behaves
  differently *before* the treatment because they
  knew it was coming (early access, pre-launch
  announcement).
- **Confounding time-shocks:** something else happened
  to the treated group in the post-period (a
  competing launch, a marketing push, a segment-
  specific outage).

**How to strengthen the design:**

- **Plot the parallel-trends check.** Chart the metric
  for treatment and control across the full pre-period
  plus the post-period. If the trends look parallel
  pre-launch and diverge post-launch, the DiD is
  credible.
- **Use multiple pre-periods.** DiD with a single pre
  and post is fragile; DiD with N pre-periods and M
  post-periods (a "two-way fixed effects" regression)
  is more robust.
- **Run a "placebo test."** Estimate DiD on a pre-
  treatment window where no treatment happened. If
  you find a spurious effect, the design is
  confounded.

**A concrete worked shape:**

> You rolled out the annual-pricing toggle to accounts
> in the "Growth" plan tier on August 1. You did not
> roll it out to "Starter" or "Enterprise" tiers.
> The metric of interest is *paid-to-annual
> conversion rate*, monthly.
>
> - Growth-tier baseline (July): 12% of new signups
>   go annual.
> - Growth-tier post (August): 22% of new signups go
>   annual.
> - Starter-tier baseline (July): 8%.
> - Starter-tier post (August): 10% (general uplift
>   from a marketing push in August).
>
> Naïve pre/post: +10 pp for Growth. Overstated,
> because the marketing push also affected them.
>
> DiD: (22 − 12) − (10 − 8) = 10 − 2 = **+8 pp
> attributed to the annual toggle**, absent the
> marketing-push effect.

The DiD estimate is 8 pp, not 10 pp — a 20%
correction for the shared time effect.

## Design 3 — Interrupted time-series (ITS)

**Interrupted time-series** is for the case where you
have *no control group at all*, only the treatment
population's own history. You model the counterfactual
— what would have happened without the treatment — as
the pre-treatment trend extrapolated forward, and
estimate the treatment effect as the deviation from
that trend after the intervention.

Formally, fit a regression on the pre-treatment data
(often with time and seasonality terms) and forecast
the post-period; the deviation of actuals from forecast
is the effect. Bayesian structural time-series (Google's
*CausalImpact* R package) is the canonical
implementation
([Brodersen et al., "Inferring causal impact using
Bayesian structural time-series models," 2015 —
[research.google.com/pubs/pub41854](https://research.google.com/pubs/pub41854.html);
CausalImpact package at
[google.github.io/CausalImpact](https://google.github.io/CausalImpact/)]).

**When ITS works well for a founding CPO:**

- You shipped a change to *everyone* — a pricing move,
  a rebrand, a global config change — and no control
  group exists.
- You have a long pre-period (ideally 6+ months) of
  stable-shape metrics.
- The metric has a clean trend and seasonality that
  the model can capture.

**When ITS fails:**

- **Concurrent confounds:** something else happened at
  the same time as the intervention (a marketing
  launch, a competitor collapse, a macro event) that
  affected the same metric.
- **Regime change:** the pre-period trend is not a
  good model for the post-period counterfactual
  because the underlying dynamics changed.
- **Short pre-period:** less than 2–3 seasonality
  cycles gives the model too little to fit against.

**How to strengthen the design:**

- **Include external controls in the model** (a
  competitor's search volume, weather, macro
  indicators) if you can identify variables that
  correlate with the metric but are not affected by
  the treatment. Adding them turns ITS into "ITS with
  covariates" (a synthetic-control-style design).
- **Show the pre-period model fit.** If the model
  cannot recover a held-out pre-period cleanly, its
  forecast for the post-period is not trustworthy.
- **Use *CausalImpact* or a peer package.** Don't
  hand-roll the statistics; the tooling handles
  Bayesian intervals, structural components, and
  covariate inclusion in a way that is much less
  error-prone than a linear regression.

## Choosing between the three

A decision tree the founding CPO can run in ten
seconds:

1. **Do you have a plausible per-user random
   assignment and enough traffic for a well-powered
   A/B in a useful window?** → **A/B** (Lecture 4).
2. **Not per-user, but you can hold back a segment
   (geo, plan, cohort) as an unchanged control?** →
   **Holdout / DiD.** Prefer DiD if you have
   pre-period data on both.
3. **No holdout possible — the change ships to
   everyone — but you have a stable pre-period
   trend?** → **ITS**, ideally with covariates.
4. **None of the above (no traffic, no control, no
   stable pre-period)?** → **Pre-registered
   ship-and-observe** with named leading indicators
   and a follow-up read in N weeks, treated as a
   *bet* not a *test*.

A useful diagnostic to add to the decision: **the
strongest quasi-experimental design is the one whose
assumptions your product actually satisfies.** DiD with
a violated parallel-trends assumption is *worse* than
an admitted ship-and-observe with named signals,
because the DiD carries the appearance of causal
inference without the substance.

## Novelty vs. sustained effects — the horizon question

All three quasi-experimental designs have to reckon
with the horizon on which the effect is measured.
Short-horizon reads (1–2 weeks) capture novelty; long-
horizon reads (2–6 months) capture sustained effects.
The two often diverge — a change with a strong 2-week
lift and a flat 3-month sustained effect is a design
that ships and then reverses.

The founding-CPO discipline: pre-register *both* the
short-horizon and long-horizon reads. Ship on the
short-horizon signal; commit to a follow-up read at
the long-horizon and un-ship if the sustained effect
is null or negative. This is the equivalent of the
"iterate if directionally right, kill if flat" rule
from Lecture 4, extended to non-experimental designs.

## Network effects and the interference problem

For marketplace, messaging, and social products, the
core A/B assumption — that treatment and control
groups do not affect each other — is violated by
design. A treated user who messages a control user
changes the control user's experience; the observed
effect is contaminated.

Two responses:

- **Cluster-randomization.** Assign at the level of
  the smallest group whose members interact — a
  workspace, a city, a friend group. Instead of
  randomizing users, randomize the *cluster*. Reduces
  interference at the cost of much smaller effective
  sample size (n = number of clusters, not users).
- **Switchback / time-based randomization.** For
  time-sliced marketplaces (rideshare, food
  delivery), alternate the treatment on and off
  across time windows. Every user experiences both;
  the effect is the difference between on-windows and
  off-windows. Lyft and Uber both published on this
  ([Chamandy, Lyft, 2016](https://eng.lyft.com/experimentation-in-a-ridesharing-marketplace-b39db027a66e);
  [Uber, "How Uber Experiments," 2022](https://www.uber.com/blog/experimentation-platform/)).

For most CPO-scope products, cluster-randomization at
the workspace level is the simpler solution and worth
knowing by name.

## Post-launch monitoring as a first-class discipline

None of the three quasi-experimental designs — nor
even a well-powered A/B — replaces the discipline of
**reading the metrics for weeks after launch**.
Kohavi et al. Chapter 4 makes this point emphatically:
even in an industrial-scale experimentation program,
some effects only become visible after 30 or 60 days
of usage, and a launch decision is a *bet* on the
short-horizon read that must be revisited on the
long-horizon read
([Kohavi, Tang & Xu, Chapter 4](https://experimentguide.com/)).

The founding-CPO version: every launch has a
pre-registered *N-week follow-up* baked into the
brief. If the follow-up read shows the effect
reversed, the change is un-shipped (or a corrective
change is queued). This is where the
retention-and-cohort work from Lecture 2 becomes the
authoritative read, and the experiment result becomes
the *initial estimate* rather than the final call.

## The credibility ladder — how to defend a
quasi-experimental result

A useful hierarchy for how *credible* a causal claim
is, from strongest to weakest:

1. **Randomized A/B with well-powered sample and no
   guardrail regression.** The gold standard.
2. **Cluster-randomized A/B** where the cluster is
   the natural unit of interaction (workspace, city).
3. **Holdout with matched pre-trends and pre-registered
   read.** Almost as credible as A/B for aggregate
   metrics.
4. **DiD with N pre-periods, parallel-trends check,
   and placebo test passed.**
5. **ITS with long pre-period, external covariates,
   and clean model fit.**
6. **Pre-registered ship-and-observe with named
   leading and lagging indicators.** Weakest, but
   still stronger than "we shipped and it feels
   better."
7. **Post-hoc storytelling** — looking at the numbers
   after launch and constructing a narrative. Not
   causal inference; a common founding-team failure
   mode dressed as one.

The founding-CPO discipline is to know *which rung*
your claim is on and to say so. A DiD claim reported
as if it were an A/B is a credibility loss the first
time a skeptic checks the parallel-trends assumption.

## What the CPO does personally

- **Chooses the design.** The decision tree above is
  a CPO call; the data team can implement.
- **Names the assumptions the design requires.** The
  parallel-trends assumption for DiD, the stable-
  pre-period assumption for ITS. Named in the brief.
- **Runs the assumption checks (or asks for them).**
  Parallel-trends plot, placebo test, held-out
  pre-period fit.
- **States the credibility rung in the write-up.**
  Not "we found +8pp"; rather "we found +8pp under
  a DiD design whose parallel-trends assumption held
  in this pre-period chart."

## What the CPO consumes

- The analytics implementation (event capture,
  segment tagging) — Lecture 3.
- The statistical tooling (CausalImpact, dowhy, dbt +
  bespoke SQL, or the analytics platform's
  quasi-experimental features) — owned by data /
  analytics-eng.
- The pre-period historical data — owned by data.

## Boundaries this lecture keeps

- **A/B experimentation** is
  [Lecture 4](04-experimentation-at-pre-seed-to-series-a.md);
  this lecture is what to do *when A/B is not
  feasible*.
- **Eval-based decisions for AI-substrate features**
  are [Lecture 6](06-eval-driven-decisions-for-llm-products.md);
  eval suites are the AI-native analogue of these
  quasi-experimental designs — the *replacement*
  for A/B on stochastic outputs, not a supplement.
- **Deep causal inference** — synthetic-control
  methods, regression discontinuity, instrumental
  variables — is out of scope; the references in
  [resources.md](../resources.md) are the deeper
  reads. A CPO at pre-seed / seed does not run these;
  a data scientist at Series-C might.
- **Marketplace / network-effect experimentation
  craft at depth** — switchback design theory,
  clustered-randomization variance corrections — is
  owned by the marketplace-specific playbooks (see
  the Lyft / Uber references cited above).

## Takeaways

- **A/B is often infeasible** at founding-CPO
  traffic; the response is not to give up on causal
  inference but to reach for the three
  quasi-experimental families.
- **Holdouts** are the simplest — ship to most, hold
  a small unchanged control, read the aggregate
  difference. Good for slow-moving metrics and
  network-effect products.
- **Difference-in-differences** is the workhorse —
  compare the *change* in the treated group's metric
  against the *change* in the control's. Requires
  parallel pre-trends.
- **Interrupted time-series** is the fallback when
  no control exists — model the counterfactual as
  the pre-period trend, estimate the effect as the
  deviation. Use *CausalImpact* or an equivalent.
- **The credibility ladder** ranges from randomized
  A/B down to post-hoc storytelling; a founding CPO
  states which rung a claim is on and does not
  dress DiD as if it were A/B.
- **Post-launch monitoring** is a discipline in its
  own right — every launch has a pre-registered
  N-week follow-up read, and the launch decision is
  a *bet* on the short-horizon signal.

Lecture 6 turns to the AI-substrate case, where the
*decision surface* is not an experiment at all but an
**eval suite** — and where most of the quasi-
experimental designs here get replaced by a
labeled-dataset regime.
