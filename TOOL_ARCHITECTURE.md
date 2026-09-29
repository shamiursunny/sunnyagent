# TOOL_ARCHITECTURE

## Kaggle (SOURCE-DERIVED, secondary): fixed tools
run_command, submit_patch, get_status, read_file, edit_file, write_file, get_code_neighbors, search_similar_code, get_code_subgraph; plus skill helpers (run_skill_script, load_skill_resource: UNVERIFIED count). We cannot add tools; we shape usage via prompts/skills. Exact signatures UNKNOWN until HARNESS_README (official) is read.
## Personal (PROPOSAL)
Tool | Purpose | Guard
- read_file(path, start, end) | ranged reads | realpath inside workspace; size cap
- search(pattern, glob) | ripgrep-like | output cap
- edit(path, old, new) | unique-match patch (idea from gemma_coder) | must match exactly once
- write_file | new files | workspace-only; deny tests dir unless allowed
- run(cmd, timeout) | shell | argv-list preferred; deny list (rm -rf outside, curl|sh, sudo); timeout; output cap; scrubbed env
- diff() / status() | evidence | -
- done(summary)
Environment interface: `execute(cmd, cwd, timeout) -> {stdout, returncode, truncated}`. Implementations: LocalConfined, Docker/bubblewrap (pattern from mini-swe-agent), NotebookEnv (Jupyter kernel-side subprocess). Security list: SECURITY_AND_LICENSE_AUDIT SEC-6.
## Tool result schema
{ok, output(<=N chars), truncated, elapsed_ms, error?} ; every call appended to the ledger.
