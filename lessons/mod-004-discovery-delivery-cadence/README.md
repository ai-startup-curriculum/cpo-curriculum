# mod-004 — Discovery / Delivery Cadence: Ship Weekly, Sweat Microcopy, Own the Pixel

> The founding CPO's fourth job — after finding pull (mod-001),
> ranking the queue (mod-002), and authoring the strategy that
> the roadmap makes concrete (mod-003) — is running the **weekly
> operating rhythm** that turns a roadmap into a stream of ships.
> This is the module where the CPO stops writing documents and
> starts moving pixels.

## Why this module exists

At the 3–8-engineer scale a founding CPO actually operates in,
what kills product velocity is not the roadmap. It is the
*rhythm* the roadmap runs inside. Ask a first-time founding CPO
how their team ships and you will hear one of three answers: a
Jira board with a two-week sprint boundary that nobody actually
observes; a Notion doc titled *Q3 Roadmap* that has not been
edited in a month; or "we do Shape Up," said with the confident
manner of someone who has read the book but not the retrospective
in Basecamp's second one.

None of these is a cadence. A cadence is a *repeating weekly
shape* — what happens on which day, what artifact each ritual
produces, and how discovery findings become delivery decisions
without a hand-off. Marty Cagan calls the shape *dual-track*:
discovery runs continuously *alongside* delivery, not as a phase
that precedes it. Teresa Torres calls the tempo *weekly*:
touchpoints with customers happen every week, not once a
quarter. Ryan Singer, writing from Basecamp, calls the delivery-
side operating model *Shape Up*: six-week appetites shaped by a
small group, then handed to a team with authority to make the
scope call.

This module teaches the shape that survives at pre-seed / seed
scale, the two delivery-side operating models that work at 3–8
engineers, the PRD form that stops PRDs from becoming a
gestation ritual, the design taste the market now expects the
CPO to bring personally, the AI/LLM-native iteration loop the
2026 postings ask for by name, and the ship-velocity anti-
patterns you have to design *out* of the rhythm — not diagnose
after the fact.

## Learning outcomes

By the end of this module you can:

1. **Design** a dual-track discovery/delivery cadence — Cagan's
   *Empowered* / *Inspired* model, Torres's continuous-discovery
   weekly rhythm — where discovery runs continuously alongside
   delivery rather than as a separate "phase" that precedes it.
