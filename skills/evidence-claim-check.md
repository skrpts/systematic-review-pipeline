---
type: skill
id: evidence-claim-check
title: Evidence-Claim Check
description: "Checks whether claims are supported by cited sources, flags unsupported assertions and overstatements"
tags: [Production, Quality, Academic]
connections:
  - target: llm-service
    type: runs_on
---

## Capability

Reviews a document's claims against its cited sources. Identifies assertions that lack supporting evidence, claims that overstate what the evidence shows, and gaps where important claims have no citation at all.

This is NOT open-web fact-checking. It works with the sources the document already cites — checking whether the claims made actually follow from those sources.

## When to Use

- After drafting academic essays, research papers, or literature reviews
- On reports that make evidence-based recommendations
- Before submitting any document where the strength of claims matters
- On user research reports to verify findings are grounded in data

## What It Checks

1. **Unsupported claims** — assertions stated as fact with no citation or evidence
2. **Overstatements** — claims that go beyond what the cited source actually demonstrates (e.g. "proves" when the study "suggests")
3. **Citation gaps** — important arguments or conclusions that lack any source reference
4. **Misattribution** — claims attributed to a source that doesn't support them
5. **Hedging gaps** — definitive language where the evidence warrants qualified language ("may", "suggests", "in some cases")

## What It Does NOT Do

- Verify sources against the open web (it trusts the sources the document cites)
- Check citation formatting (use `apa-7th-edition` or similar style references)
- Assess source quality or credibility
- Generate new citations

## Inputs

The document to check, including its citations or reference list.

## Outputs

A claim audit listing each flagged claim, the issue type (unsupported, overstated, gap, misattributed), the relevant text, and a suggested fix.
