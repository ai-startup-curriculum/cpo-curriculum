# Founding CPO / Head of Product — Job Requirements

Snapshot of what the 2026 market is asking for, mapped to existing coverage.

- **Sampled:** 32 postings observed 2026-06-07 → 2026-09-05, across Y Combinator
  Work at a Startup, Ashby, Greenhouse, Lever, Techstars, Built In,
  Dynamite Jobs, and startup.jobs.
- **Title mix (fragmented on purpose):** Founding CPO, Founding Product Manager,
  Founding Product Lead, Head of Product (early-stage), VP Product (startup),
  Chief Product Officer (early-stage).
- **Vertical mix:** AI-native / agentic ~40 %, vertical SaaS ~20 %,
  fintech ~15 %, health / bio ~15 %, devtools / infra ~10 %, plus consumer,
  marketplace, resale, industrial AI.
- **Stage mix:** pre-seed / seed ~55 %, Series A ~30 %, Series B ~15 %.
- **Machine copy:** [.aicg/job-requirements.json](.aicg/job-requirements.json).

## Ownership rule reminder

If a requirement genuinely belongs to more than one role, primary coverage
goes to the **lowest-level role** where it is required. Higher-level roles
link to that owner unless they need extra depth, architecture context, or
leadership framing. Levels used below:

- 10 Startup Foundations · 20 Founder / CEO · 25 Co-Founder / CTO
- 30 Startup Product & GTM · **35 Founding CPO / Head of Product (this repo)**
- 40 Startup Finance & Fundraising · 50 Startup Operations & Governance
- 60 Startup Exit & Endgame

## Requirement themes → coverage

