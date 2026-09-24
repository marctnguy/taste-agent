# Taste Agent — Use Case & Business Case

**Client Case:** Letterboxd
**Industry:** Digital Media & Entertainment
**Project:** AI-Powered Cross-Media Taste Intelligence
**Stage:** Proof of Concept → Proposed MVP / Pilot

---

## 1. Executive Summary

Letterboxd has grown from approximately **10 million members at the time of Tiny's majority acquisition in 2023 to more than 30.7 million members by Q2 2026**, representing 185% growth since acquisition.

At the same time, Letterboxd operates a freemium model in which paid membership is strategically important. Letterboxd identifies membership fees as its chief source of income and measures its success partly by the number of members choosing to financially support the platform.

This creates an opportunity to turn one of Letterboxd's strongest existing assets — its rich first-party preference data — into a more sophisticated premium discovery capability.

**Taste Agent** is a proposed AI-powered taste-intelligence layer that transforms cultural-consumption history into a structured and explainable **Taste Model**.

Letterboxd data provides the core of the model through signals such as film ratings and viewing history. Users could optionally enrich this model with their consumption histories from other cultural platforms.

The current POC demonstrates this cross-media approach by processing **Letterboxd film history and Goodreads book history within the same 62-dimensional semantic framework**. A future implementation could extend the architecture to additional sources such as Spotify.

This creates a broader proposition than a conventional film recommendation system:

> **Instead of modelling only what films a user likes, Taste Agent models cultural characteristics the user responds to across media and applies that intelligence back to film discovery.**

The commercial hypothesis is that deeper and more explainable personalized discovery could create additional value for Letterboxd's paid offering through conversion, retention, and tier differentiation.

The current POC tests the technical feasibility of constructing this semantic Taste Model. Recommendation quality, user adoption, and commercial impact remain hypotheses to validate through the MVP and a controlled Pilot.

---

# 2. Client Context

## 2.1 Letterboxd

Letterboxd is a global social platform for film discovery, logging, rating, reviewing, and discussion.

Its core product naturally generates a particularly rich set of explicit and behavioural preference signals:

* watched films
* ratings
* likes
* diary entries
* reviews
* lists
* watchlists
* social activity

Letterboxd describes its purpose around providing a place for members to record and share their "life in film."

The company also states that it measures success through the size and activity of its community and the number of members choosing to support the platform financially.

This makes personalized discovery strategically relevant without requiring Letterboxd to fundamentally change its existing product model.

---

## 2.2 Strong User Growth

Letterboxd has experienced rapid membership growth following Tiny's majority acquisition.

| Period                     | Members |
| -------------------------- | ------: |
| September 2023 acquisition |    ~10M |
| Q4 2025                    |   26.1M |
| Q1 2026                    |    29M+ |
| Q2 2026                    |   30.7M |

By Q2 2026, Tiny reported that Letterboxd had surpassed **30.7 million members**, representing 43% year-over-year growth and 185% growth since acquisition.

Rapid user growth increases both the volume of preference data available to Letterboxd and the potential commercial impact of improvements in paid conversion, retention, or engagement.

---

# 3. Existing Business Model

Letterboxd operates a freemium membership model.

The core service remains free, while additional functionality is offered through annual **Pro** and **Patron** subscriptions.

At the time of this analysis, standard web pricing is:

| Tier   | Annual Price* | Example Benefits                                                                                                         |
| ------ | ------------: | ------------------------------------------------------------------------------------------------------------------------ |
| Free   |            $0 | Unlimited films, diary entries, reviews, ratings and lists                                                               |
| Pro    |           $19 | No third-party ads, personalized statistics, streaming filters and notifications, additional filtering and profile tools |
| Patron |           $49 | Pro features plus additional customization, selected additional statistics and early access to some features             |

*Standard USD web pricing before applicable sales tax; pricing may vary by territory or promotion.

Letterboxd explicitly identifies membership fees as its **chief source of income**.

Paid membership is therefore not peripheral to the product. Letterboxd already uses deeper personalization — particularly personalized statistics — as part of the value proposition for paid users.

However, Letterboxd does not publicly disclose sufficient standalone information on:

* number of paid subscribers
* Free → Pro conversion
* Pro → Patron conversion
* subscriber churn
* customer lifetime value
* Letterboxd-specific revenue

These variables must therefore be treated as **unknowns**.

The financial assessment for Taste Agent uses transparent scenario assumptions rather than presenting estimated internal metrics as known company facts.

---

