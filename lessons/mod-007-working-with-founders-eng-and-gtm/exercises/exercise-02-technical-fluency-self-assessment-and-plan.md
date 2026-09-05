# Exercise 2 — Technical fluency self-assessment and 90-day plan

**Time:** ~2 hours. **Deliverable:** one self-
assessment against the four fluencies from
[Lecture 2](../lectures/02-technical-fluency-for-the-founding-cpo.md),
one 90-day plan with concrete gap-closing
artifacts per fluency, one written PR-read against
a real (or open-source) pull request, and a
reviewer's memo.

## Purpose

Diagnose your current technical fluency against
the four-rung ladder from
[Lecture 2](../lectures/02-technical-fluency-for-the-founding-cpo.md#the-four-fluencies)
and produce a 90-day plan for closing your gaps.
The plan's shape is deliberately concrete —
artifacts, not aspirations — because the fluency
gap most first-time founding CPOs carry (PR
reading, API contract reasoning, engineering
scoping) closes with practice, not with reading
about it.

Bring the artifact into a real conversation with
a real engineer if you can. The self-assessment
is more honest when someone who reads your PR
comments has a chance to disagree with your
self-scoring.

## Choosing the context

- **The company at which you'll actually use the
  fluency.** If you're currently or about to be
  the founding CPO somewhere, the plan is for
  *that* codebase, that stack, that AI
  substrate.
- **A codebase you have access to.** Otherwise
  pick an open-source project in a stack close
  to what your target company runs — a Next.js
  + Postgres + Anthropic app, an LLM-agent
  framework, a RAG example. The read drill
  needs a real repo, not a hypothetical.
- **The stack you're weakest in.** If you have
  the choice, pick the stack you're least
  fluent in. The 90-day plan is more valuable
  when the starting gap is real.

## What the artifact bundle must contain

Roughly 4–5 pages plus one attached PR-read.

### 1. Self-assessment (1.5 pages)

Score yourself against each of the four
fluencies from
[Lecture 2](../lectures/02-technical-fluency-for-the-founding-cpo.md#the-four-fluencies)
on a 1–5 scale (1 = "I can't hold this
conversation"; 3 = "I can hold it with obvious
gaps"; 5 = "I could teach it to a junior PM").
For each:

- **The score and the reasoning.** Not just a
  number; the specific evidence. "3 because I
  can read a REST API PR but I got lost on
  the last GraphQL change."
- **The specific gap.** One or two concrete
  things you can't currently do that a 4 or 5
  could.
- **The last-time-you-used-it evidence.** When
  was the last real conversation where this
  fluency mattered? A fluency you haven't used
  in six months is probably atrophying.

Four fluencies to score:

- **Reading a PR** — against the six-question
  checklist in
  [Lecture 2](../lectures/02-technical-fluency-for-the-founding-cpo.md#fluency-1--reading-a-pr).
- **Reasoning about API contracts** —
  [Lecture 2](../lectures/02-technical-fluency-for-the-founding-cpo.md#fluency-2--reasoning-about-apis).
- **Infrastructure trade-offs at framing
  level** —
  [Lecture 2](../lectures/02-technical-fluency-for-the-founding-cpo.md#fluency-3--infrastructure-trade-offs-at-the-framing-level).
- **Scoping engineering work** —
  [Lecture 2](../lectures/02-technical-fluency-for-the-founding-cpo.md#fluency-4--scoping-engineering-work).

Also score yourself against the PRD under-
specification checklist ability from
[Lecture 2](../lectures/02-technical-fluency-for-the-founding-cpo.md#fluency-5--catching-under-specified-prds).

### 2. The 90-day plan (1.5 pages)

For each fluency where your score is below 4, a
30 / 60 / 90-day closure plan. The plan is
*artifact-based* — you'll produce specific
things — not "read this book" (which never
works).

For each fluency below 4:

- **The 30-day target.** A concrete artifact.
  For PR reading: "read 3 PRs a week from the
  team's repo against the six-question
  checklist, publish my read as a comment on
  the PR." For API reasoning: "read the ADR
  for the current API-versioning strategy and
  write a one-page summary of how it plays
  with the pricing-page migration." For infra
  trade-offs: "read the CTO's most recent
  three architectural decisions and write a
  one-page CPO-side interpretation." For
  scoping: "produce written estimates for
  the next four roadmap items with the eng
  lead, dated, with named unknowns."
- **The 60-day target.** A step-up. For PR
  reading: "the eng lead reviews my
  comments and confirms I'm asking useful
  questions." For scoping: "review the 30-
  day estimates against actual delivery; write
  the retrospective."
- **The 90-day target.** A step-up. For PR
  reading: "I'm the one who catches the PRD
  under-specification in a real PR before
  it ships." For scoping: "my rough
  estimates are within a factor of two on
  6 out of 8 items."
- **The person who checks your work.** Every
  fluency needs a check. Usually the eng
  lead or CTO. Name them.

### 3. The PR-read (1 page, attached)

Pick one real pull request — from your
company's repo if you have access, or from a
target open-source project. Ideally one that
touches a user-facing surface. Read it against
the [six-question
checklist](../lectures/02-technical-fluency-for-the-founding-cpo.md#fluency-1--reading-a-pr):

1. What does this do to what the user sees or
   does?
2. Is there a state change I need to document?
3. Is there a public API change?
4. What is the failure mode?
5. What's the test coverage?
6. What's the migration story?

Write your read in one page. Add a *specific
product-implication question* you'd ask if you
were the CPO on this feature. The question is
the diagnostic — if you can't formulate one,
your read was too abstract.

### 4. The under-specification test (half page)

Pick one PRD or feature spec you've written
(or, if you don't have one, take the most
recent public example — a spec from a project
you can find online). Run it through the
[under-specification checklist](../lectures/02-technical-fluency-for-the-founding-cpo.md#fluency-5--catching-under-specified-prds):

- Missing state transitions?
- Missing permission model?
- Missing empty state?
- Missing telemetry?
- Missing migration story?
- Missing feature-flag / rollout plan?
- Missing failure semantics for AI features?
- Missing cost / latency budget?

Which did the PRD miss? What would the
addition look like?

## Starter guidance

- **Be honest on the self-assessment.** The
  90-day plan is only useful if the starting
  score is real. A 4 you don't deserve
  produces a plan that doesn't close the gap.
- **The 30 / 60 / 90 targets should be
  artifacts.** Not "study X" or "learn Y" —
  those measure nothing. Artifacts you can
  point at.
- **Name the person who checks your work.** A
  90-day plan without a checker is a 90-day
  plan you'll silently abandon.
- **Pick a real PR for the read.** The
  vocabulary you build reading a synthetic
  PR doesn't transfer. Ideally, one with
  code you can actually run locally.
- **The under-specification test is the
  fastest fluency win.** Most CPOs already
  write PRDs; running the checklist against
  a real one produces immediate awareness of
  what your default PRDs miss.

## The reviewer's memo

Half a page, written after the artifact
bundle. Answer:

- **Which fluency is most likely to still be
  weakest after 90 days?** Why? What would
  it take to close?
- **The eng-lead / CTO reaction.** If you
  showed the self-assessment and 90-day plan
  to the eng lead you'd work with, what
  would they push back on? Would they think
  the plan under-shoots or over-shoots?
- **The PR-read result.** What specifically
  did you get right? What did you get
  wrong? What would you do differently on
  the next PR-read?
- **Which fluency does your future role
  need most?** If you're joining a company
  where infra trade-offs dominate the
  conversation (heavy-workload SaaS,
  regulated industries), infrastructure
  scoring higher matters more. If joining
  an AI-native product, the AI system
  fluency from
  [Exercise 3](exercise-03-ai-system-architecture-read-drill.md)
  matters more. Name your role's shape.

## Acceptance criteria

- Self-assessment scores each of the four
  fluencies (plus PRD under-specification)
  on 1–5 with reasoning, specific gap, and
  last-used evidence.
- 90-day plan gives concrete artifacts at 30
  / 60 / 90 days for every fluency scored
  below 4, plus a named check-person per
  fluency.
- PR-read is against a real PR and answers
  all six checklist questions plus produces
  a specific product-implication question.
- Under-specification test is against a real
  PRD and names which checklist items were
  missed.
- Every reference to
  [Lecture 2](../lectures/02-technical-fluency-for-the-founding-cpo.md)
  cites the specific fluency section.
- Reviewer's memo answers all four prompts.

## Common failure modes

- **Aspirational-plan shape.** The 30 / 60 /
  90 targets read as "understand X better"
  rather than "produce this artifact." The
  plan has to be measurable.
- **Uncalibrated self-score.** The CPO
  scores themselves a 4 on every fluency
  without evidence. Fix: run each score past
  a real engineer.
- **Synthetic PR.** The PR read is against
  a toy example rather than a real one. The
  fluency doesn't transfer.
- **No check-person.** No one is on the hook
  to review the 30 / 60 / 90 outputs. Fix:
  name someone before the plan is signed
  off.
- **Missing atrophy signal.** The self-
  assessment doesn't ask when the fluency
  was last used. A fluency you haven't
  practiced in six months is degrading
  regardless of what it once was.
- **Ignoring the boundary.** The plan
  includes items that are properly CTO-
  curriculum work (writing production code,
  authoring the ADR, choosing the database).
  Fix: keep the plan inside the CPO
  consumption layer that Lecture 2
  describes.

## Source alignment

The four-fluencies framing derives from
[Lecture 2](../lectures/02-technical-fluency-for-the-founding-cpo.md).
The engineering-management vocabulary the CPO
borrows to talk about the fluencies is Camille
Fournier, *The Manager's Path*, O'Reilly, 2017 —
[oreilly.com](https://www.oreilly.com/library/view/the-managers-path/9781491973882/).
The ADR pattern the PR-read and under-
specification test reference is the Michael
Nygard-style Architecture Decision Record; see
Nygard's original writing at
[cognitect.com/blog/2011/11/15/documenting-architecture-decisions](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions).
The engineering-scoping discipline that grounds
the fluency 4 rubric derives from Ryan Singer,
*Shape Up*, Basecamp, 2019 —
[basecamp.com/shapeup](https://basecamp.com/shapeup).
The architectural depth this exercise defers to
is
[cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)
mod-102 (Architecture Under Uncertainty) and
mod-103 (Build-vs-Buy).
