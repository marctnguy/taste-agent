# Taste Agent — ROI & Risk Assessment

**Client Case:** Letterboxd
**Project:** AI-Powered Cross-Media Taste Intelligence
**Assessment Horizon:** 12 months / 36 months
**Decision Stage:** POC → Proposed MVP / Pilot

---

# 1. Purpose

The POC demonstrates that a structured semantic Taste Model can be constructed from cultural-consumption data.

Technical feasibility alone, however, does not justify investment.

The next business question is:

> **Could Taste Agent create enough incremental value for Letterboxd to justify its implementation, operating costs, and associated risks?**

This assessment evaluates:

* expected implementation costs
* ongoing operating costs
* potential revenue mechanisms
* 12-month and 36-month ROI scenarios
* break-even conditions
* key business, technical, AI, privacy, and dependency risks

Because Letterboxd does not publicly disclose paid subscriber count, conversion rate, churn, subscriber mix, or Letterboxd-specific revenue, the financial model uses **explicit scenario assumptions rather than presenting estimated internal metrics as facts**.

The purpose is therefore not to predict exact financial performance.

It is to determine whether a sufficiently plausible path to positive ROI exists to justify a controlled Pilot.

---

# 2. Known Business Inputs

The following inputs are based on publicly available Letterboxd information.

| Input                          |                             Publicly Known |
| ------------------------------ | -----------------------------------------: |
| Members, Q2 2026               |                                     30.7M+ |
| Standard Pro web price         |                                 $19 / year |
| Standard Patron web price      |                                 $49 / year |
| Free tier                      |                                        Yes |
| Subscription frequency         |                                     Annual |
| Primary monetization relevance | Membership fees are chief source of income |

Letterboxd also already offers personalized functionality within paid subscriptions, including annual and all-time statistics.

This supports the strategic logic of evaluating Taste Agent as a **premium personalization capability** rather than introducing an unrelated monetization model.

---

# 3. Unknown Business Inputs

Several variables required for an exact financial model are not publicly disclosed.

These include:

* number of Free members
* number of Pro members
* number of Patron members
* Free → paid conversion rate
* Pro → Patron conversion rate
* annual subscriber churn
* average subscription revenue per paid member
* advertising revenue impact of converting a free user
* subscriber acquisition cost
* infrastructure cost per active member
* internal engineering cost
* expected Taste Agent usage frequency

These variables should be replaced with actual internal data before a production investment decision.

For the current consulting assessment, they are represented through **clearly labelled assumptions**.

---

# 4. Value Creation Model

Taste Agent could generate economic value through three primary mechanisms.

## 4.1 Free → Paid Conversion

Taste Agent could create an additional reason for highly engaged free members to purchase Pro or Patron.

For modelling purposes, the conservative assumption is that newly converted users purchase **Pro at $19/year**.

This avoids assuming the higher Patron price where no evidence supports it.

```text
Incremental Conversion Revenue
=
Relevant Free User Base
×
Conversion Uplift
×
$19
```

---

## 4.2 Paid Retention

If Taste Agent becomes a recurring discovery tool, it could increase the perceived ongoing utility of a subscription.

```text
Retained Revenue
=
Relevant Paid Subscriber Base
×
Churn Reduction
×
Average Retained Subscription Value
```

For conservative modelling, retained subscription value can again be represented using the $19 Pro price.

This intentionally understates value if some retained subscribers are Patrons.

---

## 4.3 Pro → Patron Upsell

Cross-media functionality, Taste Evolution, or more advanced Taste Agent functionality could potentially differentiate the Patron tier.

The current standard price difference is:

```text
$49 Patron
-
$19 Pro
=
$30 additional annual revenue
```

Therefore:

```text
Incremental Upsell Revenue
=
Additional Pro → Patron Upgrades
×
$30
```

This is a product hypothesis and must be validated rather than assumed.

---

# 5. Why Revenue Is Modelled Incrementally

Taste Agent should not be credited with existing Letterboxd subscription revenue.

The relevant question is:

> **How much additional revenue would exist because Taste Agent was introduced?**

The model therefore considers only incremental effects:

