# Lecture 5 — Pricing experiments with guard metrics, and when to grandfather

## The setup

By this lecture you have (from Lecture 2) willingness-
to-pay evidence, (from Lecture 3) a packaging shape
with a meter and tier gates, and (from Lecture 4) an
entry motion. You are about to change one of them —
raise a price, add a new tier, change the meter,
tighten a gate, launch a reverse trial where you had
freemium — and the question this lecture answers is:
*how do you run that change without breaking existing
customers or trapping yourself in an unrunnable A/B?*

The generic experimentation discipline is
[mod-005 Lecture 4](../../mod-005-metrics-experimentation-and-ai-evals/lectures/04-experimentation-at-pre-seed-to-series-a.md):
hypothesis, primary metric, guard metrics, minimum-
detectable-effect (MDE) sizing, launch rule. Pricing
experiments *include* all of that, plus three
specific complications the general regime does not
have:

1. **Some pricing changes are not A/B-safe.** Charging
   two customers different prices for the same
   product creates fairness, trust, and legal
   exposure. Some pricing changes have to be run
   as *cohort* changes (only new sign-ups from date D
   onward), not per-user A/B splits.
2. **Guard metrics are lagged.** A pricing change
   that looks great at week 2 (new-signup ARPU up
   15%) can look terrible at week 26 (LTV down 30%
   because the higher price attracted low-fit buyers
   who churn hard). Pricing experiments need long-
   horizon guardrails, not just short-horizon ones.
3. **Grandfathering is a design decision, not an
   afterthought.** When you raise prices, existing
   customers on the old price expect to keep it —
   sometimes forever, sometimes for a grandfather
   window. The grandfathering decision affects
   customer trust, expansion revenue, and — at scale
   — the pricing model's whole viability.

This lecture teaches the pricing-specific additions to
the mod-005 experimentation discipline.

## Which pricing changes are A/B-safe

The core question: can this pricing change be shown to
different users at the same moment, or does it need to
be applied consistently to a cohort?

### A/B-safe changes (per-user or per-session random)

- **Pricing-page presentation.** Tier order, tier
  naming, feature-inclusion matrix layout, above-fold
  copy, comparison anchors. The *packaging is the
  same*; the *presentation* varies. Standard A/B.
- **Trial length and structure.** 7 vs. 14 vs. 30
  day trial, credit-card-required vs. not, free-tier
  cap changes for *new sign-ups only*. Each user
  sees one variant; existing users are untouched.
- **Upgrade prompt copy and timing.** When and how
  the upgrade prompt fires inside freemium or the
  free tier of a reverse trial.
- **Discount and promo experiments** — a 20%-off
  first-month offer to a subset of new sign-ups
  is standard A/B territory.

### A/B-uncomfortable but sometimes-defensible

- **New-sign-up-only price changes**. Cohort A pays
  $49, Cohort B (also new sign-ups this week) pays
  $69. This is technically A/B safe (no user sees
  two prices), but produces awkward publicity if
  the two prices become public, and is
  operationally hard (support gets tickets when
  Cohort A learns about Cohort B). Common practice
  is to run this as *sequential cohorts* — Cohort A
  is all sign-ups from date D₁ to date D₂; Cohort B
  is D₂ to D₃ — with the site showing one price at
  a time. It's still an experiment; it's just not a
  concurrent A/B.

### Not A/B-safe (require cohort or all-at-once change)

- **Existing-customer price increases.** You cannot
  charge two customers on the same plan different
  prices for the same product. The change must be
  applied to a cohort or grandfathered.
- **Meter changes.** You cannot bill customer A per-
  seat and customer B per-usage for the same
  product. The meter migration must be
  synchronized.
- **Feature-gate changes on existing tiers.** If SSO
  moves from Team to Business tier, existing Team
  customers who had SSO expect to keep it. A/B is
  not the mechanism; grandfathering + migration
  program is.
- **Tier restructures.** Removing a tier, splitting
  a tier, merging tiers. Existing customers are on
  the old tier and must be mapped to the new one.

The rule: **if the change can be experienced without
affecting an existing customer's billing or feature
access, A/B is on the table. If it affects existing
customers, it's a cohort change with a grandfathering
plan.**

## Guard metrics for pricing experiments

