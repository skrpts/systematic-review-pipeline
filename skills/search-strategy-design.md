---
type: skill
id: search-strategy-design
title: Search Strategy Design
description: "Designs thorough, reproducible search strategies for systematic literature reviews"
tags: [Production, Tested, planning:research, research:synthesis]
connections:
  - target: llm-service
    type: runs_on
  - target: prisma-guidelines-reference
    type: references
metadata:
  estimated_duration: "30-45 minutes"
  avg_tokens: 3000
---

## Capability

Designs thorough, reproducible search strategies for systematic literature reviews. This skill constructs database-specific search strings using Boolean operators, controlled vocabulary (MeSH, Emtree, PsycINFO thesaurus terms), free-text synonyms, truncation, and proximity operators. It also refines research questions using structured frameworks (PICO, SPIDER, PEO, PCC) to ensure the search is focused, answerable, and appropriately scoped.

## When to Use

- Developing a search strategy for a new systematic review
- Translating a search strategy from one database to another
- Refining a research question to make it suitable for systematic searching
- Expanding a search strategy that is not capturing known relevant studies
- Documenting a search strategy for protocol registration (PROSPERO, OSF)

## Inputs

- Research question (draft or refined)
- Target databases: PubMed/MEDLINE, Scopus, Web of Science, PsycINFO, CINAHL, Cochrane Library, Embase, ERIC, or others
- Conceptual framework: PICO, SPIDER, PEO, PCC (or let the skill recommend the most appropriate one)
- Known relevant studies (for sensitivity checking)
- Date range and language restrictions (if any)
- Any existing search terms or strategies to build upon

## Process

1. **Decompose the research question** — break it into structured components using the selected framework:
   - PICO: Population, Intervention, Comparator, Outcome
   - SPIDER: Sample, Phenomenon of Interest, Design, Evaluation, Research type
   - PEO: Population, Exposure, Outcome
   - PCC: Population, Concept, Context (for scoping reviews)

2. **Generate search terms** — for each component, compile:
   - Controlled vocabulary terms (MeSH headings for PubMed, Emtree for Embase, thesaurus terms for PsycINFO)
   - Free-text synonyms, related terms, and spelling variants
   - Abbreviations and acronyms commonly used in the field
   - Truncation wildcards to capture word variants (e.g., randomi* for randomise, randomize, randomised, randomization)

3. **Construct the search string** — combine terms within each concept using OR (to capture synonyms) and between concepts using AND (to ensure all components are present). Apply proximity operators where appropriate (e.g., ADJ3 in Ovid, NEAR/3 in Scopus).

4. **Translate for each database** — adapt the search string for each target database's syntax:
   - PubMed: [MeSH Terms], field tags [tiab], Boolean operators in capitals
   - Scopus: TITLE-ABS-KEY(), W/n proximity, AND/OR/NOT
   - Web of Science: TS=(), NEAR/n proximity
   - Ovid (MEDLINE, PsycINFO, Embase): exp/ for exploded MeSH, .mp. for multi-purpose, adj for proximity

5. **Sensitivity check** — test whether the strategy retrieves all known relevant studies. If any are missing, identify which search terms would capture them and revise accordingly.

6. **Document the strategy** — record the complete search strategy in a format suitable for publication and protocol registration: database, date searched, search string, results count, and any limits applied.

## Outputs

- Structured research question components
- Complete search strategy for each target database
- Sensitivity check results (known studies found/missed)
- Search documentation table for PRISMA reporting
- Recommended supplementary search methods (citation chaining, grey literature, hand-searching key journals)

## Constraints

- Search strategies must be fully reproducible — record every decision and the exact strings used
- Do not rely on a single database — systematic reviews require searching at least 2 databases, preferably 4+
- Include both controlled vocabulary and free-text terms to maximise recall
- Do not apply language or date filters without explicit justification in the protocol
- Favour sensitivity (capturing all relevant studies) over specificity (excluding irrelevant ones) — it is better to screen more results than to miss relevant studies
- Document any deviations from the registered protocol
