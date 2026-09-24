# Taste Agent — EU AI Act & GDPR Assessment

**Client Case:** Letterboxd
**Project:** AI-Powered Cross-Media Taste Intelligence
**Scope:** Proposed MVP / Pilot and potential production deployment
**Jurisdiction:** European Union

---

# 1. Purpose

Taste Agent would process cultural-consumption histories to construct a semantic representation of user preferences and use that representation for personalized film discovery.

This creates two primary EU regulatory considerations:

1. **EU Artificial Intelligence Act**
2. **General Data Protection Regulation (GDPR)**

The compliance objective is not simply to determine whether the product is legally permissible.

The system should be designed so that:

> **personalization remains useful without expanding unnecessarily into sensitive profiling, opaque inference, or excessive collection of behavioural data.**

This assessment covers:

* AI Act classification
* AI transparency
* GDPR roles
* personal-data categories
* profiling
* lawful basis
* purpose limitation
* data minimization
* cross-media data
* special-category inference
* automated decision-making
* data-subject rights
* retention
* international transfers
* DPIA requirements
* privacy-by-design controls

This document is a project-level compliance assessment and would require validation by qualified legal/privacy teams before production deployment.

---

# 2. Proposed Processing

At production level, Taste Agent could process three principal categories of information.

## 2.1 Letterboxd Data

Examples:

* watched films
* ratings
* likes
* diary history
* watchlists
* reviews
* lists
* interaction history

This represents the core data source.

---

## 2.2 Optional External Cultural Data

Users could optionally connect or import histories from other cultural platforms.

Examples include:

* Goodreads book history
* Spotify listening history
* future compatible cultural platforms

These connections are not required for the Letterboxd-only Taste Model.

The current POC demonstrated cross-media technical compatibility using film and Goodreads-style book histories.

Spotify is proposed as a future integration but was not implemented in the current POC.

---

## 2.3 Derived Taste Data

Taste Agent would create new information from the original behavioural data.

Examples include:

* semantic preference associations
* long-term Taste Model
* recent taste patterns
* preference changes
* recommendation scores
* recommendation explanations

These inferred outputs must also be treated as personal data when they relate to an identifiable user.

---

# 3. Simplified Data Flow

```text
USER
 │
 ├── Letterboxd History
 │
 ├── Optional Goodreads Data
 │
 └── Optional Spotify Data
          │
          ▼
   Data Normalization
          │
          ▼
   Metadata Enrichment
          │
          ▼
Stored Semantic Work Vectors
          │
          +
   User Preference Signals
          │
          ▼
       Taste Model
          │
          ▼
 Recommendation Engine
          │
          ▼
      Taste Agent
          │
          ▼
 Personalized Discovery
```

An important production distinction is that semantic descriptions of cultural works should be separated from individual user preference data wherever possible.

For example:

```text
FILM

"Melancholic: 0.8"
"Character-driven: 0.9"

        ≠

USER

"Strong positive association
with melancholic works"
```

This separation supports data minimization and reduces unnecessary transmission of behavioural data to external AI providers.

---

# 4. EU AI Act Classification

The EU AI Act applies a risk-based framework.

The principal categories relevant to system assessment are:

* prohibited AI practices
* high-risk AI systems
* systems subject to specific transparency obligations
* other limited/minimal-risk AI systems

Taste Agent must therefore be assessed according to its **intended purpose**, not simply because it uses an LLM.

---

# 5. Prohibited AI Practices

The proposed Taste Agent does not require practices such as:

* social scoring
* prohibited manipulative techniques
* biometric categorization
* emotion recognition in prohibited contexts
* predictive policing
* prohibited biometric identification

The proposed use case therefore does not appear to fall within the AI Act's prohibited-practice categories.

### Assessment

**Not prohibited under the proposed design.**

---

# 6. High-Risk AI Assessment

Taste Agent is designed for:

> **cultural preference modelling and entertainment recommendation.**

It is not intended to determine access to:

* employment
* education
* credit
* essential public/private services
* law enforcement
* migration
* justice
* democratic participation
* other high-risk contexts identified by the AI Act

Its recommendations also do not determine access to significant rights or opportunities.

### Assessment

