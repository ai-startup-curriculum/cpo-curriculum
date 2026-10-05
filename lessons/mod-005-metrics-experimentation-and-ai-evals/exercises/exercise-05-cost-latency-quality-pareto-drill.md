# Exercise 5 — Cost / latency / quality Pareto drill

**Time:** ~3 hours. **Deliverable:** one **Pareto memo**
for the same AI-substrate slice evaluated in
[Exercise 4](exercise-04-llm-eval-suite-authoring-for-one-agent.md) —
three candidate configurations, measured (or defensibly
projected) numbers on all three axes, a Pareto-dominance
check, user-facing trade-off reasoning, a recommended
default config with a one-paragraph rationale, and a
pre-registered re-evaluation trigger.

## Purpose

Walk the config decision from
[Lecture 7](../lectures/07-cost-latency-quality-pareto.md)
end to end: candidate configurations compared on **cost
per interaction**, **p95 latency**, and **eval-suite
quality**; dominated configs dropped; the Pareto decision
made explicitly against the surface's user segment and
moment. This is the second half of the AI-substrate CPO
decision loop — Exercise 4 establishes *the launch
quality bar*; this exercise picks *the config that clears
it at the right cost and latency*.

The point of the exercise is to make the trade-off
*visible*. A quality-only picker ships the frontier model
for every feature and burns runway; a cost-only picker
ships the cheapest model and loses on the long tail. The
Pareto memo is how the founding CPO reasons among the
non-dominated set and *states which point on the frontier
the product operates at* for this surface.

## What you need before you start

- The slice and eval suite from
  [Exercise 4](exercise-04-llm-eval-suite-authoring-for-one-agent.md).
  This exercise is the Pareto for *that* slice; the eval
  suite is the quality axis.