# 4. Strategic Opportunity

The opportunity is not simply to add an AI chatbot to Letterboxd.

The larger opportunity is to transform cultural-consumption data into a reusable **semantic taste-intelligence layer**.

## 4.1 First-Party Taste Intelligence

Letterboxd already knows:

> What has this user watched?

> What did they rate highly?

> What did they dislike?

> What have they added to their watchlist?

Taste Agent adds another analytical layer:

> **What characteristics consistently distinguish the works this user values from those they do not?**

Two films belonging to the same genre may produce very different responses from the same user.

Conversely, works from different genres may share characteristics that matter more to that person's preferences:

* character-driven storytelling
* intimate or dysfunctional relationships
* contemplative pacing
* melancholic tone
* experimental structure
* nostalgia
* emotional intensity
* specific thematic patterns

A semantic Taste Model can therefore complement existing metadata, social, and community discovery rather than replacing them.

---

## 4.2 Cross-Media Taste Intelligence

The second opportunity is more distinctive.

Cultural preferences do not necessarily exist independently by medium.

A preference for contemplative pacing, family conflict, nostalgia, ambiguity, emotional intensity, or experimentation may appear across films, literature, and potentially music.

Taste Agent therefore proposes an **optional cross-media enrichment layer**.

```text
Letterboxd
Films + Ratings
       │
       │
       ├───────────────┐
       │               │
   Goodreads        Spotify
     Books           Music
       │               │
       └───────┬───────┘
               │
               ▼
      Semantic Taste Model
               │
               ▼
      Letterboxd Discovery
```

The current POC has already tested the first cross-media extension by processing **films and Goodreads books through the same semantic taxonomy and preference-modelling pipeline**.

Spotify represents a proposed future integration rather than a completed POC component.

This distinction is important:

> **The objective is not to turn Letterboxd into a books or music platform. The objective is to use broader cultural taste to make Letterboxd better at film discovery.**

External data sources should therefore remain optional.

Taste Agent must provide meaningful value using Letterboxd data alone. Connected cultural histories enrich the model rather than becoming a prerequisite for the product.

---

# 5. Business Problem

Letterboxd possesses a large and growing corpus of explicit preference data.

It already provides discovery through social activity, ratings, lists, reviews, search, filtering, community signals, and other mechanisms.

The opportunity is to make deeper use of the relationship between:

**what a user consumes**

and

**how strongly they respond to the semantic characteristics of those works.**

The business problem can therefore be defined as:

> **How can Letterboxd create additional user and commercial value from the preference data it already collects — optionally enriched by users' broader cultural histories — without reducing taste to genres, popularity, or opaque AI recommendations?**

This creates three related challenges:

### Personalization

Can fragmented behavioural signals be transformed into a coherent representation of cultural preference?

### Discovery

Can that representation produce more relevant, contextual, and explainable film discovery?

### Monetization

Can that additional value meaningfully contribute to paid conversion, retention, or tier differentiation?

---

# 6. Proposed Solution — Taste Agent

Taste Agent consists conceptually of three layers.

## 6.1 Taste Model

The foundational layer converts cultural-consumption and rating history into semantic preference signals.

**Letterboxd provides the core data source**, while optional external histories can extend the evidence available to the model.

The current POC demonstrates this architecture across:

* **Letterboxd → films**
* **Goodreads → books**

A future version could extend the same principle to:

* **Spotify → music**

Instead of maintaining completely isolated "film taste," "book taste," and "music taste" profiles, Taste Agent searches for semantic patterns that may persist across media.

This allows the system to move from:

> "What kind of films does this user like?"

toward:

> **"What cultural characteristics does this user consistently respond to, and how can those patterns improve film discovery?"**

The model represents works across a controlled taxonomy including:

* themes
* character dynamics
* narrative structure
* pacing and energy
* tone
* style
* accessibility
* temporal/cultural characteristics
* intensity

It then evaluates the relationship between those semantic characteristics and observed preference signals.

Importantly:

> **Consumption prevalence is kept separate from preference association.**

Frequently consuming a characteristic does not automatically mean that characteristic predicts stronger preference.

---

## 6.2 Personalized Recommendation Layer

A future recommendation layer could combine the Taste Model with existing Letterboxd discovery signals to identify works likely to fit the user's preferences.

Instead of relying only on:

> "You liked this drama, therefore here are similar dramas."

the system could reason at a more granular level:

> "You consistently rate contemplative, character-driven works centered on intimate relationships highly, including across different genres."

