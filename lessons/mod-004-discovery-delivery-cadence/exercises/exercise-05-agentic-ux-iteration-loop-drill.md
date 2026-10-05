# Exercise 5 — Agentic UX iteration loop drill

**Time:** ~3 hours. **Deliverable:** one agentic-UX
iteration-loop design for a specific AI-substrate slice
of your product — four-surface authoring (prompt /
retrieval / tool-call / cost-latency), one full pass
through the five-step loop with a documented change, an
eval-regime design, a trajectory-review ritual, and a
reviewer's memo on what the CPO found reading real
output.

## Purpose

Run the AI-substrate iteration loop from
[Lecture 5](../lectures/05-agentic-ux-iteration-loops.md)
end to end, personally, on one narrow slice. The point
is not to produce the perfect prompt or the optimal
retrieval configuration — the point is to practice the
loop (observe output → identify failure → change one
thing → evaluate → ship) so the vocabulary and the
muscle memory become real. The single most common way
founding CPOs get sidelined on AI-substrate decisions
is the vocabulary gap; this exercise closes it.

## Choosing the slice

Pick one narrow AI-substrate slice of your product
(real or synthetic). In order of preference:

1. **An LLM-substrate slice of the Exercise 3 bet** —
   if the six-pager's mechanism involves a model call,
   a retrieval step, or a tool-call surface, use that.
2. **A live AI-substrate slice of your current
   product** — a classifier, a summary generator, a
   draft-writer, an in-product chat, an agentic
   workflow. If you ship LLM output to a user, pick
   one surface where that output lands.
3. **A plausible synthetic AI-substrate slice** on the
   Exercise 1 / 2 synthetic product. If synthetic,
   name the input (what the user types / selects), the
   model output (what the user sees), and the surface
   it appears on, in one paragraph.

Narrow is the whole point. Not "all AI features in the
product" — one slice, one output type, one eval set.

## What the deliverable must contain

Five to seven pages. Adopt the shape from
[Lecture 5](../lectures/05-agentic-ux-iteration-loops.md),
in the following order.

### 1. Slice memo (half page)

- **The slice.** What does the user ask for or do, and
  what does the model produce? Example: *"The user
  types a compliance question in plain English; the
  model returns a drafted evidence request with a
  cited source policy and a review-before-send
  gate."*
- **The user outcome.** What is the user actually
  trying to accomplish — their JTBD (mod-001) at the
  moment the model is invoked?
- **The failure cost.** What breaks when the model is
  wrong? Wasted user time, embarrassing output sent
  externally, data loss, trust loss, legal exposure?
  The failure cost shapes the eval threshold.
- **Current state.** If this slice already ships,
  name the baseline model (Claude Sonnet / Opus /
  Haiku / OpenAI equivalent / open-model), the current
  prompt structure in one paragraph, the retrieval
  configuration if any, and the tool-call set if any.
  If pre-launch, name the plausible starting
  configuration.

### 2. The four-surface authoring (one page)

