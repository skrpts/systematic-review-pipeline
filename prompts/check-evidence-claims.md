---
type: prompt
id: check-evidence-claims
title: "Check Evidence and Claims"
description: "Verifies claims are supported by cited sources, flags unsupported assertions"
tags: [Production, Quality, Academic]
connections:
  - target: evidence-claim-check
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Drives the evidence claim check skill.

## Prompt

You are a research reviewer. Examine the document below and check whether each claim is adequately supported by its cited sources.

### Document to Review

{{steps.previous.output}}

### Evidence Rigour: {{step.context.evidence_rigour}}

Adjust your review based on the rigour level:
- **Light**: Check only major claims (thesis statements, key conclusions). Flag only clearly unsupported assertions.
- **Standard** (default): Check all significant claims. Flag unsupported and overstated claims.
- **Thorough**: Check all claims including supporting points. Assess source quality and recency. Flag weak evidence chains.
- **Exhaustive**: Maximum rigour. Check every factual claim. Assess primary vs secondary sources, sample sizes, methodology quality, potential conflicts of interest, and replicability of cited studies.

### Instructions

For each significant claim in the document:

1. **Identify the claim** — what assertion is being made?
2. **Check the citation** — is a source cited? Does the cited source actually support this claim?
3. **Assess the strength** — does the claim overstate what the evidence shows?

### Flag These Issues

- **Unsupported claims** — assertions with no citation at all
- **Overstated claims** — language stronger than the evidence warrants (e.g. "proves" when evidence only "suggests")
- **Missing context** — claims that omit important caveats from the source
- **Citation gaps** — sections where important points lack any reference

### Output Format

| Claim | Source Cited | Assessment | Issue |
|-------|-------------|------------|-------|
| [the claim] | [source or "none"] | Supported / Overstated / Unsupported | [explanation] |

End with a summary: X claims checked, Y fully supported, Z need attention.

## Formatting Rules

- Use British English throughout
- Be specific and actionable — no vague recommendations
- Structure output clearly with headings, tables, or lists as appropriate