> **Taste Agent is not classified as a high-risk AI system under the proposed intended purpose.**

This conclusion depends on maintaining that intended purpose.

If the underlying Taste Model were later reused for materially different purposes — for example eligibility, employment, insurance, credit, or other consequential profiling — the regulatory assessment would need to be performed again.

---

# 7. AI Transparency

The user-facing Taste Agent would provide conversational AI interactions.

Users should therefore be clearly informed that they are interacting with an AI system.

The interface should not create the impression that Taste Agent is a human Letterboxd employee or human curator.

A suitable disclosure could be:

> **Taste Agent is an AI-powered discovery assistant. Its recommendations are generated using your Taste Model and may not always be accurate.**

Transparency should appear at the interaction level rather than being hidden only within Terms & Conditions.

Recommendation explanations should also distinguish between:

* observed user behaviour
* calculated associations
* AI-generated interpretation

For example:

> "You have historically rated character-driven and contemplative films more highly."

is preferable to:

> "You are an introspective person who needs emotionally complex stories."

The first describes observed cultural-preference evidence.

The second makes an unnecessary inference about the person.

---

# 8. General-Purpose AI Model Responsibilities

Taste Agent would likely use a third-party general-purpose AI model through an API.

The provider of that underlying GPAI model has separate obligations under the AI Act.

Letterboxd would generally be responsible for the **Taste Agent application/system it deploys**, rather than becoming the provider of the underlying GPAI model merely because it uses the API.

However, this allocation would need reassessment if Letterboxd:

* substantially modified the underlying model
* released its own general-purpose model
* otherwise met the legal definition of a GPAI model provider

Vendor due diligence should therefore form part of deployment.

Relevant checks include:

* AI Act documentation
* data-processing terms
* security controls
* model changes
* data retention
* training-on-customer-data policies
* geographic processing locations

---

# 9. GDPR Applicability

Taste Agent would process information relating to identifiable Letterboxd users.

Examples include:

* viewing history
* ratings
* likes
* reading history
* listening history
* inferred preferences
* Taste Models
* recommendation interactions

These are personal data where they relate to an identified or identifiable user.

The fact that a dataset does not contain a name or email address does **not** automatically make it anonymous.

A preference history linked to an internal user identifier can remain pseudonymised personal data.

The GDPR therefore applies to the proposed production system.

---

# 10. Controller and Processor Roles

For a native Letterboxd implementation, Letterboxd would likely act as the **data controller** for the Taste Agent service because it would determine:

* why Taste Agent processes personal data
* what data is used
* how the personalization feature operates
* how long information is retained
* which processors are involved

External providers could act as processors depending on the contractual and technical arrangement.

Potential processors could include:

* cloud infrastructure providers
* LLM API providers
* analytics services
* database providers

Each relationship would require appropriate contractual and security assessment.

Where a third party determines its own purposes for personal data, the role may differ and must be assessed separately.

---

# 11. Personal Data Inventory

| Data                   | Category                      | Source                   | Purpose                            |
| ---------------------- | ----------------------------- | ------------------------ | ---------------------------------- |
| Film history           | Behavioural personal data     | Letterboxd               | Taste modelling                    |
| Ratings                | Preference data               | Letterboxd               | Preference weighting               |
| Likes                  | Preference data               | Letterboxd               | Optional taste signal              |
| Diary history          | Behavioural data              | Letterboxd               | Temporal modelling                 |
| Watchlist              | Intent data                   | Letterboxd               | Discovery                          |
| Book history           | Behavioural / preference data | Optional external import | Cross-media enrichment             |
| Listening history      | Behavioural / preference data | Optional external import | Cross-media enrichment             |
| Semantic Taste Model   | Inferred personal data        | Taste Agent              | Personalization                    |
| Recent taste           | Inferred personal data        | Taste Agent              | Temporal personalization           |
| User prompt            | User-provided personal data   | Taste Agent              | Current intent                     |
| Recommendation history | Interaction data              | Taste Agent              | Product functionality / evaluation |

The production system should maintain a more detailed Record of Processing Activities where required.

---

# 12. Profiling

Taste Agent systematically evaluates aspects of a person's cultural preferences using automated processing.

