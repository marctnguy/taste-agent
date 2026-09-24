# Taste Agent — ROI & Risk Assessment

**Client Case:** Letterboxd  
**Project:** AI-Powered Cross-Media Taste Intelligence  
**Assessment Type:** Scenario-Based Business Case  
**Current Stage:** Proof of Concept

---

## 1. Purpose

This document evaluates the potential financial case and principal risks associated with developing Taste Agent beyond the current Proof of Concept.

The POC demonstrates that Letterboxd-style consumption data can be transformed into a structured semantic Taste Model and that film and book metadata can be represented within the same semantic architecture.

It does **not** yet demonstrate:

- improved recommendation quality
- increased subscription conversion
- improved paid-member retention
- increased Patron upgrades
- sustainable production operating costs

The ROI assessment is therefore scenario-based rather than a financial forecast.

Its purpose is to determine whether the potential value is large enough to justify a controlled Pilot and what evidence should be required before further investment.

---

## 2. Known Business Inputs

The financial model uses only publicly available Letterboxd information where possible.

| Input | Value |
|---|---:|
| Letterboxd members, Q2 2026 | 30.7M |
| Pro annual price | $19 |
| Patron annual price | $49 |
| Pro → Patron annual price difference | $30 |
| Primary monetization model | Paid memberships |

Letterboxd does not publicly disclose sufficient information to construct a reliable bottom-up revenue forecast for Taste Agent.

Important undisclosed variables include:

- number of Free members
- number of Pro members
- number of Patron members
- Free → Pro conversion rate
- paid-member churn
- average subscription lifetime
- subscription ARPU after discounts or taxes
- advertising impact
- customer acquisition cost
- internal engineering cost
- AI infrastructure cost at scale
- expected Taste Agent usage frequency

For this reason, the following financial model uses explicit illustrative assumptions rather than presenting estimates of Letterboxd's actual economics.

---

## 3. Value Creation Model

Taste Agent is proposed as a premium capability within Letterboxd's existing subscription ecosystem rather than as a separate subscription product.

The business case therefore focuses on three potential revenue mechanisms.

### 3.1 Free → Pro Conversion

A more personalized discovery experience could provide an additional reason for highly engaged Free members to upgrade to Pro.

The relevant question is:

> Does access to a richer Taste Model and semantic discovery experience increase paid conversion?

---

### 3.2 Paid-Member Retention

If Taste Agent increases discovery value and repeated engagement, it may improve the perceived value of a paid Letterboxd membership.

The relevant question is:

> Do paid members exposed to Taste Agent renew at a higher rate than comparable members who are not exposed?

---

### 3.3 Pro → Patron Upsell

More advanced Taste capabilities could potentially support additional differentiation between Pro and Patron.

For example, a future packaging experiment could reserve features such as:

- Taste Evolution
- external cultural connections
- cross-media Taste Models

for Patron members.

The relevant question is:

> Does advanced taste intelligence create sufficient incremental value to increase Pro → Patron upgrades?

---

## 4. Value Not Included in the ROI Model

The financial model intentionally excludes benefits that are harder to attribute directly.

These could include:

- increased overall engagement
- increased watchlist activity
- stronger product differentiation
- improved brand perception
- additional advertising inventory
- partnership opportunities
- long-term strategic value of a reusable semantic taste layer

These benefits may be strategically relevant but should not be used to inflate the initial financial case without evidence.

The model therefore counts only incremental subscription revenue.

---

## 5. Illustrative Pilot Investment

The following figures represent an illustrative budget for moving from the current POC to a production-oriented Pilot.

They are project assumptions rather than Letterboxd internal cost estimates.

### One-Time Implementation

| Cost Area | Illustrative Cost |
|---|---:|
| AI / backend engineering | $18,000 |
| Product / frontend development | $10,000 |
| Data and evaluation | $6,000 |
| Privacy / legal assessment | $4,000 |
| QA and monitoring setup | $3,000 |
| Contingency | $4,000 |
| **Total One-Time Investment** | **$45,000** |

---

## 6. Illustrative Annual Operating Cost

| Cost Area | Illustrative Annual Cost |
|---|---:|
| AI / API usage | $10,000 |
| Cloud, database and monitoring | $5,000 |
| Maintenance and evaluation | $12,000 |
| Compliance / operational overhead | $3,000 |
| **Total Annual Operating Cost** | **$30,000** |

This produces an illustrative:

**Year 1 cost**

```text
$45,000 implementation
+
$30,000 operating cost
=
$75,000
```