```text
Existing Revenue
        +
Incremental Conversion
        +
Incremental Retention
        +
Incremental Upsell
        -
Taste Agent Costs
```

This prevents the ROI case from being artificially inflated by revenue Letterboxd would have generated anyway.

---

# 6. Proposed Investment Structure

A production-scale rollout should not be funded immediately.

Investment is divided into stages.

## Stage 1 — POC

**Status:** Completed within this project.

Purpose:

* validate semantic modelling
* test metadata enrichment
* test structured LLM classification
* demonstrate cross-media compatibility

No production ROI claim is made from the POC.

---

## Stage 2 — MVP / Controlled Pilot

Indicative activities:

* migrate deterministic analytical logic to Python
* implement recommendation scoring
* persist semantic vectors
* build minimal user-facing experience
* establish evaluation framework
* run controlled recommendation testing
* implement privacy and consent controls
* test Letterboxd-only vs cross-media modelling
* measure AI operating cost

### Estimated One-Time Cost

| Component                         | Estimated Cost |
| --------------------------------- | -------------: |
| AI / backend engineering          |        $18,000 |
| Product / frontend implementation |        $10,000 |
| Data / evaluation work            |         $6,000 |
| Privacy / legal review            |         $4,000 |
| QA / monitoring setup             |         $3,000 |
| Contingency                       |         $4,000 |
| **Estimated Pilot Investment**    |    **$45,000** |

These are **project assumptions for scenario modelling**, not Letterboxd internal cost estimates.

The purpose is to establish an order-of-magnitude investment against which potential value can be tested.

---

# 7. Estimated Ongoing Costs

Taste Agent introduces operating costs that conventional static features may not.

The main cost categories are:

* LLM inference
* embedding / semantic processing
* data storage
* external metadata services
* monitoring and observability
* model evaluation
* engineering maintenance
* privacy and compliance maintenance

A key POC finding reduces this risk:

> **Semantic classification should be performed once per cultural work and persisted, rather than repeated for every user interaction.**

The intended production architecture therefore separates:

```text
OFFLINE / INCREMENTAL

New Work
   ↓
Metadata
   ↓
Semantic Classification
   ↓
Stored Semantic Vector
```

from:

```text
ONLINE

User Taste Model
      +
Stored Content Vectors
      +
Current Intent
      ↓
Recommendation
```

This architecture substantially reduces repeated LLM usage.

For scenario modelling, the project assumes:

| Ongoing Cost                    |      Year 1 |
| ------------------------------- | ----------: |
| AI / API usage                  |     $10,000 |
| Cloud / database / monitoring   |      $5,000 |
| Maintenance & evaluation        |     $12,000 |
| Compliance / operational review |      $3,000 |
| **Annual Operating Cost**       | **$30,000** |

Again, these values are modelling assumptions.

Actual costs should be measured during the Pilot.

---

# 8. Year-One Investment

Under the illustrative model:

```text
One-Time Pilot / Implementation
$45,000

+

Year-One Operating Cost
$30,000

=

Year-One Cost
$75,000
```

For subsequent years, the simplified model assumes approximately:

```text
$30,000 annual operating cost
```

excluding major additional product development.

Therefore:

| Horizon   | Illustrative Total Cost |
| --------- | ----------------------: |
| 12 months |                 $75,000 |
| 36 months |                $135,000 |

The 36-month estimate consists of:

```text
$45,000 initial investment
+
3 × $30,000 operating cost
=
$135,000
```

---

# 9. Revenue Scenario Model

Because Letterboxd's actual subscription funnel is unavailable, the model uses a **defined addressable cohort** rather than assuming all 30.7 million members are immediately exposed to Taste Agent.

For the scenario analysis, assume:

```text
Relevant Free User Cohort = 5,000,000
Relevant Paid User Cohort = 500,000
```

These are **illustrative modelling assumptions only**.

They are not estimates of Letterboxd's actual free or paid subscriber numbers.

The purpose is to test the sensitivity of the business case to relatively small behavioural changes.

---

# 10. Conservative Scenario

Assumptions:

| Variable                         |            Conservative |
| -------------------------------- | ----------------------: |
| Relevant Free Cohort             |               5,000,000 |
| Free → Pro uplift                | +0.05 percentage points |
| Relevant Paid Cohort             |                 500,000 |
| Churn reduction                  |  0.25 percentage points |
| Additional Pro → Patron upgrades |                   1,000 |

### Conversion

```text
5,000,000
×
0.0005
=
2,500 additional Pro members

2,500
×
$19
=
$47,500
```

### Retention

```text
500,000
×
0.0025
=
1,250 retained subscribers

1,250
×
$19
=
$23,750
```

### Upsell

```text
1,000
×
$30
=
$30,000
```

### Total Incremental Annual Revenue

```text
$47,500
+
$23,750
+
$30,000
=
$101,250
```

### 12-Month ROI

```text
ROI
=
(Benefit - Cost) / Cost

=
($101,250 - $75,000) / $75,000

=
35%
```

Under this illustrative conservative scenario, the investment becomes positive within the first year.

---

# 11. Base Scenario

Assumptions:

| Variable                         |                    Base |
| -------------------------------- | ----------------------: |
| Relevant Free Cohort             |               5,000,000 |
| Free → Pro uplift                | +0.10 percentage points |
| Relevant Paid Cohort             |                 500,000 |
| Churn reduction                  |  0.50 percentage points |
| Additional Pro → Patron upgrades |                   2,500 |

### Conversion

```text
5,000,000
×
0.001
=
5,000 additional Pro members

5,000
×
$19
=
$95,000
```

### Retention

```text
500,000
×
0.005
=
2,500 retained subscribers

2,500
×
$19
=
$47,500
```

### Upsell

```text
2,500
×
$30
=
$75,000
```

### Total Incremental Annual Revenue

```text
$95,000
+
$47,500
+
$75,000
=
$217,500
```

### 12-Month ROI

```text
($217,500 - $75,000) / $75,000
=
190%
```

This scenario illustrates how relatively small behavioural changes can become financially meaningful when applied to a large digital platform.

It does **not** predict that Taste Agent will produce those changes.

---

# 12. Upside Scenario

Assumptions:

| Variable                         |                  Upside |
| -------------------------------- | ----------------------: |
| Relevant Free Cohort             |               5,000,000 |
| Free → Pro uplift                | +0.25 percentage points |
| Relevant Paid Cohort             |                 500,000 |
| Churn reduction                  |   1.00 percentage point |
| Additional Pro → Patron upgrades |                   5,000 |

### Conversion

```text
12,500 new Pro members
×
$19
=
$237,500
```

### Retention

```text
5,000 retained subscribers
×
$19
=
$95,000
```

### Upsell

```text
5,000 upgrades
×
$30
=
$150,000
```

### Total Incremental Annual Revenue

```text
$482,500
```

### 12-Month ROI

```text
($482,500 - $75,000) / $75,000
=
543%
```

The upside scenario is included for sensitivity analysis, not as an expected outcome.

---

# 13. Scenario Comparison

| Scenario     | Incremental Annual Revenue | Year-One Cost | 12-Month ROI |
| ------------ | -------------------------: | ------------: | -----------: |
| Conservative |                   $101,250 |       $75,000 |      **35%** |
| Base         |                   $217,500 |       $75,000 |     **190%** |
| Upside       |                   $482,500 |       $75,000 |     **543%** |

The most important conclusion is **not** the individual ROI percentage.

It is that:

> **Taste Agent does not require a large percentage-point change in Letterboxd behaviour to potentially recover a relatively modest Pilot investment.**

Whether those behavioural changes are achievable remains the central commercial question for the Pilot.

---

# 14. 36-Month Scenario

For a simplified 36-month model, assume:

* initial implementation occurs once
* operating cost remains $30,000 annually
* annual incremental benefit remains constant
* no discount rate is applied
* no additional major development investment is required

This is intentionally simplified for feasibility assessment.

### Total 36-Month Cost

```text
$45,000 implementation
+
$90,000 operating cost
=
$135,000
```

### Conservative

