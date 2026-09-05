# Exercise 1 — Monetization model authoring for one product

**Time:** ~3 hours. **Deliverable:** one monetization
model memo — packaging shape, meter, tier structure,
positioning, reference-price research, competitive
alternatives — for a real (or plausible) product, plus
a reviewer's memo on what the model would break on
first.

## Purpose

Author the **monetization model** described in
[Lecture 1](../lectures/01-pricing-as-a-product-surface.md)
and [Lecture 3](../lectures/03-packaging-structure-and-metering.md).
The memo is the anchor artifact for the rest of the
module — Exercises 2, 3, 4, and 5 all operate on the
model you author here. Take the time to make it
specific.

The goal is not a full pricing recommendation with
dollar figures. Willingness-to-pay evidence
(Exercise 3) and experiment design (Exercise 4)
sharpen the numbers later. The goal here is a
**defensible packaging shape and meter** — the load-
bearing choices from
[Lecture 3](../lectures/03-packaging-structure-and-metering.md) —
plus the framing that says *why* this is a product
surface the CPO owns and not a marketing hand-off.

## Choosing the product

Use one product you can name concretely. In order of
preference:

1. **The product at the company you're currently
   working at (or about to join).** The memo is
   real; the ownership fight is real; the reviewer's
   memo has stakes.
2. **A product you recently worked on and remember
   well enough to describe the current packaging
   shape, meter, and pricing page from memory.**
3. **A product you use daily and know intimately** —
   your CRM, your calendar tool, your code editor,
   your AI-assistant product. Not a product you've
   only read about.
4. **A plausible synthetic** — a pre-seed / seed
   AI-substrate product you can describe in a
   paragraph: what it does, who buys it, what a
   typical use looks like. If you go synthetic,
   write half a page up front naming: current
   headcount, buyer persona, primary use case,
   competitive alternatives, and current pricing
   (if any). The model cannot be judged in the
   absence of them.

Whichever you pick, the artifact is authored *as if
you were the founding CPO today* — not as a case
study of what the company already does.

## What the monetization model memo must contain

Six to eight pages, plus a reviewer's memo. Adopt the
shape below, in order.

### 1. Product and buyer (half page)

- **The product in one paragraph.** What it does,
  for whom, in what workflow. If a stranger read
  only this paragraph, they should be able to
  price the product to within a factor of 2.
