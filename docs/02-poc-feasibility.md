# Taste Agent — POC Feasibility Report

**Project:** Taste Agent
**Stage:** Proof of Concept
**Implementation:** n8n + JavaScript + Structured LLM Output
**POC Question:** Can fragmented cultural-consumption data be transformed into a structured, explainable semantic Taste Model?

---

# 1. Purpose

The Taste Agent business case proposes using cultural-consumption history to build a semantic representation of user taste that could eventually support personalized and explainable film discovery.

Before investing in a recommendation engine, conversational interface, or production integration, the project first tests whether the underlying **Taste Model can be constructed reliably enough to justify further development**.

The POC therefore focuses on the foundational technical hypothesis:

> **Can consumption and rating history from different cultural media be enriched, semantically classified, and transformed into an interpretable model of preference?**

The POC does **not** attempt to validate the final Taste Agent product.

Specifically, it does not yet test:

* recommendation quality
* conversational recommendations
* user adoption
* paid conversion
* retention impact
* production scalability

Those questions belong to the MVP and Pilot stages.

---

# 2. POC Success Criteria

The POC was considered successful if it could demonstrate that:

1. cultural-consumption records could be processed through a common workflow
2. films and books could be enriched with usable metadata
3. uncertain metadata matches could be rejected rather than forced through the pipeline
4. cultural works could be represented using a consistent semantic taxonomy
5. LLM output could be constrained sufficiently for deterministic downstream analysis
6. semantic characteristics could be compared with explicit preference signals
7. the resulting output could be interpreted as a structured Taste Model
8. more than one cultural medium could be represented within the same framework

Success at this stage means **technical feasibility**, not validated recommendation performance.

---

# 3. POC Architecture

The workflow was implemented in **n8n**.

```text
Cultural Consumption Dataset
             │
             ▼
        Get Records
             │
             ▼
       Media Routing
             │
       ┌─────┴─────┐
       ▼           ▼
     Films        Books
       │           │
      TMDB     Google Books
       │           │
       ▼           ▼
   Metadata Matching
       │           │
       └─────┬─────┘
             ▼
       Unified Dataset
             │
             ▼
       Prepare for AI
             │
             ▼
       Quality Gate
             │
             ▼
   Semantic Classification
             │
             ▼
    Strict JSON Schema
     62 Dimensions
             │
             ▼
 Reattach Preference Data
             │
             ▼
 Preference Association
             │
             ▼
        Taste Model
```

The exported workflow is available at:

`poc/workflow/taste-agent-poc-v03.json`

---

# 4. Input Data

The POC models cultural-consumption records using a shared input structure.

Typical fields include:

```text
media_type
title
creator
year
user_rating
rating_scale_max
liked
consumed_date
source
source_id
preference_weight
```

The architecture was tested with:

* film records based on a Letterboxd-style dataset
* book records based on a Goodreads-style dataset

For the formal project submission, the reproducible dataset is provided as synthetic/mock data following the same schema.

The objective is to validate the **pipeline and modelling approach**, not to depend on personal user data.

---

# 5. Metadata Enrichment

Consumption exports provide preference signals but do not necessarily contain sufficient semantic information about the works themselves.

The POC therefore separates:

```text
USER SIGNALS

rating
like
consumption date
source

        from

CONTENT INFORMATION

description
genres/categories
release year
creator
metadata
```

External metadata is used to enrich each work before semantic classification.

## Films

Film records are searched through **TMDB**.

Candidate results are compared against the original record using normalized title and year information.

The initial film matching experiment achieved **19 automatic matches from 20 records**.

The remaining work was rejected rather than assigned an uncertain match.

## Books

Book records are searched through **Google Books**.

Book matching proved more difficult because of:

* translated titles
* editions
* series suffixes
* inconsistent author formatting
* missing descriptions
* incomplete categories
* publication-year differences

The matching logic was therefore expanded to consider:

* normalized title similarity
* author similarity
* publication year
* metadata completeness

A candidate must meet the required matching and metadata conditions before proceeding to semantic classification.

---

# 6. Quality Gate

One of the POC's design principles is:

> **An uncertain record should fail safely rather than generate confident semantic analysis from incorrect metadata.**

Records are therefore assigned a `ready_for_ai` state.

Only sufficiently matched and enriched records continue to semantic classification.

In the first combined film/book experiment:

```text
36 input works
30 passed quality gate
6 rejected
```

The rejected records included cases where:

* no reliable metadata match was available
* the candidate appeared to represent the wrong work
* descriptions or categories were insufficient for semantic classification

This produced an initial usable-record rate of approximately **83%**.

The objective was not to maximize throughput at any cost.

The quality gate exists specifically to reduce the risk of:

```text
Incorrect Metadata
        ↓
Incorrect Semantic Classification
        ↓
Incorrect Taste Signal
        ↓
Incorrect Recommendation
```

