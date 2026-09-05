# Lecture 3 — Reading the analytics stack and writing your own SQL against events

## The setup

The 2026 founding-PM market — the Solidroad, Reducto,
Atria-shape role — asks for a specific competency by name:
*"defines and moves metrics, writes their own SQL against
the events tables, does not wait for a data team to
answer questions."* Postings phrase it in different ways
(*"comfortable in SQL,"* *"can build their own dashboards
from raw events,"* *"reads the warehouse before opening
Amplitude"*) but the underlying ask is identical: a
founding CPO who cannot query the events table depends on
someone else's model of what happened, and — at pre-seed /
seed scale — often on someone who does not yet exist.

This lecture teaches the *shape* of the analytics stack a
founding CPO reads through (product analytics + warehouse
+ reverse-ETL), the *event-model discipline* that makes
the stack answerable at all (Segment / RudderStack tracking
plans), and the *five SQL patterns* that will handle 80% of
the CPO's own analytics needs. Exercise 6 makes you write
them; this lecture teaches you what they are.

## The stack, one diagram

The pre-seed → Series-A analytics stack a founding CPO
typically reads across has three layers plus one loop
back:

```
  +----------------+   events (JSON)   +-----------------+
  |  Product app   | ----------------> |  Ingest layer   |
  |  (web + mobile)|                   |  Segment /      |
  +----------------+                   |  RudderStack /  |
                                       |  native SDK     |
                                       +-----------------+
                                              |
                     +------------------------+---------------------+
                     |                                              |
                     v                                              v
             +---------------+                            +--------------------+
             | Product       |                            |  Data warehouse    |
             | analytics     |                            |  Snowflake /       |
             | Amplitude /   |  <-- same events, or  ->   |  BigQuery /        |
             | Mixpanel /    |     mirrored via Segment   |  Databricks /      |
             | PostHog       |                            |  Postgres          |
             +---------------+                            +--------------------+
                                                                    |
                                                                    v
                                                        +----------------------+
                                                        |  Transform (dbt)     |
                                                        |  fct_* / dim_* /     |
                                                        |  users, sessions,    |
                                                        |  subscriptions       |
                                                        +----------------------+
                                                                    |
                                                                    v
                                                        +----------------------+
                                                        |  Reverse ETL         |
                                                        |  Hightouch / Census  |
                                                        |  -> Salesforce / HS /|
                                                        |     Zendesk / Iter.  |
                                                        +----------------------+
```

The layers, in vocabulary:

- **Product analytics tool** (Amplitude, Mixpanel,
  PostHog, Heap, June). Purpose: fast, interactive
  funnel / retention / cohort analysis over instrumented
  events. Owned by product; the CPO uses it daily.
- **Ingest / event-collection layer** (Segment,
  RudderStack, Snowplow, or native SDKs). Purpose: one
  API that emits events to *many* destinations (the
  analytics tool, the warehouse, the CRM, the marketing
  tool). Owned by data-eng or product-eng; the CPO
  authors the *tracking plan* that governs what events
  exist.
- **Data warehouse** (Snowflake, BigQuery, Databricks,
  Redshift, or — at pre-seed — a Postgres running the
  same shape). Purpose: authoritative store for events,
  users, subscriptions, and everything else the business
  runs on. Owned by data-eng; the CPO queries it.
- **Transform layer** (dbt is the near-universal choice
  at pre-seed → Series-A). Purpose: turn raw events
  into modeled tables — *fact tables* for events,
  *dimension tables* for entities. Owned by
  analytics-eng or data-eng; the CPO reads the models.
- **Reverse-ETL** (Hightouch, Census, or built-in
  reverse pipes). Purpose: push warehouse data *back*
  into the operational tools — Salesforce, HubSpot,
  Zendesk, Iterable, the product itself. Owned by
  data-eng; the CPO authors the *audience definitions*.

The critical structural point: **product analytics and
the warehouse hold the same events** (or should — see the
tracking-plan discipline below). The CPO uses the product
analytics tool for interactive exploration and the
warehouse for the queries the tool cannot express.
Whichever tool is convenient is fine; the events
underneath are the same.

## The tracking plan — the CPO's contract with the events

Segment's *Analytics Academy* is the canonical reference
for *tracking-plan discipline* — the practice of specifying,
before you instrument, what events exist, what properties
each carries, and what naming conventions govern them
([Segment, "Tracking Plan" documentation](https://segment.com/docs/connections/spec/tracking-plan/);
[Segment, "Analytics Academy — Data Collection Best
Practices"](https://segment.com/academy/)).

The tracking plan is a spreadsheet or YAML file with the
shape:

| Event | When it fires | Properties | Type |
|---|---|---|---|
| `signup_completed` | User finishes registration form | `plan`, `signup_source`, `referrer_id`, `utm_*` | Track |
| `onboarding_step_completed` | User completes any onboarding step | `step_name`, `step_index`, `total_steps`, `seconds_on_step` | Track |
| `document_created` | User creates a document | `document_id`, `template_id`, `document_type`, `workspace_id` | Track |
| `document_shared` | User shares a document | `document_id`, `shared_with_user_id`, `share_type` (link / invite), `workspace_id` | Track |
| `user_signed_in` | Any authenticated session start | `session_id`, `signin_method` | Track |

The tracking plan carries three CPO-scope decisions:

- **Event naming.** `verb_object` (past-tense verb,
  singular object): `document_created`, `document_shared`,
  `workspace_joined`. Consistent naming is what makes
  funnels legible six months later.
- **Property discipline.** Every event carries the
  properties the CPO will want to *slice* on later —
  `workspace_id`, `signup_source`, `plan`,
  `experiment_variant`. Adding a property after the fact
  means back-filling data or losing the slice for the
  historical period.
- **Segment membership.** The tracking plan names the
  segment properties that appear on user (identify) and
  account (group) calls — plan tier, ACV band, industry,
  seat count. Segment cuts in the analytics tool depend
  on these being on the identify / group calls.

The failure mode the tracking plan prevents: **event
drift**. Without a plan, every engineer names events
differently, properties come and go, and the funnels
break silently. The CPO owns the plan the way the CTO
owns the API contract.

## The five SQL patterns

The CPO does not need to be a data engineer. The CPO does
need to write five SQL patterns without help. The
following patterns cover the queries a founding CPO
actually needs; they use PostgreSQL / Snowflake / BigQuery
syntax with minor variations noted where the dialects
diverge.

Assume the modeled tables `events`, `users`, and
`subscriptions`:

```
events(event_id, user_id, workspace_id, event_name, event_ts, properties JSONB)
users(user_id, signup_ts, signup_source, first_workspace_id)
subscriptions(subscription_id, workspace_id, plan, mrr, started_at, ended_at)
```

### Pattern 1 — Daily active users (DAU) with a segment cut

```sql
select
  date_trunc('day', e.event_ts)::date as day,
  s.plan,
  count(distinct e.user_id) as dau
from events e
join subscriptions s on s.workspace_id = e.workspace_id
where e.event_ts >= current_date - interval '30 days'
  and (s.ended_at is null or s.ended_at > e.event_ts)
group by 1, 2
order by 1, 2;
```

The pattern: `count(distinct user_id)` bucketed by day and
sliced by segment. The `subscriptions` join is what turns
"DAU" into "DAU by plan," which is where the interesting
questions live. The predicate on `subscriptions.ended_at`
handles the plan the user was on *at the time of the
event*, which matters for cohort-over-cohort analysis.

**Common gotchas:**

- **DAU inflates with anonymous users.** If your `user_id`
  is null for pre-auth events, filter those out.
- **Time zones.** `date_trunc('day', ts)` runs in the
  timezone of the timestamp. If your users are global,
  either standardize to UTC and note it, or convert per
  user's timezone (usually not worth the complexity).

### Pattern 2 — Funnel conversion (ordered)

```sql
with signups as (
  select user_id, event_ts as signup_ts
  from events
  where event_name = 'signup_completed'
    and event_ts >= current_date - interval '30 days'
),
first_document as (
  select e.user_id, min(e.event_ts) as first_doc_ts
  from events e
  join signups s on s.user_id = e.user_id
  where e.event_name = 'document_created'
    and e.event_ts between s.signup_ts and s.signup_ts + interval '7 days'
  group by 1
),
first_share as (
  select e.user_id, min(e.event_ts) as first_share_ts
  from events e
  join first_document f on f.user_id = e.user_id
  where e.event_name = 'document_shared'
    and e.event_ts between f.first_doc_ts and f.first_doc_ts + interval '7 days'
  group by 1
)
select
  (select count(*) from signups) as step_1_signup,
  (select count(*) from first_document) as step_2_created,
  (select count(*) from first_share) as step_3_shared,
  round(100.0 * (select count(*) from first_document) / (select count(*) from signups), 1) as pct_step_2,
  round(100.0 * (select count(*) from first_share) / (select count(*) from signups), 1) as pct_step_3
;
```

The pattern: successive CTEs, each restricted to users who
completed the prior step *within the conversion window*.
The `event_ts between prior_ts and prior_ts + interval` is
the ordered-funnel discipline. Each CTE's count divided by
the top-of-funnel count is the step conversion rate.

**Common gotchas:**

- **Window semantics.** *"Within 7 days of signup"* vs.
  *"within 7 days of the prior step"* are different
  funnels. Name which you're computing.
- **Multiple events per user.** `min(event_ts)` handles
  the case where a user creates many documents; the
  funnel counts *any* one document as step 2.

### Pattern 3 — Cohort retention

```sql
with cohorts as (
  select
    user_id,
    date_trunc('week', signup_ts)::date as cohort_week
  from users
  where signup_ts >= current_date - interval '180 days'
),
activity as (
  select
    e.user_id,
    date_trunc('week', e.event_ts)::date as active_week
  from events e
  group by 1, 2
),
retention as (
  select
    c.cohort_week,
    (a.active_week - c.cohort_week) / 7 as weeks_since_signup,
    count(distinct c.user_id) as active_users
  from cohorts c
  join activity a on a.user_id = c.user_id
  where a.active_week >= c.cohort_week
    and a.active_week <= c.cohort_week + interval '12 weeks'
  group by 1, 2
),
cohort_sizes as (
  select cohort_week, count(distinct user_id) as cohort_size
  from cohorts
  group by 1
)
select
  r.cohort_week,
  r.weeks_since_signup,
  cs.cohort_size,
  r.active_users,
  round(100.0 * r.active_users / cs.cohort_size, 1) as pct_retained
from retention r
join cohort_sizes cs on cs.cohort_week = r.cohort_week
order by r.cohort_week, r.weeks_since_signup;
```

The pattern: cohort each user by signup period; for each
cohort, count active users per subsequent period; divide
by cohort size to get a retention percentage.

**Common gotchas:**

- **Newer cohorts have fewer post-periods.** A cohort
  from three weeks ago has three weeks of retention
  data; a cohort from three months ago has twelve. Pad
  or filter accordingly.
- **Timezones and week boundaries.** Whatever week
  boundary you pick (Sunday-Saturday vs. Monday-Sunday)
  affects every cohort; document it.

### Pattern 4 — Feature adoption depth

```sql
with feature_users as (
  select
    user_id,
    min(event_ts) as first_used_ts,
    count(*) as uses,
    count(distinct date_trunc('week', event_ts)) as weeks_used
  from events
  where event_name = 'document_shared'
    and event_ts >= current_date - interval '60 days'
  group by 1
),
active_users as (
  select distinct user_id
  from events
  where event_ts >= current_date - interval '60 days'
)
select
  count(distinct au.user_id) as active_users,
  count(distinct fu.user_id) as feature_adopters,
  round(100.0 * count(distinct fu.user_id) / count(distinct au.user_id), 1) as adoption_breadth_pct,
  round(avg(fu.uses), 1) as avg_uses_per_adopter,
  round(avg(fu.weeks_used), 1) as avg_weeks_used_per_adopter
from active_users au
left join feature_users fu on fu.user_id = au.user_id;
```

The pattern: three numbers on the same query —
**breadth** (adopters ÷ active users), **depth** (uses
per adopter), and **stickiness** (weeks used per
adopter). Lecture 2's feature-adoption discipline named
these; this query is how they're read.

### Pattern 5 — Guard-metric guardrail check

```sql
with p95_latency as (
  select
    date_trunc('day', event_ts)::date as day,
    percentile_cont(0.95) within group (order by (properties->>'latency_ms')::numeric) as p95_ms
  from events
  where event_name = 'api_request_completed'
    and event_ts >= current_date - interval '14 days'
  group by 1
),
error_rate as (
  select
    date_trunc('day', event_ts)::date as day,
    100.0 * sum(case when (properties->>'status_code')::int >= 500 then 1 else 0 end)
          / count(*) as error_pct
  from events
  where event_name = 'api_request_completed'
    and event_ts >= current_date - interval '14 days'
  group by 1
)
select
  coalesce(p.day, e.day) as day,
  p.p95_ms,
  e.error_pct,
  case
    when p.p95_ms > 800 then 'BREACH'
    when e.error_pct > 1.0 then 'BREACH'
    else 'ok'
  end as guardrail_status
from p95_latency p
full outer join error_rate e on e.day = p.day
order by 1;
```

The pattern: extract JSON properties, compute per-day
p95 / error rate, tag each day with a guardrail status.
This is the query you run *before* declaring a metric
move real — a north-star up 15% with a guardrail
`BREACH` is a gaming event, not a win.

### The one SQL feature every founding CPO should learn: window functions

Window functions (`row_number()`, `rank()`, `lag()`,
`lead()`, `sum() over (...)`, `avg() over (...)`) turn
half a page of ugly self-joins into two lines. A concrete
example — "for each user, the time between their first
and second document creation":

```sql
select
  user_id,
  event_ts as first_doc_ts,
  lead(event_ts) over (partition by user_id order by event_ts) as second_doc_ts,
  extract(epoch from (lead(event_ts) over (partition by user_id order by event_ts) - event_ts)) / 3600 as hours_between
from events
where event_name = 'document_created'
qualify row_number() over (partition by user_id order by event_ts) = 1;
```

The `qualify` clause is Snowflake / BigQuery-specific;
in Postgres use a subquery with `where rn = 1`. Window
functions are the difference between "the SQL is
readable" and "the SQL is impossible."

The Mode Analytics *SQL Tutorial* is the reference for
the shape of these five patterns; Julian Hyde's essays on
SQL and the Snowflake / BigQuery docs cover window
functions in depth
([Mode Analytics, "SQL Tutorial"](https://mode.com/sql-tutorial/);
[Snowflake, "Window Functions" documentation](https://docs.snowflake.com/en/sql-reference/functions-analytic);
[Julian Hyde's blog](https://blog.hydromatic.net/)).

## The reverse-ETL loop and why the CPO cares

Reverse-ETL — Hightouch, Census, or the native pipes in
Snowflake / BigQuery — pushes warehouse data *back* into
operational tools. Concretely, the pattern the CPO
authors:

- **Audience definition in warehouse.** *"Accounts with
  a $50K+ ACV whose weekly-active-user count has
  dropped 40% over the last two weeks."* A SQL query
  against modeled tables.
- **Sync destination.** *"Salesforce → Opportunities →
  add tag 'renewal_at_risk'."* Or *"HubSpot → Contact
  Owner → notify the account manager."* Or *"Iterable
  → email list 'reengage_this_week'."*
- **Cadence.** Hourly, daily, on-change.

The CPO cares because reverse-ETL is where **the metric
regime becomes the operating tool**. A retention
guardrail that's only visible on the CPO's dashboard is
inert; the same guardrail that pages the account manager
when a top-20 account crosses it is operational. This is
a product / GTM boundary decision that neither the CPO
nor the CRO can make alone; the CPO drives the audience
definitions, the CRO drives what happens to the accounts
in each.

Hightouch and Census both document this pattern
extensively at
[hightouch.com/blog](https://hightouch.com/blog) and
[census.co/blog](https://census.co/blog).

## Product analytics vs. warehouse — when to use which

**Product analytics** (Amplitude, Mixpanel, PostHog) is
the right tool for:

- Interactive funnel exploration ("what happens if I add
  step 4 to this funnel and segment by
  signup_source?").
- Retention charts across cohorts.
- Session replay and heatmaps.
- Fast slice-and-dice with no SQL.

**The warehouse** is the right tool for:

- Joins across data the analytics tool doesn't have
  (Salesforce, Stripe, HRIS).
- Queries the analytics tool cannot express (e.g., "for
  each account, the median time between the two most
  recent power-user actions").
- Cohorts defined by combinations of events *and*
  external data ("cohort by ACV band by signup source
  by first-week-activation status").
- Any analysis that will feed reverse-ETL or a scheduled
  report.

Neither is a substitute for the other. A founding CPO who
only uses the analytics tool will be blind to
cross-source questions; one who only uses the warehouse
will move too slowly on interactive exploration.

## The inline SQL drill

A five-minute check on your SQL literacy right now. Given
the `events` table above, write (in your head or on
paper) the query for:

- The count of unique users who fired `document_created`
  in the last seven days, by signup source.
- The 7-day retention rate of users who signed up in the
  last two full weeks.
- For each workspace, the day of their peak activity
  (max distinct users active in a single day) over the
  last 30 days.
- The 90th-percentile time-to-first-document, for users
  who signed up last month.
- The list of the top ten `document_shared` recipients
  in the last week (by count of documents received),
  excluding recipients who are also senders in the same
  week.

If any of the five feels genuinely hard, Exercise 6 is
where you build the muscle. If none of them feels hard,
Exercise 6 is a warm-up before the harder problems in
Exercises 3 and 4.

## What the CPO does personally

- **Authors and maintains the tracking plan.** The plan
  is a product artifact, not an eng artifact.
- **Writes SQL against the warehouse regularly.** At
  least once a week. Muscle atrophies.
- **Explores the analytics tool daily.** Funnels,
  retention, feature-adoption charts — the CPO reads
  these before the standup.
- **Defines reverse-ETL audience definitions.** Which
  users / accounts get pushed where, on what trigger.

## What the CPO consumes

- The instrumented events (eng ships them).
- The warehouse plumbing (data-eng owns it).
- The dbt models over raw events (analytics-eng owns
  them).
- The reverse-ETL infrastructure and destinations
  (data-eng owns them).
- Data quality, freshness, and correctness (a data-eng
  discipline).

## Boundaries this lecture keeps

- **Metric taxonomy** is
  [Lecture 1](01-north-star-and-input-metric-taxonomy.md);
  this lecture is the *plumbing* the taxonomy is
  measured against.
- **Analytics vocabulary** (funnels, activation,
  retention curves, cohorts) is
  [Lecture 2](02-analytics-regime-beyond-pmf.md); this
  lecture is the *stack literacy* under it.
- **Experiment design** is
  [Lecture 4](04-experimentation-at-pre-seed-to-series-a.md);
  the SQL patterns here are the *analysis* layer that
  experiment reads run against.
- **Data-platform architecture at depth** —
  warehouse-selection trade-offs, dbt project structure,
  slowly-changing-dimension modeling, ELT vs. ETL,
  schema evolution, RBAC — is level-25 work owned by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum).
  The CPO consumes the stack; the CTO / data-lead
  authors it.
- **Deep dbt modeling and analytics-engineering craft**
  is out of scope; the CPO reads the models, does not
  author them.

## Takeaways

- The pre-seed → Series-A analytics stack is three
  layers plus one loop: **product-analytics tool** (fast
  interactive) + **warehouse** (authoritative, joinable)
  + **transform** (dbt models) + **reverse-ETL** back
  into the operational tools.
- The **tracking plan** is the CPO's contract with the
  events. Event names, properties, and segment cuts are
  product decisions.
- Five SQL patterns handle 80% of CPO analytics needs:
  **DAU / active with segment**, **funnel conversion**,
  **cohort retention**, **feature-adoption depth**,
  and **guardrail check**.
- **Window functions** are the SQL feature that
  distinguishes readable from unreadable queries; learn
  `lag`, `lead`, `row_number`, `percentile_cont`.
- **Reverse-ETL** is where the metric regime becomes
  operational — the CPO authors the audiences that get
  pushed back into the operational tools.
- Product analytics and warehouse are **complements**,
  not substitutes; the CPO uses each for what it's good
  at.

Lecture 4 turns this measurement muscle into the
**experimentation program** that moves the metrics
defensibly.
