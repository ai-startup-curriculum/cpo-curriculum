# Lecture 7 — Cost / latency / quality: the AI-substrate Pareto

## The setup

For every AI-substrate feature the founding CPO
ships, three numbers move together as a joint
constraint:

- **Cost per interaction** — the dollar cost of the
  model call(s) that produced the output, plus
  retrieval, plus any tool executions billed by
  token or by request.
- **Latency** — the wall-clock time between user
  request and useful response (or first token, in
  streaming), typically reported at p50 and p95.
- **Quality** — the eval-suite score against the
  regime from Lecture 6, either as an aggregate or
  as the pass rate on the safety / regression sets.

The three form a **Pareto frontier**. You can trade
along the frontier — smaller model reduces cost and
latency at some quality cost; longer prompts and more
retrieval improve quality at cost and latency; caching
reduces cost and latency at complexity cost.
You can *not* move all three in the "better"
direction without a genuine improvement (a better
model release, a smarter retrieval, a more compact
prompt).

The founding CPO's job is to **choose the point on
the frontier** at which the product operates, defend
the choice against pressure to move any of the
three, and re-run the choice whenever the frontier
itself shifts (new model release, provider price
change, model-provider snapshot update).

This lecture teaches the vocabulary — model tiers,
context-window sizes, streaming as a UX affordance,
prompt-caching, batch inference — that lets you reason
about the frontier, and the CPO-scope decision surface
each vocabulary term names.

## The three axes, defined

### Cost per interaction

Model providers (Anthropic, OpenAI, Google, and open-
model runtimes) charge per token. For a given feature,
cost per interaction is:

```
cost_per_interaction ≈
    (input_tokens · price_per_input_token)
  + (output_tokens · price_per_output_token)
  + (retrieval_tokens_read · retrieval_cost)
  + (tool_call_count · tool_cost)
```

For agentic features that make N model calls per
task, multiply by N.

At any given price sheet, the CPO's cost levers are:

- **Which model tier.** Frontier models are ~3–30×
  more expensive than smaller models per token, and
  ~10–100× more than open small models.
- **Prompt length.** System prompts, few-shot
  examples, retrieved context. Cutting a 4k-token
  system prompt to 1k directly cuts cost.
- **Output length.** Longer outputs cost more.
  Prompting for concise outputs is a cost lever.
- **Number of model calls per task.** An agent that
  reasons once vs. one that plans-act-observe-loops
  five times differs by 5× cost.