- **The buyer segments.** Two to four segments,
  named specifically (not "SMB" — "customer support
  managers at 20–100 person e-commerce companies").
  For each: rough headcount / company size, who
  writes the check, what problem the product
  solves for them.
- **The primary competitive alternatives.** For
  each segment, what the buyer would use instead of
  your product — a competitor, a homegrown
  solution, a manual workflow, "doing nothing."

### 2. The meter (one page)

Grounded in
[Lecture 3](../lectures/03-packaging-structure-and-metering.md#question-2--what-is-the-meter).

- **The candidate meters.** List all the meters
  that plausibly fit — seat, active user, usage
  event, output produced, outcome delivered, flat.
- **The value-metric test.** For each candidate:
  does the meter grow monotonically with customer
  value? Does it produce a comprehensible bill?
  Does it match cost-to-serve?
- **The choice.** Which meter you'd pick, and why
  the alternatives fail. Cite the specific
  failure mode from Lecture 3 that the rejected
  meters would produce.
- **The unit definition.** What exactly is one
  meter-unit? "One seat" — a named user? A seat
  can be re-assigned? "One document processed" — a
  page? A logical document? "One resolved ticket"
  — closed by the agent? Closed with human review?
  Ambiguity here will bite in Exercise 5.

### 3. The tier structure (one and a half pages)

Grounded in
[Lecture 3](../lectures/03-packaging-structure-and-metering.md#the-good--better--best-value-ladder).

- **Number of tiers**, with justification. Default
  is three (good / better / best); departure needs
  a segment-based reason.
- **Tier names.** Working names, not marketing
  copy.
- **Feature-inclusion matrix.** A table with tiers
  as columns and capabilities as rows. Every row
  ticked or blank for each tier. Include the
  candidate gates from
  [Lecture 3](../lectures/03-packaging-structure-and-metering.md#question-3--what-gates-the-upgrade):
  SSO, API access, audit log, role-based access
  control, admin controls, custom domains, white
  label, SLA, priority support — check off which
  live in which tier.
- **Value-metric capacity by tier.** How much of
  the meter each tier includes. Concrete numbers
  are OK ("Team tier includes 25 seats"; "Growth
  tier includes 10,000 documents/month"); ranges
  are fine ("~10× the Good tier capacity").
- **Overage rules.** What happens at cap. Auto-
  upgrade, throttle, prompt-to-buy-more, invoice
  overage.
- **Enterprise tier**, if any. Contact-sales or
  public price. Which enterprise-only features
  live only in this tier.

### 4. Positioning and reference product (half page)

Grounded in
[Lecture 2](../lectures/02-willingness-to-pay-research.md#the-reference-product-method).

- **The reference product for each segment.** What
  the buyer would compare your pricing to. A
  competitor product? An in-house build? A
  spreadsheet? "Doing nothing"?
- **The reference price.** What the buyer pays for
  the reference alternative today. Sourced from
  competitor pricing pages, from interviews you
  can cite, or noted as `<!-- needs-research: ...
  -->` if unknown.
- **Your differentiation and where it commands
  premium.** One sentence per segment on where
  your product is meaningfully better than the
  reference, and where you're deliberately not
  better.

### 5. Pricing hypothesis (half page)

Not a final price. A *hypothesis you'd take into
Exercise 3's WTP research*.

- **A price range per tier.** "$29–$49 / Good tier;
  $99–$199 / Better tier; $399–$999 / Best tier /
  contact-sales Enterprise." The ranges should be
  wide (WTP research narrows them).
- **The reasoning.** Where each range comes from
  — reference-product anchoring, cost-plus floor,
  competitor benchmark, prior in-market signal.
- **The bet.** Which segment is the *median buyer*
  (the compromise-effect buyer who lands in the
  middle tier); which segment is the *revenue
  ceiling*; which segment is the *volume floor*.

### 6. Why this is a CPO-owned surface (half page)

Grounded in
[Lecture 1](../lectures/01-pricing-as-a-product-surface.md#what-pricing-as-a-product-surface-means-concretely).

Write the paragraph you would take to the founder-CEO
to explain why you (the CPO) are taking pricing under
your ownership. Reference the five commitments from
Lecture 1: packaging shape, meter, WTP evidence, the
pricing experiment program, the AI-monetization model.
Not confrontational. Just: *"Here's what I'll own;
here's what marketing and sales will still own;
here's what I'll bring to you before I ship it."*

### 7. Ramanujam-failure self-check (quarter page)

Grounded in
[Lecture 1](../lectures/01-pricing-as-a-product-surface.md#ramanujams-four-monetization-failures).

For each of the four Ramanujam failure modes, one
sentence: *"Our current model is (or is not)
vulnerable to this failure because …"*

- Feature shocks (features nobody will pay for)
- Minivations (over-restricted, under-priced
  stripped-down version)
- Hidden gems (feature that would justify a
  premium tier but is buried in a single SKU)
- Undead products (features nobody uses, still
  in the SKU)

### 8. Boundaries — what this memo doesn't cover
### (quarter page)

Explicit deferrals. Reference:
- The base commercial motion is
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum)
  (level 30).
- The unit-economics math is
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum)
  (level 40).
- WTP evidence sharpening is Exercise 3.
- Experiment design is Exercise 4.
- AI-substrate-specific monetization is Exercise 5.

## Starter guidance

- **Author the meter first.** The tier structure and
  the pricing hypothesis both follow from it. A
  tier structure authored before the meter is
  decided will need to be rewritten.
- **Do the value-metric test honestly.** If your
  candidate meter fails the test (doesn't
  correlate with customer value, doesn't match
  cost-to-serve), name it. Don't paper over.
- **Write the feature-inclusion matrix as a real
  table.** Not "the Team tier includes most of the
  advanced features." A specific table with checks
  and blanks.
- **Cite the reference product research.** If you
  don't know what your reference price is,
  `<!-- needs-research: ... -->` and name what
  research would resolve it (a competitor pricing
  page pull, a discovery interview batch,
  analyst report).
- **Keep prices as ranges, not points.** The point
  price comes from Exercise 3. Don't manufacture
  false precision now.

## The reviewer's memo

Half a page, written after the monetization model
memo. Answer:

- **What breaks first?** If you deployed this model
  tomorrow, which of the six common packaging
  failure modes from
  [Lecture 3](../lectures/03-packaging-structure-and-metering.md#common-packaging-failures)
  is most likely to hit you? Why? What in the memo
  structure would prevent it?
- **CPO / CEO ownership friction.** Where in the
  memo is the founder-CEO likely to push back —
  meter choice, tier count, price range, enterprise
  vs. self-serve balance? What is the *specific*
  evidence you'd bring to that pushback conversation?
- **Comparison to today.** For real products: how
  does the model differ from the current one? For
  synthetic: how does it differ from what a first-
  time CPO would produce without the framing this
  module gives?
- **The single thing you don't know.** Every
  monetization model has one open question the memo
  can't resolve. Name yours; note what evidence
  would resolve it; state which subsequent
  exercise (2, 3, 4, or 5) is likely to touch it.

## Acceptance criteria

- Product and buyer section names product concretely,
  names 2–4 buyer segments with a specific
  competitive alternative for each.
- Meter section lists candidate meters, applies the
  value-metric test to each, and justifies the
  choice with reference to
  [Lecture 3](../lectures/03-packaging-structure-and-metering.md#question-2--what-is-the-meter)'s
  vocabulary.
- Tier structure includes a *specific* feature-
  inclusion matrix (checks and blanks, not prose)
  plus capacity-by-tier and overage rules.
- Positioning section names the reference product
  and reference price (or a `needs-research` marker)
  per segment.
- Pricing hypothesis gives *ranges*, not points, per
  tier, with reasoning.
- CPO-ownership paragraph exists and references
  the Lecture 1 five commitments.
- Ramanujam-failure self-check addresses all four
  modes explicitly.
- Boundary section explicitly cites the level-30
  and level-40 peer curricula.
- Reviewer's memo answers all four prompts.

## Common failure modes

- **Meter-by-inheritance.** The memo picks per-seat
  because "that's what SaaS does" without applying
  the value-metric test. Fix: run the test on the
  page, and name the specific value quantity your
  meter tracks.
- **Feature-inclusion prose instead of a matrix.**
  "Business tier includes advanced features" is
  not a feature-inclusion matrix. Write the table.
- **Point prices without WTP.** The memo commits
  to specific dollar figures per tier before
  Exercise 3 runs. Fix: use ranges; note the
  evidence you'd need to narrow them.
- **Undefined meter unit.** "Per document" without
  a rule for what counts as one document. Ambiguity
  bites in Exercise 5 and in real customer
  billing.
- **Enterprise-as-a-SKU without a signal.** The
  memo includes a full Enterprise tier because
  every SaaS has one, without an actual signal
  that enterprise buyers are asking. Reference
  [Lecture 7](../lectures/07-enterprise-dpa-zero-retention-on-prem-gating.md#when-to-build-the-enterprise-packaging-tier):
  build in response to demand.
- **No reference product.** The memo prices without
  naming what customers would compare it against.
  Fix: run the reference-product question against
  each buyer segment before setting prices.

## Source alignment

The overall shape derives from Madhavan Ramanujam &
Georg Tacke, *Monetizing Innovation*, Wiley, 2016,
Chapters 1 and 6 —
[wiley.com/en-us/Monetizing+Innovation](https://www.wiley.com/en-us/Monetizing+Innovation%3A+How+Smart+Companies+Design+the+Product+Around+the+Price-p-9781119240860).
The tier-structure and value-metric discipline
derives from that book combined with Kyle Poyar's
writing at OpenView / Growth Unhinged —
[growthunhinged.com](https://www.growthunhinged.com/).
The CPO-ownership framing derives from
[Lecture 1](../lectures/01-pricing-as-a-product-surface.md).
