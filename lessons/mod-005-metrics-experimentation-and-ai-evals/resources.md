# Resources — mod-005 Metrics, Experimentation, and Eval-Driven Product Decisions

Primary sources for the material in this module. Prefer the books
over the blog posts for depth; prefer the essays and online
calculators when you need a single-sitting refresher or a working
tool. Every URL below is either the author's canonical page, the
publisher's page, the official documentation host, or an archived
copy where the original has moved or lapsed.

## North-star metrics, input metrics, and growth loops (Ellis, Chen, Amplitude, Reforge)

- Sean Ellis & Morgan Brown, *Hacking Growth: How Today's Fastest-
  Growing Companies Drive Breakout Success*, Currency, 2017 —
  [hackinggrowth.com](https://hackinggrowth.com/). Chapter 3 is
  the source of the north-star framing used in
  [Lecture 1](lectures/01-north-star-and-input-metric-taxonomy.md)
  and [Exercise 1](exercises/exercise-01-north-star-and-input-metric-authoring.md) —
  the north-star as a leadership call, not a data-team deliverable,
  and the "one metric that most accurately captures the core value"
  definition.
- Andrew Chen, *The Cold Start Problem: How to Start and Scale
  Network Effects*, Harper Business, 2021 —
  [andrewchen.com/the-cold-start-problem-book](https://andrewchen.com/the-cold-start-problem-book/).
  Part IV ("The Ceiling") is the source of the input-metric /
  growth-loop decomposition that Lecture 1 and Exercise 1 build on.
  The *seven-friends-in-ten-days* Facebook activation example is
  Chen's canonical case; cited in
  [Lecture 2](lectures/02-analytics-regime-beyond-pmf.md) and
  [Exercise 2](exercises/exercise-02-activation-retention-cohort-analysis-drill.md).
- Amplitude, *The North Star Playbook*, updated periodically —
  [amplitude.com/books/north-star](https://amplitude.com/books/north-star).
  The practitioner's reference for the operational north-star
  definition, worked case studies (Airbnb nights-booked, Amplitude's
  own weekly-learning-users), and the input-metric decomposition
  pattern. Cited throughout Lecture 1 and Exercise 1.
- Brian Balfour & Reforge, "The Reforge Growth Model" and the
  Growth / Retention / Activation program essays at
  [reforge.com/blog](https://www.reforge.com/blog) and
  [reforge.com/programs](https://www.reforge.com/programs). The
  working curriculum underneath Lecture 1's input-metric framing
  and Lecture 2's activation / retention / feature-adoption-depth
  instruments. The Reforge Retention Series specifically is the
  reference for retention-curve variants cited in Lecture 2.
- Chamath Palihapitiya, "Facebook's growth playbook," Growth
  Hackers TV, 2013 — see the working transcript at
  [growthhackers.com](https://growthhackers.com/videos/chamath-palihapitiya-former-facebook-growth-on-the-1st-metric-you-need-to-focus-on).
  The original *seven friends in ten days* account; cited for
  historical grounding of the activation-event discipline.

## Product analytics regime, activation, retention, cohorts

- Amplitude, "Retention analysis" product docs —
  [amplitude.com/docs/analytics/charts/retention-analysis/retention-analysis-overview](https://amplitude.com/docs/analytics/charts/retention-analysis/retention-analysis-overview).
  The canonical practitioner reference for the retention-chart
  variants (N-day, rolling, unbounded, range) named in
  [Lecture 2 — Instrument 3](lectures/02-analytics-regime-beyond-pmf.md#instrument-3--retention-curves-and-cohort-analysis).
- Mixpanel, "Retention and cohort analysis" learning hub —
  [mixpanel.com/learn/retention-cohort-analysis](https://mixpanel.com/learn/retention-cohort-analysis/).
  Mixpanel-flavored cross-reference to the same instruments;
  useful as a second source when authoring Exercise 2.
- Bessemer Venture Partners, "State of the Cloud" essays —
  [bvp.com/atlas](https://www.bvp.com/atlas). The reference for
  net-revenue-retention (NRR) benchmarks underpinning Lecture 2's
  Instrument 6 (revenue-per-account cohorts for B2B).
- Jason Lemkin & the SaaStr archive at
  [saastr.com](https://www.saastr.com/) — practitioner commentary
  on NRR, cohort expansion, and B2B retention cited in Lecture 2
  Instrument 6 and Exercise 2.
- PostHog documentation, "Correlation analysis" and "Funnel
  analysis" —
  [posthog.com/docs/product-analytics](https://posthog.com/docs/product-analytics).
  Open-source alternative to Amplitude / Mixpanel; the correlation-
  analysis feature is a working implementation of the Lecture 2
  activation-authoring protocol step 4.

## Analytics stack, tracking plans, and SQL (Segment, dbt, Mode, Hightouch)

- Segment, "Tracking Plan" documentation —
  [segment.com/docs/connections/spec/tracking-plan](https://segment.com/docs/connections/spec/tracking-plan/).
  The canonical reference for tracking-plan discipline — event
  naming, property schema, identify / group calls — underpinning
  [Lecture 3](lectures/03-analytics-stack-and-sql-against-events.md)
  and [Exercise 6](exercises/exercise-06-sql-against-events-tables-drill.md).
- Segment, "Analytics Academy — Data Collection Best Practices" —
  [segment.com/academy](https://segment.com/academy/). The longer-
  form training material behind Segment's docs; useful as a
  single-sitting read before authoring the Exercise 6 tracking-plan
  memo.
- Mode Analytics, "SQL Tutorial" — [mode.com/sql-tutorial](https://mode.com/sql-tutorial/).
  The reference for the five SQL patterns in Lecture 3; the
  "Intermediate SQL" section covers CTEs and window functions.
- Snowflake, "Window Functions" documentation —
  [docs.snowflake.com/en/sql-reference/functions-analytic](https://docs.snowflake.com/en/sql-reference/functions-analytic).
  Dialect-specific reference for window-function syntax the Lecture
  3 window-function example depends on.
- BigQuery, "Analytic function concepts" —
  [cloud.google.com/bigquery/docs/reference/standard-sql/analytic-function-concepts](https://cloud.google.com/bigquery/docs/reference/standard-sql/analytic-function-concepts).
  BigQuery-dialect analogue.
- PostgreSQL, "Window Functions" —
  [postgresql.org/docs/current/tutorial-window.html](https://www.postgresql.org/docs/current/tutorial-window.html).
  Postgres-dialect analogue; relevant for teams running analytics
  on a pre-seed Postgres warehouse.
- dbt Labs, documentation — [docs.getdbt.com](https://docs.getdbt.com/).
  The near-universal choice for the transform layer at pre-seed →
  Series-A; referenced in Lecture 3's stack diagram.
- Hightouch, documentation — [hightouch.com/docs](https://hightouch.com/docs);
  Census, documentation — [docs.getcensus.com](https://docs.getcensus.com/).
  The reverse-ETL layer the CPO authors audiences into; cited in
  Lecture 3's reverse-ETL section.
- RudderStack, documentation — [rudderstack.com/docs](https://www.rudderstack.com/docs/).
  Open-source alternative to Segment at the ingest layer.
- Julian Hyde's blog — [blog.hydromatic.net](https://blog.hydromatic.net/).
  Deep SQL craft from the Apache Calcite author; useful as a next
  read once the Lecture 3 five patterns are internalized.

## Experimentation (Kohavi, Miller, Johari, Stucchio)

- Ron Kohavi, Diane Tang & Ya Xu, *Trustworthy Online Controlled
  Experiments: A Practical Guide to A/B Testing*, Cambridge
  University Press, 2020 — [experimentguide.com](https://experimentguide.com/).
  The canonical practitioner reference for online A/B testing
  cited throughout
  [Lecture 4](lectures/04-experimentation-at-pre-seed-to-series-a.md),
  [Lecture 5](lectures/05-quasi-experimental-methods-when-ab-fails.md),
  and [Exercise 3](exercises/exercise-03-ab-test-mde-sizing-and-guard-metric-drill.md).
  Chapter 2 — hypothesis authoring; Chapter 3 — decision rules;
  Chapter 4 — long-horizon reads; Chapter 17 — sample-size formulas;
  Chapter 18 — ratio-metric variance via the delta method; Chapter
  21 — guardrails and SRM; Chapter 22 — Simpson's paradox.
- Ron Kohavi et al., "Online Controlled Experiments and A/B
  Testing," in *Encyclopedia of Machine Learning and Data Mining*,
  2016 — pre-print listing at [exp-platform.com](https://exp-platform.com/).
  Kohavi's working research-group index; link to many of the papers
  the book summarizes.
- Evan Miller, "Sample Size Calculator" —
  [evanmiller.org/ab-testing/sample-size.html](https://www.evanmiller.org/ab-testing/sample-size.html).
  The reference online MDE calculator cited in Lecture 4 and
  Exercise 3.
- Evan Miller, "How Not to Run an A/B Test," 2010 —
  [evanmiller.org/how-not-to-run-an-ab-test.html](https://www.evanmiller.org/how-not-to-run-an-ab-test.html).
  The canonical short read on peeking and the false-positive-rate
  inflation it causes.
- Ramesh Johari, Pete Koomen, Leonid Pekelis, David Walsh,
  "Peeking at A/B Tests: Why It Matters, and What to Do About It,"
  KDD 2017 / arXiv 1512.04922 —
  [arxiv.org/abs/1512.04922](https://arxiv.org/abs/1512.04922).
  The sequential-testing method underpinning Optimizely's Stats
  Engine; cited in Lecture 4 and Exercise 3.
- Chris Stucchio, "Easy Evaluation of Decision Rules in Bayesian
  A/B Testing" (the VWO SmartStats white paper), 2015 —
  [chrisstucchio.com/pubs/VWO_SmartStats_technical_whitepaper.pdf](https://www.chrisstucchio.com/pubs/VWO_SmartStats_technical_whitepaper.pdf).
  The practitioner reference for Bayesian A/B at low traffic
  cited in Lecture 4.
- statsmodels, "Power and Sample Size Calculations" docs —
  [statsmodels.org/stable/stats.html#power-and-sample-size-calculations](https://www.statsmodels.org/stable/stats.html#power-and-sample-size-calculations).
  The Python implementation of the same MDE math for continuous
  metrics and non-standard designs.

## Quasi-experimental methods (Angrist, Pischke, Card, Brodersen)

- Joshua Angrist & Jörn-Steffen Pischke, *Mostly Harmless
  Econometrics: An Empiricist's Companion*, Princeton University
  Press, 2009 — [mostlyharmlesseconometrics.com](https://www.mostlyharmlesseconometrics.com/).
  Chapter 5 is the canonical textbook reference for difference-in-
  differences used in
  [Lecture 5](lectures/05-quasi-experimental-methods-when-ab-fails.md).
- David Card & Alan Krueger, *Myth and Measurement: The New
  Economics of the Minimum Wage*, Princeton University Press, 1997
  — [press.princeton.edu/books/paperback/9780691048239/myth-and-measurement](https://press.princeton.edu/books/paperback/9780691048239/myth-and-measurement).
  The canonical worked example of DiD (the New Jersey minimum-wage
  study) cited in Lecture 5.
- Kay H. Brodersen, Fabian Gallusser, Jim Koehler, Nicolas Remy,
  Steven L. Scott, "Inferring causal impact using Bayesian
  structural time-series models," *Annals of Applied Statistics*,
  2015 — [research.google.com/pubs/pub41854](https://research.google.com/pubs/pub41854.html).
  The paper underlying Google's *CausalImpact* package for
  interrupted time-series.
- *CausalImpact* R package, Google — [google.github.io/CausalImpact](https://google.github.io/CausalImpact/).
  The Lecture 5-recommended implementation for ITS at founding-CPO
  scope.
- Nicholas Chamandy, "Experimentation in a Ridesharing Marketplace,"
  Lyft Engineering blog, 2016 —
  [eng.lyft.com/experimentation-in-a-ridesharing-marketplace-b39db027a66e](https://eng.lyft.com/experimentation-in-a-ridesharing-marketplace-b39db027a66e).
  The practitioner reference for switchback experiments and
  marketplace interference cited in Lecture 5.
- Uber Engineering, "How Uber experiments" and the experimentation
  platform posts at
  [uber.com/blog/experimentation-platform](https://www.uber.com/blog/experimentation-platform/).
  Marketplace / network-effect experimentation practitioner
  reference.

## AI engineering, evals, and LLM-as-judge (Huyen, Husain, Yan)

- Chip Huyen, *AI Engineering: Building Applications with
  Foundation Models*, O'Reilly, 2024 —
  [oreilly.com/library/view/ai-engineering/9781098166298](https://www.oreilly.com/library/view/ai-engineering/9781098166298/).
  Chapters 3 ("Evaluation Methodology") and 4 ("Evaluating AI
  Systems") are the reference used throughout
  [Lecture 6](lectures/06-eval-driven-decisions-for-llm-products.md)
  and [Exercise 4](exercises/exercise-04-llm-eval-suite-authoring-for-one-agent.md)
  for the four eval-regime decisions and the LLM-as-judge
  calibration protocol. Chapter 7 ("Model Serving and Inference
  Optimization") is the reference for
  [Lecture 7](lectures/07-cost-latency-quality-pareto.md) and
  [Exercise 5](exercises/exercise-05-cost-latency-quality-pareto-drill.md).
- Hamel Husain, "Your AI Product Needs Evals," May 2024 —
  [hamel.dev/blog/posts/evals](https://hamel.dev/blog/posts/evals/).
  The practitioner essay that most crisply makes the "eval regime
  replaces vibes" argument used in Lecture 6.
- Hamel Husain, "Creating a LLM-as-a-Judge That Drives Business
  Results," 2024 — [hamel.dev/blog/posts/llm-judge](https://hamel.dev/blog/posts/llm-judge/)
  (see also related posts in the hamel.dev archive). The
  practitioner reference for the LLM-as-judge calibration protocol
  cited in Lecture 6 and Exercise 4.
- Hamel Husain, "Field Notes on LLM Evaluation" and related essays
  at [hamel.dev](https://hamel.dev/). Running practitioner
  commentary on eval regime shape; useful as a continuous read.
- Eugene Yan, "Evaluation & Hallucination Detection for
  Abstractive Summaries," 2023 — [eugeneyan.com/writing/abstractive](https://eugeneyan.com/writing/abstractive/).
  Worked-example reference for LLM-as-judge rubric design cited
  in Lecture 6.
- Eugene Yan, blog archive at [eugeneyan.com](https://eugeneyan.com/).
  Practitioner essays on LLM evaluation, retrieval, and systems
  design — recommended as a next read after Huyen's book.
- Jacob Cohen, "A Coefficient of Agreement for Nominal Scales,"
  *Educational and Psychological Measurement*, 1960 —
  [journals.sagepub.com/doi/10.1177/001316446002000104](https://journals.sagepub.com/doi/10.1177/001316446002000104).
  The original Cohen's κ paper for inter-annotator agreement cited
  in Lecture 6's LLM-as-judge calibration section.

## Model providers — pricing, prompt caching, eval tooling

- Anthropic, "Prompt engineering" overview —
  [docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview).
- Anthropic, "Evaluate prompts" and "Develop tests" —
  [docs.anthropic.com/en/docs/test-and-evaluate/develop-tests](https://docs.anthropic.com/en/docs/test-and-evaluate/develop-tests).
  Reference template for the smallest useful eval harness; cited
  in Lecture 6 and Exercise 4.
- Anthropic, "Reduce hallucinations" guide —
  [docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/reduce-hallucinations](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/reduce-hallucinations).
- Anthropic, "Prompt caching" docs —
  [docs.anthropic.com/en/docs/build-with-claude/prompt-caching](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching).
  Reference for the Lecture 7 cost-cutting lever.
- Anthropic, pricing — [anthropic.com/pricing](https://www.anthropic.com/pricing).
- OpenAI, "OpenAI Evals" framework —
  [github.com/openai/evals](https://github.com/openai/evals). The
  reference for a config-driven, larger-scale eval harness cited
  in Lecture 6 and Exercise 4.
- OpenAI, "Prompt caching" docs —
  [platform.openai.com/docs/guides/prompt-caching](https://platform.openai.com/docs/guides/prompt-caching).
- OpenAI, "Introducing the Model Spec" and related evaluation blog
  posts at [openai.com](https://openai.com/) — see
  [openai.com/index/introducing-the-model-spec](https://openai.com/index/introducing-the-model-spec/).
- OpenAI, pricing — [openai.com/api/pricing](https://openai.com/api/pricing/).
- Google, Gemini API pricing — [ai.google.dev/pricing](https://ai.google.dev/pricing).

## Eval dataset hosting and observability tooling

- Braintrust — [braintrust.dev](https://www.braintrust.dev/). Eval
  dataset hosting and harness; cited in Lecture 6.
- Langfuse — [langfuse.com](https://langfuse.com/). Open-source
  LLM observability + eval dataset host.
- LangSmith — [smith.langchain.com](https://smith.langchain.com/)
  (docs at [docs.smith.langchain.com](https://docs.smith.langchain.com/)).
- Arize Phoenix — [phoenix.arize.com](https://phoenix.arize.com/)
  and [github.com/Arize-ai/phoenix](https://github.com/Arize-ai/phoenix).
  Open-source LLM eval + tracing.
- Humanloop — [humanloop.com](https://humanloop.com/).
- Nielsen Norman Group, Jakob Nielsen, "Response Times: The 3
  Important Limits," 1993 (updated) —
  [nngroup.com/articles/response-times-3-important-limits](https://www.nngroup.com/articles/response-times-3-important-limits/).
  The reference for perceived-latency thresholds used in Lecture 7.

## Boundaries this module keeps — deeper reads

The following curricula hold the depth that mod-005 explicitly
*consumes* rather than authors. The CPO reads enough of these to
know what to ask for; the specialists cited author the regime.

- **[cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)**
  (level 25) — The data-platform architecture underneath Lecture
  3: warehouse selection, ELT vs. ETL, dbt modeling at depth,
  reverse-ETL vendor selection, schema evolution, RBAC. The CPO
  consumes the stack and queries it; the CTO / data lead authors
  the platform. Cited explicitly in Lecture 3's "What the CPO
  consumes" section.
- **[ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning)**
  (level 30) — App-side eval methodology at depth: eval harness
  implementation, prompt-versioning tooling, trajectory replay,
  multi-turn agentic-test-suite architecture. Lecture 6 teaches
  the CPO-scope decisions (what to eval for, how to grade, what
  threshold); the AI-eval engineer authors the harness. Cited
  explicitly in Lecture 6's boundaries section.
- **[model-evaluation-engineer-learning](https://github.com/ai-engineering-curriculum/model-evaluation-engineer-learning)**
  (level 30) — Statistical calibration depth for grader models:
  inter-annotator agreement, Cohen's κ, judge-model bias
  measurement, human-review sampling design. Lecture 6 teaches the
  CPO-scope calibration discipline (spot-check ~10% of judge
  outputs; track judge/human agreement); the model-evaluation
  engineer authors the statistical rigor. Cited explicitly in
  Lecture 6's boundaries section.
- **[rag-engineer-learning](https://github.com/ai-engineering-curriculum/rag-engineer-learning)**
  — Deep retrieval craft underneath Lecture 7's configurations;
  index design, chunking strategy, reranker evaluation. Lecture 7
  treats retrieval as a tunable config dimension; the RAG engineer
  authors the retrieval system.
- **[agentic-ai-engineer-learning](https://github.com/ai-engineering-curriculum/agentic-ai-engineer-learning)**
  — Agent framework depth underneath Lecture 7's agentic
  configurations: planning strategies, tool-use systems,
  trajectory-level evals. Lecture 7 treats agent-call-count as a
  cost / latency axis; the agentic-AI engineer owns the
  framework.

Peer / adjacent CPO-curriculum modules the metrics work connects
back to:

- **[mod-001](mod-001-customer-discovery-to-pmf/README.md)** — PMF
  measurement (Sean Ellis 40% survey, qualitative pull signal,
  retention as a fit signal). The north-star / input-metric regime
  in this module is the *post-PMF* measurement regime; mod-001
  owns the fit-signal itself.
- **[mod-002](mod-002-opportunity-assessment-and-prioritization/README.md)**
  — The opportunity queue the experiments and evals run against.
- **[mod-003](mod-003-roadmap-outcomes-and-strategy/README.md)** —
  The outcomes-based roadmap and OKR authoring that cite the
  metric taxonomy mod-005 defends. The taxonomy is defined here;
  the roadmap turns it into outcomes.
- **[mod-004](mod-004-discovery-delivery-cadence/README.md)** —
  The weekly cadence experiments and eval sweeps run inside.
  Lecture 5 of mod-004 introduces evals as a product-decision
  cadence; mod-005 owns the eval regime itself.
- **[mod-006](mod-006-pricing-packaging-and-monetization/README.md)**
  — Pricing-page experiments, willingness-to-pay research, credit /
  metering as monetization surfaces. The experimentation discipline
  in Lecture 4 applies; the pricing craft itself is mod-006.
- **[mod-007](mod-007-working-with-founders-eng-and-gtm/README.md)**
  — The founder-CEO / eng / GTM relationships underneath a
  low-power A/B disagreement or a contested north-star defense.

See [CURRICULUM.md](../../CURRICULUM.md#ownership-rule) for the full
ownership rule and the deferrals table.

## Adjacent reading (light touch)

The following are not cited in the module body but are one-step
neighbors that show up in most founding-CPO reading lists on
metrics, experimentation, and eval craft:

- Lenny Rachitsky, *Lenny's Newsletter* —
  [lennysnewsletter.com](https://www.lennysnewsletter.com/).
  Practitioner surveys on metric taxonomies, experimentation
  cadence, and north-star examples; useful as a sanity-check after
  Ellis and Chen.
- Shaun Clowes & various, writing at
  [reforge.com/blog](https://www.reforge.com/blog). The Reforge
  practitioner archive adjacent to the Growth-program essays
  cited above.
- Casey Winters, personal essays at
  [caseyaccidental.com](https://caseyaccidental.com/). Growth-PM
  practitioner commentary adjacent to Lecture 1's input-metric
  framing and Lecture 2's retention discipline.
- Elena Verna, newsletter and essays at
  [elenaverna.com](https://www.elenaverna.com/). Growth-PM
  practitioner commentary with a bias toward B2B self-serve and
  product-led-growth metric shapes.
- Statsig blog —
  [statsig.com/blog](https://www.statsig.com/blog); Eppo blog —
  [geteppo.com/blog](https://www.geteppo.com/blog). Vendor
  engineering blogs on practical experimentation at seed to
  Series-C scale; useful for the engineering-side detail Lecture 4
  omits.
- Simon Willison, personal essays at
  [simonwillison.net](https://simonwillison.net/). Practitioner
  essays on LLM evaluation, prompt engineering, and tool-use;
  useful as a continuous read on the AI-substrate side.
- Jason Liu, personal essays at [jxnl.co](https://jxnl.co/).
  Running practitioner writing on evals, structured outputs, and
  the data-flywheel discipline underneath Lecture 6.
- Hamel Husain / Shreya Shankar, "AI Evals for Engineers &
  PMs" course — [maven.com/parlance-labs/evals](https://maven.com/parlance-labs/evals).
  The practitioner-course form of Husain's eval essays; cited as a
  deeper training path once Lecture 6 and Exercise 4 are complete.
- Susan Athey & Guido Imbens, "The State of Applied Econometrics —
  Causality and Policy Evaluation," *Journal of Economic
  Perspectives*, 2017 — [aeaweb.org/articles?id=10.1257/jep.31.2.3](https://www.aeaweb.org/articles?id=10.1257/jep.31.2.3).
  Modern causal-inference survey; useful as a deeper read after
  Angrist & Pischke.
- Judea Pearl, *The Book of Why*, Basic Books, 2018 —
  [bookofwhy.com](http://bookofwhy.com/). Popular-level
  introduction to causal inference; a reasonable layperson's
  on-ramp before Angrist & Pischke.
- Christie Aschwanden, "Science Isn't Broken," FiveThirtyEight —
  [fivethirtyeight.com/features/science-isnt-broken](https://fivethirtyeight.com/features/science-isnt-broken/).
  The classic working explanation of p-hacking; useful as a short
  read on the Lecture 4 failure modes before Miller.

If a claim in the module cites a source not listed here, treat it
as a `needs-research` gap and open an issue.
