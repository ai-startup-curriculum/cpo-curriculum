# Lecture 6 — Eval-driven product decisions for LLM-native products

## The setup

Lectures 4 and 5 gave you the discipline for moving
deterministic metrics — click-through, conversion,
retention — with A/B tests and quasi-experimental
designs. This lecture is where those tools stop
working.

LLM-substrate products produce **stochastic outputs**.
The same input produces different outputs across
identical requests (temperature, sampling), across
provider snapshots (model updates, silent retraining),
and — for retrieval-augmented systems — across
document-corpus edits. A/B testing a prompt change is
possible but often not sensible: the *quality* of the
output cannot be summarized as a click, and the
*variance* of individual outputs swamps the
distinguishing signal.

The CPO-scope response, converging across the working
literature (Hamel Husain's *Your AI Product Needs
Evals* and follow-ups; Chip Huyen's *AI Engineering*
book Chapters 3–4; the practitioner writing of Eugene
Yan, Simon Willison, and the Anthropic and OpenAI
docs) is to replace A/B, for most LLM feature
decisions, with an **eval regime**: a labeled dataset
of realistic inputs, a grading approach, a threshold,
and a review discipline that makes eval outputs
comparable across prompt / retrieval / tool-call
configurations.

The founding-CPO version of this regime is what this
lecture teaches — not the eval-engineer's implementation
depth (that's
[ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning)),
but the CPO's authoring surface: *what to eval for*,
*what the dataset covers*, *how grading is done*, *how
to calibrate an LLM-as-judge against human review*,
*where the labeled data lives*, and *when the eval-suite
threshold replaces an experiment as the launch gate*.

Mod-004's Lecture 5 introduced evals as a
product-decision surface *inside the weekly cadence*.
This lecture owns the eval regime itself.

## Why A/B fails for LLM features (and what replaces it)

Three specific failure modes make A/B misfit for most
LLM product decisions:

- **Output-quality variance dwarfs the treatment
  effect.** Model output quality varies more between
  two runs of the same prompt than between a
  well-designed prompt A and a slightly-better prompt
  B. Detecting the difference requires either huge
  samples or a metric that averages away the noise
  (which usually erases the difference too).
- **The metric of interest is the *quality* of the
  output**, not a downstream user action. Users often
  can't tell a subtly-worse output from a subtly-
  better one in a single interaction. Waiting for the
  downstream retention signal takes weeks.
- **The model provider changes underneath you.**
  Silent snapshot updates, temperature-behavior
  shifts, tokenizer changes. An A/B run over four
  weeks is not comparing prompt A to prompt B; it is
  comparing prompt-A-on-model-snapshot-Nov-1 to
  prompt-B-on-model-snapshot-Nov-15.

The response: **the eval suite is the experiment**.
Instead of A/B-ing prompt versions in production, you
run both prompts (or all N candidate prompts) against
a *fixed labeled dataset* and compare their scores.
The eval suite is the *hypothesis*, the *primary
metric*, and the *decision rule*, all in one artifact.

Hamel Husain, in *Your AI Product Needs Evals* and the
follow-up field notes, is the practitioner most
associated with this framing:

> *"The single most impactful thing you can do to
> improve your AI product is to establish a strong
> evaluation system. It is not glamorous, and most
> teams underinvest in it. But without it, you are
> shipping regressions in the dark."*
>
> — paraphrased across [hamel.dev/blog/posts/evals](https://hamel.dev/blog/posts/evals/)
> and follow-ups.

Chip Huyen, in *AI Engineering* Chapters 3 and 4,
extends the framing with a taxonomy of grading
approaches and the calibration discipline that makes
LLM-as-judge trustworthy
([Huyen, *AI Engineering: Building Applications with
Foundation Models*, O'Reilly, 2024, Chapters 3–4](https://www.oreilly.com/library/view/ai-engineering/9781098166298/)).

## The four eval-regime decisions

The CPO owns four decisions on any eval suite; the
eng team implements the harness underneath.

### Decision 1 — What are we evaluating for?

The dimensions the CPO chooses among:

- **Correctness.** Did the model produce the right
  answer? Well-defined for factual queries (arithmetic,
  extraction, factual QA); noisier for open-ended
  generation. Reference-based grading works when a
  ground-truth answer exists.
- **Task success.** For agents / tool-using systems:
  did the trajectory complete the task? Booked the
  flight, closed the ticket, sent the email.
- **Format adherence.** Did the output match the
  required structure — JSON schema, particular fields,
  citation format? Easy to grade with rules; often
  where errors first show up.
- **Tone / style / voice.** For customer-facing
  outputs: did the response match the product's
  voice? Hard to grade with rules; a natural
  LLM-as-judge use case.
- **Safety / refusal behavior.** Did the model refuse
  when it should have (harmful content, prompt
  injection, out-of-scope requests) and comply when
  it should have? Often a specific eval set of
  adversarial examples.
- **Hallucination rate.** For retrieval-augmented
  systems: did the model cite sources, and were the
  citations accurate? Grading via citation-check
  rules plus spot-checks.
- **Tool-selection accuracy.** For agent systems: did
  the model call the right tool for the request,
  with the right arguments?
- **Cost per output** and **p95 latency.** Not
  quality dimensions, but eval-set-measurable and
  worth tracking alongside the quality metrics —
  see [Lecture 7](07-cost-latency-quality-pareto.md).

The rule: **pick the failure modes that matter for
this product surface and eval those.** A customer-
support-triage agent's evals are different from a
code-generation product's evals. Don't build a
generic "quality" score; build a specific set of
graders that map to the actual failure modes.

### Decision 2 — How is grading done?

Three grading approaches, each with a specific fit:

- **Rule-based grading.** For narrow, well-defined
  outputs — JSON parsability, expected fields
  present, regex match on an ID, arithmetic
  correctness. Fast, cheap, deterministic. Fails on
  open-ended outputs.
- **Human labeling.** A domain expert reads the
  output and grades it. Gold-standard for correctness
  and tone; slow, expensive, and doesn't scale to
  the frequency of iteration a working AI-substrate
  team needs. Use for calibration and for the "gold
  set" that other graders are checked against.
- **LLM-as-judge.** A stronger model grades the
  target model's output against a rubric. Fast,
  cheap, scales — and dangerous if not calibrated
  against human review. The right default for most
  open-ended eval dimensions once calibration is in
  place.

The practical answer for most teams is a **mix**:
rule-based grading for anything narrow enough,
LLM-as-judge for the open-ended dimensions, human
labeling for the calibration set. Eugene Yan and
Hamel Husain both make this point extensively; see
Yan's essay on abstractive summarization evals as a
worked example
([Yan, "Evaluation & Hallucination Detection for
Abstractive Summaries," 2023](https://eugeneyan.com/writing/abstractive/)).

### Decision 3 — What is the eval set?

The eval set is a labeled collection of *realistic
inputs* — not curated adversarial examples, not
model-provider benchmark tasks, but the actual
inputs users produce. Three sources:

- **Real production traffic.** Sampled from logs,
  anonymized as needed, with labels attached
  post-hoc. The most representative source; requires
  a working observability pipeline (Langfuse,
  Braintrust, Phoenix, LangSmith, or bespoke).
- **Customer-conversation inputs.** From mod-001
  interviews and mod-004's weekly interview cadence.
  Real user tasks phrased in real user language.
- **Curated long-tail examples.** Rare-but-important
  inputs the team knows the product must handle
  well — safety cases, high-value user flows, edge
  cases from customer support tickets.

The set has a **happy-path core** (60–80% of the
examples, representing the most-common queries) and
a **long-tail region** (20–40% covering edge cases,
adversarial examples, and known-failure categories).
Both matter. A model that scores 95% on the happy
path and 30% on the long tail will look great in a
demo and fail in production; a model that scores 85%
on both will feel more consistent to users.

**Set size rules of thumb** (Huyen Chapter 4, Husain
field notes):

- **50 examples** is the minimum for a useful eval,
  and enough for a first-pass launch decision on a
  narrow feature.
- **100–200 examples** is the working target for a
  production eval suite.
- **500+** starts to matter for A/B-style comparisons
  between prompt versions, and for detecting small
  quality regressions.
- **1000+** is the territory of a robust production
  regime — usually built up incrementally, one
  labeled example at a time, over months.

The eval set is a *product artifact*, versioned, owned
by the CPO. It grows as the team learns; it does not
get "finished."

### Decision 4 — What is the threshold?

The launch threshold is the CPO's ship / no-ship rule
against the eval suite. Three shapes:

- **Absolute threshold.** *"The model correctly
  handles ≥ 80% of the happy-path eval set, and ≥
  60% of the long-tail eval set, before launch."*
- **Relative threshold.** *"The new configuration
  scores no worse than the current production
  configuration on any category, and improves the
  aggregate by ≥ 5 percentage points."*
- **No-regression threshold.** *"The new configuration
  scores no worse than production on the safety
  eval set (any regression is a blocker); the
  aggregate quality score may vary but the
  regression set (previously-known-good examples)
  must remain 100% passing."*

The right threshold for a founding CPO is usually the
**no-regression + relative-improvement** shape:
regression on the safety / refusal set is a blocker,
and the change must improve the aggregate quality
score on the happy path. Absolute thresholds are
tempting but often wrong — a "≥ 80%" bar can trap the
team into shipping worse configurations that clear
80% while blocking better ones that don't.

## LLM-as-judge, with calibration

LLM-as-judge is where most founding-CPO eval regimes
live in practice, because the alternatives (human
labeling for every eval run, rule-based grading for
open-ended outputs) don't scale. The pattern:

1. Write a *rubric* — a prompt for the judge model
   that specifies what "good" looks like on the
   dimension being evaluated.
2. For each input in the eval set, generate the
   target model's output *and* the judge model's
   score against the rubric.
3. Aggregate: mean / median score, pass rate, error
   distribution.

The critical discipline, and where most teams cut
corners, is **calibration**: are the judge's scores
actually tracking human judgment? A judge model that
scores everything a 4/5 or that penalizes verbose
outputs the humans preferred is a broken metric.

**The calibration protocol** (paraphrased from Huyen
Chapter 4 and Husain's *"Creating a LLM-as-a-Judge That
Drives Business Results"*):

1. Sample **~10% of judge grades per week**, spread
   across the score distribution and the failure
   categories.
2. Have a **human reviewer** (ideally two, working
   independently) grade the same outputs on the same
   rubric.
3. Compute the **agreement rate** between judge and
   human. For a pass/fail rubric, agreement %. For a
   scored rubric, Cohen's κ or Spearman correlation
   ([Cohen, "A Coefficient of Agreement for Nominal
   Scales," 1960](https://journals.sagepub.com/doi/10.1177/001316446002000104);
   see the reference at
   [ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning)
   for the depth-of-statistical-treatment beyond
   this lecture's scope).
4. **Threshold for acceptable calibration:** ≥ 80%
   agreement (or Cohen's κ ≥ 0.6 for pass/fail; ≥
   0.7 for multi-score). Below that, the judge
   rubric needs revision; use human labeling in the
   meantime.
5. **Track calibration over time.** Model provider
   updates, rubric drift, and new example categories
   all degrade calibration. If agreement drops below
   the threshold, halt LLM-as-judge use and re-
   calibrate.

**Common LLM-as-judge failure modes and their fixes:**

- **Position bias.** When comparing two outputs, the
  judge favors the one in the first position
  regardless of content. **Fix:** randomize position;
  or use the *Elo-style* pairwise comparison with
  many judgments.
- **Verbosity bias.** The judge scores longer outputs
  higher regardless of quality. **Fix:** include an
  explicit "brevity is preferred" instruction in the
  rubric; normalize scores against length.
- **Self-preference bias.** A judge model prefers
  outputs from its own model family. **Fix:** use a
  *different* model family for grading than for
  generation (Claude judging GPT-4o outputs, or vice
  versa); avoid using the same model as both
  generator and judge.
- **Rubric ambiguity.** The judge's scores are
  inconsistent because the rubric leaves room for
  interpretation. **Fix:** rewrite the rubric with
  concrete examples of each score level; test
  inter-run consistency (run the judge on the same
  input twice — the score should be identical or
  very close).

Chip Huyen's Chapter 4 is the reference for these
failure modes and the calibration protocol; the
deeper statistical calibration work (inter-annotator
agreement, judge-model bias measurement, human-review
sampling design) is
[model-evaluation-engineer-learning](https://github.com/ai-engineering-curriculum/model-evaluation-engineer-learning)'s
scope.

## Dataset hosting — where labeled data lives

The eval set is a growing labeled dataset that
multiple people edit, multiple experiments read, and
the launch process references. Where it lives matters.

Three common patterns at pre-seed → Series-A:

- **A tool: Braintrust, Langfuse, Phoenix, LangSmith,
  Humanloop.** Purpose-built eval-dataset hosting
  with harness integration, judge-model runners,
  scoring UIs, and version history. Right choice for
  most teams once the eval suite passes ~100
  examples.
- **A repo: JSONL or Parquet files in a git repo.**
  Simple, versioned, diffable. Right choice for the
  first 50 examples and for teams that want the
  dataset in the same review flow as code.
- **A spreadsheet: Google Sheets or Airtable.** Right
  choice for the first 10 examples, especially when
  a non-technical CPO or PM is hand-labeling. Migrate
  to one of the above as it grows.

The wrong choice is *"no canonical home."* An eval
set that lives in the head of one engineer, in a
scratch notebook, or in a Slack thread is a set that
does not compound.

Anthropic's own docs on evaluation give one specific
pattern for the smallest useful setup — a CSV of
input / expected-output pairs, a scoring function
(rule-based or judge-based), and a run script that
compares configurations
([Anthropic, "Evaluate prompts"](https://docs.anthropic.com/en/docs/test-and-evaluate/develop-tests);
[Anthropic, "Reduce hallucinations"](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/reduce-hallucinations)).
OpenAI's *OpenAI Evals* framework is the reference
for a larger-scale, config-driven eval harness
([OpenAI, "OpenAI Evals," GitHub](https://github.com/openai/evals)).

## When the eval-suite threshold *replaces* A/B as the launch gate

For most AI-substrate feature decisions, the sequence
is:

1. **Iterate on the prompt / retrieval / tool
   configuration** against the eval suite. Ship
   changes internally that improve the score. Do
   this daily during active development.
2. **When the eval score clears the launch
   threshold**, ship the change to production
   (behind a feature flag, or to a small percent
   ramp).
3. **Monitor production traffic** against the
   guardrails: cost per interaction, p95 latency,
   error rate, user-reported issues.
4. **After N weeks in production, refresh the eval
   set** with the new failure categories production
   revealed, and repeat.

Note what is *not* here: a per-user A/B on prompt
version A vs. B. That test is either infeasible
(variance too high) or superfluous (the eval score
already showed the difference). The eval suite is
the launch gate; production monitoring is the
post-launch read.

**When A/B *does* still make sense for AI-substrate:**

- **The change is at the UX layer**, not the model
  layer — a different way to display the output,
  a different point in the flow to invoke the
  model. These are click-through / conversion
  changes and remain A/B-testable normally.
- **The change is a model-provider swap** where the
  output quality is comparable per the eval suite
  but the cost / latency / user-preference profile
  differs. Per-user A/B on latency or user-
  preference (thumbs-up / thumbs-down) is a
  legitimate use.
- **The change is a routing change** — sometimes
  use model A, sometimes model B, based on the
  query. A/B on the routing rule is legitimate.

The rule of thumb: **A/B on the click; eval on the
output.**

## Dataset drift and eval-set aging

An eval set curated in month 1 is a *sample of the
inputs that existed in month 1.* By month 6, user
inputs have shifted, new failure categories have
emerged, and the eval set no longer represents
production. If the launch threshold is still measured
against the month-1 set, launches will pass evals
and fail in production.

The discipline: **quarterly eval-set refresh.**

- Sample a fresh batch of production inputs
  (100–500).
- Human-label them.
- Compare the new-batch score distribution against
  the current eval-set score distribution. Large
  divergence signals drift.
- Add the fresh batch to the eval set. Retire (or
  re-weight) obsolete categories.
- Recalibrate the LLM-as-judge on the fresh batch.

Datasets that don't get refreshed silently rot. This
is the eval analogue of Lecture 2's "activation
definition drift" failure mode.

## The eval regime on one page

The artifact this lecture asks you to author for one
agent or LLM slice (Exercise 4):

```
FEATURE: <one AI-substrate slice — a specific agent or LLM-invoking flow>

WHAT WE'RE EVALUATING FOR
1. <dimension 1>: <specific failure mode this catches>
2. <dimension 2>: <specific failure mode this catches>
3. <dimension 3>: <specific failure mode this catches>

EVAL SET
- Size: <N examples>
- Sources: <production sample %, customer conv %, curated %>
- Coverage: <happy-path %, long-tail %, safety %>
- Hosting: <tool / repo / sheet>

GRADING
- <dimension 1>: <rule / human / LLM-as-judge>
- <dimension 2>: <rule / human / LLM-as-judge>
- <dimension 3>: <rule / human / LLM-as-judge>

LLM-AS-JUDGE CALIBRATION (for any judge-based grader)
- Rubric: <link>
- Calibration cadence: <% of grades human-reviewed weekly>
- Agreement threshold: <% or κ>
- Judge model / generator model separation: <yes/no>

LAUNCH THRESHOLD
- Regression set: <% must pass>
- Safety set: 100% must pass (or <% with rationale>)
- Happy-path aggregate: <% or Δ vs. baseline>
- Long-tail aggregate: <% or Δ vs. baseline>

POST-LAUNCH MONITORING
- Production sampling rate: <% of traffic sampled to eval batch>
- Refresh cadence: <quarterly, or triggered by drift signal>

BOUNDARIES
- What we're not evaluating for (and why)
- What we're delegating to production monitoring
```

## What the CPO does personally

- **Authors *what to eval for*.** The failure-mode
  taxonomy is a product decision.
- **Curates the initial eval set.** The first 50
  examples are the CPO's work — from mod-001
  interviews, from production traffic, from
  customer support tickets. Delegating this to eng
  yields a set that measures what eng finds easy,
  not what users need.
- **Writes and revises the judge rubrics.** The
  rubric is prose; it is microcopy for the judge
  model (like tool schemas from mod-004 Lecture 5
  are microcopy for the generator model).
- **Reads the disagreement cases.** When human
  reviewers disagree with the judge, the CPO reads
  the specific examples — that's where rubric
  ambiguity, unmeasured failure modes, and shifts
  in what "good" means all show up.
- **Sets and defends the launch threshold.**
  Threshold is a product-strategy call.
- **Runs the quarterly refresh.** Not delegable;
  drift diagnosis requires knowing what production
  inputs actually look like.

## What the CPO consumes from the eng team

- **The eval harness.** Test runners, config-driven
  execution, results storage, comparison UI. Owned
  by AI-eval engineers or a stronger eng team.
- **The judge-model infrastructure.** Model API
  wiring, cost tracking, retry logic. Owned by eng.
- **Observability tooling.** Trajectory logs, cost /
  latency metrics, error rates, sampling
  infrastructure (Langfuse / Braintrust / LangSmith
  / Phoenix / Arize). Owned by eng.
- **Statistical calibration depth.** Cohen's κ
  computation at scale, inter-annotator agreement
  studies, judge-bias measurement. Owned by an
  ML-eval or model-eval specialist if you have one;
  otherwise the CPO does the surface-level
  calibration and consumes the depth from
  [model-evaluation-engineer-learning](https://github.com/ai-engineering-curriculum/model-evaluation-engineer-learning)
  when needed.

## Boundaries this lecture keeps

- **The mod-004-Lecture-5 material** on AI-substrate
  iteration inside the weekly cadence is the
  *cadence-integration* view; this lecture is the
  eval regime itself.
- **A/B and quasi-experimental methods** for the
  non-AI parts of AI-products are still
  [Lectures 4 & 5](04-experimentation-at-pre-seed-to-series-a.md).
- **Cost / latency / quality Pareto reasoning** is
  [Lecture 7](07-cost-latency-quality-pareto.md);
  this lecture treats cost / latency as guardrail
  metrics on the eval suite, not as the primary
  trade-off surface.
- **Deep eval-harness architecture** — test-runner
  infrastructure, prompt-versioning tooling,
  trajectory replay, agentic-test-suite design at
  depth — is level-30 work owned by
  [ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning).
  The CPO consumes the harness; the AI-eval
  engineer authors it.
- **Statistical calibration at depth** — Cohen's κ
  variants, inter-annotator agreement design, judge
  bias correction, human-review sampling design at
  depth — is level-30 work owned by
  [model-evaluation-engineer-learning](https://github.com/ai-engineering-curriculum/model-evaluation-engineer-learning).
  This lecture teaches the CPO-scope calibration
  discipline (spot-check ≥ 10% weekly, track
  agreement over time); the model-evaluation
  engineer authors the rigor.
- **AI safety, alignment, and governance** at depth
  are out of scope; the AI-governance curricula
  cover them. This lecture teaches evals as a
  *product-decision surface*, with safety /
  refusal as one dimension among several.
- **The model / model-family selection decision** is
  a founder-CEO / CTO / CPO-jointly call, informed
  by the eval suite; the choice mechanism itself is
  briefly covered in
  [Lecture 7](07-cost-latency-quality-pareto.md).

## Takeaways

- LLM feature decisions are **evaluated with eval
  suites**, not per-user A/B tests. Output-quality
  variance dwarfs treatment effects; the metric of
  interest is the *quality* of the output; the
  model provider changes silently underneath.
- The CPO owns four eval-regime decisions: **what to
  eval for**, **how to grade**, **what set**, **what
  threshold**. All are product decisions.
- **Rule-based** grading for narrow outputs,
  **LLM-as-judge** for open-ended, **human** for
  calibration and the gold set. Most working
  regimes use a mix.
- **LLM-as-judge must be calibrated.** Spot-check
  ≥ 10% weekly against human review; target ≥ 80%
  agreement or Cohen's κ ≥ 0.6. Watch for position,
  verbosity, and self-preference biases.
- **Eval sets grow incrementally**, live in
  purpose-built tools (Braintrust / Langfuse / etc.)
  or a versioned repo, and are refreshed quarterly
  to prevent drift.
- **The launch threshold** is usually a
  no-regression + relative-improvement rule, not an
  absolute score.
- **A/B on the click; eval on the output.** The
  eval suite replaces A/B for prompt / retrieval /
  tool-configuration changes; UX-layer and routing
  A/Bs remain valid.

Lecture 7 turns to the **cost / latency / quality
Pareto**, the trade-off surface every LLM feature
decision runs against.