---

# 7. Semantic Taxonomy

Works passing the quality gate are classified against a fixed semantic taxonomy.

The final taxonomy contains **62 dimensions across nine groups**.

| Group               | Dimensions |
| ------------------- | ---------: |
| Themes              |         10 |
| Character           |          6 |
| Narrative           |          7 |
| Pacing & Energy     |          5 |
| Tone                |         12 |
| Style               |          9 |
| Accessibility       |          4 |
| Temporal / Cultural |          3 |
| Intensity           |          6 |
| **Total**           |     **62** |

Examples include:

### Themes

* identity
* love / desire
* grief
* class
* family
* alienation
* coming of age
* power
* morality
* friendship

### Narrative

* character-driven
* plot-driven
* nonlinear
* ambiguous
* episodic
* conventional
* complex

### Tone

* melancholic
* darkly comic
* romantic
* unsettling
* sentimental
* absurd
* ethereal
* bizarre
* joyful
* tense
* comforting
* playful

### Style

* naturalistic
* experimental
* minimalist
* maximalist
* dialogue-heavy
* atmospheric
* stylized
* surreal
* visual

Each dimension receives a semantic-presence score between:

```text
0.0 = characteristic absent / not meaningfully present

1.0 = characteristic strongly present
```

The taxonomy describes the **cultural work**, not the user.

---

# 8. Experiment 0 — Prompt-Only Classification

## Approach

The first implementation instructed the LLM through the system prompt to classify works using the desired semantic dimensions and return JSON.

No strict output schema was enforced.

## Result

The approach failed as a reliable quantitative pipeline.

Although the responses were semantically plausible, the model produced **schema drift**.

Examples included:

* different field structures between works
* renamed dimensions
* omitted dimensions
* newly invented dimensions
* inconsistent nesting

This meant outputs could not reliably feed downstream statistical analysis.

## Learning

> **Prompt instructions alone were insufficient to guarantee the structural consistency required for deterministic preference modelling.**

This became an important architectural finding.

LLMs could be used for semantic interpretation, but their output needed to be constrained before being used as structured analytical data.

---

# 9. Experiment 1 — Schema-Constrained Semantic Classification

## Change

The semantic classifier was redesigned using **strict structured output**.

A JSON Schema explicitly defines:

* all nine taxonomy groups
* all 62 dimensions
* expected numeric values
* required properties
* prohibition of additional properties

The model must therefore classify each work inside the predefined structure.

## Result

Schema drift was eliminated for the downstream workflow.

The same semantic structure could now be compared across all successfully processed works.

This transformed the LLM from:

```text
Free-Form Interpreter
```

into:

```text
Constrained Semantic Classifier
```

The distinction is important because the POC requires machine-readable output rather than prose descriptions.

## Learning

> **LLM semantic interpretation becomes significantly more useful for analytical pipelines when its output space is explicitly constrained.**

---

# 10. Separation of Content and Preference

The semantic classifier intentionally does **not** receive:

* user rating
* like status
* preference class
* preference weight

It receives information about the **work**.

This prevents the model from seeing the expected preference outcome while generating the semantic representation.

The pipeline therefore separates:

```text
CONTENT CLASSIFICATION

"What characteristics does this work contain?"

            from

PREFERENCE ANALYSIS

"Which characteristics are associated
with higher or lower ratings?"
```

This reduces target leakage and improves interpretability.

It also limits unnecessary exposure of behavioural preference data to the semantic-classification stage.

---

# 11. Experiment 2 — Continuous Preference Model

The initial feasibility experiment intentionally used strongly positive and negative examples.

This was useful for testing the architecture but was not representative enough for the final model.

The next experiment therefore introduced a larger, stratified sample and converted ratings into **continuous preference weights**.

| Rating | Preference Weight |
| -----: | ----------------: |
|    5.0 |             +1.00 |
|    4.5 |             +0.80 |
|    4.0 |             +0.60 |
|    3.5 |             +0.25 |
|    3.0 |              0.00 |
|    2.5 |             -0.25 |
|    2.0 |             -0.60 |
|    1.5 |             -0.80 |
|    1.0 |             -1.00 |
|    0.5 |             -1.00 |

This allows the system to preserve more information than a binary:

```text
LIKE / DISLIKE
```

classification.

A 3-star rating, for example, becomes neutral rather than being forced into either a positive or negative category.

---

# 12. Experiment 3 — Preference Association

The next challenge was determining how semantic dimensions should contribute to the Taste Model.

Simply calculating how often a dimension appears would answer:

> "What characteristics does this person consume?"

It would not answer:

> "What characteristics are associated with stronger preference?"

The final POC therefore calculates **Pearson correlation** between:

```text
Semantic Dimension Score
        and
Preference Weight
```

for each of the 62 dimensions.

