# Exercise 3 — AI system architecture read drill

**Time:** ~3 hours. **Deliverable:** one 3–5 page
system-architecture memo mapping a real AI-substrate
product across the five layers from
[Lecture 3](../lectures/03-ai-system-architecture-for-the-founding-cpo.md),
one labelled failure-mode catalogue, one standing
reading list, and a reviewer's memo — against a real
or open-source AI-native codebase.

## Purpose

Produce the first-week artifact a founding CPO
delivers when they join an AI-native company: a
written system map that demonstrates they have *read
the system end-to-end*, named the contracts at each
layer, catalogued the failure modes, and surfaced
the specific questions the CPO will carry into the
first eng-lead and CPO / CEO 1:1s.

The read drill from
[Lecture 3 §"The reading drill"](../lectures/03-ai-system-architecture-for-the-founding-cpo.md#the-reading-drill-how-to-read-an-ai-system-for-the-first-time)
is the exact shape. The memo is the substrate for
every AI-feature PRD the CPO writes over the next
six months, so the point is not to produce a tidy
architecture diagram — the point is to produce the
*working map* the CPO will reference when the next
scope conversation lands.

## Choosing the system

Pick one AI-substrate system you can read end-to-
end. In order of preference:

1. **The system at the company you're currently (or
   about to be) the CPO of.** Real stakes; the memo
   becomes your actual first-week artifact.
2. **A system you've worked on recently.** Your
   last team's agent, retrieval, or eval pipeline.
   Fast because you already know where files live.
