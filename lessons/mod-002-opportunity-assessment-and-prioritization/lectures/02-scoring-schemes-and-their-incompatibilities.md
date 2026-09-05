# Lecture 2 — Scoring schemes: RICE, ICE, WSJF, Kano — and why they don't compose

## The setup

Once you have a shelf of bounded opportunities (Lecture 1), the temptation
is to pick a scoring formula off a blog, plug numbers in, and let the
spreadsheet declare the ranking. It seems rigorous, and the outputs sort
nicely. The problem is that the four most-cited schemes — **RICE**, **ICE**,
**WSJF**, and **Kano** — are answering different questions, using different
units, with different assumptions about what the numbers mean. Treating
them as interchangeable produces rankings you cannot defend.

This lecture does two things. First, it gives you each scheme in its
canonical form and its intended use. Second, it names the mathematical
incompatibilities that force you to choose one and stick with it — and to
know what you're giving up when you do.

## The core question a scheme has to answer

Prioritization is a comparison problem. To rank two opportunities you need
either (a) a common scalar you can compare their scores on, (b) a common
ordering rule that says which dominates the other, or (c) a rule for
splitting the list into buckets and ordering inside each bucket. The four
schemes cover all three modes, and mixing modes is exactly where teams
fool themselves.

## Scheme 1 — RICE (a common scalar via multiplication)

