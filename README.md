# Taste Agent

**AI Consulting Final Project — Ironhack**  
**Industry:** Digital Media & Entertainment  
**Client Case:** Letterboxd  
**Stage:** Round 1 — Proof of Concept

## Overview

**Taste Agent** explores whether cultural-consumption history can be transformed into a structured semantic **Taste Model** capable of supporting more personalized and explainable film discovery.

The proposed solution is designed as a potential premium capability for Letterboxd: using existing preference signals such as ratings and consumption history to identify semantic patterns across themes, narrative, tone, style, pacing, and other characteristics.

The current project focuses on **technical and business feasibility**. It includes sector research, use-case analysis, a low-code POC, functional evaluation, business case, ROI and risk assessment, EU AI Act and GDPR analysis, and a proposed path from POC to Pilot and deployment.

## Proof of Concept

The POC was built in **n8n** and demonstrates the following pipeline:

    Consumption Data
          ↓
    Media-Type Routing
          ↓
    TMDB / Google Books Enrichment
          ↓
    Metadata Quality Gate
          ↓
    LLM Semantic Classification
          ↓
    62-Dimensional Semantic Representation
          ↓
    Preference Weighting & Analysis
          ↓
    Structured Taste Model

The final POC analyzed **107 valid works across 62 semantic dimensions**, including **96 films and 11 books**.

A dedicated evaluation tested metadata matching, safe rejection, schema compliance, semantic plausibility, and separation between content classification and user preference signals. The evaluation also identified repeated LLM classification variance as an area to address in the MVP.

The POC validates **semantic taste-modelling feasibility**. It does not yet validate recommendation quality or commercial impact; these are proposed for the MVP/Pilot stage.

### Implementation Note

Custom processing inside the n8n POC uses **JavaScript Code nodes**.

JavaScript provided the most reliable implementation path within n8n during the time-boxed POC, allowing development to focus on validating the core hypothesis.

For the **MVP**, deterministic processing, recommendation scoring, and evaluation are planned to move to **Python**, with n8n retained for orchestration where useful.

## Repository

    taste-agent/
    │
    ├── README.md
    ├── .env.example
    │
    ├── charts/
    │   ├── 01-letterboxd-growth.png
    │   ├── 02-preference-associations.png
    │   ├── 03-prevalence-vs-preference.png
    │   └── 04-roi-scenarios.png
    │
    ├── docs/
    │   ├── 01-use-case-business-case.md
    │   ├── 02-poc-feasibility.md
    │   ├── 03-roi-risk-assessment.md
    │   ├── 04-compliance.md
    │   └── 05-strategic-deployment-plan.md
    │
    ├── evaluation/
    │   ├── eval_plan.md
    │   └── scored_cases.md
    │
    ├── feedback/
    │   └── round1_decision.md
    │
    ├── poc/
    │   ├── data/
    │   │   └── taste-test.csv
    │   ├── results/
    │   │   └── taste-model-v03-example.json
    │   ├── workflow/
    │   │   └── taste-agent-poc-v03.json
    │   └── screenshots/
    │
    ├── presentation/
    │   └── final-presentation.pdf
    │
    └── research/
        ├── opportunities_risks.md
        ├── sector_research.md
        └── use_cases.md

The `feedback/` folder will contain the Round 1 feedback and resulting KEEP / CHANGE decision once stakeholder feedback is received.

## Documentation

| Area | Contents |
|---|---|
| `research/` | Sector research, opportunities and risks, and use-case selection |
| `docs/` | Business case, POC feasibility, ROI/risk, compliance, and deployment strategy |
| `charts/` | Four stakeholder-facing charts supporting the business and POC findings |
| `evaluation/` | Evaluation methodology and scored POC test cases |
| `poc/` | n8n workflow, test data, screenshots, and example Taste Model output |
| `presentation/` | Final Round 1 presentation |
| `feedback/` | Round 1 feedback and decision record once received |

## Technology

- **n8n** — POC orchestration
- **JavaScript** — POC data processing and statistical logic
- **OpenAI** — structured semantic classification
- **TMDB** — film metadata enrichment
- **Google Books** — book metadata enrichment
- **Python** — planned MVP processing, recommendation, and evaluation layer

## Data & Reproducibility

The submitted POC uses **synthetic/mock consumption data** following the same schema required by the workflow.

API credentials and secrets are not included in the repository. Required environment variables are documented in `.env.example`.

The n8n workflow can be imported from:

`poc/workflow/taste-agent-poc-v03.json`

A sample input dataset and example Taste Model output are included under `poc/data/` and `poc/results/`.

Evaluation methodology and results are available under `evaluation/`.

## Project Status

**Round 1:** Research, business case, POC and functional evaluation  
**Next:** MVP/Pilot — recommendation quality, cross-media enrichment and user validation  
**Future:** Production — subject to technical, commercial and compliance validation

---

**Marc**  
AI Consulting Final Project · 2026
