---
type: workflow
id: systematic-review-pipeline
title: Systematic Review Pipeline
description: "End-to-end systematic literature review following PRISMA 2020 methodology"
tags: [Production, Tested]
connections:
  - target: search-strategy-design
    type: uses
  - target: study-screening
    type: uses
  - target: evidence-synthesis
    type: uses
  - target: research-question-refiner
    type: uses
  - target: search-string-builder
    type: uses
  - target: screening-criteria-generator
    type: uses
  - target: data-extraction-form-builder
    type: uses
  - target: evidence-synthesis-writer
    type: uses
  - target: llm-service
    type: runs_on
  - target: prisma-guidelines-reference
    type: references
  - target: systematic-review-protocol-guide
    type: references
  - target: prisma-flow-template
    type: uses
  - target: data-extraction-template
    type: uses
metadata:
  estimated_duration: "120-240 minutes"
  trigger: manual
---

## Overview

This workflow orchestrates a complete systematic literature review following the PRISMA 2020 reporting guidelines. It covers the full review lifecycle from research question refinement through search strategy development, study screening, data extraction, and evidence synthesis. The pipeline is designed for single reviewers or small teams and emphasises transparency and reproducibility at every stage.

Systematic reviews are the gold standard of evidence synthesis. Unlike narrative reviews, they follow a pre-specified, reproducible methodology that minimises bias in study identification, selection, and synthesis. This pipeline ensures you follow that methodology rigorously.

## Prerequisites

Before starting this pipeline:
1. Assemble the review team (minimum recommended: 2 reviewers for screening, 1 for arbitration)
2. Register the review protocol on PROSPERO (for health-related reviews) or OSF (for other disciplines)
3. Determine the review scope: systematic review only, or systematic review with meta-analysis?
4. Identify the databases to search (minimum 2, recommended 4+)

## Pipeline Stages

### Stage 1: Research Question Refinement

**Input:** Draft research question, field of study, review scope

Invoke the **search-strategy-design** skill via the **research-question-refiner** prompt. Refine the research question using the PICO framework (Population, Intervention, Comparator, Outcome) for quantitative reviews or the SPIDER framework (Sample, Phenomenon of Interest, Design, Evaluation, Research type) for qualitative/mixed-methods reviews.

**Output:** Refined research question with structured components, review objectives, and scope definition.

**Checkpoint:** The refined research question must be answerable through a systematic search of the literature. If it is too broad (would return thousands of results), narrow the scope. If too narrow (fewer than 10 studies likely to exist), broaden it. Check PROSPERO and Cochrane Library for existing reviews on the same topic — if a recent, high-quality review already exists, consider whether yours adds value.

### Stage 2: Search Strategy Development

**Input:** Refined research question from Stage 1, target databases, search date range

Invoke the **search-strategy-design** skill via the **search-string-builder** prompt. Construct database-specific search strings using Boolean operators, controlled vocabulary, and free-text terms. Translate the core strategy for each target database's syntax.

**Output:** Complete search strategy documentation: search strings for each database, search date, any filters applied, and the rationale for each search decision.

**Checkpoint:** Have the search strategy peer-reviewed by a research librarian or information specialist if possible. Run pilot searches to check that the strategy retrieves known relevant studies (sensitivity check). If key known studies are missing from results, revise the search terms. Document the final strategy before running the definitive search — do not modify it retroactively.

### Stage 3: Screening

**Input:** Search results (exported from databases), inclusion/exclusion criteria

Invoke the **study-screening** skill via the **screening-criteria-generator** prompt to formalise the inclusion and exclusion criteria. Then apply these criteria in a two-stage screening process:

**Stage 3a: Title and abstract screening**
- Remove duplicates across databases
- Screen titles and abstracts against inclusion/exclusion criteria
- When in doubt, include for full-text review
- Record decisions and reasons for exclusion

**Stage 3b: Full-text screening**
- Obtain full texts of all studies passing title/abstract screening
- Screen against inclusion/exclusion criteria
- Record reasons for exclusion of each study at this stage
- Resolve disagreements between reviewers through discussion or a third reviewer

**Output:** Final set of included studies, PRISMA flow diagram numbers (identification, screening, eligibility, inclusion), and excluded studies with reasons.

