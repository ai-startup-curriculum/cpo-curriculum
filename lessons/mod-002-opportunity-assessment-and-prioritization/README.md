# mod-002 — Opportunity Assessment and Ruthless Prioritization

> The founding CPO's second job — after making sure you're building
> something someone will pull out of your hands (mod-001) — is making
> sure the thing you build *next* is the thing that most moves the
> business, and being willing to kill the last thing to do it.

## Why this module exists

Prioritization is where product organizations either compound their
advantage or slowly waste it. It is also the place where founding CPOs
make their most-visible mistakes: ranking feature lists that were never
opportunities, picking a scoring scheme off a blog without knowing what
it hides, letting each product surface's PM run a locally-optimal
roadmap whose sum is not what the company should be doing, and refusing
to kill work that no longer earns its keep because the sunk cost, the
endowment, or the last board deck won't let them.

This module gives you the authoring craft, the scoring math, the
cross-surface allocation move, and the kill discipline — bounded above
by the company thesis and below by the runway — that lets you make
ranking calls a stranger can defend and your team can commit to.

## Learning outcomes

By the end of this module you can:

1. **Author** an opportunity as a bounded, four-sentence problem
   statement — Cagan's opportunity-assessment shape, Torres's
   customer-worded opportunity node, Blank's problem-interview
   evidence standard — rather than as a feature.
2. **Score and rank** opportunities with a scheme (RICE, ICE, WSJF,
   or Kano-first classification) chosen to match the ranking
   question, and know the mathematical incompatibilities that force
   you to pick one and stick with it.
3. **Distinguish** base-rate opportunities (funnel, retention,
   activation) from strategic opportunities (new surface, segment,
   or tier) and route each to a decision cadence — weekly experiment
   queue vs. quarterly commit-or-kill — appropriate to its
   reference-class shape.
4. **Prioritize across surfaces** in a multi-tenant / API-first /
   platform-shaped product line, publishing an allocation across
   surfaces rather than a global ordered list, with a cross-surface
   metric that the CPO uses as tie-break.
5. **Kill** in-flight work with less ego than starting it — knowing
   the four biases (sunk cost, endowment, consistency, loss
   aversion) and their counter-moves, running a quarterly kill
   review as a governance ritual, and separating the person from
   the project.
