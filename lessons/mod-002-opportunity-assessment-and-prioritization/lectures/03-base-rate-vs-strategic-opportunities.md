# Lecture 3 — Base-rate vs strategic opportunities, and cadence routing

## The setup

Look at any product's prioritization queue and two shapes of item are
mixed together on the same list:

- **Base-rate opportunities.** *Improve the checkout drop-off from 34%
  to 40%. Lift week-4 retention on the mobile cohort by two points.
  Reduce time-to-first-value by half.* These have a reference class —
  other funnels, other retention curves — an established measurement
  regime, and a plausible range of outcomes you can predict *before*
  running the experiment.
- **Strategic opportunities.** *Open the API to third-party developers.
  Ship a marketplace surface. Add an enterprise tier at 10× the SMB
  price.* These change what kind of company you are. There is no
  reference class inside your product — the outcomes are wide, the
  measurement is delayed, and the decision is largely a judgment about
  the thesis, not a score off a formula.

If you rank both on the same weekly spreadsheet with the same scheme, the
base-rate items will win every time. They have crisper numbers, faster
feedback loops, and higher measured confidence. Strategic items — which
by definition don't yet — will look like bad bets and get starved. Six
quarters later you have squeezed 40 basis points out of every funnel and
your product is exactly the same shape as when you started, while a
competitor shipped the new surface and ate your growth.

This lecture gives you the vocabulary to separate the two kinds of item
and the cadence to fund them differently.

## Where the distinction comes from

