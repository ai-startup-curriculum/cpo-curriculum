# Lecture 2 — Shape Up vs weekly-ship kanban at the 3–8-engineer scale

## The setup

Lecture 1 left the *delivery* half of the dual-track rhythm
deliberately underspecified. Discovery is discovery — a
continuous, weekly, trio-owned flow. Delivery, on the other
hand, is a *choice*. At the 3–8-engineer scale a founding CPO
operates in, exactly two delivery-side operating models
consistently survive contact with reality:

- **Shape Up** — the Basecamp / Ryan Singer six-week appetite +
  two-week cool-down cycle, with a small "shaping" step
  upstream of the cycle and a bet-shaped commitment inside it.
- **Weekly-ship kanban** — a work-in-progress-limited, no-fixed-
  iteration flow where the delivery-track heartbeat is *"we
  ship something every week"*, not *"we finish a sprint every
  two weeks."*

Neither is Scrum. Neither has a story-pointing ritual, a
committed sprint scope defended against mid-sprint change, or
a Jira board that pretends to be a plan. The market has been
consistently harsh on Scrum-at-startup-scale for the same
reasons Basecamp wrote *Shape Up* against it — the ceremonies
grow, the sprints slip, the retros produce nothing anyone
acts on, and the CPO becomes a project manager.

This lecture teaches the two operating models that actually
work, the failure modes of each, and the signals that push you
toward one or the other. Exercise 2 forces you to make the
choice for your team and defend it.

## The two models, one paragraph each