Cross-media enrichment could extend this further.

For example:

> "The characteristics you respond to in literature also appear strongly in this film."

This recommendation layer is **not validated by the current POC** and forms part of the proposed MVP/Pilot.

---

## 6.3 Taste Agent

The final proposed interface is conversational.

Taste Agent would combine:

```text
Long-Term Taste
      +
Recent Taste
      +
Current Intent
      ↓
Contextual Discovery
```

This could support requests such as:

> "Give me something outside my normal taste, but not completely."

> "I want something melancholic but not emotionally exhausting."

> "I loved this book. What film might scratch the same itch?"

> "Why do you think I'd like this?"

Current intent would influence the immediate recommendation without automatically becoming part of the user's permanent Taste Model.

The conversational agent is therefore **one interface to the underlying taste-intelligence layer**, rather than the core AI asset itself.

---

# 7. Why Letterboxd?

Taste Agent is particularly relevant to Letterboxd for five reasons.

## 7.1 Existing Preference Data

The system does not require Letterboxd to create an entirely new behavioural dataset.

Ratings, watched films, diary entries, likes, reviews, lists, and watchlists already provide a strong foundation for preference modelling.

---

## 7.2 Scale

Letterboxd surpassed 30.7 million members in Q2 2026.

At this scale, even relatively small changes in paid conversion or retention could become economically meaningful.

The actual size of any uplift must nevertheless be established experimentally rather than assumed.

---

## 7.3 Discovery Is Core to the Product

Film discovery is closely aligned with Letterboxd's existing product purpose rather than representing an unrelated AI feature.

When Tiny acquired Letterboxd in 2023, it explicitly identified the potential for **superior discovery** as a significant opportunity for the platform.

Taste Agent therefore targets an existing strategic product area.

---

## 7.4 Paid Personalization Already Exists

Letterboxd already places personalized capabilities, particularly advanced statistics, within its paid offering.

Taste Agent extends an existing product logic:

> **Free product → deeper personalized insight and discovery as paid value.**

It therefore does not require introducing an entirely new monetization model.

---

## 7.5 Cross-Media Differentiation

Most recommendation systems operate primarily within the behavioural data and catalogue of a single media platform.

Taste Agent proposes a different approach:

> **Letterboxd remains the destination for film discovery, while users can optionally bring signals from other parts of their cultural history.**

The POC has already tested this concept by combining film and Goodreads book data within the same semantic framework.

Future integrations such as Spotify could enrich the model further without changing Letterboxd's core identity as a film platform.

This creates a potential point of differentiation from recommendation systems that operate only within one media catalogue.

---

# 8. Product Positioning

Taste Agent should **not** be positioned as:

> "ChatGPT inside Letterboxd."

That would make the conversational interface the product and provide limited strategic differentiation.

Instead:

> **Taste Agent turns cultural-consumption history into a semantic taste-intelligence layer for personalized and explainable film discovery.**

The underlying Taste Model could support multiple product surfaces.

### My Taste

An explainable representation of long-term preference patterns.

### Taste Evolution

A comparison between long-term preferences and recent consumption patterns.

### Semantic Recommendations

Recommendation ranking incorporating semantic preference alignment alongside existing Letterboxd signals.

### Cross-Media Discovery

Optional use of book, music, or other cultural histories to enrich film recommendations.

### Taste Agent

Conversational discovery combining long-term taste, recent taste, cross-media evidence, and immediate intent.

The strategic asset is therefore the **Taste Model**, not the chatbot.

---

# 9. Proposed Monetization Logic

Taste Agent is proposed as a **premium capability within Letterboxd**, rather than a separate consumer subscription.

The commercial hypothesis contains three principal mechanisms.

### 1. Free → Pro Conversion

Advanced personalized discovery could provide an additional reason for highly engaged free users to upgrade.

### 2. Paid Retention

If Taste Agent becomes a recurring discovery tool, it could increase the ongoing utility of paid membership and contribute to renewal.

### 3. Pro → Patron Upsell

Advanced capabilities such as cross-media enrichment and Taste Evolution could provide additional differentiation for the higher paid tier.

One possible future packaging hypothesis is:

| Capability                         |   Free  |   Pro   | Patron |
| ---------------------------------- | :-----: | :-----: | :----: |
| Basic Taste preview                |    ✓    |    ✓    |    ✓   |
| Full Letterboxd Taste Model        |    —    |    ✓    |    ✓   |
| Semantic film recommendations      |    —    |    ✓    |    ✓   |
| Taste Agent                        | Limited |    ✓    |    ✓   |
| Taste Evolution                    |    —    | Limited |    ✓   |
| External cultural data connections |    —    |    —    |    ✓   |
| Cross-media Taste Model            |    —    |    —    |    ✓   |

