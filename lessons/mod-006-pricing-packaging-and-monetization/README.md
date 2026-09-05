# mod-006 — Pricing, Packaging, and Monetization as a Product Surface

> The founding CPO's sixth job — after finding pull
> (mod-001), ranking the queue (mod-002), authoring the
> multi-quarter strategy the roadmap makes concrete
> (mod-003), running the weekly discovery/delivery rhythm
> the roadmap ships inside (mod-004), and standing up
> the measurement regime that tells the team whether any
> of it worked (mod-005) — is deciding **how the product
> gets paid for**. Pricing, packaging, and the meter that
> converts usage into revenue are product surfaces. The
> CPO owns them, the same way the CPO owns onboarding
> and the primary workflow. Delegating them to marketing
> or sales is the specific mistake this module exists to
> prevent.

## Why this module exists

Ask a first-time founding CPO who owns pricing and the
answer will be one of three shapes. The first is *"the
CEO"* — the founder set the price on the back of an
envelope during a fundraise and no one has revisited it.
The second is *"marketing"* — the pricing page lives in
the marketing site's CMS and any change requires a
marketing sprint. The third, increasingly common in
2026, is *"the model provider decides"* — the AI feature
is priced cost-plus against the API bill, no one
measured willingness to pay, and margin compresses every
time OpenAI or Anthropic changes their price sheet.

None of these is pricing as a product surface. Pricing
as a product surface means: the CPO owns the packaging
shape (what SKUs exist, what each SKU includes, what
gates the upgrade), owns the meter (per seat, per usage
unit, per outcome, per credit), runs willingness-to-pay
research the same way they run discovery research, and
runs pricing experiments the same way they run product
experiments — with hypotheses, cohorting, guard metrics,
and the discipline that some pricing changes need
grandfathering rather than an A/B split.

Madhavan Ramanujam's *Monetizing Innovation* (Simon-
Kucher & Partners, 2016) is the canonical text for this
framing: *design the product around a defensible price,
not the price around a shipped product*. Kyle Poyar's
writing at OpenView (2018–2024) is the canonical
practitioner reference for product-led-growth pricing —
freemium vs. free-trial vs. reverse-trial, the
usage-based transition, hybrid metering. Patrick
Campbell's writing at ProfitWell (now Paddle) is the
canonical practitioner reference for willingness-to-pay
research at SaaS scale — Van Westendorp price-sensitivity
meter, Gabor-Granger, cohort-based price monitoring.

This module teaches the founding-CPO version of all
three, sized to the pre-seed → Series-B reality where
the CPO has 20–200 customers, not the 20,000 the
consultancy playbooks assume. It folds AI-product
monetization — cost-plus vs. value-based, outcome-based
vs. seat-based, credit / metering models, enterprise
DPA / zero-retention / on-prem gating — into the same
regime, because at CPO scope for a small AI-native team,
the monetization model *is* the packaging shape.

## Learning outcomes

By the end of this module you can:

1. **Frame pricing and packaging as a product surface** —
   Ramanujam's *Monetizing Innovation* shape, Poyar's
   PLG pricing writing, Campbell's willingness-to-pay
   research method — and defend the shift from
   marketing-owned pricing page to CPO-owned monetization
   model to the founder-CEO who used to own it.
2. **Design a packaging structure** — good / better /
   best tiering, seat vs. usage vs. hybrid metering,
   free-trial vs. freemium vs. reverse-trial — that
   survives the seed → Series-B transition without a
   rewrite, and reason about which structural mistakes
   force the rewrite anyway.
3. **Run willingness-to-pay research at pre-seed / seed
   scale** — Van Westendorp price-sensitivity meter,
   Gabor-Granger, conjoint at small N; interpret the
   results honestly (small samples lie, and Van
   Westendorp in particular over-produces a plausible-
   looking answer from underpowered data).
4. **Design pricing experiments the way you design
   product experiments** — hypothesis, cohorting, guard
   metrics (churn, downgrade, LTV, CAC-payback), launch
   / no-launch criteria — knowing which pricing changes
   are safe to A/B on new sign-ups and which require
   grandfathering existing accounts.
5. **Choose an AI-product monetization model** — cost-
   plus vs. value-based, outcome-based vs. seat-based,
   credit / metering models, enterprise DPA / zero-
   retention / on-prem gating as a packaging tier — and
   match the model to the buyer sophistication and the
   inference-cost profile.
6. **Consume** the deeper craft at the level boundaries —
   the base commercial motions (sales stages, contracts,
   deal desk) are
   [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum)
   (level 30); the LTV / gross-margin / CAC-payback /
   Rule-of-40 math pricing must respect is
   [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum)
   (level 40). The CPO authors the monetization model
   that the GTM motion sells and the finance model
   underwrites; the CPO does not author either of the
   latter.