For a simplified 36-month scenario:

```text
$45,000 implementation
+
($30,000 × 3 years)
=
$135,000
```

Actual operating cost would depend heavily on architecture and usage.

The proposed production architecture reduces this risk by classifying cultural works once, storing their semantic vectors, and reusing those vectors for personalization rather than repeatedly calling an LLM for the same content.

---

## 7. Illustrative Addressable Cohorts

Because Letterboxd does not publicly disclose the required membership segmentation, the model uses two hypothetical cohorts solely for scenario modelling.

| Cohort | Illustrative Size |
|---|---:|
| Relevant Free-member cohort | 5,000,000 |
| Relevant paid-member cohort | 500,000 |

These figures are **not estimates of Letterboxd's actual Free or paid membership**.

They provide a consistent base for testing how small changes in subscription behaviour could affect the financial case.

---

## 8. Scenario Assumptions

Three scenarios are modelled.

### Conservative Scenario

- Free → Pro uplift: **+0.05 percentage points**
- Paid churn reduction: **0.25 percentage points**
- Pro → Patron upgrades: **1,000**

### Base Scenario

- Free → Pro uplift: **+0.10 percentage points**
- Paid churn reduction: **0.50 percentage points**
- Pro → Patron upgrades: **2,500**

### Upside Scenario

- Free → Pro uplift: **+0.25 percentage points**
- Paid churn reduction: **1.00 percentage point**
- Pro → Patron upgrades: **5,000**

These are sensitivity assumptions used to test the economics of the concept.

They are not predictions of Taste Agent's expected performance.

---

## 9. 12-Month ROI Scenarios

### Conservative Scenario

#### Free → Pro

```text
5,000,000 × 0.05%
=
2,500 incremental Pro subscriptions

2,500 × $19
=
$47,500
```

#### Paid Retention

```text
500,000 × 0.25%
=
1,250 retained paid members

1,250 × $19
=
$23,750
```

The calculation conservatively values retained members at the Pro price.

#### Pro → Patron

```text
1,000 upgrades × $30
=
$30,000
```

#### Total

```text
$47,500
+
$23,750
+
$30,000
=
$101,250 incremental annual revenue
```

With a Year 1 cost of $75,000:

```text
ROI =
($101,250 - $75,000) / $75,000

≈ 35%
```

---

### Base Scenario

#### Free → Pro

```text
5,000,000 × 0.10%
=
5,000 incremental Pro subscriptions

5,000 × $19
=
$95,000
```

#### Paid Retention

```text
500,000 × 0.50%
=
2,500 retained paid members

2,500 × $19
=
$47,500
```

#### Pro → Patron

```text
2,500 upgrades × $30
=
$75,000
```

#### Total

```text
$95,000
+
$47,500
+
$75,000
=
$217,500 incremental annual revenue
```

With a Year 1 cost of $75,000:

```text
ROI =
($217,500 - $75,000) / $75,000

=
190%
```

---

### Upside Scenario

#### Free → Pro

```text
5,000,000 × 0.25%
=
12,500 incremental Pro subscriptions

12,500 × $19
=
$237,500
```

#### Paid Retention

```text
500,000 × 1.00%
=
5,000 retained paid members

5,000 × $19
=
$95,000
```

#### Pro → Patron

```text
5,000 upgrades × $30
=
$150,000
```

#### Total

```text
$237,500
+
$95,000
+
$150,000
=
$482,500 incremental annual revenue
```

With a Year 1 cost of $75,000:

```text
ROI =
($482,500 - $75,000) / $75,000

≈ 543%
```

---

## 10. 12-Month Scenario Summary

| Scenario | Incremental Revenue | Year 1 Cost | Illustrative ROI |
|---|---:|---:|---:|
| Conservative | $101,250 | $75,000 | 35% |
| Base | $217,500 | $75,000 | 190% |
| Upside | $482,500 | $75,000 | 543% |

These figures demonstrate sensitivity to relatively small changes in subscription behaviour.

They do **not** establish that Taste Agent will generate these changes.

That must be validated experimentally.

---

## 11. 36-Month Scenario

A simplified 36-month model assumes:

- $45,000 initial implementation cost
- $30,000 annual operating cost
- constant annual incremental benefit
- no additional major development investment
- no discount rate

Total illustrative 36-month cost:

```text
$45,000 + ($30,000 × 3)
=
$135,000
```

### Conservative

```text
$101,250 × 3
=
$303,750 benefit

ROI =
($303,750 - $135,000) / $135,000

=
125%
```