6. **Consume** the company thesis (authored at level 20 in
   [founder-ceo-curriculum](https://github.com/ai-startup-curriculum/founder-ceo-curriculum))
   and the runway (authored at level 40 in
   [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum))
   as boundary constraints — and know when to escalate a
   thesis-runway mismatch rather than silently discount either.

## Prerequisites

- [mod-001](../mod-001-customer-discovery-to-pmf/README.md) —
  discovery vocabulary, opportunity solution trees, the four-sentence
  hypothesis frame. This module extends that frame into the ranking
  queue.
- A rough understanding of your company's thesis and runway. If you
  don't have either, produce a first-cut with your founder-CEO before
  starting Exercise 5 — the exercises depend on real inputs.
- One product you can name concretely — the one you're working on, a
  prior one whose numbers you remember, or a plausible synthetic you
  are willing to defend the shape of.

## Syllabus

| # | Piece | Type | Est. time |
|---|---|---|---|
| 1 | [Opportunities as bounded problems, not feature lists](lectures/01-opportunities-as-bounded-problems.md) | Lecture | 30 min |
| 2 | [Scoring schemes: RICE, ICE, WSJF, Kano — and why they don't compose](lectures/02-scoring-schemes-and-their-incompatibilities.md) | Lecture | 45 min |
| 3 | [Base-rate vs strategic opportunities, and cadence routing](lectures/03-base-rate-vs-strategic-opportunities.md) | Lecture | 30 min |
| 4 | [Multi-surface ranking: the CPO as portfolio ranker](lectures/04-multi-surface-ranking.md) | Lecture | 45 min |
| 5 | [Killing work you already started](lectures/05-killing-work-you-already-started.md) | Lecture | 45 min |
| 6 | [Thesis and runway as boundary constraints](lectures/06-thesis-and-runway-as-boundaries.md) | Lecture | 30 min |
| 1 | [Opportunity assessment authoring for three real bets](exercises/exercise-01-opportunity-assessment-authoring-for-three-real-bets.md) | Exercise | 3 hrs |
| 2 | [RICE vs WSJF vs Kano scheme-choice drill](exercises/exercise-02-rice-vs-wsjf-vs-kano-scheme-choice-drill.md) | Exercise | 2 hrs |
| 3 | [Multi-surface ranking drill](exercises/exercise-03-multi-surface-ranking-drill.md) | Exercise | 3 hrs |
| 4 | [Kill-list authoring with bias check](exercises/exercise-04-kill-list-authoring-with-bias-check.md) | Exercise | 3 hrs |
| 5 | [Prioritization under a runway constraint](exercises/exercise-05-prioritization-under-runway-constraint.md) | Exercise | 2 hrs |
| R | [Resources — books, essays, and primary sources](resources.md) | Reference | — |

## How to work this module

Read the lectures in order. Lecture 1 sets the authoring frame that
everything else assumes; Lecture 2 introduces the scoring vocabulary;
Lecture 3 explains why not all opportunities belong in the same
queue; Lecture 4 goes up a level to the portfolio; Lecture 5 turns to
the kill discipline; and Lecture 6 puts both boundaries — thesis
above, runway below — around the whole enterprise.

Do the exercises against a real product. The failure modes this
module teaches — solution-capture in the opportunity node, false
precision in the scoring, cross-surface externalities, sunk-cost
bias in the kill review — are almost invisible in toy cases. If you
must use a synthetic, defend its shape up-front and stay in-character.

Exercises 1 → 5 build on each other. Exercise 1 produces the
opportunities Exercise 2 ranks and Exercise 3 places across surfaces;
Exercise 4 kills; Exercise 5 forces all of it through three runway
scenarios so you feel where the discipline pinches.

## Deliverables

- Three opportunity assessments plus a reviewer's memo
  ([Exercise 1](exercises/exercise-01-opportunity-assessment-authoring-for-three-real-bets.md)).
- Three scheme-choice memos plus one scored ranking
  ([Exercise 2](exercises/exercise-02-rice-vs-wsjf-vs-kano-scheme-choice-drill.md)).
- Surface list, cross-surface metric, spillover table, and
  quarterly allocation memo
  ([Exercise 3](exercises/exercise-03-multi-surface-ranking-drill.md)).
- Kill list with bias-check annotations plus swap plan
  ([Exercise 4](exercises/exercise-04-kill-list-authoring-with-bias-check.md)).
- Three prioritization memos under three runways plus a
  prioritization-context sheet
  ([Exercise 5](exercises/exercise-05-prioritization-under-runway-constraint.md)).

## Boundaries this module keeps

- **Discovery craft** — hypotheses, interviews, JTBD synthesis, PMF
  measurement — is owned by
  [mod-001](../mod-001-customer-discovery-to-pmf/README.md). This
  module consumes the opportunity nodes discovery produces and
  ranks them; it does not re-teach the discovery loop.
- **Company thesis authoring** — Rumelt-shape strategy, board
  narrative, theory of winning — is level-20 work owned by
  [founder-ceo-curriculum](https://github.com/ai-startup-curriculum/founder-ceo-curriculum).
  The CPO consumes the thesis (Lecture 6); they do not author it
  alone.
- **Runway / burn modeling** and the raise decision are level-40
  work owned by
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum).
  The CPO consumes the runway line (Lecture 6); they do not model
  the burn.
- **Roadmap craft** — Now/Next/Later, OKRs at CPO scope,
  multi-quarter strategy, three-audience roadmap read-outs — is the
  subject of
  [mod-003](../mod-003-roadmap-outcomes-and-strategy/README.md).
  Prioritization feeds the roadmap; it doesn't replace it.
- **Delivery cadence, PRDs, and the discovery / delivery rhythm**
  are the subject of
  [mod-004](../mod-004-discovery-delivery-cadence/README.md).
- **Metrics, experiments, and evals** — the instrumentation that
  makes base-rate work measurable — are the subject of
  [mod-005](../mod-005-metrics-experimentation-and-ai-evals/README.md).
- **Pricing, packaging, and monetization** — including the pricing
  moves that dominate the queue under a tight runway — are the
  subject of
  [mod-006](../mod-006-pricing-packaging-and-monetization/README.md).
- **Engineering-side architectural sequencing** (which platform
  choice sequences the strategic bet queue) is level-25 work owned
  by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum).

## Sources this module leans on

- Marty Cagan, *Inspired: How to Create Tech Products Customers Love*
  (2nd ed.), Wiley, 2017 —
  [SVPG book page](https://www.svpg.com/inspired-how-to-create-products-customers-love/).
- Teresa Torres, *Continuous Discovery Habits*, Product Talk, 2021 —
  [producttalk.org/continuous-discovery-habits](https://www.producttalk.org/continuous-discovery-habits/).
- Sean McBride, "RICE: Simple prioritization for product managers,"
  Intercom, 2016 —
  [intercom.com/blog/rice-simple-prioritization-for-product-managers](https://www.intercom.com/blog/rice-simple-prioritization-for-product-managers/).
- Sean Ellis & Morgan Brown, *Hacking Growth*, Currency, 2017 —
  [hachettebookgroup.com](https://www.hachettebookgroup.com/titles/sean-ellis/hacking-growth/9780451497215/).
- Don Reinertsen, *The Principles of Product Development Flow*,
  Celeritas, 2009 —
  [celeritaspublishing.com](https://celeritaspublishing.com/product/the-principles-of-product-development-flow/).
- Noriaki Kano et al., "Attractive Quality and Must-Be Quality,"
  1984 — [ASQ Kano-model summary](https://asq.org/quality-resources/kano-model).
- Daniel Kahneman, *Thinking, Fast and Slow*, Farrar, Straus and
  Giroux, 2011 —
  [us.macmillan.com](https://us.macmillan.com/books/9780374533557/thinkingfastandslow).
- Richard Rumelt, *Good Strategy Bad Strategy*, Crown Business, 2011 —
  [crownpublishing.com](https://www.crownpublishing.com/archives/feature/good-strategy-bad-strategy-richard-rumelt).
- Jim Collins, *Good to Great*, HarperBusiness, 2001 —
  [jimcollins.com](https://www.jimcollins.com/books/good-to-great.html).
- Robert Cialdini, *Influence: The Psychology of Persuasion* (rev.
  ed.), Harper Business, 2006 —
  [influenceatwork.com](https://www.influenceatwork.com/).

See [resources.md](resources.md) for the full, linked reading list.
Additional sources are cited inline in each lecture and exercise.
