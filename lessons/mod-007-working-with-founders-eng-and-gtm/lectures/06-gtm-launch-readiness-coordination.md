# Lecture 6 — GTM launch readiness coordination

## The setup

At a mature company, launching a feature is a
choreography run by a launch manager. There is a
launch calendar, a marketing plan, an enablement
plan for sales and CS, a support-team briefing, a
press or analyst outreach schedule, and a
readiness checklist that gates the go / no-go
meeting. At a pre-seed / seed founding-team
company, none of those roles exist yet. The
"launch manager" is the founding CPO. The
"marketing plan" is often a Notion doc and a
Twitter thread. The "sales enablement" is a
Slack message on Monday morning. The "support
briefing" is a mid-launch phone call *from
support*.

That mid-launch phone call is the specific
failure the 2026 Column-Tax / Method-Financial
posting language is trying to prevent when it
asks for a founding PM who *"owns GTM
alignment."* It is not asking for the CPO to
become the head of sales. It is asking for the
CPO to run a small, disciplined launch-readiness
coordination that makes every launch land
without the third-day support meltdown.

This lecture teaches the founding-PM version of
that coordination — the launch-readiness
checklist across six functions, the go / no-go
meeting shape, the escalation-to-*not*-shipping
discipline, and the specific handoffs to sales /
CS / marketing / support the CPO owns as the
seam.

The deep enterprise-selling motion — how sales
runs deals, how CS structures onboarding, how
marketing runs campaigns — is
[startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum)
(level 30). This lecture stays at the
*coordination* layer.

## What "launch" means at founding-team scale

Not every ship is a launch. The mod-004
delivery cadence produces multiple ships per
week; most of them are incremental improvements
to shipped surfaces, and each does not need a
launch-readiness coordination. A ship is a
*launch* when at least one of these is true:

- **A new customer-facing surface** goes live
  that customers or prospects haven't seen
  before.
- **A price or packaging change** goes live
  (per [mod-006](../../mod-006-pricing-packaging-and-monetization/README.md)).
- **A workflow-breaking change** goes live —
  something existing users will hit and
  behave differently against.
- **A GTM-visible bet** goes live that sales,
  CS, or marketing are actively selling into.
- **A public commitment** — a keynote, a
  podcast promise, a customer commitment —
  attaches to the ship.

For a small team, this is typically 1–4 launches
per quarter, embedded inside 40–80 ships. The
launch-readiness discipline this lecture teaches
applies only to launches, not to every ship.

## The launch-readiness checklist — six functions

The founding-PM launch-readiness checklist runs
across six functions. Each has a small set of
concrete artifacts that need to exist before the
go / no-go meeting. The CPO owns the seam — they
do *not* produce the artifacts themselves, but
they own knowing the artifact exists and is ready.

### 1. Product — the surface itself