2. **Choose and run** either a Basecamp-style Shape Up cycle
   (Ryan Singer's six-week appetite / cool-down shape) or a
   weekly-ship kanban at the 3–8-engineer scale, knowing the
   failure modes of each and the size / stability / discovery-
   maturity signals that push you toward one or the other.
3. **Author** PRDs in the Amazon 6-pager / working-backwards
   press-release shape — a narrative document that starts with
   the customer outcome and only then names the mechanism —
   rather than a spec document that a design and engineering
   team receive as a hand-off.
4. **Sweat the microcopy and own the pixel** — ship Figma
   mockups alongside engineering, edit strings personally,
   maintain a live changelog — the CPO-as-IC-designer
   expectation that pre-seed / seed AI-native postings now
   assume by default.
5. **Fold in AI/LLM-native discovery/delivery** — agentic UX
   iteration loops, prompt / retrieval / tool-call
   experimentation as a product primitive, cost / latency as a
   user-facing surface, and MCP as an integration lever —
   grounded in Anthropic's Model Context Protocol spec and the
   practitioner writing of Simon Willison and Hamel Husain.
6. **Diagnose and design out** the ship-velocity anti-patterns
   most likely to strangle a founding-CPO cadence — planning
   theatre, PRD gestation, design-debt-in-review, spec-then-
   hand-off, the "agile" waterfall — and know the counter-move
   the cadence itself has to contain.
7. **Consume** the engineering-side delivery-cadence craft at
   the level-25 boundary owned by
   [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)
   — DORA metrics as a measurement discipline, on-call
   rotation, incident response — and know what the CPO
   consumes vs. what the CTO authors.

## Prerequisites

- [mod-001](../mod-001-customer-discovery-to-pmf/README.md) —
  discovery loops, opportunity solution trees, JTBD interviews.
  The *discovery* half of dual-track is the mod-001 loop
  running weekly; without it the cadence collapses to a
  delivery-only rhythm.
- [mod-002](../mod-002-opportunity-assessment-and-prioritization/README.md) —
  opportunity-assessment authoring, scoring, kill discipline.
  Shape Up's *shaping* step and the six-pager's *narrative*
  section both assume a well-authored opportunity underneath.
- [mod-003](../mod-003-roadmap-outcomes-and-strategy/README.md) —
  outcomes-based roadmap, product strategy, OKRs at CPO scope.
  A cadence is the *tempo* the roadmap runs at; the roadmap
  supplies the outcomes the cadence moves.
- One product you can name concretely, with a team you can
  either observe or plausibly imagine (3–8 engineers, one
  designer or a CPO doing design, one or two founders in the
  building). If you don't have one, pick a synthetic and defend
  its shape the same way mod-002 and mod-003 asked you to.
- A basic willingness to open Figma, edit a string, and read a
  Git diff. The "own the pixel" lecture and exercises assume
  you will do the work in the tools your team uses — not
  produce a document *about* the pixel.

## Syllabus

| # | Piece | Type | Est. time |
|---|---|---|---|
| 1 | [Dual-track discovery/delivery: the Cagan/Torres weekly rhythm](lectures/01-dual-track-discovery-delivery-cadence.md) | Lecture | 45 min |
| 2 | [Shape Up vs weekly-ship kanban at the 3–8-engineer scale](lectures/02-shape-up-vs-weekly-kanban.md) | Lecture | 60 min |
| 3 | [PRDs in the Amazon 6-pager / working-backwards shape](lectures/03-prd-in-amazon-6-pager-shape.md) | Lecture | 45 min |
| 4 | [Own the pixel: Figma, microcopy, and the CPO as IC designer](lectures/04-own-the-pixel-figma-and-microcopy.md) | Lecture | 45 min |
| 5 | [Agentic UX iteration loops for AI-native product](lectures/05-agentic-ux-iteration-loops.md) | Lecture | 60 min |
| 6 | [Ship-velocity anti-patterns and how to design them out](lectures/06-ship-velocity-anti-patterns.md) | Lecture | 45 min |
| 1 | [Dual-track cadence authoring for one team](exercises/exercise-01-dual-track-cadence-authoring-for-one-team.md) | Exercise | 3 hrs |
| 2 | [Shape Up vs weekly kanban choice drill](exercises/exercise-02-shape-up-vs-weekly-kanban-choice-drill.md) | Exercise | 2 hrs |
| 3 | [PRD in Amazon 6-pager shape](exercises/exercise-03-prd-in-amazon-6-pager-shape.md) | Exercise | 3 hrs |
| 4 | [Figma mockup and microcopy drill](exercises/exercise-04-figma-mockup-and-microcopy-drill.md) | Exercise | 3 hrs |
| 5 | [Agentic UX iteration loop drill](exercises/exercise-05-agentic-ux-iteration-loop-drill.md) | Exercise | 3 hrs |
| 6 | [Ship-velocity anti-pattern diagnosis](exercises/exercise-06-ship-velocity-anti-pattern-diagnosis.md) | Exercise | 2 hrs |
| R | [Resources — books, essays, and primary sources](resources.md) | Reference | — |

## How to work this module

Read the lectures in order. Lecture 1 sets the dual-track
shape the rest of the module operates inside; Lecture 2 picks
the delivery-side operating model and forces you to name why;
Lecture 3 changes the *artifact* the cadence produces (from
spec-shaped PRDs to narrative-shaped six-pagers); Lecture 4
puts the CPO's hands on the pixel and the string; Lecture 5
folds in the AI-native iteration loop that the market's
fastest-growing 2026 competency assumes you can run; and
Lecture 6 closes on the anti-patterns the whole cadence has to
design against.

Do the exercises against a real team. The failure modes this
module teaches — planning meetings that produce a decision no
customer ever sees, PRDs that die in review, hand-offs that
absorb a designer's day into an eng slack thread, "we'll fix
the copy later" microcopy debt, evals with no user-visible
consequence, retros that observe the same anti-pattern for the
third quarter running — are almost invisible in toy cases. If
you must use a synthetic, keep the team size, discovery
maturity, and product surface concrete.

Exercises 1 → 6 build on each other. Exercise 1 authors the
dual-track rhythm; Exercise 2 picks the delivery operating
model that rhythm runs inside; Exercise 3 writes a six-pager
against that model's first cycle; Exercise 4 puts the pixel and
the microcopy for that same cycle into Figma; Exercise 5 folds
in an agentic-UX iteration loop that changes how a slice of the
product gets shipped; and Exercise 6 forces the whole cadence
through an anti-pattern diagnosis so you feel where the
discipline pinches.

## Deliverables

- One dual-track cadence artifact — weekly calendar, discovery
  rhythm, delivery rhythm, hand-off boundary — for a real (or
  plausible synthetic) team
  ([Exercise 1](exercises/exercise-01-dual-track-cadence-authoring-for-one-team.md)).
- One operating-model choice memo defending Shape Up vs weekly
  kanban for the same team, with named failure modes and the
  signals you'd watch for a re-choice
  ([Exercise 2](exercises/exercise-02-shape-up-vs-weekly-kanban-choice-drill.md)).
- One PRD in Amazon 6-pager shape — press release, tenets,
  FAQ, mechanism, appendix — for a real bet
  ([Exercise 3](exercises/exercise-03-prd-in-amazon-6-pager-shape.md)).
- One Figma mockup and microcopy pass on a live surface of your
  product, with a reviewer's memo on what the CPO's edits
  changed vs the engineer / designer's first draft
  ([Exercise 4](exercises/exercise-04-figma-mockup-and-microcopy-drill.md)).
- One agentic-UX iteration-loop design for one product slice,
  naming the prompt / retrieval / tool-call surface, the eval
  regime, and the cost / latency budget that becomes user-
  facing
  ([Exercise 5](exercises/exercise-05-agentic-ux-iteration-loop-drill.md)).
- One ship-velocity anti-pattern diagnosis of a real team,
  with a designed-out counter-move for each anti-pattern named
  ([Exercise 6](exercises/exercise-06-ship-velocity-anti-pattern-diagnosis.md)).

## Boundaries this module keeps

- **Discovery craft** — hypotheses, interviews, JTBD, PMF
  measurement — is owned by
  [mod-001](../mod-001-customer-discovery-to-pmf/README.md).
  This module runs the discovery *loop* on a weekly cadence;
  it does not re-teach the loop.
- **Opportunity ranking and killing** — RICE / WSJF / Kano,
  multi-surface allocation, the quarterly kill review — is
  owned by
  [mod-002](../mod-002-opportunity-assessment-and-prioritization/README.md).
  The cadence pulls from the ranked queue; it does not re-rank.
- **Roadmap shape, product strategy, OKRs** — the multi-
  quarter framing the cadence lives inside — is owned by
  [mod-003](../mod-003-roadmap-outcomes-and-strategy/README.md).
  This module's cadence executes the roadmap's outcomes; it
  does not re-author the roadmap.
- **Metrics, experiments, and evals** — the instrumentation
  that makes the cadence measurable, A/B design, eval-driven
  decisions for LLM products — are the subject of
  [mod-005](../mod-005-metrics-experimentation-and-ai-evals/README.md).
  Lecture 5 uses evals as a *product-decision surface* inside
  the cadence; mod-005 teaches the eval regime itself.
- **Pricing and packaging** as a product surface — including
  pricing-page microcopy — are the subject of
  [mod-006](../mod-006-pricing-packaging-and-monetization/README.md).
  Lecture 4's microcopy discipline applies; the pricing craft
  itself does not.
- **The founder / eng-lead / GTM-lead relationship contract**
  underneath the cadence — how the CPO negotiates the
  operating model with a technical founder-CEO, how design
  and eng report — is the subject of
  [mod-007](../mod-007-working-with-founders-eng-and-gtm/README.md).
  This module authors the cadence artifact; mod-007 teaches
  the relationship it is negotiated inside.
- **Engineering-side delivery-cadence craft** — DORA metrics
  (deploy frequency, lead time, MTTR, change-failure rate) as
  an SRE measurement regime, on-call rotation design,
  incident-response playbook, deployment pipeline
  architecture — is level-25 work owned by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum).
  The CPO *consumes* DORA numbers as a product-cadence
  signal; the CTO authors the SRE and pipeline that generate
  them. Lecture 2 and Lecture 6 name where that boundary sits.
