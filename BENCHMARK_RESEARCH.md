# BENCHMARK_RESEARCH

Question: can available benchmark infrastructure validate a V5.5 agent before Kaggle submission?

## Findings
1. **kaggle.com/benchmarks/** - page body unreadable (metadata only: "Build, run, and share benchmarks for evaluating AI models and agents"). Applicability to the competition UNKNOWN.
2. **Kaggle/kaggle-benchmarks (Apache-2.0)** - FACT (read): Python library; tasks are `@kbench.task` functions receiving an LLM object; assertions; runs recorded; on Kaggle it is used in notebooks via kaggle.com/benchmarks/tasks/new with the library preinstalled; `local_development.md` says local development is for the Kaggle internal team only and requires a Kaggle Model Proxy key with Kaggle-authorised models. It evaluates Kaggle-hosted models on task definitions.
   - INFERENCE: it cannot execute a `submission.zip` agent tree or the competition's Docker two-container flow; no source read says otherwise.
   - INFERENCE: it cannot run the competition model `gemma-4-31b-it-qat-w4a16-ct` unless Kaggle exposes it through the proxy (UNKNOWN).
3. **Competition harness (swegemma / adk-submission / adk-eval-core)** - SOURCE-DERIVED (secondary mirror): official local evaluation path, with wheels shipped in the gated dataset; two-container lifecycle (agent container, then verification container). One third-party entrant reports validation, compilation and an end-to-end run with a scripted model using these wheels, never with the real model (UNVERIFIED claim). Another entrant reports a local re-implementation ("swelite") (UNVERIFIED).
4. **SWE-bench-style pipelines / mini-swe-agent SWE-bench and ProgramBench runners** - read; different agent interface (bash); can test the personal agent, not the YAML submission.
5. **Standardized Agent Exam skill** in kaggle-benchmarks/skills - a separate HTTP exam for agents (16 questions, 30 min per its SKILL.md). Not the competition. NOT executed.

## Conclusions (each with status)
| Claim | Status |
|---|---|
| Official swegemma wheels are the best pre-submission validator | PROPOSAL (needs dataset; INFERENCE from mirror) |
| Static validation (structure, extensions, size, YAML compile) is possible without a GPU | SOURCE-DERIVED (third-party report) - UNVERIFIED by us |
| Real-model trajectories need GPU; 4x L4 in official runs | SOURCE-DERIVED |
| kaggle-benchmarks predicts competition score | NO EVIDENCE - do not claim |
| Any local score correlates with Kaggle score | NO EVIDENCE - must be measured (Experiment plan: compare local vs official on the same policy) |

## Recommended validation layers (PROPOSAL)
L0 static checks (own script + official validator). L1 compile with official compiler. L2 scripted-model run (checks plumbing only). L3 real-model run on a small fixed task subset (GPU permitting). L4 official Kaggle run (only source of truth). Record for each: what it can and cannot show.