The resulting `preference_association` ranges from:

```text
-1                          0                          +1

associated with        no observed              associated with
lower ratings          relationship              higher ratings
```

This is an association measure, not a causal claim.

---

# 13. Prevalence vs Preference

The model deliberately preserves **prevalence** separately.

For every semantic dimension:

```text
prevalence
=
average semantic presence
across consumed works
```

while:

```text
preference_association
=
relationship between
semantic presence and rating
```

This distinction produced an important POC finding.

A user can frequently consume a characteristic without that characteristic being strongly associated with higher ratings.

For example, in the POC output:

* `atmospheric` had relatively high prevalence
* but only weak positive preference association

while:

* `niche` appeared less frequently
* but showed a stronger positive association with rating

Therefore:

> **Consumption frequency alone should not be interpreted as preference strength.**

---

# 14. Final POC — v0.3

The final POC model processed:

| Metric                      |    Result |
| --------------------------- | --------: |
| Successfully analyzed works |   **107** |
| Films                       |    **96** |
| Books                       |    **11** |
| Semantic dimensions         |    **62** |
| Mean preference weight      | **0.282** |

The final Taste Model contains, for each semantic dimension:

* prevalence
* preference association
* evidence count
* evidence confidence
* evidence scope

`evidence_confidence` is a heuristic based on evidence volume and variation.

It should **not** be interpreted as a statistical probability or formal confidence interval.

---

# 15. Example Results

The strongest positive associations observed in the v0.3 POC included:

| Dimension        | Preference Association |
| ---------------- | ---------------------: |
| Friendship       |                 +0.288 |
| Contemplative    |                 +0.251 |
| Sentimental      |                 +0.249 |
| Family           |                 +0.246 |
| Character-driven |                 +0.239 |
| Identity         |                 +0.228 |
| Melancholic      |                 +0.226 |
| Comforting       |                 +0.204 |
| Grief            |                 +0.200 |
| Niche            |                 +0.195 |

The strongest negative associations included:

| Dimension         | Preference Association |
| ----------------- | ---------------------: |
| Plot-driven       |                 -0.261 |
| Suspense          |                 -0.229 |
| Tense             |                 -0.173 |
| Power             |                 -0.143 |
| Morally ambiguous |                 -0.120 |
| Unsettling        |                 -0.114 |
| Moderate pacing   |                 -0.102 |
| Dialogue-heavy    |                 -0.098 |

Some dimensions produced associations close to zero.

For example:

* outsider protagonist: approximately +0.002
* contained: approximately -0.007
* complex: approximately +0.015
* maximalist: approximately +0.016

This is useful because the model is not forced to describe every dimension as meaningful.

---

# 16. Interpretation

Within the POC sample, higher ratings tended to be associated with characteristics including:

* character-driven narratives
* contemplative pacing
* friendship
* family
* identity
* melancholic and sentimental tones

Lower ratings showed modest associations with characteristics including:

* plot-driven narratives
* suspense
* tense tone

These results describe **relationships within the analyzed cultural-consumption sample**.

They should not be interpreted as:

* personality traits
* psychological characteristics
* identity attributes
* universal preferences
* causal relationships

The Taste Model describes observed relationships between **semantic characteristics of cultural works and explicit rating behaviour**.

---

# 17. Cross-Media Feasibility

One of the project's broader hypotheses is that cultural taste can be represented across more than one medium.

The final POC processed:

```text
96 films
+
11 books
=
107 works
```

through the same 62-dimensional semantic framework.

This demonstrates **technical compatibility across film and literature**.

It does not yet demonstrate that book data improves film recommendations.

The book sample is also substantially smaller than the film sample.

Cross-media findings should therefore be considered exploratory.

A future Pilot should explicitly compare:

```text
Film-only Taste Model
        vs.
Cross-media Taste Model
```

to determine whether external cultural histories provide measurable incremental recommendation value.

Spotify is proposed as a future third data source but was **not implemented in the current POC**.

---

# 18. Safe Failure as a POC Finding

The POC deliberately does not attempt to process every input at all costs.

A work can fail because:

* no reliable metadata match exists
* metadata is insufficient
* candidate confidence is too low
* semantic classification fails
* structured output is invalid

In these cases, the preferred behaviour is:

```text
NO RESULT
```

rather than:

```text
LOW-QUALITY INPUT
        ↓
CONFIDENT AI OUTPUT
```

This is particularly important because errors early in the pipeline propagate into the final Taste Model.

The quality gate therefore represents a feature of the architecture rather than merely an implementation limitation.

---

# 19. Technical Feasibility Findings

The POC produced several practical findings.

### Finding 1 — Metadata enrichment is necessary

Consumption histories alone do not provide sufficient semantic information.

### Finding 2 — Metadata matching is a meaningful source of risk

Books are particularly difficult because of editions, translations, titles, authors, and incomplete metadata.

