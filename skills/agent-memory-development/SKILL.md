---
name: agent-memory-development
description: >-
  Develop and debug agent-memory through the Rust Core semantic owner, thin
  typed OpenCode adapters, mapped gates, and real host replay. L1 anchors:
  Important boundaries [boundary,payload-control,soft-admission,typed-errors]
  -> L1/agent-memory-boundaries.md; Core architecture
  [architecture,opencode,rust-core,single-owner] ->
  L1/agent-memory-core-architecture.md; Development flow
  [development-flow,function-map,verification-map,worktree] ->
  L1/agent-memory-development-flow.md. For detailed memory, query L2
  then L3 by category/tag and open the generated relative detail_path; never
  infer or hardcode an entry path.
---

# agent-memory development

Use this Skill for product code, architecture changes, and debugging in this
repository. AppSDK Guidance is advisory; applicable quality and evidence gates
remain mandatory.

## Orient

1. Read `AGENTS.md`, the affected design, current `MEMORY.md`/`note.md`, and
   relevant prior evidence.
2. Locate the behavior in `.appsdk/maps/function-map.json` and its gates in
   `.appsdk/maps/verification-map.json`.
3. Bind the unique owner and allowed paths:
   - Rust business semantics and persistence: `src/**`;
   - OpenCode event translation and transport: `plugin/**`;
   - host-specific compatibility only: `compaction/**`.
4. For debugging, record the reproduction, current hypothesis, evidence, and
   first divergence in task-local notes before changing code.

## Implement

- Start from latest `origin/main` in a clean owner worktree under
  `playground/`.
- Add a focused positive/negative regression before changing critical
  admission, transaction, persistence, recovery, or adapter semantics.
- Fix the unique owner. Keep TypeScript adapters thin and preserve typed errors.
- Do not restore DSH as an active dependency, duplicate Core rules in an
  adapter, or place control state in memory payloads or metadata.
- Update function or verification maps only when their actual truth changes.

## Verify

Run the narrowest affected test first, then:

```text
cargo fmt -- --check
cargo clippy --all-targets -- -D warnings
cargo test --all-targets
cargo build --release --bin agent-memory-bridge
npx --yes tsx --test plugin/test/opencode.test.ts plugin/test/opencode-bridge.test.ts plugin/test/opencode-organized-index.test.ts
appsdk verify
appsdk compile
```

For host-facing behavior, also load the exact built adapter and bridge through a
real OpenCode entrypoint. Loader health alone is not memory behavior evidence;
exercise the affected observe, organize, persistence/reopen, recall, or
compaction path.

## Review and close

- Review the exact validated diff against owner uniqueness, payload/control
  separation, fail-closed persistence, and evidence identity.
- After authorization, integrate against latest `origin/main`, rerun affected
  gates on the integration tree, push, verify remote main, then remove the
  merged clean worktree.
- At task end, review `AGENTS.md`, this Skill, `MEMORY.md`, and task notes.
  Add durable memory only for verified non-duplicate project knowledge.
