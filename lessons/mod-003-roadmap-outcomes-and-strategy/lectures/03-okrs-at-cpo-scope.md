# Lecture 3 — OKRs at CPO scope, not as a Jira replacement

## The setup

Objectives and Key Results have two failure modes that show up
almost immediately when a founding CPO adopts them. Both are so
common they are worth naming before the mechanics.

**Failure mode one — OKRs as Jira with a heavier ceremony.** The
team's OKR sheet becomes a list of features the team was going to
ship anyway, each with a percentage-complete number attached. The
key results read as *shipped 8 of 12 planned integrations* rather
than *moved the outcome the integrations were supposed to move*.
The OKR review becomes a status update. Nobody has learned anything
they wouldn't have learned from the standup, and the ceremony has
absorbed a workday a quarter for a report the CEO doesn't need.

**Failure mode two — OKRs cascaded until they become
micromanagement.** The CPO's OKR is at the CPO's scope. Then it
gets "cascaded" into a team OKR that is a subdivision of the CPO's,
then into an individual OKR that is a subdivision of the team's.
By the time the cascade reaches an engineer, their OKR is a task
list — and the discovery loop is dead because there is no room
for what discovery actually finds to change anything.

Both failure modes trace to the same root cause: the OKR was
treated as an execution-tracking tool rather than an
**outcome-declaration tool.** This lecture puts OKRs back in their
intended role — a CPO-scope commitment to a *measurable outcome
this quarter* — and specifically not a substitute for the roadmap
or the delivery plan.