3. **A credible open-source reference.** Pick one
   whose shape maps to the kind of company you'd
   join. Workable candidates: a RAG reference app
   (Vercel's AI SDK examples, LangChain / LlamaIndex
   templates), an agent reference (OpenAI Agents SDK
   examples, Anthropic's `claude-code` tooling or
   MCP server examples at
   [github.com/modelcontextprotocol](https://github.com/modelcontextprotocol)),
   or an eval reference (OpenAI Evals, Braintrust /
   Langfuse starter projects). Pick *one*, not three.

Whichever you pick, pick one **customer-facing
feature** inside the system to trace end-to-end.
Not the whole system; a single feature's trajectory
from user click to model response and back. The
Lecture 3 drill is explicit about this: start at
the user surface and trace the request.

If you have to go synthetic, write a one-paragraph
system description up front: product shape, model
provider(s), approximate scale, the one feature
you'll trace, your source material (repo URL,
docs, dashboards you can see). Everything downstream
anchors to it.

## What the artifact bundle must contain

Roughly 3–5 pages for the main memo, plus a one-
page failure-mode catalogue and a one-page reading
list.

### 1. The system map (2–3 pages)

Walk the five layers from
[Lecture 3 §"The five layers to reason about"](../lectures/03-ai-system-architecture-for-the-founding-cpo.md#the-five-layers-to-reason-about).
For each layer:

- **Layer 1 — Context.** Name what goes into the
  model call for the feature you traced: user
  input, prior conversation state, retrieved
  documents, user-specific data, tool
  descriptions, output format instructions,
  guardrails. Where does each piece come from in
  the code? In what order? Is prompt caching
  used? Structured output or free text? Cite
  specific files or endpoints — the Lecture 3
  §"Context engineering" four decisions are the
  rubric.
- **Layer 2 — Retrieval.** Name the retrieval
  shape (vector, BM25, hybrid, structured, none).
  Where does the corpus come from, how fresh is
  it, what's the empty-retrieval UX, what quality
  metric (if any) is tracked. If retrieval is
  absent, say so explicitly — an absent layer is
  a design decision per Lecture 3.
- **Layer 3 — Tools / MCP.** List every tool the
  model has access to in this feature, grouped
  by read / write / navigation. For each, name
  the authorization model (auto-invoke, user-
  confirm, admin-only), the failure semantics,
  and the observability. If the system is
  agentic, name the planning shape (ReAct vs.
  plan-and-execute), trajectory bounds, and
  intervention surface per Lecture 3 §"Tools
  and MCP."
- **Layer 4 — Evaluation.** Name the labeled
  dataset (size, source, refresh cadence),
  graders (human / LLM-as-judge / rules), pass
  threshold, cadence, and where the eval lives
  (hosted platform / self-hosted / notebook).
  If there is no eval regime, name it — a
  shipped AI feature without an eval is
  shipping on vibes per Lecture 3 §"Layer 4."
- **Layer 5 — Cost / latency / quality
  Pareto.** Name the cost budget per invocation
  (actual or estimated), latency budget, quality
  target (from the eval), and the Pareto position
  the team chose with the reasoning. If any of
  the three is uninstrumented, say so and name
  where you'd expect the instrumentation to
  live.

For each layer, also name:

- **The contract at the boundary.** What goes
  into the layer, what comes out. Where the
  schemas are (or aren't).
- **One or two product decisions the CPO owns at
  this layer.** From Lecture 3's "what the CPO
  does personally" section — the specific
  decisions that are not CTO / eng-lead calls.

### 2. The failure-mode catalogue (1 page)

For each of the five layers, name two to five
specific ways it can fail *in this system*, and
the user-facing symptom. Not generic failure
modes; failure modes tied to the specific
retrieval corpus, tool set, and eval regime you
mapped above. Examples of shape:

- *Layer 2 — Retrieval:* "If the knowledge-base
  index is stale (indexing lags writes by >5
  minutes), queries about just-uploaded documents
  return 'I don't have that information' even
  though the document exists. User-facing: the
  'I just uploaded this!' support ticket."
- *Layer 3 — Tools:* "If the `send_email` tool
  succeeds but the model doesn't log the tool
  result, the user asks 'did it send?' and the
  model hallucinates yes/no. User-facing: a
  trust-destroying 'the AI lied to me' thread."

The catalogue is the substrate for the launch-
readiness checklist in Exercise 6 and for the
PRD-under-specification check from Exercise 2.

### 3. The standing reading list (1 page)

The specific set of files, dashboards, docs, and
PRs the CPO keeps on their desk to stay current
on the system. Per Lecture 3 §"The reading drill"
step 7. For each item:

- **What it is** (one line).
- **Where it lives** (link, file path, or
  dashboard URL).
- **How often you'd read it** (daily, weekly,
  on-change).
- **Why it's on the list** (which decision it
  informs).

Example shape:

- `apps/web/src/features/chat/orchestrator.ts` —
  the agent entry point. Read on-change. Catches
  context-assembly or tool-contract changes
  before they ship.
- Braintrust eval dashboard for the chat quality
  regime. Read weekly. Catches drift against
  the pass threshold.
- Model-provider pricing page (Anthropic / OpenAI
  / Google). Read monthly. Catches rate-card
  changes that affect the mod-006 cost model.

### 4. The three carry-in questions (half page)

Specifically for the first eng-lead 1:1 and the
first CPO / CEO 1:1 after the drill. Three
questions each, in priority order. Each question
should be answerable with evidence (not opinion)
and should surface a decision the CPO needs
clarity on.

Examples of shape:

- *For the eng lead:* "The retrieval layer uses
  BM25 only. Was that an intentional choice over
  hybrid, and what's the quality-metric reason?"
- *For the CEO:* "The current Pareto position
  sits on Claude Sonnet at ~$0.04 per
  interaction. The mod-006 cost model targets
  $0.015. Which do we move — the model tier, the
  pricing, or the quality bar?"

## Starter guidance

- **Start at the user surface.** The Lecture 3
  drill is explicit: pick one feature, trace the
  request. A top-down architecture tour is more
  tempting and much less useful — you learn more
  from one feature traced to the ground than from
  five features surveyed from above.
- **Name the absent layers.** If the system has
  no eval regime, no cost instrumentation, no
  retrieval, say so by name. An absent layer is
  a product observation the CPO owns.
- **Cite the code and the docs by location.** The
  memo is only useful if the reader (your future
  self, the eng lead) can jump to the file. "The
  context assembly lives in
  `apps/web/src/ai/context.ts:assembleContext`"
  beats "the context assembly logic."
- **Read the MCP spec once if the system uses
  tools.** [modelcontextprotocol.io](https://modelcontextprotocol.io/)
  — half an hour of reading saves many hours of
  conversation about tool contracts. Lecture 3
  calls this out specifically.
- **Pull in mod-005 vocabulary.** Lecture 3
  defers eval and cost/latency depth to
  [mod-005 Lecture 6](../../mod-005-metrics-experimentation-and-ai-evals/lectures/06-eval-driven-decisions-for-llm-products.md)
  and
  [mod-005 Lecture 7](../../mod-005-metrics-experimentation-and-ai-evals/lectures/07-cost-latency-quality-pareto.md).
  Use their vocabulary (pass-threshold-you-can-
  lose-on, Pareto position) in the Layer 4 and
  Layer 5 sections.
- **Don't try to design the fix.** The memo is
  diagnostic, not prescriptive. "Retrieval has
  no empty-state UX; see Layer 2" is enough;
  "we should add a card component with X copy"
  belongs in a later PRD.

## The reviewer's memo

Half a page, written after the artifact bundle.
Answer:

- **Which layer is the system weakest at?** Why?
  What specifically would you want to change in
  the next 90 days — and is that a product-side
  change (PRD, UX of failure, eval threshold) or
  an eng-side change (retrieval tuning, agent
  orchestration, cost instrumentation) you'd
  defer to [rag-engineer-learning](https://github.com/ai-engineering-curriculum/rag-engineer-learning),
  [agentic-ai-engineer-learning](https://github.com/ai-engineering-curriculum/agentic-ai-engineer-learning),
  or [ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning)?
- **Which decision from the Lecture 3 "what the
  CPO owns" list is currently underowned?** For
  example, if the UX of failure at retrieval is
  not product-owned, that's a layer-ownership
  gap you'd name in a first-week memo.
- **What did reading the system teach you that
  the PRD you'd write pre-reading would have
  missed?** The under-specification diagnostic
  from Lecture 2 Fluency 5 applied in reverse —
  what would the PRD-without-reading have skipped?
- **If you had 15 minutes with the eng lead,
  which one question from your carry-in list
  would you lead with?** Why that one first?

## Acceptance criteria

- System map covers all five layers with
  contracts, product decisions the CPO owns, and
  specific file / dashboard citations. Absent
  layers are named explicitly.
- Failure-mode catalogue has 2–5 failure modes
  per layer tied to the specific system, with
  the user-facing symptom named.
- Standing reading list has ≥8 items, each with
  what / where / cadence / why.
- Carry-in questions list has three questions
  for the eng lead and three for the CEO, each
  answerable with evidence rather than opinion.
- Every reference to
  [Lecture 3](../lectures/03-ai-system-architecture-for-the-founding-cpo.md)
  cites the specific layer or section rather
  than the lecture as a whole.
- The feature traced is a real customer-facing
  feature, not a hypothetical.
- Reviewer's memo answers all four prompts.

## Common failure modes

- **Top-down architecture tour.** The memo reads
  as "here is the system from above" rather than
  "here is one feature from end to end." Fix:
  pick one user interaction and trace it.
- **Opinionated review.** The memo prescribes
  fixes rather than mapping the system. Fix:
  keep the diagnostic / prescriptive split
  clean; prescriptions go in a later PRD.
- **No citations.** The memo makes claims about
  the system without pointing to the file,
  endpoint, dashboard, or doc. Fix: every claim
  gets a location.
- **Jargon without the eng-side depth.** The
  memo uses retrieval / agent / eval vocabulary
  loosely. Fix: use the Lecture 3 vocabulary
  precisely — hybrid retrieval vs. vector-only,
  ReAct vs. plan-and-execute, LLM-as-judge vs.
  rule-based grader.
- **Missing failure modes on absent layers.** No
  eval regime? That IS a failure mode; name it.
- **No reading list.** The memo describes the
  system but doesn't name the three to twelve
  things the CPO will keep reading. The reading
  list is what makes the memo *standing*
  rather than *one-time*.
- **Carry-in questions are opinion-shaped.**
  "Should we switch to hybrid retrieval?" is a
  position; "what quality-metric evidence drove
  the BM25-only choice?" is a question. The
  Lecture 4 influence craft starts in the
  question wording.

## Source alignment

The five-layer framing derives from
[Lecture 3](../lectures/03-ai-system-architecture-for-the-founding-cpo.md).
The MCP vocabulary comes from the official
specification at
[modelcontextprotocol.io](https://modelcontextprotocol.io/)
and the specification repository at
[github.com/modelcontextprotocol](https://github.com/modelcontextprotocol).
The practitioner reading-depth for this layer is
Simon Willison's writing at
[simonwillison.net](https://simonwillison.net/)
and Hamel Husain's evals material at
[hamel.dev/blog/posts/evals](https://hamel.dev/blog/posts/evals/).
The eval and cost / latency depth this exercise
reads for is
[mod-005 Lecture 6](../../mod-005-metrics-experimentation-and-ai-evals/lectures/06-eval-driven-decisions-for-llm-products.md)
and
[mod-005 Lecture 7](../../mod-005-metrics-experimentation-and-ai-evals/lectures/07-cost-latency-quality-pareto.md).
The engineering depth this exercise explicitly
defers to is
[rag-engineer-learning](https://github.com/ai-engineering-curriculum/rag-engineer-learning),
[agentic-ai-engineer-learning](https://github.com/ai-engineering-curriculum/agentic-ai-engineer-learning),
and
[ai-eval-engineer-learning](https://github.com/ai-engineering-curriculum/ai-eval-engineer-learning).
