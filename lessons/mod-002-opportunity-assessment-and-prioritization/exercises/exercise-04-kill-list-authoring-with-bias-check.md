# Exercise 4 — Kill-list authoring with bias check

**Time:** ~3 hours. **Deliverable:** a kill list with 3–5 candidates,
each with a bias-check annotation, plus a swap plan naming what each
kill funds instead.

## Purpose

Practice the ruthless half of prioritization on real (or plausible)
in-flight work — not on hypothetical items, and not only on items
someone else owns. The lecture behind this is
[Lecture 5](../lectures/05-killing-work-you-already-started.md).

## Choosing the material

Pick 3–5 candidate items for the kill list. Sources, in preferred
order:

1. **Real in-flight work** on the product you're currently working
   on. This is the highest-value version of the exercise; the
   discomfort is the point.
2. **Historical work** you shipped or oversaw at a previous company
   that in retrospect should have been killed sooner. If you go
   here, name the quarter you'd have killed it in and what evidence
   was available at that quarter.
3. **The synthetic company from Exercise 3** — if you built a
   plausible product there and can name 3–5 items on its imagined
   roadmap that a disciplined CPO might question.

At least one of the candidates **must be work you personally
championed** or would be seen as championing. The bias mechanics
Lecture 5 covers are qualitatively different when it's your bet; the
exercise is meant to force you to notice.

## What each kill-list entry must contain

Follow the shape in
[Lecture 5](../lectures/05-killing-work-you-already-started.md#the-kill-list-as-a-governance-artifact).
For each candidate:

1. **What we're killing.** Feature / opportunity / surface, named
   concretely.
2. **Why we're killing.** Which pre-registered kill criterion tripped,
   or — if none was registered up-front — which new information
   makes the case now. If there was no pre-registered criterion,
   note that; it's a finding for future funding decisions.
3. **Sunk cost.** Person-weeks / dollars spent to date. Order-of-
   magnitude is fine, but named. The point is not to shame; the
   point is to refuse to hide the number so you can watch the sunk-
   cost bias fight for the item.
4. **What frees up.** Team members, engineering capacity, oncall
   load, design load — with names / seat counts if you can.
5. **What we're funding instead.** The specific opportunity moving
   up the queue as a result. If you cannot name the swap, note that
   — you may not be ready to kill this yet, you may just want to
   pause it, and those are different actions.
6. **Bias-check annotation.** Two or three sentences answering:
   which of the four biases (sunk cost, endowment, consistency, loss
   aversion) is doing the most work to keep this item alive? Which
   specific counter-move from Lecture 5 addresses it? What would
   change your mind about the kill? Be honest — this is the section
   the exercise is really about.
7. **Sign-off.** Who owns the kill decision — CPO, surface owner,
   peer reviewer. For the item you personally championed, name the
   peer reviewer explicitly; you cannot be the sole author of your
   own kill memo (Lecture 5).

## The swap plan

After the kill-list entries, write a half-page swap plan:

- Aggregate what capacity is freed by the full list (people-weeks,
  seats).
- Name the opportunities that capacity is redirected to. Reference
  the Exercise-1 opportunity assessments or the Exercise-3
  allocation memo if you have them.
- Name at least one opportunity that will *not* be funded even
  after the kills — the discipline is that killing doesn't
  automatically solve the capacity problem, it just makes the
  tradeoffs more honest.

## Starter guidance

- **Kill work you're currently proud of.** If everything on your
  kill list is something you already privately doubted, you're
  practicing on softballs. The bet you defended in the last board
  deck is the one this exercise is trying to reach.
- **Sunk cost is a fact, not a defense.** Write the number down and
  then argue the item forward on marginal grounds. If the marginal
  case dies without the sunk cost, kill.
- **Endowment shows up as "you don't understand how important
  this is."** If your defense of the item can only be understood
  by people inside the team, that's the tell.
- **Consistency shows up as "we already told the board."** The
  counter-move (Lecture 5) is pre-registered kill criteria in the
  *same* board deck. If those don't exist retroactively, name that
  as the process gap.
- **Loss aversion shows up as vague swaps.** If your "what we're
  funding instead" is fuzzy, loss aversion has the item on life
  support. Name the swap concretely or accept that you're not
  actually going to kill.

## Acceptance criteria

- 3–5 kill-list entries, each ≤ half a page.
- At least one entry is work you personally championed and has a
  named peer reviewer.
- Every entry names the sunk cost as a number.
- Every entry names the swap concretely — a specific opportunity or
  a specific person-week reallocation.
- Every entry has a bias-check annotation naming one of the four
  biases and its counter-move.
- A swap plan of half a page follows the list, and it names at
  least one opportunity that will *not* be funded even after the
  kills.

## Common failure modes

- **Bad candidates.** The kill list becomes items nobody was going
  to fund anyway — a "kill list" for hypotheticals no one was
  attached to. That's a to-do list, not a kill list.
- **Missing bias check.** *"We're killing this because it doesn't
  fit the strategy"* is the shape the biases *want* the kill to
  take, because it's blameless. The bias check is the discipline;
  it's the section you're most tempted to skip.
- **Killing to fund yourself.** If every swap directs freed
  capacity to a project you personally proposed, examine the
  endowment bias operating in the *other* direction.
- **Announcing the kill inside the postmortem.** Lecture 5 —
  postmortem is a learning artifact, kill is a resourcing
  decision. Braided together they become performance reviews and
  the team learns to hide.

## Source alignment

- Sunk-cost fallacy — [Thaler, "Toward a Positive Theory of Consumer
  Choice," *JEBO*,
  1980](https://www.sciencedirect.com/science/article/abs/pii/0167268180900517);
  [Arkes & Blumer, "The Psychology of Sunk Cost," *OBHDP*,
  1985](https://msu.edu/~ema/803/Ch11-Uncertainty/2/ArkesBlumer85.pdf).
- Endowment effect — [Kahneman, Knetsch & Thaler, "Experimental
  Tests of the Endowment Effect and the Coase Theorem," *JPE*,
  1990](https://www.jstor.org/stable/2937761).
- Consistency & escalation of commitment — [Cialdini, *Influence:
  The Psychology of Persuasion*, rev. ed.,
  2006](https://www.influenceatwork.com/); [Staw, "Knee-Deep in the
  Big Muddy," *OBHP*,
  1976](https://www.sciencedirect.com/science/article/abs/pii/003050737690005U).
- Loss aversion — [Kahneman & Tversky, "Prospect Theory," *Econometrica*,
  1979](https://www.jstor.org/stable/1914185).
- Kill lists as governance artifact — [Collins, *Good to Great*,
  HarperBusiness, 2001, Chapter
  6](https://www.jimcollins.com/books/good-to-great.html);
  [Collins, "Best New Year's Resolution? A 'Stop Doing' List,"
  2003](https://www.jimcollins.com/article_topics/articles/best-new-years.html).
- Pre-mortems — [Klein, "Performing a Project Premortem," *HBR*,
  September 2007](https://hbr.org/2007/09/performing-a-project-premortem).
