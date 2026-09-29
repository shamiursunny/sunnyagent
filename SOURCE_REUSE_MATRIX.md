# SOURCE_REUSE_MATRIX

Classes: DIRECT COPY | ADAPT | REFERENCE ONLY | DO NOT USE. Finding: **no file needs DIRECT COPY into the Kaggle submission** (only YAML/MD/TXT/skill-scripts allowed; nothing third-party is required). Copies in `source-code/` are for study/adaptation with licenses preserved.

| Source | Path | License (verified from LICENSE file) | Class | Exported? | Purpose / modifications | Compatibility (verified?) |
|---|---|---|---|---|---|---|
| gemma-coder | gemma_coder.py | MIT (sisyphusse1-ops) | ADAPT | verbatim | patch uniqueness check, done protocol, XML tool format; must add path confinement | Not run/tested |
| gemma-coder | LICENSE | MIT | - | verbatim | attribution | - |
| mini-swe-agent | src/minisweagent/agents/default.py | MIT | ADAPT | verbatim | loop, limits, format-error exit; imports pydantic/jinja2/minisweagent (would not run standalone) | Not run |
| mini-swe-agent | src/minisweagent/environments/local.py | MIT | REFERENCE ONLY | verbatim | environment interface shape; unsandboxed | Not run |
| agentskills | docs/specification.mdx | Apache-2.0 | REFERENCE ONLY | verbatim | SKILL.md rules | Layout differs from competition (resources/ vs references/) UNVERIFIED |
| addyosmani/agent-skills | skills/{debugging-and-error-recovery,context-engineering,planning-and-task-breakdown,test-driven-development}/SKILL.md | MIT | ADAPT | verbatim | process text to be shortened for 32k context | Not tested with Gemma |
| gemma-chat | * | MIT | REFERENCE ONLY | no | - | src unread |
| git-ai | * | Apache-2.0 | REFERENCE ONLY | no | provenance idea | Rust binary |
| SWE-agent | tools/* | MIT | REFERENCE ONLY | no | tool design | code unread |
| hindsight | * | MIT | DO NOT USE (code) / REFERENCE (interface names) | no | too heavy | - |
| AgentBench | * | Apache-2.0 | REFERENCE ONLY | no | - | - |
| kaggle-benchmarks | * | Apache-2.0 | REFERENCE ONLY | no | concepts | internal-only local dev |
| ai-agent-benchmark-compendium | README.md | NONE FOUND | DO NOT USE (LICENSE UNVERIFIED - DO NOT COPY) | no | links only | - |
| MemGovern paper | - | paper license unchecked | REFERENCE ONLY (LICENSE UNVERIFIED - DO NOT COPY) | summarised | card schema idea; own schema in architecture/ | - |
| BenchGuard paper | - | CC BY 4.0 (page) | REFERENCE ONLY (cite) | summarised | taxonomy | - |
| minimal-agent.com / ProgramBench page | - | none stated | REFERENCE ONLY (LICENSE UNVERIFIED - DO NOT COPY) | summarised | - | - |
| Mirror of organizer docs | docs/*.md | none found | DO NOT USE (copy) | facts summarised only | - | provenance unverified |
| YouTube | - | - | SOURCE NOT ACCESSIBLE | no | - | - |