```text
3 × $101,250
=
$303,750 benefit

ROI
=
($303,750 - $135,000) / $135,000
=
125%
```

### Base

```text
3 × $217,500
=
$652,500 benefit

ROI
=
($652,500 - $135,000) / $135,000
=
383%
```

### Upside

```text
3 × $482,500
=
$1,447,500 benefit

ROI
=
($1,447,500 - $135,000) / $135,000
=
972%
```

| Scenario     | 36M Benefit | 36M Cost |  36M ROI |
| ------------ | ----------: | -------: | -------: |
| Conservative |    $303,750 | $135,000 | **125%** |
| Base         |    $652,500 | $135,000 | **383%** |
| Upside       |  $1,447,500 | $135,000 | **972%** |

These figures assume benefits persist and should therefore be interpreted as **scenario outputs rather than forecasts**.

---

# 15. Break-Even Analysis

A more useful decision metric than the upside scenario is the break-even point.

Year-one cost is approximately:

```text
$75,000
```

If Taste Agent generated value **only through new Pro conversions**, break-even would require:

```text
$75,000 / $19
≈
3,948 additional Pro subscriptions
```

Relative to the illustrative 5 million-member addressable cohort:

```text
3,948 / 5,000,000
≈
0.079 percentage points
```

Therefore, under the model:

> **A conversion uplift of approximately 0.08 percentage points across the illustrative 5M cohort would recover the full first-year investment if conversion were the only value mechanism.**

In reality, value could also come from retention and Patron upsell.

This break-even threshold is one of the most useful metrics to validate during a commercial experiment.

---

# 16. Cross-Media ROI Question

Cross-media enrichment introduces additional value potential but also additional cost and risk.

Connecting Goodreads, Spotify, or future cultural sources requires:

* additional ingestion logic
* data normalization
* consent management
* third-party dependency management
* additional privacy controls
* potentially additional inference
* additional product complexity

Cross-media integration should therefore **not be assumed to belong in the production product simply because it is technically possible**.

The Pilot should compare:

```text
Letterboxd-Only
Semantic Taste Model

        vs.

Cross-Media
Semantic Taste Model
```

and measure whether the second produces meaningful improvement in:

* recommendation relevance
* novelty
* intention to watch
* repeat usage
* willingness to pay

The decision rule should be:

> **Cross-media enrichment should only progress to full deployment if its incremental user or commercial value exceeds its incremental technical and privacy cost.**

This makes cross-media expansion an evidence-based investment decision rather than a feature assumption.

---

# 17. Risk Assessment Method

Risks are assessed using:

### Likelihood

* Low
* Medium
* High

### Impact

* Low
* Medium
* High

The resulting priority is used to determine which risks require mitigation before Pilot or deployment.

---

# 18. Risk Matrix

