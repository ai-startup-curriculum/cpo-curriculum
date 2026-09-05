# Lecture 7 — Enterprise DPA, zero-retention, on-prem as a packaging tier

## The setup

The last four lectures have treated packaging as
tiers with feature gates and capacity gates. This
lecture is about a specific class of gate that
matters disproportionately for AI-substrate products
selling into enterprise: **the deployment / data
handling / compliance tier**.

Enterprise buyers evaluating an AI-substrate product
ask a set of questions that self-serve buyers do not
ask, and that most SaaS security programs are not
initially set up to answer:

- Where does customer data go when it hits your
  system?
- Does it flow through third-party model providers
  (Anthropic, OpenAI, Google)? Under what data
  processing terms?
- How long is the data retained by you? By the
  model provider?
- Is customer data used to train models? Yours or
  the provider's?
- What certifications do you have (SOC 2, ISO
  27001, HIPAA, FedRAMP)?
- Can you deploy in the customer's own cloud
  account, VPC, or on-prem?

Each question corresponds to a *product surface* —
data-flow diagram, DPA text, zero-retention
architecture, deployment mode — that the CPO can
gate to a higher packaging tier. Together they form
the **enterprise DPA / zero-retention / on-prem
gating** surface: the specific mechanisms by which
you charge enterprise customers materially more than
mid-market customers for the same core product.

This lecture teaches the vocabulary and the CPO's
decision surface. The actual legal text (DPA
clauses, MSA language, indemnification wording) is
counsel's job.

## What the enterprise buyer is really buying

At self-serve, the buyer is buying the product's
functional capability — the interface, the workflow,
the feature set. At enterprise, the buyer is buying
the *functional capability plus a compliance-ready
wrapping* they can present to their security team,
their procurement team, and — increasingly —
their AI governance function.

The wrapping typically includes:

- **A signed DPA (Data Processing Agreement)** —
  contract language specifying what data you
  process, on what basis, with what
  subprocessors, under what data-transfer
  mechanisms (SCCs for EU transfers, DPF, etc.).
- **A signed MSA** with enterprise-appropriate
  terms — indemnification, limitation of liability
  at a real dollar cap, IP ownership language,
  auditability, insurance requirements.
- **A security certification** — SOC 2 Type II is
  the modal minimum; ISO 27001, HIPAA BAA,
  FedRAMP for regulated verticals.
- **Data-handling commitments** — encryption at
  rest and in transit, access controls, retention
  policies, deletion on request, right-to-audit.
- **AI-specific data commitments** — no training
  on customer data, model-provider zero-retention
  routing, transparency on which upstream models
  process the data.
- **Deployment options** — SaaS in your cloud (the
  default), SaaS in the customer's cloud (VPC /
  private cloud deployment), on-prem (air-gapped
  or connected).

Each element is a packaging lever: it can be
included in the standard offering or gated to a
higher tier. The founding CPO's job is to decide
which of these belong in which tier.

## The AI-specific data-flow question

Traditional SaaS DPA reasoning covers data going
into your systems and being stored in your database.
AI-substrate SaaS DPA reasoning has to cover an
additional flow: data going from your systems into
a third-party model provider (Anthropic, OpenAI,
Google, an open-model runtime), being processed
there, and — depending on the provider and the
account tier — potentially being retained,
inspected, or used for training.

The three data-flow patterns:

- **Passthrough.** Customer data leaves your
  system, hits the model provider's inference
  endpoint, is processed, response returns, and
  the provider *does* retain the request/response
  for some period (typically 30 days for abuse
  monitoring) unless explicitly opted out. The
  default at self-serve tiers of most model
  providers.
