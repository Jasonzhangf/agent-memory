<!-- project-memory:v1 {"category":"knowledge","created_at":"2026-09-06T03:25:00.429758+00:00","id":"agent-memory-boundaries","importance":0,"memory_level":3,"review_evidence":[],"review_status":"unreviewed","source_refs":[],"tags":["boundary","payload-control","soft-admission","typed-errors"],"updated_at":"2026-09-06T03:25:00.429758+00:00"} -->

# Important boundaries

Memory business payload contains only model-visible memory semantics. Entry IDs, source references, generations, watermarks, epochs, hashes, transactions, retries, diagnostics, provider state, and other host control truth stay in typed control resources or errors. Missing or malformed model memory never rejects or changes the parent agent output; valid recognizable entries are admitted and invalid parts remain typed diagnostics.
<!-- project-memory:end -->
