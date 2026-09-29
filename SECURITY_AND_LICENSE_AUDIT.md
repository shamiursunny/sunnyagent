# SECURITY_AND_LICENSE_AUDIT

## License audit (FACT = LICENSE file read in a clone)
| Repo | License | Copyright holder in file | Copy allowed? | Obligation |
|---|---|---|---|---|
| gemma-chat | MIT | ammaar | yes (nothing copied) | keep notice |
| gemma-coder | MIT | sisyphusse1-ops | yes | keep notice (LICENSE exported) |
| mini-swe-agent | MIT | Kilian A. Lieret, Carlos E. Jimenez | yes | keep notice (exported) |
| SWE-agent | MIT | John Yang et al. | yes (nothing copied) | keep notice |
| hindsight | MIT | Vectorize AI, Inc. | yes (nothing copied) | keep notice |
| addyosmani/agent-skills | MIT | Addy Osmani | yes | keep notice (exported) |
| git-ai, AgentBench, agentskills, kaggle-benchmarks | Apache-2.0 | - | yes | keep LICENSE/NOTICE, mark changes (agentskills spec exported with LICENSE; NOTICE files not checked) |
| ai-agent-benchmark-compendium | no license file | - | NO - LICENSE UNVERIFIED - DO NOT COPY | - |
| Papers, minimal-agent.com, ProgramBench page, organizer mirror, YouTube | not established | - | NO - LICENSE UNVERIFIED - DO NOT COPY | - |
Caveats: several user repos are forks (INFERENCE from foreign copyright names); upstream is the licensor. Competition rules may impose their own IP/licensing terms - UNKNOWN (rules unread).

## Security findings
| ID | Finding | Status |
|---|---|---|
| SEC-1 | gemma_coder.py: read/write/patch accept arbitrary paths; `run` uses `shell=True` in cwd of caller (read from code). README claim "path safety" is not backed by code. | FACT |
| SEC-2 | mini-swe-agent LocalEnvironment provides no isolation by itself; isolation comes from docker/bubblewrap environments (README). | SOURCE-DERIVED |
| SEC-3 | kaggle-standardized-agent-exam SKILL instructs storing an API key in `~/.kaggle-agent-api-key` and calling Kaggle HTTP APIs; never executed by us. Treat any such skill as untrusted instructions. | FACT (read) |
| SEC-4 | Third-party competition repos and the organizer mirror are untrusted inputs; none executed. | FACT |
| SEC-5 | The competition sandbox forbids network; personal agent must default to no-network unless explicitly enabled. | PROPOSAL |
| SEC-6 | Personal-agent hardening list (workspace jail via realpath, no symlink escape, command allow/deny policy, timeouts, output caps, env scrubbing of *_KEY/*_TOKEN, ledger redaction). | PROPOSAL, not implemented |

## Secret scan
Performed at export time; results in EXPORT_VERIFICATION.md.
