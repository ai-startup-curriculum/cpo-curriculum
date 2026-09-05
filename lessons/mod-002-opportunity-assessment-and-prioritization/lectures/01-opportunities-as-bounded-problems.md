# Lecture 1 — Opportunities as bounded problems, not feature lists

## The setup

Ask a founding CPO for their roadmap and the first draft you get back will
almost always be a list of features: *voice input, workflow templates, admin
audit log, Slack integration.* Each line reads like an intent to ship
something. None of them reads like a claim about a customer, a problem, or
what would count as evidence that shipping helped. That gap is the failure
this lecture is written against. Prioritization done over feature lists is
theater: you cannot rank items until you know what each item is *for*, and
"for" is a problem statement, not a component name.

The move mod-001 taught was to frame customer research as falsifiable
hypotheses. This module extends the same move to the prioritization queue.
Every item you're considering funding should be authored as a **bounded
problem statement** — who has the problem, what makes it a problem now,
what outcome you'd change, and what would falsify the claim that it's worth
solving.

## The three lineages you're synthesizing

Three practitioners built the modern vocabulary; they overlap on the essentials
and disagree on packaging.

**Marty Cagan — Opportunity Assessment.** Cagan's *Inspired* codifies a
short template a product manager writes *before* asking for engineering
capacity. The template exists to force a written answer to four things:
what business objective this addresses, what customer problem it solves, who
the target customer is, and how you'll know it worked. If any of those cannot
be answered in a sentence, the opportunity is not yet ready to prioritize; it
is a wish
([Cagan, *Inspired: How to Create Tech Products Customers Love*, 2nd ed.,
Wiley, 2017, Chapter 22, "Opportunity Assessment
Technique"](https://www.svpg.com/inspired-how-to-create-products-customers-love/);
[Cagan, "Product Manager Prep Work: Opportunity Assessment," SVPG, 2007 —
svpg.com/product-manager-prep-work-opportunity-assessment](https://www.svpg.com/product-manager-prep-work-opportunity-assessment/)).

**Teresa Torres — Opportunity Solution Tree.** Torres inherits the discovery
loop from mod-001 and turns the *tree* into an operational artifact for
prioritization. Every solution must attach to an *opportunity* (a customer
need, pain, or desire expressed in their words), and every opportunity must
attach to a *desired outcome* at the root. The tree makes it visible when a
proposed solution is orphaned (no opportunity underneath it) or when an
opportunity has zero solutions attached — the two shapes prioritization must
never allow to slip through
([Torres, *Continuous Discovery Habits*, Product Talk, 2021, Chapter 6,
"Mapping the Opportunity
Space"](https://www.producttalk.org/continuous-discovery-habits/); [Torres,
"Why I Use Opportunity Solution Trees," Product Talk, 2016 —
producttalk.org/2016/08/opportunity-solution-tree](https://www.producttalk.org/2016/08/opportunity-solution-tree/)).

**Steve Blank — Problem Interviews.** Blank's Customer Development separates
*problem-presentation* from *solution-presentation* interviews on purpose:
you find out whether a problem is real, painful, and currently being
worked around *before* you show any candidate solution. What you're
prioritizing at the top of the funnel are problems that survived a problem
interview, not ideas that survived a demo
([Blank & Dorf, *The Startup Owner's Manual*, K&S Ranch, 2012, Customer
Discovery Phase 2 — "Test the Problem"](https://www.strategyzer.com/library/the-startup-owners-manual)).

The synthesis for this module: **an opportunity is a customer-worded
problem, tied to a desired outcome, with an author who can defend the
target segment and a definition of what would count as success or failure.**
Anything narrower than that is a feature idea. Anything vaguer is a wish.

## The four sentences a bounded opportunity has to answer

Adapt Cagan's opportunity-assessment shape and Torres's tree shape into a
single writable artifact. A minimally-bounded opportunity has four sentences:

1. **Whose problem is it?** Name the target customer (or segment) tight enough
   that a stranger could recruit five candidates in an hour. Not "our users."
2. **What is the problem, in their words?** A verbatim clause you can point
   to in an interview transcript. Not a paraphrase, and not the name of your
   would-be feature. If you have never heard a customer say this, the
   opportunity is a hypothesis, not a finding — mark it that way.
3. **What outcome does solving it move?** Which company outcome (activation,
   week-4 retention, new-segment ARR, cost-to-serve) does progress on this
   opportunity plausibly move, and by roughly how much? A number is better
   than an adjective; a rough number with your uncertainty on it beats a
   round confident one.
4. **What would tell you you're wrong?** The falsifier. If you shipped the
   best solution you can think of to this opportunity and the outcome moved
   less than *X*, you would kill this line. Naming *X* now is the discipline;
   naming it after you ship is confirmation bias.

If a proposed line of work fails any of the four sentences, it is not ready
to enter the ranking exercise in Lecture 2. Send it back to discovery.

## A worked example

**Bad — feature-list phrasing:**

> *Add a Slack integration for enterprise customers.*

You cannot rank this. What problem does Slack solve for whom? What outcome
should improve? What would falsify it? None of these are answered.

**Better — opportunity phrasing:**

> - **Whose:** Sales engineers at 200–2,000-person B2B SaaS companies who
>   sit inside their prospect's Slack workspace during evaluation calls.
> - **In their words:** *"I don't know a deal is stuck until my AE forwards
>   me the email chain. By then I've missed the window to volunteer a fix."*
>   (Sourced from three of the last five wins, per pipeline transcripts.)
> - **Outcome:** Cut evaluation-stage cycle time by ≥5 business days on
>   enterprise deals (median of last quarter: 32 days).
> - **Falsifier:** If our next 10 enterprise-plan pilots ship the integration
>   and median cycle time drops <2 days, we treat the opportunity as
>   invalidated and de-fund; no "give it another quarter."

Now the item is rankable. You can compare it to another item that also has
four sentences. You cannot compare it to *"user analytics dashboard,"*
because that latter string is a component, not a claim.

## Why customer wording matters (and how to fake it, badly)

Torres is unusually strict about *the customer's language* on the opportunity
node. The rule sounds precious until you try to prioritize a tree where
half the "opportunities" have been rewritten in product-speak. Two problems
appear:

- **Aggregation error.** *"Users want better onboarding"* silently fuses
  three interviewees who had three different jobs: one couldn't find the
  primary action, one bounced on account setup, one didn't understand
  pricing. Ranking one blob and shipping one solution addresses none of
  them well.
- **Solution capture.** *"Add tooltips to onboarding"* looks like an
  opportunity if you squint. It isn't. It's a solution wearing an
  opportunity's hat. You'll rank it against real opportunities and pick it
  because it's small and legible; you'll never learn whether tooltips were
  the right instrument.

The check: for every opportunity on your tree, name the interview it came
from. If you can't, treat the node as a hypothesis (colour it differently on
the tree) until you can. Torres calls this the discipline of *evidence-backed
opportunities* — and it is the single most common thing product orgs skip
when they scale
([Torres, *Continuous Discovery Habits*, Chapter 6 — "Mapping the
Opportunity Space"](https://www.producttalk.org/continuous-discovery-habits/)).

## When the opportunity comes from a founder, not a customer

Half the opportunities on a pre-fit product's tree come from the founders'
vision, not from an interview. That's fine — the vision is where the search
starts (mod-001, Lecture 1). But *fine* only if you mark them:

- Route founder-sourced opportunities through the same four-sentence
  template.
- The "in their words" sentence gets a placeholder: *"no interview evidence
  yet — hypothesis from founding thesis dated <date>."* This is not a
  demotion; it is a flag that the falsifier fires early if the interviews
  don't validate the wording.
- Prioritization can still fund a founder-sourced hypothesis, but the plan
  attached to it must include the discovery work that would move it out of
  hypothesis into evidence-backed.

Un-marked founder items are how a tree quietly re-becomes a feature list.

## Boundaries this lecture keeps

- **What to *build*** — the solution branch of the tree — is out of scope
  for this module. Solution design lives in mod-003 (roadmap) and mod-004
  (delivery cadence).
- **How to *sell*** whatever you built — sales motion, GTM segmentation,
  enterprise pilot design — is deferred to
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum)
  (level 30). Prioritization tells that curriculum what to sell first; it
  does not replace it.
- **How the company *strategy*** gets authored — the thesis you're
  prioritizing against — is owned at level 20 by
  [founder-ceo-curriculum](https://github.com/ai-startup-curriculum/founder-ceo-curriculum).
  The CPO consumes the thesis; they don't author it alone. Lecture 6 comes
  back to this.

## Takeaways

- Feature-list roadmaps are unrankable. Force every candidate line into a
  four-sentence opportunity: whose problem, in their words, which outcome,
  which falsifier.
- Use Cagan's opportunity-assessment shape as the authoring template,
  Torres's opportunity solution tree as the *placement* of that shape
  inside a portfolio, and Blank's problem-interview rule as the evidence
  standard for the "in their words" sentence.
- Mark founder-sourced opportunities explicitly. Un-marked hypotheses are
  how a tree silently re-becomes the feature list you started with.

Lecture 2 turns bounded opportunities into a defensible ranking — and
picks apart the schemes (RICE, ICE, WSJF, Kano) most teams treat as
interchangeable when they are not.
