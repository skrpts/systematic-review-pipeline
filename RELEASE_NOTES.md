# Release Notes

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
Initial catalogue release with full structural and content-quality validation. All scanner checks pass.
