# Lecture 3 — PRDs in the Amazon 6-pager / working-backwards shape

## The setup

Ask a first-time founding CPO to show you a PRD and you will
usually get one of three artifacts. The first is a template
lifted from a big-company PRD library — twenty sections, most
of them left as "TBD," a fifty-line acceptance-criteria table
where the interesting product decisions have been buried. The
second is a Jira epic with two paragraphs of intent above a
list of stories. The third is a Notion doc with a heading
called *Overview* and, underneath, three months of accreted
comments no one has resolved. None of these is a PRD in the
sense this module means. Each is a *symptom* of the underlying
disease: the team has not been forced to answer the question
*what does this look like to a customer, and why is it worth
doing?* before it starts building.

Amazon's answer to this is well documented and — for a
founding CPO at pre-seed / seed scale — the single most
useful discipline you can adopt for the PRD artifact. It is
called the **six-pager** (also *the narrative* or, in its
launch-scoped variant, the *PR/FAQ* / *working-backwards*
document). Jeff Bezos banned slide decks for senior review in
his 2004 shareholder letter and mandated *narrative memos,
maximum six pages, with an appendix*, on the argument that
narrative prose forces sharper thinking than bullets do
([Bezos, 2004 Letter to Shareholders](https://www.aboutamazon.com/news/company-news/2004-letter-to-shareholders)).
Colin Bryar and Bill Carr, two former Amazon executives,
document the practice in *Working Backwards*, including the
PR/FAQ variant used for new-product proposals
([Bryar & Carr, *Working Backwards*, St. Martin's, 2021,
Chapters 4 and 5](https://www.workingbackwards.com/)).

This lecture teaches the six-pager as the founding-CPO's PRD
form — what goes in it, in what order, why the order matters,
how it differs from a spec, and how it lands in either of the
Lecture 2 operating models. Exercise 3 makes you write one.

## Why narrative, not bullets

Bezos's argument is worth stating in his own frame: bullet
points allow the author to skip the *why does this connect
to that*. Prose does not. When you write a PRD as bullets,
you can list six things that all sound reasonable and never
notice that item #3 contradicts item #5, that item #2's
success would make item #4 redundant, or that item #6 is
actually the whole idea and the rest are consequences. When
you write those same six things as a paragraph, the
contradictions become uncomfortable, the redundancies
become audible, and the actual thesis surfaces.

Bryar and Carr describe the mechanism this way: "The
six-page narrative memo is fundamentally a device for
transferring understanding from the author to the reader.
Bullet points transfer conclusions; narrative transfers the
reasoning behind them"
([Bryar & Carr, Chapter 4: "Narratives and the Six-Pager"](https://www.workingbackwards.com/)).
The move is the same one Rumelt made about strategy in
mod-003 Lecture 1: bullets let a *dog's dinner* look like a
plan; prose does not.

For a founding CPO, the practical implication is that the
PRD is a *writing exercise*, not a *filling-in-the-template*
exercise. It will take four hours to write a good one, not
forty minutes, and that is the point. You are not being
graded on the PRD; you are using the PRD to force yourself
to notice what you don't yet know.

## The two variants — PR/FAQ vs six-pager

Amazon uses two closely related narrative shapes. Both are
in scope for a founding CPO; use the right one for the
bet's size.

**The PR/FAQ (working-backwards document).** Used for
*net-new products* and *substantial new capabilities* — the
kind of bet that would justify a Shape Up cycle of its own
or a multi-week kanban thread. It starts with a **mock press
release** written *as if the product had already shipped*,
followed by a **FAQ** anticipating the questions customers,
executives, and internal teams will ask. Bryar and Carr
describe the PR/FAQ as *working backwards from the customer*:
you cannot write the press release without deciding what
outcome the customer actually gets, in what words they'd
describe it, and what price / packaging / positioning it has
at ship
([Bryar & Carr, Chapter 5: "Working
Backwards"](https://www.workingbackwards.com/)).

**The six-pager (narrative memo).** The general-purpose
narrative memo used for most significant product decisions
that are not net-new launches. Six pages, prose, with an
appendix. The structure is not rigidly fixed at Amazon —
different teams template it differently — but the shape is
consistent: context, the customer / problem, the proposal,
the mechanism, the metrics, the risks, and the appendix.

The lecture teaches both. For most week-to-week bets in
either Shape Up or kanban, the six-pager is the right form.
For a launch-shaped bet (a new surface, a new tier, a new
product), the PR/FAQ is worth the extra discipline of
writing the press release.

## The PR/FAQ, section by section

For a PR/FAQ. Adapt to your product's naming; do not skip
sections.

### Section 1 — the press release (one page)

Written as if the product had already shipped. Real
company, real quotes, real numbers. Length: one page.
Shape:

- **Headline.** One line the customer would recognize.
- **Sub-headline.** Two lines naming the customer and
  the benefit.
- **Summary paragraph.** Two to four sentences on the
  problem, the product, and the outcome for the
  customer.
- **The problem paragraph.** What was hard before?
- **The solution paragraph.** How does the product solve
  it?
- **A leader quote.** From the founder-CEO or the CPO,
  saying what the company believes about the problem
  and what makes the product possible now.
- **A customer quote.** From a hypothetical (but
  realistic) target customer, in the words they would
  actually use.
- **A call to action.** How does a customer get started?

The press release is not marketing writing. It is a
*thinking artifact*. If you cannot write the customer quote
convincingly, you do not yet know what the customer will
say — which means you do not yet know what you're building.
Send yourself back to discovery (Lecture 1) before you
continue.

### Section 2 — internal FAQ (two to three pages)

The questions your executives, engineers, and internal
teams will ask, answered honestly. Bryar and Carr suggest
these questions at minimum
([Bryar & Carr, Chapter 5](https://www.workingbackwards.com/)):

- Why is this the right thing to do, and why now?
- Who is the customer, in one segment? What is their
  job-to-be-done (mod-001 Lecture 3)?
- What is the specific problem we are solving? What
  evidence do we have (mod-001 evidence standard)?
- How does the customer solve this today, and why is
  that inadequate?
- What is our proposed solution, in one paragraph? What
  is the mechanism (mod-002 Lecture 1's *bounded
  opportunity* discipline applies here)?
- How is our solution meaningfully different from what
  exists?
- What is the timeline and appetite for this work?
  (This links to Lecture 2's operating-model choice.)
- What are the customer-side risks? (Adoption, trust,
  behavior change, migration cost.)
- What are the business risks? (Cost to build, cost to
  serve, cannibalization, revenue exposure.)
- What are the technical risks? (Feasibility, integration
  dependencies, latency / cost budget for AI substrate.)
- What is our pre-registered success metric? On what
  horizon? What signal would falsify the bet? (The
  falsifier discipline from mod-002 Lecture 1.)
- What are we explicitly not building in v1?
- What is the pricing / packaging read? (Consumed from
  mod-006, but named here so the launch does not surprise
  the pricing decision.)

The FAQ is where the *hard* thinking lives. If a founding
CPO's PR/FAQ has a two-line answer to *"what evidence do
we have for the customer problem?"* the document is not
ready.

### Section 3 — external FAQ (one page)

Questions the customer or press will ask. Pricing, launch
availability, geographic scope, competitive comparisons,
migration path, security / compliance posture. Shorter than
the internal FAQ, but non-optional — writing it forces you
to notice the questions you cannot yet answer publicly.

### Section 4 — appendix (unbounded, but read on demand)

Screens, wireframes, data, source-system dependencies,
detailed metric definitions, links to the discovery evidence
(interview notes, opportunity tree slice), engineering
architecture sketches. Everything the memo *references* lives
here. The reader should be able to read the six pages without
the appendix and understand the bet; they should be able to
*audit* the six pages by reading the appendix.

## The general six-pager, section by section

For a decision that is not a new-product launch — a
substantial feature bet, a re-architecture of an existing
surface, a change to a workflow that affects a significant
segment — the general six-pager is the right form. Structure
adapted from *Working Backwards* Chapter 4 and the
practitioner writing that followed it (see resources.md):

### Section 1 — context and diagnosis (half page)

What is the *current state* — the strategy this sits inside
(mod-003), the opportunity this responds to (mod-002), the
discovery evidence that grounds it (mod-001)? What is the
*decisive challenge* the memo addresses? (Rumelt-shape
diagnosis, mod-003 Lecture 1.) This is the "why now" answer,
condensed.

### Section 2 — the customer and the problem (one page)

Who is the customer, in the specific segment for this bet?
What job are they trying to do? What is the problem —
authored in the customer's words, per mod-001 Lecture 2 and
mod-002 Lecture 1. What evidence do you have that the
problem is real and material? (Named interview count, named
data pull, named eval result if the surface is AI-substrate.)

### Section 3 — the proposal (one page)

What are we proposing to build? Named as an *outcome to
move*, not a feature to ship. What is the mechanism — the
sketch of how the product changes to move the outcome?
What are the top three design decisions the team will
face, and — for each — the axis on which they should be
made? (See Lecture 4 for the pixel-and-microcopy version
of this.)

### Section 4 — how we know it worked (one page)

The pre-registered success metric, the horizon, the
falsifier. What would tell us at four weeks that the bet
is working? At twelve? What signal would trigger a
Not-Now demotion or a kill (mod-002 Lecture 5, mod-003
Lecture 2)? This is where the CPO writes down what
they'll believe about the bet in advance of the ship,
which is what stops after-the-fact re-interpretation.

### Section 5 — what we're not doing (half page)

Explicit deferrals for v1. Named requests from
stakeholders that will not be honored in this bet. Why
the guiding policy (mod-003 Lecture 1) forces the
deferral. What would move the deferral in a later bet.

### Section 6 — risks and open questions (half page)

Adoption risks, technical risks, cost / latency risks for
AI substrate (Lecture 5), operational risks (support
load, on-call impact — check with the CTO). Open
questions the memo has *not* yet resolved and how they'll
be resolved before ship.

### Appendix

Everything the memo references. Screens, data pulls,
interview notes, prompt / eval sketches, cost / latency
modeling. Unbounded, on-demand.

## The reading ritual

Both PR/FAQ and six-pager assume a specific *reading
ritual* Amazon calls the **silent meeting**: the group
gathers, and the first 20–30 minutes are spent *reading the
memo silently*. Only then does the discussion begin. Bezos
insisted on it because it eliminates the "did you all get
a chance to read this before we meet?" ambiguity that lets
half a room bluff their way through a discussion they
didn't prepare for
([Bezos, 2004 Letter](https://www.aboutamazon.com/news/company-news/2004-letter-to-shareholders);
Bryar & Carr, Chapter 4](https://www.workingbackwards.com/)).

Do this. It is the single most under-adopted piece of the
practice at startup scale. A silent-meeting-shaped review
of a six-pager is uncomfortable the first time, and it
consistently produces better decisions than the
"walk-through-the-slides" ritual it replaces. Twenty minutes
of silence at the top of a bet meeting or a Shape Up bet
review is worth twenty PRDs of the wrong shape.

## Where the six-pager lands in the cadence

- **In Shape Up:** the six-pager is the *shaped pitch*, or
  the appendix to it. A pitch (Singer's shape — problem,
  appetite, solution sketch, rabbit holes, no-gos) is
  compatible with a six-pager as the fuller-narrative form
  behind it. The bet meeting reads the six-pager silently,
  then decides the bet.
- **In weekly kanban:** the six-pager is the *artifact for
  the larger items*. Not every kanban item warrants a
  six-pager — a one-week bug fix does not. A three-week
  workflow change or a new surface addition does. The
  Monday commit meeting reads the six-pager silently for
  any item over a threshold you set (usually: any item that
  will take longer than one week or affects a live segment
  of users).

## The anti-PRD-gestation discipline

The single biggest failure mode of PRDs at startup scale
is *gestation*: the doc gets started, gets shared, gets
commented on, spends four weeks in review, and by the time
it is "ready" the market context has shifted and the memo
is a museum piece. Design against this explicitly:

- **Timebox the PRD.** A six-pager is a four-hour write, a
  one-hour silent review, a one-hour discussion. Not four
  weeks. If yours is taking three weeks, the document is
  hiding a discovery problem — you don't yet know what
  the bet is, and no amount of drafting will fix that.
  Go back to Lecture 1.
- **Draft in the shape from the first draft.** Do not
  write it as bullets and then convert; do not "sketch the
  outline first." Draft the press release, or the context
  paragraph, in full sentences from minute one. The
  discipline is doing the hard thinking in prose form.
- **Do not open comments before it is readable.** Ten
  reviewers commenting on a half-drafted memo will send
  the draft in ten directions and stall it. Draft in
  private, share when there is a coherent thing to react
  to, take comments in one silent-meeting-shaped review,
  then close the doc.
- **Ship the artifact behind the PRD, not the PRD.** The
  PRD is not the ship. It is the *input* to the ship.
  Teams that treat the PRD as a deliverable in itself —
  green-check the doc, then start eight weeks of build —
  are the ones that get eaten by PRD-gestation. The doc
  exists to make the build cleaner; if it isn't doing
  that, cut it.

## What the six-pager is *not*

It is worth being explicit about the two shapes it is
often confused with:

- **Not a spec.** A spec is a detailed engineering
  contract — data model changes, API endpoint definitions,
  UI acceptance criteria at the field level. The
  six-pager is the *narrative* the spec descends from, if
  a spec is needed at all. Many kanban-shaped teams do not
  produce specs; the six-pager plus the Figma mockup
  (Lecture 4) is enough.
- **Not a design doc.** A design doc, in the engineering
  sense (Google-style: the *how* of implementation, at
  architecture depth) is a CTO / eng-lead artifact, often
  owned in the codebase, addressed to the engineering team.
  A six-pager is the *product* narrative, owned by the CPO,
  addressed to the senior group deciding the bet. The
  two documents co-exist; the six-pager is upstream.

## Where the CPO writes and where the CPO consumes

- **The CPO authors:** the press release, the FAQ (both
  variants), the customer / problem section, the proposal,
  the pre-registered metric + falsifier, the deferrals.
  These are the six-pager deliverable.
- **The CPO consumes:** the engineering-risk section
  (feasibility, cost / latency budget) from the tech lead;
  the pricing / packaging read from the pricing owner
  (mod-006); the runway line if the bet is material to
  it; the on-call / support-load estimate from the eng
  lead (level-25, owned by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)).
  Consumed means *cited*, not *silently re-derived*.

## Boundaries this lecture keeps

- **Discovery evidence** — interview counts, JTBD
  framings, opportunity trees — is owned by
  [mod-001](../../mod-001-customer-discovery-to-pmf/README.md).
  The six-pager cites the discovery evidence; it does not
  re-run discovery.
- **Opportunity ranking** — scoring, deferrals, kills —
  is owned by
  [mod-002](../../mod-002-opportunity-assessment-and-prioritization/README.md).
  The six-pager describes the bet, not the ranking that
  earned it a slot.
- **Roadmap and strategy** — the multi-quarter shape the
  bet sits inside — is owned by
  [mod-003](../../mod-003-roadmap-outcomes-and-strategy/README.md).
- **Figma, microcopy, and design taste** — the
  pixel-and-string craft the six-pager sends downstream to
  the appendix — is Lecture 4.
- **Agentic UX iteration loops** — the AI-substrate-specific
  content of the *mechanism* section — is Lecture 5.
- **Engineering design docs** at implementation depth are
  level-25 work owned by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum).
- **The launch / marketing side of a PR/FAQ** — the
  external press release actually being *published* — is
  GTM work owned by
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum).
  The six-pager press release is a *thinking* artifact,
  not a launch artifact.

## Takeaways

- The founding CPO's PRD form is Amazon's **narrative
  six-pager** — prose, six pages, with an appendix — and
  its launch-scoped variant, the **PR/FAQ**. Both are
  written as *thinking artifacts*, not fill-in
  templates.
- Narrative forces sharper thinking than bullets because
  contradictions, redundancies, and gaps in the
  reasoning become audible in prose that stay hidden in a
  list.
- The PR/FAQ starts with a mock press release written *as
  if the product had shipped*; the six-pager starts with
  context / diagnosis. Both end with pre-registered
  metrics, deferrals, and an appendix.
- The **silent-meeting reading ritual** — 20–30 minutes
  of silent reading before discussion — is non-optional
  and consistently produces better decisions than the
  slide-walk-through it replaces.
- Design against **PRD gestation** with a timebox, a
  written-in-prose-from-minute-one discipline, no early
  comments, and a rule that the ship — not the PRD — is
  the deliverable.
- The six-pager is not a spec and not an engineering
  design doc. It is the product narrative the other
  artifacts descend from.

Lecture 4 pulls the CPO's hands from the memo into the
Figma file — the design taste and microcopy discipline the
market now expects the founding CPO to bring personally.