The idea that some decisions have a reference class and some don't isn't a
product-management invention. Kahneman's *outside view* — that
predictions ground themselves in the distribution of outcomes for similar
past projects, not in the internal narrative of *this* one — is the
canonical statement. He named the failure of relying on the inside view
the *planning fallacy*
([Kahneman, *Thinking, Fast and Slow*, Farrar, Straus and Giroux, 2011,
Chapter 23, "The Outside View"](https://us.macmillan.com/books/9780374533557/thinkingfastandslow)).
Reference-class forecasting is the operational form of the outside view;
Bent Flyvbjerg formalized it for large infrastructure decisions and it
maps directly to base-rate product work
([Flyvbjerg, "From Nobel Prize to Project Management: Getting Risks
Right," *Project Management Journal*, August 2006 — flyvbjerg.plan.aau.dk](https://arxiv.org/abs/1302.3642)).

Strategic opportunities have no reference class *by construction* — that's
what makes them strategic. Andy Grove drew the corresponding
management-time distinction: some decisions are *high-leverage strategic
inflection points* that reshape the business, and the ones that require
the CEO's (or CPO's) direct attention are the ones your subordinates
cannot make because they don't have your context
([Grove, *High Output Management*, Vintage, 1983/1995,
Chapter 4, on high-leverage activities and the exception principle](https://www.penguinrandomhouse.com/books/158477/high-output-management-by-andrew-s-grove/)).

The product-specific overlay is the *Three Horizons* framing McKinsey
codified in *The Alchemy of Growth* — Horizon 1 (defend and extend the
core), Horizon 2 (build emerging opportunities), Horizon 3 (create
options for future growth) — where each horizon needs a different
funding cadence, different metrics, and different tolerance for
uncertainty
([Baghai, Coley & White, *The Alchemy of Growth*, Basic Books, 2000 —
McKinsey summary at mckinsey.com/business-functions/strategy-and-corporate-finance/our-insights/enduring-ideas-the-three-horizons-of-growth](https://www.mckinsey.com/business-functions/strategy-and-corporate-finance/our-insights/enduring-ideas-the-three-horizons-of-growth)).

## A field test: is this a base-rate opportunity?

Apply four filters. If three or more are *yes*, it's base-rate; treat it
accordingly. If two or more are *no*, it's strategic and should not
share a queue with the base-rate work.

1. **Do I have a reference distribution?** Do I know, roughly, what a good
   / average / bad outcome for *this kind of change* looks like on this
   surface? Funnel-step optimizations: yes (industry benchmarks; your own
   history). New pricing tier: no (n=1 launch, sample size zero).
2. **Can I read the result in weeks?** Base-rate items land on a metric
   whose weekly cohort is already big enough to detect the change with
   your usual instrumentation. Strategic items land on a metric whose
   cohort is small, delayed, or not yet defined.
3. **Would a competent PM outside this company make roughly the same
   call?** Base-rate calls are largely craft — a competent outsider with
   the same numbers picks similarly. Strategic calls hinge on this
   company's thesis, this founder's judgment, this segment. Different
   competent people will pick differently and both be defensible.
4. **Does killing this cost the same as never starting it?** Base-rate
   experiments have low, symmetric cost. Strategic bets accumulate
   entanglement — infrastructure, contracts, positioning, hiring — that
   makes killing them mid-flight far more expensive than never starting.
   Lecture 5 comes back to this.

## Route by cadence

Once you've separated the two kinds of item, put them in queues with
different rhythms.

### Base-rate queue — weekly experiment cadence

- **Ranking scheme.** RICE or ICE (Lecture 2). Reach is countable;
  Impact anchors to prior experiments on comparable surfaces; Confidence
  ties to statistical power on the existing cohort size.
- **Decision cadence.** Weekly ranking, biweekly ship, monthly review of
  what actually landed vs. what was projected — the review is the
  calibration loop for next quarter's scoring.
- **Kill rule.** A pre-registered success criterion. If the experiment
  ships and misses the criterion, roll it back or move to the next idea;
  do not "give it another sprint."
- **Owner.** Ideally a product-manager-level owner, not the CPO. If the
  CPO is doing base-rate ranking themselves at a Series B, the strategic
  work is starving; delegate.

### Strategic queue — quarterly / annual bet cadence

- **Ranking scheme.** Not a spreadsheet score. Kano-style classification
  (Lecture 2) — *is this a table-stakes must-have to sell into the next
  segment, a reason-to-prefer differentiator, or a genuinely new pull?* —
  and Cagan's opportunity-assessment questions (Lecture 1) answered in
  writing. Judgment, anchored to the thesis (Lecture 6).
- **Decision cadence.** Quarterly commit-or-kill, annually re-scoped. A
  strategic bet gets a *runway* of quarters, a milestone that would
  trigger continued funding, and a milestone that would trigger the
  kill.
- **Kill rule.** Not a metric miss on a week-4 cohort — a checkpoint
  ("by Q2 we should have three signed pilot LOIs; if we have one or
  zero, we stop") tied to a leading indicator you agreed on when you
  funded the bet.
- **Owner.** The CPO, with the founder-CEO co-signing. Strategic bets
  are where the CPO's judgment is the differentiated input.

### Why the queues have to be visibly separate

- **Attention shape.** A weekly meeting that mixes an A/B test result
  and a new-tier launch will spend 55 minutes on the A/B test and 5
  minutes on the tier because the A/B test has a number and the tier
  doesn't yet.
- **Scoring pressure.** If you put strategic items in the RICE
  spreadsheet, someone will fill in a fake Reach and a fake Impact to
  make them scorable. Now you have false precision on the item that
  matters most.
- **Talent shape.** Base-rate work rewards experimental craft;
  strategic work rewards synthesis and judgment. The same person can
  do both, but not in the same hour. Separate the queues, separate the
  reviews.

## The counter-trap: don't strategy-wash the easy stuff

The mirror failure of *all base-rate, no strategic* is *all strategic,
no base-rate*. Every roadmap item gets re-framed as a "bet," everyone
talks about horizons, nothing gets measured in weeks, and the business
slowly bleeds because the funnel that funded the strategy stayed
broken. Some concrete symptoms:

- A quarter passes with no shipped experiment on the primary conversion
  surface.
- Retention has been "our biggest risk" in three consecutive board decks
  and nothing on the roadmap is dedicated to it.
- The strategic queue has 12 items and the base-rate queue has 3.

The fix is not more strategy — it is honest categorization. Most items
on most roadmaps *are* base-rate work, and that's fine. Base-rate work
is how the company keeps the lights on while the strategic bets pay off
(or don't).

## The mixed-cadence exception: strategic bets that fund base-rate work

Some strategic bets are actually a *change of surface* whose downstream
consequence is a fresh pool of base-rate opportunities. Opening an API
is strategic; measuring which endpoints drive activation of third-party
integrators is base-rate — once the surface exists. The cadence rule
here is:

- Fund the strategic bet at the strategic cadence, with the strategic
  kill rule.
- The moment the surface is live enough to generate cohort data, spin
  up a base-rate queue *inside* that surface with its own owner and
  weekly cadence.
- Do not let the strategic-cadence conversation degrade into a
  base-rate one now that there are numbers. The strategic question
  ("is this surface working as a bet?") is a different question from
  the base-rate one ("which endpoint is the next lift?").

## Boundaries this lecture keeps

- The *content* of the company thesis — what business we are in, what
  segment we serve, what our theory of winning is — is authored at
  level 20 in
  [founder-ceo-curriculum](https://github.com/ai-startup-curriculum/founder-ceo-curriculum).
  The CPO's job is to prioritize *given* the thesis, not to write it
  alone (Lecture 6).
- The *runway math* that says how many strategic bets you can fund
  simultaneously is owned at level 40 in
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum).
  The CPO consumes the burn model and translates it into a bet count.

## Takeaways

- Base-rate opportunities have a reference class, a fast measurement
  loop, and near-symmetric cost to start/stop. Strategic ones don't.
- Route them into separate queues at separate cadences. Base-rate:
  weekly experiment loop with a scored ranking. Strategic: quarterly
  commit-or-kill with judgment anchored to the thesis.
- Never let strategic items into the RICE spreadsheet. False precision
  on the item that matters most is the worst kind of number.
- Guard both directions — under-strategic starves growth; all-strategic
  starves the funnel that pays for the strategy.

Lecture 4 takes the ranking problem up a level: how does the CPO rank
across *surfaces* — consumer, marketplace, platform, data — when each
surface has its own PM saying yes to their own queue?
