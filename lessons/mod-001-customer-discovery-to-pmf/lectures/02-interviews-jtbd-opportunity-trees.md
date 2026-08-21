# Lecture 2 — Interview craft, Jobs-to-be-Done, and the opportunity solution tree

## What a discovery interview is for

A discovery interview is not a sales call, a demo, or a survey. It is a
structured conversation whose purpose is to surface the interviewee's *past
behavior* around a problem — what they actually did, in what context, with
what workarounds, and at what cost. Past behavior is data. Future-purchase
intent, feature wishlists, and reactions to your mockup are, at best, noise
and, at worst, actively misleading.

Rob Fitzpatrick's *The Mom Test* (2013) is the canonical short read on this;
its three rules organize the rest of this lecture:

1. Talk about their life, not your idea.
2. Ask about specifics in the past, not generics or opinions about the future.
3. Talk less and listen more.

(*Source:* Fitzpatrick, *The Mom Test*, Chapter 1, "The Mom Test," which
introduces the three rules.)

## Why "would you buy this?" is a broken question

If you ask a friendly interviewee whether they'd buy your product, they will
usually say yes. They are being polite, they like you, they don't want to
puncture the vision. Now you have a "yes" in your notes that you'll take as
evidence, and the evidence is worthless. The Mom Test move is to ask about
concrete, past behavior instead:

- Not: *Would you use an app that tracks receipts?* — Instead: *Walk me
  through what you did with the receipts from your last three jobs.*
- Not: *How much would you pay for this?* — Instead: *What are you paying
  today to solve this? What have you tried and dropped?*
- Not: *Do you think this would help you?* — Instead: *When's the last time
  this problem cost you money or time? What did you do?*

The point of the past-tense reframe is that lying about the past is harder
than fabricating an opinion about a hypothetical future. If the interviewee
has never actually tried to solve the problem — no workaround, no failed
tool, no time cost they can cite — that's evidence too: they don't have the
problem, or don't have it acutely enough to act.

## A workable interview shape

There is no one true script, but this shape works and is easy to teach to a
team:

1. **Frame** (1 min). "I'm trying to understand how people like you handle
   *X*. I'm not selling anything; I want to learn from your experience."
2. **Life-of-the-problem** (10–15 min). Ask them to walk you through the
   most recent time the problem showed up. Whose day did it interrupt? What
   did they reach for? What was the cost? Follow every specific with "and
   then what?"
3. **Workarounds & tools** (10 min). What tools, spreadsheets, humans, or
   habits do they currently use? What did they try and abandon, and why?
4. **Trigger and frequency** (5 min). What kicks off the problem? How often?
   How predictable?
5. **Close** (5 min). Ask permission to follow up, and ask who else they'd
   introduce you to (this is your recruiting funnel).

Do not demo. Do not pitch. If the interviewee asks what you're building, tell
them briefly and steer back — you're mining their past, not testing your
future.

## Jobs-to-be-Done as a synthesis framework

An interview yields transcripts and impressions. You need a shape to
synthesize into so that ten interviews become a claim, not a folder. Clayton
Christensen and colleagues argue that customers "hire" a product to make
progress on a job in a specific circumstance, and that the *job*, not the
demographic, is the unit of analysis:

> *People don't simply buy products or services; they "hire" them to make
> progress in specific circumstances.*
> — Christensen, Hall, Dillon & Duncan, "Know Your Customers' Jobs to Be
> Done," *Harvard Business Review*, September 2016 —
> [hbr.org/2016/09/know-your-customers-jobs-to-be-done](https://hbr.org/2016/09/know-your-customers-jobs-to-be-done).

A useful JTBD statement has a *when*, a *want to*, and a *so that*: **When**
I'm on-site finishing a job and the customer wants a printed receipt, **I want
to** produce one from my phone without opening a laptop, **so that** I get paid
before I leave. The statement lets you spot two products fighting for the
same job (yours vs. the paper pad in their van) and generate solution ideas
that respect the circumstance (must work offline, must fit in a work-glove
workflow).

The JTBD literature is not a single canonical method — there is the
Christensen "milkshake" school and Anthony Ulwick's earlier Outcome-Driven
Innovation school ([Ulwick, "Turn Customer Input into Innovation," *HBR*,
January 2002](https://hbr.org/2002/01/turn-customer-input-into-innovation)).
For discovery, the useful common core is: *frame around the job, not the
persona; separate the job from your solution to it*.

## From interviews to an opportunity solution tree

Teresa Torres's operational output for continuous discovery is the
**opportunity solution tree**: an outcome at the root, opportunities (customer
needs, pains, desires expressed as their words) branching off the outcome,
solution ideas branching off each opportunity, and assumption tests branching
off each solution
([Torres, "Why I Use Opportunity Solution Trees," Product Talk, 2016 —
producttalk.org](https://www.producttalk.org/2016/08/opportunity-solution-tree/);
[Torres, *Continuous Discovery Habits*, Chapter 6, "Mapping the Opportunity
Space"](https://www.producttalk.org/continuous-discovery-habits/)).

The tree is a *decision-making* artifact, not documentation. Its point:

- Every solution the team proposes must attach to an opportunity you can
  point to in someone's transcript. If it doesn't, it's a feature you want to
  build, not a customer need you're addressing.
- The tree makes it visible when two solutions target the same opportunity
  (comparison rather than everyone-gets-a-quarter) and when an opportunity has
  zero solutions attached (a gap to design against).
- It disciplines discovery-vs-delivery: if you're generating solutions faster
  than opportunities, you're guessing.

## The right cadence

Torres's continuous-discovery baseline is one interview *per team per week*,
sustained ([Torres, *Continuous Discovery Habits*, Chapter 1's definition of
continuous discovery](https://www.producttalk.org/continuous-discovery-habits/)).
Pre-fit, push higher — three to five interviews a week is realistic when the
founding CPO is doing them personally, and it takes 8–12 interviews with a
segment before patterns stabilize and new interviews stop surprising you.
<!-- needs-research: 8–12 interviews as a saturation threshold is
practitioner folklore (Steve Portigal, various user-research texts). Cite a
primary source (Portigal, *Interviewing Users*, 2nd ed., 2023) once verified. -->

## What good interview notes look like

- **Verbatim quotes** for anything emotional or specific ("I lost the
  receipt from the plumbing supply run and just ate the $312").
- **Timestamps or frequencies** ("last Thursday", "twice this month").
- **Named workarounds** ("she uses a shared Google Sheet with her wife").
- **A one-line synthesis** at the top of the notes: what job, what
  circumstance, what current solution, what's broken about it.

Notes that are only your interpretations, with no quotes and no specifics,
are stories you told yourself. Don't trust them.

## Takeaways

- Interview about the past; the future is fiction.
- Frame findings as Jobs-to-be-Done, not features or personas.
- Synthesize into an opportunity solution tree so the team can see what's
  evidence-backed and what's a wish.
- Continuous discovery is a *cadence*, not a project — weekly at minimum,
  higher pre-fit.

Lecture 3 covers how to know when you've actually found fit.