This represents a **proposed product hypothesis**, not Letterboxd's current subscription structure.

Final packaging should only be determined after Pilot evidence establishes:

* perceived user value
* repeated usage
* recommendation quality
* willingness to connect external data
* willingness to pay

---

# 10. Stakeholders

A production implementation would involve multiple stakeholder groups.

| Stakeholder             | Primary Interest                                    |
| ----------------------- | --------------------------------------------------- |
| Letterboxd Product      | User value, adoption, roadmap alignment             |
| Engineering             | Integration, scalability, reliability               |
| Data / AI               | Model quality, evaluation, monitoring               |
| Design / UX             | Explainability, interaction design, user control    |
| Growth / Commercial     | Conversion, retention, tier differentiation         |
| Legal / Privacy         | GDPR, AI Act, external data governance              |
| Customer Support        | User questions, complaints, recommendation issues   |
| Letterboxd Members      | Better discovery, transparency, privacy and control |
| External Data Providers | API/data-access requirements and terms              |
| Tiny / Ownership        | Sustainable growth and return on investment         |

Cross-media functionality introduces additional stakeholder considerations around consent, portability, third-party platform terms, and data minimization.

---

# 11. Success Criteria

Success should not be defined simply as:

> "The AI works."

The project requires validation across four layers.

## 11.1 Technical Feasibility

Can heterogeneous cultural-consumption data be reliably transformed into a structured semantic Taste Model?

**Current status: tested through the POC.**

Indicative measures include:

* metadata match rate
* semantic classification success
* schema compliance
* quality-gate rejection rate
* processing latency
* inference cost
* compatibility across media types

---

## 11.2 Recommendation Quality

Does semantic preference modelling improve discovery?

**Status: not yet validated.**

The MVP/Pilot should compare the semantic approach against an appropriate baseline.

Potential metrics:

* recommendation relevance
* novelty
* intention to watch
* save-to-watchlist rate
* already-consumed recommendation rate
* explanation usefulness

The Pilot should also test whether cross-media data produces a measurable improvement over a **Letterboxd-only Taste Model**.

This creates a useful experiment:

```text
Baseline Discovery
        vs.
Letterboxd Semantic Taste Model
        vs.
Cross-Media Semantic Taste Model
```

This allows the project to determine whether external cultural data actually adds enough value to justify the additional complexity and privacy implications.

---

## 11.3 Product Adoption

Do users find sufficient value to use the feature repeatedly?

Potential metrics:

* Taste Agent activation
* conversations per active user
* repeat usage
* recommendation interactions
* watchlist additions
* feature retention
* external account connection rate

Cross-media connections should be measured separately because their value depends on users being willing to provide additional cultural-history data.

---

## 11.4 Business Impact

Does the feature generate measurable commercial value?

Potential metrics:

* Free → paid conversion uplift
* paid renewal / retention uplift
* Pro → Patron upgrade uplift
* incremental annual subscription revenue
* cost per active Taste Agent user
* contribution margin after AI operating costs

These metrics form the basis of the scenario-based ROI model documented separately.

---

# 12. Core Hypotheses

The project deliberately separates technical, product, cross-media, and business hypotheses.

## Technical Hypothesis — Current POC

> **A structured semantic Taste Model combining explicit preferences and semantic characteristics can identify interpretable preference patterns that conventional metadata alone does not explicitly represent.**

## Cross-Media Hypothesis — Partially Tested

> **A shared semantic framework can represent cultural works from different media and identify preference patterns across them.**

The current POC demonstrates **cross-media compatibility** using films and Goodreads books.

It does **not** yet demonstrate that cross-media data improves recommendation quality.

## Product Hypothesis — MVP / Pilot

> **Semantic Taste Models can generate more relevant, explainable, and context-sensitive film recommendations than a conventional metadata-based baseline.**

## Cross-Media Product Hypothesis — Pilot

> **Adding optional cultural histories from other media produces measurably better film recommendations than using Letterboxd history alone.**

## Business Hypothesis — Pilot / Commercial Experiment

> **If users perceive sufficient additional value from semantic personalized discovery, Taste Agent can contribute to paid conversion, retention, or tier upsell at a level that exceeds its implementation and operating costs.**

