# Lecture 2 — Analytics beyond PMF: funnels, activation, retention, cohorts, feature-adoption depth

## The setup

At the mod-001 stage, three PMF instruments — the Sean
Ellis 40% survey, retention that flattens above zero, and
organic pull — are all you need to know if the product has
been pulled. Post-PMF, those instruments stop moving fast
enough to steer weekly work. The team needs an **analytics
regime**: a set of coordinated instruments that reveal
*where* users are dropping off, *when* they're retaining
(or not), *how deeply* they're using features, and *which
segments* are producing the revenue.

The vocabulary this regime runs in is the vocabulary
Amplitude, Mixpanel, PostHog, and Reforge have converged
on over the last decade: **funnel**, **activation**,
**retention curve**, **cohort**, **feature-adoption
depth**, and **revenue-per-account cohort**. The founding
growth-PM job market — the Atria, Uare, Solidroad-shape
role — assumes you can author each and read them together
without a data team's help. This lecture teaches the six
instruments, the way each one lies when misused, and the
shape of a regime that reads them together honestly.

## Instrument 1 — Funnels (with denominators)

A funnel is a *sequence of events*, ordered by time, where
each step's population is the subset of the prior step's
population that reached it. Amplitude, Mixpanel, and
PostHog all render funnels natively; the practitioner
literature is deep on how to define one honestly
([Amplitude, "Funnels" docs](https://amplitude.com/docs/analytics/charts/funnel-analysis/funnel-analysis-overview);
[Mixpanel, "Funnels" docs](https://docs.mixpanel.com/docs/reports/funnels);
[PostHog, "Funnels" tutorial](https://posthog.com/tutorials/funnels)).

The three funnel discipline questions:

- **What's the top-of-funnel population?** *"Signups"*
  is one shape; *"unique visitors to /pricing"* is
  another; *"authenticated users who came back within
  seven days"* is a third. The choice determines what
  the funnel is actually measuring. Report the funnel
  with an explicit top-of-funnel denominator every time.
- **What's the conversion window?** *"Signup → first
  action"* within 24 hours is a different funnel from
  the same steps within 30 days. Report the window
  every time.
- **Is it ordered or unordered?** Most product funnels
  are ordered — step 2 requires step 1. Some (activation
  criteria) are unordered — the user must do event A and
  event B in any order within the window. Name which.

**How funnels lie:**

- **Denominator drift.** The top-of-funnel population is
  redefined between reports (from "signups" to
  "activated users") without renaming the funnel; the
  conversion rate looks like it moved but only the
  denominator did.
- **The trailing-step trap.** The funnel's last step is
  the metric the team is optimizing for. If earlier
  steps get easier (fewer clicks to reach) but the last
  step gets harder (a paywall added), the overall
  conversion is unchanged but the mix of who converts
  shifted; the funnel is silent on this.
- **Blended segments.** Enterprise and self-serve
  segments blended into one funnel produce a Simpson's
  paradox waiting to happen — a step conversion that
  moved in every segment can be flat in the blend, or
  vice versa. Report funnels per segment, always.

**Canonical shapes to author:**

- **Signup → activation funnel.** From first landing (or
  first authenticated session) through the activation
  event (defined below). This is the funnel every
  product needs; NUX (new-user experience) drop-off is
  read from its steps.
- **Feature-adoption funnel.** From "user reached the
  feature entry point" through "user completed the
  first-use action" through "user completed a
  second-time-use action within N days." Depth of
  adoption is read from this funnel's tail.
- **Trial → paid funnel.** For products with a trial
  motion, from trial start through paid conversion,
  segmented by trial source.
- **Renewal / expansion funnel.** For subscription B2B,
  from renewal-window opens through renewal decision,
  segmented by ACV band.

## Instrument 2 — Activation

**Activation** is a defensible event — usually a
*combination* of behaviors within a *time window from
signup* — that predicts long-term retention. Its purpose
is to give the team a *near-real-time proxy* for retention:
retention curves take weeks to read (Instrument 3);
activation rate can be read within days.

Reforge's Growth Series and the Amplitude playbook both
codify the same discipline: activation is not "signed up
and did any action"; activation is "did the set of things
that we've measured *correlates with users still being
around in 30 or 90 days*." That correlation is what makes
the metric predictive. Facebook's often-cited internal
activation event — *seven friends in ten days* — is the
canonical example: not "signed up," not "added a friend,"
but a specific number of friends within a specific window
that historically predicted long-term retention
([Chamath Palihapitiya, "Facebook's growth playbook,"
Growth Hackers TV, 2013 — see the working transcript at
[growthhackers.com](https://growthhackers.com/videos/chamath-palihapitiya-former-facebook-growth-on-the-1st-metric-you-need-to-focus-on)];
Chen, *The Cold Start Problem*, on the Facebook activation
event](https://andrewchen.com/the-cold-start-problem-book/)).

**How to author an activation event:**

1. Pull the cohort of users who signed up N months ago
   (N large enough that "still using in month 3" is
   observed — usually 3–6 months back).
2. For each user, record every candidate signal — did
   they invite a teammate, did they create their first
   document, did they connect their first data source,
   did they complete onboarding tour, etc.
3. Split the cohort into *retained-at-day-90* and
   *churned-by-day-90*.
4. For each candidate signal, compare the retention rate
   of users who fired it against users who didn't.
   Signals with a *large* gap (users who fired it retain
   at 60% vs. users who didn't at 15%) are activation
   candidates.
5. Test combinations. Often the best activation event is
   a small AND-conjunction ("invited a teammate AND
   created a document AND returned once") — because each
   alone is a weaker signal, but together they predict.
6. Add a **time window** — usually 7, 14, or 30 days
   from signup. Users who cross the criteria inside the
   window are "activated"; users who don't are "at risk."
7. Validate the definition on a *fresh* cohort — the
   definition must generalize, not just fit the training
   cohort.

**How activation lies:**

- **The correlation-causation trap.** Users who did X are
  more likely to retain — but did doing X *cause* the
  retention, or did being the sort of user who retains
  also cause doing X? Activation is a proxy metric, not a
  causal one. Testing whether *changing* activation
  moves retention (Lecture 4) is the causal question;
  activation itself is a leading indicator.
- **The window trap.** Activation defined at day 7 for a
  product with a natural monthly cadence will flag most
  users as "unactivated." Match the window to the
  product's use frequency.
- **Definition drift.** Redefining activation every
  quarter is the fastest way to destroy the metric's
  usefulness. Change the definition once a year at
  most; note the change explicitly in every subsequent
  report.

## Instrument 3 — Retention curves and cohort analysis

Retention curves are the honest picture of whether the
product is used again. Cohort analysis groups users by the
period they arrived (usually week or month) and tracks each
cohort's retention *from its own start*, so you can
distinguish a product that's getting better from a product
that's just adding users faster.

The **N-day retention** shape: for each cohort C, plot
*"fraction of C active on day N since their signup."* Then
overlay multiple cohorts on the same chart — cohort of
week 1, cohort of week 2, etc.

**Three curve shapes to know (mod-001 taught these; this
lecture makes them post-PMF operational):**

- **Straight-to-zero curve.** No asymptote. You do not
  have PMF for this cohort. Return to mod-001.
- **Flattening curve above zero.** Some subset of the
  cohort retained. The *height* of the asymptote is the
  size of the retained pool.
- **Smiling curve.** The cohort decays, then the
  survivors use the product more over time. The right
  shape for a product with a working expansion loop.

**Post-PMF, the questions retention curves must answer:**

- **Is the newest cohort's curve above or below older
  cohorts'?** If newer cohorts retain *worse*, growth
  investment is bringing in less-qualified users; if
  they retain *better*, product changes are working.
  This is only visible in a per-cohort view; a blended
  retention line hides it.
- **Which segment's curve is above the average, and
  which is below?** Enterprise vs. self-serve, US vs.
  EU, verticals A vs. B. The segment with the highest
  asymptote is where the product is working; the segment
  with the lowest is where the roadmap has work to do.
- **What's the difference between day-N retention and
  cohort *revenue* retention?** A cohort can be active
  (behavioral retention) while its revenue attritions
  (they're on the free plan). The two curves diverging
  is a monetization problem, not a product problem.

**How retention curves lie:**

- **Blended retention.** A single retention line across
  all cohorts collapses newer-cohort improvements into
  older-cohort baselines; the metric flattens into an
  average that reveals nothing. Always report per-cohort.
- **Behavioral-vs-billing confusion.** "Retained" defined
  as "subscription is still active" (billing retention)
  can look strong while behavioral retention collapses;
  the subscribers who aren't logging in are on borrowed
  time until they notice and cancel. Prefer behavioral
  retention as the *product* signal; report billing
  retention separately.
- **The wrong period.** Weekly retention on a monthly-use
  product will show fake churn. Match the period to the
  product's natural use cadence.

**Practical variants:**

- **N-day retention.** Percent of a cohort active on
  *exactly* day N. Sharp signal, high variance.
- **Rolling N-day retention** (a.k.a. bracket retention).
  Percent of a cohort active on *any day* in the window
  (day N-3 to day N+3). Smoother, less prone to
  weekend noise.
- **Unbounded (a.k.a. classic) retention.** Percent of a
  cohort active *at any point since signup*. Never
  decreases; useful only for lifetime-value framing,
  not for weekly steering.
- **Range retention.** Percent of a cohort with at least
  one action in each of the last N periods. The right
  shape for products with a strong "regular use" pattern.

Amplitude and Mixpanel both document these variants in
depth; the Reforge Retention Series is the reference for
which variant to use when
([Amplitude, "Retention analysis" docs](https://amplitude.com/docs/analytics/charts/retention-analysis/retention-analysis-overview);
[Reforge, "Retention" program overview](https://www.reforge.com/programs/retention-engagement)).

## Instrument 4 — NUX / onboarding drop-off

The **new-user experience (NUX)** funnel is the specific
funnel from *first landing / signup* to *activation event*.
Its steps are the concrete actions the product's
onboarding requires: create an account, verify email,
complete onboarding tour, invite teammate, connect data
source, first-use event.

The founding-CPO discipline is to *own the NUX funnel
step-by-step*. Every step where drop-off exceeds a
threshold (a common rule of thumb: no single step should
lose more than 20% of the population, and no NUX funnel
should lose more than 60% top-to-activation) is a bet the
roadmap should be looking at. NUX drop-off is where
retention is won or lost — a user who never activated
almost never retains, so an activation-rate improvement is
one of the highest-leverage product moves available.

Concrete pattern for a NUX drop-off diagnosis:

1. Chart the funnel step-by-step for the last 30 days.
2. Identify the single largest-drop step.
3. Segment that step: is the drop uniform, or
   concentrated in one source, browser, region, or
   device?
4. Look at *time-in-step* for the users who did convert
   through it — a step where 40% of successful users
   spent > 5 minutes is a UX problem, not a motivation
   problem.
5. Read session recordings (FullStory, LogRocket, PostHog
   Session Replay) for the drop-off cohort. The
   qualitative signal from ten recordings usually names
   the fix.

## Instrument 5 — Feature-adoption depth

**Feature adoption** is often measured at *breadth* —
"what fraction of active users have used this feature?" —
which is easy and useless. Breadth is a launch metric; it
tells you whether people found the feature.

**Feature adoption depth** is the correct post-PMF read:
having found the feature, do users *keep using* it? A
useful decomposition, drawn from Reforge and the Amplitude
playbook:

- **Adoption breadth (D0).** % of active users who used
  the feature at least once ever.
- **Adoption stickiness (DAU/MAU of the feature).** Of
  users who used it in the last month, how often did
  they use it? Feature-level DAU/MAU ratio.
- **Adoption depth (habit strength).** Of users who used
  it more than once, what's the median number of uses
  per week / month?
- **Adoption impact (retention lift).** Do users who
  adopted the feature retain (at the product level)
  better than users who didn't? This is the causal
  question — see Lecture 4 for the experiment design to
  answer it defensibly, and Lecture 5 for the
  quasi-experimental fallback when you can't A/B.

A feature that scores high on breadth and low on depth is
a demo feature — people tried it, no one adopted it. A
feature that scores high on depth and low on breadth is a
niche feature — a small group loves it, and the roadmap
question is whether the niche is worth doubling down on or
whether the feature should be promoted to the main
experience. Both patterns are common; the mistake is
reading only breadth.

## Instrument 6 — Revenue-per-account cohorts (for B2B)

For a B2B product, the metrics above are necessary but not
sufficient. The buyer, the user, and the payer are often
different people, and a product can have great user-level
retention *and* churn logo after logo because the buyer
never got budget-defensible value.

The B2B-specific instrument is the **revenue-per-account
cohort curve**: for each cohort C of accounts (grouped by
month of first paid subscription), plot the cohort's
*revenue in month N since first paid*. Three ways the
curve moves:

- **Flat cohort revenue = flat account.** The account is
  still around; nothing expanded. Fine for base retention;
  concerning as a growth model if it dominates.
- **Rising cohort revenue = expansion.** Account is
  buying more seats, more usage, more product surface.
  This is the shape a B2B growth model wants.
- **Declining cohort revenue = contraction (downgrade or
  partial churn).** Account is still paying but for less.
  Precursor to full churn most of the time.

**Net revenue retention (NRR)** is the composite: for a
cohort at month N vs. their revenue at month 0,
*(expansion − contraction − churn) / month-0 revenue*. A
B2B product with NRR > 100% is expanding without net-new
sales; NRR > 120% is exceptional and usually reflects a
usage-based pricing model or a strong land-and-expand
motion. Bessemer's *State of the Cloud* essays and the
SaaStr archive are the practitioner references for NRR
benchmarks by segment
([Bessemer Venture Partners, "State of the Cloud"](https://www.bvp.com/atlas);
[SaaStr, "The Ultimate Guide to Net Revenue Retention"](https://www.saastr.com/)).

<!-- needs-research: verify Bessemer's current 2025-era
NRR benchmark ranges for early-stage SaaS by segment
(enterprise vs mid-market vs SMB) before citing specific
numbers; the ranges shift year to year. -->

## Reading the instruments together — a diagnosis regime

The six instruments together form a diagnosis regime. A
common pattern the CPO runs weekly:

1. **Look at the north-star metric (Lecture 1) and its
   direction.** Up, down, flat?
2. **Look at the input metrics.** Which input moved to
   produce the north-star move? If none, the north-star
   move is noise or exogenous.
3. **For the moving input, drop into the funnel.** Which
   step is the change concentrated in?
4. **For the moving funnel step, segment.** Which
   segment is producing the movement?
5. **For the moving segment, check retention.** Did the
   change stick — did the improved cohort retain?
6. **Check the guardrails (Lecture 1).** No cost /
   quality / UX regression?

The regime turns "the metric moved" into a five-question
diagnosis. Without the regime, the team responds to metric
moves by *guessing at causes*, which is expensive and
usually wrong.

## What the CPO does personally

- **Defines the funnels, activation event, and cohort
  cuts.** Every funnel step, every activation criterion,
  every cohort dimension is a product decision. The CPO
  authors; the data team implements.
- **Reads the curves weekly.** In the analytics tool,
  not from someone else's dashboard screenshot. Reading
  the curve builds the muscle to *know* when it looks
  wrong.
- **Runs the diagnosis when metrics move.** Not "let's
  ask the data team what happened"; the CPO drops into
  the funnel and segments the movement themselves.
  Lecture 3 is how you get the SQL literacy for the
  cases the analytics tool cannot answer.
- **Writes the segment cuts into the tracking plan.**
  Segment / RudderStack / native event-model discipline
  requires that every event carry the properties the CPO
  will want to slice on later. This is a
  before-instrumentation decision, and the CPO's to
  make.

## What the CPO consumes from the data team

- The instrumented events themselves (the eng /
  data-eng job).
- The warehouse tables that store the events (the
  data-eng / analytics-engineering job).
- The dashboard skeletons (the data / analytics job).
- SLA on data freshness and correctness (a data-eng
  discipline).

None of these are CPO-authored. All of them are things
the CPO must be able to *ask for* by name.

## Boundaries this lecture keeps

- **PMF measurement** (retention curves as a *fit*
  signal, not a *usage* signal) is owned by
  [mod-001, Lecture 3](../../mod-001-customer-discovery-to-pmf/lectures/03-measuring-pmf.md).
- **Metric taxonomy and the north-star framing** are
  owned by [Lecture 1](01-north-star-and-input-metric-taxonomy.md).
- **The analytics stack itself** — how events flow from
  the app to the warehouse, tracking-plan hygiene,
  reverse-ETL patterns — is the topic of
  [Lecture 3](03-analytics-stack-and-sql-against-events.md).
- **Experimentation** — proving a NUX / activation
  change *caused* a retention lift — is the topic of
  [Lectures 4 & 5](04-experimentation-at-pre-seed-to-series-a.md).
- **Pricing- and packaging-specific metrics** (ARPA,
  contract-level renewal patterns, seat expansion
  models) are owned by
  [mod-006](../../mod-006-pricing-packaging-and-monetization/README.md).
- **Data-platform architecture and warehouse design** is
  level-25 work owned by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum).

## Takeaways

- **Funnels** need explicit denominators, windows, and
  segment cuts. Blended-segment funnels lie via
  Simpson's paradox.
- **Activation** is a defensible event (usually a
  combination) inside a time window that historically
  predicts retention. Author it from a cohort; validate
  on a fresh cohort; change the definition rarely.
- **Retention curves** by cohort are the honest picture
  of whether the product is working. Blended curves
  hide cohort-over-cohort improvement. Prefer
  behavioral over billing retention as the *product*
  signal.
- **NUX drop-off** is where activation is won or lost.
  Own the funnel step-by-step; segment every large drop;
  read session recordings for the drop-off cohort.
- **Feature adoption depth** — stickiness, habit
  strength, and retention lift — is the post-PMF read.
  Breadth alone is a launch metric.
- **Revenue-per-account cohorts** and NRR are the B2B
  composite. A product with great user retention and
  bad NRR has a monetization problem, not a product
  problem.
- The six instruments together form a **diagnosis
  regime** — when the north-star moves, the CPO can
  trace *which* input, *which* funnel step, *which*
  segment, *which* cohort produced it, and *whether the
  guardrails held*.

Lecture 3 gives you the *stack literacy* — product
analytics + warehouse + reverse-ETL, and the SQL to write
against the events tables yourself — that lets you author
this regime without a data team's help.
