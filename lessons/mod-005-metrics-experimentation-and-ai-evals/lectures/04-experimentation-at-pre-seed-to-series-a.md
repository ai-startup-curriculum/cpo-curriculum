# Lecture 4 — Experimentation at pre-seed → Series-A scale: hypothesis, MDE, guard metrics, launch decisions

## The setup

Every large tech company runs A/B tests at industrial
scale. Microsoft's ExP platform runs tens of thousands of
experiments per year; Booking.com runs thousands
concurrently; Google, Meta, and Netflix each treat A/B as
a first-class product primitive
([Kohavi, Tang & Xu, *Trustworthy Online Controlled
Experiments*, Cambridge University Press, 2020, Chapters
1–2](https://experimentguide.com/)). The founding-CPO
market's read of that literature — often written under
the frame "how Amazon / Netflix / Booking run
experiments" — tends to produce a specific failure mode
at pre-seed / seed scale: the team runs A/B tests it
does not have the traffic to power, misreads the noisy
result as a real effect (or a real null), and either
ships changes that don't work or kills changes that do.

The founding-CPO experimentation program has to be
*sized to the traffic it actually has* — often two to
four orders of magnitude smaller than the traffic
assumed by the Kohavi book's worked examples. That
constraint changes almost everything: which metrics you
can move detectably, how long an experiment must run,
when to prefer a **holdout** to a per-user split, when
to fall back to a **quasi-experimental** analysis
(Lecture 5), and — critically — when to just *ship the
change* and rely on other instruments (retention,
qualitative signal, the metric taxonomy) rather than a
formal experiment.

This lecture teaches the discipline: **hypothesis
writing**, **minimum-detectable-effect (MDE) sizing**,
**guard metrics**, and **launch / no-launch decision
rules** — as they land at pre-seed → Series-A traffic,
with the underpowered-A/B failure modes made explicit
so you design against them.

## The hypothesis — a testable one, not a directional one

The A/B literature's opening move is a well-formed
hypothesis, in the shape:

> *If we make change X to surface Y, we expect primary
> metric M to move by ≥ E within window W, without
> guardrails G₁…Gₙ breaking, because of mechanism Z.*

Every part carries weight. Reworked from Kohavi et al.'s
Chapter 2 discipline
([Kohavi, Tang & Xu, Chapter 2](https://experimentguide.com/)):

- **Change X to surface Y.** Specific enough that
  someone else could implement it from the hypothesis
  alone. Not *"improve the pricing page"*; rather
  *"add annual pricing toggle above the monthly
  price cards, defaulting to annual, on /pricing for
  US traffic."*
- **Primary metric M.** *One* metric. If you have two
  primary metrics, you effectively double your
  false-positive rate; commit to one.
- **Effect size E.** The minimum effect you'd care to
  ship. This is the MDE (see below), and it's the load-
  bearing choice — you're saying you'll take a null
  result at this effect size as evidence not to ship.
- **Window W.** Weeks, usually. Set *before* the
  experiment; do not extend to chase a p-value.
- **Guardrails G.** The metrics that would make you
  not ship even if M moved as hoped (Lecture 1).
- **Mechanism Z.** A one-sentence causal story.
  *"Because annual pricing lowers the visible monthly
  cost anchor, users who would otherwise churn at
  price will convert."* If you can't state the
  mechanism, you don't understand the bet well enough
  to run the experiment.

The hypothesis is what you write in the experiment brief
(Exercise 3) *before* implementation starts. The
discipline it forces: the team gets clear on what the
change is *for* before spending eng cycles building it,
and the decision rule is fixed before the data comes in.

Chip Huyen's *AI Engineering* (Chapter 4 on evaluation)
and Kohavi's *Trustworthy Online Controlled Experiments*
(Chapter 2 on hypothesis structure) both make the same
point: **the hypothesis is the experiment**. Everything
downstream is measurement of the hypothesis.

## Minimum detectable effect (MDE) — the sizing question

Given a **baseline conversion rate** *p*, a desired
**statistical significance** *α* (usually 0.05), a
desired **statistical power** *(1 − β)* (usually 0.80),
and a target **effect size** *Δ*, the sample size *n* per
variant required to detect *Δ* is approximately (for a
proportion metric with two variants):

```
n ≈ 16 · p · (1 − p) / Δ²
```

The `16` is a rule-of-thumb constant derived from the
standard sample-size formula with α = 0.05 and power =
0.80 for a two-sided z-test on proportions; the full
derivation is in Kohavi et al. Chapter 17 and in Evan
Miller's canonical online calculator
([Kohavi, Tang & Xu, Chapter 17: "The Statistics behind
Online Controlled Experiments"](https://experimentguide.com/);
[Evan Miller, "Sample Size Calculator"](https://www.evanmiller.org/ab-testing/sample-size.html)).

**Worked example — the sizing question the CPO needs to
answer weekly:**

> Baseline: 4% of signups become paid trials.
> You want to detect a **20% relative** improvement
> (4% → 4.8%, absolute Δ = 0.008).
> Power 0.80, α 0.05, two variants.
>
> n ≈ 16 · 0.04 · 0.96 / (0.008)² ≈ 9,600 per variant.
> ≈ **19,200 signups total** to detect a 20% relative
> lift in trial-conversion.
>
> If you get 500 signups per week, that's **~38 weeks**.
> Which means: you cannot run this experiment.

The failure mode is not that the experiment "won't
work"; the failure mode is that the team runs it *for
four weeks*, sees a noisy 12%-relative lift, ships it,
and never learns the effect was noise around zero. The
lesson: **compute the MDE before running the experiment**,
and if the required sample is beyond your reach, do one
of four things:

- **Change the metric to a higher-baseline one.**
  Detecting a 20% lift on a 40%-baseline metric is
  much cheaper than a 4%-baseline metric — because
  variance scales with `p · (1 − p)`, which peaks at
  0.5. Move up the funnel to a step with a higher
  baseline if that step is still meaningful.
- **Widen the tolerated effect size.** Willing to
  accept detecting only a 50%-relative improvement?
  The sample requirement drops by 6.25× (since it
  scales with 1/Δ²).
- **Switch to a quasi-experimental design.** Holdout,
  diff-in-diff, or interrupted-time-series (Lecture 5).
  These trade experimental purity for statistical
  power against the whole population.
- **Ship the change without an experiment**, and
  measure via retention / cohort / qualitative signal.
  This is not laziness; it is the honest
  acknowledgment that at your traffic, the experiment
  cannot answer the question, and other instruments
  can (imperfectly) inform the decision.

The relationships worth memorizing:

| Change | Effect on sample size |
|---|---|
| Halve the effect size (Δ → Δ/2) | 4× sample |
| Double the effect size (Δ → 2Δ) | ¼× sample |
| Baseline drops from 40% → 4% | ~10× sample |
| Baseline drops from 4% → 0.4% | ~10× sample |
| Increase power from 0.80 → 0.90 | ~1.35× sample |
| Tighten α from 0.05 → 0.01 | ~1.5× sample |

*Two-variant, proportion-metric, two-sided-test approximations. Continuous metrics have different formulas; see Evan Miller's continuous-metric calculator.*

## Guard metrics — what the experiment is not allowed to break

Lecture 1 introduced guardrails as taxonomy-level
constraints. In the experimentation program, the same
metrics become **guard metrics** on each experiment:
metrics whose *deterioration* triggers a *no-launch*
decision even if the primary metric moved.

Kohavi et al. (Chapter 21) codify a set of
organizational guardrails Microsoft applies to every
experiment; the shape is the same at any scale:

- **Page-load / render latency** (p50 and p95). A change
  that improves conversion by 3% while slowing p95 load
  by 400ms may cost more downstream retention than the
  headline conversion gain.
- **Error / crash rate.** A change that improves
  activation while doubling 5xx errors is a shipping
  problem, not a product win.
- **Overall session length / DAU.** A change that
  improves one funnel step by cannibalizing another
  action is masking a net-zero (or net-negative)
  outcome; the aggregate is the guard.
- **Unsubscribe / churn indicator.** For any email or
  notification-facing surface, the fraction who opted
  out (or the leading indicator of it).
- **Business guardrails.** Revenue per user, gross
  margin per user, cost per interaction (for
  AI-substrate — see Lecture 7).

The rule: **guard metrics are pre-registered and
symmetric.** They are named in the experiment brief
before launch; they trigger a no-launch decision
regardless of the primary metric; and the threshold is
set to detect a *meaningful* regression (not statistical
significance, which will trip on every large-sample
experiment).

For pre-seed / seed teams with low traffic, the
guardrail challenge is that you often lack the sample
size to detect a *small* guardrail regression
statistically. The response is not to skip guardrails;
it's to *bound* the guardrail check as "no absolute
regression larger than X% observed in the sample," and
to plan a post-launch follow-up read on the same
guardrail once more data accumulates.

## The launch / no-launch decision

Given the experiment ran and the numbers came in, the
decision rule follows the pre-registered hypothesis:

- **Ship** if: primary metric M moved by ≥ E,
  statistically significant at α, no guard metric
  breached.
- **Kill** if: primary metric M did not move (either
  statistically null or observed effect ≤ E), *or* any
  guard metric breached (regardless of primary).
- **Iterate** if: primary metric moved directionally
  but did not clear E, no guardrail broke, and the
  qualitative / cohort evidence suggests a mechanism
  that a second iteration could strengthen. Iterate
  means *ship a modified change with a new
  hypothesis*, not *rerun the same experiment hoping
  the p-value drops*.
- **Extend the experiment** if: the experiment is
  under-powered *and no decision has been made under
  the reveal of the data.* This last condition is
  critical — extending after peeking at the interim
  data is the p-hacking failure mode below.

Kohavi et al. (Chapter 3) are emphatic on writing the
decision rule *before* looking at the data; the
practitioner tradition at Microsoft, Booking, and
Netflix is to have the ship / kill call preregistered
in the experiment brief
([Kohavi, Tang & Xu, Chapter 3](https://experimentguide.com/)).

## The seven underpowered-A/B failure modes

At founding-CPO traffic, the following seven are the
failure modes that produce most wrong decisions. Each
has a specific counter-move.

### 1. Peeking (a.k.a. optional stopping)

The team looks at the p-value daily and stops the
experiment "as soon as it's significant." This inflates
the false-positive rate — a 5% α becomes an effective
20–30% α after two weeks of daily peeking, because you
gave yourself many chances to cross the threshold.

**Counter-moves:** (a) commit to a fixed sample size or
duration in the brief; (b) if you must peek, use a
**sequential testing** correction (Wald's SPRT,
Optimizely's Stats Engine, mSPRT); (c) alternatively,
use a Bayesian setup where continuous inspection is
principled.

Evan Miller's essay "How Not to Run an A/B Test"
remains the canonical short read on peeking
([Miller, "How Not to Run an A/B Test," 2010](https://www.evanmiller.org/how-not-to-run-an-ab-test.html)).

### 2. P-hacking through metric choice

The experiment brief specified a primary metric; after
the data came in, the team noticed that a *different*
metric moved and re-frames the win around that. This
inflates false positives via the same mechanism as
peeking (many chances to find significance).

**Counter-move:** pre-register the primary metric. All
other metrics are *secondary*, and any interesting
secondary movement is a *hypothesis for a future
experiment*, not a launch justification.

### 3. Ratio-metric variance underestimation

Metrics like *revenue per user* or *sessions per user*
are ratios — sums or counts divided by user count — and
the naïve variance calculation (as if it were a
per-user mean) understates the variance dramatically for
heavy-tailed inputs. A tiny handful of whale users can
move the ratio wildly.

**Counter-move:** use the **delta method** for ratio-
metric variance, or bootstrap. Kohavi et al. Chapter 18
covers the delta method; most modern experimentation
platforms (Optimizely, Statsig, Eppo) implement it
under the hood — but check.

### 4. Novelty effect

Users notice the change simply because it's *different*
and interact with it more (or less) in the first days,
before returning to baseline. A 7-day experiment on a
UI change can produce a big spike that vanishes at
day 14.

**Counter-move:** run the experiment for at least two
full weeks and read the *last-week* effect separately
from the aggregate. If the effect decays across the
window, treat the aggregate as an overestimate.

### 5. Weekday / seasonality mix

The experiment ran Monday-through-Friday of a US
holiday week. Traffic mix (which segments came in) is
not the mix the metric was baselined on; the observed
effect reflects mix change, not change effect.

**Counter-move:** run at least one full week (ideally
two) so weekday / weekend mix balances; check for
holidays / launches / marketing pushes during the
window.

### 6. Simpson's paradox — the blended-segment trap

Aggregate effect is positive; every segment's effect is
negative (or vice versa) because the segment mix
shifted between treatment and control. A classic
version: the treatment attracts more high-baseline
users, and the aggregate looks better because of the
mix change rather than the treatment effect.

**Counter-move:** run the analysis per major segment
(new vs. returning, mobile vs. web, plan tier). If the
segment effects disagree, the blended effect is
misleading. Kohavi et al. Chapter 22 covers this in
depth.

### 7. Sample-ratio mismatch (SRM)

The randomization was supposed to produce a 50/50 split
and produced 45/55. This is often invisible in the
metrics but signals an *instrumentation bug* — a
segment of users is being excluded from one arm by a
routing rule, an assignment cache is broken, or the
experiment SDK is misconfigured.

**Counter-move:** every experiment has an **SRM check**
before any metric read. Kohavi et al. Chapter 21 makes
this the first check on any experiment. If SRM > χ²
critical value, halt analysis and diagnose the bug.

The seven failure modes are the point of the
"experimentation program" framing — a *program* is what
prevents any single experiment from falling into one of
these, by making the checks systematic.

## Sequential testing — the practical alternative to fixed-horizon

At low traffic, sequential testing is worth learning as
the founding-CPO default. The idea: use a test statistic
whose critical value is corrected for the fact that
you're looking continuously, so that early stopping is
principled.

Two flavors used in practice:

- **Optimizely / Eppo / Statsig-style Stats Engine.**
  A ratio of likelihoods that allows continuous
  monitoring with type-I error control. Papers by
  Ramesh Johari et al. underlie the implementations
  ([Johari et al., "Peeking at A/B Tests," 2017](https://arxiv.org/abs/1512.04922);
  Optimizely's Stats Engine documentation).
- **Bayesian A/B with informative or weakly-informative
  priors.** The posterior probability that treatment >
  control can be updated continuously; the decision is
  "ship when P(treatment > control | data) > 0.95."
  Chris Stucchio's writing on Bayesian A/B is the
  reference for the practical version
  ([Stucchio, "Easy Evaluation of Decision Rules in
  Bayesian A/B Testing," 2015](https://www.chrisstucchio.com/pubs/VWO_SmartStats_technical_whitepaper.pdf)).

Neither is a free lunch — sequential methods trade
early-stopping flexibility for wider "boundaries" that
need larger effect sizes to trip early. But at
low-traffic settings, they let you stop losers *fast*
without corrupting the false-positive rate.

## When *not* to A/B — and how to decide it early

A useful decision tree the founding CPO runs *before*
scoping an experiment:

1. **Can I compute the MDE, and is the required sample
   within reach in an acceptable window (usually ≤ 4
   weeks)?** If no → skip to step 4.
2. **Is the change genuinely reversible?** If shipping
   the losing arm irreversibly damages user trust or
   locks in an architecture, prefer a smaller-scope
   ship-and-observe. If reversible → good candidate
   for A/B.
3. **Is the primary metric measurable within the
   window?** If the primary metric is a lagging
   indicator (renewal that happens in 6 months), the
   experiment can't read it in time. Substitute a
   leading proxy or use a longer-horizon
   quasi-experimental design.
4. **If A/B is infeasible: which fallback?**
   - **Holdout / geo split** (Lecture 5) — ship the
     change to 90% of traffic and hold 10% as
     control; read the aggregate metric difference
     over months.
   - **Diff-in-diff** (Lecture 5) — release the change
     to a segment (a geo, a plan tier, a cohort),
     compare pre/post change against a control
     segment.
   - **Interrupted time-series** (Lecture 5) — ship
     to everyone, model the counterfactual as the
     pre-launch trend, and estimate the effect as
     the deviation.
   - **Ship with pre-registered signals** — commit
     the metric read, segment cuts, and decision
     rule *before* launch, then observe. The eval-set
     analogue of an experiment (Lecture 6).

The decision tree matters because the reflex "run an
A/B" is wrong roughly half the time at founding-CPO
scale, and the substitutes are legitimate — not
consolation prizes.

## The experiment brief — the artifact

Every experiment worth running has a one-page brief the
CPO signs off on before implementation. The shape,
grounded in Kohavi et al. Chapter 2:

```
EXPERIMENT: <short name>
Owner: <PM / CPO> | Status: proposed / running / concluded

HYPOTHESIS
If <change X> to <surface Y>, primary metric <M> will
move by ≥ <E> within <W>, without <G₁…Gₙ> breaking,
because <mechanism Z>.

PRIMARY METRIC
<name> — baseline <p>, target <p + Δ>.

GUARD METRICS (pre-registered)
- <name> — threshold <value>
- <name> — threshold <value>

SIZING
- MDE calculation: n ≈ ... per variant
- Traffic estimate: ... per week
- Duration estimate: ... weeks (for full read at MDE)

DESIGN
- Randomization unit: user / session / account
- Traffic allocation: 50/50 (or ...)
- Segments to break out in analysis: ...
- Sequential-testing method (if any): ...

DECISION RULE
- SHIP if: primary moves ≥ E, no guard breached
- KILL if: primary null OR any guard breached
- ITERATE if: <specific conditions>

POST-LAUNCH READ (if shipped)
- Which retention / cohort / long-horizon read confirms
  the effect at N weeks post-launch

RISKS
- Novelty risk: <yes/no> — how handled
- SRM check: yes (mandatory)
- Confounders: <named>
```

The brief lives with the six-pager (mod-004 Lecture 3)
for the same bet; the experiment is the
falsifier for the six-pager's mechanism claim.

## What the CPO does personally

- **Authors the hypothesis and the decision rule.** The
  hypothesis is a product-strategy artifact; the
  decision rule prevents downstream p-hacking.
- **Computes the MDE.** Kohavi et al.'s Chapter 17
  formulas or Evan Miller's calculator; either way,
  the CPO does it, not the data team, because the
  ship/no-ship threshold is a *product* call.
- **Names the guard metrics and thresholds.** No guard
  is set by the data team.
- **Signs off on the brief before implementation.** The
  experiment does not enter the queue without CPO
  approval.
- **Reads the result against the pre-registered rule.**
  No re-framing, no metric-swapping, no window
  extension after seeing the data.

## What the CPO consumes

- The experimentation platform (Optimizely, Statsig,
  Eppo, GrowthBook, or a home-grown feature-flag +
  analytics setup). Owned by eng or data.
- The statistical engine (delta method, sequential
  testing, Bayesian posterior updates). Owned by the
  platform.
- The variance and SRM checks (automatic in most
  platforms). Owned by the platform.

## Boundaries this lecture keeps

- **Non-experimental causal inference** — holdouts,
  diff-in-diff, interrupted-time-series — is
  [Lecture 5](05-quasi-experimental-methods-when-ab-fails.md).
- **Eval-based decisions for AI-substrate features**
  (which replace A/B for stochastic outputs) are
  [Lecture 6](06-eval-driven-decisions-for-llm-products.md).
- **Cost / latency / quality trade-offs** as an
  experiment surface are
  [Lecture 7](07-cost-latency-quality-pareto.md).
- **Pricing-page experiments** at depth are
  [mod-006](../../mod-006-pricing-packaging-and-monetization/README.md).
- **The statistical foundations at depth** (bootstrap,
  delta method derivation, sequential-testing theory)
  are outside a CPO curriculum's scope; the references
  in [resources.md](../resources.md) are the deeper
  reads.
- **Model-evaluation statistical calibration** — grader
  bias, inter-annotator agreement, human-review
  sampling design at depth — is level-30 work owned by
  [model-evaluation-engineer-learning](https://github.com/ai-engineering-curriculum/model-evaluation-engineer-learning).

## Takeaways

- The **hypothesis** — change / surface / primary
  metric / effect size / window / guardrails /
  mechanism — is the experiment; everything else is
  measurement.
- **MDE sizing** is the founding-CPO discipline: if
  the required sample is out of reach in a reasonable
  window, don't run the experiment. Compute it *before*
  the eng work, not after.
- **Guard metrics** are pre-registered, symmetric, and
  can veto a launch regardless of the primary metric.
- **Peeking, p-hacking, ratio-metric variance,
  novelty, seasonality, Simpson's paradox, and SRM**
  are the seven failure modes an experimentation
  program is designed against.
- **Sequential testing** is the founding-CPO default
  for low-traffic scenarios; it lets you stop losers
  fast without corrupting α.
- **A/B is not always the right answer.** Holdouts,
  diff-in-diff, and ship-and-observe are legitimate
  substitutes when traffic won't support A/B — see
  Lecture 5.
- Every experiment has a **one-page brief** the CPO
  signs off on before implementation; no experiment
  ships without a pre-registered decision rule.

Lecture 5 covers the quasi-experimental methods for
the (often majority) case where A/B is infeasible.
