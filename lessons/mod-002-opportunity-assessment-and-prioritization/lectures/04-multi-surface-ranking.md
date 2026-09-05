# Lecture 4 — Multi-surface ranking: the CPO as portfolio ranker

## The setup

Lectures 1–3 assumed a single product with a single queue. Most founding
CPO roles are not that job. The product line has multiple *surfaces*, each
with its own users, its own funnel, its own PM (or none), and its own
economics:

- A **consumer** surface — the app your end-users see.
- A **marketplace** surface — the two-sided or multi-sided venue where
  supply meets demand, with cross-side network effects.
- A **platform / API** surface — the programmable extension point that
  third parties build on.
- A **data** surface — reports, exports, embedded analytics, or a
  standalone insights product built on the corpus the other surfaces
  generate.

Not every product has all four. But once you have two — and the market's
shape here is that AI-native products, resale marketplaces, and
commerce-platform products routinely have three or four — the CPO's job
changes. You stop being the PM for one queue and start being the ranking
function *across* queues. Two PMs each running a defensible RICE
spreadsheet on their own surface will produce two locally-optimal
roadmaps whose sum is not what the company should be doing. The CPO's
value-add is the cross-surface arbitration.

This is the *Archive-* and *commercetools-shaped* problem the module
title flags — the shape isn't specific to those companies, but their
public shape (a consumer marketplace with a supply-side operations
product; a headless-commerce platform with API, frontend, and merchant
tools) is a clean example of the pattern
([commercetools "About" — commercetools.com/about](https://commercetools.com/about);
[Archive "How it works" — archive.com/how-it-works](https://archive.com/how-it-works)).
<!-- needs-research: verify current public product surface descriptions
for commercetools and Archive; both companies iterate their surface
naming frequently. If citations break, replace with the AWS
console-vs-services-vs-marketplace example (three surfaces documented at
aws.amazon.com/products) or Shopify (admin, storefront, app store, API
per shopify.dev). -->

## Why single-surface ranking fails at multi-surface scope

Three failure modes explain most of the pain:

1. **Local-optimum aggregation.** Each surface's PM optimizes their own
   metric — checkout conversion for consumer, seller-listing time for
   marketplace, endpoint latency for API. Nobody optimizes the metric
   that ties them together (marketplace liquidity, platform ecosystem
   growth, blended contribution margin).
2. **Cross-surface externalities.** A "small" consumer change increases
   support ticket volume enough to swamp the marketplace ops team. A
   platform API rate-limit change silently kills the reference
   integration the consumer app depends on. Neither surface's RICE
   sheet has the other one's cost as a term.
3. **Under-invested shared substrate.** The identity system, the
   permissions model, the observability stack, the design system — the
   things every surface uses — are nobody's roadmap priority because
   they don't move any single surface's headline metric. They rot until
   they break something in production.

Any prioritization scheme that ranks opportunities inside a single
surface's queue cannot see any of these. That's the ranking gap the CPO
fills.

## The two conceptual frames the multi-surface CPO leans on

**Aggregation Theory** (Ben Thompson) — for products where the surface
that owns the customer relationship compounds power over time; the
question "where does the demand aggregate?" is the framing that tells you
which surface is strategic and which is a tactical extension
([Thompson, "Aggregation Theory," *Stratechery*, July 2015 —
stratechery.com/2015/aggregation-theory](https://stratechery.com/2015/aggregation-theory/);
[Thompson, "Defining Aggregators," *Stratechery*, February 2017 —
stratechery.com/2017/defining-aggregators](https://stratechery.com/2017/defining-aggregators/)).

**Platform economics** (Sangeet Paul Choudary and colleagues) — for
products with cross-side network effects, the ranking rule is: fund the
scarce side of the market first, because the abundant side follows for
free once the scarce side is present
([Choudary, *Platform Scale*, Platform Thinking Labs, 2015 —
platformed.info/books](https://platformed.info/books/);
[Van Alstyne, Parker & Choudary, "Pipelines, Platforms, and the New
Rules of Strategy," *Harvard Business Review*, April 2016 —
hbr.org/2016/04/pipelines-platforms-and-the-new-rules-of-strategy](https://hbr.org/2016/04/pipelines-platforms-and-the-new-rules-of-strategy)).

You will not solve the multi-surface ranking with either frame alone; you
use them to *diagnose* which surface is the primary driver of long-term
positioning (aggregation, platform) so you know where to weight the
investment before you rank inside each queue.

## A workable multi-surface ranking procedure

There is no single canonical process — the mix of your surfaces, thesis,
and stage is idiosyncratic — but the following is a procedure that has
survived contact with real portfolios.

### Step 1 — Publish the surface list, with owners and metrics

One page. For each surface: what it is, who its users are, who owns it
today (a PM name or *unowned*), the two or three metrics it's optimized
for, and its current stage (*discovery, PMF-searching, scaling, mature,
sunset candidate*). If you cannot fit the whole portfolio on one page,
your first cross-surface problem is that you have surfaces you cannot
name — start there.

### Step 2 — Name the cross-surface metric

The metric that captures whether the *whole* product line is
compounding, not any single surface. Concrete candidates by shape:

- **Multi-sided marketplace.** Liquidity (transactions per unit of
  supply per unit of time), take-rate on transacted GMV, or the ratio
  of matched to listed supply.
- **Platform / API-first.** Number of active third-party integrations
  weighted by their downstream user count, or platform-attributable ARR.
- **Consumer + monetization surface.** Contribution margin per active
  user, blended across surfaces.
- **Data product on top of operating product.** Data-product ARR as a
  fraction of total ARR, or logo-attach rate of the data product to
  the operating product.

The metric is the *ranking function* the CPO applies across surfaces.
Every surface PM is still allowed to optimize their local metric — but
when local optima conflict, the tie-break rule is *which alternative
better moves the cross-surface metric*, and that is a CPO call.

### Step 3 — Score every opportunity's *cross-surface footprint*

Take every candidate opportunity across every surface and score it on
three additional axes on top of whatever scheme (Lecture 2) the surface
uses locally:

- **Positive spillover.** Does completing this opportunity lift another
  surface's headline metric? (New consumer feature that increases
  marketplace-side supply; new API endpoint that reduces consumer-app
  support load.)
- **Negative spillover.** Does completing this opportunity cost another
  surface — new load on shared substrate, new support burden, new
  integration debt the platform surface has to eat?
- **Substrate touch.** Does this opportunity extend or degrade the
  shared substrate (identity, permissions, billing, observability,
  design system)?

Report these as a small table alongside the local RICE / WSJF number.
The CPO's cross-surface ranking uses the spillovers and substrate cost
as tie-breakers or as veto conditions.

### Step 4 — Set an allocation, not a ranking, at the top

Instead of "here is the ordered list of the next 40 items," publish a
**quarterly allocation across surfaces**: *this quarter, consumer gets
40% of engineering capacity, marketplace 30%, platform 20%, substrate
10%.* Allocation forces the strategic conversation up-front and stops
the top of the list from being colonized by whichever surface has the
loudest PM. Inside each allocation, the surface owner ranks their queue
with the scheme they've chosen. The CPO reviews the top items of each
queue only, not the whole queue.

The allocation rule for a growth-stage platform product a mature
starting point is often 3 : 3 : 3 : 1 (consumer : marketplace : platform
: substrate), adjusted quarterly by the cross-surface metric's trend.
Any allocation that puts substrate at zero for two consecutive quarters
is a broken allocation.

### Step 5 — Explicitly rank the shared substrate

Substrate work — identity, permissions, billing, observability, error
budgets, design system — is chronically under-invested because it
doesn't map cleanly to any surface's headline metric. Two moves:

- **Give it a surface entry** on the surface list. Substrate is a
  surface with an owner and a queue; treat it that way.
- **Set a floor allocation** (5–15% of engineering, depending on how
  much the substrate is compounding tech debt vs. compounding
  leverage) that the CPO defends against every quarter's "we need
  those points for the consumer sprint" ask.

## Multi-tenant twists

If the product is multi-tenant — one deployment, many customer
organizations, isolation guarantees — two more prioritization axes
appear:

- **Blast radius per tenant.** An opportunity that ships once to all
  tenants (a platform change) has a different risk profile than one
  that ships opt-in per tenant. The blast-radius column belongs on the
  ranking sheet.
- **Tenant-tier weighting.** If ARR is concentrated in a small number
  of enterprise tenants, their asks weight more but their asks are
  also more likely to be idiosyncratic. Weight *asks that generalize
  to N tenants* more than *asks specific to one tenant*, and be
  explicit about the weighting so it doesn't get argued fresh every
  quarter.

## API-first shapes

If a surface is API-first — the platform is the primary product — the
prioritization has to think in terms of *ecosystem outcomes*, not
consumer-app metrics:

- **Time-to-first-successful-call** for a new developer.
- **Endpoint deprecation cost** — an endpoint you shipped is now a
  contract you owe, so the effort to *remove* it is a real cost you
  underweighted at ship time.
- **Reference integration health** — the two or three integrations you
  ship yourself as demos; if they break, every third-party developer
  hits the same bug.

These belong on the platform-surface owner's queue with their own
scoring, and their cross-surface footprint belongs on the CPO's
allocation review.

## When to sunset a surface

Surfaces don't only get added. The ruthless-prioritization discipline
(Lecture 5) says: at every quarterly review, ask which surface has the
worst *marginal* case for continued investment. Sometimes the answer is
"none, they're all pulling their weight." Sometimes it's a surface
whose thesis has changed and that nobody has re-defended in a year.
Naming it and killing it is the CPO's job; nobody else has the
authority to.

## Boundaries this lecture keeps

- **How to *design* the shared substrate** (identity model, permissions
  model, isolation guarantees, observability plumbing) is deferred to
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)
  (level 25). The CPO's job is to *fund* substrate, not to specify it.
- **The marketplace-specific liquidity and take-rate mechanics** live in
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum)
  (level 30) and, where they touch pricing, in this module's own
  mod-006 (Pricing, Packaging, and Monetization).
- **The AI-native-product cross-surface case** — a model + retrieval +
  eval stack sitting under multiple product surfaces — is handled in
  mod-005 (metrics, experimentation, eval-driven decisions). This
  lecture gives you the ranking; mod-005 gives you the eval regime for
  the shared AI substrate underneath.

## Takeaways

- At two surfaces or more, single-surface ranking is not enough; the CPO
  ranks across surfaces, and the schemes you learned in Lecture 2 do
  not by themselves do that.
- Publish a surface list with owners and metrics; name the
  cross-surface metric that ties the portfolio together; score every
  opportunity's spillover and substrate touch.
- Publish an *allocation* across surfaces, not a global ordered list;
  let each surface owner rank inside their allocation.
- Substrate is a surface. Give it an owner and a floor allocation, or
  it will silently break the other surfaces.
- Sunset candidates are legitimate portfolio moves; nobody but the CPO
  is positioned to make the call.

Lecture 5 turns to the harder half of ruthless prioritization: killing
work you already started, past the point where doing so is comfortable.