**Checkpoint:** Update the **prisma-flow-template** with the actual numbers from your screening. Calculate inter-rater reliability (Cohen's kappa) for screening decisions if using multiple reviewers. If the included study count is very low (fewer than 5), consider whether the search strategy was too restrictive or whether a systematic review is the appropriate review type.

### Stage 4: Data Extraction

**Input:** Full texts of included studies, research questions, data extraction form

Invoke the **study-screening** skill via the **data-extraction-form-builder** prompt. Design a structured data extraction form tailored to the review's research questions. Then extract data from each included study.

**Output:** Completed data extraction forms for all included studies, populated **data-extraction-template**.

**Checkpoint:** Pilot the extraction form on 3-5 studies before extracting from all. Revise the form if fields are ambiguous or consistently difficult to complete. Have a second reviewer independently extract data from at least 20% of studies to check extraction reliability. Resolve discrepancies through discussion.

### Stage 5: Evidence Synthesis

**Input:** Completed data extraction forms, research questions, quality assessment results

Invoke the **evidence-synthesis** skill via the **evidence-synthesis-writer** prompt. Synthesise the extracted evidence into a coherent narrative organised by research question, outcome, or theme.

**Output:** Complete evidence synthesis narrative, summary tables, and recommendations for practice/research.

**Checkpoint:** Ensure the synthesis accurately represents the body of evidence — do not overstate the strength of findings. Distinguish between what the evidence shows and what the evidence does not address. If the included studies are heterogeneous (different populations, interventions, outcomes), use a narrative synthesis approach. If sufficiently homogeneous, consider meta-analysis (not covered by this pipeline — use a dedicated statistical tool).

## Error Handling

- If the research question cannot be structured using PICO or SPIDER, it may not be suitable for a systematic review — consider a scoping review or narrative review instead
- If pilot searches return over 5,000 results, add additional search filters or narrow the research question before proceeding
- If fewer than 3 studies meet the inclusion criteria after full-text screening, consider whether to proceed (a systematic review with very few studies is still valuable if the methodology is rigorous) or to broaden the criteria
- If data extraction reveals that included studies report outcomes in incompatible formats, use a narrative synthesis rather than attempting to force quantitative comparison
- If quality assessment reveals that all included studies have critical risk of bias, state this limitation prominently and qualify all conclusions accordingly
- If the review protocol was registered, document any deviations from the protocol with justification

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.draft_research_question}}` | Yes | Draft research question | `Paste the relevant brief, notes, source material, or dataset here.` |
| `{{input.field_of_study}}` | Yes | field of study | `Paste the relevant brief, notes, source material, or dataset here.` |
| `{{input.review_scope}}` | Yes | review scope | `Paste the relevant brief, notes, source material, or dataset here.` |
| `{{input.target_databases}}` | No | target databases | `Paste the latest metrics, exported data, or summary notes relevant to the workflow.` |

## Outputs

| Name | Description |
|------|-------------|
| Refined research question | Refined research question with structured components, review objectives, and scope definition |
| Complete search strategy documentation: search strings for each database, search date, any filters applied, and the rationale for each search decision | Complete search strategy documentation: search strings for each database, search date, any filters applied, and the rationale for each search decision |
| Final set of included studies, PRISMA flow diagram numbers , and excluded studies | Final set of included studies, PRISMA flow diagram numbers , and excluded studies with reasons |
| Completed data extraction forms for all included studies, populated data-extraction-template | Completed data extraction forms for all included studies, populated data-extraction-template |
| Complete evidence synthesis narrative, summary tables, and recommendations for practice/research | Complete evidence synthesis narrative, summary tables, and recommendations for practice/research |

## Setup

Before running this workflow:

1. No external services required — paste your content directly and provide any supporting context as inputs or source nodes.
2. Review the included documents, assets, or source nodes and customise them to match your team, brand, or domain conventions where needed.
3. No specific AI provider or API key is required beyond your configured skrptiq LLM provider.

## Provider Notes

- The longer synthesis stages benefit from a model with strong reasoning and a generous context window.
- Extraction, classification, and formatting steps generally run well on smaller or faster models.
- Because there are no vendor-specific integrations here, provider choice is mostly a trade-off between speed, quality, and cost.

## Example Input

To test this workflow immediately after import:

```
Draft Research Question: "Paste the relevant brief, notes, source material, or dataset here."
Field Of Study: "Paste the relevant brief, notes, source material, or dataset here."
Review Scope: "Paste the relevant brief, notes, source material, or dataset here."
Target Databases: "Paste the latest metrics, exported data, or summary notes relevant to the workflow."
```