The general guard-metric shape from
[mod-005 Lecture 4](../../mod-005-metrics-experimentation-and-ai-evals/lectures/04-experimentation-at-pre-seed-to-series-a.md#guard-metrics)
carries. Pricing experiments add specific guards that
lag the treatment by weeks to months. The set:

### Short-horizon guards (2–4 weeks)

- **New-signup rate.** Did the pricing change tank
  the top of the funnel? Common failure: raising a
  price lifts ARPU in the short term but drops
  sign-ups so far that MRR falls.
- **Trial-to-paid or free-to-paid conversion.** For
  freemium / trial changes, did the conversion
  rate hold?
- **Cart / checkout drop-off.** For pricing-page
  changes, did the flow from pricing page to
  activated account complete at the same rate?
- **Support ticket volume on pricing.** A pricing
  change that produces a wave of "why is this so
  expensive" or "I can't figure out which tier I
  need" tickets is a UX failure inside the pricing
  change.

### Mid-horizon guards (4–12 weeks)

- **Contraction MRR.** Existing customers downgrading
  because they saw the new pricing page and revised
  their tier choice.
- **Downgrade rate on new signups.** Signups that
  land in the top tier and downgrade to a lower one
  within their first billing cycle. High rate
  signals over-priced or over-featured top tier.
- **Cohort retention at week 4, week 8, week 12.**
  The retention curve for the treatment cohort
  compared to the control. Even if the immediate
  conversion looks fine, cohort retention that
  breaks below control is a signal that the higher
  price attracted worse-fit buyers.

### Long-horizon guards (12–52 weeks)

- **LTV at horizon.** Estimated customer lifetime
  value for the treatment cohort vs. control. This
  is the most important guard and — because it
  can't be measured directly at week 4 — usually
  proxied by cohort retention shape plus expansion
  MRR at 12 weeks.
- **Net Revenue Retention (NRR)** on the treatment
  cohort. Cohorts that pay more up front but
  expand less over 12 months are the classic
  pricing-optimization trap.
- **CAC payback period.** Cost to acquire a
  customer divided by the customer's monthly gross
  margin. A pricing increase that raises ARPU 20%
  but drops sign-ups 30% produces a longer CAC
  payback, not a shorter one.

The full unit-economics view is
[startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum)
level-40 work; the CPO reads it and treats it as
constraint, does not derive it.

### The lagged-guard problem

The specific pricing-experiment failure the mod-005
regime doesn't address by itself: **the primary
metric moves fast, the guards lag**. A pricing change
that raises new-signup ARPU 15% in week 2 looks like
a win. Twelve weeks later, cohort retention has
collapsed and LTV is down 30%.

Two responses:

- **Read the retention shape early.** By week 4, the
  treatment cohort's week-1 → week-4 retention curve
  is a leading indicator of the full LTV. A cohort
  that retains meaningfully worse than the control
  at week 4 is very unlikely to catch up. Don't wait
  for month 12.
- **Pre-register the horizon.** In the experiment
  brief (Exercise 4), state up front: *"We will
  read the primary metric at week 2, the mid-horizon
  guards at week 8, and the long-horizon guards at
  week 26. We will not roll the change out
  permanently until all three checkpoints clear."*
  Without pre-registration, the team calls the
  short-horizon win as the launch signal, and the
  long-horizon regression becomes someone else's
  problem.

## The grandfathering decision

When a pricing change affects existing customers, the
CPO faces a decision that no amount of A/B discipline
can substitute for: **do existing customers keep the
old price forever, keep it for a bounded window, or
move to the new price on the next renewal?**

The four common shapes:

### Full grandfather (existing customers keep old price forever)

*"All customers who signed up before date D pay the
old price for as long as they remain customers on
this plan."*

- **Pros**: maximum customer trust, no churn
  spike, no support-ticket wave.
- **Cons**: over 3–5 years the grandfathered cohort
  becomes an increasingly expensive drag on ARPU
  and NRR. A team that has grandfathered aggressively
  over many years often finds a substantial share
  of accounts paying legacy prices.
  <!-- needs-research: cite a specific ProfitWell / Paddle or OpenView data point on grandfathered-cohort ARPU drag over multi-year windows to replace the general "substantial share" claim. -->
- **Fits when**: the customer base is small and
  loyalty is a competitive moat; when the pricing
  change is meaningful (large % increase) and a
  churn spike would be catastrophic.

### Time-bounded grandfather

*"Existing customers keep the old price for 12
months from the change date; after that, they move
to the new price on their next renewal."*

- **Pros**: preserves short-term trust, resolves
  the ARPU drag on a known horizon, gives
  customers time to budget or negotiate.
- **Cons**: the 12-month cliff produces its own
  small churn wave; requires operational tracking
  ("this account's grandfather expires on
  2026-03-15").
- **Fits when**: the price change is moderate
  (10–30% increase); when a full grandfather
  would cause too much ARPU drag; when customer
  trust is important but not existential.

### Next-renewal migration

*"Existing customers keep the old price for the
remainder of their current billing period; the new
price applies at renewal."*

- **Pros**: fast resolution of the ARPU gap; no
  long grandfathered tail; consistent with how
  customers already think about pricing (contracts
  renew at whatever the price then is).
- **Cons**: annual customers get up to 12 more
  months at the old price (still a drag, but
  bounded); monthly customers see the change
  quickly and may churn.
- **Fits when**: the price change is small; when
  most customers are on monthly billing; when the
  team can absorb a short-term retention hit.

### Immediate migration

*"All customers pay the new price from date D
onward."*

- **Pros**: cleanest ARPU move; no operational
  grandfathering tracking; consistent story to
  the market.
- **Cons**: customer trust hit; support wave;
  potential churn spike; potential legal exposure
  depending on jurisdiction and contract terms
  (many contracts include "no price change
  without 30-day notice" clauses).
- **Fits when**: the price change is very small;
  when customer contracts explicitly allow it;
  when the alternative is business insolvency.

### The default recommendation

For a founding CPO with < 500 customers, the default
that best preserves trust while resolving the pricing
math is a **time-bounded grandfather** (6–12 months)
combined with **a proactive customer communication
program**: personal email from the CEO or CPO to the
100 largest customers explaining the change and
offering to discuss; automated email to smaller
customers with clear notice of the transition date;
in-product notice on next login.

The Patrick Campbell / ProfitWell writing on this is
extensive; the through-line is: **the price change
is the easy part; the communication is where trust
is preserved or broken.**

## The pricing experiment brief

The pricing-experiment brief the CPO authors before
running any change, adapted from the mod-005 Lecture 4
brief with pricing-specific additions:

```
PRICING CHANGE: <describe the change concretely — e.g., "raise Pro tier from $49/mo to $79/mo">

WHY: <the mechanism — what WTP evidence, competitor evidence, or unit-economics
constraint drives the change>

HYPOTHESIS
- If we <make change X> to <cohort Y>, we expect
- Primary metric M to move by ≥ Δ within window W
- Without guard metrics G₁…Gₙ breaking
- Because <mechanism Z>

COHORT & EXPOSURE
- Cohort: <new signups from date D | existing accounts A/B split | all customers immediately | grandfathered cohort>
- A/B-safety: <A/B-safe / cohort-only / all-or-none, with justification>
- Grandfathering: <full / time-bounded / next-renewal / immediate, with justification>

PRIMARY METRIC
- <one metric — e.g., new-signup ARPU, trial-to-paid conversion, MRR>
- Baseline: <current value>
- Expected direction and magnitude: <e.g., +15%>
- Read horizon: <weeks>

GUARD METRICS
- Short-horizon (2–4 weeks): <signup rate, trial-to-paid, checkout dropoff, pricing-related support tickets>
- Mid-horizon (4–12 weeks): <contraction MRR, downgrade rate, cohort retention week 4/8/12>
- Long-horizon (12–52 weeks): <cohort LTV or LTV proxy, NRR, CAC payback>

MDE / TRAFFIC
- <n per variant required for detection at α=0.05, 1-β=0.80, per mod-005 Lecture 4>
- Expected weeks to detection: <given current traffic>

LAUNCH RULE
- Ship if: <primary metric moves ≥ Δ AND no guard breaks its threshold at any read horizon>
- Hold if: <primary metric ambiguous OR any guard within noise of its threshold>
- Kill if: <primary metric moves in wrong direction OR any guard breaks its threshold>

COMMUNICATION PLAN
- To existing customers: <email, in-product, 1:1 for top N, timing>
- To marketing / sales: <internal briefing, updated collateral, deal-desk memo>
- To finance: <updated forecast, cohort-level revenue projections>

ROLLBACK
- If we ship and the change goes badly, how do we roll back?
  <price reversion for new signups + honor promise to affected cohort + comms plan>
```

The brief goes to the founder-CEO, head of GTM, and
finance before the change ships. Not as approval-
seeking; as forcing-the-decision-be-made-consciously.

## Common failure modes

Seven pricing-experiment failures that recur across
founding-CPO attempts:

- **The pricing-page A/B that's really a marketing
  A/B.** Team runs an A/B on pricing-page copy and
  reports the winner as a "pricing experiment." It's
  a conversion-page experiment; the *pricing* didn't
  change. Fine, but don't conflate it with pricing
  research.
- **Peeking on pricing experiments.** The team
  watches the primary metric daily and calls the
  winner at day 5. The variance on ARPU is high;
  early reads are unreliable. Same discipline as
  mod-005 Lecture 4; pricing experiments are not
  exempt.
- **Ignoring the lagged guard.** Team ships based
  on the week-2 primary-metric win, doesn't check
  cohort retention at week 8, discovers at month 6
  that the change tanked LTV. Pre-register the
  horizons.
- **A/B on prices that aren't A/B-safe.** Team
  runs different prices to different existing
  customers concurrently. Customer discovers the
  discrepancy on a forum or Reddit. Trust break.
  Never do this.
- **No grandfather when needed.** Team raises prices
  and applies immediately to all customers without a
  communication program. Churn spike, chargeback
  spike, and a permanent trust hit on the segments
  that noticed.
- **Grandfather forever without expiry.** Team
  grandfathers aggressively over many pricing
  changes, accumulates a large legacy cohort at
  now-unsustainable prices, and eventually faces a
  much harder cleanup.
- **Pricing change with no communication.** Even
  a technically-defensible change lands badly if
  customers discover it from the pricing page
  rather than from a proactive email. The change
  itself is not the trust breaker; the surprise is.

## What the CPO does personally

- **Authors the pricing experiment brief.** Every
  pricing change goes through the brief shape
  above.
- **Sets the grandfathering policy.** Not
  delegable — the decision affects customer trust,
  which affects everything.
- **Reads the retention curves at each horizon.**
  Week 2, week 4, week 8, week 12, week 26. The
  CPO looks at the cohort curves, not just the
  aggregate dashboard.
- **Runs the top-100 customer communication.** The
  CEO or CPO personally, not marketing, for the
  largest and highest-trust accounts. Not a mail
  merge; individual emails or calls.
- **Owns the rollback.** If the change goes badly,
  the CPO owns the reversion and the make-good.

## What the CPO consumes from finance and GTM

- **Unit-economics constraints.** Gross margin
  target, CAC payback target, LTV / CAC ratio
  target. Consumed from
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum);
  used as guard-metric thresholds.
- **Contract-level pricing exceptions.** Sales
  reports which enterprise contracts include
  price-hold clauses, which customers have MFN
  clauses, which prospects are mid-cycle at the
  old price and would be unfairly hit by
  immediate migration. The CPO reads these into
  the cohort design.
- **Competitor pricing intelligence.** Marketing
  curates; the CPO reads to check the direction
  and magnitude against category norms.

## Boundaries this lecture keeps

- **Base A/B experimentation discipline** (MDE
  sizing, guard metrics, peeking, ratio-metric
  variance) is
  [mod-005 Lecture 4](../../mod-005-metrics-experimentation-and-ai-evals/lectures/04-experimentation-at-pre-seed-to-series-a.md).
  This lecture is the pricing-specific additions.
- **Cohort retention analysis and LTV modeling** at
  depth are level-30 growth-analytics work owned
  by
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum);
  the LTV / CAC / gross-margin math at
  unit-economics depth is
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum)
  level-40. The CPO reads both; does not derive
  either.
