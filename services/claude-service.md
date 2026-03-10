---
type: service
id: claude-service
title: Claude Service
description: "Anthropic Claude integration for systematic review search strategy, screening support, and evidence synthesis"
tags: [Production, Tested]
connections:
  - target: anthropic-claude
    type: runs_on
metadata:
  provider: anthropic
  model: claude-sonnet
---

## Service Description

This skrpt uses Anthropic Claude as the primary reasoning engine for systematic review tasks. Claude assists with search strategy development, screening criteria formulation, data extraction form design, and narrative evidence synthesis.

## How This Skrpt Uses Claude

### Search Strategy Design
Claude constructs comprehensive search strategies using Boolean operators, Medical Subject Headings (MeSH) and other controlled vocabulary terms, proximity operators, and truncation wildcards. It translates search strategies across different database syntaxes (PubMed, Scopus, Web of Science, PsycINFO, CINAHL, Cochrane Library).

### Screening Support
Claude generates structured inclusion and exclusion criteria based on the research question and PICO/SPIDER framework. It can assist with title and abstract screening by identifying potentially relevant studies, though human screening decisions are always required for methodological rigour.

### Data Extraction
Claude designs structured data extraction forms tailored to the review's research questions and the types of studies included. It specifies which variables to extract, how to handle missing data, and how to code study characteristics.

### Evidence Synthesis
Claude synthesises extracted evidence into a narrative review, organising findings by theme, outcome, or study characteristic. It identifies patterns, contradictions, and gaps across the included studies.

## Configuration

- **Model:** Claude Sonnet or higher for precise Boolean search construction
- **Context window:** Extended context essential for processing multiple study summaries simultaneously
- **Temperature:** 0.2 for search strategy construction (precision-critical), 0.3 for screening criteria, 0.4 for evidence synthesis
- **Output format:** Structured markdown with tables, search strings, and narrative text