- **Design systems, accessibility craft, and typography** —
  the professional-designer craft under the microcopy and
  Figma work — is out of scope for a CPO curriculum. Lecture
  4 teaches CPO-appropriate design taste at the surface
  level; a full design curriculum lives outside this repo.

## Sources this module leans on

- Marty Cagan, *Inspired: How to Create Tech Products
  Customers Love* (2nd ed.), Wiley, 2017 —
  [svpg.com/inspired](https://www.svpg.com/inspired-how-to-create-products-customers-love/).
- Marty Cagan with Chris Jones, *Empowered: Ordinary People,
  Extraordinary Products*, Wiley, 2020 —
  [svpg.com/empowered](https://www.svpg.com/empowered-ordinary-people-extraordinary-products/).
- Teresa Torres, *Continuous Discovery Habits*, Product Talk,
  2021 — [producttalk.org/continuous-discovery-habits](https://www.producttalk.org/continuous-discovery-habits/).
- Ryan Singer, *Shape Up: Stop Running in Circles and Ship Work
  that Matters*, Basecamp, 2019 —
  [basecamp.com/shapeup](https://basecamp.com/shapeup).
- Colin Bryar & Bill Carr, *Working Backwards: Insights,
  Stories, and Secrets from Inside Amazon*, St. Martin's, 2021
  — [workingbackwards.com](https://www.workingbackwards.com/).
- Jeff Bezos, "2004 Letter to Shareholders" (the "narrative six-
  pager" prohibition on PowerPoint) —
  [aboutamazon.com/news/company-news/2004-letter-to-shareholders](https://www.aboutamazon.com/news/company-news/2004-letter-to-shareholders).
- Anthropic, "Introducing the Model Context Protocol," Nov.
  2024 —
  [anthropic.com/news/model-context-protocol](https://www.anthropic.com/news/model-context-protocol);
  and the official spec at
  [modelcontextprotocol.io/specification](https://modelcontextprotocol.io/specification).
- Simon Willison, *simonwillison.net* — the running commentary
  on LLM product practice used throughout Lecture 5.
- Hamel Husain, "Your AI Product Needs Evals," May 2024 —
  [hamel.dev/blog/posts/evals](https://hamel.dev/blog/posts/evals/).
- Nicole Forsgren, Jez Humble & Gene Kim, *Accelerate: The
  Science of Lean Software and DevOps*, IT Revolution, 2018 —
  [itrevolution.com/accelerate-book](https://itrevolution.com/product/accelerate/).
- Google Cloud, "DORA — DevOps Research and Assessment," 2024 —
  [dora.dev](https://dora.dev/).

See [resources.md](resources.md) for the full, linked reading
list. Additional sources are cited inline in each lecture and
exercise.