**Shape Up.** Work happens in **six-week cycles** separated by
**two-week cool-downs**. Before a cycle starts, a small group
of senior product / engineering people **shape** a small
number of *pitches*: each pitch names a problem, an
*appetite* (how much time the company is willing to spend —
usually "six weeks" or "two weeks"), a proposed *solution
sketch* at the fat-marker level (not detailed), and the
*rabbit holes* / *no-gos* the team should avoid. A senior
group **bets** on a small set of pitches at the start of the
cycle — assigning a small team (usually one designer + two
engineers) to each. Once the bet is placed, the team has
**full autonomy over scope within the appetite**: they cannot
extend the timebox, but they can (and should) cut scope to
fit. If the appetite runs out and the work is not done, the
default answer is *no extension* — the pitch loses the bet
and either gets re-shaped for the next cycle or gets dropped
([Ryan Singer, *Shape Up*, Basecamp, 2019, especially chapters
1–3 and 8–14](https://basecamp.com/shapeup)).

**Weekly-ship kanban.** No fixed iteration boundary. The team
maintains a **WIP-limited** flow — usually three to five
concurrent work items across the team, chosen from a ranked
queue the CPO maintains — and the ritual heartbeat is *"we
ship something every week"*. There is a **weekly ship
review** on Friday and a **weekly commit** on Monday for
what enters WIP that week. The queue can be re-ordered
between cycles; work in flight is deferred as little as
possible. The discipline is not iteration boundaries; it is
*continuous flow with WIP limits and pull-based commitment*
(David Anderson's canonical form of Kanban, adapted for
product-team scale
[Anderson, *Kanban: Successful Evolutionary Change for Your
Technology Business*, Blue Hole Press, 2010](http://leankanban.com/kanban-book/)).

Both models coexist with the dual-track discovery rhythm from
Lecture 1 without modification. Discovery runs on its weekly
tempo regardless of which delivery model is chosen. What
changes is *how often the delivery track lands work in
production*, *how the team commits*, and *what the CPO's
role in the commitment ritual looks like*.

## The five signals that pick a model

Six characteristics of your team, product, and stage
consistently predict which of the two operating models will
work. Read all six honestly before choosing.

### 1. Team stability

How stable is the team? Shape Up assumes the same trio
(designer + two engineers) stays on the same bet for six
weeks straight, uninterrupted. If your team is one where the
same engineer will get pulled into a customer escalation for
a week in three of six, you cannot run Shape Up cleanly —
the cycle math breaks. Weekly kanban absorbs interruption
better because commitments are one week long, not six.

- **Shape Up:** stable team, low interrupt rate, no
  on-call-driven pulls into production incidents.
- **Weekly kanban:** interrupt-heavy environment, on-call
  rotation eats team-days, frequent scope re-prioritization
  from GTM / support.

### 2. Discovery maturity per bet

How well-shaped are the pitches you'd bet on? Shape Up assumes
a *shaped* pitch exists — the problem is named, the appetite
is honest, the fat-marker solution sketch is real, the rabbit
holes are known. If shaping is under-invested, the team spends
week 1 of the six-week bet trying to figure out what to build
and burns half the appetite on discovery that should have
happened upstream.

- **Shape Up:** the shaping step is happening (whether owned
  by the CPO or a small senior group), and the pitches
  entering the bet meeting have real problem statements,
  real appetites, and real solution sketches.
- **Weekly kanban:** bets are smaller — often one week —
  which means the discovery underneath each is
  proportionately smaller. The trio can afford to commit
  with less shaping because the exposure per commitment is
  smaller.

### 3. Scope-cut-ability of the typical unit of work

Can the typical unit of work be cut mid-flight without
becoming useless? Shape Up depends heavily on this. The six-
week appetite is a *hard* timebox; the team must be able to
descope to fit. If the typical unit is *"ship the whole SSO
integration or nothing" — where cutting scope means shipping
nothing usable* — Shape Up's descoping discipline fails and
you either extend the bet (breaking the model) or ship
nothing (wasting the cycle).

- **Shape Up:** most work is descope-able — a feature can
  ship in a smaller cut, an integration can ship for two
  IdPs instead of five, a workflow can ship without the
  admin editor.
- **Weekly kanban:** work is decomposable into weekly slices
  by the team pulling it, either because the surface is
  naturally slice-able (dashboards, list views, filters) or
  because the team has learned to slice.

### 4. Product-team autonomy vs. CPO involvement per bet

How much does the CPO need to be in the room on every scope
call inside the cycle? Shape Up assumes the *team makes the
scope call* inside the six weeks; the CPO is out of the
scope-cut conversation once the bet is placed. That is the
whole point of the model — a team that has to phone the CPO
mid-cycle for scope permission is not empowered enough to run
Shape Up.

- **Shape Up:** the team has authority to cut scope inside
  the cycle without escalation. This assumes an empowered
  product team (Cagan's *Empowered* Chapter 8: "Empowered
  Product Team").
- **Weekly kanban:** the CPO is in a weekly commit meeting
  every Monday; scope calls are made in the same room
  weekly. Appropriate when the team is new, the product is
  early, or the CPO is doing more of the product-manager
  work personally.

### 5. AI-substrate iteration density

How often does an AI-substrate slice of the product need to
iterate on prompts, retrieval, or evals? An AI-native slice
often needs a *daily* iteration loop (Lecture 5) — a
prompt-eval sweep, a retrieval-config change, a tool-call
schema tweak. A six-week appetite tolerates that loop poorly:
the team wants to ship a change and see it in production and
in an eval today, not defer it to the next cycle.

- **Shape Up:** the surface is not AI-substrate-heavy, or
  the AI iteration loop is fast enough to happen *inside*
  the six-week bet without repeatedly bumping the appetite.
- **Weekly kanban:** the surface is heavily AI-substrate,
  and the iteration loop needs to land changes weekly or
  faster; the weekly ship review absorbs prompt / eval
  changes naturally.

### 6. Team size and count of concurrent bets

How many concurrent bets can the team run? Shape Up assumes
one small team per bet, and — at 3–8 engineers — usually
one to two concurrent bets. Weekly kanban absorbs a wider
range: two to four items in WIP across a team of five, all
pulled from the same ranked queue.

- **Shape Up:** 5–8 engineers arranged into one or two
  small (designer + two engineers) bet teams per cycle.
- **Weekly kanban:** 3–8 engineers as one team with a
  shared WIP limit and a single ranked queue.

## The choice table

The six signals form a decision heuristic. Read them together;
no single signal decides. As a first cut:

| Signal | Shape Up if... | Weekly kanban if... |
|---|---|---|
| Team stability | Low interrupt, stable trio for 6 wks | High interrupt, on-call-heavy |
| Discovery maturity | Shaping step exists and produces real pitches | Shaping is thin; discovery happens inside the bet |
| Scope-cut-ability | Work is naturally descope-able | Work is fixed-scope or already sliced weekly |
| Product-team autonomy | Team makes scope calls without CPO | CPO in weekly commit meeting |
| AI iteration density | AI slices tolerate a 6-wk cycle | AI slices need weekly-or-faster iteration |
| Team shape | 5–8 eng in 1–2 bet teams | 3–8 eng in one WIP-limited flow |

Two important observations. First, hybrid models exist and
are common: teams that Shape Up the *stable* half of their
work and kanban the *AI-substrate* half; teams that run Shape
Up for two cycles a year and weekly kanban between. Do not
treat the choice as permanent. Second, choosing wrong is
recoverable; failing to choose is not — teams that "kind of
do Scrum" for eighteen months without picking either model
are the ones that lose velocity slowly and irrecoverably.

## Shape Up — the shape, in more detail

Because Shape Up is the more prescriptive of the two, and
because most first-time founding CPOs have read the book
without having run the model, it is worth walking through
what the six weeks actually look like.

**Upstream of the cycle — shaping.** A small group (the CPO,
the eng lead, sometimes the founder-CEO) shapes the pitches
that will be bet on. A pitch is *not a spec*. Singer names
five ingredients: *problem*, *appetite*, *solution* (fat-
marker sketch, not detailed screens), *rabbit holes* (the
things that could eat the appetite), and *no-gos* (things
explicitly out of scope). A shaped pitch is deliberately
under-specified in the detailed-design axis (so the team has
room to make design choices) and deliberately over-specified
in the *what we're not doing* axis (so the team knows the
edges)
([Singer, *Shape Up*, Chapters 2–6](https://basecamp.com/shapeup)).

**The bet meeting.** At the start of the cycle, the senior
group meets and *bets* on a small set of pitches. Betting
means: this team, on this pitch, for this appetite, this
cycle. Once placed, the bet is a commitment on both sides —
the company commits the team's time; the team commits to
shipping within the appetite or losing the bet.

**Weeks 1–2 — hills.** The team's first job is to get
"over the hill" on the *unknowns* in the pitch — the things
where they cannot see how the work will get done. Singer's
"hill chart" visualizes this: uphill is figuring-out-how,
downhill is doing-what-we-know. A team that is still uphill
in week 4 of 6 is signalling the bet is in trouble.

**Weeks 3–5 — build.** Downhill work. Real code. This is
the phase where the descoping discipline gets exercised:
the team is constantly making calls about what to cut to
fit the appetite. A team that never cuts scope in weeks 3–5
either shaped the appetite too generously or is about to
overrun.

**Week 6 — ship.** Ship the work, close the bet. Whatever
did not fit is either dropped or re-shaped for a future
cycle.

**Cool-down (weeks 7–8).** No bets in flight. The team
handles bugs, small improvements, and — critically — spends
time thinking about what to shape next. The CPO uses the
cool-down for the shaping work upstream of the next cycle.

## Weekly-ship kanban — the shape, in more detail

Weekly kanban is less prescriptive, but has a small number
of disciplines without which it collapses into "chaos on a
board."

**A single ranked queue.** The CPO maintains one ranked list
of work items pulled from the roadmap. When an item enters
WIP, it is committed to a specific person or pair; when it
leaves WIP (ships), the next item is pulled in. No one
starts a new item without a slot opening.

**WIP limits.** The critical mechanic. If your team is 5
engineers, WIP might be 3 or 4 concurrent items across the
whole team (not per person). Reinertsen's *Principles of
Product Development Flow* is the canonical argument for why
WIP limits — not sprint boundaries — are what makes flow
predictable
([Reinertsen, *The Principles of Product Development Flow*,
Celeritas, 2009, especially chapters 3–5](https://celeritaspublishing.com/product/the-principles-of-product-development-flow/)).

**Weekly ship review, Friday.** What shipped this week?
What's in flight? What's stalled? A stalled item is either
finished (declare it done and pull the next), killed
(declare it a mistake and pull the next), or explicitly
re-committed with a named blocker and a next-step owner.

**Weekly commit, Monday.** What enters WIP this week? The
CPO and the eng lead run this together (with the designer);
the team pulls from the top of the queue subject to the WIP
limit.

**Cycle-time SLA.** A soft one — most items ship within a
week, and items that consistently take three or four weeks
to ship signal that the slice is not really a weekly-ship
slice and probably wants a Shape Up-style appetite instead.

## Failure modes — Shape Up

Three failure modes worth naming, because each is a
Lecture 6 anti-pattern in miniature.

- **Extension creep.** The cycle overruns and the team
  extends. This defeats the whole model — the appetite
  becomes advisory rather than binding, the team learns
  that "six weeks" is really "ten," and the shaping
  discipline degrades because the team knows extension is
  possible. Counter-move: the senior group makes the
  extension decision *publicly, at the bet meeting for the
  next cycle*, and always with a named cost (which of the
  next cycle's bets are we not taking to fund this?).
- **Under-shaped pitches.** The pitches entering the bet
  meeting are not really shaped — the solution sketch is
  missing, the rabbit holes are unnamed, the appetite is a
  guess. The team burns weeks 1–2 trying to figure out
  what to build. Counter-move: a *shaping-quality gate*
  before a pitch is bet on. Singer describes it; most
  teams skip it and then wonder why cycles overrun.
- **Silent scope-cut aversion.** The team resists
  descoping because they see it as "shipping less" rather
  than as "hitting the appetite." Cycles overrun; the
  team's read of Shape Up shifts to "six weeks is when
  we're done." Counter-move: at the bet meeting, name
  which scope in the pitch is *first to cut*, second to
  cut, third to cut — a Reinertsen-style
  pre-registered cut order that turns descoping from a
  team's decision under pressure into a decision made
  under lower stakes upstream.

## Failure modes — weekly kanban

Also three:

- **Runaway WIP.** The WIP limit stops being enforced;
  three items become five, five become eight, everything
  is in flight and nothing ships. Counter-move: the Friday
  ship review counts WIP, publicly. Weeks where WIP grew
  without a corresponding ship are diagnosed as a
  discipline failure, not a scope failure.
- **Priority thrash.** The CPO re-orders the queue too
  often, and items that entered WIP get abandoned mid-
  flight for a shinier new item. Counter-move: a soft
  rule that anything in WIP finishes or is *explicitly
  killed*, in the same commit meeting, with a named
  reason.
- **Item bloat.** Weekly items grow into three-week items
  and stop shipping weekly, but nobody re-shapes them.
  The team feels productive; the cadence has silently
  collapsed. Counter-move: an item that fails to ship
  after two consecutive Fridays gets *re-shaped* (into
  smaller items) or *re-cast* as a Shape Up-style bet.

## The CPO's role in each

Different in kind, not degree. In Shape Up, the CPO is heavy
*upstream of* the cycle (shaping, betting) and light *inside*
it — the team runs autonomously. In weekly kanban, the CPO
is in the operating rhythm every week — the Monday commit,
the Friday review, and often on the phone about slice cuts
inside the week.

- **Shape Up CPO:** author pitches, chair the bet meeting,
  stay out of the team's scope calls inside the cycle,
  spend cool-down on shaping the next cycle.
- **Weekly kanban CPO:** maintain the ranked queue, chair
  the Monday commit, chair the Friday review, be the
  person who decides mid-week when a slice needs to be
  descoped or killed.

Neither role is heavier than the other in total time; they
are heavy at different moments.

## What both models refuse — and why

Both models are explicitly designed against Scrum-at-startup-
scale. It is worth being explicit about what they refuse and
why:

- **Story-pointing rituals.** Neither model uses story
  points as its unit of commitment. Shape Up uses
  *appetite* (a timebox); kanban uses *cycle time*
  (measured, not estimated). Singer is direct that story
  points invite arguments-about-estimates and hide the
  real question, which is *how much time is this worth to
  us?*
- **Fixed-scope sprints.** Both models refuse the "we
  committed to this scope in this iteration" ceremony.
  Shape Up commits to appetite, not scope; kanban commits
  to WIP, not calendar.
- **The Jira board as a plan.** Both models treat the
  operating tool as an operational record, not a plan.
  The plan is the roadmap (mod-003); the queue is the
  next-few-slices; the tool is where you write down what
  happened.

## Where Cagan sits in the choice

Cagan, notably, is agnostic between the two. *Empowered*
teaches the *product team shape* — a small, empowered trio
running dual-track — without prescribing a specific delivery
operating model. The choice of Shape Up or kanban is a
choice the empowered team makes for itself given the six
signals above. What Cagan is *not* agnostic about is that
the team must be empowered enough to make the choice
([Cagan & Jones, *Empowered*, Chapter 24: "Product Team
Autonomy"](https://www.svpg.com/empowered-ordinary-people-extraordinary-products/)).

## Boundaries this lecture keeps

- **The discovery track** — Monday interview, Thursday
  sync, Friday ship review, opportunity solution tree —
  is Lecture 1. This lecture is only about the delivery
  half.
- **PRD form (six-pager)** — the *artifact* that shapes
  work in either model — is Lecture 3. Shape Up's
  *pitch* and kanban's *ticket* both benefit from
  six-pager discipline where the bet is large enough.
- **Own the pixel** — the design-and-microcopy side of
  each cycle — is Lecture 4.
- **Agentic UX iteration loops** — the AI-substrate
  weekly-or-faster loop that pushes hard toward kanban —
  is Lecture 5.
- **DORA metrics** (deploy frequency, lead time, MTTR,
  change failure rate) — the SRE-side measurement regime
  that observes the delivery cadence — is level-25 work
  owned by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum).
  The CPO *consumes* the numbers as a signal about whether
  the chosen operating model is actually working; the CTO
  authors the pipeline that generates them. This matters
  in this lecture because — for either operating model —
  *deploy frequency* is the observable that tells you if
  the model is producing weekly-or-faster ships. Ask the
  CTO for the number; do not build the dashboard yourself.

## Takeaways

- Two operating models survive at 3–8 engineers: **Shape
  Up** (six-week appetite + cool-down, shaped pitches,
  team-owned scope) or **weekly-ship kanban** (WIP-
  limited, no fixed iteration, weekly commit and ship
  reviews). Scrum-at-startup-scale is a third option and
  is not recommended.
- Choose using the six signals: team stability, discovery
  maturity per bet, scope-cut-ability of the typical
  unit, product-team autonomy, AI iteration density,
  team shape.
- Shape Up's discipline is *appetite*: the timebox binds,
  the scope cuts. Kanban's discipline is *WIP limits and
  cycle time*: flow binds, priority is stable within the
  week.
- The CPO's role differs — heavy upstream in Shape Up,
  heavy every week in kanban — but is the same in total
  intensity.
- Both models refuse story points, fixed-scope sprints,
  and treating the Jira board as a plan. Cagan is
  agnostic between them but not agnostic about team
  empowerment.
- Consume DORA-shaped deploy-frequency numbers from the
  CTO to check whether the model is actually producing
  the cadence you chose it for.

Lecture 3 changes the *artifact* the cadence produces — from
spec-shaped PRDs to Amazon-6-pager, working-backwards
narratives — so the operating model has the right kind of
input to bet on.
