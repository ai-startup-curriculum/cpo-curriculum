# Exercise 2 — Shape Up vs weekly-kanban choice drill

**Time:** ~2 hours. **Deliverable:** one operating-model
choice memo defending Shape Up vs weekly-ship kanban for
the team you named in Exercise 1, with named failure
modes and pre-registered re-choice signals.

## Purpose

Make the *choice* between the two delivery-track operating
models that survive at the 3–8-engineer scale — Basecamp's
Shape Up (six-week appetite + cool-down) or weekly-ship
kanban (WIP-limited, no fixed iteration) — for a specific
team, on the record, with the reasoning you'd walk into a
founder-CEO conversation with. The choice memo becomes the
delivery half of the Exercise 1 cadence artifact, and the
input Exercise 3's PRD is written against.

## Use the team from Exercise 1

Do not rescope. Use the same team, the same product, the
same discovery maturity. The whole point is to make the
operating-model choice *for that team*, not for an
abstract team. If the Exercise 1 team-shape has changed
in your head since you wrote it, update Exercise 1 first
and re-submit.

## What the choice memo must contain

Two to three pages. Adopt the shape from
[Lecture 2](../lectures/02-shape-up-vs-weekly-kanban.md),
in the following order:

### 1. Team context recap (quarter page — consumed)

- **Team shape** consumed from Exercise 1: trio,
  engineering headcount and seniority, product surface,
  discovery maturity, AI-substrate intensity.
- **Roadmap horizon consumed from mod-003.** One
  paragraph on what the team is trying to move in the
  next quarter — the outcomes-based reading of the
  next 12 weeks. If mod-003 is not yet done, one
  paragraph on the same shape.

### 2. The six-signal read (one page)

Walk the [six signals from Lecture 2](../lectures/02-shape-up-vs-weekly-kanban.md#the-five-signals-that-pick-a-model)
for your team, honestly:

- **Team stability.** How interrupt-heavy is the team?
  Score: low / moderate / high. Cite evidence — an
  on-call rotation that eats N eng-days per week, a
  customer-escalation pattern that pulls the senior
  engineer weekly.
- **Discovery maturity per bet.** Do you have shaped
  pitches — problem statement, appetite, fat-marker
  solution sketch, rabbit holes — for the *next three*
  bets on the roadmap? Score: shaped / partially
  shaped / not shaped.
- **Scope-cut-ability of the typical unit of work.**
  For the last three bets shipped (or three plausible
  next bets), was each descope-able into a smaller
  useful cut? Score: yes / mixed / no.
- **Product-team autonomy vs CPO involvement.** Can
  the team make scope calls inside a cycle without
  escalation? Score: empowered / partially / not.
- **AI-substrate iteration density.** Is the primary
  surface AI-substrate-heavy and does it need weekly-
  or-faster iteration? Score: yes / partial / no.
- **Team shape.** How many engineers, arranged into
  how many concurrent bets? Score: fits Shape Up
  1–2 bet teams / fits kanban WIP-limited flow / other.

Do not fake-precision the read. If you are uncertain on
a signal, mark it "uncertain" and name what you'd want
to know.

### 3. The choice (half page)

Name the model — Shape Up or weekly-ship kanban — and
defend it. Two paragraphs:

- **Why this model.** Which of the six signals were the
  decisive drivers, and which were secondary. If the
  signals point in different directions (common), which
  did you weight most heavily and why?
- **Why not the other.** Which failure mode of the
  *other* model was the tie-breaker? If Shape Up would
  fail because interrupts break the six-week appetite,
  say so. If kanban would fail because scope keeps
  bloating past a week, say so.

### 4. The operating rhythm (half page)

Concrete: what the delivery track's week (or six-week
cycle) actually looks like for your team.

- **If Shape Up:** name the cycle length (usually 6
  weeks + 2 weeks cool-down), the shaping owners (usually
  CPO + eng lead + sometimes founder-CEO), the bet
  meeting attendees and cadence, and the team shape per
  bet (usually 1 designer + 2 engineers). Name the
  cool-down usage explicitly — what does the team do
  during cool-down?
- **If weekly kanban:** name the WIP limit (usually 3–5
  concurrent items across the team), the Monday commit
  ritual, the Friday ship review ritual, and the queue-
  owner (the CPO). Name the cycle-time SLA — "most
  items ship within a week" or similar — and what
  triggers a re-shape into Shape Up.

### 5. Named failure modes and their counter-moves (half page)

