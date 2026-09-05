# Lecture 4 — Free-trial, freemium, reverse-trial: the acquisition-monetization seam

## The setup

Lecture 3 gave you the packaging shape. This lecture is
the choice that sits *on top* of the shape: how does a
new customer first experience the product, and how does
that first experience convert into paid revenue?

At pre-seed / seed for a self-serve product, the
choice is between three entry motions:

- **Free trial** — the customer gets the paid product
  for a bounded window (7 / 14 / 30 days), typically
  the full-featured version, and must convert to
  paid at trial end or lose access.
- **Freemium** — the customer gets a permanently
  free tier with functional limits (feature-gated,
  capacity-gated, or both), and upgrades to paid
  when they want more.
- **Reverse trial** — the customer starts with the
  full paid product for a bounded window, then, at
  trial end, is **automatically downgraded to a
  functional free tier** (rather than losing access).
  Popularized by Wistia and others; documented
  extensively in Kyle Poyar's OpenView writing.

Each shape has a distinct conversion-rate range, a
distinct product-shape requirement, and a distinct
failure mode. Choosing among them by inheritance
("everyone in our category does freemium") is the
single most common pricing-model mistake at pre-seed
/ seed — because the three shapes have very different
implications for the packaging ladder, the sales
motion, and the eng cost of the free surface.

This lecture teaches the choice.

## The three motions, side by side

| Motion | What the user gets at start | What happens at day N | Where it fits |
|---|---|---|---|
| **Free trial** | Full paid product | Access is removed unless they pay | Product delivers value inside the trial window; conversion moment is external forcing (payment) |
| **Freemium** | A permanently-free tier with functional limits | Nothing — user stays on free tier indefinitely until they upgrade | Product has a natural free-tier surface that generates ongoing engagement; upgrade motion is internal (hitting a limit) |
| **Reverse trial** | Full paid product | Auto-downgraded to free tier; user can upgrade back | Product has both a free-tier surface *and* enough paid-only capability that users notice the downgrade |

The choice is not a preference. It's determined by
three product-shape questions:

1. **Does the product deliver its core value within
   a short trial window?** If yes, free trial works.
   If no (the value shows up after weeks of habit
   formation), free trial converts poorly and
   freemium or reverse trial fits better.
2. **Does the product have a natural "free tier"
   surface** — a stripped-down but genuinely useful
   version that can sustain months of use? If yes,
   freemium is viable. If no (the product is only
   useful at full-feature), freemium becomes a
   negative acquisition channel: users bounce off a
   free tier that doesn't do anything.
3. **Does the paid product have "sticky" behaviors
   the user forms during the trial** that they'd
   miss after downgrade? If yes, reverse trial is
   the highest-converting option. If no, reverse
   trial just delays the same conversion moment
   without adding leverage.

## Free trial — when and how

The classic self-serve motion. The customer signs up,
gets the paid product for 14 (or 7, or 30) days, and
must add a credit card and convert to paid before
trial end.

**Fits when**:

- The core value shows up in the first session or two
  (analytics dashboard populated, first document
  processed, first email sent).
- The buyer has authority to make a purchase decision
  in the trial window (self-serve individual or
  small-team buyer, not enterprise procurement).
- The product's cost-to-serve during trial is low
  enough that a high trial-to-paid ratio doesn't
  break unit economics (relevant for AI-substrate
  products where trial inference costs can eat
  gross margin — see
  [Lecture 6](06-ai-product-monetization-models.md)).

**Breaks when**:

- The product requires setup (integrations, data
  import, team invitations) that takes longer than
  the trial window. Users spend the trial
  configuring and never experience the value.
- The buyer is procurement-mediated. Trial windows
  are irrelevant when the purchase decision goes
  through an approval cycle that takes 30–90 days.
- Trial abuse: users create serial accounts to
  extend the trial indefinitely. Common defenses
  (email verification, device fingerprint, credit-
  card requirement) each have UX costs.

**Design choices**:

- **Credit card required or not**. Requiring a card
  raises the *effective* trial-to-paid rate (users
  who add a card have already committed
  psychologically) but lowers the trial *start* rate
  by 40–80%.
  <!-- needs-research: cite specific benchmark on card-required vs. card-not-required trial start rate impact from a primary source (Poyar OpenView or ProfitWell). -->
- **Trial length**. 14 days is the modal choice; 7
  days for products with immediate value, 30 for
  products with longer onboarding. Longer isn't
  usually better — users who don't convert in the
  first week rarely convert.
- **Trial-end handoff**. Automatic conversion (credit
  card charged silently) vs. explicit upgrade
  prompt. Automatic converts higher; explicit
  produces less refund and chargeback risk. Pick
  based on the trust and support cost you can bear.

## Freemium — when and how

The customer gets a permanently-free tier with limits
and can operate on it indefinitely. Common in
consumer-facing tools and bottoms-up B2B (Slack,
Notion, Figma, Dropbox all launched or scale
substantially on freemium).

**Fits when**:

- The product has a natural single-user or small-
  team use case where the free tier is genuinely
  useful (not crippleware).
- The free tier acts as an acquisition channel —
  users invite collaborators (viral loop), share
  outputs (embed loop), or produce artifacts
  visible to non-users (SEO / brand loop) — that
  drives new sign-ups.
- The cost-to-serve of a free user is very low
  (fixed-cost architecture, low inference cost per
  free user). Kyle Poyar has been consistent on this
  point: freemium works when free users are ~free
  to serve. If serving a free user costs $10 / month
  in cloud + LLM inference, the math changes
  fundamentally.

**Breaks when**:

- The free tier is deliberately crippled to force
  upgrade ("crippleware"). Users detect it and
  bounce; brand suffers.
- The free tier serves the same use case as the
  paid tier. The upgrade motion collapses because
  the user has no functional reason to upgrade.
- Cost of serving free users grows non-trivially
  with user count. Common failure mode in AI-
  substrate products where free-tier LLM inference
  is a large fraction of gross-margin cost.
- Free users produce ongoing support load that
  swamps the paid-user support motion.

**Design choices**:

- **Feature-gated vs. capacity-gated free tier**.
  Feature gating (free tier lacks X, Y, Z) is
  transparent but risks crippleware. Capacity
  gating (free tier includes everything, up to N
  events per month) preserves the "real product"
  experience but requires the user to grow into
  the paid tier through use.
- **Upgrade prompt frequency**. Prompt too often and
  the free tier feels adversarial; prompt too
  rarely and you leave upgrades on the table. The
  Poyar / OpenView guidance: prompt at the
  *moment of value* (user hits limit and wants
  more; user needs a paid feature specifically),
  not on a schedule.
- **What signals "ready to convert"**. Product
  telemetry — users hitting the cap, users
  invoking the upgrade prompt, teams growing past a
  threshold. Feeds the *product-qualified lead*
  (PQL) motion that Lecture 5 experiments against.

## Reverse trial — when and how

