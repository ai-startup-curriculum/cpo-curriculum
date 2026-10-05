# Exercise 6 — SQL against events tables drill

**Time:** ~3 hours. **Deliverable:** one **SQL notebook**
(a `.sql` file, a Jupyter notebook, a Hex / Mode /
Metabase document, or an equivalent) containing **five
executable queries** against a real or plausible-synthetic
events table — DAU with a segment cut, ordered funnel
conversion, cohort retention, feature-adoption depth, and
a guard-metric guardrail check — plus a half-page
**tracking-plan memo** stating which events the queries
assume and where the plan would need to grow.

## Purpose

Make the Lecture 3
([Lecture 3 — The five SQL patterns](../lectures/03-analytics-stack-and-sql-against-events.md#the-five-sql-patterns))
move operational: the founding CPO *writes their own
queries against the events table* rather than reading
dashboards someone else defined. This is the Solidroad /
Reducto-shape founding-PM expectation — a CPO who defines
and moves metrics, not one who waits for a data team to
build a report.

The queries here cross-reference the earlier exercises:
Query 1's DAU segment is the Exercise 1 taxonomy's unit;
Query 3's cohort retention is the Exercise 2 analysis's
cohort table; Query 5's guardrail check is the Exercise 3
brief's guard-metric check. Author the SQL as the
*execution engine* for the module's analytics work.

## What you need before you start

- **Access to an events table** — the real one if you
  have it (via the warehouse: BigQuery, Snowflake,
  Postgres, DuckDB, Databricks), a product-analytics
  tool with SQL-export (PostHog, Mixpanel's warehouse-
  connected shape), or a plausible-synthetic you build.
- **If synthetic:** a 90-day event stream for a
  plausible product with the Lecture 3 shape:
  ```
  events(event_id, user_id, workspace_id, event_name, event_ts, properties JSONB)
  users(user_id, signup_ts, signup_source, first_workspace_id)
  subscriptions(subscription_id, workspace_id, plan, mrr, started_at, ended_at)
  ```
  Mock Data Generator, Faker, or a 100-line Python
  script sampling signups / activations / repeats / churn
  are all adequate. DuckDB running locally against a CSV
  pile is a legitimate choice. Share the generator
  script with the deliverable.
- **The tracking plan from the product** (if real) or a
  tracking plan you author per
  [Lecture 3 — The tracking plan](../lectures/03-analytics-stack-and-sql-against-events.md#the-tracking-plan--the-cpos-contract-with-the-events).
  Query 1 needs `user_id` and a plan property; Query 2
  needs ordered events with a conversion window; etc.
- **A SQL dialect choice.** Pick one and stay in it;
  PostgreSQL, Snowflake, BigQuery, DuckDB, and Postgres
  all work. Where
  [Lecture 3](../lectures/03-analytics-stack-and-sql-against-events.md)
  shows dialect-specific syntax (`qualify`, `interval`
  literals, JSON extraction), use your dialect's
  equivalent and note the choice.
- **A reference** — [Mode Analytics "SQL
  Tutorial"](https://mode.com/sql-tutorial/) for the
  shape of the patterns;
  [Snowflake Window Functions
  docs](https://docs.snowflake.com/en/sql-reference/functions-analytic),
  [BigQuery Analytic Functions](https://cloud.google.com/bigquery/docs/reference/standard-sql/analytic-function-concepts),
  or [PostgreSQL Window Functions](https://www.postgresql.org/docs/current/tutorial-window.html)
  for the window-function syntax that Lecture 3's
  Query 5+ depends on.

## The five queries

Each query must be **executable** — not pseudo-SQL. If
the data is synthetic, state the generator and expected
row count; if the data is real, state the time range and
row count of the output.

### Query 1 — Daily active users with a segment cut

Shape per
[Lecture 3 — Pattern 1](../lectures/03-analytics-stack-and-sql-against-events.md#pattern-1--daily-active-users-dau-with-a-segment-cut):

- Compute **DAU** for the last 30 days.
- Cut by **plan tier** (or whichever segment property
  the Exercise 1 taxonomy named as the primary unit).
- Join `events` to `subscriptions` on `workspace_id`
  so the segment is the plan the user was on *at the
  time of the event* — not the current plan.
- Handle time zones per Lecture 3 (state UTC or the
  convention you adopted).
- Filter null `user_id` to avoid anonymous-event
  inflation.

**Report:** the output row count, the top 3 plan tiers
by average DAU, and one anomaly day (if any). What does
the DAU-by-plan curve tell you about the Exercise 1
taxonomy?

### Query 2 — Ordered funnel conversion

Shape per
[Lecture 3 — Pattern 2](../lectures/03-analytics-stack-and-sql-against-events.md#pattern-2--funnel-conversion-ordered):

- Define the funnel for the segment and NUX from
  Exercise 2. At minimum three ordered steps —
  signup → first use → repeat use — with a stated
  conversion window.
- Successive CTEs, each restricted to users who
  completed the prior step *within the conversion
  window*. State explicitly whether the window is
  "within N days of signup" or "within N days of
  prior step."
- `min(event_ts)` to handle multiple events per user
  — the funnel counts *any* one occurrence of the
  step.
- Compute step-level **conversion rates** with
  denominators at every step.

**Report:** the output table (step counts and
percentages), the largest-drop step, and one
segmentation of the drop (by source / plan / device /
geo).

### Query 3 — Cohort retention

Shape per
[Lecture 3 — Pattern 3](../lectures/03-analytics-stack-and-sql-against-events.md#pattern-3--cohort-retention):

- Cohort users by signup week (or month, if your
  product is monthly-use).
- For each cohort, compute `active_users` per
  period for ≥ 12 periods since signup.
- Compute `pct_retained = active_users / cohort_size`.
- At least four overlapping cohorts in the output.
- Pad or filter so newer cohorts' missing post-
  periods are visible, not silently rolled into an
  average.
- State the week-boundary convention explicitly.
- State the retention variant you're using (N-day,
  rolling, unbounded, range) and why.

**Report:** the retention table (cohort × period ×
pct), the asymptote per cohort, and whether newer
cohorts are retaining above or below older ones. This
query is the SQL backing for Exercise 2's retention
analysis.

### Query 4 — Feature-adoption depth

Shape per
[Lecture 3 — Pattern 4](../lectures/03-analytics-stack-and-sql-against-events.md#pattern-4--feature-adoption-depth):

- Pick a feature (same feature as Exercise 2's
  adoption-depth section if possible).
- Compute all four Lecture 2 adoption metrics on one
  query:
  - **Breadth** = adopters / active users (over
    some window — state it).
  - **Depth** = average uses per adopter.
  - **Stickiness** = average weeks used per
    adopter.
  - **(Impact)** — if a retention-lift read is
    feasible, join to a retention CTE and compute
    the gap between adopter and non-adopter
    retention; otherwise, state the join needed
    and defer.

**Report:** the four numbers, which of the four
Lecture 2 feature classifications (demo / niche /
core / dead) they imply, and the correlation-causation
caveat per Lecture 2 Instrument 5.

### Query 5 — Guard-metric guardrail check

Shape per
[Lecture 3 — Pattern 5](../lectures/03-analytics-stack-and-sql-against-events.md#pattern-5--guard-metric-guardrail-check):

- Pick two guard metrics from the Exercise 1
  taxonomy or the Exercise 3 experiment brief —
  typically **p95 latency** and **error rate**.
- Compute per-day p95 and error % for the last 14
  days from `events` with `properties` JSON
  extraction (per the Lecture 3 Pattern 5 shape).
- Tag each day with a **guardrail status** —
  `BREACH` if above threshold, `ok` otherwise.
- Join the two per-day series on day so each row
  shows both metrics in context.

**Report:** the daily table, any `BREACH` days, and
the breach rate across the window. If no breaches, run
the query against a synthetic breach day you injected
to prove the query catches it.

### Bonus — Window-function pattern

Per
[Lecture 3 — Window functions](../lectures/03-analytics-stack-and-sql-against-events.md#the-one-sql-feature-every-founding-cpo-should-learn-window-functions),
include at least one query (one of the five above, or a
sixth) that uses a window function — `lead()`,
`lag()`, `row_number()`, `rank()`, `sum() over (...)`,
or `avg() over (...)`. The Lecture 3 example — time
between first and second use per user — is a good
starting shape.

## Tracking-plan memo (half page)

Author or extract the tracking plan the queries assume,
per
[Lecture 3 — The tracking plan](../lectures/03-analytics-stack-and-sql-against-events.md#the-tracking-plan--the-cpos-contract-with-the-events):

| Event | When it fires | Properties | Type |
|---|---|---|---|

Fill in the events each query reads. State:
- **Event naming convention** (`verb_object`,
  past-tense, singular).
- **Property discipline** — which properties every
  event carries, so the segment cuts work (plan,
  workspace_id, signup_source, experiment_variant).
- **Segment-membership identify / group calls** —
  which properties live on `identify()` (user plan,
  ACV band, industry) and `group()` (account tier,
  seat count).
- **Gaps.** Where would the tracking plan need to grow
  for the next quarter's analytics work? Name 1–3
  specific events or properties missing today.

## Starter guidance

- **Start with the schema.** Read the events table's
  columns and sample 100 rows before writing any
  query. Half the SQL questions reduce to "what's in
  the table?"
- **Build each query from a sampled subset first.**
  Replace `where event_ts >= current_date - interval
  '30 days'` with `where event_ts >= '2026-09-01' and
  event_ts <= '2026-09-02'` while developing. Fast
  iteration beats correctness-on-the-full-run.
- **Use CTEs liberally.** The Lecture 3 patterns are
  all CTE-structured. CTE-structured SQL is readable;
  the alternative (deep subqueries) is a trap.
- **The denominator is the question.** For funnels,
  cohorts, and adoption, write the denominator
  explicitly as its own CTE. Divisions are where SQL
  gets subtle; naming the denominator makes the ratio
  defensible.
- **Window functions are the force multiplier.** The
  one Lecture 3 pattern most founding CPOs don't know
  that pays back the time to learn is window
  functions. Spend 30 minutes on the
  Snowflake / BigQuery / Postgres window-function docs
  before writing Query 3.
- **Format for review.** Every query gets a header
  comment stating purpose, inputs (tables + windows),
  outputs (expected row shape), and known limitations.
  SQL you'd put in a PR, not SQL you'd throw at a
  Slack thread.
- **Validate against the analytics tool.** If you
  have Amplitude / Mixpanel / PostHog, run the
  equivalent chart there and compare. Different
  numbers point to tracking-plan or query bugs; same
  numbers raise your trust in both.

## Acceptance criteria

- **Five executable queries** (one per Lecture 3
  pattern) — DAU with segment cut, ordered funnel,
  cohort retention, feature-adoption depth, guardrail
  check. Each runs; each produces an output row shape.
- Each query has a **header comment** stating purpose,
  input tables, time windows, output shape, and known
  limitations.
- Each query **ties back to an earlier exercise** —
  Query 1 to Exercise 1's taxonomy unit, Query 2 to
  Exercise 2's NUX funnel, Query 3 to Exercise 2's
  cohort retention, Query 4 to Exercise 2's feature-
  adoption depth, Query 5 to Exercise 1's guardrails
  or Exercise 3's guard metrics.
- At least one query uses a **window function**.
- The **tracking-plan memo** states event naming,
  property discipline, identify / group calls, and 1–3
  specific gaps.
- The **dialect** is named; dialect-specific
  constructs (JSON extraction, `qualify`, `interval`)
  match the dialect.

## Common failure modes

- **Blended retention from a single CTE.** A single
  SELECT that averages all cohorts. The Lecture 3
  Pattern 3 shape is per-cohort explicitly; blended
  retention is the Lecture 2 single-biggest lie.
- **Funnel without a window.** No `event_ts between
  prior_ts and prior_ts + interval` restriction. The
  funnel then counts users who did step 2 *months*
  after step 1 as converted; the shape is useless.
- **DAU inflated by anonymous events.** `user_id` not
  filtered for null; the count double-counts
  pre-auth sessions. Filter.
- **JSON extraction without casting.** Pulling
  `properties->>'latency_ms'` without `::numeric`;
  the p95 computes on strings and silently returns
  nonsense.
- **Hard-coded thresholds without comment.** Query 5's
  `800ms` and `1%` thresholds live in the SQL
  without a note on where they came from (Exercise 1
  taxonomy; eng SLO; wish). Comment the source.
- **Dashboard-shaped SQL.** Query produces a shape
  only a specific chart renders; another analyst
  can't reuse it. Prefer long-format output (one row
  per observation) that any tool can consume.
- **No tracking-plan memo.** The queries assume
  events that may not exist in production; without
  the memo, the gap is invisible until the first
  prod run fails. The memo is where the author
  commits to the event contract.

## Source alignment

The five SQL patterns, the tracking-plan discipline, and
the stack diagram derive from
[Lecture 3](../lectures/03-analytics-stack-and-sql-against-events.md).
The underlying references are: Segment's "Tracking Plan"
docs —
[segment.com/docs/connections/spec/tracking-plan](https://segment.com/docs/connections/spec/tracking-plan/)
— and "Analytics Academy — Data Collection Best
Practices" —
[segment.com/academy](https://segment.com/academy/);
Mode Analytics' "SQL Tutorial" —
[mode.com/sql-tutorial](https://mode.com/sql-tutorial/) —
for the pattern shapes; the dialect-specific window-
function docs — Snowflake
[docs.snowflake.com/en/sql-reference/functions-analytic](https://docs.snowflake.com/en/sql-reference/functions-analytic),
BigQuery
[cloud.google.com/bigquery/docs/reference/standard-sql/analytic-function-concepts](https://cloud.google.com/bigquery/docs/reference/standard-sql/analytic-function-concepts),
PostgreSQL
[postgresql.org/docs/current/tutorial-window.html](https://www.postgresql.org/docs/current/tutorial-window.html).
The analytics-stack vocabulary (ingest / warehouse /
transform / reverse-ETL) is a working composite of
Segment / RudderStack docs, the dbt documentation
([docs.getdbt.com](https://docs.getdbt.com/)), and
Hightouch / Census vendor documentation
([hightouch.com/docs](https://hightouch.com/docs);
[docs.getcensus.com](https://docs.getcensus.com/)).
