# Exercise 5 — AI-product monetization model drill

**Time:** ~2 hours. **Deliverable:** one **AI-product
monetization model** for one feature from the Exercise 1
product — monetization shape (cost-plus / value-based /
outcome-based / credit-metering) chosen from the Lecture
6 decision matrix with a defended rationale, meter-unit
definition, inference-cost model, floor / ceiling /
overage rules, repricing cadence, and the enterprise-DPA
/ retention / deployment tier from Lecture 7 that the
model plugs into. Plus a **median-account gross-margin
sanity check** against the inference-cost model.

## Purpose

Walk the AI-substrate monetization reasoning from
[Lecture 6](../lectures/06-ai-product-monetization-models.md)
and the enterprise-tier reasoning from
[Lecture 7](../lectures/07-enterprise-dpa-zero-retention-on-prem-gating.md)
end-to-end against one *specific* feature from the
product you authored in
[Exercise 1](exercise-01-monetization-model-authoring-for-one-product.md).
The point is to force two founding-CPO moves the
classic-SaaS version of this exercise never requires:

1. **Pick the shape from first principles, not by
   inheritance.** Cost-plus is almost always wrong past
   month 6; value-based needs a defensible value
   estimate; outcome-based needs a defensible
   attribution rule; credits are a packaging layer, not
   a shape. The default is "think from scratch" — not
   "copy OpenAI's or Intercom's structure."
2. **Reason about the inference-cost model as a first-
   class input to the pricing choice.** AI-substrate
   products operate at gross margins routinely 20–40
   percentage points below classic SaaS (per the a16z
   "New Business of AI" writing). The pricing model
   that doesn't survive a 2× jump in model-provider
   prices — or doesn't widen when prices drop — is the
   pricing model that re-opens every six months.

The exercise is deliberately *per feature*, not per
product. A real AI-substrate product usually has
several features with different cost profiles and
different value stories (one agent-shaped feature with
expensive multi-step inference, one classifier with
cheap single-call inference, one copilot with per-
interaction value). Pick the one where the
monetization choice is most load-bearing.

## Prerequisites

- [Exercise 1](exercise-01-monetization-model-authoring-for-one-product.md)
  complete — the overall monetization model is the
  context this feature-level model sits inside.
- Access to the current (or realistic estimated)
  inference-cost model for the chosen feature. If you
  don't have real cost numbers, estimate from the
  model-provider price card you'd use (Anthropic
  Claude, OpenAI GPT-4o class, open-source via
  Together / Fireworks / Groq) and the prompt /
  tool-call / output-length profile of a typical
  interaction.
- The DPA / retention / deployment surface area from
  [Lecture 7](../lectures/07-enterprise-dpa-zero-retention-on-prem-gating.md).
  You don't need to be a lawyer or compliance expert;
  the exercise asks which packaging tiers *gate* which
  of those surfaces, not what the legal text says.

## Choosing the feature

Pick one feature of the Exercise 1 product. In order
of preference:

1. **An AI-agent or multi-step inference feature** —
   where the value proposition is doing a job for the
   user (resolving a ticket, drafting an email,
   recovering a dollar) and the cost model is non-
   trivial. This is the shape Lecture 6's hardest
   choices land on.
2. **A model-powered copilot or classifier** — a
   feature where the AI augments the user's workflow
   (autocomplete, summarization, extraction).
   Cheaper inference; value estimate harder to
   quantify per interaction; often fits a flat
   monthly or a credits layer.
3. **A per-document / per-output / per-asset
   feature** — generation, transformation, scoring.
   Clean per-outcome meter; cost model directly
   tied to the output.

Avoid picking a non-AI feature; this exercise is
about the AI-specific monetization pattern. If the
Exercise 1 product doesn't have an AI-substrate
feature at all, author a plausible AI feature that
would fit it (per the Lecture 6 vocabulary) and
state the assumptions.

## What the AI-monetization model memo must contain

Three to four pages. Follow the sections below in
order.

### 1. The feature in context (quarter page)

- **The feature in one paragraph.** What it does for
  the user, inside what workflow, substituting for
  what manual work (or extending it).
- **The buyer segment** that would pay for it (one of
  the Exercise 1 segments).
