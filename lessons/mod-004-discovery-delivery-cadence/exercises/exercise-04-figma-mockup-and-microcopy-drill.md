# Exercise 4 — Figma mockup and microcopy drill

**Time:** ~3 hours. **Deliverable:** one Figma mockup
plus a microcopy pass on a live surface of your product
(or the Exercise 3 bet's primary surface), a pre-ship walk
checklist, a first changelog entry authored in the CPO's
voice, and a reviewer's memo on what the CPO's edits
changed versus the engineer / designer's first draft.

## Purpose

Put the CPO's hands on the pixel and the string, in the
tool the engineering team actually uses. The point is not
to produce a production-ready design — that is the
designer's craft, out of scope for a CPO curriculum. The
point is to practice the four
[Lecture 4](../lectures/04-own-the-pixel-figma-and-microcopy.md)
disciplines the market now expects every founding CPO to
run personally: a thinking-fidelity Figma mockup, a
microcopy pass on every user-facing string, a pre-ship
walk, and a changelog entry authored in the CPO's voice.

## Choosing the surface

Use one surface you can name concretely. In order of
preference:

1. **The primary surface of the Exercise 3 bet.** The
   six-pager you wrote already named a mechanism and
   several design decisions; put the pixel on them. This
   is the highest-value version.
2. **A live surface of your current product** that you
   have the right to touch — an empty state, an
   onboarding step, a settings page, an error flow.
3. **A plausible synthetic** on the Exercise 1 / 2
   synthetic product. If you go synthetic, write half a
   paragraph naming the surface, the user who meets it,
   and the moment in the user's journey it appears.

Whichever you pick, the surface must have **at least one
state the user has never seen before** (an empty state,
an error, an onboarding step, a first-time use flow).
Those are the states where the four Lecture 4
disciplines compound.

## What the deliverable must contain

Four to six pages of artifact plus the Figma file.
Adopt the shape from
[Lecture 4](../lectures/04-own-the-pixel-figma-and-microcopy.md),
in the following order.

### 1. Surface memo (half page)

- **What surface are you working on.** Name the screen
  (or screens, if a flow), the user segment who meets
  it, and the moment in their journey it appears.
- **What state coverage.** List every state the surface
  can be in — empty, loading, partial-data, happy-path,
  error, long-input, long-list-of-items, offline. The
  list is itself the exercise; most teams only design
  the happy path and ship the rest.
- **Current baseline.** If the surface already exists,
  include a screenshot of the current version and name
  what is wrong with it in one or two sentences
  (unedited empty state, buttons named by action not
  outcome, no error diagnosis, inconsistent tone).
- **Design-system availability.** Does your product
  have a Figma component library or a shadcn / Tailwind
  / Chakra / in-house design system you can draw from?
  Name it. If none exists, say so and note the
  component-drift cost you are about to incur.

### 2. The Figma mockup (one page of memo + Figma file)

Produce a clickable mockup in Figma covering **at least
three states** of the surface. Not production fidelity —
*thinking fidelity*. Follow the four Figma disciplines
from
[Lecture 4](../lectures/04-own-the-pixel-figma-and-microcopy.md#figma-as-thinking-tool):

- **Use the design system.** Draft in real components —
  the real button, the real input, the real card. If no
  design system exists, use shadcn / ui or Figma's
  default UI kit as a stand-in; do not invent a one-off
  button.
- **Draft in components, not rectangles.** No
  rectangles-labeled-"button." A reader of the Figma
  should be able to tell what each element *is*, not
  guess.
- **Prototype the flow.** Wire the states together in
  Figma's prototype mode so a reviewer can click
  through — mockup → next-state → error → empty →
  recovery. A static three-screen mockup is a Lecture 4
  anti-pattern.
- **Version and comment in-file.** Keep the
  conversation about the design on the frames
  themselves, not in Slack or a separate doc.

Export at least one screenshot per state for the memo.
Link the live Figma file (or an exported PDF if you
cannot share live) in the appendix.

### 3. The microcopy pass (one page)

Produce a **string table** for the surface — every
piece of user-facing text, in two columns:

| Element | First-draft string (engineer / designer / default) | CPO edit |
| --- | --- | --- |
| Primary CTA button | *Submit* | *Send invitations* |
| Empty-state headline | *No results* | *You haven't added any evidence requests yet* |
| Empty-state subhead | *Try again* | *Add your first one — most take about three minutes* |
| Error toast | *Something went wrong* | *We couldn't save your changes. Try again, or contact support if this keeps happening.* |
| Loading state | *Loading…* | *Generating draft…* |

Cover every string on the surface — buttons, labels,
headlines, subheads, tooltips, errors, loading states,
empty-state copy, onboarding microcopy, inline helper
text. Then write a half-page reflection applying the
[four microcopy disciplines from Lecture 4](../lectures/04-own-the-pixel-figma-and-microcopy.md#microcopy-is-the-product):

- **Buttons name the outcome, not the action.** Which
  buttons did you rewrite from an action verb to an
  outcome? Which did you leave alone and why?
- **Errors diagnose, then remedy.** Did you replace at
  least one "something went wrong" with a diagnosis +
  remedy pair?
- **Empty states explain and invite.** Does your empty
  state teach the surface's purpose and name the
  first step?
- **Tone is a decision.** State the tone decision you
  made (terse / warm / precise / neutral) and apply it
  consistently across every string. If your product
  does not have a published tone / voice guide, draft
  one in two paragraphs — the shape of Mailchimp's or
  GOV.UK's guides is a good reference.

For **AI-substrate surfaces** — any string that scaffolds
an LLM output — add a row for the trust-model strings:
*"Generated draft"* / *"AI-assisted — review before
sending"* / *"Sources: [1] [2]"* / regenerate-button
wording. These do disproportionate product work
([Lecture 4](../lectures/04-own-the-pixel-figma-and-microcopy.md#microcopy-is-the-product);
[Lecture 5](../lectures/05-agentic-ux-iteration-loops.md)).

### 4. The pre-ship walk checklist (half page)

Author the specific checklist you (or whichever CPO
inherits this surface) will walk before the flag flips
to real users. Not a QA checklist — a *product-taste*
checklist. From
[Lecture 4](../lectures/04-own-the-pixel-figma-and-microcopy.md#where-the-cpo-reviews-with-the-eng-team),
cover at minimum:

- **Every state renders correctly** — empty, loading,
  error, happy-path, long-list, long-input, offline.
- **Every string reads as intended** — no
  auto-generated placeholder text in production, no
  Lorem Ipsum, no engineer-shorthand strings, no
  untranslated keys.
- **The affordance test passes** (Lecture 4
  Discipline 1) — show one state to someone who has
  never seen it before and ask them what the screen
  is for and what to do next. If the read is muddled,
  the design is.
- **The visual hierarchy test passes** (Lecture 4
  Discipline 2) — the single most important thing on
  each screen is also the most visually prominent.
- **The empty state teaches** (Lecture 4 Discipline 3)
  — the first-time user, seeing zero data, can tell
  what to do next without reading a tour.
- **Latency behavior is observed on real network
  conditions** — not localhost. For AI-substrate
  surfaces, p95 latency against the budget from the
  [Exercise 3 six-pager](exercise-03-prd-in-amazon-6-pager-shape.md).

Date the walk — the checklist is not a one-off; it is
the ritual you will run every ship from here on.

### 5. The changelog entry (quarter page)

Author the live changelog entry that would ship with
this surface. Follow the four-element form from
[Lecture 4](../lectures/04-own-the-pixel-figma-and-microcopy.md#the-changelog-as-a-product-artifact):

- **Title** — outcome-shaped, in the user's words. Not
  *"Shipped new empty state"*; something like *"You
  can now add your first evidence request without
  reading the docs."*
- **One-paragraph description** — what changed, why it
  changed, who it is for.
- **Screenshot or clip** — one still from the Figma
  mockup is fine for the exercise.
- **Docs link** — if non-trivial, name the docs page
  the change updated (or would update). If no docs
  update is needed, say why.

Write the entry at the standard of Linear's / Basecamp's
public changelogs — tone-consistent, outcome-named, no
engineer-speak. If your product does not yet publish a
changelog, this exercise authors the first one and the
voice it is written in.

### 6. CPO-vs-first-draft reviewer's memo (half page)

The reflection. Answer, in prose, not bullets:

- **What did your edits change?** Line up the Figma
  states and the string-table against what the
  engineer / designer / default would have shipped and
  name the *categories* of change: component
  substitution, hierarchy inversion, microcopy
  rewrite, state coverage addition. Not every edit
  individually — the *shape* of the edits.
- **Which edits were highest leverage?** If you could
  keep only three of your edits, which three and why?
  (Usually: the empty state, the primary CTA
  microcopy, the error-state remedy.)
- **Which edits are a designer's job, not a CPO's?**
  Be honest. Did you drift into typography-token
  decisions, color-palette changes, illustration
  requests, motion specification? Those are craft
  depth the designer owns (Lecture 4). Flag the drift.
- **If this were an AI-substrate surface, what trust-
  model strings would you add or edit?** Specific to
  the model's output framing — attribution, "review
  before sending" affordances, regenerate wording,
  error framing when the model refuses or fails.

## Starter guidance

- **If you have never opened Figma, do the Saturday-
  tutorial first.** The exercise is unforgiving if you
  are still learning the tool; the point is the pixel-
  and-string discipline, not the Figma mechanics. Spend
  one Saturday on Figma's own *Getting Started*
  tutorial and a clickable mockup of a product surface
  you already use daily, then come back.
- **Draft the string table before the mockup.** The
  strings surface the surface's thinking — once you
  have written the empty-state headline and the
  primary CTA label, the mockup falls out of them. The
  reverse (mockup first, strings later) is how
  "we'll fix the copy later" starts.
- **Use the real design system.** Component drift is
  more expensive than it looks; a one-off button in a
  Figma file becomes a one-off button in the
  codebase.
- **Prototype the flow, not just the screens.** Wiring
  the states together will surface a navigation
  decision a static mockup hides.
- **Walk the surface yourself.** The pre-ship walk is
  not something you *write about* — it is something
  you *do*. If the surface is real, walk the current
  version this week and let that walk inform the
  mockup.
- **Keep the changelog voice CPO-shaped, not
  engineering-release-note-shaped.** The user is the
  reader. The user does not care which service was
  refactored; they care what they can now do.

## The reviewer's memo

Half a page, written after the Figma mockup, the
microcopy pass, the pre-ship walk checklist, and the
changelog entry. Answer:

- **What did authoring the Figma mockup force you to
  decide that writing the six-pager alone did not?**
  Specific decisions — a hierarchy call, an affordance
  call, a state-coverage addition — that only became
  visible when the components hit the canvas.
- **What proportion of your microcopy edits were about
  renaming a button vs rewriting a whole error flow?**
  The former is cheap and high leverage; the latter
  signals a deeper product-decision gap in the first
  draft.
- **Which Lecture 6 anti-patterns did the exercise
  surface?** Design-debt-in-review, late-microcopy,
  mockup-as-approximate-suggestion — name at least
  one that the first draft would have shipped with if
  the CPO had not run this pass.

## Acceptance criteria

- Surface memo names surface, states, baseline, and
  design-system availability.
- Figma file covers at least three states of the
  surface, uses real components, is prototyped
  (clickable), and is linked in the appendix.
- String table covers every user-facing string on the
  surface, in two columns (first-draft vs CPO edit).
- Microcopy reflection applies all four Lecture 4
  disciplines, with named edits.
- For AI-substrate surfaces, trust-model strings are
  called out specifically.
- Pre-ship walk checklist is dated, named, and covers
  state coverage, string correctness, affordance,
  hierarchy, empty-state teaching, and latency.
- Changelog entry has title / description / screenshot
  / docs link, authored in CPO voice.
- Reviewer's memo answers all three categories of
  edits (what changed, highest-leverage, designer-not-
  CPO drift), and names at least one anti-pattern the
  first draft would have shipped.

## Common failure modes

- **Mockup-without-states.** The Figma shows the
  happy path on three screens and ignores empty,
  error, and loading states. Those are the states
  users meet most often; shipping only the happy path
  is the single most common Lecture 4 miss.
- **Rectangles-labeled-"button."** Draft fidelity so
  low that the engineer has to re-invent the UI.
  Component-drift at origin.
- **Buttons named by action, not outcome.** *"Submit"*,
  *"OK"*, *"Click here"* — the Lecture 4 Discipline-1
  anti-pattern. Rewrite every button to name what the
  user is causing to happen.
- **"Something went wrong"-shaped errors.** Errors
  that diagnose nothing and remedy nothing. Rewrite
  every one.
- **Empty-state-as-gate.** A screen that says *"No
  items"* and does nothing else. Rewrite every one
  into an invitation that teaches the surface.
- **Designer-replacement overreach.** The CPO
  specifying typography tokens, color palette
  changes, custom illustrations, motion curves. These
  are craft depth the designer owns. Pull back.
- **Changelog-as-release-note.** Entries that read
  *"Fixed a bug in the evidence-request module"*
  rather than *"Evidence requests now save
  automatically — you'll never lose a draft."* The
  user is the reader; write for them.
- **Pre-ship walk as QA checklist.** QA is a
  different discipline; the walk is a *product-taste*
  pass. If your checklist tests browser compatibility
  and database schema, you are doing QA, not the
  walk.
- **AI-substrate trust-model strings missing.** For
  LLM-substrate surfaces, strings like *"Generated
  draft"* and *"Review before sending"* are not
  decorative — they set the user's trust model. Not
  having them is a Lecture 5 miss masquerading as a
  Lecture 4 one.

## Source alignment

The "own the pixel" expectation and the
product-minded-designer / design-minded-PM pattern
derive from Marty Cagan with Chris Jones, *Empowered:
Ordinary People, Extraordinary Products*, Wiley, 2020,
especially Chapter 10 —
[svpg.com/empowered](https://www.svpg.com/empowered-ordinary-people-extraordinary-products/).
The affordance / hierarchy / layout disciplines derive
from Don Norman, *The Design of Everyday Things*
(revised), Basic Books, 2013 —
[mitpress.mit.edu/9780262525671](https://mitpress.mit.edu/9780262525671/the-design-of-everyday-things/);
Steve Krug, *Don't Make Me Think, Revisited*, New
Riders, 2014 — [sensible.com/dmmt.html](https://www.sensible.com/dmmt.html);
and Ellen Lupton, *Thinking with Type* (revised),
Princeton Architectural Press, 2010 —
[papress.com/thinking-with-type](https://www.papress.com/products/thinking-with-type).
The microcopy discipline derives from Kinneret Yifrah,
*Microcopy: The Complete Guide*, self-published, 2017 —
[microcopybook.com](https://www.microcopybook.com/);
Mailchimp's *Content Style Guide* —
[styleguide.mailchimp.com](https://styleguide.mailchimp.com/);
and the GOV.UK *Design System content guidance* —
[design-system.service.gov.uk/styles/content](https://design-system.service.gov.uk/styles/content/).
The empty-state-is-the-product discipline is in
Basecamp's *Getting Real* era writing, especially the
"Copywriting is interface design" chapter —
[basecamp.com/gettingreal](https://basecamp.com/gettingreal).
The live-changelog form derives from Basecamp, Linear,
and Notion — see Linear's public changelog at
[linear.app/changelog](https://linear.app/changelog)
and Basecamp's *Signal v. Noise* /
*World of Business* changelog surface at
[basecamp.com/features](https://basecamp.com/features).
