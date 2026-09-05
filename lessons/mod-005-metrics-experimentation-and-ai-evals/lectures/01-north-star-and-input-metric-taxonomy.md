# Lecture 1 — North-star metric + input metrics: designing a taxonomy that lasts 12 months

## The setup

Ask a first-time founding CPO what their product's most
important metric is, and the answer will almost always fall
into one of three shapes. The first is *revenue*: MRR / ARR
/ net new logos, a downstream financial number that moves
too slowly and too noisily to steer weekly work. The second
is *DAU / MAU*: an activity count with no relationship to
whether the users doing the activity are getting value. The
third — increasingly common in 2026 — is *the vibe
dashboard*: eight or nine numbers displayed side by side
with no hierarchy, each moved by a different team, none
diagnostic.

None of these is a metric taxonomy. A taxonomy is a
*hierarchy* — a single **north-star metric** at the top,
two to three **input metrics** underneath it that
mechanically move it, and a small set of **guardrails** the
north-star cannot be moved by breaking. Sean Ellis, writing
from a growth-marketing background, is the practitioner
most associated with the north-star framing; Andrew Chen,
writing from consumer social and marketplace backgrounds,
is the practitioner most associated with the input-metric /
growth-loop framing that goes underneath. This lecture
teaches you to author both, defend the shape, and design
against the rewrite that will otherwise be forced on you in
eight months.

## Why "the metric" needs to be a hierarchy

A single number cannot steer a product team. Two symmetric
failure modes make this concrete.

**The revenue-only shape.** The team optimizes for
next-quarter ARR. Six months in, ARR is up 40% — driven
almost entirely by three big-logo deals the sales team
pulled through with heroic discounting and one-off
implementation work. Product usage inside those accounts
is thin; renewal risk is high. The metric moved; the
underlying business did not. A revenue-only taxonomy has
no diagnostic to distinguish these outcomes, because it
only measures the downstream effect.

**The activity-only shape.** The team optimizes for DAUs.
Six months in, DAUs are up 60% — driven by a notification
loop that pulls users back to the app for interactions
that generate no lasting value. Retention in the same
period is flat or degraded; revenue has not moved. The
metric moved; the underlying business did not. An
activity-only taxonomy has no diagnostic to distinguish
"engagement that leads somewhere" from "engagement that
leads nowhere."

The move both shapes miss is to name the metric that
*mechanically links* activity to value — the metric that
goes up only when the product is doing what the user hired
it to do, at the frequency the user's job demands. That is
the north-star metric. It sits above activity and below
revenue. Everything above the north-star (revenue, growth
rate, market share) is a *downstream* number the team does
not steer directly. Everything below it (feature use,
funnel steps, session counts) is an *input* the team
steers to move the north-star.

## The north-star, defined