- **Legal contract-clause implications** of pricing
  changes — MFN clauses, price-hold clauses, notice
  requirements — is legal-counsel work. The CPO
  identifies which contracts have implications; a
  lawyer interprets.
- **Enterprise contract renegotiation** — the actual
  conversation with a specific customer about
  their new price — is sales / CS work informed by
  the CPO's grandfathering policy.

## Takeaways

- **Not every pricing change is A/B-safe.** Rule:
  if it affects existing customers' billing or
  feature access, it's a cohort change with a
  grandfathering plan, not a per-user split.
- **Pricing guards are lagged.** Short horizon
  (signup rate, trial-to-paid), mid horizon
  (contraction MRR, cohort retention), long
  horizon (LTV, NRR, CAC payback). Pre-register
  the read horizons.
- **Read retention shape early**. Week-4 cohort
  retention is a leading indicator for LTV;
  don't wait until month 12 to notice a
  regression.
- **Grandfathering is a first-class decision.**
  Full / time-bounded / next-renewal / immediate,
  chosen with a trust-vs-ARPU trade-off in view.
  Default for founding CPOs: time-bounded (6–12
  months) with a proactive communication program.
- **The communication is where trust is
  preserved or broken.** Personal emails to top
  accounts; automated notice to smaller ones;
  in-product notice on next login. The price
  change is not the trust break; the surprise is.
- **The pricing-experiment brief** — hypothesis,
  cohort, guards at three horizons, grandfathering
  plan, communication plan, rollback — is the
  artifact every pricing change goes through.

Lecture 6 turns to **AI-product monetization** — the
cost-plus / value-based / outcome-based / credit-
metering choice — where all the above tools apply
against a substrate whose cost of goods sold does
not behave like classic SaaS.
