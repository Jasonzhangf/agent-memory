# Standalone repository migration

The user authorized an independent repository at
https://github.com/Jasonzhangf/agent-memory.git and removal of Git ownership
from the aggregate parent directory.

Source is extracted from the existing `codex/agent-platform-final2-20260904`
integration branch, commit `deeb5df`. Its last memory change is `907b3d7`;
the extracted root tree is `5db4bf1905f76eca70297844a5d911b5126d4038`.
Filtering retains the applicable subproject history. The original repository
and all its branches are retained separately, including the older DSH branch.

The OpenCode implementation, tests, dependencies, and AppSDK contracts are
unchanged. Hooks and current root/worktree instructions now use this repository
root. Fresh-checkout verification now builds the release bridge before the
plugin tests; previously those tests failed with ENOENT without a prior build.

Validation: Rust formatting, clippy with warnings denied, all-target Rust tests,
release bridge build, and OpenCode plugin/bridge tests pass. This migration does
not claim a new live host deployment.

`appsdk verify .` reports `DECLARED_RECORD_CONTRACT_MISMATCH` in both the
unmodified extracted baseline and the candidate. This pre-existing governance
failure remains open; migration does not rewrite its records or claim AppSDK
admission, freeze, or promotion. Existing design/status documents retain their
previous status except for repository-location instructions.
