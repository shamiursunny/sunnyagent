# S17 - Kaggle/kaggle-benchmarks (library)

**SOURCE:** Kaggle/kaggle-benchmarks (library)

**URL:** https://github.com/Kaggle/kaggle-benchmarks

**ACCESS STATUS:** ACCESSIBLE (cloned; default branch 'ci', HEAD cd465b2; main README URL 404). README, quick_start.md, local_development.md, skills/ read in part.

**REPOSITORY/PATH:** Kaggle/kaggle-benchmarks: src/kaggle_benchmarks/{tasks,assertions,chats,tools,envs,...}, skills/{kaggle-benchmarks,kaggle-standardized-agent-exam}

**LICENSE:** Apache-2.0

**LICENSE STATUS:** Apache-2.0 - LICENSE read (FACT)

**RELEVANT FILES:** README.md, quick_start.md, local_development.md, skills/*/SKILL.md

**RELEVANT CODE:** @kbench.task decorator, llm.prompt, assertions, python tool, docker/local envs (names seen; not read)

**RELEVANT ARCHITECTURE:** Task/Run/Chat/Actor/Assertion concepts; runs inside Kaggle notebooks via kaggle.com/benchmarks/tasks/new

**RELEVANT IDEAS:** Task+assertion evaluation of model outputs; run records

**DIRECT REUSE CANDIDATE:** NO (not needed)

**REFERENCE-ONLY MATERIAL:** YES

**COMPATIBILITY CONCERNS:** local_development.md states local development is for the Kaggle internal team only and needs a Kaggle Model Proxy key (FACT). Library evaluates Kaggle-hosted models; no evidence it can run a submission.zip agent (INFERENCE).

**SECURITY CONCERNS:** The skills/kaggle-standardized-agent-exam SKILL instructs registering an agent and calling Kaggle HTTP APIs and warns about key handling. NOT executed by me.

**KAGGLE RELEVANCE:** LOW-UNKNOWN: separate product from the competition evaluator.