### Base

```text
$217,500 × 3
=
$652,500 benefit

ROI =
($652,500 - $135,000) / $135,000

≈ 383%
```

### Upside

```text
$482,500 × 3
=
$1,447,500 benefit

ROI =
($1,447,500 - $135,000) / $135,000

≈ 972%
```

---

## 12. 36-Month Scenario Summary

| Scenario | 36-Month Benefit | 36-Month Cost | Illustrative ROI |
|---|---:|---:|---:|
| Conservative | $303,750 | $135,000 | 125% |
| Base | $652,500 | $135,000 | 383% |
| Upside | $1,447,500 | $135,000 | 972% |

The 36-month model is deliberately simplified.

It should not be interpreted as a discounted cash-flow valuation or financial forecast.

Its purpose is to show the potential scale of the opportunity if measurable subscription impact persists over time.

---

## 13. Break-Even Analysis

A more useful decision metric at this stage is the amount of commercial uplift required to recover the initial investment.

Using the illustrative Year 1 cost:

```text
$75,000 / $19
≈
3,948 Pro subscriptions
```

Taste Agent would therefore need approximately **3,948 incremental annual Pro subscriptions** to recover the entire illustrative Year 1 cost if conversion were the only source of value.

Against the illustrative 5 million-member relevant Free cohort:

```text
3,948 / 5,000,000
≈
0.079%
```

This is approximately:

> **0.08 percentage points of incremental Free → Pro conversion**

This does not mean Taste Agent is expected to produce this uplift.

It establishes a concrete commercial threshold that can be tested during a controlled experiment.

---

## 14. Cross-Media ROI

The POC demonstrates that films and books can technically be represented within the same semantic taxonomy.

This does not establish that external cultural data creates enough additional recommendation value to justify its cost and privacy complexity.

The Pilot should therefore compare:

```text
A. Existing / conventional discovery

B. Letterboxd-only semantic Taste Model

C. Letterboxd + cross-media Taste Model
```

Cross-media functionality should progress only if:

```text
Incremental Recommendation Value
>
Incremental Technical + Privacy + UX Cost
```

This creates an explicit decision gate rather than assuming that more data automatically creates a better product.

---

# Risk Assessment

## 15. Risk Scoring Method

Each identified risk is evaluated using two 1–5 scales.

### Likelihood

| Score | Definition |
|---:|---|
| 1 | Very unlikely |
| 2 | Unlikely |
| 3 | Possible |
| 4 | Likely |
| 5 | Very likely |

### Impact

| Score | Definition |
|---:|---|
| 1 | Minimal |
| 2 | Minor |
| 3 | Moderate |
| 4 | Major |
| 5 | Severe |

The overall risk score is calculated as:

```text
Risk Score = Likelihood × Impact
```

For prioritization within this project:

| Score | Priority |
|---:|---|
| 1–5 | Low |
| 6–10 | Medium |
| 11–15 | High |
| 16–25 | Critical |

These categories are project-defined prioritization thresholds rather than a formal Letterboxd risk framework.

---

## 16. Risk Matrix