Keeping these hypotheses separate prevents technical feasibility from being confused with recommendation quality or commercial validation.

---

# 13. POC Evidence

The current POC processes film and book consumption data through a shared semantic pipeline.

The final v0.3 experiment successfully analyzed:

* **107 works**
* **96 films**
* **11 books**
* **62 semantic dimensions**

This demonstrates that the architecture can process more than one media type within a shared semantic framework.

However, the dataset is heavily weighted toward films.

The book component should therefore be interpreted as evidence of **cross-media technical feasibility**, not robust evidence that book history improves film recommendations.

That question belongs in the Pilot.

Detailed POC architecture, experiments, methodology, and results are documented in:

`docs/02-poc-feasibility.md`

---

# 14. Scope

## In Scope — Current POC

* structured cultural-consumption data
* film and book records
* Letterboxd-derived film history
* Goodreads-derived book history
* metadata enrichment
* metadata quality controls
* shared semantic taxonomy
* schema-constrained LLM classification
* rating-derived preference weighting
* statistical preference association
* structured Taste Model
* cross-media technical feasibility
* low-code orchestration

## Out of Scope — Current POC

* Spotify integration
* production Letterboxd integration
* real-time multi-user processing
* production authentication
* payment integration
* final recommendation engine
* conversational frontend
* production-scale infrastructure
* A/B testing
* recommendation-quality validation
* commercial validation

These components belong to the proposed MVP, Pilot, or full-deployment stages.

---

# 15. Key Risks to the Business Case

Several assumptions could weaken the opportunity and should be tested rather than ignored.

### Incremental Recommendation Value

Letterboxd already provides strong community-driven discovery.

Taste Agent must demonstrate incremental value rather than simply reproducing existing discovery through a more expensive interface.

### Cross-Media Value

The assumption that book or music preferences improve film recommendations is plausible but not yet validated.

If cross-media data produces little measurable improvement, the additional integration and privacy complexity may not be justified.

### User Willingness to Connect Data

Cross-media functionality depends on users being comfortable importing or connecting external cultural histories.

The Letterboxd-only experience must therefore remain useful independently.

### AI Operating Cost

Personalization must generate sufficient incremental value to justify inference, storage, monitoring, and maintenance costs.

### Privacy and Trust

A system modelling cultural preferences can generate inferred personal data.

Explainability, user control, minimization, and avoidance of sensitive personal-attribute inference are therefore product requirements as well as compliance requirements.

### Third-Party Dependency

External data sources introduce dependencies on platform APIs, export formats, terms of service, and data availability.

Production design should not make Letterboxd's core Taste Model dependent on any single external provider.

These risks are assessed in greater detail in:

`docs/03-roi-risk-assessment.md`

and

`docs/04-compliance.md`

---

# 16. Business Case Summary

The case for investigating Taste Agent is based on five factors.

### 1. Scale

Letterboxd has grown beyond **30 million members**.

### 2. First-Party Data Asset

Its core product naturally generates rich explicit preference data.

### 3. Strategic Fit

Discovery is central to Letterboxd, and Tiny has explicitly identified superior discovery as an opportunity.

### 4. Monetization Fit

Membership fees are Letterboxd's chief source of income, while personalized features already form part of its paid proposition.

### 5. Cross-Media Differentiation

Taste Agent can potentially extend beyond isolated film preferences by allowing users to enrich their Taste Model with other cultural histories.

The POC has demonstrated that film and book data can already be represented within the same semantic architecture.

Together, these factors create a credible case for further testing.

However:

> **Technical feasibility does not yet justify full deployment.**

The recommended progression is:

```text
POC
Can we construct the Taste Model?
        │
        ▼
MVP
Can we generate useful recommendations?
        │
        ▼
CONTROLLED PILOT
Are recommendations better?
Does cross-media data add value?
Do users repeatedly engage?
        │
        ▼
COMMERCIAL EXPERIMENT
Does it improve conversion,
retention or upsell?
        │
        ▼
FULL DEPLOYMENT
Only if incremental value
exceeds cost and risk
```

The current project addresses the first question and establishes the foundation required to test the remaining ones.

---

# Sources

* Tiny Ltd. — Q2 2026 Results
* Tiny Ltd. — 2023 Majority Acquisition of Letterboxd
* Letterboxd — Purpose
* Letterboxd — Frequent Questions
* Letterboxd — Paid Subscriptions / Pro & Patron
* Letterboxd — Current Pro Upgrade Pricing

