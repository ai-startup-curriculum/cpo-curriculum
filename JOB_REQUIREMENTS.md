# Founding CPO / Head of Product — Job Requirements

Snapshot of what the 2026 market is asking for, mapped to existing coverage.

- **Sampled:** 47 postings observed 2026-08-07 → 2026-11-05, across Y Combinator
  Work at a Startup, Ashby, Greenhouse, Lever, Techstars, Built In,
  Dynamite Jobs, startup.jobs, Wellfound, YC companies, and SERP-mirrored
  postings.
- **Title mix (fragmented on purpose):** Founding CPO, Founding Product Manager,
  Founding Product Lead, Head of Product (early-stage), VP Product (startup),
  Chief Product Officer (early-stage), Chief Product & Technology Officer.
- **Vertical mix:** AI-native / agentic ~45 %, vertical SaaS ~15 %,
  fintech / payments / onchain ~17 %, health / bio / clinical ~17 %,
  devtools / infra / data ~8 %, plus consumer, cyber, crypto trading,
  logistics.
- **Stage mix:** pre-seed / seed ~43 %, Series A ~32 %, Series B+ ~25 %.
- **Machine copy:** [.aicg/job-requirements.json](.aicg/job-requirements.json).

## Headline for this cycle

The biggest change is in the repo, not the market: **mod-004 (Discovery /
Delivery Cadence)** and **mod-005 (Metrics, Experimentation, and
Eval-Driven Product Decisions)** have both been authored since the 2026-10
cycle, with 6 lectures + 6 exercises and 7 lectures + 6 exercises
respectively. That resolves the only open watch-list escalation from the
last cycle:

- **Theme-02 (AI/LLM-native PM)** is now **retired from the watch-list.**
  The prior-cycle mod-008 escalation required both (a) frequency ≥ 0.60 and
  (b) fold-in had not absorbed the demand. (a) is still met (0.74); (b) is
  demonstrably false — mod-004 lecture-05 (agentic UX iteration loops,
  446 lines), mod-005 lecture-06 (eval-driven decisions, 616 lines),
  lecture-07 (cost / latency / quality Pareto), exercise-04 (LLM eval suite
  authoring with explicit safety / refusal and prompt-injection dimensions,
  420 lines), and exercise-05 (Pareto drill with safety-pass-rate as a
  dimension, 357 lines) cover the signal.
- **Theme-19 (AI governance as a product surface)** watch condition is
  also not triggered. The AND-clause read "frequency ≥ 0.40 AND mod-005 is
  authored *without* explicit governance-eval content." Frequency is 0.40
  (borderline, down from 0.47), but mod-005 ships safety / refusal /
  prompt-injection as named dimensions. The AND fails.

Delta: **zero additions.** See
[.aicg/curriculum-plan-delta.json](.aicg/curriculum-plan-delta.json).

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

