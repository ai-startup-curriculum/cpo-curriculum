# Exercise 1 — North-star and input-metric authoring

**Time:** ~3 hours. **Deliverable:** one one-page **metric
taxonomy** — north-star metric, 2–3 input metrics, 3–5
guardrails, review cadence, and a 12-month defense — for a
real (or plausible synthetic) product, plus a half-page
reviewer's memo on what would force a rewrite inside 12
months.

## Purpose

Author the taxonomy
[Lecture 1](../lectures/01-north-star-and-input-metric-taxonomy.md)
spent the module teaching: a Sean-Ellis-shape **north-star
metric** at the top, Andrew-Chen-shape **input metrics**
underneath, and Kohavi-style **guardrails** that catch the
ways a moving north-star can lie
([Ellis & Brown, *Hacking Growth*, Chapter 3](https://hackinggrowth.com/);
[Amplitude, *North Star Playbook*](https://amplitude.com/books/north-star);
[Chen, *The Cold Start Problem*, Part IV](https://andrewchen.com/the-cold-start-problem-book/);
[Kohavi, Tang & Xu, *Trustworthy Online Controlled Experiments*, Chapter 21](https://experimentguide.com/)).
The taxonomy you author here is the input every other
exercise in this module depends on — Exercise 2 reads
retention against it, Exercise 3 sizes an A/B that moves an
input, Exercise 6 writes SQL against it. If you skip this
one, the rest become generic.

## Choosing the product

Use one product you can name concretely, in this order of
preference:

1. **The product at the company you're currently working at
   (or about to join).** The taxonomy memo is real; you can
   defend it in your next 1:1 with the founder-CEO.
2. **A product you ran closely enough in the last 24 months
   that you can name the growth loop and the activation
   event from memory.**
3. **A plausible synthetic** — a pre-seed → Series-A
   AI-native product you can specify in two paragraphs.
   If you go synthetic, write half a page up front naming:
   the value proposition in one sentence, the primary user
   segment (and the buyer, if different), the growth loop
   (viral, content, outbound, paid), the current stage of
   PMF (mod-001 — have you got pull yet?), and the AI
   substrate (is any critical surface a stochastic LLM
   output?). The taxonomy cannot be judged in the absence
   of these.

Whichever you pick, author the memo *as if you were the
founding CPO today*, not as a case study of someone else.

## What you need before you start

- A clear-enough product description that you can state
  the one-sentence *value proposition* ("the user hired
  this product to do X"). If you can't, you are in mod-001
  territory, not mod-005; the taxonomy will drift because
  the value proposition it points at is unresolved.
- A rough sense of the **growth loop** that drives the
  product
  ([Lecture 1 — Input metrics section](../lectures/01-north-star-and-input-metric-taxonomy.md#input-metrics--andrew-chens-growth-loop-framing)).
  "Acquisition × activation × retention" is a default; if
  your product is a marketplace, a social product, or a
  content product, the loop looks different — name it.
- An awareness of which **unit** matters (user, team,
  account, workspace, session). B2B products usually
  taxonomize at the team / account level, not the user
  level; getting this wrong is one of the four 12-month
  failure modes.

## What the taxonomy memo must contain

One page (the forcing function; a taxonomy requiring three
pages won't land with the team), structured as follows.
Use the one-page layout from
[Lecture 1](../lectures/01-north-star-and-input-metric-taxonomy.md#the-taxonomy-on-one-page)
as the template.

### 1. North-star metric

- **The metric itself**, in the shape *<count-of-value-
  bearing-event> per <time-window> per <unit>, for <segment>*.
  Not "revenue," not "DAU," not "a dashboard." A specific
  count of a specific event, scoped to a specific unit.
- **The three Lecture 1 tests, answered explicitly**:
  does the user get value when this event fires? Can the
  product team move it? Does its cadence match the
  product's natural use frequency?
  ([Lecture 1 — The north-star, defined](../lectures/01-north-star-and-input-metric-taxonomy.md#the-north-star-defined).)
- **One or two named precedents** from the working
  literature your north-star shape resembles (Slack
  messages-sent-by-active-team, Airbnb nights-booked,
  Amplitude weekly-learning-users). You are not required
  to match a precedent; you are required to be able to say
  why your shape is in the same *family*.
- **Explicit anti-shapes.** State the two metrics you
  considered and rejected (likely some flavor of revenue
  and some flavor of raw activity), and the reason each
  failed the three tests.

### 2. Input metrics

- **Two to three input metrics**, each stated as a weekly
  count that mechanically composes into the north-star.
  Default decomposition is *new-activated × previously-
  active × re-engaged*; departures from this default must
  cite the growth loop that justifies the swap (supply /
  demand / match-rate for marketplaces; creator /
  consumer / loop for content products).
- **The mechanism, named per input.** For each input,
  one sentence on *how it moves the north-star* — if the
  mechanism isn't nameable, the input isn't an input.
- **The owner, per input.** Which function moves it in a
  typical week — product, growth, GTM, platform.

### 3. Guardrails

- **Three to five guardrails** across the four Lecture 1
  dimensions: **quality**, **cost**, **UX**,
  **trust / safety**.
  ([Lecture 1 — Guardrails](../lectures/01-north-star-and-input-metric-taxonomy.md#guardrails--the-metrics-the-north-star-cannot-be-moved-by-breaking).)
- **For AI-substrate products**, at least one guardrail
  must be an eval-set threshold from
  [Lecture 6](../lectures/06-eval-driven-decisions-for-llm-products.md),
  and at least one must be a cost-per-interaction or p95
  latency threshold from
  [Lecture 7](../lectures/07-cost-latency-quality-pareto.md).
  Guardrail-less AI-substrate taxonomies get gamed inside
  one quarter.
- **The threshold, per guardrail.** A guardrail without a
  number is a wish. If the number isn't knowable yet,
  state the *process* for setting it ("after four weeks
  of baseline data").
- **The crediting rule.** State explicitly: "the
  north-star is not credited as moved in any period where
  a guardrail is out of bounds." This is the mechanic
  that prevents the gaming event Lecture 1 opened on.

### 4. Review cadence

- **Weekly.** Who reads the north-star and inputs, with
  what artifact (a Monday dashboard note, a weekly memo,
  a Slack post).
- **Monthly.** Who reads the cohort / segment breakdown
  (this is where Exercise 2 lives in the ongoing
  rhythm).
- **Quarterly.** The *taxonomy re-defense* — is any of
  the above wrong? If the answer is "yes, every quarter,"
  you are rewriting too often and one of the four Lecture
  1 failure modes is in play.

### 5. The 12-month defense

Half a page. Walk through each of the four Lecture 1
failure modes
([Lecture 1 — The 12-month test](../lectures/01-north-star-and-input-metric-taxonomy.md#the-12-month-test))
and state why *this* taxonomy will not fall into it:

- **Not a revenue proxy.** Why the north-star doesn't
  silently become ARR under board pressure.
- **Right scope.** Why user vs. team vs. account is the
  right unit for *this* product's buyer / user / payer
  configuration.
- **Right loop.** Why the input decomposition matches
  the actual growth model, not a template.
- **Not reverse-engineered from the tool.** Why the
  shape derives from the value proposition, not from
  what Amplitude / Mixpanel / PostHog reported by
  default.

Name the one failure mode you are *most* at risk of
falling into. Not "none" — pick one and defend against it
explicitly.

## Starter guidance

- **Author the north-star first, in isolation.** Do not
  look at the inputs or guardrails until the north-star is
  settled; otherwise you'll reverse-engineer the north-star
  from the inputs you already know how to measure. The
  Lecture 1 rule: the shape derives from the *value
  proposition and growth model*, not from the analytics
  tool's default panel.
- **Resist the two-metrics temptation.** If you catch
  yourself writing "the north-stars are X and Y," you have
  a hierarchy problem — pick one, make the other the top
  input or a guardrail. Sean Ellis's *Hacking Growth* is
  emphatic on this.
- **For B2B products, taxonomize at the right unit.** A
  B2B product's north-star is almost always a team- or
  account-scope metric, not a user-scope one — Slack
  messages-sent-by-active-team is the canonical shape, not
  DAU.
- **If this is an AI-substrate product, the eval-set
  threshold is a guardrail, not an afterthought.** A
  north-star of "weekly value-bearing interactions" with
  no eval-quality guardrail will be moved by shipping
  interactions users don't actually value — the eval set
  is what distinguishes "the model talked" from "the model
  helped."
- **Resist starting from the dashboard.** The failure mode
  the taxonomy prevents is "the metric we have is the
  metric we chose." Author on paper before opening the
  tool.

## The reviewer's memo

Half a page, written *after* the taxonomy memo. Answer:

- **The 12-month failure mode most likely to force a
  rewrite.** Which of the four Lecture 1 failures is the
  one you'd bet gets you? Why? What would you need to see
  to know it's happening early?
- **The founder-CEO challenge.** Imagine the founder-CEO
  pushes back: "why isn't the north-star ARR?" Write the
  one-paragraph defense you'd give.
- **The team-vocabulary test.** Could every engineer,
  designer, and GTM person on the team recite the
  north-star, the three inputs, and the guardrails from
  memory after two weeks? If not, which part is too
  complex to internalize, and how would you simplify it?

## Acceptance criteria

- The taxonomy fits on **one page** in the Lecture 1
  template shape — north-star + inputs + guardrails +
  review cadence + 12-month defense.
- The **north-star** is a specific *<count × window ×
  unit × segment>* statement; the three Lecture 1 tests
  are each answered in one sentence.
- Two to three **input metrics** are stated with a named
  mechanism and owner per input; the decomposition
  matches the product's actual growth loop (and the memo
  says why if it departs from the acquisition × activation
  × retention default).
- **Three to five guardrails** cover the four Lecture 1
  dimensions (quality, cost, UX, trust / safety); each has
  a threshold or a stated process for setting one; the
  crediting rule is explicit. For AI-substrate products,
  an eval-threshold guardrail and a cost / latency
  guardrail are both present.
- A **review cadence** names the owner and artifact for
  weekly, monthly, and quarterly reads.
- The **12-month defense** walks through all four Lecture
  1 failure modes and names the single one most at risk,
  with a specific early-warning signal.
- The **reviewer's memo** answers the three prompts
  (failure mode, founder-CEO defense, team-vocabulary
  test).

## Common failure modes

- **North-star as revenue proxy.** The memo claims the
  north-star is "weekly active teams" but every monthly
  review the taxonomy gets pressure-tested against ARR
  and the team quietly measures ARR instead. The
  crediting rule and the founder-CEO defense are what
  prevent this; author them.
- **Input metrics that don't mechanically compose.** The
  three inputs don't actually add up (or multiply up) to
  the north-star. If you can't write down the composition
  rule, you don't have inputs — you have correlated
  metrics.
- **Guardrails as wishes.** Thresholds like "latency
  should stay low" or "quality shouldn't regress." A
  guardrail without a number cannot be checked and will
  be ignored.
- **Taxonomy at the wrong unit.** B2B product with a
  DAU-shaped north-star; consumer product with a
  monthly-active-accounts shape. The unit mismatch is one
  of the four 12-month failure modes; name the unit
  explicitly and defend it.
- **AI-substrate without an eval guardrail.** The product
  ships LLM outputs; the taxonomy has no quality
  guardrail backed by an eval set. The north-star will
  be moved by shipping volume rather than value.
- **Review cadence as "we'll just know."** No named
  owner, no named artifact, no quarterly re-defense. The
  taxonomy that nobody reads is the taxonomy that gets
  silently rewritten after six months.

## Source alignment

The north-star framing derives from Sean Ellis and Morgan
Brown, *Hacking Growth*, Currency, 2017, Chapter 3 —
[hackinggrowth.com](https://hackinggrowth.com/); and from
Amplitude's *North Star Playbook*, updated periodically —
[amplitude.com/books/north-star](https://amplitude.com/books/north-star).
The input-metric / growth-loop decomposition derives from
Andrew Chen, *The Cold Start Problem*, Harper Business,
2021, Part IV: "The Ceiling" —
[andrewchen.com/the-cold-start-problem-book](https://andrewchen.com/the-cold-start-problem-book/)
— and the Reforge Growth Series essays at
[reforge.com/blog](https://www.reforge.com/blog). The
guardrail discipline derives from Ronny Kohavi, Diane
Tang & Ya Xu, *Trustworthy Online Controlled Experiments*,
Cambridge University Press, 2020, Chapter 21 —
[experimentguide.com](https://experimentguide.com/).
