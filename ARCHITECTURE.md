# ARCHITECTURE (all items PROPOSAL unless tagged)

Constraint driving everything (SOURCE-DERIVED, secondary; re-verify): the Kaggle submission is declarative YAML/MD/TXT plus skill scripts, run by a fixed harness, offline, 32,768-token context, one model, 9 fixed tools. Therefore "one core Python agent" cannot ship to Kaggle. Decision OD-1 pending.

## 1. System architecture
```
                 POLICY CORE  (declarative, versioned, shared)
   prompts/  skills/  protocols/(recovery, verification)  sampling  experience-cards
        |                                   |
   Track K: compile_submission.py      Track P: Python runtime (personal agent)
   -> agent.yaml tree -> submission.zip     -> CLI + notebook + local tools
        |                                   |
   Kaggle harness (fixed loop, 9 tools)     Model API (Ollama / OpenAI-compatible / vLLM)
```
## 2. Agent architecture
Kaggle: root LlmAgent (policy prompt) + optional read-only localizer sub-agent used as AgentTool (keeps search noise out of main context). No Sequential/Loop pipeline in first candidate (small-change principle). Personal: ~150-250 line loop in the style of mini-swe-agent: query model -> parse action -> execute in Environment -> observe -> limits.
## 3. Model/runtime
Kaggle: gemma-4-31b-it-qat-w4a16-ct only, sampling from generate_content_config. Personal: model.py interface `complete(messages, tools) -> Message`; backends configurable.
## 4-5. Tools / Environment: see TOOL_ARCHITECTURE.md.
## 6-7. Memory / Recovery: see MEMORY_AND_RECOVERY.md.
## 8. Planning
Task contract -> repo scan (cheap: tree, test layout) -> task analysis (issue -> suspected symptom, files, failing test) -> skill selection. Plan is 3-6 lines in a compact STATE block, not a long document.
## 9. Coding/execution loop
inspect (search before read) -> reproduce -> hypothesize -> minimal patch -> diff -> targeted test -> broader test -> final diff review -> submit. Kaggle: encoded in prompt + skills; harness executes the loop.
## 10. Verification loop
Executable evidence only: tests run before/after; diff must touch non-test code; no edits to test files unless the task requires. (Guidance on tests from third-party; rule text UNKNOWN.)
## 11. Benchmark loop
See EXPERIMENT_PLAN.md and BENCHMARK_RESEARCH.md; layers L0-L4.
## 12. Kaggle runtime
Harness-owned: containers, tool execution, compaction, retries, time budget. We control only files in the ZIP.
## 13. Personal runtime
We own everything: loop, tools, confinement, memory, ledger, CLI, notebook.
## 14. Shared
Prompts, skill folders (SKILL.md/scripts/resources), recovery+verification protocols, card schema, evidence-record schema, task fixtures for local eval.
## 15. Must remain separate
Python loop and all Python tools (personal only); SQLite memory service; network-dependent components (Hindsight, git-ai binary); secrets/config; anything not in the allowed extension list.
## Anti-overengineering rule
Any layer needs a measured benefit in EXPERIMENT_PLAN before it enters the submission.
