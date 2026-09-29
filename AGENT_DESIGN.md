# AGENT_DESIGN (PROPOSAL; numbers are placeholders to be tuned by ablation, UNVERIFIED)

## Context budget (32,768 total incl. output/thinking - SOURCE-DERIVED)
Placeholder split: system prompt <=1.5k; active skill <=1k each, at most 2 loaded; running STATE block <=0.5k; tool outputs capped (~2k each); thinking_budget and max_output set well below 32k so history is not starved. Tuning: measure prompt-size growth over a trajectory.
## Prompt structure (policy/prompts/system.md)
ROLE + CONTRACT (fix the issue, minimal change, no test edits) -> LOOP RULES (search before read, reproduce first, one hypothesis at a time) -> STATE BLOCK format -> TERMINATION (run tests, review diff, submit_patch, then final message) -> FAILURE RULES (same failure twice => change hypothesis).
## Skills (progressive disclosure; each SKILL.md short)
repository-discovery, task-analysis, code-search, implementation, debugging, testing, recovery, final-review (+ optional security-review). Frontmatter per agentskills spec; layout per competition (`resources/`). Skill scripts (python, offline): `find_tests.py` (locate relevant tests), `summarize_diff.py`, `card_search.py` (keyword search over static cards). Scripts must be deterministic and time-bounded.
## Compact STATE block (agent rewrites each few turns)
task | hypothesis | files | last_observation | active_skill | pending_validation | failures | next_action
## Personal-agent API (PROPOSAL)
`agent = GemmaAgent(config); result = agent.run(task)`; `result` = final_status, patch, ledger path. Config YAML: model, tools, memory, sandbox, limits.
## Termination
Kaggle: submit_patch then final response (harness behaviour). Personal: `done(summary)` after validation; hard limits on steps, wall time, consecutive format errors.
