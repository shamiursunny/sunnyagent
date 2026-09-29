# EXPERIMENT_PLAN

Purpose: learn how the Kaggle scoring behaves while building a useful personal agent. V0.5 = control (frozen); V5.5 = candidate. All targets below are PROPOSALS; no expected score is claimed.

## Baseline (V0.5)
Characteristics UNKNOWN until V0.5_BASELINE.md checklist is completed (ST00). Record: ZIP hash, agent.yaml, sampling, skills, prior Kaggle result (if any).
## Hypotheses
- H1: Concise policy prompt + explicit verify/recover protocol increases pass rate vs V0.5 (if V0.5 lacks them).
- H2: A read-only localizer sub-agent reduces main-context growth and context-overflow failures.
- H3: Static experience cards improve localization without hurting context (test with/without).
- H4: Fewer, shorter skills beat many long skills under 32k context.
Each hypothesis needs one measurable prediction stated BEFORE running.
## Metrics
Primary: official Kaggle score (only ground truth). Local proxies (correlation UNKNOWN): pass rate on a fixed local task subset, patch-applies rate, submitted-patch rate, context-overflow rate, steps/task, tool calls/task, repeated-action rate, wall time, tokens if available, test-file-edit rate.
## Method
Change one factor per candidate (V5.5-a, -b ...). Same tasks, seeds/sampling recorded. Ladder L0-L4 from BENCHMARK_RESEARCH.md. Record for every run: artifact SHA256, config hash, task ids, trajectories path, outcome, failure class.
## Ablations
prompt-only vs +skills vs +localizer vs +cards vs +LoRA (LoRA only if training data and time allow; UNVERIFIED feasibility).
## Failure analysis
Classify each failure: agent (localization/patch/verification/limits/format) vs benchmark/environment issue using the BenchGuard-style checks: task spec, environment, expected behavior, reference behavior, evaluator, trace. Record POSSIBLE BENCHMARK / EVALUATOR ISSUE when inconsistent. Do not auto-blame either side.
## Learning about scoring
Because official submissions may be limited (UNKNOWN) and runs long (12h budget), prioritise L0-L3 locally; use official submissions for hypothesis tests with the largest expected information. Check limits in rules first.
## Rollback / preservation
Frozen: V0.5 branch/artifact. Every candidate gets its own dir `artifacts/v5.5/<candidate>/` with ZIP, SHA256, BUILD_REPORT, config. Never overwrite; tag git. Roll back = resubmit V0.5 or previous candidate by hash.
## Result recording
experiments/result_record_schema.json; results appended to EXPERIMENT_REPORT (never fabricated; NOT_VERIFIED stays NOT_VERIFIED).
