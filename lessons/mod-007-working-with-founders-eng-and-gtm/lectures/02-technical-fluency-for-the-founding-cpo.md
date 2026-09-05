# Lecture 2 — Technical fluency for the founding CPO

## The setup

The market has quietly changed what it means for a
founding CPO to be *"technical enough."* In 2016, a
non-engineer PM at a Series-A SaaS company could
survive with a working knowledge of REST APIs, database
schemas, and "roughly how the deployment works." In
2026, at a pre-seed / seed AI-native startup — the
Solidroad / Blacksmith / saas.group / Uare-shaped
posting this module targets — the CPO is expected to
read a pull request, reason about which pieces of a
system live where and why, scope an engineering slice
within a factor of two, and catch a PRD that under-
specifies a system before the eng team discovers the
gap mid-sprint.

None of this means the founding CPO writes production
code. It means the CPO can *hold the conversation*
with the founding-engineering team on merit — without
falling back to "you're the engineers, you decide" or,
worse, to "just make it happen." Both are ways of
losing the ability to shape the product; the first
gives it away, the second gives it away *and* damages
the working relationship.

This lecture teaches the four fluencies the market
asks for and the specific ways a founding CPO acquires
each. It also names the level boundary carefully:
architectural depth — the *how do we build this
system* question at the CTO level — is
[cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)
(level 25). This lecture is the *consumption layer*,
the depth a CPO needs to be a productive partner to
the CTO.

## The four fluencies

The founding-CPO technical-fluency ladder has four
rungs. Each rung enables a specific kind of
conversation.

1. **Read a PR well enough to ask the right question.**
   Not to review it; to read it. The goal is to catch
   PRDs that missed something the code reveals, and to
   participate in scope conversations with shared
   vocabulary.
2. **Reason about API contracts and their downstream
   effects.** Public-API changes affect customers,
   integrators, and internal consumers; the CPO reads
   the change well enough to know which of those it
   touches.
3. **Reason about infrastructure trade-offs — cost,
   latency, reliability — at the framing level.** Not
   to make the choice; to understand the CTO's
   framing when it's presented, to push back where
   the product implications aren't obvious, and to
   fold the trade-off into the PRD.
4. **Scope engineering work within a factor of two.**
   The founding CPO makes rough estimates
   constantly — for the roadmap, for exec / board
   updates, for GTM launch dates. Being systematically
   optimistic by 5× is a load-bearing failure. Two
   is the honest range at CPO scope.

Each rung is teachable. Each rung is also atrophy-able:
lose the muscle and the ability to hold the conversation
goes with it.

## Fluency 1 — Reading a PR

The goal of reading a PR as a CPO is not code review.
It is not to catch bugs or approve merges — the eng
team owns both. The goal is to catch *product-
implication drift* before it ships: PRDs that
under-specified a state change, edge cases the eng
team surfaced in code but didn't flag in review,
public-facing behavior the CPO would have wanted to
know about.

A working question checklist for reading a PR — six
questions, in order:

1. **What does this do to what the user sees or does?**
   If the answer is "nothing," verify by finding the
   route / component / endpoint the change touches. If
   the answer is "something," the CPO should be able
   to describe it in one sentence in user-facing
   language.
2. **Is there a state change I need to document?**
   New database columns, new event types, new
   feature-flag defaults, new user preferences —
   anything that changes what "the system remembers"
   about a user. State changes tend to have
   downstream implications for onboarding, support,
   or migration.
3. **Is there a public API change?** Any change to a
   REST endpoint, a webhook payload, a public event
   schema, or an SDK surface. Public-API changes
   often need customer communication and always need
   version discipline.
4. **What is the failure mode?** What happens when
   this code path errors? Silent retry? Loud crash?
   User-facing error message? Half-completed state?
   The failure mode almost always has a product
   surface — the user sees *something* — and the CPO
   should know what.
5. **What's the test coverage?** Not to grade it; to
   understand what the eng team believes is tested
   and what they believe is un-tested. Un-tested
   surfaces are where the "we shipped it, then the
   week-two bug" surprises come from.
6. **What's the migration story?** For anything that
   changes existing customer state — a data
   backfill, a config migration, a feature-flag
   rollout — the CPO reads the migration plan and
   understands the customer-facing shape.

Reading a PR against this checklist takes ten to
fifteen minutes for a small change and half an hour
for a large one. The CPO does not read every PR. The
CPO reads PRs that touch:

- **Product surfaces the CPO is currently PRD-owning**
  — either shipped surfaces or in-flight ones.
- **Public API changes**, regardless of who authored
  the PRD.
- **Anything the eng lead flags in Slack** with
  "@cpo you might want to see this."

Do not review every PR. The signal-to-noise on the
whole repo is bad, the ceremony cost is high, and the
eng team will (rightly) stop flagging things because
they'll assume the CPO already saw it.

### What "reading a PR" is not

- **Approving merges.** Never. The eng team owns
  merge approval.
- **Filing style / naming nits.** Never.
- **Suggesting architectural refactors.** That is
  Lecture 5's scope-conflict discipline, not a PR
  comment.
- **Reading every PR.** Only the ones the checklist
  above pulls in.

Getting this boundary wrong is the fastest way to
turn the eng team against the CPO reading PRs. The
CPO's PR comments should almost always be *questions*
in user-facing language, not answers.

## Fluency 2 — Reasoning about APIs

APIs — REST endpoints, GraphQL schemas, gRPC
services, event streams — are how the product's
capabilities become integratable. Most product
surfaces at pre-seed / seed have three API audiences
that the CPO reasons about:

- **External customers and integrators**, who consume
  the public API to build on top of the product.
- **Internal consumers**, who consume the same API
  from other services or from the frontend.
- **Future selves**, because every public API is a
  commitment the team will still be paying for in
  eighteen months.

The founding-CPO reading of an API change is not
about the specific route or payload; it is about the
*contract*. The four contract-level questions:

- **What can consumers now do that they couldn't
  before?** Or, for a breaking change: what could
  they do that they can no longer do?
- **What's guaranteed about latency, throughput,
  and consistency?** Not a specific SLA number
  necessarily; the *shape* — is this a real-time
  read, an eventually-consistent read, a batch
  endpoint that returns within minutes.
- **How is authentication and authorization
  handled?** What data does this endpoint expose
  and to whom? This is where security-shaped
  product bugs live.
- **How does this evolve?** Is the endpoint
  versioned? Is there a deprecation policy? Is
  there a way to add fields without breaking
  existing consumers?

For most founding-CPO conversations, the four
questions are enough. When they aren't — when the
API decision has architectural implications the
CPO can't reason about — the CPO's move is to say
so and pull the CTO in. The failure to avoid is
*pretending* fluency: nodding along to an API
decision the CPO doesn't understand, then finding
out three months later that the shape locked out a
GTM commitment.

## Fluency 3 — Infrastructure trade-offs at the framing level

Infrastructure trade-offs — cloud provider, database
choice, self-hosted vs. managed, region strategy,
serverless vs. containers — are decisions the CTO
owns. The CPO does not choose Postgres or DynamoDB.
The CPO *does* need to understand the trade-offs
because most of them have product implications.

The three trade-off dimensions the CPO cares about:

- **Cost.** Every infrastructure choice has a
  cost curve. Serverless is cheap at low volume,
  expensive at high volume. Managed databases
  are more expensive but need less ops attention.
  Multi-region is materially more expensive than
  single-region. The CPO reads the cost curve to
  know where the pricing model (mod-006) has to
  keep the customer.
- **Latency.** Every user-facing action has a
  latency budget. Single-region deployments have
  a floor set by physics — a user in Sydney
  talking to a us-east-1 database sees 200ms+
  round-trip regardless of code. The CPO knows
  which product surfaces have a latency floor
  the current infra imposes.
- **Reliability.** Every service has an availability
  target. Multi-AZ / multi-region infrastructure
  is more resilient but more expensive; single-
  region is fine for most pre-seed / seed products
  but has a specific outage shape (region-wide
  failure) the CPO should be able to describe in
  one sentence to a customer.

For AI-substrate products specifically, three more
trade-offs matter and get their own treatment in
Lecture 3:

- **Which model tier for which surface.**
- **Prompt caching, batch, and streaming.**
- **Third-party model dependency and provider risk.**

The CTO owns the choice; the CPO consumes the
framing. Where a trade-off has a customer-facing
implication (region choice affects who the product
can sell to; latency affects the feel of a
workflow; provider dependency affects contract
language for enterprise customers), the CPO folds
the implication into the PRD.

## Fluency 4 — Scoping engineering work

