# Exercise 3 — Multi-surface ranking drill

**Time:** ~3 hours. **Deliverable:** a surface list, a cross-surface
metric, a scored opportunity spillover table, and a one-page quarterly
allocation memo — for a multi-surface product line.

## Purpose

Practice the CPO's most differentiated ranking move: allocating
capacity *across* surfaces rather than inside one queue. The lecture
behind this is
[Lecture 4](../lectures/04-multi-surface-ranking.md).

## The product

Choose one of the two sample products below, or bring your own real
multi-surface product (recommended if you have one; skip the sample if
so).

### Sample product 1 — Vertical AI-native SaaS with a data-export tier

- **Consumer / operator app** — the primary workflow tool used by an
  in-market operator role (pick a vertical: legal ops, revenue ops,
  clinical ops, whichever you know best).
- **API / platform surface** — programmatic access for enterprise
  buyers to feed the same workflow from their existing systems.
- **Data / insights product** — a benchmark / market-intelligence tier
  built on aggregate anonymised usage data across accounts, sold as a
  separate SKU.
- **Shared substrate** — auth, permissions, billing, observability, the
  eval / model-serving stack for the AI features.

### Sample product 2 — Two-sided marketplace with a supply-ops toolkit

- **Buyer app** — consumer-facing discovery + transaction.
- **Seller app** — listing, inventory, order management for the
  supply side.
- **Supply-operations SaaS** — a paid toolkit for professional
  sellers (bulk listing, reprice, analytics), part of the retention
  play for high-volume sellers.
- **Public API** — read/write endpoints third-party listing tools
  build on.
- **Shared substrate** — identity, payments, trust & safety, search
  infra.

## Tasks

### Part 1 — Surface list (30 min)

Publish a one-page surface list following the shape in
[Lecture 4, Step 1](../lectures/04-multi-surface-ranking.md#step-1--publish-the-surface-list-with-owners-and-metrics).
Include, per surface:

- What it is (one sentence).
- Who its users are (one sentence).
- Owner today (name a real or hypothetical PM; note *unowned* if
  applicable — that's a finding).
- Two or three metrics it's optimized for.
- Current stage: *discovery / PMF-searching / scaling / mature /
  sunset candidate*.

Include **shared substrate** as its own row on the list. Do not skip
it.

### Part 2 — Cross-surface metric (20 min)

Name one metric that captures whether the *whole* portfolio is
compounding, not any single surface. See
[Lecture 4, Step 2](../lectures/04-multi-surface-ranking.md#step-2--name-the-cross-surface-metric)
for shape hints (marketplace liquidity, platform-attributable ARR,
contribution margin per active user, data-product logo-attach).

Write:

- The metric definition (formula-level, not vibes).
- Why this metric and not the alternatives you considered.
- Where the data comes from and who computes it.
- The current baseline (a real number if you have one, an ordered
  guess with your uncertainty if you don't).

### Part 3 — Opportunity spillover table (90 min)

Pick **eight** candidate opportunities across the surfaces — aim for
at least one per surface, and at least one on the shared substrate.
For each opportunity, score three columns *in addition to* whichever
local ranking scheme its surface uses:

- **Positive spillover** — 0/1/2: does completing this lift another
  named surface's headline metric? Name the surface(s) if 1 or 2.
- **Negative spillover** — 0/1/2: does completing this cost another
  surface (load, support, integration debt)? Name the surface(s) if
  1 or 2.
- **Substrate touch** — 0/1/2: does this extend / degrade shared
  substrate? Name the substrate area if non-zero.

Do not compute a single blended cross-surface score. Present the
table with the local rank and the three spillover columns; the point
of the exercise is that the CPO reads across the columns and makes a
judgment, not that a formula picks the winner.

### Part 4 — Quarterly allocation memo (60 min)

One page. Include:

- **Allocation across surfaces this quarter** — percentages of
  engineering / design capacity across the surface list, including
  shared substrate. Substrate below 5% for two consecutive quarters
  is not an allowed answer.
- **Top item from each surface's queue** — one line each, with the
  local rank and a note on cross-surface spillover.
- **One item you are *not* funding this quarter that you'd like to** —
  and why the allocation rules it out. Explicitly naming what you're
  giving up is the discipline.
- **Sunset candidate, if any** — a surface (or a sub-surface / feature
  area) you're considering wind-down for and the question that
  would resolve it.
- **Signatures.** Who approves this allocation: at minimum the CPO;
  at a real startup, also the founder-CEO and CTO.

## Starter guidance

- **Do the surface list first.** Trying to score opportunities before
  you've named surfaces produces scores that ignore the point of the
  exercise.
- **Cross-surface metric is the hardest single artifact.** If you
  find yourself writing "user satisfaction" or "growth," you're too
  vague — go concrete or the CPO's tie-break rule has nothing to
  cite.
- **Substrate items always look boring.** They score low on any
  headline-metric scheme. That's exactly why the exercise makes you
  hold a floor allocation for them.
- **When in doubt, err on the side of naming a sunset candidate.**
  Every quarter has one; the surface owner is the last person likely
  to name theirs.

## Acceptance criteria

- Surface list is one page, includes every surface (including
  substrate), and names owners and metrics.
- Cross-surface metric has a formula-level definition and a stated
  data source.
- Spillover table has eight opportunities, spans surfaces, and shows
  the local rank plus positive / negative / substrate columns.
- Allocation memo has percentages summing to 100%, names the top
  item per surface, explicitly names an item *not* funded, and names
  a sunset candidate or defends the absence of one.
- Substrate allocation is ≥ 5% or the memo explicitly defends the
  exception.

## Common failure modes

- **"Everything is a priority."** An allocation that gives each
  surface between 20% and 30% is often the mark of an unmade
  decision. The point of the memo is to make the decision, not to
  average.
- **Consumer surface eats the allocation.** Consumer metrics are
  loudest; consumer PMs are usually most senior. Substrate,
  platform, and data surfaces get starved by default. Notice this
  when it's happening.
- **Cross-surface metric that no one owns.** If nobody on the org
  chart is on the hook to move the metric you named, the metric is
  aspirational, not operational.
- **Spillover table with all zeros.** Either the surfaces you picked
  are more independent than they look — investigate — or you're not
  looking hard enough at the shared substrate and the load
  externalities.

## Source alignment

- Ben Thompson's *Aggregation Theory* frame for "where does demand
  aggregate?" — [Thompson, *Stratechery*, 2015 —
  stratechery.com/2015/aggregation-theory](https://stratechery.com/2015/aggregation-theory/).
- Sangeet Choudary's platform economics — [Choudary, *Platform
  Scale*, 2015 —
  platformed.info](https://platformed.info/books/); [Van Alstyne,
  Parker & Choudary, "Pipelines, Platforms, and the New Rules of
  Strategy," *HBR*, April 2016 —
  hbr.org/2016/04/pipelines-platforms-and-the-new-rules-of-strategy](https://hbr.org/2016/04/pipelines-platforms-and-the-new-rules-of-strategy).
- The shape of the exercise draws from
  [Lecture 4 of this
  module](../lectures/04-multi-surface-ranking.md); use it as the
  procedural reference.
