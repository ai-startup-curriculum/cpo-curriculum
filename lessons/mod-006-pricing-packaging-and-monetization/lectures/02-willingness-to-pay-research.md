# Lecture 2 — Willingness-to-pay research at pre-seed → seed scale

## The setup

Lecture 1 argued that the CPO owns willingness-to-pay
evidence the way the CPO owns interview evidence: as a
discovery instrument that runs inside the weekly rhythm,
not as a one-off marketing exercise. This lecture is the
*how*.

The pricing research literature has three main
instruments — **Van Westendorp price sensitivity meter**,
**Gabor-Granger purchase-intent laddering**, and
**conjoint analysis** — plus dozens of variants. Each
was designed for consumer-goods research at N in the
hundreds to thousands. The pre-seed / seed CPO has, at
most, N in the tens: 5 discovery interviewees, 20 pilot
customers, 50 free-trial sign-ups. The core question of
this lecture is not "what instruments exist" — the
consultancies have thick catalogs — but "which
instruments produce a defensible read at small N, and
how do you interpret the results without inventing
precision that isn't there."

The through-line, drawn across Van Westendorp's original
1976 ESOMAR paper
([Van Westendorp, "NSS-Price Sensitivity Meter (PSM) —
A New Approach to Study Consumer Perception of Prices,"
1976](https://ana.esomar.org/documents/nss-price-sensitivity-meter-psm-a-new-approach-to-study-consumer-perception-of-prices)),
Gabor & Granger's 1966 *Economica* paper
([Gabor & Granger, "Price as an Indicator of Quality,"
1966](https://www.jstor.org/stable/2552031)), Ramanujam
& Tacke Chapter 5, and the ProfitWell / Paddle applied
writing:

**Small samples don't tell you the price. They tell you
the range, the shape of the sensitivity curve, and the
segment cuts to investigate. Treat WTP research as
directional at N < 50, hypothesis-generating at N < 200,
and price-defensible only at N ≥ 200 within a segment.**

## Instrument 1 — Van Westendorp price sensitivity meter

The Van Westendorp PSM asks four questions about a
described product or feature bundle:

1. At what price would you consider this product so
   **expensive** that you would not consider buying it?
   *(too expensive)*
2. At what price would you consider this product **so
   inexpensive** that you would question its quality?
   *(too cheap)*
3. At what price would you start to think this product
   is **expensive** — not out of the question, but you'd
   have to think about it? *(expensive)*
4. At what price would you consider this product to be
   a **bargain** — a great buy for the money? *(bargain)*

Plotted as four cumulative-distribution curves against
price on the x-axis, the intersections have specific
interpretations:

- **Point of Marginal Cheapness (PMC).** Intersection
  of "too cheap" and "bargain." Below this price,
  buyers doubt the quality more than they enjoy the
  discount.
- **Point of Marginal Expensiveness (PME).** Intersection
  of "expensive" and "too expensive." Above this price,
  the product becomes decidedly expensive.
- **Optimal Price Point (OPP).** Intersection of "too
  cheap" and "too expensive." The price at which the
  *fewest respondents reject the product* for being
  either too cheap or too expensive.
- **Indifference Price Point (IPP).** Intersection of
  "expensive" and "bargain." The price at which equal
  numbers see the product as an expensive buy vs. a
  bargain — often close to the current market price
  when respondents are aware of it.
- **Range of Acceptable Prices.** Between PMC and PME.
  The interval within which the largest share of
  respondents find the price plausible.

### How to run it at small N

The four questions are not the hard part. The hard parts
are:

- **Anchor the described product concretely.** The
  respondent needs a specific mental model of *what* is
  being priced. A one-line description ("a customer-
  support triage agent") produces answers based on the
  respondent's imagined product, not yours. Use a
  paragraph, a screenshot, or — best — a live demo
  followed by the four questions. The Ramanujam &
  Tacke Chapter 5 discipline: **describe the product
  in enough detail that two respondents given the same
  description would price the same thing.**
- **Ask the four questions in the four orders they
  should be asked.** The original Van Westendorp order
  is: *too expensive → too cheap → expensive → bargain*
  (or a rotation that keeps *too expensive* first).
  The bracketing is intentional; the anchors set the
  respondent's price range before you narrow to the
  softer judgments.
- **Ask in an interview, not a survey — at small N.**
  With N < 50 a self-serve survey conflates
  respondents who understood the concept with those
  who guessed at the meaning. In a discovery interview,
  the researcher can watch for confusion, restate the
  product, and probe follow-up ("why that number?"
  "compared to what?"). Move to survey format only
  when N ≥ 100 within the segment.
- **Cohort by segment.** Buyer segment, use-case,
  company size — pick the cut ahead of time from the
  mod-001 JTBD synthesis, and plan for enough
  respondents per segment to produce a plot (minimum
  ~15 per segment for the curves to be readable, ~30
  before you'd cite an OPP).

### The honest read at N < 50

At N < 50, the four curves are jagged and the
intersections wobble a lot. Rules of thumb from the
practitioner literature (Campbell / ProfitWell, plus
the psychometric caveats in the Van Westendorp
literature):

- **The Range of Acceptable Prices (PMC to PME) is the
  reliable output at small N.** It tells you the
  bounds. Prices outside it are almost certainly wrong;
  prices inside it are plausible.
- **The OPP is unstable at small N.** Do not quote it
  as a price recommendation with three significant
  figures. Quote a *range* around it, wider at smaller
  N. A rule of thumb from Campbell's talks: the OPP
  from N=20 is defensible to within ~40% of its own
  value; from N=100 to within ~15%; from N=500 to
  within ~5%.
  <!-- needs-research: quantify the OPP confidence interval as a function of N from primary methodological sources rather than as rule-of-thumb; original van Westendorp paper does not tabulate this. -->
- **The IPP is the anchor-price signal.** If your
  current price is far from the IPP, either your
  respondents are anchoring against a competitor
  (probe: which competitor?) or your product's
  perceived value is very different from what your
  price suggests.
- **Segment cuts matter more than aggregate curves.**
  If enterprise buyers' PMC is $30k and self-serve
  buyers' PME is $500, aggregating produces a nonsense
  curve. Segment first.

### Van Westendorp pitfalls

The instrument has known failure modes. The founding
CPO who reads only the *"here's how to run Van
Westendorp"* blog posts (there are hundreds) will
usually miss these:

- **No product = no meaningful answer.** If the
  respondent has not experienced the product, the
  responses are guesses. Van Westendorp on a landing-
  page description with no demo is entertainment.
- **Category familiarity effects.** Respondents new to
  a category (first-time buyers of "AI eval tooling")
  produce noisier, lower Van Westendorp curves than
  category-experienced buyers. Segment on category
  familiarity.
- **No willingness ≠ no purchase intent.** A
  respondent can rate a product "bargain" at $50 and
  still not buy it. Van Westendorp measures *price
  perception given interest*, not *intent conditional
  on price*. Pair with Gabor-Granger to close that
  gap.
- **Small changes in the product description swing
  the curves.** A demo that emphasizes the ROI shifts
  PME up; a demo that emphasizes limitations shifts
  it down. Keep the product description fixed across
  the study.

## Instrument 2 — Gabor-Granger purchase-intent laddering

Van Westendorp asks *what price feels right*. Gabor-
Granger asks *would you buy at this price*, and ladders
up or down until the respondent refuses.

The base method (from Gabor & Granger 1966):

- Present the product at a specific price. Ask: *"At
  price $X, would you purchase this product? (Yes /
  No / Maybe)"*
- If yes, raise the price to $X + Δ. Ask again.
- Repeat until refusal.
- (Symmetric ladder: if no, lower the price until
  acceptance.)

Across N respondents, plot the **share who would buy**
against the **price**. The resulting **purchase-intent
curve** slopes downward — the higher the price, the
smaller the share who'd buy — and (in most product
categories) has a knee where purchase-intent drops
sharply. That knee is a price recommendation.

### How to run it at small N

- **Randomize the starting price across respondents.**
  If everyone starts at $10 and ladders up, the
  results are biased by the starting anchor. Half your
  sample starts high and ladders down; half starts low
  and ladders up.
- **Use ~5 price points per respondent.** More than 5
  and respondents fatigue and default to "yes" or "no"
  regardless. Fewer than 5 and the curve is too coarse
  to see the knee.
- **Ask about a specific concrete product at a specific
  concrete moment.** *"Would you buy the Team plan
  today at $X per seat per month?"* — not *"in general,
  what would you pay for something like this?"*
- **Cohort by segment**, same discipline as Van
  Westendorp.

### What Gabor-Granger tells you that Van Westendorp
### does not

- **Revenue-optimal price** — multiply price × share-
  who'd-buy at each price point. The maximum of that
  product is the revenue-maximizing price. (Note: this
  is the *stated-intent* revenue max, not the
  *behavioral* revenue max — see the honest read
  below.)
- **The knee of the curve** — where purchase-intent
  falls off. Pricing above the knee costs a
  disproportionate share of revenue; pricing well
  below leaves money on the table.
- **A more defensible read at small N than Van
  Westendorp.** Each respondent produces a data
  point at multiple prices, which stabilizes the curve
  faster than the four-question format.

### Gabor-Granger pitfalls

- **Stated intent ≠ actual purchase.** Respondents
  reliably overstate willingness to buy. The purchase-
  intent curve is *shape-informative* (where the knee
  is) but *level-optimistic* (the absolute share is
  ~2–3× the real conversion rate, per practitioner
  benchmarks).
  <!-- needs-research: cite a specific benchmark for stated-intent inflation ratio; Sean Ellis and Campbell / ProfitWell both discuss it but a canonical citation is needed. -->
- **Anchoring bias.** The starting price influences
  the willingness curve. Randomization mitigates it;
  it doesn't eliminate it.
- **Category effects.** In categories where price is a
  quality signal (luxury, professional services), the
  curve is non-monotonic — willingness can *rise* with
  price up to a point. Gabor-Granger will show this
  correctly if you probe enough price points.

## Instrument 3 — Conjoint analysis at small N

Conjoint asks respondents to choose between full
product packages (bundle A vs. bundle B), varies the
features and prices across the choices, and infers each
feature's contribution to willingness-to-pay from the
choice pattern.

Full-strength conjoint (choice-based conjoint, adaptive
choice-based conjoint, MaxDiff) requires N in the
hundreds to be statistically defensible and typically
uses purpose-built tooling (Sawtooth Software,
Qualtrics ChoiceModel, Conjointly). It is not, in its
full form, a founding-CPO instrument.

**The founding-CPO variant** — sometimes called
*micro-conjoint* or *pairwise trade-off* — is a
qualitative research move rather than a statistical
one:

- Design **3–5 feature bundles** at different price
  points. Each bundle is a plausible good / better /
  best variant of the packaging you're considering.
- In a discovery interview, present two bundles side
  by side. Ask *"which of these would you buy, at these
  prices?"*
- Rotate through all pairwise comparisons across
  respondents.
- Do *not* fit a statistical model. Read the results
  qualitatively: which features consistently push
  respondents toward the higher-priced bundle, which
  features respondents don't seem to weigh, which
  price differences produce a coin-flip response.

The micro-conjoint output is **feature-value
directional evidence** — "the API access feature is a
premium-tier justifier for two-thirds of enterprise
respondents; the extra reporting is not" — not a
willingness-to-pay dollar figure. It feeds the
packaging design in Lecture 3.

Full statistical conjoint is worth revisiting when the
company reaches Series-B scale and can staff dedicated
pricing research. Consumed reference:
Sawtooth Software's *Getting Started with Conjoint
Analysis*
([sawtoothsoftware.com](https://sawtoothsoftware.com/conjoint-analysis))
for the depth beyond this module.

## The three instruments compared

| Instrument | What it tells you | Minimum N for a read | Best use |
|---|---|---|---|
| Van Westendorp PSM | Range of acceptable prices; approximate optimal price | 15 per segment (directional), 100+ per segment (defensible) | Setting bounds on a new-product price |
| Gabor-Granger | Purchase-intent curve; revenue-maximizing price under stated intent | 20 per segment (directional), 100+ per segment (defensible) | Choosing among candidate prices within the bounds |
| Micro-conjoint (pairwise) | Which features justify higher tiers; which price differences produce indifference | 10 per segment (qualitative) | Designing the good / better / best packaging structure |

The natural workflow at pre-seed / seed:

1. **Van Westendorp** in discovery interviews to set
   the bounds. *"Prices from $20 to $200 are inside
   the range respondents find plausible."*
2. **Gabor-Granger** on the resulting range to find
   the knee. *"The knee is around $75; revenue-optimal
   stated-intent price is around $60."*
3. **Micro-conjoint** to test which feature groupings
   should live in which tier. *"Enterprise SSO and
   audit log should be in the top tier together; API
   access can float."*
4. **Cohort the read by segment**, refresh quarterly
   or when the product changes materially.

## The Reference Product method

A supporting move that makes all three instruments more
reliable, from Ramanujam & Tacke Chapter 5: for every
WTP study, **name the reference product** the
respondent is anchoring against.

The prompt: *"If this product didn't exist, what would
you use instead? A competitor? A homegrown solution? A
spreadsheet? Doing nothing?"* Follow up: *"What do you
pay for that today?"*

The reference product tells you:

- The **anchor price** the respondent is comparing to.
  A Van Westendorp curve with a $500 IPP against a
  $0 (doing nothing) reference means the respondent
  doesn't see the alternative as free — they see it
  as costing $500 in wasted time. That's a very
  different WTP shape than the same $500 IPP against
  a $500 competitor.
- The **competitive alternative** the packaging must
  differentiate against. A Poyar / OpenView point
  worth internalizing: your competition is not always
  the other vendor in the same category; often it is
  the manual workflow the customer already runs.
- The **switching cost** the price must overcome. If
  the reference product is a $0 spreadsheet that took
  the customer three months to build, the price of
  your product is competing with the *sunk-cost
  attachment*, not the sticker.

## What the CPO does personally

- **Runs the first 20 WTP conversations.** Delegating
  the initial WTP interviews yields a set of numbers
  the CPO can't defend when the founder-CEO or the
  head of sales pushes back. First-hand exposure to
  the price-anxiety patterns is not compressible.
- **Chooses the instrument for the question.** Van
  Westendorp for bounds, Gabor-Granger for point
  price, micro-conjoint for packaging structure. A
  single instrument for every question is a red flag.
- **Cohorts by segment.** Small-N WTP that is not
  segmented is *not directional*; it's a weighted
  average of incompatible segments, and it is
  systematically wrong.
- **Reads the reference product.** What are
  respondents anchoring against? The reference product
  answer is often the most important output of the
  study.
- **Publishes the honest read.** Write up the WTP
  study with its N, its segment cuts, its confidence
  bounds, and its known biases. The write-up goes to
  the founder-CEO, marketing, and finance; it is the
  artifact that establishes CPO ownership of pricing.

## What the CPO consumes from marketing and finance

- **Category positioning research.** Marketing usually
  has the analyst reports, the third-party benchmarks,
  and the competitor pricing pages. The CPO reads
  those to set the reference product; marketing
  curates them.
- **Unit-economics constraints.** Finance has (or
  should have) the gross-margin target, the CAC-
  payback target, and the LTV expectation. The CPO
  reads these as bounds the pricing recommendation
  must respect — see Lecture 5, and defer to
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum)
  for the depth.
- **Sales-cycle qualitative signal.** Sales, in
  face-to-face pricing conversations with prospects,
  produces the highest-fidelity willingness-to-pay
  signal in the company. The CPO listens to sales
  calls (5–10 per quarter) with pricing in mind;
  sales does not own the WTP program, but the CPO
  cannot ignore what sales hears.

## Boundaries this lecture keeps

- **Full statistical conjoint** — adaptive choice-
  based conjoint, MaxDiff, Hierarchical Bayes
  estimation at depth — is not a founding-CPO
  technique at pre-seed / seed. It is Series-B+ work
  usually staffed out to a pricing consultancy or an
  in-house researcher; the depth reference is
  [sawtoothsoftware.com](https://sawtoothsoftware.com/conjoint-analysis).
- **Behavioral pricing experiments** — actually
  charging different prices in-market and observing
  conversion — are Lecture 5's job, not this
  lecture's. WTP research is the *stated-intent*
  input; the *revealed-preference* read comes from
  the experiment program.
- **Price monitoring at operational depth** — cohort
  ARPU tracking, expansion/contraction MRR
  attribution, NRR by cohort — is
  [mod-005](../../mod-005-metrics-experimentation-and-ai-evals/README.md)'s
  post-PMF analytics discipline applied to revenue
  metrics. This lecture uses WTP research to set the
  price; mod-005's analytics regime tracks whether
  the price is holding.
- **The pricing conversation with a specific
  prospect** in a sales cycle is sales' job, informed
  by the packaging and the discounting bounds the
  CPO / finance set together. Not this module's
  scope.

## Takeaways

- **Small samples don't tell you the price; they tell
  you the range and the shape.** Treat WTP as
  directional at N < 50, hypothesis-generating at
  N < 200, price-defensible at N ≥ 200 per segment.
- **Van Westendorp PSM** — four questions (too
  expensive, too cheap, expensive, bargain) — gives
  you the Range of Acceptable Prices reliably at
  small N; the OPP is unstable and should be quoted
  as a range.
- **Gabor-Granger** laddering gives you the
  purchase-intent curve and the revenue-maximizing
  stated-intent price. Randomize the starting price;
  discount the absolute intent level (~2–3× real
  conversion).
- **Micro-conjoint** (pairwise bundle comparison) is
  the qualitative variant that fits founding-CPO
  scope; use it to inform packaging structure, not
  to produce dollar figures.
- **The natural workflow**: Van Westendorp for
  bounds → Gabor-Granger for point → micro-conjoint
  for packaging. Cohort by segment; refresh
  quarterly.
- **The Reference Product** is often the most
  important output — what respondents are anchoring
  against determines what the packaging must
  differentiate from.

Lecture 3 turns to the **packaging structure** — good
/ better / best, seat vs. usage vs. hybrid meter — the
WTP research from this lecture feeds.