The customer gets the paid product for a bounded
window (14 / 30 days), and at trial end is
automatically downgraded to a functional free tier
rather than losing access. Popularized by Wistia and
several other prosumer / SMB products, documented
extensively in Kyle Poyar's writing
([Poyar, "The Rise of the Reverse Trial," Growth
Unhinged](https://www.growthunhinged.com/p/the-rise-of-the-reverse-trial)
and follow-ups).

**Fits when**:

- The product supports both a free-tier use case
  *and* a paid-tier use case where paid delivers
  meaningfully more.
- The paid features have "habit formation"
  properties — users who use them for 14 days feel
  the loss when downgraded and convert.
- The team can afford the eng and support cost of
  running both a trial motion and a free tier.

**Breaks when**:

- The product has no meaningful free tier (users
  downgraded to nothing bounce, same as trial
  expiry with no free option).
- The paid features are power-user only. Trial
  users never form habits around them, so the
  downgrade produces no felt loss.
- The downgrade experience is bad — a jarring loss
  of features with a punishing "upgrade or leave"
  screen. The reverse-trial motion's magic is a
  *gentle* downgrade with clear signposts to
  re-upgrade.

**Design choices**:

- **Which features are the "trial exclusives"** —
  the ones users lose access to on downgrade. The
  ones with the highest habit-formation and
  perceived-value should be in this bucket.
- **What downgrade feels like**. Silent (features
  disappear from the UI) vs. loud (a modal on
  first re-entry explaining the change). The Poyar
  literature recommends loud but non-punitive:
  users should know what changed and how to get it
  back.
- **Re-upgrade friction**. Ideally one click; the
  user's payment method should already be on file
  (from trial start) so the re-upgrade is a
  confirmation, not a fresh sign-up.

## The Poyar decision matrix

Kyle Poyar's writing pulls the three-motion choice
into a decision matrix along two axes:

- **Time to value** — how quickly the product
  produces its core value. Short (session 1) vs.
  long (weeks to months).
- **Free-tier viability** — whether the product has
  a natural free-tier use case that stands on its
  own.

The four cells:

|  | **Free tier viable** | **Free tier not viable** |
|---|---|---|
| **Short TTV** | Freemium *or* free trial (choose by cost-to-serve; freemium if free is cheap, free trial if not) | Free trial |
| **Long TTV** | Freemium (with in-product prompts once value shows) *or* reverse trial | Reverse trial or high-touch sales |

The Poyar canon expands with worked examples and the
specific conversion-benchmark ranges each cell tends
to produce. The reading list in
[resources.md](../resources.md) has the specific
essays.

## Common failure modes

Six failure modes across the three motions:

- **Freemium as unpriced free trial.** Team ships a
  free tier that's functionally identical to paid,
  meaning to convert users later. Users never
  convert because they have no reason to.
- **Free trial where TTV > trial length.** 14-day
  trial on a product that takes 21 days to see the
  value. Trial-to-paid conversion catastrophically
  low; team blames the marketing funnel.
- **Reverse trial with no free tier design.** The
  team ships reverse trial without designing the
  downgrade experience. Users get the "your trial
  ended" screen, downgrade to a nominally-free
  tier with no clear utility, and bounce.
- **Cost-blind freemium.** Team runs freemium on an
  AI-substrate product where serving each free user
  costs $5–20 / month in inference. Gross margin
  collapses at scale; the "growth" narrative masks
  the burn.
- **PQL signal ignored.** The team runs freemium
  but doesn't instrument the product-qualified-
  lead signal (users hitting cap, invoking upgrade
  prompt, growing past a threshold). The upgrade
  motion runs as untargeted email blasts rather
  than triggered on high-intent behavior.
- **Trial abuse as a growth channel.** Team accepts
  serial trial signups (same user, different
  emails) as "we're growing" and doesn't measure
  the trial-to-real-user ratio.

## The seam — where acquisition becomes monetization

Regardless of which motion you pick, the *seam* — the
handoff from "user is experiencing the product for
free / in trial" to "user is a paying customer" — is
the most important product surface in the pricing
model. It is where the packaging shape from
Lecture 3, the WTP evidence from Lecture 2, and the
entry motion from this lecture all become one
concrete flow.

Elements of a working seam, drawn across Poyar,
Campbell / ProfitWell, and the Reforge Monetization
program:

- **The upgrade moment is triggered by value, not
  by time.** The user should see the upgrade prompt
  when they hit a limit that matters to them — not
  on a schedule, not on trial-day-12, not on their
  15th login. The Amplitude / Mixpanel analytics
  regime from
  [mod-005](../../mod-005-metrics-experimentation-and-ai-evals/README.md)
  is what makes this measurable.
- **The upgrade flow is short.** One page. Tier
  choice, payment, confirmation. Every additional
  step drops conversion by measurable amounts.
- **The tier defaults are set to compromise.** In a
  good / better / best ladder, the Better tier is
  the default; users must actively pick Good or Best.
- **The re-engagement of lapsed free / expired
  trial users is a program, not a set of emails.**
  Winback flows, in-product prompts on next visit,
  targeted case studies. The program is authored by
  the CPO with marketing; the CPO doesn't delegate
  it wholesale.

## What the CPO does personally

- **Chooses the entry motion.** Freemium / free
  trial / reverse trial. Not by inheritance; by the
  Poyar-matrix reasoning applied to the specific
  product.
- **Designs the free-tier surface** (for freemium or
  reverse trial). Which features are included; what
  the capacity limits are; what the free-tier
  experience feels like when a user hits a limit.
- **Designs the upgrade moment.** When the upgrade
  prompt fires; what it says; what happens after
  the user upgrades.
- **Instruments the PQL / trial-to-paid signal.**
  With the mod-005 analytics regime.
- **Owns the seam.** Every step of the free-to-paid
  handoff is a CPO-owned artifact, iterated on with
  the same discovery / delivery cadence used for
  primary product surfaces.

## What the CPO consumes from marketing and growth

- **Acquisition-channel performance.** SEO, paid,
  content, community. Marketing runs the channels;
  the CPO reads which channels bring users who
  convert vs. which bring users who bounce.
- **Winback and re-engagement copy.** Marketing
  writes the emails and in-product prompt copy
  within the flow shape the CPO gave them.
- **Category-benchmark conversion rates.** Freemium
  → paid, trial → paid by segment and vertical.
  Marketing / research curates; the CPO reads to
  size expectations.

## Boundaries this lecture keeps

- **General product-analytics regime** for
  activation, retention, and cohort curves is
  [mod-005 Lecture 2](../../mod-005-metrics-experimentation-and-ai-evals/lectures/02-analytics-regime-beyond-pmf.md).
  This lecture uses those instruments to define the
  PQL signal; it does not re-teach the analytics.
- **Pricing experiments on the entry motion** — A/B
  a shorter trial, A/B a freemium tier change — is
  [Lecture 5](05-pricing-experiments-and-grandfathering.md).
- **PLG-to-SLG transition** — bringing sales in on
  the largest PQLs, deal-desk qualification, hand-
  offs — is level-30 GTM work owned by
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum).
  The CPO defines the PQL signal; sales runs the
  motion against it.