It should therefore be treated as **profiling for GDPR compliance purposes**.

The profile is used to personalize entertainment recommendations.

This requires particular attention to:

* transparency
* lawful basis
* user rights
* data accuracy
* purpose limitation
* minimization
* inferred data

Profiling itself is not prohibited by the GDPR.

The compliance question is whether the processing has an appropriate lawful basis and whether the user's rights and freedoms are adequately protected.

---

# 13. Article 22 — Automated Decision-Making

GDPR Article 22 concerns certain decisions based solely on automated processing that produce legal effects or similarly significantly affect an individual.

Taste Agent recommends cultural content.

A recommendation such as:

> "You may enjoy this film."

does not ordinarily determine a legal right or produce a similarly significant effect.

### Assessment

> **Taste Agent's core recommendation use case is unlikely to fall within the Article 22 prohibition on solely automated decisions with legal or similarly significant effects.**

However, this assessment would change if the Taste Model were reused for consequential decisions unrelated to cultural discovery.

Purpose limitation is therefore important.

The Taste Model should not silently become a general-purpose behavioural profile for unrelated decision-making.

---

# 14. Lawful Basis

A lawful basis under GDPR Article 6 must be identified for each processing purpose.

The appropriate basis may differ between:

1. core Letterboxd personalization
2. optional cross-media enrichment
3. analytics/evaluation
4. marketing or unrelated secondary uses

## Core Taste Agent

For a voluntarily activated personalization feature integrated into a paid Letterboxd product, possible legal bases could include:

* performance of a contract, where the processing is objectively necessary to deliver a service the user has requested
* legitimate interests, where appropriate and after balancing against user rights
* consent, where the processing is genuinely optional and the required conditions are met

The final basis must be determined from the final product design rather than selected solely for convenience.

---

# 15. Cross-Media Data — Recommended Approach

Cross-media enrichment creates a materially different privacy context.

The user would actively provide cultural history from another service for an additional personalization purpose.

Examples:

```text
Goodreads → Taste Agent

Spotify → Taste Agent
```

For the proposed design, the strongest privacy-by-design approach is:

> **Make cross-media enrichment explicitly optional and user initiated.**

The interface should clearly explain:

* which source is being connected
* what data will be imported
* why it is being imported
* how it changes the Taste Model
* whether it is stored
* how the user can disconnect it
* how the imported data and derived profile can be deleted

Consent, where used as the lawful basis, must meet GDPR requirements including being freely given, specific, informed and unambiguous, and capable of withdrawal.

A user who does not connect Goodreads or Spotify should still be able to use the core Letterboxd Taste Model.

---

# 16. Purpose Limitation

Data collected for cultural discovery should remain limited to cultural discovery and clearly compatible product purposes.

For example:

```text
ACCEPTABLE INTENDED PURPOSE

Film history
      ↓
Taste Model
      ↓
Film recommendation
```

should not silently become:

```text
FUNCTION CREEP

Film + Book + Music History
        ↓
Behavioural Profile
        ↓
Advertising / Political Profiling /
Credit / Employment / Other Decisions
```

Any materially new purpose would require a separate legal assessment and potentially a new lawful basis.

The safest architecture is therefore to keep the Taste Model purpose-specific.

---

# 17. Data Minimization

Taste Agent should collect only information necessary for personalization.

For example, Spotify exports may contain substantially more information than the Taste Model requires.

The system should not import an entire account archive simply because it is technically available.

Instead:

```text
External Export
      ↓
Filter Required Fields
      ↓
Normalize
      ↓
Taste Model
```

Possible required information could include:

* work identifier
* creator
* rating or behavioural preference signal
* consumption date where temporal modelling is enabled

Information unrelated to cultural preference modelling should be discarded or never imported.

---

# 18. Separation of Semantic Classification and User Preference

The POC already implements a useful privacy-by-design principle.

The LLM semantic classifier receives information about the **cultural work**, but not the user's:

* rating
* like status
* preference weight
* preference class

The model therefore answers:

> "What semantic characteristics are present in this work?"

rather than:

> "What does this person's reaction to this work reveal about them?"

This separation should be maintained in production where possible.

It reduces:

* unnecessary behavioural-data sharing
* target leakage
* sensitive inference risk
* external AI-provider exposure

---

# 19. Special-Category Data Risk

Cultural consumption can sometimes reveal or strongly suggest sensitive information.

For example, books, films, music, reviews, or behavioural patterns could potentially reveal information concerning:

* political opinions
* religious or philosophical beliefs
* health
* sexual orientation
* racial or ethnic origin
* other Article 9 categories

The risk increases when multiple cultural histories are combined.

Importantly, inferred information may itself fall within special-category protections.

Taste Agent should therefore deliberately avoid attempting to infer such characteristics.

The model should remain focused on content-level dimensions such as:

```text
melancholic
character-driven
experimental
friendship
family
contemplative
nonlinear
```

and not convert them into claims such as:

```text
politically progressive
religious
depressed
LGBTQ+
ethnic identity
personality diagnosis
```

even where an AI model might technically be capable of making such inferences.

---

# 20. Sensitive-Inference Guardrail

A production classifier should contain an explicit policy such as:

> **Do not infer or predict personality, mental health, political beliefs, religious beliefs, sexuality, ethnicity, health status, or other sensitive personal attributes from cultural-consumption history.**

This should be implemented through more than prompt wording.

Controls should include:

* restricted taxonomy
* prohibited inference categories
* output schema
* evaluation tests
* monitoring
* user-reporting mechanism
* periodic review of generated explanations

The current 62-dimensional POC taxonomy intentionally describes **cultural characteristics rather than personal identity**.

---

# 21. Transparency to Users

Users should understand:

### What data is used

For example:

> "Your Taste Model uses your ratings and viewing history."

### What external data is connected

For example:

> "You connected Goodreads. Your book ratings are now contributing to your Taste Model."

### What is inferred

For example:

> "Taste Agent identifies patterns between the characteristics of works and how you rated them."

### What AI does

For example:

> "AI helps classify the themes, tone and style of cultural works."

### What AI does not do

For example:

> "Taste Agent is designed to model cultural preferences, not infer sensitive personal characteristics."

Transparency should be layered so users can access additional detail without overwhelming the core product experience.

---

# 22. Explainability

Taste Agent should avoid unsupported recommendation explanations.

Instead of:

> "This is a 94% match for you."

where the percentage has no validated probabilistic meaning, explanations should be evidence-based.

For example:

> "You have historically rated character-driven and contemplative films more highly. This film strongly contains both characteristics."

Where cross-media evidence contributes:

> "This recommendation also shares themes that appear frequently among books you rated highly."

The system should distinguish clearly between:

* observed data
* calculated statistical association
* AI-generated semantic classification
* recommendation inference

---

# 23. User Control and Correction

Users should be able to influence or correct the profile.

Potential controls include:

### View

"What does Taste Agent think I like?"

### Explain

"Why is this part of my Taste Model?"

### Correct

"This does not represent my taste."

### Disconnect

"Stop using my Goodreads data."

### Reset

"Delete my Taste Model and rebuild it."

### Disable

"Do not use Taste Agent personalization."

These controls improve both user trust and data accuracy.

---

# 24. GDPR Data-Subject Rights

The system design must support applicable GDPR rights, including:

* right to information
* right of access
* right to rectification
* right to erasure
* right to restriction
* right to object where applicable
* right to data portability where applicable

Derived Taste Model data should not be treated as invisible simply because it was generated algorithmically.

A production data model should therefore maintain sufficient linkage and provenance to identify:

```text
Source Data
      ↓
Derived Taste Model
      ↓
Recommendation History
```

for deletion, access, and correction workflows.

---

# 25. Data Portability

Cross-media Taste Agent is partly enabled by the broader concept of data portability.

Where users obtain their cultural history from another service and choose to provide it to Taste Agent, the system should use interoperable and structured formats where practical.

Examples include:

* CSV
* JSON
* standardized internal schemas

However, the existence of a portability right does not automatically authorize every downstream use of imported data.

Once imported into Taste Agent, Letterboxd remains responsible for establishing an appropriate lawful basis, purpose, transparency, and retention policy for its own processing.

---

# 26. Retention

Taste Agent should not retain raw imported data indefinitely by default.

