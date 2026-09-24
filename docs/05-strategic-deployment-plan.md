# Taste Agent — Strategic Deployment Plan

**Client Case:** Letterboxd  
**Project:** AI-Powered Cross-Media Taste Intelligence  
**Current Stage:** Proof of Concept  
**Proposed Path:** POC → MVP / Pilot → Commercial Experiment → Full Deployment

---

## 1. Deployment Strategy

The current POC demonstrates that cultural-consumption data can be transformed into a structured semantic Taste Model.

It does not yet demonstrate that the model improves recommendations or creates measurable commercial value.

Taste Agent should therefore follow a staged deployment strategy in which investment increases only when the previous stage produces sufficient evidence.

```text
POC
Technical Feasibility
      ✓
      ↓
MVP / PILOT
Product Feasibility
      ?
      ↓
COMMERCIAL EXPERIMENT
Economic Feasibility
      ?
      ↓
FULL DEPLOYMENT
Only if validated
```

This approach reduces the risk of scaling an AI capability before its recommendation quality, user value, cost, and commercial impact have been validated.

---

## 2. Deployment Roadmap

| Phase | Objective | Main Activities | Decision Gate |
|---|---|---|---|
| **POC — Current** | Validate semantic Taste Model | Metadata enrichment, 62D taxonomy, structured LLM classification, preference modelling, cross-media feasibility | Can a structured Taste Model be constructed? |
| **MVP / Pilot — 8–12 weeks** | Validate recommendation quality | Python processing layer, recommendation engine, minimal UI, persistent semantic vectors, evaluation framework | Does semantic personalization outperform the baseline? |
| **Commercial Experiment — 8–12 weeks** | Validate user and business value | Limited user rollout, paid-tier experiment, usage measurement, conversion/retention testing | Does incremental value exceed incremental cost? |
| **Full Deployment — Conditional** | Scale validated product | Native Letterboxd integration, monitoring, infrastructure scaling, subscription integration | Are product, financial, technical and compliance thresholds satisfied? |

Timelines are indicative project estimates and would require adjustment based on Letterboxd's internal resources and roadmap.

---

## 3. MVP / Pilot

The immediate next step should be a controlled MVP rather than a production rollout.

The MVP would extend the current POC with:

- Python-based deterministic processing
- stored semantic work vectors
- recommendation scoring
- a minimal user-facing Taste Profile
- Taste Agent conversational discovery
- basic error handling
- recommendation evaluation
- privacy and user-control mechanisms

n8n may remain as an orchestration layer, while Python handles statistical processing, recommendation logic, and evaluation.

The Pilot should compare three approaches:

```text
A. Existing / Conventional Discovery

B. Letterboxd Semantic Taste Model

C. Letterboxd + Cross-Media Taste Model
```

This experiment answers two separate questions:

> **Does semantic personalization improve discovery?**

and:

> **Does adding external cultural history improve it enough to justify the additional complexity?**

Cross-media functionality should not progress automatically simply because the POC demonstrated that it is technically possible.

---

## 4. Pilot Success Metrics

Success should be measured across four dimensions.

| Area | Example Metrics |
|---|---|
| **Recommendation Quality** | relevance, novelty, intention to watch, watchlist additions, already-consumed rate |
| **Product Adoption** | activation, repeat usage, conversations per user, recommendation interactions |
| **AI / Technical** | latency, classification failure rate, recommendation errors, cost per active user |
| **Cross-Media Value** | recommendation uplift vs Letterboxd-only model, external-data opt-in rate |

The Pilot should establish predefined thresholds before results are evaluated.

A positive technical result alone should not trigger commercial deployment.

---

## 5. Commercial Experiment

If the Pilot demonstrates improved discovery and repeated user engagement, Taste Agent should progress to a limited commercial experiment.

The proposed commercialization model is:

> **Taste Agent as a native premium capability within Letterboxd's existing subscription model.**

A separate Taste Agent subscription or standalone product is not proposed.

One possible packaging hypothesis is:

| Capability | Free | Pro | Patron |
|---|:---:|:---:|:---:|
| Basic Taste preview | ✓ | ✓ | ✓ |
| Full Letterboxd Taste Model | — | ✓ | ✓ |
| Semantic recommendations | — | ✓ | ✓ |
| Taste Agent | Limited | ✓ | ✓ |
| Taste Evolution | — | Limited | ✓ |
| External cultural connections | — | — | ✓ |
| Cross-media Taste Model | — | — | ✓ |

This is a proposed commercial hypothesis, not Letterboxd's current product structure.

The experiment should determine whether Taste Agent produces measurable changes in:

- Free → paid conversion
- paid retention
- Pro → Patron upgrades
- feature engagement
- incremental revenue per exposed user
- incremental operating cost per active user

The ROI assessment estimates that approximately **3,948 additional $19 Pro subscriptions** would recover the illustrative $75,000 first-year investment if conversion were the only source of value.

This provides a concrete commercial threshold against which experimental results can be assessed.

---

## 6. Go-to-Market Approach

Taste Agent does not require a conventional external go-to-market strategy because it is proposed as a feature within an existing consumer platform.

The primary distribution channel is therefore **Letterboxd itself**.

A possible rollout sequence is:

```text
Small Opt-In Beta
        ↓
Selected Existing Users
        ↓
Paid-Membership Experiment
        ↓
Broader Pro / Patron Rollout
        ↓
Optional Cross-Media Expansion
```

Initial messaging should focus on the user benefit rather than the underlying AI technology.

For example:

> **Discover films through the patterns behind what you already love.**

Cross-media functionality could subsequently be positioned as an optional enhancement:

> **Connect more of your cultural history to make your Taste Model richer.**

Users should always be able to obtain value from the Letterboxd-only experience.

---

## 7. Stakeholder Communication

Different stakeholders require different evidence before supporting deployment.

| Stakeholder | Primary Question | Evidence Required |
|---|---|---|
| **Product / Leadership** | Does this improve Letterboxd and justify investment? | Adoption, recommendation uplift, ROI |
| **Engineering / Data** | Can this operate reliably at scale? | Architecture, latency, cost, monitoring |
| **Legal / Privacy** | Can preference profiling be deployed responsibly? | DPIA, lawful basis, data flows, AI Act assessment |
| **Design / UX** | Do users understand and trust the recommendations? | User testing, explanations, correction controls |
| **Growth / Commercial** | Does it improve subscription economics? | Conversion, retention, upsell |
| **Members** | Why should I use it and what happens to my data? | Clear value proposition, transparency and control |

This stakeholder communication should occur throughout the Pilot rather than only before launch.

---

## 8. Full Deployment Conditions

Full deployment should occur only if the Pilot and commercial experiment demonstrate that:

1. semantic recommendations meaningfully outperform the selected baseline
2. users repeatedly engage with the feature
3. recommendation explanations are useful and understandable
4. AI operating costs remain economically sustainable
5. privacy and compliance requirements can be satisfied
6. commercial impact justifies ongoing investment

Cross-media deployment has an additional condition:

> **External cultural data should only be integrated at scale if it produces measurable incremental value over the Letterboxd-only Taste Model.**

If it does not, Letterboxd should retain the simpler first-party architecture.

---

## 9. Production Architecture Direction

If deployment proceeds, the production architecture should avoid reproducing the POC literally.

The POC performs semantic enrichment as part of the workflow.

At scale, semantic representations should instead be generated once and reused.

```text
CONTENT LAYER

New Film / Work
      ↓
Metadata Enrichment
      ↓
Semantic Classification
      ↓
Stored 62D Vector
```

```text
PERSONALIZATION LAYER

User History
      +
Stored Work Vectors
      ↓
Taste Model
      ↓
Recommendation Scoring
```

```text
INTERACTION LAYER

Long-Term Taste
      +
Recent Taste
      +
Current Intent
      ↓
Taste Agent
```

This reduces repeated LLM calls, latency, and operating cost while separating reusable content intelligence from personal preference data.

---

## 10. Strategic Recommendation

Taste Agent should **not move directly from POC to full deployment**.

The recommended path is:

```text
CURRENT POC
Semantic modelling is technically feasible
        ↓
MVP / CONTROLLED PILOT
Validate recommendation quality
        ↓
CROSS-MEDIA TEST
Measure whether external cultural data adds value
        ↓
COMMERCIAL EXPERIMENT
Measure conversion, retention and cost
        ↓
SCALE / MODIFY / STOP
Based on observed evidence
```

This approach keeps the next investment relatively small while testing the assumptions that matter most.

The strategic objective is therefore not to launch an AI feature as quickly as possible.

It is to determine whether **semantic taste intelligence creates enough additional discovery and commercial value to deserve a permanent place within Letterboxd.**

---

## Related Documentation

- [`01-use-case-business-case.md`](01-use-case-business-case.md) — Strategic opportunity and business case
- [`02-poc-feasibility.md`](02-poc-feasibility.md) — Technical feasibility evidence
- [`03-roi-risk-assessment.md`](03-roi-risk-assessment.md) — Financial case and risk assessment
- [`04-compliance.md`](04-compliance.md) — EU AI Act and GDPR assessment
