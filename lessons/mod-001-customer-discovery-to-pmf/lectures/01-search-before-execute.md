# Lecture 1 — Search before execute: Customer Development in one sitting

## The setup

Most product teams behave, from day one, as if they already know what to build.
They stand up a roadmap, staff feature teams, and start executing. If the
underlying assumption — that the *thing* they're building is something a
customer will pay for and use — is wrong, no amount of executional excellence
rescues them. Steve Blank's contribution, formalized in *The Four Steps to the
Epiphany* (2005) and elaborated in *The Startup Owner's Manual* (2012, with
Bob Dorf), was to name this as a category error: a startup is not a small
version of a big company. Big companies *execute* a known business model;
startups *search* for one, and the two activities need different processes,
different metrics, and different leadership behavior.

The consequence for a founding CPO is direct: your job in the pre-fit phase is
not to run a delivery org. It's to run a search — a portfolio of falsifiable
bets — with the same rigor engineering brings to shipping.

## Customer Development in a paragraph

Blank frames the search as four steps, run mostly in sequence but with liberal
loops back to earlier stages when evidence demands it:

1. **Customer Discovery** — turn the founders' vision into a set of
   hypotheses about who the customer is, what problem they have, and what
   solution they'll pay for, then get out of the building to test them
   against real people.
2. **Customer Validation** — prove that a repeatable, scalable sales/growth
   process exists (people you didn't already know will buy at a price that
   works).
3. **Customer Creation** — spend on demand generation only after validation.
4. **Company Building** — transition from search to execute; hire functional
   leaders, build the machine.

(*Source:* Blank & Dorf, *The Startup Owner's Manual*, Chapter 1 — the
overview of the Customer Development process.)

The first two steps are where a founding CPO earns their keep. Discovery
answers *are we solving a real problem for an identifiable segment?* Validation
answers *can we sell the solution repeatably?* Skipping either — or, more
commonly, declaring victory on either based on a handful of friendly signals —
is the failure mode this module is written against.

## What "hypothesis" actually means here

A discovery hypothesis is a statement precise enough that a single interview or
experiment can move your belief in it. Compare:

- **Bad:** "SMB owners struggle with bookkeeping."
- **Better:** "Independent tradespeople with 1–10 employees currently
  reconcile receipts weekly using a paper folder and a spreadsheet, and lose
  1–2 hours a week to it."
- **Testable:** "…and would pay $30/month for a phone app that captures the
  receipt at point of purchase and posts the entries automatically."

The "better" version specifies segment, behavior, and frequency; the
"testable" version adds a purchase premise. In an interview, you can ask a
tradesperson to walk you through last week's reconciliation and get a
falsifying answer in ten minutes. You cannot get a falsifying answer to the
"bad" version — it's a mood, not a claim.

Eric Ries's *The Lean Startup* (2011) calls the pair of assumptions you have
to test first the **value hypothesis** ("does this deliver value the customer
notices?") and the **growth hypothesis** ("does use of the product cause more
use of the product, through referral, retention, or paid acquisition
economics?"). Both must be true for the business to work; discovery targets
the value hypothesis first because a growth engine wrapped around no value
is a leaky bucket at best and a fraud detection problem at worst
(*Source:* Ries, *The Lean Startup*, Chapter 5, "Leap").

## Why not just build and ship?

Two reasons, one about signal and one about cost:

**Signal.** Once you've shipped, positive metrics come from a mix of true
value, novelty, your existing network trying it out of politeness, and the
selection bias that says the first users of anything are the most sympathetic
users. You cannot easily untangle these post-hoc. In discovery you can attack
each source of noise directly: novelty by talking to the same person twice
over weeks; politeness by using Fitzpatrick's *Mom Test* moves (about which,
Lecture 2); network by explicitly recruiting strangers.

**Cost.** Engineering time compounds. A wrong architecture written to a wrong
spec accretes wrong tests, wrong docs, and a wrong on-call rotation.
Discovery is cheap — the marginal cost of one more interview is under an hour;
the marginal cost of one more sprint building the wrong thing is a quarter of
runway.

Marty Cagan puts the same argument in product-org terms in *Inspired*: the
two inconvenient truths about product are that *at least half of your ideas
are just not going to work* and *even the ideas that will work require several
iterations to get to the point where they deliver the expected business
value* (*Source:* Cagan, *Inspired*, 2nd ed., Chapter 3, "Product Discovery").
The point of discovery is to spend those iterations on paper, in
conversations, or on cheap prototypes, not in production code.

## What discovery is *not*

- **It is not focus groups.** A room of eight strangers reacting to a mock
  produces group dynamics, not evidence. Talk to people one at a time.
- **It is not "asking users what they want."** Users are unreliable narrators
  of their own future behavior; they are excellent narrators of their past.
  The Mom Test is built on this asymmetry (Lecture 2).
- **It is not a survey.** Surveys are good for turning a specific,
  well-formed claim into a number; they are bad at generating claims in the
  first place. Discovery generates claims. Save the survey for measuring PMF
  (Lecture 3).
- **It is not "we launched a beta, so we're doing discovery."** A beta is a
  delivery instrument. Discovery interviews continue during beta and after
  launch.

## The founding CPO's daily behavior in the search phase

If a week goes by and you have not talked to at least three prospective
customers, you are not doing this job — you are doing the job you had before,
running the delivery org that doesn't exist yet. Teresa Torres's operational
prescription in *Continuous Discovery Habits* is at least **one touchpoint per
week with a customer for every product team, sustained** — not a burst
followed by silence (*Source:* Torres, *Continuous Discovery Habits*, 2021,
Chapter 1's definition of continuous discovery). Adopt that as your baseline
even if your "product team" is you and one engineer.

## Takeaways

- A pre-fit startup is *searching* for a business model, not executing one;
  organize your work accordingly.
- Every claim you're operating on — about the customer, the problem, the
  solution, the price, the channel — should be written down as a hypothesis
  precise enough to fail.
- Discovery is a weekly cadence, not a phase you finish.
- If you are shipping and not also interviewing, you are collecting the wrong
  evidence.

Lecture 2 gets specific about *how* to interview so the evidence you collect
is worth anything.