- **The feature is complete** against its PRD,
  including the under-specification-checklist
  items from [Lecture 2](02-technical-fluency-for-the-founding-cpo.md#fluency-5--catching-under-specified-prds):
  state transitions, permissions, empty state,
  telemetry, migration story, failure semantics.
- **The eval regime has passed** (for AI-
  substrate features) — per
  [Lecture 3](03-ai-system-architecture-for-the-founding-cpo.md#layer-4--evaluation)
  and [mod-005 Lecture 6](../../mod-005-metrics-experimentation-and-ai-evals/lectures/06-eval-driven-decisions-for-llm-products.md).
  Threshold met on the labeled dataset.
- **The telemetry is live** — the launch-day
  dashboards exist, the tracking plan is
  correct, the mod-005 analytics regime can
  answer the launch-question.
- **The rollout mechanism is chosen** —
  feature flag, staged rollout, cohort split,
  100% at once. Per the mod-005 experiment
  discipline where applicable.
- **The rollback plan exists.** What happens
  if launch-day telemetry shows the feature
  is broken? Named engineer, named steps,
  target rollback time.

### 2. Marketing — the story

April Dunford's *Obviously Awesome: How to
Nail Product Positioning* — Ambient Press,
2019 —
[aprildunford.com/obviously-awesome](https://www.aprildunford.com/obviously-awesome/) —
is the reference for the positioning input
marketing needs from product. The CPO's
launch-readiness ask of marketing:

- **A positioning statement** for the launch
  — the alternative it competes against, the
  audience, the value, the differentiation.
  Not marketing copy; the *substrate* for
  marketing copy.
- **The customer-facing announcement** — blog
  post, changelog entry, email to existing
  customers, in-product notification. Text
  drafted, review complete.
- **Any external channel work** — social,
  paid, PR, analyst outreach — scheduled if
  applicable.
- **The pricing-page update** if the launch
  changes the SKU ladder — per [mod-006
  Lecture 1](../../mod-006-pricing-packaging-and-monetization/lectures/01-pricing-as-a-product-surface.md#what-the-cpo-owns-vs-what-marketing-and-sales-own).

### 3. Sales — enablement

- **The pitch update.** What the sales team
  says about this feature in a demo, in a
  discovery call, in the deck. One page or
  less.
- **The competitive positioning update** if
  the launch changes what the product does
  differently from the specific competitors
  sales is fighting.
- **The pricing / discounting bounds** if the
  launch changes them.
- **The FAQ.** The five questions prospects
  will ask about this feature and the
  answers.
- **The training session** — 30 minutes,
  recorded, with the CPO on the call. Not
  optional; the *"but we sent an email"*
  failure lives here.

### 4. Customer Success — support and expansion

- **The health-signal update.** If the
  feature changes what "healthy usage" looks
  like, the account-health model needs
  updating.
- **The onboarding update.** If the feature
  changes the first-run experience, the CS
  onboarding playbook needs updating.
- **The expansion story.** If the feature
  unlocks an expansion opportunity in
  existing accounts, CS needs the specific
  target-account list.
- **The training session.** Same shape as
  sales; typically CS attends the sales
  session or has a distinct 30-minute one.

### 5. Support — the incoming volume

- **The FAQ.** Same as sales, but tuned to
  the support surface — "how do I…" rather
  than "how does it work…"
- **The known-issues list.** What we know
  isn't perfect at launch, with the
  workaround. Nothing burns support faster
  than a known issue that support finds out
  about from customers.
- **The escalation path.** What support does
  when a customer hits something support
  can't fix. Named on-call engineer, named
  Slack channel, named response-time
  expectation.
- **Expected volume spike.** Rough estimate
  of ticket volume in the first week.
  Support staffing adjusts if warranted.

### 6. Telemetry and instrumentation — the launch dashboard

- **The launch dashboard.** One page, the
  metrics that answer "is this working?"
  Adoption, activation, retention on the new
  surface, error rate, latency, cost (for
  AI-substrate features).
- **The alert thresholds.** What triggers a
  page on launch day. Error rate over X;
  latency over Y; adoption under Z after 48
  hours.
- **The check-in cadence.** When the CPO,
  CTO, and GTM lead look at the dashboard
  together — typically 24 hours, 72 hours,
  and 7 days post-launch.

## The go / no-go meeting

The go / no-go is a short (30-minute) meeting
with the CPO, CTO / eng lead, and the GTM lead
(usually the head of sales or the founder-CEO
if there's no head of sales yet). It happens 24–
48 hours before the launch date. The three
questions:

1. **Is every checklist item ready?** Not
   "almost"; ready. The CPO walks the checklist;
   each function-owner confirms their items.
2. **What are the specific risks?** Named. Each
   risk has an owner and a mitigation. Risks
   without a mitigation are candidates for
   *not shipping.*
3. **Do we go?** Consensus. If any of the three
   attendees says no, we don't go — and we
   name what would change the answer.

The CPO owns the meeting. The output is a
short written go / no-go note logged with the
rest of the launch artifacts.

### The "don't ship" muscle

Most founding-team launches ship on the target
date because the target date has calcified into
a commitment the team hesitates to challenge. But
the highest-leverage launch-readiness discipline
is the ability to *not ship* when the readiness
isn't there.

Two failure modes shipping-anyway produces:

- **The launch that lands in a support
  meltdown.** Support wasn't briefed; the
  known-issues list wasn't shared; volume
  spikes; existing customers are affected;
  the launch narrative becomes about the
  outage.
- **The launch that lands but doesn't
  convert.** Sales wasn't trained; marketing
  copy hadn't landed; the pricing page wasn't
  updated. The feature exists; no one knows
  how to sell it; the launch produces zero
  pipeline lift.

The counter-move is the CPO's willingness to
*name the delay* in the go / no-go meeting.
Concretely: *"Sales training hasn't happened.
Support doesn't have the FAQ. The launch dash
isn't wired up. I'm proposing we delay by five
days so we can land those. What do you think?"*
This is influence-craft (Lecture 4) applied to
the launch decision.

Delays should be *small* and *specific* — days
or a week, not a quarter — and named for the
specific gap they're closing. A delay that
becomes indefinite is a symptom of a launch
that shouldn't be shipping at all; see the
mod-002 kill-list discipline.

### Escalation to the CEO on launch decisions

By Lecture 1's decision-rights map, the launch
date for a strategic bet is typically a
*consensus* decision between the CPO and CEO.
When the CPO wants to delay and the CEO wants
to ship anyway — or vice versa — the tie-
breaker path applies: written memo, one page,
proposing the delay with the specific gaps
named, the CEO's response.

The CPO who lets a launch ship over their own
"don't ship" objection *without escalating* is
setting up a specific downstream damage. When
the launch fails — because it will — the
retrospective produces the CPO's *"I told you
so"* stance, which damages the working
relationship irreversibly. Escalate the
disagreement before the launch; if the CEO
decides to ship anyway, commit to the ship and
help make it succeed.

## The launch-day rhythm

Launch day itself follows a specific rhythm the
CPO drives:

- **Pre-launch (T-2 hours).** Final check of
  the launch dashboard. Confirm the on-call
  engineer, the support escalation channel,
  and the CPO's own availability.
- **Launch (T-0).** Roll out per the mechanism
  (feature flag, staged rollout, 100%).
  Publish the customer-facing announcement.
  Update the pricing page if applicable.
  Send the internal Slack notification.
- **First hour.** The CPO watches the launch
  dashboard. Errors under threshold? Latency
  under threshold? Adoption starting? Support
  volume?
- **24 hours.** The CPO, CTO / eng lead, and
  GTM lead reconvene for a 15-minute review.
  Anything triggered an alert? Any support
  issues? Any sales feedback?
- **72 hours.** Second 15-minute review. Early
  adoption numbers. Cohort-1 activation on
  the new surface. Any patterns.
- **7 days.** Full launch retrospective —
  what shipped, what worked, what didn't,
  what we'd do differently. The retrospective
  is written and shared; it becomes input to
  the next launch's readiness checklist.

## Common failure modes

Seven failure modes recur across founding-team
launches:

- **The "we told support in Slack" launch.**
  Support finds out about the launch when
  tickets start coming in. FAQ doesn't exist;
  known-issues list doesn't exist; support
  escalation path is unclear. First-week
  support quality collapses.
- **The "sales sold it before it shipped"
  launch.** Sales pitched the feature in a
  demo two weeks before launch; the demo
  didn't match the shipped feature; the deal
  slipped. Lecture 1's external-communication
  row on the decision-rights map exists to
  prevent this.
- **The "pricing page wasn't updated" launch.**
  The feature is live; the pricing page still
  shows the old SKU; prospects who read the
  page today buy the old thing. Marketing
  didn't know pricing needed updating.
- **The "eval didn't pass but we shipped
  anyway" launch.** For AI features. The eval
  threshold was missed by "just a little";
  the team decided to ship; production
  reveals the eval was right. Every eval
  threshold you can lose on has to actually
  be a threshold you'd lose on — see
  [mod-005 Lecture 6](../../mod-005-metrics-experimentation-and-ai-evals/lectures/06-eval-driven-decisions-for-llm-products.md).
- **The "rollback plan didn't exist" launch.**
  Something broke in production; there was
  no plan for reverting; the eng team spent
  four hours figuring out the rollback while
  customers hit the broken state.
- **The "no launch dashboard" launch.** The
  team shipped; a week later they can't
  agree on whether the launch worked because
  no one instrumented for the question. The
  next launch-readiness checklist adds
  telemetry, but the current one is done on
  vibes.
- **The "day-of surprise" launch.** The CEO
  posted about the launch on Twitter before
  the readiness checklist was complete. The
  team spent the next 24 hours trying to ship
  under a promise instead of shipping when
  ready. The decision-rights map's external-
  communication row exists to prevent this.

## What the CPO does personally

- **Owns the launch-readiness checklist**
  end-to-end. Not producing every artifact;
  owning that every artifact exists.
- **Runs the go / no-go meeting.** Not
  "attends"; runs.
- **Trains sales and CS personally** for
  strategic-bet launches. Half an hour with
  each; the CPO is the one who understands
  the feature.
- **Watches the launch dashboard on launch
  day.** Physically at their desk (or the
  remote equivalent) for the first hours.
- **Names the "don't ship"** when readiness
  isn't there. Escalates to the CEO if the
  CEO disagrees.
- **Runs the 7-day retrospective** and
  publishes the write-up.

## What the CPO consumes from GTM counterparts

- **The sales-cycle context** — what stage
  is our pipeline in, what deals depend on
  this feature — from the head of sales.
- **The onboarding / expansion signals**
  from CS.
- **The campaign timeline** and channel
  performance from marketing.
- **The support-volume forecast** and
  known-issues list from support.

## Boundaries this lecture keeps

- **Enterprise-selling motion** — sales
  stages, MEDDIC / MEDDPICC, deal desk,
  procurement, contracting, PLG-to-SLG
  transition — is
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum)
  (level 30). This lecture coordinates *with*
  sales; it does not teach sales.
- **CS operating model** — onboarding
  playbooks, health scoring, expansion
  motions, renewal cadence — is also
  level-30 GTM craft.
- **Marketing craft** — SEO, content, paid,
  positioning execution, brand — is level-
  30 GTM craft. This lecture consumes the
  positioning input marketing produces and
  aligns on launch timing.
- **Support operating model** — ticket
  triage, escalation, self-service, tier
  design — is
  [startup-operations-governance-curriculum](https://github.com/ai-startup-curriculum/startup-operations-governance-curriculum)
  depth. This lecture coordinates *with*
  support at launch time.
- **The pricing / packaging shape** is
  [mod-006](../../mod-006-pricing-packaging-and-monetization/README.md);
  this lecture launches against it.
- **The experimentation regime** for A/B-
  gated launches is
  [mod-005 Lecture 4](../../mod-005-metrics-experimentation-and-ai-evals/README.md).
- **The eval regime** for AI feature launch
  gating is
  [mod-005 Lecture 6](../../mod-005-metrics-experimentation-and-ai-evals/lectures/06-eval-driven-decisions-for-llm-products.md)
  and
  [Lecture 3](03-ai-system-architecture-for-the-founding-cpo.md#layer-4--evaluation).

## Takeaways

- **Not every ship is a launch.** A launch is
  a new customer-facing surface, a pricing
  change, a workflow-breaking change, a GTM-
  visible bet, or a public commitment.
  Typically 1–4 per quarter inside 40–80
  ships.
- **Launch readiness runs across six
  functions**: product, marketing, sales,
  CS, support, telemetry. The CPO owns
  knowing each function's artifacts are
  ready.
- **The go / no-go meeting** is 30 minutes,
  three attendees (CPO, CTO / eng lead, GTM
  lead), three questions (checklist ready,
  risks named, do we go). Consensus
  required.
- **The "don't ship" muscle** is the highest-
  leverage launch discipline. Small, specific
  delays are healthy; the founding-CPO's
  willingness to name them is what makes them
  possible.
- **Launch day has a rhythm**: T-2 pre-check,
  T-0 launch, first-hour watch, 24h / 72h /
  7d reviews. The 7-day retrospective is
  written and shared.
- **Seven failure modes to design out**: the
  "told support in Slack" launch, the "sold
  before it shipped" launch, the "pricing
  page not updated" launch, the "eval didn't
  pass but we shipped" launch, the "no
  rollback plan" launch, the "no launch
  dashboard" launch, the "day-of surprise"
  launch.

Lecture 7 turns to **the product-progress
narrative for the board** — the CPO's slice of
the CEO's fundraise deck, and the disagreement
discipline for when the two stories diverge.
