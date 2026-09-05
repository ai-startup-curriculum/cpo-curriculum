# Lecture 5 — Agentic UX iteration loops for AI-native product

## The setup

Every previous lecture in this module works whether your
product is AI-native or not. This one is where the AI-native
2026 postings — the fastest-growing 2026 competency in the
CPO market — put specific demands on the cadence that the
non-AI shape does not.

The specific claim: for a product with an LLM in the loop,
the *unit of product iteration* is not a feature or a
mockup. It is a **prompt / retrieval / tool-call
configuration** — an artifact that generates outputs whose
quality is *statistical* rather than deterministic, whose
cost and latency show up in the user's experience directly,
whose behavior is *tested by evaluation harnesses* rather
than by unit tests, and whose integrations are increasingly
mediated by **Anthropic's Model Context Protocol (MCP)**.

The CPO of a 3–8-engineer AI-native team owns this
iteration loop the way earlier-generation CPOs owned the
Figma mockup. This lecture teaches what the loop looks like
in a founding-CPO cadence, what the CPO does personally,
what the CPO consumes from engineering, and where the
boundary sits between product decisions and infrastructure
decisions.

## The four surfaces of the AI-substrate product

Before naming the iteration loop, name the four surfaces a
CPO iterates on. Every AI-substrate feature has these; the
CPO makes product decisions at each.

