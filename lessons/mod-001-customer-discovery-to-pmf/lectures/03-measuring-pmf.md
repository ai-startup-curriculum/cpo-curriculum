# Lecture 3 — Measuring product/market fit

## "You can always feel it" — and why that isn't good enough

Marc Andreessen's often-quoted 2007 essay "The Only Thing That Matters"
defines product/market fit as *being in a good market with a product that can
satisfy that market* and argues that when you have it, *you can always feel
it*: usage grows faster than you can add servers, money piles up in the
checking account, you can't hire fast enough
([Andreessen, "The Only Thing That Matters," pmarchive, June 2007 — archived
at
web.archive.org](https://web.archive.org/web/20140705013620/http://pmarchive.com/guide_to_startups_part4.html)).

The passage is famous because it's true, and dangerous because it lets
founders declare fit based on a *feeling* long before the market has actually
said yes. This lecture gives you three instruments — a survey, a retention
curve, and a pull test — that turn the feeling into a claim you can defend or
falsify.

## Instrument 1 — The Sean Ellis 40% survey

Sean Ellis, an early growth lead at Dropbox, LogMeIn, and others, published
a simple survey question and a threshold that became the most-cited
quantitative PMF signal in the field:

> *How would you feel if you could no longer use [product]?*
> — Very disappointed / Somewhat disappointed / Not disappointed / N/A —
> I no longer use it.

Ellis's empirical claim, drawn from running the survey across many startups,
is that companies where **≥40% of active users answer "very disappointed"**
tend to have found the pull that lets growth investment work; below that
threshold, growth spend usually fizzles
([Ellis, "The Startup Pyramid," startup-marketing.com, 2009 — archived at
web.archive.org](https://web.archive.org/web/20180302113143/http://www.startup-marketing.com/the-startup-pyramid/)).

Rahul Vohra's account of using the survey at Superhuman turned it into an
operational tool — segment "very disappointed" responders, ask *what type of
person would most benefit?*, *what is the main benefit?*, and *what
improvements would you make?* — and iterate the product until the "very
disappointed" percentage in the target segment climbs. Superhuman started at
22% and iterated to 58% over quarters
([Vohra, "How Superhuman Built an Engine to Find Product/Market Fit,"
*First Round Review*,
2018](https://review.firstround.com/how-superhuman-built-an-engine-to-find-product-market-fit/)).

**Operating rules**:

- Only survey *active* users — Ellis's original guidance is people who've
  used the product recently (within roughly the last two weeks) and used it
  more than once, so you're measuring the pulled, not the curious
  ([Ellis, "The Startup Pyramid," 2009, section defining who to
  survey](https://web.archive.org/web/20180302113143/http://www.startup-marketing.com/the-startup-pyramid/)).
- Report the score *per segment*. A blended 40% that comes from 70% in one
  vertical and 10% in another is not fit — it's fit in one vertical you
  should be doubling down on.
- Do not gimmick the wording. Substituting "unhappy" for "disappointed" or
  a 5-point scale for the 3-point scale breaks comparability with the
  literature and, more importantly, with your own past runs of the survey.

The 40% threshold is a heuristic, not a law of physics — Ellis is explicit
that it's a signal that pull is there, not a certificate that growth is
guaranteed ([Ellis, "The Startup Pyramid," 2009 — read the "How to Use the
Data" section for the caveats](https://web.archive.org/web/20180302113143/http://www.startup-marketing.com/the-startup-pyramid/)).

## Instrument 2 — Retention curves

If your product has fit, users who come in a given week keep using it. If it
doesn't, retention decays to a floor of zero (or near-zero) and no volume
of top-of-funnel traffic saves you. The curve, plotted as *percentage of a
cohort still active in week N*, is the single most honest picture of whether
you have a product.

A useful shape to know:

- **Smiling curve.** The bottom quartile of the cohort churns, then the
  remaining users use the product *more* over time as they discover value
  and expand usage. This is the shape you want.
- **Flattening curve.** The cohort decays but the decay flattens to a
  non-zero asymptote — some subset of the cohort has genuinely made the
  product part of their life. The height of the asymptote is a defensible
  proxy for the size of the "very disappointed" pool.
- **Straight-to-zero curve.** No asymptote. Every cohort eventually leaves.
  You do not have fit, regardless of what the top-line numbers say.

Retention analysis is a Y Combinator and Andreessen Horowitz staple; the
"retention flattens" formulation is common in operator writing but is not tied
to a single canonical citation.
<!-- needs-research: attach a specific canonical source for the "retention
must flatten" formulation (candidates: Jonathan Hsu at Social Capital, Reid
Hoffman's "Blitzscaling" course notes, an a16z Growth blog post) once
verified. -->

**Operating rules**:

- Pick a **retention interval** that matches your product's natural use
  cadence — daily for consumer social, weekly for tools, monthly for
  infrequent-use products. A weekly cadence forced onto a monthly product
  will show fake churn.
- Plot **N ≥ 12** periods before drawing conclusions. Early cohorts are
  small and noisy; the shape reveals itself over time.
- Prefer **behavioral retention** (used the product) over
  **subscription retention** (still on the payment file) in the fit phase.
  A subscriber who hasn't logged in in eight weeks is on borrowed time.

## Instrument 3 — Organic pull

The third instrument is the qualitative one Andreessen described: things
happen that shouldn't happen if you didn't have fit. Concrete versions to
watch for:

- **Inbound you didn't ask for.** Journalists ask about you. Investors reach
  in. Prospects sign up with company email addresses from companies you never
  contacted. Existing users spontaneously write case studies or scripts around
  the product.
- **Word-of-mouth in the survey open-ends.** In the Sean Ellis survey, ask
  *how did you first hear about us?* If a growing share of the "very
  disappointed" cohort says "a friend/colleague," referral is doing work.
- **Willingness to work around limitations.** Users file bug reports and
  wait patiently instead of leaving. They write themselves scripts to fill
  gaps in the product. They ask when you're going to launch the enterprise
  plan.

None of these on its own is proof. Together, and in the presence of a
flattening retention curve and a rising "very disappointed" percentage, they
are as close to evidence of fit as you're going to get.

## Triangulate; never rely on one signal

Any single instrument is gameable or misleading:

- The Sean Ellis survey can be inflated by surveying the wrong (too warm)
  audience or by a passionate niche that will never scale.
- Retention curves can flatten for tiny cohorts in ways that don't survive
  scaling.
- Organic pull can be manufactured by a well-timed launch or a friendly press
  push and evaporate a month later.

Report all three, per segment, over time. If two are green and one is amber,
you have a claim to defend. If only one is green, you have a lead to chase,
not a finding.

## "Retention is the new revenue" — a caution

Post-2010 growth writing sometimes equates retention with fit and revenue as
downstream. That's a useful heuristic for consumer products with well-defined
active-use signals; it's a trap for B2B products where the buyer, the user,
and the payer are different people. A B2B product can have fine
end-user retention *and* churn logo after logo because the buyer never got
budget-defensible value. For B2B: measure end-user retention *and*
seat-expansion within account *and* net revenue retention across renewal
cycles, and only call it fit when all three agree.

## Takeaways

- Use the Sean-Ellis 40% survey with discipline: right audience, right
  wording, segmented reporting.
- Retention curves that flatten above zero are the honest picture of fit;
  curves that don't flatten are the honest picture of no-fit.
- Organic pull is the third leg — it's qualitative, it's real, and it can't
  substitute for the other two.
- Report per segment, over time; never declare fit from a single blended
  number or a single instrument.

Lecture 4 catalogs the ways teams fool themselves anyway.
