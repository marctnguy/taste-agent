# Taste Agent

**AI Consulting Final Project — Ironhack**  
**Industry:** Digital Media & Entertainment  
**Client Case:** Letterboxd  
**Stage:** Proof of Concept

## Overview

**Taste Agent** explores whether cultural-consumption history can be transformed into a structured semantic **Taste Model** capable of supporting more personalized and explainable discovery.

The proposed solution is designed as a potential premium capability for Letterboxd: using existing preference signals such as ratings and consumption history to identify semantic patterns across themes, narrative, tone, style, pacing, and other characteristics.

The current project focuses on **technical and business feasibility**. It includes a low-code POC, business case, ROI and risk assessment, EU AI Act and GDPR analysis, and a proposed path from POC to Pilot and deployment.

## Proof of Concept

The POC was built in **n8n** and demonstrates the following pipeline:

```text
Consumption Data
      ↓
Metadata Enrichment
      ↓
Quality Gate
      ↓
LLM Semantic Classification
      ↓
62-Dimensional Taxonomy
      ↓
Preference Analysis
      ↓
Structured Taste Model
```

The final POC analyzed **107 works across 62 semantic dimensions** and demonstrated that structured semantic characteristics can be associated with rating-derived preferences.

The POC validates **semantic taste-modelling feasibility**. It does not yet validate recommendation quality or commercial impact; these are proposed for the MVP/Pilot stage.

### Implementation Note

Custom processing inside the n8n POC uses **JavaScript Code nodes**.

Python was initially intended for these components, but JavaScript provided the most reliable implementation path within n8n during the time-boxed POC. Development time was therefore prioritized toward validating the core hypothesis rather than migrating functioning logic.

For the **MVP**, deterministic processing, recommendation scoring, and evaluation are planned to move to **Python**, with n8n retained for orchestration where useful.

## Repository

```text
taste-agent/
│
├── README.md
│
├── docs/
│   ├── 01-use-case-business-case.md
│   ├── 02-poc-feasibility.md
│   ├── 03-roi-risk-assessment.md
│   ├── 04-compliance.md
│   └── 05-strategic-deployment-plan.md
│
├── poc/
│   ├── workflow/
│   │   └── taste-agent-poc-v03.json
│   ├── data/
│   │   └── taste-test.csv
│   ├── results/
│   │   └── taste-model-v03-example.json
│   └── screenshots/
│
└── presentation/
    └── final-presentation.pdf
```

## Documentation

| Document | Purpose |
|---|---|
| [`01-use-case-business-case.md`](docs/01-use-case-business-case.md) | Business problem, client context, proposed solution, stakeholders and success criteria |
| [`02-poc-feasibility.md`](docs/02-poc-feasibility.md) | POC architecture, experiments, methodology, results and limitations |
| [`03-roi-risk-assessment.md`](docs/03-roi-risk-assessment.md) | Implementation costs, 12/36-month ROI scenarios and risk assessment |
| [`04-compliance.md`](docs/04-compliance.md) | EU AI Act and GDPR assessment |
| [`05-deployment-commercialisation.md`](docs/05-strategic-deployment-plan.md) | POC → Pilot → Full Deployment roadmap and commercialisation strategy |

## Technology

- **n8n** — POC orchestration
- **JavaScript** — POC data processing and statistical logic
- **OpenAI** — structured semantic classification
- **TMDB** — film metadata enrichment
- **Google Books** — book metadata enrichment
- **Python** — planned MVP processing, recommendation and evaluation layer

## Data & Reproducibility

The submitted POC uses **synthetic/mock consumption data** following the same schema required by the workflow.

API credentials and secrets are not included in the repository.

The n8n workflow can be imported from:

`poc/workflow/taste-agent-poc-v03.json`

A sample input dataset and example Taste Model output are included under `poc/data/` and `poc/results/`.

## Project Status

**Current:** POC — semantic taste-modelling feasibility  
**Next:** MVP/Pilot — recommendation quality and user validation  
**Future:** Production — subject to technical, commercial and compliance validation

---

**Marc**  
AI Consulting Final Project · 2026
