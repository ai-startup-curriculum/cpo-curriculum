# Lecture 4 — Influence without authority

## The setup

The founding CPO leads sales, customer success,
marketing, and design cross-functionally without any
of them reporting to them. There is no HR authority,
no comp lever, no formal escalation ladder. Everything
gets done through *influence*: shared evidence, written
pre-alignment, the mutual-benefit case, and the
occasional legitimate escalation to the CEO when the
influence doesn't land. The Solidroad / Column-Tax /
AngelList-shaped posting the 2026 market produces
assumes this shape by default.

Ask a first-time founding CPO what surprised them about
the role, and *"how much of the job is negotiation
with people I don't manage"* is at or near the top of
every list. The instinct — especially for CPOs who
came up in mature orgs where the director-of-X
counterparts had the same reporting distance — is to
either lean on the CEO for authority ("the CEO says
we're doing this") or to over-document ("here is a
40-page RACI"). Neither works. The first burns
relationship capital with the CEO on every dispute
and quickly produces the *"the CPO can't influence
anyone"* pattern. The second produces a governance
document nobody reads and no behavior change.

What works is a small set of *disciplines* that make
cross-functional alignment structural: Cagan's
*empowered product teams* as the operating shape, a
written pre-alignment pattern that surfaces
disagreements early, a "let me try to convince you"
script that engages counterparts on merit, and a
handful of specific anti-patterns to design out of
the way you work. This lecture teaches each.

## The empowered-product-team operating shape

Marty Cagan's *Empowered: Ordinary People,
Extraordinary Products* — Wiley, 2020, particularly
Chapters 8–10 on *product teams*, coaching, and
staffing —
[svpg.com/empowered](https://www.svpg.com/empowered-ordinary-people-extraordinary-products/)
— is the founding-CPO operating reference. The two
load-bearing distinctions:

- **Feature teams vs. product teams.** A *feature
  team* is given features to build. A *product
  team* is given *problems to solve* and has the
  autonomy to decide how. Cagan is emphatic that
  the empowered-product-team shape is the only
  shape that produces both engagement and
  outcomes; feature-team shapes reliably fail on
  both dimensions.
- **Product leadership as coaching, not
  directing.** The CPO's job with the trio (PM,
  designer, tech lead) and with cross-functional
  counterparts is coaching — asking questions
  that help the counterpart arrive at the right
  answer — rather than directing. This is the
  discipline that scales; direct answers do not.

For a founding CPO, the empowered-team shape has
three implications for the cross-functional seams:

- **Cross-functional counterparts have latitude
  inside their outcomes.** The head of sales
  decides how to run the sales cycle. The head
  of CS decides how to structure onboarding
  calls. The head of design (if it exists;
  otherwise the CPO wearing that hat) decides
  the design-system shape. The CPO negotiates
  the *outcomes* those counterparts commit to,
  not the *how*.
- **Disagreements are on outcomes, not on
  tactics.** *"Why did you send that email?"*
  is a bad conversation. *"The email produced
  this specific outcome I need us to fix"* is a
  good one. Empowered teams get the how; the
  seam is on the what.
- **The CPO models the coaching stance.** If the
  CPO's default mode with the eng team is
  directing, the CPO cannot expect a coaching
  stance from the CEO. Behavior at every seam
  travels; the CPO's mode with counterparts is
  what they will get in return.

Empowered-product-team craft is Cagan's whole
canon; this module borrows the vocabulary and the
operating shape but does not re-teach the craft
end-to-end. Read *Empowered* if you haven't, and
*Inspired* if you haven't.

## Written pre-alignment — the single most under-adopted discipline

Almost every cross-functional dispute the founding
CPO gets pulled into is *someone else's decision*
that the CPO didn't hear about until it was made.
Sales sold a custom SLA the product can't meet. CS
committed to a training program the roadmap didn't
know about. Marketing scheduled a launch date the
eng team hasn't seen. Design shipped a change to
the design system that broke three shipped
features.

The counter-move is **written pre-alignment**: a
convention that before any counterpart makes a
decision that touches product, they run a short
written note past the CPO for input before the
decision is final. Not for approval; for input.
The pattern:

- The counterpart writes a short note: *"I'm
  thinking about X, driven by Y evidence, with
  Z expected outcome. Anything I should know?"*
- The CPO reads it, replies within an agreed SLA
  (24 hours works for most; some decisions need
  faster).
- The counterpart decides.
- The decision, and the CPO's input, are logged
  in a shared place.

Two commitments make this stick:

- **Reciprocity.** The CPO does the same in the
  other direction. Every product decision that
  materially affects sales, CS, marketing, or
  design goes past the counterpart the same way.
  Written pre-alignment fails immediately if it
  is asymmetric.
- **Fast turnaround from the CPO.** If the CPO
  routinely takes a week to reply, counterparts
  will stop sending notes and revert to
  deciding without input. The written pre-
  alignment SLA is the load-bearing constraint;
  the CPO's calendar has to accommodate it.

The pattern is not RACI. RACI is a static role
matrix; written pre-alignment is a *behavior*
around specific decisions. The two can coexist —
a RACI matrix names who owns what, and written
pre-alignment names how "input" actually happens.
For most founding-team companies, written pre-
alignment is enough on its own.

### Where the pre-alignment note goes

The pattern only works if the note lands somewhere
the counterpart will actually see. Two workable
homes:

- **A shared Slack channel** for cross-functional
  pre-alignment. The note is a thread starter;
  replies are the input. Search-friendly, low-
  friction, hard to lose.
- **A running shared document** (Notion, Google
  Doc, Coda). Every note gets a section with a
  date; CPO's input goes under the note.
  Higher-signal than Slack but higher-friction.

The specific tool matters less than the
consistency. The failure mode is *"send it to
whichever tool the counterpart happens to use
today"* — which usually means the CPO doesn't see
it in time.

## The "let me try to convince you" script

When a counterpart proposes something the CPO
disagrees with, the reflex — especially under
time pressure — is to escalate to the CEO or to
just *say no*. Both are influence-destroyers.
Escalation reads as "the CPO can't make the case
themselves"; saying no reads as "the CPO uses
authority they don't have."

The productive alternative is a specific
conversational move: *"Let me try to convince
you"* — a short, explicit ask to make the case
on merit, with a time budget and an out.

The four-step script:

1. **Name the disagreement.** *"I disagree with
   [X]. Can I have 15 minutes to make the case?
   If I don't convince you, we go with your
   call."* The time-boxing and the out are load-
   bearing; without them the ask reads as
   "let me lobby you until you give in."
2. **Make the case with the shared vocabulary
   you both accept.** Discovery evidence,
   metrics from mod-005, cost / latency from
   the AI system, engineering estimates, GTM
   pipeline data. Land the case in the
   counterpart's *own vocabulary*, not yours.
3. **Ask the counterpart to name the specific
   piece they disagree with.** If they can name
   it, the conversation is now productive. If
   they can't — if they're at "I just don't
   think this is right" — the disagreement is
   at a lower level (trust, prior evidence, or
   a specific past experience they haven't
   surfaced) and the productive move is to
   surface it, not to press the case.
4. **Accept the outcome.** If the counterpart
   moves, the disagreement is resolved. If they
   don't, you go with their call *and mean it*.
   The influence capital comes from the *and
   mean it*.

This script produces two effects that compound.
First, over time, counterparts learn that the CPO
is worth listening to because the CPO shows up
with a real case rather than authority. Second,
the CPO's escalations to the CEO get taken more
seriously when they happen, because they happen
rarely and with a paper trail of prior attempts
that didn't resolve.

## The mutual-benefit case

Every cross-functional counterpart has their own
outcome to hit. The head of sales has a quota.
The head of CS has an NRR target. The head of
marketing has a pipeline number. The eng team
has a velocity commitment. When the CPO wants
something from a counterpart, the case that
lands is the one that shows how the ask
*helps the counterpart hit their outcome*, not
the one that shows how it helps the product.

Concrete examples:

- **Asking sales to slow down a custom-deal
  commitment.** Wrong case: "This will strain
  engineering." Right case: "This deal commits
  us to an SLA we won't meet in Q2, which will
  produce a churn event that hurts your net
  retention. Let's structure the deal with a
  phased SLA instead."
- **Asking CS to lead with the new packaging.**
  Wrong case: "This is where the product is
  going." Right case: "The new packaging
  produces a 20% higher NRR in the cohort we've
  tested, which hits your NRR target with less
  effort."
- **Asking marketing to hold a launch.** Wrong
  case: "The product isn't ready." Right case:
  "Shipping the launch now with these open bugs
  will produce a support incident on day three
  that hurts the launch narrative — let's ship
  in two weeks with the fixes and use the two
  weeks to build a stronger customer story."
- **Asking engineering to take on a debt
  cleanup.** Wrong case: "The codebase is
  gross." Right case: "This debt is costing us
  X hours a week in incident response, which is
  Y engineers-worth of capacity we could spend
  on the roadmap. See
  [Lecture 5](05-engineering-scope-conflict.md)."

The mutual-benefit case is not manipulation. It
is genuine empathy for the counterpart's
outcome, combined with the CPO's information
advantage on how the product affects that
outcome. When it isn't genuine — when the CPO
frames a mutual-benefit case that isn't actually
in the counterpart's interest — the trust burns
fast and doesn't come back.

## The counterpart briefings

A specific piece of influence craft: the CPO holds
a short recurring briefing with each cross-
functional counterpart. Not a decision meeting;
a *shared-state* meeting where the CPO gives the
counterpart a preview of what's coming and hears
what the counterpart is seeing that the CPO
should know.

Recommended cadence:

- **Head of sales / GTM lead**: weekly, 30 min.
  The CPO shares what's shipping in the next
  two weeks and what's in flight for the next
  quarter. Sales shares deal-level context and
  the specific asks coming from prospects.
- **Head of CS / support lead**: weekly, 30 min.
  The CPO shares what's shipping. CS shares
  the top support tickets, the churn indicators,
  and the account-health signals.
- **Head of marketing**: biweekly, 30 min. The
  CPO shares upcoming launches and positioning
  shifts. Marketing shares campaign performance
  and messaging tests.
- **Head of design (if a distinct role)**:
  weekly, 60 min. This overlaps with the
  mod-004 trio cadence when the CPO / designer /
  tech lead form the trio.

These briefings replace most of the ad-hoc "hey,
did you know…?" Slack traffic. They also produce
the trust capital that lets the "let me try to
convince you" script land — you have a working
relationship because you talk every week, not
because you talk when there's a conflict.

## The escalation-to-CEO test

Escalation to the CEO is a legitimate tool. It is
also expensive: it uses relationship capital with
the CEO (who is being asked to spend attention on
a resolvable dispute), it uses influence capital
with the counterpart (who now knows the CPO
brought the CEO in), and it damages the "the CPO
runs product cross-functionally" credibility if
it happens often. Two rules:

- **Try the four influence moves first.** Written
  pre-alignment, "let me try to convince you,"
  mutual-benefit case, briefings. If none of
  those resolved the dispute, escalation is
  legitimate.
- **Escalate the decision, not the person.** The
  frame is *"we need the CEO to make this call
  because we disagree and we've each made our
  case,"* not *"the head of sales is being
  unreasonable."* The person frame damages the
  counterpart relationship irreversibly; the
  decision frame does not.

The escalation is Lecture 1's tie-breaker
memo pattern applied to a cross-functional
dispute: a one-page note with the disagreement,
both proposed answers, the evidence on each
side, and a request for a decision. The CEO
decides; both parties commit; the log is
maintained.

## Common anti-patterns

Six patterns that produce more damage than they
prevent. Design each one *out* of the way you
work.

- **Escalation-as-influence.** The CPO
  routinely pulls the CEO in to settle small
  disputes. The counterparts learn to skip the
  CPO and go straight to the CEO; the CPO's
  influence collapses. Fix: the four influence
  moves; escalation only after all four have
  failed.
- **Parallel lobbying.** The CPO privately
  works multiple counterparts against each
  other to get to an outcome. When it comes to
  light — it does — the CPO's trust is
  irreparable. Fix: written pre-alignment (in
  the open) instead of parallel private
  conversations.
- **Silent RACI overrides.** The counterpart
  makes a decision on their surface, the CPO
  reverses it without telling them, and the
  team gets two versions. Fix: if the CPO
  disagrees, the "let me try to convince you"
  script; if the disagreement is at a
  decision-rights level, Lecture 1's escalation
  path.
- **Authority-borrowing.** The CPO uses "the
  CEO thinks…" or "the board wants…" to argue
  a case. Every use burns credibility whether
  the invocation is true or not. Fix: make the
  case on merit; save the CEO's actual
  authority for the actual escalation.
- **Consensus-seeking.** The CPO calls a
  meeting of five counterparts to "align" on
  a decision the CPO could and should make
  unilaterally. Every attendee spends an hour;
  the decision-rights map (Lecture 1) is
  ignored; the CPO looks indecisive. Fix:
  decide, and inform.
- **Withdrawal.** The CPO stops proposing
  things because "nobody listens anyway."
  Influence craft is a muscle; withdrawing
  atrophies it. Fix: keep making the case,
  keep writing the pre-alignment notes, even
  when it's discouraging.

## What the CPO does personally

- **Runs the counterpart briefings** on the
  weekly / biweekly cadence.
- **Writes the pre-alignment notes** for every
  product decision that touches another
  function.
- **Uses the "let me try to convince you"
  script** rather than escalating on first
  disagreement.
- **Builds the mutual-benefit case** in the
  counterpart's own vocabulary.
- **Escalates rarely, with a paper trail**,
  and only after the four influence moves have
  failed.
- **Models the coaching stance** the empowered-
  team shape requires.

## What the CPO consumes from counterparts

- **Deal-level context and prospect asks** from
  sales.
- **Support tickets, churn indicators, account
  health** from CS.
- **Campaign performance and messaging tests**
  from marketing.
- **Design-system state and constraints** from
  design.
- **Pre-alignment notes on decisions that
  affect product** from every counterpart, on
  the same reciprocal basis the CPO offers.

## Boundaries this lecture keeps

- **Base enterprise-selling motion** — sales
  stages, discovery calls, MEDDIC, deal desk,
  discounting mechanics — is
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum)
  (level 30). This lecture teaches the *seam
  with sales*; it does not teach how sales
  runs.
