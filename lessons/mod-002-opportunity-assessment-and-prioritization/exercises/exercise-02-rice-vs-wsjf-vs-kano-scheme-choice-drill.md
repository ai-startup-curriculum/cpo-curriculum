# Exercise 2 — RICE vs WSJF vs Kano scheme-choice drill

**Time:** ~2 hours. **Deliverable:** a one-page scheme-choice memo per
scenario (three scenarios below), plus a scored ranking of the sample
opportunity list under your chosen scheme for one of them.

## Purpose

Practice picking the right prioritization scheme *for a given
portfolio shape*, not "the one you like" — and produce a scored
ranking so you feel where each scheme's math actually pinches. The
lecture behind this is
[Lecture 2](../lectures/02-scoring-schemes-and-their-incompatibilities.md).

## The three scenarios

### Scenario A — Growth team at a B2C freemium mobile app

- Product is post-PMF with 400k WAU.
- The team runs 3–5 experiments a week on onboarding, notifications,
  paywall, and referral surfaces.
- Every surface is instrumented; A/B testing is cheap; sample sizes
  are large enough to detect ~2pp changes in 7-day windows.
- The queue has 40+ ideas, most from analytics review or customer
  support triage.

### Scenario B — Enterprise SaaS with a fixed 15-person engineering team

- Deals are 4–8 weeks; ARR per customer is $80k–$400k.
- Prospects consistently ask for **audit logs**, **SSO / SCIM**, and
  **a data-residency guarantee for EU customers** — items that are
  gate conditions for procurement, not differentiators.
- Two live enterprise deals have a *contractual January deadline* for
  SOC 2 Type II readiness or the deals stall.
- Engineering capacity is capacity-constrained; work in flight can't
  parallelize past a certain point.

### Scenario C — Consumer resale marketplace launching a new pricing tier

- Existing product has PMF on the buyer side; sellers are the scarce
  side.
- The team is considering a *premium seller subscription* with
  concierge listing, priority placement, and reduced take-rate.
- The bet is meaningful — potentially a new revenue stream, potentially
  a distraction from the marketplace's core liquidity work.
- There is no reference class for this specific tier in this
  marketplace; competitor examples exist but generalize poorly.

## Tasks

For **each of the three scenarios**:

1. **Pick a scheme.** RICE, ICE, WSJF, or *Kano-first classification
   followed by inside-bucket ranking* (Lecture 2 walks through each).
2. **Defend the choice in one page.** Answer:
   - What ranking question does this scenario actually pose? (comparison
     of many similar items, arbitration among a few expensive bets,
     gate-vs-differentiator classification, capacity-flow queueing?)
   - Which properties of the scheme match that question (countable
     reach, time-decay of value, classification vs. ordering, etc.)?
   - Which of the scheme's known weaknesses (Lecture 2) will bite in
     this scenario, and how will you mitigate?
   - What ordinal anchors will you use? Give at least two — e.g.,
     *"Impact 3 = matches Q3-onboarding-experiment lift of +5pp,"*
     *"CoD 8 = comparable to last SOC 2 gap that stalled two deals."*
3. **Name at least one scheme you rejected and say why.**

Then pick **one** of the three scenarios and:

4. **Score and rank** the sample opportunity list below under your
   chosen scheme. Show your work in a table.
5. **Write a two-sentence sanity check.** What would you re-examine
   about the ranking before shipping it? (e.g., "the top item scored
   high because effort was estimated at 1 week — I'd re-estimate
   before committing.")

## Sample opportunity list (use for the ranking task)

Six candidate items. Adapt to your chosen scenario — for Scenario B
some items don't apply; note which and skip.

| # | Item | Rough shape |
|---|---|---|
| 1 | Reduce onboarding step count from 5 → 3 | Consumer-app funnel; A/B-testable |
| 2 | Ship SSO / SCIM (Okta, Azure AD) | Enterprise gate; ~10 eng-weeks |
| 3 | Launch premium seller subscription pilot | New revenue surface; multi-quarter |
| 4 | Add push-notification personalization | Consumer growth; ML-adjacent |
| 5 | Ship EU data-residency deployment | Enterprise gate + regulatory deadline |
| 6 | Rework referral flow to 2-sided reward | Consumer growth; measurable |

You do not need real numbers — plausible estimates with your
uncertainty attached are fine. The point is the shape of the
comparison, not the precision.

## Starter guidance

- **Read the scenario for the *question first*, not the *items first*.**
  What are you actually being asked to rank? Growth-experiment triage,
  procurement-gate scheduling, and multi-quarter bet arbitration are
  three different questions.
- **Watch for scheme-mismatch tells.** If the top-ranked item under
  RICE is *"ship SOC 2 gap"*, RICE is wrong for this scenario — SOC 2
  is a gate, not a graduated impact, and Kano would say so first.
- **Write anchors before you score.** If you can't write two anchors
  for the ordinal scale, you don't have enough reference class to use
  the scheme; the anchor-writing failure is itself a finding.
- **In Scenario C especially, resist the urge to score.** The lecture
  argues that strategic bets should not enter a RICE spreadsheet; if
  your chosen scheme for C is a scored one, be very explicit about
  what you're giving up.

## Acceptance criteria

- A one-page memo per scenario, each ≤ 500 words.
- Each memo names one primary scheme, one rejected scheme, and the
  reason for both.
- Each memo lists at least two ordinal anchors specific to the
  scenario (not generic "3 = high").
- Your ranked table for the chosen scenario shows the components
  (Reach, Impact, Confidence, Effort — or CoD components — or Kano
  category) as separate columns; the final score is not hand-computed
  in your head.
- Your sanity check names one specific re-examination step, not "we
  should double-check the numbers."

## Common failure modes

- **Applying the same scheme across all three scenarios.** The point
  of the drill is that no single scheme fits all three.
- **Scoring strategic bets on RICE as if the Reach and Impact were
  known.** For Scenario C, an honest RICE would have Confidence at
  10–20%, which drives the score to noise. That's the tell that the
  scheme is wrong for the item.
- **Ignoring capacity flow in Scenario B.** SSO ships before SOC 2 or
  vice-versa depending on the sequence, and the sequence matters.
  WSJF is designed for this shape; a pure RICE rank is not.
- **Missing the deadline in Scenario B.** The January SOC 2 deadline
  is a time-criticality term; a scheme that doesn't have a term for
  time-decay of value is the wrong choice.

## Source alignment

- RICE — [McBride, "RICE: Simple prioritization for product managers,"
  Intercom, 2016](https://www.intercom.com/blog/rice-simple-prioritization-for-product-managers/).
- ICE — [Ellis & Brown, *Hacking Growth*, Currency, 2017, Chapter 6,
  "Testing at High Tempo"](https://www.hachettebookgroup.com/titles/sean-ellis/hacking-growth/9780451497215/).
- WSJF — [Reinertsen, *The Principles of Product Development Flow*,
  Celeritas, 2009, Chapter 5, "Managing Queues"](https://celeritaspublishing.com/product/the-principles-of-product-development-flow/);
  [SAFe, "Weighted Shortest Job First," scaledagileframework.com —
  framework.scaledagile.com/wsjf](https://framework.scaledagile.com/wsjf/).
- Kano — [Kano, Seraku, Takahashi & Tsuji, "Attractive Quality and
  Must-Be Quality," 1984 — ASQ summary at
  asq.org/quality-resources/kano-model](https://asq.org/quality-resources/kano-model).