## Prerequisites

- [mod-001](../mod-001-customer-discovery-to-pmf/README.md) —
  the discovery muscle. Willingness-to-pay research in
  this module (Lecture 2) is a specialization of the
  interview craft mod-001 teaches; running it without
  the base craft produces answers no one should act on.
- [mod-002](../mod-002-opportunity-assessment-and-prioritization/README.md) —
  the queue. Packaging changes compete for engineering
  cycles like every other bet.
- [mod-003](../mod-003-roadmap-outcomes-and-strategy/README.md) —
  the strategy the pricing model must be coherent with.
  A pricing model that pulls the product toward the
  enterprise while the roadmap points at self-serve
  will produce quarterly whiplash.
- [mod-005](../mod-005-metrics-experimentation-and-ai-evals/README.md) —
  the experimentation discipline (Lecture 4 of mod-005
  in particular). Pricing experiments in Lecture 5 of
  this module use the same MDE / guard-metric shape;
  the pricing-specific additions (grandfathering,
  cohort-vs-live-account split, LTV as a horizon-lagged
  guard metric) sit on top.
- One product you can name concretely, with at least a
  plausible current price and at least 5 real (or
  interview-derived) accounts. If your product has zero
  users and no pricing at all, work mod-001 first — the
  pricing question does not have a defensible answer
  yet.

## Syllabus

| # | Piece | Type | Est. time |
|---|---|---|---|
| 1 | [Pricing and packaging as a product surface](lectures/01-pricing-as-a-product-surface.md) | Lecture | 45 min |
| 2 | [Willingness-to-pay research at pre-seed → seed scale](lectures/02-willingness-to-pay-research.md) | Lecture | 60 min |
| 3 | [Packaging structure: good / better / best, seat vs usage vs hybrid](lectures/03-packaging-structure-and-metering.md) | Lecture | 60 min |
| 4 | [Free-trial, freemium, reverse-trial: the acquisition-monetization seam](lectures/04-free-trial-freemium-reverse-trial.md) | Lecture | 45 min |
| 5 | [Pricing experiments with guard metrics, and when to grandfather](lectures/05-pricing-experiments-and-grandfathering.md) | Lecture | 60 min |
| 6 | [AI-product monetization: cost-plus, value-based, outcome, credits, metering](lectures/06-ai-product-monetization-models.md) | Lecture | 60 min |
| 7 | [Enterprise DPA, zero-retention, on-prem as a packaging tier](lectures/07-enterprise-dpa-zero-retention-on-prem-gating.md) | Lecture | 45 min |
| 1 | [Monetization model authoring for one product](exercises/exercise-01-monetization-model-authoring-for-one-product.md) | Exercise | 3 hrs |
| 2 | [Good / better / best packaging drill](exercises/exercise-02-good-better-best-packaging-drill.md) | Exercise | 2 hrs |
| 3 | [Van Westendorp and Gabor-Granger drill](exercises/exercise-03-van-westendorp-and-gabor-granger-drill.md) | Exercise | 2 hrs |
| 4 | [Pricing experiment design with guard metrics](exercises/exercise-04-pricing-experiment-design-with-guard-metrics.md) | Exercise | 2 hrs |
| 5 | [AI-product monetization model drill](exercises/exercise-05-ai-product-monetization-model-drill.md) | Exercise | 2 hrs |
| R | [Resources — books, essays, and primary sources](resources.md) | Reference | — |

## How to work this module

Read the lectures in order. Lecture 1 fixes the *framing*
— pricing as a product surface the CPO owns — because
every exercise later assumes the founder-CEO and head of
marketing have not yet been convinced. Lecture 2 gives
you the *research muscle*: three willingness-to-pay
instruments sized to the samples a pre-seed / seed team
can actually field, and — critically — the honest
warnings about what those instruments cannot tell you.
Lectures 3 and 4 give you the *packaging muscle*: the
good / better / best tiering discipline, the seat vs.
usage vs. hybrid meter choice, and the free-trial /
freemium / reverse-trial acquisition-monetization seam.
Lecture 5 gives you the *experiment muscle*: pricing
A/Bs, guard metrics with LTV as a lagged signal, and
the grandfathering discipline that separates a legitimate
pricing change from a customer-trust break. Lectures 6
and 7 give you the *AI-monetization muscle*: how
cost-plus falls apart, how to design a value-based or
outcome-based meter that still lets you sell in year
one, and how enterprise DPA / zero-retention / on-prem
gating fits into the SKU ladder.

