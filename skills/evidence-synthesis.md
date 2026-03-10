---
type: skill
id: evidence-synthesis
title: Evidence Synthesis
description: "Synthesises extracted evidence from systematic review into a coherent narrative review"
tags: [Production, Tested]
connections:
  - target: claude-service
    type: runs_on
  - target: prisma-guidelines-reference
    type: references
metadata:
  estimated_duration: "40-60 minutes"
  avg_tokens: 3500
---

## Capability

Synthesises evidence extracted from studies included in a systematic review into a coherent, balanced narrative. This skill covers narrative synthesis (for heterogeneous study sets) and can guide the reporting structure for meta-analyses. It organises findings by theme, outcome, population subgroup, or study characteristic, and identifies patterns of agreement, contradiction, and evidence gaps across the included studies.

## When to Use

- Writing the results and synthesis sections of a systematic review
- Organising extracted data into a coherent narrative structure
- Identifying patterns, contradictions, and gaps across included studies
- Producing summary of findings tables for systematic reviews
- Writing the discussion section of a systematic review, contextualising findings within the broader literature

## Inputs

- Completed data extraction forms for all included studies
- Quality/risk of bias assessment results
- Research questions guiding the synthesis
- Synthesis approach: narrative synthesis, framework synthesis, thematic synthesis, or meta-analysis reporting
- Any subgroup analyses or sensitivity analyses to report

## Process

1. **Organise the evidence** — group included studies by the most appropriate organising principle:
   - By research question (if the review addresses multiple questions)
   - By outcome (if synthesising effects across multiple outcomes)
   - By population subgroup (if relevant differences exist between populations)
   - By intervention type or exposure category
   - By theme (for qualitative evidence synthesis)

2. **Describe the evidence base** — for each grouping, summarise:
   - Number of studies contributing
   - Study designs represented
   - Total sample size across studies
   - Geographic and temporal range
   - Overall quality/risk of bias profile

3. **Synthesise findings** — for each grouping:
   - Summarise the direction and magnitude of findings across studies
   - Identify consistent findings (most studies agree)
   - Identify contradictory findings (studies disagree) and explore possible explanations: methodological differences, population differences, intervention variations, measurement differences
   - Note where evidence is absent or insufficient to draw conclusions
   - Weight findings by study quality — give more emphasis to well-conducted studies

4. **Assess certainty of evidence** — apply GRADE (Grading of Recommendations Assessment, Development and Evaluation) or equivalent framework to rate the overall certainty of evidence for each key finding: high, moderate, low, or very low

5. **Produce summary tables** — create:
   - Characteristics of included studies table
   - Summary of findings table (key outcomes, effect estimates, certainty of evidence)
   - Risk of bias summary (across studies)

6. **Identify implications** — derive:
   - Implications for practice (what should practitioners do based on this evidence?)
   - Implications for research (what questions remain unanswered? What study designs are needed?)
   - Implications for policy (if applicable)

## Outputs

- Complete narrative synthesis organised by theme, outcome, or subgroup
- Characteristics of included studies table
- Summary of findings table
- Risk of bias summary
- GRADE evidence certainty ratings (if applicable)
- Implications for practice, research, and policy
- Identified evidence gaps and contradictions

## Constraints

- Never overstate the strength of evidence — if the evidence is weak or contradictory, say so explicitly
- Do not count studies as a measure of evidence strength ("five studies found X" is not the same as "strong evidence for X" if all five studies had high risk of bias)
- Distinguish between absence of evidence and evidence of absence — "no studies found an effect" is different from "studies found no effect"
- Weight study findings by quality — a single well-conducted RCT may provide stronger evidence than ten poorly conducted observational studies
- Report all findings, not just those that support a particular narrative — publication bias at the review level undermines the purpose of systematic reviewing
- Follow PRISMA 2020 reporting guidelines for the structure and content of the synthesis
