# Exercise 3 — PRD in Amazon 6-pager shape

**Time:** ~3 hours. **Deliverable:** one PRD in Amazon
six-pager (or PR/FAQ) shape — six pages of prose, plus
appendix — for a real product bet that will run through
the cadence you authored in Exercises 1–2, plus a
reviewer's memo on what the writing forced you to
notice.

## Purpose

Author the PRD form
[Lecture 3](../lectures/03-prd-in-amazon-6-pager-shape.md)
argues for — Amazon's narrative six-pager (or, for a
new-product / new-surface bet, the PR/FAQ variant) —
against a real bet on your team's queue. The point is not
to produce a template-filled document; the point is to
use the *act of writing prose* to notice what you don't
yet know about the bet, and to force the discovery /
Figma / eval decisions the bet will need before the team
commits.

## Choosing the bet

Use one bet you can name concretely. In order of
preference:

1. **A bet actually queued for the next Shape Up cycle
   or the next two weeks of kanban** on your team.
   Highest-value version; the memo will be read.
2. **A bet from your roadmap (mod-003) that would
   plausibly be the next commit.**
3. **A plausible synthetic bet** on the synthetic
   product you used in Exercises 1–2. If you go
   synthetic, keep the discovery evidence realistic —
   invent interview quotes only in the shape you'd
   have collected them.

Whichever you pick:

- **New-surface / new-product bet → PR/FAQ variant.**
  Write the press release first (Section 1 in the
  Lecture 3 PR/FAQ shape).
- **Feature or workflow change bet → general
  six-pager.** Skip the press release; open with
  context and diagnosis (Section 1 in the Lecture 3
  general shape).

## What the six-pager must contain