| # | Theme | Frequency | Primary owner | Coverage |
|---|---|---:|---|---|
| 1 | 0 → 1 discovery and shipping | 26 / 32 (81 %) | this repo (level 35) | Discovery half covered by [mod-001](lessons/mod-001-customer-discovery-to-pmf/README.md); shipping half maps to declared *discovery/delivery cadence* module (pipeline oldest-gap-first). Level-30 [product & GTM](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum) owns base mechanics. |
| 2 | AI/LLM-native product intuition (model capabilities, evals, agentic UX, MCP, cost/latency) | 21 / 32 (66 %) | this repo (level 35) | **Watch-list.** Not covered by any existing module. Emerging 2026 competency — fold into declared *metrics & experimentation* (eval-driven decisions) and *discovery/delivery cadence* (agentic UX iteration) modules when authored. Not a standalone gap this cycle. See [external resources](#external-resources) below. <!-- needs-research: verify whether declared modules absorb this cleanly once authored; escalate to a standalone module proposal next cycle if frequency ≥ 0.60 persists --> |
| 3 | Direct partnership with technical CEO / founding-team dynamics | 18 / 32 (56 %) | this repo (level 35) | Declared pillar *working with founders, eng, and GTM* — pipeline will author. |
| 4 | Technical fluency (read code, reason about architecture / API / infra) | 17 / 32 (53 %) | this repo (level 35) | Sub-topic of the declared *working with founders, eng, and GTM* module. Links to [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum) for architectural depth. |
| 5 | Customer discovery cadence (live conversations, on-site pods) | 16 / 32 (50 %) | this repo (level 35) | **Fully covered** by [mod-001](lessons/mod-001-customer-discovery-to-pmf/README.md) — lectures 1-2, Exercise B, Lab. |
| 6 | Ambiguity tolerance / self-directed structure-building | 15 / 32 (47 %) | [startup-foundations](https://github.com/ai-startup-curriculum/startup-foundations) (level 10) | Trait-level competency owned at the lowest level. |
| 7 | Roadmap / prioritization / operating rigor | 15 / 32 (47 %) | this repo (level 35) | Declared pillars *opportunity assessment & prioritization* and *roadmap and outcomes vs. output* — pipeline will author. |
| 8 | Cross-functional influence (sales / CS / GTM without direct authority) | 14 / 32 (44 %) | this repo (level 35) | Declared pillar *working with founders, eng, and GTM*. Links to [product & GTM](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum) for GTM-side mechanics. |
| 9 | Metric definition & analytics rigor (funnel, activation, retention, cohort) | 12 / 32 (38 %) | this repo (level 35) | Declared pillar *metrics & experimentation*. [mod-001](lessons/mod-001-customer-discovery-to-pmf/README.md) already covers PMF-specific metrics; broader funnel/cohort/experiment discipline sits in the not-yet-authored module. |
| 10 | Vertical / domain expertise | 12 / 32 (38 %) | — | Candidate-supplied, not curriculum-teachable. |
| 11 | Design taste / IC design work (Figma, microcopy, ship weekly) | 10 / 32 (31 %) | this repo (level 35) | Naturally sits inside the declared *discovery/delivery cadence* module. If the eventual author omits it, revisit as a candidate exercise. |
| 12 | Ship-velocity + weekly cadence | 10 / 32 (31 %) | this repo (level 35) | Declared pillar *discovery/delivery cadence*. |
| 13 | Growth / PLG loops, pricing & packaging | 9 / 32 (28 %) | [product & GTM](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum) (level 30) | Below threshold. CPO-specific slice sits in declared *pricing & packaging as product* pillar. |
| 14 | Building / hiring the product team | 8 / 32 (25 %) | [operations & governance](https://github.com/ai-startup-curriculum/startup-operations-governance-curriculum) (level 50) | Below threshold; primary owner at level 50. |
| 15 | Enterprise / regulated buyer sophistication | 8 / 32 (25 %) | [product & GTM](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum) (level 30) | Below threshold; owned at level 30. |
| 16 | Platform / API-first / multi-surface product strategy | 8 / 32 (25 %) | this repo (level 35) | Below threshold. Fold into declared roadmap / prioritization pillars. |
| 17 | Founder background (prior 0 → 1) | 7 / 32 (22 %) | [founder-ceo](https://github.com/ai-startup-curriculum/founder-ceo-curriculum) (level 20) | Trait / experience signal; not a level-35 curriculum item. |
| 18 | Board reporting / fundraising narrative | 4 / 32 (13 %) | [finance & fundraising](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum) (level 40) | Below threshold; primary owner at level 40. |

## What is *not* changing this cycle

Every theme above with frequency ≥ 0.30 is either **covered by mod-001** or
maps to a **declared-but-not-yet-authored pillar module** listed in
[CURRICULUM.md](CURRICULUM.md#product-modules-this-repo-owns). The autonomous
research → author pipeline authors those oldest-gap-first, so proposing them
here would double the work.

The one genuinely emerging competency — **AI/LLM-native product management**
(66 %) — is not covered anywhere yet. However, it can be absorbed cleanly into
the declared *metrics & experimentation* and *discovery/delivery cadence*
modules when they are authored. Adding a standalone module in this cycle would
preempt the declared pathway and violate continuity bias. It goes on the
watch-list; if frequency holds ≥ 0.60 next cycle and the declared modules do
not absorb it, escalate to a proposal.

Delta: **zero additions**. See
[.aicg/curriculum-plan-delta.json](.aicg/curriculum-plan-delta.json).

## External resources

For requirements that are owned by other repos or that fall in the watch-list
gap, learners can consult the following while the pipeline catches up:

**AI-native product management (theme #2)**

- Hamel Husain, "Your AI Product Needs Evals," 2024 —
  [hamel.dev/blog/posts/evals](https://hamel.dev/blog/posts/evals/)
- Anthropic, "Model Context Protocol" specification —
  [modelcontextprotocol.io](https://modelcontextprotocol.io/)
- Simon Willison, prompt-engineering writing index —
  [simonwillison.net/tags/prompt-engineering](https://simonwillison.net/tags/prompt-engineering/)
- Chip Huyen, *AI Engineering* (O'Reilly, 2025) — Chs. 3–5 on evaluation and
  cost/latency trade-offs as product decisions.

**Design taste at early stage (theme #11)**

- Ryan Singer, *Shape Up* (Basecamp) —
  [basecamp.com/shapeup](https://basecamp.com/shapeup)
- Julie Zhuo, *The Making of a Manager*, Portfolio, 2019.
- First Round Review, "Behind the Design" series —
  [review.firstround.com](https://review.firstround.com/).

## Sampled postings

Full posting list — with employer, title, URL, date, location, stage, and
extracted requirements — is in
[.aicg/job-requirements.json](.aicg/job-requirements.json) under the
`postings` array. A short selection:

- Clearly AI — Founding Head of Product —
  [workatastartup.com/jobs/95102](https://www.workatastartup.com/jobs/95102)
- Uare.ai — Head of Product —
  [greenhouse.io/uareai/4186970009](https://job-boards.greenhouse.io/uareai/jobs/4186970009)
- Harper — Founding Product Manager —
  [ycombinator.com/companies/harper](https://www.ycombinator.com/companies/harper/jobs/KfC6DN6-founding-product-manager)
- Solidroad — Founding Product Manager —
  [ashbyhq.com/solidroad](https://jobs.ashbyhq.com/solidroad/86d91276-6115-4d1b-b5f3-ac65a3ec7b0d)
- Reducto — Founding Product Manager —
  [ashbyhq.com/reducto](https://jobs.ashbyhq.com/reducto/64088355-5fe7-44b2-86d8-0cfba391f052)
- Viz.ai — Chief Product Officer —
  [dynamitejobs.com/company/vizai](https://dynamitejobs.com/company/vizai/remote-job/chief-product-officer)
- Archive — Head of Product —
  [ashbyhq.com/archive](https://jobs.ashbyhq.com/archive/cb7678cf-44db-4aec-9c6e-5891a1e7be12)
- commercetools — Head of Product, Agentic Offerings —
  [startup.jobs/…commercetools](https://startup.jobs/head-of-product-agentic-offerings-commercetools-8059257)
- Stitch Money — Head of Product —
  [greenhouse.io/stitch](https://job-boards.greenhouse.io/stitchinternalreferrals/jobs/4384921101)
- AI Fund — Founding Product Director —
  [lever.co/AIFund](https://jobs.lever.co/AIFund/d158698f-39a3-497d-8ed8-94e3f8a3c0ec)

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
