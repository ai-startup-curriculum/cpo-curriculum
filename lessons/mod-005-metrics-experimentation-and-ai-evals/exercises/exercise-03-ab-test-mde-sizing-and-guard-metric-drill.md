# Exercise 3 — A/B test MDE sizing and guard-metric drill

**Time:** ~3 hours. **Deliverable:** one **experiment
brief** in the
[Lecture 4](../lectures/04-experimentation-at-pre-seed-to-series-a.md#the-experiment-brief--the-artifact)
shape — hypothesis, primary metric, pre-registered guard
metrics, MDE calculation, traffic requirement, decision
rule, sequential-testing / peeking discipline, and
post-launch read — for a specific change your product (or
plausible-synthetic product) might ship. Plus a half-page
**fallback memo** stating what you would do if the MDE
calculation says the A/B is infeasible.

## Purpose

Walk the hypothesis → MDE → guard → decision rule
discipline from
[Lecture 4](../lectures/04-experimentation-at-pre-seed-to-series-a.md)
end to end, against a real traffic estimate and a real
baseline. The point of the exercise is to force the
founding-CPO move: **compute the MDE *before* implementing
the change**, and — half the time at pre-seed → Series-A —
discover the A/B isn't the right instrument and reach for a
Lecture 5 fallback or a Lecture 6 eval-set launch gate.

This exercise cites the hypothesis in
[Exercise 2](exercise-02-activation-retention-cohort-analysis-drill.md)'s
diagnosis — the diagnosis ends on *"what Exercise 3 should
test,"* and that is the change you brief here.

## What you need before you start

- The diagnosis from
  [Exercise 2](exercise-02-activation-retention-cohort-analysis-drill.md).
  The experiment is a *response* to the diagnosis; without
  it, the brief becomes "test an idea we had in a
  meeting," which is where most pre-seed A/Bs lose.
- The metric taxonomy from
  [Exercise 1](exercise-01-north-star-and-input-metric-authoring.md).
  The primary metric is one of the inputs; the guard
  metrics map to the taxonomy's guardrails.
- A real (or plausible-synthetic) **weekly traffic
  number** for the surface the change ships on. "500
  signups a week" is a real number; "lots of traffic" is
  not. If you don't know, estimate and state the
  estimation method.
- A real (or plausible-synthetic) **baseline rate** for
  the primary metric. "4% of signups become paid trials"
  is the shape; cite the data pull or the dashboard it
  came from.
- An MDE calculator you can run — one of:
  - Evan Miller's online calculator —
    [evanmiller.org/ab-testing/sample-size.html](https://www.evanmiller.org/ab-testing/sample-size.html).
  - The hand formula from
    [Lecture 4 — MDE](../lectures/04-experimentation-at-pre-seed-to-series-a.md#minimum-detectable-effect-mde--the-sizing-question):
    *n ≈ 16 · p · (1 − p) / Δ²* for proportion metrics
    at α=0.05, power=0.80.
  - `statsmodels.stats.power.NormalIndPower` or
    `scipy.stats` for continuous metrics
    ([statsmodels power docs](https://www.statsmodels.org/stable/stats.html#power-and-sample-size-calculations)).

## Choosing the change to brief

Pick one *specific* change. In order of preference:

1. **The change Exercise 2's diagnosis recommended.** The
   diagnosis-to-experiment link is the whole point of the
   module; honor it.
2. **A real change the team is weeks away from shipping.**
   The brief is useful immediately.
3. **A plausible-synthetic change** at the shape of the
   Lecture 4 worked example — a pricing-page toggle, an
   onboarding step reorder, a notification-copy change, a
   checkout-flow simplification. Not an AI-substrate
   model-config change; those go in
   [Exercise 4](exercise-04-llm-eval-suite-authoring-for-one-agent.md)
   and
   [Exercise 5](exercise-05-cost-latency-quality-pareto-drill.md).

Match the change scope to a *real* founding-CPO decision:
specific enough that an engineer could implement it from
the brief alone (per
[Lecture 4 — Hypothesis](../lectures/04-experimentation-at-pre-seed-to-series-a.md#the-hypothesis--a-testable-one-not-a-directional-one)).

## What the experiment brief must contain

Use the Lecture 4 template directly. Two pages max.

### 1. Hypothesis

Write it in the Lecture 4 shape:

> *If we make change X to surface Y, we expect primary
> metric M to move by ≥ E within window W, without
> guardrails G₁…Gₙ breaking, because of mechanism Z.*

Every slot filled, each with the explicitness Lecture 4
requires:
- **X** specific enough that an engineer could implement
  it from the sentence alone.
- **M** a single primary metric (two primaries doubles
  the false-positive rate — commit to one).
- **E** the minimum effect you'd care to ship. State it
  in both relative and absolute terms ("+20% relative,
  +0.008 absolute from a 4% baseline").
- **W** named up front; do not extend to chase
  significance.
- **G** three to five pre-registered guards from the
  Lecture 4 list.
- **Z** one sentence on *why you expect the mechanism to
  work*. If you can't state the mechanism, you don't
  understand the bet.

### 2. Primary metric and baseline

- The primary metric name, the exact event / query that
  defines it, and the current baseline rate (with the
  period it was computed over).
- Why *this* metric, not one further up or down the
  funnel. If it's the lowest-baseline metric on the
  funnel, state the trade-off — low-baseline metrics
  need enormous sample sizes.

### 3. Guard metrics (pre-registered)

Three to five, pulled from
[Lecture 4 — Guard metrics](../lectures/04-experimentation-at-pre-seed-to-series-a.md#guard-metrics--what-the-experiment-is-not-allowed-to-break):

- At least one **UX / latency guard** (p95 page-load or
  API latency).
- At least one **error / crash guard**.
- At least one **business guard** (revenue per user,
  gross margin, cost per interaction for AI-substrate).
- Each with a **named threshold** — a number, not a
  wish. Use the Lecture 4 small-sample bound ("no
  observed regression larger than X% in sample") if the
  statistical threshold isn't reachable at your traffic.

### 4. MDE calculation and traffic requirement

**Show the calculation.** Not just the output. For a
proportion metric at α=0.05, power=0.80:

```
n ≈ 16 · p · (1 − p) / Δ²
```

Fill in *p* and Δ, compute *n*, double it for two
variants, divide by weekly traffic to get the duration.

Then **check against your actual traffic**. The Lecture 4
worked example: 19,200 total signups at 500/week = 38
weeks. If the duration exceeds ~4 weeks, Lecture 4 says
you cannot run the experiment; proceed to the fallback
memo (Section 7 below) rather than ignoring the number.

**Scenarios.** Compute the sample / duration under three
different Δ assumptions — a 10% relative lift, a 20%
relative lift, and a 50% relative lift. Each halving of
Δ quadruples *n*; the exercise is to see this live. Use
[Lecture 4's sensitivity table](../lectures/04-experimentation-at-pre-seed-to-series-a.md#minimum-detectable-effect-mde--the-sizing-question).

### 5. Design

- **Randomization unit:** user / session / account.
  Which, and why — for B2B products, account-level
  randomization is often the right call despite the
  smaller effective *n*, because contamination
  between users within an account is high.
- **Traffic allocation:** 50/50 unless there's a
  specific reason to skew.
- **Segments to break out in analysis** (not segments
  to analyze *into* significance — Lecture 4's
  Simpson's-paradox counter is to look at segments
  but not to re-pick the primary metric).
- **Sequential-testing method**, if any. The Lecture 4
  default at low traffic is one of:
  - Optimizely / Eppo / Statsig Stats-Engine-shape
    sequential (Wald SPRT family;
    [Johari et al. 2017](https://arxiv.org/abs/1512.04922));
  - Bayesian A/B with weakly-informative priors
    (Stucchio's VWO white-paper is the practitioner
    reference —
    [chrisstucchio.com/pubs/VWO_SmartStats_technical_whitepaper.pdf](https://www.chrisstucchio.com/pubs/VWO_SmartStats_technical_whitepaper.pdf));
  - Explicit fixed-horizon with *no peeking*.
  Pick one and name it.
- **SRM check** (sample-ratio mismatch). State that it
  is **mandatory** and will run before any metric read.

### 6. Decision rule — pre-registered

Written as a decision table, from
[Lecture 4 — The launch / no-launch decision](../lectures/04-experimentation-at-pre-seed-to-series-a.md#the-launch--no-launch-decision):

- **SHIP** if: primary moves ≥ E, significant at α, no
  guard breached.
- **KILL** if: primary null (observed ≤ E or
  statistically null) OR any guard breached.
- **ITERATE** if: primary directionally positive but
  short of E and no guard broke — write the *specific*
  conditions and the *specific* next-change you'd try.
  Iterate means **ship a modified change under a new
  hypothesis**, not re-run the same test hoping p
  drops.
- **EXTEND** only if: experiment is under-powered *and
  no decision has been made under the reveal of the
  data.* Peeking-then-extending is p-hacking; the
  brief forbids it in writing.

### 7. Fallback memo — what if the MDE says no?

Half a page. If the duration estimate in Section 4 is
beyond your traffic / timeline, walk the Lecture 4
decision tree
([Lecture 4 — When *not* to A/B](../lectures/04-experimentation-at-pre-seed-to-series-a.md#when-not-to-ab--and-how-to-decide-it-early)):

- **Can you change to a higher-baseline primary metric
  further up the funnel?** State which, and the new
  MDE.
- **Can you widen the tolerated effect size?** Would you
  ship on a 50%-relative lift? What's the sample at
  that Δ?
- **Should this be a quasi-experimental design?** Which
  one from
  [Lecture 5](../lectures/05-quasi-experimental-methods-when-ab-fails.md)
  (holdout, DiD, ITS), and why — including the
  assumption each requires and whether your data
  satisfies it.
- **Should this ship without an experiment** with
  pre-registered leading indicators and a Lecture 5
  N-week follow-up read? Name the indicators.
- **If AI-substrate**, is the right launch gate an
  eval-set threshold rather than an A/B — the Lecture
  6 move
  ([Lecture 6 — When the eval-suite threshold replaces
  A/B](../lectures/06-eval-driven-decisions-for-llm-products.md#when-the-eval-suite-threshold-replaces-ab-as-the-launch-gate))?
  Author the eval set in
  [Exercise 4](exercise-04-llm-eval-suite-authoring-for-one-agent.md).

### 8. Risks — the seven underpowered-A/B failure modes

Walk the
[Lecture 4 — Seven failure modes](../lectures/04-experimentation-at-pre-seed-to-series-a.md#the-seven-underpowered-ab-failure-modes)
and name the counter-move already baked into the brief
for each:

- Peeking → fixed horizon / sequential method stated;
- P-hacking through metric choice → primary pre-
  registered, secondaries are hypotheses for future
  experiments;
- Ratio-metric variance → delta-method or bootstrap
  (consume from eng if you can't compute it);
- Novelty effect → ≥ 2-week run, last-week effect
  reported separately;
- Weekday / seasonality mix → ≥ 1 full week, holiday
  check;
- Simpson's paradox → segment breakout in analysis;
- SRM → mandatory SRM check before any metric read.

## Starter guidance

- **Compute the MDE first, before writing the
  hypothesis.** You will find that your real-traffic
  capacity shapes which hypotheses are testable; writing
  the hypothesis first invites a plan the sample size
  cannot support. Lecture 4's whole discipline is
  "number first, prose second."
- **Prefer a higher-baseline primary metric.** The
  variance structure `p · (1 − p)` peaks at 0.5; moving
  the primary metric from a 4% conversion to a 40%
  conversion drops sample size ~10×. Lecture 4's
  sensitivity table makes this concrete.
- **Guard metrics with wish-level thresholds don't
  trigger.** "Latency shouldn't regress" is wish-level;
  "p95 API latency doesn't exceed 800ms on the
  treatment arm" is a trigger.
- **Fallback memo is the point, not the fallback.** The
  CPO move at pre-seed is to see that an A/B is
  infeasible and reach for a smarter design, not to
  run an under-powered A/B and ship on noise. Write
  the fallback as if you were going to execute on it.
- **Author the brief before the engineer builds.** The
  hypothesis is what gets clear on *what the change is
  for* before eng spends cycles; the brief is the
  artifact that makes the pre-registration real.

## Acceptance criteria

- The **hypothesis** is written in the Lecture 4 shape,
  with every slot filled — X specific enough to
  implement from the sentence; M a single metric; E in
  relative and absolute terms; W named; G pre-
  registered; Z a one-sentence mechanism.
- The **MDE calculation** is shown with inputs,
  intermediate math, and the resulting *n* and duration
  — at three Δ scenarios (10% / 20% / 50% relative).
- The **guard metrics** have named thresholds (not
  wishes); UX, error, and business dimensions are each
  represented.
- The **design** names randomization unit, allocation,
  segments, sequential-testing method, and SRM check.
- The **decision rule** is a pre-registered table
  (SHIP / KILL / ITERATE / EXTEND).
- The **fallback memo** walks the Lecture 4 decision
  tree and names which fallback you'd execute if the
  MDE says no — including the specific Lecture 5
  design or Lecture 6 eval gate, if applicable.
- The **risks section** names a counter-move for each
  of the seven Lecture 4 failure modes.

## Common failure modes

- **Hypothesis without a mechanism.** "If we add
  annual pricing, trial conversion will go up." Why?
  State the causal story in one sentence or you're
  running a wish, not a hypothesis.
- **MDE theatre.** The calculation is included but the
  team runs the experiment anyway at 1/10 the required
  sample. Pre-register the duration *before* launch
  and halt at that duration — honoring the pre-
  registration is where discipline lives.
- **Guard metrics as decoration.** Pre-registered but
  without numeric thresholds, or with thresholds that
  would never trigger. The guard that cannot fire
  isn't a guard.
- **Multiple primary metrics.** "Primary metrics are M₁
  and M₂." No. Pick one; the second is a secondary
  observation whose movement is a hypothesis for a
  future experiment.
- **Peeking-then-extending.** The brief says fixed
  horizon; the team peeks at day 4 and extends to day
  21 "to get significance." This is the Lecture 4
  peeking failure mode in its most common disguise.
- **Ignoring the fallback.** The MDE says 38 weeks and
  the team runs the A/B for 4 weeks anyway. The whole
  point of this exercise is to make running the
  under-powered A/B feel wrong.
- **AI-substrate A/B on the LLM output.** Trying to
  per-user A/B prompt-version A against prompt-version
  B. The Lecture 6 move is to use the eval suite as
  the launch gate; A/B on the UX surface, not on the
  stochastic output.

## Source alignment

The experiment-brief shape, hypothesis-first discipline,
guardrail list, and seven failure modes derive from
Ronny Kohavi, Diane Tang & Ya Xu, *Trustworthy Online
Controlled Experiments*, Cambridge University Press,
2020, Chapters 2, 3, 17, 21, and 22 —
[experimentguide.com](https://experimentguide.com/).
The MDE formula and online calculator are Evan Miller,
"Sample Size Calculator" —
[evanmiller.org/ab-testing/sample-size.html](https://www.evanmiller.org/ab-testing/sample-size.html)
— and Miller, "How Not to Run an A/B Test," 2010 —
[evanmiller.org/how-not-to-run-an-ab-test.html](https://www.evanmiller.org/how-not-to-run-an-ab-test.html).
The sequential-testing references are Ramesh Johari et
al., "Peeking at A/B Tests," 2017 —
[arxiv.org/abs/1512.04922](https://arxiv.org/abs/1512.04922)
— and Chris Stucchio, "Easy Evaluation of Decision Rules
in Bayesian A/B Testing," 2015 (the VWO white paper) —
[chrisstucchio.com/pubs/VWO_SmartStats_technical_whitepaper.pdf](https://www.chrisstucchio.com/pubs/VWO_SmartStats_technical_whitepaper.pdf).