| Risk                                                          | Category           | Likelihood | Impact      | Priority   | Mitigation                                                                  |
| ------------------------------------------------------------- | ------------------ | ---------- | ----------- | ---------- | --------------------------------------------------------------------------- |
| Semantic recommendations do not outperform existing discovery | Product            | Medium     | High        | **High**   | Controlled comparison against baseline before deployment                    |
| Users do not perceive sufficient paid value                   | Commercial         | Medium     | High        | **High**   | Test feature packaging, usage and conversion experimentally                 |
| Cross-media data provides little incremental value            | Product            | Medium     | Medium      | **Medium** | Compare Letterboxd-only vs cross-media models                               |
| Users are unwilling to connect external histories             | Adoption / Privacy | Medium     | Medium      | **Medium** | Keep external connections optional; measure opt-in                          |
| Incorrect metadata contaminates Taste Model                   | Data               | Medium     | High        | **High**   | Matching thresholds, quality gates, safe rejection                          |
| LLM semantic classification is inconsistent                   | AI                 | Medium     | Medium      | **Medium** | Fixed taxonomy, structured output, evaluation dataset                       |
| Model creates inaccurate or confusing taste explanations      | AI / UX            | Medium     | High        | **High**   | Evidence-backed explanations, user feedback and correction controls         |
| Sensitive attributes are inferred unnecessarily               | Privacy / AI       | Low–Medium | High        | **High**   | Explicitly prohibit sensitive/personality inference; minimize model scope   |
| External provider/API changes break integrations              | Dependency         | Medium     | Medium      | **Medium** | Modular connectors; exports as fallback; no core dependency on one provider |
| AI operating cost exceeds incremental value                   | Financial          | Medium     | High        | **High**   | Persist semantic vectors, caching, usage limits, cost monitoring            |
| Recommendation latency harms experience                       | Technical          | Medium     | Medium      | **Medium** | Offline enrichment, precomputed profiles, lightweight online scoring        |
| User preference profile becomes stale                         | Product / AI       | Medium     | Medium      | **Medium** | Incremental updates and recent-vs-long-term modelling                       |
| Cold-start users lack sufficient history                      | Product            | High       | Medium      | **High**   | Minimum-data threshold, onboarding signals, community baseline              |
| Cross-media data creates additional GDPR complexity           | Compliance         | High       | Medium–High | **High**   | Explicit opt-in, purpose limitation, minimization, deletion/export controls |
| Third-party data use conflicts with platform terms            | Legal / Dependency | Medium     | High        | **High**   | Provider-specific legal/terms review before production integration          |
| Commercial uplift is too small to justify maintenance         | Financial          | Medium     | High        | **High**   | Predefined commercial success gates before scaling                          |

---

# 19. Highest-Priority Risks

## 19.1 Recommendation Value Risk

The largest strategic risk is not that the AI fails technically.

It is that:

> **the system works technically but does not improve discovery enough to matter.**

Letterboxd already has strong social and community-driven discovery.

Taste Agent therefore needs to demonstrate **incremental** recommendation value.

### Mitigation

Pilot comparison:

```text
Existing / Baseline Discovery
        vs.
Letterboxd Semantic Model
        vs.
Cross-Media Semantic Model
```

No full deployment should occur without measurable improvement.

---

## 19.2 Commercial Value Risk

Users may enjoy Taste Agent without being willing to pay for it.

Engagement alone does not validate the business case.

### Mitigation

The Pilot should eventually connect product metrics to commercial experiments:

* feature activation
* repeat usage
* upgrade intent
* actual paid conversion
* renewal behaviour
* tier upgrades

Commercial rollout should require measurable incremental revenue rather than positive qualitative feedback alone.

---

## 19.3 AI Quality Risk

Structured output solves schema consistency but does not guarantee semantic correctness.

An LLM can still mischaracterize a film or book while returning perfectly valid JSON.

### Mitigation

Create a manually reviewed evaluation set and measure semantic-classification quality before production deployment.

Low-confidence or insufficient-metadata works should remain eligible for rejection.

---

## 19.4 Privacy and Trust Risk

Taste Agent processes and generates preference information.

Cross-media enrichment increases the amount and variety of behavioural data being combined.

The system must avoid expanding from:

> "This user tends to rate melancholic films highly."

into unsupported or unnecessary claims about:

* personality
* mental health
* political beliefs
* sexuality
* religion
* identity
* other sensitive characteristics

### Mitigation

Maintain the existing architectural principle:

> **Classify cultural works and observed preference relationships — not the user's personality or identity.**

Cross-media connections should be optional, transparent, purpose-limited, and removable.

Detailed requirements are addressed in:

`04-compliance.md`

---

## 19.5 Cost Risk

A conversational AI feature can become expensive if every interaction requires:

* full history retrieval
* repeated content classification
* large-context LLM calls
* unnecessary regeneration of the Taste Model

### Mitigation

Use a layered architecture:

```text
Expensive Operations
        ↓
Offline / Incremental
        ↓
Stored Results

Cheap Operations
        ↓
Online Recommendation
```

Semantic work vectors and long-term Taste Models should be persisted.

Only:

* new works
* meaningful profile updates
* current user intent

should require incremental processing.

Pilot instrumentation should measure:

```text
Cost per semantic classification

Cost per Taste Model update

Cost per recommendation

Cost per active Taste Agent user
```

before commercial deployment.

---