- **AI-substrate freemium cost-to-serve** and the
  math that makes freemium infeasible on inference-
  heavy products is
  [Lecture 6](06-ai-product-monetization-models.md).

## Takeaways

- **Three entry motions**: free trial, freemium,
  reverse trial. Each has a distinct product-shape
  fit and a distinct failure mode.
- **The choice is determined by two axes** (Poyar):
  time-to-value and free-tier viability. Match the
  motion to the axes; don't pick by category
  inheritance.
- **Freemium works when free users are cheap to
  serve** and the free tier is genuinely useful.
  Fails on crippleware and on cost-heavy AI-
  substrate products.
- **Free trial works when the value shows up inside
  the trial window** and the buyer can convert
  self-serve. Fails on long-onboarding products
  and procurement-mediated deals.
- **Reverse trial works when the paid features have
  habit-formation properties** and the free tier
  is meaningful. Fails without a designed
  downgrade experience.
- **The seam** — the free-to-paid handoff — is a
  CPO-owned product surface. Value-triggered
  upgrade prompts, short upgrade flow, tier
  defaults set to compromise, winback as a program.
- **Common failures**: crippleware freemium, trial
  where TTV > trial length, reverse-trial without a
  designed downgrade, cost-blind freemium on AI-
  substrate, ignored PQL signal, trial abuse
  masquerading as growth.

Lecture 5 turns to **pricing experiments with guard
metrics** — how you'd A/B any of the entry-motion or
packaging changes above without breaking existing
customers or trapping the team with a bad-price
grandfathering situation.
