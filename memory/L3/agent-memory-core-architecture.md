<!-- project-memory:v1 {"category":"knowledge","created_at":"2026-09-06T03:24:30.558756+00:00","id":"agent-memory-core-architecture","importance":0,"memory_level":3,"review_evidence":[],"review_status":"unreviewed","source_refs":[],"tags":["architecture","opencode","rust-core","single-owner"],"updated_at":"2026-09-06T03:24:30.558756+00:00"} -->

# Core architecture

agent-memory is agent-independent. The stable runtime chain is OpenCode hooks to the thin typed TypeScript adapter to agent-memory-bridge to Rust Core. Rust Core is the sole owner of memory admission, pending state, organization, persistence, recall, and recovery; adapters only translate host events and transport typed requests.
<!-- project-memory:end -->