A production retention policy should distinguish between:

### Raw Import

Original Goodreads / Spotify export.

Potential approach:

> Delete after normalization and successful ingestion unless retention is genuinely necessary.

### Normalized Consumption History

Retain while required to provide the Taste Model, subject to account settings and deletion rights.

### Taste Model

Retain while personalization is active.

### Conversational History

Retain only where necessary and according to a clearly defined period.

### Logs

Minimize personal content and establish operational retention periods.

Retention periods should be documented rather than expressed as indefinite storage.

---

# 27. International Data Transfers

External AI, cloud, analytics, or infrastructure providers may process personal data outside the European Economic Area.

Before deployment, Letterboxd should identify:

* processor location
* sub-processors
* storage region
* inference region
* support-access locations

Where personal data is transferred internationally, an appropriate GDPR transfer mechanism must be established.

Depending on the destination and provider, this could involve:

* adequacy decision
* Standard Contractual Clauses
* supplementary measures where required

Vendor architecture should preferentially minimize unnecessary international transfers.

---

# 28. Security

Taste Agent combines behavioural histories that could become sensitive if exposed.

Appropriate security measures should include:

* encryption in transit
* encryption at rest
* role-based access
* least-privilege permissions
* secure secrets management
* logging and monitoring
* environment separation
* incident response
* processor security review
* deletion controls

External cultural histories should not be exposed through logs or debugging interfaces unnecessarily.

---

# 29. DPIA Assessment

GDPR Article 35 requires a Data Protection Impact Assessment where processing is likely to result in a high risk to individuals' rights and freedoms.

Taste Agent includes several characteristics that make a DPIA appropriate before production deployment:

* profiling
* systematic analysis of user preferences
* inferred personal data
* large potential user population
* AI processing
* potential cross-platform data combination
* potential special-category inference risk
* new technological processing

### Recommendation

> **Complete a DPIA before production Pilot/deployment involving real users and personal cultural histories.**

The DPIA should evaluate:

1. processing purposes
2. necessity
3. proportionality
4. categories of personal data
5. profiling logic
6. cross-media combination
7. AI providers
8. international transfers
9. risks to data subjects
10. mitigation measures
11. residual risk

If high residual risk remains that cannot be sufficiently mitigated, consultation with the relevant supervisory authority may be required before processing.

---

# 30. DPIA Risk Snapshot

| Risk to User                        | Likelihood | Impact      | Control                                      |
| ----------------------------------- | ---------- | ----------- | -------------------------------------------- |
| Incorrect Taste Model               | Medium     | Low–Medium  | Correction and reset controls                |
| Unexpected profiling                | Medium     | Medium      | Clear activation and transparency            |
| Sensitive inference                 | Low–Medium | High        | Restricted taxonomy and inference guardrails |
| Cross-media function creep          | Medium     | High        | Purpose limitation                           |
| External-data overcollection        | Medium     | Medium      | Field-level minimization                     |
| Data breach                         | Low–Medium | High        | Security controls and minimization           |
| Unclear AI recommendation           | Medium     | Medium      | Evidence-based explanations                  |
| Loss of control over connected data | Medium     | Medium      | Disconnect and deletion controls             |
| Third-party processor exposure      | Medium     | Medium–High | Vendor review and data-processing agreements |

Residual risk should be reassessed after the final technical architecture is known.

---

# 31. Privacy by Design

Privacy controls should be architectural rather than added after development.

The proposed design principles are:

### Letterboxd-First

Taste Agent must work using Letterboxd data alone.

### External Data Is Optional

No user should need to connect Goodreads, Spotify, or another platform to access the core product.

### Minimize Before AI

Remove unnecessary fields before data reaches AI services.

### Separate Content from User

Semantic work classification should occur independently from individual preference analysis where possible.

### Avoid Sensitive Inference

The system models cultural preferences, not identity or personality.

### Explain Recommendations

Recommendations should reference observable evidence.

### Give Users Control

Users can inspect, correct, disconnect, reset, or disable personalization.

### Process Incrementally

Do not repeatedly send complete user histories to AI models when stored semantic representations can be reused.

---

# 32. POC Compliance Position

