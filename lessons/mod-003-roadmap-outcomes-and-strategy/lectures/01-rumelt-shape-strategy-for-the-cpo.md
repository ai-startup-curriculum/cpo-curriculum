# Lecture 1 — Rumelt-shape strategy for the founding CPO

## The setup

Ask a first-time founding CPO for their *product strategy* and the
first draft you get back will almost always be one of three things:
a slogan (*"we're building the AI-native ERP"*), a market-size chart
(*"it's a $47B TAM growing 22% a year"*), or a list of themes
(*"data quality, AI copilots, workflow automation"*). None of those
is a strategy. Each is a piece of the wrapper around a strategy —
the vision, the market opportunity, the thematic surface area — but
a stranger cannot read any of them and predict what the company
will and will not do next quarter.

Richard Rumelt names this failure directly: what most companies
call strategy is what he calls *bad strategy* — fluff, mistaking
goals for strategy, mistaking a wish for a plan, or failure to face
the challenge. And the alternative — *good strategy* — is a
disciplined, three-part artifact he calls the **kernel**: a
diagnosis, a guiding policy, and a coherent set of actions
([Rumelt, *Good Strategy Bad Strategy: The Difference and Why It
Matters*, Crown Business, 2011, Chapter 5, "The Kernel of Good
Strategy"](https://www.crownpublishing.com/archives/feature/good-strategy-bad-strategy-richard-rumelt)).

Melissa Perri comes at the same failure from the product side. Her
*Escaping the Build Trap* names the mode where a product
organization confuses *output* (shipping features) with *outcome*
(moving a business number). The build trap is what happens when
there is no product strategy underneath the roadmap: teams get
graded on ship velocity because nobody has authored what "the right
thing to ship" would even mean
([Perri, *Escaping the Build Trap*, O'Reilly, 2018, Chapter 4,
"The Product Strategy
Gap"](https://www.oreilly.com/library/view/escaping-the-build/9781491973783/)).

The move this lecture teaches is the merger: use Rumelt's kernel as
the *shape* of your product strategy, and use Perri's outcome
orientation as the *content* of the guiding policy and the coherent
actions. The output is a written strategy a first-week hire can
read to understand what the company is doing and — as importantly
— what it is not.

## Where the CPO's strategy sits inside the company's

You are not writing a *company* strategy. That is level-20 work,
owned by the founder-CEO, and covered at that level by
[founder-ceo-curriculum](https://github.com/ai-startup-curriculum/founder-ceo-curriculum).
The company strategy answers questions like *what game are we
playing, who is our theory-of-winning customer, what is our
theory of the market's future shape.*

The **product strategy** is the CPO-scope subsection of that. It
inherits the company diagnosis from the founder-CEO and answers a
narrower question: *given that game, what does the product need to
be, in what sequence, to give the company its best shot?* Casey
Winters lays this out cleanly in "The Product Strategy Stack":
company vision → company strategy → **product vision → product
strategy** → product initiatives → product-team objectives, with
the CPO owning the middle two layers and consuming the layers
above
([Winters, "The Product Strategy Stack," 2019 —
caseyaccidental.com/the-product-strategy-stack](https://caseyaccidental.com/the-product-strategy-stack/)).

Two things follow. First, if the company strategy doesn't exist —
which is more common than founding CPOs admit — your Exercise 1
memo says so. You cannot author a good product strategy on top of
a bad company one, and pretending you have will produce a document
that will silently drift the first time the founder-CEO reprioritizes
the market. Second, your product strategy has to visibly consume the
company one: the diagnosis you write should read as *the product
implications of the company diagnosis*, not as a fresh diagnosis
of a different problem.

## The kernel — three parts, not four

Rumelt's kernel is deliberately austere. It is:

1. **A diagnosis.** A simplifying claim about what the challenge
   *actually is*. Not a list of problems; a naming of the *decisive*
   one. The diagnosis "brings clarity to a bewildering situation by
   identifying certain aspects as critical." A good diagnosis
   discards information; a bad one lists everything.
2. **A guiding policy.** An overall approach chosen to *cope with
   or overcome* the obstacles named in the diagnosis. It is not the
   goal; it is the *approach that makes the goal achievable*. A
   guiding policy is directional (do X, don't do Y), not
   aspirational (be great at X).
3. **A coherent set of actions.** The concrete moves — resource
   commitments, sequences, and dependencies — that follow *from*
   the guiding policy. "Coherent" here is a specific technical
   claim: the actions have to reinforce each other, not merely
   coexist. A list of unrelated initiatives that each look
   reasonable is not coherent action; it is a portfolio without a
   thesis.

([Rumelt, Chapter 5, "The Kernel of Good
Strategy"](https://www.crownpublishing.com/archives/feature/good-strategy-bad-strategy-richard-rumelt).)

The three parts are not interchangeable and are not composable in a
different order. You cannot start with the actions and back-derive
the diagnosis; that is how *feature-list-plus-slogan* documents get
written. You cannot skip the guiding policy on the theory that it
"emerges from the actions;" that is how portfolios without theses
get written. You cannot substitute a mission statement for a
diagnosis; that is how slogans get written.

## What the four bad-strategy shapes look like as a *product* document

Rumelt names four hallmarks of bad strategy: **fluff, failure to
face the challenge, mistaking goals for strategy, bad strategic
objectives.** The founding-CPO version of each is worth naming
because the product-strategy documents you inherit almost all match
one:

- **Fluff.** The document reads well and says nothing you can act
  on. *"We will be the AI-native platform of record for
  compliance-heavy verticals."* You cannot derive what to build
  next quarter from that sentence. Fluff is diagnosable by trying
  to write the actions column: if the actions could equally serve
  any of five different diagnoses, the diagnosis was fluff.
- **Failure to face the challenge.** The document lists strengths
  and market opportunities but does not name what is actually hard.
  The reader gets a picture of what winning would look like and no
  picture of what has to be *solved* for winning to be possible.
- **Mistaking goals for strategy.** *"We will hit $10M ARR and 90%
  retention by end of next year."* Those are outcomes you want; a
  strategy is the *how* that would make those outcomes plausible.
  Perri names the same failure with the term *goal-only roadmaps* —
  you have declared an outcome, but the guiding policy and the
  actions are missing.
- **Bad strategic objectives.** A "strategy" that is a scattergun
  of unrelated initiatives — each individually justifiable, none of
  which reinforce each other. Rumelt calls this the *dog's dinner*.
  Product-strategy version: a themes list where "AI copilots,"
  "self-serve onboarding," "enterprise SSO," and "usage-based
  billing" sit side by side with nothing binding them.

If your draft product strategy matches any of these four shapes,
send it back to the diagnosis before you go any further.

## The Perri build-trap frame as the content of the strategy

Perri's core move is to force everyone above the delivery layer to
declare **outcomes**, not outputs. In the build-trap frame:

- **Output** = something you shipped (a feature, an integration, a
  redesign). Countable, ship-scheduleable, and — by itself — no
  evidence of business value.
- **Outcome** = a change in customer behavior or business result
  that shipping the output was supposed to produce (activation
  rate, week-4 retention, expansion revenue in a segment,
  cost-to-serve on a workflow).

The build-trap collapses the two: the roadmap lists outputs, the
team gets graded on shipping them, and the question *did shipping
this move the outcome we cared about* never gets asked
([Perri, Chapter 3, "The Build Trap and What It
Costs"](https://www.oreilly.com/library/view/escaping-the-build/9781491973783/)).

For the *strategy* document, the implication is direct: the
guiding policy and the coherent actions must be outcome-shaped.
The guiding policy names *which outcomes* you are moving and
*which you are explicitly not*. The actions name the product bets
you believe will move those outcomes, with the falsifier attached
that would tell you the bet was wrong.

## A worked example — bad, and then good

The examples below are synthetic and are for shape only. The
numbers, segments, and specifics are illustrative; the
resemblance to any specific company is not a case study and should
not be cited as one.

**Bad — a themes-list "strategy":**

> **Product strategy, FY26**
>
> - Vision: be the AI-native operating system for compliance-heavy
>   B2B workflows.
> - Themes: (1) AI copilots, (2) workflow automation, (3) data
>   quality, (4) enterprise readiness.
> - Goal: reach $10M ARR by end of FY26 with net retention above
>   110%.

You cannot read this document and predict what the company will
and will not do next quarter. All four themes are always plausible;
the goal is a wish; there is no diagnosis. This is the *dog's
dinner* shape.

**Better — a Rumelt-shape product strategy:**

> **Product strategy, FY26**
>
> **Diagnosis.** Our current customer base is 40+ mid-market
> compliance teams whose primary job-to-be-done is *"produce an
> auditor-ready evidence package fast, without re-collecting from
> the same source system twice."* The evidence-collection step —
> not the audit-report authoring step — is where they spend 60% of
> their pre-audit time and where they most often re-buy the
> spreadsheet workaround we are supposed to be replacing. This is
> the decisive challenge: we are competing with the spreadsheet in
> the collection loop, not with a compliance-report authoring tool
> at the top of the funnel. If we do not solve the collection loop
> in FY26 we will not earn the right to be the authoring tool in
> FY27.
>
> **Guiding policy.** Concentrate FY26 product investment on the
> evidence-collection loop for the mid-market compliance-team
> segment (SOC2, ISO 27001, HIPAA). Defer the auditor-facing
> authoring surface, the enterprise-tier SSO / IdP integrations,
> and the horizontal workflow-automation platform. In every
> allocation dispute this quarter, "does it shorten the collection
> loop for a mid-market compliance team?" is the tie-breaker.
>
> **Coherent actions.**
>
> 1. Land a source-system connector library (Okta, AWS, GitHub,
>    JIRA, at least six others) that covers ≥80% of the evidence
>    types the top 20 accounts collect. This is the platform bet;
>    it is deliberate and its falsifier is in Lecture 4.
> 2. Ship a review workflow (assign, remind, sign-off) that
>    replaces the spreadsheet in the collection loop, not
>    downstream. Falsifier: if <30% of the top 20 accounts have
>    replaced the collection spreadsheet by Q3, the guiding policy
>    was wrong and we escalate.
> 3. Do not ship the auditor-portal, the workflow-automation
>    editor, or the enterprise-tier IdP work. When those come up in
>    prioritization, the answer is "yes, in FY27 if we win the
>    collection loop."
>
> The three actions reinforce each other: connectors feed the
> review workflow, the review workflow generates the account
> pattern that funds the next round of connectors, and the deferral
> of the three FY27 items is what keeps the engineering capacity
> for both.

The good version discards information. It names one decisive
challenge, one guiding policy, three actions, and — crucially —
three things it is *not* doing. It is falsifiable at the guiding-
policy level: the "collection-loop tie-breaker" and the Q3
falsifier are how you know at end of Q3 whether the strategy was
right.

## Discarding information — the CPO's hardest job

Rumelt is emphatic that a good diagnosis *discards* information.
This is the move first-time founding CPOs most often refuse.
Discarding information means telling the founder-CEO which market
opportunities you are choosing *not* to pursue, telling GTM which
customer segments the product is choosing *not* to serve well this
year, and telling the engineering team which platform capabilities
are *not* on the roadmap. Every one of those sentences is
politically expensive. That expense is the point: a strategy that
costs nothing to say has decided nothing.

Two counter-moves you will feel pressure to make and should
resist:

- **The everything-strategy.** *"We are prioritizing the collection
  loop AND the authoring surface AND the workflow platform."* This
  is the failure to face the challenge in a diplomacy costume.
  Rank the challenge; if all three are truly of equal decisiveness
  the diagnosis has not yet finished.
- **The reversible-strategy.** *"We are prioritizing the collection
  loop this quarter and we can shift to the authoring surface if
  the market moves."* This sounds prudent and is usually a way to
  avoid committing to the deferral. The falsifier discipline (from
  mod-002 Lecture 1) is what makes reversibility earned rather
  than a euphemism for indecision — pre-register the signal that
  would trigger the shift, or the reversibility is fiction.

## Where the CPO writes and where the CPO consumes

For clarity, and because the exercises depend on it:

- **The CPO authors:** the product diagnosis, the product guiding
  policy, the coherent actions, the falsifiers, and the deferrals.
  These are the exercise-1 deliverable.
- **The CPO consumes:** the company diagnosis, the company theory
  of winning, the runway line, the fundraising narrative, and the
  architectural sequencing constraints from the CTO. Each of those
  is authored elsewhere at the level owned by the corresponding
  curriculum (level-20, level-40, level-25). Your product strategy
  should *cite* those inputs — not silently re-derive them.

The most common first-CPO failure is authoring a product strategy
without visibly consuming any of these — which produces a document
that will be quietly re-litigated the first time the founder-CEO
gives an investor update.

## Boundaries this lecture keeps

- **Company-strategy authoring** — Rumelt-shape *company* strategy,
  theory of winning, board narrative — is level-20 work owned by
  [founder-ceo-curriculum](https://github.com/ai-startup-curriculum/founder-ceo-curriculum).
  You author the product subsection; you do not author the wrapper
  alone.
- **Board-facing narrative craft** — the polish and story-craft of
  the board-deck narrative the strategy lives inside — is level-40
  work owned by
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum).
  Lecture 5 is where the product-strategy content of a board
  read-out gets covered; the wrapper craft is the finance
  curriculum's job.
- **Roadmap shape** — Now / Next / Later, objective-oriented
  roadmaps, the physical layout of the artifact — is the subject
  of Lecture 2. The strategy is the *input* to that shape; it is
  not the roadmap.
- **OKR authoring** — key-result mechanics, the CPO-scope OKRs
  that operationalize the guiding policy — is Lecture 3.

## Takeaways

- A product strategy is a Rumelt-shape kernel: **diagnosis**
  (which decisive challenge), **guiding policy** (how you're going
  to cope with it), **coherent actions** (the mutually reinforcing
  moves that follow). Anything shorter is a slogan.
- The Perri build-trap frame is the *content* of the kernel:
  guiding policy and actions must be shaped as outcomes to move,
  not outputs to ship, with a falsifier attached to each.
- Good strategy *discards*. It names what you are not doing, in
  writing, with a tie-breaker rule for the next allocation
  dispute. A strategy that costs nothing to say has decided
  nothing.
- The CPO's product strategy sits inside the founder-CEO's
  company strategy. Author the product layer; consume the
  company layer; visibly cite it so the strategy doesn't quietly
  get re-litigated.

Lecture 2 turns the kernel into a Now / Next / Later (or
objective-oriented) roadmap — the physical artifact the guiding
policy becomes on a wall.
