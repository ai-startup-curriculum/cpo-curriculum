# Lecture 5 — Killing work you already started

## The setup

The ruthless-prioritization writing you'll find online is almost entirely
about *starting* the right thing: better scoring schemes, tighter
opportunity assessments, cleaner allocations. That's the easy half. The
harder half — and the one where founding CPOs are graded — is *stopping*
work already underway that is no longer the right thing. This lecture is
about the second half: the biases that make killing hard, the mechanisms
that make killing cheap, and the CPO's specific job in the ritual.

The stakes are not abstract. Every quarter you leave a stalled project
running, you are also *not* funding the strategic bet that would have
displaced it. Un-killed work is opportunity cost with an owner attached.

## The four biases you are actually fighting

The failure to kill is not laziness. It is a bundle of cognitive and
social biases, each with a long research history and each with a
specific counter-move.

### Bias 1 — Sunk-cost fallacy

The already-spent cost of a project is irrelevant to whether it's
worth spending the next dollar on. Humans nevertheless weight the sunk
cost — the more we've spent, the more we insist on continuing, and the
worse the marginal decisions become as a result. Richard Thaler
formalized this as a persistent violation of normative choice theory
([Thaler, "Toward a Positive Theory of Consumer Choice," *Journal of
Economic Behavior & Organization*, Vol. 1, Issue 1, March 1980, pp.
39–60](https://www.sciencedirect.com/science/article/abs/pii/0167268180900517);
[Arkes & Blumer, "The Psychology of Sunk Cost," *Organizational
Behavior and Human Decision Processes*, Vol. 35, No. 1, February 1985,
pp. 124–140](https://msu.edu/~ema/803/Ch11-Uncertainty/2/ArkesBlumer85.pdf)).

**In product management this looks like:** *"We've already sunk two
quarters into this platform — we can't kill it now."* The correct answer
is that two quarters gone are two quarters gone; what matters is whether
the *next* quarter is better spent here or elsewhere. If the answer is
elsewhere, kill it, book the loss, and move on.

**Counter-move.** Force decisions to compare *marginal* remaining spend
against alternatives, in writing. "If I hadn't already started this,
would I start it now knowing what I know?" is Charlie Munger's
formulation of the same test
([Munger, "The Psychology of Human Misjudgment," Harvard Law School
speech, 1995 — transcribed at fs.blog](https://fs.blog/great-talks/psychology-human-misjudgment/)).

### Bias 2 — Endowment effect

Once you own something — a codebase, a feature, a strategic bet — you
value it more than an equivalent thing you don't own. Kahneman, Knetsch
and Thaler's coffee-mug experiments demonstrated the pattern
experimentally
([Kahneman, Knetsch & Thaler, "Experimental Tests of the Endowment
Effect and the Coase Theorem," *Journal of Political Economy*, Vol. 98,
No. 6, December 1990, pp. 1325–1348](https://www.jstor.org/stable/2937761)).

**In product management this looks like:** two similar-looking
opportunities score identically on RICE, but the one you already own
somehow "clearly matters more." It doesn't; you're pricing it above the
equivalent stranger version because it is yours. This is why *outside
review* is a core kill mechanism.

**Counter-move.** Rotate a peer PM or the CPO into a fresh-eyes review
of the surface. The rule: they read the opportunity assessment and the
recent metrics *first*, form a call, then hear the owner's defense.
Order matters — hearing the defense first anchors them.

### Bias 3 — Consistency / commitment

Once you have publicly committed to a course of action, you are
disproportionately reluctant to reverse it, even when new information
warrants reversal. Robert Cialdini's *Influence* names this the
commitment-and-consistency principle
([Cialdini, *Influence: The Psychology of Persuasion*, Harper Business,
revised edition 2006, Chapter 3, "Commitment and
Consistency"](https://www.influenceatwork.com/)). The larger and more
public the commitment (a board deck, a hiring plan, a customer promise),
the stronger the pull to keep going.

Related and more specific: Barry Staw's *escalation of commitment* — the
tendency for people responsible for a failing course of action to
increase resource commitment to it rather than cut losses
([Staw, "Knee-Deep in the Big Muddy: A Study of Escalating Commitment
to a Chosen Course of Action," *Organizational Behavior and Human
Performance*, Vol. 16, No. 1, June 1976, pp. 27–44](https://www.sciencedirect.com/science/article/abs/pii/003050737690005U)).

**In product management this looks like:** a bet you presented to the
board as a headline of the next 12 months is now visibly not working,
and every quarter the pitch to keep going gets more elaborate.

**Counter-move.** Pre-commit to the kill criteria *at fund time* and
put them in the same board deck that announces the bet. A pre-registered
kill threshold is a much smaller consistency cost to honour than a
fresh reversal; you're being consistent with the *conditional* you
already committed to.

### Bias 4 — Loss aversion

Losses hurt roughly twice as much as equivalent gains feel good.
Prospect theory made this quantitative
([Kahneman & Tversky, "Prospect Theory: An Analysis of Decision under
Risk," *Econometrica*, Vol. 47, No. 2, March 1979, pp. 263–291 — SSRN
mirror](https://www.jstor.org/stable/1914185)).

**In product management this looks like:** the *loss* of killing a
project (visible reversal, team disappointment, sunk work) looms much
larger than the equivalent *gain* of freeing that capacity for the next
opportunity (invisible until the next opportunity ships). The
asymmetry is systematic, not personal.

**Counter-move.** Make the alternative *visible* at the kill review.
Don't ask "should we stop project X?" Ask "should we stop project X to
fund project Y, given X's current trajectory and Y's expected impact?"
Framing the kill as a *swap* engages loss aversion on both sides — you
also lose Y by not funding it — instead of only on the kill side.

## The kill list, as a governance artifact

Jim Collins's *Good to Great* is where the "stop-doing list" as a
management ritual gets a name; Collins argues that the most successful
executives he studied maintained a stop-doing list with the same rigor
as their to-do list
([Collins, *Good to Great*, HarperBusiness, 2001, Chapter 6, "A Culture
of Discipline," on the stop-doing list](https://www.jimcollins.com/books/good-to-great.html);
[Collins, "Best New Year's Resolution? A 'Stop Doing' List," 2003 —
jimcollins.com/article_topics/articles/best-new-years.html](https://www.jimcollins.com/article_topics/articles/best-new-years.html)).

For a founding CPO, the operational form is a written **kill list**
published alongside the roadmap, with these fields per item:

- **What we're killing.** Feature, opportunity, or whole surface.
- **Why we're killing.** Which pre-registered kill criterion tripped, or
  which new information changed the case.
- **Sunk cost.** Person-weeks spent to date. Named, not to shame, but to
  refuse to hide.
- **What frees up.** Team members, engineering capacity, oncall load,
  design load. Named specifically.
- **What we're funding instead.** The opportunity moving up the queue
  as a result. Not "we'll figure it out later" — the swap is the point.
- **Who signs off.** Usually CPO + surface owner + one peer reviewer.
- **What we're keeping.** The parts of the work worth preserving — a
  library, a data set, a UX pattern, a learning — that shouldn't go in
  the bin with the rest.

The point of the artifact is not the list; it is the *ritual*. A kill
review that happens on a schedule — quarterly is a common cadence at
startup scale, in tandem with the strategic-bet review from Lecture 3 —
turns killing from an executive act of unusual courage into an ordinary
part of the operating rhythm.

## Pre-mortems: catch what you'd otherwise kill later

Gary Klein's **pre-mortem** technique inverts the postmortem: at the
moment of committing to a project, the team is asked to *imagine it has
already failed* and to write down the most plausible reasons why. The
exercise surfaces risks and doubts that the go-ahead ritual normally
suppresses
([Klein, "Performing a Project Premortem," *Harvard Business Review*,
September 2007 — hbr.org/2007/09/performing-a-project-premortem](https://hbr.org/2007/09/performing-a-project-premortem)).

For prioritization, the pre-mortem's value is that it produces the
*kill criteria* almost automatically: the failure modes named in the
pre-mortem become the leading indicators you monitor. "If the beta ships
and the top-10 target-segment customers each use it fewer than three
times in the first month" is a kill criterion; it also, uncoincidentally,
is the top pre-mortem answer to *why did this fail?*.

Add a pre-mortem to every strategic-bet funding decision. Twenty
minutes at fund time saves a quarter of denial at kill time.

## Separating the person from the project

The single most-common practical obstacle to killing well is that the
person who championed the work will read the kill as a verdict on
their judgment. Sometimes it is; usually it isn't — you funded the bet
with them, on evidence that then turned out differently.

Three moves the CPO owns:

- **Publicly credit the risk-taking**, separately from the outcome.
  Betting on a serious opportunity and being willing to kill it is the
  behaviour you want to reward; punishing it teaches the org to bet
  smaller and hide longer.
- **Assign the champion the next comparable bet** if the postmortem
  shows the reasoning was sound and the world simply didn't cooperate.
  Withholding the next bet is punishment for the outcome; giving it is
  the tell that the org rewards the *quality of the reasoning*.
- **Never announce a kill in the same conversation as the postmortem.**
  The postmortem is a learning artifact; the kill is a resourcing
  decision. Braiding them turns both into performance reviews.

## The specific case: killing something you *personally* proposed

The bias load is heaviest when the failing bet is one the CPO championed.
Two counter-moves:

- **Delegate the kill review authorship.** Have a peer (another exec,
  the CTO, a board member) draft the "should we kill this?" memo. You
  can veto or accept, but you should not be the author who has to argue
  against themselves.
- **Set a pre-registered kill trigger *in writing to the board or your
  co-founder*.** Once the trigger exists on paper with a witness, the
  consistency bias flips: honouring the pre-registered trigger becomes
  the consistent move.

## What the ritual looks like on a Tuesday

A quarterly kill review, roughly one hour, run by the CPO:

1. **Every surface owner brings one candidate to kill.** Not zero. If
   the owner insists nothing on their surface deserves a kill, the CPO
   picks one for them to defend against.
2. **The peer reviewer presents the case *for* killing each candidate**,
   using the surface owner's own written kill criteria from the fund
   decision.
3. **The owner responds.** New evidence that changes the picture,
   proposed course corrections with their own kill criteria.
4. **A decision is written down and dated** — kill, continue-with-new-
   criteria, or continue-unchanged-with-CPO-signoff — and the swap (what
   moves up the queue as a result) is named.
5. **The kill list is published** the same day. Publishing is what makes
   it a governance artifact rather than a meeting.

That's it. The mechanism is not glamorous; the discipline is that it
happens every quarter, on the same day, with the same shape.

## Boundaries this lecture keeps

- **The people side of stopping work** — how you communicate a kill to
  the team, redeploy people, handle career impact of championing a
  killed bet — is deferred to
  [startup-operations-governance-curriculum](https://github.com/ai-startup-curriculum/startup-operations-governance-curriculum)
  (level 50) for people-ops depth.
- **The financial side of writing off in-progress investment** — what
  the burn model looks like when a bet is stopped mid-flight — is
  deferred to
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum)
  (level 40).

## Takeaways

- Kill discipline is a bias problem, not a courage problem. The four
  biases — sunk cost, endowment, consistency, loss aversion — each have
  a specific counter-move.
- Pre-register kill criteria at fund time. It's the single highest-
  leverage intervention.
- Kill lists are a *ritual*, not a document. Publish quarterly; write
  down the swap; separate the champion from the outcome.
- If a bet is yours, delegate the kill review's authorship. You cannot
  reliably be the prosecution of your own case.

Lecture 6 closes the module by naming the two boundaries that bound
prioritization above and below: the company thesis you're prioritizing
*for*, and the runway you're prioritizing *within*.
