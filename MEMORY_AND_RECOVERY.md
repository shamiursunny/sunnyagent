# MEMORY_AND_RECOVERY (PROPOSAL)

## Memory types
Episodic (what happened in a run), semantic/project (facts about a repo), procedural (how to do a task type).
## Kaggle side (no network, no DB, no live writes assumed)
Static experience cards as markdown under `skills/<x>/resources/`, procedural mostly. Access flow SEARCH -> SELECT -> BROWSE -> TRANSFER -> ACTION via `run_skill_script card_search.py <keywords>` (returns <=5 titles+ids, <=300 chars each) then `load_skill_resource` for one card. Bounded: card <=~400 tokens, index <=~1.5k tokens. Risk: contamination if cards come from evaluation-set issues (UNKNOWN rules) - build cards only from own tasks or clearly disjoint sources; log provenance per card.
Card schema (adapted from MemGovern fields; own schema): architecture/experience_card_schema.json.
## Personal side
SQLite (stdlib) or JSONL; `retain(fact, kind, source)`, `recall(query, k, budget_tokens)`, `reflect(run_id)` (writes lessons after a run). Interface names from Hindsight; no Hindsight code or service used (MIT but heavy).
## Recovery state machine (architecture/recovery_state_machine.md)
BASELINE -> LOCALIZE -> HYPOTHESIZE -> PATCH -> VALIDATE; on FAIL classify: same-root => REVISE, new-root => REPLAN; every retry records a reason; identical action+identical observation twice => forced hypothesis change; limits: max revisions per hypothesis (placeholder 2), max replans (placeholder 2), global step/time caps (personal: config; Kaggle: eval_config.yaml). After limits: submit best validated patch or stop with status BLOCKED/FAILED.