Amplitude's *North Star Playbook* is the most-cited
practitioner reference for the shape. Their operational
definition (paraphrasing across the current playbook
version and the older 2019 essay): the north-star metric
is *the one metric that best captures the core value the
product delivers to customers*, and it is a **leading
indicator** of long-term business success
([Amplitude, *North Star Playbook*](https://amplitude.com/books/north-star)).

Sean Ellis's earlier framing, from *Hacking Growth*, is
compatible and adds the growth-marketing framing: the
north-star is the metric that *"most accurately captures
the value your product delivers,"* and it is picked so
that the team *"is confident that if this metric goes up,
we're moving toward the outcomes we care about"*
([Ellis & Brown, *Hacking Growth*, Currency, 2017, Chapter
3: "Determining If Your Product Is Must-Have"](https://hackinggrowth.com/)).

Three tests to run on a candidate north-star:

- **The value test.** Does the metric go up only when the
  user gets value? *Number of documents shared with a
  collaborator* is a good value-test signal for a
  collaboration product; *number of documents created*
  is not, because a document created and never opened by
  a second person is (for that product) not value.
- **The action test.** Can the team meaningfully move the
  metric with product work in the next 90 days? *Number
  of paid users* fails the action test for most product
  teams — it moves with sales, pricing, and marketing far
  more than with product. *Number of activated users this
  week* passes.
- **The frequency test.** Does the metric's cadence match
  the product's natural use cadence? A weekly metric on
  a monthly-use product will look noisy and lead to false
  positives; a monthly metric on a daily-use product will
  lag and lead to false negatives. Match the metric's
  window to the user's job frequency.

The one-sentence rule of thumb: **the north-star metric is
the count of the thing your best customers would be
disappointed to lose (per whatever cadence they need it),
that the product team can plausibly move.**

## Named examples of north-star metrics

The examples below are drawn from the working literature
(the *Hacking Growth* case studies, the *North Star
Playbook* worked cases, and the practitioner writing at
[reforge.com](https://www.reforge.com/) and
[andrewchen.com](https://andrewchen.com/)). Where a
company is named, the framing appears in one of those
sources; where I say "shape," the pattern is common in the
literature and the specific company is illustrative, not
attested.

- **Airbnb** — *nights booked.* Not "revenue," not "hosts
  onboarded," not "sessions." Nights booked passes all
  three tests: users get value when they stay somewhere,
  the product team can move it, and its cadence matches
  the trip-planning window.
  ([Amplitude, *North Star Playbook*, worked
  examples](https://amplitude.com/books/north-star).)
- **Slack (shape)** — *messages sent by an active team.*
  A team-scope metric, not a user-scope one — Slack's
  value only accrues when a *team* uses it, and messages
  are the atomic unit of that value. This is the
  classical "value delivered by the product surface"
  shape.
- **Facebook (shape)** — *daily active users doing
  meaningful interactions* (comments, likes, shares — not
  passive scrolls). The "meaningful" adjective is the
  interesting move: it filters activity into
  value-generating activity, protecting the metric from
  the "engagement that leads nowhere" failure mode.
- **HubSpot (shape)** — *weekly active teams doing
  qualified inbound outreach*, for the marketing-hub
  product line. The B2B shape: the metric is scoped to
  team, and the activity is qualified by outcome
  (outbound that meets a quality bar), not raw count.
- **Amplitude itself** — *weekly learning users* (users
  who ran a query, viewed a chart, or shared a dashboard,
  weekly). Documented in their own playbook.
  ([Amplitude, *North Star Playbook*](https://amplitude.com/books/north-star).)

Common shape: a **count** of **value-bearing events**, by
**segment**, on the product's **natural cadence**. Not
revenue, not raw activity.

## Input metrics — Andrew Chen's growth-loop framing

The north-star tells you *what to move*. The **input
metrics** tell you *how it moves*.

Andrew Chen's *The Cold Start Problem*, and the growth-loop
literature at Reforge that Brian Balfour et al. teach, both
argue for the same shape: identify the two or three inputs
that *mechanically compound* into the north-star, and
manage the input metrics as the team's weekly work
([Chen, *The Cold Start Problem*, Harper Business, 2021,
Part IV: "The Ceiling"](https://andrewchen.com/the-cold-start-problem-book/);
Balfour, "The Reforge Growth Model," at
[reforge.com](https://www.reforge.com/blog)).

For most product shapes, three inputs suffice — the
"acquisition × activation × retention" decomposition (or an
equivalent with names that match the product's actual loop):

- **New activated users this week** — an *acquisition*
  input. The count of newly registered users who cleared
  the activation event (Lecture 2 defines activation).
- **Retained-user activity per week** — a *retention*
  input. The count of previously-active users doing the
  value-bearing action again this week.
- **Referred / re-engagement users this week** — a
  *loop* input. The count of users pulled back or pulled
  in by the product's growth loop (viral loop,
  content-loop, sales-outbound loop, or paid-loop —
  whichever your product actually runs on).

If your north-star is *weekly active teams doing X*, its
input decomposition might be *new teams activated this
week* × *previously-active teams active again this week*
× *teams recovered from dormancy this week*. The three
inputs mechanically compose into the north-star; the
team's weekly work is on the three inputs.

The Reforge / Chen framing is more general than
"acquisition × activation × retention": the correct
decomposition is *whichever inputs actually compound in
your product's growth model.* For a marketplace, the inputs
are supply, demand, and matching rate. For a content
product, the inputs are creator supply, consumer
consumption, and platform-loop virality. Choose the
decomposition that matches the product's actual loop, not a
template.

## Guardrails — the metrics the north-star cannot be moved by breaking

Every north-star metric can be gamed. A metric taxonomy
that stops at north-star + inputs is a taxonomy that will
be gamed by an ambitious team optimizing for the metric
they've been asked to move. Guardrails prevent this by
naming, in advance, the things the team may not sacrifice
to move the north-star.

Guardrails typically cover four dimensions:

- **Quality guardrails.** For a content product: the
  fraction of content flagged as low-quality. For an
  LLM product: the eval-set threshold from Lecture 6.
  For a B2B product: the CSAT / NPS of active users.
- **Cost guardrails.** For an AI-substrate product: cost
  per interaction (Lecture 7). For a paid-acquisition
  product: CAC / LTV. For any product where infra cost
  scales with usage: gross margin per active user.
- **User-experience guardrails.** Page-load latency
  (Web Vitals thresholds), p95 API latency, error rate,
  crash rate.
- **Trust / safety / policy guardrails.** Refund rate,
  chargeback rate, moderation-action rate, security
  incident count.

The rule: the north-star is *only credited* as moved when
no guardrail has moved out-of-bounds in the same window.
If DAU is up 20% but error rate is up 3× or the LLM eval
suite regressed 8 points, the north-star did not move; a
gaming event happened.

Kohavi, Tang & Xu's *Trustworthy Online Controlled
Experiments* is emphatic on the guardrail discipline: at
Microsoft, every experiment has a small set of *organizational
guardrail metrics* (page-load time, error rate, unsubscribes)
that any experiment can break, at which point the experiment
is not shipped regardless of the primary metric's movement
([Kohavi, Tang & Xu, *Trustworthy Online Controlled
Experiments*, Cambridge University Press, 2020, Chapter 21
on guardrails](https://experimentguide.com/)).

## The 12-month test

The exercise (Exercise 1) forces you to defend your
taxonomy against a specific question: *will this taxonomy
need to be rewritten in 12 months, and if so, why?* A
metric taxonomy that needs to be rewritten every quarter is
a taxonomy the team stops trusting — because the goalpost
moves too often to build any muscle around it, and because
each rewrite signals that the previous taxonomy did not, in
fact, capture "the value the product delivers."

Four failure modes cause a taxonomy to need rewriting
inside 12 months:

- **The metric was actually a proxy for revenue.** The
  team picked *weekly active teams* but was really trying
  to move *ARR*. When the two decouple (weekly active
  teams up, ARR flat), pressure to rewrite the taxonomy
  arrives from above.
- **The metric was defined at the wrong scope.** *DAU*
  for a B2B product where the buyer, decider, and user
  are different people. The team ships changes that move
  DAU but do not move the account-level economics; the
  taxonomy rewrites to a team-scope or account-scope
  metric.
- **The input decomposition did not match the actual
  growth loop.** Team picks *acquisition × activation ×
  retention* for a marketplace product where the actual
  loop is *supply × demand × matching-rate*. The inputs
  do not mechanically move the north-star, and the team
  is directionally lost.
- **The north-star was the metric the team *had*, not
  the metric the team *needed*.** The taxonomy was
  reverse-engineered from what the analytics tool
  reported by default. When the team wants to ship a
  change to a surface that isn't captured by the
  reported metrics, the taxonomy is silently ignored,
  and re-authored after the change.

The defense: pick the north-star from the *product's value
proposition and growth model*, not from the analytics
tool's default panel; decompose into inputs that match the
loop, not a template; scope to the right unit (user, team,
account, session); and write the guardrails at the same
time so the shape is stable under the pressure the team
will apply to it.

## The taxonomy on one page

The artifact this lecture asks you to author (in Exercise
1) fits on one page and has this shape:

```
NORTH-STAR METRIC
  <weekly / monthly / daily> <count of value-bearing event>,
  scoped to <user / team / account>, for <segment>

INPUT METRICS (2–3; each mechanically composes into north-star)
  1. <input> — moves the north-star by <mechanism>
  2. <input> — moves the north-star by <mechanism>
  3. <input> — moves the north-star by <mechanism>

GUARDRAILS (3–5; north-star is not credited if any is broken)
  - <quality> — measured as <metric>, threshold <value>
  - <cost> — measured as <metric>, threshold <value>
  - <UX> — measured as <metric>, threshold <value>
  - <trust / safety> — measured as <metric>, threshold <value>

REVIEW CADENCE
  - Weekly: <who> reviews <what>
  - Monthly: <who> reviews <what>
  - Quarterly: taxonomy re-defense (is any of the above wrong?)

TWELVE-MONTH DEFENSE
  - Why this north-star will still be right in 12 months
  - What would force a rewrite (name the failure mode)
```

The one-page constraint is a forcing function. A taxonomy
that requires three pages to explain is one the team will
not internalize. Aim for the whole team — engineering,
design, and GTM — being able to name the north-star and
the three inputs from memory after two weeks.

## What the CPO does personally

- **Authors the taxonomy.** This is not a data-team
  deliverable. The data team can help measure the metric
  once it exists; the *definition* — what the north-star
  is, what the inputs are, what the guardrails are — is
  a product-strategy decision that the CPO owns. Sean
  Ellis makes this point explicitly in *Hacking Growth*:
  the north-star is a leadership call, and the growth
  team measures against it after it is set
  ([Ellis & Brown, *Hacking Growth*, Chapter 3](https://hackinggrowth.com/)).
- **Defends it upward.** To the board, to the
  founder-CEO, to investors. The pressure to substitute
  revenue or a vanity metric for the real north-star
  comes from above; the CPO is the load-bearing defense.
- **Publishes it downward.** Every team member should
  know the north-star, the three inputs, and the
  guardrails from memory. If they can't recite them, the
  taxonomy has not landed.
- **Reviews it quarterly, rewrites it never (ideally).**
  The 12-month test is the standard. If you're rewriting
  it every quarter, one of the four failure modes above
  is in play; go diagnose which.

## Boundaries this lecture keeps

- **PMF measurement** (Sean Ellis 40% survey as a
  qualitative pull signal) is owned by
  [mod-001, Lecture 3](../../mod-001-customer-discovery-to-pmf/lectures/03-measuring-pmf.md).
  The north-star metric is the *post-PMF* quantitative
  north-star; it is not the 40% survey.
- **Outcome-based roadmap authoring** — how the
  north-star and input metrics become *quarterly
  outcomes* — is owned by
  [mod-003, Lecture 2](../../mod-003-roadmap-outcomes-and-strategy/lectures/02-outcomes-based-roadmap-shape.md).
  This lecture defines the metric; mod-003 turns it into
  a roadmap.
- **OKR authoring at CPO scope** is owned by
  [mod-003, Lecture 3](../../mod-003-roadmap-outcomes-and-strategy/lectures/03-okrs-at-cpo-scope.md).
  A metric taxonomy is not an OKR set; OKRs cite the
  metric taxonomy.
- **Activation, retention, cohort, and feature-adoption
  measurement** are the topic of
  [Lecture 2](02-analytics-regime-beyond-pmf.md).
- **A/B experimentation** on candidate input-metric moves
  is the topic of
  [Lecture 4](04-experimentation-at-pre-seed-to-series-a.md).
- **Financial metrics** — ARR, gross margin, LTV / CAC as
  business-model levers at depth — are level-40 work
  owned by
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum).
  This lecture treats revenue as the *downstream* number
  the north-star drives; the finance craft itself is not
  in scope.

## Takeaways

- A metric taxonomy is a **hierarchy**: one north-star,
  two or three inputs, three to five guardrails. Not a
  dashboard of nine numbers with no ranking.
- The **north-star** captures the value the product
  delivers, is movable in 90 days, and matches the
  user's job cadence. It is a *leading indicator* of
  long-term business success, not the business success
  itself.
- The **input metrics** decompose the north-star into
  the two or three levers that mechanically compound
  into it. Andrew Chen and the Reforge growth-loop
  literature are the reference. Match the decomposition
  to your product's actual loop.
- The **guardrails** name the things the north-star
  cannot be moved by breaking — quality, cost, UX,
  trust / safety. Every experiment and every ship is
  gated on them.
- Defend the taxonomy against the **12-month rewrite
  test**. If it's going to need a rewrite in three
  months, one of the four common failure modes is in
  play; diagnose it now.
- The CPO **authors, defends, and publishes** the
  taxonomy personally. It is not a data-team deliverable.

Lecture 2 gives you the *analytics regime* — funnels,
activation, retention curves, feature-adoption depth —
that the input metrics get measured against.
