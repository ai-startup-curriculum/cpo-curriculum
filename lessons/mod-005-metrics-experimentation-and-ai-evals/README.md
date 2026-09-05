# mod-005 — Metrics, Experimentation, and Eval-Driven Product Decisions

> The founding CPO's fifth job — after finding pull (mod-001),
> ranking the queue (mod-002), authoring the multi-quarter
> strategy the roadmap makes concrete (mod-003), and running
> the weekly discovery/delivery rhythm the roadmap ships
> inside (mod-004) — is running the **measurement regime**
> that tells the team whether any of it worked. At pre-seed
> and seed, that regime has three legs: a product-analytics
> shape beyond PMF, an experimentation program you can
> actually power at low traffic, and — for AI-substrate
> products — an eval discipline that replaces most A/B tests
> because A/B does not work on stochastic outputs.

## Why this module exists

Ask a first-time founding CPO how they measure whether the
product is working, and the answer will fall into one of
three shapes. The first is *the top-line dashboard*: MRR,
signups, DAUs, a single number that goes up and to the
right (or does not) and produces no diagnosis. The second
is *the vanity funnel*: a set of counts, ordered, with no
denominators and no cohorts, so nothing about the shape
reveals whether the product is retaining anyone. The third,
increasingly common in 2026, is *the eval theatre*: a
notebook of prompt outputs the team reads out at demo, with
no labeled dataset, no grader calibration, and no threshold
you can lose on — so the LLM feature ships on vibes.

None of these is a measurement regime. A regime is a
coordinated set of *instruments* — a defended north-star
metric, two to three input metrics that move it, activation
and retention and cohort curves that make retention honest,
a funnel with denominators, an experiment discipline sized
to your traffic, an eval suite whose thresholds you can
lose on, and — under all of it — enough SQL literacy that
the CPO writes queries against the events tables rather
than reading a dashboard someone else defined.

This module teaches that regime at the pre-seed → Series-A
scale where a founding CPO actually operates: low traffic
(where naïve A/B tests silently underpower), thin analytics
stack (product analytics + a warehouse + increasingly a
reverse-ETL back), and AI substrate in most 2026 postings
(where the *decision surface* is an eval, not an
experiment). It folds AI-native product management into the
metrics + eval regime rather than treating it as a separate
competency, because at CPO scope for a small AI-native team,
the two are the same job.

## Learning outcomes

By the end of this module you can:

1. **Design and defend** a metric taxonomy that survives 12
   months without a rewrite — a single **north-star metric**
   in the Sean-Ellis / Amplitude shape, two to three **input
   metrics** that mechanically move it (Andrew Chen's
   growth-loop framing), and a small set of **guardrails**
   that catch the ways a moving north-star can lie.
2. **Ship a product-analytics regime beyond PMF** — funnel
   definitions with denominators, **activation** as a
   defensible event, **retention curves** by cohort,
   NUX / onboarding drop-off, **feature-adoption depth**
   (breadth vs. depth), and **revenue-per-account** cohorts
   for B2B — grounded in the Reforge / Amplitude / Mixpanel
   working vocabulary the founding growth-PM job now
   assumes.
3. **Read the analytics stack well enough to write your own
   SQL against the events tables** — the product-analytics
   tool over the same warehouse the data team queries,
   reverse-ETL back into the CRM and product, event-model
   discipline (Segment / RudderStack tracking plan) — as
   the Solidroad / Reducto-shape expectation of a first PM
   who *defines and moves* metrics rather than reading a
   dashboard someone else defined.
