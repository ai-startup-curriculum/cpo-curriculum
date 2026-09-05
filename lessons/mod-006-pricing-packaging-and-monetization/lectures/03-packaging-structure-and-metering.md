# Lecture 3 — Packaging structure: good / better / best, seat vs. usage vs. hybrid

## The setup

Lecture 2 gave you the willingness-to-pay evidence.
This lecture is where that evidence becomes a **shape**
— a small set of SKUs, a meter, a set of feature gates,
and an upgrade path — that a sales team can carry to
market and a self-serve funnel can convert against.

The packaging shape is the load-bearing product
decision this module teaches. Get the shape right and
the pricing model tolerates 6× revenue growth, an
enterprise motion added on top of self-serve, and a
model-provider price change without a rewrite. Get the
shape wrong and every one of those inflection points
requires re-teaching customers and re-training sales.

The through-line, drawn across Ramanujam & Tacke
Chapter 6 (packaging), Kyle Poyar's writing on
usage-based pricing at OpenView (2020–2024), and the
Simon-Kucher good / better / best literature:

**Packaging is a three-question decision.** How many
tiers? What meter unit? What gates the upgrade? Everything
else — tier names, feature-inclusion matrix, above-fold
copy — is derived. The three questions are the load-
bearing ones.

## Question 1 — How many tiers?

The default answer for a founding-CPO packaging shape
is **three**: good, better, best. The reasoning, drawn
from Ramanujam & Tacke Chapter 6 and consistent across
the practitioner literature:

- **Three tiers create a middle**. With two tiers,
  every customer either takes the low-price entry or
  the high-price full package; there is no middle
  ground to negotiate to. Three tiers put a natural
  bias toward the middle option — the "compromise
  effect" from consumer choice psychology — which is
  where you can price for the median buyer.
- **Three tiers show a value ladder.** Customers infer
  what your product *is worth* from the range of your
  tiers, not from any one tier. A single $99 SKU
  looks arbitrary; a $29 / $99 / $299 ladder makes
  $99 feel like a considered choice at the middle of
  a defined range.
- **Three tiers absorb segment variance.** Different
  buyer segments land in different tiers naturally.
  Self-serve individuals in tier 1, mid-market teams
  in tier 2, enterprise in tier 3. You don't need
  four segments' worth of SKUs; three usually cover
  the mass of the distribution.

Common variants of the three-tier shape:

- **Free + 2 paid** (freemium): "Free / Pro / Team"
  or "Free / Pro / Business." The free tier is the
  acquisition channel; the two paid tiers are the
  monetization surface. Lecture 4 covers the free-
  tier design specifically.