| # | Theme | Freq (now) | Δ vs 2026-10 | Primary owner | Coverage |
|---|---|---:|---:|---|---|
| 1 | 0 → 1 discovery and shipping | 35/47 (74 %) | −0.07 | this repo (level 35) | Discovery half covered by [mod-001](lessons/mod-001-customer-discovery-to-pmf/README.md); shipping half now covered by newly authored [mod-004](lessons/mod-004-discovery-delivery-cadence/README.md). |
| 2 | AI/LLM-native product intuition (model capabilities, evals, agentic UX, MCP, cost/latency) | 35/47 (74 %) | −0.07 | this repo (level 35) | **Covered — retired from watch-list.** Authored [mod-004 lecture-05](lessons/mod-004-discovery-delivery-cadence/lectures/05-agentic-ux-iteration-loops.md), [mod-004 exercise-05](lessons/mod-004-discovery-delivery-cadence/exercises/exercise-05-agentic-ux-iteration-loop-drill.md), [mod-005 lecture-06](lessons/mod-005-metrics-experimentation-and-ai-evals/lectures/06-eval-driven-decisions-for-llm-products.md), [mod-005 lecture-07](lessons/mod-005-metrics-experimentation-and-ai-evals/lectures/07-cost-latency-quality-pareto.md), [mod-005 exercise-04](lessons/mod-005-metrics-experimentation-and-ai-evals/exercises/exercise-04-llm-eval-suite-authoring-for-one-agent.md), [mod-005 exercise-05](lessons/mod-005-metrics-experimentation-and-ai-evals/exercises/exercise-05-cost-latency-quality-pareto-drill.md). |
| 3 | Direct partnership with technical CEO / founding-team dynamics | 23/47 (49 %) | −0.01 | this repo (level 35) | Declared pillar *working with founders, eng, and GTM* ([mod-007](lessons/mod-007-working-with-founders-eng-and-gtm), planned). |
| 4 | Technical fluency (read code, reason about architecture / API / infra) | 26/47 (55 %) | −0.01 | this repo (level 35) | Sub-topic of declared [mod-007](lessons/mod-007-working-with-founders-eng-and-gtm). Links to [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum) for architectural depth. |
| 5 | Customer discovery cadence (live conversations, on-site pods) | 26/47 (55 %) | −0.01 | this repo (level 35) | **Fully covered** by [mod-001](lessons/mod-001-customer-discovery-to-pmf/README.md) — lectures 1-2, Exercise B, Lab. |
| 6 | Ambiguity tolerance / self-directed structure-building | 25/47 (53 %) | 0.00 | [startup-foundations](https://github.com/ai-startup-curriculum/startup-foundations) (level 10) | Trait-level competency owned at the lowest level. |
| 7 | Roadmap / prioritization / operating rigor (90–180 day plans) | 33/47 (70 %) | +0.01 | this repo (level 35) | Declared pillars *opportunity assessment & prioritization* ([mod-002](lessons/mod-002-opportunity-assessment-and-prioritization)) and *roadmap and outcomes vs. output* ([mod-003](lessons/mod-003-roadmap-outcomes-and-strategy)). Novellia's "hard calls on what NOT to build" and Turquoise's "defend a domain POV" extend the kill-list discipline for the mod-002 author. |
| 8 | Cross-functional influence (sales / CS / GTM without direct authority) | 32/47 (68 %) | +0.01 | this repo (level 35) | Declared [mod-007](lessons/mod-007-working-with-founders-eng-and-gtm). Citizen's "unify consumer, subscription, enterprise, and API portfolios" and Sentient's "developer communities, technical GTM, ecosystem programs" are the strongest new multi-surface-influence examples. Links to [product & GTM](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum). |
| 9 | Metric definition & analytics rigor (funnel, activation, retention, cohort) | 23/47 (49 %) | +0.02 | this repo (level 35) | **Now covered** by authored [mod-005](lessons/mod-005-metrics-experimentation-and-ai-evals) — exercise-01 (north-star + input metrics), exercise-02 (activation/retention/cohort), exercise-03 (A/B MDE sizing), exercise-06 (SQL against events). [mod-001](lessons/mod-001-customer-discovery-to-pmf) covers PMF-specific metrics. |
| 10 | Vertical / domain expertise | 27/47 (57 %) | −0.04 | — | Candidate-supplied, not curriculum-teachable at level 35. Still high. Turquoise ("peer to a GM/SME" in chargebacks/rebates/gross-to-net), Manta ("oncology depth preferred; clinician/MD-turned-PM a bonus"), and Sava ("chartered trust company, not just software") materially intensify the Day-1 domain-specialist expectation for regulated-vertical first PMs. Flag for VERSIONS.md narrative. |
| 11 | Design taste / IC design work (Figma, microcopy, ship weekly) | 13/47 (28 %) | −0.03 | this repo (level 35) | Just below 0.30 threshold but **covered** by authored [mod-004 exercise-04](lessons/mod-004-discovery-delivery-cadence/exercises/exercise-04-figma-mockup-and-microcopy-drill.md) and [lecture-04](lessons/mod-004-discovery-delivery-cadence/lectures/04-own-the-pixel-figma-and-microcopy.md). |
| 12 | Ship-velocity + weekly cadence | 19/47 (40 %) | +0.01 | this repo (level 35) | **Covered** by authored [mod-004 exercise-06](lessons/mod-004-discovery-delivery-cadence/exercises/exercise-06-ship-velocity-anti-pattern-diagnosis.md) plus Shape Up vs. weekly-kanban choice in exercise-02 / lecture-02. |
| 13 | Growth / PLG loops, pricing & packaging | 12/47 (26 %) | −0.02 | [product & GTM](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum) (level 30) | Below threshold. CPO-specific slice sits in declared [mod-006](lessons/mod-006-pricing-packaging-and-monetization) *pricing & packaging as product* pillar. |
| 14 | Building / hiring the product team | 16/47 (34 %) | −0.02 | [operations & governance](https://github.com/ai-startup-curriculum/startup-operations-governance-curriculum) (level 50) | Above 0.30. Hiring craft primary at level 50 per ownership rule; CPO-specific "first product hire" interviewing patterns remain a candidate exercise for [mod-007](lessons/mod-007-working-with-founders-eng-and-gtm) if frequency climbs further — NOT a new module. |
| 15 | Enterprise / regulated buyer sophistication | 21/47 (45 %) | +0.03 | [product & GTM](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum) (level 30) | Modest rise. Socket (Anthropic/xAI/Figma/Vercel), Sava (chartered trust compliance), Dune (institutional capital markets), Turquoise (life-sciences manufacturers) extend the prior set. Enterprise selling motion owned at level 30; regulated-buyer *product* patterns overlap theme #19 and sit in mod-005 scope. |
| 16 | Platform / API-first / multi-surface product strategy | 13/47 (28 %) | −0.03 | this repo (level 35) | Just below 0.30 this cycle (0.31 → 0.28). Already in-scope for [mod-002](lessons/mod-002-opportunity-assessment-and-prioritization) exercise-03 `multi-surface-ranking-drill` and [mod-003](lessons/mod-003-roadmap-outcomes-and-strategy). |
| 17 | Founder background (prior 0 → 1) | 9/47 (19 %) | 0.00 | [founder-ceo](https://github.com/ai-startup-curriculum/founder-ceo-curriculum) (level 20) | Trait / experience signal; not a level-35 curriculum item. |
| 18 | Board reporting / fundraising narrative | 8/47 (17 %) | 0.00 | [finance & fundraising](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum) (level 40) | Below threshold; primary owner at level 40. |
| 19 | **AI governance / model behavior as a product surface** — hallucination boundaries, prompt-injection defense, auditability, data residency, policy on training on customer data, trustworthy-AI decision boundaries | 19/47 (40 %) | −0.07 | this repo (level 35) | **Covered — watch condition not triggered.** The 2026-10 AND-clause ("frequency ≥ 0.40 AND mod-005 authored without explicit governance-eval content") fails: frequency is 0.40 (borderline), but mod-005 IS authored with explicit governance-eval content — [exercise-04](lessons/mod-005-metrics-experimentation-and-ai-evals/exercises/exercise-04-llm-eval-suite-authoring-for-one-agent.md) names safety/refusal and prompt injection as a required dimension; [lecture-06](lessons/mod-005-metrics-experimentation-and-ai-evals/lectures/06-eval-driven-decisions-for-llm-products.md) names hallucination-rate as an eval metric; [lecture-01](lessons/mod-005-metrics-experimentation-and-ai-evals/lectures/01-north-star-and-input-metric-taxonomy.md) treats trust/safety/policy guardrails as a top-level input-metric category; [lecture-07](lessons/mod-005-metrics-experimentation-and-ai-evals/lectures/07-cost-latency-quality-pareto.md) treats safety-pass-rate as a non-negotiable floor. Data-residency and audit-logs are handled as enterprise-sale gates in [mod-002 exercise-02](lessons/mod-002-opportunity-assessment-and-prioritization/exercises/exercise-02-rice-vs-wsjf-vs-kano-scheme-choice-drill.md) and [mod-006 exercise-01](lessons/mod-006-pricing-packaging-and-monetization/exercises/exercise-01-monetization-model-authoring-for-one-product.md). See [external resources](#external-resources) for depth. <!-- needs-research: next cycle, verify whether postings begin demanding data-residency as a product *promise* (not a sales gate) or policy-on-training-on-customer-data as a product *control* (not a legal clause) — those would be out-of-scope for current coverage --> |
| 20 | **Agent-orchestration / multi-agent product strategy** — owning agentic-workflow quality, agent-vs-human handoff, agent reliability as a product surface | 19/47 (40 %) | +0.07 | this repo (level 35) | **Covered.** Rising (0.33 → 0.40). Authored [mod-004 exercise-05](lessons/mod-004-discovery-delivery-cadence/exercises/exercise-05-agentic-ux-iteration-loop-drill.md) and [lecture-05](lessons/mod-004-discovery-delivery-cadence/lectures/05-agentic-ux-iteration-loops.md) cover it. Mesh (agents on live payment rails), Citizen (AI-agent systems as PM leverage), Keenable (agent-ecosystem fluency), Harper (AI agent architecture), Sentient (Agents & Evaluation team), Revefi (Raden agent) are the strongest new examples. Also folds into mod-007's AI-system-architecture read-through. |

## Candidate theme below threshold

**Principal-IC Head of Product using AI agents as execution leverage.** Four
postings this cycle use language like Citizen's "principal-level IC role —
build AI-agent systems that expand product execution rather than manage a
traditional PM team" (also Keenable, Sentient, prior-cycle Kamiwaza). At
0.09 frequency this is far below the 0.30 evidence threshold. The pattern
is a form of cross-functional influence rather than a distinct competency
area; if it climbs above ~0.20 next cycle, absorbable as a mod-007 exercise
variant ("leverage-via-agents operating model"), **not** a new module.

## What is *not* changing this cycle

Every theme with frequency ≥ 0.30 is now either (a) **covered by authored
modules** (mod-001, mod-004, mod-005), (b) mapped to a
**declared-but-not-yet-authored module** (mod-002, mod-003, mod-006,
mod-007) listed in [CURRICULUM.md](CURRICULUM.md#modules), or (c) **owned
at a lower level** per the ownership rule.

Both watch-list items from the 2026-10 cycle are retired:

- Theme-02 (AI-native PM) watch — retired because mod-004 and mod-005 are
  now authored with the agentic UX + eval-driven content the fold-in
  strategy promised.
- Theme-19 (AI governance as a product surface) watch — the AND-clause
  fails because mod-005 ships explicit governance-eval content (safety /
  refusal, prompt injection, hallucination-rate, trust-pass-rate).

Vertical-SME depth (theme #10, 57 %) and enterprise/regulated buyer
sophistication (theme #15, 45 %) are both intensifying, but neither is
curriculum-teachable at level 35 as general content — both remain
candidate-supplied or owned at level 30.

Delta: **zero additions.** See
[.aicg/curriculum-plan-delta.json](.aicg/curriculum-plan-delta.json).

## External resources

For requirements that are owned by other repos or that need depth beyond
the level-35 scope, learners can consult the following:

**AI-native product management (theme #2)**

- Hamel Husain, "Your AI Product Needs Evals," 2024 —
  [hamel.dev/blog/posts/evals](https://hamel.dev/blog/posts/evals/)
- Anthropic, "Model Context Protocol" specification —
  [modelcontextprotocol.io](https://modelcontextprotocol.io/)
- Simon Willison, prompt-engineering writing index —
  [simonwillison.net/tags/prompt-engineering](https://simonwillison.net/tags/prompt-engineering/)
- Chip Huyen, *AI Engineering* (O'Reilly, 2025) — Chs. 3–5 on evaluation
  and cost/latency trade-offs as product decisions.

**AI governance as a product surface (theme #19)**

- Anthropic, "Responsible Scaling Policy" —
  [anthropic.com/rsp](https://www.anthropic.com/rsp)
- NIST AI Risk Management Framework (AI 100-1) —
  [nist.gov/itl/ai-risk-management-framework](https://nist.gov/itl/ai-risk-management-framework)
- OWASP Top 10 for LLM Applications —
  [owasp.org/www-project-top-10-for-large-language-model-applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
- Simon Willison, prompt-injection writing index —
  [simonwillison.net/tags/prompt-injection](https://simonwillison.net/tags/prompt-injection/)

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

- Uno Wallet — Founding Head of Product —
  [workatastartup.com/jobs/113112](https://www.workatastartup.com/jobs/113112)
- Jobgether (cybersecurity partner) — Head of Product —
  [lever.co/jobgether](https://jobs.lever.co/jobgether/3bd32226-45df-4f85-ae32-e6b783f5bd53)
- Heim Health — Founding Head of Product —
  [builtin.com/heim-health](https://builtin.com/job/founding-head-product/11071967)
- Waystation AI — Head of Product —
  [ashbyhq.com/waystation](https://jobs.ashbyhq.com/waystation/76d6cc6e-293f-4a3a-96a2-87bdb4864614)
- Boam AI — Head of Product —
  [ashbyhq.com/boam](https://jobs.ashbyhq.com/boam/b3831fbb-603a-440f-b79a-ce3dbe9e6387)
- Kamiwaza AI — Principal PM / Head of Product —
  [ashbyhq.com/kamiwaza](https://jobs.ashbyhq.com/kamiwaza/60ddf375-b880-4426-a389-c54fcf2b114c)
- bareinsights — Chief Product Officer —
  [ashbyhq.com/bare](https://jobs.ashbyhq.com/bare/717c0ef5-453a-4d4b-b2b2-d068138ab7b3)
- iCOUNTER — Chief Product Officer —
  [ashbyhq.com/icounter](https://jobs.ashbyhq.com/icounter/1ebd59ba-3a09-4d92-89de-cc9f14c91eea)
- Mercury — Head of Product, Business Banking —
  [greenhouse.io/mercury](https://job-boards.greenhouse.io/mercury/jobs/6106974004)
- DEUNA — Product Head of AI (Agentic Products) —
  [lever.co/deuna](https://jobs.lever.co/deuna/ec4f69ac-f28e-496e-b925-45d21c53e467)
- Payoneer (PAYO Digital Bank) — Head of Product —
  [workopia.io/payoneer](https://workopia.io/jobs/c3986210bb8f32c269d805b168370a82)
- Novellia — Head of Product —
  [ashbyhq.com/novellia](https://jobs.ashbyhq.com/novellia/29b01938-e0f5-410b-b035-ebb40a0d673a)
- Dune — Head of Product —
  [ashbyhq.com/dune](https://jobs.ashbyhq.com/dune/b3fa8dd4-295d-4ddb-ae78-0936c48f3412)
- Mesh — Founding Product Manager, Agentic Commerce —
  [greenhouse.io/mesh](https://job-boards.greenhouse.io/mesh/jobs/5425730008)
- Sava Trust Company — Founding Product Manager —
  [ycombinator.com/sava-trust-company](https://www.ycombinator.com/companies/sava-trust-company/jobs/mFu7om9-founding-product-manager)
- Socket — Head of Product —
  [ashbyhq.com/socket](https://jobs.ashbyhq.com/socket/02c4af15-7ff5-4a4a-a961-cb1a557fb80a)
- Citizen — Head of Product, Applied AI —
  [ashbyhq.com/Citizen](https://jobs.ashbyhq.com/Citizen/ec0690d5-be5e-4e8b-be78-d832f166b242)
- Keenable.ai — Head of Product (Founding) —
  [ashbyhq.com/keenable](https://jobs.ashbyhq.com/keenable/30b1eefb-9288-4d9e-8bad-876c78215152)
- Sentient Foundation — Head of Product —
  [ashbyhq.com/sentient-foundation](https://jobs.ashbyhq.com/sentient-foundation/d95ac1b9-8a1a-4a7a-9997-ff9a3b957e0e)
- Iris Labs (Flagship Pioneering) — Head of Product (Iris Chat) —
  [greenhouse.io/flagship](https://job-boards.greenhouse.io/flagshippioneeringinc/jobs/8843628002)
- Harper — Founding Product Manager —
  [workatastartup.com/88615](https://www.workatastartup.com/jobs/88615)
- Manta Cares — Head of Product —
  [ashbyhq.com/mantacares](https://jobs.ashbyhq.com/mantacares/81f1944d-3878-41e7-ac87-61813c4a9661)
- Turquoise Health — Founding Product Manager, Life Sciences —
  [ashbyhq.com/turquoise](https://jobs.ashbyhq.com/turquoise-health/f7183632-4e65-4e1a-9d82-8d62cfc5eee3)
- Revefi — Founding Product Manager —
  [lever.co/revefi](https://jobs.lever.co/revefi/12f9922a-7dec-4567-9541-7260222ca258)

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
