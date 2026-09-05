# Exercise 4 — Platform vs point-product bet drill

**Time:** ~3 hours. **Deliverable:** a two-page written bet
defense for your product, covering the aggregation read, the
platform-scale read, and the strategy-stack read, closing with
a pre-registered falsifier and a named deferral.

## Purpose

Author the **platform-vs-point-product bet** underneath your
strategy from
[Exercise 1](exercise-01-rumelt-diagnosis-guiding-policy-coherent-action-drill.md)
using the three lenses in
[Lecture 4](../lectures/04-platform-vs-point-product-bet.md):
Ben Thompson's aggregation theory, Sangeet Choudary's platform
scale, and Casey Winters's product strategy stack. The exercise
forces you to commit — in writing — to one of *point-product
primary, platform primary, or staged / hybrid* — with an
explicit falsifier and a named deferral for the direction you
are not taking.

## What you need before you start

- The strategy memo from
  [Exercise 1](exercise-01-rumelt-diagnosis-guiding-policy-coherent-action-drill.md).
  The bet lives inside the guiding policy; it should not
  contradict the diagnosis you wrote there.
- Enough understanding of your market's *supply commoditization
  trajectory* to defend an aggregation read. If you don't yet
  have that, spend the first 30 minutes of this exercise
  collecting three current data points on the underlying
  commodity in your market — open-source alternatives,
  reference implementations, model / API price trajectories,
  connector libraries — before writing the memo.

## What the two-page memo must contain

### 1. Aggregation read — one third of a page

Answer, in prose:

- **What is the underlying good in your market, and is it
  commoditizing?** Name the good (inference, connectors,
  compliance data, payments rails, transcription, whatever
  the *unit* of value in your market is). Cite three current
  data points on whether the price of production for that
  good is falling toward marginal cost — open-source
  alternatives, price trajectories, reference
  implementations.
- **Where is the user-relationship / default-choice position
  in your market?** Do customers default-choose your surface
  for this job-to-be-done, do they default-choose a
  competitor's, or do they still default to a workaround
  (spreadsheet, script, manual process)?
- **Given the answers above, is an aggregation position
  available?** If yes, on what timeline? If not, why not?