The current formal POC uses **synthetic/mock data** for reproducibility and submission.

It therefore does not require production processing of real Letterboxd, Goodreads, or Spotify user data.

The POC nevertheless implements several controls relevant to future deployment:

* user preference signals are separated from semantic classification
* the semantic taxonomy is fixed
* sensitive/personality inference is explicitly excluded
* uncertain metadata can fail safely
* structured output limits uncontrolled model generation
* only necessary content metadata is passed to the classifier

These controls do not make the future production product automatically GDPR compliant.

They demonstrate that privacy and AI-governance considerations have influenced the architecture from the POC stage.

---

# 33. Compliance Requirements by Stage

| Requirement                   |     POC     |    MVP    |                         Pilot                        | Production |
| ----------------------------- | :---------: | :-------: | :--------------------------------------------------: | :--------: |
| Synthetic/mock data           |      ✓      | Preferred |                           —                          |      —     |
| AI risk classification        |      ✓      |   Review  |                        Review                        |  Maintain  |
| Restricted semantic taxonomy  |      ✓      |     ✓     |                           ✓                          |      ✓     |
| Sensitive inference guardrail |      ✓      |     ✓     |                           ✓                          |      ✓     |
| Privacy notice                |      —      |   Draft   |                           ✓                          |      ✓     |
| Cross-media opt-in            |      —      | Prototype |                           ✓                          |      ✓     |
| Data deletion controls        |      —      | Prototype |                           ✓                          |      ✓     |
| DPIA                          | Preliminary |   Draft   | **Required before real-data Pilot where applicable** |  Maintain  |
| Processor agreements          |      —      |   Review  |                           ✓                          |      ✓     |
| Transfer assessment           |      —      |   Review  |                           ✓                          |      ✓     |
| AI transparency disclosure    |      —      |     ✓     |                           ✓                          |      ✓     |
| Security review               |    Basic    |     ✓     |                           ✓                          | Continuous |
| Monitoring                    |    Basic    |   Build   |                           ✓                          | Continuous |

---

# 34. Compliance Decision

Based on the proposed intended purpose:

### EU AI Act

```text
Prohibited AI
      NO

High-Risk AI
      NO under current intended purpose

AI Transparency
      YES for conversational AI interaction

GPAI Provider Obligations
      Primarily underlying model provider,
      subject to final architecture
```

### GDPR

```text
Personal Data Processing
      YES

Profiling
      YES

Article 22 Significant Automated Decision
      Unlikely for entertainment recommendations

Cross-Media Processing
      Optional + enhanced transparency/control

Special-Category Risk
      YES — must be actively prevented/minimized

DPIA
      Recommended before real-user production Pilot
      and potentially required depending on final design

Data Subject Rights
      Must be supported
```

The proposed use case is therefore **not inherently incompatible with EU regulation**, but compliance depends heavily on how the system is implemented.

---

# 35. Recommendation

Taste Agent can progress to MVP/Pilot provided that privacy and AI governance remain part of the product architecture.

Before processing real cross-media user histories at Pilot scale, Letterboxd should:

1. finalize the processing purposes and lawful bases
2. complete the DPIA
3. establish user-facing AI and profiling transparency
4. implement explicit controls for external data connections
5. validate processor and international-transfer arrangements
6. implement deletion, correction, reset and disconnect mechanisms
7. maintain the restricted semantic taxonomy
8. test for sensitive-attribute inference
9. establish semantic-classification and recommendation monitoring
10. document model and data lineage

The central compliance principle should remain:

> **Taste Agent should understand what characteristics a user responds to in culture without attempting to determine who that user is as a person.**

This boundary reduces regulatory risk while remaining sufficient for the product's intended purpose: better cultural discovery.

---

## Related Documentation

* [`01-use-case-business-case.md`](01-use-case-business-case.md) — Strategic and commercial rationale
* [`02-poc-feasibility.md`](02-poc-feasibility.md) — Technical feasibility and AI architecture
* [`03-roi-risk-assessment.md`](03-roi-risk-assessment.md) — Financial and operational risk assessment
* [`05-deployment-commercialisation.md`](05-strategic-deployment-plan.md) — Deployment and commercialization strategy