- A way to measure or defensibly project **cost per
  interaction**. For a real product: per-token input +
  output costs from the provider pricing pages
  ([Anthropic pricing](https://www.anthropic.com/pricing);
  [OpenAI pricing](https://openai.com/api/pricing/);
  [Google Gemini pricing](https://ai.google.dev/pricing);
  open-model hosts' pricing pages). For a synthetic:
  look up the current pricing and compute from your
  prompt / output token estimates.
- A way to measure or defensibly project **latency**:
  TTFT, tokens/sec, p50 and p95 end-to-end — either
  measured from a real deployment or projected from
  provider benchmarks. If projected, state the source
  and the uncertainty.
- The eval harness from Exercise 4 able to run on all
  three candidate configurations. If you can only run
  one config live, run that one measured and project
  the other two from documented benchmarks + eval set
  spot-checks (state the method).

## Choosing the candidate configurations

Pick **exactly three**. Lecture 7 defines a configuration
as a combination of model + prompt + retrieval + tools +
caching
([Lecture 7 — Named configurations and CPO reasoning](../lectures/07-cost-latency-quality-pareto.md#named-configurations-and-cpo-reasoning)).
Three is enough to see the frontier; two produces a
false binary, more than three dilutes the decision.

Shape your three to span the frontier:

- **Config A — Frontier-model, full-context.** Highest
  quality, highest cost, slowest. The "we don't care
  about cost or latency, we want it right" shape.
- **Config B — Mid-tier, tightened.** Smaller or
  mid-tier model, tighter prompts, caching on,
  retrieval tuned. The "default for most users" shape.
- **Config C — Small-model or heavily-cached.**
  Smallest viable model, aggressive prompt caching,
  minimal retrieval. The "free-tier / high-throughput
  / outage-fallback" shape.

If your slice naturally produces different candidate
shapes (an agent that reasons once vs. one that
plans-act-observes five times; a RAG system with top-5
vs. top-20 retrieval), use those axes to span the
frontier.

## What the Pareto memo must contain

Use the one-page template from
[Lecture 7 — The Pareto memo](../lectures/07-cost-latency-quality-pareto.md#the-pareto-memo--the-artifact).
Two to three pages total with the reasoning sections.

### 1. The feature and the user segment it serves

One paragraph. Tie back to the Exercise 4 task
definition. State which **user segment and moment**
this config decision is for — the Lecture 7 point that
different surfaces warrant different points on the
Pareto frontier. "The free-tier user doing their first
query of the week" is a very different Pareto target
than "the enterprise analyst running a nightly batch."

### 2. Candidate configurations — spec per config (half page)

For each of the three configs, state:
- **Model** (provider + tier).
- **Prompt** — token count, structure (system +
  few-shot + context + user).
- **Retrieval** — top-N, rerank on/off, retrieval
  cost per call.
- **Caching** — Anthropic prompt-caching / OpenAI
  context-caching on or off; what fraction of the
  prompt tokens are cacheable
  ([Anthropic prompt caching docs](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching);
  [OpenAI prompt caching docs](https://platform.openai.com/docs/guides/prompt-caching)).
- **Tools** — list of tools / functions available
  (empty is fine for non-agentic surfaces).
- **Number of model calls per interaction** — 1 for a
  single-shot, N for an agent that plans-act-observes
  N times.

### 3. Measured / projected numbers (one page)

The Lecture 7 decision matrix. State *measured* for
numbers you ran against the eval harness today;
*projected* for numbers derived from documented
benchmarks + math; and name the source for each
projected number.

| | Config A | Config B | Config C |
|---|---|---|---|
| **Cost per interaction** | $0.___ | $0.___ | $0.___ |
| **p50 latency** | ___ ms | ___ ms | ___ ms |
| **p95 latency** | ___ ms | ___ ms | ___ ms |
| **TTFT (if streaming)** | ___ ms | ___ ms | ___ ms |
| **Eval — happy-path pass** | ___% | ___% | ___% |
| **Eval — long-tail pass** | ___% | ___% | ___% |
| **Eval — safety pass** | ___% | ___% | ___% |
| **Eval — category-specific** (name the categories from Exercise 4) | ___ | ___ | ___ |
| **Variance across runs** (if measurable) | ___ | ___ | ___ |

Show the cost math per config inline, using the Lecture
7 cost formula:

```
cost_per_interaction ≈
    (input_tokens · price_per_input_token)
  + (output_tokens · price_per_output_token)
  + (retrieval_tokens_read · retrieval_cost)
  + (tool_call_count · tool_cost)
```

For agentic flows, multiply by the number of calls.
For cached prompts, use the cached-token price for the
cached portion.

### 4. Pareto check (quarter page)

- **Which configs are dominated?** A config is
  dominated when another config is at least as good
  on all three axes and strictly better on at least
  one. Drop dominated configs.
- **Which configs are on the frontier?** List them.
- If all three are on the frontier (none dominated),
  the real decision is which point on the frontier
  this surface wants. If one or two are dominated, say
  so and move on.

### 5. User-facing trade-off reasoning (half page)

For the non-dominated set, work through the Lecture 7
user-facing surfaces
([Lecture 7 — Cost / latency as *user-facing surfaces*](../lectures/07-cost-latency-quality-pareto.md#cost--latency-as-user-facing-surfaces)):

- **Cost surface** — how does per-interaction cost
  show up to the user on this surface? Metered /
  quota'd / baked into price / hidden? Does the
  config's cost fit the user's pricing bucket (free /
  paid / enterprise)? Pricing craft itself is
  [mod-006](../../mod-006-pricing-packaging-and-monetization/README.md);
  this exercise asks only whether the cost is
  *compatible* with the pricing shape.
- **Latency surface** — streaming on this surface or
  not? Intermediate progress UX for agentic flows?
  Escape valves ("try again with a faster model")?
  The Lecture 7 point: streaming at 1.5s TTFT feels
  much better than non-streaming at the same total.
- **Quality gap** — if you ship the cheaper /
  faster config, what *user-visible failure mode*
  do you accept? Name it concretely from the eval
  set — "the model gets category-A long-tail wrong
  3× more often" is specific; "quality is lower"
  is not.

### 6. Recommended ship (quarter page)

- **Default config:** A, B, or C.
- **One-paragraph rationale**: *this point on the
  frontier, for this user segment, at this moment*,
  because (one reason tied to cost, one tied to
  latency, one tied to quality).
- **Fallback config:** which config you'd switch to
  if the provider degrades (outage, silent model
  update, major price change). Lecture 7 is
  emphatic that the fallback is a product decision,
  not an infra emergency.
- **Segment-dependent routing (optional).** If
  different user segments warrant different
  configs — free-tier gets Config C, paid gets
  Config B — state the routing rule.

### 7. Pre-registered re-evaluation trigger (quarter page)

The Lecture 7 "the frontier moves" discipline
([Lecture 7 — When the frontier moves](../lectures/07-cost-latency-quality-pareto.md#when-the-frontier-moves)).
Name the trigger that would re-run this exercise:

- **Model release** — within 1 week of any major
  provider release.
- **Price change** — within 1 week of a > 20% price
  change on any used model.
- **Eval drift** — any weekly eval regression of
  > 5 pp with no prompt change signals a silent
  model update; re-run.
- **Calendar trigger** — a hard 90-day re-eval date,
  even if none of the above fires.

### 8. Boundary (quarter page)

Name what you are *not* optimizing for on this surface
and why. "We are not optimizing for the lowest p95
latency — this surface tolerates a 3-second
first-response because the user runs it async."
Boundaries are what prevent the config from being
over-fit to one axis.

## Starter guidance

- **Start with the cost math, not the quality
  numbers.** The eval numbers from Exercise 4 are
  already in hand; the Pareto novelty is the cost /
  latency side. Compute cost per interaction for each
  config *first*; the shape of the Pareto comes into
  focus immediately.
- **Caching is usually underweighted.** Anthropic's
  prompt caching cuts cached-token cost ~10× and
  cached-token latency substantially; a system prompt
  that doesn't change across calls is almost always
  worth caching. If none of your configs use caching,
  revise.
- **Streaming is a product decision, not an infra
  one.** The latency surface improvement from streaming
  is one of the largest UX levers you have at any
  config choice; include it in the latency reasoning
  (Lecture 7 is emphatic).
- **Different-tier routing is a legitimate "best"
  config.** The right answer is sometimes "Config B
  for paid users, Config C for free users"; don't
  force a single config when the user segments
  genuinely differ.
- **The eval-set long-tail is where cheap configs
  break.** A 95% happy-path pass can hide a 40% long-
  tail pass; that long-tail gap is almost always
  where the user actually notices.
- **Projections are allowed; be explicit about them.**
  If you can't run config C live, project its cost
  from token math, project its latency from provider
  benchmarks, and spot-check its quality on 10
  examples. State what's measured and what's
  projected.
- **Re-run this exercise quarterly.** The 90-day
  calendar trigger exists because the frontier moves
  faster than most CPOs expect; a config decision
  rotting for six months is a config decision that is
  wrong.

## Acceptance criteria

- The **feature, user segment, and moment** are tied
  back to the Exercise 4 slice.
- **Three candidate configs** are specified at the
  Lecture 7 level of detail — model, prompt (token
  count), retrieval, caching, tools, calls per
  interaction.
- The **decision matrix** has all three axes filled —
  cost per interaction (with the math shown), p50 /
  p95 latency, eval scores by happy / long-tail /
  safety / category / variance. Measured vs.
  projected is marked.
- The **Pareto check** names dominated configs
  (if any) and the non-dominated frontier set.
- **User-facing trade-off reasoning** covers cost
  surface, latency surface, and quality gap with a
  concrete named failure mode (not a hand-wave).
- The **recommended ship** names a default, a
  one-paragraph rationale, a fallback, and
  (optionally) a routing rule.
- The **re-evaluation trigger** is pre-registered
  with specific conditions and a 90-day calendar
  date.
- A **boundary** section names what the surface is
  not optimizing for.

## Common failure modes

- **Quality-only picking.** Config A chosen because
  "it scored highest on the eval"; cost / latency
  ignored. Runs runway down. The Pareto check
  prevents this by making cost / latency first-class.
- **Cost-only picking.** Config C chosen because
  "it's cheapest"; the long-tail gap ignored. User
  trust erodes silently. The eval long-tail score
  prevents this.
- **Averaging the config.** "Our model costs about
  $0.03." The variance across configs *is* the
  decision; averaging erases it.
- **Measured-looking projections.** Numbers reported
  without "measured" / "projected" tags and no
  source. The audit test: can someone else
  reproduce? If not, state the method.
- **No caching anywhere.** The static system prompt
  isn't cached; each call pays full price. Lecture
  7 is explicit; the fix is cheap.
- **No fallback.** Provider outage happens; the team
  scrambles. The fallback config is a product
  decision pre-committed, not a scramble.
- **Static config for a moving frontier.** No re-eval
  trigger; the config decision ages six months and
  nobody noticed. The 90-day trigger exists for
  this reason.
- **Latency as end-to-end only.** TTFT ignored; the
  user feels the full generation time. For streaming
  surfaces, TTFT is the dominant metric.

## Source alignment

The cost / latency / quality framing, cost formula,
latency metrics (TTFT, p95), named configuration shapes,
Pareto-dominance reasoning, and "the frontier moves"
discipline derive from Chip Huyen, *AI Engineering:
Building Applications with Foundation Models*,
O'Reilly, 2024, Chapter 7 ("Model Serving and
Inference Optimization") and surrounding material —
[oreilly.com/library/view/ai-engineering/9781098166298](https://www.oreilly.com/library/view/ai-engineering/9781098166298/).
The prompt-caching references are Anthropic's
"Prompt caching" docs —
[docs.anthropic.com/en/docs/build-with-claude/prompt-caching](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching)
— and OpenAI's "Prompt caching" docs —
[platform.openai.com/docs/guides/prompt-caching](https://platform.openai.com/docs/guides/prompt-caching).
The perceived-latency reference is Jakob Nielsen,
"Response Times: The 3 Important Limits," Nielsen
Norman Group —
[nngroup.com/articles/response-times-3-important-limits](https://www.nngroup.com/articles/response-times-3-important-limits/).
Pricing pages: Anthropic —
[anthropic.com/pricing](https://www.anthropic.com/pricing);
OpenAI — [openai.com/api/pricing](https://openai.com/api/pricing/);
Google Gemini — [ai.google.dev/pricing](https://ai.google.dev/pricing).
