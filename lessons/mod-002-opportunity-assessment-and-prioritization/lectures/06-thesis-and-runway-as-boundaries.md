# Lecture 6 — Thesis and runway as boundary constraints

## The setup

Every technique in Lectures 1–5 is downstream of two inputs that the CPO
does not author alone:

- **Above the CPO** — the *company thesis*: the founders' answer to
  *what business are we in, who is the customer, what is our theory of
  winning?* The CPO consumes this; the founder-CEO owns authoring it.
- **Below the CPO** — the *runway* the company has to prioritize
  *within*: how many months of engineering, design, and go-to-market
  capacity the burn model actually funds. The CFO / founder-CEO owns
  authoring the burn model; the CPO consumes it.

Prioritization done without both is theater. A perfectly RICE-ranked
queue that ignores the thesis will optimize the wrong outcome; a
perfectly thesis-aligned queue that ignores runway will run out of money
mid-bet. This lecture is about the two consumption interfaces.

## The thesis: what the CPO is prioritizing *for*

A company thesis worth prioritizing against passes Richard Rumelt's
*kernel of good strategy* test: a **diagnosis** of the situation, a
**guiding policy** that responds to the diagnosis, and a set of
**coherent actions** that carry out the policy
([Rumelt, *Good Strategy Bad Strategy*, Crown Business, 2011, Chapter
5, "The Kernel of Good Strategy"](https://www.crownpublishing.com/archives/feature/good-strategy-bad-strategy-richard-rumelt)).
Rumelt's converse — *bad strategy*, the kind that names ambitions
without diagnosis, wraps them in inspirational language, and pretends
the wrapper is the plan — is what you'll usually get when you ask a
first-time founder-CEO for the thesis. That is not fatal; the CPO's
job is to consume what's there and to force the missing parts to
surface through prioritization pressure, not to write the thesis
unilaterally.

### What "consume the thesis" means in practice

Three concrete uses of a thesis at prioritization time:

1. **Tie-breaker.** Two opportunities score identically on RICE / WSJF /
   Kano. The one that better serves the thesis wins. If neither obviously
   serves the thesis, the thesis is not clear enough to prioritize
   against — flag it upward.
2. **Segment filter.** If the thesis names a target segment ("mid-market
   B2B ops teams on Salesforce"), any candidate whose target user isn't
   in that segment starts with a strike. Segment-crossing bets are
   allowed; they just have to defend the boundary crossing explicitly,
   not by omission.
3. **Portfolio allocation.** Lecture 4's cross-surface allocation is
   downstream of the thesis. A thesis of "the platform is the strategic
   surface; the consumer app is the acquisition surface" allocates
   engineering differently than "the consumer app is the product; the
   platform is a distribution channel."

### What "consume" does *not* mean

- **It doesn't mean rubber-stamping.** If the thesis and the discovery
  evidence disagree — you keep hearing a different segment's problem in
  interviews, the base-rate metrics keep telling a different story —
  the CPO's job is to *feed that back* to the founder-CEO with the
  evidence attached. This is one of the primary CPO-CEO conversations
  and is elaborated in mod-007 (Working with Founders).
- **It doesn't mean waiting for perfect thesis.** Most founding-stage
  theses are underspecified. Prioritization can and should run with the
  best available version, marking the gaps as *thesis gaps* that need
  resolving before the next quarterly commit.

### Where thesis authoring lives

The full craft of authoring a company thesis — Rumelt's kernel, the
mission / vision / values scaffolding, the theory of winning, the
board-facing narrative — is level-20 work owned by
[founder-ceo-curriculum](https://github.com/ai-startup-curriculum/founder-ceo-curriculum).
Read that curriculum's strategy modules to know what the input to *your*
prioritization looks like when it's authored well; but do not try to
substitute for it. The CPO who writes the thesis alone has skipped the
CEO-CPO conversation that makes the thesis load-bearing.

## The runway: what the CPO is prioritizing *within*

The runway constraint is deceptively simple: **cash on hand ÷ monthly
burn = months of runway**. What matters for prioritization is not the
number but its implications for the number of strategic bets you can
plausibly fund.

### The runway-to-bets translation

A rough working model for a pre-Series-B startup:

- A strategic bet (Lecture 3) is a 1–3-quarter effort with an
  associated fund-and-kill checkpoint.
- Each bet consumes some fraction of engineering capacity for its
  duration — often 20–50% depending on stage and how bounded the bet
  is.
- Any bet you fund needs enough runway *after* its expected finish
  to metabolize the result and, if the bet worked, to raise the next
  round on the strength of it.

Fred Wilson has argued repeatedly for keeping ≥18–24 months of runway
after any funding event, precisely so the burn timeline is compatible
with the bet timeline
([Wilson, "How Much Money to Raise," *AVC*, July 2011 —
avc.com/2011/07/how-much-money-to-raise](https://avc.com/2011/07/how-much-money-to-raise/);
[Wilson, "Runway," *AVC*, October 2011 —
avc.com/2011/10/runway](https://avc.com/2011/10/runway/)).
<!-- needs-research: verify Wilson's specific 18–24 month range in the
current *AVC* archive; if the exact URLs shift, replace with the
Bessemer or a16z canonical "how much runway" post or the Silicon Valley
Bank State-of-the-Market letters that publish current benchmarks. -->

The implication for the CPO's prioritization:

- **18–24 months of runway** — you can run 2–3 concurrent strategic
  bets and a re-bet cycle if one misses. This is the range most of the
  frameworks in this module implicitly assume.
- **9–15 months of runway** — you can run *one* strategic bet at a time
  and it has to work; the base-rate queue also has to defend its share
  of engineering capacity against fundraising-supporting quick wins.
  Ranking discipline gets tighter and reversibility gets weighted more
  heavily.
- **< 9 months of runway** — you are in survival mode. Strategic bets
  are dangerous; the prioritization is what will *close the round* or
  *reach cash-flow break-even*, and the CPO's queue reads like a GTM
  and monetization queue, not a discovery queue. The mechanisms in
  mod-006 (Pricing, Packaging, and Monetization) become the most
  important thing on the desk.

### Two runway questions the CPO should never answer alone

The CPO consumes the runway; the CPO does not model the burn.

- **"Should we raise now?"** — the founder-CEO's call, informed by the
  CFO / advisors. The CPO's input is *what the roadmap needs to prove
  before a round is raiseable*, not the raise decision.
- **"What's the pricing that closes the funding gap?"** — this is a
  pricing question (mod-006) informed by runway; the CPO owns the
  pricing craft, the founder-CEO owns the runway framing.

The full craft of burn modeling, runway extension mechanics, bridge
financing, and cash-flow break-even planning is level-40 work owned by
[startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum).
The CPO reads enough of that curriculum to consume the outputs; the
authoring is not this module's job.

## The two boundaries, on one page

A useful working artifact for the CPO is a **one-page prioritization
context** that the roadmap and the ranking spreadsheet both sit on top
of. It has three sections:

- **Thesis extract** (top). The two or three sentences from the
  founder-CEO's most recent thesis document that the CPO is
  prioritizing against, verbatim. If those sentences don't yet exist,
  the section reads *"THESIS GAP — pending founder-CEO clarification"*
  and the CPO is on the hook to force resolution before the next
  quarterly commit.
- **Runway line** (middle). The current runway in months, the burn
  rate, the CFO / founder-CEO's dated authorship, and the resulting
  "bets we can fund concurrently" number.
- **Prioritization implication** (bottom). Two or three sentences the
  CPO writes, translating the thesis and the runway into the current
  allocation and the current strategic-bet count. This is what the
  weekly and quarterly rankings sit on.

Refresh it monthly. Republish it any time the thesis or the runway
number moves materially.

## When the thesis and the runway disagree

The unpleasant case: the thesis says *"we are the platform for X"* — a
multi-year bet — and the runway says *"you have 8 months."* The CPO
cannot fix this by prioritizing harder. Two moves:

- **Name the mismatch upward.** *"The thesis assumes a horizon our
  current runway does not fund. Options are (a) raise now, (b) shrink
  the thesis to fit the runway, or (c) accept that we cannot execute
  the thesis and update it."* This is the CPO's founder-CEO
  conversation. Do not silently discount the thesis and prioritize as
  if it had already been shrunk; the founder-CEO needs to make the
  call.
- **Publish the ask.** The one-page prioritization context above should
  flag the mismatch in writing. Do not hide it from the board or the
  team; the mismatch is the operating reality, not a private CPO
  discomfort.

## Where the CPO does own the thesis input

The CPO is not the author of the thesis, but they are its most
important input on two dimensions:

- **Evidence.** What the discovery loop (mod-001) actually surfaced
  about the segment, the problem, and the fit signals. The thesis has
  to survive the evidence or update to it.
- **Feasibility.** What the roadmap can plausibly ship in the horizon
  the thesis assumes. A thesis that would require doubling engineering
  capacity is either a hiring plan or a fantasy; the CPO's role is to
  say which.

Feed both back in monthly. The CEO's thesis and the CPO's evidence /
feasibility inputs are meant to co-evolve; the failure mode is either
one going quiet.

## Takeaways

- The CPO's prioritization has two boundaries the CPO doesn't author:
  the thesis above (owned at level 20 by
  [founder-ceo-curriculum](https://github.com/ai-startup-curriculum/founder-ceo-curriculum))
  and the runway below (owned at level 40 by
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum)).
- Use the thesis as tie-breaker, segment filter, and portfolio
  allocation basis. Use the runway to translate cash-on-hand into a
  concrete count of concurrent strategic bets.
- Publish a one-page prioritization context that names the thesis
  extract, the runway line, and the resulting allocation and bet count.
  Refresh monthly.
- When the thesis and runway disagree, escalate; do not silently
  discount the thesis to fit the runway.

The module's exercises use the material of Lectures 1–5 against real
opportunities; Lecture 6 is the frame that makes those exercises land
inside a real company rather than in the abstract.
