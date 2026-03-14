---
type: skill
id: study-screening
title: Study Screening
description: "Defines screening criteria and supports systematic study selection for literature reviews"
tags: [Production, Tested]
connections:
  - target: llm-service
    type: runs_on
  - target: prisma-guidelines-reference
    type: references
metadata:
  estimated_duration: "20-40 minutes"
  avg_tokens: 2500
---

## Capability

Develops structured inclusion and exclusion criteria for systematic review screening, designs data extraction forms, and supports the study selection process. This skill covers the entire screening pipeline from deduplication through title/abstract screening and full-text screening, following PRISMA 2020 guidelines for transparent reporting of study selection.

## When to Use

- Defining inclusion and exclusion criteria for a systematic review
- Designing a screening protocol for a review team
- Creating structured data extraction forms for included studies
- Resolving ambiguous screening decisions
- Documenting screening decisions for PRISMA reporting

## Inputs

- Refined research question with structured components (from search-strategy-design)
- Search results exported from databases (titles, abstracts, metadata)
- Draft inclusion/exclusion criteria (or request to generate them from the research question)
- Study types to include (RCTs, cohort studies, qualitative studies, etc.)
- For data extraction: research questions, outcomes of interest, study characteristics to capture

## Process

### Screening Criteria Development
1. **Derive criteria from the research question** — map each PICO/SPIDER component to specific inclusion criteria
2. **Specify exclusion criteria** — define what falls outside the review's scope with clear, unambiguous boundaries
3. **Operationalise each criterion** — provide sufficient detail that two independent reviewers would make the same decision:
   - Population: specific age range, diagnostic criteria, setting
   - Intervention/exposure: type, dose, duration, delivery method
   - Comparator: active control, placebo, no intervention, usual care
   - Outcome: specific measure, timepoint, method of assessment
   - Study design: specify which designs are eligible and which are excluded
4. **Create a decision tree** — develop a flowchart for common ambiguous cases
5. **Pilot the criteria** — test on a sample of 20-50 records to check inter-rater agreement

### Data Extraction Form Design
1. **Identify extraction variables** — study identifiers, methods, participants, interventions, outcomes, results, quality indicators
2. **Define response options** — use closed-ended fields where possible (dropdown menus, checkboxes) to reduce extraction variability
3. **Include guidance notes** — for each field, specify how to handle missing data, multiple reports of the same study, and ambiguous reporting
4. **Design the form structure** — group fields logically (study details, participant characteristics, intervention details, outcomes, results, quality assessment)
5. **Include a quality/risk of bias assessment** — integrate the appropriate critical appraisal tool (RoB 2, ROBINS-I, JBI, CASP, Newcastle-Ottawa)

## Outputs

- Structured inclusion and exclusion criteria with operational definitions
- Screening decision tree for ambiguous cases
- Pilot screening results with inter-rater agreement statistics
- Data extraction form with field definitions and guidance notes
- Quality/risk of bias assessment framework

## Constraints

- Inclusion/exclusion criteria must be specified before screening begins — do not modify them based on what you find (unless documented as a protocol amendment)
- When in doubt during screening, include the study for full-text review — err on the side of inclusion at the title/abstract stage
- All screening decisions must be documented with reasons for exclusion at the full-text stage
- Two independent reviewers should screen at least title/abstract records, with a third to resolve disagreements
- Data extraction should be piloted on 3-5 studies before extracting from all included studies
- Report screening results using the PRISMA flow diagram format
