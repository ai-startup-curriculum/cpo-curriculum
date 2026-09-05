# Lecture 3 — AI / LLM system architecture at founding-PM depth

## The setup

An AI/LLM-native product is not a black box behind an
API call. It is a **system** — a pipeline that
assembles context, calls a model (or a chain of
models), executes tools, evaluates outputs, budgets
cost and latency, and recovers from failure. The
founding CPO at a 2026 AI-native company is expected
to reason about that system at enough depth to author
PRDs that describe it accurately, to hold scope
conversations with the eng team on merit, and to know
when the design has an architectural gap the product
strategy will not survive.

The market signal is direct. Harper, commercetools,
and Cradle — three of the shapes this module keys
against — ask for a founding PM who can talk about
retrieval, context engineering, tool contracts, and
eval loops in the same conversation. Not deep enough
to *build* the retrieval layer (that is
[rag-engineer-learning](https://github.com/ai-engineering-curriculum/rag-engineer-learning))
or to *build* the eval harness (that is
[ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning))
or to *build* the agent orchestrator (that is
[agentic-ai-engineer-learning](https://github.com/ai-engineering-curriculum/agentic-ai-engineer-learning)),
but deep enough to *reason about* each and to know
which questions land in which layer.

This lecture teaches the founding-CPO reading depth.
It is the level-consumption layer above the three peer
engineering curricula, not a substitute for any of
them.

## The five layers to reason about

An AI-substrate product typically has five layers the
CPO should be able to name and reason about:

1. **Context.** What information goes into the model
   call, why, and where it came from.
2. **Retrieval.** How the system fetches the right
   context from a corpus the model doesn't know
   by default.
3. **Tools / MCP.** How the model interacts with
   the outside world — reads state, takes actions,
   invokes services.
4. **Evaluation.** How the system knows whether the
   output is good.
5. **Cost / latency budget.** How much each
   invocation costs, how long it takes, and how
   those envelopes get enforced.

Each layer has a distinct set of choices, a
distinct set of failure modes, and a distinct set
of product surfaces the CPO owns.

## Layer 1 — Context engineering

*"Context engineering"* is the current umbrella
term for the discipline of assembling what goes
into a model call. It is the systematic descendant
of *"prompt engineering"* — the same discipline
after the field recognized that most of the work
is not writing the instruction, it is deciding
what other information to include and how to
structure it.

For a founding CPO, the four decisions to reason
about per context:

- **What information does the model need?** User
  input, prior conversation state, retrieved
  documents, retrieved user-specific data, tool
  descriptions, output format instructions,
  guardrails / policy. Any missing piece
  produces a specific failure mode; any
  unnecessary piece burns tokens and increases
  latency.
- **In what order?** Most current frontier models
  attend better to information near the beginning
  and end of the context than to the middle;
  Anthropic's and OpenAI's model cards discuss
  positioning effects. The CPO doesn't tune the
  order themselves, but knows the order matters.
  <!-- needs-research: verify the "positioning effects" claim against current Anthropic Claude and OpenAI GPT model cards for 2026 model families. -->
- **Prompt caching?** For workflows where the
  same large prefix is used across many calls
  (a long system prompt, retrieved documents
  reused in a session), prompt caching cuts
  cost significantly. See
  [Anthropic prompt caching documentation](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching)
  and the equivalent
  [OpenAI documentation](https://platform.openai.com/docs/guides/prompt-caching).
- **Structured output vs. free text?** A model
  returning free text puts the parsing burden on
  the calling code and produces frequent
  malformed responses. A model returning
  structured JSON (via a schema-enforcement
  mechanism like [Anthropic's tool use for
  structured outputs](https://docs.anthropic.com/en/docs/agents-and-tools/tool-use/overview)
  or OpenAI's *structured outputs* mode) shifts
  the constraint to the model and produces
  well-formed responses at the cost of some
  flexibility.

The founding-CPO version of a context PRD names,
for each model call the feature makes: what goes
in, in what order, what's cached, what the output
schema is. Every one of those choices is a product
decision because each affects cost, latency, and
failure shape.

## Layer 2 — Retrieval

Retrieval is how the system fetches context the
model doesn't know. The most common shape is RAG —
retrieval-augmented generation — but it isn't the
only one.

Four retrieval shapes the founding CPO reasons
about:

- **Vector search.** Documents are embedded into
  a vector space; the query is embedded; the
  top-k nearest documents are pulled and put in
  context. Fast, general-purpose, has failure
  modes around lexical vs. semantic mismatch.
- **BM25 / lexical search.** Classic keyword-
  based information retrieval. Better than vector
  search for exact-match queries (product SKUs,
  named entities, exact quotes); worse for
  semantic queries.
- **Hybrid search.** Vector + BM25 combined via
  reciprocal rank fusion or similar. Often the
  best real-world shape; the industry-standard
  reference is Elastic's and Weaviate's writing
  on hybrid retrieval.
- **Structured / SQL retrieval.** For structured
  data (user records, order histories, analytics
  events), a database query outperforms any
  vector store. The failure mode is treating
  structured data as unstructured and vectorizing
  it — an easy PRD mistake.

The CPO's decision surface on retrieval:

- **What corpus is being retrieved from?** The
  product's own documentation, the customer's
  uploaded data, the customer's connected data
  sources (via connectors or MCP), public web?
  Each has a distinct legal / privacy / freshness
  story.
- **How fresh does the corpus need to be?** Real-
  time (indexed on write)? Hourly? Daily? Weekly?
  Freshness affects the indexing pipeline's cost
  and complexity.
- **What's the failure mode when retrieval
  misses?** Model hallucinates? Model says
  "I don't know"? User sees an "I don't have
  that information" message? The CPO owns the
  UX of the miss.
- **How is retrieval quality measured?** Recall@k,
  MRR, human-graded relevance? See
  [rag-engineer-learning](https://github.com/ai-engineering-curriculum/rag-engineer-learning)
  for the depth; the CPO reads the metrics but
  doesn't design the eval.

The CPO's PRD names the corpus, freshness
expectation, retrieval shape (vector / hybrid /
structured), and the empty-retrieval UX. Depth
of retrieval-tuning craft is
[rag-engineer-learning](https://github.com/ai-engineering-curriculum/rag-engineer-learning);
the CPO defers on tuning parameters (chunk size,
overlap, embedding model choice, reranker
selection) to the engineer who owns the retrieval
layer.

## Layer 3 — Tools and MCP

Tools are how a model interacts with the outside
world beyond text generation. In 2026, tool use is
first-class in every major frontier model —
Anthropic's Claude, OpenAI's GPT, Google's Gemini
— and the vocabulary has largely converged.

The 2024-introduced **Model Context Protocol
(MCP)** — [modelcontextprotocol.io](https://modelcontextprotocol.io/) —
is Anthropic's open specification for how a model
discovers and invokes tools, resources, and
prompts from an external server. As of 2026, MCP
adoption is broad across model providers and
IDE / agent products. The founding CPO should
read the MCP specification once, because the tool
contracts your product exposes (to other agents,
via MCP servers) and consumes (from other
services, via MCP clients) are increasingly the
integration surface.
<!-- needs-research: verify the "broad adoption across model providers" claim against current MCP ecosystem — check the modelcontextprotocol.io site for the current list of implementations. -->

Four decisions on tools:

- **Which tools does the model have?** Read tools
  (fetch user data, search knowledge base, look
  up analytics), write tools (send email, update
  a record, execute a payment), navigation tools
  (browse a site, execute a workflow). Every
  additional tool expands what the model can do
  and expands the surface for failure.
- **What's the authorization model?** Some tools
  should be auto-invoked; some should require a
  user confirmation ("send this email?"); some
  should never be invoked without an admin
  action. This is a product decision, not an eng
  decision.
- **What's the failure semantics per tool?** A
  tool call can fail because the tool is down,
  because the arguments were wrong, because the
  service returned an error, or because the
  operation was intentionally rejected (e.g., a
  policy check). Each has a distinct UX.
- **What's the observability?** Every tool call
  should be logged with arguments, result,
  latency, and (for retrieval tools) the
  retrieved payload. This becomes the eval
  substrate.

For an agentic product — one that plans and
executes multi-step trajectories — the founding
CPO also reasons about:

- **The planning shape.** Does the agent produce
  a plan and execute it, or does it decide the
  next step at each step (ReAct-style)? The
  choice affects debuggability and steerability.
- **The trajectory bounds.** How many steps can
  the agent take before it stops? What happens
  if it exceeds the bound? What's the cost cap?
- **The intervention surface.** Where can the
  user (or a human reviewer) intervene? Every
  step? Only at final answer? On specific tool
  invocations?

Depth on agent orchestration —
planning, memory, multi-agent coordination,
error recovery — is
[agentic-ai-engineer-learning](https://github.com/ai-engineering-curriculum/agentic-ai-engineer-learning);
the CPO reasons about the *product surface* of
the agent, not the orchestrator implementation.

## Layer 4 — Evaluation

An LLM feature ships to production the same way any
feature does — but *"does it work"* is a distinct
question for an LLM feature because the outputs are
non-deterministic. A/B tests on stochastic outputs
are hard to power without a large N; the eval
regime replaces most A/B tests as the launch gate
for the specific feature quality question.

[mod-005 Lecture 6](../../mod-005-metrics-experimentation-and-ai-evals/lectures/06-eval-driven-decisions-for-llm-products.md)
teaches the eval discipline at CPO depth; this
lecture folds it in as a *layer of the AI system*
rather than treating it as a separate topic.

For a founding CPO reasoning about a system, the
eval layer questions are:

- **What is the labeled dataset?** Real user
  interactions, hand-curated examples, or a
  synthetic set? How many? Refreshed how often?
  A feature shipping without a labeled dataset
  is shipping on vibes.
- **What are the graders?** Human graders? LLM-
  as-judge (with what calibration)? A mix of
  rule-based checks and model checks? Hamel
  Husain's writing —
  [hamel.dev/blog/posts/evals](https://hamel.dev/blog/posts/evals/) —
  is the current practitioner reference.
- **What's the pass threshold?** The number below
  which we don't ship, and above which we do.
  A threshold you can lose on. If there is no
  such threshold, the eval is theatre.
- **How often does the eval run?** On every prompt
  change, on every model change, nightly, per
  release? Ideally on every meaningful change to
  the system.
- **Where does the eval live?** A hosted eval
  platform (Braintrust, Langfuse, OpenAI Evals),
  a self-hosted pipeline, a notebook. The choice
  affects cadence, sharing, and drift-tracking.

The CPO's PRD for an AI feature *always* names the
eval — dataset, graders, threshold, cadence. A PRD
that doesn't is under-specified in the sense of
[Lecture 2](02-technical-fluency-for-the-founding-cpo.md#fluency-5--catching-under-specified-prds).

## Layer 5 — Cost, latency, and the quality Pareto

The three axes of an AI feature's engineering
trade-off — cost, latency, quality — are almost
always in tension. Better quality often means a
larger model (more cost) or more steps (more
latency); lower cost often means a smaller model
(less quality) or aggressive caching (potentially
stale). The
[mod-005 Lecture 7](../../mod-005-metrics-experimentation-and-ai-evals/lectures/07-cost-latency-quality-pareto.md)
Pareto lecture is the vocabulary.

The founding-CPO reading of this layer:

- **The cost budget per invocation.** Concrete
  dollars per interaction. The mod-006 Lecture
  6 monetization model depends on this number
  being real and defensible.
- **The latency budget per invocation.** Concrete
  milliseconds or seconds. What does the user
  see while they wait? What does streaming
  buy? What's the user-visible failure if we
  miss the budget?
- **The quality target per invocation.** From
  the eval regime — the pass threshold above
  which we ship.
- **The Pareto position we chose and why.** The
  three axes force a choice. The PRD names it:
  *"We chose the Claude Haiku tier over Sonnet
  because we can meet the quality bar at
  significantly lower cost and half the latency;
  Sonnet is the fallback for the specific tickets
  Haiku misclassifies."*

The three-axis reasoning is the specific place
Chapter 3's engineering-scope-conflict discipline
(Lecture 5) shows up on AI features: the eng team
proposes model tier X, the CPO argues for tier Y
because of the cost implication for the pricing
model, the CTO argues for a hybrid because of the
latency budget. That conversation lands at the
Pareto question — *"where on the trade-off surface
do we want to sit for this specific feature?"* —
and the answer is a joint decision anchored in
the eval numbers and the cost model.

## The reading drill: how to read an AI system for the first time

When the founding CPO joins a team, one of the
first-week jobs is to read the AI system end-to-
end and produce a written map. The **read drill**
that
[Exercise 3](../exercises/exercise-03-ai-system-architecture-read-drill.md)
runs against is:

1. **Start at the user surface.** Pick one AI
   feature. Trace the request from "user clicks
   thing" through the frontend to the API to
   the AI orchestration layer.
2. **Identify the layers.** Which of the five
   above are present? Which are absent? An
   absent layer is a design decision (or an
   oversight).
3. **Name the contracts at each boundary.** What
   goes into each layer, what comes out. Where
   are the schemas? Where are they not?
4. **Catalogue the failure modes.** For each
   layer, list two to five ways it can go wrong
   and what the user-facing symptom is.
5. **Read the eval regime.** Is there a labeled
   dataset? Are there graders? What's the
   threshold? When did it last run?
6. **Read the cost / latency instrumentation.**
   Can you see cost per invocation? Latency
   percentiles? Where do you look?
7. **Produce the reading list.** The specific
   files, dashboards, docs, and PRs the CPO
   should keep on their desk to stay current
   on the system.

The output of this drill is a 3–5 page memo the
CPO takes into the first CPO/CEO 1:1 and into the
first eng-lead 1:1. It is the artifact that
demonstrates the CPO has read the system, and it
is the substrate for every AI-substrate PRD the
CPO writes over the next six months.

## What the CPO does personally

- **Reads the AI system end-to-end** in the first
  two weeks and produces the reading-drill memo.
- **Authors every AI-feature PRD** with all five
  layers named — context assembly, retrieval,
  tools, evals, cost / latency budget.
- **Owns the eval threshold** for launch decisions
  in coordination with the eng lead.
- **Owns the cost and latency budget** in
  coordination with the CTO.
- **Owns the UX of failure** at every layer.

## What the CPO consumes from the eng team

- **The retrieval implementation** — chunk
  strategy, embedding model, index shape,
  reranker choice — from the engineer who owns
  the retrieval layer, per
  [rag-engineer-learning](https://github.com/ai-engineering-curriculum/rag-engineer-learning).
- **The agent orchestration implementation** —
  planning, memory, error recovery — from the
  engineer who owns the agent layer, per
  [agentic-ai-engineer-learning](https://github.com/ai-engineering-curriculum/agentic-ai-engineer-learning).
- **The eval harness implementation** — dataset
  management, grader implementation, CI
  integration — from the engineer who owns
  the eval infrastructure, per
  [ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning).
- **Cost / latency observability** from the CTO
  or platform-engineering owner.
- **Model-provider price change alerts** — as
  in [mod-006 Lecture 6](../../mod-006-pricing-packaging-and-monetization/lectures/06-ai-product-monetization-models.md).

## Boundaries this lecture keeps

- **Retrieval implementation depth** — chunking,
  embedding-model choice, reranker design,
  vector-store internals, indexing pipelines —
  is [rag-engineer-learning](https://github.com/ai-engineering-curriculum/rag-engineer-learning).
- **Agent orchestration depth** — planner design,
  memory systems, multi-agent coordination,
  execution loops, error recovery — is
  [agentic-ai-engineer-learning](https://github.com/ai-engineering-curriculum/agentic-ai-engineer-learning).
- **Eval framework implementation depth** —
  grader design, dataset management,
  regression detection, LLM-as-judge
  calibration — is
  [ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning).
- **The eval-driven product decision regime** at
  CPO scope is
  [mod-005 Lecture 6](../../mod-005-metrics-experimentation-and-ai-evals/lectures/06-eval-driven-decisions-for-llm-products.md);
  this lecture uses that regime as a layer of
  the system.
- **The cost / latency / quality Pareto** at
  CPO scope is
  [mod-005 Lecture 7](../../mod-005-metrics-experimentation-and-ai-evals/lectures/07-cost-latency-quality-pareto.md);
  this lecture uses those axes as a layer of
  the system.
- **AI-substrate monetization** — cost-plus,
  value-based, outcome-based, credits — is
  [mod-006 Lecture 6](../../mod-006-pricing-packaging-and-monetization/lectures/06-ai-product-monetization-models.md).

## Takeaways

- **Reason about the AI system as five layers**:
  context, retrieval, tools / MCP, evaluation,
  cost / latency budget. The founding CPO owns
  the product decisions at each layer; the eng
  team owns the implementation.
- **Context engineering** is the discipline of
  choosing what goes into the model call. Four
  decisions: what information, in what order,
  cached or not, structured output or free
  text.
- **Retrieval** has four shapes (vector, BM25,
  hybrid, structured). The CPO reasons about
  the corpus, freshness, failure UX, and quality
  metrics; the retrieval engineer owns the
  tuning.
- **Tools and MCP** are how the model interacts
  with the world. The CPO reasons about the
  tool set, authorization model, failure
  semantics, and observability.
- **Evaluation** is how you know it works. The
  CPO owns the eval-threshold-you-can-lose-on
  discipline; the AI eval engineer owns the
  harness.
- **Cost / latency / quality Pareto** is the
  three-axis trade-off. The CPO reads the
  budgets, defends the pricing implication,
  and names the Pareto position chosen.
- **The read drill** is the first-week job:
  produce a 3–5 page memo that maps the system,
  names the contracts, catalogues failure modes,
  reads the eval regime, and produces the
  ongoing reading list.

Lecture 4 turns to **influence without authority**
— how the founding CPO leads sales, CS, marketing,
and design cross-functionally without a reporting
line.
