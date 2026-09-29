# CONTINUITY_AND_AUTOSAVE (PROPOSAL; automatic GitHub push is NOT configured or tested)

## Files updated after every completed stage
PROJECT_STATE.md (human), PROJECT_STATE.json (machine truth), TASK_LOG.md (append-only), DECISION_LOG.md (append-only).
## Protocol
1. Before a stage: set stage `in_progress` with `resume_note` and `pre_commit_sha`; commit.
2. Do the work idempotently.
3. On success: stage `complete` + evidence paths + artifact SHA256; append TASK_LOG; add decisions; update `last_verified`, `last_verified_commit`.
4. Commit; push; verify remote HEAD equals local HEAD (`git ls-remote`). If push impossible: write `STATE_SAVE_FAILED` in TASK_LOG locally and STOP and report; never claim saved.
5. Failures: append TASK_LOG entry with exact error, stage stays in_progress/blocked.
## Resume / stage detection
Another AI reads JSON: first stage not `complete` is current; if `in_progress`, compare git HEAD with `pre_commit_sha`, inspect diff since, redo unfinished steps only. Artifacts referenced by path + SHA256; frozen baselines flagged `frozen:true` and protected by a git tag. Consistency check: MD and JSON must agree on current_stage, else report.
## Optional later tooling (not built)
`tools/render_state.py` rendering MD from JSON, and a pre-commit check that validates JSON schema and that TASK_LOG only grew.