The single most common founding-CPO scoping failure
is *systematic 5× optimism*: the CPO estimates
"two weeks" for something that lands in ten weeks,
across the whole roadmap, month after month. The eng
team eventually stops trusting CPO estimates entirely
and starts padding by 3–5× in return, which then
lets the CPO be even more optimistic because the
estimates already have padding.

The mature-org fix is **story points and velocity
tracking**; the founding-team fix is a lighter
discipline that doesn't need a Jira workflow.

### The founding-CPO scoping method

Four questions per scoped slice, answered *by the eng
person who would build it*:

1. **What's the shape?** Backend change only? Frontend
   change only? Both? Data migration? Third-party
   integration? New service? Different shapes have
   different base rates.
2. **How many places does it touch?** Two files, ten
   files, forty files. Order-of-magnitude.
3. **What's the biggest unknown?** Not "unknowns" as
   a category; the *specific* biggest one. A named
   unknown is often researchable in a day; unnamed
   unknowns are what make estimates wrong.
4. **What's the eng person's *gut* number, before
   thinking?** Half a day, two days, a week, a
   month. Gut numbers are systematically better
   than deliberated numbers for coarse estimates
   at this scale.

The CPO's rough estimate is then the eng gut number
scaled by a factor that reflects the biggest unknown
(2× if the unknown is bounded; 3–5× if it isn't; if
the unknown is *unbounded*, the answer is "we can't
scope this yet — needs a spike").

### The two-week Shape Up appetite

For anything the eng team will spend more than two
weeks on, the [Shape Up appetite](https://basecamp.com/shapeup/1.2-chapter-03)
discipline from Ryan Singer's *Shape Up*
([basecamp.com/shapeup](https://basecamp.com/shapeup))
applies: the CPO decides *how much time the problem
deserves* (the appetite — "two weeks," "six weeks"),
the eng team decides what fits inside the appetite
(the shape — what gets built, what gets cut). This
is the founding-team version of what mod-004 Lecture
2 teaches for delivery operating models; it also
happens to be the sanest engineering-scoping
discipline at this scale because it forces the CPO
to separate the *value* of the work from the *size*
of the work.

### Writing the estimate down

Rough estimates that live only in the CPO's head are
where the systematic 5× optimism hides. The
founding-CPO discipline: every roadmap item with a
committed date has a written estimate, dated, with
the eng person who provided the gut number named,
and with the biggest unknown listed. When the estimate
is wrong (it will be, often), the retrospective is
against the *written record*, which produces the
learning loop that closes the estimate gap over time.

## Fluency 5 — Catching under-specified PRDs

A PRD (product requirements document) that
under-specifies the system is one the eng team
receives, starts implementing, and *only then*
discovers questions the PRD didn't answer. Every
question the PRD didn't answer is a decision the
eng team either makes without the CPO (which
compresses the CPO's product ownership) or brings
back to the CPO mid-sprint (which slows delivery).

Common under-specification patterns:

- **Missing state transitions.** The PRD describes
  a feature's happy path but not what happens on
  error, on abandonment, on retry, on partial
  completion.
- **Missing permission model.** Who can do this?
  Only the account owner? Any user? Users at
  certain plan tiers? The permission model tends
  to be an afterthought in PRDs and a first-day
  question in engineering.
- **Missing empty state.** What does the new
  feature look like before any data exists? First-
  time users hit the empty state, and the PRD
  often shows only the populated state.
- **Missing telemetry.** What events does this
  feature emit? What analytics does the CPO
  expect to see? Without this in the PRD, the
  eng team either instruments nothing or
  instruments incorrectly.
- **Missing migration story.** For any feature
  that changes existing user state, how do
  existing users get moved to the new shape?
- **Missing feature-flag / rollout plan.** How
  does this ship — to everyone at once? To 10%
  first? Behind a flag customers can opt into?
- **Missing failure semantics for AI features.**
  When the model fails or returns garbage —
  which is inevitable — what does the user see?
  What retries happen? What escalations to a
  human? Chapter 3 goes deeper.
- **Missing cost / latency budget.** For AI
  features specifically, what does the feature
  cost per invocation, and what's the latency
  budget it must meet?

The founding-CPO discipline is to run every PRD
through this checklist *before* handing it to eng.
The mod-004 Lecture 3 Amazon-6-pager PRD shape
already forces most of these into the document; the
checklist catches the ones the six-pager form
misses.

## Where the founding CPO should *not* go

Four temptations that produce more damage than they
prevent:

- **Suggesting how to build it.** The CPO who
  writes "let's use Redis for this cache" in the
  PRD is doing the CTO's job. Even if the CPO is
  right, the price is that the eng team stops
  bringing architectural options to the CPO
  because they've learned the CPO will just
  choose one.
- **Reviewing PRs as code.** Style, naming,
  refactoring suggestions. All out of scope.
- **"Just push it live" pressure.** The CPO who
  applies deploy pressure over engineering
  objection is spending relationship capital
  faster than the launch is worth.
- **Retroactively changing scope after the estimate
  is set.** If the CPO decides after the estimate
  that "we also need X," X is a *new* estimate,
  not a "just add it" ask. Compounding scope creep
  under a fixed date is where the eng team's
  trust dies.

## What the CPO does personally

- **Reads PRs against the six-question checklist**
  on surfaces they own, on public APIs, and on
  anything flagged.
- **Reads the CTO's architectural framings** —
  ADRs, RFCs, tech-spec docs — well enough to
  ask questions and hold the product-implication
  conversation.
- **Runs every PRD through the under-
  specification checklist** before handoff.
- **Writes rough estimates down** with the eng
  person, the date, and the biggest unknown
  named.
- **Owns the retrospective on missed estimates**:
  the CPO's estimates are the CPO's, not the eng
  team's. Owning the miss protects the working
  relationship.

## What the CPO consumes from the CTO / eng lead

- **Architectural decision records.** The CTO
  writes ADRs (see the [C4 model](https://c4model.com/)
  or the classic Michael Nygard ADR pattern); the
  CPO reads them.
- **Cost / latency dashboards.** Whatever the
  eng team monitors; the CPO knows where to
  look and what "normal" looks like.
- **Deployment / release notes.** Every ship the
  CPO can trace to a PR and a change.
- **Debt cost-to-carry estimates.** For
  Lecture 5's scope-conflict resolution. This is
  the [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)
  mod-105 output the CPO consumes.

## Boundaries this lecture keeps

- **Architecture at CTO depth** — system
  decomposition, service boundaries, data model
  choice, deployment topology, security
  architecture, on-call design — is level-25
  work owned by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum),
  particularly mod-102 (Architecture Under
  Uncertainty) and mod-103 (Build-vs-Buy).
- **Writing production code.** Explicitly not the
  founding CPO's job. If the CPO ends up writing
  production code, either the eng team is
  under-hired (an eng problem) or the CPO is
  displacing the eng team (a CPO problem).
- **The engineering-management vocabulary at
  depth** — Camille Fournier's *The Manager's
  Path*, [oreilly.com](https://www.oreilly.com/library/view/the-managers-path/9781491973882/),
  is the reference; the CPO reads it once and
  borrows the vocabulary but does not manage
  engineers.
- **AI-specific system architecture** — context
  engineering, retrieval, tools / MCP, evals,
  cost / latency Pareto — is
  [Lecture 3](03-ai-system-architecture-for-the-founding-cpo.md).

## Takeaways

- **The founding CPO is technical enough to hold
  the conversation, not to build the system.** Four
  fluencies: read a PR, reason about APIs, reason
  about infra trade-offs, scope engineering work.
- **Read PRs against a six-question checklist**
  (user-facing effect, state change, public API,
  failure mode, test coverage, migration story).
  Only PRs on owned surfaces, public APIs, or
  flagged; never all PRs.
- **API contract questions**: what can consumers
  do, latency / consistency shape, auth model,
  evolution / versioning.
- **Infra trade-offs**: cost curve, latency floor,
  reliability shape. CPO consumes the CTO's
  framing.
- **Scope with four questions** (shape, places
  touched, biggest unknown, gut number) and the
  Shape Up appetite discipline. Write the estimate
  down, dated, with the unknown named.
- **PRD under-specification checklist** catches the
  patterns that produce mid-sprint scope questions
  — state transitions, permissions, empty state,
  telemetry, migration, rollout, AI failure
  semantics, cost / latency budget.
- **Four things not to do**: suggest how to build
  it, review PRs as code, apply deploy pressure,
  retroactively expand scope.

Lecture 3 turns to the **AI/LLM system architecture
depth** the market now expects a founding CPO to
bring — context engineering, retrieval, tool /
MCP contracts, eval loops, and the cost / latency
budget.
