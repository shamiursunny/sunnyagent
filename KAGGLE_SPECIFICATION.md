# KAGGLE_SPECIFICATION - Gemma 4 Developer Agent Competition

Labels used here (no item is upgraded):
- **OFFICIAL-EXCERPT**: text of kaggle.com/competitions/gemma-4-developer-agent as returned by a search engine. The page body itself could not be fetched (JS-only). Not equivalent to reading the rules.
- **SOURCE-DERIVED (secondary)**: from `docs/HARNESS_README.md`, `Overview.md`, `Data.md` in a third-party repo (8kta/kaggle-gemma4), single commit dated 2026-09-28. Fidelity to the organizers' files UNVERIFIED. Organizer HARNESS_README says it is inside the gated dataset.
- **THIRD-PARTY CLAIM**, **INFERENCE**, **PROPOSAL**, **UNKNOWN**.
No item below is a "VERIFIED OFFICIAL FACT" in the strict sense; the strongest status is OFFICIAL-EXCERPT.

## 1. Task and scoring
- OFFICIAL-EXCERPT: agent has 12 hours to submit patches for all tasks, including sandbox setup, excluding patch validation; per-task limits may be set in `eval_config.yaml`.
- SOURCE-DERIVED: per issue, the submitted patch is applied to the repository and that issue's validation tests run; PASS/FAIL; overall score is a percentage of passing patches (sentence was truncated in my read - exact wording UNVERIFIED).
- THIRD-PARTY CLAIM: hidden tests; SWE-bench-style; held-out issues in popular open-source (Python) repositories. UNVERIFIED.

## 2. Model
- OFFICIAL-EXCERPT: only `gemma-4-31b-it-qat-w4a16-ct` supported; must be chosen for every agent and subagent; optional `.safetensors` LoRA adapters.
- SOURCE-DERIVED: at most one unique base model across the agent tree; W4A16 ~16-18 GB; vLLM on 4x L4 GPUs; `max_model_len=32768` (prompt + reasoning + output); `tool_call_parser='gemma4'`, `reasoning_parser='gemma4'`, thinking enabled by default; adapters selectable per agent.

## 3. ZIP structure
- OFFICIAL-EXCERPT (tree):
```
submission.zip
  agent.yaml                 REQUIRED root agent config
  configs/sampling.yaml      optional, via !include
  prompts/system.md, analyzer.md    optional, via !include
  sub_agents/*.yaml          optional sub-agent / AgentTool configs
  adapters/<name>/adapter_config.json + adapter_model.safetensors   optional
  skills/<skill>/SKILL.md, scripts/ (python or bash run in sandbox), resources/ (markdown)   optional
```
- SOURCE-DERIVED: also optional `eval_config.yaml` at root (key `evaluation:` with `timeout_seconds`, `max_tool_calls`, `max_time_minutes`, `max_turns`). Exactly one root config among agent.yaml/agent.yml/root_agent.yaml/root_agent.yml (zero => MissingRootConfigError; several => MultipleRootConfigsError). `agent.yaml` must be at the archive root, not inside an extra folder (also stated by third-party starters).
- INFERENCE: build the ZIP from inside the submission directory so paths are root-relative.

## 4. agent.yaml / compiler
- SOURCE-DERIVED: "Competitors do not submit Python code entrypoints". A sandboxed YAML compiler (`adk-submission: compile_submission`) resolves names against closed registries (tools, models, skills, callbacks). Agent classes: LlmAgent (default), SequentialAgent, ParallelAgent, LoopAgent (<=500 iterations).
- LlmAgent fields (SOURCE-DERIVED): name, model, adapter, description, instruction (supports `{state_var}` templating), tools (names, `agent_tool: {config_path, skip_summarization}`), skills (relative dirs), sub_agents (`config_path`), output_key, include_contents, disallow_transfer_to_parent/peers, generate_content_config.
- `!include`: .md/.txt as raw text; .yaml/.yml recursive (depth<=10, cycle-checked); absolute paths, `..`, null bytes, symlinks out of root blocked.

## 5. Tools (SOURCE-DERIVED; names also in third-party READMEs)
run_command, submit_patch, get_status, read_file, edit_file, write_file, get_code_neighbors, search_similar_code, get_code_subgraph (9 bound tools). Third-party READMEs additionally list run_skill_script and load_skill_resource (UNVERIFIED whether counted separately). Graph tools need precomputed graph/embedding data; a third-party entrant says the released graph tools returned nothing on the corpus as downloaded (UNVERIFIED). OFFICIAL-EXCERPT says "custom tools" may be part of the submission; SOURCE-DERIVED says tools resolve from a closed registry => custom tools presumably means skills/sub-agents, NOT new Python tools (INFERENCE; UNRESOLVED).

## 5b. Skills
OFFICIAL-EXCERPT: `skills/<name>/SKILL.md`, `scripts/` (python/bash run in a sandbox), `resources/` (domain knowledge markdown).

## 6. Runtime restrictions (SOURCE-DERIVED)
- Sandbox network `none`; no pip; dependencies preinstalled; single-command timeout 300 s (command timeout does not end session); container setup excluded from agent budget.
- Harness leaves the agent loop after `submit_patch` and final response; nudges up to 3 times if agent stops early (wording UNVERIFIED).
- Context compaction and prefix caching configured by harness; transient LLM errors (429/5xx) retried up to 5 times.
- Generation: max_output_tokens 1..32768 (default 16384), thinking_budget 0..32768 (default 4096); all sampling fields allowed.

## 7. Submission size/format limits (SOURCE-DERIVED)
3 GiB unpacked (including adapters); <=10,000 files; <=1,000 YAML files; YAML <=50 MiB; skill dir <=50 MiB; instruction <=1,000,000 chars per agent; <=500 agents; nesting depth <=50; <=1,000 skills. Allowed extensions: .yaml .yml .md .txt .py .json .safetensors; pickle weights (.bin .pt .pth) and other binaries/archives rejected; adapters must be .safetensors.

## 8. Things that could invalidate a submission (from the above; each UNVERIFIED against official file)
No/multiple root configs; agent.yaml nested; symlink/path traversal; disallowed extension; >3 GiB; more than one base model or a model other than the allowed one; Python entrypoints; pickle weights; changing test files instead of production code (third-party guidance; rule text UNKNOWN).

## 9. Dates (OFFICIAL-EXCERPT, all 23:59 UTC)
Start 2026-09-23; optional paper deadline 2026-11-12; entry deadline 2026-11-25 (rules must be accepted before); team merger 2026-11-25; final submission 2026-12-02. Organizers may change the timeline. Prizes: SOURCE-DERIVED total $100,000 incl. $35,000 paper award; a third-party issue lists $65,000 main track (UNVERIFIED).

## 10. Data (SOURCE-DERIVED, gated)
Dataset contains `sample_submission/`, `tasks.jsonl`, graphs, embeddings, `HARNESS_README.md`, and wheels for local evaluation with swegemma / adk-eval-core. Data downloadable only after accepting rules (`kaggle competitions download -c gemma-4-developer-agent`).

## 11. UNKNOWN (must be answered from the official files)
Submission count/day limits; whether daily/total compute quotas apply; exact scoring formula and tie-breaks; leaderboard visibility; open-source/licensing obligations for winners; whether skills' `resources/` retrieval counts against context; native function-calling behavior; exact tool signatures/budgets.