| Risk | Category | Likelihood (1–5) | Impact (1–5) | Score | Priority | Mitigation |
|---|---|---:|---:|---:|---|---|
| Semantic recommendations do not outperform existing discovery | Product | 4 | 5 | 20 | Critical | Controlled evaluation against existing/conventional discovery before commercial rollout |
| Taste Agent does not create sufficient paid-member value | Commercial | 3 | 5 | 15 | High | Test willingness to use and pay through a limited subscription experiment |
| Commercial uplift is insufficient to justify continued investment | Financial | 4 | 5 | 20 | Critical | Predefine break-even and ROI thresholds before scaling |
| Cross-media data produces little incremental recommendation value | Product | 3 | 3 | 9 | Medium | Compare Letterboxd-only and cross-media models experimentally |
| Users are unwilling to connect external cultural accounts | Adoption | 3 | 3 | 9 | Medium | Make external connections optional and ensure Letterboxd-only model remains useful |
| Incorrect metadata matches contaminate semantic vectors | Data | 3 | 4 | 12 | High | Metadata quality gates, match auditing and safe rejection of uncertain works |
| LLM classification produces inconsistent semantic scores | AI | 2 | 3 | 6 | Medium | Fixed taxonomy, strict structured output, evaluation set and monitoring |
| Recommendation explanations overstate what the model actually knows | AI / UX | 3 | 4 | 12 | High | Generate explanations from observed evidence and prohibit unsupported user-level claims |
| Taste modelling produces sensitive or inappropriate user inference | Privacy / AI | 2 | 5 | 10 | Medium | Restrict taxonomy to cultural characteristics; prohibit sensitive-trait and personality inference |
| Dependency on external metadata or AI providers creates operational risk | Dependency | 3 | 3 | 9 | Medium | Provider abstraction, caching, monitoring and fallback strategies |
| AI operating cost exceeds the value generated | Financial | 3 | 4 | 12 | High | Precompute semantic vectors, avoid repeated classification and monitor cost per active user |
| AI interactions create unacceptable latency | Technical | 3 | 3 | 9 | Medium | Precompute content vectors, cache results and keep deterministic scoring outside conversational calls |
| Taste Models become stale as user preferences evolve | Product | 3 | 3 | 9 | Medium | Incrementally update profiles as new ratings and activity are added |
| Limited history produces weak recommendations for new or low-activity users | Product | 4 | 3 | 12 | High | Minimum evidence thresholds, onboarding signals and fallback discovery methods |
| GDPR profiling and personal-data processing create compliance complexity | Compliance | 3 | 5 | 15 | High | Privacy-by-design, lawful-basis assessment, DPIA where required, transparency and user controls |
| External providers create data-processing or international-transfer obligations | Compliance | 2 | 4 | 8 | Medium | Provider assessment, DPAs and appropriate transfer mechanisms before production deployment |

---

## 17. Highest-Priority Risks

### 17.1 Recommendation Value

**Risk Score: 20 — Critical**

The most important product risk is that semantic modelling may be technically successful without producing better recommendations.

The POC validates the creation of a Taste Model.

It does not validate recommendation performance.

This should be addressed before significant additional investment by comparing semantic recommendations against an existing or conventional discovery baseline.

Relevant Pilot metrics could include:

- recommendation relevance
- novelty
- intention to watch
- watchlist additions
- already-consumed recommendation rate
- repeat interaction

---

### 17.2 Commercial Value

**Risk Score: 20 — Critical**

Even if users prefer Taste Agent recommendations, the feature may not materially affect subscription behaviour.

The commercial experiment should therefore measure:

- Free → paid conversion
- paid renewal / retention
- Pro → Patron upgrades
- incremental revenue per exposed user
- incremental operating cost per active user

Commercial deployment should depend on observed incremental value rather than engagement alone.

---

### 17.3 AI Quality and Explainability

LLM-based semantic classification introduces uncertainty.

The POC already reduces this risk through:

- a fixed 62-dimensional taxonomy
- strict JSON Schema output
- metadata quality gates
- separation of semantic classification from user preference signals
- deterministic downstream preference calculations

The Pilot should add:

- a fixed evaluation dataset
- periodic classification-quality testing
- regression testing
- explanation evaluation
- monitoring for schema or model drift

The system should explain recommendations using observable cultural characteristics rather than unsupported claims about the user.

---

### 17.4 Privacy and User Trust

Taste Agent processes behavioural history and creates inferred preference profiles.

The core design principle should remain:

> **Taste Agent should understand what characteristics a user responds to in culture without attempting to determine who that user is as a person.**

The system should therefore avoid inferring:

- political beliefs
- religion
- health conditions
- sexual orientation
- ethnicity
- personality
- mental-health characteristics
- other sensitive personal attributes

External cultural connections should be optional, transparent and removable.

Users should be able to understand, correct, reset or disable their Taste Model.

Detailed privacy and regulatory analysis is provided in `04-compliance.md`.

---

### 17.5 Cost and Scalability

A naive architecture could make repeated LLM calls for the same films or books whenever different users interact with Taste Agent.

This would unnecessarily increase cost and latency.

The proposed production architecture instead separates:

```text
CONTENT INTELLIGENCE
Work
→ Metadata
→ Semantic Classification
→ Stored 62D Vector
```

from:

```text
USER PERSONALIZATION
Consumption History
+
Stored Work Vectors
→
Taste Model
```

The expensive semantic classification step therefore occurs primarily when a new work enters the system rather than for every user recommendation.

This substantially changes the expected cost profile and should be validated during the Pilot.

---

## 18. Risk Reduction Already Demonstrated by the POC

The current POC already provides evidence for several technical risk controls.

### Metadata Quality

Works with insufficient or unreliable metadata can be rejected before semantic classification.

### Structured Output

The initial prompt-only experiment demonstrated schema instability.

