# Exercise 4 — Pricing experiment design with guard metrics

**Time:** ~2 hours. **Deliverable:** one **pricing
experiment brief** in the
[Lecture 5](../lectures/05-pricing-experiments-and-grandfathering.md#the-pricing-experiment-brief)
shape — pricing change described concretely, cohort /
exposure design, A/B-safety call, grandfathering plan,
primary metric with read horizon, three-horizon guard
metrics (short / mid / long), MDE / traffic estimate,
launch rule, communication plan, rollback — for a
specific pricing change against the model from
[Exercise 1](exercise-01-monetization-model-authoring-for-one-product.md)
sharpened by
[Exercise 3](exercise-03-van-westendorp-and-gabor-granger-drill.md).
Plus a half-page **grandfathering memo** that walks the
four shapes from Lecture 5 and defends the one you'd pick.

## Purpose

Walk the pricing-change → cohort / A/B-safety →
guard-metrics-at-three-horizons → grandfathering →
communication → rollback discipline from
[Lecture 5](../lectures/05-pricing-experiments-and-grandfathering.md)
end to end, against a change you'd actually make to the
model you authored in Exercise 1. The point of the
exercise is to force two founding-CPO moves:

1. **Decide whether the change is A/B-safe at all.** Half
   of pricing changes aren't — they affect existing
   customers and must be run as a cohort change with a
   grandfathering plan, not as a per-user split.
2. **Pre-register all three guard horizons before you
   launch.** Pricing primary metrics move fast; pricing
   guards lag by weeks to months. A team that reads only
   the short-horizon win and ships ends up fixing a
   long-horizon regression at month 6, usually at much
   greater cost than the short-term lift was worth.

This exercise sits on top of
[mod-005 Exercise 3](../../mod-005-metrics-experimentation-and-ai-evals/exercises/exercise-03-ab-test-mde-sizing-and-guard-metric-drill.md) —
the base A/B-brief shape — and adds the pricing-specific
discipline Lecture 5 names. If you haven't done mod-005
Exercise 3, skim its MDE / guard-metric structure first;
this brief is a specialization of it, not a replacement.

## Prerequisites

- [Exercise 1](exercise-01-monetization-model-authoring-for-one-product.md)
  complete — the monetization model is the baseline the
  change moves off of.
- [Exercise 2](exercise-02-good-better-best-packaging-drill.md)
  complete — the tier structure is what the change
  touches.
- [Exercise 3](exercise-03-van-westendorp-and-gabor-granger-drill.md)
  complete — the WTP evidence is what justifies the
  specific price-point move.
- A real (or plausible-synthetic) **weekly traffic
  number** for the surface the change ships on. "150 new
  trials a week" is a real number; "lots of traffic" is
  not. If you don't know, estimate and state the
  method.
- A real (or plausible-synthetic) **baseline rate** for
  the primary metric (new-signup ARPU, trial-to-paid
  conversion, free-to-paid conversion, contraction MRR
  — whatever you'll move). Cite the data pull or state
  the assumption.
- An MDE calculator you can run — Evan Miller's online
  tool
  ([evanmiller.org/ab-testing/sample-size.html](https://www.evanmiller.org/ab-testing/sample-size.html))
  or the hand formula from
  [mod-005 Lecture 4](../../mod-005-metrics-experimentation-and-ai-evals/lectures/04-experimentation-at-pre-seed-to-series-a.md#minimum-detectable-effect-mde--the-sizing-question).

## Choosing the pricing change to brief

Pick one *specific* change. In order of preference:

1. **The change Exercise 3's WTP evidence pointed at.**
   The study ended on a *"next-step experiment"*
   sentence (Section 6 of the write-up). Honor it.
2. **A real change the team is weeks away from
   shipping.** The brief is useful immediately.
3. **A plausible change against the Exercise 1 model.**
   Candidates include:
   - Raising the Better / middle tier from $X to $Y.
   - Switching the meter on one tier from per-seat
     to usage-based (per-document, per-outcome).
   - Adding a reverse-trial on top of today's free-
     trial (Lecture 4).
   - Adding floors or ceilings to a usage-based tier
     (Lecture 6).
   - Shifting an enterprise-only gate (SSO, audit
     log) down to the Better tier.

Pick a change *concrete enough that an engineer and a
head of marketing could implement it from the brief
alone* — the Lecture 5 brief forcing-function.

## What the pricing experiment brief must contain

Use the
[Lecture 5 template](../lectures/05-pricing-experiments-and-grandfathering.md#the-pricing-experiment-brief)
directly. Two pages max for the brief; the half-page
grandfathering memo is Section 8 below.

### 1. The change (quarter page)

- **The pricing change in one paragraph.** Specific
  enough an engineer could ship it from this
  paragraph. Not *"raise prices on Pro"* but *"raise
  Pro-tier monthly price from $49/mo to $69/mo for
  new sign-ups starting 2026-11-01; include 500
  documents/month (unchanged); overage at
  $0.05/document (unchanged)."*
- **Why — the mechanism.** One sentence on *why* this
  change should move the primary metric, grounded in
  WTP evidence (Exercise 3), competitor evidence, or
  a unit-economics constraint. If you can't name the
  mechanism, the brief is a wish.

### 2. Cohort and A/B-safety call

Grounded in
[Lecture 5 — Which pricing changes are A/B-safe](../lectures/05-pricing-experiments-and-grandfathering.md#which-pricing-changes-are-ab-safe).

- **A/B-safety classification.** One of:
  - **A/B-safe** — pricing-page presentation,
    trial-length / cap for new sign-ups, upgrade-
    prompt copy, discount / promo experiments.
    Random per-user split is on the table.
  - **A/B-uncomfortable** — new-sign-up-only price
    changes where two cohorts of new sign-ups see
    different prices in the same week. Technically
    safe (no user sees two prices) but operationally
    fragile; typically run as sequential cohorts,
    not concurrent A/B.
  - **Not A/B-safe** — existing-customer price
    increases, meter changes, feature-gate changes
    on existing tiers, tier restructures. Cohort or
    all-at-once change required.
- **Justification.** Which category and why — one
  sentence. If the change is not A/B-safe, you'll
  need Section 8 (grandfathering memo) to carry
  weight; the brief is still useful, but it is a
  *rollout plan*, not an experiment.
- **Cohort definition.** Exactly who gets the new
  price. "All new sign-ups from 2026-11-01 onward";
  "all new sign-ups in geo = US"; "existing accounts
  on Pro tier at next renewal after 2026-11-01." No
  ambiguity.

### 3. Hypothesis

Written in the mod-005 Lecture 4 shape, with Lecture 5's
pricing-specific additions:

> *If we <make change X> for <cohort Y>, we expect
> primary metric M to move by ≥ E within window W,
> without short-horizon guards G_s, mid-horizon guards
> G_m, or long-horizon guards G_l breaking, because of
> mechanism Z.*

- **X** specific enough that an engineer could ship
  it from this sentence (dollar figures, specific
  surface, specific cohort).
- **M** a single primary metric. Candidates: new-
  signup ARPU, MRR per new signup, trial-to-paid
  conversion, free-to-paid conversion, blended ARPU
  on cohort. One, not two.
- **E** the minimum effect in both relative and
  absolute terms ("+15% relative, +$7 absolute on
  $47 baseline"). This is your MDE.
- **W** the read-at horizon for the primary metric,
  usually 2–8 weeks.
- **G_s, G_m, G_l** are the three guard-horizon sets
  from Section 5 below.
- **Z** one sentence on the causal story — grounded
  in Exercise 3's WTP evidence where possible.

### 4. Primary metric and baseline

- **The primary metric name**, the exact event /
  query that defines it, and the current baseline
  rate (with the period it was computed over).
- **Why *this* metric**, not one further up or down
  the funnel. The Lecture 5 note: at founding scale,
  the common failure is to pick a metric so far
  downstream (LTV, NRR) that no sample size will
  move it. Pick the leading indicator and name the
  lagging-metric read as a mid- or long-horizon
  guard instead.

### 5. Guard metrics at three horizons — pre-registered

Grounded in
[Lecture 5 — Guard metrics for pricing experiments](../lectures/05-pricing-experiments-and-grandfathering.md#guard-metrics-for-pricing-experiments).
This is where this brief diverges most from the base
mod-005 Lecture 4 shape. Each guard has a **named
numeric threshold** — not a wish.

- **Short-horizon guards** (2–4 weeks). At least two,
  with thresholds:
  - *New-signup rate.* "Not more than 10% below
    pre-change weekly baseline."
  - *Trial-to-paid conversion* or *free-to-paid
    conversion*, depending on the entry motion.
  - *Pricing-page → checkout drop-off.*
  - *Pricing-related support ticket volume.*
    "Pricing / confusion tickets don't exceed 2× the
    pre-change weekly baseline."
- **Mid-horizon guards** (4–12 weeks). At least two,
  with thresholds:
  - *Contraction MRR* — existing customers
    downgrading because they saw the new page.
  - *Downgrade rate on new signups within first
    billing cycle.* High rate signals an
    over-priced or over-featured top tier.
  - *Cohort retention at week 4, week 8, week 12*
    for the treatment cohort — leading indicator
    for LTV at horizon.
- **Long-horizon guards** (12–52 weeks). At least
  one, with a threshold *and* an explicit
  pre-registered-horizon read date:
  - *LTV at horizon* (or a cohort-retention-shape
    proxy if you can't measure LTV directly at your
    scale).
  - *Net Revenue Retention* on the treatment cohort.
  - *CAC payback period.*

**The lagged-guard discipline (Lecture 5).** State
explicitly: *"We will not roll the change out
permanently until all three horizon reads clear."* If
the mid-horizon or long-horizon read regresses after
the short-horizon read looks good, the brief commits
you to rolling back (or holding further rollout), not
to shrugging it off.

### 6. MDE and traffic requirement

**Show the calculation**, not just the output. For a
proportion metric at α=0.05, power=0.80:

```
n ≈ 16 · p · (1 − p) / Δ²
```

For an ARPU or revenue metric, state the variance
assumption and use `statsmodels.stats.power` or Evan
Miller's continuous-metric calculator. ARPU is a
heavy-tailed metric; expect much larger sample
requirements than a proportion metric at the same
nominal effect size (Lecture 5 referencing mod-005
Lecture 4's ratio-metric variance failure mode).

Fill in *p* (or baseline mean + variance), Δ, compute
*n*, double for two variants, divide by weekly
traffic to get the duration.

**Three scenarios.** Compute the sample / duration
under three Δ assumptions — a 10% relative lift, a
20% relative lift, and a 50% relative lift — so you
see the sample-size sensitivity live. Each halving of
Δ quadruples *n* (mod-005 Lecture 4's sensitivity
table).

**Check against your actual traffic.** If duration
exceeds ~8 weeks for a pricing experiment, the brief
is at risk of becoming an under-powered A/B that
reads noise as signal. Walk the Lecture 5 fallback:
switch to a cohort read with pre-post comparison;
switch to a higher-baseline primary metric; widen the
tolerated effect size; or ship-and-observe with
pre-registered long-horizon signals.

### 7. Launch rule — pre-registered

Written as a decision table in the Lecture 5 shape:

- **SHIP** if: primary moves ≥ E at week W,
  statistically significant at α, *and* no guard
  breaches at week W, 4 weeks post, and the
  pre-registered long-horizon read.
- **HOLD** if: primary moves directionally but
  ambiguous (observed effect short of E, within
  noise); *or* any guard is within noise of its
  threshold. The hold response is to extend the
  read, not to extend the experiment peek-style.
- **KILL / ROLLBACK** if: primary moves in wrong
  direction *or* any guard breaches at any horizon.
  Rollback plan is Section 9 below.
- **STAGED ROLLOUT** if: primary looks good at W but
  the long-horizon guard can't be read yet. Expand
  rollout from, say, 10% → 50% → 100% over
  checkpoints, with a hold on expansion if an
  intermediate guard regresses.

The *pre-registration* is the point. Writing SHIP /
HOLD / KILL after the data arrives is where
pricing-experiment discipline falls apart.

### 8. Grandfathering memo (half page) — Lecture 5's four shapes

Grounded in
[Lecture 5 — The grandfathering decision](../lectures/05-pricing-experiments-and-grandfathering.md#the-grandfathering-decision).

Walk the four shapes and defend the one you'd pick:

- **Full grandfather** (existing customers keep old
  price forever).
- **Time-bounded grandfather** (6–12 months at the
  old price; new price at the first renewal after
  that).
- **Next-renewal migration** (old price for the rest
  of the current billing period; new price at
  renewal).
- **Immediate migration** (new price from date D
  onward, subject to contract-notice obligations).

For your pick, state:

- **Why this one** — grounded in the Lecture 5
  trust-vs-ARPU trade-off. The founding-CPO default
  for < 500 customers is time-bounded (6–12 months)
  with a proactive communication program; departures
  from the default need a specific reason.
- **Who's affected** — count of existing accounts,
  dollar impact, which customer tiers / segments.
- **What breaks if you got the choice wrong** — the
  specific failure mode. Full grandfather → ARPU
  drag at 3–5 years. Immediate migration → churn
  spike plus potential legal exposure on contracts
  with price-hold clauses.

If the change is **not A/B-safe** (Section 2
classification), the grandfathering memo is the
load-bearing artifact — the brief as a whole is
really a cohort-change plan, and the grandfathering
decision is where customer trust is preserved or
broken.

### 9. Communication plan and rollback

Grounded in
[Lecture 5 — Default recommendation](../lectures/05-pricing-experiments-and-grandfathering.md#the-default-recommendation)
and
[Lecture 5 — The pricing experiment brief](../lectures/05-pricing-experiments-and-grandfathering.md#the-pricing-experiment-brief).

- **Communication to existing customers.** Who gets
  what, when:
  - Top-100 (or top-10) accounts: personal email or
    call from CEO or CPO, pre-change, offering to
    discuss.
  - Smaller customers: automated email with
    transition date, in-product notice on next
    login.
  - Public: pricing-page update timing,
    announcement if any.
- **Communication to GTM and finance.** Internal
  briefing, updated collateral, deal-desk memo for
  mid-cycle deals.
- **Rollback plan.** If the experiment goes badly:
  - Price reversion for new signups.
  - Make-good for anyone charged under the new
    pricing before rollback — refund, credit, hold
    at new price with disclosure.
  - Communication to affected cohort on reversion.

The communication plan is often where founding CPOs
under-invest; Lecture 5's through-line is that *the
price change is not the trust breaker; the surprise
is.*

### 10. Risks — the Lecture 5 common failure modes

Walk the
[Lecture 5 failure-mode list](../lectures/05-pricing-experiments-and-grandfathering.md#common-failure-modes)
and name the counter-move already baked into the brief
for each:

- **Pricing-page A/B conflated with a pricing
  experiment** — be explicit about which the brief is.
- **Peeking** — fixed horizon or sequential method named
  (same as mod-005 Lecture 4).
- **Ignoring the lagged guard** — Section 5 explicitly
  pre-registers three horizons.
- **A/B on prices that aren't A/B-safe** — Section 2's
  classification call makes this impossible to miss.
- **No grandfather when needed** — Section 8 forces the
  decision.
- **Grandfather-forever without expiry** — Section 8
  defaults to time-bounded with a stated expiry date.
- **Pricing change without a communication program** —
  Section 9 is mandatory.

## Starter guidance

- **Classify A/B-safety first.** Section 2 before any
  of the rest. Half of pricing-change briefs fail
  because the team wrote an A/B hypothesis for a
  change that was never A/B-safe to begin with.
- **Pre-register all three guard horizons.** The
  common pricing-experiment pathology is reading the
  short-horizon win and shipping. The brief is where
  you make yourself commit to reading the mid- and
  long-horizon signals before calling the launch
  permanent.
- **Use Exercise 3's WTP evidence to pick the
  specific price point.** If the Range of Acceptable
  Prices from Van Westendorp was $55–$85 and the
  Gabor-Granger knee was around $75, the brief tests
  a specific point in that range (say $69 or $79) —
  not a point outside the range, and not a vaguely
  "higher price."
- **Pick a primary metric that moves on your
  timeline.** New-signup ARPU moves in weeks. LTV at
  horizon moves in months. Trial-to-paid moves in
  days to weeks. Pick the fastest-moving leading
  indicator that captures the mechanism; put the
  slower-moving ones as guards.
- **Watch the median-account gross margin.** For AI-
  substrate products, a price change that lifts
  revenue but tanks the median-account gross margin
  (because higher-paying accounts drive heavier
  usage) is a trap. Reference
  [Lecture 6](../lectures/06-ai-product-monetization-models.md)
  if the change is on an AI-substrate feature.
- **Draft the rollback with the same care as the
  launch.** The brief that doesn't document how to
  roll back is the brief whose author secretly
  doesn't believe the experiment could fail.

## Acceptance criteria

- The **change** is described concretely enough that
  an engineer and a head of marketing could ship it
  from the paragraph alone.
- **A/B-safety classification** is explicit (safe /
  uncomfortable / not safe) with a one-sentence
  justification; the cohort definition is
  unambiguous.
- **Hypothesis** is in the Lecture 5 shape with all
  slots filled — change / cohort / primary metric /
  E (relative + absolute) / W / three guard horizons
  / mechanism.
- **Guard metrics** are organized under
  short-horizon / mid-horizon / long-horizon
  headings, each with named numeric thresholds (not
  wishes), and each horizon has a stated read date.
- **MDE** is calculated at three Δ scenarios (10% /
  20% / 50% relative) with inputs, intermediate
  math, and resulting *n* and duration. The duration
  is checked against actual traffic, with the
  fallback plan named if duration is infeasible.
- **Launch rule** is a pre-registered decision table
  (SHIP / HOLD / KILL / STAGED ROLLOUT) with
  specific conditions.
- **Grandfathering memo** walks the four Lecture 5
  shapes and defends the pick with a trust-vs-ARPU
  reason; names who is affected and what breaks if
  the choice is wrong.
- **Communication plan** names top-N treatment,
  smaller-customer treatment, GTM / finance
  briefing, and timing.
- **Rollback plan** is written, including make-good
  for anyone charged under the new pricing before
  rollback.
- **Risks** section names a counter-move for each of
  the seven Lecture 5 failure modes.

## Common failure modes

- **A/B hypothesis for a change that isn't A/B-safe.**
  The brief writes a per-user split for an
  existing-customer price raise. The change is a
  cohort change, period; writing it as an A/B is
  Lecture 5's "never do this" case.
- **Guard metrics without numeric thresholds.** "Churn
  shouldn't go up" is a wish; "contraction MRR does
  not exceed 2× the pre-change weekly baseline for
  two consecutive weeks" is a trigger.
- **No long-horizon guard.** Brief covers 2-week and
  8-week guards; declares victory at week 8. Lecture
  5's pre-registered 12–52-week horizon is missing.
  Add it, even if the read is a cohort-retention-
  shape proxy rather than LTV directly.
- **Peeking-then-extending.** The brief says fixed
  horizon; the team peeks at day 7 and extends to
  day 28 to "get significance." Pricing experiments
  are not exempt from the mod-005 Lecture 4 peeking
  rules.
- **Grandfathering by default, not by decision.** The
  memo picks "time-bounded, 12 months" because
  that's the Lecture 5 default without applying the
  trust-vs-ARPU trade-off to the specific case. The
  default is a starting point, not a conclusion.
- **No rollback plan.** The brief treats the
  experiment as if it couldn't fail. Every pricing
  experiment can fail; write how you'd back out.
- **Communication plan with no top-N treatment.** The
  brief sends a mass email and calls that
  "communication." The top-100 accounts drive a
  disproportionate share of revenue and trust;
  personal outreach is not optional.
- **MDE theatre.** The calculation is in the brief
  but the team runs the experiment at 1/10 the
  required sample. Pre-register the duration *and
  honor it* — honoring the pre-registration is
  where discipline lives.
- **AI-substrate price change with no cost-model
  check.** A tier-price raise that lifts revenue but
  the heavier-usage accounts the new price attracts
  are gross-margin-negative. Reference
  [Lecture 6](../lectures/06-ai-product-monetization-models.md).

## Source alignment

The brief shape, three-horizon guards, grandfathering
discipline, and communication-plan requirement derive
from
[Lecture 5](../lectures/05-pricing-experiments-and-grandfathering.md),
which synthesizes Patrick Campbell / ProfitWell's
pricing-change writing with Kyle Poyar / OpenView's
tier-and-meter-migration essays
([paddle.com/blog/author/patrick-campbell](https://www.paddle.com/blog/author/patrick-campbell),
[growthunhinged.com](https://www.growthunhinged.com/)).
The underlying A/B discipline — hypothesis, MDE,
guards, peeking, SRM — derives from Ronny Kohavi,
Diane Tang & Ya Xu, *Trustworthy Online Controlled
Experiments*, Cambridge University Press, 2020,
Chapters 2, 3, 17, 21 —
[experimentguide.com](https://experimentguide.com/) —
and Evan Miller's calculator and essays —
[evanmiller.org/ab-testing/sample-size.html](https://www.evanmiller.org/ab-testing/sample-size.html)
and
[evanmiller.org/how-not-to-run-an-ab-test.html](https://www.evanmiller.org/how-not-to-run-an-ab-test.html).
The pricing-experiment-brief template is from
[Lecture 5](../lectures/05-pricing-experiments-and-grandfathering.md#the-pricing-experiment-brief).
