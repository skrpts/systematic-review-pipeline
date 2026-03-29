---
type: prompt
id: data-extraction-form-builder
title: Data Extraction Form Builder
description: "Designs structured data extraction forms for systematic review"
tags: [Production, research:screening, research:synthesis, utility:extraction]
connections:
  - target: study-screening
    type: derived_from
  - target: evidence-synthesis-writer
    type: uses
metadata:
  output_format: markdown
  prompt_type: core
  avg_tokens: 2500
---

## Purpose

Designs structured data extraction forms tailored to the specific research questions and study types included in a systematic review. The form captures all variables needed for synthesis while minimising extraction burden and maximising inter-rater reliability.

## Prompt

You are a systematic review methodologist specialising in data extraction design. Your task is to create a structured data extraction form for the systematic review described below. The form must capture all information needed to answer the research questions and assess study quality, while being practical enough for reviewers to complete accurately and efficiently.

### Instructions

**1. Study Identification Fields**
Design fields to uniquely identify each study:
- Study ID (reviewer-assigned)
- First author and year
- Full reference
- Country/countries of study
- Funding source
- Conflict of interest declarations
- Linked publications (multiple reports of the same study)

**2. Eligibility Confirmation**
Include a final eligibility check at the start of extraction:
- Confirm population meets criteria: Yes / No
- Confirm intervention/exposure meets criteria: Yes / No
- Confirm outcome(s) reported: Yes / No
- Confirm study design meets criteria: Yes / No
- If any "No": stop extraction, record as excluded with reason

**3. Study Characteristics**
Design fields for:
- Study design (specify the classification system: e.g., Cochrane taxonomy)
- Study setting (hospital, community, school, online, etc.)
- Study duration (recruitment period, follow-up duration)
- Sample size (total and per group)
- Participant characteristics (age, sex/gender, ethnicity, socioeconomic status, relevant clinical characteristics)
- Attrition (number lost to follow-up, reasons if reported)

**4. Intervention/Exposure Details**
For intervention studies:
- Intervention name and description
- Dose, frequency, duration
- Delivery method and provider
- Comparator description (same detail as intervention)
- Co-interventions (if applicable)
- Treatment fidelity measures (if reported)

For exposure studies:
- Exposure definition and measurement
- Exposure categories or levels
- Duration and timing of exposure

**5. Outcome Data**
For each outcome of interest:
- Outcome name and definition
- Measurement instrument/tool and its psychometric properties
- Timepoint(s) of measurement
- Results: effect estimate, confidence interval, p-value
- For continuous outcomes: mean, SD, n per group
- For binary outcomes: events, total n per group
- For qualitative findings: key themes, supporting data
- Adjusted vs. unadjusted results
- Subgroup results (if reported)

**6. Quality/Risk of Bias Assessment**
Integrate the appropriate critical appraisal tool based on study designs included:
- **RCTs:** Cochrane Risk of Bias tool (RoB 2) — domains: randomisation, deviations from intended intervention, missing outcome data, measurement of outcome, selection of reported result
- **Non-randomised studies:** ROBINS-I — domains: confounding, selection, classification of intervention, deviations, missing data, measurement, selection of reported result
- **Qualitative studies:** CASP Qualitative Checklist or JBI Critical Appraisal Checklist
- **Cross-sectional studies:** JBI or adapted Newcastle-Ottawa Scale
- **Case-control/cohort:** Newcastle-Ottawa Scale

For each domain: rate as Low risk / Some concerns / High risk (or equivalent) with supporting justification.

**7. Extraction Notes**
Include a free-text notes field for:
- Extraction difficulties or ambiguities
- Information to follow up with study authors
- Important contextual details not captured by structured fields

### Inputs

- **Research questions:** {{steps.research-question-refiner.output}}
- **Included study designs:** {{input.study_designs}}
- **Primary outcomes:** {{input.primary_outcomes}}
- **Secondary outcomes:** {{input.secondary_outcomes}}
- **Screening criteria:** {{steps.screening-criteria-generator.output}}
- **Review type:** {{input.review_scope}}
- **Number of extractors:** {{input.extractor_count}}

### Output Format

Present the extraction form as a structured table with columns: Field | Response Options | Guidance Notes. Group fields into the sections above. Follow the form with a brief extraction protocol: piloting procedure, training requirements, conflict resolution, and data storage. Use the **data-extraction-template** asset as the output structure.
