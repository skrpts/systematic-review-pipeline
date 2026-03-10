---
type: asset
id: prisma-flow-template
title: PRISMA Flow Diagram Template
description: "PRISMA 2020 flow diagram template for documenting study selection in systematic reviews"
tags: [Production, Customer-Facing]
connections:
  - target: study-screening
    type: references
metadata:
  asset_type: template
  format: markdown
---

## PRISMA 2020 Flow Diagram Template

Replace all [n] placeholders with actual numbers from your review. Delete any sections that do not apply (e.g., remove "Registers" if no registers were searched).

---

```
PRISMA 2020 Flow Diagram

IDENTIFICATION
==============

Records identified from:
    Databases (n = [n])
        [Database 1] (n = [n])
        [Database 2] (n = [n])
        [Database 3] (n = [n])
        [Database 4] (n = [n])
    Registers (n = [n])
        [Register 1] (n = [n])

Records identified from:
    Citation searching (n = [n])
    Websites (n = [n])
    Organisations (n = [n])
    Other (n = [n])

              |
              v

Records removed before screening:
    Duplicate records (n = [n])
    Records marked as ineligible
    by automation tools (n = [n])
    Records removed for other
    reasons (n = [n])

              |
              v

SCREENING
=========

Records screened
(n = [n])
              |
              +--> Records excluded (n = [n])
              |
              v

Reports sought for retrieval
(n = [n])
              |
              +--> Reports not retrieved (n = [n])
              |
              v

Reports assessed for eligibility
(n = [n])
              |
              +--> Reports excluded (n = [n])
              |    Reason 1 (n = [n])
              |    Reason 2 (n = [n])
              |    Reason 3 (n = [n])
              |    Reason 4 (n = [n])
              |    Reason 5 (n = [n])
              |
              v

INCLUDED
========

Studies included in review
(n = [n])

Reports of included studies
(n = [n])
```

---

## Completion Instructions

### Identification Section
- Record the total number of records identified from each database separately
- Include records from all sources: databases, registers, citation searching, grey literature
- If using automation tools for deduplication, record the number removed

### Screening Section
- **Records screened:** total number of unique records after deduplication
- **Records excluded:** number excluded at title/abstract stage (no reasons required at this stage)
- **Reports sought for retrieval:** number passing title/abstract screening
- **Reports not retrieved:** full texts that could not be obtained (with reasons if possible)
- **Reports assessed for eligibility:** number of full texts screened
- **Reports excluded with reasons:** provide the reason for exclusion for every full text excluded. Use categories:
  - Wrong population
  - Wrong intervention/exposure
  - Wrong comparator
  - Wrong outcome
  - Wrong study design
  - Duplicate report
  - Full text not available
  - Other (specify)

### Included Section
- **Studies included:** number of unique studies (one study may have multiple reports)
- **Reports of included studies:** total number of reports/publications (may exceed study count if multiple papers report the same study)

### Additional Notes
- If you searched for additional reports of included studies (e.g., protocol papers, companion papers), document this separately
- If studies were excluded after data extraction (e.g., upon closer inspection), document when and why
- Save this completed diagram for inclusion in your manuscript as a figure
- Some journals require the diagram as an editable figure file — use the PRISMA flow diagram generator at prisma-statement.org for a downloadable version