- **CS operating model** — onboarding
  playbooks, health scoring, expansion
  motions — is also level-30 GTM craft. The
  CPO consumes the health signals; the head
  of CS runs the motion.
- **Marketing operating model** — SEO,
  content, paid, positioning execution — is
  level-30 GTM craft. The CPO gives marketing
  the positioning input and consumes the
  performance data.
- **Empowered-team leadership at depth** —
  hiring, coaching, product-team staffing,
  performance management — is Cagan's own
  material (*Empowered* chapters 8–15) and
  level-50
  [startup-operations-governance-curriculum](https://github.com/ai-startup-curriculum/startup-operations-governance-curriculum).
  This lecture uses the operating shape; it
  does not teach the people-leadership craft.
- **Personnel management** — direct reports on
  the product team, performance reviews, comp
  decisions — is level-50 people-ops.
- **The CPO / CEO working relationship** is
  [Lecture 1](01-cpo-ceo-working-relationship.md).
  This lecture is the *cross-functional-peer*
  seam; Lecture 1 is the *founder-partner*
  seam.

## Takeaways

- **Cagan's empowered-product-team shape** is
  the operating reference. Counterparts have
  latitude inside their outcomes; disputes are
  on outcomes, not tactics; the CPO models the
  coaching stance.
- **Written pre-alignment** — a short
  reciprocal note before decisions that touch
  each other's surface — is the single most
  under-adopted cross-functional discipline.
  Fast turnaround from the CPO is the load-
  bearing constraint.
- **The "let me try to convince you" script**
  makes disagreements productive: name the
  disagreement, time-box the case, make the
  case in shared vocabulary, ask what
  specifically they disagree with, accept the
  outcome.
- **The mutual-benefit case** frames every
  cross-functional ask in the counterpart's
  own outcome vocabulary. Not manipulation;
  genuine empathy plus the CPO's information
  advantage.
- **Weekly / biweekly counterpart briefings**
  build the trust capital every other move
  spends.
- **Escalation to the CEO** is legitimate but
  expensive. Try the four influence moves
  first; escalate the decision, not the
  person; do it rarely with a paper trail.
- **Six anti-patterns to design out**:
  escalation-as-influence, parallel lobbying,
  silent RACI overrides, authority-borrowing,
  consensus-seeking, withdrawal.

Lecture 5 turns to the **engineering scope
conflict** — the "rewrite vs. ship" argument
resolved with data (technical-debt cost-to-
carry from cto-curriculum mod-105) rather than
authority.
