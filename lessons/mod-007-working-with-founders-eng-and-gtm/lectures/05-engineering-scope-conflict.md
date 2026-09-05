# Lecture 5 — Engineering scope conflict resolution

## The setup

The most common scope argument on a founding-team is
some version of: *"the engineers want to rewrite the
component; the PM wants to ship the next thing on
top of it."* It shows up on the payments module. It
shows up on the auth service. It shows up on the AI
orchestration layer within four months of first
shipping. It is *not* an unreasonable argument on
either side. The engineers are usually right that the
component has real debt that will eventually cost the
company. The PM is usually right that the roadmap
can't wait a quarter for a rewrite.

The founding-CPO failure is *resolving the argument
by authority* — "we're shipping the next thing,
because I said so" or "we're rewriting, because the
CTO said so." Both produce the same downstream
consequence: the losing side stops surfacing the
underlying evidence, the debate becomes political,
and the *next* scope dispute is harder because both
sides are now defending positions rather than
weighing costs.

The productive alternative is to resolve the argument
with *data*: the technical-debt cost-to-carry
evidence from [cto-curriculum mod-105](https://github.com/ai-startup-curriculum/cto-curriculum),
the roadmap opportunity cost from
[mod-002](../../mod-002-opportunity-assessment-and-prioritization/README.md),
the appetite discipline from [Ryan Singer's Shape
Up](https://basecamp.com/shapeup/1.2-chapter-03),
and a decision framework that names the four
possible moves and picks the one the evidence
supports. This lecture teaches that framework.

## The four possible moves

Every scope conflict of the "rewrite vs. ship" shape
resolves into one of four moves. Naming them
explicitly forces the conversation from *"rewrite or
ship?"* (a binary) to *"which of these four?"* (a
choice with evidence).

- **Rewrite.** Pause the roadmap on this surface,
  invest a bounded appetite in replacing the
  component or subsystem, resume roadmap work on
  top of the new version.
- **Refactor in place.** Keep shipping features on
  the current surface but budget a percentage of
  every sprint / cycle to incremental structural
  improvement. Fred Brooks called this pattern
  *"plan to throw one away — you will, anyhow"*
  when it works well; the modern variant is the
  incremental refactoring that avoids ever needing
  a rewrite.
- **Ship-and-fix-later.** Accept the current
  structure, ship the next features on top of it,
  explicitly schedule the fix for a specific later
  date with a specific trigger.
- **Kill.** The surface is not worth investing in
  at all. Deprecate the feature or remove it from
  the roadmap; the rewrite question becomes moot.

Each move is right in specific conditions and
wrong in others. The framework's value is that it
forces the conversation to name *which conditions
apply here*, rather than defaulting to whichever
side is more forceful in the meeting.

## When each move is right

### Rewrite is right when...

- **The component blocks a strategic bet** that
  can't be built on the current version. This is
  the strongest signal; the rewrite is *unblocking*,
  not just cleaning.
- **The cost-to-carry is measurably compounding.**
  Each new feature on top costs materially more
  than the last. This is a quantifiable claim (see
  the cost-to-carry section below), not a vibe.
- **The current version's on-call load is
  unsustainable.** The team spends more than ~20%
  of engineering time keeping the current version
  alive.
  <!-- needs-research: the 20% threshold is a common practitioner rule of thumb; verify against a specific source (Google SRE Book on toil budgets is a candidate) before quoting as authoritative. -->
- **The rewrite has a bounded appetite the team
  can commit to.** Six weeks, not "as long as it
  takes." An unbounded rewrite is the failure
  Brooks named the *second-system effect*.

### Refactor in place is right when...

- **The debt is real but not blocking.** Feature
  work is still possible on the current surface;
  it's just slower than it should be.
- **The team can define specific structural
  improvements** that pay down debt while
  shipping. Not "we'll be more disciplined"; a
  named refactor per sprint.
- **The roadmap can't afford a rewrite pause.**
  The strategic-bet queue has commitments the
  rewrite would jeopardize.
- **The current surface is *stable* structurally.**
  The problem is entropy inside a stable shape,
  not a fundamentally wrong shape.

### Ship-and-fix-later is right when...

- **The next feature is genuinely time-critical.**
  A launch date the company has committed to, a
  customer deal, a competitive window.
- **The fix is well-understood** and can be
  scheduled with confidence for a specific later
  time.
- **The scheduling trigger is real.** *"After the
  launch"* is a legitimate trigger only if the
  launch date is real and the after-work is on
  the calendar. *"When we have time"* is not a
  trigger.
- **The team accepts the debt they're incurring**
  explicitly, not silently. The engineer who
  said "this will hurt later" says it in the
  scope-conflict memo, not just in the sprint
  retrospective.

### Kill is right when...

- **The feature isn't hitting its outcome** and
  the mod-002 kill-list discipline says to
  remove it.
- **The customer segment served by the surface
  has moved.**
- **The maintenance cost exceeds the value
  produced** — the mod-002 Lecture 5 sunk-cost
  discipline applies.

Kill is under-considered. Most rewrite-vs-ship
conflicts assume the surface has to keep existing,
and skip the *"or we could just stop"* option.

## The evidence each move demands

The framework's value is that each move demands
specific evidence. If the evidence isn't available,
the move isn't yet supportable and the conversation
becomes *"what evidence do we need?"* rather than
*"who wins the argument?"*

### Evidence for a rewrite

- **Cost-to-carry data.** From the eng team, per
  [cto-curriculum mod-105](https://github.com/ai-startup-curriculum/cto-curriculum).
  The specific measurable claim: how much
  engineering time per week the current version
  costs to maintain, incidents attributable to
  it, features that took materially longer than
  they should have because of it. Numbers, not
  adjectives.
- **The blocking strategic bet.** Named from the
  mod-002 queue. Which roadmap item is blocked or
  materially harder because of the current
  version.
- **The bounded appetite.** Concrete: "six weeks
  for two engineers," "one quarter for the whole
  team." The eng lead commits to the appetite.
- **The out-condition.** What happens if the
  rewrite exceeds the appetite? Ryan Singer's
  *Shape Up* discipline —
  [basecamp.com/shapeup](https://basecamp.com/shapeup/4.5-chapter-14) —
  calls this the "circuit-breaker": at the end
  of the appetite, either the rewrite ships (and
  the team resumes roadmap on top of it) or the
  team stops and evaluates. Unbounded rewrites
  become the classic Netscape-6 shape.

### Evidence for refactor-in-place

- **The named structural improvements.** Specific
  changes with an estimated impact. "Extract this
  service into a separate module; simplifies X;
  saves Y hours per feature."
- **The refactor-percentage commitment.** How
  much of each sprint / cycle goes to the
  refactor. Typically 15–25% at pre-seed / seed
  scale; deeper if the debt is worse.
  <!-- needs-research: the 15–25% figure is a practitioner rule of thumb; verify against a specific source before citing as authoritative. -->
- **The measurable improvement over time.** Is
  the refactor working? Cost-to-carry going
  down? Feature-cycle time going down? A
  refactor-in-place approach that isn't
  measurable is a refactor-in-place approach
  that will be quietly abandoned.

### Evidence for ship-and-fix-later

- **The real time constraint.** The launch date,
  the customer commitment, the competitive
  window. Named, dated, and testable.
- **The named fix.** What specifically will be
  fixed later, by whom, when. The specificity
  matters — "we'll fix the auth module" is not
  a fix; "we'll extract the session-management
  logic into a separate service by [date],
  owned by [engineer]" is.
- **The debt acknowledgement.** Written, not
  verbal. In the scope-conflict memo. The
  engineer who said the ship-and-fix-later is
  bad practice says it in writing.

### Evidence for kill

- **The feature-usage data.** Nobody using it,
  or the customer segment served has moved.
- **The customer-notification story.** How you
  tell existing users the feature is going
  away.
- **The maintenance-cost savings.** Confirmed
  saving from removing the surface entirely.

## Cost-to-carry as the load-bearing evidence

For rewrite-vs-ship specifically, the load-bearing
evidence is the *cost-to-carry* of the current
component. This is a term the CTO curriculum
formalizes (mod-105 is the depth reference); the
CPO-side reading is:

- **Direct cost.** Engineering time per week spent
  keeping the component running — incidents,
  bug-fix backlog, integration breakage. Measurable
  in engineer-hours per week.
- **Marginal cost.** How much *more* each new
  feature on top costs compared to a hypothetical
  clean version. Harder to measure but visible in
  cycle-time trends — the last five features on
  this surface took how much longer than the
  five before.
- **Risk cost.** Incidents, security exposure,
  compliance risk attributable to the current
  structure. Priced against the outage / breach
  cost the company would bear.
- **Opportunity cost.** Roadmap items that can't
  be built on the current version. The mod-002
  queue-competition framing applies.

A rewrite is right when *"annualized cost-to-
carry > cost of rewrite (including opportunity
cost of the eng team's time during the rewrite),
inside the appetite the team can commit to."*
That framing is quantitative in principle even if
the numbers have wide error bars. Wide error bars
are fine; **no numbers at all** is the failure to
avoid.

## The scope-conflict resolution memo

When a rewrite-vs-ship dispute surfaces, the
founding-CPO discipline is to *make it written*.
The scope-conflict resolution memo has a specific
shape, one to two pages:

- **The surface at issue.** Which component or
  subsystem, in one paragraph.
- **The eng position.** What the eng team wants
  to do (typically rewrite or refactor), the
  cost-to-carry evidence backing it, and the
  bounded appetite they'd commit to.
- **The product position.** What the CPO wants
  to do (typically ship next), the roadmap
  commitment or opportunity backing it, and the
  cost of pausing on this surface.
- **The four moves considered.** Named, each
  with a one-paragraph evaluation.
- **The recommended move.** With a paragraph on
  why the evidence supports it.
- **The out-condition.** What triggers a re-
  visit. If we chose rewrite, what happens if
  the appetite is exceeded; if we chose ship-
  and-fix-later, what specifically will be
  fixed by when.
- **The specific commitment.** Named engineer,
  named PM, named date, named artifact.

The memo goes to the CEO for visibility (per
Lecture 1's decision-rights map — this is
typically a consensus decision between the CPO
and the eng lead / CTO). If the CPO and eng lead
disagree on the recommended move, the memo goes
to the CEO as a tie-breaker per Lecture 1.

## The Shape Up circuit-breaker

For any of the four moves that requires a bounded
investment — most obviously the rewrite, but also
serious refactor-in-place work — the *appetite*
discipline from Ryan Singer's *Shape Up*
([basecamp.com/shapeup/1.2-chapter-03](https://basecamp.com/shapeup/1.2-chapter-03))
is the load-bearing enforcement mechanism.

The pattern:

- Before the work starts, the CPO and eng lead
  agree on an appetite: *"two weeks," "six
  weeks."*
- The eng team decides what fits inside the
  appetite (Shape Up's "shaping" work).
- At the appetite's end, one of three things
  happens:
  - **The work ships.** Roadmap resumes on top
    of the new version.
  - **The work is close.** A short extension
    (25% of the original appetite, no more)
    lands it.
  - **The work is not close.** The team stops.
    Not the failure mode — the *design*. A
    stopped rewrite that produced learning is
    a better outcome than a rewrite that
    consumed six months and produced Netscape 6.

The circuit-breaker is what makes rewrites
*safe*. Without it, the rewrite conversation is
"pause the roadmap indefinitely," which is
correctly a scary ask; with it, the ask is "pause
the roadmap for six weeks and re-evaluate."
That is a much more supportable ask.

## Common failure modes

Six failure modes that recur across founding-CPO
rewrite-vs-ship conflicts:

- **Authority resolution.** The CPO or the CTO
  wins by rank. The losing side stops
  surfacing evidence, and every subsequent
  scope conflict is more political.
- **Unbounded rewrite.** The team commits to a
  rewrite without an appetite. Six months in,
  the rewrite is 60% done, the roadmap has
  slipped, and nobody wants to be the one who
  says stop.
- **Silent debt acceptance.** The team ships-
  and-fixes-later without writing down the
  debt or scheduling the fix. Two years later,
  the debt has compounded and the fix is now
  a rewrite.
- **Kill-as-taboo.** The team never considers
  the kill option because the feature has
  customers, even if the customer count is
  small enough that the maintenance cost
  exceeds the value.
- **Refactor-in-place-as-slogan.** The team
  commits to "refactoring as we go" without
  naming specific structural improvements or
  a percentage commitment. Predictably, no
  refactor happens.
- **Second-system syndrome** (Brooks). The
  rewrite becomes a bigger and more ambitious
  system than the one being replaced. It
  ships years late and is worse than the
  original. Prevented by the appetite +
  circuit-breaker discipline.

## Where the CPO defers

- **The engineering trade-offs inside the
  rewrite** — architecture, service boundaries,
  data-model choice — are the CTO's. The CPO
  reads the ADR per Lecture 2 and asks the
  product-implication questions; the CPO does
  not choose the service boundaries.
- **The cost-to-carry measurement methodology**
  — how the eng team measures maintenance
  hours, how they attribute incidents, how
  they compute cycle-time trends — is
  [cto-curriculum mod-105](https://github.com/ai-startup-curriculum/cto-curriculum)
  depth. The CPO consumes the numbers.
- **The refactor plan itself** — what
  specifically gets extracted, how the tests
  get restructured — is the eng team's. The
  CPO consumes the plan and holds it against
  the commitment.

## What the CPO does personally

- **Convenes the scope-conflict memo.** The CPO
  is usually the party with visibility across
  both the eng position and the roadmap
  position; the CPO drives the memo.
- **Names the four moves.** Rewrite, refactor-
  in-place, ship-and-fix-later, kill.
  Explicitly. Even if one is obviously wrong.
- **Requires the cost-to-carry evidence.** No
  numbers, no rewrite. This is not
  bureaucracy; it is the discipline that
  produces good rewrite decisions.
- **Enforces the appetite / circuit-breaker.**
  When the appetite is exceeded, the CPO is
  the one who names the stop.
- **Logs the outcome.** Every scope-conflict
  resolution goes into a shared log; the
  next dispute references the last one.

## What the CPO consumes from the CTO / eng lead

- **The cost-to-carry numbers** per
  [cto-curriculum mod-105](https://github.com/ai-startup-curriculum/cto-curriculum).
- **The bounded appetite estimate** for the
  rewrite or refactor.
- **The named structural improvements** for
  refactor-in-place.
- **The named fix** for ship-and-fix-later
  cases.
- **The named engineer** committing to the
  work.

## Boundaries this lecture keeps

- **Architecture and technical debt at CTO
  depth** — measurement methodology, refactor
  strategy, service extraction, data-model
  migration — is
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum),
  particularly mod-102 (Architecture Under
  Uncertainty) and mod-105 (Debt and Refactoring).
  This lecture consumes the numbers; it does
  not produce them.
- **Prioritization at CPO depth** — RICE,
  WSJF, opportunity assessment — is
  [mod-002](../../mod-002-opportunity-assessment-and-prioritization/README.md).
  Rewrites compete for cycles on the queue
  the same way any bet does.
- **Roadmap authoring** — how the strategic
  bet queue gets built — is
  [mod-003](../../mod-003-roadmap-outcomes-and-strategy/README.md).
- **The CPO / CEO tie-breaker discipline** for
  when the CPO and eng lead disagree and
  can't resolve — is
  [Lecture 1](01-cpo-ceo-working-relationship.md#artifact-3--the-tie-breaker).
- **The "let me try to convince you" script**
  for the interpersonal side of the
  conversation is
  [Lecture 4](04-influence-without-authority.md#the-let-me-try-to-convince-you-script).

## Takeaways

- **Rewrite-vs-ship arguments resolve into four
  moves**: rewrite, refactor-in-place, ship-
  and-fix-later, kill. Naming them forces the
  choice off *"binary"* and onto *"which
  evidence supports which."*
- **Each move demands specific evidence.** No
  evidence, no move. The scope-conflict memo
  is written; the numbers come from cto-
  curriculum mod-105.
- **Cost-to-carry** is the load-bearing evidence
  for a rewrite. Direct cost, marginal cost,
  risk cost, opportunity cost — quantified
  even if the error bars are wide.
- **The Shape Up appetite and circuit-breaker**
  make rewrites safe. Six weeks, not "as long
  as it takes." At the end, ship or stop —
  the stop is a design, not a failure.
- **Ship-and-fix-later needs the named fix in
  writing** with the trigger and the owner.
  Otherwise it is silent debt acceptance.
- **Kill is under-considered** and should be
  named explicitly in every scope-conflict
  memo, even when it's obviously the wrong
  answer.
- **Do not resolve by authority.** The losing
  side stops surfacing evidence and every
  future scope conflict is more political.

Lecture 6 turns to **GTM launch readiness
coordination** — the founding-PM version of
the go / no-go, the readiness checklist, and
the escalation-to-not-shipping discipline.