Strict JSON Schema output subsequently produced consistent semantic structures.

### Preference Leakage

The LLM classifier does not receive:

- user rating
- like status
- preference class
- preference weight

It classifies the cultural work independently.

Preference analysis occurs downstream.

### Cross-Media Compatibility

Films and books can be represented using the same 62-dimensional semantic model.

This demonstrates technical compatibility, although the current dataset is not sufficiently balanced to establish robust cross-media recommendation performance.

### Safe Interpretation

The Taste Model describes associations between semantic characteristics and ratings.

It does not attempt to infer personality, identity or sensitive personal characteristics.

---

## 19. Decision Gates

Investment should progress through explicit evidence gates.

### Gate 1 — POC → MVP

**Question**

> Can the proposed semantic Taste Model be constructed reliably enough to justify product testing?

**Current status: PASS**

The POC demonstrates:

- metadata enrichment
- semantic classification
- strict structured output
- preference weighting
- preference association
- cross-media technical compatibility

---

### Gate 2 — MVP → Pilot

**Question**

> Can the Taste Model generate recommendations that users perceive as better or more useful than the selected baseline?

**Current status: NOT YET TESTED**

Required evidence:

- recommendation-quality evaluation
- user feedback
- baseline comparison
- acceptable latency
- acceptable cost
- reliable explanations

---

### Gate 3 — Pilot → Commercial Experiment

**Question**

> Does improved recommendation quality translate into repeated user engagement and sufficient perceived value to justify testing monetization?

Required evidence:

- repeated feature usage
- positive recommendation-quality results
- acceptable trust and privacy feedback
- manageable operating cost
- stable technical performance

---

### Gate 4 — Commercial Experiment → Full Deployment

**Question**

> Does Taste Agent generate sufficient incremental economic value to justify production investment and ongoing operating cost?

Required evidence:

- conversion impact
- retention impact
- upsell impact
- incremental revenue
- cost per active user
- compliance readiness
- scalable technical performance

---

## 20. Cross-Media Decision Gate

Cross-media expansion should have its own independent gate.

The question is not:

> Can Letterboxd connect books or other cultural media?

The POC already suggests that this is technically feasible.

The relevant question is:

> Does external cultural data improve film discovery enough to justify additional integration, privacy and UX complexity?

The Pilot should therefore measure the incremental recommendation value of cross-media data separately.

If the Letterboxd-only semantic model performs similarly, the simpler first-party architecture should be preferred.

---

## 21. Overall Assessment

The current POC provides sufficient technical evidence to justify further validation of the Taste Agent concept.

The strongest remaining uncertainties are not whether an LLM can classify cultural works.

They are whether:

1. semantic preference modelling improves film discovery
2. users repeatedly value the resulting experience
3. cross-media data provides meaningful incremental value
4. the feature changes subscription behaviour
5. operating costs remain below the value created
6. the system can be deployed with appropriate privacy and compliance controls

The scenario model shows that relatively small subscription-behaviour changes could recover an illustrative Pilot investment.

However, those changes have not yet been observed.

---

## 22. Recommendation

The financial case supports **continued investment at controlled Pilot scale**, rather than full deployment.

The next investment should be designed to answer the highest-value unresolved question:

> **Does a semantic Taste Model produce measurably better film discovery than Letterboxd's existing or conventional recommendation approach?**

If that hypothesis is validated, the next stage should test whether the improved experience affects engagement and subscription behaviour.

Cross-media functionality should be evaluated as an additional source of incremental value rather than treated as a prerequisite for Taste Agent.

The recommended investment path is therefore:

```text
POC
Technical feasibility demonstrated
        ↓
MVP / PILOT
Validate recommendation quality
        ↓
CROSS-MEDIA COMPARISON
Measure incremental external-data value
        ↓
COMMERCIAL EXPERIMENT
Validate conversion / retention / upsell
        ↓
FULL DEPLOYMENT
Only if product + economic + compliance gates pass
```

This limits upfront exposure while preserving the potential strategic value of a reusable semantic taste-intelligence layer.

---

## Related Documentation

- [`01-use-case-business-case.md`](01-use-case-business-case.md) — Business problem and strategic opportunity
- [`02-poc-feasibility.md`](02-poc-feasibility.md) — POC architecture, experiments and technical findings
- [`04-compliance.md`](04-compliance.md) — EU AI Act and GDPR assessment
- [`05-strategic-deployment-plan.md`](05-strategic-deployment-plan.md) — POC-to-production roadmap and commercialization strategy