Cite Thompson's *"Aggregation Theory"* (July 2015 —
[stratechery.com/2015/aggregation-theory](https://stratechery.com/2015/aggregation-theory/))
and *"Defining Aggregators"* (Feb 2017 —
[stratechery.com/2017/defining-aggregators](https://stratechery.com/2017/defining-aggregators/))
as the lens; do not just describe the market.

### 2. Platform-scale read — one third of a page

Answer, using Choudary's platform-scale frame ([*Platform
Scale*, Platform Thinking Labs, 2015 —
platformed.info/books](https://platformed.info/books/); also
Van Alstyne / Parker / Choudary, "Pipelines, Platforms, and
the New Rules of Strategy," HBR, April 2016 —
[hbr.org/2016/04/pipelines-platforms-and-the-new-rules-of-strategy](https://hbr.org/2016/04/pipelines-platforms-and-the-new-rules-of-strategy)):

- **Which side of the platform is scarce?** Producers
  (developers, integrators, agent authors) or consumers
  (end users, buyers, requesters)?
- **What is your initial-side strategy?** How will you seed
  the scarce side — internal team as first producer, partner
  deals, subsidies, direct SDK outreach, developer-relations
  investment? Concrete moves, not "we'll launch a
  developer program."
- **On what horizon do you expect the scarce side to be
  self-sustaining?** Number of quarters, with a defined
  measure of self-sustaining (external producers as fraction
  of total, growth rate, retention of producers).
- **What are the cross-side network effects you expect?**
  Do more producers attract more consumers, and vice-versa?
  Or are you actually building a marketplace of
  undifferentiated suppliers with no user pull (Choudary's
  warning)?

If any of the four answers is *"we don't know yet,"* the
platform bet is not yet a bet — it is an aspiration, and
the memo should say so and default to point-product with a
discovery plan for the platform read.

### 3. Strategy-stack read — one third of a page

Position the bet inside the six layers of Winters's product
strategy stack ("The Product Strategy Stack," 2019 —
[caseyaccidental.com/the-product-strategy-stack](https://caseyaccidental.com/the-product-strategy-stack/)):

- **Product vision (layer 3).** One sentence — what does
  the product look like when you've won? Does the vision
  imply platform, point-product, or both? A vision that
  can only be achieved via a platform makes the platform
  bet load-bearing; a vision that can be achieved
  point-product makes the platform bet a hedge.
- **Product strategy (layer 4).** The bet itself, in one
  sentence: *"we are betting point-product primary, staging
  the platform bet as a follow-on"* or the equivalent.
- **Coherence check.** If you removed the platform bet
  from your strategy, would the rest of the strategy still
  cohere? If yes, the bet is a hedge and you should be
  clear about that; if no, the bet is load-bearing and the
  strategy depends on it holding up.

### 4. The bet, the deferral, and the falsifier — one third of a page

Close the memo with:

- **The bet.** In one paragraph: point-product primary,
  platform primary, or staged / hybrid. Name what capacity
  is being allocated where, at what ratio, this year.
- **The deferral.** Whatever direction you are *not*
  primarily investing in this year. Name it as a deferral
  with reason (from the memo above) and move-in signal
  (what would move it out of deferral).
- **The falsifier.** A pre-registered signal that would
  tell you the bet was wrong. For platform: a fraction of
  workflows / requests / revenue running through external
  producers, on a horizon. For point-product: an
  aggregation-position signal in the deferred direction
  (competitor takes the aggregator seat, commoditization
  accelerates faster than expected).

## Starter guidance

- **Do not read Thompson without the market data.** If you
  cannot cite three data points on your underlying-good
  commoditization, you are running the lens on vibes.
- **The Choudary section is where most memos fail.** The
  seeding strategy is the hardest thing to write concretely
  and the easiest thing to hand-wave. If your seeding
  strategy is *"we'll do developer marketing,"* you don't
  have one.
- **Steelman the direction you're *not* taking.** If you're
  betting point-product, write the best defense you can of
  the platform bet in the deferral section. If your best
  defense is stronger than your bet, the bet may be wrong.
- **The bet is one direction, primary.** *"Staged / hybrid"*
  is legitimate but has to be specific — this quarter is
  X% capacity into point-product and Y% into platform
  foundations, sequenced by a named signal that flips the
  ratio. A hybrid without a specified ratio is the
  *both-simultaneously* failure from Lecture 4.
- **The falsifier should be uncomfortable.** If naming it
  costs nothing, it is too loose.

## Acceptance criteria

- Two pages. All four sections above.
- Aggregation read cites three current data points on
  underlying-good commoditization.
- Platform-scale read answers all four Choudary questions
  (scarce side, seeding strategy, horizon, cross-side
  effects).
- Strategy-stack read positions the bet at layer 4, with
  the coherence check answered explicitly.
- The bet is one primary direction, with capacity
  allocation named.
- The deferral is named with reason and move-in signal.
- The falsifier has a metric and a horizon and is not
  written to feel comfortable.

## Common failure modes

- **Aggregation-as-cliché.** *"AI is a commodity so we need
  to be the aggregator."* Not an aggregation read. What
  specifically is commoditizing, on what timeline, and does
  your user-relationship position support the aggregator
  seat?
- **Platform-as-default.** *"We're building a platform."*
  Choudary's whole book is written against this. Which
  side is scarce, how are you seeding it, and what is the
  falsifier?
- **Both-simultaneously without a ratio.** The three
  first-CPO failure modes from Lecture 4 include the
  *both-simultaneously* mode; a staged / hybrid bet without
  a numeric capacity ratio and a stage-gate signal is a
  hedge in disguise.
- **Strategy-stack skipped.** If you go straight from
  "the market is commoditizing" to "so we're building a
  platform" you have skipped layer 3 (product vision).
  The bet has to be coherent with the vision, not just
  the market read.
- **Bet without a deferral.** Every bet has an implied
  deferral. Name it, or it is not a bet — it is an
  aspiration.
- **Falsifier that reads as a KPI.** *"We will monitor
  external adoption"* is not a falsifier. *"If <5% of
  workflows run through external integrators after 6
  quarters, the platform bet was wrong"* is a falsifier.

## Source alignment

The three lenses are from Ben Thompson, "Aggregation
Theory," *Stratechery*, July 2015 —
[stratechery.com/2015/aggregation-theory](https://stratechery.com/2015/aggregation-theory/);
Sangeet Paul Choudary, *Platform Scale*, Platform Thinking
Labs, 2015 —
[platformed.info/books](https://platformed.info/books/); and
Casey Winters, "The Product Strategy Stack," 2019 —
[caseyaccidental.com/the-product-strategy-stack](https://caseyaccidental.com/the-product-strategy-stack/).
The pipeline-vs-platform framing at the head of Section 2 is
Van Alstyne, Parker & Choudary, "Pipelines, Platforms, and
the New Rules of Strategy," HBR, April 2016 —
[hbr.org/2016/04/pipelines-platforms-and-the-new-rules-of-strategy](https://hbr.org/2016/04/pipelines-platforms-and-the-new-rules-of-strategy).
