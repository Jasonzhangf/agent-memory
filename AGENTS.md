# agent-memory Project Contract

## Project Truth

- `agent-memory` is an independent Git repository. Its remote is
  `https://github.com/Jasonzhangf/agent-memory.git`.
- The product is an agent-independent memory core plus a thin OpenCode adapter.
  Rust owns memory semantics, persistence, organization, recall, and recovery;
  TypeScript transports typed requests and projects OpenCode events.
- The runtime boundary is
  `OpenCode hooks -> TypeScript adapter -> agent-memory-bridge -> Rust Core`.
- `agent-tui` is a sibling repository and outside this project's ownership.
  Historical DSH loader material is compatibility evidence, not an active host
  contract.

## Semantic Invariants

- Missing or malformed model memory never rejects or changes the parent agent
  output. Recognizable valid entries are admitted; invalid parts produce typed
  diagnostics.
- Pending entries become long-term knowledge only through the single
  organization transaction owner. Raw knowledge, evidence, deltas, and epochs
  are append-only.
- Entry IDs, source references, generations, watermarks, epochs, hashes,
  transactions, retries, diagnostics, and provider state are host-owned
  control truth and never enter memory business payloads or metadata.
- OpenCode and future agent adapters may translate host events, but may not
  duplicate Rust validation, organization, persistence, or recovery semantics.

## Ownership

- `src/**`, `tests/**`: Rust Core and JSONL bridge.
- `plugin/**`: OpenCode adapter and adapter contract tests.
- `compaction/**`: retained host-specific compaction compatibility surface; it
  must not become a second memory transaction owner.
- `docs/**`, `README.md`, `MAIN.md`, `MEMORY.md`: project architecture,
  boundaries, current handoff, and verified project memory.
- `.appsdk/maps/**`: project owner/function/gate bindings. AppSDK-installed
  contracts, rules, templates, and Skills remain SDK-owned.

## Architecture Truth

- Read `.appsdk/maps/function-map.json` and
  `.appsdk/maps/verification-map.json` before changing runtime behavior.
- Update project maps in the same change when an owner, entry symbol, path, or
  required regression gate changes.
- Fix the first divergence at its unique owner. Do not add fallback paths,
  silent coercion, duplicate schedulers, or control fields in payloads.

## Development and Delivery

- Work from a clean owner worktree created from latest `origin/main`; main is
  integration-only. Worktrees live under `playground/<task>-<run-id>/`.
- Follow `skills/agent-memory-development/SKILL.md` for feature/debug work.
- Use `scripts/setup/verify-local.sh` for the focused local stack and
  `scripts/setup/verify-ci.sh` for the full local release stack. The repository
  does not require a remote AppSDK CI job.
- Report source tests, build artifact, host installation, runtime replay,
  review, merge, remote receipt, and cleanup as separate evidence.
- Remove the merged clean owner worktree after remote mainline verification.