Author each of the four
[AI-substrate surfaces from Lecture 5](../lectures/05-agentic-ux-iteration-loops.md#the-four-surfaces-of-the-ai-substrate-product):

- **Prompt.** Draft (or paste) the system prompt,
  response-format section, refusal / safety framing,
  and any few-shot examples. CPO-authored, not
  engineer-authored. If the current prompt is
  engineer-authored, rewrite it.
- **Retrieval configuration.** Name the corpus the
  model retrieves from (which documents, which
  freshness window, which tenant-scoped filter), when
  retrieval is triggered, and the top-k / re-ranking
  policy at the *product-decision* level. Delegate the
  chunking / embedding math to the eng team; author
  the surface choices.
- **Tool-call schemas.** For each tool the model can
  call, name: tool name, one-sentence description
  (the model reads this), the argument-schema shape at
  surface level (which arguments and what they mean —
  not the full JSON schema), and the side-effect
  behavior (what the tool does, whether it mutates
  state, whether a human has to approve).
- **Cost and latency budget.** Name the per-interaction
  cost budget (in USD or token count) and the p50 /
  p95 latency budget (in milliseconds / seconds), both
  as *user-facing* numbers. If the slice is agentic
  (multi-step), multiply by the plausible step count
  and name the aggregate budget.

For AI-substrate microcopy — the trust-model strings
around the model output — reference
[Exercise 4](exercise-04-figma-mockup-and-microcopy-drill.md)
rather than duplicating the authoring here.

### 3. One pass through the five-step loop (one page)

Run one full pass of the
[five-step iteration loop from Lecture 5](../lectures/05-agentic-ux-iteration-loops.md#the-iteration-loop-one-version),
documenting the pass as it happens. Not hypothetical —
run it.

- **Step 1 — observe output.** Pull a sample of 20–30
  real interactions (or, pre-launch, run the current
  prompt against a curated set of 20–30 realistic
  inputs). Read every one. Not metrics — actual input
  / output pairs. Attach five of them to the
  appendix, with your margin notes on what each got
  right or wrong.
- **Step 2 — identify a specific failure category.**
  Name one category you want to fix. Not a vague
  complaint ("sometimes it's wrong"). A named
  category: *"the model over-explains when the user
  asked a yes-or-no question"* / *"retrieval is
  pulling the wrong policy when the query contains
  the word 'compliance'"* / *"the create-record tool
  is being invoked when the user only asked a
  question."* Name the category and estimate its
  frequency across the sample.
- **Step 3 — change one thing.** Change exactly one
  of: system prompt, few-shot examples, retrieval
  config, tool-call description, or (last resort)
  model tier. Not two. Document the change — the
  before and after, with a one-sentence rationale.
- **Step 4 — evaluate the change.** Run the changed
  configuration against (a) the eval subset that
  covers the failure category and (b) a regression
  set of previously-known-good interactions. Document
  the result: how many failure-category items got
  fixed, how many regressions appeared.
- **Step 5 — ship.** Describe how the change would be
  deployed on your team — behind a feature flag, to a
  subset of traffic, with a named metric that would
  tell you (within a week) whether the change is
  working. If the slice is synthetic, describe the
  staging / canary / flag mechanic as it would run.

### 4. The eval-regime design (one page)

Author the four
[eval-regime decisions from Lecture 5](../lectures/05-agentic-ux-iteration-loops.md#evals-as-a-product-decision-surface):

- **What are we evaluating for?** Pick the two or
  three failure modes that matter most for *this
  slice*. Correctness, tone, format adherence,
  refusal behavior, hallucination rate, tool-selection
  accuracy, retrieval precision. Not all at once.
- **How is grading done?** For each eval, name the
  grading approach: human labeling, LLM-as-judge, or
  rule-based. If LLM-as-judge, name the calibration
  step (sample N items, have a human grade them, check
  judge agreement before trusting). Note that mod-005
  owns the methodology at depth; here, the CPO
  specifies the product decision.
- **What is the eval set?** Describe the input set —
  size, how it was sourced (production traffic,
  curated from interviews, synthetic adversarial), and
  how the happy-path / long-tail split is covered.
  Curating the set is a discovery activity; cite the
  mod-001 interviews or data pulls behind it.
- **What is the threshold?** Author a product-level
  threshold: *"≥85% correct on the top-100-account
  input set, with no regression on the refusal-
  behavior eval, p95 latency ≤2.5s, cost per
  interaction ≤$0.02."* The threshold goes into the
  Exercise 3 six-pager as a pre-registered signal.

### 5. Trajectory-review ritual (half page — if agentic)

If the slice is **agentic** — the model plans, calls
tools, observes results, plans again — author the
weekly trajectory-review ritual from
[Lecture 5](../lectures/05-agentic-ux-iteration-loops.md#the-agentic-ux-iteration-loop-extended):

- **Sample size.** How many trajectories per week the
  CPO reads (typically 20–30).
- **What to look for.** Loops the agent got stuck in,
  tools it should have used but didn't, costly
  detours, silent tool failures with confabulated
  final outputs.
- **Where trajectories live.** The observability tool
  the eng team uses (Langfuse, Braintrust, LangSmith,
  a home-built logging pipeline). The CPO's job is to
  be *in the tool*, weekly.
- **How findings feed the loop.** How the week's
  trajectory findings land in the Thursday sync
  ([Lecture 1](../lectures/01-dual-track-discovery-delivery-cadence.md))
  and become the next iteration on prompts, tool
  schemas, or retrieval.

If the slice is a single-shot model call (not agentic),
state that explicitly and skip the trajectory-review
authoring. One-shot slices do not need trajectory
review; they do need the four-surface authoring and
the eval regime.

### 6. MCP posture (quarter page)

Name your product's current and intended
[Model Context Protocol](https://modelcontextprotocol.io/specification)
posture, consulting
[Lecture 5](../lectures/05-agentic-ux-iteration-loops.md#mcp-as-an-integration-lever):

- **Do we consume MCP?** Are there MCP servers in the
  customer ecosystem for the systems we would
  otherwise write bespoke integrations for? If so,
  does the roadmap sequencing favor consuming them
  before building bespoke?
- **Do we expose an MCP server?** Would exposing our
  product's core data and actions over MCP make us a
  more valuable node in the broader AI ecosystem, or
  cede value to the AI client wrapping us? This is a
  mod-003 Lecture 4 (platform-vs-point-product)
  decision in disguise.
- **What is the security / permissions model?** Any
  tool that mutates data needs an authorization model
  the customer trusts. Name the affordance the
  customer sees (review-before-execute, allow-list of
  callers, scoped tokens).

If MCP is not relevant to your product today, state so
in one sentence and move on. Do not force the posture.

### 7. Cadence integration (quarter page)

How the four-surface iteration lands inside the
Exercise 1 cadence. Specifically, from
[Lecture 5](../lectures/05-agentic-ux-iteration-loops.md#what-lands-in-the-cadence):

- **Daily eval sweep.** During active development on
  the slice, name the overnight eval and the
  morning-stand-up pattern.
- **Weekly trajectory review** (if agentic). Which day
  the CPO reads trajectories, how long it takes, where
  the findings land.
- **Cost / latency dashboard as a product KPI.** How
  the slice's cost and latency numbers get reviewed —
  in the Friday ship review, on the product dashboard,
  not just in the SRE stack.

## Starter guidance

- **Narrow is the point.** The entire exercise is
  about *one* slice. If you are tempted to run it on
  "all AI features," pick the narrowest one you can
  defend as representative and run it there.
- **Read actual output, not aggregate metrics.**
  Simon Willison's non-negotiable: you have to read
  the model's output to know if your product works.
  Delegating the reading is the single most common
  CPO failure on AI substrate.
- **Change one thing at a time.** Prompt edit *and*
  retrieval config change *and* model tier swap, all
  at once, teaches you nothing about which change
  did what. Serialize the changes.
- **Use the regression eval set.** The failure
  category you fix is not the only thing in the
  product. A change that fixes category A while
  breaking B is a regression; the regression set
  catches it.
- **Author the prompt yourself.** The prompt is
  microcopy. It is a user-outcome-shaped artifact,
  not a technical artifact. If the current prompt
  was authored by an engineer at midnight, rewrite
  it.
- **Cost and latency are product KPIs.** Not just SRE
  metrics. Both go in the six-pager pre-registered
  signals; both get walked at the Friday ship
  review.
- **If you have never run an eval sweep end to end,
  pair with the eng lead on this exercise.** The
  vocabulary gap closes only when you have run the
  loop personally — but pairing is faster than solo
  on the mechanics the first time.

## The reviewer's memo

Half a page, written after the five-step pass and the
eval-regime design. Answer:

- **What did reading real output surface that you
  would not have noticed from aggregate metrics?** Be
  specific. Which input / output pair was the one
  that revealed the failure category? What about it
  made the category visible?
- **Which of your changes to the four surfaces was
  highest leverage?** Prompt edit, retrieval tweak,
  tool-call description, or model tier? Why? Would
  the other three have had similar effects, or was
  this specific?
- **What is the vocabulary gap you still have with
  eng?** Name one or two concepts (vector-store
  retrieval, re-ranking, context-window packing,
  structured-output enforcement, prompt caching, MCP
  server authorship) where you cannot yet have the
  working-level conversation with the eng team.
  Running the loop personally does not close every
  gap; naming the remaining ones is the next
  learning task.

## Acceptance criteria

- Slice memo names input, output, user outcome,
  failure cost, and current state.
- All four AI-substrate surfaces are authored —
  prompt, retrieval, tool-call schemas, cost /
  latency budget — at the product-decision level.
- The five-step loop is run (not described
  hypothetically); the appendix contains at least
  five real input / output pairs with margin notes.
- The change (step 3) is a single-variable change
  with before / after and rationale.
- The eval-regime design names what is evaluated, how
  it is graded, what the eval set is, and the
  threshold.
- Trajectory-review ritual is authored for agentic
  slices (or explicitly skipped for single-shot
  slices).
- MCP posture is named (consume, expose, or
  explicitly not-applicable).
- Cadence integration section names daily eval sweep,
  weekly trajectory review (if agentic), and cost /
  latency as a product KPI.
- Reviewer's memo answers all three prompts and names
  at least one remaining vocabulary gap.

## Common failure modes

- **Reading-by-metrics.** The CPO looks at
  aggregate accuracy / token-cost dashboards and
  skips the per-interaction reading. This is the
  single most common AI-substrate CPO failure.
  Read actual output pairs; the dashboard hides the
  failure modes.
- **Change-everything-at-once.** Prompt + retrieval +
  tool-schema + model tier, all changed in one pass.
  You learn nothing; you only ship.
- **No regression set.** The eval sweep covers only
  the failure category; previously-known-good
  interactions are not in the set. Regressions ship
  silently.
- **Prompt-written-by-engineer.** The system prompt
  is engineer-authored and the CPO has never read
  it. The prompt is microcopy; author it.
- **Cost / latency ignored.** The slice ships with a
  great eval result and a $0.30-per-interaction
  cost that breaks the pricing model (mod-006). Both
  cost and latency are user-facing surfaces.
- **Trajectory review for a non-agentic slice.**
  Over-authoring the trajectory ritual for a single-
  shot model call. If the slice is one model call
  with no tool-use loop, trajectory review is not
  the right ritual; skip it.
- **MCP as fashionable afterthought.** Writing an MCP
  posture section when MCP is not relevant to the
  product today. State "not applicable" and move on.
  The lecture does not ask every product to use MCP;
  it asks every CPO to recognize when it matters.
- **Vocabulary bluffing.** The reviewer's memo claims
  no remaining vocabulary gap. Running the loop
  closes some gaps and reveals others; the honest
  answer is always "here are the next two or three
  concepts I need to learn."

## Source alignment

The four-surface model and the five-step iteration
loop derive from Simon Willison's running commentary
on practitioner LLM product work at
[simonwillison.net](https://simonwillison.net/) —
especially the posts tagged *evals* and *prompt
engineering* at
[simonwillison.net/tags/evals](https://simonwillison.net/tags/evals/)
and
[simonwillison.net/tags/llms](https://simonwillison.net/tags/llms/).
The eval-regime discipline derives from Hamel Husain,
"Your AI Product Needs Evals," May 2024 —
[hamel.dev/blog/posts/evals](https://hamel.dev/blog/posts/evals/) —
and the follow-up "Field Notes" essays on
[hamel.dev](https://hamel.dev/). Tool-use conventions
derive from Anthropic's documentation at
[docs.anthropic.com/en/docs/build-with-claude/tool-use](https://docs.anthropic.com/en/docs/build-with-claude/tool-use).
The Model Context Protocol derives from Anthropic's
November 2024 announcement —
[anthropic.com/news/model-context-protocol](https://www.anthropic.com/news/model-context-protocol) —
and the official specification at
[modelcontextprotocol.io/specification](https://modelcontextprotocol.io/specification).
Cost / latency as a user-facing surface is grounded in
Anthropic's public pricing and model documentation at
[anthropic.com/pricing](https://www.anthropic.com/pricing)
and the API reference at
[docs.anthropic.com](https://docs.anthropic.com/).
Trajectory-observability tooling is a moving target;
Langfuse ([langfuse.com](https://langfuse.com/)) and
Braintrust ([braintrust.dev](https://www.braintrust.dev/))
are the most commonly referenced at time of writing —
<!-- needs-research: verify the market-leading
trajectory observability tool as of the current
quarter; substitute if a different vendor dominates. -->
Eval-methodology depth is owned by
[mod-005](../../mod-005-metrics-experimentation-and-ai-evals/README.md);
this exercise is only about the cadence integration.
