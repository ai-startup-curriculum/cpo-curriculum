# Lecture 1 — Pricing and packaging as a product surface

## The setup

The single most common founding-CPO failure on
monetization is not making a wrong pricing choice. It is
not making a pricing choice *at all* — treating the
price and the packaging as somebody else's problem
(marketing's, sales', the founder-CEO's) and inheriting
whatever ended up on the pricing page. The result is a
product whose *shape* was designed by the CPO but whose
*compensation model* was designed by whoever wrote the
first deck.

Madhavan Ramanujam, in *Monetizing Innovation: How Smart
Companies Design the Product Around the Price*
([Simon-Kucher & Partners / Wiley, 2016](https://www.wiley.com/en-us/Monetizing+Innovation%3A+How+Smart+Companies+Design+the+Product+Around+the+Price-p-9781119240860)),
frames this as the "design the product around the price"
inversion. Most companies design the product first, ship
it, and then hand it to marketing to price. The Simon-
Kucher position, drawn from decades of consulting on
launch-pricing failures, is that this sequence produces
one of four specific failure shapes — features nobody
will pay for, an undifferentiated me-too product, a
value proposition mispackaged as a single SKU, or a
product priced against cost rather than value — every
one of which is a product-design failure diagnosed as a
pricing failure.

The response is to treat pricing and packaging as a
**product surface**: an artifact the CPO owns, iterates
on with the same discovery / delivery discipline used
for the primary product surfaces, and defends with the
same evidence base.

This lecture is the framing lecture for the module. It
does not teach a specific pricing method. It teaches
*what pricing-as-a-product-surface means*, *what the
CPO owns vs. delegates*, and *how to reason about the
handoff to marketing and sales* — so the rest of the
module's techniques land inside a coherent
responsibility model.

## Ramanujam's four monetization failures

*Monetizing Innovation* opens by cataloging four failure
modes, drawn from Simon-Kucher's consulting engagements.
Each is a product decision misdiagnosed as a pricing
one. Paraphrased from Ramanujam & Tacke, Chapter 1:

- **Feature shocks.** The product ships loaded with
  features the team assumed customers would pay a
  premium for, and customers do not. The team's
  willingness-to-pay evidence was assembled after the
  feature scope was locked. Cure: run WTP research
  *during* discovery, not after launch.
- **Minivations.** The product ships as a stripped-down
  version of its potential, priced conservatively, and
  captures a small fraction of the value it creates.
  The team was afraid of a high price on limited
  evidence. Cure: distinguish willingness-to-pay from
  price-anxiety in the founder-CEO's head.
- **Hidden gems.** A specific feature or use case would
  command a premium if packaged separately, but it's
  buried in a single SKU. Cure: packaging (Lecture 3)
  as a first-class discipline, not an afterthought.
- **Undead products.** Features exist that nobody uses
  and nobody would pay for, kept in the SKU because
  nobody removed them. Cure: the kill-list discipline
  from
  [mod-002](../../mod-002-opportunity-assessment-and-prioritization/README.md),
  applied to the SKU.

Each failure diagnoses upstream: the team did not run
WTP research early, did not think about packaging
separately from features, did not distinguish price
courage from price recklessness, did not prune the SKU
against usage evidence. All four are product-design
failures. The pricing page is where they become
*visible*, not where they *originate*.

## What "pricing as a product surface" means concretely

The founding-CPO version of Ramanujam's framing is
five commitments the CPO makes:

1. **The CPO owns the packaging shape.** Which SKUs
   exist, what each SKU includes, what feature gates
   the upgrade. Not marketing. Not sales. Not the
   pricing-page copywriter. The SKU ladder is a
   product artifact the same way the onboarding flow
   is.
2. **The CPO owns the meter.** What unit converts
   customer value into revenue — a seat, an active
   user, an API call, a document processed, a
   ticket resolved, a credit. The meter is the
   deepest packaging choice a company makes; it
   determines the shape of the customer relationship
   for years. Wrong meter is the failure the seed →
   Series-B transition most often exposes.
3. **The CPO runs willingness-to-pay research as a
   discovery instrument.** Van Westendorp, Gabor-
   Granger, and small-N conjoint (Lecture 2) sit
   inside the weekly discovery cadence, alongside
   the interview craft from
   [mod-001](../../mod-001-customer-discovery-to-pmf/README.md).
   Not an annual marketing-led exercise.
4. **The CPO runs pricing experiments as product
   experiments.** Hypothesis, cohort, guard metrics,
   launch rule (Lecture 5). Not "let's try a higher
   price on the site and see what happens" — the
   same discipline as any A/B, plus the grandfathering
   decisions that don't exist for feature experiments.
5. **The CPO defends the pricing choice to the finance
   model, not the finance model to the pricing
   choice.** Gross margin, CAC-payback, and LTV are
   real constraints, and the CPO reads the finance
   model well enough to defend the pricing choice
   inside them. But the direction of the debate is
   *"here is the willingness-to-pay evidence, here is
   the packaging shape that captures it, and here is
   the finance model that results"* — not *"finance
   said 60% gross margin, so charge $X."*

Every technique in this module lands inside one of
these five commitments. If a technique doesn't
strengthen at least one, it isn't a founding-CPO
technique — it's a pricing-consultant technique for a
different stage.

## Kyle Poyar and the PLG pricing frame

Ramanujam's book was written before product-led growth
was a mainstream go-to-market motion, and its examples
skew toward enterprise-priced SaaS and hardware. The
practitioner literature that filled the gap for PLG
pricing — the freemium / free-trial / reverse-trial
mechanics, the usage-based-pricing transition, the
"pricing page as growth surface" mindset — is Kyle
Poyar's writing at OpenView (2018–2024, now continued at
*[Growth Unhinged](https://www.growthunhinged.com/)*).

Poyar's core moves for the founding-CPO reader are:

- **Pricing page as an experimentation surface.** The
  pricing page has traffic, conversion, and a decision
  outcome; treat it like any other high-intent product
  page. Iterate on tier names, feature-inclusion
  matrices, comparison anchors, and above-fold offer
  the same way you iterate on onboarding.
- **The usage-based-pricing transition.** As of 2020s
  benchmarks, a meaningful share of B2B SaaS has moved
  from pure per-seat to hybrid seat + usage models.
  The shift is not a pricing-page cosmetic change; it
  requires an event-collection pipeline, a metering
  system, an invoice engine that can bill for
  fractional consumption, and product surfaces that
  make usage visible so customers don't get surprise
  bills.
  <!-- needs-research: cite specific OpenView State of Usage-Based Pricing report percentages and year for the "meaningful share" claim once independently verified. -->
- **The three PLG entry motions.** Free-trial, freemium,
  reverse-trial (Lecture 4). Each has a distinct
  conversion-rate benchmark, a distinct product-shape
  requirement, and a distinct failure mode. Choosing
  the wrong entry motion is the pricing-choice most
  often made by inheritance rather than analysis.

Poyar's writing is a practitioner corpus — read it
weekly rather than end-to-end. The reading list in
[resources.md](../resources.md) links the specific
essays used through Lectures 3 and 4.

## Patrick Campbell and cohort-based willingness-to-pay

The third foundational reference this module leans on
is Patrick Campbell's work at ProfitWell (now Paddle),
which industrialized willingness-to-pay research from a
one-off consulting engagement to a *continuous* signal
tracked cohort-by-cohort. The methodological through-
line, drawn across Campbell's talks and the ProfitWell
research posts:

- **WTP is a segment-specific quantity, not a company-
  wide one.** The right price for one buyer persona is
  usually the wrong price for another. Averaging across
  segments produces a price that overcharges the low-
  willingness segment and undercharges the high one.
- **WTP moves over time.** Competitive alternatives
  shift, feature parity shifts, purchasing environments
  shift. The WTP number that was defensible in month 1
  will be stale by month 12. Cohort the research, refresh
  it quarterly or semi-annually.
- **Small samples lie in specific, predictable ways.**
  Van Westendorp with N=20 will produce a plausible-
  looking Optimal Price Point that shouldn't be
  believed. Gabor-Granger with a leading question will
  produce an upward-biased purchase-intent curve.
  Lecture 2 is explicit about the honest reads.

Campbell's team also wrote extensively on **pricing
change guardrails** — the metrics you watch after a
pricing change and the ways a nominally-successful
change (new-signup ARPU up 15%) can hide catastrophic
side effects (existing-account NRR down 8% because the
new price triggered a wave of downgrades). Lecture 5 is
where those guardrails become the CPO's pricing-
experiment discipline.

The Campbell / ProfitWell canon is deep and largely
free; the specific essays used through the module are
in [resources.md](../resources.md).

## What the CPO owns vs. what marketing and sales own

The pricing-as-product-surface framing does not mean
the CPO takes over marketing and sales. It means the
CPO owns the *artifact* those functions carry to
market. Here is the boundary this module keeps.

### The CPO owns

- **Packaging shape** — SKU count, SKU names,
  feature-inclusion matrix, upgrade / downgrade path,
  the value metric that determines which SKU a
  customer lands in.
- **The meter** — the unit that converts customer
  value into revenue.
- **Willingness-to-pay evidence** — the WTP research
  program, the segment-level WTP numbers, the
  refresh cadence.
- **The pricing experiment program** — hypothesis
  writing, cohort selection, guard metrics, launch
  rules, grandfathering decisions.
- **AI-substrate monetization model** — cost-plus vs.
  value-based vs. outcome-based, credit / metering
  shape, deployment / DPA / retention tier
  (Lectures 6, 7).

### Marketing owns

- The **pricing-page copy** and layout, within the
  packaging shape the CPO gave them. (The CPO usually
  co-designs the page; marketing owns the ship.)
- **Positioning and messaging** for each SKU. The CPO
  authors the value hypothesis; marketing authors the
  language.
- **Competitive alternative research** at the
  marketing-collateral depth — battlecards, feature
  comparisons, third-party analyst positioning.
- **The pricing-page acquisition funnel** — SEO,
  paid, above-fold conversion. The CPO reads the
  funnel; marketing runs it.

### Sales owns

- **Deal-level negotiation** within the SKU ladder and
  the discounting bounds the CPO / finance set.
- **Enterprise contracting** — MSA, order form, DPA,
  order-form addenda. Legal drafts the language;
  sales carries it.
- **Deal desk discipline** — who can approve what
  discount, what non-standard terms escalate, how
  custom deals get logged.
- **The transition from PLG to sales-assist** for
  high-touch accounts. The CPO defines the
  qualification signal (usage over threshold, seat
  count over threshold); sales runs the motion.

The founding-CPO test: if pricing on the site changed
tomorrow and no one asked you, you don't own it. If
sales sold a custom deal that didn't fit any SKU and
no one asked you, you don't own it. If either happens,
that is the ownership fight
[mod-007](../../mod-007-working-with-founders-eng-and-gtm/README.md)
teaches you how to have.

## The founder-CEO conversation

Pricing tends to be a founder-CEO-owned surface at
pre-seed and early seed by default. The founder set
the price. The founder wrote the pricing page. The
founder made every custom-deal exception. Taking
pricing over as the first CPO is a small ownership
transition inside a larger one, and it goes poorly if
done as a power move.

The productive move: bring the founder-CEO the *first
piece of pricing-as-a-product-surface evidence* — a
Van Westendorp study on the current customer base,
say, or a good / better / best packaging spec that
addresses a specific downgrade / churn problem — and
use it to frame the ownership transition as *"I'll run
the research and the experiments; you approve the
model."* Founders rarely resist that shape. They
resist *"I'll own pricing now."*

This is a
[mod-007](../../mod-007-working-with-founders-eng-and-gtm/README.md)
craft point, not a mod-006 one. The pricing artifact
you bring — Exercise 1's monetization model memo — is
mod-006's job. The relationship craft that lands it is
mod-007's.

## What this module treats as background

Two backgrounds this module assumes and does not
re-teach:

- **The base commercial motion** — how enterprise
  sales cycles work, what stages a deal goes through,
  what a deal desk does, how procurement engages, how
  contracts get red-lined — is
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum)
  (level 30). This module names the artifacts the
  motion carries (SKUs, meter, DPA tier); the motion
  itself is that curriculum's job.
- **The unit-economics math** — LTV, gross margin,
  CAC-payback, magic number, Rule of 40 — is
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum)
  (level 40). This module treats those numbers as
  *constraints the pricing model must respect* and
  as *guard metrics for pricing experiments*
  (Lecture 5), but does not derive them.

If you don't yet know what "CAC-payback" means or how
gross margin is computed for a SaaS company, work at
least the first pass of the finance & fundraising
curriculum's unit-economics chapter before Exercise 4.
Lecture 5's guard-metric discussion assumes it.

## Takeaways

- **Pricing and packaging are a product surface** the
  CPO owns, not a marketing exercise. Ramanujam's
  "design the product around the price" inversion is
  the founding framing.
- **Four monetization failures** (feature shocks,
  minivations, hidden gems, undead products) diagnose
  as product-design failures, not pricing-page failures.
- **The CPO owns five things**: packaging shape, the
  meter, WTP evidence, the pricing experiment program,
  the AI-monetization model. Marketing owns the copy
  and funnel; sales owns the deal-level motion.
- **Poyar's PLG pricing writing** is the practitioner
  reference for freemium / free-trial / reverse-trial
  mechanics and the usage-based-pricing transition
  (Lectures 3, 4).
- **Campbell's cohort-based WTP method** is the
  practitioner reference for treating willingness-to-
  pay as a continuous, segment-specific, refresh-
  quarterly signal (Lectures 2, 5).
- **The base commercial motion and the unit-economics
  math** are consumed from level-30 and level-40 peer
  curricula. This module names the artifacts and
  respects the constraints; it does not derive either.

Lecture 2 turns to the **willingness-to-pay research
methods** the CPO owns as discovery instruments — Van
Westendorp, Gabor-Granger, and small-N conjoint at the
sample sizes a pre-seed / seed team can actually field.
