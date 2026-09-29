# DECISION_LOG

## Decisions made (by the user; quoted from user instructions in this conversation)
| ID | Decision | Source |
|---|---|---|
| D-001 | V0.5 is a frozen baseline; do not modify, replace or rewrite history | user prompts |
| D-002 | V5.5 developed independently of V0.5, on a separate branch; both preserved | master prompt |
| D-003 | Research/design gate must be approved before implementation | master prompt |
| D-004 | Do not force the personal-agent runtime into the Kaggle ZIP if the competition architecture does not permit it | export prompt |
| D-005 | Implementation repo = coding-agent-platform; research export repo = gemma4-v5.5-research | user prompt |

## Open decisions (need the user)
| ID | Question | Why it matters | Default if the user says "you decide" (PROPOSAL) |
|---|---|---|---|
| OD-1 | Accept "shared POLICY core + two runtimes" instead of "one Python core agent" | Competition forbids Python entrypoints (mirror; must be re-verified) | Accept |
| OD-2 | Personal-agent model runtime: Ollama / OpenRouter / vLLM on Kaggle GPU | Determines model.py and notebook design | Model interface with OpenAI-compatible HTTP; vLLM/Ollama first |
| OD-3 | Will the user accept competition rules and download the dataset (needed for official spec, wheels, tasks)? | Blocks all Kaggle-side validation | Required |
| OD-4 | May third-party mirrors be used as an interim spec? | Provenance unverified | Interim only; every mirror fact re-verified against the official file |
| OD-5 | Make implementation repo readable to the next AI, or export state files | Blocks ST00 | Export state files (no tokens in chat) |

## Decisions proposed by the export agent (NOT decided)
P-1 Policy artifacts as the shared core. P-2 Root LlmAgent + read-only localizer AgentTool, no multi-stage pipeline for first candidate (small-change principle). P-3 Static experience cards as memory on the Kaggle side. P-4 One change per experiment; V0.5 remains control.