Six pages of prose (not bullets), plus an unbounded
appendix. Follow the shape from
[Lecture 3](../lectures/03-prd-in-amazon-6-pager-shape.md#the-general-six-pager-section-by-section)
(or the PR/FAQ variant, per your choice).

### Six-pager sections (feature / workflow bet)

1. **Context and diagnosis (half page).** The strategy
   this sits inside (mod-003), the opportunity
   underneath it (mod-002), the discovery evidence
   (mod-001). What is the decisive challenge this bet
   addresses?
2. **The customer and the problem (one page).** Who is
   the customer, in the specific segment for this bet?
   What is the JTBD? What is the problem — in the
   customer's words? What evidence: named interview
   count, named data pull, named eval result for
   AI-substrate features.
3. **The proposal (one page).** What are we proposing to
   build? Outcome-shaped, not feature-shaped. What is
   the mechanism? Top three design decisions the team
   will face, and — for each — the axis on which they
   should be made.
4. **How we know it worked (one page).** Pre-registered
   success metric, horizon, falsifier. Four-week and
   twelve-week signals. For AI-substrate bets:
   pre-registered eval threshold, cost-per-interaction
   budget, and p95 latency budget as first-class
   signals ([Lecture 5](../lectures/05-agentic-ux-iteration-loops.md#cost-and-latency-as-user-facing-surface)).
5. **What we're not doing (half page).** Explicit v1
   deferrals. Named stakeholder requests not honored.
   Why the guiding policy forces the deferral. What
   would move it in a later bet.
6. **Risks and open questions (half page).** Adoption
   risks, technical risks (consumed from the tech
   lead), cost / latency risks for AI substrate,
   operational risks (support load, on-call impact —
   consumed from
   [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)
   at level 25). Open questions the memo has not
   resolved.
7. **Appendix.** Screens, wireframes, data pulls,
   interview notes, prompt / eval sketches, cost /
   latency modeling, source-system dependencies.
   Unbounded.

### PR/FAQ sections (new-surface / new-product bet)

1. **Press release (one page).** Headline, sub-
   headline, summary paragraph, problem paragraph,
   solution paragraph, leader quote, customer quote,
   call to action.
2. **Internal FAQ (two–three pages).** The full
   question list from
   [Lecture 3](../lectures/03-prd-in-amazon-6-pager-shape.md#section-2--internal-faq-two-to-three-pages).
3. **External FAQ (one page).** Customer / press
   questions.
4. **Appendix (unbounded).**

## The reading ritual — do it

After you've drafted the memo, run the **silent-meeting
reading ritual** from
[Lecture 3](../lectures/03-prd-in-amazon-6-pager-shape.md#the-reading-ritual):

- Get one to three colleagues (real or role-played) to
  spend 20 minutes reading the memo silently, in
  person or on a shared call with cameras off.
- After the read, capture the top three questions each
  reader had, in their own words.
- Note which of their questions you had already
  answered but they missed (a writing problem) and
  which of their questions you had not answered (a
  thinking problem).

The output of the ritual becomes part of the reviewer's
memo below. If you can't get colleagues, run the ritual
on yourself 24 hours later — set the memo aside for a
day, then read it silently at your own desk, and take
the same three-question capture from the future-you
reader.

## Starter guidance

- **Write in prose from minute one.** No outlining, no
  bullets-that-you'll-convert-later. The whole
  discipline is doing the hard thinking in complete
  sentences. If you find yourself defaulting to
  bullets, close the doc and start again.
- **The press release (PR/FAQ) is a thinking artifact,
  not marketing.** Draft the customer quote in the
  language your interviews say the customer actually
  uses. If you can't write it convincingly, you don't
  yet know what the customer will say — go back to
  discovery.
- **Timebox the write.** Aim for four hours. If it's
  taking three days, the memo is hiding a discovery
  problem or a strategy problem; identify which and
  address it in the reviewer's memo.
- **Do not open comments in the doc before it is
  readable.** Draft privately. Comments live in the
  silent-meeting review, not asynchronously.
- **The pre-registered signals go in the doc, not
  in a separate metrics doc.** Making the signals
  legible to the reader of the memo is the whole
  point of the pre-registration discipline.
- **The appendix is where facts live, not
  aspiration.** Charts, interview notes, prompt
  drafts, eval sketches. Anything cited in the memo
  should be in the appendix; anything in the appendix
  should be citable from the memo.

## The reviewer's memo

Half a page, written after the six-pager and the
reading ritual. Answer:

- **What did writing this in prose force you to notice
  that you would not have noticed writing bullets?**
  Be specific. Which sentence made you realize you
  didn't have the discovery evidence, or that two
  requirements contradicted each other, or that the
  cost / latency budget was going to fight the pricing
  model.
- **What questions did the silent-meeting readers ask
  that revealed a thinking gap (not a writing gap)?**
  Which of those questions triggered a revision to
  the memo? Which triggered a decision to send the
  bet back to discovery rather than continue?
- **PRD gestation check.** How long did the memo
  actually take to draft? If materially over four
  hours, name where the time went — was it discovery
  substituting for thinking, was it stakeholder
  politics substituting for a decision, was it the
  team's PRD template forcing you to fill in twenty
  sections you don't have answers for?

## Acceptance criteria

- Six pages of prose, plus appendix. Bullets only in
  the appendix, not in the body.
- All seven sections (six-pager) or all four sections
  (PR/FAQ) are present, in order, at roughly the
  named length.
- The pre-registered success metric section names a
  metric, a horizon, and a falsifier. For
  AI-substrate bets, it also names an eval-set
  threshold, a cost-per-interaction budget, and a
  latency budget.
- At least three explicit v1 deferrals, each with a
  named stakeholder request and a move-in signal.
- The appendix contains the *evidence* the memo
  cites: interview notes / count, data pull, prompt
  or eval draft if applicable, screens if applicable.
- The silent-meeting reading ritual was run (with
  colleagues or with yourself 24 hours later); the
  reviewer's memo captures readers' questions.
- The reviewer's memo answers all three prompts and
  includes a PRD-gestation check.

## Common failure modes

- **The template-filled six-pager.** Every section is
  filled in with two paragraphs of plausible-sounding
  text that could apply to any product. Diagnose: if
  the six-pager could be swapped between two
  different products without editing more than the
  proper nouns, it is fluff.
- **Bullets-in-prose costume.** Sentences that are
  actually bullets in a sentence casing. Diagnose:
  can you remove one sentence without affecting
  another? If yes, they're bullets.
- **The unfalsifiable metric.** "We will measure
  customer delight" is not a pre-registered signal.
  "≥50% of top-20 accounts have replaced the
  spreadsheet workflow within four weeks of ship" is.
- **The absent-appendix.** The memo cites evidence
  ("customer interviews suggest…") without an
  appendix that lets a reader audit the claim.
- **The infinite-appendix.** An appendix that is
  larger than the memo and unstructured is a place to
  hide unfinished thinking, not evidence.
- **Comments-in-draft.** Ten reviewers commenting on
  a half-drafted memo. This is PRD gestation
  starting; refuse it.
- **Ship-the-doc mentality.** Green-checking the memo
  and treating it as done, then starting eight weeks
  of build. The ship is the deliverable, not the
  doc.

## Source alignment

The narrative six-pager and PR/FAQ derive from Jeff
Bezos's 2004 shareholder letter —
[aboutamazon.com/news/company-news/2004-letter-to-shareholders](https://www.aboutamazon.com/news/company-news/2004-letter-to-shareholders)
— and the working-backwards practice documented in
Colin Bryar & Bill Carr, *Working Backwards: Insights,
Stories, and Secrets from Inside Amazon*, St. Martin's,
2021 — [workingbackwards.com](https://www.workingbackwards.com/).
The outcome-shaped content of the proposal derives
from Melissa Perri, *Escaping the Build Trap*,
O'Reilly, 2018 —
[oreilly.com](https://www.oreilly.com/library/view/escaping-the-build/9781491973783/).
The pre-registered falsifier discipline is the mod-002
Lecture 1 discipline applied to a bet artifact — see
[mod-002 Lecture 1](../../mod-002-opportunity-assessment-and-prioritization/lectures/01-opportunities-as-bounded-problems.md).
