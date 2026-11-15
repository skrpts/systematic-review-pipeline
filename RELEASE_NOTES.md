# Release Notes

## v1.1.31
GH#1045 — Stage 1 of this pipeline never ran. It does now, and the stage after it was reading from nothing.

"Research Question Refinement" is the first numbered stage in this workflow's own documentation, with a
stated input, output and checkpoint — and no execution entry invoked the `research-question-refiner`
prompt, so the stage never ran. It is now backed by a new **Research Question Refinement** skill and
runs first, where the documentation places it.

**This also repairs the stage after it.** The search-strategy step reads `{{steps.previous.output}}`,
and it was the first step in the pipeline — so "previous" referred to nothing and the search strategy
was built without the refined question it is supposed to follow from. With refinement ahead of it,
that reference resolves to the refined research question.

The documentation is corrected in the same version. It told authors to invoke this prompt "via the
search-strategy-design skill" — that skill already runs the search-strategy stage, and a second entry
on one skill is refused at validation, so the instruction could not have been followed.

Also corrected: the declared contents total was 13 where the package contains 14 items, an error
introduced in v1.1.30 and never served, since that version did not publish. With this version's new
skill the total is 15.

Skills 4 → 5, total 13 (incorrect) → 15.

## v1.1.30
GH#1214 — the data-extraction stage never ran. It does now.

The stage was declared with `id: "data-extraction-template"`, pointing at a template. A template is
an asset, and only a skill or a prompt can back an executable step, so the entry matched no planner
branch and was dropped silently — no error, no warning. The stage appeared in the pipeline and
produced nothing.

It is now backed by a new **Data Extraction Design** skill, which is what the stage does: derive the
extraction fields from the review's research questions, then apply them per included study. The
extraction template remains declared as reference material.

The documentation is corrected in the same version. It told authors to invoke this prompt "via the
study-screening skill" — that skill already runs the screening stage, and a second entry on one
skill is refused at validation, so the instruction could not have been followed.

Skills 3 → 4, total 13 → 14.

## v1.1.29
GH#1044 — document the inputs this workflow's prompts REQUIRE but its Inputs table never listed. A user supplying exactly what the table asked for was running with required parameters unsatisfied — a silent wrong run, not a documentation nicety. Renamed 1 row(s) to the name the prompt actually consumes; documented 1 input(s): research_question. Every row is generated from the requiring prompt's own declared description, example and required flag — none invented. No behaviour change; documentation only.

## v1.1.28
GH#845 — republish with American English (en-US) content, completing the source-only GH#805 flip that never reached the Hub. Copy only — no functional or behaviour change.

## v1.1.27
GH#749 Phase 1b — re-pin summarise-source to v1.0.3 and supply its source via `bindings: source_text` (from Study Screening), fixing the previously-dangling {{steps.Literature Search.output}} ref (canonical `execution_step_ref_unresolved` → clean). Also declare per-step `output: {name,type}` (GH#745, deferred from the batch until this landed).

## v1.1.26
GH#645 Row 3b — migrate to K-037 dep-referenced schema. Strip 9 inline shared-content files and declare 9 hub-shared deps (UUID id + slug name + version + checksum from `gen-dep-checksums.mjs`). Closes pre-Step-3 inline-vendoring for this bundle.

## v1.1.25
Wave 2: re-signed with canonical engine signing pipeline.

## v1.1.24
Tags migrated inline into manifest (GH#586). tags.yaml retired.

## v1.1.23
Bundle re-signed with canonical engine signing pipeline (Wave 2 migration).

## v1.1.22
Signature fix — RELEASE_NOTES.md now included in integrity checksum.

## v1.1.21
Initial catalog release with full structural and content-quality validation. All scanner checks pass.
