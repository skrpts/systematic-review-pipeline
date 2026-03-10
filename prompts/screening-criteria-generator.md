---
type: prompt
id: screening-criteria-generator
title: Screening Criteria Generator
description: "Defines structured inclusion and exclusion criteria for systematic review screening"
tags: [Production]
connections:
  - target: study-screening
    type: derived_from
  - target: data-extraction-form-builder
    type: uses
metadata:
  output_format: markdown
  prompt_type: core
  avg_tokens: 2500
---

## Purpose

Generates structured, unambiguous inclusion and exclusion criteria for systematic review study selection. Well-defined criteria are essential for transparent, reproducible screening — two independent reviewers applying the same criteria should reach the same decision for the vast majority of studies.

## Prompt

You are a systematic review methodologist specialising in study selection protocols. Your task is to develop comprehensive, operationally precise inclusion and exclusion criteria for the systematic review described below. The criteria must be specific enough that two independent reviewers would make the same screening decision for at least 90% of records.

### Instructions

**1. Inclusion Criteria**
Develop criteria for each framework component:

**Population/Sample:**
- Define the eligible population precisely (age range, diagnosis, setting, geographic scope)
- Specify diagnostic criteria or classification systems accepted (e.g., DSM-5, ICD-11)
- State whether proxy populations are acceptable (e.g., animal models, simulations)

**Intervention/Phenomenon of Interest:**
- Define the eligible intervention, exposure, or phenomenon
- Specify minimum requirements (dose, duration, delivery method)
- State whether variations of the intervention are acceptable
- For qualitative reviews: define the phenomenon of interest's boundaries

**Comparator (if applicable):**
- Define acceptable comparators (active control, placebo, waitlist, no intervention, usual care)
- State whether studies without a comparator are eligible (for descriptive reviews)

**Outcome/Evaluation:**
- List the primary outcome(s) and how they must be measured
- List secondary outcomes (if applicable)
- Specify minimum follow-up duration (if applicable)
- State whether self-report, clinician-rated, or objective measures are required (or all accepted)

**Study Design/Research Type:**
- List eligible study designs (RCTs, quasi-experimental, cohort, cross-sectional, case-control, qualitative, mixed methods)
- Specify whether grey literature is included (theses, conference abstracts, reports)
- State the publication date range
- State language restrictions (if any)

**2. Exclusion Criteria**
For each inclusion criterion, state the corresponding exclusion:
- What populations are excluded and why
- What interventions or exposures are out of scope
- What study designs are excluded and why
- What publication types are excluded (editorials, commentaries, letters, protocols without results)

**3. Decision Rules for Ambiguous Cases**
Develop decision rules for scenarios that commonly cause disagreement:
- Study population partially overlaps with eligibility criteria (e.g., age range 16-25 when your criterion is 18+)
- Intervention is a variation not explicitly listed
- Outcome is measured using a non-standard instrument
- Study reports multiple populations, only some of which are eligible
- Conference abstract with insufficient detail to determine eligibility

For each scenario, specify the rule: include, exclude, or escalate to a third reviewer.

**4. Screening Protocol**
Specify the screening procedure:
- Deduplication method
- Title/abstract screening process (independent dual screening recommended)
- Full-text screening process
- Conflict resolution procedure
- Documentation requirements (reason for exclusion at full-text stage)

### Inputs

- **Research question components:** {{question_components}}
- **Review type:** {{review_type}}
- **Team size:** {{team_size}} (number of reviewers available)
- **Known grey areas:** {{known_ambiguities}} (any specific scenarios you anticipate being difficult to screen)

### Output Format

Present the criteria in a structured table with columns: Criterion | Inclusion | Exclusion | Decision Rule for Ambiguous Cases. Follow with the screening protocol as a numbered procedure. Include the decision tree for ambiguous cases as a flowchart in text form.
