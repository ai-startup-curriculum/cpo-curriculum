# Lecture 6 — Ship-velocity anti-patterns and how to design them out

## The setup

Ship velocity dies incrementally. No CPO wakes up on a
Monday morning and finds the team has stopped shipping. What
happens instead is a slow accretion of *ceremonial work
that does not produce ships* — planning meetings that
generate decisions no user ever sees, PRDs that gestate for
weeks, designs that get rewritten inside code review,
hand-offs that absorb a designer's day into an eng thread,
retros that observe the same problem for the third quarter
in a row. Each of these ceremonies had a plausible reason to
exist. Together they strangle the cadence.

This lecture names the five ship-velocity anti-patterns most
likely to appear in a founding-CPO cadence, diagnoses each,
and — this is the point — teaches the specific counter-move
the *cadence itself* must contain to design each out. The
move is not to observe the anti-pattern in a retro and hope
it goes away. The move is to make the cadence structurally
incompatible with it.

The five are: **planning theatre, PRD gestation, design-
debt-in-review, spec-then-hand-off, and the "agile"
waterfall**. Each maps to a Lecture 1–5 discipline, in
reverse: if you did the earlier lecture's job, the anti-
pattern doesn't get room to grow.

## Anti-pattern 1 — Planning theatre

**The shape.** The team holds regular planning meetings —
quarterly, monthly, sprint-boundary — that produce
elaborate artifacts (Jira epics, roadmap slides, capacity
plans, PI-planning boards) that nobody consults after the
meeting ends. The artifacts have a plausible surface
resemblance to real product decisions but are *decoupled*
from what actually ships. The team returns to the same
issues at the next planning meeting and re-decides them
without noticing.

**The diagnosis.** Planning theatre grows when the
*execution rhythm* (Lecture 2 — Shape Up cycles or weekly
kanban commits) either doesn't exist or has been
supplanted by planning meetings. The theatre exists because
somebody has to feel like they've decided something; the
alternative — actually running the operating model weekly —
requires accepting that most decisions are small and
frequent, not big and quarterly.

**What creates it.**

- No chosen delivery-track operating model (Lecture 2). If
  the team isn't running Shape Up or kanban with real
  discipline, planning meetings fill the vacuum.
- A CPO who confuses roadmap-authoring (mod-003) with
  operating-cadence-decision-making. The roadmap is the
  *strategy* the cadence executes; it is not the
  decisions.
- A "PI planning" or "quarterly planning" ritual inherited
  from a bigger-company past that never got questioned.
- Fear of small, frequent decisions — the CPO would rather
  make one big decision every quarter than 20 small ones
  every week.

**The designed-out counter-move.**

- **Pick the operating model (Lecture 2) and run it.** The
  Monday commit and Friday review (kanban) or the bet
  meeting and cool-down (Shape Up) are the *only* planning
  rituals. Everything else — roadmap review, strategy
  review, quarterly planning — is a *reading* meeting, not
  a *deciding* meeting.
- **Diagnostic rule.** If the same product decision has
  been "decided" in three consecutive planning meetings,
  it has not actually been decided; the operating model is
  missing.
- **Kill unused planning artifacts publicly.** If nobody
  has referred to the Q3 planning document since it was
  written, delete it in the Q4 planning meeting *before*
  starting the Q4 one. Making the disuse visible is what
  eventually convinces the team the theatre is theatre.

