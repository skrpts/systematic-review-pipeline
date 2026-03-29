---
type: asset
id: data-extraction-template
title: Data Extraction Template
description: "Structured template for extracting data from studies included in a systematic review"
tags: [Production, Customer-Facing, Research, Academic]
connections:
  - target: data-extraction-form-builder
    type: references
metadata:
  asset_type: template
  format: markdown
---

## Data Extraction Template

Use this template to extract data from each study included in your systematic review. Complete one form per study. If a study has multiple publications (e.g., a protocol paper and a results paper), extract from all reports but record as a single study.

---

# Data Extraction Form

**Reviewer:** [Name]
**Date of extraction:** [YYYY-MM-DD]
**Verified by:** [Second reviewer name, if applicable]

---

## 1. Study Identification

| Field | Entry |
|-------|-------|
| Study ID | [Assign a unique ID, e.g., Smith2024] |
| First author | |
| Year | |
| Full reference | |
| Country | |
| Funding source | |
| Conflicts of interest | [Declared / None declared / Not reported] |
| Linked publications | [List DOIs of related reports of this study] |

## 2. Eligibility Confirmation

| Criterion | Met? | Notes |
|-----------|------|-------|
| Population meets criteria | Yes / No | |
| Intervention/exposure meets criteria | Yes / No | |
| Outcome(s) reported | Yes / No | |
| Study design meets criteria | Yes / No | |

**Decision:** Include / Exclude
**If excluded, reason:** [Record reason and stop extraction]

## 3. Study Design and Setting

| Field | Entry |
|-------|-------|
| Study design | [RCT / Cluster RCT / Quasi-experimental / Cohort (prospective/retrospective) / Cross-sectional / Case-control / Qualitative / Mixed methods / Other: specify] |
| Setting | [Hospital / Community / Primary care / School / University / Online / Workplace / Other: specify] |
| Recruitment period | [Start date - End date] |
| Follow-up duration | |
| Number of study sites | [Single / Multi-site (n = )] |

## 4. Participants

| Field | Entry |
|-------|-------|
| Total sample size | |
| Sample size per group | [Intervention: n = ; Control: n = ] |
| Age (mean, SD or range) | |
| Sex/gender (% female) | |
| Ethnicity | [As reported] |
| Inclusion criteria (study-level) | |
| Exclusion criteria (study-level) | |
| Attrition (n lost to follow-up) | [Intervention: n = ; Control: n = ] |
| Reasons for attrition | |

## 5. Intervention / Exposure

| Field | Entry |
|-------|-------|
| Intervention name | |
| Description | |
| Dose / intensity | |
| Frequency | |
| Duration | |
| Delivery method | [Individual / Group / Online / Blended / Other] |
| Delivered by | [Clinician / Researcher / Teacher / Peer / Self-directed / Other] |
| Comparator name | |
| Comparator description | |
| Co-interventions | [None / Describe] |
| Treatment fidelity assessed | [Yes (method: ) / No / Not reported] |

## 6. Outcomes

### Primary Outcome 1: [Name]

| Field | Entry |
|-------|-------|
| Outcome definition | |
| Measurement instrument | |
| Instrument validity/reliability | [Reported / Not reported] |
| Timepoint(s) | |
| Intervention group: mean (SD), n | |
| Control group: mean (SD), n | |
| Effect estimate | [e.g., MD = , SMD = , OR = , RR = ] |
| 95% confidence interval | |
| p-value | |
| Adjusted/unadjusted | [Adjusted for: / Unadjusted] |

### Primary Outcome 2: [Name]

[Repeat the table above]

### Secondary Outcome 1: [Name]

[Repeat the table above]

## 7. Subgroup Results (if reported)

| Subgroup | Outcome | Effect Estimate | 95% CI | p-value | n |
|----------|---------|----------------|--------|---------|---|
| | | | | | |

## 8. Risk of Bias Assessment

### For RCTs (Cochrane RoB 2)

| Domain | Judgement | Support for Judgement |
|--------|----------|---------------------|
| Randomisation process | Low / Some concerns / High | |
| Deviations from intended interventions | Low / Some concerns / High | |
| Missing outcome data | Low / Some concerns / High | |
| Measurement of the outcome | Low / Some concerns / High | |
| Selection of the reported result | Low / Some concerns / High | |
| **Overall** | **Low / Some concerns / High** | |

### For Non-Randomised Studies (ROBINS-I)

| Domain | Judgement | Support for Judgement |
|--------|----------|---------------------|
| Confounding | Low / Moderate / Serious / Critical / NI | |
| Selection of participants | Low / Moderate / Serious / Critical / NI | |
| Classification of interventions | Low / Moderate / Serious / Critical / NI | |
| Deviations from intended interventions | Low / Moderate / Serious / Critical / NI | |
| Missing data | Low / Moderate / Serious / Critical / NI | |
| Measurement of outcomes | Low / Moderate / Serious / Critical / NI | |
| Selection of reported result | Low / Moderate / Serious / Critical / NI | |
| **Overall** | **Low / Moderate / Serious / Critical / NI** | |

### For Qualitative Studies (CASP)

| Question | Yes / Can't tell / No | Comments |
|----------|----------------------|----------|
| Clear statement of aims? | | |
| Qualitative methodology appropriate? | | |
| Research design appropriate? | | |
| Recruitment strategy appropriate? | | |
| Data collection appropriate? | | |
| Researcher-participant relationship considered? | | |
| Ethical issues considered? | | |
| Data analysis rigorous? | | |
| Clear statement of findings? | | |
| Value of the research? | | |

## 9. Extraction Notes

[Record any difficulties, ambiguities, or additional contextual information. Note any data that needs to be obtained from study authors.]

---

**Formatting notes:**
- Complete one form per included study
- If data are reported in multiple publications, extract from all and note the source for each data point
- For missing data: record "NR" (not reported) — do not leave cells blank
- For continuous outcomes: extract means and SDs where possible. If medians and IQRs are reported, record these and note the need for conversion
- For binary outcomes: extract events and totals per group
- Save completed forms in a consistent location and format for easy retrieval during synthesis