Do the exercises against a real product where you can.
Every exercise in this module benefits enormously from
being run against an actual pricing page and actual
customer accounts — even five real interviews are worth
more than fifty synthetic ones. If your product has zero
customers, work Exercises 1 and 2 against a plausible
product you know deeply (a product you use, a product
you nearly bought) and defer Exercises 3–5 until you
have real WTP data.

Exercises 1 → 5 build on each other. Exercise 1 authors
the monetization model — meter, packaging shape,
positioning. Exercise 2 drills the good / better / best
tier structure that Exercise 1 named. Exercise 3 runs a
small-N Van Westendorp + Gabor-Granger study against
your model. Exercise 4 designs the first pricing
experiment against real (or plausible) traffic. Exercise
5 works the AI-substrate monetization variant for one
feature.

## Deliverables

- One **monetization model memo** — packaging shape,
  meter choice, tier structure, positioning, the
  competitive alternatives you're anchored against, the
  reference-price research that grounds it
  ([Exercise 1](exercises/exercise-01-monetization-model-authoring-for-one-product.md)).
- One **good / better / best packaging spec** — three
  tiers, feature-inclusion table, the value-metric that
  determines which tier a customer lands in, the
  upgrade / downgrade path, the reason each tier's
  ceiling is where it is
  ([Exercise 2](exercises/exercise-02-good-better-best-packaging-drill.md)).
- One **willingness-to-pay research write-up** — Van
  Westendorp price-sensitivity results with Optimal
  Price Point and Range of Acceptable Prices, Gabor-
  Granger purchase-intent curve, an honest read of what
  the small sample can and can't tell you, the price
  hypothesis you'd take into the next experiment
  ([Exercise 3](exercises/exercise-03-van-westendorp-and-gabor-granger-drill.md)).
- One **pricing experiment brief** — hypothesis, cohort
  (new sign-ups only vs. all traffic), primary metric,
  guard metrics (churn, downgrade, contraction MRR,
  LTV-at-horizon), MDE / traffic requirement, launch
  rule, grandfathering decision
  ([Exercise 4](exercises/exercise-04-pricing-experiment-design-with-guard-metrics.md)).
- One **AI-product monetization model** for one feature
  — cost-plus vs. value-based vs. outcome-based
  reasoning, meter unit, inference-cost model, floor /
  ceiling / overage rules, the DPA / retention /
  deployment tier the model plugs into
  ([Exercise 5](exercises/exercise-05-ai-product-monetization-model-drill.md)).

## Boundaries this module keeps

- **PMF discovery** is
  [mod-001](../mod-001-customer-discovery-to-pmf/README.md).
  A product without PMF cannot be honestly priced;
  Lecture 2's willingness-to-pay research assumes at
  least segment-level pull.
- **Opportunity ranking** is
  [mod-002](../mod-002-opportunity-assessment-and-prioritization/README.md).
  Packaging changes compete for cycles like every other
  bet; this module does not re-rank the queue.
- **Roadmap strategy** is
  [mod-003](../mod-003-roadmap-outcomes-and-strategy/README.md).
  The pricing model must be coherent with the strategy;
  this module does not author the strategy.
- **General experimentation discipline** is
  [mod-005 Lecture 4](../mod-005-metrics-experimentation-and-ai-evals/lectures/04-experimentation-at-pre-seed-to-series-a.md).
  This module's Lecture 5 is the *pricing-specific*
  additions (grandfathering, cohort-vs-live split, LTV
  as lagged guard), not the base A/B craft.
- **AI eval regime and cost / latency / quality Pareto**
  are
  [mod-005 Lectures 6 and 7](../mod-005-metrics-experimentation-and-ai-evals/README.md).
  This module's Lecture 6 references the eval and cost
  models but does not re-teach them.
- **The founder / eng / GTM working relationship** — how
  the CPO wins the pricing-ownership fight in the first
  place — is
  [mod-007](../mod-007-working-with-founders-eng-and-gtm/README.md).
  This module teaches the *artifact* the CPO brings to
  that fight, not the influence craft.
- **Base commercial motion** — sales stages, deal desk,
  procurement, MSA / SOW / order-form structure,
  channel partnerships, PLG-to-SLG transition at
  operational depth — is level-30 work owned by
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum).
  The CPO authors the SKU ladder and the meter; the
  head of sales runs the deals against it.
- **LTV / gross-margin / CAC-payback / Rule-of-40 math**
  the pricing model must respect at unit-economics
  depth is level-40 work owned by
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum).
  The CPO reads the finance model well enough to defend
  a pricing choice against it; the CFO / head of finance
  authors it.
