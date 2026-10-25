# Release Notes

## v1.0.3
GH#1045/GH#1100 — declare the revision material this prompt consumes, so a consumer can supply it. It read `{{steps.previous.output}}` for its structured notes, which made it dependent on whatever happened to precede it, and `{{steps.Flashcard Creator.output}}` for flashcards — a named step reference that no consumer of this prompt has a node for. `source` is now a declared `context_param`, registered as a C7 source slot since 1.0.3.

The flashcards reference is REMOVED rather than declared. A referenced `{{step.context.X}}` must be bound by every invoking consumer — the engine refuses a referenced slot nothing binds — so an optional enrichment input cannot be expressed as a context_param at all: declaring it would make flashcards mandatory for every consumer, including the four that have no flashcard stage. No consumer invokes this prompt today, so nothing loses a capability it was using.

## v1.0.2
GH#657 Framing B — republish wave. Bundle now ships `dependencies: []` in its signed manifest (injected by `publish-skrpt.mjs` for `--shared` publishes), so the App's dep-referenced install pipeline (post-PR #47) accepts it on standalone update via Hub Update-all. No content changes.

## v1.0.1
GH#645 Row 3a — republish with `manifest.id` aligned to Hub catalog UUID. Pre-K-037 v1.0.0 bundle carried a local `manifest.id` that drifted from the catalog UUID. Row 5 (`0d9c9dbe`) reconciled the source file but not the signed bundle; v1.0.1 ships the corrected `manifest.id` so the batch-of-81 consumer migrations (GH#645 Row 3b) can pin this version and pass engine STEP 4d. No content changes.

## v1.0.0
Initial catalog release as independent shared object (GH#625 Step 2; canonical pick + rename surface per audit).