- **Prompts.** The instructions the model receives. System
  prompt, few-shot examples, response-format specifications,
  refusal / safety framing, tone. Owned by the CPO with the
  engineer's involvement. Simon Willison's running commentary
  at
  [simonwillison.net](https://simonwillison.net/) documents
  what a working practitioner practice looks like — prompts
  are *product artifacts*, versioned, evaluated, and edited
  by the person who understands the customer's outcome.
- **Retrieval.** What context the model gets before it
  generates. Which documents / chunks / prior conversations
  / tool outputs get injected. Retrieval configuration —
  chunk size, embedding model, top-k, re-ranking, freshness
  — is a product decision because it changes what the model
  *knows* about the user's situation.
- **Tool calls.** What the model can *do* — the tool schemas
  the model calls with structured arguments (search, fetch,
  create-record, send-email). The name, description,
  argument schema, and side-effect behavior of each tool are
  product-facing decisions. Anthropic's documentation on
  tool use is the canonical practitioner reference
  ([anthropic.com/docs/tool-use](https://docs.anthropic.com/en/docs/build-with-claude/tool-use)).
- **Cost and latency.** Because model outputs cost money per
  token and take time per response, both cost and latency
  are *user-facing surfaces* — either directly (a spinner,
  a "generating…" state, a token-limit affordance) or
  through the pricing model (mod-006). Cost per interaction
  and p50 / p95 latency are product-level KPIs, not
  infrastructure-only KPIs.

The four surfaces together define what the product actually
does. The CPO iterates on all four; the eng team makes them
easy to iterate on.

## The iteration loop, one version

The core AI-substrate iteration loop, in five steps, run
daily during active development and weekly during
maintenance:

1. **Observe the current output.** Pull a sample of real
   user interactions (or, pre-launch, a curated eval set)
   and read them. Not aggregate metrics — actual
   input/output pairs. Simon Willison's argument: *"You
   have to actually read the model's output to know if
   your product works"*
   ([Willison, "Prompt injection and jailbreaking are not
   the same thing," 2024, and many posts on eval
   practice](https://simonwillison.net/tags/evals/)).
2. **Identify a specific failure or gap.** A category —
   *"the model over-explains when the user asked a
   yes/no question"*, *"retrieval is pulling the wrong
   document when the query has 'compliance' in it"*, *"the
   tool call to create-record is being invoked when the
   user only asked a question"*. Named categories, not
   vague complaints.
3. **Change the artifact.** Edit the system prompt, adjust
   the retrieval config, refine the tool schema, or (as a
   last resort) escalate to a different model. Change one
   thing at a time.
4. **Evaluate the change.** Run an eval set that covers
   both the failure category and a *regression set* — a
   set of previously-known-good interactions that must not
   break. Hamel Husain's *"Your AI Product Needs Evals"*
   is the practitioner reference here
   ([Husain, hamel.dev/blog/posts/evals, May 2024](https://hamel.dev/blog/posts/evals/)).
5. **Ship the change and observe.** Deploy behind a flag
   or to a subset of traffic, watch a metric that would
   tell you the change is working (or a proxy the eval set
   under-covers), read production output again in a week.

The loop is *daily* during active development because each
step is small — a prompt edit and an eval sweep can be a
30-minute cycle. It is *weekly* during maintenance because
production traffic is what generates new failure categories
to iterate on.

The CPO is in the loop at steps 1, 2, and 3. The eng team
runs the harness at step 4 (with product-side eval design)
and the deploy pipeline at step 5. What the CPO does *not*
do is delegate step 1 — the reading of real output — to the
team, because delegating it collapses the loop back into an
opinion-based debate about what the model "should" be doing.

## Evals as a product-decision surface

Evaluations — automated tests that grade model output on a
set of inputs — are the AI-substrate equivalent of a
unit-test suite, with one critical difference: the *pass
criteria* are product decisions, not engineering decisions.
Choosing what to eval, how to grade it, and what threshold
counts as "acceptable" is CPO work.

Hamel Husain's argument, worth quoting the shape of: the
number of teams that have built an LLM product without a
functional eval regime is high, and the number of teams that
subsequently discovered they were shipping regressions in
the dark is exactly the same
([Husain, hamel.dev/blog/posts/evals, May 2024, and the
follow-up "Field Notes on LLM
Evaluation," 2024](https://hamel.dev/blog/posts/evals/)).
For a founding CPO, four eval-regime decisions matter:

- **What are we evaluating for?** Correctness, tone,
  format adherence, refusal behavior, latency,
  hallucination rate, tool-selection accuracy, retrieval
  precision. Not all at once — pick the failure modes that
  matter for *this* product surface and eval those. The
  CPO chooses.
- **How is grading done?** Human labeling (slow,
  expensive, gold-standard); LLM-as-judge (fast, cheap,
  requires calibration); rule-based (only for narrow,
  well-defined outputs). The right answer is usually a
  mix; the CPO chooses which grading approach applies to
  which eval.
- **What is the eval set?** A curated set of inputs that
  cover both the *happy path* (what most users do) and
  the *long tail* (rare-but-important inputs the model
  must handle well). Curating the eval set is a discovery
  activity — customer conversations from Lecture 1 are
  your best source of eval inputs.
- **What is the threshold?** *"The model's response
  matches the reference on ≥80% of the top-100 accounts'
  most-frequent queries, with no regression on the
  refusal-behavior eval set"* is a product threshold. The
  CPO writes it; the eng team measures against it.

Note: mod-005 is where the full eval-driven-decision regime
lives — LLM-as-judge calibration, MDE sizing for
A/B experiments on prompts, cost/latency/quality Pareto
analysis. This lecture is only about how evals *land inside
the weekly cadence* as a product-decision surface. The eval
methodology itself is mod-005's job.

## Cost and latency as user-facing surface

For a non-AI product, cost is a business metric and latency
is an SRE metric. For an AI-substrate product, both are
user-facing. Three specific reasons:

- **Cost per interaction is often visible in pricing.** If
  the model call costs $0.05 and the user gets it for
  "free" inside a $19/month plan, the CPO has an
  economics problem the pricing model has to solve
  (mod-006). If the cost is $0.02 and the user pays per
  request, the CPO has a UX problem — how much is the
  user paying per click, and does the product make that
  legible?
- **Latency shapes the interaction.** A response that
  takes 8 seconds is a different product than one that
  takes 800ms. Streaming, "thinking" indicators,
  intermediate outputs (partial answers), and background
  execution are all product design decisions that respond
  to model latency.
- **Both compound with agentic loops.** An agentic
  workflow that calls the model six times to complete a
  task costs six times the tokens and takes six times as
  long. The CPO owns the decision about whether that
  cost / latency is worth the outcome.

Anthropic's public documentation on their model tier
pricing, context window sizes, and streaming behavior is
the practitioner reference for what the trade-off surface
looks like at model level
([anthropic.com/pricing](https://www.anthropic.com/pricing)
and the API docs at
[docs.anthropic.com](https://docs.anthropic.com/)).

Practical implication for the cadence: the six-pager
(Lecture 3) for an AI-substrate bet should name a
**cost / latency budget per interaction** and an
**eval-set threshold** as first-class parts of the
pre-registered signals. A bet that ships and misses either
gets treated the same as a bet that missed its outcome
metric.

## MCP as an integration lever

Anthropic's **Model Context Protocol (MCP)**, announced in
November 2024, is an open standard for how AI applications
connect to external tools, data sources, and prompt
templates. The core primitive: an MCP *server* exposes a
set of tools, resources, and prompts; an MCP *client* (an
AI application) can discover and invoke them at inference
time. The specification is at
[modelcontextprotocol.io/specification](https://modelcontextprotocol.io/specification);
the introductory post is at
[anthropic.com/news/model-context-protocol](https://www.anthropic.com/news/model-context-protocol).

For a founding CPO, MCP matters for two reasons:

- **It changes the build-vs-integrate decision for AI-
  substrate integrations.** Before MCP, connecting your
  product's AI to (say) a customer's Salesforce or GitHub
  meant custom integration work per connector. With MCP,
  if a customer's system exposes an MCP server (or you
  can point one at it), your product can consume the
  connector as a first-class tool without you writing
  new integration code. This changes the roadmap math on
  a class of features that used to be individually
  expensive.
- **It changes the shape of "extensibility" as a product
  surface.** If your product exposes an MCP server,
  third-party AI clients (Claude Desktop, Cursor, other
  MCP-compatible tools) can use your product's data and
  actions inside their own AI workflows. This is a
  platform-shape decision (mod-003 Lecture 4) that shows
  up disguised as an implementation choice; the CPO
  should recognize it as a strategy decision, not an
  engineering one.

Concretely, three CPO-scope decisions MCP surfaces:

- **Do we consume MCP?** If the customer ecosystem
  already has MCP servers for the systems we would
  otherwise integrate with, consuming those is often
  cheaper than building bespoke integrations. This is
  a *sequencing* decision on the roadmap.
- **Do we expose an MCP server?** If exposing our
  product's core data and actions through MCP makes us
  a more valuable node in a broader AI ecosystem, the
  strategic question is whether we *want* that (are we
  aggregating value, or ceding it to the AI client that
  wraps us?).
- **What is the security / permissions model?** MCP
  tools run with permissions; a tool that can create,
  modify, or delete data needs an authorization model
  the customer trusts. This is a product decision (what
  affordances the customer gets to review or approve
  tool calls) as much as an engineering decision.

<!-- needs-research: verify the MCP specification's current
tool-authorization primitives and the client-side approval
UX pattern Anthropic recommends; the spec is versioned and
the recommendation may have shifted since Nov 2024. -->

Simon Willison has written extensively about MCP in
practice, including its trade-offs; his running commentary
is the best practitioner reference for what MCP looks like
at the working-product level
([simonwillison.net/tags/mcp](https://simonwillison.net/tags/mcp/)).

## The agentic-UX iteration loop, extended

For products that use *agents* — multi-step reasoning loops
where the model plans, calls tools, observes results, and
plans again — the iteration loop from earlier gets one
extra step: **the trajectory review**.

An agentic interaction produces a *trajectory* — the
sequence of tool calls, intermediate reasoning, and
observations that led to the final output. Reading the
trajectory (not just the final output) is where the CPO
finds the failure modes specific to agentic UX:

- **Loops the agent got stuck in.** Called the same tool
  three times with slight variations because the first
  two responses were unclear.
- **Tools the agent should have used but didn't.** The
  right answer was available but the tool description
  didn't make it discoverable.
- **Costly detours.** The agent read six documents to
  answer a question one document would have covered.
- **Silent failures.** A tool call failed, the agent
  didn't notice, and the final output confabulated.

The CPO reads a sample of trajectories weekly. What they
find becomes the next iteration on prompts (better
planning instructions), tool schemas (better descriptions),
or retrieval (better first-pass results). The tools your
eng team uses for trajectory inspection are Langfuse,
Braintrust, or a home-built logging pipeline; the CPO's
job is to be in the tool, weekly.

<!-- needs-research: verify that Langfuse and Braintrust
remain the most-referenced open-source and commercial
trajectory-observability tools; if the market has shifted
or new entrants dominate, substitute. -->

## What lands in the cadence

Concretely, three additions to the Lecture 1 weekly rhythm
for AI-substrate teams:

- **Daily eval sweep (during active development).** The
  team runs the current eval set against the current
  prompt / retrieval / tool-call configuration nightly.
  The morning stand-up starts with a look at overnight
  eval results and a decision on whether to iterate or
  ship. The CPO scans the sweep results; the eng team
  drives the harness.
- **Weekly trajectory review (in maintenance).** The CPO
  reads a sample of 20–30 production trajectories per
  week. Findings feed the Thursday sync (Lecture 1).
- **Cost / latency dashboard as a first-class product
  KPI.** Not just in the SRE stack — visible on the
  product dashboard, tracked in weekly ship reviews. A
  ship that regressed cost or latency by 20% is a
  product regression, not just an infra one.

All three are additive to the dual-track rhythm; none
replaces it.

## The CPO's role, explicitly

- **Prompts:** author or edit personally. Willison-style
  discipline: read output, iterate on prompt, re-read.
- **Retrieval configuration:** decide the product
  surface (what corpus is retrieved from, how freshness
  is handled, when retrieval is triggered). Delegate the
  chunking / embedding / re-ranking math to the eng
  team.
- **Tool schemas:** author the tool names and
  descriptions personally (they are microcopy the model
  reads); consume the argument-schema shape from the
  eng team.
- **Eval regime:** author what to eval for and the
  threshold; consume the harness itself and the grading
  infrastructure from eng.
- **Cost / latency budget:** author personally as part
  of the six-pager (Lecture 3); consume actual measured
  cost / latency from the eng team.
- **MCP posture:** author the consume-vs-expose
  strategic decision; consume the specific protocol
  implementation details from eng.
- **Trajectory review:** run personally, weekly.

## What the CPO consumes from engineering

- The eval harness (infrastructure, model runners,
  grading pipeline).
- The retrieval / RAG infrastructure (vector store,
  embedding pipeline, re-ranking).
- The tool-execution runtime and its security /
  permissions model.
- The observability tooling (trajectory logs, cost /
  latency metrics, model-call error rates).
- The model-provider integrations (Anthropic, OpenAI,
  open-model runtime).
- MCP client / server implementations.

None of these are CPO-authored. All of them are things
the CPO must be able to *ask for* by name, understand at
a working level, and change the product decisions
around. The vocabulary gap here is the single most-
common cause of a founding CPO being sidelined from
AI-native decisions; the antidote is to *personally* run
one full iteration loop, end to end, on one narrow
feature, so the vocabulary becomes real.

## Boundaries this lecture keeps

- **Eval methodology at depth** — LLM-as-judge
  calibration, MDE sizing for prompt A/B experiments,
  cost / quality / latency Pareto analysis — is
  [mod-005](../../mod-005-metrics-experimentation-and-ai-evals/README.md).
  This lecture is only about how evals *land in the
  weekly cadence*.
- **AI-substrate pricing and packaging** — how cost
  per interaction becomes user pricing — is
  [mod-006](../../mod-006-pricing-packaging-and-monetization/README.md).
- **The AI-engineering craft under the surface** —
  RAG systems, agent frameworks, model selection,
  fine-tuning — is out of scope for a CPO curriculum
  and covered at owner-scope in
  [ai-eval-engineer](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning),
  [rag-engineer](https://github.com/ai-engineering-curriculum/rag-engineer-learning),
  and
  [agentic-ai-engineer](https://github.com/ai-engineering-curriculum/agentic-ai-engineer-learning).
  The CPO consumes; the AI engineer authors.
- **General LLM safety, alignment, and governance** is
  out of scope; the AI-governance curricula cover it.
  This lecture teaches the *product-cadence* side of
  AI-substrate iteration.
- **Model-provider selection and vendor negotiation** is
  a founder-CEO / CTO decision the CPO consumes.

## Takeaways

- For an AI-native product, the unit of iteration is a
  **prompt / retrieval / tool-call configuration**, not a
  feature. The CPO iterates on all four surfaces
  personally: prompts, retrieval, tool schemas, cost /
  latency.
- The five-step loop — observe output, name the failure,
  change one thing, evaluate, ship — runs daily in
  active development and weekly in maintenance. Reading
  actual output is non-delegable.
- **Evals are a product-decision surface**: what to eval
  for, how to grade, what set, what threshold — all CPO
  calls. Mod-005 owns the methodology; this lecture
  owns the cadence integration.
- **Cost and latency are user-facing.** Both belong in
  the six-pager's pre-registered signals; both are
  first-class product KPIs, not infra-only KPIs.
- **MCP** changes the build-vs-integrate math and the
  extensibility posture; the CPO owns the strategic
  choice (consume, expose, security model) and consumes
  the protocol implementation from eng.
- Agentic products need a **weekly trajectory review**;
  what the CPO finds feeds the next iteration on
  prompts, tools, or retrieval.
- The vocabulary gap between CPO and eng on AI substrate
  is the most common way founding CPOs get sidelined;
  the antidote is running one full iteration loop
  personally on one narrow feature.

Lecture 6 closes the module with the anti-patterns the
whole cadence has to be designed against — planning
theatre, PRD gestation, design-debt-in-review, spec-then-
handoff, the "agile" waterfall — and the specific
counter-move each requires.
