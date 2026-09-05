# Exercise 1 — Opportunity assessment authoring for three real bets

**Time:** ~3 hours. **Deliverable:** three completed opportunity
assessments, one page each, plus a half-page reviewer's memo comparing
them.

## Purpose

Turn three real (or near-real) roadmap candidates into bounded
opportunity statements you could take into a ranking exercise. The
practice is in *authoring* — writing the four-sentence frame from
[Lecture 1](../lectures/01-opportunities-as-bounded-problems.md) — not
in ranking. Ranking is Exercise 2.

## The bets

Pick three candidate items from the roadmap of a real product you can
name. Acceptable sources:

- The product at the company you're joining or currently working at.
- The last product you worked on, if you can still remember its numbers.
- A plausible synthetic product **you can defend the shape of** — e.g.,
  an agentic-workflow tool for a vertical you know, a marketplace for a
  segment you know, a devtool you'd yourself buy. If you go synthetic,
  write half a page up-front naming the customer, the segment, the
  pricing shape, and the current stage; the exercise depends on those.

The three items should be genuinely different. A good spread:

1. A **base-rate optimization** item (funnel, activation, retention).
2. A **strategic bet** item (new surface, new segment, new pricing
   tier, new integration platform).
3. A **founder-sourced hypothesis** — an item the founder-CEO has
   raised that does not yet have discovery evidence attached.

If the roadmap in front of you doesn't have all three shapes on it,
your first finding is that the roadmap is imbalanced; note that in the
reviewer's memo.

## What each assessment must contain

Use the shape from
[Lecture 1](../lectures/01-opportunities-as-bounded-problems.md) —
four sentences, in this order, no more than one page total:

1. **Whose problem is it?** Segment named tight enough that a stranger
   could recruit five candidates in an hour. Explicit exclusions
   (*"not: consumer users; not: enterprise-only accounts"*) are
   welcome — they sharpen the frame.
2. **What is the problem, in their words?** A verbatim clause from an
   interview transcript, a support ticket, a sales call recording, or
   a community post. Cite the source (interviewee pseudonym + date, or
   ticket ID). If you have no verbatim evidence, mark the assessment
   *"hypothesis, no interview evidence"* and note the discovery step
   that would produce evidence.
3. **What outcome does solving it move?** Name a specific company
   outcome (activation, week-4 retention, cost-to-serve, ARR in a
   segment). Give a rough magnitude with your uncertainty attached
   (*"we think 3–6 percentage points on week-4; wide range because
   we have one cohort of prior data to compare to"*).
4. **What would tell you you're wrong?** A pre-registered falsifier.
   Both a numeric threshold and a time horizon (*"if we ship the top
   solution and week-4 moves <1pp in the following two cohorts, we
   kill this line"*).

Also include, on the same page:

- **Assumptions** — up to five, one line each, that would need to be
  true for the outcome to move. These become the assumption-test
  branch of the opportunity solution tree.
- **Estimated effort** — engineering weeks or a t-shirt size; the
  point is to force a shape estimate, not to commit an SLA.
- **Author** and **date**.

## Starter guidance

- **Start with the verbatim.** Pull the customer-worded sentence
  first, then write the whose/outcome/falsifier around it. If you
  start with the outcome ("we want to lift retention"), you'll
  reverse-engineer a customer problem that fits, and it will show.
- **Resist rewriting the customer's phrasing.** Their words are the
  point. If you find yourself "cleaning up" the quote to sound more
  polished, you're solution-capturing the opportunity.
- **The falsifier is the hardest sentence.** It should feel a little
  uncomfortable — a threshold you actually think might trip. If
  writing it feels safe, it's too loose; tighten it.
- **Founder-sourced items are welcome and should be marked as such.**
  Do not launder the founder's confidence into fabricated interview
  evidence. The point of the assessment is that the founder-sourced
  version comes into the ranking exercise honestly labeled.

## The reviewer's memo

Half a page, written after the three assessments. Answer:

- Which of the three would you fund first if the assessments were all
  you had? Why?
- Which of the three has the weakest evidence? What's the cheapest
  discovery step that would move it?
- Which of the three would be hardest to write a *falsifier* for, and
  what does that difficulty tell you about the item?

## Acceptance criteria

- Each assessment fits on one page.
- Each has all four sentences plus assumptions, effort, author, date.
- Each is either backed by verbatim customer evidence with a source
  citation, or explicitly labeled *"hypothesis, no interview evidence"*
  with a discovery next-step named.
- The three assessments span the three shapes (base-rate, strategic,
  founder-sourced) or the reviewer's memo flags that they don't.
- The reviewer's memo names a first-fund pick and defends it in one
  sentence a stranger could follow.

## Common failure modes

- **Rewriting features as opportunities.** *"Users need a Slack
  integration"* is a solution wearing an opportunity's hat. The
  opportunity underneath is a job the user is trying to make progress
  on, described in their language.
- **Blended segments.** *"SMBs and enterprises both need this"* — no
  they don't; they need related-looking things for different reasons.
  Pick one and be explicit about the other.
- **Aspirational outcomes.** *"This will help us dominate the market"*
  is not an outcome; it's a mood. Name the metric.
- **Missing falsifiers.** An assessment without a falsifier is a wish
  list, not a bet. The falsifier is the discipline; it's not optional.

## Source alignment

The four-sentence shape derives from Marty Cagan's opportunity-
assessment technique
([Cagan, *Inspired*, 2nd ed., Wiley, 2017, Chapter 22](https://www.svpg.com/inspired-how-to-create-products-customers-love/);
[SVPG, "Product Manager Prep Work: Opportunity Assessment," 2007 —
svpg.com/product-manager-prep-work-opportunity-assessment](https://www.svpg.com/product-manager-prep-work-opportunity-assessment/))
and Teresa Torres's discipline of *customer-worded opportunities on
the opportunity solution tree*
([Torres, *Continuous Discovery Habits*, Product Talk, 2021,
Chapter 6](https://www.producttalk.org/continuous-discovery-habits/)).
The falsifier discipline is Steve Blank's Customer Development frame
(mod-001, Lecture 1) applied to the ranking queue.