- **Where it sits in the Exercise 1 tier structure.**
  Is this a Good-tier capability? Better-tier? Best /
  Enterprise? Does it change the tier structure to
  include an AI feature here?

### 2. Inference-cost model (half page)

Grounded in
[Lecture 6 — The cost structure of AI features](../lectures/06-ai-product-monetization-models.md#the-cost-structure-of-ai-features-why-classic-saas-breaks).

- **Cost per interaction**, decomposed:
  - **Inference cost** — model, token counts (input
    + output), rate per million tokens from the
    provider's current price card. Cite the
    provider page or state the assumption and date.
    If the current price card lookup isn't
    available in your environment, insert a
    `<!-- needs-research: ... -->` marker and the
    specific numbers you'd verify.
  - **Retrieval / embedding cost** — vector DB
    reads per interaction, embedding generations
    per index.
  - **Tool-execution cost** — paid APIs the agent
    calls (search, browser automation, email send).
  - **Orchestration / observability cost** —
    logging, tracing, evals per interaction.
  - **Fixed overhead per month per account** — base
    SaaS cloud, if non-trivial for this feature.
- **The dominant cost line.** Which of the above is
  more than ~60% of the total cost. The dominant
  line is where the margin story lives or dies.
- **Cost under three usage profiles**:
  - *Light* — 10% percentile user (how many
    interactions per month).
  - *Median* — 50% percentile user.
  - *Heavy* — 90% percentile user.
- **Cost variance per interaction.** Is it tight
  (±20% around the median) or heavy-tailed (the
  90-percentile interaction costs 10× the median)?
  Heavy-tailed cost variance is the single most
  common AI-pricing-model trap — flat monthly
  pricing on a heavy-tailed cost distribution loses
  money on heavy users.

### 3. Monetization shape — the choice (one page)

Grounded in
[Lecture 6 — Monetization shapes 1–4](../lectures/06-ai-product-monetization-models.md#monetization-shape-1--cost-plus).

Walk all four shapes from Lecture 6 against the
feature. For each, one short paragraph:

- **Cost-plus.** When this fits, when it breaks for
  this feature. The Lecture 6 rule is to use cost-
  plus only as a *floor* to sanity-check against,
  not as a price to charge.
- **Value-based.** Can you name the value this
  feature creates in a quantity the buyer would
  accept? What's the fully-loaded cost of the
  manual work it displaces (or augments)? What
  fraction of that value is realistic to capture
  (Lecture 6 cites a practitioner benchmark of
  10–30% of created value; cite your source if you
  depart from that)?
- **Outcome-based.** Can you define a defensible
  outcome unit — resolved ticket, booked meeting,
  recovered dollar, qualified lead? What's the
  attribution rule — exactly when does one
  "outcome" count? What happens in gray-area cases
  (agent draft + human edit + sent)? What happens
  on failed attempts the cost-model still pays
  for?
- **Credits / metering layer.** Would you layer
  credits over any of the above to give the
  customer budget control? If yes, what does 1
  credit map to (model call? 1000 tokens? one
  task?), what are the bundle sizes, what's the
  expiration / rollover / refund policy, what
  happens on overage?

**The chosen shape.** State it in one sentence, with
a one-sentence reason. Not "value-based because
value-based is better" — "outcome-based per
resolved ticket because our buyers already measure
tickets, the attribution rule is defensible via the
mod-005 Lecture 6 eval regime, and our cost-per-
attempted-outcome is well under the proposed
per-success price."

**The decision-matrix fit.** Where this feature's
buyer segment lands on the Lecture 6 decision
matrix (buyer sophistication × cost predictability
→ best-fit shape). If you're departing from the
matrix recommendation, name the specific reason.

### 4. Meter unit definition (quarter page)

Grounded in
[Exercise 1 — The meter](exercise-01-monetization-model-authoring-for-one-product.md#2-the-meter-one-page)
and
[Lecture 6](../lectures/06-ai-product-monetization-models.md).

- **What exactly is one meter-unit?** No ambiguity.
  "One resolved ticket" — closed by the agent only?
  Closed with human review? Closed within what
  SLA? "One generated document" — one API call? One
  final output accepted by the user? "One credit" —
  one model call, 1000 tokens, one task?
- **The attribution rule for gray-area cases.**
  Written as if it were going in the customer
  invoice. Specific enough that a customer
  disputing a line item has nowhere to argue.
- **Failure handling.** When an attempted outcome
  fails, is the customer charged? If no, how do you
  cover the attempt cost? If yes, how is the
  pricing defensible for the customer?

### 5. Floors, ceilings, and overage rules (quarter page)

Grounded in
[Lecture 6 — Choosing the shape](../lectures/06-ai-product-monetization-models.md#choosing-the-shape--a-decision-matrix).

- **Monthly floor** (minimum commit from the
  customer) — what, and why. Protects you from the
  tiny-usage account that doesn't cover the fixed
  overhead per account.
- **Monthly ceiling** (cap on the customer's bill) —
  what, and why. Protects the customer from a
  runaway bill and protects you from a runaway
  usage account you can't serve profitably.
- **Overage behavior.** When the customer exceeds a
  cap or runs out of credits, what happens:
  auto-upgrade (with cap), auto-refill, block with
  prompt-to-buy, continue-and-invoice (rare and
  risky, usually enterprise-only), hard block.
- **Soft-landing design.** How you avoid the
  "sudden invoice shock" at the end of the first
  heavy month — notifications at 50% / 80% / 100%
  of the cap, pre-cap preview of the new bill,
  honor-grace-period on first overage.

### 6. Median-account gross-margin sanity check (quarter page)

Grounded in
[Lecture 6 — Three commitments protect gross margin](../lectures/06-ai-product-monetization-models.md#choosing-the-shape--a-decision-matrix).

For the chosen monetization shape and the Section 2
cost model:

- **Median account revenue** — per month, under the
  proposed price.
- **Median account cost** — the Section 2 median-
  usage cost line.
- **Median account gross margin** — (revenue − cost)
  / revenue. State the number.
- **What the number says.** Classic SaaS gross
  margin runs 70–85%; AI-substrate commonly 40–60%
  (per
  [a16z, 2023](https://a16z.com/the-new-business-of-ai-and-how-its-different-from-traditional-software/)).
  If you're below 40%, the pricing model is at
  risk; if you're below 20%, you're a services
  company, not a software company — the model is
  broken.
- **Heavy-account check.** Repeat the margin
  calculation at the 90-percentile usage profile.
  If the heavy-account margin is negative, you need
  a monthly ceiling (Section 5) or a usage-based
  overage charge that keeps heavy accounts
  profitable.
- **What happens if model-provider prices drop
  50%.** The repricing / windening scenario. If
  model prices drop and you don't move the
  customer-facing price, your gross margin widens
  materially; if competitors drop prices and you
  don't, you lose on the sales call.
- **What happens if model-provider prices rise
  2×.** The downside scenario. Does your pricing
  model absorb it (margin compresses but you stay
  profitable) or break (median account goes
  gross-margin-negative)?

### 7. Enterprise / DPA / retention / deployment tier (half page)

Grounded in
[Lecture 7](../lectures/07-enterprise-dpa-zero-retention-on-prem-gating.md).

For this feature in the proposed packaging:

- **Data-flow diagram, in one paragraph.** Customer
  data → your system → which third-party model
  provider(s) → back. State explicitly whether
  customer data traverses which model provider
  (Anthropic, OpenAI, Google) and under what
  provider account tier (standard API vs.
  zero-retention / enterprise-tier API).
- **DPA posture per tier.** Which packaging tiers
  get what:
  - **Default (Good / Better).** Standard DPA, the
    provider's standard data-handling terms.
  - **Business / Pro.** Any additional data-handling
    commitments (custom retention windows, named
    subprocessors, extended audit rights).
  - **Enterprise.** Zero-retention routing to the
    model provider, custom DPA negotiable, named
    subprocessors with customer veto, right-to-
    audit, data-residency selection, SOC 2 Type II
    + ISO 27001 as proof of controls.
- **Retention tier.** Which tier gets zero-retention
  routing (model provider does not retain inputs or
  outputs past the inference window). Lecture 7's
  default: zero-retention is a Business- or
  Enterprise-tier gate, not a Good-tier default,
  because it has operational cost (eval / safety
  tooling that depends on retained traces may
  break).
- **Deployment tier.** Which tier gets which
  deployment mode: SaaS in your cloud (default),
  SaaS in customer's cloud / VPC (typically
  Enterprise), on-prem / air-gapped (typically a
  separate contact-sales SKU).
- **No-training-on-customer-data commitment.** State
  which tiers get what. Lecture 7's observation:
  this is a surprisingly cheap commitment for most
  AI-substrate products (model providers' enterprise
  tiers already provide it) and a surprisingly
  valuable one for enterprise buyers.

### 8. Repricing cadence (quarter page)

Grounded in
[Lecture 6 — Re-price when the model provider re-prices](../lectures/06-ai-product-monetization-models.md#choosing-the-shape--a-decision-matrix).

- **Cadence.** Quarterly or semi-annual review of the
  pricing against the current cost model and the
  current WTP evidence.
- **Triggers.** What events force an off-cadence
  review:
  - Model provider price change > 20% in either
    direction.
  - Median-account gross margin crosses the
    pre-set floor (or ceiling) for two consecutive
    months.
  - Competitor material pricing change.
  - A packaging change that touches this feature's
    cost model (e.g., the feature moves tiers).
- **Who's in the room.** CPO leads; finance brings
  the cost model and the margin dashboard; eng
  brings the model-provider price-change alerts
  and the engineering levers available (model
  swap, prompt caching, batch, smaller sub-task
  models — the mod-005 Lecture 7 Pareto); GTM
  brings the competitive and customer intel.
- **What triggers a customer-facing price change
  vs. an internal re-margin.** Not every cost or
  WTP shift becomes a customer price change —
  sometimes the right move is to widen margin
  silently or invest the differential in heavier
  inference per interaction (quality lift) rather
  than a price drop. Named explicitly.

## Starter guidance

- **Model the cost per interaction before you
  write a single word about price.** The inference-
  cost model is the load-bearing input; a monetization
  shape chosen without it is a monetization shape
  you'll re-choose in three months.
- **Pick the simplest shape that fits.** Credits are
  seductive and often wrong — they add a cognitive
  layer the customer has to reason about and often
  disguise a cost-plus or usage-based price with no
  additional value. Prefer flat / outcome / usage
  until you have a specific reason to add credits.
- **Define the meter unit crisply.** The single
  biggest source of post-launch pricing pain is
  ambiguity about what one unit is. If you can't
  write the attribution rule in a sentence, redesign
  the unit.
- **Model the heavy user, not just the median.** The
  classic AI-pricing failure is pricing to the
  median usage and discovering that the top-decile
  user consumes 10× the median. Section 6's heavy-
  account margin check is non-optional.
- **Treat the DPA / retention / deployment tier as
  a product surface, not a legal footnote.** For
  enterprise buyers, the compliance wrapping is a
  substantial fraction of what they're paying extra
  for. Lecture 7's framing: it's packaging, not
  overhead.
- **Pre-write the repricing cadence.** The teams
  that reprice are the teams that have calendared
  reviews. The teams that don't reprice are the
  teams that intended to and never got around to
  it.

## Acceptance criteria

- **The feature** is named concretely with its tier
  placement from Exercise 1.
- **Inference-cost model** decomposes cost per
  interaction into inference / retrieval / tool /
  orchestration / overhead lines, identifies the
  dominant line, and reports cost under light /
  median / heavy usage.
- **Monetization-shape walkthrough** covers all four
  Lecture 6 shapes with a one-paragraph verdict for
  each; names the chosen shape with a one-sentence
  reason; cites the Lecture 6 decision matrix.
- **Meter-unit definition** has no ambiguity — the
  attribution rule is written as if it were on an
  invoice, including the gray-area and failure-
  handling cases.
- **Floors, ceilings, and overage** are stated with
  numeric values (not wishes) and a soft-landing
  design for first-overage.
- **Median-account gross-margin check** is computed
  with revenue, cost, and margin numbers, plus a
  heavy-account repeat and both price-shock
  scenarios (provider prices 2× up, 50% down).
- **DPA / retention / deployment tier** states per-
  tier posture for DPA, retention, deployment mode,
  and no-training commitment; the enterprise tier
  grounds against Lecture 7's primary-source
  references (Anthropic Trust Center, OpenAI trust
  portal, Google Cloud compliance).
- **Repricing cadence** names the review frequency,
  the triggers, the room, and the
  customer-facing-vs-internal distinction.

## Common failure modes

- **Cost-plus by default.** Memo picks cost-plus
  because "we don't know the value yet." Lecture 6's
  response: cost-plus is a floor to consult, not a
  price to charge. If you truly don't know the
  value, the next move is Exercise 3's WTP work on
  this feature specifically, not shipping cost-plus
  and hoping.
- **Value-based with no value estimate.** Memo
  claims value-based pricing but doesn't quantify
  the value. "The feature is worth a lot" is not a
  value estimate; "the feature saves a support rep
  15 minutes per ticket at $0.60/min fully-loaded,
  so $9 per ticket of created value" is.
- **Outcome-based with contested attribution.**
  Memo picks per-resolved-ticket pricing without a
  defensible rule for what counts as "resolved by
  the agent." The first customer-dispute case will
  be a disaster.
- **Credits with no formula transparency.** Memo
  layers credits over a per-call model but refuses
  to publish the credit-cost formula. Customers
  lose trust when bills feel unpredictable.
- **No heavy-account check.** Memo computes median-
  account margin and declares victory; the
  90-percentile account is gross-margin-negative
  and the model fails at scale. Section 6's
  heavy-account check is where this gets caught.
- **No repricing cadence.** Memo treats the pricing
  as if it will stand for 18 months. Model-provider
  prices move; the pricing model has to move with
  them. Section 8 is non-optional.
- **DPA / retention tier as a bullet-point
  afterthought.** Memo lists SOC 2 and SSO as
  features and considers the enterprise work done.
  Lecture 7's point: enterprise is a *packaging
  tier* with its own data-flow story, its own
  deployment options, its own tier of commitments
  — not a feature-inclusion checkbox.
- **No cost-model price-shock scenario.** Memo
  assumes model-provider prices are stable. They
  are not; they have cut and raised at various
  points; the pricing model that doesn't survive
  either direction is the model you'll re-author
  under duress.
- **Meter unit that fails in production.** "One
  document" without a rule for what makes two
  outputs one document vs. two documents.
  Ambiguity bites in real customer invoices.

## Source alignment

The four monetization shapes, cost-structure framing,
value-capture-fraction heuristic, and
decision-matrix for shape × buyer come from
[Lecture 6](../lectures/06-ai-product-monetization-models.md),
which synthesizes the a16z writing on AI business
economics — Martin Casado, David George, Sarah Wang,
"The New Business of AI (and How It's Different From
Traditional Software)," a16z, 2023 —
[a16z.com/the-new-business-of-ai-and-how-its-different-from-traditional-software](https://a16z.com/the-new-business-of-ai-and-how-its-different-from-traditional-software/) —
with Ramanujam / Simon-Kucher's value-based pricing
discipline from *Monetizing Innovation*, Wiley, 2016,
Chapters 3–6 —
[wiley.com/en-us/Monetizing+Innovation](https://www.wiley.com/en-us/Monetizing+Innovation%3A+How+Smart+Companies+Design+the+Product+Around+the+Price-p-9781119240860) —
and Kyle Poyar's usage-based-pricing writing at
Growth Unhinged —
[growthunhinged.com](https://www.growthunhinged.com/).
The DPA / retention / deployment-tier framing in
Section 7 derives from
[Lecture 7](../lectures/07-enterprise-dpa-zero-retention-on-prem-gating.md),
grounded in primary-source model-provider trust pages:
Anthropic ([anthropic.com/trust](https://www.anthropic.com/trust)),
OpenAI ([trust.openai.com](https://trust.openai.com/)),
Google Cloud
([cloud.google.com/security/compliance](https://cloud.google.com/security/compliance)).
The underlying inference-cost engineering levers —
model-tier selection, prompt caching, batch, smaller
sub-task models — are
[mod-005 Lecture 7](../../mod-005-metrics-experimentation-and-ai-evals/lectures/07-cost-latency-quality-pareto.md),
which this exercise consumes but does not re-teach.