- **3 paid + Enterprise** (the "four-tier that's
  really three plus a call-us"): "Starter / Growth /
  Business / Enterprise" where Enterprise is *"contact
  sales"* without a public price. The four-tier view
  fits the self-serve → enterprise transition without
  breaking the three-tier compromise mechanics.
- **Free + Pro + Contact us**: a common freemium
  variant that skips the middle paid tier when the
  self-serve buyer is a single-user prosumer and the
  team-scale buyer is enterprise-only.

When to depart from three tiers:

- **Two tiers.** Justifiable when the product has one
  clear self-serve buyer and no meaningful upgrade
  path (rare at seed+). Also common as a *starter*
  packaging before you have enough segment evidence
  for a defensible middle.
- **Four or more tiers.** Justifiable when the segment
  cuts are genuinely distinct (individual vs. team
  vs. business vs. enterprise, each with different
  buyer, different budget, different feature needs).
  More often, four tiers is a symptom of a team that
  couldn't decide what to leave out; the fourth tier
  should be tested against merge candidates.

**The rule.** Default to three tiers. Depart with a
specific segment-based reason. A packaging shape that
is *"four tiers because we couldn't agree"* is a
Ramanujam-shape hidden-gems failure waiting to happen.

## Question 2 — What is the meter?

The meter is the unit that converts customer value
into revenue. It is the deepest packaging choice you
make, and — in the founding-CPO's world — the one most
often chosen by inheritance rather than analysis. The
main options:

### Per-seat (per-user)

Charge per named user account. Standard for B2B SaaS
targeting collaborative teams (Slack, Notion, Figma,
Linear).

- **Fits when**: the product's value scales with the
  number of humans using it, and adding a user has
  low marginal cost to serve.
- **Breaks when**: the product's value scales with
  *use* rather than users (an analytics tool used by
  1 person to process 1M rows/day generates the same
  value at 1 seat as 10 seats), or when the buyer
  actively works to reduce the seat count via shared
  logins.

### Per-usage (metered / consumption)

Charge per unit of consumed value. Common units:
API calls, GB stored, GB transferred, documents
processed, minutes of transcription, tokens consumed.

- **Fits when**: usage varies wildly across customers
  and correlates strongly with cost-to-serve, or
  when the value the customer derives is proportional
  to consumption.
- **Breaks when**: usage is not predictable enough
  for customers to budget (procurement teams reject
  bills that surprise them; individual buyers stop
  using the product to avoid the bill), or when the
  cost-to-serve does *not* correlate with usage (a
  fixed-cost architecture with usage-based pricing
  produces margin whiplash).

### Hybrid (seat + usage)

Charge a base per-seat platform fee plus a per-usage
overage or a metered add-on. Common in modern B2B
data / AI tooling (Snowflake, Databricks, Twilio,
many LLM-adjacent products).

- **Fits when**: the product has both a fixed access-
  right value (users need the tool to log in and
  work) and a variable consumption value (the tool
  processes different volumes for different
  customers).
- **Breaks when**: the hybrid model becomes
  incomprehensible to buyers (three separate meters
  produce a bill nobody can predict), or when the
  usage component overwhelms the seat component and
  the seat fee becomes a rent-seeking tax.

### Flat-fee (per-account, per-month)

Charge a fixed price per organization per period.
Common in low-touch SMB products where the buyer
wants one predictable line item.

- **Fits when**: usage is bounded (a website has one
  homepage; a payroll runs monthly), and the buyer's
  primary need is predictability.
- **Breaks when**: the product's costs grow with
  usage but the price does not, producing gross-
  margin compression at scale.

### Per-outcome (value-based)

Charge per unit of customer value delivered. Common
in AI-substrate products where the outcome is
measurable — resolved tickets, booked meetings,
qualified leads, dollars recovered. Emerging as a
first-class option in AI-agent monetization; see
[Lecture 6](06-ai-product-monetization-models.md).

- **Fits when**: the outcome is measurable,
  attributable, and repeatable, and the customer is
  sophisticated enough to buy on unit economics
  rather than access.
- **Breaks when**: the outcome is hard to attribute
  (was it your agent or the human?), the customer
  can't predict monthly cost, or margin collapses
  because per-outcome cost of goods sold outpaces
  the per-outcome revenue (a specific AI-monetization
  failure mode; Lecture 6).

## Choosing the meter — Ramanujam's value-metric test

Ramanujam & Tacke Chapter 6 introduces the concept of
the **value metric**: the unit that best correlates
with the value the customer derives. The test:

1. **Name the value the customer derives.** *"A
   marketing analyst uses our tool to publish weekly
   reports."*
2. **Ask what quantity scales with that value.** More
   analysts? More reports? More data sources? More
   audience? Pick the one that grows monotonically
   with what the customer would say is *"more
   valuable to me."*
3. **Test it against the failure modes above.** Does
   it produce a comprehensible bill? Does it map to
   your cost-to-serve? Does it produce predictable
   monthly cost for the buyer?

The value-metric test frequently overturns the
inherited meter. A team that inherited a per-seat
meter from a founder-CEO deck often finds, on the
value-metric test, that the value scales with
*reports published* or *data sources connected* — and
the seat meter is producing customer behavior (shared
logins, artificial seat consolidation) that hides
the real usage signal.

## Question 3 — What gates the upgrade?

The final structural question is: what feature or
capacity distinction moves a customer from tier 2 to
tier 3? Three gate shapes:

### Feature gates

*"Enterprise SSO is only in Business tier."* The
higher tier includes features the lower tier does
not. Common gates: SSO, audit log, role-based access
control, API access, admin controls, priority
support, custom domains, white-label, SLA guarantees.

- **Works well** for features with clear
  segment-level demand (enterprise buyers need SSO;
  individual buyers don't).
- **Fails** when the gated feature is one the middle-
  tier buyer expects at their price point (gating
  audit log behind Enterprise on a $500/mo product
  produces a churn wave).

### Capacity gates

*"Growth tier includes 10,000 events/month;
Business tier includes 100,000."* Same feature set
across tiers; higher tier includes more of the
value-metric quantity.

- **Works well** when the value metric is
  quantitative and the customer's needs scale
  predictably.
- **Fails** when the caps are set arbitrarily
  (customers hit the cap by month 3 of a 12-month
  contract) or when overage handling is punishing
  (surprise bill vs. graceful throttle).

### Support / SLA gates

*"Business tier includes 24×5 support; Enterprise
tier includes 24×7 with 1-hour SLA."* The product is
the same; the wrap-around service level differs.

- **Works well** as a *complement* to feature or
  capacity gates, not as a standalone
  differentiator. A tier ladder that's only a
  support-level ladder feels manipulative.

### Hybrid gate (the common case)

Most working three-tier packages combine all three:
tier 1 has capacity limits and no SSO; tier 2 has
higher capacity and basic support; tier 3 has
unlimited capacity, SSO, audit log, and priority
support.

## The good / better / best value ladder

Ramanujam & Tacke's Chapter 6 lays out a specific
discipline for authoring the good / better / best
ladder that avoids the two common failure modes
(everything in one bloated middle tier; everything in
Enterprise). Simplified for founding-CPO use:

1. **List every feature the product has.** Not
   marketing-language features; capabilities.
2. **For each feature, ask "who needs this and would
   pay for it?"** Buyer persona, use case, willingness-
   to-pay signal (from Lecture 2). Score:
   - **Everyone** → Good tier (the floor).
   - **Most, especially teams** → Better tier (the
     middle).
   - **Sophisticated / large buyers only** → Best
     tier (the ceiling).
   - **Nobody actually uses / wants this** → cut.
3. **Design the tier boundaries around the value
   metric.** The Good tier's capacity limit should be
   *just below* where the Better tier's buyer
   naturally operates; the Better tier's limit
   should be just below where the Best tier's buyer
   naturally operates. Buyers grow into the next tier
   through natural product use, not artificial
   crippling.
4. **Publish the feature-inclusion matrix.** A
   table with tiers as columns and features as rows,
   ticks where included. This is not marketing
   copy; it's a product artifact. Reviewers should
   be able to determine which tier they need without
   ambiguity.
5. **Set the price ratio.** The classic good / better
   / best ratio is roughly 1 : 3 : 6 to 1 : 4 : 10
   (Better tier is 3–4× Good; Best tier is 2–3×
   Better). Larger ratios push middle-tier adoption
   (the compromise effect); smaller ratios flatten
   the ladder and reduce the upgrade signal.
   <!-- needs-research: cite specific Simon-Kucher / Ramanujam benchmark on typical GBB ratios rather than a general practitioner-heuristic range. -->

## Common packaging failures

Six failure modes that recur across founding-CPO
packaging attempts, drawn across Ramanujam & Tacke,
Poyar's essays, and the ProfitWell / Paddle post-
mortem writing:

- **Feature bloat in the middle tier.** The team,
  afraid Better won't sell against Good, loads it
  with everything Best has too. Result: no reason to
  buy Best; Best sits at 5% of accounts and every
  large buyer negotiates down to Better.
- **Empty middle tier.** The opposite: Better has
  nothing distinctive. Result: everyone stays at
  Good, and the value ladder implodes.
- **Enterprise-only gate on a self-serve feature.**
  SSO, audit log, and API access gated to
  Enterprise-only when self-serve customers
  legitimately need them at team scale. Result: a
  wave of "I need X but can't justify $50k" support
  tickets and a competitive-loss reason on every
  enterprise deal.
- **Punitive overage.** Capacity limits set low with
  surprise-bill overage. Result: usage cliff (users
  turn off the feature to avoid the bill), NPS
  crash, and a specific class of "I got a surprise
  invoice" churn.
- **Meter that doesn't match cost.** Per-seat pricing
  on a product where the cost scales with API
  volume; result: 20% gross margin on high-usage
  customers.
- **Meter that doesn't match value.** Per-API-call
  pricing on a product where the customer's value
  scales with *what the API produces* (documents
  reviewed, revenue recovered). Result: the customer
  reasonably asks *"why am I paying more when I'm
  running the same workflow more efficiently?"* —
  and starts to optimize *for lower usage*, which is
  the opposite of what the product designer wanted.

## The Simon-Kucher price / value alignment

A useful sanity check on the packaging shape,
adapted from the Ramanujam / Simon-Kucher visualization
tools: plot each tier's **relative price** against its
**relative value** (as estimated from the WTP research
and the feature-inclusion). The three points should
lie on an increasing line — more expensive tiers
deliver more value. Common failures show up
graphically:

- **Better priced above the line** — priced too high
  for its value; buyers skip past it.
- **Better priced below the line** — priced too low;
  buyers land there when they should be in Best,
  eroding revenue.
- **Best priced far above the line** — priced high
  without proportionate value; buyers negotiate down
  to Better, and Best becomes a rare closed deal.

The tool is directional at small N, but the shape of
the line is a fast visual read on whether the
packaging shape is coherent.

## What the CPO does personally

- **Authors the packaging shape.** Number of tiers,
  the meter, the gate structure. Not marketing.
- **Runs the value-metric test.** Not the meter you
  inherited; the meter the value-metric test justifies.
- **Owns the feature-inclusion matrix.** Every row
  and column decision is a product decision.
- **Sets the price ratios.** With WTP evidence from
  Lecture 2 and finance-model constraints consumed
  from
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum).
- **Defends the packaging against custom-deal drift.**
  Every custom deal that doesn't fit any SKU is a
  signal — either the packaging is wrong (fix it) or
  the deal is out-of-strategy (decline it). Custom-
  deal accumulation is how packaging silently rots.

## What the CPO consumes from marketing and sales

- **Tier names and copy.** Marketing writes them
  within the packaging shape the CPO gave them.
- **Competitive comparison matrix.** Marketing curates;
  the CPO reads to check the packaging fits the
  competitive landscape.
- **Deal-level friction reports.** Sales reports which
  features prospects ask for that aren't in the
  bought tier, which gates cause deal-cycle friction,
  which competitors' packages come up. The CPO reads
  this as continuous packaging discovery signal.

## Boundaries this lecture keeps

- **Freemium vs. free-trial vs. reverse-trial** — the
  entry-motion choice that sits *on top* of the
  packaging structure — is
  [Lecture 4](04-free-trial-freemium-reverse-trial.md).
- **Pricing experiments** — how you'd A/B a new
  packaging shape or a new tier price — is
  [Lecture 5](05-pricing-experiments-and-grandfathering.md).
- **AI-product-specific meter design** — credits,
  outcome-based, cost-plus vs. value-based — is
  [Lecture 6](06-ai-product-monetization-models.md).
  This lecture teaches the general meter vocabulary;
  the AI-substrate variants are Lecture 6's job.
- **DPA / zero-retention / on-prem as a packaging
  tier** is [Lecture 7](07-enterprise-dpa-zero-retention-on-prem-gating.md).
- **Contract-level SKU customization** for enterprise
  deals — non-standard order-form terms, custom
  metering, floor / ceiling / usage-band pricing —
  is level-30 GTM work owned by
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum).
  The CPO authors the ladder; sales negotiates
  within it.