- **Legal contract language** — DPA templates, MSA
  clauses, indemnification, data-residency contract
  wording — is out of scope. Lecture 7 teaches which
  packaging tiers exist and what they gate; the actual
  contract language is authored by counsel.
- **Vertical pricing customs** — the fintech custody-fee
  model, healthcare per-member-per-month, security
  per-endpoint, telecoms per-minute — are candidate-
  supplied. This module teaches the meter-design
  vocabulary; the vertical customs are yours to
  research.

## Sources this module leans on

- Madhavan Ramanujam & Georg Tacke, *Monetizing
  Innovation: How Smart Companies Design the Product
  Around the Price*, Wiley, 2016 —
  [wiley.com/en-us/Monetizing+Innovation](https://www.wiley.com/en-us/Monetizing+Innovation%3A+How+Smart+Companies+Design+the+Product+Around+the+Price-p-9781119240860)
  and
  [simon-kucher.com](https://www.simon-kucher.com/en/insights/monetizing-innovation-book) —
  the canonical text for pricing-as-product-design and
  the source for the four "monetization failure" shapes
  in Lecture 1.
- Peter H. van Westendorp, "NSS-Price Sensitivity Meter
  (PSM) — A New Approach to Study Consumer Perception of
  Prices," 1976 ESOMAR Congress Proceedings —
  [rwconnect.esomar.org](https://ana.esomar.org/documents/nss-price-sensitivity-meter-psm-a-new-approach-to-study-consumer-perception-of-prices) —
  the original paper introducing the four-question price
  sensitivity meter used through Lecture 2 and Exercise 3.
- André Gabor & C. W. J. Granger, "Price as an Indicator
  of Quality: Report on an Enquiry," *Economica*, 33(129),
  1966 —
  [jstor.org/stable/2552031](https://www.jstor.org/stable/2552031) —
  the source paper for the purchase-intent laddering
  method that carries their names.
- Kyle Poyar, *Growth Unhinged* (Substack) and prior
  writing as VP Growth at OpenView, 2018–2024 —
  [growthunhinged.com](https://www.growthunhinged.com/)
  and archived at
  [openviewpartners.com](https://openviewpartners.com/blog/author/kyle-poyar/) —
  the practitioner reference for PLG pricing, freemium
  vs. free-trial vs. reverse-trial, and the usage-based-
  pricing transition used through Lectures 3 and 4.
- Patrick Campbell (ProfitWell / Paddle), pricing
  research writing 2016–2023 —
  [paddle.com/blog/author/patrick-campbell](https://www.paddle.com/blog/author/patrick-campbell)
  and the ProfitWell / Paddle *Pricing I/O* content —
  the practitioner reference for cohort-based willingness-
  to-pay monitoring and pricing-change guardrails used
  in Lectures 2 and 5.
- OpenView Partners, *SaaS Benchmarks* and *Product-Led
  Growth Index*, annually 2019–2024 —
  [openviewpartners.com/blog](https://openviewpartners.com/blog/) —
  the industry benchmark data referenced across the
  packaging / freemium / trial lectures.
- a16z essays on AI pricing and gross margin — the
  founding writing on why AI-product gross margins
  differ from classic SaaS —
  [a16z.com](https://a16z.com/) (Martin Casado, David
  George, Sarah Wang), 2023–2024, particularly "The New
  Business of AI (and How It's Different From
  Traditional Software)" —
  [a16z.com/the-new-business-of-ai-and-how-its-different-from-traditional-software](https://a16z.com/the-new-business-of-ai-and-how-its-different-from-traditional-software/).
- Anthropic, "Data usage policies" and "Trust Center" —
  [anthropic.com/trust](https://www.anthropic.com/trust) —
  the primary source for zero-retention / enterprise-DPA
  patterns Lecture 7 grounds against; parallel primary
  sources at OpenAI's
  [trust.openai.com](https://trust.openai.com/) and
  Google's
  [cloud.google.com/security/compliance](https://cloud.google.com/security/compliance).
- Simon-Kucher & Partners, *Global Pricing Study*,
  annually — [simon-kucher.com](https://www.simon-kucher.com/en) —
  the industry benchmark data on how often companies
  raise prices, how many run price research, and how
  many hit their revenue lift target after a price
  change.
- Reforge Growth Series (Patrick Campbell / Fareed
  Mosavat / Elena Verna on monetization) —
  [reforge.com/programs](https://www.reforge.com/programs) —
  the peer curriculum for the growth-side of pricing;
  cited as the deeper self-study path in Lecture 4.

See [resources.md](resources.md) for the full, linked
reading list. Additional sources are cited inline in
each lecture and exercise.
