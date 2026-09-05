# Lecture 1 — Dual-track discovery/delivery: the Cagan/Torres weekly rhythm

## The setup

Ask a first-time founding CPO to describe how their team ships,
and the answer will almost always fall into one of two shapes.
The first is *phase-shaped*: "we do discovery in Q3 and delivery
in Q4." The second is *delivery-only*: "we run two-week sprints,
we take feedback in the retro." Both are diagnosable failures of
the same underlying model — a model in which discovery is a
thing that happens *before* delivery, done by someone *other*
than the delivery team, on a cadence *slower* than the
customer's.

The move Marty Cagan and Teresa Torres both argue for — one
from the empowered-product-team angle, one from the continuous-
discovery angle — is called **dual-track**. Discovery and
delivery are two tracks that run continuously **in parallel**,
by the same product team, at the same weekly cadence. The
discovery track answers *is this worth building, and if so
what shape*; the delivery track ships. The team does both every
week. There is no hand-off boundary between them, because they
are the same team.

This lecture teaches the shape of that rhythm — where discovery
sits, where delivery sits, how they intersect on the weekly
calendar, what artifacts each track produces, and what the
founding CPO does personally versus what the team does
autonomously.

## Why dual-track exists — and what it is not

The dual-track term is not new. Desirée Sy first named it in
*"Adapting Usability Investigations for Agile User-Centered
Design"* (2007) as a way to reconcile ethnographic UX research
with an agile-shaped delivery team
([jusabilitystudies.org, Vol 2, Issue 3](https://uxpajournal.org/adapting-usability-investigations-for-agile-user-centered-design/)).
Jeff Patton generalized it in *"Dual Track Development is Not
Duel Track"* (2017) as a way to distinguish the *discovery*
track (research, prototyping, validation) from the *delivery*
track (build, ship, learn from production), each running as a
continuous flow
([jpattonassociates.com](https://www.jpattonassociates.com/dual-track-development/)).

Marty Cagan makes the same point in *Inspired* and expands it
in *Empowered*: discovery is *what a product manager, product
designer, and tech lead do together every week*, not a phase.
The product manager owns the *value* and *viability* questions
(will customers use it, does the business make sense); the
product designer owns *usability* (can they figure it out); the
tech lead owns *feasibility* (can we build it, at what cost).
Discovery is the continuous, weekly answering of those four
questions before an idea earns a slot on the delivery track
([Cagan, *Inspired* (2nd ed.), Wiley, 2017, Part IV: "The
Right Process"](https://www.svpg.com/inspired-how-to-create-products-customers-love/);
Cagan & Jones, *Empowered*, Wiley, 2020, Chapter 8: "Empowered
Product Team"](https://www.svpg.com/empowered-ordinary-people-extraordinary-products/)).

Teresa Torres, writing from the continuous-discovery angle,
insists on the *weekly* tempo of the discovery track and the
role of the **weekly customer touchpoint** as its heartbeat: at
least one interview or observation per week, done by the
product trio, tied to a live opportunity solution tree, with
the discovery-side experiments generated inside the same week
([Torres, *Continuous Discovery Habits*, Product Talk, 2021,
Chapter 1: "The Discovery
Habits"](https://www.producttalk.org/continuous-discovery-habits/)).
The weekly tempo is the innovation. Without it, discovery
silently becomes a quarterly deep-dive, and the delivery track
runs on stale evidence.

Two things dual-track is *not*:

- **Not a two-team model.** There is no "discovery team" that
  hands specs to a "delivery team." That shape is
  spec-then-hand-off, a Lecture 6 anti-pattern. The whole
  point of dual-track is that the *same* trio does both
  tracks.
- **Not water-Scrum-fall.** The version where a big-up-front
  discovery phase precedes a sprint-based delivery phase
  ("agile after we know what to build") is not dual-track;
  it is agile in delivery bolted onto waterfall in discovery.
  Cagan and Torres both flag this as the most common
  misapplication.

## The two tracks, side by side

The rest of the lecture uses this shape:

```
                +-------------------------------+
                |        Product Trio           |
                |  PM  •  Product Designer  •   |
                |         Tech Lead             |
                +-------------------------------+
                           /       \
                          /         \
              Discovery track     Delivery track
              --------------      --------------
              What is worth       What we're
              building next       shipping now
              (evidence)          (production code)
              --------------      --------------
                          \        /
                           \      /
                +---------------------------+
                |  Weekly rhythm rituals    |
                |  that bind the two tracks |
                +---------------------------+
```

The **discovery track** produces *evidence*: interview notes,
prototype-test results, opportunity-tree updates, killed
assumptions. Its unit of work is the *assumption test*, not
the *feature*. Its output is a change in what the team
*believes*, not a change in production.

The **delivery track** produces *production code and shipped
outcomes*. Its unit of work is a *shipped slice* (a feature
flag flipped on, a change deployed to real users, an issue
closed). Its output is a change in what the *user experiences*,
not a change in what the team believes.

The two tracks are bound by a small number of **weekly rituals**
that make sure the belief-change (discovery) actually informs
the ship-change (delivery), and vice versa. Those rituals are
what a cadence *is*.

## What the founding CPO does personally

The Cagan / Torres model assumes a *product trio*: a PM, a
product designer, and a tech lead, running discovery together
every week. At the pre-seed / seed scale a founding CPO
operates in, that trio often does not fully exist. The
common shapes:

- **CPO doing PM-plus-designer work.** No product designer
  yet; the CPO owns discovery, prototyping, and Figma
  (Lecture 4). The tech lead is a founding engineer or the
  founder-CTO.
- **CPO plus one product designer, one tech lead.** The
  fullest form of the trio at this scale. The CPO is still
  the one making the value / viability calls; the designer
  does usability; the tech lead does feasibility.
- **CPO doing all three.** Common in the first ~30 days
  before hiring closes. Legitimate as a temporary shape;
  dangerous as a permanent one, because the feasibility
  read starts to systematically favor "what the CPO could
  imagine building."

The lecture uses "CPO / product trio" interchangeably from
here. The exercise (Exercise 1) forces you to name which
shape you are in, because the weekly calendar looks different
in each.

## The weekly rhythm — a canonical shape

The specifics vary by team, but the *shape* of a working
dual-track week has five recurring surfaces. What follows is
a canonical example; adapt the day-of-week and the exact
naming to your team.

### Monday — the weekly interview / touchpoint

Torres's non-negotiable: at least one interview or observation
with a real customer, done by the product trio, tied to a
current opportunity on the tree. Not a *demo* (that is a GTM /
sales ritual). Not a *success-team QBR* (that is retention).
An open-ended discovery conversation.

- **What it produces:** one to three new opportunities added
  to the tree, one to three assumptions falsified or
  strengthened, and — sometimes — a fresh solution idea to
  prototype-test later in the week.
- **Who runs it:** the product trio, together. Cagan and
  Torres both emphasize that all three attend; skipping the
  tech lead is the most common failure mode, because
  feasibility framings emerge in the conversation and get
  lost if only PM+designer are in the room.

### Tuesday–Wednesday — the assumption tests

Small, cheap tests of the top-of-tree assumptions. Prototype
tests (an unpolished clickable Figma tested with three
customers), fake-door tests (a call-to-action wired to a
"coming soon" page to measure demand), unmoderated usability
tests, data pulls (does the assumption we're making about
usage patterns even hold in the current logs?), or
prompt-eval sweeps for AI-substrate features (Lecture 5).

- **What they produce:** falsified or strengthened
  assumptions on named opportunities. The output is a
  *belief change*, not a design or a spec.
- **Cadence guarantee:** at least one assumption test moved
  from "planned" to "concluded" per week. If a week goes by
  without one, the discovery track is failing.

### Thursday — the trio's discovery / delivery sync

The single most important ritual in the whole cadence. The
trio spends 45–60 minutes reviewing:

- **What did discovery learn this week?** Interview
  findings, assumption-test outcomes, opportunity-tree
  updates. Which opportunities got stronger, which got
  weaker, which just moved.
- **What does delivery need next?** From the shipped slices
  currently in flight, what evidence would tell us we're on
  the right track vs. off it. What discovery would we need
  *before* the next slice in the queue can be committed to.
- **What does the queue look like next week?** Which
  opportunities are ready to move from discovery ("we
  believe this bet") to delivery ("we're building it")?
  Which delivery in flight is showing signs it needs a
  discovery detour?

This ritual is the seam between the two tracks. If it
doesn't exist, the two tracks silently detach, and
delivery starts running on the team's memory of what was
learned six weeks ago.

### Friday — the shipped-slice review + weekly changelog

The delivery-track counterpart to Monday's interview. What
did we ship this week? What did users do with it? What went
wrong, what surprised us, what needs a discovery follow-up?

The **live changelog** (Lecture 4) is authored here — a
one-paragraph public entry, per shipped slice, that names
what changed and (where visible) what we learned. The
changelog is *published to users*, not just to the team.
Authoring the changelog is a forcing function on shipping
things small enough that a human can describe them in a
paragraph.

### Continuously — the opportunity solution tree

Torres's core artifact. A live document the trio maintains
throughout the week (not a Monday-morning update). Every
interview finding lives on it. Every assumption test is
tied to a node. Every delivery-track slice is downstream
of an opportunity on it. If a slice cannot be traced to an
opportunity on the tree, the trio has to decide either to
put the opportunity on the tree or kill the slice —
because there is no third option in this model
([Torres, Chapter 6: "Mapping the Opportunity Space"](https://www.producttalk.org/continuous-discovery-habits/)).

## The seam — how discovery informs delivery (and back)

The failure mode dual-track exists to prevent is *decoupling*:
discovery producing a lot of evidence nobody uses, and
delivery running on the team's aging model of what customers
want. The seam — the Thursday sync plus the always-live
opportunity tree — is what prevents it.

Two disciplines make the seam work:

- **Every delivery slice points at an opportunity.** No
  slice ships without a named opportunity on the tree that
  the trio believes it moves. This is the same discipline
  mod-002 taught for the queue: an opportunity is a
  bounded problem, not a feature. Delivery is the
  *response* to an opportunity, not an idea that arrived
  fully formed from a stakeholder.
- **Every opportunity that graduates from discovery to
  delivery has a *pre-registered signal*.** The trio
  agrees, at commit time, on the metric or observation
  that would tell them the slice moved the opportunity —
  and the horizon on which they'll check. This is the same
  falsifier discipline mod-002 taught for actions, applied
  at the cadence level.

Without both, the seam fails silently. A dashboard of
delivery-track velocity and a dashboard of interview counts
are not enough — a team can ship a lot and interview a lot
while never letting either track affect the other.

## Where the CPO discovers, where the CPO delivers

At the pre-seed / seed scale, the founding CPO does more of
the discovery track personally than the CPO of a Series-C
company does. Concretely:

- **Weekly interviews:** the CPO is in the room, not
  reviewing recordings. This is level-with mod-001 and
  non-negotiable.
- **Assumption tests:** the CPO often designs the test and
  interprets the result; a designer or tech lead may run
  it.
- **Opportunity tree:** the CPO is the primary author until
  a PM is hired; the trio still reviews it weekly.
- **Delivery-track slices:** the CPO does *not* pick up
  eng tickets. But the CPO does own the PRD (Lecture 3),
  the Figma mockup (Lecture 4), and the microcopy pass —
  and personally reviews shipped slices with the team.
- **The Thursday sync and the Friday review:** the CPO
  attends, and — this is the one meeting the CPO chairs —
  the Thursday sync. The sync is where the CPO makes the
  call to graduate an opportunity from discovery to
  delivery, or send a delivery slice back to discovery.

Cagan is emphatic in *Empowered* that the product manager's
role is *not* to be a project-manager for the team's
delivery, but to be the *value / viability owner* who does
discovery continuously and personally. At CPO scale, that
translates to the CPO being visibly the one in the interview
room and visibly the one writing the six-pager — not the one
grooming the Jira board
([Cagan & Jones, *Empowered*, Chapter 9: "Product Manager"](https://www.svpg.com/empowered-ordinary-people-extraordinary-products/)).

## A worked example — a dual-track week

The example below is synthetic, for shape only, and does not
describe a real company. Substitute your team, product, and
day-of-week naming to fit.

> **Team:** four engineers, one product designer, one
> founding CPO. Product: an AI-native evidence-collection
> tool for mid-market compliance teams (the mod-003 Lecture
> 1 example, continued).
>
> **This week's discovery focus:** the assumption from last
> week's tree — *compliance teams will accept an
> LLM-generated first-draft evidence request in lieu of
> writing one themselves* — is the top-of-tree open bet.
>
> **This week's delivery focus:** the source-system
> connector for AWS Config is in flight; two engineers are
> on it. The review-workflow slice (assign / remind /
> sign-off) shipped last Friday and is on 15% of accounts
> behind a flag.
>
> - **Monday:** trio interviews a compliance analyst at a
>   mid-market SOC2 customer. Two findings: (a) the analyst
>   already uses ChatGPT to draft evidence requests and
>   would trust an in-product version if it cited the
>   source policy; (b) they *don't* want it auto-sent to
>   the source-system owner. Both go on the tree.
> - **Tuesday–Wednesday:** trio designs a five-account
>   prototype test — an unpolished Figma of an in-product
>   draft request, with a "cite source policy" affordance
>   and an explicit "send / edit / delete" gate before
>   dispatch. Runs the prototype test against three
>   accounts. Two of three would use the draft; one wants
>   the draft to *also* propose evidence questions, not
>   just the request wording. Assumption partially
>   strengthened; a new opportunity is added.
> - **Thursday:** trio meets. The LLM-drafted-request
>   opportunity graduates from discovery to delivery — the
>   trio commits to a review-and-send slice for the next
>   cycle, with a pre-registered signal (*"≥50% of drafts
>   sent as-is or lightly edited by the top-20 accounts
>   within four weeks of ship"*). The connector-flagged
>   accounts get a quick delivery-track check: are people
>   using the connector? Yes, three of four are already
>   above zero pulls; keep the ramp.
> - **Friday:** two delivery slices ship — a bug fix on
>   review-workflow, and the AWS Config connector to 15%.
>   The changelog gets two entries. The trio reviews
>   metrics from the review-workflow slice at 15%; usage
>   is at 40% of active accounts, above the pre-registered
>   signal. Ramp to 100% is approved for next week.
> - **Continuously:** the opportunity tree gets four
>   updates over the week; nothing gets deleted, one
>   opportunity gets deprecated ("customers will pay for
>   the draft feature as a $10/month add-on" — no
>   evidence, and the team explicitly agrees it's not
>   worth investigating this quarter).

Nothing in the week is a Ceremony with a capital C. Each
ritual produces an artifact and moves a specific decision.
That is what makes it a *cadence* rather than a *set of
meetings*.

## Where dual-track fails

Three failure modes to design against, all Lecture 6
anti-patterns in miniature.

- **Discovery drift.** The Monday interview happens for
  four weeks straight, then a busy week, then a launch
  week, then a hiring week, and by week 8 there are no
  interviews on the calendar. The whole model collapses.
  Counter-move: the interview is on the calendar as a
  recurring event owned by the CPO, and Friday's shipped-
  slice review is publicly cancelled if the Monday
  interview was skipped — a paired-cancellation rule that
  makes the trade-off visible.
- **Track detachment.** The discovery track runs, the
  delivery track runs, and the Thursday sync becomes a
  status meeting instead of a seam. The two tracks
  produce work that never affects each other. Counter-
  move: every graduated opportunity has a pre-registered
  signal named at the sync, and every delivery slice
  reviewed at Friday has to name which opportunity moved
  or didn't.
- **Trio collapse.** The tech lead stops attending
  interviews. The designer stops attending the Thursday
  sync. The CPO ends up doing all of discovery alone.
  Counter-move: the trio is a *named* structure with an
  attendance-visible weekly ritual. Missing two in a row
  triggers a re-negotiation, not a fourth-week absence.

## Boundaries this lecture keeps

- **Discovery mechanics** — interview craft, JTBD
  synthesis, opportunity-tree authoring, PMF measurement —
  are owned by
  [mod-001](../../mod-001-customer-discovery-to-pmf/README.md).
  This lecture assumes you can *run* those; it teaches
  the weekly *rhythm* at which they get run.
- **Prioritization and killing** — the queue the delivery
  track pulls from, the scoring, the kill discipline — is
  owned by
  [mod-002](../../mod-002-opportunity-assessment-and-prioritization/README.md).
  Graduating an opportunity from discovery to delivery
  assumes it earned its way through the queue.
- **Strategy and roadmap** — the multi-quarter shape the
  cadence executes — is owned by
  [mod-003](../../mod-003-roadmap-outcomes-and-strategy/README.md).
- **The delivery-track operating model** — Shape Up vs
  weekly kanban — is Lecture 2. This lecture leaves the
  delivery track under-specified deliberately; Lecture 2
  picks the shape.
- **PRD form, mockup craft, agentic UX loops, and anti-
  patterns** are Lectures 3 through 6.
- **DORA metrics and delivery-cadence engineering** are
  level-25 work owned by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum);
  the CPO consumes the numbers.

## Takeaways

- Dual-track is *two continuous tracks*, discovery and
  delivery, run by the *same product trio*, on the *same
  weekly cadence*. It is not a phase model, not a two-
  team model, not water-Scrum-fall.
- Torres's non-negotiable is the **weekly customer
  touchpoint**. Cagan's non-negotiable is that discovery
  is the trio's *continuous* job, not a project. Both
  live inside the same rhythm.
- The **seam** between the tracks is a Thursday-shaped
  sync plus an always-live opportunity solution tree.
  Without the seam, discovery and delivery decouple.
- The founding CPO does more of the discovery track
  personally than a later-stage CPO does — in the
  interview room, on the tree, at the sync — and does
  not touch the delivery-track ticket queue.
- Design against discovery drift, track detachment, and
  trio collapse; each has a specific counter-move that
  goes into the cadence artifact.

Lecture 2 picks the *delivery-track operating model* —
Shape Up vs weekly-ship kanban — that the delivery half
of this rhythm actually runs inside.