- **Caching.** Anthropic's prompt-caching and
  OpenAI's context-caching charge less on repeated
  prompts; if your system prompt is stable across
  calls, caching cuts cost dramatically for the
  cached tokens
  ([Anthropic, "Prompt caching," 2024](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching);
  [OpenAI, "Prompt caching"](https://platform.openai.com/docs/guides/prompt-caching)).
- **Batch inference.** Non-real-time workloads
  (nightly evals, background enrichment) can use
  batch APIs at ~50% discount from most providers.
- **Provider selection.** Same-tier models across
  providers differ in per-token price; open-model
  runtimes (self-hosted or via inference services
  like Together, Fireworks, Modal, Bedrock) shift
  the cost curve entirely.

Anthropic's public pricing docs and OpenAI's pricing
page are the canonical references for
current-generation numbers
([Anthropic pricing](https://www.anthropic.com/pricing);
[OpenAI pricing](https://openai.com/api/pricing/)).

<!-- needs-research: current 2026-era per-token pricing
for Claude Opus / Sonnet / Haiku, GPT-4-tier / GPT-5-tier
/ GPT-mini-tier, Gemini 2.5 / Flash tiers, and typical
open-model-hosting prices (Together / Fireworks) — cite
the pricing pages inline in the exercise; do not invent
numbers here. -->

### Latency

Latency is the wall-clock time from request to
useful response. For non-streaming APIs, it is the
time to complete generation. For streaming APIs (the
majority of user-facing AI product interactions
today), the more useful metrics are:

- **Time-to-first-token (TTFT)** — how long before
  the user sees the first character of output.
  This is the dominant perceived-latency metric for
  streaming UIs; below ~500ms feels "instant,"
  1–2s feels responsive, > 3s feels broken.
- **Tokens per second (throughput)** — how fast
  subsequent tokens arrive. Larger models are
  slower per token; smaller models are faster.
- **End-to-end latency (p50 / p95)** — from request
  to completion. Matters for non-streaming
  interactions (batch summarization, tool-call
  planning) and for the tail of streaming.

For agentic workflows (N calls per task):

- **End-to-end task latency** — sum of per-call
  latencies plus tool-execution time. An agent that
  makes 5 calls at 2s each takes 10s to complete.
- **Time-to-first-useful-signal** — often much less
  than end-to-end, if the UX shows intermediate
  progress ("searching…", "found 3 relevant
  documents…").

Latency levers:

- **Model tier.** Smaller models are faster per
  token; TTFT can be 3–10× lower on a smaller model.
- **Prompt length.** A 4k-token prompt takes longer
  to process (higher TTFT) than a 1k-token prompt,
  even for the same output.
- **Streaming.** A non-streaming API returns after
  the full generation; a streaming API returns
  tokens as they're generated. Streaming lowers
  *perceived* latency dramatically without changing
  the total.
- **Parallel model calls** for agentic tasks. Where
  the plan graph allows independent sub-calls,
  running them in parallel cuts total task latency.
- **Speculative decoding, batched inference, and
  faster hardware** — infra-side levers the CPO
  consumes from eng.

Chip Huyen's *AI Engineering* Chapter 7 covers the
latency-optimization trade-offs in depth
([Huyen, *AI Engineering*, Chapter 7](https://www.oreilly.com/library/view/ai-engineering/9781098166298/)).

### Quality

Quality is the eval-suite score from Lecture 6.
Every point on the Pareto is characterized by a
specific eval-score vector — not just one number.
The important quality dimensions to watch across
configurations:

- **Aggregate happy-path pass rate.** The most
  visible number; often the most misleading.
- **Long-tail pass rate.** The harder measure;
  where smaller models often fail dramatically vs.
  frontier models.
- **Safety / refusal pass rate.** Non-negotiable
  guard; any regression is a blocker.
- **Category-specific pass rates.** For the
  specific failure modes the product surface
  cares about (tool-selection accuracy for an
  agent, citation accuracy for a RAG system).
- **Variance.** How consistent is the output
  across identical requests? Frontier models often
  have lower variance; smaller models more.

## The frontier — what a Pareto tradeoff looks like

A stylized picture:

```
                    Quality
                       ^
                       |
             *          |
              *         |     * = frontier model, full prompt
                *       |         (high quality, high cost,
                  *     |          high latency)
                    *   |
                      * |     ° = smaller model, cached prompt
                        *          (medium quality, low cost,
                         *          low latency)
                          °|
                           °|
                            °|
                             °|-- open small model, no retrieval
                              °|   (low quality, very low cost,
                               °|    very low latency)
                                °|
                                 °-------------------> Cost (log scale)
```

Latency is a third axis; imagine the picture in 3D.
Different points are appropriate for different
product surfaces:

- **A chat assistant users pay for on demand:**
  quality dominates. Frontier model, full retrieval,
  no cost-corner-cutting. Cost-per-interaction
  budget is high.
- **A background enrichment job:** cost dominates.
  Batch API, smaller model, tighter prompts.
  Latency is invisible to the user.
- **An autocomplete-style inline UX:** latency
  dominates. Streaming, smallest model that clears
  the quality bar, prompt caching, tight prompts.
- **A safety-critical or high-stakes decision
  surface:** quality with tight guardrails,
  regardless of cost / latency.

## Named configurations and CPO reasoning

The founding CPO reasons about **candidate
configurations** — combinations of model, prompt,
retrieval, tools, and caching — as discrete options
to evaluate on all three axes.

A typical decision matrix for a single feature might
look like:

| Config | Model | Prompt | Retrieval | Caching | Cost/interaction | p95 latency | Eval score (happy) | Eval score (long-tail) | Safety pass |
|---|---|---|---|---|---|---|---|---|---|
| A | Frontier | 4k, full context | Top-10 rerank | Off | $0.08 | 4.2s | 92% | 78% | 100% |
| B | Mid-tier | 2k, tight context | Top-5 rerank | On | $0.02 | 1.8s | 88% | 65% | 100% |
| C | Small (open) | 1k, minimal | Top-3, no rerank | On | $0.001 | 0.6s | 78% | 40% | 98% |
| D | Frontier | 2k, tight context | Top-10 rerank | On | $0.04 | 2.4s | 91% | 76% | 100% |

**Config B** is the classical "good enough for most
users" middle. It costs 4× less than A, is 2× faster,
and gives up 4 points on happy path and 13 on long
tail. Ship it as the default if the surface can
absorb the long-tail gap.

**Config D** is a compromise — same model as A but
tighter prompt and caching enabled. Similar quality,
half the cost, better latency. Usually the right
answer when A is "too expensive."

**Config C** is the "for the free-tier user"
configuration — cheap and fast, quality gap large.
Not the default; potentially a paid-tier / free-tier
differentiator (mod-006 territory) or a fallback
when the primary model provider has an outage.

**The Pareto move**: any config *dominated* by
another (worse on all three axes) is off the
frontier and should be discarded. Reason among the
non-dominated set.

## Cost / latency as *user-facing surfaces*

Mod-004 Lecture 5 made this point briefly; this
lecture makes it operational. Both cost and latency
are not just infrastructure metrics — they are
product-design decisions with visible consequences.

**Cost as user-facing:**

- **Metering and quotas.** For a
  pay-per-use / credits product (many AI-native
  products at pre-seed), each interaction's cost
  is exposed to the user as a credit deduction. The
  cost per interaction *is* the pricing (mod-006
  territory).
- **Free-tier and paid-tier separation.** Different
  configs for different tiers is a legitimate
  design; a free-tier user gets Config C, a paid
  user gets Config B, an enterprise user gets
  Config A.
- **Cost caps.** A user-visible "you've used $X of
  $Y this month" surface. Requires per-user cost
  tracking (an eng ask).

**Latency as user-facing:**

- **Streaming as an affordance.** A streaming
  interface at 1.5s TTFT feels much better than a
  non-streaming interface at the same total time.
  Streaming is a product decision, not an infra
  one.
- **Intermediate progress.** For agentic
  interactions, showing "searching for X…",
  "found 3 relevant documents…", "drafting
  response…" turns a 15-second wall of latency
  into a legible sequence of steps.
- **Optimistic UI.** Show the plan or the
  intermediate output while the final answer is
  still generating.
- **Escape valves.** "Cancel" buttons, "try again
  with a faster model" fallbacks. Give the user
  agency when a long-running task feels stuck.

Kelly Cheng's writing at
[latencytipoftheday.blogspot.com](https://latencytipoftheday.blogspot.com/)
and the practitioner literature on perceived
latency (Nielsen Norman Group's work on response
time) are the deeper reads
([Nielsen, "Response Times: The 3 Important Limits"](https://www.nngroup.com/articles/response-times-3-important-limits/)).

## When the frontier moves

The frontier is not static. Three moves the CPO
watches for:

- **A new model release.** Anthropic ships a new
  Claude tier; OpenAI ships a new GPT tier; Google
  ships a new Gemini tier. Every release typically
  pushes the frontier up-and-right (better quality
  at similar cost, or same quality at lower cost).
  The CPO re-runs the config decision within a week
  of any major model release.
- **A provider price change.** Providers cut prices
  every few months; a 40% price cut on the mid-tier
  moves Config B's cost from $0.02 to $0.012, which
  may make it the default for surfaces where cost
  was previously the blocker.
- **A silent model update.** Providers occasionally
  update the model behind an API endpoint without a
  version bump — behavior shifts subtly, evals
  regress or improve. The eval suite is what
  detects this; the CPO re-runs the config decision
  when evals show a change with no prompt change.

**Discipline:** the config decision has a **stated
horizon** — "current best config as of Q3 2026." Do
not treat it as forever. Add a calendar reminder
90 days out to re-evaluate.

## The Pareto memo — the artifact

The Exercise 5 artifact:

```
FEATURE: <same one-slice feature from Exercise 4>

CANDIDATE CONFIGURATIONS (3)
Config A: <named specifics>
  - Model: <>
  - Prompt: <token count, structure>
  - Retrieval: <top-N, rerank on/off>
  - Caching: <on/off, cached prefix>
  - Tools: <list>

Config B: <named specifics>
Config C: <named specifics>

MEASURED / PROJECTED NUMBERS

|          | Config A | Config B | Config C |
|----------|----------|----------|----------|
| Cost/int | $0.___   | $0.___   | $0.___   |
| p50 lat  | ___ ms   | ___ ms   | ___ ms   |
| p95 lat  | ___ ms   | ___ ms   | ___ ms   |
| Eval-hap | ___%     | ___%     | ___%     |
| Eval-tail| ___%     | ___%     | ___%     |
| Safety   | ___%     | ___%     | ___%     |

PARETO CHECK
- Is any config dominated? <yes/no; if yes, drop it>

USER-FACING TRADE-OFFS
- Cost surface: <how does per-interaction cost show up
  to the user? metering / quotas / plan / hidden>
- Latency surface: <streaming? intermediate progress?
  escape valves?>
- Quality gap: <if we ship the cheaper config, what
  user-visible failure mode do we accept?>

RECOMMENDED SHIP
- Default: Config <>
- Reasoning (one paragraph): why this point on the
  frontier for this surface, this user segment, this
  moment.
- Fallback: Config <> (when provider degrades or
  cost spikes)

RE-EVAL TRIGGER
- Model release: within 1 week of any major provider
  release
- Price change: within 1 week of a >20% price change
- Eval drift: any weekly eval regression >5 pts

BOUNDARY
- What we're not optimizing for on this surface
  (and why)
```

## What the CPO does personally

- **Owns the config decision.** Which model, which
  prompt shape, which caching, which retrieval
  depth — CPO calls.
- **Reads the eval suite across configs.** Not just
  the aggregate; the per-category breakdown, the
  variance, the failure examples.
- **Sets the cost and latency budgets in the
  six-pager.** Mod-004 Lecture 3's PRD form
  includes cost / latency budgets as first-class
  pre-registered signals.
- **Names the frontier-moved trigger.** What model
  release, what price change, what eval drift
  will trigger a re-run of the config decision.
- **Owns the user-facing cost / latency surfaces.**
  Streaming, intermediate progress, quotas,
  fallbacks.

## What the CPO consumes from eng

- Per-interaction cost measurement (eng
  instrumentation).
- p50 / p95 latency measurement per config (eng
  observability).
- Model / provider infrastructure (eng platform).
- Caching and batching infrastructure (eng
  platform).
- Model-family selection for hosting (open-model
  runtimes, self-hosted inference) — a CTO / eng-
  lead decision the CPO informs.

## Boundaries this lecture keeps

- **The eval regime itself** is
  [Lecture 6](06-eval-driven-decisions-for-llm-products.md);
  this lecture *uses* eval scores as the quality
  axis but does not re-teach the eval regime.
- **A/B on the UX surface** for cost / latency
  design decisions (e.g., "does streaming vs.
  non-streaming affect conversion") remains valid
  and is
  [Lecture 4](04-experimentation-at-pre-seed-to-series-a.md)
  territory.
- **Model / provider selection and vendor
  negotiation** at the founder / CTO level are
  outside CPO scope; the CPO informs the choice
  from the eval + Pareto data.
- **Pricing and packaging** — how cost per
  interaction becomes user-facing pricing — is
  [mod-006](../../mod-006-pricing-packaging-and-monetization/README.md).
  This lecture treats cost as a *constraint*; pricing
  is what turns cost into revenue.
- **AI infra depth** — batch APIs, speculative
  decoding, KV-cache mechanics, self-hosted
  inference stacks — is out of scope for CPO
  curriculum. See
  [rag-engineer-learning](https://github.com/ai-engineering-curriculum/rag-engineer-learning),
  [agentic-ai-engineer-learning](https://github.com/ai-engineering-curriculum/agentic-ai-engineer-learning),
  and
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)
  for the engineering depth.

## Takeaways

- **Cost, latency, and quality form a Pareto
  frontier**; you trade along it, you don't beat
  it (except when the frontier itself moves).
- The **CPO owns the config decision** — which
  model, prompt shape, retrieval depth, caching —
  and states which point on the frontier the
  product operates at.
- **Compare 3 candidate configs on all three axes**
  before shipping. Drop dominated configs. Reason
  among the non-dominated set.
- **Cost and latency are user-facing** — metering
  and quotas expose cost; streaming and
  intermediate progress design around latency.
- **The frontier moves** with model releases,
  provider price changes, and silent model updates.
  Set a 90-day re-evaluation calendar; watch for
  eval drift as the silent-update signal.
- Author the **Pareto memo** for every AI-substrate
  slice: candidate configs, measured numbers,
  Pareto check, user-facing trade-offs,
  recommended ship, re-eval trigger.

This is the last lecture of the module. Exercises 1
through 6 make the material operational against a
real (or plausible synthetic) product; each
exercise's deliverable feeds the next one.