# 20. Risk-Based Deployment Gates

The project should progress only when predefined evidence thresholds are met.

## Gate 1 — POC → MVP

Required:

* structured semantic modelling works
* quality gates operate safely
* cross-media records can use shared taxonomy

**Current assessment: PASS**

---

## Gate 2 — MVP → Controlled Pilot

Required:

* functional recommendation engine
* evaluation framework
* basic user interface
* Python processing layer
* persistent semantic vectors
* privacy controls
* acceptable latency and cost

**Current assessment: NOT YET TESTED**

---

## Gate 3 — Pilot → Commercial Experiment

Required evidence:

* semantic recommendations outperform baseline
* explanations are considered useful
* unacceptable recommendation/error rates remain controlled
* cross-media value quantified
* operating cost within target range
* privacy and compliance review completed

---

## Gate 4 — Commercial Experiment → Full Deployment

Required evidence:

* measurable conversion, retention, or upsell effect
* positive expected contribution after AI operating cost
* acceptable technical reliability
* acceptable compliance and reputational risk
* clear user demand
* sustainable production architecture

---

# 21. Financial Decision Framework

The final production decision should not be based on:

> "AI recommendations are strategically interesting."

It should be based on:

```text
Incremental Subscription Value
+
Incremental Retention Value
+
Incremental Upsell Value

        >

Implementation
+
AI Operations
+
Infrastructure
+
Maintenance
+
Compliance
+
Risk
```

The commercial experiment should therefore establish three numbers:

### 1. Incremental Revenue per Exposed User

How much additional revenue does the feature actually generate?

### 2. Incremental Cost per Active User

How much does semantic personalization and conversational discovery cost to operate?

### 3. Incremental Contribution Margin

```text
Incremental Revenue
-
Incremental Operating Cost
=
Incremental Contribution
```

Only when incremental contribution is sustainably positive should broad deployment be recommended.

---

# 22. Assessment

The scenario model demonstrates that **positive ROI is economically plausible**, primarily because Letterboxd operates at substantial user scale while the proposed capability can initially be tested through a relatively contained Pilot.

Under the illustrative model:

| Metric                                          |                              Result |
| ----------------------------------------------- | ----------------------------------: |
| Initial implementation                          |                             $45,000 |
| Annual operations                               |                             $30,000 |
| Year-one total cost                             |                             $75,000 |
| 36-month total cost                             |                            $135,000 |
| Conversion-only year-one break-even             | ~3,948 additional Pro subscriptions |
| Break-even uplift across illustrative 5M cohort |             ~0.08 percentage points |

However, the financial model does **not demonstrate that Taste Agent will produce this uplift**.

The critical uncertainties remain:

* recommendation improvement
* user adoption
* willingness to pay
* retention impact
* cross-media incremental value
* actual AI operating cost

These variables should therefore become measurable Pilot KPIs rather than assumptions carried into deployment.

---

# 23. Recommendation

The financial case supports **continued investment at Pilot scale**, not immediate full deployment.

The next investment should remain intentionally limited and focused on resolving the highest-value uncertainties:

1. Does semantic modelling improve recommendation quality?
2. Does cross-media enrichment improve it further?
3. Do users repeatedly engage with the experience?
4. Does the feature influence willingness to pay or retention?
5. What is the real cost per active user?

If those results are positive, Letterboxd can replace the assumptions in this assessment with observed product data and build a production investment case.

If recommendation quality or commercial impact is weak, the project can be stopped after a controlled investment rather than after an expensive platform-wide implementation.

The investment logic is therefore:

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

This staged approach limits downside while preserving the potential upside of deploying semantic taste intelligence across a platform with more than 30 million members.

---

## Related Documentation

* [`01-use-case-business-case.md`](01-use-case-business-case.md) — Strategic opportunity and business case
* [`02-poc-feasibility.md`](02-poc-feasibility.md) — Technical feasibility evidence
* [`04-compliance.md`](04-compliance.md) — EU AI Act and GDPR assessment
* [`05-deployment-commercialisation.md`](05-deployment-commercialisation.md) — POC → Pilot → Production strategy
