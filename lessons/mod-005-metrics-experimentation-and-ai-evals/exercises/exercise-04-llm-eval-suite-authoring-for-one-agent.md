# Exercise 4 — LLM eval suite authoring for one agent

**Time:** ~4 hours. **Deliverable:** one **eval-suite
authoring package** for a single AI-substrate slice —
task definition, labeled eval set of **50–200 examples**,
rubric for each grading dimension, judge configuration
with a **calibration plan against human review**, and a
pre-registered **launch threshold** — plus a half-page
reviewer's memo on the eval set's drift risk.

## Purpose

Author the eval regime
[Lecture 6](../lectures/06-eval-driven-decisions-for-llm-products.md)
teaches: the four CPO-scope decisions (**what are we
evaluating for**, **how is grading done**, **what is the
eval set**, **what is the threshold**) made explicit for
one specific LLM-substrate feature, with a calibration
protocol against human review that the suite can actually
be defended by. This is the eval-driven analogue of the
A/B brief authored in
[Exercise 3](exercise-03-ab-test-mde-sizing-and-guard-metric-drill.md) —
it replaces the A/B for most stochastic-output LLM
decisions
([Lecture 6 — When the eval-suite threshold replaces A/B](../lectures/06-eval-driven-decisions-for-llm-products.md#when-the-eval-suite-threshold-replaces-ab-as-the-launch-gate)).

The eval set authored here becomes the quality axis of the
Pareto in
[Exercise 5](exercise-05-cost-latency-quality-pareto-drill.md).
Author both to the same slice.

## What you need before you start

- **One AI-substrate feature or agent** you can describe
  in two sentences — a customer-support triage agent, a
  retrieval-augmented QA system, a code-generation
  assistant, an email-drafting feature, a document-
  summarization slice. Pick one that is *scoped* enough
  for a 50–200-example eval set to be representative.
- **Access to a dataset-hosting target** per
  [Lecture 6 — Dataset hosting](../lectures/06-eval-driven-decisions-for-llm-products.md#dataset-hosting--where-labeled-data-lives):
  Braintrust, Langfuse, LangSmith, Phoenix, Humanloop,
  or (for the first 50 examples) a JSONL / Parquet repo,
  or (for the first 10) a Google Sheet / Airtable. Pick
  one and author in it — the authoring tool is part of
  the deliverable.
- **An LLM judge model.** Use a *different* model
  family from the one being graded, per
  [Lecture 6 — LLM-as-judge failure modes](../lectures/06-eval-driven-decisions-for-llm-products.md#llm-as-judge-with-calibration)
  (self-preference bias). Anthropic Claude judging GPT
  outputs, or vice versa, is the shape.
- **Access to a human reviewer.** At minimum: you,
  working through 10–20 outputs yourself as the human
  gold. Ideally: a second reviewer so you can measure
  inter-annotator agreement.
- Anthropic's "Evaluate prompts" docs and OpenAI's Evals
  framework as reference templates for the harness
  shape
  ([docs.anthropic.com/en/docs/test-and-evaluate/develop-tests](https://docs.anthropic.com/en/docs/test-and-evaluate/develop-tests);
  [github.com/openai/evals](https://github.com/openai/evals)).

## Scoping the slice

The eval suite is only coherent against a scoped slice.
Pick one of the following shapes:

- **A single agent task.** "The support-triage agent
  routes an inbound ticket to one of 12 categories and
  drafts a first-reply."
- **A single prompt / tool-use chain.** "The RAG
  pipeline retrieves top-5 passages and generates an
  answer with citations."
- **A single UX surface powered by one or more model
  calls.** "The 'summarize this document' button in
  the editor."

If your scope requires an *interactive multi-turn*
evaluation (long-horizon agentic trajectories across
dozens of tool calls), narrow it to one representative
sub-task for this exercise; multi-turn trajectory
evaluation at depth is
[ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning)'s
scope.

## What the eval-suite package must contain

### 1. Task definition (half page)

- **The task** stated as input / expected-behavior /
  output-shape, concretely. "Given an inbound support
  email, route to one of {billing, bug, feature-request,
  how-to, abuse, other}, and draft a 2–4 sentence first-
  reply in the product's voice."
- **The user hiring the feature.** Who runs it, in what
  flow, with what alternative if the feature breaks.
- **The scoped set of inputs** the feature must handle.
  State what's in scope (English-language free-form
  tickets ≤ 500 words) and what's explicitly out of
  scope (attachments, HTML tables, non-English
  content).

### 2. Decision 1 — Grading dimensions (one page)

For *this* slice, pick the grading dimensions from
[Lecture 6 — Decision 1](../lectures/06-eval-driven-decisions-for-llm-products.md#decision-1--what-are-we-evaluating-for)
that actually matter. Not all of them — the dimensions
that map to this product surface's real failure modes.
State for each:

- **Dimension name** (correctness, task success, format
  adherence, tone, safety / refusal, hallucination
  rate, tool-selection accuracy, etc.).
- **Why it matters for this slice**, in one sentence.
- **Grading approach** (rule-based / LLM-as-judge /
  human) — Decision 2 below is where you justify this.
- **Pass / fail / scored**: binary pass-fail, 1–5
  Likert, or continuous score.

**Required for every suite:**
- At least one **safety / refusal** dimension — even
  for non-adversarial products, prompt injection and
  out-of-scope requests happen.
- At least one **format-adherence** dimension — JSON
  shape, field presence, citation format. Format
  errors are where most production regressions first
  show up.

### 3. Decision 2 — Grading approach, per dimension (half page)

Per Lecture 6, use the right tool for each dimension:

- **Rule-based** for anything narrow enough — JSON
  parsing, field presence, regex match, arithmetic
  check, category match against a fixed list. Fast,
  cheap, deterministic.
- **LLM-as-judge** for open-ended dimensions — tone,
  correctness-under-ambiguity, hallucination
  detection. State the judge model (different family
  from the graded model).
- **Human labeling** for the *calibration* set and
  for anything the judge can't be trusted on.

The deliverable: a table of *dimension × grading
approach × rationale*. Not a mix on autopilot — a
justified pick per dimension.

### 4. Decision 3 — Eval set authoring (one to two pages)

The eval set is the *product artifact*. Author it:

- **50–200 labeled examples**, per the Lecture 6
  working range. 50 is the minimum for a useful read;
  100–200 is the target for a production-grade suite.
- **Happy-path core (60–80%).** The most-common input
  shapes.
- **Long-tail region (20–40%).** Rare-but-important
  shapes — safety / adversarial cases, high-value user
  flows, edge cases from support tickets.
- **Sources, per Lecture 6:**
  1. Real production traffic (if you have it) —
     sampled from logs, anonymized where needed.
  2. Mod-001 / mod-004 customer-interview inputs —
     real user tasks in real user language.
  3. Curated edge cases — safety / adversarial /
     known-failure categories.
- **Each example has**:
  - Input (the user prompt / document / query).
  - Expected behavior (ground truth where possible;
    rubric reference for open-ended cases).
  - Dimension-level labels where fixed (e.g.,
    expected category for routing; expected
    presence/absence of citation).
  - Source tag (production / interview / curated).
  - Category tag (happy-path / long-tail /
    safety-adversarial).

**Storage choice.** Name where the eval set lives per
Lecture 6's three options. For teams with no existing
tool, a JSONL file in the product repo is the right
starting shape; migrate when the set passes ~100
examples.

### 5. Decision 4 — Launch threshold (half page)

Pre-register the launch threshold, in one of the three
Lecture 6 shapes
([Lecture 6 — Decision 4](../lectures/06-eval-driven-decisions-for-llm-products.md#decision-4--what-is-the-threshold)):

- **Absolute threshold** (e.g., "≥ 80% on happy-path,
  ≥ 60% on long-tail") — simplest, often wrong,
  usable for the first launch.
- **Relative threshold** (e.g., "no worse than
  production on any category, aggregate ≥ 5 pp better") —
  the Lecture 6 recommended default for most teams.
- **No-regression + relative-improvement** — the
  shape Lecture 6 recommends for production AI
  surfaces: safety-set regression is a blocker;
  previously-known-good regression set stays 100%
  passing; aggregate improves ≥ N pp.

**State the threshold once, as a pre-registered rule**,
in the same shape as the Exercise 3 experiment
decision rule. The threshold is the launch gate; it
replaces the A/B decision rule for stochastic outputs.

### 6. LLM-as-judge configuration and calibration plan (one page)

Walk the Lecture 6 calibration protocol
([Lecture 6 — LLM-as-judge, with calibration](../lectures/06-eval-driven-decisions-for-llm-products.md#llm-as-judge-with-calibration)).

- **Rubric per dimension.** A paragraph specifying what
  "good" looks like, with concrete examples of each
  score level. Rubric ambiguity is Lecture 6's most
  common judge failure; test inter-run consistency
  (run the judge twice on the same input; score
  should be identical or near-identical).
- **Judge model and family.** Different from the graded
  model's family; stated and justified.
- **Debiasing against known failure modes:**
  - **Position bias** — randomize order on pairwise
    comparisons.
  - **Verbosity bias** — add explicit brevity
    guidance in the rubric; normalize scores by
    length if needed.
  - **Self-preference bias** — judge is a different
    family from generator.
- **Calibration protocol:**
  - Sample **~10% of judge grades per week**,
    spread across score distribution and failure
    categories.
  - Human review (minimum: you; preferred: a second
    reviewer).
  - Compute **agreement rate** — for pass/fail,
    agreement %; for scored rubrics, Cohen's κ or
    Spearman correlation.
    ([Cohen 1960 on κ](https://journals.sagepub.com/doi/10.1177/001316446002000104);
    deeper statistical treatment at
    [model-evaluation-engineer-learning](https://github.com/ai-engineering-curriculum/model-evaluation-engineer-learning).)
  - **Acceptance threshold:** ≥ 80% agreement, or
    Cohen's κ ≥ 0.6 for pass/fail / ≥ 0.7 for
    multi-score. State what you'd do if calibration
    fails (revise rubric; switch to human labeling
    temporarily).
  - **Tracking cadence:** how often you'll re-check
    calibration (Lecture 6 default: weekly or
    monthly, depending on volume).

### 7. One trial run (one page)

Actually run the suite on **one** candidate
configuration. Not multiple — one. (Multiple
configurations is Exercise 5.) Report:

- **Per-dimension score distribution.**
- **Aggregate scores**: happy-path pass rate, long-
  tail pass rate, safety pass rate.
- **Pass / fail against the pre-registered launch
  threshold** — would this configuration ship?
- **Five representative failures.** Named examples,
  what the model did, what the rubric said. The
  failures are where the eval set's calibration gets
  tested.
- **Judge-vs-human spot check** on 5–10 of those
  grades — did the judge match human review?

The trial run is where the authoring exposes its own
flaws. Expect to revise the rubric, the eval set, or
the threshold at least once based on this run.

### 8. The reviewer's memo — drift risk (half page)

Walk the Lecture 6 dataset-drift concern
([Lecture 6 — Dataset drift and eval-set aging](../lectures/06-eval-driven-decisions-for-llm-products.md#dataset-drift-and-eval-set-aging)):

- **What inputs will emerge in production in the next
  6 months** that your current eval set doesn't
  capture? Name them.
- **Quarterly refresh plan:** how you'll sample fresh
  production inputs, label them, add them to the
  set, and recalibrate the judge.
- **Retirement rule:** when (if ever) you'd retire
  older examples.

## Starter guidance

- **Scope before setting size.** 50 examples that
  cover the slice beat 500 that cover something
  adjacent. Resist the urge to build a sprawling eval
  set before you have a tight task definition.
- **Author the rubric before writing the judge
  prompt.** The rubric is a product artifact —
  concrete examples per score level, not abstractions.
  Then the judge prompt becomes a transcription of
  the rubric.
- **Human-label 10 examples yourself before building
  anything.** This is the single highest-leverage
  activity in the exercise. You'll surface rubric
  ambiguities and task-definition gaps that no amount
  of judge-model work would surface.
- **Different-family judge, always.** The
  self-preference failure mode is real and well-
  documented; the fix is cheap.
- **Hallucinated-citation checks are the hidden
  layer.** For any retrieval / RAG surface, build a
  rule-based grader that verifies each cited chunk
  exists and matches the response. This single rule
  catches a disproportionate share of production
  failures.
- **Threshold on the long-tail set, not just the
  happy path.** A suite that passes 95% on the happy
  path and 30% on the long tail will demo great and
  fail in production. Lecture 6 is emphatic.
- **The eval set is a product artifact, not a
  one-off.** Version it, review PRs against it, grow
  it monthly. If the eval set lives in one
  engineer's notebook, the suite does not compound.

## Acceptance criteria

- **Task definition** names input / expected-behavior
  / output-shape, user, and in-scope / out-of-scope
  input ranges.
- **Grading dimensions** are picked from Lecture 6's
  list by what matters for *this* slice, with safety
  and format-adherence always included.
- **Grading approach per dimension** is named and
  justified (rule / judge / human); the mix is not
  on autopilot.
- **Eval set** is 50–200 labeled examples with
  happy-path / long-tail / safety split in the
  Lecture 6 ratios, sourced from production /
  interviews / curated cases, with per-example source
  and category tags.
- **Storage** is one of the three Lecture 6 options,
  named explicitly.
- **Launch threshold** is pre-registered as a single
  rule in the no-regression + relative-improvement
  shape (or absolute / relative, with justification).
- **Judge configuration** names model (different
  family), rubric with concrete per-score examples,
  and debiasing moves for position / verbosity /
  self-preference.
- **Calibration plan** names the sampling rate
  (~10%), human-review protocol, agreement metric
  (Cohen's κ or Spearman), and acceptance threshold
  (≥ 80% / κ ≥ 0.6 / κ ≥ 0.7); the tracking cadence
  is stated.
- **Trial run** reports per-dimension and aggregate
  scores, pass/fail against threshold, five
  representative failures, and a judge-vs-human
  spot-check on 5–10 grades.
- **Reviewer's memo** names 6-month drift risks and
  a quarterly refresh plan.

## Common failure modes

- **"Quality score."** A single rolled-up number
  across all dimensions, with no visibility into
  which dimension moved. The Lecture 6 move is
  per-dimension scoring; the aggregate is for
  reporting, the per-dimension is for diagnosis.
- **Judge-and-generator from the same family.**
  Self-preference bias means your eval score becomes
  model-family-dependent noise. Different family,
  always.
- **No calibration against human review.** The
  judge's agreement with human reviewers is where
  the metric's truth lives. Without it, the eval
  score is a wish.
- **Happy-path-only eval set.** 100% happy-path
  examples; the long-tail region doesn't exist. The
  model will fail in production on the queries you
  did not practice against.
- **Absolute threshold trap.** "≥ 80%" bar blocks a
  config that would have been strictly better than
  production and admits a config that is worse. The
  Lecture 6 no-regression + relative-improvement
  shape is the default for a reason.
- **Rubric ambiguity.** The judge's inter-run
  variance is high because the rubric leaves room
  for interpretation. Add concrete per-score
  examples.
- **Static eval set.** The set authored in month 1
  is still the set in month 6; drift has silently
  invalidated the launch threshold. The quarterly
  refresh is the counter-move.
- **Eval set in a notebook.** No canonical home;
  the set does not compound. Pick a storage option
  from Lecture 6 and commit.

## Source alignment

The four CPO-scope decisions, LLM-as-judge calibration
protocol, dataset drift / refresh discipline, and
"eval replaces A/B for stochastic outputs" framing
derive from Chip Huyen, *AI Engineering: Building
Applications with Foundation Models*, O'Reilly, 2024,
Chapters 3 ("Evaluation Methodology") and 4
("Evaluating AI Systems") —
[oreilly.com/library/view/ai-engineering/9781098166298](https://www.oreilly.com/library/view/ai-engineering/9781098166298/).
The practitioner discipline on LLM-as-judge comes from
Hamel Husain, "Your AI Product Needs Evals," May
2024 —
[hamel.dev/blog/posts/evals](https://hamel.dev/blog/posts/evals/) —
and "Creating a LLM-as-a-Judge That Drives Business
Results," 2024 —
[hamel.dev/blog/posts/llm-judge](https://hamel.dev/blog/posts/llm-judge/).
Eugene Yan's "Evaluation & Hallucination Detection for
Abstractive Summaries," 2023 —
[eugeneyan.com/writing/abstractive](https://eugeneyan.com/writing/abstractive/) —
is the worked-example reference. The harness-shape
references are Anthropic's "Evaluate prompts" docs —
[docs.anthropic.com/en/docs/test-and-evaluate/develop-tests](https://docs.anthropic.com/en/docs/test-and-evaluate/develop-tests)
— and OpenAI Evals —
[github.com/openai/evals](https://github.com/openai/evals).
Cohen's κ as the inter-annotator agreement statistic
derives from Jacob Cohen, "A Coefficient of Agreement
for Nominal Scales," *Educational and Psychological
Measurement*, 1960 —
[journals.sagepub.com/doi/10.1177/001316446002000104](https://journals.sagepub.com/doi/10.1177/001316446002000104).
