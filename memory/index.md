# Memory Index

Index stores short titles, tags, and detail paths. Open the linked Markdown detail for content.

## Raw sources

- [Plan](plan.jsonl)
- [Path](path.jsonl)
- [Knowledge](knowledge.jsonl)
- [Lesson](lesson.jsonl)

## Level 1 — reviewed critical

### Important boundaries
- tags: `boundary`, `payload-control`, `soft-admission`, `typed-errors`
- details: [L1/agent-memory-boundaries.md](L1/agent-memory-boundaries.md)

### Core architecture
- tags: `architecture`, `opencode`, `rust-core`, `single-owner`
- details: [L1/agent-memory-core-architecture.md](L1/agent-memory-core-architecture.md)

### Development flow
- tags: `development-flow`, `function-map`, `verification-map`, `worktree`
- details: [L1/agent-memory-development-flow.md](L1/agent-memory-development-flow.md)

## Level 2 — reviewed reusable

_Empty._

## Level 3 — new or unreviewed

_Empty._

## Skill description candidates

Base budget: 8 lines. Copy the compact lines into the project Skill `description` after manual architecture deduplication. Fill level 1 first; use level 2, then level 3, only for remaining slots.

- L1: Important boundaries (knowledge) [boundary,payload-control,soft-admission,typed-errors] -> L1/agent-memory-boundaries.md
- L1: Core architecture (knowledge) [architecture,opencode,rust-core,single-owner] -> L1/agent-memory-core-architecture.md
- L1: Development flow (path) [development-flow,function-map,verification-map,worktree] -> L1/agent-memory-development-flow.md