### Finding 3 — LLM output requires structural control

Prompt-only classification produced schema drift.

Strict structured output solved the downstream consistency problem.

### Finding 4 — Content classification and preference analysis should remain separate

The semantic classifier should describe the work without knowing the user's rating.

### Finding 5 — Consumption frequency is not equivalent to preference

Prevalence and preference association must be represented separately.

### Finding 6 — Cross-media representation is technically possible

Film and book data can pass through the same semantic framework.

### Finding 7 — Semantic enrichment should not be repeated unnecessarily

LLM classification is one of the more expensive and slow stages.

A production architecture should classify each cultural work once, persist its semantic vector, and reuse it across users where legally and technically appropriate.

---

# 20. Implementation Trade-Off — JavaScript vs Python

Custom deterministic processing within the POC was implemented using **JavaScript Code nodes inside n8n**.

Python had initially been considered for these components.

However, during the time-boxed POC, JavaScript provided the most reliable and immediately compatible execution path within the n8n environment.

The implementation decision therefore prioritized:

> **validating the hypothesis over rewriting functioning POC logic solely to change programming language.**

This does not define the intended MVP architecture.

For the next stage, deterministic components are planned to move to Python, particularly:

* data normalization
* semantic-vector processing
* statistical analysis
* recommendation scoring
* evaluation

n8n can remain responsible for orchestration where appropriate.

The intended progression is therefore:

```text
POC

n8n
+
JavaScript
+
APIs
+
LLM
        ↓

MVP

n8n orchestration
+
Python processing
+
Recommendation Engine
+
Evaluation Framework
```

---

# 21. Production Architecture Implication

The POC currently performs semantic classification as part of the workflow.

At production scale, repeatedly classifying the same work would be inefficient.

A more appropriate architecture would separate semantic enrichment from recommendation-time processing.

```text
NEW CULTURAL WORK

Metadata Enrichment
        ↓
Semantic Classification
        ↓
Persist 62D Semantic Vector
        ↓
Reusable Content Representation
```

Then:

```text
USER HISTORY
      +
Stored Semantic Vectors
      ↓
Taste Model
      ↓
Candidate Retrieval
      ↓
Recommendation Scoring
      ↓
Taste Agent
```

Only previously unseen works would require new semantic classification.

This reduces:

* LLM calls
* latency
* inference cost
* duplicate processing

and makes the system more suitable for production-scale experimentation.

---

# 22. Limitations

The POC has several important limitations.

## Dataset Size

107 successfully analyzed works are sufficient for feasibility testing but not for production-level preference modelling.

## Cross-Media Imbalance

The final sample contains 96 films but only 11 books.

Cross-media conclusions are therefore exploratory.

## Semantic Ground Truth

The 62-dimensional semantic scores are LLM-generated classifications.

Structured output guarantees format, not semantic correctness.

## Metadata Dependence

Classification quality depends on the quality of external metadata.

## Correlation

Pearson association identifies relationships within the sample.

It does not establish causation.

## Recommendation Performance

The POC does not yet test whether the Taste Model produces better recommendations.

## User Validation

No controlled user study has yet established whether users find the model accurate, useful, or trustworthy.

## Commercial Validation

The POC provides no direct evidence of conversion, retention, or willingness to pay.

---

# 23. POC Conclusion

The POC supports the project's initial technical hypothesis.

> **Heterogeneous cultural-consumption data can be transformed into a structured and interpretable semantic Taste Model using a low-code AI pipeline.**

The POC demonstrates:

* multi-source data ingestion
* metadata enrichment
* safe metadata matching
* controlled semantic classification
* schema-constrained LLM output
* continuous preference modelling
* interpretable semantic associations
* cross-media technical compatibility

However, the POC does **not** establish that Taste Agent should be deployed.

Instead, it reduces the first major uncertainty:

```text
Can the underlying Taste Model
be constructed?

        YES — technically feasible
```

The next uncertainty is:

```text
Does using this model actually
produce better discovery?

        NOT YET TESTED
```

The appropriate next step is therefore an **MVP / controlled Pilot** comparing:

1. a conventional discovery baseline
2. a Letterboxd-only semantic Taste Model
3. a cross-media semantic Taste Model

The Pilot should determine whether the additional semantic intelligence produces sufficiently better recommendations to justify its technical, financial, and privacy costs.

---

## Related Documentation

* [`01-use-case-business-case.md`](01-use-case-business-case.md) — Why the opportunity is commercially relevant
* [`03-roi-risk-assessment.md`](03-roi-risk-assessment.md) — Whether the potential value justifies cost and risk
* [`04-compliance.md`](04-compliance.md) — EU AI Act and GDPR implications
* [`05-deployment-commercialisation.md`](05-strategic-deployment-plan.md) — How the project could progress from POC to production
