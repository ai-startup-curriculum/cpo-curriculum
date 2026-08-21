# Lecture 4 — Discovery anti-patterns and how they fool founders

You will do everything in the first three lectures and still end up believing
you have fit when you don't, unless you can recognize the specific ways
smart, motivated teams fool themselves. This lecture is a field guide.

## Anti-pattern 1 — The friendly-network false positive

You launch. Your first 200 sign-ups are your LinkedIn network and their
friends. Retention week 1 is 70%. The Sean Ellis survey comes back at 55%.
You conclude fit. Two months later the network is exhausted, cold traffic
arrives, and the numbers halve.

The failure was measuring a *biased* audience. Your network signed up because
of you, used it once out of politeness, answered the survey because you
asked, and does not represent the market you have to sell into next.

**Countermeasure.** Report your PMF instruments **excluding the first N warm
users** — anyone who arrived via a founder's personal outreach, an
angel-investor introduction, or a launch-day social push. Track the cold-only
cohort separately. If cold retention flattens and cold "very disappointed"
climbs, you have a claim. Rahul Vohra's Superhuman writeup makes exactly this
segmentation move: filter to users who actually match the target
profile before computing the score
([Vohra, "How Superhuman Built an Engine to Find Product/Market Fit,"
*First Round Review*, 2018 — see the section on segmenting
respondents](https://review.firstround.com/how-superhuman-built-an-engine-to-find-product-market-fit/)).

## Anti-pattern 2 — Leading interview questions

You ask, "Wouldn't it be useful if you could scan receipts from your phone?"
Ten out of ten interviewees say yes. You write it up as a validated need.
Zero of them actually scan a receipt when you ship it.

The interviewee said yes because the question was designed to elicit yes, and
because agreeing was the socially cheapest move. Rob Fitzpatrick catalogs
this failure at length; the fix is his rule to *ask about specifics in the
past, not generics or opinions about the future*
([Fitzpatrick, *The Mom Test*, 2013, Chapter 1's three
rules](https://www.momtestbook.com/)).

**Countermeasure.** Record interviews (with consent) and, in review, mark
every question that presumes a positive answer or asks the interviewee to
predict their own future behavior. Refactor those questions into past-tense,
behavior-specific versions. Do this weekly, as a team; the drift back into
leading questions is continuous.

## Anti-pattern 3 — Demo-driven validation

You show a mockup. The prospect says "wow, I'd definitely use that."
You count it as validation. In production the same person never signs up.

Two mechanisms are at work. First, reacting to a polished mockup is
entertainment, not commitment. Second, the prospect is imagining a version of
themselves — organized, disciplined, ready to change workflow — that isn't
the person who shows up on Monday. Steve Blank's Customer Development is
explicit that *demo* is not *sale*; only paid, repeated, cold-recruited use
counts as validation ([Blank & Dorf, *The Startup Owner's Manual*, 2012,
Chapter on Customer Validation](https://www.strategyzer.com/library/the-startup-owners-manual)).

**Countermeasure.** Move from "would you use this?" to *pre-order, deposit,
or unmistakable behavior*. A signed pilot agreement, a paid deposit, or an
introduction to their procurement lead is signal. A "wow" is not.

## Anti-pattern 4 — Vanity retention

You report *DAU / MAU = 40%* and celebrate. But your DAU counts email opens,
your MAU counts anyone who logged in once in the trailing 30 days, and your
"active" definition changed twice this year to include lighter-touch events.
The ratio is meaningless.

Andrew Chen has written extensively about vanity metrics; the mechanism is
generic. If the definitions of the metrics can drift, they will drift toward
whatever makes the founder look best.
<!-- needs-research: attach a specific canonical source; likely Andrew Chen's
"Vanity Metrics vs. Actionable Metrics" (andrewchen.com) or Eric Ries's
treatment of vanity metrics in *The Lean Startup*, Chapter 7. -->

**Countermeasure.** Write down the definition of *active* before you measure
it, tie it to a behavior that plausibly indicates value delivery (not a
notification receipt or a passive event), and refuse to redefine it inside a
measurement window.

## Anti-pattern 5 — Launch metrics mistaken for fit

Product Hunt #1. TechCrunch article. 10,000 sign-ups in a week.
You conclude PMF. The week-4 retention curve says 3%.

Launches are top-of-funnel events, not fit measurements. They surface
curious users, not users the market pulls back. Andreessen's essay is often
cited as if a big launch *is* the signal of fit; read carefully, the essay
describes what fit *looks like from the inside over time*, not what a launch
week looks like ([Andreessen, "The Only Thing That Matters," pmarchive,
2007](https://web.archive.org/web/20140705013620/http://pmarchive.com/guide_to_startups_part4.html)).

**Countermeasure.** Bar yourself from concluding anything about fit from a
launch until you have 8–12 weeks of retention data on cold cohorts arriving
after the launch spike subsides.

## Anti-pattern 6 — Falling in love with the outlier

One customer loves the product, uses it three hours a day, tells you how it
changed their life. You build the roadmap for that customer, ignoring that
they're a data-point-of-one who works in a niche you can't scale into.

This is a special case of the segmentation error. The outlier is real, but
their existence is not evidence of a market — it's evidence that a market
*might* exist adjacent to them.

**Countermeasure.** Every time you're excited about a customer, immediately
try to find their five closest analogues. If you can't articulate the
segment tightly enough to name five candidates in an hour, they're not a
segment yet; they're a friend.

## Anti-pattern 7 — Roadmap by loudest voice

The last three prospect calls all asked for feature X, so feature X is next
on the roadmap. Never mind that all three were the same buyer profile in the
same vertical, or that feature X targets an opportunity the tree says has
one supporter and no evidence.

Marty Cagan's argument in *Inspired* is that the failure isn't listening to
customers; it's letting requests bypass the discovery process. Customer
requests are input to the opportunity tree, not verdicts on the roadmap
(*Source:* Cagan, *Inspired*, 2nd ed., Chapter 3, "Product Discovery," and
the chapters on how customer feedback feeds discovery).

**Countermeasure.** Route feature requests through the opportunity solution
tree. If the request maps to a live opportunity with existing evidence, it
strengthens that branch; if it opens a new opportunity, it starts as a
hypothesis, not a commitment.

## Anti-pattern 8 — "We're pre-launch, we can't do discovery"

You skip interviews on the grounds that you have nothing to show. Then you
launch and discover in the wild what you could have discovered in a room —
except now with sunk engineering cost and a public failure.

You can do discovery on a landing page, a Figma mockup, a Wizard-of-Oz
demo where you're manually doing what the software will eventually do, or
a concierge version where the whole service is you and a spreadsheet. The
Lean Startup case studies (IMVU, Food on the Table) are largely stories
about pre-launch or launch-in-days discovery via minimum viable products
(*Source:* Ries, *The Lean Startup*, Chapter 6, "Test," on the MVP as a
discovery instrument).

**Countermeasure.** If you have less than an MVP, you have more than enough
to discover with. Start now.

## Anti-pattern 9 — Declaring fit to raise the round

The market for capital rewards confident narratives. The market for products
rewards honest measurement. Confusing the two — announcing fit to move a
term sheet forward — traps you: the next round expects the growth curves the
narrative implied, and you burn the runway trying to manufacture them.

**Countermeasure.** Keep two documents. The *investor narrative* can be
directionally optimistic. The *internal PMF memo* — the one that goes to the
board, the team, and next quarter's plan — has to survive its own instruments.
If they say different things, act on the internal one.

## Takeaways

- The failure modes cluster around biased audiences, leading questions,
  reactions mistaken for behavior, and metrics whose definitions drift.
- Every countermeasure boils down to: report per segment, over time, with
  a written-down definition, on cold-cohort behavior — and treat requests
  as input to discovery, not decisions.
- The instruments in Lecture 3 are only as honest as the audience you
  measure them on and the definitions you refuse to fudge.

Discovery is uncomfortable because it produces evidence that founders
sometimes don't want to see. That discomfort is the point.