Intercom published RICE in 2016 as an in-house tool that leaked out and
became the industry default
([McBride, "RICE: Simple prioritization for product managers," Intercom
blog, 2016 —
intercom.com/blog/rice-simple-prioritization-for-product-managers](https://www.intercom.com/blog/rice-simple-prioritization-for-product-managers/)).

The formula is:

```text
RICE = (Reach × Impact × Confidence) / Effort
```

- **Reach.** Number of people/events affected in a fixed time window (e.g.,
  users per quarter). A count.
- **Impact.** How much the opportunity moves the outcome per reached user,
  usually on a small ordinal scale — Intercom's is `{3, 2, 1, 0.5, 0.25}`
  for `{massive, high, medium, low, minimal}`.
- **Confidence.** A percentage on your estimates as a whole — Intercom's
  suggested `{100%, 80%, 50%}` for `{high, medium, low}`.
- **Effort.** Person-months (or similar), estimated up-front.

The final number reads as *impact per unit of effort, discounted by your
confidence*. Larger is better, and you rank by descending score.

**What RICE is good at.** Feature-scale comparisons where reach is genuinely
countable (funnel steps, existing-user flows, well-instrumented surfaces).
The multiplication forces you to write down four things, which is more
discipline than most orgs have.

**What RICE hides.** Three things, and they matter.

1. **Impact is ordinal being multiplied like a cardinal.** A "3 = massive"
   is not literally twice as good as "1.5 = medium." Multiplying ordinals
   invents a metric that isn't there — statisticians call this a *scale
   type violation*
   ([Stevens, "On the Theory of Scales of Measurement," *Science*, June
   1946](https://web.archive.org/web/20240128034023/https://www.jstor.org/stable/1671815)).
   Two opportunities separated by 0.3 RICE points are not meaningfully
   different.
2. **Small-effort items always look huge.** The divide-by-effort structure
   inflates the score of anything cheap. A trivial copy-tweak with plausible
   Reach can outrank a strategic surface-level bet, and the spreadsheet
   won't warn you.
3. **Confidence is doing too much work.** The 100/80/50% multiplier is a
   single lever standing in for uncertainty in Reach *and* Impact *and*
   Effort. If your Effort estimate is wrong by 2× the whole score is wrong
   by 2×; a 20% confidence trim doesn't rescue that.

## Scheme 2 — ICE (RICE minus reach; faster, weaker)

ICE — **Impact × Confidence × Ease** — predates RICE in growth-marketing
circles. Sean Ellis and the GrowthHackers community used it to rank
experiment ideas, where speed of iteration mattered more than precision
([Ellis & Brown, *Hacking Growth*, Currency, 2017, Chapter 6, "Testing at
High Tempo," on scoring test ideas by ICE](https://www.hachettebookgroup.com/titles/sean-ellis/hacking-growth/9780451497215/);
[GrowthHackers, "How to Prioritize Your Growth Ideas: ICE Score,"
growthhackers.com](https://growthhackers.com/articles/growth-hacking-ice-score-to-prioritize-growth-ideas)).

```text
ICE = Impact × Confidence × Ease
```

Each component is scored 1–10 by the author, from gut.

**What ICE is good at.** Ranking growth experiments where you have too
many ideas and too little time to instrument reach, and where the cost of
running an experiment is roughly constant. It's a triage tool.

**What ICE hides.** All the RICE issues, plus one: **author bias is
un-audited.** Two authors will score the same idea very differently on a
1–10 scale with no anchors. Sean Ellis's team ran the scoring as a group,
with disagreement forcing a conversation — the *scoring session* was the
mechanism, not the score. Adopted without the session, ICE becomes a
number generator whose ranking is whichever PM ran the sheet.

## Scheme 3 — WSJF (a rate, not a score — for a flow system)

Weighted Shortest Job First comes from Don Reinertsen's product-development
flow work and is codified in the Scaled Agile Framework
([Reinertsen, *The Principles of Product Development Flow*, Celeritas
Publishing, 2009, Chapter 5, "Managing Queues," on Cost of Delay divided
by duration](https://celeritaspublishing.com/product/the-principles-of-product-development-flow/);
[SAFe, "Weighted Shortest Job First," scaledagileframework.com —
framework.scaledagile.com/wsjf](https://framework.scaledagile.com/wsjf/)).

```text
WSJF = Cost of Delay / Job Duration
```

**Cost of Delay** (CoD) is the money you lose per unit of time by *not*
doing this job now. SAFe decomposes CoD into three additive components on
a Fibonacci-anchored relative scale (1, 2, 3, 5, 8, 13, 20…):

- **User-business value** — how much users/customers want this.
- **Time criticality** — does the value decay if delayed? (deadlines, fixed
  events, competitive windows)
- **Risk reduction / opportunity enablement** — does doing this unlock or
  de-risk other jobs?

Duration is estimated the same way. The result is a rate — *dollars-of-delay
per week-of-work* — and you take jobs highest-rate-first from the queue.

**What WSJF is good at.** Queue systems with fixed engineering capacity
where jobs arrive over time and dependencies matter. It captures two things
RICE and ICE do not: **time-decay of value** (a January-launch is worth
less if it slips to March) and **enabling / unlocking** (doing this small
thing now cheapens the big thing next quarter). Reinertsen's argument is
that ignoring cost-of-delay is the single most expensive mistake in
product-development economics.

**What WSJF hides.** Two things.

1. **Cost of Delay is often unmeasurable.** SAFe finesses this by making
   CoD *relative* (Fibonacci 1–20) instead of dollar-denominated. That
   preserves the ranking property (largest CoD first) but sacrifices the
   *rate* interpretation — you cannot say "this job is worth $50k/week and
   that one is worth $25k/week" any more, only that this one is nominally
   ranked higher.
2. **Duration estimation gets a division-based penalty.** Same as RICE:
   a job you estimated at 1 week gets a 3× WSJF boost over one you
   estimated at 3 weeks, even if the estimates are noise. Reinertsen's
   own advice is to *batch small* on the input side (smaller jobs, more
   frequent), not to game duration on the scoring side.

## Scheme 4 — Kano (classification, not scoring)

Noriaki Kano's 1984 model, later published in English in *Attractive
Quality and Must-Be Quality*, does not produce a single number to sort by.
It classifies each candidate feature by how it maps satisfaction to
implementation
([Kano, Seraku, Takahashi & Tsuji, "Attractive Quality and Must-Be
Quality," *Journal of the Japanese Society for Quality Control*, Vol. 14,
No. 2, 1984 — English translation reprinted in *The Best on Quality*,
IAQ, 1996](https://asq.org/quality-resources/articles/attractive-quality-and-must-be-quality-noriaki-kano);
[Kano Model Consulting summary at asq.org — asq.org/quality-resources/kano-model](https://asq.org/quality-resources/kano-model)).

Categories:

- **Must-be (basic).** If missing, users are angry; if present, users don't
  notice. Login works; the app doesn't crash on start; passwords reset.
  Not shipping these is negative. Shipping them is table stakes.
- **Performance (one-dimensional).** More-is-better with a roughly linear
  satisfaction return. Faster page loads; more storage.
- **Attractive (excitement/delighter).** Absence is silently tolerated;
  presence causes disproportionate delight. Novel differentiators.
- **Indifferent.** Users don't care either way.
- **Reverse.** Adding this *lowers* satisfaction (over-featuring; forced
  workflow).

You classify with a paired-question survey — a *functional* form ("how
would you feel if this were present?") and a *dysfunctional* form ("how
would you feel if this were absent?") — and read the pair off a lookup
table.

**What Kano is good at.** Deciding whether an item is a *precondition* to
selling at all (Must-be), a *reason to prefer* you (Performance), or a
*reason to notice* you (Attractive). This maps to fund/de-fund decisions
better than any single number.

**What Kano cannot do.** Rank items within a category. Two Attractive
features cannot be ordered by their Kano classifications; you still need
a scheme like RICE or WSJF *inside* the category.

## The mathematical incompatibilities you can't argue away

Where teams get themselves in trouble is treating the four schemes as
different flavours of the same thing. They aren't.

- **RICE and ICE are cardinal-arithmetic schemes** over ordinal inputs.
  Their outputs are ranked, but the *distances* between ranks are noise.
  Do not report "RICE-32 is twice as important as RICE-16."
- **WSJF is a rate, not a score.** Two jobs with the same WSJF have the
  same value-per-week, not the same value. If your capacity constraint is
  people-months (not calendar weeks) WSJF may not be the right shape.
- **Kano is a classification, not a scale.** Comparing a "Must-be" to an
  "Attractive" via a single scalar collapses the very distinction that
  makes Kano useful.
- **You cannot mix schemes on the same ranked list.** A blended
  spreadsheet where some items are scored RICE and some WSJF and some
  Kano is not a ranking — it is four rankings pretending to be one, and
  the sort order is an artifact of whichever scheme happened to produce
  the biggest numbers.

The corollary: **choose one scheme per portfolio, per horizon**, and know
what you gave up. A common working shape (Lecture 3 will elaborate):

- **Base-rate optimization queue** (funnel improvements, retention lifts):
  RICE or WSJF, weekly ranking cadence.
- **Strategic-bet queue** (new surfaces, new segments, new tiers): Kano
  classification to sort into "must-do to keep selling / reason to prefer /
  new pull" buckets, then discovery-shaped judgment (Lecture 1's four
  sentences and Cagan's opportunity assessment) rather than a scheme.
- **Flow-limited engineering queue** across mixed items: WSJF, to keep
  time-decay and enablement in the picture.

## Anchors: make your scale readable, or don't use it

The single highest-leverage discipline on top of any scheme is **anchor
your ordinal scales to written examples**. Not "Impact 3 = massive," but
"Impact 3 = *comparable to the mobile-app launch in Q2, which drove +8pp
week-4 retention*." Anchors do two things: they let scoring sessions
converge across authors, and they force the scale to inherit your
historical realities instead of blogosphere defaults.

Rebuild the anchors quarterly. What was "massive" last year is table
stakes now; if you don't refresh, your ordinal drift silently deflates
everything.

## Confidence, and why "we're 30% sure" is often a lie

Every scheme has a confidence knob or an implicit assumption. Two common
failure modes:

- **False precision.** "70% confidence" reported without any process for
  arriving at it (calibration, base rates, reference class) is the author's
  gut with a decimal on it.
- **Confidence-washing.** Multiplying by a low confidence to "penalize"
  a risky opportunity is *not* the same as running a cheap experiment to
  raise the confidence. If a discovery week could take you from 30% to
  70% on the top-ranked opportunity, that discovery week is the
  highest-EV item on the roadmap.

Prefer explicit *this-is-a-hypothesis* labels on any opportunity where
confidence < 50%, plus a discovery task attached to it, over a confidence
multiplier that quietly kills the item without ever testing it.

## Takeaways

- The four canonical schemes answer different questions with different
  math; treating them as interchangeable produces indefensible rankings.
- Use RICE / ICE for scalar ranking inside a well-defined pool with
  countable reach; use WSJF when time-decay and enabling matter and
  you're capacity-limited; use Kano to *classify* items into must-do /
  differentiator / delighter buckets before you rank inside a bucket.
- Anchor your ordinal scales to written historical examples; refresh
  the anchors quarterly.
- Treat low confidence as a signal to *run discovery*, not to trim the
  score.

Lecture 3 uses these tools to draw a bigger distinction: not every
opportunity belongs in the same queue at the same cadence.
