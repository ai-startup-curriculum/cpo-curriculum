# Exercise 2 — Good / better / best packaging drill

**Time:** ~2 hours. **Deliverable:** one good / better /
best packaging spec — three tiers, feature-inclusion
matrix, value-metric capacity per tier, upgrade / down-
grade path, price ratios — for the product you named in
Exercise 1, plus a Simon-Kucher-style value-alignment
plot and a reviewer's memo.

## Purpose

Sharpen the tier structure from
[Exercise 1](exercise-01-monetization-model-authoring-for-one-product.md)
into a **shippable good / better / best packaging
spec**, following the discipline from
[Lecture 3](../lectures/03-packaging-structure-and-metering.md#the-good--better--best-value-ladder).

Exercise 1 established the *shape* of the tier
structure. This exercise makes it *concrete enough
to hand to eng and marketing* — every feature placed,
every gate justified, every price ratio defended,
every failure mode from the Lecture 3 list
inspected.

## Prerequisites

- [Exercise 1](exercise-01-monetization-model-authoring-for-one-product.md)
  complete — the meter and rough tier shape are the
  input to this exercise.

## What the packaging spec must contain

Three to four pages. Follow the sections below in
order.

### 1. Tier lineup (quarter page)

- **Number of tiers.** Confirm the choice from
  Exercise 1 or update it, with justification. If
  you're departing from three, cite the specific
  segment-based reason from
  [Lecture 3](../lectures/03-packaging-structure-and-metering.md#question-1--how-many-tiers).
- **Tier names.** Working names or (if you're
  ready) marketing names. Naming convention:
  functional ("Team / Business / Enterprise") or
  aspirational ("Grow / Scale / Custom") — pick
  and be consistent.
- **The compromise-effect middle tier.** Which tier
  is designed as the *default choice*. Which
  buyer segment lands in it. Why the ladder pushes
  buyers toward it.

### 2. Feature-inclusion matrix (one page)

Grounded in
[Lecture 3](../lectures/03-packaging-structure-and-metering.md#the-good--better--best-value-ladder).

A single table. Rows are capabilities; columns are
tiers. Cells are checked or blank. Include:

- **Core product features** — the primary
  capabilities of the product. Every tier should
  include these; if not, name the exception.
- **Team / collaboration features** — sharing,
  workspace, comments, member management.
- **Admin features** — role-based access control,
  audit log, admin API, user provisioning.
- **Security / compliance features** — SSO
  (SAML, OIDC), advanced authentication, audit
  export, data-residency selection.
- **API / integration features** — public API,
  webhooks, SDKs, third-party connectors.
- **Support features** — email support, chat,
  priority queue, dedicated CSM, SLA.
- **AI-substrate features** (if applicable) —
  model tier selection, custom prompts, agent
  capabilities, eval access. Referenced from
  [Lecture 6](../lectures/06-ai-product-monetization-models.md).
- **Deployment / DPA features** (if any) —
  standard DPA, custom DPA, VPC deployment.
  Referenced from
  [Lecture 7](../lectures/07-enterprise-dpa-zero-retention-on-prem-gating.md).

For each row, the placement decision should
correspond to the four-way test from
[Lecture 3](../lectures/03-packaging-structure-and-metering.md#the-good--better--best-value-ladder):

- Everyone → Good tier
- Most, especially teams → Better tier
- Sophisticated / large buyers only → Best tier
  (or Enterprise)
- Nobody actually uses / wants this → cut

Every "Best tier only" placement gets a one-sentence
justification (who specifically wants this, what
willingness-to-pay signal supports the gating).

### 3. Value-metric capacity per tier (half page)

Grounded in the meter chosen in Exercise 1.

- **How much of the meter each tier includes.**
  Specific numbers (seats, events, documents,
  outcomes, credits — whatever your meter unit
  is). Ranges are OK if you don't have WTP data
  yet.
- **The ratio between tiers.** Better should
  typically include ~5–10× the capacity of Good;
  Best should include ~5–10× the capacity of
  Better. Cite the source of your ratio.
- **What "unlimited" means** for the top tier, if
  applicable. Fair-use policy? Contract cap?
  Contact-sales when you exceed?

### 4. Gate types per tier (quarter page)

Grounded in
[Lecture 3](../lectures/03-packaging-structure-and-metering.md#question-3--what-gates-the-upgrade).

Name explicitly which gate type moves each buyer
segment between tiers:

- Feature gate → what feature
- Capacity gate → what value-metric cap
- Support / SLA gate → what service level
- Hybrid → which mix

## 5. Upgrade and downgrade paths (quarter page)

- **Upgrade trigger.** What in-product signal causes
  a Good-tier buyer to consider upgrading. Hitting
  a capacity cap? Wanting a specific feature?
  Being invited to a paid workspace?
- **Upgrade friction.** How many clicks from
  "I want to upgrade" to "I'm on the new tier."
  Payment on file? Approval workflow? Requires
  admin?
- **Downgrade path.** Can a Better-tier buyer
  downgrade to Good self-serve? What happens to
  their data (features become read-only? get
  deleted?)? Is there a grace period?
- **Downgrade defense.** What in-product signal
  fires when a customer initiates a downgrade —
  is there a save / retention flow? What does it
  offer?

### 6. Price ratios (quarter page)

Grounded in
[Lecture 3](../lectures/03-packaging-structure-and-metering.md#the-good--better--best-value-ladder).

- **Absolute price ranges per tier**, from
  Exercise 1's hypothesis or updated.
- **The ratio between tiers.** Ratio of Better to
  Good; ratio of Best to Better; overall Best-to-
  Good ratio. Compare to the roughly 1 : 3 : 6 to
  1 : 4 : 10 range Lecture 3 cites.
- **Justification for the ratio.** Push middle-
  tier adoption (larger ratio)? Preserve
  self-serve accessibility (smaller ratio)?
  Match a competitor's ratio?

### 7. Value-alignment plot (half page)

Grounded in
[Lecture 3](../lectures/03-packaging-structure-and-metering.md#the-simon-kucher-price--value-alignment).

Draw the plot (or sketch it in ASCII / markdown).
X-axis: relative value delivered (from WTP
evidence, from the feature-inclusion matrix, from
qualitative discovery signal). Y-axis: relative
price.

- **Plot the three (or four) tiers as points.**
- **Draw the best-fit line through them.** It
  should be increasing and roughly straight.
- **Note any deviations.** A tier above the line
  is over-priced for its value; below the line is
  under-priced. Both are packaging problems.
- **State what you'd change** if a tier deviates
  meaningfully.

### 8. Failure-mode inspection (quarter page)

Grounded in
[Lecture 3](../lectures/03-packaging-structure-and-metering.md#common-packaging-failures).

For each of the six packaging failure modes, one
sentence: *"This packaging is (or is not)
vulnerable to this failure because …"*

- Feature bloat in the middle tier
- Empty middle tier
- Enterprise-only gate on a self-serve feature
- Punitive overage
- Meter that doesn't match cost
- Meter that doesn't match value

## Starter guidance

- **Do the feature-inclusion matrix on paper (or in
  a spreadsheet) before you write prose.** The
  matrix is the load-bearing artifact; the prose is
  commentary on it.
- **Ask "what's the middle-tier buyer's job?" for
  each row.** If the middle-tier buyer wouldn't
  notice a feature missing, put it in the top
  tier. If they'd notice its absence and switch
  tools, put it in the middle tier.
- **Watch for creeping-Best.** If every
  ambiguous-placement feature ends up in Best,
  you'll ship an empty middle tier. Discipline
  yourself: half of the ambiguous features
  should land in the middle.
- **Sketch the value-alignment plot before you
  finalize prices.** If the plot shows a kink,
  either the prices are wrong or the tier value
  differences are wrong. Fix before shipping.
- **Draft the downgrade flow explicitly.** Most
  founding CPOs skip this and discover in month 6
  that customers who wanted to downgrade churned
  instead. The downgrade flow is a retention
  surface.

## The reviewer's memo

Quarter page, written after the packaging spec.
Answer:

- **Which tier is the compromise-effect middle?**
  Is it obvious from the ladder shape? If a
  reviewer read only the pricing page, would they
  land in the middle tier without prompting?
- **What's in Best that isn't in Better and why?**
  List the three most differentiating Best-only
  features. For each, name the buyer segment that
  will actually pay for it (not "large customers"
  — a specific segment).
- **The one row in the matrix you're least sure
  of.** Which capability's tier placement is the
  wobbliest decision in the memo? What evidence
  from Exercise 3's WTP research would resolve it?
- **How this differs from today.** For real
  products: what changed between this spec and
  the current pricing page? For synthetic: what's
  different from the default a first-time CPO
  would ship?

## Acceptance criteria

- Tier lineup names 3 (or a justified departure)
  tiers with working names and identifies the
  compromise-effect middle tier.
- Feature-inclusion matrix is a real table with
  checks and blanks across ≥ 15 capability rows.
- Every Best-tier-only placement has a one-
  sentence buyer-segment justification.
- Value-metric capacity is stated per tier with a
  ratio between tiers.
- Gate types (feature / capacity / support /
  hybrid) are named per tier.
- Upgrade *and* downgrade paths are documented,
  including the downgrade defense flow.
- Price ratios are stated and compared to the
  1 : 3 : 6 → 1 : 4 : 10 range from Lecture 3.
- Value-alignment plot exists (sketch is fine) and
  shows the three tiers with a fitted line.
- Failure-mode inspection addresses all six
  Lecture 3 modes explicitly.
- Reviewer's memo answers all four prompts.

## Common failure modes

- **Matrix written as prose.** "Team tier
  includes team collaboration; Business tier
  includes advanced admin." Not a matrix. Write
  the table.
- **Best tier as a dumping ground.** Every
  ambiguous feature lands in Best. Middle tier
  has nothing distinctive. Ladder collapses to
  Good-vs-Best; middle is empty.
- **Symmetric ratios that flatten the ladder.**
  1 : 1.5 : 2.25 ratios don't push buyers toward
  the middle — they blur the tiers. Widen the
  ratios.
- **Downgrade path unwritten.** Customers who want
  to downgrade churn instead because the flow
  doesn't exist. Design the downgrade the way you
  design the upgrade.
- **Enterprise-only features that middle-tier
  buyers legitimately need.** SSO on Enterprise-
  only in a $500/mo product; audit log on
  Enterprise-only when a $2k/mo team has
  compliance requirements. Every such placement
  needs a specific justification.
- **Value-alignment plot skipped.** The plot
  reveals structural problems fast. Skipping it
  ships packaging that customers experience as
  "this pricing doesn't make sense."

## Source alignment

The good / better / best discipline derives from
Madhavan Ramanujam & Georg Tacke, *Monetizing
Innovation*, Wiley, 2016, Chapter 6, and the
Simon-Kucher literature on multi-tier packaging —
[simon-kucher.com](https://www.simon-kucher.com/en).
The compromise-effect reasoning derives from the
consumer-choice literature summarized in Ramanujam
& Tacke. The value-alignment plot is a founding-
CPO simplification of the Simon-Kucher price /
value alignment tool.