- **Zero-retention.** Customer data leaves your
  system, hits the model provider's zero-retention
  inference endpoint, is processed, response
  returns, and the provider *does not* retain the
  request/response. Available at Anthropic
  ([Anthropic Trust Center, "Data usage and
  retention"](https://www.anthropic.com/trust)),
  OpenAI ([OpenAI trust portal](https://trust.openai.com/)),
  and Google Cloud ([cloud.google.com/security/compliance](https://cloud.google.com/security/compliance)),
  typically as a feature of the enterprise API
  tier.
- **Customer-hosted inference.** Customer data
  never leaves the customer's environment; model
  runs in the customer's cloud (via BYOC
  deployment or an on-prem model). Highest
  compliance guarantee; highest deployment
  complexity.

The enterprise buyer's data governance function
increasingly asks specifically which pattern you
run for their data. "Yes, we use OpenAI" is not the
same answer as "we use OpenAI's zero-retention
endpoint under a signed DPA with them." The former
is a red flag; the latter is a green light.

## What the CPO gates to higher tiers

A working founding-CPO DPA / deployment ladder,
drawn across public enterprise-vs-team plan pages
of major AI vendors:

### Free / Team tier

- Standard DPA (self-serve, click-through).
- No custom terms.
- Model providers on their standard retention (30
  days for abuse monitoring; customer data
  potentially used for training on some providers'
  free / consumer tiers, though most business API
  tiers now default to no-training).
- SOC 2 Type II may be available on request but
  usually not part of the tier.

### Business / Growth tier

- Signed DPA with the standard clauses.
- SOC 2 Type II report available under NDA.
- Zero-retention model routing available for AI
  features that touch customer content (or should
  be — this is a packaging decision).
- Enterprise SSO, role-based access control, audit
  log.
- No training on customer data (a commitment your
  DPA should make explicit).

### Enterprise tier

- Customer-redlineable MSA with real liability
  cap and indemnification.
- Custom DPA terms per customer (data residency,
  subprocessor consent, notification windows).
- ISO 27001, HIPAA BAA where relevant,
  vertical-specific certifications.
- Zero-retention model routing as a hard commitment
  in contract.
- Optional VPC / BYOC deployment.
- Named security contact, quarterly security
  reviews.
- SLA guarantees with real credits.

### Dedicated / on-prem tier (highest)

- All of Enterprise, plus:
- Deployment in customer's cloud account or on-prem
  hardware, sometimes air-gapped.
- Customer-provided model (if the customer has
  their own Azure OpenAI subscription, Bedrock
  account, or on-prem model — the product uses
  the customer's inference rather than yours).
- Higher price point reflecting the operational
  cost of supporting per-customer deployments.

The gates: each successive tier adds security and
compliance commitments that either cost you money
(certification maintenance, dedicated security
staff), constrain your operations (you can't ship
features that break the DPA promise), or add
operational complexity (per-customer VPC
deployments are not free to run). Higher tier
prices reflect those costs plus the willingness-to-
pay premium enterprise buyers place on compliance.

## The "SOC 2 as pricing lever" pattern

A specific packaging move worth naming: the
**SOC 2 gate**. Many founding CPOs treat the SOC 2
Type II certification as a company-wide artifact
available to any customer who asks. That's
reasonable at pre-seed / seed. Once the company is
past seed and enterprise deals are on the table, a
better packaging move is:

- **SOC 2 Type II is available as a downloadable
  artifact only to customers on Business tier or
  above.** Below that, customers can see the
  attestation exists (a badge on the site), but
  not download the report.
- **Custom security reviews (extended
  questionnaires, video calls with the security
  team) are Enterprise-only.** Below that,
  customers get the standard security package.
- **Custom DPA and MSA redlines are Enterprise-
  only.** Below that, customers accept the
  click-through DPA or don't buy.

The economics: SOC 2 audits are non-trivial (tens
to hundreds of thousands of dollars per year in
audit and remediation costs); dedicated security
staff to handle enterprise reviews is a real
headcount cost; custom redlines burn legal cycles.
Gating them to tiers that pay for the overhead is
consistent with the value-based pricing framing
from
[Lecture 6](06-ai-product-monetization-models.md).

## The AI-specific DPA additions

Beyond the standard DPA clauses, AI-substrate
products face a specific set of AI-related
questions enterprise buyers now include in their
security reviews. The DPA (or DPA addendum) should
address:

- **Subprocessor list including model providers.**
  Anthropic, OpenAI, Google, and any open-model
  hosting providers appear as named subprocessors.
- **Training on customer data.** Explicit
  commitment (typically "no"): we do not train
  our models on your data; our upstream model
  providers do not train their models on your
  data under our arrangement with them.
- **Data retention windows** at each layer: your
  systems, model-provider systems (zero-retention
  if applicable), embedding / vector-store
  retention.
- **Data residency**. Where the data physically
  sits. AI-substrate products often need to
  disclose that the model provider may process
  data in specific regions, and enterprise
  customers may require in-region processing
  (Anthropic, OpenAI, Google all offer regional
  API endpoints at enterprise tiers).
- **Auditability**. Right for the customer's
  security team to audit your controls, typically
  once per year on reasonable notice.
- **Notification on prompt-injection or model-
  provider incidents.** Enterprise customers
  increasingly want to be told if their data
  triggered a security event at a model provider.

The exact contract language is counsel-authored; the
CPO's job is to know what commitments the packaging
tier makes so counsel can write to it.

## When to build the enterprise packaging tier

A common founding-CPO mistake: standing up the full
enterprise packaging tier (custom DPA, SOC 2,
Enterprise SKU, dedicated CSM) before there are
enterprise buyers to buy it. The build cost is
substantial and the maintenance cost is ongoing;
prematurely investing there starves the mid-market
motion.

The Kyle Poyar / OpenView guidance, plausible at
seed and early Series A: **build enterprise
packaging in response to demand, not in
anticipation of it.** Signals it's time:

- **Three or more inbound enterprise prospects** who
  need SOC 2, custom DPA, or BYOC deployment,
  each representing $100k+ ARR.
- **Deal-cycle friction on the largest deals** —
  enterprise procurement rejecting your standard
  MSA, security teams rejecting your standard
  DPA. Deals stalling for compliance reasons
  rather than product reasons.
- **A commercial motion** — an SDR team, an AE, a
  head of sales — capable of running enterprise
  sales cycles. Building the tier without the
  motion is building a product surface no one
  can sell.

The counter-signal: **no enterprise prospects, all
mid-market self-serve.** Enterprise packaging for a
product with no enterprise pull is a distraction.
Stay focused on the self-serve motion; build
enterprise packaging when the demand is real.

## The public-price / contact-sales split

A specific packaging decision that recurs: does the
enterprise tier have a public price, or is it
"contact sales"?

- **Public price** on Enterprise tier. Transparent;
  works for products with relatively standardized
  enterprise offerings (e.g., a per-seat premium
  plan). Reduces sales cycle friction; allows
  procurement to compare vendors without a call.
  Common at high-volume self-serve companies
  scaling into enterprise.
- **"Contact sales"** on Enterprise tier. Standard.
  Allows per-deal negotiation on pricing, terms,
  SLA, deployment. Slows the sales cycle
  slightly but preserves margin and flexibility.
  Common at classic enterprise SaaS and most
  AI-substrate products with custom deployment
  needs.

The founding-CPO default: **"contact sales" on
Enterprise for the first two years**, then re-
evaluate. A public enterprise price constrains you
too early; hiding the price behind a call lets you
adapt as the deals teach you what enterprise buyers
actually want to pay.

## Common failure modes

Six failure modes that recur across founding-CPO
enterprise-tier attempts:

- **Premature enterprise packaging.** Team builds
  SOC 2, custom DPA, Enterprise tier, and CSM
  program at seed, before there are enterprise
  prospects. Six months of eng and legal cost
  with no enterprise revenue to show for it.
- **Free enterprise features.** Team gives away
  SSO, audit log, custom DPA, and SOC 2 access
  to any customer who asks, without moving them
  to Enterprise tier. Enterprise gets its
  features without paying enterprise prices;
  ARPU stays low.
- **DPA promises the product can't keep.** Sales
  signs a DPA that commits to zero-retention on
  model calls, but the product routes through a
  passthrough endpoint. Legal exposure and
  customer-trust break when discovered.
- **Certification without operational discipline.**
  Team gets SOC 2 Type II attestation, then
  operates in ways that would fail the next
  audit (access controls slip, log retention
  slips). The next audit produces qualified
  opinion; enterprise deals stall.
- **AI-specific DPA absent.** Standard SaaS DPA
  signed without AI-specific additions (model
  provider subprocessors, training commitments,
  zero-retention terms). Enterprise buyer's AI
  governance team catches it; deal stalls.
- **On-prem promised, not designed.** Team
  promises on-prem deployment to close a large
  deal, then discovers the product architecture
  can't run air-gapped. Multi-quarter eng
  investment to unblock the deal already signed.

## What the CPO does personally

- **Owns the DPA / deployment ladder.** Which
  tier includes what data-handling commitments,
  what deployment options, what certifications.
- **Reads the enterprise-deal blockers.** In the
  first year of enterprise sales, the CPO
  personally reviews the deals that stall on
  compliance — what specific term, what
  specific missing feature, what specific DPA
  clause. Feeds packaging revisions.
- **Sets the "contact sales" vs. public-price
  policy** on the top tier.
- **Owns the "training on customer data"
  commitment.** Product decision — do you or
  don't you — with contract implications.
- **Sanity-checks the enterprise-tier price**
  against WTP evidence (Lecture 2) and the
  operational cost of maintaining the tier.

## What the CPO consumes from legal, security, and sales

- **DPA and MSA text.** Counsel drafts; the CPO
  reads to check the commitments match the
  packaging.
- **SOC 2 audit findings.** The security lead or
  CTO owns the certification program; the CPO
  reads the findings to know which packaging
  commitments are safe to make.
- **Model-provider trust program details.**
  Anthropic's, OpenAI's, and Google's trust
  centers publish the standard commitments and
  the enterprise-only upgrades. The CPO reads
  these directly and updates the packaging when
  they change.
- **Enterprise-deal-cycle friction reports.**
  Sales reports which prospects stall on which
  compliance terms; the CPO reads for packaging
  signal.

## Boundaries this lecture keeps

- **Legal contract language** — the actual DPA
  clauses, MSA wording, indemnification
  language — is counsel's job. The CPO knows what
  commitments each tier makes; counsel writes
  the language.
- **Security operations** — running the SOC 2
  program, managing access controls, incident
  response, subprocessor management — is CTO /
  security-lead work owned by
  [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum)
  at level 25. The CPO defines what the tier
  commits to; security operates it.
- **Enterprise sales cycle mechanics** — how the
  procurement conversation goes, how the
  security review runs, how the MSA gets
  redlined — is level-30 GTM work owned by
  [startup-product-gtm-curriculum](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum).
- **AI governance at depth** — the AI-safety and
  compliance framework, model risk management,
  the EU AI Act and similar regulatory regimes at
  operational depth — is
  [chief-ai-officer-learning](https://github.com/ai-governance-curriculum/chief-ai-officer-learning)
  and similar level-70 governance curricula.
  This lecture teaches the *packaging surface*
  the CPO gates; the governance framework itself
  is elsewhere.

## Takeaways

- **Enterprise packaging is a compliance-and-
  deployment tier**, not just a feature tier. DPA
  signature, MSA redline rights, SOC 2 access,
  zero-retention model routing, VPC / on-prem
  deployment.
- **AI-substrate products have an extra data-flow
  question**: where does customer data go at the
  model provider? Passthrough vs. zero-retention
  vs. customer-hosted. Enterprise buyers now ask
  this specifically.
- **Gate compliance features to tiers that pay for
  them.** SOC 2 report, custom DPA, custom MSA,
  BYOC deployment — each has real costs; each
  should live in a tier priced to cover them.
- **AI-specific DPA clauses** — subprocessor list,
  training commitments, retention windows, data
  residency, incident notification — are standard
  now for enterprise AI-product deals.
- **Build enterprise packaging in response to
  demand.** Three inbound enterprise prospects
  representing $100k+ ARR each is a signal;
  no prospects at all means don't build the tier
  yet.
- **"Contact sales" default on Enterprise** for
  the first two years; re-evaluate as the deal
  patterns stabilize.
- **Six common failures**: premature enterprise
  packaging, free enterprise features, DPA
  promises the product can't keep, certification
  without operational discipline, missing AI-
  specific DPA additions, on-prem promised
  before designed.

This lecture ends the module. Return to the
[README](../README.md) for the deliverables and
exercises that pull the seven lectures together
against a real (or plausible) product.
