# Lecture 6 — Disagreement with a founder-CEO: decision rights, tie-breakers, disagree-and-commit

## The setup

A founding CPO does not report to a professional-CEO with a
long career in delegating product ownership. They report to a
**founder-CEO**, typically technical, who ran product before the
CPO existed, has the strongest opinions in the building about
what to ship, has the deepest customer relationships from the
first ten deals, and — importantly — sits inside a flat
organization structure where "the CPO's decision" and "the CEO's
decision" are not clearly separated by an org chart or a written
charter.

This is the environment the market actually hires founding CPOs
into. The 2026 posting corpus for the role (see
[JOB_REQUIREMENTS.md](../../../JOB_REQUIREMENTS.md#requirement-themes--coverage)
in this repo) shows ~56% of postings explicitly asking for a
*direct working relationship with a technical founder-CEO*. The
CPO who cannot handle roadmap disagreement in this environment
becomes one of two things: a Jira admin executing the CEO's
mental model unchallenged, or a leader who quits after six
months because they were not allowed to lead. Neither is what
the company hired the CPO to be.

This lecture is the disagreement mechanic. It is short because
the moves are few and the discipline is in doing them
consistently. Three sources anchor the treatment: Amazon's
public *"disagree and commit"* principle ([Bezos, 2016
shareholder letter —
aboutamazon.com](https://www.aboutamazon.com/news/company-news/2016-letter-to-shareholders)),
Netflix's decision-framework work on the *"informed captain"*
model (Reed Hastings and Erin Meyer, *No Rules Rules*, Penguin,
2020 —
[penguin.co.uk](https://www.penguin.co.uk/books/439291/no-rules-rules-by-hastings-reed-and-meyer-erin/9780753553640)),
and — for the specific dysfunctions of founder-flat structures
— Ben Horowitz's *The Hard Thing About Hard Things* (Harper
Business, 2014 —
[a16z.com/book/the-hard-thing-about-hard-things](https://a16z.com/book/the-hard-thing-about-hard-things/)).

## The three disagreement categories

Not all roadmap disagreements are the same shape. Confusing them
is where first-time CPOs get stuck. Three categories, each with
a different resolution mechanic:

1. **Diagnosis disagreements.** The CPO and CEO disagree about
   what the *decisive challenge* is (Lecture 1's diagnosis).
   These are the highest-stakes disagreements and they cannot
   be resolved by process. They have to be worked through
   substantively — with evidence — because the diagnosis is
   what everything else on the roadmap follows from.
2. **Guiding-policy disagreements.** They agree on the
   diagnosis but disagree on the approach. *"We both see that
   the collection loop is the decisive challenge; you think we
   should platform it, I think we should point-product it
   first."* These are the productive disagreements — the
   evidence in the platform-vs-point-product lecture (Lecture
   4) is what resolves them.
3. **Coherent-action disagreements.** They agree on the
   policy but disagree on the specific bets underneath.
   *"We agree we're going point-product first; you want to
   ship the review workflow first, I want the connectors
   first."* These are the lowest-stakes disagreements and the
   ones the CPO should be *allowed* to make unilaterally in a
   healthy operating relationship. If the CPO cannot make
   category-3 calls without CEO approval, the operating
   relationship is broken and Lecture 5's peer read-out
   frequency is not going to fix it.

The first move in any disagreement is to name which category
it's in. Half the founder-CEO / CPO fights in first-time
founding-CPO experience are category-3 fights that got
mis-diagnosed as category-1 or -2 and dragged all three
audiences of Lecture 5 in unnecessarily.

## Decision rights — write them down before you need them

The largest single mistake first-CPOs make is not writing
decision rights down until they're in the middle of a
disagreement. By then, one or both parties will read the
proposed rights as a power move rather than a normalization.

The right time to author decision rights is in the first
30 days on the job, before there is anything to disagree
about. The right shape is a short document — one page — that
names, for each roadmap-relevant decision type, who has the
call. RACI works, but at a founding-team scale a lighter
frame is usually better. The **DACI** frame — Driver,
Approver, Contributors, Informed — from Atlassian
([atlassian.com/team-playbook/plays/daci](https://www.atlassian.com/team-playbook/plays/daci))
is the most useful shape for founder-CEO / CPO clarity because
the Driver / Approver split explicitly names *who can call it*
and *who can override*.

A minimal decision-rights table for a founding-CPO / founder-
CEO relationship (adapt to your context):

| Decision | Driver | Approver | Consulted | Informed |
|---|---|---|---|---|
| Company diagnosis (Rumelt Level-1) | Founder-CEO | Board | CPO, other execs | Team |
| Product diagnosis (product-scope) | CPO | Founder-CEO | Other execs | Team |
| Guiding policy (product-scope) | CPO | Founder-CEO | Other execs | Team |
| Coherent-action list (in-quarter) | CPO | — | Founder-CEO, other execs | Team |
| Deferrals (Not-Now list) | CPO | — | Founder-CEO, GTM | Team, board |
| Platform-vs-point-product bet | CPO | Founder-CEO | CTO, GTM lead | Team, board |
| Team OKRs (per-team) | Team + CPO | — | Founder-CEO on request | Peers |
| CPO OKRs (quarterly) | CPO | Founder-CEO | Other execs | Team, board |
| Kill decisions (in-quarter) | CPO | — | Founder-CEO if strategic | Team |
| Strategy revision (mid-quarter) | CPO | Founder-CEO | Board on request | Team |

Two things about this table:

- **The CPO drives more calls than they need approval for.**
  This is the point. A CPO who needs approval on every
  coherent-action call is a Jira admin. If your table has the
  founder-CEO as Approver on every row, the operating
  relationship is not yet a CPO relationship.
- **The founder-CEO is Approver on the strategy-scope calls,
  not the delivery calls.** This is what preserves the
  founder-CEO's legitimate authority over the direction
  without pulling them into every bet.

Author this table with the founder-CEO in the first month,
review it every six months, and refer to it *by name* in
disagreements. *"This is a Guiding-policy call; I'm Driver,
you're Approver."* The naming is what turns a personality
disagreement into a process disagreement, which is the only
kind that resolves.

## The disagree-and-commit mechanic

Amazon's Leadership Principles include *Have Backbone;
Disagree and Commit* ([Amazon Leadership Principles —
aboutamazon.com/about-us/leadership-principles](https://www.aboutamazon.com/about-us/leadership-principles)),
formalized publicly in Bezos's 2016 shareholder letter
([aboutamazon.com/news/company-news/2016-letter-to-shareholders](https://www.aboutamazon.com/news/company-news/2016-letter-to-shareholders)).
The mechanic:

- **Disagree first, in writing, with evidence.** If you
  disagree with a call the CEO is about to make on a
  strategy-scope roadmap question, write the disagreement
  down. State your read of the diagnosis, your read of the
  evidence, and what falsifier would tell you either of you
  was wrong. Do not present the disagreement verbally in a
  hallway; do not raise it in a group meeting the first time.
- **Commit, once the call is made, and commit visibly.**
  If the founder-CEO calls it the other way — and, per the
  decision-rights table, they are the Approver on
  strategy-scope calls — you commit to the call. That means
  executing it, defending it to the team and to peers, and
  not litigating it in the next hallway conversation. The
  visibility of the commit is what makes disagree-and-commit
  more than an intellectual pose.
- **Pre-register what would move the call.** As part of the
  disagreement, name what evidence would cause the call to
  be revisited. This is what makes disagree-and-commit
  compatible with intellectual honesty: you are not
  abandoning your read, you are naming what would change it.

Bezos's specific 2016 example — committing to the *Amazon
Studios* production greenlight despite disagreeing with its
prospects — is worth reading in the letter itself. The point
that most first-time CPOs miss: he *voiced the disagreement
in writing* first, then committed, then honored the commit
visibly. All three steps are load-bearing.

## Escalation and the tie-breaker

Two conditions where the disagree-and-commit mechanic does
not apply and the CPO should escalate rather than commit:

1. **The call violates a strategy-level commitment made to a
   third party.** If the CEO is asking the CPO to promise a
   feature to a customer that contradicts a commitment made
   to the board in the last read-out, the CPO's job is to
   surface the conflict to the CEO in writing before
   committing. Not doing so puts the CPO in a position of
   having lied to one audience or the other.
2. **The call would require the CPO to falsify evidence.**
   If the CEO is asking the CPO to present roadmap outcomes
   in a way the discovery evidence does not support — soften
   a falsifier, remove a Not-Now item that was decided on
   evidence, or write an OKR whose KRs the CPO does not
   believe are honest — the CPO does not commit. This is a
   values-scope decision, not a decision-rights-scope
   decision. Ben Horowitz's *Hard Thing About Hard Things*
   is directly on this point: the CEO's job is to *make the
   call*, and the CPO's job is to *tell the CEO the
   uncomfortable truth about the call* before it becomes a
   commitment to third parties
   ([Horowitz, *The Hard Thing About Hard Things*, Harper
   Business, 2014, "Lead
   Bullets"](https://a16z.com/book/the-hard-thing-about-hard-things/)).

For everything else, disagree-and-commit. Escalation is not a
regular tool; it is a rare tool.

## The tie-breaker vote — you already lost

A common first-time CPO pattern is to end a disagreement by
saying *"let's put it to a vote of the leadership team."*
Two things to know:

- **In a founder-flat structure the founder-CEO gets the
  tie-breaker.** They are the Approver on strategy-scope
  calls. Putting it to a vote does not change the outcome;
  it drags peers into the disagreement and lowers the
  CPO's authority for the next disagreement.
- **A well-authored decision-rights table already has the
  tie-breaker.** The tie-breaker for a category-1 or -2
  disagreement is the founder-CEO. The tie-breaker for a
  category-3 disagreement is the CPO. There is no vote.

If the CPO finds themselves proposing a vote, that is
usually a signal that (a) the decision-rights table was
never authored, or (b) the CPO has not committed after a
prior disagreement and is trying to get a new outcome by
reopening the question in a different forum. Neither is a
sustainable move.

## Cadence — the direct-with-founder rhythm

The disagreement mechanic depends on frequency of direct
contact. In a founder-flat structure the CPO / CEO one-on-one
is usually 2–3× a week at pre-Series-A, tapering to weekly
after that. The one-on-one is where diagnosis disagreements
get worked substantively, guiding-policy disagreements get
resolved with evidence, and coherent-action calls that the
CPO is about to make get *previewed* (so the CEO is never
surprised by a category-3 call they would have wanted to
weigh in on).

Two failure modes on cadence:

- **The one-on-one becomes a status update.** The CEO uses
  it to get delivery status, the CPO uses it to
  demonstrate progress, and neither one raises the
  strategy-scope questions. Symptom: the strategy hasn't
  been re-litigated in six weeks and both parties assume
  they agree. Fix: reserve half the meeting for a
  strategy-scope question the CPO comes with.
- **The one-on-one becomes an all-hallway substitute.** The
  CEO makes strategy-scope calls in hallway conversations
  with individual engineers, GTM leads, or the CTO,
  bypassing the CPO entirely. The CPO finds out via the
  team read-out that the strategy has been changed. Fix:
  raise it explicitly, once, with the decision-rights
  table in hand. If the pattern continues, the operating
  relationship is broken and no lecture will fix it.

## The written disagreement memo — the exercise-6 shape

The Exercise-6 deliverable is a written disagreement memo on
one real (or plausibly-synthetic) roadmap call where the CPO
and founder-CEO see it differently. The memo shape:

1. **The call being made.** One paragraph. State the CEO's
   position and yours; state which of the three categories
   above it is; state who is Driver and who is Approver per
   the decision-rights table.
2. **Your diagnosis-and-evidence.** Two paragraphs. What you
   believe the decisive challenge is, what evidence supports
   it, what evidence would falsify it. Include the customer
   quotes / metrics / discovery evidence that generated your
   read; do not present opinion without evidence.
3. **The CEO's diagnosis-and-evidence, in the best form you
   can steelman it.** One paragraph. If you cannot write a
   good version of the CEO's position, the disagreement is
   not ready to escalate — you have not understood it yet.
   This is the same discipline you'd apply to any adversarial
   verification (mod-002 Lecture 5, the pre-mortem move).
4. **What would move the call.** One paragraph. The signals
   that would cause you to commit to the CEO's call
   voluntarily, or that would cause the CEO to commit to
   yours. Concrete metrics, dated, at least one from each
   side.
5. **Your commit, if the call goes against you.** One
   paragraph. What you will do to execute the CEO's call
   visibly, what you will say to the team about it, and how
   you will monitor the falsifier you registered above.

The memo is short. The point is to force the disagreement
into a discussable artifact before it becomes a hallway
argument. Most first-time CPOs find that authoring the memo
resolves the disagreement — the discipline of steelmanning
the CEO's position frequently discovers evidence the CPO
hadn't weighted properly, or the discipline of writing your
falsifier out convinces the CEO the call should go your
way.

## What a healthy operating relationship looks like

For calibration, because most first-time CPOs have never
seen one:

- **Diagnosis disagreements happen quarterly, in writing,
  and are resolved substantively.** They do not happen in
  hallway conversations or in the middle of board meetings.
- **Guiding-policy disagreements happen every two to three
  months, are resolved by the evidence in Lecture 4's
  three-lens frame, and the loser commits visibly.**
- **Coherent-action disagreements happen weekly, are
  resolved by the CPO exercising the Driver role, and the
  CEO gets an FYI-visible read via the one-on-one before
  the call becomes public.**
- **Neither party is quietly re-litigating a call the other
  believed was closed.** If either party is, the
  disagree-and-commit mechanic has broken and the operating
  relationship needs a reset conversation before any more
  strategy-scope work gets done.
- **The team never sees a public disagreement between CPO
  and CEO where the two are undermining each other.** All
  three read-outs from Lecture 5 speak with one voice. The
  disagreements happen upstream; the read-outs show a
  committed direction.

If the operating relationship does not look like this within
six months, the CPO has three moves: renegotiate the
decision-rights table (usually works if the founder-CEO is
willing), escalate to the board (rarely appropriate for a
founding CPO), or leave (the correct call in a small but
real fraction of cases; Ben Horowitz's *Hard Thing* is
directly on this).

## Boundaries this lecture keeps

- **The general founder-CEO relationship contract** —
  building trust, communicating up, managing lateral
  relationships beyond the roadmap — is the subject of
  [mod-007](../../mod-007-working-with-founders-eng-and-gtm/README.md).
  This lecture teaches the roadmap-specific disagreement
  pattern; mod-007 teaches the general relationship it
  lives inside.
- **People-ops depth** — how to have hard conversations
  with reports, performance management, hiring and firing
  — is level-50 work owned by
  [startup-operations-governance-curriculum](https://github.com/ai-startup-curriculum/startup-operations-governance-curriculum).
- **Board dynamics and governance escalation** — when and
  how to escalate a CEO conflict to the board, board
  observer / voting rights, chairman dynamics — is level-40
  work owned by
  [startup-finance-fundraising-curriculum](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum).

## Takeaways

- **Name the disagreement category first.** Diagnosis,
  guiding-policy, or coherent-action. Half the founder-
  CEO / CPO fights are category-3 fights that got
  mis-escalated.
- **Author decision rights in writing in the first 30
  days**, before there's anything to disagree about. DACI
  is a fine shape. Refer to the table *by name* in
  disagreements — process disagreements resolve;
  personality disagreements do not.
- **Disagree first (in writing, with evidence and
  falsifiers), then commit visibly**, then honor the
  commit in the team and peer read-outs. The visibility of
  the commit is what makes disagree-and-commit more than a
  pose.
- **Escalate rarely — only for third-party commitments
  and evidence-falsification asks.** Everything else is
  disagree-and-commit.
- The **written disagreement memo** — call, diagnosis with
  evidence, steelmanned counter-position, what would move
  the call, commit-plan — is the artifact that most often
  resolves the disagreement without needing to escalate.

This closes the module. The exercises put the lectures to
work on your real (or plausibly-synthetic) product: strategy
in Rumelt-shape, roadmap in outcomes, OKRs at CPO scope,
platform bet with a falsifier, three-audience read-outs, and
one written founder-CEO disagreement.