## Takeaways

- **Packaging is a three-question decision**: how
  many tiers, what meter, what gates the upgrade.
  Everything else is derived.
- **Default to three tiers** — the good / better /
  best shape — with Enterprise as a "contact us"
  fourth tier when a sales-assist motion exists.
- **The meter is the deepest choice.** Seat, usage,
  hybrid, flat, or outcome. Test with Ramanujam's
  value-metric test: which quantity scales with
  customer value, produces a comprehensible bill,
  and matches cost-to-serve.
- **Gate the upgrade with a mix**: feature gates for
  segment-differentiated needs, capacity gates for
  quantitative value metrics, support / SLA gates
  as a complement. Never as a standalone
  differentiator.
- **Price ratios** in the roughly 1 : 3 : 6 to
  1 : 4 : 10 range push the compromise effect toward
  the middle tier; flatter ratios weaken the ladder.
- **Watch for six failure modes**: bloated middle,
  empty middle, over-restrictive Enterprise gates,
  punitive overage, meter-cost mismatch, meter-
  value mismatch.
- **Plot price against value across tiers**. The line
  should be increasing and roughly straight; kinks
  and steep steps are packaging problems.

Lecture 4 turns to the **entry-motion** that sits on
top of the packaging shape — freemium vs. free-trial
vs. reverse-trial, and the seam where acquisition
becomes monetization.