Reference: Basecamp's *Shape Up* argues directly against
the "sprint boundary as planning ritual" that Scrum shops
degrade into
([Singer, *Shape Up*, Chapter 1](https://basecamp.com/shapeup/1.1-chapter-01)).
Reinertsen's *Principles of Product Development Flow* is
the more general argument for why frequent-small commit
rituals dominate infrequent-large ones
([Reinertsen, *Principles*, Chapters 3 and 5](https://celeritaspublishing.com/product/the-principles-of-product-development-flow/)).

## Anti-pattern 2 — PRD gestation

**The shape.** The PRD gets started. It gets shared in draft.
Comments accumulate. The draft goes through five revisions.
Three weeks pass. When the PRD is "ready," the market has
moved, the discovery evidence is stale, and the engineering
capacity that was supposed to build the thing has been
pulled to something else. The team ships the PRD but not
the product.

**The diagnosis.** PRD gestation is what happens when the
PRD is treated as a *deliverable* rather than as *the
input to a decision*. Once the PRD is a deliverable, there
is a *quality gate* on it, and everybody with an opinion
becomes a gatekeeper. The document becomes a consensus
artifact rather than a decision artifact.

**What creates it.**

- The PRD template has 20+ sections, most of which the
  team doesn't have answers for; filling them all in takes
  weeks and produces speculation-shaped content.
- Comments are opened before the doc is coherent, sending
  the draft in ten directions.
- The reading ritual is "everybody reviews async" rather
  than "silent meeting reads together, then discusses" —
  which means asynchronous drift and no clean decision
  moment.
- The CPO uses PRD-writing as a substitute for discovery
  when they don't yet know what the bet is.

**The designed-out counter-move.**

- **Adopt the six-pager form (Lecture 3).** Six pages is a
  hard cap. The prose form makes half-answered questions
  visible; a 20-section template hides them.
- **Timebox the write.** Four hours to draft, one hour to
  read (silent-meeting), one hour to decide. If yours is
  taking three weeks, the doc is hiding a discovery
  problem; go back to Lecture 1 and run an interview.
- **Delay opening comments until the doc is readable.**
  The CPO drafts privately, then shares for the silent-
  meeting read; comments live in the meeting, not
  asynchronously on the doc.
- **The PRD is not the ship.** The next slice shipped is
  the deliverable. If the six-pager is "done" but no
  slice has shipped, the six-pager did not produce
  progress.

Reference: Bezos on the six-pager and silent-meeting
reading
([Bezos, 2004 Letter to
Shareholders](https://www.aboutamazon.com/news/company-news/2004-letter-to-shareholders));
Bryar & Carr on the anti-gestation discipline
([Bryar & Carr, *Working Backwards*, Chapter
4](https://www.workingbackwards.com/)).

## Anti-pattern 3 — Design-debt-in-review

**The shape.** The eng team implements a feature from a
Figma mockup (or, worse, from a text description). The
implemented version is shown to the CPO / designer for the
first time in a *code review* or a *staging demo*. The CPO
sees a dozen things that don't match the mockup, three
strings that were auto-generated, and an empty state that
was never designed. The list becomes "design debt" that
gets tracked in a separate backlog and never gets fixed —
because there is never a moment where fixing it is more
valuable than shipping the next thing.

**The diagnosis.** Design-debt-in-review is what happens
when the CPO / designer is not *in flight* with the engineer
during implementation. The mockup got tossed over a fence,
the engineer made the 100 micro-decisions the mockup
didn't specify, and the resulting product doesn't match the
CPO's intent — but by the time the CPO sees it, changing it
means asking the engineer to redo work they thought was
done.

**What creates it.**

- No paired review during implementation. The Figma is
  the last time the CPO / designer sees the surface until
  it's built.
- The design system is under-invested, so the engineer has
  to *invent* components mid-implementation, and the
  invented components don't match the CPO's aesthetic.
- The "own the pixel" discipline (Lecture 4) is not
  running — no mid-cycle design review, no pre-ship walk.
- The team treats the mockup as an *approximate*
  suggestion rather than as the *specification of the
  product surface*.

**The designed-out counter-move.**

- **Paired mid-cycle design review (Lecture 4).** The CPO,
  the designer, and the implementing engineer look at the
  staging surface together at least once between mockup
  and ship. Anything that surprises the CPO gets logged
  and fixed *before ship*, not after.
- **Pre-ship walk (Lecture 4).** The CPO clicks the
  deployed surface personally before the flag flips.
  Nothing ships past the walk in a broken state; the walk
  is where "we'll fix it later" gets converted into
  "we'll fix it now or defer the ship."
- **Microcopy pass (Lecture 4).** All user-facing strings
  are edited by the CPO before ship. No auto-generated
  strings ship.
- **Figma in components, not rectangles (Lecture 4).**
  The mockup uses the real components; the engineer
  doesn't have to invent anything to implement it.
- **Design debt as ship blocker, not backlog item.**
  A design mismatch found in review is a *slice failed
  to ship correctly* moment, not a *log it for later*
  moment. Fix it in this ship or delay the ship.

Reference: this is the pattern Cagan describes as the
*"why product teams miss the mark on quality"* failure
in *Empowered*
([Cagan & Jones, *Empowered*, Chapter
10](https://www.svpg.com/empowered-ordinary-people-extraordinary-products/));
also see Ryan Singer's "Hills" chapter in *Shape Up* for
the paired-in-flight review as the counter to end-of-cycle
surprise
([Singer, *Shape Up*, Chapter 12](https://basecamp.com/shapeup/3.4-chapter-13)).

## Anti-pattern 4 — Spec-then-hand-off

**The shape.** The CPO writes a detailed specification.
The specification is shared with the design team, which
takes two weeks to produce mockups. The mockups are shared
with the engineering team, which takes three weeks to
implement. Each hand-off is a *phase boundary* with a
review meeting. The dual-track discipline from Lecture 1
does not exist because there is no *trio*; there are three
sequential functions that hand documents to each other.

**The diagnosis.** Spec-then-hand-off is the shape a team
takes when it *organizes by function* rather than *by
trio*. It is the shape most people who came up in
big-company product orgs default to. It kills velocity for
three reasons: each hand-off adds a queue (Reinertsen's
Cost of Delay math from mod-002 Lecture 2), each hand-off
loses information (the eng team never talked to the
customer, so they can't make micro-decisions with the
customer's frame in mind), and each hand-off invites
politics (the reviewer's job is to catch the previous
function's mistakes, which turns every review into a
tribunal).

**What creates it.**

- Missing product trio (Lecture 1). PM, design, and eng
  are separate functions with separate leads and separate
  meetings.
- The CPO is functioning as a *specifier* rather than as
  a *trio member*.
- The design team is booked on multiple projects at once
  and cannot pair with a specific engineer for the
  duration of a bet.
- The engineering team is booked on multiple projects at
  once and cannot pair with a specific designer for the
  duration of a bet.

**The designed-out counter-move.**

- **Organize by trio, not by function (Lecture 1).** For
  any bet, name the specific PM (or CPO), designer (or
  CPO wearing that hat), and eng lead (or founding
  engineer) who own the bet together, for the duration.
  All three attend the Monday interview, the Thursday
  sync, and the pre-ship walk.
- **Refuse hand-off review meetings.** If a "design
  review" or "PRD sign-off" meeting exists as a separate
  ceremony from the trio's regular rhythm, kill it. The
  trio's Thursday sync is the review.
- **The six-pager is upstream, not downstream (Lecture
  3).** The six-pager is the *input to the trio*, not the
  *output of the CPO handed to design*. Draft it as a
  trio artifact; walk it as a trio.
- **CPO does not write specs.** The CPO writes six-
  pagers (Lecture 3) and Figma mockups (Lecture 4). The
  spec — if one exists at all — is authored by the trio
  together, or by the engineer, based on the six-pager
  and the mockup.

Reference: Cagan's *Empowered* Chapter 8 on the empowered
product team as the antidote to the functional-org shape
([Cagan & Jones, *Empowered*](https://www.svpg.com/empowered-ordinary-people-extraordinary-products/));
Torres's *Continuous Discovery Habits* on the product-trio
as the discovery unit
([Torres, Chapter 3: "Involve Your Product Trio"](https://www.producttalk.org/continuous-discovery-habits/)).

## Anti-pattern 5 — The "agile" waterfall

**The shape.** The team says it does agile. Sprints exist,
stand-ups happen, retros happen. But the *product-decision
shape* is waterfall: big-up-front discovery ("we'll do
research this month"), followed by big-up-front design
("designs will be ready by end of Q3"), followed by build
("we'll ship in Q4"). Sprints are used as execution
buckets, not as commitment mechanisms. Nothing ships until
the whole thing is done. Retros discuss what's blocking the
Q4 launch.

**The diagnosis.** The "agile" waterfall is what happens
when a team adopts the *ceremonies* of agile without the
*continuous-flow* premise underneath them. It is the
degenerate form of Scrum-at-startup-scale. Cagan calls it
*"faux agile"* in *Inspired* Chapter 8; it is the shape
Shape Up and weekly kanban both exist as alternatives to
([Cagan, *Inspired* (2nd ed.), Chapter
8](https://www.svpg.com/inspired-how-to-create-products-customers-love/)).

**What creates it.**

- Phase-shaped discovery (Lecture 1 not running).
- Phase-shaped design (spec-then-hand-off; anti-pattern 4).
- No chosen delivery operating model (anti-pattern 1
  variant).
- A "launch date" mindset — the belief that products get
  *launched* rather than *shipped continuously*.
- Pressure from the founder-CEO or the board to have a
  "big launch" that structures the year around one
  release.

**The designed-out counter-move.**

- **Dual-track discovery (Lecture 1).** Discovery is
  continuous, weekly, and by the trio; there is no
  discovery *phase*.
- **Shape Up or weekly kanban (Lecture 2).** The delivery
  track has a continuous-flow operating model; there is
  no "we'll ship in Q4" horizon that isn't broken into
  weekly-or-cycle-scale slices.
- **Live changelog (Lecture 4).** The changelog itself is
  a forcing function — you cannot maintain a live
  changelog if you are only shipping once a quarter.
- **Refuse "the launch."** If a big-launch date is being
  proposed, decompose it publicly into the continuous-
  ship slices that would get to it. Big launches are for
  marketing (owned by GTM at level 30); product ships
  continuously.
- **Cadence-DORA check.** Ask the CTO for the team's
  *deploy frequency* (a DORA metric, level-25). If it is
  less than weekly, the agile-waterfall pattern is
  probably present regardless of what the team says it
  does.

## What the CTO owns that the CPO consumes

The engineering-side of the cadence has its own
discipline, owned by the CTO / eng lead, that the CPO
depends on. This module treats those disciplines as
*consumed*, not authored. The key ones — all level-25 work
owned by
[cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum):

- **DORA metrics.** Deploy frequency, lead time for
  changes, change-failure rate, mean time to restore.
  Named in Forsgren, Humble & Kim's *Accelerate*
  ([IT Revolution, 2018](https://itrevolution.com/product/accelerate/))
  and maintained on the ongoing DORA program at
  [dora.dev](https://dora.dev/). The CPO consumes these
  as signals about whether the delivery cadence is
  actually delivering — a deploy-frequency of
  once-per-quarter tells you agile-waterfall is present
  even if the retro says otherwise. The CTO authors the
  pipeline and the measurement.
- **On-call rotation.** Who is paged when production
  breaks. The CPO depends on this existing (because
  without it, engineers burn out from unbounded off-hours
  interruption, and the delivery track collapses); the
  CTO authors the rotation, the paging tool
  configuration, and the runbook standards.
- **Incident response.** How incidents get triaged,
  fixed, and post-morteMed. The CPO participates in
  post-mortems where the *product* was implicated
  (a shipped feature caused the incident); the CTO owns
  the incident-management process and the SRE culture
  underneath it. Google's *SRE Book* is the canonical
  reference ([sre.google/sre-book](https://sre.google/sre-book/table-of-contents/));
  Charity Majors's *Observability Engineering* is the
  modern practitioner reference for the observability
  side ([O'Reilly, 2022](https://www.oreilly.com/library/view/observability-engineering/9781492076438/)).

For the CPO's cadence, the practical implication is that
you *ask for the numbers*, you *incorporate them into your
weekly rhythm* (deploy frequency in the Friday review,
change failure rate as a ship-quality signal), and you
*escalate* when the numbers indicate the delivery cadence
you designed isn't happening — but you do not author the
underlying SRE regime yourself.

## A diagnostic: what to look at

A founding CPO should be able to diagnose the presence of
each anti-pattern within one week of joining a team. The
five diagnostic reads:

- **Planning theatre.** Are the same decisions being
  re-discussed in successive planning meetings? Look at
  the last three planning artifacts and count the number
  of times the same topic recurs.
- **PRD gestation.** How long has the newest PRD been in
  draft? How many people are on the comment thread? Is
  it "ready to ship yet"? A PRD older than two weeks in
  active draft is a gestation.
- **Design-debt-in-review.** Ask to see the "design
  debt" or "polish backlog." If one exists and is long,
  design-debt-in-review is the pattern.
- **Spec-then-hand-off.** Does the team have "design
  review" and "PRD sign-off" meetings that are separate
  from the operating rhythm? Are design and eng booked on
  the same bet for the bet's duration, or are they
  time-sharing across three projects?
- **Agile waterfall.** What is the deploy frequency
  (DORA)? If it is less than weekly, and the team says
  "we ship every quarter," the pattern is present.

## The retro that actually works

Retrospectives are the ritual most likely to become
ceremonial themselves. A retro that lists "improvements"
that never get implemented is a retro that has become
theatre. Two disciplines make retros work at CPO scale:

- **Every retro finding becomes a change to the cadence.**
  Not a Jira ticket. Not a "we'll do better." A specific
  change to a specific ritual — the Monday interview
  moves to Tuesday, the Thursday sync gets 15 more
  minutes, the pre-ship walk becomes a hard gate. If a
  retro finding does not map to a cadence change, the
  finding is fluff.
- **The retro looks at the *cadence*, not the *sprint*.**
  Because the cadence is the thing that produced the
  outcome. A retro that focuses on "what went well in
  Sprint 47" misses the structural questions.

A monthly cadence retro (not per-sprint) with these two
disciplines does more than a weekly ceremonial one.

## Boundaries this lecture keeps

- **Dual-track cadence** — Lecture 1.
- **Delivery operating models** — Lecture 2.
- **PRD form** — Lecture 3.
- **Pixel and microcopy discipline** — Lecture 4.
- **Agentic-UX iteration loops** — Lecture 5.
- **DORA metrics, on-call, incident response** — level-25
  work owned by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum).
  The CPO consumes; the CTO authors.
- **Engineering-management discipline underneath the eng
  lead** — team topologies, hiring, performance — is
  also level-25 work owned by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum).
- **The founder-CEO relationship contract** that lets the
  CPO refuse "the big launch" — is
  [mod-007](../../mod-007-working-with-founders-eng-and-gtm/README.md).

## Takeaways

- Five ship-velocity anti-patterns to design *out* of the
  cadence: **planning theatre, PRD gestation, design-
  debt-in-review, spec-then-hand-off, the "agile"
  waterfall.**
- Each anti-pattern has a specific counter-move that is
  a Lecture 1–5 discipline enforced structurally, not a
  retro finding to try again.
- **Planning theatre** is what fills the vacuum left by
  no chosen operating model (Lecture 2). Fix by picking
  one and running it.
- **PRD gestation** is what happens when the PRD is a
  deliverable, not an input. Fix by adopting the
  six-pager form (Lecture 3), timeboxing the write, and
  making the ship — not the doc — the deliverable.
- **Design-debt-in-review** is what happens without paired
  in-flight review (Lecture 4). Fix by putting the CPO
  and designer in the mid-cycle review and treating
  design mismatch as a ship blocker, not a backlog item.
- **Spec-then-hand-off** is what a functional-org shape
  degrades into. Fix with the empowered product trio
  (Lecture 1) and the removal of hand-off review
  ceremonies.
- **The "agile" waterfall** is what happens when the
  team adopts ceremonies without continuous flow. Fix
  with dual-track discovery, a real delivery operating
  model, a live changelog, and a deploy-frequency check
  against the CTO's DORA numbers.
- **DORA metrics, on-call, and incident response** live
  at the level-25 boundary and are consumed by the CPO,
  authored by the CTO. Ask for the numbers; do not build
  the pipeline.
- Retros work only when every finding becomes a cadence
  change and the retro is monthly, cadence-scoped.

This closes the module. The exercises turn each lecture
into a concrete artifact against a real team; when you're
done, you have a cadence artifact you can walk into a
first-week founding-CPO job with.