4. **Run an experimentation program at pre-seed → Series-A
   scale** — hypothesis writing, minimum-detectable-effect
   (MDE) sizing, guard-metric design, launch / no-launch
   decision criteria — and diagnose the underpowered-A/B
   failure modes that dominate at low traffic (peeking,
   p-hacking, ratio-metric variance, novelty effect,
   Simpson's-paradox blends).
5. **Choose the right causal-inference method for the
   traffic you actually have** — when to run an A/B test,
   when to run a **holdout / geo split**, when to run a
   **difference-in-differences** analysis, when to fall
   back to **interrupted-time-series** — and defend the
   choice against a "just run an A/B" reflex you cannot
   afford.
6. **Adopt eval-driven product decisions for AI/LLM-native
   product surfaces** — the Hamel Husain evals discipline,
   Chip Huyen's *AI Engineering* chapters on evaluation,
   **LLM-as-judge** with calibration against human review,
   dataset-hosting patterns (Braintrust / Langfuse /
   OpenAI Evals-shape), and the point at which an eval
   suite replaces an A/B experiment as the launch gate.
7. **Reason about the cost / latency / quality Pareto** for
   AI-substrate features — model tier selection,
   context-window trade-offs, streaming as a UX affordance,
   caching, batching — as a first-class CPO decision
   surface, not a delegated eng-only trade-off.
8. **Consume** the deeper craft at the level boundaries —
   the data-platform architecture underneath is
   [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)
   (level 25); the app-side eval methodology at depth is
   [ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning)
   (level 30); the statistical-calibration depth on
   grader models is
   [model-evaluation-engineer-learning](https://github.com/ai-engineering-curriculum/model-evaluation-engineer-learning)
   (level 30) — and know what the CPO authors vs. consumes.

## Prerequisites

- [mod-001](../mod-001-customer-discovery-to-pmf/README.md) —
  PMF measurement (Sean Ellis 40% survey, retention curves,
  pull). This module is the *post-PMF* measurement regime;
  the PMF instruments themselves are mod-001's.
- [mod-002](../mod-002-opportunity-assessment-and-prioritization/README.md) —
  the queue the experiments run against. An experiment
  without an opportunity underneath it is a ceremony.
- [mod-003](../mod-003-roadmap-outcomes-and-strategy/README.md) —
  outcomes-based roadmap. The north-star and input metrics
  this module defends are what the roadmap's outcomes point
  at.
- [mod-004](../mod-004-discovery-delivery-cadence/README.md) —
  the weekly rhythm the experiments and eval sweeps run
  inside. Lecture 5 of mod-004 introduces evals as a
  product-decision surface; this module owns the eval
  regime itself.
- One product you can name concretely, with enough traffic
  (or a plausible traffic estimate) that MDE sizing is a
  real question, and — for the LLM-side lectures — an
  AI-substrate surface you can imagine iterating on.
- A working SQL literacy at the *SELECT / JOIN / GROUP BY /
  window-function* level. If you don't have it, work
  Lecture 3's inline drill before Exercise 6. The
  CTO-curriculum data-engineering module is deeper than
  this one needs; this module needs "can write your own
  query," not "can design a warehouse."

## Syllabus

| # | Piece | Type | Est. time |
|---|---|---|---|
| 1 | [North-star metric + input metrics: designing a taxonomy that lasts 12 months](lectures/01-north-star-and-input-metric-taxonomy.md) | Lecture | 60 min |
| 2 | [Analytics beyond PMF: funnels, activation, retention, cohorts, feature-adoption depth](lectures/02-analytics-regime-beyond-pmf.md) | Lecture | 75 min |
| 3 | [Reading the analytics stack and writing your own SQL against events](lectures/03-analytics-stack-and-sql-against-events.md) | Lecture | 75 min |
| 4 | [Experimentation at pre-seed → Series-A scale: hypothesis, MDE, guard metrics, launch decisions](lectures/04-experimentation-at-pre-seed-to-series-a.md) | Lecture | 75 min |
| 5 | [When A/B fails: holdouts, diff-in-diff, interrupted-time-series](lectures/05-quasi-experimental-methods-when-ab-fails.md) | Lecture | 60 min |
| 6 | [Eval-driven product decisions for LLM-native products](lectures/06-eval-driven-decisions-for-llm-products.md) | Lecture | 75 min |
| 7 | [Cost / latency / quality: the AI-substrate Pareto](lectures/07-cost-latency-quality-pareto.md) | Lecture | 60 min |
| 1 | [North-star and input-metric authoring](exercises/exercise-01-north-star-and-input-metric-authoring.md) | Exercise | 3 hrs |
| 2 | [Activation / retention / cohort analysis drill](exercises/exercise-02-activation-retention-cohort-analysis-drill.md) | Exercise | 3 hrs |
| 3 | [A/B MDE sizing and guard-metric drill](exercises/exercise-03-ab-test-mde-sizing-and-guard-metric-drill.md) | Exercise | 3 hrs |
| 4 | [LLM eval suite authoring for one agent](exercises/exercise-04-llm-eval-suite-authoring-for-one-agent.md) | Exercise | 4 hrs |
| 5 | [Cost / latency / quality Pareto drill](exercises/exercise-05-cost-latency-quality-pareto-drill.md) | Exercise | 3 hrs |
| 6 | [SQL against events tables drill](exercises/exercise-06-sql-against-events-tables-drill.md) | Exercise | 3 hrs |
| R | [Resources — books, essays, and primary sources](resources.md) | Reference | — |

## How to work this module

Read the lectures in order. Lecture 1 fixes the *taxonomy*
the rest of the module measures against — north-star,
inputs, guardrails — because a measurement regime that
starts with a funnel and works up to the metric that
matters is a regime that has already lost. Lectures 2 and 3
give you the *analytics muscle*: the shape of the curves a
post-PMF product runs against, and the stack literacy that
lets you author them yourself. Lectures 4 and 5 give you
the *experimentation muscle*: the A/B discipline you can
actually power at your traffic, and the causal-inference
fallbacks for when you cannot. Lectures 6 and 7 give you
the *AI-substrate muscle*: the eval regime that replaces
A/B for stochastic outputs, and the cost / latency /
quality Pareto you own.

Do the exercises against real data. Every exercise in this
module benefits enormously from being run against an actual
events table or a real product surface — even a synthetic
CSV of 90 days of pageviews is better than an entirely
made-up example. If your product has zero users, mod-005
work is premature; go back to mod-001 and get pull first.
The two exceptions are Exercises 3 and 4: MDE sizing and
eval-suite authoring can be worked productively against a
plausible synthetic if you don't yet have traffic or a
labeled dataset.

Exercises 1 → 6 build on each other. Exercise 1 defends the
metric taxonomy. Exercise 2 is the honest retention /
cohort read on the taxonomy you just authored — which
usually reveals that the north star you picked is not
moving in the direction you assumed. Exercise 3 sizes the
next A/B against the traffic you actually have; Exercise 4
authors the eval suite for the AI-substrate slice most
likely to ship next; Exercise 5 works the cost / latency /
quality Pareto for the same slice; Exercise 6 is a pure
SQL drill that lets you check any of the above without
depending on someone else's dashboard.

## Deliverables

- One **metric taxonomy memo** — north-star metric, two to
  three input metrics, three to five guardrails, plus the
  12-month defense of why this shape does not need a
  rewrite ([Exercise 1](exercises/exercise-01-north-star-and-input-metric-authoring.md)).
- One **cohort / retention / activation analysis** for the
  product's largest segment, with a defensible activation
  event, an N ≥ 12-period retention curve, and a
  feature-adoption-depth read
  ([Exercise 2](exercises/exercise-02-activation-retention-cohort-analysis-drill.md)).
- One **A/B experiment brief** — hypothesis, primary
  metric, guard metrics, MDE calculation, traffic
  requirement, decision rule, sequential-testing / peeking
  discipline
  ([Exercise 3](exercises/exercise-03-ab-test-mde-sizing-and-guard-metric-drill.md)).
- One **LLM eval suite** for one agent or LLM-substrate
  slice — task definition, dataset (50–200 examples),
  grading approach (rule-based / LLM-as-judge / human),
  calibration plan for the judge, launch threshold
  ([Exercise 4](exercises/exercise-04-llm-eval-suite-authoring-for-one-agent.md)).
- One **cost / latency / quality Pareto memo** for the
  same slice — three plausible configurations, the
  measured or projected numbers on each axis, the
  configuration you'd ship and why
  ([Exercise 5](exercises/exercise-05-cost-latency-quality-pareto-drill.md)).
- One **SQL notebook** — five queries against a real (or
  plausible synthetic) events table, at increasing
  difficulty, covering daily active users, funnel
  conversion, cohort retention, feature adoption depth,
  and a guard-metric guardrail check
  ([Exercise 6](exercises/exercise-06-sql-against-events-tables-drill.md)).

## Boundaries this module keeps

- **PMF measurement** — Sean Ellis 40% survey, retention as
  a *fit* signal, organic pull — is owned by
  [mod-001](../mod-001-customer-discovery-to-pmf/README.md).
  This module is the *post-PMF* measurement regime; a
  product that is not pulled yet does not need most of
  what's in here.
- **Opportunity ranking and killing** is owned by
  [mod-002](../mod-002-opportunity-assessment-and-prioritization/README.md).
  Experiments and evals evaluate opportunities *the queue
  has already ranked*; they do not re-rank the queue.
- **Roadmap outcomes and OKR authoring** is owned by
  [mod-003](../mod-003-roadmap-outcomes-and-strategy/README.md).
  The metric taxonomy this module defends is what the
  roadmap's outcomes point at.
- **The weekly discovery / delivery cadence** the
  experiments run inside is owned by
  [mod-004](../mod-004-discovery-delivery-cadence/README.md).
  Lecture 5 of mod-004 introduces evals as a
  product-decision *cadence*; this module owns the eval
  regime itself.
- **Pricing and packaging** experiments — pricing-page A/B,
  willingness-to-pay research, credit / metering as a
  monetization surface — are owned by
  [mod-006](../mod-006-pricing-packaging-and-monetization/README.md).
  Lecture 4's experimentation discipline applies; the
  pricing craft itself does not.
- **The founder / eng / GTM relationship** underneath a
  low-power A/B disagreement is owned by
  [mod-007](../mod-007-working-with-founders-eng-and-gtm/README.md).
- **Data-platform architecture** — how the warehouse is
  built, ELT vs. ETL, dbt modeling, reverse-ETL vendor
  selection at depth, schema evolution, RBAC — is
  level-25 work owned by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum).
  The CPO *consumes* the stack (Lecture 3), reads it well
  enough to write SQL against it, and asks for the tables
  they need; the CTO / data lead authors the platform.
- **App-side eval methodology at depth** — building the
  eval harness itself, prompt-versioning tooling,
  trajectory replay, agentic-test-suite architecture — is
  level-30 work owned by
  [ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning).
  Lecture 6 teaches the CPO-scope decisions (what to eval
  for, how to grade, what threshold); the AI-eval engineer
  authors the harness.
- **Statistical calibration depth for grader models** —
  inter-annotator agreement, Cohen's κ, judge-model bias
  measurement, human-review sampling design at depth — is
  level-30 work owned by
  [model-evaluation-engineer-learning](https://github.com/ai-engineering-curriculum/model-evaluation-engineer-learning).
  Lecture 6 teaches the CPO-scope calibration discipline
  (spot-check ~10% of judge outputs against human review,
  track judge/human agreement over time); the
  model-evaluation engineer authors the statistical rigor.
- **Deep causal inference** — synthetic-control methods,
  regression discontinuity, instrumental variables,
  bandit-style adaptive experiments at depth — is out of
  scope. Lecture 5 teaches the three fallbacks a founding
  CPO can actually run; deeper causal-inference reading
  is cited in [resources.md](resources.md).

## Sources this module leans on

- Sean Ellis & Morgan Brown, *Hacking Growth*, Currency,
  2017 — [hackinggrowth.com](https://hackinggrowth.com/).
- Andrew Chen, *The Cold Start Problem*, Harper Business,
  2021 — [andrewchen.com/the-cold-start-problem-book](https://andrewchen.com/the-cold-start-problem-book/).
- Amplitude, "North Star Playbook" (Amplitude Engineering),
  updated periodically —
  [amplitude.com/books/north-star](https://amplitude.com/books/north-star).
- Reforge Growth Series (Brian Balfour et al.) — the
  reference curriculum for growth-model, retention, and
  activation frameworks used in Lecture 2 —
  [reforge.com/programs](https://www.reforge.com/programs).
- Ronny Kohavi, Diane Tang & Ya Xu, *Trustworthy Online
  Controlled Experiments*, Cambridge University Press,
  2020 —
  [experimentguide.com](https://experimentguide.com/) —
  the canonical practitioner reference for online A/B
  design.
- Ron Kohavi et al., "Online Controlled Experiments and
  A/B Testing," in *Encyclopedia of Machine Learning and
  Data Mining*, 2016 — see the pre-print listing at
  [exp-platform.com](https://exp-platform.com/).
- Joshua Angrist & Jörn-Steffen Pischke, *Mostly Harmless
  Econometrics*, Princeton, 2009 — the reference for
  diff-in-diff and quasi-experimental design used in
  Lecture 5 — [mostlyharmlesseconometrics.com](https://www.mostlyharmlesseconometrics.com/).
- Chip Huyen, *AI Engineering: Building Applications with
  Foundation Models*, O'Reilly, 2024 — Chapter 3
  ("Evaluation Methodology") and Chapter 4 ("Evaluating
  AI Systems") are the reference used through Lecture 6 —
  [oreilly.com/library/view/ai-engineering/9781098166298](https://www.oreilly.com/library/view/ai-engineering/9781098166298/).
- Hamel Husain, "Your AI Product Needs Evals," May 2024 —
  [hamel.dev/blog/posts/evals](https://hamel.dev/blog/posts/evals/) —
  and the follow-up "Field Notes on LLM Evaluation" and
  "Creating a LLM-as-a-Judge That Drives Business
  Results" at [hamel.dev](https://hamel.dev/).
- Eugene Yan, "Evaluation & Hallucination Detection for
  Abstractive Summaries," and related essays at
  [eugeneyan.com](https://eugeneyan.com/) — practitioner
  writing on the LLM-as-judge calibration discipline.
- Anthropic, "Prompt Engineering" and "Evaluate Prompts"
  documentation —
  [docs.anthropic.com](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
  and
  [docs.anthropic.com/en/docs/test-and-evaluate](https://docs.anthropic.com/en/docs/test-and-evaluate/develop-tests).
- OpenAI, "OpenAI Evals" —
  [github.com/openai/evals](https://github.com/openai/evals) —
  and the Model Spec / evaluation blog posts at
  [openai.com/index/introducing-the-model-spec](https://openai.com/index/introducing-the-model-spec/).
- Segment, "Analytics Academy — Data Collection" —
  [segment.com/academy](https://segment.com/academy/) —
  the reference for event-model discipline used in
  Lecture 3.

See [resources.md](resources.md) for the full, linked
reading list. Additional sources are cited inline in each
lecture and exercise.
