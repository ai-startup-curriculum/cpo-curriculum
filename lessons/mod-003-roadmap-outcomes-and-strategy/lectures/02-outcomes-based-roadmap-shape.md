# Lecture 2 — Outcomes-based roadmaps: Now / Next / Later and objective-oriented

## The setup

A first-time founding CPO's first roadmap is almost always a
calendar: Q1 ships feature A, Q2 ships feature B, Q3 ships the
integration platform. It looks disciplined. It sorts nicely on a
Gantt chart. And it puts the CPO in an unwinnable position within
a quarter: either the ship dates hold and the numbers do not
move — because the wrong features were on the calendar — or the
numbers move and the ship dates slip, and the CPO gets asked why
they missed the plan.

This lecture is the alternative shape. Melissa Perri names the
first version the **build trap**: a product organization that has
converted its strategy into a shipment schedule, and now grades
itself on ship velocity because that is the only thing left to
measure ([Perri, *Escaping the Build Trap*, O'Reilly, 2018, Chapter
3](https://www.oreilly.com/library/view/escaping-the-build/9781491973783/)).
The escape is a roadmap authored in **outcomes** — customer or
business behaviors the product should change — with **outputs**
(the features you plan to ship) held explicitly downstream of
the outcomes and revisable when the discovery loop learns
something.

The two most-used outcome-roadmap shapes are Janna Bastow's **Now
/ Next / Later** (ProdPad, 2013 onward — see [prodpad.com/blog/tag/now-next-later](https://www.prodpad.com/blog/tag/now-next-later/))
and the **objective-oriented roadmap** popularized by Marty
Cagan's *Empowered* and Perri's own work — a roadmap organized
around product outcomes with named teams accountable for each
([Cagan, *Empowered: Ordinary People, Extraordinary Products*,
Wiley, 2020, Chapter
25](https://www.svpg.com/empowered-ordinary-people-extraordinary-products/)).
Both are valid; the pick depends on the stage.

## The three questions a roadmap has to answer

Regardless of shape, a roadmap has to answer three questions for
its three primary readers:

1. **What outcomes are we trying to move, and in what sequence?**
   (This is what the board and the CEO want to know.)
2. **What are we currently investing engineering / design capacity
   in, and what are we not?** (This is what GTM, eng, and design
   want to know — GTM to sell against it, eng to sequence
   architectural work, design to plan research.)
3. **How is my work connected to a company outcome?** (This is
   what individual contributors want to know — and if the roadmap
   can't answer it in a sentence, morale and retention will show
   you soon enough.)

A calendar-shaped roadmap answers question 2 only. An outcomes-
based roadmap answers all three, at the cost of no longer
promising a specific ship date for a specific feature to
question 2's reader — which is the reason it takes discipline to
adopt.

## Now / Next / Later — the pre-scale default

Bastow's **Now / Next / Later** is deliberately austere. It is a
three-column artifact:

- **Now** — the outcomes currently being worked on, with the
  discovery-and-delivery work in flight. Items in Now are
  committed: a team is on them, capacity is allocated, and the
  falsifier (from mod-002 Lecture 1) is being watched.
- **Next** — the outcomes we will *probably* work on next, in the
  ranked order we currently believe they should be worked on.
  Items in Next are not committed. They are subject to
  reprioritization if the Now cohort's evidence moves.
- **Later** — the outcomes we believe are in the strategy but not
  yet close enough to invest capacity in. Items in Later are
  visible so stakeholders can see the direction without being able
  to demand a date.

The three columns explicitly do not correspond to Q1 / Q2 / Q3.
That is the mistake most teams make on adoption. **Now** is not
"this quarter"; it is "the things a team is currently on." **Next**
is not "next quarter"; it is "the things we think we would move
onto when the current things finish or falsify." The temporal
looseness is the point — it is what lets the outcomes discipline
survive contact with a discovery loop that learns something
unexpected in week five.

Bastow's own framing: the roadmap is a *conversation prompt*, not
a commitment device
([Bastow, "The Now / Next / Later Roadmap," ProdPad —
prodpad.com/blog/tag/now-next-later](https://www.prodpad.com/blog/tag/now-next-later/)).
The stakeholder who wants a date is asking the wrong tool for the
answer; the answer to *"when will feature X ship"* is not on a
strategy roadmap and never should be. It lives in the delivery
plan (mod-004).

**When Now/Next/Later fits.** Pre-Series-A, or any stage where the
discovery loop is still visibly changing the picture. Small
product teams (one to four squads). Companies whose CEO can be
brought along on the "no dates on the strategy roadmap" contract.

**When it strains.** Once the company is committing to
enterprise-contract deliverables tied to specific quarters, once
regulatory or compliance work has fixed external deadlines, or
once the company has enough squads that a three-column artifact
loses resolution on who owns what. At that point the objective-
oriented variant is the next step.

## Objective-oriented roadmaps — the multi-team default

Once you have more than a handful of squads and more than one
company-level outcome you are simultaneously moving, Now / Next /
Later loses fidelity. The alternative is an **objective-oriented
roadmap** — a matrix organized around outcomes (the rows) with
teams accountable for each (the cells).

The shape, adapted from Cagan's *Empowered* and Perri's
*Escaping the Build Trap*:

- **Rows** are outcomes you want to move — the guiding-policy
  actions from Lecture 1, expressed as outcomes rather than
  outputs. *"Cut the median evidence-collection loop time from 32
  days to 14 days for the top-40 mid-market accounts by end of
  Q3."*
- **Cells** name the team or teams currently accountable for the
  outcome and, at high level, the current bet on how they'll move
  it. Not a feature list; a bet with a falsifier.
- **Columns** — where you have them — are horizons (this half,
  next half, exploratory) rather than calendar months. Some
  companies drop columns entirely and put the horizon in the cell.

The gain over Now / Next / Later is that a team ships against a
*named outcome*, not an inherited task list, and that outcome
appears once — every team looking at the roadmap can see which
outcome overlaps with theirs. The cost is that authoring is
harder: you have to have real outcomes, not just themes, or the
matrix silently becomes a themes-list wearing an outcome's hat.

**When objective-oriented fits.** Multiple squads, multiple
concurrent outcomes to move, and enough discovery-and-delivery
maturity that teams can actually own outcomes. This is the shape
most Series A → Series B product organizations move to.

## The outcome, not the output — Perri's discipline

Both shapes depend on being able to write an *outcome*. Perri's
own framing, worth restating because most first drafts still
fail it: an outcome is a **measurable change in customer or
business behavior**. Two tests:

1. **The audit test.** If we shipped every feature on the
   solution branch of this outcome and the outcome number did not
   move, would we still call this a success? If the answer is
   "yes, because we shipped what we planned," it is not an
   outcome — it is a set of outputs with an outcome label glued to
   the top. The outcome is the number, not the shipments.
2. **The instrumentation test.** Can we measure this outcome
   today, and if not, is the instrumentation for it *on the
   roadmap*? If neither is true, the outcome is decorative — you
   have declared it because it sounds better than the feature
   list, but you cannot tell whether it moved.

The instrumentation test is the reason mod-003 depends on mod-005
(metrics, experimentation, evals) — an outcomes roadmap without
instrumentation is a wish list with better sentence structure.

## Deprioritization is a first-class citizen on the roadmap

Most published roadmap templates hide what the roadmap *is not*
doing. This is a failure mode. The Rumelt discipline from Lecture
1 — "good strategy discards" — has to be visible on the roadmap
artifact or it will silently be re-litigated in every
prioritization dispute.

The concrete moves:

- **Now / Next / Later.** Include a fourth, explicit **Not Now**
  column or panel. Items in Not Now are things the strategy has
  explicitly deferred — customer-requested features, board-
  suggested initiatives, competitor moves — with a one-sentence
  reason and, ideally, a signal that would move them into
  consideration. *"Enterprise SSO — Not Now. We are not
  investing in the enterprise segment until we win the mid-market
  collection loop. Move-in signal: >30% of qualified enterprise
  pipeline blocked on SSO by end of Q2."*
- **Objective-oriented.** Include a **Not-Investing** row that
  lists deferred outcomes with the same reason + signal
  annotation. This makes the deferral discussable in the same
  artifact rather than hiding it in a side memo.

The point is not to make the deferrals look impressive; it is to
make them visible so they *are* actually deferred rather than
being silently added back by whichever stakeholder is loudest
this week.

## Timeframes on outcomes, not on outputs

The one place a date does belong on an outcomes roadmap is
attached to the **outcome itself**, not to the feature shipments
underneath it. *"Cut median evidence-collection loop time to 14
days by end of Q3"* is a legitimate roadmap entry with a date.
*"Ship the review-workflow UI by end of Q1"* is a delivery-plan
entry that does not belong on the strategy roadmap.

The distinction matters because dates on outputs invite the
build-trap grading (*did we ship by the promised date?*), while
dates on outcomes invite the outcome grading (*did the number
move by the promised date, and if not, what did we learn?*).
The second question is the one that keeps the strategy honest;
the first is the one that grinds down the discovery loop.

## A worked example — the same strategy, in three shapes

Continuing the synthetic compliance-tool example from Lecture 1
(names and numbers illustrative, not a case study).

**Bad — calendar-shaped:**

> **FY26 Product Roadmap**
>
> | Q1 | Q2 | Q3 | Q4 |
> |---|---|---|---|
> | Okta connector | GitHub connector | Review workflow v1 | Auditor portal v1 |
> | AWS connector | JIRA connector | Reminder engine | Enterprise SSO |
> | Slack integration | GCP connector | Sign-off UI | Data warehouse export |

You cannot tell from this what any of it is *for*, why the
ordering is what it is, or what would tell the CPO the sequence
was wrong. This is the build trap in table form.

**Better — Now / Next / Later, outcomes-shaped:**

> **FY26 Product Roadmap — Now / Next / Later**
>
> **Now (currently investing):**
> - *Outcome:* Cut median evidence-collection loop time from 32
>   days to 14 days for the top-40 mid-market accounts by end of
>   Q3. *Team:* Collection Squad. *Falsifier:* If <30% of the top
>   20 accounts have replaced the collection spreadsheet by end
>   of Q3, escalate to strategy review.
>
> **Next (probable, in believed order):**
> - *Outcome:* Grow expansion revenue from adjacent frameworks
>   (ISO 27001, HIPAA) within the same top-40 accounts by
>   producing framework-agnostic evidence-collection loops.
> - *Outcome:* Move week-1 activation for new mid-market accounts
>   from 22% to 45%.
>
> **Later (in the strategy, not yet close):**
> - *Outcome:* Auditor-facing report-authoring surface, for FY27
>   if the collection loop wins.
> - *Outcome:* Enterprise-tier readiness (SSO, IdP, audit log),
>   for FY27 if the mid-market position stabilizes.
>
> **Not Now (explicitly deferred):**
> - *Horizontal workflow-automation platform.* Move-in signal:
>   more than one top-10 account rejects the collection-loop
>   deal because they wanted an editor.
> - *Consumer-facing self-serve compliance packs.* Move-in
>   signal: none this year; deferred to strategic review FY27Q1.

**Better still — objective-oriented, for when there are more
teams:**

> **FY26 Product Roadmap — Objective-Oriented**
>
> | Outcome (with target and horizon) | Accountable team | Current bet |
> |---|---|---|
> | Cut median collection-loop time 32d → 14d (top-40 mid-market, end of Q3) | Collection Squad | Connector library (top-6 sources) + review workflow, replacing spreadsheet in-loop |
> | Move week-1 activation 22% → 45% (mid-market new-account cohort, end of Q2) | Activation Squad | Guided setup + first-connector-in-30-min, evaluated by cohort |
> | Grow expansion revenue in adjacent frameworks (top-40, +$1.2M ARR by end of H2) | Frameworks Squad | Framework-agnostic collector schema; ISO 27001 first |
> | **Not investing:** auditor-facing authoring surface, enterprise SSO, workflow-automation editor | — | Deferred to FY27; move-in signals as in Not-Now |

The two "better" shapes carry the same strategy content. The
Now/Next/Later fits a smaller team where a shared queue makes
sense; the objective-oriented fits when multiple squads need to
see their outcome next to peers'.

## Common failure modes

- **The outcome is a theme, not a change.** *"Improve
  onboarding"* is a theme; *"move week-1 activation from 22% to
  45%"* is an outcome. If the current value is missing, or the
  target is missing, or both — you have a theme.
- **The outcome is a shipment in disguise.** *"Launch enterprise
  tier"* is a shipment. *"Land $2M in ARR in the enterprise
  segment"* is an outcome. If your outcome names a launch, it is
  an output the fluffy way.
- **Every team has three outcomes.** More than one primary
  outcome per team, per horizon, is usually a symptom of a team
  that hasn't yet finished its own local prioritization. Force
  one — or split the team.
- **The Later column is a graveyard.** If items sit in Later for
  a year with no evolution, the roadmap has become a
  wish-holding artifact. Either promote them, retire them, or
  put them in Not Now with a move-in signal.
- **Now / Next / Later with dates on the columns.** If a
  stakeholder can pattern-match Now → Q1, Next → Q2, Later → Q3,
  you have re-created the calendar. Break the pattern
  deliberately: rotate Now items in and out on the discovery
  cadence, not on a quarterly boundary.

## Boundaries this lecture keeps

- **Delivery scheduling** — ship dates for individual outputs,
  PR-level sequencing, sprint rhythm — belongs on the delivery
  plan, not the strategy roadmap.
  [mod-004](../../mod-004-discovery-delivery-cadence/README.md)
  covers the delivery-plan shape.
- **OKR authoring** — the key-result mechanics that turn the
  outcomes on the roadmap into declared quarterly commitments —
  is Lecture 3.
- **Instrumentation and evals** — the measurement layer that
  makes the outcomes on this roadmap trackable — is
  [mod-005](../../mod-005-metrics-experimentation-and-ai-evals/README.md).
- **Board-facing narrative shape** — the wrapper around the
  Now/Next/Later or objective-oriented artifact when it goes into
  a board deck — is Lecture 5, with the narrative-craft depth
  itself deferred to
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum).

## Takeaways

- Pick **Now / Next / Later** at pre-scale; move to
  **objective-oriented** when you have multiple squads moving
  multiple outcomes concurrently. Both are outcome-shaped, not
  output-shaped.
- Every roadmap entry is an **outcome**: a measurable change with
  a current value, a target, and a horizon — and it survives the
  audit test (would we call this a success if the number did not
  move?) and the instrumentation test (can we measure it, and if
  not, is that instrumentation on the roadmap?).
- Make **deprioritization** first-class: a *Not Now* column or
  row with reasons and move-in signals, so the discards from
  Lecture 1 stay discarded.
- Dates go on **outcomes**, not on outputs. Dates on outputs are
  how the build trap reasserts itself.

Lecture 3 turns the roadmap outcomes into OKRs at the CPO's
scope — outcome declarations, not Jira surrogates.
