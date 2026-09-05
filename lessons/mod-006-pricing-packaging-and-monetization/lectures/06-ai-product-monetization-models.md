# Lecture 6 — AI-product monetization: cost-plus, value-based, outcome, credits, metering

## The setup

Classic SaaS gross margin runs at 70–85%, and the
pricing conversation is largely about how much value
the customer captures and how much you keep. AI-
substrate products routinely operate at 40–60% gross
margin — sometimes lower — because inference is a
non-trivial cost of goods sold that scales with usage.
The a16z essay *"The New Business of AI (and How It's
Different From Traditional Software)"*
([a16z, 2023](https://a16z.com/the-new-business-of-ai-and-how-its-different-from-traditional-software/))
is the canonical practitioner writing on this shift;
the through-line is that AI-native businesses look
partly like SaaS and partly like services, and the
monetization model has to face both.

The founding-CPO consequence is that many of the
default SaaS monetization patterns break for AI-
substrate products, and the CPO has to reason from
first principles about which pattern fits the
specific feature. This lecture is the vocabulary and
the decision framework.

The four core monetization shapes for AI-substrate
features:

1. **Cost-plus** — price = your inference cost + a
   fixed markup. Common at seed; almost always
   wrong beyond that.
2. **Value-based** — price = a fraction of the value
   the feature creates for the customer. The
   Ramanujam-shape default; hard to prove at seed
   scale.
3. **Outcome-based** — price = payment per delivered
   outcome (resolved ticket, booked meeting,
   recovered dollar). Emerging as a first-class
   option in AI-agent monetization.
4. **Credit / metering** — customer buys a bucket of
   consumption units, spends them across the
   product. Layered on top of any of the above.

This lecture teaches the trade-offs and the fit test
for each.

## The cost structure of AI features (why classic SaaS breaks)

Before the monetization shapes, the cost model. An
AI-substrate feature's cost per user typically
decomposes as:

- **Inference cost.** Model provider API cost (per
  input token, per output token, per image, per
  minute of audio). For frontier models in
  2024–2026, roughly $3–15 per million input
  tokens and $15–75 per million output tokens for
  Anthropic Claude / OpenAI GPT-4o class; smaller
  models 10–100× cheaper.
  <!-- needs-research: check current published rate cards (Anthropic pricing page, OpenAI pricing page) for exact 2026 numbers before quoting benchmarks. -->
- **Retrieval / embeddings cost.** Vector DB reads,
  embedding API calls for indexing, storage.
- **Tool-execution cost.** If the agent invokes
  paid third-party APIs (search, browser
  automation, email send), those costs pass
  through.
- **Orchestration and observability cost.** Logging,
  tracing, eval infrastructure per interaction.
- **Base cloud infrastructure.** The usual SaaS
  overhead.

For an AI-substrate feature, the *inference cost per
interaction* is the load-bearing number. A customer-
support triage agent that runs on GPT-4o class
inference might cost $0.05–0.50 per ticket resolved,
depending on prompt length and tool-call count. If
the customer is paying $0.75 per ticket resolved,
that's a 33–93% cost of goods sold on the feature
alone. Classic SaaS gross-margin math produces
laughable answers.

The mod-005 Lecture 7 cost / latency / quality
Pareto lecture
([mod-005 Lecture 7](../../mod-005-metrics-experimentation-and-ai-evals/lectures/07-cost-latency-quality-pareto.md))
is the vocabulary for reducing this cost — model tier
selection, prompt caching, batch inference, smaller
models on cheap sub-tasks — and it is the *engineering
lever* on the monetization math. This lecture is the
*pricing lever*.

## Monetization shape 1 — Cost-plus

*"Our inference cost per user is $10 / month;
we'll charge $30 / month for a 66% margin."*

**Fits when**:

- You are truly early — the market has no price
  reference for the feature and you need something
  on the pricing page.
- The inference cost is stable and predictable
  (fixed prompt, deterministic model tier, well-
  bounded output length).

**Breaks when** (which is almost always, by month
6–12):

- **Model provider prices drop.** OpenAI and
  Anthropic have both cut per-token prices
  substantially at various points; a cost-plus
  price that was $30 becomes $12 overnight, and
  competitors either pass through the drop or you
  do. Cost-plus turns you into a pass-through.
- **The customer's value derived is way higher than
  your cost.** Ramanujam-shape hidden gems: you're
  charging a fraction of what the feature is
  worth because you priced from your side of the
  ledger, not theirs.
- **The customer's value derived is much lower
  than your cost.** The customer uses the feature
  lightly but you've priced for average
  consumption. Underpriced-heavy-users subsidize
  overpriced-light-users; the low-users churn
  because they're paying too much for what they
  use.
- **The customer changes usage behavior in ways
  that break your cost model.** A cost-plus per-
  month price on a heavy-usage account produces a
  gross-margin-negative account.

**The rule.** Cost-plus is a *floor* to consult, not
a price to charge. Every AI-product price should be
sanity-checked against the cost model (are we
losing money on the median account?), but the price
itself should come from willingness-to-pay or
value-based reasoning.

## Monetization shape 2 — Value-based

*"Our customer support triage agent saves the customer
~15 minutes per ticket at a fully-loaded rep cost of
$0.60 per minute. The agent creates $9 of value per
ticket resolved. We'll capture ~20% of that, so we
charge $1.80 per ticket resolved."*

**Fits when**:

- The value is nameable, quantifiable, and the
  customer will accept the value estimate.
- The customer is sophisticated enough to buy on
  unit-economic reasoning.
- You have enough evidence (case studies, pilots,
  the mod-005 analytics regime applied to the
  feature) to defend the value estimate.

**Breaks when**:

- The value is fuzzy or contested. "How much is a
  better-written email worth?" is a value-based
  pricing question that has no defensible answer
  without a lot of context.
- The customer doesn't accept the value estimate.
  A per-outcome price of $1.80 that the customer
  believes is worth $0.90 is a stalled deal.
- The value varies wildly across customers. One
  customer's $9 per ticket is another customer's
  $1 per ticket; value-based pricing that
  averages across them under-captures from high-
  value customers and prices out low-value ones.

**The founding-CPO version of value-based pricing:**

- Do value quantification with the mod-001 discovery
  method — 20 interviews with users of the feature,
  asking specifically about the value-metric quantity
  (time saved, tickets resolved, dollars recovered)
  and the fully-loaded cost the feature displaces.
- Publish a **value calculator** on the pricing page
  or in the sales collateral: *"tell us your ticket
  volume and average resolution time; we'll show you
  the value and the price."* This makes value-based
  pricing self-justifying to the customer.
- Charge a **fraction of the value** (typically 10–
  30%, per practitioner benchmarks). Charging more
  than half of the created value is where value-
  based pricing produces buyer resistance.
  <!-- needs-research: cite specific practitioner benchmark on value-capture percentages for AI outcome pricing — this is a well-cited number but source varies. -->

## Monetization shape 3 — Outcome-based

*"We charge $2 per closed ticket, regardless of how
many model calls it took us to close."*

Outcome-based is a specific value-based variant: the
value metric is a **binary or countable outcome the
product produces**, and the customer pays only for
outcomes delivered. Common in AI-agent monetization
where the outcome is measurable: a resolved support
ticket, a booked meeting, a qualified lead, a
recovered dollar of accounts receivable.

**Fits when**:

- The outcome is measurable and attributable to
  the product. "This ticket was closed by the
  agent, not the human" must be a defensible
  claim.
- The customer will accept the attribution rule.
  Gray-area cases (agent draft + human edit + sent)
  need a clear "who counts this as an outcome"
  rule.
- Your cost per attempted outcome is lower than the
  price per successful outcome. If the agent fails
  60% of the time and you charge only for success,
  the effective revenue per attempt is 40% of the
  headline price — the cost model has to close.
- The buyer is sophisticated (usually enterprise
  or mid-market with a finance function that
  understands per-outcome pricing).

**Breaks when**:

- Attribution is contested. The customer disputes
  whether the agent or the human resolved the
  ticket.
- The customer optimizes against the meter. If you
  charge per resolved ticket, the customer can
  route hard tickets away from the agent, keeping
  your headline resolution rate high but leaving
  you with only the easy tickets.
- Cost of attempted outcomes runs high and the
  success rate is unpredictable. You end up paying
  cost of goods sold for failed attempts you
  don't get paid for.
- The customer's revenue is lumpy or seasonal. A
  law firm that does 2 large matters a quarter
  won't pay per-matter reliably.

**Sirena Salesforce Salesforce's per-conversation
Agentforce pricing** and similar 2024–2026
announcements from major SaaS vendors are the
public market signal on outcome-based AI pricing;
each has specific attribution rules and floor / cap
structures worth studying.
<!-- needs-research: cite specific Salesforce Agentforce pricing announcement / 2024–2026 primary source before making this claim precise. -->

## Monetization shape 4 — Credits and metering

*"You buy 10,000 credits for $100. Each interaction
consumes a variable number of credits depending on
model tier and output length."*

Credits are a *packaging layer* over any of the
above shapes. Instead of billing per interaction (or
per outcome, or per month), the customer buys a
bucket and spends it. Common in developer-facing
AI products (OpenAI ChatGPT team plans, Anthropic
Claude plans, image-generation tools, agent
platforms).

**Fits when**:

- Usage is variable and hard for the customer to
  forecast. Credits let them cap exposure.
- Different actions have very different costs
  (a small chat vs. a long agent trajectory). One
  price per interaction hides the cost
  differential; credits expose it in the meter.
- The customer wants budget control. Credits map
  cleanly to internal cost centers.

**Breaks when**:

- Credits become an opaque currency the customer
  can't reason about. "Why did that request cost
  47 credits?" without a clear formula produces
  frustration.
- Unused credits create refund and rollover
  expectations. Credit systems need explicit
  policies for expiration, rollover, refunds.
- The credit-to-cost mapping shifts as your cost
  model changes. If model prices drop and you
  keep the credit cost the same, you're charging
  more than justified; if you cut credit costs,
  the perceived value of previously-bought
  credits deflates.

**Design considerations**:

- **Credit definition**: what does 1 credit = ?
  Some products define 1 credit = 1 model call
  (simple, breaks when call costs vary widely).
  Others define 1 credit = 1000 tokens (aligns
  with model cost but exposes the token unit to
  users). Others define 1 credit = 1 "task"
  (opaque but customer-friendly).
- **Bundle sizes**: how big are the buckets and
  how are they priced. Typical bundles are non-
  linear (buy 100 credits for $10; buy 1000 for
  $80). Larger bundles create commitment and
  reduce churn.
- **Expiration and rollover**. Do credits expire?
  Do they roll over? What happens on downgrade?
  All decisions with trust implications.
- **Overage**: what happens when the customer runs
  out mid-month. Auto-refill (with cap), block
  (with prompt to buy more), continue-but-invoice
  (rare and risky).

## Choosing the shape — a decision matrix

|  | **Buyer sophistication** | **Cost predictability** | **Best fit** |
|---|---|---|---|
| Self-serve individuals / small teams | Low | Value hard to name | Flat monthly (with credits or usage floor as add-on) |
| SMB / mid-market | Medium | Value nameable but variable | Seat + usage hybrid; credits |
| Mid-market / enterprise | High | Value nameable and quantifiable | Value-based per-outcome or usage-based with commit |
| Large enterprise | Very high | Value negotiable | Custom outcome-based with SLAs and floor / ceiling |

Regardless of shape, three commitments protect
gross margin:

- **Set floors and ceilings.** Even a value-based
  or outcome-based price benefits from a monthly
  minimum (the customer commits to at least $X /
  month, floor) and a monthly maximum (customer's
  bill can't exceed $Y / month, ceiling — protects
  the customer, and protects you from a runaway
  usage account you can't serve).
- **Watch the median-account gross margin monthly.**
  Cost-per-account divided by price-per-account.
  If the median drops below your gross-margin
  floor, the pricing model is broken; fix before
  it becomes catastrophic.
- **Re-price when the model provider re-prices.**
  Anthropic and OpenAI have both cut per-token
  prices materially at various points; each is an
  opportunity to either widen margin or drop
  price. The a16z essay is emphatic on this:
  AI-product economics are a moving target and
  the pricing model has to be re-inspected on the
  same cadence as the cost model.

## Common failure modes

Seven AI-monetization failures that recur across
founding-CPO attempts:

- **Cost-plus persistence past product-market
  fit.** Team stays on cost-plus long after they
  have enough evidence to move to value-based.
  Result: leaving the majority of created value
  on the table.
- **Value-based pricing with no value estimate.**
  Team claims value-based but has no defensible
  value quantification. The price is a number
  someone thought sounded reasonable; the "value-
  based" label is marketing.
- **Outcome-based pricing with contested
  attribution.** Team charges per closed ticket
  but has no clear rule for who counts a ticket
  as "closed by the agent." Support tickets and
  invoice disputes follow.
- **Freemium on a cost-heavy AI feature.** Team
  offers a generous free tier of an inference-
  heavy feature; the marketing-attribution costs
  hide the fact that each free user costs $5–15 /
  month to serve. See
  [Lecture 4](04-free-trial-freemium-reverse-trial.md).
- **Credit systems without formula transparency.**
  Team charges variable credits per action but
  won't publish the formula. Users lose trust when
  their bills feel unpredictable.
- **Unit economics that don't survive a model-
  provider price change.** Team's whole gross-
  margin story depends on model prices staying
  where they are. Model provider updates the price
  sheet; the pricing model breaks.
- **No repricing cadence.** Team sets the price at
  launch and doesn't revisit for 18 months, during
  which model prices have dropped 4×, the product
  has added features, and the willingness-to-pay
  has doubled. The team is under-priced and
  doesn't know it.

## What the CPO does personally

- **Chooses the monetization shape.** Cost-plus,
  value-based, outcome-based, or credit / metering,
  chosen from the decision matrix — not by
  inheritance.
- **Quantifies the value estimate.** For value-based
  or outcome-based, the CPO runs the discovery
  work that produces the value number.
- **Sets floors, ceilings, and overage rules.**
  Design decisions with implications for margin and
  customer trust.
- **Sanity-checks against cost.** Median-account
  gross margin, monthly. The CPO reads this; the
  finance team may compute it.
- **Runs the repricing cadence.** Quarterly or
  semi-annual review of the pricing model against
  the current cost model and WTP evidence. Not
  delegable — the CPO is who has all four inputs
  (cost, value, competition, packaging) in view.

## What the CPO consumes from eng and finance

- **Cost-per-interaction telemetry.** Eng
  instruments the model calls with cost attribution;
  the CPO reads.
- **Cost-model projections.** Finance projects the
  cost side against the pricing side; the CPO
  reads to defend the pricing choice.
- **Model-provider price change alerts.** Eng and
  procurement track upstream provider price
  changes; the CPO reads and initiates the
  repricing review.
- **Enterprise-deal cost-of-goods-sold estimates.**
  For large custom deals, finance estimates the
  fully-loaded COGS on the proposed contract; the
  CPO uses this to defend or reject the discount.

## Boundaries this lecture keeps

- **The cost / latency / quality Pareto** — the
  engineering levers for reducing inference cost —
  is
  [mod-005 Lecture 7](../../mod-005-metrics-experimentation-and-ai-evals/lectures/07-cost-latency-quality-pareto.md).
  This lecture reasons about the pricing side;
  mod-005 teaches the engineering side.
- **Enterprise DPA / zero-retention / on-prem as
  a packaging tier** is
  [Lecture 7](07-enterprise-dpa-zero-retention-on-prem-gating.md).
- **AI-agent evals and outcome measurement** at
  depth are
  [mod-005 Lecture 6](../../mod-005-metrics-experimentation-and-ai-evals/lectures/06-eval-driven-decisions-for-llm-products.md)
  and, at engineering depth,
  [ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning).
  This lecture uses eval results as inputs to the
  outcome-attribution rule; it does not teach the
  evals themselves.
- **Unit-economics modeling** at CFO depth is
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum);
  the CPO consumes the model.
- **Sales negotiation on custom outcome-based
  contracts** is level-30 GTM craft owned by
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum).
  The CPO authors the SKU; sales negotiates the
  specific deal.

## Takeaways

- **AI-substrate products have SaaS-and-services
  gross margin profiles** — commonly 40–60%, often
  lower. Classic SaaS monetization patterns
  frequently break; the CPO reasons from first
  principles for each feature.
- **Four monetization shapes**: cost-plus (floor
  only, don't charge on it), value-based (default
  when value is nameable), outcome-based (value-
  based with a measurable outcome unit), credit /
  metering (packaging layer over any of the
  above).
- **Value-based pricing needs a defensible value
  estimate.** Run the discovery; publish the
  calculator; charge a fraction of the value
  (typically 10–30%).
- **Outcome-based pricing needs a defensible
  attribution rule.** Who counts an outcome as
  delivered, in gray-area cases; what happens on
  failure.
- **Credits are a packaging layer**, not a shape by
  themselves. Design them with formula
  transparency, expiration policy, overage
  handling.
- **Floors and ceilings protect both sides.**
  Monthly minimum for you; monthly maximum for the
  customer.
- **Watch median-account gross margin monthly**;
  reprice when the model provider does. AI-product
  economics are a moving target.

Lecture 7 turns to the **enterprise-facing packaging
tier** — DPA, zero-retention, on-prem, and the
security / compliance surfaces the CPO gates
higher-priced tiers with.