The vocabulary comes from Andy Grove's *High Output Management*
(where the OKR mechanic originates in mid-1970s Intel),
popularized by John Doerr's *Measure What Matters* (Portfolio,
2018 — [whatmatters.com](https://www.whatmatters.com/the-book)),
and taught with the most useful anti-patterns catalog by Christina
Wodtke in *Radical Focus* (2nd ed., 2021 —
[eleganthack.com/the-art-of-the-okr](https://eleganthack.com/the-art-of-the-okr/)).
The mechanics below are all standard; the *scope* application to
the CPO's role is the thing this lecture teaches.

## What an OKR actually is

An OKR is two things. The **Objective** is a qualitative direction
of change — the sentence that says what the world will look like
different if this quarter goes well. The **Key Results** are the
two to five measurable outcomes that would tell you the objective
was actually achieved. Doerr's short form: "the O is what you want
to accomplish; the KRs are how you'll know you got there"
([Doerr, *Measure What Matters*, Portfolio, 2018, Chapter
1](https://www.whatmatters.com/the-book)).

Two features of the mechanic that are load-bearing and often lost:

- **Key results are outcomes, not milestones.** *"Ship review
  workflow v1 by end of Q2"* is a milestone; *"reduce median
  collection-loop time from 32 days to 18 days in the top-20
  accounts by end of Q2"* is a key result. Milestones are
  *inputs* to a KR — a way you might move it — not the KR
  itself.
- **The score is a signal, not a grade.** Wodtke and Doerr both
  argue for the 0.7-target norm: a well-authored KR should land
  around 0.7 in expectation, so 1.0 signals the target was too
  soft and 0.4 signals the target was too aggressive. If everyone
  is at 1.0 every quarter, the ceremony has degraded into a
  soft-commitment ritual and the outcome discipline is gone
  ([Wodtke, *Radical Focus*, 2nd ed., Cucina Media, 2021,
  Chapter on "How to Set OKRs"](https://eleganthack.com/the-art-of-the-okr/)).

## Where the CPO's OKRs sit

There are three separable OKR scopes in a startup product
organization, and confusing them is where cascade-as-micromanagement
begins:

1. **Company OKRs** — set by the founder-CEO, one to three of
   them, one to two years' cadence typically re-declared quarterly.
   The company OKRs are what everyone else's OKRs should
   *ladder to* — but "ladder to" is not the same as "be a
   subdivision of."
2. **CPO / functional OKRs** — the CPO's own quarterly
   commitments about what the *product* will do to move the
   company outcomes. Two to four objectives, each with two to four
   key results. These are the roadmap outcomes from Lecture 2
   expressed as declared commitments the CPO is accountable for.
3. **Team OKRs** — the individual product-team commitments,
   authored by the team lead / PM with the CPO. These are *not*
   subdivisions of the CPO OKRs; they are the team's own take on
   how to move the outcome the CPO has declared. The team's KRs
   are typically at a finer grain, the team's O may or may not
   copy the CPO's O verbatim, and — importantly — the team is
   allowed to author KRs that do not appear in the CPO's OKRs
   at all if the team has surfaced a finer-grained outcome the
   CPO's roadmap didn't name.

Individual OKRs are usually a mistake at startup scale and are not
covered here. Grove himself was skeptical of them; Wodtke argues
against them explicitly. Individual performance is what one-on-ones
and career growth are for; it is not what a quarterly outcome
commitment is for.

## What CPO-scope OKRs are for

The CPO's OKRs are a declaration to three audiences:

- **To the founder-CEO and board.** *This quarter, these are the
  product outcomes I am on the hook for.* The board can read the
  KRs and know, at the end of the quarter, whether the product
  layer moved the company outcomes as planned. The KRs are the
  short form of the roadmap for a board reader who does not want
  to open the whole strategy document.
- **To GTM / eng / design peers.** *These are the outcomes I am
  organizing product capacity around; these are the outcomes I
  will trade off for; these are the outcomes I will not chase
  even if you ask.* Peer-level OKRs are how a CPO stays aligned
  with a sales leader whose own OKRs are quota-shaped without
  quietly becoming a customer-request queue.
- **To the product teams.** *These are the outcomes I am
  accountable for at my scope; here's the room your team's OKRs
  can breathe within.* The CPO OKR is a *canopy*, not a mold —
  it defines the outcome space the team OKRs sit inside without
  authoring the team's KRs for them.

Each audience reads a slightly different subset of the same set of
sentences. This is why Lecture 5's three-audience read-out
discipline applies to OKRs as well as the roadmap.

## Authoring CPO-scope KRs

The rule of thumb, distilled from Doerr and Wodtke and used
throughout the exercises: **write KRs as customer or business
outcome changes with a current value, a target value, and a
horizon** — the same three properties an outcome on the roadmap
needs.

The template that keeps first-time CPOs from drifting into
milestones:

> By [end of Q3], we will have moved [named metric] from
> [current value] to [target value] for [named segment or
> cohort], as measured by [named instrument / dashboard].

A worked pair of examples, continuing the synthetic compliance
strategy:

**Bad — milestone-shaped KRs:**

> **Objective:** Deliver the collection-loop v1.
>
> - KR1: Ship six connectors in Q2.
> - KR2: Launch review workflow v1 by end of Q3.
> - KR3: Onboard 10 accounts to the new workflow.

These are outputs with a KR label. There is no outcome number
attached; the strategy could be entirely wrong and these could
still all be 1.0.

**Better — outcome-shaped KRs:**

> **Objective:** Make the mid-market evidence-collection loop the
> first thing customers point to when they compare us to the
> spreadsheet workaround.
>
> - KR1: Move median collection-loop time from 32 days to 14 days
>   for the top-40 mid-market accounts, measured on the audit-cycle
>   dashboard, by end of Q3.
> - KR2: Grow the fraction of top-20 accounts that have retired
>   the collection spreadsheet from 5% to 40%, measured by the
>   monthly account-review survey, by end of Q3.
> - KR3: Reduce escalations tagged *"cannot find evidence"* from a
>   weekly average of 12 to a weekly average of ≤3, measured on
>   the support tag dashboard, by end of Q3.

The three KRs are all outcomes, all instrumented, all with a
falsifier baked in (the 0.7 grading norm). A team can and should
name the milestones underneath — connectors, workflow, dashboards —
but those live on the *delivery plan*, not the OKR.

## The Doerr / Wodtke rules the CPO should honor

Because these are widely-published, quickly summarized, and easy
to violate accidentally:

- **Two to four Os, two to four KRs each.** More than that at CPO
  scope is a signal that the *strategy* has not yet done the
  work of concentrating the guiding policy from Lecture 1. If you
  have seven objectives, six of them are non-load-bearing.
- **Aspirational vs committed.** Doerr distinguishes *committed*
  OKRs (0.9–1.0 is expected, missing is a fire drill) from
  *aspirational / stretch* OKRs (0.6–0.7 is expected, 1.0 is
  overachievement). A CPO's board-visible KRs are typically
  committed; strategic-bet KRs may be aspirational. Mark which
  are which; do not have all your KRs be one flavor
  ([Doerr, Chapter 5, "Stretch: The DHL / Google Chrome
  Chapter"](https://www.whatmatters.com/the-book)).
- **Confidence checks at midpoint.** At around week 6 of the
  quarter, each KR gets a confidence number — 1–10 — for
  landing on-plan. Wodtke's "OKR ceremonies" chapter treats this
  as the mechanism that keeps the OKR from being a start-of-
  quarter fire-and-forget
  ([Wodtke, *Radical Focus*, 2nd ed., "The Rhythm of the OKR
  Cycle"](https://eleganthack.com/the-art-of-the-okr/)).
- **Retros with an honest score.** End-of-quarter score is the
  learning artifact, not the performance rating. If the score
  gets used to grade individuals, teams learn to sandbag the KRs
  and the outcome discipline dies quietly within two quarters.

## What CPO-scope OKRs are *not* for

Naming what the OKR is not for is as important as naming what it
is for. The three most common accidents:

- **Not a task tracker.** OKRs do not enumerate features to
  ship. Features are in the delivery plan
  ([mod-004](../../mod-004-discovery-delivery-cadence/README.md)).
  The KR is the outcome; the feature list is the plan to move it.
- **Not a stack rank of the team's Jira board.** If your KRs
  are the top five items in the sprint backlog, you have written
  the sprint backlog twice.
- **Not the mechanism to hold a team accountable to a specific
  ship date.** Delivery commitments live on the delivery plan.
  The KR is *"the outcome we would need to see, however you
  chose to move it"* — teams that own the KR own the how, or
  they are not owning the outcome.
- **Not a substitute for the strategy.** If you can read the
  KRs but not the strategy, you know what the CPO is being
  measured on this quarter — you don't know why those measures
  matter. The KRs *ladder from* the strategy; they do not
  replace it. A KR without a strategy behind it is metric
  chasing.

## The cascade problem — and how to prevent it

The single most common OKR failure is what Wodtke calls
*cascading*: the CPO writes an O, the team copies half of it as
their O and refines the KRs, an engineer copies half of the
team's and refines further, and by the time the outcome
declaration reaches the person doing the work it is a Jira
ticket with a fancy header. The discovery loop from mod-001 dies
because there is no room for what discovery *finds* to change
what a team's KRs say.

The concrete preventions:

- **Do not require identical Os across scopes.** The CPO's O is
  a CPO-scope claim; a team's O can be either the same (they're
  the primary team on it), a narrower version (they're the
  primary team on one KR under the CPO's O), or an entirely
  different O that supports the CPO's canopy (they're moving a
  measurable input to the CPO's outcome without owning the
  outcome itself).
- **Allow team KRs that do not appear in the CPO's KRs.** The
  team may have surfaced a finer-grained outcome — activation,
  latency, a specific segment — that supports the CPO KR
  without being a subdivision of it. Grant this; it is where
  the discovery loop actually surfaces.
- **Do not translate KRs into task counts.** *"Complete 40 story
  points of connector work"* is not a KR. It is an input.
  Inputs live in the delivery plan.
- **Grow the strategy layer, not the OKR count.** If team OKRs
  keep bloating to cover cases the CPO's OKRs miss, the
  problem is usually a strategy that is not concentrating —
  send it back to Lecture 1.

## What the OKR ritual actually is

The value of OKRs at CPO scope is not the sheet. The sheet is
the artifact of a ritual — quarterly authoring, midpoint
confidence check, end-of-quarter score-and-learn — that forces
the CPO to *commit outcomes in writing to three audiences*, and
to defend those commitments at the same three audiences a
quarter later. The ritual is where the discipline is; the
software is where teams cargo-cult.

If your OKR sheet is filled in every quarter and the KR scores
are always in the 0.9–1.0 band and nobody ever escalates a KR
at the midpoint, the ritual is dead even if the artifact looks
alive. That is the state Wodtke's *Radical Focus* was written
against and the state most founding-CPO OKR implementations
drift to within a year.

## Boundaries this lecture keeps

- **KPI trees and product-analytics regimes** — activation,
  retention, cohort curves, the funnel — are the subject of
  [mod-005](../../mod-005-metrics-experimentation-and-ai-evals/README.md).
  KRs *use* those instruments; they do not build them.
- **Delivery-plan scheduling** — sprint rhythm, ship dates,
  discovery-delivery cadence — is
  [mod-004](../../mod-004-discovery-delivery-cadence/README.md).
- **Company-level OKR authoring** — the founder-CEO's
  quarterly commitment to the board — is level-20, owned by
  [founder-ceo-curriculum](https://github.com/ai-startup-curriculum/founder-ceo-curriculum).
  The CPO consumes those; the CPO authors the product-scope
  layer under them.
- **Individual performance management** — one-on-ones, career
  growth conversations, performance reviews — is level-50,
  owned by
  [startup-operations-governance-curriculum](https://github.com/ai-startup-curriculum/startup-operations-governance-curriculum).
  OKR scores are not performance ratings.

## Takeaways

- CPO-scope OKRs are **outcome declarations** at the CPO's
  scope — two to four Os, two to four KRs each, each KR an
  instrumented change in a customer / business number. They are
  the short form of the roadmap for a reader who does not want
  the whole strategy document.
- KRs are outcomes with a current value, a target value, a
  horizon, and a named instrument. Milestones — *"ship X by Y"*
  — are inputs to KRs and belong in the delivery plan, not the
  OKR sheet.
- Do not cascade Os and KRs mechanically down to individuals.
  Team OKRs *ladder from* the CPO's, not *subdivide* them, and
  should be free to name outcomes the CPO's OKRs did not.
- Distinguish committed vs aspirational; use the 0.7-target
  norm; run midpoint confidence checks; retrospect honestly. The
  ritual is the discipline; the sheet is the artifact of the
  ritual.

Lecture 4 pulls up a level to the platform-vs-point-product bet
that shapes what outcomes the roadmap even *has*.
