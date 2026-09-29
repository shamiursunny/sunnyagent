# PROJECT_STATE (research-export edition)

> WARNING: This is NOT the authoritative `gemma4-kaggle/PROJECT_STATE.md` from `coding-agent-platform`.
> The export agent could not read that repository (HTTP 404 unauthenticated; likely private - UNVERIFIED).
> Everything about V0.5 history, prior stages and Kaggle results is therefore UNKNOWN here.
> When the real file is available it WINS on any conflict about project history; this file wins only on what was done in the research/export phase.

Tags: FACT (observed by the export agent) | SOURCE-DERIVED | INFERENCE | PROPOSAL | UNVERIFIED

TIMESTAMP: 2026-09-29
PROJECT: Gemma 4 Developer Agent competition - V5.5 research
CURRENT_BASELINE: V0.5 (branch `gemma4-kaggle-v0.5-dual-space`; artifact `gemma4-kaggle/artifacts/v0.5-dual-space/submission.zip`, SHA256 `cb854c2906de49624e646ca4b9826c9379eb1e6f77551d3459006a25343fb68f`) - values quoted from the user's message; NOT VERIFIED (artifact unreadable to export agent). FROZEN: do not modify.
ACTIVE_VERSION: V5.5 (research only; NO implementation exists)
ACTIVE_BRANCH: none created (no write access to implementation repo)
CURRENT_STAGE: ST02 - export package produced locally (not uploaded)
FIRST_INCOMPLETE_STAGE: ST00 - capture authoritative V0.5 state (BLOCKED: repo unreadable to research agent)
KAGGLE_STATUS: NOT RUN by export agent. Nothing submitted. Prior V0.5 Kaggle result: UNKNOWN.
BENCHMARK_STATUS: Nothing executed. See BENCHMARK_RESEARCH.md.
CURRENT_ARTIFACT: none for V5.5. (V0.5 ZIP above is unverified.)

## Stage table
| ID | Stage | Status | Evidence |
|---|---|---|---|
| ST00 | Capture authoritative V0.5 state (PROJECT_STATE.md, TASK_LOG.md, V0.5 build report, git history) | BLOCKED | TASK_LOG T-002 |
| ST01 | Public-source audit (22 records) | COMPLETE-WITH-GAPS (YouTube, kaggle.com/benchmarks body, official competition page body, official HARNESS_README unread) | sources/, SOURCE_INDEX.md |
| ST02 | Export package | COMPLETE locally; NOT uploaded | EXPORT_VERIFICATION.md |
| ST03 | Acquire official spec (accept rules, download dataset: HARNESS_README, sample_submission, tasks.jsonl, wheels) | INCOMPLETE - needs user | KAGGLE_SPECIFICATION.md |
| ST04 | User decisions OD-1..OD-5 (DECISION_LOG.md) | INCOMPLETE | DECISION_LOG.md |
| ST05 | Policy core + deterministic Kaggle compiler + static validation | NOT STARTED | V5.5_IMPLEMENTATION_PLAN.md |
| ST06 | Local harness validation (official wheels, scripted model, then real model if GPU) | NOT STARTED | |
| ST07 | Personal agent (loop, confined env, ledger, CLI, notebook) | NOT STARTED | |
| ST08 | Memory (static cards for Kaggle; SQLite retain/recall/reflect for personal) | NOT STARTED | |
| ST09 | Local eval + benchmark-integrity audit | NOT STARTED | |
| ST10 | Package, BUILD_REPORT, EXPERIMENT_REPORT | NOT STARTED | |
| ST11 | Kaggle submission (user-triggered only) | NOT STARTED | |

DO_NOT_RESTART: ST01, ST02 (unless sources change). Never overwrite V0.5.
KNOWN_FAILURES: see RISKS_AND_UNKNOWNS.md
NEXT_ACTION: give the next AI the real state files (ST00) and resolve OD-1..OD-5 (ST04), then ST03.

## How a future AI interprets: "Read gemma4-kaggle/PROJECT_STATE.md from my GitHub repository and continue the Gemma 4 competition project from the first incomplete stage."
1. Read `gemma4-kaggle/PROJECT_STATE.md` in the implementation repo (`coding-agent-platform`). If it is unreadable, STOP and report the exact access error; do not reconstruct from this export.
2. Read `PROJECT_STATE.json` (machine truth), `TASK_LOG.md` (append-only), `DECISION_LOG.md`. If MD and JSON disagree, report the disagreement; prefer the one with the later `last_verified` AND a matching git commit; never silently merge.
3. Run `git log -3`, `git status`, `git branch -a`; compare HEAD with `last_verified_commit` in JSON. If HEAD is newer, list the commits and check whether they completed a stage before continuing.
4. Verify the latest artifact: recompute SHA256 and compare with the recorded value. Mismatch => mark BLOCKED, do not continue.
5. Find the first stage whose status is not COMPLETE (order by stage ID). If it is IN_PROGRESS, read its `resume_note` and redo only the unfinished steps (stages must be idempotent).
6. Never restart COMPLETE stages; never modify frozen baselines (`frozen: true` in JSON `artifacts`).
7. On finishing a stage follow architecture/CONTINUITY_AND_AUTOSAVE.md (update 4 state files, commit, verify remote).
