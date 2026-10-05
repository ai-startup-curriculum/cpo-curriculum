# Founding CPO / Head of Product — Job Requirements

Snapshot of what the 2026 market is asking for, mapped to existing coverage.

- **Sampled:** 36 postings observed 2026-07-07 → 2026-10-05, across Y Combinator
  Work at a Startup, Ashby, Greenhouse, Lever, Techstars, Built In,
  Dynamite Jobs, startup.jobs, Wellfound, and SERP-mirrored postings.
- **Title mix (fragmented on purpose):** Founding CPO, Founding Product Manager,
  Founding Product Lead, Head of Product (early-stage), VP Product (startup),
  Chief Product Officer (early-stage), Chief Product & Technology Officer.
- **Vertical mix:** AI-native / agentic ~45 %, vertical SaaS ~15 %,
  fintech / payments ~15 %, health / bio ~15 %, devtools / infra ~5 %,
  plus consumer, marketplace, logistics, cyber, trading.
- **Stage mix:** pre-seed / seed ~45 %, Series A ~30 %, Series B+ ~25 %.
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

| # | Theme | Freq (now) | Δ vs 2026-09 | Primary owner | Coverage |
|---|---|---:|---:|---|---|
| 1 | 0 → 1 discovery and shipping | 29/36 (81 %) | — | this repo (level 35) | Discovery half covered by [mod-001](lessons/mod-001-customer-discovery-to-pmf/README.md); shipping half maps to declared *discovery/delivery cadence* module (mod-004, planned). Level-30 [product & GTM](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum) owns base mechanics. |
| 2 | AI/LLM-native product intuition (model capabilities, evals, agentic UX, MCP, cost/latency) | 29/36 (81 %) | +0.15 | this repo (level 35) | **Watch-list.** Now universal in the sample. Fold-in strategy from 2026-09 still correct — [mod-005](lessons/mod-005-metrics-experimentation-and-ai-evals) (eval-driven decisions) + [mod-004](lessons/mod-004-discovery-delivery-cadence) (agentic UX iteration) own it. Both still planned, not authored. Escalation condition (a) frequency ≥ 0.60 is met; condition (b) fold-in gap cannot be measured until authoring happens. See [external resources](#external-resources). <!-- needs-research: re-evaluate theme-02 escalation the moment mod-004 and mod-005 are authored --> |
| 3 | Direct partnership with technical CEO / founding-team dynamics | 18/36 (50 %) | −0.06 | this repo (level 35) | Declared pillar *working with founders, eng, and GTM* ([mod-007](lessons/mod-007-working-with-founders-eng-and-gtm), planned). |
| 4 | Technical fluency (read code, reason about architecture / API / infra) | 20/36 (56 %) | +0.03 | this repo (level 35) | Sub-topic of declared [mod-007](lessons/mod-007-working-with-founders-eng-and-gtm). Links to [cto-curriculum](https://github.com/ai-startup-curriculum/cto-curriculum) for architectural depth. |
| 5 | Customer discovery cadence (live conversations, on-site pods) | 20/36 (56 %) | +0.06 | this repo (level 35) | **Fully covered** by [mod-001](lessons/mod-001-customer-discovery-to-pmf/README.md) — lectures 1-2, Exercise B, Lab. |
| 6 | Ambiguity tolerance / self-directed structure-building | 19/36 (53 %) | +0.06 | [startup-foundations](https://github.com/ai-startup-curriculum/startup-foundations) (level 10) | Trait-level competency owned at the lowest level. |
| 7 | Roadmap / prioritization / operating rigor (90–180 day plans) | 25/36 (69 %) | **+0.22** | this repo (level 35) | Declared pillars *opportunity assessment & prioritization* ([mod-002](lessons/mod-002-opportunity-assessment-and-prioritization)) and *roadmap and outcomes vs. output* ([mod-003](lessons/mod-003-roadmap-outcomes-and-strategy)). Table-stakes operating-cadence vocabulary (Waystation, Kamiwaza, bareinsights, ZIRO) is now explicit — flag for mod-002/mod-003 authors. |
| 8 | Cross-functional influence (sales / CS / GTM without direct authority) | 24/36 (67 %) | **+0.23** | this repo (level 35) | Declared pillar [mod-007](lessons/mod-007-working-with-founders-eng-and-gtm). More postings now call out explicit PMM / sales-enablement ownership (bareinsights, iCOUNTER) — flag for the mod-007 author. Links to [product & GTM](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum) for GTM-side mechanics. |
| 9 | Metric definition & analytics rigor (funnel, activation, retention, cohort) | 17/36 (47 %) | +0.09 | this repo (level 35) | Declared [mod-005](lessons/mod-005-metrics-experimentation-and-ai-evals). [mod-001](lessons/mod-001-customer-discovery-to-pmf) already covers PMF-specific metrics. |
| 10 | Vertical / domain expertise | 22/36 (61 %) | **+0.23** | — | Candidate-supplied, not curriculum-teachable. Market is less tolerant of pure-generalist 0→1 chops this cycle. |
| 11 | Design taste / IC design work (Figma, microcopy, ship weekly) | 11/36 (31 %) | — | this repo (level 35) | Sits inside declared [mod-004](lessons/mod-004-discovery-delivery-cadence) — exercise-04 `figma-mockup-and-microcopy-drill`. |
| 12 | Ship-velocity + weekly cadence | 14/36 (39 %) | +0.08 | this repo (level 35) | Declared [mod-004](lessons/mod-004-discovery-delivery-cadence) — lab-01 `run-a-one-week-ship-cycle-end-to-end`. |
| 13 | Growth / PLG loops, pricing & packaging | 10/36 (28 %) | — | [product & GTM](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum) (level 30) | Below threshold. CPO-specific slice sits in declared [mod-006](lessons/mod-006-pricing-packaging-and-monetization) *pricing & packaging as product* pillar. |
| 14 | Building / hiring the product team | 13/36 (36 %) | +0.11 | [operations & governance](https://github.com/ai-startup-curriculum/startup-operations-governance-curriculum) (level 50) | Crossed 0.30 this cycle. Hiring craft primary at level 50 per ownership rule; CPO-specific 'first product hire' interviewing patterns remain a candidate exercise for [mod-007](lessons/mod-007-working-with-founders-eng-and-gtm) if frequency climbs further — NOT a new module. |
| 15 | Enterprise / regulated buyer sophistication | 15/36 (42 %) | **+0.17** | [product & GTM](https://github.com/ai-startup-curriculum/startup-product-gtm-curriculum) (level 30) | Material rise driven by AI procurement maturity (Kamiwaza federal, ExTrac gov, Siftwell/HIPAA, Payoneer OCC/Fed). Enterprise selling motions owned at level 30; CPO-specific regulated-buyer *product* patterns (not sales motion) overlap with new theme #19 and can be absorbed there. |
| 16 | Platform / API-first / multi-surface product strategy | 11/36 (31 %) | +0.06 | this repo (level 35) | Crossed 0.30 this cycle. Already in-scope for [mod-002](lessons/mod-002-opportunity-assessment-and-prioritization) exercise-03 `multi-surface-ranking-drill` and [mod-003](lessons/mod-003-roadmap-outcomes-and-strategy). |
| 17 | Founder background (prior 0 → 1) | 7/36 (19 %) | −0.03 | [founder-ceo](https://github.com/ai-startup-curriculum/founder-ceo-curriculum) (level 20) | Trait / experience signal; not a level-35 curriculum item. |
| 18 | Board reporting / fundraising narrative | 6/36 (17 %) | +0.04 | [finance & fundraising](https://github.com/ai-startup-curriculum/startup-finance-fundraising-curriculum) (level 40) | Below threshold; primary owner at level 40. |
| **19** | **AI governance / model behavior as a product surface** — hallucination boundaries, prompt-injection defense, auditability, data residency, policy on training on customer data, trustworthy-AI decision boundaries | **17/36 (47 %)** | **NEW** | this repo (level 35) | **Watch-list.** Distinct from theme #2 (that's *having* AI intuition; this is *shipping governance as a product surface*). Can be absorbed into declared [mod-005](lessons/mod-005-metrics-experimentation-and-ai-evals) — exercise-04 `llm-eval-suite-authoring-for-one-agent` naturally extends to governance evals; exercise-05 `cost-latency-quality-pareto-drill` can include trust/safety as a Pareto dimension. See [external resources](#external-resources). <!-- needs-research: if mod-005 is authored without explicit governance evals, escalate to a dedicated exercise or standalone module next cycle --> |
| **20** | **Agent-orchestration / multi-agent product strategy** — owning agentic-workflow quality, agent-vs-human handoff, agent reliability as a product surface | **12/36 (33 %)** | **NEW** | this repo (level 35) | Crosses threshold at 0.33. Partially overlaps theme #16 (platform strategy) and theme #2 (AI-native). Absorbed by [mod-004](lessons/mod-004-discovery-delivery-cadence) exercise-05 `agentic-ux-iteration-loop-drill` and [mod-007](lessons/mod-007-working-with-founders-eng-and-gtm) AI-system-architecture read-through. |

## What is *not* changing this cycle

Every theme with frequency ≥ 0.30 is either (a) **covered by mod-001**, (b)
mapped to a **declared-but-not-yet-authored pillar module** (mod-002–mod-007)
listed in [CURRICULUM.md](CURRICULUM.md#modules), or (c) **owned at a lower
level** per the ownership rule.

The two **new themes** this cycle — AI governance as a product surface
(47 %, theme #19) and agent-orchestration product strategy (33 %, theme #20) —
both have clean fold-in paths:

- Theme #19 → `mod-005/exercise-04-llm-eval-suite-authoring-for-one-agent`
  and `mod-005/exercise-05-cost-latency-quality-pareto-drill`
- Theme #20 → `mod-004/exercise-05-agentic-ux-iteration-loop-drill`
  and the AI-system-architecture section of `mod-007`

The watch-list theme #2 (AI/LLM-native PM) now meets condition (a) of its
escalation criteria (frequency ≥ 0.60 — in fact 0.81), but condition (b)
'fold-in has not absorbed the demand (measured by module authoring gap in
mod-004/mod-005)' cannot yet be measured — both modules are still planned.
Re-evaluate the moment mod-004 and mod-005 are authored.

Adding content now in any of these cases would preempt the declared pathway
and violate continuity bias.

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

**AI governance as a product surface (theme #19, new this cycle)**

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
- plancraft — Head of Product —
  [ashbyhq.com/plancraft](https://jobs.ashbyhq.com/plancraft/4bb37fe2-8fc5-46bb-9914-ec072dd659e4)
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

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