From
[Lecture 2](../lectures/02-shape-up-vs-weekly-kanban.md#failure-modes--shape-up)
[and](../lectures/02-shape-up-vs-weekly-kanban.md#failure-modes--weekly-kanban),
name the three failure modes of the model you chose,
and — for each — the *specific rule* you're building
into the cadence that prevents it. Not "we'll be
disciplined." A rule ("extension decisions are made
publicly at the next bet meeting with a named cost").

### 6. Re-choice signals (quarter page)

Pre-register the signals that would tell you the choice
was wrong and it's time to switch models. Examples:

- *"Three consecutive Shape Up cycles overrun their
  appetite — switch to kanban to force smaller
  commitments."*
- *"WIP consistently balloons past 5 items and the
  team can't hold the limit — switch to Shape Up so
  the appetite discipline replaces WIP-holding as the
  binding constraint."*
- *"Deploy frequency drops below one ship per week
  for four weeks running — the operating model isn't
  producing the cadence we chose it for; audit."*

Two or three named signals with named horizons.

### 7. DORA cadence-check (quarter page — consumed)

Consumed from the CTO / eng lead. What is the team's
current **deploy frequency** (a DORA metric owned at
level-25 by
[cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum))?
If it is below one deploy per week today, note the gap
between what the operating model *should* produce and
what the pipeline actually does. If the pipeline is the
bottleneck rather than the model, name that — no
operating-model choice fixes a broken deploy pipeline.

## Starter guidance

- **Do not pick "hybrid" as an escape.** Hybrids exist
  and are common — a Shape Up stable half + kanban
  AI-substrate half — but if you go hybrid, name the
  *split* explicitly (which surfaces on which model)
  and pass the six-signal read separately for each
  half. Vague hybrids are how the choice silently
  becomes "we didn't decide."
- **Steelman the model you didn't pick.** Write the
  version of the memo that picks the other model
  before you commit. If the other version reads
  plausibly, the choice you made was under-defended.
- **Interrupt-heavy environments almost always want
  kanban.** Shape Up's six-week appetite depends on
  the same trio staying on the same bet for six
  weeks uninterrupted. If your team routinely gets
  pulled into support, don't pretend Shape Up will
  work.
- **AI-substrate iteration density is a real
  driver.** If your product's primary surface is
  LLM-substrate and you need daily prompt / eval
  iteration, kanban dominates by default. Shape Up
  tolerates it poorly.
- **Consult the CTO on the deploy pipeline first.**
  If the team can't deploy weekly regardless of
  operating model, the pipeline is the bottleneck and
  the operating-model choice is downstream of a
  bigger fix.

## The re-choice signal discipline

The point of the pre-registered re-choice signals is
to make the *decision to switch* a matter of observed
data, not politics. Without pre-registered signals,
switching operating models becomes a founder-CEO
argument every six months. With them, the trio just
notices the signal hit and re-decides.

At least one of the signals should be **DORA-shaped**
— deploy frequency, lead time, or change-failure rate
— because those numbers are hard to argue with. Consume
from the CTO.

## Acceptance criteria

- Team context recap cites Exercise 1 team-shape and
  mod-003 roadmap horizon (or a stand-in one-
  paragraph shape).
- Six-signal read is honestly scored; uncertain
  signals are marked as such.
- The choice paragraph names the model and defends
  with which signals were decisive, and which failure
  mode of the *other* model was the tie-breaker.
- Operating rhythm section is concrete: named
  meetings, named cadences, named owners.
- At least three failure-mode counter-moves are
  named, each as a structural rule (not a cultural
  aspiration).
- At least two pre-registered re-choice signals,
  each with a horizon.
- DORA cadence-check section notes current deploy
  frequency and names whether the pipeline is a
  bottleneck.

## Common failure modes

- **Choice-by-inertia.** "We already do Scrum" is not
  a choice; it's the vacuum Lecture 2 argues against.
  Neither Shape Up nor kanban is Scrum.
- **Fake-precision on the signals.** Scoring team
  stability as "moderate" without evidence, or
  autonomy as "empowered" when the team escalates
  every scope call to the CPO. Cite evidence.
- **Failure modes as culture.** "We'll cut scope when
  we need to" is not a counter-move. "At the bet
  meeting, name which scope is first-to-cut, second,
  third" is a counter-move.
- **Re-choice signals as never-triggered.** Signals
  that would never hit in practice are decorative;
  pick signals that *could* realistically trigger
  within a quarter or two.
- **Ignoring the pipeline reality.** Picking a weekly-
  ship kanban when the pipeline deploys biweekly is
  optimistic; consult the CTO first.
- **Hybrid as the default.** "We'll kind of do both"
  is not a choice. If hybrid, name the split
  explicitly.

## Source alignment

Shape Up derives from Ryan Singer, *Shape Up: Stop
Running in Circles and Ship Work that Matters*,
Basecamp, 2019 —
[basecamp.com/shapeup](https://basecamp.com/shapeup).
Kanban's shape derives from David J. Anderson, *Kanban:
Successful Evolutionary Change for Your Technology
Business*, Blue Hole Press, 2010 —
[leankanban.com/kanban-book](http://leankanban.com/kanban-book/);
the queue and WIP-limit mechanics from Don Reinertsen,
*The Principles of Product Development Flow*,
Celeritas, 2009 —
[celeritaspublishing.com](https://celeritaspublishing.com/product/the-principles-of-product-development-flow/).
Cagan's agnostic-but-empowered stance is in *Empowered*
Chapter 24 —
[svpg.com/empowered](https://www.svpg.com/empowered-ordinary-people-extraordinary-products/).
DORA metrics derive from Nicole Forsgren, Jez Humble &
Gene Kim, *Accelerate*, IT Revolution, 2018 —
[itrevolution.com/accelerate-book](https://itrevolution.com/product/accelerate/)
— and the ongoing program at
[dora.dev](https://dora.dev/); the CTO curriculum owns
the SRE-side authoring, per the
[mod-004 README](../README.md#boundaries-this-module-keeps).
